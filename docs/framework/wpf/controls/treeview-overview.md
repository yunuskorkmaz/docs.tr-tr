---
title: TreeView Genel Bakışı
ms.date: 03/30/2017
helpviewer_keywords:
- expanding node [WPF]
- TreeView control [WPF], about TreeView control
- Control class [WPF], TreeView
ms.assetid: 62212512-5a5c-4864-949e-b6a6a3a52c02
ms.openlocfilehash: 267e870e13d26439e4fbcbba3c5741ff84cabe3c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187379"
---
# <a name="treeview-overview"></a>TreeView Genel Bakışı
Denetim, <xref:System.Windows.Controls.TreeView> katlanabilir düğümler kullanarak hiyerarşik bir yapıdaki bilgileri görüntülemek için bir yol sağlar. Bu konu, <xref:System.Windows.Controls.TreeView> denetimleri ve denetimleri tanır <xref:System.Windows.Controls.TreeViewItem> ve bunların kullanımına basit örnekler sağlar.  

<a name="Simple_TreeView_Control"></a>
## <a name="what-is-a-treeview"></a>TreeView nedir?  
 <xref:System.Windows.Controls.TreeView>denetimleri <xref:System.Windows.Controls.ItemsControl> kullanarak <xref:System.Windows.Controls.TreeViewItem> öğeleri iç içe bir olan bir. Aşağıdaki örnekte bir <xref:System.Windows.Controls.TreeView>.  
  
 [!code-xaml[TreeViewSnips#EmbeddedTVIs](~/samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSnips/CSharp/Window1.xaml#embeddedtvis)]  
  
<a name="Creating_a_TreeView"></a>
## <a name="creating-a-treeview"></a>TreeView oluşturma  
 Denetim, <xref:System.Windows.Controls.TreeView> denetimler hiyerarşisi <xref:System.Windows.Controls.TreeViewItem> içerir. <xref:System.Windows.Controls.TreeViewItem> Denetim, a <xref:System.Windows.Controls.HeaderedItemsControl> ve <xref:System.Windows.Controls.HeaderedItemsControl.Header%2A> koleksiyonu <xref:System.Windows.Controls.ItemsControl.Items%2A> olan bir denetimdir.  
  
 A'yı <xref:System.Windows.Controls.TreeView> kullanarak [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]tanımlıyorsanız, denetimin <xref:System.Windows.Controls.HeaderedItemsControl.Header%2A> <xref:System.Windows.Controls.TreeViewItem> içeriğini ve koleksiyonunu oluşturan öğeleri açıkça tanımlayabilirsiniz. Önceki resimde bu yöntemi göstermektedir.  
  
 <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> Ayrıca bir veri kaynağı olarak belirtebilir <xref:System.Windows.Controls.HeaderedItemsControl.HeaderTemplate%2A> ve <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> daha <xref:System.Windows.Controls.TreeViewItem> sonra bir belirtebilir ve içeriği tanımlamak için.  
  
 Denetimin <xref:System.Windows.Controls.TreeViewItem> düzenini tanımlamak için nesneleri <xref:System.Windows.HierarchicalDataTemplate> de kullanabilirsiniz. Daha fazla bilgi ve örnek için [Bkz. SelectedValue, SelectedValuePath ve SelectedItem'i kullan.](how-to-use-selectedvalue-selectedvaluepath-and-selecteditem.md)  
  
 Bir öğe denetim <xref:System.Windows.Controls.TreeViewItem> değilse, <xref:System.Windows.Controls.TreeViewItem> <xref:System.Windows.Controls.TreeView> denetim görüntülendiğinde otomatik olarak bir denetim tarafından kapatılır.  
  
<a name="Expanding_and_Collapsing_a_TreeViewItem"></a>
## <a name="expanding-and-collapsing-a-treeviewitem"></a>Bir TreeViewItem'i Genişletme ve Daraltma  
 Kullanıcı bir <xref:System.Windows.Controls.TreeViewItem>genişletirse, <xref:System.Windows.Controls.TreeViewItem.IsExpanded%2A> özellik `true`. Ayrıca, özelliği `true` (genişletme) veya (daraltma) olarak ayarlayarak `false` herhangi bir doğrudan kullanıcı eylemi olmadan bir <xref:System.Windows.Controls.TreeViewItem> özelliği genişletebilir veya daraltabilirsiniz. <xref:System.Windows.Controls.TreeViewItem.IsExpanded%2A> Bu özellik değiştiğinde, bir <xref:System.Windows.Controls.TreeViewItem.Expanded> veya <xref:System.Windows.Controls.TreeViewItem.Collapsed> olay oluşur.  
  
 <xref:System.Windows.FrameworkElement.BringIntoView%2A> Yöntem denetime <xref:System.Windows.Controls.TreeViewItem> çağrıldığında, <xref:System.Windows.Controls.TreeViewItem> üst <xref:System.Windows.Controls.TreeViewItem> denetimleri genişletilir. A <xref:System.Windows.Controls.TreeViewItem> görünür veya kısmen görünmüyorsa, <xref:System.Windows.Controls.TreeView> parşömenler görünür hale getirmek için.  
  
<a name="TreeViewItem_Selection"></a>
## <a name="treeviewitem-selection"></a>TreeViewItem Seçimi  
 Bir kullanıcı onu <xref:System.Windows.Controls.TreeViewItem> seçmek için bir <xref:System.Windows.Controls.TreeViewItem.Selected> denetimi tıklattığında, <xref:System.Windows.Controls.TreeViewItem.IsSelected%2A> olay oluşur `true`ve özelliği . Aynı <xref:System.Windows.Controls.TreeViewItem> zamanda <xref:System.Windows.Controls.TreeView.SelectedItem%2A> <xref:System.Windows.Controls.TreeView> kontrol olur. <xref:System.Windows.Controls.TreeViewItem> Tam tersine, seçim bir denetimden <xref:System.Windows.Controls.TreeViewItem.Unselected> değiştiğinde, olayı <xref:System.Windows.Controls.TreeViewItem.IsSelected%2A> oluşur ve `false`özelliği .  
  
 <xref:System.Windows.Controls.TreeView> Denetimdeki <xref:System.Windows.Controls.TreeView.SelectedItem%2A> özellik salt okunur bir özelliktir; bu nedenle, açıkça ayarlayamazsınız. Kullanıcı <xref:System.Windows.Controls.TreeView.SelectedItem%2A> bir <xref:System.Windows.Controls.TreeViewItem> denetimi tıklattığında veya <xref:System.Windows.Controls.TreeViewItem.IsSelected%2A> özellik `true` <xref:System.Windows.Controls.TreeViewItem> denetimde ayarlandığında özellik ayarlanır.  
  
 Bir <xref:System.Windows.Controls.TreeView.SelectedItem%2A> <xref:System.Windows.Controls.TreeView.SelectedValuePath%2A> ' nin <xref:System.Windows.Controls.TreeView.SelectedValue%2A> bir belirtinimi için özelliği kullanın Daha fazla bilgi için [Bkz. SelectedValue, SelectedValuePath ve SelectedItem'i kullan.](how-to-use-selectedvalue-selectedvaluepath-and-selecteditem.md)  
  
 Seçili <xref:System.Windows.Controls.TreeViewItem> bir değişikliğin ne <xref:System.Windows.Controls.TreeView.SelectedItemChanged> zaman değiştiğini belirlemek için olay üzerinde bir olay işleyicisi kaydedebilirsiniz. Olay işleyicisine sağlanan, önceki seçim <xref:System.Windows.RoutedPropertyChangedEventArgs%601.NewValue%2A> <xref:System.Windows.RoutedPropertyChangedEventArgs%601.OldValue%2A>olan , geçerli seçim olan , <xref:System.Windows.RoutedPropertyChangedEventArgs%601> Uygulama veya `null` kullanıcı önceki veya geçerli bir seçim yapmadıysa, değer olabilir.  
  
<a name="TreeView_Style"></a>
## <a name="treeview-style"></a>TreeView Stili  
 Denetim <xref:System.Windows.Controls.TreeView> için varsayılan stil, denetim <xref:System.Windows.Controls.StackPanel> içeren <xref:System.Windows.Controls.ScrollViewer> bir nesnenin içine yerleştirir. Bir <xref:System.Windows.Controls.TreeView>, <xref:System.Windows.FrameworkElement.Width%2A> bu <xref:System.Windows.FrameworkElement.Height%2A> değerler için ve özelliklerini <xref:System.Windows.Controls.StackPanel> <xref:System.Windows.Controls.TreeView>ayarladığınızda, bu değerler . Görüntülenecek içerik görüntü alanından daha büyükse, kullanıcının <xref:System.Windows.Controls.ScrollViewer> <xref:System.Windows.Controls.TreeView> içerikte kaydırabilmesi için otomatik olarak görüntülenir.  
  
 Denetimgörünümünü <xref:System.Windows.Controls.TreeViewItem> özelleştirmek için <xref:System.Windows.FrameworkElement.Style%2A> özelliği özel <xref:System.Windows.Style>olarak ayarlayın.  
  
 Aşağıdaki <xref:System.Windows.Controls.Control.Foreground%2A> örnekte, bir <xref:System.Windows.Controls.Control.FontSize%2A> <xref:System.Windows.Controls.TreeViewItem> <xref:System.Windows.FrameworkElement.Style%2A>denetim için özellik değerlerinin nasıl ayarlanılmayı gösterir.  
  
 [!code-xaml[TreeViewSimple#8](~/samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSimple/CS/Window1.xaml#8)]  
  
<a name="Adding_Images_and_oOther_Content_to_TreeView_Items"></a>
## <a name="adding-images-and-other-content-to-treeview-items"></a>TreeView Öğelerine Resim ve Diğer İçerik Ekleme  
 Bir 'nin içeriğine <xref:System.Windows.Controls.HeaderedItemsControl.Header%2A> birden fazla <xref:System.Windows.Controls.TreeViewItem>nesne ekleyebilirsiniz. <xref:System.Windows.Controls.HeaderedItemsControl.Header%2A> İçeriye birden çok nesne eklemek için, nesneleri bir <xref:System.Windows.Controls.Panel> düzen <xref:System.Windows.Controls.StackPanel>denetiminin içine içine ekleyin.  
  
 Aşağıdaki örnek, a'nın <xref:System.Windows.Controls.HeaderedItemsControl.Header%2A> <xref:System.Windows.Controls.TreeViewItem> bir <xref:System.Windows.Controls.CheckBox> <xref:System.Windows.Controls.TextBlock> denetimde <xref:System.Windows.Controls.DockPanel> nasıl tanımlandığını gösterir.  
  
 [!code-xaml[TreeViewSnips#TVIHeader](~/samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSnips/CSharp/Window1.xaml#tviheader)]  
  
 Aşağıdaki örnek, bir ve <xref:System.Windows.DataTemplate> bir <xref:System.Windows.Controls.Image> denetimi <xref:System.Windows.Controls.TextBlock> niçin kapalı <xref:System.Windows.Controls.DockPanel> bir içeren bir tanımlamak için gösterir. <xref:System.Windows.DataTemplate> A'yı ayarlamak için <xref:System.Windows.Controls.HeaderedItemsControl.HeaderTemplate%2A> <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> kullanabilirsiniz <xref:System.Windows.Controls.TreeViewItem>veya bir .  
  
 [!code-xaml[TreeViewDataBinding#6](~/samples/snippets/csharp/VS_Snippets_Wpf/TreeViewDataBinding/CSharp/Window1.xaml#6)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Controls.TreeView>
- <xref:System.Windows.Controls.TreeViewItem>
- [Nasıl Dır Konular](treeview-how-to-topics.md)
- [WPF İçerik Modeli](wpf-content-model.md)
