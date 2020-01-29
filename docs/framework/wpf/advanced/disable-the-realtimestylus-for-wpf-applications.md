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
# <a name="disable-the-realtimestylus-for-wpf-applications"></a><span data-ttu-id="d15b6-102">WPF Uygulamaları için RealTimeStylus'u Devre Dışı Bırakma</span><span class="sxs-lookup"><span data-stu-id="d15b6-102">Disable the RealTimeStylus for WPF Applications</span></span>

<span data-ttu-id="d15b6-103">Windows Presentation Foundation (WPF), Windows 7 Touch girişini işlemek için yerleşik desteğe sahiptir.</span><span class="sxs-lookup"><span data-stu-id="d15b6-103">Windows Presentation Foundation (WPF) has built in support for processing Windows 7 touch input.</span></span> <span data-ttu-id="d15b6-104">Destek, tablet platformunun gerçek zamanlı iğne girişi <xref:System.Windows.UIElement.OnStylusDown%2A>, <xref:System.Windows.UIElement.OnStylusUp%2A>ve <xref:System.Windows.UIElement.OnStylusMove%2A> olayları aracılığıyla sunulur.</span><span class="sxs-lookup"><span data-stu-id="d15b6-104">The support comes through the tablet platform’s real-time stylus input as <xref:System.Windows.UIElement.OnStylusDown%2A>, <xref:System.Windows.UIElement.OnStylusUp%2A>, and <xref:System.Windows.UIElement.OnStylusMove%2A> events.</span></span> <span data-ttu-id="d15b6-105">Windows 7 Ayrıca, Win32 WM_TOUCH pencere iletileri olarak çok dokunmalı giriş de sağlar.</span><span class="sxs-lookup"><span data-stu-id="d15b6-105">Windows 7 also provides multi-touch input as Win32 WM_TOUCH window messages.</span></span> <span data-ttu-id="d15b6-106">Bu iki API aynı HWND üzerinde birbirini dışlıyor.</span><span class="sxs-lookup"><span data-stu-id="d15b6-106">These two APIs are mutually exclusive on the same HWND.</span></span> <span data-ttu-id="d15b6-107">Tablet platformu aracılığıyla dokunmatik girişi etkinleştirme (WPF uygulamaları için varsayılan) WM_TOUCH iletileri devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="d15b6-107">Enabling touch input via the tablet platform (the default for WPF applications) disables WM_TOUCH messages.</span></span> <span data-ttu-id="d15b6-108">Sonuç olarak, WPF penceresinden dokunmatik ileti almak için WM_TOUCH kullanmak için WPF 'de yerleşik ekran kalemi desteğini devre dışı bırakmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="d15b6-108">As a result, to use WM_TOUCH to receive touch messages from a WPF window, you must disable the built-in stylus support in WPF.</span></span> <span data-ttu-id="d15b6-109">Bu, WM_TOUCH kullanan bir bileşeni barındıran WPF penceresi gibi bir senaryoda geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="d15b6-109">This is applicable in a scenario such as a WPF window hosting a component that uses WM_TOUCH.</span></span>  
  
 <span data-ttu-id="d15b6-110">WPF 'yi ekran kalemi girişine dinlemeyi devre dışı bırakmak için WPF penceresi tarafından eklenen tüm tablet desteğini kaldırın.</span><span class="sxs-lookup"><span data-stu-id="d15b6-110">To disable WPF listening to stylus input, remove any tablet support added by the WPF window.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d15b6-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="d15b6-111">Example</span></span>  
 <span data-ttu-id="d15b6-112">Aşağıdaki örnek kod, yansıma kullanarak varsayılan tablet platformu desteğinin nasıl kaldırılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="d15b6-112">The following sample code shows how to remove the default tablet platform support by using reflection.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="d15b6-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d15b6-113">See also</span></span>

- [<span data-ttu-id="d15b6-114">Ekran Kaleminden Gelen Girişi Önleme</span><span class="sxs-lookup"><span data-stu-id="d15b6-114">Intercepting Input from the Stylus</span></span>](intercepting-input-from-the-stylus.md)
