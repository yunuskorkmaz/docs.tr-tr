---
title: "ListView Genel Bakışı"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [WPF], ListView
- ListView controls [WPF], about ListView control
ms.assetid: 989e12b0-260e-4570-95c6-489284003ce2
caps.latest.revision: "25"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: e0886e387b6de34673cd4990ef8b61e08674b531
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="listview-overview"></a>ListView Genel Bakışı
<xref:System.Windows.Controls.ListView> Denetimi farklı düzenler veya görünümlerde veri öğeleri kümesini görüntülemek için altyapı sağlar. Örneğin, bir kullanıcı bir tabloda veri öğelerini görüntülemek ve sütunları sıralamak isteyebilir.  
  
  
<a name="WhatisaListView"></a>   
## <a name="what-is-a-listview"></a>ListView nedir?  
 <xref:System.Windows.Controls.ListView> Denetimi bir <xref:System.Windows.Controls.ItemsControl> öğesinden türetilen <xref:System.Windows.Controls.ListBox>. Genellikle, öğelerinden veri koleksiyonunun üyesi olan ve olarak temsil edilir <xref:System.Windows.Controls.ListViewItem> nesneleri. A <xref:System.Windows.Controls.ListViewItem> olan bir <xref:System.Windows.Controls.ContentControl> ve yalnızca tek bir alt öğe içermelidir. Ancak, bu alt öğe herhangi bir görsel öğe olabilir.  
  
