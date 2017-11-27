---
title: "Çok XmlDocument giriş"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 97115892-410a-4657-ab47-1e14dfba73f8
caps.latest.revision: "3"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 554faffb676337f8846eb6ba24152d77793b8fe0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="xmldocument-input-to-xsltransform"></a>Çok XmlDocument giriş
<xref:System.Xml.XmlDocument> Sınıfı bir XML belgesi için düzenleme özellikleri sağlar. XML düzenlenmesine veya için gönderilmeden önce değiştirilen gerekip gerekmediğini <xref:System.Xml.Xsl.XslTransform.Transform%2A> yöntemi, XML öğesine yük bir <xref:System.Xml.XmlDocument>, düzenlemek ve içinde göndermeden <xref:System.Xml.Xsl.XslTransform>.  
  
> [!NOTE]
>  <xref:System.Xml.Xsl.XslTransform> Sınıftır'te eski [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)]. Genişletilebilir Stil sayfası dili kullanarak Dönüşümleri (XSLT) dönüştürmeleri için gerçekleştirebilirsiniz <xref:System.Xml.Xsl.XslCompiledTransform> sınıfı. Bkz: [XslCompiledTransform sınıfını kullanarak](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) ve [çok sınıfı geçirme](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md) daha fazla bilgi için.  
  
 <xref:System.Xml.XmlDocument> Uygulayan <xref:System.Xml.XPath.IXPathNavigable> arabirim için belge geçirilebilmesi <xref:System.Xml.Xsl.XslTransform.Transform%2A> düzenleme sonrasında yöntemi.  
  
 Düzenleme yeteneğini nedeniyle <xref:System.Xml.XmlDocument>kullanarak <xref:System.Xml.XmlDocument> sınıfı bir dönüşüm girişine kullanmaktan daha yavaş olduğu gibi bir <xref:System.Xml.XPath.XPathDocument> Dönüşümleri (XSLT) dönüştürmeleri için Genişletilebilir Stil sayfası dilde olarak <xref:System.Xml.XPath.XPathDocument> olduğu İç depolaması nedeniyle XML Path dili (XPath) sorguları için en iyi duruma getirilmiş.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte gösterildiği nasıl kod bir <xref:System.Xml.XmlDocument> için sağlanan <xref:System.Xml.Xsl.XslTransform>, gönderilen çıkış bir <xref:System.Xml.XmlReader>.  
  
```vb  
Dim doc as XmlDocument = new XmlDocument()  
doc.Load("books.xml")  
Dim trans As XslTransform = new XslTransform()  
trans.Load("book.xsl")  
Dim rdr As XmlReader = trans.Transform(doc, Nothing, Nothing)  
while (rdr.Read())  
end while  
```  
  
```csharp  
XmlDocument doc = new XmlDocument();  
doc.Load("books.xml");  
XslTransform trans = new XslTransform();  
trans.Load("book.xsl");  
XmlReader rdr = trans.Transform(doc, null, null);  
while (rdr.Read()) {}  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Xml.XmlDocument>  
 [Çok sınıfı ile XSLT dönüştürmeler](../../../../docs/standard/data/xml/xslt-transformations-with-the-xsltransform-class.md)  
 [XSLT işlemci çok sınıfı uygular](../../../../docs/standard/data/xml/xsltransform-class-implements-the-xslt-processor.md)  
 [Dönüşümleri XPathNavigator](../../../../docs/standard/data/xml/xpathnavigator-in-transformations.md)  
 [Dönüşümleri XPathNodeIterator](../../../../docs/standard/data/xml/xpathnodeiterator-in-transformations.md)  
 [Çok XPathDocument giriş](../../../../docs/standard/data/xml/xpathdocument-input-to-xsltransform.md)  
 [Çok XmlDataDocument giriş](../../../../docs/standard/data/xml/xmldatadocument-input-to-xsltransform.md)
