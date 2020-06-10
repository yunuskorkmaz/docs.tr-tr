---
title: System.ServiceModel.Channels.FailedPipeConnect
ms.date: 03/30/2017
ms.assetid: 9a827e0f-fb91-46bb-bd54-926d4b74d8a6
ms.openlocfilehash: 790a15e5401850f2767cb06f5f321ad80c674f2b
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84582419"
---
# <a name="systemservicemodelchannelsfailedpipeconnect"></a><span data-ttu-id="c741a-102">System.ServiceModel.Channels.FailedPipeConnect</span><span class="sxs-lookup"><span data-stu-id="c741a-102">System.ServiceModel.Channels.FailedPipeConnect</span></span>
<span data-ttu-id="c741a-103">Adlandırılmış kanal uç noktasına bağlanma girişimi başarısız oldu.</span><span class="sxs-lookup"><span data-stu-id="c741a-103">An attempt to connect to the named pipe endpoint failed.</span></span> <span data-ttu-id="c741a-104">Belirtilen zaman aşımı süresi içinde başka bir girişim yapılır.</span><span class="sxs-lookup"><span data-stu-id="c741a-104">Another attempt is made within the specified timeout period.</span></span>  
  
## <a name="description"></a><span data-ttu-id="c741a-105">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c741a-105">Description</span></span>  
 <span data-ttu-id="c741a-106">Bu bilgi izleme, adlandırılmış kanal uç noktasına bağlanma başarısızlığının olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="c741a-106">This informational trace indicates a failure to connect to a named pipe endpoint.</span></span> <span data-ttu-id="c741a-107">Adlandırılmış kanal uç noktası bulunamazsa veya meşgulse bu durum oluşabilir.</span><span class="sxs-lookup"><span data-stu-id="c741a-107">This could happen if the named pipe endpoint is not found or is busy.</span></span> <span data-ttu-id="c741a-108">Her biri başarılı olana veya OpenTimeout sona erene kadar, her biri kısa bir süre ayırarak ek denemeler yapılır.</span><span class="sxs-lookup"><span data-stu-id="c741a-108">Additional attempts are made, each separated by a short amount of time, until one succeeds or the OpenTimeout expires.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c741a-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c741a-109">See also</span></span>

- [<span data-ttu-id="c741a-110">İzleme</span><span class="sxs-lookup"><span data-stu-id="c741a-110">Tracing</span></span>](index.md)
- [<span data-ttu-id="c741a-111">Uygulamanızda Sorun Giderme için İzleme Kullanma</span><span class="sxs-lookup"><span data-stu-id="c741a-111">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="c741a-112">Yönetim ve tanılama</span><span class="sxs-lookup"><span data-stu-id="c741a-112">Administration and Diagnostics</span></span>](../index.md)
