
<h1 align=center font-weight=strong>CodingPad<h1>
  
  
## Introdução

O CodingPad trata-se de um editor de texto multiusuário cooperativo, realtime. Além disso, caso o texto seja código ele irá padronizar o espaçamento, cores, sintaxe, etc. de acordo com a linguagem escolhida. 
<hr>

## Funcionamento
Inicialmente vale ressaltar que cada URL trata-se de uma página para edição de texto.
Para criar uma página basta entrar na URL do site e colocar o nome da página que deseja entrar, por exemplo: codingpad/teste
Dessa forma, o servidor irá verificar se a pagina "teste" ja existe. Caso exista, buscará ela no servidor e irá retornar o conteúdo ao usuário. Caso não exista, criará uma nova página e retornará ao usuário com as configurações padrões.
Vale ressaltar que podemos criar subpáginas, por exemplo: codingpad/teste/subpágina1
Nesse cenário, a "subpágina1" faz parte da página “teste” e pode ser acessada diretamente pela URL também, além de também ser feita a verificação de existência mencionada acima.
Além disso, todos que estiverem na mesma URL poderão editar o documento juntos e as alterações serão repassadas em tempo real para todos os usuários que estão nela.
No caso do texto ser código, haverá opção de qualquer usuário escolher a linguagem específica que deseja para que a padronização do código seja feita.
Por fim, vale ressaltar que não será necessário se cadastrar no site para criar ou editar páginas, mas todas as páginas criadas sem login serão públicas para todos os usuários visualizarem e editarem. Assim, todos os usuários logados poderão criar páginas privadas.
<hr>

## Arquitetura
- Arquitetura Cliente / Servidor
- Cache salvo no Redis
- Requisições tratadas por fila (Kafka ou RabbitMQ)
- Persistir texto da página em um arquivo de texto cujo nome e identificador único será o caminho depois da domínio do site
- Persistir dados em banco de dados (SQL ou NOSQL)
- Retorno via JSON
- Padrão REST
<hr>

## Testes
- **Testes de caixa-preta (funcionais):** verificar se o sistema atende todas as especificações e requisitos, o teste é executado e o resultado obtido é comparado a um resultado esperado previamente conhecido.
- **Teste de concorrência:** verificar se o sistema atende múltiplos usuários sem comportamentos inesperados
- **Teste de recuperação de falhas:** quando um componente falha e volta a executar, ele não leva o sistema a nenhum estado inesperado.
- **Teste de carga:** verificar se o sistema mantém a performance mesmo com vários clientes acessando ao mesmo tempo
<hr>
