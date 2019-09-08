---
title: OLE DB Şema Koleksiyonları
ms.date: 03/30/2017
ms.assetid: 6380c36b-658e-4d67-91e8-7131ef4a7c2c
ms.openlocfilehash: 2d5718c12100ebea49a6b6fab29a3790918c6ad3
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70783453"
---
# <a name="ole-db-schema-collections"></a>OLE DB Şema Koleksiyonları
Bu bölümde Microsoft SQL Server, Oracle ve Microsoft Jet için OLE DB sağlayıcıları için şema koleksiyonu desteği açıklanmaktadır.  
  
## <a name="microsoft-sql-server-ole-db-provider"></a>Microsoft SQL Server OLE DB sağlayıcısı  
 Microsoft SQL Server OLE DB sürücü, ortak şema koleksiyonlarına ek olarak aşağıdaki belirli şema koleksiyonlarını destekler:  
  
- Takvimleri  
  
- Sütunlar  
  
- Yordamlar  
  
- ProcedureParameters  
  
- Katalog  
  
- Dizinlerde  
  
### <a name="tables"></a>Takvimleri  
  
|Tation|DataType|  
|----------------|--------------|  
|TABLE_CATALOG|Dize|  
|TABLE_SCHEMA|Dize|  
|TABLE_NAME|Dize|  
|TABLE_TYPE|Dize|  
|TABLE_GUID|Guid|  
|AÇIKLAMASI|Dize|  
|TABLE_PROPID|Int64|  
|DATE_CREATED|DateTime|  
|DATE_MODIFIED|DateTime|  
  
### <a name="columns"></a>Sütunlar  
  
|Tation|DataType|  
|----------------|--------------|  
|TABLE_CATALOG|Dize|  
|TABLE_SCHEMA|Dize|  
|TABLE_NAME|Dize|  
|COLUMN_NAME|Dize|  
|COLUMN_GUID|Guid|  
|COLUMN_PROPID|Int64|  
|ORDINAL_POSITION|Int64|  
|COLUMN_HASDEFAULT|Boole değeri|  
|COLUMN_DEFAULT|Dize|  
|COLUMN_FLAGS|Int64|  
|IS_NULLABLE|Boole değeri|  
|DATA_TYPE|Int32|  
|TYPE_GUID|Guid|  
|CHARACTER_MAXIMUM_LENGTH|Int64|  
|CHARACTER_OCTET_LENGTH|Int64|  
|NUMERIC_PRECISION|Int32|  
|NUMERIC_SCALE|Int16|  
|DATETIME_PRECISION|Int64|  
|CHARACTER_SET_CATALOG|Dize|  
|CHARACTER_SET_SCHEMA|Dize|  
|CHARACTER_SET_NAME|Dize|  
|COLLATION_CATALOG|Dize|  
|COLLATION_SCHEMA|Dize|  
|COLLATION_NAME|Dize|  
|DOMAIN_CATALOG|Dize|  
|DOMAIN_SCHEMA|Dize|  
|DOMAIN_NAME|Dize|  
|AÇIKLAMASI|Dize|  
|COLUMN_LCID|Int32|  
|COLUMN_COMPFLAGS|Int32|  
|COLUMN_SORTID|Int32|  
|COLUMN_TDSCOLLATION|Byte[]|  
|IS_COMPUTED|Boole değeri|  
  
### <a name="procedures"></a>Yordamlar  
  
|Tation|DataType|  
|----------------|--------------|  
|PROCEDURE_CATALOG|Dize|  
|PROCEDURE_SCHEMA|Dize|  
|PROCEDURE_NAME|Dize|  
|PROCEDURE_TYPE|Int16|  
|PROCEDURE_DEFINITION|Dize|  
|AÇIKLAMASI|Dize|  
|DATE_CREATED|DateTime|  
|DATE_MODIFIED|DateTime|  
  
### <a name="procedureparameters"></a>ProcedureParameters  
  
