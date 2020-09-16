---
title: UI Otomasyon SelectionItem Denetim Düzeni Uygulama
description: Kullanıcı Arabirimi Otomasyonu 'nda SelectionItem denetim modelini uygulamak için yönergeler ve kurallar bölümüne bakın. ISelectionItemProvider arabirimi için gerekli üyeleri öğrenin.
ms.date: 03/30/2017
helpviewer_keywords:
- Selection Item control pattern
- UI Automation, Selection Item control pattern
- control patterns, Selection Item
ms.assetid: 76b0949a-5b23-4cfc-84cc-154f713e2e12
ms.openlocfilehash: 671a18d43a297026e4264cc35412fb9d233b2f33
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90551510"
---
# <a name="implementing-the-ui-automation-selectionitem-control-pattern"></a>UI Otomasyon SelectionItem Denetim Düzeni Uygulama
> [!NOTE]
> Bu belge, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ad alanında tanımlanan yönetilen sınıfları kullanmak isteyen .NET Framework geliştiricilere yöneliktir <xref:System.Windows.Automation> . Hakkında en son bilgiler için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] bkz. [WINDOWS Otomasyonu API: UI Otomasyonu](/windows/win32/winauto/entry-uiauto-win32).  
  
 Bu konuda <xref:System.Windows.Automation.Provider.ISelectionItemProvider> Özellikler, Yöntemler ve olaylar hakkında bilgiler de dahil olmak üzere uygulama yönergeleri ve kuralları tanıtılmaktadır. Ek başvuruların bağlantıları genel bakış sonunda listelenir.  
  
 <xref:System.Windows.Automation.SelectionItemPattern>Denetim stili, uygulayan kapsayıcı denetimlerinin bağımsız, seçilebilir alt öğeleri olarak davranan denetimleri desteklemek için kullanılır <xref:System.Windows.Automation.Provider.ISelectionProvider> . SelectionItem denetim modelini uygulayan denetimlerin örnekleri için bkz. [UI Otomasyon istemcileri Için denetim model eşlemesi](control-pattern-mapping-for-ui-automation-clients.md)  
  
<a name="Implementation_Guidelines_and_Conventions"></a>
## <a name="implementation-guidelines-and-conventions"></a>Uygulama kılavuzları ve kuralları  
 Seçim öğesi denetim modelini uygularken aşağıdaki kılavuz ve kurallara göz önünde yer verilmiştir:  
  
- <xref:System.Windows.Automation.Provider.IRawElementProviderFragmentRoot> **Görüntüleme özellikleri** Iletişim kutusundaki **ekran çözünürlüğü** kaydırıcısı gibi, uygulayan alt denetimleri yöneten tek seçimli denetimler, ve <xref:System.Windows.Automation.Provider.ISelectionProvider> öğelerinin her ikisini de uygulamalıdır <xref:System.Windows.Automation.Provider.IRawElementProviderFragment> <xref:System.Windows.Automation.Provider.ISelectionItemProvider> .  
  
<a name="Required_Members_for_the_IValueProvider_Interface"></a>
## <a name="required-members-for-iselectionitemprovider"></a>ISelectionItemProvider için gerekli Üyeler  
 Uygulama için aşağıdaki özellikler, Yöntemler ve olaylar gereklidir <xref:System.Windows.Automation.Provider.ISelectionItemProvider> .  
  
|Gerekli Üyeler|Üye türü|Notlar|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider.CanSelectMultiple%2A>|Özellik|Yok|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider.IsSelectionRequired%2A>|Özellik|Yok|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider.GetSelection%2A>|Yöntem|Yok|  
|<xref:System.Windows.Automation.SelectionPatternIdentifiers.InvalidatedEvent>|Olay|Kapsayıcıda bir seçim önemli ölçüde değiştirildiğinde ve <xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementSelectedEvent> <xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementRemovedFromSelectionEvent> sabit izin verenden daha fazla ve olay gönderilmesini gerektirdiğinde tetiklenir <xref:System.Windows.Automation.Provider.AutomationInteropProvider.InvalidateLimit> .|  
  
- Bir <xref:System.Windows.Automation.SelectionItemPattern.Select%2A> , <xref:System.Windows.Automation.SelectionItemPattern.AddToSelection%2A> , veya bir sonucu <xref:System.Windows.Automation.SelectionItemPattern.RemoveFromSelection%2A> Seçili tek bir öğe ise, bir oluşturulmalıdır <xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementSelectedEvent> ; Aksi takdirde <xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementAddedToSelectionEvent> /  <xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementRemovedFromSelectionEvent> uygun şekilde gönderin.  
  
<a name="Exceptions"></a>
## <a name="exceptions"></a>Özel durumlar  
 Sağlayıcılar aşağıdaki özel durumları oluşturması gerekir.  
  
|Özel durum türü|Koşul|  
|--------------------|---------------|  
|<xref:System.InvalidOperationException>|Aşağıdakilerden biri denendiğinde:<br /><br /> -   <xref:System.Windows.Automation.Provider.ISelectionItemProvider.RemoveFromSelection%2A>, <xref:System.Windows.Automation.SelectionPattern.IsSelectionRequiredProperty>  =  `true` ve öğesi zaten seçili olan tek seçimli kapsayıcıda çağrılır.<br />-   <xref:System.Windows.Automation.Provider.ISelectionItemProvider.RemoveFromSelection%2A>birden çok seçimli kapsayıcıda çağrılır <xref:System.Windows.Automation.SelectionPattern.IsSelectionRequiredProperty>  =  `true` ve yalnızca bir öğe seçilir.<br />-   <xref:System.Windows.Automation.Provider.ISelectionItemProvider.AddToSelection%2A>, <xref:System.Windows.Automation.SelectionPattern.CanSelectMultipleProperty>  =  `false` ve başka bir öğenin zaten seçildiği tek seçimli kapsayıcıda çağrılır.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [UI Otomasyon Denetim Düzenlerine Genel Bakış](ui-automation-control-patterns-overview.md)
- [UI Otomasyon Sağlayıcısında Denetim Düzenleri Desteği](support-control-patterns-in-a-ui-automation-provider.md)
- [İstemciler İçin UI Otomasyon Denetim Düzenleri](ui-automation-control-patterns-for-clients.md)
- [UI Otomasyon Seçim Denetim Düzenini Uygulama](implementing-the-ui-automation-selection-control-pattern.md)
- [UI Otomasyon Ağacına Genel Bakış](ui-automation-tree-overview.md)
- [UI Otomasyonda Önbelleğe Almayı Kullanma](use-caching-in-ui-automation.md)
- [Parça sağlayıcısı örneği](/previous-versions/dotnet/netframework-3.5/ms771502(v=vs.90))
