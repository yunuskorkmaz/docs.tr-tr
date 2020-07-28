---
title: UI Otomasyonu Kaydırma Denetim Düzenini Uygulama
description: UI otomasyonunda Scroll Control deseninin uygulanması için yönergeleri ve kuralları gözden geçirin. IScrollProvider arabirimi için gereken üyelere bakın.
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, Scroll control pattern
- control patterns, Scroll
- Scroll control pattern
ms.assetid: 73d64242-6cbb-424c-92dd-dc69530b7899
ms.openlocfilehash: 830d65286f27302dcad109384b8df187ed4af1a5
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87166992"
---
# <a name="implementing-the-ui-automation-scroll-control-pattern"></a>UI Otomasyonu Kaydırma Denetim Düzenini Uygulama
> [!NOTE]
> Bu belge, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ad alanında tanımlanan yönetilen sınıfları kullanmak isteyen .NET Framework geliştiricilere yöneliktir <xref:System.Windows.Automation> . Hakkında en son bilgiler için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] bkz. [WINDOWS Otomasyonu API: UI Otomasyonu](/windows/win32/winauto/entry-uiauto-win32).  
  
 Bu konu <xref:System.Windows.Automation.Provider.IScrollProvider> , olaylar ve özellikler hakkında bilgiler de dahil olmak üzere uygulama yönergelerini ve kurallarını tanıtır. Ek başvuruların bağlantıları konunun sonunda listelenmiştir.  
  
 <xref:System.Windows.Automation.ScrollPattern>Denetim stili, alt nesnelerin bir koleksiyonu için kaydırılabilir kapsayıcı olarak davranan bir denetimi desteklemek için kullanılır. Denetim, kayan işlevselliği desteklemek için, yaygın olarak olsa da, kaydırma çubuklarını kullanmak için gerekli değildir.  
  
 ![Kaydırma çubuğu olmadan kaydırma denetimi.](./media/uia-scrollpattern-without-scrollbars.PNG "UIA_ScrollPattern_Without_Scrollbars")  
Kaydırma çubuğu kullanmayan bir kaydırma denetimi örneği  
  
 Bu denetimi uygulayan denetimlerin örnekleri için bkz. [UI Otomasyonu istemcileri Için denetim model eşlemesi](control-pattern-mapping-for-ui-automation-clients.md).  
  
<a name="Implementation_Guidelines_and_Conventions"></a>
## <a name="implementation-guidelines-and-conventions"></a>Uygulama kılavuzları ve kuralları  
 Kaydırma denetim modelini uygularken, aşağıdaki kılavuz ve kurallara göz önünde aklınızda olmanız gerekir:  
  
- Bu denetimin alt öğelerinin uygulanması gerekir <xref:System.Windows.Automation.Provider.IScrollItemProvider> .  
  
- Bir kapsayıcı denetiminin kaydırma çubukları <xref:System.Windows.Automation.ScrollPattern> Denetim düzenlerini desteklemez. <xref:System.Windows.Automation.RangeValuePattern>Bunun yerine denetim modelini desteklemesi gerekir.  
  
- Kaydırma yüzde cinsinden ölçülerek, Scroll mezuniyet ile ilgili tüm değerler veya tutarlar 0 ile 100 arasında normalleştirilmelidir.  
  
- <xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontallyScrollableProperty>ve ' den <xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticallyScrollableProperty> bağımsızdır <xref:System.Windows.Automation.AutomationElement.IsEnabledProperty> .  
  
