---
title: UI Otomasyonu Değer Denetim Düzenini Uygulama
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, Value
- UI Automation, Value control pattern
- Value control pattern
ms.assetid: b0fcdd87-3add-4345-bca9-e891205e02ba
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: b9c748ccc695ae67306c293c10248c4f3f22c043
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="implementing-the-ui-automation-value-control-pattern"></a>UI Otomasyonu Değer Denetim Düzenini Uygulama
> [!NOTE]
>  Bu belge yönetilen kullanmak isteyen .NET Framework için tasarlanan [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tanımlanan sınıflar <xref:System.Windows.Automation> ad alanı. Hakkında en yeni bilgiler için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], bkz: [Windows Otomasyon API: UI Otomasyonu](http://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Bu konu kılavuzları ve uygulamak için kuralları tanıtır <xref:System.Windows.Automation.Provider.IValueProvider>, olaylar ve özellikler hakkında bilgiler dahil olmak üzere. Ek başvurular bağlantılar konunun sonunda listelenmiştir.  
  
 <xref:System.Windows.Automation.ValuePattern> Denetim düzeni aralığı kapsayıcı olmayan bir değer varsa ve, temsil bir dize olarak denetimleri desteklemek için kullanılır. Bu dize denetim ve ayarlarına bağlı olarak düzenlenebilir olabilir. Bu deseni uygulayan denetimleri örnekleri için bkz: [denetim düzeni eşleştirmesi UI Otomasyon istemcileri için](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md).  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a>Uygulama rehberi ve kuralları  
 Değer denetim düzenini uygulama, aşağıdaki yönergeleri ve kuralları dikkat edin:  
  
-   Gibi denetimler <xref:System.Windows.Automation.ControlType.ListItem> ve <xref:System.Windows.Automation.ControlType.TreeItem> desteklemelidir <xref:System.Windows.Automation.ValuePattern> öğelerden herhangi birini değerini düzenlenebilir ise, bağımsız olarak geçerli düzenleme moduna denetimi. Üst denetim de desteklemelidir <xref:System.Windows.Automation.ValuePattern> alt öğeleri düzenlenebilir ise.  
  
 ![Düzenlenebilir bir liste öğesi. ] (../../../docs/framework/ui-automation/media/uia-valuepattern-editable-listitem.PNG "UIA_ValuePattern_Editable_ListItem")  
Düzenlenebilir bir liste öğesi örneği  
  
-   Tek satırlı düzenleme denetimleri uygulayarak içeriklerini program erişimi destekleyen <xref:System.Windows.Automation.Provider.IValueProvider>. Ancak, çok satırlı düzenleme denetimlerinde uygulamayan <xref:System.Windows.Automation.Provider.IValueProvider>; bunun yerine uygulayarak içeriğine erişim sağlar <xref:System.Windows.Automation.Provider.ITextProvider>.  
  
-   Çok satırlı düzenleme denetimi metin içeriğini almak için Denetim uygulamalıdır <xref:System.Windows.Automation.Provider.ITextProvider>. Ancak, <xref:System.Windows.Automation.Provider.ITextProvider> bir denetimin değeri ayarını desteklemiyor.  
  
-   <xref:System.Windows.Automation.Provider.IValueProvider> bilgi veya alt dize değerleri biçimlendirme alma desteklemez. Uygulama <xref:System.Windows.Automation.Provider.ITextProvider> bu senaryolarda.  
  
-   <xref:System.Windows.Automation.Provider.IValueProvider> denetimleri tarafından gibi uygulanmalı **Renk Seçici** Seçim denetiminden [!INCLUDE[TLA#tla_word](../../../includes/tlasharptla-word-md.md)] (aşağıda Resimli), bir renk değeri (örneğin, "Sarı") ile eşdeğer bir iç arasındadizeeşlemedestekleyen[!INCLUDE[TLA#tla_rgb](../../../includes/tlasharptla-rgb-md.md)]yapısı.  
  
 ![Renk Seçici vurgulanan sarı ile. ] (../../../docs/framework/ui-automation/media/uia-valuepattern-colorpicker.png "UIA_ValuePattern_ColorPicker")  
Renk örneği dize eşleme örneği  
  
-   Bir denetim olmalıdır, <xref:System.Windows.Automation.AutomationElement.IsEnabledProperty> kümesine `true` ve kendi <xref:System.Windows.Automation.ValuePattern.IsReadOnlyProperty> kümesine `false` yapılan bir çağrı izin vermeden önce <xref:System.Windows.Automation.Provider.IValueProvider.SetValue%2A>.  
  
<a name="Required_Members_for_the_IValueProvider_Interface"></a>   
## <a name="required-members-for-ivalueprovider"></a>Gerekli üyeleri IValueProvider için  
 Aşağıdaki özellikleri ve yöntemleri uygulamak için gerekli olan <xref:System.Windows.Automation.Provider.IValueProvider>.  
  
|Gerekli üyeleri|Üye türü|Notlar|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.ValuePattern.IsReadOnlyProperty>|Özellik|Yok.|  
|<xref:System.Windows.Automation.ValuePattern.ValueProperty>|Özellik|Yok.|  
|<xref:System.Windows.Automation.ValuePattern.SetValue%2A>|Yöntem|Yok.|  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a>Özel Durumlar  
 Sağlayıcıları aşağıdaki özel durumlar oluşturma gerekir.  
  
|Özel durum türü|Koşul|  
|--------------------|---------------|  
|<xref:System.InvalidOperationException>|<xref:System.Windows.Automation.ValuePattern.SetValue%2A><br /><br /> -Yerel ayarlara özgü bilgiler denetim hatalı biçimlendirilmiş bir tarihi gibi hatalı bir biçimde geçirilir|  
|<xref:System.ArgumentException>|<xref:System.Windows.Automation.ValuePattern.SetValue%2A><br /><br /> -Yeni bir değer bir dizeden bir biçime dönüştürülemiyorsa denetimi tanır.|  
|<xref:System.Windows.Automation.ElementNotEnabledException>|<xref:System.Windows.Automation.ValuePattern.SetValue%2A><br /><br /> -Zaman girişimini etkin bir denetim işlemek için yapılır.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [UI Otomasyonu Denetim Desenlerine Genel Bakış](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)  
 [UI Otomasyonu Sağlayıcıda Denetim Düzenleri Desteği](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)  
 [İstemciler İçin UI Otomasyonu Denetim Düzenleri](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)  
 [TextPattern Ekle metin örneği](http://msdn.microsoft.com/library/67353f93-7ee2-42f2-ab76-5c078cf6ca16)  
 [UI Otomasyon Ağacına Genel Bakış](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)  
 [UI Otomasyonunda Önbelleğe Almayı Kullanma](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)
