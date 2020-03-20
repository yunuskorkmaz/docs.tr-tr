---
title: UI Otomasyonu Kaydırma Denetim Düzenini Uygulama
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, Scroll control pattern
- control patterns, Scroll
- Scroll control pattern
ms.assetid: 73d64242-6cbb-424c-92dd-dc69530b7899
ms.openlocfilehash: 0420adaefb91f0c9f0d34d5bdf5863373a0b652b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79180159"
---
# <a name="implementing-the-ui-automation-scroll-control-pattern"></a>UI Otomasyonu Kaydırma Denetim Düzenini Uygulama
> [!NOTE]
> Bu dokümantasyon, ad alanında tanımlanan yönetilen [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] sınıfları kullanmak <xref:System.Windows.Automation> isteyen .NET Framework geliştiricileri için tasarlanmıştır. Hakkında en son [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]bilgi için [Bkz. Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).  
  
 Bu <xref:System.Windows.Automation.Provider.IScrollProvider>konu, olaylar ve özellikler hakkında bilgiler de dahil olmak üzere, uygulama yönergeleri ve kuralları sunar. Ek başvurulara bağlantılar konunun sonunda listelenir.  
  
 Denetim <xref:System.Windows.Automation.ScrollPattern> deseni, alt nesneler topluluğu için kaydırılabilir bir kapsayıcı görevi gören bir denetimi desteklemek için kullanılır. Denetim, kaydırma işlevini desteklemek için kaydırma çubukları kullanmak için gerekli değildir, ancak genellikle bunu yapar.  
  
 ![Kaydırma çubukları olmadan kaydırma denetimi.](./media/uia-scrollpattern-without-scrollbars.PNG "UIA_ScrollPattern_Without_Scrollbars")  
