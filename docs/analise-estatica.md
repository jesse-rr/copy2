# 2.2.2 Análise Estática

## 1. Ler e inspecionar o código-fonte:

### (a) Variáveis e métodos não utilizados
*   **Variáveis não utilizadas/redundante:**
    *   `JogadaMorelli.posicaoOrigem`, `.posicaoDestino`
    *   `Tabuleiro.jogador1`, `.jogador2`, `.proximoJogador`
    *   `AtorJogador.tabuleiroAtualizado`
    *   `Posicao.jogador`, `.adjacentes`
*   **Métodos não utilizados:**
    *   `ImagemDeTabuleiro.assumirMensagem()`, `assumirValor()`, `assumirPlacar()`
    *   `Tabuleiro.calcularVerticeFaixa()`, `definePartidaFinalizada()`, `recuperarFaixaDaPosicao()`
    *   `Posicao.setAdjacentes()`, `verificarAdjacentes()`, `possuiAdjacentesCorOposta()`, `verficarCaminho()`.
    *   `AtorJogador.notificaNaoJogando()`, `notificaJaConectado()`.

### (b) Código morto e/ou duplicado
*   **Código morto:**
    *   Classe `ImagemDeTabuleiro` inteira não utilizada.
    *   Métodos que lançam `UnsupportedOperationException` com `// TODO`.
    *   Classes comentadas fora - Inumeras
*   **Código duplicado:**
    *   `Tabuleiro.calcularMovimentoLinha()` e `Tabuleiro.calcularMovimentoColuna()` possuem estruturas muito similares.
    *   Vários métodos em `AtorJogador` possuem funcionalidades sobrepostas.

### (c) Uso incorreto de padrões de estilo e convenções
*   **Problemas de nomenclatura:**
    *   `Tabuleiro.calcularTomadaTrono()` - Nome confuso.
    *   `verficarCaminho()` - digitado errado.
    *   Enums em letra minuscula. ex: `Cor { roxo, azulEscuro }`. 
*   **Outros problemas de estilo:**
    *   Mistura de inglês e português em codigo e comentarios.
    *   Falta de documentacao.
    *   Uso excesso de `//TODO`.

### (d) Código de alta complexidade
*   **Alta complexidade cognitiva:**
    *   `Tabuleiro.verificarAdjacentes()` - Múltiplos loops aninhados e condições.
    *   `Tabuleiro.calcularTomadaTrono()` - Lógica intrincada.
    *   `Faixa.construtor` - Algoritmo complexo.
    *   `Tabuleiro.calcularCaptura()`
*   **Alta complexidade computacional:**
    *   Loops aninhados em `verificarAdjacentes()` podem resultar em O(n³).
    *   Algoritmos de verificação de movimento possuem loops aninhados.

### (e) Dependências desnecessárias
*   **Dependências problemáticas:**
    *   `Tabuleiro` depende de `AtorJogador` - violação da separação de conceitos.
    *   `JogadaMorelli` implementa `Jogada` sem funcionalidade significativa.
*   **Acoplamento excessivo:**
    *   `AtorJogador` possui conhecimento detalhado do `Tabuleiro`.
    *   Falta de interfaces bem definidas entre camadas.

## 2. Avaliar a complexidade (ex.: O(1), O(n), O(n²)) de todas as funções da classe Tabuleiro.
*M = número de faixas (constante, ~7), N = número médio de posições por faixa*

*   **O(1) - Tempo Constante:**
    *   `setPartidaEmAndamento()`, `isPartidaEmAndamento()`
    *   `atualizarTabuleiro()`, `getTabuleiro()`
    *   `abandonarPartida()`, `realizarAcordo()`, `getAjuda()`
    *   `atualizaJogadorDaVez()`
    *   `getPosicaoOrigem()`, `setPosicaoOrigem()`
    *   `getPosicaoDestino()`, `setPosicaoDestino()`
    *   `movimentoAoCentro()`, `calcularMovimentoDiagonal()`
    *   `calcularCaptura()` (itera sobre ~8 adjacentes)
    *   `criaJogadaDeFinalizacaoPartida()`, `finalizaPartida()`

*   **O(M) - Linear no número de Faixas:**
    *   `limparTabuleiro()`: Itera sobre todas as M faixas.

*   **O(N) - Linear no número de Posições:**
    *   `distribuiPecas()`: Opera sobre ~24 peças em N posições.
    *   `verificarAdjacentes()`: Percorre N posições em faixas próximas.
    *   `calcularTomadaTrono()`: Itera sobre N posições de uma faixa.
    *   `moverPeca()`, `atualizarPosicaoTabuleiro()`: Encontra posição em N.

*   **O(M * N) - Linear no total de Posições:**
    *   `calcularMovimentoLinha()`, `calcularMovimentoColuna()`: Loops sobre M faixas e N posições.
    *   `calcularMovimento()`: Chama os métodos acima.