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
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 92d0688b86e6a95af46e09c21c1a8b3cdf66efc3
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="xslt-transformations"></a><span data-ttu-id="927ab-102">XSLT dönüştürmeleri</span><span class="sxs-lookup"><span data-stu-id="927ab-102">XSLT Transformations</span></span>
<span data-ttu-id="927ab-103">Genişletilebilir Stil Sayfası Dil Dönüşümü (XSLT), bir kaynak XML belgesinin içeriğini veya yapısını biçiminde farklı başka bir belge dönüştürmek olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="927ab-103">The Extensible Stylesheet Language Transformation (XSLT) lets you transform the content of a source XML document into another document that is different in format or structure.</span></span> <span data-ttu-id="927ab-104">Örneğin, bir Web sitesinde kullanılmak üzere XML HTML'e dönüştürmek için veya yalnızca bir uygulama tarafından gerekli alanları içeren bir belgeyi dönüştürmek için XSLT kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="927ab-104">For example, you can use XSLT to transform XML into HTML for use on a Web site or to transform it into a document that contains only the fields required by an application.</span></span> <span data-ttu-id="927ab-105">Bu dönüştürme süreci tarafından belirtilen [W3C XSL Dönüşümleri (XSLT) sürüm 1.0 öneri](http://go.microsoft.com/fwlink/?LinkID=49919).</span><span class="sxs-lookup"><span data-stu-id="927ab-105">This transformation process is specified by the [W3C XSL Transformations (XSLT) Version 1.0 recommendation](http://go.microsoft.com/fwlink/?LinkID=49919).</span></span>  
  
 <span data-ttu-id="927ab-106"><xref:System.Xml.Xsl.XslCompiledTransform> .NET Framework XSLT işlemcide bir sınıftır.</span><span class="sxs-lookup"><span data-stu-id="927ab-106">The <xref:System.Xml.Xsl.XslCompiledTransform> class is the XSLT processor in the .NET Framework.</span></span> <span data-ttu-id="927ab-107"><xref:System.Xml.Xsl.XslCompiledTransform> Sınıfı, W3C XSLT 1.0 öneri destekler.</span><span class="sxs-lookup"><span data-stu-id="927ab-107">The <xref:System.Xml.Xsl.XslCompiledTransform> class supports the W3C XSLT 1.0 recommendation.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="927ab-108"><xref:System.Xml.Xsl.XslTransform> Sınıf .NET Framework sürüm 2.0 kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="927ab-108">The <xref:System.Xml.Xsl.XslTransform> class is obsolete in .NET Framework version 2.0.</span></span> <span data-ttu-id="927ab-109"><xref:System.Xml.Xsl.XslCompiledTransform> XSLT Altyapısı'nın yeni bir uygulama bir sınıftır.</span><span class="sxs-lookup"><span data-stu-id="927ab-109">The <xref:System.Xml.Xsl.XslCompiledTransform> class is a new implementation of the XSLT engine.</span></span> <span data-ttu-id="927ab-110">Performans iyileştirmeleri ve yeni güvenlik özelliklerini içerir.</span><span class="sxs-lookup"><span data-stu-id="927ab-110">It includes performance improvements and new security features.</span></span> <span data-ttu-id="927ab-111">Kullanarak XSLT uygulamaları oluşturmak için önerilen yöntemdir <xref:System.Xml.Xsl.XslCompiledTransform> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="927ab-111">The recommended practice is to create XSLT applications using the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="927ab-112">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="927ab-112">In This Section</span></span>  
 [<span data-ttu-id="927ab-113">XslCompiledTransform Sınıfını Kullanma</span><span class="sxs-lookup"><span data-stu-id="927ab-113">Using the XslCompiledTransform Class</span></span>](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md)  
 <span data-ttu-id="927ab-114">Hakkında bilgi verir <xref:System.Xml.Xsl.XslCompiledTransform> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="927ab-114">Provides information on using the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span>  
  
 [<span data-ttu-id="927ab-115">XslTransform Sınıfından Geçirme</span><span class="sxs-lookup"><span data-stu-id="927ab-115">Migrating From the XslTransform Class</span></span>](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md)  
 <span data-ttu-id="927ab-116">Koddan geçirmek nasıl ele <xref:System.Xml.Xsl.XslTransform> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="927ab-116">Discusses how to migrate code from the <xref:System.Xml.Xsl.XslTransform> class.</span></span>  
  
 [<span data-ttu-id="927ab-117">XSLT Derleyicisi (xsltc.exe)</span><span class="sxs-lookup"><span data-stu-id="927ab-117">XSLT Compiler (xsltc.exe)</span></span>](../../../../docs/standard/data/xml/xslt-compiler-xsltc-exe.md)  
 <span data-ttu-id="927ab-118">XSLT derleyici hakkında bilgi verir.</span><span class="sxs-lookup"><span data-stu-id="927ab-118">Provides information on using the XSLT compiler.</span></span>  
  
 [<span data-ttu-id="927ab-119">XslTransform Sınıfı ile XSLT Dönüşümleri</span><span class="sxs-lookup"><span data-stu-id="927ab-119">XSLT Transformations with the XslTransform Class</span></span>](../../../../docs/standard/data/xml/xslt-transformations-with-the-xsltransform-class.md)  
 <span data-ttu-id="927ab-120">Hakkında bilgi verir <xref:System.Xml.Xsl.XslTransform> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="927ab-120">Provides information on using the <xref:System.Xml.Xsl.XslTransform> class.</span></span>  
  
 <span data-ttu-id="927ab-121">**Not** <xref:System.Xml.Xsl.XslTransform> sınıfı .NET Framework 2.0 sürümünde kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="927ab-121">**Note** The <xref:System.Xml.Xsl.XslTransform> class is obsolete in the .NET Framework 2.0 release.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="927ab-122">Başvuru</span><span class="sxs-lookup"><span data-stu-id="927ab-122">Reference</span></span>  
 <xref:System.Xml.Xsl.XslCompiledTransform>  
  
 <xref:System.Xml.Xsl.XsltArgumentList>  
  
 <xref:System.Xml.Xsl.XsltSettings>  
  
## <a name="related-sections"></a><span data-ttu-id="927ab-123">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="927ab-123">Related Sections</span></span>  
 [<span data-ttu-id="927ab-124">XML Belgeleri ve Verileri</span><span class="sxs-lookup"><span data-stu-id="927ab-124">XML Documents and Data</span></span>](../../../../docs/standard/data/xml/index.md)
