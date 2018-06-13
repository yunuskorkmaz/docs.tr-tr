---
title: 'Nasıl yapılır: Metne Animasyon Uygulama'
ms.date: 03/30/2017
helpviewer_keywords:
- typography [WPF], animations
- animation [WPF], text
ms.assetid: eec3d26c-0a21-420f-8012-671621c47089
ms.openlocfilehash: 56a12ca915cc320619a094df38d118eabf202734
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33545444"
---
# <a name="how-to-apply-animations-to-text"></a>Nasıl yapılır: Metne Animasyon Uygulama
Animasyon, görüntüleme ve uygulamanızdaki metnin görünümünü değiştirebilirsiniz. Aşağıdaki örnekler farklı türdeki animasyonları metin görünümünü kullanın. bir <xref:System.Windows.Controls.TextBlock> denetim.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek kullanan bir <xref:System.Windows.Media.Animation.DoubleAnimation> metin bloğunun genişliğini animasyon uygulamak için. Genişlik değeri metin bloğunun genişliğini 10 saniye süresince 0 olarak değiştirir ve ardından genişlik değerleri tersine çevirir ve devam eder. Bu tür bir animasyon silme etkisi oluşturur.  
  
 [!code-xaml[TextAnimationSample#TextAnimationSample1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextAnimationSample/CS/Window1.xaml#textanimationsample1)]  
  
 Aşağıdaki örnek kullanan bir <xref:System.Windows.Media.Animation.DoubleAnimation> metin bloğunun geçirgenliğini animasyon uygulamak için. Geçirgenlik değeri 1.0 5 saniye süresince 0 olarak değiştirir ve ardından opaklık değerleri tersine çevirir ve devam eder.  
  
 [!code-xaml[TextAnimationSample#TextAnimationSample2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextAnimationSample/CS/Window1.xaml#textanimationsample2)]  
  
 Aşağıdaki diyagramda etkisini gösterir <xref:System.Windows.Controls.TextBlock> saydamlığını gelen değiştirme denetim `1.00` için `0.00` tarafından tanımlanan 5 saniyelik aralık boyunca <xref:System.Windows.Media.Animation.Timeline.Duration%2A>.  
  
 ![Opaklık 1.00 0,00 için değiştirme metin](../../../../docs/framework/wpf/advanced/media/fadedtext01.png "FadedText01")  
Metin geçirgenliği 1.00 0,00 için değiştirme  
  
 Aşağıdaki örnek kullanan bir <xref:System.Windows.Media.Animation.ColorAnimation> metin bloğu ön plan rengini animasyon uygulamak için. Ön plan rengi değeri bir renkten ikinci bir renge 5 saniye süresince değiştirir ve ardından renk değerleri tersine çevirir ve devam eder.  
  
 [!code-xaml[TextAnimationSample#TextAnimationSample3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextAnimationSample/CS/Window1.xaml#textanimationsample3)]  
  
 Aşağıdaki örnek kullanan bir <xref:System.Windows.Media.Animation.DoubleAnimation> metin bloğunu döndürmek için. Metin bloğu 20 saniye süresince tam dönmesini gerçekleştirir ve tekrar devam eder.  
  
 [!code-xaml[TextAnimationSample#TextAnimationSample4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextAnimationSample/CS/Window1.xaml#textanimationsample4)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Animasyona Genel bakış](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)
