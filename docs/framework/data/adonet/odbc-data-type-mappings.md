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
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 6c383207c8290932c407af8c317775b5943b5450
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
---
# <a name="odbc-data-type-mappings"></a>ODBC veri türü eşlemeleri
Aşağıdaki tabloda oluşturulursa gösterilmektedir [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] ODBC için .NET Framework Veri Sağlayıcısı'ndan veri türleri için türü (<xref:System.Data.Odbc>). Yazılı erişimci yöntemleri <xref:System.Data.Odbc.OdbcDataReader> da listelenir.  
  
|ODBC türü|[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]türü|[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]yazılı erişimcisi|  
|---------------|----------------------------------------------------------------------|--------------------------------------------------------------------------------|  
|SQL_BIGINT|Int64|GetInt64()|  
|SQL_BINARY|Byte]|GetBytes()|  
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
 [ADO.NET’te Veri Alma ve Değiştirme](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)  
 [ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi](http://go.microsoft.com/fwlink/?LinkId=217917)
