---
title: DOM düğümleri kaldırma
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 0a98e0ca-0555-45c1-ab69-0d8d20ca1abd
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ec786564e6246f10e10d600f4822442884323557
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="removing-nodes-from-the-dom"></a>DOM düğümleri kaldırma
XML belge nesne modeli (DOM) gelen bir düğümünü kaldırmak için kullanın <xref:System.Xml.XmlNode.RemoveChild%2A> belirli bir düğümü çıkarmak için yöntem. Yöntemi, bir düğümü kaldırdığınızda, kaldırılmakta olan düğüme ait alt ağacı kaldırır; diğer bir deyişle, bir yaprak düğüm değilse.  
  
 DOM birden çok düğüm kaldırmak için kullanın <xref:System.Xml.XmlNode.RemoveAll%2A> geçerli düğümünün varsa, tüm alt öğeleri ve öznitelikleri kaldırmak için yöntem.  
  
 İle çalışıyorsanız bir <xref:System.Xml.XmlNamedNodeMap>, kullanarak bir düğümü kaldırma <xref:System.Xml.XmlNamedNodeMap.RemoveNamedItem%2A> yöntemi.  
  
 Öznitelikleri kaldırmak için bkz: [DOM öğesi düğümünde kaldırma özniteliklerden](../../../../docs/standard/data/xml/removing-attributes-from-an-element-node-in-the-dom.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [XML Belge Nesne Modeli (DOM)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
