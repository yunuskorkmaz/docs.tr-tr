---
title: "UI Otomasyon RangeValue Denetim Düzeni Uygulama"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- control patterns, Range Value
- Range Value control pattern
- UI Automation, Range Value control pattern
ms.assetid: 225feaa4-918e-418b-938e-7389338d0a69
caps.latest.revision: "19"
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: 9ae70f1dfc4c0a8d97d2fbcfd23822450727e59e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="implementing-the-ui-automation-rangevalue-control-pattern"></a>UI Otomasyon RangeValue Denetim Düzeni Uygulama
> [!NOTE]
>  Bu belge yönetilen kullanmak isteyen .NET Framework için tasarlanan [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tanımlanan sınıflar <xref:System.Windows.Automation> ad alanı. Hakkında en yeni bilgiler için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], bkz: [Windows Otomasyon API: UI Otomasyonu](http://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Bu konu kılavuzları ve uygulamak için kuralları tanıtır <xref:System.Windows.Automation.Provider.IRangeValueProvider>, olayları ve özellikleri hakkındaki bilgileri de dahil olmak üzere. Ek başvurular bağlantılar konunun sonunda listelenmiştir.  
  
 <xref:System.Windows.Automation.RangeValuePattern> Denetim düzeni bir aralık içinde bir değere ayarlanabilir denetimleri desteklemek için kullanılır. Bu denetim düzeni uygulama denetimleri örnekleri için bkz: [denetim düzeni eşleştirmesi UI Otomasyon istemcileri için](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md).  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a>Uygulama rehberi ve kuralları  
 Aralık değeri denetim düzeni uygulama, aşağıdaki yönergeleri ve kuralları dikkat edin:  
  
-   Denetimler recalibration bunların desteklenen özelliklerinin yerel ayar veya kullanıcı alınarak izin verir. Bunun bir örneğini sıcaklık Fahrenhayt veya derece cinsinden görüntülemek için ayarlayabileceğiniz bir termometre denetimdir.  
  
-   İlerleme çubukları veya kaydırıcıları, gibi belirsiz aralık değerlerine sahip denetimleri normalleştirilmiş bu değerlere sahip olmalıdır.  
  
 ![İlerleme çubuğu. ] (../../../docs/framework/ui-automation/media/uia-rangevaluepattern-progress-bar.PNG "UIA_RangeValuePattern_Progress_Bar")  
Değerin türü tamsayı ve Minimum ve maksimum özellik değerlerini olduğu bir ilerleme çubuğu örneği normalleştirilmiş 0 ile 100, sırasıyla  
  
<a name="Required_Members_for_the_IRangeValueProvider"></a>   
## <a name="required-members-for-irangevalueprovider"></a>Gerekli üyeleri IRangeValueProvider için  
  
|Gerekli üye|Üye türü|Notlar|  
|---------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.RangeValuePattern.IsReadOnlyProperty>|Özellik|Yok.|  
|<xref:System.Windows.Automation.RangeValuePattern.ValueProperty>|Özellik|Yok.|  
|<xref:System.Windows.Automation.RangeValuePattern.LargeChangeProperty>|Özellik|Yok.|  
|<xref:System.Windows.Automation.RangeValuePattern.SmallChangeProperty>|Özellik|Yok.|  
|<xref:System.Windows.Automation.RangeValuePattern.MaximumProperty>|Özellik|Yok.|  
|<xref:System.Windows.Automation.RangeValuePattern.MinimumProperty>|Özellik|Yok.|  
|<xref:System.Windows.Automation.RangeValuePattern.SetValue%2A>|Yöntemler|Yok.|  
  
 Bu denetim düzeni ilişkili olay vardır.  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a>Özel Durumlar  
 Sağlayıcıları aşağıdaki özel durumlar oluşturma gerekir.  
  
|Özel durum türü|Koşul|  
|--------------------|---------------|  
|<xref:System.ArgumentOutOfRangeException>|<xref:System.Windows.Automation.RangeValuePattern.SetValue%2A>herhangi bir değerle çağrılır büyük <xref:System.Windows.Automation.RangeValuePattern.MaximumProperty> veya küçüktür <xref:System.Windows.Automation.RangeValuePattern.MinimumProperty>.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [UI Otomasyon denetim düzenlerine genel bakış](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)  
 [UI Otomasyon sağlayıcısında denetim düzenleri desteği](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)  
 [İstemciler için UI Otomasyon denetim düzenleri](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)  
 [UI Otomasyon ağacına genel bakış](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)  
 [UI otomasyonda önbelleğe almayı kullanma](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)
