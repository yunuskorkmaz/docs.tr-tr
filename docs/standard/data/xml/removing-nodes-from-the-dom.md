---
title: "DOM düğümleri kaldırma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0a98e0ca-0555-45c1-ab69-0d8d20ca1abd
caps.latest.revision: "3"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 0885d53e737153448fabfd394d49bfdc793e0599
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="removing-nodes-from-the-dom"></a>DOM düğümleri kaldırma
XML belge nesne modeli (DOM) gelen bir düğümünü kaldırmak için kullanın <xref:System.Xml.XmlNode.RemoveChild%2A> belirli bir düğümü çıkarmak için yöntem. Yöntemi, bir düğümü kaldırdığınızda, kaldırılmakta olan düğüme ait alt ağacı kaldırır; diğer bir deyişle, bir yaprak düğüm değilse.  
  
 DOM birden çok düğüm kaldırmak için kullanın <xref:System.Xml.XmlNode.RemoveAll%2A> geçerli düğümünün varsa, tüm alt öğeleri ve öznitelikleri kaldırmak için yöntem.  
  
 İle çalışıyorsanız bir <xref:System.Xml.XmlNamedNodeMap>, kullanarak bir düğümü kaldırma <xref:System.Xml.XmlNamedNodeMap.RemoveNamedItem%2A> yöntemi.  
  
 Öznitelikleri kaldırmak için bkz: [DOM öğesi düğümünde kaldırma özniteliklerden](../../../../docs/standard/data/xml/removing-attributes-from-an-element-node-in-the-dom.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [XML belge nesne modeli (DOM)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
