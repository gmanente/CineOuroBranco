# CineOuroBranco
Sistema de Gestão de Cinemas

### 🗄️ Banco de Dados
- **MariaDB**: Estrutura relacional onde os dados são armazenados e organizados.
- **DBEaver**: Utilizado para modelar e gerenciar o banco de dados.
- **Estrutura**: O banco de dados possui tabelas que armazenam informações de acordo com a vontade do usuário administrativo para a gestão das informações do Cine Ouro Branco
  
DDL - Linguagem de Definição de Dados 
```sql
--
-- CRIAÇÃO DO BANCO DE DADOS
--
create database cine_ouro_branco;

--
-- CRIAÇÃO DA TABELA PAIS
--
-- cine_ouro_branco.pais definição

CREATE TABLE `pais` (
  `id_pais` int(11) NOT NULL,
  `nome_pais` varchar(150) NOT NULL,
  PRIMARY KEY (`id_pais`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_general_ci;

--
-- CRIAÇÃO DA TABELA DE ESTADO
--
-- cine_ouro_branco.estado definição

CREATE TABLE `estado` (
  `id_estado` int(11) NOT NULL,
  `id_pais` int(11) NOT NULL,
  `nome_estado` varchar(120) NOT NULL,
  `sigla_estado` char(5) NOT NULL,
  PRIMARY KEY (`id_estado`),
  KEY `fk_estado_x_pais` (`id_pais`),
  CONSTRAINT `fk_estado_x_pais` FOREIGN KEY (`id_pais`) REFERENCES `pais` (`id_pais`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_general_ci;

-- cine_ouro_branco.cidade definição

CREATE TABLE `cidade` (
  `id_cidade` int(11) NOT NULL,
  `id_estado` int(11) NOT NULL,
  `nome_cidade` varchar(120) NOT NULL,
  PRIMARY KEY (`id_cidade`),
  KEY `fk_cidade_x_estado` (`id_estado`),
  CONSTRAINT `fk_cidade_x_estado` FOREIGN KEY (`id_estado`) REFERENCES `estado` (`id_estado`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_general_ci;
