---
title: DOM Yüklerken Boşluk ve Önemli Boşluk İşleme
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 1b141a0a-50d8-4ebd-83cd-a84449bb22b2
ms.openlocfilehash: 520d965737b82fda082aa44029f2a4042d948deb
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84281784"
---
# <a name="white-space-and-significant-white-space-handling-when-loading-the-dom"></a>DOM Yüklerken Boşluk ve Önemli Boşluk İşleme
Belge yüklenirken, boşluk koruma ve belge ağacında **XmlWhitespace** düğümleri oluşturma seçeneğini ayarlayabilirsiniz. Boşluk düğümleri oluşturmak için **PreserveWhitespace** özelliğini true olarak ayarlayın. Özelliği **false**olarak ayarlandıysa, varsayılan değer olan boşluk düğümleri oluşturulmaz. Önemli beyaz alanlar düğümleri her zaman korunur ve **XmlSignificantWhitespace** düğümleri her zaman bu verileri temsil etmek Için, **PreserveWhitespace** bayrağının ayarından bağımsız olarak her zaman bellekte oluşturulur.  
  
 Belge bir okuyucudan yüklenirse, **XmlDocument** sınıfında **PreserveWhitespace** bayrak özelliğinin ayarlanması yalnızca **XmlTextReader** üzerinde **WhitespaceHandling** özelliği **WhitespaceHandling. None**olarak ayarlanmamışsa **XmlWhitespace** düğümlerinin oluşturulmasını etkiler. Bu, okuyucudaki **WhitespaceHandling** özelliğinin değeridir. Bu, **XmlDocument**üzerindeki bu bayrağın ayarından önceliklidir. **XmlSignificantWhitespace**hakkında daha fazla bilgi için bkz <xref:System.Xml.XmlSignificantWhitespace> ..  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XML Belge Nesne Modeli (DOM)](xml-document-object-model-dom.md)
