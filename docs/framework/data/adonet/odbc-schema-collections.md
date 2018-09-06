---
title: ODBC şema koleksiyonları
ms.date: 03/30/2017
ms.assetid: 1bb126a5-ceec-4649-a4bc-8aa19e801046
ms.openlocfilehash: bdedbb11960f02b99dcca6388abf663635238f74
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43877537"
---
# <a name="odbc-schema-collections"></a>ODBC şema koleksiyonları
Bu bölümde, Microsoft SQL Server, Oracle ve Microsoft Jet ODBC sürücüleri için şema koleksiyonu desteği açıklanmaktadır.  
  
## <a name="microsoft-sql-server-odbc-driver"></a>Microsoft SQL Server ODBC sürücüsü  
 Microsoft SQL Server ODBC sürücüsü, ortak şema koleksiyonları ek olarak aşağıdaki belirli şema koleksiyonları destekler:  
  
-   Tabloları  
  
-   Dizinleri  
  
-   Sütunlar  
  
-   Yordamlar  
  
-   ProcedureColumns  
  
-   ProcedureParameters  
  
-   Görünümler  
  
### <a name="tables-and-views"></a>Tabloları ve görünümleri  
  
|ColumnName|Veri türü|  
|----------------|--------------|  
|TABLE_CAT|Dize|  
|TABLE_SCHEM|Dize|  
|TABLE_NAME|Dize|  
|TABLE_TYPE|Dize|  
|AÇIKLAMALAR|Dize|  
  
### <a name="indexes"></a>Dizinleri  
  
|ColumnName|Veri türü|  
|----------------|--------------|  
|TABLE_CAT|Dize|  
|TABLE_SCHEM|Dize|  
|TABLE_NAME|Dize|  
|NON_UNIQUE|Int16|  
|INDEX_QUALIFIER|Dize|  
|INDEX_NAME|Dize|  
|TÜRÜ|Int16|  
|ORDINAL_POSITION|Int16|  
|COLUMN_NAME|Dize|  
|ASC_OR_DESC|Dize|  
|CARDINATLITY|Int32|  
|SAYFALARI|Int32|  
|FILTER_CONDITION|Dize|  
|SS_TYPE_SCHEMA|Dize|  
|SS_DATA_TYPE|Bayt|  
  
### <a name="columns"></a>Sütunlar  
  
|ColumnName|Veri türü|  
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
|BOŞ DEĞER ATANABİLİR|Int16|  
|AÇIKLAMALAR|Dize|  
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
  
|ColumnName|Veri türü|  
|----------------|--------------|  
|PROCEDURE_CAT|Dize|  
|PROCEDURE_SCHEM|Dize|  
|PROCEDURE_NAME|Dize|  
|NUM_INPUT_PARAMS|Int32|  
|NUM_OUTPUT_PARAMS|Int32|  
|NUM_RESULT_SETS|Int32|  
|AÇIKLAMALAR|Dize|  
|PROCEDURE_TYPE|Int16|  
  
### <a name="procedurecolumns"></a>ProcedureColumns  
  
|ColumnName|Veri türü|  
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
|BOŞ DEĞER ATANABİLİR|Int16|  
|AÇIKLAMALAR|Dize|  
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
  
|ColumnName|Veri türü|  
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
|BOŞ DEĞER ATANABİLİR|Int16|  
|AÇIKLAMALAR|Dize|  
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
 Microsoft SQL Server ve Oracle ODBC sürücüsü, ortak şema koleksiyonları ek olarak aşağıdaki belirli şema koleksiyonları destekler:  
  
-   Tabloları  
  
-   Sütunlar  
  
-   Yordamlar  
  
-   ProcedureColumns  
  
-   ProcedureParameters  
  
-   Görünümler  
  
-   Dizinleri  
  
### <a name="tables-and-views"></a>Tabloları ve görünümleri  
  
|ColumnName|Veri türü|  
|----------------|--------------|  
|TABLE_QUALIFIER|Dize|  
|TABLE_OWNER|Dize|  
|TABLE_NAME|Dize|  
|TABLE_TYPE|Dize|  
|AÇIKLAMALAR|Dize|  
  
### <a name="columns"></a>Sütunlar  
  
|ColumnName|Veri türü|  
|----------------|--------------|  
|TABLE_QUALIFIER|Dize|  
|TABLE_OWNER|Dize|  
|TABLE_NAME|Dize|  
|COLUMN_NAME|Dize|  
|DATA_TYPE|Int16|  
|TYPE_NAME|Dize|  
|DUYARLIK|Int32|  
|UZUNLUĞU|Int32|  
|ÖLÇEK|Int16|  
|SAYI TABANI|Int16|  
|BOŞ DEĞER ATANABİLİR|Int16|  
|AÇIKLAMALAR|Dize|  
|ORDINAL_POSITION|Int32|  
  
### <a name="procedures"></a>Yordamlar  
  
