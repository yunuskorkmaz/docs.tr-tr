---
title: İçerik Modeli
ms.date: 03/30/2017
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
ms.openlocfilehash: ec4e96c0883489135b77f09a3c19f144cb4d30bc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187399"
---
# <a name="wpf-content-model"></a>WPF İçerik Modeli
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]birincil amacı farklı içerik türlerini görüntülemek olan birçok denetim ve denetim benzeri türler sağlayan bir sunum platformudur. Hangi denetimin kullanılacağını veya hangi denetimden türediğinizi belirlemek için, belirli bir denetimin en iyi görüntülenebildiği nesne türlerini anlamanız gerekir.  
  
 Bu konu, denetim ve [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] denetim benzeri türleri için içerik modelini özetler. İçerik modeli, denetimde hangi içeriğin kullanılabileceğini açıklar. Bu konu, her içerik modeli için içerik özelliklerini de listeler. İçerik özelliği, nesnenin içeriğini depolamak için kullanılan bir özelliktir.  

<a name="classes_that_contain_arbitrary_content"></a>
## <a name="classes-that-contain-arbitrary-content"></a>Rasgele İçerik İçeren Sınıflar  
 Bazı denetimler, dize, <xref:System.DateTime> nesne veya ek öğeler için <xref:System.Windows.UIElement> kapsayıcı olan bir kapsayıcı gibi herhangi bir türde bir nesne içerebilir. Örneğin, bir <xref:System.Windows.Controls.Button> resim ve bazı metin içerebilir; veya <xref:System.Windows.Controls.CheckBox> bir değeri <xref:System.DateTime.Now%2A?displayProperty=nameWithType>içerebilir.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]rasgele içerik içerebilen dört sınıfı vardır. Aşağıdaki tabloda, 'den <xref:System.Windows.Controls.Control>devralınan sınıflar listele  
  
|Rasgele içerik içeren sınıf|İçerik|  
|-------------------------------------------|-------------|  
|<xref:System.Windows.Controls.ContentControl>|Tek bir rasgele nesne.|  
|<xref:System.Windows.Controls.HeaderedContentControl>|Her ikisi de rasgele nesneler olan bir üstbilgi ve tek bir öğe.|  
|<xref:System.Windows.Controls.ItemsControl>|Rasgele nesneler topluluğu.|  
|<xref:System.Windows.Controls.HeaderedItemsControl>|Üstbilgi ve öğelerin bir koleksiyon, hepsi rasgele nesnelerdir.|  
  
 Bu sınıflardan devralan denetimler aynı içerik türünü içerebilir ve içeriği aynı şekilde işleyebilir. Aşağıdaki resimde, resim ve bazı metin içeren her içerik modelinden bir denetim gösterilmektedir:  
  
 ![Her içerik modelinden bir tane olmak üzere dört farklı denetim gösteren ekran görüntüsü.](./media/wpf-content-model/control-content-model-image-text.png)  
  
### <a name="controls-that-contain-a-single-arbitrary-object"></a>Tek Bir Rasgele Nesne İçeren Denetimler  
 Sınıf, <xref:System.Windows.Controls.ContentControl> tek bir rasgele içerik parçası içerir. İçeriğinin özelliği <xref:System.Windows.Controls.ContentControl.Content%2A>. Aşağıdaki denetimler, <xref:System.Windows.Controls.ContentControl> içerik modelinden devralır ve kullanır:  
  
- <xref:System.Windows.Controls.Button>  
  
- <xref:System.Windows.Controls.Primitives.ButtonBase>  
  
- <xref:System.Windows.Controls.CheckBox>  
  
- <xref:System.Windows.Controls.ComboBoxItem>  
  
- <xref:System.Windows.Controls.ContentControl>  
  
- <xref:System.Windows.Controls.Frame>  
  
- <xref:System.Windows.Controls.GridViewColumnHeader>  
  
- <xref:System.Windows.Controls.GroupItem>  
  
- <xref:System.Windows.Controls.Label>  
  
- <xref:System.Windows.Controls.ListBoxItem>  
  
