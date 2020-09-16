---
title: 'Hizmet: Saniyede Güvenlik Doğrulama ve Kimlik Doğrulama Hatası'
ms.date: 03/30/2017
ms.assetid: 4af18009-e778-490b-9ba6-e76485285830
ms.openlocfilehash: f6dbf7f6da208bde3a9a380d50fd6caf68576f25
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90535917"
---
# <a name="service-security-validation-and-authentication-failures-per-second"></a><span data-ttu-id="42cfb-102">Hizmet: Saniyede Güvenlik Doğrulama ve Kimlik Doğrulama Hatası</span><span class="sxs-lookup"><span data-stu-id="42cfb-102">Service: Security Validation and Authentication Failures Per Second</span></span>
<span data-ttu-id="42cfb-103">Sayaç adı: saniye başına güvenlik doğrulaması ve kimlik doğrulama başarısızlığı.</span><span class="sxs-lookup"><span data-stu-id="42cfb-103">Counter name: Security Validation and Authentication Failures Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="42cfb-104">Description</span><span class="sxs-lookup"><span data-stu-id="42cfb-104">Description</span></span>  
 <span data-ttu-id="42cfb-105">Bu sayaç, "güvenlik çağrıları yetkilendirilmemiş" sayacı kapsamında olmayan bir güvenlik sorunu nedeniyle her ileti reddedildiğinde artırılır.</span><span class="sxs-lookup"><span data-stu-id="42cfb-105">This counter is incremented whenever a message is rejected due to a security problem not covered by the "Security Calls Not Authorized" counter.</span></span> <span data-ttu-id="42cfb-106">Bu tür sorunlar şunlardır:</span><span class="sxs-lookup"><span data-stu-id="42cfb-106">Such problems include:</span></span>  
  
- <span data-ttu-id="42cfb-107">İstemci belirteci iletiden okunamıyor.</span><span class="sxs-lookup"><span data-stu-id="42cfb-107">Client token cannot be read from the message.</span></span>  
  
- <span data-ttu-id="42cfb-108">İstemci belirteci kimlik doğrulaması başarısız oldu (örneğin, hatalı parola).</span><span class="sxs-lookup"><span data-stu-id="42cfb-108">Client token has failed authentication (for example, bad password).</span></span>  
  
- <span data-ttu-id="42cfb-109">İmza doğrulama başarısız oldu (örneğin, ileti değiştirilmiş).</span><span class="sxs-lookup"><span data-stu-id="42cfb-109">Signature verification has failed (for example, the message has been tampered).</span></span>  
  
- <span data-ttu-id="42cfb-110">İleti, bir yeniden yürütme saldırısında meydana gelebilen bir öncekinden yineleniyor.</span><span class="sxs-lookup"><span data-stu-id="42cfb-110">The message is a duplicate from a previous one, which can happen during a replay attack.</span></span>  
  
- <span data-ttu-id="42cfb-111">Şifre çözme hatası oluştu.</span><span class="sxs-lookup"><span data-stu-id="42cfb-111">A decryption failure has occurred.</span></span>  
  
- <span data-ttu-id="42cfb-112">İletide bazı gerekli öğeler (örneğin, eksik zaman damgası veya şifrelenmiş veri bloğu) eksik.</span><span class="sxs-lookup"><span data-stu-id="42cfb-112">Some required elements (for example, missing timestamp or encrypted data block) are missing from the message.</span></span>  
  
- <span data-ttu-id="42cfb-113">TLSNEGO/SPNEGO Handshake sırasında hatalar oluştu.</span><span class="sxs-lookup"><span data-stu-id="42cfb-113">Errors have occurred during TLSNEGO/SPNEGO handshake.</span></span>  
  
 <span data-ttu-id="42cfb-114">Bu sayaç, değeri aşağıdaki formül kullanılarak hesaplanmış olan [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10))performans sayacı türüdür.</span><span class="sxs-lookup"><span data-stu-id="42cfb-114">This counter is of performance counter type [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), whose value is calculated using the following formula,</span></span>  
  
 <span data-ttu-id="42cfb-115">(N 1-N 0)/((D 1-D 0)/F)</span><span class="sxs-lookup"><span data-stu-id="42cfb-115">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
