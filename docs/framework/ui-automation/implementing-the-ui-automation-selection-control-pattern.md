---
title: UI Otomasyon Seçim Denetim Düzenini Uygulama
description: Kullanıcı Arabirimi Otomasyonu 'nda seçim denetim deseninin uygulanması için yönergeleri ve kuralları gözden geçirin. ISelectionProvider arabirimi için gereken üyelere bakın.
ms.date: 03/30/2017
helpviewer_keywords:
- Selection control pattern
- UI Automation, Selection control pattern
- control patterns, Selection
ms.assetid: 449c3068-a5d6-4f66-84c6-1bcc7dd4d209
ms.openlocfilehash: d3854a401ae6179be4e4e75d86964108d83b0ccf
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87163586"
---
# <a name="implementing-the-ui-automation-selection-control-pattern"></a>UI Otomasyon Seçim Denetim Düzenini Uygulama
> [!NOTE]
> Bu belge, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ad alanında tanımlanan yönetilen sınıfları kullanmak isteyen .NET Framework geliştiricilere yöneliktir <xref:System.Windows.Automation> . Hakkında en son bilgiler için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] bkz. [WINDOWS Otomasyonu API: UI Otomasyonu](/windows/win32/winauto/entry-uiauto-win32).  
  
 Bu konu <xref:System.Windows.Automation.Provider.ISelectionProvider> , olaylar ve özellikler hakkında bilgiler de dahil olmak üzere uygulama yönergelerini ve kurallarını tanıtır. Ek başvuruların bağlantıları konunun sonunda listelenmiştir.  
  
 <xref:System.Windows.Automation.SelectionPattern>Denetim stili, seçilebilir alt öğelerin bir koleksiyonu için kapsayıcılar olarak davranan denetimleri desteklemek için kullanılır. Bu öğenin alt öğelerinin uygulanması gerekir <xref:System.Windows.Automation.Provider.ISelectionItemProvider> . Bu denetim modelini uygulayan denetimlerin örnekleri için bkz. [UI Otomasyonu istemcileri Için denetim model eşlemesi](control-pattern-mapping-for-ui-automation-clients.md).  
  
<a name="Implementation_Guidelines_and_Conventions"></a>
## <a name="implementation-guidelines-and-conventions"></a>Uygulama kılavuzları ve kuralları  
 Seçim Denetim modelini uygularken, aşağıdaki kılavuz ve kurallara göz önünde aklınızda olmanız gerekir:  
  
- Uygulayan denetimlerin <xref:System.Windows.Automation.Provider.ISelectionProvider> tek veya birden çok alt öğe seçmesine izin ver. Örneğin, liste kutusu, liste görünümü ve ağaç görünümü birden çok seçimi destekler, Birleşik giriş kutusu, kaydırıcı ve radyo düğmesi grubu tek seçimi destekler.  
  
- **Birim** kaydırıcı denetimi gibi minimum, maksimum ve sürekli aralığa sahip denetimler <xref:System.Windows.Automation.Provider.IRangeValueProvider> yerine uygulanmalıdır <xref:System.Windows.Automation.Provider.ISelectionProvider> .  
  
- <xref:System.Windows.Automation.Provider.IRawElementProviderFragmentRoot> **Görüntüleme özellikleri** Iletişim kutusundaki **ekran çözünürlüğü** kaydırıcısı veya Microsoft Word (aşağıda gösterilmiştir) **renk seçici** seçim denetimi gibi, uygulayan alt denetimleri yöneten tek seçim denetimleri, uygulamanız gerekir <xref:System.Windows.Automation.Provider.ISelectionProvider> ; alt öğeleri hem hem de uygulamalıdır <xref:System.Windows.Automation.Provider.IRawElementProviderFragment> <xref:System.Windows.Automation.Provider.ISelectionItemProvider> .  
  
 ![Sarı vurgulanmış şekilde renk seçici.](./media/uia-valuepattern-colorpicker.png "UIA_ValuePattern_ColorPicker")  
Renk örneği dize eşlemesi örneği  
  
