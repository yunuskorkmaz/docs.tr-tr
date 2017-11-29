---
title: "UI Otomasyon Öğesi Özelliklerini Alma"
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
- properties, retrieving
- UI Automation, retrieving properties of elements
ms.assetid: 09576b1a-291f-435c-980e-dee32d899ae1
caps.latest.revision: "5"
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: 2b9e1f24a6384cd052dd7b15c7afb3facac05c57
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="get-ui-automation-element-properties"></a>UI Otomasyon Öğesi Özelliklerini Alma
> [!NOTE]
>  Bu belge yönetilen kullanmak isteyen .NET Framework için tasarlanan [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tanımlanan sınıflar <xref:System.Windows.Automation> ad alanı. Hakkında en yeni bilgiler için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], bkz: [Windows Otomasyon API: UI Otomasyonu](http://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Bu konuda, özelliklerini almak gösterilmiştir bir [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] öğesi.  
  
### <a name="get-a-current-property-value"></a>Geçerli bir özellik değeri Al  
  
1.  Elde <xref:System.Windows.Automation.AutomationElement> almak istediğiniz, özelliği.  
  
2.  Çağrı <xref:System.Windows.Automation.AutomationElement.GetCurrentPropertyValue%2A>, ya da almak <xref:System.Windows.Automation.AutomationElement.Current%2A> özelliği yapısı ve get üyeleri birinden değeri.  
  
### <a name="get-a-cached-property-value"></a>Önbelleğe alınan özellik değerini alın  
  
1.  Elde <xref:System.Windows.Automation.AutomationElement> almak istediğiniz, özelliği. Özelliği, belirtilmiş olmalıdır <xref:System.Windows.Automation.CacheRequest>.  
  
2.  Çağrı <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A>, ya da almak <xref:System.Windows.Automation.AutomationElement.Cached%2A> özelliği yapısı ve get üyeleri birinden değeri.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, geçerli özelliklerini almak için çeşitli yollar gösterir bir <xref:System.Windows.Automation.AutomationElement>.  
  
 [!code-csharp[UIAClient_snip#170](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#170)]
 [!code-vb[UIAClient_snip#170](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#170)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [İstemciler için UI Otomasyon özellikleri](../../../docs/framework/ui-automation/ui-automation-properties-for-clients.md)  
 [UI otomasyonda önbelleğe almayı kullanma](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)  
 [UI otomasyonda önbelleğe alma](../../../docs/framework/ui-automation/caching-in-ui-automation-clients.md)
