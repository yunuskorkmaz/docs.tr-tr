---
title: 'Nasıl yapılır: Görsel Taslak Kullanarak Özelliğe Animasyon Ekleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- animation [WPF], Storyboards
- Storyboards [WPF], animation
ms.assetid: f4a314e9-1da2-4367-85fc-1232487efa7a
ms.openlocfilehash: f6064368b4f5e4fa8324b4039d734d4430cd9174
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61761214"
---
# <a name="how-to-animate-a-property-by-using-a-storyboard"></a>Nasıl yapılır: Görsel Taslak Kullanarak Özelliğe Animasyon Ekleme
Bu örnek nasıl kullanılacağını gösterir. bir <xref:System.Windows.Media.Animation.Storyboard> özelliklerine animasyon uygulamak için. Kullanarak bir özelliğe animasyon ekleme için bir <xref:System.Windows.Media.Animation.Storyboard>, animasyon ve ayrıca oluşturmak istediğiniz her bir özellik için bir animasyon oluşturmak bir <xref:System.Windows.Media.Animation.Storyboard> animasyonları içermesi için.  
  
 Özelliğin türünü kullanmak için animasyon türünü belirler. Örneğin, alan özelliği oynatmak <xref:System.Double> değerleri kullanan bir <xref:System.Windows.Media.Animation.DoubleAnimation>. <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> Ve <xref:System.Windows.Media.Animation.Storyboard.TargetProperty> iliştirilmiş özellikler animasyon uygulanan bir özellik ve nesne belirtin.  
  
 İçinde bir film şeridi başlatmak için [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], kullanan bir <xref:System.Windows.Media.Animation.BeginStoryboard> eylem ve bir <xref:System.Windows.EventTrigger>. <xref:System.Windows.EventTrigger> Başlar <xref:System.Windows.Media.Animation.BeginStoryboard> olay olduğunda bir eylem tarafından belirtilen kendi <xref:System.Windows.EventTrigger.RoutedEvent%2A> özelliği gerçekleşir. <xref:System.Windows.Media.Animation.BeginStoryboard> Eylemi başlatıldığında <xref:System.Windows.Media.Animation.Storyboard>.  
  
 Aşağıdaki örnekte <xref:System.Windows.Media.Animation.Storyboard> iki animasyon uygulamak için nesneleri <xref:System.Windows.Controls.Button> kontrol eder. İlk düğmenin boyutu değiştirmek için kendi <xref:System.Windows.FrameworkElement.Width%2A> bir animasyon görünür. İkinci düğmenin rengini değiştirmek için <xref:System.Windows.Media.SolidColorBrush.Color%2A> özelliği <xref:System.Windows.Media.SolidColorBrush> ayarlamak için kullanılan <xref:System.Windows.Controls.Control.Background%2A> animasyonlu düğme.  
  
## <a name="example"></a>Örnek  
 [!code-xaml[AnimatePropertyStoryboards#1](~/samples/snippets/xaml/VS_Snippets_Wpf/AnimatePropertyStoryboards/XAML/StoryboardExample.xaml#1)]  
  
> [!NOTE]
>  Animasyonları'nın hem de hedef rağmen bir <xref:System.Windows.FrameworkElement> nesne gibi bir <xref:System.Windows.Controls.Control> veya <xref:System.Windows.Controls.Panel>ve <xref:System.Windows.Freezable> nesne gibi bir <xref:System.Windows.Media.Brush> veya <xref:System.Windows.Media.Transform>, yalnızca Çerçeve öğelerine sahip bir <xref:System.Windows.FrameworkElement.Name%2A> özelliği. Böylece bir animasyon tarafından hedeflenen bir ad için freezable atamak için kullanın [x: Name yönergesi](../../xaml-services/x-name-directive.md)önceki örnekte gösterildiği gibi.  
  
 Kodu kullanırsanız oluşturmalısınız bir <xref:System.Windows.NameScope> için bir <xref:System.Windows.FrameworkElement> ve ile animasyon uygulamak için nesnelerin adlarını kaydetme <xref:System.Windows.FrameworkElement>. Kod içinde animasyonları başlatmak için kullanmak bir <xref:System.Windows.Media.Animation.BeginStoryboard> eylemiyle bir <xref:System.Windows.EventTrigger>. İsteğe bağlı olarak, bir olay işleyicisi kullanabilirsiniz ve <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> yöntemi <xref:System.Windows.Media.Animation.Storyboard>. Aşağıdaki örnek nasıl kullanılacağını gösterir <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> yöntemi.  
  
 [!code-csharp[AnimatePropertyStoryboards#11](~/samples/snippets/csharp/VS_Snippets_Wpf/AnimatePropertyStoryboards/CSharp/StoryboardExample.cs#11)]
 [!code-vb[AnimatePropertyStoryboards#11](~/samples/snippets/visualbasic/VS_Snippets_Wpf/AnimatePropertyStoryboards/VisualBasic/StoryboardExample.vb#11)]  
  
 Animasyon ve görsel Taslaklar hakkında daha fazla bilgi için bkz: [animasyona genel bakış](animation-overview.md).  
  
 Kodu kullanırsanız kullanarak sınırlı olmamak <xref:System.Windows.Media.Animation.Storyboard> özelliklerine animasyon uygulamak için nesne. Daha fazla bilgi ve örnekler için bkz. [özelliği olmadan kullanarak bir görsel taslak animasyon](how-to-animate-a-property-without-using-a-storyboard.md) ve [AnimationClock kullanarak bir özelliğe animasyon ekleme](how-to-animate-a-property-by-using-an-animationclock.md).
