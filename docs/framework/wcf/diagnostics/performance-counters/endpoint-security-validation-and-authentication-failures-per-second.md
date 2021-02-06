---
description: 'Şu konuda daha fazla bilgi edinin: uç nokta: güvenlik doğrulama ve saniyede kimlik doğrulama başarısızlığı'
title: 'Uç Noktası: Saniyede Güvenlik Doğrulama ve Kimlik Doğrulama Hatası'
ms.date: 03/30/2017
ms.assetid: 89a70b90-d7e4-4b03-9b84-4dc88ce3d605
ms.openlocfilehash: aa5ccc4049dc81a7c2d545cfc70e9078ac72d87a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99655441"
---
# <a name="endpoint-security-validation-and-authentication-failures-per-second"></a><span data-ttu-id="73140-103">Uç Noktası: Saniyede Güvenlik Doğrulama ve Kimlik Doğrulama Hatası</span><span class="sxs-lookup"><span data-stu-id="73140-103">Endpoint: Security Validation and Authentication Failures Per Second</span></span>

<span data-ttu-id="73140-104">Sayaç adı: güvenlik doğrulaması ve saniye başına kimlik doğrulama başarısızlığı</span><span class="sxs-lookup"><span data-stu-id="73140-104">Counter name: Security Validation and Authentication Failures Per Second</span></span>  
  
## <a name="description"></a><span data-ttu-id="73140-105">Description</span><span class="sxs-lookup"><span data-stu-id="73140-105">Description</span></span>  

 <span data-ttu-id="73140-106">Bu sayaç, "güvenlik çağrıları yetkilendirilmemiş" sayacı kapsamında olmayan bir güvenlik sorunu nedeniyle her ileti reddedildiğinde artırılır.</span><span class="sxs-lookup"><span data-stu-id="73140-106">This counter is incremented whenever a message is rejected due to a security problem not covered by the "Security Calls Not Authorized" counter.</span></span> <span data-ttu-id="73140-107">Bu tür sorunlar şunlardır:</span><span class="sxs-lookup"><span data-stu-id="73140-107">Such problems include:</span></span>  
  
- <span data-ttu-id="73140-108">İstemci belirteci iletiden okunamıyor.</span><span class="sxs-lookup"><span data-stu-id="73140-108">Client token cannot be read from the message.</span></span>  
  
- <span data-ttu-id="73140-109">İstemci belirteci kimlik doğrulaması başarısız oldu (örneğin, hatalı parola).</span><span class="sxs-lookup"><span data-stu-id="73140-109">Client token has failed authentication (for example, bad password).</span></span>  
  
- <span data-ttu-id="73140-110">İmza doğrulama başarısız oldu (örneğin, ileti değiştirilmiş).</span><span class="sxs-lookup"><span data-stu-id="73140-110">Signature verification has failed (for example, the message has been tampered).</span></span>  
  
- <span data-ttu-id="73140-111">İleti, bir yeniden yürütme saldırısında meydana gelebilen bir öncekinden yineleniyor.</span><span class="sxs-lookup"><span data-stu-id="73140-111">The message is a duplicate from a previous one, which can happen during a replay attack.</span></span>  
  
- <span data-ttu-id="73140-112">Şifre çözme hatası oluştu.</span><span class="sxs-lookup"><span data-stu-id="73140-112">A decryption failure has occurred.</span></span>  
  
- <span data-ttu-id="73140-113">İletide bazı gerekli öğeler (örneğin, eksik zaman damgası veya şifrelenmiş veri bloğu) eksik.</span><span class="sxs-lookup"><span data-stu-id="73140-113">Some required elements (for example, missing timestamp or encrypted data block) are missing from the message.</span></span>  
  
- <span data-ttu-id="73140-114">TLSNEGO/SPNEGO Handshake sırasında hatalar oluştu.</span><span class="sxs-lookup"><span data-stu-id="73140-114">Errors have occurred during TLSNEGO/SPNEGO handshake.</span></span>  
  
 <span data-ttu-id="73140-115">Bu sayaç, değeri aşağıdaki formül kullanılarak hesaplanan [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10))performans sayacı türüdür:</span><span class="sxs-lookup"><span data-stu-id="73140-115">This counter is of performance counter type [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), whose value is calculated using the following formula:</span></span>  
  
 <span data-ttu-id="73140-116">(N1-N0)/((D1-D0)/F)</span><span class="sxs-lookup"><span data-stu-id="73140-116">(N1-N0)/((D1-D0)/F)</span></span>
