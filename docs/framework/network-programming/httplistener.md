---
title: HttpListener
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: HTTP
ms.assetid: 5b89d3fb-3c9a-49e2-af1f-c34c020c68ac
caps.latest.revision: "9"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: ca0a22ff1d06485658da75a46bd408a12a3a964c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="httplistener"></a><span data-ttu-id="1d404-102">HttpListener</span><span class="sxs-lookup"><span data-stu-id="1d404-102">HttpListener</span></span>
<span data-ttu-id="1d404-103"><xref:System.Net.HttpListener> Sınıfı, bir program aracılığıyla denetlenen HTTP protokolü dinleyici sağlar.</span><span class="sxs-lookup"><span data-stu-id="1d404-103">The <xref:System.Net.HttpListener> class provides a programmatically controlled HTTP protocol listener.</span></span> <span data-ttu-id="1d404-104">Dinleyici ömrü boyunca etkin olan <xref:System.Net.HttpListener> nesne ve uygulamanız içinde çalışır.</span><span class="sxs-lookup"><span data-stu-id="1d404-104">The listener is active for the lifetime of the <xref:System.Net.HttpListener> object and runs within your application.</span></span>  
  
## <a name="httpsys"></a><span data-ttu-id="1d404-105">HTTP. SYS</span><span class="sxs-lookup"><span data-stu-id="1d404-105">HTTP.SYS</span></span>  
 <span data-ttu-id="1d404-106"><xref:System.Net.HttpListener> Sınıfı, Windows için tüm HTTP trafiğini işleyen çekirdek modu dinleyicisi HTTP.sys üstünde oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="1d404-106">The <xref:System.Net.HttpListener> class is built on top of HTTP.sys, which is the kernel mode listener that handles all HTTP traffic for Windows.</span></span> <span data-ttu-id="1d404-107">HTTP.sys bağlantı yönetimi, bant genişliği azaltma ve Web sunucusu günlüğü sağlar.</span><span class="sxs-lookup"><span data-stu-id="1d404-107">HTTP.sys provides connection management, bandwidth throttling, and Web server logging.</span></span> <span data-ttu-id="1d404-108">Kullanım `HttpCfg.exe` SSL sertifikalarını eklemek için aracı.</span><span class="sxs-lookup"><span data-stu-id="1d404-108">Use the `HttpCfg.exe` tool to add SSL certificates.</span></span> <span data-ttu-id="1d404-109">Daha fazla bilgi için belgelere bakın [HttpCfg.exe](http://go.microsoft.com/fwlink/?LinkID=178284) içinde aracı [Server](http://go.microsoft.com/fwlink/?LinkID=178285) belgeleri.</span><span class="sxs-lookup"><span data-stu-id="1d404-109">For more information, see the documentation on the [HttpCfg.exe](http://go.microsoft.com/fwlink/?LinkID=178284) tool in the [Server](http://go.microsoft.com/fwlink/?LinkID=178285) documentation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1d404-110">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="1d404-110">See Also</span></span>  
 <xref:System.Net.HttpListener>  
 <xref:System.Net.HttpWebRequest>  
 <xref:System.Net.HttpWebResponse>  
 [<span data-ttu-id="1d404-111">HTTP sunucusu</span><span class="sxs-lookup"><span data-stu-id="1d404-111">HTTP Server</span></span>](http://go.microsoft.com/fwlink/?LinkID=178285)  
 [<span data-ttu-id="1d404-112">Internet Information güvenlik iyileştirmeleri</span><span class="sxs-lookup"><span data-stu-id="1d404-112">Security Enhancements in Internet Information</span></span>](http://go.microsoft.com/fwlink/?LinkID=178286)  
 [<span data-ttu-id="1d404-113">HttpListener ASPX konak uygulama örneği</span><span class="sxs-lookup"><span data-stu-id="1d404-113">HttpListener ASPX Host Application Sample</span></span>](http://go.microsoft.com/fwlink/?LinkID=179560)  
 [<span data-ttu-id="1d404-114">HttpListener teknoloji örnek</span><span class="sxs-lookup"><span data-stu-id="1d404-114">HttpListener Technology Sample</span></span>](http://go.microsoft.com/fwlink/?LinkID=179558)  
 [<span data-ttu-id="1d404-115">Ağ programlama örnekleri</span><span class="sxs-lookup"><span data-stu-id="1d404-115">Network Programming Samples</span></span>](../../../docs/framework/network-programming/network-programming-samples.md)
