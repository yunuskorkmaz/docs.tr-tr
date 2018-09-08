---
title: Xsltransform'a XmlDocument girişi
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 97115892-410a-4657-ab47-1e14dfba73f8
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e83cf82aee57b1f40f695700d8d0b38c12e0ac39
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2018
ms.locfileid: "44217054"
---
# <a name="xmldocument-input-to-xsltransform"></a><span data-ttu-id="75b0a-102">Xsltransform'a XmlDocument girişi</span><span class="sxs-lookup"><span data-stu-id="75b0a-102">XmlDocument Input to XslTransform</span></span>
<span data-ttu-id="75b0a-103"><xref:System.Xml.XmlDocument> Sınıf bir XML belgesi için düzenleme özellikleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="75b0a-103">The <xref:System.Xml.XmlDocument> class provides editing capabilities for an XML document.</span></span> <span data-ttu-id="75b0a-104">XML düzenlenmesine veya için gönderilmeden önce değiştirilen gerekip gerekmediğini <xref:System.Xml.Xsl.XslTransform.Transform%2A> yöntemi, XML verilerinin yük bir <xref:System.Xml.XmlDocument>, düzenlemek ve içinde göndermek <xref:System.Xml.Xsl.XslTransform>.</span><span class="sxs-lookup"><span data-stu-id="75b0a-104">If the XML needs to be edited or modified before being sent to the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method, load the XML into an <xref:System.Xml.XmlDocument>, edit it, and send it in to the <xref:System.Xml.Xsl.XslTransform>.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="75b0a-105"><xref:System.Xml.Xsl.XslTransform> Sınıftır eski [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)].</span><span class="sxs-lookup"><span data-stu-id="75b0a-105">The <xref:System.Xml.Xsl.XslTransform> class is obsolete in the [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)].</span></span> <span data-ttu-id="75b0a-106">Genişletilebilir Stil Sayfası Dil Dönüşümleri (XSLT) dönüştürmeleri için kullanarak gerçekleştirebileceğiniz <xref:System.Xml.Xsl.XslCompiledTransform> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="75b0a-106">You can perform Extensible Stylesheet Language for Transformations (XSLT) transformations using the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span> <span data-ttu-id="75b0a-107">Bkz: [XslCompiledTransform sınıfını kullanma](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) ve [geçirme gelen XslTransform sınıfı](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md) daha fazla bilgi için.</span><span class="sxs-lookup"><span data-stu-id="75b0a-107">See [Using the XslCompiledTransform Class](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) and [Migrating From the XslTransform Class](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md) for more information.</span></span>  
  
 <span data-ttu-id="75b0a-108"><xref:System.Xml.XmlDocument> Uygulayan <xref:System.Xml.XPath.IXPathNavigable> belge geçirilebilir için arabirim <xref:System.Xml.Xsl.XslTransform.Transform%2A> düzenleme sonra yöntemi.</span><span class="sxs-lookup"><span data-stu-id="75b0a-108">The <xref:System.Xml.XmlDocument> implements the <xref:System.Xml.XPath.IXPathNavigable> interface, so the document can be passed to the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method after editing.</span></span>  
  
 <span data-ttu-id="75b0a-109">Düzenleme yeteneğini nedeniyle <xref:System.Xml.XmlDocument>kullanarak <xref:System.Xml.XmlDocument> sınıf dönüştürme için giriş kullanmaktan daha yavaş olduğu gibi bir <xref:System.Xml.XPath.XPathDocument> Genişletilebilir Stil Sayfası Dil Dönüşümleri (XSLT) dönüşümlere olarak <xref:System.Xml.XPath.XPathDocument> olduğu İç Depolama nedeniyle XML Path Language (XPath) sorgular için en iyi duruma getirilmiş.</span><span class="sxs-lookup"><span data-stu-id="75b0a-109">Due to the editing capability of the <xref:System.Xml.XmlDocument>, using the <xref:System.Xml.XmlDocument> class as input to a transformation is slower than using an <xref:System.Xml.XPath.XPathDocument> for the Extensible Stylesheet Language for Transformations (XSLT) transformations, as the <xref:System.Xml.XPath.XPathDocument> is optimized for XML Path Language (XPath) queries due to the internal storage.</span></span>  
  
## <a name="example"></a><span data-ttu-id="75b0a-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="75b0a-110">Example</span></span>  
 <span data-ttu-id="75b0a-111">Aşağıdaki örnekte gösterildiği nasıl kod bir <xref:System.Xml.XmlDocument> için sağlanan <xref:System.Xml.Xsl.XslTransform>, gönderilen çıktıyla bir <xref:System.Xml.XmlReader>.</span><span class="sxs-lookup"><span data-stu-id="75b0a-111">The following code example shows how an <xref:System.Xml.XmlDocument> can be supplied to the <xref:System.Xml.Xsl.XslTransform>, with the output sent to an <xref:System.Xml.XmlReader>.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="75b0a-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="75b0a-112">See also</span></span>

- <xref:System.Xml.XmlDocument>  
- [<span data-ttu-id="75b0a-113">XslTransform Sınıfı ile XSLT Dönüşümleri</span><span class="sxs-lookup"><span data-stu-id="75b0a-113">XSLT Transformations with the XslTransform Class</span></span>](../../../../docs/standard/data/xml/xslt-transformations-with-the-xsltransform-class.md)  
- [<span data-ttu-id="75b0a-114">XslTransform Sınıfı XSLT İşlemcisini Uygular</span><span class="sxs-lookup"><span data-stu-id="75b0a-114">XslTransform Class Implements the XSLT Processor</span></span>](../../../../docs/standard/data/xml/xsltransform-class-implements-the-xslt-processor.md)  
- [<span data-ttu-id="75b0a-115">Dönüşümlerde XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="75b0a-115">XPathNavigator in Transformations</span></span>](../../../../docs/standard/data/xml/xpathnavigator-in-transformations.md)  
- [<span data-ttu-id="75b0a-116">Dönüşümlerde XPathNodeIterator</span><span class="sxs-lookup"><span data-stu-id="75b0a-116">XPathNodeIterator in Transformations</span></span>](../../../../docs/standard/data/xml/xpathnodeiterator-in-transformations.md)  
- [<span data-ttu-id="75b0a-117">XslTransform’a XPathDocument Girişi</span><span class="sxs-lookup"><span data-stu-id="75b0a-117">XPathDocument Input to XslTransform</span></span>](../../../../docs/standard/data/xml/xpathdocument-input-to-xsltransform.md)  
- [<span data-ttu-id="75b0a-118">XslTransform’a XmlDataDocument Girişi</span><span class="sxs-lookup"><span data-stu-id="75b0a-118">XmlDataDocument Input to XslTransform</span></span>](../../../../docs/standard/data/xml/xmldatadocument-input-to-xsltransform.md)
