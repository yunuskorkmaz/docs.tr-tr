---
title: 'Hizmet: Güvenlik Doğrulaması ve Kimlik Doğrulaması Hataları'
ms.date: 03/30/2017
ms.assetid: 55c98268-b1ad-459d-851b-25ef52248187
author: BrucePerlerMS
ms.openlocfilehash: 4c74cb1962bbc0f03ac33d8fcc7b10052bec8273
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/26/2018
ms.locfileid: "47197090"
---
# <a name="service-security-validation-and-authentication-failures"></a><span data-ttu-id="2c8e2-102">Hizmet: Güvenlik Doğrulaması ve Kimlik Doğrulaması Hataları</span><span class="sxs-lookup"><span data-stu-id="2c8e2-102">Service: Security Validation and Authentication Failures</span></span>
<span data-ttu-id="2c8e2-103">Sayaç adı: güvenlik doğrulaması ve kimlik doğrulaması hataları</span><span class="sxs-lookup"><span data-stu-id="2c8e2-103">Counter name: Security Validation and Authentication Failures</span></span>  
  
## <a name="description"></a><span data-ttu-id="2c8e2-104">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2c8e2-104">Description</span></span>  
 <span data-ttu-id="2c8e2-105">Her bir ileti "Güvenlik çağrıları yetkilendirilmedi" sayacı tarafından kapsanmayan bir güvenlik sorunu nedeniyle reddedilmesi Bu sayaç artırılır.</span><span class="sxs-lookup"><span data-stu-id="2c8e2-105">This counter is incremented whenever a message is rejected due to a security problem not covered by the "Security Calls Not Authorized" counter.</span></span> <span data-ttu-id="2c8e2-106">Bu tür sorunlar şunlardır:</span><span class="sxs-lookup"><span data-stu-id="2c8e2-106">Such problems include:</span></span>  
  
-   <span data-ttu-id="2c8e2-107">İstemci belirteci iletiden okunamıyor.</span><span class="sxs-lookup"><span data-stu-id="2c8e2-107">Client token cannot be read from the message.</span></span>  
  
-   <span data-ttu-id="2c8e2-108">İstemci belirteci (örneğin, hatalı parola) kimlik doğrulaması başarısız oldu.</span><span class="sxs-lookup"><span data-stu-id="2c8e2-108">Client token has failed authentication (for example,, bad password).</span></span>  
  
-   <span data-ttu-id="2c8e2-109">İmza doğrulaması başarısız oldu (örneğin, iletiyi oynanmadığını).</span><span class="sxs-lookup"><span data-stu-id="2c8e2-109">Signature verification has failed (for example,, the message has been tampered).</span></span>  
  
-   <span data-ttu-id="2c8e2-110">İleti yeniden yürütme bir saldırı sırasında gerçekleşebilir bir önceki bir yineleniyor.</span><span class="sxs-lookup"><span data-stu-id="2c8e2-110">The message is a duplicate from a previous one, which can happen during a replay attack.</span></span>  
  
-   <span data-ttu-id="2c8e2-111">Bir şifre çözme hatası oluştu.</span><span class="sxs-lookup"><span data-stu-id="2c8e2-111">A decryption failure has occurred.</span></span>  
  
-   <span data-ttu-id="2c8e2-112">Gereken bazı öğeleri (örneğin, eksik bir zaman damgası veya şifrelenmiş veriler engelleme) gelen iletiyi yok.</span><span class="sxs-lookup"><span data-stu-id="2c8e2-112">Some required elements (for example,, missing timestamp or encrypted data block) are missing from the message.</span></span>  
  
-   <span data-ttu-id="2c8e2-113">TLSNEGO/SPNEGO anlaşması sırasında hatalar oluştu.</span><span class="sxs-lookup"><span data-stu-id="2c8e2-113">Errors have occurred during TLSNEGO/SPNEGO handshake.</span></span>
