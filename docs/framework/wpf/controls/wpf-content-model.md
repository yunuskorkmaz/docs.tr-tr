---
title: İçerik modeli
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
ms.openlocfilehash: a84ab2e66b4e373591fc9365b1c17d0bb0c66713
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76738274"
---
# <a name="wpf-content-model"></a>WPF İçerik Modeli
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)], birincil amacı farklı içerik türlerini görüntülemek olan çok sayıda denetim ve denetim benzeri tür sağlayan bir sunum platformudur. Hangi denetimin kullanılacağını veya hangi denetimin türetileceğini öğrenmek için, belirli bir denetimin en iyi şekilde görüntüleyeceği nesne türlerini anlamanız gerekir.  
  
 Bu konu, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] denetimi ve denetim benzeri türler için içerik modeli özetler. İçerik modeli, bir denetimde hangi içeriğin kullanılabileceğini açıklar. Bu konu, her bir içerik modeli için içerik özelliklerini de listeler. İçerik özelliği, nesnenin içeriğini depolamak için kullanılan bir özelliktir.  

<a name="classes_that_contain_arbitrary_content"></a>   
## <a name="classes-that-contain-arbitrary-content"></a>Rastgele Içerik içeren sınıflar  
 Bazı denetimler dize, <xref:System.DateTime> nesnesi veya ek öğeler için kapsayıcı olan bir <xref:System.Windows.UIElement> gibi herhangi bir türde bir nesne içerebilir. Örneğin, bir <xref:System.Windows.Controls.Button> görüntü ve bazı metinler içerebilir; veya bir <xref:System.Windows.Controls.CheckBox>, <xref:System.DateTime.Now%2A?displayProperty=nameWithType>değerini içerebilir.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], rastgele içerik içerebilen dört sınıfa sahiptir. Aşağıdaki tabloda, <xref:System.Windows.Controls.Control>devraldığı sınıflar listelenmektedir.  
  
|Rastgele içerik içeren sınıf|İçerik|  
|-------------------------------------------|-------------|  
|<xref:System.Windows.Controls.ContentControl>|Tek bir rastgele nesne.|  
|<xref:System.Windows.Controls.HeaderedContentControl>|Her ikisi de rastgele nesneler olan üst bilgi ve tek öğe.|  
|<xref:System.Windows.Controls.ItemsControl>|Rastgele nesnelerden oluşan bir koleksiyon.|  
|<xref:System.Windows.Controls.HeaderedItemsControl>|Hepsi rastgele nesneler olan bir üst bilgi ve öğe koleksiyonu.|  
  
 Bu sınıflardan devralma denetimleri aynı içerik türünü içerebilir ve içeriği aynı şekilde ele alabilir. Aşağıdaki çizimde, bir görüntü ve bazı metinler içeren her bir içerik modelinden bir denetim gösterilmektedir:  
  
 ![Her içerik modelinden biri olmak üzere dört farklı denetimi gösteren ekran görüntüsü.](./media/wpf-content-model/control-content-model-image-text.png)  
  
### <a name="controls-that-contain-a-single-arbitrary-object"></a>Tek bir rastgele nesne içeren denetimler  
 <xref:System.Windows.Controls.ContentControl> sınıfı, tek bir rastgele içerik parçası içerir. İçerik özelliği <xref:System.Windows.Controls.ContentControl.Content%2A>. Aşağıdaki denetimler <xref:System.Windows.Controls.ContentControl> devralınır ve içerik modelini kullanır:  
  
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
  
 Aşağıdaki çizimde <xref:System.Windows.Controls.ContentControl.Content%2A> dize, <xref:System.DateTime> nesnesi, <xref:System.Windows.Shapes.Rectangle>ve <xref:System.Windows.Shapes.Ellipse> ve <xref:System.Windows.Controls.TextBlock>içeren bir <xref:System.Windows.Controls.Panel> olarak ayarlanan dört düğme gösterilmektedir:  
  
 ![Farklı içerik türleriyle dört düğme gösteren ekran görüntüsü.](./media/wpf-content-model/control-content-model-buttons.png)  
  
 <xref:System.Windows.Controls.ContentControl.Content%2A> özelliğinin nasıl ayarlanacağı hakkında bir örnek için bkz. <xref:System.Windows.Controls.ContentControl>.  
  
