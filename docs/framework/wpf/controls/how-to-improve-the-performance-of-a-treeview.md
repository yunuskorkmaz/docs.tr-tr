---
title: "Nasıl yapılır: TreeView'un Performansını Artırma"
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- TreeView control [WPF], improving the performance
ms.assetid: b792c740-cf2b-4da8-8ba8-3d2e5a821874
ms.openlocfilehash: de1b46da2a7c6c3db0c0c19cdbb654fcf2fbbd6c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59153445"
---
# <a name="how-to-improve-the-performance-of-a-treeview"></a><span data-ttu-id="d5452-102">Nasıl yapılır: TreeView'un Performansını Artırma</span><span class="sxs-lookup"><span data-stu-id="d5452-102">How to: Improve the Performance of a TreeView</span></span>
<span data-ttu-id="d5452-103">Varsa bir <xref:System.Windows.Controls.TreeView> sayıda öğe içeriyorsa kullanıcı arabiriminde, yüklemek için gereken süreyi önemli gecikmeye neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="d5452-103">If a <xref:System.Windows.Controls.TreeView> contains many items, the amount of time it takes to load may cause a significant delay in the user interface.</span></span> <span data-ttu-id="d5452-104">Yükleme süresi ayarlayarak iyileştirebilirsiniz `VirtualizingStackPanel.IsVirtualizing` özelliğine bağlı `true`.</span><span class="sxs-lookup"><span data-stu-id="d5452-104">You can improve the load time by setting the `VirtualizingStackPanel.IsVirtualizing` attached property to `true`.</span></span>  <span data-ttu-id="d5452-105">Kullanıcı arabirimini de bir kullanıcı kaydırdığında tepki vermek yavaş olabilir <xref:System.Windows.Controls.TreeView> fare tekerleğini kullanarak veya bir kaydırma çubuğunun sürükleyerek.</span><span class="sxs-lookup"><span data-stu-id="d5452-105">The UI might also be slow to react when a user scrolls the <xref:System.Windows.Controls.TreeView> by using the mouse wheel or dragging the thumb of a scrollbar.</span></span> <span data-ttu-id="d5452-106">Performansını iyileştirebilir <xref:System.Windows.Controls.TreeView> kullanıcı ne zaman kaydırma ayarlayarak `VirtualizingStackPanel.VirtualizationMode` özelliğine bağlı <xref:System.Windows.Controls.VirtualizationMode.Recycling?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="d5452-106">You can improve the performance of the <xref:System.Windows.Controls.TreeView> when the user scrolls by setting the `VirtualizingStackPanel.VirtualizationMode` attached property to <xref:System.Windows.Controls.VirtualizationMode.Recycling?displayProperty=nameWithType>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d5452-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="d5452-107">Example</span></span>  
  
## <a name="description"></a><span data-ttu-id="d5452-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d5452-108">Description</span></span>  
<span data-ttu-id="d5452-109">Aşağıdaki örnek, oluşturur bir <xref:System.Windows.Controls.TreeView> ayarlayan `VirtualizingStackPanel.IsVirtualizing` özelliği true olarak eklenmiş ve `VirtualizingStackPanel.VirtualizationMode` özelliğine bağlı <xref:System.Windows.Controls.VirtualizationMode.Recycling?displayProperty=nameWithType> performansı iyileştirmek için.</span><span class="sxs-lookup"><span data-stu-id="d5452-109">The following example creates a <xref:System.Windows.Controls.TreeView> that sets the `VirtualizingStackPanel.IsVirtualizing` attached property to true and the `VirtualizingStackPanel.VirtualizationMode` attached property to <xref:System.Windows.Controls.VirtualizationMode.Recycling?displayProperty=nameWithType> to optimize its performance.</span></span>  
  
## <a name="code"></a><span data-ttu-id="d5452-110">Kod</span><span class="sxs-lookup"><span data-stu-id="d5452-110">Code</span></span>  
 [!code-xaml[RecycleItemContainerShippets#VirtualizingTreeView](~/samples/snippets/csharp/VS_Snippets_Wpf/RecycleItemContainerShippets/CSharp/Window1.xaml#virtualizingtreeview)]  
  
 <span data-ttu-id="d5452-111">Aşağıdaki örnek, önceki örnekte kullandığı verileri gösterir.</span><span class="sxs-lookup"><span data-stu-id="d5452-111">The following example shows the data that the previous example uses.</span></span>  
  
 [!code-csharp[RecycleItemContainerShippets#TreeViewData](~/samples/snippets/csharp/VS_Snippets_Wpf/RecycleItemContainerShippets/CSharp/Window1.xaml.cs#treeviewdata)]
 [!code-vb[RecycleItemContainerShippets#TreeViewData](~/samples/snippets/visualbasic/VS_Snippets_Wpf/RecycleItemContainerShippets/visualbasic/window1.xaml.vb#treeviewdata)]  
  
## <a name="see-also"></a><span data-ttu-id="d5452-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d5452-112">See also</span></span>

- [<span data-ttu-id="d5452-113">Denetimler</span><span class="sxs-lookup"><span data-stu-id="d5452-113">Controls</span></span>](../advanced/optimizing-performance-controls.md)
