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
ms.openlocfilehash: 1b82302ff89d2e8407871cbfba6c10e8322ac4e7
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74435504"
---
# <a name="get-ui-automation-element-properties"></a>UI Otomasyon Öğesi Özelliklerini Alma
> [!NOTE]
> Bu belge, <xref:System.Windows.Automation> ad alanında tanımlanan yönetilen [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] sınıflarını kullanmak isteyen .NET Framework geliştiricilere yöneliktir. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]hakkında en son bilgiler için bkz. [Windows Otomasyonu API: UI Otomasyonu](/windows/win32/winauto/entry-uiauto-win32).  
  
 Bu konu, bir [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] öğesinin özelliklerinin nasıl alınacağını gösterir.  
  
### <a name="get-a-current-property-value"></a>Geçerli özellik değerini Al  
  
1. Özelliğini almak istediğiniz <xref:System.Windows.Automation.AutomationElement> alın.  
  
2. <xref:System.Windows.Automation.AutomationElement.GetCurrentPropertyValue%2A>çağırın veya <xref:System.Windows.Automation.AutomationElement.Current%2A> özellik yapısını alın ve üyelerinden birinden değeri alın.  
  
### <a name="get-a-cached-property-value"></a>Önbelleğe alınmış Özellik değeri alma  
  
1. Özelliğini almak istediğiniz <xref:System.Windows.Automation.AutomationElement> alın. Özelliğin <xref:System.Windows.Automation.CacheRequest>belirtilmiş olması gerekir.  
  
2. <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A>çağırın veya <xref:System.Windows.Automation.AutomationElement.Cached%2A> özellik yapısını alın ve üyelerinden birinden değeri alın.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, <xref:System.Windows.Automation.AutomationElement>geçerli özelliklerini almanın çeşitli yollarını gösterir.  
  
 [!code-csharp[UIAClient_snip#170](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#170)]
 [!code-vb[UIAClient_snip#170](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#170)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [İstemciler İçin UI Otomasyonu Özellikleri](ui-automation-properties-for-clients.md)
- [UI Otomasyonunda Önbelleğe Almayı Kullanma](use-caching-in-ui-automation.md)
- [UI Otomasyonu İstemcilerinde Önbelleğe Alma](caching-in-ui-automation-clients.md)
