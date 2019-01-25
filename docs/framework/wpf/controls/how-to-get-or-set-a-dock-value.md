---
title: 'Nasıl yapılır: Yerleştirme Değerini Alma veya Ayarlama'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Dock values [WPF], setting
- Dock values [WPF], getting
ms.assetid: fcf4ab8a-c7cd-4835-8d04-de1c999ab4a8
ms.openlocfilehash: 847f8732e1807ab2541d42fe720aacbecb034154
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54738514"
---
# <a name="how-to-get-or-set-a-dock-value"></a><span data-ttu-id="3e0b3-102">Nasıl yapılır: Yerleştirme Değerini Alma veya Ayarlama</span><span class="sxs-lookup"><span data-stu-id="3e0b3-102">How to: Get or Set a Dock Value</span></span>
<span data-ttu-id="3e0b3-103">Aşağıdaki örnek nasıl atanacağını gösterir bir <xref:System.Windows.Controls.Dock> nesnenin değeri.</span><span class="sxs-lookup"><span data-stu-id="3e0b3-103">The following example shows how to assign a <xref:System.Windows.Controls.Dock> value for an object.</span></span> <span data-ttu-id="3e0b3-104">Örnekte <xref:System.Windows.Controls.DockPanel.GetDock%2A> ve <xref:System.Windows.Controls.DockPanel.SetDock%2A> yöntemlerinin <xref:System.Windows.Controls.DockPanel>.</span><span class="sxs-lookup"><span data-stu-id="3e0b3-104">The example uses the <xref:System.Windows.Controls.DockPanel.GetDock%2A> and <xref:System.Windows.Controls.DockPanel.SetDock%2A> methods of <xref:System.Windows.Controls.DockPanel>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3e0b3-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="3e0b3-105">Example</span></span>  
 <span data-ttu-id="3e0b3-106">Örnek örneği oluşturur <xref:System.Windows.Controls.TextBlock> öğesi `txt1`ve atar bir <xref:System.Windows.Controls.Dock> değerini `Top` kullanarak <xref:System.Windows.Controls.DockPanel.SetDock%2A> yöntemi <xref:System.Windows.Controls.DockPanel>.</span><span class="sxs-lookup"><span data-stu-id="3e0b3-106">The example creates an instance of the <xref:System.Windows.Controls.TextBlock> element, `txt1`, and assigns a <xref:System.Windows.Controls.Dock> value of `Top` by using the <xref:System.Windows.Controls.DockPanel.SetDock%2A> method of <xref:System.Windows.Controls.DockPanel>.</span></span> <span data-ttu-id="3e0b3-107">Ardından değerini ekler <xref:System.Windows.Controls.Dock> özelliğini <xref:System.Windows.Controls.TextBlock.Text%2A> , <xref:System.Windows.Controls.TextBlock> kullanarak öğesi <xref:System.Windows.Controls.DockPanel.GetDock%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="3e0b3-107">It then appends the value of the <xref:System.Windows.Controls.Dock> property to the <xref:System.Windows.Controls.TextBlock.Text%2A> of the <xref:System.Windows.Controls.TextBlock> element by using the <xref:System.Windows.Controls.DockPanel.GetDock%2A> method.</span></span> <span data-ttu-id="3e0b3-108">Son olarak, örnek ekler <xref:System.Windows.Controls.TextBlock> üst öğeye <xref:System.Windows.Controls.DockPanel>, `dp1`.</span><span class="sxs-lookup"><span data-stu-id="3e0b3-108">Finally, the example adds the <xref:System.Windows.Controls.TextBlock> element to the parent <xref:System.Windows.Controls.DockPanel>, `dp1`.</span></span>  
  
 [!code-csharp[DockPanelSetDock#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DockPanelSetDock/CSharp/DockPanel_SetDock.cs#1)]
 [!code-vb[DockPanelSetDock#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DockPanelSetDock/VisualBasic/DockPanel_SetDock.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="3e0b3-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3e0b3-109">See also</span></span>
- <xref:System.Windows.Controls.DockPanel>
- <xref:System.Windows.Controls.DockPanel.GetDock%2A>
- <xref:System.Windows.Controls.DockPanel.SetDock%2A>
- [<span data-ttu-id="3e0b3-110">Panellere Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="3e0b3-110">Panels Overview</span></span>](../../../../docs/framework/wpf/controls/panels-overview.md)
