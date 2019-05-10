---
title: GridView Genel Bakışı
ms.date: 03/30/2017
helpviewer_keywords:
- GridView view mode [WPF]
- ListView controls [WPF], GridView view mode
- controls [WPF], ListView
ms.assetid: b2d02267-32b3-40ce-8e9f-06972d8749d9
ms.openlocfilehash: d1b9efb4016fbc3c4f7e14ea4a1c63308d992504
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64649168"
---
# <a name="gridview-overview"></a>GridView Genel Bakışı
<xref:System.Windows.Controls.GridView> Görünüm modu görüntüleme modlarına ilişkin biridir bir <xref:System.Windows.Controls.ListView> denetimi. <xref:System.Windows.Controls.GridView> Siz ve kullanıcılarınız genellikle etkileşimli sütun üst bilgilerini düğmeleri kullanan bir tablo öğesi koleksiyonları görüntülemek sınıf ve bunun destekleyici sınıfları etkinleştirin. Bu konu tanıtır <xref:System.Windows.Controls.GridView> sınıfı ve kullanımını açıklar.  

<a name="DefiningaListViewthatusesGridViewView"></a>   
## <a name="what-is-a-gridview-view"></a>GridView Görünüm nedir?  
 <xref:System.Windows.Controls.GridView> Görünüm modu sütunlara bağlama veri alanları ve alan tanımlamak için bir sütun başlığına göstererek veri öğelerinin bir listesini görüntüler. Varsayılan <xref:System.Windows.Controls.GridView> stil sütun başlığı olarak düğmeler uygular. Sütun üst bilgilerini düğmeleri kullanarak önemli kullanıcı etkileşim özellikleri uygulayabilir; Örneğin, kullanıcıların sıralamak için sütun başlığına tıklayarak <xref:System.Windows.Controls.GridView> verileri belirli bir sütunun içeriğine göre.  
  
