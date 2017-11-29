---
title: Yuva
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "8"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: de5778e398a9a7205e99cc810d0b672ac247da08
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="sockets"></a><span data-ttu-id="210fa-102">Yuva</span><span class="sxs-lookup"><span data-stu-id="210fa-102">Sockets</span></span>
<span data-ttu-id="210fa-103"><xref:System.Net.Sockets> Ad alanı, yönetilen bir uygulama Windows Sockets arabirimi içerir.</span><span class="sxs-lookup"><span data-stu-id="210fa-103">The <xref:System.Net.Sockets> namespace contains a managed implementation of the Windows Sockets interface.</span></span> <span data-ttu-id="210fa-104">Tüm diğer ağ erişim sınıfları <xref:System.Net> ad alanı, bu yuva uygulama üstünde yerleşiktir.</span><span class="sxs-lookup"><span data-stu-id="210fa-104">All other network-access classes in the <xref:System.Net> namespace are built on top of this implementation of sockets.</span></span>  
  
 <span data-ttu-id="210fa-105">.NET Framework <xref:System.Net.Sockets.Socket> Winsock32 API'si tarafından sağlanan yuva services yönetilen kod sürümü bir sınıftır.</span><span class="sxs-lookup"><span data-stu-id="210fa-105">The .NET Framework <xref:System.Net.Sockets.Socket> class is a managed-code version of the socket services provided by the Winsock32 API.</span></span> <span data-ttu-id="210fa-106">Çoğu durumda, **yuva** yöntemleri yalnızca sınıf yerel Win32 dekiler verileri sıralama ve tüm gerekli güvenlik denetimlerini tanıtıcı.</span><span class="sxs-lookup"><span data-stu-id="210fa-106">In most cases, the **Socket** class methods simply marshal data into their native Win32 counterparts and handle any necessary security checks.</span></span>  
  
 <span data-ttu-id="210fa-107">**Yuva** sınıfı, zaman uyumlu ve zaman uyumsuz olmak üzere iki temel modunu destekler.</span><span class="sxs-lookup"><span data-stu-id="210fa-107">The **Socket** class supports two basic modes, synchronous and asynchronous.</span></span> <span data-ttu-id="210fa-108">Ağ işlemlerini gerçekleştirme işlevleri için zaman uyumlu modda çağıran (gibi <xref:System.Net.Sockets.Socket.Send%2A> ve <xref:System.Net.Sockets.Socket.Receive%2A>) denetimi çağıran program döndürmeden önce işlemi tamamlanana dek bekleyin.</span><span class="sxs-lookup"><span data-stu-id="210fa-108">In synchronous mode, calls to functions that perform network operations (such as <xref:System.Net.Sockets.Socket.Send%2A> and <xref:System.Net.Sockets.Socket.Receive%2A>) wait until the operation completes before returning control to the calling program.</span></span> <span data-ttu-id="210fa-109">Zaman uyumsuz modda çağrıları, hemen döndürülür.</span><span class="sxs-lookup"><span data-stu-id="210fa-109">In asynchronous mode, these calls return immediately.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="210fa-110">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="210fa-110">See Also</span></span>  
 [<span data-ttu-id="210fa-111">Nasıl yapılır: bir yuva oluşturun</span><span class="sxs-lookup"><span data-stu-id="210fa-111">How to: Create a Socket</span></span>](../../../docs/framework/network-programming/how-to-create-a-socket.md)  
    
 [<span data-ttu-id="210fa-112">Uygulama protokolleri kullanma</span><span class="sxs-lookup"><span data-stu-id="210fa-112">Using Application Protocols</span></span>](../../../docs/framework/network-programming/using-application-protocols.md)
