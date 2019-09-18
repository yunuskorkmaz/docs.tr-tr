---
title: MenuItem Denetim Türü için UI Otomasyon Desteği
ms.date: 03/30/2017
helpviewer_keywords:
- control types, Menu Item
- Menu Item control type
- UI Automation, Menu Item control type
ms.assetid: 54bce311-3d23-40b9-ba90-1bdbdaf8fbba
ms.openlocfilehash: a1dba653a308bc4fa865e8ee362893cbd15d68da
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71041284"
---
# <a name="ui-automation-support-for-the-menuitem-control-type"></a>MenuItem Denetim Türü için UI Otomasyon Desteği

> [!NOTE]
> Bu belge, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] <xref:System.Windows.Automation> ad alanında tanımlanan yönetilen sınıfları kullanmak isteyen .NET Framework geliştiricilere yöneliktir. Hakkında [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]en son bilgiler için bkz [. Windows Otomasyonu API 'si: UI Otomasyonu](https://go.microsoft.com/fwlink/?LinkID=156746).

Bu konuda, MenuItem denetim [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] türü için destek hakkında bilgi sağlanır. Denetimin [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] ağaç yapısını açıklar ve MenuItem denetim türü için gereken özellikleri ve denetim desenlerini sağlar.

Bir menü denetimi, komutlarla ve olay işleyicileriyle ilişkili öğelerin hiyerarşik kuruluşunun oluşturulmasına olanak sağlar. Tipik [!INCLUDE[TLA#tla_win](../../../includes/tlasharptla-win-md.md)] bir uygulamada, bir menü çubuğu birkaç menü öğesi (örneğin, **Dosya**, **düzenleme**ve **pencere**) içerir ve her menü öğesi bir menü görüntüler. Bir menü, ek menü öğelerini göstermek veya tıklandığında belirli bir eylem gerçekleştirmek üzere genişletilebilen bir menü öğeleri ( **New**, **Open**ve **Close**gibi) koleksiyonunu içerir. Bir menü öğesi bir menü, menü çubuğu veya araç çubuğunda barındırılabilir.

Aşağıdaki bölümler, MenuItem denetim türü [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] için gerekli ağaç yapısını, özellikleri, denetim desenlerini ve olayları tanımlar. Gereksinimler,, [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)]veya [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)] şeklinde[!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)]tüm liste denetimleri için geçerlidir. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]

<a name="Required_UI_Automation_Tree_Structure"></a>

## <a name="required-ui-automation-tree-structure"></a>Gerekli UI Otomasyonu ağaç yapısı

