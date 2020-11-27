---
title: NetworkInformation
ms.date: 03/30/2017
helpviewer_keywords:
- Network
ms.assetid: 31b44dd3-b903-4a48-8419-40419a3e4038
ms.openlocfilehash: 550555be7cc95cafebabfd3ac230ced024a9202c
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96261624"
---
# <a name="networkinformation"></a>NetworkInformation

<xref:System.Net.NetworkInformation>Ad alanı, ağ olayları, değişiklikler, istatistikler ve özellikler hakkında bilgi toplamanıza olanak sağlar. Ayrıca, sınıfını kullanarak bir uzak ana bilgisayarın erişilebilir olup olmadığını da belirleyebilirsiniz <xref:System.Net.NetworkInformation.Ping?displayProperty=nameWithType> .  
  
## <a name="network-availability-and-events"></a>Ağ kullanılabilirliği ve olayları  

 <xref:System.Net.NetworkInformation.NetworkChange?displayProperty=nameWithType>Sınıfı, ağ adresinin veya kullanılabilirliğinin değiştirilip değiştirilmediğini belirlemenizi sağlar. Bu sınıfı kullanmak için değişikliği işlemek üzere bir olay işleyicisi oluşturun ve bir veya ile ilişkilendirin <xref:System.Net.NetworkInformation.NetworkAddressChangedEventHandler> <xref:System.Net.NetworkInformation.NetworkAvailabilityChangedEventHandler> . Daha fazla bilgi için bkz. [nasıl yapılır: algılama ağ kullanılabilirliği ve adres değişiklikleri](how-to-detect-network-availability-and-address-changes.md).  
  
## <a name="network-statistics-and-properties"></a>Ağ Istatistikleri ve özellikleri  

 Ağ istatistiklerini ve özelliklerini bir arabirim ya da protokol temelinde toplayabilirsiniz. , <xref:System.Net.NetworkInformation.NetworkInterface> , <xref:System.Net.NetworkInformation.NetworkInterfaceType> Ve <xref:System.Net.NetworkInformation.PhysicalAddress> sınıfları belirli bir ağ arabirimi hakkında bilgi verir,,,, <xref:System.Net.NetworkInformation.IPInterfaceProperties> <xref:System.Net.NetworkInformation.IPGlobalProperties> <xref:System.Net.NetworkInformation.IPGlobalStatistics> <xref:System.Net.NetworkInformation.TcpStatistics> ve <xref:System.Net.NetworkInformation.UdpStatistics> sınıfları katman 3 ve katman 4 paketleri hakkında bilgi verir. Daha fazla bilgi için bkz. [nasıl yapılır: arabirim ve protokol alma bilgileri](how-to-get-interface-and-protocol-information.md).  
  
## <a name="determine-if-a-remote-host-is-reachable"></a>Uzak bir konağın erişilebilir olup olmadığını belirleme  

 <xref:System.Net.NetworkInformation.Ping>Bir uzak konağın çalışır durumda olup olmadığını, ağda ve erişilebilir olduğunu anlamak için sınıfını kullanabilirsiniz. Daha fazla bilgi için bkz. [nasıl yapılır: ping a Host](how-to-ping-a-host.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Ağ Programlama Örnekleri](network-programming-samples.md)

<!-- to-do: review sample links
- [Network Information Technology Sample](https://archive.msdn.microsoft.com/nclsamples/Wiki/View.aspx?title=Network%20Information)
- [NetStat Tool Technology Sample](https://archive.msdn.microsoft.com/nclsamples/Wiki/View.aspx?title=NetStat%20Tool)
- [Ping Client Technology Sample](https://archive.msdn.microsoft.com/nclsamples/Wiki/View.aspx?title=Ping%20Client)
-->
