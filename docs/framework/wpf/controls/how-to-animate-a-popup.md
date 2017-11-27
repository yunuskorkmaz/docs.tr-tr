---
title: "Nasıl yapılır: Açılan Pencereye Animasyon Ekleme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Popup control [WPF], animating
- animation [WPF], Popup controls
ms.assetid: acaa2a0a-6137-4efd-9cd1-75ece222e390
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 276c1a54cfdddcde84c0702f4e84f1dc6174bbda
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-animate-a-popup"></a><span data-ttu-id="c8c81-102">Nasıl yapılır: Açılan Pencereye Animasyon Ekleme</span><span class="sxs-lookup"><span data-stu-id="c8c81-102">How to: Animate a Popup</span></span>
<span data-ttu-id="c8c81-103">Bu örnek, animasyon için iki yol gösterir. bir <xref:System.Windows.Controls.Primitives.Popup> denetim.</span><span class="sxs-lookup"><span data-stu-id="c8c81-103">This example shows two ways to animate a <xref:System.Windows.Controls.Primitives.Popup> control.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c8c81-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="c8c81-104">Example</span></span>  
 <span data-ttu-id="c8c81-105">Aşağıdaki örnek kümeleri <xref:System.Windows.Controls.Primitives.PopupAnimation> değerini özelliğine <xref:System.Windows.Controls.Primitives.PopupAnimation.Slide>, hangi nedenler <xref:System.Windows.Controls.Primitives.Popup> görüntülendiğinde "bileşenini için".</span><span class="sxs-lookup"><span data-stu-id="c8c81-105">The following example sets the <xref:System.Windows.Controls.Primitives.PopupAnimation> property to a value of <xref:System.Windows.Controls.Primitives.PopupAnimation.Slide>, which causes the <xref:System.Windows.Controls.Primitives.Popup> to "slide-in" when it appears.</span></span>  
  
 <span data-ttu-id="c8c81-106">Döndürmek için <xref:System.Windows.Controls.Primitives.Popup>, bu örnek atar bir <xref:System.Windows.Media.RotateTransform> için <xref:System.Windows.UIElement.RenderTransform%2A> özelliği <xref:System.Windows.Controls.Canvas>, alt öğesi olan olduğu <xref:System.Windows.Controls.Primitives.Popup>.</span><span class="sxs-lookup"><span data-stu-id="c8c81-106">In order to rotate the <xref:System.Windows.Controls.Primitives.Popup>, this example assigns a <xref:System.Windows.Media.RotateTransform> to the <xref:System.Windows.UIElement.RenderTransform%2A> property on the <xref:System.Windows.Controls.Canvas>, which is the child element of the <xref:System.Windows.Controls.Primitives.Popup>.</span></span>  
  
 <span data-ttu-id="c8c81-107">Dönüştürme düzgün çalışması örnek ayarlamalısınız <xref:System.Windows.Controls.Primitives.Popup.AllowsTransparency%2A> özelliğine `true`.</span><span class="sxs-lookup"><span data-stu-id="c8c81-107">For the transform to work correctly, the example must set the <xref:System.Windows.Controls.Primitives.Popup.AllowsTransparency%2A> property to `true`.</span></span> <span data-ttu-id="c8c81-108">Ayrıca, <xref:System.Windows.FrameworkElement.Margin%2A> üzerinde <xref:System.Windows.Controls.Canvas> içerik için yeterli alan belirtmelidir <xref:System.Windows.Controls.Primitives.Popup> döndürmek için.</span><span class="sxs-lookup"><span data-stu-id="c8c81-108">In addition, the <xref:System.Windows.FrameworkElement.Margin%2A> on the <xref:System.Windows.Controls.Canvas> content must specify enough space for the <xref:System.Windows.Controls.Primitives.Popup> to rotate.</span></span>  
  
 [!code-xaml[AnimatedPopup#RotateTransform2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AnimatedPopup/CS/Window1.xaml#rotatetransform2)]  
  
 <span data-ttu-id="c8c81-109">Aşağıdaki örnekte gösterildiği nasıl bir <xref:System.Windows.Controls.Primitives.ButtonBase.Click> oluşur olay olduğunda bir <xref:System.Windows.Controls.Button> tıklandığında, Tetikleyicileri <xref:System.Windows.Media.Animation.Storyboard> animasyonu başlatır.</span><span class="sxs-lookup"><span data-stu-id="c8c81-109">The following example shows how a <xref:System.Windows.Controls.Primitives.ButtonBase.Click> event, which occurs when a <xref:System.Windows.Controls.Button> is clicked, triggers the <xref:System.Windows.Media.Animation.Storyboard> that starts the animation.</span></span>  
  
 [!code-xaml[AnimatedPopup#RotateTransform1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AnimatedPopup/CS/Window1.xaml#rotatetransform1)]  
  
## <a name="see-also"></a><span data-ttu-id="c8c81-110">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c8c81-110">See Also</span></span>  
 <xref:System.Windows.UIElement.RenderTransform%2A>  
 <xref:System.Windows.Controls.Primitives.BulletDecorator>  
 <xref:System.Windows.Media.RotateTransform>  
 <xref:System.Windows.Media.Animation.Storyboard>  
 <xref:System.Windows.Controls.Primitives.Popup>  
 [<span data-ttu-id="c8c81-111">Nasıl Yapılır Konuları</span><span class="sxs-lookup"><span data-stu-id="c8c81-111">How-to Topics</span></span>](../../../../docs/framework/wpf/controls/popup-how-to-topics.md)  
 [<span data-ttu-id="c8c81-112">Açılan genel bakış</span><span class="sxs-lookup"><span data-stu-id="c8c81-112">Popup Overview</span></span>](../../../../docs/framework/wpf/controls/popup-overview.md)
