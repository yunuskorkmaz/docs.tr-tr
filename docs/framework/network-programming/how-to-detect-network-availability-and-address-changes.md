---
description: 'Hakkında daha fazla bilgi edinin: nasıl yapılır: Ağ kullanılabilirliğini algılama ve adres değişiklikleri'
title: 'Nasıl yapılır: Ağ Kullanılabilirliğini Algılama ve Adres Değişiklikleri'
ms.date: 03/30/2017
helpviewer_keywords:
- Network
ms.assetid: d4377115-4a76-4848-ab23-4898d65c771c
ms.openlocfilehash: b9465cbfc538c551725d6510cac3c73d006b7b59
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99747445"
---
# <a name="how-to-detect-network-availability-and-address-changes"></a><span data-ttu-id="b666a-103">Nasıl yapılır: Ağ Kullanılabilirliğini Algılama ve Adres Değişiklikleri</span><span class="sxs-lookup"><span data-stu-id="b666a-103">How to: Detect Network Availability and Address Changes</span></span>

<span data-ttu-id="b666a-104">Bu örnek, bir arabirimin ağ adresindeki değişikliklerin nasıl algılanacağını göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="b666a-104">This sample shows how to detect changes in the network address of an interface.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b666a-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="b666a-105">Example</span></span>  
  
```csharp
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
  
## <a name="compiling-the-code"></a><span data-ttu-id="b666a-106">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="b666a-106">Compiling the Code</span></span>  

 <span data-ttu-id="b666a-107">Bu örnek şunları gerektirir:</span><span class="sxs-lookup"><span data-stu-id="b666a-107">This example requires:</span></span>  
  
- <span data-ttu-id="b666a-108">**System.net** ad alanına başvurular.</span><span class="sxs-lookup"><span data-stu-id="b666a-108">References to the **System.Net** namespace.</span></span>
