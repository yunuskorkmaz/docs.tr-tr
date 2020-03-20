---
title: Standart Denetimler İçin UI Otomasyon Desteği
ms.date: 03/30/2017
helpviewer_keywords:
- controls, UI Automation support for
- UI Automation, support for standard controls
ms.assetid: 3770ea8a-2655-4add-9c59-fe0610ad5084
ms.openlocfilehash: 36028d589e98177f6a0e83092edd656860b1a8d4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179857"
---
# <a name="ui-automation-support-for-standard-controls"></a>Standart Denetimler İçin UI Otomasyon Desteği
> [!NOTE]
> Bu dokümantasyon, ad alanında tanımlanan yönetilen [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] sınıfları kullanmak <xref:System.Windows.Automation> isteyen .NET Framework geliştiricileri için tasarlanmıştır. Hakkında en son [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]bilgi için [Bkz. Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).  
  
 Bu [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)]konu, [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] Win32 ve Windows Forms çerçeveleri için geliştirilen uygulamalarda standart denetimdesteği hakkında bilgi içerir.  
  
<a name="Windows_Presentation_Foundation_Controls"></a>
## <a name="windows-presentation-foundation-controls"></a>Windows Sunum Temel Denetimleri  
 Kullanıcı [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] etkileşimi için bilgi veya destek sağlayan tüm [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]denetim öğeleri için tam yerel destek var. Paneller gibi diğer öğeler için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]görünmez.  
  
<a name="Win32_Controls"></a>
## <a name="win32-controls"></a>Win32 Kontroller  
 Win32 denetimlerinin çoğu, UIAutomationClientsideProviders.dll'deki istemci tarafındaki sağlayıcılar [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] aracılığıyla uygulanır. Bu derleme otomatik olarak UI Automation istemci uygulamalarında kullanılmak üzere kaydedilir.  
  
 Tam destek yalnızca *ComCtrl32.dll'nin*6.  
  
 Aşağıdaki denetimler desteklenir.  
  
|Sınıf adı|Kontrol Türü|  
|----------------|------------------|  
|Düğme|Düğme|  
|Düğme|RadioButton|  
|Düğme|Grup|  
|Düğme|CheckBox|  
|Düğme|Köprü|  
|Düğme|Splitbutton|  
|Düğme|CheckBox|  
|ComboBoxEx32|ComboBox|  
|ComboBox|ComboBox|  
|Düzenle|Belge|  
|Düzenle|Düzenle|  
|SysLink|Köprü|  
|Statik|Metin|  
|Statik|Görüntü|  
|SysIPAddress32|Özel|  
|SysHeader32|Üstbilgi/Üstbilgi Öğesi|  
|SysListView32|DataGrid|  
|SysListView32|Liste|  
|ListBox|Liste|  
|ListBox|Listıtem|  
|#32768|Menü|  
|#32768|MenuItem|  
|msctls_progress32|ProgressBar|  
|Richedit|Belge. Nota bakın.|  
|RichEdit20A|Belge|  
|ZenginEdit20W|Belge|  
|ZenginEdit50W|Belge|  
|ScrollBar|Kaydırıcı|  
|msctls_trackbar32|Kaydırıcı|  
|msctls_updown32|Değer Değiştirici|  
|msctls_statusbar32|StatusBar|  
|SysTabControl32|Tab|  
|SysTabControl32|Tabıtem|  
|Araç ÇubuğuWindow32|ToolBar|  
|Araç ÇubuğuWindow32|MenuItem|  
|Araç ÇubuğuWindow32|Düğme|  
|Araç ÇubuğuWindow32|CheckBox|  
|Araç ÇubuğuWindow32|RadioButton|  
|Araç ÇubuğuWindow32|Ayırıcı|  
|tooltips_class32|ToolTip|  
|#32774|ToolTip|  
|RebarWindow32|Araç Çubuğu|  
|SysTreeView32|Ağaç|  
|SysTreeView32|Treeıtem|  
  
 **Not** RichEdit denetimi yalnızca Windows Vista (RichEd20.dll sürüm 3.1 ve daha sonra ve MsftEdit.dll sürüm 4.1 ve sonraki sürümlerde) ile gönderilen sürümler için desteklenir.  
  
 Aşağıdaki denetimler desteklenmez.  
  
|Sınıf adı|Denetim türü|  
|----------------|------------------|  
|SysAnimate32|Görüntü|  
|SysPager|Değer Değiştirici|  
|SysDateTimePick32|Özel|  
|SysMonthCal32|Takvim|  
|MS_WINNOTE|Araç İpucu|  
|VBBubble|Araç İpucu|  
|ScrollBar (bağımsız denetim olarak kullanıldığında)|Kaydırıcı|  
|SuperGrid|Özel|  
  
<a name="Windows_Forms_Controls"></a>
## <a name="windows-forms-controls"></a>Windows Forms Denetimleri  
 Windows Forms denetimleri, UIAutomationClientsideProviders.dll'deki istemci tarafındaki sağlayıcılar [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] aracılığıyla uygulanır. Bu derleme otomatik olarak UI Automation istemci uygulamalarında kullanılmak üzere kaydedilir.  
  
 Genellikle, Win32 ortak denetimleri için yönetilen Windows Forms denetimleri tarafından [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]desteklenir. Aşağıdaki denetimler desteklenir.  
  
|Sınıf Adı|  
|----------------|  
|Düğme|  
|CheckBox|  
|Checkedlistbox|  
|Colordialog|  
|ComboBox|  
|KlasörTarayıcı|  
|FontDialog|  
|GroupBox|  
|Hscrollbar|  
|ımagelist|  
|Etiketle|  
|ListBox|  
|ListView|  
|MainMenu/ContextMenu|  
|MonthCalendar|  
|Notifyıcon|  
|Openfiledialog|  
|SayfaSetupDialog|  
|PrintDialog|  
|ProgressBar|  
|RadioButton|  
|RichTextBox|  
|Savefiledialog|  
|ScrollableControl|  
|Soundplayer|  
|StatusBar|  
|Sekme/Sekme Sayfası|  
|TextBox|  
|Zamanlayıcı|  
|Araç Çubuğu|  
|ToolTip|  
|Trackbar|  
|TreeView|  
|Vscrollbar|  
|Webbrowser|  
  
 Aşağıdaki denetimler yalnızca [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] Microsoft Etkin Erişilebilirlik desteği ile maruz kalır. Bazı işlevler kullanılamayabilir.  
  
|Kontrol Adı|  
|------------------|  
|BindingSource|  
|DataGrid|  
|Datagridview|  
|DataNavigator|  
|DomainUpDown|  
|Hata Sağlayıcısı|  
|Flowlayoutpanel|  
|Form|  
|Bağlantı Etiketi|  
|Yardım Sağlayıcısı|  
|Maskedtextbox|  
|MenüŞeridi/BağlammenüŞeridi|  
|NumericUpDown|  
|Panel|  
|Picturebox|  
|Printdocument|  
|PrintPreview-Control|  
|PrintPreview-Dialog|  
|Emlak Grid|  
|Usercontrol|  
|ToolStrip|  
|Tablelayoutpanel|  
|SplitContainer/SplitterPanel|  
|Bölücü|  
|RaftingKonteyner|  
|StatusStrip|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [UI Otomasyon Denetim Türleri](ui-automation-control-types.md)
