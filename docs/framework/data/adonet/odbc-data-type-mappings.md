---
title: "ODBC veri türü eşlemeleri"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 43c35d32-831d-480f-a150-78f7e869d17f
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 82c4a84f1aee5872a899d8d42a06d22abc10b603
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="odbc-data-type-mappings"></a>ODBC veri türü eşlemeleri
Aşağıdaki tabloda oluşturulursa gösterilmektedir [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] ODBC için .NET Framework Veri Sağlayıcısı'ndan veri türleri için türü (<xref:System.Data.Odbc>). Yazılı erişimci yöntemleri <xref:System.Data.Odbc.OdbcDataReader> da listelenir.  
  
|ODBC türü|[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]türü|[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]yazılı erişimcisi|  
|---------------|----------------------------------------------------------------------|--------------------------------------------------------------------------------|  
|SQL_BIGINT|Int64|GetInt64()|  
|UZUN SQL_BINARY|Byte]|GetBytes()|  
|SQL_BIT|Boole değeri|GetBoolean()|  
|SQL_CHAR|Dize<br /><br /> Char]|GetString()<br /><br /> GetChars()|  
|SQL_DECIMAL|Ondalık|GetDecimal()|  
|SQL_DOUBLE|Çift|GetDouble()|  
|SQL_GUID|Guid|GetGuid()|  
|SQL_INTEGER|Int32|GetInt32()|  
|SQL_LONG_VARCHAR|Dize<br /><br /> Char]|GetString()<br /><br /> GetChars()|  
|SQL_LONGVARBINARY|Byte]|GetBytes()|  
|SQL_NUMERIC|Ondalık|GetDecimal()|  
|SQL_REAL|Tek|GetFloat()|  
|SQL_SMALLINT|Int16|GetInt16()|  
|SQL_TINYINT|Bayt|GetByte()|  
|SQL_TYPE_TIMES|DateTime|GetDateTime()|  
|SQL_TYPE_TIMESTAMP|DateTime|GetDateTime()|  
|SQL_VARBINARY|Byte]|GetBytes()|  
|SQL_WCHAR|Dize<br /><br /> Char]|GetString()<br /><br /> GetChars()|  
|SQL_WLONGVARCHAR|Dize<br /><br /> Char]|GetString()<br /><br /> GetChars()|  
|SQL_WVARCHAR|Dize<br /><br /> Char]|GetString()<br /><br /> GetChars()|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Alma ve ADO.NET veri değiştirme](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)  
 [ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi](http://go.microsoft.com/fwlink/?LinkId=217917)
