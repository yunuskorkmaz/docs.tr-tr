---
title: XslTransform’a XmlDocument Girişi
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 97115892-410a-4657-ab47-1e14dfba73f8
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 60b9b66ea9b1c74dc34e2e99dcf651f9dac1725e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69915965"
---
# <a name="xmldocument-input-to-xsltransform"></a>XslTransform’a XmlDocument Girişi
Sınıfı <xref:System.Xml.XmlDocument> , bir XML belgesi için düzenlenebilir özellikleri sağlar. XML 'nin <xref:System.Xml.Xsl.XslTransform.Transform%2A> yönteme gönderilmeden önce düzenlenmesi veya değiştirilmesi gerekiyorsa, XML 'yi bir <xref:System.Xml.XmlDocument>öğesine yükleyin, düzenleyin ve içine <xref:System.Xml.Xsl.XslTransform>gönderin.  
  
> [!NOTE]
> <xref:System.Xml.Xsl.XslTransform> Sınıf .NET Framework 2,0 ' de kullanılmıyor. <xref:System.Xml.Xsl.XslCompiledTransform> Sınıfını kullanarak dönüşümler için Genişletilebilir Stil sayfası dili (XSLT) dönüşümleri gerçekleştirebilirsiniz. Daha fazla bilgi için, bkz. [XslCompiledTransform sınıfını kullanma](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) ve [XslTransform sınıfından geçiş](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md) .  
  
 , <xref:System.Xml.XmlDocument> Arabirimini<xref:System.Xml.XPath.IXPathNavigable> uygular, bu nedenle belge Düzenlemeden sonra <xref:System.Xml.Xsl.XslTransform.Transform%2A> yönteme geçirilebilir.  
  
 Öğesinin <xref:System.Xml.XmlDocument>düzenlenme özelliği nedeniyle, <xref:System.Xml.XmlDocument> sınıfının bir dönüşüme giriş olarak kullanılması, <xref:System.Xml.XPath.XPathDocument> olduğu gibi dönüşümler (XSLT) dönüştürmeleri için Genişletilebilir <xref:System.Xml.XPath.XPathDocument> stil sayfası dili için kullanmaktan daha yavaştır. iç depolama nedeniyle XML yol dili (XPath) sorguları için iyileştirildi.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği, <xref:System.Xml.XmlDocument> <xref:System.Xml.Xsl.XslTransform>' a gönderilen <xref:System.Xml.XmlReader>çıkış ile öğesine nasıl sağlanabilecek gösterilmektedir.  
  
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
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Xml.XmlDocument>
- [XslTransform Sınıfı ile XSLT Dönüşümleri](../../../../docs/standard/data/xml/xslt-transformations-with-the-xsltransform-class.md)
- [XslTransform Sınıfı XSLT İşlemcisini Uygular](../../../../docs/standard/data/xml/xsltransform-class-implements-the-xslt-processor.md)
- [Dönüşümlerde XPathNavigator](../../../../docs/standard/data/xml/xpathnavigator-in-transformations.md)
- [Dönüşümlerde XPathNodeIterator](../../../../docs/standard/data/xml/xpathnodeiterator-in-transformations.md)
- [XslTransform’a XPathDocument Girişi](../../../../docs/standard/data/xml/xpathdocument-input-to-xsltransform.md)
- [XslTransform’a XmlDataDocument Girişi](../../../../docs/standard/data/xml/xmldatadocument-input-to-xsltransform.md)
