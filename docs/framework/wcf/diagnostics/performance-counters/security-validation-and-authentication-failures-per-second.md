---
description: 'Daha fazla bilgi edinin: güvenlik doğrulaması ve saniye başına kimlik doğrulama başarısızlığı'
title: Güvenlik Doğrulaması ve Kimlik Doğrulaması Hatası/Saniye
ms.date: 03/30/2017
ms.assetid: 266c3bd3-2ffc-4471-94b7-3675443be1ac
ms.openlocfilehash: 77c11e8f47b5d91ea38030841f6ca33ba0f0795c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99803405"
---
# <a name="security-validation-and-authentication-failures-per-second"></a><span data-ttu-id="3f3f0-103">Güvenlik Doğrulaması ve Kimlik Doğrulaması Hatası/Saniye</span><span class="sxs-lookup"><span data-stu-id="3f3f0-103">Security Validation and Authentication Failures Per Second</span></span>

<span data-ttu-id="3f3f0-104">Sayaç adı: saniye başına güvenlik doğrulaması ve kimlik doğrulama başarısızlığı.</span><span class="sxs-lookup"><span data-stu-id="3f3f0-104">Counter name: Security Validation and Authentication Failures Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="3f3f0-105">Description</span><span class="sxs-lookup"><span data-stu-id="3f3f0-105">Description</span></span>  

 <span data-ttu-id="3f3f0-106">Bu sayaç, "güvenlik çağrıları yetkilendirilmemiş" sayacı kapsamında olmayan bir güvenlik sorunu nedeniyle her ileti reddedildiğinde artırılır.</span><span class="sxs-lookup"><span data-stu-id="3f3f0-106">This counter is incremented whenever a message is rejected due to a security problem not covered by the "Security Calls Not Authorized" counter.</span></span> <span data-ttu-id="3f3f0-107">Bu tür sorunlar şunlardır:</span><span class="sxs-lookup"><span data-stu-id="3f3f0-107">Such problems include:</span></span>  
  
- <span data-ttu-id="3f3f0-108">İstemci belirteci iletiden okunamıyor.</span><span class="sxs-lookup"><span data-stu-id="3f3f0-108">Client token cannot be read from the message.</span></span>  
  
- <span data-ttu-id="3f3f0-109">İstemci belirteci kimlik doğrulaması başarısız oldu (örneğin, hatalı parola).</span><span class="sxs-lookup"><span data-stu-id="3f3f0-109">Client token has failed authentication (for example, bad password).</span></span>  
  
- <span data-ttu-id="3f3f0-110">İmza doğrulama başarısız oldu (örneğin, ileti değiştirilmiş).</span><span class="sxs-lookup"><span data-stu-id="3f3f0-110">Signature verification has failed (for example, the message has been tampered).</span></span>  
  
- <span data-ttu-id="3f3f0-111">İleti, bir yeniden yürütme saldırısında meydana gelebilen bir öncekinden yineleniyor.</span><span class="sxs-lookup"><span data-stu-id="3f3f0-111">The message is a duplicate from a previous one, which can happen during a replay attack.</span></span>  
  
- <span data-ttu-id="3f3f0-112">Şifre çözme hatası oluştu.</span><span class="sxs-lookup"><span data-stu-id="3f3f0-112">A decryption failure has occurred.</span></span>  
  
- <span data-ttu-id="3f3f0-113">İletide bazı gerekli öğeler (örneğin, eksik zaman damgası veya şifrelenmiş veri bloğu) eksik.</span><span class="sxs-lookup"><span data-stu-id="3f3f0-113">Some required elements (for example, missing timestamp or encrypted data block) are missing from the message.</span></span>  
  
- <span data-ttu-id="3f3f0-114">TLSNEGO/SPNEGO Handshake sırasında hatalar oluştu.</span><span class="sxs-lookup"><span data-stu-id="3f3f0-114">Errors have occurred during TLSNEGO/SPNEGO handshake.</span></span>  
  
 <span data-ttu-id="3f3f0-115">Bu sayaç, değeri aşağıdaki formül kullanılarak hesaplanan [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10))performans sayacı türüdür:</span><span class="sxs-lookup"><span data-stu-id="3f3f0-115">This counter is of performance counter type [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), whose value is calculated using the following formula:</span></span>  
  
 <span data-ttu-id="3f3f0-116">(N1-N0)/((D1-D0)/F)</span><span class="sxs-lookup"><span data-stu-id="3f3f0-116">(N1-N0)/((D1-D0)/F)</span></span>
