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
ms.openlocfilehash: eeaea4732855155bf711912644f2f5b3f5a4f8d0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61651369"
---
# <a name="how-to-animate-the-position-or-color-of-a-gradient-stop"></a><span data-ttu-id="e85d4-102">Nasıl yapılır: Gradyan Duraklarının Konumuna veya Rengine Animasyon Ekleme</span><span class="sxs-lookup"><span data-stu-id="e85d4-102">How to: Animate the Position or Color of a Gradient Stop</span></span>
<span data-ttu-id="e85d4-103">Bu örnek, animasyon ekleme işlemi gösterilmektedir <xref:System.Windows.Media.GradientStop.Color%2A> ve <xref:System.Windows.Media.GradientStop.Offset%2A> , <xref:System.Windows.Media.GradientStop> nesneleri.</span><span class="sxs-lookup"><span data-stu-id="e85d4-103">This example shows how to animate the <xref:System.Windows.Media.GradientStop.Color%2A> and <xref:System.Windows.Media.GradientStop.Offset%2A> of <xref:System.Windows.Media.GradientStop> objects.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e85d4-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="e85d4-104">Example</span></span>  
 <span data-ttu-id="e85d4-105">Aşağıdaki örnek üç gradyan durağını içinde canlandırır bir <xref:System.Windows.Media.LinearGradientBrush>.</span><span class="sxs-lookup"><span data-stu-id="e85d4-105">The following example animates three gradient stops inside a <xref:System.Windows.Media.LinearGradientBrush>.</span></span> <span data-ttu-id="e85d4-106">Örnek üç animasyon, her biri farklı bir gradyan durağını canlandırır kullanır:</span><span class="sxs-lookup"><span data-stu-id="e85d4-106">The example uses three animations, each of which animates a different gradient stop:</span></span>  
  
- <span data-ttu-id="e85d4-107">İlk animasyon, bir <xref:System.Windows.Media.Animation.DoubleAnimation>, ilk gradyan durağının <xref:System.Windows.Media.GradientStop.Offset%2A> 0,0-1.0 0.0 yeniden.</span><span class="sxs-lookup"><span data-stu-id="e85d4-107">The first animation, a <xref:System.Windows.Media.Animation.DoubleAnimation>, animates the first gradient stop's <xref:System.Windows.Media.GradientStop.Offset%2A> from 0.0 to 1.0 and then back to 0.0.</span></span> <span data-ttu-id="e85d4-108">Sonuç olarak, ilk sağ tarafındaki dikdörtgenin sol taraftaki gradyan kaydırılır, renk ve ardından sol tarafa yeniden.</span><span class="sxs-lookup"><span data-stu-id="e85d4-108">As a result, the first color in the gradient shifts from the left side to the right side of the rectangle and then back to the left side.</span></span>  
  
- <span data-ttu-id="e85d4-109">İkinci animasyon bir <xref:System.Windows.Media.Animation.ColorAnimation>, ikinci gradyan durağının <xref:System.Windows.Media.GradientStop.Color%2A> gelen <xref:System.Windows.Media.Colors.Purple%2A> için <xref:System.Windows.Media.Colors.Yellow%2A> ve ardından yeniden <xref:System.Windows.Media.Colors.Purple%2A>.</span><span class="sxs-lookup"><span data-stu-id="e85d4-109">The second animation, a <xref:System.Windows.Media.Animation.ColorAnimation>, animates the second gradient stop's <xref:System.Windows.Media.GradientStop.Color%2A> from <xref:System.Windows.Media.Colors.Purple%2A> to <xref:System.Windows.Media.Colors.Yellow%2A> and then back to <xref:System.Windows.Media.Colors.Purple%2A>.</span></span> <span data-ttu-id="e85d4-110">Sonuç olarak, Orta Gradyan Rengi sarı ve mor dön mor değiştirir.</span><span class="sxs-lookup"><span data-stu-id="e85d4-110">As a result, the middle color in the gradient changes from purple to yellow and back to purple.</span></span>  
  
- <span data-ttu-id="e85d4-111">Üçüncü animasyon, başka bir <xref:System.Windows.Media.Animation.ColorAnimation>, üçüncü gradyan durağının saydamlığını canlandırır <xref:System.Windows.Media.GradientStop.Color%2A> göre -1 ve ardından yeniden.</span><span class="sxs-lookup"><span data-stu-id="e85d4-111">The third animation, another <xref:System.Windows.Media.Animation.ColorAnimation>, animates the opacity of the third gradient stop's <xref:System.Windows.Media.GradientStop.Color%2A> by -1 and then back.</span></span> <span data-ttu-id="e85d4-112">Sonuç olarak, üçüncü bir renk gradyanı, kaybolur ve daha sonra yeniden donuk olur.</span><span class="sxs-lookup"><span data-stu-id="e85d4-112">As a result, the third color in the gradient fades away and then becomes opaque again.</span></span>  
  
 [!code-csharp[BrushesIntroduction_snip#GraphicsMMGradientAnimationExamplesWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/GradientStopAnimationExample.cs#graphicsmmgradientanimationexampleswholepage)]
 [!code-vb[BrushesIntroduction_snip#GraphicsMMGradientAnimationExamplesWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/gradientstopanimationexample.vb#graphicsmmgradientanimationexampleswholepage)]
 [!code-xaml[BrushesIntroduction_snip#GraphicsMMGradientAnimationExamplesWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/GradientStopAnimationExample.xaml#graphicsmmgradientanimationexampleswholepage)]  
  
 <span data-ttu-id="e85d4-113">Bu örnekte rağmen bir <xref:System.Windows.Media.LinearGradientBrush>, aynı animasyon ekleme işlemidir <xref:System.Windows.Media.GradientStop> içindeki nesneleri bir <xref:System.Windows.Media.RadialGradientBrush>.</span><span class="sxs-lookup"><span data-stu-id="e85d4-113">Although this example uses a <xref:System.Windows.Media.LinearGradientBrush>, the process is the same for animating <xref:System.Windows.Media.GradientStop> objects inside a <xref:System.Windows.Media.RadialGradientBrush>.</span></span>  
  
 <span data-ttu-id="e85d4-114">Diğer örnekler için [Fırçalar örnek](https://go.microsoft.com/fwlink/?LinkID=159973).</span><span class="sxs-lookup"><span data-stu-id="e85d4-114">For additional examples, see the [Brushes Sample](https://go.microsoft.com/fwlink/?LinkID=159973).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e85d4-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e85d4-115">See also</span></span>

- <xref:System.Windows.Media.GradientStop>
- [<span data-ttu-id="e85d4-116">Animasyona Genel bakış</span><span class="sxs-lookup"><span data-stu-id="e85d4-116">Animation Overview</span></span>](animation-overview.md)
- [<span data-ttu-id="e85d4-117">Görsel Taslaklara Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="e85d4-117">Storyboards Overview</span></span>](storyboards-overview.md)