### <a name="controls-that-contain-a-header-and-a-single-arbitrary-object"></a>Üst bilgi ve tek bir rastgele nesne içeren denetimler  
 <xref:System.Windows.Controls.HeaderedContentControl> sınıfı <xref:System.Windows.Controls.ContentControl> devralır ve üst bilgiyle içerik görüntüler. <xref:System.Windows.Controls.ContentControl> ' dan <xref:System.Windows.Controls.ContentControl.Content%2A>içerik özelliğini devralır ve <xref:System.Object>türündeki <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> özelliğini tanımlar. Bu nedenle, her ikisi de rastgele bir nesne olabilir.  
  
 Aşağıdaki denetimler <xref:System.Windows.Controls.HeaderedContentControl> devralınır ve içerik modelini kullanır:  
  
- <xref:System.Windows.Controls.Expander>  
  
- <xref:System.Windows.Controls.GroupBox>  
  
- <xref:System.Windows.Controls.TabItem>  
  
 Aşağıdaki çizimde iki <xref:System.Windows.Controls.TabItem> nesnesi gösterilmektedir. İlk <xref:System.Windows.Controls.TabItem>, <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> ve <xref:System.Windows.Controls.ContentControl.Content%2A>olarak <xref:System.Windows.UIElement> nesneleri içerir. <xref:System.Windows.Controls.HeaderedContentControl.Header%2A>, <xref:System.Windows.Shapes.Ellipse> ve <xref:System.Windows.Controls.TextBlock>içeren bir <xref:System.Windows.Controls.StackPanel> ayarlanır. <xref:System.Windows.Controls.ContentControl.Content%2A>, <xref:System.Windows.Controls.TextBlock> ve <xref:System.Windows.Controls.Label>içeren bir <xref:System.Windows.Controls.StackPanel> ayarlanır. İkinci <xref:System.Windows.Controls.TabItem>, <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> bir dizeye ve <xref:System.Windows.Controls.ContentControl.Content%2A><xref:System.Windows.Controls.TextBlock>.  
  
 ![Üst bilgi özelliğinde farklı türler kullanan TabControl.](./media/wpf-content-model/control-content-model-tab.png)  
  
 <xref:System.Windows.Controls.TabItem> nesnelerinin nasıl oluşturulacağı hakkında bir örnek için bkz. <xref:System.Windows.Controls.HeaderedContentControl>.  
  
### <a name="controls-that-contain-a-collection-of-arbitrary-objects"></a>Rastgele nesneler koleksiyonu Içeren denetimler  
 <xref:System.Windows.Controls.ItemsControl> sınıfı <xref:System.Windows.Controls.Control> devralır ve dizeler, nesneler veya diğer öğeler gibi birden çok öğe içerebilir. İçerik özellikleri <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> ve <xref:System.Windows.Controls.ItemsControl.Items%2A>. <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>, genellikle <xref:System.Windows.Controls.ItemsControl> bir veri koleksiyonuyla doldurmak için kullanılır. <xref:System.Windows.Controls.ItemsControl>doldurmak için bir koleksiyon kullanmak istemiyorsanız, <xref:System.Windows.Controls.ItemsControl.Items%2A> özelliğini kullanarak öğe ekleyebilirsiniz.  
  
 Aşağıdaki denetimler <xref:System.Windows.Controls.ItemsControl> devralınır ve içerik modelini kullanır:  
  
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
  
 Aşağıdaki çizimde, bu tür öğeleri içeren bir <xref:System.Windows.Controls.ListBox> gösterilmektedir:  
  
- Bir dize.  
  
- A <xref:System.DateTime> nesne.  
  
- A <xref:System.Windows.UIElement>.  
  
- Bir <xref:System.Windows.Shapes.Ellipse> ve <xref:System.Windows.Controls.TextBlock>içeren bir <xref:System.Windows.Controls.Panel>.  
  
 ![Dört tür içerik içeren bir ListBox gösteren ekran görüntüsü.](./media/wpf-content-model/control-content-model-listbox.png)  
  
### <a name="controls-that-contain-a-header-and-a-collection-of-arbitrary-objects"></a>Bir üst bilgi ve rastgele nesneler koleksiyonu içeren denetimler  
 <xref:System.Windows.Controls.HeaderedItemsControl> sınıfı <xref:System.Windows.Controls.ItemsControl> devralır ve dizeler, nesneler veya diğer öğeler ve bir üst bilgi gibi birden çok öğe içerebilir. <xref:System.Windows.Controls.ItemsControl> içerik özelliklerini, <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>ve <xref:System.Windows.Controls.ItemsControl.Items%2A>devralır ve rastgele bir nesne olabilecek <xref:System.Windows.Controls.HeaderedItemsControl.Header%2A> özelliğini tanımlar.  
  
 Aşağıdaki denetimler <xref:System.Windows.Controls.HeaderedItemsControl> devralınır ve içerik modelini kullanır:  
  
