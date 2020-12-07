### Analise Descritiva

setwd("C:/Users/Lavo/Desktop/Pós - Ciencia de Dados/03 Análise Estatística de Dados/Projeto Final")
library(tidyverse)
library(plotly)
library(e1071)
library(Hmisc)
library(esquisse)
library(DescTools)
library(gridExtra)
library(PMCMR)

## item A

bd=read_csv2("bd.analise.new.csv")

gr1 = bd %>% ggplot(aes(x=NT_GER)) + 
  geom_histogram(aes(y=..density..),fill="purple",bins=10)+
  geom_density(color="red",size=1)+
  labs(x="nota",y="frequência")+theme_minimal()+theme(axis.text.y = element_blank())+
  theme(plot.title = element_text(size = 12, face = "bold"))
gr1

gr2=bd %>% select(Turno,Regiao,NT_GER) %>% 
  ggplot(aes(x=Regiao,y=NT_GER,fill=Regiao)) + geom_boxplot(show.legend = F)+
  labs(x="turno",y="notas")+theme_minimal()+facet_wrap(~Turno,ncol=2)+
  theme_minimal()+theme(axis.text.x = element_blank())
gr2

for(n in 1:2){
  ggsave(filename=paste0("C:/Users/Lavo/Desktop/gr",n,".png"),plot=paste0("gr",n))
}

gr1 = bd %>% ggplot(aes(x=NT_GER)) + 
  geom_histogram(aes(y=..density..),fill="purple",bins=10)+
  geom_density(color="red",size=1)+
  labs(x="nota",y="frequência")+theme_minimal()+theme(axis.text.y = element_blank())+
  theme(plot.title = element_text(size = 12, face = "bold"))
gr1

ggsave(filename="C:/Users/Lavo/Desktop/gr1.png",plot=gr1)


       