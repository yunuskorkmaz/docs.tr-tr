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
ms.openlocfilehash: 034ec2e57fb3b6a9b3a81f66f6888a68e2c113d7
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59219050"
---
# <a name="how-to-find-a-treeviewitem-in-a-treeview"></a><span data-ttu-id="9e0c3-102">Nasıl yapılır: TreeView İçinde TreeViewItem Bulma</span><span class="sxs-lookup"><span data-stu-id="9e0c3-102">How to: Find a TreeViewItem in a TreeView</span></span>
<span data-ttu-id="9e0c3-103"><xref:System.Windows.Controls.TreeView> Denetimi hiyerarşik verileri görüntülemek için kolay bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="9e0c3-103">The <xref:System.Windows.Controls.TreeView> control provides a convenient way to display hierarchical data.</span></span> <span data-ttu-id="9e0c3-104">Varsa, <xref:System.Windows.Controls.TreeView> bir veri kaynağına bağlı <xref:System.Windows.Controls.TreeView.SelectedItem%2A> özelliği, seçilen veri nesnesinin hızlıca almak kolay bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="9e0c3-104">If your <xref:System.Windows.Controls.TreeView> is bound to a data source, the <xref:System.Windows.Controls.TreeView.SelectedItem%2A> property provides a convenient way for you to quickly retrieve the selected data object.</span></span> <span data-ttu-id="9e0c3-105">Temel alınan veri nesnesi ile çalışmak genellikle en iyisidir ancak bazı durumlarda veri içeren programsal gerekebilir <xref:System.Windows.Controls.TreeViewItem>.</span><span class="sxs-lookup"><span data-stu-id="9e0c3-105">It is typically best to work with the underlying data object, but sometimes you may need to programmatically manipulate the data's containing <xref:System.Windows.Controls.TreeViewItem>.</span></span> <span data-ttu-id="9e0c3-106">Örneğin, program aracılığıyla genişletmeniz gerekebilir <xref:System.Windows.Controls.TreeViewItem>, veya farklı bir öğe seçin <xref:System.Windows.Controls.TreeView>.</span><span class="sxs-lookup"><span data-stu-id="9e0c3-106">For example, you may need to programmatically expand the <xref:System.Windows.Controls.TreeViewItem>, or select a different item in the <xref:System.Windows.Controls.TreeView>.</span></span>  
  
 <span data-ttu-id="9e0c3-107">Bulunacak bir <xref:System.Windows.Controls.TreeViewItem> her düzeyde geçmesi gereken, belirli bir veri nesnesini içeren <xref:System.Windows.Controls.TreeView>.</span><span class="sxs-lookup"><span data-stu-id="9e0c3-107">To find a <xref:System.Windows.Controls.TreeViewItem> that contains a specific data object, you must traverse each level of the <xref:System.Windows.Controls.TreeView>.</span></span> <span data-ttu-id="9e0c3-108">Öğeleri bir <xref:System.Windows.Controls.TreeView> performansını artırmak için ayrıca sanallaştırılabilir.</span><span class="sxs-lookup"><span data-stu-id="9e0c3-108">The items in a <xref:System.Windows.Controls.TreeView> can also be virtualized to improve performance.</span></span> <span data-ttu-id="9e0c3-109">Burada öğeleri sanallaştırılabilir durumda da, sizin de fark ettiğinizden gerekir bir <xref:System.Windows.Controls.TreeViewItem> veri nesnesi içerip içermediğini denetlemek için.</span><span class="sxs-lookup"><span data-stu-id="9e0c3-109">In the case where items might be virtualized, you also must realize a <xref:System.Windows.Controls.TreeViewItem> to check whether it contains the data object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9e0c3-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="9e0c3-110">Example</span></span>  
  
