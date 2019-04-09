---
title: 'Nasıl yapılır: PointAnimation Kullanarak bir Nesnenin Konumuna Animasyon Ekleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- graphics [WPF], animation
- animation [WPF], PointAnimation
ms.assetid: 42310977-cc90-438a-8a47-0345898e01be
ms.openlocfilehash: 1ef3f77e551affaa7e61d2aabf95f10c29275417
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59111312"
---
# <a name="how-to-animate-the-position-of-an-object-by-using-pointanimation"></a><span data-ttu-id="b0cf7-102">Nasıl yapılır: PointAnimation Kullanarak bir Nesnenin Konumuna Animasyon Ekleme</span><span class="sxs-lookup"><span data-stu-id="b0cf7-102">How to: Animate the Position of an Object by Using PointAnimation</span></span>
<span data-ttu-id="b0cf7-103">Bu örnek nasıl kullanılacağını gösterir <xref:System.Windows.Media.Animation.PointAnimation> bir nesnenin animasyon uygulamak için sınıfı bir <xref:System.Windows.Shapes.Path>.</span><span class="sxs-lookup"><span data-stu-id="b0cf7-103">This example shows how to use the <xref:System.Windows.Media.Animation.PointAnimation> class to animate an object along a <xref:System.Windows.Shapes.Path>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b0cf7-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="b0cf7-104">Example</span></span>  
 <span data-ttu-id="b0cf7-105">Aşağıdaki örnek, bir elips taşır bir <xref:System.Windows.Shapes.Path> başka bir ekrandaki bir noktadan.</span><span class="sxs-lookup"><span data-stu-id="b0cf7-105">The following example moves an ellipse along a <xref:System.Windows.Shapes.Path> from one point on the screen to another.</span></span> <span data-ttu-id="b0cf7-106">Örnek konumunu canlandırır bir <xref:System.Windows.Media.EllipseGeometry> kullanarak <xref:System.Windows.Media.Animation.PointAnimation> animasyon uygulamak için <xref:System.Windows.Media.EllipseGeometry.Center%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="b0cf7-106">The example animates the position of an <xref:System.Windows.Media.EllipseGeometry> by using <xref:System.Windows.Media.Animation.PointAnimation> to animate the <xref:System.Windows.Media.EllipseGeometry.Center%2A> property.</span></span>  
  
 [!code-csharp[BasicAnimations_snip#PointAnimationWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/BasicAnimations_snip/CSharp/PointAnimationExample.cs#pointanimationwholepage)]
 [!code-vb[BasicAnimations_snip#PointAnimationWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BasicAnimations_snip/VisualBasic/PointAnimationExample.vb#pointanimationwholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="b0cf7-107">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b0cf7-107">See also</span></span>

- <xref:System.Windows.Media.Animation.PointAnimation>
- <xref:System.Windows.Shapes.Path>
- <xref:System.Windows.Media.EllipseGeometry>
- <xref:System.Windows.Media.EllipseGeometry.Center%2A>
- [<span data-ttu-id="b0cf7-108">Animasyona Genel bakış</span><span class="sxs-lookup"><span data-stu-id="b0cf7-108">Animation Overview</span></span>](animation-overview.md)
- [<span data-ttu-id="b0cf7-109">Grafikler ve Multimedya</span><span class="sxs-lookup"><span data-stu-id="b0cf7-109">Graphics and Multimedia</span></span>](index.md)
- [<span data-ttu-id="b0cf7-110">Grafikler ile İlgili Nasıl Yapılır Konuları</span><span class="sxs-lookup"><span data-stu-id="b0cf7-110">Graphics How-to Topics</span></span>](graphics-how-to-topics.md)
- [<span data-ttu-id="b0cf7-111">Animasyon ve Zamanlama ile İlgili Nasıl Yapılır Konuları</span><span class="sxs-lookup"><span data-stu-id="b0cf7-111">Animation and Timing How-to Topics</span></span>](animation-and-timing-how-to-topics.md)
