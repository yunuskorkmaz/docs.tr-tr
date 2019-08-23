---
title: Dönüşümlerdeki Düğüm Kümeleri
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: ad034f0e-ff8b-4a71-9a4c-528c754263c4
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 8a84234ee797dac7487492dc92af2de4fa7ef503
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69962545"
---
# <a name="node-sets-in-transformations"></a><span data-ttu-id="90c03-102">Dönüşümlerdeki Düğüm Kümeleri</span><span class="sxs-lookup"><span data-stu-id="90c03-102">Node Sets in Transformations</span></span>
<span data-ttu-id="90c03-103">Düğüm kümeleri, XML yol dili (XPath) ifadelerinden döndürülen dört temel veri türünden biridir.</span><span class="sxs-lookup"><span data-stu-id="90c03-103">Node sets are one of four basic data types that are returned from XML Path Language (XPath) expressions.</span></span> <span data-ttu-id="90c03-104">Belge düzeninde oluşturulan ve yinelenen düğümleri olmayan düğümlerin sıralanmamış bir koleksiyonu olan düğüm kümesi, bir stil sayfasında bir değişkene atanabilir.</span><span class="sxs-lookup"><span data-stu-id="90c03-104">A node set, which is an unordered collection of nodes without duplicates, created in document order, can be assigned to a variable in a style sheet.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="90c03-105"><xref:System.Xml.Xsl.XslTransform> Sınıf .NET Framework 2,0 ' de kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="90c03-105">The <xref:System.Xml.Xsl.XslTransform> class is obsolete in the .NET Framework 2.0.</span></span> <span data-ttu-id="90c03-106"><xref:System.Xml.Xsl.XslCompiledTransform> Sınıfını kullanarak dönüşümler için Genişletilebilir Stil sayfası dili (XSLT) dönüşümleri gerçekleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="90c03-106">You can perform Extensible Stylesheet Language for Transformations (XSLT) transformations using the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span> <span data-ttu-id="90c03-107">Daha fazla bilgi için, bkz. [XslCompiledTransform sınıfını kullanma](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) ve [XslTransform sınıfından geçiş](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md) .</span><span class="sxs-lookup"><span data-stu-id="90c03-107">See [Using the XslCompiledTransform Class](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) and [Migrating From the XslTransform Class](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md) for more information.</span></span>  
  
 <span data-ttu-id="90c03-108">Düğüm kümeleri, XPath ifadelerinden döndürülen dört temel veri türünden biridir.</span><span class="sxs-lookup"><span data-stu-id="90c03-108">Node sets are one of four basic data types that are returned from XPath expressions.</span></span> <span data-ttu-id="90c03-109">Belge düzeninde oluşturulan ve yinelenen düğümleri olmayan düğümlerin sıralanmamış bir koleksiyonu olan düğüm kümesi, bir stil sayfasında bir değişkene atanabilir.</span><span class="sxs-lookup"><span data-stu-id="90c03-109">A node set, which is an unordered collection of nodes without duplicates, created in document order, can be assigned to a variable in a style sheet.</span></span> <span data-ttu-id="90c03-110">Dönüşümdeki bir `select` öznitelikte kullanılan bir XPath ifadesinin sonucu olan bu düğüm kümesi, XML belge nesne modeli (DOM) bir düğüm kümesiyle aynı davranışa sahiptir.</span><span class="sxs-lookup"><span data-stu-id="90c03-110">This node set, which is a result of an XPath expression used in a `select` attribute in a transformation, has the same behavior as a node set from the XML Document Object Model (DOM).</span></span> <span data-ttu-id="90c03-111">Bir düğüm kümesinde gezinme için, bir sonuç ağacı parçasının veya sonuç ağacı [](../../../../docs/standard/data/xml/node-set-navigation-using-xpathnavigator.md)parçasının aksine (örneğin, <xref:System.Xml.XPath.XPathNodeIterator> gezinti için) bir düğüm kümesi gezinmede gösterilen bir yöntem kümesini kullanarak gidebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="90c03-111">You can navigate a node set using a set of methods shown in [Node Set Navigation Using XPathNavigator](../../../../docs/standard/data/xml/node-set-navigation-using-xpathnavigator.md), unlike a result tree fragment or result tree fragment, which uses the <xref:System.Xml.XPath.XPathNodeIterator> for navigation.</span></span>  
  
 <span data-ttu-id="90c03-112">Aşağıdaki kod örneği, bir stil sayfasındaki bir `variable` veya `parameter` öğesinin bir düğüm kümesini değerlendirirken bir düğüm kümesi üzerinde nasıl yineleceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="90c03-112">The following code sample shows how to iterate over a node set when a `variable` or `parameter` element in a style sheet evaluates to a node set.</span></span>  
  
## <a name="style-sheet"></a><span data-ttu-id="90c03-113">Stil sayfası</span><span class="sxs-lookup"><span data-stu-id="90c03-113">Style Sheet</span></span>  
  
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
  
## <a name="input"></a><span data-ttu-id="90c03-114">Giriş</span><span class="sxs-lookup"><span data-stu-id="90c03-114">Input</span></span>  
  
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
  
## <a name="output"></a><span data-ttu-id="90c03-115">Çıkış</span><span class="sxs-lookup"><span data-stu-id="90c03-115">Output</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="90c03-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="90c03-116">See also</span></span>

- <xref:System.Xml.XPath.XPathNodeIterator>
- [<span data-ttu-id="90c03-117">XslTransform Sınıfı ile XSLT Dönüşümleri</span><span class="sxs-lookup"><span data-stu-id="90c03-117">XSLT Transformations with the XslTransform Class</span></span>](../../../../docs/standard/data/xml/xslt-transformations-with-the-xsltransform-class.md)
- [<span data-ttu-id="90c03-118">XslTransform Sınıfı XSLT İşlemcisini Uygular</span><span class="sxs-lookup"><span data-stu-id="90c03-118">XslTransform Class Implements the XSLT Processor</span></span>](../../../../docs/standard/data/xml/xsltransform-class-implements-the-xslt-processor.md)
