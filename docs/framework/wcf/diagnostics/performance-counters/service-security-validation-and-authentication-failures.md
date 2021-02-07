---
description: 'Şu konuda daha fazla bilgi edinin: hizmet: güvenlik doğrulama ve kimlik doğrulama sorunları'
title: 'Hizmet: Güvenlik Doğrulama ve Kimlik Doğrulama Hataları'
ms.date: 03/30/2017
ms.assetid: 55c98268-b1ad-459d-851b-25ef52248187
ms.openlocfilehash: 8938c74e706526a02bf2ea5885951d067d6ebae9
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99759490"
---
# <a name="service-security-validation-and-authentication-failures"></a><span data-ttu-id="4c5a5-103">Hizmet: Güvenlik Doğrulama ve Kimlik Doğrulama Hataları</span><span class="sxs-lookup"><span data-stu-id="4c5a5-103">Service: Security Validation and Authentication Failures</span></span>

<span data-ttu-id="4c5a5-104">Sayaç adı: güvenlik doğrulama ve kimlik doğrulama sorunları</span><span class="sxs-lookup"><span data-stu-id="4c5a5-104">Counter name: Security Validation and Authentication Failures</span></span>  
  
## <a name="description"></a><span data-ttu-id="4c5a5-105">Description</span><span class="sxs-lookup"><span data-stu-id="4c5a5-105">Description</span></span>  

 <span data-ttu-id="4c5a5-106">Bu sayaç, "güvenlik çağrıları yetkilendirilmemiş" sayacı kapsamında olmayan bir güvenlik sorunu nedeniyle her ileti reddedildiğinde artırılır.</span><span class="sxs-lookup"><span data-stu-id="4c5a5-106">This counter is incremented whenever a message is rejected due to a security problem not covered by the "Security Calls Not Authorized" counter.</span></span> <span data-ttu-id="4c5a5-107">Bu tür sorunlar şunlardır:</span><span class="sxs-lookup"><span data-stu-id="4c5a5-107">Such problems include:</span></span>  
  
- <span data-ttu-id="4c5a5-108">İstemci belirteci iletiden okunamıyor.</span><span class="sxs-lookup"><span data-stu-id="4c5a5-108">Client token cannot be read from the message.</span></span>  
  
- <span data-ttu-id="4c5a5-109">İstemci belirteci kimlik doğrulaması başarısız oldu (örneğin, hatalı parola).</span><span class="sxs-lookup"><span data-stu-id="4c5a5-109">Client token has failed authentication (for example, bad password).</span></span>  
  
- <span data-ttu-id="4c5a5-110">İmza doğrulama başarısız oldu (örneğin, ileti değiştirilmiş).</span><span class="sxs-lookup"><span data-stu-id="4c5a5-110">Signature verification has failed (for example, the message has been tampered).</span></span>  
  
- <span data-ttu-id="4c5a5-111">İleti, bir yeniden yürütme saldırısında meydana gelebilen bir öncekinden yineleniyor.</span><span class="sxs-lookup"><span data-stu-id="4c5a5-111">The message is a duplicate from a previous one, which can happen during a replay attack.</span></span>  
  
- <span data-ttu-id="4c5a5-112">Şifre çözme hatası oluştu.</span><span class="sxs-lookup"><span data-stu-id="4c5a5-112">A decryption failure has occurred.</span></span>  
  
- <span data-ttu-id="4c5a5-113">İletide bazı gerekli öğeler (örneğin, eksik zaman damgası veya şifrelenmiş veri bloğu) eksik.</span><span class="sxs-lookup"><span data-stu-id="4c5a5-113">Some required elements (for example, missing timestamp or encrypted data block) are missing from the message.</span></span>  
  
- <span data-ttu-id="4c5a5-114">TLSNEGO/SPNEGO Handshake sırasında hatalar oluştu.</span><span class="sxs-lookup"><span data-stu-id="4c5a5-114">Errors have occurred during TLSNEGO/SPNEGO handshake.</span></span>
