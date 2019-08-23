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
ms.openlocfilehash: a7a2656d84d37d3e2726df009a07ccf29661df07
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69963038"
---
# <a name="how-to-animate-a-property-by-using-a-storyboard"></a>Nasıl yapılır: Görsel Taslak Kullanarak Özelliğe Animasyon Ekleme
Bu örnek, özellikleri hareketlendirmek <xref:System.Windows.Media.Animation.Storyboard> için nasıl kullanılacağını gösterir. Kullanarak <xref:System.Windows.Media.Animation.Storyboard>bir özelliğe animasyon uygulamak için, hareketlendirmek istediğiniz her özellik için bir animasyon oluşturun ve ayrıca animasyonları içeren bir <xref:System.Windows.Media.Animation.Storyboard> oluşturun.  
  
 Özelliğin türü, kullanılacak animasyonun türünü belirler. Örneğin, değer alan <xref:System.Double> bir özelliğe animasyon uygulamak için bir <xref:System.Windows.Media.Animation.DoubleAnimation>kullanın. <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> Ve<xref:System.Windows.Media.Animation.Storyboard.TargetProperty> Ekli özellikler, animasyonun uygulandığı nesne ve özelliği belirtir.  
  
 İçinde [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]bir film şeridi başlatmak için bir <xref:System.Windows.Media.Animation.BeginStoryboard> eylem ve bir <xref:System.Windows.EventTrigger>kullanın. , <xref:System.Windows.EventTrigger> Özelliği<xref:System.Windows.EventTrigger.RoutedEvent%2A> tarafından <xref:System.Windows.Media.Animation.BeginStoryboard> belirtilen olay gerçekleştiğinde eyleme başlar. <xref:System.Windows.Media.Animation.BeginStoryboard> Eylem öğesini <xref:System.Windows.Media.Animation.Storyboard>başlatır.  
  
 Aşağıdaki örnek, iki <xref:System.Windows.Media.Animation.Storyboard> <xref:System.Windows.Controls.Button> denetimi hareketlendirmek için nesneleri kullanır. İlk düğmenin boyut <xref:System.Windows.FrameworkElement.Width%2A> olarak değiştirilmesini sağlamak için animasyon canlandırılır. İkinci düğme rengini değiştirmek için, <xref:System.Windows.Media.SolidColorBrush.Color%2A> <xref:System.Windows.Media.SolidColorBrush> öğesinin özelliği, hareketlendirilen düğmenin öğesini ayarlamak <xref:System.Windows.Controls.Control.Background%2A> için kullanılır.  
  
## <a name="example"></a>Örnek  
 [!code-xaml[AnimatePropertyStoryboards#1](~/samples/snippets/xaml/VS_Snippets_Wpf/AnimatePropertyStoryboards/XAML/StoryboardExample.xaml#1)]  
  
> [!NOTE]
> Animasyonlar <xref:System.Windows.FrameworkElement> , <xref:System.Windows.Freezable> <xref:System.Windows.FrameworkElement.Name%2A> veya gibibir<xref:System.Windows.Media.Brush> nesneyi ve ya<xref:System.Windows.Media.Transform>da gibi bir nesneyi hedefleyebilir, ancak yalnızca Framework öğelerinde bir özelliği vardır. <xref:System.Windows.Controls.Panel> <xref:System.Windows.Controls.Control> Bir animasyonuna bir ad atamak için, bir animasyon tarafından hedeflenebilmesi için, önceki örnekte gösterildiği gibi [X:Name yönergesini](../../xaml-services/x-name-directive.md)kullanın.  
  
 Kod kullanırsanız, bir <xref:System.Windows.NameScope> <xref:System.Windows.FrameworkElement> için bir oluşturmanız ve animasyon eklemek için <xref:System.Windows.FrameworkElement>nesnelerin adlarını kaydetmeniz gerekir. Koddaki animasyonları başlatmak için <xref:System.Windows.Media.Animation.BeginStoryboard> <xref:System.Windows.EventTrigger>ile bir eylem kullanın. İsteğe bağlı olarak, bir olay işleyicisi ve <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> <xref:System.Windows.Media.Animation.Storyboard>yöntemini kullanabilirsiniz. Aşağıdaki örnek <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> yönteminin nasıl kullanılacağını gösterir.  
  
 [!code-csharp[AnimatePropertyStoryboards#11](~/samples/snippets/csharp/VS_Snippets_Wpf/AnimatePropertyStoryboards/CSharp/StoryboardExample.cs#11)]
 [!code-vb[AnimatePropertyStoryboards#11](~/samples/snippets/visualbasic/VS_Snippets_Wpf/AnimatePropertyStoryboards/VisualBasic/StoryboardExample.vb#11)]  
  
 Animasyon ve film şeritleri hakkında daha fazla bilgi için bkz. [animasyon genel bakış](animation-overview.md).  
  
 Kod kullanırsanız, özellikleri hareketlendirmek için nesneleri kullanma <xref:System.Windows.Media.Animation.Storyboard> sınırlı değildir. Daha fazla bilgi ve örnek için bkz. [görsel taslak kullanmadan özelliğe animasyon ekleme](how-to-animate-a-property-without-using-a-storyboard.md) ve bir [animasyon saati kullanarak bir özelliğe animasyon ekleme](how-to-animate-a-property-by-using-an-animationclock.md).
