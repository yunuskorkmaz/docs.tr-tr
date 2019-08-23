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
ms.openlocfilehash: ad72c7a7fb11dfe605db4119dde831b47dd7c5a4
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69962089"
---
# <a name="how-to-find-a-treeviewitem-in-a-treeview"></a>Nasıl yapılır: TreeView İçinde TreeViewItem Bulma
<xref:System.Windows.Controls.TreeView> Denetim hiyerarşik verileri göstermek için uygun bir yol sağlar. Bir veri kaynağına bağlıysa <xref:System.Windows.Controls.TreeView.SelectedItem%2A> , özelliği seçili veri nesnesini hızlı bir şekilde almanızı sağlayan uygun bir yol sağlar. <xref:System.Windows.Controls.TreeView> Genellikle temel alınan veri nesnesiyle çalışmak en iyisidir, ancak bazen verilerin <xref:System.Windows.Controls.TreeViewItem>birlikte çalışmasını programlı bir şekilde değiştirmeniz gerekebilir. Örneğin, ' yi programlı bir şekilde genişletmeniz <xref:System.Windows.Controls.TreeViewItem>veya <xref:System.Windows.Controls.TreeView>içinde farklı bir öğe seçmeniz gerekebilir.  
  
 Belirli bir veri <xref:System.Windows.Controls.TreeViewItem> nesnesini içeren bir bulmak için, her bir düzeyini <xref:System.Windows.Controls.TreeView>de çapraz geçiş yapmanız gerekir. Ayrıca, içindeki <xref:System.Windows.Controls.TreeView> öğeler de performansı artırmak için sanallaştırılabilir. Öğelerin sanallaştırılmış olması durumunda, veri nesnesini içerip içermediğini denetlemek için bir <xref:System.Windows.Controls.TreeViewItem> de sağlamalısınız.  
  
## <a name="example"></a>Örnek  
  
## <a name="description"></a>Açıklama  
 Aşağıdaki örnek, belirli bir <xref:System.Windows.Controls.TreeView> nesne için arar ve nesnenin kendisini <xref:System.Windows.Controls.TreeViewItem>döndürür. Örnek, alt öğelerinin aranabilmesi için her birinin <xref:System.Windows.Controls.TreeViewItem> oluşturulmasını sağlar. Bu örnek, <xref:System.Windows.Controls.TreeView> sanallaştırılmış öğeleri kullanmıyorsa de işe yarar.  
  
> [!NOTE]
> Aşağıdaki örnek, temel alınan veri <xref:System.Windows.Controls.TreeView>modelinden bağımsız olarak her türlü için geçerlidir ve nesne bulunana kadar <xref:System.Windows.Controls.TreeViewItem> her bir arama yapar. Daha iyi performansa sahip olan başka bir teknik ise, belirtilen nesnenin veri modelini aramak, veri hiyerarşisinde konumunu izlemek ve ' <xref:System.Windows.Controls.TreeViewItem> <xref:System.Windows.Controls.TreeView>de karşılık gelen ' ı bulmasıdır. Ancak, daha iyi performansa sahip olan teknik, veri modeli hakkında bilgi gerektirir ve herhangi bir <xref:System.Windows.Controls.TreeView>şekilde genelleştirilemez.  
  
## <a name="code"></a>Kod  
 [!code-csharp[TreeViewFindTVI#1](~/samples/snippets/csharp/VS_Snippets_Wpf/TreeViewFindTVI/CSharp/MainWindow.xaml.cs#1)]
 [!code-vb[TreeViewFindTVI#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TreeViewFindTVI/VisualBasic/MainWindow.xaml.vb#1)]  
  
 Önceki kod, adlı <xref:System.Windows.Controls.VirtualizingStackPanel> `BringIntoView`bir yöntemi kullanıma sunan bir özel kullanır. Aşağıdaki kod özel <xref:System.Windows.Controls.VirtualizingStackPanel>tanımlar.  
  
 [!code-csharp[TreeViewFindTVI#2](~/samples/snippets/csharp/VS_Snippets_Wpf/TreeViewFindTVI/CSharp/MainWindow.xaml.cs#2)]
 [!code-vb[TreeViewFindTVI#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TreeViewFindTVI/VisualBasic/MainWindow.xaml.vb#2)]  
  
 Aşağıdaki XAML, özel <xref:System.Windows.Controls.TreeView> <xref:System.Windows.Controls.VirtualizingStackPanel>' i kullanan bir oluşturmayı gösterir.  
  
 [!code-xaml[TreeViewFindTVI#3](~/samples/snippets/csharp/VS_Snippets_Wpf/TreeViewFindTVI/CSharp/MainWindow.xaml#3)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [TreeView'ın Performansını Artırma](how-to-improve-the-performance-of-a-treeview.md)
