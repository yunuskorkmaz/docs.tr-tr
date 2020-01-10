---
title: DOM’daki Düğüm İçeriğini Kaldırma
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 615d81a7-f44f-416c-a9ab-bfe03f85e6e4
ms.openlocfilehash: f5086bdea8ff1f0ee5329f347223ebb4a6bd71da
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75710342"
---
# <a name="removing-node-content-in-the-dom"></a>DOM’daki Düğüm İçeriğini Kaldırma
<xref:System.Xml.XmlComment>, <xref:System.Xml.XmlText>, <xref:System.Xml.XmlCDataSection>, <xref:System.Xml.XmlWhitespace>ve <xref:System.Xml.XmlSignificantWhitespace> düğüm türleri olan <xref:System.Xml.XmlCharacterData>'ten devraldığı düğüm türleri için, düğümden bir karakter aralığını kaldıran <xref:System.Xml.XmlCharacterData.DeleteData%2A> yöntemini kullanarak karakterleri kaldırabilirsiniz. İçeriği tamamen kaldırmak istiyorsanız, içeriği içeren düğümü kaldırırsınız. Düğümü korumak istiyorsanız, ancak içerik yanlış ise içeriği değiştirin. Bir düğümün içeriğini değiştirme hakkında daha fazla bilgi için bkz. [BIR XML belgesindeki düğümleri, içeriği ve değerleri değiştirme](../../../../docs/standard/data/xml/modifying-nodes-content-and-values-in-an-xml-document.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XML Belge Nesne Modeli (DOM)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
