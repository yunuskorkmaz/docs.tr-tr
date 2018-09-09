---
title: ': Node-set() işlevi desteği'
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: d0cbf517-d9f6-4097-9851-4fa62903decd
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d4b1fb4abe8ca0ba7afcefe996de59ceaf67a249
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/09/2018
ms.locfileid: "44252785"
---
# <a name="support-for-the-msxslnode-set-function"></a><span data-ttu-id="216f5-102">: Node-set() işlevi desteği</span><span class="sxs-lookup"><span data-stu-id="216f5-102">Support for the msxsl:node-set() Function</span></span>
<span data-ttu-id="216f5-103">`msxsl:node-set` İşlevi bir sonuç ağacı parçası düğümünü kümeyi dönüştürmek sağlar.</span><span class="sxs-lookup"><span data-stu-id="216f5-103">The `msxsl:node-set` function enables you to convert a result tree fragment into a node set.</span></span> <span data-ttu-id="216f5-104">Sonuç olarak oluşan düğüm her zaman tek bir düğüm içeriyor ve ağaç kök düğümü.</span><span class="sxs-lookup"><span data-stu-id="216f5-104">The resulting node set always contains a single node and is the root node of the tree.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="216f5-105"><xref:System.Xml.Xsl.XslTransform> Sınıftır eski [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)].</span><span class="sxs-lookup"><span data-stu-id="216f5-105">The <xref:System.Xml.Xsl.XslTransform> class is obsolete in the [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)].</span></span> <span data-ttu-id="216f5-106">Genişletilebilir Stil Sayfası Dil Dönüşümleri (XSLT) dönüştürmeleri için kullanarak gerçekleştirebileceğiniz <xref:System.Xml.Xsl.XslCompiledTransform> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="216f5-106">You can perform Extensible Stylesheet Language for Transformations (XSLT) transformations using the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span> <span data-ttu-id="216f5-107">Bkz: [XslCompiledTransform sınıfını kullanma](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) ve [geçirme gelen XslTransform sınıfı](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md) daha fazla bilgi için.</span><span class="sxs-lookup"><span data-stu-id="216f5-107">See [Using the XslCompiledTransform Class](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) and [Migrating From the XslTransform Class](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md) for more information.</span></span>  
  
 <span data-ttu-id="216f5-108">`msxsl:node-set` İşlevi bir sonuç ağacı parçası düğümünü kümeyi dönüştürmek sağlar.</span><span class="sxs-lookup"><span data-stu-id="216f5-108">The `msxsl:node-set` function enables you to convert a result tree fragment into a node set.</span></span> <span data-ttu-id="216f5-109">Sonuç olarak oluşan düğüm her zaman tek bir düğüm içeriyor ve ağaç kök düğümü.</span><span class="sxs-lookup"><span data-stu-id="216f5-109">The resulting node set always contains a single node and is the root node of the tree.</span></span>  
  
## <a name="example"></a><span data-ttu-id="216f5-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="216f5-110">Example</span></span>  
 <span data-ttu-id="216f5-111">Aşağıdaki örnekte, `$var` stil sayfası düğümü ağacında bir değişkendir.</span><span class="sxs-lookup"><span data-stu-id="216f5-111">In the following example, `$var` is a variable that is a node tree in the style sheet.</span></span> <span data-ttu-id="216f5-112">For-each ifadesinin birlikte `node-set` işlevi bu düğüm ağacı bir düğüm kümesi olarak gezinilen kullanıcının sağlar.</span><span class="sxs-lookup"><span data-stu-id="216f5-112">The for-each statement combined with the `node-set` function allows the user to iterate over this node tree as a node set.</span></span>  
  
## <a name="nodesetxsl"></a><span data-ttu-id="216f5-113">NodeSet.xsl</span><span class="sxs-lookup"><span data-stu-id="216f5-113">nodeset.xsl</span></span>  
  
```xml  
<xsl:stylesheet xmlns:xsl="http://www.w3.org/1999/XSL/Transform"  
                xmlns:msxsl="urn:schemas-microsoft-com:xslt"  
                xmlns:user="http://www.contoso.com"  
                version="1.0">  
    <xsl:variable name="books">  
        <book author="Michael Howard">Writing Secure Code</book>  
        <book author="Michael Kay">XSLT Reference</book>  
    </xsl:variable>  
  
    <xsl:template match="/">  
        <authors>  
            <xsl:for-each select="msxsl:node-set($books)/book">   
                <author><xsl:value-of select="@author"/)</author>  
            </xsl:for-each>  
        </authors>  
    </xsl:template>  
</xsl:stylesheet>  
```  
  
## <a name="output"></a><span data-ttu-id="216f5-114">Çıkış</span><span class="sxs-lookup"><span data-stu-id="216f5-114">Output</span></span>  
 <span data-ttu-id="216f5-115">Dönüşümün çıkış</span><span class="sxs-lookup"><span data-stu-id="216f5-115">The output of the transformation is</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<authors><author>Michael Howard</author><author>Michael Kay</author></authors>  
```  
  
## <a name="see-also"></a><span data-ttu-id="216f5-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="216f5-116">See also</span></span>

- [<span data-ttu-id="216f5-117">XslTransform Sınıfı XSLT İşlemcisini Uygular</span><span class="sxs-lookup"><span data-stu-id="216f5-117">XslTransform Class Implements the XSLT Processor</span></span>](../../../../docs/standard/data/xml/xsltransform-class-implements-the-xslt-processor.md)
