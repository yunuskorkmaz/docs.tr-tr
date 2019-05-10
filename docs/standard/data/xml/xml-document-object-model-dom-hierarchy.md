---
title: XML Belge Nesne Modeli (DOM) Hiyerarşisi
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 9d187d4f-c76e-4223-a670-cc290783ce47
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 79078b16f0d56c40a3dcfeabaaed9b5cbb7753a0
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64589836"
---
# <a name="xml-document-object-model-dom-hierarchy"></a>XML Belge Nesne Modeli (DOM) Hiyerarşisi
Sınıf hiyerarşisi için XML belge nesne modeli (DOM), aşağıdaki çizimde, ilgili olduğu sınıf adıyla birlikte parantez içinde World Wide Web Consortium (W3C) adı.  
  
 ![XML belge nesne modeli &#40;DOM&#41; hiyerarşi](../../../../docs/standard/data/xml/media/dom-class-hierarchy.gif "Dom_class_hierarchy")  
XML belge nesne modeli (DOM) hiyerarşisi  
  
 Aşağıdaki sınıflar seçeneğinden devralmamanızı **XmlNode**:  
  
- **XmlImplementation**  
  
- **XmlNamedNodeMap**  
  
- **XmlNodeList**  
  
- **XmlNodeChangedEventArgs**  
  
 **XmlImplementation** sınıfı, bir XML belgesi oluşturmak için kullanılır. Daha fazla bilgi için [XML belgesi oluşturma](../../../../docs/standard/data/xml/xml-document-creation.md).  
  
 **XmlNamedNodeMap** sınıfı sırasız bir dizi düğümü işler. Daha fazla bilgi için [ada veya dizine göre sırasız düğüm alma](../../../../docs/standard/data/xml/unordered-node-retrieval-by-name-or-index.md).  
  
 **XmlNodeList** sınıfı işleme düğümleri sıralı bir listesi. Daha fazla bilgi için [dizine göre sıralı düğüm alma](../../../../docs/standard/data/xml/ordered-node-retrieval-by-index.md).  
  
 **XmlNodeChangedEventArgs** sınıfı işleme kayıtlı olay işleyicilerinin **XmlDocument**. Daha fazla bilgi için [XML belgesinde XmlNodeChangedEventArgs kullanarak olay işleme](../../../../docs/standard/data/xml/event-handling-in-an-xml-document-using-the-xmlnodechangedeventargs.md).  
  
 **XmlLinkedNode** sınıfının devraldığı **XmlNode**. İki yöntemleri geçersiz kılmak için amacı olan **XmlNode**: **PreviousSibling** ve **NextSibling** yöntemleri. Bu geçersiz kılınan yöntemler ardından devralınan ve tarafından kullanılan **XmlCharacterData**, **XmlDeclaration**, **XmlDocumentType**, **XmlElement**, **XmlEntityReference**, ve **XmlProcessingInstruction**, önceki ve sonraki eşdüzey öğesi olan sınıfları şunlardır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XML Belge Nesne Modeli (DOM)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
