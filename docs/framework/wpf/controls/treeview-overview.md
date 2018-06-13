---
title: TreeView Genel Bakışı
ms.date: 03/30/2017
helpviewer_keywords:
- expanding node [WPF]
- TreeView control [WPF], about TreeView control
- Control class [WPF], TreeView
ms.assetid: 62212512-5a5c-4864-949e-b6a6a3a52c02
ms.openlocfilehash: f8c49013bc34671ec590f0bd9f84a0f2cf3f9aaf
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33557790"
---
# <a name="treeview-overview"></a>TreeView Genel Bakışı
<xref:System.Windows.Controls.TreeView> Denetimi daraltılabilir düğümleri kullanarak hiyerarşik yapıda bilgileri görüntülemek için bir yol sağlar. Bu konu tanıtır <xref:System.Windows.Controls.TreeView> ve <xref:System.Windows.Controls.TreeViewItem> denetler ve bunların kullanımıyla basit örnekler sağlar.  
  
  
<a name="Simple_TreeView_Control"></a>   
## <a name="what-is-a-treeview"></a>TreeView nedir?  
 <xref:System.Windows.Controls.TreeView> olan bir <xref:System.Windows.Controls.ItemsControl> öğeleri kullanarak katmandan <xref:System.Windows.Controls.TreeViewItem> kontrol eder. Aşağıdaki örnekte bir <xref:System.Windows.Controls.TreeView>.  
  
 [!code-xaml[TreeViewSnips#EmbeddedTVIs](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSnips/CSharp/Window1.xaml#embeddedtvis)]  
  
<a name="Creating_a_TreeView"></a>   
## <a name="creating-a-treeview"></a>TreeView oluşturma  
 <xref:System.Windows.Controls.TreeView> Denetimi içeren bir hiyerarşiye <xref:System.Windows.Controls.TreeViewItem> kontrol eder. A <xref:System.Windows.Controls.TreeViewItem> denetimi bir <xref:System.Windows.Controls.HeaderedItemsControl> olan bir <xref:System.Windows.Controls.HeaderedItemsControl.Header%2A> ve bir <xref:System.Windows.Controls.ItemsControl.Items%2A> koleksiyonu.  
  
 Tanımlıyorsanız, bir <xref:System.Windows.Controls.TreeView> kullanarak [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], açıkça tanımlayabilirsiniz <xref:System.Windows.Controls.HeaderedItemsControl.Header%2A> içeriğini bir <xref:System.Windows.Controls.TreeViewItem> denetim ve koleksiyonu oluşturan öğeler. Önceki çizimde, bu yöntem gösterilmektedir.  
  
 Ayrıca belirtebilirsiniz bir <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> bir veri kaynağı ve ardından belirtin bir <xref:System.Windows.Controls.HeaderedItemsControl.HeaderTemplate%2A> ve <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> tanımlamak için <xref:System.Windows.Controls.TreeViewItem> içeriği.  
  
 Düzenini tanımlamak için bir <xref:System.Windows.Controls.TreeViewItem> denetimi de kullanabilirsiniz <xref:System.Windows.HierarchicalDataTemplate> nesneleri. Daha fazla bilgi ve bir örnek için bkz: [kullanım SelectedValue, SelectedValuePath ve SelectedItem](../../../../docs/framework/wpf/controls/how-to-use-selectedvalue-selectedvaluepath-and-selecteditem.md).  
  
 Bir öğe değilse, bir <xref:System.Windows.Controls.TreeViewItem> denetimi, bunu otomatik olarak içine alınır tarafından bir <xref:System.Windows.Controls.TreeViewItem> denetimi <xref:System.Windows.Controls.TreeView> denetim görüntülenir.  
  
<a name="Expanding_and_Collapsing_a_TreeViewItem"></a>   
## <a name="expanding-and-collapsing-a-treeviewitem"></a>Genişletme ve daraltma TreeViewItem  
 Kullanıcı genişletir, bir <xref:System.Windows.Controls.TreeViewItem>, <xref:System.Windows.Controls.TreeViewItem.IsExpanded%2A> özelliği ayarlanmış `true`. Ayrıca genişletebilir veya daraltabilirsiniz bir <xref:System.Windows.Controls.TreeViewItem> ayarlayarak doğrudan kullanıcı eylemi olmadan <xref:System.Windows.Controls.TreeViewItem.IsExpanded%2A> özelliğine `true` (expand) veya `false` (daraltma). Bu özellik değiştiğinde bir <xref:System.Windows.Controls.TreeViewItem.Expanded> veya <xref:System.Windows.Controls.TreeViewItem.Collapsed> olayı oluşur.  
  
 Zaman <xref:System.Windows.FrameworkElement.BringIntoView%2A> yöntemi çağrıldığında bir <xref:System.Windows.Controls.TreeViewItem> denetimi <xref:System.Windows.Controls.TreeViewItem> ve kendi üst <xref:System.Windows.Controls.TreeViewItem> denetimleri genişletin. Varsa bir <xref:System.Windows.Controls.TreeViewItem> görünür veya kısmen görünür değil <xref:System.Windows.Controls.TreeView> görünür yapmak için kayar.  
  
<a name="TreeViewItem_Selection"></a>   
## <a name="treeviewitem-selection"></a>TreeViewItem seçimi  
 Bir kullanıcı tıkladığında bir <xref:System.Windows.Controls.TreeViewItem> , seçmek için Denetim <xref:System.Windows.Controls.TreeViewItem.Selected> olayı oluşur ve kendi <xref:System.Windows.Controls.TreeViewItem.IsSelected%2A> özelliği ayarlanmış `true`. <xref:System.Windows.Controls.TreeViewItem> Haline <xref:System.Windows.Controls.TreeView.SelectedItem%2A> , <xref:System.Windows.Controls.TreeView> denetim. Buna karşılık, seçim değiştiğinde alanından bir <xref:System.Windows.Controls.TreeViewItem> denetim, kendi <xref:System.Windows.Controls.TreeViewItem.Unselected> olayı oluşur ve kendi <xref:System.Windows.Controls.TreeViewItem.IsSelected%2A> özelliği ayarlanmış `false`.  
  
 <xref:System.Windows.Controls.TreeView.SelectedItem%2A> Özellikte <xref:System.Windows.Controls.TreeView> denetim özelliği salt okunur; bu nedenle, açıkça bunu göremezsiniz. <xref:System.Windows.Controls.TreeView.SelectedItem%2A> Özellik ayarlanmışsa üzerinde kullanıcı bir <xref:System.Windows.Controls.TreeViewItem> denetim veya ne zaman <xref:System.Windows.Controls.TreeViewItem.IsSelected%2A> özelliği ayarlanmış `true` üzerinde <xref:System.Windows.Controls.TreeViewItem> denetim.  
  
 Kullanım <xref:System.Windows.Controls.TreeView.SelectedValuePath%2A> özelliği belirtmek için bir <xref:System.Windows.Controls.TreeView.SelectedValue%2A> , bir <xref:System.Windows.Controls.TreeView.SelectedItem%2A>. Daha fazla bilgi için bkz: [kullanım SelectedValue, SelectedValuePath ve SelectedItem](../../../../docs/framework/wpf/controls/how-to-use-selectedvalue-selectedvaluepath-and-selecteditem.md).  
  
 Üzerinde bir olay işleyicisi kaydedebilirsiniz <xref:System.Windows.Controls.TreeView.SelectedItemChanged> seçili belirlemek için olay <xref:System.Windows.Controls.TreeViewItem> değişiklikler. <xref:System.Windows.RoutedPropertyChangedEventArgs%601> Olay işleyicisi belirtir sağlanan olan <xref:System.Windows.RoutedPropertyChangedEventArgs%601.OldValue%2A>, önceki seçimi olduğu ve <xref:System.Windows.RoutedPropertyChangedEventArgs%601.NewValue%2A>, geçerli seçim olduğu. Her iki değer `null` uygulama veya kullanıcıya önceki ya da geçerli bir seçim değil yapmadığında.  
  
<a name="TreeView_Style"></a>   
## <a name="treeview-style"></a>TreeView Stili  
 Varsayılan stilini bir <xref:System.Windows.Controls.TreeView> denetim yerleştirir içinde bir <xref:System.Windows.Controls.StackPanel> içeren nesne bir <xref:System.Windows.Controls.ScrollViewer> denetim. Ayarladığınızda <xref:System.Windows.FrameworkElement.Width%2A> ve <xref:System.Windows.FrameworkElement.Height%2A> özelliklerini bir <xref:System.Windows.Controls.TreeView>, bu değerleri boyutuna kullanılan <xref:System.Windows.Controls.StackPanel> görüntüler nesne <xref:System.Windows.Controls.TreeView>. Görüntülenecek içerik görüntü alanından daha büyükse bir <xref:System.Windows.Controls.ScrollViewer> kullanıcı kaydırmak otomatik olarak görüntüler, böylece <xref:System.Windows.Controls.TreeView> içeriği.  
  
 Görünümünü özelleştirmek için bir <xref:System.Windows.Controls.TreeViewItem> denetlemek, Ayarla <xref:System.Windows.FrameworkElement.Style%2A> özelliğini özel <xref:System.Windows.Style>.  
  
 Aşağıdaki örnekte nasıl ayarlanacağını gösterir <xref:System.Windows.Controls.Control.Foreground%2A> ve <xref:System.Windows.Controls.Control.FontSize%2A> özellik değerleri için bir <xref:System.Windows.Controls.TreeViewItem> kullanarak denetim bir <xref:System.Windows.FrameworkElement.Style%2A>.  
  
 [!code-xaml[TreeViewSimple#8](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSimple/CS/Window1.xaml#8)]  
  
<a name="Adding_Images_and_oOther_Content_to_TreeView_Items"></a>   
## <a name="adding-images-and-other-content-to-treeview-items"></a>Resimleri ve diğer içeriği TreeView öğeler ekleme  
 Birden fazla nesne içerebilir <xref:System.Windows.Controls.HeaderedItemsControl.Header%2A> içeriğini bir <xref:System.Windows.Controls.TreeViewItem>. Birden çok nesnenin içerecek şekilde <xref:System.Windows.Controls.HeaderedItemsControl.Header%2A> içerik, nesneleri bir düzen denetimi içine aşağıdaki gibi alın bir <xref:System.Windows.Controls.Panel> veya <xref:System.Windows.Controls.StackPanel>.  
  
 Aşağıdaki örnekte nasıl tanımlanacağı gösterilmektedir <xref:System.Windows.Controls.HeaderedItemsControl.Header%2A> , bir <xref:System.Windows.Controls.TreeViewItem> olarak bir <xref:System.Windows.Controls.CheckBox> ve <xref:System.Windows.Controls.TextBlock> hem de iliştirilir bir <xref:System.Windows.Controls.DockPanel> denetim.  
  
 [!code-xaml[TreeViewSnips#TVIHeader](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSnips/CSharp/Window1.xaml#tviheader)]  
  
 Aşağıdaki örnekte nasıl tanımlanacağı gösterilmektedir bir <xref:System.Windows.DataTemplate> içeren bir <xref:System.Windows.Controls.Image> ve <xref:System.Windows.Controls.TextBlock> içinde çevrelenmiş bir <xref:System.Windows.Controls.DockPanel> denetim. Kullanabileceğiniz bir <xref:System.Windows.DataTemplate> ayarlamak için <xref:System.Windows.Controls.HeaderedItemsControl.HeaderTemplate%2A> veya <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> için bir <xref:System.Windows.Controls.TreeViewItem>.  
  
 [!code-xaml[TreeViewDataBinding#6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TreeViewDataBinding/CSharp/Window1.xaml#6)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Controls.TreeView>  
 <xref:System.Windows.Controls.TreeViewItem>  
 [Nasıl Yapılır Konuları](../../../../docs/framework/wpf/controls/treeview-how-to-topics.md)  
 [WPF İçerik Modeli](../../../../docs/framework/wpf/controls/wpf-content-model.md)
