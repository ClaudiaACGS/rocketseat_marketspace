# rocketseat_marketspace

O Marketspace é o terceiro desafio da trilha da formação React Native 2022.
Neste projeto, o objetivo é construir um aplicativo de anúncios de produtos no estilo OLX, no qual os usuários podem cadastrar, gerenciar e vender seus itens.

A aplicação contempla autenticação de usuários, criação e edição de anúncios com upload de imagens, listagem com filtros e busca, além da possibilidade de entrar em contato com o vendedor via WhatsApp.

Esse desafio reforça conceitos fundamentais do React Native e aprofunda em novos tópicos que serão usados em qualquer aplicação mobile real: autenticação JWT, consumo de APIs REST, Context API, manipulação de imagens, formulários avançados, rotas privadas e upload de arquivos.

Instruções
Estrutura, regras e requisitos do projeto

1. Objetivo
Construir um aplicativo de marketplace funcional, aplicando os seguintes pontos:

Login e cadastro de usuários (com autenticação JWT).
Criação, edição, ativação/desativação e exclusão de anúncios.
Upload e exibição de múltiplas imagens de produtos.
Listagem de anúncios com busca e filtros.
Contato com o vendedor via WhatsApp.
Consumo da API fornecida pela Rocketseat para persistência de dados.
2. Conceitos e Regras
Autenticação e Contexto
Implementar autenticação JWT com Context API para gerenciar sessão.
Proteger rotas privadas (acesso somente após login).
Gerenciar refresh token.
Consumo de API
Utilizar Axios para chamadas HTTP.
Integrar com a API disponibilizada do desafio.
Gerenciar erros e exibir mensagens de feedback para o usuário.
Formulários
Utilizar React Hook Form para formulários, com validação.
Criar formulários para login, cadastro de usuário e cadastro/edição de produtos.
Imagens e Upload
Utilizar expo-image-picker para selecionar imagens da galeria.
Enviar múltiplas imagens no cadastro do produto.
Exibir imagens no formato de carrossel.
Navegação
Usar React Navigation com:
Stack Navigator (fluxos de cadastro e edição de produto).
Bottom Tabs para navegação principal.
Tratar corretamente rotas públicas e privadas.
Componentização e Estilização
Utilizar GlueStack e styled-components para construir interfaces declarativas e responsivas.
Criar componentes reutilizáveis (inputs, botões, cards de anúncio).
Funcionalidades do App
Home: listar anúncios disponíveis, com barra de busca e filtro avançado.
Meus Anúncios: exibir anúncios do usuário com opções de ativar/desativar.
Criar/Editar Anúncio: formulário em etapas (imagens, detalhes, condições de venda).
Detalhes do Produto: exibir informações completas e botão de contato via WhatsApp.
Desenvolvendo o projeto
Para desenvolver esse projeto, recomendamos utilizar as principais ferramentas que utilizamos durante o desenvolvimento do projeto Ignite Gym dessa formação.

Além disso, você deve consumir a API que preparamos para esse projeto, assim você pode se concentrar em desenvolver apenas a parte mobile. Nas 2 próximas seções, abordaremos com mais detalhes sobre a estrutura e como utilizá-la.

Como utilizar a API?
Para que você consiga utilizar a API, é preciso 
baixar o código no repositório
, seja clonando utilizando o comando git clone https://github.com/rocketseat-education/ignite-rn-2022-challenge-marketspace-api.git ou clicando na opção Download ZIP.

GitHub - rocketseat-education/ignite-rn-2022-challenge-marketspace-api

Após o download, você deve acessar a pasta do seu projeto e instalar as dependências com o comando npm i. Para executar o projeto, basta executar o comando npm run dev.

Com isso, a sua API estará pronta para ser consumida no endereço http://localhost:3333.

Estrutura da API
A API desse desafio foi estruturada seguindo a mesma ideia da API utilizada no projeto Ignite Gym. Para entender melhor sobre a estrutura e funcionamento da API você tem algumas opções:

