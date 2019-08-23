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
ms.openlocfilehash: ad72c7a7fb11dfe605db4119dde831b47dd7c5a4
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69962089"
---
# <a name="how-to-find-a-treeviewitem-in-a-treeview"></a><span data-ttu-id="24c4e-102">Nasıl yapılır: TreeView İçinde TreeViewItem Bulma</span><span class="sxs-lookup"><span data-stu-id="24c4e-102">How to: Find a TreeViewItem in a TreeView</span></span>
<span data-ttu-id="24c4e-103"><xref:System.Windows.Controls.TreeView> Denetim hiyerarşik verileri göstermek için uygun bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="24c4e-103">The <xref:System.Windows.Controls.TreeView> control provides a convenient way to display hierarchical data.</span></span> <span data-ttu-id="24c4e-104">Bir veri kaynağına bağlıysa <xref:System.Windows.Controls.TreeView.SelectedItem%2A> , özelliği seçili veri nesnesini hızlı bir şekilde almanızı sağlayan uygun bir yol sağlar. <xref:System.Windows.Controls.TreeView></span><span class="sxs-lookup"><span data-stu-id="24c4e-104">If your <xref:System.Windows.Controls.TreeView> is bound to a data source, the <xref:System.Windows.Controls.TreeView.SelectedItem%2A> property provides a convenient way for you to quickly retrieve the selected data object.</span></span> <span data-ttu-id="24c4e-105">Genellikle temel alınan veri nesnesiyle çalışmak en iyisidir, ancak bazen verilerin <xref:System.Windows.Controls.TreeViewItem>birlikte çalışmasını programlı bir şekilde değiştirmeniz gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="24c4e-105">It is typically best to work with the underlying data object, but sometimes you may need to programmatically manipulate the data's containing <xref:System.Windows.Controls.TreeViewItem>.</span></span> <span data-ttu-id="24c4e-106">Örneğin, ' yi programlı bir şekilde genişletmeniz <xref:System.Windows.Controls.TreeViewItem>veya <xref:System.Windows.Controls.TreeView>içinde farklı bir öğe seçmeniz gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="24c4e-106">For example, you may need to programmatically expand the <xref:System.Windows.Controls.TreeViewItem>, or select a different item in the <xref:System.Windows.Controls.TreeView>.</span></span>  
  
 <span data-ttu-id="24c4e-107">Belirli bir veri <xref:System.Windows.Controls.TreeViewItem> nesnesini içeren bir bulmak için, her bir düzeyini <xref:System.Windows.Controls.TreeView>de çapraz geçiş yapmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="24c4e-107">To find a <xref:System.Windows.Controls.TreeViewItem> that contains a specific data object, you must traverse each level of the <xref:System.Windows.Controls.TreeView>.</span></span> <span data-ttu-id="24c4e-108">Ayrıca, içindeki <xref:System.Windows.Controls.TreeView> öğeler de performansı artırmak için sanallaştırılabilir.</span><span class="sxs-lookup"><span data-stu-id="24c4e-108">The items in a <xref:System.Windows.Controls.TreeView> can also be virtualized to improve performance.</span></span> <span data-ttu-id="24c4e-109">Öğelerin sanallaştırılmış olması durumunda, veri nesnesini içerip içermediğini denetlemek için bir <xref:System.Windows.Controls.TreeViewItem> de sağlamalısınız.</span><span class="sxs-lookup"><span data-stu-id="24c4e-109">In the case where items might be virtualized, you also must realize a <xref:System.Windows.Controls.TreeViewItem> to check whether it contains the data object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="24c4e-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="24c4e-110">Example</span></span>  
  
