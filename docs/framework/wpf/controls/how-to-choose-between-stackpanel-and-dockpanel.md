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
# <a name="how-to-choose-between-stackpanel-and-dockpanel"></a>Nasıl yapılır: StackPanel ve DockPanel Arasında Seçim Yapma
Bu örnek nasıl kullanma arasında seçim gösterir bir <xref:System.Windows.Controls.StackPanel> veya <xref:System.Windows.Controls.DockPanel> içeriğinde yığın ne zaman bir <xref:System.Windows.Controls.Panel>.  
  
## <a name="example"></a>Örnek  
 Ya da kullanabilirsiniz, ancak <xref:System.Windows.Controls.DockPanel> veya <xref:System.Windows.Controls.StackPanel> alt öğeleri yığma için iki denetimi her zaman aynı sonuçları üretmez. Örneğin, alt öğeleri yerleştirme alt öğeleri boyutunu etkileyebilir bir <xref:System.Windows.Controls.DockPanel> fakat bir <xref:System.Windows.Controls.StackPanel>. Bu farklı davranış <xref:System.Windows.Controls.StackPanel> yığının yönde ölçüler <xref:System.Double>.<xref:System.Double.PositiveInfinity>; ancak <xref:System.Windows.Controls.DockPanel> yalnızca kullanılabilir boyutunu ölçer.  
  
 Aşağıdaki örnek, bu temel farkı göstermektedir <xref:System.Windows.Controls.DockPanel> ve <xref:System.Windows.Controls.StackPanel>.  
  
 [!code-cpp[StackPanelOvw4#1](~/samples/snippets/cpp/VS_Snippets_Wpf/StackPanelOvw4/CPP/StackPanel_Ovw_Sample4.cpp#1)]
 [!code-csharp[StackPanelOvw4#1](~/samples/snippets/csharp/VS_Snippets_Wpf/StackPanelOvw4/CSharp/StackPanel_Ovw_Sample4.cs#1)]
 [!code-vb[StackPanelOvw4#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StackPanelOvw4/VisualBasic/StackPanelSamp.vb#1)]
 [!code-xaml[StackPanelOvw4#1](~/samples/snippets/xaml/VS_Snippets_Wpf/StackPanelOvw4/XAML/default.xaml#1)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Controls.StackPanel>
- <xref:System.Windows.Controls.DockPanel>
- [Panellere Genel Bakış](panels-overview.md)
