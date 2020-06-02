---
title: .NET Framework Türlerini Dizelere Dönüştürme
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: dc2e2b65-f623-4dc3-938b-d2a054d6832c
ms.openlocfilehash: d232fb0e3ea4cf3189294d6e6f43ae9270417407
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84287824"
---
# <a name="converting-net-framework-types-to-strings"></a>.NET Framework Türlerini Dizelere Dönüştürme
Bir .NET Framework türünü dizeye dönüştürmek istiyorsanız, **ToString** yöntemini kullanın. **ToString** yöntemi geçirilen türün dize gösterimini döndürür. Aşağıdaki tabloda, XML şeması (XSD) belirtimlerine eşlenen bir biçimde dize döndüren .NET Framework türleri listelenmektedir.  
  
|.NET Framework türü|Döndürülen dize türü|  
|-------------------------|--------------------------|  
|Boole|"true", "false"|  
|Single. PositiveInfinity|'SI|  
|Tek. NegativeInfinity|"-INF"|  
|Double. PositiveInfinity|'SI|  
|Double. NegativeInfinity|"-INF"|  
|DateTime|Biçim yyyy-MM-ddTHH: mm: sszzzzzz ve alt kümeleridir.|  
|Timespan|Biçim Pnazmntnhnmns, örneğin `P2Y10M15DT10H30M20S` 2 yıl, 10 ay, 15 gün, 10 saat, 30 dakika ve 20 saniye.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XML Veri Türlerini Dönüştürme](conversion-of-xml-data-types.md)
- [.NET Framework Veri Türleri için Dizeleri Dönüştürme](converting-strings-to-dotnet-data-types.md)