> [!NOTE]
>  Bu düğme denetimleri <xref:System.Windows.Controls.GridView> kullanımlar için sütun başlıkları türetilir <xref:System.Windows.Controls.Primitives.ButtonBase>.  
  
 Aşağıdaki çizimde gösterildiği bir <xref:System.Windows.Controls.GridView> görünümünü <xref:System.Windows.Controls.ListView> içeriği.  
    
 ![GridView Görünüm ListView içeriğini gösteren ekran görüntüsü.](./media/gridview-overview/styled-listview-content.png)  
  
 <xref:System.Windows.Controls.GridView> sütunları olarak temsil edilir <xref:System.Windows.Controls.GridViewColumn> kendi içeriğinin boyutunu otomatik olarak nesneleri. İsteğe bağlı olarak, açıkça ayarlayabilirsiniz bir <xref:System.Windows.Controls.GridViewColumn> belirli bir genişliğe. Kavrayıcının sütun başlıkları arasında sürükleyerek sütunları yeniden boyutlandırabilirsiniz. Ayrıca dinamik olarak ekleyebilir, Kaldır, Değiştir ve bu işlev yerleşik olarak bulunur çünkü sütunları yeniden Sırala <xref:System.Windows.Controls.GridView>. Ancak, <xref:System.Windows.Controls.GridView> görüntülediği verileri doğrudan güncelleştirilemiyor.  
  
 Aşağıdaki örnek nasıl tanımlanacağını gösterir bir <xref:System.Windows.Controls.GridView> , çalışan verilerini görüntüler. Bu örnekte, <xref:System.Windows.Controls.ListView> tanımlar `EmployeeInfoDataSource` olarak <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>. Özellik tanımlarını <xref:System.Windows.Controls.GridViewColumn.DisplayMemberBinding%2A> bağlama <xref:System.Windows.Controls.GridViewColumn> içerik `EmployeeInfoDataSource` veri kategorileri.  
  
 [!code-xaml[ListViewCode#ListViewEmployee](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewCode/CSharp/Window1.xaml#listviewemployee)]  
  
 Aşağıdaki resimde, önceki örneğin oluşturduğu tabloda gösterilmiştir. GridView denetiminde ItemsSource nesne verilerden görüntüler:
    
 ![Bir ListView GridView çıktıyla gösteren ekran görüntüsü.](./media/gridview-overview/listview-gridview-output.jpg)  
  
<a name="GridViewLayoutandStyle"></a>   
## <a name="gridview-layout-and-style"></a>GridView düzenini ve stili  
 Sütun hücreleri ve sütun üst bilgisine bir <xref:System.Windows.Controls.GridViewColumn> aynı genişliğe sahiptir. Varsayılan olarak, her bir sütunun genişliğini İçeriği sığdırmak için boyutlandırır. İsteğe bağlı olarak, sabit bir genişliğe bir sütuna ayarlayabilirsiniz.  
  
 İlgili veri içeriğini yatay satır görüntüler. Yatay bir satırda göründükleri çünkü Örneğin, önceki resimde, her çalışanın soyadı, ad ve kimlik numarası bir küme olarak görüntülenir.  
  
<a name="DefiningandStylingColumnsinaGridView"></a>   
### <a name="defining-and-styling-columns-in-a-gridview"></a>Tanımlama ve içinde GridView Sütun stiller  
 Görüntülenecek veri alanı tanımlarken bir <xref:System.Windows.Controls.GridViewColumn>, kullanın <xref:System.Windows.Controls.GridViewColumn.DisplayMemberBinding%2A>, <xref:System.Windows.Controls.GridViewColumn.CellTemplate%2A>, veya <xref:System.Windows.Controls.GridViewColumn.CellTemplateSelector%2A> özellikleri. <xref:System.Windows.Controls.GridViewColumn.DisplayMemberBinding%2A> Özellik ya da şablon özelliklerinin öncelik alır.  
  
 Bir sütunda içeriği hizalaması belirtmek için bir <xref:System.Windows.Controls.GridView>, tanımlayan bir <xref:System.Windows.Controls.GridViewColumn.CellTemplate%2A>. Kullanmayın <xref:System.Windows.Controls.Control.HorizontalContentAlignment%2A> ve <xref:System.Windows.Controls.Control.VerticalContentAlignment%2A> özelliklerini <xref:System.Windows.Controls.ListView> kullanılarak görüntülenen içerik bir <xref:System.Windows.Controls.GridView>.  
  
 Sütun başlıkları için şablon ve stil özelliklerini belirtmek için kullanın <xref:System.Windows.Controls.GridView>, <xref:System.Windows.Controls.GridViewColumn>, ve <xref:System.Windows.Controls.GridViewColumnHeader> sınıfları. Daha fazla bilgi için [GridView sütun üstbilgi stil ve şablonlarına genel bakış](gridview-column-header-styles-and-templates-overview.md).  
  
<a name="AddingVisualElementstoaGridViewView"></a>   
### <a name="adding-visual-elements-to-a-gridview"></a>GridView görsel öğe ekleme  
 Görsel öğeler eklemek için <xref:System.Windows.Controls.CheckBox> ve <xref:System.Windows.Controls.Button> denetimleri bir <xref:System.Windows.Controls.GridView> görünüm modu, şablon veya stil kullanın.  
  
 Bir görsel öğe açıkça bir veri öğesi tanımlarsanız, içinde yalnızca bir kez görünebilir bir <xref:System.Windows.Controls.GridView>. Bir öğe yalnızca bir üste sahip olabilir ve bu nedenle, görsel ağaç yalnızca bir kez görünebilir çünkü bu sınırlama bulunmaktadır.  
  
<a name="StylingRowsinaGridViewView"></a>   
### <a name="styling-rows-in-a-gridview"></a>GridView içinde satırları stillendirme  
 Kullanım <xref:System.Windows.Controls.GridViewRowPresenter> ve <xref:System.Windows.Controls.GridViewHeaderRowPresenter> sınıfları biçimlendirmek ve satırları görüntülemek için bir <xref:System.Windows.Controls.GridView>. Stil satırlara ilişkin bir örnek için bir <xref:System.Windows.Controls.GridView> modunda görüntülemek için bkz: [GridView ListView olmasını uygular içinde bir satıra stil](how-to-style-a-row-in-a-listview-that-implements-a-gridview.md).  
  
<a name="AlignmentIssuesWhenUsingItemContainerStyle"></a>   
### <a name="alignment-issues-when-you-use-itemcontainerstyle"></a>ItemContainerStyle kullandığınızda hizalama sorunları  
 Sütun başlıklarının ve hücrelerin arasında hizalama sorunları önlemek için değil bir özelliği ayarlamak veya bir öğe genişliğini etkileyen bir şablonu belirtin bir <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A>. Örneğin, ayarlamayın <xref:System.Windows.FrameworkElement.Margin%2A> özelliği veya bir <xref:System.Windows.Controls.ControlTemplate> ekleyen bir <xref:System.Windows.Controls.CheckBox> için bir <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> üzerinde tanımlanan bir <xref:System.Windows.Controls.ListView> denetimi. Bunun yerine, özellikler ve doğrudan tanımlayan sınıflar üzerinde sütun genişliği etkileyen şablonlar belirtin bir <xref:System.Windows.Controls.GridView> görünüm modu.  
  
 Örneğin, eklemek için bir <xref:System.Windows.Controls.CheckBox> satırlara <xref:System.Windows.Controls.GridView> Ekle, görünüm modu <xref:System.Windows.Controls.CheckBox> için bir <xref:System.Windows.DataTemplate>ve ardından <xref:System.Windows.Controls.GridViewColumn.CellTemplate%2A> özelliğini <xref:System.Windows.DataTemplate>.  
  
<a name="InteractingwithaGridViewControl"></a>   
## <a name="user-interactions-with-a-gridview"></a>GridView kullanıcı etkileşim  
 Kullandığınızda, bir <xref:System.Windows.Controls.GridView> uygulamanızda, kullanıcılar etkileşim ve biçimini değiştirebilir <xref:System.Windows.Controls.GridView>. Örneğin, kullanıcılar sütunları yeniden Sırala, bir sütunu yeniden boyutlandır, tablo ve içerik öğeleri seçin. Kullanıcının sütun üst bilgisi düğmeye tıkladığında, yanıt veren bir olay işleyicisi de tanımlayabilirsiniz. Olay işleyicisi görüntülenen verileri sıralama gibi işlemler gerçekleştirebilirsiniz <xref:System.Windows.Controls.GridView> bir sütunun içeriğine göre.  
  
 Aşağıdaki listede, yeteneklerini kullanarak daha ayrıntılı olarak anlatır <xref:System.Windows.Controls.GridView> kullanıcı etkileşimi için:  
  
- **Sürükle ve bırak yöntemiyle sütunları yeniden Sırala.**  
  
     Kullanıcılar sütunları yeniden Sırala bir <xref:System.Windows.Controls.GridView> sütun başlığı üzerindeyken farenin sol düğmesine basarak ve ardından bu sütunu yeni bir konuma sürükleyerek. Kullanıcının sütun üst bilgisine sürüklerken, kayan bir üst bilgi sürümü sütun eklemek istediğiniz yeri gösteren düz bir siyah çizgi yanı sıra görüntülenir.  
  
     Kayan bir üst bilgi sürümü için varsayılan stili değiştirmek istiyorsanız, belirtin. bir <xref:System.Windows.Controls.ControlTemplate> için bir <xref:System.Windows.Controls.GridViewColumnHeader> yazın olduğunda tetiklenen <xref:System.Windows.Controls.GridViewColumnHeader.Role%2A> özelliği <xref:System.Windows.Controls.GridViewColumnHeaderRole.Floating>. Daha fazla bilgi için [bir Sürüklenen GridView sütun başlığı için stil oluşturma](how-to-create-a-style-for-a-dragged-gridview-column-header.md).  
  
- **İçeriği bir sütunu yeniden boyutlandır.**  
  
     Kullanıcılar, bir sütunu yeniden boyutlandırmak için sütun başlığına sağ kavrayıcıyı İçeriği sığdırmak için çift tıklayabilirsiniz.  
  
    > [!NOTE]
    >  Ayarlayabileceğiniz <xref:System.Windows.Controls.GridViewColumn.Width%2A> özelliğini `Double.NaN` aynı etkiyi oluşturmak için.  
  
- **Satır öğeleri seçin.**  
  
     Kullanıcılar, bir veya daha fazla öğe seçebilir bir <xref:System.Windows.Controls.GridView>.  
  
     Değiştirmek istiyorsanız <xref:System.Windows.Style> seçili bir öğe bkz: [bir ListView seçili öğelere stil için Tetikleyicileri kullanma](how-to-use-triggers-to-style-selected-items-in-a-listview.md).  
  
- **İlk ekranda görünür değil içeriği görüntülemek için kaydırın.**  
  
     Varsa boyutunu <xref:System.Windows.Controls.GridView> olan yeterince büyük değilse tüm öğeleri görüntülemek için kullanıcıların yatay olarak kaydırılıp veya dikey kaydırma çubuklarını kullanarak, tarafından sağlanan bir <xref:System.Windows.Controls.ScrollViewer> denetimi. A <xref:System.Windows.Controls.Primitives.ScrollBar> tüm içeriği belirli bir yönde görünür durumdaysa gizlenir. Sütun üst bilgilerini bir dikey kaydırma çubuğunun kaydırma değil, ancak yatay kaydırma.  
  
- **Sütunları içeren sütun başlığı düğmeleri tıklayarak etkileşim kurun.**  
  
     Kullanıcılar bir sütun üst bilgisi Düğmeye tıkladığınızda, sıralama algoritması sağladıysanız sütunda görüntülenen verileri sıralama yapabilirsiniz.  
  
     İşleyebilirsiniz <xref:System.Windows.Controls.Primitives.ButtonBase.Click> Sıralama algoritması gibi işlevler sağlamak için sütun üst bilgisi düğmeleri için olay. İşlenecek <xref:System.Windows.Controls.Primitives.ButtonBase.Click> olay tek bir sütun üst bilgisi için açık bir olay işleyicisi ayarlayın <xref:System.Windows.Controls.GridViewColumnHeader>. İşleme bir olay işleyicisini <xref:System.Windows.Controls.Primitives.ButtonBase.Click> tüm sütun başlıkları için olay işleyicisi üzerinde ayarlamak <xref:System.Windows.Controls.ListView> denetimi.  
  
<a name="Obtaining_Other_Custom_Views"></a>   
## <a name="obtaining-other-custom-views"></a>Diğer özel görünümleri edinme  
 <xref:System.Windows.Controls.GridView> Sınıfından türetilen sınıf <xref:System.Windows.Controls.ViewBase> soyut sınıfını, olası görüntüleme modlarına ilişkin yalnızca biri <xref:System.Windows.Controls.ListView> sınıfı. İçin diğer özel görünümler oluşturabileceğiniz <xref:System.Windows.Controls.ListView> türetilen <xref:System.Windows.Controls.ViewBase> sınıfı. Özel Görünüm modu örneği için bkz: [bir ListView için özel görünüm modu oluşturma](how-to-create-a-custom-view-mode-for-a-listview.md).  
  
<a name="GridViewSupportingClasses"></a>   
## <a name="gridview-supporting-classes"></a>GridView destekleyen sınıfları  
 Aşağıdaki sınıflar Destek <xref:System.Windows.Controls.GridView> görünüm modu.  
  
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
