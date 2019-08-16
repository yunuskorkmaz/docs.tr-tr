---
title: UI Otomasyon Seçim Denetim Düzenini Uygulama
ms.date: 03/30/2017
helpviewer_keywords:
- Selection control pattern
- UI Automation, Selection control pattern
- control patterns, Selection
ms.assetid: 449c3068-a5d6-4f66-84c6-1bcc7dd4d209
ms.openlocfilehash: 2297ea0a181fe0fd16aa32b85909acdad5f129ab
ms.sourcegitcommit: 43761fcee10aeefcf851ea81cea3f3c691420856
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/16/2019
ms.locfileid: "69545194"
---
# <a name="implementing-the-ui-automation-selection-control-pattern"></a>UI Otomasyon Seçim Denetim Düzenini Uygulama
> [!NOTE]
>  Bu belge, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] <xref:System.Windows.Automation> ad alanında tanımlanan yönetilen sınıfları kullanmak isteyen .NET Framework geliştiricilere yöneliktir. Hakkında [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]en son bilgiler için bkz [. Windows Otomasyonu API 'si: UI Otomasyonu](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Bu konu, olaylar ve özellikler hakkında bilgiler <xref:System.Windows.Automation.Provider.ISelectionProvider>de dahil olmak üzere uygulama yönergelerini ve kurallarını tanıtır. Ek başvuruların bağlantıları konunun sonunda listelenmiştir.  
  
 <xref:System.Windows.Automation.SelectionPattern> Denetim stili, seçilebilir alt öğelerin bir koleksiyonu için kapsayıcılar olarak davranan denetimleri desteklemek için kullanılır. Bu öğenin alt öğelerinin uygulanması <xref:System.Windows.Automation.Provider.ISelectionItemProvider>gerekir. Bu denetim modelini uygulayan denetimlerin örnekleri için bkz. [UI Otomasyonu istemcileri Için denetim model eşlemesi](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md).  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a>Uygulama kılavuzları ve kuralları  
 Seçim Denetim modelini uygularken, aşağıdaki kılavuz ve kurallara göz önünde aklınızda olmanız gerekir:  
  
- Uygulayan <xref:System.Windows.Automation.Provider.ISelectionProvider> denetimlerin tek veya birden çok alt öğe seçmesine izin ver. Örneğin, liste kutusu, liste görünümü ve ağaç görünümü birden çok seçimi destekler, Birleşik giriş kutusu, kaydırıcı ve radyo düğmesi grubu tek seçimi destekler.  
  
- **Birim** kaydırıcı denetimi gibi minimum, maksimum ve sürekli aralığa sahip denetimler <xref:System.Windows.Automation.Provider.IRangeValueProvider> yerine <xref:System.Windows.Automation.Provider.ISelectionProvider>uygulanmalıdır.  
  
- **Görüntü özellikleri** iletişim kutusundaki **ekran çözünürlüğü** kaydırıcısı veya ' den <xref:System.Windows.Automation.Provider.IRawElementProviderFragmentRoot> [!INCLUDE[TLA#tla_word](../../../includes/tlasharptla-word-md.md)] **renk seçici** seçim denetimi gibi, uygulayan alt denetimleri yöneten tek seçim denetimleri ( aşağıda gösterildiği gibi), uygulaması <xref:System.Windows.Automation.Provider.ISelectionProvider>gerekir; alt öğeleri <xref:System.Windows.Automation.Provider.ISelectionItemProvider>hem hem <xref:System.Windows.Automation.Provider.IRawElementProviderFragment> de uygulamalıdır.  
  
 ![Sarı vurgulanmış şekilde renk seçici.](../../../docs/framework/ui-automation/media/uia-valuepattern-colorpicker.png "UIA_ValuePattern_ColorPicker")  
Renk örneği dize eşlemesi örneği  
  
- Menüler desteklemez <xref:System.Windows.Automation.SelectionPattern>. Hem grafik hem de metin içeren menü öğeleriyle çalışıyorsanız (Microsoft Outlook 'ta **Görünüm** menüsündeki <xref:System.Windows.Automation.Provider.IToggleProvider> **Önizleme bölmesi** öğeleri gibi) ve durumu iletmelisiniz, uygulamanız gerekir.  
  
<a name="Required_Members_for_ISelectionProvider"></a>   
## <a name="required-members-for-iselectionprovider"></a>ISelectionProvider için gerekli Üyeler  
 <xref:System.Windows.Automation.Provider.ISelectionProvider> Arabirim için aşağıdaki özellikler, Yöntemler ve olaylar gereklidir.  
  
|Gerekli Üyeler|Tür|Notlar|  
|----------------------|----------|-----------|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider.CanSelectMultiple%2A>|Özellik|, Ve <xref:System.Windows.Automation.Automation.AddAutomationPropertyChangedEventHandler%2A> <xref:System.Windows.Automation.Automation.RemoveAutomationPropertyChangedEventHandler%2A>kullanan özellik değişmiş olayları desteklemelidir.|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider.IsSelectionRequired%2A>|Özellik|, Ve <xref:System.Windows.Automation.Automation.AddAutomationPropertyChangedEventHandler%2A> <xref:System.Windows.Automation.Automation.RemoveAutomationPropertyChangedEventHandler%2A>kullanan özellik değişmiş olayları desteklemelidir.|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider.GetSelection%2A>|Yöntem|Yok.|  
|<xref:System.Windows.Automation.SelectionPatternIdentifiers.InvalidatedEvent>|Olay|Kapsayıcıda bir seçim önemli ölçüde değiştirildiğinde ve <xref:System.Windows.Automation.Provider.AutomationInteropProvider.InvalidateLimit> sabit izin verenden daha fazla ekleme ve kaldırma olayı gönderilmesini gerektirdiğinde tetiklenir.|  
  
 <xref:System.Windows.Automation.Provider.ISelectionProvider.IsSelectionRequired%2A> Ve<xref:System.Windows.Automation.Provider.ISelectionProvider.CanSelectMultiple%2A> özellikleri dinamik olabilir. Örneğin, bir denetimin ilk durumu varsayılan olarak seçili herhangi bir öğeye sahip olmayabilir ve bunu gösterir <xref:System.Windows.Automation.Provider.ISelectionProvider.IsSelectionRequired%2A>. `false` Ancak, bir öğe seçildikten sonra Denetim her zaman en az bir öğe seçilmiş olmalıdır. Benzer şekilde, ender durumlarda, bir denetim birden fazla öğenin başlatma sırasında seçilebilsin, ancak bundan sonra yalnızca tek seçimlerin olmasına izin verebilir.  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a>Özel Durumlar  
 Sağlayıcılar aşağıdaki özel durumları oluşturması gerekir.  
  
|Özel Durum Türü|Koşul|  
|--------------------|---------------|  
|<xref:System.Windows.Automation.ElementNotEnabledException>|Denetim etkinleştirilmemişse.|  
|<xref:System.InvalidOperationException>|Denetim gizliyse.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [UI Otomasyonu Denetim Desenlerine Genel Bakış](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)
- [UI Otomasyonu Sağlayıcıda Denetim Düzenleri Desteği](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)
- [İstemciler İçin UI Otomasyonu Denetim Düzenleri](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)
- [UI Otomasyonu SelectionItem Denetim Desenini Uygulama](../../../docs/framework/ui-automation/implementing-the-ui-automation-selectionitem-control-pattern.md)
- [UI Otomasyon Ağacına Genel Bakış](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)
- [UI Otomasyonunda Önbelleğe Almayı Kullanma](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)
