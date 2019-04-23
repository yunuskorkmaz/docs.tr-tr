---
title: 'Nasıl yapılır: Metne Animasyon Uygulama'
ms.date: 03/30/2017
helpviewer_keywords:
- typography [WPF], animations
- animation [WPF], text
ms.assetid: eec3d26c-0a21-420f-8012-671621c47089
ms.openlocfilehash: 38aa432fecc5b5e10d8eb90be9c1c596728ed613
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59108218"
---
# <a name="how-to-apply-animations-to-text"></a>Nasıl yapılır: Metne Animasyon Uygulama
Animasyonları, görüntü ve metin uygulamanızın görünümünü değiştirebilirsiniz. Aşağıdaki örnekler animasyonları farklı türde metin görünümünü kullanın. bir <xref:System.Windows.Controls.TextBlock> denetimi.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte bir <xref:System.Windows.Media.Animation.DoubleAnimation> metin bloğu genişliğini animasyon uygulamak için. Genişlik değeri metin bloğunun genişliğini 0 olarak 10 saniye süresince değiştirir ve ardından genişlik değerleri tersine çevirir ve devam eder. Bu tür bir animasyon bir temizleme efekti oluşturur.  
  
 [!code-xaml[TextAnimationSample#TextAnimationSample1](~/samples/snippets/csharp/VS_Snippets_Wpf/TextAnimationSample/CS/Window1.xaml#textanimationsample1)]  
  
 Aşağıdaki örnekte bir <xref:System.Windows.Media.Animation.DoubleAnimation> metin bloğu opaklığına animasyon için. Geçirgenlik değeri 1.0 5 saniye süresince 0 olarak değiştirir ve ardından opaklık değerleri tersine çevirir ve devam eder.  
  
 [!code-xaml[TextAnimationSample#TextAnimationSample2](~/samples/snippets/csharp/VS_Snippets_Wpf/TextAnimationSample/CS/Window1.xaml#textanimationsample2)]  
  
 Aşağıdaki diyagramda etkisini gösterir <xref:System.Windows.Controls.TextBlock> gelen saydamlığını değiştirme denetimi `1.00` için `0.00` tarafından tanımlanan 5 saniyelik aralığına sırasında <xref:System.Windows.Media.Animation.Timeline.Duration%2A>.  
  
 ![Opaklık 1,00 0.00 değiştirme metni.](./media/how-to-apply-animations-to-text/faded-text-opacity-change.png)  
   
 Aşağıdaki örnekte bir <xref:System.Windows.Media.Animation.ColorAnimation> metin bloğu ön plan rengini animasyon uygulamak için. Ön plan rengi değer rengi 5 saniye süre içinde ikinci bir renge değişir ve ardından renk değerleri tersine çevirir ve devam eder.  
  
 [!code-xaml[TextAnimationSample#TextAnimationSample3](~/samples/snippets/csharp/VS_Snippets_Wpf/TextAnimationSample/CS/Window1.xaml#textanimationsample3)]  
  
 Aşağıdaki örnekte bir <xref:System.Windows.Media.Animation.DoubleAnimation> metin bloğu döndürmek için. Metin bloğu, tam bir dönüşü 20 saniye süresince gerçekleştirir ve ardından tekrar devam eder.  
  
 [!code-xaml[TextAnimationSample#TextAnimationSample4](~/samples/snippets/csharp/VS_Snippets_Wpf/TextAnimationSample/CS/Window1.xaml#textanimationsample4)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Animasyona Genel bakış](../graphics-multimedia/animation-overview.md)
