---
title: DOM’dan Düğümleri Kaldırma
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 0a98e0ca-0555-45c1-ab69-0d8d20ca1abd
ms.openlocfilehash: a34b92abc59215c3cb2b94afd88e2e30405b4e9a
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75710316"
---
# <a name="removing-nodes-from-the-dom"></a>DOM’dan Düğümleri Kaldırma
XML Belge Nesne Modeli (DOM) bir düğümü kaldırmak için, belirli bir düğümü kaldırmak <xref:System.Xml.XmlNode.RemoveChild%2A> için yöntemini kullanın. Bir düğümü kaldırdığınızda, yöntemi kaldırılan düğüme ait olan alt ağacı kaldırır; diğer bir deyişle, bir yaprak düğüm değildir.  
  
 DOM 'dan birden fazla düğümü kaldırmak için, geçerli düğümün <xref:System.Xml.XmlNode.RemoveAll%2A> varsa tüm alt öğeleri ve öznitelikleri kaldırmak için yöntemini kullanın.  
  
 İle çalışıyorsanız <xref:System.Xml.XmlNamedNodeMap>, <xref:System.Xml.XmlNamedNodeMap.RemoveNamedItem%2A> yöntemini kullanarak bir düğümü kaldırabilirsiniz.  
  
 Öznitelikleri kaldırmak için bkz. [Dom 'daki bir öğe düğümünden öznitelikleri kaldırma](../../../../docs/standard/data/xml/removing-attributes-from-an-element-node-in-the-dom.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XML Belge Nesne Modeli (DOM)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
