---
title: Opaklık Maskelerine Genel Bakış
ms.date: 03/30/2017
helpviewer_keywords:
- brushes [WPF], opacity masks
- masks [WPF], opacity
- opacity [WPF], masks
ms.assetid: 22367fab-5f59-4583-abfd-db2bf86eaef7
ms.openlocfilehash: 680d7441301b425c088d549f9e0e0d2b976cc69f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33566239"
---
# <a name="opacity-masks-overview"></a>Opaklık Maskelerine Genel Bakış
Geçirgenlik maskeleri bölümleri bir öğe veya görselin saydam veya kısmen saydam yapmanızı sağlar. Geçirgenlik maskesi oluşturmak için uygulamanız bir <xref:System.Windows.Media.Brush> için <xref:System.Windows.UIElement.OpacityMask%2A> özelliği, bir öğenin veya <xref:System.Windows.Media.Visual>.  Öğe veya görsel fırça eşlenen ve her fırça piksel geçirgenlik değeri karşılık gelen her piksel öğe veya görselin sonuç geçirgenliğini belirlemek için kullanılır.  
  
<a name="prereqs"></a>   
## <a name="prerequisites"></a>Önkoşullar  
 Bu genel bakışta aşina olduğunuzu varsayar <xref:System.Windows.Media.Brush> nesneleri. Fırçalar kullanmaya giriş bilgileri için bkz: [gradyan genel bakış ve düz renk ile Boyama](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md). Hakkında bilgi için <xref:System.Windows.Media.ImageBrush> ve <xref:System.Windows.Media.DrawingBrush>, bkz: [görüntüleri, çizimler ve görsellerle boyama](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md).  
  
<a name="opacitymasks"></a>   
## <a name="creating-visual-effects-with-opacity-masks"></a>Görsel efektler geçirgenlik maskeleri ile oluşturma  
 Geçirgenlik maskesi öğe veya görsel içeriğinin eşleyerek çalışır. Her bir fırça piksel alfa kanal sonra öğe veya görselin karşılık gelen sonuç geçirgenliğini belirlemek için kullanılır; Fırça gerçek rengi göz ardı edilir. Fırça belirli bir kısmı saydam ise, öğenin veya visual karşılık gelen bölümü saydam olur. Fırça belirli bir kısmı donuk ise, öğe veya görselin karşılık gelen bölümünün geçirgenliğini değiştirilmez. Geçirgenlik maskesi tarafından belirtilen geçirgenlik herhangi geçirgenlik ayarlarıyla öğesinde yok veya visual birleştirilir. Örneğin, bir öğe yüzde 25 donuk ve geçirgenlik maskesi tamamıyla opak görünümden tamamen saydam olarak geçiş uygulanır, sonuç yüzde 25 saydamlığı için tamamen saydam geçişleri bir öğe olur.  
  
> [!NOTE]
>  Bu genel bakıştaki örnekler imaj öğelerinde geçirgenlik maskeleri kullanımını gösterir ancak geçirgenlik maskesi herhangi bir öğeye uygulanan veya <xref:System.Windows.Media.Visual>paneller ve denetimleri dahil olmak üzere.  
  
 Geçirgenlik maskeleri görüntüleri veya silinerek düğmeler görünümünden öğelere dokular ekleme veya cam benzeri yüzeyleri üretmek için gradyanları birleştirme oluşturmak için gibi ilginç görsel efektler oluşturmak için kullanılır. Aşağıdaki çizimde geçirgenlik maskesi kullanımını göstermektedir. Damalı arka plan maskesi bölümlerini saydam göstermek için kullanılır.  
  
 ![LinearGradientBrush geçirgenlik maskesi olan nesne](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-graphicsmm-opacitymask-imageexample.png "wcpsdk_graphicsmm_opacitymask_imageexample")  
Geçirgenlik maskeleme örneği  
  
<a name="creatingopacitymasks"></a>   
## <a name="creating-an-opacity-mask"></a>Geçirgenlik maskesi oluşturma  
 Geçirgenlik maskesi oluşturmak için oluşturduğunuz bir <xref:System.Windows.Media.Brush> ve uygulayan <xref:System.Windows.UIElement.OpacityMask%2A> bir öğe veya görselin özelliği. Herhangi bir türü kullanabilirsiniz <xref:System.Windows.Media.Brush> geçirgenlik maskesi olarak.  
  
-   <xref:System.Windows.Media.LinearGradientBrush>, <xref:System.Windows.Media.RadialGradientBrush>: Bir öğe veya görünümden visual yavaşça yapmak için kullanılır.  
  
     Aşağıdaki resimde gösterildiği bir <xref:System.Windows.Media.LinearGradientBrush> geçirgenlik maskesi olarak kullanılır.  
  
     ![LinearGradientBrush geçirgenlik maskesi olan bir nesne](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-graphicsmm-brushes-lineagradientopacitymasksingle.jpg "wcpsdk_graphicsmm_brushes_lineagradientopacitymasksingle")  
