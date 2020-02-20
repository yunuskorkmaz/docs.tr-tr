---
title: 'Nasıl yapılır: Bir Öğenin Yerinde Dönmesini Sağlama'
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [WPF], spinning elements
- spinning elements [WPF]
ms.assetid: 1f011976-8b07-4c31-9faf-019e0ddaa24c
ms.openlocfilehash: 2e72389a11e48629c2763fcbd9f7b1945ffff5dd
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452798"
---
# <a name="how-to-make-an-element-spin-in-place"></a><span data-ttu-id="2253b-102">Nasıl yapılır: Bir Öğenin Yerinde Dönmesini Sağlama</span><span class="sxs-lookup"><span data-stu-id="2253b-102">How to: Make an Element Spin in Place</span></span>
<span data-ttu-id="2253b-103">Bu örnek, bir <xref:System.Windows.Media.RotateTransform> ve <xref:System.Windows.Media.Animation.DoubleAnimation>kullanarak nasıl bir öğe dönmesi yapılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="2253b-103">This example shows how to make an element spin by using a <xref:System.Windows.Media.RotateTransform> and a <xref:System.Windows.Media.Animation.DoubleAnimation>.</span></span>  
  
 <span data-ttu-id="2253b-104">Aşağıdaki örnek, <xref:System.Windows.Media.RotateTransform> öğesinin <xref:System.Windows.UIElement.RenderTransform%2A> özelliğine uygular.</span><span class="sxs-lookup"><span data-stu-id="2253b-104">The following example applies the <xref:System.Windows.Media.RotateTransform> to the <xref:System.Windows.UIElement.RenderTransform%2A> property of the element.</span></span> <span data-ttu-id="2253b-105">Örnek, <xref:System.Windows.Media.RotateTransform><xref:System.Windows.Media.RotateTransform.Angle%2A> hareketlendirmek için bir <xref:System.Windows.Media.Animation.DoubleAnimation> kullanır.</span><span class="sxs-lookup"><span data-stu-id="2253b-105">The example uses a <xref:System.Windows.Media.Animation.DoubleAnimation> to animate the <xref:System.Windows.Media.RotateTransform.Angle%2A> of the <xref:System.Windows.Media.RotateTransform>.</span></span> <span data-ttu-id="2253b-106">Öğe dönmesini yerine getirmek için, örnek, öğesinin <xref:System.Windows.UIElement.RenderTransformOrigin%2A> özelliğini nokta (0,5, 0,5) olarak ayarlar.</span><span class="sxs-lookup"><span data-stu-id="2253b-106">To make the element spin in place, the example sets the <xref:System.Windows.UIElement.RenderTransformOrigin%2A> property of the element to the point (0.5, 0.5).</span></span>  
  
## <a name="example"></a><span data-ttu-id="2253b-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="2253b-107">Example</span></span>  
 [!code-xaml[transformanimations_snip#11](~/samples/snippets/xaml/VS_Snippets_Wpf/transformanimations_snip/XAML/RotateAboutCenterExample.xaml#11)]  
  
 <span data-ttu-id="2253b-108">Daha fazla dönüştürme örneği içeren tam örnek için bkz. [2-b dönüşümler örneği](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/2DTransforms).</span><span class="sxs-lookup"><span data-stu-id="2253b-108">For the complete sample, which includes more transformation examples, see [2-D Transforms Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/2DTransforms).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2253b-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2253b-109">See also</span></span>

- [<span data-ttu-id="2253b-110">Animasyona Genel bakış</span><span class="sxs-lookup"><span data-stu-id="2253b-110">Animation Overview</span></span>](animation-overview.md)
- [<span data-ttu-id="2253b-111">Dönüşümlere Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="2253b-111">Transforms Overview</span></span>](transforms-overview.md)
