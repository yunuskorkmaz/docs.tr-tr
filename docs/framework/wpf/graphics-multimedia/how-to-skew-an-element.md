---
title: "Nasıl yapılır: Bir Öğeyi Eğme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- skewing elements [WPF]
- graphics [WPF], skewing elements
- classes [WPF], SkewTransform
ms.assetid: 56b65f2f-dc6e-4238-923f-ca44ec53c52f
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a9da10e4eb6cf045c6c4936b76f847f21ea1495e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-skew-an-element"></a><span data-ttu-id="68d3c-102">Nasıl yapılır: Bir Öğeyi Eğme</span><span class="sxs-lookup"><span data-stu-id="68d3c-102">How to: Skew an Element</span></span>
<span data-ttu-id="68d3c-103">Bu örnek nasıl kullanılacağını gösteren bir <xref:System.Windows.Media.SkewTransform> bir öğeyi eğme için.</span><span class="sxs-lookup"><span data-stu-id="68d3c-103">This example shows how to use a <xref:System.Windows.Media.SkewTransform> to skew an element.</span></span> <span data-ttu-id="68d3c-104">Olarak da bilinen bükme olduğundan, bir eğme koordinat Tekdüzen olmayan bir biçimde uzatan bir dönüşümü gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="68d3c-104">A skew, which is also known as a shear, is a transformation that stretches the coordinate space in a non-uniform manner.</span></span> <span data-ttu-id="68d3c-105">Tipik bir kullanımı, bir <xref:System.Windows.Media.SkewTransform> benzetimi yapmasıdır [!INCLUDE[TLA#tla_3d](../../../../includes/tlasharptla-3d-md.md)] derinlemesine [!INCLUDE[TLA#tla_2d](../../../../includes/tlasharptla-2d-md.md)] nesneleri.</span><span class="sxs-lookup"><span data-stu-id="68d3c-105">One typical use of a <xref:System.Windows.Media.SkewTransform> is for simulating [!INCLUDE[TLA#tla_3d](../../../../includes/tlasharptla-3d-md.md)] depth in [!INCLUDE[TLA#tla_2d](../../../../includes/tlasharptla-2d-md.md)] objects.</span></span>  
  
 <span data-ttu-id="68d3c-106">Kullanım <xref:System.Windows.Media.SkewTransform.CenterX%2A> ve <xref:System.Windows.Media.SkewTransform.CenterY%2A> center belirtmek için özellikleri noktasını <xref:System.Windows.Media.SkewTransform>.</span><span class="sxs-lookup"><span data-stu-id="68d3c-106">Use the <xref:System.Windows.Media.SkewTransform.CenterX%2A> and <xref:System.Windows.Media.SkewTransform.CenterY%2A> properties to specify the center point of the <xref:System.Windows.Media.SkewTransform>.</span></span>  
  
 <span data-ttu-id="68d3c-107">Kullanım <xref:System.Windows.Media.SkewTransform.AngleX%2A> ve <xref:System.Windows.Media.SkewTransform.AngleY%2A> özellikleri x ve y ekseni eğme açısını belirtmek ve bu eksen boyunca geçerli koordinat sistemi eğme.</span><span class="sxs-lookup"><span data-stu-id="68d3c-107">Use the <xref:System.Windows.Media.SkewTransform.AngleX%2A> and <xref:System.Windows.Media.SkewTransform.AngleY%2A> properties to specify the skew angle of the x-axis and y-axis, and to skew the current coordinate system along these axes.</span></span>  
  
 <span data-ttu-id="68d3c-108">Bir eğme dönüştürmesi etkisini tahmin etmek için göz önünde bulundurun <xref:System.Windows.Media.SkewTransform.AngleX%2A> x ekseni değerleri özgün koordinat sistemi göre Eğer.</span><span class="sxs-lookup"><span data-stu-id="68d3c-108">To predict the effect of a skew transformation, consider that <xref:System.Windows.Media.SkewTransform.AngleX%2A> skews x-axis values relative to the original coordinate system.</span></span> <span data-ttu-id="68d3c-109">Bu nedenle, bir <xref:System.Windows.Media.SkewTransform.AngleX%2A> 30, y ekseni kaynağı üzerinden 30 derece döner ve değerlerini x-kaynağından 30 derece eğer.</span><span class="sxs-lookup"><span data-stu-id="68d3c-109">Therefore, for an <xref:System.Windows.Media.SkewTransform.AngleX%2A> of 30, the y-axis rotates 30 degrees through the origin and skews the values in x- by 30 degrees from that origin.</span></span> <span data-ttu-id="68d3c-110">Benzer şekilde, bir <xref:System.Windows.Media.SkewTransform.AngleY%2A> şeklin y değerleri 30 kaynaktan 30 derece eğer.</span><span class="sxs-lookup"><span data-stu-id="68d3c-110">Likewise, an <xref:System.Windows.Media.SkewTransform.AngleY%2A> of 30 skews the y- values of the shape by 30 degrees from the origin.</span></span> <span data-ttu-id="68d3c-111">Bu (taşıma) çevirme aynı etkiye olmadığını unutmayın 30 derece x ve y koordinat sistemi.</span><span class="sxs-lookup"><span data-stu-id="68d3c-111">Note that this is not the same effect as translating (moving) the coordinate system by 30 degrees in x- or y-.</span></span>  
  
 <span data-ttu-id="68d3c-112">Aşağıdaki örnekte, 45 derece yatay eğme uygulanır bir <xref:System.Windows.Shapes.Rectangle> merkezi noktasından (0,0).</span><span class="sxs-lookup"><span data-stu-id="68d3c-112">The following example applies a horizontal skew of 45 degrees to a <xref:System.Windows.Shapes.Rectangle> from a center point of (0,0).</span></span>  
  
## <a name="example"></a><span data-ttu-id="68d3c-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="68d3c-113">Example</span></span>  
 [!code-xaml[transformsSample#41](../../../../samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/SkewTransformExample.xaml#41)]  
  
 <span data-ttu-id="68d3c-114">Aşağıdaki örnekte, 45 derece yatay eğme uygulanır bir <xref:System.Windows.Shapes.Rectangle> merkezi noktasından (25,25).</span><span class="sxs-lookup"><span data-stu-id="68d3c-114">The following example applies a horizontal skew of 45 degrees to a <xref:System.Windows.Shapes.Rectangle> from a center point of (25,25).</span></span>  
  
 [!code-xaml[transformsSample#42](../../../../samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/SkewTransformExample.xaml#42)]  
  
 <span data-ttu-id="68d3c-115">Aşağıdaki örnekte, 45 derece dikey eğme uygulanır bir <xref:System.Windows.Shapes.Rectangle> merkezi noktasından (25,25).</span><span class="sxs-lookup"><span data-stu-id="68d3c-115">The following example applies a vertical skew of 45 degrees to a <xref:System.Windows.Shapes.Rectangle> from a center point of (25,25).</span></span>  
  
 [!code-xaml[transformsSample#43](../../../../samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/SkewTransformExample.xaml#43)]  
  
 <span data-ttu-id="68d3c-116">Aşağıdaki çizimde, bu örnekte kullanılır farklı eğriltir gösterir.</span><span class="sxs-lookup"><span data-stu-id="68d3c-116">The following illustration shows the different skews that are used in this example.</span></span>  
  
 <span data-ttu-id="68d3c-117">![SkewTransform örnekleri](../../../../docs/framework/wpf/graphics-multimedia/media/img-wcpsdk-graphicsmm-skewtransformexample.gif "img_wcpsdk_graphicsmm_skewtransformexample")</span><span class="sxs-lookup"><span data-stu-id="68d3c-117">![SkewTransform examples](../../../../docs/framework/wpf/graphics-multimedia/media/img-wcpsdk-graphicsmm-skewtransformexample.gif "img_wcpsdk_graphicsmm_skewtransformexample")</span></span>  
<span data-ttu-id="68d3c-118">Gösterilen üç SkewTransform örneği</span><span class="sxs-lookup"><span data-stu-id="68d3c-118">The three SkewTransform examples illustrated</span></span>  
  
 <span data-ttu-id="68d3c-119">Tam bir örnek için bkz: [2-D dönüşümler örnek](http://go.microsoft.com/fwlink/?LinkID=158252).</span><span class="sxs-lookup"><span data-stu-id="68d3c-119">For the complete sample, see [2-D Transforms Sample](http://go.microsoft.com/fwlink/?LinkID=158252).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="68d3c-120">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="68d3c-120">See Also</span></span>  
 <xref:System.Windows.Media.Transform>  
 <xref:System.Windows.Media.SkewTransform>  
 [<span data-ttu-id="68d3c-121">Dönüşümlere Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="68d3c-121">Transforms Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md)  
 [<span data-ttu-id="68d3c-122">Nasıl Yapılır Konuları</span><span class="sxs-lookup"><span data-stu-id="68d3c-122">How-to Topics</span></span>](../../../../docs/framework/wpf/graphics-multimedia/transformations-how-to-topics.md)
