---
title: UI Otomasyon Özelliklerine Genel Bakış
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, properties
- properties, UI Automation
ms.assetid: a6c31d7b-b33e-49b3-b5c1-31a345f9b7c8
ms.openlocfilehash: 8a44fd89017002ae51d9b15a22bac97668d0ff90
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179863"
---
# <a name="ui-automation-properties-overview"></a>UI Otomasyon Özelliklerine Genel Bakış
> [!NOTE]
> Bu dokümantasyon, ad alanında tanımlanan yönetilen [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] sınıfları kullanmak <xref:System.Windows.Automation> isteyen .NET Framework geliştiricileri için tasarlanmıştır. Hakkında en son [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]bilgi için [Bkz. Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).  
  
 UI Otomasyon sağlayıcıları, [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] öğeler üzerindeki özellikleri ortaya çıkarır. Bu özellikler, Kullanıcı Birsonucu Otomasyon istemci [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)]uygulamalarının, statik ve dinamik veriler de dahil olmak üzere, özellikle denetimlerin parçaları hakkında bilgi keşfetmesini sağlar.  
  
 Bu bölümde [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] özellikleri geniş bir genel bakış sağlar. Daha ayrıntılı bilgi aşağıdaki konularda verilmiştir:  
  
- [İstemciler İçin UI Otomasyonu Özellikleri](ui-automation-properties-for-clients.md)  
  
- [Sunucu Tarafı UI Otomasyonu Sağlayıcıyı Uygulama](server-side-ui-automation-provider-implementation.md)  
  
<a name="Property_Identifiers"></a>
## <a name="property-identifiers"></a>Özellik Tanımlayıcıları  
 Her özellik bir sayı ve bir ad ile tanımlanır. Özelliklerin adları yalnızca hata ayıklama ve tanı için kullanılır. Sağlayıcılar, gelen özellik isteklerini tanımlamak için sayısal kimliklerini kullanır. Ancak istemci uygulamaları, yalnızca <xref:System.Windows.Automation.AutomationProperty>almak istedikleri özellikleri tanımlamak için numarayı ve adı kapsülleyen kişileri kullanır.  
  
 <xref:System.Windows.Automation.AutomationProperty>belirli özellikleri temsil eden nesneler çeşitli sınıflarda alanlar olarak kullanılabilir. Güvenlik nedenleriyle, UI Automation sağlayıcıları bu nesneleri Uiautomationtypes.dll'de bulunan ayrı bir sınıf kümesinden elde eder.  
  
 Aşağıdaki tablo, <xref:System.Windows.Automation.AutomationProperty>özellikleri, disleri içeren sınıflara göre kategorilere ayırıyor.  
  
|Özellik türleri|Müşteriler,|Sağlayıcılar,|  
|-------------------------|--------------------------|----------------------------|  
|Tüm öğeleriçin ortak özellikler (aşağıdaki tablolara bakın)|<xref:System.Windows.Automation.AutomationElement>|<xref:System.Windows.Automation.AutomationElementIdentifiers>|  
|Yerleştirme penceresinin konumu|<xref:System.Windows.Automation.DockPattern>|<xref:System.Windows.Automation.DockPatternIdentifiers>|  
|Genişletilebilen ve çökebilen bir öğenin durumu|<xref:System.Windows.Automation.ExpandCollapsePattern>|<xref:System.Windows.Automation.ExpandCollapsePatternIdentifiers>|  
|Bir maddenin ızgaradaki özellikleri|<xref:System.Windows.Automation.GridItemPattern>|<xref:System.Windows.Automation.GridItemPatternIdentifiers>|  
|Bir ızgaranın özellikleri|<xref:System.Windows.Automation.GridPattern>|<xref:System.Windows.Automation.GridPatternIdentifiers>|  
|Birden çok görünüme sahip bir öğenin geçerli ve desteklenen görünümü|<xref:System.Windows.Automation.MultipleViewPattern>|<xref:System.Windows.Automation.MultipleViewPatternIdentifiers>|  
|Kaydırıcı gibi bir değer aralığı üzerinde hareket eden bir öğenin özellikleri|<xref:System.Windows.Automation.RangeValuePattern>|<xref:System.Windows.Automation.RangeValuePatternIdentifiers>|  
|Kaydırma penceresinin özellikleri|<xref:System.Windows.Automation.ScrollPattern>|<xref:System.Windows.Automation.ScrollPatternIdentifiers>|  
|Listedeki gibi seçilebilen bir öğenin durumu ve kapsayıcısı|<xref:System.Windows.Automation.SelectionItemPattern>|<xref:System.Windows.Automation.SelectionItemPatternIdentifiers>|  
|Seçim öğelerini içeren denetimin özellikleri|<xref:System.Windows.Automation.SelectionPattern>|<xref:System.Windows.Automation.SelectionPatternIdentifiers>|  
|Tablodaki bir öğenin sütun ve satır üstbilgi|<xref:System.Windows.Automation.TableItemPattern>|<xref:System.Windows.Automation.TableItemPatternIdentifiers>|  
|Tablonun sütun ve satır üstbilgi ve yönlendirmesi|<xref:System.Windows.Automation.TablePattern>|<xref:System.Windows.Automation.TablePatternIdentifiers>|  
|Geçiş denetiminin durumu|<xref:System.Windows.Automation.TogglePattern>|<xref:System.Windows.Automation.TogglePatternIdentifiers>|  
|Taşınabilen, döndürülebilen veya yeniden boyutlandırılabilen bir öğenin yetenekleri|<xref:System.Windows.Automation.TransformPattern>|<xref:System.Windows.Automation.TransformPatternIdentifiers>|  
|Değeri olan bir öğenin değer ve okuma/yazma yetenekleri|<xref:System.Windows.Automation.ValuePattern>|<xref:System.Windows.Automation.ValuePatternIdentifiers>|  
|Bir pencerenin özellikleri ve durumu|<xref:System.Windows.Automation.WindowPattern>|<xref:System.Windows.Automation.WindowPatternIdentifiers>|  
  
