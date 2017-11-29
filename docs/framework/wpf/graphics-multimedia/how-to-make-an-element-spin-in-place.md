---
title: "Nasıl yapılır: Bir Öğenin Yerinde Dönmesini Sağlama"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- graphics [WPF], spinning elements
- spinning elements [WPF]
ms.assetid: 1f011976-8b07-4c31-9faf-019e0ddaa24c
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: e7dac2b1afb9d0ed385f3c25c2e30a93ea8a24f5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-make-an-element-spin-in-place"></a><span data-ttu-id="f4498-102">Nasıl yapılır: Bir Öğenin Yerinde Dönmesini Sağlama</span><span class="sxs-lookup"><span data-stu-id="f4498-102">How to: Make an Element Spin in Place</span></span>
<span data-ttu-id="f4498-103">Bu örnek kullanarak döndürme bir öğe nasıl yapılacağını gösterir bir <xref:System.Windows.Media.RotateTransform> ve <xref:System.Windows.Media.Animation.DoubleAnimation>.</span><span class="sxs-lookup"><span data-stu-id="f4498-103">This example shows how to make an element spin by using a <xref:System.Windows.Media.RotateTransform> and a <xref:System.Windows.Media.Animation.DoubleAnimation>.</span></span>  
  
 <span data-ttu-id="f4498-104">Aşağıdaki örnek uygular <xref:System.Windows.Media.RotateTransform> için <xref:System.Windows.UIElement.RenderTransform%2A> öğesi özelliği.</span><span class="sxs-lookup"><span data-stu-id="f4498-104">The following example applies the <xref:System.Windows.Media.RotateTransform> to the <xref:System.Windows.UIElement.RenderTransform%2A> property of the element.</span></span> <span data-ttu-id="f4498-105">Örnek kullanan bir <xref:System.Windows.Media.Animation.DoubleAnimation> animasyon için <xref:System.Windows.Media.RotateTransform.Angle%2A> , <xref:System.Windows.Media.RotateTransform>.</span><span class="sxs-lookup"><span data-stu-id="f4498-105">The example uses a <xref:System.Windows.Media.Animation.DoubleAnimation> to animate the <xref:System.Windows.Media.RotateTransform.Angle%2A> of the <xref:System.Windows.Media.RotateTransform>.</span></span> <span data-ttu-id="f4498-106">Yerinde öğeyi göstermek için örnek ayarlar <xref:System.Windows.UIElement.RenderTransformOrigin%2A> (0,5, 0,5) noktasına öğesi özelliği.</span><span class="sxs-lookup"><span data-stu-id="f4498-106">To make the element spin in place, the example sets the <xref:System.Windows.UIElement.RenderTransformOrigin%2A> property of the element to the point (0.5, 0.5).</span></span>  
  
## <a name="example"></a><span data-ttu-id="f4498-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="f4498-107">Example</span></span>  
 [!code-xaml[transformanimations_snip#11](../../../../samples/snippets/xaml/VS_Snippets_Wpf/transformanimations_snip/XAML/RotateAboutCenterExample.xaml#11)]  
  
 <span data-ttu-id="f4498-108">Daha fazla dönüşüm örnekleri içeren tam örnek için bkz: [2-D dönüşümler örnek](http://go.microsoft.com/fwlink/?LinkID=158252).</span><span class="sxs-lookup"><span data-stu-id="f4498-108">For the complete sample, which includes more transformation examples, see [2-D Transforms Sample](http://go.microsoft.com/fwlink/?LinkID=158252).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f4498-109">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f4498-109">See Also</span></span>  
 [<span data-ttu-id="f4498-110">Animasyon genel bakış</span><span class="sxs-lookup"><span data-stu-id="f4498-110">Animation Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [<span data-ttu-id="f4498-111">Dönüşümler genel bakış</span><span class="sxs-lookup"><span data-stu-id="f4498-111">Transforms Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md)
