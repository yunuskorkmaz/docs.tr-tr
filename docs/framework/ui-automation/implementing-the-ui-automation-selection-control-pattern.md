---
title: UI Otomasyon Seçim Denetim Düzenini Uygulama
ms.date: 03/30/2017
helpviewer_keywords:
- Selection control pattern
- UI Automation, Selection control pattern
- control patterns, Selection
ms.assetid: 449c3068-a5d6-4f66-84c6-1bcc7dd4d209
ms.openlocfilehash: 39baadbad4bf5aff1cc2cd7877489f43581e0fa0
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73458164"
---
# <a name="implementing-the-ui-automation-selection-control-pattern"></a>UI Otomasyon Seçim Denetim Düzenini Uygulama
> [!NOTE]
> Bu belge, <xref:System.Windows.Automation> ad alanında tanımlanan yönetilen [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] sınıflarını kullanmak isteyen .NET Framework geliştiricilere yöneliktir. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]hakkında en son bilgiler için bkz. [Windows Otomasyonu API: UI Otomasyonu](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Bu konu, olaylar ve özellikler hakkında bilgiler de dahil olmak üzere <xref:System.Windows.Automation.Provider.ISelectionProvider>uygulamak için kılavuz ve kuralları tanıtır. Ek başvuruların bağlantıları konunun sonunda listelenmiştir.  
  
 <xref:System.Windows.Automation.SelectionPattern> denetim stili, seçilebilir alt öğelerin bir koleksiyonu için kapsayıcılar olarak davranan denetimleri desteklemek için kullanılır. Bu öğenin alt öğeleri <xref:System.Windows.Automation.Provider.ISelectionItemProvider>gerçekleştirmelidir. Bu denetim modelini uygulayan denetimlerin örnekleri için bkz. [UI Otomasyonu istemcileri Için denetim model eşlemesi](control-pattern-mapping-for-ui-automation-clients.md).  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a>Uygulama kılavuzları ve kuralları  
 Seçim Denetim modelini uygularken, aşağıdaki kılavuz ve kurallara göz önünde aklınızda olmanız gerekir:  
  
- <xref:System.Windows.Automation.Provider.ISelectionProvider> uygulayan denetimler tek veya birden çok alt öğenin seçili olmasını sağlar. Örneğin, liste kutusu, liste görünümü ve ağaç görünümü birden çok seçimi destekler, Birleşik giriş kutusu, kaydırıcı ve radyo düğmesi grubu tek seçimi destekler.  
  
- **Birim** kaydırıcı denetimi gibi minimum, maksimum ve sürekli aralığa sahip denetimler <xref:System.Windows.Automation.Provider.ISelectionProvider>yerine <xref:System.Windows.Automation.Provider.IRangeValueProvider> uygulamalıdır.  
  
- **Görüntüleme özellikleri** Iletişim kutusundaki **ekran çözünürlüğü** kaydırıcısı veya Microsoft Word 'deki **renk Seçicisi** seçim denetimi gibi <xref:System.Windows.Automation.Provider.IRawElementProviderFragmentRoot>uygulayan alt denetimleri yöneten tek seçim denetimleri (aşağıda gösterilmiştir ), <xref:System.Windows.Automation.Provider.ISelectionProvider>uygulamalıdır; alt öğeleri hem <xref:System.Windows.Automation.Provider.IRawElementProviderFragment> hem de <xref:System.Windows.Automation.Provider.ISelectionItemProvider>uygulamalıdır.  
  
 ![Sarı vurgulanmış şekilde renk seçici.](./media/uia-valuepattern-colorpicker.png "UIA_ValuePattern_ColorPicker")  
Renk örneği dize eşlemesi örneği  
  
- Menüler <xref:System.Windows.Automation.SelectionPattern>desteklemez. Hem grafik hem de metin içeren menü öğeleriyle çalışıyorsanız (Microsoft Outlook 'ta **Görünüm** menüsündeki **Önizleme bölmesi** öğeleri gibi) ve durumu iletmelisiniz, <xref:System.Windows.Automation.Provider.IToggleProvider>uygulamanız gerekir.  
  
<a name="Required_Members_for_ISelectionProvider"></a>   
## <a name="required-members-for-iselectionprovider"></a>ISelectionProvider için gerekli Üyeler  
 <xref:System.Windows.Automation.Provider.ISelectionProvider> arabirimi için aşağıdaki özellikler, Yöntemler ve olaylar gereklidir.  
  
|Gerekli Üyeler|Tür|Notlar|  
|----------------------|----------|-----------|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider.CanSelectMultiple%2A>|Özellik|<xref:System.Windows.Automation.Automation.AddAutomationPropertyChangedEventHandler%2A> ve <xref:System.Windows.Automation.Automation.RemoveAutomationPropertyChangedEventHandler%2A>kullanarak özellik değiştirilen olayları desteklemelidir.|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider.IsSelectionRequired%2A>|Özellik|<xref:System.Windows.Automation.Automation.AddAutomationPropertyChangedEventHandler%2A> ve <xref:System.Windows.Automation.Automation.RemoveAutomationPropertyChangedEventHandler%2A>kullanarak özellik değiştirilen olayları desteklemelidir.|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider.GetSelection%2A>|Yöntem|Yok.|  
|<xref:System.Windows.Automation.SelectionPatternIdentifiers.InvalidatedEvent>|Olay|Kapsayıcıda bir seçim önemli ölçüde değiştiği ve <xref:System.Windows.Automation.Provider.AutomationInteropProvider.InvalidateLimit> sabitinden izin verdiğinden daha fazla ekleme ve kaldırma olayı gönderilmesini gerektirdiğinde tetiklenir.|  
  
 <xref:System.Windows.Automation.Provider.ISelectionProvider.IsSelectionRequired%2A> ve <xref:System.Windows.Automation.Provider.ISelectionProvider.CanSelectMultiple%2A> özellikleri dinamik olabilir. Örneğin, bir denetimin ilk durumu varsayılan olarak seçili herhangi bir öğeye sahip olmayabilir ve bu <xref:System.Windows.Automation.Provider.ISelectionProvider.IsSelectionRequired%2A> `false`. Ancak, bir öğe seçildikten sonra Denetim her zaman en az bir öğe seçilmiş olmalıdır. Benzer şekilde, ender durumlarda, bir denetim birden fazla öğenin başlatma sırasında seçilebilsin, ancak bundan sonra yalnızca tek seçimlerin olmasına izin verebilir.  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a>Özel Durumlar  
 Sağlayıcılar aşağıdaki özel durumları oluşturması gerekir.  
  
|Özel durum türü|Koşul|  
|--------------------|---------------|  
|<xref:System.Windows.Automation.ElementNotEnabledException>|Denetim etkinleştirilmemişse.|  
|<xref:System.InvalidOperationException>|Denetim gizliyse.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [UI Otomasyonu Denetim Desenlerine Genel Bakış](ui-automation-control-patterns-overview.md)
- [UI Otomasyonu Sağlayıcıda Denetim Düzenleri Desteği](support-control-patterns-in-a-ui-automation-provider.md)
- [İstemciler İçin UI Otomasyonu Denetim Düzenleri](ui-automation-control-patterns-for-clients.md)
- [UI Otomasyonu SelectionItem Denetim Desenini Uygulama](implementing-the-ui-automation-selectionitem-control-pattern.md)
- [UI Otomasyon Ağacına Genel Bakış](ui-automation-tree-overview.md)
- [UI Otomasyonunda Önbelleğe Almayı Kullanma](use-caching-in-ui-automation.md)
