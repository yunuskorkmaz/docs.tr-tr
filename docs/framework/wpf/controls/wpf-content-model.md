---
title: "WPF İçerik Modeli"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- UIElement class [WPF], displaying content
- content model [WPF], controls
- controls [WPF], displaying text
- content display [WPF], controls
- controls [WPF], formatting text
- displaying content [WPF]
- arbitrary content classes [WPF], content model
- ContentControl class [WPF], displaying content
ms.assetid: 214da5ef-547a-4cf8-9b07-4aa8a0e52cdd
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7d708674682ffd7b0d13c9cbe828e28bbc26e260
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="wpf-content-model"></a>WPF İçerik Modeli
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]birçok denetimleri ve farklı içerik türlerini görüntülemek için birincil amacı olan denetim benzeri türleri sağlayan bir sunu platformudur. Kullanılacak hangi denetim veya denetleyen öğesinden türetilen belirlemek için belirli bir denetim en iyi görüntüleme nesne türlerini anlamanız gerekir.  
  
 Bu konu için içerik modelini özetler [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] denetimi ve denetim benzeri türler. İçerik modeli, hangi içerik denetimi kullanılabilir açıklar. Bu konu aynı zamanda her bir içerik modeli için içerik özellikleri listeler. İçerik özelliği nesnenin içeriğini depolamak için kullanılan bir özelliğidir.  
  
 
  
<a name="classes_that_contain_arbitrary_content"></a>   
## <a name="classes-that-contain-arbitrary-content"></a>Rasgele içerik içeren sınıflar  
 Bazı denetimler, dize gibi herhangi bir türde bir nesne içerebilir bir <xref:System.DateTime> nesnesi veya bir <xref:System.Windows.UIElement> yani ek öğelere ilişkin bir kapsayıcıdır. Örneğin, bir <xref:System.Windows.Controls.Button> resim ve bazı metinler; içerebilir veya <xref:System.Windows.Controls.CheckBox> değerini içerebilir <xref:System.DateTime.Now%2A?displayProperty=nameWithType>.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]rasgele içerik içerebilir dört sınıfları içerir. Devralınan sınıfları aşağıdaki tabloda listelenmektedir <xref:System.Windows.Controls.Control>.  
  
|Rastgele içeriği sınıfı|İçerik|  
|-------------------------------------------|-------------|  
|<xref:System.Windows.Controls.ContentControl>|Tek bir rasgele nesne.|  
|<xref:System.Windows.Controls.HeaderedContentControl>|Üstbilgi ve her ikisi de rasgele nesne olan tek bir öğe.|  
|<xref:System.Windows.Controls.ItemsControl>|Rastgele nesneleri koleksiyonu.|  
|<xref:System.Windows.Controls.HeaderedItemsControl>|Üstbilgi ve rasgele nesneler tümü öğeleri koleksiyonu.|  
  
 Bu sınıflardan devralan denetimleri aynı tür içerik içerebilir ve içeriği aynı şekilde ele alın. Aşağıdaki çizimde bir görüntü içeren her bir içerik modeli ve bazı metin bir denetimden gösterir.  
  
 ![Düğme, GroupBox, Listbax, TreeViewItem](../../../../docs/framework/wpf/controls/media/controlcontentmodelimagetextinto.PNG "ControlContentModelImageTextInto")  
  
### <a name="controls-that-contain-a-single-arbitrary-object"></a>Tek bir rasgele nesne içeren denetimler  
 <xref:System.Windows.Controls.ContentControl> Sınıfı rasgele içeriğin tek bir parçasını içerir. İçerik özelliği olan <xref:System.Windows.Controls.ContentControl.Content%2A>. Aşağıdaki denetimleri devralınmalıdır <xref:System.Windows.Controls.ContentControl> ve kendi içerik modelini kullanır:  
  
-   <xref:System.Windows.Controls.Button>  
  
-   <xref:System.Windows.Controls.Primitives.ButtonBase>  
  
-   <xref:System.Windows.Controls.CheckBox>  
  
-   <xref:System.Windows.Controls.ComboBoxItem>  
  
-   <xref:System.Windows.Controls.ContentControl>  
  
-   <xref:System.Windows.Controls.Frame>  
  
-   <xref:System.Windows.Controls.GridViewColumnHeader>  
  
