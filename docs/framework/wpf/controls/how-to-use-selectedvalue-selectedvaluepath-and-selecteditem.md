---
title: 'Nasıl yapılır: SelectedValue, SelectedValuePath ve SelectedItem Kullanma'
description: Windows Presentation Foundation TreeView 'un Selecteditıtem için bir değer belirtmek üzere SelectedValue ve SelectedValuePath özelliklerinin nasıl kullanılacağını öğrenin.
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
ms.openlocfilehash: ddac2455dee0bf69d25307340eddd5364e43e823
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87166281"
---
# <a name="how-to-use-selectedvalue-selectedvaluepath-and-selecteditem"></a>Nasıl yapılır: SelectedValue, SelectedValuePath ve SelectedItem Kullanma
Bu örnek <xref:System.Windows.Controls.TreeView.SelectedValue%2A> <xref:System.Windows.Controls.TreeView.SelectedValuePath%2A> , öğesinin bir değerini belirtmek için ve özelliklerini nasıl kullanacağınızı gösterir <xref:System.Windows.Controls.TreeView.SelectedItem%2A> <xref:System.Windows.Controls.TreeView> .  
  
## <a name="example"></a>Örnek  
 <xref:System.Windows.Controls.TreeView.SelectedValuePath%2A>Özelliği <xref:System.Windows.Controls.TreeView.SelectedValue%2A> , içinde için bir belirtmek için bir yol sağlar <xref:System.Windows.Controls.TreeView.SelectedItem%2A> <xref:System.Windows.Controls.TreeView> . , <xref:System.Windows.Controls.TreeView.SelectedItem%2A> Koleksiyondaki bir nesneyi temsil eder <xref:System.Windows.Controls.ItemsControl.Items%2A> ve <xref:System.Windows.Controls.TreeView> Seçili öğenin tek bir özelliğinin değerini görüntüler. <xref:System.Windows.Controls.TreeView.SelectedValuePath%2A>Özelliği, özelliğinin değerini belirlemede kullanılan özelliğin yolunu belirtir <xref:System.Windows.Controls.TreeView.SelectedValue%2A> . Bu konudaki örneklerde bu kavram gösterilmektedir.  
  
 Aşağıdaki örnek, <xref:System.Windows.Data.XmlDataProvider> çalışan bilgilerini içeren bir gösterir.  
  
 [!code-xaml[TreeViewSelectedValue#XMLDataProvider](~/samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSelectedValue/CS/Window1.xaml#xmldataprovider)]  
  
 Aşağıdaki örnek <xref:System.Windows.HierarchicalDataTemplate> `EmployeeName` , ve ' i görüntüleyen bir tanımlar `EmployeeWorkDay` `Employee` . Öğesinin, <xref:System.Windows.HierarchicalDataTemplate> `EmployeeNumber` şablonun parçası olarak belirtmediğini unutmayın.  
  
 [!code-xaml[TreeViewSelectedValue#HierarchicalDataTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSelectedValue/CS/Window1.xaml#hierarchicaldatatemplate)]  
  
 Aşağıdaki örnek, <xref:System.Windows.Controls.TreeView> daha önce tanımlanan <xref:System.Windows.HierarchicalDataTemplate> ve özelliğini ' a ayarlayan öğesini gösterir <xref:System.Windows.Controls.TreeView.SelectedValue%2A> `EmployeeNumber` . İçinde bir seçtiğinizde `EmployeeName` <xref:System.Windows.Controls.TreeView> , <xref:System.Windows.Controls.TreeView.SelectedItem%2A> özelliği `EmployeeInfo` Seçili öğesine karşılık gelen veri öğesini döndürür `EmployeeName` . Ancak, öğesinin ' a ayarlandığı için, olarak <xref:System.Windows.Controls.TreeView.SelectedValuePath%2A> <xref:System.Windows.Controls.TreeView> `EmployeeNumber` <xref:System.Windows.Controls.TreeView.SelectedValue%2A> ayarlanır `EmployeeNumber` .  
  
 [!code-xaml[TreeViewSelectedValue#SelectedValuePath](~/samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSelectedValue/CS/Window1.xaml#selectedvaluepath)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Controls.TreeView>
- <xref:System.Windows.Controls.TreeViewItem>
- [TreeView Genel Bakışı](treeview-overview.md)
- [Nasıl Yapılır Konuları](treeview-how-to-topics.md)
