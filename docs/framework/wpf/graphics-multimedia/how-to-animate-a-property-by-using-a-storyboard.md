---
title: 'Nasıl yapılır: Görsel Taslak Kullanarak Özelliğe Animasyon Ekleme'
description: Kullanıcı arayüzüne animasyon ve film şeridi (Windows Presentation Foundation (WPF) içindeki özellikler için canlandırın.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- animation [WPF], Storyboards
- Storyboards [WPF], animation
ms.assetid: f4a314e9-1da2-4367-85fc-1232487efa7a
ms.openlocfilehash: f21b606751b845905a7bde6d3a7658b214369cc6
ms.sourcegitcommit: b6a1869f97a37f11a68c90afde1a520a6887dcbc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/02/2020
ms.locfileid: "85853743"
---
# <a name="how-to-animate-a-property-by-using-a-storyboard"></a>Nasıl yapılır: Görsel Taslak Kullanarak Özelliğe Animasyon Ekleme
Bu örnek, <xref:System.Windows.Media.Animation.Storyboard> özellikleri hareketlendirmek için nasıl kullanılacağını gösterir. Kullanarak bir özelliğe animasyon uygulamak için <xref:System.Windows.Media.Animation.Storyboard> , hareketlendirmek istediğiniz her özellik için bir animasyon oluşturun ve ayrıca <xref:System.Windows.Media.Animation.Storyboard> animasyonları içeren bir oluşturun.  
  
 Özelliğin türü, kullanılacak animasyonun türünü belirler. Örneğin, değer alan bir özelliğe animasyon uygulamak için <xref:System.Double> bir kullanın <xref:System.Windows.Media.Animation.DoubleAnimation> . <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A>Ve <xref:System.Windows.Media.Animation.Storyboard.TargetProperty> Ekli özellikler, animasyonun uygulandığı nesne ve özelliği belirtir.  
  
 İçinde bir film şeridi başlatmak için [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] bir <xref:System.Windows.Media.Animation.BeginStoryboard> eylem ve bir kullanın <xref:System.Windows.EventTrigger> . , <xref:System.Windows.EventTrigger> <xref:System.Windows.Media.Animation.BeginStoryboard> Özelliği tarafından belirtilen olay gerçekleştiğinde eyleme başlar <xref:System.Windows.EventTrigger.RoutedEvent%2A> . <xref:System.Windows.Media.Animation.BeginStoryboard>Eylem öğesini başlatır <xref:System.Windows.Media.Animation.Storyboard> .  
  
 Aşağıdaki örnek, <xref:System.Windows.Media.Animation.Storyboard> iki denetimi hareketlendirmek için nesneleri kullanır <xref:System.Windows.Controls.Button> . İlk düğmenin boyut olarak değiştirilmesini sağlamak için <xref:System.Windows.FrameworkElement.Width%2A> animasyon canlandırılır. İkinci düğme rengini değiştirmek için, <xref:System.Windows.Media.SolidColorBrush.Color%2A> öğesinin özelliği, <xref:System.Windows.Media.SolidColorBrush> hareketlendirilen düğmenin öğesini ayarlamak için kullanılır <xref:System.Windows.Controls.Control.Background%2A> .  
  
## <a name="example"></a>Örnek  
 [!code-xaml[AnimatePropertyStoryboards#1](~/samples/snippets/xaml/VS_Snippets_Wpf/AnimatePropertyStoryboards/XAML/StoryboardExample.xaml#1)]  
  
> [!NOTE]
> Animasyonlar, veya gibi bir nesneyi ve ya da gibi bir nesneyi hedefleyebilir, ancak <xref:System.Windows.FrameworkElement> <xref:System.Windows.Controls.Control> <xref:System.Windows.Controls.Panel> <xref:System.Windows.Freezable> <xref:System.Windows.Media.Brush> <xref:System.Windows.Media.Transform> yalnızca Framework öğelerinde bir <xref:System.Windows.FrameworkElement.Name%2A> özelliği vardır. Bir animasyonuna bir ad atamak için, bir animasyon tarafından hedeflenebilmesi için, önceki örnekte gösterildiği gibi [X:Name yönergesini](../../../desktop-wpf/xaml-services/xname-directive.md)kullanın.  
  
 Kod kullanırsanız, <xref:System.Windows.NameScope> bir için bir oluşturmanız <xref:System.Windows.FrameworkElement> ve animasyon eklemek için nesnelerin adlarını kaydetmeniz gerekir <xref:System.Windows.FrameworkElement> . Koddaki animasyonları başlatmak için <xref:System.Windows.Media.Animation.BeginStoryboard> ile bir eylem kullanın <xref:System.Windows.EventTrigger> . İsteğe bağlı olarak, bir olay işleyicisi ve yöntemini kullanabilirsiniz <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> <xref:System.Windows.Media.Animation.Storyboard> . Aşağıdaki örnek yönteminin nasıl kullanılacağını gösterir <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> .  
  
 [!code-csharp[AnimatePropertyStoryboards#11](~/samples/snippets/csharp/VS_Snippets_Wpf/AnimatePropertyStoryboards/CSharp/StoryboardExample.cs#11)]
 [!code-vb[AnimatePropertyStoryboards#11](~/samples/snippets/visualbasic/VS_Snippets_Wpf/AnimatePropertyStoryboards/VisualBasic/StoryboardExample.vb#11)]  
  
 Animasyon ve film şeritleri hakkında daha fazla bilgi için bkz. [animasyon genel bakış](animation-overview.md).  
  
 Kod kullanırsanız, <xref:System.Windows.Media.Animation.Storyboard> özellikleri hareketlendirmek için nesneleri kullanma sınırlı değildir. Daha fazla bilgi ve örnek için bkz. [görsel taslak kullanmadan özelliğe animasyon ekleme](how-to-animate-a-property-without-using-a-storyboard.md) ve bir [animasyon saati kullanarak bir özelliğe animasyon ekleme](how-to-animate-a-property-by-using-an-animationclock.md).
