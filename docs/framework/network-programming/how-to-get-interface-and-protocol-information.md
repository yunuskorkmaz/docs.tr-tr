---
title: 'Nasıl yapılır: arabirim ve protokol bilgilerini al'
ms.date: 03/30/2017
helpviewer_keywords:
- Network
ms.assetid: fd88d26c-4063-495e-a253-736ac3e6b23f
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 6c793f98e25c22ecb34b8aa8deb185048a08a1f9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33395092"
---
# <a name="how-to-get-interface-and-protocol-information"></a><span data-ttu-id="e40c9-102">Nasıl yapılır: arabirim ve protokol bilgilerini al</span><span class="sxs-lookup"><span data-stu-id="e40c9-102">How to: Get Interface and Protocol Information</span></span>
<span data-ttu-id="e40c9-103">Bu örnek, bir ağ arabiriminin TCP istatistikleri okumak gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="e40c9-103">This sample shows how to read the TCP statistics of a network interface.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e40c9-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="e40c9-104">Example</span></span>  
  
```  
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
  
## <a name="compiling-the-code"></a><span data-ttu-id="e40c9-105">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="e40c9-105">Compiling the Code</span></span>  
 <span data-ttu-id="e40c9-106">Bu örnek gerektirir:</span><span class="sxs-lookup"><span data-stu-id="e40c9-106">This example requires:</span></span>  
  
-   <span data-ttu-id="e40c9-107">Başvurular **System.Net** ad alanı.</span><span class="sxs-lookup"><span data-stu-id="e40c9-107">References to the **System.Net** namespace.</span></span>
