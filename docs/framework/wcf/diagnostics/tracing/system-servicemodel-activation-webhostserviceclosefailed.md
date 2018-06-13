---
title: System.ServiceModel.Activation.WebHostServiceCloseFailed
ms.date: 03/30/2017
ms.assetid: 3cab9856-a5cf-4f0e-a0cb-89425e368f8e
ms.openlocfilehash: aa9df795ee8601a4c4f4e2ce7427ffb0dd530bba
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33476493"
---
# <a name="systemservicemodelactivationwebhostserviceclosefailed"></a><span data-ttu-id="09c78-102">System.ServiceModel.Activation.WebHostServiceCloseFailed</span><span class="sxs-lookup"><span data-stu-id="09c78-102">System.ServiceModel.Activation.WebHostServiceCloseFailed</span></span>
<span data-ttu-id="09c78-103">Hizmet düzgün biçimde kapatılamaz ve iptal gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="09c78-103">Occurs when a service cannot be closed gracefully and is aborted.</span></span>  
  
## <a name="description"></a><span data-ttu-id="09c78-104">Açıklama</span><span class="sxs-lookup"><span data-stu-id="09c78-104">Description</span></span>  
 <span data-ttu-id="09c78-105">Bu hata kodu yalnızca günlük dosyasında görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="09c78-105">This error code only appears in the log file.</span></span> <span data-ttu-id="09c78-106">Bir hizmet durdurma zaten çağrıldıktan sonra kapatmaya çalıştığınızda, genellikle bir programlama hatası örneğin gösterir.</span><span class="sxs-lookup"><span data-stu-id="09c78-106">It usually indicates a programming error, for example, when you try to close a service after Abort has already been called.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="09c78-107">Sorun giderme</span><span class="sxs-lookup"><span data-stu-id="09c78-107">Troubleshooting</span></span>  
 <span data-ttu-id="09c78-108">Uygulama kaynak koduna bakın.</span><span class="sxs-lookup"><span data-stu-id="09c78-108">Check the application source code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="09c78-109">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="09c78-109">See Also</span></span>  
 [<span data-ttu-id="09c78-110">İzleme</span><span class="sxs-lookup"><span data-stu-id="09c78-110">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="09c78-111">Uygulamanızda Sorun Giderme için İzleme Kullanma</span><span class="sxs-lookup"><span data-stu-id="09c78-111">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="09c78-112">Yönetim ve Tanılama</span><span class="sxs-lookup"><span data-stu-id="09c78-112">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
