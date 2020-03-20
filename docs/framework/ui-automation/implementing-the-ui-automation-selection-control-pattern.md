---
title: UI Otomasyon Seçim Denetim Düzenini Uygulama
ms.date: 03/30/2017
helpviewer_keywords:
- Selection control pattern
- UI Automation, Selection control pattern
- control patterns, Selection
ms.assetid: 449c3068-a5d6-4f66-84c6-1bcc7dd4d209
ms.openlocfilehash: 083a4bb56fe76c1d65015ffabf741d7e1953d2ff
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79180125"
---
# <a name="implementing-the-ui-automation-selection-control-pattern"></a>UI Otomasyon Seçim Denetim Düzenini Uygulama
> [!NOTE]
> Bu dokümantasyon, ad alanında tanımlanan yönetilen [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] sınıfları kullanmak <xref:System.Windows.Automation> isteyen .NET Framework geliştiricileri için tasarlanmıştır. Hakkında en son [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]bilgi için [Bkz. Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).  
  
 Bu <xref:System.Windows.Automation.Provider.ISelectionProvider>konu, olaylar ve özellikler hakkında bilgiler de dahil olmak üzere, uygulama yönergeleri ve kuralları sunar. Ek başvurulara bağlantılar konunun sonunda listelenir.  
  
 Denetim <xref:System.Windows.Automation.SelectionPattern> deseni, seçilebilir alt öğelerin bir koleksiyonu için kapsayıcı görevi yapan denetimleri desteklemek için kullanılır. Bu öğenin çocukları <xref:System.Windows.Automation.Provider.ISelectionItemProvider>uygulamak gerekir. Bu denetim deseni uygulayan denetim örnekleri için, [UI Otomasyon Istemcileri için Denetim Deseni Eşleciliği'ne](control-pattern-mapping-for-ui-automation-clients.md)bakın.  
  
<a name="Implementation_Guidelines_and_Conventions"></a>
## <a name="implementation-guidelines-and-conventions"></a>Uygulama Yönergeleri ve Sözleşmeleri  
 Seçim denetimi modelini uygularken aşağıdaki yönergeleri ve kuralları not edin:  
  
- Uygulanan <xref:System.Windows.Automation.Provider.ISelectionProvider> denetimler, tek veya birden çok alt öğenin seçilmesine izin verir. Örneğin, liste kutusu, liste görünümü ve ağaç görünümü birden çok seçimi desteklerken, açılan kutu, kaydırıcı ve radyo düğmesi grubu tek seçimi destekler.  
  
- **Birim** kaydırıcı denetimi gibi minimum, en büyük ve sürekli aralıkta <xref:System.Windows.Automation.Provider.IRangeValueProvider> olan <xref:System.Windows.Automation.Provider.ISelectionProvider>denetimler yerine uygulanmalıdır.  
  
- **Ekran Özellikleri** iletişim kutusundaki Ekran <xref:System.Windows.Automation.Provider.IRawElementProviderFragmentRoot> **Çözünürlüğü** kaydırıcısı veya Microsoft Word'deki **Renk Seçici** seçim denetimi (aşağıda gösterildiği gibi) gibi alt denetimleri yöneten tek seçim denetimleri uygulanmalıdır; <xref:System.Windows.Automation.Provider.ISelectionProvider> çocukları her ikisini <xref:System.Windows.Automation.Provider.IRawElementProviderFragment> <xref:System.Windows.Automation.Provider.ISelectionItemProvider>de uygulamalı ve .  
  
 ![Sarı vurgulanmış renk seçici.](./media/uia-valuepattern-colorpicker.png "UIA_ValuePattern_ColorPicker")  
Renk Swatch String Eşleme Örneği  
  
- Menüler desteklenmez. <xref:System.Windows.Automation.SelectionPattern> Hem grafik hem de metin içeren menü öğeleriyle (Microsoft Outlook'taki **Görünüm** menüsündeki **Önizleme Bölmesi** öğeleri gibi) <xref:System.Windows.Automation.Provider.IToggleProvider>çalışıyorsanız ve durumu iletmesi gerekiyorsa, uygulamanız gerekir.  
  
<a name="Required_Members_for_ISelectionProvider"></a>
## <a name="required-members-for-iselectionprovider"></a>ISelectionProvider için Gerekli Üyeler  
 <xref:System.Windows.Automation.Provider.ISelectionProvider> Arabirim için aşağıdaki özellikler, yöntemler ve olaylar gereklidir.  
  
|Gerekli üyeler|Tür|Notlar|  
|----------------------|----------|-----------|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider.CanSelectMultiple%2A>|Özellik|Özelliği kullanarak değiştirilen <xref:System.Windows.Automation.Automation.AddAutomationPropertyChangedEventHandler%2A> olayları <xref:System.Windows.Automation.Automation.RemoveAutomationPropertyChangedEventHandler%2A>desteklemeli ve .|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider.IsSelectionRequired%2A>|Özellik|Özelliği kullanarak değiştirilen <xref:System.Windows.Automation.Automation.AddAutomationPropertyChangedEventHandler%2A> olayları <xref:System.Windows.Automation.Automation.RemoveAutomationPropertyChangedEventHandler%2A>desteklemeli ve .|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider.GetSelection%2A>|Yöntem|None|  
|<xref:System.Windows.Automation.SelectionPatternIdentifiers.InvalidatedEvent>|Olay|Bir kapsayıcıdaki bir seçim önemli ölçüde değiştiğinde ve <xref:System.Windows.Automation.Provider.AutomationInteropProvider.InvalidateLimit> sürekli izinlerden daha fazla ekleme ve kaldırma olayı göndermeyi gerektirdiğinde yükseltilir.|  
  
 <xref:System.Windows.Automation.Provider.ISelectionProvider.IsSelectionRequired%2A> Ve <xref:System.Windows.Automation.Provider.ISelectionProvider.CanSelectMultiple%2A> özellikleri dinamik olabilir. Örneğin, denetimin ilk durumu varsayılan olarak seçilen herhangi bir öğe <xref:System.Windows.Automation.Provider.ISelectionProvider.IsSelectionRequired%2A> `false`olmayabilir, bu . Ancak, bir öğe seçildikten sonra, denetimher zaman en az bir öğe seçili olmalıdır. Benzer şekilde, nadir durumlarda, bir denetim başlatma da birden çok öğenin seçilmesine izin verebilir, ancak daha sonra yalnızca tek bir seçim yapılmasına izin verebilir.  
  
<a name="Exceptions"></a>
## <a name="exceptions"></a>Özel durumlar  
 Sağlayıcılar aşağıdaki özel durumları atmalıdır.  
  
|Özel Durum Türü|Koşul|  
|--------------------|---------------|  
|<xref:System.Windows.Automation.ElementNotEnabledException>|Denetim etkin değilse.|  
|<xref:System.InvalidOperationException>|Eğer kontrol gizliyse.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [UI Otomasyonu Denetim Desenlerine Genel Bakış](ui-automation-control-patterns-overview.md)
- [UI Otomasyonu Sağlayıcıda Denetim Düzenleri Desteği](support-control-patterns-in-a-ui-automation-provider.md)
- [İstemciler İçin UI Otomasyonu Denetim Düzenleri](ui-automation-control-patterns-for-clients.md)
- [UI Otomasyonu SelectionItem Denetim Desenini Uygulama](implementing-the-ui-automation-selectionitem-control-pattern.md)
- [UI Otomasyon Ağacına Genel Bakış](ui-automation-tree-overview.md)
- [UI Otomasyonunda Önbelleğe Almayı Kullanma](use-caching-in-ui-automation.md)
