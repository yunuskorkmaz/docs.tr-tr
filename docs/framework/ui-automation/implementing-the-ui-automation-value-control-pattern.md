---
title: UI Otomasyonu Değer Denetim Düzenini Uygulama
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, Value
- UI Automation, Value control pattern
- Value control pattern
ms.assetid: b0fcdd87-3add-4345-bca9-e891205e02ba
ms.openlocfilehash: 4af35b3ad1277723d4102b3aeac48748588ef8bf
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70244013"
---
# <a name="implementing-the-ui-automation-value-control-pattern"></a>UI Otomasyonu Değer Denetim Düzenini Uygulama
> [!NOTE]
> Bu belge, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] <xref:System.Windows.Automation> ad alanında tanımlanan yönetilen sınıfları kullanmak isteyen .NET Framework geliştiricilere yöneliktir. Hakkında [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]en son bilgiler için bkz [. Windows Otomasyonu API 'si: UI Otomasyonu](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Bu konu, olaylar ve özellikler hakkında bilgiler <xref:System.Windows.Automation.Provider.IValueProvider>de dahil olmak üzere uygulama yönergelerini ve kurallarını tanıtır. Ek başvuruların bağlantıları konunun sonunda listelenmiştir.  
  
 Denetim <xref:System.Windows.Automation.ValuePattern> stili, bir aralığa yayılmayan ve dize olarak gösterilebilen bir iç değere sahip denetimleri desteklemek için kullanılır. Bu dize, denetime ve ayarlarına bağlı olarak düzenlenebilir. Bu kalıbı uygulayan denetimlerin örnekleri için bkz. [UI Otomasyonu istemcileri Için denetim model eşlemesi](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md).  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a>Uygulama kılavuzları ve kuralları  
 Değer denetim modelini uygularken, aşağıdaki kılavuz ve kurallara göz önünde yer verilmiştir:  
  
- Ve gibi denetimler, denetimin geçerli <xref:System.Windows.Automation.ValuePattern> düzenleme modundan bağımsız olarak, öğelerin herhangi birinin değeri düzenlenebilir ise, desteklemesi gerekir. <xref:System.Windows.Automation.ControlType.TreeItem> <xref:System.Windows.Automation.ControlType.ListItem> Alt öğelerin düzenlenebilir olması durumunda üst <xref:System.Windows.Automation.ValuePattern> denetim de desteklemelidir.  
  
 ![Düzenlenebilir liste öğesi.](../../../docs/framework/ui-automation/media/uia-valuepattern-editable-listitem.PNG "UIA_ValuePattern_Editable_ListItem")  
Düzenlenebilir liste öğesi örneği  
  
- Tek satırlık düzenleme denetimleri, uygulayarak <xref:System.Windows.Automation.Provider.IValueProvider>içeriğine programlı erişimi destekler. Ancak, çok satırlı düzenleme denetimleri uygulamaz <xref:System.Windows.Automation.Provider.IValueProvider>; bunun yerine kendi içeriğine <xref:System.Windows.Automation.Provider.ITextProvider>erişim sağlar.  
  
- Çok satırlı bir düzenleme denetiminin metin içeriğini almak için, denetimin uygulanması <xref:System.Windows.Automation.Provider.ITextProvider>gerekir. Ancak, <xref:System.Windows.Automation.Provider.ITextProvider> bir denetimin değerini ayarlamayı desteklemez.  
  
- <xref:System.Windows.Automation.Provider.IValueProvider>biçimlendirme bilgilerinin veya alt dize değerlerinin alınmasını desteklemez. Bu <xref:System.Windows.Automation.Provider.ITextProvider> senaryolarda uygulayın.  
  
- <xref:System.Windows.Automation.Provider.IValueProvider>, bir renk değeri (örneğin, "sarı") ve eşdeğer [!INCLUDE[TLA#tla_word](../../../includes/tlasharptla-word-md.md)] iç RGB yapısı arasındaki dize eşlemesini destekleyen (aşağıda gösterilmiştir) **renk seçici** seçim denetimi gibi denetimler tarafından uygulanmalıdır.  
  
 ![Sarı vurgulanmış şekilde renk seçici.](../../../docs/framework/ui-automation/media/uia-valuepattern-colorpicker.png "UIA_ValuePattern_ColorPicker")  
Renk örneği dize eşlemesi örneği  
  
- Bir denetimin <xref:System.Windows.Automation.AutomationElement.IsEnabledProperty> öğesine, `true`çağrısınaizinvermedenönce, olarak ayarlanmış olması gerekir. <xref:System.Windows.Automation.Provider.IValueProvider.SetValue%2A> <xref:System.Windows.Automation.ValuePattern.IsReadOnlyProperty> `false`  
  
<a name="Required_Members_for_the_IValueProvider_Interface"></a>   
## <a name="required-members-for-ivalueprovider"></a>IValueProvider için gerekli Üyeler  
 Uygulamak <xref:System.Windows.Automation.Provider.IValueProvider>için aşağıdaki özellikler ve Yöntemler gereklidir.  
  
|Gerekli Üyeler|Üye türü|Notlar|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.ValuePattern.IsReadOnlyProperty>|Özellik|Yok.|  
|<xref:System.Windows.Automation.ValuePattern.ValueProperty>|Özellik|Yok.|  
|<xref:System.Windows.Automation.ValuePattern.SetValue%2A>|Yöntem|Yok.|  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a>Özel Durumlar  
 Sağlayıcılar aşağıdaki özel durumları oluşturması gerekir.  
  
|Özel durum türü|Koşul|  
|--------------------|---------------|  
|<xref:System.InvalidOperationException>|<xref:System.Windows.Automation.ValuePattern.SetValue%2A><br /><br /> -Yerel ayara özgü bilgiler hatalı biçimlendirilmiş bir tarih gibi yanlış biçimde bir denetime geçirildiyse.|  
|<xref:System.ArgumentException>|<xref:System.Windows.Automation.ValuePattern.SetValue%2A><br /><br /> -Yeni bir değer bir dizeden denetimin tanıdığı biçime dönüştürülemez.|  
|<xref:System.Windows.Automation.ElementNotEnabledException>|<xref:System.Windows.Automation.ValuePattern.SetValue%2A><br /><br /> -Etkin olmayan bir denetimi işlemek için bir girişimde bulunuldu.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [UI Otomasyonu Denetim Desenlerine Genel Bakış](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)
- [UI Otomasyonu Sağlayıcıda Denetim Düzenleri Desteği](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)
- [İstemciler İçin UI Otomasyonu Denetim Düzenleri](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)
- [Valuemodel metin ekleme örneği](https://github.com/Microsoft/WPF-Samples/tree/master/Accessibility/InsertText)
- [UI Otomasyon Ağacına Genel Bakış](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)
- [UI Otomasyonunda Önbelleğe Almayı Kullanma](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)
