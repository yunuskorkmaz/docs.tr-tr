---
title: UI Otomasyon Denetim Türlerine Genel Bakış
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, control types
- control types, UI Automation
ms.assetid: 75159ef8-bd43-4d13-acb7-1f1fe9253160
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: c8ca0934e724c4035fb24b9cb246b0b2f41eea3d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="ui-automation-control-types-overview"></a>UI Otomasyon Denetim Türlerine Genel Bakış
> [!NOTE]
>  Bu belge yönetilen kullanmak isteyen .NET Framework için tasarlanan [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tanımlanan sınıflar <xref:System.Windows.Automation> ad alanı. Hakkında en yeni bilgiler için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], bkz: [Windows Otomasyon API: UI Otomasyonu](http://go.microsoft.com/fwlink/?LinkID=156746).  
  
 [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] Denetim türleri ne tür bir denetim belirli bir öğe, bir birleşik giriş kutusu veya düğmesi gibi temsil eden belirtmek için kullanılan iyi bilinen tanımlayıcılardır.  
  
 İyi bilinen bir tanımlayıcı sahip kolaylaştırır hangi tür denetimlerin kullanılabilir olduğunu belirlemek yardımcı teknoloji aygıtlarını [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] ve denetimleri ile etkileşime geçebilirsiniz.  
  
<a name="UI_Automation_Control_Type_Requisites"></a>   
## <a name="ui-automation-control-type-requisites"></a>UI Otomasyon denetim türü gereksinimleri  
 [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] Denetim türleri sağlayıcıları karşılaması gereken koşulları belirtin. Bu koşullar karşılandığında denetimi belirli denetim türü adı kullanabilirsiniz. Her denetim türü için aşağıdaki koşullar vardır:  
  
-   [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Denetim desenleri — hangi denetim düzenleri desteklenen, hangi denetimi desenleri isteğe bağlı ve hangi denetim düzenleri gerekir desteklenmiyor denetim tarafından.  
  
-   [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] özellik değerlerini — hangi özellik değerleri desteklenir.  
  
-   [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağaç yapısı — gerekli [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağaç yapısı denetimi için.  
  
 Bir denetim belirli denetim türü için koşulları karşıladığında <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.ControlType%2A> özellik değerini denetleyen göstermek türü.  
  
<a name="Current_UI_Automation_Control_Types"></a>   
## <a name="current-ui-automation-control-types"></a>Geçerli UI Otomasyon denetim türleri  
 Aşağıdaki listede, geçerli kümesi içeriyor. [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] kontrol türleri:  
  
-   [Button Denetim Türü İçin UI Otomasyonu Desteği](../../../docs/framework/ui-automation/ui-automation-support-for-the-button-control-type.md)  
  
-   [Calendar Denetim Türü İçin UI Otomasyonu Desteği](../../../docs/framework/ui-automation/ui-automation-support-for-the-calendar-control-type.md)  
  
-   [CheckBox Denetim Türü için UI Otomasyonu Desteği](../../../docs/framework/ui-automation/ui-automation-support-for-the-checkbox-control-type.md)  
  
-   [ComboBox Denetim Türü için UI Otomasyonu Desteği](../../../docs/framework/ui-automation/ui-automation-support-for-the-combobox-control-type.md)  
  
-   [DataGrid Denetim Türü için UI Otomasyonu Desteği](../../../docs/framework/ui-automation/ui-automation-support-for-the-datagrid-control-type.md)  
  
-   [DataItem Denetim Türü için UI Otomasyonu Desteği](../../../docs/framework/ui-automation/ui-automation-support-for-the-dataitem-control-type.md)  
  
-   [Document Denetim Türü İçin UI Otomasyonu Desteği](../../../docs/framework/ui-automation/ui-automation-support-for-the-document-control-type.md)  
  
-   [Edit Denetim Türü İçin UI Otomasyonu Desteği](../../../docs/framework/ui-automation/ui-automation-support-for-the-edit-control-type.md)  
  
-   [Group Denetim Türü İçin UI Otomasyonu Desteği](../../../docs/framework/ui-automation/ui-automation-support-for-the-group-control-type.md)  
  
-   [Header Denetim Türü İçin UI Otomasyonu Desteği](../../../docs/framework/ui-automation/ui-automation-support-for-the-header-control-type.md)  
  
-   [HeaderItem Denetim Türü için UI Otomasyonu Desteği](../../../docs/framework/ui-automation/ui-automation-support-for-the-headeritem-control-type.md)  
  
-   [Hyperlink Denetim Türü İçin UI Otomasyonu Desteği](../../../docs/framework/ui-automation/ui-automation-support-for-the-hyperlink-control-type.md)  
  
-   [Image Denetim Türü İçin UI Otomasyonu Desteği](../../../docs/framework/ui-automation/ui-automation-support-for-the-image-control-type.md)  
  
-   [List Denetim Türü İçin UI Otomasyonu Desteği](../../../docs/framework/ui-automation/ui-automation-support-for-the-list-control-type.md)  
  
-   [ListItem Denetim Türü için UI Otomasyonu Desteği](../../../docs/framework/ui-automation/ui-automation-support-for-the-listitem-control-type.md)  
  
-   [Menu Denetim Türü İçin UI Otomasyonu Desteği](../../../docs/framework/ui-automation/ui-automation-support-for-the-menu-control-type.md)  
  
-   [MenuBar Denetim Türü için UI Otomasyonu Desteği](../../../docs/framework/ui-automation/ui-automation-support-for-the-menubar-control-type.md)  
  
-   [MenuItem Denetim Türü için UI Otomasyonu Desteği](../../../docs/framework/ui-automation/ui-automation-support-for-the-menuitem-control-type.md)  
  
-   [Pane Denetim Türü İçin UI Otomasyonu Desteği](../../../docs/framework/ui-automation/ui-automation-support-for-the-pane-control-type.md)  
  
-   [ProgressBar Denetim Türü için UI Otomasyonu Desteği](../../../docs/framework/ui-automation/ui-automation-support-for-the-progressbar-control-type.md)  
  
-   [RadioButton Denetim Türü için UI Otomasyonu Desteği](../../../docs/framework/ui-automation/ui-automation-support-for-the-radiobutton-control-type.md)  
  
-   [ScrollBar Denetim Türü için UI Otomasyonu Desteği](../../../docs/framework/ui-automation/ui-automation-support-for-the-scrollbar-control-type.md)  
  
-   [Separator Denetim Türü İçin UI Otomasyonu Desteği](../../../docs/framework/ui-automation/ui-automation-support-for-the-separator-control-type.md)  
  
-   [Slider Denetim Türü İçin UI Otomasyonu Desteği](../../../docs/framework/ui-automation/ui-automation-support-for-the-slider-control-type.md)  
  
-   [Spinner Denetim Türü İçin UI Otomasyonu Desteği](../../../docs/framework/ui-automation/ui-automation-support-for-the-spinner-control-type.md)  
  
-   [SplitButton Denetim Türü İçin UI Otomasyonu Desteği](../../../docs/framework/ui-automation/ui-automation-support-for-the-splitbutton-control-type.md)  
  
-   [StatusBar Denetim Türü İçin UI Otomasyonu Desteği](../../../docs/framework/ui-automation/ui-automation-support-for-the-statusbar-control-type.md)  
  
-   [Tab Denetim Türü İçin UI Otomasyonu Desteği](../../../docs/framework/ui-automation/ui-automation-support-for-the-tab-control-type.md)  
  
-   [TabItem Denetim Türü İçin UI Otomasyonu Desteği](../../../docs/framework/ui-automation/ui-automation-support-for-the-tabitem-control-type.md)  
  
-   [Table Denetim Türü İçin UI Otomasyonu Desteği](../../../docs/framework/ui-automation/ui-automation-support-for-the-table-control-type.md)  
  
-   [Text Denetim Türü İçin UI Otomasyonu Desteği](../../../docs/framework/ui-automation/ui-automation-support-for-the-text-control-type.md)  
  
-   [Thumb Denetim Türü İçin UI Otomasyonu Desteği](../../../docs/framework/ui-automation/ui-automation-support-for-the-thumb-control-type.md)  
  
-   [TitleBar Denetim Türü İçin UI Otomasyonu Desteği](../../../docs/framework/ui-automation/ui-automation-support-for-the-titlebar-control-type.md)  
  
-   [ToolBar Denetim Türü İçin UI Otomasyonu Desteği](../../../docs/framework/ui-automation/ui-automation-support-for-the-toolbar-control-type.md)  
  
-   [ToolTip Denetim Türü İçin UI Otomasyonu Desteği](../../../docs/framework/ui-automation/ui-automation-support-for-the-tooltip-control-type.md)  
  
-   [Tree Denetim Türü İçin UI Otomasyonu Desteği](../../../docs/framework/ui-automation/ui-automation-support-for-the-tree-control-type.md)  
  
-   [TreeItem Denetim Türü İçin UI Otomasyonu Desteği](../../../docs/framework/ui-automation/ui-automation-support-for-the-treeitem-control-type.md)  
  
-   [Window Denetim Türü İçin UI Otomasyonu Desteği](../../../docs/framework/ui-automation/ui-automation-support-for-the-window-control-type.md)  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Automation.ControlType>
