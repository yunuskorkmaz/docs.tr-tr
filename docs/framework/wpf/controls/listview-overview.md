---
title: ListView Genel Bakışı
description: Farklı düzende veya görünümlerde veri öğelerini göstermek için altyapıyı sağlayan Windows Presentation Foundation ListView denetimi hakkında bilgi edinin.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [WPF], ListView
- ListView controls [WPF], about ListView control
ms.assetid: 989e12b0-260e-4570-95c6-489284003ce2
ms.openlocfilehash: 419c6216f0af696ec71e7607c79c2db637caa785
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87164562"
---
# <a name="listview-overview"></a>ListView Genel Bakışı
<xref:System.Windows.Controls.ListView>Denetim, farklı düzende veya görünümlerde bir dizi veri öğesi göstermek için altyapıyı sağlar. Örneğin, bir Kullanıcı bir tablodaki veri öğelerini ve ayrıca sütunlarını sıralamak isteyebilir.  

<a name="WhatisaListView"></a>
## <a name="what-is-a-listview"></a>ListView nedir?  
 <xref:System.Windows.Controls.ListView>Denetim, öğesinden türetilmiş bir ' dır <xref:System.Windows.Controls.ItemsControl> <xref:System.Windows.Controls.ListBox> . Genellikle, öğeleri bir veri koleksiyonunun üyeleridir ve nesneler olarak temsil edilir <xref:System.Windows.Controls.ListViewItem> . <xref:System.Windows.Controls.ListViewItem>, Bir <xref:System.Windows.Controls.ContentControl> öğesidir ve yalnızca tek bir alt öğe içerebilir. Ancak, bu alt öğe herhangi bir görsel öğe olabilir.  
  
