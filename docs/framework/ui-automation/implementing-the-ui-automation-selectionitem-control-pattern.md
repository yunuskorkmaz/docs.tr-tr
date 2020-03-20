---
title: UI Otomasyon SelectionItem Denetim Düzeni Uygulama
ms.date: 03/30/2017
helpviewer_keywords:
- Selection Item control pattern
- UI Automation, Selection Item control pattern
- control patterns, Selection Item
ms.assetid: 76b0949a-5b23-4cfc-84cc-154f713e2e12
ms.openlocfilehash: 02505224e4673592f1e169c40af1cfb098e5d9bb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79180096"
---
# <a name="implementing-the-ui-automation-selectionitem-control-pattern"></a>UI Otomasyon SelectionItem Denetim Düzeni Uygulama
> [!NOTE]
> Bu dokümantasyon, ad alanında tanımlanan yönetilen [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] sınıfları kullanmak <xref:System.Windows.Automation> isteyen .NET Framework geliştiricileri için tasarlanmıştır. Hakkında en son [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]bilgi için [Bkz. Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).  
  
 Bu konu, özellikler, yöntemler ve <xref:System.Windows.Automation.Provider.ISelectionItemProvider>olaylar hakkında bilgiler de dahil olmak üzere uygulama yönergeleri ve kuralları sunar. Ek başvurulara bağlantılar genel bakışın sonunda listelenir.  
  
 Denetim <xref:System.Windows.Automation.SelectionItemPattern> deseni, kapsayıcı denetimlerini uygulayan <xref:System.Windows.Automation.Provider.ISelectionProvider>tek tek, seçilebilir alt öğeleri olarak hareket eden denetimleri desteklemek için kullanılır. SelectionItem denetim deseni uygulayan denetim örnekleri [için, UI Otomasyon İstemleri için Denetim Deseni Eşleme'ye](control-pattern-mapping-for-ui-automation-clients.md) bakın  
  
<a name="Implementation_Guidelines_and_Conventions"></a>
## <a name="implementation-guidelines-and-conventions"></a>Uygulama Yönergeleri ve Sözleşmeleri  
 Seçim Öğesi denetim modelini uygularken aşağıdaki yönergeleri ve kuralları not edin:  
  
- **Ekran Özellikleri** iletişim kutusundaki Ekran <xref:System.Windows.Automation.Provider.IRawElementProviderFragmentRoot> **Çözünürlüğü** kaydırıcısı gibi uygulayan alt denetimleri <xref:System.Windows.Automation.Provider.ISelectionProvider> yöneten tek seçimli denetimler uygulamalı ve altları hem de <xref:System.Windows.Automation.Provider.IRawElementProviderFragment> <xref:System.Windows.Automation.Provider.ISelectionItemProvider>.  
  
<a name="Required_Members_for_the_IValueProvider_Interface"></a>
## <a name="required-members-for-iselectionitemprovider"></a>ISelectionItemProvider için Gerekli Üyeler  
 Aşağıdaki özellikleri, yöntemleri ve olayları uygulamak <xref:System.Windows.Automation.Provider.ISelectionItemProvider>için gereklidir.  
  
|Gerekli üyeler|Üye tipi|Notlar|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider.CanSelectMultiple%2A>|Özellik|None|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider.IsSelectionRequired%2A>|Özellik|None|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider.GetSelection%2A>|Yöntem|None|  
|<xref:System.Windows.Automation.SelectionPatternIdentifiers.InvalidatedEvent>|Olay|Bir kapsayıcıdaki bir seçim önemli ölçüde değiştiğinde <xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementRemovedFromSelectionEvent> ve <xref:System.Windows.Automation.Provider.AutomationInteropProvider.InvalidateLimit> sürekli izinlerden daha fazla <xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementSelectedEvent> ve olay göndermeyi gerektirdiğinde yükseltilir.|  
  
- Bir , , <xref:System.Windows.Automation.SelectionItemPattern.Select%2A>veya <xref:System.Windows.Automation.SelectionItemPattern.AddToSelection%2A>a'nın <xref:System.Windows.Automation.SelectionItemPattern.RemoveFromSelection%2A> sonucu tek bir <xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementSelectedEvent> seçili öğeise, bir öğe yükseltilmelidir; aksi <xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementAddedToSelectionEvent> /  <xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementRemovedFromSelectionEvent> takdirde uygun olarak gönderin.  
  
<a name="Exceptions"></a>
## <a name="exceptions"></a>Özel durumlar  
 Sağlayıcılar aşağıdaki özel durumları atmalıdır.  
  
|Özel durum türü|Koşul|  
|--------------------|---------------|  
|<xref:System.InvalidOperationException>|Aşağıdakilerden herhangi biri denendiğinde:<br /><br /> -   <xref:System.Windows.Automation.Provider.ISelectionItemProvider.RemoveFromSelection%2A>öğenin zaten seçildiği tek <xref:System.Windows.Automation.SelectionPattern.IsSelectionRequiredProperty>  =  `true` seçimli kapsayıcıya çağrılır.<br />-   <xref:System.Windows.Automation.Provider.ISelectionItemProvider.RemoveFromSelection%2A>birden çok seçim <xref:System.Windows.Automation.SelectionPattern.IsSelectionRequiredProperty>  =  `true` kapsayıcısı olarak adlandırılır ve yalnızca bir öğe seçilir.<br />-   <xref:System.Windows.Automation.Provider.ISelectionItemProvider.AddToSelection%2A>tek seçimli bir kapsayıcıda <xref:System.Windows.Automation.SelectionPattern.CanSelectMultipleProperty>  =  `false` çağrılır ve başka bir öğe zaten seçilir.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [UI Otomasyonu Denetim Desenlerine Genel Bakış](ui-automation-control-patterns-overview.md)
- [UI Otomasyonu Sağlayıcıda Denetim Düzenleri Desteği](support-control-patterns-in-a-ui-automation-provider.md)
- [İstemciler İçin UI Otomasyonu Denetim Düzenleri](ui-automation-control-patterns-for-clients.md)
- [UI Otomasyonu Selection Denetim Desenini Uygulama](implementing-the-ui-automation-selection-control-pattern.md)
- [UI Otomasyon Ağacına Genel Bakış](ui-automation-tree-overview.md)
- [UI Otomasyonunda Önbelleğe Almayı Kullanma](use-caching-in-ui-automation.md)
- [Parça Sağlayıcı Örneği](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms771502(v=vs.90))