-   <xref:System.Windows.Controls.GroupItem>  
  
-   <xref:System.Windows.Controls.Label>  
  
-   <xref:System.Windows.Controls.ListBoxItem>  
  
-   <xref:System.Windows.Controls.ListViewItem>  
  
-   <xref:System.Windows.Navigation.NavigationWindow>  
  
-   <xref:System.Windows.Controls.RadioButton>  
  
-   <xref:System.Windows.Controls.Primitives.RepeatButton>  
  
-   <xref:System.Windows.Controls.ScrollViewer>  
  
-   <xref:System.Windows.Controls.Primitives.StatusBarItem>  
  
-   <xref:System.Windows.Controls.Primitives.ToggleButton>  
  
-   <xref:System.Windows.Controls.ToolTip>  
  
-   <xref:System.Windows.Controls.UserControl>  
  
-   <xref:System.Windows.Window>  
  
 Aşağıdaki çizimde gösterildiği dört düğmeleri <xref:System.Windows.Controls.ContentControl.Content%2A> bir dizeye ayarlayın bir <xref:System.DateTime> nesne, bir <xref:System.Windows.Shapes.Rectangle>ve bir <xref:System.Windows.Controls.Panel> içeren bir <xref:System.Windows.Shapes.Ellipse> ve <xref:System.Windows.Controls.TextBlock>.  
  
 ![Dört düğme](../../../../docs/framework/wpf/controls/media/controlcontentmodelbuttons.PNG "ControlContentModelButtons")  
Farklı türde içerik sahibi olan dört düğmeleri  
  
 Bir örnek için nasıl ayarlanacağı <xref:System.Windows.Controls.ContentControl.Content%2A> özelliği, bkz: <xref:System.Windows.Controls.ContentControl>.  
  
### <a name="controls-that-contain-a-header-and-a-single-arbitrary-object"></a>Üstbilgi ve tek bir rasgele nesne içeren denetimler  
 <xref:System.Windows.Controls.HeaderedContentControl> Sınıfının devraldığı <xref:System.Windows.Controls.ContentControl> ve bir üstbilgiyle içeriğini görüntüler. İçerik özelliği devralır <xref:System.Windows.Controls.ContentControl.Content%2A>, gelen <xref:System.Windows.Controls.ContentControl> ve tanımlar <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> türü özelliği <xref:System.Object>; bu nedenle, her ikisi de rasgele bir nesne olabilir.  
  
 Aşağıdaki denetimleri devralınmalıdır <xref:System.Windows.Controls.HeaderedContentControl> ve kendi içerik modelini kullanır:  
  
-   <xref:System.Windows.Controls.Expander>  
  
-   <xref:System.Windows.Controls.GroupBox>  
  
-   <xref:System.Windows.Controls.TabItem>  
  
 Aşağıdaki çizimde iki gösterir <xref:System.Windows.Controls.TabItem> nesneleri. İlk <xref:System.Windows.Controls.TabItem> sahip <xref:System.Windows.UIElement> olarak nesneleri <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> ve <xref:System.Windows.Controls.ContentControl.Content%2A>. <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> Ayarlanmış bir <xref:System.Windows.Controls.StackPanel> içeren bir <xref:System.Windows.Shapes.Ellipse> ve <xref:System.Windows.Controls.TextBlock>. <xref:System.Windows.Controls.ContentControl.Content%2A> Ayarlanmış bir <xref:System.Windows.Controls.StackPanel> içeren bir <xref:System.Windows.Controls.TextBlock> ve <xref:System.Windows.Controls.Label>. İkinci <xref:System.Windows.Controls.TabItem> bir dize olan <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> ve <xref:System.Windows.Controls.TextBlock> içinde <xref:System.Windows.Controls.ContentControl.Content%2A>.  
  
 ![TabControl](../../../../docs/framework/wpf/controls/media/controlcontentmodelteabitem.PNG "ControlContentModelTeabItem")  
Üstbilgi özelliğinde farklı türlerini kullanan TabControl  
  
 Bir örnek için nasıl oluşturulacağını <xref:System.Windows.Controls.TabItem> nesneleri bkz <xref:System.Windows.Controls.HeaderedContentControl>.  
  
