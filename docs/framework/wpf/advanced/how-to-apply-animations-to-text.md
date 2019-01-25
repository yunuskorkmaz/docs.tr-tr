---
title: 'Nasıl yapılır: Metne Animasyon Uygulama'
ms.date: 03/30/2017
helpviewer_keywords:
- typography [WPF], animations
- animation [WPF], text
ms.assetid: eec3d26c-0a21-420f-8012-671621c47089
ms.openlocfilehash: 56336c45639168c6432b92fe555c6d37448cb7cd
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54720515"
---
# <a name="how-to-apply-animations-to-text"></a>Nasıl yapılır: Metne Animasyon Uygulama
Animasyonları, görüntü ve metin uygulamanızın görünümünü değiştirebilirsiniz. Aşağıdaki örnekler animasyonları farklı türde metin görünümünü kullanın. bir <xref:System.Windows.Controls.TextBlock> denetimi.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte bir <xref:System.Windows.Media.Animation.DoubleAnimation> metin bloğu genişliğini animasyon uygulamak için. Genişlik değeri metin bloğunun genişliğini 0 olarak 10 saniye süresince değiştirir ve ardından genişlik değerleri tersine çevirir ve devam eder. Bu tür bir animasyon bir temizleme efekti oluşturur.  
  
 [!code-xaml[TextAnimationSample#TextAnimationSample1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextAnimationSample/CS/Window1.xaml#textanimationsample1)]  
  
 Aşağıdaki örnekte bir <xref:System.Windows.Media.Animation.DoubleAnimation> metin bloğu opaklığına animasyon için. Geçirgenlik değeri 1.0 5 saniye süresince 0 olarak değiştirir ve ardından opaklık değerleri tersine çevirir ve devam eder.  
  
 [!code-xaml[TextAnimationSample#TextAnimationSample2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextAnimationSample/CS/Window1.xaml#textanimationsample2)]  
  
 Aşağıdaki diyagramda etkisini gösterir <xref:System.Windows.Controls.TextBlock> gelen saydamlığını değiştirme denetimi `1.00` için `0.00` tarafından tanımlanan 5 saniyelik aralığına sırasında <xref:System.Windows.Media.Animation.Timeline.Duration%2A>.  
  
 ![Opaklık 1,00 0.00 değiştirme metni](../../../../docs/framework/wpf/advanced/media/fadedtext01.png "FadedText01")  
Metin opaklık 1,00 0.00 değiştirme  
  
 Aşağıdaki örnekte bir <xref:System.Windows.Media.Animation.ColorAnimation> metin bloğu ön plan rengini animasyon uygulamak için. Ön plan rengi değer rengi 5 saniye süre içinde ikinci bir renge değişir ve ardından renk değerleri tersine çevirir ve devam eder.  
  
 [!code-xaml[TextAnimationSample#TextAnimationSample3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextAnimationSample/CS/Window1.xaml#textanimationsample3)]  
  
 Aşağıdaki örnekte bir <xref:System.Windows.Media.Animation.DoubleAnimation> metin bloğu döndürmek için. Metin bloğu, tam bir dönüşü 20 saniye süresince gerçekleştirir ve ardından tekrar devam eder.  
  
 [!code-xaml[TextAnimationSample#TextAnimationSample4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextAnimationSample/CS/Window1.xaml#textanimationsample4)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Animasyona Genel bakış](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)