|ColumnName|Veri türü|  
|----------------|--------------|  
|PROCEDURE_QUALIFIER|Dize|  
|PROCEDURE_OWNER|Dize|  
|PROCEDURE_NAME|Dize|  
|NUM_INPUT_PARAMS|Int16|  
|NUM_OUTPUT_PARAMS|Int16|  
|NUM_RESULT_SETS|Int16|  
|AÇIKLAMALAR|Dize|  
|PROCEDURE_TYPE|Int16|  
  
### <a name="procedurecolumns"></a>ProcedureColumns  
  
|ColumnName|Veri türü|  
|----------------|--------------|  
|PROCEDURE_QUALIFIER|Dize|  
|PROCEDURE_OWNER|Dize|  
|PROCEDURE_NAME|Dize|  
|COLUMN_NAME|Dize|  
|COLUMN_TYPE|Int16|  
|DATA_TYPE|Int16|  
|TYPE_NAME|Dize|  
|DUYARLIK|Int32|  
|UZUNLUĞU|Int32|  
|ÖLÇEK|Int16|  
|SAYI TABANI|Int16|  
|BOŞ DEĞER ATANABİLİR|Int16|  
|AÇIKLAMALAR|Dize|  
|AŞIRI YÜKLEME|Int32|  
|ORDINAL_POSITION|Int32|  
  
## <a name="microsoft-jet-odbc-driver"></a>Microsoft Jet ODBC sürücüsü  
 Microsoft Jet ODBC sürücüsü, ortak şema koleksiyonları ek olarak aşağıdaki belirli şema koleksiyonları destekler:  
  
-   Tabloları  
  
-   Dizinleri  
  
-   Sütunlar  
  
-   Yordamlar  
  
-   ProcedureColumns  
  
-   ProcedureParameters  
  
-   Görünümler  
  
### <a name="tables-and-views"></a>Tabloları ve görünümleri  
  
|ColumnName|Veri türü|  
|----------------|--------------|  
|TABLE_QUALIFIER|Dize|  
|TABLE_OWNER|Dize|  
|TABLE_NAME|Dize|  
|TABLE_TYPE|Dize|  
|AÇIKLAMALAR|Dize|  
  
### <a name="columns"></a>Sütunlar  
  
|ColumnName|Veri türü|  
|----------------|--------------|  
|TABLE_QUALIFIER|Dize|  
|TABLE_OWNER|Dize|  
|TABLE_NAME|Dize|  
|COLUMN_NAME|Dize|  
|DATA_TYPE|Int16|  
|TYPE_NAME|Dize|  
|DUYARLIK|Int32|  
|UZUNLUĞU|Int32|  
|ÖLÇEK|Int16|  
|SAYI TABANI|Int16|  
|BOŞ DEĞER ATANABİLİR|Int16|  
|AÇIKLAMALAR|Dize|  
|ORDINAL_POSITION|Int32|  
  
### <a name="procedures"></a>Yordamlar  
  
|ColumnName|Veri türü|  
|----------------|--------------|  
|PROCEDURE_QUALIFIER|Dize|  
|PROCEDURE_OWNER|Dize|  
|PROCEDURE_NAME|Dize|  
|NUM_INPUT_PARAMS|Int16|  
|NUM_OUTPUT_PARAMS|Int16|  
|NUM_RESULT_SETS|Int16|  
|AÇIKLAMALAR|Dize|  
|PROCEDURE_TYPE|Int16|  
  
### <a name="procedurecolumns"></a>ProcedureColumns  
  
|ColumnName|Veri türü|  
|----------------|--------------|  
|PROCEDURE_QUALIFIER|Dize|  
|PROCEDURE_OWNER|Dize|  
|PROCEDURE_NAME|Dize|  
|COLUMN_NAME|Dize|  
|COLUMN_TYPE|Int16|  
|DATA_TYPE|Int16|  
|TYPE_NAME|Dize|  
|DUYARLIK|Int32|  
|UZUNLUĞU|Int32|  
|ÖLÇEK|Int16|  
|SAYI TABANI|Int16|  
|BOŞ DEĞER ATANABİLİR|Int16|  
|AÇIKLAMALAR|Dize|  
|AŞIRI YÜKLEME|Int32|  
|ORDINAL_POSITION|Int32|  
  
### <a name="procedureparameters"></a>ProcedureParameters  
  
|ColumnName|Veri türü|  
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
|BOŞ DEĞER ATANABİLİR|Int16|  
|AÇIKLAMALAR|Dize|  
|COLUMN_DEF|Dize|  
|SQL_DATA_TYPE|Int16|  
|SQL_DATETIME_SUB|Int16|  
|CHAR_OCTET_LENGTH|Int32|  
|ORDINAL_POSITION|Int32|  
|IS_NULLABLE|Dize|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi](https://go.microsoft.com/fwlink/?LinkId=217917)
