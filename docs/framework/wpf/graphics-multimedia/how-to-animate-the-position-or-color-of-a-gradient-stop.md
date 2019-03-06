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
ms.openlocfilehash: 6d8c1bb5cd133b2ee9d50a7e851d2ca3b4fff023
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57368892"
---
# <a name="how-to-animate-the-position-or-color-of-a-gradient-stop"></a>Nasıl yapılır: Gradyan Duraklarının Konumuna veya Rengine Animasyon Ekleme
Bu örnek, animasyon ekleme işlemi gösterilmektedir <xref:System.Windows.Media.GradientStop.Color%2A> ve <xref:System.Windows.Media.GradientStop.Offset%2A> , <xref:System.Windows.Media.GradientStop> nesneleri.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek üç gradyan durağını içinde canlandırır bir <xref:System.Windows.Media.LinearGradientBrush>. Örnek üç animasyon, her biri farklı bir gradyan durağını canlandırır kullanır:  
  
-   İlk animasyon, bir <xref:System.Windows.Media.Animation.DoubleAnimation>, ilk gradyan durağının <xref:System.Windows.Media.GradientStop.Offset%2A> 0,0-1.0 0.0 yeniden. Sonuç olarak, ilk sağ tarafındaki dikdörtgenin sol taraftaki gradyan kaydırılır, renk ve ardından sol tarafa yeniden.  
  
-   İkinci animasyon bir <xref:System.Windows.Media.Animation.ColorAnimation>, ikinci gradyan durağının <xref:System.Windows.Media.GradientStop.Color%2A> gelen <xref:System.Windows.Media.Colors.Purple%2A> için <xref:System.Windows.Media.Colors.Yellow%2A> ve ardından yeniden <xref:System.Windows.Media.Colors.Purple%2A>. Sonuç olarak, Orta Gradyan Rengi sarı ve mor dön mor değiştirir.  
  
-   Üçüncü animasyon, başka bir <xref:System.Windows.Media.Animation.ColorAnimation>, üçüncü gradyan durağının saydamlığını canlandırır <xref:System.Windows.Media.GradientStop.Color%2A> göre -1 ve ardından yeniden. Sonuç olarak, üçüncü bir renk gradyanı, kaybolur ve daha sonra yeniden donuk olur.  
  
 [!code-csharp[BrushesIntroduction_snip#GraphicsMMGradientAnimationExamplesWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/GradientStopAnimationExample.cs#graphicsmmgradientanimationexampleswholepage)]
 [!code-vb[BrushesIntroduction_snip#GraphicsMMGradientAnimationExamplesWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/gradientstopanimationexample.vb#graphicsmmgradientanimationexampleswholepage)]
 [!code-xaml[BrushesIntroduction_snip#GraphicsMMGradientAnimationExamplesWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/GradientStopAnimationExample.xaml#graphicsmmgradientanimationexampleswholepage)]  
  
 Bu örnekte rağmen bir <xref:System.Windows.Media.LinearGradientBrush>, aynı animasyon ekleme işlemidir <xref:System.Windows.Media.GradientStop> içindeki nesneleri bir <xref:System.Windows.Media.RadialGradientBrush>.  
  
 Diğer örnekler için [Fırçalar örnek](https://go.microsoft.com/fwlink/?LinkID=159973).  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Windows.Media.GradientStop>
- [Animasyona Genel bakış](animation-overview.md)
- [Görsel Taslaklara Genel Bakış](storyboards-overview.md)
