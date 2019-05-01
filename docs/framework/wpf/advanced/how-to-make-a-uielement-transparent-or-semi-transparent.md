---
title: 'Nasıl yapılır: Saydam veya Yarı Saydam UIElement Oluşturma'
ms.date: 03/30/2017
helpviewer_keywords:
- UIElements [WPF], transparency
- opacity [WPF], of UIElements
- transparency of UIElements [WPF]
- UIElements [WPF], opacity
ms.assetid: a49fc8d6-7b32-4f28-9122-39b632a19b4b
ms.openlocfilehash: 1de9a7e11fee241ecb71242e9808e77b7e5e63b0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61942876"
---
# <a name="how-to-make-a-uielement-transparent-or-semi-transparent"></a><span data-ttu-id="ddf67-102">Nasıl yapılır: Saydam veya Yarı Saydam UIElement Oluşturma</span><span class="sxs-lookup"><span data-stu-id="ddf67-102">How to: Make a UIElement Transparent or Semi-Transparent</span></span>
<span data-ttu-id="ddf67-103">Bu örnek nasıl yapılacağını gösteren bir <xref:System.Windows.UIElement> saydam veya yarı saydam.</span><span class="sxs-lookup"><span data-stu-id="ddf67-103">This example shows how to make a <xref:System.Windows.UIElement> transparent or semi-transparent.</span></span> <span data-ttu-id="ddf67-104">Öğeyi saydam veya yarı saydam yapmak için ayarlamanız, <xref:System.Windows.UIElement.Opacity%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="ddf67-104">To make an element transparent or semi-transparent, you set its <xref:System.Windows.UIElement.Opacity%2A> property.</span></span> <span data-ttu-id="ddf67-105">Değerini `0.0` öğe değeri tamamen saydam yapar `1.0` öğe tamamen opak yapar.</span><span class="sxs-lookup"><span data-stu-id="ddf67-105">A value of `0.0` makes the element completely transparent, while a value of `1.0` makes the element completely opaque.</span></span> <span data-ttu-id="ddf67-106">Değerini `0.5` öğe % 50 opak vb. sağlar.</span><span class="sxs-lookup"><span data-stu-id="ddf67-106">A value of `0.5` makes the element 50% opaque, and so on.</span></span> <span data-ttu-id="ddf67-107">Bir öğenin <xref:System.Windows.UIElement.Opacity%2A> ayarlanır `1.0` varsayılan olarak.</span><span class="sxs-lookup"><span data-stu-id="ddf67-107">An element's <xref:System.Windows.UIElement.Opacity%2A> is set to `1.0` by default.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ddf67-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="ddf67-108">Example</span></span>  
 <span data-ttu-id="ddf67-109">Aşağıdaki örnek kümeleri <xref:System.Windows.UIElement.Opacity%2A> bir düğmenin `0.25`ve içeriğinin (Bu durumda düğmenin metni) % 25 donuk yapma.</span><span class="sxs-lookup"><span data-stu-id="ddf67-109">The following example sets the <xref:System.Windows.UIElement.Opacity%2A> of a button to `0.25`, making it and its contents (in this case, the button's text) 25% opaque.</span></span>  
  
 [!code-xaml[brushsamples_snip#2](~/samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/OpacityExample.xaml#2)]  
  
 [!code-csharp[brushsamples_procedural_snip#2](~/samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_procedural_snip/CSharp/OpacityExample.cs#2)]  
  
 <span data-ttu-id="ddf67-110">Bir öğenin içeriğini kendi varsa <xref:System.Windows.UIElement.Opacity%2A> ayarları, bu değerleri içeren öğelerle çarpılır <xref:System.Windows.UIElement.Opacity%2A>.</span><span class="sxs-lookup"><span data-stu-id="ddf67-110">If an element's contents have their own <xref:System.Windows.UIElement.Opacity%2A> settings, those values are multiplied against the containing elements <xref:System.Windows.UIElement.Opacity%2A>.</span></span>  
  
 <span data-ttu-id="ddf67-111">Aşağıdaki örnek, bir düğmenin ayarlar <xref:System.Windows.UIElement.Opacity%2A> için `0.25`ve <xref:System.Windows.UIElement.Opacity%2A> , bir <xref:System.Windows.Controls.Image> düğmede bulunan denetim `0.5`.</span><span class="sxs-lookup"><span data-stu-id="ddf67-111">The following example sets a button's <xref:System.Windows.UIElement.Opacity%2A> to `0.25`, and the <xref:System.Windows.UIElement.Opacity%2A> of an <xref:System.Windows.Controls.Image> control contained with in the button to `0.5`.</span></span> <span data-ttu-id="ddf67-112">Sonuç olarak, görüntü %12,5 donuk görünür: 0.25 \* 0.5 = 0.125.</span><span class="sxs-lookup"><span data-stu-id="ddf67-112">As a result, the image appears 12.5% opaque: 0.25 \* 0.5 = 0.125.</span></span>  
  
 [!code-xaml[brushsamples_snip#3](~/samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/OpacityExample.xaml#3)]  
  
 [!code-csharp[brushsamples_procedural_snip#3](~/samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_procedural_snip/CSharp/OpacityExample.cs#3)]  
  
 <span data-ttu-id="ddf67-113">Bir öğenin denetlemek için başka bir yolu opaklığını ayarlamaktır <xref:System.Windows.Media.Brush> , öğe boyar.</span><span class="sxs-lookup"><span data-stu-id="ddf67-113">Another way to control the opacity of an element is to set the opacity of the <xref:System.Windows.Media.Brush> that paints the element.</span></span> <span data-ttu-id="ddf67-114">Bu yaklaşım bir öğe bölümlerini opaklığını seçmeli olarak değiştirmeyi etkinleştirir ve öğenin yerine performans avantajı sağlar <xref:System.Windows.UIElement.Opacity%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="ddf67-114">This approach enables you to selectively alter the opacity of portions of an element, and provides performance benefits over using the element's <xref:System.Windows.UIElement.Opacity%2A> property.</span></span> <span data-ttu-id="ddf67-115">Aşağıdaki örnek kümeleri <xref:System.Windows.Media.Brush.Opacity%2A> , bir <xref:System.Windows.Media.SolidColorBrush> düğmenin boyamak için kullanılan <xref:System.Windows.Controls.Control.Background%2A> ayarlanır `0.25`.</span><span class="sxs-lookup"><span data-stu-id="ddf67-115">The following example sets the <xref:System.Windows.Media.Brush.Opacity%2A> of a <xref:System.Windows.Media.SolidColorBrush> used to paint the button's <xref:System.Windows.Controls.Control.Background%2A> is set to `0.25`.</span></span> <span data-ttu-id="ddf67-116">Sonuç olarak, % 25 opak fırçanın arka plan olur, ancak % 100 (düğmenin metni) içeriğini kalır.</span><span class="sxs-lookup"><span data-stu-id="ddf67-116">As a result, the brush's background is 25% opaque, but its contents (the button's text) remain 100% opaque.</span></span>  
  
 [!code-xaml[brushsamples_snip#4](~/samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/OpacityExample.xaml#4)]  
  
 [!code-csharp[brushsamples_procedural_snip#4](~/samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_procedural_snip/CSharp/OpacityExample.cs#4)]  
  
 <span data-ttu-id="ddf67-117">Ayrıca, tek tek renkler içinde bir fırça opaklığını denetleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ddf67-117">You may also control the opacity of individual colors within a brush.</span></span> <span data-ttu-id="ddf67-118">Renkler ve Fırçalar hakkında daha fazla bilgi için bkz. [düz renkler ve gradyanlar genel bakış boyama](../graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md).</span><span class="sxs-lookup"><span data-stu-id="ddf67-118">For more information about colors and brushes, see [Painting with Solid Colors and Gradients Overview](../graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md).</span></span> <span data-ttu-id="ddf67-119">Bir öğenin opaklık nasıl yapıldığını gösteren bir örnek için bkz [bir öğe veya fırça opaklığına](../graphics-multimedia/how-to-animate-the-opacity-of-an-element-or-brush.md).</span><span class="sxs-lookup"><span data-stu-id="ddf67-119">For an example showing how to animate an element's opacity, see [Animate the Opacity of an Element or Brush](../graphics-multimedia/how-to-animate-the-opacity-of-an-element-or-brush.md).</span></span>
