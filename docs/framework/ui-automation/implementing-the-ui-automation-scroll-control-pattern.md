---
title: "UI Otomasyonu Kaydırma Denetim Düzenini Uygulama"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- UI Automation, Scroll control pattern
- control patterns, Scroll
- Scroll control pattern
ms.assetid: 73d64242-6cbb-424c-92dd-dc69530b7899
caps.latest.revision: "23"
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: b9f38bbe185013c498a7ecf98bbf915b35c2d791
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="implementing-the-ui-automation-scroll-control-pattern"></a>UI Otomasyonu Kaydırma Denetim Düzenini Uygulama
> [!NOTE]
>  Bu belge yönetilen kullanmak isteyen .NET Framework için tasarlanan [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tanımlanan sınıflar <xref:System.Windows.Automation> ad alanı. Hakkında en yeni bilgiler için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], bkz: [Windows Otomasyon API: UI Otomasyonu](http://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Bu konu kılavuzları ve uygulamak için kuralları tanıtır <xref:System.Windows.Automation.Provider.IScrollProvider>, olayları ve özellikleri hakkındaki bilgileri de dahil olmak üzere. Ek başvurular bağlantılar konunun sonunda listelenmiştir.  
  
 <xref:System.Windows.Automation.ScrollPattern> Denetim düzeni alt nesneler koleksiyonunu kaydırılabilir kapsayıcısı olarak davranan bir denetimini desteklemek için kullanılır. Denetim genellikle yapmasa da scrollbars kaydırma işlevselliği desteklemek üzere kullanmak için gerekli değildir.  
  
 ![Kaydırma çubukları olmadan kaydırma denetim. ] (../../../docs/framework/ui-automation/media/uia-scrollpattern-without-scrollbars.PNG "UIA_ScrollPattern_Without_Scrollbars")  
Kaydırma çubukları kullanmayan kaydırma denetimi örneği  
  
 Bu denetimi denetimleri örnekleri için bkz: [denetim düzeni eşleştirmesi UI Otomasyon istemcileri için](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md).  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a>Uygulama rehberi ve kuralları  
 Kaydırma denetim düzenini uygulama, aşağıdaki yönergeleri ve kuralları dikkat edin:  
  
-   Bu denetim alt uygulamalıdır <xref:System.Windows.Automation.Provider.IScrollItemProvider>.  
  
-   Bir kapsayıcı denetiminin scrollbars desteklemeyen <xref:System.Windows.Automation.ScrollPattern> denetim düzeni. Desteklemesi gerekir <xref:System.Windows.Automation.RangeValuePattern> düzeni yerine denetim.  
  
-   Kaydırma yüzde olarak ölçülür olduğunda tüm değerleri veya tutarlar Mezuniyet kaydırmak için 0 ile 100 arası bir aralığa normalleştirilmiş ilgili.  
  
-   <xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontallyScrollableProperty>ve <xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticallyScrollableProperty> bağımsız <xref:System.Windows.Automation.AutomationElement.IsEnabledProperty>.  
  
-   Varsa <xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontallyScrollableProperty>  =  `false` sonra <xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontalViewSizeProperty> % 100'e ayarlanması gerekir ve <xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontalScrollPercentProperty> ayarlanmalı <xref:System.Windows.Automation.ScrollPatternIdentifiers.NoScroll>. Benzer şekilde, varsa <xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticallyScrollableProperty>  =  `false` sonra <xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticalViewSizeProperty> yüzde 100 olarak ayarlamanız gerekir ve <xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticalScrollPercentProperty> ayarlanmalı <xref:System.Windows.Automation.ScrollPatternIdentifiers.NoScroll>. Bu özellik değerlerini içinde kullanmak UI otomasyon istemci böylece <xref:System.Windows.Automation.ScrollPattern.SetScrollPercent%2A> önleme sırasında yöntemi bir [durumunu koşulu](http://support.microsoft.com/default.aspx?scid=kb;en-us;317723) bir yön istemci ilginizi değilse, kaydırma etkin hale gelir.  
  
-   <xref:System.Windows.Automation.Provider.IScrollProvider.HorizontalScrollPercent%2A>yerel ayar özgüdür. HorizontalScrollPercent ayarı = 100.0 ayarlamanız gerekir denetimin kaydırma konumunu en sağdaki konumuna soldan sağa okuyun İngilizce gibi diller için eşdeğerine. Alternatif olarak, doğru okunan Arapça gibi diller için HorizontalScrollPercent ayarı sola = 100.0 soldaki konuma kaydırma konumunu ayarlamanız gerekir.  
  
<a name="Required_Members_for_IScrollProvider"></a>   
## <a name="required-members-for-iscrollprovider"></a>Gerekli üyeleri IScrollProvider için  
 Aşağıdaki özellikleri ve yöntemleri uygulamak için gerekli olan <xref:System.Windows.Automation.Provider.IScrollProvider>.  
  
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
  
 Bu denetim düzeni ilişkili olay vardır.  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a>Özel Durumlar  
 Sağlayıcıları aşağıdaki özel durumlar oluşturma gerekir.  
  
|Özel durum türü|Koşul|  
|--------------------|---------------|  
|<xref:System.ArgumentException>|<xref:System.Windows.Automation.Provider.IScrollProvider.Scroll%2A>bir denetim destekliyorsa, bu özel durum oluşturur <xref:System.Windows.Automation.ScrollAmount.SmallIncrement> yatay veya dikey kaydırma için özel olarak değerleri ancak <xref:System.Windows.Automation.ScrollAmount.LargeIncrement> değeri geçirilir.|  
|<xref:System.ArgumentException>|<xref:System.Windows.Automation.Provider.IScrollProvider.SetScrollPercent%2A>içinde bir double dönüştürülemeyecek bir değer geçirildiğinde bu özel durum oluşturur.|  
|<xref:System.ArgumentOutOfRangeException>|<xref:System.Windows.Automation.Provider.IScrollProvider.SetScrollPercent%2A>içinde bir değer 100'den büyük veya 0'dan geçirildiğinde bu özel durum oluşturur (dışındaki eşdeğerdir -1 <xref:System.Windows.Automation.ScrollPatternIdentifiers.NoScroll>).|  
|<xref:System.InvalidOperationException>|Her ikisi de <xref:System.Windows.Automation.Provider.IScrollProvider.Scroll%2A> ve <xref:System.Windows.Automation.Provider.IScrollProvider.SetScrollPercent%2A> desteklenmeyen bir yönde kaydırma girişiminde bulunulduğunda bu özel durum.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [UI Otomasyon denetim düzenlerine genel bakış](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)  
 [UI Otomasyon sağlayıcısında denetim düzenleri desteği](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)  
 [İstemciler için UI Otomasyon denetim düzenleri](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)  
 [UI Otomasyon ağacına genel bakış](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)  
 [UI otomasyonda önbelleğe almayı kullanma](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)
