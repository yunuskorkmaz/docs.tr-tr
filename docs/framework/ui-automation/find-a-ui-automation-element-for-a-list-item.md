---
title: "Liste Öğesi İçin UI Otomasyon Öğesi Bulma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- list items, finding elements for
- elements, finding for list items
- UI Automation, finding elements for List items
ms.assetid: c326ad2b-2144-4f64-ae4c-d850c74f95c5
caps.latest.revision: "5"
author: Xansky
ms.author: mhopkins
manager: markl
ms.workload: dotnet
ms.openlocfilehash: a00019e5aaaefaddd94689bd192973d5d5ad175a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="find-a-ui-automation-element-for-a-list-item"></a>Liste Öğesi İçin UI Otomasyon Öğesi Bulma
> [!NOTE]
>  Bu belge yönetilen kullanmak isteyen .NET Framework için tasarlanan [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tanımlanan sınıflar <xref:System.Windows.Automation> ad alanı. Hakkında en yeni bilgiler için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], bkz: [Windows Otomasyon API: UI Otomasyonu](http://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Bu konuda nasıl alınacağını gösteren bir <xref:System.Windows.Automation.AutomationElement> öğenin dizini bilindiğinde listesindeki bir öğeye ait.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, belirli bir öğeyi listeden birini kullanarak almanın iki yolu gösterir <xref:System.Windows.Automation.TreeWalker> ve diğer kullanma <xref:System.Windows.Automation.AutomationElement.FindAll%2A>.  
  
 İlk teknik için daha hızlı olma eğilimindedir [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] denetimleri, ancak ikinci için daha hızlı [!INCLUDE[TLA#tla_wpf](../../../includes/tlasharptla-wpf-md.md)] kontrol eder.  
  
 [!code-csharp[UIAClient_snip#184](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#184)]
 [!code-vb[UIAClient_snip#184](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#184)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [UI Otomasyonu Öğelerini Alma](../../../docs/framework/ui-automation/obtaining-ui-automation-elements.md)
