---
title: UI Otomasyon MultipleView Denetim Düzeni Uygulama
description: Kullanıcı Arabirimi Otomasyonu 'nda MultipleView denetim modelini uygulamak için yönergeleri ve kuralları gözden geçirin. IMultipleViewProvider arabirimi için gereken üyelere bakın.
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, MultipleView control pattern
- MultipleView control pattern
- control patterns, MultipleView
ms.assetid: 5bf1b248-ffee-48c8-9613-0b134bbe9f6a
ms.openlocfilehash: 0d65d57637891fcb1307f5ee83a417941ff323fb
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87168225"
---
# <a name="implementing-the-ui-automation-multipleview-control-pattern"></a>UI Otomasyon MultipleView Denetim Düzeni Uygulama
> [!NOTE]
> Bu belge, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ad alanında tanımlanan yönetilen sınıfları kullanmak isteyen .NET Framework geliştiricilere yöneliktir <xref:System.Windows.Automation> . Hakkında en son bilgiler için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] bkz. [WINDOWS Otomasyonu API: UI Otomasyonu](/windows/win32/winauto/entry-uiauto-win32).  
  
 Bu konu <xref:System.Windows.Automation.Provider.IMultipleViewProvider> , olaylar ve özellikler hakkında bilgiler de dahil olmak üzere uygulama yönergelerini ve kurallarını tanıtır. Ek başvuruların bağlantıları konunun sonunda listelenmiştir.  
  
 <xref:System.Windows.Automation.MultipleViewPattern>Denetim stili, aynı bilgi kümesinin veya alt denetimlerin birden çok temsilini sağlayan ve arasında geçiş yapabilecek denetimleri desteklemek için kullanılır.  
  
 Birden çok görünüm sunan denetimlerin örnekleri, liste görünümünü içerir (Bu, içeriğini küçük resim olarak gösterebilir) Kutucuklar, simgeler veya Ayrıntılar), Microsoft Excel grafikleri (pasta, çizgi, çubuk, formül içeren hücre değeri), Microsoft Word belgeleri (normal, Web düzeni, yazdırma düzeni, okuma düzeni, ana hat), Microsoft Outlook Takvim (year, month, Week, Day) ve Microsoft Windows Media Player kaplamaları. Desteklenen görünümler denetim geliştiricisi tarafından belirlenir ve her denetime özeldir.  
  
<a name="Implementation_Guidelines_and_Conventions"></a>
## <a name="implementation-guidelines-and-conventions"></a>Uygulama kılavuzları ve kuralları  
 Birden çok görünüm denetim modelini uygularken aşağıdaki kılavuz ve kurallara göz önünde yer verilmiştir:  
  
- <xref:System.Windows.Automation.Provider.IMultipleViewProvider>geçerli görünümü sağlayan bir denetimden farklıysa geçerli görünümü yöneten bir kapsayıcıya de uygulanmalıdır. Örneğin, Windows Gezgini, denetimin görünümü Windows Gezgini uygulamasından yönetilirken, geçerli klasör içeriği için bir liste denetimi içerir.  
  
- İçeriğini sıralayacak bir denetim, birden fazla görünümü destekleyecek şekilde değerlendirilmez.  
  
- Görünümler koleksiyonu örneklerin tamamında aynı olmalıdır.  
  
- Görünüm adları Metin Okuma, Braille ve diğer insan tarafından okunabilen uygulamalarda kullanım için uygun olmalıdır.  
  
<a name="Required_Members_for_IMultipleViewProvider"></a>
## <a name="required-members-for-imultipleviewprovider"></a>IMultipleViewProvider için gerekli Üyeler  
 IMultipleViewProvider uygulamak için aşağıdaki özellikler ve Yöntemler gereklidir.  
  
|Gerekli Üyeler|Üye türü|Notlar|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.IMultipleViewProvider.CurrentView%2A>|Özellik|Hiçbiri|  
|<xref:System.Windows.Automation.Provider.IMultipleViewProvider.GetSupportedViews%2A>|Yöntem|Hiçbiri|  
|<xref:System.Windows.Automation.Provider.IMultipleViewProvider.GetViewName%2A>|Yöntem|Hiçbiri|  
|<xref:System.Windows.Automation.Provider.IMultipleViewProvider.SetCurrentView%2A>|Yöntem|Hiçbiri|  
  
 Bu denetim düzeniyle ilişkili hiçbir olay yok.  
  
<a name="Exceptions"></a>
## <a name="exceptions"></a>Özel durumlar  
 Sağlayıcı aşağıdaki özel durumları oluşturması gerekir.  
  
|Özel durum türü|Koşul|  
|--------------------|---------------|  
|<xref:System.ArgumentException>|Ya da <xref:System.Windows.Automation.Provider.IMultipleViewProvider.SetCurrentView%2A> <xref:System.Windows.Automation.Provider.IMultipleViewProvider.GetViewName%2A> Desteklenen görünümler koleksiyonunun üyesi olmayan bir parametre ile çağrıldığında.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [UI Otomasyon Denetim Düzenlerine Genel Bakış](ui-automation-control-patterns-overview.md)
- [UI Otomasyon Sağlayıcısında Denetim Düzenleri Desteği](support-control-patterns-in-a-ui-automation-provider.md)
- [İstemciler İçin UI Otomasyon Denetim Düzenleri](ui-automation-control-patterns-for-clients.md)
- [UI Otomasyon Ağacına Genel Bakış](ui-automation-tree-overview.md)
- [UI Otomasyonda Önbelleğe Almayı Kullanma](use-caching-in-ui-automation.md)
