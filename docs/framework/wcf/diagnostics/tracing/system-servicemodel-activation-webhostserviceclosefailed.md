---
title: System.ServiceModel.Activation.WebHostServiceCloseFailed
ms.date: 03/30/2017
ms.assetid: 3cab9856-a5cf-4f0e-a0cb-89425e368f8e
ms.openlocfilehash: e39ca97bdefafee840206036f89e8b165609516a
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96263015"
---
# <a name="systemservicemodelactivationwebhostserviceclosefailed"></a><span data-ttu-id="09246-102">System.ServiceModel.Activation.WebHostServiceCloseFailed</span><span class="sxs-lookup"><span data-stu-id="09246-102">System.ServiceModel.Activation.WebHostServiceCloseFailed</span></span>

<span data-ttu-id="09246-103">Bir hizmet düzgün şekilde kapatılamazsa ve iptal edildiğinde gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="09246-103">Occurs when a service cannot be closed gracefully and is aborted.</span></span>  
  
## <a name="description"></a><span data-ttu-id="09246-104">Açıklama</span><span class="sxs-lookup"><span data-stu-id="09246-104">Description</span></span>  

 <span data-ttu-id="09246-105">Bu hata kodu yalnızca günlük dosyasında görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="09246-105">This error code only appears in the log file.</span></span> <span data-ttu-id="09246-106">Genellikle bir programlama hatası gösterir, örneğin, durdurma zaten çağrıldıktan sonra bir hizmeti kapatmaya çalıştığınızda.</span><span class="sxs-lookup"><span data-stu-id="09246-106">It usually indicates a programming error, for example, when you try to close a service after Abort has already been called.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="09246-107">Sorun giderme</span><span class="sxs-lookup"><span data-stu-id="09246-107">Troubleshooting</span></span>  

 <span data-ttu-id="09246-108">Uygulama kaynak kodunu kontrol edin.</span><span class="sxs-lookup"><span data-stu-id="09246-108">Check the application source code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="09246-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="09246-109">See also</span></span>

- [<span data-ttu-id="09246-110">İzleme</span><span class="sxs-lookup"><span data-stu-id="09246-110">Tracing</span></span>](index.md)
- [<span data-ttu-id="09246-111">Uygulamanızda Sorun Giderme için İzleme Kullanma</span><span class="sxs-lookup"><span data-stu-id="09246-111">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="09246-112">Yönetim ve tanılama</span><span class="sxs-lookup"><span data-stu-id="09246-112">Administration and Diagnostics</span></span>](../index.md)
