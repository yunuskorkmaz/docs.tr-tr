---
title: Dönüşümlerdeki düğüm kümeleri
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: ad034f0e-ff8b-4a71-9a4c-528c754263c4
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f33320603b175f04d0372fd5f2a2ee16d286d7b3
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43866825"
---
# <a name="node-sets-in-transformations"></a><span data-ttu-id="97752-102">Dönüşümlerdeki düğüm kümeleri</span><span class="sxs-lookup"><span data-stu-id="97752-102">Node Sets in Transformations</span></span>
<span data-ttu-id="97752-103">Düğüm kümeleri XML Path Language (XPath) ifade döndürülen dört temel veri türlerinden biridir.</span><span class="sxs-lookup"><span data-stu-id="97752-103">Node sets are one of four basic data types that are returned from XML Path Language (XPath) expressions.</span></span> <span data-ttu-id="97752-104">Belge sırada oluşturulan yinelemeleri olmadan düğümler sırasız koleksiyonunun ise, bir stil sayfası bir değişkene atanabilir bir düğüm kümesi.</span><span class="sxs-lookup"><span data-stu-id="97752-104">A node set, which is an unordered collection of nodes without duplicates, created in document order, can be assigned to a variable in a style sheet.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="97752-105"><xref:System.Xml.Xsl.XslTransform> Sınıftır eski [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)].</span><span class="sxs-lookup"><span data-stu-id="97752-105">The <xref:System.Xml.Xsl.XslTransform> class is obsolete in the [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)].</span></span> <span data-ttu-id="97752-106">Genişletilebilir Stil Sayfası Dil Dönüşümleri (XSLT) dönüştürmeleri için kullanarak gerçekleştirebileceğiniz <xref:System.Xml.Xsl.XslCompiledTransform> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="97752-106">You can perform Extensible Stylesheet Language for Transformations (XSLT) transformations using the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span> <span data-ttu-id="97752-107">Bkz: [XslCompiledTransform sınıfını kullanma](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) ve [geçirme gelen XslTransform sınıfı](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md) daha fazla bilgi için.</span><span class="sxs-lookup"><span data-stu-id="97752-107">See [Using the XslCompiledTransform Class](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) and [Migrating From the XslTransform Class](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md) for more information.</span></span>  
  
 <span data-ttu-id="97752-108">Düğüm kümeleri XPath ifadeleri döndürülen dört temel veri türlerinden biridir.</span><span class="sxs-lookup"><span data-stu-id="97752-108">Node sets are one of four basic data types that are returned from XPath expressions.</span></span> <span data-ttu-id="97752-109">Belge sırada oluşturulan yinelemeleri olmadan düğümler sırasız koleksiyonunun ise, bir stil sayfası bir değişkene atanabilir bir düğüm kümesi.</span><span class="sxs-lookup"><span data-stu-id="97752-109">A node set, which is an unordered collection of nodes without duplicates, created in document order, can be assigned to a variable in a style sheet.</span></span> <span data-ttu-id="97752-110">Kullanılan ifade bir XPath bir sonuç bu düğüm kümesi bir `select` Dönüşümde öznitelik, XML belge nesne modeli (DOM) öğesinden ayarlanmış bir düğüm aynı davranışı sahiptir.</span><span class="sxs-lookup"><span data-stu-id="97752-110">This node set, which is a result of an XPath expression used in a `select` attribute in a transformation, has the same behavior as a node set from the XML Document Object Model (DOM).</span></span> <span data-ttu-id="97752-111">Düğüm kümesi bir dizi yöntem gösterilen kullanarak gidebilirsiniz [kullanarak düğüm kümesi Gezinti XPathNavigator](../../../../docs/standard/data/xml/node-set-navigation-using-xpathnavigator.md), farklı bir sonuç ağacı parçası veya kullanan sonuç ağacı parçası olarak <xref:System.Xml.XPath.XPathNodeIterator> gezinme için.</span><span class="sxs-lookup"><span data-stu-id="97752-111">You can navigate a node set using a set of methods shown in [Node Set Navigation Using XPathNavigator](../../../../docs/standard/data/xml/node-set-navigation-using-xpathnavigator.md), unlike a result tree fragment or result tree fragment, which uses the <xref:System.Xml.XPath.XPathNodeIterator> for navigation.</span></span>  
  
 <span data-ttu-id="97752-112">Aşağıdaki kod örneği nasıl yineleneceğini gösterir. bir düğüm kümesi üzerinde bir `variable` veya `parameter` bir stil sayfası öğesinde bir düğüm kümesi olarak değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="97752-112">The following code sample shows how to iterate over a node set when a `variable` or `parameter` element in a style sheet evaluates to a node set.</span></span>  
  
## <a name="style-sheet"></a><span data-ttu-id="97752-113">Stil sayfası</span><span class="sxs-lookup"><span data-stu-id="97752-113">Style Sheet</span></span>  
  
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
  
## <a name="input"></a><span data-ttu-id="97752-114">Giriş</span><span class="sxs-lookup"><span data-stu-id="97752-114">Input</span></span>  
  
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
  
## <a name="output"></a><span data-ttu-id="97752-115">Çıkış</span><span class="sxs-lookup"><span data-stu-id="97752-115">Output</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="97752-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="97752-116">See also</span></span>

- <xref:System.Xml.XPath.XPathNodeIterator>  
- [<span data-ttu-id="97752-117">XslTransform Sınıfı ile XSLT Dönüşümleri</span><span class="sxs-lookup"><span data-stu-id="97752-117">XSLT Transformations with the XslTransform Class</span></span>](../../../../docs/standard/data/xml/xslt-transformations-with-the-xsltransform-class.md)  
- [<span data-ttu-id="97752-118">XslTransform Sınıfı XSLT İşlemcisini Uygular</span><span class="sxs-lookup"><span data-stu-id="97752-118">XslTransform Class Implements the XSLT Processor</span></span>](../../../../docs/standard/data/xml/xsltransform-class-implements-the-xslt-processor.md)
