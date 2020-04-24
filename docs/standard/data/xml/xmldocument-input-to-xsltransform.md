---
title: XslTransform’a XmlDocument Girişi
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 97115892-410a-4657-ab47-1e14dfba73f8
ms.openlocfilehash: c7819c3cb6b1430dcdb8a78c43f7138f64e691a8
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709848"
---
# <a name="xmldocument-input-to-xsltransform"></a>XslTransform’a XmlDocument Girişi
Sınıfı <xref:System.Xml.XmlDocument> , bir XML belgesi için düzenlenebilir özellikleri sağlar. XML 'nin <xref:System.Xml.Xsl.XslTransform.Transform%2A> yönteme gönderilmeden önce düzenlenmesi veya değiştirilmesi GEREKIYORSA, XML 'yi bir <xref:System.Xml.XmlDocument>öğesine yükleyin, düzenleyin ve içine gönderin. <xref:System.Xml.Xsl.XslTransform>  
  
> [!NOTE]
> <xref:System.Xml.Xsl.XslTransform> Sınıf .NET Framework 2,0 ' de kullanılmıyor. <xref:System.Xml.Xsl.XslCompiledTransform> Sınıfını kullanarak dönüşümler Için Genişletilebilir Stil sayfası DILI (XSLT) dönüşümleri gerçekleştirebilirsiniz. Daha fazla bilgi için, bkz. [XslCompiledTransform sınıfını kullanma](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) ve [XslTransform sınıfından geçiş](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md) .  
  
 , <xref:System.Xml.XmlDocument> <xref:System.Xml.XPath.IXPathNavigable> Arabirimini uygular, bu nedenle belge Düzenlemeden sonra <xref:System.Xml.Xsl.XslTransform.Transform%2A> yönteme geçirilebilir.  
  
 Öğesinin <xref:System.Xml.XmlDocument>düzenlenme özelliği nedeniyle, <xref:System.Xml.XmlDocument> sınıfının bir dönüşüme giriş olarak kullanılması, Iç depolama nedeniyle XML yol dili (XPath) <xref:System.Xml.XPath.XPathDocument> sorguları için optimize edilmiş olduğundan, <xref:System.Xml.XPath.XPathDocument> dönüşümler için Genişletilebilir Stil sayfası dili (XSLT) dönüştürmeleri için kullanmaktan daha yavaştır.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği, <xref:System.Xml.XmlDocument> <xref:System.Xml.Xsl.XslTransform>' a gönderilen çıkış ile öğesine nasıl sağlanabilecek gösterilmektedir. <xref:System.Xml.XmlReader>  
  
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
