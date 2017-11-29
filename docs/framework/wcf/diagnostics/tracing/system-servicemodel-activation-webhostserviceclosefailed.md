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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 8550c30f74968d4f58d9a2fd1deac69bf9d3abe7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="systemservicemodelactivationwebhostserviceclosefailed"></a><span data-ttu-id="f6ca9-102">System.ServiceModel.Activation.WebHostServiceCloseFailed</span><span class="sxs-lookup"><span data-stu-id="f6ca9-102">System.ServiceModel.Activation.WebHostServiceCloseFailed</span></span>
<span data-ttu-id="f6ca9-103">Hizmet düzgün biçimde kapatılamaz ve iptal gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="f6ca9-103">Occurs when a service cannot be closed gracefully and is aborted.</span></span>  
  
## <a name="description"></a><span data-ttu-id="f6ca9-104">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f6ca9-104">Description</span></span>  
 <span data-ttu-id="f6ca9-105">Bu hata kodu yalnızca günlük dosyasında görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="f6ca9-105">This error code only appears in the log file.</span></span> <span data-ttu-id="f6ca9-106">Bir hizmet durdurma zaten çağrıldıktan sonra kapatmaya çalıştığınızda, genellikle bir programlama hatası örneğin gösterir.</span><span class="sxs-lookup"><span data-stu-id="f6ca9-106">It usually indicates a programming error, for example, when you try to close a service after Abort has already been called.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="f6ca9-107">Sorun giderme</span><span class="sxs-lookup"><span data-stu-id="f6ca9-107">Troubleshooting</span></span>  
 <span data-ttu-id="f6ca9-108">Uygulama kaynak koduna bakın.</span><span class="sxs-lookup"><span data-stu-id="f6ca9-108">Check the application source code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f6ca9-109">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f6ca9-109">See Also</span></span>  
 [<span data-ttu-id="f6ca9-110">İzleme</span><span class="sxs-lookup"><span data-stu-id="f6ca9-110">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="f6ca9-111">Uygulamanızda sorun giderme için izlemeyi kullanma</span><span class="sxs-lookup"><span data-stu-id="f6ca9-111">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="f6ca9-112">Yönetim ve tanılama</span><span class="sxs-lookup"><span data-stu-id="f6ca9-112">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
