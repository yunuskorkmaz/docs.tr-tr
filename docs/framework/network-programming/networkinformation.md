---
description: 'Daha fazla bilgi edinin: NetworkInformation'
title: NetworkInformation
ms.date: 03/30/2017
helpviewer_keywords:
- Network
ms.assetid: 31b44dd3-b903-4a48-8419-40419a3e4038
ms.openlocfilehash: 9092fd0593d9046f419018b882c08066a6bc654c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99785711"
---
# <a name="networkinformation"></a><span data-ttu-id="c96bf-103">NetworkInformation</span><span class="sxs-lookup"><span data-stu-id="c96bf-103">NetworkInformation</span></span>

<span data-ttu-id="c96bf-104"><xref:System.Net.NetworkInformation>Ad alanı, ağ olayları, değişiklikler, istatistikler ve özellikler hakkında bilgi toplamanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="c96bf-104">The <xref:System.Net.NetworkInformation> namespace enables you to gather information about network events, changes, statistics, and properties.</span></span> <span data-ttu-id="c96bf-105">Ayrıca, sınıfını kullanarak bir uzak ana bilgisayarın erişilebilir olup olmadığını da belirleyebilirsiniz <xref:System.Net.NetworkInformation.Ping?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="c96bf-105">You can also determine whether a remote host is reachable by using the <xref:System.Net.NetworkInformation.Ping?displayProperty=nameWithType> class.</span></span>  
  
## <a name="network-availability-and-events"></a><span data-ttu-id="c96bf-106">Ağ kullanılabilirliği ve olayları</span><span class="sxs-lookup"><span data-stu-id="c96bf-106">Network Availability and Events</span></span>  

 <span data-ttu-id="c96bf-107"><xref:System.Net.NetworkInformation.NetworkChange?displayProperty=nameWithType>Sınıfı, ağ adresinin veya kullanılabilirliğinin değiştirilip değiştirilmediğini belirlemenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="c96bf-107">The <xref:System.Net.NetworkInformation.NetworkChange?displayProperty=nameWithType> class enables you to determine whether the network address or availability has changed.</span></span> <span data-ttu-id="c96bf-108">Bu sınıfı kullanmak için değişikliği işlemek üzere bir olay işleyicisi oluşturun ve bir veya ile ilişkilendirin <xref:System.Net.NetworkInformation.NetworkAddressChangedEventHandler> <xref:System.Net.NetworkInformation.NetworkAvailabilityChangedEventHandler> .</span><span class="sxs-lookup"><span data-stu-id="c96bf-108">To use this class, create an event handler to process the change, and associate it with a <xref:System.Net.NetworkInformation.NetworkAddressChangedEventHandler> or a <xref:System.Net.NetworkInformation.NetworkAvailabilityChangedEventHandler>.</span></span> <span data-ttu-id="c96bf-109">Daha fazla bilgi için bkz. [nasıl yapılır: algılama ağ kullanılabilirliği ve adres değişiklikleri](how-to-detect-network-availability-and-address-changes.md).</span><span class="sxs-lookup"><span data-stu-id="c96bf-109">For more information, see [How to: Detect Network Availability and Address Changes](how-to-detect-network-availability-and-address-changes.md).</span></span>  
  
## <a name="network-statistics-and-properties"></a><span data-ttu-id="c96bf-110">Ağ Istatistikleri ve özellikleri</span><span class="sxs-lookup"><span data-stu-id="c96bf-110">Network Statistics and Properties</span></span>  

 <span data-ttu-id="c96bf-111">Ağ istatistiklerini ve özelliklerini bir arabirim ya da protokol temelinde toplayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c96bf-111">You can gather network statistics and properties on an interface or protocol basis.</span></span> <span data-ttu-id="c96bf-112">, <xref:System.Net.NetworkInformation.NetworkInterface> , <xref:System.Net.NetworkInformation.NetworkInterfaceType> Ve <xref:System.Net.NetworkInformation.PhysicalAddress> sınıfları belirli bir ağ arabirimi hakkında bilgi verir,,,, <xref:System.Net.NetworkInformation.IPInterfaceProperties> <xref:System.Net.NetworkInformation.IPGlobalProperties> <xref:System.Net.NetworkInformation.IPGlobalStatistics> <xref:System.Net.NetworkInformation.TcpStatistics> ve <xref:System.Net.NetworkInformation.UdpStatistics> sınıfları katman 3 ve katman 4 paketleri hakkında bilgi verir.</span><span class="sxs-lookup"><span data-stu-id="c96bf-112">The <xref:System.Net.NetworkInformation.NetworkInterface>, <xref:System.Net.NetworkInformation.NetworkInterfaceType>, and <xref:System.Net.NetworkInformation.PhysicalAddress> classes give information about a particular network interface, while the <xref:System.Net.NetworkInformation.IPInterfaceProperties>, <xref:System.Net.NetworkInformation.IPGlobalProperties>, <xref:System.Net.NetworkInformation.IPGlobalStatistics>, <xref:System.Net.NetworkInformation.TcpStatistics>, and <xref:System.Net.NetworkInformation.UdpStatistics> classes give information about layer 3 and layer 4 packets.</span></span> <span data-ttu-id="c96bf-113">Daha fazla bilgi için bkz. [nasıl yapılır: arabirim ve protokol alma bilgileri](how-to-get-interface-and-protocol-information.md).</span><span class="sxs-lookup"><span data-stu-id="c96bf-113">For more information, see [How to: Get Interface and Protocol Information](how-to-get-interface-and-protocol-information.md).</span></span>  
  
## <a name="determine-if-a-remote-host-is-reachable"></a><span data-ttu-id="c96bf-114">Uzak bir konağın erişilebilir olup olmadığını belirleme</span><span class="sxs-lookup"><span data-stu-id="c96bf-114">Determine if a Remote Host is Reachable</span></span>  

 <span data-ttu-id="c96bf-115"><xref:System.Net.NetworkInformation.Ping>Bir uzak konağın çalışır durumda olup olmadığını, ağda ve erişilebilir olduğunu anlamak için sınıfını kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c96bf-115">You can use the <xref:System.Net.NetworkInformation.Ping> class to determine whether a Remote Host is up, on the network, and reachable.</span></span> <span data-ttu-id="c96bf-116">Daha fazla bilgi için bkz. [nasıl yapılır: ping a Host](how-to-ping-a-host.md).</span><span class="sxs-lookup"><span data-stu-id="c96bf-116">For more information, see [How to: Ping a Host](how-to-ping-a-host.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c96bf-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c96bf-117">See also</span></span>

- [<span data-ttu-id="c96bf-118">Ağ Programlama Örnekleri</span><span class="sxs-lookup"><span data-stu-id="c96bf-118">Network Programming Samples</span></span>](network-programming-samples.md)

<!-- to-do: review sample links
- [Network Information Technology Sample](https://archive.msdn.microsoft.com/nclsamples/Wiki/View.aspx?title=Network%20Information)
- [NetStat Tool Technology Sample](https://archive.msdn.microsoft.com/nclsamples/Wiki/View.aspx?title=NetStat%20Tool)
- [Ping Client Technology Sample](https://archive.msdn.microsoft.com/nclsamples/Wiki/View.aspx?title=Ping%20Client)
-->
