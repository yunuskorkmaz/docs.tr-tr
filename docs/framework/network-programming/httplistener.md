---
title: HttpListener
ms.date: 03/30/2017
helpviewer_keywords:
- HTTP
ms.assetid: 5b89d3fb-3c9a-49e2-af1f-c34c020c68ac
ms.openlocfilehash: d5b07617617ac28e4f7f72bc23a96b45a85dff75
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71047987"
---
# <a name="httplistener"></a><span data-ttu-id="43a0a-102">HttpListener</span><span class="sxs-lookup"><span data-stu-id="43a0a-102">HttpListener</span></span>
<span data-ttu-id="43a0a-103">Sınıfı <xref:System.Net.HttpListener> , programlı olarak denetlenen bir http protokol dinleyicisi sağlar.</span><span class="sxs-lookup"><span data-stu-id="43a0a-103">The <xref:System.Net.HttpListener> class provides a programmatically controlled HTTP protocol listener.</span></span> <span data-ttu-id="43a0a-104">Dinleyici, <xref:System.Net.HttpListener> nesne ömrü için etkin ve uygulamanızda çalıştırılır.</span><span class="sxs-lookup"><span data-stu-id="43a0a-104">The listener is active for the lifetime of the <xref:System.Net.HttpListener> object and runs within your application.</span></span>  
  
## <a name="httpsys"></a><span data-ttu-id="43a0a-105">HTTP. DOSYASINDA</span><span class="sxs-lookup"><span data-stu-id="43a0a-105">HTTP.SYS</span></span>  
 <span data-ttu-id="43a0a-106"><xref:System.Net.HttpListener> Sınıfı, Windows için tüm HTTP trafiğini işleyen çekirdek modu dinleyicisi olan http. sys ' nin üzerine kurulmuştur.</span><span class="sxs-lookup"><span data-stu-id="43a0a-106">The <xref:System.Net.HttpListener> class is built on top of HTTP.sys, which is the kernel mode listener that handles all HTTP traffic for Windows.</span></span> <span data-ttu-id="43a0a-107">HTTP. sys, bağlantı yönetimi, bant genişliği azaltma ve Web sunucusu günlüğü sağlar.</span><span class="sxs-lookup"><span data-stu-id="43a0a-107">HTTP.sys provides connection management, bandwidth throttling, and Web server logging.</span></span> <span data-ttu-id="43a0a-108">SSL sertifikaları eklemek için aracınıkullanın.`HttpCfg.exe`</span><span class="sxs-lookup"><span data-stu-id="43a0a-108">Use the `HttpCfg.exe` tool to add SSL certificates.</span></span> <span data-ttu-id="43a0a-109">Daha fazla bilgi için [sunucu](https://go.microsoft.com/fwlink/?LinkID=178285) belgelerindeki [Httpcfg. exe](https://go.microsoft.com/fwlink/?LinkID=178284) aracında bulunan belgelere bakın.</span><span class="sxs-lookup"><span data-stu-id="43a0a-109">For more information, see the documentation on the [HttpCfg.exe](https://go.microsoft.com/fwlink/?LinkID=178284) tool in the [Server](https://go.microsoft.com/fwlink/?LinkID=178285) documentation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="43a0a-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="43a0a-110">See also</span></span>

- <xref:System.Net.HttpListener>
- <xref:System.Net.HttpWebRequest>
- <xref:System.Net.HttpWebResponse>
- [<span data-ttu-id="43a0a-111">HTTP sunucusu</span><span class="sxs-lookup"><span data-stu-id="43a0a-111">HTTP Server</span></span>](https://go.microsoft.com/fwlink/?LinkID=178285)
- [<span data-ttu-id="43a0a-112">Internet bilgilerinde güvenlik geliştirmeleri</span><span class="sxs-lookup"><span data-stu-id="43a0a-112">Security Enhancements in Internet Information</span></span>](https://go.microsoft.com/fwlink/?LinkID=178286)
- [<span data-ttu-id="43a0a-113">HttpListener ASPX konak uygulaması örneği</span><span class="sxs-lookup"><span data-stu-id="43a0a-113">HttpListener ASPX Host Application Sample</span></span>](https://go.microsoft.com/fwlink/?LinkID=179560)
- [<span data-ttu-id="43a0a-114">HttpListener teknoloji örneği</span><span class="sxs-lookup"><span data-stu-id="43a0a-114">HttpListener Technology Sample</span></span>](https://go.microsoft.com/fwlink/?LinkID=179558)
- [<span data-ttu-id="43a0a-115">Ağ Programlama Örnekleri</span><span class="sxs-lookup"><span data-stu-id="43a0a-115">Network Programming Samples</span></span>](network-programming-samples.md)
