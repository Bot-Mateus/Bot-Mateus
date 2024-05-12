

# Integração da Inteligência Artificial Gemini no WhatsApp

## Descrição

Este projeto visa integrar a inteligência artificial Gemini ao WhatsApp do usuário comum, permitindo aos usuários fazerem perguntas de forma simples e receberem respostas rápidas e precisas da IA.

Resumindo, sua tia pode usar o Gemini para pedir uma receita de bolo ou uma ajuda com a mensagem de bom dia. O objetivo é usar uma plataforma altamente usada e conhecida para democratizar o uso da IA.

Facilitem o acesso do Gemini para seus avós e tios que tem dificuldades com essas coisas de tecnologia, basta seguir esses passos.

*obs: infelizmente não tenho dinheiro para bancar os gastos com hospedagem e uso da API Gemini, se não era só chamar no zap...*
## Funcionalidades Principais

- **Benefício Principal**: A integração da IA Gemini com o WhatsApp facilita o acesso a uma IA avançada para pessoas mais velhas e leigas em tecnologia. Ao utilizar uma plataforma familiar como o WhatsApp, os usuários podem interagir com a IA de maneira intuitiva e conveniente, sem a necessidade de aprender novas interfaces ou tecnologias complicadas.
-   **Interação Simples**: Os usuários podem fazer perguntas para a inteligência artificial Gemini diretamente pelo WhatsApp.
-   **Respostas Rápidas**: As respostas são geradas instantaneamente, proporcionando uma experiência fluida ao usuário.
-   **Suporte a Diferentes Perguntas**: A inteligência artificial é capaz de lidar com uma variedade de perguntas, incluindo imagens e fornecer respostas relevantes.

# Exemplos de uso
Aqui teremos alguns exemplos de uso da aplicação, mostrando como ela pode ser útil no seu dia dia.

