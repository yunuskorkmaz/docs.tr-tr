---
title: UI Otomasyonu Pencere Denetim Düzenini Uygulama
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, Window
- UI Automation, Window control pattern
- Window control pattern
ms.assetid: a28cb286-296e-4a62-b4cb-55ad636ebccc
ms.openlocfilehash: d8afaa13bd4eca9f9fcd4c8ed26c09c62ad74931
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74447036"
---
# <a name="implementing-the-ui-automation-window-control-pattern"></a>UI Otomasyonu Pencere Denetim Düzenini Uygulama
> [!NOTE]
> This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace. For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).  
  
 This topic introduces guidelines and conventions for implementing <xref:System.Windows.Automation.Provider.IWindowProvider>, including information about <xref:System.Windows.Automation.WindowPattern> properties, methods, and events. Links to additional references are listed at the end of the topic.  
  
 The <xref:System.Windows.Automation.WindowPattern> control pattern is used to support controls that provide fundamental window-based functionality within a traditional graphical user interface (GUI). Examples of controls that must implement this control pattern include top-level application windows, multiple-document interface (MDI) child windows, resizable split pane controls, modal dialogs and balloon help windows.  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a>Implementation Guidelines and Conventions  
 When implementing the Window control pattern, note the following guidelines and conventions:  
  
- To support the ability to modify both window size and screen position using UI Automation, a control must implement <xref:System.Windows.Automation.Provider.ITransformProvider> in addition to <xref:System.Windows.Automation.Provider.IWindowProvider>.  
  
- Controls that contain title bars and title bar elements that enable the control to be moved, resized, maximized, minimized, or closed are typically required to implement <xref:System.Windows.Automation.Provider.IWindowProvider>.  
  
- Controls such as tooltip pop-ups and combo box or menu drop-downs do not typically implement <xref:System.Windows.Automation.Provider.IWindowProvider>.  
  
- Balloon help windows are differentiated from basic tooltip pop-ups by the provision of a window-like Close button.  
  
- Full-screen mode is not supported by IWindowProvider as it is feature-specific to an application and is not typical window behavior.  
  
<a name="Required_Members_for_IWindowProvider"></a>   
## <a name="required-members-for-iwindowprovider"></a>Required Members for IWindowProvider  
 The following properties, methods, and events are required for the IWindowProvider interface.  
  
|Required member|Member type|Notlar|  
|---------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.InteractionState%2A>|Özellik|Yok.|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.IsModal%2A>|Özellik|Yok.|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.IsTopmost%2A>|Özellik|Yok.|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.Maximizable%2A>|Özellik|Yok.|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.Minimizable%2A>|Özellik|Yok.|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.VisualState%2A>|Özellik|Yok.|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.Close%2A>|Yöntem|Yok.|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.SetVisualState%2A>|Yöntem|Yok.|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.WaitForInputIdle%2A>|Yöntem|Yok.|  
|<xref:System.Windows.Automation.WindowPattern.WindowClosedEvent>|Olay|Yok.|  
|<xref:System.Windows.Automation.WindowPattern.WindowOpenedEvent>|Olay|Yok.|  
|<xref:System.Windows.Automation.WindowInteractionState>|Olay|Is not guaranteed to be <xref:System.Windows.Automation.WindowInteractionState.ReadyForUserInteraction>|  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a>Özel Durumlar  
 Providers must throw the following exceptions.  
  
|Özel durum türü|Koşul|  
|--------------------|---------------|  
|<xref:System.InvalidOperationException>|<xref:System.Windows.Automation.Provider.IWindowProvider.SetVisualState%2A><br /><br /> -   When a control does not support a requested behavior.|  
|<xref:System.ArgumentOutOfRangeException>|<xref:System.Windows.Automation.Provider.IWindowProvider.WaitForInputIdle%2A><br /><br /> -   When the parameter is not a valid number.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [UI Otomasyonu Denetim Desenlerine Genel Bakış](ui-automation-control-patterns-overview.md)
- [UI Otomasyonu Sağlayıcıda Denetim Düzenleri Desteği](support-control-patterns-in-a-ui-automation-provider.md)
- [İstemciler İçin UI Otomasyonu Denetim Düzenleri](ui-automation-control-patterns-for-clients.md)
- [UI Otomasyon Ağacına Genel Bakış](ui-automation-tree-overview.md)
- [UI Otomasyonunda Önbelleğe Almayı Kullanma](use-caching-in-ui-automation.md)
