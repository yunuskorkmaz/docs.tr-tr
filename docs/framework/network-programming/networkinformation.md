---
title: NetworkInformation
ms.date: 03/30/2017
helpviewer_keywords:
- Network
ms.assetid: 31b44dd3-b903-4a48-8419-40419a3e4038
ms.openlocfilehash: 65b15e61acaa39c9bfc4e0bd81b26f5a211bd1f1
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71047555"
---
# <a name="networkinformation"></a>NetworkInformation
<xref:System.Net.NetworkInformation> Ad alanı, ağ olayları, değişiklikler, istatistikler ve özellikler hakkında bilgi toplamanıza olanak sağlar. Ayrıca, <xref:System.Net.NetworkInformation.Ping?displayProperty=nameWithType> sınıfını kullanarak bir uzak ana bilgisayarın erişilebilir olup olmadığını da belirleyebilirsiniz.  
  
## <a name="network-availability-and-events"></a>Ağ kullanılabilirliği ve olayları  
 <xref:System.Net.NetworkInformation.NetworkChange?displayProperty=nameWithType> Sınıfı, ağ adresinin veya kullanılabilirliğinin değiştirilip değiştirilmediğini belirlemenizi sağlar. Bu sınıfı kullanmak için değişikliği işlemek üzere bir olay işleyicisi oluşturun ve bir <xref:System.Net.NetworkInformation.NetworkAddressChangedEventHandler> <xref:System.Net.NetworkInformation.NetworkAvailabilityChangedEventHandler>veya ile ilişkilendirin. Daha fazla bilgi için [nasıl yapılır: Ağ kullanılabilirliğini ve adres değişikliklerini](how-to-detect-network-availability-and-address-changes.md)tespit edin.  
  
## <a name="network-statistics-and-properties"></a>Ağ Istatistikleri ve özellikleri  
 Ağ istatistiklerini ve özelliklerini bir arabirim ya da protokol temelinde toplayabilirsiniz. <xref:System.Net.NetworkInformation.IPInterfaceProperties> ,,<xref:System.Net.NetworkInformation.IPGlobalProperties>Ve sınıflarıbelirlibir<xref:System.Net.NetworkInformation.TcpStatistics>ağ arabirimi hakkında bilgi verir <xref:System.Net.NetworkInformation.UdpStatistics> ,,,, ve sınıfları bilgi verir <xref:System.Net.NetworkInformation.IPGlobalStatistics> <xref:System.Net.NetworkInformation.PhysicalAddress> <xref:System.Net.NetworkInformation.NetworkInterface> <xref:System.Net.NetworkInformation.NetworkInterfaceType> Katman 3 ve katman 4 paketleri hakkında. Daha fazla bilgi için [nasıl yapılır: Arabirim ve protokol bilgilerini](how-to-get-interface-and-protocol-information.md)alın.  
  
## <a name="determine-if-a-remote-host-is-reachable"></a>Uzak bir konağın erişilebilir olup olmadığını belirleme  
 Bir uzak konağın çalışır <xref:System.Net.NetworkInformation.Ping> durumda olup olmadığını, ağda ve erişilebilir olduğunu anlamak için sınıfını kullanabilirsiniz. Daha fazla bilgi için [nasıl yapılır: Ana bilgisayara](how-to-ping-a-host.md)ping gönderin.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Ağ Programlama Örnekleri](network-programming-samples.md)
- [Ağ bilgileri teknolojisi örneği](https://go.microsoft.com/fwlink/?LinkID=179564)
- [NetStat aracı teknoloji örneği](https://go.microsoft.com/fwlink/?LinkID=179562)
- [Ping Istemci teknolojisi örneği](https://go.microsoft.com/fwlink/?LinkID=179565)
