---
title: ListView Genel Bakışı
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [WPF], ListView
- ListView controls [WPF], about ListView control
ms.assetid: 989e12b0-260e-4570-95c6-489284003ce2
ms.openlocfilehash: a3b5805808ce2e84e7713f07694464b75d83a391
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43424268"
---
# <a name="listview-overview"></a>ListView Genel Bakışı
<xref:System.Windows.Controls.ListView> Denetim bir veri öğeleri kümesi farklı düzenler veya görünümleri görüntülemek için altyapı sağlar. Örneğin, bir kullanıcı, bir tablodaki veri öğelerini görüntülemek ve sıralama sütunlarını isteyebilirsiniz.  
  
  
<a name="WhatisaListView"></a>   
## <a name="what-is-a-listview"></a>Bir ListView nedir?  
 <xref:System.Windows.Controls.ListView> Denetimi bir <xref:System.Windows.Controls.ItemsControl> sınıfından türetilen <xref:System.Windows.Controls.ListBox>. Genellikle, öğelerinden veri koleksiyonunun üyeleridir ve olarak temsil edilmektedir <xref:System.Windows.Controls.ListViewItem> nesneleri. A <xref:System.Windows.Controls.ListViewItem> olduğu bir <xref:System.Windows.Controls.ContentControl> ve yalnızca tek bir alt öğe içerebilir. Ancak, bu alt öğesi herhangi bir görsel öğe olabilir.  
  
