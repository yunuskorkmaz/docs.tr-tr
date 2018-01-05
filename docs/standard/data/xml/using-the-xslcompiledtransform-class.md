---
title: "XslCompiledTransform sınıfını kullanma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f9b074f6-d6f4-49dd-a093-df510bf0cf7b
caps.latest.revision: "3"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 50d391718c53916749121aed35dceb00a65bc42a
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="using-the-xslcompiledtransform-class"></a><span data-ttu-id="0b9c7-102">XslCompiledTransform sınıfını kullanma</span><span class="sxs-lookup"><span data-stu-id="0b9c7-102">Using the XslCompiledTransform Class</span></span>
<span data-ttu-id="0b9c7-103"><xref:System.Xml.Xsl.XslCompiledTransform> Microsoft .NET Framework XSLT işlemci bir sınıftır.</span><span class="sxs-lookup"><span data-stu-id="0b9c7-103">The <xref:System.Xml.Xsl.XslCompiledTransform> class is the Microsoft .NET Framework XSLT processor.</span></span> <span data-ttu-id="0b9c7-104">Bu sınıf, stil sayfaları derlemek ve XSLT dönüştürmeleri yürütmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="0b9c7-104">This class is used to compile style sheets and execute XSLT transformations.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0b9c7-105">Ancak genel performansını <xref:System.Xml.Xsl.XslCompiledTransform> sınıftır daha iyi <xref:System.Xml.Xsl.XslTransform> sınıfı, <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> yöntemi <xref:System.Xml.Xsl.XslCompiledTransform> sınıfı daha gerçekleştirebileceğiniz daha yavaş <xref:System.Xml.Xsl.XslTransform.Load%2A> yöntemi <xref:System.Xml.Xsl.XslTransform> sınıfı ilk kez üzerinde dönüştürme adı verilir.</span><span class="sxs-lookup"><span data-stu-id="0b9c7-105">Although the overall performance of the <xref:System.Xml.Xsl.XslCompiledTransform> class is better than the <xref:System.Xml.Xsl.XslTransform> class, the <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> method of the <xref:System.Xml.Xsl.XslCompiledTransform> class might perform more slowly than the <xref:System.Xml.Xsl.XslTransform.Load%2A> method of the <xref:System.Xml.Xsl.XslTransform> class the first time it is called on a transformation.</span></span> <span data-ttu-id="0b9c7-106">XSLT dosyasının yüklendiği önce derlenmelidir olmasıdır.</span><span class="sxs-lookup"><span data-stu-id="0b9c7-106">This is because the XSLT file must be compiled before it is loaded.</span></span> <span data-ttu-id="0b9c7-107">Daha fazla bilgi için aşağıdaki blog gönderisine bakın: [XslCompiledTransform çok daha yavaş?](http://go.microsoft.com/fwlink/?LinkId=130590)</span><span class="sxs-lookup"><span data-stu-id="0b9c7-107">For more information, see the following blog post: [XslCompiledTransform Slower than XslTransform?](http://go.microsoft.com/fwlink/?LinkId=130590)</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="0b9c7-108">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="0b9c7-108">In This Section</span></span>  
 [<span data-ttu-id="0b9c7-109">XslCompiledTransform Sınıfına Girişler</span><span class="sxs-lookup"><span data-stu-id="0b9c7-109">Inputs to the XslCompiledTransform Class</span></span>](../../../../docs/standard/data/xml/inputs-to-the-xslcompiledtransform-class.md)  
 <span data-ttu-id="0b9c7-110">Kullanılabilir XSLT giriş seçenekleri açıklar.</span><span class="sxs-lookup"><span data-stu-id="0b9c7-110">Describes the available XSLT input options.</span></span>  
  
 [<span data-ttu-id="0b9c7-111">XslCompiledTransform Sınıfındaki Çıkış Seçenekleri</span><span class="sxs-lookup"><span data-stu-id="0b9c7-111">Output Options on the XslCompiledTransform Class</span></span>](../../../../docs/standard/data/xml/output-options-on-the-xslcompiledtransform-class.md)  
 <span data-ttu-id="0b9c7-112">Kullanılabilir XSLT çıkış seçeneklerini açıklar.</span><span class="sxs-lookup"><span data-stu-id="0b9c7-112">Describes the available XSLT output options.</span></span>  
  
 [<span data-ttu-id="0b9c7-113">XSLT İşleme Sırasında Dış Kaynakları Çözümleme</span><span class="sxs-lookup"><span data-stu-id="0b9c7-113">Resolving External Resources During XSLT Processing</span></span>](../../../../docs/standard/data/xml/resolving-external-resources-during-xslt-processing.md)  
 <span data-ttu-id="0b9c7-114">Kullanarak açıklanır <xref:System.Xml.XmlResolver> dış kaynaklara çözümlemek için sınıf.</span><span class="sxs-lookup"><span data-stu-id="0b9c7-114">Discusses using the <xref:System.Xml.XmlResolver> class to resolve external resources.</span></span>  
  
 [<span data-ttu-id="0b9c7-115">XSLT Stil Sayfalarını Genişletme</span><span class="sxs-lookup"><span data-stu-id="0b9c7-115">Extending XSLT Style Sheets</span></span>](../../../../docs/standard/data/xml/extending-xslt-style-sheets.md)  
 <span data-ttu-id="0b9c7-116">XSLT uzantıları nasıl desteklediği açıklanır.</span><span class="sxs-lookup"><span data-stu-id="0b9c7-116">Discusses how XSLT extensions are supported.</span></span>  
  
