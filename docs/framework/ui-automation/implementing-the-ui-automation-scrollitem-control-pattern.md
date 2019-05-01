---
title: UI Otomasyon ScrollItem Denetim Düzeni Uygulama
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, Scroll Item
- UI Automation, Scroll Item control pattern
- Scroll Item control pattern
ms.assetid: 903bab5c-80c1-44d7-bdc2-0a418893b987
ms.openlocfilehash: c0bb852fa6c117ae8eb2644a0be75f20367b2054
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61983313"
---
# <a name="implementing-the-ui-automation-scrollitem-control-pattern"></a>UI Otomasyon ScrollItem Denetim Düzeni Uygulama
> [!NOTE]
>  Bu belge yönetilen kullanmak isteyen .NET Framework için tasarlanan [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tanımlanan sınıflar <xref:System.Windows.Automation> ad alanı. En son bilgileri [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], bkz: [Windows Automation API: UI Otomasyonu](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Bu konu, yönergeleri ve uygulama kuralları tanıtır <xref:System.Windows.Automation.Provider.IScrollItemProvider>, özellikler, yöntemler ve olaylar hakkında bilgiler dahil olmak üzere. Ek başvurular bağlantılar konunun sonunda listelenmiştir.  
  
 <xref:System.Windows.Automation.ScrollItemPattern> Denetim düzeni uygulama kapsayıcılarının tek alt denetimler desteklemek için kullanılan <xref:System.Windows.Automation.Provider.IScrollProvider>. Bu denetim düzeni, bir iletişim kanalı arasındaki bir alt denetimin ve alt denetim görüntülemek için Görünüm penceresi içinde şu anda görünür içeriğe (veya bölge) kapsayıcı değiştirebilirsiniz emin olmak için kendi kapsayıcı görevi görür. Bu denetim düzeni uygulama denetimleri örnekleri için bkz: [denetim düzeni eşlemesi için UI Otomasyonu istemcileri](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md).  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a>Uygulama yönergeleri ve kuralları  
 Kaydırma öğesi denetim düzeni uygularken aşağıdaki yönergeler ve kuralları dikkat edin:  
  
- Bir pencere veya Tuval denetimi içinde bulunan öğeleri IScrollItemProvider arabirim uygulamak için gerekli değildir. Alternatif olarak, ancak bunlar için geçerli bir konum açığa çıkarmalıdır <xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>. Bunu kullanmak UI otomasyon istemci uygulaması sağlayacak <xref:System.Windows.Automation.ScrollPattern> denetim alt öğeyi görüntülemek için kapsayıcı üzerindeki deseni yöntemleri.  
  
<a name="Required_Members_for_IScrollItemProvider"></a>   
## <a name="required-members-for-iscrollitemprovider"></a>Gerekli üyeleri IScrollItemProvider için  
 Aşağıdaki yöntem IScrollProvider arabirim uygulamak için gereklidir.  
  
|Gerekli üyeleri|Üye türü|Notlar|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.IScrollItemProvider.ScrollIntoView%2A>|-Yöntemi|Yok.|  
  
 Bu denetim düzeni hiçbir ilişkili özellikleri veya olayları vardır.  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a>Özel Durumlar  
 Sağlayıcıları, aşağıdaki özel durumlar gerekir.  
  
|Özel Durum Türü|Koşul|  
|--------------------|---------------|  
|<xref:System.InvalidOperationException>|Bir öğe görünüme kaydırılan olamaz varsa:<br /><br /> -   <xref:System.Windows.Automation.ScrollItemPattern.ScrollIntoView%2A>|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [UI Otomasyonu Denetim Desenlerine Genel Bakış](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)
- [UI Otomasyonu Sağlayıcıda Denetim Düzenleri Desteği](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)
- [İstemciler İçin UI Otomasyonu Denetim Düzenleri](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)
- [UI Otomasyon Ağacına Genel Bakış](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)
- [UI Otomasyonunda Önbelleğe Almayı Kullanma](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)