<a name="DefiningaListViewView"></a>   
## <a name="defining-a-view-mode-for-a-listview"></a>Bir ListView için bir görünüm modu tanımlama  
 İçeriği için görüntüleme modu belirtmek için bir <xref:System.Windows.Controls.ListView> denetimi, ayarladığınız <xref:System.Windows.Controls.ListView.View%2A> özelliği. Bir görünüm modu, [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] sağlar olan <xref:System.Windows.Controls.GridView>, özelleştirilebilir sütunları olan bir tabloda veri öğelerinin bir koleksiyonunu görüntüler.  
  
 Aşağıdaki örnek nasıl tanımlanacağını gösterir bir <xref:System.Windows.Controls.GridView> için bir <xref:System.Windows.Controls.ListView> çalışan bilgilerini görüntüleyen denetim.  
  
 [!code-xaml[ListViewCode#ListViewEmployee](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewCode/CSharp/Window1.xaml#listviewemployee)]  
  
 Aşağıdaki çizim, önceki örneğin verinin nasıl göründüğünü gösterir.  
  
 ![ListView GridView çıktıyla](../../../../docs/framework/wpf/controls/media/listviewgridview.JPG "ListViewGridView")  
  
 Özel Görünüm modu öğesinden devralınan bir sınıf tanımlayarak oluşturabileceğiniz <xref:System.Windows.Controls.ViewBase> sınıfı. <xref:System.Windows.Controls.ViewBase> Sınıfı, bir özel görünüm oluşturmak için gereken altyapıyı sağlar. Özel Görünüm oluşturma hakkında daha fazla bilgi için bkz. [bir ListView için özel görünüm modu oluşturma](../../../../docs/framework/wpf/controls/how-to-create-a-custom-view-mode-for-a-listview.md).  
  
<a name="BindingDatatoaListView"></a>   
## <a name="binding-data-to-a-listview"></a>Bir ListView veri bağlama  
 Kullanım <xref:System.Windows.Controls.ItemsControl.Items%2A> ve <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> özellikleri öğelerini belirtmek için bir <xref:System.Windows.Controls.ListView> denetimi. Aşağıdaki örnek kümeleri <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> çağrılan bir veri toplama özelliğini `EmployeeInfoDataSource`.  
  
 [!code-xaml[ListViewCode#ItemsSource](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewCode/CSharp/Window1.xaml#itemssource)]  
  
 İçinde bir <xref:System.Windows.Controls.GridView>, <xref:System.Windows.Controls.GridViewColumn> nesneleri belirtilen veri alanları bağlayın. Aşağıdaki örnek bağlayan bir <xref:System.Windows.Controls.GridViewColumn> belirterek bir veri alanı nesnesine bir <xref:System.Windows.Data.Binding> için <xref:System.Windows.Controls.GridViewColumn.DisplayMemberBinding%2A> özelliği.  
  
 [!code-csharp[ListViewCode#GridViewColumnProperties](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewCode/CSharp/Window1.xaml.cs#gridviewcolumnproperties)]
 [!code-vb[ListViewCode#GridViewColumnProperties](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ListViewCode/visualbasic/window1.xaml.vb#gridviewcolumnproperties)]
 [!code-xaml[ListViewCode#GridViewColumnProperties](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewCode/CSharp/Window1.xaml#gridviewcolumnproperties)]  
  
 Ayrıca belirtebileceğiniz bir <xref:System.Windows.Data.Binding> parçası olarak bir <xref:System.Windows.DataTemplate> bir sütundaki hücrelerinin stilini belirlemek için kullandığınız tanımı. Aşağıdaki örnekte, <xref:System.Windows.DataTemplate> ile tanımlanan bir <xref:System.Windows.ResourceKey> ayarlar <xref:System.Windows.Data.Binding> için bir <xref:System.Windows.Controls.GridViewColumn>. Bu örnekte tanımlamaz Not <xref:System.Windows.Controls.GridViewColumn.DisplayMemberBinding%2A> Bunun yapılması, bu nedenle tarafından belirtilen bağlama geçersiz kılar çünkü <xref:System.Windows.DataTemplate>.  
  
 [!code-xaml[ListViewTemplate#GridViewCellTemplate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewTemplate/CS/window1.xaml#gridviewcelltemplate)]  
  
 [!code-xaml[ListViewTemplate#CellTemplateProperty](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewTemplate/CS/window1.xaml#celltemplateproperty)]  
  
<a name="StylingaListView"></a>   
## <a name="styling-a-listview-that-implements-a-gridview"></a>GridView Uygulayan ListView bir stil uygulama  
 <xref:System.Windows.Controls.ListView> Denetimi içeren <xref:System.Windows.Controls.ListViewItem> görüntülenecek veri öğelerini temsil eden nesneleri. İçerik ve veri öğelerinin stilini tanımlamak için aşağıdaki özellikleri kullanabilirsiniz:  
  
-   Üzerinde <xref:System.Windows.Controls.ListView> denetlemek, kullanın <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A>, <xref:System.Windows.Controls.ItemsControl.ItemTemplateSelector%2A>, ve <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> özellikleri.  
  
-   Üzerinde <xref:System.Windows.Controls.ListViewItem> denetlemek, kullanın <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> ve <xref:System.Windows.Controls.ContentControl.ContentTemplateSelector%2A> özellikleri.  
  
 Hücrelerde arasında hizalama sorunları önlemek için bir <xref:System.Windows.Controls.GridView>, kullanmayın <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> özellikleri ayarlamak veya içindeki bir öğenin genişliğini etkiler içerik eklemek için bir <xref:System.Windows.Controls.ListView>. Ayarladığınızda gibi bir hizalama sorun ortaya çıkabilir <xref:System.Windows.FrameworkElement.Margin%2A> özelliğinde <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A>. Özellikleri belirtin veya öğe genişliğini etkiler içeriği tanımlamak için bir <xref:System.Windows.Controls.GridView>, özelliklerini kullanmak <xref:System.Windows.Controls.GridView> sınıfı ve ilişkili sınıflarının gibi <xref:System.Windows.Controls.GridViewColumn>.  
  
 Nasıl kullanılacağı hakkında daha fazla bilgi için <xref:System.Windows.Controls.GridView> ve destekleyici sınıflarının [GridView genel bakışı](../../../../docs/framework/wpf/controls/gridview-overview.md).  
  
 Tanımlarsanız bir <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> için bir <xref:System.Windows.Controls.ListView> denetleyen ve ayrıca tanımlayan bir <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A>, eklemeniz gerekir bir <xref:System.Windows.Controls.ContentPresenter> sırayla stilde <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> düzgün çalışması için.  
  
 Kullanmayın <xref:System.Windows.Controls.Control.HorizontalContentAlignment%2A> ve <xref:System.Windows.Controls.Control.VerticalContentAlignment%2A> özelliklerini <xref:System.Windows.Controls.ListView> kullanılarak görüntülenen içerik bir <xref:System.Windows.Controls.GridView>. Bir sütunda içeriği hizalaması belirtmek için bir <xref:System.Windows.Controls.GridView>, tanımlayan bir <xref:System.Windows.Controls.GridViewColumn.CellTemplate%2A>.  
  
<a name="UsingtheSameViewMoreThanOnce"></a>   
## <a name="sharing-the-same-view-mode"></a>Aynı görünüm modunu paylaşma  
 İki <xref:System.Windows.Controls.ListView> denetimleri, aynı anda aynı görünüm modu paylaşamaz. Birden fazla ile aynı görünüm modunu kullanmayı denerseniz <xref:System.Windows.Controls.ListView> denetimi, bir özel durum oluşur.  
  
 Aynı anda birden fazla tarafından kullanılan bir görünüm modu belirtmek için <xref:System.Windows.Controls.ListView>, şablon veya stil kullanın. Görünüm olarak tanımlamak nasıl bir örnek için <xref:System.Windows.FrameworkElement.Resources%2A>, bkz: [birden çok örneği ile ListView](https://go.microsoft.com/fwlink/?LinkID=160013).  
  
<a name="CreatingaCustomView"></a>   
## <a name="creating-a-custom-view-mode"></a>Özel Görünüm modu oluşturma  
 Özelleştirilmiş görünümleri gibi <xref:System.Windows.Controls.GridView> türetilmiştir <xref:System.Windows.Controls.ViewBase> soyut olarak temsil edilen veri öğelerini görüntülemek için araçlar sağlar sınıfını <xref:System.Windows.Controls.ListViewItem> nesneleri.  
  
 Özel Görünüm modu örneği için bkz: [birden çok örneği ile ListView](https://go.microsoft.com/fwlink/?LinkID=160013).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Controls.GridView>  
 <xref:System.Windows.Controls.ListView>  
 <xref:System.Windows.Controls.ListViewItem>  
 <xref:System.Windows.Data.Binding>  
 [GridView Genel Bakış](../../../../docs/framework/wpf/controls/gridview-overview.md)  
 [Nasıl Yapılır Konuları](../../../../docs/framework/wpf/controls/listview-how-to-topics.md)  
 [Denetimler](../../../../docs/framework/wpf/advanced/optimizing-performance-controls.md)
