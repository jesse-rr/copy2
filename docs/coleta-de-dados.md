# 2.2.1 Coleta de Informações

## 1. Analisar a documentação disponível do sistema legado (se houver):

### (a) Diagramas UML, requisitos, manuais técnicos;
*   Não foram encontrados diagramas UML, manuais técnicos ou documentação formal de requisitos.
*   A única documentação identificada consiste em um arquivo `README.txt` gerado automaticamente, contendo instruções básicas para execução do arquivo JAR.

### (b) Scripts de banco de dados (MER, SQL);
*   Não foram encontrados scripts SQL, modelos MER ou qualquer artefato relacionado a persistência de dados.
*   A aplicação não utiliza banco de dados, mantendo seu estado em memória.

### (c) Comentários e logs de execução.
*   O código-fonte possui **mínima documentação interna** (comentários), dificultando a compreensão da lógica.
*   A aplicacao utiliza Log4j (configurado).

## 2. Mapear a estrutura geral do sistema:

### (a) Arquitetura utilizada (camadas, pacotes, módulos); 
*   **Arquitetura:** Estrutura monolítica simples, sem separação clara de camadas (MVC não implementado).
*   **Pacotes:**
    *   `entidades`: Classes de domínio (`Jogador`, `Tabuleiro`).
    *   `imagens`: Recursos estáticos (imagens).
    *   `interfaceGrafica`: Classes de UI (`AtorJogador`, `TelaJogador`).
    *   `mensagens`: Internacionalização (textos em inglês/português).
    *   `morelli`: Classe principal (`Main`).

### (b) Tecnologias empregadas (frameworks, bibliotecas, banco de dados);
*   **Linguagem:** Java (11+).
*   **Interface Gráfica:** Swing (`JFrame`), sem JavaFX.
*   **Dependências:** Gerenciamento manual (sem Maven/Gradle).
*   **Persistência:** Estado em memória (sem banco de dados).
*   **Bibliotecas:** Apenas bibliotecas padrão do Java & alguns outros projetos em forma de "jar".

### (c) Principais classes, métodos e dependências.
*   **`Tabuleiro`**: Classe central do jogo.
    *   *Responsabilidades:* Inicialização, distribuição de peças, validação de movimentos, cálculo de capturas.
*   **`Faixa`**: Representa faixas concêntricas do tabuleiro.
*   **`Posicao`**: Célula individual do tabuleiro.
*   **`Jogador`**: Representa jogador humano.
*   **`JogadaMorelli`**: Implementa jogada para rede.
*   **`NetGames`**: Gerencia comunicação de rede.
*   **`Ajuda`**: Fornece conteúdo de ajuda.
*   **Enums:** `TipoJogada`, `Cor`.

## 3. Anotar dúvidas e pontos de atenção para análise posterior.

*   **Qual o nome do jogo & funcionalidades?**
*   **Como rodar o jogo em casa?**
