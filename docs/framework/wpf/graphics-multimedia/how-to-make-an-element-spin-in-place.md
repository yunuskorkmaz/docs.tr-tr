---
title: 'Nasıl yapılır: Bir Öğenin Yerinde Dönmesini Sağlama'
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [WPF], spinning elements
- spinning elements [WPF]
ms.assetid: 1f011976-8b07-4c31-9faf-019e0ddaa24c
ms.openlocfilehash: 2eaca5ba75eb8ac2eeb375a177c08659a65af2db
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57371508"
---
# <a name="how-to-make-an-element-spin-in-place"></a><span data-ttu-id="fd08a-102">Nasıl yapılır: Bir Öğenin Yerinde Dönmesini Sağlama</span><span class="sxs-lookup"><span data-stu-id="fd08a-102">How to: Make an Element Spin in Place</span></span>
<span data-ttu-id="fd08a-103">Bu örnek nasıl döndürme kullanarak bir öğeyi gösterir bir <xref:System.Windows.Media.RotateTransform> ve <xref:System.Windows.Media.Animation.DoubleAnimation>.</span><span class="sxs-lookup"><span data-stu-id="fd08a-103">This example shows how to make an element spin by using a <xref:System.Windows.Media.RotateTransform> and a <xref:System.Windows.Media.Animation.DoubleAnimation>.</span></span>  
  
 <span data-ttu-id="fd08a-104">Aşağıdaki örnek geçerli <xref:System.Windows.Media.RotateTransform> için <xref:System.Windows.UIElement.RenderTransform%2A> öğesinin özelliği.</span><span class="sxs-lookup"><span data-stu-id="fd08a-104">The following example applies the <xref:System.Windows.Media.RotateTransform> to the <xref:System.Windows.UIElement.RenderTransform%2A> property of the element.</span></span> <span data-ttu-id="fd08a-105">Örnekte bir <xref:System.Windows.Media.Animation.DoubleAnimation> animasyon uygulamak için <xref:System.Windows.Media.RotateTransform.Angle%2A> , <xref:System.Windows.Media.RotateTransform>.</span><span class="sxs-lookup"><span data-stu-id="fd08a-105">The example uses a <xref:System.Windows.Media.Animation.DoubleAnimation> to animate the <xref:System.Windows.Media.RotateTransform.Angle%2A> of the <xref:System.Windows.Media.RotateTransform>.</span></span> <span data-ttu-id="fd08a-106">Yerinde öğe yapmak için örnekte <xref:System.Windows.UIElement.RenderTransformOrigin%2A> noktasına (0,5, 0,5) öğesinin özelliği.</span><span class="sxs-lookup"><span data-stu-id="fd08a-106">To make the element spin in place, the example sets the <xref:System.Windows.UIElement.RenderTransformOrigin%2A> property of the element to the point (0.5, 0.5).</span></span>  
  
## <a name="example"></a><span data-ttu-id="fd08a-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="fd08a-107">Example</span></span>  
 [!code-xaml[transformanimations_snip#11](~/samples/snippets/xaml/VS_Snippets_Wpf/transformanimations_snip/XAML/RotateAboutCenterExample.xaml#11)]  
  
 <span data-ttu-id="fd08a-108">Daha fazla dönüşüm örnekleri içeren, tam örnek için bkz [2B dönüşüm örnek](https://go.microsoft.com/fwlink/?LinkID=158252).</span><span class="sxs-lookup"><span data-stu-id="fd08a-108">For the complete sample, which includes more transformation examples, see [2-D Transforms Sample](https://go.microsoft.com/fwlink/?LinkID=158252).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fd08a-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fd08a-109">See also</span></span>
- [<span data-ttu-id="fd08a-110">Animasyona Genel bakış</span><span class="sxs-lookup"><span data-stu-id="fd08a-110">Animation Overview</span></span>](animation-overview.md)
- [<span data-ttu-id="fd08a-111">Dönüşümlere Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="fd08a-111">Transforms Overview</span></span>](transforms-overview.md)
