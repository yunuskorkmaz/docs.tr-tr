---
title: UI Otomasyon SelectionItem Denetim Düzeni Uygulama
ms.date: 03/30/2017
helpviewer_keywords:
- Selection Item control pattern
- UI Automation, Selection Item control pattern
- control patterns, Selection Item
ms.assetid: 76b0949a-5b23-4cfc-84cc-154f713e2e12
ms.openlocfilehash: aef1d31499f65834fa1268147e45f82294fe560a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69935684"
---
# <a name="implementing-the-ui-automation-selectionitem-control-pattern"></a>UI Otomasyon SelectionItem Denetim Düzeni Uygulama
> [!NOTE]
> Bu belge, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] <xref:System.Windows.Automation> ad alanında tanımlanan yönetilen sınıfları kullanmak isteyen .NET Framework geliştiricilere yöneliktir. Hakkında [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]en son bilgiler için bkz [. Windows Otomasyonu API 'si: UI Otomasyonu](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Bu konuda özellikler, Yöntemler ve olaylar hakkında <xref:System.Windows.Automation.Provider.ISelectionItemProvider>bilgiler de dahil olmak üzere uygulama yönergeleri ve kuralları tanıtılmaktadır. Ek başvuruların bağlantıları genel bakış sonunda listelenir.  
  
 Denetim stili, uygulayan <xref:System.Windows.Automation.Provider.ISelectionProvider>kapsayıcı denetimlerinin bağımsız, seçilebilir alt öğeleri olarak davranan denetimleri desteklemek için kullanılır. <xref:System.Windows.Automation.SelectionItemPattern> SelectionItem denetim modelini uygulayan denetimlerin örnekleri için bkz. [UI Otomasyon istemcileri Için denetim model eşlemesi](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md)  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a>Uygulama kılavuzları ve kuralları  
 Seçim öğesi denetim modelini uygularken aşağıdaki kılavuz ve kurallara göz önünde yer verilmiştir:  
  
- **Görüntüleme özellikleri** iletişim kutusundaki <xref:System.Windows.Automation.Provider.ISelectionProvider> **ekran çözünürlüğü** kaydırıcısı gibi, uygulayan <xref:System.Windows.Automation.Provider.IRawElementProviderFragmentRoot>alt denetimleri yöneten tek seçim denetimleri, her ikisini de uygulamalıdır.<xref:System.Windows.Automation.Provider.IRawElementProviderFragment> ve .<xref:System.Windows.Automation.Provider.ISelectionItemProvider>  
  
<a name="Required_Members_for_the_IValueProvider_Interface"></a>   
## <a name="required-members-for-iselectionitemprovider"></a>ISelectionItemProvider için gerekli Üyeler  
 Uygulama <xref:System.Windows.Automation.Provider.ISelectionItemProvider>için aşağıdaki özellikler, Yöntemler ve olaylar gereklidir.  
  
|Gerekli Üyeler|Üye türü|Notlar|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider.CanSelectMultiple%2A>|Özellik|Yok.|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider.IsSelectionRequired%2A>|Özellik|Yok.|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider.GetSelection%2A>|Yöntem|Yok.|  
|<xref:System.Windows.Automation.SelectionPatternIdentifiers.InvalidatedEvent>|Olay|Kapsayıcıda bir seçim önemli ölçüde değiştirildiğinde ve <xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementSelectedEvent> <xref:System.Windows.Automation.Provider.AutomationInteropProvider.InvalidateLimit> sabit izin verenden daha fazla ve <xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementRemovedFromSelectionEvent> olay gönderilmesini gerektirdiğinde tetiklenir.|  
  
- <xref:System.Windows.Automation.SelectionItemPattern.Select%2A>Bir <xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementAddedToSelectionEvent> /  <xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementSelectedEvent> <xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementRemovedFromSelectionEvent> ,, veya bir <xref:System.Windows.Automation.SelectionItemPattern.RemoveFromSelection%2A> sonucu seçili tek bir öğe ise, bir oluşturulmalıdır; Aksi takdirde uygun şekilde gönderin. <xref:System.Windows.Automation.SelectionItemPattern.AddToSelection%2A>  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a>Özel Durumlar  
 Sağlayıcılar aşağıdaki özel durumları oluşturması gerekir.  
  
|Özel durum türü|Koşul|  
|--------------------|---------------|  
|<xref:System.InvalidOperationException>|Aşağıdakilerden biri denendiğinde:<br /><br /> -   <xref:System.Windows.Automation.Provider.ISelectionItemProvider.RemoveFromSelection%2A>, `true` ve öğesi zaten seçili olan tek seçimli kapsayıcıda <xref:System.Windows.Automation.SelectionPattern.IsSelectionRequiredProperty>  =  çağrılır.<br />-   <xref:System.Windows.Automation.Provider.ISelectionItemProvider.RemoveFromSelection%2A>birden çok seçimli kapsayıcıda <xref:System.Windows.Automation.SelectionPattern.IsSelectionRequiredProperty>  =  `true` çağrılır ve yalnızca bir öğe seçilir.<br />-   <xref:System.Windows.Automation.Provider.ISelectionItemProvider.AddToSelection%2A>, `false` ve başka bir öğenin zaten seçildiği tek seçimli <xref:System.Windows.Automation.SelectionPattern.CanSelectMultipleProperty> kapsayıcıda  =  çağrılır.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [UI Otomasyonu Denetim Desenlerine Genel Bakış](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)
- [UI Otomasyonu Sağlayıcıda Denetim Düzenleri Desteği](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)
- [İstemciler İçin UI Otomasyonu Denetim Düzenleri](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)
- [UI Otomasyonu Selection Denetim Desenini Uygulama](../../../docs/framework/ui-automation/implementing-the-ui-automation-selection-control-pattern.md)
- [UI Otomasyon Ağacına Genel Bakış](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)
- [UI Otomasyonunda Önbelleğe Almayı Kullanma](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)
- [Parça sağlayıcısı örneği](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms771502(v=vs.90))
