---
title: 'Uç Noktası: Saniyede Güvenlik Doğrulaması ve Kimlik Doğrulaması Hatası'
ms.date: 03/30/2017
ms.assetid: 89a70b90-d7e4-4b03-9b84-4dc88ce3d605
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: bc68f49326818f0e6687c06a38e5e51fd6960c9f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33474740"
---
# <a name="endpoint-security-validation-and-authentication-failures-per-second"></a><span data-ttu-id="2afe9-102">Uç Noktası: Saniyede Güvenlik Doğrulaması ve Kimlik Doğrulaması Hatası</span><span class="sxs-lookup"><span data-stu-id="2afe9-102">Endpoint: Security Validation and Authentication Failures Per Second</span></span>
<span data-ttu-id="2afe9-103">Sayaç adı: güvenlik doğrulaması ve kimlik doğrulama hataları saniye başına</span><span class="sxs-lookup"><span data-stu-id="2afe9-103">Counter name: Security Validation and Authentication Failures Per Second</span></span>  
  
## <a name="description"></a><span data-ttu-id="2afe9-104">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2afe9-104">Description</span></span>  
 <span data-ttu-id="2afe9-105">Bir ileti "Güvenlik çağrıları yetkilendirilmedi" sayacı tarafından kapsanmayan bir güvenlik sorunu nedeniyle reddedilen olduğunda bu sayaç artırılır.</span><span class="sxs-lookup"><span data-stu-id="2afe9-105">This counter is incremented whenever a message is rejected due to a security problem not covered by the "Security Calls Not Authorized" counter.</span></span> <span data-ttu-id="2afe9-106">Bu tür sorunlar içerir:</span><span class="sxs-lookup"><span data-stu-id="2afe9-106">Such problems include:</span></span>  
  
-   <span data-ttu-id="2afe9-107">İstemci belirteci iletiden okunamıyor.</span><span class="sxs-lookup"><span data-stu-id="2afe9-107">Client token cannot be read from the message.</span></span>  
  
-   <span data-ttu-id="2afe9-108">İstemci belirteci kimlik doğrulaması (örneğin, hatalı parola) başarısız oldu.</span><span class="sxs-lookup"><span data-stu-id="2afe9-108">Client token has failed authentication (for example, bad password).</span></span>  
  
-   <span data-ttu-id="2afe9-109">İmza doğrulaması başarısız oldu (örneğin, ileti değiştirilmiş).</span><span class="sxs-lookup"><span data-stu-id="2afe9-109">Signature verification has failed (for example, the message has been tampered).</span></span>  
  
-   <span data-ttu-id="2afe9-110">İleti yeniden yürütme saldırı sırasında gerçekleşebilir bir önceki bir yineleniyor.</span><span class="sxs-lookup"><span data-stu-id="2afe9-110">The message is a duplicate from a previous one, which can happen during a replay attack.</span></span>  
  
-   <span data-ttu-id="2afe9-111">Bir şifre çözme hatası oluştu.</span><span class="sxs-lookup"><span data-stu-id="2afe9-111">A decryption failure has occurred.</span></span>  
  
-   <span data-ttu-id="2afe9-112">Gereken bazı iletiden öğeleri (örneğin, eksik zaman damgası veya engelleme şifrelenmiş veriler) eksik.</span><span class="sxs-lookup"><span data-stu-id="2afe9-112">Some required elements (for example, missing timestamp or encrypted data block) are missing from the message.</span></span>  
  
-   <span data-ttu-id="2afe9-113">TLSNEGO/SPNEGO anlaşması sırasında hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="2afe9-113">Errors have occurred during TLSNEGO/SPNEGO handshake.</span></span>  
  
 <span data-ttu-id="2afe9-114">Bu sayaç, performans sayacı türü [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), değeri, aşağıdaki formül kullanılarak hesaplanır:</span><span class="sxs-lookup"><span data-stu-id="2afe9-114">This counter is of performance counter type [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula:</span></span>  
  
 <span data-ttu-id="2afe9-115">(N1-N0)/((D1-D0)/F)</span><span class="sxs-lookup"><span data-stu-id="2afe9-115">(N1-N0)/((D1-D0)/F)</span></span>
