---
title: 'Nasıl yapılır: Bir Öğenin Yerinde Dönmesini Sağlama'
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [WPF], spinning elements
- spinning elements [WPF]
ms.assetid: 1f011976-8b07-4c31-9faf-019e0ddaa24c
ms.openlocfilehash: a1b515822391de08ec8ed8ff0ff1f0086874dc02
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/21/2020
ms.locfileid: "80112082"
---
# <a name="how-to-make-an-element-spin-in-place"></a><span data-ttu-id="06541-102">Nasıl yapılır: Bir Öğenin Yerinde Dönmesini Sağlama</span><span class="sxs-lookup"><span data-stu-id="06541-102">How to: Make an Element Spin in Place</span></span>
<span data-ttu-id="06541-103">Bu örnek, bir öğenin a <xref:System.Windows.Media.RotateTransform> ve <xref:System.Windows.Media.Animation.DoubleAnimation>a kullanarak nasıl döndürülür hale getirilebildiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="06541-103">This example shows how to make an element spin by using a <xref:System.Windows.Media.RotateTransform> and a <xref:System.Windows.Media.Animation.DoubleAnimation>.</span></span>  
  
 <span data-ttu-id="06541-104">Aşağıdaki örnek öğenin <xref:System.Windows.Media.RotateTransform> <xref:System.Windows.UIElement.RenderTransform%2A> özelliği ne uygulanır.</span><span class="sxs-lookup"><span data-stu-id="06541-104">The following example applies the <xref:System.Windows.Media.RotateTransform> to the <xref:System.Windows.UIElement.RenderTransform%2A> property of the element.</span></span> <span data-ttu-id="06541-105">Örnek, a'yı <xref:System.Windows.Media.Animation.DoubleAnimation> <xref:System.Windows.Media.RotateTransform.Angle%2A> animasyona vermek <xref:System.Windows.Media.RotateTransform>için kullanır.</span><span class="sxs-lookup"><span data-stu-id="06541-105">The example uses a <xref:System.Windows.Media.Animation.DoubleAnimation> to animate the <xref:System.Windows.Media.RotateTransform.Angle%2A> of the <xref:System.Windows.Media.RotateTransform>.</span></span> <span data-ttu-id="06541-106">Öğeyi yerinde döndürmek için, örnek <xref:System.Windows.UIElement.RenderTransformOrigin%2A> öğenin özelliğini noktaya ayarlar (0,5, 0,5).</span><span class="sxs-lookup"><span data-stu-id="06541-106">To make the element spin in place, the example sets the <xref:System.Windows.UIElement.RenderTransformOrigin%2A> property of the element to the point (0.5, 0.5).</span></span>  
  
## <a name="example"></a><span data-ttu-id="06541-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="06541-107">Example</span></span>  
 [!code-xaml[transformanimations_snip#11](~/samples/snippets/xaml/VS_Snippets_Wpf/transformanimations_snip/XAML/RotateAboutCenterExample.xaml#11)]  
  
 <span data-ttu-id="06541-108">Daha fazla dönüşüm örneği içeren tam örnek için [bkz.](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/2DTransforms)</span><span class="sxs-lookup"><span data-stu-id="06541-108">For the complete sample, which includes more transformation examples, see [2D Transforms Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/2DTransforms).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="06541-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="06541-109">See also</span></span>

- [<span data-ttu-id="06541-110">Animasyona Genel bakış</span><span class="sxs-lookup"><span data-stu-id="06541-110">Animation Overview</span></span>](animation-overview.md)
- [<span data-ttu-id="06541-111">Dönüşümlere Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="06541-111">Transforms Overview</span></span>](transforms-overview.md)
