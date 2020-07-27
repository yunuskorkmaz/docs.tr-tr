---
title: MenuItem Denetim Türü için UI Otomasyon Desteği
description: MenuItem denetim türü için UI Otomasyonu desteği hakkında bilgi alın. Gerekli ağaç yapısını, özellikleri, denetim desenlerini ve olayları öğrenin.
ms.date: 03/30/2017
helpviewer_keywords:
- control types, Menu Item
- Menu Item control type
- UI Automation, Menu Item control type
ms.assetid: 54bce311-3d23-40b9-ba90-1bdbdaf8fbba
ms.openlocfilehash: 248fdacee42c3a67c6c3b2d5792b774dfdc8408f
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87166013"
---
# <a name="ui-automation-support-for-the-menuitem-control-type"></a>MenuItem Denetim Türü için UI Otomasyon Desteği

> [!NOTE]
> Bu belge, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ad alanında tanımlanan yönetilen sınıfları kullanmak isteyen .NET Framework geliştiricilere yöneliktir <xref:System.Windows.Automation> . Hakkında en son bilgiler için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] bkz. [WINDOWS Otomasyonu API: UI Otomasyonu](/windows/win32/winauto/entry-uiauto-win32).

Bu konuda [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] , MenuItem denetim türü için destek hakkında bilgi sağlanır. Denetimin [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] ağaç yapısını açıklar ve MenuItem denetim türü için gereken özellikleri ve denetim desenlerini sağlar.

Bir menü denetimi, komutlarla ve olay işleyicileriyle ilişkili öğelerin hiyerarşik kuruluşunun oluşturulmasına olanak sağlar. Tipik bir Microsoft Windows uygulamasında, bir menü çubuğu birçok menü öğesi (örneğin, **Dosya**, **düzenleme**ve **pencere**) içerir ve her menü öğesi bir menü görüntüler. Bir menü, ek menü öğelerini göstermek veya tıklandığında belirli bir eylem gerçekleştirmek üzere genişletilebilen bir menü öğeleri ( **New**, **Open**ve **Close**gibi) koleksiyonunu içerir. Bir menü öğesi bir menü, menü çubuğu veya araç çubuğunda barındırılabilir.

Aşağıdaki bölümler, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] MenuItem denetim türü için gerekli ağaç yapısını, özellikleri, denetim desenlerini ve olayları tanımlar. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Gereksinimler, Win32 veya Windows Forms tüm liste denetimleri için geçerlidir [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)] .

<a name="Required_UI_Automation_Tree_Structure"></a>

## <a name="required-ui-automation-tree-structure"></a>Gerekli UI Otomasyonu ağaç yapısı

Aşağıdaki tabloda, menü öğesi denetimleriyle ilgili ağacın denetim görünümü ve içerik görünümü gösterilmektedir [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ve her görünümde nelerin yer aldığı açıklanmaktadır. Ağaç hakkında daha fazla bilgi için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] bkz. [UI Otomasyon ağacına genel bakış](ui-automation-tree-overview.md).

|Denetim görünümü|İçerik görünümü|
|------------------|------------------|
|MenuItem "yardım"<br /><br /> <ul><li>Menü (Yardım menü öğesinin alt menüsü)<br /><br /> <ul><li>MenuItem "Yardım konuları"</li><li>MenuItem "Not defteri"</li></ul></li></ul>|MenuItem "yardım"<br /><br /> -MenuItem "Yardım konuları"<br />-MenuItem "Not defteri hakkında"|

Menü öğesi denetiminin denetim görünümü [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] yukarıda gösterilen ağaç yapısına sahiptir. Alt menü hiyerarşisinin tipik bir menüsünde yapıyı daha iyi göstermek için **Yardım** menüsü öğesinin dahil edildiğini unutmayın.

İçerik görünümü için, bir menü, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] son kullanıcıya anlamlı bilgiler iletmediğinden ağaçta yok.

