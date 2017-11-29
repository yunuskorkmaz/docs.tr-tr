---
title: NetworkInformation
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Network
ms.assetid: 31b44dd3-b903-4a48-8419-40419a3e4038
caps.latest.revision: "5"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: acf15eb79fab479036f182c58b8ec94d3ac43ea0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="networkinformation"></a><span data-ttu-id="ccf72-102">NetworkInformation</span><span class="sxs-lookup"><span data-stu-id="ccf72-102">NetworkInformation</span></span>
<span data-ttu-id="ccf72-103"><xref:System.Net.NetworkInformation> Ad alanı, ağ olayları, değişiklikleri, istatistikleri ve özellikler hakkında bilgi toplamak sağlar.</span><span class="sxs-lookup"><span data-stu-id="ccf72-103">The <xref:System.Net.NetworkInformation> namespace enables you to gather information about network events, changes, statistics, and properties.</span></span> <span data-ttu-id="ccf72-104">Kullanarak uzak ana bilgisayar erişilebilir olup olmadığını belirleyebilirsiniz <xref:System.Net.NetworkInformation.Ping?displayProperty=nameWithType> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="ccf72-104">You can also determine whether a remote host is reachable by using the <xref:System.Net.NetworkInformation.Ping?displayProperty=nameWithType> class.</span></span>  
  
## <a name="network-availability-and-events"></a><span data-ttu-id="ccf72-105">Ağ kullanılabilirliğini ve olaylar</span><span class="sxs-lookup"><span data-stu-id="ccf72-105">Network Availability and Events</span></span>  
 <span data-ttu-id="ccf72-106"><xref:System.Net.NetworkInformation.NetworkChange?displayProperty=nameWithType> Sınıfı, kullanılabilirlik ve ağ adresi değişip değişmediğini belirlemek sağlar.</span><span class="sxs-lookup"><span data-stu-id="ccf72-106">The <xref:System.Net.NetworkInformation.NetworkChange?displayProperty=nameWithType> class enables you to determine whether the network address or availability has changed.</span></span> <span data-ttu-id="ccf72-107">Bu sınıf kullanmak için değişiklik işlemek için bir olay işleyicisi oluşturun ve bu ilişkilendirmeyi bir <xref:System.Net.NetworkInformation.NetworkAddressChangedEventHandler> veya <xref:System.Net.NetworkInformation.NetworkAvailabilityChangedEventHandler>.</span><span class="sxs-lookup"><span data-stu-id="ccf72-107">To use this class, create an event handler to process the change, and associate it with a <xref:System.Net.NetworkInformation.NetworkAddressChangedEventHandler> or a <xref:System.Net.NetworkInformation.NetworkAvailabilityChangedEventHandler>.</span></span> <span data-ttu-id="ccf72-108">Daha fazla bilgi için bkz: [nasıl yapılır: Ağ kullanılabilirliğini algılamak ve adresi değişiklikleri](../../../docs/framework/network-programming/how-to-detect-network-availability-and-address-changes.md).</span><span class="sxs-lookup"><span data-stu-id="ccf72-108">For more information, see [How to: Detect Network Availability and Address Changes](../../../docs/framework/network-programming/how-to-detect-network-availability-and-address-changes.md).</span></span>  
  
