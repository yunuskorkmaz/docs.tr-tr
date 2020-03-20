---
title: GridView Genel Bakışı
ms.date: 03/30/2017
helpviewer_keywords:
- GridView view mode [WPF]
- ListView controls [WPF], GridView view mode
- controls [WPF], ListView
ms.assetid: b2d02267-32b3-40ce-8e9f-06972d8749d9
ms.openlocfilehash: 98bc7985172cabeab19469af4b4c21e13a6bce73
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181896"
---
# <a name="gridview-overview"></a>GridView Genel Bakışı
<xref:System.Windows.Controls.GridView>görünüm modu, denetim <xref:System.Windows.Controls.ListView> için görünüm modlarından biridir. Sınıf <xref:System.Windows.Controls.GridView> ve destekleyici sınıfları, sizin ve kullanıcılarınızın öğe koleksiyonlarını genellikle düğmeleri etkileşimli sütun üstbilgi olarak kullanan bir tabloda görüntülemenize olanak tanır. Bu konu <xref:System.Windows.Controls.GridView> sınıfı tanır ve kullanımını özetler.  

<a name="DefiningaListViewthatusesGridViewView"></a>
## <a name="what-is-a-gridview-view"></a>GridView Görünümü Nedir?  
 Görünüm <xref:System.Windows.Controls.GridView> modu, veri alanlarını sütunlara bağlayarak ve alanı tanımlamak için bir sütun üstbilgisi görüntüleyerek veri öğelerinin listesini görüntüler. Varsayılan <xref:System.Windows.Controls.GridView> stil düğmeleri sütun üstbilgi olarak uygular. Sütun üstbilgi düğmeleri kullanarak önemli kullanıcı etkileşimi yeteneklerini uygulayabilirsiniz; örneğin, kullanıcılar belirli bir sütunun <xref:System.Windows.Controls.GridView> içeriğine göre verileri sıralamak için sütun üstbilgisini tıklatabilir.  
  
