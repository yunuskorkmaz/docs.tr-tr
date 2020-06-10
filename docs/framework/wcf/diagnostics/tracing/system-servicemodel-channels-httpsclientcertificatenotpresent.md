---
title: System.ServiceModel.Channels.HttpsClientCertificateNotPresent
ms.date: 03/30/2017
ms.assetid: b13ef1b6-e340-401d-93ca-2710c3842205
ms.openlocfilehash: 3e3bedca7a46f147ee3d9e143cea7e57095c99d1
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84602050"
---
# <a name="systemservicemodelchannelshttpsclientcertificatenotpresent"></a><span data-ttu-id="2c7c8-102">System.ServiceModel.Channels.HttpsClientCertificateNotPresent</span><span class="sxs-lookup"><span data-stu-id="2c7c8-102">System.ServiceModel.Channels.HttpsClientCertificateNotPresent</span></span>
<span data-ttu-id="2c7c8-103">İstemci sertifikası gereklidir.</span><span class="sxs-lookup"><span data-stu-id="2c7c8-103">Client certificate is required.</span></span> <span data-ttu-id="2c7c8-104">İstekte hiçbir sertifika bulunamadı.</span><span class="sxs-lookup"><span data-stu-id="2c7c8-104">No certificate was found in the request.</span></span>  
  
## <a name="description"></a><span data-ttu-id="2c7c8-105">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2c7c8-105">Description</span></span>  
 <span data-ttu-id="2c7c8-106">Bu izleme, HTTPS dinleyicisinin bir istemci sertifikası ile ilişkilendirilmemiş bir HTTPS isteği aldığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="2c7c8-106">This trace indicates that the HTTPS listener received an HTTPS request that was not associated with a client certificate.</span></span> <span data-ttu-id="2c7c8-107">Dinleyici, tüm HTTPS isteklerinde istemci sertifikaları gerektirecek şekilde yapılandırıldığından, dinleyici istemcinin kimliğini doğrulayamadı.</span><span class="sxs-lookup"><span data-stu-id="2c7c8-107">Since the listener was configured to require client certificates on all HTTPS requests, the listener failed to validate the client’s authenticity.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2c7c8-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2c7c8-108">See also</span></span>

- [<span data-ttu-id="2c7c8-109">İzleme</span><span class="sxs-lookup"><span data-stu-id="2c7c8-109">Tracing</span></span>](index.md)
- [<span data-ttu-id="2c7c8-110">Uygulamanızda Sorun Giderme için İzleme Kullanma</span><span class="sxs-lookup"><span data-stu-id="2c7c8-110">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="2c7c8-111">Yönetim ve tanılama</span><span class="sxs-lookup"><span data-stu-id="2c7c8-111">Administration and Diagnostics</span></span>](../index.md)
