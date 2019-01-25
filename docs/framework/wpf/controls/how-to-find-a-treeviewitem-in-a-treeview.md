---
title: 'Nasıl yapılır: TreeView İçinde TreeViewItem Bulma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- TreeView control [WPF], finding a TreeViewItem
- TreeViewItem [WPF], finding
ms.assetid: 72ecd40c-3939-4e01-b617-5e9daa6074d9
ms.openlocfilehash: bce4f059e76b0ebea29b023eba2e9e2f59813035
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54636033"
---
# <a name="how-to-find-a-treeviewitem-in-a-treeview"></a>Nasıl yapılır: TreeView İçinde TreeViewItem Bulma
<xref:System.Windows.Controls.TreeView> Denetimi hiyerarşik verileri görüntülemek için kolay bir yol sağlar. Varsa, <xref:System.Windows.Controls.TreeView> bir veri kaynağına bağlı <xref:System.Windows.Controls.TreeView.SelectedItem%2A> özelliği, seçilen veri nesnesinin hızlıca almak kolay bir yol sağlar. Temel alınan veri nesnesi ile çalışmak genellikle en iyisidir ancak bazı durumlarda veri içeren programsal gerekebilir <xref:System.Windows.Controls.TreeViewItem>. Örneğin, program aracılığıyla genişletmeniz gerekebilir <xref:System.Windows.Controls.TreeViewItem>, veya farklı bir öğe seçin <xref:System.Windows.Controls.TreeView>.  
  
 Bulunacak bir <xref:System.Windows.Controls.TreeViewItem> her düzeyde geçmesi gereken, belirli bir veri nesnesini içeren <xref:System.Windows.Controls.TreeView>. Öğeleri bir <xref:System.Windows.Controls.TreeView> performansını artırmak için ayrıca sanallaştırılabilir. Burada öğeleri sanallaştırılabilir durumda da, sizin de fark ettiğinizden gerekir bir <xref:System.Windows.Controls.TreeViewItem> veri nesnesi içerip içermediğini denetlemek için.  
  
## <a name="example"></a>Örnek  
  
## <a name="description"></a>Açıklama  
 Aşağıdaki örnek aramalar bir <xref:System.Windows.Controls.TreeView> belirli bir nesneyi ve nesnenin projenin kapsayan döndürür <xref:System.Windows.Controls.TreeViewItem>. Örneğin, her sağlar <xref:System.Windows.Controls.TreeViewItem> böylece onun alt öğelerini aranabilir oluşturulur. Bu örnek de çalışır <xref:System.Windows.Controls.TreeView> sanallaştırılmış öğeleri kullanmaz.  
  
> [!NOTE]
>  Aşağıdaki örnek için çalışır <xref:System.Windows.Controls.TreeView>, temel alınan veri modeli ve aramalar bağımsız olarak her <xref:System.Windows.Controls.TreeViewItem> nesne bulunana kadar. Daha iyi performansa sahip başka bir veri modeli belirtilen nesne için arama, verileri hiyerarşi içinde konumunu izlemenize ve ardından ilgili bulun tekniktir <xref:System.Windows.Controls.TreeViewItem> içinde <xref:System.Windows.Controls.TreeView>. Ancak, daha iyi performansa sahip teknik bilgi veri modelinin gerektirir ve herhangi için verilen genelleştirilemediği <xref:System.Windows.Controls.TreeView>.  
  
## <a name="code"></a>Kod  
 [!code-csharp[TreeViewFindTVI#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TreeViewFindTVI/CSharp/MainWindow.xaml.cs#1)]
 [!code-vb[TreeViewFindTVI#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TreeViewFindTVI/VisualBasic/MainWindow.xaml.vb#1)]  
  
 Önceki kod üzerinde özel bir kullanır <xref:System.Windows.Controls.VirtualizingStackPanel> adlı bir yöntem sunan `BringIntoView`. Aşağıdaki kod özel tanımlar <xref:System.Windows.Controls.VirtualizingStackPanel>.  
  
 [!code-csharp[TreeViewFindTVI#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TreeViewFindTVI/CSharp/MainWindow.xaml.cs#2)]
 [!code-vb[TreeViewFindTVI#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TreeViewFindTVI/VisualBasic/MainWindow.xaml.vb#2)]  
  
 Aşağıdaki XAML nasıl oluşturulacağını gösterir. bir <xref:System.Windows.Controls.TreeView> özel kullanan <xref:System.Windows.Controls.VirtualizingStackPanel>.  
  
 [!code-xaml[TreeViewFindTVI#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TreeViewFindTVI/CSharp/MainWindow.xaml#3)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [TreeView'ın Performansını Artırma](../../../../docs/framework/wpf/controls/how-to-improve-the-performance-of-a-treeview.md)
