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
ms.openlocfilehash: 8636afcc5b63b71dc729812a7f3eb4945ba49494
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/21/2020
ms.locfileid: "80112043"
---
# <a name="graphics-and-multimedia"></a>Grafikler ve Multimedya

<a name="introduction"></a>
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]multimedya, vektör grafikleri, animasyon ve içerik kompozisyonu için destek sağlayarak geliştiricilerin ilginç kullanıcı arabirimleri ve içerik oluşturmalarını kolaylaştırır. Visual Studio'yu kullanarak vektör grafikleri veya karmaşık animasyonlar oluşturabilir ve ortamı uygulamalarınız için entegre edebilirsiniz.

Bu konu, uygulamalarınıza grafik, geçiş [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]efektleri, ses ve video eklemenize olanak tanıyan grafik, animasyon ve medya özelliklerini tanır.

> [!NOTE]
> Bir Windows hizmetinde WPF türlerinin kullanılması nın önerilmesi kuvvetle yapılır. Bir Windows hizmetinde WPF türlerini kullanmaya çalışırsanız, hizmet beklendiği gibi çalışmayabilir.

<a name="whats_new_with_graphics_and_multimedia_in_wpf_4"></a>

## <a name="whats-new-with-graphics-and-multimedia-in-wpf-4"></a>WPF 4'te Grafik ve Multimedya ile Yenilikler

Grafik ve animasyonlarla ilgili çeşitli değişiklikler yapılmıştır.

- Düzen Yuvarlama

  Bir nesne kenarı bir piksel aygıtının ortasına düştüğünde, DPI'dan bağımsız grafik sistemi bulanık veya yarı saydam kenarlar gibi işleme yapıları oluşturabilir. WPF'nin önceki sürümlerinde bu servis talebinin ele alınaması için piksel tutturulması da yer aldı. Silverlight 2, kenarların tüm piksel sınırlarına düşmesi için öğeleri taşımanın başka bir yolu olan düzen yuvarlama ile tanıtıldı. WPF artık <xref:System.Windows.FrameworkElement.UseLayoutRounding%2A> ekli özellik ile düzen <xref:System.Windows.FrameworkElement>yuvarlama destekler.

- Önbelleğe Alınmış Kompozisyon

  Yeni <xref:System.Windows.Media.BitmapCache> ve <xref:System.Windows.Media.BitmapCacheBrush> sınıfları kullanarak, görsel ağacın karmaşık bir bölümünü bit eşlemi olarak önbelleğe alabilir ve işleme süresini büyük ölçüde artırabilirsiniz. Bit eşlemi fare tıklamaları gibi kullanıcı girişine yanıt vermeye devam eder ve bunu herhangi bir fırça gibi diğer öğelere boyayabilirsiniz.

- Pixel Shader 3 Desteği

  WPF 4, Pixel Shader (PS) sürüm 3.0 kullanarak uygulamaların efekt yazmasına izin vererek WPF 3.5 SP1'de tanıtılan <xref:System.Windows.Media.Effects.ShaderEffect> desteğin üzerine kuruludur. PS 3.0 shader modeli, desteklenen donanım üzerinde daha fazla etki sağlayan PS 2.0'dan daha gelişmiştir.

- Kolaylaştırıcı İşlevler

  Animasyonları kolaylaştırma işlevleriyle büyütebilirsiniz, bu da animasyonların davranışı üzerinde ek denetim sağlar. Örneğin, animasyona yaylı bir davranış vermek için animasyona bir <xref:System.Windows.Media.Animation.ElasticEase> animasyon uygulayabilirsiniz. Daha fazla bilgi için ad <xref:System.Windows.Media.Animation> alanındaki kolaylaştırma türlerine bakın.

<a name="graphics_and_rendering"></a>

## <a name="graphics-and-rendering"></a>Grafik ve Görüntüleme

