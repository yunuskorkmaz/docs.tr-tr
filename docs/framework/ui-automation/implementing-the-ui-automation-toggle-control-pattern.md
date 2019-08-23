---
title: UI Otomasyonu Değiştirme Denetim Düzenini Uygulama
ms.date: 03/30/2017
helpviewer_keywords:
- Toggle control pattern
- control patterns, Toggle
- UI Automation, Toggle control pattern
ms.assetid: 3cfe875f-b0c0-413d-9703-5f14e6a1a30e
ms.openlocfilehash: 2293dc77369ecf019bd1093808135eeefd99c115
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69932059"
---
# <a name="implementing-the-ui-automation-toggle-control-pattern"></a>UI Otomasyonu Değiştirme Denetim Düzenini Uygulama
> [!NOTE]
> Bu belge, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] <xref:System.Windows.Automation> ad alanında tanımlanan yönetilen sınıfları kullanmak isteyen .NET Framework geliştiricilere yöneliktir. Hakkında [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]en son bilgiler için bkz [. Windows Otomasyonu API 'si: UI Otomasyonu](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Bu konu, Yöntemler ve özellikler hakkında bilgiler <xref:System.Windows.Automation.Provider.IToggleProvider>de dahil olmak üzere uygulama yönergelerini ve kurallarını tanıtır. Ek başvuruların bağlantıları konunun sonunda listelenmiştir.  
  
 <xref:System.Windows.Automation.TogglePattern> Denetim stili, bir durum kümesi boyunca geçiş yapan ve bir kez ayarlandıktan sonra bir durumu korumak için kullanılan denetimleri desteklemek için kullanılır. Bu denetim modelini uygulayan denetimlerin örnekleri için bkz. [UI Otomasyonu istemcileri Için denetim model eşlemesi](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md).  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a>Uygulama kılavuzları ve kuralları  
 Iki durumlu denetim modelini uygularken aşağıdaki kılavuz ve kurallara göz önünde  
  
- Etkin olduğunda, düğme, araç çubuğu düğmeleri ve köprüler gibi durumları korumayan denetimler bunun yerine uygulamanız <xref:System.Windows.Automation.Provider.IInvokeProvider> gerekir.  
  
- Bir denetim,, destekleniyorsa, <xref:System.Windows.Automation.ToggleState> aşağıdaki sırayla ilerlemeli: <xref:System.Windows.Automation.ToggleState.On>, <xref:System.Windows.Automation.ToggleState.Off> ve destekleniyorsa <xref:System.Windows.Automation.ToggleState.Indeterminate>.  
  
- <xref:System.Windows.Automation.TogglePattern>, Üçlü durum onay kutusunun doğrudan ayarını çevreleyen sorunlar nedeniyle, uygun <xref:System.Windows.Automation.ToggleState> sırası boyunca geçiş yapılmadan bir setstate (newState) yöntemi sağlamaz.  
  
- RadioButton denetimi geçerli durumları arasında geçiş <xref:System.Windows.Automation.Provider.IToggleProvider>yeteneğine sahip olmadığından uygulamaz.  
  
<a name="Required_Members_for_IToggleProvider"></a>   
## <a name="required-members-for-itoggleprovider"></a>IToggleProvider için gerekli Üyeler  
 Uygulamak <xref:System.Windows.Automation.Provider.IToggleProvider>için aşağıdaki özellikler ve Yöntemler gereklidir.  
  
|Gerekli üye|Üye türü|Notlar|  
|---------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.TogglePattern.Toggle%2A>|Yöntem|Yok.|  
|<xref:System.Windows.Automation.TogglePatternIdentifiers.ToggleStateProperty>|Özellik|Yok.|  
  
 Bu denetim deseninin ilişkili olayları yok.  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a>Özel Durumlar  
 Bu denetim deseninin ilişkili özel durumları yok.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [UI Otomasyonu Denetim Desenlerine Genel Bakış](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)
- [UI Otomasyonu Sağlayıcıda Denetim Düzenleri Desteği](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)
- [İstemciler İçin UI Otomasyonu Denetim Düzenleri](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)
- [UI Otomasyonunu Kullanarak Onay Kutusunun Değiştir Durumunu Alma](../../../docs/framework/ui-automation/get-the-toggle-state-of-a-check-box-using-ui-automation.md)
- [UI Otomasyon Ağacına Genel Bakış](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)
- [UI Otomasyonunda Önbelleğe Almayı Kullanma](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)
