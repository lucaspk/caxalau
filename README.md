# Caxalau

![](https://raw.githubusercontent.com/lucaspk/caxalau/master/Caxalau%20preditor.png)

Caxalau é o filho primogênito da entidade mitológica Mãe Milina e seu esposo Cachangalanga. Porém, no projeto em tela, ele assumirá o papel de preditor de reprovações em um conjunto de disciplinas baseado nas notas dos pré-requisitos delas. Para essa finalidade, utilizaremos redes bayesianas.

Teremos 3 modelos principais:
- o modelo gerado sem qualquer filtragem nos dados;
- o modelo gerado filtrando os dados pela nota do pré-requisito em um intervalo de um ponto. Esse é o **modelo Caxalau**. Por exemplo: se você digitar a nota 6.5 para a disciplina y, será gerado o modelo considerando dados da disciplina y em que a média ficou no intervalo fechado **[piso(média), teto(média)]**, em que *piso()* é a função piso e *teto()* é a função teto;
- o modelo gerado filtrando os dados pela nota exata fornecida para os pré-requisitos, também chamado de **modelo Safatraio**.

Nesse projeto, iremos utilizar dados do controle acadêmico da UFCG, bem como o ambiente de desenvolvimento R.

Além disso, será utilizado o package "bnlearn" que contém os procedimentos necessários relativos à rede bayesiana. Para instala-lo, basta digitar no console do RStudio:

    install.packages("bnlearn")

Estabelecemos a escala *Samarílio Samarago* em quatro níveis para mensurar o risco de reprovação, sendo eles:
- risco baixo: probabilidade <= 15%
- risco moderado: probabilidade > 15% e <= 45%
- risco alto: probabilidade > 45% e <= 65%
- risco mafra boy virado no victolino chapolithoveenetsmile: probabilidade > 65% 

## Dados escolhidos
Por questões de simplificação, serão utilizados dados das disciplinas ministradas pelos docentes do Departamento de Sistemas e Computação (DSC) da UFCG dos três primeiros períodos, já que a imputação de pré-requisitos é manual. Porém, o modelo é generalizável para toda a grade curricular.

**Resumindo**
 - Queremos prever risco de reprovação em um conjunto de disciplina no segundo período, então forneceremos as notas dos pré-requisitos do primeiro período.
 - Queremos fazer o mesmo que acima, mas agora para o terceiro período, então forneceremos as notas dos pré-requisitos do segundo período. 

## Sobre os arquivos com os dados
Arquivo **dados_alunos_cc.csv**: são os dados dos alunos de CC, de todas as disciplinas cursadas. Note que não estão todas as colunas dos dados brutos, tendo em vista que escolhemos apenas trabalhar com: *Matricula, Cod_Disciplina, Cod_Evasao, Nome_Disciplina, Media_Disciplina e Situacao*.

Arquivo **alunos_notas_simplif.csv**: são os dados no formato que será adequado ao nosso modelo preditivo de reprovações utilizando nota dos pré-requisitos.


### Todo 

- [x] Organizar esse código em arquivos distintos. As funções para manipular os dados em um script e as de manipular o modelo em outro;
- [ ] Desenvolver uma lógica adequada para generalização para várias outras disciplinas;
- [ ] Colocar para gerar o modelo para um exemplo concreto;
- [ ] Treinar os 3 modelos: 60% dados para treino e 40% teste(talvez fazer validação cruzada, o que fica 20% para vc e 20% para teste);
- [ ] Avaliar os 3 modelos. Comparar acurária e probabilidades geradas entre si;
- [ ] Web application para passar as notas em campo de texto e escolher disciplina em um dropdown ou outro selectable element. 

