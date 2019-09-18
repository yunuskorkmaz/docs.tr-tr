---
title: Düzenleme Denetim Türü İçin UI Otomasyon Desteği
ms.date: 03/30/2017
helpviewer_keywords:
- control types, Edit
- Edit control type
- UI Automation, Edit control type
ms.assetid: 6db9d231-c0a0-4e17-910e-ac80357f774f
ms.openlocfilehash: 5cce634e2ba80b496b808a4ec66c4c06118b5989
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71041706"
---
# <a name="ui-automation-support-for-the-edit-control-type"></a>Düzenleme Denetim Türü İçin UI Otomasyon Desteği

> [!NOTE]
> Bu belge, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] <xref:System.Windows.Automation> ad alanında tanımlanan yönetilen sınıfları kullanmak isteyen .NET Framework geliştiricilere yöneliktir. Hakkında [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]en son bilgiler için bkz [. Windows Otomasyonu API 'si: UI Otomasyonu](https://go.microsoft.com/fwlink/?LinkID=156746).

Bu konu, düzenleme denetim [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] türü için destek hakkında bilgi sağlar. ' [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]De, bir denetim türü, <xref:System.Windows.Automation.AutomationElement.ControlTypeProperty> özelliği kullanmak için bir denetimin uyması gereken koşullar kümesidir. Koşullar, ağaç yapısı, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] özellik değerleri ve Denetim desenleri için özel kurallar içerir.

Denetimleri Düzenle, bir kullanıcının zengin biçimlendirme desteği olmadan basit bir metin satırını görüntülemesini ve düzenlemesini sağlar.

Aşağıdaki bölümler, düzenleme denetim türü [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] için gerekli ağaç yapısını, özellikleri, denetim desenlerini ve olayları tanımlar. Gereksinimler,, [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)]veya [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)] şeklinde[!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)]tüm düzenleme denetimleri için geçerlidir. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]

<a name="Required_UI_Automation_Tree_Structure"></a>

## <a name="required-ui-automation-tree-structure"></a>Gerekli UI Otomasyonu ağaç yapısı

