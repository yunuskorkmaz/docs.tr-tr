---
title: Grafikler ve Multimedya
ms.date: 03/30/2017
dev_langs:
  - csharp
  - vb
helpviewer_keywords:
  - 'media [WPF], features'
  - 'video effects [WPF]'
  - 'sound effects [WPF]'
  - 'animation [WPF], features'
  - 'graphics features [WPF]'
  - 'transition effects [WPF]'
ms.assetid: 1817d9dc-3d6c-46cb-afc8-63b0bae35e37
---
# <a name="graphics-and-multimedia"></a>Grafikler ve Multimedya
<a name="introduction"></a>
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] multimedya, vektör grafikleri, animasyon ve ilgi çekici kullanıcı arabirimleri ve içerik oluşturmak geliştiriciler için kolaylaştıran, içerik oluşturma için destek sağlar. Kullanarak [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)], vektör grafik veya karmaşık animasyonları oluşturun ve medya uygulamalarınızla tümleştirin.  
  
 Bu konuda, grafik, animasyon ve medya özelliklerini tanıtır [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], grafik, geçiş efektleri, ses ve video uygulamalarınıza ekleyin etkinleştirin.  
  
> [!NOTE]
>  WPF türlerini kullanarak bir Windows hizmetinde kesinlikle önerilmez. Bir Windows hizmetinde WPF türleri kullanmayı denerseniz, hizmetin beklendiği gibi çalışmayabilir.   
  
<a name="whats_new_with_graphics_and_multimedia_in_wpf_4"></a>   
## <a name="whats-new-with-graphics-and-multimedia-in-wpf-4"></a>Grafikler ve multimedya WPF 4 ile yenilikler  
 Grafikler ve animasyon ilgili birkaç değişiklik yapılmıştır.  
  
-   Düzen yuvarlama  
  
     Bir nesnenin kenar ortasında bir pixel cihazda düştüğünde DPI bağımsız grafik sistemi bulanık veya yarı saydam kenarları gibi işleme yapılarını oluşturabilirsiniz. WPF önceki sürümleri, bu durumda işlemeye yardımcı olmak için piksel yaslamayı dahil. Silverlight 2 Düzen yuvarlama, tüm piksel sınırlardaki kenarları kalan öğeleri taşımak, başka bir yolu olan sunulmuştur. WPF düzen ile yuvarlama artık destekliyor <xref:System.Windows.FrameworkElement.UseLayoutRounding%2A> üzerinde ekli özellik <xref:System.Windows.FrameworkElement>.  
  
-   Önbelleğe alınan oluşturma  
  
     Yeni kullanarak <xref:System.Windows.Media.BitmapCache> ve <xref:System.Windows.Media.BitmapCacheBrush> sınıfları, bit eşlem olarak görsel ağacı karmaşık bir kısmını önbelleğe ve işleme süresini önemli ölçüde geliştirmek. Bit eşlem fare tıklama gibi kullanıcı girişine yanıt olarak kalır ve herhangi bir fırça gibi diğer öğeler üzerine boyama.  
  
-   Piksel gölgelendirici 3 desteği  
  
     WPF 4 derlemeleri üst kısmındaki <xref:System.Windows.Media.Effects.ShaderEffect> etkileri piksel gölgelendiricisi (PS) sürüm 3.0 kullanarak yazmak uygulamaları sağlayarak WPF 3.5 SP1'de sunulan destek. PS 3.0 gölgelendirici modeli desteklenen donanım üzerinde daha fazla efekte sağlayan PS 2.0 daha karmaşıktır.  
  
-   Kolaylaştırıcı İşlevler  
  
     Animasyon davranışları üzerinde ek denetim size kolaylaştırıcı işlevler animasyonlarla geliştirebilirsiniz. Örneğin, geçerli bir <xref:System.Windows.Media.Animation.ElasticEase> animasyon esnek bir davranış sağlamak için bir animasyon için. Kolaylaştırıcı türlerinde daha fazla bilgi için bkz. <xref:System.Windows.Media.Animation> ad alanı.  
  
