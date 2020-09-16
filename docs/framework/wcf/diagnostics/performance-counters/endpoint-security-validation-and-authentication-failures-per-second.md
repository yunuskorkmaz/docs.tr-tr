---
title: 'Uç Noktası: Saniyede Güvenlik Doğrulama ve Kimlik Doğrulama Hatası'
ms.date: 03/30/2017
ms.assetid: 89a70b90-d7e4-4b03-9b84-4dc88ce3d605
ms.openlocfilehash: 8573c35f16d03e2f86310c054703c25a3175200c
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90541506"
---
# <a name="endpoint-security-validation-and-authentication-failures-per-second"></a><span data-ttu-id="08230-102">Uç Noktası: Saniyede Güvenlik Doğrulama ve Kimlik Doğrulama Hatası</span><span class="sxs-lookup"><span data-stu-id="08230-102">Endpoint: Security Validation and Authentication Failures Per Second</span></span>
<span data-ttu-id="08230-103">Sayaç adı: güvenlik doğrulaması ve saniye başına kimlik doğrulama başarısızlığı</span><span class="sxs-lookup"><span data-stu-id="08230-103">Counter name: Security Validation and Authentication Failures Per Second</span></span>  
  
## <a name="description"></a><span data-ttu-id="08230-104">Description</span><span class="sxs-lookup"><span data-stu-id="08230-104">Description</span></span>  
 <span data-ttu-id="08230-105">Bu sayaç, "güvenlik çağrıları yetkilendirilmemiş" sayacı kapsamında olmayan bir güvenlik sorunu nedeniyle her ileti reddedildiğinde artırılır.</span><span class="sxs-lookup"><span data-stu-id="08230-105">This counter is incremented whenever a message is rejected due to a security problem not covered by the "Security Calls Not Authorized" counter.</span></span> <span data-ttu-id="08230-106">Bu tür sorunlar şunlardır:</span><span class="sxs-lookup"><span data-stu-id="08230-106">Such problems include:</span></span>  
  
- <span data-ttu-id="08230-107">İstemci belirteci iletiden okunamıyor.</span><span class="sxs-lookup"><span data-stu-id="08230-107">Client token cannot be read from the message.</span></span>  
  
- <span data-ttu-id="08230-108">İstemci belirteci kimlik doğrulaması başarısız oldu (örneğin, hatalı parola).</span><span class="sxs-lookup"><span data-stu-id="08230-108">Client token has failed authentication (for example, bad password).</span></span>  
  
- <span data-ttu-id="08230-109">İmza doğrulama başarısız oldu (örneğin, ileti değiştirilmiş).</span><span class="sxs-lookup"><span data-stu-id="08230-109">Signature verification has failed (for example, the message has been tampered).</span></span>  
  
- <span data-ttu-id="08230-110">İleti, bir yeniden yürütme saldırısında meydana gelebilen bir öncekinden yineleniyor.</span><span class="sxs-lookup"><span data-stu-id="08230-110">The message is a duplicate from a previous one, which can happen during a replay attack.</span></span>  
  
- <span data-ttu-id="08230-111">Şifre çözme hatası oluştu.</span><span class="sxs-lookup"><span data-stu-id="08230-111">A decryption failure has occurred.</span></span>  
  
- <span data-ttu-id="08230-112">İletide bazı gerekli öğeler (örneğin, eksik zaman damgası veya şifrelenmiş veri bloğu) eksik.</span><span class="sxs-lookup"><span data-stu-id="08230-112">Some required elements (for example, missing timestamp or encrypted data block) are missing from the message.</span></span>  
  
- <span data-ttu-id="08230-113">TLSNEGO/SPNEGO Handshake sırasında hatalar oluştu.</span><span class="sxs-lookup"><span data-stu-id="08230-113">Errors have occurred during TLSNEGO/SPNEGO handshake.</span></span>  
  
 <span data-ttu-id="08230-114">Bu sayaç, değeri aşağıdaki formül kullanılarak hesaplanan [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10))performans sayacı türüdür:</span><span class="sxs-lookup"><span data-stu-id="08230-114">This counter is of performance counter type [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), whose value is calculated using the following formula:</span></span>  
  
 <span data-ttu-id="08230-115">(N1-N0)/((D1-D0)/F)</span><span class="sxs-lookup"><span data-stu-id="08230-115">(N1-N0)/((D1-D0)/F)</span></span>
