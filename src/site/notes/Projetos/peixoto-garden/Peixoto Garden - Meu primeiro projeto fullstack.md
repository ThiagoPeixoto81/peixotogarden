---
{"dg-publish":true,"dg-home":null,"permalink":"/projetos/peixoto-garden/peixoto-garden-meu-primeiro-projeto-fullstack/","dgPassFrontmatter":true}
---

tag: [[Tópicos/Projetos\|Projetos]]

Eu tenho usado o obsidian para fazer meu digital garden ([[Projetos/Digital Garden/O que é um digital garden e porque acho daora a ideia de ter um.\|O que é um digital garden e porque acho daora a ideia de ter um.]]), porém falta para ele algo que gosto de aplicar em todos os projetos e coisas que uso: personalidade, gosto de fazer as coisas de modo que faça eu me lembrar que aquilo saiu do meu cérebro.

## Ideia inicial

A ideia inicial é que seja em react simples, sem muita firula, quero algo simples apenas para externar o que penso, não sei ainda como abordar isso, mas acho que vai ser uma experiência legal, o problema vai ser o back-end, vou fazer uma api em python provavelmente, porém não faço ideia de como fazer uma banco de dados realmente funcional, isso vai ser divertido.

Uma das premissas que quero abordar aqui é tentar fazer as coisas de maneira mais autoral possível, tenho pensado bastante em quanto tenho estado tão depedente de IAs para algumas coisas, então vou tentar codar a moda antiga, resolvendo tudo na mão e procurando erros no stack overflow ou algo assim, vai ser divertido.


## PASSO 1 - Fazer template no figma

A ideia do design é ser algo simples, não quero que isso seja  
um major design complexo, porque o foco do “projeto” não tá nisso  
ta em criar o meu espaço e eu sou muito fã das coisas simples  
isso reflete bem o que ta rolando na minha cabeça enquanto faço  
esse figma. Não é por conta da minha preguiça crônica não.  
  
Resolvi fazer três páginas principais, que vai ser a home, a página  
onde vai estar a nota e as categorias das notas, o resultado ficou legal porque ficou bem simples e minimalista, mas cumpre bem o papel que tenho em mente.

![Pasted image 20251119181744.png](/img/user/Projetos/peixoto-garden/imgs/Pasted%20image%2020251119181744.png)
  
  
Ainda não sei as tecnologias que vou usar, só tenho em mente o front-end que será em react provavelmente, e o back-end grandes chances de ser em python, mas ainda vou analisar corretamente, mas com isso a primeira fase foi concluída.

Eu vi que tem opções de exportar direto o obsidian para um site, mas ainda sinto que mesmo assim faltaria muito desse  toque pessoal que quero que tenha no meu garden.


## PASSO 2 - Decidir as tecnologias para front e back-end

Para **front-end** a ideia é usar **react**, mas quero usar com **tailwind**, é algo que nunca usei e que me parece divertido de tentar.

Para **back-end**, irei usar python com fast api, como é um projeto pequeno pretendo usar o sqlite mesmo


## PASSO 3 - Back-end

Para fazer o back-end foi bem simples, já havia feito um mais complexo para um outro projeto chamado [[Projetos/Mnemosyne/Mnemosyne\|Mnemosyne]], que inclusive ainda não terminei por preguiça, mas que vou abordar em algum momento por aqui.

![Pasted image 20251119225036.png](/img/user/Projetos/peixoto-garden/imgs/Pasted%20image%2020251119225036.png)

Essa parte finalizada ficou com essa composição de pastas, vou passar rapidamente por cada uma e explicar a função de cada uma:

- **app** => está o arquivo que usei para gerar o db em sqlite3 e o main.py que reúne todas os endpoints da API e também o titulo dela que coloquei como "Peixoto Garden API", inclusive se você está vendo isso no site, grande chance de esse ser o nome ou dominio.

- **repositories** => é o arquivo que vai se comunicar diretamente com o banco de dados, ele vai fazer as consultas, é a unica parte em que isso vai acontecer o resto do repositório não rela no banco

- **schemas** => é uma especie de tipagem, nessa parte uso pydantic, com ele monto os models que vão ser usados para tipar as requisições
	![Pasted image 20251119230135.png](/img/user/Projetos/peixoto-garden/imgs/Pasted%20image%2020251119230135.png)
	O que é legal de fazer os schemas certinho é que no /docs do Fast API, fica bem "didático", então é bom fazer isso além da padronização do projeto.