|Tation|DataType|  
|----------------|--------------|  
|PROCEDURE_CATALOG|Dize|  
|PROCEDURE_SCHEMA|Dize|  
|PROCEDURE_NAME|Dize|  
|PARAMETER_NAME|Dize|  
|ORDINAL_POSITION|Int32|  
|PARAMETER_TYPE|Int32|  
|PARAMETER_HASDEFAULT|Boole değeri|  
|PARAMETER_DEFAULT|Dize|  
|IS_NULLABLE|Boole değeri|  
|DATA_TYPE|Int32|  
|CHARACTER_MAXIMUM_LENGTH|Int64|  
|CHARACTER_OCTET_LENGTH|Int64|  
|NUMERIC_PRECISION|Int32|  
|NUMERIC_SCALE|Int16|  
|AÇIKLAMASI|Dize|  
|TYPE_NAME|Dize|  
|LOCAL_TYPE_NAME|Dize|  
  
### <a name="catalog"></a>Katalog  
  
|Tation|DataType|  
|----------------|--------------|  
|CATALOG_NAME|Dize|  
|AÇIKLAMASI|Dize|  
  
### <a name="indexes"></a>Dizinlerde  
  
|Tation|DataType|  
|----------------|--------------|  
|TABLE_CATALOG|Dize|  
|TABLE_SCHEMA|Dize|  
|TABLE_NAME|Dize|  
|INDEX_CATALOG|Dize|  
|INDEX_SCHEMA|Dize|  
|INDEX_NAME|Dize|  
|PRIMARY_KEY|Boole değeri|  
|EŞI|Boole değeri|  
|CLUSTERED|Boole değeri|  
|TÜRÜYLE|Int32|  
|FILL_FACTOR|Int32|  
|INITIAL_SIZE|Int32|  
|NULLS|Int32|  
|SORT_BOOKMARKS|Boole değeri|  
|AUTO_UPDATE|Boole değeri|  
|NULL_COLLATION|Int32|  
|ORDINAL_POSITION|Int64|  
|COLUMN_NAME|Dize|  
|COLUMN_GUID|Guid|  
|COLUMN_PROPID|Int64|  
|MEDIĞINDEN|Int16|  
|ITE|Ondalık|  
|SAYFALARI|Int32|  
|FILTER_CONDITION|Dize|  
|ILMIŞTIR|Boole değeri|  
  
## <a name="microsoft-oracle-ole-db-provider"></a>Microsoft Oracle OLE DB sağlayıcısı  
 Microsoft Oracle OLE DB sürücüsü, ortak şema koleksiyonlarına ek olarak aşağıdaki belirli şema koleksiyonlarını destekler:  
  
- Takvimleri  
  
- Sütunlar  
  
- Yordamlar  
  
- ProcedureColumns  
  
- ProcedureParameters  
  
- Görünümler  
  
- Dizinlerde  
  
### <a name="tables"></a>Takvimleri  
  
|Tation|DataType|  
|----------------|--------------|  
|TABLE_CATALOG|Dize|  
|TABLE_SCHEMA|Dize|  
|TABLE_NAME|Dize|  
|TABLE_TYPE|Dize|  
|TABLE_GUID|Guid|  
|AÇIKLAMASI|Dize|  
|TABLE_PROPID|Int64|  
|DATE_CREATED|DateTime|  
|DATE_MODIFIED|DateTime|  
  
### <a name="columns"></a>Sütunlar  
  
|Tation|DataType|  
|----------------|--------------|  
|TABLE_CATALOG|Dize|  
|TABLE_SCHEMA|Dize|  
|TABLE_NAME|Dize|  
|COLUMN_NAME|Dize|  
|COLUMN_GUID|Guid|  
|COLUMN_PROPID|Int64|  
|ORDINAL_POSITION|Int64|  
|COLUMN_HASDEFAULT|Boole değeri|  
|COLUMN_DEFAULT|Dize|  
|COLUMN_FLAGS|Int64|  
|IS_NULLABLE|Boole değeri|  
|DATA_TYPE|Int32|  
|TYPE_GUID|Guid|  
|CHARACTER_MAXIMUM_LENGTH|Int64|  
|CHARACTER_OCTET_LENGTH|Int64|  
|NUMERIC_PRECISION|Int32|  
|NUMERIC_SCALE|Int16|  
|DATETIME_PRECISION|Int64|  
|CHARACTER_SET_CATALOG|Dize|  
|CHARACTER_SET_SCHEMA|Dize|  
|CHARACTER_SET_NAME|Dize|  
|COLLATION_CATALOG|Dize|  
|COLLATION_SCHEMA|Dize|  
|COLLATION_NAME|Dize|  
|DOMAIN_CATALOG|Dize|  
|DOMAIN_SCHEMA|Dize|  
|DOMAIN_NAME|Dize|  
|AÇIKLAMASI|Dize|  
  
