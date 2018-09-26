---
title: 'Uç Noktası: Güvenlik Doğrulaması ve Kimlik Doğrulaması Hataları'
ms.date: 03/30/2017
ms.assetid: 5bad60aa-6084-4c7b-aefd-9b581f04382e
author: BrucePerlerMS
ms.openlocfilehash: f7cd2268eefa0176ab71a3d5d3bc82c178664742
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/25/2018
ms.locfileid: "47075102"
---
# <a name="endpoint-security-validation-and-authentication-failures"></a><span data-ttu-id="77de8-102">Uç Noktası: Güvenlik Doğrulaması ve Kimlik Doğrulaması Hataları</span><span class="sxs-lookup"><span data-stu-id="77de8-102">Endpoint: Security Validation and Authentication Failures</span></span>
<span data-ttu-id="77de8-103">Sayaç adı: güvenlik doğrulaması ve kimlik doğrulaması hataları</span><span class="sxs-lookup"><span data-stu-id="77de8-103">Counter name: Security Validation and Authentication Failures</span></span>  
  
## <a name="description"></a><span data-ttu-id="77de8-104">Açıklama</span><span class="sxs-lookup"><span data-stu-id="77de8-104">Description</span></span>  
 <span data-ttu-id="77de8-105">Her bir ileti "Güvenlik çağrıları yetkilendirilmedi" sayacı tarafından kapsanmayan bir güvenlik sorunu nedeniyle reddedilmesi Bu sayaç artırılır.</span><span class="sxs-lookup"><span data-stu-id="77de8-105">This counter is incremented whenever a message is rejected due to a security problem not covered by the "Security Calls Not Authorized" counter.</span></span> <span data-ttu-id="77de8-106">Bu tür sorunlar şunlardır:</span><span class="sxs-lookup"><span data-stu-id="77de8-106">Such problems include:</span></span>  
  
-   <span data-ttu-id="77de8-107">İstemci belirteci iletiden okunamıyor.</span><span class="sxs-lookup"><span data-stu-id="77de8-107">Client token cannot be read from the message.</span></span>  
  
-   <span data-ttu-id="77de8-108">İstemci belirteci (hatalı parola) kimlik doğrulaması başarısız oldu.</span><span class="sxs-lookup"><span data-stu-id="77de8-108">Client token has failed authentication (bad password).</span></span>  
  
-   <span data-ttu-id="77de8-109">İmza doğrulaması başarısız oldu. (ileti oynanmış).</span><span class="sxs-lookup"><span data-stu-id="77de8-109">Signature verification has failed (the message has been tampered).</span></span>  
  
-   <span data-ttu-id="77de8-110">İleti yeniden yürütme bir saldırı sırasında gerçekleşebilir bir önceki bir yineleniyor.</span><span class="sxs-lookup"><span data-stu-id="77de8-110">The message is a duplicate from a previous one, which can happen during a replay attack.</span></span>  
  
-   <span data-ttu-id="77de8-111">Bir şifre çözme hatası oluştu.</span><span class="sxs-lookup"><span data-stu-id="77de8-111">A decryption failure has occurred.</span></span>  
  
-   <span data-ttu-id="77de8-112">İleti (zaman damgası veya şifrelenmiş veri bloğu eksik) bazı gerekli öğeleri eksik.</span><span class="sxs-lookup"><span data-stu-id="77de8-112">Some required elements (missing timestamp or encrypted data block) are missing from the message.</span></span>  
  
-   <span data-ttu-id="77de8-113">TLSNEGO/SPNEGO anlaşması sırasında hatalar oluştu.</span><span class="sxs-lookup"><span data-stu-id="77de8-113">Errors have occurred during TLSNEGO/SPNEGO handshake.</span></span>
