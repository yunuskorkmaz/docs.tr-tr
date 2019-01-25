---
title: 'Nasıl yapılır: Özellik Değeri Değiştiğinde bir Animasyonu Tetikleme'
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], starting when property values change
- triggering animation [WPF]
- Storyboards [WPF], starting when property values change
ms.assetid: 12399c21-0300-4f4f-9e3a-d92d9907e5f5
ms.openlocfilehash: 2be85a9ae93d504d98930468ad2e257385e835f6
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54705303"
---
# <a name="how-to-trigger-an-animation-when-a-property-value-changes"></a>Nasıl yapılır: Özellik Değeri Değiştiğinde bir Animasyonu Tetikleme
Bu örnek nasıl kullanılacağını gösterir. bir <xref:System.Windows.Trigger> başlatmak için bir <xref:System.Windows.Media.Animation.Storyboard> bir özellik değeri değiştiğinde. Kullanabileceğiniz bir <xref:System.Windows.Trigger> içinde bir <xref:System.Windows.Style>, <xref:System.Windows.Controls.ControlTemplate>, veya <xref:System.Windows.DataTemplate>.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte bir <xref:System.Windows.Trigger> animasyon uygulamak için <xref:System.Windows.UIElement.Opacity%2A> , bir <xref:System.Windows.Controls.Button> olduğunda kendi <xref:System.Windows.UIElement.IsMouseOver%2A> özellik olur `true`.  
  
 [!code-xaml[AnimatePropertyStoryboards#PropertyTriggerExample](../../../../samples/snippets/xaml/VS_Snippets_Wpf/AnimatePropertyStoryboards/XAML/PropertyTriggerExample.xaml#propertytriggerexample)]  
  
 Özelliği tarafından uygulanan animasyonlar <xref:System.Windows.Trigger> nesneleri davranır daha karmaşık bir biçimde <xref:System.Windows.EventTrigger> animasyonlar veya animasyonları kullanılarak başlatılan <xref:System.Windows.Media.Animation.Storyboard> yöntemleri.  Bunlar animasyonlarla "iletim diğer tarafından tanımlanan" <xref:System.Windows.Trigger> nesneleri, ancak compose ile <xref:System.Windows.EventTrigger> ve animasyonlar yöntemi tetiklendi.  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Windows.Trigger>
- [Özellik Animasyon Tekniklerine Genel Bakış](../../../../docs/framework/wpf/graphics-multimedia/property-animation-techniques-overview.md)
- [Görsel Taslaklara Genel Bakış](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md)
