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
manager: markl
ms.openlocfilehash: abf1c1851e10036ecf46b04662d41a4d9f2667e1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="implementing-the-ui-automation-selectionitem-control-pattern"></a>UI Otomasyon SelectionItem Denetim Düzeni Uygulama
> [!NOTE]
>  Bu belge yönetilen kullanmak isteyen .NET Framework için tasarlanan [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tanımlanan sınıflar <xref:System.Windows.Automation> ad alanı. Hakkında en yeni bilgiler için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], bkz: [Windows Otomasyon API: UI Otomasyonu](http://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Bu konu kılavuzları ve uygulamak için kuralları tanıtır <xref:System.Windows.Automation.Provider.ISelectionItemProvider>, özellikleri, yöntemleri ve etkinlikleri hakkında bilgiler dahil olmak üzere. Ek başvurular bağlantılar genel bakış sonunda listelenmiştir.  
  
 <xref:System.Windows.Automation.SelectionItemPattern> Denetim düzeni uygulama kapsayıcı denetimleri tek tek, seçilebilir alt öğeleri olarak hareket denetimleri desteklemek için kullanılan <xref:System.Windows.Automation.Provider.ISelectionProvider>. SelectionItem denetim düzeni uygulama denetimleri örnekleri için bkz: [denetim düzeni eşleştirmesi UI Otomasyon istemcileri için](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md)  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a>Uygulama rehberi ve kuralları  
 Seçim öğesi denetim düzeni uygulama, aşağıdaki yönergeleri ve kuralları dikkat edin:  
  
-   Uygulama alt denetimleri yönetmek tek seçim denetimleri <xref:System.Windows.Automation.Provider.IRawElementProviderFragmentRoot>, gibi **ekran çözünürlüğü** uygulamasındaki kaydırıcı **görüntü özellikleri** iletişim kutusu, uygulamalıdır<xref:System.Windows.Automation.Provider.ISelectionProvider>ve bunların alt öğeleri hem uygulamalıdır <xref:System.Windows.Automation.Provider.IRawElementProviderFragment> ve <xref:System.Windows.Automation.Provider.ISelectionItemProvider>.  
  
<a name="Required_Members_for_the_IValueProvider_Interface"></a>   
## <a name="required-members-for-iselectionitemprovider"></a>Gerekli üyeleri ISelectionItemProvider için  
 Aşağıdaki özellikleri, yöntemleri ve olayları uygulamak için gerekli olan <xref:System.Windows.Automation.Provider.ISelectionItemProvider>.  
  
|Gerekli üyeleri|Üye türü|Notlar|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider.CanSelectMultiple%2A>|Özellik|Yok.|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider.IsSelectionRequired%2A>|Özellik|Yok.|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider.GetSelection%2A>|Yöntem|Yok.|  
|<xref:System.Windows.Automation.SelectionPatternIdentifiers.InvalidatedEvent>|Olay|Bir kapsayıcıda seçimi önemli ölçüde değişti ve daha fazla gönderme gerektirdiğinde yükseltilmiş <xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementSelectedEvent> ve <xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementRemovedFromSelectionEvent> daha olayları <xref:System.Windows.Automation.Provider.AutomationInteropProvider.InvalidateLimit> sabiti izin verir.|  
  
-   Varsa sonucunu bir <xref:System.Windows.Automation.SelectionItemPattern.Select%2A>, bir <xref:System.Windows.Automation.SelectionItemPattern.AddToSelection%2A>, veya bir <xref:System.Windows.Automation.SelectionItemPattern.RemoveFromSelection%2A> tek seçilen öğe bir <xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementSelectedEvent> oluşmalıdır; Aksi takdirde Gönder <xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementAddedToSelectionEvent> /  <xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementRemovedFromSelectionEvent> uygun şekilde.  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a>Özel Durumlar  
 Sağlayıcıları aşağıdaki özel durumlar oluşturma gerekir.  
  
|Özel durum türü|Koşul|  
|--------------------|---------------|  
|<xref:System.InvalidOperationException>|Ne zaman aşağıdakilerden herhangi birini denenme:<br /><br /> -   <xref:System.Windows.Automation.Provider.ISelectionItemProvider.RemoveFromSelection%2A> bir tek seçim kapsayıcıda adlı nerede <xref:System.Windows.Automation.SelectionPattern.IsSelectionRequiredProperty>  =  `true` ve bir öğe zaten seçilidir.<br />-   <xref:System.Windows.Automation.Provider.ISelectionItemProvider.RemoveFromSelection%2A> bir çoklu seçim kapsayıcıda adlı nerede <xref:System.Windows.Automation.SelectionPattern.IsSelectionRequiredProperty>  =  `true` ve yalnızca tek bir öğe seçilidir.<br />-   <xref:System.Windows.Automation.Provider.ISelectionItemProvider.AddToSelection%2A> bir tek seçim kapsayıcıda adlı nerede <xref:System.Windows.Automation.SelectionPattern.CanSelectMultipleProperty>  =  `false` ve başka bir öğe zaten seçilidir.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [UI Otomasyonu Denetim Desenlerine Genel Bakış](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)  
 [UI Otomasyonu Sağlayıcıda Denetim Düzenleri Desteği](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)  
 [İstemciler İçin UI Otomasyonu Denetim Düzenleri](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)  
 [UI Otomasyonu Selection Denetim Desenini Uygulama](../../../docs/framework/ui-automation/implementing-the-ui-automation-selection-control-pattern.md)  
 [UI Otomasyon Ağacına Genel Bakış](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)  
 [UI Otomasyonunda Önbelleğe Almayı Kullanma](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)  
 [Parça sağlayıcı örneği](http://msdn.microsoft.com/library/778ef1bc-8610-4bc9-886e-aeff94a8a13e)
