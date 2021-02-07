---
description: 'Şu konuda daha fazla bilgi edinin: hizmet: güvenlik doğrulama ve kimlik doğrulama başarısızlığı/saniye'
title: 'Hizmet: Saniyede Güvenlik Doğrulama ve Kimlik Doğrulama Hatası'
ms.date: 03/30/2017
ms.assetid: 4af18009-e778-490b-9ba6-e76485285830
ms.openlocfilehash: 8c0baedab3335031ed1737e0e4cecff7febc2944
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99759529"
---
# <a name="service-security-validation-and-authentication-failures-per-second"></a><span data-ttu-id="99b62-103">Hizmet: Saniyede Güvenlik Doğrulama ve Kimlik Doğrulama Hatası</span><span class="sxs-lookup"><span data-stu-id="99b62-103">Service: Security Validation and Authentication Failures Per Second</span></span>

<span data-ttu-id="99b62-104">Sayaç adı: saniye başına güvenlik doğrulaması ve kimlik doğrulama başarısızlığı.</span><span class="sxs-lookup"><span data-stu-id="99b62-104">Counter name: Security Validation and Authentication Failures Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="99b62-105">Description</span><span class="sxs-lookup"><span data-stu-id="99b62-105">Description</span></span>  

 <span data-ttu-id="99b62-106">Bu sayaç, "güvenlik çağrıları yetkilendirilmemiş" sayacı kapsamında olmayan bir güvenlik sorunu nedeniyle her ileti reddedildiğinde artırılır.</span><span class="sxs-lookup"><span data-stu-id="99b62-106">This counter is incremented whenever a message is rejected due to a security problem not covered by the "Security Calls Not Authorized" counter.</span></span> <span data-ttu-id="99b62-107">Bu tür sorunlar şunlardır:</span><span class="sxs-lookup"><span data-stu-id="99b62-107">Such problems include:</span></span>  
  
- <span data-ttu-id="99b62-108">İstemci belirteci iletiden okunamıyor.</span><span class="sxs-lookup"><span data-stu-id="99b62-108">Client token cannot be read from the message.</span></span>  
  
- <span data-ttu-id="99b62-109">İstemci belirteci kimlik doğrulaması başarısız oldu (örneğin, hatalı parola).</span><span class="sxs-lookup"><span data-stu-id="99b62-109">Client token has failed authentication (for example, bad password).</span></span>  
  
- <span data-ttu-id="99b62-110">İmza doğrulama başarısız oldu (örneğin, ileti değiştirilmiş).</span><span class="sxs-lookup"><span data-stu-id="99b62-110">Signature verification has failed (for example, the message has been tampered).</span></span>  
  
- <span data-ttu-id="99b62-111">İleti, bir yeniden yürütme saldırısında meydana gelebilen bir öncekinden yineleniyor.</span><span class="sxs-lookup"><span data-stu-id="99b62-111">The message is a duplicate from a previous one, which can happen during a replay attack.</span></span>  
  
- <span data-ttu-id="99b62-112">Şifre çözme hatası oluştu.</span><span class="sxs-lookup"><span data-stu-id="99b62-112">A decryption failure has occurred.</span></span>  
  
- <span data-ttu-id="99b62-113">İletide bazı gerekli öğeler (örneğin, eksik zaman damgası veya şifrelenmiş veri bloğu) eksik.</span><span class="sxs-lookup"><span data-stu-id="99b62-113">Some required elements (for example, missing timestamp or encrypted data block) are missing from the message.</span></span>  
  
- <span data-ttu-id="99b62-114">TLSNEGO/SPNEGO Handshake sırasında hatalar oluştu.</span><span class="sxs-lookup"><span data-stu-id="99b62-114">Errors have occurred during TLSNEGO/SPNEGO handshake.</span></span>  
  
 <span data-ttu-id="99b62-115">Bu sayaç, değeri aşağıdaki formül kullanılarak hesaplanmış olan [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10))performans sayacı türüdür.</span><span class="sxs-lookup"><span data-stu-id="99b62-115">This counter is of performance counter type [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), whose value is calculated using the following formula,</span></span>  
  
 <span data-ttu-id="99b62-116">(N 1-N 0)/((D 1-D 0)/F)</span><span class="sxs-lookup"><span data-stu-id="99b62-116">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
