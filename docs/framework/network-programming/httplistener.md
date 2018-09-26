---
title: HttpListener
ms.date: 03/30/2017
helpviewer_keywords:
- HTTP
ms.assetid: 5b89d3fb-3c9a-49e2-af1f-c34c020c68ac
author: mcleblanc
ms.author: markl
ms.openlocfilehash: 0d5b7fccdac9dba3fd44d12241dd60cbaefa1b7a
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/26/2018
ms.locfileid: "47192946"
---
# <a name="httplistener"></a><span data-ttu-id="9da93-102">HttpListener</span><span class="sxs-lookup"><span data-stu-id="9da93-102">HttpListener</span></span>
<span data-ttu-id="9da93-103"><xref:System.Net.HttpListener> Programlı bir şekilde denetlenen bir HTTP protokolü dinleyicisi sınıfı sağlar.</span><span class="sxs-lookup"><span data-stu-id="9da93-103">The <xref:System.Net.HttpListener> class provides a programmatically controlled HTTP protocol listener.</span></span> <span data-ttu-id="9da93-104">Dinleyici ömrü boyunca etkin olduğu <xref:System.Net.HttpListener> nesne ve uygulamanız içinde çalışır.</span><span class="sxs-lookup"><span data-stu-id="9da93-104">The listener is active for the lifetime of the <xref:System.Net.HttpListener> object and runs within your application.</span></span>  
  
## <a name="httpsys"></a><span data-ttu-id="9da93-105">HTTP. SYS</span><span class="sxs-lookup"><span data-stu-id="9da93-105">HTTP.SYS</span></span>  
 <span data-ttu-id="9da93-106"><xref:System.Net.HttpListener> Sınıfı, Windows için tüm HTTP trafiğini işleyen çekirdek modu dinleyici HTTP.sys üzerine kurulmuştur.</span><span class="sxs-lookup"><span data-stu-id="9da93-106">The <xref:System.Net.HttpListener> class is built on top of HTTP.sys, which is the kernel mode listener that handles all HTTP traffic for Windows.</span></span> <span data-ttu-id="9da93-107">HTTP.sys bağlantı yönetimi, bant genişliği azaltma ve Web sunucusu günlüğü sağlar.</span><span class="sxs-lookup"><span data-stu-id="9da93-107">HTTP.sys provides connection management, bandwidth throttling, and Web server logging.</span></span> <span data-ttu-id="9da93-108">Kullanım `HttpCfg.exe` SSL sertifikaları eklemek için araç.</span><span class="sxs-lookup"><span data-stu-id="9da93-108">Use the `HttpCfg.exe` tool to add SSL certificates.</span></span> <span data-ttu-id="9da93-109">Daha fazla bilgi için şirket belgelerine bakın. [HttpCfg.exe](https://go.microsoft.com/fwlink/?LinkID=178284) aracına [sunucu](https://go.microsoft.com/fwlink/?LinkID=178285) belgeleri.</span><span class="sxs-lookup"><span data-stu-id="9da93-109">For more information, see the documentation on the [HttpCfg.exe](https://go.microsoft.com/fwlink/?LinkID=178284) tool in the [Server](https://go.microsoft.com/fwlink/?LinkID=178285) documentation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9da93-110">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="9da93-110">See Also</span></span>  
 <xref:System.Net.HttpListener>  
 <xref:System.Net.HttpWebRequest>  
 <xref:System.Net.HttpWebResponse>  
 [<span data-ttu-id="9da93-111">HTTP sunucusu</span><span class="sxs-lookup"><span data-stu-id="9da93-111">HTTP Server</span></span>](https://go.microsoft.com/fwlink/?LinkID=178285)  
 [<span data-ttu-id="9da93-112">Internet Information güvenlik geliştirmeleri</span><span class="sxs-lookup"><span data-stu-id="9da93-112">Security Enhancements in Internet Information</span></span>](https://go.microsoft.com/fwlink/?LinkID=178286)  
 [<span data-ttu-id="9da93-113">HttpListener ASPX konak uygulama örneği</span><span class="sxs-lookup"><span data-stu-id="9da93-113">HttpListener ASPX Host Application Sample</span></span>](https://go.microsoft.com/fwlink/?LinkID=179560)  
 [<span data-ttu-id="9da93-114">HttpListener teknolojisi örneği</span><span class="sxs-lookup"><span data-stu-id="9da93-114">HttpListener Technology Sample</span></span>](https://go.microsoft.com/fwlink/?LinkID=179558)  
 [<span data-ttu-id="9da93-115">Ağ Programlama Örnekleri</span><span class="sxs-lookup"><span data-stu-id="9da93-115">Network Programming Samples</span></span>](../../../docs/framework/network-programming/network-programming-samples.md)
