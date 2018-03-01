---
title: HttpListener
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- HTTP
ms.assetid: 5b89d3fb-3c9a-49e2-af1f-c34c020c68ac
caps.latest.revision: 
author: mcleblanc
ms.author: markl
manager: markl
ms.workload:
- dotnet
ms.openlocfilehash: b4b8c1e916aa9382d156a197fa15c2e72e900a1c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="httplistener"></a><span data-ttu-id="e2bb3-102">HttpListener</span><span class="sxs-lookup"><span data-stu-id="e2bb3-102">HttpListener</span></span>
<span data-ttu-id="e2bb3-103"><xref:System.Net.HttpListener> Sınıfı, bir program aracılığıyla denetlenen HTTP protokolü dinleyici sağlar.</span><span class="sxs-lookup"><span data-stu-id="e2bb3-103">The <xref:System.Net.HttpListener> class provides a programmatically controlled HTTP protocol listener.</span></span> <span data-ttu-id="e2bb3-104">Dinleyici ömrü boyunca etkin olan <xref:System.Net.HttpListener> nesne ve uygulamanız içinde çalışır.</span><span class="sxs-lookup"><span data-stu-id="e2bb3-104">The listener is active for the lifetime of the <xref:System.Net.HttpListener> object and runs within your application.</span></span>  
  
## <a name="httpsys"></a><span data-ttu-id="e2bb3-105">HTTP. SYS</span><span class="sxs-lookup"><span data-stu-id="e2bb3-105">HTTP.SYS</span></span>  
 <span data-ttu-id="e2bb3-106"><xref:System.Net.HttpListener> Sınıfı, Windows için tüm HTTP trafiğini işleyen çekirdek modu dinleyicisi HTTP.sys üstünde oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="e2bb3-106">The <xref:System.Net.HttpListener> class is built on top of HTTP.sys, which is the kernel mode listener that handles all HTTP traffic for Windows.</span></span> <span data-ttu-id="e2bb3-107">HTTP.sys bağlantı yönetimi, bant genişliği azaltma ve Web sunucusu günlüğü sağlar.</span><span class="sxs-lookup"><span data-stu-id="e2bb3-107">HTTP.sys provides connection management, bandwidth throttling, and Web server logging.</span></span> <span data-ttu-id="e2bb3-108">Kullanım `HttpCfg.exe` SSL sertifikalarını eklemek için aracı.</span><span class="sxs-lookup"><span data-stu-id="e2bb3-108">Use the `HttpCfg.exe` tool to add SSL certificates.</span></span> <span data-ttu-id="e2bb3-109">Daha fazla bilgi için belgelere bakın [HttpCfg.exe](http://go.microsoft.com/fwlink/?LinkID=178284) içinde aracı [Server](http://go.microsoft.com/fwlink/?LinkID=178285) belgeleri.</span><span class="sxs-lookup"><span data-stu-id="e2bb3-109">For more information, see the documentation on the [HttpCfg.exe](http://go.microsoft.com/fwlink/?LinkID=178284) tool in the [Server](http://go.microsoft.com/fwlink/?LinkID=178285) documentation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e2bb3-110">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e2bb3-110">See Also</span></span>  
 <xref:System.Net.HttpListener>  
 <xref:System.Net.HttpWebRequest>  
 <xref:System.Net.HttpWebResponse>  
 [<span data-ttu-id="e2bb3-111">HTTP sunucusu</span><span class="sxs-lookup"><span data-stu-id="e2bb3-111">HTTP Server</span></span>](http://go.microsoft.com/fwlink/?LinkID=178285)  
 [<span data-ttu-id="e2bb3-112">Internet Information güvenlik iyileştirmeleri</span><span class="sxs-lookup"><span data-stu-id="e2bb3-112">Security Enhancements in Internet Information</span></span>](http://go.microsoft.com/fwlink/?LinkID=178286)  
 [<span data-ttu-id="e2bb3-113">HttpListener ASPX konak uygulama örneği</span><span class="sxs-lookup"><span data-stu-id="e2bb3-113">HttpListener ASPX Host Application Sample</span></span>](http://go.microsoft.com/fwlink/?LinkID=179560)  
 [<span data-ttu-id="e2bb3-114">HttpListener teknoloji örnek</span><span class="sxs-lookup"><span data-stu-id="e2bb3-114">HttpListener Technology Sample</span></span>](http://go.microsoft.com/fwlink/?LinkID=179558)  
 [<span data-ttu-id="e2bb3-115">Ağ Programlama Örnekleri</span><span class="sxs-lookup"><span data-stu-id="e2bb3-115">Network Programming Samples</span></span>](../../../docs/framework/network-programming/network-programming-samples.md)
