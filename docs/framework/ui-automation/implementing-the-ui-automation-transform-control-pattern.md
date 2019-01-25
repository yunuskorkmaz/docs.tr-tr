---
title: UI Otomasyonu Dönüştürme Denetim Düzenini Uygulama
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, Transform
- Transform control pattern
- UI Automation, Transform control pattern
ms.assetid: 5f49d843-5845-4800-9d9c-56ce0d146844
author: Xansky
ms.author: mhopkins
ms.openlocfilehash: 5070403cea88fb9c4a5b5d6140fe4d5a5218c636
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54512173"
---
# <a name="implementing-the-ui-automation-transform-control-pattern"></a>UI Otomasyonu Dönüştürme Denetim Düzenini Uygulama
> [!NOTE]
>  Bu belge yönetilen kullanmak isteyen .NET Framework için tasarlanan [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tanımlanan sınıflar <xref:System.Windows.Automation> ad alanı. En son bilgileri [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], bkz: [Windows Automation API: UI Otomasyonu](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Bu konu, yönergeleri ve uygulama kuralları tanıtır <xref:System.Windows.Automation.Provider.ITransformProvider>, özellikler, yöntemler ve olaylar hakkında bilgiler dahil olmak üzere. Ek başvurular bağlantılar konunun sonunda listelenmiştir.  
  
 <xref:System.Windows.Automation.TransformPattern> Denetim düzeni taşınmış, yeniden boyutlandırılabilir veya iki boyutlu bir alanı içinde Döndürülmüş denetimleri desteklemek için kullanılır. Bu denetim düzeni uygulama denetimleri örnekleri için bkz: [denetim düzeni eşlemesi için UI Otomasyonu istemcileri](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md).  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a>Uygulama yönergeleri ve kuralları  
 Dönüşüm denetim düzeni uygularken aşağıdaki yönergeler ve kuralları dikkat edin:  
  
-   Bu denetim düzeni için destek masaüstünde nesnelere sınırlı değildir. Alt taşınmış, yeniden boyutlandırılabilir veya serbestçe kapsayıcının sınırları içinde döndürülen, bu denetim düzeni de kapsayıcı nesnesinin alt tarafından desteklenmesi gerekir.  
  
-   Bir nesne taşınamaz, yeniden boyutlandırılmış veya elde edilen ekran konumunu veya tamamen kapsayıcısının ve bu nedenle erişilemez klavye koordinatları dışında olması (örneğin, bir üst düzey pencere off-screen taşındığında veya bir fare Döndürülmüş alt nesne kapsayıcının Görünüm penceresi sınırları dışında taşınır). Bu gibi durumlarda, istenen ekran koordinatları olarak mümkün olduğunca kapsayıcı sınırlar içinde geçersiz üst veya sol koordinatları ile yakın nesne yerleştirilir.  
  
-   Bir nesne taşınırsa, çoklu monitör sistemler için yeniden boyutlandırılıyor veya tamamen birleşik masaüstü ekran koordinatları dışında döndürülen nesne birincil monitörde istenen koordinatları olarak mümkün olduğunca yakın yerleştirilir.  
  
-   Tüm parametrelerin ve özellik değerlerini mutlak ve yerel ayar bağımsızdır.  
  
<a name="Required_Members_for_the_IValueProvider_Interface"></a>   
## <a name="required-members-for-itransformprovider"></a>Gerekli üyeleri ITransformProvider için  
 Aşağıdaki özellikleri ve yöntemleri uygulamak için gerekli olan <xref:System.Windows.Automation.Provider.ITransformProvider>.  
  
|Gerekli üyeleri|Üye türü|Notlar|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.ITransformProvider.CanMove%2A>|Özellik|Hiçbiri|  
|<xref:System.Windows.Automation.Provider.ITransformProvider.CanResize%2A>|Özellik|Hiçbiri|  
|<xref:System.Windows.Automation.Provider.ITransformProvider.CanRotate%2A>|Özellik|Hiçbiri|  
|<xref:System.Windows.Automation.Provider.ITransformProvider.Move%2A>|Yöntem|Hiçbiri|  
|<xref:System.Windows.Automation.Provider.ITransformProvider.Resize%2A>|Yöntem|Hiçbiri|  
|<xref:System.Windows.Automation.Provider.ITransformProvider.Rotate%2A>|Yöntem|Hiçbiri|  
  
 Bu denetim düzeni, ilişkili olay vardır.  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a>Özel Durumlar  
 Sağlayıcıları, aşağıdaki özel durumlar gerekir.  
  
|Özel Durum Türü|Koşul|  
|--------------------|---------------|  
|<xref:System.InvalidOperationException>|<xref:System.Windows.Automation.Provider.ITransformProvider.Move%2A><br /><br /> -Eğer <xref:System.Windows.Automation.TransformPatternIdentifiers.CanMoveProperty> false'tur.|  
|<xref:System.InvalidOperationException>|<xref:System.Windows.Automation.Provider.ITransformProvider.Resize%2A><br /><br /> -Eğer <xref:System.Windows.Automation.TransformPatternIdentifiers.CanResizeProperty> false'tur.|  
|<xref:System.InvalidOperationException>|<xref:System.Windows.Automation.Provider.ITransformProvider.Rotate%2A><br /><br /> -Eğer <xref:System.Windows.Automation.TransformPatternIdentifiers.CanRotateProperty> false'tur.|  
  
## <a name="see-also"></a>Ayrıca bkz.
- [UI Otomasyonu Denetim Desenlerine Genel Bakış](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)
- [UI Otomasyonu Sağlayıcıda Denetim Düzenleri Desteği](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)
- [İstemciler İçin UI Otomasyonu Denetim Düzenleri](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)
- [UI Otomasyon Ağacına Genel Bakış](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)
- [UI Otomasyonunda Önbelleğe Almayı Kullanma](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)
