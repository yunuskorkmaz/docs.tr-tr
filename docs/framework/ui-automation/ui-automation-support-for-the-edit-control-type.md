---
title: Düzenleme Denetim Türü İçin UI Otomasyon Desteği
ms.date: 03/30/2017
helpviewer_keywords:
- control types, Edit
- Edit control type
- UI Automation, Edit control type
ms.assetid: 6db9d231-c0a0-4e17-910e-ac80357f774f
ms.openlocfilehash: cdbb400d438231689fe35c4bff2bd2946b6bed80
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76789502"
---
# <a name="ui-automation-support-for-the-edit-control-type"></a>Düzenleme Denetim Türü İçin UI Otomasyon Desteği

> [!NOTE]
> Bu belge, <xref:System.Windows.Automation> ad alanında tanımlanan yönetilen [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] sınıflarını kullanmak isteyen .NET Framework geliştiricilere yöneliktir. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]hakkında en son bilgiler için bkz. [Windows Otomasyonu API: UI Otomasyonu](/windows/win32/winauto/entry-uiauto-win32).

Bu konu, düzenleme denetim türü için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] desteği hakkında bilgi sağlar. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], denetim türü, bir denetimin <xref:System.Windows.Automation.AutomationElement.ControlTypeProperty> özelliğini kullanmak için karşılaması gereken koşullar kümesidir. Koşullar [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağaç yapısı, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] özellik değerleri ve Denetim desenleri için özel yönergeler içerir.

Denetimleri Düzenle, bir kullanıcının zengin biçimlendirme desteği olmadan basit bir metin satırını görüntülemesini ve düzenlemesini sağlar.

Aşağıdaki bölümler, düzenleme denetim türü için gerekli [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağaç yapısını, özellikleri, denetim desenlerini ve olayları tanımlar. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] gereksinimleri, [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)], Win32 veya Windows Forms gibi tüm düzenleme denetimleri için geçerlidir.

<a name="Required_UI_Automation_Tree_Structure"></a>

## <a name="required-ui-automation-tree-structure"></a>Gerekli UI Otomasyonu ağaç yapısı

