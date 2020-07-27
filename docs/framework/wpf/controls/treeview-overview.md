---
title: TreeView Genel Bakışı
description: Windows Presentation Foundation TreeView denetiminin bilgileri, basit örnekler de dahil olmak üzere düğümleri kullanarak hiyerarşik bir yapıda nasıl görüntülediğini öğrenin.
ms.date: 03/30/2017
helpviewer_keywords:
- expanding node [WPF]
- TreeView control [WPF], about TreeView control
- Control class [WPF], TreeView
ms.assetid: 62212512-5a5c-4864-949e-b6a6a3a52c02
ms.openlocfilehash: 6ef77febdd3facb7c7e1af566841c2a1aeaff810
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87164533"
---
# <a name="treeview-overview"></a>TreeView Genel Bakışı
<xref:System.Windows.Controls.TreeView>Denetim, daraltılabilir düğümleri kullanarak hiyerarşik bir yapıda bilgi görüntülemenin bir yolunu sağlar. Bu konu, <xref:System.Windows.Controls.TreeView> ve denetimlerini tanıtır ve kullanımları için <xref:System.Windows.Controls.TreeViewItem> basit örnekler sağlar.  

<a name="Simple_TreeView_Control"></a>
## <a name="what-is-a-treeview"></a>TreeView nedir?  
 <xref:System.Windows.Controls.TreeView>, <xref:System.Windows.Controls.ItemsControl> denetimleri kullanarak öğeleri hedefleyen bir <xref:System.Windows.Controls.TreeViewItem> . Aşağıdaki örnek bir oluşturur <xref:System.Windows.Controls.TreeView> .  
  
 [!code-xaml[TreeViewSnips#EmbeddedTVIs](~/samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSnips/CSharp/Window1.xaml#embeddedtvis)]  
  
<a name="Creating_a_TreeView"></a>
## <a name="creating-a-treeview"></a>TreeView oluşturma  
 <xref:System.Windows.Controls.TreeView>Denetim bir denetim hiyerarşisi içerir <xref:System.Windows.Controls.TreeViewItem> . Bir <xref:System.Windows.Controls.TreeViewItem> Denetim, <xref:System.Windows.Controls.HeaderedItemsControl> ve bir koleksiyonuna sahiptir <xref:System.Windows.Controls.HeaderedItemsControl.Header%2A> <xref:System.Windows.Controls.ItemsControl.Items%2A> .  
  
 Kullanarak bir ile tanımlıyorsanız <xref:System.Windows.Controls.TreeView> [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] , <xref:System.Windows.Controls.HeaderedItemsControl.Header%2A> bir <xref:System.Windows.Controls.TreeViewItem> denetimin içeriğini ve koleksiyonunu oluşturan öğeleri açık bir şekilde tanımlayabilirsiniz. Önceki çizimde bu yöntem gösterilmektedir.  
  
 Ayrıca bir <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> veri kaynağı olarak belirtebilirsiniz ve sonra <xref:System.Windows.Controls.HeaderedItemsControl.HeaderTemplate%2A> <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> içeriği tanımlamak için bir ve belirtebilirsiniz <xref:System.Windows.Controls.TreeViewItem> .  
  
 Bir denetimin yerleşimini tanımlamak için <xref:System.Windows.Controls.TreeViewItem> nesneleri de kullanabilirsiniz <xref:System.Windows.HierarchicalDataTemplate> . Daha fazla bilgi ve bir örnek için bkz. [SelectedValue, SelectedValuePath ve SelectedItem kullanma](how-to-use-selectedvalue-selectedvaluepath-and-selecteditem.md).  
  
 Bir öğe bir <xref:System.Windows.Controls.TreeViewItem> Denetim değilse, denetim görüntülenirken otomatik olarak bir denetim tarafından alınır <xref:System.Windows.Controls.TreeViewItem> <xref:System.Windows.Controls.TreeView> .  
  
<a name="Expanding_and_Collapsing_a_TreeViewItem"></a>
## <a name="expanding-and-collapsing-a-treeviewitem"></a>Bir TreeViewItem genişletme ve daraltma  
 Kullanıcı bir öğesini genişlediğinde <xref:System.Windows.Controls.TreeViewItem> , <xref:System.Windows.Controls.TreeViewItem.IsExpanded%2A> özelliği olarak ayarlanır `true` . Ayrıca <xref:System.Windows.Controls.TreeViewItem> , <xref:System.Windows.Controls.TreeViewItem.IsExpanded%2A> özelliği `true` (Genişlet) veya `false` (daraltma) özelliğini ayarlayarak doğrudan Kullanıcı eylemi olmadan bir öğesini genişletebilir veya daraltabilirsiniz. Bu özellik değiştiğinde <xref:System.Windows.Controls.TreeViewItem.Expanded> veya bir <xref:System.Windows.Controls.TreeViewItem.Collapsed> olay oluşur.  
  
 <xref:System.Windows.FrameworkElement.BringIntoView%2A>Yöntemi bir <xref:System.Windows.Controls.TreeViewItem> denetimde çağrıldığında, <xref:System.Windows.Controls.TreeViewItem> ve üst <xref:System.Windows.Controls.TreeViewItem> denetimleri genişletilir. Bir <xref:System.Windows.Controls.TreeViewItem> veya kısmen görünür değilse, görünür <xref:System.Windows.Controls.TreeView> hale getirmek için kayar.  
  
<a name="TreeViewItem_Selection"></a>
## <a name="treeviewitem-selection"></a>TreeViewItem Seçimi  
 Kullanıcı <xref:System.Windows.Controls.TreeViewItem> onu seçmek için bir denetime tıkladığında <xref:System.Windows.Controls.TreeViewItem.Selected> olay oluşur ve <xref:System.Windows.Controls.TreeViewItem.IsSelected%2A> özelliği olarak ayarlanır `true` . , <xref:System.Windows.Controls.TreeViewItem> Denetimin de olur <xref:System.Windows.Controls.TreeView.SelectedItem%2A> <xref:System.Windows.Controls.TreeView> . Buna karşılık, seçim bir <xref:System.Windows.Controls.TreeViewItem> denetimden değiştiğinde, <xref:System.Windows.Controls.TreeViewItem.Unselected> olayı oluşur ve <xref:System.Windows.Controls.TreeViewItem.IsSelected%2A> özelliği olarak ayarlanır `false` .  
  
 <xref:System.Windows.Controls.TreeView.SelectedItem%2A> <xref:System.Windows.Controls.TreeView> Denetimdeki özelliği salt okunurdur. bu nedenle, açıkça ayarlayamazsınız. <xref:System.Windows.Controls.TreeView.SelectedItem%2A>Kullanıcı bir <xref:System.Windows.Controls.TreeViewItem> denetime tıkladığında veya <xref:System.Windows.Controls.TreeViewItem.IsSelected%2A> özellik denetimde olarak ayarlandığında özellik ayarlanır `true` <xref:System.Windows.Controls.TreeViewItem> .  
  
 Bir öğesini <xref:System.Windows.Controls.TreeView.SelectedValuePath%2A> belirtmek için özelliğini kullanın <xref:System.Windows.Controls.TreeView.SelectedValue%2A> <xref:System.Windows.Controls.TreeView.SelectedItem%2A> . Daha fazla bilgi için bkz. [SelectedValue, SelectedValuePath ve SelectedItem kullanma](how-to-use-selectedvalue-selectedvaluepath-and-selecteditem.md).  
  
 <xref:System.Windows.Controls.TreeView.SelectedItemChanged>Seçili bir değişikliğin ne zaman olacağını öğrenmek için olaya bir olay işleyicisi kaydedebilirsiniz <xref:System.Windows.Controls.TreeViewItem> . <xref:System.Windows.RoutedPropertyChangedEventArgs%601>Olay işleyicisine sunulan, <xref:System.Windows.RoutedPropertyChangedEventArgs%601.OldValue%2A> önceki seçim ve geçerli seçim olan öğesini belirtir <xref:System.Windows.RoutedPropertyChangedEventArgs%601.NewValue%2A> . `null`Uygulamanın veya kullanıcının önceki veya geçerli bir seçimi yapmadığından, her iki değer de olabilir.  
  
<a name="TreeView_Style"></a>
## <a name="treeview-style"></a>TreeView stili  
 Bir denetimin varsayılan stili, <xref:System.Windows.Controls.TreeView> <xref:System.Windows.Controls.StackPanel> denetimi içeren bir nesnenin içine koyar <xref:System.Windows.Controls.ScrollViewer> . <xref:System.Windows.FrameworkElement.Width%2A> <xref:System.Windows.FrameworkElement.Height%2A> ' A ait ve özelliklerini ayarladığınızda <xref:System.Windows.Controls.TreeView> , bu değerler öğesini görüntüleyen nesnesini boyutlandırdığınızda kullanılır <xref:System.Windows.Controls.StackPanel> <xref:System.Windows.Controls.TreeView> . Görüntülenecek içerik görüntüleme alanından büyükse, <xref:System.Windows.Controls.ScrollViewer> kullanıcının içeriği kaydırabilmesi için otomatik olarak bir görüntülenir <xref:System.Windows.Controls.TreeView> .  
  
 Bir denetimin görünüşünü özelleştirmek için <xref:System.Windows.Controls.TreeViewItem> , <xref:System.Windows.FrameworkElement.Style%2A> özelliği özel olarak ayarlayın <xref:System.Windows.Style> .  
  
 Aşağıdaki örnek, <xref:System.Windows.Controls.Control.Foreground%2A> <xref:System.Windows.Controls.Control.FontSize%2A> bir denetim için ' a kullanarak ve özellik değerlerinin nasıl ayarlanacağını gösterir <xref:System.Windows.Controls.TreeViewItem> <xref:System.Windows.FrameworkElement.Style%2A> .  
  
 [!code-xaml[TreeViewSimple#8](~/samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSimple/CS/Window1.xaml#8)]  
  
<a name="Adding_Images_and_oOther_Content_to_TreeView_Items"></a>
## <a name="adding-images-and-other-content-to-treeview-items"></a>TreeView öğelerine görüntü ve diğer Içerik ekleme  
 Bir ' ın içeriğine birden fazla nesne ekleyebilirsiniz <xref:System.Windows.Controls.HeaderedItemsControl.Header%2A> <xref:System.Windows.Controls.TreeViewItem> . İçeriğe birden fazla nesne eklemek için <xref:System.Windows.Controls.HeaderedItemsControl.Header%2A> , nesneleri bir veya gibi bir düzen denetiminin içine ekleyin <xref:System.Windows.Controls.Panel> <xref:System.Windows.Controls.StackPanel> .  
  
 Aşağıdaki örnek, bir, <xref:System.Windows.Controls.HeaderedItemsControl.Header%2A> <xref:System.Windows.Controls.TreeViewItem> ve öğelerinin her ikisi de bir <xref:System.Windows.Controls.CheckBox> <xref:System.Windows.Controls.TextBlock> denetimin içine <xref:System.Windows.Controls.DockPanel> nasıl tanımlanacağını gösterir.  
  
 [!code-xaml[TreeViewSnips#TVIHeader](~/samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSnips/CSharp/Window1.xaml#tviheader)]  
  
 Aşağıdaki örnek, bir <xref:System.Windows.DataTemplate> <xref:System.Windows.Controls.Image> denetimin içindeki ve içeren bir ' ın nasıl tanımlanacağını gösterir <xref:System.Windows.Controls.TextBlock> <xref:System.Windows.Controls.DockPanel> . <xref:System.Windows.DataTemplate>Veya için öğesini ayarlamak için kullanabilirsiniz <xref:System.Windows.Controls.HeaderedItemsControl.HeaderTemplate%2A> <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> <xref:System.Windows.Controls.TreeViewItem> .  
  
 [!code-xaml[TreeViewDataBinding#6](~/samples/snippets/csharp/VS_Snippets_Wpf/TreeViewDataBinding/CSharp/Window1.xaml#6)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Controls.TreeView>
- <xref:System.Windows.Controls.TreeViewItem>
- [Nasıl Yapılır Konuları](treeview-how-to-topics.md)
- [WPF İçerik Modeli](wpf-content-model.md)
