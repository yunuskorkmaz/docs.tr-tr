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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: a258b315b5a8537de87a603b5d1ec0c18387ddbe
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="systemservicemodelchannelshttpchannelmessagereceivefailed"></a><span data-ttu-id="c712a-102">System.ServiceModel.Channels.HttpChannelMessageReceiveFailed</span><span class="sxs-lookup"><span data-stu-id="c712a-102">System.ServiceModel.Channels.HttpChannelMessageReceiveFailed</span></span>
<span data-ttu-id="c712a-103">Bir HTTP kanalı üzerinden bir ileti almak başarısız oldu.</span><span class="sxs-lookup"><span data-stu-id="c712a-103">Failed to receive a message over an HTTP channel.</span></span>  
  
## <a name="description"></a><span data-ttu-id="c712a-104">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c712a-104">Description</span></span>  
 <span data-ttu-id="c712a-105">Bu izleme, bir uyarı veya hata gösterilen.</span><span class="sxs-lookup"><span data-stu-id="c712a-105">This trace can be emitted as a warning or an error.</span></span> <span data-ttu-id="c712a-106">Her iki durumda da, uyumlu bir dinleyici için gelen bir HTTP isteği bulunamadı ve HTTP isteği atılır izleme yayınlanır.</span><span class="sxs-lookup"><span data-stu-id="c712a-106">In both cases, the trace is emitted when a compatible listener is not found for an incoming HTTP request and the HTTP request is discarded.</span></span> <span data-ttu-id="c712a-107">İsteğin HTTP fiili tüm HTTP dinleyicisi tarafından tanınmadı ya da hiç dinleyici adresini dinlemesini olduğundan isteği için hedeflendiğini çünkü bu meydana gelmiş olabilir.</span><span class="sxs-lookup"><span data-stu-id="c712a-107">This could happen because the request’s HTTP verb was not recognized by any HTTP listener, or because no listener was listening on the address the request was targeted for.</span></span> <span data-ttu-id="c712a-108">Hizmet IIS içinde barındırıldığında izleme kendini barındıran durumda bir uyarı ve hata olarak yayılır.</span><span class="sxs-lookup"><span data-stu-id="c712a-108">The trace is emitted as a warning in the self-hosted case, and as an error when the service is hosted in IIS.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c712a-109">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c712a-109">See Also</span></span>  
 [<span data-ttu-id="c712a-110">İzleme</span><span class="sxs-lookup"><span data-stu-id="c712a-110">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="c712a-111">Uygulamanızda sorun giderme için izlemeyi kullanma</span><span class="sxs-lookup"><span data-stu-id="c712a-111">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="c712a-112">Yönetim ve tanılama</span><span class="sxs-lookup"><span data-stu-id="c712a-112">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
