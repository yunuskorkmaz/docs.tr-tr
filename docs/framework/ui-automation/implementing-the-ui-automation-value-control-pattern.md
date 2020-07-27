---
title: UI Otomasyonu Değer Denetim Düzenini Uygulama
description: Kullanıcı Arabirimi Otomasyonu 'nda değer denetim deseninin uygulanması için yönergeleri ve kuralları gözden geçirin. IValueProvider arabirimi için gerekli üyeleri öğrenin.
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, Value
- UI Automation, Value control pattern
- Value control pattern
ms.assetid: b0fcdd87-3add-4345-bca9-e891205e02ba
ms.openlocfilehash: a15c0b50996e2c0dfdc937bc9565d5f9ba20c992
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87168205"
---
# <a name="implementing-the-ui-automation-value-control-pattern"></a>UI Otomasyonu Değer Denetim Düzenini Uygulama
> [!NOTE]
> Bu belge, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ad alanında tanımlanan yönetilen sınıfları kullanmak isteyen .NET Framework geliştiricilere yöneliktir <xref:System.Windows.Automation> . Hakkında en son bilgiler için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] bkz. [WINDOWS Otomasyonu API: UI Otomasyonu](/windows/win32/winauto/entry-uiauto-win32).  
  
 Bu konu <xref:System.Windows.Automation.Provider.IValueProvider> , olaylar ve özellikler hakkında bilgiler de dahil olmak üzere uygulama yönergelerini ve kurallarını tanıtır. Ek başvuruların bağlantıları konunun sonunda listelenmiştir.  
  
 <xref:System.Windows.Automation.ValuePattern>Denetim stili, bir aralığa yayılmayan ve dize olarak gösterilebilen bir iç değere sahip denetimleri desteklemek için kullanılır. Bu dize, denetime ve ayarlarına bağlı olarak düzenlenebilir. Bu kalıbı uygulayan denetimlerin örnekleri için bkz. [UI Otomasyonu istemcileri Için denetim model eşlemesi](control-pattern-mapping-for-ui-automation-clients.md).  
  
<a name="Implementation_Guidelines_and_Conventions"></a>
## <a name="implementation-guidelines-and-conventions"></a>Uygulama kılavuzları ve kuralları  
 Değer denetim modelini uygularken, aşağıdaki kılavuz ve kurallara göz önünde yer verilmiştir:  
  
- Ve gibi denetimler <xref:System.Windows.Automation.ControlType.ListItem> , <xref:System.Windows.Automation.ControlType.TreeItem> <xref:System.Windows.Automation.ValuePattern> denetimin geçerli düzenleme modundan bağımsız olarak, öğelerin herhangi birinin değeri düzenlenebilir ise, desteklemesi gerekir. Alt öğelerin düzenlenebilir olması durumunda üst denetim de desteklemelidir <xref:System.Windows.Automation.ValuePattern> .  
  
 ![Düzenlenebilir liste öğesi.](./media/uia-valuepattern-editable-listitem.PNG "UIA_ValuePattern_Editable_ListItem")  
Düzenlenebilir liste öğesi örneği  
  
- Tek satırlık düzenleme denetimleri, uygulayarak içeriğine programlı erişimi destekler <xref:System.Windows.Automation.Provider.IValueProvider> . Ancak, çok satırlı düzenleme denetimleri uygulamaz <xref:System.Windows.Automation.Provider.IValueProvider> ; bunun yerine kendi içeriğine erişim sağlar <xref:System.Windows.Automation.Provider.ITextProvider> .  
  
- Çok satırlı bir düzenleme denetiminin metin içeriğini almak için, denetimin uygulanması gerekir <xref:System.Windows.Automation.Provider.ITextProvider> . Ancak, <xref:System.Windows.Automation.Provider.ITextProvider> bir denetimin değerini ayarlamayı desteklemez.  
  
- <xref:System.Windows.Automation.Provider.IValueProvider>biçimlendirme bilgilerinin veya alt dize değerlerinin alınmasını desteklemez. <xref:System.Windows.Automation.Provider.ITextProvider>Bu senaryolarda uygulayın.  
  
- <xref:System.Windows.Automation.Provider.IValueProvider>, bir renk değeri (örneğin, "sarı") ve eşdeğer iç RGB yapısı arasındaki dize eşlemesini destekleyen Microsoft Word 'den (aşağıda gösterildiği gibi) **renk seçici** seçim denetimi gibi denetimler tarafından uygulanmalıdır.  
  
 ![Sarı vurgulanmış şekilde renk seçici.](./media/uia-valuepattern-colorpicker.png "UIA_ValuePattern_ColorPicker")  
Renk örneği dize eşlemesi örneği  
  
- Bir denetimin öğesine, <xref:System.Windows.Automation.AutomationElement.IsEnabledProperty> `true` <xref:System.Windows.Automation.ValuePattern.IsReadOnlyProperty> `false` çağrısına izin vermeden önce, olarak ayarlanmış olması gerekir <xref:System.Windows.Automation.Provider.IValueProvider.SetValue%2A> .  
  
<a name="Required_Members_for_the_IValueProvider_Interface"></a>
## <a name="required-members-for-ivalueprovider"></a>IValueProvider için gerekli Üyeler  
 Uygulamak için aşağıdaki özellikler ve Yöntemler gereklidir <xref:System.Windows.Automation.Provider.IValueProvider> .  
  
|Gerekli Üyeler|Üye türü|Notlar|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.ValuePattern.IsReadOnlyProperty>|Özellik|Hiçbiri|  
|<xref:System.Windows.Automation.ValuePattern.ValueProperty>|Özellik|Hiçbiri|  
|<xref:System.Windows.Automation.ValuePattern.SetValue%2A>|Yöntem|Hiçbiri|  
  
<a name="Exceptions"></a>
## <a name="exceptions"></a>Özel durumlar  
 Sağlayıcılar aşağıdaki özel durumları oluşturması gerekir.  
  
|Özel durum türü|Koşul|  
|--------------------|---------------|  
|<xref:System.InvalidOperationException>|<xref:System.Windows.Automation.ValuePattern.SetValue%2A><br /><br /> -Yerel ayara özgü bilgiler hatalı biçimlendirilmiş bir tarih gibi yanlış biçimde bir denetime geçirildiyse.|  
|<xref:System.ArgumentException>|<xref:System.Windows.Automation.ValuePattern.SetValue%2A><br /><br /> -Yeni bir değer bir dizeden denetimin tanıdığı biçime dönüştürülemez.|  
|<xref:System.Windows.Automation.ElementNotEnabledException>|<xref:System.Windows.Automation.ValuePattern.SetValue%2A><br /><br /> -Etkin olmayan bir denetimi işlemek için bir girişimde bulunuldu.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [UI Otomasyon Denetim Düzenlerine Genel Bakış](ui-automation-control-patterns-overview.md)
- [UI Otomasyon Sağlayıcısında Denetim Düzenleri Desteği](support-control-patterns-in-a-ui-automation-provider.md)
- [İstemciler İçin UI Otomasyon Denetim Düzenleri](ui-automation-control-patterns-for-clients.md)
- [Valuemodel metin ekleme örneği](https://github.com/Microsoft/WPF-Samples/tree/master/Accessibility/InsertText)
- [UI Otomasyon Ağacına Genel Bakış](ui-automation-tree-overview.md)
- [UI Otomasyonda Önbelleğe Almayı Kullanma](use-caching-in-ui-automation.md)
