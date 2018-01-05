---
title: "Nasıl yapılır: TreeView İçinde TreeViewItem Bulma"
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
- TreeView control [WPF], finding a TreeViewItem
- TreeViewItem [WPF], finding
ms.assetid: 72ecd40c-3939-4e01-b617-5e9daa6074d9
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 696a9e2d92b9c44e4aedbcc200b41e5548cd7411
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-find-a-treeviewitem-in-a-treeview"></a>Nasıl yapılır: TreeView İçinde TreeViewItem Bulma
<xref:System.Windows.Controls.TreeView> Denetimi hiyerarşik verileri görüntülemek için kullanışlı bir yol sağlar. Varsa, <xref:System.Windows.Controls.TreeView> bir veri kaynağına bağlı olduğu <xref:System.Windows.Controls.TreeView.SelectedItem%2A> özelliği, hızlı bir şekilde seçili veri nesnesini almak kolay bir yol sağlar. Temel alınan veri nesnesi ile çalışmak genellikle en iyisidir, ancak bazen verinin içeren programsal gerekebilir <xref:System.Windows.Controls.TreeViewItem>. Örneğin, program aracılığıyla genişletmeniz gerekebilir <xref:System.Windows.Controls.TreeViewItem>, veya farklı bir öğe seçin <xref:System.Windows.Controls.TreeView>.  
  
 Bulmak için bir <xref:System.Windows.Controls.TreeViewItem> belirli veri nesnesi içeren, her düzeyde geçmesi gereken <xref:System.Windows.Controls.TreeView>. Öğeleri bir <xref:System.Windows.Controls.TreeView> performansını artırmak için de sanallaştırılabilecek. Burada öğeleri sanallaştırılmış durumda, aynı zamanda farkında olun gerekir bir <xref:System.Windows.Controls.TreeViewItem> veri nesnesi içerip içermediğini denetlemek için.  
  
## <a name="example"></a>Örnek  
  
## <a name="description"></a>Açıklama  
 Aşağıdaki örnek aramalar bir <xref:System.Windows.Controls.TreeView> belirli bir nesnesi ve nesnesini içeren döndürür <xref:System.Windows.Controls.TreeViewItem>. Örneğin, her sağlar <xref:System.Windows.Controls.TreeViewItem> böylece alt öğelerinden aranabilecek örneği. Bu örnek ayrıca çalışır <xref:System.Windows.Controls.TreeView> sanallaştırılmış öğeleri kullanmaz.  
  
> [!NOTE]
>  Aşağıdaki örnek için çalışır <xref:System.Windows.Controls.TreeView>temel alınan veri modeli ve aramaları bağımsız olarak her <xref:System.Windows.Controls.TreeViewItem> nesne bulunana kadar. Daha iyi performans sahip başka bir veri modeli belirtilen nesne için arama, verileri hiyerarşi içinde konumunu izlemenize ve karşılık gelen bulmak için bir tekniktir <xref:System.Windows.Controls.TreeViewItem> içinde <xref:System.Windows.Controls.TreeView>. Ancak, daha iyi performans sahip teknik bilgi ve veri modelinin gerektirir ve verilen herhangi için genelleştirilmiş olamaz <xref:System.Windows.Controls.TreeView>.  
  
## <a name="code"></a>Kod  
 [!code-csharp[TreeViewFindTVI#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TreeViewFindTVI/CSharp/MainWindow.xaml.cs#1)]
 [!code-vb[TreeViewFindTVI#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TreeViewFindTVI/VisualBasic/MainWindow.xaml.vb#1)]  
  
 Önceki kod üzerinde özel dayanır <xref:System.Windows.Controls.VirtualizingStackPanel> adlı bir yöntemi gösterir `BringIntoView`. Aşağıdaki kod özel tanımlar <xref:System.Windows.Controls.VirtualizingStackPanel>.  
  
 [!code-csharp[TreeViewFindTVI#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TreeViewFindTVI/CSharp/MainWindow.xaml.cs#2)]
 [!code-vb[TreeViewFindTVI#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TreeViewFindTVI/VisualBasic/MainWindow.xaml.vb#2)]  
  
 Aşağıdaki XAML nasıl oluşturulacağını gösterir bir <xref:System.Windows.Controls.TreeView> özel kullanan <xref:System.Windows.Controls.VirtualizingStackPanel>.  
  
 [!code-xaml[TreeViewFindTVI#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TreeViewFindTVI/CSharp/MainWindow.xaml#3)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [TreeView'ın Performansını Artırma](../../../../docs/framework/wpf/controls/how-to-improve-the-performance-of-a-treeview.md)
