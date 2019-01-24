---
title: 'Nasıl yapılır: Geometriyi Parametre Olarak Kullanan Tıklama Testi'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hit tests [WPF], on visual objects using Geometry objects [WPF]
- visual objects [WPF], hit tests on
- Geometry objects [WPF], hit tests on visual objects [WPF]
ms.assetid: 6c8bdbf2-19e0-4fbb-bf89-c1252b2ebc61
ms.openlocfilehash: d52f8da891ecdf632952c441f94aab4c0b56da7f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54564259"
---
# <a name="how-to-hit-test-using-geometry-as-a-parameter"></a><span data-ttu-id="03f6b-102">Nasıl yapılır: Geometriyi Parametre Olarak Kullanan Tıklama Testi</span><span class="sxs-lookup"><span data-stu-id="03f6b-102">How to: Hit Test Using Geometry as a Parameter</span></span>
<span data-ttu-id="03f6b-103">Bu örnek gösterir kullanarak visual nesne üzerinde bir isabet testi gerçekleştirmek nasıl bir <xref:System.Windows.Media.Geometry> parametre isabet testi.</span><span class="sxs-lookup"><span data-stu-id="03f6b-103">This example shows how to perform a hit test on a visual object using a <xref:System.Windows.Media.Geometry> as a hit test parameter.</span></span>  
  
