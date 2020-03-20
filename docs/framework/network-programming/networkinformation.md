---
title: NetworkInformation
ms.date: 03/30/2017
helpviewer_keywords:
- Network
ms.assetid: 31b44dd3-b903-4a48-8419-40419a3e4038
ms.openlocfilehash: bc0604fd33d06521727c9aa0302ed313d8a2305f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "74428239"
---
# <a name="networkinformation"></a>NetworkInformation
Ad <xref:System.Net.NetworkInformation> alanı, ağ olayları, değişiklikler, istatistikler ve özellikler hakkında bilgi toplamanızı sağlar. Sınıfı kullanarak <xref:System.Net.NetworkInformation.Ping?displayProperty=nameWithType> uzak bir ana bilgisayara erişilip erişilemeyeceğini de belirleyebilirsiniz.  
  
## <a name="network-availability-and-events"></a>Ağ Kullanılabilirliği ve Etkinlikler  
 Sınıf, <xref:System.Net.NetworkInformation.NetworkChange?displayProperty=nameWithType> ağ adresinin veya kullanılabilirlik durumunun değişip değişmediğini belirlemenize olanak tanır. Bu sınıfı kullanmak için, değişikliği işlemek için bir olay işleyicisi oluşturun ve bir veya bir <xref:System.Net.NetworkInformation.NetworkAddressChangedEventHandler> <xref:System.Net.NetworkInformation.NetworkAvailabilityChangedEventHandler>. ile ilişkilendirin Daha fazla bilgi için [bkz: Ağ Kullanılabilirliğini ve Adres Değişikliklerini Algıla.](how-to-detect-network-availability-and-address-changes.md)  
  
## <a name="network-statistics-and-properties"></a>Ağ İstatistikleri ve Özellikleri  
 Ağ istatistiklerini ve özelliklerini arabirim veya protokol temelinde toplayabilirsiniz. <xref:System.Net.NetworkInformation.NetworkInterfaceType>, <xref:System.Net.NetworkInformation.NetworkInterface>ve <xref:System.Net.NetworkInformation.PhysicalAddress> sınıflar belirli bir ağ arabirimi <xref:System.Net.NetworkInformation.IPInterfaceProperties>hakkında <xref:System.Net.NetworkInformation.IPGlobalProperties> <xref:System.Net.NetworkInformation.IPGlobalStatistics>bilgi <xref:System.Net.NetworkInformation.TcpStatistics>verirken, , , , ve <xref:System.Net.NetworkInformation.UdpStatistics> sınıflar katman 3 ve katman 4 paketleri hakkında bilgi verir. Daha fazla bilgi [için bkz: Arabirim ve Protokol Bilgilerini Alın.](how-to-get-interface-and-protocol-information.md)  
  
## <a name="determine-if-a-remote-host-is-reachable"></a>Uzak Ana Bilgisayara Erişilip Erişilemeyin  
 Uzaktan Ana <xref:System.Net.NetworkInformation.Ping> Bilgisayar'ın ağda, ağda ve ulaşılabilir olup olmadığını belirlemek için sınıfı kullanabilirsiniz. Daha fazla bilgi için [bkz: Ana Bilgisayar](how-to-ping-a-host.md)Pingi .  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Ağ Programlama Örnekleri](network-programming-samples.md)

<!-- to-do: review sample links
- [Network Information Technology Sample](https://archive.msdn.microsoft.com/nclsamples/Wiki/View.aspx?title=Network%20Information)
- [NetStat Tool Technology Sample](https://archive.msdn.microsoft.com/nclsamples/Wiki/View.aspx?title=NetStat%20Tool)
- [Ping Client Technology Sample](https://archive.msdn.microsoft.com/nclsamples/Wiki/View.aspx?title=Ping%20Client)
-->
