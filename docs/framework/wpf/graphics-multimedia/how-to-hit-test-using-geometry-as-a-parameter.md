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
ms.openlocfilehash: 8bed7784b00f49178c9a87def74b62f7ce620ec7
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69923401"
---
# <a name="how-to-hit-test-using-geometry-as-a-parameter"></a><span data-ttu-id="feed5-102">Nasıl yapılır: Geometriyi Parametre Olarak Kullanan Tıklama Testi</span><span class="sxs-lookup"><span data-stu-id="feed5-102">How to: Hit Test Using Geometry as a Parameter</span></span>
<span data-ttu-id="feed5-103">Bu örnek, bir isabet testi parametresi olarak kullanarak bir <xref:System.Windows.Media.Geometry> görsel nesnesi üzerinde bir isabet testinin nasıl gerçekleştirileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="feed5-103">This example shows how to perform a hit test on a visual object using a <xref:System.Windows.Media.Geometry> as a hit test parameter.</span></span>  
  
## <a name="example"></a><span data-ttu-id="feed5-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="feed5-104">Example</span></span>  
 <span data-ttu-id="feed5-105">Aşağıdaki örnek, <xref:System.Windows.Media.GeometryHitTestParameters> <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> yöntemi için kullanarak bir isabet testinin nasıl ayarlanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="feed5-105">The following example shows how to set up a hit test using <xref:System.Windows.Media.GeometryHitTestParameters> for the <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> method.</span></span> <span data-ttu-id="feed5-106">Yönteminegeçirilen`OnMouseDown`değer, isabet testinin aralığını genişletmek için bir <xref:System.Windows.Media.Geometry> nesne oluşturmak için kullanılır. <xref:System.Windows.Point></span><span class="sxs-lookup"><span data-stu-id="feed5-106">The <xref:System.Windows.Point> value that is passed to the `OnMouseDown` method is used to create a <xref:System.Windows.Media.Geometry> object in order to expand the range of the hit test.</span></span>  
  
 [!code-csharp[HitTestingOverview#HitTestingOverviewSnippet10](~/samples/snippets/csharp/VS_Snippets_Wpf/HitTestingOverview/CSharp/GeometryHitTest.cs#hittestingoverviewsnippet10)]
 [!code-vb[HitTestingOverview#HitTestingOverviewSnippet10](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HitTestingOverview/visualbasic/geometryhittest.vb#hittestingoverviewsnippet10)]  
  
 <span data-ttu-id="feed5-107">Özelliği, <xref:System.Windows.Media.GeometryHitTestResult.IntersectionDetail%2A> bir isabet testi parametresi olarak kullanan bir <xref:System.Windows.Media.Geometry> isabet testinin sonuçlarıyla ilgili bilgiler sağlar.<xref:System.Windows.Media.GeometryHitTestResult></span><span class="sxs-lookup"><span data-stu-id="feed5-107">The <xref:System.Windows.Media.GeometryHitTestResult.IntersectionDetail%2A> property of <xref:System.Windows.Media.GeometryHitTestResult> provides information about the results of a hit test that uses a <xref:System.Windows.Media.Geometry> as a hit test parameter.</span></span> <span data-ttu-id="feed5-108">Aşağıdaki çizimde, hedef görsel nesnesinin (kırmızı kare) isabet testi geometrisi (mavi daire) ve işlenmiş içeriği arasındaki ilişki gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="feed5-108">The following illustration shows the relationship between the hit test geometry (the blue circle) and the rendered content of the target visual object (the red square).</span></span>  
  
 ![İsabet testinde kullanılan IntersectionDetail gösteren diyagram.](./media/how-to-hit-test-using-geometry-as-a-parameter/intersectiondetail-hit-test.png)  
  
 <span data-ttu-id="feed5-110">Aşağıdaki örnek, bir isabet testi parametresi olarak kullanıldığında bir <xref:System.Windows.Media.Geometry> isabet testi geri çağrısının nasıl uygulanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="feed5-110">The following example shows how to implement a hit test callback when a <xref:System.Windows.Media.Geometry> is used as a hit test parameter.</span></span> <span data-ttu-id="feed5-111">Parametresi, özelliğin değerini almak için <xref:System.Windows.Media.GeometryHitTestResult> bir olarak öğesine dönüştürüldü. <xref:System.Windows.Media.GeometryHitTestResult.IntersectionDetail%2A> `result`</span><span class="sxs-lookup"><span data-stu-id="feed5-111">The `result` parameter is cast to a <xref:System.Windows.Media.GeometryHitTestResult> in order to retrieve the value of the <xref:System.Windows.Media.GeometryHitTestResult.IntersectionDetail%2A> property.</span></span> <span data-ttu-id="feed5-112">Özellik değeri, isabet sınama parametresinin, isabet testi <xref:System.Windows.Media.Geometry> hedefinin işlenmiş içeriği içinde tam mı yoksa kısmen mi olduğunu belirlemenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="feed5-112">The property value allows you to determine if the <xref:System.Windows.Media.Geometry> hit test parameter is fully or partially contained within the rendered content of the hit test target.</span></span> <span data-ttu-id="feed5-113">Bu durumda, örnek kod yalnızca hedef sınırın içinde tam olarak bulunan görsellerin listesine vuruş testi sonuçları ekler.</span><span class="sxs-lookup"><span data-stu-id="feed5-113">In this case, the sample code is only adding hit test results to the list for visuals that are fully contained within the target boundary.</span></span>  
  
 [!code-csharp[HitTestingOverview#HitTestingOverviewSnippet11](~/samples/snippets/csharp/VS_Snippets_Wpf/HitTestingOverview/CSharp/GeometryHitTest.cs#hittestingoverviewsnippet11)]
 [!code-vb[HitTestingOverview#HitTestingOverviewSnippet11](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HitTestingOverview/visualbasic/geometryhittest.vb#hittestingoverviewsnippet11)]  
  
> [!NOTE]
> <span data-ttu-id="feed5-114">Kesişim ayrıntısı olduğunda geri çağırma çağrılmamalıdır. <xref:System.Windows.Media.IntersectionDetail.Empty> <xref:System.Windows.Media.HitTestResult></span><span class="sxs-lookup"><span data-stu-id="feed5-114">The <xref:System.Windows.Media.HitTestResult> callback should not be called when the intersection detail is <xref:System.Windows.Media.IntersectionDetail.Empty>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="feed5-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="feed5-115">See also</span></span>

- [<span data-ttu-id="feed5-116">Görsel Katmanda Tıklama Testi</span><span class="sxs-lookup"><span data-stu-id="feed5-116">Hit Testing in the Visual Layer</span></span>](hit-testing-in-the-visual-layer.md)
- [<span data-ttu-id="feed5-117">Görselde Tıklama Testi Geometrisi</span><span class="sxs-lookup"><span data-stu-id="feed5-117">Hit Test Geometry in a Visual</span></span>](how-to-hit-test-geometry-in-a-visual.md)
