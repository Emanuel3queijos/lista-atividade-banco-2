# Exercício de revisão e fixação, Emanuel Santos Almeida

### 1. O que é mapeamento objeto relacional(ORM)

O Mapeamento Objeto-Relacional (ORM - Object-Relational Mapping) é uma técnica de programação que permite converter dados entre sistemas de tipos incompatíveis em linguagens de programação orientadas a objetos. É uma ferramenta que cria uma "ponte" entre o mundo dos objetos (utilizados na programação orientada a objetos) e o mundo dos bancos de dados relacionais (baseados em tabelas).

### 2. vantagens e desvantagens do uso de ORM em projetos de software

**Vantagens:**

1. **Produtividade:**
   - Menos código manual, já que não é necessário escrever SQL para operações comuns.
   - Automação de tarefas repetitivas, como mapeamento de tabelas e gerenciamento de conexões.

2. **Manutenção:**
   - Código mais limpo e organizado.
   - Atualizações no modelo de dados são mais fáceis de gerenciar.

3. **Portabilidade:**
   - Abstração das diferenças entre sistemas de gerenciamento de banco de dados (SGBD).
   - Facilidade de migração entre diferentes bancos de dados.

4. **Segurança:**
   - Ajuda a prevenir injeção de SQL.

5. **Conformidade com o Modelo de Domínio:**
   - Integração melhor entre a lógica de negócios e a persistência de dados.

**Desvantagens:**

1. **Desempenho:**
   - Possível overhead, tornando algumas operações menos eficientes.
   - Dificuldade em implementar consultas complexas de forma otimizada.

2. **Curva de Aprendizado:**
   - Pode ser desafiador aprender e configurar o ORM corretamente.

3. **Complexidade Oculta:**
   - Oculta a complexidade das operações de banco de dados.
   - Problemas de desempenho podem ser difíceis de diagnosticar.

4. **Flexibilidade Reduzida:**
   - Limitações impostas pelo framework ORM, restringindo o uso de recursos específicos do banco de dados.

### 3. O que é Object Query Language (OQL)

Object Query Language (OQL) é uma linguagem de consulta desenvolvida para interagir com bancos de dados orientados a objetos. Ela permite que os desenvolvedores façam consultas sobre objetos armazenados em um banco de dados orientado a objetos de maneira semelhante a como SQL (Structured Query Language) é usada para consultar dados em bancos de dados relacionais.

### Características do OQL

1. **Orientada a Objetos:**
   - OQL foi projetada para trabalhar com a estrutura de dados orientada a objetos, permitindo consultas diretas sobre objetos, seus atributos e relações.
   
2. **Sintaxe Semelhante ao SQL:**
   - A sintaxe do OQL é inspirada no SQL, facilitando a adoção por desenvolvedores familiarizados com SQL, mas adaptada para lidar com as nuances de objetos.

3. **Suporte a Consultas Complexas:**
   - OQL pode realizar consultas complexas, incluindo joins, filtragem e agregação, diretamente sobre os atributos e métodos dos objetos.

### Diferenças entre OQL e SQL Tradicional

1. **Modelo de Dados:**
   - **SQL:** Trabalha com um modelo relacional baseado em tabelas, colunas e linhas.
   - **OQL:** Trabalha com um modelo orientado a objetos, lidando com classes, objetos e atributos.

2. **Consultas:**
   - **SQL:** As consultas são feitas sobre tabelas e relacionamentos baseados em chaves primárias e estrangeiras.
   - **OQL:** As consultas são feitas diretamente sobre objetos e suas relações, utilizando referências de objetos e navegação por atributos.

3. **Abstração e Encapsulamento:**
   - **SQL:** Não possui um conceito de encapsulamento; os dados são acessados diretamente nas tabelas.
   - **OQL:** Respeita os princípios de orientação a objetos, permitindo acesso a dados através de métodos e atributos de objetos.

4. **Suporte a Herança e Polimorfismo:**
   - **SQL:** Não possui suporte nativo para herança ou polimorfismo.
   - **OQL:** Suporta herança e polimorfismo, permitindo consultas que refletem essas características dos objetos.

