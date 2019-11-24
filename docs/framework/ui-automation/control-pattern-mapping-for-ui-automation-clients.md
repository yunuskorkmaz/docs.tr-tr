---
title: UI Otomasyon İstemcileri İçin Denetim Düzeni Eşleştirmesi
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, for UI Automation clients
- UI Automation, clients, control patterns for
ms.assetid: 8b81645b-8be3-4e26-9c98-4fb0fceca06b
ms.openlocfilehash: 48298cb8d89958c701d7150aeb497e82d565bde1
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74433863"
---
# <a name="control-pattern-mapping-for-ui-automation-clients"></a>UI Otomasyon İstemcileri İçin Denetim Düzeni Eşleştirmesi
> [!NOTE]
> This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace. For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).  
  
 This topic lists control types and their associated control patterns.  
  
 The following table organizes the control patterns into the following categories:  
  
- Desteklenen. The control must support this control pattern.  
  
- Conditional support. The control may support this control pattern depending on the state of the control.  
  
- Desteklenmez. The control does not support this control pattern; custom controls may support this control pattern.  
  
> [!NOTE]
> Some controls have conditional support for several control patterns depending on the functionality of the control. For example, the menu item control has conditional support for the <xref:System.Windows.Automation.InvokePattern>, <xref:System.Windows.Automation.ExpandCollapsePattern>, <xref:System.Windows.Automation.TogglePattern>, or <xref:System.Windows.Automation.SelectionItemPattern> control pattern, depending on its function in the menu control.  
  
<a name="control_mapping_clients"></a>   
## <a name="ui-automation-control-patterns-for-clients"></a>İstemciler İçin UI Otomasyon Denetim Düzenleri  
  
|Control Type|Desteklenir|Conditional Support|Desteklenmez|  
|------------------|---------------|-------------------------|-------------------|  
|Düğme|Yok.|Invoke, Toggle, Expand Collapse|Yok.|  
|Takvim|Grid, Table|Selection, Scroll|Değer|  
|Check Box|İki Durumlu Düğme|Yok.|Yok.|  
|Birleşik Giriş Kutusu|Expand Collapse|Selection, Value|Kaydırma|  
|Veri Kılavuzu|Kılavuz|Scroll, Selection, Table|Yok.|  
|Veri Öğesi|Seçim Öğesi|Expand Collapse, Grid Item, Scroll Item, Table, Toggle, Value|Yok.|  
|Belge|Metin|Scroll, Value|Yok.|  
|Düzenle|Yok.|Text, Range Value, Value|Yok.|  
|Grup|Yok.|Expand Collapse|Yok.|  
|Üstbilgi|Yok.|Dönüştürme|Yok.|  
|Üstbilgi Öğesi|Yok.|Transform, Invoke|Yok.|  
|Köprü|Çağır|Değer|Yok.|  
|Görüntü|Yok.|Grid Item, Table Item|Invoke, Selection Item|  
|List|Yok.|Grid, Multiple View, Scroll, Selection|Tablo|  
|List Item|Seçim Öğesi|Expand Collapse, Grid Item, Invoke, Scroll Item, Toggle, Value|Yok.|  
|Menü|Yok.|Yok.|Yok.|  
|Menü Çubuğu|Yok.|Expand Collapse, Dock, Transform|Yok.|  
|Menü Öğesi|Yok.|Expand Collapse, Invoke, Selection Item, Toggle|Yok.|  
|Bölme|Yok.|Dock. Scroll, Transform|Pencere|  
|İlerleme Çubuğu|Yok.|Range Value, Value|Yok.|  
|Radyo Düğmesi|Seçim Öğesi|Yok.|İki Durumlu Düğme|  
|Kaydırma Çubuğu|Yok.|Aralık Değeri|Kaydırma|  
|Ayırıcı|Yok.|Yok.|Yok.|  
|Kaydırıcı|Yok.|Range Value, Selection, Value|Yok.|  
|Değer Değiştirici|Yok.|Range Value, Selection, Value|Yok.|  
|Bölünmüş Düğme|Invoke, Expand Collapse|Yok.|Yok.|  
|Durum Çubuğu|Yok.|Kılavuz|Yok.|  
|Tab|Seçim|Kaydırma|Yok.|  
|Sekme Öğesi|Seçim Öğesi|Yok.|Çağır|  
|Tablo|Grid, Grid Item, Table, Table Item|Yok.|Yok.|  
|Metin|Yok.|Grid Item, Table Item, Text|Değer|  
|Parmak|Dönüştürme|Yok.|Yok.|  
|Başlık Çubuğu|Yok.|Yok.|Yok.|  
|Tool Bar|Yok.|Dock, Expand Collapse, Transform|Yok.|  
|Tool Tip|Yok.|Text, Window|Yok.|  
|Ağaç|Yok.|Scroll, Selection|Yok.|  
|Ağaç Öğesi|Expand Collapse|Invoke, Scroll Item, Selection Item, Toggle|Yok.|  
|Pencere|Transform, Window|Dock|Yok.|  
  
> [!NOTE]
> If a control type has no supported control patterns listed but has one or more conditionally-supported control patterns, then one of those conditional control patterns will be supported at all times.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [UI Otomasyonuna Genel Bakış](ui-automation-overview.md)
