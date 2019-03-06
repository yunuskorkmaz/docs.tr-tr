---
title: WPF Uygulamaları için RealTimeStylus'u Devre Dışı Bırakma
ms.date: 03/30/2017
ms.assetid: e0525309-5ede-4782-837d-dbf6e5554859
ms.openlocfilehash: 6af7ff3addfe2673ab73ff0f977770f89c6234bb
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57371152"
---
# <a name="disable-the-realtimestylus-for-wpf-applications"></a>WPF Uygulamaları için RealTimeStylus'u Devre Dışı Bırakma
Windows Presentation Foundation (WPF), Windows 7 dokunma girişini işlemek için destek sunmuştur. Tablet platformun gerçek zamanlı iğne girişi aracılığıyla desteği geldi <xref:System.Windows.UIElement.OnStylusDown%2A>, <xref:System.Windows.UIElement.OnStylusUp%2A>, ve <xref:System.Windows.UIElement.OnStylusMove%2A> olayları. Windows 7, çok noktalı dokunma girişi Win32 WM_TOUCH pencere iletileri de sağlar. Bu iki API üzerinde aynı HWND karşılıklı olarak birbirini dışlar. Etkinleştirme touch tablet platformda (WPF uygulamaları için varsayılan) aracılığıyla devre dışı bırakır WM_TOUCH iletileri girin. Sonuç olarak, bir WPF penceresinden touch iletileri alacak şekilde WM_TOUCH kullanmak için yerleşik ekran kalemi desteği ' WPF'de devre dışı bırakmalısınız. Bu, bir WPF penceresi WM_TOUCH kullanan bileşen barındırma gibi senaryolarda geçerlidir.  
  
 WPF iğne girişi için dinleme devre dışı bırakmak için WPF penceresi tarafından eklenen herhangi bir tablet destek kaldırın.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek kod, yansıma kullanarak varsayılan tablet platform desteği kaldırılacağı gösterilmektedir.  
  
```  
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
