---
title: UI Otomasyon Seçim Denetim Düzenini Uygulama
ms.date: 03/30/2017
helpviewer_keywords:
- Selection control pattern
- UI Automation, Selection control pattern
- control patterns, Selection
ms.assetid: 449c3068-a5d6-4f66-84c6-1bcc7dd4d209
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: fb37c55076f243c48604cbaafdb5fd32c94934f2
ms.sourcegitcommit: ba5c189bf44d44204a3e8838e59ec378a62d82f3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/12/2018
ms.locfileid: "44708380"
---
# <a name="implementing-the-ui-automation-selection-control-pattern"></a>UI Otomasyon Seçim Denetim Düzenini Uygulama
> [!NOTE]
>  Bu belge yönetilen kullanmak isteyen .NET Framework için tasarlanan [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tanımlanan sınıflar <xref:System.Windows.Automation> ad alanı. En son bilgileri [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], bkz: [Windows Automation API: UI Otomasyonu](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Bu konu, yönergeleri ve uygulama kuralları tanıtır <xref:System.Windows.Automation.Provider.ISelectionProvider>, olayları ve özellikleri hakkında bilgi dahil olmak üzere. Ek başvurular bağlantılar konunun sonunda listelenmiştir.  
  
 <xref:System.Windows.Automation.SelectionPattern> Denetim düzeni, seçilebilir alt öğeleri koleksiyonu için kapsayıcı işlevi gören denetimleri desteklemek için kullanılır. Bu öğenin alt öğeleri uygulamalıdır <xref:System.Windows.Automation.Provider.ISelectionItemProvider>. Bu denetim düzeni uygulama denetimleri örnekleri için bkz: [denetim düzeni eşlemesi için UI Otomasyonu istemcileri](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md).  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a>Uygulama yönergeleri ve kuralları  
 Seçim denetim düzeni uygularken aşağıdaki yönergeler ve kuralları dikkat edin:  
  
-   Denetimleri uygulayan <xref:System.Windows.Automation.Provider.ISelectionProvider> tek veya birden çok alt öğeler seçilmesine izin verin. Örneğin, tek bir seçim birleşik giriş kutusu ve kaydırıcı radyo düğmesi grubunda desteklerken liste kutusu, liste görünümü ile ağaç görünümü birden fazla seçimi destekler.  
  
-   Minimum, maksimum ve sürekli bir aralık gibi sahip denetimler **birim** kaydırıcı denetimi, uygulamanız gerekir <xref:System.Windows.Automation.Provider.IRangeValueProvider> yerine <xref:System.Windows.Automation.Provider.ISelectionProvider>.  
  
-   Uygulama alt denetimler yönetme tek seçim denetimleri <xref:System.Windows.Automation.Provider.IRawElementProviderFragmentRoot>, gibi **ekran çözünürlüğü** kaydırıcı **görüntü özellikleri** iletişim kutusu veya **rengi Seçici** Seçim denetiminden [!INCLUDE[TLA#tla_word](../../../includes/tlasharptla-word-md.md)] (aşağıda gösterilen), uygulamalıdır <xref:System.Windows.Automation.Provider.ISelectionProvider>; bunların alt öğeleri hem de uygulamalıdır <xref:System.Windows.Automation.Provider.IRawElementProviderFragment> ve <xref:System.Windows.Automation.Provider.ISelectionItemProvider>.  
  
 ![Renk Seçici vurgulanan sarı ile. ](../../../docs/framework/ui-automation/media/uia-valuepattern-colorpicker.png "UIA_ValuePattern_ColorPicker")  
Renk örneği dize eşleme örneği  
  
-   Menüler desteklemez <xref:System.Windows.Automation.SelectionPattern>. Grafik ve metin içeren menü öğeleri ile çalışıyorsanız (gibi **önizleme bölmesinde** öğeler **görünümü** menüde [!INCLUDE[TLA#tla_outlook](../../../includes/tlasharptla-outlook-md.md)]) ve durumu iletmeniz gerekir, uygulamalıdır<xref:System.Windows.Automation.Provider.IToggleProvider>.  
  
<a name="Required_Members_for_ISelectionProvider"></a>   
## <a name="required-members-for-iselectionprovider"></a>Gerekli üyeleri ISelectionProvider için  
 Aşağıdaki özellikleri, yöntemleri ve olayları için gerekli olan <xref:System.Windows.Automation.Provider.ISelectionProvider> arabirimi.  
  
|Gerekli üyeleri|Tür|Notlar|  
|----------------------|----------|-----------|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider.CanSelectMultiple%2A>|Özellik|Özellik değişti olayları kullanarak desteklemelidir <xref:System.Windows.Automation.Automation.AddAutomationPropertyChangedEventHandler%2A> ve <xref:System.Windows.Automation.Automation.RemoveAutomationPropertyChangedEventHandler%2A>.|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider.IsSelectionRequired%2A>|Özellik|Özellik değişti olayları kullanarak desteklemelidir <xref:System.Windows.Automation.Automation.AddAutomationPropertyChangedEventHandler%2A> ve <xref:System.Windows.Automation.Automation.RemoveAutomationPropertyChangedEventHandler%2A>.|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider.GetSelection%2A>|Yöntem|Yok.|  
|<xref:System.Windows.Automation.SelectionPatternIdentifiers.InvalidatedEvent>|Olay|Bir kapsayıcı seçim önemli ölçüde değişti ve değerinden daha fazla ekleme ve kaldırma olayları gönderme gerektirir harekete geçirilen <xref:System.Windows.Automation.Provider.AutomationInteropProvider.InvalidateLimit> sabiti izin verir.|  
  
 <xref:System.Windows.Automation.Provider.ISelectionProvider.IsSelectionRequired%2A> Ve <xref:System.Windows.Automation.Provider.ISelectionProvider.CanSelectMultiple%2A> özellikleri dinamik olabilir. Örneğin, bir denetimin ilk durumunu belirten, varsayılan olarak hiçbir öğe olmayabilir <xref:System.Windows.Automation.Provider.ISelectionProvider.IsSelectionRequired%2A> olduğu `false`. Bir öğe seçildikten sonra ancak denetimi her zaman en az bir seçili öğe olmalıdır. Benzer şekilde, nadir durumlarda, bir denetim başlatmayı seçilmesi, ancak bundan sonra yalnızca tek seçim yapılmasına izin vermek birden çok öğe izin verebilir.  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a>Özel Durumlar  
 Sağlayıcıları, aşağıdaki özel durumlar gerekir.  
  
|Özel durum türü|Koşul|  
|--------------------|---------------|  
|<xref:System.Windows.Automation.ElementNotEnabledException>|Denetimin etkin değilse.|  
|<xref:System.InvalidOperationException>|Denetimin gizli değilse.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [UI Otomasyonu Denetim Desenlerine Genel Bakış](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)  
 [UI Otomasyonu Sağlayıcıda Denetim Düzenleri Desteği](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)  
 [İstemciler İçin UI Otomasyonu Denetim Düzenleri](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)  
 [UI Otomasyonu SelectionItem Denetim Desenini Uygulama](../../../docs/framework/ui-automation/implementing-the-ui-automation-selectionitem-control-pattern.md)  
 [UI Otomasyon Ağacına Genel Bakış](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)  
 [UI Otomasyonunda Önbelleğe Almayı Kullanma](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)
