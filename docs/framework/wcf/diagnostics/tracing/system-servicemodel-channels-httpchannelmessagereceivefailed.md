---
description: ': System. ServiceModel. Channels. HttpChannelMessageReceiveFailed hakkında daha fazla bilgi edinin'
title: System.ServiceModel.Channels.HttpChannelMessageReceiveFailed
ms.date: 03/30/2017
ms.assetid: 9eb311da-fdcc-4dd3-9d85-05b3280dfdda
ms.openlocfilehash: 41c31305fabc369faedec460fc3a042426d45e37
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99769877"
---
# <a name="systemservicemodelchannelshttpchannelmessagereceivefailed"></a><span data-ttu-id="84d63-103">System.ServiceModel.Channels.HttpChannelMessageReceiveFailed</span><span class="sxs-lookup"><span data-stu-id="84d63-103">System.ServiceModel.Channels.HttpChannelMessageReceiveFailed</span></span>

<span data-ttu-id="84d63-104">HTTP kanalı üzerinden bir ileti alınamadı.</span><span class="sxs-lookup"><span data-stu-id="84d63-104">Failed to receive a message over an HTTP channel.</span></span>  
  
## <a name="description"></a><span data-ttu-id="84d63-105">Description</span><span class="sxs-lookup"><span data-stu-id="84d63-105">Description</span></span>  

 <span data-ttu-id="84d63-106">Bu izleme bir uyarı veya hata olarak dağıtılabilir.</span><span class="sxs-lookup"><span data-stu-id="84d63-106">This trace can be emitted as a warning or an error.</span></span> <span data-ttu-id="84d63-107">Her iki durumda da, gelen HTTP isteği için uyumlu bir dinleyici bulunamadığında ve HTTP isteği atıldığı zaman, izleme yayınlanır.</span><span class="sxs-lookup"><span data-stu-id="84d63-107">In both cases, the trace is emitted when a compatible listener is not found for an incoming HTTP request and the HTTP request is discarded.</span></span> <span data-ttu-id="84d63-108">Bu durum, isteğin HTTP fiilinin herhangi bir HTTP dinleyicisi tarafından tanınamadığı veya isteğin hedeflediği adreste bir dinleyici dinlediği için meydana gelebilir.</span><span class="sxs-lookup"><span data-stu-id="84d63-108">This could happen because the request’s HTTP verb was not recognized by any HTTP listener, or because no listener was listening on the address the request was targeted for.</span></span> <span data-ttu-id="84d63-109">İzleme, şirket içinde barındırılan durumda ve hizmet IIS 'de barındırıldığında bir hata olarak bir uyarı olarak yayınlanır.</span><span class="sxs-lookup"><span data-stu-id="84d63-109">The trace is emitted as a warning in the self-hosted case, and as an error when the service is hosted in IIS.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="84d63-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="84d63-110">See also</span></span>

- [<span data-ttu-id="84d63-111">İzleme</span><span class="sxs-lookup"><span data-stu-id="84d63-111">Tracing</span></span>](index.md)
- [<span data-ttu-id="84d63-112">Uygulamanızda Sorun Giderme için İzleme Kullanma</span><span class="sxs-lookup"><span data-stu-id="84d63-112">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="84d63-113">Yönetim ve tanılama</span><span class="sxs-lookup"><span data-stu-id="84d63-113">Administration and Diagnostics</span></span>](../index.md)
