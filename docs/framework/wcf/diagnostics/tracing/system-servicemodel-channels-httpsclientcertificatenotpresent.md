---
title: System.ServiceModel.Channels.HttpsClientCertificateNotPresent
ms.date: 03/30/2017
ms.assetid: b13ef1b6-e340-401d-93ca-2710c3842205
ms.openlocfilehash: 9ec25138130311f8cdd9af8fb32a3e80fb33ed68
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96258094"
---
# <a name="systemservicemodelchannelshttpsclientcertificatenotpresent"></a><span data-ttu-id="bd09f-102">System.ServiceModel.Channels.HttpsClientCertificateNotPresent</span><span class="sxs-lookup"><span data-stu-id="bd09f-102">System.ServiceModel.Channels.HttpsClientCertificateNotPresent</span></span>

<span data-ttu-id="bd09f-103">İstemci sertifikası gereklidir.</span><span class="sxs-lookup"><span data-stu-id="bd09f-103">Client certificate is required.</span></span> <span data-ttu-id="bd09f-104">İstekte hiçbir sertifika bulunamadı.</span><span class="sxs-lookup"><span data-stu-id="bd09f-104">No certificate was found in the request.</span></span>  
  
## <a name="description"></a><span data-ttu-id="bd09f-105">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bd09f-105">Description</span></span>  

 <span data-ttu-id="bd09f-106">Bu izleme, HTTPS dinleyicisinin bir istemci sertifikası ile ilişkilendirilmemiş bir HTTPS isteği aldığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="bd09f-106">This trace indicates that the HTTPS listener received an HTTPS request that was not associated with a client certificate.</span></span> <span data-ttu-id="bd09f-107">Dinleyici, tüm HTTPS isteklerinde istemci sertifikaları gerektirecek şekilde yapılandırıldığından, dinleyici istemcinin kimliğini doğrulayamadı.</span><span class="sxs-lookup"><span data-stu-id="bd09f-107">Since the listener was configured to require client certificates on all HTTPS requests, the listener failed to validate the client’s authenticity.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bd09f-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bd09f-108">See also</span></span>

- [<span data-ttu-id="bd09f-109">İzleme</span><span class="sxs-lookup"><span data-stu-id="bd09f-109">Tracing</span></span>](index.md)
- [<span data-ttu-id="bd09f-110">Uygulamanızda Sorun Giderme için İzleme Kullanma</span><span class="sxs-lookup"><span data-stu-id="bd09f-110">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="bd09f-111">Yönetim ve tanılama</span><span class="sxs-lookup"><span data-stu-id="bd09f-111">Administration and Diagnostics</span></span>](../index.md)
