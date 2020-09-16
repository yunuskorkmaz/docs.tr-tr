---
title: Güvenlik Doğrulaması ve Kimlik Doğrulaması Hatası/Saniye
ms.date: 03/30/2017
ms.assetid: 266c3bd3-2ffc-4471-94b7-3675443be1ac
ms.openlocfilehash: 7d680e9a5b03943fdec212c509b6d80a2d60246c
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90559141"
---
# <a name="security-validation-and-authentication-failures-per-second"></a><span data-ttu-id="a7a48-102">Güvenlik Doğrulaması ve Kimlik Doğrulaması Hatası/Saniye</span><span class="sxs-lookup"><span data-stu-id="a7a48-102">Security Validation and Authentication Failures Per Second</span></span>
<span data-ttu-id="a7a48-103">Sayaç adı: saniye başına güvenlik doğrulaması ve kimlik doğrulama başarısızlığı.</span><span class="sxs-lookup"><span data-stu-id="a7a48-103">Counter name: Security Validation and Authentication Failures Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="a7a48-104">Description</span><span class="sxs-lookup"><span data-stu-id="a7a48-104">Description</span></span>  
 <span data-ttu-id="a7a48-105">Bu sayaç, "güvenlik çağrıları yetkilendirilmemiş" sayacı kapsamında olmayan bir güvenlik sorunu nedeniyle her ileti reddedildiğinde artırılır.</span><span class="sxs-lookup"><span data-stu-id="a7a48-105">This counter is incremented whenever a message is rejected due to a security problem not covered by the "Security Calls Not Authorized" counter.</span></span> <span data-ttu-id="a7a48-106">Bu tür sorunlar şunlardır:</span><span class="sxs-lookup"><span data-stu-id="a7a48-106">Such problems include:</span></span>  
  
- <span data-ttu-id="a7a48-107">İstemci belirteci iletiden okunamıyor.</span><span class="sxs-lookup"><span data-stu-id="a7a48-107">Client token cannot be read from the message.</span></span>  
  
- <span data-ttu-id="a7a48-108">İstemci belirteci kimlik doğrulaması başarısız oldu (örneğin, hatalı parola).</span><span class="sxs-lookup"><span data-stu-id="a7a48-108">Client token has failed authentication (for example, bad password).</span></span>  
  
- <span data-ttu-id="a7a48-109">İmza doğrulama başarısız oldu (örneğin, ileti değiştirilmiş).</span><span class="sxs-lookup"><span data-stu-id="a7a48-109">Signature verification has failed (for example, the message has been tampered).</span></span>  
  
- <span data-ttu-id="a7a48-110">İleti, bir yeniden yürütme saldırısında meydana gelebilen bir öncekinden yineleniyor.</span><span class="sxs-lookup"><span data-stu-id="a7a48-110">The message is a duplicate from a previous one, which can happen during a replay attack.</span></span>  
  
- <span data-ttu-id="a7a48-111">Şifre çözme hatası oluştu.</span><span class="sxs-lookup"><span data-stu-id="a7a48-111">A decryption failure has occurred.</span></span>  
  
- <span data-ttu-id="a7a48-112">İletide bazı gerekli öğeler (örneğin, eksik zaman damgası veya şifrelenmiş veri bloğu) eksik.</span><span class="sxs-lookup"><span data-stu-id="a7a48-112">Some required elements (for example, missing timestamp or encrypted data block) are missing from the message.</span></span>  
  
- <span data-ttu-id="a7a48-113">TLSNEGO/SPNEGO Handshake sırasında hatalar oluştu.</span><span class="sxs-lookup"><span data-stu-id="a7a48-113">Errors have occurred during TLSNEGO/SPNEGO handshake.</span></span>  
  
 <span data-ttu-id="a7a48-114">Bu sayaç, değeri aşağıdaki formül kullanılarak hesaplanan [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10))performans sayacı türüdür:</span><span class="sxs-lookup"><span data-stu-id="a7a48-114">This counter is of performance counter type [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), whose value is calculated using the following formula:</span></span>  
  
 <span data-ttu-id="a7a48-115">(N1-N0)/((D1-D0)/F)</span><span class="sxs-lookup"><span data-stu-id="a7a48-115">(N1-N0)/((D1-D0)/F)</span></span>
