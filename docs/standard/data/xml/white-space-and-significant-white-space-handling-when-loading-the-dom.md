---
title: DOM Yüklerken Boşluk ve Önemli Boşluk İşleme
ms.date: 03/30/2017
ms.assetid: 1b141a0a-50d8-4ebd-83cd-a84449bb22b2
ms.openlocfilehash: 6282b47e8a63143e32df39db02e79e7b44d38275
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95675561"
---
# <a name="white-space-and-significant-white-space-handling-when-loading-the-dom"></a>DOM Yüklerken Boşluk ve Önemli Boşluk İşleme

Belge yüklenirken, boşluk koruma ve belge ağacında **XmlWhitespace** düğümleri oluşturma seçeneğini ayarlayabilirsiniz. Boşluk düğümleri oluşturmak için **PreserveWhitespace** özelliğini true olarak ayarlayın. Özelliği **false** olarak ayarlandıysa, varsayılan değer olan boşluk düğümleri oluşturulmaz. Önemli beyaz alanlar düğümleri her zaman korunur ve **XmlSignificantWhitespace** düğümleri her zaman bu verileri temsil etmek Için, **PreserveWhitespace** bayrağının ayarından bağımsız olarak her zaman bellekte oluşturulur.  
  
 Belge bir okuyucudan yüklenirse, **XmlDocument** sınıfında **PreserveWhitespace** bayrak özelliğinin ayarlanması yalnızca **XmlTextReader** üzerinde **WhitespaceHandling** özelliği **WhitespaceHandling. None** olarak ayarlanmamışsa **XmlWhitespace** düğümlerinin oluşturulmasını etkiler. Bu, okuyucudaki **WhitespaceHandling** özelliğinin değeridir. Bu, **XmlDocument** üzerindeki bu bayrağın ayarından önceliklidir. **XmlSignificantWhitespace** hakkında daha fazla bilgi için bkz <xref:System.Xml.XmlSignificantWhitespace> ..  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XML Belge Nesne Modeli (DOM)](xml-document-object-model-dom.md)
