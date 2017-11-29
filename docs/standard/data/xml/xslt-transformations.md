---
title: "XSLT dönüştürmeleri"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 202f8820-224c-494f-b61e-cd127eac6e03
caps.latest.revision: "4"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 0d7fa8492487daff68fd8ebaf4159dd537d13e51
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="xslt-transformations"></a><span data-ttu-id="ea55c-102">XSLT dönüştürmeleri</span><span class="sxs-lookup"><span data-stu-id="ea55c-102">XSLT Transformations</span></span>
<span data-ttu-id="ea55c-103">Genişletilebilir Stil Sayfası Dil Dönüşümü (XSLT), bir kaynak XML belgesinin içeriğini veya yapısını biçiminde farklı başka bir belge dönüştürmek olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="ea55c-103">The Extensible Stylesheet Language Transformation (XSLT) lets you transform the content of a source XML document into another document that is different in format or structure.</span></span> <span data-ttu-id="ea55c-104">Örneğin, bir Web sitesinde kullanılmak üzere XML HTML'e dönüştürmek için veya yalnızca bir uygulama tarafından gerekli alanları içeren bir belgeyi dönüştürmek için XSLT kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ea55c-104">For example, you can use XSLT to transform XML into HTML for use on a Web site or to transform it into a document that contains only the fields required by an application.</span></span> <span data-ttu-id="ea55c-105">Bu dönüştürme süreci tarafından belirtilen [W3C XSL Dönüşümleri (XSLT) sürüm 1.0 öneri](http://go.microsoft.com/fwlink/?LinkID=49919).</span><span class="sxs-lookup"><span data-stu-id="ea55c-105">This transformation process is specified by the [W3C XSL Transformations (XSLT) Version 1.0 recommendation](http://go.microsoft.com/fwlink/?LinkID=49919).</span></span>  
  
 <span data-ttu-id="ea55c-106"><xref:System.Xml.Xsl.XslCompiledTransform> .NET Framework XSLT işlemcide bir sınıftır.</span><span class="sxs-lookup"><span data-stu-id="ea55c-106">The <xref:System.Xml.Xsl.XslCompiledTransform> class is the XSLT processor in the .NET Framework.</span></span> <span data-ttu-id="ea55c-107"><xref:System.Xml.Xsl.XslCompiledTransform> Sınıfı, W3C XSLT 1.0 öneri destekler.</span><span class="sxs-lookup"><span data-stu-id="ea55c-107">The <xref:System.Xml.Xsl.XslCompiledTransform> class supports the W3C XSLT 1.0 recommendation.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ea55c-108"><xref:System.Xml.Xsl.XslTransform> Sınıf .NET Framework sürüm 2.0 kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="ea55c-108">The <xref:System.Xml.Xsl.XslTransform> class is obsolete in .NET Framework version 2.0.</span></span> <span data-ttu-id="ea55c-109"><xref:System.Xml.Xsl.XslCompiledTransform> XSLT Altyapısı'nın yeni bir uygulama bir sınıftır.</span><span class="sxs-lookup"><span data-stu-id="ea55c-109">The <xref:System.Xml.Xsl.XslCompiledTransform> class is a new implementation of the XSLT engine.</span></span> <span data-ttu-id="ea55c-110">Performans iyileştirmeleri ve yeni güvenlik özelliklerini içerir.</span><span class="sxs-lookup"><span data-stu-id="ea55c-110">It includes performance improvements and new security features.</span></span> <span data-ttu-id="ea55c-111">Kullanarak XSLT uygulamaları oluşturmak için önerilen yöntemdir <xref:System.Xml.Xsl.XslCompiledTransform> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="ea55c-111">The recommended practice is to create XSLT applications using the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="ea55c-112">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="ea55c-112">In This Section</span></span>  
 [<span data-ttu-id="ea55c-113">XslCompiledTransform sınıfını kullanma</span><span class="sxs-lookup"><span data-stu-id="ea55c-113">Using the XslCompiledTransform Class</span></span>](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md)  
 <span data-ttu-id="ea55c-114">Hakkında bilgi verir <xref:System.Xml.Xsl.XslCompiledTransform> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="ea55c-114">Provides information on using the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span>  
  
 [<span data-ttu-id="ea55c-115">Çok sınıftan geçirme</span><span class="sxs-lookup"><span data-stu-id="ea55c-115">Migrating From the XslTransform Class</span></span>](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md)  
 <span data-ttu-id="ea55c-116">Koddan geçirmek nasıl ele <xref:System.Xml.Xsl.XslTransform> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="ea55c-116">Discusses how to migrate code from the <xref:System.Xml.Xsl.XslTransform> class.</span></span>  
  
 [<span data-ttu-id="ea55c-117">XSLT derleyici (xsltc.exe)</span><span class="sxs-lookup"><span data-stu-id="ea55c-117">XSLT Compiler (xsltc.exe)</span></span>](../../../../docs/standard/data/xml/xslt-compiler-xsltc-exe.md)  
 <span data-ttu-id="ea55c-118">XSLT derleyici hakkında bilgi verir.</span><span class="sxs-lookup"><span data-stu-id="ea55c-118">Provides information on using the XSLT compiler.</span></span>  
  
 [<span data-ttu-id="ea55c-119">Çok sınıfı ile XSLT dönüştürmeler</span><span class="sxs-lookup"><span data-stu-id="ea55c-119">XSLT Transformations with the XslTransform Class</span></span>](../../../../docs/standard/data/xml/xslt-transformations-with-the-xsltransform-class.md)  
 <span data-ttu-id="ea55c-120">Hakkında bilgi verir <xref:System.Xml.Xsl.XslTransform> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="ea55c-120">Provides information on using the <xref:System.Xml.Xsl.XslTransform> class.</span></span>  
  
 <span data-ttu-id="ea55c-121">**Not** <xref:System.Xml.Xsl.XslTransform> sınıfı .NET Framework 2.0 sürümünde kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="ea55c-121">**Note** The <xref:System.Xml.Xsl.XslTransform> class is obsolete in the .NET Framework 2.0 release.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="ea55c-122">Başvuru</span><span class="sxs-lookup"><span data-stu-id="ea55c-122">Reference</span></span>  
 <xref:System.Xml.Xsl.XslCompiledTransform>  
  
 <xref:System.Xml.Xsl.XsltArgumentList>  
  
 <xref:System.Xml.Xsl.XsltSettings>  
  
## <a name="related-sections"></a><span data-ttu-id="ea55c-123">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="ea55c-123">Related Sections</span></span>  
 [<span data-ttu-id="ea55c-124">XML belgeleri ve verileri</span><span class="sxs-lookup"><span data-stu-id="ea55c-124">XML Documents and Data</span></span>](../../../../docs/standard/data/xml/index.md)
