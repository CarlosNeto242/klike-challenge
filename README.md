## 🛠️ Como Executar o Projeto Localmente

Siga o passo a passo abaixo para clonar o repositório, criar um ambiente virtual isolado, instalar as dependências e executar os notebooks do desafio.

### 1. Pré-requisitos
- **Python 3.10+** instalado no sistema ([download oficial](https://www.python.org/downloads/)).
- **Git** instalado.

### 2. Instalação

### Criar o ambiente virtual
Abra um terminal no Powershell e execute o seguinte comando:
- `python -m venv .venv`
E espera até que ele seja criado
### Ativar o ambiente virtual

Para adentrar o ambiente virtual, execute o seguinte comando dentro do Powershell:
- `.venv\Scripts\Activate`

### Instalar as dependências
Dentro do ambiente virtual, execute o seguinte comanto abaixo
- `pip install -r requirements.txt`

---


## 4. Visão de Produto e Próximos Passos (Product & Engineering Vision)

### 4.1. Novas Features Extraíveis de Vídeo Bruto

O dataset atual trabalha com metadados agregados e binários (`has_hook`, `has_face`, etc.). Em um produto escalável e maduro, uma esteira de inteligência artificial multimodal processaria diretamente o arquivo `.mp4` para extrair variáveis comportamentais e estruturais contínuas de altíssima granularidade:

1. **Visão Computacional e Dinâmica de Edição:**
   - **Ritmo de Cortes e Mudanças de Cena:** Frequência de transições por segundo. Em plataformas verticais como o TikTok, a transição constante entre cenários/fundos prendem mais a atenção do usuário.
   - **Contato Visual e Expressões Faciais:** Não apenas verificar a presença de um rosto, mas quais as emoções ele está transmitindo ao telespectador.
   - **Análise das HashTags presentes nos vídeos:** Identificação do tema por meio das hashtags utilizadas nos vídeos. Dessa forma, poderíamos identificar que tipo de conteúdo gera mais engajamento e assim otimizar a produção de conteúdo futuro.

2. **Processamento de Áudio e Fala (Audio & Speech AI):**
   - **Velocidade de Fala e Cadência (WPM - Words Per Minute):** Medição da cadência de fala via modelos ASR (*Whisper*), identificando pausas mortas ou trechos monótonos no início do vídeo.
   - **Classificação Semântica do Gancho (*Hook Categorization* via NLP):** Categorização do gancho inicial dos primeiros 3 segundos em arquétipos comprovados (ex: *Gancho de Dor/Problema*, *Curiosidade*, *Antes e Depois*, *Controvérsia*).
   - **Proporção Harmônica e *Trending Sounds*:** Detecção da presença de faixas comerciais genéricas versus músicas e áudios que estão em alta (*trending*) no algoritmo da plataforma no momento da veiculação.

---

### 4.2. Arquitetura de Produção e Estratégia de Deploy

Para entregar valor imediato às equipes de marketing, criação e tráfego pago, a solução foi pensada como uma aplicação web interativa, acessível e de baixa complexidade operacional:

1. Desenvolvimento de um site web utilizando o framework Django
2. Criando uma página dentro desse site contendo os campos de texto que o usuário poderá adicionar 
3. Por conta de Django funcionar com o python. Ao entrar na rota e executar um POST, criaríamos uma função para a rota da página, função que poderíamos simplesmente pegar o request.POST para obter cada campo que o usuário preencheu 
4. Com isso, pegaríamos cada campo e passaríamos ele como argumento na nossa função.
5. Renderizamos a mesma página, só que agora passamos para o HTML as respostas (`return render(request, "pagina.html, {'respostas': all_respostas})`)
6. Com o site criado, poderíamos finalmente dar deploy nele usando algum serviço para isso. Eu escolheria o Render para isso


### 4.3. O que faria com mais tempo e mais dados?

1. **Modelos Especializados por Plataforma:**
   - No projeto atual, treinamos um modelo "global" devido à limitação de dados (500 linhas no total, ou seja, "cerca" de 160 por plataforma). Com mais dados históricos e o devido tempo, a abordagem alternativa seria treinar **três modelos independentes (um para TikTok, um para Meta e outro para LinkedIn)**, capturando com precisão cirúrgica a receita de sucesso e a sensibilidade de cada rede.
2. **Uso de I.A generativa (LLM):**
   - Integrar uma API de algum modelo de linguagem (Claude Opus 5.5, Gemini Argon...) para tornar as análises ainda mais personalizadas. Com um bom "prompt" de instrução passado via código, as resposta poderiam ser mais completas e abrangir insights além daqueles que um modelo de regressão conseguiria nos dar de forma direta.
3. 

