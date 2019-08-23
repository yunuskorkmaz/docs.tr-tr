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
ms.openlocfilehash: d22a808ce3ab95e3b351408bf4cc372a335da553
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69960192"
---
# <a name="how-to-partition-space-by-using-the-dockpanel-element"></a>Nasıl yapılır: DockPanel Öğesini Kullanarak Boşluğu Bölümleme
Aşağıdaki örnek, bir [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] <xref:System.Windows.Controls.DockPanel> öğesi kullanılarak basit bir çerçeve oluşturur. Bölümler <xref:System.Windows.Controls.DockPanel> , alt öğeleri için kullanılabilir alanı.  
  
## <a name="example"></a>Örnek  
 Bu örnek, bölümlenmiş <xref:System.Windows.Controls.DockPanel.Dock%2A> alanın iki özdeş <xref:System.Windows.Controls.Border> öğesini <xref:System.Windows.Controls.Dock.Top> yerleştirmek için iliştirilmiş bir özellik olan özelliğini kullanır. Üçüncü <xref:System.Windows.Controls.Border> bir öğe, genişliği 200 piksel <xref:System.Windows.Controls.Dock.Left>olarak ayarlanan öğesine yerleştirildi. Dördüncü <xref:System.Windows.Controls.Border> bir, ekranda yerleşiktir <xref:System.Windows.Controls.Dock.Bottom> . Son <xref:System.Windows.Controls.Border> öğe kalan alanı otomatik olarak doldurur.  
  
 [!code-cpp[DockPanelOvwSample#1](~/samples/snippets/cpp/VS_Snippets_Wpf/DockPanelOvwSample/CPP/DockPanel_Ovw_Sample.cpp#1)]
 [!code-csharp[DockPanelOvwSample#1](~/samples/snippets/csharp/VS_Snippets_Wpf/DockPanelOvwSample/CSharp/DockPanel_Ovw_Sample.cs#1)]
 [!code-vb[DockPanelOvwSample#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DockPanelOvwSample/VisualBasic/dockpanel_vb.vb#1)]
 [!code-xaml[DockPanelOvwSample#1](~/samples/snippets/xaml/VS_Snippets_Wpf/DockPanelOvwSample/XAML/default.xaml#1)]  
  
> [!NOTE]
> Varsayılan olarak, bir <xref:System.Windows.Controls.DockPanel> öğenin son alt öğesi kalan ayrılmamış alanı doldurur. Bu davranışı istemiyorsanız, ayarlayın `LastChildFill="False"`.  
  
 Derlenen uygulama, şuna benzeyen yeni bir kullanıcı arabirimi oluşturur.  
  
 ![Tipik bir DockPanel senaryosu.](./media/panel-intro-dockpanel.PNG "panel_intro_dockpanel")  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Controls.DockPanel>
- [Panellere Genel Bakış](panels-overview.md)
