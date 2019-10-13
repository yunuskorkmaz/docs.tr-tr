---
title: Panellere genel bakış
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Panel control [WPF], about Panel control
- controls [WPF], Panel
ms.assetid: f73644af-9941-4611-8754-6d4cef03fc44
ms.openlocfilehash: d77ce78fe914bf300c5b33019d7cf67aa4ad74c3
ms.sourcegitcommit: 9c3a4f2d3babca8919a1e490a159c1500ba7a844
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2019
ms.locfileid: "72291451"
---
# <a name="panels-overview"></a>Panellere genel bakış
<xref:System.Windows.Controls.Panel> öğeleri, öğelerin işlenmesini denetleyen bileşenlerdir — boyut ve boyutlar, bunların konumları ve alt içeriklerinin yerleşimi. @No__t-0, bir dizi önceden tanımlanmış <xref:System.Windows.Controls.Panel> öğesi ve özel <xref:System.Windows.Controls.Panel> öğeleri oluşturma özelliğini sağlar.  
  
 Bu konu, aşağıdaki bölümleri içerir.  
  
- [Panel sınıfı](#Panels_view_from_10000_feet)  
  
- [Panel öğesi ortak üyeleri](#Panels_declared_members)  
  
- [Türetilmiş Panel öğeleri](#Panels_derived_elements)  
  
- [Kullanıcı arabirimi bölmeleri](#Panels_main_UI_elements)  
  
- [İç içe Panel öğeleri](#Panels_nested_panel_elements)  
  
- [Özel Panel öğeleri](#Panels_custom_panel_elements)  
  
- [Yerelleştirme/genelleştirme desteği](#Panels_global_localization)  
  
<a name="Panels_view_from_10000_feet"></a>   
## <a name="the-panel-class"></a>Panel sınıfı  
 <xref:System.Windows.Controls.Panel>, [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] ' de düzen desteği sağlayan tüm öğeler için temel sınıftır. Türetilmiş <xref:System.Windows.Controls.Panel> öğeleri, öğeleri [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] ve kodda konumlandırmak ve düzenlemek için kullanılır.  
  
 @No__t-0, birçok karmaşık düzeni etkinleştiren bir türetilmiş panel uygulamaları paketini içerir. Bu türetilmiş sınıflar, çoğu standart [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] senaryoyu etkinleştiren özellikleri ve yöntemleri sunar. İhtiyaçlarını karşılayan bir alt düzenleme davranışı bulamadığı geliştiriciler <xref:System.Windows.FrameworkElement.ArrangeOverride%2A> ve <xref:System.Windows.FrameworkElement.MeasureOverride%2A> yöntemlerini geçersiz kılarak yeni düzenler oluşturabilir. Özel düzen davranışları hakkında daha fazla bilgi için bkz. [Özel Panel öğeleri](#Panels_custom_panel_elements).  
  
<a name="Panels_declared_members"></a>   
## <a name="panel-common-members"></a>Panel ortak Üyeler  
 Tüm <xref:System.Windows.Controls.Panel> öğeleri, <xref:System.Windows.FrameworkElement.Height%2A>, <xref:System.Windows.FrameworkElement.Width%2A>, <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>, <xref:System.Windows.FrameworkElement.VerticalAlignment%2A>, <xref:System.Windows.FrameworkElement.Margin%2A> ve <xref:System.Windows.FrameworkElement.LayoutTransform%2A> dahil olmak üzere <xref:System.Windows.FrameworkElement> tarafından tanımlanan temel boyutlandırma ve konumlandırma özelliklerini destekler. @No__t-0 tarafından tanımlanan özellikleri konumlandırma hakkında daha fazla bilgi için bkz. [Hizalama, kenar boşlukları ve doldurmaya genel bakış](../advanced/alignment-margins-and-padding-overview.md).  
  
 <xref:System.Windows.Controls.Panel>, düzeni anlama ve kullanma konusunda kritik öneme sahip ek özellikler sunar. @No__t-0 özelliği, türetilmiş Panel öğesinin sınırları arasındaki alanı <xref:System.Windows.Media.Brush> ile dolduracak şekilde kullanılır. <xref:System.Windows.Controls.Panel.Children%2A>, <xref:System.Windows.Controls.Panel> ' in içerdiği öğelerin alt koleksiyonunu temsil eder. <xref:System.Windows.Controls.Panel.InternalChildren%2A> <xref:System.Windows.Controls.Panel.Children%2A> koleksiyonun içeriğini ve veri bağlama tarafından oluşturulan üyeleri temsil eder. Her ikisi de üst <xref:System.Windows.Controls.Panel> içinde barındırılan alt öğelerin <xref:System.Windows.Controls.UIElementCollection> ' dan oluşur.  
  
 Panel Ayrıca, türetilmiş bir <xref:System.Windows.Controls.Panel> ' de katmanlı sıraya ulaşmak için kullanılabilecek <xref:System.Windows.Controls.Panel.ZIndex%2A?displayProperty=nameWithType> iliştirilmiş bir özellik sunar. Bir panelin <xref:System.Windows.Controls.Panel.Children%2A> koleksiyonunun daha yüksek <xref:System.Windows.Controls.Panel.ZIndex%2A?displayProperty=nameWithType> değeri olan üyeleri, daha düşük bir <xref:System.Windows.Controls.Panel.ZIndex%2A?displayProperty=nameWithType> değeri olan olanların önünde görünür. Bu, <xref:System.Windows.Controls.Canvas> ve <xref:System.Windows.Controls.Grid> gibi panolar için, alt öğelerin aynı koordinat alanını paylaşmasına izin veren, özellikle yararlıdır.  
  
 <xref:System.Windows.Controls.Panel>, bir <xref:System.Windows.Controls.Panel> ' nin varsayılan sunum davranışını geçersiz kılmak için kullanılabilen <xref:System.Windows.Controls.Panel.OnRender%2A> yöntemini de tanımlar.  
  
#### <a name="attached-properties"></a>Ekli Özellikler  
 Türetilmiş Panel öğeleri, ekli özelliklerden oluşan kapsamlı kullanımı kolaylaştırır. İliştirilmiş bir özellik, geleneksel ortak dil çalışma zamanı (CLR) özelliği "sarmalayıcı" olmayan, bağımlılık özelliği 'nin özelleşmiş bir biçimidir. Ekli özellikler, [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] ' da, izleyen bazı örneklerde görünebilen özel bir sözdizimine sahiptir.  
  
 İliştirilmiş bir özelliğin amacı, alt öğelerin gerçekten üst öğe tarafından tanımlanan bir özelliğin benzersiz değerlerini depolamasına izin versağlamaktır. Bu işlevselliğin bir uygulaması, alt öğelerin, uygulama düzeni için son derece faydalı olan [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] ' da nasıl sunulmasını istediğinizi bilgilendirmesini sağlar. Daha fazla bilgi için bkz. [ekli özelliklere genel bakış](../advanced/attached-properties-overview.md).  
  
<a name="Panels_derived_elements"></a>   
## <a name="derived-panel-elements"></a>Türetilmiş Panel öğeleri  
 Birçok nesne <xref:System.Windows.Controls.Panel> ' dan türetilir, ancak bunların hepsi kök Düzen sağlayıcıları olarak kullanılmak üzere tasarlanmamıştır. Özellikle-6 uygulaması oluşturmak için tasarlanan altı tanımlanmış Panel sınıfı (<xref:System.Windows.Controls.Canvas>, <xref:System.Windows.Controls.DockPanel>, <xref:System.Windows.Controls.Grid>, <xref:System.Windows.Controls.StackPanel>, <xref:System.Windows.Controls.VirtualizingStackPanel> ve <xref:System.Windows.Controls.WrapPanel>) vardır.  
  
 Her panel öğesi, aşağıdaki tabloda görüldüğü gibi kendi özel işlevselliğini Kapsüller.  
  
|Öğe adı|UI paneli?|Açıklama|  
|------------------|---------------|-----------------|  
|<xref:System.Windows.Controls.Canvas>|Yes|Alt öğeleri <xref:System.Windows.Controls.Canvas> alanına göre koordinatlara göre açıkça konumlandırabileceğiniz bir alan tanımlar.|  
|<xref:System.Windows.Controls.DockPanel>|Yes|Alt öğeleri yatay veya dikey olarak birbirlerine göre düzenleyebileceğiniz bir alan tanımlar.|  
|<xref:System.Windows.Controls.Grid>|Yes|Sütun ve satırlardan oluşan esnek bir kılavuz alanını tanımlar. @No__t-0 ' ın alt öğeleri, <xref:System.Windows.FrameworkElement.Margin%2A> özelliği kullanılarak tam olarak konumlandırılmış olabilir.|  
|<xref:System.Windows.Controls.StackPanel>|Yes|Alt öğeleri yatay veya dikey olarak yönelimli tek bir satıra yerleştirir.|  
|<xref:System.Windows.Controls.Primitives.TabPanel>|Hayır|@No__t-0 ' daki sekme düğmelerinin yerleşimini işler.|  
|<xref:System.Windows.Controls.Primitives.ToolBarOverflowPanel>|Hayır|@No__t-0 denetimindeki bir denetim içindeki içeriği düzenler.|  
|<xref:System.Windows.Controls.Primitives.UniformGrid>|Hayır|<xref:System.Windows.Controls.Primitives.UniformGrid>, bir kılavuzdaki alt öğeleri eşit hücre boyutlarına göre düzenlemek için kullanılır.|  
|<xref:System.Windows.Controls.VirtualizingPanel>|Hayır|, Alt öğelerini "sanallaştırmaya" yardımcı olan panolar için bir temel sınıf sağlar.|  
|<xref:System.Windows.Controls.VirtualizingStackPanel>|Yes|İçeriği yatay veya dikey olarak tek bir satıra göre düzenler ve sanallaştırır.|  
|<xref:System.Windows.Controls.WrapPanel>|Yes|<xref:System.Windows.Controls.WrapPanel> alt öğeleri soldan sağa, kapsayan kutunun kenarındaki içerikleri sonraki satıra kadar parçalara konumlandırır. Sonraki sıralama, <xref:System.Windows.Controls.WrapPanel.Orientation%2A> özelliğinin değerine bağlı olarak yukarıdan aşağıya veya sağdan sola doğru bir şekilde gerçekleşir.|  
  
<a name="Panels_main_UI_elements"></a>   
## <a name="user-interface-panels"></a>Kullanıcı arabirimi bölmeleri  
 @No__t-0 ' da bulunan ve [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] senaryolarını destekleyecek şekilde iyileştirilmiş altı panel sınıfı vardır: <xref:System.Windows.Controls.Canvas>, <xref:System.Windows.Controls.DockPanel>, <xref:System.Windows.Controls.Grid>, <xref:System.Windows.Controls.StackPanel>, <xref:System.Windows.Controls.VirtualizingStackPanel> ve <xref:System.Windows.Controls.WrapPanel>. Bu panel öğelerinin çoğu uygulama için kullanımı kolay, çok yönlü ve genişletilebilir.  
  
 Her türetilmiş <xref:System.Windows.Controls.Panel> öğesi boyutlandırma kısıtlamalarını farklı şekilde değerlendirir. @No__t-0 ' ın yatay veya dikey yöndeki kısıtlamaları nasıl işleyeceğini anlamak, düzeni daha öngörülebilir hale getirebilir.  
  
|**Panel adı**|**x boyutlu**|**y-Dimension**|  
|--------------------|----------------------|----------------------|  
|<xref:System.Windows.Controls.Canvas>|İçerikle kısıtlanmış|İçerikle kısıtlanmış|  
|<xref:System.Windows.Controls.DockPanel>|Kısıtlanmış|Kısıtlanmış|  
|<xref:System.Windows.Controls.StackPanel> (dikey yönlendirme)|Kısıtlanmış|İçerikle kısıtlanmış|  
|<xref:System.Windows.Controls.StackPanel> (yatay yönlendirme)|İçerikle kısıtlanmış|Kısıtlanmış|  
|<xref:System.Windows.Controls.Grid>|Kısıtlanmış|@No__t-0 ' ın satırlar ve sütunlar için uygulanacağı durumlar haricinde kısıtlanmış|  
|<xref:System.Windows.Controls.WrapPanel>|İçerikle kısıtlanmış|İçerikle kısıtlanmış|  
  
 Bu öğelerin her birine yönelik daha ayrıntılı açıklamalar ve kullanım örnekleri aşağıda bulabilirsiniz.  
  
<a name="Panels_overview_Canvas_subsection"></a>   
### <a name="canvas"></a>Tuvalinin  
 @No__t-0 öğesi, mutlak *x* ve *y*koordinatlarına göre içerik konumlandırmasını sağlar. Öğeler benzersiz bir konumda çizilebilirler; ya da öğeler aynı koordinatları kapladıklarında, İşaretlemede görünme sırası öğelerin çizildiği sırayı belirler.  
  
 <xref:System.Windows.Controls.Canvas>, herhangi bir <xref:System.Windows.Controls.Panel> ' in en esnek düzen desteğini sağlar. Height ve Width özellikleri, tuvalin alanını tanımlamak için kullanılır ve içindeki öğeler, üst <xref:System.Windows.Controls.Canvas> ' ın alanına göre mutlak koordinatları atanır. Dört Ekli Özellik <xref:System.Windows.Controls.Canvas.Left%2A?displayProperty=nameWithType>, <xref:System.Windows.Controls.Canvas.Top%2A?displayProperty=nameWithType>, <xref:System.Windows.Controls.Canvas.Right%2A?displayProperty=nameWithType> ve <xref:System.Windows.Controls.Canvas.Bottom%2A?displayProperty=nameWithType>, <xref:System.Windows.Controls.Canvas> içinde nesne yerleştirmesi üzerinde ince denetime izin verir, böylece Geliştirici öğeleri ekranda hassas bir şekilde konumlandırın ve düzenleyebilir.  
  
#### <a name="cliptobounds-within-a-canvas"></a>Tuval Içindeki Cliptosınırlara  
 <xref:System.Windows.Controls.Canvas>, kendi tanımlı <xref:System.Windows.FrameworkElement.Height%2A> ve <xref:System.Windows.FrameworkElement.Width%2A> dışındaki koordinatlara bile alt öğeleri ekran üzerinde herhangi bir konumda konumlandırabilirsiniz. Ayrıca, <xref:System.Windows.Controls.Canvas> alt öğelerinin boyutundan etkilenmez. Sonuç olarak, alt öğe @no__t üst öğenin sınırlayıcı dikdörtgeni dışında diğer öğeleri fazla çizmesi mümkündür-0. @No__t-0 ' ın varsayılan davranışı alt öğelerin üst @no__t sınırlarının dışına çizilmesini izin vermelidir. Bu davranış istenmeyen ise, <xref:System.Windows.UIElement.ClipToBounds%2A> özelliği `true` olarak ayarlanabilir. Bu, <xref:System.Windows.Controls.Canvas> ' ın kendi boyutuna kırpmasına neden olur. <xref:System.Windows.Controls.Canvas>, alt öğelerin sınırlarının dışına çizilmesini sağlayan tek düzen öğesidir.  
  
 Bu davranış, [Width özellikleri karşılaştırma örneğinde](https://go.microsoft.com/fwlink/?LinkID=160050)grafiksel olarak gösterilmiştir.  
  
#### <a name="defining-and-using-a-canvas"></a>Tuval tanımlama ve kullanma  
 @No__t-0, yalnızca [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] veya kod kullanılarak oluşturulabilir. Aşağıdaki örnek, içeriğin mutlak olarak konumlandırılması için <xref:System.Windows.Controls.Canvas> ' ın nasıl kullanılacağını gösterir. Bu kod 3 100 piksellik kareler üretir. İlk kare kırmızı ve sol üst (*x, y*) konumu (0, 0) olarak belirtilir. İkinci kare yeşil ve sol üst konumu (100, 100), ilk karenin hemen altına ve sağına eklenir. Üçüncü kare mavi ve sol üst konumu (50, 50), bu nedenle ilk karenin sağ alt çeyreğine ve ikincinin sol üst çeyreğine dahil olur. Üçüncü kare en son düzenlendiği için, diğer iki karenin üzerinde olduğu gibi görünür, diğer bir deyişle, çakışan bölümler üçüncü kutunun rengine varsayılmıştır.  
  
 [!code-csharp[CanvasOvwSample#1](~/samples/snippets/csharp/VS_Snippets_Wpf/CanvasOvwSample/CSharp/Canvas_Ovw_Sample.cs#1)]
 [!code-vb[CanvasOvwSample#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CanvasOvwSample/VisualBasic/canvas_vb.vb#1)]
 [!code-xaml[CanvasOvwSample#1](~/samples/snippets/xaml/VS_Snippets_Wpf/CanvasOvwSample/XAML/default.xaml#1)]  
  
 Derlenen uygulama, şuna benzeyen yeni bir @no__t (0) verir.  
  
 ![Tipik bir tuval öğesi.](./media/panel-intro-canvas.PNG "panel_intro_canvas")  
  
<a name="Panels_overview_DockPanel_subsection"></a>   
### <a name="dockpanel"></a>DockPanel  
 @No__t-0 öğesi, bir kapsayıcının kenarları üzerinde içerik konumlandırmak için alt içerik öğelerinde ayarlanan <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType> ekli özelliğini kullanır. @No__t-0 <xref:System.Windows.Controls.Dock.Top> veya <xref:System.Windows.Controls.Dock.Bottom> olarak ayarlandığında, alt öğeleri birbirlerinin üzerinde veya altında konumlandırır. @No__t-0 <xref:System.Windows.Controls.Dock.Left> veya <xref:System.Windows.Controls.Dock.Right> olarak ayarlandığında, alt öğeleri diğerinin soluna veya sağına konumlandırır. @No__t-0 özelliği, bir <xref:System.Windows.Controls.DockPanel> ' in alt öğesi olarak eklenen son öğenin konumunu belirler.  
  
 @No__t-0 ' ı, bir düğme kümesi gibi ilgili denetimlerin grubunu konumlandırmak için kullanabilirsiniz. Alternatif olarak, Microsoft Outlook 'ta bulunanlara benzer bir "paned" [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] oluşturmak için bunu kullanabilirsiniz.  
  
#### <a name="sizing-to-content"></a>Içeriğe boyutlandırma  
 @No__t-0 ve <xref:System.Windows.FrameworkElement.Width%2A> özellikleri belirtilmemişse, içeriğine <xref:System.Windows.Controls.DockPanel> boyut kullanılır. Boyut, alt öğelerinin boyutuna uyum sağlayacak şekilde artırabilir veya azalabilir. Ancak, bu özellikler belirtildiğinde ve sonraki belirtilen alt öğe için artık yer kalmadığında, <xref:System.Windows.Controls.DockPanel> o alt öğeyi veya sonraki alt öğeleri görüntülemez ve sonraki alt öğeleri ölçmez.  
  
#### <a name="lastchildfill"></a>LastChildFill  
 Varsayılan olarak, <xref:System.Windows.Controls.DockPanel> öğesinin son alt öğesi kalan, ayrılmamış alanı "doldurur". Bu davranış istenmiyorsa <xref:System.Windows.Controls.DockPanel.LastChildFill%2A> özelliğini `false` olarak ayarlayın.  
  
#### <a name="defining-and-using-a-dockpanel"></a>DockPanel tanımlama ve kullanma  
 Aşağıdaki örnek, <xref:System.Windows.Controls.DockPanel> kullanılarak alanın nasıl bölümlenmesi gerektiğini gösterir. Beş <xref:System.Windows.Controls.Border> öğe, üst <xref:System.Windows.Controls.DockPanel> ' in alt öğesi olarak eklenir. Her biri, alanı bölümlemek için <xref:System.Windows.Controls.DockPanel> ' ın farklı bir konumlama özelliğini kullanır. Son öğesi "doldurur" ve kalan ayrılmamış alanı.  
  
 [!code-cpp[DockPanelOvwSample#1](~/samples/snippets/cpp/VS_Snippets_Wpf/DockPanelOvwSample/CPP/DockPanel_Ovw_Sample.cpp#1)]
 [!code-csharp[DockPanelOvwSample#1](~/samples/snippets/csharp/VS_Snippets_Wpf/DockPanelOvwSample/CSharp/DockPanel_Ovw_Sample.cs#1)]
 [!code-vb[DockPanelOvwSample#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DockPanelOvwSample/VisualBasic/dockpanel_vb.vb#1)]
 [!code-xaml[DockPanelOvwSample#1](~/samples/snippets/xaml/VS_Snippets_Wpf/DockPanelOvwSample/XAML/default.xaml#1)]  
  
 Derlenen uygulama, şuna benzeyen yeni bir @no__t (0) verir.  
  
 ![Tipik bir DockPanel senaryosu.](./media/panel-intro-dockpanel.PNG "panel_intro_dockpanel")  
  
<a name="Panels_overview_Grid_subsection"></a>   
### <a name="grid"></a>Çizgisi  
 @No__t-0 öğesi, mutlak bir konumlandırma ve tablosal veri denetiminin işlevselliğini birleştirir. @No__t-0, kolayca konumlandırabilirsiniz ve stil öğeleri sağlar. <xref:System.Windows.Controls.Grid>, esnek satır ve sütun gruplandırmaları tanımlamanızı sağlar ve hatta birden çok <xref:System.Windows.Controls.Grid> öğe arasında boyutlandırma bilgilerini paylaşma mekanizması sağlar.  
  
#### <a name="how-is-grid-different-from-table"></a>Kılavuz, tablodan farklı midir?  
 <xref:System.Windows.Documents.Table> ve <xref:System.Windows.Controls.Grid> bazı yaygın işlevselliği paylaşır, ancak her biri farklı senaryolar için idealdir. @No__t-0, akış içeriği içinde kullanılmak üzere tasarlanmıştır (akış içeriği hakkında daha fazla bilgi için bkz. [Flow belgesine genel bakış](../advanced/flow-document-overview.md) ). Kılavuzlar, formların içinde en iyi şekilde kullanılır (temel olarak, akış içeriğinin dışında herhangi bir yerde). @No__t-0 <xref:System.Windows.Documents.Table>, <xref:System.Windows.Controls.Grid> olmadığı sürece sayfalandırma, sütun yeniden akıtma ve içerik seçimi gibi akış içeriği davranışlarını destekler. Diğer taraftan <xref:System.Windows.Controls.Grid> ' @no__t ın dışında en iyi şekilde <xref:System.Windows.Controls.Grid> ' nin bir satır ve sütun dizinine göre öğeleri eklemesi gibi birçok nedenden dolayı, <xref:System.Windows.Documents.Table> ' ü içermez. @No__t-0 öğesi, alt içeriğin katmanlanışını sağlar ve tek bir "hücresinde" birden fazla öğenin var olmasına izin verir. <xref:System.Windows.Documents.Table> katman katmanlarını desteklemez. @No__t-0 ' ın alt öğeleri, "hücre" sınırlarının alanına göre mutlak olarak konumlandırılmış olabilir. <xref:System.Windows.Documents.Table> bu özelliği desteklemez. Son olarak, <xref:System.Windows.Controls.Grid> <xref:System.Windows.Documents.Table> ' den daha açık ağırlıkdır.  
  
#### <a name="sizing-behavior-of-columns-and-rows"></a>Sütunların ve satırların boyutlandırma davranışı  
 @No__t-0 içinde tanımlanan sütunlar ve satırlar, kalan alanı orantılı bir şekilde dağıtmak için <xref:System.Windows.GridUnitType.Star> boyutlandırmanın avantajlarından yararlanabilir. @No__t-0 bir satır veya sütunun yükseklik veya genişliği olarak seçildiğinde, bu sütun veya satır kalan kullanılabilir alanın ağırlıklı oranını alır. Bu, <xref:System.Windows.GridUnitType.Auto> ' a karşılık gelir. Bu, bir sütun veya satır içindeki içeriğin boyutuna göre eşit bir şekilde dağıtabilecek bir alandır. Bu değer, [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] kullanılırken `*` veya `2*` olarak ifade edilir. İlk durumda, satır veya sütun kullanılabilir alanı bir kez, ikinci durumda iki kez ve bu şekilde alır. Bu tekniği birleştirerek <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> ile alanı orantılı bir şekilde dağıtın @no__t ve `Stretch` değeri, düzen alanının ekran alanı yüzdesine göre bölümlenmesi mümkündür. <xref:System.Windows.Controls.Grid>, alanı bu şekilde dağıtabilecek tek düzen panelidir.  
  
#### <a name="defining-and-using-a-grid"></a>Kılavuz tanımlama ve kullanma  
 Aşağıdaki örnek, Windows Başlat menüsünde bulunan Çalıştır iletişim kutusunda bulunan ile benzer bir @no__t nasıl oluşturulacağını gösterir.  
  
 [!code-csharp[GridRunDialog#1](~/samples/snippets/csharp/VS_Snippets_Wpf/GridRunDialog/CSharp/window1.xaml.cs#1)]
 [!code-vb[GridRunDialog#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/GridRunDialog/VisualBasic/grid_vb.vb#1)]  
  
 Derlenen uygulama, şuna benzeyen yeni bir @no__t (0) verir.  
  
 ![Tipik bir Grid öğesi.](./media/avalon-run-dialog.PNG "avalon_run_dialog")  
  
<a name="Panels_overview_StackPanel_subsection"></a>   
### <a name="stackpanel"></a>StackPanel  
 @No__t-0, atanan bir yönde öğeleri "yığmanızı" sağlar. Varsayılan yığın yönü dikeydir. @No__t-0 özelliği, içerik akışını denetlemek için kullanılabilir.  
  
#### <a name="stackpanel-vs-dockpanel"></a>StackPanel ve DockPanel karşılaştırması  
 @No__t-0 "Stack" alt öğeleri de "Stack" olsa da, <xref:System.Windows.Controls.DockPanel> ve <xref:System.Windows.Controls.StackPanel>, bazı kullanım senaryolarında benzer sonuçlar üretmez. Örneğin, alt öğelerinin sıralaması <xref:System.Windows.Controls.DockPanel> ' daki boyutunu etkileyebilir, ancak <xref:System.Windows.Controls.StackPanel> ' de olamaz. Bunun nedeni, <xref:System.Windows.Controls.StackPanel> ' ı <xref:System.Double.PositiveInfinity> ' deki yığınlama yönünde ölçtüğünden <xref:System.Windows.Controls.DockPanel> ' nin yalnızca kullanılabilir boyutunu ölçtüğünden kaynaklanır.  
  
 Aşağıdaki örnek bu temel farkı gösterir.  
  
 [!code-cpp[StackPanelOvw4#1](~/samples/snippets/cpp/VS_Snippets_Wpf/StackPanelOvw4/CPP/StackPanel_Ovw_Sample4.cpp#1)]
 [!code-csharp[StackPanelOvw4#1](~/samples/snippets/csharp/VS_Snippets_Wpf/StackPanelOvw4/CSharp/StackPanel_Ovw_Sample4.cs#1)]
 [!code-vb[StackPanelOvw4#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StackPanelOvw4/VisualBasic/StackPanelSamp.vb#1)]
 [!code-xaml[StackPanelOvw4#1](~/samples/snippets/xaml/VS_Snippets_Wpf/StackPanelOvw4/XAML/default.xaml#1)]  
  
 İşleme davranışlarındaki fark bu görüntüde görülebilir.  
  
 ![Ekran görüntüsü: StackPanel Ile DockPanel ekran görüntüsü](./media/layout-smiley-stackpanel.PNG "layout_smiley_stackpanel")  
  
#### <a name="defining-and-using-a-stackpanel"></a>StackPanel tanımlama ve kullanma  
 Aşağıdaki örnek, dikey konumlandırılmış düğmeler kümesi oluşturmak için <xref:System.Windows.Controls.StackPanel> ' ın nasıl kullanılacağını gösterir. Yatay konumlandırma için <xref:System.Windows.Controls.StackPanel.Orientation%2A> özelliğini <xref:System.Windows.Controls.Orientation.Horizontal> olarak ayarlayın.  
  
 [!code-csharp[StackPanel_ovw2#1](~/samples/snippets/csharp/VS_Snippets_Wpf/StackPanel_ovw2/CSharp/StackPanel_Ovw_Sample2.cs#1)]
 [!code-vb[StackPanel_ovw2#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StackPanel_ovw2/VisualBasic/StackPanelOvw.vb#1)]  
  
 Derlenen uygulama, şuna benzeyen yeni bir @no__t (0) verir.  
  
 ![Tipik bir StackPanel öğesi.](./media/panel-intro-stackpanel.PNG "panel_intro_stackpanel")  
  
<a name="Panels_overview_VirtualizingStackPanel_subsection"></a>   
#### <a name="virtualizingstackpanel"></a>VirtualizingStackPanel  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ' da, veri bağlantılı alt içeriği otomatik olarak "sanallaştırır" <xref:System.Windows.Controls.StackPanel> öğesinin bir çeşitlemesi de sağlar. Bu bağlamda, sanalbir sözcük, öğelerin bir alt kümesinin ekranda görünür olduğu çok fazla sayıda veri öğesinden oluşturulduğu bir tekniğe başvurur. Belirli bir zamanda ekranda yalnızca birkaç tane olabilir, çok sayıda UI öğesi oluşturmak için hem bellek hem de işlemci bakımından yoğun bir şekilde yoğundur. <xref:System.Windows.Controls.VirtualizingStackPanel> (<xref:System.Windows.Controls.VirtualizingPanel> tarafından sunulan işlevler aracılığıyla) görünür öğeleri hesaplar ve yalnızca görünür öğeler için öğeler oluşturmak üzere bir @no__t 3 ' ten (<xref:System.Windows.Controls.ListBox> veya <xref:System.Windows.Controls.ListView>) <xref:System.Windows.Controls.ItemContainerGenerator> ile birlikte çalışarak.  
  
 @No__t-0 öğesi, <xref:System.Windows.Controls.ListBox> gibi denetimler için öğeler ana bilgisayarı olarak otomatik olarak ayarlanır. Veri ile bağlantılı bir koleksiyon barındırırken, içerik <xref:System.Windows.Controls.ScrollViewer> sınırları içinde olduğu sürece içerik otomatik olarak sanallaştırılır. Bu, çok sayıda alt öğe barındırırken performansı önemli ölçüde artırır.  
  
 Aşağıdaki biçimlendirme <xref:System.Windows.Controls.VirtualizingStackPanel> ' ın bir öğe Konağı olarak nasıl kullanılacağını göstermektedir. @No__t-0 eklenmiş özelliği sanallaştırmanın gerçekleşmesi için `true` (varsayılan) olarak ayarlanmalıdır.  
  
 [!code-xaml[VirtualizingStackPanel_Intro#1](~/samples/snippets/csharp/VS_Snippets_Wpf/VirtualizingStackPanel_Intro/CS/default.xaml#1)]  
  
<a name="Panels_overview_WrapPanel"></a>   
### <a name="wrappanel"></a>WrapPanel  
 <xref:System.Windows.Controls.WrapPanel>, alt öğelerin üst kapsayıcısının kenarına ulaştığında bir sonraki satıra kadar olan alt öğeleri soldan sağa konumlandırmak için kullanılır. İçerik yatay veya dikey olarak yönetilebilir. <xref:System.Windows.Controls.WrapPanel> basit akan [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] senaryolar için yararlıdır. Bu, tüm alt öğelerine tek biçimli boyutlandırma uygulamak için de kullanılabilir.  
  
 Aşağıdaki örnek, kapsayıcının kenarına ulaşan <xref:System.Windows.Controls.Button> denetimlerini göstermek için <xref:System.Windows.Controls.WrapPanel> oluşturmayı gösterir.  
  
 [!code-cpp[WrapPanel_Intro#1](~/samples/snippets/cpp/VS_Snippets_Wpf/WrapPanel_Intro/CPP/WrapPanel_Code.cpp#1)]
 [!code-csharp[WrapPanel_Intro#1](~/samples/snippets/csharp/VS_Snippets_Wpf/WrapPanel_Intro/CSharp/WrapPanel_Code.cs#1)]
 [!code-vb[WrapPanel_Intro#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WrapPanel_Intro/VisualBasic/WrapPanel_vb.vb#1)]
 [!code-xaml[WrapPanel_Intro#1](~/samples/snippets/xaml/VS_Snippets_Wpf/WrapPanel_Intro/XAML/default.xaml#1)]  
  
 Derlenen uygulama, şuna benzeyen yeni bir @no__t (0) verir.  
  
 ![Tipik bir WrapPanel öğesi.](./media/wrappanel-element.PNG "WrapPanel_Element")  
  
<a name="Panels_nested_panel_elements"></a>   
## <a name="nested-panel-elements"></a>İç içe Panel öğeleri  
 <xref:System.Windows.Controls.Panel> öğeleri, karmaşık düzenler oluşturmak için birbirlerine iç içe eklenebilir. Bu, bir <xref:System.Windows.Controls.Panel> [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] ' in bir bölümü için ideal olduğu, ancak [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] ' nin farklı bir kısmının ihtiyaçlarını karşılayamadığı durumlarda çok yararlı olabilir.  
  
 Uygulamanızın destekleyebileceğinden iç içe geçme miktarı için pratik bir sınır yoktur, ancak uygulamanızı yalnızca istediğiniz düzen için gerçekten gerekli olan panoları kullanacak şekilde sınırlamak genellikle en iyisidir. Çoğu durumda, bir <xref:System.Windows.Controls.Grid> öğesi, iç içe geçmiş paneller yerine, bir düzen kapsayıcısı olarak esneklik nedeniyle kullanılabilir. Bu, gereksiz öğeleri ağaçta tutarak uygulamanızdaki performansı artırabilir.  
  
 Aşağıdaki örnek, belirli bir düzene ulaşmak için iç içe <xref:System.Windows.Controls.Panel> öğelerinden faydalanan bir [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] oluşturmayı gösterir. Bu durumda, [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] yapısı sağlamak için bir <xref:System.Windows.Controls.DockPanel> öğesi, iç içe geçmiş <xref:System.Windows.Controls.StackPanel> öğeleri, bir <xref:System.Windows.Controls.Grid> ve @no__t alt öğelerini üst <xref:System.Windows.Controls.DockPanel> içinde konumlandırmak için kullanılır.  
  
 [!code-csharp[Nested_Panels#1](~/samples/snippets/csharp/VS_Snippets_Wpf/Nested_Panels/CSharp/nestedpanels.cs#1)]
 [!code-vb[Nested_Panels#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Nested_Panels/VisualBasic/nestedpanels.vb#1)]  
  
 Derlenen uygulama, şuna benzeyen yeni bir @no__t (0) verir.  
  
 ![İç içe panellerden faydalanan bir kullanıcı arabirimi.](./media/nested-panels.PNG "nested_panels")  
  
<a name="Panels_custom_panel_elements"></a>   
## <a name="custom-panel-elements"></a>Özel Panel öğeleri  
 @No__t-0 esnek düzen denetimleri dizisi sağlarken, özel düzen davranışları <xref:System.Windows.FrameworkElement.ArrangeOverride%2A> ve <xref:System.Windows.FrameworkElement.MeasureOverride%2A> yöntemlerinin geçersiz kılınmasıyla de elde edilebilir. Özel boyutlandırma ve konumlandırma, bu geçersiz kılma yöntemleri içinde yeni konumlandırma davranışları tanımlayarak gerçekleştirilebilir.  
  
 Benzer şekilde, türetilmiş sınıflara dayalı özel düzen davranışları (<xref:System.Windows.Controls.Canvas> veya <xref:System.Windows.Controls.Grid>), @no__t 2 ve <xref:System.Windows.FrameworkElement.MeasureOverride%2A> yöntemleri geçersiz kılınarak tanımlanabilir.  
  
 Aşağıdaki biçimlendirme özel bir <xref:System.Windows.Controls.Panel> öğesinin nasıl oluşturulacağını göstermektedir. @No__t-1 olarak tanımlanan bu yeni <xref:System.Windows.Controls.Panel>, sabit kodlanmış *x* ve *y*koordinatları kullanılarak alt öğelerin konumlandırılmasını destekler. Bu örnekte, <xref:System.Windows.Shapes.Rectangle> öğesi (gösterilmez), 50 (*x*) ve 50 (*y*) çizim noktasında konumlandırılır.  
  
 [!code-cpp[PlotPanel#1](~/samples/snippets/cpp/VS_Snippets_Wpf/PlotPanel/CPP/PlotPanel.cpp#1)]
 [!code-csharp[PlotPanel#1](~/samples/snippets/csharp/VS_Snippets_Wpf/PlotPanel/CSharp/PlotPanel.cs#1)]
 [!code-vb[PlotPanel#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PlotPanel/VisualBasic/PlotPanel.vb#1)]  
  
 Daha karmaşık bir özel panel uygulamasını görüntülemek için bkz. [özel Içerik sarmalama paneli örneği oluşturma](https://go.microsoft.com/fwlink/?LinkID=159979).  
  
<a name="Panels_global_localization"></a>   
## <a name="localizationglobalization-support"></a>Yerelleştirme/genelleştirme desteği  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], yerelleştirilebilir [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] oluşturulmasına yardımcı olan çok sayıda özelliği destekler.  
  
 Tüm Panel öğeleri, bir kullanıcının yerel ayarlarına veya dil ayarlarına göre içeriği dinamik olarak yeniden akıtmak için kullanılabilen <xref:System.Windows.FrameworkElement.FlowDirection%2A> özelliğini yerel olarak destekler. Daha fazla bilgi için bkz. <xref:System.Windows.FrameworkElement.FlowDirection%2A>.  
  
 @No__t-0 özelliği, uygulama geliştiricilerinin yerelleştirilmiş [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] ihtiyaçlarını tahmin etmesini sağlayan bir mekanizma sağlar. Bu özelliğin <xref:System.Windows.SizeToContent.WidthAndHeight> değerini kullanarak, üst <xref:System.Windows.Window> her zaman içeriğe sığacak şekilde boyutları vardır ve yapay yükseklik veya genişlik kısıtlamalarına göre kısıtlanmaz.  
  
 <xref:System.Windows.Controls.DockPanel>, <xref:System.Windows.Controls.Grid> ve <xref:System.Windows.Controls.StackPanel>, yerelleştirilebilir [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] için iyi seçeneklerdir. <xref:System.Windows.Controls.Canvas> iyi bir seçenek değildir, çünkü içeriği kesinlikle konumlandırır, yerelleştirilmesi zor hale getirir.  
  
 Yerelleştirilebilir kullanıcı arabirimleri (UG 'ler) ile [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulamaları oluşturma hakkında daha fazla bilgi için, [Otomatik düzeni kullanma genel bakış ' a](../advanced/use-automatic-layout-overview.md)bakın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [İzlenecek yol: ilk WPF Masaüstü Uygulamam](../getting-started/walkthrough-my-first-wpf-desktop-application.md)
- [WPF düzen Galerisi örneği](https://go.microsoft.com/fwlink/?LinkID=160054)
- [Düzenle](../advanced/layout.md)
- [WPF denetimleri Galeri örneği](https://go.microsoft.com/fwlink/?LinkID=160053)
- [Hizalama, kenar boşlukları ve doldurmaya genel bakış](../advanced/alignment-margins-and-padding-overview.md)
- [Özel Içerik sarmalama paneli örneği oluşturma](https://go.microsoft.com/fwlink/?LinkID=159979)
- [Ekli özelliklere genel bakış](../advanced/attached-properties-overview.md)
- [Otomatik düzeni Kullan genel bakış](../advanced/use-automatic-layout-overview.md)
- [Düzen ve tasarım](../advanced/optimizing-performance-layout-and-design.md)
