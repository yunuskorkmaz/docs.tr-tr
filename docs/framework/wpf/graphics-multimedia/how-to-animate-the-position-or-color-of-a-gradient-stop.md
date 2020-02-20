---
title: 'Nasıl yapılır: Gradyan Duraklarının Konumuna veya Rengine Animasyon Ekleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- position [WPF], animating
- animation [WPF], position of GradientStop objects
- GradientStop objects [WPF], animating color of
- colors [WPF], animating
- animation [WPF], color of GradientStop objects
- GradientStop objects [WPF], animating position of
ms.assetid: 6f5b8b47-6c32-4b8e-98ee-fdf6515ec843
ms.openlocfilehash: aeae33f5f3c8016808988f58d61969e9b6f05039
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452850"
---
# <a name="how-to-animate-the-position-or-color-of-a-gradient-stop"></a>Nasıl yapılır: Gradyan Duraklarının Konumuna veya Rengine Animasyon Ekleme
Bu örnek, <xref:System.Windows.Media.GradientStop> nesnelerinin <xref:System.Windows.Media.GradientStop.Color%2A> ve <xref:System.Windows.Media.GradientStop.Offset%2A> nasıl hareketlendirileceğini gösterir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, <xref:System.Windows.Media.LinearGradientBrush>içinde üç gradyan durağını hareketlendirir. Örnek, her biri farklı bir gradyan durağını canlandırarak üç animasyon kullanır:  
  
- İlk animasyon, bir <xref:System.Windows.Media.Animation.DoubleAnimation>, ilk gradyan durağının <xref:System.Windows.Media.GradientStop.Offset%2A> 0,0 ' den 1,0 ' ye ve ardından 0,0 ' a geri hareketlenir. Sonuç olarak, gradyanın ilk rengi, dikdörtgenin sol tarafından sağ tarafına ve ardından sol tarafa geri kayar.  
  
- İkinci animasyon, bir <xref:System.Windows.Media.Animation.ColorAnimation>, ikinci gradyan durağının <xref:System.Windows.Media.GradientStop.Color%2A> <xref:System.Windows.Media.Colors.Purple%2A> <xref:System.Windows.Media.Colors.Yellow%2A> ve daha sonra <xref:System.Windows.Media.Colors.Purple%2A>'e geri hareketlendirir. Sonuç olarak, gradyanın ortadaki rengi mor ve mor olarak değişir.  
  
- Üçüncü animasyon, başka bir <xref:System.Windows.Media.Animation.ColorAnimation>, üçüncü gradyan durağının <xref:System.Windows.Media.GradientStop.Color%2A> saydamlığını-1 ve sonra geri hareketlendirir. Sonuç olarak, gradyanın üçüncü rengi kaybolur ve sonra yeniden donuk hale gelir.  
  
 [!code-csharp[BrushesIntroduction_snip#GraphicsMMGradientAnimationExamplesWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/GradientStopAnimationExample.cs#graphicsmmgradientanimationexampleswholepage)]
 [!code-vb[BrushesIntroduction_snip#GraphicsMMGradientAnimationExamplesWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/gradientstopanimationexample.vb#graphicsmmgradientanimationexampleswholepage)]
 [!code-xaml[BrushesIntroduction_snip#GraphicsMMGradientAnimationExamplesWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/GradientStopAnimationExample.xaml#graphicsmmgradientanimationexampleswholepage)]  
  
 Bu örnek bir <xref:System.Windows.Media.LinearGradientBrush>kullansa da, işlem <xref:System.Windows.Media.RadialGradientBrush>içindeki <xref:System.Windows.Media.GradientStop> nesneleri hareketlendirmek için aynıdır.  
  
 Daha fazla örnek için bkz. [fırçalar örneği](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Brushes).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Media.GradientStop>
- [Animasyona Genel bakış](animation-overview.md)
- [Görsel Taslaklara Genel Bakış](storyboards-overview.md)
