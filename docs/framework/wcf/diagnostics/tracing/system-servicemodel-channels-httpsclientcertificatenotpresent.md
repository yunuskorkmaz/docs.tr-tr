---
title: System.ServiceModel.Channels.HttpsClientCertificateNotPresent
ms.date: 03/30/2017
ms.assetid: b13ef1b6-e340-401d-93ca-2710c3842205
ms.openlocfilehash: 15ae13563cfcfb3765559cafb2d31bd6482df7b2
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59201188"
---
# <a name="systemservicemodelchannelshttpsclientcertificatenotpresent"></a><span data-ttu-id="16615-102">System.ServiceModel.Channels.HttpsClientCertificateNotPresent</span><span class="sxs-lookup"><span data-stu-id="16615-102">System.ServiceModel.Channels.HttpsClientCertificateNotPresent</span></span>
<span data-ttu-id="16615-103">İstemci sertifikası gereklidir.</span><span class="sxs-lookup"><span data-stu-id="16615-103">Client certificate is required.</span></span> <span data-ttu-id="16615-104">Sertifika, istekte bulundu.</span><span class="sxs-lookup"><span data-stu-id="16615-104">No certificate was found in the request.</span></span>  
  
## <a name="description"></a><span data-ttu-id="16615-105">Açıklama</span><span class="sxs-lookup"><span data-stu-id="16615-105">Description</span></span>  
 <span data-ttu-id="16615-106">Bu izleme, HTTPS dinleyicisi bir istemci sertifikası ile ilişkilendirilmemiş bir HTTPS isteği aldığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="16615-106">This trace indicates that the HTTPS listener received an HTTPS request that was not associated with a client certificate.</span></span> <span data-ttu-id="16615-107">Dinleyici tüm HTTPS isteklerinde istemci sertifikaları gerektirmek için yapılandırılıldıktan sonra dinleyici istemcinin orijinallik sertifikası doğrulanamadı.</span><span class="sxs-lookup"><span data-stu-id="16615-107">Since the listener was configured to require client certificates on all HTTPS requests, the listener failed to validate the client’s authenticity.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="16615-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="16615-108">See also</span></span>

- [<span data-ttu-id="16615-109">İzleme</span><span class="sxs-lookup"><span data-stu-id="16615-109">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [<span data-ttu-id="16615-110">Uygulamanızda Sorun Giderme için İzleme Kullanma</span><span class="sxs-lookup"><span data-stu-id="16615-110">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="16615-111">Yönetim ve Tanılama</span><span class="sxs-lookup"><span data-stu-id="16615-111">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
