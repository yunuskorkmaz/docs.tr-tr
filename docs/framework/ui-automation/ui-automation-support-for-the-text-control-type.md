---
title: Metin Denetim Türü İçin UI Otomasyon Desteği
ms.date: 03/30/2017
helpviewer_keywords:
- Text control type
- UI Automation, Text control type
- control types, Text
ms.assetid: ab0d0ada-8a71-4547-9c03-aadf675938f2
ms.openlocfilehash: 7fcfd783f4e6aa755d9c10f4a27296db548fd1df
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179512"
---
# <a name="ui-automation-support-for-the-text-control-type"></a>Metin Denetim Türü İçin UI Otomasyon Desteği
> [!NOTE]
> Bu dokümantasyon, ad alanında tanımlanan yönetilen [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] sınıfları kullanmak <xref:System.Windows.Automation> isteyen .NET Framework geliştiricileri için tasarlanmıştır. Hakkında en son [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]bilgi için [Bkz. Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).  
  
 Bu konu, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Metin denetim türü için destek hakkında bilgi sağlar. Denetim [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]türü, <xref:System.Windows.Automation.AutomationElement.ControlTypeProperty> özelliği kullanmak için denetimin karşılaması gereken koşullar kümesidir. Koşullar, ağaç yapısı, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] özellik değerleri ve denetim desenleri için özel yönergeler içerir.  
  
 Metin denetimleri, ekrandaki bir metin parçasını temsil eden temel kullanıcı arabirimi öğesidir.  
  
 Aşağıdaki bölümler, Metin [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] denetim türü için gerekli ağaç yapısını, özelliklerini, denetim desenlerini ve olaylarını tanımlar. Gereksinimler, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Win32 veya [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)]Windows Forms olsun, tüm metin denetimleri için geçerlidir.  
  
