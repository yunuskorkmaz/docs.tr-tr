---
title: OLE DB şema koleksiyonları
ms.date: 03/30/2017
ms.assetid: 6380c36b-658e-4d67-91e8-7131ef4a7c2c
ms.openlocfilehash: 1ab6426875b73b400a59b7e4cf155615d7472d05
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43514495"
---
# <a name="ole-db-schema-collections"></a>OLE DB şema koleksiyonları
Bu bölümde, Microsoft SQL Server, Oracle ve Microsoft Jet OLE DB sağlayıcıları için şema koleksiyonu desteğini açıklar.  
  
## <a name="microsoft-sql-server-ole-db-provider"></a>Microsoft SQL Server'ı OLE DB sağlayıcısı  
 Microsoft SQL Server OLE DB sürücüsü aşağıdaki özel şema koleksiyonları ortak şema koleksiyonları yanı sıra destekler:  
  
-   Tabloları  
  
-   Sütunlar  
  
-   Yordamlar  
  
-   ProcedureParameters  
  
-   Kataloğu  
  
-   Dizinleri  
  
### <a name="tables"></a>Tabloları  
  
|ColumnName|Veri türü|  
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
  
|ColumnName|Veri türü|  
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
|COLUMN_TDSCOLLATION|Bayt]|  
|IS_COMPUTED|Boole değeri|  
  
### <a name="procedures"></a>Yordamlar  
  
|ColumnName|Veri türü|  
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
  
|ColumnName|Veri türü|  
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
  
### <a name="catalog"></a>Kataloğu  
  
|ColumnName|Veri türü|  
|----------------|--------------|  
|CATALOG_NAME|Dize|  
|AÇIKLAMASI|Dize|  
  
### <a name="indexes"></a>Dizinleri  
  
|ColumnName|Veri türü|  
|----------------|--------------|  
|TABLE_CATALOG|Dize|  
|TABLE_SCHEMA|Dize|  
|TABLE_NAME|Dize|  
|INDEX_CATALOG|Dize|  
|INDEX_SCHEMA|Dize|  
|INDEX_NAME|Dize|  
|İŞLEM|Boole değeri|  
|BENZERSİZ|Boole değeri|  
|CLUSTERED|Boole değeri|  
|TÜRÜ|Int32|  
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
|HARMANLAMA|Int16|  
|ÖNEM DÜZEYİ|Ondalık|  
|SAYFALARI|Int32|  
|FILTER_CONDITION|Dize|  
|TÜMLEŞİK|Boole değeri|  
  
## <a name="microsoft-oracle-ole-db-provider"></a>Microsoft Oracle OLE DB sağlayıcısı  
 Microsoft Oracle OLE DB sürücüsü aşağıdaki özel şema koleksiyonları ortak şema koleksiyonları yanı sıra destekler:  
  
-   Tabloları  
  
-   Sütunlar  
  
-   Yordamlar  
  
-   ProcedureColumns  
  
-   ProcedureParameters  
  
-   Görünümler  
  
-   Dizinleri  
  
### <a name="tables"></a>Tabloları  
  
|ColumnName|Veri türü|  
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
  
|ColumnName|Veri türü|  
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
  
|ColumnName|Veri türü|  
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
  
|ColumnName|Veri türü|  
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
|AŞIRI YÜKLEME|Int16|  
  
### <a name="views"></a>Görünümler  
  
|ColumnName|Veri türü|  
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
  
### <a name="indexes"></a>Dizinleri  
  
|ColumnName|Veri türü|  
|----------------|--------------|  
|TABLE_CATALOG|Dize|  
|TABLE_SCHEMA|Dize|  
|TABLE_NAME|Dize|  
|INDEX_CATALOG|Dize|  
|INDEX_SCHEMA|Dize|  
|INDEX_NAME|Dize|  
|İŞLEM|Boole değeri|  
|BENZERSİZ|Boole değeri|  
|CLUSTERED|Boole değeri|  
|TÜRÜ|Int32|  
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
|HARMANLAMA|Int16|  
|ÖNEM DÜZEYİ|Ondalık|  
|SAYFALARI|Int32|  
|FILTER_CONDITION|Dize|  
|TÜMLEŞİK|Boole değeri|  
  
## <a name="microsoft-jet-ole-db-provider"></a>Microsoft Jet OLE DB sağlayıcısı  
 Microsoft Jet OLE DB sürücüsü aşağıdaki özel şema koleksiyonları ortak şema koleksiyonları yanı sıra destekler:  
  
-   Tabloları  
  
-   Sütunlar  
  
-   Yordamlar  
  
-   Görünümler  
  
-   Dizinleri  
  
### <a name="tables"></a>Tabloları  
  
|ColumnName|Veri türü|  
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
  
|ColumnName|Veri türü|  
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
  
|ColumnName|Veri türü|  
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
  
|ColumnName|Veri türü|  
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
  
### <a name="indexes"></a>Dizinleri  
  
|ColumnName|Veri türü|  
|----------------|--------------|  
|TABLE_CATALOG|Dize|  
|TABLE_SCHEMA|Dize|  
|TABLE_NAME|Dize|  
|INDEX_CATALOG|Dize|  
|INDEX_SCHEMA|Dize|  
|INDEX_NAME|Dize|  
|İŞLEM|Boole değeri|  
|BENZERSİZ|Boole değeri|  
|CLUSTERED|Boole değeri|  
|TÜRÜ|Int32|  
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
|HARMANLAMA|Int16|  
|ÖNEM DÜZEYİ|Ondalık|  
|SAYFALARI|Int32|  
|FILTER_CONDITION|Dize|  
|TÜMLEŞİK|Boole değeri|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi](https://go.microsoft.com/fwlink/?LinkId=217917)
