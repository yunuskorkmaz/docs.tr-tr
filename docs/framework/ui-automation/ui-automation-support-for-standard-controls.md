---
title: Standart Denetimler İçin UI Otomasyon Desteği
description: Windows Presentation Foundation (WPF), Win32 ve Windows Forms için geliştirilen uygulamalardaki standart denetimler için UI Otomasyonu desteği hakkında bilgi alın.
ms.date: 03/30/2017
helpviewer_keywords:
- controls, UI Automation support for
- UI Automation, support for standard controls
ms.assetid: 3770ea8a-2655-4add-9c59-fe0610ad5084
ms.openlocfilehash: 17916a6978008439e91caae00d8b6f26045f9018
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87166127"
---
# <a name="ui-automation-support-for-standard-controls"></a>Standart Denetimler İçin UI Otomasyon Desteği
> [!NOTE]
> Bu belge, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ad alanında tanımlanan yönetilen sınıfları kullanmak isteyen .NET Framework geliştiricilere yöneliktir <xref:System.Windows.Automation> . Hakkında en son bilgiler için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] bkz. [WINDOWS Otomasyonu API: UI Otomasyonu](/windows/win32/winauto/entry-uiauto-win32).  
  
 Bu konu [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] , Win32 ve Windows Forms çerçeveleri için geliştirilen uygulamalardaki standart denetimler için destek hakkında bilgiler içerir.  
  
<a name="Windows_Presentation_Foundation_Controls"></a>
## <a name="windows-presentation-foundation-controls"></a>Windows Presentation Foundation denetimleri  
 [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)]Kullanıcı etkileşimi için bilgi veya destek sağlayan tüm denetim öğeleri için tam yerel destek vardır [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] . Paneller gibi diğer öğeler, için görünür değildir [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] .  
  
<a name="Win32_Controls"></a>
## <a name="win32-controls"></a>Win32 denetimleri  
 Çoğu Win32 denetimi, [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] UIAutomationClientsideProviders.dll istemci tarafı sağlayıcılar aracılığıyla sunulur. Bu derleme, UI Otomasyonu istemci uygulamalarıyla kullanılmak üzere otomatik olarak kaydedilir.  
  
 Tam destek yalnızca *ComCtrl32.dll*sürüm 6 ' dan denetimler için sağlanır.  
  
 Aşağıdaki denetimler desteklenir.  
  
|Sınıf adı|Denetim türü|  
|----------------|------------------|  
|Düğme|Düğme|  
|Düğme|RadioButton|  
|Düğme|Grup|  
|Düğme|CheckBox|  
|Düğme|Köprü|  
|Düğme|SplitButton|  
|Düğme|CheckBox|  
|ComboBoxEx32|ComboBox|  
|ComboBox|ComboBox|  
|Düzenle|Belge|  
|Düzenle|Düzenle|  
|SysLink|Köprü|  
|Statik|Metin|  
|Statik|Görüntü|  
|SysIPAddress32|Özel|  
|SysHeader32|Üstbilgi/HeaderItem|  
|SysListView32|DataGrid|  
|SysListView32|Liste|  
|ListBox|Liste|  
|ListBox|Liste|  
|#32768|Menü|  
|#32768|MenuItem|  
|msctls_progress32|ProgressBar|  
|RichEdit|Belgedeki. Bkz. Note.|  
|RichEdit20A|Belge|  
|RichEdit20W|Belge|  
|RichEdit50W|Belge|  
|ScrollBar|Slider|  
|msctls_trackbar32|Slider|  
|msctls_updown32|Değer Değiştirici|  
|msctls_statusbar32|StatusBar|  
|SysTabControl32|Tab|  
|SysTabControl32|TabItem|  
|ToolbarWindow32|ToolBar|  
|ToolbarWindow32|MenuItem|  
|ToolbarWindow32|Düğme|  
|ToolbarWindow32|CheckBox|  
|ToolbarWindow32|RadioButton|  
|ToolbarWindow32|Ayırıcı|  
|tooltips_class32|ToolTip|  
|#32774|ToolTip|  
|ReBarWindow32|Araç Çubuğu|  
|SysTreeView32|Ağaç|  
|SysTreeView32|TreeItem|  
  
 **Göz önünde** RichEdit denetimi yalnızca Windows Vista ile birlikte gelen sürümler için desteklenir (RichEd20.dll sürüm 3,1 ve üzeri sürümlerde ve MsftEdit.dll sürüm 4,1 ve üzeri).  
  
 Aşağıdaki denetimler desteklenmez.  
  
|Sınıf adı|Denetim türü|  
|----------------|------------------|  
|SysAnimate32|Görüntü|  
|SysPager|Değer Değiştirici|  
|SysDateTimePick32|Özel|  
|SysMonthCal32|Takvim|  
|MS_WINNOTE|Araç ipucu|  
|Vbkabarcık|Araç ipucu|  
|Kaydırma çubuğu (tek başına denetim olarak kullanıldığında)|Slider|  
|SuperGrid|Özel|  
  
<a name="Windows_Forms_Controls"></a>
## <a name="windows-forms-controls"></a>Windows Forms Denetimleri  
 Windows Forms denetimleri, [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] UIAutomationClientsideProviders.dll istemci tarafı sağlayıcılar aracılığıyla sunulur. Bu derleme, UI Otomasyonu istemci uygulamalarıyla kullanılmak üzere otomatik olarak kaydedilir.  
  
 Genellikle, Win32 ortak denetimleri için yönetilen sarmalayıcılar olan Windows Forms denetimleri tarafından desteklenir [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] . Aşağıdaki denetimler desteklenir.  
  
|Sınıf Adı|  
|----------------|  
|Düğme|  
|CheckBox|  
|CheckedListBox|  
|ColorDialog|  
|ComboBox|  
|FolderBrowser|  
|FontDialog|  
|GroupBox|  
|HscrollBar|  
|'I|  
|Etiketle|  
|ListBox|  
|ListView|  
|MainMenu/ContextMenu|  
|MonthCalendar|  
|NotifyIcon|  
|OpenFileDialog|  
|PageSetupDialog|  
|PrintDialog|  
|ProgressBar|  
|RadioButton|  
|RichTextBox|  
|SaveFileDialog|  
|ScrollableControl|  
|SoundPlayer|  
|StatusBar|  
|TabControl/TabPage|  
|TextBox|  
|Zamanlayıcı|  
|Araç Çubuğu|  
|ToolTip|  
|TrackBar|  
|TreeView|  
|VscrollBar|  
|'A|  
  
 Aşağıdaki denetimler [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] yalnızca Microsoft Etkin Erişilebilirlik desteğiyle kullanıma sunulur. Bazı işlevler kullanılamayabilir.  
  
|Denetim adı|  
|------------------|  
|BindingSource|  
|DataGrid|  
|DataGridView|  
|DataNavigator|  
|DomainUpDown|  
|Bileþeni|  
|FlowLayoutPanel|  
|Form|  
|LinkLabel|  
|HelpProvider|  
|MaskedTextBox|  
|MenuStrip/ContextMenuStrip|  
|NumericUpDown|  
|Panel|  
|PictureBox|  
|Öniz|  
|PrintPreview-denetim|  
|PrintPreview-Iletişim kutusu|  
|'In|  
|UserControl|  
|ToolStrip|  
|TableLayoutPanel|  
|SplitContainer/SplitterPanel|  
|Bölücü|  
|RaftingContainer|  
|StatusStrip|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [UI Otomasyon Denetim Türleri](ui-automation-control-types.md)
