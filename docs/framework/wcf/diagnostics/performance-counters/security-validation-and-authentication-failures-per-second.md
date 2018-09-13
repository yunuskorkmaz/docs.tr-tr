---
title: Saniyede Güvenlik Doğrulaması ve Kimlik Doğrulaması Hatası
ms.date: 03/30/2017
ms.assetid: 266c3bd3-2ffc-4471-94b7-3675443be1ac
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 4836a5076401de2f7c3112b298cdadc0e0307962
ms.sourcegitcommit: ba5c189bf44d44204a3e8838e59ec378a62d82f3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/12/2018
ms.locfileid: "44710284"
---
# <a name="security-validation-and-authentication-failures-per-second"></a><span data-ttu-id="fcdd7-102">Saniyede Güvenlik Doğrulaması ve Kimlik Doğrulaması Hatası</span><span class="sxs-lookup"><span data-stu-id="fcdd7-102">Security Validation and Authentication Failures Per Second</span></span>
<span data-ttu-id="fcdd7-103">Sayaç adı: güvenlik doğrulaması ve kimlik doğrulama hataları saniye başına.</span><span class="sxs-lookup"><span data-stu-id="fcdd7-103">Counter name: Security Validation and Authentication Failures Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="fcdd7-104">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fcdd7-104">Description</span></span>  
 <span data-ttu-id="fcdd7-105">Her bir ileti "Güvenlik çağrıları yetkilendirilmedi" sayacı tarafından kapsanmayan bir güvenlik sorunu nedeniyle reddedilmesi Bu sayaç artırılır.</span><span class="sxs-lookup"><span data-stu-id="fcdd7-105">This counter is incremented whenever a message is rejected due to a security problem not covered by the "Security Calls Not Authorized" counter.</span></span> <span data-ttu-id="fcdd7-106">Bu tür sorunlar şunlardır:</span><span class="sxs-lookup"><span data-stu-id="fcdd7-106">Such problems include:</span></span>  
  
-   <span data-ttu-id="fcdd7-107">İstemci belirteci iletiden okunamıyor.</span><span class="sxs-lookup"><span data-stu-id="fcdd7-107">Client token cannot be read from the message.</span></span>  
  
-   <span data-ttu-id="fcdd7-108">İstemci belirteci (örneğin, hatalı parola) kimlik doğrulaması başarısız oldu.</span><span class="sxs-lookup"><span data-stu-id="fcdd7-108">Client token has failed authentication (for example, bad password).</span></span>  
  
-   <span data-ttu-id="fcdd7-109">İmza doğrulaması başarısız oldu (örneğin, iletiyi oynanmadığını).</span><span class="sxs-lookup"><span data-stu-id="fcdd7-109">Signature verification has failed (for example, the message has been tampered).</span></span>  
  
-   <span data-ttu-id="fcdd7-110">İleti yeniden yürütme bir saldırı sırasında gerçekleşebilir bir önceki bir yineleniyor.</span><span class="sxs-lookup"><span data-stu-id="fcdd7-110">The message is a duplicate from a previous one, which can happen during a replay attack.</span></span>  
  
-   <span data-ttu-id="fcdd7-111">Bir şifre çözme hatası oluştu.</span><span class="sxs-lookup"><span data-stu-id="fcdd7-111">A decryption failure has occurred.</span></span>  
  
-   <span data-ttu-id="fcdd7-112">Gereken bazı öğeleri (örneğin, eksik bir zaman damgası veya şifrelenmiş veriler engelle) gelen iletiyi yok.</span><span class="sxs-lookup"><span data-stu-id="fcdd7-112">Some required elements (for example, missing timestamp or encrypted data block) are missing from the message.</span></span>  
  
-   <span data-ttu-id="fcdd7-113">TLSNEGO/SPNEGO anlaşması sırasında hatalar oluştu.</span><span class="sxs-lookup"><span data-stu-id="fcdd7-113">Errors have occurred during TLSNEGO/SPNEGO handshake.</span></span>  
  
 <span data-ttu-id="fcdd7-114">Bu sayaç performans sayacı türüdür [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), değeri aşağıdaki formül kullanılarak hesaplanır:</span><span class="sxs-lookup"><span data-stu-id="fcdd7-114">This counter is of performance counter type [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula:</span></span>  
  
 <span data-ttu-id="fcdd7-115">(N1-N0)/((D1-D0)/F)</span><span class="sxs-lookup"><span data-stu-id="fcdd7-115">(N1-N0)/((D1-D0)/F)</span></span>
