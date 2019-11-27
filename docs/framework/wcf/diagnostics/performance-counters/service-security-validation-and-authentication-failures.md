---
title: 'Hizmet: Güvenlik Doğrulama ve Kimlik Doğrulama Hataları'
ms.date: 03/30/2017
ms.assetid: 55c98268-b1ad-459d-851b-25ef52248187
ms.openlocfilehash: 399249926bcb1383fd33f60510c2c212c6f4261c
ms.sourcegitcommit: 81ad1f09b93f3b3e6706a7f2e4ddf50ef229ea3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/20/2019
ms.locfileid: "74204574"
---
# <a name="service-security-validation-and-authentication-failures"></a><span data-ttu-id="05c40-102">Hizmet: Güvenlik Doğrulama ve Kimlik Doğrulama Hataları</span><span class="sxs-lookup"><span data-stu-id="05c40-102">Service: Security Validation and Authentication Failures</span></span>
<span data-ttu-id="05c40-103">Sayaç adı: güvenlik doğrulama ve kimlik doğrulama sorunları</span><span class="sxs-lookup"><span data-stu-id="05c40-103">Counter name: Security Validation and Authentication Failures</span></span>  
  
## <a name="description"></a><span data-ttu-id="05c40-104">Açıklama</span><span class="sxs-lookup"><span data-stu-id="05c40-104">Description</span></span>  
 <span data-ttu-id="05c40-105">Bu sayaç, "güvenlik çağrıları yetkilendirilmemiş" sayacı kapsamında olmayan bir güvenlik sorunu nedeniyle her ileti reddedildiğinde artırılır.</span><span class="sxs-lookup"><span data-stu-id="05c40-105">This counter is incremented whenever a message is rejected due to a security problem not covered by the "Security Calls Not Authorized" counter.</span></span> <span data-ttu-id="05c40-106">Bu tür sorunlar şunlardır:</span><span class="sxs-lookup"><span data-stu-id="05c40-106">Such problems include:</span></span>  
  
- <span data-ttu-id="05c40-107">İstemci belirteci iletiden okunamıyor.</span><span class="sxs-lookup"><span data-stu-id="05c40-107">Client token cannot be read from the message.</span></span>  
  
- <span data-ttu-id="05c40-108">İstemci belirteci kimlik doğrulaması başarısız oldu (örneğin, hatalı parola).</span><span class="sxs-lookup"><span data-stu-id="05c40-108">Client token has failed authentication (for example, bad password).</span></span>  
  
- <span data-ttu-id="05c40-109">İmza doğrulama başarısız oldu (örneğin, ileti değiştirilmiş).</span><span class="sxs-lookup"><span data-stu-id="05c40-109">Signature verification has failed (for example, the message has been tampered).</span></span>  
  
- <span data-ttu-id="05c40-110">İleti, bir yeniden yürütme saldırısında meydana gelebilen bir öncekinden yineleniyor.</span><span class="sxs-lookup"><span data-stu-id="05c40-110">The message is a duplicate from a previous one, which can happen during a replay attack.</span></span>  
  
- <span data-ttu-id="05c40-111">Şifre çözme hatası oluştu.</span><span class="sxs-lookup"><span data-stu-id="05c40-111">A decryption failure has occurred.</span></span>  
  
- <span data-ttu-id="05c40-112">İletide bazı gerekli öğeler (örneğin, eksik zaman damgası veya şifrelenmiş veri bloğu) eksik.</span><span class="sxs-lookup"><span data-stu-id="05c40-112">Some required elements (for example, missing timestamp or encrypted data block) are missing from the message.</span></span>  
  
- <span data-ttu-id="05c40-113">TLSNEGO/SPNEGO Handshake sırasında hatalar oluştu.</span><span class="sxs-lookup"><span data-stu-id="05c40-113">Errors have occurred during TLSNEGO/SPNEGO handshake.</span></span>
