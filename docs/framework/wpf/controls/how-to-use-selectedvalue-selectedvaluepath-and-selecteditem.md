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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61699142"
---
# <a name="how-to-use-selectedvalue-selectedvaluepath-and-selecteditem"></a><span data-ttu-id="105f4-102">Nasıl yapılır: SelectedValue, SelectedValuePath ve SelectedItem Kullanma</span><span class="sxs-lookup"><span data-stu-id="105f4-102">How to: Use SelectedValue, SelectedValuePath, and SelectedItem</span></span>
<span data-ttu-id="105f4-103">Bu örnek nasıl kullanılacağını gösterir <xref:System.Windows.Controls.TreeView.SelectedValue%2A> ve <xref:System.Windows.Controls.TreeView.SelectedValuePath%2A> için bir değer belirtmek için özellikleri <xref:System.Windows.Controls.TreeView.SelectedItem%2A> , bir <xref:System.Windows.Controls.TreeView>.</span><span class="sxs-lookup"><span data-stu-id="105f4-103">This example shows how to use the <xref:System.Windows.Controls.TreeView.SelectedValue%2A> and <xref:System.Windows.Controls.TreeView.SelectedValuePath%2A> properties to specify a value for the <xref:System.Windows.Controls.TreeView.SelectedItem%2A> of a <xref:System.Windows.Controls.TreeView>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="105f4-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="105f4-104">Example</span></span>  
 <span data-ttu-id="105f4-105"><xref:System.Windows.Controls.TreeView.SelectedValuePath%2A> Özelliği belirtmek için bir yol sağlayan bir <xref:System.Windows.Controls.TreeView.SelectedValue%2A> için <xref:System.Windows.Controls.TreeView.SelectedItem%2A> içinde bir <xref:System.Windows.Controls.TreeView>.</span><span class="sxs-lookup"><span data-stu-id="105f4-105">The <xref:System.Windows.Controls.TreeView.SelectedValuePath%2A> property provides a way to specify a <xref:System.Windows.Controls.TreeView.SelectedValue%2A> for the <xref:System.Windows.Controls.TreeView.SelectedItem%2A> in a <xref:System.Windows.Controls.TreeView>.</span></span> <span data-ttu-id="105f4-106"><xref:System.Windows.Controls.TreeView.SelectedItem%2A> Nesneyi temsil eden <xref:System.Windows.Controls.ItemsControl.Items%2A> koleksiyonu ve <xref:System.Windows.Controls.TreeView> seçilen öğenin tek bir özelliğinin değerini görüntüler.</span><span class="sxs-lookup"><span data-stu-id="105f4-106">The <xref:System.Windows.Controls.TreeView.SelectedItem%2A> represents an object in the <xref:System.Windows.Controls.ItemsControl.Items%2A> collection and the <xref:System.Windows.Controls.TreeView> displays the value of a single property of the selected item.</span></span> <span data-ttu-id="105f4-107"><xref:System.Windows.Controls.TreeView.SelectedValuePath%2A> Özellik değerini belirlemek için kullanılan özellik yolunu belirtir <xref:System.Windows.Controls.TreeView.SelectedValue%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="105f4-107">The <xref:System.Windows.Controls.TreeView.SelectedValuePath%2A> property specifies the path to the property that is used to determine the value of the <xref:System.Windows.Controls.TreeView.SelectedValue%2A> property.</span></span> <span data-ttu-id="105f4-108">Bu konudaki örnekler, bu kavramı gösterir.</span><span class="sxs-lookup"><span data-stu-id="105f4-108">The examples in this topic illustrate this concept.</span></span>  
  
 <span data-ttu-id="105f4-109">Aşağıdaki örnekte gösterildiği bir <xref:System.Windows.Data.XmlDataProvider> , çalışan bilgilerini içerir.</span><span class="sxs-lookup"><span data-stu-id="105f4-109">The following example shows an <xref:System.Windows.Data.XmlDataProvider> that contains employee information.</span></span>  
  
 [!code-xaml[TreeViewSelectedValue#XMLDataProvider](~/samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSelectedValue/CS/Window1.xaml#xmldataprovider)]  
  
 <span data-ttu-id="105f4-110">Aşağıdaki örnekte tanımlayan bir <xref:System.Windows.HierarchicalDataTemplate> görüntüleyen `EmployeeName` ve `EmployeeWorkDay` , `Employee`.</span><span class="sxs-lookup"><span data-stu-id="105f4-110">The following example defines a <xref:System.Windows.HierarchicalDataTemplate> that displays the `EmployeeName` and `EmployeeWorkDay` of the `Employee`.</span></span> <span data-ttu-id="105f4-111">Unutmayın <xref:System.Windows.HierarchicalDataTemplate> belirttiğinde `EmployeeNumber` şablonunun bir parçası olarak.</span><span class="sxs-lookup"><span data-stu-id="105f4-111">Note that the <xref:System.Windows.HierarchicalDataTemplate> does not specify the `EmployeeNumber` as part of the template.</span></span>  
  
 [!code-xaml[TreeViewSelectedValue#HierarchicalDataTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSelectedValue/CS/Window1.xaml#hierarchicaldatatemplate)]  
  
 <span data-ttu-id="105f4-112">Aşağıdaki örnekte gösterildiği bir <xref:System.Windows.Controls.TreeView> önceden tanımlanmış kullanan <xref:System.Windows.HierarchicalDataTemplate> ve ayarlayan <xref:System.Windows.Controls.TreeView.SelectedValue%2A> özelliğini `EmployeeNumber`.</span><span class="sxs-lookup"><span data-stu-id="105f4-112">The following example shows a <xref:System.Windows.Controls.TreeView> that uses the previously defined <xref:System.Windows.HierarchicalDataTemplate> and that sets the <xref:System.Windows.Controls.TreeView.SelectedValue%2A> property to the `EmployeeNumber`.</span></span> <span data-ttu-id="105f4-113">Seçtiğinizde, bir `EmployeeName` içinde <xref:System.Windows.Controls.TreeView>, <xref:System.Windows.Controls.TreeView.SelectedItem%2A> özelliği döndürür `EmployeeInfo` seçili karşılık gelen bir veri öğesi `EmployeeName`.</span><span class="sxs-lookup"><span data-stu-id="105f4-113">When you select an `EmployeeName` in the <xref:System.Windows.Controls.TreeView>, the <xref:System.Windows.Controls.TreeView.SelectedItem%2A> property returns the `EmployeeInfo` data item that corresponds to the selected `EmployeeName`.</span></span> <span data-ttu-id="105f4-114">Ancak, çünkü <xref:System.Windows.Controls.TreeView.SelectedValuePath%2A> bu <xref:System.Windows.Controls.TreeView> ayarlanır `EmployeeNumber`, <xref:System.Windows.Controls.TreeView.SelectedValue%2A> ayarlanır `EmployeeNumber`.</span><span class="sxs-lookup"><span data-stu-id="105f4-114">However, because the <xref:System.Windows.Controls.TreeView.SelectedValuePath%2A> of this <xref:System.Windows.Controls.TreeView> is set to `EmployeeNumber`, the <xref:System.Windows.Controls.TreeView.SelectedValue%2A> is set to the `EmployeeNumber`.</span></span>  
  
 [!code-xaml[TreeViewSelectedValue#SelectedValuePath](~/samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSelectedValue/CS/Window1.xaml#selectedvaluepath)]  
  
## <a name="see-also"></a><span data-ttu-id="105f4-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="105f4-115">See also</span></span>

- <xref:System.Windows.Controls.TreeView>
- <xref:System.Windows.Controls.TreeViewItem>
- [<span data-ttu-id="105f4-116">TreeView Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="105f4-116">TreeView Overview</span></span>](treeview-overview.md)
- [<span data-ttu-id="105f4-117">Nasıl Yapılır Konuları</span><span class="sxs-lookup"><span data-stu-id="105f4-117">How-to Topics</span></span>](treeview-how-to-topics.md)
