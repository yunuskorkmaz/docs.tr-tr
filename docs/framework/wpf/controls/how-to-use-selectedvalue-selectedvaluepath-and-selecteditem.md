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
ms.openlocfilehash: 1bb307009586a5bbf4e9accefb633b97dc837528
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54637835"
---
# <a name="how-to-use-selectedvalue-selectedvaluepath-and-selecteditem"></a><span data-ttu-id="fcb8f-102">Nasıl yapılır: SelectedValue, SelectedValuePath ve SelectedItem Kullanma</span><span class="sxs-lookup"><span data-stu-id="fcb8f-102">How to: Use SelectedValue, SelectedValuePath, and SelectedItem</span></span>
<span data-ttu-id="fcb8f-103">Bu örnek nasıl kullanılacağını gösterir <xref:System.Windows.Controls.TreeView.SelectedValue%2A> ve <xref:System.Windows.Controls.TreeView.SelectedValuePath%2A> için bir değer belirtmek için özellikleri <xref:System.Windows.Controls.TreeView.SelectedItem%2A> , bir <xref:System.Windows.Controls.TreeView>.</span><span class="sxs-lookup"><span data-stu-id="fcb8f-103">This example shows how to use the <xref:System.Windows.Controls.TreeView.SelectedValue%2A> and <xref:System.Windows.Controls.TreeView.SelectedValuePath%2A> properties to specify a value for the <xref:System.Windows.Controls.TreeView.SelectedItem%2A> of a <xref:System.Windows.Controls.TreeView>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fcb8f-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="fcb8f-104">Example</span></span>  
 <span data-ttu-id="fcb8f-105"><xref:System.Windows.Controls.TreeView.SelectedValuePath%2A> Özelliği belirtmek için bir yol sağlayan bir <xref:System.Windows.Controls.TreeView.SelectedValue%2A> için <xref:System.Windows.Controls.TreeView.SelectedItem%2A> içinde bir <xref:System.Windows.Controls.TreeView>.</span><span class="sxs-lookup"><span data-stu-id="fcb8f-105">The <xref:System.Windows.Controls.TreeView.SelectedValuePath%2A> property provides a way to specify a <xref:System.Windows.Controls.TreeView.SelectedValue%2A> for the <xref:System.Windows.Controls.TreeView.SelectedItem%2A> in a <xref:System.Windows.Controls.TreeView>.</span></span> <span data-ttu-id="fcb8f-106"><xref:System.Windows.Controls.TreeView.SelectedItem%2A> Nesneyi temsil eden <xref:System.Windows.Controls.ItemsControl.Items%2A> koleksiyonu ve <xref:System.Windows.Controls.TreeView> seçilen öğenin tek bir özelliğinin değerini görüntüler.</span><span class="sxs-lookup"><span data-stu-id="fcb8f-106">The <xref:System.Windows.Controls.TreeView.SelectedItem%2A> represents an object in the <xref:System.Windows.Controls.ItemsControl.Items%2A> collection and the <xref:System.Windows.Controls.TreeView> displays the value of a single property of the selected item.</span></span> <span data-ttu-id="fcb8f-107"><xref:System.Windows.Controls.TreeView.SelectedValuePath%2A> Özellik değerini belirlemek için kullanılan özellik yolunu belirtir <xref:System.Windows.Controls.TreeView.SelectedValue%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="fcb8f-107">The <xref:System.Windows.Controls.TreeView.SelectedValuePath%2A> property specifies the path to the property that is used to determine the value of the <xref:System.Windows.Controls.TreeView.SelectedValue%2A> property.</span></span> <span data-ttu-id="fcb8f-108">Bu konudaki örnekler, bu kavramı gösterir.</span><span class="sxs-lookup"><span data-stu-id="fcb8f-108">The examples in this topic illustrate this concept.</span></span>  
  
 <span data-ttu-id="fcb8f-109">Aşağıdaki örnekte gösterildiği bir <xref:System.Windows.Data.XmlDataProvider> , çalışan bilgilerini içerir.</span><span class="sxs-lookup"><span data-stu-id="fcb8f-109">The following example shows an <xref:System.Windows.Data.XmlDataProvider> that contains employee information.</span></span>  
  
 [!code-xaml[TreeViewSelectedValue#XMLDataProvider](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSelectedValue/CS/Window1.xaml#xmldataprovider)]  
  
 <span data-ttu-id="fcb8f-110">Aşağıdaki örnekte tanımlayan bir <xref:System.Windows.HierarchicalDataTemplate> görüntüleyen `EmployeeName` ve `EmployeeWorkDay` , `Employee`.</span><span class="sxs-lookup"><span data-stu-id="fcb8f-110">The following example defines a <xref:System.Windows.HierarchicalDataTemplate> that displays the `EmployeeName` and `EmployeeWorkDay` of the `Employee`.</span></span> <span data-ttu-id="fcb8f-111">Unutmayın <xref:System.Windows.HierarchicalDataTemplate> belirttiğinde `EmployeeNumber` şablonunun bir parçası olarak.</span><span class="sxs-lookup"><span data-stu-id="fcb8f-111">Note that the <xref:System.Windows.HierarchicalDataTemplate> does not specify the `EmployeeNumber` as part of the template.</span></span>  
  
 [!code-xaml[TreeViewSelectedValue#HierarchicalDataTemplate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSelectedValue/CS/Window1.xaml#hierarchicaldatatemplate)]  
  
 <span data-ttu-id="fcb8f-112">Aşağıdaki örnekte gösterildiği bir <xref:System.Windows.Controls.TreeView> önceden tanımlanmış kullanan <xref:System.Windows.HierarchicalDataTemplate> ve ayarlayan <xref:System.Windows.Controls.TreeView.SelectedValue%2A> özelliğini `EmployeeNumber`.</span><span class="sxs-lookup"><span data-stu-id="fcb8f-112">The following example shows a <xref:System.Windows.Controls.TreeView> that uses the previously defined <xref:System.Windows.HierarchicalDataTemplate> and that sets the <xref:System.Windows.Controls.TreeView.SelectedValue%2A> property to the `EmployeeNumber`.</span></span> <span data-ttu-id="fcb8f-113">Seçtiğinizde, bir `EmployeeName` içinde <xref:System.Windows.Controls.TreeView>, <xref:System.Windows.Controls.TreeView.SelectedItem%2A> özelliği döndürür `EmployeeInfo` seçili karşılık gelen bir veri öğesi `EmployeeName`.</span><span class="sxs-lookup"><span data-stu-id="fcb8f-113">When you select an `EmployeeName` in the <xref:System.Windows.Controls.TreeView>, the <xref:System.Windows.Controls.TreeView.SelectedItem%2A> property returns the `EmployeeInfo` data item that corresponds to the selected `EmployeeName`.</span></span> <span data-ttu-id="fcb8f-114">Ancak, çünkü <xref:System.Windows.Controls.TreeView.SelectedValuePath%2A> bu <xref:System.Windows.Controls.TreeView> ayarlanır `EmployeeNumber`, <xref:System.Windows.Controls.TreeView.SelectedValue%2A> ayarlanır `EmployeeNumber`.</span><span class="sxs-lookup"><span data-stu-id="fcb8f-114">However, because the <xref:System.Windows.Controls.TreeView.SelectedValuePath%2A> of this <xref:System.Windows.Controls.TreeView> is set to `EmployeeNumber`, the <xref:System.Windows.Controls.TreeView.SelectedValue%2A> is set to the `EmployeeNumber`.</span></span>  
  
 [!code-xaml[TreeViewSelectedValue#SelectedValuePath](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSelectedValue/CS/Window1.xaml#selectedvaluepath)]  
  
## <a name="see-also"></a><span data-ttu-id="fcb8f-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fcb8f-115">See also</span></span>
- <xref:System.Windows.Controls.TreeView>
- <xref:System.Windows.Controls.TreeViewItem>
- [<span data-ttu-id="fcb8f-116">TreeView Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="fcb8f-116">TreeView Overview</span></span>](../../../../docs/framework/wpf/controls/treeview-overview.md)
- [<span data-ttu-id="fcb8f-117">Nasıl Yapılır Konuları</span><span class="sxs-lookup"><span data-stu-id="fcb8f-117">How-to Topics</span></span>](../../../../docs/framework/wpf/controls/treeview-how-to-topics.md)
