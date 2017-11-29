---
title: "Nasıl yapılır: ToolBar Üzerindeki Stil Denetimleri"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- styling controls on toolbar [WPF]
- toolbars [WPF]
- customizing controls on toolbar [WPF]
ms.assetid: ba6ae056-d6a9-4c24-90f8-467ab0bc0b1a
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: ce090ace11262e4809dbecadd5fe89d7dfaf62e5
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-style-controls-on-a-toolbar"></a>Nasıl yapılır: ToolBar Üzerindeki Stil Denetimleri
<xref:System.Windows.Controls.ToolBar> Tanımlar <xref:System.Windows.ResourceKey> içindeki denetimlerin stilini belirlemek için nesneleri <xref:System.Windows.Controls.ToolBar>.  Bir denetimde stilini belirlemek için bir <xref:System.Windows.Controls.ToolBar>ayarlayın `x:key` stil özniteliği bir <xref:System.Windows.ResourceKey> tanımlanan <xref:System.Windows.Controls.ToolBar>.  
  
 <xref:System.Windows.Controls.ToolBar> Aşağıdaki tanımlar <xref:System.Windows.ResourceKey> nesneler:  
  
-   <xref:System.Windows.Controls.ToolBar.ButtonStyleKey%2A>  
  
-   <xref:System.Windows.Controls.ToolBar.CheckBoxStyleKey%2A>  
  
-   <xref:System.Windows.Controls.ToolBar.ComboBoxStyleKey%2A>  
  
-   <xref:System.Windows.Controls.ToolBar.MenuStyleKey%2A>  
  
-   <xref:System.Windows.Controls.ToolBar.RadioButtonStyleKey%2A>  
  
-   <xref:System.Windows.Controls.ToolBar.SeparatorStyleKey%2A>  
  
-   <xref:System.Windows.Controls.ToolBar.TextBoxStyleKey%2A>  
  
-   <xref:System.Windows.Controls.ToolBar.ToggleButtonStyleKey%2A>  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek içindeki denetimler için stiller tanımlar bir <xref:System.Windows.Controls.ToolBar>.  
  
 [!code-xaml[ToolBar_snip#ToolBarAllStyles](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ToolBar_snip/CS/pane1.xaml#toolbarallstyles)]  
[!code-xaml[ToolBar_snip#ToolBar](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ToolBar_snip/CS/pane1.xaml#toolbar)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Stil ve şablon oluşturma](../../../../docs/framework/wpf/controls/styling-and-templating.md)
