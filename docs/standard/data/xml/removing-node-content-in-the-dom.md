---
title: DOM düğüm içeriğini kaldırma
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 615d81a7-f44f-416c-a9ab-bfe03f85e6e4
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 737766586ee920a87c25dd42896bdfb14ae69d98
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43877852"
---
# <a name="removing-node-content-in-the-dom"></a>DOM düğüm içeriğini kaldırma
Devralınan düğüm türleri için <xref:System.Xml.XmlCharacterData>, hangi <xref:System.Xml.XmlComment>, <xref:System.Xml.XmlText>, <xref:System.Xml.XmlCDataSection>, <xref:System.Xml.XmlWhitespace>, ve <xref:System.Xml.XmlSignificantWhitespace> düğüm türlerini kullanarak karakterler kaldırabilirsiniz <xref:System.Xml.XmlCharacterData.DeleteData%2A> çeşitli kaldıran yöntemi düğümünden karakter. İçeriği tamamen kaldırmak istiyorsanız, içeriğin bulunduğu düğümü kaldırın. Ardından düğümü tutmak istediğiniz, ancak içerik yanlış, içeriği değiştirin. Bir düğüm içeriğini değiştirme hakkında daha fazla bilgi için bkz: [değiştirme düğümleri, içeriği ve değerleri bir XML belgesi](../../../../docs/standard/data/xml/modifying-nodes-content-and-values-in-an-xml-document.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XML Belge Nesne Modeli (DOM)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
