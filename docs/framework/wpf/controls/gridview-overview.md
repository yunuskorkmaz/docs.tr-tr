---
title: GridView Genel Bakışı
ms.date: 03/30/2017
helpviewer_keywords:
- GridView view mode [WPF]
- ListView controls [WPF], GridView view mode
- controls [WPF], ListView
ms.assetid: b2d02267-32b3-40ce-8e9f-06972d8749d9
ms.openlocfilehash: 6da556296679de1161f609a7731c6fbf14e94730
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69966478"
---
# <a name="gridview-overview"></a>GridView Genel Bakışı
<xref:System.Windows.Controls.GridView>Görünüm modu, bir <xref:System.Windows.Controls.ListView> denetim için görünüm modlarından biridir. <xref:System.Windows.Controls.GridView> Sınıfı ve destekleyici sınıfları, sizin ve kullanıcılarınızın, genellikle düğmeleri etkileşimli sütun başlıkları olarak kullanan bir tablodaki öğe koleksiyonlarını görüntülemesini sağlar. Bu konu <xref:System.Windows.Controls.GridView> sınıfı tanıtır ve kullanımını özetler.  

<a name="DefiningaListViewthatusesGridViewView"></a>   
## <a name="what-is-a-gridview-view"></a>GridView görünümü nedir?  
 Görünüm <xref:System.Windows.Controls.GridView> modu, veri alanlarını sütunlara bağlayarak ve alanı tanımlamak için bir sütun üst bilgisi görüntüleyerek veri öğelerinin bir listesini görüntüler. Varsayılan <xref:System.Windows.Controls.GridView> stil düğmeleri sütun başlıkları olarak uygular. Sütun başlıkları için düğmeleri kullanarak, önemli Kullanıcı etkileşimi özelliklerini uygulayabilirsiniz; Örneğin, kullanıcılar verileri belirli bir sütunun içeriğine göre sıralamak <xref:System.Windows.Controls.GridView> için sütun başlığına tıklabilirler.  
  
