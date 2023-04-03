# ATM-GNS3

### Instituto Federal de Mato Grosso

Estudante: João Angello R. O.      
Matrícula: 2015178440352     
Curso: Engenharia da Computação     
Disciplina: Redes de Computadores II

---
# Configuração da rede ATM

![topology](topology.png)

Este relatório apresenta as configurações realizadas nos roteadores R1 e R2, bem como nos switches ATM ATMSWx, a fim de estabelecer a conexão entre eles.

Configurações dos Roteadores:
Para configurar as interfaces dos roteadores, as seguintes etapas foram realizadas:

No roteador R1, entrou-se no modo de configuração e, em seguida, na interface atm1/0, que foi ativada usando o comando "no shutdown".
Em seguida, a subinterface atm1/0.100 foi configurada para uso ponto a ponto, e foi atribuído um endereço IP de 10.10.10.1/30 e um circuito virtual PVC 100/101 para transportar o tráfego IP.
O protocolo IP foi configurado com o endereço IP de destino 10.10.10.2 para envio de broadcast.
Por fim, a encapsulação aal5snap foi configurada na subinterface, e saiu-se do modo de configuração.

### R1:
```
configure terminal
int atm1/0
no shutdown
exit
int atm1/0.100 point-to-point
ip address 10.10.10.1 255.255.255.252
pvc 100/101
protocol ip 10.10.10.2 broadcast
encapsulation aal5snap
exit
exit
exit
```

No roteador R2, as mesmas configurações foram realizadas, mas com valores diferentes para o endereço IP, o PVC e o endereço IP de destino no protocolo IP.



#### R2:
```
configure terminal
int atm1/0
no shutdown
exit
int atm1/0.100 point-to-point
ip address 10.10.10.2 255.255.255.252
pvc 100/201
protocol ip 10.10.10.1 broadcast
encapsulation aal5snap
exit
exit
exit
```

Configurações dos Switches ATM:
Os switches ATM ATMSWx foram configurados com as seguintes configurações:

No ATMSW1, a porta 1 foi configurada com o VPI 100 e o VCI 101, e a porta 3 foi configurada com o VPI 100 e o VCI 150.
No ATMSW2, a porta 2 foi configurada com o VPI 100 e o VCI 150, e a porta 3 foi configurada com o VPI 100 e o VCI 50.
No ATMSW3, a porta 3 foi configurada com o VPI 100 e o VCI 50, e a porta 1 foi configurada com o VPI 100 e o VCI 201.


### ATMSW1:

![atm1.png](atm1.png)


### ATMSW2:
![atm2.png](atm2.png)


### ATMSW3:
![atm3.png](atm3.png)


|Name|Port|VPI|VCI|Port|VPI|VCI|
|-|-|-|-|-|-|-|
|ATMSW1|1|100|101|3|100|150|
|ATMSW2|2|100|150|3|100|50|
|ATMSW3|3|100|50|1|100|201|


Conclusão:
As configurações realizadas nos roteadores e switches ATM ATMSWx permitirão o transporte de tráfego IP através da rede ATM. É importante salientar que as configurações realizadas foram feitas com base nas informações fornecidas, e que a configuração da rede depende de muitos outros fatores e detalhes que não foram fornecidos.
