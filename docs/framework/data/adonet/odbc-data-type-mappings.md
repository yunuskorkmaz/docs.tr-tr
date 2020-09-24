---
title: ODBC Veri Türü Eşlemeleri
ms.date: 03/30/2017
ms.assetid: 43c35d32-831d-480f-a150-78f7e869d17f
ms.openlocfilehash: b08c649c148aacf4050c1f7ebcc17f79d1305e0c
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91150719"
---
# <a name="odbc-data-type-mappings"></a>ODBC Veri Türü Eşlemeleri

Aşağıdaki tabloda, ODBC () için .NET Framework Veri Sağlayıcısı veri türleri için gösterilen .NET Framework türü gösterilmektedir <xref:System.Data.Odbc> . İçin yazılmış erişimci yöntemleri <xref:System.Data.Odbc.OdbcDataReader> de listelenir.  
  
|ODBC türü|.NET Framework türü|Türü belirlenmiş erişimci .NET Framework|  
|---------------|----------------------------------------------------------------------|--------------------------------------------------------------------------------|  
|SQL_BIGINT|Int64|GetInt64()|  
|SQL_BINARY|Byte []|GetBytes ()|  
|SQL_BIT|Boole|GetBoolean ()|  
|SQL_CHAR|Dize<br /><br /> Char []|GetString ()<br /><br /> GetChars ()|  
|SQL_DECIMAL|Ondalık|GetDecimal ()|  
|SQL_DOUBLE|Çift|GetDouble ()|  
|SQL_GUID|Guid|GetGuid ()|  
|SQL_INTEGER|Int32|Getınt32 ()|  
|SQL_LONG_VARCHAR|Dize<br /><br /> Char []|GetString ()<br /><br /> GetChars ()|  
|SQL_LONGVARBINARY|Byte []|GetBytes ()|  
|SQL_NUMERIC|Ondalık|GetDecimal ()|  
|SQL_REAL|Tek|GetFloat ()|  
|SQL_SMALLINT|Int16|Getınt16 ()|  
|SQL_TINYINT|Bayt|GetByte ()|  
|SQL_TYPE_TIMES|DateTime|GetDateTime ()|  
|SQL_TYPE_TIMESTAMP|DateTime|GetDateTime ()|  
|SQL_VARBINARY|Byte []|GetBytes ()|  
|SQL_WCHAR|Dize<br /><br /> Char []|GetString ()<br /><br /> GetChars ()|  
|SQL_WLONGVARCHAR|Dize<br /><br /> Char []|GetString ()<br /><br /> GetChars ()|  
|SQL_WVARCHAR|Dize<br /><br /> Char []|GetString ()<br /><br /> GetChars ()|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ADO.NET’te Veri Alma ve Değiştirme](retrieving-and-modifying-data.md)
- [ADO.NET’e Genel Bakış](ado-net-overview.md)
