# ProjetoN2
+--------------------------------+
|           Usuario              |
+--------------------------------+
| - id: Long                     |
| - nomeUsuario: String          |
| - email: String                |
| - senha: String                |
| - pontuacaoTotal: int          |
| - dataUltimoJogo: LocalDate    |
+--------------------------------+
| +jogar(jogo: Jogo): void       |
| +adicionarAmigo(u: Usuario)    |
| +entrarGuilda(g: Guilda)       |
| +editarPerfil(p: Perfil)       |
| +usarConsumivel(c: Consumivel, alvo: Usuario): void |
+--------------------------------+
             |
             | 1
             |-------------------+
             |                   | 1
        +----------+       +---------------+
        |  Perfil  |       |  Inventario   |
        +----------+       +---------------+
        | - nome: String   | - id: Long    |
        | - avatarURL: Str | - itens: List<Consumivel> |
        | - bio: String    +---------------+
        +----------+       | +adicionar(c: Consumivel) |
                           | +remover(c: Consumivel)   |
                           | +listarItens(): List<Consumivel> |
                           +---------------+
                                   |
                                   | 1
                                   |-------+
                                   |       | *
                              +-------------------+
                              |   Consumivel      |
                              +-------------------+
                              | - id: Long        |
                              | - nome: String    |
                              | - tipo: TipoConsumivel |
                              | - efeito: EfeitoConsumivel |
                              | - descricao: String |
                              +-------------------+
                              | +usar(alvo: Usuario): void |
                              +-------------------+

+---------------------------+
|  EfeitoConsumivel         |
+---------------------------+
| - tipoEfeito: String      |
| - intensidade: double     |
| - duracao: int            |
+---------------------------+
| +aplicar(alvo: Usuario)   |
+---------------------------+

+------------------+
|    Jogo          |
+------------------+
| - id: Long       |
| - nome: String   |
| - descricao: Str |
| - chanceDrop: double |
+------------------+
| +jogar(u: Usuario) |
| +sortearDrop(): Consumivel |
+------------------+
        |
        | 1
        |--------------------+
        |                    | *
   +-------------+       +----------------+
   |  SessaoJogo |       |   Pontuacao    |
   +-------------+       +----------------+
   | - id: Long  |       | - valor: int   |
   | - data: LocalDate | | - multiplicador: double |
   +-------------+       | - usuario: Usuario |
   | +calcularPontos()  | - jogo: Jogo |
   +-------------+       +----------------+

+------------------+
| DropService      |
+------------------+
| +gerarDrop(jogo: Jogo): Optional<Consumivel> |
+------------------+

+----------------------+
| Guilda               |
+----------------------+
| - id: Long           |
| - nome: String       |
| - descricao: String  |
| - membros: List<Usuario> |
| - ranking: Ranking   |
+----------------------+
| +addMembro(u:Usuario) |
| +removerMembro(u:Usuario) |
| +calcularRanking()    |
+----------------------+
