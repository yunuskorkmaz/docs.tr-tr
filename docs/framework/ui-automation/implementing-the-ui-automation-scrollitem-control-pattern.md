---
title: UI Otomasyon ScrollItem Denetim Düzeni Uygulama
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, Scroll Item
- UI Automation, Scroll Item control pattern
- Scroll Item control pattern
ms.assetid: 903bab5c-80c1-44d7-bdc2-0a418893b987
ms.openlocfilehash: 4883184d75a21efbc08947008baddf31346d7951
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69935752"
---
# <a name="implementing-the-ui-automation-scrollitem-control-pattern"></a>UI Otomasyon ScrollItem Denetim Düzeni Uygulama
> [!NOTE]
> Bu belge, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] <xref:System.Windows.Automation> ad alanında tanımlanan yönetilen sınıfları kullanmak isteyen .NET Framework geliştiricilere yöneliktir. Hakkında [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]en son bilgiler için bkz [. Windows Otomasyonu API 'si: UI Otomasyonu](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Bu konuda özellikler, Yöntemler ve olaylar hakkında bilgiler <xref:System.Windows.Automation.Provider.IScrollItemProvider>de dahil olmak üzere uygulama yönergeleri ve kuralları tanıtılmaktadır. Ek başvuruların bağlantıları konunun sonunda listelenmiştir.  
  
 Denetim stili, uygulayan <xref:System.Windows.Automation.Provider.IScrollProvider>kapsayıcıların tek tek alt denetimlerini desteklemek için kullanılır. <xref:System.Windows.Automation.ScrollItemPattern> Bu denetim stili, kapsayıcının kendi görünüm içindeki görünür içeriği (veya bölgeyi) alt denetimi görüntüleyecek şekilde değiştirebildiğinden emin olmak için bir alt denetim ve kapsayıcısı arasında bir iletişim kanalı işlevi görür. Bu denetim modelini uygulayan denetimlerin örnekleri için bkz. [UI Otomasyonu istemcileri Için denetim model eşlemesi](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md).  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a>Uygulama kılavuzları ve kuralları  
 Kaydırma öğesi denetim modelini uygularken aşağıdaki kılavuz ve kurallara göz önünde yer verilmiştir:  
  
- Bir pencere veya tuval denetiminde bulunan öğelerin ıcrollitemprovider arabirimini uygulaması için gerekli değildir. Ancak alternatif olarak, için <xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>geçerli bir konum kullanıma sunmaları gerekir. Bu, bir UI Otomasyonu istemci uygulamasının alt öğeyi göstermek için <xref:System.Windows.Automation.ScrollPattern> kapsayıcıda denetim deseninin yöntemlerini kullanmasına izin verir.  
  
<a name="Required_Members_for_IScrollItemProvider"></a>   
## <a name="required-members-for-iscrollitemprovider"></a>Icrollitemprovider için gerekli Üyeler  
 IScrollProvider arabirimini uygulamak için aşağıdaki yöntem gereklidir.  
  
|Gerekli Üyeler|Üye türü|Notlar|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.IScrollItemProvider.ScrollIntoView%2A>|-Yöntemi|Yok.|  
  
 Bu denetim deseninin ilişkili özellikleri veya olayları yok.  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a>Özel Durumlar  
 Sağlayıcılar aşağıdaki özel durumları oluşturması gerekir.  
  
|Özel Durum Türü|Koşul|  
|--------------------|---------------|  
|<xref:System.InvalidOperationException>|Bir öğe görünüme kaydırılayoksa:<br /><br /> -   <xref:System.Windows.Automation.ScrollItemPattern.ScrollIntoView%2A>|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [UI Otomasyonu Denetim Desenlerine Genel Bakış](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)
- [UI Otomasyonu Sağlayıcıda Denetim Düzenleri Desteği](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)
- [İstemciler İçin UI Otomasyonu Denetim Düzenleri](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)
- [UI Otomasyon Ağacına Genel Bakış](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)
- [UI Otomasyonunda Önbelleğe Almayı Kullanma](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)
