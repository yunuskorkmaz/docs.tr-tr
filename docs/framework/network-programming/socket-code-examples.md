---
title: "Yuva kod örnekleri"
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
- Socket class, asynchronous server sockets
- data requests, sockets
- requesting data from Internet, sockets
- server sockets
- sockets, code examples
- receiving data, sockets
- protocols, sockets
- Internet, sockets
- client sockets
ms.assetid: f3fc7533-6956-42c6-bbc3-73e5a221027d
caps.latest.revision: "9"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: ac2363ce7c2affcc0b56f7ce8b9d41180b4c3a1f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="socket-code-examples"></a><span data-ttu-id="1f2b5-102">Yuva kod örnekleri</span><span class="sxs-lookup"><span data-stu-id="1f2b5-102">Socket Code Examples</span></span>
<span data-ttu-id="1f2b5-103">Aşağıdaki kod örnekleri nasıl kullanılacağını gösteren <xref:System.Net.Sockets.Socket> sınıfı uzak ağ hizmetlerine bağlanmak için bir istemci ve uzak istemci bağlantılarını dinlemek için bir sunucu olarak.</span><span class="sxs-lookup"><span data-stu-id="1f2b5-103">The following code examples demonstrate how to use the <xref:System.Net.Sockets.Socket> class as a client to connect to remote network services and as a server to listen for connections from remote clients.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="1f2b5-104">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="1f2b5-104">In This Section</span></span>  
 [<span data-ttu-id="1f2b5-105">Zaman uyumlu istemci yuva örneği</span><span class="sxs-lookup"><span data-stu-id="1f2b5-105">Synchronous Client Socket Example</span></span>](../../../docs/framework/network-programming/synchronous-client-socket-example.md)  
 <span data-ttu-id="1f2b5-106">Bir zaman uyumlu uygulamak gösterilmiştir <xref:System.Net.Sockets.Socket> bir sunucuya bağlanan ve verileri görüntüler istemci sunucudan döndürdü.</span><span class="sxs-lookup"><span data-stu-id="1f2b5-106">Shows how to implement a synchronous <xref:System.Net.Sockets.Socket> client that connects to a server and displays the data returned from the server.</span></span>  
  
 [<span data-ttu-id="1f2b5-107">Zaman uyumlu Server yuva örneği</span><span class="sxs-lookup"><span data-stu-id="1f2b5-107">Synchronous Server Socket Example</span></span>](../../../docs/framework/network-programming/synchronous-server-socket-example.md)  
 <span data-ttu-id="1f2b5-108">Bir zaman uyumlu uygulamak gösterilmektedir <xref:System.Net.Sockets.Socket> bir istemciden gelen bağlantıları kabul eder ve geri istemciden alınan verileri görüntülemektedir.</span><span class="sxs-lookup"><span data-stu-id="1f2b5-108">Shows how to implement a synchronous <xref:System.Net.Sockets.Socket> server that accepts connections from a client and echoes back the data received from the client.</span></span>  
  
 [<span data-ttu-id="1f2b5-109">Zaman uyumsuz istemcisi yuva örneği</span><span class="sxs-lookup"><span data-stu-id="1f2b5-109">Asynchronous Client Socket Example</span></span>](../../../docs/framework/network-programming/asynchronous-client-socket-example.md)  
 <span data-ttu-id="1f2b5-110">Zaman uyumsuz bir uygulama gösterilmektedir <xref:System.Net.Sockets.Socket> bir sunucuya bağlanan ve verileri görüntüler istemci sunucudan döndürdü.</span><span class="sxs-lookup"><span data-stu-id="1f2b5-110">Shows how to implement an asynchronous <xref:System.Net.Sockets.Socket> client that connects to a server and displays the data returned from the server.</span></span>  
  
 [<span data-ttu-id="1f2b5-111">Zaman uyumsuz Server yuva örneği</span><span class="sxs-lookup"><span data-stu-id="1f2b5-111">Asynchronous Server Socket Example</span></span>](../../../docs/framework/network-programming/asynchronous-server-socket-example.md)  
 <span data-ttu-id="1f2b5-112">Zaman uyumsuz bir uygulama gösterilmektedir <xref:System.Net.Sockets.Socket> bir istemciden gelen bağlantıları kabul eder ve geri istemciden alınan verileri görüntülemektedir.</span><span class="sxs-lookup"><span data-stu-id="1f2b5-112">Shows how to implement an asynchronous <xref:System.Net.Sockets.Socket> server that accepts connections from a client and echoes back the data received from the client.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="1f2b5-113">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="1f2b5-113">Related Sections</span></span>  
 [<span data-ttu-id="1f2b5-114">Yuva</span><span class="sxs-lookup"><span data-stu-id="1f2b5-114">Sockets</span></span>](../../../docs/framework/network-programming/sockets.md)  
 <span data-ttu-id="1f2b5-115">Hakkında temel bilgileri sağlayan <xref:System.Net.Sockets> ad alanı ve <xref:System.Net.Sockets.Socket> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="1f2b5-115">Provides basic information about the <xref:System.Net.Sockets> namespace and the <xref:System.Net.Sockets.Socket> class.</span></span>  
  
 [<span data-ttu-id="1f2b5-116">Güvenlik ağ programlama</span><span class="sxs-lookup"><span data-stu-id="1f2b5-116">Security in Network Programming</span></span>](../../../docs/framework/network-programming/security-in-network-programming.md)  
 <span data-ttu-id="1f2b5-117">Standart Internet güvenliği ve kimlik doğrulama tekniklerinin nasıl kullanılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="1f2b5-117">Describes how to use standard Internet security and authentication techniques.</span></span>