## <a name="network-statistics-and-properties"></a><span data-ttu-id="ccf72-109">Ağ istatistikleri ve özellikleri</span><span class="sxs-lookup"><span data-stu-id="ccf72-109">Network Statistics and Properties</span></span>  
 <span data-ttu-id="ccf72-110">Bir arabirim veya protokolü temelinde ağ istatistikleri ve özellikleri toplayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ccf72-110">You can gather network statistics and properties on an interface or protocol basis.</span></span> <span data-ttu-id="ccf72-111"><xref:System.Net.NetworkInformation.NetworkInterface>, <xref:System.Net.NetworkInformation.NetworkInterfaceType>, Ve <xref:System.Net.NetworkInformation.PhysicalAddress> sınıfları belirli bir ağ arabirimi hakkında bilgi vermek sırada <xref:System.Net.NetworkInformation.IPInterfaceProperties>, <xref:System.Net.NetworkInformation.IPGlobalProperties>, <xref:System.Net.NetworkInformation.IPGlobalStatistics>, <xref:System.Net.NetworkInformation.TcpStatistics>, ve <xref:System.Net.NetworkInformation.UdpStatistics> sınıfları bilgi verin Katman 3 hakkında ve 4 paketleri katman.</span><span class="sxs-lookup"><span data-stu-id="ccf72-111">The <xref:System.Net.NetworkInformation.NetworkInterface>, <xref:System.Net.NetworkInformation.NetworkInterfaceType>, and <xref:System.Net.NetworkInformation.PhysicalAddress> classes give information about a particular network interface, while the <xref:System.Net.NetworkInformation.IPInterfaceProperties>, <xref:System.Net.NetworkInformation.IPGlobalProperties>, <xref:System.Net.NetworkInformation.IPGlobalStatistics>, <xref:System.Net.NetworkInformation.TcpStatistics>, and <xref:System.Net.NetworkInformation.UdpStatistics> classes give information about layer 3 and layer 4 packets.</span></span> <span data-ttu-id="ccf72-112">Daha fazla bilgi için bkz: [nasıl yapılır: arabirim almak ve protokol bilgileri](../../../docs/framework/network-programming/how-to-get-interface-and-protocol-information.md).</span><span class="sxs-lookup"><span data-stu-id="ccf72-112">For more information, see [How to: Get Interface and Protocol Information](../../../docs/framework/network-programming/how-to-get-interface-and-protocol-information.md).</span></span>  
  
## <a name="determine-if-a-remote-host-is-reachable"></a><span data-ttu-id="ccf72-113">Uzak bir ana bilgisayar erişilebilir olup olmadığını belirler</span><span class="sxs-lookup"><span data-stu-id="ccf72-113">Determine if a Remote Host is Reachable</span></span>  
 <span data-ttu-id="ccf72-114">Kullanabileceğiniz <xref:System.Net.NetworkInformation.Ping> uzak bir ana bilgisayar ve yukarı, ağ üzerinde ve erişilebilir olup olmadığını belirlemek için sınıf.</span><span class="sxs-lookup"><span data-stu-id="ccf72-114">You can use the <xref:System.Net.NetworkInformation.Ping> class to determine whether a Remote Host is up, on the network, and reachable.</span></span> <span data-ttu-id="ccf72-115">Daha fazla bilgi için bkz: [nasıl yapılır: bir ana bilgisayara Ping](../../../docs/framework/network-programming/how-to-ping-a-host.md).</span><span class="sxs-lookup"><span data-stu-id="ccf72-115">For more information, see [How to: Ping a Host](../../../docs/framework/network-programming/how-to-ping-a-host.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ccf72-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="ccf72-116">See Also</span></span>  
 [<span data-ttu-id="ccf72-117">Ağ programlama örnekleri</span><span class="sxs-lookup"><span data-stu-id="ccf72-117">Network Programming Samples</span></span>](../../../docs/framework/network-programming/network-programming-samples.md)  
 [<span data-ttu-id="ccf72-118">Ağ bilgi teknolojisi örnek</span><span class="sxs-lookup"><span data-stu-id="ccf72-118">Network Information Technology Sample</span></span>](http://go.microsoft.com/fwlink/?LinkID=179564)  
 [<span data-ttu-id="ccf72-119">NetStat araç teknolojisi örneği</span><span class="sxs-lookup"><span data-stu-id="ccf72-119">NetStat Tool Technology Sample</span></span>](http://go.microsoft.com/fwlink/?LinkID=179562)  
 [<span data-ttu-id="ccf72-120">Ping istemci teknolojisi örnek</span><span class="sxs-lookup"><span data-stu-id="ccf72-120">Ping Client Technology Sample</span></span>](http://go.microsoft.com/fwlink/?LinkID=179565)
