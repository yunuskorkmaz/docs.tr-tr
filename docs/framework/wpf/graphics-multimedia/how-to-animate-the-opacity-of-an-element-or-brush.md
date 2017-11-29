---
title: "Nasıl yapılır: Bir Öğe veya Fırça Opaklığına Animasyon Ekleme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- opacity [WPF], animating
- animation [WPF], Opacity property
ms.assetid: 572af23b-39dd-48d1-9db5-4bca56a4b3d3
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 808d29292e176af8d3af1fc0f4a02c48ee05ea35
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-animate-the-opacity-of-an-element-or-brush"></a><span data-ttu-id="32b76-102">Nasıl yapılır: Bir Öğe veya Fırça Opaklığına Animasyon Ekleme</span><span class="sxs-lookup"><span data-stu-id="32b76-102">How to: Animate the Opacity of an Element or Brush</span></span>
<span data-ttu-id="32b76-103">Görünüm ve bu moddan silinerek çerçeve öğesi yapmak için animasyon uygulayabilirsiniz kendi <xref:System.Windows.UIElement.Opacity%2A> özellik veya animasyon <xref:System.Windows.Media.Brush.Opacity%2A> özelliği <xref:System.Windows.Media.Brush> (veya Fırçalar) onu boyamak için kullanılan.</span><span class="sxs-lookup"><span data-stu-id="32b76-103">To make a framework element fade in and out of view, you can animate its <xref:System.Windows.UIElement.Opacity%2A> property or you can animate the <xref:System.Windows.Media.Brush.Opacity%2A> property of the <xref:System.Windows.Media.Brush> (or brushes) used to paint it.</span></span> <span data-ttu-id="32b76-104">Kolaylaştırır öğenin opaklık animasyon ve alt görünümü ve bu moddan silinerek, ancak öğe boyamak için kullanılan fırça animasyon öğesi hangi kısmının belirerek hakkında daha fazla seçmeli olarak sağlar.</span><span class="sxs-lookup"><span data-stu-id="32b76-104">Animating the element's opacity makes it and its children fade in and out of view, but animating the brush used to paint the element enables you to be more selective about which portion of the element fades.</span></span> <span data-ttu-id="32b76-105">Örneğin, bir düğmenin arka planını boyamak için kullanılan fırça geçirgenliğini animasyon.</span><span class="sxs-lookup"><span data-stu-id="32b76-105">For example, you could animate the opacity of a brush used to paint a button's background.</span></span> <span data-ttu-id="32b76-106">Bu, içeri ve dışarı görünümünün metnini tamamıyla opak bırakarak sırasında silinerek için düğmenin arka plan neden olur.</span><span class="sxs-lookup"><span data-stu-id="32b76-106">This would cause the button's background to fade in and out of view, while leaving its text fully opaque.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="32b76-107">Animasyon <xref:System.Windows.Media.Brush.Opacity%2A> , bir <xref:System.Windows.Media.Brush> animasyon üzerinden performans avantajı sağlar <xref:System.Windows.UIElement.Opacity%2A> bir öğenin özelliği.</span><span class="sxs-lookup"><span data-stu-id="32b76-107">Animating the <xref:System.Windows.Media.Brush.Opacity%2A> of a <xref:System.Windows.Media.Brush> provides performance benefits over animating the <xref:System.Windows.UIElement.Opacity%2A> property of an element.</span></span>  
  
 <span data-ttu-id="32b76-108">Böylece Görünüm ve bu moddan silinerek aşağıdaki örnekte, iki düğme oynatılır.</span><span class="sxs-lookup"><span data-stu-id="32b76-108">In the following example, two buttons are animated so that they fade in and out of view.</span></span> <span data-ttu-id="32b76-109">İlk geçirgenliğini <xref:System.Windows.Controls.Button> gelen animasyonlu `1.0` için `0.0` üzerinden bir <xref:System.Windows.Media.Animation.Timeline.Duration%2A> beş saniye.</span><span class="sxs-lookup"><span data-stu-id="32b76-109">The Opacity of the first <xref:System.Windows.Controls.Button> is animated from `1.0` to `0.0` over a <xref:System.Windows.Media.Animation.Timeline.Duration%2A> of five seconds.</span></span> <span data-ttu-id="32b76-110">İkinci düğme ayrıca animasyonlu ancak SolidColorBrush kısmını boyamak için kullanılan kendi <xref:System.Windows.Controls.Control.Background%2A> tüm düğmenin geçirgenliğini yerine animasyonlu.</span><span class="sxs-lookup"><span data-stu-id="32b76-110">The second button is also animated, but the Opacity of the SolidColorBrush used to paint its <xref:System.Windows.Controls.Control.Background%2A> is animated rather than the opacity of the entire button.</span></span> <span data-ttu-id="32b76-111">Örnek çalıştırdığınızda, yalnızca ikinci düğmenin arka plan Görünüm ve bu moddan belirerek sırada ilk düğme tamamen görünümü ve bu moddan kaybolur.</span><span class="sxs-lookup"><span data-stu-id="32b76-111">When the example is run, the first button completely fades in and out of view, while only the background of the second button fades in and out of view.</span></span> <span data-ttu-id="32b76-112">Metni ve kenarlığı tamamen donuk kalır.</span><span class="sxs-lookup"><span data-stu-id="32b76-112">Its text and border remain fully opaque.</span></span>  
  
## <a name="example"></a><span data-ttu-id="32b76-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="32b76-113">Example</span></span>  
 [!code-xaml[timingbehaviors_snip#10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/OpacityAnimationExample.xaml#10)]  
  
 <span data-ttu-id="32b76-114">Kod bu örnekten çıkarılmıştır.</span><span class="sxs-lookup"><span data-stu-id="32b76-114">Code has been omitted from this example.</span></span> <span data-ttu-id="32b76-115">Tam örnek ayrıca geçirgenliğini animasyon gösterilmektedir bir <xref:System.Windows.Media.Color> içinde bir <xref:System.Windows.Media.LinearGradientBrush>.</span><span class="sxs-lookup"><span data-stu-id="32b76-115">The full sample also shows how to animate the opacity of a <xref:System.Windows.Media.Color> within a <xref:System.Windows.Media.LinearGradientBrush>.</span></span>  <span data-ttu-id="32b76-116">Tam bir örnek için bkz: [öğesi örneği geçirgenliğini animasyon](http://go.microsoft.com/fwlink/?LinkID=159968).</span><span class="sxs-lookup"><span data-stu-id="32b76-116">For the full sample, see the [Animating the Opacity of an Element Sample](http://go.microsoft.com/fwlink/?LinkID=159968).</span></span>
