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
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: 4f0af8eac1238c377682bd4880efb89c4d9442db
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33403207"
---
# <a name="get-the-toggle-state-of-a-check-box-using-ui-automation"></a>UI Otomasyonunu Kullanarak Onay Kutusunun Değiştir Durumunu Alma
> [!NOTE]
>  Bu belge yönetilen kullanmak isteyen .NET Framework için tasarlanan [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tanımlanan sınıflar <xref:System.Windows.Automation> ad alanı. Hakkında en yeni bilgiler için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], bkz: [Windows Otomasyon API: UI Otomasyonu](http://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Bu konuda nasıl kullanılacağını gösterir [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] denetim Değiştir durumunu alma.  
  
## <a name="example"></a>Örnek  
 Bu örnekte <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> yöntemi <xref:System.Windows.Automation.AutomationElement> elde etmek için sınıf bir <xref:System.Windows.Automation.TogglePattern> nesne denetimden ve dönüş kendi <xref:System.Windows.Automation.ToggleState> özelliği.  
  
 [!code-csharp[NavigatingWithTreeWalker#1200](../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigatingWithTreeWalker/CSharp/ClientClass.cs#1200)]
 [!code-vb[NavigatingWithTreeWalker#1200](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/NavigatingWithTreeWalker/visualbasic/clientclass.vb#1200)]
