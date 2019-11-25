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
ms.openlocfilehash: bdf4b38e67a7856136224368e86609c135e5ad6f
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73976434"
---
# <a name="how-to-choose-between-stackpanel-and-dockpanel"></a><span data-ttu-id="0f582-102">Nasıl yapılır: StackPanel ve DockPanel Arasında Seçim Yapma</span><span class="sxs-lookup"><span data-stu-id="0f582-102">How to: Choose Between StackPanel and DockPanel</span></span>
<span data-ttu-id="0f582-103">Bu örnek, bir <xref:System.Windows.Controls.Panel>içerik yığdığınızda bir <xref:System.Windows.Controls.StackPanel> veya <xref:System.Windows.Controls.DockPanel> kullanma arasında nasıl seçim yapılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="0f582-103">This example shows how to choose between using a <xref:System.Windows.Controls.StackPanel> or a <xref:System.Windows.Controls.DockPanel> when you stack content in a <xref:System.Windows.Controls.Panel>.</span></span>

## <a name="example"></a><span data-ttu-id="0f582-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="0f582-104">Example</span></span>
 <span data-ttu-id="0f582-105">Alt öğeleri yığmak için <xref:System.Windows.Controls.DockPanel> ya da <xref:System.Windows.Controls.StackPanel> kullanabilirsiniz, ancak iki denetim her zaman aynı sonuçları oluşturmaz.</span><span class="sxs-lookup"><span data-stu-id="0f582-105">Although you can use either <xref:System.Windows.Controls.DockPanel> or <xref:System.Windows.Controls.StackPanel> to stack child elements, the two controls do not always produce the same results.</span></span> <span data-ttu-id="0f582-106">Örneğin, alt öğeleri yerleştirdiğiniz sıra bir <xref:System.Windows.Controls.DockPanel> alt öğelerinin boyutunu etkileyebilir, ancak bir <xref:System.Windows.Controls.StackPanel>olamaz.</span><span class="sxs-lookup"><span data-stu-id="0f582-106">For example, the order that you place child elements can affect the size of child elements in a <xref:System.Windows.Controls.DockPanel> but not in a <xref:System.Windows.Controls.StackPanel>.</span></span> <span data-ttu-id="0f582-107">Bu farklı davranış oluşur çünkü <xref:System.Windows.Controls.StackPanel> [Double. PositiveInfinity](xref:System.Double.PositiveInfinity)içindeki yığınlama yönünde ölçer; Ancak <xref:System.Windows.Controls.DockPanel> yalnızca kullanılabilir boyutu ölçer.</span><span class="sxs-lookup"><span data-stu-id="0f582-107">This different behavior occurs because <xref:System.Windows.Controls.StackPanel> measures in the direction of stacking at [Double.PositiveInfinity](xref:System.Double.PositiveInfinity); however, <xref:System.Windows.Controls.DockPanel> measures only the available size.</span></span>

 <span data-ttu-id="0f582-108">Aşağıdaki örnek, <xref:System.Windows.Controls.DockPanel> ve <xref:System.Windows.Controls.StackPanel>arasındaki bu temel farkı gösterir.</span><span class="sxs-lookup"><span data-stu-id="0f582-108">The following example demonstrates this key difference between <xref:System.Windows.Controls.DockPanel> and <xref:System.Windows.Controls.StackPanel>.</span></span>

 [!code-cpp[StackPanelOvw4#1](~/samples/snippets/cpp/VS_Snippets_Wpf/StackPanelOvw4/CPP/StackPanel_Ovw_Sample4.cpp#1)]
 [!code-csharp[StackPanelOvw4#1](~/samples/snippets/csharp/VS_Snippets_Wpf/StackPanelOvw4/CSharp/StackPanel_Ovw_Sample4.cs#1)]
 [!code-vb[StackPanelOvw4#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StackPanelOvw4/VisualBasic/StackPanelSamp.vb#1)]
 [!code-xaml[StackPanelOvw4#1](~/samples/snippets/xaml/VS_Snippets_Wpf/StackPanelOvw4/XAML/default.xaml#1)]

## <a name="see-also"></a><span data-ttu-id="0f582-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0f582-109">See also</span></span>

- <xref:System.Windows.Controls.StackPanel>
- <xref:System.Windows.Controls.DockPanel>
- [<span data-ttu-id="0f582-110">Panellere Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="0f582-110">Panels Overview</span></span>](panels-overview.md)
