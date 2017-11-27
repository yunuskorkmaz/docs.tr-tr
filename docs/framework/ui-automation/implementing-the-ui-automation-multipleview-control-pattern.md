---
title: "UI Otomasyon MultipleView Denetim Düzeni Uygulama"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- UI Automation, MultipleView control pattern
- MultipleView control pattern
- control patterns, MultipleView
ms.assetid: 5bf1b248-ffee-48c8-9613-0b134bbe9f6a
caps.latest.revision: "15"
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: 899f260dfef1d1e28a5a3605de772cdb7d358b64
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="implementing-the-ui-automation-multipleview-control-pattern"></a>UI Otomasyon MultipleView Denetim Düzeni Uygulama
> [!NOTE]
>  Bu belge yönetilen kullanmak isteyen .NET Framework için tasarlanan [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tanımlanan sınıflar <xref:System.Windows.Automation> ad alanı. Hakkında en yeni bilgiler için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], bkz: [Windows Otomasyon API: UI Otomasyonu](http://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Bu konu kılavuzları ve uygulamak için kuralları tanıtır <xref:System.Windows.Automation.Provider.IMultipleViewProvider>, olayları ve özellikleri hakkındaki bilgileri de dahil olmak üzere. Ek başvurular bağlantılar konunun sonunda listelenmiştir.  
  
 <xref:System.Windows.Automation.MultipleViewPattern> Denetim düzeni sağlayan ve birden çok bilgi veya alt denetimleri aynı kümesini gösterimlerini, arasında geçiş yapabilir denetimleri desteklemek için kullanılır.  
  
 Örnekler birden çok görünüm sunabilirsiniz denetimlerinizin (hangi içeriğinin küçük resimleri, kutucukları, simgeler veya ayrıntılar gösterebilir) liste görünümü [!INCLUDE[TLA#tla_xl](../../../includes/tlasharptla-xl-md.md)] grafikleri (pasta, satır, çubuğu, hücre değerini bir formülü olan), [!INCLUDE[TLA#tla_word](../../../includes/tlasharptla-word-md.md)] belgeleri (normal, Web düzeni yazdırma düzeni, okuma düzeni, anahat), [!INCLUDE[TLA#tla_outlook](../../../includes/tlasharptla-outlook-md.md)] Takvim (yıl, ay, hafta, gün), ve [!INCLUDE[TLA#tla_wmp](../../../includes/tlasharptla-wmp-md.md)] kaplamaları. Desteklenen görünümler denetim geliştirici tarafından belirlenir ve her denetim için özeldir.  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a>Uygulama rehberi ve kuralları  
 Birden çok görünüm denetim düzenini uygulama, aşağıdaki yönergeleri ve kuralları dikkat edin:  
  
-   <xref:System.Windows.Automation.Provider.IMultipleViewProvider>Ayrıca geçerli görünümü sağlayan denetimden farklıysa, geçerli görünümü yöneten bir kapsayıcısı üzerinde uygulanmalıdır. Örneğin, denetimin görünümünü Windows Explorer uygulamasından yönetilen sırasında Windows Explorer geçerli klasör içerik için bir liste denetimini içerir.  
  
-   İçeriğini sıralama yapabiliyor bir denetim, birden çok görünüm desteklemek için dikkate alınmaz.  
  
-   Görünümler koleksiyonu örneklerinde aynı olmalıdır.  
  
-   Görünüm adları metin okuma, Braille ve diğer okunabilir uygulamaları kullanmak için uygun olması gerekir.  
  
<a name="Required_Members_for_IMultipleViewProvider"></a>   
## <a name="required-members-for-imultipleviewprovider"></a>Gerekli üyeleri IMultipleViewProvider için  
 Aşağıdaki özellikleri ve yöntemleri IMultipleViewProvider uygulamak için gereklidir.  
  
|Gerekli üyeleri|Üye türü|Notlar|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.IMultipleViewProvider.CurrentView%2A>|Özellik|Yok.|  
|<xref:System.Windows.Automation.Provider.IMultipleViewProvider.GetSupportedViews%2A>|Yöntem|Yok.|  
|<xref:System.Windows.Automation.Provider.IMultipleViewProvider.GetViewName%2A>|Yöntem|Yok.|  
|<xref:System.Windows.Automation.Provider.IMultipleViewProvider.SetCurrentView%2A>|Yöntem|Yok.|  
  
 Bu denetim düzeni ile ilişkili olay yok.  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a>Özel Durumlar  
 Sağlayıcı, aşağıdaki özel durumlar oluşturma gerekir.  
  
|Özel durum türü|Koşul|  
|--------------------|---------------|  
|<xref:System.ArgumentException>|Zaman da <xref:System.Windows.Automation.Provider.IMultipleViewProvider.SetCurrentView%2A> veya <xref:System.Windows.Automation.Provider.IMultipleViewProvider.GetViewName%2A> desteklenen görünümler koleksiyonunun bir üyesi olmayan bir parametre olarak adlandırılır.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [UI Otomasyon denetim düzenlerine genel bakış](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)  
 [UI Otomasyon sağlayıcısında denetim düzenleri desteği](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)  
 [İstemciler için UI Otomasyon denetim düzenleri](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)  
 [UI Otomasyon ağacına genel bakış](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)  
 [UI otomasyonda önbelleğe almayı kullanma](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)
