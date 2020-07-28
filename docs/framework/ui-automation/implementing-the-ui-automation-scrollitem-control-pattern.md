---
title: UI Otomasyon ScrollItem Denetim Düzeni Uygulama
description: UI otomasyonunda Scrollıdıtem denetim deseninin uygulanması için yönergeleri ve kuralları gözden geçirin. Icrollitemprovider arabirimi için gereken üyelere bakın.
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, Scroll Item
- UI Automation, Scroll Item control pattern
- Scroll Item control pattern
ms.assetid: 903bab5c-80c1-44d7-bdc2-0a418893b987
ms.openlocfilehash: a548eb25280d9a8feddc4633a1ba3e7dc022af36
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87163573"
---
# <a name="implementing-the-ui-automation-scrollitem-control-pattern"></a>UI Otomasyon ScrollItem Denetim Düzeni Uygulama
> [!NOTE]
> Bu belge, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ad alanında tanımlanan yönetilen sınıfları kullanmak isteyen .NET Framework geliştiricilere yöneliktir <xref:System.Windows.Automation> . Hakkında en son bilgiler için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] bkz. [WINDOWS Otomasyonu API: UI Otomasyonu](/windows/win32/winauto/entry-uiauto-win32).  
  
 Bu konuda <xref:System.Windows.Automation.Provider.IScrollItemProvider> Özellikler, Yöntemler ve olaylar hakkında bilgiler de dahil olmak üzere uygulama yönergeleri ve kuralları tanıtılmaktadır. Ek başvuruların bağlantıları konunun sonunda listelenmiştir.  
  
 <xref:System.Windows.Automation.ScrollItemPattern>Denetim stili, uygulayan kapsayıcıların tek tek alt denetimlerini desteklemek için kullanılır <xref:System.Windows.Automation.Provider.IScrollProvider> . Bu denetim stili, kapsayıcının kendi görünüm içindeki görünür içeriği (veya bölgeyi) alt denetimi görüntüleyecek şekilde değiştirebildiğinden emin olmak için bir alt denetim ve kapsayıcısı arasında bir iletişim kanalı işlevi görür. Bu denetim modelini uygulayan denetimlerin örnekleri için bkz. [UI Otomasyonu istemcileri Için denetim model eşlemesi](control-pattern-mapping-for-ui-automation-clients.md).  
  
<a name="Implementation_Guidelines_and_Conventions"></a>
## <a name="implementation-guidelines-and-conventions"></a>Uygulama kılavuzları ve kuralları  
 Kaydırma öğesi denetim modelini uygularken aşağıdaki kılavuz ve kurallara göz önünde yer verilmiştir:  
  
- Bir pencere veya tuval denetiminde bulunan öğelerin ıcrollitemprovider arabirimini uygulaması için gerekli değildir. Ancak alternatif olarak, için geçerli bir konum kullanıma sunmaları gerekir <xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty> . Bu, bir UI Otomasyonu istemci uygulamasının <xref:System.Windows.Automation.ScrollPattern> alt öğeyi göstermek için kapsayıcıda denetim deseninin yöntemlerini kullanmasına izin verir.  
  
<a name="Required_Members_for_IScrollItemProvider"></a>
## <a name="required-members-for-iscrollitemprovider"></a>Icrollitemprovider için gerekli Üyeler  
 IScrollProvider arabirimini uygulamak için aşağıdaki yöntem gereklidir.  
  
|Gerekli Üyeler|Üye türü|Notlar|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.IScrollItemProvider.ScrollIntoView%2A>|-Yöntemi|Hiçbiri|  
  
 Bu denetim deseninin ilişkili özellikleri veya olayları yok.  
  
<a name="Exceptions"></a>
## <a name="exceptions"></a>Özel durumlar  
 Sağlayıcılar aşağıdaki özel durumları oluşturması gerekir.  
  
|Özel durum türü|Koşul|  
|--------------------|---------------|  
|<xref:System.InvalidOperationException>|Bir öğe görünüme kaydırılayoksa:<br /><br /> -   <xref:System.Windows.Automation.ScrollItemPattern.ScrollIntoView%2A>|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [UI Otomasyon Denetim Düzenlerine Genel Bakış](ui-automation-control-patterns-overview.md)
- [UI Otomasyon Sağlayıcısında Denetim Düzenleri Desteği](support-control-patterns-in-a-ui-automation-provider.md)
- [İstemciler İçin UI Otomasyon Denetim Düzenleri](ui-automation-control-patterns-for-clients.md)
- [UI Otomasyon Ağacına Genel Bakış](ui-automation-tree-overview.md)
- [UI Otomasyonda Önbelleğe Almayı Kullanma](use-caching-in-ui-automation.md)
