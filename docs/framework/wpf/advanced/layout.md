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
ms.openlocfilehash: 00c2b2bcb58e60c1a60d2d360f25089c079c0704
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="layout"></a>Düzen
Bu konuda açıklanmaktadır [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] düzen sistemi. Düzen hesaplamaları nasıl ve ne zaman meydana anlamak, kullanıcı arabirimi oluşturmak için temel [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
 Bu konu aşağıdaki bölümleri içermektedir:  
  
-   [Sınırlayıcı kutular öğesi](#LayoutSystem_BoundingBox)  
  
-   [Düzen sistemi](#LayoutSystem_Overview)  
  
-   [Ölçme ve alt öğelerini düzenleme](#LayoutSystem_Measure_Arrange)  
  
-   [Panel öğeleri ve özel yerleşim davranışları](#LayoutSystem_PanelsCustom)  
  
-   [Düzen performans etkenleri](#LayoutSystem_Performance)  
  
-   [Alt piksel işleme ve Düzen yuvarlama](#LayoutSystem_LayoutRounding)  
  
-   [Sırada ne var?](#LayoutSystem_whatsnext)  
  
<a name="LayoutSystem_BoundingBox"></a>   
## <a name="element-bounding-boxes"></a>Sınırlayıcı kutular öğesi  
 Düzende hakkında düşünürken, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], tüm öğeleri çevreleyen sınırlama kutusu anlamak önemlidir. Her <xref:System.Windows.FrameworkElement> tüketilen düzeni tarafından sistem, Düzen yarıklı bir dikdörtgen olarak düşünülebilir. <xref:System.Windows.Controls.Primitives.LayoutInformation> Sınıfı, bir öğenin düzeni ayırmayı veya yuva sınırlarının döndürür. Dikdörtgen boyutu kullanılabilir ekran alanının, kısıtlamalar, Düzen özgü özellikleri (örneğin, kenar boşluğu bırakma ve doldurma) ve üst tek tek davranışını boyutunu hesaplayarak belirlenir <xref:System.Windows.Controls.Panel> öğesi. Bu veri işleme, düzen sistemi belirli bir öğenin alt öğelerine konumunu hesaplamak yapabiliyor <xref:System.Windows.Controls.Panel>. Gibi özellikleri boyutlandırma üst öğede tanımlanan unutulmaması önemlidir; bir <xref:System.Windows.Controls.Border>, alt öğelerini etkiler.  
  
 Aşağıdaki çizim basit bir düzen göstermektedir.  
  
 ![Tipik bir kılavuz, sınırlama kutusu yerleştirilmemiş. ] (../../../../docs/framework/wpf/advanced/media/boundingbox1.png "boundingbox1")  
  
 Bu düzen aşağıdaki kullanarak elde edilebilir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].  
  
 [!code-xaml[LayoutInformation#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LayoutInformation/CSharp/Window1.xaml#1)]  
  
 Tek bir <xref:System.Windows.Controls.TextBlock> öğesi içinde barındırılan bir <xref:System.Windows.Controls.Grid>. Metnin ilk sütun için ayrılan alanı yalnızca sol üst köşesindeki doldururken <xref:System.Windows.Controls.TextBlock> gerçekten çok büyük. Sınırlama kutusu herhangi <xref:System.Windows.FrameworkElement> kullanılarak alınabilir <xref:System.Windows.Controls.Primitives.LayoutInformation.GetLayoutSlot%2A> yöntemi. Sınırlama kutusu aşağıda gösterilmiştir <xref:System.Windows.Controls.TextBlock> öğesi.  
  
 ![Sınırlama kutusu TextBlock öğesinin artık görünür olur. ] (../../../../docs/framework/wpf/advanced/media/boundingbox2.png "boundingbox2")  
  
 Sarı dikdörtgen için ayrılan alanı gösterildiği gibi <xref:System.Windows.Controls.TextBlock> öğesidir göründüğü gerçekten çok büyük. Ek öğeler eklendikçe <xref:System.Windows.Controls.Grid>, bu ayırma daraltabilir veya eklenen öğelerinin boyutunu ve türünü bağlı olarak,'ı genişletin.  
  
 Düzen yuvasını <xref:System.Windows.Controls.TextBlock> erişimcisine bir <xref:System.Windows.Shapes.Path> kullanarak <xref:System.Windows.Controls.Primitives.LayoutInformation.GetLayoutSlot%2A> yöntemi. Bu yöntem, bir öğenin sınırlama kutusu görüntülemek için yararlı olabilir.  
  
 [!code-csharp[LayoutInformation#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LayoutInformation/CSharp/Window1.xaml.cs#2)]
 [!code-vb[LayoutInformation#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/LayoutInformation/VisualBasic/Window1.xaml.vb#2)]  
  
<a name="LayoutSystem_Overview"></a>   
## <a name="the-layout-system"></a>Düzen sistemi  
 En basit şekliyle, Düzen sistemidir, bir öğenin yeniden boyutlandırılmış konumlandırılmış ve çizilmiş götüren bir özyinelemeli. Daha açık belirtmek gerekirse düzeni ölçme ve üyeleri düzenleme işlemi açıklanır bir <xref:System.Windows.Controls.Panel> öğenin <xref:System.Windows.Controls.Panel.Children%2A> koleksiyonu. Düzen yoğunluklu bir işlemdir. Büyük <xref:System.Windows.Controls.Panel.Children%2A> koleksiyonu, yapılması gereken hesaplamalar büyük sayısı. Karmaşıklık ayrıca sunulmuştur tarafından tanımlanan düzeni davranışa göre <xref:System.Windows.Controls.Panel> koleksiyona sahip öğe. Görece basit <xref:System.Windows.Controls.Panel>, gibi <xref:System.Windows.Controls.Canvas>, daha karmaşık daha önemli ölçüde daha iyi performans sağlayabilirsiniz <xref:System.Windows.Controls.Panel>, gibi <xref:System.Windows.Controls.Grid>.  
  
 Her bir alt <xref:System.Windows.UIElement> konumunu değiştirdiğinde düzen sisteminde yeni bir geçişi tetikleme olasılığı vardır. Bu nedenle, gereksiz çağırma olarak düzen sistemi çağırabileceği olayları zayıf uygulama performansını açabilir anlamak önemlidir. Aşağıdaki düzen sistemi çağrıldığında oluşan işlemini açıklar.  
  
1.  Bir alt <xref:System.Windows.UIElement> çekirdek özellikleri ölçülerek düzen işlemine başlar.  
  
2.  Üzerinde tanımlanan özellikler boyutlandırma <xref:System.Windows.FrameworkElement> , aşağıdaki gibi değerlendirilir <xref:System.Windows.FrameworkElement.Width%2A>, <xref:System.Windows.FrameworkElement.Height%2A>, ve <xref:System.Windows.FrameworkElement.Margin%2A>.  
  
3.  <xref:System.Windows.Controls.Panel>-belirli mantığı uygulandığı gibi <xref:System.Windows.Controls.Dock> yönünü veya yığınlama <xref:System.Windows.Controls.StackPanel.Orientation%2A>.  
  
4.  Tüm alt öğeleri ölçülen sonra içerik düzenlenmiş.  
  
5.  <xref:System.Windows.Controls.Panel.Children%2A> Koleksiyonu ekranda çizilir.  
  
6.  İşlemi yeniden ek çağrılır <xref:System.Windows.Controls.Panel.Children%2A> koleksiyonuna eklenen bir <xref:System.Windows.FrameworkElement.LayoutTransform%2A> uygulanan veya <xref:System.Windows.UIElement.UpdateLayout%2A> yöntemi çağrılır.  
  
 Bu işlem ve nasıl çağrıldığını aşağıdaki bölümlerde daha ayrıntılı olarak tanımlanır.  
  
<a name="LayoutSystem_Measure_Arrange"></a>   
## <a name="measuring-and-arranging-children"></a>Ölçme ve alt öğelerini düzenleme  
 Düzen sistemi her üyesi için iki geçiş tamamlandıktan <xref:System.Windows.Controls.Panel.Children%2A> koleksiyonu, bir ölçü geçişi ve bir düzenleme geçişi. Her alt <xref:System.Windows.Controls.Panel> kendi sağlar <xref:System.Windows.FrameworkElement.MeasureOverride%2A> ve <xref:System.Windows.FrameworkElement.ArrangeOverride%2A> kendi belirli düzen davranışını ulaşmak için yöntem.  
  
 Ölçü geçişi sırasında her bir üyesi <xref:System.Windows.Controls.Panel.Children%2A> koleksiyonu değerlendirildiği. Çağrısıyla işlemi başlar. <xref:System.Windows.UIElement.Measure%2A> yöntemi. Bu yöntem üst uygulama içinde çağrılır <xref:System.Windows.Controls.Panel> öğesi ve açıkça ortaya düzeni için çağrılması gerekmez.  
  
 İlk, yerel boyutu özelliklerini <xref:System.Windows.UIElement> , aşağıdaki gibi değerlendirilir <xref:System.Windows.UIElement.Clip%2A> ve <xref:System.Windows.UIElement.Visibility%2A>. Bu adlı bir değer oluşturur `constraintSize` için geçirilen <xref:System.Windows.FrameworkElement.MeasureCore%2A>.  
  
 İkincisi, üzerinde framework özellikleri tanımlanan <xref:System.Windows.FrameworkElement> işlenir, değerini etkiler `constraintSize`. Bu özellikleri genellikle temel boyutlandırma özelliklerini açıklayan <xref:System.Windows.UIElement>, gibi kendi <xref:System.Windows.FrameworkElement.Height%2A>, <xref:System.Windows.FrameworkElement.Width%2A>, <xref:System.Windows.FrameworkElement.Margin%2A>, ve <xref:System.Windows.FrameworkElement.Style%2A>. Bu özelliklerin her biri öğeyi görüntülemek için gerekli alanı değiştirebilirsiniz. <xref:System.Windows.FrameworkElement.MeasureOverride%2A> sonra çağrılır `constraintSize` bir parametre olarak.  
  
> [!NOTE]
>  Özellikleri arasında bir fark <xref:System.Windows.FrameworkElement.Height%2A> ve <xref:System.Windows.FrameworkElement.Width%2A> ve <xref:System.Windows.FrameworkElement.ActualHeight%2A> ve <xref:System.Windows.FrameworkElement.ActualWidth%2A>. Örneğin, <xref:System.Windows.FrameworkElement.ActualHeight%2A> diğer yükseklik girişleri ve Düzen sistemine dayalı bir hesaplanan değer bir özelliktir. Değer bir gerçek işleme geçişte, düzen sistem tabanlı kendisi tarafından ayarlanır ve bu nedenle biraz özellikleri değerini ayarlayın gibi geri kalabilir <xref:System.Windows.FrameworkElement.Height%2A>, giriş değiştirme temeli olan.  
>   
>  Çünkü <xref:System.Windows.FrameworkElement.ActualHeight%2A> bilmeniz gereken bir hesaplanan değer olan birden çok da olabilir veya artımlı bildirilen için çeşitli işlemleri sonucunda düzen sistemi tarafından değiştirir. Düzen sistemi alt öğeler, üst öğenin vb. tarafından kısıtlamaları için gerekli ölçü alanı hesaplama.  
  
 Ultimate ölçü geçişi belirlemek için alt hedefidir kendi <xref:System.Windows.UIElement.DesiredSize%2A>, oluştuğu sırasında <xref:System.Windows.FrameworkElement.MeasureCore%2A> çağırın. <xref:System.Windows.UIElement.DesiredSize%2A> Değeri tarafından depolanır <xref:System.Windows.UIElement.Measure%2A> içerik Yerleştir geçişi sırasında kullanılacak.  
  
 Düzenleme geçişi yapılan bir çağrı ile başlayan <xref:System.Windows.UIElement.Arrange%2A> yöntemi. Yerleştir geçişi sırasında üst <xref:System.Windows.Controls.Panel> alt sınırlarını temsil eden bir dikdörtgen öğesi oluşturur. Bu değer geçirilir <xref:System.Windows.FrameworkElement.ArrangeCore%2A> işleme yöntemi.  
  
 <xref:System.Windows.FrameworkElement.ArrangeCore%2A> Yöntemi değerlendirir <xref:System.Windows.UIElement.DesiredSize%2A> alt ve öğe işlenmiş boyutunu etkileyebilecek herhangi ek kenar boşluklarını değerlendirir. <xref:System.Windows.FrameworkElement.ArrangeCore%2A> oluşturan bir `arrangeSize`, için geçirilen <xref:System.Windows.FrameworkElement.ArrangeOverride%2A> yöntemi <xref:System.Windows.Controls.Panel> bir parametre olarak. <xref:System.Windows.FrameworkElement.ArrangeOverride%2A> oluşturur `finalSize` alt. Son olarak, <xref:System.Windows.FrameworkElement.ArrangeCore%2A> yöntemi kenar boşluğu ve hizalama gibi uzaklık özelliklerinin son değerlendirme yapar ve kendi düzeni yuvası içinde alt koyar. Alt yok (ve sık desteklemez) ayrılmış alanı tüm doldurun. Denetim üst sonra döndürülen <xref:System.Windows.Controls.Panel> ve düzeni işlemi tamamlanır.  
  
<a name="LayoutSystem_PanelsCustom"></a>   
## <a name="panel-elements-and-custom-layout-behaviors"></a>Panel öğeleri ve özel yerleşim davranışları  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] öğesinden türetilen öğeleri grubunu içeren <xref:System.Windows.Controls.Panel>. Bunlar <xref:System.Windows.Controls.Panel> öğeleri çok karmaşık düzenleri etkinleştirin. Örneğin, öğeleri yığma kolayca kullanarak elde edilebilir <xref:System.Windows.Controls.StackPanel> kullanarak daha karmaşık ve ücretsiz boyunca düzenleri olası sırada öğesi, bir <xref:System.Windows.Controls.Canvas>.  
  
 Aşağıdaki tabloda kullanılabilir düzeni özetler <xref:System.Windows.Controls.Panel> öğeleri.  
  
|Panel adı|Açıklama|  
|----------------|-----------------|  
|<xref:System.Windows.Controls.Canvas>|İçinde açıkça getirin alt öğeleri göreli koordinatları tarafından bir alanı tanımlar <xref:System.Windows.Controls.Canvas> alanı.|  
|<xref:System.Windows.Controls.DockPanel>|İçinde alt öğelerini yatay veya dikey olarak, diğer göre düzenleyebilirsiniz alanı tanımlar.|  
|<xref:System.Windows.Controls.Grid>|Sütunları ve satırları oluşan bir esnek Kılavuz alanı tanımlar.|  
|<xref:System.Windows.Controls.StackPanel>|Alt öğelerini yatay veya dikey olarak yönlendirilebilir tek bir satıra düzenler.|  
|<xref:System.Windows.Controls.VirtualizingPanel>|İçin bir çerçeve sunar <xref:System.Windows.Controls.Panel> kendi alt veri toplama sanallaştırmak öğeleri. Bu soyut bir sınıftır.|  
|<xref:System.Windows.Controls.WrapPanel>|Sonraki satıra kapsayan kutunun kenarında içeriği ayırma sağa sıralı konumundan konumlar alt öğe kalmadı. Sonraki sıralama oluşur sıralı olarak üstten alta veya sağdan sola değerine bağlı olarak <xref:System.Windows.Controls.WrapPanel.Orientation%2A> özelliği.|  
  
 Önceden tanımlanmış birini kullanarak mümkün olmayan bir düzen gerektiren uygulamalar için <xref:System.Windows.Controls.Panel> öğeleri, özel düzen davranışları elde edilebilir devralarak <xref:System.Windows.Controls.Panel> ve geçersiz kılma <xref:System.Windows.FrameworkElement.MeasureOverride%2A> ve <xref:System.Windows.FrameworkElement.ArrangeOverride%2A> yöntemleri. Bir örnek için bkz: [özel Radyal paneli örneği](http://go.microsoft.com/fwlink/?LinkID=159982).  
  
<a name="LayoutSystem_Performance"></a>   
## <a name="layout-performance-considerations"></a>Düzen performans etkenleri  
 Düzen yinelemeli bir işlemdir. Her bir alt öğe bir <xref:System.Windows.Controls.Panel.Children%2A> koleksiyonu her düzen sistemi başlatma sırasında işlenen. Gerekli olmadığında sonuç olarak, düzen sistemi tetikleme kaçınılmalıdır. Aşağıdaki konular daha iyi performans elde size yardımcı olabilir.  
  
-   Hangi özellik değeri değişiklikleri özyinelemeli güncelleştirme düzen sistemi tarafından zorlayacağı dikkat edin.  
  
     Bağımlılık özellikleri değerleri başlatılması düzen sistemi neden olabilir, ortak bayrakları ile işaretlenir. <xref:System.Windows.FrameworkPropertyMetadata.AffectsMeasure%2A> ve <xref:System.Windows.FrameworkPropertyMetadata.AffectsArrange%2A> hangi özelliği için değer değişikliklerini bir özyinelemeli zorlayacak yararlı ipuçları güncelleştirme düzen sistemi tarafından sağlayın. Genel olarak, bir öğenin sınırlayıcı kutu boyutunu etkileyebilecek herhangi bir özellik olmalıdır bir <xref:System.Windows.FrameworkPropertyMetadata.AffectsMeasure%2A> bayrağı true olarak ayarlanmış. Daha fazla bilgi için bkz: [bağımlılık özelliklerine genel bakış](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md).  
  
-   Mümkün olduğunda kullanın bir <xref:System.Windows.UIElement.RenderTransform%2A> yerine bir <xref:System.Windows.FrameworkElement.LayoutTransform%2A>.  
  
     A <xref:System.Windows.FrameworkElement.LayoutTransform%2A> içeriğini etkilemek için çok kullanışlı bir yoldur bir [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]. Dönüştürme etkisini diğer öğeleri konumunu etkileyen gerekmez, ancak kullanmak en iyisidir bir <xref:System.Windows.UIElement.RenderTransform%2A> bunun yerine, çünkü <xref:System.Windows.UIElement.RenderTransform%2A> düzen sistemi çağrılmaz. <xref:System.Windows.FrameworkElement.LayoutTransform%2A> kendi dönüştürmesi uygular ve etkilenen öğesinin yeni konumu için hesap için bir özyinelemeli Düzen güncelleştirmesini zorlar.  
  
-   Gereksiz çağrıları kaçının <xref:System.Windows.UIElement.UpdateLayout%2A>.  
  
     <xref:System.Windows.UIElement.UpdateLayout%2A> Yöntemi bir özyinelemeli Düzen güncelleştirmesini zorlar ve sık gerekli değildir. Tam güncelleştirme gerekli olduğundan emin değilseniz, sizin için bu yöntemi çağırmak için Düzen sistemi kullanır.  
  
-   Büyük ile çalışırken <xref:System.Windows.Controls.Panel.Children%2A> koleksiyonu kullanmayı bir <xref:System.Windows.Controls.VirtualizingStackPanel> bir normal yerine <xref:System.Windows.Controls.StackPanel>.  
  
     Alt koleksiyona sanallaştırılmasını tarafından <xref:System.Windows.Controls.VirtualizingStackPanel> yalnızca şu anda üst öğenin görünüm penceresinin içinde olan bellekte nesneleri tutar. Sonuç olarak, performans Çoğu senaryoda önemli ölçüde geliştirildi.  
  
<a name="LayoutSystem_LayoutRounding"></a>   
## <a name="sub-pixel-rendering-and-layout-rounding"></a>Alt piksel işleme ve Düzen yuvarlama  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Grafik sistemi çözünürlüğü ve aygıttan bağımsızlığı etkinleştirmek için CİHAZDAN bağımsız birimler kullanır. Her aygıttan bağımsız piksel sisteminin otomatik olarak ölçekler [!INCLUDE[TLA#tla_dpi](../../../../includes/tlasharptla-dpi-md.md)] ayarı. Bu sağlar [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulamaları için uygun ölçeklendirme farklı [!INCLUDE[TLA2#tla_dpi](../../../../includes/tla2sharptla-dpi-md.md)] ayarları ve uygulama otomatik olarak yapar [!INCLUDE[TLA2#tla_dpi](../../../../includes/tla2sharptla-dpi-md.md)]-kullanan.  
  
 Ancak, bu [!INCLUDE[TLA2#tla_dpi](../../../../includes/tla2sharptla-dpi-md.md)] bağımsızlığı nedeniyle düzgünleştirme düzensiz kenar işleme oluşturabilirsiniz. Aygıt piksel arasında kenar konumunu aygıt piksel yerine ortasında düştüğünde genellikle bulanık veya yarı saydam kenarları görülür, bu yapıtların ortaya çıkabilir. Düzen sistemi bu düzen yuvarlama ile ayarlamak için bir yol sağlar. Düzen yuvarlama burada düzen sistemi integral olmayan piksel değerleri Düzen geçişi sırasında yuvarlar olur.  
  
 Düzen yuvarlama varsayılan olarak devre dışıdır. Düzen yuvarlama etkinleştirmek için ayarlanmış <xref:System.Windows.FrameworkElement.UseLayoutRounding%2A> özelliğine `true` herhangi <xref:System.Windows.FrameworkElement>. Bağımlılık özelliği olduğundan, değerin görsel ağaç öğenin alt öğelerine yayılır. Tüm kullanıcı Arabirimi yuvarlama düzeni etkinleştirmek için ayarlayın <xref:System.Windows.FrameworkElement.UseLayoutRounding%2A> için `true` kök kapsayıcısı üzerinde. Örnek için bkz. <xref:System.Windows.FrameworkElement.UseLayoutRounding%2A>  
  
<a name="LayoutSystem_whatsnext"></a>   
## <a name="whats-next"></a>Sırada ne var?  
 Öğeleri nasıl ölçülen ve düzenlenmiş anlama anlama düzeni ilk adımdır. Kullanılabilir hakkında daha fazla bilgi için <xref:System.Windows.Controls.Panel> öğeler, bkz [paneller genel bakış](../../../../docs/framework/wpf/controls/panels-overview.md). Düzen etkileyen çeşitli konumlandırma özelliklerini daha iyi anlamak için bkz: [hizalama, kenar boşlukları ve doldurma genel bakış](../../../../docs/framework/wpf/advanced/alignment-margins-and-padding-overview.md). Özel bir örneği için <xref:System.Windows.Controls.Panel> öğesi, bkz: [özel Radyal paneli örnek](http://go.microsoft.com/fwlink/?LinkID=159982). Hafif uygulamada hepsini bir araya getirin hazır olduğunuzda bkz [gözden geçirme: ilk WPF Masaüstü Uygulamam](../../../../docs/framework/wpf/getting-started/walkthrough-my-first-wpf-desktop-application.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.FrameworkElement>  
 <xref:System.Windows.UIElement>  
 [Panellere Genel Bakış](../../../../docs/framework/wpf/controls/panels-overview.md)  
 [Hizalama, Kenar Boşlukları ve Doldurmaya Genel Bakış](../../../../docs/framework/wpf/advanced/alignment-margins-and-padding-overview.md)  
 [Düzen ve Tasarım](../../../../docs/framework/wpf/advanced/optimizing-performance-layout-and-design.md)
