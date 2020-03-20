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
ms.openlocfilehash: 867f39e3df8493014d8601530e91310c3bbbeeb5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79141620"
---
# <a name="how-to-apply-transforms-to-text"></a>Nasıl yapılır: Metne Dönüşüm Uygulama
Dönüşümler, uygulamanızdaki metnin ekranını değiştirebilir. Aşağıdaki örnekler, bir <xref:System.Windows.Controls.TextBlock> denetimdeki metnin görüntülenmesini etkilemek için farklı türde işleme dönüşümleri kullanır.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte, iki boyutlu x-y düzleminde belirtilen bir nokta hakkında döndürülen metin gösterilmektedir.  
  
 ![DöndürmeTransform kullanılarak döndürülen metin](./media/how-to-apply-transforms-to-text/text-rotated-ninety-degrees.jpg)  
  
 Aşağıdaki kod örneği <xref:System.Windows.Media.RotateTransform> metni döndürmek için a kullanır. 90 <xref:System.Windows.Media.RotateTransform.Angle%2A> değeri, öğeyi saat yönünde 90 derece döndürür.  
  
 [!code-xaml[TextTransformSample#TextTransformSample1](~/samples/snippets/csharp/VS_Snippets_Wpf/TextTransformSample/CS/Window1.xaml#texttransformsample1)]  
  
 Aşağıdaki örnek, x ekseni boyunca %150 ölçeklendirilen ikinci metin satırını ve y ekseni boyunca %150 ölçeklendirilen üçüncü metin satırını gösterir.  
  
 ![Bir ScaleTransform kullanılarak ölçeklendirilen metin](./media/how-to-apply-transforms-to-text/scaled-text-scaletransform.jpg)
  
 Aşağıdaki kod örneği, <xref:System.Windows.Media.ScaleTransform> metni özgün boyutundan ölçeklendirmek için bir kod kullanır.  
  
 [!code-xaml[TextTransformSample#TextTransformSample2](~/samples/snippets/csharp/VS_Snippets_Wpf/TextTransformSample/CS/Window1.xaml#texttransformsample2)]  
  
> [!NOTE]
> Metni ölçekleme, metnin yazı tipi boyutunu artırmakla aynı şey değildir. Yazı tipi boyutları, farklı boyutlarda en iyi çözünürlüğü sağlamak için birbirinden bağımsız olarak hesaplanır. Diğer taraftan, ölçeklenmiş metin orijinal boyutlu metnin oranlarını korur.  
  
 Aşağıdaki örnek, x ekseni boyunca eğriltilen metni gösterir.  
  
 ![SkewTransform kullanılarak eğriltilen metin](./media/how-to-apply-transforms-to-text/skewed-transformed-text.jpg)

 Aşağıdaki kod örneği, <xref:System.Windows.Media.SkewTransform> metni eğriltmek için a kullanır. Bir eğrilik, aynı zamanda bir yama olarak bilinen, olmayan bir üniforma şekilde koordinat alanı uzanan bir dönüşümdür. Bu örnekte, iki metin dizeleri x-koordinatı boyunca -30° ve 30° şeklinde eğriltilir.  
  
 [!code-xaml[TextTransformSample#TextTransformSample3](~/samples/snippets/csharp/VS_Snippets_Wpf/TextTransformSample/CS/Window1.xaml#texttransformsample3)]  
  
 Aşağıdaki örnekte, x- ve y ekseni boyunca çevrilen veya taşınan metin gösterilmektedir.  
  
 ![TranslateTransform kullanarak metin mahsup](./media/how-to-apply-transforms-to-text/transformed-text-x-y-axis.jpg)
  
 Aşağıdaki kod örneği, <xref:System.Windows.Media.TranslateTransform> metni dengelemek için a kullanır. Bu örnekte, birincil metnin altındaki metnin biraz ofset kopyası gölge efekti oluşturur.  
  
 [!code-xaml[TextTransformSample#TextTransformSample4](~/samples/snippets/csharp/VS_Snippets_Wpf/TextTransformSample/CS/Window1.xaml#texttransformsample4)]  
  
> [!NOTE]
> Gölge <xref:System.Windows.Media.Effects.DropShadowBitmapEffect> efektleri sağlamak için zengin bir özellik kümesi sağlar. Daha fazla bilgi için [bkz.](how-to-create-text-with-a-shadow.md)  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Metne Animasyon Uygulama](how-to-apply-animations-to-text.md)
