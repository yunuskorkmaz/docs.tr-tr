---
title: "Nasıl yapılır: TreeView İçinde TreeViewItem Bulma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- TreeView control [WPF], finding a TreeViewItem
- TreeViewItem [WPF], finding
ms.assetid: 72ecd40c-3939-4e01-b617-5e9daa6074d9
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 696a9e2d92b9c44e4aedbcc200b41e5548cd7411
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-find-a-treeviewitem-in-a-treeview"></a><span data-ttu-id="864e6-102">Nasıl yapılır: TreeView İçinde TreeViewItem Bulma</span><span class="sxs-lookup"><span data-stu-id="864e6-102">How to: Find a TreeViewItem in a TreeView</span></span>
<span data-ttu-id="864e6-103"><xref:System.Windows.Controls.TreeView> Denetimi hiyerarşik verileri görüntülemek için kullanışlı bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="864e6-103">The <xref:System.Windows.Controls.TreeView> control provides a convenient way to display hierarchical data.</span></span> <span data-ttu-id="864e6-104">Varsa, <xref:System.Windows.Controls.TreeView> bir veri kaynağına bağlı olduğu <xref:System.Windows.Controls.TreeView.SelectedItem%2A> özelliği, hızlı bir şekilde seçili veri nesnesini almak kolay bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="864e6-104">If your <xref:System.Windows.Controls.TreeView> is bound to a data source, the <xref:System.Windows.Controls.TreeView.SelectedItem%2A> property provides a convenient way for you to quickly retrieve the selected data object.</span></span> <span data-ttu-id="864e6-105">Temel alınan veri nesnesi ile çalışmak genellikle en iyisidir, ancak bazen verinin içeren programsal gerekebilir <xref:System.Windows.Controls.TreeViewItem>.</span><span class="sxs-lookup"><span data-stu-id="864e6-105">It is typically best to work with the underlying data object, but sometimes you may need to programmatically manipulate the data's containing <xref:System.Windows.Controls.TreeViewItem>.</span></span> <span data-ttu-id="864e6-106">Örneğin, program aracılığıyla genişletmeniz gerekebilir <xref:System.Windows.Controls.TreeViewItem>, veya farklı bir öğe seçin <xref:System.Windows.Controls.TreeView>.</span><span class="sxs-lookup"><span data-stu-id="864e6-106">For example, you may need to programmatically expand the <xref:System.Windows.Controls.TreeViewItem>, or select a different item in the <xref:System.Windows.Controls.TreeView>.</span></span>  
  
 <span data-ttu-id="864e6-107">Bulmak için bir <xref:System.Windows.Controls.TreeViewItem> belirli veri nesnesi içeren, her düzeyde geçmesi gereken <xref:System.Windows.Controls.TreeView>.</span><span class="sxs-lookup"><span data-stu-id="864e6-107">To find a <xref:System.Windows.Controls.TreeViewItem> that contains a specific data object, you must traverse each level of the <xref:System.Windows.Controls.TreeView>.</span></span> <span data-ttu-id="864e6-108">Öğeleri bir <xref:System.Windows.Controls.TreeView> performansını artırmak için de sanallaştırılabilecek.</span><span class="sxs-lookup"><span data-stu-id="864e6-108">The items in a <xref:System.Windows.Controls.TreeView> can also be virtualized to improve performance.</span></span> <span data-ttu-id="864e6-109">Burada öğeleri sanallaştırılmış durumda, aynı zamanda farkında olun gerekir bir <xref:System.Windows.Controls.TreeViewItem> veri nesnesi içerip içermediğini denetlemek için.</span><span class="sxs-lookup"><span data-stu-id="864e6-109">In the case where items might be virtualized, you also must realize a <xref:System.Windows.Controls.TreeViewItem> to check whether it contains the data object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="864e6-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="864e6-110">Example</span></span>  
  
