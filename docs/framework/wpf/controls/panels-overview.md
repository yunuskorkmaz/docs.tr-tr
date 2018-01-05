---
title: "Panellere Genel Bakış"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Panel control [WPF], about Panel control
- controls [WPF], Panel
ms.assetid: f73644af-9941-4611-8754-6d4cef03fc44
caps.latest.revision: "48"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d25c6d9e4e6d067ad2107df2374329d84300c015
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="panels-overview"></a>Panellere Genel Bakış
<xref:System.Windows.Controls.Panel>öğeleridir öğelerin işlenmesi kontrol bileşenleri — boyutlarına ve boyutları, konumlarına ve alt içeriklerini düzenleme. [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] Sağlayan bir dizi önceden tanımlanmış <xref:System.Windows.Controls.Panel> özel oluşturabilme olanağı yanı sıra öğeleri <xref:System.Windows.Controls.Panel> öğeleri.  
  
 Bu konu aşağıdaki bölümleri içerir.  
  
-   [Panel sınıfı](#Panels_view_from_10000_feet)  
  
-   [Panel öğesi ortak üyeler](#Panels_declared_members)  
  
-   [Türetilen Panel öğeleri](#Panels_derived_elements)  
  
-   [Kullanıcı arabirimi bölmeleri](#Panels_main_UI_elements)  
  
-   [İç içe geçmiş Panel öğeleri](#Panels_nested_panel_elements)  
  
-   [Özel Panel öğeleri](#Panels_custom_panel_elements)  
  
-   [Yerelleştirme/Genelleştirme desteği](#Panels_global_localization)  
  
<a name="Panels_view_from_10000_feet"></a>   
## <a name="the-panel-class"></a>Panel sınıfı  
 <xref:System.Windows.Controls.Panel>Düzen sağlayan tüm öğeler desteklemek için temel sınıfı olan [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]. Türetilmiş <xref:System.Windows.Controls.Panel> öğeleri getirin ve öğelerini düzenlemek için kullanılan [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] ve kod.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Birçok karmaşık düzenleri etkinleştirmek türetilmiş paneli uygulamaları kapsamlı dizisi içerir. Bu türetilmiş sınıfları, özellikleri ve çoğu standart sağlayan yöntemler kullanıma [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] senaryoları. Geliştiriciler kendi gereksinimlerini karşılayan bir alt düzenleme davranışını geçersiz kılarak yeni düzenleri oluşturabilir bulamıyorsunuz <xref:System.Windows.FrameworkElement.ArrangeOverride%2A> ve <xref:System.Windows.FrameworkElement.MeasureOverride%2A> yöntemleri. Özel düzen davranışları hakkında daha fazla bilgi için bkz: [özel Panel öğeleri](#Panels_custom_panel_elements).  
  
<a name="Panels_declared_members"></a>   
## <a name="panel-common-members"></a>Panel ortak üyeler  
 Tüm <xref:System.Windows.Controls.Panel> öğeleri boyutlandırma ve tarafından tanımlanan konumlandırma özellikleri temel destek <xref:System.Windows.FrameworkElement>dahil <xref:System.Windows.FrameworkElement.Height%2A>, <xref:System.Windows.FrameworkElement.Width%2A>, <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>, <xref:System.Windows.FrameworkElement.VerticalAlignment%2A>, <xref:System.Windows.FrameworkElement.Margin%2A>, ve <xref:System.Windows.FrameworkElement.LayoutTransform%2A>. Tarafından tanımlanan konumlandırma özellikleri hakkında ek bilgi için <xref:System.Windows.FrameworkElement>, bkz: [hizalama, kenar boşlukları ve doldurma genel bakış](../../../../docs/framework/wpf/advanced/alignment-margins-and-padding-overview.md).  
  
 <xref:System.Windows.Controls.Panel>Düzen anlaşılması ve kritik öneme sahip ek özellikleri sunar. <xref:System.Windows.Controls.Panel.Background%2A> Özelliği olan bir türetilmiş panel öğesi sınırlarının arasında alanı dolduracak şekilde kullanılır bir <xref:System.Windows.Media.Brush>. <xref:System.Windows.Controls.Panel.Children%2A>alt öğe koleksiyonunu temsil eder, <xref:System.Windows.Controls.Panel> oluşur. <xref:System.Windows.Controls.Panel.InternalChildren%2A>içeriğini temsil eder <xref:System.Windows.Controls.Panel.Children%2A> koleksiyonu artı veri bağlama tarafından oluşturulan bu üyeler. Her ikisi de oluşur bir <xref:System.Windows.Controls.UIElementCollection> üst içinde barındırılan alt öğelerini <xref:System.Windows.Controls.Panel>.  
  
 Panel de ortaya çıkarır bir <xref:System.Windows.Controls.Panel.ZIndex%2A?displayProperty=nameWithType> türetilmiş bir katmanlı sırayla elde etmek için kullanılan özelliği eklenmiş <xref:System.Windows.Controls.Panel>. Bir bölmenin üyeleri <xref:System.Windows.Controls.Panel.Children%2A> daha yüksek koleksiyonuyla <xref:System.Windows.Controls.Panel.ZIndex%2A?displayProperty=nameWithType> değeri görünür bir alt olanlar önünde <xref:System.Windows.Controls.Panel.ZIndex%2A?displayProperty=nameWithType> değeri. Bu gibi paneller için özellikle yararlıdır <xref:System.Windows.Controls.Canvas> ve <xref:System.Windows.Controls.Grid> aynı koordinat paylaşmak alt izin verin.  
  
 <xref:System.Windows.Controls.Panel>Ayrıca tanımlar <xref:System.Windows.Controls.Panel.OnRender%2A> varsayılan sunu davranışını geçersiz kılmak için kullanılan yöntemi bir <xref:System.Windows.Controls.Panel>.  
  
#### <a name="attached-properties"></a>Ekli Özellikler  
 Türetilen panel öğeleri ekli özellikler kapsamlı kullanımını olun. Ekli özellik geleneksel yok bağımlılık özelliği özel biçimidir [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] özellik "sarmalayıcı". Ekli özellikler olmayan özel bir söz dizimi [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], hangi görülme birkaç izleyin örnekleri.  
  
 Ekli özellik tek amacı, alt öğeleri gerçekten üst öğesi tarafından tanımlanan bir özelliğin benzersiz değerler depolamak izin vermektir. Bir uygulama bu işlevlerin nasıl içinde sunulan istedikleri üst bildirmek alt öğelerini sahip [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)], uygulama düzeni için son derece yararlı olduğu. Daha fazla bilgi için bkz: [bağlı özelliklerine genel bakış](../../../../docs/framework/wpf/advanced/attached-properties-overview.md).  
  
<a name="Panels_derived_elements"></a>   
## <a name="derived-panel-elements"></a>Türetilen Panel öğeleri  
 Birçok nesne öğesinden türetilen <xref:System.Windows.Controls.Panel>, ancak bunları tüm kök yerleşim sağlayıcıları olarak kullanılmak üzere tasarlanmıştır. Altı tanımlı paneli sınıfları vardır (<xref:System.Windows.Controls.Canvas>, <xref:System.Windows.Controls.DockPanel>, <xref:System.Windows.Controls.Grid>, <xref:System.Windows.Controls.StackPanel>, <xref:System.Windows.Controls.VirtualizingStackPanel>, ve <xref:System.Windows.Controls.WrapPanel>) özellikle uygulama oluşturmak için tasarlanan [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)].  
  
 Her panel öğesi, aşağıdaki tabloda görüldüğü gibi kendi özel işlevselliği kapsar.  
  
|Öğe adı|UI paneli?|Açıklama|  
|------------------|---------------|-----------------|  
|<xref:System.Windows.Controls.Canvas>|Evet|İçinde açıkça getirin alt öğeleri göreli koordinatları tarafından bir alanı tanımlar <xref:System.Windows.Controls.Canvas> alanı.|  
|<xref:System.Windows.Controls.DockPanel>|Evet|İçinde alt öğelerini yatay veya dikey olarak, diğer göre düzenleyebilirsiniz alanı tanımlar.|  
|<xref:System.Windows.Controls.Grid>|Evet|Sütunları ve satırları oluşan bir esnek Kılavuz alanı tanımlar. Alt öğelerinin bir <xref:System.Windows.Controls.Grid> tam olarak kullanarak yerleştirilebilir <xref:System.Windows.FrameworkElement.Margin%2A> özelliği.|  
|<xref:System.Windows.Controls.StackPanel>|Evet|Alt öğelerini yatay veya dikey olarak yönlendirilebilir tek bir satıra düzenler.|  
|<xref:System.Windows.Controls.Primitives.TabPanel>|Hayır|Sekme düğmeleri yerleşimini işler bir <xref:System.Windows.Controls.TabControl>.|  
|<xref:System.Windows.Controls.Primitives.ToolBarOverflowPanel>|Hayır|İçerik içinde düzenler bir <xref:System.Windows.Controls.ToolBar> denetim.|  
|<xref:System.Windows.Controls.Primitives.UniformGrid>|Hayır|<xref:System.Windows.Controls.Primitives.UniformGrid>bir kılavuzdaki alt tüm eşit hücre boyutlarıyla düzenlemek için kullanılır.|  
|<xref:System.Windows.Controls.VirtualizingPanel>|Hayır|"Kendi alt öğelerini koleksiyon sanallaştırabilirsiniz" panolar için bir temel sınıf sağlar.|  
|<xref:System.Windows.Controls.VirtualizingStackPanel>|Evet|Düzenler ve içeriği yatay veya dikey yönelik tek bir satırda sanallaştırır.|  
|<xref:System.Windows.Controls.WrapPanel>|Evet|<xref:System.Windows.Controls.WrapPanel>alt öğelerini soldan sağa doğru içeriği kapsayan kutunun kenarında sonraki satıra bölerek sıralı konumda yerleştirir. Sonraki sıralama olur sıralı olarak üstten alta veya sağdan sola değerine bağlı olarak <xref:System.Windows.Controls.WrapPanel.Orientation%2A> özelliği.|  
  
<a name="Panels_main_UI_elements"></a>   
## <a name="user-interface-panels"></a>Kullanıcı arabirimi bölmeleri  
 Altı paneli sınıfları bulunan [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] desteklemek için iyileştirilmiş [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] senaryolar: <xref:System.Windows.Controls.Canvas>, <xref:System.Windows.Controls.DockPanel>, <xref:System.Windows.Controls.Grid>, <xref:System.Windows.Controls.StackPanel>, <xref:System.Windows.Controls.VirtualizingStackPanel>, ve <xref:System.Windows.Controls.WrapPanel>. Bu panel öğeleri, kullanımı kolay, çok yönlü ve çoğu uygulama için yeterince genişletilebilir.  
  
 Her türetilmiş <xref:System.Windows.Controls.Panel> öğesi boyutlandırma kısıtlamaları farklı şekilde ele alır. Anlama nasıl bir <xref:System.Windows.Controls.Panel> tanıtıcıları kısıtlamaları yatay veya dikey yönde yapabilir düzeni daha tahmin edilebilir.  
  
|**Panel adı**|**x boyutu**|**y-boyut**|  
|--------------------|----------------------|----------------------|  
|<xref:System.Windows.Controls.Canvas>|İçeriği kısıtlı|İçeriği kısıtlı|  
|<xref:System.Windows.Controls.DockPanel>|Kısıtlı|Kısıtlı|  
|<xref:System.Windows.Controls.StackPanel>(Dikey yönlendirme)|Kısıtlı|İçeriği kısıtlı|  
|<xref:System.Windows.Controls.StackPanel>(Yatay yönlendirme)|İçeriği kısıtlı|Kısıtlı|  
|<xref:System.Windows.Controls.Grid>|Kısıtlı|Kısıtlı, dışındaki durumlarda nerede <xref:System.Windows.GridUnitType.Auto> satırlara ve sütunlara Uygula|  
|<xref:System.Windows.Controls.WrapPanel>|İçeriği kısıtlı|İçeriği kısıtlı|  
  
 Daha ayrıntılı açıklamaları ve bu öğelerin her birini kullanım örnekleri aşağıda bulabilirsiniz.  
  
<a name="Panels_overview_Canvas_subsection"></a>   
### <a name="canvas"></a>Tuval  
 <xref:System.Windows.Controls.Canvas> Öğeleri sağlar mutlak göre içerik konumlandırma *x -* ve *y*koordinatları. Öğeler benzersiz bir konumda çizilebilir; veya öğeleri koordinatlarının kaplar, öğeleri çizilen sırası biçimlendirmede görünme sırasını belirler.  
  
 <xref:System.Windows.Controls.Canvas>herhangi birinin en esnek düzeni destek sağlayan <xref:System.Windows.Controls.Panel>. Tuvale alanını tanımlamak için kullanılan yükseklik ve genişlik özelliklerini ve içindeki öğeler, üst alanının göreli mutlak koordinatları atanır <xref:System.Windows.Controls.Canvas>. Dört bağlı özelliklerini <xref:System.Windows.Controls.Canvas.Left%2A?displayProperty=nameWithType>, <xref:System.Windows.Controls.Canvas.Top%2A?displayProperty=nameWithType>, <xref:System.Windows.Controls.Canvas.Right%2A?displayProperty=nameWithType> ve <xref:System.Windows.Controls.Canvas.Bottom%2A?displayProperty=nameWithType>, nesne yerleşiminin içinde ayrıntılı denetimini izin bir <xref:System.Windows.Controls.Canvas>, geliştiricinin getirin ve öğeleri tam ekranda Düzenle izin vererek.  
  
#### <a name="cliptobounds-within-a-canvas"></a>Bir tuval içinde ClipToBounds  
 <xref:System.Windows.Controls.Canvas>alt öğeler ekranında, hatta kendi dışında tanımlanmıştır koordinatları, herhangi bir konumda yerleştirebilirsiniz <xref:System.Windows.FrameworkElement.Height%2A> ve <xref:System.Windows.FrameworkElement.Width%2A>. Ayrıca, <xref:System.Windows.Controls.Canvas> alt boyutu tarafından etkilenmez. Sonuç olarak, bir alt öğesi üst sınırlayıcı dikdörtgenini dışındaki diğer öğeleri overdraw mümkündür <xref:System.Windows.Controls.Canvas>. Varsayılan davranışının bir <xref:System.Windows.Controls.Canvas> alt üst sınırları dışında çizilmesine izin <xref:System.Windows.Controls.Canvas>. Bu davranış istenmeyen, ise <xref:System.Windows.UIElement.ClipToBounds%2A> özelliği ayarlanabilir `true`. Bu neden <xref:System.Windows.Controls.Canvas> küçük kendi boyutuna için. <xref:System.Windows.Controls.Canvas>Çocuklar kendi sınırları dışında çizilmesine izin veren yalnızca Düzen öğesidir.  
  
 Bu davranış grafik gösterilmiştir [genişlik özelliklerini karşılaştırma örneği](http://go.microsoft.com/fwlink/?LinkID=160050).  
  
#### <a name="defining-and-using-a-canvas"></a>Tanımlama ve bir tuval kullanma  
 A <xref:System.Windows.Controls.Canvas> yalnızca kullanarak oluşturulabilir [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] veya kod. Aşağıdaki örnekte nasıl kullanılacağı ortaya <xref:System.Windows.Controls.Canvas> kesinlikle konumlandırmak için. Bu kod üç 100 piksel kare üretir. İlk kare kırmızı, kendi üst sol ise (*x, y*) konumu olarak belirtilir (0, 0). İkinci kare yeşil ve sol üst konumu (100, 100) hemen altındaki ve ilk kare sağındaki. Üçüncü kare mavi ve sol üst konumu (50, 50), bu nedenle ilk kare sağ alt çeyreğinde ve ikinci sol üst çeyreğinde kapsayan. Üçüncü kare en son düzenlenir olduğundan, diğer iki kare en üstünde olacak şekilde göründüğü — diğer bir deyişle, çakışan bölümler üçüncü kutusunun rengini varsayalım.  
  
 [!code-csharp[CanvasOvwSample#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CanvasOvwSample/CSharp/Canvas_Ovw_Sample.cs#1)]
 [!code-vb[CanvasOvwSample#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CanvasOvwSample/VisualBasic/canvas_vb.vb#1)]
 [!code-xaml[CanvasOvwSample#1](../../../../samples/snippets/xaml/VS_Snippets_Wpf/CanvasOvwSample/XAML/default.xaml#1)]  
  
 Derlenmiş uygulama yeni bir verir [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] aşağıdakine benzer.  
  
 ![Tipik bir Canvas öğesi. ] (../../../../docs/framework/wpf/controls/media/panel-intro-canvas.PNG "panel_intro_canvas")  
  
<a name="Panels_overview_DockPanel_subsection"></a>   
### <a name="dockpanel"></a>DockPanel  
 <xref:System.Windows.Controls.DockPanel> Öğesini kullanan <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType> bir kapsayıcı kenarlarında konumlandırmak için içerik öğeleri alt kümesi olarak özelliği eklenmiş. Zaman <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType> ayarlanır <xref:System.Windows.Controls.Dock.Top> veya <xref:System.Windows.Controls.Dock.Bottom>, alt öğelerini üstüne veya altına birbirleri konumlandırır. Zaman <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType> ayarlanır <xref:System.Windows.Controls.Dock.Left> veya <xref:System.Windows.Controls.Dock.Right>, alt öğelerini birbirine sağa veya sola yerleştirir. <xref:System.Windows.Controls.DockPanel.LastChildFill%2A> Özelliği, bir alt öğesi olarak eklenen son öğenin konumunu belirler bir <xref:System.Windows.Controls.DockPanel>.  
  
 Kullanabileceğiniz <xref:System.Windows.Controls.DockPanel> bir dizi düğmesi gibi ilgili denetimleri bir grup konumlandırmak için. Oluşturmak için kullanın alternatif olarak, "paned" a [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]bulunan benzer [!INCLUDE[TLA#tla_outlook](../../../../includes/tlasharptla-outlook-md.md)].  
  
#### <a name="sizing-to-content"></a>İçeriği boyutlandırma  
 Varsa, <xref:System.Windows.FrameworkElement.Height%2A> ve <xref:System.Windows.FrameworkElement.Width%2A> özellikleri belirtilmedi, <xref:System.Windows.Controls.DockPanel> içeriğine yönelik boyutları. Boyutunu artırın veya alt öğelerinden boyutuna uygun şekilde azaltın. Ancak, ne zaman bu özellikleri belirtilir ve artık yer sonraki belirtilen alt öğesinin <xref:System.Windows.Controls.DockPanel> o alt öğesi ya da sonraki alt öğeleri göstermez ve sonraki alt öğelerini ölçü değil.  
  
#### <a name="lastchildfill"></a>LastChildFill  
 Varsayılan olarak, son alt bir <xref:System.Windows.Controls.DockPanel> öğesi "doldurur" kalan ayrılmamış. Bu davranış değil istenirse, ayarlamak <xref:System.Windows.Controls.DockPanel.LastChildFill%2A> özelliğine `false`.  
  
#### <a name="defining-and-using-a-dockpanel"></a>Tanımlama ve DockPanel kullanma  
 Aşağıdaki örnek alanı kullanarak bölümlemek nasıl gösteren bir <xref:System.Windows.Controls.DockPanel>. Beş <xref:System.Windows.Controls.Border> öğeleri, bir üst öğenin alt öğesi olarak eklenir <xref:System.Windows.Controls.DockPanel>. Her farklı konumlandırma özelliğini kullanan bir <xref:System.Windows.Controls.DockPanel> bölüm alanına. Son öğe "kalan ayrılmamış alan doldurur".  
  
 [!code-cpp[DockPanelOvwSample#1](../../../../samples/snippets/cpp/VS_Snippets_Wpf/DockPanelOvwSample/CPP/DockPanel_Ovw_Sample.cpp#1)]
 [!code-csharp[DockPanelOvwSample#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DockPanelOvwSample/CSharp/DockPanel_Ovw_Sample.cs#1)]
 [!code-vb[DockPanelOvwSample#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DockPanelOvwSample/VisualBasic/dockpanel_vb.vb#1)]
 [!code-xaml[DockPanelOvwSample#1](../../../../samples/snippets/xaml/VS_Snippets_Wpf/DockPanelOvwSample/XAML/default.xaml#1)]  
  
 Derlenmiş uygulama yeni bir verir [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] aşağıdakine benzer.  
  
 ![Tipik bir DockPanel senaryosu. ] (../../../../docs/framework/wpf/controls/media/panel-intro-dockpanel.PNG "panel_intro_dockpanel")  
  
<a name="Panels_overview_Grid_subsection"></a>   
### <a name="grid"></a>Kılavuz  
 <xref:System.Windows.Controls.Grid> Öğesi bir mutlak konumlandırma ve tablo veri denetim işlevselliğini birleştirir. A <xref:System.Windows.Controls.Grid> kolayca konumunu ve stili öğelerine sağlar. <xref:System.Windows.Controls.Grid>Esnek satır ve sütun gruplandırmaları tanımlamanıza olanak sağlar ve hatta birden çok arasında boyutlandırma bilgi paylaşmak için bir mekanizma sağlar <xref:System.Windows.Controls.Grid> öğeleri.  
  
#### <a name="how-is-grid-different-from-table"></a>Nasıl kılavuz farklı tablosundan mı?  
 <xref:System.Windows.Documents.Table>ve <xref:System.Windows.Controls.Grid> ortak işlevselliğinin paylaşır, ancak her farklı senaryolar için uygundur. A <xref:System.Windows.Documents.Table> akış içeriği içinde kullanılmak üzere tasarlanmış (bkz [akış belge genel bakış](../../../../docs/framework/wpf/advanced/flow-document-overview.md) akış içeriği hakkında daha fazla bilgi için). Kılavuzları en iyi forms içinde kullanılan (neredeyse her yerden dışında içerik akışı). İçinde bir <xref:System.Windows.Documents.FlowDocument>, <xref:System.Windows.Documents.Table> destekler, sayfa numaralandırma, sütun yeniden akış ve içerik seçimi gibi içerik davranışları akış bir <xref:System.Windows.Controls.Grid> desteklemez. A <xref:System.Windows.Controls.Grid> diğer yandan en iyi dışında kullanılan bir <xref:System.Windows.Documents.FlowDocument> dahil olmak üzere birçok nedenlerle <xref:System.Windows.Controls.Grid> bir satır ve sütun dizini üzerinde temel öğeleri ekler <xref:System.Windows.Documents.Table> desteklemez. <xref:System.Windows.Controls.Grid> Öğesi tek "hücre." mevcut birden fazla öğe izin vererek alt içeriğinin katmanlama sağlar <xref:System.Windows.Documents.Table>katmanlama desteklemez. Alt öğelerinin bir <xref:System.Windows.Controls.Grid> "hücre" sınırlarının alanına göre mutlak olarak konumlandırılmış olabilir. <xref:System.Windows.Documents.Table>Bu özelliği desteklemez. Son olarak, bir <xref:System.Windows.Controls.Grid> daha açık ağırlığı bir <xref:System.Windows.Documents.Table>.  
  
#### <a name="sizing-behavior-of-columns-and-rows"></a>Satırları ve sütunları boyutlandırma davranışı  
 İçinde tanımlanan satırları ve sütunları bir <xref:System.Windows.Controls.Grid> yararlanabilir <xref:System.Windows.GridUnitType.Star> kalan alanı orantılı olarak dağıtmak için boyutlandırma. Zaman <xref:System.Windows.GridUnitType.Star> bir satır veya sütun veya satır kalan kullanılabilir alan ağırlıklı bir kısmının aldığını sütun genişliği veya yüksekliği seçilir. Tersine için budur <xref:System.Windows.GridUnitType.Auto>, hangi eşit olarak bir sütun veya satır içinde içeriğin boyutunu temel alan dağıtmak. Bu değer olarak ifade edilen `*` veya `2*` kullanırken [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]. İlk durumda satır veya sütun bir kez kullanılabilir alanı, İkinci durumda, iki kez almak ve benzeri. Orantılı olarak alanıyla dağıtmak için bu tekniği birleştiren bir <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> ve <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> değerini `Stretch` Bölümü düzen alanına ekran alanının yüzdesi olarak mümkündür. <xref:System.Windows.Controls.Grid>Bu şekilde alanı dağıtabilirsiniz tek düzen panosudur.  
  
#### <a name="defining-and-using-a-grid"></a>Tanımlama ve kılavuz kullanma  
 Aşağıdaki örnekte nasıl oluşturulacağını gösteren bir [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] Çalıştır iletişim kutusunda kullanılabilir bulunan benzer [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] Başlat menüsü.  
  
 [!code-csharp[GridRunDialog#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GridRunDialog/CSharp/window1.xaml.cs#1)]
 [!code-vb[GridRunDialog#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/GridRunDialog/VisualBasic/grid_vb.vb#1)]  
  
 Derlenmiş uygulama yeni bir verir [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] aşağıdakine benzer.  
  
 ![Tipik bir kılavuz öğesi. ] (../../../../docs/framework/wpf/controls/media/avalon-run-dialog.PNG "avalon_run_dialog")  
  
<a name="Panels_overview_StackPanel_subsection"></a>   
### <a name="stackpanel"></a>StackPanel  
 A <xref:System.Windows.Controls.StackPanel> "atanmış bir yönde öğeleri yığın" sağlar. Varsayılan yığın yönü dikeydir. <xref:System.Windows.Controls.StackPanel.Orientation%2A> Özelliği, içerik akışını denetlemek için kullanılabilir.  
  
#### <a name="stackpanel-vs-dockpanel"></a>StackPanel vs. DockPanel  
 Ancak <xref:System.Windows.Controls.DockPanel> de "alt öğelerini yığın" <xref:System.Windows.Controls.DockPanel> ve <xref:System.Windows.Controls.StackPanel> benzer bazı kullanım senaryolarında sonuçlar değil. Örneğin, alt öğelerin sırasını kendi boyutunda etkileyebilecek bir <xref:System.Windows.Controls.DockPanel> de bir <xref:System.Windows.Controls.StackPanel>. Bunun nedeni, <xref:System.Windows.Controls.StackPanel> ölçüleri yığının yönde <xref:System.Double.PositiveInfinity>, ancak <xref:System.Windows.Controls.DockPanel> yalnızca kullanılabilir boyutu ölçer.  
  
 Aşağıdaki örnek, bu anahtar farklılık gösterir.  
  
 [!code-cpp[StackPanelOvw4#1](../../../../samples/snippets/cpp/VS_Snippets_Wpf/StackPanelOvw4/CPP/StackPanel_Ovw_Sample4.cpp#1)]
 [!code-csharp[StackPanelOvw4#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StackPanelOvw4/CSharp/StackPanel_Ovw_Sample4.cs#1)]
 [!code-vb[StackPanelOvw4#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/StackPanelOvw4/VisualBasic/StackPanelSamp.vb#1)]
 [!code-xaml[StackPanelOvw4#1](../../../../samples/snippets/xaml/VS_Snippets_Wpf/StackPanelOvw4/XAML/default.xaml#1)]  
  
 Bu görüntü işleme davranışı fark görülebilir.  
  
 ![Ekran görüntüsü: StackPanel vs. DockPanel ekran](../../../../docs/framework/wpf/controls/media/layout-smiley-stackpanel.PNG "layout_smiley_stackpanel")  
  
#### <a name="defining-and-using-a-stackpanel"></a>Tanımlama ve StackPanel kullanma  
 Aşağıdaki örnekte nasıl kullanılacağını gösteren bir <xref:System.Windows.Controls.StackPanel> düğmelerini dikey olarak konumlandırılmış bir küme oluşturmak için. Yatay konumlandırma için ayarlanmış <xref:System.Windows.Controls.StackPanel.Orientation%2A> özelliğine <xref:System.Windows.Controls.Orientation.Horizontal>.  
  
 [!code-csharp[StackPanel_ovw2#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StackPanel_ovw2/CSharp/StackPanel_Ovw_Sample2.cs#1)]
 [!code-vb[StackPanel_ovw2#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/StackPanel_ovw2/VisualBasic/StackPanelOvw.vb#1)]  
  
 Derlenmiş uygulama yeni bir verir [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] aşağıdakine benzer.  
  
 ![Tipik bir StackPanel öğesi. ] (../../../../docs/framework/wpf/controls/media/panel-intro-stackpanel.PNG "panel_intro_stackpanel")  
  
<a name="Panels_overview_VirtualizingStackPanel_subsection"></a>   
#### <a name="virtualizingstackpanel"></a>VirtualizingStackPanel  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]Ayrıca bir çeşitlemesi sağlar <xref:System.Windows.Controls.StackPanel> otomatik olarak "veri bağlama alt içeriğini sanallaştıran" öğesi. Bu bağlamda word sanallaştırmak olarak bir alt öğelerinin oluşturulduğu çok sayıda veri öğeleri hangi öğelerin ekranda görülebilir olduğuna dayalı bir tekniği anlamına gelir. Hem bellek ve sadece birkaç ekranda belirli bir zamanda olabilir, çok sayıda kullanıcı Arabirimi öğeleri oluşturmak için işlemci bakımından yoğun. <xref:System.Windows.Controls.VirtualizingStackPanel>(tarafından sağlanan işlevsellik aracılığıyla <xref:System.Windows.Controls.VirtualizingPanel>) görünen öğeleri hesaplar ve birlikte çalıştığı <xref:System.Windows.Controls.ItemContainerGenerator> gelen bir <xref:System.Windows.Controls.ItemsControl> (gibi <xref:System.Windows.Controls.ListBox> veya <xref:System.Windows.Controls.ListView>) yalnızca görünür öğeler için oluşturmak için.  
  
 <xref:System.Windows.Controls.VirtualizingStackPanel> Öğesini otomatik olarak ayarlamak için denetimleri gibi öğeler konağı olarak <xref:System.Windows.Controls.ListBox>. Bir veri barındırma koleksiyonu bağlı olduğunda, içerik sınırları içinde olduğu sürece içeriği otomatik olarak, sanallaştırılmış bir <xref:System.Windows.Controls.ScrollViewer>. Bu önemli ölçüde performans birçok alt öğeleri barındırma artırır.  
  
 Aşağıdaki biçimlendirmede nasıl kullanılacağını göstermektedir bir <xref:System.Windows.Controls.VirtualizingStackPanel> öğeleri ana bilgisayarı olarak. <xref:System.Windows.Controls.VirtualizingStackPanel.IsVirtualizingProperty%2A?displayProperty=nameWithType> Ekli özellik ayarlanmalıdır `true` (varsayılan) gerçekleşmesi, sanallaştırma için.  
  
 [!code-xaml[VirtualizingStackPanel_Intro#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/VirtualizingStackPanel_Intro/CS/default.xaml#1)]  
  
<a name="Panels_overview_WrapPanel"></a>   
### <a name="wrappanel"></a>WrapPanel  
 <xref:System.Windows.Controls.WrapPanel>alt öğelerini soldan sağa doğru içeriği kendi üst kapsayıcı kenarı ulaştığında sonraki satıra bölerek sıralı konumda yerleştirmek için kullanılır. İçerik yatay veya dikey olarak yönlendirilebilir. <xref:System.Windows.Controls.WrapPanel>Basit akan için yararlıdır [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] senaryoları. Ayrıca, tüm alt öğeleri Tekdüzen boyutlandırma uygulamak için de kullanılabilir.  
  
 Aşağıdaki örnekte nasıl oluşturulduğunu gösteren bir <xref:System.Windows.Controls.WrapPanel> görüntülenecek <xref:System.Windows.Controls.Button> kendi kapsayıcı kenarı ulaştığında sarmalamak denetimleri.  
  
 [!code-cpp[WrapPanel_Intro#1](../../../../samples/snippets/cpp/VS_Snippets_Wpf/WrapPanel_Intro/CPP/WrapPanel_Code.cpp#1)]
 [!code-csharp[WrapPanel_Intro#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WrapPanel_Intro/CSharp/WrapPanel_Code.cs#1)]
 [!code-vb[WrapPanel_Intro#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WrapPanel_Intro/VisualBasic/WrapPanel_vb.vb#1)]
 [!code-xaml[WrapPanel_Intro#1](../../../../samples/snippets/xaml/VS_Snippets_Wpf/WrapPanel_Intro/XAML/default.xaml#1)]  
  
 Derlenmiş uygulama yeni bir verir [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] aşağıdakine benzer.  
  
 ![Tipik bir WrapPanel öğesi. ] (../../../../docs/framework/wpf/controls/media/wrappanel-element.PNG "WrapPanel_Element")  
  
<a name="Panels_nested_panel_elements"></a>   
## <a name="nested-panel-elements"></a>İç içe geçmiş Panel öğeleri  
 <xref:System.Windows.Controls.Panel>öğeleri diğer içinde karmaşık düzenleri üretmek için iç içe. Bu durumlarda çok kullanışlı bir yerde kanıtlayabilirsiniz <xref:System.Windows.Controls.Panel> bir kısmı için ideal bir [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], farklı bir kısmı gereksinimlerini karşılamayabilir ancak [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)].  
  
 Uygulamanızın destekleyebileceği iç içe geçme miktarı için kullanışlı bir sınır yoktur, ancak yalnızca istenen düzeninizi için gerçekten gerekli olan bu paneller kullanmak için uygulamanızı sınırlamak genellikle en iyisidir. Çoğu durumda, bir <xref:System.Windows.Controls.Grid> öğesi, iç içe geçmiş paneller düzen kapsayıcı olarak esnekliği nedeniyle yerine kullanılabilir. Gereksiz öğeleri ağaç dışında tutarak bu, uygulamanızın performansını artırabilir.  
  
 Aşağıdaki örnekte nasıl oluşturulduğunu gösteren bir [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] yararlanır iç içe <xref:System.Windows.Controls.Panel> belirli bir düzen elde etmek için öğeleri. Bu örnekte, bir <xref:System.Windows.Controls.DockPanel> öğesi sağlamak için kullanılır [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] yapısı ve iç içe geçmiş <xref:System.Windows.Controls.StackPanel> öğeleri, bir <xref:System.Windows.Controls.Grid>ve bir <xref:System.Windows.Controls.Canvas> alt öğelerin tam olarak üst konumlandırmak için kullanılan <xref:System.Windows.Controls.DockPanel>.  
  
 [!code-csharp[Nested_Panels#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Nested_Panels/CSharp/nestedpanels.cs#1)]
 [!code-vb[Nested_Panels#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Nested_Panels/VisualBasic/nestedpanels.vb#1)]  
  
 Derlenmiş uygulama yeni bir verir [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] aşağıdakine benzer.  
  
 ![İç içe geçmiş paneller yararlanan bir kullanıcı Arabirimi. ] (../../../../docs/framework/wpf/controls/media/nested-panels.PNG "nested_panels")  
  
<a name="Panels_custom_panel_elements"></a>   
## <a name="custom-panel-elements"></a>Özel Panel öğeleri  
 Sırada [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] esnek düzen denetimleri, davranışları da elde edilebilir kılarak özel düzen dizisi sağlar <xref:System.Windows.FrameworkElement.ArrangeOverride%2A> ve <xref:System.Windows.FrameworkElement.MeasureOverride%2A> yöntemleri. Boyutlandırma ve konumlama özel tarafından gerçekleştirilebilir geçersiz kılma yöntemleri yeni davranışları bunlar içinde konumlandırma tanımlama.  
  
 Benzer şekilde, özel düzen davranışlarına dayalı türetilmiş sınıfları (gibi <xref:System.Windows.Controls.Canvas> veya <xref:System.Windows.Controls.Grid>) geçersiz kılarak tanımlanabilir kendi <xref:System.Windows.FrameworkElement.ArrangeOverride%2A> ve <xref:System.Windows.FrameworkElement.MeasureOverride%2A> yöntemleri.  
  
 Aşağıdaki biçimlendirmede nasıl özel bir oluşturulduğunu gösteren <xref:System.Windows.Controls.Panel> öğesi. Bu yeni <xref:System.Windows.Controls.Panel>, tanımlanmış olarak `PlotPanel`, sabit kodlanmış kullanımı ile alt öğeleri konumlandırma destekleyen *x -* ve *y*koordinatları. Bu örnekte, bir <xref:System.Windows.Shapes.Rectangle> (gösterilmez) öğesi çizim noktada 50 konumlandırılır (*x*) ve 50 (*y*).  
  
 [!code-cpp[PlotPanel#1](../../../../samples/snippets/cpp/VS_Snippets_Wpf/PlotPanel/CPP/PlotPanel.cpp#1)]
 [!code-csharp[PlotPanel#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PlotPanel/CSharp/PlotPanel.cs#1)]
 [!code-vb[PlotPanel#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PlotPanel/VisualBasic/PlotPanel.vb#1)]  
  
 Daha karmaşık bir özel Masası uygulaması görüntülemek için bkz: [kaydırma özel içerik Panel örneği oluşturma](http://go.microsoft.com/fwlink/?LinkID=159979).  
  
<a name="Panels_global_localization"></a>   
## <a name="localizationglobalization-support"></a>Yerelleştirme/Genelleştirme desteği  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]Yerelleştirilebilir oluşturulmasında yardımcı özellikleri destekler [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)].  
  
 Tüm panel öğeleri yerel olarak destekleyen <xref:System.Windows.FrameworkElement.FlowDirection%2A> dinamik olarak bir kullanıcının yerel ayarı veya dil ayarlarınızı temel alan içeriği yeniden akış için kullanılan özellik. Daha fazla bilgi için bkz. <xref:System.Windows.FrameworkElement.FlowDirection%2A>.  
  
 <xref:System.Windows.Window.SizeToContent%2A> Özelliği, uygulama geliştiricilerinin sağlayan bir mekanizma sağlar gereksinimlerini tahmin etmenize yerelleştirilmiş [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]. Kullanarak <xref:System.Windows.SizeToContent.WidthAndHeight> bu özellik, bir üst değerini <xref:System.Windows.Window> her zaman içeriğin sığması için dinamik olarak boyutları ve yapay yüksekliği veya genişliği kısıtlamalar ile sınırlı değildir.  
  
 <xref:System.Windows.Controls.DockPanel>, <xref:System.Windows.Controls.Grid>, ve <xref:System.Windows.Controls.StackPanel> için tüm iyi seçimleri yerelleştirilebilir [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]. <xref:System.Windows.Controls.Canvas>iyi bir seçim değildir, ancak, bu içeriği mutlak, yerelleştirme zorlaşır konumlandırır nedeni.  
  
 Oluşturma hakkında ek bilgi için [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] yerelleştirilebilir uygulamalarla [!INCLUDE[TLA#tla_ui#plural](../../../../includes/tlasharptla-uisharpplural-md.md)]s, bkz: [kullanım Otomatik Yerleşim genel bakış](../../../../docs/framework/wpf/advanced/use-automatic-layout-overview.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [İzlenecek Yol: İlk WPF masaüstü uygulamam](../../../../docs/framework/wpf/getting-started/walkthrough-my-first-wpf-desktop-application.md)  
 [WPF Düzen Galerisi örneği](http://go.microsoft.com/fwlink/?LinkID=160054)  
 [Düzen](../../../../docs/framework/wpf/advanced/layout.md)  
 [WPF denetimleri galeri örneği](http://go.microsoft.com/fwlink/?LinkID=160053)  
 [Hizalama, Kenar Boşlukları ve Doldurmaya Genel Bakış](../../../../docs/framework/wpf/advanced/alignment-margins-and-padding-overview.md)  
 [Özel bir içerik kaydırma Panel örneği oluşturma](http://go.microsoft.com/fwlink/?LinkID=159979)  
 [Ekli Özelliklere Genel Bakış](../../../../docs/framework/wpf/advanced/attached-properties-overview.md)  
 [Otomatik Düzen Kullanımına Genel Bakış](../../../../docs/framework/wpf/advanced/use-automatic-layout-overview.md)  
 [Düzen ve Tasarım](../../../../docs/framework/wpf/advanced/optimizing-performance-layout-and-design.md)
