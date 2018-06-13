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
ms.openlocfilehash: 2eb528127c8aa66976788ec1f4e5362ca3a1ef26
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33558674"
---
# <a name="how-to-animate-the-position-or-color-of-a-gradient-stop"></a>Nasıl yapılır: Gradyan Duraklarının Konumuna veya Rengine Animasyon Ekleme
Bu örnek animasyon gösterilmektedir <xref:System.Windows.Media.GradientStop.Color%2A> ve <xref:System.Windows.Media.GradientStop.Offset%2A> , <xref:System.Windows.Media.GradientStop> nesneleri.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek içinde üç gradyan durakları canlandırır bir <xref:System.Windows.Media.LinearGradientBrush>. Örneğin, her biri farklı bir gradyan durağında canlandırır üç animasyon kullanır:  
  
-   İlk animasyon, bir <xref:System.Windows.Media.Animation.DoubleAnimation>, ilk gradyan durağının <xref:System.Windows.Media.GradientStop.Offset%2A> 1.0 için 0,0 ve 0,0 olarak yedekleyin. Sonuç olarak, ilk solundan gradyan kaydırmalar dikdörtgen sağ tarafındaki için renk ve sol tarafa yedekleyin.  
  
-   İkinci animasyon, bir <xref:System.Windows.Media.Animation.ColorAnimation>, ikinci gradyan durağının <xref:System.Windows.Media.GradientStop.Color%2A> gelen <xref:System.Windows.Media.Colors.Purple%2A> için <xref:System.Windows.Media.Colors.Yellow%2A> ve ardından yeniden <xref:System.Windows.Media.Colors.Purple%2A>. Sonuç olarak, geçişin orta rengi sarı daha sonra tekrar mor geçiş mor değiştirir.  
  
-   Üçüncü animasyon, başka bir <xref:System.Windows.Media.Animation.ColorAnimation>, üçüncü gradyan durağının saydamlığını canlandırır <xref:System.Windows.Media.GradientStop.Color%2A> -1 olarak ve ardından yeniden. Sonuç olarak, geçişin üçüncü rengi kaybolur ve tekrar donuk olur.  
  
 [!code-csharp[BrushesIntroduction_snip#GraphicsMMGradientAnimationExamplesWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/GradientStopAnimationExample.cs#graphicsmmgradientanimationexampleswholepage)]
 [!code-vb[BrushesIntroduction_snip#GraphicsMMGradientAnimationExamplesWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/gradientstopanimationexample.vb#graphicsmmgradientanimationexampleswholepage)]
 [!code-xaml[BrushesIntroduction_snip#GraphicsMMGradientAnimationExamplesWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/GradientStopAnimationExample.xaml#graphicsmmgradientanimationexampleswholepage)]  
  
 Bu örnek kullanıyor olsa da bir <xref:System.Windows.Media.LinearGradientBrush>, animasyon için aynı işlemidir <xref:System.Windows.Media.GradientStop> içindeki nesneleri bir <xref:System.Windows.Media.RadialGradientBrush>.  
  
 Ek örnekler için bkz: [Fırçalar örnek](http://go.microsoft.com/fwlink/?LinkID=159973).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Media.GradientStop>  
 [Animasyona Genel bakış](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [Görsel Taslaklara Genel Bakış](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md)
