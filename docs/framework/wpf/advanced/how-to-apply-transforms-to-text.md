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
ms.openlocfilehash: b749d21c1b5940d216e244393eeb3c133dc153b6
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69956478"
---
# <a name="how-to-apply-transforms-to-text"></a>Nasıl yapılır: Metne Dönüşüm Uygulama
Dönüşümler uygulamanızdaki metnin görüntülenmesini değiştirebilir. Aşağıdaki örnekler, bir <xref:System.Windows.Controls.TextBlock> denetimdeki metnin görüntülenmesini etkilemek için farklı türde işleme dönüştürmelerini kullanır.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte, iki boyutlu x-y düzleinde belirtilen bir nokta hakkında döndürülmüş metin gösterilmektedir.  
  
 ![RotateTransform kullanılarak döndürülen metin](./media/how-to-apply-transforms-to-text/text-rotated-ninety-degrees.jpg)  
  
 Aşağıdaki kod örneği, metni döndürmek <xref:System.Windows.Media.RotateTransform> için bir kullanır. 90 <xref:System.Windows.Media.RotateTransform.Angle%2A> değeri, öğe 90 derece saat yönünde döner.  
  
 [!code-xaml[TextTransformSample#TextTransformSample1](~/samples/snippets/csharp/VS_Snippets_Wpf/TextTransformSample/CS/Window1.xaml#texttransformsample1)]  
  
 Aşağıdaki örnek, x ekseni ve y ekseni üzerinde% 150 ile ölçeklenmiş üçüncü metin satırındaki 150 metnin ikinci satırını gösterir.  
  
 ![ScaleTransform kullanılarak Ölçeklendirilmiş metin](./media/how-to-apply-transforms-to-text/scaled-text-scaletransform.jpg) 
  
 Aşağıdaki kod örneği, bir metni <xref:System.Windows.Media.ScaleTransform> özgün boyutundan ölçeklendirmek için bir kullanır.  
  
 [!code-xaml[TextTransformSample#TextTransformSample2](~/samples/snippets/csharp/VS_Snippets_Wpf/TextTransformSample/CS/Window1.xaml#texttransformsample2)]  
  
> [!NOTE]
> Metin ölçekleme metin yazı tipi boyutunun artmasından farklı değildir. Yazı tipi boyutları, farklı boyutlarda en iyi çözünürlüğü sağlamak için birbirinden bağımsız olarak hesaplanır. Ölçeklenmiş metin, diğer yandan, orijinal boyutlu metnin oranlarını korur.  
  
 Aşağıdaki örnek, x ekseni üzerinde eğilmiş metni gösterir.  
  
 ![SkewTransform kullanarak eğilmiş metin](./media/how-to-apply-transforms-to-text/skewed-transformed-text.jpg)
   
 Aşağıdaki kod örneği, metni eğmek için bir <xref:System.Windows.Media.SkewTransform> kullanır. Yamultma olarak da bilinen eğme, koordinat alanını Tekdüzen olmayan bir şekilde uzatır bir dönüşümdür. Bu örnekte, iki metin dizesi x koordinatı üzerinde 30 ° ve 30 ° eğriltilir.  
  
 [!code-xaml[TextTransformSample#TextTransformSample3](~/samples/snippets/csharp/VS_Snippets_Wpf/TextTransformSample/CS/Window1.xaml#texttransformsample3)]  
  
 Aşağıdaki örnek, x ve y ekseni üzerinde çevrilmiş veya taşınan metni gösterir.  
  
 ![TranslateTransform kullanan metin boşluğu](./media/how-to-apply-transforms-to-text/transformed-text-x-y-axis.jpg)
  
 Aşağıdaki kod örneği, metin kaydırmak <xref:System.Windows.Media.TranslateTransform> için bir kullanır. Bu örnekte, birincil metnin altındaki metnin biraz bir konum kopyası bir gölge efekti oluşturur.  
  
 [!code-xaml[TextTransformSample#TextTransformSample4](~/samples/snippets/csharp/VS_Snippets_Wpf/TextTransformSample/CS/Window1.xaml#texttransformsample4)]  
  
> [!NOTE]
> , <xref:System.Windows.Media.Effects.DropShadowBitmapEffect> Gölge etkileri sağlamaya yönelik zengin bir özellikler kümesi sağlar. Daha fazla bilgi için bkz. [Gölge Ile metin oluşturma](how-to-create-text-with-a-shadow.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Metne Animasyon Uygulama](how-to-apply-animations-to-text.md)
