---
title: "Nasıl yapılır: StackPanel ve DockPanel Arasında Seçim Yapma"
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
- cpp
helpviewer_keywords:
- controls [WPF], DockPanel
- DockPanel control [WPF], StackPanel control compared to
- StackPanel control [WPF], DockPanel control compared to
- controls [WPF], StackPanel
ms.assetid: f9239086-451f-42e6-81f7-ef89ef349742
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0274a0f078c378a101bdf4a4ae456fd2ce9f4185
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-choose-between-stackpanel-and-dockpanel"></a>Nasıl yapılır: StackPanel ve DockPanel Arasında Seçim Yapma
Bu örnek, kullanma arasında seçim yapma gösterir bir <xref:System.Windows.Controls.StackPanel> veya <xref:System.Windows.Controls.DockPanel> yığın zaman içeriğinde bir <xref:System.Windows.Controls.Panel>.  
  
## <a name="example"></a>Örnek  
 Ya da kullanabilirsiniz ancak <xref:System.Windows.Controls.DockPanel> veya <xref:System.Windows.Controls.StackPanel> alt öğeleri yığmak için iki denetimi her zaman aynı sonucu vermez. Örneğin, alt öğelerini yerleştirme alt öğelerinin boyutunu etkileyebilecek bir <xref:System.Windows.Controls.DockPanel> de bir <xref:System.Windows.Controls.StackPanel>. Bu farklı davranış <xref:System.Windows.Controls.StackPanel> ölçüleri yığının yönde <xref:System.Double>.<xref:System.Double.PositiveInfinity>; ancak, <xref:System.Windows.Controls.DockPanel> yalnızca kullanılabilir boyutu ölçer.  
  
 Aşağıdaki örnek, bu arasındaki temel farklılık gösterir <xref:System.Windows.Controls.DockPanel> ve <xref:System.Windows.Controls.StackPanel>.  
  
 [!code-cpp[StackPanelOvw4#1](../../../../samples/snippets/cpp/VS_Snippets_Wpf/StackPanelOvw4/CPP/StackPanel_Ovw_Sample4.cpp#1)]
 [!code-csharp[StackPanelOvw4#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StackPanelOvw4/CSharp/StackPanel_Ovw_Sample4.cs#1)]
 [!code-vb[StackPanelOvw4#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/StackPanelOvw4/VisualBasic/StackPanelSamp.vb#1)]
 [!code-xaml[StackPanelOvw4#1](../../../../samples/snippets/xaml/VS_Snippets_Wpf/StackPanelOvw4/XAML/default.xaml#1)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Controls.StackPanel>  
 <xref:System.Windows.Controls.DockPanel>  
 [Panellere Genel Bakış](../../../../docs/framework/wpf/controls/panels-overview.md)
