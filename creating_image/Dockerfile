FROM debian

LABEL app="Nome_da_imagem"

ENV VARIAVEL_DE_TESTE="valor_da_variavel"

RUN apt-get update && apt-get install -y stress && apt-get clean

CMD stress --cpu 1 --vm-bytes 64M --vm 1
