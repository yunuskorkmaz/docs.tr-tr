---
title: Yeni düğümler DOM'da oluşturma
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 6c2b9789-b61a-49f9-b33f-db01a945edf2
author: mairaw
ms.author: mairaw
ms.openlocfilehash: bbc8d6c1055afc1a0799522f341551d04bab4ace
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33569310"
---
# <a name="create-new-nodes-in-the-dom"></a>Yeni düğümler DOM'da oluşturma
<xref:System.Xml.XmlDocument> Tüm düğüm türü için create yöntemi vardır. Gerekli olduğunda bir adla yöntemi sağlayın ve içerik veya içeriğe (örneğin, bir metin düğümü) sahip düğümleri ve düğüm için başka parametre oluşturulur. Aşağıdaki yöntemler, bir ada ihtiyacınız olanları ve uygun bir düğüm oluşturmak için doldurulmuş birkaç diğer parametreleri yöneliktir.  
  
-   <xref:System.Xml.XmlDocument.CreateCDataSection%2A>  
  
-   <xref:System.Xml.XmlDocument.CreateComment%2A>  
  
-   <xref:System.Xml.XmlDocument.CreateDocumentFragment%2A>  
  
-   <xref:System.Xml.XmlDocument.CreateDocumentType%2A>  
  
-   <xref:System.Xml.XmlDocument.CreateElement%2A>  
  
-   <xref:System.Xml.XmlDocument.CreateNode%2A>  
  
-   <xref:System.Xml.XmlDocument.CreateProcessingInstruction%2A>  
  
-   <xref:System.Xml.XmlDocument.CreateSignificantWhitespace%2A>  
  
-   <xref:System.Xml.XmlDocument.CreateTextNode%2A>  
  
-   <xref:System.Xml.XmlDocument.CreateWhitespace%2A>  
  
-   <xref:System.Xml.XmlDocument.CreateXmlDeclaration%2A>  
  
 Diğer düğüm türleri yalnızca veri parametrelerine sağlamaktan daha fazla gereksinimlere sahiptir.  
  
 Öznitelikleri hakkında daha fazla bilgi için bkz: [DOM öğeleri için yeni öznitelikler oluşturma](../../../../docs/standard/data/xml/creating-new-attributes-for-elements-in-the-dom.md). Öğe ve öznitelik adı doğrulama hakkında daha fazla bilgi için bkz: [XML öğesi ve öznitelik adı oluştururken doğrulama yeni düğümler](../../../../docs/standard/data/xml/xml-element-and-attribute-name-verification-when-creating-new-nodes.md). Varlık başvuruları oluşturmak için bkz: [oluşturma yeni varlık başvuruları](../../../../docs/standard/data/xml/creating-new-entity-references.md). Ad alanları varlık başvuruları genişletme etkilemesi hakkında daha fazla bilgi için bkz: [yeni düğümler içeren öğeleri ve öznitelikleri için varlık başvurusu genişletme Namespace güncelleştirmedikçe](../../../../docs/standard/data/xml/namespace-affect-on-entity-ref-expansion-for-new-nodes.md).  
  
 Yeni düğümler oluşturulduktan sonra ağacına eklemek kullanılabilecek çeşitli yöntemler vardır. Tablo, yeni düğümü XML belge nesne modeli (DOM) göründüğü açıklaması yöntemleriyle listeler.  
  
|Yöntem|Düğüm yerleştirme|  
|------------|--------------------|  
|<xref:System.Xml.XmlNode.InsertBefore%2A>|Referans düğümün önce eklenir. Örneğin, 5. konumda yeni düğüm eklemek için şunu yazın:<br /><br /> `Dim refChild As XmlNode = node.ChildNodes(4) 'The reference is zero-based.node.InsertBefore(newChild, refChild);`<br /><br /> `XmlNode refChild = node.ChildNodes[4]; //The reference is zero-based. node.InsertBefore(newChild, refChild);`<br /><br /> Daha fazla bilgi için bkz: <xref:System.Xml.XmlNode.InsertBefore%2A> yöntemi.|  
|<xref:System.Xml.XmlNode.InsertAfter%2A>|Referans düğümün sonra eklenir. Örneğin:<br /><br /> `node.InsertAfter(newChild, refChild)`<br /><br /> `node.InsertAfter(newChild, refChild);`<br /><br /> Daha fazla bilgi için bkz: <xref:System.Xml.XmlNode.InsertAfter%2A> yöntemi.|  
|<xref:System.Xml.XmlNode.AppendChild%2A>|Düğümün alt düğümleri verilen düğüm için listesinin sonuna ekler. Düğümü olan eklenir, bir <xref:System.Xml.XmlDocumentFragment>, belge parça tüm içeriğini bu düğümün alt listesine taşınır. Daha fazla bilgi için bkz: <xref:System.Xml.XmlNode.AppendChild%2A> yöntemi.|  
|<xref:System.Xml.XmlNode.PrependChild%2A>|Düğüm belirtilen düğümün alt öğelerinin listesi başlangıcına ekler. Düğümü olan eklenir, bir <xref:System.Xml.XmlDocumentFragment>, belge parça tüm içeriğini bu düğümün alt listesine taşınır. Daha fazla bilgi için bkz: <xref:System.Xml.XmlNode.PrependChild%2A> yöntemi.|  
|<xref:System.Xml.XmlAttributeCollection.Append%2A>|Ekler bir <xref:System.Xml.XmlAttribute> sonuna kadar bir öğesiyle ilişkili öznitelik koleksiyonu düğümü. Daha fazla bilgi için bkz: <xref:System.Xml.XmlAttributeCollection.Append%2A> yöntemi.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [XML Belge Nesne Modeli (DOM)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
