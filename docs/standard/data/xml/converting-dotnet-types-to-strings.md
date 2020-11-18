---
title: .NET türlerini dizelere dönüştürme
ms.date: 03/30/2017
ms.assetid: dc2e2b65-f623-4dc3-938b-d2a054d6832c
ms.openlocfilehash: 9744224b4346b865a112b0eb6957f12553e1ec5f
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94830993"
---
# <a name="convert-net-types-to-strings"></a>.NET türlerini dizelere Dönüştür

Bir .NET türünü dizeye dönüştürmek istiyorsanız, **ToString** yöntemini kullanın. **ToString** yöntemi geçirilen türün dize gösterimini döndürür. Aşağıdaki tabloda, XML şeması (XSD) belirtimlerine eşlenen bir biçimde dize döndüren .NET türleri listelenmektedir.  
  
|.NET türü|Döndürülen dize türü|  
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
- [Dizeleri .NET veri türlerine dönüştürme](converting-strings-to-dotnet-data-types.md)
