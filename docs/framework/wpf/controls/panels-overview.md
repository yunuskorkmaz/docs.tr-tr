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
ms.openlocfilehash: 77f8fc5057b8f31e684941b742f2cf696afd6b07
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54525215"
---
# <a name="panels-overview"></a>Panellere Genel Bakış
<xref:System.Windows.Controls.Panel> öğeler öğelerin işlenmesi denetleyen bileşenleri — boyutlarına ve boyutlar, konumlarına ve alt içeriklerinin düzenini. [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] Sağlayan bir dizi önceden tanımlanmış <xref:System.Windows.Controls.Panel> öğeleri ve bunun yanı sıra özel oluşturabilme olanağı <xref:System.Windows.Controls.Panel> öğeleri.  
  
 Bu konuda aşağıdaki bölümleri içerir.  
  
-   [Paneli sınıfı](#Panels_view_from_10000_feet)  
  
-   [Panel öğesi ortak üyeler](#Panels_declared_members)  
  
-   [Türetilen bir Panel öğeleri](#Panels_derived_elements)  
  
-   [Kullanıcı arabirimi bölmeleri](#Panels_main_UI_elements)  
  
-   [İç içe geçmiş Panel öğeleri](#Panels_nested_panel_elements)  
  
-   [Özel Panel öğeleri](#Panels_custom_panel_elements)  
  
-   [Yerelleştirme/Genelleştirme desteği](#Panels_global_localization)  
  
<a name="Panels_view_from_10000_feet"></a>   
## <a name="the-panel-class"></a>Paneli sınıfı  
 <xref:System.Windows.Controls.Panel> Düzen sağlayan tüm öğeler desteklemek için temel sınıftır [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]. Türetilmiş <xref:System.Windows.Controls.Panel> öğeleri konumlandırma ve öğeleri düzenlemek için kullanılan [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] ve kod.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Birçok karmaşık düzenler etkinleştirme türetilmiş paneli uygulamaları içeren kapsamlı bir paketi içerir. Bu türetilmiş sınıfların özelliklerini ve çoğu standart olanak tanıyan yöntemler kullanıma [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] senaryoları. Geliştiriciler, ihtiyaçlarını karşılayan bir alt düzenleme davranışını geçersiz kılarak yeni düzenleri oluşturabilirsiniz bulamıyorsunuz <xref:System.Windows.FrameworkElement.ArrangeOverride%2A> ve <xref:System.Windows.FrameworkElement.MeasureOverride%2A> yöntemleri. Özel düzen davranışları hakkında daha fazla bilgi için bkz. [özel Panel öğeleri](#Panels_custom_panel_elements).  
  
<a name="Panels_declared_members"></a>   
## <a name="panel-common-members"></a>Ortak üyeleri paneli  
 Tüm <xref:System.Windows.Controls.Panel> öğeleri boyutlandırma ve konumlandırma tarafından tanımlanan özelliklerini temel destek <xref:System.Windows.FrameworkElement>de dahil olmak üzere <xref:System.Windows.FrameworkElement.Height%2A>, <xref:System.Windows.FrameworkElement.Width%2A>, <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>, <xref:System.Windows.FrameworkElement.VerticalAlignment%2A>, <xref:System.Windows.FrameworkElement.Margin%2A>, ve <xref:System.Windows.FrameworkElement.LayoutTransform%2A>. Konumlandırma özelliklerini tarafından tanımlanan hakkında ek bilgi <xref:System.Windows.FrameworkElement>, bkz: [hizalama, kenar boşlukları ve dolguya genel bakış](../../../../docs/framework/wpf/advanced/alignment-margins-and-padding-overview.md).  
  
 <xref:System.Windows.Controls.Panel> anlama ve düzeni kullanarak kritik öneme sahip ek özellikleri sunar. <xref:System.Windows.Controls.Panel.Background%2A> Özelliği ile bir türetilmiş panel öğesi sınırları arasında alanı dolduracak şekilde kullanılan bir <xref:System.Windows.Media.Brush>. <xref:System.Windows.Controls.Panel.Children%2A> alt öğelerinin koleksiyonunu temsil eder, <xref:System.Windows.Controls.Panel> oluşur. <xref:System.Windows.Controls.Panel.InternalChildren%2A> içeriğini temsil eden <xref:System.Windows.Controls.Panel.Children%2A> yanı sıra veri bağlama tarafından oluşturulan bu üyeler koleksiyonu. Hem de oluşan bir <xref:System.Windows.Controls.UIElementCollection> üst öğe içinde bulunan alt öğelerin <xref:System.Windows.Controls.Panel>.  
  
 Paneli ayrıca kullanıma sunan bir <xref:System.Windows.Controls.Panel.ZIndex%2A?displayProperty=nameWithType> ekli türetilmiş katmanlı sırayla elde etmek için kullanılan özellik <xref:System.Windows.Controls.Panel>. Bir panonun üyelerini <xref:System.Windows.Controls.Panel.Children%2A> daha yüksek bir koleksiyonla <xref:System.Windows.Controls.Panel.ZIndex%2A?displayProperty=nameWithType> değer görünür önünde bir alt olanlar <xref:System.Windows.Controls.Panel.ZIndex%2A?displayProperty=nameWithType> değeri. Bu gibi bölmeleri için özellikle yararlıdır <xref:System.Windows.Controls.Canvas> ve <xref:System.Windows.Controls.Grid> aynı koordinat paylaşmak alt izin verin.  
  
 <xref:System.Windows.Controls.Panel> Ayrıca tanımlar <xref:System.Windows.Controls.Panel.OnRender%2A> sunu varsayılan davranışı geçersiz kılmak için kullanılan yöntemi bir <xref:System.Windows.Controls.Panel>.  
  
#### <a name="attached-properties"></a>Ekli Özellikler  
 Türetilen bir panel öğeleri iliştirilmiş özellikler kapsamlı kullanımını olun. Ekli özelliği geleneksel yok bağımlılık özelliğinin özelleştirilmiş bir biçimidir [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] özelliği "sarmalayıcı". Ekli özelliklere sahip özel bir söz dizimi [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], hangi görülebilir birkaç aşağıdaki örneklerde.  
  
 Ekli özelliği tek amacı, alt öğelerin aslında bir üst öğesi tarafından tanımlanan bir özelliğin benzersiz değerleri depolamak izin vermektir. Bu işlev bir uygulamayı nasıl içinde istedikleri üst bildirmek alt öğeleri yaşıyor [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)], uygulama düzeni için son derece kullanışlı olduğu. Daha fazla bilgi için [ekli özelliklere genel bakış](../../../../docs/framework/wpf/advanced/attached-properties-overview.md).  
  
<a name="Panels_derived_elements"></a>   
## <a name="derived-panel-elements"></a>Türetilen bir Panel öğeleri  
 Çok sayıda nesne öğesinden türetilen <xref:System.Windows.Controls.Panel>, ancak bunların hepsi kök Düzen sağlayıcıları olarak kullanılmak üzere tasarlanmıştır. Altı tanımlanmış paneli sınıfı vardır (<xref:System.Windows.Controls.Canvas>, <xref:System.Windows.Controls.DockPanel>, <xref:System.Windows.Controls.Grid>, <xref:System.Windows.Controls.StackPanel>, <xref:System.Windows.Controls.VirtualizingStackPanel>, ve <xref:System.Windows.Controls.WrapPanel>) uygulama oluşturmak için özel olarak tasarlanan [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)].  
  
 Aşağıdaki tabloda görüldüğü gibi her bir panel öğesi kendi özel işlevler kapsüller.  
  
|Öğe adı|UI paneli?|Açıklama|  
|------------------|---------------|-----------------|  
|<xref:System.Windows.Controls.Canvas>|Evet|İçinde açıkça konumlandırma alt öğeler tarafından göreli koordinatları bir alan tanımlar <xref:System.Windows.Controls.Canvas> alan.|  
|<xref:System.Windows.Controls.DockPanel>|Evet|İçinde alt öğeleri yatay veya dikey olarak birbirlerine göreli dizebileceğiniz bir alan tanımlar.|  
|<xref:System.Windows.Controls.Grid>|Evet|Sütun ve satırlardan oluşan esnek bir kılavuz alanı tanımlar. Alt öğeleri bir <xref:System.Windows.Controls.Grid> kullanarak tam olarak konumlandırılmış <xref:System.Windows.FrameworkElement.Margin%2A> özelliği.|  
|<xref:System.Windows.Controls.StackPanel>|Evet|Alt öğeleri yatay veya dikey olarak yönlendirilebilir tek bir çizgi yerleştirir.|  
|<xref:System.Windows.Controls.Primitives.TabPanel>|Hayır|İçinde sekme düğmelerinin düzenini işler bir <xref:System.Windows.Controls.TabControl>.|  
|<xref:System.Windows.Controls.Primitives.ToolBarOverflowPanel>|Hayır|İçindeki içeriği düzenler bir <xref:System.Windows.Controls.ToolBar> denetimi.|  
|<xref:System.Windows.Controls.Primitives.UniformGrid>|Hayır|<xref:System.Windows.Controls.Primitives.UniformGrid> bir grid'in içindeki alt öğeleri ile tüm eşit hücre boyutlarını düzenlemek için kullanılır.|  
|<xref:System.Windows.Controls.VirtualizingPanel>|Hayır|"Alt koleksiyonu sanallaştırabilirsiniz" panolar için bir temel sınıf sağlar.|  
|<xref:System.Windows.Controls.VirtualizingStackPanel>|Evet|Düzenler ve içerik yatay veya dikey olarak yönelik tek bir satırda sanallaştırır.|  
|<xref:System.Windows.Controls.WrapPanel>|Evet|<xref:System.Windows.Controls.WrapPanel> Sonraki satır kutusunun kenarında içerik bozucu sağa doğru ardışık konumları alt öğeleri kalmadı. Sonraki sıralama olur sırayla üstten alta veya değerine bağlı olarak bir soldan sağa <xref:System.Windows.Controls.WrapPanel.Orientation%2A> özelliği.|  
  
<a name="Panels_main_UI_elements"></a>   
## <a name="user-interface-panels"></a>Kullanıcı arabirimi bölmeleri  
 Altı paneli sınıfları bulunan [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] desteklemek için iyileştirilmiş [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] senaryoları: <xref:System.Windows.Controls.Canvas>, <xref:System.Windows.Controls.DockPanel>, <xref:System.Windows.Controls.Grid>, <xref:System.Windows.Controls.StackPanel>, <xref:System.Windows.Controls.VirtualizingStackPanel>, ve <xref:System.Windows.Controls.WrapPanel>. Bu panel öğeleri, kullanımı kolay, çok yönlü ve uygulamalarının çoğu için yeterince genişletilebilir.  
  
 Her türetilmiş <xref:System.Windows.Controls.Panel> öğesi boyutlandırma kısıtlamaları farklı davranır. Anlama nasıl bir <xref:System.Windows.Controls.Panel> tanıtıcıları kısıtlamaları yatay veya dikey yönde yapabilir düzeni daha tahmin edilebilir.  
  
|**Panel adı**|**x-boyutu**|**y-boyut**|  
|--------------------|----------------------|----------------------|  
|<xref:System.Windows.Controls.Canvas>|İçerik kısıtlanmış|İçerik kısıtlanmış|  
|<xref:System.Windows.Controls.DockPanel>|Kısıtlanmış|Kısıtlanmış|  
|<xref:System.Windows.Controls.StackPanel> (Dikey hizalama)|Kısıtlanmış|İçerik kısıtlanmış|  
|<xref:System.Windows.Controls.StackPanel> (Yatay yönlendirme)|İçerik kısıtlanmış|Kısıtlanmış|  
|<xref:System.Windows.Controls.Grid>|Kısıtlanmış|Kısıtlanmış, dışındaki durumlarda burada <xref:System.Windows.GridUnitType.Auto> satırlar ve sütunlar için geçerlidir|  
|<xref:System.Windows.Controls.WrapPanel>|İçerik kısıtlanmış|İçerik kısıtlanmış|  
  
 Aşağıda daha ayrıntılı açıklamaları ve bu öğelerin her biri kullanım örneklerini bulunabilir.  
  
<a name="Panels_overview_Canvas_subsection"></a>   
### <a name="canvas"></a>Tuval  
 <xref:System.Windows.Controls.Canvas> Öğesi sağlayan mutlak göre içerik konumlandırma *x -* ve *y -* koordinatları. Öğeleri benzersiz bir konumda çizilir; Alternatif olarak, öğeleri aynı koordinatlara kaplayabilir, işaretlemede görünme sırasını öğeleri çizilen sırasını belirler.  
  
 <xref:System.Windows.Controls.Canvas> içlerinden en esnek düzen desteği sağlar <xref:System.Windows.Controls.Panel>. Yükseklik ve genişlik özellikleri tuval alanını tanımlamak için kullanılır ve içinde öğeleri üst alanına göre mutlak koordinat atanan <xref:System.Windows.Controls.Canvas>. Dört iliştirilmiş özellikler <xref:System.Windows.Controls.Canvas.Left%2A?displayProperty=nameWithType>, <xref:System.Windows.Controls.Canvas.Top%2A?displayProperty=nameWithType>, <xref:System.Windows.Controls.Canvas.Right%2A?displayProperty=nameWithType> ve <xref:System.Windows.Controls.Canvas.Bottom%2A?displayProperty=nameWithType>, içinde nesne yerleştirme ince denetim bir <xref:System.Windows.Controls.Canvas>, konumlandırabilir ve tam ekranda öğeleri düzenleyin geliştiricisi izin verme.  
  
#### <a name="cliptobounds-within-a-canvas"></a>Bir tuval içinde ClipToBounds  
 <xref:System.Windows.Controls.Canvas> alt öğeleri ekranında, hatta kendi dışında tanımlanmıştır koordinatlarda herhangi bir konuma yerleştirebilirsiniz <xref:System.Windows.FrameworkElement.Height%2A> ve <xref:System.Windows.FrameworkElement.Width%2A>. Ayrıca, <xref:System.Windows.Controls.Canvas> alt boyutu tarafından etkilenmez. Sonuç olarak, olası bir alt öğenin üst sınırlayıcı dikdörtgenini dışında diğer öğeleri overdraw <xref:System.Windows.Controls.Canvas>. Varsayılan davranışını bir <xref:System.Windows.Controls.Canvas> alt ve üst sınırları dışında çizilecek izin vermesidir <xref:System.Windows.Controls.Canvas>. Bu davranış istenmeyen, ise <xref:System.Windows.UIElement.ClipToBounds%2A> özelliği ayarlanabilir `true`. Bu neden <xref:System.Windows.Controls.Canvas> küçük kendi boyutu için. <xref:System.Windows.Controls.Canvas> sınırlarının dışında çizilecek alt veren tek düzen öğesi var.  
  
 Bu davranış grafik gösterilmiştir [genişlik özelliklerini karşılaştırma örneği](https://go.microsoft.com/fwlink/?LinkID=160050).  
  
#### <a name="defining-and-using-a-canvas"></a>Tanımlama ve tuval kullanma  
 A <xref:System.Windows.Controls.Canvas> yalnızca kullanarak oluşturulabilir [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] veya kod. Aşağıdaki örnek nasıl kullanılacağını gösterir <xref:System.Windows.Controls.Canvas> kesinlikle yeniden konumlandırmak için. Bu kod, üç 100 piksel kare üretir. Kırmızı ve kendi üst sol ilk kare olacağı (*x, y*) olarak belirtilen konum (0, 0). İkinci kare yeşil ve sol üst konumu (100, 100) yalnızca aşağı ve sağa ilk kare. Üçüncü kare mavi ve sol üst konumu (50, 50), bu nedenle ilk kare sağ quadrant ve ikinci sol quadrant kapsayan. Üçüncü kare, en son düzenlenir olduğundan, diğer iki karenin üzerinde görünen — diğer bir deyişle, çakışan bölümlerini üçüncü kutusunun rengindedir.  
  
 [!code-csharp[CanvasOvwSample#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CanvasOvwSample/CSharp/Canvas_Ovw_Sample.cs#1)]
 [!code-vb[CanvasOvwSample#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CanvasOvwSample/VisualBasic/canvas_vb.vb#1)]
 [!code-xaml[CanvasOvwSample#1](../../../../samples/snippets/xaml/VS_Snippets_Wpf/CanvasOvwSample/XAML/default.xaml#1)]  
  
 Derlenmiş uygulama yeni bir verir [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] aşağıdakine benzer.  
  
 ![Tipik bir tuvale öğe. ](../../../../docs/framework/wpf/controls/media/panel-intro-canvas.PNG "panel_intro_canvas")  
  
<a name="Panels_overview_DockPanel_subsection"></a>   
### <a name="dockpanel"></a>DockPanel  
 <xref:System.Windows.Controls.DockPanel> Öğesini kullanan <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType> kapsayıcı kenarlarında konumlandırmak için içerik öğeleri alt kümesi olarak ekli özellik. Zaman <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType> ayarlanır <xref:System.Windows.Controls.Dock.Top> veya <xref:System.Windows.Controls.Dock.Bottom>, alt öğelerini birbiriyle altına veya üstüne yerleştirir. Zaman <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType> ayarlanır <xref:System.Windows.Controls.Dock.Left> veya <xref:System.Windows.Controls.Dock.Right>, alt öğelerini birbiriyle sağa veya sola yerleştirir. <xref:System.Windows.Controls.DockPanel.LastChildFill%2A> Özelliği bir alt öğesi olarak eklenen son öğenin konumunu belirleyen bir <xref:System.Windows.Controls.DockPanel>.  
  
 Kullanabileceğiniz <xref:System.Windows.Controls.DockPanel> düğme kümesi gibi ilgili denetimleri bir grup yerleştirmek için. Oluşturmak için kullanın alternatif olarak, bir "paned" [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]bulunan benzer [!INCLUDE[TLA#tla_outlook](../../../../includes/tlasharptla-outlook-md.md)].  
  
#### <a name="sizing-to-content"></a>İçerik boyutu  
 Varsa, <xref:System.Windows.FrameworkElement.Height%2A> ve <xref:System.Windows.FrameworkElement.Width%2A> özellikleri belirtilmemişse, <xref:System.Windows.Controls.DockPanel> içeriğine boyutları. Boyutu artırabilir veya onun alt öğeleri boyutunu uyum sağlayacak şekilde azaltabilirsiniz. Ancak, bu özellikleri belirtilir ve yer artık sonraki belirtilen alt öğe için <xref:System.Windows.Controls.DockPanel> o alt öğesi ya da sonraki alt öğeleri görüntülemez ve sonraki alt öğeleri ölçü yok.  
  
#### <a name="lastchildfill"></a>LastChildFill  
 Varsayılan olarak, son alt bir <xref:System.Windows.Controls.DockPanel> öğesi "doldurur" kalan ayrılmamış. Bu davranışı istemiyorsanız ayarlamak <xref:System.Windows.Controls.DockPanel.LastChildFill%2A> özelliğini `false`.  
  
#### <a name="defining-and-using-a-dockpanel"></a>Tanımlama ve DockPanel kullanma  
 Aşağıdaki örnek alanı kullanarak bölüm yapmayı gösteren bir <xref:System.Windows.Controls.DockPanel>. Beş <xref:System.Windows.Controls.Border> öğeleri, bir üst öğesinin alt öğeleri olarak eklenir <xref:System.Windows.Controls.DockPanel>. Her farklı bir konum özelliği kullanan bir <xref:System.Windows.Controls.DockPanel> boşluğu bölümleme için. Son öğesi "kalan ayrılmamış alan doldurur".  
  
 [!code-cpp[DockPanelOvwSample#1](../../../../samples/snippets/cpp/VS_Snippets_Wpf/DockPanelOvwSample/CPP/DockPanel_Ovw_Sample.cpp#1)]
 [!code-csharp[DockPanelOvwSample#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DockPanelOvwSample/CSharp/DockPanel_Ovw_Sample.cs#1)]
 [!code-vb[DockPanelOvwSample#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DockPanelOvwSample/VisualBasic/dockpanel_vb.vb#1)]
 [!code-xaml[DockPanelOvwSample#1](../../../../samples/snippets/xaml/VS_Snippets_Wpf/DockPanelOvwSample/XAML/default.xaml#1)]  
  
 Derlenmiş uygulama yeni bir verir [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] aşağıdakine benzer.  
  
 ![Tipik bir DockPanel senaryo. ](../../../../docs/framework/wpf/controls/media/panel-intro-dockpanel.PNG "panel_intro_dockpanel")  
  
<a name="Panels_overview_Grid_subsection"></a>   
### <a name="grid"></a>Kılavuz  
 <xref:System.Windows.Controls.Grid> Öğesi mutlak konumlandırma ve sekmeli veri denetimi işlevlerini birleştirir. A <xref:System.Windows.Controls.Grid> kolayca konumu ve stil öğeleri sağlar. <xref:System.Windows.Controls.Grid> Esnek satır ve sütun gruplandırmaları tanımlamanıza olanak sağlar ve hatta birden fazla arasında boyutlandırma bilgi paylaşmak için bir mekanizma sağlar <xref:System.Windows.Controls.Grid> öğeleri.  
  
#### <a name="how-is-grid-different-from-table"></a>Nasıl kılavuz tablo farklıdır?  
 <xref:System.Windows.Documents.Table> ve <xref:System.Windows.Controls.Grid> bazı ortak işlevselliği paylaşır, ancak her farklı senaryolar için idealdir. A <xref:System.Windows.Documents.Table> akış içeriği içinde kullanmak için tasarlanmıştır (bkz [akış belgesine genel bakış](../../../../docs/framework/wpf/advanced/flow-document-overview.md) akış içeriği hakkında daha fazla bilgi için). Kılavuzlar formları içinde kullanılan en iyi (temel olarak her yerde dışında içerik akışı). İçinde bir <xref:System.Windows.Documents.FlowDocument>, <xref:System.Windows.Documents.Table> destekleyen akış içerik davranışları sayfalandırma ve sütun yeniden akış içerik seçimi gibi bir <xref:System.Windows.Controls.Grid> desteklemez. A <xref:System.Windows.Controls.Grid> diğer yandan en iyi dışında kullanılan bir <xref:System.Windows.Documents.FlowDocument> dahil olmak üzere birçok nedenden dolayı <xref:System.Windows.Controls.Grid> öğeleri satır ve sütun dizinini temel alarak ekler <xref:System.Windows.Documents.Table> desteklemez. <xref:System.Windows.Controls.Grid> Öğesi alt içeriğin tek bir "hücre." mevcut birden fazla öğe izin vererek, katman sağlar. <xref:System.Windows.Documents.Table> katmanlama desteklemez. Alt öğeleri bir <xref:System.Windows.Controls.Grid> "hücre" sınırlarının alanını göre mutlak konumlandırılmalıdır. <xref:System.Windows.Documents.Table> Bu özelliği desteklemez. Son olarak, bir <xref:System.Windows.Controls.Grid> daha açık ağırlığı bir <xref:System.Windows.Documents.Table>.  
  
#### <a name="sizing-behavior-of-columns-and-rows"></a>Satırları ve sütunları boyutlandırma davranışını  
 Sütun ve satır içinde tanımlanan bir <xref:System.Windows.Controls.Grid> yararlanabilirsiniz <xref:System.Windows.GridUnitType.Star> kalan alanı orantılı olarak dağıtılabilmesi için boyutlandırma. Zaman <xref:System.Windows.GridUnitType.Star> bir satır veya sütun veya satır ağırlıklı bütünün kalan kullanılabilir alanı alır, sütun genişliği veya yüksekliği seçilir. Tersine budur <xref:System.Windows.GridUnitType.Auto>, hangi eşit olarak bir sütun veya satır içinde içerik boyutunu temel alan dağıtmak. Bu değer olarak ifade edilen `*` veya `2*` kullanırken [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]. Bu durumda, satır veya sütun bir kez kullanılabilir alanı, İkinci durumda, iki kez alma vb. Boşluk ile orantılı olarak dağıtmak için bu teknikten birleştirerek bir <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> ve <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> değerini `Stretch` bölüm düzeni alanı ekran alanı yüzdesine göre filtrelenebilir. <xref:System.Windows.Controls.Grid> Bu şekilde alanı dağıtabilirsiniz tek düzen panosudur.  
  
#### <a name="defining-and-using-a-grid"></a>Tanımlama ve kılavuz kullanma  
 Aşağıdaki örnek nasıl oluşturulacağını gösterir. bir [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] benzer şekilde, kullanılabilir Çalıştır iletişim kutusunda bulunan [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] Başlat menüsü.  
  
 [!code-csharp[GridRunDialog#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GridRunDialog/CSharp/window1.xaml.cs#1)]
 [!code-vb[GridRunDialog#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/GridRunDialog/VisualBasic/grid_vb.vb#1)]  
  
 Derlenmiş uygulama yeni bir verir [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] aşağıdakine benzer.  
  
 ![Tipik bir kılavuz öğesi. ](../../../../docs/framework/wpf/controls/media/avalon-run-dialog.PNG "avalon_run_dialog")  
  
<a name="Panels_overview_StackPanel_subsection"></a>   
### <a name="stackpanel"></a>StackPanel  
 A <xref:System.Windows.Controls.StackPanel> "yığın atanan bir yönde öğeleri" sağlar. Varsayılan yığın yönü dikey olur. <xref:System.Windows.Controls.StackPanel.Orientation%2A> Özelliği, içerik akışını denetlemek için kullanılabilir.  
  
#### <a name="stackpanel-vs-dockpanel"></a>StackPanel vs. DockPanel  
 Ancak <xref:System.Windows.Controls.DockPanel> ayrıca "alt öğeleri yığınlayabilir" <xref:System.Windows.Controls.DockPanel> ve <xref:System.Windows.Controls.StackPanel> bazı kullanım senaryoları benzer sonuçlar üretmez. Örneğin, alt öğelerin sırasını kendi boyutunu etkileyebilir bir <xref:System.Windows.Controls.DockPanel> fakat bir <xref:System.Windows.Controls.StackPanel>. Bunun nedeni, <xref:System.Windows.Controls.StackPanel> yığının yönde ölçüler <xref:System.Double.PositiveInfinity>bilgileriyse <xref:System.Windows.Controls.DockPanel> yalnızca kullanılabilir boyutunu ölçer.  
  
 Aşağıdaki örnek, bu önemli bir fark gösterir.  
  
 [!code-cpp[StackPanelOvw4#1](../../../../samples/snippets/cpp/VS_Snippets_Wpf/StackPanelOvw4/CPP/StackPanel_Ovw_Sample4.cpp#1)]
 [!code-csharp[StackPanelOvw4#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StackPanelOvw4/CSharp/StackPanel_Ovw_Sample4.cs#1)]
 [!code-vb[StackPanelOvw4#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/StackPanelOvw4/VisualBasic/StackPanelSamp.vb#1)]
 [!code-xaml[StackPanelOvw4#1](../../../../samples/snippets/xaml/VS_Snippets_Wpf/StackPanelOvw4/XAML/default.xaml#1)]  
  
 Bu görüntüde işleme davranıştaki farkı görülebilir.  
  
 ![Ekran: StackPanel vs. DockPanel ekran](../../../../docs/framework/wpf/controls/media/layout-smiley-stackpanel.PNG "layout_smiley_stackpanel")  
  
#### <a name="defining-and-using-a-stackpanel"></a>Tanımlama ve StackPanel kullanma  
 Aşağıdaki örnek nasıl kullanılacağını gösterir. bir <xref:System.Windows.Controls.StackPanel> düğmelerini dikey olarak konumlandırılmış bir dizi oluşturmak için. Yatay konumlandırma için ayarlanmış <xref:System.Windows.Controls.StackPanel.Orientation%2A> özelliğini <xref:System.Windows.Controls.Orientation.Horizontal>.  
  
 [!code-csharp[StackPanel_ovw2#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StackPanel_ovw2/CSharp/StackPanel_Ovw_Sample2.cs#1)]
 [!code-vb[StackPanel_ovw2#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/StackPanel_ovw2/VisualBasic/StackPanelOvw.vb#1)]  
  
 Derlenmiş uygulama yeni bir verir [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] aşağıdakine benzer.  
  
 ![Tipik bir StackPanel öğesi. ](../../../../docs/framework/wpf/controls/media/panel-intro-stackpanel.PNG "panel_intro_stackpanel")  
  
<a name="Panels_overview_VirtualizingStackPanel_subsection"></a>   
#### <a name="virtualizingstackpanel"></a>VirtualizingStackPanel  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Ayrıca bir çeşitlemesi sağlar <xref:System.Windows.Controls.StackPanel> otomatik olarak "sanallaştırır verilere bağlı alt içeriğin" öğesi. Sözcüğü bu bağlamda sanallaştırmak tarafından bir alt öğelerinin oluşturulduğu çok sayıda veri öğelerinin hangi öğelerin ekranda görülebilir olduğuna göre bir teknik ifade eder. Bu, hem bellek ve yalnızca birkaç belirli bir zamanda ekranda olabilir, çok sayıda UI öğesi oluşturmak için işlemci açısından yoğun bir işlemdir. <xref:System.Windows.Controls.VirtualizingStackPanel> (tarafından sağlanan işlevsellik aracılığıyla <xref:System.Windows.Controls.VirtualizingPanel>) görünen öğeler hesaplar ve çalışır <xref:System.Windows.Controls.ItemContainerGenerator> gelen bir <xref:System.Windows.Controls.ItemsControl> (gibi <xref:System.Windows.Controls.ListBox> veya <xref:System.Windows.Controls.ListView>) yalnızca görünür öğeler için oluşturulacak.  
  
 <xref:System.Windows.Controls.VirtualizingStackPanel> Öğe öğeleri gibi denetimler için konak olarak otomatik olarak ayarladığınız <xref:System.Windows.Controls.ListBox>. Koleksiyon veri barındırma bağlı içeriği sınırları içinde olduğu sürece içeriği otomatik olarak, sanallaştırılmış bir <xref:System.Windows.Controls.ScrollViewer>. Bu önemli ölçüde performans barındırma alt öğe sayısını artırır.  
  
 Aşağıdaki biçimlendirmede nasıl kullanılacağını gösteren bir <xref:System.Windows.Controls.VirtualizingStackPanel> bir öğenin konağı olarak. <xref:System.Windows.Controls.VirtualizingStackPanel.IsVirtualizingProperty?displayProperty=nameWithType> Ekli özellik ayarlanmalıdır `true` (varsayılan) gerçekleşmesi, sanallaştırma için.  
  
 [!code-xaml[VirtualizingStackPanel_Intro#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/VirtualizingStackPanel_Intro/CS/default.xaml#1)]  
  
<a name="Panels_overview_WrapPanel"></a>   
### <a name="wrappanel"></a>WrapPanel  
 <xref:System.Windows.Controls.WrapPanel> soldan sağa doğru en son içeriği sonraki satıra üst kapsayıcısının kenarı ulaştığında, alt öğeleri konumlandırmak için kullanılır. Yatay veya dikey olarak içerik yönlendirilebilir. <xref:System.Windows.Controls.WrapPanel> Basit akan yararlıdır [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] senaryoları. Ayrıca, tüm alt öğeleri için Tekdüzen boyutlandırma uygulamak için de kullanılabilir.  
  
 Aşağıdaki örnek nasıl oluşturulacağını gösterir. bir <xref:System.Windows.Controls.WrapPanel> görüntülenecek <xref:System.Windows.Controls.Button> bunlar kendi kapsayıcı kenarı ulaştığında sarmalayan denetimleri.  
  
 [!code-cpp[WrapPanel_Intro#1](../../../../samples/snippets/cpp/VS_Snippets_Wpf/WrapPanel_Intro/CPP/WrapPanel_Code.cpp#1)]
 [!code-csharp[WrapPanel_Intro#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WrapPanel_Intro/CSharp/WrapPanel_Code.cs#1)]
 [!code-vb[WrapPanel_Intro#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WrapPanel_Intro/VisualBasic/WrapPanel_vb.vb#1)]
 [!code-xaml[WrapPanel_Intro#1](../../../../samples/snippets/xaml/VS_Snippets_Wpf/WrapPanel_Intro/XAML/default.xaml#1)]  
  
 Derlenmiş uygulama yeni bir verir [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] aşağıdakine benzer.  
  
 ![Tipik bir WrapPanel öğesi. ](../../../../docs/framework/wpf/controls/media/wrappanel-element.PNG "WrapPanel_Element")  
  
<a name="Panels_nested_panel_elements"></a>   
## <a name="nested-panel-elements"></a>İç içe geçmiş Panel öğeleri  
 <xref:System.Windows.Controls.Panel> öğeleri diğer içinde karmaşık düzenler oluşturmak için yuvalanabilir. Bu durumlarda çok kullanışlı bir yerde kanıtlayabilirsiniz <xref:System.Windows.Controls.Panel> değerinin bir bölümü için ideal bir [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], ancak farklı bir kısmını gereksinimlerini karşılamayabilir [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)].  
  
 Uygulamanızı destekleyen bir iç içe geçme miktarını için pratik bir sınır yoktur, ancak yalnızca istenen düzeninizi için gerçekten gerekli olup bu panelleri kullanmak için uygulamanızı sınırlamak genellikle en iyisidir. Çoğu durumda, bir <xref:System.Windows.Controls.Grid> öğesi, iç içe geçmiş panelleri esnek bir düzen kapsayıcısı olarak nedeniyle yerine kullanılabilir. Gereksiz öğeler ağaç dışında tutarak bu, uygulamanızın performansını artırabilir.  
  
 Aşağıdaki örnek nasıl oluşturulacağını gösterir. bir [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] yararlanır, iç içe geçmiş <xref:System.Windows.Controls.Panel> belirli bir düzeni elde etmek için öğeleri. Bu özel durumda bir <xref:System.Windows.Controls.DockPanel> öğesi sağlamak amacıyla kullanılır [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] yapısı ve iç içe geçmiş <xref:System.Windows.Controls.StackPanel> öğeleri bir <xref:System.Windows.Controls.Grid>ve <xref:System.Windows.Controls.Canvas> üst içindeki tam alt öğeleri konumlandırmak için kullanılan <xref:System.Windows.Controls.DockPanel>.  
  
 [!code-csharp[Nested_Panels#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Nested_Panels/CSharp/nestedpanels.cs#1)]
 [!code-vb[Nested_Panels#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Nested_Panels/VisualBasic/nestedpanels.vb#1)]  
  
 Derlenmiş uygulama yeni bir verir [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] aşağıdakine benzer.  
  
 ![İç içe geçmiş paneller yararlanır bir kullanıcı Arabirimi. ](../../../../docs/framework/wpf/controls/media/nested-panels.PNG "nested_panels")  
  
<a name="Panels_custom_panel_elements"></a>   
## <a name="custom-panel-elements"></a>Özel Panel öğeleri  
 Sırada [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] esnek düzen denetimleri, davranışları da elde edilebilir geçersiz kılarak özel düzen dizisi sağlar <xref:System.Windows.FrameworkElement.ArrangeOverride%2A> ve <xref:System.Windows.FrameworkElement.MeasureOverride%2A> yöntemleri. Boyutlandırma ve konumlama özel tarafından gerçekleştirilebilir yeni davranışlar bunlar içinde konumlandırma tanımlama yöntemleri geçersiz kılın.  
  
 Benzer şekilde, özel düzen davranışlarına göre türetilmiş sınıfları (gibi <xref:System.Windows.Controls.Canvas> veya <xref:System.Windows.Controls.Grid>) geçersiz kılma tarafından tanımlanan kendi <xref:System.Windows.FrameworkElement.ArrangeOverride%2A> ve <xref:System.Windows.FrameworkElement.MeasureOverride%2A> yöntemleri.  
  
 Aşağıdaki biçimlendirme, özel bir oluşturma işlemi gösterilmektedir <xref:System.Windows.Controls.Panel> öğesi. Bu yeni <xref:System.Windows.Controls.Panel>olarak tanımlanan `PlotPanel`, sabit kodlanmış kullanarak alt öğelerini konumlandırma destekler *x -* ve *y -* koordinatları. Bu örnekte, bir <xref:System.Windows.Shapes.Rectangle> (gösterilmemiştir) öğesi çizim noktada 50 konumlandırılmış (*x*) ve 50 (*y*).  
  
 [!code-cpp[PlotPanel#1](../../../../samples/snippets/cpp/VS_Snippets_Wpf/PlotPanel/CPP/PlotPanel.cpp#1)]
 [!code-csharp[PlotPanel#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PlotPanel/CSharp/PlotPanel.cs#1)]
 [!code-vb[PlotPanel#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PlotPanel/VisualBasic/PlotPanel.vb#1)]  
  
 Daha karmaşık bir özel panel uygulama görüntülemek için bkz: [sarmalama özel içerik Panel örneği oluşturma](https://go.microsoft.com/fwlink/?LinkID=159979).  
  
<a name="Panels_global_localization"></a>   
## <a name="localizationglobalization-support"></a>Yerelleştirme/Genelleştirme desteği  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Yerelleştirilebilir oluşturulmasında assist özellikleri destekler [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)].  
  
 Tüm panel öğeleri yerel olarak destekleyen <xref:System.Windows.FrameworkElement.FlowDirection%2A> dinamik olarak yeniden kullanıcının yerel ayarı veya dil ayarları temel alarak içerik akışı için kullanılan özellik. Daha fazla bilgi için bkz. <xref:System.Windows.FrameworkElement.FlowDirection%2A>.  
  
 <xref:System.Windows.Window.SizeToContent%2A> Özelliği, uygulama geliştiricilerin sağlayan bir mekanizma sağlar gereksinimlerini öngörmek yerelleştirilmiş [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]. Kullanarak <xref:System.Windows.SizeToContent.WidthAndHeight> bu özelliğin değeri, bir üst <xref:System.Windows.Window> her zaman içeriği sığdıracak şekilde dinamik olarak boyutlandırır ve yapay enlerini veya boylarını kısıtlamalar ile sınırlı değildir.  
  
 <xref:System.Windows.Controls.DockPanel>, <xref:System.Windows.Controls.Grid>, ve <xref:System.Windows.Controls.StackPanel> için tüm iyi seçimler yerelleştirilebilir [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]. <xref:System.Windows.Controls.Canvas> iyi bir seçim değildir, ancak bu içeriği kesinlikle yerelleştirmek zorlaştıran konumlandırır olmasıdır.  
  
 Oluşturma hakkında ek bilgi için [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] yerelleştirilebilir uygulamalarla [!INCLUDE[TLA#tla_ui#plural](../../../../includes/tlasharptla-uisharpplural-md.md)]s, bkz: [kullanım otomatik düzen genel bakış](../../../../docs/framework/wpf/advanced/use-automatic-layout-overview.md).  
  
## <a name="see-also"></a>Ayrıca bkz.
- [İzlenecek yol: İlk WPF Masaüstü Uygulamam](../../../../docs/framework/wpf/getting-started/walkthrough-my-first-wpf-desktop-application.md)
- [WPF Düzen Galerisi örneği](https://go.microsoft.com/fwlink/?LinkID=160054)
- [Düzen](../../../../docs/framework/wpf/advanced/layout.md)
- [WPF denetimleri Galerisi örneği](https://go.microsoft.com/fwlink/?LinkID=160053)
- [Hizalama, Kenar Boşlukları ve Doldurmaya Genel Bakış](../../../../docs/framework/wpf/advanced/alignment-margins-and-padding-overview.md)
- [Özel içerik kaydırma paneli örneği oluşturma](https://go.microsoft.com/fwlink/?LinkID=159979)
- [Ekli Özelliklere Genel Bakış](../../../../docs/framework/wpf/advanced/attached-properties-overview.md)
- [Otomatik Düzen Kullanımına Genel Bakış](../../../../docs/framework/wpf/advanced/use-automatic-layout-overview.md)
- [Düzen ve Tasarım](../../../../docs/framework/wpf/advanced/optimizing-performance-layout-and-design.md)