- <xref:System.Windows.Controls.MenuItem>  
  
- <xref:System.Windows.Controls.ToolBar>  
  
- <xref:System.Windows.Controls.TreeViewItem>  
  
<a name="classes_that_contain_a_collection_of_uielement_objects"></a>   
## <a name="classes-that-contain-a-collection-of-uielement-objects"></a>UIElement nesnelerinin bir koleksiyonunu Içeren Sınıflar  
 <xref:System.Windows.Controls.Panel> sınıfı, alt <xref:System.Windows.UIElement> nesnelerini konumlandırır ve düzenler. İçerik özelliği <xref:System.Windows.Controls.Panel.Children%2A>.  
  
 Aşağıdaki sınıflar <xref:System.Windows.Controls.Panel> sınıfından devralınır ve onun içerik modelini kullanır:  
  
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
  
 Daha fazla bilgi için bkz. [panellere genel bakış](panels-overview.md).  
  
<a name="classes_that_affects_the_appearance_of_a_uielement"></a>   
## <a name="classes-that-affect-the-appearance-of-a-uielement"></a>UIElement görünümünü etkileyen sınıflar  
 <xref:System.Windows.Controls.Decorator> sınıfı, tek bir alt <xref:System.Windows.UIElement>üzerinde veya çevresinde görsel etkiler uygular. İçerik özelliği <xref:System.Windows.Controls.Decorator.Child%2A>. Aşağıdaki sınıflar <xref:System.Windows.Controls.Decorator> devralınır ve içerik modelini kullanır:  
  
- <xref:System.Windows.Documents.AdornerDecorator>  
  
- <xref:System.Windows.Controls.Border>  
  
- <xref:System.Windows.Controls.Primitives.BulletDecorator>  
  
- <xref:Microsoft.Windows.Themes.ButtonChrome>  
  
- <xref:Microsoft.Windows.Themes.ClassicBorderDecorator>  
  
- <xref:System.Windows.Controls.InkPresenter>  
  
- <xref:Microsoft.Windows.Themes.ListBoxChrome>  
  
- <xref:Microsoft.Windows.Themes.SystemDropShadowChrome>  
  
- <xref:System.Windows.Controls.Viewbox>  
  
 Aşağıdaki çizimde, etrafında bir <xref:System.Windows.Controls.Border> olan (ile donatılmış) bir <xref:System.Windows.Controls.TextBox> gösterilmektedir.  
  
 ![Siyah kenarlıklı metin kutusu](./media/layout-border-around-textbox.png "Layout_Border_around_TextBox")  
Kenarlığı olan TextBlock  
  
<a name="classes_that_provides_visual_feedback_about_a_uielement"></a>   
## <a name="classes-that-provide-visual-feedback-about-a-uielement"></a>UIElement hakkında görsel geri bildirim sağlayan sınıflar  
 <xref:System.Windows.Documents.Adorner> sınıfı bir kullanıcıya görsel ipucu sağlar. Örneğin, öğelere işlevsel işleyiciler eklemek veya bir denetimle ilgili durum bilgilerini sağlamak için bir <xref:System.Windows.Documents.Adorner> kullanın. <xref:System.Windows.Documents.Adorner> sınıfı, kendi donatıcıları oluşturabilmeniz için bir çerçeve sağlar. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], uygulanan hiçbir donatıcıları sağlamıyor. Daha fazla bilgi için bkz. [donatıcıları genel bakış](adorners-overview.md).  
  
<a name="classes_that_enable_users_to_enter_text"></a>   
## <a name="classes-that-enable-users-to-enter-text"></a>Kullanıcıların metin girmesini sağlayan sınıflar  
 WPF, kullanıcıların metin girmesini sağlayan üç birincil denetim sağlar. Her denetim, metni farklı görüntüler. Aşağıdaki tabloda, metin ile ilgili bu üç denetim, metin görüntüleme özellikleri ve denetimin metnini içeren özellikler listelenmiştir.  
  
