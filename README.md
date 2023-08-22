### **Arquitetura de Solução para Projeto de Engenharia de Dados**

Nesta documentação, vou detalhar a arquitetura de solução proposta para o projeto de engenharia de dados da empresa. A solução visa coletar, transformar, armazenar dados de várias fontes, aplicar regras de negócio, permitir análises seguras e escaláveis, bem como garantir o mascaramento de dados sensíveis. A arquitetura inclui as seguintes ferramentas: Airbyte, Snowflake e dbt.
![image](https://github.com/biancaclazzaris/projeto-manchester/assets/91158522/48acf46e-76c9-4685-a32b-d9a7d04c36f8)


**1. Airbyte - Coleta de Dados**
O Airbyte é uma plataforma de código aberto projetada para coletar dados de várias fontes, incluindo APIs públicas e privadas. Ele simplifica a configuração de conexões, mapeamento de dados e agendamento de sincronizações. O Airbyte atende aos seguintes requisitos:

- **Escalabilidade:** O Airbyte pode lidar com uma variedade de fontes de dados e é escalável para lidar com grandes volumes.
- **Segurança:** Pode-se configurar autenticação para as conexões.
- **Fácil de Usar:** A interface do Airbyte facilita a configuração das conexões e o mapeamento de dados.

**2. Snowflake - Armazenamento de Dados e Mascaramento**
O Snowflake é um banco de dados em nuvem altamente escalável que armazenará os dados após a coleta e transformação. Ele oferece recursos avançados de segurança, escalabilidade e desempenho. Além disso, o Snowflake oferece funcionalidades de mascaramento de dados que atendem aos seguintes requisitos:

- **Escalabilidade:** O Snowflake é projetado para lidar com grandes volumes de dados e consultas complexas.
- **Segurança:** Fornece recursos robustos de segurança, como criptografia, autenticação e controle de acesso.
- **Mascaramento de Dados:** O Snowflake oferece recursos para aplicar políticas de mascaramento, permitindo que dados sensíveis sejam ocultados para diferentes grupos de usuários.

**3. dbt - Transformação de Dados**
O dbt é uma ferramenta que permite transformar dados diretamente no banco de dados. Ele facilita a aplicação de regras de negócio, limpeza e agregações. O dbt atende aos seguintes requisitos:

- **Escalabilidade:** As transformações são executadas diretamente no banco de dados, aproveitando a escalabilidade do Snowflake.
- **Segurança:** As transformações são executadas dentro do ambiente seguro do banco de dados.
- **Qualidade de Dados:** O dbt suporta testes automatizados para garantir a qualidade dos dados transformados.




**Análise das ferramentas:**

A decisão das ferramentas reflete a estratégia cuidadosa que busquei alinhar com as metas e necessidades específicas. Optei pelo Airbyte, uma plataforma open-source que traz simplicidade e versatilidade, integrando-se perfeitamente às nossas operações. A facilidade de uso do Airbyte simplifica a coleta de dados de várias fontes, incluindo APIs, proporcionando uma abordagem ágil e adaptável para a ingestão de informações.

A escolha do Snowflake como plataforma de armazenamento de dados é motivada pela sua ênfase na análise e recuperação de dados, visto que ele é projetado para Data Warehousing de forma muito escalável e segura. As funcionalidades avançadas de autenticação e o controle de acesso robusto oferecem uma camada adicional de proteção aos nossos dados, atendendo aos requisitos de privacidade e conformidade. O Snowflake também apresenta uma série de vantagens que vão além do armazenamento, eliminando a necessidade de outro banco de dados e simplificando nossa infraestrutura. A função de Mascaramento de Dados do Snowflake oferece recursos para aplicar políticas de mascaramento, permitindo que dados sensíveis sejam ocultados para diferentes grupos de usuários.

Para as transformações de dados, eu escolhi o dbt, que representa uma abordagem pragmática e eficiente. A habilidade de utilizar SQL para conduzir transformações, comparar diferentes camadas de dados e escrever diretamente no Snowflake é um diferencial substancial. A possibilidade de parametrizar a qualidade dos dados e a dispensa da necessidade de profundo conhecimento em tecnologias como Spark acelera o processo, permitindo que possamos entregar valor de maneira mais eficaz.

Uma característica importante do dbt é a capacidade de criar a arquitetura Delta Lake de camadas Bronze, Silver e Gold. Essa abordagem gradativa oferece transformações e limpezas progressivas, garantindo a qualidade dos dados em cada etapa. Potencializando a qualidade de dados com o uso de bibliotecas como o "Great Expectations" do Python. Essa ferramenta de código aberto desempenha um papel vital na garantia da qualidade dos dados. Através do Great Expectations, posso definir expectativas detalhadas sobre os dados, especificando condições que eles devem atender. Isso inclui valores mínimos e máximos, formatos esperados, integridade de relacionamentos e muito mais. Ao incorporar testes automatizados baseados nessas expectativas em meu fluxo de dados, posso identificar de maneira proativa problemas de qualidade ou anomalias nos dados à medida que fluem pelos pipelines. Isso resulta em informações confiáveis e úteis para nossas análises, permitindo que usuários com diferentes níveis de conhecimento construam suas interpretações com base em dados sólidos e consistentes.

![image](https://github.com/biancaclazzaris/projeto-manchester/assets/91158522/f8fa3c8f-aa73-44fe-bb79-95e6aaf6094f)


Além disso, o dbt oferece uma funcionalidade de versionamento que é essencial para manter o controle sobre as transformações aplicadas aos dados. Isso nos permite rastrear alterações ao longo do tempo, facilitando auditorias e garantindo a transparência em relação à evolução das regras de transformação. O versionamento também é crucial para colaboração em equipe, permitindo que vários membros trabalhem em conjunto de maneira organizada.

O GitHub Actions, como ferramenta de integração contínua e entrega contínua (CI/CD), encaixa-se perfeitamente nesse cenário. Ele nos permite automatizar as etapas do processo, desde a coleta de dados até a transformação com o dbt e o armazenamento no Snowflake. Podemos configurar fluxos de trabalho personalizados que se ajustam às nossas necessidades, incluindo testes automatizados, validações de qualidade de dados e implantação em diferentes ambientes. A integração direta com o GitHub simplifica a gestão e o acompanhamento dos fluxos de trabalho, proporcionando um ambiente transparente e ágil para desenvolvimento e entrega.

Em síntese, a combinação do Airbyte, Snowflake, dbt e GitHub Actions reflete a escolha estratégica que fiz para atender às necessidades da nossa empresa. Essas ferramentas complementares abordam desde a coleta até a transformação e análise de dados, proporcionando uma solução integrada e eficaz. Essa abordagem permitirá que enfrentemos desafios e aproveitemos oportunidades com confiança, eficiência e resultados sólidos, ao mesmo tempo em que capacitamos nossos analistas de dados a explorar insights valiosos a partir de dados de alta qualidade.
