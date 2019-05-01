---
title: XSLT Dönüşümleri
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 202f8820-224c-494f-b61e-cd127eac6e03
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 922de11567af9409265ee18bfa6a2637951c57c1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62026592"
---
# <a name="xslt-transformations"></a><span data-ttu-id="a2003-102">XSLT Dönüşümleri</span><span class="sxs-lookup"><span data-stu-id="a2003-102">XSLT Transformations</span></span>
<span data-ttu-id="a2003-103">Genişletilebilir Stil Sayfası Dil Dönüşümü (XSLT) kaynak XML belgesinin içeriğini başka bir belgeye biçimi veya yapıda farklı dönüştürme sağlar.</span><span class="sxs-lookup"><span data-stu-id="a2003-103">The Extensible Stylesheet Language Transformation (XSLT) lets you transform the content of a source XML document into another document that is different in format or structure.</span></span> <span data-ttu-id="a2003-104">Örneğin, bir Web sitesinde kullanılmak HTML'e XML dönüştürmek için veya yalnızca bir uygulama tarafından gerekli alanları içeren bir belgeyi dönüştürmek için XSLT kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a2003-104">For example, you can use XSLT to transform XML into HTML for use on a Web site or to transform it into a document that contains only the fields required by an application.</span></span> <span data-ttu-id="a2003-105">Bu dönüştürme işlemi tarafından belirtilen [W3C XSLT Dönüşümleri (XSLT) sürüm 1.0 öneri](https://www.w3.org/TR/xslt-10/).</span><span class="sxs-lookup"><span data-stu-id="a2003-105">This transformation process is specified by the [W3C XSL Transformations (XSLT) Version 1.0 recommendation](https://www.w3.org/TR/xslt-10/).</span></span>  
  
 <span data-ttu-id="a2003-106"><xref:System.Xml.Xsl.XslCompiledTransform> .NET içinde XSLT işlemci bir sınıftır.</span><span class="sxs-lookup"><span data-stu-id="a2003-106">The <xref:System.Xml.Xsl.XslCompiledTransform> class is the XSLT processor in .NET.</span></span> <span data-ttu-id="a2003-107"><xref:System.Xml.Xsl.XslCompiledTransform> Sınıfı destekler [W3C XSLT 1.0 öneri](https://www.w3.org/TR/xslt-10/).</span><span class="sxs-lookup"><span data-stu-id="a2003-107">The <xref:System.Xml.Xsl.XslCompiledTransform> class supports the [W3C XSLT 1.0 recommendation](https://www.w3.org/TR/xslt-10/).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a2003-108"><xref:System.Xml.Xsl.XslTransform> Sınıfı .NET Framework 2.0 sürümünde kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="a2003-108">The <xref:System.Xml.Xsl.XslTransform> class is obsolete in .NET Framework version 2.0.</span></span> <span data-ttu-id="a2003-109"><xref:System.Xml.Xsl.XslCompiledTransform> XSLT Altyapısı'nın yeni bir uygulama bir sınıftır.</span><span class="sxs-lookup"><span data-stu-id="a2003-109">The <xref:System.Xml.Xsl.XslCompiledTransform> class is a new implementation of the XSLT engine.</span></span> <span data-ttu-id="a2003-110">Bu performans geliştirmeleri ve yeni güvenlik özellikleri içerir.</span><span class="sxs-lookup"><span data-stu-id="a2003-110">It includes performance improvements and new security features.</span></span> <span data-ttu-id="a2003-111">Kullanarak XSLT uygulamaları oluşturmak için önerilen yöntemdir <xref:System.Xml.Xsl.XslCompiledTransform> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="a2003-111">The recommended practice is to create XSLT applications using the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="a2003-112">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="a2003-112">In This Section</span></span>  
 [<span data-ttu-id="a2003-113">XslCompiledTransform Sınıfını Kullanma</span><span class="sxs-lookup"><span data-stu-id="a2003-113">Using the XslCompiledTransform Class</span></span>](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md)  
 <span data-ttu-id="a2003-114">Kullanma hakkında bilgi sağlar <xref:System.Xml.Xsl.XslCompiledTransform> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="a2003-114">Provides information on using the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span>  
  
 [<span data-ttu-id="a2003-115">XslTransform Sınıfından Geçirme</span><span class="sxs-lookup"><span data-stu-id="a2003-115">Migrating From the XslTransform Class</span></span>](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md)  
 <span data-ttu-id="a2003-116">Nasıl koddan geçirileceği anlatılmaktadır <xref:System.Xml.Xsl.XslTransform> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="a2003-116">Discusses how to migrate code from the <xref:System.Xml.Xsl.XslTransform> class.</span></span>  
  
 [<span data-ttu-id="a2003-117">XSLT Derleyicisi (xsltc.exe)</span><span class="sxs-lookup"><span data-stu-id="a2003-117">XSLT Compiler (xsltc.exe)</span></span>](../../../../docs/standard/data/xml/xslt-compiler-xsltc-exe.md)  
 <span data-ttu-id="a2003-118">XSLT derleyicisi kullanma hakkında bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="a2003-118">Provides information on using the XSLT compiler.</span></span>  
  
 [<span data-ttu-id="a2003-119">XslTransform Sınıfı ile XSLT Dönüşümleri</span><span class="sxs-lookup"><span data-stu-id="a2003-119">XSLT Transformations with the XslTransform Class</span></span>](../../../../docs/standard/data/xml/xslt-transformations-with-the-xsltransform-class.md)  
 <span data-ttu-id="a2003-120">Kullanma hakkında bilgi sağlar <xref:System.Xml.Xsl.XslTransform> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="a2003-120">Provides information on using the <xref:System.Xml.Xsl.XslTransform> class.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="a2003-121">Başvuru</span><span class="sxs-lookup"><span data-stu-id="a2003-121">Reference</span></span>  
 <xref:System.Xml.Xsl.XslCompiledTransform>  
 <xref:System.Xml.Xsl.XsltArgumentList>  
 <xref:System.Xml.Xsl.XsltSettings>  
  
## <a name="related-sections"></a><span data-ttu-id="a2003-122">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="a2003-122">Related Sections</span></span>  
 [<span data-ttu-id="a2003-123">XML Belgeleri ve Verileri</span><span class="sxs-lookup"><span data-stu-id="a2003-123">XML Documents and Data</span></span>](../../../../docs/standard/data/xml/index.md)