- <xref:System.Windows.Controls.ListViewItem>  
  
- <xref:System.Windows.Navigation.NavigationWindow>  
  
- <xref:System.Windows.Controls.RadioButton>  
  
- <xref:System.Windows.Controls.Primitives.RepeatButton>  
  
- <xref:System.Windows.Controls.ScrollViewer>  
  
- <xref:System.Windows.Controls.Primitives.StatusBarItem>  
  
- <xref:System.Windows.Controls.Primitives.ToggleButton>  
  
- <xref:System.Windows.Controls.ToolTip>  
  
- <xref:System.Windows.Controls.UserControl>  
  
- <xref:System.Windows.Window>  
  
 Aşağıdaki resimde, bir <xref:System.Windows.Controls.ContentControl.Content%2A> dize, bir <xref:System.DateTime> nesne, a <xref:System.Windows.Shapes.Rectangle>, ve <xref:System.Windows.Controls.Panel> a <xref:System.Windows.Shapes.Ellipse> için <xref:System.Windows.Controls.TextBlock>ayarlanmış dört düğme gösterir ve bir:  
  
 ![Farklı içerik türlerine sahip dört düğme gösteren ekran görüntüsü.](./media/wpf-content-model/control-content-model-buttons.png)  
  
 Özelliğin nasıl ayarlanabildiğini <xref:System.Windows.Controls.ContentControl.Content%2A> öğrenmek <xref:System.Windows.Controls.ContentControl>için bkz.  
  
### <a name="controls-that-contain-a-header-and-a-single-arbitrary-object"></a>Üstbilgi ve Tek Rasgele Nesne İçeren Denetimler  
 Sınıf, <xref:System.Windows.Controls.HeaderedContentControl> içeriği <xref:System.Windows.Controls.ContentControl> üstbilgiyle devralır ve görüntüler. İçerik özelliğini devralır <xref:System.Windows.Controls.ContentControl.Content%2A> <xref:System.Windows.Controls.ContentControl> ve türünde <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> <xref:System.Object>olan özelliği tanımlar; bu nedenle, her ikisi de rasgele bir nesne olabilir.  
  
 Aşağıdaki denetimler, <xref:System.Windows.Controls.HeaderedContentControl> içerik modelinden devralır ve kullanır:  
  
- <xref:System.Windows.Controls.Expander>  
  
- <xref:System.Windows.Controls.GroupBox>  
  
- <xref:System.Windows.Controls.TabItem>  
  
 Aşağıdaki resimde iki <xref:System.Windows.Controls.TabItem> nesne gösterilmektedir. İlk <xref:System.Windows.Controls.TabItem> ve <xref:System.Windows.UIElement> olarak <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> nesneleri <xref:System.Windows.Controls.ContentControl.Content%2A>vardır. Bir <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> ve bir <xref:System.Windows.Controls.StackPanel> <xref:System.Windows.Shapes.Ellipse> içeren bir <xref:System.Windows.Controls.TextBlock>olarak ayarlanır. A <xref:System.Windows.Controls.ContentControl.Content%2A> ve a <xref:System.Windows.Controls.StackPanel> içeren <xref:System.Windows.Controls.TextBlock> bir <xref:System.Windows.Controls.Label>olarak ayarlanır. İkinci <xref:System.Windows.Controls.TabItem> ve bir <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> <xref:System.Windows.Controls.TextBlock> dize vardır <xref:System.Windows.Controls.ContentControl.Content%2A>.  
  
 ![Üstbilgi özelliğinde farklı türleri kullanan Sekme Denetimi.](./media/wpf-content-model/control-content-model-tab.png)  
  
 Nesnelerin nasıl oluşturulabildiğini <xref:System.Windows.Controls.TabItem> görmek için <xref:System.Windows.Controls.HeaderedContentControl>bkz.  
  
