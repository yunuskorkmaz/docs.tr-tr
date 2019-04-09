---
title: WPF İçerik Modeli
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
ms.openlocfilehash: 4f866e0366a7781c287b3ebae7b668c2b296a5cc
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59134614"
---
# <a name="wpf-content-model"></a>WPF İçerik Modeli
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] birçok denetimleri ve farklı içerik türlerini görüntülemek için birincil amacı olan denetim-like türleri sağlayan bir sunu platformudur. Hangi denetimi kullanmak için veya türetmek için hangi denetimi belirlemek için belirli bir denetimi en iyi görüntüleyebilirsiniz nesne türlerini anlamanız gerekir.  
  
 İçerik modeli için bu konuda özetlenir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] denetimi ve denetim-like türleri. İçerik modeli, hangi içerik denetimi kullanılabileceğini anlatmaktadır. Bu konu, ayrıca her bir içerik modeli için içerik özellikleri listeler. İçerik özelliği bir nesnenin içeriğini depolamak için kullanılan bir özelliktir.  

<a name="classes_that_contain_arbitrary_content"></a>   
## <a name="classes-that-contain-arbitrary-content"></a>Rasgele içerik içeren sınıflar  
 Bazı denetimler, dize gibi herhangi bir türde bir nesne içerebilir bir <xref:System.DateTime> nesnesi veya bir <xref:System.Windows.UIElement> ek öğeler için diğer bir deyişle bir kapsayıcı. Örneğin, bir <xref:System.Windows.Controls.Button> görüntü ve metin; içerebilir veya <xref:System.Windows.Controls.CheckBox> değerini içerebilir <xref:System.DateTime.Now%2A?displayProperty=nameWithType>.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] rasgele içerik içerebilir dört sınıfları içerir. Devralma sınıfları aşağıdaki tabloda listelenmektedir <xref:System.Windows.Controls.Control>.  
  
|Rasgele içerik içeren sınıfı|İçerik|  
|-------------------------------------------|-------------|  
|<xref:System.Windows.Controls.ContentControl>|Tek bir rasgele nesne.|  
|<xref:System.Windows.Controls.HeaderedContentControl>|Üstbilgi ve ikisi için de rasgele nesne olan tek bir öğe.|  
|<xref:System.Windows.Controls.ItemsControl>|Rastgele nesneleri koleksiyonu.|  
|<xref:System.Windows.Controls.HeaderedItemsControl>|Üstbilgi ve tümü isteğe bağlı nesneleri olan öğelerin bir koleksiyonu.|  
  
 Bu sınıflardan devralmasına denetimleri, aynı içerik türünü içerir ve içerik aynı şekilde davranma. Aşağıdaki resimde, bir görüntü içeren her bir içerik modeli ve bazı metinler denetiminden gösterilmektedir:  
  
 ![İçerik modeli her birinden dört farklı denetim gösteren ekran görüntüsü.](./media/wpf-content-model/control-content-model-image-text.png)  
  
### <a name="controls-that-contain-a-single-arbitrary-object"></a>Tek bir rasgele nesne içeren denetimler  
 <xref:System.Windows.Controls.ContentControl> Sınıfı, rastgele içeriği tek bir parçasını içerir. İçerik özelliği olan <xref:System.Windows.Controls.ContentControl.Content%2A>. Aşağıdaki denetimler devralınacak <xref:System.Windows.Controls.ContentControl> ve kendi içerik modelini kullanın:  
  
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
  
 Aşağıdaki resimde dört düğme gösterilmektedir <xref:System.Windows.Controls.ContentControl.Content%2A> bir dize olarak ayarlanmış bir <xref:System.DateTime> nesnesi bir <xref:System.Windows.Shapes.Rectangle>ve <xref:System.Windows.Controls.Panel> içeren bir <xref:System.Windows.Shapes.Ellipse> ve <xref:System.Windows.Controls.TextBlock>:  
  
 ![Farklı içerik türleri ile dört düğme gösteren ekran görüntüsü.](./media/wpf-content-model/control-content-model-buttons.png)  
  
 Ayarlama örneği için <xref:System.Windows.Controls.ContentControl.Content%2A> özelliği bkz <xref:System.Windows.Controls.ContentControl>.  
  
