---
title: "Düğüm dönüşümler ayarlar"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ad034f0e-ff8b-4a71-9a4c-528c754263c4
caps.latest.revision: "4"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: e4d6d2f5a68ce5cef9937edc136e52efcd5366df
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="node-sets-in-transformations"></a><span data-ttu-id="de763-102">Düğüm dönüşümler ayarlar</span><span class="sxs-lookup"><span data-stu-id="de763-102">Node Sets in Transformations</span></span>
<span data-ttu-id="de763-103">Düğüm kümeleri gelen XML Path dili (XPath) ifadeleri döndürülen dört temel veri türlerini biridir.</span><span class="sxs-lookup"><span data-stu-id="de763-103">Node sets are one of four basic data types that are returned from XML Path Language (XPath) expressions.</span></span> <span data-ttu-id="de763-104">Belge sırada oluşturulan yinelemeleri olmadan düğümler sırasız bir koleksiyonudur, stil sayfası bir değişkende atanmış bir düğüm kümesi.</span><span class="sxs-lookup"><span data-stu-id="de763-104">A node set, which is an unordered collection of nodes without duplicates, created in document order, can be assigned to a variable in a style sheet.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="de763-105"><xref:System.Xml.Xsl.XslTransform> Sınıftır'te eski [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)].</span><span class="sxs-lookup"><span data-stu-id="de763-105">The <xref:System.Xml.Xsl.XslTransform> class is obsolete in the [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)].</span></span> <span data-ttu-id="de763-106">Genişletilebilir Stil sayfası dili kullanarak Dönüşümleri (XSLT) dönüştürmeleri için gerçekleştirebilirsiniz <xref:System.Xml.Xsl.XslCompiledTransform> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="de763-106">You can perform Extensible Stylesheet Language for Transformations (XSLT) transformations using the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span> <span data-ttu-id="de763-107">Bkz: [XslCompiledTransform sınıfını kullanarak](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) ve [çok sınıfı geçirme](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md) daha fazla bilgi için.</span><span class="sxs-lookup"><span data-stu-id="de763-107">See [Using the XslCompiledTransform Class](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) and [Migrating From the XslTransform Class](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md) for more information.</span></span>  
  
 <span data-ttu-id="de763-108">Düğüm kümeleri gelen XPath ifadeleri döndürülen dört temel veri türlerini biridir.</span><span class="sxs-lookup"><span data-stu-id="de763-108">Node sets are one of four basic data types that are returned from XPath expressions.</span></span> <span data-ttu-id="de763-109">Belge sırada oluşturulan yinelemeleri olmadan düğümler sırasız bir koleksiyonudur, stil sayfası bir değişkende atanmış bir düğüm kümesi.</span><span class="sxs-lookup"><span data-stu-id="de763-109">A node set, which is an unordered collection of nodes without duplicates, created in document order, can be assigned to a variable in a style sheet.</span></span> <span data-ttu-id="de763-110">XPath ifadesi kullanılan sonucu bu düğüm kümesi bir `select` özniteliği bir dönüşüm, XML belge nesne modeli (DOM) gelen ayarlanmış bir düğümü aynı davranışı sahiptir.</span><span class="sxs-lookup"><span data-stu-id="de763-110">This node set, which is a result of an XPath expression used in a `select` attribute in a transformation, has the same behavior as a node set from the XML Document Object Model (DOM).</span></span> <span data-ttu-id="de763-111">Bir dizi gösterilen yöntem kullanılarak ayarlanan bir düğüm gidebilirsiniz [düğüm kümesi Gezinti kullanarak XPathNavigator](../../../../docs/standard/data/xml/node-set-navigation-using-xpathnavigator.md), farklı sonuç ağacı parçası veya kullanan sonuç ağacı parçası olarak <xref:System.Xml.XPath.XPathNodeIterator> gezinti için.</span><span class="sxs-lookup"><span data-stu-id="de763-111">You can navigate a node set using a set of methods shown in [Node Set Navigation Using XPathNavigator](../../../../docs/standard/data/xml/node-set-navigation-using-xpathnavigator.md), unlike a result tree fragment or result tree fragment, which uses the <xref:System.Xml.XPath.XPathNodeIterator> for navigation.</span></span>  
  
 <span data-ttu-id="de763-112">Aşağıdaki kod örneği, yinelemek gösterilmiştir bir düğüm kümesi üzerinde bir `variable` veya `parameter` bir stil sayfası öğesinde düğüm kümesi olarak değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="de763-112">The following code sample shows how to iterate over a node set when a `variable` or `parameter` element in a style sheet evaluates to a node set.</span></span>  
  
## <a name="style-sheet"></a><span data-ttu-id="de763-113">Stil sayfası</span><span class="sxs-lookup"><span data-stu-id="de763-113">Style Sheet</span></span>  
  
```xml  
<xsl:stylesheet xmlns:xsl="http://www.w3.org/1999/XSL/Transform" version="1.0">  
  
    <xsl:variable name="x" select="bookstore/book/title"></xsl:variable>  
  
    <xsl:template match="/">  
        <xsl:for-each select="$x">  
            ******  
            <xsl:value-of select="."></xsl:value-of>  
            ******  
        </xsl:for-each>  
    </xsl:template>  
  
</xsl:stylesheet>  
```  
  
## <a name="input"></a><span data-ttu-id="de763-114">Giriş</span><span class="sxs-lookup"><span data-stu-id="de763-114">Input</span></span>  
  
```xml  
<bookstore>  
   <book style="autobiography">  
      <title>Seven Years in Trenton</title>  
   </book>  
  
   <book style="autobiography">  
      <title>Seven Years in Trenton2</title>  
   </book>  
  
   <book style="textbook">  
      <title>History of Trenton Vol 3</title>  
   </book>  
</bookstore>  
```  
  
## <a name="output"></a><span data-ttu-id="de763-115">Çıkış</span><span class="sxs-lookup"><span data-stu-id="de763-115">Output</span></span>  
  
```  
******  
Seven Years in Trenton  
******  
  
******  
Seven Years in Trenton2  
******  
  
******  
History of Trenton Vol 3  
******  
```  
  
## <a name="see-also"></a><span data-ttu-id="de763-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="de763-116">See Also</span></span>  
 <xref:System.Xml.XPath.XPathNodeIterator>  
 [<span data-ttu-id="de763-117">Çok sınıfı ile XSLT dönüştürmeler</span><span class="sxs-lookup"><span data-stu-id="de763-117">XSLT Transformations with the XslTransform Class</span></span>](../../../../docs/standard/data/xml/xslt-transformations-with-the-xsltransform-class.md)  
 [<span data-ttu-id="de763-118">XSLT işlemci çok sınıfı uygular</span><span class="sxs-lookup"><span data-stu-id="de763-118">XslTransform Class Implements the XSLT Processor</span></span>](../../../../docs/standard/data/xml/xsltransform-class-implements-the-xslt-processor.md)
