---
title: Web ve Yuva İzinleri
ms.date: 03/30/2017
helpviewer_keywords:
- Networking
- positions [.NET Framework], accepting
- sockets, permissions
- network, permissions
- Internet, permissions
- Network Resources
- SocketPermission class, about SocketPermission class
- positions [.NET Framework], connecting
- WebPermission class, about WebPermission class
- permissions [.NET Framework], sockets
- security [.NET Framework], Internet
- positions [.NET Framework], granting
ms.assetid: d51ad8cb-03ae-4a51-bfcd-cfcf6b98afa9
ms.openlocfilehash: fbb4e5d7171c50c06f55706df90240ffa205ee73
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69967616"
---
# <a name="web-and-socket-permissions"></a>Web ve Yuva İzinleri
<xref:System.Net> Ad alanını kullanan uygulamalar için Internet güvenliği, <xref:System.Net.WebPermission> ve <xref:System.Net.SocketPermission> sınıfları tarafından sağlanır. **WebPermission** sınıfı bir URI 'den veri istemek veya bir URI 'yi Internet 'e sağlamak için bir uygulamanın hakkını denetler. **SocketPermission** sınıfı, bir uygulamanın, bir <xref:System.Net.Sockets.Socket> yerel bağlantı noktasındaki verileri kabul etmek veya başka bir adreste bir aktarım protokolü kullanarak uzak cihazlara iletişim kurmak için, ' ın ana bilgisayar, bağlantı noktası numarası ve aktarım protokolüne bağlı olarak kullanılması hakkını denetler yuvasının.  
  
 Kullandığınız izin sınıfı, uygulama türüne bağlıdır. Ve alt öğeleri kullanan uygulamaların, izinleri yönetmek için **WebPermission** sınıfını kullanması gerekir. <xref:System.Net.WebRequest> Yuva düzeyi erişim kullanan uygulamaların, izinleri yönetmek için **SocketPermission** sınıfını kullanması gerekir.  
  
 **WebPermission** ve **SocketPermission** iki izin tanımlar: Accept ve Connect. Accept, uygulamayı başka bir taraftan gelen bir bağlantıyı yanıtlamak için hak verir. Connect, uygulamaya başka bir tarafa bağlantı başlatma hakkı verir.  
  
 **SocketPermission** örnekleri için kabul et, bir uygulamanın yerel bir aktarım adresinde gelen bağlantıları kabul edebileceği anlamına gelir; Connect, bir uygulamanın bir uzak (veya yerel) aktarım adresine bağlanabileceği anlamına gelir.  
  
 **WebPermission** örnekleri için kabul et, bir uygulamanın **WebPermission** tarafından denetlenen URI 'yi dünyaya dışa verebileceği anlamına gelir; bağlantı, bir uygulamanın bu URI 'ye erişebileceği anlamına gelir (uzak veya yerel olsun).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Güvenlik](../../standard/security/index.md)
- [Ağ Programlama Güvenliği](../../../docs/framework/network-programming/security-in-network-programming.md)
