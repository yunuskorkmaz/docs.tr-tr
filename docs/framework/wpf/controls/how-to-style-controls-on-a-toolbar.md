---
title: 'Nasıl yapılır: ToolBar Üzerindeki Stil Denetimleri'
ms.date: 03/30/2017
helpviewer_keywords:
- styling controls on toolbar [WPF]
- toolbars [WPF]
- customizing controls on toolbar [WPF]
ms.assetid: ba6ae056-d6a9-4c24-90f8-467ab0bc0b1a
ms.openlocfilehash: 097bb23a41ba68bf9c121a53920f19694508348b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54544867"
---
# <a name="how-to-style-controls-on-a-toolbar"></a>Nasıl yapılır: ToolBar Üzerindeki Stil Denetimleri
<xref:System.Windows.Controls.ToolBar> Tanımlar <xref:System.Windows.ResourceKey> içindeki denetimleri stilini belirlemek için nesneleri <xref:System.Windows.Controls.ToolBar>.  Bir denetimde stilini belirlemek için bir <xref:System.Windows.Controls.ToolBar>ayarlayın `x:key` stil özniteliği bir <xref:System.Windows.ResourceKey> tanımlanan <xref:System.Windows.Controls.ToolBar>.  
  
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
 Aşağıdaki örnek, içindeki denetimler için stiller tanımlar. bir <xref:System.Windows.Controls.ToolBar>.  
  
 [!code-xaml[ToolBar_snip#ToolBarAllStyles](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ToolBar_snip/CS/pane1.xaml#toolbarallstyles)]  
[!code-xaml[ToolBar_snip#ToolBar](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ToolBar_snip/CS/pane1.xaml#toolbar)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Stil ve Şablon Oluşturma](../../../../docs/framework/wpf/controls/styling-and-templating.md)
