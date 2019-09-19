---
title: UI Otomasyonu Kaydırma Denetim Düzenini Uygulama
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, Scroll control pattern
- control patterns, Scroll
- Scroll control pattern
ms.assetid: 73d64242-6cbb-424c-92dd-dc69530b7899
ms.openlocfilehash: b8193ed8c7b5fab934d83eb31f5b562136a290ec
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71043311"
---
# <a name="implementing-the-ui-automation-scroll-control-pattern"></a>UI Otomasyonu Kaydırma Denetim Düzenini Uygulama
> [!NOTE]
> Bu belge, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] <xref:System.Windows.Automation> ad alanında tanımlanan yönetilen sınıfları kullanmak isteyen .NET Framework geliştiricilere yöneliktir. Hakkında [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]en son bilgiler için bkz [. Windows Otomasyonu API 'si: UI Otomasyonu](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Bu konu, olaylar ve özellikler hakkında bilgiler <xref:System.Windows.Automation.Provider.IScrollProvider>de dahil olmak üzere uygulama yönergelerini ve kurallarını tanıtır. Ek başvuruların bağlantıları konunun sonunda listelenmiştir.  
  
 <xref:System.Windows.Automation.ScrollPattern> Denetim stili, alt nesnelerin bir koleksiyonu için kaydırılabilir kapsayıcı olarak davranan bir denetimi desteklemek için kullanılır. Denetim, kayan işlevselliği desteklemek için, yaygın olarak olsa da, kaydırma çubuklarını kullanmak için gerekli değildir.  
  
 Kaydırma ![çubuğu olmadan kaydırma denetimi.](./media/uia-scrollpattern-without-scrollbars.PNG "UIA_ScrollPattern_Without_Scrollbars")  
Kaydırma çubuğu kullanmayan bir kaydırma denetimi örneği  
  
 Bu denetimi uygulayan denetimlerin örnekleri için bkz. [UI Otomasyonu istemcileri Için denetim model eşlemesi](control-pattern-mapping-for-ui-automation-clients.md).  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a>Uygulama kılavuzları ve kuralları  
 Kaydırma denetim modelini uygularken, aşağıdaki kılavuz ve kurallara göz önünde aklınızda olmanız gerekir:  
  
- Bu denetimin alt öğelerinin uygulanması <xref:System.Windows.Automation.Provider.IScrollItemProvider>gerekir.  
  
- Bir kapsayıcı denetiminin kaydırma çubukları <xref:System.Windows.Automation.ScrollPattern> denetim düzenlerini desteklemez. Bunun yerine <xref:System.Windows.Automation.RangeValuePattern> denetim modelini desteklemesi gerekir.  
  
- Kaydırma yüzde cinsinden ölçülerek, Scroll mezuniyet ile ilgili tüm değerler veya tutarlar 0 ile 100 arasında normalleştirilmelidir.  
  
- <xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontallyScrollableProperty>ve <xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticallyScrollableProperty> ' den bağımsızdır <xref:System.Windows.Automation.AutomationElement.IsEnabledProperty>.  
  
- <xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontallyScrollableProperty> Dahasonra<xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontalViewSizeProperty> % 100 olarak ayarlanmalıdır ve<xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontalScrollPercentProperty> olarak ayarlanmalıdır<xref:System.Windows.Automation.ScrollPatternIdentifiers.NoScroll>.  =  `false` Benzer şekilde, <xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticallyScrollableProperty>  =  yüzde100`false` olarak ayarlanmalıdır ve<xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticalScrollPercentProperty> olarak<xref:System.Windows.Automation.ScrollPatternIdentifiers.NoScroll>ayarlanmalıdır. <xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticalViewSizeProperty> Bu, bir UI Otomasyonu istemcisinin bu özellik değerlerini <xref:System.Windows.Automation.ScrollPattern.SetScrollPercent%2A> yöntem içinde kullanmasına izin verir, çünkü istemcinin kaydırma ile ilgilenmediği bir yön etkinleştirildiğinde bir [yarış durumu](https://support.microsoft.com/default.aspx?scid=kb;en-us;317723) önlemez.  
  
- <xref:System.Windows.Automation.Provider.IScrollProvider.HorizontalScrollPercent%2A>yerel ayara özgüdür. HorizontalScrollPercent = 100,0 ayarı, denetimin kaydırma konumunu, Ingilizce gibi, soldan sağa doğru okunan diller için en sağdaki konumunun eşdeğerine ayarlamanız gerekir. Alternatif olarak, sağdan sola okunan Arapça gibi diller için, HorizontalScrollPercent = 100,0 ayarı, kaydırma konumunu en soldaki konuma ayarlamanız gerekir.  
  
<a name="Required_Members_for_IScrollProvider"></a>   
## <a name="required-members-for-iscrollprovider"></a>IScrollProvider için gerekli Üyeler  
 Uygulamak <xref:System.Windows.Automation.Provider.IScrollProvider>için aşağıdaki özellikler ve Yöntemler gereklidir.  
  
|Gerekli üye|Üye türü|Notlar|  
|---------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.IScrollProvider.HorizontalScrollPercent%2A>|Özellik|Yok.|  
|<xref:System.Windows.Automation.Provider.IScrollProvider.VerticalScrollPercent%2A>|Özellik|Yok.|  
|<xref:System.Windows.Automation.Provider.IScrollProvider.HorizontalViewSize%2A>|Özellik|Yok.|  
|<xref:System.Windows.Automation.Provider.IScrollProvider.VerticalViewSize%2A>|Özellik|Yok.|  
|<xref:System.Windows.Automation.Provider.IScrollProvider.HorizontallyScrollable%2A>|Özellik|Yok.|  
|<xref:System.Windows.Automation.Provider.IScrollProvider.VerticallyScrollable%2A>|Özellik|Yok.|  
|<xref:System.Windows.Automation.Provider.IScrollProvider.Scroll%2A>|Yöntem|Yok.|  
|<xref:System.Windows.Automation.Provider.IScrollProvider.SetScrollPercent%2A>|Yöntem|Yok.|  
  
 Bu denetim deseninin ilişkili olayları yok.  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a>Özel Durumlar  
 Sağlayıcılar aşağıdaki özel durumları oluşturması gerekir.  
  
|Özel Durum Türü|Koşul|  
|--------------------|---------------|  
|<xref:System.ArgumentException>|<xref:System.Windows.Automation.Provider.IScrollProvider.Scroll%2A>bir denetim yalnızca yatay veya dikey kaydırma <xref:System.Windows.Automation.ScrollAmount.SmallIncrement> için değerleri destekliyorsa bu özel durumu oluşturur, ancak bir <xref:System.Windows.Automation.ScrollAmount.LargeIncrement> değer geçirilir.|  
|<xref:System.ArgumentException>|<xref:System.Windows.Automation.Provider.IScrollProvider.SetScrollPercent%2A>Double değerine dönüştürülemeyen bir değer geçirildiğinde bu özel durumu oluşturur.|  
|<xref:System.ArgumentOutOfRangeException>|<xref:System.Windows.Automation.Provider.IScrollProvider.SetScrollPercent%2A>100 'den büyük veya 0 ' dan küçük bir değer geçirildiğinde bu özel durumu oluşturur (ile eşdeğer <xref:System.Windows.Automation.ScrollPatternIdentifiers.NoScroll>olan-1 hariç).|  
|<xref:System.InvalidOperationException>|Her <xref:System.Windows.Automation.Provider.IScrollProvider.Scroll%2A> ikisi <xref:System.Windows.Automation.Provider.IScrollProvider.SetScrollPercent%2A> de, desteklenmeyen bir yönde kaydırmak için bir deneme yapıldığında bu özel durumu oluşturur.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [UI Otomasyonu Denetim Desenlerine Genel Bakış](ui-automation-control-patterns-overview.md)
- [UI Otomasyonu Sağlayıcıda Denetim Düzenleri Desteği](support-control-patterns-in-a-ui-automation-provider.md)
- [İstemciler İçin UI Otomasyonu Denetim Düzenleri](ui-automation-control-patterns-for-clients.md)
- [UI Otomasyon Ağacına Genel Bakış](ui-automation-tree-overview.md)
- [UI Otomasyonunda Önbelleğe Almayı Kullanma](use-caching-in-ui-automation.md)
