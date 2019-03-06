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
ms.openlocfilehash: 04dbcfdb64525e6231ecf33c8ac5ecf2a2d2cb7e
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57357952"
---
# <a name="how-to-animate-the-position-of-an-object-by-using-pointanimation"></a><span data-ttu-id="ee529-102">Nasıl yapılır: PointAnimation Kullanarak bir Nesnenin Konumuna Animasyon Ekleme</span><span class="sxs-lookup"><span data-stu-id="ee529-102">How to: Animate the Position of an Object by Using PointAnimation</span></span>
<span data-ttu-id="ee529-103">Bu örnek nasıl kullanılacağını gösterir <xref:System.Windows.Media.Animation.PointAnimation> bir nesnenin animasyon uygulamak için sınıfı bir <xref:System.Windows.Shapes.Path>.</span><span class="sxs-lookup"><span data-stu-id="ee529-103">This example shows how to use the <xref:System.Windows.Media.Animation.PointAnimation> class to animate an object along a <xref:System.Windows.Shapes.Path>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ee529-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="ee529-104">Example</span></span>  
 <span data-ttu-id="ee529-105">Aşağıdaki örnek, bir elips taşır bir <xref:System.Windows.Shapes.Path> başka bir ekrandaki bir noktadan.</span><span class="sxs-lookup"><span data-stu-id="ee529-105">The following example moves an ellipse along a <xref:System.Windows.Shapes.Path> from one point on the screen to another.</span></span> <span data-ttu-id="ee529-106">Örnek konumunu canlandırır bir <xref:System.Windows.Media.EllipseGeometry> kullanarak <xref:System.Windows.Media.Animation.PointAnimation> animasyon uygulamak için <xref:System.Windows.Media.EllipseGeometry.Center%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="ee529-106">The example animates the position of an <xref:System.Windows.Media.EllipseGeometry> by using <xref:System.Windows.Media.Animation.PointAnimation> to animate the <xref:System.Windows.Media.EllipseGeometry.Center%2A> property.</span></span>  
  
 [!code-csharp[BasicAnimations_snip#PointAnimationWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/BasicAnimations_snip/CSharp/PointAnimationExample.cs#pointanimationwholepage)]
 [!code-vb[BasicAnimations_snip#PointAnimationWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BasicAnimations_snip/VisualBasic/PointAnimationExample.vb#pointanimationwholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="ee529-107">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ee529-107">See also</span></span>
- <xref:System.Windows.Media.Animation.PointAnimation>
- <xref:System.Windows.Shapes.Path>
- <xref:System.Windows.Media.EllipseGeometry>
- <xref:System.Windows.Media.EllipseGeometry.Center%2A>
- [<span data-ttu-id="ee529-108">Animasyona Genel bakış</span><span class="sxs-lookup"><span data-stu-id="ee529-108">Animation Overview</span></span>](animation-overview.md)
- [<span data-ttu-id="ee529-109">Grafikler ve Multimedya</span><span class="sxs-lookup"><span data-stu-id="ee529-109">Graphics and Multimedia</span></span>](index.md)
- [<span data-ttu-id="ee529-110">Grafikler ile ilgili nasıl yapılır konuları</span><span class="sxs-lookup"><span data-stu-id="ee529-110">Graphics How-to Topics</span></span>](graphics-how-to-topics.md)
- [<span data-ttu-id="ee529-111">Animasyon ve zamanlama ile ilgili nasıl yapılır konuları</span><span class="sxs-lookup"><span data-stu-id="ee529-111">Animation and Timing How-to Topics</span></span>](animation-and-timing-how-to-topics.md)
