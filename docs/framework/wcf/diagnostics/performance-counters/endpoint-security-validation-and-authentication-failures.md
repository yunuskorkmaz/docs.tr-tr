---
title: 'Uç Noktası: Güvenlik Doğrulaması ve Kimlik Doğrulaması Hataları'
ms.date: 03/30/2017
ms.assetid: 5bad60aa-6084-4c7b-aefd-9b581f04382e
ms.openlocfilehash: a9a4758b26c744c55af200aee22a7e90c5a5cf57
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96256475"
---
# <a name="endpoint-security-validation-and-authentication-failures"></a><span data-ttu-id="76485-102">Uç Noktası: Güvenlik Doğrulaması ve Kimlik Doğrulaması Hataları</span><span class="sxs-lookup"><span data-stu-id="76485-102">Endpoint: Security Validation and Authentication Failures</span></span>

<span data-ttu-id="76485-103">Sayaç adı: güvenlik doğrulama ve kimlik doğrulama sorunları</span><span class="sxs-lookup"><span data-stu-id="76485-103">Counter name: Security Validation and Authentication Failures</span></span>  
  
## <a name="description"></a><span data-ttu-id="76485-104">Açıklama</span><span class="sxs-lookup"><span data-stu-id="76485-104">Description</span></span>  

 <span data-ttu-id="76485-105">Bu sayaç, "güvenlik çağrıları yetkilendirilmemiş" sayacı kapsamında olmayan bir güvenlik sorunu nedeniyle her ileti reddedildiğinde artırılır.</span><span class="sxs-lookup"><span data-stu-id="76485-105">This counter is incremented whenever a message is rejected due to a security problem not covered by the "Security Calls Not Authorized" counter.</span></span> <span data-ttu-id="76485-106">Bu tür sorunlar şunlardır:</span><span class="sxs-lookup"><span data-stu-id="76485-106">Such problems include:</span></span>  
  
- <span data-ttu-id="76485-107">İstemci belirteci iletiden okunamıyor.</span><span class="sxs-lookup"><span data-stu-id="76485-107">Client token cannot be read from the message.</span></span>  
  
- <span data-ttu-id="76485-108">İstemci belirteci kimlik doğrulaması başarısız oldu (hatalı parola).</span><span class="sxs-lookup"><span data-stu-id="76485-108">Client token has failed authentication (bad password).</span></span>  
  
- <span data-ttu-id="76485-109">İmza doğrulama başarısız oldu (ileti değiştirilmiş).</span><span class="sxs-lookup"><span data-stu-id="76485-109">Signature verification has failed (the message has been tampered).</span></span>  
  
- <span data-ttu-id="76485-110">İleti, bir yeniden yürütme saldırısında meydana gelebilen bir öncekinden yineleniyor.</span><span class="sxs-lookup"><span data-stu-id="76485-110">The message is a duplicate from a previous one, which can happen during a replay attack.</span></span>  
  
- <span data-ttu-id="76485-111">Şifre çözme hatası oluştu.</span><span class="sxs-lookup"><span data-stu-id="76485-111">A decryption failure has occurred.</span></span>  
  
- <span data-ttu-id="76485-112">İletide bazı gerekli öğeler (eksik zaman damgası veya şifrelenmiş veri bloğu) eksik.</span><span class="sxs-lookup"><span data-stu-id="76485-112">Some required elements (missing timestamp or encrypted data block) are missing from the message.</span></span>  
  
- <span data-ttu-id="76485-113">TLSNEGO/SPNEGO Handshake sırasında hatalar oluştu.</span><span class="sxs-lookup"><span data-stu-id="76485-113">Errors have occurred during TLSNEGO/SPNEGO handshake.</span></span>
