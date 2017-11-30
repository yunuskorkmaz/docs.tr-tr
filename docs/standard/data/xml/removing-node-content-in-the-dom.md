---
title: "DOM düğümü içeriği kaldırma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 615d81a7-f44f-416c-a9ab-bfe03f85e6e4
caps.latest.revision: "3"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 76be90829a414b091d3b311b96bf9bab9a2b56ed
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="removing-node-content-in-the-dom"></a>DOM düğümü içeriği kaldırma
Devralınan düğüm türleri için <xref:System.Xml.XmlCharacterData>, hangi <xref:System.Xml.XmlComment>, <xref:System.Xml.XmlText>, <xref:System.Xml.XmlCDataSection>, <xref:System.Xml.XmlWhitespace>, ve <xref:System.Xml.XmlSignificantWhitespace> düğüm türlerini kullanarak karakterlerini kaldırabilirsiniz <xref:System.Xml.XmlCharacterData.DeleteData%2A> aralığını kaldırır yöntemi karakter düğümünden. İçerik tamamen kaldırmak istiyorsanız, içeriğin bulunduğu düğümü kaldırın. Düğüm tutmak istediğiniz, ancak içeriğin yanlış olduğundan, içeriği değiştirin. Bir düğümün içeriğini değiştirme hakkında daha fazla bilgi için bkz: [değiştirme düğümleri, içerik ve bir XML belgesi değerleri](../../../../docs/standard/data/xml/modifying-nodes-content-and-values-in-an-xml-document.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [XML belge nesne modeli (DOM)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
