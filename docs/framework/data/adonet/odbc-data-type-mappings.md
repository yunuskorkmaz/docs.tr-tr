---
title: ODBC veri türü eşlemeleri
ms.date: 03/30/2017
ms.assetid: 43c35d32-831d-480f-a150-78f7e869d17f
ms.openlocfilehash: ece9397e8c8e8b9d26f8aac2298aa25173ac2d93
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2018
ms.locfileid: "44047769"
---
# <a name="odbc-data-type-mappings"></a>ODBC veri türü eşlemeleri
Aşağıdaki tabloda gösterilen gösterilmektedir [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] türü ODBC için .NET Framework Veri Sağlayıcısı'ndan veri türleri için (<xref:System.Data.Odbc>). Türü belirlenmiş erişimci yöntemlerini <xref:System.Data.Odbc.OdbcDataReader> da listelenir.  
  
|ODBC türü|[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Türü|[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] türü belirlenmiş erişimcisi|  
|---------------|----------------------------------------------------------------------|--------------------------------------------------------------------------------|  
|SQL_BIGINT|Int64|GetInt64()|  
|SQL_BINARY|Bayt]|GetBytes()|  
|SQL_BIT|Boole değeri|GetBoolean()|  
|SQL_CHAR|Dize<br /><br /> Char]|GetString() yöntemini kullanarak<br /><br /> GetChars()|  
|SQL_DECIMAL|Ondalık|GetDecimal()|  
|SQL_DOUBLE|Çift|GetDouble()|  
|SQL_GUID|Guid|GetGuid()|  
|SQL_INTEGER|Int32|GetInt32()|  
|SQL_LONG_VARCHAR|Dize<br /><br /> Char]|GetString() yöntemini kullanarak<br /><br /> GetChars()|  
|SQL_LONGVARBINARY|Bayt]|GetBytes()|  
|SQL_NUMERIC|Ondalık|GetDecimal()|  
|SQL_REAL|Tek|GetFloat()|  
|SQL_SMALLINT|Int16|GetInt16()|  
|SQL_TINYINT|Bayt|GetByte()|  
|SQL_TYPE_TIMES|DateTime|GetDateTime()|  
|SQL_TYPE_TIMESTAMP|DateTime|GetDateTime()|  
|SQL_VARBINARY|Bayt]|GetBytes()|  
|SQL_WCHAR|Dize<br /><br /> Char]|GetString() yöntemini kullanarak<br /><br /> GetChars()|  
|SQL_WLONGVARCHAR|Dize<br /><br /> Char]|GetString() yöntemini kullanarak<br /><br /> GetChars()|  
|SQL_WVARCHAR|Dize<br /><br /> Char]|GetString() yöntemini kullanarak<br /><br /> GetChars()|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ADO.NET’te Veri Alma ve Değiştirme](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)  
 [ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi](https://go.microsoft.com/fwlink/?LinkId=217917)