### <a name="controls-that-contain-a-collection-of-arbitrary-objects"></a>Rasgele Nesneler Topluluğu İçeren Denetimler  
 Sınıf, <xref:System.Windows.Controls.ItemsControl> dizeleri, nesneleri veya diğer öğeler gibi birden çok öğeden <xref:System.Windows.Controls.Control> devralır ve içerebilir. İçerik özellikleri <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> ve <xref:System.Windows.Controls.ItemsControl.Items%2A>. <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>genellikle bir veri toplama <xref:System.Windows.Controls.ItemsControl> ile doldurmak için kullanılır. Doldurmak için bir koleksiyon kullanmak <xref:System.Windows.Controls.ItemsControl>istemiyorsanız, <xref:System.Windows.Controls.ItemsControl.Items%2A> özelliği kullanarak öğeleri ekleyebilirsiniz.  
  
 Aşağıdaki denetimler, <xref:System.Windows.Controls.ItemsControl> içerik modelinden devralır ve kullanır:  
  
- <xref:System.Windows.Controls.Menu>  
  
- <xref:System.Windows.Controls.Primitives.MenuBase>  
  
- <xref:System.Windows.Controls.ContextMenu>  
  
- <xref:System.Windows.Controls.ComboBox>  
  
- <xref:System.Windows.Controls.ItemsControl>  
  
- <xref:System.Windows.Controls.ListBox>  
  
- <xref:System.Windows.Controls.ListView>  
  
- <xref:System.Windows.Controls.TabControl>  
  
- <xref:System.Windows.Controls.TreeView>  
  
- <xref:System.Windows.Controls.Primitives.Selector>  
  
- <xref:System.Windows.Controls.Primitives.StatusBar>  
  
 Aşağıdaki resimde bu <xref:System.Windows.Controls.ListBox> tür öğeleri içeren bir gösteri:  
  
- Bir ip.  
  
- Bir <xref:System.DateTime> nesnesi.  
  
- Bir <xref:System.Windows.UIElement>.  
  
- A <xref:System.Windows.Controls.Panel> ve <xref:System.Windows.Shapes.Ellipse> bir <xref:System.Windows.Controls.TextBlock>içerir.  
  
 ![Dört tür içeriğe sahip bir ListBox gösteren ekran görüntüsü.](./media/wpf-content-model/control-content-model-listbox.png)  
  
### <a name="controls-that-contain-a-header-and-a-collection-of-arbitrary-objects"></a>Üstbilgi ve Rasgele Nesneler Topluluğu İçeren Denetimler  
 Sınıf, <xref:System.Windows.Controls.HeaderedItemsControl> dizeleri, nesneler veya diğer öğeler ve bir üstbilgi gibi birden çok öğeden <xref:System.Windows.Controls.ItemsControl> devralır ve içerebilir. İçerik özelliklerini <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>devralır ve <xref:System.Windows.Controls.ItemsControl.Items%2A>rasgele bir nesne <xref:System.Windows.Controls.HeaderedItemsControl.Header%2A> olabilecek özelliği tanımlar. <xref:System.Windows.Controls.ItemsControl>  
  
 Aşağıdaki denetimler, <xref:System.Windows.Controls.HeaderedItemsControl> içerik modelinden devralır ve kullanır:  
  
- <xref:System.Windows.Controls.MenuItem>  
  
- <xref:System.Windows.Controls.ToolBar>  
  
- <xref:System.Windows.Controls.TreeViewItem>  
  
<a name="classes_that_contain_a_collection_of_uielement_objects"></a>
## <a name="classes-that-contain-a-collection-of-uielement-objects"></a>UIElement Nesnelerinin Bir Koleksiyonunu İçeren Sınıflar  
 Sınıf <xref:System.Windows.Controls.Panel> konumları ve <xref:System.Windows.UIElement> alt nesneleri düzenler. İçeriğinin özelliği <xref:System.Windows.Controls.Panel.Children%2A>.  
  
 Aşağıdaki sınıflar <xref:System.Windows.Controls.Panel> sınıftan devralır ve içerik modelini kullanır:  
  
- <xref:System.Windows.Controls.Canvas>  
  
- <xref:System.Windows.Controls.DockPanel>  
  
- <xref:System.Windows.Controls.Grid>  
  
- <xref:System.Windows.Controls.Primitives.TabPanel>  
  
