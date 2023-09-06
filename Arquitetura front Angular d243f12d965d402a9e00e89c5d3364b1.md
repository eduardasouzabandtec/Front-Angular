# Arquitetura front Angular

“O verdadeiro custo do software é sua manutenção. Ter uma arquitetura bem fundamentada ajuda a reduzir os custos de manutenção do sistema.” - Robert C. Martin

- Angular
    
    O que é o Angular?
    
    O [Angular](https://angular.io/) é um framework  desenvolvido pelo Google que usamos para construir aplicações web e webview.
    
    Baseado no paradgima funcional e reativo; 
    
    Sua linguagem é typescript (Javascript com “super poderes”);
    
    Como aprender Angular ?
    Além da otima [documentação](https://angular.io/guide/what-is-angular) existe um [curso](https://www.youtube.com/playlist?list=PLGxZ4Rq3BOBoSRcKWEdQACbUCNWLczg2G) da [Loiane Groner](https://www.linkedin.com/in/loiane/) onde em algumas aulas e usando o Angular2 conseguimos ter uma base excelente para trabalhar com as versões atuais do Angular.
    
- Desenvolvimento
    - basico para iniciar projeto Angular
        
        O projeto deve ser criado através do quickweb;
        
        A versão minima desejavel é 13.0;
        
        Realizar requisições atraves do RouterModule;
        
        As “OP” devem ser definidas na JSP;
        
        Não ultilizar components do voxel/comunitty;
        
        Evitar ultilizar components do voxel/internet;
        
        Em casos de **control c + control v** de components entre projetos validar o uso do team componets;
        
        Observable com o dólar na frente $
        
    - Padrao de projeto
        - Teste unitarios
        - Estrutura de pastas
            
            Word 
            
        - Modulos
            
            Nas versões atuais do Angular não precisamos nos preocupar com os Modulos graças ao [Standalone](https://angular.io/guide/standalone-components), mas enquanto essa magia não chega nas versões disponiveis para o nosso uso (no Itaú. Usem nos seus projetos pessoais e apaixone-se),  qual a melhor forma de usarmos e devidir as modules ? 
            
            Essa foi uma duvida que me gerou alguns dias de pesquisa e a conclusão é DEPENDE. Para uma estrutura como essa precisamos pensar no cenario que vamos implantar, dessa forma chegamos a esse modelo:
            
            ![Untitled](Arquitetura%20front%20Angular%20d243f12d965d402a9e00e89c5d3364b1/Untitled.png)
            
            Os nossos projetos geralmente são divididos por fluxos e por isso são pequenos, contendo no maximo 4 pages, além de termos um aliado muito importante para compartilhar components o Voxel.  Sendo assim a estrutura que mais se adapta ao nosso “mundo” é como o diagrama acima.
            
            Onde podemos ter o **SharedComponents** (components usados em mais de uma page, geralmente os components do voxel);
            
            Já nas modules dos nossos **Smarts Components** (pages), declaramos e exportamos os dumb componts apenas para uso proprio. 
            
            Nesse modelo conseguimos dividir as modules e aplicar [lazy loading](https://angular.io/guide/lazy-loading-ngmodules).
            
    - Documentação
        
        A documentação é como um mapa do projeto com intuito de facilitar o aprendizado de novos integrantes e também auxiliar veteranos no time. 
        
        É preciso conter algumas informações importante como o nome do projeto, descrição, intuito, rotas, regras e toggle, tudo que facilite o entendimento. 
        
        Segue algumas dicas sobre documentação: 
        
        Ao iniciar um projeto ou fazer uma alteração devemos cria/atualizar a nossa doc;
        
        Deve ser criada no SharedPoint do time;
        
        O link deve ser incluido no README do projeto;
        
        Podemos seguir o  exemplo da doc “minhas preferencias” << por link
        
        Documentação vai além das requisições front/bff;
        
        Principais pontos a detalhar/descrever : 
        
        Services - detalhar sua funcionalidade 
        
        Pipes - detalhar com entrada e saida do dado
        
        Components - imagem e descrição
        
        Regras - detalhar suas regras e chave admin 
        
        Toogle - detalhar suas regras e chave admin
        
        Mock - como rodar o mock e quais são as requisições mockadas
        
        Build - como buildar o projeto local
        
        Start projeto - como rodar o projeto local 
        
        Test Projeto - como testar o projeto
        
        Versões e evolução - o que mudou nas versoes 
        
        Figma com link
        
        Tagueamento com link
        
    - Lint
        
        Pensando em manter uma qualidade de codigo e um padrão e também previnir futuros erros podemos instalar e configurar em nossos projetos os EsLint  e o Prettier.
        
        Porque o EsLint e não o TSLint ? Simples, o TsLint foi descontinuado 😧 !
        
        [EsLint](https://eslint.org/) → previnir erros e padronizar o desenvolvimento.  Imagine que em uma equipe de dois desenvolvedores um tenha mania de colocar ponto e virgula ( ; ) e a outra tem mania de usa aspas duplas(”), quando usamos o EsLint obrigamos a seguirem o mesmo padrão, assim podemos definir que ambos vão ultilizar o ponto e virgula e também as aspas simples. 
        
        [Prettier](https://prettier.io/) → Formatação de codigo.
        
        E como podemos instalar e configurar [](https://github.com/angular-eslint/angular-eslint)?
        Nas versões anteriores a 12 o angular vinha com o TsLint instalado, mas após o mesmo ser descontinuado não vem com nenhum  lint por padrão. 
        Mas para instalar basta seguir a documentação do [angular-eslint](https://github.com/angular-eslint/angular-eslint)
        
        Configuração do lint :
        INCLUIR O CODE 
        
    
- Gerenciamento de estado
    
    O que é Gerenciamento de estado ?
    
    O modo como os dados são armazenados  e alterados de maneira organizada e eficiente.
    
    Porque devemos nos preocupar com isso e quais são os beneficios ?
    
    Os benefícios são visíveis principalmente quando a nossa aplicação começa a crescer e alguns deles são: 
    
    Isolamento de responsabilidade → os components ficarão responsáveis por lidar com um dado x 
    
    Desacoplamento de estado → realizar abstração para que o estado seja compartilhado de outra forma que não seja componentes “pai”.
    
    O angular é baseado em programação reativa mas para que o nosso projeto seja de fato reativo precisamos seguir um design ou uma arquitetura reativa.
    
    Por isso precisamos ter o gerenciamento de estado e controle de fluxo. 
    
    Quando pensamos ou pesquisamos  sobre ****State Management**** no Angular o principal resultado será o [NgRx](https://ngrx.io/). 
    
    O NgRx é um framework que a junção do Angular + Redux + RxJS, muito usado em projetos parrudos. Mas esse não é nosso caso, por isso vamos ultilizar somente o RxJS. 
    
    Afinal o que é o RxJS ?
    
- RxJS
    
    [RxJS](https://rxjs.dev/) é uma biblioteca javascript muito conhecida quando falamos de progamação reativa, baseado no padrão de projeto [Observer](https://refactoring.guru/pt-br/design-patterns/observer). 
    
    O seu tipo principal é o [Observable](https://rxjs.dev/guide/observable) que é ultilizado nas rotas, formularios, estados e comunicação [HTTP](https://angular.io/api/common/http/HttpClient).
    
    Observable → uma coleção que funciona de forma unidirecional, ele emite notificações sempre que ocorre uma mudança em um de seus itens e apartir dessa notificação podemos executar uma ação. Para “ouvir” essas notificações usamos o famoso Subscribe , mas não se engane, o RxJS vai muito além do subscribe, tem muitos **[Operators](https://rxjs.dev/guide/operators)** para serem ********desbravados.
    
    - Qual Operator devo usar ?
        
        **[Operator Decision Tree](https://rxjs.dev/operator-decision-tree) é** um questionario que ao final de uma sequencia de perguntas nos retorna qual o operator que mais se encaixa com a nossa necessidade.
        
    - CRIAR EXEMPLO DE USO
        
        [Facades](https://andrewrosario.medium.com/o-padr%C3%A3o-de-projeto-facade-no-angular-1784dda6e129) 
        
        - **TodosService:** Serviço responsável pelas chamadas HTTP
        - **TodosState:** Serviço onde está armazenado o nosso estado
    - Memory leak
        
        
        Se imagine em uma sala de cinema após o filme acabar, as luzes acenderem  e a tela apagar, você continuaria sentado observando o vazio ? ou simplesmente iria embora ? 
        Essa é a sensação quando temos um subscribe que recebe uma notificação e não deve receber nenhuma outra.
        
        Quando destruimos um component ou diretiva deixamos os “subscriptions” ativos isso nos causa um problema: **Memory Leak** (vazamento de memoria), além de prejudicar o desempenho e perfomance,  pode causar um erro dificil de se localizar.
         E como podemos Resolver isso ?
        Se desincreva sempre que não precisar mais do Observable!
        
        Algumas formas de se desinscrever:
        
        CRIAR EXEMPLO
        
        .unsubscribe no NgOndestroy - quando temos um subscribe no ts 
        
        [array de sub](https://github.com/loiane/curso-angular/blob/master/requests-http/src/app/unsubscribe-rxjs/componentes/poc-unsub.component.ts)  →  tipo [subscription](https://rxjs.dev/guide/subscription)  quando temos muitos subscribe no ts 
        
        [TakeUntil](https://github.com/loiane/curso-angular/blob/master/requests-http/src/app/unsubscribe-rxjs/componentes/poc-take-until.component.ts) → recebe um observable e quando recebe um valor se desinscreve, no onDestroy eu notifico (.next) e completo (.complete) 
        
        [take](https://github.com/loiane/curso-angular/blob/master/requests-http/src/app/unsubscribe-rxjs/componentes/poc-take.component.ts) → passamos um numero de quantas vezes deve ser chamado e depois destruido
        
        [Asyn pipe](https://github.com/loiane/curso-angular/blob/master/requests-http/src/app/unsubscribe-rxjs/componentes/poc-async.component.ts) → no html e se desincreve quando o component  é destruido automaticamente
        
    - Diferença entre subject e behaviorsubject
        
        Quando gerenciamos os estados os tipos de Observable que mais são ultilizados são o subject e behaviorsubject mas qual a diferença entre eles ?
        
        Subject → Tipo especial de Observable, um multicast, ou seja possui varios observadores mas podemos cancelar (desincrever) de apenas um, e ele continuara a produzir valores até que todos se desincreva.
        
        [imagem](https://thepragmaticengineer.hashnode.dev/entendendo-o-rxjs-subject-vs-observable)
        
        BehaviorSubject → uma variante do subject mas emite sempre o ultimo valor recebido e precisa de valor para ser iniciado
        
    - Onde aprender ?
        
        Além da documentação existe um site [LearnRxjs.io](https://www.learnrxjs.io/) com exemplos das funcionalidades do RxJS.
        
- Team Components
- Acessibilidade
- Commit
    - Commit semantico
    - Code Review
- Branch
- Versao do projeto
- Deploy
    - GMUD
        
        Documentar GMUD LINK
        

[boaspraticas](https://andrewrosario.medium.com/padr%C3%B5es-e-boas-pr%C3%A1ticas-em-angular-que-te-ajudar%C3%A3o-a-escalar-5001e544e7de)

[links](https://www.youtube.com/watch?v=b-hebNuMrWA)

[linked](https://www.linkedin.com/pulse/gerenciamento-de-estado-redux-aplicado-ao-angular-abner-cleim/?originalSubdomain=pt)

[fabio](https://fabiodemiranda.com.br/gerenciamento-de-estado-ngxs-angular-flux-redux/)

[beneficios](https://gabrieluizramos.com.br/context-redux-e-gerenciamento-de-estado)

[reduxng](https://balta.io/blog/angular-redux-ngrx)

[a](https://www.dio.me/articles/gerenciando-estado-no-angular)

[medium](https://medium.com/@lucassimas/porque-n%C3%A3o-usar-ngrx-726633f21174)

[slideloiane](https://www.slideshare.net/loianeg/gerenciamento-de-estado-no-angular-com-ngrx)