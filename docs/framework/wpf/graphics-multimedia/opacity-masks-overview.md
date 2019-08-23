---
title: Opaklık Maskelerine Genel Bakış
ms.date: 03/30/2017
helpviewer_keywords:
- brushes [WPF], opacity masks
- masks [WPF], opacity
- opacity [WPF], masks
ms.assetid: 22367fab-5f59-4583-abfd-db2bf86eaef7
ms.openlocfilehash: d0fea1aac4efb17811404ce45769615bb2e7234f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69929656"
---
# <a name="opacity-masks-overview"></a>Opaklık Maskelerine Genel Bakış
Opaklık maskeleri, bir öğenin veya görselin bölümlerini saydam veya kısmen saydam hale getirme imkanı sağlar. Bir opaklık maskesi oluşturmak için, bir öğesi veya <xref:System.Windows.Media.Brush> <xref:System.Windows.UIElement.OpacityMask%2A> <xref:System.Windows.Media.Visual>özelliğine bir öğesi uygularsınız.  Fırça, öğe veya görsele eşlenir ve her fırça pikselin opaklık değeri, öğe veya görselin her bir pikselin elde edilen opaklığını belirlemede kullanılır.  
  
<a name="prereqs"></a>   
## <a name="prerequisites"></a>Önkoşullar  
 Bu genel bakışta <xref:System.Windows.Media.Brush> nesneler hakkında bilgi sahibi olduğunuz varsayılır. Fırçaları kullanmaya giriş için bkz. [düz renklerle boyama ve degradelere genel bakış](painting-with-solid-colors-and-gradients-overview.md). <xref:System.Windows.Media.ImageBrush> Ve<xref:System.Windows.Media.DrawingBrush>hakkında daha fazla bilgi için bkz. [görüntü, çizim ve görsellerle boyama](painting-with-images-drawings-and-visuals.md).  
  
<a name="opacitymasks"></a>   
## <a name="creating-visual-effects-with-opacity-masks"></a>Opaklık maskeleri ile görsel etkiler oluşturma  
 Opaklık maskesi, içeriğini öğe veya görsele eşleyerek işe yarar. Fırçanın piksellerinin her birinin alfa kanalı daha sonra öğenin veya görselin karşılık gelen piksellerin elde edilen opaklığını belirlemede kullanılır; fırçanın gerçek rengi yok sayılır. Fırçanın belirli bir bölümü saydam ise, öğenin veya görselin karşılık gelen bölümü saydam hale gelir. Fırçanın belirli bir kısmı donuk ise, öğenin veya görselin karşılık gelen bölümünün geçirgenliği değiştirilmez. Opaklık maskesi tarafından belirtilen opaklık, öğesinde veya görselde bulunan herhangi bir opaklık ayarı ile birleştirilir. Örneğin, bir öğe yüzde 25 donuk ise ve tam opak 'dan tamamen saydam 'e geçiş yapan bir opaklık maskesi uygulanırsa, sonuç, yüzde 25 opaklıktan tamamen saydamlığa geçiş yapan bir öğedir.  
  
> [!NOTE]
> Bu genel bakışta yer alan örneklere, görüntü öğelerinde opaklık maskelerinin kullanımı gösterimi olsa da, bir opaklık maskesi herhangi bir öğeye veya <xref:System.Windows.Media.Visual>paneller ve denetimler dahil olmak üzere uygulanabilir.  
  
 Opaklık maskeleri, görünümden geçiş yapan görüntü veya düğme oluşturmak, öğelere dokular eklemek veya cam benzeri yüzeyler oluşturmak için degradeleri birleştirmek gibi ilginç görsel etkiler oluşturmak için kullanılır. Aşağıdaki çizimde bir Opaklık maskesinin kullanımı gösterilmektedir. Damalı arka planı, maskenin saydam bölümlerini göstermek için kullanılır.  
  
 ![Bir Doğrgradientbrush opaklık maskesine sahip nesne](./media/wcpsdk-graphicsmm-opacitymask-imageexample.png "wcpsdk_graphicsmm_opacitymask_imageexample")  
