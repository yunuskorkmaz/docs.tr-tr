---
title: Düzenleme Denetim Türü İçin UI Otomasyon Desteği
description: Düzenleme denetim türü için UI Otomasyonu desteği hakkında bilgi alın. Gerekli ağaç yapısını, özellikleri, denetim desenlerini ve olayları öğrenin.
ms.date: 03/30/2017
helpviewer_keywords:
- control types, Edit
- Edit control type
- UI Automation, Edit control type
ms.assetid: 6db9d231-c0a0-4e17-910e-ac80357f774f
ms.openlocfilehash: 6c404786d58cfcb4cc7dabd982eea33694b7cd0b
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87167938"
---
# <a name="ui-automation-support-for-the-edit-control-type"></a>Düzenleme Denetim Türü İçin UI Otomasyon Desteği

> [!NOTE]
> Bu belge, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ad alanında tanımlanan yönetilen sınıfları kullanmak isteyen .NET Framework geliştiricilere yöneliktir <xref:System.Windows.Automation> . Hakkında en son bilgiler için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] bkz. [WINDOWS Otomasyonu API: UI Otomasyonu](/windows/win32/winauto/entry-uiauto-win32).

Bu konu [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] , düzenleme denetim türü için destek hakkında bilgi sağlar. ' De [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] , bir denetim türü, özelliği kullanmak için bir denetimin uyması gereken koşullar kümesidir <xref:System.Windows.Automation.AutomationElement.ControlTypeProperty> . Koşullar, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağaç yapısı, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] özellik değerleri ve Denetim desenleri için özel kurallar içerir.

Denetimleri Düzenle, bir kullanıcının zengin biçimlendirme desteği olmadan basit bir metin satırını görüntülemesini ve düzenlemesini sağlar.

Aşağıdaki bölümler, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] düzenleme denetim türü için gerekli ağaç yapısını, özellikleri, denetim desenlerini ve olayları tanımlar. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Gereksinimler, Win32 veya Windows Forms tüm düzenleme denetimleri için geçerlidir [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)] .

<a name="Required_UI_Automation_Tree_Structure"></a>

## <a name="required-ui-automation-tree-structure"></a>Gerekli UI Otomasyonu ağaç yapısı

Aşağıdaki tabloda, düzenleme denetimleriyle ilgili olan ağacın denetim görünümü ve içerik görünümü gösterilmektedir [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ve her görünümde nelerin yer aldığı açıklanmaktadır. Ağaç hakkında daha fazla bilgi için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] bkz. [UI Otomasyon ağacına genel bakış](ui-automation-tree-overview.md).

|Denetim görünümü|İçerik görünümü|
|------------------|------------------|
|Düzenle|Düzenle|

Düzenleme denetim türünü uygulayan denetimlerin, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tek satırlık bir denetim olduğu için ağacın denetim görünümünde her zaman sıfır kaydırma çubuğu olacaktır. Tek metin satırı bazı düzen senaryolarında kaydırılabilir. Düzenleme denetim türü, küçük miktarlarda düzenlenebilir veya seçilebilir metinler tutmak için idealdir.

<a name="Required_UI_Automation_Properties"></a>

## <a name="required-ui-automation-properties"></a>Gerekli UI Otomasyon Özellikleri

Aşağıdaki tabloda, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] değeri veya tanımı özellikle düzenleme denetimleriyle ilgili olan özellikler listelenmiştir. Özellikler hakkında daha fazla bilgi için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] bkz. [Istemciler Için UI Otomasyon özellikleri](ui-automation-properties-for-clients.md).

