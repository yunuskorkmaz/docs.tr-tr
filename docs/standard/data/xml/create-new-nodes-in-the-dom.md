---
title: DOM’da Yeni Düğümler Oluşturma
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 6c2b9789-b61a-49f9-b33f-db01a945edf2
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 390ffa1dd9f2e76372b0e4fcbf2916918b64d748
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61934608"
---
# <a name="create-new-nodes-in-the-dom"></a>DOM’da Yeni Düğümler Oluşturma
<xref:System.Xml.XmlDocument> Tüm düğüm türü için bir oluşturma yöntemi vardır. Gerekli olduğunda bir ada sahip yöntem sağlamanız ve içerik veya diğer parametreler (örneğin, bir metin düğümü) içeriğe sahip düğümleri ve düğüm için oluşturulur. Aşağıdaki yöntemlerden bir ada ihtiyacınız olanları ve uygun bir düğüm oluşturmak için doldurulmuş birkaç diğer parametreleri var.  
  
- <xref:System.Xml.XmlDocument.CreateCDataSection%2A>  
  
- <xref:System.Xml.XmlDocument.CreateComment%2A>  
  
- <xref:System.Xml.XmlDocument.CreateDocumentFragment%2A>  
  
- <xref:System.Xml.XmlDocument.CreateDocumentType%2A>  
  
- <xref:System.Xml.XmlDocument.CreateElement%2A>  
  
- <xref:System.Xml.XmlDocument.CreateNode%2A>  
  
- <xref:System.Xml.XmlDocument.CreateProcessingInstruction%2A>  
  
- <xref:System.Xml.XmlDocument.CreateSignificantWhitespace%2A>  
  
- <xref:System.Xml.XmlDocument.CreateTextNode%2A>  
  
- <xref:System.Xml.XmlDocument.CreateWhitespace%2A>  
  
- <xref:System.Xml.XmlDocument.CreateXmlDeclaration%2A>  
  
 Diğer düğüm türleri yalnızca parametreleri için veri sağlama değerinden daha fazla gereksinimleri vardır.  
  
 Öznitelikler hakkında daha fazla bilgi için bkz. [DOM öğeleri için yeni öznitelikler oluşturma](../../../../docs/standard/data/xml/creating-new-attributes-for-elements-in-the-dom.md). Öğe ve öznitelik adı doğrulaması hakkında daha fazla bilgi için bkz: [XML öğesi ve öznitelik adı doğrulaması oluştururken, yeni düğümleri](../../../../docs/standard/data/xml/xml-element-and-attribute-name-verification-when-creating-new-nodes.md). Varlık başvuruları oluşturmak için bkz: [yeni öğe başvuruları oluşturma](../../../../docs/standard/data/xml/creating-new-entity-references.md). Ad alanları genişletme ve varlık başvuruları nasıl etkilediği hakkında daha fazla bilgi için bkz: [Namespace etkiler içeren yeni düğümler öğeler ve öznitelikler için varlık başvurusu genişlemesine](../../../../docs/standard/data/xml/namespace-affect-on-entity-ref-expansion-for-new-nodes.md).  
  
 Yeni düğümleri oluşturulduktan sonra bunları ağacına eklemek kullanılabilir olan çeşitli yöntemler vardır. Tabloda yeni bir düğüm XML belge nesne modeli (DOM) göründüğü açıklaması ile yöntemler listelenmiştir.  
  
|Yöntem|Düğüm yerleştirme|  
|------------|--------------------|  
|<xref:System.Xml.XmlNode.InsertBefore%2A>|Referans düğümün önce eklenmiş. Örneğin, 5 konumda yeni düğümü eklemek için şunu yazın:<br /><br /> `Dim refChild As XmlNode = node.ChildNodes(4) 'The reference is zero-based.node.InsertBefore(newChild, refChild);`<br /><br /> `XmlNode refChild = node.ChildNodes[4]; //The reference is zero-based. node.InsertBefore(newChild, refChild);`<br /><br /> Daha fazla bilgi için <xref:System.Xml.XmlNode.InsertBefore%2A> yöntemi.|  
|<xref:System.Xml.XmlNode.InsertAfter%2A>|Referans düğümün sonra eklenir. Örneğin:<br /><br /> `node.InsertAfter(newChild, refChild)`<br /><br /> `node.InsertAfter(newChild, refChild);`<br /><br /> Daha fazla bilgi için <xref:System.Xml.XmlNode.InsertAfter%2A> yöntemi.|  
|<xref:System.Xml.XmlNode.AppendChild%2A>|Düğüm belirtilen düğümün alt düğümü listesinin sonuna ekler. Olan düğüm eklendiğinde, bir <xref:System.Xml.XmlDocumentFragment>, belge parça öğesinin tüm içeriğini bu düğümün alt listesine taşınır. Daha fazla bilgi için <xref:System.Xml.XmlNode.AppendChild%2A> yöntemi.|  
|<xref:System.Xml.XmlNode.PrependChild%2A>|Düğüm başına verilen düğüm alt düğüm listesi ekler. Olan düğüm eklendiğinde, bir <xref:System.Xml.XmlDocumentFragment>, belge parça öğesinin tüm içeriğini bu düğümün alt listesine taşınır. Daha fazla bilgi için <xref:System.Xml.XmlNode.PrependChild%2A> yöntemi.|  
|<xref:System.Xml.XmlAttributeCollection.Append%2A>|Ekler bir <xref:System.Xml.XmlAttribute> sonuna bir öğe ile ilgili öznitelik koleksiyonu düğümü. Daha fazla bilgi için <xref:System.Xml.XmlAttributeCollection.Append%2A> yöntemi.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XML Belge Nesne Modeli (DOM)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