5. **Manipulação de Dados:**
   - **SQL:** Focado em operações CRUD (Create, Read, Update, Delete) sobre tabelas.
   - **OQL:** Focado na recuperação de objetos e suas relações, deixando a manipulação de objetos para a linguagem de programação orientada a objetos.

### Exemplo Comparativo

**Consulta em SQL:**

```sql
SELECT employees.name, departments.name
FROM employees
JOIN departments ON employees.department_id = departments.id
WHERE employees.age > 30;
```

**Consulta em OQL:**

```sql
SELECT e.name, e.department.name
FROM employees e
WHERE e.age > 30;
```

### 4. Consulta em OQL para Buscar Objetos da Classe `Produto` com Preço Maior que 100

```sql
SELECT p
FROM Produto p
WHERE p.preco > 100;
```

### 5. O que é a Java Persistence API (JPA) e quais são seus principais componentes

A Java Persistence API (JPA) é uma especificação da Java EE para persistência de dados em aplicações Java, que define como os dados devem ser armazenados, recuperados e manipulados em um banco de dados relacional. 

**Principais componentes:**
- **Entidades:** Classes Java que representam tabelas no banco de dados.
- **Entity Manager:** Interface para realizar operações de persistência em entidades.
- **Persistência Unit:** Conjunto de todas as entidades que são gerenciadas por uma instância do Entity Manager.
- **Anotações:** Metadados usados para mapear classes e atributos a tabelas e colunas no banco de dados (e.g., `@Entity`, `@Id`, `@GeneratedValue`).

### 6. Descreva o processo de configuração de uma entidade JPA, incluindo as anotações principais (`@Entity`, `@Id`, `@GeneratedValue`, etc.)

Para configurar uma entidade JPA, siga estes passos:

1. **Anote a classe com `@Entity`:**
   ```java
   @Entity
   public class Produto {
       // ...
   }
   ```

2. **Defina a chave primária com `@Id` e `@GeneratedValue`:**
   ```java
   @Id
   @GeneratedValue(strategy = GenerationType.IDENTITY)
   private Long id;
   ```

3. **Mapeie os atributos às colunas do banco de dados:**
   ```java
   private String nome;
   private Double preco;
   private String descricao;
   ```

### 7. Crie uma classe `Produto` com os seguintes atributos: `id` (chave primária), `nome`, `preco`, `descricao`. Anote a classe e seus atributos para que seja uma entidade JPA válida.

```java
import javax.persistence.Entity;
import javax.persistence.Id;
import javax.persistence.GeneratedValue;
import javax.persistence.GenerationType;

@Entity
public class Produto {
    
    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Long id;
    
    private String nome;
    private Double preco;
    private String descricao;

    // Getters and Setters
}
```

### 8. O que é o Hibernate e como ele se relaciona com a JPA?

Hibernate é um framework de mapeamento objeto-relacional (ORM) para Java, que implementa a especificação JPA. Ele facilita o trabalho com bancos de dados, automatizando a conversão de dados entre o modelo de objetos Java e o modelo relacional.

### 9. Quais são as quatro principais características do Hibernate?

1. **Mapeamento Objeto-Relacional:** Converte dados entre sistemas de tipos incompatíveis.
2. **Transparência de Persistência:** Facilita a persistência de dados sem a necessidade de código específico de banco de dados.
3. **Cache:** Suporte para cache de primeiro e segundo nível para otimizar o acesso aos dados.
4. **Consultas Flexíveis:** Suporte a HQL (Hibernate Query Language) e Criteria API para consultas complexas.

### 10. Explique os diferentes níveis de cache do Hibernate (Primeiro Nível, Segundo Nível e Cache de Consulta).

1. **Primeiro Nível (Session Cache):**
   - Cache local ao escopo da sessão.
   - Ativado por padrão e gerencia entidades dentro de uma sessão específica.

2. **Segundo Nível (SessionFactory Cache):**
   - Cache compartilhado entre múltiplas sessões.
   - Configurado opcionalmente e utilizado para melhorar a performance de leituras frequentes.

3. **Cache de Consulta:**
   - Armazena os resultados de consultas executadas.
   - Pode ser configurado para armazenar resultados de queries HQL e Criteria.
