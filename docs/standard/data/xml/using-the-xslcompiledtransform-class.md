---
title: XslCompiledTransform Sınıfını Kullanma
ms.date: 03/30/2017
ms.assetid: f9b074f6-d6f4-49dd-a093-df510bf0cf7b
ms.openlocfilehash: cdcbb803fee8eba2b05c7ca12208dbf9c5ad0f7f
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95675613"
---
# <a name="using-the-xslcompiledtransform-class"></a><span data-ttu-id="428fa-102">XslCompiledTransform Sınıfını Kullanma</span><span class="sxs-lookup"><span data-stu-id="428fa-102">Using the XslCompiledTransform Class</span></span>

<span data-ttu-id="428fa-103"><xref:System.Xml.Xsl.XslCompiledTransform>Sınıfı, Microsoft .NET Framework XSLT işlemcisidir.</span><span class="sxs-lookup"><span data-stu-id="428fa-103">The <xref:System.Xml.Xsl.XslCompiledTransform> class is the Microsoft .NET Framework XSLT processor.</span></span> <span data-ttu-id="428fa-104">Bu sınıf, stil sayfalarını derlemek ve XSLT dönüştürmelerini yürütmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="428fa-104">This class is used to compile style sheets and execute XSLT transformations.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="428fa-105">Sınıfının genel performansı <xref:System.Xml.Xsl.XslCompiledTransform> sınıfından daha iyidir <xref:System.Xml.Xsl.XslTransform> , ancak <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> sınıfın yöntemi, <xref:System.Xml.Xsl.XslCompiledTransform> <xref:System.Xml.Xsl.XslTransform.Load%2A> <xref:System.Xml.Xsl.XslTransform> bir dönüşümde ilk kez çağrıldığında sınıfının yönteminden daha yavaş çalışabilir.</span><span class="sxs-lookup"><span data-stu-id="428fa-105">Although the overall performance of the <xref:System.Xml.Xsl.XslCompiledTransform> class is better than the <xref:System.Xml.Xsl.XslTransform> class, the <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> method of the <xref:System.Xml.Xsl.XslCompiledTransform> class might perform more slowly than the <xref:System.Xml.Xsl.XslTransform.Load%2A> method of the <xref:System.Xml.Xsl.XslTransform> class the first time it is called on a transformation.</span></span> <span data-ttu-id="428fa-106">Bunun nedeni XSLT dosyasının yüklenmeden önce derlenmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="428fa-106">This is because the XSLT file must be compiled before it is loaded.</span></span> <span data-ttu-id="428fa-107">Daha fazla bilgi için şu blog gönderisine bakın: [XslCompiledTransform, XslTransform 'Dan daha yavaş?](/archive/blogs/antosha/xslcompiledtransform-slower-than-xsltransform)</span><span class="sxs-lookup"><span data-stu-id="428fa-107">For more information, see the following blog post: [XslCompiledTransform Slower than XslTransform?](/archive/blogs/antosha/xslcompiledtransform-slower-than-xsltransform)</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="428fa-108">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="428fa-108">In This Section</span></span>  

 [<span data-ttu-id="428fa-109">XslCompiledTransform Sınıfına Girişler</span><span class="sxs-lookup"><span data-stu-id="428fa-109">Inputs to the XslCompiledTransform Class</span></span>](inputs-to-the-xslcompiledtransform-class.md)  
 <span data-ttu-id="428fa-110">Kullanılabilir XSLT giriş seçeneklerini açıklar.</span><span class="sxs-lookup"><span data-stu-id="428fa-110">Describes the available XSLT input options.</span></span>  
  
 [<span data-ttu-id="428fa-111">XslCompiledTransform Sınıfındaki Çıkış Seçenekleri</span><span class="sxs-lookup"><span data-stu-id="428fa-111">Output Options on the XslCompiledTransform Class</span></span>](output-options-on-the-xslcompiledtransform-class.md)  
 <span data-ttu-id="428fa-112">Kullanılabilir XSLT çıkış seçeneklerini açıklar.</span><span class="sxs-lookup"><span data-stu-id="428fa-112">Describes the available XSLT output options.</span></span>  
  
 [<span data-ttu-id="428fa-113">XSLT İşleme Sırasında Dış Kaynakları Çözümleme</span><span class="sxs-lookup"><span data-stu-id="428fa-113">Resolving External Resources During XSLT Processing</span></span>](resolving-external-resources-during-xslt-processing.md)  
 <span data-ttu-id="428fa-114"><xref:System.Xml.XmlResolver>Dış kaynakları çözümlemek için sınıfının kullanımını açıklar.</span><span class="sxs-lookup"><span data-stu-id="428fa-114">Discusses using the <xref:System.Xml.XmlResolver> class to resolve external resources.</span></span>  
  
 [<span data-ttu-id="428fa-115">XSLT Stil Sayfalarını Genişletme</span><span class="sxs-lookup"><span data-stu-id="428fa-115">Extending XSLT Style Sheets</span></span>](extending-xslt-style-sheets.md)  
 <span data-ttu-id="428fa-116">XSLT uzantılarının nasıl desteklendiğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="428fa-116">Discusses how XSLT extensions are supported.</span></span>  
  
|||  
|-|-|  
|[<span data-ttu-id="428fa-117">Kurtarılabilir XSLT Hataları</span><span class="sxs-lookup"><span data-stu-id="428fa-117">Recoverable XSLT Errors</span></span>](recoverable-xslt-errors.md)|<span data-ttu-id="428fa-118">World Wide Web Konsorsiyumu (W3C) XSLT 1,0 önerisi tarafından izin verilen isteğe bağlı davranışları listeler ve bu davranışların sınıf tarafından nasıl işlendiğini açıklar <xref:System.Xml.Xsl.XslCompiledTransform> .</span><span class="sxs-lookup"><span data-stu-id="428fa-118">Lists discretionary behaviors allowed by the World Wide Web Consortium (W3C) XSLT 1.0 recommendation and describes how these behaviors are handled by the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span>|  
|[<span data-ttu-id="428fa-119">Nasıl yapılır: Düğüm Parçasını Dönüştürme</span><span class="sxs-lookup"><span data-stu-id="428fa-119">How to: Transform a Node Fragment</span></span>](how-to-transform-a-node-fragment.md)|<span data-ttu-id="428fa-120">Bir düğüm parçasının nasıl dönüştürüleceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="428fa-120">Describes how to transform a node fragment.</span></span>|  
  
## <a name="related-sections"></a><span data-ttu-id="428fa-121">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="428fa-121">Related Sections</span></span>  

 [<span data-ttu-id="428fa-122">XslTransform Sınıfından Geçirme</span><span class="sxs-lookup"><span data-stu-id="428fa-122">Migrating From the XslTransform Class</span></span>](migrating-from-the-xsltransform-class.md)  
 <span data-ttu-id="428fa-123">Sınıfından kodun nasıl geçirileceğiyle anlatılmaktadır <xref:System.Xml.Xsl.XslTransform></span><span class="sxs-lookup"><span data-stu-id="428fa-123">Discusses how to migrate code from the <xref:System.Xml.Xsl.XslTransform> class</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="428fa-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="428fa-124">See also</span></span>

- <xref:System.Xml.Xsl.XsltSettings>
- <xref:System.Xml.Xsl.XsltMessageEncounteredEventArgs>
