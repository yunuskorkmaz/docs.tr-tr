---
title: GridView Genel Bakışı
ms.date: 03/30/2017
helpviewer_keywords:
- GridView view mode [WPF]
- ListView controls [WPF], GridView view mode
- controls [WPF], ListView
ms.assetid: b2d02267-32b3-40ce-8e9f-06972d8749d9
ms.openlocfilehash: 776897d490b2748e240cf7b9a4ea21364284c4c4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33557688"
---
# <a name="gridview-overview"></a>GridView Genel Bakışı
<xref:System.Windows.Controls.GridView> Görünüm modu için görüntüleme modlarından biridir bir <xref:System.Windows.Controls.ListView> denetim. <xref:System.Windows.Controls.GridView> Sınıfı ve bunun destekleyici sınıfları siz ve kullanıcılarınız öğesi, genellikle düğmeleri etkileşimli sütun üst bilgileri olarak kullanan bir tabloda koleksiyonları görüntülemek etkinleştirin. Bu konu tanıtır <xref:System.Windows.Controls.GridView> sınıfı ve kullanımını özetler.  
  
  
  
<a name="DefiningaListViewthatusesGridViewView"></a>   
## <a name="what-is-a-gridview-view"></a>GridView Görünüm nedir?  
 <xref:System.Windows.Controls.GridView> Görünüm modu sütunlara veri alanları bağlama ve alan tanımlamak için bir sütun başlığını göstererek veri öğelerinin bir listesini görüntüler. Varsayılan <xref:System.Windows.Controls.GridView> stil düğmeleri sütun başlığı olarak uygular. Sütun üstbilgileri düğmelerini kullanarak önemli kullanıcı etkileşimi yeteneklerini uygulayabilirsiniz; Örneğin, kullanıcılar sıralamak için sütun başlığını tıklatabilir <xref:System.Windows.Controls.GridView> verileri belirli bir sütunun içeriğine göre.  
  
