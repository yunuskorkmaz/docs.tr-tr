---
title: "Nasıl yapılır: Bir Stile Animasyon Ekleme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- animation [WPF], properties [WPF], within styles
- styles [WPF], animating properties within
ms.assetid: 6a791f3d-6b1f-4972-a2f9-35880bcfd954
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2aabe24b77a9016b5b8119646c80ea84eb73acb9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-animate-in-a-style"></a><span data-ttu-id="cc82a-102">Nasıl yapılır: Bir Stile Animasyon Ekleme</span><span class="sxs-lookup"><span data-stu-id="cc82a-102">How to: Animate in a Style</span></span>
<span data-ttu-id="cc82a-103">Bu örnek, stil içindeki özelliklere animasyon gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="cc82a-103">This example shows how to animate properties within a style.</span></span> <span data-ttu-id="cc82a-104">Stil içinde animasyon eklerken, yalnızca stili tanımlandığı çerçeve öğesi doğrudan hedeflenebilir.</span><span class="sxs-lookup"><span data-stu-id="cc82a-104">When animating within a style, only the framework element for which the style is defined can be targeted directly.</span></span> <span data-ttu-id="cc82a-105">Freezable nesne hedeflemek için "aşağı stilde öğe özelliğinden nokta gerekir".</span><span class="sxs-lookup"><span data-stu-id="cc82a-105">To target a freezable object, you must "dot down" from a property of the styled element.</span></span>  
  
 <span data-ttu-id="cc82a-106">Aşağıdaki örnekte, birkaç animasyon stil içinde tanımlanır ve uygulanan bir <xref:System.Windows.Controls.Button>.</span><span class="sxs-lookup"><span data-stu-id="cc82a-106">In the following example, several animations are defined within a style and applied to a <xref:System.Windows.Controls.Button>.</span></span> <span data-ttu-id="cc82a-107">Kullanıcı fare düğmesini taşındığında, opak görünümden kısmen saydam ve geri belirerek, tekrar.</span><span class="sxs-lookup"><span data-stu-id="cc82a-107">When the user moves the mouse over the button, it fades from opaque to partially translucent and back again, repeatedly.</span></span> <span data-ttu-id="cc82a-108">Kullanıcının fare düğmesini devre dışı geçtiğinde, tamamen opak olur.</span><span class="sxs-lookup"><span data-stu-id="cc82a-108">When the user moves the mouse off the button, it becomes completely opaque.</span></span> <span data-ttu-id="cc82a-109">Düğmesine tıklandığında, arka plan rengi beyaz ve yeniden turuncu değiştirir.</span><span class="sxs-lookup"><span data-stu-id="cc82a-109">When the button is clicked, its background color changes from orange to white and back again.</span></span> <span data-ttu-id="cc82a-110">Çünkü <xref:System.Windows.Media.SolidColorBrush> boyamak için kullanılan düğme doğrudan hedefleyemez, düğmenin noktalanarak erişilir <xref:System.Windows.Controls.Control.Background%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="cc82a-110">Because the <xref:System.Windows.Media.SolidColorBrush> used to paint the button can't be targeted directly, it is accessed by dotting down from the button's <xref:System.Windows.Controls.Control.Background%2A> property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cc82a-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="cc82a-111">Example</span></span>  
 [!code-xaml[timingbehaviors_snip#21](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/StyleStoryboardsExample.xaml#21)]  
  
 <span data-ttu-id="cc82a-112">Stil içinde animasyon eklerken, yoksa hedef nesneler için mümkün olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="cc82a-112">Note that when animating within a style, it's possible to target objects that don't exist.</span></span> <span data-ttu-id="cc82a-113">Örneğin, stilinize kullandığını varsayın bir <xref:System.Windows.Media.SolidColorBrush> düğmenin arka plan özelliği ayarlanmış, ancak bir stil noktada için geçersiz kılınır ve düğmenin arka planı ile ayarlanmış bir <xref:System.Windows.Media.LinearGradientBrush>.</span><span class="sxs-lookup"><span data-stu-id="cc82a-113">For example, suppose your style uses a <xref:System.Windows.Media.SolidColorBrush> to set a Button's background property, but at some point the style is overridden and the button's background is set with a <xref:System.Windows.Media.LinearGradientBrush>.</span></span>  <span data-ttu-id="cc82a-114">Animasyon çalışılırken <xref:System.Windows.Media.SolidColorBrush> bir özel durum; throw olmaz animasyon sessizce başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="cc82a-114">Trying to animate the <xref:System.Windows.Media.SolidColorBrush> won't throw an exception; the animation will simply fail silently.</span></span>  
  
 <span data-ttu-id="cc82a-115">Sözdizimi hedefleyen film şeridi hakkında daha fazla bilgi için bkz: [film şeritleri genel bakış](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md).</span><span class="sxs-lookup"><span data-stu-id="cc82a-115">Fore more information about storyboard targeting syntax, see the [Storyboards Overview](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md).</span></span> <span data-ttu-id="cc82a-116">Animasyon hakkında daha fazla bilgi için bkz: [animasyon genel bakış](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md).</span><span class="sxs-lookup"><span data-stu-id="cc82a-116">For more information about animation, see the [Animation Overview](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md).</span></span> <span data-ttu-id="cc82a-117">Stilleri hakkında daha fazla bilgi için bkz: [stil ve şablon](../../../../docs/framework/wpf/controls/styling-and-templating.md).</span><span class="sxs-lookup"><span data-stu-id="cc82a-117">For more information about styles, see the [Styling and Templating](../../../../docs/framework/wpf/controls/styling-and-templating.md).</span></span>
