---
title: 'Nasıl yapılır: Ağ Kullanılabilirliğini Algılama ve Adres Değişiklikleri'
ms.date: 03/30/2017
helpviewer_keywords:
- Network
ms.assetid: d4377115-4a76-4848-ab23-4898d65c771c
ms.openlocfilehash: 8066286f458c730671acbafd713d0cbda4218ec3
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64624616"
---
# <a name="how-to-detect-network-availability-and-address-changes"></a><span data-ttu-id="0904d-102">Nasıl yapılır: Ağ Kullanılabilirliğini Algılama ve Adres Değişiklikleri</span><span class="sxs-lookup"><span data-stu-id="0904d-102">How to: Detect Network Availability and Address Changes</span></span>
<span data-ttu-id="0904d-103">Bu örnek, bir arabirimin ağ adresi değişikliklerini algılamak nasıl gösterir.</span><span class="sxs-lookup"><span data-stu-id="0904d-103">This sample shows how to detect changes in the network address of an interface.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0904d-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="0904d-104">Example</span></span>  
  
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
  
## <a name="compiling-the-code"></a><span data-ttu-id="0904d-105">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="0904d-105">Compiling the Code</span></span>  
 <span data-ttu-id="0904d-106">Bu örnek gerektirir:</span><span class="sxs-lookup"><span data-stu-id="0904d-106">This example requires:</span></span>  
  
- <span data-ttu-id="0904d-107">Başvurular **System.Net** ad alanı.</span><span class="sxs-lookup"><span data-stu-id="0904d-107">References to the **System.Net** namespace.</span></span>