> [!NOTE]
>  Düğme denetleyen <xref:System.Windows.Controls.GridView> sütun üstbilgilerini türetilir <xref:System.Windows.Controls.Primitives.ButtonBase>.  
  
 Aşağıdaki çizimde gösterildiği bir <xref:System.Windows.Controls.GridView> görünümünü <xref:System.Windows.Controls.ListView> içeriği.  
  
 **ListView içeriğinin GridView görünümü**  
  
 ![ListView stilde](../../../../docs/framework/wpf/controls/media/styledlistview.PNG "StyledListView")  
  
 <xref:System.Windows.Controls.GridView> sütunları temsil ettiği <xref:System.Windows.Controls.GridViewColumn> kendi içeriğinin boyutunu otomatik olarak nesneleri. İsteğe bağlı olarak, açıkça ayarlayabileceğiniz bir <xref:System.Windows.Controls.GridViewColumn> belirli bir genişliğe. Sütun üstbilgileri arasında kavrayıcının sürükleyerek sütunları yeniden boyutlandırabilirsiniz. Ayrıca dinamik olarak ekleyebilir, Kaldır, Değiştir ve bu işlev yerleşik olduğundan sütunları yeniden sıralama <xref:System.Windows.Controls.GridView>. Ancak, <xref:System.Windows.Controls.GridView> görüntülediği veriyi doğrudan güncelleştiremez.  
  
 Aşağıdaki örnekte nasıl tanımlanacağı gösterilmektedir bir <xref:System.Windows.Controls.GridView> çalışan verilerini görüntüler. Bu örnekte, <xref:System.Windows.Controls.ListView> tanımlar `EmployeeInfoDataSource` olarak <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>. Özellik tanımları <xref:System.Windows.Controls.GridViewColumn.DisplayMemberBinding%2A> bağlamak <xref:System.Windows.Controls.GridViewColumn> içerik `EmployeeInfoDataSource` veri kategorilerini.  
  
 [!code-xaml[ListViewCode#ListViewEmployee](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewCode/CSharp/Window1.xaml#listviewemployee)]  
  
 Aşağıdaki çizimde, önceki örnekte oluşturduğu tablo gösterir.  
  
 **Bir ItemsSource verileri görüntüleyen GridView**  
  
 ![GridView çıkışıyla ListView](../../../../docs/framework/wpf/controls/media/listviewgridview.JPG "ListViewGridView")  
  
<a name="GridViewLayoutandStyle"></a>   
## <a name="gridview-layout-and-style"></a>GridView düzenini ve stili  
 Sütun hücreleri ve sütun başlığı bir <xref:System.Windows.Controls.GridViewColumn> aynı genişliğe sahiptir. Varsayılan olarak, her sütunun genişliği içeriğinin sığması için boyutları. İsteğe bağlı olarak bir sütun için sabit genişlikte ayarlayabilirsiniz.  
  
 İlgili veri içeriğini yatay satır görüntüler. Yatay bir satırda göründüğünden Örneğin, önceki çizimde, her çalışanın soyadı, ad ve kimlik numarasını bir küme olarak görüntülenir.  
  
<a name="DefiningandStylingColumnsinaGridView"></a>   
### <a name="defining-and-styling-columns-in-a-gridview"></a>Tanımlama ve sütunları bir GridView stil oluşturma  
 Görüntülenecek veri alanı tanımlarken bir <xref:System.Windows.Controls.GridViewColumn>, kullanın <xref:System.Windows.Controls.GridViewColumn.DisplayMemberBinding%2A>, <xref:System.Windows.Controls.GridViewColumn.CellTemplate%2A>, veya <xref:System.Windows.Controls.GridViewColumn.CellTemplateSelector%2A> özellikleri. <xref:System.Windows.Controls.GridViewColumn.DisplayMemberBinding%2A> Özelliği ya da şablon özelliklerinin öncelik alır.  
  
 İçerik hizalamasını sütununda belirtmek için bir <xref:System.Windows.Controls.GridView>, tanımlayan bir <xref:System.Windows.Controls.GridViewColumn.CellTemplate%2A>. Kullanmayın <xref:System.Windows.Controls.Control.HorizontalContentAlignment%2A> ve <xref:System.Windows.Controls.Control.VerticalContentAlignment%2A> özelliklerini <xref:System.Windows.Controls.ListView> kullanılarak görüntülenen içeriği bir <xref:System.Windows.Controls.GridView>.  
  
 Sütun üstbilgileri şablon ve stil özelliklerini belirtmek için kullanın <xref:System.Windows.Controls.GridView>, <xref:System.Windows.Controls.GridViewColumn>, ve <xref:System.Windows.Controls.GridViewColumnHeader> sınıfları. Daha fazla bilgi için bkz: [GridView sütun üstbilgi stilleri ve şablonlarına genel bakış](../../../../docs/framework/wpf/controls/gridview-column-header-styles-and-templates-overview.md).  
  
<a name="AddingVisualElementstoaGridViewView"></a>   
### <a name="adding-visual-elements-to-a-gridview"></a>GridView için görsel öğeleri ekleme  
 Görsel öğeler gibi eklemek için <xref:System.Windows.Controls.CheckBox> ve <xref:System.Windows.Controls.Button> denetimleri bir <xref:System.Windows.Controls.GridView> görüntüleme modu, şablonlar veya stilleri kullanın.  
  
 Veri öğesi olarak açıkça bir görsel öğe tanımlarsanız, içinde yalnızca bir kez görünebilir bir <xref:System.Windows.Controls.GridView>. Bir öğe yalnızca bir üst olabilir ve bu nedenle, yalnızca bir kez görsel ağaç görülebilir var olduğundan, bu sınırlama.  
  
<a name="StylingRowsinaGridViewView"></a>   
### <a name="styling-rows-in-a-gridview"></a>GridView stil satır  
 Kullanım <xref:System.Windows.Controls.GridViewRowPresenter> ve <xref:System.Windows.Controls.GridViewHeaderRowPresenter> sınıfları biçimlendirmek ve satırlarını görüntülemek için bir <xref:System.Windows.Controls.GridView>. Stil satırlara nasıl ilişkin bir örnek bir <xref:System.Windows.Controls.GridView> modu görüntülemek için bkz: [bir satır GridView ListView olduğunu uygular stil](../../../../docs/framework/wpf/controls/how-to-style-a-row-in-a-listview-that-implements-a-gridview.md).  
  
<a name="AlignmentIssuesWhenUsingItemContainerStyle"></a>   
### <a name="alignment-issues-when-you-use-itemcontainerstyle"></a>ItemContainerStyle kullandığınızda hizalama sorunları  
 Sütun üstbilgileri ve hücreler arasındaki hizalama sorunlarını önlemek için bir özellik Ayarla veya değil bir öğenin genişliğini etkileyen bir şablonu belirtin bir <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A>. Örneğin, ayarlamayın <xref:System.Windows.FrameworkElement.Margin%2A> özelliği veya belirtmek bir <xref:System.Windows.Controls.ControlTemplate> ekleyen bir <xref:System.Windows.Controls.CheckBox> için bir <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> üzerinde tanımlanan bir <xref:System.Windows.Controls.ListView> denetim. Bunun yerine, özellikler ve doğrudan tanımlayan sınıflar üzerinde sütun genişliği etkileyen şablonlar belirtin bir <xref:System.Windows.Controls.GridView> görüntüleme modu.  
  
 Örneğin, eklemek için bir <xref:System.Windows.Controls.CheckBox> satırlara <xref:System.Windows.Controls.GridView> görünüm modu, ekleme <xref:System.Windows.Controls.CheckBox> için bir <xref:System.Windows.DataTemplate>ve ardından <xref:System.Windows.Controls.GridViewColumn.CellTemplate%2A> özelliğini <xref:System.Windows.DataTemplate>.  
  
<a name="InteractingwithaGridViewControl"></a>   
## <a name="user-interactions-with-a-gridview"></a>GridView ile kullanıcı etkileşimleri  
 Kullandığınızda, bir <xref:System.Windows.Controls.GridView> uygulamanızda, kullanıcıların etkileşime ve biçimlendirmesini değiştirme <xref:System.Windows.Controls.GridView>. Örneğin, kullanıcılar sütunları yeniden sıralama, bir sütunu yeniden boyutlandırmak, öğeleri bir tablo ve içerik kaydırma seçin. Ayrıca, bir kullanıcı sütun üstbilgisi düğmesine tıkladığında yanıt veren bir olay işleyicisi tanımlayabilirsiniz. Olay işleyicisi görüntülenen verileri sıralama gibi işlemler gerçekleştirebilirsiniz <xref:System.Windows.Controls.GridView> bir sütunun içeriğine göre.  
  
 Aşağıdaki listede kullanmanın yeteneklerini daha ayrıntılı olarak anlatılmaktadır <xref:System.Windows.Controls.GridView> kullanıcı etkileşimi için:  
  
-   **Sütunları yeniden sıralama sürükle ve bırak yöntemini kullanarak.**  
  
     Kullanıcıların sütunları yeniden sıralama bir <xref:System.Windows.Controls.GridView> bir sütun başlığına sol fare düğmesine basarak ve sonra bu sütun için yeni bir konuma sürükleyerek. Sütun başlığı kullanıcının sürüklediği olsa da, kayan bir sürüm üst bilgisi sütun eklemek istediğiniz yeri gösteren düz bir siyah çizgi yanı sıra görüntülenir.  
  
     Üstbilginin kayan sürümü için varsayılan stili değiştirmek istiyorsanız, belirtin bir <xref:System.Windows.Controls.ControlTemplate> için bir <xref:System.Windows.Controls.GridViewColumnHeader> yazın ayarlandığında tetiklenen <xref:System.Windows.Controls.GridViewColumnHeader.Role%2A> özelliği ayarlanmış <xref:System.Windows.Controls.GridViewColumnHeaderRole.Floating>. Daha fazla bilgi için bkz: [Sürüklenen GridView sütun başlığı için stil oluşturma](../../../../docs/framework/wpf/controls/how-to-create-a-style-for-a-dragged-gridview-column-header.md).  
  
-   **Bir sütunun içeriğine yönelik yeniden boyutlandırın.**  
  
     Kullanıcılar kendi içeriğin sığması için sütunu yeniden boyutlandırmak için sütun başlığını sağ kavrayıcıyı çift tıklayabilirsiniz.  
  
    > [!NOTE]
    >  Ayarlayabileceğiniz <xref:System.Windows.Controls.GridViewColumn.Width%2A> özelliğine `Double.NaN` aynı etkiyi üretmek için.  
  
-   **Satır öğeleri seçin.**  
  
     Kullanıcılar, bir veya daha fazla öğe seçebilirsiniz bir <xref:System.Windows.Controls.GridView>.  
  
     Değiştirmek istiyorsanız <xref:System.Windows.Style> seçili bir öğenin, bkz: [öğelerine stil seçili ListView Tetikleyicileri kullanma](../../../../docs/framework/wpf/controls/how-to-use-triggers-to-style-selected-items-in-a-listview.md).  
  
-   **Başlangıçta ekranda görünür olmayan içerik görüntülemek için gidin.**  
  
     Varsa boyutunu <xref:System.Windows.Controls.GridView> olan yeterince büyük değilse tüm öğeleri görüntülemek için kullanıcılar yatay kaydırma yapabilir veya dikey kaydırma çubuklarını kullanarak tarafından sağlanan bir <xref:System.Windows.Controls.ScrollViewer> denetim. A <xref:System.Windows.Controls.Primitives.ScrollBar> tüm içeriği belirli bir yönde görünür durumdaysa gizlenir. Sütun üst bilgileri ile bir dikey kaydırma çubuğunun kaydırma değil, ancak yatay kaydırma.  
  
-   **Sütun başlığı düğmelerini tıklayarak sütunlarla etkileşim.**  
  
     Kullanıcılar bir sütun üstbilgisi düğmesine tıkladığınızda, bunlar bir sıralama algoritması sağlanmışsa sütunda görüntülenen verileri sıralayabilirsiniz.  
  
     İşleyebilir <xref:System.Windows.Controls.Primitives.ButtonBase.Click> Sıralama algoritması gibi bir işlevsellik sağlamak için sütun başlığı düğmeleri için olay. İşlenecek <xref:System.Windows.Controls.Primitives.ButtonBase.Click> olayı bir tek sütun başlığı için açık bir olay işleyicisi ayarlayın <xref:System.Windows.Controls.GridViewColumnHeader>. İşleme bir olay işleyici ayarlamayı <xref:System.Windows.Controls.Primitives.ButtonBase.Click> olay tüm sütun başlıkları için ayarlandığında işleyici <xref:System.Windows.Controls.ListView> denetim.  
  
<a name="Obtaining_Other_Custom_Views"></a>   
## <a name="obtaining-other-custom-views"></a>Diğer özel görünümleri edinme  
 <xref:System.Windows.Controls.GridView> Türetilmiş sınıf <xref:System.Windows.Controls.ViewBase> soyut sınıf, olası görüntüleme modları için yalnızca biri <xref:System.Windows.Controls.ListView> sınıfı. Diğer özel görünümleri için oluşturabileceğiniz <xref:System.Windows.Controls.ListView> türetme tarafından <xref:System.Windows.Controls.ViewBase> sınıfı. Özel Görünüm modu örneği için bkz: [ListView için özel bir görünüm modu oluşturma](../../../../docs/framework/wpf/controls/how-to-create-a-custom-view-mode-for-a-listview.md).  
  
<a name="GridViewSupportingClasses"></a>   
## <a name="gridview-supporting-classes"></a>GridView destekleme sınıfları  
 Aşağıdaki sınıflar Destek <xref:System.Windows.Controls.GridView> görüntüleme modu.  
  
-   <xref:System.Windows.Controls.GridViewColumn>  
  
-   <xref:System.Windows.Controls.GridViewColumnHeader>  
  
-   <xref:System.Windows.Controls.GridViewRowPresenter>  
  
-   <xref:System.Windows.Controls.GridViewHeaderRowPresenter>  
  
-   <xref:System.Windows.Controls.GridViewColumnCollection>  
  
-   <xref:System.Windows.Controls.GridViewColumnHeaderRole>  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Controls.ListView>  
 <xref:System.Windows.Controls.ListViewItem>  
 <xref:System.Windows.Controls.GridViewColumn>  
 <xref:System.Windows.Controls.GridViewColumnHeader>  
 <xref:System.Windows.Controls.GridViewRowPresenter>  
 <xref:System.Windows.Controls.GridViewHeaderRowPresenter>  
 <xref:System.Windows.Controls.ViewBase>  
 [ListView Genel Bakış](../../../../docs/framework/wpf/controls/listview-overview.md)  
 [Üst Bilgiye Tıklandığında GridView Sütununu Sıralama](../../../../docs/framework/wpf/controls/how-to-sort-a-gridview-column-when-a-header-is-clicked.md)  
 [Nasıl Yapılır Konuları](../../../../docs/framework/wpf/controls/listview-how-to-topics.md)
