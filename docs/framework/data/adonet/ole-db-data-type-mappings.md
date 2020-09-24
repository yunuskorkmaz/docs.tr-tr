---
title: OLE DB Veri Türü Eşlemeleri
ms.date: 03/30/2017
ms.assetid: 04bcb259-59d3-4fd7-894d-4f0dd0c68069
ms.openlocfilehash: 7f3b498e39feac4a6fe98e739793d20e0268b8f4
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91150706"
---
# <a name="ole-db-data-type-mappings"></a>OLE DB Veri Türü Eşlemeleri

Aşağıdaki tabloda, ADO ve OLE DB () için .NET Framework Veri Sağlayıcısı veri türleri için gösterilen .NET Framework türü gösterilmektedir <xref:System.Data.OleDb> . İçin yazılmış erişimci yöntemleri <xref:System.Data.OleDb.OleDbDataReader> de listelenir.  
  
|ADO türü|OLE DB türü|.NET Framework türü|Türü belirlenmiş erişimci .NET Framework|  
|--------------|-----------------|----------------------------------------------------------------------|--------------------------------------------------------------------------------|  
|adBigInt|DBTYPE_I8|Int64|GetInt64()|  
|adBinary|DBTYPE_BYTES|Byte []|GetBytes ()|  
|adBoolean|DBTYPE_BOOL|Boole|GetBoolean ()|  
|adBSTR|DBTYPE_BSTR|Dize|GetString ()|  
|Adbölüm|DBTYPE_HCHAPTER|İle desteklenir `DataReader` . Bkz. [DataReader kullanarak veri alma](retrieving-data-using-a-datareader.md).|GetValue ()|  
|adChar|DBTYPE_STR|Dize|GetString ()|  
|adCurrency|DBTYPE_CY|Ondalık|GetDecimal ()|  
|adDate|DBTYPE_DATE|DateTime|GetDateTime ()|  
|adDBDate|DBTYPE_DBDATE|DateTime|GetDateTime ()|  
|adDBTime|DBTYPE_DBTIME|DateTime|GetDateTime ()|  
|adDBTimeStamp|DBTYPE_DBTIMESTAMP|DateTime|GetDateTime ()|  
|adDecimal|DBTYPE_DECIMAL|Ondalık|GetDecimal ()|  
|adDouble|DBTYPE_R8|Çift|GetDouble ()|  
|adError|DBTYPE_ERROR|ExternalException|GetValue ()|  
|adFileTime|DBTYPE_FILETIME|DateTime|GetDateTime ()|  
|adGUID|DBTYPE_GUID|Guid|GetGuid ()|  
|adIDispatch|DBTYPE_IDISPATCH *|Nesne|GetValue ()|  
|adInteger|DBTYPE_I4|Int32|Getınt32 ()|  
|adIUnknown|DBTYPE_IUNKNOWN *|Nesne|GetValue ()|  
|adNumeric|DBTYPE_NUMERIC|Ondalık|GetDecimal ()|  
|adPropVariant|DBTYPE_PROPVARIANT|Nesne|GetValue ()|  
|adSingle|DBTYPE_R4|Tek|GetFloat ()|  
|adSmallInt|DBTYPE_I2|Int16|Getınt16 ()|  
|adTinyInt|DBTYPE_I1|Bayt|GetByte ()|  
|Adunsignedbigınt|DBTYPE_UI8|UInt64|GetValue ()|  
|adUnsignedInt|DBTYPE_UI4|UInt32|GetValue ()|  
|adUnsignedSmallInt|DBTYPE_UI2|UInt16|GetValue ()|  
|Adunsignedtınyıint|DBTYPE_UI1|Bayt|GetByte ()|  
|adVariant|DBTYPE_VARIANT|Nesne|GetValue ()|  
|adWChar|DBTYPE_WSTR|Dize|GetString ()|  
|adUserDefined|DBTYPE_UDT|desteklenmiyor||  
|adVarNumeric|DBTYPE_VARNUMERIC|desteklenmiyor||  
  
 \* OLE DB türleri `DBTYPE_IUNKNOWN` ve `DBTYPE_IDISPATCH` , nesne başvurusu, işaretçinin sıralanmış bir gösterimidir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ADO.NET’te Veri Alma ve Değiştirme](retrieving-and-modifying-data.md)
- [ADO.NET’e Genel Bakış](ado-net-overview.md)