Swagger: Assim como na API disponibilizada na aula, você pode acessar a documentação que criamos com o Swagger, basta executar a API e acessar a rota a/docs
Beekeeper: Assim como nas aulas, recomendamos o uso do Beekeeper para visualização dos dados do banco de dados.
Prisma Studio: Caso prefira outra forma de visualizar os dados do banco de dados, basta acessar a pasta da sua API pelo terminal e executar o comando npx prisma studio. Dessa forma, você vai conseguir ver as tabelas e os registros na url http://localhost:5555/
Insomnia: Caso queira interagir com a API de uma maneira bem direta e fácil, você pode utilizar um API Rest Client como o Insomnia. Basta 
executar o download dele
 e importar 
as configurações que disponibilizamos aqui
. Dessa forma, você terá acesso a todas as rotas e poderá fazer as requisições diretamente por ele.
Para entender melhor essas 4 opções acima, criamos um vídeo explicando todo o processo: desde o download do código no Github até a manipulação com essas opções.

Caso queira seguir um guia em vídeo, 
clique aqui

Rotas
Clique aqui para expandir
Redefinir do banco de dados
Caso tenha tido problemas com o banco de dados e queira recomeçar, você pode redefini-lo executando o seguinte comando no terminal da API:

npx prisma migrate reset
A CLI irá retornar a seguinte mensagem: Are you sure you want to reset your database? All data will be lost. › (y/N). Digite y e aperte Enter para confirmar.

Dicas
Inputs
Vocês irão perceber que nesse desafio trabalharemos com mais variedades de inputs do que o clássico TextInput. Além da possibilidade de criá-los manualmente, você utilizar libs como GlueStack para ajudá-lo, 
clique aqui

Modal
Nesse desafio, a seleção dos filtros é apresentada dentro de uma Modal. Vocês podem utilizar o 
componente do próprio React Native
, do 
GlueStack
 ou caso queira mais personalização e animação uma ótima biblioteca é a 
Bottom Sheet

Cadastro e Edição do produto
Como vocês podem ver no layout, no momento da criação e edição do produto podemos navegar por múltiplas páginas que se assemelham ao formato de pilha (botão de voltar, sem aparecer tabBar). Apesar de ser possível criar tudo no navegador de Abas e sumir manualmente com a tabBar, você também pode aninhar navegadores a fim de atingir o melhor dos dois mundos. A documentação oficial traz mais informações sobre isso:

Aninhando navegadores
Escondendo tabBar em telas específicas
Carrosel de imagens
Na hora de visualizar os produtos, o usuário poderá ver as múltiplas imagens cadastradas em formato de carrosel. Uma maneira manual de fazer seria implementar uma FlatList com 
pagingEnabled
 e monitorar os itens atualmente visíveis com o 
onViewableItensChanged
, porém também existem libs que além de já disponibilizarem o componente pronto para você são mais performáticas como a 
react-native-reanimated-carousel
.

Link WhatsApp
Quando o usuário estiver interessado no produto e quiser entrar em contato com o vendedor, basta clicar no botão para entrar em contato via WhatsApp. Para obter essa funcionalidade, você pode usar a 
API de Linking
 do React Native para abrir a URL do WhatsApp. Já para montar a URL com o número do vendedor do produto, você precisará seguir o formato definido pelo WhatsApp: [https://wa.me/](https://wa.me/5543998859908?text=Oi+Gabi%21+Gostaria+de+solicitar+um+or%C3%A7amento+de+projeto+%3A%29){número-de-telefone-com-ddi-e-ddd}. Segue 
a documentação oficial
 para mais informações.

Caso você tenha alguma dificuldade você pode ir no nosso 
fórum
 e deixar sua dúvida por lá!

Após terminar o desafio, caso você queira, você pode tentar dar o próximo passo e deixar a aplicação com a sua cara. Tente mudar o layout, cores, ou até adicionar novas funcionalidades para ir além 🚀

Entrega
Após concluir o desafio, você deve enviar a URL do seu código no Github.

Além disso, que tal fazer um post no LinkedIn compartilhando o seu aprendizado e contando como foi a experiência?

É uma excelente forma de demonstrar seus conhecimentos e atrair novas oportunidades!

Obs: Se você se sentir à vontade, pode postar um print do resultado e nos marcar! Vai ser incrível acompanhar a sua evolução! 💜

Feito com 💜 por Rocketseat 👋
