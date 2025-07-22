Abaixo, apresento um resumo essencial de **cada bullet point** listado no documento **"TQS24 - Tópicos de estudo.pdf"** para o exame de **Teste e Qualidade de Software (TQS)**. Cada ponto é abordado de forma concisa, destacando o conceito principal ou a ideia central, mantendo a estrutura do documento. Para atender ao seu pedido, respondi literalmente a cada bullet point, agrupando por tópicos e subseções, com linguagem clara e objetiva. As alterações marcadas em amarelo (atualizações de 2024) recebem atenção especial, mas todos os pontos são cobertos.

---

## **1. Qualidade do Software (Conceitos)**

### **1.1 Fatores de Qualidade**
- **Fatores de qualidade**: Características que definem a qualidade do software, como funcionalidade (atende requisitos), confiabilidade (opera sem falhas), usabilidade (fácil de usar), eficiência (bom desempenho), manutenibilidade (fácil de corrigir) e portabilidade (funciona em diferentes plataformas), conforme ISO/IEC 25010.

### **1.2 Métricas e Monitorização da Qualidade**
- **Apresentar diferentes métricas usadas na avaliação do grau de cobertura**: Métricas como cobertura de código (percentual de linhas/branches executadas), cobertura de requisitos (requisitos testados) e cobertura de mutação (mutantes mortos) avaliam a eficácia dos testes.
- **Admita a utilização da métrica defeitos/kLOC para medir a densidade de defeitos num dado projeto. Critique o uso desta métrica, analisando, por exemplo, a sua eficácia, limitações ou facilidade de a implementar**: Defeitos/kLOC (defeitos por 1000 linhas de código) compara projetos, mas é limitada por não considerar complexidade, tipo de linguagem ou qualidade do código; fácil de calcular, mas pode enganar em projetos concisos.
- **Argumente sobre o nível de cobertura de código ideal que deve ser incluído num quality gate**: Depende do contexto: 80-90% para sistemas comuns, >95% para críticos; quality gates rejeitam builds abaixo do limite, equilibrando esforço e risco.
- **Explicar/definir as métricas de qualidade (comuns) usadas pela ferramenta SonarQube**: Incluem bugs (erros), vulnerabilidades (falhas de segurança), code smells (más práticas), cobertura de testes, duplicação de código e dívida técnica (esforço para corrigir problemas).
- **Caraterize a métrica maintainability (facilidade de manutenção), na perspetiva do SonarQube, analisando os elementos que podem contribuir para a definir**: Avalia esforço para manter código, medido por dívida técnica (tempo para corrigir code smells) e complexidade (ex.: métodos longos, aninhamento).
- **Que fatores objetivos podem influenciar a métrica de complexidade do código?**: Tamanho de métodos/classes, número de caminhos lógicos (cyclomatic complexity), acoplamento entre componentes e uso de estruturas condicionais.
- **Explicar o conceito technical debt e o seu impacto na gestão da qualidade**: Dívida técnica é o custo acumulado de adiamento de correções (ex.: code smells, bugs). Impacta aumentando custos de manutenção e riscos de falhas.
- **Explique o conceito de Cyclomatic complexity e calcule-a, a partir de um excerto de código**: Mede caminhos independentes no código (E - N + 2P, onde E = arestas, N = nós, P = componentes). Ex.: Método com 2 `if`s tem complexidade 3 (1 + 2 decisões).

---

## **2. SQA e Métodos Ágeis**

- **No contexto dos métodos ágeis, o que é uma (user) story?**: Descrição curta de uma funcionalidade do ponto de vista do usuário (ex.: "Como cliente, quero filtrar produtos por preço").
- **Como é que as user stories podem ser vistas como um instrumento conversacional para recolher e evoluir os requisitos do sistema?**: Promovem diálogo entre desenvolvedores, QAs e stakeholders, refinando requisitos via feedback e exemplos concretos.
- **Como é que a user story é usada como unidade elementar de funcionalidade do produto (na gestão do trabalho, verificação de qualidade, entrega contínua)?**: Serve como base para planejamento (sprints), testes (critérios de aceitação) e entregas incrementais em CI/CD.
- **Apresentar, no contexto no projeto do grupo, exemplos concretos de stories, incluindo a sua descrição (âmbito funcional e critérios de aceitação) de acordo com o esquema de documentação proposto nos métodos ágeis**: Ex.: Story "Adicionar item ao carrinho"; Descrição: "Como cliente, quero adicionar produtos ao carrinho"; Critérios: "Item aparece no carrinho em 2s, estoque é atualizado".
- **Explicar a prática do BDD e relacioná-la com o desenvolvimento por user stories**: BDD define comportamentos testáveis (Given-When-Then) a partir de user stories, garantindo que o código atenda aos requisitos de negócio.
- **Que tipo de assuntos são incluídos numa "definition of done (DoD)"? Como é que este conceito é usado para assistir uma estratégia de QA?**: Inclui código testado, revisado, documentado, implantado. DoD assegura qualidade consistente e validação completa.
- **Qual o valor acrescentado para o processo de SQA da utilização de dashboards de qualidade a nível dos requisitos?**: Dashboards (ex.: XRay) rastreiam cobertura de testes por stories/épicos, oferecem visibilidade, priorizam defeitos e aceleram feedback.