- <xref:System.Windows.Controls.Primitives.ToolBarOverflowPanel>  
  
- <xref:System.Windows.Controls.Primitives.ToolBarPanel>  
  
- <xref:System.Windows.Controls.Primitives.UniformGrid>  
  
- <xref:System.Windows.Controls.StackPanel>  
  
- <xref:System.Windows.Controls.VirtualizingPanel>  
  
- <xref:System.Windows.Controls.VirtualizingStackPanel>  
  
- <xref:System.Windows.Controls.WrapPanel>  
  
 Daha fazla bilgi için [Paneller Genel Bakış'a](panels-overview.md)bakın.  
  
<a name="classes_that_affects_the_appearance_of_a_uielement"></a>
## <a name="classes-that-affect-the-appearance-of-a-uielement"></a>Bir UIElement görünümünü etkileyen sınıflar  
 Sınıf, <xref:System.Windows.Controls.Decorator> tek bir çocuğun <xref:System.Windows.UIElement>üzerine veya çevresine görsel efektler uygular. İçeriğinin özelliği <xref:System.Windows.Controls.Decorator.Child%2A>. Aşağıdaki sınıflar, <xref:System.Windows.Controls.Decorator> içerik modelinden devralır ve kullanır:  
  
- <xref:System.Windows.Documents.AdornerDecorator>  
  
- <xref:System.Windows.Controls.Border>  
  
- <xref:System.Windows.Controls.Primitives.BulletDecorator>  
  
- <xref:Microsoft.Windows.Themes.ButtonChrome>  
  
- <xref:Microsoft.Windows.Themes.ClassicBorderDecorator>  
  
- <xref:System.Windows.Controls.InkPresenter>  
  
- <xref:Microsoft.Windows.Themes.ListBoxChrome>  
  
- <xref:Microsoft.Windows.Themes.SystemDropShadowChrome>  
  
- <xref:System.Windows.Controls.Viewbox>  
  
 Aşağıdaki resimde, <xref:System.Windows.Controls.TextBox> etrafında bir (ile süslenmiş) <xref:System.Windows.Controls.Border> bir gösterir.  
  
 ![Kara kenarlıklı TextBox](./media/layout-border-around-textbox.png "Layout_Border_around_TextBox")  
Kenarlık olan TextBlock  
  
<a name="classes_that_provides_visual_feedback_about_a_uielement"></a>
## <a name="classes-that-provide-visual-feedback-about-a-uielement"></a>UIElement Hakkında Görsel Geri Bildirim Sağlayan Sınıflar  
 Sınıf, <xref:System.Windows.Documents.Adorner> kullanıcıya görsel ipuçları sağlar. Örneğin, öğelere <xref:System.Windows.Documents.Adorner> işlevsel işletmeler eklemek veya denetim hakkında durum bilgileri sağlamak için bir kullanın. Sınıf, <xref:System.Windows.Documents.Adorner> kendi süsleyicilerinizi oluşturabilmeniz için bir çerçeve sağlar. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]uygulanan süsleyiciler sağlamaz. Daha fazla bilgi için [Bkz. Adorners Genel Bakış.](adorners-overview.md)  
  
<a name="classes_that_enable_users_to_enter_text"></a>
## <a name="classes-that-enable-users-to-enter-text"></a>Kullanıcıların Metin Girmesini Sağlayan Sınıflar  
 WPF, kullanıcıların metin girmesini sağlayan üç birincil denetim sağlar. Her denetim metni farklı görüntüler. Aşağıdaki tabloda bu üç metinle ilgili denetim, metni görüntülediklerinde ki yetenekleri ve denetimmetnini içeren özellikleri listelenmektedir.  
  
|Denetim|Metin olarak görüntülenir|İçerik özelliği|  
|-------------|--------------------------|----------------------|  
|<xref:System.Windows.Controls.TextBox>|Düz metin|<xref:System.Windows.Controls.TextBox.Text%2A>|  
|<xref:System.Windows.Controls.RichTextBox>|Biçimlendirilmiş metin|<xref:System.Windows.Controls.RichTextBox.Document%2A>|  
|<xref:System.Windows.Controls.PasswordBox>|Gizli metin (karakterler maskelenir)|<xref:System.Windows.Controls.PasswordBox.Password%2A>|  
  
