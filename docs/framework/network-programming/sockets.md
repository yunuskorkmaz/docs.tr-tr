---
title: Yuvalar
description: WinSock32 API 'SI tarafından sunulan yuva hizmetlerinin yönetilen kod sürümü olan .NET Framework yuva sınıfı hakkında bilgi edinin.
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
ms.openlocfilehash: e00d04164f7ce5251b7f30b5abd16c14643f6862
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96263132"
---
# <a name="sockets"></a><span data-ttu-id="f895f-103">Yuvalar</span><span class="sxs-lookup"><span data-stu-id="f895f-103">Sockets</span></span>

<span data-ttu-id="f895f-104"><xref:System.Net.Sockets>Ad alanı, Windows Sockets arabiriminin yönetilen bir uygulamasını içerir.</span><span class="sxs-lookup"><span data-stu-id="f895f-104">The <xref:System.Net.Sockets> namespace contains a managed implementation of the Windows Sockets interface.</span></span> <span data-ttu-id="f895f-105">Ad alanındaki diğer tüm ağ erişim sınıfları, <xref:System.Net> Bu yuvalar uygulamasının üzerine kurulmuştur.</span><span class="sxs-lookup"><span data-stu-id="f895f-105">All other network-access classes in the <xref:System.Net> namespace are built on top of this implementation of sockets.</span></span>  
  
 <span data-ttu-id="f895f-106">.NET Framework <xref:System.Net.Sockets.Socket> sınıfı, WinSock32 API 'si tarafından belirtilen yuva hizmetlerinin yönetilen kod sürümüdür.</span><span class="sxs-lookup"><span data-stu-id="f895f-106">The .NET Framework <xref:System.Net.Sockets.Socket> class is a managed-code version of the socket services provided by the Winsock32 API.</span></span> <span data-ttu-id="f895f-107">Çoğu durumda, **Socket** sınıfı yöntemleri yalnızca yerel Win32 karşılıklarına veri sıralamalarını ve gerekli güvenlik denetimlerini işlemelerini sağlamaktır.</span><span class="sxs-lookup"><span data-stu-id="f895f-107">In most cases, the **Socket** class methods simply marshal data into their native Win32 counterparts and handle any necessary security checks.</span></span>  
  
 <span data-ttu-id="f895f-108">**Yuva** sınıfı iki temel modu destekler, zaman uyumlu ve zaman uyumsuz.</span><span class="sxs-lookup"><span data-stu-id="f895f-108">The **Socket** class supports two basic modes, synchronous and asynchronous.</span></span> <span data-ttu-id="f895f-109">Zaman uyumlu modda, ağ işlemleri gerçekleştiren işlevlere yapılan çağrılar ( <xref:System.Net.Sockets.Socket.Send%2A> ve gibi), <xref:System.Net.Sockets.Socket.Receive%2A> çağıran programa denetim döndürmeden önce işlem tamamlanana kadar bekler.</span><span class="sxs-lookup"><span data-stu-id="f895f-109">In synchronous mode, calls to functions that perform network operations (such as <xref:System.Net.Sockets.Socket.Send%2A> and <xref:System.Net.Sockets.Socket.Receive%2A>) wait until the operation completes before returning control to the calling program.</span></span> <span data-ttu-id="f895f-110">Zaman uyumsuz modda bu çağrılar hemen döndürülür.</span><span class="sxs-lookup"><span data-stu-id="f895f-110">In asynchronous mode, these calls return immediately.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f895f-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f895f-111">See also</span></span>

- [<span data-ttu-id="f895f-112">Nasıl yapılır: Yuva Oluşturma</span><span class="sxs-lookup"><span data-stu-id="f895f-112">How to: Create a Socket</span></span>](how-to-create-a-socket.md)

- [<span data-ttu-id="f895f-113">Uygulama Protokolleri Kullanma</span><span class="sxs-lookup"><span data-stu-id="f895f-113">Using Application Protocols</span></span>](using-application-protocols.md)
