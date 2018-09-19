---
title: "Nasıl yapılır: Viewport3D'de Tıklama Testi"
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- 3-D visuals [WPF], hit-testing for
- hit tests [WPF], for 3-D visuals
- Viewport3D [WPF]
ms.assetid: 42bfbd99-c7c6-43f1-940b-90448faa412e
ms.openlocfilehash: 297fe17b8844f7542255afcfe442fbf9b7a0d59d
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46003925"
---
# <a name="how-to-hit-test-in-a-viewport3d"></a><span data-ttu-id="cfdc5-102">Nasıl yapılır: Viewport3D'de Tıklama Testi</span><span class="sxs-lookup"><span data-stu-id="cfdc5-102">How to: Hit Test in a Viewport3D</span></span>
<span data-ttu-id="cfdc5-103">Bu örnek nasıl tıklama testi için 3B Görsellerde gösterir bir <xref:System.Windows.Controls.Viewport3D>.</span><span class="sxs-lookup"><span data-stu-id="cfdc5-103">This example shows how to hit test for 3D Visuals in a <xref:System.Windows.Controls.Viewport3D>.</span></span>  
  
 <span data-ttu-id="cfdc5-104">Çünkü <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> 2B ve 3B bilgilerini döndürür yalnızca 3B sonuçları okumak için test sonuçlarını yinelemek mümkündür.</span><span class="sxs-lookup"><span data-stu-id="cfdc5-104">Because <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> returns 2D and 3D information, it is possible to iterate through the test results to read only 3D results.</span></span>  
  
 [!code-csharp[HitTest3D#HitTest3D3DN4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HitTest3D/CSharp/Window1.xaml.cs#hittest3d3dn4)]
 [!code-vb[HitTest3D#HitTest3D3DN4](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HitTest3D/visualbasic/window1.xaml.vb#hittest3d3dn4)]  
  
 <span data-ttu-id="cfdc5-105"><xref:System.Windows.Media.HitTestResultBehavior> Aşağıdaki kodda, isabet test sonuçlarını nasıl işleneceğini belirler.</span><span class="sxs-lookup"><span data-stu-id="cfdc5-105">The <xref:System.Windows.Media.HitTestResultBehavior> in the following code determines how the hit test results are processed.</span></span>  <span data-ttu-id="cfdc5-106">`UpdateResultInfo` ve `UpdateMaterial` yerel olarak tanımlanan yöntemler.</span><span class="sxs-lookup"><span data-stu-id="cfdc5-106">`UpdateResultInfo` and `UpdateMaterial` are locally defined methods.</span></span>  
  
 [!code-csharp[HitTest3D#HitTest3D3DN5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HitTest3D/CSharp/Window1.xaml.cs#hittest3d3dn5)]
 [!code-vb[HitTest3D#HitTest3D3DN5](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HitTest3D/visualbasic/window1.xaml.vb#hittest3d3dn5)]  
  
## <a name="see-also"></a><span data-ttu-id="cfdc5-107">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="cfdc5-107">See Also</span></span>  
 [<span data-ttu-id="cfdc5-108">3B isabet sınaması örneği</span><span class="sxs-lookup"><span data-stu-id="cfdc5-108">3-D Hit Testing Sample</span></span>](https://go.microsoft.com/fwlink/?LinkID=159959)
