---
title: XSLT Dönüşümleri
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 202f8820-224c-494f-b61e-cd127eac6e03
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 93d45b58433dc3c7231cea741aa7ea67dfab2d7a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69912032"
---
# <a name="xslt-transformations"></a><span data-ttu-id="6d2a7-102">XSLT Dönüşümleri</span><span class="sxs-lookup"><span data-stu-id="6d2a7-102">XSLT Transformations</span></span>
<span data-ttu-id="6d2a7-103">Genişletilebilir Stil sayfası dil dönüşümü (XSLT), kaynak XML belgesinin içeriğini biçim veya yapıda farklı başka bir belgeye dönüştürmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="6d2a7-103">The Extensible Stylesheet Language Transformation (XSLT) lets you transform the content of a source XML document into another document that is different in format or structure.</span></span> <span data-ttu-id="6d2a7-104">Örneğin, XSLT 'yi bir Web sitesinde kullanılmak üzere HTML 'ye dönüştürmek veya yalnızca bir uygulamanın gerektirdiği alanları içeren bir belgeye dönüştürmek için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6d2a7-104">For example, you can use XSLT to transform XML into HTML for use on a Web site or to transform it into a document that contains only the fields required by an application.</span></span> <span data-ttu-id="6d2a7-105">Bu dönüştürme işlemi [W3C XSL dönüştürmeleri (XSLT) sürüm 1,0 önerisi](https://www.w3.org/TR/xslt-10/)tarafından belirtilir.</span><span class="sxs-lookup"><span data-stu-id="6d2a7-105">This transformation process is specified by the [W3C XSL Transformations (XSLT) Version 1.0 recommendation](https://www.w3.org/TR/xslt-10/).</span></span>  
  
 <span data-ttu-id="6d2a7-106"><xref:System.Xml.Xsl.XslCompiledTransform> Sınıfı, .net 'teki XSLT işlemcisidir.</span><span class="sxs-lookup"><span data-stu-id="6d2a7-106">The <xref:System.Xml.Xsl.XslCompiledTransform> class is the XSLT processor in .NET.</span></span> <span data-ttu-id="6d2a7-107">Sınıfı, [W3C XSLT 1,0 önerisini](https://www.w3.org/TR/xslt-10/)destekler. <xref:System.Xml.Xsl.XslCompiledTransform></span><span class="sxs-lookup"><span data-stu-id="6d2a7-107">The <xref:System.Xml.Xsl.XslCompiledTransform> class supports the [W3C XSLT 1.0 recommendation](https://www.w3.org/TR/xslt-10/).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6d2a7-108">Sınıf <xref:System.Xml.Xsl.XslTransform> , .NET Framework sürüm 2,0 ' de kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="6d2a7-108">The <xref:System.Xml.Xsl.XslTransform> class is obsolete in .NET Framework version 2.0.</span></span> <span data-ttu-id="6d2a7-109"><xref:System.Xml.Xsl.XslCompiledTransform> Sınıfı, XSLT altyapısının yeni bir uygulamasıdır.</span><span class="sxs-lookup"><span data-stu-id="6d2a7-109">The <xref:System.Xml.Xsl.XslCompiledTransform> class is a new implementation of the XSLT engine.</span></span> <span data-ttu-id="6d2a7-110">Performans iyileştirmeleri ve yeni güvenlik özellikleri içerir.</span><span class="sxs-lookup"><span data-stu-id="6d2a7-110">It includes performance improvements and new security features.</span></span> <span data-ttu-id="6d2a7-111">Önerilen uygulama, <xref:System.Xml.Xsl.XslCompiledTransform> sınıfını kullanarak XSLT uygulamaları oluşturmaktır.</span><span class="sxs-lookup"><span data-stu-id="6d2a7-111">The recommended practice is to create XSLT applications using the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="6d2a7-112">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="6d2a7-112">In This Section</span></span>  
 [<span data-ttu-id="6d2a7-113">XslCompiledTransform Sınıfını Kullanma</span><span class="sxs-lookup"><span data-stu-id="6d2a7-113">Using the XslCompiledTransform Class</span></span>](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md)  
 <span data-ttu-id="6d2a7-114"><xref:System.Xml.Xsl.XslCompiledTransform> Sınıfını kullanma hakkında bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="6d2a7-114">Provides information on using the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span>  
  
 [<span data-ttu-id="6d2a7-115">XslTransform Sınıfından Geçirme</span><span class="sxs-lookup"><span data-stu-id="6d2a7-115">Migrating From the XslTransform Class</span></span>](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md)  
 <span data-ttu-id="6d2a7-116"><xref:System.Xml.Xsl.XslTransform> Sınıfından kodun nasıl geçirileceği açıklanır.</span><span class="sxs-lookup"><span data-stu-id="6d2a7-116">Discusses how to migrate code from the <xref:System.Xml.Xsl.XslTransform> class.</span></span>  
  
 [<span data-ttu-id="6d2a7-117">XSLT Derleyicisi (xsltc.exe)</span><span class="sxs-lookup"><span data-stu-id="6d2a7-117">XSLT Compiler (xsltc.exe)</span></span>](../../../../docs/standard/data/xml/xslt-compiler-xsltc-exe.md)  
 <span data-ttu-id="6d2a7-118">XSLT derleyicisini kullanma hakkında bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="6d2a7-118">Provides information on using the XSLT compiler.</span></span>  
  
 [<span data-ttu-id="6d2a7-119">XslTransform Sınıfı ile XSLT Dönüşümleri</span><span class="sxs-lookup"><span data-stu-id="6d2a7-119">XSLT Transformations with the XslTransform Class</span></span>](../../../../docs/standard/data/xml/xslt-transformations-with-the-xsltransform-class.md)  
 <span data-ttu-id="6d2a7-120"><xref:System.Xml.Xsl.XslTransform> Sınıfını kullanma hakkında bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="6d2a7-120">Provides information on using the <xref:System.Xml.Xsl.XslTransform> class.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="6d2a7-121">Başvuru</span><span class="sxs-lookup"><span data-stu-id="6d2a7-121">Reference</span></span>  
 <xref:System.Xml.Xsl.XslCompiledTransform>  
 <xref:System.Xml.Xsl.XsltArgumentList>  
 <xref:System.Xml.Xsl.XsltSettings>  
  
## <a name="related-sections"></a><span data-ttu-id="6d2a7-122">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="6d2a7-122">Related Sections</span></span>  
 [<span data-ttu-id="6d2a7-123">XML Belgeleri ve Verileri</span><span class="sxs-lookup"><span data-stu-id="6d2a7-123">XML Documents and Data</span></span>](../../../../docs/standard/data/xml/index.md)
