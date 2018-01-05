---
title: "Saniyede Güvenlik Doğrulaması ve Kimlik Doğrulaması Hatası"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 266c3bd3-2ffc-4471-94b7-3675443be1ac
caps.latest.revision: "8"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 8159527f8f958c747a464641c69910c9df1b3d4e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="security-validation-and-authentication-failures-per-second"></a><span data-ttu-id="fc831-102">Saniyede Güvenlik Doğrulaması ve Kimlik Doğrulaması Hatası</span><span class="sxs-lookup"><span data-stu-id="fc831-102">Security Validation and Authentication Failures Per Second</span></span>
<span data-ttu-id="fc831-103">Sayaç adı: güvenlik doğrulaması ve kimlik doğrulama hataları saniyede.</span><span class="sxs-lookup"><span data-stu-id="fc831-103">Counter name: Security Validation and Authentication Failures Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="fc831-104">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fc831-104">Description</span></span>  
 <span data-ttu-id="fc831-105">Bir ileti "Güvenlik çağrıları yetkilendirilmedi" sayacı tarafından kapsanmayan bir güvenlik sorunu nedeniyle reddedilen olduğunda bu sayaç artırılır.</span><span class="sxs-lookup"><span data-stu-id="fc831-105">This counter is incremented whenever a message is rejected due to a security problem not covered by the "Security Calls Not Authorized" counter.</span></span> <span data-ttu-id="fc831-106">Bu tür sorunlar içerir:</span><span class="sxs-lookup"><span data-stu-id="fc831-106">Such problems include:</span></span>  
  
-   <span data-ttu-id="fc831-107">İstemci belirteci iletiden okunamıyor.</span><span class="sxs-lookup"><span data-stu-id="fc831-107">Client token cannot be read from the message.</span></span>  
  
-   <span data-ttu-id="fc831-108">İstemci belirteci kimlik doğrulaması (örneğin, hatalı parola) başarısız oldu.</span><span class="sxs-lookup"><span data-stu-id="fc831-108">Client token has failed authentication (for example, bad password).</span></span>  
  
-   <span data-ttu-id="fc831-109">İmza doğrulaması başarısız oldu (örneğin, ileti değiştirilmiş).</span><span class="sxs-lookup"><span data-stu-id="fc831-109">Signature verification has failed (for example, the message has been tampered).</span></span>  
  
-   <span data-ttu-id="fc831-110">İleti yeniden yürütme saldırı sırasında gerçekleşebilir bir önceki bir yineleniyor.</span><span class="sxs-lookup"><span data-stu-id="fc831-110">The message is a duplicate from a previous one, which can happen during a replay attack.</span></span>  
  
-   <span data-ttu-id="fc831-111">Bir şifre çözme hatası oluştu.</span><span class="sxs-lookup"><span data-stu-id="fc831-111">A decryption failure has occurred.</span></span>  
  
-   <span data-ttu-id="fc831-112">Gereken bazı iletiden öğeleri (örneğin, eksik zaman damgası veya engelleme şifrelenmiş veriler) eksik.</span><span class="sxs-lookup"><span data-stu-id="fc831-112">Some required elements (for example, missing timestamp or encrypted data block) are missing from the message.</span></span>  
  
-   <span data-ttu-id="fc831-113">TLSNEGO/SPNEGO anlaşması sırasında hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="fc831-113">Errors have occurred during TLSNEGO/SPNEGO handshake.</span></span>  
  
 <span data-ttu-id="fc831-114">Bu sayaç, performans sayacı türü [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), değeri, aşağıdaki formül kullanılarak hesaplanır:</span><span class="sxs-lookup"><span data-stu-id="fc831-114">This counter is of performance counter type [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula:</span></span>  
  
 <span data-ttu-id="fc831-115">(N1-N0)/((D1-D0)/F)</span><span class="sxs-lookup"><span data-stu-id="fc831-115">(N1-N0)/((D1-D0)/F)</span></span>
