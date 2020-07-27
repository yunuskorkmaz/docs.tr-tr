---
title: UI Otomasyonu Değiştirme Denetim Düzenini Uygulama
description: UI otomasyonunda Iki durumlu denetim deseninin uygulanması için yönergeleri ve kuralları gözden geçirin. IToggleProvider arabirimi için gerekli üyeleri öğrenin.
ms.date: 03/30/2017
helpviewer_keywords:
- Toggle control pattern
- control patterns, Toggle
- UI Automation, Toggle control pattern
ms.assetid: 3cfe875f-b0c0-413d-9703-5f14e6a1a30e
ms.openlocfilehash: f9ae850a560101582b5f1a461de19f260ef59798
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87168038"
---
# <a name="implementing-the-ui-automation-toggle-control-pattern"></a>UI Otomasyonu Değiştirme Denetim Düzenini Uygulama
> [!NOTE]
> Bu belge, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ad alanında tanımlanan yönetilen sınıfları kullanmak isteyen .NET Framework geliştiricilere yöneliktir <xref:System.Windows.Automation> . Hakkında en son bilgiler için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] bkz. [WINDOWS Otomasyonu API: UI Otomasyonu](/windows/win32/winauto/entry-uiauto-win32).  
  
 Bu konu <xref:System.Windows.Automation.Provider.IToggleProvider> , Yöntemler ve özellikler hakkında bilgiler de dahil olmak üzere uygulama yönergelerini ve kurallarını tanıtır. Ek başvuruların bağlantıları konunun sonunda listelenmiştir.  
  
 <xref:System.Windows.Automation.TogglePattern>Denetim stili, bir durum kümesi boyunca geçiş yapan ve bir kez ayarlandıktan sonra bir durumu korumak için kullanılan denetimleri desteklemek için kullanılır. Bu denetim modelini uygulayan denetimlerin örnekleri için bkz. [UI Otomasyonu istemcileri Için denetim model eşlemesi](control-pattern-mapping-for-ui-automation-clients.md).  
  
<a name="Implementation_Guidelines_and_Conventions"></a>
## <a name="implementation-guidelines-and-conventions"></a>Uygulama kılavuzları ve kuralları  
 Iki durumlu denetim modelini uygularken aşağıdaki kılavuz ve kurallara göz önünde  
  
- Etkin olduğunda, düğme, araç çubuğu düğmeleri ve köprüler gibi durumları korumayan denetimler <xref:System.Windows.Automation.Provider.IInvokeProvider> bunun yerine uygulamanız gerekir.  
  
- Bir denetim,, destekleniyorsa, <xref:System.Windows.Automation.ToggleState> aşağıdaki sırayla ilerlemeli: <xref:System.Windows.Automation.ToggleState.On> , <xref:System.Windows.Automation.ToggleState.Off> ve destekleniyorsa <xref:System.Windows.Automation.ToggleState.Indeterminate> .  
  
- <xref:System.Windows.Automation.TogglePattern>, Üçlü durum onay kutusunun doğrudan ayarını çevreleyen sorunlar nedeniyle, uygun sırası boyunca geçiş yapılmadan bir SetState (newState) yöntemi sağlamaz <xref:System.Windows.Automation.ToggleState> .  
  
- RadioButton denetimi <xref:System.Windows.Automation.Provider.IToggleProvider> geçerli durumları arasında geçiş yeteneğine sahip olmadığından uygulamaz.  
  
<a name="Required_Members_for_IToggleProvider"></a>
## <a name="required-members-for-itoggleprovider"></a>IToggleProvider için gerekli Üyeler  
 Uygulamak için aşağıdaki özellikler ve Yöntemler gereklidir <xref:System.Windows.Automation.Provider.IToggleProvider> .  
  
|Gerekli üye|Üye türü|Notlar|  
|---------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.TogglePattern.Toggle%2A>|Yöntem|Hiçbiri|  
|<xref:System.Windows.Automation.TogglePatternIdentifiers.ToggleStateProperty>|Özellik|Hiçbiri|  
  
 Bu denetim deseninin ilişkili olayları yok.  
  
<a name="Exceptions"></a>
## <a name="exceptions"></a>Özel durumlar  
 Bu denetim deseninin ilişkili özel durumları yok.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [UI Otomasyon Denetim Düzenlerine Genel Bakış](ui-automation-control-patterns-overview.md)
- [UI Otomasyon Sağlayıcısında Denetim Düzenleri Desteği](support-control-patterns-in-a-ui-automation-provider.md)
- [İstemciler İçin UI Otomasyon Denetim Düzenleri](ui-automation-control-patterns-for-clients.md)
- [UI Otomasyonunu Kullanarak Onay Kutusunun Değiştir Durumunu Alma](get-the-toggle-state-of-a-check-box-using-ui-automation.md)
- [UI Otomasyon Ağacına Genel Bakış](ui-automation-tree-overview.md)
- [UI Otomasyonda Önbelleğe Almayı Kullanma](use-caching-in-ui-automation.md)