- <xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontallyScrollableProperty>  =  `false` Daha sonra <xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontalViewSizeProperty> %100 olarak ayarlanmalıdır ve <xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontalScrollPercentProperty> olarak ayarlanmalıdır <xref:System.Windows.Automation.ScrollPatternIdentifiers.NoScroll> . Benzer şekilde, <xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticallyScrollableProperty>  =  `false` <xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticalViewSizeProperty> yüzde 100 olarak ayarlanmalıdır ve <xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticalScrollPercentProperty> olarak ayarlanmalıdır <xref:System.Windows.Automation.ScrollPatternIdentifiers.NoScroll> . Bu, bir UI Otomasyonu istemcisinin bu özellik değerlerini yöntem içinde kullanmasına izin verir, çünkü <xref:System.Windows.Automation.ScrollPattern.SetScrollPercent%2A> istemcinin kaydırma ile ilgilenmediği bir yön etkinleştirildiğinde bir [yarış durumu](https://support.microsoft.com/default.aspx?scid=kb;en-us;317723) önlemez.  
  
- <xref:System.Windows.Automation.Provider.IScrollProvider.HorizontalScrollPercent%2A>yerel ayara özgüdür. HorizontalScrollPercent = 100,0 ayarı, denetimin kaydırma konumunu, Ingilizce gibi, soldan sağa doğru okunan diller için en sağdaki konumunun eşdeğerine ayarlamanız gerekir. Alternatif olarak, sağdan sola okunan Arapça gibi diller için, HorizontalScrollPercent = 100,0 ayarı, kaydırma konumunu en soldaki konuma ayarlamanız gerekir.  
  
<a name="Required_Members_for_IScrollProvider"></a>
## <a name="required-members-for-iscrollprovider"></a>IScrollProvider için gerekli Üyeler  
 Uygulamak için aşağıdaki özellikler ve Yöntemler gereklidir <xref:System.Windows.Automation.Provider.IScrollProvider> .  
  
|Gerekli üye|Üye türü|Notlar|  
|---------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.IScrollProvider.HorizontalScrollPercent%2A>|Özellik|Hiçbiri|  
|<xref:System.Windows.Automation.Provider.IScrollProvider.VerticalScrollPercent%2A>|Özellik|Hiçbiri|  
|<xref:System.Windows.Automation.Provider.IScrollProvider.HorizontalViewSize%2A>|Özellik|Hiçbiri|  
|<xref:System.Windows.Automation.Provider.IScrollProvider.VerticalViewSize%2A>|Özellik|Hiçbiri|  
|<xref:System.Windows.Automation.Provider.IScrollProvider.HorizontallyScrollable%2A>|Özellik|Hiçbiri|  
|<xref:System.Windows.Automation.Provider.IScrollProvider.VerticallyScrollable%2A>|Özellik|Hiçbiri|  
|<xref:System.Windows.Automation.Provider.IScrollProvider.Scroll%2A>|Yöntem|Hiçbiri|  
|<xref:System.Windows.Automation.Provider.IScrollProvider.SetScrollPercent%2A>|Yöntem|Hiçbiri|  
  
 Bu denetim deseninin ilişkili olayları yok.  
  
<a name="Exceptions"></a>
## <a name="exceptions"></a>Özel durumlar  
 Sağlayıcılar aşağıdaki özel durumları oluşturması gerekir.  
  
|Özel durum türü|Koşul|  
|--------------------|---------------|  
|<xref:System.ArgumentException>|<xref:System.Windows.Automation.Provider.IScrollProvider.Scroll%2A>bir denetim <xref:System.Windows.Automation.ScrollAmount.SmallIncrement> yalnızca yatay veya dikey kaydırma için değerleri destekliyorsa bu özel durumu oluşturur, ancak bir <xref:System.Windows.Automation.ScrollAmount.LargeIncrement> değer geçirilir.|  
|<xref:System.ArgumentException>|<xref:System.Windows.Automation.Provider.IScrollProvider.SetScrollPercent%2A>Double değerine dönüştürülemeyen bir değer geçirildiğinde bu özel durumu oluşturur.|  
|<xref:System.ArgumentOutOfRangeException>|<xref:System.Windows.Automation.Provider.IScrollProvider.SetScrollPercent%2A>100 'den büyük veya 0 ' dan küçük bir değer geçirildiğinde bu özel durumu oluşturur (ile eşdeğer olan-1 hariç <xref:System.Windows.Automation.ScrollPatternIdentifiers.NoScroll> ).|  
|<xref:System.InvalidOperationException>|Her ikisi de <xref:System.Windows.Automation.Provider.IScrollProvider.Scroll%2A> , <xref:System.Windows.Automation.Provider.IScrollProvider.SetScrollPercent%2A> Desteklenmeyen bir yönde kaydırmak için bir deneme yapıldığında bu özel durumu oluşturur.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [UI Otomasyon Denetim Düzenlerine Genel Bakış](ui-automation-control-patterns-overview.md)
- [UI Otomasyon Sağlayıcısında Denetim Düzenleri Desteği](support-control-patterns-in-a-ui-automation-provider.md)
- [İstemciler İçin UI Otomasyon Denetim Düzenleri](ui-automation-control-patterns-for-clients.md)
- [UI Otomasyon Ağacına Genel Bakış](ui-automation-tree-overview.md)
- [UI Otomasyonda Önbelleğe Almayı Kullanma](use-caching-in-ui-automation.md)
