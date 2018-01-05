---
title: "Nasıl yapılır: Geometriyi Parametre Olarak Kullanan Tıklama Testi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hit tests [WPF], on visual objects using Geometry objects [WPF]
- visual objects [WPF], hit tests on
- Geometry objects [WPF], hit tests on visual objects [WPF]
ms.assetid: 6c8bdbf2-19e0-4fbb-bf89-c1252b2ebc61
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1b5c5bb47e3f435419bcf3c472f052260adec7c0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-hit-test-using-geometry-as-a-parameter"></a><span data-ttu-id="e9324-102">Nasıl yapılır: Geometriyi Parametre Olarak Kullanan Tıklama Testi</span><span class="sxs-lookup"><span data-stu-id="e9324-102">How to: Hit Test Using Geometry as a Parameter</span></span>
<span data-ttu-id="e9324-103">Bu örnek kullanarak visual nesne üzerinde isabet testi gerçekleştirmek nasıl gösterir bir <xref:System.Windows.Media.Geometry> parametresi isabet testi.</span><span class="sxs-lookup"><span data-stu-id="e9324-103">This example shows how to perform a hit test on a visual object using a <xref:System.Windows.Media.Geometry> as a hit test parameter.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e9324-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="e9324-104">Example</span></span>  
 <span data-ttu-id="e9324-105">Aşağıdaki örnekte bir isabet testi kullanılarak ayarlanan gösterilmektedir <xref:System.Windows.Media.GeometryHitTestParameters> için <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="e9324-105">The following example shows how to set up a hit test using <xref:System.Windows.Media.GeometryHitTestParameters> for the <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> method.</span></span> <span data-ttu-id="e9324-106"><xref:System.Windows.Point> İçin geçirilen değer `OnMouseDown` yöntemi oluşturmak için kullanılan bir <xref:System.Windows.Media.Geometry> isabet testi aralığını genişletmek için nesne.</span><span class="sxs-lookup"><span data-stu-id="e9324-106">The <xref:System.Windows.Point> value that is passed to the `OnMouseDown` method is used to create a <xref:System.Windows.Media.Geometry> object in order to expand the range of the hit test.</span></span>  
  
 [!code-csharp[HitTestingOverview#HitTestingOverviewSnippet10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HitTestingOverview/CSharp/GeometryHitTest.cs#hittestingoverviewsnippet10)]
 [!code-vb[HitTestingOverview#HitTestingOverviewSnippet10](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HitTestingOverview/visualbasic/geometryhittest.vb#hittestingoverviewsnippet10)]  
  
 <span data-ttu-id="e9324-107"><xref:System.Windows.Media.GeometryHitTestResult.IntersectionDetail%2A> Özelliği <xref:System.Windows.Media.GeometryHitTestResult> kullanan bir isabet testi sonuçlarını hakkında bilgi sağlar bir <xref:System.Windows.Media.Geometry> parametresi isabet testi.</span><span class="sxs-lookup"><span data-stu-id="e9324-107">The <xref:System.Windows.Media.GeometryHitTestResult.IntersectionDetail%2A> property of <xref:System.Windows.Media.GeometryHitTestResult> provides information about the results of a hit test that uses a <xref:System.Windows.Media.Geometry> as a hit test parameter.</span></span> <span data-ttu-id="e9324-108">Aşağıdaki çizimde isabet testi geometrisi (mavi daire) ve hedef görsel nesne (kırmızı kare) işlenmiş içeriği arasındaki ilişkiyi gösterir.</span><span class="sxs-lookup"><span data-stu-id="e9324-108">The following illustration shows the relationship between the hit test geometry (the blue circle) and the rendered content of the target visual object (the red square).</span></span>  
  
 <span data-ttu-id="e9324-109">![Tıklatma testinde kullanılan IntersectionDetail diyagramı isabet testi](../../../../docs/framework/wpf/graphics-multimedia/media/intersectiondetail01.png "IntersectionDetail01")</span><span class="sxs-lookup"><span data-stu-id="e9324-109">![Diagram of IntersectionDetail used in hit testing](../../../../docs/framework/wpf/graphics-multimedia/media/intersectiondetail01.png "IntersectionDetail01")</span></span>  
<span data-ttu-id="e9324-110">İsabet testi geometrisi ve hedef görsel nesnesinin kesişimi</span><span class="sxs-lookup"><span data-stu-id="e9324-110">Intersection between hit test geometry and target visual object</span></span>  
  
 <span data-ttu-id="e9324-111">Aşağıdaki örnek, bir isabet testi geri uygulamak gösterilmektedir, bir <xref:System.Windows.Media.Geometry> isabet testi parametre olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="e9324-111">The following example shows how to implement a hit test callback when a <xref:System.Windows.Media.Geometry> is used as a hit test parameter.</span></span> <span data-ttu-id="e9324-112">`result` Parametresi atandığında bir <xref:System.Windows.Media.GeometryHitTestResult> değerini almak için <xref:System.Windows.Media.GeometryHitTestResult.IntersectionDetail%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="e9324-112">The `result` parameter is cast to a <xref:System.Windows.Media.GeometryHitTestResult> in order to retrieve the value of the <xref:System.Windows.Media.GeometryHitTestResult.IntersectionDetail%2A> property.</span></span> <span data-ttu-id="e9324-113">Özellik değeri, belirlemenize olanak tanır <xref:System.Windows.Media.Geometry> isabet testi parametresi tamamen veya kısmen barındırılan hedef isabet testinin işlenmiş içeriği içinde.</span><span class="sxs-lookup"><span data-stu-id="e9324-113">The property value allows you to determine if the <xref:System.Windows.Media.Geometry> hit test parameter is fully or partially contained within the rendered content of the hit test target.</span></span> <span data-ttu-id="e9324-114">Bu durumda, örnek kod için tam olarak hedef sınırı içinde bulunan görselleri listesine yalnızca isabet testi sonuçları eklemektir.</span><span class="sxs-lookup"><span data-stu-id="e9324-114">In this case, the sample code is only adding hit test results to the list for visuals that are fully contained within the target boundary.</span></span>  
  
 [!code-csharp[HitTestingOverview#HitTestingOverviewSnippet11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HitTestingOverview/CSharp/GeometryHitTest.cs#hittestingoverviewsnippet11)]
 [!code-vb[HitTestingOverview#HitTestingOverviewSnippet11](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HitTestingOverview/visualbasic/geometryhittest.vb#hittestingoverviewsnippet11)]  
  
> [!NOTE]
>  <span data-ttu-id="e9324-115"><xref:System.Windows.Media.HitTestResult> Geri çağırma çağrılmamalı kesişim ayrıntı olduğunda <xref:System.Windows.Media.IntersectionDetail.Empty>.</span><span class="sxs-lookup"><span data-stu-id="e9324-115">The <xref:System.Windows.Media.HitTestResult> callback should not be called when the intersection detail is <xref:System.Windows.Media.IntersectionDetail.Empty>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e9324-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e9324-116">See Also</span></span>  
 [<span data-ttu-id="e9324-117">Görsel Katmanda Tıklama Testi</span><span class="sxs-lookup"><span data-stu-id="e9324-117">Hit Testing in the Visual Layer</span></span>](../../../../docs/framework/wpf/graphics-multimedia/hit-testing-in-the-visual-layer.md)  
 [<span data-ttu-id="e9324-118">Görselde Tıklama Testi Geometrisi</span><span class="sxs-lookup"><span data-stu-id="e9324-118">Hit Test Geometry in a Visual</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-hit-test-geometry-in-a-visual.md)
