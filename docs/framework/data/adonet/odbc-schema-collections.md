---
title: ODBC şeması koleksiyonları
ms.date: 03/30/2017
ms.assetid: 1bb126a5-ceec-4649-a4bc-8aa19e801046
ms.openlocfilehash: 36d0859b897bfcea33803c219ade14722ed90421
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
---
# <a name="odbc-schema-collections"></a>ODBC şeması koleksiyonları
Bu bölümde, Microsoft SQL Server, Oracle ve Microsoft Jet ODBC sürücüleri için şema koleksiyonu desteği açıklanmaktadır.  
  
## <a name="microsoft-sql-server-odbc-driver"></a>Microsoft SQL Server ODBC sürücüsü  
 Microsoft SQL Server ODBC sürücüsü ortak şeması koleksiyonları ek olarak aşağıdaki belirli şeması koleksiyonları destekler:  
  
-   tabloları  
  
-   Dizinler  
  
-   Sütunlar  
  
-   Yordamlar  
  
-   ProcedureColumns  
  
-   ProcedureParameters  
  
-   Görünümler  
  
### <a name="tables-and-views"></a>Tabloları ve görünümleri  
  
|columnName|Veri türü|  
|----------------|--------------|  
|TABLE_CAT|Dize|  
|TABLE_SCHEM|Dize|  
|TABLE_NAME|Dize|  
|TABLE_TYPE|Dize|  
|AÇIKLAMALAR|Dize|  
  
### <a name="indexes"></a>Dizinler  
  
|columnName|Veri türü|  
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
  
|columnName|Veri türü|  
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
  
|columnName|Veri türü|  
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
  
|columnName|Veri türü|  
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
  
|columnName|Veri türü|  
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
 Microsoft SQL Server Oracle ODBC sürücüsü ortak şeması koleksiyonları ek olarak aşağıdaki belirli şeması koleksiyonları destekler:  
  
-   tabloları  
  
-   Sütunlar  
  
-   Yordamlar  
  
-   ProcedureColumns  
  
-   ProcedureParameters  
  
-   Görünümler  
  
-   Dizinler  
  
### <a name="tables-and-views"></a>Tabloları ve görünümleri  
  
|columnName|Veri türü|  
|----------------|--------------|  
|TABLE_QUALIFIER|Dize|  
|TABLE_OWNER|Dize|  
|TABLE_NAME|Dize|  
|TABLE_TYPE|Dize|  
|AÇIKLAMALAR|Dize|  
  
### <a name="columns"></a>Sütunlar  
  
|columnName|Veri türü|  
|----------------|--------------|  
|TABLE_QUALIFIER|Dize|  
|TABLE_OWNER|Dize|  
|TABLE_NAME|Dize|  
|COLUMN_NAME|Dize|  
|DATA_TYPE|Int16|  
|TYPE_NAME|Dize|  
|DUYARLILIK|Int32|  
|UZUNLUĞU|Int32|  
|ÖLÇEK|Int16|  
|SAYI TABANINI|Int16|  
|BOŞ DEĞER ATANABİLİR|Int16|  
|AÇIKLAMALAR|Dize|  
|ORDINAL_POSITION|Int32|  
  
### <a name="procedures"></a>Yordamlar  
  
|columnName|Veri türü|  
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
  
|columnName|Veri türü|  
|----------------|--------------|  
|PROCEDURE_QUALIFIER|Dize|  
|PROCEDURE_OWNER|Dize|  
|PROCEDURE_NAME|Dize|  
|COLUMN_NAME|Dize|  
|COLUMN_TYPE|Int16|  
|DATA_TYPE|Int16|  
|TYPE_NAME|Dize|  
|DUYARLILIK|Int32|  
|UZUNLUĞU|Int32|  
|ÖLÇEK|Int16|  
|SAYI TABANINI|Int16|  
|BOŞ DEĞER ATANABİLİR|Int16|  
|AÇIKLAMALAR|Dize|  
|AŞIRI YÜKLEME|Int32|  
|ORDINAL_POSITION|Int32|  
  
## <a name="microsoft-jet-odbc-driver"></a>Microsoft Jet ODBC sürücüsü  
 Microsoft Jet ODBC sürücüsü ortak şeması koleksiyonları ek olarak aşağıdaki belirli şeması koleksiyonları destekler:  
  
-   tabloları  
  
-   Dizinler  
  
-   Sütunlar  
  
-   Yordamlar  
  
-   ProcedureColumns  
  
-   ProcedureParameters  
  
-   Görünümler  
  
### <a name="tables-and-views"></a>Tabloları ve görünümleri  
  
|columnName|Veri türü|  
|----------------|--------------|  
|TABLE_QUALIFIER|Dize|  
|TABLE_OWNER|Dize|  
|TABLE_NAME|Dize|  
|TABLE_TYPE|Dize|  
|AÇIKLAMALAR|Dize|  
  
### <a name="columns"></a>Sütunlar  
  
|columnName|Veri türü|  
|----------------|--------------|  
|TABLE_QUALIFIER|Dize|  
|TABLE_OWNER|Dize|  
|TABLE_NAME|Dize|  
|COLUMN_NAME|Dize|  
|DATA_TYPE|Int16|  
|TYPE_NAME|Dize|  
|DUYARLILIK|Int32|  
|UZUNLUĞU|Int32|  
|ÖLÇEK|Int16|  
|SAYI TABANINI|Int16|  
|BOŞ DEĞER ATANABİLİR|Int16|  
|AÇIKLAMALAR|Dize|  
|ORDINAL_POSITION|Int32|  
  
### <a name="procedures"></a>Yordamlar  
  
|columnName|Veri türü|  
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
  
|columnName|Veri türü|  
|----------------|--------------|  
|PROCEDURE_QUALIFIER|Dize|  
|PROCEDURE_OWNER|Dize|  
|PROCEDURE_NAME|Dize|  
|COLUMN_NAME|Dize|  
|COLUMN_TYPE|Int16|  
|DATA_TYPE|Int16|  
|TYPE_NAME|Dize|  
|DUYARLILIK|Int32|  
|UZUNLUĞU|Int32|  
|ÖLÇEK|Int16|  
|SAYI TABANINI|Int16|  
|BOŞ DEĞER ATANABİLİR|Int16|  
|AÇIKLAMALAR|Dize|  
|AŞIRI YÜKLEME|Int32|  
|ORDINAL_POSITION|Int32|  
  
### <a name="procedureparameters"></a>ProcedureParameters  
  
|columnName|Veri türü|  
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
 [ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi](http://go.microsoft.com/fwlink/?LinkId=217917)
