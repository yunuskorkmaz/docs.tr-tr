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
# <a name="how-to-use-selectedvalue-selectedvaluepath-and-selecteditem"></a><span data-ttu-id="58026-103">Nasıl yapılır: SelectedValue, SelectedValuePath ve SelectedItem Kullanma</span><span class="sxs-lookup"><span data-stu-id="58026-103">How to: Use SelectedValue, SelectedValuePath, and SelectedItem</span></span>
<span data-ttu-id="58026-104">Bu örnek <xref:System.Windows.Controls.TreeView.SelectedValue%2A> <xref:System.Windows.Controls.TreeView.SelectedValuePath%2A> , öğesinin bir değerini belirtmek için ve özelliklerini nasıl kullanacağınızı gösterir <xref:System.Windows.Controls.TreeView.SelectedItem%2A> <xref:System.Windows.Controls.TreeView> .</span><span class="sxs-lookup"><span data-stu-id="58026-104">This example shows how to use the <xref:System.Windows.Controls.TreeView.SelectedValue%2A> and <xref:System.Windows.Controls.TreeView.SelectedValuePath%2A> properties to specify a value for the <xref:System.Windows.Controls.TreeView.SelectedItem%2A> of a <xref:System.Windows.Controls.TreeView>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="58026-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="58026-105">Example</span></span>  
 <span data-ttu-id="58026-106"><xref:System.Windows.Controls.TreeView.SelectedValuePath%2A>Özelliği <xref:System.Windows.Controls.TreeView.SelectedValue%2A> , içinde için bir belirtmek için bir yol sağlar <xref:System.Windows.Controls.TreeView.SelectedItem%2A> <xref:System.Windows.Controls.TreeView> .</span><span class="sxs-lookup"><span data-stu-id="58026-106">The <xref:System.Windows.Controls.TreeView.SelectedValuePath%2A> property provides a way to specify a <xref:System.Windows.Controls.TreeView.SelectedValue%2A> for the <xref:System.Windows.Controls.TreeView.SelectedItem%2A> in a <xref:System.Windows.Controls.TreeView>.</span></span> <span data-ttu-id="58026-107">, <xref:System.Windows.Controls.TreeView.SelectedItem%2A> Koleksiyondaki bir nesneyi temsil eder <xref:System.Windows.Controls.ItemsControl.Items%2A> ve <xref:System.Windows.Controls.TreeView> Seçili öğenin tek bir özelliğinin değerini görüntüler.</span><span class="sxs-lookup"><span data-stu-id="58026-107">The <xref:System.Windows.Controls.TreeView.SelectedItem%2A> represents an object in the <xref:System.Windows.Controls.ItemsControl.Items%2A> collection and the <xref:System.Windows.Controls.TreeView> displays the value of a single property of the selected item.</span></span> <span data-ttu-id="58026-108"><xref:System.Windows.Controls.TreeView.SelectedValuePath%2A>Özelliği, özelliğinin değerini belirlemede kullanılan özelliğin yolunu belirtir <xref:System.Windows.Controls.TreeView.SelectedValue%2A> .</span><span class="sxs-lookup"><span data-stu-id="58026-108">The <xref:System.Windows.Controls.TreeView.SelectedValuePath%2A> property specifies the path to the property that is used to determine the value of the <xref:System.Windows.Controls.TreeView.SelectedValue%2A> property.</span></span> <span data-ttu-id="58026-109">Bu konudaki örneklerde bu kavram gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="58026-109">The examples in this topic illustrate this concept.</span></span>  
  
 <span data-ttu-id="58026-110">Aşağıdaki örnek, <xref:System.Windows.Data.XmlDataProvider> çalışan bilgilerini içeren bir gösterir.</span><span class="sxs-lookup"><span data-stu-id="58026-110">The following example shows an <xref:System.Windows.Data.XmlDataProvider> that contains employee information.</span></span>  
  
 [!code-xaml[TreeViewSelectedValue#XMLDataProvider](~/samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSelectedValue/CS/Window1.xaml#xmldataprovider)]  
  
 <span data-ttu-id="58026-111">Aşağıdaki örnek <xref:System.Windows.HierarchicalDataTemplate> `EmployeeName` , ve ' i görüntüleyen bir tanımlar `EmployeeWorkDay` `Employee` .</span><span class="sxs-lookup"><span data-stu-id="58026-111">The following example defines a <xref:System.Windows.HierarchicalDataTemplate> that displays the `EmployeeName` and `EmployeeWorkDay` of the `Employee`.</span></span> <span data-ttu-id="58026-112">Öğesinin, <xref:System.Windows.HierarchicalDataTemplate> `EmployeeNumber` şablonun parçası olarak belirtmediğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="58026-112">Note that the <xref:System.Windows.HierarchicalDataTemplate> does not specify the `EmployeeNumber` as part of the template.</span></span>  
  
 [!code-xaml[TreeViewSelectedValue#HierarchicalDataTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSelectedValue/CS/Window1.xaml#hierarchicaldatatemplate)]  
  
 <span data-ttu-id="58026-113">Aşağıdaki örnek, <xref:System.Windows.Controls.TreeView> daha önce tanımlanan <xref:System.Windows.HierarchicalDataTemplate> ve özelliğini ' a ayarlayan öğesini gösterir <xref:System.Windows.Controls.TreeView.SelectedValue%2A> `EmployeeNumber` .</span><span class="sxs-lookup"><span data-stu-id="58026-113">The following example shows a <xref:System.Windows.Controls.TreeView> that uses the previously defined <xref:System.Windows.HierarchicalDataTemplate> and that sets the <xref:System.Windows.Controls.TreeView.SelectedValue%2A> property to the `EmployeeNumber`.</span></span> <span data-ttu-id="58026-114">İçinde bir seçtiğinizde `EmployeeName` <xref:System.Windows.Controls.TreeView> , <xref:System.Windows.Controls.TreeView.SelectedItem%2A> özelliği `EmployeeInfo` Seçili öğesine karşılık gelen veri öğesini döndürür `EmployeeName` .</span><span class="sxs-lookup"><span data-stu-id="58026-114">When you select an `EmployeeName` in the <xref:System.Windows.Controls.TreeView>, the <xref:System.Windows.Controls.TreeView.SelectedItem%2A> property returns the `EmployeeInfo` data item that corresponds to the selected `EmployeeName`.</span></span> <span data-ttu-id="58026-115">Ancak, öğesinin ' a ayarlandığı için, olarak <xref:System.Windows.Controls.TreeView.SelectedValuePath%2A> <xref:System.Windows.Controls.TreeView> `EmployeeNumber` <xref:System.Windows.Controls.TreeView.SelectedValue%2A> ayarlanır `EmployeeNumber` .</span><span class="sxs-lookup"><span data-stu-id="58026-115">However, because the <xref:System.Windows.Controls.TreeView.SelectedValuePath%2A> of this <xref:System.Windows.Controls.TreeView> is set to `EmployeeNumber`, the <xref:System.Windows.Controls.TreeView.SelectedValue%2A> is set to the `EmployeeNumber`.</span></span>  
  
 [!code-xaml[TreeViewSelectedValue#SelectedValuePath](~/samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSelectedValue/CS/Window1.xaml#selectedvaluepath)]  
  
## <a name="see-also"></a><span data-ttu-id="58026-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="58026-116">See also</span></span>

- <xref:System.Windows.Controls.TreeView>
- <xref:System.Windows.Controls.TreeViewItem>
- [<span data-ttu-id="58026-117">TreeView Genel Bakışı</span><span class="sxs-lookup"><span data-stu-id="58026-117">TreeView Overview</span></span>](treeview-overview.md)
- [<span data-ttu-id="58026-118">Nasıl Yapılır Konuları</span><span class="sxs-lookup"><span data-stu-id="58026-118">How-to Topics</span></span>](treeview-how-to-topics.md)