> [!NOTE]
> Sütun üstbilgilerinin <xref:System.Windows.Controls.GridView> kullandığı düğme <xref:System.Windows.Controls.Primitives.ButtonBase>denetimleri.  
  
 Aşağıdaki resimde <xref:System.Windows.Controls.GridView> <xref:System.Windows.Controls.ListView> içerik görünümü gösterilmektedir.  

 ![ListView içeriğinin GridView görünümünü gösteren ekran görüntüsü.](./media/gridview-overview/styled-listview-content.png)  
  
 <xref:System.Windows.Controls.GridView>sütunlar, içeriklerine otomatik olarak boyutlandırılabilen nesneler tarafından <xref:System.Windows.Controls.GridViewColumn> temsil edilir. İsteğe bağlı olarak, a'yı <xref:System.Windows.Controls.GridViewColumn> açıkça belirli bir genişliğe ayarlayabilirsiniz. Kavrayıcıyı sütun başlıkları arasında sürükleyerek sütunları yeniden boyutlandırabilirsiniz. Ayrıca, bu işlevsellik yerleşik olduğundan, sütunları dinamik olarak ekleyebilir, kaldırabilir, değiştirebilir ve yeniden <xref:System.Windows.Controls.GridView>sıralayabilirsiniz. Ancak, <xref:System.Windows.Controls.GridView> görüntülenebilen verileri doğrudan güncelleştiremezsiniz.  
  
 Aşağıdaki örnek, çalışan verilerini <xref:System.Windows.Controls.GridView> görüntüleyen bir şeyin nasıl tanımlanılsüreceğini gösterir. Bu örnekte, <xref:System.Windows.Controls.ListView> `EmployeeInfoDataSource` <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>'. Bağlayıcı <xref:System.Windows.Controls.GridViewColumn.DisplayMemberBinding%2A> <xref:System.Windows.Controls.GridViewColumn> içeriğin veri kategorilerine `EmployeeInfoDataSource` özellik tanımları.  
  
 [!code-xaml[ListViewCode#ListViewEmployee](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewCode/CSharp/Window1.xaml#listviewemployee)]  
  
 Aşağıdaki resimde, önceki örnekte oluşturduğu tablo gösterilmektedir. GridView denetimi, Bir ItemsSource nesnesinden gelen verileri görüntüler:

 ![GridView çıktılı bir ListView gösteren ekran görüntüsü.](./media/gridview-overview/listview-gridview-output.jpg)  
  
<a name="GridViewLayoutandStyle"></a>
## <a name="gridview-layout-and-style"></a>GridView Düzeni ve Stili  
 Sütun hücreleri ve bir <xref:System.Windows.Controls.GridViewColumn> sütun üstbilgiaynı genişliğe sahip. Varsayılan olarak, her sütun kendi içeriğine uyacak şekilde genişliğini boyutlar. İsteğe bağlı olarak, bir sütunu sabit genişliğe ayarlayabilirsiniz.  
  
 İlgili veri içeriği yatay satırlarda görüntülenir. Örneğin, önceki resimde, yatay bir satırda göründükleri için her çalışanın soyadı, adı ve kimlik numarası küme olarak görüntülenir.  
  
<a name="DefiningandStylingColumnsinaGridView"></a>
### <a name="defining-and-styling-columns-in-a-gridview"></a>GridView'da Sütunları Tanımlama ve Şekillendirme  
 Görüntülemek için veri alanını tanımlarken <xref:System.Windows.Controls.GridViewColumn> <xref:System.Windows.Controls.GridViewColumn.DisplayMemberBinding%2A>, , <xref:System.Windows.Controls.GridViewColumn.CellTemplate%2A>veya <xref:System.Windows.Controls.GridViewColumn.CellTemplateSelector%2A> özellikleri kullanın. Özellik, <xref:System.Windows.Controls.GridViewColumn.DisplayMemberBinding%2A> şablon özelliklerinden herhangi biri üzerinde önceliklidir.  
  
 Bir sütundaki içeriğin hizalanmasını <xref:System.Windows.Controls.GridView>belirtmek için <xref:System.Windows.Controls.GridViewColumn.CellTemplate%2A>, bir . <xref:System.Windows.Controls.Control.HorizontalContentAlignment%2A> <xref:System.Windows.Controls.GridView>Bir <xref:System.Windows.Controls.Control.VerticalContentAlignment%2A> <xref:System.Windows.Controls.ListView>  
  
 Sütun üstbilgiler için şablon ve stil <xref:System.Windows.Controls.GridView>özelliklerini <xref:System.Windows.Controls.GridViewColumn>belirtmek <xref:System.Windows.Controls.GridViewColumnHeader> için , ve sınıfları kullanın. Daha fazla bilgi için [GridView Sütun Üstbilgi Stilleri ve Şablonlara Genel Bakış'a](gridview-column-header-styles-and-templates-overview.md)bakın.  
  
<a name="AddingVisualElementstoaGridViewView"></a>
### <a name="adding-visual-elements-to-a-gridview"></a>GridView'a Görsel Öğeler Ekleme  
 Görünüm moduna ve <xref:System.Windows.Controls.CheckBox> <xref:System.Windows.Controls.Button> denetimler gibi görsel öğeler eklemek için şablonları veya stilleri kullanın. <xref:System.Windows.Controls.GridView>  
  
 Görsel öğeyi açıkça bir veri öğesi olarak tanımlarsanız, bir <xref:System.Windows.Controls.GridView>'de yalnızca bir kez görüntülenebilir. Bu sınırlama, bir öğenin yalnızca bir üst öğesi olabilir ve bu nedenle, görsel ağaçta yalnızca bir kez görüntülenebilir çünkü var.  
  
<a name="StylingRowsinaGridViewView"></a>
### <a name="styling-rows-in-a-gridview"></a>GridView'da Satırları Şekillendirme  
 Bir <xref:System.Windows.Controls.GridViewRowPresenter> <xref:System.Windows.Controls.GridView>' <xref:System.Windows.Controls.GridViewHeaderRowPresenter> nin satırlarını biçimlendirmek ve görüntülemek için ve sınıfları kullanın. <xref:System.Windows.Controls.GridView> Görünüm modunda satırları nasıl stile uygulayacağınız örneği için [GridView Uygulayan ListView'da Satır Stili'ne](how-to-style-a-row-in-a-listview-that-implements-a-gridview.md)bakın.  
  
<a name="AlignmentIssuesWhenUsingItemContainerStyle"></a>
### <a name="alignment-issues-when-you-use-itemcontainerstyle"></a>ItemContainerStyle kullanırken hizalama sorunları  
 Sütun üstbilgi ve hücreler arasındaki hizalama sorunlarını önlemek için, bir özellik ayarlamayın <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A>veya bir maddenin genişliğini etkileyen bir şablon belirtin. Örneğin, <xref:System.Windows.FrameworkElement.Margin%2A> özelliği ayarlamayın veya <xref:System.Windows.Controls.ControlTemplate> denetimde <xref:System.Windows.Controls.CheckBox> tanımlanan <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> bir a'ya <xref:System.Windows.Controls.ListView> bir şey ekleyen bir özellik belirtmeyin. Bunun yerine, <xref:System.Windows.Controls.GridView> sütun genişliğini doğrudan bir görünüm modu tanımlayan sınıflarda etkileyen özellikleri ve şablonları belirtin.  
  
 Örneğin, <xref:System.Windows.Controls.CheckBox> <xref:System.Windows.Controls.GridView> görünüm modundasatırlara bir eklemek <xref:System.Windows.Controls.CheckBox> için, bir <xref:System.Windows.DataTemplate>,'a ekleyin <xref:System.Windows.Controls.GridViewColumn.CellTemplate%2A> ve <xref:System.Windows.DataTemplate>sonra özelliği buna ayarlayın.  
  
<a name="InteractingwithaGridViewControl"></a>
## <a name="user-interactions-with-a-gridview"></a>GridView ile Kullanıcı Etkileşimleri  
 Uygulamanızda bir <xref:System.Windows.Controls.GridView> a kullandığınızda, kullanıcılar ile etkileşim ve <xref:System.Windows.Controls.GridView>biçimlendirme değiştirebilirsiniz. Örneğin, kullanıcılar sütunları yeniden sıralayabilir, sütunu yeniden boyutlandırabilir, tablodaki öğeleri seçebilir ve içerik arasında gezinebilir. Ayrıca, bir kullanıcı sütun üstbilgisi düğmesini tıklattığında yanıt veren bir olay işleyicisi de tanımlayabilirsiniz. Olay işleyicisi, sütuniçeriğine <xref:System.Windows.Controls.GridView> göre görüntülenen verileri sıralama gibi işlemler gerçekleştirebilir.  
  
 Aşağıdaki liste, kullanıcı etkileşimi için kullanma <xref:System.Windows.Controls.GridView> nın yeteneklerini daha ayrıntılı olarak tartışır:  
  
- **Sürükle ve bırak yöntemini kullanarak sütunları yeniden sırala.**  
  
     Kullanıcılar, sütun üstbilginin üzerindeyken sol fare düğmesine <xref:System.Windows.Controls.GridView> basarak ve sonra bu sütunu yeni bir konuma sürükleyerek sütunları yeniden sıralayabilir. Kullanıcı sütun üstbilgisini sürüklerken, üstbilginin kayan bir sürümü ve sütunun nereye ekleneceğini gösteren düz siyah bir çizgi görüntülenir.  
  
     Üstbilginin kayan sürümü için varsayılan stili değiştirmek istiyorsanız, <xref:System.Windows.Controls.ControlTemplate> özellik <xref:System.Windows.Controls.GridViewColumnHeader> ayarlandığında tetiklenen bir <xref:System.Windows.Controls.GridViewColumnHeader.Role%2A> tür için <xref:System.Windows.Controls.GridViewColumnHeaderRole.Floating>bir a belirtin. Daha fazla bilgi için bkz: [Sürüncemede Edilmiş GridView Sütun Başlığı için Stil Oluştur.](how-to-create-a-style-for-a-dragged-gridview-column-header.md)  
  
- **Bir sütunu içeriğine göre yeniden boyutlandırın.**  
  
     Kullanıcılar, bir sütunu içeriğine uyacak şekilde yeniden boyutlandırmak için sütun başlığının sağındaki kavrayıcıyı çift tıklatabilir.  
  
    > [!NOTE]
    > <xref:System.Windows.Controls.GridViewColumn.Width%2A> Özelliği aynı etkiyi `Double.NaN` üretecek şekilde ayarlayabilirsiniz.  
  
- **Satır öğelerini seçin.**  
  
     Kullanıcılar bir <xref:System.Windows.Controls.GridView>'de bir veya daha fazla öğe seçebilir.  
  
     Seçili bir öğenin öğesini <xref:System.Windows.Style> değiştirmek istiyorsanız, [listview'de Seçili Öğeleri Stil'de Tetikleyicileri Kullan'a](how-to-use-triggers-to-style-selected-items-in-a-listview.md)bakın.  
  
- **Başlangıçta ekranda görünmeyen içeriği görüntülemek için kaydırın.**  
  
     Boyutu <xref:System.Windows.Controls.GridView> tüm öğeleri görüntülemek için yeterince büyük değilse, kullanıcılar bir <xref:System.Windows.Controls.ScrollViewer> denetim tarafından sağlanan kaydırma çubukları kullanarak yatay veya dikey kaydırma yapabilirsiniz. Tüm <xref:System.Windows.Controls.Primitives.ScrollBar> içerik belirli bir yönde görünürse A gizlenir. Sütun başlıkları dikey kaydırma çubuğuyla kaydırmaz, yatay kaydırma yapar.  
  
- **Sütun üstbilgi düğmelerini tıklatarak sütunlarla etkileşimkurun.**  
  
     Kullanıcılar bir sütun üstbilgisi düğmesini tıklattıklarında, sıralama algoritması sağladıysanız sütunda görüntülenen verileri sıralayabilirler.  
  
     Sıralama algoritması <xref:System.Windows.Controls.Primitives.ButtonBase.Click> gibi işlevsellik sağlamak için sütun üstbilgi düğmeleri için olayı işleyebilirsiniz. Olayı tek <xref:System.Windows.Controls.Primitives.ButtonBase.Click> bir sütun üstbilgiiçin işlemek için, ''nin üzerinde bir olay işleyicisi <xref:System.Windows.Controls.GridViewColumnHeader>ayarlayın Tüm sütun üstbilgilerinin <xref:System.Windows.Controls.Primitives.ButtonBase.Click> olayı işleyen bir olay işleyicisini ayarlamak için <xref:System.Windows.Controls.ListView> işleyiciyi denetime ayarlayın.  
  
<a name="Obtaining_Other_Custom_Views"></a>
## <a name="obtaining-other-custom-views"></a>Diğer Özel Görünümleri Edinme  
 Soyut sınıftan türetilen sınıf, <xref:System.Windows.Controls.ListView> sınıfın olası görünüm modlarından sadece biridir. <xref:System.Windows.Controls.GridView> <xref:System.Windows.Controls.ViewBase> <xref:System.Windows.Controls.ViewBase> Sınıftan <xref:System.Windows.Controls.ListView> türeyen diğer özel görünümler oluşturabilirsiniz. Özel görünüm modu örneği [için](how-to-create-a-custom-view-mode-for-a-listview.md)bkz.  
  
<a name="GridViewSupportingClasses"></a>
## <a name="gridview-supporting-classes"></a>GridView Destekleyici Sınıflar  
 Aşağıdaki sınıflar görünüm <xref:System.Windows.Controls.GridView> modunu destekler.  
  
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
- [Nasıl Dır Konular](listview-how-to-topics.md)