|||  
|-|-|  
|[<span data-ttu-id="0b9c7-117">Kurtarılabilir XSLT Hataları</span><span class="sxs-lookup"><span data-stu-id="0b9c7-117">Recoverable XSLT Errors</span></span>](../../../../docs/standard/data/xml/recoverable-xslt-errors.md)|<span data-ttu-id="0b9c7-118">İsteğe bağlı davranışları 1.0 öneri World Wide Web Konsorsiyumu (W3C) XSLT tarafından izin verilen listeler ve bu davranışların tarafından nasıl işleneceğini açıklayan <xref:System.Xml.Xsl.XslCompiledTransform> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="0b9c7-118">Lists discretionary behaviors allowed by the World Wide Web Consortium (W3C) XSLT 1.0 recommendation and describes how these behaviors are handled by the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span>|  
|[<span data-ttu-id="0b9c7-119">Nasıl yapılır: Düğüm Parçasını Dönüştürme</span><span class="sxs-lookup"><span data-stu-id="0b9c7-119">How to: Transform a Node Fragment</span></span>](../../../../docs/standard/data/xml/how-to-transform-a-node-fragment.md)|<span data-ttu-id="0b9c7-120">Bir düğüm parça dönüştürme açıklar.</span><span class="sxs-lookup"><span data-stu-id="0b9c7-120">Describes how to transform a node fragment.</span></span>|  
  
## <a name="related-sections"></a><span data-ttu-id="0b9c7-121">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="0b9c7-121">Related Sections</span></span>  
 [<span data-ttu-id="0b9c7-122">XslTransform Sınıfından Geçirme</span><span class="sxs-lookup"><span data-stu-id="0b9c7-122">Migrating From the XslTransform Class</span></span>](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md)  
 <span data-ttu-id="0b9c7-123">Koddan geçirmek nasıl ele <xref:System.Xml.Xsl.XslTransform> sınıfı</span><span class="sxs-lookup"><span data-stu-id="0b9c7-123">Discusses how to migrate code from the <xref:System.Xml.Xsl.XslTransform> class</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0b9c7-124">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="0b9c7-124">See Also</span></span>  
 <xref:System.Xml.Xsl.XsltSettings>  
 <xref:System.Xml.Xsl.XsltMessageEncounteredEventArgs>
