---
title: UI Otomasyon Denetim Türlerine Genel Bakış
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, control types
- control types, UI Automation
ms.assetid: 75159ef8-bd43-4d13-acb7-1f1fe9253160
ms.openlocfilehash: 643c89e8f6c5e34aa1fb3c5c7c6c750c72046277
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179929"
---
# <a name="ui-automation-control-types-overview"></a>UI Otomasyon Denetim Türlerine Genel Bakış
> [!NOTE]
> Bu dokümantasyon, ad alanında tanımlanan yönetilen [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] sınıfları kullanmak <xref:System.Windows.Automation> isteyen .NET Framework geliştiricileri için tasarlanmıştır. Hakkında en son [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]bilgi için [Bkz. Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).  
  
 [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)]denetim türleri, açılan kutu veya düğme gibi belirli bir öğenin ne tür bir denetimi temsil ettiğini belirtmek için kullanılabilecek iyi bilinen tanımlayıcılardır.  
  
 İyi bilinen bir tanımlayıcıya sahip olmak, yardımcı teknoloji aygıtlarının denetimlerde hangi denetim türlerinin [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] mevcut olduğunu ve denetimlerle nasıl etkileşimde bulunup bulunup etki edilebildiğini belirlemesini kolaylaştırır.  
  
<a name="UI_Automation_Control_Type_Requisites"></a>
## <a name="ui-automation-control-type-requisites"></a>UI Otomasyon Kontrol Tipi Gerekli  
 [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)]denetim türleri, sağlayıcıların karşılaması gereken bir dizi koşul sağlar. Bu koşullar yerine getirildiğinde, denetim belirli denetim türü adını kullanabilir. Her denetim türü aşağıdaki koşullara sahiptir:  
  
- [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]denetim desenleri desteklenmeli, hangi denetim desenleri isteğe bağlıdır ve denetim desenleri denetim tarafından desteklenmemelidir.  
  
- [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]özellik değerleri desteklenir.  
  
- [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]ağaç yapısı-kontrol [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] için gerekli ağaç yapısı.  
  
 Denetim belirli bir denetim türü için koşulları <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.ControlType%2A> karşıladığında, özellik değeri bu denetim türünü gösterir.  
  
<a name="Current_UI_Automation_Control_Types"></a>
## <a name="current-ui-automation-control-types"></a>Güncel UI Otomasyon Kontrol Tipleri  
 Aşağıdaki liste geçerli denetim [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] türleri kümesini içerir:  
  
- [Button Denetim Türü İçin UI Otomasyonu Desteği](ui-automation-support-for-the-button-control-type.md)  
  
- [Calendar Denetim Türü İçin UI Otomasyonu Desteği](ui-automation-support-for-the-calendar-control-type.md)  
  
- [CheckBox Denetim Türü için UI Otomasyon Desteği](ui-automation-support-for-the-checkbox-control-type.md)  
  
- [ComboBox Denetim Türü için UI Otomasyonu Desteği](ui-automation-support-for-the-combobox-control-type.md)  
  
- [DataGrid Denetim Türü için UI Otomasyon Desteği](ui-automation-support-for-the-datagrid-control-type.md)  
  
- [DataItem Denetim Türü için UI Otomasyon Desteği](ui-automation-support-for-the-dataitem-control-type.md)  
  
- [Belge Denetim Türü İçin UI Otomasyon Desteği](ui-automation-support-for-the-document-control-type.md)  
  
- [Edit Denetim Türü İçin UI Otomasyonu Desteği](ui-automation-support-for-the-edit-control-type.md)  
  
- [Grup Denetim Türü İçin UI Otomasyon Desteği](ui-automation-support-for-the-group-control-type.md)  
  
- [Başlık Denetim Türü İçin UI Otomasyon Desteği](ui-automation-support-for-the-header-control-type.md)  
  
