# Challenge Telecom X - (Oracle Next Education - ONE):

Repositório diz respeito ao segundo desafio (Challenge) especializado em Data Science do Programa Oracle Next Education 2025 - G8. No seguinte desafio, é proposto ao estudante avaliar os dados de uma companhia telefônica chamada **Telecom X**, descobrir padrões nas evasões de clientes e produzir alguns insights para a empresa.

## 🚩 **Objetivos Gerais:**

Com base nos dados disponibilizados pela Alura, foram propostas as
seguintes análises:

- I. Extração de Dados via API
- II. Limpeza e Tratamento de Informações
- III. Análise exploratória das informações estudadas
- IV. Conclusões e Insights
- V. Recomendações para a empresa

## 💾 **Informações sobre Instalação:**

> Caso o projeto seja rodado localmente em um arquivo.ipynb, serão necessários os seguintes softwares:

-  Python 3.8+
- Ambiente Python como *Jupyter Notebook* ou IDEs como *Visual Studio Code*.
- Biblioteca *pandas*
- Biblioteca *matplotlib*
- Biblioteca *numpy*
- Biblioteca *seaborn*
- data/dadosAPI/TelecomX_Data.json *(Diretório contendo dados)*

> Caso a intensão for rodar o arquivo via **Google Colab**, basta fazer upload do arquivo **TelecomX_BR.ipynb** no Google Drive e então executá-lo (Clicar em *Executar Tudo* via Colab).

## 🗂️ **Arquivos presentes no repositório:**

Único arquivo necessário para rodar projeto em nuvem ou localmente é o arquivo **TelecomX_BR.ipynb**, pois o próprio puxa dados de um outro repositório da própria Alura.

A estrutura abaixo mostra todos os arquivos contidos no diretório.

- 📂 data/
    - 📂 dadosAPI/
        - TelecomX_Data.json
        - TelecomX_dicionario.md
- 📂 images/
    - ... Todas as imagens de gráficos gerados durante o challenge.
- README.md
- TelecomX_BR.ipynb

## 📋 **Análises Geradas (*presentes no relatório final*):**

> <p>NOTA IMPORTANTE:</p> Relatório também disponível no arquivo TelecomX_BR.ipynb.

#### **1. Introdução:**

- **Problema osbservado:** Ao analisar o dataset, é informado que há um grau alto de evasão nos clientes da **Telecom X**.
- **Objetivo da Análise:**
No Challenge em questão, foi passada a mim a tarefa de descobrir padrões relacionados a evasão de clientes na empresa **Telecom X**; e com base em tais descobertas, a equipe de Data Science poderá então produzir modelos para melhor retenção de usuários.

#### **2. Limpeza e Tratamento de Dados:**

Nas primeiras etapas do Challenge, foi priorizado obter conhecimento de como o dataset disponibilizado pela Alura/Oracle funciona. Foram realizados os seguintes passos:

- 1) *Extração dos dados via API:*
    - Foi baixado o arquivo.json contendo os dados a respeito do Challenge. O arquivo em si tem o nome **TelecomX_Data.json**.
    - Em seguida, o mesmo foi armazenado em uma pasta específica do repositóro por mim criado. Portanto, o arquivo está disponível atualmente em: **data/dadosAPI/TelecomX_Data.json**.
- 2) *Limpeza e Tratamento de Dados:*
    - Depois de extraído, os componentes do dataset foram estudados por mim, para melhor compreensão das informações presentes no mesmo. Avaliei a necessidade delas serem normalizadas, apagadas, se haviam informações vazias, dados inadequados etc.
    - Entre os principais passos do tratamento de informações, houve a normalização de colunas compactadas por meio do método **pd.json_normalize()**. Usado para desaglutinar dados e os inserir na forma de informações descompactadas em um dataset reajustado, organizando tais informações descompactadas pelo ID de cada usuário.
    - Em seguida, foi-se utilizado o método **dataframe.unique()** e outros para observar tipos de informações preenchidas por coluna. Feito isso, informações vazias ou inadequadas foram removidas do dataset. Logo depois, foi feita uma cópia dele, a qual qualquer informação string do tipo **"Yes"/"No"** foi substituída por **1** e **0** para facilitar manipulações futuras.

#### **3. Análise Exploratória de Dados:**

Certos padrões foram notados entre os usuários evasores da empresa, segue abaixo a apresentação e contextualização do mesmos. A primeira observação feita, foi com relação à porcentagem de evasão. Viu-se que aproximadamente 1/4 dos clientes (*26.6%*) evadiram:

##### **Figura 1: Planos ativos e cancelados:**