## <a name="description"></a><span data-ttu-id="9e0c3-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9e0c3-111">Description</span></span>  
 <span data-ttu-id="9e0c3-112">Aşağıdaki örnek aramalar bir <xref:System.Windows.Controls.TreeView> belirli bir nesneyi ve nesnenin projenin kapsayan döndürür <xref:System.Windows.Controls.TreeViewItem>.</span><span class="sxs-lookup"><span data-stu-id="9e0c3-112">The following example searches a <xref:System.Windows.Controls.TreeView> for a specific object and returns the object's containing <xref:System.Windows.Controls.TreeViewItem>.</span></span> <span data-ttu-id="9e0c3-113">Örneğin, her sağlar <xref:System.Windows.Controls.TreeViewItem> böylece onun alt öğelerini aranabilir oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="9e0c3-113">The example ensures that each <xref:System.Windows.Controls.TreeViewItem> is instantiated so that its child items can be searched.</span></span> <span data-ttu-id="9e0c3-114">Bu örnek de çalışır <xref:System.Windows.Controls.TreeView> sanallaştırılmış öğeleri kullanmaz.</span><span class="sxs-lookup"><span data-stu-id="9e0c3-114">This example also works if the <xref:System.Windows.Controls.TreeView> does not use virtualized items.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9e0c3-115">Aşağıdaki örnek için çalışır <xref:System.Windows.Controls.TreeView>, temel alınan veri modeli ve aramalar bağımsız olarak her <xref:System.Windows.Controls.TreeViewItem> nesne bulunana kadar.</span><span class="sxs-lookup"><span data-stu-id="9e0c3-115">The following example works for any <xref:System.Windows.Controls.TreeView>, regardless of the underlying data model, and searches every <xref:System.Windows.Controls.TreeViewItem> until the object is found.</span></span> <span data-ttu-id="9e0c3-116">Daha iyi performansa sahip başka bir veri modeli belirtilen nesne için arama, verileri hiyerarşi içinde konumunu izlemenize ve ardından ilgili bulun tekniktir <xref:System.Windows.Controls.TreeViewItem> içinde <xref:System.Windows.Controls.TreeView>.</span><span class="sxs-lookup"><span data-stu-id="9e0c3-116">Another technique that has better performance is to search the data model for the specified object, keep track of its location within the data hierarchy, and then find the corresponding <xref:System.Windows.Controls.TreeViewItem> in the <xref:System.Windows.Controls.TreeView>.</span></span> <span data-ttu-id="9e0c3-117">Ancak, daha iyi performansa sahip teknik bilgi veri modelinin gerektirir ve herhangi için verilen genelleştirilemediği <xref:System.Windows.Controls.TreeView>.</span><span class="sxs-lookup"><span data-stu-id="9e0c3-117">However, the technique that has better performance requires knowledge of the data model and cannot be generalized for any given <xref:System.Windows.Controls.TreeView>.</span></span>  
  
## <a name="code"></a><span data-ttu-id="9e0c3-118">Kod</span><span class="sxs-lookup"><span data-stu-id="9e0c3-118">Code</span></span>  
 [!code-csharp[TreeViewFindTVI#1](~/samples/snippets/csharp/VS_Snippets_Wpf/TreeViewFindTVI/CSharp/MainWindow.xaml.cs#1)]
 [!code-vb[TreeViewFindTVI#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TreeViewFindTVI/VisualBasic/MainWindow.xaml.vb#1)]  
  
 <span data-ttu-id="9e0c3-119">Önceki kod üzerinde özel bir kullanır <xref:System.Windows.Controls.VirtualizingStackPanel> adlı bir yöntem sunan `BringIntoView`.</span><span class="sxs-lookup"><span data-stu-id="9e0c3-119">The previous code relies on a custom <xref:System.Windows.Controls.VirtualizingStackPanel> that exposes a method named `BringIntoView`.</span></span> <span data-ttu-id="9e0c3-120">Aşağıdaki kod özel tanımlar <xref:System.Windows.Controls.VirtualizingStackPanel>.</span><span class="sxs-lookup"><span data-stu-id="9e0c3-120">The following code defines the custom <xref:System.Windows.Controls.VirtualizingStackPanel>.</span></span>  
  
 [!code-csharp[TreeViewFindTVI#2](~/samples/snippets/csharp/VS_Snippets_Wpf/TreeViewFindTVI/CSharp/MainWindow.xaml.cs#2)]
 [!code-vb[TreeViewFindTVI#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TreeViewFindTVI/VisualBasic/MainWindow.xaml.vb#2)]  
  
 <span data-ttu-id="9e0c3-121">Aşağıdaki XAML nasıl oluşturulacağını gösterir. bir <xref:System.Windows.Controls.TreeView> özel kullanan <xref:System.Windows.Controls.VirtualizingStackPanel>.</span><span class="sxs-lookup"><span data-stu-id="9e0c3-121">The following XAML shows how to create a <xref:System.Windows.Controls.TreeView> that uses the custom <xref:System.Windows.Controls.VirtualizingStackPanel>.</span></span>  
  
 [!code-xaml[TreeViewFindTVI#3](~/samples/snippets/csharp/VS_Snippets_Wpf/TreeViewFindTVI/CSharp/MainWindow.xaml#3)]  
  
## <a name="see-also"></a><span data-ttu-id="9e0c3-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9e0c3-122">See also</span></span>

- [<span data-ttu-id="9e0c3-123">TreeView'un Performansını Artırma</span><span class="sxs-lookup"><span data-stu-id="9e0c3-123">Improve the Performance of a TreeView</span></span>](how-to-improve-the-performance-of-a-treeview.md)
