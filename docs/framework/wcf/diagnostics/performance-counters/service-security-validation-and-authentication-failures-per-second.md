---
title: 'Hizmet: Saniyede Güvenlik Doğrulama ve Kimlik Doğrulama Hatası'
ms.date: 03/30/2017
ms.assetid: 4af18009-e778-490b-9ba6-e76485285830
ms.openlocfilehash: f66e6b90622cf181229938bc4fd877a98cd23a48
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96236890"
---
# <a name="service-security-validation-and-authentication-failures-per-second"></a><span data-ttu-id="9759b-102">Hizmet: Saniyede Güvenlik Doğrulama ve Kimlik Doğrulama Hatası</span><span class="sxs-lookup"><span data-stu-id="9759b-102">Service: Security Validation and Authentication Failures Per Second</span></span>

<span data-ttu-id="9759b-103">Sayaç adı: saniye başına güvenlik doğrulaması ve kimlik doğrulama başarısızlığı.</span><span class="sxs-lookup"><span data-stu-id="9759b-103">Counter name: Security Validation and Authentication Failures Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="9759b-104">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9759b-104">Description</span></span>  

 <span data-ttu-id="9759b-105">Bu sayaç, "güvenlik çağrıları yetkilendirilmemiş" sayacı kapsamında olmayan bir güvenlik sorunu nedeniyle her ileti reddedildiğinde artırılır.</span><span class="sxs-lookup"><span data-stu-id="9759b-105">This counter is incremented whenever a message is rejected due to a security problem not covered by the "Security Calls Not Authorized" counter.</span></span> <span data-ttu-id="9759b-106">Bu tür sorunlar şunlardır:</span><span class="sxs-lookup"><span data-stu-id="9759b-106">Such problems include:</span></span>  
  
- <span data-ttu-id="9759b-107">İstemci belirteci iletiden okunamıyor.</span><span class="sxs-lookup"><span data-stu-id="9759b-107">Client token cannot be read from the message.</span></span>  
  
- <span data-ttu-id="9759b-108">İstemci belirteci kimlik doğrulaması başarısız oldu (örneğin, hatalı parola).</span><span class="sxs-lookup"><span data-stu-id="9759b-108">Client token has failed authentication (for example, bad password).</span></span>  
  
- <span data-ttu-id="9759b-109">İmza doğrulama başarısız oldu (örneğin, ileti değiştirilmiş).</span><span class="sxs-lookup"><span data-stu-id="9759b-109">Signature verification has failed (for example, the message has been tampered).</span></span>  
  
- <span data-ttu-id="9759b-110">İleti, bir yeniden yürütme saldırısında meydana gelebilen bir öncekinden yineleniyor.</span><span class="sxs-lookup"><span data-stu-id="9759b-110">The message is a duplicate from a previous one, which can happen during a replay attack.</span></span>  
  
- <span data-ttu-id="9759b-111">Şifre çözme hatası oluştu.</span><span class="sxs-lookup"><span data-stu-id="9759b-111">A decryption failure has occurred.</span></span>  
  
- <span data-ttu-id="9759b-112">İletide bazı gerekli öğeler (örneğin, eksik zaman damgası veya şifrelenmiş veri bloğu) eksik.</span><span class="sxs-lookup"><span data-stu-id="9759b-112">Some required elements (for example, missing timestamp or encrypted data block) are missing from the message.</span></span>  
  
- <span data-ttu-id="9759b-113">TLSNEGO/SPNEGO Handshake sırasında hatalar oluştu.</span><span class="sxs-lookup"><span data-stu-id="9759b-113">Errors have occurred during TLSNEGO/SPNEGO handshake.</span></span>  
  
 <span data-ttu-id="9759b-114">Bu sayaç, değeri aşağıdaki formül kullanılarak hesaplanmış olan [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10))performans sayacı türüdür.</span><span class="sxs-lookup"><span data-stu-id="9759b-114">This counter is of performance counter type [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), whose value is calculated using the following formula,</span></span>  
  
 <span data-ttu-id="9759b-115">(N 1-N 0)/((D 1-D 0)/F)</span><span class="sxs-lookup"><span data-stu-id="9759b-115">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