LinearGradientBrush geçirgenlik maskeleme örneği  
  
-   <xref:System.Windows.Media.ImageBrush>: Doku ve Yumuşak ya da bozuk efektler oluşturmak için kullanılır.  
  
     Aşağıdaki resimde gösterildiği bir <xref:System.Windows.Media.ImageBrush> geçirgenlik maskesi olarak kullanılır.  
  
     ![ImageBrush geçirgenlik maskesi olan nesneyi](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-graphicsmm-brushes-imageasopacitymasksingle.jpg "wcpsdk_graphicsmm_brushes_imageasopacitymasksingle")  
LinearGradientBrush geçirgenlik maskeleme örneği  
  
-   <xref:System.Windows.Media.DrawingBrush>: Şekil, görüntüler ve gradyan modellerinden karmaşık geçirgenlik maskeleri oluşturmak için kullanılır.  
  
     Aşağıdaki resimde gösterildiği bir <xref:System.Windows.Media.DrawingBrush> geçirgenlik maskesi olarak kullanılır.  
  
     ![DrawingBrush geçirgenlik maskesi nesnesiyle](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-drawingbrushasopacitymask-single.jpg "wcpsdk_drawingbrushasopacitymask_single")  
DrawingBrush geçirgenlik maskeleme örneği  
  
 Gradyan Fırçalar (<xref:System.Windows.Media.LinearGradientBrush> ve <xref:System.Windows.Media.RadialGradientBrush>) özellikle çok geçirgenlik maskesi olarak kullanım için uygundur. Çünkü bir <xref:System.Windows.Media.SolidColorBrush> dolgular tekdüze bir renk ile alanı yaptıkları zayıf opaklık maskeleri; kullanarak bir <xref:System.Windows.Media.SolidColorBrush> öğenin veya görselin ayarlamaya eşittir <xref:System.Windows.UIElement.OpacityMask%2A> özelliği.  
  
