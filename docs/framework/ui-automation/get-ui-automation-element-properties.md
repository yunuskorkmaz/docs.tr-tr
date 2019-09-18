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
ms.openlocfilehash: 158ebf29bb504dd11f9e8416011226fc5846873e
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71043607"
---
# <a name="get-ui-automation-element-properties"></a>UI Otomasyon Öğesi Özelliklerini Alma
> [!NOTE]
> Bu belge, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] <xref:System.Windows.Automation> ad alanında tanımlanan yönetilen sınıfları kullanmak isteyen .NET Framework geliştiricilere yöneliktir. Hakkında [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]en son bilgiler için bkz [. Windows Otomasyonu API 'si: UI Otomasyonu](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Bu konu, bir [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] öğenin özelliklerinin nasıl alınacağını gösterir.  
  
### <a name="get-a-current-property-value"></a>Geçerli özellik değerini Al  
  
1. <xref:System.Windows.Automation.AutomationElement> Hangi özelliği almak istediğinizi edinin.  
  
2. <xref:System.Windows.Automation.AutomationElement.Current%2A> Özellik yapısını çağırın <xref:System.Windows.Automation.AutomationElement.GetCurrentPropertyValue%2A>ya da alın ve üyelerinden birindeki değeri alın.  
  
### <a name="get-a-cached-property-value"></a>Önbelleğe alınmış Özellik değeri alma  
  
1. <xref:System.Windows.Automation.AutomationElement> Hangi özelliği almak istediğinizi edinin. Özelliği içinde <xref:System.Windows.Automation.CacheRequest>belirtilmiş olmalıdır.  
  
2. <xref:System.Windows.Automation.AutomationElement.Cached%2A> Özellik yapısını çağırın <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A>ya da alın ve üyelerinden birindeki değeri alın.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, öğesinin <xref:System.Windows.Automation.AutomationElement>geçerli özelliklerini almanın çeşitli yollarını gösterir.  
  
 [!code-csharp[UIAClient_snip#170](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#170)]
 [!code-vb[UIAClient_snip#170](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#170)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [İstemciler İçin UI Otomasyonu Özellikleri](ui-automation-properties-for-clients.md)
- [UI Otomasyonunda Önbelleğe Almayı Kullanma](use-caching-in-ui-automation.md)
- [UI Otomasyonu İstemcilerinde Önbelleğe Alma](caching-in-ui-automation-clients.md)