<a name="Required_UI_Automation_Properties"></a>

## <a name="required-ui-automation-properties"></a>Gerekli UI Otomasyon Özellikleri

Aşağıdaki tabloda, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] değeri veya tanımı özellikle menü öğesi denetimleriyle ilgili olan özellikler listelenmiştir. Özellikler hakkında daha fazla bilgi için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] bkz. [Istemciler Için UI Otomasyon özellikleri](ui-automation-properties-for-clients.md).

|Özellik|Değer|Açıklama|
|--------------|-----------|-----------------|
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationIdProperty>|Notlara bakın.|Bu özelliğin değerinin bir uygulamadaki tüm denetimlerde benzersiz olması gerekir.|
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>|Notlara bakın.|Tüm denetimi içeren en dıştaki dikdörtgen.|
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ClickablePointProperty>|Notlara bakın.|Sınırlayıcı bir dikdörtgen varsa desteklenir. Sınırlayıcı dikdörtgenin içindeki her nokta tıklatılabilir ise ve özelleştirilmiş isabet testi gerçekleştirirseniz ve ardından tıklatılabilir bir nokta sağlayabilirsiniz.|
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsKeyboardFocusableProperty>|Notlara bakın.|Denetim, klavye odağı alamıyorsa, bu özelliği desteklemesi gerekir.|
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>|Notlara bakın.|Menü öğesi denetimi ağacın içerik görünümüne dahildir [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ve bir adla kendi kendine etiketlidir.|
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LabeledByProperty>|`Null`|Etiket yok.|
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ControlTypeProperty>|MenuItem|Bu değer tüm UI çerçeveleri için aynıdır.|
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LocalizedControlTypeProperty>|"menü öğesi"|MenuItem denetim türüne karşılık gelen yerelleştirilmiş dize.|
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsContentElementProperty>|Doğru|Menü öğesi denetimi, ağacın içerik görünümüne hiçbir daha dahil değildir [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] .|
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsControlElementProperty>|Doğru|Menü öğesi denetimi her zaman ağacın denetim görünümüne eklenmelidir [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] .|

<a name="Required_UI_Automation_Control_Patterns"></a>

## <a name="required-ui-automation-control-patterns"></a>Gerekli UI Otomasyonu Denetim desenleri

Aşağıdaki tabloda, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] menü öğesi denetimleri tarafından desteklenmesi gereken denetim desenleri listelenmektedir. Denetim desenleri hakkında daha fazla bilgi için bkz. [UI Otomasyonu Denetim desenlerine genel bakış](ui-automation-control-patterns-overview.md).

|Denetim deseninin özelliği|Destek|Notlar|
|------------------------------|-------------|-----------|
|<xref:System.Windows.Automation.Provider.IExpandCollapseProvider>|Şekline|Denetim genişletilebilir veya daraltılabilse, uygulayın <xref:System.Windows.Automation.Provider.IExpandCollapseProvider> .|
|<xref:System.Windows.Automation.Provider.IInvokeProvider>|Şekline|Denetim tek bir eylem veya komut çalıştırırsa, uygulayın <xref:System.Windows.Automation.Provider.IInvokeProvider> .|
|<xref:System.Windows.Automation.Provider.IToggleProvider>|Şekline|Denetim açık veya kapalı olabilecek bir seçeneği temsil ediyorsa, uygulayın <xref:System.Windows.Automation.Provider.IToggleProvider> .|
|<xref:System.Windows.Automation.Provider.ISelectionItemProvider>|Şekline|Denetim, menü öğeleri arasındaki seçenekler listesinden seçim yapmak için kullanılırsa, uygulayın <xref:System.Windows.Automation.Provider.ISelectionItemProvider> .|

<a name="UI_Automation_Events_for_Menu_Item"></a>

## <a name="ui-automation-events-for-menu-item"></a>Menü öğesi için UI Otomasyon olayları

