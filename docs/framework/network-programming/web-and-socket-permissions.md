---
title: Web ve Yuva İzinleri
description: WebPermission ve SocketPermission sınıflarının, .NET Framework System.Net ad alanını kullanmak için internet güvenliği nasıl sağladığını öğrenin.
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
ms.openlocfilehash: 08ae360e8097f7281631da2a3f9846994dfbf5b6
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501904"
---
# <a name="web-and-socket-permissions"></a>Web ve Yuva İzinleri
Ad alanını kullanan uygulamalar için Internet güvenliği <xref:System.Net> , <xref:System.Net.WebPermission> ve sınıfları tarafından sağlanır <xref:System.Net.SocketPermission> . **WebPermission** sınıfı bir URI 'den veri istemek veya bir URI 'yi Internet 'e sağlamak için bir uygulamanın hakkını denetler. **SocketPermission** sınıfı, bir uygulamanın <xref:System.Net.Sockets.Socket> , bir yerel bağlantı noktasındaki verileri kabul etmek veya başka bir adreste bir aktarım protokolü kullanarak uzak cihazlara bağlantı kurmak için, yuvanın ana bilgisayar, bağlantı noktası numarası ve aktarım protokolüne bağlı olarak kullanılması hakkını denetler.  
  
 Kullandığınız izin sınıfı, uygulama türüne bağlıdır. <xref:System.Net.WebRequest>Ve alt öğeleri kullanan uygulamaların, izinleri yönetmek Için **WebPermission** sınıfını kullanması gerekir. Yuva düzeyi erişim kullanan uygulamaların, izinleri yönetmek için **SocketPermission** sınıfını kullanması gerekir.  
  
 **WebPermission** ve **SocketPermission** iki izin tanımlar: Accept ve Connect. Accept, uygulamayı başka bir taraftan gelen bir bağlantıyı yanıtlamak için hak verir. Connect, uygulamaya başka bir tarafa bağlantı başlatma hakkı verir.  
  
 **SocketPermission** örnekleri için kabul et, bir uygulamanın yerel bir aktarım adresinde gelen bağlantıları kabul edebileceği anlamına gelir; Connect, bir uygulamanın bir uzak (veya yerel) aktarım adresine bağlanabileceği anlamına gelir.  
  
 **WebPermission** örnekleri için kabul et, bir uygulamanın **WebPermission** tarafından denetlenen URI 'yi dünyaya dışa verebileceği anlamına gelir; bağlantı, bir uygulamanın bu URI 'ye erişebileceği anlamına gelir (uzak veya yerel olsun).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Güvenlik](../../standard/security/index.md)
- [Ağ Programlama Güvenliği](security-in-network-programming.md)
