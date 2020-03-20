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
ms.openlocfilehash: d1b993acbf20eac244e596075c3f826bba3211a1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "71046861"
---
# <a name="web-and-socket-permissions"></a>Web ve Yuva İzinleri
<xref:System.Net> Ad alanını kullanan uygulamalar için Internet güvenliği <xref:System.Net.WebPermission> <xref:System.Net.SocketPermission> ve sınıflar tarafından sağlanır. **WebPermission** sınıfı, bir uygulamanın URI'den veri isteme veya Bir URI'yi Internet'e sunma hakkını denetler. **SocketPermission** sınıfı, bir uygulamanın yerel <xref:System.Net.Sockets.Socket> bir bağlantı noktasında veri kabul etmek veya yuvanın ana bilgisayar, bağlantı noktası numarası ve taşıma protokolüne dayalı olarak başka bir adreste taşıma protokolü kullanarak uzak aygıtlarla iletişim kurmak için bir uygulamanın kullanma hakkını denetler.  
  
 Hangi izin sınıfını kullandığınız uygulama türüne bağlıdır. Kullanan <xref:System.Net.WebRequest> uygulamalar ve onun soyundan gelenler izinleri yönetmek için **WebPermission** sınıfını kullanmalıdır. Soket düzeyinde erişim kullanan uygulamalar, izinleri yönetmek için **SocketPermission** sınıfını kullanmalıdır.  
  
 **WebPermission** ve **SocketPermission** iki izin tanımlar: kabul edin ve bağlanın. Kabul kabul edin, başvuruya başka bir taraftan gelen bir bağlantıyı yanıtlama hakkı verir. Connect, uygulamaya başka bir tarafa bağlantı kurma hakkı verir.  
  
 **SocketPermission** örnekleri için, bir uygulamanın yerel bir aktarım adresinde gelen bağlantıları kabul edebileceği anlamına gelir; bağlantı, bir uygulamanın bazı uzak (veya yerel) aktarım adresine bağlanabileceği anlamına gelir.  
  
 **WebPermission** örnekleri için, bir uygulamanın **WebPermission** tarafından kontrol edilen URI'yi dünyaya dışa aktarabileceği anlamına gelir; bağlanmak, bir uygulamanın o URI'ye (uzak veya yerel olsun) erişebileceği anlamına gelir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Güvenlik](../../standard/security/index.md)
- [Ağ Programlama Güvenliği](security-in-network-programming.md)
