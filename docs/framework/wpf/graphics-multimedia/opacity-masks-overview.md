---
title: Opaklık Maskelerine Genel Bakış
ms.date: 03/30/2017
helpviewer_keywords:
- brushes [WPF], opacity masks
- masks [WPF], opacity
- opacity [WPF], masks
ms.assetid: 22367fab-5f59-4583-abfd-db2bf86eaef7
ms.openlocfilehash: 7554471d8b812b60e0b1aeb6dd3096b542ca44d6
ms.sourcegitcommit: 4d8efe00f2e5ab42e598aff298d13b8c052d9593
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/16/2019
ms.locfileid: "68238413"
---
# <a name="opacity-masks-overview"></a>Opaklık Maskelerine Genel Bakış
Opaklık maskeleri saydam veya saydam kısmen bölümleri bir öğe veya görselin yapmanızı sağlar. Geçirgenlik maskesi oluşturma için geçerli bir <xref:System.Windows.Media.Brush> için <xref:System.Windows.UIElement.OpacityMask%2A> özelliği bir öğe veya <xref:System.Windows.Media.Visual>.  Fırça öğeye veya görsel eşlenir ve her fırça piksel geçirgenlik değeri elde edilen opaklık öğe veya görselin karşılık gelen her pikselin belirlemek için kullanılır.  
  
<a name="prereqs"></a>   
## <a name="prerequisites"></a>Önkoşullar  
 Bu genel bakışta aşina olduğunuzu varsayar <xref:System.Windows.Media.Brush> nesneleri. Fırça kullanarak bir giriş için bkz. [düz renkler ve gradyanlar genel bakış boyama](painting-with-solid-colors-and-gradients-overview.md). Hakkında bilgi için <xref:System.Windows.Media.ImageBrush> ve <xref:System.Windows.Media.DrawingBrush>, bkz: [görüntüler, çizimler ve görsellerle boyama](painting-with-images-drawings-and-visuals.md).  
  
<a name="opacitymasks"></a>   
## <a name="creating-visual-effects-with-opacity-masks"></a>Opaklık maskeleri görsel efekt oluşturma  
 Bir opaklık maskesi, içeriği öğe veya visual eşleyerek çalışır. Alfa kanalını her fırçanın piksel sonra elde edilen opaklığını öğe veya görselin karşılık gelen piksel belirlemek üzere kullanılır; Fırça rengini gerçek göz ardı edilir. Fırça belirli bir kısmı saydamdır, ilgili kısmının öğe veya visual saydam hale gelir. Fırça belirli bir kısmı katıysa öğe veya görselin ilgili kısmının opaklığını değiştirilmez. Geçirgenlik maskesi tarafından belirtilen opaklık herhangi opaklık ayarlarla öğesinde mevcut veya görsel birleştirilir. Örneğin, yüzde 25 donuk bir öğedir ve tam opak tamamen saydam olarak geçiş uygulanan bir opaklık maskesi, öğenin yüzde 25 opaklığı tamamen saydam olarak geçiş sonucudur.  
  
> [!NOTE]
>  Bu genel bakışta örneklerde opaklık maskeleri görüntü öğelerde kullanımını gösteren olsa da, herhangi bir öğeye bir opaklık maskesi uygulanabilir veya <xref:System.Windows.Media.Visual>paneller ve denetimleri dahil olmak üzere.  
  
 Opaklık maskeleri ilgi çekici görsel efektler görünümünden, doku öğeleri eklemek ya da cam benzeri yüzeyler üretmek için gradyan birleştirmek için Soldurma düğme veya görüntü oluşturma gibi oluşturmak için kullanılır. Aşağıdaki çizim bir opaklık maskesi kullanımını gösterir. Damalı arka plan maske saydam bölümlerini göstermek için kullanılır.  
  
 ![Nesne LinearGradientBrush opaklık maskesine sahip](./media/wcpsdk-graphicsmm-opacitymask-imageexample.png "wcpsdk_graphicsmm_opacitymask_imageexample")  
Opaklık maskeleme örneği  
  
<a name="creatingopacitymasks"></a>   
## <a name="creating-an-opacity-mask"></a>Geçirgenlik maskesi oluşturma  
 Geçirgenlik maskesi oluşturma için oluşturduğunuz bir <xref:System.Windows.Media.Brush> ve uygulamak <xref:System.Windows.UIElement.OpacityMask%2A> bir öğe veya görselin özelliği. Herhangi bir türde kullanabileceğiniz <xref:System.Windows.Media.Brush> geçirgenlik maskesi olarak.  
  
- <xref:System.Windows.Media.LinearGradientBrush>, <xref:System.Windows.Media.RadialGradientBrush>: Bir öğe veya görünümden visual fade yapmak için kullanılır.  
  
     Aşağıdaki görüntüde bir <xref:System.Windows.Media.LinearGradientBrush> geçirgenlik maskesi olarak kullanılır.  
  
     ![Bir LinearGradientBrush opaklık maskesine sahip bir nesne](./media/wcpsdk-graphicsmm-brushes-lineagradientopacitymasksingle.jpg "wcpsdk_graphicsmm_brushes_lineagradientopacitymasksingle")  