### Ajuda com legenda para o Instagram
![Legenda para Instagram](https://github.com/Bot-Mateus/zapgemini/blob/main/Imagens%20dos%20Testes%20-%20zapgemini/legenda-instagram.jpg)
### Criar resumos
![Criar resumos](https://github.com/Bot-Mateus/zapgemini/blob/main/Imagens%20dos%20Testes%20-%20zapgemini/resumo-filme.jpg)
### Transcrever e interpretar imagens
![Transcrever imagens](https://github.com/Bot-Mateus/zapgemini/blob/main/Imagens%20dos%20Testes%20-%20zapgemini/transcrever-imagem.jpg)
### Criar mensagens com base em imagens
![Criar mensagens](https://github.com/Bot-Mateus/zapgemini/blob/main/Imagens%20dos%20Testes%20-%20zapgemini/texto-base-imagem.png)
## Índice

-   [Rodar a Aplicação](https://github.com/Bot-Mateus/Bot-Mateus/edit/main/README.md#rodar-a-aplica%C3%A7%C3%A3o)
-   [Funcionamento do Programa](https://github.com/Bot-Mateus/Bot-Mateus/edit/main/README.md#funcionamento-do-programa)
    -   [Módulo main.py](https://github.com/Bot-Mateus/Bot-Mateus/edit/main/README.md#m%C3%B3dulo-mainpy)
    -   [Módulo gemini_response.py](https://github.com/Bot-Mateus/Bot-Mateus/edit/main/README.md#m%C3%B3dulo-gemini_responsepy)
    -   [Módulo whatsapp_user_automator.py](https://github.com/Bot-Mateus/Bot-Mateus/edit/main/README.md#m%C3%B3dulo-whatsapp_user_automatorpy)
    -   [Módulo selenium_utils.py](https://github.com/Bot-Mateus/Bot-Mateus/edit/main/README.md#m%C3%B3dulo-selenium_utilspy)
-   [Melhorias Futuras](https://github.com/Bot-Mateus/Bot-Mateus/edit/main/README.md#melhorias-futuras)
-   [Como me encontrar](https://github.com/Bot-Mateus/Bot-Mateus/edit/main/README.md#como-me-encontrar)

## Rodar a Aplicação
No momento, o número utilizado no projeto não é público, mas caso você queira utilizar o Gemini no seu WhatsApp, pode seguir esses passos de instalação:

**Baixar os Arquivos**: Clone ou baixe os arquivos do projeto do repositório do GitHub:

```git
git clone https://github.com/Bot-Mateus/zapgemini.git
```

-   **Alterar a API Key**: Abra o arquivo `gemini_response.py` e substitua a chave de API existente pela sua chave pessoal. Isso garantirá que a aplicação faça uso correto da API Gemini. 

- Se tiver dúvidas sobre a API Key consulte esse site [[Obter chave da API]](https://ai.google.dev/gemini-api/docs/api-key?hl=pt-br&_gl=1*poxqt0*_up*MQ..&gclid=CjwKCAjwrvyxBhAbEiwAEg_Kgr8mEA92mgSSTobUgwxlwEqsmr70kmUZO7y2s0zP_cmHGEHQ54uDExoCcsUQAvD_BwE)

```python
GOOGLE_API_KEY = "SUA_API_KEY"
```
    
-   **Instalar Dependências**: Certifique-se de ter instalado todas as dependências necessárias. Você pode instalá-las executando o seguinte comando no terminal:

```python
pip install -r requirements.txt
```

**Executar o Programa**: Execute o arquivo `main.py` para iniciar a aplicação:

```python
python main.py"
``` 
    
-  **Adicionar o Contato**: Adicione o número de telefone associado à inteligência artificial Gemini em seus contatos do WhatsApp.

- **Atenticação**: Inicie a aplicação Flask 
  - acesse http://127.0.0.1:5000/ e faça a autenticação. 
    
-   **Fazer Perguntas**: Inicie uma conversa com o contato da inteligência artificial no WhatsApp e envie suas perguntas no formato de mensagens de texto simples ou com uma imagem com descrição, a descrição será sua pergunta a respeito da imagem.
    
-   **Receber Respostas**: Você receberá as respostas da inteligência artificial Gemini em pouquissimos segundos.


# Funcionamento do Programa
O programa possui uma interface web simples, responsável por ligar e desligar o bot e autenticar o Gemini no número de WhatsApp desejado.

Neste capítulo irei tentar resumir os módulos mais relevantes, informando brevemente o que cada coisa faz.

![Interface web](https://github.com/Bot-Mateus/zapgemini/blob/main/Imagens%20dos%20Testes%20-%20zapgemini/interface.png)
## Módulo main.py

Este módulo implementa a lógica principal da aplicação Flask responsável por controlar a ativação e desativação do robô Gemini no WhatsApp, bem como fornecer informações sobre o status atual do robô.

### Funcionalidades Principais:

-   **Iniciar o Robô em uma Thread Separada**: A função `iniciar_em_thread()` é responsável por iniciar o robô em uma thread separada, permitindo que a aplicação continue a responder enquanto o robô é inicializado.
    
-   **Ativar o Robô**: A rota `/toggle_ai` permite ativar o robô para um determinado usuário. Se o robô já estiver ativo, retorna uma mensagem de erro.
    
-   **Desativar o Robô**: A rota `/desativar_funcao/<username>` permite desativar o robô para um usuário específico.
    
-   **Atualizar a Autenticação**: A rota `/update_autenticacao/<username>` permite atualizar a autenticação do usuário.
    
-   **Verificar o Status do Robô**: A rota `/status_bot/<username>` retorna o status atual do robô para um usuário específico.
    

### Bibliotecas Utilizadas:

-   `threading`: Utilizada para iniciar o robô em uma thread separada.
-   `Flask`: Utilizada para criar a aplicação web e definir rotas.
-   `render_template`, `jsonify`, `request`, `redirect`, `url_for`, `flash`, `session`: Utilizadas para manipulação de requisições e renderização de templates HTML.
-   `automation_status`: Contém funções relacionadas ao status do robô.
-   `whatsapp_user_automator`: Contém funções para iniciar e desativar o robô no WhatsApp.

### Execução:

O arquivo `main.py` pode ser executado diretamente. Ele iniciará o servidor Flask em modo de depuração (`debug=True`), permitindo o desenvolvimento e teste da aplicação.

## Módulo gemini_response.py

Este módulo contém funções para enviar consultas para a inteligência artificial Gemini e receber respostas, tanto em texto quanto em imagem.

### Funcionalidades Principais:

-   **Quebra de Linha**: A função `break_line(message)` é responsável por substituir quebras de linha em mensagens por um caractere especial reconhecido pelo WhatsApp.
    
-   **Resposta de Texto do Gemini**: A função `gemini_response_text(message)` envia uma mensagem para a inteligência artificial Gemini e retorna a resposta em formato de texto.
    
-   **Resposta de Imagem do Gemini**: A função `gemini_response_image(message, image)` envia uma mensagem e uma imagem para a inteligência artificial Gemini e retorna a resposta em formato de texto.
    

### Bibliotecas Utilizadas:

-   `PIL.Image`: Utilizada para manipular imagens.
-   `google.generativeai`: Utilizada para acessar a inteligência artificial Gemini.
-   `selenium.webdriver.Keys`: Utilizada para simular teclas de atalho no navegador.

### Configuração da API:

A variável `GOOGLE_API_KEY` armazena a chave de API necessária para acessar a inteligência artificial Gemini.

### Modelos Utilizados:

-   `gemini-1.0-pro`: Modelo utilizado para respostas de texto.
-   `gemini-pro-vision`: Modelo utilizado para respostas de imagem.

### Configurações de Geração:

-   `candidate_count`: Número de candidatos a serem gerados pela inteligência artificial.
-   `temperature`: Parâmetro de "temperatura" que controla a diversidade das respostas geradas.

### Configurações de Segurança:

-   Configurações de segurança são aplicadas para evitar a geração de conteúdo impróprio, como discurso de ódio, assédio, conteúdo sexualmente explícito ou perigoso.

## Módulo whatsapp_user_automator.py

Este módulo é responsável por automatizar a interação do robô Gemini no WhatsApp, incluindo a autenticação, o envio de mensagens e a obtenção de respostas.

### Funcionalidades Principais:

-   **Configuração do Navegador**: A função `configurar_navegador_gemini(username)` configura o navegador para interagir com o WhatsApp Web.
    
-   **Verificar Status do Bot**: A função `verificar_bot_ativo()` verifica se o bot Gemini está ativo.
    
-   **Desativar Bot**: A função `desativar(username)` desativa o bot Gemini e fecha o navegador.
    
-   **Iniciar Bot**: A função `iniciar()` inicia o bot Gemini, autentica-se no WhatsApp Web e interage com as conversas.
    
-   **Responder a Mensagens**: O bot responde automaticamente às mensagens dos usuários, usando a inteligência artificial Gemini para gerar respostas em texto ou imagem.
    

### Bibliotecas Utilizadas:

-   `selenium.common`: Utilizada para lidar com exceções comuns do Selenium.
-   `selenium.webdriver.common.by`: Utilizada para selecionar elementos por diferentes estratégias de localização.
-   `time`: Utilizada para inserir pausas na execução do código.
-   `selenium.webdriver.support.ui`: Utilizada para aguardar a presença de elementos na página.
-   `selenium.webdriver.support.expected_conditions`: Utilizada para definir condições de espera para elementos específicos.
-   `verificador_elementos_html`: Contém funções para encontrar elementos HTML de forma segura.
-   `selenium_utils`: Contém funções utilitárias para interagir com o Selenium.
-   `automation_status`: Contém funções relacionadas ao status da automação.
-   `gemini_response`: Contém funções para obter respostas da inteligência artificial Gemini.

### Variáveis Globais:

-   `bot_ativo`: Variável global que indica se o bot Gemini está ativo.
-   `browser_ativo`: Variável global que indica se o navegador está ativo.
-   `browser`: Variável que armazena a instância do navegador Selenium.

### Configuração do Navegador:

-   A função `configurar_navegador_gemini(username)` configura o navegador para interagir com o WhatsApp Web, incluindo a autenticação com o QR code.

### Fluxo de Execução:

-   O bot inicia a interação com o WhatsApp Web, autentica-se e aguarda a chegada de novas mensagens.
-   Quando uma nova mensagem é recebida, o bot responde automaticamente usando a inteligência artificial Gemini.
- Após responder o chat é fechado e o bot aguarda uma nova mensagem aparecer.

## Módulo selenium_utils.py

Este módulo fornece funcionalidades para automatizar interações com o WhatsApp Web, incluindo configuração do navegador, captura de tela, envio de respostas e obtenção de informações do usuário.

### Funcionalidades Principais:

-   **Configuração do Navegador**: A função `configurar_navegador(username)` configura o navegador para interagir com o WhatsApp Web, suportando tanto o Edge no Windows quanto o Firefox no Linux.
    
-   **Captura de Tela do QR Code**: A função `tirar_screenshot_qr_code(driver, nome_arquivo, tempo_espera)` captura o QR code da tela do WhatsApp Web e salva como imagem.
    
-   **Captura de Tela de Imagem**: A função `tirar_screenshot_foto(driver)` captura a tela de uma imagem recebida no chat e a salva como arquivo de imagem.
    
-   **Conexão com Número**: A função `conectar_com_numero(browser, numero)` permite a conexão do navegador com um número específico do WhatsApp.
    
-   **Envio de Resposta**: A função `enviar_resposta(browser, mensagem)` envia uma mensagem de resposta ao usuário no chat do WhatsApp.
    
-   **Obtenção de Resposta do Usuário**: A função `obter_resposta_usuario(browser)` obtém a última mensagem enviada pelo usuário no chat do WhatsApp.
    
-   **Obtenção de Resposta do Bot**: A função `obter_resposta_bot(browser)` obtém a última mensagem enviada pelo bot Gemini no chat do WhatsApp.
    
-   **Obtenção de Número do Usuário**: A função `obter_numero(browser)` obtém o número de telefone do usuário a partir do perfil no WhatsApp Web.
    

### Bibliotecas Utilizadas:

-   `selenium`: Utilizada para automatizar interações com o navegador web.
-   `PIL`: Utilizada para processar e manipular imagens.
-   `datetime`: Utilizada para manipulação de datas e horas.
-   `requests`: Utilizada para fazer requisições HTTP.
-   `uuid`: Utilizada para gerar identificadores únicos.
-   `os`: Utilizada para manipulação de arquivos e diretórios.
-   `platform`: Utilizada para obter informações sobre o sistema operacional.

### Configuração do Navegador:

-   O navegador é configurado de acordo com o sistema operacional do usuário, suportando o Edge no Windows e o Firefox no Linux.

### Fluxo de Execução:

-   O módulo inicia configurando o navegador e realiza as interações necessárias com o WhatsApp Web.
-   As funções são projetadas para capturar informações do usuário, enviar respostas automáticas, e obter e processar imagens e mensagens do chat.

# Melhorias Futuras
O projeto ainda está em desenvolvimento e desejo fazer muitas melhorias, a principal delas é fazer com que a automação funcione dentro do contato pessoal do usuário, desse jeito qualquer um poderá ter acesso ao Gemini, basta iniciar uma conversa com você mesmo, e não terá a necessidade de existir um número dedicado para ele.

Irei acrescentar funções para automatizar a interação do bot em grupos, desse jeito ele pode servir para diversos fins, desde um "administrador" até um "professor" que ajuda com as dúvidas dos alunos quando o verdadeiro professor está indisponível.

Partes do código para essas melhorias já estão escritas, como o botão "autenticar com celular", a verificação para saber se a mensagem recebida é de um grupo ou usuário individual... mas não estão 100% funcionais. 

Com o tempo trarei novas atualizações do projeto aqui.

Obrigado pela sua atenção e paciência.

# Como me encontrar

<p align="left">
<!-- <a href="https://elbrusagency.com/"><img src="https://img.shields.io/badge/-elbrusagency.com-3423A6?style=flat&logo=Google-Chrome&logoColor=white"/></a> -->
<a href="https://www.linkedin.com/in/mateus-carvalho-da-silva/"><img src="https://img.shields.io/badge/-Mateus%20Carvalho-0077B5?style=flat&logo=Linkedin&logoColor=white"/></a>
<a href="mailto:carvalho.silva2001@gmail.com"><img src="https://img.shields.io/badge/-carvalho.silva2001@gmail.com-D14836?style=flat&logo=Gmail&logoColor=white"/></a>
<a href="https://www.instagram.com/mateusoaksilva/"><img src="https://img.shields.io/badge/-@mateusoaksilva-E4405F?style=flat&logo=Instagram&logoColor=white"/></a>
</p>

