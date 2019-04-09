---
title: WPF Uygulamaları için RealTimeStylus'u Devre Dışı Bırakma
ms.date: 03/30/2017
ms.assetid: e0525309-5ede-4782-837d-dbf6e5554859
ms.openlocfilehash: e44b71ac5af64ab3a6cb008db71e5a8881592e91
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59124689"
---
# <a name="disable-the-realtimestylus-for-wpf-applications"></a><span data-ttu-id="ec177-102">WPF Uygulamaları için RealTimeStylus'u Devre Dışı Bırakma</span><span class="sxs-lookup"><span data-stu-id="ec177-102">Disable the RealTimeStylus for WPF Applications</span></span>
<span data-ttu-id="ec177-103">Windows Presentation Foundation (WPF), Windows 7 dokunma girişini işlemek için destek sunmuştur. Tablet platformun gerçek zamanlı iğne girişi aracılığıyla desteği geldi <xref:System.Windows.UIElement.OnStylusDown%2A>, <xref:System.Windows.UIElement.OnStylusUp%2A>, ve <xref:System.Windows.UIElement.OnStylusMove%2A> olayları.</span><span class="sxs-lookup"><span data-stu-id="ec177-103">Windows Presentation Foundation (WPF) has built in support for processing Windows 7 touch input.The support comes through the tablet platform’s real-time stylus input as <xref:System.Windows.UIElement.OnStylusDown%2A>, <xref:System.Windows.UIElement.OnStylusUp%2A>, and <xref:System.Windows.UIElement.OnStylusMove%2A> events.</span></span> <span data-ttu-id="ec177-104">Windows 7, çok noktalı dokunma girişi Win32 WM_TOUCH pencere iletileri de sağlar.</span><span class="sxs-lookup"><span data-stu-id="ec177-104">Windows 7 also provides multi-touch input as Win32 WM_TOUCH window messages.</span></span> <span data-ttu-id="ec177-105">Bu iki API üzerinde aynı HWND karşılıklı olarak birbirini dışlar.</span><span class="sxs-lookup"><span data-stu-id="ec177-105">These two APIs are mutually exclusive on the same HWND.</span></span> <span data-ttu-id="ec177-106">Etkinleştirme touch tablet platformda (WPF uygulamaları için varsayılan) aracılığıyla devre dışı bırakır WM_TOUCH iletileri girin.</span><span class="sxs-lookup"><span data-stu-id="ec177-106">Enabling touch input via the tablet platform (the default for WPF applications) disables WM_TOUCH messages.</span></span> <span data-ttu-id="ec177-107">Sonuç olarak, bir WPF penceresinden touch iletileri alacak şekilde WM_TOUCH kullanmak için yerleşik ekran kalemi desteği ' WPF'de devre dışı bırakmalısınız.</span><span class="sxs-lookup"><span data-stu-id="ec177-107">As a result, to use WM_TOUCH to receive touch messages from a WPF window, you must disable the built-in stylus support in WPF.</span></span> <span data-ttu-id="ec177-108">Bu, bir WPF penceresi WM_TOUCH kullanan bileşen barındırma gibi senaryolarda geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="ec177-108">This is applicable in a scenario such as a WPF window hosting a component that uses WM_TOUCH.</span></span>  
  
 <span data-ttu-id="ec177-109">WPF iğne girişi için dinleme devre dışı bırakmak için WPF penceresi tarafından eklenen herhangi bir tablet destek kaldırın.</span><span class="sxs-lookup"><span data-stu-id="ec177-109">To disable WPF listening to stylus input, remove any tablet support added by the WPF window.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ec177-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="ec177-110">Example</span></span>  
 <span data-ttu-id="ec177-111">Aşağıdaki örnek kod, yansıma kullanarak varsayılan tablet platform desteği kaldırılacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="ec177-111">The following sample code shows how to remove the default tablet platform support by using reflection.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="ec177-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ec177-112">See also</span></span>

- [<span data-ttu-id="ec177-113">Ekran Kaleminden Gelen Girişi Önleme</span><span class="sxs-lookup"><span data-stu-id="ec177-113">Intercepting Input from the Stylus</span></span>](intercepting-input-from-the-stylus.md)
