---
title: "UI Otomasyonu Dönüştürme Denetim Düzenini Uygulama"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- control patterns, Transform
- Transform control pattern
- UI Automation, Transform control pattern
ms.assetid: 5f49d843-5845-4800-9d9c-56ce0d146844
caps.latest.revision: "14"
author: Xansky
ms.author: mhopkins
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 629428f2f5e30d0b7dee07f270fcf5bacaeb5f30
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="implementing-the-ui-automation-transform-control-pattern"></a>UI Otomasyonu Dönüştürme Denetim Düzenini Uygulama
> [!NOTE]
>  Bu belge yönetilen kullanmak isteyen .NET Framework için tasarlanan [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tanımlanan sınıflar <xref:System.Windows.Automation> ad alanı. Hakkında en yeni bilgiler için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], bkz: [Windows Otomasyon API: UI Otomasyonu](http://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Bu konu kılavuzları ve uygulamak için kuralları tanıtır <xref:System.Windows.Automation.Provider.ITransformProvider>, özellikleri, yöntemleri ve etkinlikleri hakkında bilgiler dahil olmak üzere. Ek başvurular bağlantılar konunun sonunda listelenmiştir.  
  
 <xref:System.Windows.Automation.TransformPattern> Denetim düzeni taşınmış, yeniden boyutlandırılmış veya iki boyutlu bir boşluğuna Döndürülmüş denetimleri desteklemek için kullanılır. Bu denetim düzeni uygulama denetimleri örnekleri için bkz: [denetim düzeni eşleştirmesi UI Otomasyon istemcileri için](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md).  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a>Uygulama rehberi ve kuralları  
 Dönüştürme denetim düzenini uygulama, aşağıdaki yönergeleri ve kuralları dikkat edin:  
  
-   Bu denetim düzeni için destek masaüstündeki nesneler için sınırlı değildir. Alt taşınmış, yeniden boyutlandırılmış veya serbestçe kapsayıcı sınırlar içinde Döndürülmüş bu denetim düzeni ayrıca bir kapsayıcı nesne gruplar tarafından desteklenmesi gerekir.  
  
-   Bir nesne taşınamaz, yeniden boyutlandırılabilir ya da sonuçta elde edilen ekran konumuna veya tamamen kapsayıcısının ve bu nedenle klavye için erişilemez koordinatları dışında olabilir (örneğin, üst düzey bir pencere off-screen taşındığında veya bir fare şekilde Döndürülmüş alt nesne kapsayıcının görünüm penceresinin sınırları dışında taşınır). Bu durumlarda, nesne, istenen ekran koordinatları olarak mümkün olduğunca kapsayıcı sınırlar içinde geçersiz üst veya sol koordinatları ile yakın yerleştirilir.  
  
-   Bir nesne taşınırsa, birden çok monitör sistemler için yeniden boyutlandırılmış veya birleştirilmiş masaüstü ekran koordinatları tamamen dışında döndürülen nesne birincil monitörde istenen koordinatları olarak mümkün olduğunca yakın yerleştirilir.  
  
-   Tüm parametreleri ve özellik değerlerini mutlak ve yerel ayar bağımsızdır.  
  
<a name="Required_Members_for_the_IValueProvider_Interface"></a>   
## <a name="required-members-for-itransformprovider"></a>Gerekli üyeleri ITransformProvider için  
 Aşağıdaki özellikleri ve yöntemleri uygulamak için gerekli olan <xref:System.Windows.Automation.Provider.ITransformProvider>.  
  
|Gerekli üyeleri|Üye türü|Notlar|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.ITransformProvider.CanMove%2A>|Özellik|Yok.|  
|<xref:System.Windows.Automation.Provider.ITransformProvider.CanResize%2A>|Özellik|Yok.|  
|<xref:System.Windows.Automation.Provider.ITransformProvider.CanRotate%2A>|Özellik|Yok.|  
|<xref:System.Windows.Automation.Provider.ITransformProvider.Move%2A>|Yöntem|Yok.|  
|<xref:System.Windows.Automation.Provider.ITransformProvider.Resize%2A>|Yöntem|Yok.|  
|<xref:System.Windows.Automation.Provider.ITransformProvider.Rotate%2A>|Yöntem|Yok.|  
  
 Bu denetim düzeni ilişkili olay vardır.  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a>Özel Durumlar  
 Sağlayıcıları aşağıdaki özel durumlar oluşturma gerekir.  
  
|Özel durum türü|Koşul|  
|--------------------|---------------|  
|<xref:System.InvalidOperationException>|<xref:System.Windows.Automation.Provider.ITransformProvider.Move%2A><br /><br /> -İf <xref:System.Windows.Automation.TransformPatternIdentifiers.CanMoveProperty> false olur.|  
|<xref:System.InvalidOperationException>|<xref:System.Windows.Automation.Provider.ITransformProvider.Resize%2A><br /><br /> -İf <xref:System.Windows.Automation.TransformPatternIdentifiers.CanResizeProperty> false olur.|  
|<xref:System.InvalidOperationException>|<xref:System.Windows.Automation.Provider.ITransformProvider.Rotate%2A><br /><br /> -İf <xref:System.Windows.Automation.TransformPatternIdentifiers.CanRotateProperty> false olur.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [UI Otomasyonu Denetim Desenlerine Genel Bakış](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)  
 [UI Otomasyonu Sağlayıcıda Denetim Düzenleri Desteği](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)  
 [İstemciler İçin UI Otomasyonu Denetim Düzenleri](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)  
 [UI Otomasyon Ağacına Genel Bakış](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)  
 [UI Otomasyonunda Önbelleğe Almayı Kullanma](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)
