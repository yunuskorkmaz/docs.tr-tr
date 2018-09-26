---
title: Güvenlik Doğrulama ve Kimlik Doğrulama Hataları
ms.date: 03/30/2017
ms.assetid: 0d4e3666-dfc6-421c-baf8-9479c22f7050
author: BrucePerlerMS
ms.openlocfilehash: d13e94800d71c6f567c6aab61974e42b1a3f1706
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/26/2018
ms.locfileid: "47198195"
---
# <a name="security-validation-and-authentication-failures"></a><span data-ttu-id="334f0-102">Güvenlik Doğrulama ve Kimlik Doğrulama Hataları</span><span class="sxs-lookup"><span data-stu-id="334f0-102">Security Validation and Authentication Failures</span></span>
<span data-ttu-id="334f0-103">Sayaç adı: güvenlik doğrulaması ve kimlik doğrulaması hataları</span><span class="sxs-lookup"><span data-stu-id="334f0-103">Counter name: Security Validation and Authentication Failures</span></span>  
  
## <a name="description"></a><span data-ttu-id="334f0-104">Açıklama</span><span class="sxs-lookup"><span data-stu-id="334f0-104">Description</span></span>  
 <span data-ttu-id="334f0-105">Her bir ileti "Güvenlik çağrıları yetkilendirilmedi" sayacı tarafından kapsanmayan bir güvenlik sorunu nedeniyle reddedilmesi Bu sayaç artırılır.</span><span class="sxs-lookup"><span data-stu-id="334f0-105">This counter is incremented whenever a message is rejected due to a security problem not covered by the "Security Calls Not Authorized" counter.</span></span> <span data-ttu-id="334f0-106">Bu tür sorunlar şunlardır:</span><span class="sxs-lookup"><span data-stu-id="334f0-106">Such problems include:</span></span>  
  
-   <span data-ttu-id="334f0-107">İstemci belirteci iletiden okunamıyor.</span><span class="sxs-lookup"><span data-stu-id="334f0-107">Client token cannot be read from the message.</span></span>  
  
-   <span data-ttu-id="334f0-108">İstemci belirteci (örneğin, hatalı parola) kimlik doğrulaması başarısız oldu.</span><span class="sxs-lookup"><span data-stu-id="334f0-108">Client token has failed authentication (for example, bad password).</span></span>  
  
-   <span data-ttu-id="334f0-109">İmza doğrulaması başarısız oldu (örneğin, iletiyi oynanmadığını).</span><span class="sxs-lookup"><span data-stu-id="334f0-109">Signature verification has failed (for example, the message has been tampered).</span></span>  
  
-   <span data-ttu-id="334f0-110">İleti yeniden yürütme bir saldırı sırasında gerçekleşebilir bir önceki bir yineleniyor.</span><span class="sxs-lookup"><span data-stu-id="334f0-110">The message is a duplicate from a previous one, which can happen during a replay attack.</span></span>  
  
-   <span data-ttu-id="334f0-111">Bir şifre çözme hatası oluştu.</span><span class="sxs-lookup"><span data-stu-id="334f0-111">A decryption failure has occurred.</span></span>  
  
-   <span data-ttu-id="334f0-112">Gereken bazı öğeleri (örneğin, eksik bir zaman damgası veya şifrelenmiş veriler engelle) gelen iletiyi yok.</span><span class="sxs-lookup"><span data-stu-id="334f0-112">Some required elements (for example, missing timestamp or encrypted data block) are missing from the message.</span></span>  
  
-   <span data-ttu-id="334f0-113">TLSNEGO/SPNEGO anlaşması sırasında hatalar oluştu.</span><span class="sxs-lookup"><span data-stu-id="334f0-113">Errors have occurred during TLSNEGO/SPNEGO handshake.</span></span>
