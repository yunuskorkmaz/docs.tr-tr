---
title: "UI Otomasyon Denetim Türlerine Genel Bakış"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- UI Automation, control types
- control types, UI Automation
ms.assetid: 75159ef8-bd43-4d13-acb7-1f1fe9253160
caps.latest.revision: "22"
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: c1a424f05f2d57f773e8367e102f553d69b7dc22
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="ui-automation-control-types-overview"></a>UI Otomasyon Denetim Türlerine Genel Bakış
> [!NOTE]
>  Bu belge yönetilen kullanmak isteyen .NET Framework için tasarlanan [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tanımlanan sınıflar <xref:System.Windows.Automation> ad alanı. Hakkında en yeni bilgiler için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], bkz: [Windows Otomasyon API: UI Otomasyonu](http://go.microsoft.com/fwlink/?LinkID=156746).  
  
 [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)]Denetim türleri ne tür bir denetim belirli bir öğe, bir birleşik giriş kutusu veya düğmesi gibi temsil eden belirtmek için kullanılan iyi bilinen tanımlayıcılardır.  
  
 İyi bilinen bir tanımlayıcı sahip kolaylaştırır hangi tür denetimlerin kullanılabilir olduğunu belirlemek yardımcı teknoloji aygıtlarını [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] ve denetimleri ile etkileşime geçebilirsiniz.  
  
<a name="UI_Automation_Control_Type_Requisites"></a>   
## <a name="ui-automation-control-type-requisites"></a>UI Otomasyon denetim türü gereksinimleri  
 [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)]Denetim türleri sağlayıcıları karşılaması gereken koşulları belirtin. Bu koşullar karşılandığında denetimi belirli denetim türü adı kullanabilirsiniz. Her denetim türü için aşağıdaki koşullar vardır:  
  
