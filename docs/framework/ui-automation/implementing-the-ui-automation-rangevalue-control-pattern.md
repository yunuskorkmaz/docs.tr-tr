---
title: UI Otomasyon RangeValue Denetim Düzeni Uygulama
description: UI otomasyonunda RangeValue denetim deseninin uygulanması için yönergeleri ve kuralları gözden geçirin. IRangeValueProvider arabirimi için gereken üyelere bakın.
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, Range Value
- Range Value control pattern
- UI Automation, Range Value control pattern
ms.assetid: 225feaa4-918e-418b-938e-7389338d0a69
ms.openlocfilehash: ccb6aeb5f8451975d7e2e9649bbb82c0c3ae23d5
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87164085"
---
# <a name="implementing-the-ui-automation-rangevalue-control-pattern"></a>UI Otomasyon RangeValue Denetim Düzeni Uygulama
> [!NOTE]
> Bu belge, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ad alanında tanımlanan yönetilen sınıfları kullanmak isteyen .NET Framework geliştiricilere yöneliktir <xref:System.Windows.Automation> . Hakkında en son bilgiler için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] bkz. [WINDOWS Otomasyonu API: UI Otomasyonu](/windows/win32/winauto/entry-uiauto-win32).  
  
 Bu konu <xref:System.Windows.Automation.Provider.IRangeValueProvider> , olaylar ve özellikler hakkında bilgiler de dahil olmak üzere uygulama yönergelerini ve kurallarını tanıtır. Ek başvuruların bağlantıları konunun sonunda listelenmiştir.  
  
 <xref:System.Windows.Automation.RangeValuePattern>Denetim deseninin bir Aralık içindeki bir değere ayarlanabilir denetimleri desteklemek için kullanılır. Bu denetim modelini uygulayan denetimlerin örnekleri için bkz. [UI Otomasyonu istemcileri Için denetim model eşlemesi](control-pattern-mapping-for-ui-automation-clients.md).  
  
<a name="Implementation_Guidelines_and_Conventions"></a>
## <a name="implementation-guidelines-and-conventions"></a>Uygulama kılavuzları ve kuralları  
 Aralık değeri denetim modelini uygularken, aşağıdaki kılavuz ve kurallara göz önünde aklınızda olmanız gerekir:  
  
- Denetimler, yerel ayar veya kullanıcı tercihlerine göre desteklenen özelliklerinin yeniden yüklenmesine izin verir. Bunun bir örneği, sıcaklığın Fahrenveya santigrat cinsinden gösterilmesi için ayarlanabilir bir termometre denetimidir.  
  
- İlerleme çubukları veya kaydırıcılar gibi belirsiz Aralık değerlerine sahip denetimler bu değerlerin normalleştirilmesine sahip olmalıdır.  
  
 ![İlerleme çubuğu.](./media/uia-rangevaluepattern-progress-bar.PNG "UIA_RangeValuePattern_Progress_Bar")  
Değerin tamsayı türünde ve en düşük ve en yüksek özellik değerlerinin, sırasıyla 0 ve 100 olarak normalleştirilme Ilerleme çubuğu örneği  
  
<a name="Required_Members_for_the_IRangeValueProvider"></a>
## <a name="required-members-for-irangevalueprovider"></a>IRangeValueProvider için gerekli Üyeler  
  
|Gerekli üye|Üye türü|Notlar|  
|---------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.RangeValuePattern.IsReadOnlyProperty>|Özellik|Hiçbiri|  
|<xref:System.Windows.Automation.RangeValuePattern.ValueProperty>|Özellik|Hiçbiri|  
|<xref:System.Windows.Automation.RangeValuePattern.LargeChangeProperty>|Özellik|Hiçbiri|  
|<xref:System.Windows.Automation.RangeValuePattern.SmallChangeProperty>|Özellik|Hiçbiri|  
|<xref:System.Windows.Automation.RangeValuePattern.MaximumProperty>|Özellik|Hiçbiri|  
|<xref:System.Windows.Automation.RangeValuePattern.MinimumProperty>|Özellik|Hiçbiri|  
|<xref:System.Windows.Automation.RangeValuePattern.SetValue%2A>|Yöntemler|Hiçbiri|  
  
 Bu denetim deseninin ilişkili olayları yok.  
  
<a name="Exceptions"></a>
## <a name="exceptions"></a>Özel durumlar  
 Sağlayıcılar aşağıdaki özel durumları oluşturması gerekir.  
  
|Özel durum türü|Koşul|  
|--------------------|---------------|  
|<xref:System.ArgumentOutOfRangeException>|<xref:System.Windows.Automation.RangeValuePattern.SetValue%2A>değerinden büyük veya bundan küçük bir değerle çağırılır <xref:System.Windows.Automation.RangeValuePattern.MaximumProperty> <xref:System.Windows.Automation.RangeValuePattern.MinimumProperty> .|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [UI Otomasyon Denetim Düzenlerine Genel Bakış](ui-automation-control-patterns-overview.md)
- [UI Otomasyon Sağlayıcısında Denetim Düzenleri Desteği](support-control-patterns-in-a-ui-automation-provider.md)
- [İstemciler İçin UI Otomasyon Denetim Düzenleri](ui-automation-control-patterns-for-clients.md)
- [UI Otomasyon Ağacına Genel Bakış](ui-automation-tree-overview.md)
- [UI Otomasyonda Önbelleğe Almayı Kullanma](use-caching-in-ui-automation.md)
