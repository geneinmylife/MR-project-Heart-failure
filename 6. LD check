####LD_check

input <- read_excel("LD_check_input.xlsx",sheet=1)
input$SNP
outcome <- read.table("outcome.txt",sep="\t",header=FALSE)

i<-1

for (i in 1:nrow(input)){
  print(i)
  
  c <- NULL 
  d <- input[i,]
  
  rsid <- input$SNP[i]
  chr<-input$CHR[i]
  p1<-input$Lower[i]
  p2<-input$Upper[i]
  data<-outcome[outcome$chr==chr &outcome$position>p1 & outcome$position<p2,]
  
  try(data <- data[order(data$p_value),])
  try(data <- data[data$p_value<1E-3,])
  try(if(nrow(data)>=500){data <- data[1:499,] })
  
  if (nrow(data)!=0){
    rsid <- as.character(unlist(d[1,6]))
    snp <- append(as.character(unlist(data$snp)), rsid)
    
    a <- NULL
    attempts <- 0
    while(attempts<=10){    
      try(a <- ld_matrix(snp))  
      if(is.null(a)){
        attempts<-attempts+1}
      else{
        break
      }
    }
    
    if(is.null(nrow(a))==TRUE){
      c <- as.data.frame(cbind(as.character(unlist(d[1,6])), as.character(unlist(d[1,1])),rsid, 1 ) )
    } else {
      col.index <- which(grepl(rsid,colnames(a)))
      b <- (a[,col.index])^2
      b <- b[order(b)]
      b <- b[(length(b)-1)] 
      c <- as.data.frame(cbind(as.character(unlist(d[1,6])),as.character(unlist(d[1,1])), names(b), as.character(unlist(b))) )
    }
    
  } else {
    c <- as.data.frame(cbind(as.character(unlist(d[1,6])), as.character(unlist(d[1,1])),"NA","NA" ) ) 
  }
  
  result_file <- paste0("./ld-check/",as.character(unlist(d[1,6])),".",as.character(unlist(d[1,1])),"_ldcheck")
  if (exists("c")==TRUE){ write.table(c,file=result_file,sep="\t",col.names=F,row.names=F,quote=F)}
  
}
