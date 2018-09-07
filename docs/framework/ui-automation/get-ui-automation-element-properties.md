---
title: UI Otomasyon Öğesi Özelliklerini Alma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- properties, retrieving
- UI Automation, retrieving properties of elements
ms.assetid: 09576b1a-291f-435c-980e-dee32d899ae1
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: 9876aa894c49ec7af1ecd240e12e0f70eccfd89f
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44083809"
---
# <a name="get-ui-automation-element-properties"></a>UI Otomasyon Öğesi Özelliklerini Alma
> [!NOTE]
>  Bu belge yönetilen kullanmak isteyen .NET Framework için tasarlanan [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tanımlanan sınıflar <xref:System.Windows.Automation> ad alanı. En son bilgileri [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], bkz: [Windows Automation API: UI Otomasyonu](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Bu konu başlığı altında özelliklerini alma işlemi gösterilmektedir bir [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] öğesi.  
  
### <a name="get-a-current-property-value"></a>Geçerli bir özellik değeri Al  
  
1.  Elde <xref:System.Windows.Automation.AutomationElement> almak istediğiniz özelliği.  
  
2.  Çağrı <xref:System.Windows.Automation.AutomationElement.GetCurrentPropertyValue%2A>, ABD'deki <xref:System.Windows.Automation.AutomationElement.Current%2A> özelliği yapısı ve get üyelerini birinden değer.  
  
### <a name="get-a-cached-property-value"></a>Önbelleğe alınan özellik değer alma  
  
1.  Elde <xref:System.Windows.Automation.AutomationElement> almak istediğiniz özelliği. Özelliği içinde belirtilen gerekir <xref:System.Windows.Automation.CacheRequest>.  
  
2.  Çağrı <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A>, ABD'deki <xref:System.Windows.Automation.AutomationElement.Cached%2A> özelliği yapısı ve get üyelerini birinden değer.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, geçerli özelliklerini almak için çeşitli yollar gösterir. bir <xref:System.Windows.Automation.AutomationElement>.  
  
 [!code-csharp[UIAClient_snip#170](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#170)]
 [!code-vb[UIAClient_snip#170](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#170)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [İstemciler İçin UI Otomasyonu Özellikleri](../../../docs/framework/ui-automation/ui-automation-properties-for-clients.md)  
 [UI Otomasyonunda Önbelleğe Almayı Kullanma](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)  
 [UI Otomasyonu İstemcilerinde Önbelleğe Alma](../../../docs/framework/ui-automation/caching-in-ui-automation-clients.md)
