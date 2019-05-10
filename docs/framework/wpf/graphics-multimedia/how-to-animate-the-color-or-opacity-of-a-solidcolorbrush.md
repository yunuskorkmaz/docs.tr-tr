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
ms.openlocfilehash: 610a7c4879b4ffe54940e8bc744dcca0711e84d2
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64593394"
---
# <a name="how-to-animate-the-color-or-opacity-of-a-solidcolorbrush"></a><span data-ttu-id="b732b-102">Nasıl yapılır: SolidColorBrush'ın Rengine veya Opaklığına Animasyon Ekleme</span><span class="sxs-lookup"><span data-stu-id="b732b-102">How to: Animate the Color or Opacity of a SolidColorBrush</span></span>
<span data-ttu-id="b732b-103">Bu örnek, animasyon ekleme işlemi gösterilmektedir <xref:System.Windows.Media.SolidColorBrush.Color%2A> ve <xref:System.Windows.Media.Brush.Opacity%2A> , bir <xref:System.Windows.Media.SolidColorBrush>.</span><span class="sxs-lookup"><span data-stu-id="b732b-103">This example shows how to animate the <xref:System.Windows.Media.SolidColorBrush.Color%2A> and <xref:System.Windows.Media.Brush.Opacity%2A> of a <xref:System.Windows.Media.SolidColorBrush>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b732b-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="b732b-104">Example</span></span>  
 <span data-ttu-id="b732b-105">Aşağıdaki örnek, animasyon uygulamak için üç animasyonlarını kullanıp <xref:System.Windows.Media.SolidColorBrush.Color%2A> ve <xref:System.Windows.Media.Brush.Opacity%2A> , bir <xref:System.Windows.Media.SolidColorBrush>.</span><span class="sxs-lookup"><span data-stu-id="b732b-105">The following example uses three animations to animate the <xref:System.Windows.Media.SolidColorBrush.Color%2A> and <xref:System.Windows.Media.Brush.Opacity%2A> of a <xref:System.Windows.Media.SolidColorBrush>.</span></span>  
  
- <span data-ttu-id="b732b-106">İlk animasyon, bir <xref:System.Windows.Media.Animation.ColorAnimation>, fırça rengi değişir <xref:System.Windows.Media.Colors.Gray%2A> fare dikdörtgen girdiğinde.</span><span class="sxs-lookup"><span data-stu-id="b732b-106">The first animation, a <xref:System.Windows.Media.Animation.ColorAnimation>, changes the brush's color to <xref:System.Windows.Media.Colors.Gray%2A> when the mouse enters the rectangle.</span></span>  
  
- <span data-ttu-id="b732b-107">Sonraki animasyon, başka bir <xref:System.Windows.Media.Animation.ColorAnimation>, fırça rengi değişir <xref:System.Windows.Media.Colors.Orange%2A> fare dikdörtgen ayrıldığında.</span><span class="sxs-lookup"><span data-stu-id="b732b-107">The next animation, another <xref:System.Windows.Media.Animation.ColorAnimation>, changes the brush's color to <xref:System.Windows.Media.Colors.Orange%2A> when the mouse leaves the rectangle.</span></span>  
  
- <span data-ttu-id="b732b-108">Son animasyon, bir <xref:System.Windows.Media.Animation.DoubleAnimation>, farenin sol düğmesine basıldığında fırça opaklığını 0.0 değiştirir.</span><span class="sxs-lookup"><span data-stu-id="b732b-108">The final animation, a <xref:System.Windows.Media.Animation.DoubleAnimation>, changes the brush's opacity to 0.0 when the left mouse button is pressed.</span></span>  
  
 [!code-csharp[brushanimations_snip#SolidColorBrushAnimationExample](~/samples/snippets/csharp/VS_Snippets_Wpf/brushanimations_snip/CSharp/SolidColorBrushExample.cs#solidcolorbrushanimationexample)]  
  
 <span data-ttu-id="b732b-109">Farklı türde Fırçalar animasyonunu gösteren daha eksiksiz bir örnek için bkz. [Fırçalar örnek](https://go.microsoft.com/fwlink/?LinkID=159973).</span><span class="sxs-lookup"><span data-stu-id="b732b-109">For a more complete sample, which shows how to animate different types of brushes, see the [Brushes Sample](https://go.microsoft.com/fwlink/?LinkID=159973).</span></span> <span data-ttu-id="b732b-110">Animasyon hakkında daha fazla bilgi için bkz. [animasyona genel bakış](animation-overview.md).</span><span class="sxs-lookup"><span data-stu-id="b732b-110">For more information about animation, see the [Animation Overview](animation-overview.md).</span></span>  
  
 <span data-ttu-id="b732b-111">Diğer animasyon örnekleriyle tutarlılık sağlamak için bu örnek kod sürümleri kullanan bir <xref:System.Windows.Media.Animation.Storyboard> kendi animasyon uygulamak için nesne.</span><span class="sxs-lookup"><span data-stu-id="b732b-111">For consistency with other animation examples, the code versions of this example use a <xref:System.Windows.Media.Animation.Storyboard> object to apply their animations.</span></span> <span data-ttu-id="b732b-112">Ancak, tek bir animasyonu kod uygularken kullanmak daha basit olduğu <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> yöntemi kullanmak yerine bir <xref:System.Windows.Media.Animation.Storyboard>.</span><span class="sxs-lookup"><span data-stu-id="b732b-112">However, when applying a single animation in code, it's simpler to use the <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> method instead of using a <xref:System.Windows.Media.Animation.Storyboard>.</span></span> <span data-ttu-id="b732b-113">Bir örnek için bkz. [özelliği olmadan kullanarak bir görsel taslak animasyon](how-to-animate-a-property-without-using-a-storyboard.md).</span><span class="sxs-lookup"><span data-stu-id="b732b-113">For an example, see [Animate a Property Without Using a Storyboard](how-to-animate-a-property-without-using-a-storyboard.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b732b-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b732b-114">See also</span></span>

- [<span data-ttu-id="b732b-115">Animasyona Genel bakış</span><span class="sxs-lookup"><span data-stu-id="b732b-115">Animation Overview</span></span>](animation-overview.md)
- [<span data-ttu-id="b732b-116">Görsel Taslaklara Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="b732b-116">Storyboards Overview</span></span>](storyboards-overview.md)
- [<span data-ttu-id="b732b-117">Fırça örneği</span><span class="sxs-lookup"><span data-stu-id="b732b-117">Brushes Sample</span></span>](https://go.microsoft.com/fwlink/?LinkID=159973)
