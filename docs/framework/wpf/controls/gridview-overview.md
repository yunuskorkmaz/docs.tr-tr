---
title: GridView Genel Bakışı
description: Windows Presentation Foundation ListView denetimi için stiller ve şablonlar hakkında bilgi edinin. Denetime benzersiz bir görünüm sağlamak için ControlTemplate 'i değiştirin.
ms.date: 03/30/2017
helpviewer_keywords:
- GridView view mode [WPF]
- ListView controls [WPF], GridView view mode
- controls [WPF], ListView
ms.assetid: b2d02267-32b3-40ce-8e9f-06972d8749d9
ms.openlocfilehash: 02a2182ef1fc893107e434f431b9fbe0b3fbcd08
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87165925"
---
# <a name="gridview-overview"></a>GridView Genel Bakışı
<xref:System.Windows.Controls.GridView>Görünüm modu, bir denetim için görünüm modlarından biridir <xref:System.Windows.Controls.ListView> . <xref:System.Windows.Controls.GridView>Sınıfı ve destekleyici sınıfları, sizin ve kullanıcılarınızın, genellikle düğmeleri etkileşimli sütun başlıkları olarak kullanan bir tablodaki öğe koleksiyonlarını görüntülemesini sağlar. Bu konu sınıfı tanıtır <xref:System.Windows.Controls.GridView> ve kullanımını özetler.  

<a name="DefiningaListViewthatusesGridViewView"></a>
## <a name="what-is-a-gridview-view"></a>GridView görünümü nedir?  
 <xref:System.Windows.Controls.GridView>Görünüm modu, veri alanlarını sütunlara bağlayarak ve alanı tanımlamak için bir sütun üst bilgisi görüntüleyerek veri öğelerinin bir listesini görüntüler. Varsayılan <xref:System.Windows.Controls.GridView> stil düğmeleri sütun başlıkları olarak uygular. Sütun başlıkları için düğmeleri kullanarak, önemli Kullanıcı etkileşimi özelliklerini uygulayabilirsiniz; Örneğin, kullanıcılar <xref:System.Windows.Controls.GridView> verileri belirli bir sütunun içeriğine göre sıralamak için sütun başlığına tıklabilirler.  
  
