---
title: XML Belge Nesne Modeli (DOM) Hiyerarşisi
ms.date: 03/30/2017
ms.assetid: 9d187d4f-c76e-4223-a670-cc290783ce47
ms.openlocfilehash: 24ef51a18392fe3034e64bd585d879941fca4b95
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95718364"
---
# <a name="xml-document-object-model-dom-hierarchy"></a>XML Belge Nesne Modeli (DOM) Hiyerarşisi

Aşağıdaki çizim, parantez içinde World Wide Web Konsorsiyumu (W3C) adı olan XML Belge Nesne Modeli (DOM) için sınıf hiyerarşisini ve ilgili olduğu sınıf adını gösterir.  
  
 ![XML Belge Nesne Modeli &#40;DOM&#41; hiyerarşisi](media/dom-class-hierarchy.gif "Dom_class_hierarchy")  
XML Belge Nesne Modeli (DOM) hiyerarşisi  
  
 Aşağıdaki sınıflar **XMLNode**'dan aktarılmaz:  
  
- **XmlImplementation**  
  
- **XmlNamedNodeMap**  
  
- **XmlNodeList**  
  
- **XmlNodeChangedEventArgs**  
  
 **XmlImplementation** sınıfı bir XML belgesi oluşturmak için kullanılır. Daha fazla bilgi için bkz. [XML belgesi oluşturma](xml-document-creation.md).  
  
 **XmlNamedNodeMap** sınıfı, sıralanmamış bir düğüm kümesini işler. Daha fazla bilgi için bkz. [ada veya dizine göre sıralanmamış düğüm alma](unordered-node-retrieval-by-name-or-index.md).  
  
 **XmlNodeList** sınıfı, sıralı bir düğüm listesini işler. Daha fazla bilgi için bkz. [dizine göre sıralı düğüm alma](ordered-node-retrieval-by-index.md).  
  
 **XmlNodeChangedEventArgs** sınıfı, **XmlDocument** üzerinde kayıtlı olay işleyicilerini işler. Daha fazla bilgi için bkz. [XML belgesinde XmlNodeChangedEventArgs kullanılarak olay işleme](event-handling-in-an-xml-document-using-the-xmlnodechangedeventargs.md).  
  
 **XmlLinkedNode** sınıfı **XMLNode**'dan devralır. Amacı **XMLNode**'dan iki yöntemi geçersiz kılmalıdır: **Previouseşdüzey** ve **nexteşdüzey** yöntemleri. Bu geçersiz kılınan Yöntemler daha sonra devralınan ve **Xmlkarakterverisi**, **XmlDeclaration**, **XmlDocumentType**, **XmlElement**, **XmlEntityReference** ve **xmlprocessinginstruction** tarafından, önceki ve sonraki eşdüzey olan sınıflar tarafından kullanılır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XML Belge Nesne Modeli (DOM)](xml-document-object-model-dom.md)
