---
title: Yuvalar
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
ms.openlocfilehash: cffad6b4677a880bd63f5ae0232c639f7a262c59
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "71047253"
---
# <a name="sockets"></a><span data-ttu-id="f5c01-102">Yuvalar</span><span class="sxs-lookup"><span data-stu-id="f5c01-102">Sockets</span></span>
<span data-ttu-id="f5c01-103">Ad <xref:System.Net.Sockets> alanı, Windows Soketleri arabiriminin yönetilen bir uygulamasını içerir.</span><span class="sxs-lookup"><span data-stu-id="f5c01-103">The <xref:System.Net.Sockets> namespace contains a managed implementation of the Windows Sockets interface.</span></span> <span data-ttu-id="f5c01-104"><xref:System.Net> Ad alanındaki diğer tüm ağ erişim sınıfları, soketlerin bu uygulamasının üzerine inşa edilmiştir.</span><span class="sxs-lookup"><span data-stu-id="f5c01-104">All other network-access classes in the <xref:System.Net> namespace are built on top of this implementation of sockets.</span></span>  
  
 <span data-ttu-id="f5c01-105">.NET Framework <xref:System.Net.Sockets.Socket> sınıfı, Winsock32 API tarafından sağlanan soket hizmetlerinin yönetilen kodlu bir sürümüdür.</span><span class="sxs-lookup"><span data-stu-id="f5c01-105">The .NET Framework <xref:System.Net.Sockets.Socket> class is a managed-code version of the socket services provided by the Winsock32 API.</span></span> <span data-ttu-id="f5c01-106">Çoğu durumda, **Socket** sınıfı yöntemleri verileri yalnızca yerel Win32 muadillerine göre yönetir ve gerekli güvenlik denetimlerini işler.</span><span class="sxs-lookup"><span data-stu-id="f5c01-106">In most cases, the **Socket** class methods simply marshal data into their native Win32 counterparts and handle any necessary security checks.</span></span>  
  
 <span data-ttu-id="f5c01-107">**Soket** sınıfı senkron ve eşzamanlı olmak üzere iki temel modu destekler.</span><span class="sxs-lookup"><span data-stu-id="f5c01-107">The **Socket** class supports two basic modes, synchronous and asynchronous.</span></span> <span data-ttu-id="f5c01-108">Senkron modda, ağ işlemleri gerçekleştiren işlevlere <xref:System.Net.Sockets.Socket.Send%2A> (örneğin ve) <xref:System.Net.Sockets.Socket.Receive%2A>arama programına denetimi döndürmeden önce işlem tamamlanana kadar bekler.</span><span class="sxs-lookup"><span data-stu-id="f5c01-108">In synchronous mode, calls to functions that perform network operations (such as <xref:System.Net.Sockets.Socket.Send%2A> and <xref:System.Net.Sockets.Socket.Receive%2A>) wait until the operation completes before returning control to the calling program.</span></span> <span data-ttu-id="f5c01-109">Eşzamanlı modda, bu çağrılar hemen geri döner.</span><span class="sxs-lookup"><span data-stu-id="f5c01-109">In asynchronous mode, these calls return immediately.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f5c01-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f5c01-110">See also</span></span>

- [<span data-ttu-id="f5c01-111">Nasıl Yapılır: Yuva Oluşturma</span><span class="sxs-lookup"><span data-stu-id="f5c01-111">How to: Create a Socket</span></span>](how-to-create-a-socket.md)

- [<span data-ttu-id="f5c01-112">Uygulama Protokolleri Kullanma</span><span class="sxs-lookup"><span data-stu-id="f5c01-112">Using Application Protocols</span></span>](using-application-protocols.md)