<a name="graphics_and_rendering"></a>   
## <a name="graphics-and-rendering"></a>Grafik ve oluşturma  
 WPF, yüksek kaliteli 2B grafikler için destek içerir. Fırçalar, geometri, resimler, şekiller ve dönüşümler işlevleri içerir. Daha fazla bilgi için [grafik](graphics.md). Grafik öğelerin işlenmesi dayanır <xref:System.Windows.Media.Visual> sınıfı. Görsel nesneler ekranında yapısını görsel ağacını tarafından tanımlanır. Daha fazla bilgi için [WPF Grafik işlemeye genel bakış](wpf-graphics-rendering-overview.md).  
  
### <a name="2-d-shapes"></a>2B şekiller  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] yaygın olarak kullanılan, vektör çizilmiş bir kitaplık sağlar [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] dikdörtgenler ve elipsler aşağıdaki çizimin gösterdiği gibi şekiller.  
  
 ![Elips ve dikdörtgen](./media/wpfintrofigure4.PNG "WPFIntroFigure4")  
  
 Bu iç [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] şekilleri yalnızca şekil değil: Bunlar birçok klavye ve fare girişi içeren, en yaygın denetimlerden beklediğiniz özelliği uygulayan programlanabilir öğeleridir. Aşağıdaki örnek nasıl işleneceğini gösterir <xref:System.Windows.UIElement.MouseUp> tıklayarak harekete geçirilen olay bir <xref:System.Windows.Shapes.Ellipse> öğesi.  
  
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
  
 Önceki çıktı aşağıda gösterilmiştir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] işaretleme ve arka plan kod.  
  
 ![Metin içeren bir pencere "elips tıkladığınız&#33;"](./media/wpfintrofigure12.png "WPFIntroFigure12")  
  
 Daha fazla bilgi için [şekiller ve temel çizimlere WPF genel bakışında](shapes-and-basic-drawing-in-wpf-overview.md). Tanıtıcı bir örnek için bkz. [şekil öğeleri örneği](https://go.microsoft.com/fwlink/?LinkID=160037).  
  
### <a name="2-d-geometries"></a>2B geometri  
 Zaman [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] şekiller [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] sağlar kullanabileceğiniz yeterli [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] geometrileri ve kendi yolları için destek. Aşağıdaki çizimde, çizim Fırçası gibi şekiller, oluşturmak ve diğeri küçük resim için geometri nasıl kullanabileceğinizi gösterir [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] öğeleri.  
  
 ![Bir yol çeşitli kullanımları](./media/wpfintrofigure5.PNG "WPFIntroFigure5")  
  
 Daha fazla bilgi için [geometrisi](geometry-overview.md). Tanıtıcı bir örnek için bkz. [geometri örneği](https://go.microsoft.com/fwlink/?LinkID=159989).  
  
### <a name="2-d-effects"></a>2B efektler  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] bir kitaplık sağlar [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] sınıflar etkileri çeşitli oluşturmak için kullanabilirsiniz. [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] İşleme yeteneğini [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] boyama olanak tanıyor [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] gradyan, bit eşlemler, çizimler ve videoları; olan öğeler ve döndürme, kullanarak işlemek için ölçeklendirme ve eğriltme. Aşağıdaki resimde bir örnek kullanarak elde edebileceğiniz birçok etkileri verir [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] Fırçalar.  
  
 ![Farklı fırçalar gösterimi](./media/wpfintrofigure6.PNG "WPFIntroFigure6")  
  
 Daha fazla bilgi için [WPF fırçalarına genel bakış](wpf-brushes-overview.md). Tanıtıcı bir örnek için bkz. [Fırçalar örnek](https://go.microsoft.com/fwlink/?LinkID=159973).  
  
<a name="rendering"></a>   
## <a name="3-d-rendering"></a>3B işleme  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] takımına [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] tümleştirin işleme özellikleri [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] grafikler, destek [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] daha heyecan verici düzen oluşturmak için sırayla [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]ve veri görselleştirmesi. Spektrumun ucunda [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] işleme sayesinde [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] görüntüleri yüzeyleriyle [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] şekiller, aşağıdaki çizimde gösterilmektedir.  
  
 ![Visual3D örnek ekran görüntüsünde](./media/wpfintrofigure13.png "WPFIntroFigure13")  
  
 Daha fazla bilgi için [3B Grafiklere Genel Bakış](3-d-graphics-overview.md). Tanıtıcı bir örnek için bkz. [3-b düz çizgi örneği](https://go.microsoft.com/fwlink/?LinkID=159964).  
  
<a name="animation"></a>   
## <a name="animation"></a>Animasyon  
 Animasyon denetimleri ve büyütün, sallayın, çalıştırın ve Soluklaştır öğeleri yapmak için kullanın. ve ilgi çekici sayfa geçişleri ve daha fazlasını oluşturun. Çünkü [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] etkinleştirir, özelliklerin çoğu, yalnızca animasyon uygulamak için birçok animasyon [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] nesnelerini de kullanabilirsiniz [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] oluşturduğunuz özel nesneleri animasyon uygulamak için.  
  
 ![Animasyonlu bir küp görüntülerini](./media/wpfintrofigure7.png "WPFIntroFigure7")  
  
 Daha fazla bilgi için [animasyona genel bakış](animation-overview.md). Tanıtıcı bir örnek için bkz. [animasyon örnek Galerisi](https://go.microsoft.com/fwlink/?LinkID=159969).  
  
<a name="media"></a>   
## <a name="media"></a>Medya  
 Görüntü, video ve ses bilgileri ve kullanıcı deneyimlerini yaygınlaşmıştır, zengin medya yöntemleridir.  
  
### <a name="images"></a>Görüntüler  
 Görüntüler, simgeler, arka plan ve hatta animasyonları parçalarını içeren çoğu uygulamalar çekirdek parçasıdır. Sık görüntüleri kullanmanız gerekir çünkü [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] çeşitli yollarla onlarla çalışma olanağı sunar. Bu yollardan yalnızca biri aşağıda gösterilmiştir.  
  
 ![Stil örnek ekran görüntüsünde](../controls/./media/stylingintro-eventtriggers.png "StylingIntro_EventTriggers")  
  
 Daha fazla bilgi için [Imaging genel bakış](imaging-overview.md).  
  
### <a name="video-and-audio"></a>Video ve ses  
 Çekirdek özelliği, grafik yeteneklerini [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] video ve ses içeren çoklu ortam ile çalışmak için yerel destek sağlar. Aşağıdaki örnek bir medya yürütücüsü bir uygulamaya nasıl ekleneceğini gösterir.  
  
```xaml  
<MediaElement Source="media\numbers.wmv" Width="450" Height="250" />  
```  
  
 <xref:System.Windows.Controls.MediaElement> video ve ses çalabilir ve özel bir kolayca oluşturulmasını izin vermek için Genişletilebilir [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)].  
  
 Daha fazla bilgi için [multimedya genel bakış](multimedia-overview.md).  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Windows.Media>
- <xref:System.Windows.Media.Animation>
- <xref:System.Windows.Media.Media3D>
- [2B Grafikleri ve Görüntüleme](../advanced/optimizing-performance-2d-graphics-and-imaging.md)
- [WPF’de Şekiller ve Temel Çizimlere Genel Bakış](shapes-and-basic-drawing-in-wpf-overview.md)
- [Düz Renkler ve Gradyanlar ile Boyamaya Genel Bakış](painting-with-solid-colors-and-gradients-overview.md)
- [Görüntüler, Çizimler ve Görsellerle Boyama](painting-with-images-drawings-and-visuals.md)
- [Animasyon ve zamanlama ile ilgili nasıl yapılır konuları](animation-and-timing-how-to-topics.md)
- [3B Grafiklere Genel Bakış](3-d-graphics-overview.md)
- [Multimedyaya Genel Bakış](multimedia-overview.md)
