---
title: 'Uç Noktası: Saniyede Güvenlik Doğrulaması ve Kimlik Doğrulaması Hatası'
ms.date: 03/30/2017
ms.assetid: 89a70b90-d7e4-4b03-9b84-4dc88ce3d605
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: b857a608c6b485c384956e55247b6e02c49a8564
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43725117"
---
# <a name="endpoint-security-validation-and-authentication-failures-per-second"></a><span data-ttu-id="500fe-102">Uç Noktası: Saniyede Güvenlik Doğrulaması ve Kimlik Doğrulaması Hatası</span><span class="sxs-lookup"><span data-stu-id="500fe-102">Endpoint: Security Validation and Authentication Failures Per Second</span></span>
<span data-ttu-id="500fe-103">Sayaç adı: güvenlik doğrulaması ve kimlik doğrulama hataları saniye başına</span><span class="sxs-lookup"><span data-stu-id="500fe-103">Counter name: Security Validation and Authentication Failures Per Second</span></span>  
  
## <a name="description"></a><span data-ttu-id="500fe-104">Açıklama</span><span class="sxs-lookup"><span data-stu-id="500fe-104">Description</span></span>  
 <span data-ttu-id="500fe-105">Her bir ileti "Güvenlik çağrıları yetkilendirilmedi" sayacı tarafından kapsanmayan bir güvenlik sorunu nedeniyle reddedilmesi Bu sayaç artırılır.</span><span class="sxs-lookup"><span data-stu-id="500fe-105">This counter is incremented whenever a message is rejected due to a security problem not covered by the "Security Calls Not Authorized" counter.</span></span> <span data-ttu-id="500fe-106">Bu tür sorunlar şunlardır:</span><span class="sxs-lookup"><span data-stu-id="500fe-106">Such problems include:</span></span>  
  
-   <span data-ttu-id="500fe-107">İstemci belirteci iletiden okunamıyor.</span><span class="sxs-lookup"><span data-stu-id="500fe-107">Client token cannot be read from the message.</span></span>  
  
-   <span data-ttu-id="500fe-108">İstemci belirteci (örneğin, hatalı parola) kimlik doğrulaması başarısız oldu.</span><span class="sxs-lookup"><span data-stu-id="500fe-108">Client token has failed authentication (for example, bad password).</span></span>  
  
-   <span data-ttu-id="500fe-109">İmza doğrulaması başarısız oldu (örneğin, iletiyi oynanmadığını).</span><span class="sxs-lookup"><span data-stu-id="500fe-109">Signature verification has failed (for example, the message has been tampered).</span></span>  
  
-   <span data-ttu-id="500fe-110">İleti yeniden yürütme bir saldırı sırasında gerçekleşebilir bir önceki bir yineleniyor.</span><span class="sxs-lookup"><span data-stu-id="500fe-110">The message is a duplicate from a previous one, which can happen during a replay attack.</span></span>  
  
-   <span data-ttu-id="500fe-111">Bir şifre çözme hatası oluştu.</span><span class="sxs-lookup"><span data-stu-id="500fe-111">A decryption failure has occurred.</span></span>  
  
-   <span data-ttu-id="500fe-112">Gereken bazı öğeleri (örneğin, eksik bir zaman damgası veya şifrelenmiş veriler engelle) gelen iletiyi yok.</span><span class="sxs-lookup"><span data-stu-id="500fe-112">Some required elements (for example, missing timestamp or encrypted data block) are missing from the message.</span></span>  
  
-   <span data-ttu-id="500fe-113">TLSNEGO/SPNEGO anlaşması sırasında hatalar oluştu.</span><span class="sxs-lookup"><span data-stu-id="500fe-113">Errors have occurred during TLSNEGO/SPNEGO handshake.</span></span>  
  
 <span data-ttu-id="500fe-114">Bu sayaç performans sayacı türüdür [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), değeri aşağıdaki formül kullanılarak hesaplanır:</span><span class="sxs-lookup"><span data-stu-id="500fe-114">This counter is of performance counter type [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula:</span></span>  
  
 <span data-ttu-id="500fe-115">(N1-N0)/((D1-D0)/F)</span><span class="sxs-lookup"><span data-stu-id="500fe-115">(N1-N0)/((D1-D0)/F)</span></span>
