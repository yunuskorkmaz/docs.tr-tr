---
title: TreeView Genel Bakışı
ms.date: 03/30/2017
helpviewer_keywords:
- expanding node [WPF]
- TreeView control [WPF], about TreeView control
- Control class [WPF], TreeView
ms.assetid: 62212512-5a5c-4864-949e-b6a6a3a52c02
ms.openlocfilehash: 5758aead9811cdbaf7f61bbd710092f6b4474ad8
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57369636"
---
# <a name="treeview-overview"></a>TreeView Genel Bakışı
<xref:System.Windows.Controls.TreeView> Denetimi daraltılabilir düğümleri kullanarak hiyerarşik bir yapıda bilgilerini görüntülemek için bir yol sağlar. Bu konu tanıtır <xref:System.Windows.Controls.TreeView> ve <xref:System.Windows.Controls.TreeViewItem> denetler ve kullanımlarının ilişkin basit örnekler sağlar.  
  
  
<a name="Simple_TreeView_Control"></a>   
## <a name="what-is-a-treeview"></a>TreeView nedir?  
 <xref:System.Windows.Controls.TreeView> olan bir <xref:System.Windows.Controls.ItemsControl> öğelerini kullanarak katmandan <xref:System.Windows.Controls.TreeViewItem> kontrol eder. Aşağıdaki örnek, oluşturur bir <xref:System.Windows.Controls.TreeView>.  
  
 [!code-xaml[TreeViewSnips#EmbeddedTVIs](~/samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSnips/CSharp/Window1.xaml#embeddedtvis)]  
  
<a name="Creating_a_TreeView"></a>   
## <a name="creating-a-treeview"></a>TreeView oluşturma  
 <xref:System.Windows.Controls.TreeView> Denetimi içeren bir hiyerarşisini <xref:System.Windows.Controls.TreeViewItem> kontrol eder. A <xref:System.Windows.Controls.TreeViewItem> denetimi bir <xref:System.Windows.Controls.HeaderedItemsControl> olan bir <xref:System.Windows.Controls.HeaderedItemsControl.Header%2A> ve <xref:System.Windows.Controls.ItemsControl.Items%2A> koleksiyonu.  
  
 Tanımlıyorsanız, bir <xref:System.Windows.Controls.TreeView> kullanarak [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], açıkça tanımlayabilirsiniz <xref:System.Windows.Controls.HeaderedItemsControl.Header%2A> içeriğini bir <xref:System.Windows.Controls.TreeViewItem> denetimi ve koleksiyonu oluşturan öğeler. Önceki çizimde, bu yöntem gösterilmektedir.  
  
 Belirtebilirsiniz bir <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> bir veri kaynağı ve ardından belirtin bir <xref:System.Windows.Controls.HeaderedItemsControl.HeaderTemplate%2A> ve <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> tanımlamak için <xref:System.Windows.Controls.TreeViewItem> içeriği.  
  
 Düzenini tanımlamak için bir <xref:System.Windows.Controls.TreeViewItem> denetimi de kullanabilirsiniz <xref:System.Windows.HierarchicalDataTemplate> nesneleri. Daha fazla bilgi ve örnek için bkz. [kullanım SelectedValue, SelectedValuePath ve SelectedItem](how-to-use-selectedvalue-selectedvaluepath-and-selecteditem.md).  
  
 Bir öğe değilse bir <xref:System.Windows.Controls.TreeViewItem> denetimi, otomatik olarak içine alınır tarafından bir <xref:System.Windows.Controls.TreeViewItem> denetimi <xref:System.Windows.Controls.TreeView> denetim görüntülenir.  
  
<a name="Expanding_and_Collapsing_a_TreeViewItem"></a>   
## <a name="expanding-and-collapsing-a-treeviewitem"></a>Bir TreeViewItem daraltma ve genişletme  
 Kullanıcı genişletir, bir <xref:System.Windows.Controls.TreeViewItem>, <xref:System.Windows.Controls.TreeViewItem.IsExpanded%2A> özelliği `true`. Ayrıca genişletmek veya daraltmak bir <xref:System.Windows.Controls.TreeViewItem> ayarlayarak doğrudan kullanıcı eylemi olmadan <xref:System.Windows.Controls.TreeViewItem.IsExpanded%2A> özelliğini `true` (expand) veya `false` (Daralt). Bu özellik değiştiğinde bir <xref:System.Windows.Controls.TreeViewItem.Expanded> veya <xref:System.Windows.Controls.TreeViewItem.Collapsed> olayı oluşur.  
  
 Zaman <xref:System.Windows.FrameworkElement.BringIntoView%2A> yöntemi çağrıldığında bir <xref:System.Windows.Controls.TreeViewItem> denetimi <xref:System.Windows.Controls.TreeViewItem> ve kendi üst <xref:System.Windows.Controls.TreeViewItem> denetimleri genişletin. Varsa bir <xref:System.Windows.Controls.TreeViewItem> görünür veya kısmen görünür olup olmadığını <xref:System.Windows.Controls.TreeView> görünür yapmak için kayar.  
  
<a name="TreeViewItem_Selection"></a>   
## <a name="treeviewitem-selection"></a>TreeViewItem seçimi  
 Kullanıcı tıkladığında bir <xref:System.Windows.Controls.TreeViewItem> seçmek için Denetim <xref:System.Windows.Controls.TreeViewItem.Selected> olayı oluşur ve <xref:System.Windows.Controls.TreeViewItem.IsSelected%2A> özelliği `true`. <xref:System.Windows.Controls.TreeViewItem> Ayrıca olur <xref:System.Windows.Controls.TreeView.SelectedItem%2A> , <xref:System.Windows.Controls.TreeView> denetimi. Buna karşılık, seçimi değiştiğinde gelen bir <xref:System.Windows.Controls.TreeViewItem> denetimi, onun <xref:System.Windows.Controls.TreeViewItem.Unselected> olayı oluşur ve <xref:System.Windows.Controls.TreeViewItem.IsSelected%2A> özelliği `false`.  
  
 <xref:System.Windows.Controls.TreeView.SelectedItem%2A> Özelliği <xref:System.Windows.Controls.TreeView> denetimi salt okunur bir özellik; bu nedenle açıkça bunu göremezsiniz. <xref:System.Windows.Controls.TreeView.SelectedItem%2A> Özelliği ayarlanmışsa kullanıcı tıkladığında bir <xref:System.Windows.Controls.TreeViewItem> denetim veya <xref:System.Windows.Controls.TreeViewItem.IsSelected%2A> özelliği `true` üzerinde <xref:System.Windows.Controls.TreeViewItem> denetimi.  
  
 Kullanım <xref:System.Windows.Controls.TreeView.SelectedValuePath%2A> özelliği belirtmek için bir <xref:System.Windows.Controls.TreeView.SelectedValue%2A> , bir <xref:System.Windows.Controls.TreeView.SelectedItem%2A>. Daha fazla bilgi için [kullanım SelectedValue, SelectedValuePath ve SelectedItem](how-to-use-selectedvalue-selectedvaluepath-and-selecteditem.md).  
  
 Bir olay işleyicisi kaydedebileceğiniz <xref:System.Windows.Controls.TreeView.SelectedItemChanged> seçili belirlemek için olay <xref:System.Windows.Controls.TreeViewItem> değişiklikler. <xref:System.Windows.RoutedPropertyChangedEventArgs%601> İçin olay işleyicisi belirtir sağlanan olan <xref:System.Windows.RoutedPropertyChangedEventArgs%601.OldValue%2A>, önceki seçimi olduğu ve <xref:System.Windows.RoutedPropertyChangedEventArgs%601.NewValue%2A>, geçerli seçimi olduğu. Her iki değer `null` uygulama veya kullanıcıya bir önceki ya da geçerli seçimi yapmamışsa.  
  
<a name="TreeView_Style"></a>   
## <a name="treeview-style"></a>TreeView Stili  
 Varsayılan stili bir <xref:System.Windows.Controls.TreeView> denetim yerleştirir içinde bir <xref:System.Windows.Controls.StackPanel> içeren nesne bir <xref:System.Windows.Controls.ScrollViewer> denetimi. Ayarladığınızda <xref:System.Windows.FrameworkElement.Width%2A> ve <xref:System.Windows.FrameworkElement.Height%2A> özelliklerini bir <xref:System.Windows.Controls.TreeView>, bu değerleri boyutu için kullanılan <xref:System.Windows.Controls.StackPanel> görüntüler nesne <xref:System.Windows.Controls.TreeView>. Görüntülenecek içeriği görünen alanın büyükse bir <xref:System.Windows.Controls.ScrollViewer> böylece kullanıcının kaydırma yapmasına otomatik olarak görüntüler <xref:System.Windows.Controls.TreeView> içeriği.  
  
 Görünümünü özelleştirmek için bir <xref:System.Windows.Controls.TreeViewItem> denetlemek için ayarlayın <xref:System.Windows.FrameworkElement.Style%2A> özelliğini özel <xref:System.Windows.Style>.  
  
 Aşağıdaki örnek nasıl ayarlanacağını gösterir <xref:System.Windows.Controls.Control.Foreground%2A> ve <xref:System.Windows.Controls.Control.FontSize%2A> özellik değerleri için bir <xref:System.Windows.Controls.TreeViewItem> denetimi kullanarak bir <xref:System.Windows.FrameworkElement.Style%2A>.  
  
 [!code-xaml[TreeViewSimple#8](~/samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSimple/CS/Window1.xaml#8)]  
  
<a name="Adding_Images_and_oOther_Content_to_TreeView_Items"></a>   
## <a name="adding-images-and-other-content-to-treeview-items"></a>Görüntüleri ve diğer içerik TreeView öğeler ekleme  
 Birden fazla nesne içerebilir <xref:System.Windows.Controls.HeaderedItemsControl.Header%2A> içeriğini bir <xref:System.Windows.Controls.TreeViewItem>. Birden çok nesnenin içerecek şekilde <xref:System.Windows.Controls.HeaderedItemsControl.Header%2A> içerik, nesneleri bir düzen denetimi içine aşağıdaki gibi alın bir <xref:System.Windows.Controls.Panel> veya <xref:System.Windows.Controls.StackPanel>.  
  
 Aşağıdaki örnek nasıl tanımlanacağını gösterir <xref:System.Windows.Controls.HeaderedItemsControl.Header%2A> , bir <xref:System.Windows.Controls.TreeViewItem> olarak bir <xref:System.Windows.Controls.CheckBox> ve <xref:System.Windows.Controls.TextBlock> hem de alınmış bir <xref:System.Windows.Controls.DockPanel> denetimi.  
  
 [!code-xaml[TreeViewSnips#TVIHeader](~/samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSnips/CSharp/Window1.xaml#tviheader)]  
  
 Aşağıdaki örnek nasıl tanımlanacağını gösterir bir <xref:System.Windows.DataTemplate> içeren bir <xref:System.Windows.Controls.Image> ve <xref:System.Windows.Controls.TextBlock> içinde alınmış bir <xref:System.Windows.Controls.DockPanel> denetimi. Kullanabileceğiniz bir <xref:System.Windows.DataTemplate> ayarlanacak <xref:System.Windows.Controls.HeaderedItemsControl.HeaderTemplate%2A> veya <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> için bir <xref:System.Windows.Controls.TreeViewItem>.  
  
 [!code-xaml[TreeViewDataBinding#6](~/samples/snippets/csharp/VS_Snippets_Wpf/TreeViewDataBinding/CSharp/Window1.xaml#6)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Windows.Controls.TreeView>
- <xref:System.Windows.Controls.TreeViewItem>
- [Nasıl Yapılır Konuları](treeview-how-to-topics.md)
- [WPF İçerik Modeli](wpf-content-model.md)
