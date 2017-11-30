---
title: Grafikler ve Multimedya
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "30"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: e212de5f1f92a2a797da7f2534d28ff8b6dbdd12
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="graphics-and-multimedia"></a>Grafikler ve Multimedya
<a name="introduction"></a>
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]multimedya, vektör grafikleri, animasyon ve ilginç kullanıcı arabirimleri ve içerik oluşturmada geliştiricilere kolaylaşır içerik oluşturma için destek sağlar. Kullanarak [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)], vektör grafikleri veya karmaşık bir animasyon oluşturabilir ve ortam uygulamalarınıza tümleştirebilirsiniz.  
  
 Bu konu, grafik, animasyon ve ortam özelliklerini tanıtır [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], grafik, geçiş efektleri, ses ve video uygulamalarınıza eklemek etkinleştirin.  
  
> [!NOTE]
>  Bir Windows hizmetinde WPF türlerini kullanarak kesinlikle önerilmez. Bir Windows hizmetinde WPF türleri kullanmayı denerseniz, hizmet beklendiği gibi çalışmayabilir.   
  
<a name="whats_new_with_graphics_and_multimedia_in_wpf_4"></a>   
## <a name="whats-new-with-graphics-and-multimedia-in-wpf-4"></a>Grafiklerle ve WPF 4 multimedya yenilikler  
 Grafikler ve animasyon ilgili birkaç değişiklik yapılmıştır.  
  
-   Düzen yuvarlama  
  
     DPI bağımsız grafik sistemi nesnenin bir kenarı piksel aygıtının ortasında düştüğünde bulanık veya yarı saydam kenarlar gibi işleme yapılarını oluşturabilirsiniz. WPF önceki sürümleri, bu durumda işlemeye yardımcı olmak için piksel tutturma dahil. Silverlight 2 düzeni yuvarlama, böylece Kenarları piksel sınırlarının tamamına kalan öğeleri taşımak için başka bir yol olduğu sunmuştur. WPF ile yuvarlama düzeni artık destekliyor <xref:System.Windows.FrameworkElement.UseLayoutRounding%2A> üzerinde ekli özellik <xref:System.Windows.FrameworkElement>.  
  
-   Önbelleğe alınan oluşturma  
  
     Yeni kullanarak <xref:System.Windows.Media.BitmapCache> ve <xref:System.Windows.Media.BitmapCacheBrush> sınıfları, bit eşlem olarak görsel ağaç karmaşık bir kısmını önbelleğe ve işleme süresini önemli ölçüde artırmak. Bit eşlem fare tıklamaları gibi kullanıcı girişine yanıt vermeyi kalır ve herhangi bir fırça gibi diğer öğeler üzerine boyamak.  
  
-   Piksel gölgelendirici 3 desteği  
  
     WPF 4 derlemeler üstünde <xref:System.Windows.Media.Effects.ShaderEffect> piksel gölgelendirici (PS) sürüm 3.0 kullanarak etkileri yazmak uygulamaları vererek WPF 3.5 SP1'de sunulan destek. PS 3.0 gölgelendirici modeli desteklenen donanım daha da fazla etkileri izin veren PS 2.0 daha karmaşıktır.  
  
-   Kolaylaştırıcı İşlevler  
  
     Animasyon davranışını üzerinde ek denetime hareket hızı işlevleri ile animasyonları geliştirebilirsiniz. Örneğin, geçerli bir <xref:System.Windows.Media.Animation.ElasticEase> animasyonun animasyonun esnek bir davranış vermek için. Daha fazla bilgi için bkz: hareket hızı türlerinde <xref:System.Windows.Media.Animation> ad alanı.  
  
<a name="graphics_and_rendering"></a>   
## <a name="graphics-and-rendering"></a>Grafikler ve işleme  
 WPF yüksek kaliteli 2B grafik için destek içerir. İşlev Fırçalar, geometri, görüntüler, şekiller ve dönüşümler içerir. Daha fazla bilgi için bkz: [grafik](../../../../docs/framework/wpf/graphics-multimedia/graphics.md). Grafik öğelerin işlenmesi dayanır <xref:System.Windows.Media.Visual> sınıfı. Ekranında visual nesnelerin yapısı görsel ağaç tarafından tanımlanır. Daha fazla bilgi için bkz: [WPF Grafik işleme genel bakış](../../../../docs/framework/wpf/graphics-multimedia/wpf-graphics-rendering-overview.md).  
  
