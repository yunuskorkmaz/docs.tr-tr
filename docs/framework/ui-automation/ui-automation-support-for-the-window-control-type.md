---
title: Pencere Denetim Türü İçin UI Otomasyon Desteği
description: Pencere denetim türü için UI Otomasyonu desteği hakkında bilgi alın. Gerekli ağaç yapısını, özellikleri, denetim desenlerini ve olayları öğrenin.
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, Window control type
- Window control type
- control types, Window
ms.assetid: 53be78a6-cdcc-4af3-a464-5927d19c54e8
ms.openlocfilehash: ba5ea794fb9712f7e48f76c6ca3884d4bb05728e
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87167704"
---
# <a name="ui-automation-support-for-the-window-control-type"></a>Pencere Denetim Türü İçin UI Otomasyon Desteği
> [!NOTE]
> Bu belge, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ad alanında tanımlanan yönetilen sınıfları kullanmak isteyen .NET Framework geliştiricilere yöneliktir <xref:System.Windows.Automation> . Hakkında en son bilgiler için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] bkz. [WINDOWS Otomasyonu API: UI Otomasyonu](/windows/win32/winauto/entry-uiauto-win32).  
  
 Bu konu [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] , pencere denetim türü için destek hakkında bilgi sağlar. ' De [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] , bir denetim türü, özelliği kullanmak için bir denetimin uyması gereken koşullar kümesidir <xref:System.Windows.Automation.AutomationElement.ControlTypeProperty> . Koşullar, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağaç yapısı, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] özellik değerleri ve Denetim desenleri için özel kurallar içerir.  
  
 Pencere denetimi, başlık çubuğu, istemci ve diğer nesneler gibi alt nesneleri içeren pencere çerçevesisinden oluşur.  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Aşağıdaki bölümlerde yer alan gereksinimler, pencere denetim türü, Win32 veya Windows Forms uygulayan tüm denetimler için geçerlidir [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)] .  
  
## <a name="required-ui-automation-tree-structure"></a>Gerekli UI Otomasyonu ağaç yapısı  
 Aşağıdaki tabloda, pencere denetimleriyle ilgili ağacın denetim görünümü ve içerik görünümü gösterilmektedir [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ve her görünümde nelerin yer aldığı açıklanmaktadır. Ağaç hakkında daha fazla bilgi için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] bkz. [UI Otomasyon ağacına genel bakış](ui-automation-tree-overview.md).  
  
|Denetim görünümü|İçerik görünümü|  
|------------------|------------------|  
|Pencere|Pencere|  
  
