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
# <a name="how-to-use-selectedvalue-selectedvaluepath-and-selecteditem"></a><span data-ttu-id="823ae-102">Nasıl yapılır: SelectedValue, SelectedValuePath ve SelectedItem Kullanma</span><span class="sxs-lookup"><span data-stu-id="823ae-102">How to: Use SelectedValue, SelectedValuePath, and SelectedItem</span></span>
<span data-ttu-id="823ae-103">Bu örnek nasıl kullanılacağını gösterir <xref:System.Windows.Controls.TreeView.SelectedValue%2A> ve <xref:System.Windows.Controls.TreeView.SelectedValuePath%2A> için bir değer belirtmek için özellikleri <xref:System.Windows.Controls.TreeView.SelectedItem%2A> , bir <xref:System.Windows.Controls.TreeView>.</span><span class="sxs-lookup"><span data-stu-id="823ae-103">This example shows how to use the <xref:System.Windows.Controls.TreeView.SelectedValue%2A> and <xref:System.Windows.Controls.TreeView.SelectedValuePath%2A> properties to specify a value for the <xref:System.Windows.Controls.TreeView.SelectedItem%2A> of a <xref:System.Windows.Controls.TreeView>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="823ae-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="823ae-104">Example</span></span>  
 <span data-ttu-id="823ae-105"><xref:System.Windows.Controls.TreeView.SelectedValuePath%2A> Özelliği belirtmek için bir yol sağlayan bir <xref:System.Windows.Controls.TreeView.SelectedValue%2A> için <xref:System.Windows.Controls.TreeView.SelectedItem%2A> içinde bir <xref:System.Windows.Controls.TreeView>.</span><span class="sxs-lookup"><span data-stu-id="823ae-105">The <xref:System.Windows.Controls.TreeView.SelectedValuePath%2A> property provides a way to specify a <xref:System.Windows.Controls.TreeView.SelectedValue%2A> for the <xref:System.Windows.Controls.TreeView.SelectedItem%2A> in a <xref:System.Windows.Controls.TreeView>.</span></span> <span data-ttu-id="823ae-106"><xref:System.Windows.Controls.TreeView.SelectedItem%2A> Nesneyi temsil eden <xref:System.Windows.Controls.ItemsControl.Items%2A> koleksiyonu ve <xref:System.Windows.Controls.TreeView> seçilen öğenin tek bir özelliğin değerini görüntüler.</span><span class="sxs-lookup"><span data-stu-id="823ae-106">The <xref:System.Windows.Controls.TreeView.SelectedItem%2A> represents an object in the <xref:System.Windows.Controls.ItemsControl.Items%2A> collection and the <xref:System.Windows.Controls.TreeView> displays the value of a single property of the selected item.</span></span> <span data-ttu-id="823ae-107"><xref:System.Windows.Controls.TreeView.SelectedValuePath%2A> Özellik değeri belirlemek için kullanılan özellik yolunu belirtir <xref:System.Windows.Controls.TreeView.SelectedValue%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="823ae-107">The <xref:System.Windows.Controls.TreeView.SelectedValuePath%2A> property specifies the path to the property that is used to determine the value of the <xref:System.Windows.Controls.TreeView.SelectedValue%2A> property.</span></span> <span data-ttu-id="823ae-108">Bu konudaki örnekler, bu kavram gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="823ae-108">The examples in this topic illustrate this concept.</span></span>  
  
 <span data-ttu-id="823ae-109">Aşağıdaki örnekte gösterildiği bir <xref:System.Windows.Data.XmlDataProvider> , çalışan bilgilerini içeren.</span><span class="sxs-lookup"><span data-stu-id="823ae-109">The following example shows an <xref:System.Windows.Data.XmlDataProvider> that contains employee information.</span></span>  
  
 [!code-xaml[TreeViewSelectedValue#XMLDataProvider](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSelectedValue/CS/Window1.xaml#xmldataprovider)]  
  
 <span data-ttu-id="823ae-110">Aşağıdaki örnek tanımlayan bir <xref:System.Windows.HierarchicalDataTemplate> görüntüleyen `EmployeeName` ve `EmployeeWorkDay` , `Employee`.</span><span class="sxs-lookup"><span data-stu-id="823ae-110">The following example defines a <xref:System.Windows.HierarchicalDataTemplate> that displays the `EmployeeName` and `EmployeeWorkDay` of the `Employee`.</span></span> <span data-ttu-id="823ae-111">Unutmayın <xref:System.Windows.HierarchicalDataTemplate> belirtmediği `EmployeeNumber` şablonunun parçası olarak.</span><span class="sxs-lookup"><span data-stu-id="823ae-111">Note that the <xref:System.Windows.HierarchicalDataTemplate> does not specify the `EmployeeNumber` as part of the template.</span></span>  
  
 [!code-xaml[TreeViewSelectedValue#HierarchicalDataTemplate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSelectedValue/CS/Window1.xaml#hierarchicaldatatemplate)]  
  
 <span data-ttu-id="823ae-112">Aşağıdaki örnekte gösterildiği bir <xref:System.Windows.Controls.TreeView> önceden tanımlanmış kullanan <xref:System.Windows.HierarchicalDataTemplate> ve ayarlar <xref:System.Windows.Controls.TreeView.SelectedValue%2A> özelliğine `EmployeeNumber`.</span><span class="sxs-lookup"><span data-stu-id="823ae-112">The following example shows a <xref:System.Windows.Controls.TreeView> that uses the previously defined <xref:System.Windows.HierarchicalDataTemplate> and that sets the <xref:System.Windows.Controls.TreeView.SelectedValue%2A> property to the `EmployeeNumber`.</span></span> <span data-ttu-id="823ae-113">Seçtiğinizde, bir `EmployeeName` içinde <xref:System.Windows.Controls.TreeView>, <xref:System.Windows.Controls.TreeView.SelectedItem%2A> özelliği döndürür `EmployeeInfo` seçili karşılık gelen veri öğesi `EmployeeName`.</span><span class="sxs-lookup"><span data-stu-id="823ae-113">When you select an `EmployeeName` in the <xref:System.Windows.Controls.TreeView>, the <xref:System.Windows.Controls.TreeView.SelectedItem%2A> property returns the `EmployeeInfo` data item that corresponds to the selected `EmployeeName`.</span></span> <span data-ttu-id="823ae-114">Ancak, çünkü <xref:System.Windows.Controls.TreeView.SelectedValuePath%2A> bu <xref:System.Windows.Controls.TreeView> ayarlanır `EmployeeNumber`, <xref:System.Windows.Controls.TreeView.SelectedValue%2A> ayarlanır `EmployeeNumber`.</span><span class="sxs-lookup"><span data-stu-id="823ae-114">However, because the <xref:System.Windows.Controls.TreeView.SelectedValuePath%2A> of this <xref:System.Windows.Controls.TreeView> is set to `EmployeeNumber`, the <xref:System.Windows.Controls.TreeView.SelectedValue%2A> is set to the `EmployeeNumber`.</span></span>  
  
 [!code-xaml[TreeViewSelectedValue#SelectedValuePath](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSelectedValue/CS/Window1.xaml#selectedvaluepath)]  
  
## <a name="see-also"></a><span data-ttu-id="823ae-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="823ae-115">See Also</span></span>  
 <xref:System.Windows.Controls.TreeView>  
 <xref:System.Windows.Controls.TreeViewItem>  
 [<span data-ttu-id="823ae-116">TreeView genel bakış</span><span class="sxs-lookup"><span data-stu-id="823ae-116">TreeView Overview</span></span>](../../../../docs/framework/wpf/controls/treeview-overview.md)  
 [<span data-ttu-id="823ae-117">Nasıl Yapılır Konuları</span><span class="sxs-lookup"><span data-stu-id="823ae-117">How-to Topics</span></span>](../../../../docs/framework/wpf/controls/treeview-how-to-topics.md)
