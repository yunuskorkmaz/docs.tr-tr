---
title: RealTimeStylus 'ı devre dışı bırak
ms.date: 03/30/2017
ms.assetid: e0525309-5ede-4782-837d-dbf6e5554859
ms.openlocfilehash: 74145c32af7e9ebbc774a0301e205aa1eb1539b3
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76737944"
---
# <a name="disable-the-realtimestylus-for-wpf-applications"></a>WPF Uygulamaları için RealTimeStylus'u Devre Dışı Bırakma

Windows Presentation Foundation (WPF), Windows 7 Touch girişini işlemek için yerleşik desteğe sahiptir. Destek, tablet platformunun gerçek zamanlı iğne girişi <xref:System.Windows.UIElement.OnStylusDown%2A>, <xref:System.Windows.UIElement.OnStylusUp%2A>ve <xref:System.Windows.UIElement.OnStylusMove%2A> olayları aracılığıyla sunulur. Windows 7 Ayrıca, Win32 WM_TOUCH pencere iletileri olarak çok dokunmalı giriş de sağlar. Bu iki API aynı HWND üzerinde birbirini dışlıyor. Tablet platformu aracılığıyla dokunmatik girişi etkinleştirme (WPF uygulamaları için varsayılan) WM_TOUCH iletileri devre dışı bırakır. Sonuç olarak, WPF penceresinden dokunmatik ileti almak için WM_TOUCH kullanmak için WPF 'de yerleşik ekran kalemi desteğini devre dışı bırakmanız gerekir. Bu, WM_TOUCH kullanan bir bileşeni barındıran WPF penceresi gibi bir senaryoda geçerlidir.  
  
 WPF 'yi ekran kalemi girişine dinlemeyi devre dışı bırakmak için WPF penceresi tarafından eklenen tüm tablet desteğini kaldırın.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek kod, yansıma kullanarak varsayılan tablet platformu desteğinin nasıl kaldırılacağını gösterir.  
  
```csharp  
public static void DisableWPFTabletSupport()  
{  
    // Get a collection of the tablet devices for this window.    
    TabletDeviceCollection devices = System.Windows.Input.Tablet.TabletDevices;  
  
    if (devices.Count > 0)  
    {     
        // Get the Type of InputManager.  
        Type inputManagerType = typeof(System.Windows.Input.InputManager);  
  
        // Call the StylusLogic method on the InputManager.Current instance.  
        object stylusLogic = inputManagerType.InvokeMember("StylusLogic",  
                    BindingFlags.GetProperty | BindingFlags.Instance | BindingFlags.NonPublic,  
                    null, InputManager.Current, null);  
  
        if (stylusLogic != null)  
        {  
            //  Get the type of the stylusLogic returned from the call to StylusLogic.  
            Type stylusLogicType = stylusLogic.GetType();  
  
            // Loop until there are no more devices to remove.  
            while (devices.Count > 0)  
            {  
                // Remove the first tablet device in the devices collection.  
                stylusLogicType.InvokeMember("OnTabletRemoved",  
                        BindingFlags.InvokeMethod | BindingFlags.Instance | BindingFlags.NonPublic,  
                        null, stylusLogic, new object[] { (uint)0 });  
            }                  
        }  
  
    }  
}  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Ekran Kaleminden Gelen Girişi Önleme](intercepting-input-from-the-stylus.md)
