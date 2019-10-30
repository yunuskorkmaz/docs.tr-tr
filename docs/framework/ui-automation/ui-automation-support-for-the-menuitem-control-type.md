---
title: MenuItem Denetim Türü için UI Otomasyon Desteği
ms.date: 03/30/2017
helpviewer_keywords:
- control types, Menu Item
- Menu Item control type
- UI Automation, Menu Item control type
ms.assetid: 54bce311-3d23-40b9-ba90-1bdbdaf8fbba
ms.openlocfilehash: 5b9983dda790fbf501b055ea8e592851e61e1e89
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/29/2019
ms.locfileid: "73039424"
---
# <a name="ui-automation-support-for-the-menuitem-control-type"></a>MenuItem Denetim Türü için UI Otomasyon Desteği

> [!NOTE]
> Bu belge, <xref:System.Windows.Automation> ad alanında tanımlanan yönetilen [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] sınıflarını kullanmak isteyen .NET Framework geliştiricilere yöneliktir. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]hakkında en son bilgiler için bkz. [Windows Otomasyonu API: UI Otomasyonu](https://go.microsoft.com/fwlink/?LinkID=156746).

Bu konu, MenuItem denetim türü için [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] desteği hakkında bilgi sağlar. Denetimin [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] ağaç yapısını açıklar ve MenuItem denetim türü için gereken özellikleri ve denetim desenlerini sağlar.

Bir menü denetimi, komutlarla ve olay işleyicileriyle ilişkili öğelerin hiyerarşik kuruluşunun oluşturulmasına olanak sağlar. Tipik bir Microsoft Windows uygulamasında, bir menü çubuğu birçok menü öğesi (örneğin, **Dosya**, **düzenleme**ve **pencere**) içerir ve her menü öğesi bir menü görüntüler. Bir menü, ek menü öğelerini göstermek veya tıklandığında belirli bir eylem gerçekleştirmek üzere genişletilebilen bir menü öğeleri ( **New**, **Open**ve **Close**gibi) koleksiyonunu içerir. Bir menü öğesi bir menü, menü çubuğu veya araç çubuğunda barındırılabilir.

Aşağıdaki bölümler, MenuItem denetim türü için gerekli [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağaç yapısını, özellikleri, denetim desenlerini ve olayları tanımlar. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] gereksinimler, [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)], [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)]veya [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)]bakılmaksızın tüm liste denetimleri için geçerlidir.

<a name="Required_UI_Automation_Tree_Structure"></a>

## <a name="required-ui-automation-tree-structure"></a>Gerekli UI Otomasyonu ağaç yapısı

