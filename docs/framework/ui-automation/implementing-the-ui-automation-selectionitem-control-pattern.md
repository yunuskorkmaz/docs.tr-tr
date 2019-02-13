---
title: UI Otomasyon SelectionItem Denetim Düzeni Uygulama
ms.date: 03/30/2017
helpviewer_keywords:
- Selection Item control pattern
- UI Automation, Selection Item control pattern
- control patterns, Selection Item
ms.assetid: 76b0949a-5b23-4cfc-84cc-154f713e2e12
author: Xansky
ms.author: mhopkins
ms.openlocfilehash: 2d6e59264fb7a1ce396329abf2eb7db7f2a36429
ms.sourcegitcommit: 30e2fe5cc4165aa6dde7218ec80a13def3255e98
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/13/2019
ms.locfileid: "56220555"
---
# <a name="implementing-the-ui-automation-selectionitem-control-pattern"></a>UI Otomasyon SelectionItem Denetim Düzeni Uygulama
> [!NOTE]
>  Bu belge yönetilen kullanmak isteyen .NET Framework için tasarlanan [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tanımlanan sınıflar <xref:System.Windows.Automation> ad alanı. En son bilgileri [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], bkz: [Windows Automation API: UI Otomasyonu](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Bu konu, yönergeleri ve uygulama kuralları tanıtır <xref:System.Windows.Automation.Provider.ISelectionItemProvider>, özellikler, yöntemler ve olaylar hakkında bilgiler dahil olmak üzere. Ek başvurular bağlantılar genel bakış sonunda listelenmiştir.  
  
 <xref:System.Windows.Automation.SelectionItemPattern> Denetim düzeni uygulama kapsayıcı denetimleri tek tek, seçilebilir alt öğeleri olarak davranan denetimleri desteklemek için kullanılan <xref:System.Windows.Automation.Provider.ISelectionProvider>. SelectionItem denetim desenini uygulama denetimleri örnekleri için bkz: [denetim düzeni eşlemesi için UI Otomasyon istemcileri](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md)  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a>Uygulama yönergeleri ve kuralları  
 Seçim öğesi denetim düzeni uygularken aşağıdaki yönergeler ve kuralları dikkat edin:  
  
-   Uygulama alt denetimler yönetme tek seçim denetimleri <xref:System.Windows.Automation.Provider.IRawElementProviderFragmentRoot>, gibi **ekran çözünürlüğü** kaydırıcı **görüntü özellikleri** iletişim kutusu, uygulamalıdır<xref:System.Windows.Automation.Provider.ISelectionProvider>ve bunların alt öğeleri hem de uygulamalıdır <xref:System.Windows.Automation.Provider.IRawElementProviderFragment> ve <xref:System.Windows.Automation.Provider.ISelectionItemProvider>.  
  
<a name="Required_Members_for_the_IValueProvider_Interface"></a>   
## <a name="required-members-for-iselectionitemprovider"></a>Gerekli üyeleri ISelectionItemProvider için  
 Aşağıdaki özellikleri, yöntemleri ve olayları uygulamak için gerekli olan <xref:System.Windows.Automation.Provider.ISelectionItemProvider>.  
  
|Gerekli üyeleri|Üye türü|Notlar|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider.CanSelectMultiple%2A>|Özellik|Hiçbiri|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider.IsSelectionRequired%2A>|Özellik|Hiçbiri|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider.GetSelection%2A>|Yöntem|Hiçbiri|  
|<xref:System.Windows.Automation.SelectionPatternIdentifiers.InvalidatedEvent>|Olay|Bir kapsayıcı seçim önemli ölçüde değişti ve daha fazla gönderilmesi gerekir harekete geçirilen <xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementSelectedEvent> ve <xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementRemovedFromSelectionEvent> olayı <xref:System.Windows.Automation.Provider.AutomationInteropProvider.InvalidateLimit> sabiti izin verir.|  
  
-   Sonucu bir <xref:System.Windows.Automation.SelectionItemPattern.Select%2A>e <xref:System.Windows.Automation.SelectionItemPattern.AddToSelection%2A>, veya bir <xref:System.Windows.Automation.SelectionItemPattern.RemoveFromSelection%2A> tek bir seçili öğe bir <xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementSelectedEvent> oluşmalıdır; Aksi takdirde Gönder <xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementAddedToSelectionEvent> /  <xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementRemovedFromSelectionEvent> uygun şekilde.  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a>Özel Durumlar  
 Sağlayıcıları, aşağıdaki özel durumlar gerekir.  
  
|Özel durum türü|Koşul|  
|--------------------|---------------|  
|<xref:System.InvalidOperationException>|Aşağıdakilerden herhangi birini ne zaman denenmez:<br /><br /> -   <xref:System.Windows.Automation.Provider.ISelectionItemProvider.RemoveFromSelection%2A> tek seçimli bir kapsayıcı olarak adlandırılan burada <xref:System.Windows.Automation.SelectionPattern.IsSelectionRequiredProperty>  =  `true` ve bir öğe zaten seçilir.<br />-   <xref:System.Windows.Automation.Provider.ISelectionItemProvider.RemoveFromSelection%2A> Çoklu seçim bir kapsayıcı olarak adlandırılır burada <xref:System.Windows.Automation.SelectionPattern.IsSelectionRequiredProperty>  =  `true` ve yalnızca bir öğe seçilidir.<br />-   <xref:System.Windows.Automation.Provider.ISelectionItemProvider.AddToSelection%2A> tek seçimli bir kapsayıcı olarak adlandırılan burada <xref:System.Windows.Automation.SelectionPattern.CanSelectMultipleProperty>  =  `false` ve başka bir öğe zaten seçilir.|  
  
## <a name="see-also"></a>Ayrıca bkz.
- [UI Otomasyonu Denetim Desenlerine Genel Bakış](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)
- [UI Otomasyonu Sağlayıcıda Denetim Düzenleri Desteği](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)
- [İstemciler İçin UI Otomasyonu Denetim Düzenleri](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)
- [UI Otomasyonu Selection Denetim Desenini Uygulama](../../../docs/framework/ui-automation/implementing-the-ui-automation-selection-control-pattern.md)
- [UI Otomasyon Ağacına Genel Bakış](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)
- [UI Otomasyonunda Önbelleğe Almayı Kullanma](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)
- [Parça sağlayıcı örneği](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms771502(v=vs.90))
