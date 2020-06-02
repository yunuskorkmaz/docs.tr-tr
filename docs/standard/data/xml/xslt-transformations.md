---
title: XSLT Dönüşümleri
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 202f8820-224c-494f-b61e-cd127eac6e03
ms.openlocfilehash: 92d0af1519260d458d3954beaef38e698142367a
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84288309"
---
# <a name="xslt-transformations"></a><span data-ttu-id="fd488-102">XSLT Dönüşümleri</span><span class="sxs-lookup"><span data-stu-id="fd488-102">XSLT Transformations</span></span>
<span data-ttu-id="fd488-103">Genişletilebilir Stil sayfası dil dönüşümü (XSLT), kaynak XML belgesinin içeriğini biçim veya yapıda farklı başka bir belgeye dönüştürmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="fd488-103">The Extensible Stylesheet Language Transformation (XSLT) lets you transform the content of a source XML document into another document that is different in format or structure.</span></span> <span data-ttu-id="fd488-104">Örneğin, XSLT 'yi bir Web sitesinde kullanılmak üzere HTML 'ye dönüştürmek veya yalnızca bir uygulamanın gerektirdiği alanları içeren bir belgeye dönüştürmek için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fd488-104">For example, you can use XSLT to transform XML into HTML for use on a Web site or to transform it into a document that contains only the fields required by an application.</span></span> <span data-ttu-id="fd488-105">Bu dönüştürme işlemi [W3C XSL dönüştürmeleri (XSLT) sürüm 1,0 önerisi](https://www.w3.org/TR/xslt-10/)tarafından belirtilir.</span><span class="sxs-lookup"><span data-stu-id="fd488-105">This transformation process is specified by the [W3C XSL Transformations (XSLT) Version 1.0 recommendation](https://www.w3.org/TR/xslt-10/).</span></span>  
  
 <span data-ttu-id="fd488-106"><xref:System.Xml.Xsl.XslCompiledTransform>Sınıfı, .net 'TEKI XSLT işlemcisidir.</span><span class="sxs-lookup"><span data-stu-id="fd488-106">The <xref:System.Xml.Xsl.XslCompiledTransform> class is the XSLT processor in .NET.</span></span> <span data-ttu-id="fd488-107"><xref:System.Xml.Xsl.XslCompiledTransform>Sınıfı, [W3C XSLT 1,0 önerisini](https://www.w3.org/TR/xslt-10/)destekler.</span><span class="sxs-lookup"><span data-stu-id="fd488-107">The <xref:System.Xml.Xsl.XslCompiledTransform> class supports the [W3C XSLT 1.0 recommendation](https://www.w3.org/TR/xslt-10/).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="fd488-108"><xref:System.Xml.Xsl.XslTransform>Sınıf, .NET Framework sürüm 2,0 ' de kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="fd488-108">The <xref:System.Xml.Xsl.XslTransform> class is obsolete in .NET Framework version 2.0.</span></span> <span data-ttu-id="fd488-109"><xref:System.Xml.Xsl.XslCompiledTransform>Sınıfı, XSLT altyapısının yeni bir uygulamasıdır.</span><span class="sxs-lookup"><span data-stu-id="fd488-109">The <xref:System.Xml.Xsl.XslCompiledTransform> class is a new implementation of the XSLT engine.</span></span> <span data-ttu-id="fd488-110">Performans iyileştirmeleri ve yeni güvenlik özellikleri içerir.</span><span class="sxs-lookup"><span data-stu-id="fd488-110">It includes performance improvements and new security features.</span></span> <span data-ttu-id="fd488-111">Önerilen uygulama, sınıfını kullanarak XSLT uygulamaları oluşturmaktır <xref:System.Xml.Xsl.XslCompiledTransform> .</span><span class="sxs-lookup"><span data-stu-id="fd488-111">The recommended practice is to create XSLT applications using the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="fd488-112">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="fd488-112">In This Section</span></span>  
 [<span data-ttu-id="fd488-113">XslCompiledTransform Sınıfını Kullanma</span><span class="sxs-lookup"><span data-stu-id="fd488-113">Using the XslCompiledTransform Class</span></span>](using-the-xslcompiledtransform-class.md)  
 <span data-ttu-id="fd488-114">Sınıfını kullanma hakkında bilgi sağlar <xref:System.Xml.Xsl.XslCompiledTransform> .</span><span class="sxs-lookup"><span data-stu-id="fd488-114">Provides information on using the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span>  
  
 [<span data-ttu-id="fd488-115">XslTransform Sınıfından Geçirme</span><span class="sxs-lookup"><span data-stu-id="fd488-115">Migrating From the XslTransform Class</span></span>](migrating-from-the-xsltransform-class.md)  
 <span data-ttu-id="fd488-116">Sınıfından kodun nasıl geçirileceği açıklanır <xref:System.Xml.Xsl.XslTransform> .</span><span class="sxs-lookup"><span data-stu-id="fd488-116">Discusses how to migrate code from the <xref:System.Xml.Xsl.XslTransform> class.</span></span>  
  
 [<span data-ttu-id="fd488-117">XSLT Derleyicisi (xsltc.exe)</span><span class="sxs-lookup"><span data-stu-id="fd488-117">XSLT Compiler (xsltc.exe)</span></span>](xslt-compiler-xsltc-exe.md)  
 <span data-ttu-id="fd488-118">XSLT derleyicisini kullanma hakkında bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="fd488-118">Provides information on using the XSLT compiler.</span></span>  
  
 [<span data-ttu-id="fd488-119">XslTransform Sınıfı ile XSLT Dönüşümleri</span><span class="sxs-lookup"><span data-stu-id="fd488-119">XSLT Transformations with the XslTransform Class</span></span>](xslt-transformations-with-the-xsltransform-class.md)  
 <span data-ttu-id="fd488-120">Sınıfını kullanma hakkında bilgi sağlar <xref:System.Xml.Xsl.XslTransform> .</span><span class="sxs-lookup"><span data-stu-id="fd488-120">Provides information on using the <xref:System.Xml.Xsl.XslTransform> class.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="fd488-121">Başvuru</span><span class="sxs-lookup"><span data-stu-id="fd488-121">Reference</span></span>  
 <xref:System.Xml.Xsl.XslCompiledTransform>  
 <xref:System.Xml.Xsl.XsltArgumentList>  
 <xref:System.Xml.Xsl.XsltSettings>  
  
## <a name="related-sections"></a><span data-ttu-id="fd488-122">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="fd488-122">Related Sections</span></span>  
 [<span data-ttu-id="fd488-123">XML belgeleri ve verileri</span><span class="sxs-lookup"><span data-stu-id="fd488-123">XML Documents and Data</span></span>](index.md)
