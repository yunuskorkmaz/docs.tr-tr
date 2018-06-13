---
title: İstemciler İçin UI Otomasyon Olayları
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, events for clients
- events, UI Automation clients
ms.assetid: b909e388-3f24-4997-b6d4-bd9c35c2dc27
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: d471ee08f60d6fdd029b2057d629ad824ae9fdcf
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33408040"
---
# <a name="ui-automation-events-for-clients"></a>İstemciler İçin UI Otomasyon Olayları
> [!NOTE]
>  Bu belge yönetilen kullanmak isteyen .NET Framework için tasarlanan [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tanımlanan sınıflar <xref:System.Windows.Automation> ad alanı. Hakkında en yeni bilgiler için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], bkz: [Windows Otomasyon API: UI Otomasyonu](http://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Bu konuda açıklanmaktadır nasıl [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] olayları UI Otomasyon istemcileri tarafından kullanılır.  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] istemcilerin ilgi olaylarına abone olma olanak sağlar. Bu özellik, sürekli olarak tüm yoklamak için gereksinimini ortadan kaldırarak performansı artırır [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] tüm bilgileri, yapı veya durumu değişip değişmediğini görmek için sistemdeki öğeleri.  
  
 Verimliliği de yalnızca tanımlı bir kapsamdaki olayları dinler özelliği tarafından geliştirilmiştir. Örneğin, tüm odak değişikliği olaylarını istemci dinlediği [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] öğeleri ağacında ya da tek bir öğe ve alt öğeleri.  
  
> [!NOTE]
>  Tüm olası olaylar tarafından oluşturulur varsayın olmayan bir [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] sağlayıcısı. Örneğin, tüm özellik değişikliği olayları için standart proxy sağlayıcıları tarafından gerçekleştirilen neden [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)] ve [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] kontrol eder.  
  
 Daha geniş bir görünümü için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] olayları görmek [UI Otomasyonu olaylarına genel bakış](../../../docs/framework/ui-automation/ui-automation-events-overview.md).  
  
<a name="Subscribing_to_Events"></a>   
## <a name="subscribing-to-events"></a>Olaylara abone olma  
 İstemci uygulamaları, aşağıdaki yöntemlerden birini kullanarak bir olay işleyicisi kaydederek belirli bir türde olaylarına abone olma.  
  
|Yöntem|Olay türü|Olay bağımsız değişken türü|Temsilci türü|  
|------------|----------------|--------------------------|-------------------|  
|<xref:System.Windows.Automation.Automation.AddAutomationFocusChangedEventHandler%2A>|Odağı Değiştir|<xref:System.Windows.Automation.AutomationFocusChangedEventArgs>|<xref:System.Windows.Automation.AutomationFocusChangedEventHandler>|  
|<xref:System.Windows.Automation.Automation.AddAutomationPropertyChangedEventHandler%2A>|Özellik değişikliği|<xref:System.Windows.Automation.AutomationPropertyChangedEventArgs>|<xref:System.Windows.Automation.AutomationPropertyChangedEventHandler>|  
|<xref:System.Windows.Automation.Automation.AddStructureChangedEventHandler%2A>|Yapı değişikliğine|<xref:System.Windows.Automation.StructureChangedEventArgs>|<xref:System.Windows.Automation.StructureChangedEventHandler>|  
|<xref:System.Windows.Automation.Automation.AddAutomationEventHandler%2A>|Tarafından tanımlanan tüm diğer olaylar, bir <xref:System.Windows.Automation.AutomationEvent>|<xref:System.Windows.Automation.AutomationEventArgs> Veya <xref:System.Windows.Automation.WindowClosedEventArgs>|<xref:System.Windows.Automation.AutomationEventHandler>|  
  
 Bir yöntemini çağırmadan önce olayını işlemek için temsilci yöntemi oluşturmanız gerekir. İsterseniz, farklı türde tek bir yöntem olayları işlemek ve bu yöntem tablosundaki yöntemlerini birine birden fazla çağrı geçirin. Örneğin, bir tek <xref:System.Windows.Automation.AutomationEventHandler> farklı aşağıdakilere göre çeşitli olayları işlemek için ayarlanabilir <xref:System.Windows.Automation.AutomationEventArgs.EventId%2A>.  
  
> [!NOTE]
>  Pencere kapatıldığında olayları işlemek için olay işleyici olarak geçirilen bağımsız değişken türü cast <xref:System.Windows.Automation.WindowClosedEventArgs>. Çünkü [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] pencere öğesi artık geçerli değil, kullanamazsınız `sender` bilgiler; almak için parametre kullanmak <xref:System.Windows.Automation.WindowClosedEventArgs.GetRuntimeId%2A> yerine.  
  
> [!CAUTION]
>  Uygulamanızı olayları kendi alabilirse [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)], uygulamanızın kullanmayın [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] iş parçacığı olaylarına abone olma ya da bunlara ilişkin aboneliği. Bunun yapılması için beklenmeyen davranışlara neden olabilir. Daha fazla bilgi için bkz: [UI Otomasyon iş parçacığı oluşturma sorunları](../../../docs/framework/ui-automation/ui-automation-threading-issues.md).  
  
 Kapatma sırasında veya ne zaman [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] olayları artık uygulamaya ilgi, UI Otomasyon istemcileri aşağıdaki yöntemlerden birini çağrı.  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|<xref:System.Windows.Automation.Automation.RemoveAutomationEventHandler%2A>|Kullanarak kayıtlı bir olay işleyicisi kaydını siler <xref:System.Windows.Automation.Automation.AddAutomationEventHandler%2A>.|  
|<xref:System.Windows.Automation.Automation.RemoveAutomationFocusChangedEventHandler%2A>|Kullanarak kayıtlı bir olay işleyicisi kaydını siler <xref:System.Windows.Automation.Automation.AddAutomationFocusChangedEventHandler%2A>.|  
|<xref:System.Windows.Automation.Automation.RemoveAutomationPropertyChangedEventHandler%2A>|Kullanarak kayıtlı bir olay işleyicisi kaydını siler <xref:System.Windows.Automation.Automation.AddAutomationPropertyChangedEventHandler%2A>.|  
|<xref:System.Windows.Automation.Automation.RemoveAllEventHandlers%2A>|Tüm kayıtlı olay işleyicileri kaydını siler.|  
  
 Örnek kod, bkz: [UI Otomasyon olaylarına abone](../../../docs/framework/ui-automation/subscribe-to-ui-automation-events.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [UI Otomasyonu Olaylarına Abone Olma](../../../docs/framework/ui-automation/subscribe-to-ui-automation-events.md)  
 [UI Otomasyonu Olaylarına Genel Bakış](../../../docs/framework/ui-automation/ui-automation-events-overview.md)  
 [UI Otomasyonu Özelliklerine Genel Bakış](../../../docs/framework/ui-automation/ui-automation-properties-overview.md)  
 [TrackFocus örnek](http://msdn.microsoft.com/library/4a91c0af-6bb5-4d38-a743-cf136f268fc9)
