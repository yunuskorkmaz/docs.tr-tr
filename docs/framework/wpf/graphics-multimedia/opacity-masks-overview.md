---
title: Opaklık Maskelerine Genel Bakış
ms.date: 03/30/2017
helpviewer_keywords:
- brushes [WPF], opacity masks
- masks [WPF], opacity
- opacity [WPF], masks
ms.assetid: 22367fab-5f59-4583-abfd-db2bf86eaef7
ms.openlocfilehash: 0c859659c35e2a5806b8585214c87c18fbcb62d4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187682"
---
# <a name="opacity-masks-overview"></a>Opaklık Maskelerine Genel Bakış
Opaklık maskeleri, bir öğenin veya görsel in bölümlerini saydam veya kısmen saydam yapmanızı sağlar. Opaklık maskesi oluşturmak için, <xref:System.Windows.Media.Brush> bir <xref:System.Windows.UIElement.OpacityMask%2A> öğenin özelliğine <xref:System.Windows.Media.Visual>bir öğe veya .  Fırça öğeye veya görsele eşlenir ve her fırça pikselinin opaklık değeri, öğenin veya görselin karşılık gelen her pikselin inden oluşan opaklığını belirlemek için kullanılır.  
  
<a name="prereqs"></a>
## <a name="prerequisites"></a>Önkoşullar  
 Bu genel bakış, nesnelere <xref:System.Windows.Media.Brush> aşina olduğunuzu varsayar. Fırçaları kullanmaya giriş için Bkz. [Düz Renkler ve Degradelerle Boyama](painting-with-solid-colors-and-gradients-overview.md)Genel Bakış. Hakkında <xref:System.Windows.Media.ImageBrush> bilgi <xref:System.Windows.Media.DrawingBrush>için ve , [Resimler, Çizimler ve Görseller ile Boyama](painting-with-images-drawings-and-visuals.md)bakın.  
  
<a name="opacitymasks"></a>
## <a name="creating-visual-effects-with-opacity-masks"></a>Opaklık Maskeleri ile Görsel Efekt Oluşturma  
 Opaklık maskesi, içeriğini öğeyle veya görselle eşleyerek çalışır. Fırçanın piksellerinin her birinin alfa kanalı, öğenin veya görselin karşılık gelen piksellerinin ortaya çıkan donukluğunu belirlemek için kullanılır; fırçanın gerçek rengi yoksayılır. Fırçanın belirli bir bölümü saydamsa, öğenin veya görselin karşılık gelen bölümü saydam hale gelir. Fırçanın belirli bir bölümü opaksa, öğenin veya görselin karşılık gelen bölümünün opaklığı değişmez. Opaklık maskesi tarafından belirtilen opaklık, öğeveya görselde bulunan herhangi bir opaklık ayarı ile birleştirilir. Örneğin, bir eleman yüzde 25 opaksa ve tam opaktan tamamen saydama geçiş yapan bir opaklık maskesi uygulanıyorsa, sonuç yüzde 25 opaklıktan tamamen saydama geçiş yapan bir öğedir.  
  
> [!NOTE]
> Bu genel bakıştaki örnekler görüntü öğeleriüzerinde opaklık maskelerinin kullanımını gösterse de, paneller ve denetimler de dahil olmak üzere herhangi bir elemana veya <xref:System.Windows.Media.Visual>opaklık maskesi uygulanabilir.  
  
 Opaklık maskeleri, görünümden solan görüntüler veya düğmeler oluşturmak, öğelere doku lar eklemek veya cam benzeri yüzeyler üretmek için degradeleri birleştirmek gibi ilginç görsel efektler oluşturmak için kullanılır. Aşağıdaki resimde opaklık maskesi kullanımı gösteriş göstermektedir. Maskenin saydam kısımlarını göstermek için damalı arka plan kullanılır.  
  
 ![LinearGradientBrush opaklık maskesi olan nesne](./media/wcpsdk-graphicsmm-opacitymask-imageexample.png "wcpsdk_graphicsmm_opacitymask_imageexample")  
Opaklık maskeleme örneği  
  
<a name="creatingopacitymasks"></a>
## <a name="creating-an-opacity-mask"></a>Opaklık Maskesi Oluşturma  
 Opaklık maskesi oluşturmak için, <xref:System.Windows.Media.Brush> bir öğe veya <xref:System.Windows.UIElement.OpacityMask%2A> görsel özelliğine bir oluşturup uygularsınız. Opaklık maskesi <xref:System.Windows.Media.Brush> olarak her türlü kullanabilirsiniz.  
  
- <xref:System.Windows.Media.LinearGradientBrush>, <xref:System.Windows.Media.RadialGradientBrush>: Bir öğeyi veya görsel görünümünden solmaya yapmak için kullanılır.  
  
     Aşağıdaki resimde opaklık maskesi olarak <xref:System.Windows.Media.LinearGradientBrush> kullanılan bir görüntü gösterilmektedir.  
  
     ![LinearGradientBrush opaklık maskesi olan bir nesne](./media/wcpsdk-graphicsmm-brushes-lineagradientopacitymasksingle.jpg "wcpsdk_graphicsmm_brushes_lineagradientopacitymasksingle")  
