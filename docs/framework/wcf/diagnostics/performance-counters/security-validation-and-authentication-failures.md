---
description: 'Daha fazla bilgi edinin: güvenlik doğrulama ve kimlik doğrulama sorunları'
title: Güvenlik Doğrulama ve Kimlik Doğrulama Hataları
ms.date: 03/30/2017
ms.assetid: 0d4e3666-dfc6-421c-baf8-9479c22f7050
ms.openlocfilehash: 1de74a277c3b63d304be35baac9117ec613e3c7d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99803392"
---
# <a name="security-validation-and-authentication-failures"></a><span data-ttu-id="12b47-103">Güvenlik Doğrulama ve Kimlik Doğrulama Hataları</span><span class="sxs-lookup"><span data-stu-id="12b47-103">Security Validation and Authentication Failures</span></span>

<span data-ttu-id="12b47-104">Sayaç adı: güvenlik doğrulama ve kimlik doğrulama sorunları</span><span class="sxs-lookup"><span data-stu-id="12b47-104">Counter name: Security Validation and Authentication Failures</span></span>  
  
## <a name="description"></a><span data-ttu-id="12b47-105">Description</span><span class="sxs-lookup"><span data-stu-id="12b47-105">Description</span></span>  

 <span data-ttu-id="12b47-106">Bu sayaç, "güvenlik çağrıları yetkilendirilmemiş" sayacı kapsamında olmayan bir güvenlik sorunu nedeniyle her ileti reddedildiğinde artırılır.</span><span class="sxs-lookup"><span data-stu-id="12b47-106">This counter is incremented whenever a message is rejected due to a security problem not covered by the "Security Calls Not Authorized" counter.</span></span> <span data-ttu-id="12b47-107">Bu tür sorunlar şunlardır:</span><span class="sxs-lookup"><span data-stu-id="12b47-107">Such problems include:</span></span>  
  
- <span data-ttu-id="12b47-108">İstemci belirteci iletiden okunamıyor.</span><span class="sxs-lookup"><span data-stu-id="12b47-108">Client token cannot be read from the message.</span></span>  
  
- <span data-ttu-id="12b47-109">İstemci belirteci kimlik doğrulaması başarısız oldu (örneğin, hatalı parola).</span><span class="sxs-lookup"><span data-stu-id="12b47-109">Client token has failed authentication (for example, bad password).</span></span>  
  
- <span data-ttu-id="12b47-110">İmza doğrulama başarısız oldu (örneğin, ileti değiştirilmiş).</span><span class="sxs-lookup"><span data-stu-id="12b47-110">Signature verification has failed (for example, the message has been tampered).</span></span>  
  
- <span data-ttu-id="12b47-111">İleti, bir yeniden yürütme saldırısında meydana gelebilen bir öncekinden yineleniyor.</span><span class="sxs-lookup"><span data-stu-id="12b47-111">The message is a duplicate from a previous one, which can happen during a replay attack.</span></span>  
  
- <span data-ttu-id="12b47-112">Şifre çözme hatası oluştu.</span><span class="sxs-lookup"><span data-stu-id="12b47-112">A decryption failure has occurred.</span></span>  
  
- <span data-ttu-id="12b47-113">İletide bazı gerekli öğeler (örneğin, eksik zaman damgası veya şifrelenmiş veri bloğu) eksik.</span><span class="sxs-lookup"><span data-stu-id="12b47-113">Some required elements (for example, missing timestamp or encrypted data block) are missing from the message.</span></span>  
  
- <span data-ttu-id="12b47-114">TLSNEGO/SPNEGO Handshake sırasında hatalar oluştu.</span><span class="sxs-lookup"><span data-stu-id="12b47-114">Errors have occurred during TLSNEGO/SPNEGO handshake.</span></span>
