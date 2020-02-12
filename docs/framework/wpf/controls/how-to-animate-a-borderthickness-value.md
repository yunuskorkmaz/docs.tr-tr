---
title: 'Nasıl yapılır: BorderThickness Değerine Animasyon Ekleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- border thickness [WPF], animating changes to
- animation [WPF], changes to border thickness
ms.assetid: fd021978-f74b-4e7b-a7f7-3987dcad9e0f
ms.openlocfilehash: 4533ce6f2a1fe7243267ee8d638e2ad0a4f9cf3a
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/11/2020
ms.locfileid: "77124669"
---
# <a name="how-to-animate-a-borderthickness-value"></a><span data-ttu-id="7a102-102">Nasıl yapılır: BorderThickness Değerine Animasyon Ekleme</span><span class="sxs-lookup"><span data-stu-id="7a102-102">How to: Animate a BorderThickness Value</span></span>
<span data-ttu-id="7a102-103">Bu örnek, <xref:System.Windows.Media.Animation.ThicknessAnimation> sınıfını kullanarak bir kenarlık kalınlığına yapılan değişikliklere nasıl animasyon ekleneceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="7a102-103">This example shows how to animate changes to the thickness of a border by using the <xref:System.Windows.Media.Animation.ThicknessAnimation> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7a102-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="7a102-104">Example</span></span>  
 <span data-ttu-id="7a102-105">Aşağıdaki örnek, <xref:System.Windows.Media.Animation.ThicknessAnimation>kullanarak bir kenarlık kalınlığını hareketlendirir.</span><span class="sxs-lookup"><span data-stu-id="7a102-105">The following example animates the thickness of a border by using <xref:System.Windows.Media.Animation.ThicknessAnimation>.</span></span> <span data-ttu-id="7a102-106">Örnek, <xref:System.Windows.Controls.Border><xref:System.Windows.Controls.Border.BorderThickness%2A> özelliğini kullanır.</span><span class="sxs-lookup"><span data-stu-id="7a102-106">The example uses the <xref:System.Windows.Controls.Border.BorderThickness%2A> property of <xref:System.Windows.Controls.Border>.</span></span>  
  
 [!code-csharp[BasicAnimations_snip#ThicknessAnimationWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/BasicAnimations_snip/CSharp/ThicknessAnimationExample.cs#thicknessanimationwholepage)]
 [!code-vb[BasicAnimations_snip#ThicknessAnimationWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BasicAnimations_snip/VisualBasic/ThicknessAnimationExample.vb#thicknessanimationwholepage)]  
  
 <span data-ttu-id="7a102-107">Tüm örnek için bkz. [animasyon örnek Galerisi](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/AnimationExamples).</span><span class="sxs-lookup"><span data-stu-id="7a102-107">For the complete sample, see [Animation Example Gallery](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/AnimationExamples).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7a102-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7a102-108">See also</span></span>

- <xref:System.Windows.Media.Animation.ThicknessAnimation>
- <xref:System.Windows.Controls.Border.BorderThickness%2A>
- <xref:System.Windows.Controls.Border>
- [<span data-ttu-id="7a102-109">Animasyona Genel bakış</span><span class="sxs-lookup"><span data-stu-id="7a102-109">Animation Overview</span></span>](../graphics-multimedia/animation-overview.md)
- [<span data-ttu-id="7a102-110">Animasyon ve zamanlama ile ilgili nasıl yapılır konuları</span><span class="sxs-lookup"><span data-stu-id="7a102-110">Animation and Timing How-to Topics</span></span>](../graphics-multimedia/animation-and-timing-how-to-topics.md)
- [<span data-ttu-id="7a102-111">Anahtar Çerçeveler Kullanarak Kenarlık Kalınlığına Animasyon Ekleme</span><span class="sxs-lookup"><span data-stu-id="7a102-111">Animate the Thickness of a Border by Using Key Frames</span></span>](../graphics-multimedia/how-to-animate-the-thickness-of-a-border-by-using-key-frames.md)
