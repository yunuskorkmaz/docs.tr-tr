---
title: System.ServiceModel.Activation.WebHostServiceCloseFailed
ms.date: 03/30/2017
ms.assetid: 3cab9856-a5cf-4f0e-a0cb-89425e368f8e
ms.openlocfilehash: 0ed3a9a1c16247f94c739a43d84d51e4750b3c2f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54597664"
---
# <a name="systemservicemodelactivationwebhostserviceclosefailed"></a><span data-ttu-id="1d3e8-102">System.ServiceModel.Activation.WebHostServiceCloseFailed</span><span class="sxs-lookup"><span data-stu-id="1d3e8-102">System.ServiceModel.Activation.WebHostServiceCloseFailed</span></span>
<span data-ttu-id="1d3e8-103">Bir hizmet düzgün bir şekilde kapatıldı ve iptal gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="1d3e8-103">Occurs when a service cannot be closed gracefully and is aborted.</span></span>  
  
## <a name="description"></a><span data-ttu-id="1d3e8-104">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1d3e8-104">Description</span></span>  
 <span data-ttu-id="1d3e8-105">Bu hata kodu yalnızca günlük dosyasında görünür.</span><span class="sxs-lookup"><span data-stu-id="1d3e8-105">This error code only appears in the log file.</span></span> <span data-ttu-id="1d3e8-106">Hizmet durdurma zaten çağrıldıktan sonra kapatmak çalıştığınızda, genellikle bir programlama hatası gibi gösterir.</span><span class="sxs-lookup"><span data-stu-id="1d3e8-106">It usually indicates a programming error, for example, when you try to close a service after Abort has already been called.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="1d3e8-107">Sorun giderme</span><span class="sxs-lookup"><span data-stu-id="1d3e8-107">Troubleshooting</span></span>  
 <span data-ttu-id="1d3e8-108">Uygulama kaynak kodunu kontrol edin.</span><span class="sxs-lookup"><span data-stu-id="1d3e8-108">Check the application source code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1d3e8-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1d3e8-109">See also</span></span>
- [<span data-ttu-id="1d3e8-110">İzleme</span><span class="sxs-lookup"><span data-stu-id="1d3e8-110">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [<span data-ttu-id="1d3e8-111">Uygulamanızda Sorun Giderme için İzleme Kullanma</span><span class="sxs-lookup"><span data-stu-id="1d3e8-111">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="1d3e8-112">Yönetim ve Tanılama</span><span class="sxs-lookup"><span data-stu-id="1d3e8-112">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
