---
title: UI Otomasyonu Değer Denetim Düzenini Uygulama
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, Value
- UI Automation, Value control pattern
- Value control pattern
ms.assetid: b0fcdd87-3add-4345-bca9-e891205e02ba
ms.openlocfilehash: eb77f26bbe3546a3f90804c3648f8547fb6abad0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79180087"
---
# <a name="implementing-the-ui-automation-value-control-pattern"></a>UI Otomasyonu Değer Denetim Düzenini Uygulama
> [!NOTE]
> Bu dokümantasyon, ad alanında tanımlanan yönetilen [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] sınıfları kullanmak <xref:System.Windows.Automation> isteyen .NET Framework geliştiricileri için tasarlanmıştır. Hakkında en son [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]bilgi için [Bkz. Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).  
  
 Bu <xref:System.Windows.Automation.Provider.IValueProvider>konu, olaylar ve özellikler hakkında bilgi de dahil olmak üzere, uygulama yönergeleri ve kuralları tanıtır. Ek başvurulara bağlantılar konunun sonunda listelenir.  
  
 Denetim <xref:System.Windows.Automation.ValuePattern> deseni, bir aralığı kapsamayan ve dize olarak temsil edilebilen içsel bir değere sahip denetimleri desteklemek için kullanılır. Bu dize, denetime ve ayarlarına bağlı olarak değiştirilebilir. Bu deseni uygulayan denetim örnekleri için, [UI Otomasyon İstemcileri için Denetim Deseni Eşleciliği'ne](control-pattern-mapping-for-ui-automation-clients.md)bakın.  
  
<a name="Implementation_Guidelines_and_Conventions"></a>
## <a name="implementation-guidelines-and-conventions"></a>Uygulama Yönergeleri ve Sözleşmeleri  
 Değer denetimi modelini uygularken aşağıdaki yönergeleri ve kuralları not edin:  
  
- Denetimin <xref:System.Windows.Automation.ControlType.ListItem> geçerli <xref:System.Windows.Automation.ControlType.TreeItem> editmodune bakılmaksızın, öğelerden herhangi birinin değeri kullanılabilirse, bu tür denetimler desteklenmelidir. <xref:System.Windows.Automation.ValuePattern> Alt öğeler değiştirilebilirse üst denetim de desteklenmelidir. <xref:System.Windows.Automation.ValuePattern>  
  
 ![Değiştirilebilir liste öğesi.](./media/uia-valuepattern-editable-listitem.PNG "UIA_ValuePattern_Editable_ListItem")  
Kullanılabilir Liste Öğesi Örneği  
  
- Tek satırlı düzenleme, uygulayarak <xref:System.Windows.Automation.Provider.IValueProvider>içeriklerine programlı erişimi destekler. Ancak, çok satırlı düzen denetimleri uygulamaz; <xref:System.Windows.Automation.Provider.IValueProvider> bunun yerine uygulayarak <xref:System.Windows.Automation.Provider.ITextProvider>içeriklerine erişim sağlarlar.  
  
- Çok satırlı bir düzen denetiminin metin içeriğini almak için <xref:System.Windows.Automation.Provider.ITextProvider>denetimin uygulanması gerekir. Ancak, <xref:System.Windows.Automation.Provider.ITextProvider> denetimin değerini ayarlamayı desteklemez.  
  
- <xref:System.Windows.Automation.Provider.IValueProvider>biçimlendirme bilgileri veya alt dize değerlerini alma desteklemez. Bu <xref:System.Windows.Automation.Provider.ITextProvider> senaryolarda uygulayın.  
  
- <xref:System.Windows.Automation.Provider.IValueProvider>bir renk değeri (örneğin, "sarı") ve eşdeğer bir iç RGB yapısı arasındaki dize eşlemi destekleyen Microsoft Word'den (aşağıda gösterildiği gibi) **Color Picker** seçim denetimi gibi denetimler tarafından uygulanmalıdır.  
  
 ![Sarı vurgulanmış renk seçici.](./media/uia-valuepattern-colorpicker.png "UIA_ValuePattern_ColorPicker")  
Renk Swatch String Eşleme Örneği  
  
- Bir denetim için <xref:System.Windows.Automation.AutomationElement.IsEnabledProperty> bir `true` çağrı <xref:System.Windows.Automation.ValuePattern.IsReadOnlyProperty> izin `false` vermeden önce onun <xref:System.Windows.Automation.Provider.IValueProvider.SetValue%2A>ayarlanmış ve onun ayarlamak olmalıdır.  
  
<a name="Required_Members_for_the_IValueProvider_Interface"></a>
## <a name="required-members-for-ivalueprovider"></a>IValueProvider için Gerekli Üyeler  
 Uygulamak için aşağıdaki özellikler ve <xref:System.Windows.Automation.Provider.IValueProvider>yöntemler gereklidir.  
  
|Gerekli üyeler|Üye tipi|Notlar|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.ValuePattern.IsReadOnlyProperty>|Özellik|None|  
|<xref:System.Windows.Automation.ValuePattern.ValueProperty>|Özellik|None|  
|<xref:System.Windows.Automation.ValuePattern.SetValue%2A>|Yöntem|None|  
  
<a name="Exceptions"></a>
## <a name="exceptions"></a>Özel durumlar  
 Sağlayıcılar aşağıdaki özel durumları atmalıdır.  
  
|Özel durum türü|Koşul|  
|--------------------|---------------|  
|<xref:System.InvalidOperationException>|<xref:System.Windows.Automation.ValuePattern.SetValue%2A><br /><br /> - Yerel bilgilere özgü bilgiler yanlış biçimlendirilmiş tarih gibi yanlış biçimde bir denetime aktarılırsa.|  
|<xref:System.ArgumentException>|<xref:System.Windows.Automation.ValuePattern.SetValue%2A><br /><br /> - Yeni bir değer dizeden bir biçime dönüştürülemiyorsa denetim tanır.|  
|<xref:System.Windows.Automation.ElementNotEnabledException>|<xref:System.Windows.Automation.ValuePattern.SetValue%2A><br /><br /> - Etkin olmayan bir denetimi manipüle etme girişiminde bulunulduğunda.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [UI Otomasyonu Denetim Desenlerine Genel Bakış](ui-automation-control-patterns-overview.md)
- [UI Otomasyonu Sağlayıcıda Denetim Düzenleri Desteği](support-control-patterns-in-a-ui-automation-provider.md)
- [İstemciler İçin UI Otomasyonu Denetim Düzenleri](ui-automation-control-patterns-for-clients.md)
- [ValuePattern Ekle Metin Örneği](https://github.com/Microsoft/WPF-Samples/tree/master/Accessibility/InsertText)
- [UI Otomasyon Ağacına Genel Bakış](ui-automation-tree-overview.md)
- [UI Otomasyonunda Önbelleğe Almayı Kullanma](use-caching-in-ui-automation.md)
