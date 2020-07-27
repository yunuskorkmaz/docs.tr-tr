---
title: UI Otomasyon Denetim Türlerine Genel Bakış
description: Bir öğenin ne tür bir denetimin temsil ettiğini göstermek için kullanılabilecek iyi bilinen tanımlayıcılar olan UI Otomasyonu Denetim türlerine genel bakış konusunu okuyun.
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, control types
- control types, UI Automation
ms.assetid: 75159ef8-bd43-4d13-acb7-1f1fe9253160
ms.openlocfilehash: 204e950fca74c4f7bd2c13dc8a8891152954c071
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87166140"
---
# <a name="ui-automation-control-types-overview"></a>UI Otomasyon Denetim Türlerine Genel Bakış
> [!NOTE]
> Bu belge, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ad alanında tanımlanan yönetilen sınıfları kullanmak isteyen .NET Framework geliştiricilere yöneliktir <xref:System.Windows.Automation> . Hakkında en son bilgiler için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] bkz. [WINDOWS Otomasyonu API: UI Otomasyonu](/windows/win32/winauto/entry-uiauto-win32).  
  
 [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)]Denetim türleri, Birleşik giriş kutusu ya da düğme gibi belirli bir öğenin ne tür bir denetimin temsil ettiğini göstermek için kullanılabilen, tanınmış tanımlayıcılardır.  
  
 İyi bilinen bir tanımlayıcıya sahip olmak, yardımcı teknoloji cihazlarının ' de hangi tür denetimlerin kullanılabilir olduğunu [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] ve denetimlerle nasıl etkileşime gireceğini belirlemenizi kolaylaştırır.  
  
<a name="UI_Automation_Control_Type_Requisites"></a>
## <a name="ui-automation-control-type-requisites"></a>UI Otomasyonu Denetim türü gereksinimleri  
 [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)]Denetim türleri, sağlayıcıların karşılaması gereken koşullar kümesini sağlar. Bu koşullar karşılandığında denetim, belirli denetim türü adını kullanabilir. Her denetim türü aşağıdakiler için koşullara sahiptir:  
  
