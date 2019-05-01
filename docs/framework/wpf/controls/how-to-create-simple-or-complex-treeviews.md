---
title: 'Nasıl yapılır: Basit veya Karmaşık TreeViews Oluşturma'
ms.date: 03/30/2017
helpviewer_keywords:
- TreeView control [WPF], creating
- Control class [WPF], TreeView [WPF], creating
ms.assetid: 1defbb78-b8e7-4c0e-b650-576453ac828d
ms.openlocfilehash: 7edb4933ebcc0f0d2cb02754238c2342ee9dd4a2
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62031921"
---
# <a name="how-to-create-simple-or-complex-treeviews"></a>Nasıl yapılır: Basit veya Karmaşık TreeViews Oluşturma
Bu örnek, basit veya karmaşık oluşturma işlemi gösterilmektedir <xref:System.Windows.Controls.TreeView> kontrol eder.  
  
 A <xref:System.Windows.Controls.TreeView> hiyerarşisinden oluşur <xref:System.Windows.Controls.TreeViewItem> gibi basit metin dizelerini ve ayrıca daha karmaşık içerik içerebilen denetimleri <xref:System.Windows.Controls.Button> denetimleri veya <xref:System.Windows.Controls.StackPanel> katıştırılmış içeriğe sahip. Açıkça tanımlayabilirsiniz <xref:System.Windows.Controls.TreeView> içerik veya bir veri kaynağı içerik sağlayabilir. Bu konu, bu kavramları örnekleri sağlar.  
  
## <a name="example"></a>Örnek  
 <xref:System.Windows.Controls.HeaderedItemsControl.Header%2A> Özelliği <xref:System.Windows.Controls.TreeViewItem> içeriğin bulunduğu, <xref:System.Windows.Controls.TreeView> için bu öğeyi görüntüler. A <xref:System.Windows.Controls.TreeViewItem> bulundurabilirsiniz <xref:System.Windows.Controls.TreeViewItem> denetimler ve onun alt öğeleri olarak kullanarak bu alt öğeleri tanımlayabilirsiniz <xref:System.Windows.Controls.ItemsControl.Items%2A> özelliği.  
  
 Aşağıdaki örnek, açıkça tanımlamak gösterilmektedir <xref:System.Windows.Controls.TreeViewItem> ayarlayarak içerik <xref:System.Windows.Controls.HeaderedItemsControl.Header%2A> özelliğini bir metin dizesi.  
  
 [!code-xaml[TreeViewSimple#1](~/samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSimple/CS/Window1.xaml#1)]  
  
 Aşağıdaki örnek Göster alt öğeleri tanımlamak nasıl bir <xref:System.Windows.Controls.TreeViewItem> tanımlayarak <xref:System.Windows.Controls.ItemsControl.Items%2A> olan <xref:System.Windows.Controls.Button> kontrol eder.  
  
 [!code-xaml[TreeViewSimple#3](~/samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSimple/CS/Window1.xaml#3)]  
  
 Aşağıdaki örnek nasıl oluşturulacağını gösterir. bir <xref:System.Windows.Controls.TreeView> burada bir <xref:System.Windows.Data.XmlDataProvider> sağlar <xref:System.Windows.Controls.TreeViewItem> içeriği ve <xref:System.Windows.HierarchicalDataTemplate> içeriğinin görünümünü tanımlar.  
  
 [!code-xaml[TreeViewSimple#6](~/samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSimple/CS/Window1.xaml#6)]  
  
 [!code-xaml[TreeViewSimple#7](~/samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSimple/CS/Window1.xaml#7)]  
  
 [!code-xaml[TreeViewSimple#5](~/samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSimple/CS/Window1.xaml#5)]  
  
 Aşağıdaki örnek nasıl oluşturulacağını gösterir. bir <xref:System.Windows.Controls.TreeView> burada <xref:System.Windows.Controls.TreeViewItem> içeriği <xref:System.Windows.Controls.DockPanel> katıştırılmış içeriğe sahip denetimler.  
  
 [!code-xaml[TreeViewSimple#9](~/samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSimple/CS/Window1.xaml#9)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Controls.TreeView>
- <xref:System.Windows.Controls.TreeViewItem>
- [TreeView Genel Bakış](treeview-overview.md)
- [Nasıl Yapılır Konuları](treeview-how-to-topics.md)