### <a name="controls-that-contain-a-header-and-a-single-arbitrary-object"></a>Üst bilgi ve tek bir rasgele nesne içeren denetimler  
 <xref:System.Windows.Controls.HeaderedContentControl> Sınıfının devraldığı <xref:System.Windows.Controls.ContentControl> ve bir üst bilgisiyle içeriğini görüntüler. İçerik özelliği devralan <xref:System.Windows.Controls.ContentControl.Content%2A>, gelen <xref:System.Windows.Controls.ContentControl> tanımlar <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> tür özelliği <xref:System.Object>; bu nedenle, her ikisi de rastgele bir nesne olabilir.  
  
 Aşağıdaki denetimler devralınacak <xref:System.Windows.Controls.HeaderedContentControl> ve kendi içerik modelini kullanın:  
  
-   <xref:System.Windows.Controls.Expander>  
  
-   <xref:System.Windows.Controls.GroupBox>  
  
-   <xref:System.Windows.Controls.TabItem>  
  
 Aşağıdaki iki resimde <xref:System.Windows.Controls.TabItem> nesneleri. İlk <xref:System.Windows.Controls.TabItem> sahip <xref:System.Windows.UIElement> olarak nesneleri <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> ve <xref:System.Windows.Controls.ContentControl.Content%2A>. <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> Ayarlanmış bir <xref:System.Windows.Controls.StackPanel> içeren bir <xref:System.Windows.Shapes.Ellipse> ve <xref:System.Windows.Controls.TextBlock>. <xref:System.Windows.Controls.ContentControl.Content%2A> Ayarlanmış bir <xref:System.Windows.Controls.StackPanel> içeren bir <xref:System.Windows.Controls.TextBlock> ve <xref:System.Windows.Controls.Label>. İkinci <xref:System.Windows.Controls.TabItem> cinsinden bir dize olan <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> ve <xref:System.Windows.Controls.TextBlock> içinde <xref:System.Windows.Controls.ContentControl.Content%2A>.  
  
 ![Farklı üst bilgi özelliği kullanan TabControl.](./media/wpf-content-model/control-content-model-tab.png)  
  
 Nasıl oluşturulacağına dair bir örnek <xref:System.Windows.Controls.TabItem> nesneleri bkz <xref:System.Windows.Controls.HeaderedContentControl>.  
  
### <a name="controls-that-contain-a-collection-of-arbitrary-objects"></a>Rastgele nesnelerinin bir koleksiyonunu içeren denetimler  
 <xref:System.Windows.Controls.ItemsControl> Sınıfının devraldığı <xref:System.Windows.Controls.Control> ve dizeler, nesneler veya diğer öğeleri gibi birden çok öğe içerebilir. İçerik özellikleri olan <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> ve <xref:System.Windows.Controls.ItemsControl.Items%2A>. <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> genellikle doldurmak için kullanılan <xref:System.Windows.Controls.ItemsControl> veri koleksiyonu. Doldurmak için bir koleksiyon kullanmak istemiyorsanız <xref:System.Windows.Controls.ItemsControl>, kullanarak öğeleri ekleyebilirsiniz <xref:System.Windows.Controls.ItemsControl.Items%2A> özelliği.  
  
 Aşağıdaki denetimler devralınacak <xref:System.Windows.Controls.ItemsControl> ve kendi içerik modelini kullanın:  
  
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
  
-   A <xref:System.DateTime> nesne.  
  
-   A <xref:System.Windows.UIElement>.  
  
-   A <xref:System.Windows.Controls.Panel> içeren bir <xref:System.Windows.Shapes.Ellipse> ve <xref:System.Windows.Controls.TextBlock>.  
  
 ![Dört tür içerikle ListBox gösteren ekran görüntüsü.](./media/wpf-content-model/control-content-model-listbox.png)  
  
