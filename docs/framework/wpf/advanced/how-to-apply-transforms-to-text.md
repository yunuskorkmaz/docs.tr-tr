---
title: 'Nasıl yapılır: Metne Dönüşüm Uygulama'
ms.date: 03/30/2017
helpviewer_keywords:
- typography [WPF], rotated text
- typography [WPF], scaled text
- skewed text [WPF]
- typography [WPF], translated text
- typography [WPF], shadowed text
- rotated text [WPF]
- translated text [WPF]
- shadowed text [WPF]
- transforms in text [WPF]
- typography [WPF], transforms
- scaled text [WPF]
- typography [WPF], skewed text
ms.assetid: 0d61678a-4185-4f2a-85c6-c1d020f96fa0
ms.openlocfilehash: fd86293c539bf58ac93894e0b879dddb984825e1
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57378957"
---
# <a name="how-to-apply-transforms-to-text"></a>Nasıl yapılır: Metne Dönüşüm Uygulama
Dönüşümler uygulamanızda metin görünümünü değiştirebilirsiniz. Aşağıdaki örnekler işleme dönüşümleri farklı türde metin görünümünü kullanın. bir <xref:System.Windows.Controls.TextBlock> denetimi.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, iki boyutlu x-y düzlemleriyle içinde belirtilen bir noktadan döndürülen metni gösterir.  
  
 ![RotateTransform kullanılarak döndürülen metin](./media/transformedtext01.jpg "TransformedText01")  
90 derece döndürülmüş metin örneği  
  
 Aşağıdaki kod örneğinde bir <xref:System.Windows.Media.RotateTransform> metni döndürmek için. Bir <xref:System.Windows.Media.RotateTransform.Angle%2A> 90 değerini 90 derece saat yönünde öğeyi döndürür.  
  
 [!code-xaml[TextTransformSample#TextTransformSample1](~/samples/snippets/csharp/VS_Snippets_Wpf/TextTransformSample/CS/Window1.xaml#texttransformsample1)]  
  
 Aşağıdaki örnek, % 150 x ekseni boyunca ölçeği metnin ikinci satırı ve y ekseni boyunca % 150 ölçeklendirilmiş metin üçüncü satır gösterir.  
  
 ![ScaleTransform kullanılarak ölçeklendirilen metin](./media/transformedtext02.jpg "TransformedText02")  
Ölçeklendirilmiş metin örneği  
  
 Aşağıdaki kod örneğinde bir <xref:System.Windows.Media.ScaleTransform> özgün boyutuna ölçek metni için.  
  
 [!code-xaml[TextTransformSample#TextTransformSample2](~/samples/snippets/csharp/VS_Snippets_Wpf/TextTransformSample/CS/Window1.xaml#texttransformsample2)]  
  
> [!NOTE]
>  Metin ölçeklendirme metnin yazı tipi boyutunu artırma ile aynı değil. Yazı tipi boyutlarını birbirinden farklı boyutlarda en iyi çözüm sağlamak için hesaplanır. Ölçeklendirilmiş metin, diğer taraftan, özgün boyutunda metin oranlarını korur.  
  
 Aşağıdaki örnek x ekseni boyunca Eğilmiş metin gösterir.  
  
 ![SkewTransform kullanılarak Eğilmiş metin](./media/transformedtext03.jpg "TransformedText03")  
Eğilmiş metin örneği  
  
 Aşağıdaki kod örneğinde bir <xref:System.Windows.Media.SkewTransform> metin eğriltmek için. Bir eğme yamultma olarak da bilinen bir koordinat bir Tekdüzen olmayan şekilde uzatır bir dönüşümdür. Bu örnekte, iki metin dengesiz-30 ° ve x koordinatını boyunca 30 ° dizelerdir.  
  
 [!code-xaml[TextTransformSample#TextTransformSample3](~/samples/snippets/csharp/VS_Snippets_Wpf/TextTransformSample/CS/Window1.xaml#texttransformsample3)]  
  
 Aşağıdaki örnek, çevrilmiş veya taşınmış, x ve y ekseni metni gösterir.  
  
 ![Metin TranslateTransform kullanan uzaklığı](./media/transformedtext04.jpg "TransformedText04")  
Çevrilmiş metin örneği  
  
 Aşağıdaki kod örneğinde bir <xref:System.Windows.Media.TranslateTransform> metin uzaklık. Bu örnekte, bir gölge etkisi birincil metin aşağıdaki metni biraz uzaklık bir kopyasını oluşturur.  
  
 [!code-xaml[TextTransformSample#TextTransformSample4](~/samples/snippets/csharp/VS_Snippets_Wpf/TextTransformSample/CS/Window1.xaml#texttransformsample4)]  
  
> [!NOTE]
>  <xref:System.Windows.Media.Effects.DropShadowBitmapEffect> Gölge efektleri sağlayan zengin bir özellikler kümesi sağlar. Daha fazla bilgi için [gölgeli metin oluşturma](how-to-create-text-with-a-shadow.md).  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Metne Animasyon Uygulama](how-to-apply-animations-to-text.md)