<a name="DefiningaListViewView"></a>   
## <a name="defining-a-view-mode-for-a-listview"></a>ListView için bir görünüm modu tanımlama  
 İçeriği için görüntüleme modu belirtmek için bir <xref:System.Windows.Controls.ListView> denetim, ayarladığınız <xref:System.Windows.Controls.ListView.View%2A> özelliği. Bir görünüm modu, [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] sağlar olan <xref:System.Windows.Controls.GridView>, özelleştirilebilir sütunları olan bir tabloda veri öğeleri koleksiyonu görüntüler.  
  
 Aşağıdaki örnekte nasıl tanımlanacağı gösterilmektedir bir <xref:System.Windows.Controls.GridView> için bir <xref:System.Windows.Controls.ListView> çalışan bilgilerini görüntüleyen denetim.  
  
 [!code-xaml[ListViewCode#ListViewEmployee](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewCode/CSharp/Window1.xaml#listviewemployee)]  
  
 Aşağıdaki çizimde, önceki örnekte verinin nasıl göründüğünü gösterir.  
  
 ![GridView çıkışıyla ListView](../../../../docs/framework/wpf/controls/media/listviewgridview.JPG "ListViewGridView")  
  
 Öğesinden devralınan bir sınıf tanımlayarak özel görünüm modu oluşturabilirsiniz <xref:System.Windows.Controls.ViewBase> sınıfı. <xref:System.Windows.Controls.ViewBase> Sınıfı özel görünüm oluşturmak için gereken altyapıyı sağlar. Özel bir görünüm oluşturma hakkında daha fazla bilgi için bkz: [ListView için özel bir görünüm modu oluşturma](../../../../docs/framework/wpf/controls/how-to-create-a-custom-view-mode-for-a-listview.md).  
  
<a name="BindingDatatoaListView"></a>   
## <a name="binding-data-to-a-listview"></a>ListView veri bağlama  
 Kullanım <xref:System.Windows.Controls.ItemsControl.Items%2A> ve <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> özellikler öğelerini belirtmek için bir <xref:System.Windows.Controls.ListView> denetim. Aşağıdaki örnek kümeleri <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> çağrılan bir veri toplama özelliğine `EmployeeInfoDataSource`.  
  
 [!code-xaml[ListViewCode#ItemsSource](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewCode/CSharp/Window1.xaml#itemssource)]  
  
 İçinde bir <xref:System.Windows.Controls.GridView>, <xref:System.Windows.Controls.GridViewColumn> nesneleri bağlamak için belirtilen veri alanları. Aşağıdaki örnek bağlar bir <xref:System.Windows.Controls.GridViewColumn> belirterek bir veri alanı nesnesine bir <xref:System.Windows.Data.Binding> için <xref:System.Windows.Controls.GridViewColumn.DisplayMemberBinding%2A> özelliği.  
  
 [!code-csharp[ListViewCode#GridViewColumnProperties](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewCode/CSharp/Window1.xaml.cs#gridviewcolumnproperties)]
 [!code-vb[ListViewCode#GridViewColumnProperties](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ListViewCode/visualbasic/window1.xaml.vb#gridviewcolumnproperties)]
 [!code-xaml[ListViewCode#GridViewColumnProperties](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewCode/CSharp/Window1.xaml#gridviewcolumnproperties)]  
  
 Ayrıca belirtebilirsiniz bir <xref:System.Windows.Data.Binding> parçası olarak bir <xref:System.Windows.DataTemplate> sütunda hücrelerinin stilini belirlemek için kullandığınız tanımı. Aşağıdaki örnekte, <xref:System.Windows.DataTemplate> ile tanımlanan bir <xref:System.Windows.ResourceKey> ayarlar <xref:System.Windows.Data.Binding> için bir <xref:System.Windows.Controls.GridViewColumn>. Bu örnek tanımlamaz Not <xref:System.Windows.Controls.GridViewColumn.DisplayMemberBinding%2A> bunun nedenle tarafından belirtilen bağlama kıldığından <xref:System.Windows.DataTemplate>.  
  
 [!code-xaml[ListViewTemplate#GridViewCellTemplate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewTemplate/CS/window1.xaml#gridviewcelltemplate)]  
  
 [!code-xaml[ListViewTemplate#CellTemplateProperty](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewTemplate/CS/window1.xaml#celltemplateproperty)]  
  
<a name="StylingaListView"></a>   
## <a name="styling-a-listview-that-implements-a-gridview"></a>GridView Uygulayan ListView, stil oluşturma  
 <xref:System.Windows.Controls.ListView> Denetimi içeren <xref:System.Windows.Controls.ListViewItem> görüntülenen veri öğelerini temsil eden nesne. İçerik ve stil veri öğeleri tanımlamak için aşağıdaki özellikleri kullanabilirsiniz:  
  
-   Üzerinde <xref:System.Windows.Controls.ListView> denetlemek, kullanın <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A>, <xref:System.Windows.Controls.ItemsControl.ItemTemplateSelector%2A>, ve <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> özellikleri.  
  
-   Üzerinde <xref:System.Windows.Controls.ListViewItem> denetlemek, kullanın <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> ve <xref:System.Windows.Controls.ContentControl.ContentTemplateSelector%2A> özellikleri.  
  
 Hücrelerde arasındaki hizalama sorunlarını önlemek için bir <xref:System.Windows.Controls.GridView>, kullanmayın <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> özelliklerini ayarlamak veya bir öğenin genişliğini etkiler içeriği eklemek için bir <xref:System.Windows.Controls.ListView>. Örneğin, ayarlarken bir hizalama sorun ortaya çıkabilir <xref:System.Windows.FrameworkElement.Margin%2A> özelliğinde <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A>. Özellikleri belirtin veya içindeki öğelerin genişliğini etkiler içerik tanımlamak için bir <xref:System.Windows.Controls.GridView>, özelliklerini kullanmak <xref:System.Windows.Controls.GridView> sınıfı ve onun ilişkili sınıflar gibi <xref:System.Windows.Controls.GridViewColumn>.  
  
 Nasıl kullanılacağı hakkında daha fazla bilgi için <xref:System.Windows.Controls.GridView> ve destekleyici sınıflarının [GridView genel bakış](../../../../docs/framework/wpf/controls/gridview-overview.md).  
  
 Tanımlarsanız bir <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> için bir <xref:System.Windows.Controls.ListView> denetleyen ve ayrıca tanımlayan bir <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A>, eklemelisiniz bir <xref:System.Windows.Controls.ContentPresenter> sırayla stilde <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> düzgün çalışması için.  
  
 Kullanmayın <xref:System.Windows.Controls.Control.HorizontalContentAlignment%2A> ve <xref:System.Windows.Controls.Control.VerticalContentAlignment%2A> özelliklerini <xref:System.Windows.Controls.ListView> kullanılarak görüntülenen içeriği bir <xref:System.Windows.Controls.GridView>. İçerik hizalamasını sütununda belirtmek için bir <xref:System.Windows.Controls.GridView>, tanımlayan bir <xref:System.Windows.Controls.GridViewColumn.CellTemplate%2A>.  
  
<a name="UsingtheSameViewMoreThanOnce"></a>   
## <a name="sharing-the-same-view-mode"></a>Aynı görünüm modunu paylaşma  
 İki <xref:System.Windows.Controls.ListView> denetimleri aynı anda aynı görünüm modunu paylaşamaz. Birden fazla ile aynı görünüm modunu kullanmayı denerseniz <xref:System.Windows.Controls.ListView> denetlemek, bir özel durum oluşur.  
  
 Aynı anda birden fazla tarafından kullanılan görüntüleme modunu belirtmek için <xref:System.Windows.Controls.ListView>, şablonlar veya stilleri kullanın. Bir örnek olarak görünümlerini tanımlamak nasıl <xref:System.Windows.FrameworkElement.Resources%2A>, bkz: [ListView birden çok görünümler örnek ile](http://go.microsoft.com/fwlink/?LinkID=160013).  
  
<a name="CreatingaCustomView"></a>   
## <a name="creating-a-custom-view-mode"></a>Bir özel görünüm modu oluşturma  
 Gibi özelleştirilmiş görünümler <xref:System.Windows.Controls.GridView> türetilmiş <xref:System.Windows.Controls.ViewBase> soyut olarak temsil edilir veri öğelerini görüntülemek için araçlar sağlayan sınıf <xref:System.Windows.Controls.ListViewItem> nesneleri.  
  
 Özel Görünüm modu örneği için bkz: [ListView birden çok görünümler örnek ile](http://go.microsoft.com/fwlink/?LinkID=160013).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Controls.GridView>  
 <xref:System.Windows.Controls.ListView>  
 <xref:System.Windows.Controls.ListViewItem>  
 <xref:System.Windows.Data.Binding>  
 [GridView genel bakış](../../../../docs/framework/wpf/controls/gridview-overview.md)  
 [Nasıl Yapılır Konuları](../../../../docs/framework/wpf/controls/listview-how-to-topics.md)  
 [Denetimleri](../../../../docs/framework/wpf/advanced/optimizing-performance-controls.md)
