---
title: RealTimeStylus devre dışı
ms.date: 03/30/2017
ms.assetid: e0525309-5ede-4782-837d-dbf6e5554859
ms.openlocfilehash: c2500b494f76c85e4b23823a44a180d85d5092ff
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186079"
---
# <a name="disable-the-realtimestylus-for-wpf-applications"></a>WPF Uygulamaları için RealTimeStylus'u Devre Dışı Bırakma

Windows Presentation Foundation (WPF), Windows 7 dokunmatik girişinin işlenmesi için destek oluşturmuştur. Destek tablet platformunun gerçek zamanlı kalem girişi olarak <xref:System.Windows.UIElement.OnStylusDown%2A>gelir , <xref:System.Windows.UIElement.OnStylusUp%2A>, <xref:System.Windows.UIElement.OnStylusMove%2A> ve olaylar. Windows 7 ayrıca Win32 WM_TOUCH pencere iletileri olarak çoklu dokunmatik giriş sağlar. Bu iki API aynı HWND üzerinde birbirini dışlar. Tablet platformu (WPF uygulamaları için varsayılan) üzerinden dokunma girişi etkinleştirmek WM_TOUCH iletileri devre dışı bırakarak devre dışı bırak. Sonuç olarak, WPF penceresinden dokunmatik iletileri almak için WM_TOUCH kullanmak için, WPF'deki yerleşik kalem desteğini devre dışı bmelisiniz. Bu, WM_TOUCH kullanan bir bileşeni barındıran Bir WPF penceresi gibi bir senaryoda geçerlidir.  
  
 Stylus girişini dinleyerek WPF'yi devre dışı kaldırmak için WPF penceresi tarafından eklenen tablet desteğini kaldırın.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek kod, yansımayı kullanarak varsayılan tablet platformu desteğinin nasıl kaldırılır olduğunu gösterir.  
  
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
