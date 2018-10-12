# Caxalau

![](https://raw.githubusercontent.com/lucaspk/caxalau/master/Caxalau%20preditor.png)

Caxalau é o filho primogênito da entidade mitológica Mãe Milina e seu esposo Cachangalanga. Porém, no projeto em tela, ele assumirá o papel de preditor de reprovações em um conjunto de disciplinas baseado nas notas dos pré-requisitos delas utilizando redes bayesianas.

# Os Modelos 
Teremos 3 modelos:
- Um sem qualquer filtragem nos dados;
- Um filtrando os dados pela nota do pré-requisito em um intervalo de um ponto. Esse é o **modelo Caxalau**. Por exemplo: se você digitar a nota 6.5 para a disciplina y, será gerado o modelo considerando dados da disciplina y em que a média ficou no intervalo fechado **[piso(média), teto(média)]**, em que *piso()* é a função piso e *teto()* é a função teto;
- Um filtrando os dados pela nota exata fornecida para os pré-requisitos, também chamado de **modelo Safatraio**.

# Ferramentas
Utilizamos o ambiente de desenvolvimento **R** e o package "bnlearn" que contém os procedimentos necessários relativos à rede bayesiana. Para instalá-lo, basta digitar no console do RStudio:

    install.packages("bnlearn")
    
# Execução do Código
Basta abrir o arquivo de interesse e executar os blocos de código na ordem em que aparecerem, começando pela inicialização dos pacotes.

# Escalas de Risco de Reprovação
Estabelecemos a escala *Samarílio Samarago* em quatro níveis para mensurar o risco de reprovação, sendo eles:
- risco baixo: probabilidade <= 15%
- risco moderado: probabilidade > 15% e <= 45%
- risco alto: probabilidade > 45% e <= 65%
- risco mafra boy virado no victolino chapolithoveenetsmile: probabilidade > 65% 

# Sobre os dados
Nesse projeto, iremos utilizar dados do controle acadêmico da Universidade Federal de Campina Grande (UFCG), do curso de Ciência da Computação (CC).

### Dados escolhidos para o projeto
Por questões de simplificação, serão utilizados dados das disciplinas ministradas pelos docentes do Departamento de Sistemas e Computação (DSC) da UFCG dos três primeiros períodos, já que a imputação de pré-requisitos é manual. Porém, o modelo é generalizável para toda a grade curricular.

### Formato dos dados
Os dados brutos vêm com diversas colunas, porém selecionamos as seguintes: *Matricula, Cod_Disciplina,	Cod_Evasao, Nome_Disciplina, Media_Disciplina, Situacao*.

## Justificativa para os fatores escolhidos
Primeiro, precisamos definir o que é semelhança. No contexto dos nossos modelos preditivos propostos, ela significa:
- Que um (a) aluno (a) possui a mesma nota, no caso do **modelo Safatraio**;
- Ou que possui uma nota em um intervalo fechado de até um ponto, ou seja, [piso(média_fornecida), teto(média_fornecida)], para o **modelo Caxalau**. 

**Note** que para o modelo básico sem filtragem esse conceito de semelhança é inexistente, visto que não tomaremos qualquer fator de similaridade para predizermos o risco. 

Agora, vamos às justificativas.
- Matricula: mesmo ofuscada, servirá para filtrarmos os alunos semelhantes ao usuário;
- Cod_Disciplina: servirá de base para manipularmos as disciplinas fornecidas pelo usuário;
- Nome_Disciplina: será útil para identificação a qual disciplina o código diz respeito;
- Media_Disciplina: é a variável independente do nosso modelo. Utilizaremos ela para obtermos respostas à respeito do risco de Reprovação;
- Situacao: é a variável dependente, a qual queremos saber através do cálculo probabilístico do risco utilizando Redes Bayesianas.

**Por exemplo:**
 - Queremos prever risco de reprovação em um conjunto de disciplina no segundo período, então forneceremos as notas dos pré-requisitos do primeiro período.
 - Queremos fazer o mesmo que acima, mas agora para o terceiro período, então forneceremos as notas dos pré-requisitos do segundo período. 

## Manipulações nos dados
Removemos os dados relativos à trancamento de disciplina, visto que os valores delas eram **NA's**, além de não ser útil para nosso modelo esse tipo de situação. Além disso, transformamos todos os valores "Reprovado por Falta" para "Reprovado", visto que não nos interessa o tipo e sim o risco de ter sido Reprovado dada a similaridade entre as notas.


# Sobre os arquivos com os dados
Arquivo **dados_alunos_cc.csv**: são os dados dos alunos de CC, de todas as disciplinas cursadas. Note que não estão todas as colunas dos dados brutos, tendo em vista que escolhemos apenas trabalhar com: *Matricula, Cod_Disciplina, Cod_Evasao, Nome_Disciplina, Media_Disciplina e Situacao*.

Arquivo **alunos_notas_simplif.csv**: são os dados no formato que será adequado ao nosso modelo preditivo de reprovações utilizando nota dos pré-requisitos.

# Créditos
Projeto desenvolvido por Arthur Vinícius Rodrigues, João Victor Mafra e Jobson Lucas Dias.

