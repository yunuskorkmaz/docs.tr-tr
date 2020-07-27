---
title: ComboBox Denetim Türü için UI Otomasyon Desteği
description: ComboBox Denetim türü için UI Otomasyonu desteği hakkında bilgi alın. Gerekli ağaç yapısını, özellikleri, denetim desenlerini ve olayları öğrenin.
ms.date: 03/30/2017
helpviewer_keywords:
- control types, Combo Box
- UI Automation, Combo Box control type
- ComboBox controls
ms.assetid: bb321126-4770-41da-983a-67b7b89d45dd
ms.openlocfilehash: c708de791056969e281ad1bc223e2a2233fa170b
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87166098"
---
# <a name="ui-automation-support-for-the-combobox-control-type"></a>ComboBox Denetim Türü için UI Otomasyon Desteği
> [!NOTE]
> Bu belge, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ad alanında tanımlanan yönetilen sınıfları kullanmak isteyen .NET Framework geliştiricilere yöneliktir <xref:System.Windows.Automation> . Hakkında en son bilgiler için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] bkz. [WINDOWS Otomasyonu API: UI Otomasyonu](/windows/win32/winauto/entry-uiauto-win32).  
  
 Bu konuda [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ComboBox Denetim türü için destek hakkında bilgi verilmektedir. ' De [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] , bir denetim türü, özelliği kullanmak için bir denetimin uyması gereken koşullar kümesidir <xref:System.Windows.Automation.AutomationElement.ControlTypeProperty> . Koşullar, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağaç yapısı, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] özellik değerleri, Denetim desenleri ve olaylar için özel kurallar içerir [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] .  
  
 Birleşik giriş kutusu, bir statik denetimle birleştirilmiş bir liste kutusudur veya açılan kutunun liste kutusu bölümünde seçili olan öğeyi görüntüleyen bir düzenleme denetimidir. Denetimin liste kutusu kısmı her zaman görüntülenir veya yalnızca Kullanıcı, denetimin yanındaki açılan oku (bir itme düğmesi) seçtiğinde görüntülenir. Seçim alanı bir düzenleme denetimi ise, Kullanıcı listede olmayan bilgiler girebilir; Aksi takdirde, Kullanıcı yalnızca listedeki öğeleri seçebilir.  
  
 Aşağıdaki bölümler, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ComboBox Denetim türü için gerekli ağaç yapısını, özellikleri, denetim desenlerini ve olayları tanımlar. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Gereksinimler [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)] , Win32 veya Windows Forms tüm Birleşik giriş kutusu denetimleri için geçerlidir.  
  
<a name="Required_UI_Automation_Tree_Structure"></a>
## <a name="required-ui-automation-tree-structure"></a>Gerekli UI Otomasyonu ağaç yapısı  
 Aşağıdaki tabloda, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Birleşik giriş kutusu denetimleriyle ilgili ağacın denetim görünümü ve içerik görünümü gösterilmektedir ve her görünümde nelerin yer aldığı açıklanmaktadır. Ağaç hakkında daha fazla bilgi için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] bkz. [UI Otomasyon ağacına genel bakış](ui-automation-tree-overview.md).  
  
