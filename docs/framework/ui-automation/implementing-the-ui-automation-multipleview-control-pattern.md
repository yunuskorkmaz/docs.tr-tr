---
title: UI Otomasyon MultipleView Denetim Düzeni Uygulama
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, MultipleView control pattern
- MultipleView control pattern
- control patterns, MultipleView
ms.assetid: 5bf1b248-ffee-48c8-9613-0b134bbe9f6a
ms.openlocfilehash: 9decb617e30a340d3e73e911f7848110de5599e9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79180165"
---
# <a name="implementing-the-ui-automation-multipleview-control-pattern"></a>UI Otomasyon MultipleView Denetim Düzeni Uygulama
> [!NOTE]
> Bu dokümantasyon, ad alanında tanımlanan yönetilen [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] sınıfları kullanmak <xref:System.Windows.Automation> isteyen .NET Framework geliştiricileri için tasarlanmıştır. Hakkında en son [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]bilgi için [Bkz. Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).  
  
 Bu <xref:System.Windows.Automation.Provider.IMultipleViewProvider>konu, olaylar ve özellikler hakkında bilgiler de dahil olmak üzere, uygulama yönergeleri ve kuralları sunar. Ek başvurulara bağlantılar konunun sonunda listelenir.  
  
 Denetim <xref:System.Windows.Automation.MultipleViewPattern> deseni, aynı bilgi kümesinin veya alt denetimlerin birden çok temsilini sağlayan ve aralarında geçiş yapan denetimleri desteklemek için kullanılır.  
  
 Birden çok görünüm sunabilecek denetimlere örnek olarak liste görünümü (içeriğini küçük resimler, döşemeler, simgeler veya ayrıntılar olarak gösterebilen), Microsoft Excel grafikleri (pasta, satır, çubuk, formüllü hücre değeri), Microsoft Word belgeleri (normal, Web düzeni, yazdırma düzen, okuma düzeni, anahat), Microsoft Outlook takvimi (yıl, ay, hafta, gün) ve Microsoft Windows Media Player görünümleri. Desteklenen görünümler denetim geliştiricisi tarafından belirlenir ve her denetime özgür.  
  
<a name="Implementation_Guidelines_and_Conventions"></a>
## <a name="implementation-guidelines-and-conventions"></a>Uygulama Yönergeleri ve Sözleşmeleri  
 Çoklu Görünüm denetim deseni uygularken aşağıdaki yönergeleri ve kuralları not edin:  
  
- <xref:System.Windows.Automation.Provider.IMultipleViewProvider>geçerli görünümü sağlayan bir denetimden farklıysa, geçerli görünümü yöneten bir kapsayıcı üzerinde de uygulanmalıdır. Örneğin, Windows Gezgini geçerli klasör içeriği için bir Liste denetimi içerirken, denetim görünümü Windows Gezgini uygulamasından yönetilir.  
  
- İçeriğini sıralayabilen bir denetim, birden çok görünümü desteklemek için kabul edilmez.  
  
- Görünümler topluluğu örnekler arasında aynı olmalıdır.  
  
- Görünüm adları Metinden Konuşmaya, Braille'de ve diğer insan tarafından okunabilir uygulamalarda kullanıma uygun olmalıdır.  
  
<a name="Required_Members_for_IMultipleViewProvider"></a>
## <a name="required-members-for-imultipleviewprovider"></a>IMultipleViewProvider için Gerekli Üyeler  
 IMultipleViewProvider'ı uygulamak için aşağıdaki özellikler ve yöntemler gereklidir.  
  
|Gerekli üyeler|Üye tipi|Notlar|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.IMultipleViewProvider.CurrentView%2A>|Özellik|None|  
|<xref:System.Windows.Automation.Provider.IMultipleViewProvider.GetSupportedViews%2A>|Yöntem|None|  
|<xref:System.Windows.Automation.Provider.IMultipleViewProvider.GetViewName%2A>|Yöntem|None|  
|<xref:System.Windows.Automation.Provider.IMultipleViewProvider.SetCurrentView%2A>|Yöntem|None|  
  
 Bu denetim deseniyle ilişkili olaylar yok.  
  
<a name="Exceptions"></a>
## <a name="exceptions"></a>Özel durumlar  
 Sağlayıcı aşağıdaki özel durumları atmalıdır.  
  
|Özel durum türü|Koşul|  
|--------------------|---------------|  
|<xref:System.ArgumentException>|Desteklenen <xref:System.Windows.Automation.Provider.IMultipleViewProvider.SetCurrentView%2A> görünümler koleksiyonunun üyesi olmayan bir parametre yle çağrıldığınızda. <xref:System.Windows.Automation.Provider.IMultipleViewProvider.GetViewName%2A>|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [UI Otomasyonu Denetim Desenlerine Genel Bakış](ui-automation-control-patterns-overview.md)
- [UI Otomasyonu Sağlayıcıda Denetim Düzenleri Desteği](support-control-patterns-in-a-ui-automation-provider.md)
- [İstemciler İçin UI Otomasyonu Denetim Düzenleri](ui-automation-control-patterns-for-clients.md)
- [UI Otomasyon Ağacına Genel Bakış](ui-automation-tree-overview.md)
- [UI Otomasyonunda Önbelleğe Almayı Kullanma](use-caching-in-ui-automation.md)
