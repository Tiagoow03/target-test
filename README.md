## 1) Observe o trecho de código:

```
int INDICE = 12, SOMA = 0, K = 1;
enquanto K < INDICE faça
{ K = K + 1; SOMA = SOMA + K;}
imprimir(SOMA);
```

### resposta: 

ao final do processamento, o valor da variável SOMA foi 77.

### explicação:

para testar o valor da variável fiz o método em java, ficando:

```java
public class Main {
    public static void main(String[] args) {
        int INDICE = 12;
        int SOMA = 0;
        int K = 1;

        while (K < INDICE) {
            K = K + 1;
            SOMA = SOMA + K;
        }

        System.out.println(SOMA);
    }
}
```

___________________________________________________________________________________________________

## 2) Descubra a lógica e complete o próximo elemento:

### a) 1, 3, 5, 7, ___

#### resposta: 9

explicação: números ímpares

### b) 2, 4, 8, 16, 32, 64, ____

#### resposta: 128

explicação: dobro do número anterior (potências de 2)

### c) 0, 1, 4, 9, 16, 25, 36, ____

#### resposta: 49

explicação: números quadrados perfeitos

### d) 4, 16, 36, 64, ____

#### resposta: 100

explicação: n^2, onde n é sempre um número par

### e) 1, 1, 2, 3, 5, 8, ____

#### resposta: 13

explicação: essa por incrível que pareça minha mente travou, mas lembrei de fibonacci kkkk, cada número é a soma dos dois anteriores

### f) 2,10, 12, 16, 17, 18, 19, ____

#### resposta: 20

explicação: aumento gradual com quebras na lógica da sequência, mas a partir do 16 ele seguem em ordem crescente

___________________________________________________________________________________________________

## 3) Dado um vetor que guarda o valor de faturamento diário de uma distribuidora de todos os dias de um ano, faça um programa, na linguagem que desejar, que calcule e retorne:

- O menor valor de faturamento ocorrido em um dia do ano;
- O maior valor de faturamento ocorrido em um dia do ano;
- Número de dias no ano em que o valor de faturamento diário foi superior à média anual.

### a) Considerar o vetor já carregado com as informações de valor de faturamento.
### b) Podem existir dias sem faturamento, como nos finais de semana e feriados. Estes dias devem ser ignorados no cálculo da média.
### c) Utilize o algoritmo mais veloz que puder definir.

#### resposta e explicação:

eu gosto de java, mas como você pediu o algoritmo "mais veloz", eu creio que nesse caso (lógica teoricamente pequena) cabe um prompt em python, em java o código ficaria um pouco maior

```python
# aqui eu estou supondo que o vetor já estivesse carregado 
faturamento_diario = [
    # exemplo de dados de faturamento.
    0, 220.5, 150.7, 0, 330.2, 0, 400.0, 120.5, 0, 450.3, 0, 0, 210.1, 500.8, 0
]

def calcular_faturamento(faturamento_diario):
    # filtra os dias com faturamento maior que zero
    dias_com_faturamento = [f for f in faturamento_diario if f > 0]

    # calcula o menor e o maior valor de faturamento
    menor_faturamento = min(dias_com_faturamento)
    maior_faturamento = max(dias_com_faturamento)

    # calcula a média do faturamento
    media_faturamento = sum(dias_com_faturamento) / len(dias_com_faturamento)

    # calcula o número de dias com faturamento acima da média
    dias_acima_da_media = len([f for f in dias_com_faturamento if f > media_faturamento])

    return menor_faturamento, maior_faturamento, dias_acima_da_media

# chama a função e armazena os resultados
menor, maior, dias_acima_media = calcular_faturamento(faturamento_diario)

# resultados
print(f"Menor valor de faturamento: {menor}")
print(f"Maior valor de faturamento: {maior}")
print(f"Número de dias com faturamento acima da média: {dias_acima_media}")
```
___________________________________________________________________________________________________

## 4) Banco de dados

Uma empresa solicitou a você um aplicativo para manutenção de um cadastro de clientes. Após a reunião de definição dos requisitos, as conclusões foram as seguintes:

- Um cliente pode ter um número ilimitado de telefones;
- Cada telefone de cliente tem um tipo, por exemplo: comercial, residencial, celular, etc. O sistema deve permitir cadastrar novos tipos de telefone;
- A princípio, é necessário saber apenas em qual estado brasileiro cada cliente se encontra. O sistema deve permitir cadastrar novos estados;

Você ficou responsável pela parte da estrutura de banco de dados que será usada pelo aplicativo. Assim sendo:

