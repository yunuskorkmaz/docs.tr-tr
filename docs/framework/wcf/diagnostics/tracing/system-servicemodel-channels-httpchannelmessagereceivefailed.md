---
title: System.ServiceModel.Channels.HttpChannelMessageReceiveFailed
ms.date: 03/30/2017
ms.assetid: 9eb311da-fdcc-4dd3-9d85-05b3280dfdda
ms.openlocfilehash: 97f22a01df84c39915f74fa7677e5dd18154b952
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96256228"
---
# <a name="systemservicemodelchannelshttpchannelmessagereceivefailed"></a><span data-ttu-id="15916-102">System.ServiceModel.Channels.HttpChannelMessageReceiveFailed</span><span class="sxs-lookup"><span data-stu-id="15916-102">System.ServiceModel.Channels.HttpChannelMessageReceiveFailed</span></span>

<span data-ttu-id="15916-103">HTTP kanalı üzerinden bir ileti alınamadı.</span><span class="sxs-lookup"><span data-stu-id="15916-103">Failed to receive a message over an HTTP channel.</span></span>  
  
## <a name="description"></a><span data-ttu-id="15916-104">Açıklama</span><span class="sxs-lookup"><span data-stu-id="15916-104">Description</span></span>  

 <span data-ttu-id="15916-105">Bu izleme bir uyarı veya hata olarak dağıtılabilir.</span><span class="sxs-lookup"><span data-stu-id="15916-105">This trace can be emitted as a warning or an error.</span></span> <span data-ttu-id="15916-106">Her iki durumda da, gelen HTTP isteği için uyumlu bir dinleyici bulunamadığında ve HTTP isteği atıldığı zaman, izleme yayınlanır.</span><span class="sxs-lookup"><span data-stu-id="15916-106">In both cases, the trace is emitted when a compatible listener is not found for an incoming HTTP request and the HTTP request is discarded.</span></span> <span data-ttu-id="15916-107">Bu durum, isteğin HTTP fiilinin herhangi bir HTTP dinleyicisi tarafından tanınamadığı veya isteğin hedeflediği adreste bir dinleyici dinlediği için meydana gelebilir.</span><span class="sxs-lookup"><span data-stu-id="15916-107">This could happen because the request’s HTTP verb was not recognized by any HTTP listener, or because no listener was listening on the address the request was targeted for.</span></span> <span data-ttu-id="15916-108">İzleme, şirket içinde barındırılan durumda ve hizmet IIS 'de barındırıldığında bir hata olarak bir uyarı olarak yayınlanır.</span><span class="sxs-lookup"><span data-stu-id="15916-108">The trace is emitted as a warning in the self-hosted case, and as an error when the service is hosted in IIS.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="15916-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="15916-109">See also</span></span>

- [<span data-ttu-id="15916-110">İzleme</span><span class="sxs-lookup"><span data-stu-id="15916-110">Tracing</span></span>](index.md)
- [<span data-ttu-id="15916-111">Uygulamanızda Sorun Giderme için İzleme Kullanma</span><span class="sxs-lookup"><span data-stu-id="15916-111">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="15916-112">Yönetim ve tanılama</span><span class="sxs-lookup"><span data-stu-id="15916-112">Administration and Diagnostics</span></span>](../index.md)
