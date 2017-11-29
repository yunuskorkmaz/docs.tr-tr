---
title: "Nasıl yapılır: FrameworkElement Boyutuna Animasyon Ekleme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- animation [WPF], FrameworkElement size
- FrameworkElement [WPF], animating size of
ms.assetid: d4cd5a13-c20d-4a6f-a2ba-14f2c9ce4cef
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 17882494e48c5d692c8a774e6d77408557976c71
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-animate-the-size-of-a-frameworkelement"></a><span data-ttu-id="1f3df-102">Nasıl yapılır: FrameworkElement Boyutuna Animasyon Ekleme</span><span class="sxs-lookup"><span data-stu-id="1f3df-102">How to: Animate the Size of a FrameworkElement</span></span>
<span data-ttu-id="1f3df-103">Boyutunu animasyon uygulamak için bir <xref:System.Windows.FrameworkElement>, animasyon ya da kendi <xref:System.Windows.FrameworkElement.Width%2A> ve <xref:System.Windows.FrameworkElement.Height%2A> özellikleri veya kullanım animasyonlu <xref:System.Windows.Media.ScaleTransform>.</span><span class="sxs-lookup"><span data-stu-id="1f3df-103">To animate the size of a <xref:System.Windows.FrameworkElement>, you can either animate its <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> properties or use an animated <xref:System.Windows.Media.ScaleTransform>.</span></span>  
  
 <span data-ttu-id="1f3df-104">Aşağıdaki örnekte, bu iki yaklaşım kullanarak iki düğmenin boyutunu canlandırır.</span><span class="sxs-lookup"><span data-stu-id="1f3df-104">In the following example animates the size of two buttons using these two approaches.</span></span> <span data-ttu-id="1f3df-105">Bir düğme yeniden boyutlandırılır animasyon tarafından kendi <xref:System.Windows.FrameworkElement.Width%2A> özelliği ve başka bir yeniden boyutlandırılır animasyon tarafından bir <xref:System.Windows.Media.ScaleTransform> uygulanan kendi <xref:System.Windows.UIElement.RenderTransform%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="1f3df-105">One button is resized by animating its <xref:System.Windows.FrameworkElement.Width%2A> property and another is resized by animating a <xref:System.Windows.Media.ScaleTransform> applied to its <xref:System.Windows.UIElement.RenderTransform%2A> property.</span></span> <span data-ttu-id="1f3df-106">Her düğme bazı metinler içerir.</span><span class="sxs-lookup"><span data-stu-id="1f3df-106">Each button contains some text.</span></span> <span data-ttu-id="1f3df-107">Başlangıçta, metin hem düğmeleri aynı görünür, ancak düğmeler yeniden boyutlandırıldığında gibi ikinci düğme metni bozulur.</span><span class="sxs-lookup"><span data-stu-id="1f3df-107">Initially, the text appears the same in both buttons, but as the buttons are resized, the text in the second button becomes distorted.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1f3df-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="1f3df-108">Example</span></span>  
 [!code-xaml[transformanimations_snip#1](../../../../samples/snippets/xaml/VS_Snippets_Wpf/transformanimations_snip/XAML/AnimatingSizeExample.xaml#1)]  
  
 <span data-ttu-id="1f3df-109">Bir öğenin dönüştürme, öğenin tamamını ve içeriği dönüştürülür.</span><span class="sxs-lookup"><span data-stu-id="1f3df-109">When you transform an element, the entire element and its contents are transformed.</span></span> <span data-ttu-id="1f3df-110">İlk düğme durumunda olduğu gibi bir öğenin boyutunu doğrudan değiştirdiğinizde, boyutunu ve konumunu kendi üst öğesi boyutuna göre değişir sürece öğenin içeriği yeniden boyutlandırılıyor değil.</span><span class="sxs-lookup"><span data-stu-id="1f3df-110">When you directly alter the size of an element, as in the case of the first button, the element's contents are not resized unless their size and position depend on the size of their parent element.</span></span>  
  
 <span data-ttu-id="1f3df-111">Animasyonlu dönüşüm uygulayarak bir öğenin boyutunu animasyon kendi <xref:System.Windows.UIElement.RenderTransform%2A> özelliği animasyonlu daha iyi performans sağlar, <xref:System.Windows.FrameworkElement.Width%2A> ve <xref:System.Windows.FrameworkElement.Height%2A> doğrudan, çünkü <xref:System.Windows.UIElement.RenderTransform%2A> özelliği düzen geçişini tetiklemez.</span><span class="sxs-lookup"><span data-stu-id="1f3df-111">Animating the size of an element by applying an animated transform to its <xref:System.Windows.UIElement.RenderTransform%2A> property provides better performance than animated its <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> directly, because the <xref:System.Windows.UIElement.RenderTransform%2A> property does not trigger a layout pass.</span></span>  
  
 <span data-ttu-id="1f3df-112">Özellikleri hakkında daha fazla bilgi için bkz: [animasyon genel bakış](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md).</span><span class="sxs-lookup"><span data-stu-id="1f3df-112">For more information about animating properties, see the [Animation Overview](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md).</span></span> <span data-ttu-id="1f3df-113">Dönüşümler hakkında daha fazla bilgi için bkz: [dönüştüren genel bakış](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md).</span><span class="sxs-lookup"><span data-stu-id="1f3df-113">For more information about transforms, see the [Transforms Overview](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md).</span></span>