-   [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Denetim desenleri — hangi denetim düzenleri desteklenen, hangi denetimi desenleri isteğe bağlı ve hangi denetim düzenleri gerekir desteklenmiyor denetim tarafından.  
  
-   [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]özellik değerlerini — hangi özellik değerleri desteklenir.  
  
-   [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]ağaç yapısı — gerekli [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağaç yapısı denetimi için.  
  
 Bir denetim belirli denetim türü için koşulları karşıladığında <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.ControlType%2A> özellik değerini denetleyen göstermek türü.  
  
<a name="Current_UI_Automation_Control_Types"></a>   
## <a name="current-ui-automation-control-types"></a>Geçerli UI Otomasyon denetim türleri  
 Aşağıdaki listede, geçerli kümesi içeriyor. [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] kontrol türleri:  
  
-   [Düğme denetim türü için UI Otomasyon desteği](../../../docs/framework/ui-automation/ui-automation-support-for-the-button-control-type.md)  
  
-   [Takvim denetim türü için UI Otomasyon desteği](../../../docs/framework/ui-automation/ui-automation-support-for-the-calendar-control-type.md)  
  
-   [CheckBox denetim türü için UI Otomasyon desteği](../../../docs/framework/ui-automation/ui-automation-support-for-the-checkbox-control-type.md)  
  
-   [ComboBox denetim türü için UI Otomasyon desteği](../../../docs/framework/ui-automation/ui-automation-support-for-the-combobox-control-type.md)  
  
-   [DataGrid denetim türü için UI Otomasyon desteği](../../../docs/framework/ui-automation/ui-automation-support-for-the-datagrid-control-type.md)  
  
-   [DataItem denetim türü için UI Otomasyon desteği](../../../docs/framework/ui-automation/ui-automation-support-for-the-dataitem-control-type.md)  
  
-   [Belge Denetim türü için UI Otomasyon desteği](../../../docs/framework/ui-automation/ui-automation-support-for-the-document-control-type.md)  
  
-   [Düzenleme denetim türü için UI Otomasyon desteği](../../../docs/framework/ui-automation/ui-automation-support-for-the-edit-control-type.md)  
  
-   [Grup denetim türü için UI Otomasyon desteği](../../../docs/framework/ui-automation/ui-automation-support-for-the-group-control-type.md)  
  
-   [Başlık denetim türü için UI Otomasyon desteği](../../../docs/framework/ui-automation/ui-automation-support-for-the-header-control-type.md)  
  
-   [Headerıtem denetim türü için UI Otomasyon desteği](../../../docs/framework/ui-automation/ui-automation-support-for-the-headeritem-control-type.md)  
  
-   [Köprü denetim türü için UI Otomasyon desteği](../../../docs/framework/ui-automation/ui-automation-support-for-the-hyperlink-control-type.md)  
  
-   [Görüntü Denetim türü için UI Otomasyon desteği](../../../docs/framework/ui-automation/ui-automation-support-for-the-image-control-type.md)  
  
-   [Liste Denetim türü için UI Otomasyon desteği](../../../docs/framework/ui-automation/ui-automation-support-for-the-list-control-type.md)  
  
-   [ListItem denetim türü için UI Otomasyon desteği](../../../docs/framework/ui-automation/ui-automation-support-for-the-listitem-control-type.md)  
  
-   [Menü denetim türü için UI Otomasyon desteği](../../../docs/framework/ui-automation/ui-automation-support-for-the-menu-control-type.md)  
  
-   [MenuBar denetim türü için UI Otomasyon desteği](../../../docs/framework/ui-automation/ui-automation-support-for-the-menubar-control-type.md)  
  
-   [MenuItem denetim türü için UI Otomasyon desteği](../../../docs/framework/ui-automation/ui-automation-support-for-the-menuitem-control-type.md)  
  
-   [Bölme denetim türü için UI Otomasyon desteği](../../../docs/framework/ui-automation/ui-automation-support-for-the-pane-control-type.md)  
  
-   [ProgressBar denetim türü için UI Otomasyon desteği](../../../docs/framework/ui-automation/ui-automation-support-for-the-progressbar-control-type.md)  
  
-   [RadioButton denetim türü için UI Otomasyon desteği](../../../docs/framework/ui-automation/ui-automation-support-for-the-radiobutton-control-type.md)  
  
-   [ScrollBar denetim türü için UI Otomasyon desteği](../../../docs/framework/ui-automation/ui-automation-support-for-the-scrollbar-control-type.md)  
  
-   [Ayırıcı denetim türü için UI Otomasyon desteği](../../../docs/framework/ui-automation/ui-automation-support-for-the-separator-control-type.md)  
  
-   [Kaydırıcı denetim türü için UI Otomasyon desteği](../../../docs/framework/ui-automation/ui-automation-support-for-the-slider-control-type.md)  
  
-   [Değer değiştirici denetim türü için UI Otomasyon desteği](../../../docs/framework/ui-automation/ui-automation-support-for-the-spinner-control-type.md)  
  
-   [Bölünmüş düğme denetim türü için UI Otomasyon desteği](../../../docs/framework/ui-automation/ui-automation-support-for-the-splitbutton-control-type.md)  
  
-   [StatusBar denetim türü için UI Otomasyon desteği](../../../docs/framework/ui-automation/ui-automation-support-for-the-statusbar-control-type.md)  
  
-   [Sekme denetim türü için UI Otomasyon desteği](../../../docs/framework/ui-automation/ui-automation-support-for-the-tab-control-type.md)  
  
-   [TabItem denetim türü için UI Otomasyon desteği](../../../docs/framework/ui-automation/ui-automation-support-for-the-tabitem-control-type.md)  
  
-   [Tablo denetim türü için UI Otomasyon desteği](../../../docs/framework/ui-automation/ui-automation-support-for-the-table-control-type.md)  
  
-   [Metin denetim türü için UI Otomasyon desteği](../../../docs/framework/ui-automation/ui-automation-support-for-the-text-control-type.md)  
  
-   [Parmak denetim türü için UI Otomasyon desteği](../../../docs/framework/ui-automation/ui-automation-support-for-the-thumb-control-type.md)  
  
-   [TitleBar denetim türü için UI Otomasyon desteği](../../../docs/framework/ui-automation/ui-automation-support-for-the-titlebar-control-type.md)  
  
-   [Araç çubuğu denetim türü için UI Otomasyon desteği](../../../docs/framework/ui-automation/ui-automation-support-for-the-toolbar-control-type.md)  
  
-   [ToolTip denetim türü için UI Otomasyon desteği](../../../docs/framework/ui-automation/ui-automation-support-for-the-tooltip-control-type.md)  
  
-   [Ağaç denetim türü için UI Otomasyon desteği](../../../docs/framework/ui-automation/ui-automation-support-for-the-tree-control-type.md)  
  
-   [Treeıtem denetim türü için UI Otomasyon desteği](../../../docs/framework/ui-automation/ui-automation-support-for-the-treeitem-control-type.md)  
  
-   [Pencere denetim türü için UI Otomasyon desteği](../../../docs/framework/ui-automation/ui-automation-support-for-the-window-control-type.md)  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Automation.ControlType>
