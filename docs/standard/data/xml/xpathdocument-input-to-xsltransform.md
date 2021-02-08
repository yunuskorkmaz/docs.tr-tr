---
description: Daha fazla bilgi için bkz. XslTransform için XPathDocument girişi
title: XslTransform’a XPathDocument Girişi
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 7d1bbe8b-ed43-4e62-a5ba-d602d244f4ae
ms.openlocfilehash: 5778a359cd4bfa748318533c9be6a1def97b5be3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99782591"
---
# <a name="xpathdocument-input-to-xsltransform"></a>XslTransform’a XPathDocument Girişi

, <xref:System.Xml.XPath.XPathDocument> İle belgelerin işlenmesine yönelik salt okunurdur <xref:System.Xml.Xsl.XslTransform> . Bu, XML Belge Nesne Modeli (DOM) için yapısal olarak benzerdir, ancak ' deki XPath iyileştirme işlevleri kullanılarak dönüşümler için Genişletilebilir Stil sayfası dili (XSLT) işleme ve XML yol dili (XPath) veri modeli için oldukça iyileştirilmiştir <xref:System.Xml.XPath.XPathNavigator> .  
  
> [!NOTE]
> <xref:System.Xml.Xsl.XslTransform>Sınıf .NET Framework 2,0 ' de kullanılmıyor. Sınıfını kullanarak dönüşümler için Genişletilebilir Stil sayfası dili (XSLT) dönüşümleri gerçekleştirebilirsiniz <xref:System.Xml.Xsl.XslCompiledTransform> . Daha fazla bilgi için, bkz. [XslCompiledTransform sınıfını kullanma](using-the-xslcompiledtransform-class.md) ve [XslTransform sınıfından geçiş](migrating-from-the-xsltransform-class.md) .  
  
 Aşağıdaki kod örneği <xref:System.Xml.XPath.XPathDocument> bir Transform için bir as girişi oluşturur.  
  
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

- [XslTransform Sınıfı XSLT İşlemcisini Uygular](xsltransform-class-implements-the-xslt-processor.md)
