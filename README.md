# AutomatizedGoogleDrive

O código fornecido tem como objetivo automatizar a tarefa de exportar um relatório de uma página web, baixar o arquivo resultante e, em seguida, fazer o upload desse arquivo para o 
Google Drive usando a API do Google Drive.

Aqui está um resumo detalhado de como o código funciona:

1. Importação das bibliotecas:
   - `os`, `os.path`, `shutil`, `glob`: Bibliotecas para manipulação de arquivos e diretórios.
   - `time`: Biblioteca para adicionar pausas entre as ações automatizadas.
   - `datetime`: Biblioteca para trabalhar com datas e horários.
   - `pandas`: Biblioteca para manipulação de dados em formato de planilha.
   - `selenium`: Biblioteca para automação de testes em navegadores web.
   - `webdriver_manager.chrome`: Biblioteca para gerenciar o driver do Chrome.
   - `google.oauth2.credentials.Credentials`: Classe para armazenar e gerenciar credenciais de autenticação do Google.
   - `googleapiclient.discovery.build`: Função para construir um serviço da API do Google a partir de suas informações de serviço.
   - `googleapiclient.errors.HttpError`: Classe para tratar erros da API do Google.
   - `googleapiclient.http.MediaFileUpload`: Classe para carregar arquivos de mídia para o Google Drive.
   - `google.auth.transport.requests.Request`: Classe para enviar solicitações autenticadas.
   - `google_auth_oauthlib.flow.InstalledAppFlow`: Classe para configurar o fluxo de autorização de aplicativo instalado do Google.

2. Inicialização do navegador:
   - É criada uma instância do webdriver do Chrome e o site alvo é carregado.

3. Preenchimento de campos de login:
   - Os campos de email e senha são localizados por seus nomes e preenchidos com as informações de login.

4. Efetuação do login:
   - O botão de login é clicado para efetuar o login.

5. Exportação do relatório:
   - É localizado o botão "Exportar Relatório" e clicado.

6. Download do arquivo:
   - É localizado o botão de download e clicado.

7. Movendo o arquivo baixado:
   - O caminho para a pasta de downloads é obtido e o arquivo mais recente é identificado usando a função `max` com base no tempo de criação.
   - É definido o caminho para a pasta de destino e o arquivo é movido para essa pasta usando a função `shutil.move`.

8. Autenticação com o Google Drive:
   - São definidas as constantes `SCOPES` para especificar as permissões necessárias para a API do Google Drive.
   - É feita a verificação das credenciais existentes no arquivo "token.json". Se não houver credenciais válidas, o fluxo de autorização é executado para obter novas credenciais.
   - As credenciais atualizadas são salvas no arquivo "token.json".

9. Upload do arquivo para o Google Drive:
   - É criado o serviço da API do Google Drive usando as credenciais autenticadas.
   - É especificado o ID da pasta de destino no Google Drive.
   - A pasta local é percorrida para localizar arquivos.
   - Cada arquivo encontrado é renomeado e então enviado para o Google Drive usando a função `service.files().create()` com o

 objeto `MediaFileUpload`.
   - O ID do arquivo no Google Drive é impresso como resultado.

10. Tratamento de exceções:
    - Qualquer exceção ocorrida durante a execução do código é capturada e uma mensagem de erro é exibida.

O código utiliza as seguintes bibliotecas e APIs:

- Bibliotecas Python:
  - `os`, `os.path`, `shutil`, `glob`: Para manipulação de arquivos e diretórios.
  - `time`, `datetime`: Para controle de tempo e pausas.
  - `pandas`: Para manipulação de dados em formato de planilha.
  - `selenium`: Para automação de ações em navegadores web.

- Bibliotecas do Selenium:
  - `webdriver`: Para criação e manipulação de instâncias de navegadores web.
  - `webdriver_manager.chrome`: Para gerenciar o driver do Chrome.

- Bibliotecas do Google:
  - `google.oauth2.credentials.Credentials`: Para armazenar e gerenciar credenciais de autenticação do Google.
  - `googleapiclient.discovery.build`: Para construir um serviço da API do Google a partir de suas informações de serviço.
  - `googleapiclient.errors.HttpError`: Para tratar erros da API do Google.
  - `googleapiclient.http.MediaFileUpload`: Para carregar arquivos de mídia para o Google Drive.
  - `google.auth.transport.requests.Request`: Para enviar solicitações autenticadas.
  - `google_auth_oauthlib.flow.InstalledAppFlow`: Para configurar o fluxo de autorização de aplicativo instalado do Google.

O código automatiza o processo de exportar um relatório de uma página web, fazer o download do arquivo resultante e, em seguida, fazer o upload desse arquivo para o 
Google Drive usando a API do Google Drive. Isso economiza tempo e esforço manual, permitindo que a tarefa seja executada de forma automatizada.
