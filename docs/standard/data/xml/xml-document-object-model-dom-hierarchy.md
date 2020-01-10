---
title: XML Belge Nesne Modeli (DOM) Hiyerarşisi
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 9d187d4f-c76e-4223-a670-cc290783ce47
ms.openlocfilehash: 1193d7631816fe9fbf7aa1984d79ef8e61d5da80
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709978"
---
# <a name="xml-document-object-model-dom-hierarchy"></a>XML Belge Nesne Modeli (DOM) Hiyerarşisi
Aşağıdaki çizim, parantez içinde World Wide Web Konsorsiyumu (W3C) adı olan XML Belge Nesne Modeli (DOM) için sınıf hiyerarşisini ve ilgili olduğu sınıf adını gösterir.  
  
 ![XML Belge Nesne Modeli &#40;Dom&#41; hiyerarşisi](../../../../docs/standard/data/xml/media/dom-class-hierarchy.gif "Dom_class_hierarchy")  
XML Belge Nesne Modeli (DOM) hiyerarşisi  
  
 Aşağıdaki sınıflar **XMLNode**'dan aktarılmaz:  
  
- **XmlImplementation**  
  
- **XmlNamedNodeMap**  
  
- **XmlNodeList**  
  
- **XmlNodeChangedEventArgs**  
  
 **XmlImplementation** sınıfı bir XML belgesi oluşturmak için kullanılır. Daha fazla bilgi için bkz. [XML belgesi oluşturma](../../../../docs/standard/data/xml/xml-document-creation.md).  
  
 **XmlNamedNodeMap** sınıfı, sıralanmamış bir düğüm kümesini işler. Daha fazla bilgi için bkz. [ada veya dizine göre sıralanmamış düğüm alma](../../../../docs/standard/data/xml/unordered-node-retrieval-by-name-or-index.md).  
  
 **XmlNodeList** sınıfı, sıralı bir düğüm listesini işler. Daha fazla bilgi için bkz. [dizine göre sıralı düğüm alma](../../../../docs/standard/data/xml/ordered-node-retrieval-by-index.md).  
  
 **XmlNodeChangedEventArgs** sınıfı, **XmlDocument**üzerinde kayıtlı olay işleyicilerini işler. Daha fazla bilgi için bkz. [XML belgesinde XmlNodeChangedEventArgs kullanılarak olay işleme](../../../../docs/standard/data/xml/event-handling-in-an-xml-document-using-the-xmlnodechangedeventargs.md).  
  
 **XmlLinkedNode** sınıfı **XMLNode**'dan devralır. Amacı **XMLNode**'dan iki yöntemi geçersiz kılmalıdır: **Previouseşdüzey** ve **nexteşdüzey** yöntemleri. Bu geçersiz kılınan Yöntemler daha sonra devralınan ve **Xmlkarakterverisi**, **XmlDeclaration**, **XmlDocumentType**, **XmlElement**, **XmlEntityReference**ve **xmlprocessinginstruction**tarafından, önceki ve sonraki eşdüzey olan sınıflar tarafından kullanılır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XML Belge Nesne Modeli (DOM)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