Aşağıdaki tabloda, [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] menü öğesi denetimiyle ilişkili olaylar listelenmektedir.

|Olay|Destek|Açıklama|
|-----------|-------------|-----------------|
|<xref:System.Windows.Automation.InvokePatternIdentifiers.InvokedEvent>|Şekline|Denetim, denetim deseninin çağrılmasını destekliyorsa oluşturulmalıdır.|
|<xref:System.Windows.Automation.TogglePatternIdentifiers.ToggleStateProperty>özellik değişti olayı.|Şekline|Denetim Iki durumlu denetim düzenine destekliyorsa, oluşturulmalıdır.|
|<xref:System.Windows.Automation.ExpandCollapsePatternIdentifiers.ExpandCollapseStateProperty>özellik değişti olayı.|Şekline|Denetim, Genişlet denetim stilini destekliyorsa, bunun oluşturulması gerekir.|
|<xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementSelectedEvent>|Şekline|Yok.|

<a name="Required_UI_Automation_Events"></a>

## <a name="required-ui-automation-events"></a>Gerekli UI Otomasyon olayları

Aşağıdaki tabloda, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tüm menü öğesi denetimleri tarafından desteklenmesi gereken olaylar listelenmektedir. Olaylar hakkında daha fazla bilgi için bkz. [UI Otomasyonu olaylarına genel bakış](ui-automation-events-overview.md).

|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Olay|Destek/değer|Notlar|
|---------------------------------------------------------------------------------|--------------------|-----------|
|<xref:System.Windows.Automation.InvokePatternIdentifiers.InvokedEvent>|Şekline|Hiçbiri|
|<xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementAddedToSelectionEvent>|Şekline|Hiçbiri|
|<xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementRemovedFromSelectionEvent>|Şekline|Hiçbiri|
|<xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementSelectedEvent>|Şekline|Hiçbiri|
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>özellik değişti olayı.|Gerekli|Hiçbiri|
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsOffscreenProperty>özellik değişti olayı.|Gerekli|Hiçbiri|
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsEnabledProperty>özellik değişti olayı.|Gerekli|Hiçbiri|
|<xref:System.Windows.Automation.ExpandCollapsePatternIdentifiers.ExpandCollapseStateProperty>özellik değişti olayı.|Şekline|Hiçbiri|
|<xref:System.Windows.Automation.TogglePatternIdentifiers.ToggleStateProperty>özellik değişti olayı.|Şekline|Hiçbiri|
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationFocusChangedEvent>|Gerekli|Hiçbiri|
|<xref:System.Windows.Automation.AutomationElementIdentifiers.StructureChangedEvent>|Gerekli|Hiçbiri|

<a name="Legacy_Issues"></a>

## <a name="legacy-issues"></a>Eski sorunlar

Değiştirme stili yalnızca Win32 menü öğesi işaretlendiğinde ve geçiş modelini desteklemek için program aracılığıyla gerekli olarak belirlenebileceği şekilde desteklenecektir. Win32 menü öğesi, denetlenmesi mümkün olup olmadığını göstermediğinden, menü öğesi işaretlenmediği zaman Invoke deseninin desteklenecek olması gerekir. Yalnızca geçiş modelini destekleyen menü öğeleri için de her zaman çağırma modelini desteklemek için bir özel durum oluşturulur. Bu sayede istemciler, çağırma modelini destekleyen bir öğenin (menü öğesi işaretlenmediği zaman), bir kez işaretlendikten sonra stili artık desteklemediği için karıştırılır.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Automation.ControlType.MenuItem>
- [UI Otomasyon Denetim Düzenlerine Genel Bakış](ui-automation-control-patterns-overview.md)
- [UI Otomasyon Denetim Türlerine Genel Bakış](ui-automation-control-types-overview.md)
- [UI Otomasyonuna Genel Bakış](ui-automation-overview.md)
