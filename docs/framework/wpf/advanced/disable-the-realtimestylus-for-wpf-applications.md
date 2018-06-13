---
title: WPF Uygulamaları için RealTimeStylus'u Devre Dışı Bırakma
ms.date: 03/30/2017
ms.assetid: e0525309-5ede-4782-837d-dbf6e5554859
ms.openlocfilehash: ddf4a7f4488f957b2f413d61ad02aa59beba30f6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33545668"
---
# <a name="disable-the-realtimestylus-for-wpf-applications"></a><span data-ttu-id="4fc35-102">WPF Uygulamaları için RealTimeStylus'u Devre Dışı Bırakma</span><span class="sxs-lookup"><span data-stu-id="4fc35-102">Disable the RealTimeStylus for WPF Applications</span></span>
<span data-ttu-id="4fc35-103">Windows Presentation Foundation (WPF), Windows 7 dokunmatik girişi işlemek için destek oluşturdu. Destek tablet platformun gerçek zamanlı kalem giriş olarak üzerinden gelen <xref:System.Windows.UIElement.OnStylusDown%2A>, <xref:System.Windows.UIElement.OnStylusUp%2A>, ve <xref:System.Windows.UIElement.OnStylusMove%2A> olaylar.</span><span class="sxs-lookup"><span data-stu-id="4fc35-103">Windows Presentation Foundation (WPF) has built in support for processing Windows 7 touch input.The support comes through the tablet platform’s real-time stylus input as <xref:System.Windows.UIElement.OnStylusDown%2A>, <xref:System.Windows.UIElement.OnStylusUp%2A>, and <xref:System.Windows.UIElement.OnStylusMove%2A> events.</span></span> <span data-ttu-id="4fc35-104">Windows 7, Win32 WM_TOUCH pencere iletileri şeklinde çoklu dokunma girişi de sağlar.</span><span class="sxs-lookup"><span data-stu-id="4fc35-104">Windows 7 also provides multi-touch input as Win32 WM_TOUCH window messages.</span></span> <span data-ttu-id="4fc35-105">Bu iki API aynı HWND üzerinde karşılıklı olarak birbirini dışlar.</span><span class="sxs-lookup"><span data-stu-id="4fc35-105">These two APIs are mutually exclusive on the same HWND.</span></span> <span data-ttu-id="4fc35-106">Etkinleştirme dokunma tablet platform (WPF uygulamaları için varsayılan) aracılığıyla devre dışı bırakır WM_TOUCH iletilerini girin.</span><span class="sxs-lookup"><span data-stu-id="4fc35-106">Enabling touch input via the tablet platform (the default for WPF applications) disables WM_TOUCH messages.</span></span> <span data-ttu-id="4fc35-107">Sonuç olarak, WPF penceresinden dokunma iletileri almak için WM_TOUCH kullanmak için WPF içinde yerleşik kalem desteğini devre dışı bırakmalısınız.</span><span class="sxs-lookup"><span data-stu-id="4fc35-107">As a result, to use WM_TOUCH to receive touch messages from a WPF window, you must disable the built-in stylus support in WPF.</span></span> <span data-ttu-id="4fc35-108">Bu, WM_TOUCH kullanan bir bileşeni barındıran bir WPF penceresi gibi senaryolarda geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="4fc35-108">This is applicable in a scenario such as a WPF window hosting a component that uses WM_TOUCH.</span></span>  
  
 <span data-ttu-id="4fc35-109">Kalem girişini Dinlemesini devre dışı bırakmak için WPF penceresi tarafından eklenen herhangi bir tablet desteğini kaldırın.</span><span class="sxs-lookup"><span data-stu-id="4fc35-109">To disable WPF listening to stylus input, remove any tablet support added by the WPF window.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4fc35-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="4fc35-110">Example</span></span>  
 <span data-ttu-id="4fc35-111">Aşağıdaki örnek kod, yansıma kullanarak varsayılan tablet platform desteği kaldırma gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="4fc35-111">The following sample code shows how to remove the default tablet platform support by using reflection.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="4fc35-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="4fc35-112">See Also</span></span>  
 [<span data-ttu-id="4fc35-113">Ekran Kaleminden Gelen Girişi Önleme</span><span class="sxs-lookup"><span data-stu-id="4fc35-113">Intercepting Input from the Stylus</span></span>](../../../../docs/framework/wpf/advanced/intercepting-input-from-the-stylus.md)