- Proponha um modelo lógico para o banco de dados que vai atender a aplicação. Desenhe as tabelas necessárias, os campos de cada uma e marque com setas os relacionamentos existentes entre as tabelas;
- Aponte os campos que são chave primária (PK) e chave estrangeira (FK);
- Faça uma busca utilizando comando SQL que traga o código, a razão social e o(s) telefone(s) de todos os clientes do estado de São Paulo (código “SP”);

### respostas e explicações:

#### tabela de Clientes

| Campo           | Tipo     | Descrição                             | PK | FK |
|-----------------|----------|---------------------------------------|----|----|
| `id_cliente`    | INT      | Identificador único                   | X  |    |
| `razao_social`  | VARCHAR  | Razão social do cliente               |    |    |
| `id_estado`     | INT      | Relacionamento com a tabela Estados   |    | X  |

#### tabela de Telefones

| Campo              | Tipo     | Descrição                                  | PK | FK |
|--------------------|----------|--------------------------------------------|----|----|
| `id_telefone`      | INT      | Identificador único                        | X  |    |
| `id_cliente`       | INT      | Relacionamento com a tabela Clientes       |    | X  |
| `numero`           | VARCHAR  | Número de telefone                         |    |    |
| `id_tipo_telefone` | INT      | Relacionamento com a tabela Tipos_Telefone |    | X  |

#### tabela dos Tipos de Telefone (tipo_telefone)

| Campo             | Tipo     | Descrição                            | PK | FK |
|-------------------|----------|--------------------------------------|----|----|
| `id_tipo_telefone`| INT      | Identificador único                  | X  |    |
| `descricao`       | VARCHAR  | Descrição do tipo de telefone        |    |    |

#### tabela de Estados Brasileiros (estados)

| Campo         | Tipo       | Descrição                        | PK | FK |
|---------------|------------|----------------------------------|----|----|
| `id_estado`   | INT        | Identificador único               | X  |    |
| `uf`          | VARCHAR(2) | Sigla do estado (ex: SP)          |    |    |
| `nome_estado` | VARCHAR    | Nome do estado                    |    |    |


prompt para buscar clientes e telefones do estados de São Paulo:
```sql
SELECT c.id_cliente, c.razao_social, t.numero AS telefone
FROM clientes c
JOIN telefones t ON c.id_cliente = t.id_cliente
JOIN estados e ON c.id_estado = e.id_estado
WHERE e.uf = 'SP';
```
___________________________________________________________________________________________________

## 5) Dois veículos, um carro e um caminhão, saem respectivamente de cidades opostas pela mesma rodovia. O carro, de Ribeirão Preto em direção a Barretos, a uma velocidade constante de 90 km/h, e o caminhão, de Barretos em direção a Ribeirão Preto, a uma velocidade constante de 80 km/h. Quando eles se cruzarem no percurso, qual estará mais próximo da cidade de Ribeirão Preto?

### a) Considerar a distância de 125km entre a cidade de Ribeirão Preto <-> Barretos.
### b) Considerar 3 pedágios como obstáculo e que o carro leva 5 minutos a mais para passar em cada um deles, pois ele não possui dispositivo de cobrança de pedágio.
### c) Explique como chegou no resultado.

#### respostas: 

Os dois veículos estarão na mesma distância de seus respectivos destinos, pois estarão no mesmo ponto da estrada.

#### explicação:

- temos as seguintes informações:

```
distância (ribeirão preto - barretos) -> 125km\n
velocidade do carro -> 90km/h
velocidade do caminhão -> 80km/h
total de pedágios -> 3 - *o carro para 5 minutos em cada (15min = 0.25 horas [15/60])
```

- tempo até o cruzamento sem os pedágios:

```
velocidade relativa dos veículos -> 90 + 80 = 170km/h
agora precisamos descobrir o tempo, que nada mais é do que a razão da distância total pela velocidade relativa de cada um dos veículos:
t -> dist. total/veloc. relativa - t -> 125/170, isso dá aproximadamente 0.735 horas, uns 44 minutos
```

- tempo total do carro, considerando os pedágios:

```
tempo adicional -> 15min = 0.25 horas
tempo do carro -> 0.735 + 0.25 = 0.985 horas, quase 1 horinha
```

- distância percorrido no momento que eles se cruzam:

```
distancia = velocidade * tempo
carro -> 90 * 0.735 = **66.15 km percorridos
*foi considerando apenas o tempo que o carro estava em movimento
caminhão -> 80 * 0.735 = 58.8 km percorridos (125 - 58.8 = **66.2 km de ribeirão preto)
```

#### Portanto, no momento de encontro dos veículos eles estarão praticamente na mesma distância de Ribeirão Preto, pois o tempo adicional nos pedágios não altera MUITO a posição do ponto de encontro.