## <a name="description"></a><span data-ttu-id="24c4e-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="24c4e-111">Description</span></span>  
 <span data-ttu-id="24c4e-112">Aşağıdaki örnek, belirli bir <xref:System.Windows.Controls.TreeView> nesne için arar ve nesnenin kendisini <xref:System.Windows.Controls.TreeViewItem>döndürür.</span><span class="sxs-lookup"><span data-stu-id="24c4e-112">The following example searches a <xref:System.Windows.Controls.TreeView> for a specific object and returns the object's containing <xref:System.Windows.Controls.TreeViewItem>.</span></span> <span data-ttu-id="24c4e-113">Örnek, alt öğelerinin aranabilmesi için her birinin <xref:System.Windows.Controls.TreeViewItem> oluşturulmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="24c4e-113">The example ensures that each <xref:System.Windows.Controls.TreeViewItem> is instantiated so that its child items can be searched.</span></span> <span data-ttu-id="24c4e-114">Bu örnek, <xref:System.Windows.Controls.TreeView> sanallaştırılmış öğeleri kullanmıyorsa de işe yarar.</span><span class="sxs-lookup"><span data-stu-id="24c4e-114">This example also works if the <xref:System.Windows.Controls.TreeView> does not use virtualized items.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="24c4e-115">Aşağıdaki örnek, temel alınan veri <xref:System.Windows.Controls.TreeView>modelinden bağımsız olarak her türlü için geçerlidir ve nesne bulunana kadar <xref:System.Windows.Controls.TreeViewItem> her bir arama yapar.</span><span class="sxs-lookup"><span data-stu-id="24c4e-115">The following example works for any <xref:System.Windows.Controls.TreeView>, regardless of the underlying data model, and searches every <xref:System.Windows.Controls.TreeViewItem> until the object is found.</span></span> <span data-ttu-id="24c4e-116">Daha iyi performansa sahip olan başka bir teknik ise, belirtilen nesnenin veri modelini aramak, veri hiyerarşisinde konumunu izlemek ve ' <xref:System.Windows.Controls.TreeViewItem> <xref:System.Windows.Controls.TreeView>de karşılık gelen ' ı bulmasıdır.</span><span class="sxs-lookup"><span data-stu-id="24c4e-116">Another technique that has better performance is to search the data model for the specified object, keep track of its location within the data hierarchy, and then find the corresponding <xref:System.Windows.Controls.TreeViewItem> in the <xref:System.Windows.Controls.TreeView>.</span></span> <span data-ttu-id="24c4e-117">Ancak, daha iyi performansa sahip olan teknik, veri modeli hakkında bilgi gerektirir ve herhangi bir <xref:System.Windows.Controls.TreeView>şekilde genelleştirilemez.</span><span class="sxs-lookup"><span data-stu-id="24c4e-117">However, the technique that has better performance requires knowledge of the data model and cannot be generalized for any given <xref:System.Windows.Controls.TreeView>.</span></span>  
  
## <a name="code"></a><span data-ttu-id="24c4e-118">Kod</span><span class="sxs-lookup"><span data-stu-id="24c4e-118">Code</span></span>  
 [!code-csharp[TreeViewFindTVI#1](~/samples/snippets/csharp/VS_Snippets_Wpf/TreeViewFindTVI/CSharp/MainWindow.xaml.cs#1)]
 [!code-vb[TreeViewFindTVI#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TreeViewFindTVI/VisualBasic/MainWindow.xaml.vb#1)]  
  
 <span data-ttu-id="24c4e-119">Önceki kod, adlı <xref:System.Windows.Controls.VirtualizingStackPanel> `BringIntoView`bir yöntemi kullanıma sunan bir özel kullanır.</span><span class="sxs-lookup"><span data-stu-id="24c4e-119">The previous code relies on a custom <xref:System.Windows.Controls.VirtualizingStackPanel> that exposes a method named `BringIntoView`.</span></span> <span data-ttu-id="24c4e-120">Aşağıdaki kod özel <xref:System.Windows.Controls.VirtualizingStackPanel>tanımlar.</span><span class="sxs-lookup"><span data-stu-id="24c4e-120">The following code defines the custom <xref:System.Windows.Controls.VirtualizingStackPanel>.</span></span>  
  
 [!code-csharp[TreeViewFindTVI#2](~/samples/snippets/csharp/VS_Snippets_Wpf/TreeViewFindTVI/CSharp/MainWindow.xaml.cs#2)]
 [!code-vb[TreeViewFindTVI#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TreeViewFindTVI/VisualBasic/MainWindow.xaml.vb#2)]  
  
 <span data-ttu-id="24c4e-121">Aşağıdaki XAML, özel <xref:System.Windows.Controls.TreeView> <xref:System.Windows.Controls.VirtualizingStackPanel>' i kullanan bir oluşturmayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="24c4e-121">The following XAML shows how to create a <xref:System.Windows.Controls.TreeView> that uses the custom <xref:System.Windows.Controls.VirtualizingStackPanel>.</span></span>  
  
 [!code-xaml[TreeViewFindTVI#3](~/samples/snippets/csharp/VS_Snippets_Wpf/TreeViewFindTVI/CSharp/MainWindow.xaml#3)]  
  
## <a name="see-also"></a><span data-ttu-id="24c4e-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="24c4e-122">See also</span></span>

- [<span data-ttu-id="24c4e-123">TreeView'ın Performansını Artırma</span><span class="sxs-lookup"><span data-stu-id="24c4e-123">Improve the Performance of a TreeView</span></span>](how-to-improve-the-performance-of-a-treeview.md)