### <a name="controls-that-contain-a-collection-of-arbitrary-objects"></a>Rastgele nesne koleksiyonu içeren denetimler  
 <xref:System.Windows.Controls.ItemsControl> Sınıfının devraldığı <xref:System.Windows.Controls.Control> ve dize, nesneleri ve diğer öğeler gibi birden çok öğe içerebilir. İçerik özellikleri olan <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> ve <xref:System.Windows.Controls.ItemsControl.Items%2A>. <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>genellikle doldurmak için kullanılan <xref:System.Windows.Controls.ItemsControl> veri koleksiyonu. Doldurmak için bir koleksiyon kullanmak istemiyorsanız <xref:System.Windows.Controls.ItemsControl>, kullanarak öğeleri ekleyebilirsiniz <xref:System.Windows.Controls.ItemsControl.Items%2A> özelliği.  
  
 Aşağıdaki denetimleri devralınmalıdır <xref:System.Windows.Controls.ItemsControl> ve kendi içerik modelini kullanır:  
  
-   <xref:System.Windows.Controls.Menu>  
  
-   <xref:System.Windows.Controls.Primitives.MenuBase>  
  
-   <xref:System.Windows.Controls.ContextMenu>  
  
-   <xref:System.Windows.Controls.ComboBox>  
  
-   <xref:System.Windows.Controls.ItemsControl>  
  
-   <xref:System.Windows.Controls.ListBox>  
  
-   <xref:System.Windows.Controls.ListView>  
  
-   <xref:System.Windows.Controls.TabControl>  
  
-   <xref:System.Windows.Controls.TreeView>  
  
-   <xref:System.Windows.Controls.Primitives.Selector>  
  
-   <xref:System.Windows.Controls.Primitives.StatusBar>  
  
 Aşağıdaki çizimde gösterildiği bir <xref:System.Windows.Controls.ListBox> , bu tür öğeleri içerir:  
  
-   Bir dize.  
  
-   A <xref:System.DateTime> nesnesi.  
  
-   A <xref:System.Windows.UIElement>.  
  
-   A <xref:System.Windows.Controls.Panel> içeren bir <xref:System.Windows.Shapes.Ellipse> ve <xref:System.Windows.Controls.TextBlock>.  
  
 ![Dört tür içerikle ListBox](../../../../docs/framework/wpf/controls/media/controlcontentmodellistbox2.PNG "ControlContentModelListBox2")  
Birçok nesne türünü içeren ListBox  
  
### <a name="controls-that-contain-a-header-and-a-collection-of-arbitrary-objects"></a>Üstbilgi ve rasgele nesneler koleksiyonunu içeren denetimler  
 <xref:System.Windows.Controls.HeaderedItemsControl> Sınıfının devraldığı <xref:System.Windows.Controls.ItemsControl> ve dizeler, nesneler veya diğer öğeleri ve bir üstbilgi gibi birden çok öğe içerebilir. Devralır <xref:System.Windows.Controls.ItemsControl> içerik özellikleri, <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>, ve <xref:System.Windows.Controls.ItemsControl.Items%2A>, ve tanımlar <xref:System.Windows.Controls.HeaderedItemsControl.Header%2A> rasgele bir nesne olabilir özelliği.  
  
 Aşağıdaki denetimleri devralınmalıdır <xref:System.Windows.Controls.HeaderedItemsControl> ve kendi içerik modelini kullanır:  
  
-   <xref:System.Windows.Controls.MenuItem>  
  
-   <xref:System.Windows.Controls.ToolBar>  
  
-   <xref:System.Windows.Controls.TreeViewItem>  
  
<a name="classes_that_contain_a_collection_of_uielement_objects"></a>   
## <a name="classes-that-contain-a-collection-of-uielement-objects"></a>UIElement nesnelerinin bir koleksiyonunu içeren sınıflar  
 <xref:System.Windows.Controls.Panel> Sınıfı yerleştirir ve alt düzenler <xref:System.Windows.UIElement> nesneleri. İçerik özelliği olan <xref:System.Windows.Controls.Panel.Children%2A>.  
  
 Aşağıdaki sınıflar devralınmalıdır <xref:System.Windows.Controls.Panel> sınıfı ve kendi içerik modelini kullanır:  
  
-   <xref:System.Windows.Controls.Canvas>  
  
-   <xref:System.Windows.Controls.DockPanel>  
  
-   <xref:System.Windows.Controls.Grid>  
  
