---
title: UI Otomasyon RangeValue Denetim Düzeni Uygulama
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, Range Value
- Range Value control pattern
- UI Automation, Range Value control pattern
ms.assetid: 225feaa4-918e-418b-938e-7389338d0a69
ms.openlocfilehash: 847a8aae3fd0c3d6965c910d19a4cec11cd2a3b7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79180174"
---
# <a name="implementing-the-ui-automation-rangevalue-control-pattern"></a>UI Otomasyon RangeValue Denetim Düzeni Uygulama
> [!NOTE]
> Bu dokümantasyon, ad alanında tanımlanan yönetilen [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] sınıfları kullanmak <xref:System.Windows.Automation> isteyen .NET Framework geliştiricileri için tasarlanmıştır. Hakkında en son [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]bilgi için [Bkz. Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).  
  
 Bu <xref:System.Windows.Automation.Provider.IRangeValueProvider>konu, olaylar ve özellikler hakkında bilgiler de dahil olmak üzere, uygulama yönergeleri ve kuralları sunar. Ek başvurulara bağlantılar konunun sonunda listelenir.  
  
 Denetim <xref:System.Windows.Automation.RangeValuePattern> deseni, aralıktaki bir değere ayarlanabilen denetimleri desteklemek için kullanılır. Bu denetim deseni uygulayan denetim örnekleri için, [UI Otomasyon Istemcileri için Denetim Deseni Eşleciliği'ne](control-pattern-mapping-for-ui-automation-clients.md)bakın.  
  
<a name="Implementation_Guidelines_and_Conventions"></a>
## <a name="implementation-guidelines-and-conventions"></a>Uygulama Yönergeleri ve Sözleşmeleri  
 Aralık Değeri denetim deseni uygulanırken aşağıdaki yönergeleri ve kuralları not edin:  
  
- Denetimler, desteklenen özelliklerinin yerel veya kullanıcı tercihine göre yeniden kalibrasyonuna olanak sağlar. Bunun bir örneği, Sıcaklığı Fahrenhayt veya Santigrat cinsinden görüntülemek üzere ayarlanabilen bir termometre kontrolüdür.  
  
- İlerleme çubukları veya kaydırıcılar gibi belirsiz aralık değerlerine sahip denetimler, bu değerleri normalleştirmelidir.  
  
 ![İlerleme çubuğu.](./media/uia-rangevaluepattern-progress-bar.PNG "UIA_RangeValuePattern_Progress_Bar")  
Değerin Tür Tamsayı olduğu ve Minimum ve Maksimum Özellik Değerlerinin Sırasıyla 0 ve 100'e Normalleştirildiği İlerleme Çubuğu Örneği  
  
<a name="Required_Members_for_the_IRangeValueProvider"></a>
## <a name="required-members-for-irangevalueprovider"></a>IRangeValueProvider için Gerekli Üyeler  
  
|Gerekli üye|Üye tipi|Notlar|  
|---------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.RangeValuePattern.IsReadOnlyProperty>|Özellik|None|  
|<xref:System.Windows.Automation.RangeValuePattern.ValueProperty>|Özellik|None|  
|<xref:System.Windows.Automation.RangeValuePattern.LargeChangeProperty>|Özellik|None|  
|<xref:System.Windows.Automation.RangeValuePattern.SmallChangeProperty>|Özellik|None|  
|<xref:System.Windows.Automation.RangeValuePattern.MaximumProperty>|Özellik|None|  
|<xref:System.Windows.Automation.RangeValuePattern.MinimumProperty>|Özellik|None|  
|<xref:System.Windows.Automation.RangeValuePattern.SetValue%2A>|Yöntemler|None|  
  
 Bu denetim deseni ilişkili olaylar vardır.  
  
<a name="Exceptions"></a>
## <a name="exceptions"></a>Özel durumlar  
 Sağlayıcılar aşağıdaki özel durumları atmalıdır.  
  
|Özel durum türü|Koşul|  
|--------------------|---------------|  
|<xref:System.ArgumentOutOfRangeException>|<xref:System.Windows.Automation.RangeValuePattern.SetValue%2A>'den <xref:System.Windows.Automation.RangeValuePattern.MaximumProperty> büyük veya daha az bir <xref:System.Windows.Automation.RangeValuePattern.MinimumProperty>değerle çağrılır.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [UI Otomasyonu Denetim Desenlerine Genel Bakış](ui-automation-control-patterns-overview.md)
- [UI Otomasyonu Sağlayıcıda Denetim Düzenleri Desteği](support-control-patterns-in-a-ui-automation-provider.md)
- [İstemciler İçin UI Otomasyonu Denetim Düzenleri](ui-automation-control-patterns-for-clients.md)
- [UI Otomasyon Ağacına Genel Bakış](ui-automation-tree-overview.md)
- [UI Otomasyonunda Önbelleğe Almayı Kullanma](use-caching-in-ui-automation.md)