- **services** => é as funções que vão chamar as consultas do repositories, é uma forma bem organizada de fazer essas chamadas e é bem mais clean code.

- **controllers** => É onde está os endpoints da API, é onde chamaremos as funções vindas do service e definiremos a requisição como POST, GET, DELETE OU PUT, e passar o endereço certinho das rotas. Só precisei criar 4 por enquanto, mas acho que terei mais em breve

Com essa parte pronta e funcionando de maneira correta, agora é hora de fazer o front-end para então fazer a integração e partir para o deploy, to bem ansioso para fazer esse front.


## PASSO 4 - Front-end

O front-end foi mais díficil do que eu pensava, eu estava um pouco enferrujado com react e além disso resolvi usar tailwind para estilizar os componentes.

Falando sobre o tailwind, eu gostei bastante de utiliza-lo, foi mais simples do que eu pensava que seria e até me lembrou um pouco a época em que usava bootstrap junto com html (bons tempos!), foi um experiência legal.

Bom, para esse projeto em **REACT + TAILWIND**, ainda utilizei mais três dependências para outras funções:

- **iconify** => para pegar um ícone que usei na página de post, eu gosto muito de usar esse banco de icons, uso desde os primórdios e até hoje não abandonei

- **react router** => esse é básico de todo projeto em react, é usado para navegar entre as páginas.

- **react-markdown** => esse foi necessário para algo que vou comentar em breve

A estrutura de pastas foi algo bem padrão de react, com uma pasta para páginas, outra para os hooks, uma para components e outra para os assets, e o resto é os arquivos padrão de react (main.tsx, etc...).

Meu principal desafio aqui  foi conseguir ajustar a responsividade, eu nunca tinha feito em tailwind, então me passei um pouco, eu lembro que no chackra UI a gente fazia isso através de hooks, aqui no tailwind, é passado na própria classe da tag html, e não vou mentir que achei mais organizado até, me lembrou muito muito bootstrap, como eu havia dito.

Eu mudei algumas coisas do figma que eu tinha feito, mudanças substanciais mas que achei melhores, a maioria relacionado a tamanho da fonte em algumas partes em que achei que exagerei um pouco, parecia que eu tava fazendo um site para gente com uma visão horrível ler já que as letras estavam gigantes kkkkkkkk.

Acho que a maior mudança no projeto mesmo aqui, foi a ideia que tive de ao invés de passar o texto no banco, eu colocar em formato de .md, não sei se vou colocar o arquivo direto ou mandar escrito em md, mas em formato de string. Não sei se deu para entender, mas é isso. Por isso tive que usar essa biblioteca react-markdown, ele pega um markdown e transformar em tags html, ai você estiliza e ele deixa tudo certinho, sem dificuldade nenhuma. Trabalhar com .md vai ser melhor, porque como eu disse, a maioria das coisas que tem no site foi algo que escrevi e coloquei no meu obsidian e o obsidian salva as notas em .md então assim vai ser mais fácil.

Resultado final:

![Pasted image 20251124211022.png](/img/user/Projetos/peixoto-garden/imgs/Pasted%20image%2020251124211022.png)

![Pasted image 20251124210951.png](/img/user/Projetos/peixoto-garden/imgs/Pasted%20image%2020251124210951.png)

![Pasted image 20251124211059.png](/img/user/Projetos/peixoto-garden/imgs/Pasted%20image%2020251124211059.png)

![Pasted image 20251124211117.png](/img/user/Projetos/peixoto-garden/imgs/Pasted%20image%2020251124211117.png)


## PASSO 5 - Mudanças no back-end

Isso demandou mais tempo do que eu pensava também, mas foi uma parte divertida do projeto, se você voltar na sessão em que falei do back-end, no final termino dizendo que no momento existia quatro endpoints na API, bom, depois dessa etapa aqui os endpoints mais que duplicaram.

Vou falar quais adicionei, porém não acredito que precise explicar pois o nome já é bem auto explicativo.

- **get_post_from_category**
- **get_all_posts**
- **get_favorite_posts**
- **change_post_favorite_status**
- **delete_post**
- **delete_category**

