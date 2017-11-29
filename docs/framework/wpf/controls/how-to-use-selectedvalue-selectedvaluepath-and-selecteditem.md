---
title: "Nasıl yapılır: SelectedValue, SelectedValuePath ve SelectedItem Kullanma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: fdc478d62ca97f8f61c26fbbf1ee6c3ea8b4e189
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-use-selectedvalue-selectedvaluepath-and-selecteditem"></a>Nasıl yapılır: SelectedValue, SelectedValuePath ve SelectedItem Kullanma
Bu örnek nasıl kullanılacağını gösterir <xref:System.Windows.Controls.TreeView.SelectedValue%2A> ve <xref:System.Windows.Controls.TreeView.SelectedValuePath%2A> için bir değer belirtmek için özellikleri <xref:System.Windows.Controls.TreeView.SelectedItem%2A> , bir <xref:System.Windows.Controls.TreeView>.  
  
## <a name="example"></a>Örnek  
 <xref:System.Windows.Controls.TreeView.SelectedValuePath%2A> Özelliği belirtmek için bir yol sağlayan bir <xref:System.Windows.Controls.TreeView.SelectedValue%2A> için <xref:System.Windows.Controls.TreeView.SelectedItem%2A> içinde bir <xref:System.Windows.Controls.TreeView>. <xref:System.Windows.Controls.TreeView.SelectedItem%2A> Nesneyi temsil eden <xref:System.Windows.Controls.ItemsControl.Items%2A> koleksiyonu ve <xref:System.Windows.Controls.TreeView> seçilen öğenin tek bir özelliğin değerini görüntüler. <xref:System.Windows.Controls.TreeView.SelectedValuePath%2A> Özellik değeri belirlemek için kullanılan özellik yolunu belirtir <xref:System.Windows.Controls.TreeView.SelectedValue%2A> özelliği. Bu konudaki örnekler, bu kavram gösterilmektedir.  
  
 Aşağıdaki örnekte gösterildiği bir <xref:System.Windows.Data.XmlDataProvider> , çalışan bilgilerini içeren.  
  
 [!code-xaml[TreeViewSelectedValue#XMLDataProvider](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSelectedValue/CS/Window1.xaml#xmldataprovider)]  
  
 Aşağıdaki örnek tanımlayan bir <xref:System.Windows.HierarchicalDataTemplate> görüntüleyen `EmployeeName` ve `EmployeeWorkDay` , `Employee`. Unutmayın <xref:System.Windows.HierarchicalDataTemplate> belirtmediği `EmployeeNumber` şablonunun parçası olarak.  
  
 [!code-xaml[TreeViewSelectedValue#HierarchicalDataTemplate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSelectedValue/CS/Window1.xaml#hierarchicaldatatemplate)]  
  
 Aşağıdaki örnekte gösterildiği bir <xref:System.Windows.Controls.TreeView> önceden tanımlanmış kullanan <xref:System.Windows.HierarchicalDataTemplate> ve ayarlar <xref:System.Windows.Controls.TreeView.SelectedValue%2A> özelliğine `EmployeeNumber`. Seçtiğinizde, bir `EmployeeName` içinde <xref:System.Windows.Controls.TreeView>, <xref:System.Windows.Controls.TreeView.SelectedItem%2A> özelliği döndürür `EmployeeInfo` seçili karşılık gelen veri öğesi `EmployeeName`. Ancak, çünkü <xref:System.Windows.Controls.TreeView.SelectedValuePath%2A> bu <xref:System.Windows.Controls.TreeView> ayarlanır `EmployeeNumber`, <xref:System.Windows.Controls.TreeView.SelectedValue%2A> ayarlanır `EmployeeNumber`.  
  
 [!code-xaml[TreeViewSelectedValue#SelectedValuePath](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSelectedValue/CS/Window1.xaml#selectedvaluepath)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Controls.TreeView>  
 <xref:System.Windows.Controls.TreeViewItem>  
 [TreeView genel bakış](../../../../docs/framework/wpf/controls/treeview-overview.md)  
 [Nasıl Yapılır Konuları](../../../../docs/framework/wpf/controls/treeview-how-to-topics.md)