Opaklık maskeleme örneği  
  
<a name="creatingopacitymasks"></a>   
## <a name="creating-an-opacity-mask"></a>Opaklık maskesi oluşturma  
 Bir opaklık maskesi oluşturmak için, oluşturun <xref:System.Windows.Media.Brush> ve bunu <xref:System.Windows.UIElement.OpacityMask%2A> bir öğe veya görselin özelliğine uygularsınız. Herhangi bir tür <xref:System.Windows.Media.Brush> opaklık maskesi olarak kullanabilirsiniz.  
  
- <xref:System.Windows.Media.LinearGradientBrush>, <xref:System.Windows.Media.RadialGradientBrush>: Bir öğeyi veya görseli görünümden belirme yapmak için kullanılır.  
  
     Aşağıdaki görüntüde opaklık maskesi olarak <xref:System.Windows.Media.LinearGradientBrush> kullanılan bir gösterilmektedir.  
  
     ![Bir Doğrgradientbrush opaklık maskesine sahip bir nesne](./media/wcpsdk-graphicsmm-brushes-lineagradientopacitymasksingle.jpg "wcpsdk_graphicsmm_brushes_lineagradientopacitymasksingle")  
Doğrgradientbrush opaklık maskeleme örneği  
  
- <xref:System.Windows.Media.ImageBrush>: Doku ve geçici ya da yırtılmış kenar efektleri oluşturmak için kullanılır.  
  
     Aşağıdaki görüntüde bir opaklık maskesi <xref:System.Windows.Media.ImageBrush> olarak kullanılan gösterilmektedir.  
  
     ![ImageBrush opaklık maskesine sahip nesne](./media/wcpsdk-graphicsmm-brushes-imageasopacitymasksingle.jpg "wcpsdk_graphicsmm_brushes_imageasopacitymasksingle")  
Doğrgradientbrush opaklık maskeleme örneği  
  
- <xref:System.Windows.Media.DrawingBrush>: Şekil, resim ve degradeler desenlerinden karmaşık opaklık maskeleri oluşturmak için kullanılır.  
  
     Aşağıdaki görüntüde opaklık maskesi olarak <xref:System.Windows.Media.DrawingBrush> kullanılan bir gösterilmektedir.  
  
     ![DrawingBrush opaklık maskesine sahip nesne](./media/wcpsdk-drawingbrushasopacitymask-single.jpg "wcpsdk_drawingbrushasopacitymask_single")  
DrawingBrush opaklık maskeleme örneği  
  
 Gradyan fırçaları (<xref:System.Windows.Media.LinearGradientBrush> ve <xref:System.Windows.Media.RadialGradientBrush>) özellikle bir opaklık maskesi olarak kullanım için uygundur. Bir <xref:System.Windows.Media.SolidColorBrush> alan, Tekdüzen rengi olan bir alanı doldurduğundan, kötü opaklık maskeleri yapabilirler; bir <xref:System.Windows.Media.SolidColorBrush> öğesi, öğenin veya görselin <xref:System.Windows.UIElement.OpacityMask%2A> özelliğini ayarlamaya eşdeğerdir.  
  
