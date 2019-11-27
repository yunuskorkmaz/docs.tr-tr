---
title: UI Otomasyon SelectionItem Denetim Düzeni Uygulama
ms.date: 03/30/2017
helpviewer_keywords:
- Selection Item control pattern
- UI Automation, Selection Item control pattern
- control patterns, Selection Item
ms.assetid: 76b0949a-5b23-4cfc-84cc-154f713e2e12
ms.openlocfilehash: 53a5a739918e61d53b3102c2c85d4ef2b8425173
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74447116"
---
# <a name="implementing-the-ui-automation-selectionitem-control-pattern"></a>UI Otomasyon SelectionItem Denetim Düzeni Uygulama
> [!NOTE]
> Bu belge, <xref:System.Windows.Automation> ad alanında tanımlanan yönetilen [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] sınıflarını kullanmak isteyen .NET Framework geliştiricilere yöneliktir. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]hakkında en son bilgiler için bkz. [Windows Otomasyonu API: UI Otomasyonu](/windows/win32/winauto/entry-uiauto-win32).  
  
 Bu konuda özellikler, Yöntemler ve olaylar hakkında bilgiler de dahil olmak üzere <xref:System.Windows.Automation.Provider.ISelectionItemProvider>uygulamak için yönergeler ve kurallar tanıtılmaktadır. Ek başvuruların bağlantıları genel bakış sonunda listelenir.  
  
 <xref:System.Windows.Automation.SelectionItemPattern> denetim stili, <xref:System.Windows.Automation.Provider.ISelectionProvider>uygulayan kapsayıcı denetimlerinin bağımsız, seçilebilir alt öğeleri olarak davranan denetimleri desteklemek için kullanılır. SelectionItem denetim modelini uygulayan denetimlerin örnekleri için bkz. [UI Otomasyon istemcileri Için denetim model eşlemesi](control-pattern-mapping-for-ui-automation-clients.md)  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a>Uygulama kılavuzları ve kuralları  
 Seçim öğesi denetim modelini uygularken aşağıdaki kılavuz ve kurallara göz önünde yer verilmiştir:  
  
- **Görüntüleme özellikleri** Iletişim kutusundaki **ekran çözünürlüğü** kaydırıcısı gibi <xref:System.Windows.Automation.Provider.IRawElementProviderFragmentRoot>uygulayan alt denetimleri yöneten tek seçim denetimleri, <xref:System.Windows.Automation.Provider.ISelectionProvider> uygulamalıdır ve alt öğeleri hem <xref:System.Windows.Automation.Provider.IRawElementProviderFragment> hem de <xref:System.Windows.Automation.Provider.ISelectionItemProvider>uygulamalıdır.  
  
<a name="Required_Members_for_the_IValueProvider_Interface"></a>   
## <a name="required-members-for-iselectionitemprovider"></a>ISelectionItemProvider için gerekli Üyeler  
 <xref:System.Windows.Automation.Provider.ISelectionItemProvider>uygulamak için aşağıdaki özellikler, Yöntemler ve olaylar gereklidir.  
  
|Gerekli Üyeler|Üye türü|Notlar|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider.CanSelectMultiple%2A>|Özellik|Yok.|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider.IsSelectionRequired%2A>|Özellik|Yok.|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider.GetSelection%2A>|Yöntem|Yok.|  
|<xref:System.Windows.Automation.SelectionPatternIdentifiers.InvalidatedEvent>|Olay|Kapsayıcıda bir seçim önemli ölçüde değiştirildiğinde ve <xref:System.Windows.Automation.Provider.AutomationInteropProvider.InvalidateLimit> sabitinden izin verdiğinden daha fazla <xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementSelectedEvent> ve <xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementRemovedFromSelectionEvent> olay gönderilmesini gerektirdiğinde tetiklenir.|  
  
- Bir <xref:System.Windows.Automation.SelectionItemPattern.Select%2A>sonucu, bir <xref:System.Windows.Automation.SelectionItemPattern.AddToSelection%2A>veya <xref:System.Windows.Automation.SelectionItemPattern.RemoveFromSelection%2A> tek bir seçili öğe ise, bir <xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementSelectedEvent> oluşmalıdır; Aksi takdirde <xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementAddedToSelectionEvent>/ <xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementRemovedFromSelectionEvent> uygun şekilde gönderin.  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a>Özel durumlar  
 Sağlayıcılar aşağıdaki özel durumları oluşturması gerekir.  
  
|Özel durum türü|Koşul|  
|--------------------|---------------|  
|<xref:System.InvalidOperationException>|Aşağıdakilerden biri denendiğinde:<br /><br /> -   <xref:System.Windows.Automation.Provider.ISelectionItemProvider.RemoveFromSelection%2A>, <xref:System.Windows.Automation.SelectionPattern.IsSelectionRequiredProperty> = `true` ve bir öğe zaten seçili olan tek seçimli kapsayıcıda çağırılır.<br />-   <xref:System.Windows.Automation.Provider.ISelectionItemProvider.RemoveFromSelection%2A>, <xref:System.Windows.Automation.SelectionPattern.IsSelectionRequiredProperty> = `true` ve yalnızca bir öğe seçildiği birden çok seçimli kapsayıcıda çağırılır.<br />-   <xref:System.Windows.Automation.Provider.ISelectionItemProvider.AddToSelection%2A>, <xref:System.Windows.Automation.SelectionPattern.CanSelectMultipleProperty> = `false` ve başka bir öğenin zaten seçildiği tek seçimli kapsayıcıda çağırılır.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [UI Otomasyonu Denetim Desenlerine Genel Bakış](ui-automation-control-patterns-overview.md)
- [UI Otomasyonu Sağlayıcıda Denetim Düzenleri Desteği](support-control-patterns-in-a-ui-automation-provider.md)
- [İstemciler İçin UI Otomasyonu Denetim Düzenleri](ui-automation-control-patterns-for-clients.md)
- [UI Otomasyonu Selection Denetim Desenini Uygulama](implementing-the-ui-automation-selection-control-pattern.md)
- [UI Otomasyon Ağacına Genel Bakış](ui-automation-tree-overview.md)
- [UI Otomasyonunda Önbelleğe Almayı Kullanma](use-caching-in-ui-automation.md)
- [Parça sağlayıcısı örneği](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms771502(v=vs.90))
