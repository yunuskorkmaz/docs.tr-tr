---
title: "Nasıl yapılır: Özellik Değeri Değiştiğinde bir Animasyonu Tetikleme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- animation [WPF], starting when property values change
- triggering animation [WPF]
- Storyboards [WPF], starting when property values change
ms.assetid: 12399c21-0300-4f4f-9e3a-d92d9907e5f5
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 4d722be0f0367f7e6e98ef1c8451ce58ee28fedd
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-trigger-an-animation-when-a-property-value-changes"></a><span data-ttu-id="4c76c-102">Nasıl yapılır: Özellik Değeri Değiştiğinde bir Animasyonu Tetikleme</span><span class="sxs-lookup"><span data-stu-id="4c76c-102">How to: Trigger an Animation When a Property Value Changes</span></span>
<span data-ttu-id="4c76c-103">Bu örnek nasıl kullanılacağını gösteren bir <xref:System.Windows.Trigger> başlatmak için bir <xref:System.Windows.Media.Animation.Storyboard> bir özellik değeri değiştiğinde.</span><span class="sxs-lookup"><span data-stu-id="4c76c-103">This example shows how to use a <xref:System.Windows.Trigger> to start a <xref:System.Windows.Media.Animation.Storyboard> when a property value changes.</span></span> <span data-ttu-id="4c76c-104">Kullanabileceğiniz bir <xref:System.Windows.Trigger> içinde bir <xref:System.Windows.Style>, <xref:System.Windows.Controls.ControlTemplate>, veya <xref:System.Windows.DataTemplate>.</span><span class="sxs-lookup"><span data-stu-id="4c76c-104">You can use a <xref:System.Windows.Trigger> inside a <xref:System.Windows.Style>, <xref:System.Windows.Controls.ControlTemplate>, or <xref:System.Windows.DataTemplate>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4c76c-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="4c76c-105">Example</span></span>  
 <span data-ttu-id="4c76c-106">Aşağıdaki örnek kullanan bir <xref:System.Windows.Trigger> animasyon için <xref:System.Windows.UIElement.Opacity%2A> , bir <xref:System.Windows.Controls.Button> zaman kendi <xref:System.Windows.UIElement.IsMouseOver%2A> özellik olur `true`.</span><span class="sxs-lookup"><span data-stu-id="4c76c-106">The following example uses a <xref:System.Windows.Trigger> to animate the <xref:System.Windows.UIElement.Opacity%2A> of a <xref:System.Windows.Controls.Button> when its <xref:System.Windows.UIElement.IsMouseOver%2A> property becomes `true`.</span></span>  
  
 [!code-xaml[AnimatePropertyStoryboards#PropertyTriggerExample](../../../../samples/snippets/xaml/VS_Snippets_Wpf/AnimatePropertyStoryboards/XAML/PropertyTriggerExample.xaml#propertytriggerexample)]  
  
 <span data-ttu-id="4c76c-107">Özelliği tarafından uygulanan bir animasyon <xref:System.Windows.Trigger> nesneleri davranırlar daha karmaşık bir şekilde <xref:System.Windows.EventTrigger> animasyonları veya animasyonları kullanılarak başlatılan <xref:System.Windows.Media.Animation.Storyboard> yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="4c76c-107">Animations applied by property <xref:System.Windows.Trigger> objects behave in a more complex fashion than <xref:System.Windows.EventTrigger> animations or animations started using <xref:System.Windows.Media.Animation.Storyboard> methods.</span></span>  <span data-ttu-id="4c76c-108">Bunlar animasyonları ile "iletimi diğer tarafından tanımlanan" <xref:System.Windows.Trigger> nesneleri, ancak oluşturma ile <xref:System.Windows.EventTrigger> ve yöntemi tetiklenen animasyonları.</span><span class="sxs-lookup"><span data-stu-id="4c76c-108">They "handoff" with animations defined by other <xref:System.Windows.Trigger> objects, but compose with <xref:System.Windows.EventTrigger> and method-triggered animations.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4c76c-109">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="4c76c-109">See Also</span></span>  
 <xref:System.Windows.Trigger>  
 [<span data-ttu-id="4c76c-110">Özellik Animasyon Tekniklerine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="4c76c-110">Property Animation Techniques Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/property-animation-techniques-overview.md)  
 [<span data-ttu-id="4c76c-111">Film şeritleri genel bakış</span><span class="sxs-lookup"><span data-stu-id="4c76c-111">Storyboards Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md)
