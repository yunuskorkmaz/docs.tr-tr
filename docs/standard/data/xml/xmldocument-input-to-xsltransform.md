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
# <a name="xmldocument-input-to-xsltransform"></a><span data-ttu-id="84299-102">XslTransform’a XmlDocument Girişi</span><span class="sxs-lookup"><span data-stu-id="84299-102">XmlDocument Input to XslTransform</span></span>
<span data-ttu-id="84299-103">Sınıfı <xref:System.Xml.XmlDocument> , bir XML belgesi için düzenlenebilir özellikleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="84299-103">The <xref:System.Xml.XmlDocument> class provides editing capabilities for an XML document.</span></span> <span data-ttu-id="84299-104">XML 'nin <xref:System.Xml.Xsl.XslTransform.Transform%2A> yönteme gönderilmeden önce düzenlenmesi veya değiştirilmesi gerekiyorsa, XML 'yi bir <xref:System.Xml.XmlDocument>öğesine yükleyin, düzenleyin ve içine <xref:System.Xml.Xsl.XslTransform>gönderin.</span><span class="sxs-lookup"><span data-stu-id="84299-104">If the XML needs to be edited or modified before being sent to the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method, load the XML into an <xref:System.Xml.XmlDocument>, edit it, and send it in to the <xref:System.Xml.Xsl.XslTransform>.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="84299-105"><xref:System.Xml.Xsl.XslTransform> Sınıf .NET Framework 2,0 ' de kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="84299-105">The <xref:System.Xml.Xsl.XslTransform> class is obsolete in the .NET Framework 2.0.</span></span> <span data-ttu-id="84299-106"><xref:System.Xml.Xsl.XslCompiledTransform> Sınıfını kullanarak dönüşümler için Genişletilebilir Stil sayfası dili (XSLT) dönüşümleri gerçekleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="84299-106">You can perform Extensible Stylesheet Language for Transformations (XSLT) transformations using the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span> <span data-ttu-id="84299-107">Daha fazla bilgi için, bkz. [XslCompiledTransform sınıfını kullanma](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) ve [XslTransform sınıfından geçiş](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md) .</span><span class="sxs-lookup"><span data-stu-id="84299-107">See [Using the XslCompiledTransform Class](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) and [Migrating From the XslTransform Class](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md) for more information.</span></span>  
  
 <span data-ttu-id="84299-108">, <xref:System.Xml.XmlDocument> Arabirimini<xref:System.Xml.XPath.IXPathNavigable> uygular, bu nedenle belge Düzenlemeden sonra <xref:System.Xml.Xsl.XslTransform.Transform%2A> yönteme geçirilebilir.</span><span class="sxs-lookup"><span data-stu-id="84299-108">The <xref:System.Xml.XmlDocument> implements the <xref:System.Xml.XPath.IXPathNavigable> interface, so the document can be passed to the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method after editing.</span></span>  
  
 <span data-ttu-id="84299-109">Öğesinin <xref:System.Xml.XmlDocument>düzenlenme özelliği nedeniyle, <xref:System.Xml.XmlDocument> sınıfının bir dönüşüme giriş olarak kullanılması, <xref:System.Xml.XPath.XPathDocument> olduğu gibi dönüşümler (XSLT) dönüştürmeleri için Genişletilebilir <xref:System.Xml.XPath.XPathDocument> stil sayfası dili için kullanmaktan daha yavaştır. iç depolama nedeniyle XML yol dili (XPath) sorguları için iyileştirildi.</span><span class="sxs-lookup"><span data-stu-id="84299-109">Due to the editing capability of the <xref:System.Xml.XmlDocument>, using the <xref:System.Xml.XmlDocument> class as input to a transformation is slower than using an <xref:System.Xml.XPath.XPathDocument> for the Extensible Stylesheet Language for Transformations (XSLT) transformations, as the <xref:System.Xml.XPath.XPathDocument> is optimized for XML Path Language (XPath) queries due to the internal storage.</span></span>  
  
## <a name="example"></a><span data-ttu-id="84299-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="84299-110">Example</span></span>  
 <span data-ttu-id="84299-111">Aşağıdaki kod örneği, <xref:System.Xml.XmlDocument> <xref:System.Xml.Xsl.XslTransform>' a gönderilen <xref:System.Xml.XmlReader>çıkış ile öğesine nasıl sağlanabilecek gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="84299-111">The following code example shows how an <xref:System.Xml.XmlDocument> can be supplied to the <xref:System.Xml.Xsl.XslTransform>, with the output sent to an <xref:System.Xml.XmlReader>.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="84299-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="84299-112">See also</span></span>

- <xref:System.Xml.XmlDocument>
- [<span data-ttu-id="84299-113">XslTransform Sınıfı ile XSLT Dönüşümleri</span><span class="sxs-lookup"><span data-stu-id="84299-113">XSLT Transformations with the XslTransform Class</span></span>](../../../../docs/standard/data/xml/xslt-transformations-with-the-xsltransform-class.md)
- [<span data-ttu-id="84299-114">XslTransform Sınıfı XSLT İşlemcisini Uygular</span><span class="sxs-lookup"><span data-stu-id="84299-114">XslTransform Class Implements the XSLT Processor</span></span>](../../../../docs/standard/data/xml/xsltransform-class-implements-the-xslt-processor.md)
- [<span data-ttu-id="84299-115">Dönüşümlerde XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="84299-115">XPathNavigator in Transformations</span></span>](../../../../docs/standard/data/xml/xpathnavigator-in-transformations.md)
- [<span data-ttu-id="84299-116">Dönüşümlerde XPathNodeIterator</span><span class="sxs-lookup"><span data-stu-id="84299-116">XPathNodeIterator in Transformations</span></span>](../../../../docs/standard/data/xml/xpathnodeiterator-in-transformations.md)
- [<span data-ttu-id="84299-117">XslTransform’a XPathDocument Girişi</span><span class="sxs-lookup"><span data-stu-id="84299-117">XPathDocument Input to XslTransform</span></span>](../../../../docs/standard/data/xml/xpathdocument-input-to-xsltransform.md)
- [<span data-ttu-id="84299-118">XslTransform’a XmlDataDocument Girişi</span><span class="sxs-lookup"><span data-stu-id="84299-118">XmlDataDocument Input to XslTransform</span></span>](../../../../docs/standard/data/xml/xmldatadocument-input-to-xsltransform.md)