|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Özelliði|Değer|Notlar|
|------------------------------------------------------------------------------------|-----------|-----------|
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationIdProperty>|Notlara bakın.|Bu özelliğin değerinin bir uygulamadaki tüm denetimlerde benzersiz olması gerekir.|
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>|Notlara bakın.|Tüm denetimi içeren en dıştaki dikdörtgen.|
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ClickablePointProperty>|Notlara bakın.|Düzenleme denetimi, kullanıcı fareyle tıkladığında, denetimin düzenleme bölümüne giriş odağı veren bir tıklatılabilir noktaya sahip olmalıdır.|
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsKeyboardFocusableProperty>|Notlara bakın.|Denetim, klavye odağı alamıyorsa, bu özelliği desteklemesi gerekir.|
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>|Notlara bakın.|Düzenleme denetiminin adı genellikle statik bir metin etiketinden oluşturulur. Statik bir metin etiketi yoksa, `Name` uygulama geliştiricisi tarafından bir özellik değeri atanmalıdır. `Name`Özelliği asla düzenleme denetiminin metin içeriğini içermemelidir.|
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LabeledByProperty>|Notlara bakın.|Denetimle ilişkili bir statik metin etiketi varsa, bu özellik bu denetimin bir başvurusunu kullanıma sunmalıdır. Metin denetimi başka bir denetimin alt bileşeni ise, bir `LabeledBy` özellik kümesine sahip olmaz.|
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ControlTypeProperty>|Düzenle|Bu değer tüm çerçeveler için aynıdır [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] .|
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LocalizedControlTypeProperty>|Düzenle|Düzenleme denetim türüne karşılık gelen yerelleştirilmiş dize.|
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsContentElementProperty>|Doğru|Düzenleme denetimi her zaman ağacın içerik görünümüne dahil edilmiştir [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] .|
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsControlElementProperty>|Doğru|Düzenleme denetimi her zaman ağacın denetim görünümüne dahil edilmiştir [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] .|
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsPasswordProperty>|Notlara bakın.|Parola içeren düzenleme denetimlerinde true olarak ayarlanmalıdır. Bir düzenleme denetimi parola içerikleri içeriyorsa, bu özellik bir ekran okuyucu tarafından Kullanıcı tarafından yazarken tuş vuruşlarının okunup okunmayacağını anlamak için kullanılabilir.|

<a name="Required_UI_Automation_Control_Patterns"></a>

## <a name="required-ui-automation-control-patterns-and-properties"></a>Gerekli UI Otomasyonu Denetim desenleri ve özellikleri

Aşağıdaki tabloda, tüm düzenleme denetimleri tarafından desteklenmesi gereken denetim desenleri listelenmektedir. Denetim desenleri hakkında daha fazla bilgi için bkz. [UI Otomasyonu Denetim desenlerine genel bakış](ui-automation-control-patterns-overview.md).

|Denetim deseninin/denetim deseninin özelliği|Destek/değer|Notlar|
|-----------------------------------------------|--------------------|-----------|
|<xref:System.Windows.Automation.Provider.ITextProvider>|Şekline|Ayrıntılı metin bilgileri her zaman istemciler için kullanılabilir olması gerektiğinden, düzenleme denetimleri metin denetim modelini desteklemelidir.|
|<xref:System.Windows.Automation.Provider.IValueProvider>|Şekline|Bir dize alan tüm düzenleme denetimleri değer modelini kullanıma sunmalıdır.|
|<xref:System.Windows.Automation.Provider.IValueProvider.IsReadOnly%2A>|Notlara bakın.|Bu özellik, denetimin bir değer olarak ayarlanmış veya Kullanıcı tarafından düzenlenebilir olup olmayacağını belirtmek için ayarlanmalıdır.|
|<xref:System.Windows.Automation.Provider.IValueProvider.Value%2A>|Notlara bakın.|Bu özellik, düzenleme denetiminin metin içeriğini döndürür. , `IsPasswordProperty` Olarak ayarlandıysa `true` , bu özellik istendiğinde bir değer vermelidir `InvalidOperationException` .|
|<xref:System.Windows.Automation.Provider.IRangeValueProvider>|Şekline|Sayısal bir Aralık alan tüm düzenleme denetimleri, Aralık değeri denetim modelini kullanıma sunmalıdır.|
|<xref:System.Windows.Automation.Provider.IRangeValueProvider.Minimum%2A>|Notlara bakın.|Bu özellik, düzenleme denetiminin içeriğinin ayarlayabilmesi için en küçük değer olmalıdır.|
|<xref:System.Windows.Automation.Provider.IRangeValueProvider.Maximum%2A>|Notlara bakın.|Bu özellik, düzenleme denetimi içeriğinin ayarlandığı en büyük değer olmalıdır.|
|<xref:System.Windows.Automation.Provider.IRangeValueProvider.SmallChange%2A>|Notlara bakın.|Bu özellik, değerin ayarlanabileceği ondalık basamak sayısını belirtmelidir. Düzenleme yalnızca tamsayı al ise, 1 olmalıdır `SmallChangeProperty` . Düzenleme 1,0 ile 2,0 arasında bir Aralık alırsa, bu, 0,1 olmalıdır `SmallChangeProperty` . Düzenleme denetimi 1,00 ile 2,00 arasında bir Aralık alırsa, bu, `SmallChangeProperty` 0,001 olmalıdır.|
|<xref:System.Windows.Automation.Provider.IRangeValueProvider.LargeChange%2A>|`Null`|Bu özelliğin bir düzenleme denetiminde açığa çıkarılması gerekmez.|
|<xref:System.Windows.Automation.Provider.IRangeValueProvider.Value%2A>|Notlara bakın.|Bu özellik, düzenleme denetiminin sayısal içeriğini gösterir. Ve özelliklerinde belirtilen aralıklar içindeki bir istemci tarafından daha kesin bir değer ayarlandığında [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] `Minimum` `Maximum` , Value özelliği otomatik olarak en yakın kabul edilen değere yuvarlanır.|

