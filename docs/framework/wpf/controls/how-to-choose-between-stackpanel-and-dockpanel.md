---
title: 'Nasıl yapılır: StackPanel ve DockPanel Arasında Seçim Yapma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- controls [WPF], DockPanel
- DockPanel control [WPF], StackPanel control compared to
- StackPanel control [WPF], DockPanel control compared to
- controls [WPF], StackPanel
ms.assetid: f9239086-451f-42e6-81f7-ef89ef349742
ms.openlocfilehash: 8338421dfb1bea856c15edf9d324cec955584f9f
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59206973"
---
# <a name="how-to-choose-between-stackpanel-and-dockpanel"></a><span data-ttu-id="30088-102">Nasıl yapılır: StackPanel ve DockPanel Arasında Seçim Yapma</span><span class="sxs-lookup"><span data-stu-id="30088-102">How to: Choose Between StackPanel and DockPanel</span></span>
<span data-ttu-id="30088-103">Bu örnek nasıl kullanma arasında seçim gösterir bir <xref:System.Windows.Controls.StackPanel> veya <xref:System.Windows.Controls.DockPanel> içeriğinde yığın ne zaman bir <xref:System.Windows.Controls.Panel>.</span><span class="sxs-lookup"><span data-stu-id="30088-103">This example shows how to choose between using a <xref:System.Windows.Controls.StackPanel> or a <xref:System.Windows.Controls.DockPanel> when you stack content in a <xref:System.Windows.Controls.Panel>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="30088-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="30088-104">Example</span></span>  
 <span data-ttu-id="30088-105">Ya da kullanabilirsiniz, ancak <xref:System.Windows.Controls.DockPanel> veya <xref:System.Windows.Controls.StackPanel> alt öğeleri yığma için iki denetimi her zaman aynı sonuçları üretmez.</span><span class="sxs-lookup"><span data-stu-id="30088-105">Although you can use either <xref:System.Windows.Controls.DockPanel> or <xref:System.Windows.Controls.StackPanel> to stack child elements, the two controls do not always produce the same results.</span></span> <span data-ttu-id="30088-106">Örneğin, alt öğeleri yerleştirme alt öğeleri boyutunu etkileyebilir bir <xref:System.Windows.Controls.DockPanel> fakat bir <xref:System.Windows.Controls.StackPanel>.</span><span class="sxs-lookup"><span data-stu-id="30088-106">For example, the order that you place child elements can affect the size of child elements in a <xref:System.Windows.Controls.DockPanel> but not in a <xref:System.Windows.Controls.StackPanel>.</span></span> <span data-ttu-id="30088-107">Bu farklı davranış <xref:System.Windows.Controls.StackPanel> yığının yönde ölçüler <xref:System.Double>.<xref:System.Double.PositiveInfinity>; ancak <xref:System.Windows.Controls.DockPanel> yalnızca kullanılabilir boyutunu ölçer.</span><span class="sxs-lookup"><span data-stu-id="30088-107">This different behavior occurs because <xref:System.Windows.Controls.StackPanel> measures in the direction of stacking at <xref:System.Double>.<xref:System.Double.PositiveInfinity>; however, <xref:System.Windows.Controls.DockPanel> measures only the available size.</span></span>  
  
 <span data-ttu-id="30088-108">Aşağıdaki örnek, bu temel farkı göstermektedir <xref:System.Windows.Controls.DockPanel> ve <xref:System.Windows.Controls.StackPanel>.</span><span class="sxs-lookup"><span data-stu-id="30088-108">The following example demonstrates this key difference between <xref:System.Windows.Controls.DockPanel> and <xref:System.Windows.Controls.StackPanel>.</span></span>  
  
 [!code-cpp[StackPanelOvw4#1](~/samples/snippets/cpp/VS_Snippets_Wpf/StackPanelOvw4/CPP/StackPanel_Ovw_Sample4.cpp#1)]
 [!code-csharp[StackPanelOvw4#1](~/samples/snippets/csharp/VS_Snippets_Wpf/StackPanelOvw4/CSharp/StackPanel_Ovw_Sample4.cs#1)]
 [!code-vb[StackPanelOvw4#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StackPanelOvw4/VisualBasic/StackPanelSamp.vb#1)]
 [!code-xaml[StackPanelOvw4#1](~/samples/snippets/xaml/VS_Snippets_Wpf/StackPanelOvw4/XAML/default.xaml#1)]  
  
## <a name="see-also"></a><span data-ttu-id="30088-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="30088-109">See also</span></span>

- <xref:System.Windows.Controls.StackPanel>
- <xref:System.Windows.Controls.DockPanel>
- [<span data-ttu-id="30088-110">Panellere Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="30088-110">Panels Overview</span></span>](panels-overview.md)