<a name="creatingopacitymaskswithgradients"></a>   
## <a name="using-a-gradient-as-an-opacity-mask"></a>Gradyan geçirgenlik maskesi kullanma  
 Gradyan dolgusu oluşturmak için iki veya daha fazla gradyan durağı belirtin. Her gradyan durağının içeren bir renk ve bir konuma açıklar (bkz [gradyan genel bakış ve düz renk ile Boyama](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md) gradyanları oluşturma ve kullanma hakkında daha fazla bilgi için). Renkleri karıştırma yerine opaklık maskesi gradyan alfa kanal değerleri karıştırır dışında işlem gradyan geçirgenlik maskesi olarak, kullanırken aynıdır. Bu nedenle gradyan içeriği gerçek rengi önemli değildir; yalnızca alfa kanal veya her rengin geçirgenliğini önemlidir. Bir örnek verilmiştir.  
  
 [!code-xaml[OpacityMasksSnippet#LinearGradientOpacityMaskonImage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OpacityMasksSnippet/CS/GradientBrushExample.xaml#lineargradientopacitymaskonimage)]  
  
<a name="specifyinggradientcolors"></a>   
## <a name="specifying-gradient-stops-for-an-opacity-mask"></a>Geçirgenlik maskesi için gradyan durakları belirtme  
 Önceki örnekte, sistem tarafından tanımlanan renk <xref:System.Windows.Media.Colors.Black%2A> geçişin başlangıç rengi kullanılır. Çünkü tüm renkleri <xref:System.Windows.Media.Colors> sınıfı dışında <xref:System.Windows.Media.Colors.Transparent%2A>, bunlar yalnızca gradyan geçirgenlik maskesinin başlangıç rengini tanımlamak için kullanılabilecek tam olarak donuk olan.  
  
 Geçirgenlik maskesi tanımlarken alfa değerleri üzerinde ek denetim için kullanarak renklerin alfa kanal belirtebilirsiniz [!INCLUDE[TLA#tla_argb](../../../../includes/tlasharptla-argb-md.md)] işaretleme veya kullanarak onaltılık gösterimde <xref:System.Windows.Media.Color.FromScRgb%2A?displayProperty=nameWithType> yöntemi.  
  
<a name="argbsyntax"></a>   
### <a name="specifying-color-opacity-in-xaml"></a>"XAML" içinde Renk Geçirgenliği Belirtme  
 İçinde [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], kullandığınız [!INCLUDE[TLA2#tla_argb](../../../../includes/tla2sharptla-argb-md.md)] tek tek renkleri geçirgenliğini belirtmek için onaltılık gösterimi. [!INCLUDE[TLA2#tla_argb](../../../../includes/tla2sharptla-argb-md.md)] onaltılık gösterimi aşağıdaki söz dizimini kullanır:  
  
 `#` **aa** *rrggbb*  
  
 *Aa* önceki satırda rengin geçirgenliğini belirtmek için kullanılan iki basamaklı onaltılık değeri temsil eder. *Rr*, *gg*, ve *bb* her rengi kırmızı, yeşil ve mavi miktarını belirtmek için kullanılan iki basamaklı onaltılık değeri temsil eder. Her bir onaltılık değerinin 0-9 veya A-f arasında olabilir 0 en küçük değerdir ve F en büyük değerdir. 00 alfa değeri FF alfa değeri bir renk oluştururken, tamamen saydam olacak bir renk tamamıyla opak belirtir.  Aşağıdaki örnekte, onaltılık [!INCLUDE[TLA2#tla_argb](../../../../includes/tla2sharptla-argb-md.md)] gösterimi iki rengi belirtmek için kullanılır. İlk tamamıyla opak açıkken ikinci tamamen saydamdır.  
  
 [!code-xaml[OpacityMasksSnippet#AARRGGBBValueonOpacityMask](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OpacityMasksSnippet/CS/GradientBrushExample.xaml#aarrggbbvalueonopacitymask)]  
  
<a name="usingimageasopacitymask"></a>   
## <a name="using-an-image-as-an-opacity-mask"></a>Bir görüntü geçirgenlik maskesi kullanma  
 Görüntüleri geçirgenlik maskesi olarak da kullanılabilir. Aşağıdaki resimde bir örnek gösterilmektedir. Damalı arka plan maskesi bölümlerini saydam göstermek için kullanılır.  
  
 ![ImageBrush geçirgenlik maskesi olan bir nesne](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-graphicsmm-imageasopacitymask.png "wcpsdk_graphicsmm_imageasopacitymask")  
Geçirgenlik maskeleme örneği  
  
 Bir görüntü geçirgenlik maskesi olarak kullanmak için bir <xref:System.Windows.Media.ImageBrush> resmi içerecek. Geçirgenlik maskesi olarak kullanılacak görüntüyü oluştururken, görüntünün saydamlık, birden çok düzeyi gibi destekleyen bir biçimde kaydetmek [!INCLUDE[TLA#tla_png](../../../../includes/tlasharptla-png-md.md)]. Aşağıdaki örnek önceki gösterimi oluşturmak için kullanılan kod gösterir.  
  
 [!code-xaml[OpacityMasksSnippet#UIElementOpacityMask](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OpacityMasksSnippet/CS/ImageBrushExample.xaml#uielementopacitymask)]  
  
<a name="tilingimageopacitymask"></a>   
### <a name="using-a-tiled-image-as-an-opacity-mask"></a>Geçirgenlik maskesi döşeli görüntü kullanma  
 Aşağıdaki örnekte, başka bir işlemle aynı görüntü kullanılan <xref:System.Windows.Media.ImageBrush>, ancak fırça döşeme özellikleri görüntü 50 piksel kare döşemesi üretmek için kullanılır.  
  
 [!code-xaml[OpacityMasksSnippet#TiledImageasOpacityMask](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OpacityMasksSnippet/CS/ImageBrushExample.xaml#tiledimageasopacitymask)]  
  
<a name="drawingbrushasopacitymask"></a>   
## <a name="creating-an-opacity-mask-from-a-drawing"></a>Çizimden Geçirgenlik maskesi oluşturma  
 Çizimler geçirgenlik maskesi kullanılır. Çizim içinde bulunan şekiller kendilerini gradyan, düz renkler, görüntüler veya diğer çizimlerle bile doldurulabilir. Aşağıdaki resimde geçirgenlik maskesi olarak kullanılan bir çizim örneği gösterilmiştir. Damalı arka plan maskesi bölümlerini saydam göstermek için kullanılır.  
  
 ![DrawingBrush geçirgenlik maskesi olan bir nesne](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-drawingbrushasopacitymask.png "wcpsdk_drawingbrushasopacitymask")  
DrawingBrush geçirgenlik maskeleme örneği  
  
 Çizim geçirgenlik maskesi olarak kullanmak için bir <xref:System.Windows.Media.DrawingBrush> çizimi içerecek. Aşağıdaki örnek önceki gösterimi oluşturmak için kullanılan kod gösterir:  
  
 [!code-xaml[OpacityMasksSnippet#OpacityMaskfromDrawing](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OpacityMasksSnippet/CS/DrawingBrushExample.xaml#opacitymaskfromdrawing)]  
  
<a name="tileddrawingbrush"></a>   
### <a name="using-a-tiled-drawing-as-an-opacity-mask"></a>Geçirgenlik maskesi döşeli çizim kullanma  
 Gibi <xref:System.Windows.Media.ImageBrush>, <xref:System.Windows.Media.DrawingBrush> kendi çizim döşeme yapılabilir. Aşağıdaki örnekte, çizim Fırçası döşeli geçirgenlik maskesi oluşturmak için kullanılır.  
  
 [!code-xaml[OpacityMasksSnippet#TiledDrawingasOpacityMask](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OpacityMasksSnippet/CS/DrawingBrushExample.xaml#tileddrawingasopacitymask)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Görüntüler, Çizimler ve Görsellerle Boyama](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md)  
 [Düz Renkler ve Gradyanlar ile Boyamaya Genel Bakış](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md)
