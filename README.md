# Caxalau

![](https://raw.githubusercontent.com/lucaspk/caxalau/master/Caxalau%20preditor.png)

Caxalau é o filho primogênito da entidade mitológica Mãe Milina e seu esposo Cachangalanga. Porém, no projeto em tela, ele assumirá o papel de preditor de reprovações em um conjunto de disciplinas baseado nas notas dos pré-requisitos delas. Para essa finalidade, utilizaremos redes bayesianas.

Nesse projeto, iremos utilizar dados do controle acadêmico da UFCG, bem como o ambiente de desenvolvimento R.

Além disso, será utilizado o package "bnlearn" que contém os procedimentos necessários relativos à rede bayesiana. Para instala-lo, basta digitar no console do RStudio:

    install.packages("bnlearn")

Estabelecemos a escala *Samarílio Samarago* em quatro níveis para mensurar o risco de reprovação, sendo eles:
- risco baixo: probabilidade <= 15%
- risco moderado: probabilidade > 15% e <= 45%
- risco alto: probabilidade > 45% e <= 65%
- risco mafra boy fantasiado de victolino chapolithoveenetsmile: probabilidade > 65% 