> [!NOTE]
> Sütun başlıkları için <xref:System.Windows.Controls.GridView> kullanılan düğme denetimleri öğesinden <xref:System.Windows.Controls.Primitives.ButtonBase>türetilir.  
  
 Aşağıdaki çizimde bir <xref:System.Windows.Controls.GridView> <xref:System.Windows.Controls.ListView> içerik görünümü gösterilmektedir.  
    
 ![ListView içeriğinin GridView görünümünü gösteren ekran görüntüsü.](./media/gridview-overview/styled-listview-content.png)  
  
 <xref:System.Windows.Controls.GridView>sütunlar nesneler tarafından <xref:System.Windows.Controls.GridViewColumn> temsil edilir ve içeriğe otomatik olarak boyutlenebilir. İsteğe bağlı olarak, açıkça belirli bir <xref:System.Windows.Controls.GridViewColumn> genişlik olarak ayarlayabilirsiniz. Kavrayıcıyı sütun başlıkları arasında sürükleyerek sütunları yeniden boyutlandırabilirsiniz. Ayrıca, bu işlev yerleşik <xref:System.Windows.Controls.GridView>olarak bulunduğu için sütunları dinamik olarak ekleyebilir, kaldırabilir, değiştirebilir ve yeniden sıralayabilirsiniz. Ancak, <xref:System.Windows.Controls.GridView> görüntülediği veriler doğrudan güncelleştirilemez.  
  
 Aşağıdaki örnek, çalışan verilerini görüntüleyen bir <xref:System.Windows.Controls.GridView> 'nın nasıl tanımlanacağını göstermektedir. Bu örnekte, öğesini <xref:System.Windows.Controls.ListView> `EmployeeInfoDataSource` olarak <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>tanımlar. İçerik <xref:System.Windows.Controls.GridViewColumn.DisplayMemberBinding%2A> bağlama<xref:System.Windows.Controls.GridViewColumn>özelliğinin özellik tanımları verikategorilerine.`EmployeeInfoDataSource`  
  
 [!code-xaml[ListViewCode#ListViewEmployee](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewCode/CSharp/Window1.xaml#listviewemployee)]  
  
 Aşağıdaki çizimde, önceki örneğin oluşturduğu tablo gösterilmektedir. GridView denetimi bir ıtemısource nesnesinden verileri görüntüler:
    
 ![GridView çıkışıyla bir ListView gösteren ekran görüntüsü.](./media/gridview-overview/listview-gridview-output.jpg)  
  
<a name="GridViewLayoutandStyle"></a>   
## <a name="gridview-layout-and-style"></a>GridView düzeni ve stili  
 Sütun hücrelerinin ve sütununun sütun üstbilgisinin <xref:System.Windows.Controls.GridViewColumn> genişliği aynı. Varsayılan olarak, her sütun genişliğini içeriğine uyacak şekilde boyutlandırır. İsteğe bağlı olarak, bir sütunu sabit genişliğe ayarlayabilirsiniz.  
  
 İlgili veri içeriği yatay satırlarda görüntülenir. Örneğin, önceki çizimde, her çalışanın soyadı, adı ve KIMLIK numarası, yatay bir satırda göründükleri için bir küme olarak görüntülenir.  
  
<a name="DefiningandStylingColumnsinaGridView"></a>   
### <a name="defining-and-styling-columns-in-a-gridview"></a>GridView 'da sütunları tanımlama ve Stillendirme  
 İçinde <xref:System.Windows.Controls.GridViewColumn>görüntülenecek veri alanını tanımlarken,, veya <xref:System.Windows.Controls.GridViewColumn.CellTemplateSelector%2A> özelliklerini <xref:System.Windows.Controls.GridViewColumn.DisplayMemberBinding%2A>kullanın <xref:System.Windows.Controls.GridViewColumn.CellTemplate%2A>. <xref:System.Windows.Controls.GridViewColumn.DisplayMemberBinding%2A> Özelliği, şablon özelliklerinden herhangi birinin üzerine gelir.  
  
 İçeriğinin bir sütununda <xref:System.Windows.Controls.GridView>hizalamasını belirtmek için bir <xref:System.Windows.Controls.GridViewColumn.CellTemplate%2A>tanımlayın. <xref:System.Windows.Controls.Control.HorizontalContentAlignment%2A> <xref:System.Windows.Controls.Control.VerticalContentAlignment%2A> Kullanılarak görüntüleneniçerik<xref:System.Windows.Controls.ListView> için ve özelliklerini kullanmayın. <xref:System.Windows.Controls.GridView>  
  
 Sütun başlıkları için şablon ve stil özelliklerini belirtmek üzere,, ve <xref:System.Windows.Controls.GridView> <xref:System.Windows.Controls.GridViewColumnHeader> sınıflarını <xref:System.Windows.Controls.GridViewColumn>kullanın. Daha fazla bilgi için bkz. [GridView sütun üst bilgi stilleri ve şablonlara genel bakış](gridview-column-header-styles-and-templates-overview.md).  
  
<a name="AddingVisualElementstoaGridViewView"></a>   
### <a name="adding-visual-elements-to-a-gridview"></a>GridView 'a görsel öğe ekleme  
 <xref:System.Windows.Controls.CheckBox> <xref:System.Windows.Controls.GridView> Ve denetimlerigibigörselöğeleribirgörünümmodunaeklemekiçinşablonlarveyastillerkullanın.<xref:System.Windows.Controls.Button>  
  
 Bir görsel öğeyi bir veri öğesi olarak açıkça tanımlarsanız, bir <xref:System.Windows.Controls.GridView>içinde yalnızca bir kez görünebilir. Bu sınırlama, bir öğenin yalnızca bir üst öğesi olabileceğinden ve bu nedenle görsel ağaçta yalnızca bir kez görünebildiğinden oluşur.  
  
<a name="StylingRowsinaGridViewView"></a>   
### <a name="styling-rows-in-a-gridview"></a>GridView 'da satır Stillendirme  
 Ve satırlarını biçimlendirmek <xref:System.Windows.Controls.GridViewHeaderRowPresenter> ve<xref:System.Windows.Controls.GridView>göstermek için ve sınıflarını kullanın. <xref:System.Windows.Controls.GridViewRowPresenter> Bir <xref:System.Windows.Controls.GridView> görünüm modundaki satırların nasıl Stillendirilmesi hakkında bir örnek için, bkz. [GridView Uygulayan ListView içindeki bir satırı stilme](how-to-style-a-row-in-a-listview-that-implements-a-gridview.md).  
  
<a name="AlignmentIssuesWhenUsingItemContainerStyle"></a>   
### <a name="alignment-issues-when-you-use-itemcontainerstyle"></a>ItemContainerStyle kullandığınızda hizalama sorunları  
 Sütun üstbilgileri ve hücreler arasındaki hizalama sorunlarını engellemek için, bir özellik ayarlamayın veya içindeki <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A>bir öğenin genişliğini etkileyen bir şablon belirtmeyin. Örneğin <xref:System.Windows.FrameworkElement.Margin%2A> , özelliğini ayarlamayın veya bir <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> <xref:System.Windows.Controls.ControlTemplate> denetimde<xref:System.Windows.Controls.ListView> tanımlı bir <xref:System.Windows.Controls.CheckBox> öğesine ekleyen bir öğesini belirtin. Bunun yerine, bir <xref:System.Windows.Controls.GridView> görünüm modunu tanımlayan sınıflarda doğrudan sütun genişliğini etkileyen özellikleri ve şablonları belirtin.  
  
 Örneğin <xref:System.Windows.Controls.CheckBox> , <xref:System.Windows.Controls.GridView> <xref:System.Windows.DataTemplate> <xref:System.Windows.DataTemplate> görüntülememodundaki<xref:System.Windows.Controls.GridViewColumn.CellTemplate%2A> satırlara bir eklemek için öğesini öğesineekleyinvesonraözelliğibuolarakayarlayın.<xref:System.Windows.Controls.CheckBox>  
  
<a name="InteractingwithaGridViewControl"></a>   
## <a name="user-interactions-with-a-gridview"></a>GridView ile kullanıcı etkileşimleri  
 Uygulamanızda bir <xref:System.Windows.Controls.GridView> kullandığınızda, kullanıcılar ile etkileşime geçebilir ve biçimlendirmesini <xref:System.Windows.Controls.GridView>değiştirebilir. Örneğin, kullanıcılar sütunları yeniden sıralayabilir, bir sütunu yeniden boyutlandırabilir, tablodaki öğeleri seçebilir ve içeriği kaydırabilirler. Ayrıca, bir Kullanıcı sütun üst bilgisi düğmesine tıkladığında yanıt veren bir olay işleyicisi tanımlayabilirsiniz. Olay işleyicisi, <xref:System.Windows.Controls.GridView> bir sütunun içeriğine göre görüntülenen verileri sıralama gibi işlemler gerçekleştirebilir.  
  
 Aşağıdaki liste, Kullanıcı etkileşimi için kullanmanın <xref:System.Windows.Controls.GridView> yeteneklerini daha ayrıntılı bir şekilde anlatmaktadır:  
  
- **Sürükle ve bırak yöntemini kullanarak sütunları yeniden sıralayın.**  
  
     Kullanıcılar bir <xref:System.Windows.Controls.GridView> sütun başlığı üzerindeyken sol fare düğmesine basarak ve sonra bu sütunu yeni bir konuma sürükleyerek, içindeki sütunları yeniden sıralayabilir. Kullanıcı sütun başlığını sürüklediğinde, başlığın kayan bir sürümü ve sütunun ekleneceği yeri gösteren düz bir siyah çizgi görüntülenir.  
  
     Bir üstbilginin kayan sürümünün varsayılan stilini değiştirmek <xref:System.Windows.Controls.ControlTemplate> istiyorsanız, <xref:System.Windows.Controls.GridViewColumnHeader.Role%2A> özelliği olarak <xref:System.Windows.Controls.GridViewColumnHeaderRole.Floating>ayarlandığında tetiklenen bir <xref:System.Windows.Controls.GridViewColumnHeader> tür için bir seçin. Daha fazla bilgi için bkz. [sürüklenen GridView sütun üst bilgisi Için stil oluşturma](how-to-create-a-style-for-a-dragged-gridview-column-header.md).  
  
- **Bir sütunu içeriğine göre yeniden boyutlandırın.**  
  
     Kullanıcılar bir sütunu içeriğe sığacak şekilde yeniden boyutlandırmak için bir sütun üst bilgisinin sağındaki kavrayıcıyı çift tıklayabilirler.  
  
    > [!NOTE]
    > <xref:System.Windows.Controls.GridViewColumn.Width%2A> Özelliğini aynı etkiyi oluşturmak için olarak `Double.NaN` ayarlayabilirsiniz.  
  
- **Satır öğelerini seçin.**  
  
     Kullanıcılar bir veya daha fazla öğeyi bir <xref:System.Windows.Controls.GridView>veya daha fazla seçim yapabilir.  
  
     Seçili bir öğenin öğesini değiştirmek <xref:System.Windows.Style> istiyorsanız, bkz. [ListView içindeki seçili öğelere stil eklemek için Tetikleyicileri kullanma](how-to-use-triggers-to-style-selected-items-in-a-listview.md).  
  
- **Başlangıçta ekranda görünmeyen içeriği görüntülemek için kaydırın.**  
  
     Boyutu <xref:System.Windows.Controls.GridView> tüm öğelerin görüntülenmesi için yeterince büyük değilse, kullanıcılar bir denetim tarafından sunulan kaydırma çubuklarını kullanarak yatay veya dikey bir <xref:System.Windows.Controls.ScrollViewer> şekilde kaydırabilirler. Tüm içerik belirli bir yönde görünür durumdaysa, gizli olur.<xref:System.Windows.Controls.Primitives.ScrollBar> Sütun başlıkları dikey bir kaydırma çubuğuyla kaydırılmaz, ancak yatay olarak kaydırılmaz.  
  
- **Sütun başlığı düğmelerine tıklayarak sütunlarla etkileşime geçin.**  
  
     Kullanıcılar bir sütun üst bilgisi düğmesine tıkladıklarında, bir sıralama algoritması sağladıysanız sütunda görüntülenen verileri sıralabilirler.  
  
     Sıralama algoritması gibi işlevler <xref:System.Windows.Controls.Primitives.ButtonBase.Click> sağlamak için sütun üst bilgisi düğmelerinin olayını işleyebilirsiniz. Tek bir sütun <xref:System.Windows.Controls.Primitives.ButtonBase.Click> üst bilgisinin olayını işlemek için <xref:System.Windows.Controls.GridViewColumnHeader>üzerinde bir olay işleyicisi ayarlayın. Tüm sütun başlıkları için <xref:System.Windows.Controls.Primitives.ButtonBase.Click> olayı işleyen bir olay işleyicisi ayarlamak için, <xref:System.Windows.Controls.ListView> denetimde işleyiciyi ayarlayın.  
  
<a name="Obtaining_Other_Custom_Views"></a>   
## <a name="obtaining-other-custom-views"></a>Diğer özel görünümleri edinme  
 <xref:System.Windows.Controls.ViewBase> <xref:System.Windows.Controls.ListView> Soyut sınıftan türetilmiş sınıf,sınıfiçinolası<xref:System.Windows.Controls.GridView> görünüm modlarından yalnızca biridir. <xref:System.Windows.Controls.ViewBase> Sınıfından türeterek için <xref:System.Windows.Controls.ListView> başka özel görünümler oluşturabilirsiniz. Özel görünüm moduna bir örnek için bkz. [ListView Için özel görünüm modu oluşturma](how-to-create-a-custom-view-mode-for-a-listview.md).  
  
<a name="GridViewSupportingClasses"></a>   
## <a name="gridview-supporting-classes"></a>GridView destekleme sınıfları  
 Aşağıdaki sınıflar <xref:System.Windows.Controls.GridView> görünüm modunu destekler.  
  
- <xref:System.Windows.Controls.GridViewColumn>  
  
- <xref:System.Windows.Controls.GridViewColumnHeader>  
  
- <xref:System.Windows.Controls.GridViewRowPresenter>  
  
- <xref:System.Windows.Controls.GridViewHeaderRowPresenter>  
  
- <xref:System.Windows.Controls.GridViewColumnCollection>  
  
- <xref:System.Windows.Controls.GridViewColumnHeaderRole>  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Controls.ListView>
- <xref:System.Windows.Controls.ListViewItem>
- <xref:System.Windows.Controls.GridViewColumn>
- <xref:System.Windows.Controls.GridViewColumnHeader>
- <xref:System.Windows.Controls.GridViewRowPresenter>
- <xref:System.Windows.Controls.GridViewHeaderRowPresenter>
- <xref:System.Windows.Controls.ViewBase>
- [ListView Genel Bakış](listview-overview.md)
- [Üst Bilgiye Tıklandığında GridView Sütununu Sıralama](how-to-sort-a-gridview-column-when-a-header-is-clicked.md)
- [Nasıl Yapılır Konuları](listview-how-to-topics.md)
