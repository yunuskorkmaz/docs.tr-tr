---
title: XslCompiledTransform Sınıfını Kullanma
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: f9b074f6-d6f4-49dd-a093-df510bf0cf7b
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a524b80d8789567dc2aa943d7321fd49fe3c7c33
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69939419"
---
# <a name="using-the-xslcompiledtransform-class"></a><span data-ttu-id="e6a76-102">XslCompiledTransform Sınıfını Kullanma</span><span class="sxs-lookup"><span data-stu-id="e6a76-102">Using the XslCompiledTransform Class</span></span>
<span data-ttu-id="e6a76-103"><xref:System.Xml.Xsl.XslCompiledTransform> Sınıfı, Microsoft .NET Framework XSLT işlemcisidir.</span><span class="sxs-lookup"><span data-stu-id="e6a76-103">The <xref:System.Xml.Xsl.XslCompiledTransform> class is the Microsoft .NET Framework XSLT processor.</span></span> <span data-ttu-id="e6a76-104">Bu sınıf, stil sayfalarını derlemek ve XSLT dönüştürmelerini yürütmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="e6a76-104">This class is used to compile style sheets and execute XSLT transformations.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e6a76-105"><xref:System.Xml.Xsl.XslCompiledTransform> Sınıfının genel performansı <xref:System.Xml.Xsl.XslTransform> sınıfından daha iyi olsa da <xref:System.Xml.Xsl.XslCompiledTransform> , <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> sınıfının yöntemi ilk kez <xref:System.Xml.Xsl.XslTransform> sınıfın <xref:System.Xml.Xsl.XslTransform.Load%2A> yönteminden daha yavaş çalışabilir. bir dönüşümde çağrılır.</span><span class="sxs-lookup"><span data-stu-id="e6a76-105">Although the overall performance of the <xref:System.Xml.Xsl.XslCompiledTransform> class is better than the <xref:System.Xml.Xsl.XslTransform> class, the <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> method of the <xref:System.Xml.Xsl.XslCompiledTransform> class might perform more slowly than the <xref:System.Xml.Xsl.XslTransform.Load%2A> method of the <xref:System.Xml.Xsl.XslTransform> class the first time it is called on a transformation.</span></span> <span data-ttu-id="e6a76-106">Bunun nedeni XSLT dosyasının yüklenmeden önce derlenmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="e6a76-106">This is because the XSLT file must be compiled before it is loaded.</span></span> <span data-ttu-id="e6a76-107">Daha fazla bilgi için aşağıdaki blog gönderisine bakın: [XslCompiledTransform, XslTransform 'dan daha yavaş?](https://blogs.msdn.microsoft.com/antosha/2006/07/16/xslcompiledtransform-slower-than-xsltransform/)</span><span class="sxs-lookup"><span data-stu-id="e6a76-107">For more information, see the following blog post: [XslCompiledTransform Slower than XslTransform?](https://blogs.msdn.microsoft.com/antosha/2006/07/16/xslcompiledtransform-slower-than-xsltransform/)</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="e6a76-108">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="e6a76-108">In This Section</span></span>  
 [<span data-ttu-id="e6a76-109">XslCompiledTransform Sınıfına Girişler</span><span class="sxs-lookup"><span data-stu-id="e6a76-109">Inputs to the XslCompiledTransform Class</span></span>](../../../../docs/standard/data/xml/inputs-to-the-xslcompiledtransform-class.md)  
 <span data-ttu-id="e6a76-110">Kullanılabilir XSLT giriş seçeneklerini açıklar.</span><span class="sxs-lookup"><span data-stu-id="e6a76-110">Describes the available XSLT input options.</span></span>  
  
 [<span data-ttu-id="e6a76-111">XslCompiledTransform Sınıfındaki Çıkış Seçenekleri</span><span class="sxs-lookup"><span data-stu-id="e6a76-111">Output Options on the XslCompiledTransform Class</span></span>](../../../../docs/standard/data/xml/output-options-on-the-xslcompiledtransform-class.md)  
 <span data-ttu-id="e6a76-112">Kullanılabilir XSLT çıkış seçeneklerini açıklar.</span><span class="sxs-lookup"><span data-stu-id="e6a76-112">Describes the available XSLT output options.</span></span>  
  
 [<span data-ttu-id="e6a76-113">XSLT İşleme Sırasında Dış Kaynakları Çözümleme</span><span class="sxs-lookup"><span data-stu-id="e6a76-113">Resolving External Resources During XSLT Processing</span></span>](../../../../docs/standard/data/xml/resolving-external-resources-during-xslt-processing.md)  
 <span data-ttu-id="e6a76-114">Dış kaynakları çözümlemek <xref:System.Xml.XmlResolver> için sınıfının kullanımını açıklar.</span><span class="sxs-lookup"><span data-stu-id="e6a76-114">Discusses using the <xref:System.Xml.XmlResolver> class to resolve external resources.</span></span>  
  
 [<span data-ttu-id="e6a76-115">XSLT Stil Sayfalarını Genişletme</span><span class="sxs-lookup"><span data-stu-id="e6a76-115">Extending XSLT Style Sheets</span></span>](../../../../docs/standard/data/xml/extending-xslt-style-sheets.md)  
 <span data-ttu-id="e6a76-116">XSLT uzantılarının nasıl desteklendiğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="e6a76-116">Discusses how XSLT extensions are supported.</span></span>  
  
|||  
|-|-|  
|[<span data-ttu-id="e6a76-117">Kurtarılabilir XSLT Hataları</span><span class="sxs-lookup"><span data-stu-id="e6a76-117">Recoverable XSLT Errors</span></span>](../../../../docs/standard/data/xml/recoverable-xslt-errors.md)|<span data-ttu-id="e6a76-118">World Wide Web Konsorsiyumu (W3C) XSLT 1,0 önerisi tarafından izin verilen isteğe bağlı davranışları listeler ve bu davranışların <xref:System.Xml.Xsl.XslCompiledTransform> sınıf tarafından nasıl işlendiğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="e6a76-118">Lists discretionary behaviors allowed by the World Wide Web Consortium (W3C) XSLT 1.0 recommendation and describes how these behaviors are handled by the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span>|  
|[<span data-ttu-id="e6a76-119">Nasıl yapılır: Düğüm parçasını dönüştürme</span><span class="sxs-lookup"><span data-stu-id="e6a76-119">How to: Transform a Node Fragment</span></span>](../../../../docs/standard/data/xml/how-to-transform-a-node-fragment.md)|<span data-ttu-id="e6a76-120">Bir düğüm parçasının nasıl dönüştürüleceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="e6a76-120">Describes how to transform a node fragment.</span></span>|  
  
## <a name="related-sections"></a><span data-ttu-id="e6a76-121">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="e6a76-121">Related Sections</span></span>  
 [<span data-ttu-id="e6a76-122">XslTransform Sınıfından Geçirme</span><span class="sxs-lookup"><span data-stu-id="e6a76-122">Migrating From the XslTransform Class</span></span>](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md)  
 <span data-ttu-id="e6a76-123"><xref:System.Xml.Xsl.XslTransform> Sınıfından kodun nasıl geçirileceğiyle anlatılmaktadır</span><span class="sxs-lookup"><span data-stu-id="e6a76-123">Discusses how to migrate code from the <xref:System.Xml.Xsl.XslTransform> class</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e6a76-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e6a76-124">See also</span></span>

- <xref:System.Xml.Xsl.XsltSettings>
- <xref:System.Xml.Xsl.XsltMessageEncounteredEventArgs>