![porcentagem_evasores](https://raw.githubusercontent.com/Megalonnix/ChallengeTelecomX/refs/heads/master/images/imagens_relatorio/img1.png)

Foi então analisado quais grupos estavam entre os maiores evasores, com base no **tipo de contrato do cliente** foi descoberto o seguinte: a maior parte das evasões vem de contratos baseados em **cobrança mensal**.

##### **Figura 2: Evasões por tipo de contrato:**

![contratos_evasores](https://raw.githubusercontent.com/Megalonnix/ChallengeTelecomX/refs/heads/master/images/imagens_relatorio/img2.png)

Com base na descoberta acima, fui instigado a fazer análises com relação a distribuição de valores, pagos por clientes que possuiam certo tipo de contrato. De fato, nota-se pelo *gráfico abaixo*, que clientes com contrato **Month-to-month** tendem a pagar taxas diárias mais altas que clientes de outros tipos:

> ⚠️ **Aviso:** Dada a *figura 3* ser muito grande, recomenda-se clicar com o botão direito na mesma, e depois
escolher "Abrir imagem num novo separador".

##### **Figura 3: Distribuição de valores pagos por assinantes de determinados tipos de contrato:**

![dist_contratos_evasores](https://raw.githubusercontent.com/Megalonnix/ChallengeTelecomX/refs/heads/master/images/imagens_relatorio/img3.png)

Observou-se também (baseado na *figura 4*) que a **diferença entre evasores e não evasores**, presentes nos três grupos acima é *elevada*. A *figura 4* mostra como *todos os grupos evasores tendem a pagar maiores valores*, e **como usuários Month-to-month tendem a serem os que mais evadem**:

##### **Figura 4: Distribuição de valores pagos por assinantes de determinados tipos de contrato (Evasores & Não Evasores):**

![porcentagem_evasores2](https://raw.githubusercontent.com/Megalonnix/ChallengeTelecomX/refs/heads/master/images/imagens_relatorio/img5.png)

Além de discrepâncias com base no tipo de contrato, busquei outras possíveis relações, tal como diferenças entre gênero dos usuários, método de pagamento, entre outras.

Abaixo seguem as análises com maior discrepância no número de evasores e não evasores. A *categoria de pagamentos por Cheque Eletrônico é a que mais apresenta evasões*. A *figura 5* mostra tal situação.

##### **Figura 5: Distribuição de valores pagos por assinantes por Método de Pagamento (Evasores & Não Evasores):**

![porcentagem_evasores3](https://raw.githubusercontent.com/Megalonnix/ChallengeTelecomX/refs/heads/master/images/imagens_relatorio/img6.png)

Outro fator relevante visto foi a taxa de retenção de clientes por tempo de contrato em meses.

##### **Figura 6: Distribuição na duração em de meses de contrato por assinantes (Evasores & Não Evasores):**

![qtd_evasores4](https://raw.githubusercontent.com/Megalonnix/ChallengeTelecomX/refs/heads/master/images/imagens_relatorio/img7b.png)

Observa-se, com base na *figura 6* acima, que a maior parte dos evasores são pessoas com poucos meses de contrato.

Após tais observações terem cido feitas, outra dúvita veio em mente. **Quais são os serviços mais usados por evasores?**

Com base na *figura 7* abaixo, conclui-se que os *serviços mais utilizados por clientes evasores* são:

- **1º Lugar:** Serviço de Internet;
- **2º Lugar:** Serviço de Telefone;
- **3º Lugar:** Múltiplas Linhas Telefônicas;

##### **Figura 7: Quantidade (%) de evasores por tipo de serviço:**

![qtd_evasores4](https://raw.githubusercontent.com/Megalonnix/ChallengeTelecomX/refs/heads/master/images/imagens_relatorio/img8.png)

Complementando o gráfico da *figura 7*, o gráfico da *figura 8* evidencia como clientes, usuários dos **três serviços mais usados por evasores**, tendem a pagar taxas diárias por uso de serviço **mais altas**.

##### **Figura 8: Distribuição de taxas diárias pagas pelos 3 serviços mais usados por Evasores (Comparando também com Não Evasores):**

![dist_evasores5](https://raw.githubusercontent.com/Megalonnix/ChallengeTelecomX/refs/heads/master/images/imagens_relatorio/img9.png)

#### 📋**Conclusões e Insights:**

Com base nas análises mostradas acima, podemos observar os principais padrões ligados a evasão:
- **1º:** Contratos baseados em pagamento mensal;
- **2º:** Evasores tendem a pagar maiores taxas diárias;
- **3º:** A maior parte dos evasores tendem a usar como método de pagamento Cheque Eletrônico;
- **4º:** A maioria dos evasores não permaneceram muitos meses;
- **5º:** A maioria dos evasores usa em grande parte serviços para uso de Internet e Telefone, considerando até múltiplas linhas telefônicas.

É possível que as altas taxas pagas por evasores, estejam justamente ligadas ao uso de serviços de telefonia e internet dos mesmos.

#### **Recomendações:**

Com base nos padrões captados, talvez a empresa **Telecom X** pudesse oferecer bônus cumulativos por quantidade de linhas telefonicas abertas. Além de estimular pacotes de internet e telefonia com bônus, baseados em uma maior quantidade de meses de assinatura. Quanto maior o tempo de assinatura do cliente, mais descontos ou benefícios o mesmo ganharia da empresa.