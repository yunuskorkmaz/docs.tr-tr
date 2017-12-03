---
title: System.ServiceModel.Activation.WebHostServiceCloseFailed
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3cab9856-a5cf-4f0e-a0cb-89425e368f8e
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 1761ef66bf2aedf2d4382558ba70bf1956af0f3e
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="systemservicemodelactivationwebhostserviceclosefailed"></a><span data-ttu-id="865c8-102">System.ServiceModel.Activation.WebHostServiceCloseFailed</span><span class="sxs-lookup"><span data-stu-id="865c8-102">System.ServiceModel.Activation.WebHostServiceCloseFailed</span></span>
<span data-ttu-id="865c8-103">Hizmet düzgün biçimde kapatılamaz ve iptal gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="865c8-103">Occurs when a service cannot be closed gracefully and is aborted.</span></span>  
  
## <a name="description"></a><span data-ttu-id="865c8-104">Açıklama</span><span class="sxs-lookup"><span data-stu-id="865c8-104">Description</span></span>  
 <span data-ttu-id="865c8-105">Bu hata kodu yalnızca günlük dosyasında görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="865c8-105">This error code only appears in the log file.</span></span> <span data-ttu-id="865c8-106">Bir hizmet durdurma zaten çağrıldıktan sonra kapatmaya çalıştığınızda, genellikle bir programlama hatası örneğin gösterir.</span><span class="sxs-lookup"><span data-stu-id="865c8-106">It usually indicates a programming error, for example, when you try to close a service after Abort has already been called.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="865c8-107">Sorun giderme</span><span class="sxs-lookup"><span data-stu-id="865c8-107">Troubleshooting</span></span>  
 <span data-ttu-id="865c8-108">Uygulama kaynak koduna bakın.</span><span class="sxs-lookup"><span data-stu-id="865c8-108">Check the application source code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="865c8-109">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="865c8-109">See Also</span></span>  
 [<span data-ttu-id="865c8-110">İzleme</span><span class="sxs-lookup"><span data-stu-id="865c8-110">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="865c8-111">Uygulamanızda sorun giderme için izlemeyi kullanma</span><span class="sxs-lookup"><span data-stu-id="865c8-111">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="865c8-112">Yönetim ve tanılama</span><span class="sxs-lookup"><span data-stu-id="865c8-112">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
