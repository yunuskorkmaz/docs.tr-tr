---
title: "Nasıl yapılır: Belirlenemeyen Derinliğe Sahip Veriyi TreeView'a Bağlama"
ms.date: 03/30/2017
helpviewer_keywords:
- TreeView control [WPF], binding to data of indeterminate depth
ms.assetid: daddcd74-1b0f-4ffd-baeb-ec934c5e0f53
ms.openlocfilehash: cd9a1ee015ebb707a7a06d1c062a1bb3003c96e8
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73458619"
---
# <a name="how-to-bind-a-treeview-to-data-that-has-an-indeterminable-depth"></a>Nasıl yapılır: Belirlenemeyen Derinliğe Sahip Veriyi TreeView'a Bağlama
Derinliği bilinen bir veri kaynağına <xref:System.Windows.Controls.TreeView> bağlamak istediğiniz zaman olabilir.  Bu durum, verilerin bir dosya sistemi gibi (örneğin, klasörler) veya Şirketin kuruluş yapısını, çalışanların doğrudan rapor olarak başka çalışanları olduğu bir dosya sistemi gibi özyinelemeli olduğunda meydana gelebilir.  
  
 Veri kaynağının hiyerarşik bir nesne modeli olmalıdır. Örneğin, bir `Employee` sınıfı bir çalışanın doğrudan raporu olan çalışan nesnelerinin bir koleksiyonunu içerebilir. Veriler hiyerarşik olmayan bir şekilde gösteriliyorsa, verilerin hiyerarşik bir gösterimini derlemeniz gerekir.  
  
 <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A?displayProperty=nameWithType> özelliğini ayarladığınızda ve <xref:System.Windows.Controls.ItemsControl> her alt öğe için bir <xref:System.Windows.Controls.ItemsControl> oluşturursa, alt <xref:System.Windows.Controls.ItemsControl> üst öğeyle aynı <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> kullanır. Örneğin, bir veri bağlantılı <xref:System.Windows.Controls.TreeView><xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> özelliğini ayarlarsanız, oluşturulan her <xref:System.Windows.Controls.TreeViewItem> <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> <xref:System.Windows.Controls.TreeView>özelliğine atanmış <xref:System.Windows.DataTemplate> kullanır.  
  
 <xref:System.Windows.HierarchicalDataTemplate>, veri şablonunda bir <xref:System.Windows.Controls.TreeViewItem>veya herhangi bir <xref:System.Windows.Controls.HeaderedItemsControl>için <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> belirtmenize olanak sağlar. <xref:System.Windows.HierarchicalDataTemplate.ItemsSource%2A?displayProperty=nameWithType> özelliğini ayarladığınızda, <xref:System.Windows.HierarchicalDataTemplate> uygulandığında bu değer kullanılır. <xref:System.Windows.HierarchicalDataTemplate>kullanarak, <xref:System.Windows.Controls.TreeView>her <xref:System.Windows.Controls.TreeViewItem> için <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> yinelemeli olarak ayarlayabilirsiniz.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir <xref:System.Windows.Controls.TreeView> hiyerarşik verilere nasıl bağlanacağını ve her bir <xref:System.Windows.Controls.TreeViewItem><xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> belirtmek için <xref:System.Windows.HierarchicalDataTemplate> nasıl kullanılacağını gösterir.  <xref:System.Windows.Controls.TreeView>, bir şirketteki çalışanları temsil eden XML verilerine bağlanır.  Her `Employee` öğesi kimin kim tarafından rapor olduğunu göstermek için diğer `Employee` öğeleri içerebilir. Veriler özyinelemeli olduğundan <xref:System.Windows.HierarchicalDataTemplate> her düzeye uygulanabilir.  
  
 [!code-xaml[TreeViewWithUnknownDepth#1](~/samples/snippets/csharp/VS_Snippets_Wpf/TreeViewWithUnknownDepth/CS/Window1.xaml#1)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Veri Bağlamaya Genel Bakış](../../../desktop-wpf/data/data-binding-overview.md)
- [Veri Şablonu Oluşturmaya Genel Bakış](../data/data-templating-overview.md)
