---
description: 'Daha fazla bilgi edinin: uç nokta: güvenlik doğrulama ve kimlik doğrulama sorunları'
title: 'Uç Noktası: Güvenlik Doğrulaması ve Kimlik Doğrulaması Hataları'
ms.date: 03/30/2017
ms.assetid: 5bad60aa-6084-4c7b-aefd-9b581f04382e
ms.openlocfilehash: 9131eebcf85032c591ebf7f65e2b0e5f67ec60df
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99655430"
---
# <a name="endpoint-security-validation-and-authentication-failures"></a><span data-ttu-id="5a56d-103">Uç Noktası: Güvenlik Doğrulaması ve Kimlik Doğrulaması Hataları</span><span class="sxs-lookup"><span data-stu-id="5a56d-103">Endpoint: Security Validation and Authentication Failures</span></span>

<span data-ttu-id="5a56d-104">Sayaç adı: güvenlik doğrulama ve kimlik doğrulama sorunları</span><span class="sxs-lookup"><span data-stu-id="5a56d-104">Counter name: Security Validation and Authentication Failures</span></span>  
  
## <a name="description"></a><span data-ttu-id="5a56d-105">Description</span><span class="sxs-lookup"><span data-stu-id="5a56d-105">Description</span></span>  

 <span data-ttu-id="5a56d-106">Bu sayaç, "güvenlik çağrıları yetkilendirilmemiş" sayacı kapsamında olmayan bir güvenlik sorunu nedeniyle her ileti reddedildiğinde artırılır.</span><span class="sxs-lookup"><span data-stu-id="5a56d-106">This counter is incremented whenever a message is rejected due to a security problem not covered by the "Security Calls Not Authorized" counter.</span></span> <span data-ttu-id="5a56d-107">Bu tür sorunlar şunlardır:</span><span class="sxs-lookup"><span data-stu-id="5a56d-107">Such problems include:</span></span>  
  
- <span data-ttu-id="5a56d-108">İstemci belirteci iletiden okunamıyor.</span><span class="sxs-lookup"><span data-stu-id="5a56d-108">Client token cannot be read from the message.</span></span>  
  
- <span data-ttu-id="5a56d-109">İstemci belirteci kimlik doğrulaması başarısız oldu (hatalı parola).</span><span class="sxs-lookup"><span data-stu-id="5a56d-109">Client token has failed authentication (bad password).</span></span>  
  
- <span data-ttu-id="5a56d-110">İmza doğrulama başarısız oldu (ileti değiştirilmiş).</span><span class="sxs-lookup"><span data-stu-id="5a56d-110">Signature verification has failed (the message has been tampered).</span></span>  
  
- <span data-ttu-id="5a56d-111">İleti, bir yeniden yürütme saldırısında meydana gelebilen bir öncekinden yineleniyor.</span><span class="sxs-lookup"><span data-stu-id="5a56d-111">The message is a duplicate from a previous one, which can happen during a replay attack.</span></span>  
  
- <span data-ttu-id="5a56d-112">Şifre çözme hatası oluştu.</span><span class="sxs-lookup"><span data-stu-id="5a56d-112">A decryption failure has occurred.</span></span>  
  
- <span data-ttu-id="5a56d-113">İletide bazı gerekli öğeler (eksik zaman damgası veya şifrelenmiş veri bloğu) eksik.</span><span class="sxs-lookup"><span data-stu-id="5a56d-113">Some required elements (missing timestamp or encrypted data block) are missing from the message.</span></span>  
  
- <span data-ttu-id="5a56d-114">TLSNEGO/SPNEGO Handshake sırasında hatalar oluştu.</span><span class="sxs-lookup"><span data-stu-id="5a56d-114">Errors have occurred during TLSNEGO/SPNEGO handshake.</span></span>
