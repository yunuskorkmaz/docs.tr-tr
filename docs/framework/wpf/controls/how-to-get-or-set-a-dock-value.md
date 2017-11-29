---
title: "Nasıl yapılır: Yerleştirme Değerini Alma veya Ayarlama"
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
- Dock values [WPF], setting
- Dock values [WPF], getting
ms.assetid: fcf4ab8a-c7cd-4835-8d04-de1c999ab4a8
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 8ca4d7e753282a7c1d2236a70535e10d5109cd3c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-get-or-set-a-dock-value"></a><span data-ttu-id="5a174-102">Nasıl yapılır: Yerleştirme Değerini Alma veya Ayarlama</span><span class="sxs-lookup"><span data-stu-id="5a174-102">How to: Get or Set a Dock Value</span></span>
<span data-ttu-id="5a174-103">Aşağıdaki örnekte nasıl atanacağını gösterir bir <xref:System.Windows.Controls.Dock> bir nesne değeri.</span><span class="sxs-lookup"><span data-stu-id="5a174-103">The following example shows how to assign a <xref:System.Windows.Controls.Dock> value for an object.</span></span> <span data-ttu-id="5a174-104">Örnek kullanır <xref:System.Windows.Controls.DockPanel.GetDock%2A> ve <xref:System.Windows.Controls.DockPanel.SetDock%2A> yöntemlerini <xref:System.Windows.Controls.DockPanel>.</span><span class="sxs-lookup"><span data-stu-id="5a174-104">The example uses the <xref:System.Windows.Controls.DockPanel.GetDock%2A> and <xref:System.Windows.Controls.DockPanel.SetDock%2A> methods of <xref:System.Windows.Controls.DockPanel>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5a174-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="5a174-105">Example</span></span>  
 <span data-ttu-id="5a174-106">Örnek bir örneğini oluşturur <xref:System.Windows.Controls.TextBlock> öğesi, `txt1`ve atar bir <xref:System.Windows.Controls.Dock> değerini `Top` kullanarak <xref:System.Windows.Controls.DockPanel.SetDock%2A> yöntemi <xref:System.Windows.Controls.DockPanel>.</span><span class="sxs-lookup"><span data-stu-id="5a174-106">The example creates an instance of the <xref:System.Windows.Controls.TextBlock> element, `txt1`, and assigns a <xref:System.Windows.Controls.Dock> value of `Top` by using the <xref:System.Windows.Controls.DockPanel.SetDock%2A> method of <xref:System.Windows.Controls.DockPanel>.</span></span> <span data-ttu-id="5a174-107">Ardından değerini ekler <xref:System.Windows.Controls.Dock> özelliğine <xref:System.Windows.Controls.TextBlock.Text%2A> , <xref:System.Windows.Controls.TextBlock> kullanarak öğesi <xref:System.Windows.Controls.DockPanel.GetDock%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="5a174-107">It then appends the value of the <xref:System.Windows.Controls.Dock> property to the <xref:System.Windows.Controls.TextBlock.Text%2A> of the <xref:System.Windows.Controls.TextBlock> element by using the <xref:System.Windows.Controls.DockPanel.GetDock%2A> method.</span></span> <span data-ttu-id="5a174-108">Son olarak, örnek ekler <xref:System.Windows.Controls.TextBlock> üst öğeye <xref:System.Windows.Controls.DockPanel>, `dp1`.</span><span class="sxs-lookup"><span data-stu-id="5a174-108">Finally, the example adds the <xref:System.Windows.Controls.TextBlock> element to the parent <xref:System.Windows.Controls.DockPanel>, `dp1`.</span></span>  
  
 [!code-csharp[DockPanelSetDock#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DockPanelSetDock/CSharp/DockPanel_SetDock.cs#1)]
 [!code-vb[DockPanelSetDock#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DockPanelSetDock/VisualBasic/DockPanel_SetDock.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="5a174-109">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="5a174-109">See Also</span></span>  
 <xref:System.Windows.Controls.DockPanel>  
 <xref:System.Windows.Controls.DockPanel.GetDock%2A>  
 <xref:System.Windows.Controls.DockPanel.SetDock%2A>  
 [<span data-ttu-id="5a174-110">Paneller Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="5a174-110">Panels Overview</span></span>](../../../../docs/framework/wpf/controls/panels-overview.md)