Kaydırma Çubukları Kullanmayan Kaydırma Denetimi Örneği  
  
 Bu denetimi uygulayan denetimörnekleri için, [UI Otomasyon İstemcileri için Denetim Deseni Eşleciliği'ne](control-pattern-mapping-for-ui-automation-clients.md)bakın.  
  
<a name="Implementation_Guidelines_and_Conventions"></a>
## <a name="implementation-guidelines-and-conventions"></a>Uygulama Yönergeleri ve Sözleşmeleri  
 Kaydırma denetim deseni uygulanırken aşağıdaki yönergeleri ve kuralları not edin:  
  
- Bu kontrolün çocukları <xref:System.Windows.Automation.Provider.IScrollItemProvider>uygulamalıdır.  
  
- Kapsayıcı denetiminin kaydırma çubukları denetim <xref:System.Windows.Automation.ScrollPattern> deseni desteklemez. Bunun yerine <xref:System.Windows.Automation.RangeValuePattern> kontrol modelini desteklemeleri gerekir.  
  
- Kaydırma yüzdelerle ölçüldüğünde, kaydırma mezuniyeti ile ilgili tüm değerler veya tutarlar 0 ile 100 arasında bir aralıkta normalleştirilmelidir.  
  
- <xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontallyScrollableProperty>ve <xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticallyScrollableProperty> <xref:System.Windows.Automation.AutomationElement.IsEnabledProperty>bağımsızdır.  
  
- <xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontallyScrollableProperty>  =  Daha `false` <xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontalViewSizeProperty> sonra % 100 olarak <xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontalScrollPercentProperty> ayarlanmalıdır <xref:System.Windows.Automation.ScrollPatternIdentifiers.NoScroll>ve . Aynı şekilde, <xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticallyScrollableProperty>  =  `false` <xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticalViewSizeProperty> eğer o zaman yüzde 100 olarak ayarlanmalıdır ve <xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticalScrollPercentProperty> <xref:System.Windows.Automation.ScrollPatternIdentifiers.NoScroll>ayarlanmalıdır. Bu, bir Kullanıcı Arabirimi Otomasyon istemcisinin, istemcinin <xref:System.Windows.Automation.ScrollPattern.SetScrollPercent%2A> kaydırmayla ilgilenmediği bir yön etkinleştirildiğinde bir yarış [koşulunu](https://support.microsoft.com/default.aspx?scid=kb;en-us;317723) önlerken yöntem içinde bu özellik değerlerini kullanmasına olanak tanır.  
  
- <xref:System.Windows.Automation.Provider.IScrollProvider.HorizontalScrollPercent%2A>yerele özgüdür. HorizontalScrollPercent = 100.0'ı ayarlamak, soldan sağa okuyan İngilizce gibi diller için denetimin kaydırma konumunu en sağdaki konumuna ayarlamalıdır. Alternatif olarak, arapça gibi sağdan sola okuyan diller için HorizontalScrollPercent = 100.0'ı ayarlamak kaydırma konumunu en soldaki konuma ayarlamalıdır.  
  
<a name="Required_Members_for_IScrollProvider"></a>
## <a name="required-members-for-iscrollprovider"></a>IScrollProvider için Gerekli Üyeler  
 Uygulamak için aşağıdaki özellikler ve <xref:System.Windows.Automation.Provider.IScrollProvider>yöntemler gereklidir.  
  
|Gerekli üye|Üye tipi|Notlar|  
|---------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.IScrollProvider.HorizontalScrollPercent%2A>|Özellik|None|  
|<xref:System.Windows.Automation.Provider.IScrollProvider.VerticalScrollPercent%2A>|Özellik|None|  
|<xref:System.Windows.Automation.Provider.IScrollProvider.HorizontalViewSize%2A>|Özellik|None|  
|<xref:System.Windows.Automation.Provider.IScrollProvider.VerticalViewSize%2A>|Özellik|None|  
|<xref:System.Windows.Automation.Provider.IScrollProvider.HorizontallyScrollable%2A>|Özellik|None|  
|<xref:System.Windows.Automation.Provider.IScrollProvider.VerticallyScrollable%2A>|Özellik|None|  
|<xref:System.Windows.Automation.Provider.IScrollProvider.Scroll%2A>|Yöntem|None|  
|<xref:System.Windows.Automation.Provider.IScrollProvider.SetScrollPercent%2A>|Yöntem|None|  
  
 Bu denetim deseni ilişkili olaylar vardır.  
  
<a name="Exceptions"></a>
## <a name="exceptions"></a>Özel durumlar  
 Sağlayıcılar aşağıdaki özel durumları atmalıdır.  
  
|Özel Durum Türü|Koşul|  
|--------------------|---------------|  
|<xref:System.ArgumentException>|<xref:System.Windows.Automation.Provider.IScrollProvider.Scroll%2A>bir denetim yalnızca yatay <xref:System.Windows.Automation.ScrollAmount.SmallIncrement> veya dikey kaydırma için değerleri destekliyorsa, ancak bir <xref:System.Windows.Automation.ScrollAmount.LargeIncrement> değer geçirilirse, bu özel durum atar.|  
|<xref:System.ArgumentException>|<xref:System.Windows.Automation.Provider.IScrollProvider.SetScrollPercent%2A>çifte dönüştürülemeyen bir değer geçirildiğinde bu özel durum atar.|  
|<xref:System.ArgumentOutOfRangeException>|<xref:System.Windows.Automation.Provider.IScrollProvider.SetScrollPercent%2A>100'den büyük veya 0'dan küçük bir değer geçtiğinde (eşdeğeri -1 <xref:System.Windows.Automation.ScrollPatternIdentifiers.NoScroll>hariç) bu özel durum atar.|  
|<xref:System.InvalidOperationException>|Her <xref:System.Windows.Automation.Provider.IScrollProvider.Scroll%2A> <xref:System.Windows.Automation.Provider.IScrollProvider.SetScrollPercent%2A> ikisi de ve desteklenmeyen bir yönde kaydırma girişimi yapıldığında bu özel durum atın.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [UI Otomasyonu Denetim Desenlerine Genel Bakış](ui-automation-control-patterns-overview.md)
- [UI Otomasyonu Sağlayıcıda Denetim Düzenleri Desteği](support-control-patterns-in-a-ui-automation-provider.md)
- [İstemciler İçin UI Otomasyonu Denetim Düzenleri](ui-automation-control-patterns-for-clients.md)
- [UI Otomasyon Ağacına Genel Bakış](ui-automation-tree-overview.md)
- [UI Otomasyonunda Önbelleğe Almayı Kullanma](use-caching-in-ui-automation.md)
