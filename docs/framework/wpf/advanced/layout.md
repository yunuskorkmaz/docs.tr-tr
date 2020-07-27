---
title: Layout
description: Windows Presentation Foundation düzen sisteminde düzen hesaplamalarının nasıl ve ne zaman gerçekleşeceğini anlayın.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WPF layout system [WPF]
- controls [WPF], layout system
- layout system [WPF]
ms.assetid: 3eecdced-3623-403a-a077-7595453a9221
ms.openlocfilehash: 0db3f2a6cbabc610362435d64de3fc970f01a73c
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87164767"
---
# <a name="layout"></a>Layout

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

WPF 'de düzen düşünürken, tüm öğeleri çevreleyen sınırlayıcı kutuyu anlamak önemlidir. <xref:System.Windows.FrameworkElement>Düzen sistemi tarafından tüketilen her biri, düzene göre eğimli bir dikdörtgen olarak düşünülebilir. <xref:System.Windows.Controls.Primitives.LayoutInformation>Sınıfı, bir öğenin düzen ayırma veya yuvasının sınırlarını döndürür. Dikdörtgenin boyutu kullanılabilir ekran alanı, herhangi bir kısıtlamaların boyutu, düzene özgü özellikler (kenar boşluğu ve doldurma gibi) ve üst öğenin tek bir davranışı hesaplanarak belirlenir <xref:System.Windows.Controls.Panel> . Bu veriler işlenirken, Düzen sistemi belirli bir ' ın tüm alt öğelerinin konumunu hesaplayabilecektir <xref:System.Windows.Controls.Panel> . Üst öğede tanımlanan boyutlandırma özelliklerinin, örneğin, <xref:System.Windows.Controls.Border> alt öğelerini etkilediğini unutmamak önemlidir.

Aşağıdaki çizimde basit bir düzen gösterilmektedir.

![Sınırlama kutusu bulunmayan tipik bir kılavuz gösteren ekran görüntüsü.](./media/layout/grid-no-bounding-box-superimpose.png)

Bu düzen aşağıdakiler kullanılarak elde edilebilir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] .

