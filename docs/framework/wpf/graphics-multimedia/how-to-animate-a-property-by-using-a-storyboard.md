---
title: "Nasıl yapılır: Görsel Taslak Kullanarak Özelliğe Animasyon Ekleme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- animation [WPF], Storyboards
- Storyboards [WPF], animation
ms.assetid: f4a314e9-1da2-4367-85fc-1232487efa7a
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ba6cb3483c983ddbcd3fac2281fe40aef31301b4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-animate-a-property-by-using-a-storyboard"></a>Nasıl yapılır: Görsel Taslak Kullanarak Özelliğe Animasyon Ekleme
Bu örnek nasıl kullanılacağını gösteren bir <xref:System.Windows.Media.Animation.Storyboard> özelliklerine animasyon uygulamak için. Bir özellik kullanarak animasyon için bir <xref:System.Windows.Media.Animation.Storyboard>, animasyon ve ayrıca oluşturmak istediğiniz her bir özellik için bir animasyon oluşturmak bir <xref:System.Windows.Media.Animation.Storyboard> animasyonları içermesi için.  
  
 Özelliğin türünü kullanmak için animasyon türünü belirler. Örneğin, alan bir özelliği animasyon için <xref:System.Double> değerleri kullanan bir <xref:System.Windows.Media.Animation.DoubleAnimation>. <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> Ve <xref:System.Windows.Media.Animation.Storyboard.TargetProperty%2A> ekli özellikler nesne ve animasyonun uygulandığı özelliğini belirtin.  
  
 Film şeridi başlatmak için [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], kullanan bir <xref:System.Windows.Media.Animation.BeginStoryboard> eylem ve bir <xref:System.Windows.EventTrigger>. <xref:System.Windows.EventTrigger> Başlar <xref:System.Windows.Media.Animation.BeginStoryboard> olay olduğunda eylem tarafından belirtilen kendi <xref:System.Windows.EventTrigger.RoutedEvent%2A> özelliği oluşur. <xref:System.Windows.Media.Animation.BeginStoryboard> Eylemi başlatır <xref:System.Windows.Media.Animation.Storyboard>.  
  
 Aşağıdaki örnek kullanır <xref:System.Windows.Media.Animation.Storyboard> iki animasyon nesnelere <xref:System.Windows.Controls.Button> kontrol eder. İlk düğmenin boyutunu değiştirmek için kendi <xref:System.Windows.FrameworkElement.Width%2A> animasyon eklenir. İkinci düğmenin rengini değiştirmek için <xref:System.Windows.Media.SolidColorBrush.Color%2A> özelliği <xref:System.Windows.Media.SolidColorBrush> ayarlamak için kullanılan <xref:System.Windows.Controls.Control.Background%2A> animasyonlu düğmesinin.  
  
## <a name="example"></a>Örnek  
 [!code-xaml[AnimatePropertyStoryboards#1](../../../../samples/snippets/xaml/VS_Snippets_Wpf/AnimatePropertyStoryboards/XAML/StoryboardExample.xaml#1)]  
  
> [!NOTE]
>  Animasyonların hem de hedef alabilmesine rağmen bir <xref:System.Windows.FrameworkElement> nesne gibi bir <xref:System.Windows.Controls.Control> veya <xref:System.Windows.Controls.Panel>ve bir <xref:System.Windows.Freezable> nesnesi, gibi bir <xref:System.Windows.Media.Brush> veya <xref:System.Windows.Media.Transform>, yalnızca Çerçeve öğelerine sahip bir <xref:System.Windows.FrameworkElement.Name%2A> özelliği. Böylece bir animasyon tarafından hedeflenebilir bir ad için freezable atamak için kullandığınız [x: Name yönergesi](../../../../docs/framework/xaml-services/x-name-directive.md), önceki örnekte de görüldüğü gibi.  
  
 Kod kullanırsanız, oluşturmalısınız bir <xref:System.Windows.NameScope> için bir <xref:System.Windows.FrameworkElement> ve nesneleri ile animasyon adlarını kaydetme <xref:System.Windows.FrameworkElement>. Kod içinde animasyonları başlatmak için kullanmak bir <xref:System.Windows.Media.Animation.BeginStoryboard> eylemiyle bir <xref:System.Windows.EventTrigger>. İsteğe bağlı olarak, bir olay işleyicisi kullanabilirsiniz ve <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> yöntemi <xref:System.Windows.Media.Animation.Storyboard>. Aşağıdaki örnekte nasıl kullanılacağını gösterir <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> yöntemi.  
  
 [!code-csharp[AnimatePropertyStoryboards#11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AnimatePropertyStoryboards/CSharp/StoryboardExample.cs#11)]
 [!code-vb[AnimatePropertyStoryboards#11](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/AnimatePropertyStoryboards/VisualBasic/StoryboardExample.vb#11)]  
  
 Animasyon ve film şeritleri hakkında daha fazla bilgi için bkz: [animasyon genel bakış](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md).  
  
 Kod kullanırsanız, kullanmaya sınırlı değildir <xref:System.Windows.Media.Animation.Storyboard> özelliklerine animasyon için nesneleri. Daha fazla bilgi ve örnekler için bkz: [özelliği olmadan kullanarak bir film şeridi animasyon](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-without-using-a-storyboard.md) ve [AnimationClock kullanarak bir özelliği animasyon](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-by-using-an-animationclock.md).
