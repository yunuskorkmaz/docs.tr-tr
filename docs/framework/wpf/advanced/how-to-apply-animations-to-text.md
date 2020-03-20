---
title: 'Nasıl yapılır: Metne Animasyon Uygulama'
ms.date: 03/30/2017
helpviewer_keywords:
- typography [WPF], animations
- animation [WPF], text
ms.assetid: eec3d26c-0a21-420f-8012-671621c47089
ms.openlocfilehash: ed2f3beb904f724ac93e2c4033aa6b2eb3fa1290
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174634"
---
# <a name="how-to-apply-animations-to-text"></a>Nasıl yapılır: Metne Animasyon Uygulama
Animasyonlar, uygulamanızdaki metnin görünümünü ve görünümünü değiştirebilir. Aşağıdaki örnekler, denetimdeki <xref:System.Windows.Controls.TextBlock> metnin görüntülenmesini etkilemek için farklı animasyon türleri kullanır.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte <xref:System.Windows.Media.Animation.DoubleAnimation> metin bloğunun genişliğini canlandırmak için a kullanır. Genişlik değeri metin bloğunun genişliğinden 10 saniye lik bir süre içinde 0'a değişir ve ardından genişlik değerlerini tersine çevirir ve devam eder. Bu tür animasyonlar silme efekti oluşturur.  
  
 [!code-xaml[TextAnimationSample#TextAnimationSample1](~/samples/snippets/csharp/VS_Snippets_Wpf/TextAnimationSample/CS/Window1.xaml#textanimationsample1)]  
  
 Aşağıdaki örnekte <xref:System.Windows.Media.Animation.DoubleAnimation> metin bloğunun opaklığını canlandırmak için a kullanır. Opaklık değeri 5 saniyelik bir süre içinde 1,0'dan 0'a değişir ve sonra opaklık değerlerini tersine çevirir ve devam eder.  
  
 [!code-xaml[TextAnimationSample#TextAnimationSample2](~/samples/snippets/csharp/VS_Snippets_Wpf/TextAnimationSample/CS/Window1.xaml#textanimationsample2)]  
  
 Aşağıdaki <xref:System.Windows.Controls.TextBlock> diyagram, denetimin opaklığını `1.00` `0.00` 5 <xref:System.Windows.Media.Animation.Timeline.Duration%2A>saniyelik aralıktan .  
  
 ![Donukluğu 1,00'den 0,00'a değiştiren metin.](./media/how-to-apply-animations-to-text/faded-text-opacity-change.png)  

 Aşağıdaki örnekte, <xref:System.Windows.Media.Animation.ColorAnimation> metin bloğunun ön plan rengini canlandırmak için a kullanır. Ön plan renk değeri 5 saniye lik bir süre içinde bir renkten ikinci renge dönüşür ve ardından renk değerlerini tersine çevirir ve devam eder.  
  
 [!code-xaml[TextAnimationSample#TextAnimationSample3](~/samples/snippets/csharp/VS_Snippets_Wpf/TextAnimationSample/CS/Window1.xaml#textanimationsample3)]  
  
 Aşağıdaki örnekte <xref:System.Windows.Media.Animation.DoubleAnimation> metin bloğunu döndürmek için a kullanır. Metin bloğu 20 saniye boyunca tam bir döndürme gerçekleştirir ve sonra döndürmeyi yinelemeye devam eder.  
  
 [!code-xaml[TextAnimationSample#TextAnimationSample4](~/samples/snippets/csharp/VS_Snippets_Wpf/TextAnimationSample/CS/Window1.xaml#textanimationsample4)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Animasyona Genel bakış](../graphics-multimedia/animation-overview.md)