[!code-xaml[LayoutInformation#1](~/samples/snippets/csharp/VS_Snippets_Wpf/LayoutInformation/CSharp/Window1.xaml#1)]

Tek <xref:System.Windows.Controls.TextBlock> bir öğe bir içinde barındırılır <xref:System.Windows.Controls.Grid> . Metin yalnızca ilk sütunun sol üst köşesini doldururken, için ayrılan alan <xref:System.Windows.Controls.TextBlock> gerçekten çok daha büyük olur. Herhangi bir sınırlayıcı kutusu <xref:System.Windows.FrameworkElement> yöntemi kullanılarak alınabilir <xref:System.Windows.Controls.Primitives.LayoutInformation.GetLayoutSlot%2A> . Aşağıdaki çizimde öğesi için sınırlayıcı kutusu gösterilmektedir <xref:System.Windows.Controls.TextBlock> .

![TextBlock sınırlayıcı kutusunun artık görünür olduğunu gösteren ekran görüntüsü.](./media/layout/visible-textblock-bounding-box.png)

Sarı dikdörtgende gösterildiği gibi, öğe için ayrılan alan, <xref:System.Windows.Controls.TextBlock> gerçekten görüntülenenden çok daha büyük olur. Öğesine ek öğeler eklendikçe, <xref:System.Windows.Controls.Grid> eklenen öğelerin türüne ve boyutuna bağlı olarak bu ayırma küçülebilir veya genişleyebilir.

Öğesinin düzen yuvası <xref:System.Windows.Controls.TextBlock> <xref:System.Windows.Shapes.Path> yöntemi kullanılarak öğesine çevrilir <xref:System.Windows.Controls.Primitives.LayoutInformation.GetLayoutSlot%2A> . Bu teknik, bir öğenin sınırlayıcı kutusunu görüntülemek için yararlı olabilir.

[!code-csharp[LayoutInformation#2](~/samples/snippets/csharp/VS_Snippets_Wpf/LayoutInformation/CSharp/Window1.xaml.cs#2)]
[!code-vb[LayoutInformation#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/LayoutInformation/VisualBasic/Window1.xaml.vb#2)]

<a name="LayoutSystem_Overview"></a>

## <a name="the-layout-system"></a>Düzen sistemi

En basit olan düzen, boyutlandırılmış, konumlandırılmış ve çizilmiş bir öğeye yol gösteren özyinelemeli bir sistemdir. Daha belirgin olarak, düzen bir öğe koleksiyonunun üyelerini ölçme ve düzenleme sürecini açıklar <xref:System.Windows.Controls.Panel> <xref:System.Windows.Controls.Panel.Children%2A> . Düzen yoğun bir işlemdir. Koleksiyon ne kadar büyükse <xref:System.Windows.Controls.Panel.Children%2A> , yapılması gereken hesaplamaların sayısı artar. Karmaşıklık, <xref:System.Windows.Controls.Panel> koleksiyona sahip olan öğe tarafından tanımlanan düzen davranışına göre de kullanıma sunulmuştur. Gibi görece basit <xref:System.Windows.Controls.Panel> <xref:System.Windows.Controls.Canvas> olan, gibi daha karmaşık bir performansa sahip olabilir <xref:System.Windows.Controls.Panel> <xref:System.Windows.Controls.Grid> .

Bir alt öğe konumunu her <xref:System.Windows.UIElement> değiştirdiğinde, Düzen sistemi tarafından yeni bir geçiş tetiklenmesi olası olur. Bu nedenle, gereksiz çağrı kötü uygulama performansına neden olabileceği için, düzen sistemini çağırabilen olayları anlamak önemlidir. Aşağıda, Düzen sistemi çağrıldığında gerçekleşen işlem açıklanmaktadır.

1. Alt öğe <xref:System.Windows.UIElement> , öncelikle temel özellikleri ölçülerek düzen işlemini başlatır.

2. Üzerinde tanımlanan boyutlandırma özellikleri,, <xref:System.Windows.FrameworkElement> ve gibi değerlendirilir <xref:System.Windows.FrameworkElement.Width%2A> <xref:System.Windows.FrameworkElement.Height%2A> <xref:System.Windows.FrameworkElement.Margin%2A> .

3. <xref:System.Windows.Controls.Panel>Yön veya yığınlama gibi belirli bir Logic uygulandı <xref:System.Windows.Controls.Dock> <xref:System.Windows.Controls.StackPanel.Orientation%2A> .

4. İçerik tüm alt öğeler ölçülerek düzenlenir.

5. <xref:System.Windows.Controls.Panel.Children%2A>Koleksiyon ekranda çizilir.

6. İşlem, <xref:System.Windows.Controls.Panel.Children%2A> koleksiyona ek eklenirse, bir <xref:System.Windows.FrameworkElement.LayoutTransform%2A> uygulanmışsa veya <xref:System.Windows.UIElement.UpdateLayout%2A> yöntemi çağrıldığında yeniden çağrılır.

Bu işlem ve nasıl çağrıldığı, aşağıdaki bölümlerde daha ayrıntılı olarak tanımlanmıştır.

<a name="LayoutSystem_Measure_Arrange"></a>

## <a name="measuring-and-arranging-children"></a>Alt öğeleri ölçme ve düzenleme

Düzen sistemi, koleksiyonun her üyesi için iki geçişi tamamlar <xref:System.Windows.Controls.Panel.Children%2A> , bir ölçü geçti ve bir düzenleme geçişi. Her alt öğe kendi <xref:System.Windows.Controls.Panel> <xref:System.Windows.FrameworkElement.MeasureOverride%2A> <xref:System.Windows.FrameworkElement.ArrangeOverride%2A> özel düzen davranışına ulaşmak için kendi ve yöntemlerini sağlar.

Ölçü geçişi sırasında koleksiyonun her üyesi <xref:System.Windows.Controls.Panel.Children%2A> değerlendirilir. İşlem yöntemi çağrısıyla başlar <xref:System.Windows.UIElement.Measure%2A> . Bu yöntem, üst öğe uygulamasının içinde çağrılır <xref:System.Windows.Controls.Panel> ve düzen gerçekleşmesi için açıkça çağrılması gerekmez.

İlk olarak, öğesinin yerel boyut özellikleri <xref:System.Windows.UIElement> değerlendirilir, <xref:System.Windows.UIElement.Clip%2A> ve gibi <xref:System.Windows.UIElement.Visibility%2A> . Bu, öğesine geçirilen adlı bir değer oluşturur `constraintSize` <xref:System.Windows.FrameworkElement.MeasureCore%2A> .

İkinci olarak, üzerinde tanımlanan çerçeve özellikleri <xref:System.Windows.FrameworkElement> işlenir ve bu değerini etkiler `constraintSize` . Bu özellikler genellikle,,, ve gibi temeldeki boyut özelliklerini anlatmaktadır <xref:System.Windows.UIElement> <xref:System.Windows.FrameworkElement.Height%2A> <xref:System.Windows.FrameworkElement.Width%2A> <xref:System.Windows.FrameworkElement.Margin%2A> <xref:System.Windows.FrameworkElement.Style%2A> . Bu özelliklerin her biri, öğesini göstermek için gereken alanı değiştirebilir. <xref:System.Windows.FrameworkElement.MeasureOverride%2A>daha sonra `constraintSize` parametresi olarak çağırılır.

> [!NOTE]
> Ve ve özelliklerinin özellikleri arasında bir farklılık vardır <xref:System.Windows.FrameworkElement.Height%2A> <xref:System.Windows.FrameworkElement.Width%2A> <xref:System.Windows.FrameworkElement.ActualHeight%2A> <xref:System.Windows.FrameworkElement.ActualWidth%2A> . Örneğin, <xref:System.Windows.FrameworkElement.ActualHeight%2A> özellik diğer yükseklik girdilerine ve Düzen sistemine göre hesaplanan bir değerdir. Değer, gerçek bir işleme geçişine göre düzen sisteminin kendisi tarafından ayarlanır ve bu nedenle, örneğin <xref:System.Windows.FrameworkElement.Height%2A> , giriş değişikliğinin temelini oluşturan özellikler kümesi değeri biraz daha geride olabilir.
>
> <xref:System.Windows.FrameworkElement.ActualHeight%2A>Hesaplanan bir değer olduğundan, Düzen sistemine göre çeşitli işlemlere neden olarak, üzerinde birden fazla veya artımlı bildirilen değişiklik olduğunu bilmelisiniz. Düzen sistemi, alt öğeler için gerekli ölçü alanını, üst öğeye göre kısıtlamaları ve bu şekilde hesaplamayı gösterebilir.

Ölçüm geçişinin nihai hedefi, alt öğesi, <xref:System.Windows.UIElement.DesiredSize%2A> çağrı sırasında oluşan öğesini tespit etmek için kullanılır <xref:System.Windows.FrameworkElement.MeasureCore%2A> . <xref:System.Windows.UIElement.DesiredSize%2A>Değer, <xref:System.Windows.UIElement.Measure%2A> içerik düzenleme geçişi sırasında kullanılmak üzere tarafından depolanır.

Düzenleme geçişi, yöntemi çağrısıyla başlar <xref:System.Windows.UIElement.Arrange%2A> . Düzenleme geçişi sırasında, üst <xref:System.Windows.Controls.Panel> öğe alt öğenin sınırlarını temsil eden bir dikdörtgen oluşturur. Bu değer, <xref:System.Windows.FrameworkElement.ArrangeCore%2A> işleme yöntemine geçirilir.

<xref:System.Windows.FrameworkElement.ArrangeCore%2A>Yöntemi, <xref:System.Windows.UIElement.DesiredSize%2A> alt öğesini değerlendirir ve öğenin işlenmiş boyutunu etkileyebilecek ek kenar boşluklarını değerlendirir. <xref:System.Windows.FrameworkElement.ArrangeCore%2A>`arrangeSize` <xref:System.Windows.FrameworkElement.ArrangeOverride%2A> parametresi olarak yöntemine geçirilen bir oluşturur <xref:System.Windows.Controls.Panel> . <xref:System.Windows.FrameworkElement.ArrangeOverride%2A>`finalSize`alt öğesinin öğesini oluşturur. Son olarak, <xref:System.Windows.FrameworkElement.ArrangeCore%2A> yöntemi kenar boşluğu ve hizalama gibi bir sınır özelliği değerlendirmesi yapar ve alt öğesini Düzen yuvasının içine koyar. Alt öğe, ayrılan alanın tamamını doldurmalı (ve sık değil). Sonra Denetim üst öğeye döndürülür <xref:System.Windows.Controls.Panel> ve düzen işlemi tamamlanmıştır.

<a name="LayoutSystem_PanelsCustom"></a>

## <a name="panel-elements-and-custom-layout-behaviors"></a>Panel öğeleri ve özel düzen davranışları

WPF, öğesinden türetilen bir öğe grubunu içerir <xref:System.Windows.Controls.Panel> . Bu <xref:System.Windows.Controls.Panel> öğeler birçok karmaşık düzeni etkinleştirir. Örneğin, yığın öğeleri öğesi kullanılarak kolayca elde edilebilir <xref:System.Windows.Controls.StackPanel> , ancak daha karmaşık ve ücretsiz akış düzenleri bir kullanılarak yapılabilir <xref:System.Windows.Controls.Canvas> .

Aşağıdaki tabloda kullanılabilir Düzen <xref:System.Windows.Controls.Panel> öğeleri özetlenmektedir.

|Panel adı|Açıklama|
|----------------|-----------------|
|<xref:System.Windows.Controls.Canvas>|Alt öğeleri alana göreli olarak açıkça konumlandırabileceğiniz bir alan tanımlar <xref:System.Windows.Controls.Canvas> .|
|<xref:System.Windows.Controls.DockPanel>|Alt öğeleri yatay veya dikey olarak birbirlerine göre düzenleyebileceğiniz bir alan tanımlar.|
|<xref:System.Windows.Controls.Grid>|Sütun ve satırlardan oluşan esnek bir kılavuz alanı tanımlar.|
|<xref:System.Windows.Controls.StackPanel>|Alt öğeleri yatay veya dikey olarak yönelimli tek bir satıra yerleştirir.|
|<xref:System.Windows.Controls.VirtualizingPanel>|<xref:System.Windows.Controls.Panel>Alt veri koleksiyonlarını sanallaştıran öğeler için bir çerçeve sağlar. Bu soyut bir sınıftır.|
|<xref:System.Windows.Controls.WrapPanel>|Sol taraftaki alt öğeleri, kapsayan kutunun kenarındaki bir sonraki satıra kadar olan sıralı konumda konumlandırır. Sonraki sıralama, özelliğin değerine bağlı olarak yukarıdan aşağıya veya sağdan sola doğru bir şekilde gerçekleşir <xref:System.Windows.Controls.WrapPanel.Orientation%2A> .|

Önceden tanımlanmış öğelerden herhangi birini kullanarak mümkün olmayan bir düzen gerektiren uygulamalar için <xref:System.Windows.Controls.Panel> , ve yöntemlerini devralarak ve geçersiz kılarak özel düzen davranışları elde edilebilir <xref:System.Windows.Controls.Panel> <xref:System.Windows.FrameworkElement.MeasureOverride%2A> <xref:System.Windows.FrameworkElement.ArrangeOverride%2A> .

<a name="LayoutSystem_Performance"></a>

## <a name="layout-performance-considerations"></a>Düzen performansı konuları

Düzen özyinelemeli bir işlemdir. Bir koleksiyondaki her alt öğe <xref:System.Windows.Controls.Panel.Children%2A> , düzen sisteminin her çağrılması sırasında işlenir. Sonuç olarak, gerekli olmadığında düzen sisteminin tetiklenmesi gerekir. Aşağıdaki noktalar daha iyi performans elde etmenize yardımcı olabilir.

- Hangi özellik değeri değişikliklerinin düzen sistemi tarafından özyinelemeli güncelleştirme zorlayacaktır.

  Değerleri, düzen sisteminin başlatılmasına neden olabilecek bağımlılık özellikleri, ortak bayraklarla işaretlenir. <xref:System.Windows.FrameworkPropertyMetadata.AffectsMeasure%2A>ve <xref:System.Windows.FrameworkPropertyMetadata.AffectsArrange%2A> hangi özellik değeri değişikliklerinin düzen sistemi tarafından özyinelemeli bir güncelleştirme zoracağı konusunda yararlı ipuçları sağlar. Genel olarak, bir öğenin sınırlayıcı kutusunun boyutunu etkileyebilecek herhangi bir özelliğin, <xref:System.Windows.FrameworkPropertyMetadata.AffectsMeasure%2A> true olarak ayarlanmış bir bayrağı olmalıdır. Daha fazla bilgi için bkz. [bağımlılık özelliklerine genel bakış](dependency-properties-overview.md).

- Mümkün olduğunda, yerine bir kullanın <xref:System.Windows.UIElement.RenderTransform%2A> <xref:System.Windows.FrameworkElement.LayoutTransform%2A> .

  Bir <xref:System.Windows.FrameworkElement.LayoutTransform%2A> , içeriğini etkilemek için çok kullanışlı bir yol olabilir [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] . Ancak, dönüşümün etkisinin diğer öğelerin konumunu etkilemesi gerekmez, <xref:System.Windows.UIElement.RenderTransform%2A> çünkü <xref:System.Windows.UIElement.RenderTransform%2A> düzen sistemini çağırmaz, bunun yerine bunun kullanılması en iyisidir. <xref:System.Windows.FrameworkElement.LayoutTransform%2A>dönüşümünü uygular ve etkilenen öğenin yeni konumu için bir özyinelemeli Düzen güncelleştirmesini hesaba zorlar.

- İçin gereksiz çağrılardan kaçının <xref:System.Windows.UIElement.UpdateLayout%2A> .

  <xref:System.Windows.UIElement.UpdateLayout%2A>Yöntemi özyinelemeli bir Düzen güncelleştirmesini zorlar ve genellikle gerekli değildir. Tam bir güncelleştirmenin gerekli olduğundan emin olmadığınız için, bu yöntemi sizin için çağırmak üzere Düzen sistemine güvenin.

- Büyük bir <xref:System.Windows.Controls.Panel.Children%2A> koleksiyonla çalışırken, normal yerine bir kullanmayı düşünün <xref:System.Windows.Controls.VirtualizingStackPanel> <xref:System.Windows.Controls.StackPanel> .

  Alt koleksiyonu sanallaştırarak, <xref:System.Windows.Controls.VirtualizingStackPanel> yalnızca üst öğe görünüm içerisindeki bellekteki nesneleri tutar. Sonuç olarak, Çoğu senaryoda performans önemli ölçüde geliştirilmiştir.

<a name="LayoutSystem_LayoutRounding"></a>

## <a name="sub-pixel-rendering-and-layout-rounding"></a>Alt piksel Işleme ve yerleşim yuvarlama

WPF Grafik sistemi, çözümleme ve cihaz bağımsızlığını etkinleştirmek için cihazdan bağımsız birimler kullanır. Her cihazdan bağımsız piksel, sistemin nokta/inç (dpi) ayarıyla otomatik olarak ölçeklendirilir. Bu, WPF uygulamalarına farklı DPI ayarları için uygun ölçeklendirmeyi sağlar ve uygulamayı otomatik olarak DPI duyarlı hale getirir.

Ancak, bu DPI bağımsızlık, kenar yumuşatma nedeniyle düzensiz kenar işleme oluşturabilir. Genellikle bulanık veya yarı saydam kenarlar olarak görülen bu yapıtlar, bir kenarın konumu cihaz pikselleri arasında değil bir cihaz pikseli ortasında kaldığında gerçekleşebilir. Düzen sistemi, düzen yuvarlama ile bunu yapmak için bir yol sağlar. Düzen yuvarlama, düzen sisteminin, düzen geçişi sırasında tam sayı olmayan piksel değerlerini yuvarlar.

Düzen yuvarlama varsayılan olarak devre dışıdır. Düzen yuvarlamayı etkinleştirmek için <xref:System.Windows.FrameworkElement.UseLayoutRounding%2A> özelliği `true` herhangi bir üzerinde olarak ayarlayın <xref:System.Windows.FrameworkElement> . Bir bağımlılık özelliği olduğundan, değer görsel ağaçtaki tüm alt öğelere yayılır. Tüm Kullanıcı arabiriminin düzen yuvarlamayı etkinleştirmek için, <xref:System.Windows.FrameworkElement.UseLayoutRounding%2A> `true` kök kapsayıcısında olarak ayarlayın. Örnek için bkz. <xref:System.Windows.FrameworkElement.UseLayoutRounding%2A>

<a name="LayoutSystem_whatsnext"></a>

## <a name="whats-next"></a>Sırada Ne Var?

Öğelerin nasıl ölçüleceğini ve düzenlenmesini anlamak, düzeni anlamak için ilk adımdır. Kullanılabilir öğeler hakkında daha fazla bilgi için <xref:System.Windows.Controls.Panel> bkz. [panellere genel bakış](../controls/panels-overview.md). Düzeni etkileyebilecek çeşitli konumlandırma özelliklerini daha iyi anlamak için bkz. [Hizalama, kenar boşlukları ve doldurmaya genel bakış](alignment-margins-and-padding-overview.md). Bunu hafif bir uygulamada bir araya getirmek için hazırsanız, bkz. [Izlenecek yol: Ilk WPF Masaüstü](../getting-started/walkthrough-my-first-wpf-desktop-application.md)Uygulamam.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.FrameworkElement>
- <xref:System.Windows.UIElement>
- [Panellere Genel Bakış](../controls/panels-overview.md)
- [Hizalama, Kenar Boşlukları ve Doldurmaya Genel Bakış](alignment-margins-and-padding-overview.md)
- [Düzen ve Tasarım](optimizing-performance-layout-and-design.md)
