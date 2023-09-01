# Lista 01

## 1 - Fale o que é um SGBD e explique algumas de suas vantagens em relação aos sistemas de arquivos.

Um Sistema de Gerenciamento de Banco de Dados (SGBD) é um software projetado para gerenciar e facilitar o armazenamento, a organização, a recuperação e a manipulação de dados em um banco de dados. Ele atua como uma interface entre os usuários ou aplicativos e os dados armazenados, oferecendo várias funcionalidades que simplificam o gerenciamento de informações. Abaixo estão algumas vantagens dos SGBDs em relação aos sistemas de arquivos tradicionais:

**1 - Integridade de Dados:** Os SGBDs garantem a integridade dos dados por meio de mecanismos de restrição e validação. Isso evita a inserção de dados inconsistentes ou inválidos no banco de dados.

**2- Segurança de Dados:** Os SGBDs oferecem recursos de segurança, como controle de acesso, autenticação e autorização, que protegem os dados contra acessos não autorizados. Isso é fundamental para a conformidade com regulamentações de privacidade de dados.

**3 - Consultas Complexas:** SGBDs permitem a execução de consultas complexas em grandes conjuntos de dados usando SQL (Structured Query Language), o que é muito mais difícil e ineficiente de realizar em sistemas de arquivos.

**4 - Escalabilidade:** Os SGBDs são projetados para serem escaláveis, permitindo a expansão de capacidade à medida que a quantidade de dados e o número de usuários aumentam.

**5 - Backup e Recuperação Eficiente:** SGBDs oferecem recursos de backup e restauração de dados, tornando mais fácil a manutenção e a recuperação de informações em caso de perda ou erro.

**6 - Manutenção Simplificada:** Gerenciar dados em um SGBD é mais fácil do que gerenciar arquivos em sistemas de arquivos, especialmente quando se trata de manutenção, atualização e migração de dados.

Em resumo, um SGBD oferece várias vantagens em relação aos sistemas de arquivos tradicionais, tornando o gerenciamento de dados mais eficiente, seguro e robusto, especialmente em ambientes onde a quantidade de dados é grande e a integridade, segurança e escalabilidade são essenciais.

## 2. BD Campeonato - Construa o Diagrama Entidade Relacionamento para os requisitos:

```mermaid
erDiagram
  CAMPEONATO {
    string codigo
    string nome
    string data_inicio
    string data_fim
  }

  PARTIDA {
    string data
    string endereco
    string[] gols
  }

  EQUIPE {
    string codigo
    string nome
  }

  JOGADOR {
    string codigo
    string nome
    string apelido
    string posicao
  }

  COMISSAO{
    string codigo
    string nome
    string funcao
  }




  CAMPEONATO }|--|{ EQUIPE : "Tem"
  CAMPEONATO ||--|{ PARTIDA : "Tem"
  EQUIPE }|--|{ JOGADOR : "Possui"
  EQUIPE }|--|{ COMISSAO : "Possui"
  EQUIPE }|--|{ PARTIDA : "Escalacao"

```

## 3. BD Universidade - Construa o Diagrama Entidade Relacionamento para os requisitos:

```mermaid
erDiagram

    CENTRO {
    string id
    string Nome
    }

    CURSO {
    string id
    string Nome
    }

  DEPARTAMENTO {
    string id
    string Nome
  }

    CC {
    string id
    string Tipo
    string Nome
    string Requisito
  }

DISCIPLINA {
    string id
    string codigo
  }

   DOCENTE {
    string id
    string Nome
  }

  TURMA {
    string id
    string cod
    string Ano
  }

  DISCENTE {
    string id
    string Nome
    float[] nota
  }

DISCENTE_MONITOR {
    string id
    string Nome
  }

  CENTRO ||--|{ CURSO : "Tem"
  CENTRO ||--|{ DEPARTAMENTO : "Tem"
  DISCENTE }o--|| CURSO : "Está matriculado em"
  CURSO }o--|{ CC : "TURMA"
  DEPARTAMENTO ||--|{ CC : "Tem"
  DOCENTE }|--|{ TURMA : "Ensina"
  TURMA }|--|{ DISCENTE : "Tem"
  TURMA }|--|| DISCIPLINA : "É de"
  DISCENTE_MONITOR one or many to only one TURMA : tem
  DOCENTE }|--|| DEPARTAMENTO : "Vinculado a"
```

## 4. BD Locadora de Veículos - Construa o Diagrama Entidade Relacionamento para os requisitos:

```mermaid
erDiagram
   LOCADORA {
  string nome
  int quantidade_veiculos
}

VEICULO {
  int numero
  string marca
  int ano
  string placa
  string cor
  float quilometragem
  float valor_locacao
  string tipo_locacao
  string categoria
}

CLIENTE {
  string CPF
  string CNH
  string nome
  string endereco
  int idade
  string telefone
}

REGISTRO_ALUGUEL {
  CLIENTE cliente
  VEICULO veiculo
  int numero
  string data_locacao
  string hora_locacao
}

TECNICO {
  int numero_cadastro
  string CPF
  string nome
}

PERFIL_CLIENTE {
  int total_alugueis
  float total_horas_alugadas
  float total_valor_alugueis
  int total_multas
}

LOCADORA ||--o{ VEICULO : "Possui"
  LOCADORA }|--o{ CLIENTE : "Possui"
  LOCADORA ||--o{ TECNICO : "Possui"
  LOCADORA ||--o{ REGISTRO_ALUGUEL : "Realiza"
  CLIENTE }|--o{ PERFIL_CLIENTE : "Possui"
```

## 5. Entidade-Relacionamento:

```mermaid
erDiagram

CLIENTE {
  string documento_identificacao
  string nome
  string telefone
  string endereco
}

PRODUTO {
  string nome_produto
  string tipo
  float preco
  int quantidade_estoque
}

COMPRA {
  int numero_compra
  string data_compra
  float valor_total
}

FUNCIONARIO {
  string nome_funcionario
  string telefone
  string endereco
  float salario
  string funcao
  string documento_identificacao
}

FORNECEDOR {
  string nome_fornecedor
  string CNPJ
  string telefone
  string endereco
}

CLIENTE }|..|{ COMPRA : "Realiza"
  PRODUTO }|--|{ COMPRA : "Inclui"
  FUNCIONARIO }|--|{ COMPRA : "Atende"
  FORNECEDOR }|--|{ COMPRA : "Fornece"

```