<a name="Required_UI_Automation_Tree_Structure"></a>
## <a name="required-ui-automation-tree-structure"></a>Gerekli UI Otomasyon Ağaç Yapısı  
 Aşağıdaki tablo, metin denetimleri ile ilgili [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] denetim görünümünü ve ağacın içerik görünümünü görüntüler ve her görünümde nelerin bulunabileceğini açıklar. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Ağaç hakkında daha fazla bilgi için [UI Automation Tree Genel Bakış'a](ui-automation-tree-overview.md)bakın.  
  
|Kontrol Görünümü|İçerik Görünümü|  
|------------------|------------------|  
|Metin|Metin (içerik varsa)|  
  
 Metin denetimi tek başına etiket olarak veya formdaki statik metin olarak kullanılabilir. Ayrıca bir yapı içinde bulunabilir:  
  
- Listıtem  
  
- Treeıtem  
  
- Dataıtem  
  
 Metin genellikle başka bir denetim aracılığıyla [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] görüntülendiğinden, metin `NameProperty` denetimleri ağacın İçerik Görünümü'nde olmayabilir. Örneğin, Combo Box denetimini etiketlemek için kullanılan metin, `NameProperty` denetimin değeri üzerinden ortaya çıkarır. Combo Box denetimi Kullanıcı Arabirimi Otomasyon Ağacı'nın içerik görünümünde olduğundan, metin denetiminin orada olması gerekmez. Metin denetimlerinde içerik görünümünde her zaman 0 alt bilgi var  
  
<a name="Required_UI_Automation_Properties"></a>
## <a name="required-ui-automation-properties"></a>Gerekli UI Otomasyon Özellikleri  
 Aşağıdaki tablo, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] değeri veya tanımı özellikle metin denetimleri ile ilgili özellikleri listeler. Özellikler hakkında [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] daha fazla bilgi [için, Müşteriler için Kullanıcı Arabirimi Otomasyon Özellikleri'ne](ui-automation-properties-for-clients.md)bakın.  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Özellik|Değer|Notlar|  
|------------------------------------------------------------------------------------|-----------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationIdProperty>|Notlara bakın.|Bu özelliğin değeri, bir uygulamadaki tüm denetimler arasında benzersiz olmalıdır.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>|Notlara bakın.|Tüm denetimi içeren en dıştaki dikdörtgen.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ClickablePointProperty>|Notlara bakın.|Sınırlayıcı bir dikdörtgen varsa desteklenir. Sınırlayıcı dikdörtgen içindeki her nokta tıklatılabilir değilse ve özel isabet testi gerçekleştirin, sonra geçersiz kılınve tıklanabilir bir nokta sağlayın.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsKeyboardFocusableProperty>|Notlara bakın.|Denetim klavye odağı alabiliyorsa, bu özelliği desteklemesi gerekir.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>|Notlara bakın.|Metin çubuğu denetiminin adı her zaman görüntülenebilen txt'dir.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LabeledByProperty>|`Null`|Metin denetimleri statik metin etiketine sahip değildir.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ControlTypeProperty>|Metin|Bu değer tüm Ara bilgi arabirimi çerçeveleri için aynıdır.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LocalizedControlTypeProperty>|"metin"|Metin denetim türüne karşılık gelen yerelleştirilmiş dize.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsContentElementProperty>|-sına bağ -lıdır|Metin denetimi, başka bir denetimin NameProperty'inde açığa alınmayan bilgiler içeriyorsa içerik olacaktır.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsControlElementProperty>|True|Metin denetimi her zaman bir denetim olmalıdır.|  
  
<a name="Required_UI_Automation_Control_Patterns"></a>
## <a name="required-ui-automation-control-patterns"></a>Gerekli UI Otomasyon Kontrol Desenleri  
 Aşağıdaki tabloda [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] metin denetimleri tarafından desteklenmesi gereken denetim desenleri listelenir. Denetim desenleri hakkında daha fazla bilgi için [UI Otomasyon Kontrol Modellerine Genel Bakış'a](ui-automation-control-patterns-overview.md)bakın.  
  
|Kontrol Deseni|Destek|Notlar|  
|---------------------|-------------|-----------|  
|<xref:System.Windows.Automation.Provider.IValueProvider>|Hiçbir zaman|Metin hiçbir zaman ValuePattern'i desteklemez. Metin editable ise, bu Edit denetim türüdür.|  
|<xref:System.Windows.Automation.Provider.ITextProvider>|-sına bağ -lıdır|Metin, daha iyi erişilebilirlik için Metin denetim deseni desteklemelidir; ancak, gerekli değildir. Metin denetimi deseni, metin zengin stil ve özniteliklere (örneğin, renk, kalın ve italik) sahipolduğunda yararlıdır. Çerçeveye göre değişir.|  
|<xref:System.Windows.Automation.Provider.ITableItemProvider>|-sına bağ -lıdır|Metin öğesi Tablo denetiminde yer alırsa, bu desteklenmelidir.|  
|<xref:System.Windows.Automation.Provider.IRangeValueProvider>|-sına bağ -lıdır|Metin öğesi bir tablo denetimi içinde yer alırsa, bu desteklenmelidir.|  
  
<a name="Required_UI_Automation_Events"></a>
## <a name="required-ui-automation-events"></a>Gerekli UI Otomasyon Etkinlikleri  
 Aşağıdaki tablo, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tüm metin denetimleri tarafından desteklenmesi gereken olayları listeler. Etkinlikler hakkında daha fazla bilgi için [UI Otomasyon Etkinliklerine Genel Bakış'a](ui-automation-events-overview.md)bakın.  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Olay|Destek|Notlar|  
|---------------------------------------------------------------------------------|-------------|-----------|  
|<xref:System.Windows.Automation.TextPatternIdentifiers.TextSelectionChangedEvent>|Gerekli|None|  
|<xref:System.Windows.Automation.TextPatternIdentifiers.TextChangedEvent>|Gerekli|None|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>özellik değiştirilen olay.|Gerekli|None|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsOffscreenProperty>özellik değiştirilen olay.|Gerekli|None|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsEnabledProperty>özellik değiştirilen olay.|Gerekli|None|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>özellik değiştirilen olay.|Gerekli|None|  
|<xref:System.Windows.Automation.ValuePatternIdentifiers.ValueProperty>özellik değiştirilen olay.|Hiçbir zaman|None|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationFocusChangedEvent>|Gerekli|None|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.StructureChangedEvent>|Gerekli|None|  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Automation.ControlType.Text>
- [UI Otomasyonu Denetim Türlerine Genel Bakış](ui-automation-control-types-overview.md)
- [UI Otomasyonuna Genel Bakış](ui-automation-overview.md)
