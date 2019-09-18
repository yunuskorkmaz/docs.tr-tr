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
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71047253"
---
# <a name="sockets"></a><span data-ttu-id="1a1a0-102">Yuvalar</span><span class="sxs-lookup"><span data-stu-id="1a1a0-102">Sockets</span></span>
<span data-ttu-id="1a1a0-103">Ad <xref:System.Net.Sockets> alanı, Windows Sockets arabiriminin yönetilen bir uygulamasını içerir.</span><span class="sxs-lookup"><span data-stu-id="1a1a0-103">The <xref:System.Net.Sockets> namespace contains a managed implementation of the Windows Sockets interface.</span></span> <span data-ttu-id="1a1a0-104">Ad alanındaki diğer tüm ağ erişim sınıfları, <xref:System.Net> bu yuvalar uygulamasının üzerine kurulmuştur.</span><span class="sxs-lookup"><span data-stu-id="1a1a0-104">All other network-access classes in the <xref:System.Net> namespace are built on top of this implementation of sockets.</span></span>  
  
 <span data-ttu-id="1a1a0-105">.NET Framework <xref:System.Net.Sockets.Socket> sınıfı, WinSock32 API 'si tarafından belirtilen yuva hizmetlerinin yönetilen kod sürümüdür.</span><span class="sxs-lookup"><span data-stu-id="1a1a0-105">The .NET Framework <xref:System.Net.Sockets.Socket> class is a managed-code version of the socket services provided by the Winsock32 API.</span></span> <span data-ttu-id="1a1a0-106">Çoğu durumda, **Socket** sınıfı yöntemleri yalnızca yerel Win32 karşılıklarına veri sıralamalarını ve gerekli güvenlik denetimlerini işlemelerini sağlamaktır.</span><span class="sxs-lookup"><span data-stu-id="1a1a0-106">In most cases, the **Socket** class methods simply marshal data into their native Win32 counterparts and handle any necessary security checks.</span></span>  
  
 <span data-ttu-id="1a1a0-107">**Yuva** sınıfı iki temel modu destekler, zaman uyumlu ve zaman uyumsuz.</span><span class="sxs-lookup"><span data-stu-id="1a1a0-107">The **Socket** class supports two basic modes, synchronous and asynchronous.</span></span> <span data-ttu-id="1a1a0-108">Zaman uyumlu modda, ağ işlemleri gerçekleştiren işlevlere yapılan çağrılar ( <xref:System.Net.Sockets.Socket.Send%2A> ve <xref:System.Net.Sockets.Socket.Receive%2A>gibi), çağıran programa denetim döndürmeden önce işlem tamamlanana kadar bekler.</span><span class="sxs-lookup"><span data-stu-id="1a1a0-108">In synchronous mode, calls to functions that perform network operations (such as <xref:System.Net.Sockets.Socket.Send%2A> and <xref:System.Net.Sockets.Socket.Receive%2A>) wait until the operation completes before returning control to the calling program.</span></span> <span data-ttu-id="1a1a0-109">Zaman uyumsuz modda bu çağrılar hemen döndürülür.</span><span class="sxs-lookup"><span data-stu-id="1a1a0-109">In asynchronous mode, these calls return immediately.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1a1a0-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1a1a0-110">See also</span></span>

- [<span data-ttu-id="1a1a0-111">Nasıl yapılır: Yuva oluşturma</span><span class="sxs-lookup"><span data-stu-id="1a1a0-111">How to: Create a Socket</span></span>](how-to-create-a-socket.md)

- [<span data-ttu-id="1a1a0-112">Uygulama Protokolleri Kullanma</span><span class="sxs-lookup"><span data-stu-id="1a1a0-112">Using Application Protocols</span></span>](using-application-protocols.md)
