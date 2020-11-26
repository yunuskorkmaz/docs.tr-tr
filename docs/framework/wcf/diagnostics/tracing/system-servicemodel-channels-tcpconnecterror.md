---
title: System.ServiceModel.Channels.TcpConnectError
ms.date: 03/30/2017
ms.assetid: 22d93797-072e-405d-a3e0-5c519ddf290b
ms.openlocfilehash: 5efc14109fb2ad2d4444baae0d9423694e0f5b25
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96246816"
---
# <a name="systemservicemodelchannelstcpconnecterror"></a><span data-ttu-id="76852-102">System.ServiceModel.Channels.TcpConnectError</span><span class="sxs-lookup"><span data-stu-id="76852-102">System.ServiceModel.Channels.TcpConnectError</span></span>

<span data-ttu-id="76852-103">TCP bağlanma işlemi başarısız oldu.</span><span class="sxs-lookup"><span data-stu-id="76852-103">The TCP connect operation failed.</span></span>  
  
## <a name="description"></a><span data-ttu-id="76852-104">Açıklama</span><span class="sxs-lookup"><span data-stu-id="76852-104">Description</span></span>  

 <span data-ttu-id="76852-105">Bu uyarı düzeyi izleme, bir TCP uç noktasına bağlanma başarısızlığının olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="76852-105">This warning level trace indicates a failure to connect to a TCP endpoint.</span></span> <span data-ttu-id="76852-106">Bu durum, uzak uç noktanın belirli bir IP adresi ve bağlantı noktasında yanıt vermemesi durumunda meydana gelebilir.</span><span class="sxs-lookup"><span data-stu-id="76852-106">This could happen if the remote endpoint is not responding at a given IP address and port.</span></span> <span data-ttu-id="76852-107">Sonraki geçerli IP adreslerine (örneğin, IPv4 veya IPv6 adresleri ya da belirli bir ana bilgisayar adını temsil eden diğer IP adresleri) bağlanmayı denediğinde bu izleme yoksayılabilir.</span><span class="sxs-lookup"><span data-stu-id="76852-107">This trace can be ignored if subsequent attempts to connect to other valid IP addresses (such as IPv4 or IPv6 addresses, or other IP addresses representing a given hostname) succeed.</span></span> <span data-ttu-id="76852-108">Bu izleme içindeki özel durum, hata hakkındaki ek bilgileri açığa çıkaryükleyebilir.</span><span class="sxs-lookup"><span data-stu-id="76852-108">The exception within this trace can reveal additional information about the error.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="76852-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="76852-109">See also</span></span>

- [<span data-ttu-id="76852-110">İzleme</span><span class="sxs-lookup"><span data-stu-id="76852-110">Tracing</span></span>](index.md)
- [<span data-ttu-id="76852-111">Uygulamanızda Sorun Giderme için İzleme Kullanma</span><span class="sxs-lookup"><span data-stu-id="76852-111">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="76852-112">Yönetim ve tanılama</span><span class="sxs-lookup"><span data-stu-id="76852-112">Administration and Diagnostics</span></span>](../index.md)