## <a name="example"></a><span data-ttu-id="03f6b-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="03f6b-104">Example</span></span>  
 <span data-ttu-id="03f6b-105">Aşağıdaki örnek bir isabet sınaması kullanılarak ayarlanan gösterilmiştir <xref:System.Windows.Media.GeometryHitTestParameters> için <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="03f6b-105">The following example shows how to set up a hit test using <xref:System.Windows.Media.GeometryHitTestParameters> for the <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> method.</span></span> <span data-ttu-id="03f6b-106"><xref:System.Windows.Point> Geçirilen değer `OnMouseDown` yöntemi oluşturmak için kullanılan bir <xref:System.Windows.Media.Geometry> isabet sınaması aralığını genişletmek için nesne.</span><span class="sxs-lookup"><span data-stu-id="03f6b-106">The <xref:System.Windows.Point> value that is passed to the `OnMouseDown` method is used to create a <xref:System.Windows.Media.Geometry> object in order to expand the range of the hit test.</span></span>  
  
 [!code-csharp[HitTestingOverview#HitTestingOverviewSnippet10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HitTestingOverview/CSharp/GeometryHitTest.cs#hittestingoverviewsnippet10)]
 [!code-vb[HitTestingOverview#HitTestingOverviewSnippet10](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HitTestingOverview/visualbasic/geometryhittest.vb#hittestingoverviewsnippet10)]  
  
 <span data-ttu-id="03f6b-107"><xref:System.Windows.Media.GeometryHitTestResult.IntersectionDetail%2A> Özelliği <xref:System.Windows.Media.GeometryHitTestResult> kullanan isabet sınaması sonuçlarıyla ilgili bilgi sağlar bir <xref:System.Windows.Media.Geometry> parametre isabet testi.</span><span class="sxs-lookup"><span data-stu-id="03f6b-107">The <xref:System.Windows.Media.GeometryHitTestResult.IntersectionDetail%2A> property of <xref:System.Windows.Media.GeometryHitTestResult> provides information about the results of a hit test that uses a <xref:System.Windows.Media.Geometry> as a hit test parameter.</span></span> <span data-ttu-id="03f6b-108">İsabet testi geometrisi (mavi daire) ve işlenmiş içeriği hedef visual nesnenin (kırmızı kare) arasındaki ilişki aşağıda gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="03f6b-108">The following illustration shows the relationship between the hit test geometry (the blue circle) and the rendered content of the target visual object (the red square).</span></span>  
  
 <span data-ttu-id="03f6b-109">![Diyagram Tıklatma testinde kullanılan IntersectionDetail isabet sınaması](../../../../docs/framework/wpf/graphics-multimedia/media/intersectiondetail01.png "IntersectionDetail01")</span><span class="sxs-lookup"><span data-stu-id="03f6b-109">![Diagram of IntersectionDetail used in hit testing](../../../../docs/framework/wpf/graphics-multimedia/media/intersectiondetail01.png "IntersectionDetail01")</span></span>  
<span data-ttu-id="03f6b-110">İsabet testi geometrisi ve hedef görsel nesneyi kesişimi</span><span class="sxs-lookup"><span data-stu-id="03f6b-110">Intersection between hit test geometry and target visual object</span></span>  
  
 <span data-ttu-id="03f6b-111">Aşağıdaki örnek, bir isabet sınaması geri çağırmanızı uygulamak gösterilmektedir, bir <xref:System.Windows.Media.Geometry> isabet sınaması parametre olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="03f6b-111">The following example shows how to implement a hit test callback when a <xref:System.Windows.Media.Geometry> is used as a hit test parameter.</span></span> <span data-ttu-id="03f6b-112">`result` Parametre türünden bir <xref:System.Windows.Media.GeometryHitTestResult> değerini almak için <xref:System.Windows.Media.GeometryHitTestResult.IntersectionDetail%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="03f6b-112">The `result` parameter is cast to a <xref:System.Windows.Media.GeometryHitTestResult> in order to retrieve the value of the <xref:System.Windows.Media.GeometryHitTestResult.IntersectionDetail%2A> property.</span></span> <span data-ttu-id="03f6b-113">Özellik değeri, belirlemenize olanak tanır <xref:System.Windows.Media.Geometry> isabet sınaması parametresi tamamen veya kısmen yer alan isabet sınaması hedef işlenmiş içeriği içinde.</span><span class="sxs-lookup"><span data-stu-id="03f6b-113">The property value allows you to determine if the <xref:System.Windows.Media.Geometry> hit test parameter is fully or partially contained within the rendered content of the hit test target.</span></span> <span data-ttu-id="03f6b-114">Bu durumda, örnek kod için tam olarak hedef sınırları içinde bulunan görselleri listesine yalnızca isabet testi sonuçlarını eklemektir.</span><span class="sxs-lookup"><span data-stu-id="03f6b-114">In this case, the sample code is only adding hit test results to the list for visuals that are fully contained within the target boundary.</span></span>  
  
 [!code-csharp[HitTestingOverview#HitTestingOverviewSnippet11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HitTestingOverview/CSharp/GeometryHitTest.cs#hittestingoverviewsnippet11)]
 [!code-vb[HitTestingOverview#HitTestingOverviewSnippet11](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HitTestingOverview/visualbasic/geometryhittest.vb#hittestingoverviewsnippet11)]  
  
> [!NOTE]
>  <span data-ttu-id="03f6b-115"><xref:System.Windows.Media.HitTestResult> Kesişimi ayrıntı olduğunda geri çağırma çağırılmalıdır <xref:System.Windows.Media.IntersectionDetail.Empty>.</span><span class="sxs-lookup"><span data-stu-id="03f6b-115">The <xref:System.Windows.Media.HitTestResult> callback should not be called when the intersection detail is <xref:System.Windows.Media.IntersectionDetail.Empty>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="03f6b-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="03f6b-116">See also</span></span>
- [<span data-ttu-id="03f6b-117">Görsel Katmanda Tıklama Testi</span><span class="sxs-lookup"><span data-stu-id="03f6b-117">Hit Testing in the Visual Layer</span></span>](../../../../docs/framework/wpf/graphics-multimedia/hit-testing-in-the-visual-layer.md)
- [<span data-ttu-id="03f6b-118">Görselde Tıklama Testi Geometrisi</span><span class="sxs-lookup"><span data-stu-id="03f6b-118">Hit Test Geometry in a Visual</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-hit-test-geometry-in-a-visual.md)