|Denetim görünümü|İçerik görünümü|  
|------------------|------------------|  
|ComboBox<br /><br /> -Düzenle (0 veya 1)<br />-Liste (1)<br />-List öğesi (liste alt öğesi; 0-çok)<br />-Düğme (1)|ComboBox<br /><br /> -Liste öğesi (0 ' a kadar)|  
  
 Birleşik giriş kutusunun Denetim görünümündeki düzenleme denetimi, Çalıştır iletişim kutusundaki Birleşik giriş kutusunda olduğu gibi, yalnızca Birleşik giriş kutusunun herhangi bir girişi alacak şekilde düzenlenebildiği durumlarda gereklidir.  
  
<a name="Required_UI_Automation_Properties"></a>
## <a name="required-ui-automation-properties"></a>Gerekli UI Otomasyon Özellikleri  
 Aşağıdaki tabloda, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] değeri veya tanımı özellikle Birleşik giriş kutusu denetimleriyle ilgili olan özellikler listelenmiştir. Özellikler hakkında daha fazla bilgi için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] bkz. [Istemciler Için UI Otomasyon özellikleri](ui-automation-properties-for-clients.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Özelliði|Değer|Notlar|  
|------------------------------------------------------------------------------------|-----------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationIdProperty>|Notlara bakın.|Bu özelliğin değerinin bir uygulamadaki tüm denetimlerde benzersiz olması gerekir.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>|Notlara bakın.|Tüm denetimi içeren en dıştaki dikdörtgen.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ClickablePointProperty>|Notlara bakın.|Sınırlayıcı bir dikdörtgen varsa desteklenir. Sınırlayıcı dikdörtgenin içindeki her nokta tıklatılabilir ise ve özelleştirilmiş isabet testi gerçekleştirirseniz ve ardından tıklatılabilir bir nokta sağlayabilirsiniz.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ControlTypeProperty>|ComboBox|Bu değer tüm çerçeveler için aynıdır [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] .|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.HelpTextProperty>|Notlara bakın.|Birleşik giriş kutusu denetimleri için yardım metni, kullanıcıdan Birleşik giriş kutusundan bir seçenek seçmesinin neden istenmekte olduğunu açıklamalıdır. Metin, bir araç ipucuyla sunulan bilgilere benzer. Örneğin, "monitörünüzün ekran çözünürlüğünü ayarlamak için bir öğe seçin."|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsContentElementProperty>|Doğru|Birleşik giriş kutusu denetimleri her zaman ağacın içerik görünümüne dahildir [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] .|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsControlElementProperty>|Doğru|Birleşik giriş kutusu denetimleri her zaman ağacın denetim görünümüne dahildir [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] .|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsKeyboardFocusableProperty>|Doğru|Birleşik giriş kutusu denetimleri bir öğe kümesini seçim kapsayıcısından kullanıma sunar. Birleşik giriş kutusu denetimi klavye odağını alabilir, ancak bir UI Otomasyon istemcisi bir Birleşik giriş kutusuna odak ayarladığında, Birleşik giriş kutusu alt ağacındaki herhangi bir öğe odağı alabilir.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LabeledByProperty>|Notlara bakın.|Birleşik giriş kutusu denetimlerinin genellikle bu özelliğin başvurduğu statik bir metin etiketi vardır.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LocalizedControlTypeProperty>|"Birleşik giriş kutusu"|ComboBox denetim türüne karşılık gelen yerelleştirilmiş dize.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>|Notlara bakın.|Birleşik giriş kutusu denetimi genellikle statik metin denetiminden adını alır.|  
  
<a name="Required_UI_Automation_Control_Patterns"></a>
## <a name="required-ui-automation-control-patterns"></a>Gerekli UI Otomasyonu Denetim desenleri  
 Aşağıdaki tabloda, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Tüm açılan kutu denetimleri tarafından desteklenmesi gereken denetim desenleri listelenmektedir. Denetim desenleri hakkında daha fazla bilgi için bkz. [UI Otomasyonu Denetim desenlerine genel bakış](ui-automation-control-patterns-overview.md).  
  
|Denetim deseninin|Destek|Notlar|  
|---------------------|-------------|-----------|  
|<xref:System.Windows.Automation.Provider.IExpandCollapseProvider>|Yes|Birleşik giriş kutusu denetimi her zaman açılan düğmeyi bir açılan kutu olması için içermelidir.|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider>|Yes|Birleşik giriş kutusundaki geçerli seçimi görüntüler. Bu destek, Birleşik giriş kutusunun altındaki liste kutusunda temsil edilir.|  
|<xref:System.Windows.Automation.Provider.IValueProvider>|Şekline|Birleşik giriş kutusunun rastgele metin değerleri alma özelliği varsa, değer deseninin desteklenmesi gerekir. Bu model, Birleşik giriş kutusunun dize içeriğini programlı bir şekilde ayarlamanıza olanak sağlar. Değer stili desteklenmiyorsa, bu, kullanıcının açılan kutunun alt ağacındaki liste öğelerinden seçim yapması gerektiğini gösterir.|  
|<xref:System.Windows.Automation.Provider.IScrollProvider>|Asla|Kaydırma deseninin doğrudan Birleşik giriş kutusunda hiçbir şekilde desteklenmez. Birleşik giriş kutusu içinde yer alan bir liste kutusu kaydırılabilen bu, desteklenir. Yalnızca liste kutusu ekranda görünür olduğunda desteklenir.|  
  
<a name="Required_Events"></a>
## <a name="required-events"></a>Gerekli olaylar  
 Aşağıdaki tabloda, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Tüm açılan kutu denetimleri tarafından desteklenmesi gereken olaylar listelenmektedir. Olaylar hakkında daha fazla bilgi için bkz. [UI Otomasyonu olaylarına genel bakış](ui-automation-events-overview.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Olay|Destek|Notlar|  
|---------------------------------------------------------------------------------|-------------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationFocusChangedEvent>|Gerekli|Hiçbiri|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>özellik değişti olayı.|Gerekli|Hiçbiri|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsOffscreenProperty>özellik değişti olayı.|Gerekli|Hiçbiri|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsEnabledProperty>özellik değişti olayı.|Gerekli|Hiçbiri|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.StructureChangedEvent>|Gerekli|Hiçbiri|  
|<xref:System.Windows.Automation.ExpandCollapsePatternIdentifiers.ExpandCollapseStateProperty>özellik değişti olayı.|Gerekli|Hiçbiri|  
|<xref:System.Windows.Automation.ValuePatternIdentifiers.ValueProperty>özellik değişti olayı.|Şekline|Denetim değer modelini destekliyorsa, bu olayı desteklemesi gerekir.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Automation.ControlType.ComboBox>
- [UI Otomasyon Denetim Türlerine Genel Bakış](ui-automation-control-types-overview.md)
- [UI Otomasyonuna Genel Bakış](ui-automation-overview.md)