LinearGradientBrush Opaklık Maskeleme Örneği  
  
- <xref:System.Windows.Media.ImageBrush>: Doku ve yumuşak veya yırtık kenar efektleri oluşturmak için kullanılır.  
  
     Aşağıdaki resimde opaklık maskesi olarak <xref:System.Windows.Media.ImageBrush> kullanılan bir görüntü gösterilmektedir.  
  
     ![ImageBrush opaklık maskesi olan nesne](./media/wcpsdk-graphicsmm-brushes-imageasopacitymasksingle.jpg "wcpsdk_graphicsmm_brushes_imageasopacitymasksingle")  
LinearGradientFırça opaklık maskeleme örneği  
  
- <xref:System.Windows.Media.DrawingBrush>: Şekil, görüntü ve degrade desenlerinden karmaşık opaklık maskeleri oluşturmak için kullanılır.  
  
     Aşağıdaki resimde opaklık maskesi olarak <xref:System.Windows.Media.DrawingBrush> kullanılan bir görüntü gösterilmektedir.  
  
     ![DrawingBrush opaklık maskesi olan nesne](./media/wcpsdk-drawingbrushasopacitymask-single.jpg "wcpsdk_drawingbrushasopacitymask_single")  
ÇizimFırça opaklık maskeleme örneği  
  
 Degrade fırçalar<xref:System.Windows.Media.LinearGradientBrush> ( <xref:System.Windows.Media.RadialGradientBrush>ve ) özellikle iyi bir opaklık maskesi olarak kullanmak için uygundur. Bir <xref:System.Windows.Media.SolidColorBrush> alanı tek tip bir renkle doldurduğu için, kötü opaklık maskeleri yaparlar; a <xref:System.Windows.Media.SolidColorBrush> kullanmak, öğenin veya görselin <xref:System.Windows.UIElement.OpacityMask%2A> özelliğini ayarlamaya eşdeğerdir.  
  
