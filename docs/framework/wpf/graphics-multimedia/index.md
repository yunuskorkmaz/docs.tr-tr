---
title: Grafikler ve Multimedya
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- media [WPF], features
- video effects [WPF]
- sound effects [WPF]
- animation [WPF], features
- graphics features [WPF]
- transition effects [WPF]
ms.assetid: 1817d9dc-3d6c-46cb-afc8-63b0bae35e37
ms.openlocfilehash: ecc54ad9453343f6306b0133fa180abd0db46f82
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84596428"
---
# <a name="graphics-and-multimedia"></a>Grafikler ve Multimedya

<a name="introduction"></a>
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]Çoklu ortam, vektör grafikleri, animasyon ve içerik oluşturma desteği sunarak geliştiricilerin ilginç kullanıcı arabirimlerini ve içerikleri oluşturmasını kolaylaştırır. Visual Studio 'yu kullanarak vektör grafikleri veya karmaşık animasyonlar oluşturabilir ve bu ortamları uygulamalarınızla tümleştirin.

Bu konuda [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] , uygulamalarınıza grafikler, geçiş efektleri, ses ve video eklemenize olanak sağlayan grafik, animasyon ve medya özellikleri tanıtılmaktadır.

> [!NOTE]
> Windows hizmetinde WPF türlerinin kullanılması kesinlikle önerilmez. Windows hizmetinde WPF türlerini kullanmaya çalışırsanız, hizmet beklendiği gibi çalışmayabilir.

<a name="whats_new_with_graphics_and_multimedia_in_wpf_4"></a>

## <a name="whats-new-with-graphics-and-multimedia-in-wpf-4"></a>WPF 4 ' te grafik ve multimedya yenilikleri

Grafiklerle ve animasyonlarla ilgili çeşitli değişiklikler yapılmıştır.

- Düzen yuvarlama

  Bir nesne kenarı bir piksel cihazının ortasında yer alıyorsa, DPı bağımsız grafik sistemi bulanık veya yarı saydam kenarlar gibi işleme yapıtları oluşturabilir. WPF 'nin önceki sürümleri, bu durumu işlemeye yardımcı olmak için piksel yaslaması içerir. Silverlight 2 ' de, öğelerin tam piksel sınırlarına dönüşecek şekilde öğeleri taşımanın başka bir yolu olan düzen yuvarlama sunuldu. WPF artık ekli özelliği olan düzen yuvarlamayı desteklemektedir <xref:System.Windows.FrameworkElement.UseLayoutRounding%2A> <xref:System.Windows.FrameworkElement> .

- Önbelleğe alınmış bileşim

  Yeni <xref:System.Windows.Media.BitmapCache> ve <xref:System.Windows.Media.BitmapCacheBrush> sınıflarını kullanarak görsel ağacın karmaşık bir bölümünü bit eşlem olarak önbelleğe alabilir ve büyük ölçüde işleme süresini geliştirebilirsiniz. Bit eşlem, fare tıklamaları gibi kullanıcı girişine yanıt vermeye devam eder ve tıpkı herhangi bir fırçayla tıpkı diğer öğelere de boyayabilirsiniz.

- Pixel Shader 3 desteği

  WPF 4, <xref:System.Windows.Media.Effects.ShaderEffect> uygulamaların Pixel Shader (PS) sürüm 3,0 ' i kullanarak etkileri yazmasına izin vererek wpf 3,5 SP1 'de sunulan desteğin en üstünde oluşturulur. PS 3,0 gölgelendirici modeli PS 2,0 ' den daha karmaşıktır ve desteklenen donanımlar üzerinde daha da fazla etkiye olanak tanır.

- Kolaylaştırıcı İşlevler

  Animasyonların davranışları üzerinde size ek denetim sağlayan kolaylaştırıcı işlevlerle animasyonları geliştirebilirsiniz. Örneğin, <xref:System.Windows.Media.Animation.ElasticEase> animasyona bir spriny davranışı vermek için bir animasyon uygulayabilirsiniz. Daha fazla bilgi için bkz <xref:System.Windows.Media.Animation> . ad alanındaki kolaylaştırıcı türler.

<a name="graphics_and_rendering"></a>

## <a name="graphics-and-rendering"></a>Grafik ve Işleme