### <a name="2-d-shapes"></a>2B şekiller  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]yaygın olarak kullanılan, vektör çizilmiş kitaplığını sağlar [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] dikdörtgenler ve aşağıda gösterilmiştir elipsler gibi şekiller.  
  
 ![Elipsler ve dikdörtgenler](../../../../docs/framework/wpf/graphics-multimedia/media/wpfintrofigure4.PNG "WPFIntroFigure4")  
  
 Bu iç [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] şekilleri yalnızca şekil değil: Bunlar, klavye ve fare girişi içeren, en sık kullanılan denetimlerden beklediğiniz özelliklerin çoğunu uygulayan programlanabilir öğelerdir. Aşağıdaki örnekte nasıl işleneceğini gösterir <xref:System.Windows.UIElement.MouseUp> olay gerçekleşti tıklayarak bir <xref:System.Windows.Shapes.Ellipse> öğesi.  
  
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
  
 Aşağıdaki şekilde önceki çıktı gösterilmiştir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] biçimlendirme ve arka plan kodu.  
  
 ![Metinle "elips &#33; tıkladığınız" penceresi ] (../../../../docs/framework/wpf/graphics-multimedia/media/wpfintrofigure12.png "WPFIntroFigure12")  
  
 Daha fazla bilgi için bkz: [şekilleri ve WPF genel bakış temel çizim](../../../../docs/framework/wpf/graphics-multimedia/shapes-and-basic-drawing-in-wpf-overview.md). Tanıtıcı bir örnek için bkz: [şekil öğeleri örneği](http://go.microsoft.com/fwlink/?LinkID=160037).  
  
### <a name="2-d-geometries"></a>2-D geometri  
 Zaman [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] şekiller [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] sağlar kullanabileceğiniz yeterli [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] geometri ve kendi oluşturmak için yollar için desteği. Aşağıdaki çizimde, şekiller çizme fırça olarak oluşturmak ve diğer küçük geometri nasıl kullanabileceğinizi gösterir [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] öğeleri.  
  
 ![Bir yol çeşitli kullanımları](../../../../docs/framework/wpf/graphics-multimedia/media/wpfintrofigure5.PNG "WPFIntroFigure5")  
  
 Daha fazla bilgi için bkz: [geometrisi](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md). Tanıtıcı bir örnek için bkz: [geometri örneği](http://go.microsoft.com/fwlink/?LinkID=159989).  
  
### <a name="2-d-effects"></a>2B efektler  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]kitaplığını sağlar [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] çeşitli efektler oluşturmak için kullanabileceğiniz sınıfları. [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] İşleme yeteneğini [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] boyamak olanağı sağlar [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] gradyan, bit eşlemler, çizimler ve videolar; olan öğenin ve döndürme, kullanarak işlemek için ölçekleme ve eğriltme. Aşağıdaki çizim bir örnek kullanarak elde edebileceğiniz birçok etkileri verir [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] Fırçalar.  
  
 ![Farklı fırçalar çizimi](../../../../docs/framework/wpf/graphics-multimedia/media/wpfintrofigure6.PNG "WPFIntroFigure6")  
  
 Daha fazla bilgi için bkz: [WPF Fırçaları Genel Bakış](../../../../docs/framework/wpf/graphics-multimedia/wpf-brushes-overview.md). Tanıtıcı bir örnek için bkz: [Fırçalar örnek](http://go.microsoft.com/fwlink/?LinkID=159973).  
  
<a name="rendering"></a>   
## <a name="3-d-rendering"></a>3B işleme  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]bir dizi sağlar [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] tümleştirileceğini işleme yeteneklerini [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] grafik desteği [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] daha heyecan verici bir düzen oluşturmak için sırayla [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]ve veri görselleştirme. Spektrumun bir ucunda [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] işlenecek sağlar [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] yüzeyleriyle görüntüleri [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] şekiller, aşağıdaki çizimde gösterilmektedir.  
  
 ![Visual3D örnek ekran görüntüsü](../../../../docs/framework/wpf/graphics-multimedia/media/wpfintrofigure13.png "WPFIntroFigure13")  
  
 Daha fazla bilgi için bkz: [3-b grafiklere genel bakış](../../../../docs/framework/wpf/graphics-multimedia/3-d-graphics-overview.md). Tanıtıcı bir örnek için bkz: [3-b düz çizgi örneği](http://go.microsoft.com/fwlink/?LinkID=159964).  
  
<a name="animation"></a>   
## <a name="animation"></a>Animasyon  
 Animasyon denetimleri ve büyüme, sallama, döndürme ve silinerek öğeleri yapmak için kullanın; ve ilginç sayfa geçişleri ve daha fazlasını oluşturun. Çünkü [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] özelliklerinin çoğu, yalnızca animasyon eklemek için şunları yapabilirsiniz etkinleştirir, çoğu hareketli hale getirmeyi [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] nesnelerini de kullanabilir [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] oluşturduğunuz özel nesnelere animasyon uygulamak.  
  
 ![Animasyonlu bir küpü görüntülerini](../../../../docs/framework/wpf/graphics-multimedia/media/wpfintrofigure7.png "WPFIntroFigure7")  
  
 Daha fazla bilgi için bkz: [animasyon genel bakış](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md). Tanıtıcı bir örnek için bkz: [animasyon örnek Galerisi](http://go.microsoft.com/fwlink/?LinkID=159969).  
  
<a name="media"></a>   
## <a name="media"></a>Medya  
 Resim, video ve ses bilgileri ve kullanıcı deneyimlerini aktaran, medya zengin yöntemleridir.  
  
### <a name="images"></a>Görüntüler  
 Simgeler, arka planlar ve hatta animasyonların bölümleri içerir, görüntüleri çoğu uygulamayı çekirdek parçasıdır. Sık görüntüleri kullanmak gerektiğinden [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] çeşitli şekillerde onlarla çalışma olanağı sunar. Aşağıda bu yollardan biri gösterilmektedir.  
  
 ![Stil örnek ekran görüntüsü](../../../../docs/framework/wpf/controls/media/stylingintro-eventtriggers.png "StylingIntro_EventTriggers")  
  
 Daha fazla bilgi için bkz: [Imaging genel bakış](../../../../docs/framework/wpf/graphics-multimedia/imaging-overview.md).  
  
### <a name="video-and-audio"></a>Video ve ses  
 Grafik özelliklerini çekirdek özelliği [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] video ve ses içeren çoklu ortam ile çalışmak için yerel destek sağlar. Aşağıdaki örnek bir medya oynatıcı bir uygulamaya eklemek nasıl gösterir.  
  
```xaml  
<MediaElement Source="media\numbers.wmv" Width="450" Height="250" />  
```  
  
 <xref:System.Windows.Controls.MediaElement>video ve ses çalma yeteneğine sahiptir ve özel kolay oluşturulmasına izin için Genişletilebilir [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)].  
  
 Daha fazla bilgi için bkz: [multimedya genel bakış](../../../../docs/framework/wpf/graphics-multimedia/multimedia-overview.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Media>  
 <xref:System.Windows.Media.Animation>  
 <xref:System.Windows.Media.Media3D>  
 [2B grafik ve görüntü](../../../../docs/framework/wpf/advanced/optimizing-performance-2d-graphics-and-imaging.md)  
 [Şekiller ve temel çizim WPF genel bakış](../../../../docs/framework/wpf/graphics-multimedia/shapes-and-basic-drawing-in-wpf-overview.md)  
 [Boyama düz renklerle ve gradyan genel bakış](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md)  
 [Görüntüleri, çizimler ve görsellerle boyama](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md)  
 [Animasyon ve zamanlama](http://msdn.microsoft.com/en-us/7d83765b-d5ae-41b1-b423-80206e1124aa)  
 [3B grafik](http://msdn.microsoft.com/en-us/565c1f3c-235b-47de-b05b-3b53ed63f1b8)  
 [Multimedya](http://msdn.microsoft.com/en-us/44a8dcd0-80cb-4db0-a222-87cde68c2fac)