---

## **3. Teste de Software**

### **3.1 Conceitos e Princípios**
- **Distinguir entre verificação e validação**: Verificação confirma que o software foi construído corretamente (ex.: testes unitários); validação confirma que atende aos requisitos do usuário (ex.: testes de aceitação).
- **Distinguir entre testes unitários, de integração, de sistema e funcionais/aceitação**: Unitários testam componentes isolados; integração verifica interação entre componentes; sistema testa o software completo; funcionais/aceitação validam comportamento do usuário.
- **Interpretar o modelo da "pirâmide dos testes", explicando a razão da existência de camadas verticais e dos diferentes "tamanhos" de cada nível**: Base larga (muitos unitários, rápidos, baratos), meio (integração, moderados), topo estreito (sistema/aceitação, lentos, caros). Camadas refletem custo e escopo.
- **Associar tipos de teste aos níveis da pirâmide dos testes e aos papéis na equipa**: Unitários (devs), integração (devs/QAs), sistema/aceitação (QAs/stakeholders).
- **O que são testes "flaky"? Qual o papel das estratégias de "mocking" neste contexto?**: Testes flaky têm resultados instáveis (ex.: devido a rede). Mocking isola dependências externas, reduzindo flakiness.
- **Porque é importante testar de forma "isolada" (test in isolation)?**: Testes unitários isolados focam em uma unidade, evitam interferências externas, facilitam depuração.
- **Porque é que os testes unitários devem ser independentes? Que condições devem ser observadas?**: Não devem compartilhar estado ou ordem de execução. Condições: Limpar dados, evitar dependências globais.
- **Explicar a necessidade de suplementar o código de produção com testes**: Testes validam funcionalidade, evitam regressões e suportam CI/CD com entregas confiáveis.
- **Relacionar os níveis de abstração nos testes com o âmbito dos objetos/assuntos sob teste**: Unitários (métodos), integração (módulos), sistema (fluxos completos). V-Model mapeia testes a fases; ágeis iteram rapidamente.

### **3.2 Processo e Práticas de Teste**
- **Explicar o princípio "testar tão cedo quanto possível"**: Testar desde requisitos ou codificação reduz custos de correção, detectando defeitos cedo.
- **Explique o sentido da expressão "shift left"**: Mover testes para fases iniciais (ex.: TDD, revisões), integrado a CI para feedback rápido.
- **Confrontar V-Model com BDD**: V-Model é estruturado, testes por fase; BDD é colaborativo, focado em cenários de negócio executáveis.
- **Relacionar TDD e BDD**: TDD (bottom-up, testes unitários) foca em técnica; BDD (top-down, cenários) foca em comportamento. Ambos guiam desenvolvimento via testes.
- **Implicações de Debug Later vs. TDD**: Debug Later atrasa detecção, aumentando custos; TDD encontra erros cedo, agilizando correções.
- **Sentido da afirmação sobre BDD**: BDD planeja testes automatizáveis desde o início, baseados em cenários de negócio.
- **Mocks vs. Serviços Reais**: Mocks são rápidos, isolados, mas podem divergir; serviços em containers são realistas, mas complexos.
- **Critérios de aceitação executáveis**: Devem ser automatizados (ex.: Cucumber) para validar comportamento de forma objetiva.
- **Page Object Model**: Cada página web é uma classe com métodos de interação, melhorando reusabilidade em testes Selenium.
- **Testes de exceções**: Devem verificar contratos (ex.: lançar exceção para entrada inválida).
- **Vantagem de top-down**: Alinha com requisitos de negócio, guiado por BDD; testes refletem valor do usuário.
- **Browsers headless**: Mais rápidos, consomem menos recursos, ideais para CI.
- **Testes de desempenho distribuídos**: Simulam carga real, testando escalabilidade.
- **Funcionais vs. Não Funcionais**: Estratégia deve equilibrar ambos, priorizando conforme o projeto.
- **Pairwise Testing**: Testa combinações de entradas em pares, maximizando cobertura com menos casos.