LinearGradientBrush opaklık maskeleme örneği  
  
- <xref:System.Windows.Media.ImageBrush>: Doku ve yazılım ya da bozuk efektler oluşturmak için kullanılır.  
  
     Aşağıdaki görüntüde bir <xref:System.Windows.Media.ImageBrush> geçirgenlik maskesi olarak kullanılır.  
  
     ![Bir ImageBrush opaklık maskesine sahip bir nesne](./media/wcpsdk-graphicsmm-brushes-imageasopacitymasksingle.jpg "wcpsdk_graphicsmm_brushes_imageasopacitymasksingle")  
LinearGradientBrush opaklık maskeleme örneği  
  
- <xref:System.Windows.Media.DrawingBrush>: Şekilleri ve görüntüleri gradyanlar modellerinden karmaşık opaklık maskeleri oluşturmak için kullanılır.  
  
     Aşağıdaki görüntüde bir <xref:System.Windows.Media.DrawingBrush> geçirgenlik maskesi olarak kullanılır.  
  
     ![DrawingBrush opaklık maskesine sahip nesne](./media/wcpsdk-drawingbrushasopacitymask-single.jpg "wcpsdk_drawingbrushasopacitymask_single")  
DrawingBrush opaklık maskeleme örneği  
  
 Gradyan Fırçalar (<xref:System.Windows.Media.LinearGradientBrush> ve <xref:System.Windows.Media.RadialGradientBrush>) özellikle bir opaklık maskesi olarak kullanım için uygundur. Çünkü bir <xref:System.Windows.Media.SolidColorBrush> dolgular Tekdüzen bir renk ile bir alanı yaptıkları düşük opaklık maskeleri; kullanarak bir <xref:System.Windows.Media.SolidColorBrush> öğenin veya görselin ayarlamaya eşittir <xref:System.Windows.UIElement.OpacityMask%2A> özelliği.  
  