## <a name="description"></a><span data-ttu-id="864e6-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="864e6-111">Description</span></span>  
 <span data-ttu-id="864e6-112">Aşağıdaki örnek aramalar bir <xref:System.Windows.Controls.TreeView> belirli bir nesnesi ve nesnesini içeren döndürür <xref:System.Windows.Controls.TreeViewItem>.</span><span class="sxs-lookup"><span data-stu-id="864e6-112">The following example searches a <xref:System.Windows.Controls.TreeView> for a specific object and returns the object's containing <xref:System.Windows.Controls.TreeViewItem>.</span></span> <span data-ttu-id="864e6-113">Örneğin, her sağlar <xref:System.Windows.Controls.TreeViewItem> böylece alt öğelerinden aranabilecek örneği.</span><span class="sxs-lookup"><span data-stu-id="864e6-113">The example ensures that each <xref:System.Windows.Controls.TreeViewItem> is instantiated so that its child items can be searched.</span></span> <span data-ttu-id="864e6-114">Bu örnek ayrıca çalışır <xref:System.Windows.Controls.TreeView> sanallaştırılmış öğeleri kullanmaz.</span><span class="sxs-lookup"><span data-stu-id="864e6-114">This example also works if the <xref:System.Windows.Controls.TreeView> does not use virtualized items.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="864e6-115">Aşağıdaki örnek için çalışır <xref:System.Windows.Controls.TreeView>temel alınan veri modeli ve aramaları bağımsız olarak her <xref:System.Windows.Controls.TreeViewItem> nesne bulunana kadar.</span><span class="sxs-lookup"><span data-stu-id="864e6-115">The following example works for any <xref:System.Windows.Controls.TreeView>, regardless of the underlying data model, and searches every <xref:System.Windows.Controls.TreeViewItem> until the object is found.</span></span> <span data-ttu-id="864e6-116">Daha iyi performans sahip başka bir veri modeli belirtilen nesne için arama, verileri hiyerarşi içinde konumunu izlemenize ve karşılık gelen bulmak için bir tekniktir <xref:System.Windows.Controls.TreeViewItem> içinde <xref:System.Windows.Controls.TreeView>.</span><span class="sxs-lookup"><span data-stu-id="864e6-116">Another technique that has better performance is to search the data model for the specified object, keep track of its location within the data hierarchy, and then find the corresponding <xref:System.Windows.Controls.TreeViewItem> in the <xref:System.Windows.Controls.TreeView>.</span></span> <span data-ttu-id="864e6-117">Ancak, daha iyi performans sahip teknik bilgi ve veri modelinin gerektirir ve verilen herhangi için genelleştirilmiş olamaz <xref:System.Windows.Controls.TreeView>.</span><span class="sxs-lookup"><span data-stu-id="864e6-117">However, the technique that has better performance requires knowledge of the data model and cannot be generalized for any given <xref:System.Windows.Controls.TreeView>.</span></span>  
  
## <a name="code"></a><span data-ttu-id="864e6-118">Kod</span><span class="sxs-lookup"><span data-stu-id="864e6-118">Code</span></span>  
 [!code-csharp[TreeViewFindTVI#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TreeViewFindTVI/CSharp/MainWindow.xaml.cs#1)]
 [!code-vb[TreeViewFindTVI#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TreeViewFindTVI/VisualBasic/MainWindow.xaml.vb#1)]  
  
 <span data-ttu-id="864e6-119">Önceki kod üzerinde özel dayanır <xref:System.Windows.Controls.VirtualizingStackPanel> adlı bir yöntemi gösterir `BringIntoView`.</span><span class="sxs-lookup"><span data-stu-id="864e6-119">The previous code relies on a custom <xref:System.Windows.Controls.VirtualizingStackPanel> that exposes a method named `BringIntoView`.</span></span> <span data-ttu-id="864e6-120">Aşağıdaki kod özel tanımlar <xref:System.Windows.Controls.VirtualizingStackPanel>.</span><span class="sxs-lookup"><span data-stu-id="864e6-120">The following code defines the custom <xref:System.Windows.Controls.VirtualizingStackPanel>.</span></span>  
  
 [!code-csharp[TreeViewFindTVI#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TreeViewFindTVI/CSharp/MainWindow.xaml.cs#2)]
 [!code-vb[TreeViewFindTVI#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TreeViewFindTVI/VisualBasic/MainWindow.xaml.vb#2)]  
  
 <span data-ttu-id="864e6-121">Aşağıdaki XAML nasıl oluşturulacağını gösterir bir <xref:System.Windows.Controls.TreeView> özel kullanan <xref:System.Windows.Controls.VirtualizingStackPanel>.</span><span class="sxs-lookup"><span data-stu-id="864e6-121">The following XAML shows how to create a <xref:System.Windows.Controls.TreeView> that uses the custom <xref:System.Windows.Controls.VirtualizingStackPanel>.</span></span>  
  
 [!code-xaml[TreeViewFindTVI#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TreeViewFindTVI/CSharp/MainWindow.xaml#3)]  
  
## <a name="see-also"></a><span data-ttu-id="864e6-122">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="864e6-122">See Also</span></span>  
 [<span data-ttu-id="864e6-123">TreeView'ın Performansını Artırma</span><span class="sxs-lookup"><span data-stu-id="864e6-123">Improve the Performance of a TreeView</span></span>](../../../../docs/framework/wpf/controls/how-to-improve-the-performance-of-a-treeview.md)