WPF, yüksek kaliteli 2B grafikler için destek içerir. İşlevsellik, fırçalar, geometriler, görüntüler, şekiller ve dönüşümler içerir. Daha fazla bilgi için bkz. [grafikler](graphics.md). Grafik öğelerinin işlenmesi sınıfı temel alır <xref:System.Windows.Media.Visual> . Ekrandaki görsel nesnelerin yapısı, görsel ağaç tarafından açıklanmıştır. Daha fazla bilgi için bkz. [WPF Grafik Işlemeye genel bakış](wpf-graphics-rendering-overview.md).

### <a name="2d-shapes"></a>2B şekiller

WPF, aşağıdaki çizimin gösterdiği dikdörtgen ve elips gibi yaygın olarak kullanılan, vektör çizimli 2B şekillerin bir kitaplığını sağlar.

![Üç nokta ve dikdörtgeni gösteren diyagram.](./media/index/two-deminsional-shapes-ellipses-rectangles.png)

Bu iç WPF şekilleri yalnızca şekil değildir: klavye ve fare girişi içeren en yaygın denetimlerden beklediğinizi birçok özelliği uygulayan programlanabilir öğelerdir. Aşağıdaki örnek, <xref:System.Windows.UIElement.MouseUp> bir öğesine tıklanarak oluşturulan olayın nasıl işleneceğini gösterir <xref:System.Windows.Shapes.Ellipse> .

```xaml
<Window
  xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
  xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
  x:Class="Window1" >
  <Ellipse Fill="LightBlue" MouseUp="ellipseButton_MouseUp" />
</Window>
```

```csharp
public partial class Window1  : Window
{
    void ellipseButton_MouseUp(object sender, MouseButtonEventArgs e)
    {
        MessageBox.Show("You clicked the ellipse!");
    }
}
```

```vb
Partial Public Class Window1
    Inherits Window
    Private Sub ellipseButton_MouseUp(ByVal sender As Object, ByVal e As MouseButtonEventArgs)
        MessageBox.Show("You clicked the ellipse!")
    End Sub
End Class
```

Aşağıdaki çizimde, önceki [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] biçimlendirme ve arka plan kodu için çıkış gösterilmektedir.

!["Elips tıkladınız!" ifadesini bildiren bir ileti kutusu](./media/index/messagebox-text-output.png)