-   <xref:System.Windows.Controls.Primitives.TabPanel>  
  
-   <xref:System.Windows.Controls.Primitives.ToolBarOverflowPanel>  
  
-   <xref:System.Windows.Controls.Primitives.ToolBarPanel>  
  
-   <xref:System.Windows.Controls.Primitives.UniformGrid>  
  
-   <xref:System.Windows.Controls.StackPanel>  
  
-   <xref:System.Windows.Controls.VirtualizingPanel>  
  
-   <xref:System.Windows.Controls.VirtualizingStackPanel>  
  
-   <xref:System.Windows.Controls.WrapPanel>  
  
 Daha fazla bilgi için bkz: [paneller genel bakış](../../../../docs/framework/wpf/controls/panels-overview.md).  
  
<a name="classes_that_affects_the_appearance_of_a_uielement"></a>   
## <a name="classes-that-affect-the-appearance-of-a-uielement"></a>UIElement görünümünü etkileyen sınıfları  
 <xref:System.Windows.Controls.Decorator> Sınıfı uygulanır görsel efektler üzerine veya tek bir alt etrafında <xref:System.Windows.UIElement>. İçerik özelliği olan <xref:System.Windows.Controls.Decorator.Child%2A>. Aşağıdaki sınıflar devralınmalıdır <xref:System.Windows.Controls.Decorator> ve kendi içerik modelini kullanır:  
  
-   <xref:System.Windows.Documents.AdornerDecorator>  
  
-   <xref:System.Windows.Controls.Border>  
  
-   <xref:System.Windows.Controls.Primitives.BulletDecorator>  
  
-   <xref:Microsoft.Windows.Themes.ButtonChrome>  
  
-   <xref:Microsoft.Windows.Themes.ClassicBorderDecorator>  
  
-   <xref:System.Windows.Controls.InkPresenter>  
  
-   <xref:Microsoft.Windows.Themes.ListBoxChrome>  
  
-   <xref:Microsoft.Windows.Themes.SystemDropShadowChrome>  
  
-   <xref:System.Windows.Controls.Viewbox>  
  
 Aşağıdaki çizimde gösterildiği bir <xref:System.Windows.Controls.TextBox> olan (ile donatılmış) bir <xref:System.Windows.Controls.Border> çevresinde.  
  
 ![Siyah kenarlık kutusuyla](../../../../docs/framework/wpf/controls/media/layout-border-around-textbox.png "Layout_Border_around_TextBox")  
Kenarlığı olan TextBlock  
  
<a name="classes_that_provides_visual_feedback_about_a_uielement"></a>   
## <a name="classes-that-provide-visual-feedback-about-a-uielement"></a>UIElement hakkında görsel geribildirim sağlamak sınıfları  
 <xref:System.Windows.Documents.Adorner> Sınıfı, bir kullanıcı için görsel ipuçları sağlar. Örneğin, bir <xref:System.Windows.Documents.Adorner> işlevsel tanıtıcıları öğelere eklemek ya da bir denetimi hakkındaki durum bilgilerini sağlamak için. <xref:System.Windows.Documents.Adorner> Sınıfı, kendi donatıcılarınızı oluşturabilmesi için bir çerçeve sağlar. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]hiçbir uygulanmış donatıcı sağlamaz. Daha fazla bilgi için bkz: [Donatıcılara Genel Bakış](../../../../docs/framework/wpf/controls/adorners-overview.md).  
  
<a name="classes_that_enable_users_to_enter_text"></a>   
## <a name="classes-that-enable-users-to-enter-text"></a>Kullanıcıların metin girmesini sağlayan sınıflar  
 WPF metin girmesini sağlayan üç birincil denetimleri sağlar. Her denetim metni farklı görüntüler. Aşağıdaki tabloda, bu üç metin ile ilişkili denetimleri, metin ve denetimin metnini içeren özelliklerini görüntülediğinizde yeteneklerini listeler.  
  
|Denetim|Metin olarak görüntülenir|İçerik özelliği|  
|-------------|--------------------------|----------------------|  
|<xref:System.Windows.Controls.TextBox>|Düz metin|<xref:System.Windows.Controls.TextBox.Text%2A>|  
|<xref:System.Windows.Controls.RichTextBox>|Biçimlendirilmiş metin|<xref:System.Windows.Controls.RichTextBox.Document%2A>|  
|<xref:System.Windows.Controls.PasswordBox>|Gizli metin (karakterler maskelenir)|<xref:System.Windows.Controls.PasswordBox.Password%2A>|  
  