WPF, yüksek kaliteli 2B grafikler için destek içerir. İşlevsellik fırçalar, geometriler, görüntüler, şekiller ve dönüşümler içerir. Daha fazla bilgi için [Bkz. Grafik.](graphics.md) Grafik öğelerinin işlenmesi sınıfa <xref:System.Windows.Media.Visual> dayanır. Ekrandaki görsel nesnelerin yapısı görsel ağaç tarafından tanımlanır. Daha fazla bilgi için [WPF Grafik Oluşturma Genel Bakış'a](wpf-graphics-rendering-overview.md)bakın.

### <a name="2d-shapes"></a>2B Şekiller

WPF, aşağıdaki resimde gösterildiği gibi dikdörtgenler ve elipsler gibi yaygın olarak kullanılan, vektör çizimli 2B şekillerden oluşan bir kitaplık sağlar.

![Elipsleri ve dikdörtgenleri gösteren diyagram.](./media/index/two-deminsional-shapes-ellipses-rectangles.png)

Bu içsel WPF şekilleri sadece şekiller değildir: klavye ve fare girişi içeren en yaygın denetimlerden beklediğiniz özelliklerin çoğunu uygulayan programlanabilir öğelerdir. Aşağıdaki örnek, bir <xref:System.Windows.UIElement.MouseUp> <xref:System.Windows.Shapes.Ellipse> öğeyi tıklatarak yükseltilen olayın nasıl işleyeceğini gösterir.

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

Aşağıdaki resimde önceki [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] biçimlendirme ve kod arkası çıktısı gösterilmektedir.

!["Elipsi tıklattın!" yazan bir mesaj kutusu](./media/index/messagebox-text-output.png)

Daha fazla bilgi için [WPF'ye Genel Bakış'ta Şekiller ve Temel Çizim'e](shapes-and-basic-drawing-in-wpf-overview.md)bakın. Bir tanıtım örneği için [Şekil Elemanları Örneği'ne](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ShapeElements)bakın.

### <a name="2d-geometries"></a>2B Geometriler

WPF'nin sağladığı 2B şekiller yeterli olmadığında, kendi şekillerinizi oluşturmak için geometriler ve yollar için WPF desteğini kullanabilirsiniz. Aşağıdaki resimde, çizim fırçası olarak şekiller oluşturmak ve diğer WPF öğelerini kesmek için geometrileri nasıl kullanabileceğiniz gösterilmektedir.

![Şekiller oluşturmak için geometrileri nasıl kullanabileceğinizi gösteren ekran görüntüsü.](./media/index/use-geometries-create-shapes.png)

Daha fazla bilgi için [Geometriye Genel Bakış'a](geometry-overview.md)bakın. Bir tanıtım örneği için [Geometriler Örneği'ne](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Geometry)bakın.

### <a name="2d-effects"></a>2B Efektler

WPF, çeşitli efektler oluşturmak için kullanabileceğiniz 2B sınıflardan oluşan bir kitaplık sağlar. WPF'nin 2B görüntüleme özelliği, degradelere, bit eşlemlere, çizimlere ve videolara sahip öğeleri boyama [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] olanağı sağlar; ve döndürme, ölçekleme ve eğrilme kullanarak onları işlemek için. Aşağıdaki resimde WPF fırçaları kullanarak elde edebilirsiniz birçok etkileri bir örnek verir.

![Farklı WPF fırçalarını ve boya elemanlarını gösteren çizim.](./media/index/brushes-paint-elements.png)

Daha fazla bilgi için [WPF Fırçalar Genel Bakış'a](wpf-brushes-overview.md)bakın. Bir tanıtım örneği için [Fırçalar Örneği'ne](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Brushes)bakın.

<a name="rendering"></a>

## <a name="3d-rendering"></a>3D Görüntüleme

WPF, [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]daha heyecan verici düzen ve veri görselleştirme oluşturmak için WPF'de 2B grafik desteğiyle bütünleşen bir dizi 3B görüntüleme özelliği sağlar. Spektrumun bir ucunda, WPF 2B görüntüleri aşağıdaki resimde gösterdiği 3B şekillerin yüzeylerine oluşturmanıza olanak tanır.

![Farklı dokulara sahip 3B şekilleri gösteren bir örneğin ekran görüntüsü.](./media/index/visual-three-dimensional-shape.png)

Daha fazla bilgi için [3B Grafik Genel Bakışı'na](3-d-graphics-overview.md)bakın. Bir tanıtım örneği için [3B Katı Numunesi'ne](https://go.microsoft.com/fwlink/?LinkID=159964)bakın.

<a name="animation"></a>

## <a name="animation"></a>Animasyon

Denetimlerin ve öğelerin büyümesini, sallanmasını, dönmesini ve solmasını sağlamak için animasyonu kullanın; ve ilginç sayfa geçişleri oluşturmak ve daha fazlası. WPF çoğu özelliği animasyona reanimasyon alabilmenizi sağladığından, yalnızca çoğu WPF nesnesini canlandırmakla kullanabilirsiniz, ayrıca oluşturduğunuz özel nesneleri canlandırmak için WPF'yi de kullanabilirsiniz.

![Animasyonlu küpün ekran görüntüsü.](./media/index/animate-custom-objects.png)

Daha fazla bilgi için [Animasyona Genel Bakış'a](animation-overview.md)bakın. Tanıtım örneği için [Animasyon Örnek Galerisi'ne](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/AnimationExamples)bakın.

<a name="media"></a>

## <a name="media"></a>Medya

Görüntüler, video ve ses, bilgi ve kullanıcı deneyimlerini aktarmanın medya açısından zengin yollarıdır.

### <a name="images"></a>Görüntüler

Simgeleri, arka planlar ve hatta animasyonların parçalarını içeren görüntüler çoğu uygulamanın temel parçasıdır. Sık sık görüntüleri kullanmanız gerektiğinden, WPF onlarla çeşitli şekillerde çalışma yeteneğini ortaya çıkarır. Aşağıdaki resimde bu yollardan yalnızca biri gösterilmektedir.

![Stil örnek ekran görüntüsü](../controls/./media/stylingintro-eventtriggers.png "StylingIntro_EventTriggers")

Daha fazla bilgi için [Görüntülemegenel bakış](imaging-overview.md)bilgisine bakın.

### <a name="video-and-audio"></a>Video ve Ses

WPF grafik yetenekleri bir temel özelliği video ve ses içeren multimedya ile çalışmak için yerel destek sağlamaktır. Aşağıdaki örnek, bir ortam oynatıcısının uygulamaya nasıl yerleştirilebildiğini gösterir.

```xaml
<MediaElement Source="media\numbers.wmv" Width="450" Height="250" />
```

<xref:System.Windows.Controls.MediaElement>hem video hem de ses oynatma yeteneğine sahiptir ve özel Kullanıcı II'lerin kolay oluşturulmasına izin verecek kadar genişletilebilir.

Daha fazla bilgi için [Multimedyagenel bakış](multimedia-overview.md)ına bakın.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Media>
- <xref:System.Windows.Media.Animation>
- <xref:System.Windows.Media.Media3D>
- [2B Grafikleri ve Görüntüleme](../advanced/optimizing-performance-2d-graphics-and-imaging.md)
- [WPF Genel Bakışı İçinde Şekiller ve Temel Çizimler](shapes-and-basic-drawing-in-wpf-overview.md)
- [Düz Renkler ve Gradyanlar ile Boyamaya Genel Bakış](painting-with-solid-colors-and-gradients-overview.md)
- [Görüntüler, Çizimler ve Görsellerle Boyama](painting-with-images-drawings-and-visuals.md)
- [Animasyon ve Zamanlama ile İlgili Nasıl Yapılır Konuları](animation-and-timing-how-to-topics.md)
- [3D Grafiklere Genel Bakış](3-d-graphics-overview.md)
- [Multimedyaya Genel Bakış](multimedia-overview.md)