- [HeaderItem Denetim Türü için UI Otomasyon Desteği](ui-automation-support-for-the-headeritem-control-type.md)  
  
- [Köprü Denetim Türü İçin UI Otomasyon Desteği](ui-automation-support-for-the-hyperlink-control-type.md)  
  
- [Image Denetim Türü İçin UI Otomasyonu Desteği](ui-automation-support-for-the-image-control-type.md)  
  
- [Liste Denetim Türü İçin UI Otomasyon Desteği](ui-automation-support-for-the-list-control-type.md)  
  
- [ListItem Denetim Türü için UI Otomasyonu Desteği](ui-automation-support-for-the-listitem-control-type.md)  
  
- [Menu Denetim Türü İçin UI Otomasyonu Desteği](ui-automation-support-for-the-menu-control-type.md)  
  
- [MenuBar Denetim Türü için UI Otomasyonu Desteği](ui-automation-support-for-the-menubar-control-type.md)  
  
- [MenuItem Denetim Türü için UI Otomasyonu Desteği](ui-automation-support-for-the-menuitem-control-type.md)  
  
- [Pane Denetim Türü İçin UI Otomasyonu Desteği](ui-automation-support-for-the-pane-control-type.md)  
  
- [ProgressBar Denetim Türü için UI Otomasyonu Desteği](ui-automation-support-for-the-progressbar-control-type.md)  
  
- [RadioButton Denetim Türü için UI Otomasyonu Desteği](ui-automation-support-for-the-radiobutton-control-type.md)  
  
- [ScrollBar Denetim Türü için UI Otomasyon Desteği](ui-automation-support-for-the-scrollbar-control-type.md)  
  
- [Separator Denetim Türü İçin UI Otomasyonu Desteği](ui-automation-support-for-the-separator-control-type.md)  
  
- [Slider Denetim Türü İçin UI Otomasyonu Desteği](ui-automation-support-for-the-slider-control-type.md)  
  
- [Değer Değiştirici Denetim Türü İçin UI Otomasyon Desteği](ui-automation-support-for-the-spinner-control-type.md)  
  
- [SplitButton Denetim Türü İçin UI Otomasyonu Desteği](ui-automation-support-for-the-splitbutton-control-type.md)  
  
- [StatusBar Denetim Türü İçin UI Otomasyonu Desteği](ui-automation-support-for-the-statusbar-control-type.md)  
  
- [Sekme Denetim Türü İçin UI Otomasyon Desteği](ui-automation-support-for-the-tab-control-type.md)  
  
- [TabItem Denetim Türü İçin UI Otomasyonu Desteği](ui-automation-support-for-the-tabitem-control-type.md)  
  
- [Table Denetim Türü İçin UI Otomasyonu Desteği](ui-automation-support-for-the-table-control-type.md)  
  
- [Metin Denetim Türü İçin UI Otomasyon Desteği](ui-automation-support-for-the-text-control-type.md)  
  
- [Thumb Denetim Türü İçin UI Otomasyonu Desteği](ui-automation-support-for-the-thumb-control-type.md)  
  
- [TitleBar Denetim Türü için UI Otomasyon Desteği](ui-automation-support-for-the-titlebar-control-type.md)  
  
- [ToolBar Denetim Türü İçin UI Otomasyonu Desteği](ui-automation-support-for-the-toolbar-control-type.md)  
  
- [ToolTip Denetim Türü İçin UI Otomasyonu Desteği](ui-automation-support-for-the-tooltip-control-type.md)  
  
- [Tree Denetim Türü İçin UI Otomasyonu Desteği](ui-automation-support-for-the-tree-control-type.md)  
  
- [TreeItem Denetim Türü İçin UI Otomasyonu Desteği](ui-automation-support-for-the-treeitem-control-type.md)  
  
- [Pencere Denetim Türü İçin UI Otomasyon Desteği](ui-automation-support-for-the-window-control-type.md)  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Automation.ControlType>
