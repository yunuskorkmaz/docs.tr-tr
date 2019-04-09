---
title: 'Nasıl yapılır: SelectedValue, SelectedValuePath ve SelectedItem Kullanma'
ms.date: 03/30/2017
helpviewer_keywords:
- TreeView control [WPF], SelectedValue properties
- Control class [WPF], SelectedItem properties
- Control class [WPF], TreeView properties
- Control class [WPF], SelectedValue properties
- TreeView control [WPF], SelectedItem properties
- SelectedValue [WPF], SelectedValuePath properties
- TreeView control [WPF], SelectedValuePath properties
- Control class [WPF], SelectedValuePath properties
- SelectedValue [WPF], SelectedItem properties
ms.assetid: 2fc92ad4-f02c-4f89-bbe9-d4978a7af0db
ms.openlocfilehash: d9f7a8f04f53b7d38a49dfef2c947dfa1c2d263d
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59169714"
---
# <a name="how-to-use-selectedvalue-selectedvaluepath-and-selecteditem"></a>Nasıl yapılır: SelectedValue, SelectedValuePath ve SelectedItem Kullanma
Bu örnek nasıl kullanılacağını gösterir <xref:System.Windows.Controls.TreeView.SelectedValue%2A> ve <xref:System.Windows.Controls.TreeView.SelectedValuePath%2A> için bir değer belirtmek için özellikleri <xref:System.Windows.Controls.TreeView.SelectedItem%2A> , bir <xref:System.Windows.Controls.TreeView>.  
  
## <a name="example"></a>Örnek  
 <xref:System.Windows.Controls.TreeView.SelectedValuePath%2A> Özelliği belirtmek için bir yol sağlayan bir <xref:System.Windows.Controls.TreeView.SelectedValue%2A> için <xref:System.Windows.Controls.TreeView.SelectedItem%2A> içinde bir <xref:System.Windows.Controls.TreeView>. <xref:System.Windows.Controls.TreeView.SelectedItem%2A> Nesneyi temsil eden <xref:System.Windows.Controls.ItemsControl.Items%2A> koleksiyonu ve <xref:System.Windows.Controls.TreeView> seçilen öğenin tek bir özelliğinin değerini görüntüler. <xref:System.Windows.Controls.TreeView.SelectedValuePath%2A> Özellik değerini belirlemek için kullanılan özellik yolunu belirtir <xref:System.Windows.Controls.TreeView.SelectedValue%2A> özelliği. Bu konudaki örnekler, bu kavramı gösterir.  
  
 Aşağıdaki örnekte gösterildiği bir <xref:System.Windows.Data.XmlDataProvider> , çalışan bilgilerini içerir.  
  
 [!code-xaml[TreeViewSelectedValue#XMLDataProvider](~/samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSelectedValue/CS/Window1.xaml#xmldataprovider)]  
  
 Aşağıdaki örnekte tanımlayan bir <xref:System.Windows.HierarchicalDataTemplate> görüntüleyen `EmployeeName` ve `EmployeeWorkDay` , `Employee`. Unutmayın <xref:System.Windows.HierarchicalDataTemplate> belirttiğinde `EmployeeNumber` şablonunun bir parçası olarak.  
  
 [!code-xaml[TreeViewSelectedValue#HierarchicalDataTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSelectedValue/CS/Window1.xaml#hierarchicaldatatemplate)]  
  
 Aşağıdaki örnekte gösterildiği bir <xref:System.Windows.Controls.TreeView> önceden tanımlanmış kullanan <xref:System.Windows.HierarchicalDataTemplate> ve ayarlayan <xref:System.Windows.Controls.TreeView.SelectedValue%2A> özelliğini `EmployeeNumber`. Seçtiğinizde, bir `EmployeeName` içinde <xref:System.Windows.Controls.TreeView>, <xref:System.Windows.Controls.TreeView.SelectedItem%2A> özelliği döndürür `EmployeeInfo` seçili karşılık gelen bir veri öğesi `EmployeeName`. Ancak, çünkü <xref:System.Windows.Controls.TreeView.SelectedValuePath%2A> bu <xref:System.Windows.Controls.TreeView> ayarlanır `EmployeeNumber`, <xref:System.Windows.Controls.TreeView.SelectedValue%2A> ayarlanır `EmployeeNumber`.  
  
 [!code-xaml[TreeViewSelectedValue#SelectedValuePath](~/samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSelectedValue/CS/Window1.xaml#selectedvaluepath)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Controls.TreeView>
- <xref:System.Windows.Controls.TreeViewItem>
- [TreeView Genel Bakışı](treeview-overview.md)
- [Nasıl Yapılır Konuları](treeview-how-to-topics.md)
