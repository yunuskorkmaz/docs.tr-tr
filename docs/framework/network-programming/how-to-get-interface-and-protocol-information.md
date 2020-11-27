---
title: 'Nasıl yapılır: Arabirim ve Protokol Bilgilerini Alma'
ms.date: 03/30/2017
helpviewer_keywords:
- Network
ms.assetid: fd88d26c-4063-495e-a253-736ac3e6b23f
ms.openlocfilehash: 6e94914ec6312fad9a22cdbb4d145ed131d233da
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96250534"
---
# <a name="how-to-get-interface-and-protocol-information"></a><span data-ttu-id="07b5c-102">Nasıl yapılır: Arabirim ve Protokol Bilgilerini Alma</span><span class="sxs-lookup"><span data-stu-id="07b5c-102">How to: Get Interface and Protocol Information</span></span>

<span data-ttu-id="07b5c-103">Bu örnek, bir ağ arabiriminin TCP istatistiklerinin nasıl okunacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="07b5c-103">This sample shows how to read the TCP statistics of a network interface.</span></span>  
  
## <a name="example"></a><span data-ttu-id="07b5c-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="07b5c-104">Example</span></span>  
  
```csharp
public static void ShowTcpStatistics(NetworkInterfaceComponent version)  
{  
    IPGlobalProperties properties =  
          IPGlobalProperties.GetIPGlobalProperties();  
    TcpStatistics tcpstat = null;  
    Console.WriteLine("");  
    switch (version)  
    {  
        case NetworkInterfaceComponent.IPv4:  
             tcpstat = properties.GetTcpIPv4Statistics();  
            Console.WriteLine("TCP/IPv4 Statistics:");  
            break;  
        case NetworkInterfaceComponent.IPv6:  
            tcpstat = properties.GetTcpIPv6Statistics();  
            Console.WriteLine("TCP/IPv6 Statistics:");  
            break;  
        default:  
            throw new ArgumentException("version");  
            break;  
    }  
    Console.WriteLine("  Minimum Transmission Timeout. : {0}",
        tcpstat.MinimumTransmissionTimeout);  
    Console.WriteLine("  Maximum Transmission Timeout. : {0}",
        tcpstat.MaximumTransmissionTimeout);  
  
    Console.WriteLine("  Connection Data:");  
    Console.WriteLine("      Current : {0}",
    tcpstat.CurrentConnections);  
    Console.WriteLine("      Cumulative : {0}",
        tcpstat.CumulativeConnections);  
    Console.WriteLine("      Initiated  : {0}",
        tcpstat.ConnectionsInitiated);  
    Console.WriteLine("      Accepted : {0}",
        tcpstat.ConnectionsAccepted);  
    Console.WriteLine("      Failed Attempts : {0}",
        tcpstat.FailedConnectionAttempts);  
    Console.WriteLine("      Reset : {0}",
        tcpstat.ResetConnections);  
  
    Console.WriteLine("");  
    Console.WriteLine("  Segment Data:");  
    Console.WriteLine("      Received  ................... : {0}",
        tcpstat.SegmentsReceived);  
    Console.WriteLine("      Sent : {0}",
        tcpstat.SegmentsSent);  
    Console.WriteLine("      Retransmitted : {0}",
        tcpstat.SegmentsResent);  
  
    Console.WriteLine("");  
}  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="07b5c-105">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="07b5c-105">Compiling the Code</span></span>  

 <span data-ttu-id="07b5c-106">Bu örnek şunları gerektirir:</span><span class="sxs-lookup"><span data-stu-id="07b5c-106">This example requires:</span></span>  
  
- <span data-ttu-id="07b5c-107">**System.net** ad alanına başvurular.</span><span class="sxs-lookup"><span data-stu-id="07b5c-107">References to the **System.Net** namespace.</span></span>
