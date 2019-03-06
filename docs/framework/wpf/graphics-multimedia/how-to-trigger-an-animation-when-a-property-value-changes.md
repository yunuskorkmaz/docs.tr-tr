---
title: 'Nasıl yapılır: Özellik Değeri Değiştiğinde bir Animasyonu Tetikleme'
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], starting when property values change
- triggering animation [WPF]
- Storyboards [WPF], starting when property values change
ms.assetid: 12399c21-0300-4f4f-9e3a-d92d9907e5f5
ms.openlocfilehash: 87f7525755556301fec3f00da612fc5262f1f533
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57356149"
---
# <a name="how-to-trigger-an-animation-when-a-property-value-changes"></a><span data-ttu-id="7a653-102">Nasıl yapılır: Özellik Değeri Değiştiğinde bir Animasyonu Tetikleme</span><span class="sxs-lookup"><span data-stu-id="7a653-102">How to: Trigger an Animation When a Property Value Changes</span></span>
<span data-ttu-id="7a653-103">Bu örnek nasıl kullanılacağını gösterir. bir <xref:System.Windows.Trigger> başlatmak için bir <xref:System.Windows.Media.Animation.Storyboard> bir özellik değeri değiştiğinde.</span><span class="sxs-lookup"><span data-stu-id="7a653-103">This example shows how to use a <xref:System.Windows.Trigger> to start a <xref:System.Windows.Media.Animation.Storyboard> when a property value changes.</span></span> <span data-ttu-id="7a653-104">Kullanabileceğiniz bir <xref:System.Windows.Trigger> içinde bir <xref:System.Windows.Style>, <xref:System.Windows.Controls.ControlTemplate>, veya <xref:System.Windows.DataTemplate>.</span><span class="sxs-lookup"><span data-stu-id="7a653-104">You can use a <xref:System.Windows.Trigger> inside a <xref:System.Windows.Style>, <xref:System.Windows.Controls.ControlTemplate>, or <xref:System.Windows.DataTemplate>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7a653-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="7a653-105">Example</span></span>  
 <span data-ttu-id="7a653-106">Aşağıdaki örnekte bir <xref:System.Windows.Trigger> animasyon uygulamak için <xref:System.Windows.UIElement.Opacity%2A> , bir <xref:System.Windows.Controls.Button> olduğunda kendi <xref:System.Windows.UIElement.IsMouseOver%2A> özellik olur `true`.</span><span class="sxs-lookup"><span data-stu-id="7a653-106">The following example uses a <xref:System.Windows.Trigger> to animate the <xref:System.Windows.UIElement.Opacity%2A> of a <xref:System.Windows.Controls.Button> when its <xref:System.Windows.UIElement.IsMouseOver%2A> property becomes `true`.</span></span>  
  
 [!code-xaml[AnimatePropertyStoryboards#PropertyTriggerExample](~/samples/snippets/xaml/VS_Snippets_Wpf/AnimatePropertyStoryboards/XAML/PropertyTriggerExample.xaml#propertytriggerexample)]  
  
 <span data-ttu-id="7a653-107">Özelliği tarafından uygulanan animasyonlar <xref:System.Windows.Trigger> nesneleri davranır daha karmaşık bir biçimde <xref:System.Windows.EventTrigger> animasyonlar veya animasyonları kullanılarak başlatılan <xref:System.Windows.Media.Animation.Storyboard> yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="7a653-107">Animations applied by property <xref:System.Windows.Trigger> objects behave in a more complex fashion than <xref:System.Windows.EventTrigger> animations or animations started using <xref:System.Windows.Media.Animation.Storyboard> methods.</span></span>  <span data-ttu-id="7a653-108">Bunlar animasyonlarla "iletim diğer tarafından tanımlanan" <xref:System.Windows.Trigger> nesneleri, ancak compose ile <xref:System.Windows.EventTrigger> ve animasyonlar yöntemi tetiklendi.</span><span class="sxs-lookup"><span data-stu-id="7a653-108">They "handoff" with animations defined by other <xref:System.Windows.Trigger> objects, but compose with <xref:System.Windows.EventTrigger> and method-triggered animations.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7a653-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7a653-109">See also</span></span>
- <xref:System.Windows.Trigger>
- [<span data-ttu-id="7a653-110">Özellik Animasyon Tekniklerine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="7a653-110">Property Animation Techniques Overview</span></span>](property-animation-techniques-overview.md)
- [<span data-ttu-id="7a653-111">Görsel Taslaklara Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="7a653-111">Storyboards Overview</span></span>](storyboards-overview.md)
