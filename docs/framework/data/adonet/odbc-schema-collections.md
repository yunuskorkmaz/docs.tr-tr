---
description: 'Daha fazla bilgi edinin: ODBC şema koleksiyonları'
title: ODBC Şema Koleksiyonları
ms.date: 03/30/2017
ms.assetid: 1bb126a5-ceec-4649-a4bc-8aa19e801046
ms.openlocfilehash: ceac67e49914db7010e315a2dfcdb630bea1e29f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99786205"
---
# <a name="odbc-schema-collections"></a>ODBC Şema Koleksiyonları

Bu bölümde Microsoft SQL Server, Oracle ve Microsoft Jet için ODBC sürücüleri için şema koleksiyonu desteği açıklanmaktadır.

## <a name="microsoft-sql-server-odbc-driver"></a>Microsoft SQL Server ODBC sürücüsü

Microsoft SQL Server ODBC sürücüsü, ortak şema koleksiyonlarına ek olarak aşağıdaki belirli şema koleksiyonlarını destekler:

- Tablolar

- Dizinler

- Sütunlar

- Yordamlar

- ProcedureColumns

- ProcedureParameters

- Görünümler

### <a name="tables-and-views"></a>Tablolar ve görünümler

|ColumnName|DataType|
|----------------|--------------|
|TABLE_CAT|Dize|
|TABLE_SCHEM|Dize|
|TABLE_NAME|Dize|
|TABLE_TYPE|Dize|
|AÇıKLAMALARıNıN|Dize|

### <a name="indexes"></a>Dizinler

|ColumnName|DataType|
|----------------|--------------|
|TABLE_CAT|Dize|
|TABLE_SCHEM|Dize|
|TABLE_NAME|Dize|
|NON_UNIQUE|Int16|
|INDEX_QUALIFIER|Dize|
|INDEX_NAME|Dize|
|TÜR|Int16|
|ORDINAL_POSITION|Int16|
|COLUMN_NAME|Dize|
|ASC_OR_DESC|Dize|
|ITE|Int32|
|SAYFALARı|Int32|
|FILTER_CONDITION|Dize|
|SS_TYPE_SCHEMA|Dize|
|SS_DATA_TYPE|Bayt|

### <a name="columns"></a>Sütunlar

|ColumnName|DataType|
|----------------|--------------|
|TABLE_CAT|Dize|
|TABLE_SCHEM|Dize|
|TABLE_NAME|Dize|
|COLUMN_NAME|Dize|
|DATA_TYPE|Int16|
|TYPE_NAME|Dize|
|COLUMN_SIZE|Int32|
|BUFFER_LENGTH|Int32|
|DECIMAL_DIGITS|Int16|
|NUM_PREC_RADIX|Int16|
|YAPıLAMAZ|Int16|
|AÇıKLAMALARıNıN|Dize|
|COLUMN_DEF|Dize|
|SQL_DATA_TYPE|Int16|
|SQL_DATETIME_SUB|Int16|
|CHAR_OCTET_LENGTH|Int32|
|ORDINAL_POSITION|Int32|
|IS_NULLABLE|Dize|
|SS_TYPE_CATALOG|Dize|
|SS_TYPE_SCHEMA|Dize|
|SS_DATA_TYPE|Bayt|

### <a name="procedures"></a>Yordamlar

|ColumnName|DataType|
|----------------|--------------|
|PROCEDURE_CAT|Dize|
|PROCEDURE_SCHEM|Dize|
|PROCEDURE_NAME|Dize|
|NUM_INPUT_PARAMS|Int32|
|NUM_OUTPUT_PARAMS|Int32|
|NUM_RESULT_SETS|Int32|
|AÇıKLAMALARıNıN|Dize|
|PROCEDURE_TYPE|Int16|

### <a name="procedurecolumns"></a>ProcedureColumns