Aşağıdaki tabloda, düzenleme denetimleriyle ilgili olan [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağacın denetim görünümü ve içerik görünümü gösterilmektedir ve her görünümde nelerin yer aldığı açıklanmaktadır. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Ağaç hakkında daha fazla bilgi için bkz. [UI Otomasyon ağacına genel bakış](ui-automation-tree-overview.md).

|Denetim görünümü|İçerik görünümü|
|------------------|------------------|
|Düzenle|Düzenle|

Düzenleme denetim türünü uygulayan denetimlerin, tek satırlık bir denetim olduğu için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağacın denetim görünümünde her zaman sıfır kaydırma çubuğu olacaktır. Tek metin satırı bazı düzen senaryolarında kaydırılabilir. Düzenleme denetim türü, küçük miktarlarda düzenlenebilir veya seçilebilir metinler tutmak için idealdir.

<a name="Required_UI_Automation_Properties"></a>

## <a name="required-ui-automation-properties"></a>Gerekli UI Otomasyon Özellikleri

Aşağıdaki tabloda, değeri veya [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tanımı özellikle düzenleme denetimleriyle ilgili olan özellikler listelenmiştir. Özellikler hakkında [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] daha fazla bilgi için bkz. [istemciler için UI Otomasyon özellikleri](ui-automation-properties-for-clients.md).

|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Özelliði|Değer|Notlar|
|------------------------------------------------------------------------------------|-----------|-----------|
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationIdProperty>|Notlara bakın.|Bu özelliğin değerinin bir uygulamadaki tüm denetimlerde benzersiz olması gerekir.|
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>|Notlara bakın.|Tüm denetimi içeren en dıştaki dikdörtgen.|
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ClickablePointProperty>|Notlara bakın.|Düzenleme denetimi, kullanıcı fareyle tıkladığında, denetimin düzenleme bölümüne giriş odağı veren bir tıklatılabilir noktaya sahip olmalıdır.|
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsKeyboardFocusableProperty>|Notlara bakın.|Denetim, klavye odağı alamıyorsa, bu özelliği desteklemesi gerekir.|
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>|Notlara bakın.|Düzenleme denetiminin adı genellikle statik bir metin etiketinden oluşturulur. Statik bir metin etiketi yoksa, uygulama geliştiricisi tarafından bir özellik değeri `Name` atanmalıdır. `Name` Özelliği asla düzenleme denetiminin metin içeriğini içermemelidir.|
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LabeledByProperty>|Notlara bakın.|Denetimle ilişkili bir statik metin etiketi varsa, bu özellik bu denetimin bir başvurusunu kullanıma sunmalıdır. Metin denetimi başka bir denetimin alt bileşeni ise, bir `LabeledBy` özellik kümesine sahip olmaz.|
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ControlTypeProperty>|Düzenle|Bu değer tüm [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] çerçeveler için aynıdır.|
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LocalizedControlTypeProperty>|Düzenle|Düzenleme denetim türüne karşılık gelen yerelleştirilmiş dize.|
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsContentElementProperty>|Doğru|Düzenleme denetimi her zaman [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağacın içerik görünümüne dahil edilmiştir.|
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsControlElementProperty>|Doğru|Düzenleme denetimi her zaman [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağacın denetim görünümüne dahil edilmiştir.|
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsPasswordProperty>|Notlara bakın.|Parola içeren düzenleme denetimlerinde true olarak ayarlanmalıdır. Bir düzenleme denetimi parola içerikleri içeriyorsa, bu özellik bir ekran okuyucu tarafından Kullanıcı tarafından yazarken tuş vuruşlarının okunup okunmayacağını anlamak için kullanılabilir.|

<a name="Required_UI_Automation_Control_Patterns"></a>

## <a name="required-ui-automation-control-patterns-and-properties"></a>Gerekli UI Otomasyonu Denetim desenleri ve özellikleri

Aşağıdaki tabloda, tüm düzenleme denetimleri tarafından desteklenmesi gereken denetim desenleri listelenmektedir. Denetim desenleri hakkında daha fazla bilgi için bkz. [UI Otomasyonu Denetim desenlerine genel bakış](ui-automation-control-patterns-overview.md).

|Denetim deseninin/denetim deseninin özelliği|Destek/değer|Notlar|
|-----------------------------------------------|--------------------|-----------|
|<xref:System.Windows.Automation.Provider.ITextProvider>|Şekline|Ayrıntılı metin bilgileri her zaman istemciler için kullanılabilir olması gerektiğinden, düzenleme denetimleri metin denetim modelini desteklemelidir.|
|<xref:System.Windows.Automation.Provider.IValueProvider>|Şekline|Bir dize alan tüm düzenleme denetimleri değer modelini kullanıma sunmalıdır.|
|<xref:System.Windows.Automation.Provider.IValueProvider.IsReadOnly%2A>|Notlara bakın.|Bu özellik, denetimin bir değer olarak ayarlanmış veya Kullanıcı tarafından düzenlenebilir olup olmayacağını belirtmek için ayarlanmalıdır.|
|<xref:System.Windows.Automation.Provider.IValueProvider.Value%2A>|Notlara bakın.|Bu özellik, düzenleme denetiminin metin içeriğini döndürür. `InvalidOperationException` , Olarak `true`ayarlandıysa, bu özellik istendiğinde bir değervermelidir.`IsPasswordProperty`|
|<xref:System.Windows.Automation.Provider.IRangeValueProvider>|Şekline|Sayısal bir Aralık alan tüm düzenleme denetimleri, Aralık değeri denetim modelini kullanıma sunmalıdır.|
|<xref:System.Windows.Automation.Provider.IRangeValueProvider.Minimum%2A>|Notlara bakın.|Bu özellik, düzenleme denetiminin içeriğinin ayarlayabilmesi için en küçük değer olmalıdır.|
|<xref:System.Windows.Automation.Provider.IRangeValueProvider.Maximum%2A>|Notlara bakın.|Bu özellik, düzenleme denetimi içeriğinin ayarlandığı en büyük değer olmalıdır.|
|<xref:System.Windows.Automation.Provider.IRangeValueProvider.SmallChange%2A>|Notlara bakın.|Bu özellik, değerin ayarlanabileceği ondalık basamak sayısını belirtmelidir. Düzenleme yalnızca tamsayı `SmallChangeProperty` al ise, 1 olmalıdır. Düzenleme 1,0 ile 2,0 arasında bir Aralık alırsa, bu, `SmallChangeProperty` 0,1 olmalıdır. Düzenleme denetimi 1,00 ile 2,00 arasında bir Aralık alırsa, bu, `SmallChangeProperty` 0,001 olmalıdır.|
|<xref:System.Windows.Automation.Provider.IRangeValueProvider.LargeChange%2A>|`Null`|Bu özelliğin bir düzenleme denetiminde açığa çıkarılması gerekmez.|
|<xref:System.Windows.Automation.Provider.IRangeValueProvider.Value%2A>|Notlara bakın.|Bu özellik, düzenleme denetiminin sayısal içeriğini gösterir. `Minimum` [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Ve`Maximum` özelliklerinde belirtilen aralıklar içindeki bir istemci tarafından daha kesin bir değer ayarlandığında, Value özelliği otomatik olarak en yakın kabul edilen değere yuvarlanır.|

<a name="Required_UI_Automation_Events"></a>

## <a name="required-ui-automation-events"></a>Gerekli UI Otomasyon olayları

Aşağıdaki tabloda, tüm düzenleme [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] denetimleri tarafından desteklenmesi gereken olaylar listelenmektedir. Olaylar hakkında daha fazla bilgi için bkz. [UI Otomasyonu olaylarına genel bakış](ui-automation-events-overview.md).

|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Olay|Destek|Notlar|
|---------------------------------------------------------------------------------|-------------|-----------|
|<xref:System.Windows.Automation.SelectionPatternIdentifiers.InvalidatedEvent>|Gerekli|Yok.|
|<xref:System.Windows.Automation.TextPatternIdentifiers.TextSelectionChangedEvent>|Gerekli|Yok.|
|<xref:System.Windows.Automation.TextPatternIdentifiers.TextChangedEvent>|Gerekli|Yok.|
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>özellik değişti olayı.|Gerekli|Yok.|
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsOffscreenProperty>özellik değişti olayı.|Gerekli|Yok.|
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsEnabledProperty>özellik değişti olayı.|Gerekli|Yok.|
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>özellik değişti olayı.|Gerekli|Yok.|
|<xref:System.Windows.Automation.ValuePatternIdentifiers.ValueProperty>özellik değişti olayı.|Şekline|Yok.|
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontallyScrollableProperty>özellik değişti olayı.|hiçbir zaman|Yok.|
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontalScrollPercentProperty>özellik değişti olayı.|hiçbir zaman|Yok.|
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontalViewSizeProperty>özellik değişti olayı.|hiçbir zaman|Yok.|
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticalScrollPercentProperty>özellik değişti olayı.|hiçbir zaman|Yok.|
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticallyScrollableProperty>özellik değişti olayı.|hiçbir zaman|Yok.|
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticalViewSizeProperty>özellik değişti olayı.|hiçbir zaman|Yok.|
|<xref:System.Windows.Automation.RangeValuePatternIdentifiers.ValueProperty>özellik değişti olayı.|Şekline|Denetim, Aralık değeri denetim modelini destekliyorsa, bu olayı desteklemelidir.|
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationFocusChangedEvent>|Gerekli|Yok.|
|<xref:System.Windows.Automation.AutomationElementIdentifiers.StructureChangedEvent>|Gerekli|Yok.|

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Automation.ControlType.Edit>
- [UI Otomasyonu Denetim Türlerine Genel Bakış](ui-automation-control-types-overview.md)
- [UI Otomasyonuna Genel Bakış](ui-automation-overview.md)
