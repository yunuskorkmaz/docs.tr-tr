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
# <a name="how-to-trigger-an-animation-when-a-property-value-changes"></a>Nasıl yapılır: Özellik Değeri Değiştiğinde bir Animasyonu Tetikleme
Bu örnek nasıl kullanılacağını gösteren bir <xref:System.Windows.Trigger> başlatmak için bir <xref:System.Windows.Media.Animation.Storyboard> bir özellik değeri değiştiğinde. Kullanabileceğiniz bir <xref:System.Windows.Trigger> içinde bir <xref:System.Windows.Style>, <xref:System.Windows.Controls.ControlTemplate>, veya <xref:System.Windows.DataTemplate>.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek kullanan bir <xref:System.Windows.Trigger> animasyon için <xref:System.Windows.UIElement.Opacity%2A> , bir <xref:System.Windows.Controls.Button> zaman kendi <xref:System.Windows.UIElement.IsMouseOver%2A> özellik olur `true`.  
  
 [!code-xaml[AnimatePropertyStoryboards#PropertyTriggerExample](../../../../samples/snippets/xaml/VS_Snippets_Wpf/AnimatePropertyStoryboards/XAML/PropertyTriggerExample.xaml#propertytriggerexample)]  
  
 Özelliği tarafından uygulanan bir animasyon <xref:System.Windows.Trigger> nesneleri davranırlar daha karmaşık bir şekilde <xref:System.Windows.EventTrigger> animasyonları veya animasyonları kullanılarak başlatılan <xref:System.Windows.Media.Animation.Storyboard> yöntemleri.  Bunlar animasyonları ile "iletimi diğer tarafından tanımlanan" <xref:System.Windows.Trigger> nesneleri, ancak oluşturma ile <xref:System.Windows.EventTrigger> ve yöntemi tetiklenen animasyonları.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Trigger>  
 [Özellik Animasyon Tekniklerine Genel Bakış](../../../../docs/framework/wpf/graphics-multimedia/property-animation-techniques-overview.md)  
 [Film şeritleri genel bakış](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md)