Daha fazla bilgi için bkz. [WPF 'de şekillere ve temel çizime genel bakış](shapes-and-basic-drawing-in-wpf-overview.md). Bir tanıtıcı örnek için bkz. [Şekil öğeleri örneği](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ShapeElements).

### <a name="2d-geometries"></a>2B geometriler

WPF 'in sağladığı 2B şekiller yeterli olmadığında, kendinizinkini oluşturmak için geometriler ve yollar için WPF desteği kullanabilirsiniz. Aşağıdaki çizimde, bir çizim Fırçası olarak şekiller oluşturmak ve diğer WPF öğelerini kırpmak için geometriler nasıl kullanabileceğiniz gösterilmektedir.

![Şekil oluşturmak için geometrilerin nasıl kullanılabileceğini gösteren ekran görüntüsü.](./media/index/use-geometries-create-shapes.png)

Daha fazla bilgi için bkz. [geometriye genel bakış](geometry-overview.md). Tanıtıcı bir örnek için bkz. [geometriler örneği](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Geometry).

### <a name="2d-effects"></a>2B efektler

WPF, çeşitli efektler oluşturmak için kullanabileceğiniz bir 2B sınıf kitaplığı sağlar. WPF 'in 2B işleme özelliği, [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] degradeler, bit eşlemler, çizimler ve videolar içeren öğeleri boyama ve döndürme, ölçekleme ve eğriltme kullanarak bunları değiştirme olanağı sağlar. Aşağıdaki çizimde, WPF fırçalarını kullanarak elde edilebilecek birçok etkiye bir örnek verilmiştir.

![Farklı WPF fırçalarını ve boyama öğelerini gösteren çizim.](./media/index/brushes-paint-elements.png)

Daha fazla bilgi için bkz. [WPF Fırçalarına Genel Bakış](wpf-brushes-overview.md). Tanıtıcı bir örnek için bkz. [fırçalar örneği](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Brushes).

<a name="rendering"></a>

## <a name="3d-rendering"></a>3B Işleme

WPF, daha heyecan verici düzen, [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] ve veri görselleştirmesi oluşturabilmeniz IÇIN WPF 'de 2B grafik desteğiyle tümleştirilebilen bir dizi 3B işleme özelliği sağlar. Bu, tayfın bir ucunda, 2B görüntüleri aşağıdaki çizimin gösterdiği 3B şekillerin yüzeylerine göre işlemenizi sağlar.

![Farklı dokularla 3B şekilleri gösteren örnek ekran görüntüsü.](./media/index/visual-three-dimensional-shape.png)

Daha fazla bilgi için bkz. [3B grafiklere genel bakış](3-d-graphics-overview.md). Tanıtıcı bir örnek için bkz. [3B Solids örneği](https://go.microsoft.com/fwlink/?LinkID=159964).

<a name="animation"></a>

## <a name="animation"></a>Animasyon

Denetimleri ve öğeleri büyütmek, sallama, döndürme ve belirme yapmak için animasyon kullanın; ve ilginç sayfa geçişleri ve daha fazlasını oluşturun. WPF birçok özelliğe animasyon uygulamanızı sağladığından, yalnızca birçok WPF nesnesini hareketlendirmenize olanak tanıdığından, oluşturduğunuz özel nesnelere animasyon eklemek için WPF de kullanabilirsiniz.

![Animasyonlu küpün ekran görüntüsü.](./media/index/animate-custom-objects.png)

Daha fazla bilgi için bkz. [animasyon genel bakış](animation-overview.md). Bir tanıtıcı örnek için bkz. [animasyon örnek Galerisi](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/AnimationExamples).

<a name="media"></a>

## <a name="media"></a>Medya

Görüntü, video ve ses, bilgi ve kullanıcı deneyimlerini vermenin zengin ortamlarıdır.

### <a name="images"></a>Görüntüler

Simgeler, arka planlar ve hatta animasyonların parçaları dahil olmak üzere birçok uygulamanın temel bir parçası olan görüntüler. Genellikle görüntüleri kullanmanız gerektiğinden, WPF bunlarla çeşitli yollarla çalışma olanağı sunar. Aşağıdaki çizimde bu yolların yalnızca biri gösterilmektedir.

![Stil örnek ekran görüntüsü](../controls/media/stylingintro-eventtriggers.png "StylingIntro_EventTriggers")

Daha fazla bilgi için bkz. [Imaging 'e genel bakış](imaging-overview.md).

### <a name="video-and-audio"></a>Video ve ses

WPF 'nin grafik özelliklerinin temel bir özelliği, video ve ses dahil olmak üzere multimedya ile çalışmaya yönelik yerel destek sağlamaktır. Aşağıdaki örnek, bir medya yürütücüsünün bir uygulamaya nasıl ekleneceğini gösterir.

```xaml
<MediaElement Source="media\numbers.wmv" Width="450" Height="250" />
```

<xref:System.Windows.Controls.MediaElement>hem video hem de ses oynamaya sahiptir ve özel Uıof 'ın kolay oluşturulmasına izin vermek için yeterince genişletilebilir.

Daha fazla bilgi için [Çoklu ortama genel bakış](multimedia-overview.md)konusuna bakın.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Media>
- <xref:System.Windows.Media.Animation>
- <xref:System.Windows.Media.Media3D>
- [2B Grafikleri ve Görüntüleme](../advanced/optimizing-performance-2d-graphics-and-imaging.md)
- [WPF Genel Bakışı İçinde Şekiller ve Temel Çizimler](shapes-and-basic-drawing-in-wpf-overview.md)
- [Düz Renkler ve Gradyanlar ile Boyamaya Genel Bakış](painting-with-solid-colors-and-gradients-overview.md)
- [Görüntüler, Çizimler ve Görsellerle Boyama](painting-with-images-drawings-and-visuals.md)
- [Animasyon ve Zamanlama ile İlgili Nasıl Yapılır Konuları](animation-and-timing-how-to-topics.md)
- [3B Grafiklere Genel Bakış](3-d-graphics-overview.md)
- [Multimedyaya Genel Bakış](multimedia-overview.md)
