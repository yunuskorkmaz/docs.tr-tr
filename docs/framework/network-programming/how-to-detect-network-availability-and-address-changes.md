---
title: 'Nasıl yapılır: Ağ kullanılabilirliğini algılamak ve adres değişiklikleri'
ms.date: 03/30/2017
helpviewer_keywords:
- Network
ms.assetid: d4377115-4a76-4848-ab23-4898d65c771c
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 9056c8b2ecf18c4a57d356e7c9698984df1558eb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33396265"
---
# <a name="how-to-detect-network-availability-and-address-changes"></a><span data-ttu-id="23dc7-102">Nasıl yapılır: Ağ kullanılabilirliğini algılamak ve adres değişiklikleri</span><span class="sxs-lookup"><span data-stu-id="23dc7-102">How to: Detect Network Availability and Address Changes</span></span>
<span data-ttu-id="23dc7-103">Bu örnek, bir arabirim ağ adresi değişikliklerini algılamak gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="23dc7-103">This sample shows how to detect changes in the network address of an interface.</span></span>  
  
## <a name="example"></a><span data-ttu-id="23dc7-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="23dc7-104">Example</span></span>  
  
```  
using System;  
using System.Net;  
using System.Net.NetworkInformation;  
  
namespace Examples.Net.AddressChanges  
{  
    public class NetworkingExample  
    {  
        public static void Main()  
        {  
            NetworkChange.NetworkAddressChanged += new   
             NetworkAddressChangedEventHandler(AddressChangedCallback);  
            Console.WriteLine("Listening for address changes. Press any key to exit.");  
            Console.ReadLine();  
        }  
        static void AddressChangedCallback(object sender, EventArgs e)  
        {  
  
            NetworkInterface[] adapters = NetworkInterface.GetAllNetworkInterfaces();  
            foreach(NetworkInterface n in adapters)  
            {  
                Console.WriteLine("   {0} is {1}", n.Name, n.OperationalStatus);  
            }  
        }  
    }  
}  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="23dc7-105">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="23dc7-105">Compiling the Code</span></span>  
 <span data-ttu-id="23dc7-106">Bu örnek gerektirir:</span><span class="sxs-lookup"><span data-stu-id="23dc7-106">This example requires:</span></span>  
  
-   <span data-ttu-id="23dc7-107">Başvurular **System.Net** ad alanı.</span><span class="sxs-lookup"><span data-stu-id="23dc7-107">References to the **System.Net** namespace.</span></span>
