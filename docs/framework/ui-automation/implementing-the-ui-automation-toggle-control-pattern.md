---
title: UI Otomasyonu Değiştirme Denetim Düzenini Uygulama
ms.date: 03/30/2017
helpviewer_keywords:
- Toggle control pattern
- control patterns, Toggle
- UI Automation, Toggle control pattern
ms.assetid: 3cfe875f-b0c0-413d-9703-5f14e6a1a30e
ms.openlocfilehash: 5f64842d31d46af3d648b9b570d1cfb210e2910a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79180058"
---
# <a name="implementing-the-ui-automation-toggle-control-pattern"></a>UI Otomasyonu Değiştirme Denetim Düzenini Uygulama
> [!NOTE]
> Bu dokümantasyon, ad alanında tanımlanan yönetilen [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] sınıfları kullanmak <xref:System.Windows.Automation> isteyen .NET Framework geliştiricileri için tasarlanmıştır. Hakkında en son [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]bilgi için [Bkz. Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).  
  
 Bu <xref:System.Windows.Automation.Provider.IToggleProvider>konu, yöntemler ve özellikler hakkında bilgi de dahil olmak üzere, uygulama yönergeleri ve kuralları tanıtır. Ek başvurulara bağlantılar konunun sonunda listelenir.  
  
 Denetim <xref:System.Windows.Automation.TogglePattern> deseni, bir dizi durum arasında geçiş yapabilecek ve bir kez ayarlanan durumu koruyabilen denetimleri desteklemek için kullanılır. Bu denetim deseni uygulayan denetim örnekleri için, [UI Otomasyon Istemcileri için Denetim Deseni Eşleciliği'ne](control-pattern-mapping-for-ui-automation-clients.md)bakın.  
  
<a name="Implementation_Guidelines_and_Conventions"></a>
## <a name="implementation-guidelines-and-conventions"></a>Uygulama Yönergeleri ve Sözleşmeleri  
 Geçiş denetimi deseni uygularken aşağıdaki yönergeleri ve kuralları not edin:  
  
- Düğmeler, araç çubuğu düğmeleri ve köprüler gibi etkinleştirildiğinde durum tutmayan <xref:System.Windows.Automation.Provider.IInvokeProvider> denetimler bunun yerine uygulanmalıdır.  
  
- Bir <xref:System.Windows.Automation.ToggleState> denetim, aşağıdaki sırayla üzerinden <xref:System.Windows.Automation.ToggleState.On> <xref:System.Windows.Automation.ToggleState.Off> döngü gerekir: , <xref:System.Windows.Automation.ToggleState.Indeterminate>ve, eğer desteklenirse, .  
  
- <xref:System.Windows.Automation.TogglePattern>uygun <xref:System.Windows.Automation.ToggleState> sırası ile bisiklet olmadan üç devletli CheckBox doğrudan ayarı çevreleyen sorunlar nedeniyle bir SetState (newState) yöntemi sağlamaz.  
  
- RadioButton denetimi, geçerli <xref:System.Windows.Automation.Provider.IToggleProvider>durumları arasında bisiklete binme yeteneğine sahip olmadığı için uygulamaz.  
  
<a name="Required_Members_for_IToggleProvider"></a>
## <a name="required-members-for-itoggleprovider"></a>IToggleProvider için Gerekli Üyeler  
 Uygulamak için aşağıdaki özellikler ve <xref:System.Windows.Automation.Provider.IToggleProvider>yöntemler gereklidir.  
  
|Gerekli üye|Üye tipi|Notlar|  
|---------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.TogglePattern.Toggle%2A>|Yöntem|None|  
|<xref:System.Windows.Automation.TogglePatternIdentifiers.ToggleStateProperty>|Özellik|None|  
  
 Bu denetim deseni ilişkili olaylar vardır.  
  
<a name="Exceptions"></a>
## <a name="exceptions"></a>Özel durumlar  
 Bu denetim deseni ilişkili özel durumlar vardır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [UI Otomasyonu Denetim Desenlerine Genel Bakış](ui-automation-control-patterns-overview.md)
- [UI Otomasyonu Sağlayıcıda Denetim Düzenleri Desteği](support-control-patterns-in-a-ui-automation-provider.md)
- [İstemciler İçin UI Otomasyonu Denetim Düzenleri](ui-automation-control-patterns-for-clients.md)
- [UI Otomasyonunu Kullanarak Onay Kutusunun Değiştir Durumunu Alma](get-the-toggle-state-of-a-check-box-using-ui-automation.md)
- [UI Otomasyon Ağacına Genel Bakış](ui-automation-tree-overview.md)
- [UI Otomasyonunda Önbelleğe Almayı Kullanma](use-caching-in-ui-automation.md)