Aşağıdaki tabloda, menü öğesi denetimleriyle ilgili [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağacın denetim görünümü ve içerik görünümü gösterilmektedir ve her görünümde nelerin yer aldığı açıklanmaktadır. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Ağaç hakkında daha fazla bilgi için bkz. [UI Otomasyon ağacına genel bakış](ui-automation-tree-overview.md).

|Denetim görünümü|İçerik görünümü|
|------------------|------------------|
|MenuItem "yardım"<br /><br /> <ul><li>Menü (Yardım menü öğesinin alt menüsü)<br /><br /> <ul><li>MenuItem "Yardım konuları"</li><li>MenuItem "Not defteri"</li></ul></li></ul>|MenuItem "yardım"<br /><br /> -MenuItem "Yardım konuları"<br />-MenuItem "Not defteri hakkında"|

Menü öğesi denetiminin denetim görünümü yukarıda gösterilen [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağaç yapısına sahiptir. Alt menü hiyerarşisinin tipik bir menüsünde yapıyı daha iyi göstermek için **Yardım** menüsü öğesinin dahil edildiğini unutmayın.

İçerik görünümü için, bir menü, son kullanıcıya anlamlı [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] bilgiler iletmediğinden ağaçta yok.

<a name="Required_UI_Automation_Properties"></a>

## <a name="required-ui-automation-properties"></a>Gerekli UI Otomasyon Özellikleri

Aşağıdaki tabloda, değeri veya [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tanımı özellikle menü öğesi denetimleriyle ilgili olan özellikler listelenmiştir. Özellikler hakkında [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] daha fazla bilgi için bkz. [istemciler için UI Otomasyon özellikleri](ui-automation-properties-for-clients.md).

|Özellik|Değer|Açıklama|
|--------------|-----------|-----------------|
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationIdProperty>|Notlara bakın.|Bu özelliğin değerinin bir uygulamadaki tüm denetimlerde benzersiz olması gerekir.|
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>|Notlara bakın.|Tüm denetimi içeren en dıştaki dikdörtgen.|
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ClickablePointProperty>|Notlara bakın.|Sınırlayıcı bir dikdörtgen varsa desteklenir. Sınırlayıcı dikdörtgenin içindeki her nokta tıklatılabilir ise ve özelleştirilmiş isabet testi gerçekleştirirseniz ve ardından tıklatılabilir bir nokta sağlayabilirsiniz.|
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsKeyboardFocusableProperty>|Notlara bakın.|Denetim, klavye odağı alamıyorsa, bu özelliği desteklemesi gerekir.|
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>|Notlara bakın.|Menü öğesi denetimi [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağacın içerik görünümüne dahildir ve bir adla kendi kendine etiketlidir.|
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LabeledByProperty>|`Null`|Etiket yok.|
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ControlTypeProperty>|MenuItem|Bu değer tüm UI çerçeveleri için aynıdır.|
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LocalizedControlTypeProperty>|"menü öğesi"|MenuItem denetim türüne karşılık gelen yerelleştirilmiş dize.|
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsContentElementProperty>|Doğru|Menü öğesi denetimi, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağacın içerik görünümüne hiçbir daha dahil değildir.|
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsControlElementProperty>|Doğru|Menü öğesi denetimi her zaman [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağacın denetim görünümüne eklenmelidir.|

<a name="Required_UI_Automation_Control_Patterns"></a>

## <a name="required-ui-automation-control-patterns"></a>Gerekli UI Otomasyonu Denetim desenleri

Aşağıdaki tabloda, menü öğesi [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] denetimleri tarafından desteklenmesi gereken denetim desenleri listelenmektedir. Denetim desenleri hakkında daha fazla bilgi için bkz. [UI Otomasyonu Denetim desenlerine genel bakış](ui-automation-control-patterns-overview.md).

|Denetim deseninin özelliği|Destek|Notlar|
|------------------------------|-------------|-----------|
|<xref:System.Windows.Automation.Provider.IExpandCollapseProvider>|Şekline|Denetim genişletilebilir veya daraltılabilse, uygulayın <xref:System.Windows.Automation.Provider.IExpandCollapseProvider>.|
|<xref:System.Windows.Automation.Provider.IInvokeProvider>|Şekline|Denetim tek bir eylem veya komut çalıştırırsa, uygulayın <xref:System.Windows.Automation.Provider.IInvokeProvider>.|
|<xref:System.Windows.Automation.Provider.IToggleProvider>|Şekline|Denetim açık veya kapalı olabilecek bir seçeneği temsil ediyorsa, uygulayın <xref:System.Windows.Automation.Provider.IToggleProvider>.|
|<xref:System.Windows.Automation.Provider.ISelectionItemProvider>|Şekline|Denetim, menü öğeleri arasındaki seçenekler listesinden seçim yapmak için kullanılırsa, uygulayın <xref:System.Windows.Automation.Provider.ISelectionItemProvider>.|

<a name="UI_Automation_Events_for_Menu_Item"></a>

## <a name="ui-automation-events-for-menu-item"></a>Menü öğesi için UI Otomasyon olayları

Aşağıdaki tabloda, menü öğesi [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] denetimiyle ilişkili olaylar listelenmektedir.

|Olay|Destek|Açıklama|
|-----------|-------------|-----------------|
|<xref:System.Windows.Automation.InvokePatternIdentifiers.InvokedEvent>|Şekline|Denetim, denetim deseninin çağrılmasını destekliyorsa oluşturulmalıdır.|
|<xref:System.Windows.Automation.TogglePatternIdentifiers.ToggleStateProperty>özellik değişti olayı.|Şekline|Denetim Iki durumlu denetim düzenine destekliyorsa, oluşturulmalıdır.|
|<xref:System.Windows.Automation.ExpandCollapsePatternIdentifiers.ExpandCollapseStateProperty>özellik değişti olayı.|Şekline|Denetim, Genişlet denetim stilini destekliyorsa, bunun oluşturulması gerekir.|
|<xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementSelectedEvent>|Şekline|Yok.|

<a name="Required_UI_Automation_Events"></a>

## <a name="required-ui-automation-events"></a>Gerekli UI Otomasyon olayları

Aşağıdaki tabloda, tüm menü [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] öğesi denetimleri tarafından desteklenmesi gereken olaylar listelenmektedir. Olaylar hakkında daha fazla bilgi için bkz. [UI Otomasyonu olaylarına genel bakış](ui-automation-events-overview.md).

|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Olay|Destek/değer|Notlar|
|---------------------------------------------------------------------------------|--------------------|-----------|
|<xref:System.Windows.Automation.InvokePatternIdentifiers.InvokedEvent>|Şekline|Yok.|
|<xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementAddedToSelectionEvent>|Şekline|Yok.|
|<xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementRemovedFromSelectionEvent>|Şekline|Yok.|
|<xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementSelectedEvent>|Şekline|Yok.|
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>özellik değişti olayı.|Gerekli|Yok.|
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsOffscreenProperty>özellik değişti olayı.|Gerekli|Yok.|
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsEnabledProperty>özellik değişti olayı.|Gerekli|Yok.|
|<xref:System.Windows.Automation.ExpandCollapsePatternIdentifiers.ExpandCollapseStateProperty>özellik değişti olayı.|Şekline|Yok.|
|<xref:System.Windows.Automation.TogglePatternIdentifiers.ToggleStateProperty>özellik değişti olayı.|Şekline|Yok.|
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationFocusChangedEvent>|Gerekli|Yok.|
|<xref:System.Windows.Automation.AutomationElementIdentifiers.StructureChangedEvent>|Gerekli|Yok.|

<a name="Legacy_Issues"></a>

## <a name="legacy-issues"></a>Eski sorunlar

Değiştirme stili yalnızca [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)] menü öğesi işaretlendiğinde ve geçiş modelini desteklemek için program aracılığıyla gerekli olarak belirlenebileceği şekilde desteklenecektir. [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)] Menü öğesi, denetlenecek özelliği olup olmadığını göstermediğinden, menü öğesi işaretlenmediği zaman Invoke deseninin desteklenecek olması gerekir. Yalnızca geçiş modelini destekleyen menü öğeleri için de her zaman çağırma modelini desteklemek için bir özel durum oluşturulur. Bu sayede istemciler, çağırma modelini destekleyen bir öğenin (menü öğesi işaretlenmediği zaman), bir kez işaretlendikten sonra stili artık desteklemediği için karıştırılır.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Automation.ControlType.MenuItem>
- [UI Otomasyonu Denetim Desenlerine Genel Bakış](ui-automation-control-patterns-overview.md)
- [UI Otomasyonu Denetim Türlerine Genel Bakış](ui-automation-control-types-overview.md)
- [UI Otomasyonuna Genel Bakış](ui-automation-overview.md)