- Menüler desteklemez <xref:System.Windows.Automation.SelectionPattern> . Hem grafik hem de metin içeren menü öğeleriyle çalışıyorsanız (Microsoft Outlook 'ta **Görünüm** menüsündeki **Önizleme bölmesi** öğeleri gibi) ve durumu iletmelisiniz, uygulamanız gerekir <xref:System.Windows.Automation.Provider.IToggleProvider> .  
  
<a name="Required_Members_for_ISelectionProvider"></a>
## <a name="required-members-for-iselectionprovider"></a>ISelectionProvider için gerekli Üyeler  
 Arabirim için aşağıdaki özellikler, Yöntemler ve olaylar gereklidir <xref:System.Windows.Automation.Provider.ISelectionProvider> .  
  
|Gerekli Üyeler|Tür|Notlar|  
|----------------------|----------|-----------|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider.CanSelectMultiple%2A>|Özellik|, Ve kullanan özellik değişmiş olayları <xref:System.Windows.Automation.Automation.AddAutomationPropertyChangedEventHandler%2A> desteklemelidir <xref:System.Windows.Automation.Automation.RemoveAutomationPropertyChangedEventHandler%2A> .|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider.IsSelectionRequired%2A>|Özellik|, Ve kullanan özellik değişmiş olayları <xref:System.Windows.Automation.Automation.AddAutomationPropertyChangedEventHandler%2A> desteklemelidir <xref:System.Windows.Automation.Automation.RemoveAutomationPropertyChangedEventHandler%2A> .|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider.GetSelection%2A>|Yöntem|Hiçbiri|  
|<xref:System.Windows.Automation.SelectionPatternIdentifiers.InvalidatedEvent>|Olay|Kapsayıcıda bir seçim önemli ölçüde değiştirildiğinde ve sabit izin verenden daha fazla ekleme ve kaldırma olayı gönderilmesini gerektirdiğinde tetiklenir <xref:System.Windows.Automation.Provider.AutomationInteropProvider.InvalidateLimit> .|  
  
 <xref:System.Windows.Automation.Provider.ISelectionProvider.IsSelectionRequired%2A>Ve <xref:System.Windows.Automation.Provider.ISelectionProvider.CanSelectMultiple%2A> özellikleri dinamik olabilir. Örneğin, bir denetimin ilk durumu varsayılan olarak seçili herhangi bir öğeye sahip olmayabilir ve bunu gösterir <xref:System.Windows.Automation.Provider.ISelectionProvider.IsSelectionRequired%2A> `false` . Ancak, bir öğe seçildikten sonra Denetim her zaman en az bir öğe seçilmiş olmalıdır. Benzer şekilde, ender durumlarda, bir denetim birden fazla öğenin başlatma sırasında seçilebilsin, ancak bundan sonra yalnızca tek seçimlerin olmasına izin verebilir.  
  
<a name="Exceptions"></a>
## <a name="exceptions"></a>Özel durumlar  
 Sağlayıcılar aşağıdaki özel durumları oluşturması gerekir.  
  
|Özel durum türü|Koşul|  
|--------------------|---------------|  
|<xref:System.Windows.Automation.ElementNotEnabledException>|Denetim etkinleştirilmemişse.|  
|<xref:System.InvalidOperationException>|Denetim gizliyse.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [UI Otomasyon Denetim Düzenlerine Genel Bakış](ui-automation-control-patterns-overview.md)
- [UI Otomasyon Sağlayıcısında Denetim Düzenleri Desteği](support-control-patterns-in-a-ui-automation-provider.md)
- [İstemciler İçin UI Otomasyon Denetim Düzenleri](ui-automation-control-patterns-for-clients.md)
- [UI Otomasyon SelectionItem Denetim Düzeni Uygulama](implementing-the-ui-automation-selectionitem-control-pattern.md)
- [UI Otomasyon Ağacına Genel Bakış](ui-automation-tree-overview.md)
- [UI Otomasyonda Önbelleğe Almayı Kullanma](use-caching-in-ui-automation.md)
