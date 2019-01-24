---
title: "Nasıl yapılır: TreeView'ın Performansını Artırma"
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- TreeView control [WPF], improving the performance
ms.assetid: b792c740-cf2b-4da8-8ba8-3d2e5a821874
ms.openlocfilehash: 3c7bd151e1c8a5f318660cc45702b5b9c98534a8
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54500700"
---
# <a name="how-to-improve-the-performance-of-a-treeview"></a><span data-ttu-id="06acc-102">Nasıl yapılır: TreeView'ın Performansını Artırma</span><span class="sxs-lookup"><span data-stu-id="06acc-102">How to: Improve the Performance of a TreeView</span></span>
<span data-ttu-id="06acc-103">Varsa bir <xref:System.Windows.Controls.TreeView> sayıda öğe içeriyorsa kullanıcı arabiriminde, yüklemek için gereken süreyi önemli gecikmeye neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="06acc-103">If a <xref:System.Windows.Controls.TreeView> contains many items, the amount of time it takes to load may cause a significant delay in the user interface.</span></span> <span data-ttu-id="06acc-104">Yükleme süresi ayarlayarak iyileştirebilirsiniz `VirtualizingStackPanel.IsVirtualizing` özelliğine bağlı `true`.</span><span class="sxs-lookup"><span data-stu-id="06acc-104">You can improve the load time by setting the `VirtualizingStackPanel.IsVirtualizing` attached property to `true`.</span></span>  <span data-ttu-id="06acc-105">Kullanıcı arabirimini de bir kullanıcı kaydırdığında tepki vermek yavaş olabilir <xref:System.Windows.Controls.TreeView> fare tekerleğini kullanarak veya bir kaydırma çubuğunun sürükleyerek.</span><span class="sxs-lookup"><span data-stu-id="06acc-105">The UI might also be slow to react when a user scrolls the <xref:System.Windows.Controls.TreeView> by using the mouse wheel or dragging the thumb of a scrollbar.</span></span> <span data-ttu-id="06acc-106">Performansını iyileştirebilir <xref:System.Windows.Controls.TreeView> kullanıcı ne zaman kaydırma ayarlayarak `VirtualizingStackPanel.VirtualizationMode` özelliğine bağlı <xref:System.Windows.Controls.VirtualizationMode.Recycling?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="06acc-106">You can improve the performance of the <xref:System.Windows.Controls.TreeView> when the user scrolls by setting the `VirtualizingStackPanel.VirtualizationMode` attached property to <xref:System.Windows.Controls.VirtualizationMode.Recycling?displayProperty=nameWithType>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="06acc-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="06acc-107">Example</span></span>  
  
## <a name="description"></a><span data-ttu-id="06acc-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="06acc-108">Description</span></span>  
<span data-ttu-id="06acc-109">Aşağıdaki örnek, oluşturur bir <xref:System.Windows.Controls.TreeView> ayarlayan `VirtualizingStackPanel.IsVirtualizing` özelliği true olarak eklenmiş ve `VirtualizingStackPanel.VirtualizationMode` özelliğine bağlı <xref:System.Windows.Controls.VirtualizationMode.Recycling?displayProperty=nameWithType> performansı iyileştirmek için.</span><span class="sxs-lookup"><span data-stu-id="06acc-109">The following example creates a <xref:System.Windows.Controls.TreeView> that sets the `VirtualizingStackPanel.IsVirtualizing` attached property to true and the `VirtualizingStackPanel.VirtualizationMode` attached property to <xref:System.Windows.Controls.VirtualizationMode.Recycling?displayProperty=nameWithType> to optimize its performance.</span></span>  
  
## <a name="code"></a><span data-ttu-id="06acc-110">Kod</span><span class="sxs-lookup"><span data-stu-id="06acc-110">Code</span></span>  
 [!code-xaml[RecycleItemContainerShippets#VirtualizingTreeView](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RecycleItemContainerShippets/CSharp/Window1.xaml#virtualizingtreeview)]  
  
 <span data-ttu-id="06acc-111">Aşağıdaki örnek, önceki örnekte kullandığı verileri gösterir.</span><span class="sxs-lookup"><span data-stu-id="06acc-111">The following example shows the data that the previous example uses.</span></span>  
  
 [!code-csharp[RecycleItemContainerShippets#TreeViewData](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RecycleItemContainerShippets/CSharp/Window1.xaml.cs#treeviewdata)]
 [!code-vb[RecycleItemContainerShippets#TreeViewData](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/RecycleItemContainerShippets/visualbasic/window1.xaml.vb#treeviewdata)]  
  
## <a name="see-also"></a><span data-ttu-id="06acc-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="06acc-112">See also</span></span>
- [<span data-ttu-id="06acc-113">Denetimler</span><span class="sxs-lookup"><span data-stu-id="06acc-113">Controls</span></span>](../../../../docs/framework/wpf/advanced/optimizing-performance-controls.md)
