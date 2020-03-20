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
ms.openlocfilehash: 2f336d1eb8dcdfec3c3c8059ba865147c6b6c825
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187514"
---
# <a name="listview-overview"></a>ListView Genel Bakışı
Denetim, <xref:System.Windows.Controls.ListView> farklı düzenlerde veya görünümlerde bir veri öğesi kümesini görüntülemek için altyapı sağlar. Örneğin, bir kullanıcı bir tabloda veri öğelerini görüntülemek ve sütunlarını sıralamak isteyebilir.  

<a name="WhatisaListView"></a>
## <a name="what-is-a-listview"></a>ListView Nedir?  
 Denetim, <xref:System.Windows.Controls.ListView> 'den <xref:System.Windows.Controls.ItemsControl> <xref:System.Windows.Controls.ListBox>türetilen bir denetimdir. Genellikle, öğeleri bir veri koleksiyonunun üyeleridir ve <xref:System.Windows.Controls.ListViewItem> nesne olarak temsil edilir. A <xref:System.Windows.Controls.ListViewItem> a'dır <xref:System.Windows.Controls.ContentControl> ve yalnızca tek bir alt öğe içerebilir. Ancak, bu alt öğe herhangi bir görsel öğe olabilir.  
  
<a name="DefiningaListViewView"></a>
## <a name="defining-a-view-mode-for-a-listview"></a>ListView için Görünüm Modu Tanımlama  
 Denetimin <xref:System.Windows.Controls.ListView> içeriği için bir görünüm modu belirtmek <xref:System.Windows.Controls.ListView.View%2A> için özelliği ayarlarsınız. [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] Sağlayan bir görünüm <xref:System.Windows.Controls.GridView>modu, özelleştirilebilir sütunlar olan bir tabloda veri öğeleri koleksiyonu görüntüler.  
  
 Aşağıdaki örnek, çalışan bilgilerini <xref:System.Windows.Controls.GridView> görüntüleyen bir <xref:System.Windows.Controls.ListView> denetim için a'nın nasıl tanımlanır gösteriş yapılacağını gösterir.  
  
 [!code-xaml[ListViewCode#ListViewEmployee](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewCode/CSharp/Window1.xaml#listviewemployee)]  
  
 Aşağıdaki resimde, önceki örnekiçin verilerin nasıl göründüğü gösterilmektedir.  
  
 ![GridView çıktılı bir ListView gösteren ekran görüntüsü.](./media/gridview-overview/listview-gridview-output.jpg)  
  
 <xref:System.Windows.Controls.ViewBase> Sınıftan devralan bir sınıf tanımlayarak özel bir görünüm modu oluşturabilirsiniz. Sınıf, <xref:System.Windows.Controls.ViewBase> özel bir görünüm oluşturmak için gereken altyapıyı sağlar. Özel görünüm oluşturma hakkında daha fazla bilgi için, [bkz.](how-to-create-a-custom-view-mode-for-a-listview.md)  
  
<a name="BindingDatatoaListView"></a>
## <a name="binding-data-to-a-listview"></a>Verileri ListView'a Bağlama  
 Denetim <xref:System.Windows.Controls.ListView> <xref:System.Windows.Controls.ItemsControl.Items%2A> için <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> öğeleri belirtmek için ve özellikleri kullanın. Aşağıdaki örnek, <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> özelliği . `EmployeeInfoDataSource`  
  
 [!code-xaml[ListViewCode#ItemsSource](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewCode/CSharp/Window1.xaml#itemssource)]  
  
 Bir <xref:System.Windows.Controls.GridView>, <xref:System.Windows.Controls.GridViewColumn> nesneler belirtilen veri alanlarına bağlanır. Aşağıdaki örnek, <xref:System.Windows.Controls.GridViewColumn> <xref:System.Windows.Data.Binding> <xref:System.Windows.Controls.GridViewColumn.DisplayMemberBinding%2A> bir nesneyi bir veri alanına bir özellik için a belirterek bağlar.  
  
 [!code-csharp[ListViewCode#GridViewColumnProperties](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewCode/CSharp/Window1.xaml.cs#gridviewcolumnproperties)]
 [!code-vb[ListViewCode#GridViewColumnProperties](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ListViewCode/visualbasic/window1.xaml.vb#gridviewcolumnproperties)]
 [!code-xaml[ListViewCode#GridViewColumnProperties](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewCode/CSharp/Window1.xaml#gridviewcolumnproperties)]  
  
 Bir sütundaki <xref:System.Windows.Data.Binding> hücreleri stillemek <xref:System.Windows.DataTemplate> için kullandığınız tanımın bir parçası olarak da a belirtebilirsiniz. Aşağıdaki örnekte, <xref:System.Windows.DataTemplate> bir <xref:System.Windows.ResourceKey> kümesle <xref:System.Windows.Data.Binding> tanımlanan bir <xref:System.Windows.Controls.GridViewColumn>. Bu örneğin, çünkü bunu <xref:System.Windows.Controls.GridViewColumn.DisplayMemberBinding%2A> yapmak tarafından <xref:System.Windows.DataTemplate>belirtilen bağlama geçersiz kılar çünkü tanımlamaz unutmayın.  
  
 [!code-xaml[ListViewTemplate#GridViewCellTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewTemplate/CS/window1.xaml#gridviewcelltemplate)]  
  
 [!code-xaml[ListViewTemplate#CellTemplateProperty](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewTemplate/CS/window1.xaml#celltemplateproperty)]  
  
<a name="StylingaListView"></a>
## <a name="styling-a-listview-that-implements-a-gridview"></a>GridView Uygulayan Bir ListView'ı Şekillendirme  
 Denetim, <xref:System.Windows.Controls.ListView> <xref:System.Windows.Controls.ListViewItem> görüntülenen veri öğelerini temsil eden nesneler içerir. Veri öğelerinin içeriğini ve stilini tanımlamak için aşağıdaki özellikleri kullanabilirsiniz:  
  
- Denetimde <xref:System.Windows.Controls.ListView> <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A>, ve <xref:System.Windows.Controls.ItemsControl.ItemTemplateSelector%2A> <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> özellikleri kullanın.  
  
- Denetimde, <xref:System.Windows.Controls.ListViewItem> ve <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> <xref:System.Windows.Controls.ContentControl.ContentTemplateSelector%2A> özellikleri kullanın.  
  
 Hücreler <xref:System.Windows.Controls.GridView>arasındaki hizalama sorunlarını önlemek <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> için, bir maddenin genişliğini etkileyen özellikleri ayarlamak veya <xref:System.Windows.Controls.ListView>içerik eklemek için kullanmayın. Örneğin, <xref:System.Windows.FrameworkElement.Margin%2A> özelliği <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A>. Özellikleri belirtmek veya bir <xref:System.Windows.Controls.GridView>maddedeki öğelerin genişliğini etkileyen içeriği <xref:System.Windows.Controls.GridView> tanımlamak için sınıfın ve <xref:System.Windows.Controls.GridViewColumn>ilgili sınıfların özelliklerini kullanın.  
  
 Nasıl kullanılacağı <xref:System.Windows.Controls.GridView> ve destekleyici sınıfları hakkında daha fazla bilgi için [GridView Genel Bakış'a](gridview-overview.md)bakın.  
  
 <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> Bir <xref:System.Windows.Controls.ListView> denetim için bir tanım ve <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A>aynı zamanda <xref:System.Windows.Controls.ContentPresenter> tanımlarsanız, doğru çalışması <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> için bir stili eklemeniz gerekir.  
  
 <xref:System.Windows.Controls.Control.HorizontalContentAlignment%2A> <xref:System.Windows.Controls.GridView>Bir <xref:System.Windows.Controls.Control.VerticalContentAlignment%2A> <xref:System.Windows.Controls.ListView> Bir sütundaki içeriğin hizalanmasını <xref:System.Windows.Controls.GridView>belirtmek için <xref:System.Windows.Controls.GridViewColumn.CellTemplate%2A>, bir .  
  
<a name="UsingtheSameViewMoreThanOnce"></a>
## <a name="sharing-the-same-view-mode"></a>Aynı Görünüm Modunu Paylaşma  
 İki <xref:System.Windows.Controls.ListView> denetim aynı anda aynı görünüm modunu paylaşamaz. Aynı görünüm modunu birden <xref:System.Windows.Controls.ListView> fazla denetimle kullanmaya çalışırsanız, bir özel durum oluşur.  
  
 Birden <xref:System.Windows.Controls.ListView>fazla kişi tarafından aynı anda kullanılabilen bir görünüm modu belirtmek için şablonlar veya stiller kullanın.
  
<a name="CreatingaCustomView"></a>
## <a name="creating-a-custom-view-mode"></a>Özel Görünüm Modu Oluşturma  
 Beğenmek gibi <xref:System.Windows.Controls.GridView> özelleştirilmiş <xref:System.Windows.Controls.ViewBase> görünümler, nesne olarak <xref:System.Windows.Controls.ListViewItem> temsil edilen veri öğelerini görüntülemek için araçlar sağlayan soyut sınıftan türetilmiştir.
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Controls.GridView>
- <xref:System.Windows.Controls.ListView>
- <xref:System.Windows.Controls.ListViewItem>
- <xref:System.Windows.Data.Binding>
- [GridView Genel Bakış](gridview-overview.md)
- [Nasıl Dır Konular](listview-how-to-topics.md)
- [Denetimler](../advanced/optimizing-performance-controls.md)