Aşağıdaki tabloda, düzenleme denetimleriyle ilgili [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağacının denetim görünümü ve içerik görünümü gösterilmektedir ve her görünümde nelerin yer aldığı açıklanmaktadır. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağacı hakkında daha fazla bilgi için bkz. [UI Otomasyon ağacına genel bakış](ui-automation-tree-overview.md).

|Denetim görünümü|İçerik görünümü|
|------------------|------------------|
|Düzenle|Düzenle|

Tek satırlı bir denetim olduğundan, düzenleme denetim türünü uygulayan denetimler her zaman [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağacının denetim görünümünde sıfır kaydırma çubuklarına sahip olur. Tek metin satırı bazı düzen senaryolarında kaydırılabilir. Düzenleme denetim türü, küçük miktarlarda düzenlenebilir veya seçilebilir metinler tutmak için idealdir.

<a name="Required_UI_Automation_Properties"></a>

## <a name="required-ui-automation-properties"></a>Gerekli UI Otomasyon Özellikleri

Aşağıdaki tabloda, değeri veya tanımı özellikle düzenleme denetimleriyle ilgili olan [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] özellikleri listelenmektedir. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] özellikleri hakkında daha fazla bilgi için bkz. [istemciler Için UI Otomasyon özellikleri](ui-automation-properties-for-clients.md).

|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] özelliği|Değer|Notlar|
|------------------------------------------------------------------------------------|-----------|-----------|
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationIdProperty>|Notlara bakın.|Bu özelliğin değerinin bir uygulamadaki tüm denetimlerde benzersiz olması gerekir.|
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>|Notlara bakın.|Tüm denetimi içeren en dıştaki dikdörtgen.|
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ClickablePointProperty>|Notlara bakın.|Düzenleme denetimi, kullanıcı fareyle tıkladığında, denetimin düzenleme bölümüne giriş odağı veren bir tıklatılabilir noktaya sahip olmalıdır.|
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsKeyboardFocusableProperty>|Notlara bakın.|Denetim, klavye odağı alamıyorsa, bu özelliği desteklemesi gerekir.|
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>|Notlara bakın.|Düzenleme denetiminin adı genellikle statik bir metin etiketinden oluşturulur. Statik bir metin etiketi yoksa, `Name` için bir özellik değeri uygulama geliştiricisi tarafından atanmalıdır. `Name` özelliği asla düzenleme denetiminin metin içeriğini içermemelidir.|
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LabeledByProperty>|Notlara bakın.|Denetimle ilişkili bir statik metin etiketi varsa, bu özellik bu denetimin bir başvurusunu kullanıma sunmalıdır. Metin denetimi başka bir denetimin alt bileşeni ise, `LabeledBy` özellik kümesine sahip olmaz.|
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ControlTypeProperty>|Düzenle|Bu değer tüm [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] çerçeveleri için aynıdır.|
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LocalizedControlTypeProperty>|Düzenle|Düzenleme denetim türüne karşılık gelen yerelleştirilmiş dize.|
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsContentElementProperty>|Doğru|Düzenleme denetimi her zaman [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağacının içerik görünümüne dahil edilmiştir.|
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsControlElementProperty>|Doğru|Düzenleme denetimi her zaman [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağacının denetim görünümüne dahil edilmiştir.|
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsPasswordProperty>|Notlara bakın.|Parola içeren düzenleme denetimlerinde true olarak ayarlanmalıdır. Bir düzenleme denetimi parola içerikleri içeriyorsa, bu özellik bir ekran okuyucu tarafından Kullanıcı tarafından yazarken tuş vuruşlarının okunup okunmayacağını anlamak için kullanılabilir.|

<a name="Required_UI_Automation_Control_Patterns"></a>

## <a name="required-ui-automation-control-patterns-and-properties"></a>Gerekli UI Otomasyonu Denetim desenleri ve özellikleri

Aşağıdaki tabloda, tüm düzenleme denetimleri tarafından desteklenmesi gereken denetim desenleri listelenmektedir. Denetim desenleri hakkında daha fazla bilgi için bkz. [UI Otomasyonu Denetim desenlerine genel bakış](ui-automation-control-patterns-overview.md).

|Denetim deseninin/denetim deseninin özelliği|Destek/değer|Notlar|
|-----------------------------------------------|--------------------|-----------|
|<xref:System.Windows.Automation.Provider.ITextProvider>|Şekline|Ayrıntılı metin bilgileri her zaman istemciler için kullanılabilir olması gerektiğinden, düzenleme denetimleri metin denetim modelini desteklemelidir.|
|<xref:System.Windows.Automation.Provider.IValueProvider>|Şekline|Bir dize alan tüm düzenleme denetimleri değer modelini kullanıma sunmalıdır.|
|<xref:System.Windows.Automation.Provider.IValueProvider.IsReadOnly%2A>|Notlara bakın.|Bu özellik, denetimin bir değer olarak ayarlanmış veya Kullanıcı tarafından düzenlenebilir olup olmayacağını belirtmek için ayarlanmalıdır.|
|<xref:System.Windows.Automation.Provider.IValueProvider.Value%2A>|Notlara bakın.|Bu özellik, düzenleme denetiminin metin içeriğini döndürür. `IsPasswordProperty` `true`olarak ayarlanırsa, bu özellik istendiğinde bir `InvalidOperationException` yükseltmelidir.|
|<xref:System.Windows.Automation.Provider.IRangeValueProvider>|Şekline|Sayısal bir Aralık alan tüm düzenleme denetimleri, Aralık değeri denetim modelini kullanıma sunmalıdır.|
|<xref:System.Windows.Automation.Provider.IRangeValueProvider.Minimum%2A>|Notlara bakın.|Bu özellik, düzenleme denetiminin içeriğinin ayarlayabilmesi için en küçük değer olmalıdır.|
|<xref:System.Windows.Automation.Provider.IRangeValueProvider.Maximum%2A>|Notlara bakın.|Bu özellik, düzenleme denetimi içeriğinin ayarlandığı en büyük değer olmalıdır.|
|<xref:System.Windows.Automation.Provider.IRangeValueProvider.SmallChange%2A>|Notlara bakın.|Bu özellik, değerin ayarlanabileceği ondalık basamak sayısını belirtmelidir. Düzenleme yalnızca tamsayı al ise, `SmallChangeProperty` 1 olmalıdır. Düzenleme 1,0 ile 2,0 arasında bir Aralık alırsa `SmallChangeProperty` 0,1 olmalıdır. Düzenleme denetimi 1,00 ile 2,00 arasında bir Aralık alırsa `SmallChangeProperty` 0,001 olmalıdır.|
|<xref:System.Windows.Automation.Provider.IRangeValueProvider.LargeChange%2A>|`Null`|Bu özelliğin bir düzenleme denetiminde açığa çıkarılması gerekmez.|
|<xref:System.Windows.Automation.Provider.IRangeValueProvider.Value%2A>|Notlara bakın.|Bu özellik, düzenleme denetiminin sayısal içeriğini gösterir. Daha kesin bir değer, `Minimum` ve `Maximum` özelliklerinde belirtilen aralıklar dahilinde bir [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] istemci tarafından ayarlandığında, Value özelliği otomatik olarak en yakın kabul edilen değere yuvarlanır.|

<a name="Required_UI_Automation_Events"></a>

## <a name="required-ui-automation-events"></a>Gerekli UI Otomasyon olayları

Aşağıdaki tabloda, tüm düzenleme denetimleri tarafından desteklenmesi gereken [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] olayları listelenmektedir. Olaylar hakkında daha fazla bilgi için bkz. [UI Otomasyonu olaylarına genel bakış](ui-automation-events-overview.md).

|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] olayı|Destek|Notlar|
|---------------------------------------------------------------------------------|-------------|-----------|
|<xref:System.Windows.Automation.SelectionPatternIdentifiers.InvalidatedEvent>|Gerekli|Yok.|
|<xref:System.Windows.Automation.TextPatternIdentifiers.TextSelectionChangedEvent>|Gerekli|Yok.|
|<xref:System.Windows.Automation.TextPatternIdentifiers.TextChangedEvent>|Gerekli|Yok.|
|özellik değişti olayı <xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>.|Gerekli|Yok.|
|özellik değişti olayı <xref:System.Windows.Automation.AutomationElementIdentifiers.IsOffscreenProperty>.|Gerekli|Yok.|
|özellik değişti olayı <xref:System.Windows.Automation.AutomationElementIdentifiers.IsEnabledProperty>.|Gerekli|Yok.|
|özellik değişti olayı <xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>.|Gerekli|Yok.|
|özellik değişti olayı <xref:System.Windows.Automation.ValuePatternIdentifiers.ValueProperty>.|Şekline|Yok.|
|özellik değişti olayı <xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontallyScrollableProperty>.|hiçbir zaman|Yok.|
|özellik değişti olayı <xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontalScrollPercentProperty>.|hiçbir zaman|Yok.|
|özellik değişti olayı <xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontalViewSizeProperty>.|hiçbir zaman|Yok.|
|özellik değişti olayı <xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticalScrollPercentProperty>.|hiçbir zaman|Yok.|
|özellik değişti olayı <xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticallyScrollableProperty>.|hiçbir zaman|Yok.|
|özellik değişti olayı <xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticalViewSizeProperty>.|hiçbir zaman|Yok.|
|özellik değişti olayı <xref:System.Windows.Automation.RangeValuePatternIdentifiers.ValueProperty>.|Şekline|Denetim, Aralık değeri denetim modelini destekliyorsa, bu olayı desteklemelidir.|
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationFocusChangedEvent>|Gerekli|Yok.|
|<xref:System.Windows.Automation.AutomationElementIdentifiers.StructureChangedEvent>|Gerekli|Yok.|

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Automation.ControlType.Edit>
- [UI Otomasyonu Denetim Türlerine Genel Bakış](ui-automation-control-types-overview.md)
- [UI Otomasyonuna Genel Bakış](ui-automation-overview.md)
