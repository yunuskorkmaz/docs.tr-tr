---
title: UI Otomasyon Öğesi Özelliklerini Alma
description: Bkz. bir UI Otomasyon öğesinin güncel veya önbelleğe alınmış özelliklerinin nasıl alınacağını gösteren yönergeler ve bir örnek.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- properties, retrieving
- UI Automation, retrieving properties of elements
ms.assetid: 09576b1a-291f-435c-980e-dee32d899ae1
ms.openlocfilehash: 277822c9d89046bfbad50df16bce83da7dd45b3b
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87164101"
---
# <a name="get-ui-automation-element-properties"></a>UI Otomasyon Öğesi Özelliklerini Alma
> [!NOTE]
> Bu belge, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ad alanında tanımlanan yönetilen sınıfları kullanmak isteyen .NET Framework geliştiricilere yöneliktir <xref:System.Windows.Automation> . Hakkında en son bilgiler için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] bkz. [WINDOWS Otomasyonu API: UI Otomasyonu](/windows/win32/winauto/entry-uiauto-win32).  
  
 Bu konu, bir öğenin özelliklerinin nasıl alınacağını gösterir [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] .  
  
### <a name="get-a-current-property-value"></a>Geçerli özellik değerini Al  
  
1. Hangi <xref:System.Windows.Automation.AutomationElement> özelliği almak istediğinizi edinin.  
  
2. <xref:System.Windows.Automation.AutomationElement.GetCurrentPropertyValue%2A>Özellik yapısını çağırın ya da alın <xref:System.Windows.Automation.AutomationElement.Current%2A> ve üyelerinden birindeki değeri alın.  
  
### <a name="get-a-cached-property-value"></a>Önbelleğe alınmış Özellik değeri alma  
  
1. Hangi <xref:System.Windows.Automation.AutomationElement> özelliği almak istediğinizi edinin. Özelliği içinde belirtilmiş olmalıdır <xref:System.Windows.Automation.CacheRequest> .  
  
2. <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A>Özellik yapısını çağırın ya da alın <xref:System.Windows.Automation.AutomationElement.Cached%2A> ve üyelerinden birindeki değeri alın.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, öğesinin geçerli özelliklerini almanın çeşitli yollarını gösterir <xref:System.Windows.Automation.AutomationElement> .  
  
 [!code-csharp[UIAClient_snip#170](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#170)]
 [!code-vb[UIAClient_snip#170](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#170)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [İstemciler İçin UI Otomasyon Özellikleri](ui-automation-properties-for-clients.md)
- [UI Otomasyonda Önbelleğe Almayı Kullanma](use-caching-in-ui-automation.md)
- [UI Otomasyonda Önbelleğe Alma](caching-in-ui-automation-clients.md)