### **3.3 Teste de Aplicações Multi-Camada (Spring Boot)**
- **Relação entre anotações Spring Boot**: `@DataJpaTest` testa repositórios; `@WebMvcTest` testa controladores; `@SpringBootTest` testa aplicação completa.
- **Unitários vs. Integração**: Unitários isolam componentes (ex.: serviço com mocks); integração testa interação (ex.: controlador + banco).
- **Dependency Injection**: Facilita mocks em testes e modularidade no código.
- **Flyway DB**: Gerencia migrações de banco, garantindo schema consistente em testes.
- **Estratégias Spring Boot**: **A favor**: Automação, integração com JUnit/Mockito. **Contra**: Overhead em `@SpringBootTest`.

### **3.4 Trechos de Código e Tipos de Teste**
- **Testes unitários (JUnit)**: Verificam métodos isolados, com/sem mocks (ex.: `assertEquals`).
- **Testes Spring Boot**: Unitários com `@MockBean`; integração com `TestRestTemplate` (HTTP real) ou `MockMvc` (simulado).
- **Test Containers**: Iniciam containers (ex.: PostgreSQL) para testes realistas.
- **Rest-Assured**: Testa APIs com sintaxe fluente, integrado ao Spring Boot.
- **Pipelines CI/CD**: Interpretar fluxos (ex.: build → test → deploy) em Jenkins/GitHub Actions.

---

## **4. Práticas de Garantia de Qualidade (SQA)**

### **4.1 Práticas Gerais**
- **Tecnologias SQA**: Identificar ferramentas como SonarQube, Jenkins, Selenium em vagas.
- **Perfil Engenheiro QA**: Competências em automação, CI/CD, métricas; ferramentas como JUnit, XRay.
- **Desafios de Testes**: Falta de adesão devido a prazos, cultura fraca. Solução: TDD/BDD, CI/CD, quality gates.

### **4.2 Práticas de Equipa**
- **Feature-Branch Workflow**: Cada funcionalidade em branch separado, merge via PR.
- **Merge/Pull Request**: Integra código com revisão e testes automatizados, usando GitHub/GitLab.
- **Style Guide**: Define padrões (ex.: nomenclatura, formatação) para consistência.
- **Android Open Source Practices**: Incluem revisão de código, testes automatizados, documentação clara.
- **GitFlow**: Usa branches `main`, `develop`, `feature`, `release` para ciclos estruturados.

### **4.3 Revisão de Código**
- **Vantagens**: Detecta bugs, melhora qualidade, promove aprendizado.
- **Extreme Programming**: Revisão contínua via pair programming.
- **Revisão de Testes**: Testes devem ser revisados para garantir clareza e cobertura.
- **Defeitos**: Bugs lógicos, code smells, violações de padrões.
- **Cultura**: Encontrar defeitos é positivo, foca em melhoria.
- **Formal Code Inspection**: Recomendada para sistemas críticos (ex.: aviação).

### **4.4 Análise Estática de Código**
- **Problemas Detectados**: Bugs, vulnerabilidades, code smells.
- **Ferramentas Java**: SonarQube, Checkstyle, PMD.
- **Defeitos Invisíveis**: Ex.: memory leaks, condições de corrida.
- **Vulnerabilidades**: Credenciais hardcoded, validação fraca.
- **CI/CD**: Executar análise estática em pipelines para feedback rápido.

### **4.5 Redesenho (Refactoring)**
- **Exemplos**: Extrair método, renomear variáveis, simplificar condicionais.
- **IDEs (IntelliJ)**: Suportam refatorações automáticas (ex.: extract method).
- **Exceções em Java**: **Checked** (ex.: `IOException`) exigem tratamento; **unchecked** (ex.: `NullPointerException`) são opcionais.
- **Más Práticas**: Capturar `Exception` genérica, ignorar exceções. **Refactoring**: Especificar tipo, usar `try-with-resources`.
- **Complexidade Cognitiva**: Aumentada por aninhamento, métodos longos.
- **Anti-Padrões**: Métodos longos, classes gigantes. **Refactoring**: Dividir em unidades menores.

