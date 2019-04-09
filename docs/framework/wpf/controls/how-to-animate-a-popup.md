---
title: 'Nasıl yapılır: Açılan Pencereye Animasyon Ekleme'
ms.date: 03/30/2017
helpviewer_keywords:
- Popup control [WPF], animating
- animation [WPF], Popup controls
ms.assetid: acaa2a0a-6137-4efd-9cd1-75ece222e390
ms.openlocfilehash: b70d9c4cb1bca26a6c77d3a7c50add517ca8ef92
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59150117"
---
# <a name="how-to-animate-a-popup"></a><span data-ttu-id="077f9-102">Nasıl yapılır: Açılan Pencereye Animasyon Ekleme</span><span class="sxs-lookup"><span data-stu-id="077f9-102">How to: Animate a Popup</span></span>
<span data-ttu-id="077f9-103">Bu örnek animasyon uygulamak için iki yolunu gösterir bir <xref:System.Windows.Controls.Primitives.Popup> denetimi.</span><span class="sxs-lookup"><span data-stu-id="077f9-103">This example shows two ways to animate a <xref:System.Windows.Controls.Primitives.Popup> control.</span></span>  
  
## <a name="example"></a><span data-ttu-id="077f9-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="077f9-104">Example</span></span>  
 <span data-ttu-id="077f9-105">Aşağıdaki örnek kümeleri <xref:System.Windows.Controls.Primitives.PopupAnimation> bir değere <xref:System.Windows.Controls.Primitives.PopupAnimation.Slide>, hangi nedenleri <xref:System.Windows.Controls.Primitives.Popup> göründüğünde "açma için".</span><span class="sxs-lookup"><span data-stu-id="077f9-105">The following example sets the <xref:System.Windows.Controls.Primitives.PopupAnimation> property to a value of <xref:System.Windows.Controls.Primitives.PopupAnimation.Slide>, which causes the <xref:System.Windows.Controls.Primitives.Popup> to "slide-in" when it appears.</span></span>  
  
 <span data-ttu-id="077f9-106">Döndürmek için <xref:System.Windows.Controls.Primitives.Popup>, bu örnekte atar bir <xref:System.Windows.Media.RotateTransform> için <xref:System.Windows.UIElement.RenderTransform%2A> özelliği <xref:System.Windows.Controls.Canvas>, alt öğesi olan <xref:System.Windows.Controls.Primitives.Popup>.</span><span class="sxs-lookup"><span data-stu-id="077f9-106">In order to rotate the <xref:System.Windows.Controls.Primitives.Popup>, this example assigns a <xref:System.Windows.Media.RotateTransform> to the <xref:System.Windows.UIElement.RenderTransform%2A> property on the <xref:System.Windows.Controls.Canvas>, which is the child element of the <xref:System.Windows.Controls.Primitives.Popup>.</span></span>  
  
 <span data-ttu-id="077f9-107">Örnek dönüştürme düzgün çalışması ayarlamanız gerekir <xref:System.Windows.Controls.Primitives.Popup.AllowsTransparency%2A> özelliğini `true`.</span><span class="sxs-lookup"><span data-stu-id="077f9-107">For the transform to work correctly, the example must set the <xref:System.Windows.Controls.Primitives.Popup.AllowsTransparency%2A> property to `true`.</span></span> <span data-ttu-id="077f9-108">Ayrıca, <xref:System.Windows.FrameworkElement.Margin%2A> üzerinde <xref:System.Windows.Controls.Canvas> içerik için yeterli alan belirtmelidir <xref:System.Windows.Controls.Primitives.Popup> döndürmek için.</span><span class="sxs-lookup"><span data-stu-id="077f9-108">In addition, the <xref:System.Windows.FrameworkElement.Margin%2A> on the <xref:System.Windows.Controls.Canvas> content must specify enough space for the <xref:System.Windows.Controls.Primitives.Popup> to rotate.</span></span>  
  
 [!code-xaml[AnimatedPopup#RotateTransform2](~/samples/snippets/csharp/VS_Snippets_Wpf/AnimatedPopup/CS/Window1.xaml#rotatetransform2)]  
  
 <span data-ttu-id="077f9-109">Aşağıdaki örnekte gösterildiği nasıl bir <xref:System.Windows.Controls.Primitives.ButtonBase.Click> gerçekleşen olay olduğunda bir <xref:System.Windows.Controls.Button> tıklandığında Tetikleyicileri <xref:System.Windows.Media.Animation.Storyboard> animasyon başlar.</span><span class="sxs-lookup"><span data-stu-id="077f9-109">The following example shows how a <xref:System.Windows.Controls.Primitives.ButtonBase.Click> event, which occurs when a <xref:System.Windows.Controls.Button> is clicked, triggers the <xref:System.Windows.Media.Animation.Storyboard> that starts the animation.</span></span>  
  
 [!code-xaml[AnimatedPopup#RotateTransform1](~/samples/snippets/csharp/VS_Snippets_Wpf/AnimatedPopup/CS/Window1.xaml#rotatetransform1)]  
  
## <a name="see-also"></a><span data-ttu-id="077f9-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="077f9-110">See also</span></span>

- <xref:System.Windows.UIElement.RenderTransform%2A>
- <xref:System.Windows.Controls.Primitives.BulletDecorator>
- <xref:System.Windows.Media.RotateTransform>
- <xref:System.Windows.Media.Animation.Storyboard>
- <xref:System.Windows.Controls.Primitives.Popup>
- [<span data-ttu-id="077f9-111">Nasıl Yapılır Konuları</span><span class="sxs-lookup"><span data-stu-id="077f9-111">How-to Topics</span></span>](popup-how-to-topics.md)
- [<span data-ttu-id="077f9-112">Açılır Pencereye Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="077f9-112">Popup Overview</span></span>](popup-overview.md)