### <a name="controls-that-contain-a-header-and-a-collection-of-arbitrary-objects"></a>Üst bilgi ve rastgele nesnelerinin bir koleksiyonunu içeren denetimler  
 <xref:System.Windows.Controls.HeaderedItemsControl> Sınıfının devraldığı <xref:System.Windows.Controls.ItemsControl> ve dizeler, nesneler veya diğer öğeleri ve bir üst bilgisi gibi birden çok öğe içerebilir. Devralır <xref:System.Windows.Controls.ItemsControl> içerik özellikleri, <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>, ve <xref:System.Windows.Controls.ItemsControl.Items%2A>, ve tanımladığı <xref:System.Windows.Controls.HeaderedItemsControl.Header%2A> özelliği rastgele bir nesne olabilir.  
  
 Aşağıdaki denetimler devralınacak <xref:System.Windows.Controls.HeaderedItemsControl> ve kendi içerik modelini kullanın:  
  
-   <xref:System.Windows.Controls.MenuItem>  
  
-   <xref:System.Windows.Controls.ToolBar>  
  
-   <xref:System.Windows.Controls.TreeViewItem>  
  
<a name="classes_that_contain_a_collection_of_uielement_objects"></a>   
## <a name="classes-that-contain-a-collection-of-uielement-objects"></a>UIElement nesnelerinin bir koleksiyonunu içeren sınıflar  
 <xref:System.Windows.Controls.Panel> Sınıfı yerleştirir ve alt düzenler <xref:System.Windows.UIElement> nesneleri. İçerik özelliği olan <xref:System.Windows.Controls.Panel.Children%2A>.  
  
 Aşağıdaki sınıflar devralınacak <xref:System.Windows.Controls.Panel> sınıfı ve kendi içerik modelini kullanın:  
  
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
  
 Daha fazla bilgi için [panellere genel bakış](panels-overview.md).  
  
<a name="classes_that_affects_the_appearance_of_a_uielement"></a>   
## <a name="classes-that-affect-the-appearance-of-a-uielement"></a>UIElement'i görünümünü etkileyen sınıfları  
 <xref:System.Windows.Controls.Decorator> Görsel efektler üzerine veya çevresine tek bir alt sınıfı uygulanır <xref:System.Windows.UIElement>. İçerik özelliği olan <xref:System.Windows.Controls.Decorator.Child%2A>. Aşağıdaki sınıflar devralınacak <xref:System.Windows.Controls.Decorator> ve kendi içerik modelini kullanın:  
  
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
  
 ![TextBox siyah kenarlığa sahip](./media/layout-border-around-textbox.png "Layout_Border_around_TextBox")  
Bir kenarlığa sahip bir TextBlock  
  
<a name="classes_that_provides_visual_feedback_about_a_uielement"></a>   
## <a name="classes-that-provide-visual-feedback-about-a-uielement"></a>UIElement'i hakkında görsel geri bildirim sağlayan sınıflar  
 <xref:System.Windows.Documents.Adorner> Sınıfı, bir kullanıcı için görsel ipuçları sağlar. Örneğin, bir <xref:System.Windows.Documents.Adorner> işlevsel tanıtıcıları öğeleri ekleyin ya da bir denetimi hakkındaki durum bilgilerini sağlamak için. <xref:System.Windows.Documents.Adorner> Sınıf kendi donatıcıları oluşturabilmesi bir çerçeve sağlar. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulanan tüm donatıcıları sağlamaz. Daha fazla bilgi için [Donatıcılara Genel Bakış](adorners-overview.md).  
  
<a name="classes_that_enable_users_to_enter_text"></a>   
## <a name="classes-that-enable-users-to-enter-text"></a>Kullanıcıların metin girmesine olanak tanıyan sınıflar  
 WPF metin girmesini sağlayan üç birincil denetim sağlar. Her denetim farklı metni görüntüler. Aşağıdaki tabloda bu üç metin ile ilgili denetimleri, metin ve denetimin metni içeren özelliklerini görüntülediğinizde yeteneklerini listeler.  
  
|Denetim|Metin olarak görüntülenir|İçerik özelliği|  
|-------------|--------------------------|----------------------|  
|<xref:System.Windows.Controls.TextBox>|Düz metin|<xref:System.Windows.Controls.TextBox.Text%2A>|  
|<xref:System.Windows.Controls.RichTextBox>|Biçimlendirilmiş metin|<xref:System.Windows.Controls.RichTextBox.Document%2A>|  
|<xref:System.Windows.Controls.PasswordBox>|Gizli metin (karakterler maskelenir)|<xref:System.Windows.Controls.PasswordBox.Password%2A>|  
  
