---
title: XslTransform’a XPathDocument Girişi
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 7d1bbe8b-ed43-4e62-a5ba-d602d244f4ae
author: mairaw
ms.author: mairaw
ms.openlocfilehash: beefaffa0365efbb808fd15c1253027e4d5b09a1
ms.sourcegitcommit: a8d3504f0eae1a40bda2b06bd441ba01f1631ef0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/18/2019
ms.locfileid: "67170912"
---
# <a name="xpathdocument-input-to-xsltransform"></a>XslTransform’a XPathDocument Girişi
<xref:System.Xml.XPath.XPathDocument> Belgelerle işlemek için salt okunur önbellek <xref:System.Xml.Xsl.XslTransform>. XML belge nesne modeli (DOM) yapısal olarak benzerdir, ancak bu yüksek oranda için Genişletilebilir Stil Sayfası Dil Dönüşümleri (XSLT) işleme ve XML Path Language (XPath) veri modeli üzerinde XPathiyileştirmeişlevlerikullanarakiçinoptimizeedilmiştir<xref:System.Xml.XPath.XPathNavigator>.  
  
> [!NOTE]
>  <xref:System.Xml.Xsl.XslTransform> Sınıfı .NET Framework 2. 0'kullanılmıyor. Genişletilebilir Stil Sayfası Dil Dönüşümleri (XSLT) dönüştürmeleri için kullanarak gerçekleştirebileceğiniz <xref:System.Xml.Xsl.XslCompiledTransform> sınıfı. Bkz: [XslCompiledTransform sınıfını kullanma](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) ve [geçirme gelen XslTransform sınıfı](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md) daha fazla bilgi için.  
  
 Aşağıdaki kod örneği oluşturur bir <xref:System.Xml.XPath.XPathDocument> dönüşüm giriş olarak.  
  
```vb  
Dim xslt as XslTransform = new XslTransform()  
Xslt.Load(someStylesheet)  
Dim doc as XPathDocument = New XPathDocument("books.xml")  
Dim fs as StringWriter = new StringWriter()  
Xslt.Transform(doc, Nothing, fs, Nothing);  
```  
  
```csharp  
XslTransform xslt = new XslTransform();  
Xslt.Load(someStylesheet);  
XPathDocument doc = XPathDocument("books.xml");  
StringWriter fs = new StringWriter();  
Xslt.Transform(doc, null, fs, null);  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XslTransform Sınıfı XSLT İşlemcisini Uygular](../../../../docs/standard/data/xml/xsltransform-class-implements-the-xslt-processor.md)
