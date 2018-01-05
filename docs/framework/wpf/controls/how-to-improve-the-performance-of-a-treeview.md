---
title: "Nasıl yapılır: TreeView'ın Performansını Artırma"
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
helpviewer_keywords: TreeView control [WPF], improving the performance
ms.assetid: b792c740-cf2b-4da8-8ba8-3d2e5a821874
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2c13a9c89bdcb149df61f26177ea8705e502402f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-improve-the-performance-of-a-treeview"></a><span data-ttu-id="4ce12-102">Nasıl yapılır: TreeView'ın Performansını Artırma</span><span class="sxs-lookup"><span data-stu-id="4ce12-102">How to: Improve the Performance of a TreeView</span></span>
<span data-ttu-id="4ce12-103">Varsa bir <xref:System.Windows.Controls.TreeView> sayıda öğe içeriyorsa kullanıcı arabiriminde geçen yüklemek için süreyi önemli gecikmeye neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="4ce12-103">If a <xref:System.Windows.Controls.TreeView> contains many items, the amount of time it takes to load may cause a significant delay in the user interface.</span></span> <span data-ttu-id="4ce12-104">Ayarlayarak yükleme süresini artırabilir `VirtualizingStackPanel.IsVirtualizing` özelliğine bağlı `true`.</span><span class="sxs-lookup"><span data-stu-id="4ce12-104">You can improve the load time by setting the `VirtualizingStackPanel.IsVirtualizing` attached property to `true`.</span></span>  <span data-ttu-id="4ce12-105">UI Ayrıca kullanıcı kaydırdığında tepki vermek yavaş olabilir <xref:System.Windows.Controls.TreeView> fare tekerleği kullanarak veya bir kaydırma çubuğu sürükleyerek.</span><span class="sxs-lookup"><span data-stu-id="4ce12-105">The UI might also be slow to react when a user scrolls the <xref:System.Windows.Controls.TreeView> by using the mouse wheel or dragging the thumb of a scrollbar.</span></span> <span data-ttu-id="4ce12-106">Performansını artırabilir <xref:System.Windows.Controls.TreeView> kullanıcı ne zaman kayar ayarlayarak `VirtualizingStackPanel.VirtualizationMode` özelliğine bağlı <xref:System.Windows.Controls.VirtualizationMode.Recycling?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="4ce12-106">You can improve the performance of the <xref:System.Windows.Controls.TreeView> when the user scrolls by setting the `VirtualizingStackPanel.VirtualizationMode` attached property to <xref:System.Windows.Controls.VirtualizationMode.Recycling?displayProperty=nameWithType>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4ce12-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="4ce12-107">Example</span></span>  
  
## <a name="description"></a><span data-ttu-id="4ce12-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4ce12-108">Description</span></span>  
<span data-ttu-id="4ce12-109">Aşağıdaki örnekte bir <xref:System.Windows.Controls.TreeView> ayarlayan `VirtualizingStackPanel.IsVirtualizing` özelliği true olarak eklenmiş ve `VirtualizingStackPanel.VirtualizationMode` özelliğine bağlı <xref:System.Windows.Controls.VirtualizationMode.Recycling?displayProperty=nameWithType> performansı iyileştirmek için.</span><span class="sxs-lookup"><span data-stu-id="4ce12-109">The following example creates a <xref:System.Windows.Controls.TreeView> that sets the `VirtualizingStackPanel.IsVirtualizing` attached property to true and the `VirtualizingStackPanel.VirtualizationMode` attached property to <xref:System.Windows.Controls.VirtualizationMode.Recycling?displayProperty=nameWithType> to optimize its performance.</span></span>  
  
## <a name="code"></a><span data-ttu-id="4ce12-110">Kod</span><span class="sxs-lookup"><span data-stu-id="4ce12-110">Code</span></span>  
 [!code-xaml[RecycleItemContainerShippets#VirtualizingTreeView](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RecycleItemContainerShippets/CSharp/Window1.xaml#virtualizingtreeview)]  
  
 <span data-ttu-id="4ce12-111">Aşağıdaki örnek, önceki örnekte kullandığı verileri gösterir.</span><span class="sxs-lookup"><span data-stu-id="4ce12-111">The following example shows the data that the previous example uses.</span></span>  
  
 [!code-csharp[RecycleItemContainerShippets#TreeViewData](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RecycleItemContainerShippets/CSharp/Window1.xaml.cs#treeviewdata)]
 [!code-vb[RecycleItemContainerShippets#TreeViewData](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/RecycleItemContainerShippets/visualbasic/window1.xaml.vb#treeviewdata)]  
  
## <a name="see-also"></a><span data-ttu-id="4ce12-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="4ce12-112">See Also</span></span>  
 [<span data-ttu-id="4ce12-113">Denetimler</span><span class="sxs-lookup"><span data-stu-id="4ce12-113">Controls</span></span>](../../../../docs/framework/wpf/advanced/optimizing-performance-controls.md)
