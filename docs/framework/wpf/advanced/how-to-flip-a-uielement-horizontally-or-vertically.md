---
title: "Nasıl yapılır: UIElement'i Yatay veya Dikey Olarak Çevirme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- flipping UIElements [WPF]
- UIElements [WPF], flipping
ms.assetid: 02c6730f-65c0-40d5-a553-4cb663721882
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 84d1360246141cfa565d669fff108e3e4db3ce33
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-flip-a-uielement-horizontally-or-vertically"></a><span data-ttu-id="61cf8-102">Nasıl yapılır: UIElement'i Yatay veya Dikey Olarak Çevirme</span><span class="sxs-lookup"><span data-stu-id="61cf8-102">How to: Flip a UIElement Horizontally or Vertically</span></span>
<span data-ttu-id="61cf8-103">Bu örnek nasıl kullanılacağını gösteren bir <xref:System.Windows.Media.ScaleTransform> ters çevirmek için bir <xref:System.Windows.UIElement> yatay veya dikey olarak.</span><span class="sxs-lookup"><span data-stu-id="61cf8-103">This example shows how to use a <xref:System.Windows.Media.ScaleTransform> to flip a <xref:System.Windows.UIElement> horizontally or vertically.</span></span> <span data-ttu-id="61cf8-104">Bu örnekte, bir <xref:System.Windows.Controls.Button> denetimi (bir tür <xref:System.Windows.UIElement>) uygulanarak çevrilmiş bir <xref:System.Windows.Media.ScaleTransform> için kendi <xref:System.Windows.UIElement.RenderTransform%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="61cf8-104">In this example, a <xref:System.Windows.Controls.Button> control (a type of <xref:System.Windows.UIElement>) is flipped by applying a <xref:System.Windows.Media.ScaleTransform> to its <xref:System.Windows.UIElement.RenderTransform%2A> property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="61cf8-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="61cf8-105">Example</span></span>  
 <span data-ttu-id="61cf8-106">Aşağıdaki çizimde ters çevirmek için düğmesini gösterir.</span><span class="sxs-lookup"><span data-stu-id="61cf8-106">The following illustration shows the button to flip.</span></span>  
  
 <span data-ttu-id="61cf8-107">![Hiçbir dönüştürme düğmesiyle](../../../../docs/framework/wpf/advanced/media/graphicsmm-buttonflipbeforeflip.gif "graphicsmm_buttonflipbeforeflip")</span><span class="sxs-lookup"><span data-stu-id="61cf8-107">![A button with no transform](../../../../docs/framework/wpf/advanced/media/graphicsmm-buttonflipbeforeflip.gif "graphicsmm_buttonflipbeforeflip")</span></span>  
