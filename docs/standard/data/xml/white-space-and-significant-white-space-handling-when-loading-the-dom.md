---
description: 'Daha fazla bilgi edinin: DOM yüklenirken boşluk ve önemli boşluk Işleme'
title: DOM Yüklerken Boşluk ve Önemli Boşluk İşleme
ms.date: 03/30/2017
ms.assetid: 1b141a0a-50d8-4ebd-83cd-a84449bb22b2
ms.openlocfilehash: b863f5921bf3e9e3da9489d02a7bd09d25f38c7d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99782825"
---
# <a name="white-space-and-significant-white-space-handling-when-loading-the-dom"></a>DOM Yüklerken Boşluk ve Önemli Boşluk İşleme

Belge yüklenirken, boşluk koruma ve belge ağacında **XmlWhitespace** düğümleri oluşturma seçeneğini ayarlayabilirsiniz. Boşluk düğümleri oluşturmak için **PreserveWhitespace** özelliğini true olarak ayarlayın. Özelliği **false** olarak ayarlandıysa, varsayılan değer olan boşluk düğümleri oluşturulmaz. Önemli beyaz alanlar düğümleri her zaman korunur ve **XmlSignificantWhitespace** düğümleri her zaman bu verileri temsil etmek Için, **PreserveWhitespace** bayrağının ayarından bağımsız olarak her zaman bellekte oluşturulur.  
  
 Belge bir okuyucudan yüklenirse, **XmlDocument** sınıfında **PreserveWhitespace** bayrak özelliğinin ayarlanması yalnızca **XmlTextReader** üzerinde **WhitespaceHandling** özelliği **WhitespaceHandling. None** olarak ayarlanmamışsa **XmlWhitespace** düğümlerinin oluşturulmasını etkiler. Bu, okuyucudaki **WhitespaceHandling** özelliğinin değeridir. Bu, **XmlDocument** üzerindeki bu bayrağın ayarından önceliklidir. **XmlSignificantWhitespace** hakkında daha fazla bilgi için bkz <xref:System.Xml.XmlSignificantWhitespace> ..  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XML Belge Nesne Modeli (DOM)](xml-document-object-model-dom.md)