|ColumnName|DataType|
|----------------|--------------|
|PROCEDURE_CAT|Dize|
|PROCEDURE_SCHEM|Dize|
|PROCEDURE_NAME|Dize|
|COLUMN_NAME|Dize|
|COLUMN_TYPE|Int16|
|DATA_TYPE|Int16|
|TYPE_NAME|Dize|
|COLUMN_SIZE|Int32|
|BUFFER_LENGTH|Int32|
|DECIMAL_DIGITS|Int16|
|NUM_PREC_RADIX|Int16|
|YAPıLAMAZ|Int16|
|AÇıKLAMALARıNıN|Dize|
|COLUMN_DEF|Dize|
|SQL_DATA_TYPE|Int16|
|SQL_DATETIME_SUB|Int16|
|CHAR_OCTET_LENGTH|Int32|
|ORDINAL_POSITION|Int32|
|IS_NULLABLE|Dize|
|SS_TYPE_CATALOG|Dize|
|SS_TYPE_SCHEMA|Dize|
|SS_DATA_TYPE|Bayt|

### <a name="procedureparameters"></a>ProcedureParameters

|ColumnName|DataType|
|----------------|--------------|
|PROCEDURE_CAT|Dize|
|PROCEDURE_SCHEM|Dize|
|PROCEDURE_NAME|Dize|
|COLUMN_NAME|Dize|
|COLUMN_TYPE|Int16|
|DATA_TYPE|Int16|
|TYPE_NAME|Dize|
|COLUMN_SIZE|Int32|
|BUFFER_LENGTH|Int32|
|DECIMAL_DIGITS|Int16|
|NUM_PREC_RADIX|Int16|
|YAPıLAMAZ|Int16|
|AÇıKLAMALARıNıN|Dize|
|COLUMN_DEF|Dize|
|SQL_DATA_TYPE|Int16|
|SQL_DATETIME_SUB|Int16|
|CHAR_OCTET_LENGTH|Int32|
|ORDINAL_POSITION|Int32|
|IS_NULLABLE|Dize|
|SS_TYPE_CATALOG|Dize|
|SS_TYPE_SCHEMA|Dize|
|SS_DATA_TYPE|Bayt|

## <a name="microsoft-oracle-odbc-driver"></a>Microsoft Oracle ODBC sürücüsü

Microsoft SQL Server Oracle ODBC sürücüsü, ortak şema koleksiyonlarına ek olarak aşağıdaki belirli şema koleksiyonlarını destekler:

- Tablolar

- Sütunlar

- Yordamlar

- ProcedureColumns

- ProcedureParameters

- Görünümler

- Dizinler

### <a name="tables-and-views"></a>Tablolar ve görünümler

|ColumnName|DataType|
|----------------|--------------|
|TABLE_QUALIFIER|Dize|
|TABLE_OWNER|Dize|
|TABLE_NAME|Dize|
|TABLE_TYPE|Dize|
|AÇıKLAMALARıNıN|Dize|

### <a name="columns"></a>Sütunlar

|ColumnName|DataType|
|----------------|--------------|
|TABLE_QUALIFIER|Dize|
|TABLE_OWNER|Dize|
|TABLE_NAME|Dize|
|COLUMN_NAME|Dize|
|DATA_TYPE|Int16|
|TYPE_NAME|Dize|
|DUYARLıLıK|Int32|
|LENGTH|Int32|
|ÖLÇEK|Int16|
|TABAN|Int16|
|YAPıLAMAZ|Int16|
|AÇıKLAMALARıNıN|Dize|
|ORDINAL_POSITION|Int32|

### <a name="procedures"></a>Yordamlar

|ColumnName|DataType|
|----------------|--------------|
|PROCEDURE_QUALIFIER|Dize|
|PROCEDURE_OWNER|Dize|
|PROCEDURE_NAME|Dize|
|NUM_INPUT_PARAMS|Int16|
|NUM_OUTPUT_PARAMS|Int16|
|NUM_RESULT_SETS|Int16|
|AÇıKLAMALARıNıN|Dize|
|PROCEDURE_TYPE|Int16|

### <a name="procedurecolumns"></a>ProcedureColumns

