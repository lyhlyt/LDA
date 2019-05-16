# LDA
library(ggsci)
library(ggthemes)
mydata<-read.csv("C:/Users/lyh/Desktop/Rdata/data11.csv",header = TRUE,sep =",")
mydata
library(ggplot2)
mydata$group = factor(mydata$group, levels=c("81~100","61~80","41~60","21~40","<20"))
mydata$Rank = factor(mydata$Rank, levels=c("3 WEEK","6 WEEK","12 WEEK","18 WEEK","24 WEEK"))
A<-ggplot(mydata,aes(x=Rank,y=ratio,fill=group))+
  geom_bar(stat="identity",position="stack", width = 0.5)+
  labs(y="Proportion (%)",x="",fill="(%)")+
  scale_fill_npg()+
  theme(title=element_text(size=15,face= "bold"),
        axis.title.y=element_text(size=12,face= "bold"),
        axis.text.x=element_text(size = 10,face = "bold"),
        axis.title.x =element_text(size=12,face= "plain"),
        axis.text.y=element_text(size =10 ,face = "bold"),
        legend.text=element_text(size=12),
        legend.title=element_text(size=12),
        legend.position="right",
        panel.background = element_rect(fill = "transparent",colour = NA),
        axis.line=element_line(size = 1,color="black"))+
  scale_y_continuous(breaks = seq(0,100,by=20))+
  geom_text(aes(x=Rank,y=label_y,label=RT),
            position='identity', color='black')
A

print("Hello world")
