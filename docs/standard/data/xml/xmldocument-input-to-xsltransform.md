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
# <a name="xmldocument-input-to-xsltransform"></a><span data-ttu-id="2362a-102">XslTransform’a XmlDocument Girişi</span><span class="sxs-lookup"><span data-stu-id="2362a-102">XmlDocument Input to XslTransform</span></span>
<span data-ttu-id="2362a-103"><xref:System.Xml.XmlDocument> sınıfı, bir XML belgesi için özellikleri düzenlemenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="2362a-103">The <xref:System.Xml.XmlDocument> class provides editing capabilities for an XML document.</span></span> <span data-ttu-id="2362a-104">XML 'nin <xref:System.Xml.Xsl.XslTransform.Transform%2A> yöntemine gönderilmeden önce düzenlenmesi veya değiştirilmesi gerekiyorsa, XML 'yi bir <xref:System.Xml.XmlDocument>yükleyin, düzenleyin ve <xref:System.Xml.Xsl.XslTransform>içine gönderin.</span><span class="sxs-lookup"><span data-stu-id="2362a-104">If the XML needs to be edited or modified before being sent to the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method, load the XML into an <xref:System.Xml.XmlDocument>, edit it, and send it in to the <xref:System.Xml.Xsl.XslTransform>.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2362a-105"><xref:System.Xml.Xsl.XslTransform> sınıfı, .NET Framework 2,0 ' de kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="2362a-105">The <xref:System.Xml.Xsl.XslTransform> class is obsolete in the .NET Framework 2.0.</span></span> <span data-ttu-id="2362a-106"><xref:System.Xml.Xsl.XslCompiledTransform> sınıfını kullanarak dönüşümler için Genişletilebilir Stil sayfası dili (XSLT) dönüşümleri gerçekleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2362a-106">You can perform Extensible Stylesheet Language for Transformations (XSLT) transformations using the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span> <span data-ttu-id="2362a-107">Daha fazla bilgi için, bkz. [XslCompiledTransform sınıfını kullanma](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) ve [XslTransform sınıfından geçiş](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md) .</span><span class="sxs-lookup"><span data-stu-id="2362a-107">See [Using the XslCompiledTransform Class](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) and [Migrating From the XslTransform Class](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md) for more information.</span></span>  
  
 <span data-ttu-id="2362a-108"><xref:System.Xml.XmlDocument> <xref:System.Xml.XPath.IXPathNavigable> arabirimini uygular, bu nedenle belge, Düzenlemeden sonra <xref:System.Xml.Xsl.XslTransform.Transform%2A> yöntemine geçirilebilir.</span><span class="sxs-lookup"><span data-stu-id="2362a-108">The <xref:System.Xml.XmlDocument> implements the <xref:System.Xml.XPath.IXPathNavigable> interface, so the document can be passed to the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method after editing.</span></span>  
  
 <span data-ttu-id="2362a-109"><xref:System.Xml.XmlDocument>'nin düzenlenme özelliği nedeniyle, bir dönüşüme giriş olarak <xref:System.Xml.XmlDocument> sınıfının kullanılması, iç depolama nedeniyle XML yol dili (XPath) sorguları için optimize edilmiş şekilde, <xref:System.Xml.XPath.XPathDocument> dönüşümler için Genişletilebilir Stil sayfası dili (XSLT) dönüştürmelerinin <xref:System.Xml.XPath.XPathDocument> kullanmaktan daha yavaştır.</span><span class="sxs-lookup"><span data-stu-id="2362a-109">Due to the editing capability of the <xref:System.Xml.XmlDocument>, using the <xref:System.Xml.XmlDocument> class as input to a transformation is slower than using an <xref:System.Xml.XPath.XPathDocument> for the Extensible Stylesheet Language for Transformations (XSLT) transformations, as the <xref:System.Xml.XPath.XPathDocument> is optimized for XML Path Language (XPath) queries due to the internal storage.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2362a-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="2362a-110">Example</span></span>  
 <span data-ttu-id="2362a-111">Aşağıdaki kod örneği, bir <xref:System.Xml.XmlReader>gönderilen çıkış ile <xref:System.Xml.Xsl.XslTransform><xref:System.Xml.XmlDocument> nasıl sağlanabilecek gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="2362a-111">The following code example shows how an <xref:System.Xml.XmlDocument> can be supplied to the <xref:System.Xml.Xsl.XslTransform>, with the output sent to an <xref:System.Xml.XmlReader>.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="2362a-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2362a-112">See also</span></span>

- <xref:System.Xml.XmlDocument>
- [<span data-ttu-id="2362a-113">XslTransform Sınıfı ile XSLT Dönüşümleri</span><span class="sxs-lookup"><span data-stu-id="2362a-113">XSLT Transformations with the XslTransform Class</span></span>](../../../../docs/standard/data/xml/xslt-transformations-with-the-xsltransform-class.md)
- [<span data-ttu-id="2362a-114">XslTransform Sınıfı XSLT İşlemcisini Uygular</span><span class="sxs-lookup"><span data-stu-id="2362a-114">XslTransform Class Implements the XSLT Processor</span></span>](../../../../docs/standard/data/xml/xsltransform-class-implements-the-xslt-processor.md)
- [<span data-ttu-id="2362a-115">Dönüşümlerde XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="2362a-115">XPathNavigator in Transformations</span></span>](../../../../docs/standard/data/xml/xpathnavigator-in-transformations.md)
- [<span data-ttu-id="2362a-116">Dönüşümlerde XPathNodeIterator</span><span class="sxs-lookup"><span data-stu-id="2362a-116">XPathNodeIterator in Transformations</span></span>](../../../../docs/standard/data/xml/xpathnodeiterator-in-transformations.md)
- [<span data-ttu-id="2362a-117">XslTransform’a XPathDocument Girişi</span><span class="sxs-lookup"><span data-stu-id="2362a-117">XPathDocument Input to XslTransform</span></span>](../../../../docs/standard/data/xml/xpathdocument-input-to-xsltransform.md)
- [<span data-ttu-id="2362a-118">XslTransform’a XmlDataDocument Girişi</span><span class="sxs-lookup"><span data-stu-id="2362a-118">XmlDataDocument Input to XslTransform</span></span>](../../../../docs/standard/data/xml/xmldatadocument-input-to-xsltransform.md)
