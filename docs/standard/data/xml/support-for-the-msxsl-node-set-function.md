---
title: msxsl:node-set() İşlevi Desteği
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: d0cbf517-d9f6-4097-9851-4fa62903decd
ms.openlocfilehash: 30652d8cbaac333cc1cb35954742b16dc7c4764b
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91071995"
---
# <a name="support-for-the-msxslnode-set-function"></a><span data-ttu-id="c49dc-102">msxsl:node-set() İşlevi Desteği</span><span class="sxs-lookup"><span data-stu-id="c49dc-102">Support for the msxsl:node-set() Function</span></span>
<span data-ttu-id="c49dc-103">`msxsl:node-set`İşlevi, bir sonuç ağacı parçasını bir düğüm kümesine dönüştürmenize olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="c49dc-103">The `msxsl:node-set` function enables you to convert a result tree fragment into a node set.</span></span> <span data-ttu-id="c49dc-104">Sonuçta elde edilen düğüm kümesi her zaman tek bir düğüm içerir ve ağacın kök düğümüdür.</span><span class="sxs-lookup"><span data-stu-id="c49dc-104">The resulting node set always contains a single node and is the root node of the tree.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c49dc-105"><xref:System.Xml.Xsl.XslTransform>Sınıf .NET Framework 2,0 ' de kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="c49dc-105">The <xref:System.Xml.Xsl.XslTransform> class is obsolete in the .NET Framework 2.0.</span></span> <span data-ttu-id="c49dc-106">Sınıfını kullanarak dönüşümler için Genişletilebilir Stil sayfası dili (XSLT) dönüşümleri gerçekleştirebilirsiniz <xref:System.Xml.Xsl.XslCompiledTransform> .</span><span class="sxs-lookup"><span data-stu-id="c49dc-106">You can perform Extensible Stylesheet Language for Transformations (XSLT) transformations using the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span> <span data-ttu-id="c49dc-107">Daha fazla bilgi için, bkz. [XslCompiledTransform sınıfını kullanma](using-the-xslcompiledtransform-class.md) ve [XslTransform sınıfından geçiş](migrating-from-the-xsltransform-class.md) .</span><span class="sxs-lookup"><span data-stu-id="c49dc-107">See [Using the XslCompiledTransform Class](using-the-xslcompiledtransform-class.md) and [Migrating From the XslTransform Class](migrating-from-the-xsltransform-class.md) for more information.</span></span>  
  
 <span data-ttu-id="c49dc-108">`msxsl:node-set`İşlevi, bir sonuç ağacı parçasını bir düğüm kümesine dönüştürmenize olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="c49dc-108">The `msxsl:node-set` function enables you to convert a result tree fragment into a node set.</span></span> <span data-ttu-id="c49dc-109">Sonuçta elde edilen düğüm kümesi her zaman tek bir düğüm içerir ve ağacın kök düğümüdür.</span><span class="sxs-lookup"><span data-stu-id="c49dc-109">The resulting node set always contains a single node and is the root node of the tree.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c49dc-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="c49dc-110">Example</span></span>  
 <span data-ttu-id="c49dc-111">Aşağıdaki örnekte, `$books` stil sayfasındaki düğüm ağacı olan bir değişkendir.</span><span class="sxs-lookup"><span data-stu-id="c49dc-111">In the following example, `$books` is a variable that is a node tree in the style sheet.</span></span> <span data-ttu-id="c49dc-112">İşleviyle birlikte bulunan for-each deyimleri, `node-set` kullanıcının bu düğüm ağacı üzerinde bir düğüm kümesi olarak yinemasına olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="c49dc-112">The for-each statement combined with the `node-set` function allows the user to iterate over this node tree as a node set.</span></span>  
  
## <a name="nodesetxsl"></a><span data-ttu-id="c49dc-113">nodeset. Xsl</span><span class="sxs-lookup"><span data-stu-id="c49dc-113">nodeset.xsl</span></span>  
  
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
                <author><xsl:value-of select="@author"/></author>  
            </xsl:for-each>  
        </authors>  
    </xsl:template>  
</xsl:stylesheet>  
```  
  
## <a name="output"></a><span data-ttu-id="c49dc-114">Çıkış</span><span class="sxs-lookup"><span data-stu-id="c49dc-114">Output</span></span>  
 <span data-ttu-id="c49dc-115">Dönüşümün çıktısı</span><span class="sxs-lookup"><span data-stu-id="c49dc-115">The output of the transformation is</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<authors><author>Michael Howard</author><author>Michael Kay</author></authors>  
```  
  
## <a name="see-also"></a><span data-ttu-id="c49dc-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c49dc-116">See also</span></span>

- [<span data-ttu-id="c49dc-117">XslTransform Sınıfı XSLT İşlemcisini Uygular</span><span class="sxs-lookup"><span data-stu-id="c49dc-117">XslTransform Class Implements the XSLT Processor</span></span>](xsltransform-class-implements-the-xslt-processor.md)
