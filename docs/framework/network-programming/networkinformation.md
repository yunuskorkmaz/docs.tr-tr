---
title: NetworkInformation
ms.date: 03/30/2017
helpviewer_keywords:
- Network
ms.assetid: 31b44dd3-b903-4a48-8419-40419a3e4038
ms.openlocfilehash: 0820ad6a6d5000ef7ea575e856d883ba5325b1b0
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59230986"
---
# <a name="networkinformation"></a>NetworkInformation
<xref:System.Net.NetworkInformation> Ad alanı ağ olayları, değişiklikler, istatistikler ve özellikler hakkında bilgi toplamanızı sağlar. Kullanarak uzak ana erişilebilir olup olmadığını belirleyebilirsiniz <xref:System.Net.NetworkInformation.Ping?displayProperty=nameWithType> sınıfı.  
  
## <a name="network-availability-and-events"></a>Ağ kullanılabilirliğine ve olaylar  
 <xref:System.Net.NetworkInformation.NetworkChange?displayProperty=nameWithType> Sınıfı, kullanılabilirlik ve ağ adresi değişip değişmediğini belirlemek sağlar. Bu sınıf kullanmak için değişiklik işlemek için bir olay işleyicisi oluşturun ve ilişkilendirin bir <xref:System.Net.NetworkInformation.NetworkAddressChangedEventHandler> veya <xref:System.Net.NetworkInformation.NetworkAvailabilityChangedEventHandler>. Daha fazla bilgi için [nasıl yapılır: Ağ kullanılabilirliğini algılama ve adres değişiklikleri](../../../docs/framework/network-programming/how-to-detect-network-availability-and-address-changes.md).  
  
## <a name="network-statistics-and-properties"></a>Ağ istatistikler ve Özellikler  
 Ağ istatistikler ve özellikler bir arabirim veya protokolü bazında toplayabilirsiniz. <xref:System.Net.NetworkInformation.NetworkInterface>, <xref:System.Net.NetworkInformation.NetworkInterfaceType>, Ve <xref:System.Net.NetworkInformation.PhysicalAddress> sınıfları, belirli bir ağ arabirimi hakkında bilgi verin sırada <xref:System.Net.NetworkInformation.IPInterfaceProperties>, <xref:System.Net.NetworkInformation.IPGlobalProperties>, <xref:System.Net.NetworkInformation.IPGlobalStatistics>, <xref:System.Net.NetworkInformation.TcpStatistics>, ve <xref:System.Net.NetworkInformation.UdpStatistics> sınıfları bilgi verin hakkında 3 katman ve katman 4 paketleri. Daha fazla bilgi için [nasıl yapılır: Arabirim ve protokol bilgilerini alma](../../../docs/framework/network-programming/how-to-get-interface-and-protocol-information.md).  
  
## <a name="determine-if-a-remote-host-is-reachable"></a>Uzak bir ana bilgisayarın erişilebilir olup olmadığını belirler  
 Kullanabileceğiniz <xref:System.Net.NetworkInformation.Ping> uzak bir ana bilgisayarın ayarlama, ağ ve erişilebilir olup olmadığını belirlemek için sınıf. Daha fazla bilgi için [nasıl yapılır: Konağa ping yapma](../../../docs/framework/network-programming/how-to-ping-a-host.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Ağ Programlama Örnekleri](../../../docs/framework/network-programming/network-programming-samples.md)
- [Ağ bilgi teknolojisi örneği](https://go.microsoft.com/fwlink/?LinkID=179564)
- [NetStat aracı teknolojisi örneği](https://go.microsoft.com/fwlink/?LinkID=179562)
- [Ping istemci teknolojisi örneği](https://go.microsoft.com/fwlink/?LinkID=179565)
