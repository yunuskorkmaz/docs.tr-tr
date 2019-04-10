---
title: UI Otomasyon Denetim Türlerine Genel Bakış
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, control types
- control types, UI Automation
ms.assetid: 75159ef8-bd43-4d13-acb7-1f1fe9253160
ms.openlocfilehash: e9cbff2ec6496cabe827e075b737a8c6f16fee93
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59147725"
---
# <a name="ui-automation-control-types-overview"></a>UI Otomasyon Denetim Türlerine Genel Bakış
> [!NOTE]
>  Bu belge yönetilen kullanmak isteyen .NET Framework için tasarlanan [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tanımlanan sınıflar <xref:System.Windows.Automation> ad alanı. En son bilgileri [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], bkz: [Windows Automation API: UI Otomasyonu](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] Denetim türleri ne tür bir denetim belirli bir öğenin, birleşik giriş kutusu veya bir düğme gibi temsil eden belirtmek için kullanılan bilinen tanıtıcılardır.  
  
 İyi bilinen bir tanımlayıcıya sahip kolaylaştırır ne tür denetimler kullanılabilir belirlemek yardımcı teknoloji cihazları [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] ve denetimler ile etkileşim öğrenin.  
  
<a name="UI_Automation_Control_Type_Requisites"></a>   
## <a name="ui-automation-control-type-requisites"></a>UI Otomasyon denetim türü gereksinimleri  
 [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] Denetim türleri sağlayıcıları karşılaması gereken koşulları kümesi sağlar. Bu koşullar karşılandığında, denetimin belirli denetim türü adı kullanabilirsiniz. Her denetim türü için aşağıdaki koşullar vardır:  
  
-   [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Denetim desenleri — hangi denetim düzenleri desteklenmelidir denetleyen biçimlerinin isteğe bağlı olduğu ve hangi denetim düzenleri denetim tarafından değil desteklenmelidir.  
  
-   [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] özellik değerlerini — hangi özellik değerleri desteklenir.  
  
-   [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağaç yapısı — gerekli [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağaç yapısı denetimi.  
  
 Bir denetimi, belirli bir denetim türü için koşulları karşıladığında <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.ControlType%2A> özellik değeri, bu denetim gösterecektir türü.  
  
<a name="Current_UI_Automation_Control_Types"></a>   
## <a name="current-ui-automation-control-types"></a>Geçerli UI Otomasyon denetim türleri  
 Aşağıdaki listede geçerli kümesini içeren [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] denetim türlerinin:  
  
-   [Düğme Denetim Türü İçin UI Otomasyon Desteği](../../../docs/framework/ui-automation/ui-automation-support-for-the-button-control-type.md)  
  
-   [Takvim Denetim Türü İçin UI Otomasyon Desteği](../../../docs/framework/ui-automation/ui-automation-support-for-the-calendar-control-type.md)  
  
-   [CheckBox Denetim Türü için UI Otomasyon Desteği](../../../docs/framework/ui-automation/ui-automation-support-for-the-checkbox-control-type.md)  
  
-   [ComboBox Denetim Türü için UI Otomasyon Desteği](../../../docs/framework/ui-automation/ui-automation-support-for-the-combobox-control-type.md)  
  
-   [DataGrid Denetim Türü için UI Otomasyon Desteği](../../../docs/framework/ui-automation/ui-automation-support-for-the-datagrid-control-type.md)  
  
-   [DataItem Denetim Türü için UI Otomasyon Desteği](../../../docs/framework/ui-automation/ui-automation-support-for-the-dataitem-control-type.md)  
  
-   [Belge Denetim Türü İçin UI Otomasyon Desteği](../../../docs/framework/ui-automation/ui-automation-support-for-the-document-control-type.md)  
  
-   [Düzenleme Denetim Türü İçin UI Otomasyon Desteği](../../../docs/framework/ui-automation/ui-automation-support-for-the-edit-control-type.md)  
  
-   [Grup Denetim Türü İçin UI Otomasyon Desteği](../../../docs/framework/ui-automation/ui-automation-support-for-the-group-control-type.md)  
  
-   [Başlık Denetim Türü İçin UI Otomasyon Desteği](../../../docs/framework/ui-automation/ui-automation-support-for-the-header-control-type.md)  
  
-   [HeaderItem Denetim Türü için UI Otomasyon Desteği](../../../docs/framework/ui-automation/ui-automation-support-for-the-headeritem-control-type.md)  
  
-   [Köprü Denetim Türü İçin UI Otomasyon Desteği](../../../docs/framework/ui-automation/ui-automation-support-for-the-hyperlink-control-type.md)  
  
-   [Görüntü Denetim Türü İçin UI Otomasyon Desteği](../../../docs/framework/ui-automation/ui-automation-support-for-the-image-control-type.md)  
  
-   [Liste Denetim Türü İçin UI Otomasyon Desteği](../../../docs/framework/ui-automation/ui-automation-support-for-the-list-control-type.md)  
  
-   [ListItem Denetim Türü için UI Otomasyon Desteği](../../../docs/framework/ui-automation/ui-automation-support-for-the-listitem-control-type.md)  
  
-   [Menü Denetim Türü İçin UI Otomasyon Desteği](../../../docs/framework/ui-automation/ui-automation-support-for-the-menu-control-type.md)  
  
-   [MenuBar Denetim Türü için UI Otomasyon Desteği](../../../docs/framework/ui-automation/ui-automation-support-for-the-menubar-control-type.md)  
  
-   [MenuItem Denetim Türü için UI Otomasyon Desteği](../../../docs/framework/ui-automation/ui-automation-support-for-the-menuitem-control-type.md)  
  
-   [Bölme Denetim Türü İçin UI Otomasyon Desteği](../../../docs/framework/ui-automation/ui-automation-support-for-the-pane-control-type.md)  
  
-   [ProgressBar Denetim Türü için UI Otomasyon Desteği](../../../docs/framework/ui-automation/ui-automation-support-for-the-progressbar-control-type.md)  
  
-   [RadioButton Denetim Türü için UI Otomasyon Desteği](../../../docs/framework/ui-automation/ui-automation-support-for-the-radiobutton-control-type.md)  
  
-   [ScrollBar Denetim Türü için UI Otomasyon Desteği](../../../docs/framework/ui-automation/ui-automation-support-for-the-scrollbar-control-type.md)  
  
-   [Ayırıcı Denetim Türü İçin UI Otomasyon Desteği](../../../docs/framework/ui-automation/ui-automation-support-for-the-separator-control-type.md)  
  
-   [Kaydırıcı Denetim Türü İçin UI Otomasyon Desteği](../../../docs/framework/ui-automation/ui-automation-support-for-the-slider-control-type.md)  
  
-   [Değer Değiştirici Denetim Türü İçin UI Otomasyon Desteği](../../../docs/framework/ui-automation/ui-automation-support-for-the-spinner-control-type.md)  
  
-   [SplitButton Denetim Türü için UI Otomasyon Desteği](../../../docs/framework/ui-automation/ui-automation-support-for-the-splitbutton-control-type.md)  
  
-   [StatusBar Denetim Türü için UI Otomasyon Desteği](../../../docs/framework/ui-automation/ui-automation-support-for-the-statusbar-control-type.md)  
  
-   [Sekme Denetim Türü İçin UI Otomasyon Desteği](../../../docs/framework/ui-automation/ui-automation-support-for-the-tab-control-type.md)  
  
-   [TabItem Denetim Türü için UI Otomasyon Desteği](../../../docs/framework/ui-automation/ui-automation-support-for-the-tabitem-control-type.md)  
  
-   [Tablo Denetim Türü İçin UI Otomasyon Desteği](../../../docs/framework/ui-automation/ui-automation-support-for-the-table-control-type.md)  
  
-   [Metin Denetim Türü İçin UI Otomasyon Desteği](../../../docs/framework/ui-automation/ui-automation-support-for-the-text-control-type.md)  
  
-   [Parmak Denetim Türü İçin UI Otomasyon Desteği](../../../docs/framework/ui-automation/ui-automation-support-for-the-thumb-control-type.md)  
  
-   [TitleBar Denetim Türü için UI Otomasyon Desteği](../../../docs/framework/ui-automation/ui-automation-support-for-the-titlebar-control-type.md)  
  
-   [ToolBar Denetim Türü için UI Otomasyon Desteği](../../../docs/framework/ui-automation/ui-automation-support-for-the-toolbar-control-type.md)  
  
-   [ToolTip Denetim Türü için UI Otomasyon Desteği](../../../docs/framework/ui-automation/ui-automation-support-for-the-tooltip-control-type.md)  
  
-   [Ağaç Denetim Türü İçin UI Otomasyon Desteği](../../../docs/framework/ui-automation/ui-automation-support-for-the-tree-control-type.md)  
  
-   [TreeItem Denetim Türü için UI Otomasyon Desteği](../../../docs/framework/ui-automation/ui-automation-support-for-the-treeitem-control-type.md)  
  
-   [Pencere Denetim Türü İçin UI Otomasyon Desteği](../../../docs/framework/ui-automation/ui-automation-support-for-the-window-control-type.md)  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Automation.ControlType>
