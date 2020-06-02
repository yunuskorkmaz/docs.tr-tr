---
title: XslTransform’a XmlDocument Girişi
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 97115892-410a-4657-ab47-1e14dfba73f8
ms.openlocfilehash: e990c8ca3bb2a7145157fcedd06da4ea769c6ad3
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84290259"
---
# <a name="xmldocument-input-to-xsltransform"></a>XslTransform’a XmlDocument Girişi
<xref:System.Xml.XmlDocument>Sınıfı, BIR XML belgesi için düzenlenebilir özellikleri sağlar. XML 'nin yönteme gönderilmeden önce düzenlenmesi veya değiştirilmesi gerekiyorsa, XML 'yi bir öğesine <xref:System.Xml.Xsl.XslTransform.Transform%2A> yükleyin <xref:System.Xml.XmlDocument> , düzenleyin ve içine gönderin <xref:System.Xml.Xsl.XslTransform> .  
  
> [!NOTE]
> <xref:System.Xml.Xsl.XslTransform>Sınıf .NET Framework 2,0 ' de kullanılmıyor. Sınıfını kullanarak dönüşümler için Genişletilebilir Stil sayfası dili (XSLT) dönüşümleri gerçekleştirebilirsiniz <xref:System.Xml.Xsl.XslCompiledTransform> . Daha fazla bilgi için, bkz. [XslCompiledTransform sınıfını kullanma](using-the-xslcompiledtransform-class.md) ve [XslTransform sınıfından geçiş](migrating-from-the-xsltransform-class.md) .  
  
 , <xref:System.Xml.XmlDocument> Arabirimini uygular <xref:System.Xml.XPath.IXPathNavigable> , bu nedenle belge <xref:System.Xml.Xsl.XslTransform.Transform%2A> Düzenlemeden sonra yönteme geçirilebilir.  
  
 Öğesinin düzenlenme özelliği nedeniyle, <xref:System.Xml.XmlDocument> <xref:System.Xml.XmlDocument> sınıfının bir dönüşüme giriş olarak kullanılması, <xref:System.Xml.XPath.XPathDocument> <xref:System.Xml.XPath.XPathDocument> Iç depolama nedeniyle XML yol dili (XPath) sorguları için optimize edilmiş olduğundan, dönüşümler Için Genişletilebilir stıl sayfası dili (XSLT) dönüştürmeleri için kullanmaktan daha yavaştır.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği, <xref:System.Xml.XmlDocument> ' a gönderilen çıkış ile öğesine nasıl sağlanabilecek gösterilmektedir <xref:System.Xml.Xsl.XslTransform> <xref:System.Xml.XmlReader> .  
  
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
- [XslTransform Sınıfı ile XSLT Dönüşümleri](xslt-transformations-with-the-xsltransform-class.md)
- [XslTransform Sınıfı XSLT İşlemcisini Uygular](xsltransform-class-implements-the-xslt-processor.md)
- [Dönüşümlerde XPathNavigator](xpathnavigator-in-transformations.md)
- [Dönüşümlerde XPathNodeIterator](xpathnodeiterator-in-transformations.md)
- [XslTransform’a XPathDocument Girişi](xpathdocument-input-to-xsltransform.md)
- [XslTransform’a XmlDataDocument Girişi](xmldatadocument-input-to-xsltransform.md)
