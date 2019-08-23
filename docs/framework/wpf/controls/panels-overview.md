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
ms.openlocfilehash: 5fe464f2b79fa1f7b0674c049110d32f2ad32335
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69944814"
---
# <a name="panels-overview"></a>Panellere Genel Bakış
<xref:System.Windows.Controls.Panel>öğeler öğelerin işlenmesini denetleyen bileşenlerdir: boyut ve boyutlar, bunların konumları ve alt içeriklerinin yerleşimi. , [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] Bir dizi önceden tanımlanmış <xref:System.Windows.Controls.Panel> öğe ve özel <xref:System.Windows.Controls.Panel> öğe oluşturma özelliğini sağlar.  
  
 Bu konuda aşağıdaki bölümleri içerir.  
  
- [Panel sınıfı](#Panels_view_from_10000_feet)  
  
- [Panel öğesi ortak üyeleri](#Panels_declared_members)  
  
- [Türetilmiş Panel öğeleri](#Panels_derived_elements)  
  
- [Kullanıcı arabirimi bölmeleri](#Panels_main_UI_elements)  
  
- [İç içe Panel öğeleri](#Panels_nested_panel_elements)  
  
- [Özel Panel öğeleri](#Panels_custom_panel_elements)  
  
- [Yerelleştirme/genelleştirme desteği](#Panels_global_localization)  
  
<a name="Panels_view_from_10000_feet"></a>   
## <a name="the-panel-class"></a>Panel sınıfı  
 <xref:System.Windows.Controls.Panel>, içinde [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]düzen desteği sağlayan tüm öğeler için temel sınıftır. Türetilmiş <xref:System.Windows.Controls.Panel> öğeler, [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] ve kodundaki öğeleri konumlandırmak ve düzenlemek için kullanılır.  
  
 , [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Birçok karmaşık düzeni etkinleştiren kapsamlı bir türetilmiş panel uygulamaları paketini içerir. Bu türetilmiş sınıflar, çoğu standart [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] senaryoyu etkinleştiren özellikleri ve yöntemleri sunar. İhtiyaçlarını karşılayan bir alt düzenleme davranışı bulamadığı geliştiriciler, <xref:System.Windows.FrameworkElement.ArrangeOverride%2A> ve <xref:System.Windows.FrameworkElement.MeasureOverride%2A> yöntemlerini geçersiz kılarak yeni düzenler oluşturabilir. Özel düzen davranışları hakkında daha fazla bilgi için bkz. [Özel Panel öğeleri](#Panels_custom_panel_elements).  
  
<a name="Panels_declared_members"></a>   
## <a name="panel-common-members"></a>Panel ortak Üyeler  
 Tüm <xref:System.Windows.Controls.Panel> öğeler,,,,, <xref:System.Windows.FrameworkElement.Height%2A>ve <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> <xref:System.Windows.FrameworkElement> <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> <xref:System.Windows.FrameworkElement.Width%2A> dahilolmaküzeretarafındantanımlanantemelboyutlandırmavekonumlandırmaözelliklerinidestekler.<xref:System.Windows.FrameworkElement.LayoutTransform%2A> <xref:System.Windows.FrameworkElement.Margin%2A> Tarafından <xref:System.Windows.FrameworkElement>tanımlanan özellikleri konumlandırma hakkında daha fazla bilgi için bkz. [Hizalama, kenar boşlukları ve doldurmaya genel bakış](../advanced/alignment-margins-and-padding-overview.md).  
  
 <xref:System.Windows.Controls.Panel>düzeni anlamak ve kullanmak için kritik öneme sahip ek özellikler sunar. Özelliği, bir türetilmiş Panel öğesinin sınırları arasındaki alanı bir <xref:System.Windows.Media.Brush>ile dolduracak şekilde kullanılır. <xref:System.Windows.Controls.Panel.Background%2A> <xref:System.Windows.Controls.Panel.Children%2A>öğesinin içerdiği <xref:System.Windows.Controls.Panel> öğelerin alt koleksiyonunu temsil eder. <xref:System.Windows.Controls.Panel.InternalChildren%2A><xref:System.Windows.Controls.Panel.Children%2A> koleksiyonun içeriğini ve veri bağlama tarafından oluşturulan üyeleri temsil eder. Her ikisi de üst <xref:System.Windows.Controls.UIElementCollection> <xref:System.Windows.Controls.Panel>öğe içinde barındırılan alt öğelerinden oluşur.  
  
 Panel Ayrıca, türetilmiş <xref:System.Windows.Controls.Panel.ZIndex%2A?displayProperty=nameWithType> <xref:System.Windows.Controls.Panel>bir üzerinde katmanlı sıra elde etmek için kullanılabilecek iliştirilmiş bir özellik sunar. Daha yüksek <xref:System.Windows.Controls.Panel.Children%2A> <xref:System.Windows.Controls.Panel.ZIndex%2A?displayProperty=nameWithType> bir değere sahip bir Panel koleksiyonunun üyeleri, daha düşük <xref:System.Windows.Controls.Panel.ZIndex%2A?displayProperty=nameWithType> bir değere sahip olanların önünde görüntülenir. Bu, özellikle <xref:System.Windows.Controls.Canvas> ve <xref:System.Windows.Controls.Grid> alt öğelerin aynı koordinat alanını paylaşmasına izin veren panolar için yararlıdır.  
  
 <xref:System.Windows.Controls.Panel>Ayrıca, <xref:System.Windows.Controls.Panel.OnRender%2A> <xref:System.Windows.Controls.Panel>öğesinin varsayılan sunum davranışını geçersiz kılmak için kullanılabilen yöntemini tanımlar.  
  
#### <a name="attached-properties"></a>Ekli Özellikler  
 Türetilmiş Panel öğeleri, ekli özelliklerden oluşan kapsamlı kullanımı kolaylaştırır. İliştirilmiş bir özellik, geleneksel ortak dil çalışma zamanı (CLR) özelliği "sarmalayıcı" olmayan, bağımlılık özelliği 'nin özelleşmiş bir biçimidir. Eklenmiş Özellikler ' de [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], izleyen bazı örneklerde görünebilen özel bir sözdizimi vardır.  
  
 İliştirilmiş bir özelliğin amacı, alt öğelerin gerçekten üst öğe tarafından tanımlanan bir özelliğin benzersiz değerlerini depolamasına izin versağlamaktır. Bu işlevselliğin bir uygulaması, alt öğelerin, [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]uygulama düzeni için son derece faydalı olan ' de nasıl sunulmasını istediğinizi bilgilendirmesini sağlar. Daha fazla bilgi için bkz. [ekli özelliklere genel bakış](../advanced/attached-properties-overview.md).  
  
<a name="Panels_derived_elements"></a>   
## <a name="derived-panel-elements"></a>Türetilmiş Panel öğeleri  
 Birçok nesne öğesinden <xref:System.Windows.Controls.Panel>türetilir, ancak bunların hepsi kök Düzen sağlayıcıları olarak kullanılmak üzere tasarlanmamıştır. Özellikle<xref:System.Windows.Controls.Canvas>uygulama <xref:System.Windows.Controls.VirtualizingStackPanel> <xref:System.Windows.Controls.Grid> <xref:System.Windows.Controls.StackPanel> <xref:System.Windows.Controls.DockPanel> <xref:System.Windows.Controls.WrapPanel>oluşturmak içintasarlananaltıtanımlanmışPanelsınıfı(,,,,,ve)vardır.[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]  
  
 Her panel öğesi, aşağıdaki tabloda görüldüğü gibi kendi özel işlevselliğini Kapsüller.  
  
|Öğe adı|UI paneli?|Açıklama|  
|------------------|---------------|-----------------|  
|<xref:System.Windows.Controls.Canvas>|Evet|Alt öğeleri <xref:System.Windows.Controls.Canvas> alana göreli olarak açıkça konumlandırabileceğiniz bir alan tanımlar.|  
|<xref:System.Windows.Controls.DockPanel>|Evet|Alt öğeleri yatay veya dikey olarak birbirlerine göre düzenleyebileceğiniz bir alan tanımlar.|  
|<xref:System.Windows.Controls.Grid>|Evet|Sütun ve satırlardan oluşan esnek bir kılavuz alanını tanımlar. Öğesinin alt öğeleri, <xref:System.Windows.Controls.Grid> <xref:System.Windows.FrameworkElement.Margin%2A> özelliği kullanılarak tam olarak konumlandırılmış olabilir.|  
|<xref:System.Windows.Controls.StackPanel>|Evet|Alt öğeleri yatay veya dikey olarak yönelimli tek bir satıra yerleştirir.|  
|<xref:System.Windows.Controls.Primitives.TabPanel>|Hayır|İçindeki sekme düğmelerinin yerleşimini işler <xref:System.Windows.Controls.TabControl>.|  
|<xref:System.Windows.Controls.Primitives.ToolBarOverflowPanel>|Hayır|Bir <xref:System.Windows.Controls.ToolBar> denetim içindeki içeriği düzenler.|  
|<xref:System.Windows.Controls.Primitives.UniformGrid>|Hayır|<xref:System.Windows.Controls.Primitives.UniformGrid>Tüm eşit hücre boyutlarına sahip bir kılavuzdaki alt öğeleri düzenlemek için kullanılır.|  
|<xref:System.Windows.Controls.VirtualizingPanel>|Hayır|, Alt öğelerini "sanallaştırmaya" yardımcı olan panolar için bir temel sınıf sağlar.|  
|<xref:System.Windows.Controls.VirtualizingStackPanel>|Evet|İçeriği yatay veya dikey olarak tek bir satıra göre düzenler ve sanallaştırır.|  
|<xref:System.Windows.Controls.WrapPanel>|Evet|<xref:System.Windows.Controls.WrapPanel>Sol taraftaki alt öğeleri, kapsayan kutunun kenarındaki bir sonraki satıra kadar olan sıralı konumda konumlandırır. Sonraki sıralama, <xref:System.Windows.Controls.WrapPanel.Orientation%2A> özelliğin değerine bağlı olarak yukarıdan aşağıya veya sağdan sola doğru bir şekilde gerçekleşir.|  
  
<a name="Panels_main_UI_elements"></a>   
## <a name="user-interface-panels"></a>Kullanıcı arabirimi bölmeleri  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ' De,,,,, ve <xref:System.Windows.Controls.DockPanel> [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] için en iyi duruma getirilmiş altı panel sınıfı <xref:System.Windows.Controls.Grid>mevcuttur <xref:System.Windows.Controls.StackPanel>: <xref:System.Windows.Controls.VirtualizingStackPanel> <xref:System.Windows.Controls.Canvas>,, <xref:System.Windows.Controls.WrapPanel>,, ve. Bu panel öğelerinin çoğu uygulama için kullanımı kolay, çok yönlü ve genişletilebilir.  
  
 Her türetilmiş <xref:System.Windows.Controls.Panel> öğe boyutlandırma kısıtlamalarını farklı şekilde değerlendirir. Yatay veya dikey <xref:System.Windows.Controls.Panel> yöndeki bir tanıtıcı kısıtlamalarının düzeni nasıl daha öngörülebilir hale getirebilir anlamak.  
  
|**Panel adı**|**x boyutlu**|**y-Dimension**|  
|--------------------|----------------------|----------------------|  
|<xref:System.Windows.Controls.Canvas>|İçerikle kısıtlanmış|İçerikle kısıtlanmış|  
|<xref:System.Windows.Controls.DockPanel>|Kısıtlanmış|Kısıtlanmış|  
|<xref:System.Windows.Controls.StackPanel>(Dikey yön)|Kısıtlanmış|İçerikle kısıtlanmış|  
|<xref:System.Windows.Controls.StackPanel>(Yatay yönlendirme)|İçerikle kısıtlanmış|Kısıtlanmış|  
|<xref:System.Windows.Controls.Grid>|Kısıtlanmış|, Satırlar ve sütunlar için <xref:System.Windows.GridUnitType.Auto> uygulanacak durumlar dışında kısıtlanmış|  
|<xref:System.Windows.Controls.WrapPanel>|İçerikle kısıtlanmış|İçerikle kısıtlanmış|  
  
 Bu öğelerin her birine yönelik daha ayrıntılı açıklamalar ve kullanım örnekleri aşağıda bulabilirsiniz.  
  
<a name="Panels_overview_Canvas_subsection"></a>   
### <a name="canvas"></a>Tuval  
 Öğesi <xref:System.Windows.Controls.Canvas> , mutlak *x* ve *y*koordinatlarına göre içerik konumlandırmasını sağlar. Öğeler benzersiz bir konumda çizilebilirler; ya da öğeler aynı koordinatları kapladıklarında, İşaretlemede görünme sırası öğelerin çizildiği sırayı belirler.  
  
 <xref:System.Windows.Controls.Canvas>, herhangi <xref:System.Windows.Controls.Panel>birinin en esnek düzen desteğini sağlar. Height ve Width özellikleri, tuvalin alanını tanımlamak için kullanılır ve içindeki öğeler, üst <xref:System.Windows.Controls.Canvas>öğenin alanına göre mutlak koordinatları atanır. Dört Ekli Özellik, <xref:System.Windows.Controls.Canvas.Left%2A?displayProperty=nameWithType> <xref:System.Windows.Controls.Canvas.Top%2A?displayProperty=nameWithType>,, <xref:System.Windows.Controls.Canvas.Right%2A?displayProperty=nameWithType> ve <xref:System.Windows.Controls.Canvas.Bottom%2A?displayProperty=nameWithType>, içindeki nesne yerleşimi üzerinde ince denetime izin verir <xref:System.Windows.Controls.Canvas>, böylece Geliştirici öğeleri ekranda hassas bir şekilde konumlandırın ve düzenleyebilir.  
  
#### <a name="cliptobounds-within-a-canvas"></a>Tuval Içindeki Cliptosınırlara  
 <xref:System.Windows.Controls.Canvas>, kendi tanımlı <xref:System.Windows.FrameworkElement.Height%2A> ve <xref:System.Windows.FrameworkElement.Width%2A>dışındaki koordinatlara bile, alt öğeleri ekranda herhangi bir konumda konumlandırabilirsiniz. Ayrıca, <xref:System.Windows.Controls.Canvas> alt öğelerinin boyutundan etkilenmez. Sonuç olarak, alt öğe, üst <xref:System.Windows.Controls.Canvas>öğenin sınırlayıcı dikdörtgeni dışında diğer öğeleri fazla çizmek için mümkündür. Varsayılan davranışı <xref:System.Windows.Controls.Canvas> , alt öğelerin üst <xref:System.Windows.Controls.Canvas>öğenin sınırları dışında çizilsin. Bu davranış istenmeyen ise, <xref:System.Windows.UIElement.ClipToBounds%2A> özelliği olarak `true`ayarlanabilir. Bu, <xref:System.Windows.Controls.Canvas> kendi boyutuna kırpmasına neden olur. <xref:System.Windows.Controls.Canvas>, alt öğelerin sınırlarının dışına çizilmesini sağlayan tek düzen öğesidir.  
  
 Bu davranış, [Width özellikleri karşılaştırma örneğinde](https://go.microsoft.com/fwlink/?LinkID=160050)grafiksel olarak gösterilmiştir.  
  
#### <a name="defining-and-using-a-canvas"></a>Tuval tanımlama ve kullanma  
 Bir <xref:System.Windows.Controls.Canvas> , veya kodu kullanılarak [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] basitçe oluşturulabilir. Aşağıdaki örnek, içeriğin mutlak <xref:System.Windows.Controls.Canvas> olarak konumlandırılması için nasıl kullanılacağını gösterir. Bu kod 3 100 piksellik kareler üretir. İlk kare kırmızı ve sol üst (*x, y*) konumu (0, 0) olarak belirtilir. İkinci kare yeşil ve sol üst konumu (100, 100), ilk karenin hemen altına ve sağına eklenir. Üçüncü kare mavi ve sol üst konumu (50, 50), bu nedenle ilk karenin sağ alt çeyreğine ve ikincinin sol üst çeyreğine dahil olur. Üçüncü kare en son düzenlendiği için, diğer iki karenin üzerinde olduğu gibi görünür, diğer bir deyişle, çakışan bölümler üçüncü kutunun rengine varsayılmıştır.  
  
 [!code-csharp[CanvasOvwSample#1](~/samples/snippets/csharp/VS_Snippets_Wpf/CanvasOvwSample/CSharp/Canvas_Ovw_Sample.cs#1)]
 [!code-vb[CanvasOvwSample#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CanvasOvwSample/VisualBasic/canvas_vb.vb#1)]
 [!code-xaml[CanvasOvwSample#1](~/samples/snippets/xaml/VS_Snippets_Wpf/CanvasOvwSample/XAML/default.xaml#1)]  
  
 Derlenen uygulama, şuna benzeyen yeni [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] bir oluşturur.  
  
 ![Tipik bir tuval öğesi.](./media/panel-intro-canvas.PNG "panel_intro_canvas")  
  
<a name="Panels_overview_DockPanel_subsection"></a>   
### <a name="dockpanel"></a>DockPanel  
 Öğesi <xref:System.Windows.Controls.DockPanel> , bir kapsayıcının <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType> kenarları üzerinde içerik konumlandırmak için alt içerik öğelerinde ayarlanan ekli özelliği kullanır. <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType> Veya olarak<xref:System.Windows.Controls.Dock.Bottom>ayarlandığında, alt öğeleri birbirlerinin üzerinde veya altında konumlandırır. <xref:System.Windows.Controls.Dock.Top> <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType> Veya olarak<xref:System.Windows.Controls.Dock.Right>ayarlandığında, alt öğeleri diğerinin sol veya sağ tarafında konumlandırır. <xref:System.Windows.Controls.Dock.Left> Özelliği, son öğesinin bir <xref:System.Windows.Controls.DockPanel>alt öğesi olarak eklenen konumunu belirler. <xref:System.Windows.Controls.DockPanel.LastChildFill%2A>  
  
 Düğme kümesi gibi <xref:System.Windows.Controls.DockPanel> ilgili denetimlerin grubunu konumlandırmak için öğesini kullanabilirsiniz. Alternatif olarak, Microsoft Outlook 'ta bulunanlara benzer bir "paned [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]" oluşturmak için bunu kullanabilirsiniz.  
  
#### <a name="sizing-to-content"></a>Içeriğe boyutlandırma  
 Ve özellikleri belirtilmemişse ,<xref:System.Windows.Controls.DockPanel> içeriğine göre boyutlar. <xref:System.Windows.FrameworkElement.Width%2A> <xref:System.Windows.FrameworkElement.Height%2A> Boyut, alt öğelerinin boyutuna uyum sağlayacak şekilde artırabilir veya azalabilir. Ancak, bu özellikler belirtildiğinde ve sonraki belirtilen alt öğe için artık yer kalmadığında, <xref:System.Windows.Controls.DockPanel> bu alt öğeyi veya sonraki alt öğeleri görüntülemez ve sonraki alt öğeleri ölçmez.  
  
#### <a name="lastchildfill"></a>LastChildFill  
 Varsayılan olarak, bir <xref:System.Windows.Controls.DockPanel> öğenin son alt öğesi kalan, ayrılmamış alanı "doldurur". Bu davranış istenmiyorsa, <xref:System.Windows.Controls.DockPanel.LastChildFill%2A> özelliğini olarak `false`ayarlayın.  
  
#### <a name="defining-and-using-a-dockpanel"></a>DockPanel tanımlama ve kullanma  
 Aşağıdaki örnek, kullanarak <xref:System.Windows.Controls.DockPanel>alanın nasıl bölümleyeceğinizi gösterir. Bir <xref:System.Windows.Controls.Border> üst<xref:System.Windows.Controls.DockPanel>öğenin alt öğesi olarak beş öğe eklenir. Her biri, ' ın bölüm alanı için <xref:System.Windows.Controls.DockPanel> farklı bir konumlama özelliği kullanır. Son öğesi "doldurur" ve kalan ayrılmamış alanı.  
  
 [!code-cpp[DockPanelOvwSample#1](~/samples/snippets/cpp/VS_Snippets_Wpf/DockPanelOvwSample/CPP/DockPanel_Ovw_Sample.cpp#1)]
 [!code-csharp[DockPanelOvwSample#1](~/samples/snippets/csharp/VS_Snippets_Wpf/DockPanelOvwSample/CSharp/DockPanel_Ovw_Sample.cs#1)]
 [!code-vb[DockPanelOvwSample#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DockPanelOvwSample/VisualBasic/dockpanel_vb.vb#1)]
 [!code-xaml[DockPanelOvwSample#1](~/samples/snippets/xaml/VS_Snippets_Wpf/DockPanelOvwSample/XAML/default.xaml#1)]  
  
 Derlenen uygulama, şuna benzeyen yeni [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] bir oluşturur.  
  
 ![Tipik bir DockPanel senaryosu.](./media/panel-intro-dockpanel.PNG "panel_intro_dockpanel")  
  
<a name="Panels_overview_Grid_subsection"></a>   
### <a name="grid"></a>Kılavuz  
 Öğesi <xref:System.Windows.Controls.Grid> , mutlak bir konumlandırma ve tablosal veri denetiminin işlevselliğini birleştirir. , Öğeleri kolayca konumlandırmanızı ve stil eklemenizisağlar.<xref:System.Windows.Controls.Grid> <xref:System.Windows.Controls.Grid>esnek satır ve sütun gruplandırmaları tanımlamanızı sağlar ve hatta birden fazla <xref:System.Windows.Controls.Grid> öğe arasında boyutlandırma bilgilerini paylaşma mekanizması sağlar.  
  
#### <a name="how-is-grid-different-from-table"></a>Kılavuz, tablodan farklı midir?  
 <xref:System.Windows.Documents.Table>ve <xref:System.Windows.Controls.Grid> bazı yaygın işlevleri paylaşabilirsiniz, ancak her biri farklı senaryolar için idealdir. , Akış içeriği içinde kullanılmak üzere tasarlanmıştır (akış içeriği hakkında daha fazla bilgi için bkz. [akış belgesine genel bakış](../advanced/flow-document-overview.md) ). <xref:System.Windows.Documents.Table> Kılavuzlar, formların içinde en iyi şekilde kullanılır (temel olarak, akış içeriğinin dışında herhangi bir yerde). Bir <xref:System.Windows.Documents.FlowDocument>içinde, <xref:System.Windows.Documents.Table> sayfalandırma, sütun yeniden akışı <xref:System.Windows.Controls.Grid> ve içerik seçimi gibi akış içeriği davranışlarını destekler, ancak bunu yapmaz. Diğer taraftan bir, bir satır ve sütun dizinine <xref:System.Windows.Documents.Table> göre öğe ekleme dahil olmak üzere <xref:System.Windows.Controls.Grid> birçok nedenden dolayı en iyi şekilde kullanılır <xref:System.Windows.Documents.FlowDocument>. <xref:System.Windows.Controls.Grid> <xref:System.Windows.Controls.Grid> Öğesi, alt içeriğin katmanlanışını sağlar ve tek bir "hücresinde" birden fazla öğenin var olmasına izin verir. <xref:System.Windows.Documents.Table>katmanlanın desteklemez. Öğesinin <xref:System.Windows.Controls.Grid> alt öğeleri, "hücre" sınırlarının alanına göre mutlak olarak konumlandırılmış olabilir. <xref:System.Windows.Documents.Table>Bu özelliği desteklemez. Son olarak, <xref:System.Windows.Controls.Grid> a 'dan daha açık bir <xref:System.Windows.Documents.Table>ağırdır.  
  
#### <a name="sizing-behavior-of-columns-and-rows"></a>Sütunların ve satırların boyutlandırma davranışı  
 Bir <xref:System.Windows.Controls.Grid> içinde tanımlanan sütunlar ve satırlar, kalan alanı orantılı <xref:System.Windows.GridUnitType.Star> bir şekilde dağıtmak için boyutlandırmanın avantajlarından yararlanabilir. <xref:System.Windows.GridUnitType.Star> Bir satır veya sütunun yükseklik veya genişliği olarak seçildiğinde, bu sütun veya satır, kalan kullanılabilir alanın ağırlıklı oranını alır. Bunun aksine, bir sütun <xref:System.Windows.GridUnitType.Auto>veya satır içindeki içeriğin boyutuna göre eşit bir şekilde dağıtırsınız. Bu değer, kullanırken `*` `2*` [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]veya olarak ifade edilir. İlk durumda, satır veya sütun kullanılabilir alanı bir kez, ikinci durumda iki kez ve bu şekilde alır. Bu tekniği birleştirerek bir ve <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> değeri `Stretch` ile alanı orantılı bir şekilde dağıtmak için, ekran alanı yüzdesine göre düzen alanını bölümlemek mümkündür. <xref:System.Windows.Controls.Grid>, alanı bu şekilde dağıtabilecek tek düzen bölmesi olur.  
  
#### <a name="defining-and-using-a-grid"></a>Kılavuz tanımlama ve kullanma  
 Aşağıdaki örnek, Windows Başlat menüsünde bulunan Çalıştır [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] iletişim kutusunda bulunan ile benzer bir şekilde nasıl oluşturulacağını gösterir.  
  
 [!code-csharp[GridRunDialog#1](~/samples/snippets/csharp/VS_Snippets_Wpf/GridRunDialog/CSharp/window1.xaml.cs#1)]
 [!code-vb[GridRunDialog#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/GridRunDialog/VisualBasic/grid_vb.vb#1)]  
  
 Derlenen uygulama, şuna benzeyen yeni [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] bir oluşturur.  
  
 ![Tipik bir Grid öğesi.](./media/avalon-run-dialog.PNG "avalon_run_dialog")  
  
<a name="Panels_overview_StackPanel_subsection"></a>   
### <a name="stackpanel"></a>StackPanel  
 , Atanan bir yönde öğeleri "yığmanızı" sağlar.<xref:System.Windows.Controls.StackPanel> Varsayılan yığın yönü dikeydir. Özelliği <xref:System.Windows.Controls.StackPanel.Orientation%2A> , içerik akışını denetlemek için kullanılabilir.  
  
#### <a name="stackpanel-vs-dockpanel"></a>StackPanel ile DockPanel  
 <xref:System.Windows.Controls.StackPanel> Ayrıca, <xref:System.Windows.Controls.DockPanel> alt öğeleri de "yığmaya" ve bazı kullanım senaryolarında benzer sonuçlar üretmese de olabilir.<xref:System.Windows.Controls.DockPanel> Örneğin, alt öğelerinin sırası, boyutunu ' a değil <xref:System.Windows.Controls.DockPanel> <xref:System.Windows.Controls.StackPanel>, ' de etkileyebilir. Bunun nedeni, <xref:System.Windows.Controls.StackPanel> <xref:System.Double.PositiveInfinity>üzerindeyığınlamayönündeki ölçülerin yalnızca kullanılabilir boyutunu ölçüledir.<xref:System.Windows.Controls.DockPanel>  
  
 Aşağıdaki örnek bu temel farkı gösterir.  
  
 [!code-cpp[StackPanelOvw4#1](~/samples/snippets/cpp/VS_Snippets_Wpf/StackPanelOvw4/CPP/StackPanel_Ovw_Sample4.cpp#1)]
 [!code-csharp[StackPanelOvw4#1](~/samples/snippets/csharp/VS_Snippets_Wpf/StackPanelOvw4/CSharp/StackPanel_Ovw_Sample4.cs#1)]
 [!code-vb[StackPanelOvw4#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StackPanelOvw4/VisualBasic/StackPanelSamp.vb#1)]
 [!code-xaml[StackPanelOvw4#1](~/samples/snippets/xaml/VS_Snippets_Wpf/StackPanelOvw4/XAML/default.xaml#1)]  
  
 İşleme davranışlarındaki fark bu görüntüde görülebilir.  
  
 ![Yakala StackPanel ile DockPanel ekran]görüntüsü(./media/layout-smiley-stackpanel.PNG "layout_smiley_stackpanel")  
  
#### <a name="defining-and-using-a-stackpanel"></a>StackPanel tanımlama ve kullanma  
 Aşağıdaki örnek, bir <xref:System.Windows.Controls.StackPanel> dikey konumlandırılmış düğme kümesi oluşturmak için öğesinin nasıl kullanılacağını gösterir. Yatay konumlandırma için <xref:System.Windows.Controls.StackPanel.Orientation%2A> özelliğini olarak <xref:System.Windows.Controls.Orientation.Horizontal>ayarlayın.  
  
 [!code-csharp[StackPanel_ovw2#1](~/samples/snippets/csharp/VS_Snippets_Wpf/StackPanel_ovw2/CSharp/StackPanel_Ovw_Sample2.cs#1)]
 [!code-vb[StackPanel_ovw2#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StackPanel_ovw2/VisualBasic/StackPanelOvw.vb#1)]  
  
 Derlenen uygulama, şuna benzeyen yeni [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] bir oluşturur.  
  
 ![Tipik bir StackPanel öğesi.](./media/panel-intro-stackpanel.PNG "panel_intro_stackpanel")  
  
<a name="Panels_overview_VirtualizingStackPanel_subsection"></a>   
#### <a name="virtualizingstackpanel"></a>VirtualizingStackPanel  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]Ayrıca, <xref:System.Windows.Controls.StackPanel> veri bağlantılı alt içeriği otomatik olarak "sanallaştırın" bir öğe çeşitlemesi sağlar. Bu bağlamda, sanalbir sözcük, öğelerin bir alt kümesinin ekranda görünür olduğu çok fazla sayıda veri öğesinden oluşturulduğu bir tekniğe başvurur. Belirli bir zamanda ekranda yalnızca birkaç tane olabilir, çok sayıda UI öğesi oluşturmak için hem bellek hem de işlemci bakımından yoğun bir şekilde yoğundur. <xref:System.Windows.Controls.VirtualizingStackPanel>( <xref:System.Windows.Controls.VirtualizingPanel>tarafından sunulan işlevsellik aracılığıyla) görünür öğeleri hesaplar ve ' <xref:System.Windows.Controls.ListBox> <xref:System.Windows.Controls.ItemContainerGenerator> den <xref:System.Windows.Controls.ItemsControl> (veya <xref:System.Windows.Controls.ListView>gibi) ile birlikte çalışarak yalnızca görünür öğeler için öğeleri oluşturur.  
  
 <xref:System.Windows.Controls.VirtualizingStackPanel> Öğesi ,<xref:System.Windows.Controls.ListBox>gibi denetimler için öğe ana bilgisayar olarak otomatik olarak ayarlanır. Veri ile bağlantılı bir koleksiyon barındırırken içerik bir a <xref:System.Windows.Controls.ScrollViewer>sınırları içinde olduğu sürece otomatik olarak sanallaştırılır. Bu, çok sayıda alt öğe barındırırken performansı önemli ölçüde artırır.  
  
 Aşağıdaki biçimlendirme, öğesinin bir <xref:System.Windows.Controls.VirtualizingStackPanel> öğe ana bilgisayarı olarak nasıl kullanılacağını göstermektedir. Sanallaştırmanın gerçekleşmesi için `true` iliştirilmişözelliğin(varsayılan)olarakayarlanmasıgerekir.<xref:System.Windows.Controls.VirtualizingStackPanel.IsVirtualizingProperty?displayProperty=nameWithType>  
  
 [!code-xaml[VirtualizingStackPanel_Intro#1](~/samples/snippets/csharp/VS_Snippets_Wpf/VirtualizingStackPanel_Intro/CS/default.xaml#1)]  
  
<a name="Panels_overview_WrapPanel"></a>   
### <a name="wrappanel"></a>WrapPanel  
 <xref:System.Windows.Controls.WrapPanel>alt öğeleri, üst kapsayıcısının kenarına ulaştığında bir sonraki satıra doğru bir şekilde, alt öğeleri sıralı konumda konumlandırmak için kullanılır. İçerik yatay veya dikey olarak yönetilebilir. <xref:System.Windows.Controls.WrapPanel>basit akan [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] senaryolar için yararlıdır. Bu, tüm alt öğelerine tek biçimli boyutlandırma uygulamak için de kullanılabilir.  
  
 Aşağıdaki örnek, kapsayıcının kenarına ulaşan denetimleri göstermek <xref:System.Windows.Controls.WrapPanel> <xref:System.Windows.Controls.Button> için nasıl oluşturulacağını gösterir.  
  
 [!code-cpp[WrapPanel_Intro#1](~/samples/snippets/cpp/VS_Snippets_Wpf/WrapPanel_Intro/CPP/WrapPanel_Code.cpp#1)]
 [!code-csharp[WrapPanel_Intro#1](~/samples/snippets/csharp/VS_Snippets_Wpf/WrapPanel_Intro/CSharp/WrapPanel_Code.cs#1)]
 [!code-vb[WrapPanel_Intro#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WrapPanel_Intro/VisualBasic/WrapPanel_vb.vb#1)]
 [!code-xaml[WrapPanel_Intro#1](~/samples/snippets/xaml/VS_Snippets_Wpf/WrapPanel_Intro/XAML/default.xaml#1)]  
  
 Derlenen uygulama, şuna benzeyen yeni [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] bir oluşturur.  
  
 ![Tipik bir WrapPanel öğesi.](./media/wrappanel-element.PNG "WrapPanel_Element")  
  
<a name="Panels_nested_panel_elements"></a>   
## <a name="nested-panel-elements"></a>İç içe Panel öğeleri  
 <xref:System.Windows.Controls.Panel>Karmaşık düzenler oluşturmak için Öğeler birbirlerine iç içe eklenebilir. Bu, birinin <xref:System.Windows.Controls.Panel> bir [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]bölümü için ideal olduğu, ancak farklı [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]bir bölümünün ihtiyaçlarını karşılayamadığı durumlarda çok faydalı olabilir.  
  
 Uygulamanızın destekleyebileceğinden iç içe geçme miktarı için pratik bir sınır yoktur, ancak uygulamanızı yalnızca istediğiniz düzen için gerçekten gerekli olan panoları kullanacak şekilde sınırlamak genellikle en iyisidir. Çoğu durumda, bir düzen <xref:System.Windows.Controls.Grid> kapsayıcısı olarak esnekliği nedeniyle iç içe geçmiş paneller yerine bir öğe kullanılabilir. Bu, gereksiz öğeleri ağaçta tutarak uygulamanızdaki performansı artırabilir.  
  
 Aşağıdaki örnek, belirli bir düzene ulaşmak için [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] iç içe geçmiş <xref:System.Windows.Controls.Panel> öğelerin avantajlarından yararlanan bir oluşturmayı gösterir. <xref:System.Windows.Controls.DockPanel> Bu durumda, bir öğe yapı sağlamak [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] için kullanılır ve iç içe <xref:System.Windows.Controls.StackPanel> öğeler, a <xref:System.Windows.Controls.Grid>ve <xref:System.Windows.Controls.Canvas> , alt öğeleri üst <xref:System.Windows.Controls.DockPanel>öğe içinde tam olarak konumlandırmak için kullanılır.  
  
 [!code-csharp[Nested_Panels#1](~/samples/snippets/csharp/VS_Snippets_Wpf/Nested_Panels/CSharp/nestedpanels.cs#1)]
 [!code-vb[Nested_Panels#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Nested_Panels/VisualBasic/nestedpanels.vb#1)]  
  
 Derlenen uygulama, şuna benzeyen yeni [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] bir oluşturur.  
  
 ![İç içe panellerden faydalanan bir kullanıcı arabirimi.](./media/nested-panels.PNG "nested_panels")  
  
<a name="Panels_custom_panel_elements"></a>   
## <a name="custom-panel-elements"></a>Özel Panel öğeleri  
 Esnek [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] düzen denetimleri dizisi sağlarken, <xref:System.Windows.FrameworkElement.ArrangeOverride%2A> ve <xref:System.Windows.FrameworkElement.MeasureOverride%2A> yöntemleri geçersiz kılarak özel düzen davranışları da elde edilebilir. Özel boyutlandırma ve konumlandırma, bu geçersiz kılma yöntemleri içinde yeni konumlandırma davranışları tanımlayarak gerçekleştirilebilir.  
  
 Benzer şekilde, türetilmiş sınıfları temel alan özel düzen davranışları <xref:System.Windows.Controls.Canvas> (veya <xref:System.Windows.Controls.Grid>gibi), <xref:System.Windows.FrameworkElement.ArrangeOverride%2A> ve <xref:System.Windows.FrameworkElement.MeasureOverride%2A> yöntemleri geçersiz kılınarak tanımlanabilir.  
  
 Aşağıdaki biçimlendirme özel <xref:System.Windows.Controls.Panel> bir öğenin nasıl oluşturulacağını göstermektedir. Bu yeni <xref:System.Windows.Controls.Panel>, `PlotPanel`olarak tanımlanan, sabit kodlanmış *x* ve *y*koordinatları kullanılarak alt öğelerin konumlandırılmasını destekler. Bu örnekte, bir <xref:System.Windows.Shapes.Rectangle> öğe (gösterilmez), çizim noktası 50 (*x*) ve 50 (*y*) konumuna yerleştirilir.  
  
 [!code-cpp[PlotPanel#1](~/samples/snippets/cpp/VS_Snippets_Wpf/PlotPanel/CPP/PlotPanel.cpp#1)]
 [!code-csharp[PlotPanel#1](~/samples/snippets/csharp/VS_Snippets_Wpf/PlotPanel/CSharp/PlotPanel.cs#1)]
 [!code-vb[PlotPanel#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PlotPanel/VisualBasic/PlotPanel.vb#1)]  
  
 Daha karmaşık bir özel panel uygulamasını görüntülemek için bkz. [özel Içerik sarmalama paneli örneği oluşturma](https://go.microsoft.com/fwlink/?LinkID=159979).  
  
<a name="Panels_global_localization"></a>   
## <a name="localizationglobalization-support"></a>Yerelleştirme/genelleştirme desteği  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]yerelleştirilebilir [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]oluşturulmasına yardımcı olan birçok özelliği destekler.  
  
 Tüm Panel öğeleri, bir kullanıcının <xref:System.Windows.FrameworkElement.FlowDirection%2A> yerel ayarlarına veya dil ayarlarına bağlı olarak içeriği dinamik olarak yeniden akıtmak için kullanılabilen özelliğini yerel olarak destekler. Daha fazla bilgi için bkz. <xref:System.Windows.FrameworkElement.FlowDirection%2A>.  
  
 Özelliği <xref:System.Windows.Window.SizeToContent%2A> , uygulama geliştiricilerinin yerelleştirilmiş [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]ihtiyaçlarını tahmin etmesini sağlayan bir mekanizma sağlar. Bu özelliğin <xref:System.Windows.Window> değerini kullanarak, bir üst öğe içeriği her zaman dinamik olarak boyutlandırır ve yapay yükseklik veya genişlik kısıtlamalarına göre kısıtlanmaz. <xref:System.Windows.SizeToContent.WidthAndHeight>  
  
 <xref:System.Windows.Controls.DockPanel>, <xref:System.Windows.Controls.Grid>ve <xref:System.Windows.Controls.StackPanel> yerelleştirilebilir[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]için tüm iyi seçeneklerdir. <xref:System.Windows.Controls.Canvas>, doğru bir seçim değildir, çünkü içeriği kesinlikle konumlandırır, yerelleştirilmesi zordur.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Yerelleştirilebilir[!INCLUDE[TLA#tla_ui#plural](../../../../includes/tlasharptla-uisharpplural-md.md)]uygulamalar oluşturma hakkında daha fazla bilgi için bkz. [Otomatik düzeni kullanma genel bakış](../advanced/use-automatic-layout-overview.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [İzlenecek yol: İlk WPF Masaüstü Uygulamam](../getting-started/walkthrough-my-first-wpf-desktop-application.md)
- [WPF düzen Galerisi örneği](https://go.microsoft.com/fwlink/?LinkID=160054)
- [Düzen](../advanced/layout.md)
- [WPF denetimleri Galeri örneği](https://go.microsoft.com/fwlink/?LinkID=160053)
- [Hizalama, Kenar Boşlukları ve Doldurmaya Genel Bakış](../advanced/alignment-margins-and-padding-overview.md)
- [Özel Içerik sarmalama paneli örneği oluşturma](https://go.microsoft.com/fwlink/?LinkID=159979)
- [Ekli Özelliklere Genel Bakış](../advanced/attached-properties-overview.md)
- [Otomatik Düzen Kullanımına Genel Bakış](../advanced/use-automatic-layout-overview.md)
- [Düzen ve Tasarım](../advanced/optimizing-performance-layout-and-design.md)
