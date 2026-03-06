# Teste-QA-4blue

## Bug N°1: Severidade Crítica, Prioridade Alta
Titulo: Login > Criar Conta - Validação de campos não sendo realizada.

Descrição: Identificado nos testes que os campos na tela de cadastro não contém validações e nem obrigatoriedade de preenchimento, bem como não contém limite de caracteres para os campos, como por exemplo:

  Ex¹.: Campo de "Nome Completo"
  
	1. Não é de preenchimento obrigatório.
	2. Permite inserir qualquer quantidade caracteres.

  Ex².: Campo "Telefone"
  
	1. Não é de preenchimento obrigatório.
	2. Permite inserir letras.
	3. Não valida se o número preenchido é válido ou não.

  Ex³.: Campo "E-mail"
  
	1. Não é de preenchimento obrigatório.
	2. Permite inserir qualquer tipo de caractere.
	3. Não verifica se o e-mail é válido.

  Ex⁴.: Campo "Senha" e "Confirmar Senha"
  
	1. Não é de preenchimento obrigatório.
	2. Não valida se o preenchimento do campo cumpre as regras de no mínimo 8 caracteres e ao menos 1 caractere especial.
	3. Não valida se ambos os campos estão preenchidos corretamente, ou seja, se ambos estão iguais.

Evidência:
  https://jam.dev/c/074a6e8a-9180-48c4-9634-7e2d62d93fb4

É esperado que, ao realizar o cadastro de usuário sejam realizadas algumas validações e limitações para que ao ser utilizado pelo usuário a tela funcione da seguinte forma:

	1. Campos deveriam ser de preenchimento obrigatório, sendo destacados caso o usuário tente finalizar o cadastro sem realizar o preenchimento dos mesmos.
	2. Uma limitação de caracteres nos campos, impedindo que seja inserido mais que 11 caracteres no campo de telefone por exemplo (DD + Número), ou no campo de Nome e E-mail a depender do tipo do campo no banco de dados.
	3. Campo de E-mail por exemplo, deveria validar se o e-mail inserido é válido, pois por padrão fornecedores desse serviço como Outlook, Gmail ou Yahoo não permitem o cadastro de e-mails com ponto final antes do arroba entre outros caracteres especiais que não são permitidos. Ou seja, implementação de uma Regex.
	4. Validar se o preenchimento do campo Senha cumpre os pré-requisitos previamente definidos que são mínimo de 8 caracteres e ao menos 1 caractere especial.
	5. Validar se o preenchimento do campo Confirmar Senha corresponde com o preenchimento do campo Senha, ou seja, verificar se ambos os campos estão preenchidos iguais.

------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

# Bug N°2: Severidade Alta, Prioridade Alta
Titulo: Login - Validação de preenchimento dos campos.

Descrição: Identificado nos testes que os campos na tela de Login não estão validando se estão preenchidos, apenas realiza a validação de Login verificando se há cadastros com o e-mail informado, permitindo assim que, caso haja um cadastro de usuário com as informações vazias (Vide Erro N°3) é possível realizar login no sistema, da seguinte forma:

	1. Abrir a tela de Login.
	2. Não preencher o campo de E-mail nem o campo de Senha.
	3. Clicar no botão "Entrar".

Com isso será redirecionado para a tela de Sucesso no login caso haja um cadastro realizado conforme relatado no Erro N°3, ou exiba o pop-up informando que a conta não foi encontrada e deve ser criado uma conta primeiro caso não haja um cadastro realizado conforme relatado no Erro N°3.

Evidência:
  https://jam.dev/c/3ebcdd86-ac4c-4f98-b468-393da8d293ed
  https://jam.dev/c/7fd8b725-418f-47f6-853b-55ca1e677a3e

É esperado que, ao realizar uma tentativa de Login com os campos vazios, os mesmos sejam destacados e informado ao usuário que os campos devem ser preenchidos, ao invés de seguir para o login propriamente dito.

------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

