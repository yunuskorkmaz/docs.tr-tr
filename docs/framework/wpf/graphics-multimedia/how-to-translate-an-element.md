---
title: 'Nasıl yapılır: Bir Öğeyi Çevirme'
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [WPF], translations
ms.assetid: 461c8273-15df-42f6-8672-89ba22887cc0
ms.openlocfilehash: addff0e22fb3f27ea924887809c0635aeb3ad67d
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/21/2020
ms.locfileid: "80111978"
---
# <a name="how-to-translate-an-element"></a><span data-ttu-id="50492-102">Nasıl yapılır: Bir Öğeyi Çevirme</span><span class="sxs-lookup"><span data-stu-id="50492-102">How to: Translate an Element</span></span>
<span data-ttu-id="50492-103">Bu örnek, bir öğeyi kullanarak nasıl <xref:System.Windows.Media.TranslateTransform>çevrilecek (taşınır) gösterir.</span><span class="sxs-lookup"><span data-stu-id="50492-103">This example shows how to translate (move) an element by using a <xref:System.Windows.Media.TranslateTransform>.</span></span>  
  
 <span data-ttu-id="50492-104">Sınıf, <xref:System.Windows.Media.TranslateTransform> özellikle mutlak konumlandırmayı desteklemeyen panellerin içindeki öğeleri taşımak için kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="50492-104">The <xref:System.Windows.Media.TranslateTransform> class is especially useful for moving elements inside panels that do not support absolute positioning.</span></span> <span data-ttu-id="50492-105">Örneğin, bir öğenin <xref:System.Windows.Media.TranslateTransform> <xref:System.Windows.UIElement.RenderTransform%2A> özelliğine a uygulayarak, bir <xref:System.Windows.Controls.StackPanel> öğeyi <xref:System.Windows.Controls.DockPanel>veya .</span><span class="sxs-lookup"><span data-stu-id="50492-105">For example, by applying a <xref:System.Windows.Media.TranslateTransform> to the <xref:System.Windows.UIElement.RenderTransform%2A> property of an element, you can move an element within a <xref:System.Windows.Controls.StackPanel> or <xref:System.Windows.Controls.DockPanel>.</span></span>  
  
 <span data-ttu-id="50492-106">Öğeyi <xref:System.Windows.Media.TranslateTransform.X%2A> x <xref:System.Windows.Media.TranslateTransform> ekseni boyunca taşımak için pikselolarak miktarı belirtmek için öğenin özelliğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="50492-106">Use the <xref:System.Windows.Media.TranslateTransform.X%2A> property of the <xref:System.Windows.Media.TranslateTransform> to specify the amount, in pixels, to move the element along the x-axis.</span></span> <span data-ttu-id="50492-107">Öğeyi <xref:System.Windows.Media.TranslateTransform.Y%2A> y ekseni boyunca taşımak için piksellerde miktarı belirtmek için özelliği kullanın.</span><span class="sxs-lookup"><span data-stu-id="50492-107">Use the <xref:System.Windows.Media.TranslateTransform.Y%2A> property to specify the amount, in pixels, to move the element along the y-axis.</span></span> <span data-ttu-id="50492-108">Son olarak, <xref:System.Windows.Media.TranslateTransform> öğenin <xref:System.Windows.UIElement.RenderTransform%2A> özelliğine uygulayın.</span><span class="sxs-lookup"><span data-stu-id="50492-108">Finally, apply the <xref:System.Windows.Media.TranslateTransform> to the <xref:System.Windows.UIElement.RenderTransform%2A> property of the element.</span></span>  
  
 <span data-ttu-id="50492-109">Aşağıdaki örnekte, <xref:System.Windows.Media.TranslateTransform> bir öğeyi 50 piksel sağa ve 50 piksel aşağıya taşımak için a kullanır.</span><span class="sxs-lookup"><span data-stu-id="50492-109">The following example uses a <xref:System.Windows.Media.TranslateTransform> to move an element 50 pixels to the right and 50 pixels down.</span></span>  
  
## <a name="example"></a><span data-ttu-id="50492-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="50492-110">Example</span></span>  
 [!code-xaml[transformsSample#53](~/samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/TranslateTransformExample.xaml#53)]  
  
 <span data-ttu-id="50492-111">Tam örnek için [2B Dönüşümler Örneği'ne](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/2DTransforms)bakın.</span><span class="sxs-lookup"><span data-stu-id="50492-111">For the complete sample, see [2D Transforms Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/2DTransforms).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="50492-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="50492-112">See also</span></span>

- [<span data-ttu-id="50492-113">Dönüşümlere Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="50492-113">Transforms Overview</span></span>](transforms-overview.md)
