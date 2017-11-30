---
title: "UI Otomasyon ScrollItem Denetim Düzeni Uygulama"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- control patterns, Scroll Item
- UI Automation, Scroll Item control pattern
- Scroll Item control pattern
ms.assetid: 903bab5c-80c1-44d7-bdc2-0a418893b987
caps.latest.revision: "16"
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: 92c3b4fad775dcd04299e18da126107d8fbb4471
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="implementing-the-ui-automation-scrollitem-control-pattern"></a>UI Otomasyon ScrollItem Denetim Düzeni Uygulama
> [!NOTE]
>  Bu belge yönetilen kullanmak isteyen .NET Framework için tasarlanan [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tanımlanan sınıflar <xref:System.Windows.Automation> ad alanı. Hakkında en yeni bilgiler için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], bkz: [Windows Otomasyon API: UI Otomasyonu](http://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Bu konu kılavuzları ve uygulamak için kuralları tanıtır <xref:System.Windows.Automation.Provider.IScrollItemProvider>, özellikleri, yöntemleri ve etkinlikleri hakkında bilgiler dahil olmak üzere. Ek başvurular bağlantılar konunun sonunda listelenmiştir.  
  
 <xref:System.Windows.Automation.ScrollItemPattern> Denetim düzeni tek tek alt denetimler uygulamak kapsayıcıların desteklemek için kullanılan <xref:System.Windows.Automation.Provider.IScrollProvider>. Bu denetim düzeni alt denetim ve alt denetim görüntülemek için kendi görünüm penceresinin içinde kapsayıcı şu anda görünür içeriğe (veya bölge) değiştirebilirsiniz emin olmak için kapsayıcısının arasında bir iletişim kanalı olarak görev yapar. Bu denetim düzeni uygulama denetimleri örnekleri için bkz: [denetim düzeni eşleştirmesi UI Otomasyon istemcileri için](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md).  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a>Uygulama rehberi ve kuralları  
 Kaydırma öğesi denetim deseni uygularken, aşağıdaki yönergeleri ve kuralları dikkat edin:  
  
-   İçinde bir pencere veya tuvale denetimi bulunan öğeleri IScrollItemProvider arabirimi uygulamak için gerekli değildir. Alternatif olarak, ancak bunlar için geçerli bir konum kullanıma gerekir <xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>. Bu kullanmak için UI otomasyon istemci uygulaması sağlayacak <xref:System.Windows.Automation.ScrollPattern> denetim düzeni yöntemlere alt öğesi görüntülemek için kapsayıcı.  
  
<a name="Required_Members_for_IScrollItemProvider"></a>   
## <a name="required-members-for-iscrollitemprovider"></a>Gerekli üyeleri IScrollItemProvider için  
 Aşağıdaki yöntem, IScrollProvider arabirimi uygulamak için gereklidir.  
  
|Gerekli üyeleri|Üye türü|Notlar|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.IScrollItemProvider.ScrollIntoView%2A>|-Yöntemi|Yok.|  
  
 Bu denetim düzeni ilişkili özellikleri ya da olaylar vardır.  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a>Özel Durumlar  
 Sağlayıcıları aşağıdaki özel durumlar oluşturma gerekir.  
  
|Özel durum türü|Koşul|  
|--------------------|---------------|  
|<xref:System.InvalidOperationException>|Bir öğe görünüme kaydırılan edilemez ise:<br /><br /> -   <xref:System.Windows.Automation.ScrollItemPattern.ScrollIntoView%2A>|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [UI Otomasyon denetim düzenlerine genel bakış](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)  
 [UI Otomasyon sağlayıcısında denetim düzenleri desteği](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)  
 [İstemciler için UI Otomasyon denetim düzenleri](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)  
 [UI Otomasyon ağacına genel bakış](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)  
 [UI otomasyonda önbelleğe almayı kullanma](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)
