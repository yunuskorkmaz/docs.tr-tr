---
title: UI Otomasyonunu Kullanarak Onay Kutusunun Değiştir Durumunu Alma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- UI Automation, getting toggle states of check boxes
- check boxes, getting toggle states of
- getting, toggle states of check boxes
ms.assetid: 84fc31a3-175f-4e93-90a0-dd29d89b77ce
ms.openlocfilehash: 42dc9c679f877b0136cac12eae232e4365f79bdf
ms.sourcegitcommit: 58fc0e6564a37fa1b9b1b140a637e864c4cf696e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2019
ms.locfileid: "57676622"
---
# <a name="get-the-toggle-state-of-a-check-box-using-ui-automation"></a>UI Otomasyonunu Kullanarak Onay Kutusunun Değiştir Durumunu Alma
> [!NOTE]
>  Bu belge yönetilen kullanmak isteyen .NET Framework için tasarlanan [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tanımlanan sınıflar <xref:System.Windows.Automation> ad alanı. En son bilgileri [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], bkz: [Windows Automation API: UI Otomasyonu](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Bu konu nasıl kullanılacağını gösterir [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] bir denetimi Değiştir durumunu alma için.  
  
## <a name="example"></a>Örnek  
 Bu örnekte <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> yöntemi <xref:System.Windows.Automation.AutomationElement> almak için bir <xref:System.Windows.Automation.TogglePattern> nesne denetimden ve dönüş kendi <xref:System.Windows.Automation.ToggleState> özelliği.  
  
 [!code-csharp[NavigatingWithTreeWalker#1200](../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigatingWithTreeWalker/CSharp/ClientClass.cs#1200)]
 [!code-vb[NavigatingWithTreeWalker#1200](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/NavigatingWithTreeWalker/visualbasic/clientclass.vb#1200)]
