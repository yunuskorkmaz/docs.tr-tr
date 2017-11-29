---
title: "UI Otomasyon Seçim Denetim Düzenini Uygulama"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Selection control pattern
- UI Automation, Selection control pattern
- control patterns, Selection
ms.assetid: 449c3068-a5d6-4f66-84c6-1bcc7dd4d209
caps.latest.revision: "33"
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: cb8b47b147e3a7a3c615418e2c0987e4d6a20f4c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="implementing-the-ui-automation-selection-control-pattern"></a>UI Otomasyon Seçim Denetim Düzenini Uygulama
> [!NOTE]
>  Bu belge yönetilen kullanmak isteyen .NET Framework için tasarlanan [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tanımlanan sınıflar <xref:System.Windows.Automation> ad alanı. Hakkında en yeni bilgiler için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], bkz: [Windows Otomasyon API: UI Otomasyonu](http://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Bu konu kılavuzları ve uygulamak için kuralları tanıtır <xref:System.Windows.Automation.Provider.ISelectionProvider>, olayları ve özellikleri hakkındaki bilgileri de dahil olmak üzere. Ek başvurular bağlantılar konunun sonunda listelenmiştir.  
  
 <xref:System.Windows.Automation.SelectionPattern> Denetim düzeni seçilebilir alt öğeleri koleksiyonu için kapsayıcı olarak hareket denetimleri desteklemek için kullanılır. Bu öğenin alt öğeleri uygulamalıdır <xref:System.Windows.Automation.Provider.ISelectionItemProvider>. Bu denetim düzeni uygulama denetimleri örnekleri için bkz: [denetim düzeni eşleştirmesi UI Otomasyon istemcileri için](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md).  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a>Uygulama rehberi ve kuralları  
 Seçim denetim düzenini uygulama, aşağıdaki yönergeleri ve kuralları dikkat edin:  
  
-   Denetimleri uygulayan <xref:System.Windows.Automation.Provider.ISelectionProvider> tek veya birden çok alt öğeleri seçilmesini sağlar. Örneğin, açılan kutu, kaydırıcıyı ve radyo düğmesi grubunda tek seçimi destekler ancak liste kutusu, liste görünümü ve ağaç görünümü birden çok seçimin destekler.  
  
-   En az, en büyük ve sürekli bir aralık gibi sahip denetimleri **birim** kaydırıcı denetimi, uygulamanız gerekir <xref:System.Windows.Automation.Provider.IRangeValueProvider> yerine <xref:System.Windows.Automation.Provider.ISelectionProvider>.  
  
-   Uygulama alt denetimleri yönetmek tek seçim denetimleri <xref:System.Windows.Automation.Provider.IRawElementProviderFragmentRoot>, gibi **ekran çözünürlüğü** uygulamasındaki kaydırıcı **görüntü özellikleri** iletişim kutusu veya **rengi Seçici** Seçim denetiminden [!INCLUDE[TLA#tla_word](../../../includes/tlasharptla-word-md.md)] (aşağıda gösterilmiştir), uygulamalıdır <xref:System.Windows.Automation.Provider.ISelectionProvider>; bunların alt öğeleri hem uygulamalıdır <xref:System.Windows.Automation.Provider.IRawElementProviderFragment> ve <xref:System.Windows.Automation.Provider.ISelectionItemProvider>.  
  
 ![Renk Seçici vurgulanan sarı ile. ] (../../../docs/framework/ui-automation/media/uia-valuepattern-colorpicker.png "UIA_ValuePattern_ColorPicker")  
Renk örneği dize eşleme örneği  
  
-   Menüleri desteklemez <xref:System.Windows.Automation.SelectionPattern>. Hem grafik hem de metin menü öğeleri ile çalışıyorsanız (gibi **önizleme bölmesinde** öğeler **Görünüm** menüde [!INCLUDE[TLA#tla_outlook](../../../includes/tlasharptla-outlook-md.md)]) ve durumu iletmek gereken, uygulamalıdır<xref:System.Windows.Automation.Provider.IToggleProvider>.  
  
<a name="Required_Members_for_ISelectionProvider"></a>   
## <a name="required-members-for-iselectionprovider"></a>Gerekli üyeleri ISelectionProvider için  
 Aşağıdaki özellikleri, yöntemleri ve olayları için gerekli olan <xref:System.Windows.Automation.Provider.ISelectionProvider> arabirimi.  
  
|Gerekli üyeleri|Tür|Notlar|  
|----------------------|----------|-----------|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider.CanSelectMultiple%2A>|Özellik|Özellik değişti olayları kullanarak desteklemelidir <xref:System.Windows.Automation.Automation.AddAutomationPropertyChangedEventHandler%2A> ve <xref:System.Windows.Automation.Automation.RemoveAutomationPropertyChangedEventHandler%2A>.|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider.IsSelectionRequired%2A>|Özellik|Özellik değişti olayları kullanarak desteklemelidir <xref:System.Windows.Automation.Automation.AddAutomationPropertyChangedEventHandler%2A> ve <xref:System.Windows.Automation.Automation.RemoveAutomationPropertyChangedEventHandler%2A>.|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider.GetSelection%2A>|Yöntem|Yok.|  
|<xref:System.Windows.Automation.SelectionPatternIdentifiers.InvalidatedEvent>|Olay|Bir kapsayıcıda seçimi önemli ölçüde değişti ve daha çok ekleme ve kaldırma olay gönderme gerektirdiğinde yükseltilmiş <xref:System.Windows.Automation.Provider.AutomationInteropProvider.InvalidateLimit> sabiti izin verir.|  
  
 <xref:System.Windows.Automation.Provider.ISelectionProvider.IsSelectionRequired%2A> Ve <xref:System.Windows.Automation.Provider.ISelectionProvider.CanSelectMultiple%2A> özellikleri dinamik olabilir. Örneğin, bir denetimin ilk durumunu gösteren varsayılan olarak, seçilen öğeleri olmayabilir <xref:System.Windows.Automation.Provider.ISelectionProvider.IsSelectionRequired%2A> olan `false`. Bir öğe seçtikten sonra ancak, denetimi her zaman en az bir öğe seçili olması gerekir. Benzer şekilde, nadir durumlarda başlatmayı seçilmesi, ancak sonradan yapılacak yalnızca tek seçimler izin vermek birden çok öğe denetim sağlayabilir.  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a>Özel Durumlar  
 Sağlayıcıları aşağıdaki özel durumlar oluşturma gerekir.  
  
|Özel durum türü|Koşul|  
|--------------------|---------------|  
|<xref:System.Windows.Automation.ElementNotEnabledException>|Denetim etkin değilse.|  
|<xref:System.InvalidOperationException>|Denetim gizli değilse.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [UI Otomasyon denetim düzenlerine genel bakış](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)  
 [UI Otomasyon sağlayıcısında denetim düzenleri desteği](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)  
 [İstemciler için UI Otomasyon denetim düzenleri](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)  
 [UI Otomasyon SelectionItem denetim düzeni uygulama](../../../docs/framework/ui-automation/implementing-the-ui-automation-selectionitem-control-pattern.md)  
 [UI Otomasyon ağacına genel bakış](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)  
 [UI otomasyonda önbelleğe almayı kullanma](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)