<a name="classes_that_display_text"></a>   
## <a name="classes-that-display-your-text"></a>Metninizi görüntülemek sınıfları  
 Birden fazla sınıf düz veya biçimlendirilmiş metni görüntülemek için kullanılabilir. Kullanabileceğiniz <xref:System.Windows.Controls.TextBlock> küçük miktarda metin görüntülemek için. Büyük miktarda metin görüntülemek istiyorsanız, kullanmak <xref:System.Windows.Controls.FlowDocumentReader>, <xref:System.Windows.Controls.FlowDocumentPageViewer>, veya <xref:System.Windows.Controls.FlowDocumentScrollViewer> kontrol eder.  
  
 <xref:System.Windows.Controls.TextBlock> İki içerik özelliği vardır: <xref:System.Windows.Controls.TextBlock.Text%2A> ve <xref:System.Windows.Controls.TextBlock.Inlines%2A>. Tutarlı biçimlendirme kullanan metni görüntülemek istediğinizde <xref:System.Windows.Controls.TextBlock.Text%2A> özelliktir genellikle en iyi seçimdir. Metnin tamamında farklı biçimlendirme kullanmayı planlıyorsanız, kullanmak <xref:System.Windows.Controls.TextBlock.Inlines%2A> özelliği. <xref:System.Windows.Controls.TextBlock.Inlines%2A> Özelliktir koleksiyonu <xref:System.Windows.Documents.Inline> metnin nasıl biçimlendirileceğini belirtin nesneleri.  
  
 İçerik özelliği için aşağıdaki tabloda listelenmektedir <xref:System.Windows.Controls.FlowDocumentReader>, <xref:System.Windows.Controls.FlowDocumentPageViewer>, ve <xref:System.Windows.Controls.FlowDocumentScrollViewer> sınıfları.  
  
|Denetim|İçerik özelliği|İçerik özelliği türü|  
|-------------|----------------------|---------------------------|  
|<xref:System.Windows.Controls.FlowDocumentPageViewer>|Belge|<xref:System.Windows.Documents.IDocumentPaginatorSource>|  
|<xref:System.Windows.Controls.FlowDocumentReader>|Belge|<xref:System.Windows.Documents.FlowDocument>|  
|<xref:System.Windows.Controls.FlowDocumentScrollViewer>|Belge|<xref:System.Windows.Documents.FlowDocument>|  
  
 <xref:System.Windows.Documents.FlowDocument> Uygulayan <xref:System.Windows.Documents.IDocumentPaginatorSource> arabirim; bu nedenle, tüm üç sınıf gerçekleştirebilir bir <xref:System.Windows.Documents.FlowDocument> içeriği.  
  
<a name="classes_that_format_text"></a>   
## <a name="classes-that-format-your-text"></a>Metni Biçimlendir sınıfları  
 <xref:System.Windows.Documents.TextElement>ve metin biçimlendirmek, ilgili sınıflar sağlar. <xref:System.Windows.Documents.TextElement>nesneleri içeren ve biçimlendirme metinde <xref:System.Windows.Controls.TextBlock> ve <xref:System.Windows.Documents.FlowDocument> nesneleri. İki birincil tür <xref:System.Windows.Documents.TextElement> nesneler <xref:System.Windows.Documents.Block> öğeleri ve <xref:System.Windows.Documents.Inline> öğeleri. A <xref:System.Windows.Documents.Block> öğesi, paragraf veya liste gibi bir metin bloğunu temsil eder. Bir <xref:System.Windows.Documents.Inline> öğesi blok içindeki metnin bir bölümünü temsil eder. Birçok <xref:System.Windows.Documents.Inline> sınıfları belirtmek için bunlar uygulanma metin için biçimlendirme. Her <xref:System.Windows.Documents.TextElement> kendi içerik modeli vardır. Daha fazla bilgi için bkz: [TextElement içerik modeli genel bakış](../../../../docs/framework/wpf/advanced/textelement-content-model-overview.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Gelişmiş](../../../../docs/framework/wpf/advanced/index.md)
