**nome dos alunos: RM 85225 - Carlos Eduardo Hayashi

RM 85169 - Larissah Silva

RM 85455 - Mike Freire

**Turma: 2TDS-F

**Ano: 2° Ano


## Sobre
O projeto **BancoDimDim** simula um banco digital, contendo a área do cliente e administrativa, permitindo depósitos e transferências entre contas do mesmo banco..

## Atenção
- O projeto terá um melhor desempenho utilizando o Microsoft Visual Studio
- Este não é um projeto para ser utilizado em produção. Ele é apenas uma demonstração do uso das tecnologias e da arquitetura em que foi construído. **Existem ajustes e melhorias a serem feitos**.

## Dados para acesso da agência

**CNPJ:** 03569262000160

**Senha** 123456

## Informações importantes
- Todos os valores internamente são tratados como centavos convertidos para R$ apenas na exibição ao cliente
- Os eventos orquestrados por filas terão um delay de 30 segundos apenas para percepção do uso da fila.
- O contexto de AGÊNCIA não possui CQRS para demonstrar que pode-se manter diferentes padrões conforme a necessidade.
- Os containeres **não** estão utilizando volumes, portanto ao matá-los irá causar a perda dos dados.
- A aplicação pode levar alguns segundos para iniciar.

## Fluxo
- Ao iniciar a aplicação pela primeira vez será cadastrado uma agência com um usuário administrador
- Ao criar sua conta o cliente ficará com o status pendente até que o usuário administrador aprove seu cadastro.
- Ao aprovar ou recusar, será disparado um evento de envio de e-mail (apenas simulando, não envia realmente) notificando o cliente.
- Ao aprovar, será criada uma conta bancária automaticamente vinculada ao cliente com saldo zerado.
- O cliente poderá realizar depositos online (simulado, pode-se colocar o valor que quiser) que ao cadastrado ficará como pendente, sendo adicionado na fila para ser efetuado.
- O cliente poderá realizar uma transferência para outras contas que ao solicitar a transferência ela ficará como pendente, sendo adicionada na fila para ser efetuada ou cancelada.
- Quando o depósito ou transferência forem efetuados/recusados (cancelado) será disparado um evento.
- Quando o depósito ou transferência forem efetuados com sucesso, será registrada a movimentação.