<span data-ttu-id="61cf8-108">Çevrilecek UIElement</span><span class="sxs-lookup"><span data-stu-id="61cf8-108">The UIElement to flip</span></span>  
  
 <span data-ttu-id="61cf8-109">Aşağıdaki düğmeyi oluşturan kodu gösterir.</span><span class="sxs-lookup"><span data-stu-id="61cf8-109">The following shows the code that creates the button.</span></span>  
  
 [!code-xaml[Transforms_snip#GraphicsMMButtonWithoutFlip](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/FlipExample.xaml#graphicsmmbuttonwithoutflip)]  
  
## <a name="example"></a><span data-ttu-id="61cf8-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="61cf8-110">Example</span></span>  
 <span data-ttu-id="61cf8-111">Düğmeyi Yatayda ters çevirmek için oluşturma bir <xref:System.Windows.Media.ScaleTransform> ve kendi <xref:System.Windows.Media.ScaleTransform.ScaleX%2A> özelliği-1.</span><span class="sxs-lookup"><span data-stu-id="61cf8-111">To flip the button horizontally, create a <xref:System.Windows.Media.ScaleTransform> and set its <xref:System.Windows.Media.ScaleTransform.ScaleX%2A> property to -1.</span></span> <span data-ttu-id="61cf8-112">Uygulama <xref:System.Windows.Media.ScaleTransform> düğmenin için <xref:System.Windows.UIElement.RenderTransform%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="61cf8-112">Apply the <xref:System.Windows.Media.ScaleTransform> to the button's <xref:System.Windows.UIElement.RenderTransform%2A> property.</span></span>  
  
 [!code-xaml[Transforms_snip#GraphicsMMFlipButtonExample1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/FlipExample.xaml#graphicsmmflipbuttonexample1)]  
  
 <span data-ttu-id="61cf8-113">![Yatay hakkında çevrilmiş bir düğme &#40; 0,0 &#41; ] (../../../../docs/framework/wpf/advanced/media/graphicsmm-buttonfliphorizontalflip-displaced.gif "graphicsmm_buttonfliphorizontalflip_displaced")</span><span class="sxs-lookup"><span data-stu-id="61cf8-113">![A button flipped horizontally about &#40;0,0&#41;](../../../../docs/framework/wpf/advanced/media/graphicsmm-buttonfliphorizontalflip-displaced.gif "graphicsmm_buttonfliphorizontalflip_displaced")</span></span>  
<span data-ttu-id="61cf8-114">ScaleTransform uygulandıktan sonra düğmesi</span><span class="sxs-lookup"><span data-stu-id="61cf8-114">The button after applying the ScaleTransform</span></span>  
  
## <a name="example"></a><span data-ttu-id="61cf8-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="61cf8-115">Example</span></span>  
 <span data-ttu-id="61cf8-116">Önceki çizimden görüldüğü gibi düğme çevrilmiş, ancak aynı zamanda taşındı.</span><span class="sxs-lookup"><span data-stu-id="61cf8-116">As you can see from the previous illustration, the button was flipped, but it was also moved.</span></span> <span data-ttu-id="61cf8-117">Düğme sol üst köşeden çevrilmiş olmasıdır.</span><span class="sxs-lookup"><span data-stu-id="61cf8-117">That's because the button was flipped from its top left corner.</span></span> <span data-ttu-id="61cf8-118">Uygulamak istediğiniz yerde düğmesi ters çevirmek için <xref:System.Windows.Media.ScaleTransform> köşesi yerine kendi merkezi.</span><span class="sxs-lookup"><span data-stu-id="61cf8-118">To flip the button in place, you want to apply the <xref:System.Windows.Media.ScaleTransform> to its center, not its corner.</span></span> <span data-ttu-id="61cf8-119">Uygulama için kolay bir yol <xref:System.Windows.Media.ScaleTransform> düğmelere merkezi düğmenin ayarlamaktır <xref:System.Windows.UIElement.RenderTransformOrigin%2A> 0,5, özelliğine 0,5.</span><span class="sxs-lookup"><span data-stu-id="61cf8-119">An easy way to apply the <xref:System.Windows.Media.ScaleTransform> to the buttons center is to set the button's <xref:System.Windows.UIElement.RenderTransformOrigin%2A> property to 0.5, 0.5.</span></span>  
  
 [!code-xaml[Transforms_snip#GraphicsMMFlipButtonExample2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/FlipExample.xaml#graphicsmmflipbuttonexample2)]  
  
 <span data-ttu-id="61cf8-120">![Çevrilen düğme yatay ortasından](../../../../docs/framework/wpf/advanced/media/graphicsmm-buttonfliphorizontalflip-inplace.gif "graphicsmm_buttonfliphorizontalflip_inplace")</span><span class="sxs-lookup"><span data-stu-id="61cf8-120">![A button flipped horizontally about its center](../../../../docs/framework/wpf/advanced/media/graphicsmm-buttonfliphorizontalflip-inplace.gif "graphicsmm_buttonfliphorizontalflip_inplace")</span></span>  
<span data-ttu-id="61cf8-121">Düğme 0,5, RenderTransformOrigin'i 0,5</span><span class="sxs-lookup"><span data-stu-id="61cf8-121">The button with a RenderTransformOrigin of 0.5, 0.5</span></span>  
  
## <a name="example"></a><span data-ttu-id="61cf8-122">Örnek</span><span class="sxs-lookup"><span data-stu-id="61cf8-122">Example</span></span>  
 <span data-ttu-id="61cf8-123">Düğmeyi Dikeyde ters çevirmek için ayarlanmış <xref:System.Windows.Media.ScaleTransform> nesnenin <xref:System.Windows.Media.ScaleTransform.ScaleY%2A> özelliği yerine kendi <xref:System.Windows.Media.ScaleTransform.ScaleX%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="61cf8-123">To flip the button vertically, set the <xref:System.Windows.Media.ScaleTransform> object's <xref:System.Windows.Media.ScaleTransform.ScaleY%2A> property instead of its <xref:System.Windows.Media.ScaleTransform.ScaleX%2A> property.</span></span>  
  
 [!code-xaml[Transforms_snip#GraphicsMMVerticalFlipButtonExample2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/FlipExample.xaml#graphicsmmverticalflipbuttonexample2)]  
  
 <span data-ttu-id="61cf8-124">![Çevrilen düğme dikey ortasından](../../../../docs/framework/wpf/advanced/media/graphicsmm-buttonflipverticalflip-inplace.gif "graphicsmm_buttonflipverticalflip_inplace")</span><span class="sxs-lookup"><span data-stu-id="61cf8-124">![A button flipped vertically about its center](../../../../docs/framework/wpf/advanced/media/graphicsmm-buttonflipverticalflip-inplace.gif "graphicsmm_buttonflipverticalflip_inplace")</span></span>  
<span data-ttu-id="61cf8-125">Dikey olarak çevrilen düğme</span><span class="sxs-lookup"><span data-stu-id="61cf8-125">The vertically flipped button</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="61cf8-126">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="61cf8-126">See Also</span></span>  
 [<span data-ttu-id="61cf8-127">Dönüşümler genel bakış</span><span class="sxs-lookup"><span data-stu-id="61cf8-127">Transforms Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md)
