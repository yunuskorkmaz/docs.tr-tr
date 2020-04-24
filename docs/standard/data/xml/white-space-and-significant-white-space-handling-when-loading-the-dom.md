---
title: DOM Yüklerken Boşluk ve Önemli Boşluk İşleme
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 1b141a0a-50d8-4ebd-83cd-a84449bb22b2
ms.openlocfilehash: 834644a07d790401a1131d6d901f144ef90dc495
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75710030"
---
# <a name="white-space-and-significant-white-space-handling-when-loading-the-dom"></a>DOM Yüklerken Boşluk ve Önemli Boşluk İşleme
Belge yüklenirken, boşluk koruma ve belge ağacında **XmlWhitespace** düğümleri oluşturma seçeneğini ayarlayabilirsiniz. Boşluk düğümleri oluşturmak için **PreserveWhitespace** özelliğini true olarak ayarlayın. Özelliği **false**olarak ayarlandıysa, varsayılan değer olan boşluk düğümleri oluşturulmaz. Önemli beyaz alanlar düğümleri her zaman korunur ve **XmlSignificantWhitespace** düğümleri her zaman bu verileri temsil etmek Için, **PreserveWhitespace** bayrağının ayarından bağımsız olarak her zaman bellekte oluşturulur.  
  
 Belge bir okuyucudan yüklenirse, **XmlDocument** sınıfında **PreserveWhitespace** bayrak özelliğinin ayarlanması yalnızca **XmlTextReader** üzerinde **WhitespaceHandling** özelliği **WhitespaceHandling. None**olarak ayarlanmamışsa **XmlWhitespace** düğümlerinin oluşturulmasını etkiler. Bu, okuyucudaki **WhitespaceHandling** özelliğinin değeridir. Bu, **XmlDocument**üzerindeki bu bayrağın ayarından önceliklidir. **XmlSignificantWhitespace**hakkında daha fazla bilgi için bkz <xref:System.Xml.XmlSignificantWhitespace>..  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XML Belge Nesne Modeli (DOM)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