|Denetim|Metin şöyle görüntülenir|İçerik özelliği|  
|-------------|--------------------------|----------------------|  
|<xref:System.Windows.Controls.TextBox>|Düz metin|<xref:System.Windows.Controls.TextBox.Text%2A>|  
|<xref:System.Windows.Controls.RichTextBox>|Biçimlendirilmiş metin|<xref:System.Windows.Controls.RichTextBox.Document%2A>|  
|<xref:System.Windows.Controls.PasswordBox>|Gizli metin (karakterler maskelenir)|<xref:System.Windows.Controls.PasswordBox.Password%2A>|  
  
<a name="classes_that_display_text"></a>   
## <a name="classes-that-display-your-text"></a>Metninizi görüntüleyen sınıflar  
 Düz veya biçimli metinleri göstermek için birkaç sınıf kullanılabilir. Küçük miktarlarda metin göstermek için <xref:System.Windows.Controls.TextBlock> kullanabilirsiniz. Büyük miktarlarda metin göstermek istiyorsanız <xref:System.Windows.Controls.FlowDocumentReader>, <xref:System.Windows.Controls.FlowDocumentPageViewer>veya <xref:System.Windows.Controls.FlowDocumentScrollViewer> denetimlerini kullanın.  
  
 <xref:System.Windows.Controls.TextBlock> iki içerik özelliği vardır: <xref:System.Windows.Controls.TextBlock.Text%2A> ve <xref:System.Windows.Controls.TextBlock.Inlines%2A>. Tutarlı biçimlendirme kullanan metni göstermek istediğinizde, <xref:System.Windows.Controls.TextBlock.Text%2A> özelliği genellikle en iyi seçimdir. Metnin tamamında farklı biçimlendirme kullanmayı planlıyorsanız <xref:System.Windows.Controls.TextBlock.Inlines%2A> özelliğini kullanın. <xref:System.Windows.Controls.TextBlock.Inlines%2A> özelliği, metnin nasıl biçimlendirileceğini belirten bir <xref:System.Windows.Documents.Inline> nesneleri koleksiyonudur.  
  
 Aşağıdaki tabloda <xref:System.Windows.Controls.FlowDocumentReader>, <xref:System.Windows.Controls.FlowDocumentPageViewer>ve <xref:System.Windows.Controls.FlowDocumentScrollViewer> sınıflarının içerik özelliği listelenmektedir.  
  
|Denetim|İçerik özelliği|İçerik özelliği türü|  
|-------------|----------------------|---------------------------|  
|<xref:System.Windows.Controls.FlowDocumentPageViewer>|Belge|<xref:System.Windows.Documents.IDocumentPaginatorSource>|  
|<xref:System.Windows.Controls.FlowDocumentReader>|Belge|<xref:System.Windows.Documents.FlowDocument>|  
|<xref:System.Windows.Controls.FlowDocumentScrollViewer>|Belge|<xref:System.Windows.Documents.FlowDocument>|  
  
 <xref:System.Windows.Documents.FlowDocument>, <xref:System.Windows.Documents.IDocumentPaginatorSource> arabirimini uygular; Bu nedenle, üç sınıfın hepsi içerik olarak <xref:System.Windows.Documents.FlowDocument> alabilir.  
  
<a name="classes_that_format_text"></a>   
## <a name="classes-that-format-your-text"></a>Metninizi biçimlendirmek için sınıflar  
 <xref:System.Windows.Documents.TextElement> ve ilgili sınıfları metni biçimlendirmeye izin verir. <xref:System.Windows.Documents.TextElement> nesneler <xref:System.Windows.Controls.TextBlock> ve <xref:System.Windows.Documents.FlowDocument> nesnelerinde metin içerir ve biçimlendirir. <xref:System.Windows.Documents.TextElement> nesnelerinin iki birincil türü <xref:System.Windows.Documents.Block> öğeler ve <xref:System.Windows.Documents.Inline> öğelerdir. Bir <xref:System.Windows.Documents.Block> öğesi paragraf veya liste gibi bir metin bloğunu temsil eder. Bir <xref:System.Windows.Documents.Inline> öğesi bir bloğundaki metnin bir bölümünü temsil eder. Birçok <xref:System.Windows.Documents.Inline> sınıfı, uygulandıkları metin için biçimlendirme belirler. Her <xref:System.Windows.Documents.TextElement> kendi içerik modeline sahiptir. Daha fazla bilgi için bkz. [TextElement Içerik modeline genel bakış](../advanced/textelement-content-model-overview.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Gelişmiş](../advanced/index.md)
