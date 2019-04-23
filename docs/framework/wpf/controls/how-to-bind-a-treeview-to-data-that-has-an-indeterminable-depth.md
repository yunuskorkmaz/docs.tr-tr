---
title: "Nasıl yapılır: Belirlenemeyen Derinliğe Sahip Veriyi TreeView'a Bağlama"
ms.date: 03/30/2017
helpviewer_keywords:
- TreeView control [WPF], binding to data of indeterminate depth
ms.assetid: daddcd74-1b0f-4ffd-baeb-ec934c5e0f53
ms.openlocfilehash: 7da0a121cdb854c787c105c92cec70b7c4b3244e
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59214864"
---
# <a name="how-to-bind-a-treeview-to-data-that-has-an-indeterminable-depth"></a>Nasıl yapılır: Belirlenemeyen Derinliğe Sahip Veriyi TreeView'a Bağlama
Bağlamak istediğiniz zamanlar olabilir bir <xref:System.Windows.Controls.TreeView> Derinliği bilinmeyen bir veri kaynağı.  Veriler doğal olarak nerede klasörleri klasörleri içeren bir dosya sistemi veya bir şirketin kuruluş yapısı gibi özyinelemeli çalışanların diğer çalışanlarla çalışanların olduğu olduğunda bu durum oluşabilir.  
  
 Veri kaynağı bir hiyerarşik nesne modeli yüklü olmalıdır. Örneğin, bir `Employee` sınıfı, bir çalışanın doğrudan rapor çalışan nesnelerinin bir koleksiyonu içerebilir. Hiyerarşik olmayan bir şekilde veri gösteriliyorsa, verilerin hiyerarşik bir sunumunu oluşturmanız gerekir.  
  
 Ayarladığınızda <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A?displayProperty=nameWithType> özelliği ve <xref:System.Windows.Controls.ItemsControl> oluşturur bir <xref:System.Windows.Controls.ItemsControl> her alt öğenin alt boyunca <xref:System.Windows.Controls.ItemsControl> ndedir <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> üst öğe olarak. Örneğin ayarlarsanız <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> verilere bağlı özellikte <xref:System.Windows.Controls.TreeView>, her <xref:System.Windows.Controls.TreeViewItem> oluşturulan kullanan diğer bir deyişle <xref:System.Windows.DataTemplate> için atanma <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> özelliği <xref:System.Windows.Controls.TreeView>.  
  
 <xref:System.Windows.HierarchicalDataTemplate> Belirtmenize olanak tanıyan <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> için bir <xref:System.Windows.Controls.TreeViewItem>, ya da tüm <xref:System.Windows.Controls.HeaderedItemsControl>, veri şablonu üzerinde. Ayarladığınızda <xref:System.Windows.HierarchicalDataTemplate.ItemsSource%2A?displayProperty=nameWithType> değeri özelliği yüklendiğinde <xref:System.Windows.HierarchicalDataTemplate> uygulanır. Kullanarak bir <xref:System.Windows.HierarchicalDataTemplate>, yinelemeli olarak ayarlayabilirsiniz <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> her <xref:System.Windows.Controls.TreeViewItem> içinde <xref:System.Windows.Controls.TreeView>.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek nasıl bağlanacağını gösterir. bir <xref:System.Windows.Controls.TreeView> hiyerarşik veriler ve kullanmak için bir <xref:System.Windows.HierarchicalDataTemplate> belirtmek için <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> her <xref:System.Windows.Controls.TreeViewItem>.  <xref:System.Windows.Controls.TreeView> Şirket çalışanlar temsil eden bir XML verilerini bağlar.  Her `Employee` öğesi diğer içerebilir `Employee` kimin kime rapor göstermek için öğeleri. Verileri özyinelemeli olduğundan <xref:System.Windows.HierarchicalDataTemplate> her düzeye uygulanabilir.  
  
 [!code-xaml[TreeViewWithUnknownDepth#1](~/samples/snippets/csharp/VS_Snippets_Wpf/TreeViewWithUnknownDepth/CS/Window1.xaml#1)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Veri Bağlamaya Genel Bakış](../data/data-binding-overview.md)
- [Veri Şablonu Oluşturmaya Genel Bakış](../data/data-templating-overview.md)
