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
# <a name="xpathdocument-input-to-xsltransform"></a><span data-ttu-id="5c53b-102">XslTransform’a XPathDocument Girişi</span><span class="sxs-lookup"><span data-stu-id="5c53b-102">XPathDocument Input to XslTransform</span></span>
<span data-ttu-id="5c53b-103"><xref:System.Xml.XPath.XPathDocument> Belgelerle işlemek için salt okunur önbellek <xref:System.Xml.Xsl.XslTransform>.</span><span class="sxs-lookup"><span data-stu-id="5c53b-103">The <xref:System.Xml.XPath.XPathDocument> is a read-only cache, for processing documents with <xref:System.Xml.Xsl.XslTransform>.</span></span> <span data-ttu-id="5c53b-104">XML belge nesne modeli (DOM) yapısal olarak benzerdir, ancak bu yüksek oranda için Genişletilebilir Stil Sayfası Dil Dönüşümleri (XSLT) işleme ve XML Path Language (XPath) veri modeli üzerinde XPathiyileştirmeişlevlerikullanarakiçinoptimizeedilmiştir<xref:System.Xml.XPath.XPathNavigator>.</span><span class="sxs-lookup"><span data-stu-id="5c53b-104">It is structurally similar to the XML Document Object Model (DOM), but it is highly optimized for Extensible Stylesheet Language for Transformations (XSLT) processing and the XML Path Language (XPath) data model using the XPath optimization functions on the <xref:System.Xml.XPath.XPathNavigator>.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5c53b-105"><xref:System.Xml.Xsl.XslTransform> Sınıfı .NET Framework 2. 0'kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="5c53b-105">The <xref:System.Xml.Xsl.XslTransform> class is obsolete in the .NET Framework 2.0.</span></span> <span data-ttu-id="5c53b-106">Genişletilebilir Stil Sayfası Dil Dönüşümleri (XSLT) dönüştürmeleri için kullanarak gerçekleştirebileceğiniz <xref:System.Xml.Xsl.XslCompiledTransform> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="5c53b-106">You can perform Extensible Stylesheet Language for Transformations (XSLT) transformations using the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span> <span data-ttu-id="5c53b-107">Bkz: [XslCompiledTransform sınıfını kullanma](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) ve [geçirme gelen XslTransform sınıfı](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md) daha fazla bilgi için.</span><span class="sxs-lookup"><span data-stu-id="5c53b-107">See [Using the XslCompiledTransform Class](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) and [Migrating From the XslTransform Class](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md) for more information.</span></span>  
  
 <span data-ttu-id="5c53b-108">Aşağıdaki kod örneği oluşturur bir <xref:System.Xml.XPath.XPathDocument> dönüşüm giriş olarak.</span><span class="sxs-lookup"><span data-stu-id="5c53b-108">The following code sample creates an <xref:System.Xml.XPath.XPathDocument> as input to a transform.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="5c53b-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5c53b-109">See also</span></span>

- [<span data-ttu-id="5c53b-110">XslTransform Sınıfı XSLT İşlemcisini Uygular</span><span class="sxs-lookup"><span data-stu-id="5c53b-110">XslTransform Class Implements the XSLT Processor</span></span>](../../../../docs/standard/data/xml/xsltransform-class-implements-the-xslt-processor.md)
