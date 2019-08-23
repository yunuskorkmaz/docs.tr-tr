---
title: UI Otomasyon MultipleView Denetim Düzeni Uygulama
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, MultipleView control pattern
- MultipleView control pattern
- control patterns, MultipleView
ms.assetid: 5bf1b248-ffee-48c8-9613-0b134bbe9f6a
ms.openlocfilehash: 6a77b81cab34b1824b23b1e3e050ecf034ab7700
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69932165"
---
# <a name="implementing-the-ui-automation-multipleview-control-pattern"></a>UI Otomasyon MultipleView Denetim Düzeni Uygulama
> [!NOTE]
> Bu belge, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] <xref:System.Windows.Automation> ad alanında tanımlanan yönetilen sınıfları kullanmak isteyen .NET Framework geliştiricilere yöneliktir. Hakkında [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]en son bilgiler için bkz [. Windows Otomasyonu API 'si: UI Otomasyonu](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Bu konu, olaylar ve özellikler hakkında bilgiler <xref:System.Windows.Automation.Provider.IMultipleViewProvider>de dahil olmak üzere uygulama yönergelerini ve kurallarını tanıtır. Ek başvuruların bağlantıları konunun sonunda listelenmiştir.  
  
 <xref:System.Windows.Automation.MultipleViewPattern> Denetim stili, aynı bilgi kümesinin veya alt denetimlerin birden çok temsilini sağlayan ve arasında geçiş yapabilecek denetimleri desteklemek için kullanılır.  
  
 Birden çok görünüm sunan denetimlerin örnekleri, liste görünümünü (içeriğini küçük resimler, Kutucuklar, simgeler veya ayrıntılar olarak gösterebilir), [!INCLUDE[TLA#tla_xl](../../../includes/tlasharptla-xl-md.md)] grafikler (pasta, çizgi, çubuk, formül içeren hücre değeri), [!INCLUDE[TLA#tla_word](../../../includes/tlasharptla-word-md.md)] belgeler (normal, Web düzeni, Yazdırma düzeni, okuma düzeni, ana hat), Microsoft Outlook Takvim (yıl, ay, hafta, gün) ve [!INCLUDE[TLA#tla_wmp](../../../includes/tlasharptla-wmp-md.md)] kaplamalar. Desteklenen görünümler denetim geliştiricisi tarafından belirlenir ve her denetime özeldir.  
  
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
|<xref:System.Windows.Automation.Provider.IMultipleViewProvider.CurrentView%2A>|Özellik|Yok.|  
|<xref:System.Windows.Automation.Provider.IMultipleViewProvider.GetSupportedViews%2A>|Yöntem|Yok.|  
|<xref:System.Windows.Automation.Provider.IMultipleViewProvider.GetViewName%2A>|Yöntem|Yok.|  
|<xref:System.Windows.Automation.Provider.IMultipleViewProvider.SetCurrentView%2A>|Yöntem|Yok.|  
  
 Bu denetim düzeniyle ilişkili hiçbir olay yok.  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a>Özel Durumlar  
 Sağlayıcı aşağıdaki özel durumları oluşturması gerekir.  
  
|Özel durum türü|Koşul|  
|--------------------|---------------|  
|<xref:System.ArgumentException>|Ya da <xref:System.Windows.Automation.Provider.IMultipleViewProvider.SetCurrentView%2A> <xref:System.Windows.Automation.Provider.IMultipleViewProvider.GetViewName%2A> desteklenen görünümler koleksiyonunun üyesi olmayan bir parametre ile çağrıldığında.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [UI Otomasyonu Denetim Desenlerine Genel Bakış](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)
- [UI Otomasyonu Sağlayıcıda Denetim Düzenleri Desteği](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)
- [İstemciler İçin UI Otomasyonu Denetim Düzenleri](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)
- [UI Otomasyon Ağacına Genel Bakış](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)
- [UI Otomasyonunda Önbelleğe Almayı Kullanma](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)
