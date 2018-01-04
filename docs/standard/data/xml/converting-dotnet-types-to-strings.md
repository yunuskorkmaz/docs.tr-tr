---
title: ".NET Framework türleri dizeleri dönüştürme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: dc2e2b65-f623-4dc3-938b-d2a054d6832c
caps.latest.revision: "3"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 6ca134e13593fdacd759b0000e0e159f76ea067f
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="converting-net-framework-types-to-strings"></a>.NET Framework türleri dizeleri dönüştürme
.NET Framework türü bir dizeye dönüştürmek istediğiniz kullanırsanız **ToString** yöntemi. **ToString** yöntemi geçirilen tür bir dize gösterimini döndürür. Aşağıdaki tabloda XML Şeması (XSD) belirtimleri eşleyen biçiminde bir dize döndürecek .NET Framework türleri listelenmektedir.  
  
|.NET Framework türü|Döndürülen dize türü|  
|-------------------------|--------------------------|  
|Boole değeri|"true", "false"|  
|Single.PositiveInfinity|"INF"|  
|Single.NegativeInfinity|"-INF"|  
|Double.PositiveInfinity|"INF"|  
|Double.NegativeInfinity|"-INF"|  
|DateTime|Biçimidir yyyy-aa-ddTHH:mm:sszzzzzz ve onun alt kümeleri.|  
|TimeSpan|Biçimidir PnYnMnTnHnMnS, örneğin, `P2Y10M15DT10H30M20S` 2 yıl, 10 ay, 15 gün, 10hours süresi 30 dakika ve 20 saniyedir.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [XML Veri Türlerini Dönüştürme](../../../../docs/standard/data/xml/conversion-of-xml-data-types.md)  
 [.NET Framework Veri Türleri için Dizeleri Dönüştürme](../../../../docs/standard/data/xml/converting-strings-to-dotnet-data-types.md)