<a name="DefiningaListViewView"></a>
## <a name="defining-a-view-mode-for-a-listview"></a>ListView için görünüm modunu tanımlama  
 Bir denetimin içeriği için bir görünüm modu belirtmek için <xref:System.Windows.Controls.ListView> <xref:System.Windows.Controls.ListView.View%2A> özelliğini ayarlarsınız. [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] <xref:System.Windows.Controls.GridView> Özelleştirilebilir sütunları olan bir tablodaki veri öğelerinin koleksiyonunu görüntüleyen bir görünüm modu.  
  
 Aşağıdaki örnek, <xref:System.Windows.Controls.GridView> çalışan bilgilerini görüntüleyen bir denetim için nasıl tanımlanacağını gösterir <xref:System.Windows.Controls.ListView> .  
  
 [!code-xaml[ListViewCode#ListViewEmployee](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewCode/CSharp/Window1.xaml#listviewemployee)]  
  
 Aşağıdaki çizimde, verilerin önceki örnekte nasıl göründüğü gösterilmektedir.  
  
 ![GridView çıkışıyla bir ListView gösteren ekran görüntüsü.](./media/gridview-overview/listview-gridview-output.jpg)  
  
 Sınıfından devralan bir sınıfı tanımlayarak özel bir görünüm modu oluşturabilirsiniz <xref:System.Windows.Controls.ViewBase> . <xref:System.Windows.Controls.ViewBase>Sınıfı, özel bir görünüm oluşturmak için ihtiyaç duyduğunuz altyapıyı sağlar. Özel görünüm oluşturma hakkında daha fazla bilgi için bkz. [ListView Için özel görünüm modu oluşturma](how-to-create-a-custom-view-mode-for-a-listview.md).  
  
<a name="BindingDatatoaListView"></a>
## <a name="binding-data-to-a-listview"></a>ListView 'a veri bağlama  
 <xref:System.Windows.Controls.ItemsControl.Items%2A> <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> Bir denetimin öğelerini belirtmek için ve özelliklerini kullanın <xref:System.Windows.Controls.ListView> . Aşağıdaki örnek, <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> özelliğini çağrılan bir veri koleksiyonuna ayarlar `EmployeeInfoDataSource` .  
  
 [!code-xaml[ListViewCode#ItemsSource](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewCode/CSharp/Window1.xaml#itemssource)]  
  
 ' De <xref:System.Windows.Controls.GridView> , <xref:System.Windows.Controls.GridViewColumn> nesneler belirtilen veri alanlarına bağlanır. Aşağıdaki örnek, <xref:System.Windows.Controls.GridViewColumn> özelliği için bir nesnesi belirterek bir nesneyi veri alanına bağlar <xref:System.Windows.Data.Binding> <xref:System.Windows.Controls.GridViewColumn.DisplayMemberBinding%2A> .  
  
 [!code-csharp[ListViewCode#GridViewColumnProperties](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewCode/CSharp/Window1.xaml.cs#gridviewcolumnproperties)]
 [!code-vb[ListViewCode#GridViewColumnProperties](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ListViewCode/visualbasic/window1.xaml.vb#gridviewcolumnproperties)]
 [!code-xaml[ListViewCode#GridViewColumnProperties](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewCode/CSharp/Window1.xaml#gridviewcolumnproperties)]  
  
 Ayrıca, bir <xref:System.Windows.Data.Binding> <xref:System.Windows.DataTemplate> sütundaki hücrelere stil eklemek için kullandığınız tanımın bir parçası olarak belirtebilirsiniz. Aşağıdaki örnekte, <xref:System.Windows.DataTemplate> için bir kümesi olarak tanımlanır <xref:System.Windows.ResourceKey> <xref:System.Windows.Data.Binding> <xref:System.Windows.Controls.GridViewColumn> . Bu örnek, <xref:System.Windows.Controls.GridViewColumn.DisplayMemberBinding%2A> tarafından belirtilen bağlamayı geçersiz kıldığından, bunu tanımlamaz <xref:System.Windows.DataTemplate> .  
  
 [!code-xaml[ListViewTemplate#GridViewCellTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewTemplate/CS/window1.xaml#gridviewcelltemplate)]  
  
 [!code-xaml[ListViewTemplate#CellTemplateProperty](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewTemplate/CS/window1.xaml#celltemplateproperty)]  
  
<a name="StylingaListView"></a>
## <a name="styling-a-listview-that-implements-a-gridview"></a>GridView Uygulayan ListView 'u Stillendirme  
 <xref:System.Windows.Controls.ListView>Denetim, <xref:System.Windows.Controls.ListViewItem> görüntülenen veri öğelerini temsil eden nesneleri içerir. Veri öğelerinin içeriğini ve stilini tanımlamak için aşağıdaki özellikleri kullanabilirsiniz:  
  
- Denetimde,, <xref:System.Windows.Controls.ListView> <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> <xref:System.Windows.Controls.ItemsControl.ItemTemplateSelector%2A> ve özelliklerini kullanın <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> .  
  
- <xref:System.Windows.Controls.ListViewItem>Denetimde <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> ve <xref:System.Windows.Controls.ContentControl.ContentTemplateSelector%2A> özelliklerini kullanın.  
  
 İçindeki hücreler arasındaki hizalama sorunlarından kaçınmak için, <xref:System.Windows.Controls.GridView> <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> özelliklerini ayarlamak veya içindeki bir öğenin genişliğini etkileyen içerik eklemek için kullanmayın <xref:System.Windows.Controls.ListView> . Örneğin, içinde özelliği ayarladığınızda bir hizalama sorunu ortaya çıkabilir <xref:System.Windows.FrameworkElement.Margin%2A> <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> . Özellikleri belirtmek veya içindeki öğelerin genişliğini etkileyen içerik tanımlamak için <xref:System.Windows.Controls.GridView> , <xref:System.Windows.Controls.GridView> sınıfının özelliklerini ve gibi ilgili sınıfları kullanın <xref:System.Windows.Controls.GridViewColumn> .  
  
 Ve destekleyici sınıflarının kullanımı hakkında daha fazla bilgi için <xref:System.Windows.Controls.GridView> bkz. [GridView Overview](gridview-overview.md).  
  
 Bir <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> Denetim için tanımlar <xref:System.Windows.Controls.ListView> ve ayrıca bir tanımlar <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> , doğru çalışması için stiline bir dahil etmeniz gerekir <xref:System.Windows.Controls.ContentPresenter> <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> .  
  
 <xref:System.Windows.Controls.Control.HorizontalContentAlignment%2A> <xref:System.Windows.Controls.Control.VerticalContentAlignment%2A> Kullanılarak görüntülenen içerik için ve özelliklerini kullanmayın <xref:System.Windows.Controls.ListView> <xref:System.Windows.Controls.GridView> . İçeriğinin bir sütununda hizalamasını belirtmek için <xref:System.Windows.Controls.GridView> bir tanımlayın <xref:System.Windows.Controls.GridViewColumn.CellTemplate%2A> .  
  
<a name="UsingtheSameViewMoreThanOnce"></a>
## <a name="sharing-the-same-view-mode"></a>Aynı görünüm modunu paylaşma  
 İki <xref:System.Windows.Controls.ListView> denetim aynı anda aynı görünüm modunu paylaşamaz. Aynı görünüm modunu birden fazla denetimle kullanmaya çalışırsanız <xref:System.Windows.Controls.ListView> , bir özel durum oluşur.  
  
 Aynı anda birden fazla tarafından kullanılabilen bir görünüm modu belirtmek için <xref:System.Windows.Controls.ListView> , şablonları veya stilleri kullanın.
  
<a name="CreatingaCustomView"></a>
## <a name="creating-a-custom-view-mode"></a>Özel görünüm modu oluşturma  
 Gibi özelleştirilmiş görünümler <xref:System.Windows.Controls.GridView> <xref:System.Windows.Controls.ViewBase> , nesne olarak temsil edilen veri öğelerini göstermek için araçlar sağlayan soyut sınıftan türetilir <xref:System.Windows.Controls.ListViewItem> .
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Controls.GridView>
- <xref:System.Windows.Controls.ListView>
- <xref:System.Windows.Controls.ListViewItem>
- <xref:System.Windows.Data.Binding>
- [GridView Genel Bakışı](gridview-overview.md)
- [Nasıl Yapılır Konuları](listview-how-to-topics.md)
- [Denetimler](../advanced/optimizing-performance-controls.md)
