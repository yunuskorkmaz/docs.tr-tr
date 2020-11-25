---
title: XslTransform’a XmlDocument Girişi
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 97115892-410a-4657-ab47-1e14dfba73f8
ms.openlocfilehash: 1c7aa1a9d5c02aaac5a78603bd2397f012d4640d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95721939"
---
# <a name="xmldocument-input-to-xsltransform"></a><span data-ttu-id="93ef3-102">XslTransform’a XmlDocument Girişi</span><span class="sxs-lookup"><span data-stu-id="93ef3-102">XmlDocument Input to XslTransform</span></span>

<span data-ttu-id="93ef3-103"><xref:System.Xml.XmlDocument>Sınıfı, BIR XML belgesi için düzenlenebilir özellikleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="93ef3-103">The <xref:System.Xml.XmlDocument> class provides editing capabilities for an XML document.</span></span> <span data-ttu-id="93ef3-104">XML 'nin yönteme gönderilmeden önce düzenlenmesi veya değiştirilmesi gerekiyorsa, XML 'yi bir öğesine <xref:System.Xml.Xsl.XslTransform.Transform%2A> yükleyin <xref:System.Xml.XmlDocument> , düzenleyin ve içine gönderin <xref:System.Xml.Xsl.XslTransform> .</span><span class="sxs-lookup"><span data-stu-id="93ef3-104">If the XML needs to be edited or modified before being sent to the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method, load the XML into an <xref:System.Xml.XmlDocument>, edit it, and send it in to the <xref:System.Xml.Xsl.XslTransform>.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="93ef3-105"><xref:System.Xml.Xsl.XslTransform>Sınıf .NET Framework 2,0 ' de kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="93ef3-105">The <xref:System.Xml.Xsl.XslTransform> class is obsolete in the .NET Framework 2.0.</span></span> <span data-ttu-id="93ef3-106">Sınıfını kullanarak dönüşümler için Genişletilebilir Stil sayfası dili (XSLT) dönüşümleri gerçekleştirebilirsiniz <xref:System.Xml.Xsl.XslCompiledTransform> .</span><span class="sxs-lookup"><span data-stu-id="93ef3-106">You can perform Extensible Stylesheet Language for Transformations (XSLT) transformations using the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span> <span data-ttu-id="93ef3-107">Daha fazla bilgi için, bkz. [XslCompiledTransform sınıfını kullanma](using-the-xslcompiledtransform-class.md) ve [XslTransform sınıfından geçiş](migrating-from-the-xsltransform-class.md) .</span><span class="sxs-lookup"><span data-stu-id="93ef3-107">See [Using the XslCompiledTransform Class](using-the-xslcompiledtransform-class.md) and [Migrating From the XslTransform Class](migrating-from-the-xsltransform-class.md) for more information.</span></span>  
  
 <span data-ttu-id="93ef3-108">, <xref:System.Xml.XmlDocument> Arabirimini uygular <xref:System.Xml.XPath.IXPathNavigable> , bu nedenle belge <xref:System.Xml.Xsl.XslTransform.Transform%2A> Düzenlemeden sonra yönteme geçirilebilir.</span><span class="sxs-lookup"><span data-stu-id="93ef3-108">The <xref:System.Xml.XmlDocument> implements the <xref:System.Xml.XPath.IXPathNavigable> interface, so the document can be passed to the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method after editing.</span></span>  
  
 <span data-ttu-id="93ef3-109">Öğesinin düzenlenme özelliği nedeniyle, <xref:System.Xml.XmlDocument> <xref:System.Xml.XmlDocument> sınıfının bir dönüşüme giriş olarak kullanılması, <xref:System.Xml.XPath.XPathDocument> <xref:System.Xml.XPath.XPathDocument> Iç depolama nedeniyle XML yol dili (XPath) sorguları için optimize edilmiş olduğundan, dönüşümler Için Genişletilebilir stıl sayfası dili (XSLT) dönüştürmeleri için kullanmaktan daha yavaştır.</span><span class="sxs-lookup"><span data-stu-id="93ef3-109">Due to the editing capability of the <xref:System.Xml.XmlDocument>, using the <xref:System.Xml.XmlDocument> class as input to a transformation is slower than using an <xref:System.Xml.XPath.XPathDocument> for the Extensible Stylesheet Language for Transformations (XSLT) transformations, as the <xref:System.Xml.XPath.XPathDocument> is optimized for XML Path Language (XPath) queries due to the internal storage.</span></span>  
  
## <a name="example"></a><span data-ttu-id="93ef3-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="93ef3-110">Example</span></span>  

 <span data-ttu-id="93ef3-111">Aşağıdaki kod örneği, <xref:System.Xml.XmlDocument> ' a gönderilen çıkış ile öğesine nasıl sağlanabilecek gösterilmektedir <xref:System.Xml.Xsl.XslTransform> <xref:System.Xml.XmlReader> .</span><span class="sxs-lookup"><span data-stu-id="93ef3-111">The following code example shows how an <xref:System.Xml.XmlDocument> can be supplied to the <xref:System.Xml.Xsl.XslTransform>, with the output sent to an <xref:System.Xml.XmlReader>.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="93ef3-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="93ef3-112">See also</span></span>

- <xref:System.Xml.XmlDocument>
- [<span data-ttu-id="93ef3-113">XslTransform Sınıfı ile XSLT Dönüşümleri</span><span class="sxs-lookup"><span data-stu-id="93ef3-113">XSLT Transformations with the XslTransform Class</span></span>](xslt-transformations-with-the-xsltransform-class.md)
- [<span data-ttu-id="93ef3-114">XslTransform Sınıfı XSLT İşlemcisini Uygular</span><span class="sxs-lookup"><span data-stu-id="93ef3-114">XslTransform Class Implements the XSLT Processor</span></span>](xsltransform-class-implements-the-xslt-processor.md)
- [<span data-ttu-id="93ef3-115">Dönüşümlerde XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="93ef3-115">XPathNavigator in Transformations</span></span>](xpathnavigator-in-transformations.md)
- [<span data-ttu-id="93ef3-116">Dönüşümlerde XPathNodeIterator</span><span class="sxs-lookup"><span data-stu-id="93ef3-116">XPathNodeIterator in Transformations</span></span>](xpathnodeiterator-in-transformations.md)
- [<span data-ttu-id="93ef3-117">XslTransform’a XPathDocument Girişi</span><span class="sxs-lookup"><span data-stu-id="93ef3-117">XPathDocument Input to XslTransform</span></span>](xpathdocument-input-to-xsltransform.md)
- [<span data-ttu-id="93ef3-118">XslTransform’a XmlDataDocument Girişi</span><span class="sxs-lookup"><span data-stu-id="93ef3-118">XmlDataDocument Input to XslTransform</span></span>](xmldatadocument-input-to-xsltransform.md)
