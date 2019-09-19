---
title: Standart Denetimler İçin UI Otomasyon Desteği
ms.date: 03/30/2017
helpviewer_keywords:
- controls, UI Automation support for
- UI Automation, support for standard controls
ms.assetid: 3770ea8a-2655-4add-9c59-fe0610ad5084
ms.openlocfilehash: 6cbf31c8a1cdf6e853e56445d22f4a7513bd1859
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71042003"
---
# <a name="ui-automation-support-for-standard-controls"></a>Standart Denetimler İçin UI Otomasyon Desteği
> [!NOTE]
> Bu belge, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] <xref:System.Windows.Automation> ad alanında tanımlanan yönetilen sınıfları kullanmak isteyen .NET Framework geliştiricilere yöneliktir. Hakkında [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]en son bilgiler için bkz [. Windows Otomasyonu API 'si: UI Otomasyonu](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Bu konu,, ve [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)]çerçeveleriiçin [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)]geliştirilen uygulamalardakistandartdenetimleriçindestekhakkındabilgileriçerir.[!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)]  
  
<a name="Windows_Presentation_Foundation_Controls"></a>   
## <a name="windows-presentation-foundation-controls"></a>Windows Presentation Foundation denetimleri  
 Kullanıcı [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] etkileşimi için bilgi veya destek sağlayan tüm denetim öğeleri için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]tam yerel destek vardır. Paneller gibi diğer öğeler, için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]görünür değildir.  
  
<a name="Win32_Controls"></a>   
## <a name="win32-controls"></a>Win32 denetimleri  
 Çoğu [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] denetim UIAutomationClientsideProviders. dll içindeki istemci tarafı sağlayıcılar [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] aracılığıyla sunulur. Bu derleme, UI Otomasyonu istemci uygulamalarıyla kullanılmak üzere otomatik olarak kaydedilir.  
  
 Tam destek yalnızca ComCtrl32. dll sürüm 6 [!INCLUDE[TLA#tla_winxp](../../../includes/tlasharptla-winxp-md.md)] ' dan (ve üzeri sürümlerde kullanılabilir) denetimler için sağlanır.  
  
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
|SysListView32|List|  
|ListBox|List|  
|ListBox|Liste|  
|#32768|Menü|  
|#32768|MenuItem|  
|msctls_progress32|ProgressBar|  
|RichEdit|belgedeki. Bkz. Note.|  
|RichEdit20A|Belge|  
|RichEdit20W|Belge|  
|RichEdit50W|Belge|  
|ScrollBar|Kaydırıcı|  
|msctls_trackbar32|Kaydırıcı|  
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
  
 **Göz önünde** RichEdit denetimi yalnızca ile [!INCLUDE[TLA#tla_winvista](../../../includes/tlasharptla-winvista-md.md)] birlikte gelen sürümler için desteklenir (riched20. dll sürümü 3,1 ve üzeri ve Msftedit. dll sürüm 4,1 ve üzeri).  
  
 Aşağıdaki denetimler desteklenmez.  
  
|Sınıf adı|Denetim türü|  
|----------------|------------------|  
|SysAnimate32|Görüntü|  
|SysPager|Değer Değiştirici|  
|SysDateTimePick32|Özel|  
|SysMonthCal32|Takvim|  
|MS_WINNOTE|İpucuna|  
|Vbkabarcık|İpucuna|  
|Kaydırma çubuğu (tek başına denetim olarak kullanıldığında)|Kaydırıcı|  
|SuperGrid|Özel|  
  
<a name="Windows_Forms_Controls"></a>   
## <a name="windows-forms-controls"></a>Windows Forms Denetimleri  
 Windows Forms denetimleri, UIAutomationClientsideProviders. dll içindeki istemci tarafı sağlayıcılar [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] aracılığıyla sunulur. Bu derleme, UI Otomasyonu istemci uygulamalarıyla kullanılmak üzere otomatik olarak kaydedilir.  
  
 Genellikle, [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] ortak denetimlerin yönetilen sarmalayıcılarını kullanan Windows Forms denetimleri tarafından [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]desteklenir. Aşağıdaki denetimler desteklenir.  
  
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
|Ekleyecek|  
|SplitContainer/SplitterPanel|  
|Bölücü|  
|RaftingContainer|  
|StatusStrip|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [UI Otomasyonu Denetim Türleri](ui-automation-control-types.md)