# Bug N°3: Severidade Média, Prioridade Média
Titulo: Login > Criar Conta - Cadastro de Login com campos vazios.

Descrição: Identificado nos testes que está sendo possível realizar um cadastro sem preenchimento dos campos. Para reproduzir o erro é necessário:

	1. Acessar a tela de Login.
	2. Clicar na opção "Criar conta" presente na parte inferior.
	3. Clicar no botão "Criar conta" sem realizar o preenchimento dos campos presentes na tela.

Com isso será redirecionado para a tela de sucesso ao realizar o cadastro e agora é possível realizar o login sem preenchimento dos campos de login apenas clicando no botão "Entrar" (Vide Erro N°2).

Evidência:
  https://jam.dev/c/d713f558-7a12-496d-9342-5ff9f0110783

É esperado que ao realizar uma tentativa de cadastro com um ou mais campos sem preenchimento, o cadastro não seja finalizado e informe ao usuário que existem campos sem preenchimento, destacando assim os campos que necessitam serem preenchidos para prosseguir com o cadastro.

------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

# Bug N°4: Severidade Média, Prioridade Baixa
Titulo: Login > Criar Conta - Sobreposição de campos na tela de cadastro.

Descrição: Identificado nos testes que os campos na tela de cadastro estão se sobrepondo, dificultando visualmente o preenchimento dos campos e a experiencia do usuário.

	1. Acessar a tela de Login.
	2. Utilizar a opção "Criar conta" presente na parte inferior.

Com isso será redirecionado para a tela de cadastro, onde é possível visualizar a sobreposição dos campos.

Evidência:
  https://jam.dev/c/0f418340-c148-4926-aef7-1ba025276323

É esperado que nessa tela, os campos não se sobreponham uns aos outros, tendo o campo Telefone abaixo do campo Nome Completo, bem como o campo Confirmar Senha abaixo do campo Senha.

------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

# Bug N°5: Severidade Baixa, Prioridade Baixa
Titulo: Login > Mensagem de erro e sucesso simultâneo

Descrição: Identificado que após a realização do login, e exibido a mensagem de sucesso ao logar bem como uma mensagem de Erro na parte inferior esquerda da tela.

Acessar a tela de Login.
Informar um E-mail e Senha previamente cadastrados.
Clicar no botão "Entrar".

Com isso será redirecionado para a tela de sucesso bem como será exibido uma mensagem de erro na parte inferior direita da tela.

Evidência:
  https://jam.dev/c/96bb86c0-923c-4d3a-9ce0-d024275728f2

É esperado que ao realizar o login com e-mail e senha válido, seja redirecionado para a tela de sucesso sem a ocorrência de erros.

------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

Para a Correção dos bugs, acredito que a prioridade seja do Bug N°1, pois é o ponto mais crítico no microssistema apresentado e com a correção do mesmo na implementação de Regex e demais validações dos campos, é possível que o Bug N°3 não ocorra mais, bem como a parte de Login sem informar E-mail e Senha relatados no Bug N°2. Após a correção do Bug N°1, seguiria para a correção do Bug N°4 pois após a correção do N°1, o N°3 não deve ocorrer mais bem como a severidade do N°2 diminua pois não seria mais possível realizar login no sistema sem e-mail e senha, agora obrigatórios no cadastro. Finalizando com a correção do Bug N°2 e depois o Bug N°5, ficando da seguinte ordem de mais prioritário para menos prioritário, Bug N°1>Bug N°4>Bug N°2>Bug N°5 e validando se o Bug N°3 ainda ocorre após a correção no Bug N°1.

E para finalizar, uma sugestão de melhoria seria na parte do cadastro de Senha, ao invés de ser apenas mínimo de 8 caracteres e 1 caractere especial, implementaria obrigatoriedade de ao menos 1 letra maiúscula, 1 minúscula, 1 número, não conter sequencia de números e nem utilizar parte do nome na senha. Bem como colocar uma confirmação visual abaixo do campo de senha, que ao decorrer que vai preenchendo os requisitos eles vão sendo marcados.