<a name="creatingopacitymaskswithgradients"></a>
## <a name="using-a-gradient-as-an-opacity-mask"></a>Opaklık Maskesi Olarak Degrade Kullanma  
 Bir degrade dolgu oluşturmak için, iki veya daha fazla degrade durakları belirtin. Her degrade durağı bir renk ve bir konum içerir [(bkz.](painting-with-solid-colors-and-gradients-overview.md) Opaklık maskesi olarak bir degrade kullanırken işlem aynıdır, ancak renkleri karıştırmak yerine, opaklık maskesi degradesi alfa kanal değerlerini karıştırır. Yani degradenin içeriğinin gerçek rengi önemli değildir; sadece alfa kanal, ya da opaklık, her renk konularda. Bir örnek verilmiştir.  
  
 [!code-xaml[OpacityMasksSnippet#LinearGradientOpacityMaskonImage](~/samples/snippets/csharp/VS_Snippets_Wpf/OpacityMasksSnippet/CS/GradientBrushExample.xaml#lineargradientopacitymaskonimage)]  
  
<a name="specifyinggradientcolors"></a>
## <a name="specifying-gradient-stops-for-an-opacity-mask"></a>Opaklık Maskesi için Degrade Durakları Belirtme  
 Önceki örnekte, sistem tanımlı <xref:System.Windows.Media.Colors.Black%2A> renk degradebaşlangıç rengi olarak kullanılır. <xref:System.Windows.Media.Colors> Sınıftaki tüm renkler, tamamen <xref:System.Windows.Media.Colors.Transparent%2A>opak olduğundan, sadece bir degrade opaklık maskesi için bir başlangıç rengi tanımlamak için kullanılabilir.  
  
 Opaklık maskesi tanımlarken alfa değerleri üzerinde ek denetim için, biçimlendirmede veya <xref:System.Windows.Media.Color.FromScRgb%2A?displayProperty=nameWithType> yöntemi kullanarak ARGB hexadecimal gösterimini kullanarak renklerin alfa kanalını belirtebilirsiniz.  
  
<a name="argbsyntax"></a>
### <a name="specifying-color-opacity-in-xaml"></a>"XAML"da Renk Opaklığı Belirtme  
 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], tek tek renklerin opaklık belirtmek için ARGB hexadecimal gösterim kullanın. ARGB hexadecimal gösterimaşağıdaki sözdizimini kullanır:  
  
 `#`**aa** *rrggbb*  
  
 Önceki satırdaki *aa,* rengin opaklığını belirtmek için kullanılan iki basamaklı heksadedesimal değeri temsil eder. *Rr*, *gg*, ve *bb* her iki basamaklı hexadecimal değeri kırmızı, yeşil ve mavi renk miktarını belirtmek için kullanılır temsil. Her hexadecimal basamak 0-9 veya A-F bir değere sahip olabilir. 0 en küçük değerdir ve F en büyüktür. 00'lık bir alfa değeri tamamen saydam bir renk belirtirken, FF'nin alfa değeri tamamen opak bir renk oluşturur.  Aşağıdaki örnekte, hexadecimal ARGB gösterimi iki renk belirtmek için kullanılır. İlki tamamen opak, ikincisi ise tamamen saydamdır.  
  
 [!code-xaml[OpacityMasksSnippet#AARRGGBBValueonOpacityMask](~/samples/snippets/csharp/VS_Snippets_Wpf/OpacityMasksSnippet/CS/GradientBrushExample.xaml#aarrggbbvalueonopacitymask)]  
  
<a name="usingimageasopacitymask"></a>
## <a name="using-an-image-as-an-opacity-mask"></a>Görüntüyü Opaklık Maskesi Olarak Kullanma  
 Görüntüler opaklık maskesi olarak da kullanılabilir. Aşağıdaki resimde bir örnek gösterilir. Maskenin saydam kısımlarını göstermek için damalı arka plan kullanılır.  
  
 ![ImageBrush opaklık maskesi olan bir nesne](./media/wcpsdk-graphicsmm-imageasopacitymask.png "wcpsdk_graphicsmm_imageasopacitymask")  
Opaklık maskeleme örneği  
  
 Bir görüntüyü opaklık maskesi olarak kullanmak <xref:System.Windows.Media.ImageBrush> için görüntüyü içeren bir görüntü kullanın. Donukluk maskesi olarak kullanılacak bir görüntü oluştururken, görüntüyü Taşınabilir Ağ Grafikleri (PNG) gibi birden çok saydamlık düzeylerini destekleyen bir biçimde kaydedin. Aşağıdaki örnekte, önceki çizimi oluşturmak için kullanılan kod gösterilmektedir.  
  
 [!code-xaml[OpacityMasksSnippet#UIElementOpacityMask](~/samples/snippets/csharp/VS_Snippets_Wpf/OpacityMasksSnippet/CS/ImageBrushExample.xaml#uielementopacitymask)]  
  
<a name="tilingimageopacitymask"></a>
### <a name="using-a-tiled-image-as-an-opacity-mask"></a>Opaklık Maskesi Olarak Döşenmiş Görüntü Kullanma  
 Aşağıdaki örnekte, aynı görüntü başka <xref:System.Windows.Media.ImageBrush>bir , ancak fırçanın döşeme özellikleri görüntü 50 piksel kare fayans üretmek için kullanılır.  
  
 [!code-xaml[OpacityMasksSnippet#TiledImageasOpacityMask](~/samples/snippets/csharp/VS_Snippets_Wpf/OpacityMasksSnippet/CS/ImageBrushExample.xaml#tiledimageasopacitymask)]  
  
<a name="drawingbrushasopacitymask"></a>
## <a name="creating-an-opacity-mask-from-a-drawing"></a>Çizimden Opaklık Maskesi Oluşturma  
 Çizimler opaklık maskesi kullanılabilir. Çizimin içinde yer alan şekiller degradeler, düz renkler, görüntüler ve hatta diğer çizimlerle doldurulabilir. Aşağıdaki resimde, opaklık maskesi olarak kullanılan bir çizim örneği gösterilmektedir. Maskenin saydam kısımlarını göstermek için damalı arka plan kullanılır.  
  
 ![DrawingBrush opaklık maskesi olan bir nesne](./media/wcpsdk-drawingbrushasopacitymask.png "wcpsdk_drawingbrushasopacitymask")  
ÇizimFırça opaklık maskeleme örneği  
  
 Çizimi opaklık maskesi olarak kullanmak <xref:System.Windows.Media.DrawingBrush> için, çizimi içeren a'yı kullanın. Aşağıdaki örnekte, önceki çizimi oluşturmak için kullanılan kod gösterilmektedir:  
  
 [!code-xaml[OpacityMasksSnippet#OpacityMaskfromDrawing](~/samples/snippets/csharp/VS_Snippets_Wpf/OpacityMasksSnippet/CS/DrawingBrushExample.xaml#opacitymaskfromdrawing)]  
  
<a name="tileddrawingbrush"></a>
### <a name="using-a-tiled-drawing-as-an-opacity-mask"></a>Opaklık Maskesi Olarak Kiremit Çizimi Kullanma  
 Gibi <xref:System.Windows.Media.ImageBrush>, <xref:System.Windows.Media.DrawingBrush> onun çizim fayans yapılabilir. Aşağıdaki örnekte, bir çizim fırçası karo opaklık maskesi oluşturmak için kullanılır.  
  
 [!code-xaml[OpacityMasksSnippet#TiledDrawingasOpacityMask](~/samples/snippets/csharp/VS_Snippets_Wpf/OpacityMasksSnippet/CS/DrawingBrushExample.xaml#tileddrawingasopacitymask)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Görüntüler, Çizimler ve Görsellerle Boyama](painting-with-images-drawings-and-visuals.md)
- [Düz Renkler ve Gradyanlar ile Boyamaya Genel Bakış](painting-with-solid-colors-and-gradients-overview.md)
