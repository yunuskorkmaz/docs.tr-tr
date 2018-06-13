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
# <a name="how-to-partition-space-by-using-the-dockpanel-element"></a><span data-ttu-id="bb952-102">Nasıl yapılır: DockPanel Öğesini Kullanarak Boşluğu Bölümleme</span><span class="sxs-lookup"><span data-stu-id="bb952-102">How to: Partition Space by Using the DockPanel Element</span></span>
<span data-ttu-id="bb952-103">Aşağıdaki örnek, basit bir oluşturur [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] framework kullanarak bir <xref:System.Windows.Controls.DockPanel> öğesi.</span><span class="sxs-lookup"><span data-stu-id="bb952-103">The following example creates a simple [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] framework using a <xref:System.Windows.Controls.DockPanel> element.</span></span> <span data-ttu-id="bb952-104"><xref:System.Windows.Controls.DockPanel> Ve alt öğeleri için kullanılabilir boşluğu bölümler.</span><span class="sxs-lookup"><span data-stu-id="bb952-104">The <xref:System.Windows.Controls.DockPanel> partitions available space to its child elements.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bb952-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="bb952-105">Example</span></span>  
 <span data-ttu-id="bb952-106">Bu örnekte <xref:System.Windows.Controls.DockPanel.Dock%2A> iki özdeş sabitlemek için eklenen bir özellik olan özelliği, <xref:System.Windows.Controls.Border> öğeler <xref:System.Windows.Controls.Dock.Top> bölümlenmiş.</span><span class="sxs-lookup"><span data-stu-id="bb952-106">This example uses the <xref:System.Windows.Controls.DockPanel.Dock%2A> property, which is an attached property, to dock two identical <xref:System.Windows.Controls.Border> elements at the <xref:System.Windows.Controls.Dock.Top> of the partitioned space.</span></span> <span data-ttu-id="bb952-107">Üçüncü <xref:System.Windows.Controls.Border> öğesi için yerleştirilmiştir <xref:System.Windows.Controls.Dock.Left>, genişlik 200 piksel olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="bb952-107">A third <xref:System.Windows.Controls.Border> element is docked to the <xref:System.Windows.Controls.Dock.Left>, with its width set to 200 pixels.</span></span> <span data-ttu-id="bb952-108">Dördüncü <xref:System.Windows.Controls.Border> için yerleşik <xref:System.Windows.Controls.Dock.Bottom> ekranın.</span><span class="sxs-lookup"><span data-stu-id="bb952-108">A fourth <xref:System.Windows.Controls.Border> is docked to the <xref:System.Windows.Controls.Dock.Bottom> of the screen.</span></span> <span data-ttu-id="bb952-109">Son <xref:System.Windows.Controls.Border> öğesi kalan alanı otomatik olarak doldurur.</span><span class="sxs-lookup"><span data-stu-id="bb952-109">The last <xref:System.Windows.Controls.Border> element automatically fills the remaining space.</span></span>  
  
 [!code-cpp[DockPanelOvwSample#1](../../../../samples/snippets/cpp/VS_Snippets_Wpf/DockPanelOvwSample/CPP/DockPanel_Ovw_Sample.cpp#1)]
 [!code-csharp[DockPanelOvwSample#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DockPanelOvwSample/CSharp/DockPanel_Ovw_Sample.cs#1)]
 [!code-vb[DockPanelOvwSample#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DockPanelOvwSample/VisualBasic/dockpanel_vb.vb#1)]
 [!code-xaml[DockPanelOvwSample#1](../../../../samples/snippets/xaml/VS_Snippets_Wpf/DockPanelOvwSample/XAML/default.xaml#1)]  
  
> [!NOTE]
>  <span data-ttu-id="bb952-110">Varsayılan olarak, son alt bir <xref:System.Windows.Controls.DockPanel> öğesi doldurur kalan ayrılmamış.</span><span class="sxs-lookup"><span data-stu-id="bb952-110">By default, the last child of a <xref:System.Windows.Controls.DockPanel> element fills the remaining unallocated space.</span></span> <span data-ttu-id="bb952-111">Bu davranış istemiyorsanız ayarlamak `LastChildFill="False"`.</span><span class="sxs-lookup"><span data-stu-id="bb952-111">If you do not want this behavior, set `LastChildFill="False"`.</span></span>  
  
 <span data-ttu-id="bb952-112">Derlenmiş uygulama şöyle yeni bir kullanıcı Arabirimi sağlar.</span><span class="sxs-lookup"><span data-stu-id="bb952-112">The compiled application yields a new UI that looks like this.</span></span>  
  
 <span data-ttu-id="bb952-113">![Tipik bir DockPanel senaryosu. ] (../../../../docs/framework/wpf/controls/media/panel-intro-dockpanel.PNG "panel_intro_dockpanel")</span><span class="sxs-lookup"><span data-stu-id="bb952-113">![A typical DockPanel scenario.](../../../../docs/framework/wpf/controls/media/panel-intro-dockpanel.PNG "panel_intro_dockpanel")</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bb952-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="bb952-114">See Also</span></span>  
 <xref:System.Windows.Controls.DockPanel>  
 [<span data-ttu-id="bb952-115">Panellere Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="bb952-115">Panels Overview</span></span>](../../../../docs/framework/wpf/controls/panels-overview.md)
