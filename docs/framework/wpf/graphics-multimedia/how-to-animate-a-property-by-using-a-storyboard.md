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
ms.openlocfilehash: 6cfce9a5b070a23ed9ac03473888bf572b61393b
ms.sourcegitcommit: f8c36054eab877de4d40a705aacafa2552ce70e9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/31/2019
ms.locfileid: "75559644"
---
# <a name="how-to-animate-a-property-by-using-a-storyboard"></a>Nasıl yapılır: Görsel Taslak Kullanarak Özelliğe Animasyon Ekleme
Bu örnek, özellikleri hareketlendirmek için bir <xref:System.Windows.Media.Animation.Storyboard> nasıl kullanacağınızı gösterir. Bir <xref:System.Windows.Media.Animation.Storyboard>kullanarak bir özelliğe animasyon uygulamak için, hareketlendirmek istediğiniz her özellik için bir animasyon oluşturun ve ayrıca animasyonları içeren bir <xref:System.Windows.Media.Animation.Storyboard> oluşturun.  
  
 Özelliğin türü, kullanılacak animasyonun türünü belirler. Örneğin, <xref:System.Double> değerler alan bir özelliğe animasyon eklemek için bir <xref:System.Windows.Media.Animation.DoubleAnimation>kullanın. <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> ve <xref:System.Windows.Media.Animation.Storyboard.TargetProperty> eklenmiş özellikler, animasyonun uygulandığı nesne ve özelliği belirtir.  
  
 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]bir film şeridini başlatmak için <xref:System.Windows.Media.Animation.BeginStoryboard> eylemi ve bir <xref:System.Windows.EventTrigger>kullanın. <xref:System.Windows.EventTrigger>, <xref:System.Windows.EventTrigger.RoutedEvent%2A> özelliği tarafından belirtilen olay gerçekleştiğinde <xref:System.Windows.Media.Animation.BeginStoryboard> eyleme başlar. <xref:System.Windows.Media.Animation.BeginStoryboard> eylem <xref:System.Windows.Media.Animation.Storyboard>başlatır.  
  
 Aşağıdaki örnek iki <xref:System.Windows.Controls.Button> denetimine animasyon uygulamak için <xref:System.Windows.Media.Animation.Storyboard> nesnelerini kullanır. İlk düğmenin boyut olarak değiştirilmesini sağlamak için, <xref:System.Windows.FrameworkElement.Width%2A> canlandırılır. İkinci düğme rengini değiştirmek için, <xref:System.Windows.Media.SolidColorBrush> <xref:System.Windows.Media.SolidColorBrush.Color%2A> özelliği, hareketlendirilen düğmenin <xref:System.Windows.Controls.Control.Background%2A> ayarlamak için kullanılır.  
  
## <a name="example"></a>Örnek  
 [!code-xaml[AnimatePropertyStoryboards#1](~/samples/snippets/xaml/VS_Snippets_Wpf/AnimatePropertyStoryboards/XAML/StoryboardExample.xaml#1)]  
  
> [!NOTE]
> Animasyonlar, <xref:System.Windows.Controls.Control> veya <xref:System.Windows.Controls.Panel>gibi bir <xref:System.Windows.FrameworkElement> nesnesini ve <xref:System.Windows.Media.Brush> veya <xref:System.Windows.Media.Transform>gibi bir <xref:System.Windows.Freezable> nesnesini hedefleyebilir, ancak yalnızca Framework öğelerinde bir <xref:System.Windows.FrameworkElement.Name%2A> özelliği vardır. Bir animasyonuna bir ad atamak için, bir animasyon tarafından hedeflenebilmesi için, önceki örnekte gösterildiği gibi [X:Name yönergesini](../../../desktop-wpf/xaml-services/xname-directive.md)kullanın.  
  
 Kod kullanırsanız, bir <xref:System.Windows.FrameworkElement> için <xref:System.Windows.NameScope> oluşturmanız ve bu <xref:System.Windows.FrameworkElement>animasyon uygulamak için nesnelerin adlarını kaydetmeniz gerekir. Koddaki animasyonları başlatmak için <xref:System.Windows.EventTrigger>bir <xref:System.Windows.Media.Animation.BeginStoryboard> eylemi kullanın. İsteğe bağlı olarak, bir olay işleyicisi ve <xref:System.Windows.Media.Animation.Storyboard><xref:System.Windows.Media.Animation.Storyboard.Begin%2A> yöntemi kullanabilirsiniz. Aşağıdaki örnek, <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> yönteminin nasıl kullanılacağını gösterir.  
  
 [!code-csharp[AnimatePropertyStoryboards#11](~/samples/snippets/csharp/VS_Snippets_Wpf/AnimatePropertyStoryboards/CSharp/StoryboardExample.cs#11)]
 [!code-vb[AnimatePropertyStoryboards#11](~/samples/snippets/visualbasic/VS_Snippets_Wpf/AnimatePropertyStoryboards/VisualBasic/StoryboardExample.vb#11)]  
  
 Animasyon ve film şeritleri hakkında daha fazla bilgi için bkz. [animasyon genel bakış](animation-overview.md).  
  
 Kod kullanırsanız, özellikleri hareketlendirmek için <xref:System.Windows.Media.Animation.Storyboard> nesneleri kullanma sınırlandırırsınız. Daha fazla bilgi ve örnek için bkz. [görsel taslak kullanmadan özelliğe animasyon ekleme](how-to-animate-a-property-without-using-a-storyboard.md) ve bir [animasyon saati kullanarak bir özelliğe animasyon ekleme](how-to-animate-a-property-by-using-an-animationclock.md).
