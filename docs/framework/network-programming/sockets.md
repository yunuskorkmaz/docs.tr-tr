---
title: Yuva
ms.date: 03/30/2017
helpviewer_keywords:
- application protocols, sockets
- sending data, sockets
- data requests, sockets
- Windows Sockets
- sockets, about sockets
- Socket class, about Socket class
- sockets
- requesting data from Internet, sockets
- network, sockets
- receiving data, sockets
- protocols, sockets
- Internet, sockets
ms.assetid: 10d22735-bd37-42c1-a2be-c1932f979a7d
author: mcleblanc
ms.author: markl
ms.openlocfilehash: ce7ded81ad23c2df55afa9360435e8391fea7a63
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/25/2018
ms.locfileid: "47176831"
---
# <a name="sockets"></a><span data-ttu-id="1b377-102">Yuva</span><span class="sxs-lookup"><span data-stu-id="1b377-102">Sockets</span></span>
<span data-ttu-id="1b377-103"><xref:System.Net.Sockets> Ad alanı, Windows yuva arabiriminin yönetilen bir uygulamasını içerir.</span><span class="sxs-lookup"><span data-stu-id="1b377-103">The <xref:System.Net.Sockets> namespace contains a managed implementation of the Windows Sockets interface.</span></span> <span data-ttu-id="1b377-104">Yer alan tüm diğer ağ erişim sınıfları <xref:System.Net> ad alanı, bu yuva uygulaması üzerinde oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="1b377-104">All other network-access classes in the <xref:System.Net> namespace are built on top of this implementation of sockets.</span></span>  
  
 <span data-ttu-id="1b377-105">.NET Framework <xref:System.Net.Sockets.Socket> sınıftır Winsock32 API'sı tarafından sağlanan yuva services yönetilen kod sürümü.</span><span class="sxs-lookup"><span data-stu-id="1b377-105">The .NET Framework <xref:System.Net.Sockets.Socket> class is a managed-code version of the socket services provided by the Winsock32 API.</span></span> <span data-ttu-id="1b377-106">Çoğu durumda **yuva** yöntemleri yalnızca sınıf yerel Win32 karşılıkları veri hazırlamak ve tüm gerekli güvenlik denetimlerini işleyecek.</span><span class="sxs-lookup"><span data-stu-id="1b377-106">In most cases, the **Socket** class methods simply marshal data into their native Win32 counterparts and handle any necessary security checks.</span></span>  
  
 <span data-ttu-id="1b377-107">**Yuva** sınıfı, zaman uyumlu ve zaman uyumsuz olmak üzere iki temel modlarını destekler.</span><span class="sxs-lookup"><span data-stu-id="1b377-107">The **Socket** class supports two basic modes, synchronous and asynchronous.</span></span> <span data-ttu-id="1b377-108">Zaman uyumlu modda ağ işlemleri gerçekleştirmek için işlevleri çağırır (gibi <xref:System.Net.Sockets.Socket.Send%2A> ve <xref:System.Net.Sockets.Socket.Receive%2A>) denetimi çağırma program döndürmeden önce işlemi tamamlanana kadar bekleyin.</span><span class="sxs-lookup"><span data-stu-id="1b377-108">In synchronous mode, calls to functions that perform network operations (such as <xref:System.Net.Sockets.Socket.Send%2A> and <xref:System.Net.Sockets.Socket.Receive%2A>) wait until the operation completes before returning control to the calling program.</span></span> <span data-ttu-id="1b377-109">Zaman uyumsuz modda bu çağrılar hemen döndürür.</span><span class="sxs-lookup"><span data-stu-id="1b377-109">In asynchronous mode, these calls return immediately.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1b377-110">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="1b377-110">See Also</span></span>  
 [<span data-ttu-id="1b377-111">Nasıl Yapılır: Yuva Oluşturma</span><span class="sxs-lookup"><span data-stu-id="1b377-111">How to: Create a Socket</span></span>](../../../docs/framework/network-programming/how-to-create-a-socket.md)  
    
 [<span data-ttu-id="1b377-112">Uygulama Protokolleri Kullanma</span><span class="sxs-lookup"><span data-stu-id="1b377-112">Using Application Protocols</span></span>](../../../docs/framework/network-programming/using-application-protocols.md)