<a name="creatingopacitymaskswithgradients"></a>   
## <a name="using-a-gradient-as-an-opacity-mask"></a>Opaklık maskesi olarak gradyan kullanma  
 Gradyan dolgusu oluşturmak için iki veya daha fazla gradyan duru belirtirsiniz. Her gradyan durağı bir renk ve konum tanımlar (degradeler oluşturma ve kullanma hakkında daha fazla bilgi için bkz. [düz renklerle boyama ve degradelere genel bakış](painting-with-solid-colors-and-gradients-overview.md) ). Bir gradyan opaklık maskesi olarak kullanılırken aynı olur, ancak karıştırma renkleri, opaklık maskesi gradyanın alfa kanalı değerlerini karıştırın. Bu nedenle, degradenin içeriğinin gerçek rengi önemi yoktur; yalnızca alfa kanalı veya opaklık, her rengin önemli. Bir örnek verilmiştir.  
  
 [!code-xaml[OpacityMasksSnippet#LinearGradientOpacityMaskonImage](~/samples/snippets/csharp/VS_Snippets_Wpf/OpacityMasksSnippet/CS/GradientBrushExample.xaml#lineargradientopacitymaskonimage)]  
  
<a name="specifyinggradientcolors"></a>   
## <a name="specifying-gradient-stops-for-an-opacity-mask"></a>Opaklık maskesi için gradyan duraklarının belirtilmesi  
 Önceki örnekte, sistem tarafından tanımlanan renk <xref:System.Windows.Media.Colors.Black%2A> , degradenin başlangıç rengi olarak kullanılır. <xref:System.Windows.Media.Colors> Sınıfındaki<xref:System.Windows.Media.Colors.Transparent%2A>tüm renkler tamamen donuk olduğundan, bir gradyan opaklık maskesi için bir başlangıç rengi tanımlamak üzere kullanılabilir.  
  
 Opaklık maskesini tanımlarken alfa değerleri üzerinde ek denetim için, İşaretlemede argb onaltılı gösterimi kullanarak renklerin alfa kanalını belirtebilir veya <xref:System.Windows.Media.Color.FromScRgb%2A?displayProperty=nameWithType> yöntemini kullanabilirsiniz.  
  
<a name="argbsyntax"></a>   
### <a name="specifying-color-opacity-in-xaml"></a>"XAML" içinde renk geçirgenliği belirtme  
 İçinde [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], tek tek renklerin saydamlığını belirtmek için ARGB onaltılık gösterimini kullanırsınız. ARGB onaltılık gösterimi aşağıdaki sözdizimini kullanır:  
  
 `#`**AA** *RRGGBB*  
  
 Önceki satırdaki *AA* , rengin opaklığını belirtmek için kullanılan iki basamaklı bir onaltılık değeri temsil eder. *RR*, *gg*ve *BB* her biri, rengin kırmızı, yeşil ve mavi miktarını belirtmek için kullanılan iki basamaklı bir onaltılık değeri temsil eder. Her onaltılık basamak 0-9 veya A-F arasında bir değere sahip olabilir. 0 en küçük değerdir ve F en büyük değerdir. 00 ' ın alfa değeri tamamen saydam bir rengi belirtir, bu da bir FF Alpha değeri tamamen opak bir renk oluşturur.  Aşağıdaki örnekte, iki renk belirtmek için onaltılı ARGB gösterimi kullanılır. İlki tamamen opaktır, ikincisi tamamen saydamdır.  
  
 [!code-xaml[OpacityMasksSnippet#AARRGGBBValueonOpacityMask](~/samples/snippets/csharp/VS_Snippets_Wpf/OpacityMasksSnippet/CS/GradientBrushExample.xaml#aarrggbbvalueonopacitymask)]  
  
<a name="usingimageasopacitymask"></a>   
## <a name="using-an-image-as-an-opacity-mask"></a>Opaklık maskesi olarak görüntü kullanma  
 Görüntüler, geçirgenlik maskesi olarak da kullanılabilir. Aşağıdaki resimde bir örnek gösterilir. Damalı arka planı, maskenin saydam bölümlerini göstermek için kullanılır.  
  
 ![ImageBrush opaklık maskesine sahip bir nesne](./media/wcpsdk-graphicsmm-imageasopacitymask.png "wcpsdk_graphicsmm_imageasopacitymask")  
Opaklık maskeleme örneği  
  
 Bir görüntüyü bir opaklık maskesi olarak kullanmak için, bir <xref:System.Windows.Media.ImageBrush> görüntüyü içeren öğesini kullanın. Opaklık maskesi olarak kullanılacak bir görüntü oluştururken, görüntüyü Taşınabilir Ağ Grafikleri (PNG) gibi birden çok saydamlık düzeyini destekleyen bir biçimde kaydedin. Aşağıdaki örnek, önceki çizimi oluşturmak için kullanılan kodu gösterir.  
  
 [!code-xaml[OpacityMasksSnippet#UIElementOpacityMask](~/samples/snippets/csharp/VS_Snippets_Wpf/OpacityMasksSnippet/CS/ImageBrushExample.xaml#uielementopacitymask)]  
  
<a name="tilingimageopacitymask"></a>   
### <a name="using-a-tiled-image-as-an-opacity-mask"></a>Döşeli bir görüntüyü opaklık maskesi olarak kullanma  
 Aşağıdaki örnekte, aynı görüntü diğeri <xref:System.Windows.Media.ImageBrush>ile birlikte kullanılır, ancak fırçanın döşeme özellikleri görüntünün 50 piksel kare içinde kutucuk oluşturmak için kullanılır.  
  
 [!code-xaml[OpacityMasksSnippet#TiledImageasOpacityMask](~/samples/snippets/csharp/VS_Snippets_Wpf/OpacityMasksSnippet/CS/ImageBrushExample.xaml#tiledimageasopacitymask)]  
  
<a name="drawingbrushasopacitymask"></a>   
## <a name="creating-an-opacity-mask-from-a-drawing"></a>Çizimden opaklık maskesi oluşturma  
 Çizimler bir opaklık maskesi için kullanılabilir. Çizim içinde bulunan şekillerin kendisi gradyanlar, düz renkler, görüntüler ve hatta diğer çizimlerle doldurulabilir. Aşağıdaki görüntüde, geçirgenlik maskesi olarak kullanılan bir çizim örneği gösterilmektedir. Damalı arka planı, maskenin saydam bölümlerini göstermek için kullanılır.  
  
 ![DrawingBrush opaklık maskesine sahip bir nesne](./media/wcpsdk-drawingbrushasopacitymask.png "wcpsdk_drawingbrushasopacitymask")  
DrawingBrush opaklık maskeleme örneği  
  
 Bir çizimi opaklık maskesi olarak kullanmak için, çizimi içeren bir <xref:System.Windows.Media.DrawingBrush> kullanın. Aşağıdaki örnek, önceki çizimi oluşturmak için kullanılan kodu gösterir:  
  
 [!code-xaml[OpacityMasksSnippet#OpacityMaskfromDrawing](~/samples/snippets/csharp/VS_Snippets_Wpf/OpacityMasksSnippet/CS/DrawingBrushExample.xaml#opacitymaskfromdrawing)]  
  
<a name="tileddrawingbrush"></a>   
### <a name="using-a-tiled-drawing-as-an-opacity-mask"></a>Döşenmiş çizimi opaklık maskesi olarak kullanma  
 Gibi, onun gibi, çizimini döşemek için deyapılabilir.<xref:System.Windows.Media.DrawingBrush> <xref:System.Windows.Media.ImageBrush> Aşağıdaki örnekte, bir çizim Fırçası döşeli bir opaklık maskesi oluşturmak için kullanılır.  
  
 [!code-xaml[OpacityMasksSnippet#TiledDrawingasOpacityMask](~/samples/snippets/csharp/VS_Snippets_Wpf/OpacityMasksSnippet/CS/DrawingBrushExample.xaml#tileddrawingasopacitymask)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Görüntüler, Çizimler ve Görsellerle Boyama](painting-with-images-drawings-and-visuals.md)
- [Düz Renkler ve Gradyanlar ile Boyamaya Genel Bakış](painting-with-solid-colors-and-gradients-overview.md)