esses três ultimos foram os primeiros que fiz que não eram GET nem POST, não muda nada, mas fica de cores diferentes no swagger da fast api, achei daora isso.

Bom, em ideias gerais, isso serviu para dar os ajustes finais na API para fazer a integração com o front-end.

Eu também descobri que é bem possivel passar o markdown em texto mesmo ao invés de arquivo como eu estava um pouco inclinado a fazer, passando em texto é bem melhor. A única coisa que tenho que fazer é burlar os espaços do markdown substituindo por \n, mas isso foi bem rapidinho de fazer, mas acho que muito provavelmente vou fazer um painel onde vou fazer os posts e categorias, melhor do que ficar passando diretamente no python (ava, é memo?)

## PASSO 6 - Integrando tudo

A parte da integração foi simples, só tive que ajustar pequenos detalhes e fazer as requisições, tudo funcionou extremamente bem e agora o site está funcional, pegando todos os dados da api e exibindo perfeitamente. Sobre essa parte não tem muito o que falar pois não teve tantos problemas aqui.

Foi o procedimento padrão de consumir APIs através do react, você usa o axios, passa as rotas e pega as informações, quando fiz o front já deixei tudo perfeitamente preparado para receber as informações exatamente como viriam, essa é uma das vantagens de também ser o responsável pelo back-end, você já faz com que API mande exatamente o que você quer.

Com essa parte concluída, estou a poucos passos de terminar todo o projeto. Hoje é dia 15 de dezembro e gostaria muito de terminar antes do natal.

## PASSO 7 - Melhorando a segurança da API

Vou melhorar a segurança da API, minha ideia inicial é deixar os GETs públicos e os outros endpoints (PUT, DELETE, POST) privados.

Os GETs podem ser público porque é simplesmente pegar informações da API, não enxergo nenhum problema nisso. Já os outros métodos de endpoint não podem ser público porque mexem com informações sensíveis da API, uma pessoa que não seja eu pode modificar e fazer coisas engraçadinhas, não é o que desejo.

Então para fazer essa parte, eu separei os controllers do que vai ficar público e do que vai ser do admin, dessa forma deu pra organizar melhor na fast api o que vai ser mostrado e o que não vai.

Com isso pronto, gerei chave da api que só eu tenho acesso e criei um auth.py, então nas rotas que são put, delete e post, eu passo uma dependência que chama uma função chamada 'admin required', essa função verifica a chave da api que está sendo passada, se for diferente da minha, ele nega o acesso, se for igual ele autoriza.

Foi um passo bem simples, eu nunca tinha feito algo assim, então foi bem divertido, e ver funcionando do jeito que planejei é bom demais.

## PASSO 8 - Fazendo o deploy da API e do Front-end

Para fazer o deploy da API, eu usei o render e para o deploy do front usei o vercel, eu comprei o domínio, esse que, provavelmente, você acessou.

O deploy foi bem simples também, o da API foi o único que eu ainda não tinha feito, deploy de front eu já tinha feito em outras ocasiões então não tinha muitos segredos.

Para a API a única coisa que tive que me atentar foi para passar o pathway das pastas certinho, para que assim na hora do deployment fosse possível ter acesso a todas.

No deploy do front-end foi tudo tranquilo, eu ajustei o front para ter um loading, para ele aguardar a informação da API chegar, isso é melhor do que deixar tudo em branco, ficou legal.

Depois disso, foi simples, o vercel ajuda muito com a questão de deploy e apontar para um domínio.


## PASSO 9 - Ajustes finais

api
- criar rota de editar e editar as notas

front
- opacidade dos icones na home
- espaçamento da direita
- tentar entender pq com f5 o site cai
- bold no hover da home


## CONCLUSÃO

Com isso tudo feito, o projeto está pronto e funcional, se você está lendo isso no site, você está tendo a prova viva de que tudo está funcionando. Agora meu próximo projeto é criar um painel para gerir melhor os posts e etc, pretendo fazer isso em next.js para já aprender esse framework também.

Aprendi muitas coisas novas nesse projeto e revisei algumas coisas velhas, obviamente não está perfeito, num futuro não muito distante pretendo dar uma repaginada no site, tentar deixa-lo mais bonito, mas estou satisfeito com o resultado final.

É isso, se você leu até aqui, você acompanhou a minha jornada no meu primeiro projeto fullstack, espero que tenha gostado!
