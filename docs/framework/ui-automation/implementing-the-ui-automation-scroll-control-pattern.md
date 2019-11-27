---
title: UI Otomasyonu Kaydırma Denetim Düzenini Uygulama
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, Scroll control pattern
- control patterns, Scroll
- Scroll control pattern
ms.assetid: 73d64242-6cbb-424c-92dd-dc69530b7899
ms.openlocfilehash: d146ba67f4fe3f5fda6196231f96f428f702086a
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74447162"
---
# <a name="implementing-the-ui-automation-scroll-control-pattern"></a>UI Otomasyonu Kaydırma Denetim Düzenini Uygulama
> [!NOTE]
> Bu belge, <xref:System.Windows.Automation> ad alanında tanımlanan yönetilen [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] sınıflarını kullanmak isteyen .NET Framework geliştiricilere yöneliktir. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]hakkında en son bilgiler için bkz. [Windows Otomasyonu API: UI Otomasyonu](/windows/win32/winauto/entry-uiauto-win32).  
  
 Bu konu, olaylar ve özellikler hakkında bilgiler de dahil olmak üzere <xref:System.Windows.Automation.Provider.IScrollProvider>uygulamak için kılavuz ve kuralları tanıtır. Ek başvuruların bağlantıları konunun sonunda listelenmiştir.  
  
 <xref:System.Windows.Automation.ScrollPattern> denetim stili, alt nesnelerin bir koleksiyonu için kaydırılabilir kapsayıcı olarak davranan bir denetimi desteklemek için kullanılır. Denetim, kayan işlevselliği desteklemek için, yaygın olarak olsa da, kaydırma çubuklarını kullanmak için gerekli değildir.  
  
 ![Kaydırma çubuğu olmadan kaydırma denetimi.](./media/uia-scrollpattern-without-scrollbars.PNG "UIA_ScrollPattern_Without_Scrollbars")  
Kaydırma çubuğu kullanmayan bir kaydırma denetimi örneği  
  
 Bu denetimi uygulayan denetimlerin örnekleri için bkz. [UI Otomasyonu istemcileri Için denetim model eşlemesi](control-pattern-mapping-for-ui-automation-clients.md).  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a>Uygulama kılavuzları ve kuralları  
 Kaydırma denetim modelini uygularken, aşağıdaki kılavuz ve kurallara göz önünde aklınızda olmanız gerekir:  
  
- Bu denetimin alt öğelerinin <xref:System.Windows.Automation.Provider.IScrollItemProvider>uygulaması gerekir.  
  
- Bir kapsayıcı denetiminin kaydırma çubukları <xref:System.Windows.Automation.ScrollPattern> denetim modelini desteklemez. Bunun yerine <xref:System.Windows.Automation.RangeValuePattern> denetim modelini desteklemesi gerekir.  
  
- Kaydırma yüzde cinsinden ölçülerek, Scroll mezuniyet ile ilgili tüm değerler veya tutarlar 0 ile 100 arasında normalleştirilmelidir.  
  
- <xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontallyScrollableProperty> ve <xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticallyScrollableProperty> <xref:System.Windows.Automation.AutomationElement.IsEnabledProperty>bağımsızdır.  
  
- <xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontallyScrollableProperty> = `false` <xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontalViewSizeProperty> %100 olarak ayarlanmalıdır ve <xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontalScrollPercentProperty> <xref:System.Windows.Automation.ScrollPatternIdentifiers.NoScroll>olarak ayarlanmalıdır. Benzer şekilde, <xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticallyScrollableProperty> = `false` <xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticalViewSizeProperty> yüzde 100 olarak ayarlanmalıdır ve <xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticalScrollPercentProperty> <xref:System.Windows.Automation.ScrollPatternIdentifiers.NoScroll>olarak ayarlanmalıdır. Bu, bir UI Otomasyon istemcisinin <xref:System.Windows.Automation.ScrollPattern.SetScrollPercent%2A> yöntemi içinde bu özellik değerlerini kullanmasına izin verir, çünkü istemcinin kaydırma ile ilgilenmediği bir yön etkin hale gelirse bir [yarış durumu](https://support.microsoft.com/default.aspx?scid=kb;en-us;317723) önlemez.  
  
- <xref:System.Windows.Automation.Provider.IScrollProvider.HorizontalScrollPercent%2A>, yerel ayara özgüdür. HorizontalScrollPercent = 100,0 ayarı, denetimin kaydırma konumunu, Ingilizce gibi, soldan sağa doğru okunan diller için en sağdaki konumunun eşdeğerine ayarlamanız gerekir. Alternatif olarak, sağdan sola okunan Arapça gibi diller için, HorizontalScrollPercent = 100,0 ayarı, kaydırma konumunu en soldaki konuma ayarlamanız gerekir.  
  
<a name="Required_Members_for_IScrollProvider"></a>   
## <a name="required-members-for-iscrollprovider"></a>IScrollProvider için gerekli Üyeler  
 <xref:System.Windows.Automation.Provider.IScrollProvider>uygulamak için aşağıdaki özellikler ve Yöntemler gereklidir.  
  
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
## <a name="exceptions"></a>Özel durumlar  
 Sağlayıcılar aşağıdaki özel durumları oluşturması gerekir.  
  
|Özel Durum Türü|Koşul|  
|--------------------|---------------|  
|<xref:System.ArgumentException>|<xref:System.Windows.Automation.Provider.IScrollProvider.Scroll%2A>, bir denetim yalnızca yatay veya dikey kaydırma için <xref:System.Windows.Automation.ScrollAmount.SmallIncrement> değerlerini destekliyorsa, ancak bir <xref:System.Windows.Automation.ScrollAmount.LargeIncrement> değeri geçirildiğinde bu özel durumu oluşturur.|  
|<xref:System.ArgumentException>|<xref:System.Windows.Automation.Provider.IScrollProvider.SetScrollPercent%2A>, Double değerine dönüştürülemeyen bir değer geçirildiğinde bu özel durumu oluşturur.|  
|<xref:System.ArgumentOutOfRangeException>|<xref:System.Windows.Automation.Provider.IScrollProvider.SetScrollPercent%2A>, 100 ' den büyük veya 0 ' dan küçük bir değer geçirildiğinde bu özel durumu (<xref:System.Windows.Automation.ScrollPatternIdentifiers.NoScroll>ile eşdeğer olan 1 dışında) oluşturur.|  
|<xref:System.InvalidOperationException>|Hem <xref:System.Windows.Automation.Provider.IScrollProvider.Scroll%2A> hem de <xref:System.Windows.Automation.Provider.IScrollProvider.SetScrollPercent%2A>, desteklenmeyen bir yönde kaydırmak için bir deneme yapıldığında bu özel durumu oluşturur.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [UI Otomasyonu Denetim Desenlerine Genel Bakış](ui-automation-control-patterns-overview.md)
- [UI Otomasyonu Sağlayıcıda Denetim Düzenleri Desteği](support-control-patterns-in-a-ui-automation-provider.md)
- [İstemciler İçin UI Otomasyonu Denetim Düzenleri](ui-automation-control-patterns-for-clients.md)
- [UI Otomasyon Ağacına Genel Bakış](ui-automation-tree-overview.md)
- [UI Otomasyonunda Önbelleğe Almayı Kullanma](use-caching-in-ui-automation.md)
