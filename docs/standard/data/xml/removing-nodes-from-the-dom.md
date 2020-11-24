---
title: DOM’dan Düğümleri Kaldırma
ms.date: 03/30/2017
ms.assetid: 0a98e0ca-0555-45c1-ab69-0d8d20ca1abd
ms.openlocfilehash: 5b1a6dfb2da4556e0332441a8e56679aee37a091
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95686663"
---
# <a name="removing-nodes-from-the-dom"></a>DOM’dan Düğümleri Kaldırma

XML Belge Nesne Modeli (DOM) bir düğümü kaldırmak için, <xref:System.Xml.XmlNode.RemoveChild%2A> belirli bir düğümü kaldırmak için yöntemini kullanın. Bir düğümü kaldırdığınızda, yöntemi kaldırılan düğüme ait olan alt ağacı kaldırır; diğer bir deyişle, bir yaprak düğüm değildir.  
  
 DOM 'dan birden fazla düğümü kaldırmak için, <xref:System.Xml.XmlNode.RemoveAll%2A> geçerli düğümün varsa tüm alt öğeleri ve öznitelikleri kaldırmak için yöntemini kullanın.  
  
 İle çalışıyorsanız <xref:System.Xml.XmlNamedNodeMap> , yöntemini kullanarak bir düğümü kaldırabilirsiniz <xref:System.Xml.XmlNamedNodeMap.RemoveNamedItem%2A> .  
  
 Öznitelikleri kaldırmak için bkz. [Dom 'daki bir öğe düğümünden öznitelikleri kaldırma](removing-attributes-from-an-element-node-in-the-dom.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XML Belge Nesne Modeli (DOM)](xml-document-object-model-dom.md)
