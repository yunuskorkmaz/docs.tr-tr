---
title: UI Otomasyonu Değer Denetim Düzenini Uygulama
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, Value
- UI Automation, Value control pattern
- Value control pattern
ms.assetid: b0fcdd87-3add-4345-bca9-e891205e02ba
ms.openlocfilehash: d8b05238b55369fca3df76cf309f5cf742685b41
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64603314"
---
# <a name="implementing-the-ui-automation-value-control-pattern"></a>UI Otomasyonu Değer Denetim Düzenini Uygulama
> [!NOTE]
>  Bu belge yönetilen kullanmak isteyen .NET Framework için tasarlanan [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tanımlanan sınıflar <xref:System.Windows.Automation> ad alanı. En son bilgileri [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], bkz: [Windows Automation API: UI Otomasyonu](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Bu konu, yönergeleri ve uygulama kuralları tanıtır <xref:System.Windows.Automation.Provider.IValueProvider>, olayları ve özellikleri hakkında bilgi dahil olmak üzere. Ek başvurular bağlantılar konunun sonunda listelenmiştir.  
  
 <xref:System.Windows.Automation.ValuePattern> Denetim düzeni aralığını kapsayan olmayan bir değer olan ve bir dize olarak gösterilebileceği denetimler desteklemek için kullanılır. Bu dize, Denetim ve ayarlarına bağlı olarak düzenlenebilir olabilir. Bu tasarımın denetimleri örnekleri için bkz. [denetim düzeni eşlemesi için UI Otomasyonu istemcileri](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md).  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a>Uygulama yönergeleri ve kuralları  
 Değer denetim düzeni uygularken aşağıdaki yönergeler ve kuralları dikkat edin:  
  
- Gibi denetimler <xref:System.Windows.Automation.ControlType.ListItem> ve <xref:System.Windows.Automation.ControlType.TreeItem> desteklemelidir <xref:System.Windows.Automation.ValuePattern> öğelerden herhangi birinin değeri düzenlenebilir ise bağımsız olarak geçerli düzenleme modu denetimi. Üst denetimin ayrıca desteklemelidir <xref:System.Windows.Automation.ValuePattern> ise alt öğeleri düzenlenebilir.  
  
 ![Düzenlenebilir bir liste öğesi. ](../../../docs/framework/ui-automation/media/uia-valuepattern-editable-listitem.PNG "UIA_ValuePattern_Editable_ListItem")  
Düzenlenebilir bir liste öğesi örneği  
  
- Tek satırlı düzenleme denetimleri uygulayarak içeriklerini programlı erişim desteği <xref:System.Windows.Automation.Provider.IValueProvider>. Ancak, çok satırlı düzenleme denetimleri uygulamayın <xref:System.Windows.Automation.Provider.IValueProvider>; bunun yerine uygulayarak, içeriklerinin erişim sağlar <xref:System.Windows.Automation.Provider.ITextProvider>.  
  
- Çok satırlı düzenleme denetiminin metin içeriğini almak için Denetim uygulamalıdır <xref:System.Windows.Automation.Provider.ITextProvider>. Ancak, <xref:System.Windows.Automation.Provider.ITextProvider> bir denetimin değerini ayarlanmasını desteklemez.  
  
- <xref:System.Windows.Automation.Provider.IValueProvider> bilgi veya alt dize değerleri biçimlendirme almayı desteklemiyor. Uygulama <xref:System.Windows.Automation.Provider.ITextProvider> bu senaryolarda.  
  
- <xref:System.Windows.Automation.Provider.IValueProvider> gibi denetimleri tarafından uygulanan **Renk Seçici** Seçim denetiminden [!INCLUDE[TLA#tla_word](../../../includes/tlasharptla-word-md.md)] (aşağıda Resimli), bir renk değeri (örneğin, "Sarı") ile eşdeğer bir iç arasındakidizeeşlemeyidestekleyen[!INCLUDE[TLA#tla_rgb](../../../includes/tlasharptla-rgb-md.md)]yapısı.  
  
 ![Renk Seçici vurgulanan sarı ile. ](../../../docs/framework/ui-automation/media/uia-valuepattern-colorpicker.png "UIA_ValuePattern_ColorPicker")  
Renk örneği dize eşleme örneği  
  
- Bir denetim olmalıdır, <xref:System.Windows.Automation.AutomationElement.IsEnabledProperty> kümesine `true` ve kendi <xref:System.Windows.Automation.ValuePattern.IsReadOnlyProperty> kümesine `false` bir çağrısına izin vermeden önce <xref:System.Windows.Automation.Provider.IValueProvider.SetValue%2A>.  
  
<a name="Required_Members_for_the_IValueProvider_Interface"></a>   
## <a name="required-members-for-ivalueprovider"></a>Gerekli üyeleri IValueProvider için  
 Aşağıdaki özellikleri ve yöntemleri uygulamak için gerekli olan <xref:System.Windows.Automation.Provider.IValueProvider>.  
  
|Gerekli üyeleri|Üye türü|Notlar|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.ValuePattern.IsReadOnlyProperty>|Özellik|Yok.|  
|<xref:System.Windows.Automation.ValuePattern.ValueProperty>|Özellik|None|  
|<xref:System.Windows.Automation.ValuePattern.SetValue%2A>|Yöntem|None|  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a>Özel Durumlar  
 Sağlayıcıları, aşağıdaki özel durumlar gerekir.  
  
|Özel durum türü|Koşul|  
|--------------------|---------------|  
|<xref:System.InvalidOperationException>|<xref:System.Windows.Automation.ValuePattern.SetValue%2A><br /><br /> -Yerel ayara özgü bilgileri hatalı biçimlendirilmiş tarihi gibi yanlış bir biçimde denetiminde iletilmezse.|  
|<xref:System.ArgumentException>|<xref:System.Windows.Automation.ValuePattern.SetValue%2A><br /><br /> -Yeni bir değer bir dizeden bir biçimine dönüştürülemiyor. Eğer denetimin tanır.|  
|<xref:System.Windows.Automation.ElementNotEnabledException>|<xref:System.Windows.Automation.ValuePattern.SetValue%2A><br /><br /> -Girişimini etkin bir denetim işlemek için yapılır.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [UI Otomasyonu Denetim Desenlerine Genel Bakış](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)
- [UI Otomasyonu Sağlayıcıda Denetim Düzenleri Desteği](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)
- [İstemciler İçin UI Otomasyonu Denetim Düzenleri](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)
- [Metin örnek ValuePattern'ı Ekle](https://github.com/Microsoft/WPF-Samples/tree/master/Accessibility/InsertText)
- [UI Otomasyon Ağacına Genel Bakış](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)
- [UI Otomasyonunda Önbelleğe Almayı Kullanma](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)
