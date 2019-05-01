---
title: 'Uç noktası: Güvenlik Doğrulama ve Kimlik Doğrulama Hataları'
ms.date: 03/30/2017
ms.assetid: 5bad60aa-6084-4c7b-aefd-9b581f04382e
ms.openlocfilehash: e69549a276e2f9cece966dd44f6a1b3a3d3cb59f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61916337"
---
# <a name="endpoint-security-validation-and-authentication-failures"></a><span data-ttu-id="34698-102">Uç noktası: Güvenlik Doğrulama ve Kimlik Doğrulama Hataları</span><span class="sxs-lookup"><span data-stu-id="34698-102">Endpoint: Security Validation and Authentication Failures</span></span>
<span data-ttu-id="34698-103">Sayaç adı: Güvenlik Doğrulama ve Kimlik Doğrulama Hataları</span><span class="sxs-lookup"><span data-stu-id="34698-103">Counter name: Security Validation and Authentication Failures</span></span>  
  
## <a name="description"></a><span data-ttu-id="34698-104">Açıklama</span><span class="sxs-lookup"><span data-stu-id="34698-104">Description</span></span>  
 <span data-ttu-id="34698-105">Her bir ileti "Güvenlik çağrıları yetkilendirilmedi" sayacı tarafından kapsanmayan bir güvenlik sorunu nedeniyle reddedilmesi Bu sayaç artırılır.</span><span class="sxs-lookup"><span data-stu-id="34698-105">This counter is incremented whenever a message is rejected due to a security problem not covered by the "Security Calls Not Authorized" counter.</span></span> <span data-ttu-id="34698-106">Bu tür sorunlar şunlardır:</span><span class="sxs-lookup"><span data-stu-id="34698-106">Such problems include:</span></span>  
  
- <span data-ttu-id="34698-107">İstemci belirteci iletiden okunamıyor.</span><span class="sxs-lookup"><span data-stu-id="34698-107">Client token cannot be read from the message.</span></span>  
  
- <span data-ttu-id="34698-108">İstemci belirteci (hatalı parola) kimlik doğrulaması başarısız oldu.</span><span class="sxs-lookup"><span data-stu-id="34698-108">Client token has failed authentication (bad password).</span></span>  
  
- <span data-ttu-id="34698-109">İmza doğrulaması başarısız oldu. (ileti oynanmış).</span><span class="sxs-lookup"><span data-stu-id="34698-109">Signature verification has failed (the message has been tampered).</span></span>  
  
- <span data-ttu-id="34698-110">İleti yeniden yürütme bir saldırı sırasında gerçekleşebilir bir önceki bir yineleniyor.</span><span class="sxs-lookup"><span data-stu-id="34698-110">The message is a duplicate from a previous one, which can happen during a replay attack.</span></span>  
  
- <span data-ttu-id="34698-111">Bir şifre çözme hatası oluştu.</span><span class="sxs-lookup"><span data-stu-id="34698-111">A decryption failure has occurred.</span></span>  
  
- <span data-ttu-id="34698-112">İleti (zaman damgası veya şifrelenmiş veri bloğu eksik) bazı gerekli öğeleri eksik.</span><span class="sxs-lookup"><span data-stu-id="34698-112">Some required elements (missing timestamp or encrypted data block) are missing from the message.</span></span>  
  
- <span data-ttu-id="34698-113">TLSNEGO/SPNEGO anlaşması sırasında hatalar oluştu.</span><span class="sxs-lookup"><span data-stu-id="34698-113">Errors have occurred during TLSNEGO/SPNEGO handshake.</span></span>
