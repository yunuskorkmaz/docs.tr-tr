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
ms.openlocfilehash: ab51270644bf370944ebc933c765b40c528681c5
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62052189"
---
# <a name="how-to-partition-space-by-using-the-dockpanel-element"></a>Nasıl yapılır: DockPanel Öğesini Kullanarak Boşluğu Bölümleme
Aşağıdaki örnek, basit bir oluşturur [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] framework kullanarak bir <xref:System.Windows.Controls.DockPanel> öğesi. <xref:System.Windows.Controls.DockPanel> Bölümleri alt öğeleri için kullanılabilir alanı.  
  
## <a name="example"></a>Örnek  
 Bu örnekte <xref:System.Windows.Controls.DockPanel.Dock%2A> iki özdeş sabitlemek için ekli özelliği, özelliğinin <xref:System.Windows.Controls.Border> öğeler <xref:System.Windows.Controls.Dock.Top> bölümlenmiş. Bir üçüncü <xref:System.Windows.Controls.Border> öğesi yerleştirilmiştir <xref:System.Windows.Controls.Dock.Left>, kendi genişlikle 200 piksel olarak ayarlayın. Dördüncü <xref:System.Windows.Controls.Border> dayandığı <xref:System.Windows.Controls.Dock.Bottom> ekran. Son <xref:System.Windows.Controls.Border> öğesi kalan alanı otomatik olarak doldurur.  
  
 [!code-cpp[DockPanelOvwSample#1](~/samples/snippets/cpp/VS_Snippets_Wpf/DockPanelOvwSample/CPP/DockPanel_Ovw_Sample.cpp#1)]
 [!code-csharp[DockPanelOvwSample#1](~/samples/snippets/csharp/VS_Snippets_Wpf/DockPanelOvwSample/CSharp/DockPanel_Ovw_Sample.cs#1)]
 [!code-vb[DockPanelOvwSample#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DockPanelOvwSample/VisualBasic/dockpanel_vb.vb#1)]
 [!code-xaml[DockPanelOvwSample#1](~/samples/snippets/xaml/VS_Snippets_Wpf/DockPanelOvwSample/XAML/default.xaml#1)]  
  
> [!NOTE]
>  Varsayılan olarak, son alt bir <xref:System.Windows.Controls.DockPanel> öğesi doldurur kalan ayrılmamış. Bu davranışı istemiyorsanız ayarlamak `LastChildFill="False"`.  
  
 Derlenmiş uygulama şuna benzer yeni bir kullanıcı Arabirimi sağlar.  
  
 ![Tipik bir DockPanel senaryo. ](./media/panel-intro-dockpanel.PNG "panel_intro_dockpanel")  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Controls.DockPanel>
- [Panellere Genel Bakış](panels-overview.md)
