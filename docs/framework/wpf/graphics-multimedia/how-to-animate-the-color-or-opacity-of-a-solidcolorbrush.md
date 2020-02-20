---
title: "Nasıl yapılır: SolidColorBrush'ın Rengine veya Opaklığına Animasyon Ekleme"
ms.date: 03/30/2017
helpviewer_keywords:
- SolidColorBrush [WPF], animating color of
- colors [WPF], animating
- opacity [WPF], animating
- animation [WPF], color of SolidColorBrush
- animation [WPF], opacity of SolidColorBrush
- SolidColorBrush [WPF], animating opacity of
ms.assetid: d9154354-843f-4713-bad1-35bb0ba6eaeb
ms.openlocfilehash: 08b85935e0cb1ababd1fb63b9d02518ea3fcfa17
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452889"
---
# <a name="how-to-animate-the-color-or-opacity-of-a-solidcolorbrush"></a><span data-ttu-id="91add-102">Nasıl yapılır: SolidColorBrush'ın Rengine veya Opaklığına Animasyon Ekleme</span><span class="sxs-lookup"><span data-stu-id="91add-102">How to: Animate the Color or Opacity of a SolidColorBrush</span></span>
<span data-ttu-id="91add-103">Bu örnek, bir <xref:System.Windows.Media.SolidColorBrush><xref:System.Windows.Media.SolidColorBrush.Color%2A> ve <xref:System.Windows.Media.Brush.Opacity%2A> nasıl hareketlendirileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="91add-103">This example shows how to animate the <xref:System.Windows.Media.SolidColorBrush.Color%2A> and <xref:System.Windows.Media.Brush.Opacity%2A> of a <xref:System.Windows.Media.SolidColorBrush>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="91add-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="91add-104">Example</span></span>  
 <span data-ttu-id="91add-105">Aşağıdaki örnek, bir <xref:System.Windows.Media.SolidColorBrush><xref:System.Windows.Media.SolidColorBrush.Color%2A> ve <xref:System.Windows.Media.Brush.Opacity%2A> hareketlendirmek için üç animasyon kullanır.</span><span class="sxs-lookup"><span data-stu-id="91add-105">The following example uses three animations to animate the <xref:System.Windows.Media.SolidColorBrush.Color%2A> and <xref:System.Windows.Media.Brush.Opacity%2A> of a <xref:System.Windows.Media.SolidColorBrush>.</span></span>  
  
- <span data-ttu-id="91add-106">İlk animasyon, bir <xref:System.Windows.Media.Animation.ColorAnimation>, fare dikdörtgene girdiğinde fırçanın rengini <xref:System.Windows.Media.Colors.Gray%2A> olarak değiştirir.</span><span class="sxs-lookup"><span data-stu-id="91add-106">The first animation, a <xref:System.Windows.Media.Animation.ColorAnimation>, changes the brush's color to <xref:System.Windows.Media.Colors.Gray%2A> when the mouse enters the rectangle.</span></span>  
  
- <span data-ttu-id="91add-107">Sonraki animasyon, başka bir <xref:System.Windows.Media.Animation.ColorAnimation>, fare dikdörtgenden çıktığında fırçanın rengini <xref:System.Windows.Media.Colors.Orange%2A> olarak değiştirir.</span><span class="sxs-lookup"><span data-stu-id="91add-107">The next animation, another <xref:System.Windows.Media.Animation.ColorAnimation>, changes the brush's color to <xref:System.Windows.Media.Colors.Orange%2A> when the mouse leaves the rectangle.</span></span>  
  
- <span data-ttu-id="91add-108">Son animasyon, bir <xref:System.Windows.Media.Animation.DoubleAnimation>, sol fare düğmesine basıldığında fırçanın saydamlığını 0,0 olarak değiştirir.</span><span class="sxs-lookup"><span data-stu-id="91add-108">The final animation, a <xref:System.Windows.Media.Animation.DoubleAnimation>, changes the brush's opacity to 0.0 when the left mouse button is pressed.</span></span>  
  
 [!code-csharp[brushanimations_snip#SolidColorBrushAnimationExample](~/samples/snippets/csharp/VS_Snippets_Wpf/brushanimations_snip/CSharp/SolidColorBrushExample.cs#solidcolorbrushanimationexample)]  
  
 <span data-ttu-id="91add-109">Farklı fırça türlerine nasıl animasyon ekleneceğini gösteren daha kapsamlı bir örnek için bkz. [fırçalar örneği](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Brushes).</span><span class="sxs-lookup"><span data-stu-id="91add-109">For a more complete sample, which shows how to animate different types of brushes, see the [Brushes Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Brushes).</span></span> <span data-ttu-id="91add-110">Animasyon hakkında daha fazla bilgi için bkz. [animasyona genel bakış](animation-overview.md).</span><span class="sxs-lookup"><span data-stu-id="91add-110">For more information about animation, see the [Animation Overview](animation-overview.md).</span></span>  
  
 <span data-ttu-id="91add-111">Diğer animasyon örnekleriyle tutarlılık için, bu örneğin kod sürümleri animasyonlarını uygulamak için bir <xref:System.Windows.Media.Animation.Storyboard> nesnesi kullanır.</span><span class="sxs-lookup"><span data-stu-id="91add-111">For consistency with other animation examples, the code versions of this example use a <xref:System.Windows.Media.Animation.Storyboard> object to apply their animations.</span></span> <span data-ttu-id="91add-112">Ancak, kodda tek bir animasyon uygulanırken, <xref:System.Windows.Media.Animation.Storyboard>kullanmak yerine <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> yönteminin kullanılması daha basittir.</span><span class="sxs-lookup"><span data-stu-id="91add-112">However, when applying a single animation in code, it's simpler to use the <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> method instead of using a <xref:System.Windows.Media.Animation.Storyboard>.</span></span> <span data-ttu-id="91add-113">Bir örnek için bkz. [görsel taslak kullanmadan özelliğe animasyon ekleme](how-to-animate-a-property-without-using-a-storyboard.md).</span><span class="sxs-lookup"><span data-stu-id="91add-113">For an example, see [Animate a Property Without Using a Storyboard](how-to-animate-a-property-without-using-a-storyboard.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="91add-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="91add-114">See also</span></span>

- [<span data-ttu-id="91add-115">Animasyona Genel bakış</span><span class="sxs-lookup"><span data-stu-id="91add-115">Animation Overview</span></span>](animation-overview.md)
- [<span data-ttu-id="91add-116">Görsel Taslaklara Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="91add-116">Storyboards Overview</span></span>](storyboards-overview.md)
- [<span data-ttu-id="91add-117">Fırçalar örneği</span><span class="sxs-lookup"><span data-stu-id="91add-117">Brushes Sample</span></span>](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Brushes)
