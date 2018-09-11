---
title: Düzen
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WPF layout system [WPF]
- controls [WPF], layout system
- layout system [WPF]
ms.assetid: 3eecdced-3623-403a-a077-7595453a9221
ms.openlocfilehash: 869780f2b6a625923ce869bcaafbbd2319f6cb23
ms.sourcegitcommit: 67de6cb5dd66a19f2180ba7e4d7aecc697f8a963
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2018
ms.locfileid: "44339519"
---
# <a name="layout"></a>Düzen
Bu konu başlığı altında açıklanır [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] düzen sistemi. Düzen hesaplamalar nasıl ve ne zaman ortaya anlamak, kullanıcı arabirimi oluşturmak için gerekli [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
 Bu konu aşağıdaki bölümleri içermektedir:  
  
-   [Sınırlayıcı kutular öğesi](#LayoutSystem_BoundingBox)  
  
-   [Düzen sistemi](#LayoutSystem_Overview)  
  
-   [Ölçme ve alt öğeleri düzenleme](#LayoutSystem_Measure_Arrange)  
  
-   [Panel öğeleri ve özel düzen davranışları](#LayoutSystem_PanelsCustom)  
  
-   [Düzen performansla ilgili önemli noktalar](#LayoutSystem_Performance)  
  
-   [Alt piksel işleme ve düzeni yuvarlama](#LayoutSystem_LayoutRounding)  
  
-   [Yenilikler](#LayoutSystem_whatsnext)  
  
<a name="LayoutSystem_BoundingBox"></a>   
## <a name="element-bounding-boxes"></a>Sınırlayıcı kutular öğesi  
 Düzende hakkında düşünürken, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], tüm öğeler çevreleyen sınırlayıcı kutunun anlamak önemlidir. Her <xref:System.Windows.FrameworkElement> tüketilen düzeni sistem, düzene yarıklı bir dikdörtgen olarak düşünülebilir. <xref:System.Windows.Controls.Primitives.LayoutInformation> Sınıfı, bir öğenin Düzen ayırma veya yuva sınırları döndürür. Dikdörtgenin boyutu kullanılabilir ekran alanı, kısıtlamalar, Düzen özgü özellikler (örneğin, kenar boşlukları ve doldurma) ve üst bireysel davranışını boyutunu hesaplayarak belirlenir <xref:System.Windows.Controls.Panel> öğesi. Bu veri işleme, düzen sistemi belirli bir tüm alt öğeleri konumunu hesaplayabilirsiniz <xref:System.Windows.Controls.Panel>. Gibi özellikleri boyutlandırma üst öğede tanımlanan unutmamak gerekir bir <xref:System.Windows.Controls.Border>, alt öğelerini etkiler.  
  
 Aşağıdaki çizim basit bir düzen gösterir.  
  
 ![Tipik bir kılavuz, sınırlama kutusu yerleştirilmemiş. ](../../../../docs/framework/wpf/advanced/media/boundingbox1.png "boundingbox1")  
  
 Bu düzen aşağıdaki kullanarak ulaşılabilecek [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].  
  
 [!code-xaml[LayoutInformation#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LayoutInformation/CSharp/Window1.xaml#1)]  
  
 Tek bir <xref:System.Windows.Controls.TextBlock> öğesi içinde barındırılan bir <xref:System.Windows.Controls.Grid>. Metnin sol üst köşesinin yalnızca ilk sütun, için ayrılan alanı doldururken <xref:System.Windows.Controls.TextBlock> gerçekten çok büyük. Herhangi bir sınırlama kutusu <xref:System.Windows.FrameworkElement> kullanılarak alınabilir <xref:System.Windows.Controls.Primitives.LayoutInformation.GetLayoutSlot%2A> yöntemi. Sınırlayıcı kutu için aşağıdaki çizimde <xref:System.Windows.Controls.TextBlock> öğesi.  
  
 ![TextBlock'ın sınırlama kutusu görünür. ](../../../../docs/framework/wpf/advanced/media/boundingbox2.png "boundingbox2")  
  
 Sarı bir dikdörtgen, için ayrılan alanı tarafından gösterilen şekilde <xref:System.Windows.Controls.TextBlock> öğedir göründüğü gerçekten çok büyük. Ek öğeler eklendikçe <xref:System.Windows.Controls.Grid>, bu ayırma daraltabilir veya eklenen öğelerin boyutunu ve türünü bağlı olarak genişletin.  
  
 Düzen yuvasını <xref:System.Windows.Controls.TextBlock> erişimcisine bir <xref:System.Windows.Shapes.Path> kullanarak <xref:System.Windows.Controls.Primitives.LayoutInformation.GetLayoutSlot%2A> yöntemi. Bu teknik, bir öğenin sınırlama kutusu görüntülemek için yararlı olabilir.  
  
 [!code-csharp[LayoutInformation#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LayoutInformation/CSharp/Window1.xaml.cs#2)]
 [!code-vb[LayoutInformation#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/LayoutInformation/VisualBasic/Window1.xaml.vb#2)]  
  
<a name="LayoutSystem_Overview"></a>   
## <a name="the-layout-system"></a>Düzen sistemi  
 En basit şekliyle, düzen, bir öğenin yeniden boyutlandırılmış, konumlandırılmış çizilmiş müşteri adaylarını ve bir özyinelemeli sistemidir. Daha açık belirtmek gerekirse ölçme ve üyelerinin düzenleme işleminin düzeninin açıklandığı bir <xref:System.Windows.Controls.Panel> öğenin <xref:System.Windows.Controls.Panel.Children%2A> koleksiyonu. Düzen yoğunluklu bir işlemdir. Büyük <xref:System.Windows.Controls.Panel.Children%2A> koleksiyonu, yapılmalıdır hesaplamalar büyük sayısı. Karmaşıklık de sunulan tarafından tanımlanan Düzen davranışa göre <xref:System.Windows.Controls.Panel> koleksiyona sahip olan öğe. Görece basit <xref:System.Windows.Controls.Panel>, gibi <xref:System.Windows.Controls.Canvas>, daha karmaşık önemli ölçüde daha iyi performans sağlayabilirsiniz <xref:System.Windows.Controls.Panel>, gibi <xref:System.Windows.Controls.Grid>.  
  
 Her bir alt <xref:System.Windows.UIElement> konumunu değiştirir. yeni bir düzen sistemi geçişi tetikleme olasılığına sahiptir. Bu nedenle, gereksiz çağırma olarak düzen sistemi çağırabilirsiniz olayları kötü uygulama performansı artırabilir anlamak önemlidir. Düzen sistemi çağrıldığında oluşan süreci açıklanmaktadır.  
  
1.  Bir alt <xref:System.Windows.UIElement> çekirdek özellikleri sağlayarak düzen işlemine başlar.  
  
2.  Tanımlanan özelliklerini boyutlandırma <xref:System.Windows.FrameworkElement> , aşağıdaki gibi değerlendirilir <xref:System.Windows.FrameworkElement.Width%2A>, <xref:System.Windows.FrameworkElement.Height%2A>, ve <xref:System.Windows.FrameworkElement.Margin%2A>.  
  
3.  <xref:System.Windows.Controls.Panel>-belirli bir mantıksal uygulandığı gibi <xref:System.Windows.Controls.Dock> yönünü veya yığın <xref:System.Windows.Controls.StackPanel.Orientation%2A>.  
  
4.  Tüm alt ölçüldükten sonra içeriği yerleştirilmiştir.  
  
5.  <xref:System.Windows.Controls.Panel.Children%2A> Koleksiyonu, ekranda çizilir.  
  
6.  İşlemi yeniden ek oluşursa çağrılır <xref:System.Windows.Controls.Panel.Children%2A> koleksiyona eklenen bir <xref:System.Windows.FrameworkElement.LayoutTransform%2A> uygulanan veya <xref:System.Windows.UIElement.UpdateLayout%2A> yöntemi çağrılır.  
  
 Bu işlem ve nasıl çağrılır, aşağıdaki bölümlerde daha ayrıntılı tanımlanır.  
  
<a name="LayoutSystem_Measure_Arrange"></a>   
## <a name="measuring-and-arranging-children"></a>Ölçme ve alt öğeleri düzenleme  
 Düzen sistemi her üyesi için iki geçiş tamamlandıktan <xref:System.Windows.Controls.Panel.Children%2A> koleksiyonu, bir ölçü geçişi ve düzenleme geçişi. Her alt <xref:System.Windows.Controls.Panel> kendi sağlar <xref:System.Windows.FrameworkElement.MeasureOverride%2A> ve <xref:System.Windows.FrameworkElement.ArrangeOverride%2A> kendi özel düzen davranışını elde etmek için yöntemleri.  
  
 Ölçü geçişi sırasında her üyesi <xref:System.Windows.Controls.Panel.Children%2A> koleksiyon değerlendirilir. İşlem çağrısı ile başlar <xref:System.Windows.UIElement.Measure%2A> yöntemi. Bu yöntem, üst uygulama içinde çağrılır <xref:System.Windows.Controls.Panel> öğesi ve düzeni gerçekleşmesi özel olarak çağrılması gerekmez.  
  
 İlk, yerel boyut özelliklerini <xref:System.Windows.UIElement> , aşağıdaki gibi değerlendirilir <xref:System.Windows.UIElement.Clip%2A> ve <xref:System.Windows.UIElement.Visibility%2A>. Bu adlı bir değer üreten `constraintSize` yapan <xref:System.Windows.FrameworkElement.MeasureCore%2A>.  
  
 Çerçeve Özellikleri İkincisi, tanımlanan <xref:System.Windows.FrameworkElement> işlenir, değerini etkiler `constraintSize`. Bu özellikler genellikle arka plandaki boyutlandırma özelliklerini açıklayan <xref:System.Windows.UIElement>, gibi kendi <xref:System.Windows.FrameworkElement.Height%2A>, <xref:System.Windows.FrameworkElement.Width%2A>, <xref:System.Windows.FrameworkElement.Margin%2A>, ve <xref:System.Windows.FrameworkElement.Style%2A>. Bu özelliklerin her biri, öğe görüntülemek gerekli olan bir alanı değiştirebilirsiniz. <xref:System.Windows.FrameworkElement.MeasureOverride%2A> sonra çağrılır `constraintSize` bir parametre olarak.  
  
> [!NOTE]
>  Özellikleri arasında bir fark <xref:System.Windows.FrameworkElement.Height%2A> ve <xref:System.Windows.FrameworkElement.Width%2A> ve <xref:System.Windows.FrameworkElement.ActualHeight%2A> ve <xref:System.Windows.FrameworkElement.ActualWidth%2A>. Örneğin, <xref:System.Windows.FrameworkElement.ActualHeight%2A> diğer yükseklik girişler ve düzen sistemi dayanan bir hesaplanan değer bir özelliktir. Değer bir gerçek işleme geçişte, temel düzen sistemi kendisi tarafından ayarlanır ve bu nedenle biraz özellikleri kümesi değerini gibi öteleme <xref:System.Windows.FrameworkElement.Height%2A>, giriş değiştirme temeli olan.  
>   
>  Çünkü <xref:System.Windows.FrameworkElement.ActualHeight%2A> bilmeniz gereken hesaplanmış bir değer olan birden çok da olabilir veya artımlı bildirilen için çeşitli işlemleri sonucunda düzen sistemi tarafından değiştirir. Düzen sistemi alt öğeleri, üst öğenin vb. kısıtlamaları için gerekli ölçü alanı hesaplanıyor.  
  
 Ölçü geçişi nihai amacı olduğunu belirlemek için alt kendi <xref:System.Windows.UIElement.DesiredSize%2A>, oluştuğu sırasında <xref:System.Windows.FrameworkElement.MeasureCore%2A> çağırın. <xref:System.Windows.UIElement.DesiredSize%2A> Tarafından depolanan değer <xref:System.Windows.UIElement.Measure%2A> içerik düzenleme geçişi sırasında kullanılacak.  
  
 Düzenleme geçişi çağrısı ile başlayan <xref:System.Windows.UIElement.Arrange%2A> yöntemi. Üst düzenleme geçişi sırasında <xref:System.Windows.Controls.Panel> öğesi alt sınırlarını temsil eden bir dikdörtgen oluşturur. Bu değer gönderilirse <xref:System.Windows.FrameworkElement.ArrangeCore%2A> işleme için yöntemi.  
  
 <xref:System.Windows.FrameworkElement.ArrangeCore%2A> Yöntemi değerlendirir <xref:System.Windows.UIElement.DesiredSize%2A> alt ve öğenin işlenmiş boyutunu etkileyebilecek herhangi ek bir kenar boşlukları değerlendirir. <xref:System.Windows.FrameworkElement.ArrangeCore%2A> oluşturur bir `arrangeSize`, için geçirilen <xref:System.Windows.FrameworkElement.ArrangeOverride%2A> yöntemi <xref:System.Windows.Controls.Panel> bir parametre olarak. <xref:System.Windows.FrameworkElement.ArrangeOverride%2A> oluşturur `finalSize` alt. Son olarak, <xref:System.Windows.FrameworkElement.ArrangeCore%2A> yöntemi bir son değerlendirme gibi hizalama, kenar boşluğu bırakma ve uzaklık özelliklerinin yapar ve alt düzen yuvasındaki içinde koyar. Alt gerekmez (ve sık desteklemez) tüm ayrılmış alanı doldurun. Denetimi üst döndürülen <xref:System.Windows.Controls.Panel> ve Düzen işlemi tamamlanmış olur.  
  
<a name="LayoutSystem_PanelsCustom"></a>   
## <a name="panel-elements-and-custom-layout-behaviors"></a>Panel öğeleri ve özel düzen davranışları  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] öğesinden türetilen öğeleri bir grup içeren <xref:System.Windows.Controls.Panel>. Bunlar <xref:System.Windows.Controls.Panel> öğeleri etkinleştirme birçok karmaşık düzenler. Örneğin, öğeleri yığma kolayca kullanarak gerçekleştirilebilir <xref:System.Windows.Controls.StackPanel> daha karmaşık ve ücretsiz akışı sağlama düzenleri kullanarak mümkün olsa da öğesi bir <xref:System.Windows.Controls.Canvas>.  
  
 Aşağıdaki tabloda kullanılabilir Düzen özetlenmektedir <xref:System.Windows.Controls.Panel> öğeleri.  
  
|Panel adı|Açıklama|  
|----------------|-----------------|  
|<xref:System.Windows.Controls.Canvas>|İçinde açıkça konumlandırma alt öğeler tarafından göreli koordinatları bir alan tanımlar <xref:System.Windows.Controls.Canvas> alan.|  
|<xref:System.Windows.Controls.DockPanel>|İçinde alt öğeleri yatay veya dikey olarak birbirlerine göreli dizebileceğiniz bir alan tanımlar.|  
|<xref:System.Windows.Controls.Grid>|Sütun ve satırlardan oluşan esnek bir kılavuz alanı tanımlar.|  
|<xref:System.Windows.Controls.StackPanel>|Alt öğeleri yatay veya dikey olarak yönlendirilebilir tek bir çizgi yerleştirir.|  
|<xref:System.Windows.Controls.VirtualizingPanel>|İçin bir çerçeve sunar <xref:System.Windows.Controls.Panel> alt veri koleksiyonlarını sanallaştıran öğeleri. Bu bir soyut sınıftır.|  
|<xref:System.Windows.Controls.WrapPanel>|Sonraki satır kutusunun kenarında içerik bozucu sağa doğru ardışık konumları alt öğeleri kalmadı. Sonraki sıralama gerçekleşir sırayla üstten alta veya değerine bağlı olarak bir soldan sağa <xref:System.Windows.Controls.WrapPanel.Orientation%2A> özelliği.|  
  
 Önceden tanımlanmış kullanarak mümkün olmayan bir düzen gerektiren uygulamalar için <xref:System.Windows.Controls.Panel> öğeleri, özel düzen davranışları devralarak gerçekleştirilebilir <xref:System.Windows.Controls.Panel> ve geçersiz kılma <xref:System.Windows.FrameworkElement.MeasureOverride%2A> ve <xref:System.Windows.FrameworkElement.ArrangeOverride%2A> yöntemleri. Bir örnek için bkz. [özel Radyal paneli örnek](https://go.microsoft.com/fwlink/?LinkID=159982).  
  
<a name="LayoutSystem_Performance"></a>   
## <a name="layout-performance-considerations"></a>Düzen performansla ilgili önemli noktalar  
 Düzen yinelemeli bir işlemdir. Her bir alt öğesinde bir <xref:System.Windows.Controls.Panel.Children%2A> koleksiyon her düzen sistemi çağrılması sırasında işlenen. Gerekli olmadığı durumlarda sonuç olarak, düzen sistemi tetikleme kaçınılmalıdır. Aşağıdaki konular daha iyi performans elde etmenize yardımcı olabilir.  
  
-   Hangi özellik değeri değiştiğinde bir özyinelemeli güncelleştirme düzen sistemi tarafından zorlar dikkat edin.  
  
     Bağımlılık özellikleri değerleri başlatılacak düzen sistemi neden olabilir, Genel Bayrak ile işaretlenir. <xref:System.Windows.FrameworkPropertyMetadata.AffectsMeasure%2A> ve <xref:System.Windows.FrameworkPropertyMetadata.AffectsArrange%2A> yararlı ipuçları için hangi özelliğinin değeri değiştiğinde bir özyinelemeli zorlayacak güncelleştirme tarafından düzen sistemi sağlar. Genel olarak, bir öğenin sınırlayıcı kutusunun boyutunu etkileyen herhangi bir özellik olmalıdır bir <xref:System.Windows.FrameworkPropertyMetadata.AffectsMeasure%2A> bayrağı true olarak ayarlanmış. Daha fazla bilgi için [bağımlılık özelliklerine genel bakış](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md).  
  
-   Mümkün olduğunda, kullanmak bir <xref:System.Windows.UIElement.RenderTransform%2A> yerine bir <xref:System.Windows.FrameworkElement.LayoutTransform%2A>.  
  
     A <xref:System.Windows.FrameworkElement.LayoutTransform%2A> içeriğini etkilemek için çok kullanışlı bir yol olabilir bir [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]. Dönüştürme etkisini diğer öğeleri konumunu etkileyen gerekmez, ancak bunu kullanmak en iyisidir bir <xref:System.Windows.UIElement.RenderTransform%2A> bunun yerine, çünkü <xref:System.Windows.UIElement.RenderTransform%2A> düzen sistemi çağrılmaz. <xref:System.Windows.FrameworkElement.LayoutTransform%2A> dönüştürmenin uygular ve için etkilenen öğenin yeni konumu dikkate almak için özyinelemeli Düzen güncelleştirmenin yapılmasını sağlar.  
  
-   Gereksiz çağrılar önlemek <xref:System.Windows.UIElement.UpdateLayout%2A>.  
  
     <xref:System.Windows.UIElement.UpdateLayout%2A> Yöntemi özyinelemeli düzeni güncelleştirme zorlar ve sık gerekli değildir. Tam bir güncelleştirme gerekli olduğundan emin değilseniz, sizin için bu yöntemi çağırmak için Düzen sistemi kullanır.  
  
-   Büyük bir çalışırken <xref:System.Windows.Controls.Panel.Children%2A> koleksiyonu kullanmayı bir <xref:System.Windows.Controls.VirtualizingStackPanel> yerine normal <xref:System.Windows.Controls.StackPanel>.  
  
     Alt koleksiyon sanallaştırma tarafından <xref:System.Windows.Controls.VirtualizingStackPanel> yalnızca üst görünüm penceresinin içinde olan bellekte nesneleri tutar. Sonuç olarak, çoğu senaryoda performansı önemli ölçüde geliştirilmiştir.  
  
<a name="LayoutSystem_LayoutRounding"></a>   
## <a name="sub-pixel-rendering-and-layout-rounding"></a>Alt piksel işleme ve düzeni yuvarlama  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Grafik sistemi, çözümleme ve cihaz bağımsızlığı etkinleştirmek için CİHAZDAN bağımsız birimler kullanır. Her cihaz bağımsız piksel sistem otomatik olarak ölçeklenen [!INCLUDE[TLA#tla_dpi](../../../../includes/tlasharptla-dpi-md.md)] ayarı. Bu sağlar [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulamaları için uygun ölçeklendirme farklı [!INCLUDE[TLA2#tla_dpi](../../../../includes/tla2sharptla-dpi-md.md)] ayarları ve uygulama otomatik olarak yapar [!INCLUDE[TLA2#tla_dpi](../../../../includes/tla2sharptla-dpi-md.md)]-uyumlu.  
  
 Ancak, bu [!INCLUDE[TLA2#tla_dpi](../../../../includes/tla2sharptla-dpi-md.md)] bağımsızlığı Düzensiz kenarlı işleme nedeniyle düzgünleştirme oluşturabilirsiniz. Cihaz piksel arasında kenar konumu yerine bir cihaz piksel ortasında düştüğünde genellikle bulanık veya yarı saydam kenarları görüldüğü için bu yapılar, ortaya çıkabilir. Düzen sistemi bu düzen yuvarlama ile ayarlamak için bir yol sağlar. Düzen yuvarlama düzen sistemi herhangi bir tamsayı olmayan piksel değeri Düzen geçişi sırasında yere yuvarlar olur.  
  
 Düzen yuvarlama, varsayılan olarak devre dışıdır. Düzen yuvarlama etkinleştirmek için ayarlayın <xref:System.Windows.FrameworkElement.UseLayoutRounding%2A> özelliğini `true` herhangi <xref:System.Windows.FrameworkElement>. Bağımlılık özelliği olduğundan, görsel ağaç tüm alt öğeleri için değer yayılır. Tüm kullanıcı Arabiriminde yuvarlama Düzen etkinleştirmek için <xref:System.Windows.FrameworkElement.UseLayoutRounding%2A> için `true` kök kapsayıcısı üzerinde. Örnek için bkz. <xref:System.Windows.FrameworkElement.UseLayoutRounding%2A>  
  
<a name="LayoutSystem_whatsnext"></a>   
## <a name="whats-next"></a>Yenilikler  
 Öğeleri nasıl ölçülür ve düzenlenmiş anlama anlama Düzen ilk adımdır. Kullanılabilir hakkında daha fazla bilgi için <xref:System.Windows.Controls.Panel> öğeler, bkz [panellere genel bakış](../../../../docs/framework/wpf/controls/panels-overview.md). Düzen etkileyen çeşitli konumlandırma özelliklerini daha iyi anlamak için bkz: [hizalama, kenar boşlukları ve dolguya genel bakış](../../../../docs/framework/wpf/advanced/alignment-margins-and-padding-overview.md). Özel bir örneği için <xref:System.Windows.Controls.Panel> öğesi bkz [özel Radyal paneli örnek](https://go.microsoft.com/fwlink/?LinkID=159982). Basit uygulamada araya getirelim hazır olduğunuzda bkz [izlenecek yol: ilk WPF Masaüstü Uygulamam](../../../../docs/framework/wpf/getting-started/walkthrough-my-first-wpf-desktop-application.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.FrameworkElement>  
 <xref:System.Windows.UIElement>  
 [Panellere Genel Bakış](../../../../docs/framework/wpf/controls/panels-overview.md)  
 [Hizalama, Kenar Boşlukları ve Doldurmaya Genel Bakış](../../../../docs/framework/wpf/advanced/alignment-margins-and-padding-overview.md)  
 [Düzen ve Tasarım](../../../../docs/framework/wpf/advanced/optimizing-performance-layout-and-design.md)
