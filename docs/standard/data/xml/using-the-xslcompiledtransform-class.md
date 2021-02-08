---
description: 'Hakkında daha fazla bilgi edinin: XslCompiledTransform sınıfını kullanma'
title: XslCompiledTransform Sınıfını Kullanma
ms.date: 03/30/2017
ms.assetid: f9b074f6-d6f4-49dd-a093-df510bf0cf7b
ms.openlocfilehash: 76f595e0604fb586223affe2155ad7fdcac83963
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99782851"
---
# <a name="using-the-xslcompiledtransform-class"></a><span data-ttu-id="836da-103">XslCompiledTransform Sınıfını Kullanma</span><span class="sxs-lookup"><span data-stu-id="836da-103">Using the XslCompiledTransform Class</span></span>

<span data-ttu-id="836da-104"><xref:System.Xml.Xsl.XslCompiledTransform>Sınıfı, Microsoft .NET Framework XSLT işlemcisidir.</span><span class="sxs-lookup"><span data-stu-id="836da-104">The <xref:System.Xml.Xsl.XslCompiledTransform> class is the Microsoft .NET Framework XSLT processor.</span></span> <span data-ttu-id="836da-105">Bu sınıf, stil sayfalarını derlemek ve XSLT dönüştürmelerini yürütmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="836da-105">This class is used to compile style sheets and execute XSLT transformations.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="836da-106">Sınıfının genel performansı <xref:System.Xml.Xsl.XslCompiledTransform> sınıfından daha iyidir <xref:System.Xml.Xsl.XslTransform> , ancak <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> sınıfın yöntemi, <xref:System.Xml.Xsl.XslCompiledTransform> <xref:System.Xml.Xsl.XslTransform.Load%2A> <xref:System.Xml.Xsl.XslTransform> bir dönüşümde ilk kez çağrıldığında sınıfının yönteminden daha yavaş çalışabilir.</span><span class="sxs-lookup"><span data-stu-id="836da-106">Although the overall performance of the <xref:System.Xml.Xsl.XslCompiledTransform> class is better than the <xref:System.Xml.Xsl.XslTransform> class, the <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> method of the <xref:System.Xml.Xsl.XslCompiledTransform> class might perform more slowly than the <xref:System.Xml.Xsl.XslTransform.Load%2A> method of the <xref:System.Xml.Xsl.XslTransform> class the first time it is called on a transformation.</span></span> <span data-ttu-id="836da-107">Bunun nedeni XSLT dosyasının yüklenmeden önce derlenmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="836da-107">This is because the XSLT file must be compiled before it is loaded.</span></span> <span data-ttu-id="836da-108">Daha fazla bilgi için şu blog gönderisine bakın: [XslCompiledTransform, XslTransform 'Dan daha yavaş?](/archive/blogs/antosha/xslcompiledtransform-slower-than-xsltransform)</span><span class="sxs-lookup"><span data-stu-id="836da-108">For more information, see the following blog post: [XslCompiledTransform Slower than XslTransform?](/archive/blogs/antosha/xslcompiledtransform-slower-than-xsltransform)</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="836da-109">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="836da-109">In This Section</span></span>  

 [<span data-ttu-id="836da-110">XslCompiledTransform Sınıfına Girişler</span><span class="sxs-lookup"><span data-stu-id="836da-110">Inputs to the XslCompiledTransform Class</span></span>](inputs-to-the-xslcompiledtransform-class.md)  
 <span data-ttu-id="836da-111">Kullanılabilir XSLT giriş seçeneklerini açıklar.</span><span class="sxs-lookup"><span data-stu-id="836da-111">Describes the available XSLT input options.</span></span>  
  
 [<span data-ttu-id="836da-112">XslCompiledTransform Sınıfındaki Çıkış Seçenekleri</span><span class="sxs-lookup"><span data-stu-id="836da-112">Output Options on the XslCompiledTransform Class</span></span>](output-options-on-the-xslcompiledtransform-class.md)  
 <span data-ttu-id="836da-113">Kullanılabilir XSLT çıkış seçeneklerini açıklar.</span><span class="sxs-lookup"><span data-stu-id="836da-113">Describes the available XSLT output options.</span></span>  
  
 [<span data-ttu-id="836da-114">XSLT İşleme Sırasında Dış Kaynakları Çözümleme</span><span class="sxs-lookup"><span data-stu-id="836da-114">Resolving External Resources During XSLT Processing</span></span>](resolving-external-resources-during-xslt-processing.md)  
 <span data-ttu-id="836da-115"><xref:System.Xml.XmlResolver>Dış kaynakları çözümlemek için sınıfının kullanımını açıklar.</span><span class="sxs-lookup"><span data-stu-id="836da-115">Discusses using the <xref:System.Xml.XmlResolver> class to resolve external resources.</span></span>  
  
 [<span data-ttu-id="836da-116">XSLT Stil Sayfalarını Genişletme</span><span class="sxs-lookup"><span data-stu-id="836da-116">Extending XSLT Style Sheets</span></span>](extending-xslt-style-sheets.md)  
 <span data-ttu-id="836da-117">XSLT uzantılarının nasıl desteklendiğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="836da-117">Discusses how XSLT extensions are supported.</span></span>  
  
|||  
|-|-|  
|[<span data-ttu-id="836da-118">Kurtarılabilir XSLT Hataları</span><span class="sxs-lookup"><span data-stu-id="836da-118">Recoverable XSLT Errors</span></span>](recoverable-xslt-errors.md)|<span data-ttu-id="836da-119">World Wide Web Konsorsiyumu (W3C) XSLT 1,0 önerisi tarafından izin verilen isteğe bağlı davranışları listeler ve bu davranışların sınıf tarafından nasıl işlendiğini açıklar <xref:System.Xml.Xsl.XslCompiledTransform> .</span><span class="sxs-lookup"><span data-stu-id="836da-119">Lists discretionary behaviors allowed by the World Wide Web Consortium (W3C) XSLT 1.0 recommendation and describes how these behaviors are handled by the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span>|  
|[<span data-ttu-id="836da-120">Nasıl yapılır: Düğüm Parçasını Dönüştürme</span><span class="sxs-lookup"><span data-stu-id="836da-120">How to: Transform a Node Fragment</span></span>](how-to-transform-a-node-fragment.md)|<span data-ttu-id="836da-121">Bir düğüm parçasının nasıl dönüştürüleceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="836da-121">Describes how to transform a node fragment.</span></span>|  
  
## <a name="related-sections"></a><span data-ttu-id="836da-122">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="836da-122">Related Sections</span></span>  

 [<span data-ttu-id="836da-123">XslTransform Sınıfından Geçirme</span><span class="sxs-lookup"><span data-stu-id="836da-123">Migrating From the XslTransform Class</span></span>](migrating-from-the-xsltransform-class.md)  
 <span data-ttu-id="836da-124">Sınıfından kodun nasıl geçirileceğiyle anlatılmaktadır <xref:System.Xml.Xsl.XslTransform></span><span class="sxs-lookup"><span data-stu-id="836da-124">Discusses how to migrate code from the <xref:System.Xml.Xsl.XslTransform> class</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="836da-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="836da-125">See also</span></span>

- <xref:System.Xml.Xsl.XsltSettings>
- <xref:System.Xml.Xsl.XsltMessageEncounteredEventArgs>