<a name="creatingopacitymaskswithgradients"></a>   
## <a name="using-a-gradient-as-an-opacity-mask"></a>Gradyan geçirgenlik maskesi kullanma  
 Gradyan Dolgu oluşturmak için iki veya daha fazla gradyan duraklarının belirtin. Her gradyan durağını içeren bir renk ve bir konumu açıklar (bkz [düz renkler ve gradyanlar genel bakış boyama](painting-with-solid-colors-and-gradients-overview.md) gradyanları oluşturma ve kullanma hakkında daha fazla bilgi için). Renkleri karıştırma yerine opaklık maskesi gradyan alfa kanalı değerlerini karıştırır dışında aynı gradyan bir opaklık maskesi kullanılırken işlemidir. Bu nedenle gradyan İçindekiler gerçek renk önemli değildir; yalnızca alfa kanalı veya her rengin geçirgenliğini önemlidir. Bir örnek verilmiştir.  
  
 [!code-xaml[OpacityMasksSnippet#LinearGradientOpacityMaskonImage](~/samples/snippets/csharp/VS_Snippets_Wpf/OpacityMasksSnippet/CS/GradientBrushExample.xaml#lineargradientopacitymaskonimage)]  
  
<a name="specifyinggradientcolors"></a>   
## <a name="specifying-gradient-stops-for-an-opacity-mask"></a>Gradyan durakları bir opaklık maskesi için belirtme  
 Önceki örnekte, sistem tarafından tanımlanan renk <xref:System.Windows.Media.Colors.Black%2A> gradyan başlangıç rengi olarak kullanılır. Çünkü tüm renkleri <xref:System.Windows.Media.Colors> sınıfı dışında <xref:System.Windows.Media.Colors.Transparent%2A>, bunlar yalnızca bir gradyan opaklık maskesi için başlangıç rengini tanımlamak için kullanılabilir tam opak olan.  
  
 Bir opaklık maskesi tanımlarken alfa değerleri üzerinde ek denetim için alfa kanalı veya biçimlendirmede ARGB onaltılık gösterim kullanarak renkler belirtebilirsiniz <xref:System.Windows.Media.Color.FromScRgb%2A?displayProperty=nameWithType> yöntemi.  
  
<a name="argbsyntax"></a>   
### <a name="specifying-color-opacity-in-xaml"></a>"XAML" renk opaklığı belirtme  
 İçinde [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], ARGB onaltılık gösterimde tek tek renkler opaklığını belirtmek için kullanın. ARGB onaltılık gösterim aşağıdaki sözdizimini kullanır:  
  
 `#` **aa** *rrggbb*  
  
 *Aa* önceki satıra rengin geçirgenliğini belirtmek için kullanılan iki basamaklı bir onaltılık değer temsil eder. *Rr*, *gg*, ve *bb* her rengin kırmızı, yeşil ve mavi miktarını belirtmek için kullanılan iki basamaklı bir onaltılık değeri temsil eder. Her bir onaltılık basamak 0-9 veya A-f arasında bir değer olabilir. en küçük değer 0 ise ve F en büyük değerdir. Alfa değeri 00 ila tamamen opak FF alfa değeri olan bir renk oluştururken tamamen şeffaf olduğundan bir renk belirtir.  Aşağıdaki örnekte, ARGB onaltılık gösterim iki renkleri belirtmek için kullanılır. İlk tam opak açıkken ikinci tamamen saydamdır.  
  
 [!code-xaml[OpacityMasksSnippet#AARRGGBBValueonOpacityMask](~/samples/snippets/csharp/VS_Snippets_Wpf/OpacityMasksSnippet/CS/GradientBrushExample.xaml#aarrggbbvalueonopacitymask)]  
  
<a name="usingimageasopacitymask"></a>   
## <a name="using-an-image-as-an-opacity-mask"></a>Bir görüntü geçirgenlik maskesi kullanma  
 Görüntüleri bir opaklık maskesi da kullanılabilir. Aşağıdaki resimde bir örnek gösterilir. Damalı arka plan maske saydam bölümlerini göstermek için kullanılır.  
  
 ![Bir ImageBrush opaklık maskesine sahip bir nesne](./media/wcpsdk-graphicsmm-imageasopacitymask.png "wcpsdk_graphicsmm_imageasopacitymask")  
Opaklık maskeleme örneği  
  
 Bir opaklık maskesi görüntü kullanmak için bir <xref:System.Windows.Media.ImageBrush> resmi içerecek. Bir opaklık maskesi kullanılacak bir görüntü oluşturulurken görüntü gibi birden fazla düzeyde saydamlık destekleyen bir biçimde kaydetmek [!INCLUDE[TLA#tla_png](../../../../includes/tlasharptla-png-md.md)]. Aşağıdaki örnek, önceki çizim oluşturmak için kullanılan kodlar gösterilmiştir.  
  
 [!code-xaml[OpacityMasksSnippet#UIElementOpacityMask](~/samples/snippets/csharp/VS_Snippets_Wpf/OpacityMasksSnippet/CS/ImageBrushExample.xaml#uielementopacitymask)]  
  
<a name="tilingimageopacitymask"></a>   
### <a name="using-a-tiled-image-as-an-opacity-mask"></a>Döşenmiş bir görüntü geçirgenlik maskesi kullanma  
 Aşağıdaki örnekte, birbiriyle aynı görüntü kullanılan <xref:System.Windows.Media.ImageBrush>, ancak fırça döşeme özellikleri kutucukları görüntü 50 piksel kare oluşturmak için kullanılır.  
  
 [!code-xaml[OpacityMasksSnippet#TiledImageasOpacityMask](~/samples/snippets/csharp/VS_Snippets_Wpf/OpacityMasksSnippet/CS/ImageBrushExample.xaml#tiledimageasopacitymask)]  
  
<a name="drawingbrushasopacitymask"></a>   
## <a name="creating-an-opacity-mask-from-a-drawing"></a>Çizimden Geçirgenlik maskesi oluşturma  
 Çizimler bir opaklık maskesi kullanılır. Çizim içinde bulunan şekilleri gradyanlar, düz renkler, görüntüleri veya hatta diğer çizimler ile kendilerini doldurulabilir. Aşağıdaki görüntüde bir opaklık maskesi kullanılan bir çizim bir örnek gösterilmektedir. Damalı arka plan maske saydam bölümlerini göstermek için kullanılır.  
  
 ![DrawingBrush opaklık maskesine sahip bir nesne](./media/wcpsdk-drawingbrushasopacitymask.png "wcpsdk_drawingbrushasopacitymask")  
DrawingBrush opaklık maskeleme örneği  
  
 Çizim geçirgenlik maskesi olarak kullanmak için bir <xref:System.Windows.Media.DrawingBrush> çizimi içerecek. Aşağıdaki örnek, önceki çizim oluşturmak için kullanılan kodlar gösterilmiştir:  
  
 [!code-xaml[OpacityMasksSnippet#OpacityMaskfromDrawing](~/samples/snippets/csharp/VS_Snippets_Wpf/OpacityMasksSnippet/CS/DrawingBrushExample.xaml#opacitymaskfromdrawing)]  
  
<a name="tileddrawingbrush"></a>   
### <a name="using-a-tiled-drawing-as-an-opacity-mask"></a>Döşenmiş çizim geçirgenlik maskesi kullanma  
 Gibi <xref:System.Windows.Media.ImageBrush>, <xref:System.Windows.Media.DrawingBrush> kendi çizim kutucuğa yapılabilir. Aşağıdaki örnekte, bir çizim Fırçası döşenmiş geçirgenlik maskesi oluşturma için kullanılır.  
  
 [!code-xaml[OpacityMasksSnippet#TiledDrawingasOpacityMask](~/samples/snippets/csharp/VS_Snippets_Wpf/OpacityMasksSnippet/CS/DrawingBrushExample.xaml#tileddrawingasopacitymask)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Görüntüler, Çizimler ve Görsellerle Boyama](painting-with-images-drawings-and-visuals.md)
- [Düz Renkler ve Gradyanlar ile Boyamaya Genel Bakış](painting-with-solid-colors-and-gradients-overview.md)
