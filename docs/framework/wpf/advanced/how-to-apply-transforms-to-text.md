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
ms.openlocfilehash: 531537013ab3bbfba278ca63e14155341eefc826
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-apply-transforms-to-text"></a>Nasıl yapılır: Metne Dönüşüm Uygulama
Dönüşümler uygulamanızdaki metnin görüntüsünü değiştirebilir. Aşağıdaki örnekler farklı türdeki işleme dönüşümlerini metin görünümünü kullanın. bir <xref:System.Windows.Controls.TextBlock> denetim.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte, iki boyutlu x-y düzlem olarak belirtilen bir nokta döndürülen metin gösterir.  
  
 ![RotateTransform kullanılarak döndürülen metin](../../../../docs/framework/wpf/advanced/media/transformedtext01.jpg "TransformedText01")  
90 derece döndürülmüş metin örneği  
  
 Aşağıdaki kod örneğinde bir <xref:System.Windows.Media.RotateTransform> metni döndürmek için. Bir <xref:System.Windows.Media.RotateTransform.Angle%2A> değeri olarak 90 90 derece saat yönünde öğesi döndürür.  
  
 [!code-xaml[TextTransformSample#TextTransformSample1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextTransformSample/CS/Window1.xaml#texttransformsample1)]  
  
 Aşağıdaki örnek, x ekseni boyunca % 150 ölçeklendirilmiş metin satırının ikinci ve üçüncü y ekseni boyunca % 150 ölçeklendirilmiş metin satırının gösterir.  
  
 ![ScaleTransform kullanılarak ölçeklendirilen metin](../../../../docs/framework/wpf/advanced/media/transformedtext02.jpg "TransformedText02")  
Ölçeklendirilmiş metin örneği  
  
 Aşağıdaki kod örneğinde bir <xref:System.Windows.Media.ScaleTransform> özgün boyutuna ölçek metinden için.  
  
 [!code-xaml[TextTransformSample#TextTransformSample2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextTransformSample/CS/Window1.xaml#texttransformsample2)]  
  
> [!NOTE]
>  Metin ölçeklendirme metnin yazı tipi boyutunu artırma ile aynı değil. Yazı tipi boyutlarını farklı boyutlarda en iyi çözüm sunmak için diğer bağımsız olarak hesaplanır. Ölçeklendirilmiş metin, diğer yandan, özgün boyutlu metin oranlarını korur.  
  
 Aşağıdaki örnek eksenindeki eğri metni gösterir.  
  
 ![SkewTransform kullanılarak eğri metin](../../../../docs/framework/wpf/advanced/media/transformedtext03.jpg "TransformedText03")  
Çarpık metin örneği  
  
 Aşağıdaki kod örneğinde bir <xref:System.Windows.Media.SkewTransform> metin eğme için. Bir eğme olarak da bilinen eğme, koordinat Tekdüzen olmayan bir biçimde uzatan bir dönüşümü gerçekleşir. Bu örnekte, iki metin çarpık-30 ° ve 30 ° x koordinatını boyunca dizelerdir.  
  
 [!code-xaml[TextTransformSample#TextTransformSample3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextTransformSample/CS/Window1.xaml#texttransformsample3)]  
  
 Aşağıdaki örnek çevrilmiş veya taşınmış, x ve y ekseni metin gösterir.  
  
 ![TranslateTransform kullanan metin uzaklığı](../../../../docs/framework/wpf/advanced/media/transformedtext04.jpg "TransformedText04")  
Çevrilmiş metin örneği  
  
 Aşağıdaki kod örneğinde bir <xref:System.Windows.Media.TranslateTransform> metni dengelemek için. Bu örnekte, bir gölge etkisi birincil metin altındaki metin biraz uzaklık bir kopyasını oluşturur.  
  
 [!code-xaml[TextTransformSample#TextTransformSample4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextTransformSample/CS/Window1.xaml#texttransformsample4)]  
  
> [!NOTE]
>  <xref:System.Windows.Media.Effects.DropShadowBitmapEffect> Gölge efektleri sağlayan zengin bir özellikler kümesi sağlar. Daha fazla bilgi için bkz: [gölgeli metin oluşturma](../../../../docs/framework/wpf/advanced/how-to-create-text-with-a-shadow.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Metne Animasyon Uygulama](../../../../docs/framework/wpf/advanced/how-to-apply-animations-to-text.md)
