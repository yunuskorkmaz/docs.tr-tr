---
title: DOM'dan düğümleri kaldırma
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 0a98e0ca-0555-45c1-ab69-0d8d20ca1abd
author: mairaw
ms.author: mairaw
ms.openlocfilehash: be592466627e6ee7b23c608e0defe786548907ad
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/16/2018
ms.locfileid: "45676077"
---
# <a name="removing-nodes-from-the-dom"></a>DOM'dan düğümleri kaldırma
XML belge nesne modeli (DOM) öğesinden bir düğümü kaldırmak için <xref:System.Xml.XmlNode.RemoveChild%2A> belirli bir düğümü kaldırmak için yöntemi. Yöntemi, bir düğümü kaldırdığınızda, kaldırılmakta olan düğüme ait alt ağacı kaldırır; diğer bir deyişle, bir yaprak düğüm değilse.  
  
 DOM'dan birden fazla düğüm kaldırmak için <xref:System.Xml.XmlNode.RemoveAll%2A> geçerli düğümünün (varsa), tüm alt öğeleri ve öznitelikleri kaldırmak için yöntemi.  
  
 İle çalışıyorsanız bir <xref:System.Xml.XmlNamedNodeMap>, kullanarak bir düğümü kaldırmak <xref:System.Xml.XmlNamedNodeMap.RemoveNamedItem%2A> yöntemi.  
  
 Öznitelikleri kaldırmak için bkz: [DOM'da bir öğe düğümünden öznitelikleri kaldırma](../../../../docs/standard/data/xml/removing-attributes-from-an-element-node-in-the-dom.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XML Belge Nesne Modeli (DOM)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