<a name="classes_that_display_text"></a>   
## <a name="classes-that-display-your-text"></a>Metninizi görüntüleme sınıfları  
 Düz veya biçimlendirilmiş metni görüntülemek için çeşitli sınıflar kullanılabilir. Kullanabileceğiniz <xref:System.Windows.Controls.TextBlock> küçük miktarda metni görüntülemek için. Büyük miktarda metni görüntülemek istiyorsanız, kullanın <xref:System.Windows.Controls.FlowDocumentReader>, <xref:System.Windows.Controls.FlowDocumentPageViewer>, veya <xref:System.Windows.Controls.FlowDocumentScrollViewer> kontrol eder.  
  
 <xref:System.Windows.Controls.TextBlock> İçerik iki özelliğe sahiptir: <xref:System.Windows.Controls.TextBlock.Text%2A> ve <xref:System.Windows.Controls.TextBlock.Inlines%2A>. Tutarlı biçimlendirme kullanan metni görüntülemek istediğinizde <xref:System.Windows.Controls.TextBlock.Text%2A> özelliği olan genellikle en iyi seçimdir. Farklı biçimlendirme boyunda metinde kullanmayı planlıyorsanız, kullanmak <xref:System.Windows.Controls.TextBlock.Inlines%2A> özelliği. <xref:System.Windows.Controls.TextBlock.Inlines%2A> Özelliktir koleksiyonu <xref:System.Windows.Documents.Inline> metnin nasıl biçimlendirileceğini belirten nesneleri.  
  
 İçerik özelliği için aşağıdaki tabloda <xref:System.Windows.Controls.FlowDocumentReader>, <xref:System.Windows.Controls.FlowDocumentPageViewer>, ve <xref:System.Windows.Controls.FlowDocumentScrollViewer> sınıfları.  
  
|Denetim|İçerik özelliği|İçerik özelliği türü|  
|-------------|----------------------|---------------------------|  
|<xref:System.Windows.Controls.FlowDocumentPageViewer>|Belge|<xref:System.Windows.Documents.IDocumentPaginatorSource>|  
|<xref:System.Windows.Controls.FlowDocumentReader>|Belge|<xref:System.Windows.Documents.FlowDocument>|  
|<xref:System.Windows.Controls.FlowDocumentScrollViewer>|Belge|<xref:System.Windows.Documents.FlowDocument>|  
  
 <xref:System.Windows.Documents.FlowDocument> Uygulayan <xref:System.Windows.Documents.IDocumentPaginatorSource> arabirim; bu nedenle, tüm üç sınıf sürebilir bir <xref:System.Windows.Documents.FlowDocument> içeriği.  
  
<a name="classes_that_format_text"></a>   
## <a name="classes-that-format-your-text"></a>Metninizi biçimlendirmek sınıfları  
 <xref:System.Windows.Documents.TextElement> ve ilişkili sınıflarının metni biçimlendirmek izin verir. <xref:System.Windows.Documents.TextElement> nesneler içerir ve metni biçimlendirebilir <xref:System.Windows.Controls.TextBlock> ve <xref:System.Windows.Documents.FlowDocument> nesneleri. İki birincil türlerini <xref:System.Windows.Documents.TextElement> nesneler <xref:System.Windows.Documents.Block> öğeleri ve <xref:System.Windows.Documents.Inline> öğeleri. A <xref:System.Windows.Documents.Block> öğesi, paragraf ya da liste gibi bir metin bloğu temsil eder. Bir <xref:System.Windows.Documents.Inline> öğesi bir blok içinde metnin bir bölümünü temsil eder. Birçok <xref:System.Windows.Documents.Inline> sınıfları için bunlar uygulandığı metin biçimlendirme belirtin. Her <xref:System.Windows.Documents.TextElement> kendi içerik modeli vardır. Daha fazla bilgi için [TextElement içerik modeline genel bakış](../advanced/textelement-content-model-overview.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Gelişmiş](../advanced/index.md)
