---
title: Panellere Genel Bakış
description: Windows Presentation Foundation, öğelerin işlenmesini denetleyen önceden tanımlanmış Panel öğeleri sağlar. Özel Panel öğeleri oluşturmayı öğrenin.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Panel control [WPF], about Panel control
- controls [WPF], Panel
ms.assetid: f73644af-9941-4611-8754-6d4cef03fc44
ms.openlocfilehash: 7f3f6948de28f50dc6470a7dfc1a5bad67e57c79
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87167767"
---
# <a name="panels-overview"></a>Panellere Genel Bakış
<xref:System.Windows.Controls.Panel>öğeler öğelerin işlenmesini denetleyen bileşenlerdir: boyut ve boyutlar, bunların konumları ve alt içeriklerinin yerleşimi. , [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] Bir dizi önceden tanımlanmış <xref:System.Windows.Controls.Panel> öğe ve özel öğe oluşturma özelliğini sağlar <xref:System.Windows.Controls.Panel> .  
  
 Bu konuda aşağıdaki bölümler yer almaktadır.  
  
- [Panel sınıfı](#Panels_view_from_10000_feet)  
  
- [Panel öğesi ortak üyeleri](#Panels_declared_members)  
  
- [Türetilmiş Panel öğeleri](#Panels_derived_elements)  
  
- [Kullanıcı arabirimi bölmeleri](#Panels_main_UI_elements)  
  
- [İç içe Panel öğeleri](#Panels_nested_panel_elements)  
  
- [Özel Panel öğeleri](#Panels_custom_panel_elements)  
  
- [Yerelleştirme/genelleştirme desteği](#Panels_global_localization)  
  
<a name="Panels_view_from_10000_feet"></a>
## <a name="the-panel-class"></a>Panel sınıfı  
 <xref:System.Windows.Controls.Panel>, içinde düzen desteği sağlayan tüm öğeler için temel sınıftır [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] . Türetilmiş <xref:System.Windows.Controls.Panel> öğeler, ve kodundaki öğeleri konumlandırmak ve düzenlemek için kullanılır [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] .  
  
 , [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Birçok karmaşık düzeni etkinleştiren kapsamlı bir türetilmiş panel uygulamaları paketini içerir. Bu türetilmiş sınıflar, çoğu standart senaryoyu etkinleştiren özellikleri ve yöntemleri sunar [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] . İhtiyaçlarını karşılayan bir alt düzenleme davranışı bulamadığı geliştiriciler, ve yöntemlerini geçersiz kılarak yeni düzenler oluşturabilir <xref:System.Windows.FrameworkElement.ArrangeOverride%2A> <xref:System.Windows.FrameworkElement.MeasureOverride%2A> . Özel düzen davranışları hakkında daha fazla bilgi için bkz. [Özel Panel öğeleri](#Panels_custom_panel_elements).  
  
<a name="Panels_declared_members"></a>
## <a name="panel-common-members"></a>Panel ortak Üyeler  
 Tüm öğeler,,,,, <xref:System.Windows.Controls.Panel> <xref:System.Windows.FrameworkElement> ve dahil olmak üzere tarafından tanımlanan temel boyutlandırma ve konumlandırma özelliklerini destekler <xref:System.Windows.FrameworkElement.Height%2A> <xref:System.Windows.FrameworkElement.Width%2A> <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> <xref:System.Windows.FrameworkElement.Margin%2A> <xref:System.Windows.FrameworkElement.LayoutTransform%2A> . Tarafından tanımlanan özellikleri konumlandırma hakkında daha fazla bilgi için <xref:System.Windows.FrameworkElement> bkz. [Hizalama, kenar boşlukları ve doldurmaya genel bakış](../advanced/alignment-margins-and-padding-overview.md).  
  
 <xref:System.Windows.Controls.Panel>düzeni anlamak ve kullanmak için kritik öneme sahip ek özellikler sunar. <xref:System.Windows.Controls.Panel.Background%2A>Özelliği, bir türetilmiş Panel öğesinin sınırları arasındaki alanı bir ile dolduracak şekilde kullanılır <xref:System.Windows.Media.Brush> . <xref:System.Windows.Controls.Panel.Children%2A>öğesinin içerdiği öğelerin alt koleksiyonunu temsil eder <xref:System.Windows.Controls.Panel> . <xref:System.Windows.Controls.Panel.InternalChildren%2A>koleksiyonun içeriğini ve <xref:System.Windows.Controls.Panel.Children%2A> veri bağlama tarafından oluşturulan üyeleri temsil eder. Her ikisi de <xref:System.Windows.Controls.UIElementCollection> üst öğe içinde barındırılan alt öğelerinden oluşur <xref:System.Windows.Controls.Panel> .  
  
 Panel ayrıca <xref:System.Windows.Controls.Panel.ZIndex%2A?displayProperty=nameWithType> , türetilmiş bir üzerinde katmanlı sıra elde etmek için kullanılabilecek iliştirilmiş bir özellik sunar <xref:System.Windows.Controls.Panel> . <xref:System.Windows.Controls.Panel.Children%2A>Daha yüksek bir değere sahip bir Panel koleksiyonunun üyeleri, <xref:System.Windows.Controls.Panel.ZIndex%2A?displayProperty=nameWithType> daha düşük bir değere sahip olanların önünde görüntülenir <xref:System.Windows.Controls.Panel.ZIndex%2A?displayProperty=nameWithType> . Bu, özellikle <xref:System.Windows.Controls.Canvas> ve <xref:System.Windows.Controls.Grid> alt öğelerin aynı koordinat alanını paylaşmasına izin veren panolar için yararlıdır.  
  
 <xref:System.Windows.Controls.Panel>Ayrıca <xref:System.Windows.Controls.Panel.OnRender%2A> , öğesinin varsayılan sunum davranışını geçersiz kılmak için kullanılabilen yöntemini tanımlar <xref:System.Windows.Controls.Panel> .  
  
#### <a name="attached-properties"></a>İliştirilmiş Özellikler  
 Türetilmiş Panel öğeleri, ekli özelliklerden oluşan kapsamlı kullanımı kolaylaştırır. İliştirilmiş bir özellik, geleneksel ortak dil çalışma zamanı (CLR) özelliği "sarmalayıcı" olmayan, bağımlılık özelliği 'nin özelleşmiş bir biçimidir. Eklenmiş Özellikler ' de [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] , izleyen bazı örneklerde görünebilen özel bir sözdizimi vardır.  
  
 İliştirilmiş bir özelliğin amacı, alt öğelerin gerçekten üst öğe tarafından tanımlanan bir özelliğin benzersiz değerlerini depolamasına izin versağlamaktır. Bu işlevselliğin bir uygulaması, alt öğelerin, [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] uygulama düzeni için son derece faydalı olan ' de nasıl sunulmasını istediğinizi bilgilendirmesini sağlar. Daha fazla bilgi için bkz. [ekli özelliklere genel bakış](../advanced/attached-properties-overview.md).  
  
<a name="Panels_derived_elements"></a>
## <a name="derived-panel-elements"></a>Türetilmiş Panel öğeleri  
 Birçok nesne öğesinden türetilir <xref:System.Windows.Controls.Panel> , ancak bunların hepsi kök Düzen sağlayıcıları olarak kullanılmak üzere tasarlanmamıştır. <xref:System.Windows.Controls.Canvas> <xref:System.Windows.Controls.DockPanel> <xref:System.Windows.Controls.Grid> <xref:System.Windows.Controls.StackPanel> <xref:System.Windows.Controls.VirtualizingStackPanel> <xref:System.Windows.Controls.WrapPanel> Özellikle uygulama oluşturmak için tasarlanan [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] altı tanımlanmış Panel sınıfı (,,,,, ve) vardır.  
  
 Her panel öğesi, aşağıdaki tabloda görüldüğü gibi kendi özel işlevselliğini Kapsüller.  
  
|Öğe Adı|UI paneli?|Açıklama|  
|------------------|---------------|-----------------|  
|<xref:System.Windows.Controls.Canvas>|Evet|Alt öğeleri alana göreli olarak açıkça konumlandırabileceğiniz bir alan tanımlar <xref:System.Windows.Controls.Canvas> .|  
|<xref:System.Windows.Controls.DockPanel>|Yes|Alt öğeleri yatay veya dikey olarak birbirlerine göre düzenleyebileceğiniz bir alan tanımlar.|  
|<xref:System.Windows.Controls.Grid>|Yes|Sütun ve satırlardan oluşan esnek bir kılavuz alanını tanımlar. Öğesinin alt öğeleri <xref:System.Windows.Controls.Grid> , özelliği kullanılarak tam olarak konumlandırılmış olabilir <xref:System.Windows.FrameworkElement.Margin%2A> .|  
|<xref:System.Windows.Controls.StackPanel>|Yes|Alt öğeleri yatay veya dikey olarak yönelimli tek bir satıra yerleştirir.|  
|<xref:System.Windows.Controls.Primitives.TabPanel>|Hayır|İçindeki sekme düğmelerinin yerleşimini işler <xref:System.Windows.Controls.TabControl> .|  
|<xref:System.Windows.Controls.Primitives.ToolBarOverflowPanel>|Hayır|Bir denetim içindeki içeriği düzenler <xref:System.Windows.Controls.ToolBar> .|  
|<xref:System.Windows.Controls.Primitives.UniformGrid>|Hayır|<xref:System.Windows.Controls.Primitives.UniformGrid>Tüm eşit hücre boyutlarına sahip bir kılavuzdaki alt öğeleri düzenlemek için kullanılır.|  
|<xref:System.Windows.Controls.VirtualizingPanel>|Hayır|, Alt öğelerini "sanallaştırmaya" yardımcı olan panolar için bir temel sınıf sağlar.|  
|<xref:System.Windows.Controls.VirtualizingStackPanel>|Yes|İçeriği yatay veya dikey olarak tek bir satıra göre düzenler ve sanallaştırır.|  
|<xref:System.Windows.Controls.WrapPanel>|Yes|<xref:System.Windows.Controls.WrapPanel>Sol taraftaki alt öğeleri, kapsayan kutunun kenarındaki bir sonraki satıra kadar olan sıralı konumda konumlandırır. Sonraki sıralama, özelliğin değerine bağlı olarak yukarıdan aşağıya veya sağdan sola doğru bir şekilde gerçekleşir <xref:System.Windows.Controls.WrapPanel.Orientation%2A> .|  
  
<a name="Panels_main_UI_elements"></a>
## <a name="user-interface-panels"></a>Kullanıcı arabirimi bölmeleri  
 ' De,,,,, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ve için en iyi duruma getirilmiş altı panel sınıfı mevcuttur [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] : <xref:System.Windows.Controls.Canvas> , <xref:System.Windows.Controls.DockPanel> ,, <xref:System.Windows.Controls.Grid> <xref:System.Windows.Controls.StackPanel> , <xref:System.Windows.Controls.VirtualizingStackPanel> ve <xref:System.Windows.Controls.WrapPanel> . Bu panel öğelerinin çoğu uygulama için kullanımı kolay, çok yönlü ve genişletilebilir.  
  
 Her türetilmiş <xref:System.Windows.Controls.Panel> öğe boyutlandırma kısıtlamalarını farklı şekilde değerlendirir. <xref:System.Windows.Controls.Panel>Yatay veya dikey yöndeki bir tanıtıcı kısıtlamalarının düzeni nasıl daha öngörülebilir hale getirebilir anlamak.  
  
|**Panel adı**|**x boyutlu**|**y-Dimension**|  
|--------------------|----------------------|----------------------|  
|<xref:System.Windows.Controls.Canvas>|İçerikle kısıtlanmış|İçerikle kısıtlanmış|  
|<xref:System.Windows.Controls.DockPanel>|Kısıtlanmış|Kısıtlanmış|  
|<xref:System.Windows.Controls.StackPanel>(Dikey yön)|Kısıtlanmış|İçerikle kısıtlanmış|  
|<xref:System.Windows.Controls.StackPanel>(Yatay yönlendirme)|İçerikle kısıtlanmış|Kısıtlanmış|  
|<xref:System.Windows.Controls.Grid>|Kısıtlanmış|, <xref:System.Windows.GridUnitType.Auto> Satırlar ve sütunlar için uygulanacak durumlar dışında kısıtlanmış|  
|<xref:System.Windows.Controls.WrapPanel>|İçerikle kısıtlanmış|İçerikle kısıtlanmış|  
  
 Bu öğelerin her birine yönelik daha ayrıntılı açıklamalar ve kullanım örnekleri aşağıda bulabilirsiniz.  
  
<a name="Panels_overview_Canvas_subsection"></a>
### <a name="canvas"></a>Tuval  
 <xref:System.Windows.Controls.Canvas>Öğesi, mutlak *x* ve *y* koordinatlarına göre içerik konumlandırmasını sağlar. Öğeler benzersiz bir konumda çizilebilirler; ya da öğeler aynı koordinatları kapladıklarında, İşaretlemede görünme sırası öğelerin çizildiği sırayı belirler.  
  
 <xref:System.Windows.Controls.Canvas>, herhangi birinin en esnek düzen desteğini sağlar <xref:System.Windows.Controls.Panel> . Height ve Width özellikleri, tuvalin alanını tanımlamak için kullanılır ve içindeki öğeler, üst öğenin alanına göre mutlak koordinatları atanır <xref:System.Windows.Controls.Canvas> . Dört Ekli Özellik, <xref:System.Windows.Controls.Canvas.Left%2A?displayProperty=nameWithType> , <xref:System.Windows.Controls.Canvas.Top%2A?displayProperty=nameWithType> , <xref:System.Windows.Controls.Canvas.Right%2A?displayProperty=nameWithType> ve <xref:System.Windows.Controls.Canvas.Bottom%2A?displayProperty=nameWithType> , içindeki nesne yerleşimi üzerinde ince denetime izin verir <xref:System.Windows.Controls.Canvas> , böylece Geliştirici öğeleri ekranda hassas bir şekilde konumlandırın ve düzenleyebilir.  
  
#### <a name="cliptobounds-within-a-canvas"></a>Tuval Içindeki Cliptosınırlara  
 <xref:System.Windows.Controls.Canvas>, kendi tanımlı ve dışındaki koordinatlara bile, alt öğeleri ekranda herhangi bir konumda konumlandırabilirsiniz <xref:System.Windows.FrameworkElement.Height%2A> <xref:System.Windows.FrameworkElement.Width%2A> . Ayrıca, <xref:System.Windows.Controls.Canvas> alt öğelerinin boyutundan etkilenmez. Sonuç olarak, alt öğe, üst öğenin sınırlayıcı dikdörtgeni dışında diğer öğeleri fazla çizmek için mümkündür <xref:System.Windows.Controls.Canvas> . Varsayılan davranışı, <xref:System.Windows.Controls.Canvas> alt öğelerin üst öğenin sınırları dışında çizilsin <xref:System.Windows.Controls.Canvas> . Bu davranış istenmeyen ise, <xref:System.Windows.UIElement.ClipToBounds%2A> özelliği olarak ayarlanabilir `true` . Bu <xref:System.Windows.Controls.Canvas> , kendi boyutuna kırpmasına neden olur. <xref:System.Windows.Controls.Canvas>, alt öğelerin sınırlarının dışına çizilmesini sağlayan tek düzen öğesidir.  
  
 Bu davranış, [Width özellikleri karşılaştırma örneğinde](https://github.com/Microsoft/WPF-Samples/tree/master/Elements/WidthProperties)grafiksel olarak gösterilmiştir.  
  
#### <a name="defining-and-using-a-canvas"></a>Tuval tanımlama ve kullanma  
 Bir <xref:System.Windows.Controls.Canvas> , veya kodu kullanılarak basitçe oluşturulabilir [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] . Aşağıdaki örnek, <xref:System.Windows.Controls.Canvas> içeriğin mutlak olarak konumlandırılması için nasıl kullanılacağını gösterir. Bu kod 3 100 piksellik kareler üretir. İlk kare kırmızı ve sol üst (*x, y*) konumu (0, 0) olarak belirtilir. İkinci kare yeşil ve sol üst konumu (100, 100), ilk karenin hemen altına ve sağına eklenir. Üçüncü kare mavi ve sol üst konumu (50, 50), bu nedenle ilk karenin sağ alt çeyreğine ve ikincinin sol üst çeyreğine dahil olur. Üçüncü kare en son düzenlendiği için, diğer iki karenin üzerinde olduğu gibi görünür, diğer bir deyişle, çakışan bölümler üçüncü kutunun rengine varsayılmıştır.  
  
 [!code-csharp[CanvasOvwSample#1](~/samples/snippets/csharp/VS_Snippets_Wpf/CanvasOvwSample/CSharp/Canvas_Ovw_Sample.cs#1)]
 [!code-vb[CanvasOvwSample#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CanvasOvwSample/VisualBasic/canvas_vb.vb#1)]
 [!code-xaml[CanvasOvwSample#1](~/samples/snippets/xaml/VS_Snippets_Wpf/CanvasOvwSample/XAML/default.xaml#1)]  
  
 Derlenen uygulama, şuna benzeyen yeni bir oluşturur [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] .  
  
 ![Tipik bir tuval öğesi.](./media/panel-intro-canvas.PNG "panel_intro_canvas")  
  
<a name="Panels_overview_DockPanel_subsection"></a>
### <a name="dockpanel"></a>DockPanel  
 <xref:System.Windows.Controls.DockPanel>Öğesi, <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType> bir kapsayıcının kenarları üzerinde içerik konumlandırmak için alt içerik öğelerinde ayarlanan ekli özelliği kullanır. <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType>Veya olarak ayarlandığında <xref:System.Windows.Controls.Dock.Top> <xref:System.Windows.Controls.Dock.Bottom> , alt öğeleri birbirlerinin üzerinde veya altında konumlandırır. <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType>Veya olarak ayarlandığında <xref:System.Windows.Controls.Dock.Left> <xref:System.Windows.Controls.Dock.Right> , alt öğeleri diğerinin sol veya sağ tarafında konumlandırır. <xref:System.Windows.Controls.DockPanel.LastChildFill%2A>Özelliği, son öğesinin bir alt öğesi olarak eklenen konumunu belirler <xref:System.Windows.Controls.DockPanel> .  
  
 <xref:System.Windows.Controls.DockPanel>Düğme kümesi gibi ilgili denetimlerin grubunu konumlandırmak için öğesini kullanabilirsiniz. Alternatif olarak, [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] Microsoft Outlook 'ta bulunanlara benzer bir "paned" oluşturmak için bunu kullanabilirsiniz.  
  
#### <a name="sizing-to-content"></a>Içeriğe boyutlandırma  
 <xref:System.Windows.FrameworkElement.Height%2A>Ve <xref:System.Windows.FrameworkElement.Width%2A> özellikleri belirtilmemişse, <xref:System.Windows.Controls.DockPanel> içeriğine göre boyutlar. Boyut, alt öğelerinin boyutuna uyum sağlayacak şekilde artırabilir veya azalabilir. Ancak, bu özellikler belirtildiğinde ve sonraki belirtilen alt öğe için artık yer kalmadığında, bu <xref:System.Windows.Controls.DockPanel> alt öğeyi veya sonraki alt öğeleri görüntülemez ve sonraki alt öğeleri ölçmez.  
  
#### <a name="lastchildfill"></a>LastChildFill  
 Varsayılan olarak, bir öğenin son alt öğesi <xref:System.Windows.Controls.DockPanel> kalan, ayrılmamış alanı "doldurur". Bu davranış istenmiyorsa, <xref:System.Windows.Controls.DockPanel.LastChildFill%2A> özelliğini olarak ayarlayın `false` .  
  
#### <a name="defining-and-using-a-dockpanel"></a>DockPanel tanımlama ve kullanma  
 Aşağıdaki örnek, kullanarak alanın nasıl bölümleyeceğinizi gösterir <xref:System.Windows.Controls.DockPanel> . <xref:System.Windows.Controls.Border>Bir üst öğenin alt öğesi olarak beş öğe eklenir <xref:System.Windows.Controls.DockPanel> . Her biri, ' ın bölüm alanı için farklı bir konumlama özelliği kullanır <xref:System.Windows.Controls.DockPanel> . Son öğesi "doldurur" ve kalan ayrılmamış alanı.  
  
 [!code-cpp[DockPanelOvwSample#1](~/samples/snippets/cpp/VS_Snippets_Wpf/DockPanelOvwSample/CPP/DockPanel_Ovw_Sample.cpp#1)]
 [!code-csharp[DockPanelOvwSample#1](~/samples/snippets/csharp/VS_Snippets_Wpf/DockPanelOvwSample/CSharp/DockPanel_Ovw_Sample.cs#1)]
 [!code-vb[DockPanelOvwSample#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DockPanelOvwSample/VisualBasic/dockpanel_vb.vb#1)]
 [!code-xaml[DockPanelOvwSample#1](~/samples/snippets/xaml/VS_Snippets_Wpf/DockPanelOvwSample/XAML/default.xaml#1)]  
  
 Derlenen uygulama, şuna benzeyen yeni bir oluşturur [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] .  
  
 ![Tipik bir DockPanel senaryosu.](./media/panel-intro-dockpanel.PNG "panel_intro_dockpanel")  
  
<a name="Panels_overview_Grid_subsection"></a>
### <a name="grid"></a>Kılavuz  
 <xref:System.Windows.Controls.Grid>Öğesi, mutlak bir konumlandırma ve tablosal veri denetiminin işlevselliğini birleştirir. <xref:System.Windows.Controls.Grid>, Öğeleri kolayca konumlandırmanızı ve stil eklemenizi sağlar. <xref:System.Windows.Controls.Grid>esnek satır ve sütun gruplandırmaları tanımlamanızı sağlar ve hatta birden fazla öğe arasında boyutlandırma bilgilerini paylaşma mekanizması sağlar <xref:System.Windows.Controls.Grid> .  
  
#### <a name="how-is-grid-different-from-table"></a>Kılavuz, tablodan farklı midir?  
 <xref:System.Windows.Documents.Table>ve <xref:System.Windows.Controls.Grid> bazı yaygın işlevleri paylaşabilirsiniz, ancak her biri farklı senaryolar için idealdir. <xref:System.Windows.Documents.Table>, Akış içeriği içinde kullanılmak üzere tasarlanmıştır (akış içeriği hakkında daha fazla bilgi için bkz. [akış belgesine genel bakış](../advanced/flow-document-overview.md) ). Kılavuzlar, formların içinde en iyi şekilde kullanılır (temel olarak, akış içeriğinin dışında herhangi bir yerde). Bir içinde <xref:System.Windows.Documents.FlowDocument> , <xref:System.Windows.Documents.Table> sayfalandırma, sütun yeniden akışı ve içerik seçimi gibi akış içeriği davranışlarını destekler, ancak <xref:System.Windows.Controls.Grid> bunu yapmaz. Diğer taraftan bir, bir <xref:System.Windows.Controls.Grid> <xref:System.Windows.Documents.FlowDocument> <xref:System.Windows.Controls.Grid> satır ve sütun dizinine göre öğe ekleme dahil olmak üzere birçok nedenden dolayı en iyi şekilde kullanılır <xref:System.Windows.Documents.Table> . <xref:System.Windows.Controls.Grid>Öğesi, alt içeriğin katmanlanışını sağlar ve tek bir "hücresinde" birden fazla öğenin var olmasına izin verir. <xref:System.Windows.Documents.Table>katmanlanın desteklemez. Öğesinin alt öğeleri, <xref:System.Windows.Controls.Grid> "hücre" sınırlarının alanına göre mutlak olarak konumlandırılmış olabilir. <xref:System.Windows.Documents.Table>Bu özelliği desteklemez. Son olarak, a <xref:System.Windows.Controls.Grid> 'dan daha açık bir ağırdır <xref:System.Windows.Documents.Table> .  
  
#### <a name="sizing-behavior-of-columns-and-rows"></a>Sütunların ve satırların boyutlandırma davranışı  
 Bir içinde tanımlanan sütunlar ve satırlar <xref:System.Windows.Controls.Grid> , <xref:System.Windows.GridUnitType.Star> kalan alanı orantılı bir şekilde dağıtmak için boyutlandırmanın avantajlarından yararlanabilir. <xref:System.Windows.GridUnitType.Star>Bir satır veya sütunun yükseklik veya genişliği olarak seçildiğinde, bu sütun veya satır, kalan kullanılabilir alanın ağırlıklı oranını alır. Bunun aksine <xref:System.Windows.GridUnitType.Auto> , bir sütun veya satır içindeki içeriğin boyutuna göre eşit bir şekilde dağıtırsınız. Bu değer, kullanırken veya olarak ifade edilir `*` `2*` [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] . İlk durumda, satır veya sütun kullanılabilir alanı bir kez, ikinci durumda iki kez ve bu şekilde alır. Bu tekniği birleştirerek bir ve değeri ile alanı orantılı bir şekilde dağıtmak için <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> `Stretch` , ekran alanı yüzdesine göre düzen alanını bölümlemek mümkündür. <xref:System.Windows.Controls.Grid>, alanı bu şekilde dağıtabilecek tek düzen bölmesi olur.  
  
#### <a name="defining-and-using-a-grid"></a>Kılavuz tanımlama ve kullanma  
 Aşağıdaki örnek, [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] Windows Başlat menüsünde bulunan Çalıştır iletişim kutusunda bulunan ile benzer bir şekilde nasıl oluşturulacağını gösterir.  
  
 [!code-csharp[GridRunDialog#1](~/samples/snippets/csharp/VS_Snippets_Wpf/GridRunDialog/CSharp/window1.xaml.cs#1)]
 [!code-vb[GridRunDialog#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/GridRunDialog/VisualBasic/grid_vb.vb#1)]  
  
 Derlenen uygulama, şuna benzeyen yeni bir oluşturur [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] .  
  
 ![Tipik bir Grid öğesi.](./media/avalon-run-dialog.PNG "avalon_run_dialog")  
  
<a name="Panels_overview_StackPanel_subsection"></a>
### <a name="stackpanel"></a>StackPanel  
 <xref:System.Windows.Controls.StackPanel>, Atanan bir yönde öğeleri "yığmanızı" sağlar. Varsayılan yığın yönü dikeydir. <xref:System.Windows.Controls.StackPanel.Orientation%2A>Özelliği, içerik akışını denetlemek için kullanılabilir.  
  
#### <a name="stackpanel-vs-dockpanel"></a>StackPanel ve DockPanel karşılaştırması  
 <xref:System.Windows.Controls.DockPanel>Ayrıca, alt öğeleri de "yığmaya" <xref:System.Windows.Controls.DockPanel> ve <xref:System.Windows.Controls.StackPanel> bazı kullanım senaryolarında benzer sonuçlar üretmese de olabilir. Örneğin, alt öğelerinin sırası, boyutunu ' a değil, ' de etkileyebilir <xref:System.Windows.Controls.DockPanel> <xref:System.Windows.Controls.StackPanel> . Bunun nedeni <xref:System.Windows.Controls.StackPanel> , üzerinde yığınlama yönündeki ölçülerin <xref:System.Double.PositiveInfinity> <xref:System.Windows.Controls.DockPanel> yalnızca kullanılabilir boyutunu ölçüledir.  
  
 Aşağıdaki örnek bu temel farkı gösterir.  
  
 [!code-cpp[StackPanelOvw4#1](~/samples/snippets/cpp/VS_Snippets_Wpf/StackPanelOvw4/CPP/StackPanel_Ovw_Sample4.cpp#1)]
 [!code-csharp[StackPanelOvw4#1](~/samples/snippets/csharp/VS_Snippets_Wpf/StackPanelOvw4/CSharp/StackPanel_Ovw_Sample4.cs#1)]
 [!code-vb[StackPanelOvw4#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StackPanelOvw4/VisualBasic/StackPanelSamp.vb#1)]
 [!code-xaml[StackPanelOvw4#1](~/samples/snippets/xaml/VS_Snippets_Wpf/StackPanelOvw4/XAML/default.xaml#1)]  
  
 İşleme davranışlarındaki fark bu görüntüde görülebilir.  
  
 ![Ekran görüntüsü: StackPanel ile DockPanel ekran görüntüsü](./media/layout-smiley-stackpanel.PNG "layout_smiley_stackpanel")  
  
#### <a name="defining-and-using-a-stackpanel"></a>StackPanel tanımlama ve kullanma  
 Aşağıdaki örnek, bir <xref:System.Windows.Controls.StackPanel> Dikey konumlandırılmış düğme kümesi oluşturmak için öğesinin nasıl kullanılacağını gösterir. Yatay konumlandırma için <xref:System.Windows.Controls.StackPanel.Orientation%2A> özelliğini olarak ayarlayın <xref:System.Windows.Controls.Orientation.Horizontal> .  
  
 [!code-csharp[StackPanel_ovw2#1](~/samples/snippets/csharp/VS_Snippets_Wpf/StackPanel_ovw2/CSharp/StackPanel_Ovw_Sample2.cs#1)]
 [!code-vb[StackPanel_ovw2#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StackPanel_ovw2/VisualBasic/StackPanelOvw.vb#1)]  
  
 Derlenen uygulama, şuna benzeyen yeni bir oluşturur [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] .  
  
 ![Tipik bir StackPanel öğesi.](./media/panel-intro-stackpanel.PNG "panel_intro_stackpanel")  
  
<a name="Panels_overview_VirtualizingStackPanel_subsection"></a>
#### <a name="virtualizingstackpanel"></a>VirtualizingStackPanel  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]Ayrıca, <xref:System.Windows.Controls.StackPanel> veri bağlantılı alt içeriği otomatik olarak "sanallaştırın" bir öğe çeşitlemesi sağlar. Bu bağlamda, sanalbir sözcük, öğelerin bir alt kümesinin ekranda görünür olduğu çok fazla sayıda veri öğesinden oluşturulduğu bir tekniğe başvurur. Belirli bir zamanda ekranda yalnızca birkaç tane olabilir, çok sayıda UI öğesi oluşturmak için hem bellek hem de işlemci bakımından yoğun bir şekilde yoğundur. <xref:System.Windows.Controls.VirtualizingStackPanel>(tarafından sunulan işlevleri aracılığıyla <xref:System.Windows.Controls.VirtualizingPanel> ) görünür öğeleri hesaplar ve ' <xref:System.Windows.Controls.ItemContainerGenerator> den (veya gibi) ile birlikte çalışarak <xref:System.Windows.Controls.ItemsControl> <xref:System.Windows.Controls.ListBox> <xref:System.Windows.Controls.ListView> yalnızca görünür öğeler için öğeleri oluşturun.  
  
 <xref:System.Windows.Controls.VirtualizingStackPanel>Öğesi, gibi denetimler için öğe ana bilgisayar olarak otomatik olarak ayarlanır <xref:System.Windows.Controls.ListBox> . Veri ile bağlantılı bir koleksiyon barındırırken içerik bir a sınırları içinde olduğu sürece otomatik olarak sanallaştırılır <xref:System.Windows.Controls.ScrollViewer> . Bu, çok sayıda alt öğe barındırırken performansı önemli ölçüde artırır.  
  
 Aşağıdaki biçimlendirme, <xref:System.Windows.Controls.VirtualizingStackPanel> öğesinin bir öğe ana bilgisayarı olarak nasıl kullanılacağını göstermektedir. <xref:System.Windows.Controls.VirtualizingStackPanel.IsVirtualizingProperty?displayProperty=nameWithType> `true` Sanallaştırmanın gerçekleşmesi için iliştirilmiş özelliğin (varsayılan) olarak ayarlanması gerekir.  
  
 [!code-xaml[VirtualizingStackPanel_Intro#1](~/samples/snippets/csharp/VS_Snippets_Wpf/VirtualizingStackPanel_Intro/CS/default.xaml#1)]  
  
<a name="Panels_overview_WrapPanel"></a>
### <a name="wrappanel"></a>WrapPanel  
 <xref:System.Windows.Controls.WrapPanel>alt öğeleri, üst kapsayıcısının kenarına ulaştığında bir sonraki satıra doğru bir şekilde, alt öğeleri sıralı konumda konumlandırmak için kullanılır. İçerik yatay veya dikey olarak yönetilebilir. <xref:System.Windows.Controls.WrapPanel>basit akan senaryolar için yararlıdır [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] . Bu, tüm alt öğelerine tek biçimli boyutlandırma uygulamak için de kullanılabilir.  
  
 Aşağıdaki örnek, <xref:System.Windows.Controls.WrapPanel> <xref:System.Windows.Controls.Button> kapsayıcının kenarına ulaşan denetimleri göstermek için nasıl oluşturulacağını gösterir.  
  
 [!code-cpp[WrapPanel_Intro#1](~/samples/snippets/cpp/VS_Snippets_Wpf/WrapPanel_Intro/CPP/WrapPanel_Code.cpp#1)]
 [!code-csharp[WrapPanel_Intro#1](~/samples/snippets/csharp/VS_Snippets_Wpf/WrapPanel_Intro/CSharp/WrapPanel_Code.cs#1)]
 [!code-vb[WrapPanel_Intro#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WrapPanel_Intro/VisualBasic/WrapPanel_vb.vb#1)]
 [!code-xaml[WrapPanel_Intro#1](~/samples/snippets/xaml/VS_Snippets_Wpf/WrapPanel_Intro/XAML/default.xaml#1)]  
  
 Derlenen uygulama, şuna benzeyen yeni bir oluşturur [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] .  
  
 ![Tipik bir WrapPanel öğesi.](./media/wrappanel-element.PNG "WrapPanel_Element")  
  
<a name="Panels_nested_panel_elements"></a>
## <a name="nested-panel-elements"></a>İç içe Panel öğeleri  
 <xref:System.Windows.Controls.Panel>Karmaşık düzenler oluşturmak için Öğeler birbirlerine iç içe eklenebilir. Bu <xref:System.Windows.Controls.Panel> , birinin bir bölümü için ideal olduğu [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] , ancak farklı bir bölümünün ihtiyaçlarını karşılayamadığı durumlarda çok faydalı olabilir [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] .  
  
 Uygulamanızın destekleyebileceğinden iç içe geçme miktarı için pratik bir sınır yoktur, ancak uygulamanızı yalnızca istediğiniz düzen için gerçekten gerekli olan panoları kullanacak şekilde sınırlamak genellikle en iyisidir. Çoğu durumda, bir <xref:System.Windows.Controls.Grid> Düzen kapsayıcısı olarak esnekliği nedeniyle iç içe geçmiş paneller yerine bir öğe kullanılabilir. Bu, gereksiz öğeleri ağaçta tutarak uygulamanızdaki performansı artırabilir.  
  
 Aşağıdaki örnek, [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] belirli bir düzene ulaşmak için iç içe geçmiş öğelerin avantajlarından yararlanan bir oluşturmayı gösterir <xref:System.Windows.Controls.Panel> . Bu durumda, bir <xref:System.Windows.Controls.DockPanel> öğe yapı sağlamak için kullanılır [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] ve iç içe <xref:System.Windows.Controls.StackPanel> öğeler, a <xref:System.Windows.Controls.Grid> ve, <xref:System.Windows.Controls.Canvas> alt öğeleri üst öğe içinde tam olarak konumlandırmak için kullanılır <xref:System.Windows.Controls.DockPanel> .  
  
 [!code-csharp[Nested_Panels#1](~/samples/snippets/csharp/VS_Snippets_Wpf/Nested_Panels/CSharp/nestedpanels.cs#1)]
 [!code-vb[Nested_Panels#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Nested_Panels/VisualBasic/nestedpanels.vb#1)]  
  
 Derlenen uygulama, şuna benzeyen yeni bir oluşturur [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] .  
  
 ![İç içe panellerden faydalanan bir kullanıcı arabirimi.](./media/nested-panels.PNG "nested_panels")  
  
<a name="Panels_custom_panel_elements"></a>
## <a name="custom-panel-elements"></a>Özel Panel öğeleri  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]Esnek düzen denetimleri dizisi sağlarken, ve yöntemleri geçersiz kılarak özel düzen davranışları da elde edilebilir <xref:System.Windows.FrameworkElement.ArrangeOverride%2A> <xref:System.Windows.FrameworkElement.MeasureOverride%2A> . Özel boyutlandırma ve konumlandırma, bu geçersiz kılma yöntemleri içinde yeni konumlandırma davranışları tanımlayarak gerçekleştirilebilir.  
  
 Benzer şekilde, türetilmiş sınıfları temel alan özel düzen davranışları ( <xref:System.Windows.Controls.Canvas> veya gibi <xref:System.Windows.Controls.Grid> ), ve yöntemleri geçersiz kılınarak <xref:System.Windows.FrameworkElement.ArrangeOverride%2A> tanımlanabilir <xref:System.Windows.FrameworkElement.MeasureOverride%2A> .  
  
 Aşağıdaki biçimlendirme özel bir öğenin nasıl oluşturulacağını göstermektedir <xref:System.Windows.Controls.Panel> . Bu yeni <xref:System.Windows.Controls.Panel> , olarak tanımlanan `PlotPanel` , sabit kodlanmış *x* ve *y* koordinatları kullanılarak alt öğelerin konumlandırılmasını destekler. Bu örnekte, bir <xref:System.Windows.Shapes.Rectangle> öğe (gösterilmez), çizim noktası 50 (*x*) ve 50 (*y*) konumuna yerleştirilir.  
  
 [!code-cpp[PlotPanel#1](~/samples/snippets/cpp/VS_Snippets_Wpf/PlotPanel/CPP/PlotPanel.cpp#1)]
 [!code-csharp[PlotPanel#1](~/samples/snippets/csharp/VS_Snippets_Wpf/PlotPanel/CSharp/PlotPanel.cs#1)]
 [!code-vb[PlotPanel#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PlotPanel/VisualBasic/PlotPanel.vb#1)]  
  
 Daha karmaşık bir özel panel uygulamasını görüntülemek için bkz. [özel Içerik sarmalama paneli örneği oluşturma](https://go.microsoft.com/fwlink/?LinkID=159979).  
  
<a name="Panels_global_localization"></a>
## <a name="localizationglobalization-support"></a>Yerelleştirme/genelleştirme desteği  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]yerelleştirilebilir oluşturulmasına yardımcı olan birçok özelliği destekler [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] .  
  
 Tüm Panel öğeleri <xref:System.Windows.FrameworkElement.FlowDirection%2A> , bir kullanıcının yerel ayarlarına veya dil ayarlarına bağlı olarak içeriği dinamik olarak yeniden akıtmak için kullanılabilen özelliğini yerel olarak destekler. Daha fazla bilgi için bkz. <xref:System.Windows.FrameworkElement.FlowDirection%2A>.  
  
 <xref:System.Windows.Window.SizeToContent%2A>Özelliği, uygulama geliştiricilerinin yerelleştirilmiş ihtiyaçlarını tahmin etmesini sağlayan bir mekanizma sağlar [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] . <xref:System.Windows.SizeToContent.WidthAndHeight>Bu özelliğin değerini kullanarak, bir üst öğe <xref:System.Windows.Window> içeriği her zaman dinamik olarak boyutlandırır ve yapay yükseklik veya genişlik kısıtlamalarına göre kısıtlanmaz.  
  
 <xref:System.Windows.Controls.DockPanel>, <xref:System.Windows.Controls.Grid> ve <xref:System.Windows.Controls.StackPanel> yerelleştirilebilir için tüm iyi seçeneklerdir [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] . <xref:System.Windows.Controls.Canvas>, doğru bir seçim değildir, çünkü içeriği kesinlikle konumlandırır, yerelleştirilmesi zordur.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]Yerelleştirilebilir kullanıcı arabirimleri (UG 'ler) ile uygulama oluşturma hakkında daha fazla bilgi için bkz. [Otomatik düzeni kullanma genel bakış](../advanced/use-automatic-layout-overview.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [İzlenecek yol: İlk WPF masaüstü uygulamam](../getting-started/walkthrough-my-first-wpf-desktop-application.md)
- [WPF düzen Galerisi örneği](https://go.microsoft.com/fwlink/?LinkID=160054)
- [Düzen](../advanced/layout.md)
- [WPF denetimleri Galeri örneği](https://github.com/Microsoft/WPF-Samples/tree/master/Getting%20Started/ControlsAndLayout)
- [Hizalama, Kenar Boşlukları ve Doldurmaya Genel Bakış](../advanced/alignment-margins-and-padding-overview.md)
- [Özel Içerik sarmalama paneli örneği oluşturma](https://go.microsoft.com/fwlink/?LinkID=159979)
- [Ekli Özelliklere Genel Bakış](../advanced/attached-properties-overview.md)
- [Otomatik Düzen Kullanımına Genel Bakış](../advanced/use-automatic-layout-overview.md)
- [Düzen ve Tasarım](../advanced/optimizing-performance-layout-and-design.md)
