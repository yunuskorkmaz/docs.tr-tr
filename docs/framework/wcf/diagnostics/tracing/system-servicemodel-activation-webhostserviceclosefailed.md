---
description: ': System. ServiceModel. Activation. WebHostServiceCloseFailed hakkında daha fazla bilgi edinin'
title: System.ServiceModel.Activation.WebHostServiceCloseFailed
ms.date: 03/30/2017
ms.assetid: 3cab9856-a5cf-4f0e-a0cb-89425e368f8e
ms.openlocfilehash: fae41b72e2eb9aba76993081769afc42c0ec8975
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99720455"
---
# <a name="systemservicemodelactivationwebhostserviceclosefailed"></a><span data-ttu-id="62864-103">System.ServiceModel.Activation.WebHostServiceCloseFailed</span><span class="sxs-lookup"><span data-stu-id="62864-103">System.ServiceModel.Activation.WebHostServiceCloseFailed</span></span>

<span data-ttu-id="62864-104">Bir hizmet düzgün şekilde kapatılamazsa ve iptal edildiğinde gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="62864-104">Occurs when a service cannot be closed gracefully and is aborted.</span></span>  
  
## <a name="description"></a><span data-ttu-id="62864-105">Description</span><span class="sxs-lookup"><span data-stu-id="62864-105">Description</span></span>  

 <span data-ttu-id="62864-106">Bu hata kodu yalnızca günlük dosyasında görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="62864-106">This error code only appears in the log file.</span></span> <span data-ttu-id="62864-107">Genellikle bir programlama hatası gösterir, örneğin, durdurma zaten çağrıldıktan sonra bir hizmeti kapatmaya çalıştığınızda.</span><span class="sxs-lookup"><span data-stu-id="62864-107">It usually indicates a programming error, for example, when you try to close a service after Abort has already been called.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="62864-108">Sorun giderme</span><span class="sxs-lookup"><span data-stu-id="62864-108">Troubleshooting</span></span>  

 <span data-ttu-id="62864-109">Uygulama kaynak kodunu kontrol edin.</span><span class="sxs-lookup"><span data-stu-id="62864-109">Check the application source code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="62864-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="62864-110">See also</span></span>

- [<span data-ttu-id="62864-111">İzleme</span><span class="sxs-lookup"><span data-stu-id="62864-111">Tracing</span></span>](index.md)
- [<span data-ttu-id="62864-112">Uygulamanızda Sorun Giderme için İzleme Kullanma</span><span class="sxs-lookup"><span data-stu-id="62864-112">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="62864-113">Yönetim ve tanılama</span><span class="sxs-lookup"><span data-stu-id="62864-113">Administration and Diagnostics</span></span>](../index.md)