## <a name="required-ui-automation-properties"></a>Gerekli UI Otomasyon Özellikleri  
 Aşağıdaki tabloda, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] değeri veya tanımı özellikle pencere denetimleriyle ilgili olan özellikler listelenmiştir. Özellikler hakkında daha fazla bilgi için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] bkz. [Istemciler Için UI Otomasyon özellikleri](ui-automation-properties-for-clients.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Özelliði|Değer|Notlar|  
|------------------------------------------------------------------------------------|-----------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationIdProperty>|Notlara bakın.|Bu özelliğin değerinin bir uygulamadaki tüm denetimlerde benzersiz olması gerekir.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>|Notlara bakın.|Tüm denetimi içeren en dıştaki dikdörtgen.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ClickablePointProperty>|Notlara bakın.|Pencere denetiminin, pencerenin seçili veya seçilmemiş olmasına neden olacak bir tıklatılabilir noktası olmalıdır.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ControlTypeProperty>|Pencere|Bu değer tüm UI çerçeveleri için aynıdır.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsContentElementProperty>|Doğru|Pencere denetimi her zaman içerik olmalıdır.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsControlElementProperty>|Doğru|Pencere denetimi her zaman bir denetim olmalıdır.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsKeyboardFocusableProperty>|Notlara bakın.|Denetim, klavye odağı alamıyorsa, bu özelliği desteklemesi gerekir.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LabeledByProperty>|`null`|Pencere denetimlerinde statik pencere etiketi yoktur.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LocalizedControlTypeProperty>|penceresine|Pencere denetim türüne karşılık gelen yerelleştirilmiş dize.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>|Notlara bakın.|Pencere denetimi her zaman, kullanıcının öğe için en anlamlı tanımlayıcı olarak ilişkilendirilebilmesi ile ilişkili bir birincil pencere öğesi içerir.|  
  
## <a name="required-ui-automation-control-patterns"></a>Gerekli UI Otomasyonu Denetim desenleri  
 Aşağıdaki tabloda, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Pencere denetimleri tarafından desteklenmesi için gereken denetim desenleri listelenmektedir. Denetim desenleri hakkında daha fazla bilgi için bkz. [UI Otomasyonu Denetim desenlerine genel bakış](ui-automation-control-patterns-overview.md).  
  
|Denetim deseninin|Destek|Notlar|  
|---------------------|-------------|-----------|  
|<xref:System.Windows.Automation.Provider.IDockProvider>|Koşullu|Pencere, yerleşik bir özelliği varsa desteklenmelidir.|  
|<xref:System.Windows.Automation.Provider.ITransformProvider>|Gerekli|Pencerenin ekranda taşınmasını, yeniden boyutlandırılmasını veya döndürülmesine izin vermez.|  
|<xref:System.Windows.Automation.Provider.IWindowProvider>|Gerekli|Pencere için belirli işlemleri sunar.|  
  
## <a name="required-ui-automation-events"></a>Gerekli UI Otomasyon olayları  
 Aşağıdaki tabloda [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tüm pencere denetimleri tarafından desteklenmesi gereken olaylar listelenmektedir. Olaylar hakkında daha fazla bilgi için bkz. [UI Otomasyonu olaylarına genel bakış](ui-automation-events-overview.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Olay|Destek|Notlar|  
|---------------------------------------------------------------------------------|-------------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AsyncContentLoadedEvent>|Gerekli|Hiçbiri|  
|<xref:System.Windows.Automation.AutomationElement.AutomationFocusChangedEvent>|Gerekli|Hiçbiri|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>özellik değişti olayı.|Gerekli|Hiçbiri|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsEnabledProperty>özellik değişti olayı.|Gerekli|Hiçbiri|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsOffscreenProperty>özellik değişti olayı.|Gerekli|Hiçbiri|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LayoutInvalidatedEvent>|Gerekli|Hiçbiri|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>özellik değişti olayı.|Gerekli|Hiçbiri|  
|<xref:System.Windows.Automation.AutomationElement.StructureChangedEvent>|Gerekli|Hiçbiri|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontallyScrollableProperty>özellik değişti olayı.|Şekline|Hiçbiri|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontalScrollPercentProperty>özellik değişti olayı.|Şekline|Hiçbiri|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontalViewSizeProperty>özellik değişti olayı.|Şekline|Hiçbiri|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticalScrollPercentProperty>özellik değişti olayı.|Şekline|Hiçbiri|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticallyScrollableProperty>özellik değişti olayı.|Şekline|Hiçbiri|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticalViewSizeProperty>özellik değişti olayı.|Şekline|Hiçbiri|  
|<xref:System.Windows.Automation.WindowPatternIdentifiers.WindowClosedEvent>|Gerekli|Hiçbiri|  
|<xref:System.Windows.Automation.WindowPatternIdentifiers.WindowOpenedEvent>|Gerekli|Hiçbiri|  
|<xref:System.Windows.Automation.WindowPatternIdentifiers.WindowVisualStateProperty>özellik değişti olayı.|Şekline|Hiçbiri|  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Automation.ControlType.Window>
- [UI Otomasyon Denetim Türlerine Genel Bakış](ui-automation-control-types-overview.md)
- [UI Otomasyonuna Genel Bakış](ui-automation-overview.md)
