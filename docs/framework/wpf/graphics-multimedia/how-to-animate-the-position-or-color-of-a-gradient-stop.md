---
title: 'Nasıl yapılır: Gradyan Duraklarının Konumuna veya Rengine Animasyon Ekleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- position [WPF], animating
- animation [WPF], position of GradientStop objects
- GradientStop objects [WPF], animating color of
- colors [WPF], animating
- animation [WPF], color of GradientStop objects
- GradientStop objects [WPF], animating position of
ms.assetid: 6f5b8b47-6c32-4b8e-98ee-fdf6515ec843
ms.openlocfilehash: aeae33f5f3c8016808988f58d61969e9b6f05039
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452850"
---
# <a name="how-to-animate-the-position-or-color-of-a-gradient-stop"></a><span data-ttu-id="5e814-102">Nasıl yapılır: Gradyan Duraklarının Konumuna veya Rengine Animasyon Ekleme</span><span class="sxs-lookup"><span data-stu-id="5e814-102">How to: Animate the Position or Color of a Gradient Stop</span></span>
<span data-ttu-id="5e814-103">Bu örnek, <xref:System.Windows.Media.GradientStop> nesnelerinin <xref:System.Windows.Media.GradientStop.Color%2A> ve <xref:System.Windows.Media.GradientStop.Offset%2A> nasıl hareketlendirileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="5e814-103">This example shows how to animate the <xref:System.Windows.Media.GradientStop.Color%2A> and <xref:System.Windows.Media.GradientStop.Offset%2A> of <xref:System.Windows.Media.GradientStop> objects.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5e814-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="5e814-104">Example</span></span>  
 <span data-ttu-id="5e814-105">Aşağıdaki örnek, <xref:System.Windows.Media.LinearGradientBrush>içinde üç gradyan durağını hareketlendirir.</span><span class="sxs-lookup"><span data-stu-id="5e814-105">The following example animates three gradient stops inside a <xref:System.Windows.Media.LinearGradientBrush>.</span></span> <span data-ttu-id="5e814-106">Örnek, her biri farklı bir gradyan durağını canlandırarak üç animasyon kullanır:</span><span class="sxs-lookup"><span data-stu-id="5e814-106">The example uses three animations, each of which animates a different gradient stop:</span></span>  
  
- <span data-ttu-id="5e814-107">İlk animasyon, bir <xref:System.Windows.Media.Animation.DoubleAnimation>, ilk gradyan durağının <xref:System.Windows.Media.GradientStop.Offset%2A> 0,0 ' den 1,0 ' ye ve ardından 0,0 ' a geri hareketlenir.</span><span class="sxs-lookup"><span data-stu-id="5e814-107">The first animation, a <xref:System.Windows.Media.Animation.DoubleAnimation>, animates the first gradient stop's <xref:System.Windows.Media.GradientStop.Offset%2A> from 0.0 to 1.0 and then back to 0.0.</span></span> <span data-ttu-id="5e814-108">Sonuç olarak, gradyanın ilk rengi, dikdörtgenin sol tarafından sağ tarafına ve ardından sol tarafa geri kayar.</span><span class="sxs-lookup"><span data-stu-id="5e814-108">As a result, the first color in the gradient shifts from the left side to the right side of the rectangle and then back to the left side.</span></span>  
  
- <span data-ttu-id="5e814-109">İkinci animasyon, bir <xref:System.Windows.Media.Animation.ColorAnimation>, ikinci gradyan durağının <xref:System.Windows.Media.GradientStop.Color%2A> <xref:System.Windows.Media.Colors.Purple%2A> <xref:System.Windows.Media.Colors.Yellow%2A> ve daha sonra <xref:System.Windows.Media.Colors.Purple%2A>'e geri hareketlendirir.</span><span class="sxs-lookup"><span data-stu-id="5e814-109">The second animation, a <xref:System.Windows.Media.Animation.ColorAnimation>, animates the second gradient stop's <xref:System.Windows.Media.GradientStop.Color%2A> from <xref:System.Windows.Media.Colors.Purple%2A> to <xref:System.Windows.Media.Colors.Yellow%2A> and then back to <xref:System.Windows.Media.Colors.Purple%2A>.</span></span> <span data-ttu-id="5e814-110">Sonuç olarak, gradyanın ortadaki rengi mor ve mor olarak değişir.</span><span class="sxs-lookup"><span data-stu-id="5e814-110">As a result, the middle color in the gradient changes from purple to yellow and back to purple.</span></span>  
  
- <span data-ttu-id="5e814-111">Üçüncü animasyon, başka bir <xref:System.Windows.Media.Animation.ColorAnimation>, üçüncü gradyan durağının <xref:System.Windows.Media.GradientStop.Color%2A> saydamlığını-1 ve sonra geri hareketlendirir.</span><span class="sxs-lookup"><span data-stu-id="5e814-111">The third animation, another <xref:System.Windows.Media.Animation.ColorAnimation>, animates the opacity of the third gradient stop's <xref:System.Windows.Media.GradientStop.Color%2A> by -1 and then back.</span></span> <span data-ttu-id="5e814-112">Sonuç olarak, gradyanın üçüncü rengi kaybolur ve sonra yeniden donuk hale gelir.</span><span class="sxs-lookup"><span data-stu-id="5e814-112">As a result, the third color in the gradient fades away and then becomes opaque again.</span></span>  
  
 [!code-csharp[BrushesIntroduction_snip#GraphicsMMGradientAnimationExamplesWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/GradientStopAnimationExample.cs#graphicsmmgradientanimationexampleswholepage)]
 [!code-vb[BrushesIntroduction_snip#GraphicsMMGradientAnimationExamplesWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/gradientstopanimationexample.vb#graphicsmmgradientanimationexampleswholepage)]
 [!code-xaml[BrushesIntroduction_snip#GraphicsMMGradientAnimationExamplesWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/GradientStopAnimationExample.xaml#graphicsmmgradientanimationexampleswholepage)]  
  
 <span data-ttu-id="5e814-113">Bu örnek bir <xref:System.Windows.Media.LinearGradientBrush>kullansa da, işlem <xref:System.Windows.Media.RadialGradientBrush>içindeki <xref:System.Windows.Media.GradientStop> nesneleri hareketlendirmek için aynıdır.</span><span class="sxs-lookup"><span data-stu-id="5e814-113">Although this example uses a <xref:System.Windows.Media.LinearGradientBrush>, the process is the same for animating <xref:System.Windows.Media.GradientStop> objects inside a <xref:System.Windows.Media.RadialGradientBrush>.</span></span>  
  
 <span data-ttu-id="5e814-114">Daha fazla örnek için bkz. [fırçalar örneği](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Brushes).</span><span class="sxs-lookup"><span data-stu-id="5e814-114">For additional examples, see the [Brushes Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Brushes).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5e814-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5e814-115">See also</span></span>

- <xref:System.Windows.Media.GradientStop>
- [<span data-ttu-id="5e814-116">Animasyona Genel bakış</span><span class="sxs-lookup"><span data-stu-id="5e814-116">Animation Overview</span></span>](animation-overview.md)
- [<span data-ttu-id="5e814-117">Görsel Taslaklara Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="5e814-117">Storyboards Overview</span></span>](storyboards-overview.md)
