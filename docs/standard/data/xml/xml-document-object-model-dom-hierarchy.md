---
title: "XML belge nesne modeli (DOM) hiyerarşisi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9d187d4f-c76e-4223-a670-cc290783ce47
caps.latest.revision: "3"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 4d2ffaa994ce3c9b02ed0937967845be1b803f6d
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="xml-document-object-model-dom-hierarchy"></a>XML belge nesne modeli (DOM) hiyerarşisi
Sınıf hiyerarşisi için XML belge nesne modeli (DOM), aşağıdaki çizimde gösterilmektedir World Wide Web Konsorsiyumu (W3C) ile ilgili olduğu sınıf adı ile birlikte parantez içinde adı.  
  
 ![XML belge nesnesi modeli &#40; DOM &#41; Hiyerarşi](../../../../docs/standard/data/xml/media/dom-class-hierarchy.gif "Dom_class_hierarchy")  
XML belge nesne modeli (DOM) hiyerarşisi  
  
 Aşağıdaki sınıflar devralınmalıdır değil **XmlNode**:  
  
-   **XmlImplementation**  
  
-   **XmlNamedNodeMap**  
  
-   **XmlNodeList**  
  
-   **XmlNodeChangedEventArgs**  
  
 **XmlImplementation** sınıfı, bir XML belgesi oluşturmak için kullanılır. Daha fazla bilgi için bkz: [XML belgesi oluşturma](../../../../docs/standard/data/xml/xml-document-creation.md).  
  
 **XmlNamedNodeMap** sınıfı düğümler sırasız bir kümesini işler. Daha fazla bilgi için bkz: [adı veya dizin tarafından sırasız düğümü alma](../../../../docs/standard/data/xml/unordered-node-retrieval-by-name-or-index.md).  
  
 **XmlNodeList** sınıfı işler düğümleri sıralı bir listesi. Daha fazla bilgi için bkz: [dizine göre sıralı düğüm alma](../../../../docs/standard/data/xml/ordered-node-retrieval-by-index.md).  
  
 **XmlNodeChangedEventArgs** sınıfı işler kayıtlı olay işleyicileri **XmlDocument**. Daha fazla bilgi için bkz: [olay işleme XmlNodeChangedEventArgs kullanarak bir XML belgesi](../../../../docs/standard/data/xml/event-handling-in-an-xml-document-using-the-xmlnodechangedeventargs.md).  
  
 **XmlLinkedNode** sınıfının devraldığı **XmlNode**. İki yöntemleri geçersiz kılmak için amacı olan **XmlNode**: **PreviousSibling** ve **NextSibling** yöntemleri. Geçersiz kılınan bu yöntemleri sonra devralınan ve tarafından kullanılan **XmlCharacterData**, **XmlDeclaration**, **XmlDocumentType**, **XmlElement**, **XmlEntityReference**, ve **XmlProcessingInstruction**, önceki ve sonraki eşdüzey öğesi sınıfları olduğu.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [XML Belge Nesne Modeli (DOM)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