<a name="Properties_by_Category"></a>
## <a name="properties-by-category"></a>Kategoriye Göre Özellikler  
 Aşağıdaki tablolar, <xref:System.Windows.Automation.AutomationElement> kimlikleri bulunan özellikleri kategorilere <xref:System.Windows.Automation.AutomationElementIdentifiers>ayırın ve . Bu özellikler tüm denetimler için ortaktadır. Bunların birkaçı hariç hepsi sağlayıcı uygulamanın ömrü boyunca statik olma olasılığı yüksektir; çoğu dinamik özellik denetim desenleri ile ilişkilidir.  
  
 **Özellik Erişim** sütunu, her özellik için diğer erişimcileri listeler, buna ek olarak <xref:System.Windows.Automation.AutomationElement.GetCurrentPropertyValue%2A> ve <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A>. İstemci uygulamasında özellikleri alma hakkında daha fazla bilgi [için, Istemciler için Kullanıcı Arabirimi Otomasyon Özellikleri'ne](ui-automation-properties-for-clients.md)bakın.  
  
> [!NOTE]
> Her özellik hakkında belirli bilgiler **için, Özellik Erişimi** sütunundaki bağlantıyı izleyin.  
  
### <a name="display-characteristics"></a>Görüntü Özellikleri  
  
|Özellik tanımlayıcısı|Özellik erişimi|  
|-------------------------|---------------------|  
|<xref:System.Windows.Automation.AutomationElement.BoundingRectangleProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.BoundingRectangle%2A>|  
|<xref:System.Windows.Automation.AutomationElement.CultureProperty>|yok|  
|<xref:System.Windows.Automation.AutomationElement.HelpTextProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.HelpText%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsOffscreenProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsOffscreen%2A>|  
|<xref:System.Windows.Automation.AutomationElement.OrientationProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Orientation%2A>|  
  
### <a name="element-type"></a>Eleman Türü  
  
|Özellik tanımlayıcısı|Özellik erişimi|  
|-------------------------|---------------------|  
|<xref:System.Windows.Automation.AutomationElement.ControlTypeProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.ControlType%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsContentElementProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsContentElement%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsControlElementProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsControlElement%2A>|  
|<xref:System.Windows.Automation.AutomationElement.ItemTypeProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.ItemType%2A>|  
|<xref:System.Windows.Automation.AutomationElement.LocalizedControlTypeProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.LocalizedControlType%2A>|  
  
### <a name="identification"></a>Kimlik  
  
|Özellik tanımlayıcısı|Özellik erişimi|  
|-------------------------|---------------------|  
|<xref:System.Windows.Automation.AutomationElement.AutomationIdProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.AutomationId%2A>|  
|<xref:System.Windows.Automation.AutomationElement.ClassNameProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.ClassName%2A>|  
|<xref:System.Windows.Automation.AutomationElement.FrameworkIdProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.FrameworkId%2A>|  
|<xref:System.Windows.Automation.AutomationElement.LabeledByProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.LabeledBy%2A>|  
|<xref:System.Windows.Automation.AutomationElement.NameProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Name%2A>|  
|<xref:System.Windows.Automation.AutomationElement.ProcessIdProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.ProcessId%2A>|  
|<xref:System.Windows.Automation.AutomationElement.RuntimeIdProperty>|<xref:System.Windows.Automation.AutomationElement.GetRuntimeId%2A>|  
|<xref:System.Windows.Automation.AutomationElement.NativeWindowHandleProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.NativeWindowHandle%2A>|  
  
### <a name="interaction"></a>Etkileşim  
  
|Özellik tanımlayıcısı|Özellik erişimi|  
|-------------------------|---------------------|  
|<xref:System.Windows.Automation.AutomationElement.AcceleratorKeyProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.AcceleratorKey%2A>|  
|<xref:System.Windows.Automation.AutomationElement.AccessKeyProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.AccessKey%2A>|  
|<xref:System.Windows.Automation.AutomationElement.ClickablePointProperty>|<xref:System.Windows.Automation.AutomationElement.GetClickablePoint%2A>|  
|<xref:System.Windows.Automation.AutomationElement.HasKeyboardFocusProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.HasKeyboardFocus%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsEnabledProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsEnabled%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsKeyboardFocusableProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsKeyboardFocusable%2A>|  
  
### <a name="support-for-patterns"></a>Desenler için Destek  
  
|Özellik tanımlayıcısı|Özellik erişimi|  
|-------------------------|---------------------|  
|<xref:System.Windows.Automation.AutomationElement.IsDockPatternAvailableProperty>|<xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsExpandCollapsePatternAvailableProperty>|<xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsGridItemPatternAvailableProperty>|<xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsGridPatternAvailableProperty>|<xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsInvokePatternAvailableProperty>|<xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsMultipleViewPatternAvailableProperty>|<xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsRangeValuePatternAvailableProperty>|<xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsScrollItemPatternAvailableProperty>|<xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsScrollPatternAvailableProperty>|<xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsSelectionItemPatternAvailableProperty>|<xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsSelectionPatternAvailableProperty>|<xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsTableItemPatternAvailableProperty>|<xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsTablePatternAvailableProperty>|<xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsTextPatternAvailableProperty>|<xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsTogglePatternAvailableProperty>|<xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsTransformPatternAvailableProperty>|<xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsValuePatternAvailableProperty>|<xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsWindowPatternAvailableProperty>|<xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>|  
  
### <a name="miscellaneous"></a>Çeşitli  
  
|Özellik tanımlayıcısı|Özellik erişimi|  
|-------------------------|---------------------|  
|<xref:System.Windows.Automation.AutomationElement.IsRequiredForFormProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsRequiredForForm%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsPasswordProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsPassword%2A>|  
|<xref:System.Windows.Automation.AutomationElement.ItemStatusProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.ItemStatus%2A>|  
  
<a name="Localization"></a>
## <a name="localization"></a>Yerelleştirme  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]sağlayıcılar işletim sisteminin dilinde aşağıdaki özellikleri sunmalıdır:  
  
- <xref:System.Windows.Automation.AutomationElementIdentifiers.AcceleratorKeyProperty>  
  
- <xref:System.Windows.Automation.AutomationElementIdentifiers.AccessKeyProperty>  
  
- <xref:System.Windows.Automation.AutomationElementIdentifiers.HelpTextProperty>  
  
- <xref:System.Windows.Automation.AutomationElementIdentifiers.LocalizedControlTypeProperty>  
  
- <xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>  
  
<a name="Properties_and_Events"></a>
## <a name="properties-and-events"></a>Özellikler ve Etkinlikler  
 Mülkiyetin değişmesi ile yakından [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] bağlantılı olan olaylar kavramıdır. Dinamik özellikler için istemci uygulamasının, bilgi önbelleğini güncelleştirebilmesi veya yeni bilgilere başka bir şekilde tepki verebilmesi için özellik değerinin değiştiğini bilmek için bir yol gerekir.  
  
 [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] Sağlayıcılar, değişikliklerde bir şey olduğunda olayları yükseltir. Örneğin, bir onay kutusu seçilir veya temizlenirse, sağlayıcının Geçiş deseni uygulaması tarafından özellik değiştirilen bir olay yükseltilir. Sağlayıcılar, herhangi bir istemcinin olayları dinlediğine veya belirli olayları dinlemesine bağlı olarak etkinlikleri seçici olarak yükseltebilir.  
  
 Tüm özellik değişiklikleri olayları yükseltmek değil; bu tamamen öğe için UI Automation sağlayıcısının uygulanmasına kalmıştır. Örneğin, liste kutuları için standart proxy sağlayıcıları <xref:System.Windows.Automation.SelectionPattern.SelectionProperty> değişiklikler olduğunda bir olay yükseltmez. Bu durumda, uygulama yerine bir <xref:System.Windows.Automation.SelectionItemPattern.ElementSelectedEvent>.  
  
 Müşteriler etkinlikleri onlara abone olarak dinlerler. Olaylara abone olmak, olayları işleyebilir temsilci yöntemleri oluşturmak ve ardından [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] yöntemleri bu yöntemlerde ele alınacak belirli olaylarla birlikte geçirmek anlamına gelir. Özellikle özellik değiştirilen olaylar için istemcilerin uygulaması <xref:System.Windows.Automation.AutomationPropertyChangedEventHandler>gerekir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [UI Otomasyonu İstemcilerinde Önbelleğe Alma](caching-in-ui-automation-clients.md)
- [İstemciler İçin UI Otomasyonu Özellikleri](ui-automation-properties-for-clients.md)
- [Sunucu Tarafı UI Otomasyonu Sağlayıcıyı Uygulama](server-side-ui-automation-provider-implementation.md)
- [Özellik Koşulunu Temel Alan UI Otomasyon Öğesi Bulma](find-a-ui-automation-element-based-on-a-property-condition.md)
- [UI Otomasyonu Sağlayıcı Dönüş Özellikleri](return-properties-from-a-ui-automation-provider.md)
- [UI Otomasyonu Sağlayıcıda Olay Tetikleme](raise-events-from-a-ui-automation-provider.md)
