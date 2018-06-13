---
title: 'Nasıl yapılır: DockPanel Öğesini Kullanarak Boşluğu Bölümleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- controls [WPF], DockPanel
- DockPanel control [WPF], partitioning space
- partitioning space [WPF]
ms.assetid: a219b9e5-b205-4438-89b5-0a137ac463ab
ms.openlocfilehash: 6b10fbcd14236f9259dc5772e7f8763c1602d0fe
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33553890"
---
# <a name="how-to-partition-space-by-using-the-dockpanel-element"></a>Nasıl yapılır: DockPanel Öğesini Kullanarak Boşluğu Bölümleme
Aşağıdaki örnek, basit bir oluşturur [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] framework kullanarak bir <xref:System.Windows.Controls.DockPanel> öğesi. <xref:System.Windows.Controls.DockPanel> Ve alt öğeleri için kullanılabilir boşluğu bölümler.  
  
## <a name="example"></a>Örnek  
 Bu örnekte <xref:System.Windows.Controls.DockPanel.Dock%2A> iki özdeş sabitlemek için eklenen bir özellik olan özelliği, <xref:System.Windows.Controls.Border> öğeler <xref:System.Windows.Controls.Dock.Top> bölümlenmiş. Üçüncü <xref:System.Windows.Controls.Border> öğesi için yerleştirilmiştir <xref:System.Windows.Controls.Dock.Left>, genişlik 200 piksel olarak ayarlayın. Dördüncü <xref:System.Windows.Controls.Border> için yerleşik <xref:System.Windows.Controls.Dock.Bottom> ekranın. Son <xref:System.Windows.Controls.Border> öğesi kalan alanı otomatik olarak doldurur.  
  
 [!code-cpp[DockPanelOvwSample#1](../../../../samples/snippets/cpp/VS_Snippets_Wpf/DockPanelOvwSample/CPP/DockPanel_Ovw_Sample.cpp#1)]
 [!code-csharp[DockPanelOvwSample#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DockPanelOvwSample/CSharp/DockPanel_Ovw_Sample.cs#1)]
 [!code-vb[DockPanelOvwSample#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DockPanelOvwSample/VisualBasic/dockpanel_vb.vb#1)]
 [!code-xaml[DockPanelOvwSample#1](../../../../samples/snippets/xaml/VS_Snippets_Wpf/DockPanelOvwSample/XAML/default.xaml#1)]  
  
> [!NOTE]
>  Varsayılan olarak, son alt bir <xref:System.Windows.Controls.DockPanel> öğesi doldurur kalan ayrılmamış. Bu davranış istemiyorsanız ayarlamak `LastChildFill="False"`.  
  
 Derlenmiş uygulama şöyle yeni bir kullanıcı Arabirimi sağlar.  
  
 ![Tipik bir DockPanel senaryosu. ] (../../../../docs/framework/wpf/controls/media/panel-intro-dockpanel.PNG "panel_intro_dockpanel")  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Controls.DockPanel>  
 [Panellere Genel Bakış](../../../../docs/framework/wpf/controls/panels-overview.md)