Aşağıdaki tabloda, menü öğesi denetimleriyle ilgili [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağacının denetim görünümü ve içerik görünümü gösterilmektedir ve her görünümde nelerin yer aldığı açıklanmaktadır. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağacı hakkında daha fazla bilgi için bkz. [UI Otomasyon ağacına genel bakış](ui-automation-tree-overview.md).

|Denetim görünümü|İçerik görünümü|
|------------------|------------------|
|MenuItem "yardım"<br /><br /> <ul><li>Menü (Yardım menü öğesinin alt menüsü)<br /><br /> <ul><li>MenuItem "Yardım konuları"</li><li>MenuItem "Not defteri"</li></ul></li></ul>|MenuItem "yardım"<br /><br /> -MenuItem "Yardım konuları"<br />-MenuItem "Not defteri hakkında"|

Menü öğesi denetiminin denetim görünümü yukarıda gösterilen [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağaç yapısına sahiptir. Alt menü hiyerarşisinin tipik bir menüsünde yapıyı daha iyi göstermek için **Yardım** menüsü öğesinin dahil edildiğini unutmayın.

İçerik görünümü için, son kullanıcıya anlamlı bilgiler iletmediğinden [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağaçta menü yok.

<a name="Required_UI_Automation_Properties"></a>

## <a name="required-ui-automation-properties"></a>Gerekli UI Otomasyon Özellikleri

Aşağıdaki tabloda, değeri veya tanımı özellikle menü öğesi denetimleriyle ilgili olan [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] özellikleri listelenmektedir. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] özellikleri hakkında daha fazla bilgi için bkz. [istemciler Için UI Otomasyon özellikleri](ui-automation-properties-for-clients.md).

|Özellik|Değer|Açıklama|
|--------------|-----------|-----------------|
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationIdProperty>|Notlara bakın.|Bu özelliğin değerinin bir uygulamadaki tüm denetimlerde benzersiz olması gerekir.|
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>|Notlara bakın.|Tüm denetimi içeren en dıştaki dikdörtgen.|
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ClickablePointProperty>|Notlara bakın.|Sınırlayıcı bir dikdörtgen varsa desteklenir. Sınırlayıcı dikdörtgenin içindeki her nokta tıklatılabilir ise ve özelleştirilmiş isabet testi gerçekleştirirseniz ve ardından tıklatılabilir bir nokta sağlayabilirsiniz.|
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsKeyboardFocusableProperty>|Notlara bakın.|Denetim, klavye odağı alamıyorsa, bu özelliği desteklemesi gerekir.|
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>|Notlara bakın.|Menü öğesi denetimi, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağacının içerik görünümüne dahildir ve kendi kendine bir adla etiketlidir.|
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LabeledByProperty>|`Null`|Etiket yok.|
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ControlTypeProperty>|MenuItem|Bu değer tüm UI çerçeveleri için aynıdır.|
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LocalizedControlTypeProperty>|"menü öğesi"|MenuItem denetim türüne karşılık gelen yerelleştirilmiş dize.|
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsContentElementProperty>|Doğru|Menü öğesi denetimi, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağacının içerik görünümüne hiçbir şekilde dahil değildir.|
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsControlElementProperty>|Doğru|Menü öğesi denetimi her zaman [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağacının denetim görünümüne eklenmelidir.|

<a name="Required_UI_Automation_Control_Patterns"></a>

## <a name="required-ui-automation-control-patterns"></a>Gerekli UI Otomasyonu Denetim desenleri

Aşağıdaki tabloda, menü öğesi denetimleri tarafından desteklenmesi gereken [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Denetim desenleri listelenmektedir. Denetim desenleri hakkında daha fazla bilgi için bkz. [UI Otomasyonu Denetim desenlerine genel bakış](ui-automation-control-patterns-overview.md).

|Denetim deseninin özelliği|Destek|Notlar|
|------------------------------|-------------|-----------|
|<xref:System.Windows.Automation.Provider.IExpandCollapseProvider>|Şekline|Denetim genişletilebilir veya daraltılabilse <xref:System.Windows.Automation.Provider.IExpandCollapseProvider>uygulayın.|
|<xref:System.Windows.Automation.Provider.IInvokeProvider>|Şekline|Denetim tek bir eylem veya komut çalıştırırsa <xref:System.Windows.Automation.Provider.IInvokeProvider>uygulayın.|
|<xref:System.Windows.Automation.Provider.IToggleProvider>|Şekline|Denetim açılabilir veya kapatılabilir bir seçeneği temsil ediyorsa, <xref:System.Windows.Automation.Provider.IToggleProvider>uygulayın.|
|<xref:System.Windows.Automation.Provider.ISelectionItemProvider>|Şekline|Denetim, menü öğeleri arasındaki seçenekler listesinden seçim yapmak için kullanılıyorsa, <xref:System.Windows.Automation.Provider.ISelectionItemProvider>uygulayın.|

<a name="UI_Automation_Events_for_Menu_Item"></a>

## <a name="ui-automation-events-for-menu-item"></a>Menü öğesi için UI Otomasyon olayları

Aşağıdaki tabloda, menü öğesi denetimiyle ilişkili [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] olayları listelenmektedir.

|Olay|Destek|Açıklama|
|-----------|-------------|-----------------|
|<xref:System.Windows.Automation.InvokePatternIdentifiers.InvokedEvent>|Şekline|Denetim, denetim deseninin çağrılmasını destekliyorsa oluşturulmalıdır.|
|özellik değişti olayı <xref:System.Windows.Automation.TogglePatternIdentifiers.ToggleStateProperty>.|Şekline|Denetim Iki durumlu denetim düzenine destekliyorsa, oluşturulmalıdır.|
|özellik değişti olayı <xref:System.Windows.Automation.ExpandCollapsePatternIdentifiers.ExpandCollapseStateProperty>.|Şekline|Denetim, Genişlet denetim stilini destekliyorsa, bunun oluşturulması gerekir.|
|<xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementSelectedEvent>|Şekline|Yok.|

<a name="Required_UI_Automation_Events"></a>

## <a name="required-ui-automation-events"></a>Gerekli UI Otomasyon olayları

Aşağıdaki tabloda, tüm menü öğesi denetimleri tarafından desteklenmesi gereken [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] olayları listelenmektedir. Olaylar hakkında daha fazla bilgi için bkz. [UI Otomasyonu olaylarına genel bakış](ui-automation-events-overview.md).

|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] olayı|Destek/değer|Notlar|
|---------------------------------------------------------------------------------|--------------------|-----------|
|<xref:System.Windows.Automation.InvokePatternIdentifiers.InvokedEvent>|Şekline|Yok.|
|<xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementAddedToSelectionEvent>|Şekline|Yok.|
|<xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementRemovedFromSelectionEvent>|Şekline|Yok.|
|<xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementSelectedEvent>|Şekline|Yok.|
|özellik değişti olayı <xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>.|Gerekli|Yok.|
|özellik değişti olayı <xref:System.Windows.Automation.AutomationElementIdentifiers.IsOffscreenProperty>.|Gerekli|Yok.|
|özellik değişti olayı <xref:System.Windows.Automation.AutomationElementIdentifiers.IsEnabledProperty>.|Gerekli|Yok.|
|özellik değişti olayı <xref:System.Windows.Automation.ExpandCollapsePatternIdentifiers.ExpandCollapseStateProperty>.|Şekline|Yok.|
|özellik değişti olayı <xref:System.Windows.Automation.TogglePatternIdentifiers.ToggleStateProperty>.|Şekline|Yok.|
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationFocusChangedEvent>|Gerekli|Yok.|
|<xref:System.Windows.Automation.AutomationElementIdentifiers.StructureChangedEvent>|Gerekli|Yok.|

<a name="Legacy_Issues"></a>

## <a name="legacy-issues"></a>Eski sorunlar

İki durumlu model yalnızca [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)] menü öğesi işaretlendiğinde ve geçiş modelini desteklemek için program aracılığıyla gerekli olarak belirlenebileceği şekilde desteklenecektir. [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)] menü öğesi, denetlenecek özelliği olup olmadığını göstermediğinden, menü öğesi işaretlenmediği zaman Invoke deseninin desteklenecek. Yalnızca geçiş modelini destekleyen menü öğeleri için de her zaman çağırma modelini desteklemek için bir özel durum oluşturulur. Bu sayede istemciler, çağırma modelini destekleyen bir öğenin (menü öğesi işaretlenmediği zaman), bir kez işaretlendikten sonra stili artık desteklemediği için karıştırılır.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Automation.ControlType.MenuItem>
- [UI Otomasyonu Denetim Desenlerine Genel Bakış](ui-automation-control-patterns-overview.md)
- [UI Otomasyonu Denetim Türlerine Genel Bakış](ui-automation-control-types-overview.md)
- [UI Otomasyonuna Genel Bakış](ui-automation-overview.md)
