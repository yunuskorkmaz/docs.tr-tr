---
title: Güvenlik Doğrulaması ve Kimlik Doğrulaması Hatası/Saniye
ms.date: 03/30/2017
ms.assetid: 266c3bd3-2ffc-4471-94b7-3675443be1ac
ms.openlocfilehash: c64c121550043127db674fac6287a870449d789d
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96253134"
---
# <a name="security-validation-and-authentication-failures-per-second"></a><span data-ttu-id="4e828-102">Güvenlik Doğrulaması ve Kimlik Doğrulaması Hatası/Saniye</span><span class="sxs-lookup"><span data-stu-id="4e828-102">Security Validation and Authentication Failures Per Second</span></span>

<span data-ttu-id="4e828-103">Sayaç adı: saniye başına güvenlik doğrulaması ve kimlik doğrulama başarısızlığı.</span><span class="sxs-lookup"><span data-stu-id="4e828-103">Counter name: Security Validation and Authentication Failures Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="4e828-104">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4e828-104">Description</span></span>  

 <span data-ttu-id="4e828-105">Bu sayaç, "güvenlik çağrıları yetkilendirilmemiş" sayacı kapsamında olmayan bir güvenlik sorunu nedeniyle her ileti reddedildiğinde artırılır.</span><span class="sxs-lookup"><span data-stu-id="4e828-105">This counter is incremented whenever a message is rejected due to a security problem not covered by the "Security Calls Not Authorized" counter.</span></span> <span data-ttu-id="4e828-106">Bu tür sorunlar şunlardır:</span><span class="sxs-lookup"><span data-stu-id="4e828-106">Such problems include:</span></span>  
  
- <span data-ttu-id="4e828-107">İstemci belirteci iletiden okunamıyor.</span><span class="sxs-lookup"><span data-stu-id="4e828-107">Client token cannot be read from the message.</span></span>  
  
- <span data-ttu-id="4e828-108">İstemci belirteci kimlik doğrulaması başarısız oldu (örneğin, hatalı parola).</span><span class="sxs-lookup"><span data-stu-id="4e828-108">Client token has failed authentication (for example, bad password).</span></span>  
  
- <span data-ttu-id="4e828-109">İmza doğrulama başarısız oldu (örneğin, ileti değiştirilmiş).</span><span class="sxs-lookup"><span data-stu-id="4e828-109">Signature verification has failed (for example, the message has been tampered).</span></span>  
  
- <span data-ttu-id="4e828-110">İleti, bir yeniden yürütme saldırısında meydana gelebilen bir öncekinden yineleniyor.</span><span class="sxs-lookup"><span data-stu-id="4e828-110">The message is a duplicate from a previous one, which can happen during a replay attack.</span></span>  
  
- <span data-ttu-id="4e828-111">Şifre çözme hatası oluştu.</span><span class="sxs-lookup"><span data-stu-id="4e828-111">A decryption failure has occurred.</span></span>  
  
- <span data-ttu-id="4e828-112">İletide bazı gerekli öğeler (örneğin, eksik zaman damgası veya şifrelenmiş veri bloğu) eksik.</span><span class="sxs-lookup"><span data-stu-id="4e828-112">Some required elements (for example, missing timestamp or encrypted data block) are missing from the message.</span></span>  
  
- <span data-ttu-id="4e828-113">TLSNEGO/SPNEGO Handshake sırasında hatalar oluştu.</span><span class="sxs-lookup"><span data-stu-id="4e828-113">Errors have occurred during TLSNEGO/SPNEGO handshake.</span></span>  
  
 <span data-ttu-id="4e828-114">Bu sayaç, değeri aşağıdaki formül kullanılarak hesaplanan [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10))performans sayacı türüdür:</span><span class="sxs-lookup"><span data-stu-id="4e828-114">This counter is of performance counter type [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), whose value is calculated using the following formula:</span></span>  
  
 <span data-ttu-id="4e828-115">(N1-N0)/((D1-D0)/F)</span><span class="sxs-lookup"><span data-stu-id="4e828-115">(N1-N0)/((D1-D0)/F)</span></span>
