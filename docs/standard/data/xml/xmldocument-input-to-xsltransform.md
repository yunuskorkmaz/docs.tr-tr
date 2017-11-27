---
title: "Çok XmlDocument giriş"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 97115892-410a-4657-ab47-1e14dfba73f8
caps.latest.revision: "3"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 554faffb676337f8846eb6ba24152d77793b8fe0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="xmldocument-input-to-xsltransform"></a><span data-ttu-id="a3428-102">Çok XmlDocument giriş</span><span class="sxs-lookup"><span data-stu-id="a3428-102">XmlDocument Input to XslTransform</span></span>
<span data-ttu-id="a3428-103"><xref:System.Xml.XmlDocument> Sınıfı bir XML belgesi için düzenleme özellikleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="a3428-103">The <xref:System.Xml.XmlDocument> class provides editing capabilities for an XML document.</span></span> <span data-ttu-id="a3428-104">XML düzenlenmesine veya için gönderilmeden önce değiştirilen gerekip gerekmediğini <xref:System.Xml.Xsl.XslTransform.Transform%2A> yöntemi, XML öğesine yük bir <xref:System.Xml.XmlDocument>, düzenlemek ve içinde göndermeden <xref:System.Xml.Xsl.XslTransform>.</span><span class="sxs-lookup"><span data-stu-id="a3428-104">If the XML needs to be edited or modified before being sent to the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method, load the XML into an <xref:System.Xml.XmlDocument>, edit it, and send it in to the <xref:System.Xml.Xsl.XslTransform>.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a3428-105"><xref:System.Xml.Xsl.XslTransform> Sınıftır'te eski [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)].</span><span class="sxs-lookup"><span data-stu-id="a3428-105">The <xref:System.Xml.Xsl.XslTransform> class is obsolete in the [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)].</span></span> <span data-ttu-id="a3428-106">Genişletilebilir Stil sayfası dili kullanarak Dönüşümleri (XSLT) dönüştürmeleri için gerçekleştirebilirsiniz <xref:System.Xml.Xsl.XslCompiledTransform> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="a3428-106">You can perform Extensible Stylesheet Language for Transformations (XSLT) transformations using the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span> <span data-ttu-id="a3428-107">Bkz: [XslCompiledTransform sınıfını kullanarak](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) ve [çok sınıfı geçirme](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md) daha fazla bilgi için.</span><span class="sxs-lookup"><span data-stu-id="a3428-107">See [Using the XslCompiledTransform Class](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) and [Migrating From the XslTransform Class](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md) for more information.</span></span>  
  
 <span data-ttu-id="a3428-108"><xref:System.Xml.XmlDocument> Uygulayan <xref:System.Xml.XPath.IXPathNavigable> arabirim için belge geçirilebilmesi <xref:System.Xml.Xsl.XslTransform.Transform%2A> düzenleme sonrasında yöntemi.</span><span class="sxs-lookup"><span data-stu-id="a3428-108">The <xref:System.Xml.XmlDocument> implements the <xref:System.Xml.XPath.IXPathNavigable> interface, so the document can be passed to the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method after editing.</span></span>  
  
 <span data-ttu-id="a3428-109">Düzenleme yeteneğini nedeniyle <xref:System.Xml.XmlDocument>kullanarak <xref:System.Xml.XmlDocument> sınıfı bir dönüşüm girişine kullanmaktan daha yavaş olduğu gibi bir <xref:System.Xml.XPath.XPathDocument> Dönüşümleri (XSLT) dönüştürmeleri için Genişletilebilir Stil sayfası dilde olarak <xref:System.Xml.XPath.XPathDocument> olduğu İç depolaması nedeniyle XML Path dili (XPath) sorguları için en iyi duruma getirilmiş.</span><span class="sxs-lookup"><span data-stu-id="a3428-109">Due to the editing capability of the <xref:System.Xml.XmlDocument>, using the <xref:System.Xml.XmlDocument> class as input to a transformation is slower than using an <xref:System.Xml.XPath.XPathDocument> for the Extensible Stylesheet Language for Transformations (XSLT) transformations, as the <xref:System.Xml.XPath.XPathDocument> is optimized for XML Path Language (XPath) queries due to the internal storage.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a3428-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="a3428-110">Example</span></span>  
 <span data-ttu-id="a3428-111">Aşağıdaki örnekte gösterildiği nasıl kod bir <xref:System.Xml.XmlDocument> için sağlanan <xref:System.Xml.Xsl.XslTransform>, gönderilen çıkış bir <xref:System.Xml.XmlReader>.</span><span class="sxs-lookup"><span data-stu-id="a3428-111">The following code example shows how an <xref:System.Xml.XmlDocument> can be supplied to the <xref:System.Xml.Xsl.XslTransform>, with the output sent to an <xref:System.Xml.XmlReader>.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="a3428-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a3428-112">See Also</span></span>  
 <xref:System.Xml.XmlDocument>  
 [<span data-ttu-id="a3428-113">Çok sınıfı ile XSLT dönüştürmeler</span><span class="sxs-lookup"><span data-stu-id="a3428-113">XSLT Transformations with the XslTransform Class</span></span>](../../../../docs/standard/data/xml/xslt-transformations-with-the-xsltransform-class.md)  
 [<span data-ttu-id="a3428-114">XSLT işlemci çok sınıfı uygular</span><span class="sxs-lookup"><span data-stu-id="a3428-114">XslTransform Class Implements the XSLT Processor</span></span>](../../../../docs/standard/data/xml/xsltransform-class-implements-the-xslt-processor.md)  
 [<span data-ttu-id="a3428-115">Dönüşümleri XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="a3428-115">XPathNavigator in Transformations</span></span>](../../../../docs/standard/data/xml/xpathnavigator-in-transformations.md)  
 [<span data-ttu-id="a3428-116">Dönüşümleri XPathNodeIterator</span><span class="sxs-lookup"><span data-stu-id="a3428-116">XPathNodeIterator in Transformations</span></span>](../../../../docs/standard/data/xml/xpathnodeiterator-in-transformations.md)  
 [<span data-ttu-id="a3428-117">Çok XPathDocument giriş</span><span class="sxs-lookup"><span data-stu-id="a3428-117">XPathDocument Input to XslTransform</span></span>](../../../../docs/standard/data/xml/xpathdocument-input-to-xsltransform.md)  
 [<span data-ttu-id="a3428-118">Çok XmlDataDocument giriş</span><span class="sxs-lookup"><span data-stu-id="a3428-118">XmlDataDocument Input to XslTransform</span></span>](../../../../docs/standard/data/xml/xmldatadocument-input-to-xsltransform.md)
