---
description: 'Daha fazla bilgi edinin: ODBC veri türü eşlemeleri'
title: ODBC Veri Türü Eşlemeleri
ms.date: 03/30/2017
ms.assetid: 43c35d32-831d-480f-a150-78f7e869d17f
ms.openlocfilehash: 0589f065da852158d35ee1104618dd13e5b2d36f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99786218"
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
