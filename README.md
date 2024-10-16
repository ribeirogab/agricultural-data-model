# Modelo de Banco de Dados para Gestão de Insumos Agrícolas

## Introdução

Este repositório contém a modelagem de um banco de dados relacional para o projeto da Startup **FarmTech Solutions**, que visa otimizar a irrigação e a aplicação de nutrientes em plantações através do uso de sensores de umidade, pH e nutrientes. A modelagem foi realizada de acordo com os princípios de relacionamento de banco de dados, utilizando o [SQLDesigner](https://github.com/ondras/wwwsqldesigner) para criar o DER (Diagrama Entidade-Relacionamento).

## Objetivo

O objetivo deste projeto é desenvolver um sistema que permita o armazenamento e a análise dos dados coletados pelos sensores, ajustando de maneira precisa a quantidade de água e nutrientes aplicados nas plantações. Isso inclui:

- Monitoramento contínuo de diferentes tipos de sensores.
- Armazenamento de leituras de umidade, pH, fósforo e potássio.
- Aplicação de água e nutrientes com base nos dados coletados.
- Capacidade de rastrear leituras e ajustes por cultura e local.

## Diagrama Entidade-Relacionamento (DER)

![Diagrama Entidade-Relacionamento](./diagram.png)

## Entidades Principais

### 1. **Sensor**

Representa os diferentes sensores usados nas plantações.

- **Atributos**:

  - `sensor_id`: Identificador único do sensor.
  - `sensor_type`: Tipo do sensor (Umidade, pH, Nutrientes).

### 2. **Sensor_Reading**

Armazena as leituras feitas pelos sensores em momentos específicos.

- **Atributos**:
  - `reading_id`: Identificador único da leitura.
  - `sensor_id`: Referência ao sensor que coletou a leitura.
  - `crop_id`: Referência à cultura monitorada.
  - `location_id`: Referência ao local da leitura.
  - `timestamp`: Data e hora da leitura.
  - `moisture_value`: Valor de umidade coletado (se aplicável).
  - `ph_value`: Valor de pH coletado (se aplicável).
  - `phosphorus_value`: Nível de fósforo (se aplicável).
  - `potassium_value`: Nível de potássio (se aplicável).

### 3. **Application**

Armazena os ajustes feitos na irrigação e aplicação de nutrientes.

- **Atributos**:

  - `application_id`: Identificador único da aplicação.
  - `crop_id`: Referência à cultura que recebeu a aplicação.
  - `timestamp`: Data e hora do ajuste.
  - `water_amount`: Quantidade de água aplicada.
  - `phosphorus_amount`: Quantidade de fósforo aplicado.
  - `potassium_amount`: Quantidade de potássio aplicado.

### 4. **Crop**

Armazena informações sobre as culturas plantadas.

- **Atributos**:

  - `crop_id`: Identificador único da cultura.
  - `crop_name`: Nome da cultura.
  - `planting_date`: Data de plantio.

### 5. **Location**

Armazena informações sobre as localizações da plantação onde as leituras são feitas.

- **Atributos**:

  - `location_id`: Identificador único da localização.
  - `location_name`: Nome da localização.
  - `coordinates`: Coordenadas geográficas da localização.

## Relacionamentos

- Um **Sensor** pode ter várias **Sensor_Reading** associadas (1:N).
- Uma **Crop** pode ter várias **Sensor_Reading** e **Application** associadas (1:N).
- Uma **Location** pode estar associada a várias **Sensor_Reading** (1:N).
- Cada **Application** está relacionada a uma **Crop** (N:1).

## Arquivos Incluídos

- **`data-model.xml`**: Arquivo XML contendo a definição do modelo de banco de dados para ser importado no SQLDesigner.
- **`data-model.sql`**: Script SQL para a criação das tabelas do modelo no banco de dados.
- **`diagram.png`**: Imagem do Diagrama Entidade-Relacionamento (DER) gerado a partir do modelo.
- **`README.md`**: Este arquivo de documentação explicando o projeto.
