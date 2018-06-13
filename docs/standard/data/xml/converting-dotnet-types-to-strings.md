---
title: .NET Framework türleri dizeleri dönüştürme
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: dc2e2b65-f623-4dc3-938b-d2a054d6832c
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b1e9b22a4bc876e9b02ec0da0439682082d2d706
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33568777"
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
