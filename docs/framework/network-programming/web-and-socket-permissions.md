---
title: Web ve yuva izinleri
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "9"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: b426b5e7e6a9b617311db05670f526fc415d591d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="web-and-socket-permissions"></a>Web ve yuva izinleri
Internet güvenliği kullanan uygulamalar için <xref:System.Net> ad alanı tarafından sağlanan <xref:System.Net.WebPermission> ve <xref:System.Net.SocketPermission> sınıfları. **WebPermission** sınıfı, bir uygulamanın sağ istek verileri için bir URI veya Internet'e bir URI sunmak için denetler. **SocketPermission** sınıfı bir uygulamayı kullanmak doğru denetimleri bir <xref:System.Net.Sockets.Socket> yerel bağlantı noktası verileri kabul etmek veya başka bir adresinde konak, bağlantı noktası numarası, temel bir aktarım protokolünü kullanarak uzak aygıtlar iletişim kurmak için ve Soket Aktarım Protokolü.  
  
 Kullandığınız hangi izni sınıfı, uygulama türüne bağlıdır. Kullanan uygulamalar <xref:System.Net.WebRequest> ve alt öğeleri kullanması gereken **WebPermission** izinleri yönetmek için sınıf. Yuva düzeyinde erişim kullanan uygulamaları kullanması gereken **SocketPermission** izinleri yönetmek için sınıf.  
  
 **WebPermission** ve **SocketPermission** iki izinlerini tanımlamak: kabul etmek ve bağlanın. Kabul uygulama başka bir tarafa gelen bir bağlantıdan yanıt hakkı verir. Bağlantı uygulama başka bir tarafa bir bağlantı başlatmak hakkı verir.  
  
 İçin **SocketPermission** örnekleri, bir uygulamanın yerel gelen bağlantıları kabul edebilir anlamına gelir kabul aktarım adres; Bağlan uygulamanın bazı Uzak (veya yerel) aktarım adresine bağlanabilir anlamına gelir.  
  
 İçin **WebPermission** örnekleri, bir uygulama tarafından denetlenen URI verebilirsiniz anlamına gelir kabul **WebPermission** dünyasına; bir uygulama (olup bu URI erişebileceği anlamına gelir Bağlan Uzak veya yerel).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Güvenlik](../../../docs/standard/security/index.md)  
 [Ağ Programlama Güvenliği](../../../docs/framework/network-programming/security-in-network-programming.md)