### **4.6 Integração Contínua (CI)**
- **Práticas Fowler**: Commits frequentes, builds automatizados, testes rápidos.
- **Fluxo de Trabalho**: Commits em branches, CI executa testes/builds, feedback via dashboards.
- **Cultura CI**: Colaboração, automação, qualidade contínua.
- **CI vs. Delivery vs. Deployment**: CI (build/teste), Delivery (deploy manual), Deployment (deploy automático).
- **Feedback**: Resultados de testes, erros de build.
- **Contínua**: Integração frequente (várias vezes/dia).
- **Compile vs. Build**: Compile gera bytecode; build inclui testes, empacotamento.
- **Pipeline as Code**: Pipelines em `.yml` (ex.: GitHub Actions).
- **Registries**: Armazenam artefatos (ex.: Docker Hub).
- **DevOps as Code**: Infra/pipelines como código.

### **4.7 Entrega Contínua (CD)**
- **Workflow CD**: Build → Testes → Deploy (dev, staging, produção opcional).
- **Deployment Pipeline**: Automatiza build, teste, deploy, release.
- **Ferramentas**: Jenkins (orquestração), Artifactory (artefatos), Docker (ambientes).
- **Delivery vs. Deployment**: Delivery exige aprovação; Deployment é automático.
- **Containers (Docker, Kubernetes)**: Padronizam e escalam deploys.
- **Registry (ex.: GitHub Packages)**: Armazena imagens/artefatos, facilita CD.
- **Observability**: Monitora produção, permitindo diagnosticar problemas.

---

## **5. Ferramentas**
- **SonarQube Dashboard**: Exibe métricas (bugs, cobertura, dívida técnica).
- **JUnit Testes Unitários**: Escrever testes com `@Test`, `assertEquals`.
- **Mockito Testes**: Usar mocks para isolar dependências (ex.: `when().thenReturn()`).
- **Mockito Primitivas**: `@Mock` (objeto falso), `@Spy` (objeto real com overrides).
- **Selenium WebDriver**: Automatiza interações com browsers em testes web.
- **JUnit + Selenium**: Testes funcionais verificam fluxos web (ex.: login).
- **Maven Goals**: `compile` (gera bytecode), `test` (executa testes), `package` (gera JAR).
- **Cucumber Feature**: Especificar cenários Gherkin (ex.: `Feature: Login`).
- **Git Flow Workflow**: Branches `main`, `develop`, `feature`; comandos como `git checkout -b feature/x`.
- **Jenkins Dashboard**: Exibe status de builds/testes em pipelines.
- **GitHub Actions**: Workflows `.yml` definem CI/CD, versionados e reutilizáveis.
- **Docker e Continuous Deployment**: Containers garantem consistência em deploys.
- **BDD em Spring Boot**: Usa Cucumber, JUnit, Selenium para cenários full-stack.
- **JMeter Elementos**: **Samplers** (requisições), **Timers** (intervalos), **Listeners** (resultados).
- **@Mock vs. @Spy**: `@Mock` substitui objeto; `@Spy` permite comportamento real.
- **@InjectMocks e IoC**: Injeta mocks automaticamente, seguindo inversão de controle.
- **Test Containers**: Inicia containers (ex.: banco) para testes de integração.

---

## **6. Outros Tópicos**
- **Qualidade Tradicional vs. IA**: Tradicional foca em requisitos claros; IA foca em dados, métricas como acurácia, incertezas.
- **Especialistas de Domínio em BDD e IA**: Em BDD, definem cenários; em IA, interpretam dados e validam modelos.
- **Acurácia em IA**: Não é suficiente; considerar precisão, recall, explicabilidade.

---

## **Notas Finais**
- **Exame**: Inclui interpretação de código (JUnit, Spring Boot, Mockito, TestRestTemplate, MockMvc, RestAssured, Test Containers) e pipelines CI/CD.
- **Foco**: Compreender conceitos, relacionar práticas (TDD, BDD, CI/CD) e aplicar ferramentas.
- **Alterações 2024 (amarelo)**: Ênfase em pipelines CI/CD, Test Containers, e tópicos de IA.

Se precisar de exemplos de código para algum bullet point, explicações mais detalhadas, ou ajuda com questões práticas, é só avisar!