|ColumnName|DataType|
|----------------|--------------|
|PROCEDURE_QUALIFIER|Dize|
|PROCEDURE_OWNER|Dize|
|PROCEDURE_NAME|Dize|
|COLUMN_NAME|Dize|
|COLUMN_TYPE|Int16|
|DATA_TYPE|Int16|
|TYPE_NAME|Dize|
|DUYARLıLıK|Int32|
|LENGTH|Int32|
|ÖLÇEK|Int16|
|TABAN|Int16|
|YAPıLAMAZ|Int16|
|AÇıKLAMALARıNıN|Dize|
|YÜKLEMEK|Int32|
|ORDINAL_POSITION|Int32|

## <a name="microsoft-jet-odbc-driver"></a>Microsoft Jet ODBC sürücüsü

Microsoft Jet ODBC sürücüsü, ortak şema koleksiyonlarına ek olarak aşağıdaki belirli şema koleksiyonlarını destekler:

- Tablolar

- Dizinler

- Sütunlar

- Yordamlar

- ProcedureColumns

- ProcedureParameters

- Görünümler

### <a name="tables-and-views"></a>Tablolar ve görünümler

|ColumnName|DataType|
|----------------|--------------|
|TABLE_QUALIFIER|Dize|
|TABLE_OWNER|Dize|
|TABLE_NAME|Dize|
|TABLE_TYPE|Dize|
|AÇıKLAMALARıNıN|Dize|

### <a name="columns"></a>Sütunlar

|ColumnName|DataType|
|----------------|--------------|
|TABLE_QUALIFIER|Dize|
|TABLE_OWNER|Dize|
|TABLE_NAME|Dize|
|COLUMN_NAME|Dize|
|DATA_TYPE|Int16|
|TYPE_NAME|Dize|
|DUYARLıLıK|Int32|
|LENGTH|Int32|
|ÖLÇEK|Int16|
|TABAN|Int16|
|YAPıLAMAZ|Int16|
|AÇıKLAMALARıNıN|Dize|
|ORDINAL_POSITION|Int32|

### <a name="procedures"></a>Yordamlar

|ColumnName|DataType|
|----------------|--------------|
|PROCEDURE_QUALIFIER|Dize|
|PROCEDURE_OWNER|Dize|
|PROCEDURE_NAME|Dize|
|NUM_INPUT_PARAMS|Int16|
|NUM_OUTPUT_PARAMS|Int16|
|NUM_RESULT_SETS|Int16|
|AÇıKLAMALARıNıN|Dize|
|PROCEDURE_TYPE|Int16|

### <a name="procedurecolumns"></a>ProcedureColumns

|ColumnName|DataType|
|----------------|--------------|
|PROCEDURE_QUALIFIER|Dize|
|PROCEDURE_OWNER|Dize|
|PROCEDURE_NAME|Dize|
|COLUMN_NAME|Dize|
|COLUMN_TYPE|Int16|
|DATA_TYPE|Int16|
|TYPE_NAME|Dize|
|DUYARLıLıK|Int32|
|LENGTH|Int32|
|ÖLÇEK|Int16|
|TABAN|Int16|
|YAPıLAMAZ|Int16|
|AÇıKLAMALARıNıN|Dize|
|YÜKLEMEK|Int32|
|ORDINAL_POSITION|Int32|

### <a name="procedureparameters"></a>ProcedureParameters

|ColumnName|DataType|
|----------------|--------------|
|PROCEDURE_CAT|Dize|
|PROCEDURE_SCHEM|Dize|
|PROCEDURE_NAME|Dize|
|COLUMN_NAME|Dize|
|COLUMN_TYPE|Int16|
|DATA_TYPE|Int16|
|TYPE_NAME|Dize|
|COLUMN_SIZE|Int32|
|BUFFER_LENGTH|Int32|
|DECIMAL_DIGITS|Int16|
|NUM_PREC_RADIX|Int16|
|YAPıLAMAZ|Int16|
|AÇıKLAMALARıNıN|Dize|
|COLUMN_DEF|Dize|
|SQL_DATA_TYPE|Int16|
|SQL_DATETIME_SUB|Int16|
|CHAR_OCTET_LENGTH|Int32|
|ORDINAL_POSITION|Int32|
|IS_NULLABLE|Dize|

## <a name="see-also"></a>Ayrıca bkz.

- [ADO.NET’e Genel Bakış](ado-net-overview.md)
