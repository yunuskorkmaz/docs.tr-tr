---
title: UI Otomasyonu Kaydırma Denetim Düzenini Uygulama
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, Scroll control pattern
- control patterns, Scroll
- Scroll control pattern
ms.assetid: 73d64242-6cbb-424c-92dd-dc69530b7899
author: Xansky
ms.author: mhopkins
ms.openlocfilehash: 4d8d2c8135e8f24f62b83837b610292ae2b258ce
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54546644"
---
# <a name="implementing-the-ui-automation-scroll-control-pattern"></a>UI Otomasyonu Kaydırma Denetim Düzenini Uygulama
> [!NOTE]
>  Bu belge yönetilen kullanmak isteyen .NET Framework için tasarlanan [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tanımlanan sınıflar <xref:System.Windows.Automation> ad alanı. En son bilgileri [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], bkz: [Windows Automation API: UI Otomasyonu](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Bu konu, yönergeleri ve uygulama kuralları tanıtır <xref:System.Windows.Automation.Provider.IScrollProvider>, olayları ve özellikleri hakkında bilgi dahil olmak üzere. Ek başvurular bağlantılar konunun sonunda listelenmiştir.  
  
 <xref:System.Windows.Automation.ScrollPattern> Denetim düzeni, alt nesne koleksiyonu için kaydırılabilir bir kapsayıcı görevi gören bir denetimini desteklemek için kullanılır. Denetimin kaydırma işlevleri desteklemek için yaygın olarak yapmasına rağmen kaydırma çubukları kullanmak için gerekli değildir.  
  
 ![Kaydırma çubukları olmadan kaydırma denetim. ](../../../docs/framework/ui-automation/media/uia-scrollpattern-without-scrollbars.PNG "UIA_ScrollPattern_Without_Scrollbars")  
Kaydırma çubukları kullanmayan kayan denetimi örneği  
  
 Bu denetimi uygulamak denetimleri örnekleri için bkz: [denetim düzeni eşlemesi için UI Otomasyonu istemcileri](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md).  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a>Uygulama yönergeleri ve kuralları  
 Kaydırma denetim düzeni uygularken aşağıdaki yönergeler ve kuralları dikkat edin:  
  
-   Bu denetimin alt uygulamalıdır <xref:System.Windows.Automation.Provider.IScrollItemProvider>.  
  
-   Bir kapsayıcı denetimin kaydırma çubukları desteklemeyen <xref:System.Windows.Automation.ScrollPattern> denetim düzeni. Desteklemeleri gereken <xref:System.Windows.Automation.RangeValuePattern> deseni denetimi.  
  
-   Kaydırma yüzde olarak ölçülür, tüm değerleri veya tutarlar Mezuniyet kaydırmak için 0 ile 100 arası bir aralığa normalleştirilmiş ilgili.  
  
-   <xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontallyScrollableProperty> ve <xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticallyScrollableProperty> bağımsız <xref:System.Windows.Automation.AutomationElement.IsEnabledProperty>.  
  
-   Varsa <xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontallyScrollableProperty>  =  `false` ardından <xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontalViewSizeProperty> % 100'e ayarlanması gerekir ve <xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontalScrollPercentProperty> ayarlanmalıdır <xref:System.Windows.Automation.ScrollPatternIdentifiers.NoScroll>. Benzer şekilde, varsa <xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticallyScrollableProperty>  =  `false` ardından <xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticalViewSizeProperty> yüzde 100 olarak ayarlayın ve <xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticalScrollPercentProperty> ayarlanmalıdır <xref:System.Windows.Automation.ScrollPatternIdentifiers.NoScroll>. Bu özellik değerleri içinde kullanmak UI Otomasyonu istemci böylece <xref:System.Windows.Automation.ScrollPattern.SetScrollPercent%2A> önleme sırasında yöntemi bir [yarış durumu](https://support.microsoft.com/default.aspx?scid=kb;en-us;317723) yön istemci ilginizi değilse, kaydırma etkin hale gelir.  
  
-   <xref:System.Windows.Automation.Provider.IScrollProvider.HorizontalScrollPercent%2A> yerel ayara özgü olur. HorizontalScrollPercent ayarlama = 100.0 ayarlamanız gerekir denetimin kaydırma konumunu en sağdaki konumuna soldan sağa okuma İngilizce gibi diller için eşdeğeri. Alternatif olarak, sağ oku Arapça gibi diller için sola HorizontalScrollPercent ayarlama = 100.0 kaydırma konumu en soldaki konuma ayarlamanız gerekir.  
  
<a name="Required_Members_for_IScrollProvider"></a>   
## <a name="required-members-for-iscrollprovider"></a>Gerekli üyeleri IScrollProvider için  
 Aşağıdaki özellikleri ve yöntemleri uygulamak için gerekli olan <xref:System.Windows.Automation.Provider.IScrollProvider>.  
  
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
  
 Bu denetim düzeni, ilişkili olay vardır.  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a>Özel Durumlar  
 Sağlayıcıları, aşağıdaki özel durumlar gerekir.  
  
|Özel Durum Türü|Koşul|  
|--------------------|---------------|  
|<xref:System.ArgumentException>|<xref:System.Windows.Automation.Provider.IScrollProvider.Scroll%2A> bir denetim destekliyorsa, bu özel durum oluşturur <xref:System.Windows.Automation.ScrollAmount.SmallIncrement> yatay veya dikey kaydırma, değerleri yalnızca ancak <xref:System.Windows.Automation.ScrollAmount.LargeIncrement> değeri geçirilir.|  
|<xref:System.ArgumentException>|<xref:System.Windows.Automation.Provider.IScrollProvider.SetScrollPercent%2A> double'a dönüştürülemeyecek bir değer olarak geçirildiğinde, bu özel durum oluşturur.|  
|<xref:System.ArgumentOutOfRangeException>|<xref:System.Windows.Automation.Provider.IScrollProvider.SetScrollPercent%2A> bir değer 100'den büyük veya 0'dan geçirildiğinde, bu özel durum oluşturur (eşdeğerdir -1 dışındaki <xref:System.Windows.Automation.ScrollPatternIdentifiers.NoScroll>).|  
|<xref:System.InvalidOperationException>|Her ikisi de <xref:System.Windows.Automation.Provider.IScrollProvider.Scroll%2A> ve <xref:System.Windows.Automation.Provider.IScrollProvider.SetScrollPercent%2A> desteklenmeyen bir yönde kaydırmak için denemesi yapıldığında bu özel durum.|  
  
## <a name="see-also"></a>Ayrıca bkz.
- [UI Otomasyonu Denetim Desenlerine Genel Bakış](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)
- [UI Otomasyonu Sağlayıcıda Denetim Düzenleri Desteği](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)
- [İstemciler İçin UI Otomasyonu Denetim Düzenleri](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)
- [UI Otomasyon Ağacına Genel Bakış](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)
- [UI Otomasyonunda Önbelleğe Almayı Kullanma](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)