> [!NOTE]
> <xref:System.Windows.Controls.GridView>Sütun başlıkları için kullanılan düğme denetimleri öğesinden türetilir <xref:System.Windows.Controls.Primitives.ButtonBase> .  
  
 Aşağıdaki çizimde bir <xref:System.Windows.Controls.GridView> içerik görünümü gösterilmektedir <xref:System.Windows.Controls.ListView> .  

 ![ListView içeriğinin GridView görünümünü gösteren ekran görüntüsü.](./media/gridview-overview/styled-listview-content.png)  
  
 <xref:System.Windows.Controls.GridView>sütunlar nesneler tarafından temsil edilir <xref:System.Windows.Controls.GridViewColumn> ve içeriğe otomatik olarak boyutlenebilir. İsteğe bağlı olarak, açıkça belirli bir <xref:System.Windows.Controls.GridViewColumn> Genişlik olarak ayarlayabilirsiniz. Kavrayıcıyı sütun başlıkları arasında sürükleyerek sütunları yeniden boyutlandırabilirsiniz. Ayrıca, bu işlev yerleşik olarak bulunduğu için sütunları dinamik olarak ekleyebilir, kaldırabilir, değiştirebilir ve yeniden sıralayabilirsiniz <xref:System.Windows.Controls.GridView> . Ancak, <xref:System.Windows.Controls.GridView> görüntülediği veriler doğrudan güncelleştirilemez.  
  
 Aşağıdaki örnek, <xref:System.Windows.Controls.GridView> çalışan verilerini görüntüleyen bir 'nın nasıl tanımlanacağını göstermektedir. Bu örnekte, öğesini <xref:System.Windows.Controls.ListView> olarak tanımlar `EmployeeInfoDataSource` <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> . İçerik bağlama özelliğinin özellik <xref:System.Windows.Controls.GridViewColumn.DisplayMemberBinding%2A> tanımları <xref:System.Windows.Controls.GridViewColumn> `EmployeeInfoDataSource` veri kategorilerine.  
  
 [!code-xaml[ListViewCode#ListViewEmployee](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewCode/CSharp/Window1.xaml#listviewemployee)]  
  
 Aşağıdaki çizimde, önceki örneğin oluşturduğu tablo gösterilmektedir. GridView denetimi bir ıtemısource nesnesinden verileri görüntüler:

 ![GridView çıkışıyla bir ListView gösteren ekran görüntüsü.](./media/gridview-overview/listview-gridview-output.jpg)  
  
<a name="GridViewLayoutandStyle"></a>
## <a name="gridview-layout-and-style"></a>GridView düzeni ve stili  
 Sütun hücrelerinin ve sütununun sütun üstbilgisinin <xref:System.Windows.Controls.GridViewColumn> genişliği aynı. Varsayılan olarak, her sütun genişliğini içeriğine uyacak şekilde boyutlandırır. İsteğe bağlı olarak, bir sütunu sabit genişliğe ayarlayabilirsiniz.  
  
 İlgili veri içeriği yatay satırlarda görüntülenir. Örneğin, önceki çizimde, her çalışanın soyadı, adı ve KIMLIK numarası, yatay bir satırda göründükleri için bir küme olarak görüntülenir.  
  
<a name="DefiningandStylingColumnsinaGridView"></a>
### <a name="defining-and-styling-columns-in-a-gridview"></a>GridView 'da sütunları tanımlama ve Stillendirme  
 İçinde görüntülenecek veri alanını tanımlarken,, <xref:System.Windows.Controls.GridViewColumn> <xref:System.Windows.Controls.GridViewColumn.DisplayMemberBinding%2A> <xref:System.Windows.Controls.GridViewColumn.CellTemplate%2A> veya <xref:System.Windows.Controls.GridViewColumn.CellTemplateSelector%2A> özelliklerini kullanın. <xref:System.Windows.Controls.GridViewColumn.DisplayMemberBinding%2A>Özelliği, şablon özelliklerinden herhangi birinin üzerine gelir.  
  
 İçeriğinin bir sütununda hizalamasını belirtmek için <xref:System.Windows.Controls.GridView> bir tanımlayın <xref:System.Windows.Controls.GridViewColumn.CellTemplate%2A> . <xref:System.Windows.Controls.Control.HorizontalContentAlignment%2A> <xref:System.Windows.Controls.Control.VerticalContentAlignment%2A> Kullanılarak görüntülenen içerik için ve özelliklerini kullanmayın <xref:System.Windows.Controls.ListView> <xref:System.Windows.Controls.GridView> .  
  
 Sütun başlıkları için şablon ve stil özelliklerini belirtmek üzere,, <xref:System.Windows.Controls.GridView> <xref:System.Windows.Controls.GridViewColumn> ve <xref:System.Windows.Controls.GridViewColumnHeader> sınıflarını kullanın. Daha fazla bilgi için bkz. [GridView sütun üst bilgi stilleri ve şablonlara genel bakış](gridview-column-header-styles-and-templates-overview.md).  
  
<a name="AddingVisualElementstoaGridViewView"></a>
### <a name="adding-visual-elements-to-a-gridview"></a>GridView 'a görsel öğe ekleme  
 Ve denetimleri gibi görsel öğeleri <xref:System.Windows.Controls.CheckBox> <xref:System.Windows.Controls.Button> bir <xref:System.Windows.Controls.GridView> Görünüm moduna eklemek için şablonlar veya stiller kullanın.  
  
 Bir görsel öğeyi bir veri öğesi olarak açıkça tanımlarsanız, bir içinde yalnızca bir kez görünebilir <xref:System.Windows.Controls.GridView> . Bu sınırlama, bir öğenin yalnızca bir üst öğesi olabileceğinden ve bu nedenle görsel ağaçta yalnızca bir kez görünebildiğinden oluşur.  
  
<a name="StylingRowsinaGridViewView"></a>
### <a name="styling-rows-in-a-gridview"></a>GridView 'da satır Stillendirme  
 <xref:System.Windows.Controls.GridViewRowPresenter>Ve <xref:System.Windows.Controls.GridViewHeaderRowPresenter> satırlarını biçimlendirmek ve göstermek için ve sınıflarını kullanın <xref:System.Windows.Controls.GridView> . Bir görünüm modundaki satırların nasıl Stillendirilmesi hakkında bir örnek için <xref:System.Windows.Controls.GridView> , bkz. [GridView Uygulayan ListView Içindeki bir satırı stilme](how-to-style-a-row-in-a-listview-that-implements-a-gridview.md).  
  
<a name="AlignmentIssuesWhenUsingItemContainerStyle"></a>
### <a name="alignment-issues-when-you-use-itemcontainerstyle"></a>ItemContainerStyle kullandığınızda hizalama sorunları  
 Sütun üstbilgileri ve hücreler arasındaki hizalama sorunlarını engellemek için, bir özellik ayarlamayın veya içindeki bir öğenin genişliğini etkileyen bir şablon belirtmeyin <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> . Örneğin, <xref:System.Windows.FrameworkElement.Margin%2A> özelliğini ayarlamayın veya bir <xref:System.Windows.Controls.ControlTemplate> <xref:System.Windows.Controls.CheckBox> denetimde tanımlı bir öğesine ekleyen bir öğesini belirtin <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> <xref:System.Windows.Controls.ListView> . Bunun yerine, bir görünüm modunu tanımlayan sınıflarda doğrudan sütun genişliğini etkileyen özellikleri ve şablonları belirtin <xref:System.Windows.Controls.GridView> .  
  
 Örneğin, görüntüleme modundaki satırlara bir eklemek için öğesini <xref:System.Windows.Controls.CheckBox> <xref:System.Windows.Controls.GridView> <xref:System.Windows.Controls.CheckBox> öğesine ekleyin <xref:System.Windows.DataTemplate> ve sonra <xref:System.Windows.Controls.GridViewColumn.CellTemplate%2A> özelliği bu olarak ayarlayın <xref:System.Windows.DataTemplate> .  
  
<a name="InteractingwithaGridViewControl"></a>
## <a name="user-interactions-with-a-gridview"></a>GridView ile kullanıcı etkileşimleri  
 Uygulamanızda bir kullandığınızda <xref:System.Windows.Controls.GridView> , kullanıcılar ile etkileşime geçebilir ve biçimlendirmesini değiştirebilir <xref:System.Windows.Controls.GridView> . Örneğin, kullanıcılar sütunları yeniden sıralayabilir, bir sütunu yeniden boyutlandırabilir, tablodaki öğeleri seçebilir ve içeriği kaydırabilirler. Ayrıca, bir Kullanıcı sütun üst bilgisi düğmesine tıkladığında yanıt veren bir olay işleyicisi tanımlayabilirsiniz. Olay işleyicisi, <xref:System.Windows.Controls.GridView> bir sütunun içeriğine göre görüntülenen verileri sıralama gibi işlemler gerçekleştirebilir.  
  
 Aşağıdaki liste, Kullanıcı etkileşimi için kullanmanın yeteneklerini daha ayrıntılı bir şekilde anlatmaktadır <xref:System.Windows.Controls.GridView> :  
  
- **Sürükle ve bırak yöntemini kullanarak sütunları yeniden sıralayın.**  
  
     Kullanıcılar bir <xref:System.Windows.Controls.GridView> sütun başlığı üzerindeyken sol fare düğmesine basarak ve sonra bu sütunu yeni bir konuma sürükleyerek, içindeki sütunları yeniden sıralayabilir. Kullanıcı sütun başlığını sürüklediğinde, başlığın kayan bir sürümü ve sütunun ekleneceği yeri gösteren düz bir siyah çizgi görüntülenir.  
  
     Bir üstbilginin kayan sürümünün varsayılan stilini değiştirmek istiyorsanız, <xref:System.Windows.Controls.ControlTemplate> <xref:System.Windows.Controls.GridViewColumnHeader> özelliği olarak ayarlandığında tetiklenen bir tür için bir seçin <xref:System.Windows.Controls.GridViewColumnHeader.Role%2A> <xref:System.Windows.Controls.GridViewColumnHeaderRole.Floating> . Daha fazla bilgi için bkz. [sürüklenen GridView sütun üst bilgisi Için stil oluşturma](how-to-create-a-style-for-a-dragged-gridview-column-header.md).  
  
- **Bir sütunu içeriğine göre yeniden boyutlandırın.**  
  
     Kullanıcılar bir sütunu içeriğe sığacak şekilde yeniden boyutlandırmak için bir sütun üst bilgisinin sağındaki kavrayıcıyı çift tıklayabilirler.  
  
    > [!NOTE]
    > <xref:System.Windows.Controls.GridViewColumn.Width%2A>Özelliğini `Double.NaN` aynı etkiyi oluşturmak için olarak ayarlayabilirsiniz.  
  
- **Satır öğelerini seçin.**  
  
     Kullanıcılar bir veya daha fazla öğeyi bir veya daha fazla seçim yapabilir <xref:System.Windows.Controls.GridView> .  
  
     <xref:System.Windows.Style>Seçili bir öğenin öğesini değiştirmek istiyorsanız, bkz. [ListView Içindeki seçili öğelere stil eklemek Için Tetikleyicileri kullanma](how-to-use-triggers-to-style-selected-items-in-a-listview.md).  
  
- **Başlangıçta ekranda görünmeyen içeriği görüntülemek için kaydırın.**  
  
     Boyutu <xref:System.Windows.Controls.GridView> tüm öğelerin görüntülenmesi için yeterince büyük değilse, kullanıcılar bir denetim tarafından sunulan kaydırma çubuklarını kullanarak yatay veya dikey bir şekilde kaydırabilirler <xref:System.Windows.Controls.ScrollViewer> . <xref:System.Windows.Controls.Primitives.ScrollBar>Tüm içerik belirli bir yönde görünür durumdaysa, gizli olur. Sütun başlıkları dikey bir kaydırma çubuğuyla kaydırılmaz, ancak yatay olarak kaydırılmaz.  
  
- **Sütun başlığı düğmelerine tıklayarak sütunlarla etkileşime geçin.**  
  
     Kullanıcılar bir sütun üst bilgisi düğmesine tıkladıklarında, bir sıralama algoritması sağladıysanız sütunda görüntülenen verileri sıralabilirler.  
  
     <xref:System.Windows.Controls.Primitives.ButtonBase.Click>Sıralama algoritması gibi işlevler sağlamak için sütun üst bilgisi düğmelerinin olayını işleyebilirsiniz. <xref:System.Windows.Controls.Primitives.ButtonBase.Click>Tek bir sütun üst bilgisinin olayını işlemek için üzerinde bir olay işleyicisi ayarlayın <xref:System.Windows.Controls.GridViewColumnHeader> . Tüm sütun başlıkları için olayı işleyen bir olay işleyicisi ayarlamak için <xref:System.Windows.Controls.Primitives.ButtonBase.Click> , denetimde işleyiciyi ayarlayın <xref:System.Windows.Controls.ListView> .  
  
<a name="Obtaining_Other_Custom_Views"></a>
## <a name="obtaining-other-custom-views"></a>Diğer özel görünümleri edinme  
 <xref:System.Windows.Controls.GridView>Soyut sınıftan türetilmiş sınıf, <xref:System.Windows.Controls.ViewBase> sınıf için olası görünüm modlarından yalnızca biridir <xref:System.Windows.Controls.ListView> . Sınıfından türeterek için başka özel görünümler oluşturabilirsiniz <xref:System.Windows.Controls.ListView> <xref:System.Windows.Controls.ViewBase> . Özel görünüm moduna bir örnek için bkz. [ListView Için özel görünüm modu oluşturma](how-to-create-a-custom-view-mode-for-a-listview.md).  
  
<a name="GridViewSupportingClasses"></a>
## <a name="gridview-supporting-classes"></a>GridView destekleme sınıfları  
 Aşağıdaki sınıflar <xref:System.Windows.Controls.GridView> Görünüm modunu destekler.  
  
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
- [ListView Genel Bakışı](listview-overview.md)
- [Üst Bilgiye Tıklandığında GridView Sütununu Sıralama](how-to-sort-a-gridview-column-when-a-header-is-clicked.md)
- [Nasıl Yapılır Konuları](listview-how-to-topics.md)