<a name="Required_UI_Automation_Events"></a>

## <a name="required-ui-automation-events"></a>Gerekli UI Otomasyon olayları

Aşağıdaki tabloda, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tüm düzenleme denetimleri tarafından desteklenmesi gereken olaylar listelenmektedir. Olaylar hakkında daha fazla bilgi için bkz. [UI Otomasyonu olaylarına genel bakış](ui-automation-events-overview.md).

|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Olay|Destek|Notlar|
|---------------------------------------------------------------------------------|-------------|-----------|
|<xref:System.Windows.Automation.SelectionPatternIdentifiers.InvalidatedEvent>|Gerekli|Hiçbiri|
|<xref:System.Windows.Automation.TextPatternIdentifiers.TextSelectionChangedEvent>|Gerekli|Hiçbiri|
|<xref:System.Windows.Automation.TextPatternIdentifiers.TextChangedEvent>|Gerekli|Hiçbiri|
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>özellik değişti olayı.|Gerekli|Hiçbiri|
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsOffscreenProperty>özellik değişti olayı.|Gerekli|Hiçbiri|
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsEnabledProperty>özellik değişti olayı.|Gerekli|Hiçbiri|
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>özellik değişti olayı.|Gerekli|Hiçbiri|
|<xref:System.Windows.Automation.ValuePatternIdentifiers.ValueProperty>özellik değişti olayı.|Şekline|Hiçbiri|
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontallyScrollableProperty>özellik değişti olayı.|Asla|Hiçbiri|
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontalScrollPercentProperty>özellik değişti olayı.|Asla|Hiçbiri|
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontalViewSizeProperty>özellik değişti olayı.|Asla|Hiçbiri|
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticalScrollPercentProperty>özellik değişti olayı.|Asla|Hiçbiri|
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticallyScrollableProperty>özellik değişti olayı.|Asla|Hiçbiri|
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticalViewSizeProperty>özellik değişti olayı.|Asla|Hiçbiri|
|<xref:System.Windows.Automation.RangeValuePatternIdentifiers.ValueProperty>özellik değişti olayı.|Şekline|Denetim, Aralık değeri denetim modelini destekliyorsa, bu olayı desteklemelidir.|
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationFocusChangedEvent>|Gerekli|Hiçbiri|
|<xref:System.Windows.Automation.AutomationElementIdentifiers.StructureChangedEvent>|Gerekli|Hiçbiri|

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Automation.ControlType.Edit>
- [UI Otomasyon Denetim Türlerine Genel Bakış](ui-automation-control-types-overview.md)
- [UI Otomasyonuna Genel Bakış](ui-automation-overview.md)