<a name="classes_that_display_text"></a>
## <a name="classes-that-display-your-text"></a>Metninizi Görüntüleyen Sınıflar  
 Düz veya biçimlendirilmiş metni görüntülemek için çeşitli sınıflar kullanılabilir. Küçük miktarda <xref:System.Windows.Controls.TextBlock> metin görüntülemek için kullanabilirsiniz. Büyük miktarda metin görüntülemek istiyorsanız, <xref:System.Windows.Controls.FlowDocumentReader>", <xref:System.Windows.Controls.FlowDocumentPageViewer>" <xref:System.Windows.Controls.FlowDocumentScrollViewer> veya denetimleri kullanın.  
  
 İki <xref:System.Windows.Controls.TextBlock> içerik özelliği <xref:System.Windows.Controls.TextBlock.Text%2A> vardır: ve <xref:System.Windows.Controls.TextBlock.Inlines%2A>. Tutarlı biçimlendirme kullanan metni görüntülemek istediğinizde, <xref:System.Windows.Controls.TextBlock.Text%2A> özellik genellikle en iyi seçimdir. Metin boyunca farklı biçimlendirme kullanmayı planlıyorsanız, <xref:System.Windows.Controls.TextBlock.Inlines%2A> özelliği kullanın. Özellik, <xref:System.Windows.Controls.TextBlock.Inlines%2A> metnin <xref:System.Windows.Documents.Inline> nasıl biçimlendirilenini belirten nesneler topluluğudur.  
  
 Aşağıdaki tabloda, ve <xref:System.Windows.Controls.FlowDocumentReader> <xref:System.Windows.Controls.FlowDocumentPageViewer> <xref:System.Windows.Controls.FlowDocumentScrollViewer> sınıflar için içerik özelliği listeleniztir.  
  
|Denetim|İçerik özelliği|İçerik özellik türü|  
|-------------|----------------------|---------------------------|  
|<xref:System.Windows.Controls.FlowDocumentPageViewer>|Belge|<xref:System.Windows.Documents.IDocumentPaginatorSource>|  
|<xref:System.Windows.Controls.FlowDocumentReader>|Belge|<xref:System.Windows.Documents.FlowDocument>|  
|<xref:System.Windows.Controls.FlowDocumentScrollViewer>|Belge|<xref:System.Windows.Documents.FlowDocument>|  
  
 <xref:System.Windows.Documents.IDocumentPaginatorSource> Arabirimi <xref:System.Windows.Documents.FlowDocument> uygular; bu nedenle, her üç <xref:System.Windows.Documents.FlowDocument> sınıf bir içerik olarak alabilir.  
  
<a name="classes_that_format_text"></a>
## <a name="classes-that-format-your-text"></a>Metninizi Biçimlendiren Sınıflar  
 <xref:System.Windows.Documents.TextElement>ve ilgili sınıfları metni biçimlendirmenize olanak sağlar. <xref:System.Windows.Documents.TextElement>nesneler metin <xref:System.Windows.Controls.TextBlock> içerir ve <xref:System.Windows.Documents.FlowDocument> biçimlendirin ve nesneler. İki birincil <xref:System.Windows.Documents.TextElement> nesne türü <xref:System.Windows.Documents.Block> öğeler <xref:System.Windows.Documents.Inline> ve öğelerdir. Öğe, <xref:System.Windows.Documents.Block> paragraf veya liste gibi bir metin bloğunu temsil eder. Öğe, <xref:System.Windows.Documents.Inline> bloğun metninin bir bölümünü temsil eder. Birçok <xref:System.Windows.Documents.Inline> sınıf, uygulandıkları metin için biçimlendirme belirtir. Her <xref:System.Windows.Documents.TextElement> birinin kendi içerik modeli vardır. Daha fazla bilgi için [TextElement İçerik Modeline Genel Bakış'a](../advanced/textelement-content-model-overview.md)bakın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Gelişmiş](../advanced/index.md)