### <a name="procedures"></a>Yordamlar  
  
|Tation|DataType|  
|----------------|--------------|  
|PROCEDURE_CATALOG|Dize|  
|PROCEDURE_SCHEMA|Dize|  
|PROCEDURE_NAME|Dize|  
|PROCEDURE_TYPE|Int16|  
|PROCEDURE_DEFINITION|Dize|  
|AÇIKLAMASI|Dize|  
|DATE_CREATED|DateTime|  
|DATE_MODIFIED|DateTime|  
  
### <a name="procedurecolumns"></a>ProcedureColumns  
  
|Tation|DataType|  
|----------------|--------------|  
|PROCEDURE_CATALOG|Dize|  
|PROCEDURE_SCHEMA|Dize|  
|PROCEDURE_NAME|Dize|  
|COLUMN_NAME|Dize|  
|COLUMN_GUID|Guid|  
|COLUMN_PROPID|Int64|  
|ROWSET_NUMBER|Int64|  
|ORDINAL_POSITION|Int64|  
|IS_NULLABLE|Boole değeri|  
|DATA_TYPE|Int32|  
|TYPE_GUID|Guid|  
|CHARACTER_MAXIMUM_LENGTH|Int64|  
|CHARACTER_OCTET_LENGTH|Int64|  
|NUMERIC_PRECISION|Int32|  
|NUMERIC_SCALE|Int16|  
|AÇIKLAMASI|Dize|  
|YÜKLEMEK|Int16|  
  
### <a name="views"></a>Görünümler  
  
|Tation|DataType|  
|----------------|--------------|  
|TABLE_CATALOG|Dize|  
|TABLE_SCHEMA|Dize|  
|TABLE_NAME|Dize|  
|VIEW_DEFINITION|Dize|  
|CHECK_OPTION|Boole değeri|  
|IS_UPDATABLE|Boole değeri|  
|AÇIKLAMASI|Dize|  
|DATE_CREATED|DateTime|  
|DATE_MODIFIED|DateTime|  
  
### <a name="indexes"></a>Dizinlerde  
  
|Tation|DataType|  
|----------------|--------------|  
|TABLE_CATALOG|Dize|  
|TABLE_SCHEMA|Dize|  
|TABLE_NAME|Dize|  
|INDEX_CATALOG|Dize|  
|INDEX_SCHEMA|Dize|  
|INDEX_NAME|Dize|  
|PRIMARY_KEY|Boole değeri|  
|EŞI|Boole değeri|  
|CLUSTERED|Boole değeri|  
|TÜRÜYLE|Int32|  
|FILL_FACTOR|Int32|  
|INITIAL_SIZE|Int32|  
|NULLS|Int32|  
|SORT_BOOKMARKS|Boole değeri|  
|AUTO_UPDATE|Boole değeri|  
|NULL_COLLATION|Int32|  
|ORDINAL_POSITION|Int64|  
|COLUMN_NAME|Dize|  
|COLUMN_GUID|Guid|  
|COLUMN_PROPID|Int64|  
|MEDIĞINDEN|Int16|  
|ITE|Ondalık|  
|SAYFALARI|Int32|  
|FILTER_CONDITION|Dize|  
|ILMIŞTIR|Boole değeri|  
  
## <a name="microsoft-jet-ole-db-provider"></a>Microsoft Jet OLE DB sağlayıcısı  
 Microsoft Jet OLE DB sürücüsü, ortak şema koleksiyonlarına ek olarak aşağıdaki belirli şema koleksiyonlarını destekler:  
  
- Takvimleri  
  
- Sütunlar  
  
- Yordamlar  
  
- Görünümler  
  
- Dizinlerde  
  
### <a name="tables"></a>Takvimleri  
  
