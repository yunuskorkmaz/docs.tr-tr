---
title: Panellere Genel Bakış
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Panel control [WPF], about Panel control
- controls [WPF], Panel
ms.assetid: f73644af-9941-4611-8754-6d4cef03fc44
ms.openlocfilehash: 7810bfbf4f5bedf51e0797a4b9017f589e0b0a8a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187588"
---
# <a name="panels-overview"></a>Panellere Genel Bakış
<xref:System.Windows.Controls.Panel>öğeler, öğelerin boyut ve boyutlarını, konumlarını ve alt içeriklerinin düzenlenmesini kontrol eden bileşenlerdir. Önceden [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] tanımlanmış <xref:System.Windows.Controls.Panel> öğelerin bir dizi yanı sıra özel <xref:System.Windows.Controls.Panel> öğeler oluşturmak için yeteneği sağlar.  
  
 Bu konuda aşağıdaki bölümler yer almaktadır.  
  
- [Panel Sınıfı](#Panels_view_from_10000_feet)  
  
- [Panel Elemanı Ortak Üyeler](#Panels_declared_members)  
  
- [Türemiş Panel Elemanları](#Panels_derived_elements)  
  
- [Kullanıcı Arayüz Panelleri](#Panels_main_UI_elements)  
  
- [İç Içe Panel Elemanları](#Panels_nested_panel_elements)  
  
- [Özel Panel Elemanları](#Panels_custom_panel_elements)  
  
- [Yerelleştirme/Küreselleşme Desteği](#Panels_global_localization)  
  
<a name="Panels_view_from_10000_feet"></a>
## <a name="the-panel-class"></a>Panel Sınıfı  
 <xref:System.Windows.Controls.Panel>' de [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]düzen desteği sağlayan tüm öğeler için taban sınıftır. Türemiş <xref:System.Windows.Controls.Panel> öğeler, öğeleri konumlandırmak [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] ve düzenlemek ve kodlamak için kullanılır.  
  
 Birçok [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] karmaşık düzenleri etkinleştirmek türemiş panel uygulamaları kapsamlı bir paketi içerir. Bu türemiş sınıflar, çoğu [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] standart senaryoyu etkinleştiren özellikleri ve yöntemleri ortaya çıkarır. Gereksinimlerini karşılayan bir alt düzenleme davranışı bulamayan geliştiriciler, bu ve <xref:System.Windows.FrameworkElement.ArrangeOverride%2A> <xref:System.Windows.FrameworkElement.MeasureOverride%2A> yöntemleri geçersiz kılarak yeni düzenler oluşturabilir. Özel düzen davranışları hakkında daha fazla bilgi için [Bkz. Özel Panel Öğeleri.](#Panels_custom_panel_elements)  
  
<a name="Panels_declared_members"></a>
## <a name="panel-common-members"></a>Panel Ortak Üyeleri  
 Tüm <xref:System.Windows.Controls.Panel> <xref:System.Windows.FrameworkElement>öğeler, <xref:System.Windows.FrameworkElement.Height%2A>, , <xref:System.Windows.FrameworkElement.Width%2A> <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> <xref:System.Windows.FrameworkElement.Margin%2A>, , , ve <xref:System.Windows.FrameworkElement.LayoutTransform%2A>. Tarafından <xref:System.Windows.FrameworkElement>tanımlanan konumlandırma özellikleri hakkında ek bilgi için bkz: [Hizalama, Kenar Boşlukları ve Dolgu Genel Bakışı.](../advanced/alignment-margins-and-padding-overview.md)  
  
 <xref:System.Windows.Controls.Panel>düzeni anlama ve kullanmada kritik öneme sahip ek özellikler ortaya çıkarır. Özellik, <xref:System.Windows.Controls.Panel.Background%2A> türetilmiş bir panel öğesinin sınırları arasındaki alanı <xref:System.Windows.Media.Brush>bir . <xref:System.Windows.Controls.Panel.Children%2A>oluşan öğelerin <xref:System.Windows.Controls.Panel> alt koleksiyonunu temsil eder. <xref:System.Windows.Controls.Panel.InternalChildren%2A><xref:System.Windows.Controls.Panel.Children%2A> toplama nın içeriğini ve veri bağlama tarafından oluşturulan üyeleri temsil eder. Her ikisi <xref:System.Windows.Controls.UIElementCollection> de ebeveyn <xref:System.Windows.Controls.Panel>içinde barındırılan alt öğelerden oluşur.  
  
 Panel ayrıca türetilmiş <xref:System.Windows.Controls.Panel.ZIndex%2A?displayProperty=nameWithType> <xref:System.Windows.Controls.Panel>bir sırada katmanlı sipariş elde etmek için kullanılabilecek ekli bir özelliği ortaya çıkarır. Daha yüksek <xref:System.Windows.Controls.Panel.Children%2A> <xref:System.Windows.Controls.Panel.ZIndex%2A?displayProperty=nameWithType> değere sahip bir panelin koleksiyonunun üyeleri, <xref:System.Windows.Controls.Panel.ZIndex%2A?displayProperty=nameWithType> daha düşük değere sahip olanların önünde görünür. Bu, özellikle çocukların aynı <xref:System.Windows.Controls.Canvas> koordinat <xref:System.Windows.Controls.Grid> alanını paylaşmasına olanak tanıyan ve paneller için kullanışlıdır.  
  
 <xref:System.Windows.Controls.Panel><xref:System.Windows.Controls.Panel.OnRender%2A> ayrıca, bir <xref:System.Windows.Controls.Panel>.  
  
#### <a name="attached-properties"></a>Ekli Özellikler  
 Türetilmiş panel elemanları ekli özellikleri geniş ölçüde kullanır. Ekli özellik, geleneksel ortak dil çalışma zamanı (CLR) özelliği "sarmalayıcısı" olmayan özel bir bağımlılık özelliği biçimidir. Eklenmiş özellikleri, aşağıdaki örneklerin [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]birkaç görülebilir özel bir sözdizimi var.  
  
 Ekli bir özelliğin bir amacı, alt öğelerin aslında bir üst öğe tarafından tanımlanan bir özelliğin benzersiz değerlerini depolamak için izin vermektir. Bu işlevselliğin bir uygulama alt öğeleri nasıl sunulmasını istediğinizi [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]ebeveyn bilgilendirmek olmasıdır , hangi uygulama düzeni için son derece yararlıdır. Daha fazla bilgi için [bkz.](../advanced/attached-properties-overview.md)  
  
<a name="Panels_derived_elements"></a>
## <a name="derived-panel-elements"></a>Türemiş Panel Elemanları  
 Birçok nesne, ancak <xref:System.Windows.Controls.Panel>hepsi kök düzeni sağlayıcıları olarak kullanılmak üzere tasarlanmıştır türetilmiştir. <xref:System.Windows.Controls.Canvas>Uygulama [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]oluşturmak için özel <xref:System.Windows.Controls.DockPanel>olarak <xref:System.Windows.Controls.Grid> <xref:System.Windows.Controls.StackPanel>tasarlanmış <xref:System.Windows.Controls.VirtualizingStackPanel>altı tanımlı panel sınıfı (, , , , , ve <xref:System.Windows.Controls.WrapPanel>) vardır.  
  
 Her panel öğesi, aşağıdaki tabloda görüldüğü gibi kendi özel işlevini saklar.  
  
|Öğe Adı|UI Paneli mi?|Açıklama|  
|------------------|---------------|-----------------|  
|<xref:System.Windows.Controls.Canvas>|Evet|Alt öğeleri <xref:System.Windows.Controls.Canvas> alana göre koordinatlara göre açıkça konumlandırabileceğiniz bir alan tanımlar.|  
|<xref:System.Windows.Controls.DockPanel>|Evet|Alt öğeleri yatay veya dikey olarak, birbirlerine göre düzenleyebileceğiniz bir alan tanımlar.|  
|<xref:System.Windows.Controls.Grid>|Evet|Sütunlar ve satırlardan oluşan esnek bir ızgara alanı tanımlar. A'nın <xref:System.Windows.Controls.Grid> alt öğeleri <xref:System.Windows.FrameworkElement.Margin%2A> özelliği kullanılarak tam olarak konumlandırılabilir.|  
|<xref:System.Windows.Controls.StackPanel>|Evet|Alt öğeleri yatay veya dikey olarak yönlendirilebilen tek bir satıra düzenler.|  
|<xref:System.Windows.Controls.Primitives.TabPanel>|Hayır|Sekme düğmelerinin düzenini bir <xref:System.Windows.Controls.TabControl>' deki işler.|  
|<xref:System.Windows.Controls.Primitives.ToolBarOverflowPanel>|Hayır|İçeriği bir <xref:System.Windows.Controls.ToolBar> denetim içinde düzenler.|  
|<xref:System.Windows.Controls.Primitives.UniformGrid>|Hayır|<xref:System.Windows.Controls.Primitives.UniformGrid>tüm eşit hücre boyutlarına sahip bir ızgarada çocukları düzenlemek için kullanılır.|  
|<xref:System.Windows.Controls.VirtualizingPanel>|Hayır|Alt koleksiyonlarını "sanallaştırabilen" paneller için bir taban sınıf sağlar.|  
|<xref:System.Windows.Controls.VirtualizingStackPanel>|Evet|İçeriği yatay veya dikey olarak tek bir satırda düzenler ve sanallaştırır.|  
|<xref:System.Windows.Controls.WrapPanel>|Evet|<xref:System.Windows.Controls.WrapPanel>alt öğeleri soldan sağa sıralı konuma yerleştirerek içeriği içeren kutunun kenarındaki bir sonraki satıra ayırArak konumlandırın. Sonraki sıralama, <xref:System.Windows.Controls.WrapPanel.Orientation%2A> özelliğin değerine bağlı olarak yukarıdan aşağıya veya sağdan sola sırayla gerçekleşir.|  
  
<a name="Panels_main_UI_elements"></a>
## <a name="user-interface-panels"></a>Kullanıcı Arayüz Panelleri  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Senaryoları desteklemek [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] için optimize edilmiş altı panel sınıfı <xref:System.Windows.Controls.Canvas> <xref:System.Windows.Controls.DockPanel>vardır: <xref:System.Windows.Controls.StackPanel> <xref:System.Windows.Controls.VirtualizingStackPanel>, <xref:System.Windows.Controls.WrapPanel>, <xref:System.Windows.Controls.Grid>, , ve . Bu panel elemanlarının kullanımı kolay, çok yönlü ve çoğu uygulama için yeterince genişletilebilir.  
  
 Her <xref:System.Windows.Controls.Panel> türemiş öğe boyutlandırma kısıtlamaları farklı davranır. Yatay veya <xref:System.Windows.Controls.Panel> dikey yöndeki kısıtlamaları nasıl işlediğianlamak düzeni daha öngörülebilir hale getirebilir.  
  
|**Panel Adı**|**x-Boyut**|**y-Boyut**|  
|--------------------|----------------------|----------------------|  
|<xref:System.Windows.Controls.Canvas>|İçerir ile sınırlandırılmıştır|İçerir ile sınırlandırılmıştır|  
|<xref:System.Windows.Controls.DockPanel>|Kısıtlı|Kısıtlı|  
|<xref:System.Windows.Controls.StackPanel>(Dikey Yönlendirme)|Kısıtlı|İçerir ile sınırlandırılmıştır|  
|<xref:System.Windows.Controls.StackPanel>(Yatay Yönlendirme)|İçerir ile sınırlandırılmıştır|Kısıtlı|  
|<xref:System.Windows.Controls.Grid>|Kısıtlı|Satır lar ve sütunlar <xref:System.Windows.GridUnitType.Auto> için geçerli olduğu durumlar dışında, kısıtlanmış|  
|<xref:System.Windows.Controls.WrapPanel>|İçerir ile sınırlandırılmıştır|İçerir ile sınırlandırılmıştır|  
  
 Bu öğelerin her birinin daha ayrıntılı açıklamaları ve kullanım örneklerini aşağıda bulabilirsiniz.  
  
<a name="Panels_overview_Canvas_subsection"></a>
### <a name="canvas"></a>Tuval  
 Öğe, <xref:System.Windows.Controls.Canvas> içeriğin mutlak *x-* ve *y-* koordinatlarına göre konumlandırılmasını sağlar. Öğeler benzersiz bir konumda çizilebilir; veya öğeler aynı koordinatları kapsa, biçimlendirmede göründükleri sıra, öğelerin çizilme sırasını belirler.  
  
 <xref:System.Windows.Controls.Canvas>herhangi bir <xref:System.Windows.Controls.Panel>en esnek düzen desteği sağlar. Yükseklik ve Genişlik özellikleri tuval alanını tanımlamak için kullanılır ve içindeki öğeler üst <xref:System.Windows.Controls.Canvas>alana göre mutlak koordinatlar atanır. Dört <xref:System.Windows.Controls.Canvas.Left%2A?displayProperty=nameWithType>ekli özellik, <xref:System.Windows.Controls.Canvas.Top%2A?displayProperty=nameWithType> <xref:System.Windows.Controls.Canvas.Right%2A?displayProperty=nameWithType> , <xref:System.Windows.Controls.Canvas.Bottom%2A?displayProperty=nameWithType>, ve , bir <xref:System.Windows.Controls.Canvas>içinde nesne yerleşimince kontrol sağlar , geliştirici konumlandırmak ve ekranda tam olarak öğeleri düzenlemek için izin.  
  
#### <a name="cliptobounds-within-a-canvas"></a>Tuval İçindeki ClipToBounds  
 <xref:System.Windows.Controls.Canvas>kendi tanımladığı <xref:System.Windows.FrameworkElement.Height%2A> ve <xref:System.Windows.FrameworkElement.Width%2A>dışında koordinatlarda bile, ekranda herhangi bir pozisyonda alt öğeleri konumlandırabilirsiniz. Ayrıca, <xref:System.Windows.Controls.Canvas> çocuklarının boyutu etkilenmez. Sonuç olarak, bir alt öğenin üst <xref:System.Windows.Controls.Canvas>öğenin sınırlayıcı dikdörtgendışında diğer öğeleri abartması mümkündür. A'nın <xref:System.Windows.Controls.Canvas> varsayılan davranışı, çocukların ebeveynin <xref:System.Windows.Controls.Canvas>sınırlarının dışına çekilmesine izin vermektir. Bu davranış istenmiyorsa, <xref:System.Windows.UIElement.ClipToBounds%2A> özellik `true`' e ayarlanabilir. Bu, <xref:System.Windows.Controls.Canvas> kendi boyutuna klip neden olur. <xref:System.Windows.Controls.Canvas>çocukların sınırlarının dışına çekilmesini sağlayan tek düzen öğesidir.  
  
 Bu [davranış, Genişlik Özellikleri Karşılaştırma Örneğinde](https://github.com/Microsoft/WPF-Samples/tree/master/Elements/WidthProperties)grafik olarak gösterilmiştir.  
  
#### <a name="defining-and-using-a-canvas"></a>Tuval Tanımlama ve Kullanma  
 A <xref:System.Windows.Controls.Canvas> sadece kullanarak [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] veya kod kullanılarak anlık olabilir. Aşağıdaki örnek, içeriği kesinlikle <xref:System.Windows.Controls.Canvas> konumlandırmak için nasıl kullanılacağını göstermektedir. Bu kod üç 100 piksel kare üretir. İlk kare kırmızıdır ve sol üstteki *(x, y)* konumu (0, 0) olarak belirtilir. İkinci kare yeşildir ve sol üstteki konumu (100, 100), ilk karenin hemen altında ve sağındadır. Üçüncü kare mavidir ve sol üst konumu (50, 50), böylece ilk karenin sağ alt kadranda ve ikincinin sol üst kadrandasını kapsar. Üçüncü kare en son ortaya konulduğu için, diğer iki karenin üstünde gibi görünür,yani çakışan kısımlar üçüncü kutunun rengini varsayar.  
  
 [!code-csharp[CanvasOvwSample#1](~/samples/snippets/csharp/VS_Snippets_Wpf/CanvasOvwSample/CSharp/Canvas_Ovw_Sample.cs#1)]
 [!code-vb[CanvasOvwSample#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CanvasOvwSample/VisualBasic/canvas_vb.vb#1)]
 [!code-xaml[CanvasOvwSample#1](~/samples/snippets/xaml/VS_Snippets_Wpf/CanvasOvwSample/XAML/default.xaml#1)]  
  
 Derlenen uygulama, bu [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] gibi görünen yeni bir sonuç verir.  
  
 ![Tipik bir Tuval Öğesi.](./media/panel-intro-canvas.PNG "panel_intro_canvas")  
  
<a name="Panels_overview_DockPanel_subsection"></a>
### <a name="dockpanel"></a>DockPanel  
 Öğe, <xref:System.Windows.Controls.DockPanel> içeriği <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType> kapsayıcının kenarlarına yerleştirmek için alt içerik öğelerinde ayarlanan ekli özelliği kullanır. Ne <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType> zaman <xref:System.Windows.Controls.Dock.Top> ayarlanır <xref:System.Windows.Controls.Dock.Bottom>veya , birbirinin üstünde veya altında alt alt alt çocuk öğeleri konumlandırın. Ne <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType> zaman <xref:System.Windows.Controls.Dock.Left> ayarlanır <xref:System.Windows.Controls.Dock.Right>veya , birbirinin solunda veya sağına alt öğeleri konumlandırın. Özellik, <xref:System.Windows.Controls.DockPanel.LastChildFill%2A> bir <xref:System.Windows.Controls.DockPanel>çocuğun çocuğu olarak eklenen son öğenin konumunu belirler.  
  
 Düğme kümesi <xref:System.Windows.Controls.DockPanel> gibi ilgili denetimler grubunu konumlandırmak için kullanabilirsiniz. Alternatif olarak, Microsoft Outlook'ta bulunana [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]benzer bir "paned" oluşturmak için kullanabilirsiniz.  
  
#### <a name="sizing-to-content"></a>İçerime Boyutlandırma  
 Özellikleri <xref:System.Windows.FrameworkElement.Height%2A> belirtilmemişse, <xref:System.Windows.FrameworkElement.Width%2A> <xref:System.Windows.Controls.DockPanel> içeriğine göre boyutlanır. Boyutu artırabilir veya onun alt öğelerin boyutunu karşılamak için azalabilir. Ancak, bu özellikler belirtildiğinde ve bir sonraki belirtilen alt <xref:System.Windows.Controls.DockPanel> öğe için artık yer olmadığında, bu alt öğeyi veya sonraki alt öğeleri görüntülemez ve sonraki alt öğeleri ölçmez.  
  
#### <a name="lastchildfill"></a>SonChildFill  
 Varsayılan olarak, bir <xref:System.Windows.Controls.DockPanel> öğenin son alt kalan, ayrılmamış alanı "dolduracak". Bu davranış istenmiyorsa, <xref:System.Windows.Controls.DockPanel.LastChildFill%2A> `false`özelliği ' ye ayarla.  
  
#### <a name="defining-and-using-a-dockpanel"></a>DockPanel Tanımlama ve Kullanma  
 Aşağıdaki örnek, bir <xref:System.Windows.Controls.DockPanel>. Bir <xref:System.Windows.Controls.Border> ebeveynin <xref:System.Windows.Controls.DockPanel>çocukları olarak beş öğe eklenir. Her biri, bölüm alanı <xref:System.Windows.Controls.DockPanel> için farklı bir konumlandırma özelliği kullanır. Son öğe kalan, ayrılmamış alanı "doldurur".  
  
 [!code-cpp[DockPanelOvwSample#1](~/samples/snippets/cpp/VS_Snippets_Wpf/DockPanelOvwSample/CPP/DockPanel_Ovw_Sample.cpp#1)]
 [!code-csharp[DockPanelOvwSample#1](~/samples/snippets/csharp/VS_Snippets_Wpf/DockPanelOvwSample/CSharp/DockPanel_Ovw_Sample.cs#1)]
 [!code-vb[DockPanelOvwSample#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DockPanelOvwSample/VisualBasic/dockpanel_vb.vb#1)]
 [!code-xaml[DockPanelOvwSample#1](~/samples/snippets/xaml/VS_Snippets_Wpf/DockPanelOvwSample/XAML/default.xaml#1)]  
  
 Derlenen uygulama, bu [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] gibi görünen yeni bir sonuç verir.  
  
 ![Tipik bir DockPanel senaryosu.](./media/panel-intro-dockpanel.PNG "panel_intro_dockpanel")  
  
<a name="Panels_overview_Grid_subsection"></a>
### <a name="grid"></a>Kılavuz  
 Öğe, <xref:System.Windows.Controls.Grid> mutlak konumlandırma ve tabular veri denetimi işlevselliğini birleştirir. A, <xref:System.Windows.Controls.Grid> öğeleri kolayca konumlandırmanızı ve stil haline getirebilmenizi sağlar. <xref:System.Windows.Controls.Grid>esnek satır ve sütun gruplandırmaları tanımlamanızı sağlar ve hatta boyutlandırma <xref:System.Windows.Controls.Grid> bilgilerini birden çok öğe arasında paylaşmak için bir mekanizma sağlar.  
  
#### <a name="how-is-grid-different-from-table"></a>Izgaratablodan Farkı Nedir?  
 <xref:System.Windows.Documents.Table>ve <xref:System.Windows.Controls.Grid> bazı ortak işlevleri paylaşın, ancak her biri farklı senaryolar için en uygunudur. A, <xref:System.Windows.Documents.Table> akış içeriği içinde kullanılmak üzere tasarlanmıştır (akış içeriği hakkında daha fazla bilgi için [Akış Belgesine Genel Bakış'a](../advanced/flow-document-overview.md) bakın). Izgaralar en iyi formların içinde kullanılır (temelde akış içeriğidışında herhangi bir yerde). Bir <xref:System.Windows.Documents.FlowDocument>içinde, <xref:System.Windows.Documents.Table> bir değil iken <xref:System.Windows.Controls.Grid> pagination, sütun yeniden akışı ve içerik seçimi gibi akış içeriği davranışlarını destekler. Öte <xref:System.Windows.Controls.Grid> yandan a en iyi bir <xref:System.Windows.Documents.FlowDocument> satır ve <xref:System.Windows.Controls.Grid> sütun dizini dayalı öğeleri ekler <xref:System.Windows.Documents.Table> dahil olmak üzere birçok nedenden dolayı dışında kullanılır, değil. Öğe, <xref:System.Windows.Controls.Grid> tek bir "hücre" içinde birden fazla öğenin bulunmasına izin vererek alt içeriğin katmanlanmasına izin verir. <xref:System.Windows.Documents.Table>katmanlamayı desteklemez. A'nın <xref:System.Windows.Controls.Grid> alt öğeleri kesinlikle kendi "hücre" sınırlarının alanına göre konumlandırılabilir. <xref:System.Windows.Documents.Table>bu özelliği desteklemez. Son olarak, bir <xref:System.Windows.Controls.Grid> daha <xref:System.Windows.Documents.Table>hafif bir .  
  
#### <a name="sizing-behavior-of-columns-and-rows"></a>Sütun ve Satırboyutlandırma Davranışı  
 A <xref:System.Windows.Controls.Grid> içinde tanımlanan sütunlar ve <xref:System.Windows.GridUnitType.Star> satırlar, kalan alanı orantılı olarak dağıtmak için boyutlandırmadan yararlanabilir. Bir <xref:System.Windows.GridUnitType.Star> satırın veya sütunun Yüksekliği veya Genişliği seçildiğinde, bu sütun veya satır kalan kullanılabilir alanın ağırlıklı bir oranını alır. <xref:System.Windows.GridUnitType.Auto>Bu, bir sütun veya satırdaki içeriğin boyutuna göre alanı eşit olarak dağıtacak olan ın tam tersidir. Bu değer, `*` 'yi kullanırken veya `2*` kullanırken [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]ifade edilir. İlk durumda, satır veya sütun, ikinci durumda, iki kez ve benzeri bir kez kullanılabilir alan alırsınız. Bu tekniği birleştirerek alanı bir <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> ve <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> değeri `Stretch` ile orantılı olarak dağıtmak için düzen alanını ekran alanının yüzdesi ile bölmek mümkündür. <xref:System.Windows.Controls.Grid>alanı bu şekilde dağıtabilen tek düzen panelidir.  
  
#### <a name="defining-and-using-a-grid"></a>Izgara Tanımlama ve Kullanma  
 Aşağıdaki örnek, Windows Başlat [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] menüsünde bulunan Çalıştır iletişim kutusunda bulunana benzer bir yapının nasıl oluşturulabildiğini göstermektedir.  
  
 [!code-csharp[GridRunDialog#1](~/samples/snippets/csharp/VS_Snippets_Wpf/GridRunDialog/CSharp/window1.xaml.cs#1)]
 [!code-vb[GridRunDialog#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/GridRunDialog/VisualBasic/grid_vb.vb#1)]  
  
 Derlenen uygulama, bu [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] gibi görünen yeni bir sonuç verir.  
  
 ![Tipik bir Izgara Öğesi.](./media/avalon-run-dialog.PNG "avalon_run_dialog")  
  
<a name="Panels_overview_StackPanel_subsection"></a>
### <a name="stackpanel"></a>StackPanel  
 A, <xref:System.Windows.Controls.StackPanel> öğeleri atanmış bir yönde "yığınla" yapmanızı sağlar. Varsayılan yığın yönü dikeydir. Özellik <xref:System.Windows.Controls.StackPanel.Orientation%2A> içerik akışını denetlemek için kullanılabilir.  
  
#### <a name="stackpanel-vs-dockpanel"></a>StackPanel vs DockPanel  
 Her <xref:System.Windows.Controls.DockPanel> ne kadar alt öğeleri <xref:System.Windows.Controls.DockPanel> <xref:System.Windows.Controls.StackPanel> "yığını" ve bazı kullanım senaryolarında benzer sonuçlar üretmez. Örneğin, alt öğelerin sırası bir <xref:System.Windows.Controls.DockPanel> 'deki boyutlarını <xref:System.Windows.Controls.StackPanel>etkileyebilir, ancak bir ' deki boyutlarını etkileyebilir. Bunun <xref:System.Windows.Controls.StackPanel> <xref:System.Double.PositiveInfinity>nedeni, istifleme yönünde ölçüler, <xref:System.Windows.Controls.DockPanel> oysa yalnızca kullanılabilir boyutu ölçer.  
  
 Aşağıdaki örnek, bu önemli farkı göstermektedir.  
  
 [!code-cpp[StackPanelOvw4#1](~/samples/snippets/cpp/VS_Snippets_Wpf/StackPanelOvw4/CPP/StackPanel_Ovw_Sample4.cpp#1)]
 [!code-csharp[StackPanelOvw4#1](~/samples/snippets/csharp/VS_Snippets_Wpf/StackPanelOvw4/CSharp/StackPanel_Ovw_Sample4.cs#1)]
 [!code-vb[StackPanelOvw4#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StackPanelOvw4/VisualBasic/StackPanelSamp.vb#1)]
 [!code-xaml[StackPanelOvw4#1](~/samples/snippets/xaml/VS_Snippets_Wpf/StackPanelOvw4/XAML/default.xaml#1)]  
  
 Render davranış farkı bu resimde görülebilir.  
  
 ![Ekran görüntüsü: StackPanel vs. DockPanel ekran görüntüsü](./media/layout-smiley-stackpanel.PNG "layout_smiley_stackpanel")  
  
#### <a name="defining-and-using-a-stackpanel"></a>StackPanel Tanımlama ve Kullanma  
 Aşağıdaki örnek, dikey konumlandırılmış <xref:System.Windows.Controls.StackPanel> düğmeler kümesi oluşturmak için a'nın nasıl kullanılacağını gösterir. Yatay konumlandırma için özelliği <xref:System.Windows.Controls.StackPanel.Orientation%2A> <xref:System.Windows.Controls.Orientation.Horizontal>' ye göre ayarla  
  
 [!code-csharp[StackPanel_ovw2#1](~/samples/snippets/csharp/VS_Snippets_Wpf/StackPanel_ovw2/CSharp/StackPanel_Ovw_Sample2.cs#1)]
 [!code-vb[StackPanel_ovw2#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StackPanel_ovw2/VisualBasic/StackPanelOvw.vb#1)]  
  
 Derlenen uygulama, bu [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] gibi görünen yeni bir sonuç verir.  
  
 ![Tipik bir StackPanel öğesi.](./media/panel-intro-stackpanel.PNG "panel_intro_stackpanel")  
  
<a name="Panels_overview_VirtualizingStackPanel_subsection"></a>
#### <a name="virtualizingstackpanel"></a>VirtualizingStackPanel  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]ayrıca, verilere bağlı <xref:System.Windows.Controls.StackPanel> alt içeriği otomatik olarak "sanallaştıran" öğenin bir varyasyonunu sağlar. Bu bağlamda, sanallaştırma sözcüğü, öğelerin ekranda görünür olduğu daha fazla sayıda veri öğesinden bir öğe alt kümesinin oluşturulduğu bir tekniği ifade eder. Belirli bir anda ekranda yalnızca birkaç kişi olabilirken, hem bellek hem de işlemci açısından çok sayıda UI öğesi oluşturmak yoğundur. <xref:System.Windows.Controls.VirtualizingStackPanel>(tarafından <xref:System.Windows.Controls.VirtualizingPanel>sağlanan işlevsellik yoluyla) görünür öğeleri <xref:System.Windows.Controls.ItemContainerGenerator> hesaplar <xref:System.Windows.Controls.ItemsControl> ve <xref:System.Windows.Controls.ListBox> yalnızca görünür öğeler için öğeler oluşturmak için bir (gibi veya) <xref:System.Windows.Controls.ListView>ile çalışır.  
  
 Öğe <xref:System.Windows.Controls.VirtualizingStackPanel> otomatik olarak gibi denetimler için madde <xref:System.Windows.Controls.ListBox>ana bilgisayar olarak ayarlanır . Veriye bağlı bir koleksiyon barındırırken, içerik bir <xref:System.Windows.Controls.ScrollViewer>. Bu, birçok alt öğeyi barındırırken performansı büyük ölçüde artırır.  
  
 Aşağıdaki biçimlendirme, bir öğe <xref:System.Windows.Controls.VirtualizingStackPanel> ana bilgisayar olarak nasıl kullanılacağını gösterir. Sanallaştırmanın <xref:System.Windows.Controls.VirtualizingStackPanel.IsVirtualizingProperty?displayProperty=nameWithType> oluşması için `true` ekli özelliğin (varsayılan) olarak ayarlanabilmesi gerekir.  
  
 [!code-xaml[VirtualizingStackPanel_Intro#1](~/samples/snippets/csharp/VS_Snippets_Wpf/VirtualizingStackPanel_Intro/CS/default.xaml#1)]  
  
<a name="Panels_overview_WrapPanel"></a>
### <a name="wrappanel"></a>WrapPanel  
 <xref:System.Windows.Controls.WrapPanel>alt öğeleri soldan sağa sıralı konuma yerleştirmek ve üst kapsayıcının kenarına ulaştığında içeriği bir sonraki satıra bölmek için kullanılır. İçerik yatay veya dikey olarak yönlendirilebilir. <xref:System.Windows.Controls.WrapPanel>basit akan [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] senaryolar için yararlıdır. Ayrıca tüm alt öğeleri için üniforma boyutlandırma uygulamak için kullanılabilir.  
  
 Aşağıdaki örnek, kapsayıcılarının kenarına ulaştıklarında kaydıran bir <xref:System.Windows.Controls.WrapPanel> ekran <xref:System.Windows.Controls.Button> denetiminin nasıl oluşturulacağını gösterir.  
  
 [!code-cpp[WrapPanel_Intro#1](~/samples/snippets/cpp/VS_Snippets_Wpf/WrapPanel_Intro/CPP/WrapPanel_Code.cpp#1)]
 [!code-csharp[WrapPanel_Intro#1](~/samples/snippets/csharp/VS_Snippets_Wpf/WrapPanel_Intro/CSharp/WrapPanel_Code.cs#1)]
 [!code-vb[WrapPanel_Intro#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WrapPanel_Intro/VisualBasic/WrapPanel_vb.vb#1)]
 [!code-xaml[WrapPanel_Intro#1](~/samples/snippets/xaml/VS_Snippets_Wpf/WrapPanel_Intro/XAML/default.xaml#1)]  
  
 Derlenen uygulama, bu [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] gibi görünen yeni bir sonuç verir.  
  
 ![Tipik bir WrapPanel Öğesi.](./media/wrappanel-element.PNG "WrapPanel_Element")  
  
<a name="Panels_nested_panel_elements"></a>
## <a name="nested-panel-elements"></a>İç Içe Panel Elemanları  
 <xref:System.Windows.Controls.Panel>karmaşık düzenler oluşturmak için öğeler birbirinin içinde iç içe olabilir. Bu bir kısmı için ideal <xref:System.Windows.Controls.Panel> olduğu durumlarda çok [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]yararlı olabilir , ama farklı bir bölümünün ihtiyaçlarını karşılamak olmayabilir [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)].  
  
 Uygulamanızın destekedebileceği iç içe geçme miktarı için pratik bir sınır yoktur, ancak uygulamanızı yalnızca istediğiniz düzen için gerçekten gerekli olan panelleri kullanmak üzere sınırlamak genellikle en iyisidir. Çoğu durumda, <xref:System.Windows.Controls.Grid> bir düzen kapsayıcısı olarak esnekliği nedeniyle iç içe geçmiş paneller yerine bir öğe kullanılabilir. Bu, gereksiz öğeleri ağacın dışında tutarak uygulamanızın performansını artırabilir.  
  
 Aşağıdaki örnek, belirli bir [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] düzene ulaşmak için <xref:System.Windows.Controls.Panel> iç içe olan öğelerden yararlanan bir öğenin nasıl oluşturulabildiğini gösterir. Bu özel durumda, <xref:System.Windows.Controls.DockPanel> bir öğe [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] yapısı sağlamak için <xref:System.Windows.Controls.StackPanel> kullanılır <xref:System.Windows.Controls.Grid>ve iç <xref:System.Windows.Controls.Canvas> içe öğeleri, a , ve <xref:System.Windows.Controls.DockPanel>a alt öğeleri tam olarak üst içinde konumlandırmak için kullanılır.  
  
 [!code-csharp[Nested_Panels#1](~/samples/snippets/csharp/VS_Snippets_Wpf/Nested_Panels/CSharp/nestedpanels.cs#1)]
 [!code-vb[Nested_Panels#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Nested_Panels/VisualBasic/nestedpanels.vb#1)]  
  
 Derlenen uygulama, bu [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] gibi görünen yeni bir sonuç verir.  
  
 ![İç içe panellerden yararlanan bir u-ui.](./media/nested-panels.PNG "nested_panels")  
  
<a name="Panels_custom_panel_elements"></a>
## <a name="custom-panel-elements"></a>Özel Panel Elemanları  
 Esnek [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] düzen denetimleri bir dizi sağlar ken, özel düzen davranışları <xref:System.Windows.FrameworkElement.ArrangeOverride%2A> <xref:System.Windows.FrameworkElement.MeasureOverride%2A> da ve yöntemleri geçersiz kılınarak elde edilebilir. Özel boyutlandırma ve konumlandırma, bu geçersiz kılma yöntemleri içinde yeni konumlandırma davranışları tanımlayarak gerçekleştirilebilir.  
  
 Benzer şekilde, türemiş sınıflara (örneğin <xref:System.Windows.Controls.Canvas> <xref:System.Windows.Controls.Grid>veya) dayalı özel düzen <xref:System.Windows.FrameworkElement.ArrangeOverride%2A> <xref:System.Windows.FrameworkElement.MeasureOverride%2A> davranışları, bunların ve yöntemlerinin geçersiz kılınmasıyla tanımlanabilir.  
  
 Aşağıdaki biçimlendirme, özel <xref:System.Windows.Controls.Panel> bir öğenin nasıl oluşturulup oluşturulabildiğini gösterir. Bu <xref:System.Windows.Controls.Panel>yeni , `PlotPanel`olarak tanımlanan , sabit kodlu *x-* ve *y-* koordinatları kullanarak alt öğelerin konumlandırma destekler. Bu örnekte, <xref:System.Windows.Shapes.Rectangle> bir öğe (gösterilmez) çizim noktası 50 (*x*) ve 50 (*y)* olarak konumlandırılır.  
  
 [!code-cpp[PlotPanel#1](~/samples/snippets/cpp/VS_Snippets_Wpf/PlotPanel/CPP/PlotPanel.cpp#1)]
 [!code-csharp[PlotPanel#1](~/samples/snippets/csharp/VS_Snippets_Wpf/PlotPanel/CSharp/PlotPanel.cs#1)]
 [!code-vb[PlotPanel#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PlotPanel/VisualBasic/PlotPanel.vb#1)]  
  
 Daha karmaşık bir özel panel uygulamasını görüntülemek için [bkz.](https://go.microsoft.com/fwlink/?LinkID=159979)  
  
<a name="Panels_global_localization"></a>
## <a name="localizationglobalization-support"></a>Yerelleştirme/Küreselleşme Desteği  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]yerelleştirilebilir oluşturulmasına yardımcı özellikleri bir dizi [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]destekler.  
  
 Tüm panel öğeleri, <xref:System.Windows.FrameworkElement.FlowDirection%2A> kullanıcının yerel ayarlarına veya dil ayarlarına bağlı olarak içeriği dinamik olarak yeniden akış için kullanılabilen özelliği doğal olarak destekler. Daha fazla bilgi için bkz. <xref:System.Windows.FrameworkElement.FlowDirection%2A>.  
  
 Özellik, <xref:System.Windows.Window.SizeToContent%2A> uygulama geliştiricilerin yerelleştirilmiş [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]gereksinimlerini tahmin etmesini sağlayan bir mekanizma sağlar. Bu <xref:System.Windows.SizeToContent.WidthAndHeight> özelliğin değerini kullanarak, <xref:System.Windows.Window> bir üst öğe her zaman içeriğe sığacak şekilde dinamik boyutlar ve yapay yükseklik veya genişlik kısıtlamaları ile sınırlandırılmamıştır.  
  
 <xref:System.Windows.Controls.DockPanel>, <xref:System.Windows.Controls.Grid>ve <xref:System.Windows.Controls.StackPanel> yerelleştirilebilir [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]için tüm iyi seçimlerdir. <xref:System.Windows.Controls.Canvas>ancak içeriği kesinlikle konumlandırdığı için iyi bir seçim değildir ve bu da yerelleştirmeyi zorlaştırır.  
  
 Yerelleştirilebilir kullanıcı [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] arabirimleri (UI)s ile uygulama oluşturma hakkında daha fazla bilgi [için, Otomatik Düzen Genel Bakış'ı Kullan'a](../advanced/use-automatic-layout-overview.md)bakın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [İzlenecek Yol: İlk WPF masaüstü uygulamam](../getting-started/walkthrough-my-first-wpf-desktop-application.md)
- [WPF Düzen Galerisi Örneği](https://go.microsoft.com/fwlink/?LinkID=160054)
- [Düzen](../advanced/layout.md)
- [WPF Denetimleri Galeri Örneği](https://github.com/Microsoft/WPF-Samples/tree/master/Getting%20Started/ControlsAndLayout)
- [Hizalama, Kenar Boşlukları ve Doldurmaya Genel Bakış](../advanced/alignment-margins-and-padding-overview.md)
- [Özel İçerik Sarma Paneli Örneği Oluşturma](https://go.microsoft.com/fwlink/?LinkID=159979)
- [Ekli Özelliklere Genel Bakış](../advanced/attached-properties-overview.md)
- [Otomatik Düzen Kullanımına Genel Bakış](../advanced/use-automatic-layout-overview.md)
- [Düzen ve Tasarım](../advanced/optimizing-performance-layout-and-design.md)
