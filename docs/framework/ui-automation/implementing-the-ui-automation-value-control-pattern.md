---
title: UI Otomasyonu Değer Denetim Düzenini Uygulama
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, Value
- UI Automation, Value control pattern
- Value control pattern
ms.assetid: b0fcdd87-3add-4345-bca9-e891205e02ba
ms.openlocfilehash: 75cf628b6faad1f8c52a70c77baa4ede21160510
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73458139"
---
# <a name="implementing-the-ui-automation-value-control-pattern"></a>UI Otomasyonu Değer Denetim Düzenini Uygulama
> [!NOTE]
> Bu belge, <xref:System.Windows.Automation> ad alanında tanımlanan yönetilen [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] sınıflarını kullanmak isteyen .NET Framework geliştiricilere yöneliktir. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]hakkında en son bilgiler için bkz. [Windows Otomasyonu API: UI Otomasyonu](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Bu konu, olaylar ve özellikler hakkında bilgiler de dahil olmak üzere <xref:System.Windows.Automation.Provider.IValueProvider>uygulamak için kılavuz ve kuralları tanıtır. Ek başvuruların bağlantıları konunun sonunda listelenmiştir.  
  
 <xref:System.Windows.Automation.ValuePattern> denetim deseninin, bir aralığa yayılmayan ve dize olarak gösterilebilen bir iç değere sahip denetimleri desteklemek için kullanılır. Bu dize, denetime ve ayarlarına bağlı olarak düzenlenebilir. Bu kalıbı uygulayan denetimlerin örnekleri için bkz. [UI Otomasyonu istemcileri Için denetim model eşlemesi](control-pattern-mapping-for-ui-automation-clients.md).  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a>Uygulama kılavuzları ve kuralları  
 Değer denetim modelini uygularken, aşağıdaki kılavuz ve kurallara göz önünde yer verilmiştir:  
  
- <xref:System.Windows.Automation.ControlType.ListItem> ve <xref:System.Windows.Automation.ControlType.TreeItem> gibi denetimler, denetimin geçerli düzenleme modundan bağımsız olarak bazı öğelerin değeri düzenlenebilir durumdaysa <xref:System.Windows.Automation.ValuePattern> desteklemelidir. Alt öğeler düzenlenebilir ise üst denetim de <xref:System.Windows.Automation.ValuePattern> desteklemelidir.  
  
 ![Düzenlenebilir liste öğesi.](./media/uia-valuepattern-editable-listitem.PNG "UIA_ValuePattern_Editable_ListItem")  
Düzenlenebilir liste öğesi örneği  
  
- Tek satırlık düzenleme denetimleri, <xref:System.Windows.Automation.Provider.IValueProvider>uygulayarak içeriğine programlı erişimi destekler. Ancak, çok satırlı düzenleme denetimleri <xref:System.Windows.Automation.Provider.IValueProvider>uygulamaz; Bunun yerine, <xref:System.Windows.Automation.Provider.ITextProvider>uygulayarak içeriğine erişim sağlar.  
  
- Çok satırlı bir düzenleme denetiminin metin içeriğini almak için, denetimin <xref:System.Windows.Automation.Provider.ITextProvider>uygulaması gerekir. Ancak, <xref:System.Windows.Automation.Provider.ITextProvider> denetimin değerini ayarlamayı desteklemez.  
  
- <xref:System.Windows.Automation.Provider.IValueProvider>, biçimlendirme bilgilerinin veya alt dize değerlerinin alınmasını desteklemez. Bu senaryolarda <xref:System.Windows.Automation.Provider.ITextProvider> uygulayın.  
  
- <xref:System.Windows.Automation.Provider.IValueProvider>, bir renk değeri (örneğin, "sarı") ve eşdeğer iç RGB yapısı arasındaki dize eşlemesini destekleyen Microsoft Word 'den (aşağıda gösterildiği gibi) **renk seçici** seçim denetimi gibi denetimler tarafından uygulanmalıdır.  
  
 ![Sarı vurgulanmış şekilde renk seçici.](./media/uia-valuepattern-colorpicker.png "UIA_ValuePattern_ColorPicker")  
Renk örneği dize eşlemesi örneği  
  
- Bir denetimin <xref:System.Windows.Automation.AutomationElement.IsEnabledProperty> `true` olarak ayarlanmış olması gerekir ve <xref:System.Windows.Automation.Provider.IValueProvider.SetValue%2A>bir çağrıya izin vermeden önce <xref:System.Windows.Automation.ValuePattern.IsReadOnlyProperty> `false` olarak ayarlanır.  
  
<a name="Required_Members_for_the_IValueProvider_Interface"></a>   
## <a name="required-members-for-ivalueprovider"></a>IValueProvider için gerekli Üyeler  
 <xref:System.Windows.Automation.Provider.IValueProvider>uygulamak için aşağıdaki özellikler ve Yöntemler gereklidir.  
  
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

- [UI Otomasyonu Denetim Desenlerine Genel Bakış](ui-automation-control-patterns-overview.md)
- [UI Otomasyonu Sağlayıcıda Denetim Düzenleri Desteği](support-control-patterns-in-a-ui-automation-provider.md)
- [İstemciler İçin UI Otomasyonu Denetim Düzenleri](ui-automation-control-patterns-for-clients.md)
- [Valuemodel metin ekleme örneği](https://github.com/Microsoft/WPF-Samples/tree/master/Accessibility/InsertText)
- [UI Otomasyon Ağacına Genel Bakış](ui-automation-tree-overview.md)
- [UI Otomasyonunda Önbelleğe Almayı Kullanma](use-caching-in-ui-automation.md)
