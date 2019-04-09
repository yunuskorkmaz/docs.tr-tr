---
title: System.ServiceModel.Activation.WebHostServiceCloseFailed
ms.date: 03/30/2017
ms.assetid: 3cab9856-a5cf-4f0e-a0cb-89425e368f8e
ms.openlocfilehash: afe84db3d4df8914ff1ed001b064439d581ead89
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59085401"
---
# <a name="systemservicemodelactivationwebhostserviceclosefailed"></a><span data-ttu-id="2934c-102">System.ServiceModel.Activation.WebHostServiceCloseFailed</span><span class="sxs-lookup"><span data-stu-id="2934c-102">System.ServiceModel.Activation.WebHostServiceCloseFailed</span></span>
<span data-ttu-id="2934c-103">Bir hizmet düzgün bir şekilde kapatıldı ve iptal gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="2934c-103">Occurs when a service cannot be closed gracefully and is aborted.</span></span>  
  
## <a name="description"></a><span data-ttu-id="2934c-104">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2934c-104">Description</span></span>  
 <span data-ttu-id="2934c-105">Bu hata kodu yalnızca günlük dosyasında görünür.</span><span class="sxs-lookup"><span data-stu-id="2934c-105">This error code only appears in the log file.</span></span> <span data-ttu-id="2934c-106">Hizmet durdurma zaten çağrıldıktan sonra kapatmak çalıştığınızda, genellikle bir programlama hatası gibi gösterir.</span><span class="sxs-lookup"><span data-stu-id="2934c-106">It usually indicates a programming error, for example, when you try to close a service after Abort has already been called.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="2934c-107">Sorun giderme</span><span class="sxs-lookup"><span data-stu-id="2934c-107">Troubleshooting</span></span>  
 <span data-ttu-id="2934c-108">Uygulama kaynak kodunu kontrol edin.</span><span class="sxs-lookup"><span data-stu-id="2934c-108">Check the application source code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2934c-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2934c-109">See also</span></span>

- [<span data-ttu-id="2934c-110">İzleme</span><span class="sxs-lookup"><span data-stu-id="2934c-110">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [<span data-ttu-id="2934c-111">Uygulamanızda Sorun Giderme için İzleme Kullanma</span><span class="sxs-lookup"><span data-stu-id="2934c-111">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="2934c-112">Yönetim ve Tanılama</span><span class="sxs-lookup"><span data-stu-id="2934c-112">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
