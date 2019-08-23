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
ms.openlocfilehash: eb254503f5ce2240a03179da693c66f7ada876be
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69918292"
---
# <a name="layout"></a>Düzen
Bu konuda Windows Presentation Foundation (WPF) Düzen sistemi açıklanmaktadır. Düzen hesaplamalarının nasıl ve ne zaman gerçekleşeceğini anlamak, WPF 'de Kullanıcı arabirimleri oluşturmak için önemlidir.  
  
 Bu konu aşağıdaki bölümleri içermektedir:  
  
- [Öğe sınırlayıcı kutuları](#LayoutSystem_BoundingBox)  
  
- [Düzen sistemi](#LayoutSystem_Overview)  
  
- [Alt öğeleri ölçme ve düzenleme](#LayoutSystem_Measure_Arrange)  
  
- [Panel öğeleri ve özel düzen davranışları](#LayoutSystem_PanelsCustom)  
  
- [Düzen performansı konuları](#LayoutSystem_Performance)  
  
- [Alt piksel Işleme ve yerleşim yuvarlama](#LayoutSystem_LayoutRounding)  
  
- [Sıradaki](#LayoutSystem_whatsnext)  
  
<a name="LayoutSystem_BoundingBox"></a>   
## <a name="element-bounding-boxes"></a>Öğe sınırlayıcı kutuları  
 WPF 'de düzen düşünürken, tüm öğeleri çevreleyen sınırlayıcı kutuyu anlamak önemlidir. Düzen <xref:System.Windows.FrameworkElement> sistemi tarafından tüketilen her biri, düzene göre eğimli bir dikdörtgen olarak düşünülebilir. <xref:System.Windows.Controls.Primitives.LayoutInformation> Sınıfı, bir öğenin düzen ayırma veya yuvasının sınırlarını döndürür. Dikdörtgenin boyutu kullanılabilir ekran alanı, herhangi bir kısıtlamaların boyutu, düzene özgü özellikler (kenar boşluğu ve doldurma gibi) ve üst <xref:System.Windows.Controls.Panel> öğenin tek bir davranışı hesaplanarak belirlenir. Bu veriler işlenirken, Düzen sistemi belirli <xref:System.Windows.Controls.Panel>bir ' ın tüm alt öğelerinin konumunu hesaplayabilecektir. Üst öğede <xref:System.Windows.Controls.Border>tanımlanan boyutlandırma özelliklerinin, örneğin, alt öğelerini etkilediğini unutmamak önemlidir.  
  
 Aşağıdaki çizimde basit bir düzen gösterilmektedir.  
  
 ![Sınırlama kutusu bulunmayan tipik bir kılavuz gösteren ekran görüntüsü.](./media/layout/grid-no-bounding-box-superimpose.png)  
  
 Bu düzen aşağıdakiler [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]kullanılarak elde edilebilir.  
  
 [!code-xaml[LayoutInformation#1](~/samples/snippets/csharp/VS_Snippets_Wpf/LayoutInformation/CSharp/Window1.xaml#1)]  
  
 Tek <xref:System.Windows.Controls.TextBlock> bir öğe bir <xref:System.Windows.Controls.Grid>içinde barındırılır. Metin yalnızca ilk sütunun sol üst köşesini doldururken, için <xref:System.Windows.Controls.TextBlock> ayrılan alan gerçekten çok daha büyük olur. Herhangi bir <xref:System.Windows.FrameworkElement> sınırlayıcı kutusu <xref:System.Windows.Controls.Primitives.LayoutInformation.GetLayoutSlot%2A> yöntemi kullanılarak alınabilir. Aşağıdaki çizimde <xref:System.Windows.Controls.TextBlock> öğesi için sınırlayıcı kutusu gösterilmektedir.  
  
 ![TextBlock sınırlayıcı kutusunun artık görünür olduğunu gösteren ekran görüntüsü.](./media/layout/visible-textblock-bounding-box.png)  
  
 Sarı dikdörtgende gösterildiği gibi, <xref:System.Windows.Controls.TextBlock> öğe için ayrılan alan, gerçekten görüntülenenden çok daha büyük olur. Öğesine <xref:System.Windows.Controls.Grid>ek öğeler eklendikçe, eklenen öğelerin türüne ve boyutuna bağlı olarak bu ayırma küçülebilir veya genişleyebilir.  
  
 Öğesinin <xref:System.Windows.Controls.TextBlock> düzen yuvası <xref:System.Windows.Controls.Primitives.LayoutInformation.GetLayoutSlot%2A> yöntemi kullanılarak <xref:System.Windows.Shapes.Path> öğesine çevrilir. Bu teknik, bir öğenin sınırlayıcı kutusunu görüntülemek için yararlı olabilir.  
  
 [!code-csharp[LayoutInformation#2](~/samples/snippets/csharp/VS_Snippets_Wpf/LayoutInformation/CSharp/Window1.xaml.cs#2)]
 [!code-vb[LayoutInformation#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/LayoutInformation/VisualBasic/Window1.xaml.vb#2)]  
  
<a name="LayoutSystem_Overview"></a>   
## <a name="the-layout-system"></a>Düzen sistemi  
 En basit olan düzen, boyutlandırılmış, konumlandırılmış ve çizilmiş bir öğeye yol gösteren özyinelemeli bir sistemdir. Daha belirgin olarak, düzen bir <xref:System.Windows.Controls.Panel> <xref:System.Windows.Controls.Panel.Children%2A> öğe koleksiyonunun üyelerini ölçme ve düzenleme sürecini açıklar. Düzen yoğun bir işlemdir. <xref:System.Windows.Controls.Panel.Children%2A> Koleksiyon ne kadar büyükse, yapılması gereken hesaplamaların sayısı artar. Karmaşıklık, koleksiyona sahip olan <xref:System.Windows.Controls.Panel> öğe tarafından tanımlanan düzen davranışına göre de kullanıma sunulmuştur. Gibi görece basit <xref:System.Windows.Controls.Panel> <xref:System.Windows.Controls.Canvas>olan, <xref:System.Windows.Controls.Panel> gibi<xref:System.Windows.Controls.Grid>daha karmaşık bir performansa sahip olabilir.  
  
 Bir alt öğe <xref:System.Windows.UIElement> konumunu her değiştirdiğinde, Düzen sistemi tarafından yeni bir geçiş tetiklenmesi olası olur. Bu nedenle, gereksiz çağrı kötü uygulama performansına neden olabileceği için, düzen sistemini çağırabilen olayları anlamak önemlidir. Aşağıda, Düzen sistemi çağrıldığında gerçekleşen işlem açıklanmaktadır.  
  
1. Alt öğe <xref:System.Windows.UIElement> , öncelikle temel özellikleri ölçülerek düzen işlemini başlatır.  
  
2. Üzerinde <xref:System.Windows.FrameworkElement> tanımlanan boyutlandırma özellikleri,, ve <xref:System.Windows.FrameworkElement.Margin%2A>gibi değerlendirilir <xref:System.Windows.FrameworkElement.Width%2A>. <xref:System.Windows.FrameworkElement.Height%2A>  
  
3. <xref:System.Windows.Controls.Panel><xref:System.Windows.Controls.Dock> yön veya yığınlama <xref:System.Windows.Controls.StackPanel.Orientation%2A>gibi belirli bir Logic uygulandı.  
  
4. İçerik tüm alt öğeler ölçülerek düzenlenir.  
  
5. <xref:System.Windows.Controls.Panel.Children%2A> Koleksiyon ekranda çizilir.  
  
6. İşlem, koleksiyona ek <xref:System.Windows.Controls.Panel.Children%2A> eklenirse, bir <xref:System.Windows.FrameworkElement.LayoutTransform%2A> uygulanmışsa veya <xref:System.Windows.UIElement.UpdateLayout%2A> yöntemi çağrıldığında yeniden çağrılır.  
  
 Bu işlem ve nasıl çağrıldığı, aşağıdaki bölümlerde daha ayrıntılı olarak tanımlanmıştır.  
  
<a name="LayoutSystem_Measure_Arrange"></a>   
## <a name="measuring-and-arranging-children"></a>Alt öğeleri ölçme ve düzenleme  
 Düzen sistemi, <xref:System.Windows.Controls.Panel.Children%2A> koleksiyonun her üyesi için iki geçişi tamamlar, bir ölçü geçti ve bir düzenleme geçişi. Her alt <xref:System.Windows.Controls.Panel> öğe kendi özel <xref:System.Windows.FrameworkElement.MeasureOverride%2A> Düzen <xref:System.Windows.FrameworkElement.ArrangeOverride%2A> davranışına ulaşmak için kendi ve yöntemlerini sağlar.  
  
 Ölçü geçişi sırasında <xref:System.Windows.Controls.Panel.Children%2A> koleksiyonun her üyesi değerlendirilir. İşlem <xref:System.Windows.UIElement.Measure%2A> yöntemi çağrısıyla başlar. Bu yöntem, üst <xref:System.Windows.Controls.Panel> öğe uygulamasının içinde çağrılır ve düzen gerçekleşmesi için açıkça çağrılması gerekmez.  
  
 İlk olarak, <xref:System.Windows.UIElement> öğesinin yerel boyut özellikleri değerlendirilir, <xref:System.Windows.UIElement.Clip%2A> ve <xref:System.Windows.UIElement.Visibility%2A>gibi. Bu, öğesine <xref:System.Windows.FrameworkElement.MeasureCore%2A>geçirilen adlı `constraintSize` bir değer oluşturur.  
  
 İkinci olarak, üzerinde <xref:System.Windows.FrameworkElement> tanımlanan çerçeve özellikleri işlenir ve bu `constraintSize`değerini etkiler. Bu özellikler genellikle,,, ve <xref:System.Windows.UIElement> <xref:System.Windows.FrameworkElement.Width%2A> <xref:System.Windows.FrameworkElement.Height%2A> <xref:System.Windows.FrameworkElement.Margin%2A>gibitemeldekiboyut özelliklerinianlatmaktadır<xref:System.Windows.FrameworkElement.Style%2A>. Bu özelliklerin her biri, öğesini göstermek için gereken alanı değiştirebilir. <xref:System.Windows.FrameworkElement.MeasureOverride%2A>daha sonra parametresi `constraintSize` olarak çağırılır.  
  
> [!NOTE]
> <xref:System.Windows.FrameworkElement.Height%2A> Ve ve özelliklerinin özellikleri <xref:System.Windows.FrameworkElement.Width%2A> <xref:System.Windows.FrameworkElement.ActualHeight%2A> arasında<xref:System.Windows.FrameworkElement.ActualWidth%2A>bir farklılık vardır. Örneğin, <xref:System.Windows.FrameworkElement.ActualHeight%2A> özellik diğer yükseklik girdilerine ve Düzen sistemine göre hesaplanan bir değerdir. Değer, gerçek bir işleme geçişine göre düzen sisteminin kendisi tarafından ayarlanır ve bu nedenle, örneğin <xref:System.Windows.FrameworkElement.Height%2A>, giriş değişikliğinin temelini oluşturan özellikler kümesi değeri biraz daha geride olabilir.  
>   
>  Hesaplanan <xref:System.Windows.FrameworkElement.ActualHeight%2A> bir değer olduğundan, Düzen sistemine göre çeşitli işlemlere neden olarak, üzerinde birden fazla veya artımlı bildirilen değişiklik olduğunu bilmelisiniz. Düzen sistemi, alt öğeler için gerekli ölçü alanını, üst öğeye göre kısıtlamaları ve bu şekilde hesaplamayı gösterebilir.  
  
 Ölçüm geçişinin nihai hedefi, alt öğesi, <xref:System.Windows.UIElement.DesiredSize%2A> <xref:System.Windows.FrameworkElement.MeasureCore%2A> çağrı sırasında oluşan öğesini tespit etmek için kullanılır. Değer, içerik düzenleme geçişi <xref:System.Windows.UIElement.Measure%2A> sırasında kullanılmak üzere tarafından depolanır. <xref:System.Windows.UIElement.DesiredSize%2A>  
  
 Düzenleme geçişi, <xref:System.Windows.UIElement.Arrange%2A> yöntemi çağrısıyla başlar. Düzenleme geçişi sırasında, üst <xref:System.Windows.Controls.Panel> öğe alt öğenin sınırlarını temsil eden bir dikdörtgen oluşturur. Bu değer, <xref:System.Windows.FrameworkElement.ArrangeCore%2A> işleme yöntemine geçirilir.  
  
 Yöntemi, alt öğesini <xref:System.Windows.UIElement.DesiredSize%2A> değerlendirir ve öğenin işlenmiş boyutunu etkileyebilecek ek kenar boşluklarını değerlendirir. <xref:System.Windows.FrameworkElement.ArrangeCore%2A> <xref:System.Windows.FrameworkElement.ArrangeCore%2A>parametresi <xref:System.Windows.FrameworkElement.ArrangeOverride%2A> `arrangeSize` olarak<xref:System.Windows.Controls.Panel> yöntemine geçirilen bir oluşturur. <xref:System.Windows.FrameworkElement.ArrangeOverride%2A>`finalSize` alt öğesinin öğesini oluşturur. Son olarak, <xref:System.Windows.FrameworkElement.ArrangeCore%2A> yöntemi kenar boşluğu ve hizalama gibi bir sınır özelliği değerlendirmesi yapar ve alt öğesini Düzen yuvasının içine koyar. Alt öğe, ayrılan alanın tamamını doldurmalı (ve sık değil). Sonra Denetim üst öğeye <xref:System.Windows.Controls.Panel> döndürülür ve düzen işlemi tamamlanmıştır.  
  
<a name="LayoutSystem_PanelsCustom"></a>   
## <a name="panel-elements-and-custom-layout-behaviors"></a>Panel öğeleri ve özel düzen davranışları  
WPF, öğesinden <xref:System.Windows.Controls.Panel>türetilen bir öğe grubunu içerir. Bu <xref:System.Windows.Controls.Panel> öğeler birçok karmaşık düzeni etkinleştirir. Örneğin, yığın öğeleri <xref:System.Windows.Controls.StackPanel> öğesi kullanılarak kolayca elde edilebilir, ancak daha karmaşık ve ücretsiz akış düzenleri bir <xref:System.Windows.Controls.Canvas>kullanılarak yapılabilir.  
  
 Aşağıdaki tabloda kullanılabilir Düzen <xref:System.Windows.Controls.Panel> öğeleri özetlenmektedir.  
  
|Panel adı|Açıklama|  
|----------------|-----------------|  
|<xref:System.Windows.Controls.Canvas>|Alt öğeleri <xref:System.Windows.Controls.Canvas> alana göreli olarak açıkça konumlandırabileceğiniz bir alan tanımlar.|  
|<xref:System.Windows.Controls.DockPanel>|Alt öğeleri yatay veya dikey olarak birbirlerine göre düzenleyebileceğiniz bir alan tanımlar.|  
|<xref:System.Windows.Controls.Grid>|Sütun ve satırlardan oluşan esnek bir kılavuz alanı tanımlar.|  
|<xref:System.Windows.Controls.StackPanel>|Alt öğeleri yatay veya dikey olarak yönelimli tek bir satıra yerleştirir.|  
|<xref:System.Windows.Controls.VirtualizingPanel>|Alt veri koleksiyonlarını sanallaştıran öğeler için <xref:System.Windows.Controls.Panel> bir çerçeve sağlar. Bu soyut bir sınıftır.|  
|<xref:System.Windows.Controls.WrapPanel>|Sol taraftaki alt öğeleri, kapsayan kutunun kenarındaki bir sonraki satıra kadar olan sıralı konumda konumlandırır. Sonraki sıralama, <xref:System.Windows.Controls.WrapPanel.Orientation%2A> özelliğin değerine bağlı olarak yukarıdan aşağıya veya sağdan sola doğru bir şekilde gerçekleşir.|  
  
 Önceden tanımlanmış <xref:System.Windows.Controls.Panel> öğelerden herhangi birini kullanarak mümkün olmayan bir düzen gerektiren uygulamalar için, <xref:System.Windows.FrameworkElement.MeasureOverride%2A> ve <xref:System.Windows.FrameworkElement.ArrangeOverride%2A> yöntemlerini <xref:System.Windows.Controls.Panel> devralarak ve geçersiz kılarak özel düzen davranışları elde edilebilir.  
  
<a name="LayoutSystem_Performance"></a>   
## <a name="layout-performance-considerations"></a>Düzen performansı konuları  
 Düzen özyinelemeli bir işlemdir. Bir <xref:System.Windows.Controls.Panel.Children%2A> koleksiyondaki her alt öğe, düzen sisteminin her çağrılması sırasında işlenir. Sonuç olarak, gerekli olmadığında düzen sisteminin tetiklenmesi gerekir. Aşağıdaki noktalar daha iyi performans elde etmenize yardımcı olabilir.  
  
- Hangi özellik değeri değişikliklerinin düzen sistemi tarafından özyinelemeli güncelleştirme zorlayacaktır.  
  
     Değerleri, düzen sisteminin başlatılmasına neden olabilecek bağımlılık özellikleri, ortak bayraklarla işaretlenir. <xref:System.Windows.FrameworkPropertyMetadata.AffectsMeasure%2A>ve <xref:System.Windows.FrameworkPropertyMetadata.AffectsArrange%2A> hangi özellik değeri değişikliklerinin düzen sistemi tarafından özyinelemeli bir güncelleştirme zoracağı konusunda yararlı ipuçları sağlar. Genel olarak, bir öğenin sınırlayıcı kutusunun boyutunu etkileyebilecek herhangi bir özelliğin, true olarak ayarlanmış bir <xref:System.Windows.FrameworkPropertyMetadata.AffectsMeasure%2A> bayrağı olmalıdır. Daha fazla bilgi için bkz. [bağımlılık özelliklerine genel bakış](dependency-properties-overview.md).  
  
- Mümkün olduğunda, <xref:System.Windows.UIElement.RenderTransform%2A> yerine <xref:System.Windows.FrameworkElement.LayoutTransform%2A>bir kullanın.  
  
     Bir <xref:System.Windows.FrameworkElement.LayoutTransform%2A> , içeriğini [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]etkilemek için çok kullanışlı bir yol olabilir. Ancak, dönüşümün etkisinin diğer öğelerin konumunu etkilemesi gerekmez, çünkü <xref:System.Windows.UIElement.RenderTransform%2A> <xref:System.Windows.UIElement.RenderTransform%2A> düzen sistemini çağırmaz, bunun yerine bunun kullanılması en iyisidir. <xref:System.Windows.FrameworkElement.LayoutTransform%2A>dönüşümünü uygular ve etkilenen öğenin yeni konumu için bir özyinelemeli Düzen güncelleştirmesini hesaba zorlar.  
  
- İçin <xref:System.Windows.UIElement.UpdateLayout%2A>gereksiz çağrılardan kaçının.  
  
     <xref:System.Windows.UIElement.UpdateLayout%2A> Yöntemi özyinelemeli bir Düzen güncelleştirmesini zorlar ve genellikle gerekli değildir. Tam bir güncelleştirmenin gerekli olduğundan emin olmadığınız için, bu yöntemi sizin için çağırmak üzere Düzen sistemine güvenin.  
  
- Büyük <xref:System.Windows.Controls.Panel.Children%2A> bir koleksiyonla çalışırken, normal <xref:System.Windows.Controls.StackPanel>yerine bir <xref:System.Windows.Controls.VirtualizingStackPanel> kullanmayı düşünün.  
  
     Alt koleksiyonu sanallaştırarak, <xref:System.Windows.Controls.VirtualizingStackPanel> yalnızca üst öğe görünüm içerisindeki bellekteki nesneleri tutar. Sonuç olarak, Çoğu senaryoda performans önemli ölçüde geliştirilmiştir.  
  
<a name="LayoutSystem_LayoutRounding"></a>   
## <a name="sub-pixel-rendering-and-layout-rounding"></a>Alt piksel Işleme ve yerleşim yuvarlama  
 WPF Grafik sistemi, çözümleme ve cihaz bağımsızlığını etkinleştirmek için cihazdan bağımsız birimler kullanır. Her cihazdan bağımsız piksel, sistemin nokta/inç (dpi) ayarıyla otomatik olarak ölçeklendirilir. Bu, WPF uygulamalarına farklı DPI ayarları için uygun ölçeklendirmeyi sağlar ve uygulamayı otomatik olarak DPI duyarlı hale getirir.  
  
 Ancak, bu DPI bağımsızlık, kenar yumuşatma nedeniyle düzensiz kenar işleme oluşturabilir. Genellikle bulanık veya yarı saydam kenarlar olarak görülen bu yapıtlar, bir kenarın konumu cihaz pikselleri arasında değil bir cihaz pikseli ortasında kaldığında gerçekleşebilir. Düzen sistemi, düzen yuvarlama ile bunu yapmak için bir yol sağlar. Düzen yuvarlama, düzen sisteminin, düzen geçişi sırasında tam sayı olmayan piksel değerlerini yuvarlar.  
  
 Düzen yuvarlama varsayılan olarak devre dışıdır. Düzen yuvarlamayı etkinleştirmek için <xref:System.Windows.FrameworkElement.UseLayoutRounding%2A> özelliği herhangi bir <xref:System.Windows.FrameworkElement>üzerinde olarak `true` ayarlayın. Bir bağımlılık özelliği olduğundan, değer görsel ağaçtaki tüm alt öğelere yayılır. Tüm Kullanıcı arabiriminin düzen yuvarlamayı etkinleştirmek için, kök kapsayıcısında <xref:System.Windows.FrameworkElement.UseLayoutRounding%2A> olarak `true` ayarlayın. Örnek için bkz. <xref:System.Windows.FrameworkElement.UseLayoutRounding%2A>  
  
<a name="LayoutSystem_whatsnext"></a>   
## <a name="whats-next"></a>Sıradaki  
 Öğelerin nasıl ölçüleceğini ve düzenlenmesini anlamak, düzeni anlamak için ilk adımdır. Kullanılabilir <xref:System.Windows.Controls.Panel> öğeler hakkında daha fazla bilgi için bkz. [panellere genel bakış](../controls/panels-overview.md). Düzeni etkileyebilecek çeşitli konumlandırma özelliklerini daha iyi anlamak için bkz. [Hizalama, kenar boşlukları ve doldurmaya genel bakış](alignment-margins-and-padding-overview.md). Bunu hafif bir uygulamada birlikte koymaya hazırsanız bkz [. İzlenecek yol: İlk WPF Masaüstü](../getting-started/walkthrough-my-first-wpf-desktop-application.md)Uygulamam.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.FrameworkElement>
- <xref:System.Windows.UIElement>
- [Panellere Genel Bakış](../controls/panels-overview.md)
- [Hizalama, Kenar Boşlukları ve Doldurmaya Genel Bakış](alignment-margins-and-padding-overview.md)
- [Düzen ve Tasarım](optimizing-performance-layout-and-design.md)
