---
title: System.ServiceModel.Channels.HttpChannelMessageReceiveFailed
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9eb311da-fdcc-4dd3-9d85-05b3280dfdda
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 46bc39237f0a6f0b9b25b9616782ec3e97fa22ca
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="systemservicemodelchannelshttpchannelmessagereceivefailed"></a><span data-ttu-id="9ccb7-102">System.ServiceModel.Channels.HttpChannelMessageReceiveFailed</span><span class="sxs-lookup"><span data-stu-id="9ccb7-102">System.ServiceModel.Channels.HttpChannelMessageReceiveFailed</span></span>
<span data-ttu-id="9ccb7-103">Bir HTTP kanalı üzerinden bir ileti almak başarısız oldu.</span><span class="sxs-lookup"><span data-stu-id="9ccb7-103">Failed to receive a message over an HTTP channel.</span></span>  
  
## <a name="description"></a><span data-ttu-id="9ccb7-104">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9ccb7-104">Description</span></span>  
 <span data-ttu-id="9ccb7-105">Bu izleme, bir uyarı veya hata gösterilen.</span><span class="sxs-lookup"><span data-stu-id="9ccb7-105">This trace can be emitted as a warning or an error.</span></span> <span data-ttu-id="9ccb7-106">Her iki durumda da, uyumlu bir dinleyici için gelen bir HTTP isteği bulunamadı ve HTTP isteği atılır izleme yayınlanır.</span><span class="sxs-lookup"><span data-stu-id="9ccb7-106">In both cases, the trace is emitted when a compatible listener is not found for an incoming HTTP request and the HTTP request is discarded.</span></span> <span data-ttu-id="9ccb7-107">İsteğin HTTP fiili tüm HTTP dinleyicisi tarafından tanınmadı ya da hiç dinleyici adresini dinlemesini olduğundan isteği için hedeflendiğini çünkü bu meydana gelmiş olabilir.</span><span class="sxs-lookup"><span data-stu-id="9ccb7-107">This could happen because the request’s HTTP verb was not recognized by any HTTP listener, or because no listener was listening on the address the request was targeted for.</span></span> <span data-ttu-id="9ccb7-108">Hizmet IIS içinde barındırıldığında izleme kendini barındıran durumda bir uyarı ve hata olarak yayılır.</span><span class="sxs-lookup"><span data-stu-id="9ccb7-108">The trace is emitted as a warning in the self-hosted case, and as an error when the service is hosted in IIS.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9ccb7-109">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="9ccb7-109">See Also</span></span>  
 [<span data-ttu-id="9ccb7-110">İzleme</span><span class="sxs-lookup"><span data-stu-id="9ccb7-110">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="9ccb7-111">Uygulamanızda Sorun Giderme için İzleme Kullanma</span><span class="sxs-lookup"><span data-stu-id="9ccb7-111">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="9ccb7-112">Yönetim ve Tanılama</span><span class="sxs-lookup"><span data-stu-id="9ccb7-112">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
