---
title: Güvenlik Doğrulama ve Kimlik Doğrulama Hataları
ms.date: 03/30/2017
ms.assetid: 0d4e3666-dfc6-421c-baf8-9479c22f7050
ms.openlocfilehash: 3bcc6111f322a3bd8169567e8f436871eb19f879
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96253056"
---
# <a name="security-validation-and-authentication-failures"></a><span data-ttu-id="ccef3-102">Güvenlik Doğrulama ve Kimlik Doğrulama Hataları</span><span class="sxs-lookup"><span data-stu-id="ccef3-102">Security Validation and Authentication Failures</span></span>

<span data-ttu-id="ccef3-103">Sayaç adı: güvenlik doğrulama ve kimlik doğrulama sorunları</span><span class="sxs-lookup"><span data-stu-id="ccef3-103">Counter name: Security Validation and Authentication Failures</span></span>  
  
## <a name="description"></a><span data-ttu-id="ccef3-104">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ccef3-104">Description</span></span>  

 <span data-ttu-id="ccef3-105">Bu sayaç, "güvenlik çağrıları yetkilendirilmemiş" sayacı kapsamında olmayan bir güvenlik sorunu nedeniyle her ileti reddedildiğinde artırılır.</span><span class="sxs-lookup"><span data-stu-id="ccef3-105">This counter is incremented whenever a message is rejected due to a security problem not covered by the "Security Calls Not Authorized" counter.</span></span> <span data-ttu-id="ccef3-106">Bu tür sorunlar şunlardır:</span><span class="sxs-lookup"><span data-stu-id="ccef3-106">Such problems include:</span></span>  
  
- <span data-ttu-id="ccef3-107">İstemci belirteci iletiden okunamıyor.</span><span class="sxs-lookup"><span data-stu-id="ccef3-107">Client token cannot be read from the message.</span></span>  
  
- <span data-ttu-id="ccef3-108">İstemci belirteci kimlik doğrulaması başarısız oldu (örneğin, hatalı parola).</span><span class="sxs-lookup"><span data-stu-id="ccef3-108">Client token has failed authentication (for example, bad password).</span></span>  
  
- <span data-ttu-id="ccef3-109">İmza doğrulama başarısız oldu (örneğin, ileti değiştirilmiş).</span><span class="sxs-lookup"><span data-stu-id="ccef3-109">Signature verification has failed (for example, the message has been tampered).</span></span>  
  
- <span data-ttu-id="ccef3-110">İleti, bir yeniden yürütme saldırısında meydana gelebilen bir öncekinden yineleniyor.</span><span class="sxs-lookup"><span data-stu-id="ccef3-110">The message is a duplicate from a previous one, which can happen during a replay attack.</span></span>  
  
- <span data-ttu-id="ccef3-111">Şifre çözme hatası oluştu.</span><span class="sxs-lookup"><span data-stu-id="ccef3-111">A decryption failure has occurred.</span></span>  
  
- <span data-ttu-id="ccef3-112">İletide bazı gerekli öğeler (örneğin, eksik zaman damgası veya şifrelenmiş veri bloğu) eksik.</span><span class="sxs-lookup"><span data-stu-id="ccef3-112">Some required elements (for example, missing timestamp or encrypted data block) are missing from the message.</span></span>  
  
- <span data-ttu-id="ccef3-113">TLSNEGO/SPNEGO Handshake sırasında hatalar oluştu.</span><span class="sxs-lookup"><span data-stu-id="ccef3-113">Errors have occurred during TLSNEGO/SPNEGO handshake.</span></span>