|Tation|DataType|  
|----------------|--------------|  
|TABLE_CATALOG|Dize|  
|TABLE_SCHEMA|Dize|  
|TABLE_NAME|Dize|  
|TABLE_TYPE|Dize|  
|TABLE_GUID|Guid|  
|AÇIKLAMASI|Dize|  
|TABLE_PROPID|Int64|  
|DATE_CREATED|DateTime|  
|DATE_MODIFIED|DateTime|  
  
### <a name="columns"></a>Sütunlar  
  
|Tation|DataType|  
|----------------|--------------|  
|TABLE_CATALOG|Dize|  
|TABLE_SCHEMA|Dize|  
|TABLE_NAME|Dize|  
|COLUMN_NAME|Dize|  
|COLUMN_GUID|Guid|  
|COLUMN_PROPID|Int64|  
|ORDINAL_POSITION|Int64|  
|COLUMN_HASDEFAULT|Boole değeri|  
|COLUMN_DEFAULT|Dize|  
|COLUMN_FLAGS|Int64|  
|IS_NULLABLE|Boole değeri|  
|DATA_TYPE|Int32|  
|TYPE_GUID|Guid|  
|CHARACTER_MAXIMUM_LENGTH|Int64|  
|CHARACTER_OCTET_LENGTH|Int64|  
|NUMERIC_PRECISION|Int32|  
|NUMERIC_SCALE|Int16|  
|DATETIME_PRECISION|Int64|  
|CHARACTER_SET_CATALOG|Dize|  
|CHARACTER_SET_SCHEMA|Dize|  
|CHARACTER_SET_NAME|Dize|  
|COLLATION_CATALOG|Dize|  
|COLLATION_SCHEMA|Dize|  
|COLLATION_NAME|Dize|  
|DOMAIN_CATALOG|Dize|  
|DOMAIN_SCHEMA|Dize|  
|DOMAIN_NAME|Dize|  
|AÇIKLAMASI|Dize|  
  
### <a name="procedures"></a>Yordamlar  
  
|Tation|DataType|  
|----------------|--------------|  
|PROCEDURE_CATALOG|Dize|  
|PROCEDURE_SCHEMA|Dize|  
|PROCEDURE_NAME|Dize|  
|PROCEDURE_TYPE|Int16|  
|PROCEDURE_DEFINITION|Dize|  
|AÇIKLAMASI|Dize|  
|DATE_CREATED|DateTime|  
|DATE_MODIFIED|DateTime|  
  
### <a name="views"></a>Görünümler  
  
|Tation|DataType|  
|----------------|--------------|  
|TABLE_CATALOG|Dize|  
|TABLE_SCHEMA|Dize|  
|TABLE_NAME|Dize|  
|VIEW_DEFINITION|Dize|  
|CHECK_OPTION|Boole değeri|  
|IS_UPDATABLE|Boole değeri|  
|AÇIKLAMASI|Dize|  
|DATE_CREATED|DateTime|  
|DATE_MODIFIED|DateTime|  
  
### <a name="indexes"></a>Dizinlerde  
  
|Tation|DataType|  
|----------------|--------------|  
|TABLE_CATALOG|Dize|  
|TABLE_SCHEMA|Dize|  
|TABLE_NAME|Dize|  
|INDEX_CATALOG|Dize|  
|INDEX_SCHEMA|Dize|  
|INDEX_NAME|Dize|  
|PRIMARY_KEY|Boole değeri|  
|EŞI|Boole değeri|  
|CLUSTERED|Boole değeri|  
|TÜRÜYLE|Int32|  
|FILL_FACTOR|Int32|  
|INITIAL_SIZE|Int32|  
|NULLS|Int32|  
|SORT_BOOKMARKS|Boole değeri|  
|AUTO_UPDATE|Boole değeri|  
|NULL_COLLATION|Int32|  
|ORDINAL_POSITION|Int64|  
|COLUMN_NAME|Dize|  
|COLUMN_GUID|Guid|  
|COLUMN_PROPID|Int64|  
|MEDIĞINDEN|Int16|  
|ITE|Ondalık|  
|SAYFALARI|Int32|  
|FILTER_CONDITION|Dize|  
|ILMIŞTIR|Boole değeri|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ADO.NET’e Genel Bakış](ado-net-overview.md)