- [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Denetim desenleri — hangi denetim desenlerinin desteklenecek, hangi denetim desenlerinin isteğe bağlı olduğu ve hangi denetim desenlerinin denetim tarafından desteklenmemelidir gerekir.  
  
- [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Özellik değerleri — hangi özellik değerlerini destekler.  
  
- [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]ağaç yapısı — [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Denetim için gerekli ağaç yapısı.  
  
 Bir denetim belirli bir denetim türünün koşullarını karşılıyorsa, <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.ControlType%2A> özellik değeri bu denetim türünü gösterir.  
  
<a name="Current_UI_Automation_Control_Types"></a>
## <a name="current-ui-automation-control-types"></a>Geçerli UI Otomasyon Denetim türleri  
 Aşağıdaki liste geçerli [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] Denetim türleri kümesini içerir:  
  
- [Düğme Denetim Türü İçin UI Otomasyon Desteği](ui-automation-support-for-the-button-control-type.md)  
  
- [Takvim Denetim Türü İçin UI Otomasyon Desteği](ui-automation-support-for-the-calendar-control-type.md)  
  
- [CheckBox Denetim Türü için UI Otomasyon Desteği](ui-automation-support-for-the-checkbox-control-type.md)  
  
- [ComboBox Denetim Türü için UI Otomasyon Desteği](ui-automation-support-for-the-combobox-control-type.md)  
  
- [DataGrid Denetim Türü için UI Otomasyon Desteği](ui-automation-support-for-the-datagrid-control-type.md)  
  
- [DataItem Denetim Türü için UI Otomasyon Desteği](ui-automation-support-for-the-dataitem-control-type.md)  
  
- [Belge Denetim Türü İçin UI Otomasyon Desteği](ui-automation-support-for-the-document-control-type.md)  
  
- [Düzenleme Denetim Türü İçin UI Otomasyon Desteği](ui-automation-support-for-the-edit-control-type.md)  
  
- [Grup Denetim Türü İçin UI Otomasyon Desteği](ui-automation-support-for-the-group-control-type.md)  
  
- [Başlık Denetim Türü İçin UI Otomasyon Desteği](ui-automation-support-for-the-header-control-type.md)  
  
- [HeaderItem Denetim Türü için UI Otomasyon Desteği](ui-automation-support-for-the-headeritem-control-type.md)  
  
- [Köprü Denetim Türü İçin UI Otomasyon Desteği](ui-automation-support-for-the-hyperlink-control-type.md)  
  
- [Görüntü Denetim Türü İçin UI Otomasyon Desteği](ui-automation-support-for-the-image-control-type.md)  
  
- [Liste Denetim Türü İçin UI Otomasyon Desteği](ui-automation-support-for-the-list-control-type.md)  
  
- [ListItem Denetim Türü için UI Otomasyon Desteği](ui-automation-support-for-the-listitem-control-type.md)  
  
- [Menü Denetim Türü İçin UI Otomasyon Desteği](ui-automation-support-for-the-menu-control-type.md)  
  
- [MenuBar Denetim Türü için UI Otomasyon Desteği](ui-automation-support-for-the-menubar-control-type.md)  
  
- [MenuItem Denetim Türü için UI Otomasyon Desteği](ui-automation-support-for-the-menuitem-control-type.md)  
  
- [Bölme Denetim Türü İçin UI Otomasyon Desteği](ui-automation-support-for-the-pane-control-type.md)  
  
- [ProgressBar Denetim Türü için UI Otomasyon Desteği](ui-automation-support-for-the-progressbar-control-type.md)  
  
- [RadioButton Denetim Türü için UI Otomasyon Desteği](ui-automation-support-for-the-radiobutton-control-type.md)  
  
- [ScrollBar Denetim Türü için UI Otomasyon Desteği](ui-automation-support-for-the-scrollbar-control-type.md)  
  
- [Ayırıcı Denetim Türü İçin UI Otomasyon Desteği](ui-automation-support-for-the-separator-control-type.md)  
  
- [Kaydırıcı Denetim Türü İçin UI Otomasyon Desteği](ui-automation-support-for-the-slider-control-type.md)  
  
- [Değer Değiştirici Denetim Türü İçin UI Otomasyon Desteği](ui-automation-support-for-the-spinner-control-type.md)  
  
- [SplitButton Denetim Türü için UI Otomasyon Desteği](ui-automation-support-for-the-splitbutton-control-type.md)  
  
- [StatusBar Denetim Türü için UI Otomasyon Desteği](ui-automation-support-for-the-statusbar-control-type.md)  
  
- [Sekme Denetim Türü İçin UI Otomasyon Desteği](ui-automation-support-for-the-tab-control-type.md)  
  
- [TabItem Denetim Türü için UI Otomasyon Desteği](ui-automation-support-for-the-tabitem-control-type.md)  
  
- [Tablo Denetim Türü İçin UI Otomasyon Desteği](ui-automation-support-for-the-table-control-type.md)  
  
- [Metin Denetim Türü İçin UI Otomasyon Desteği](ui-automation-support-for-the-text-control-type.md)  
  
- [Parmak Denetim Türü İçin UI Otomasyon Desteği](ui-automation-support-for-the-thumb-control-type.md)  
  
- [TitleBar Denetim Türü için UI Otomasyon Desteği](ui-automation-support-for-the-titlebar-control-type.md)  
  
- [ToolBar Denetim Türü için UI Otomasyon Desteği](ui-automation-support-for-the-toolbar-control-type.md)  
  
- [ToolTip Denetim Türü için UI Otomasyon Desteği](ui-automation-support-for-the-tooltip-control-type.md)  
  
- [Ağaç Denetim Türü İçin UI Otomasyon Desteği](ui-automation-support-for-the-tree-control-type.md)  
  
- [TreeItem Denetim Türü için UI Otomasyon Desteği](ui-automation-support-for-the-treeitem-control-type.md)  
  
- [Pencere Denetim Türü İçin UI Otomasyon Desteği](ui-automation-support-for-the-window-control-type.md)  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Automation.ControlType>
