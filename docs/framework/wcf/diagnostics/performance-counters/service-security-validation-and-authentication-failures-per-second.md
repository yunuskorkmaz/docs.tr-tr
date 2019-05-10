---
title: 'Hizmet: Güvenlik Doğrulaması ve Kimlik Doğrulaması Hatası/Saniye'
ms.date: 03/30/2017
ms.assetid: 4af18009-e778-490b-9ba6-e76485285830
ms.openlocfilehash: 2caebed85a28004ef038beee7d07c05a23da53c0
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64613680"
---
# <a name="service-security-validation-and-authentication-failures-per-second"></a><span data-ttu-id="676b6-102">Hizmet: Güvenlik Doğrulaması ve Kimlik Doğrulaması Hatası/Saniye</span><span class="sxs-lookup"><span data-stu-id="676b6-102">Service: Security Validation and Authentication Failures Per Second</span></span>
<span data-ttu-id="676b6-103">Sayaç adı: Güvenlik doğrulaması ve saniye başına kimlik doğrulama hataları.</span><span class="sxs-lookup"><span data-stu-id="676b6-103">Counter name: Security Validation and Authentication Failures Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="676b6-104">Açıklama</span><span class="sxs-lookup"><span data-stu-id="676b6-104">Description</span></span>  
 <span data-ttu-id="676b6-105">Her bir ileti "Güvenlik çağrıları yetkilendirilmedi" sayacı tarafından kapsanmayan bir güvenlik sorunu nedeniyle reddedilmesi Bu sayaç artırılır.</span><span class="sxs-lookup"><span data-stu-id="676b6-105">This counter is incremented whenever a message is rejected due to a security problem not covered by the "Security Calls Not Authorized" counter.</span></span> <span data-ttu-id="676b6-106">Bu tür sorunlar şunlardır:</span><span class="sxs-lookup"><span data-stu-id="676b6-106">Such problems include:</span></span>  
  
- <span data-ttu-id="676b6-107">İstemci belirteci iletiden okunamıyor.</span><span class="sxs-lookup"><span data-stu-id="676b6-107">Client token cannot be read from the message.</span></span>  
  
- <span data-ttu-id="676b6-108">İstemci belirteci (örneğin, hatalı parola) kimlik doğrulaması başarısız oldu.</span><span class="sxs-lookup"><span data-stu-id="676b6-108">Client token has failed authentication (for example, bad password).</span></span>  
  
- <span data-ttu-id="676b6-109">İmza doğrulaması başarısız oldu (örneğin, iletiyi oynanmadığını).</span><span class="sxs-lookup"><span data-stu-id="676b6-109">Signature verification has failed (for example, the message has been tampered).</span></span>  
  
- <span data-ttu-id="676b6-110">İleti yeniden yürütme bir saldırı sırasında gerçekleşebilir bir önceki bir yineleniyor.</span><span class="sxs-lookup"><span data-stu-id="676b6-110">The message is a duplicate from a previous one, which can happen during a replay attack.</span></span>  
  
- <span data-ttu-id="676b6-111">Bir şifre çözme hatası oluştu.</span><span class="sxs-lookup"><span data-stu-id="676b6-111">A decryption failure has occurred.</span></span>  
  
- <span data-ttu-id="676b6-112">Gereken bazı öğeleri (örneğin, eksik bir zaman damgası veya şifrelenmiş veriler engelle) gelen iletiyi yok.</span><span class="sxs-lookup"><span data-stu-id="676b6-112">Some required elements (for example, missing timestamp or encrypted data block) are missing from the message.</span></span>  
  
- <span data-ttu-id="676b6-113">TLSNEGO/SPNEGO anlaşması sırasında hatalar oluştu.</span><span class="sxs-lookup"><span data-stu-id="676b6-113">Errors have occurred during TLSNEGO/SPNEGO handshake.</span></span>  
  
 <span data-ttu-id="676b6-114">Bu sayaç performans sayacı türüdür [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), değeri aşağıdaki formül kullanılarak hesaplanır</span><span class="sxs-lookup"><span data-stu-id="676b6-114">This counter is of performance counter type [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula,</span></span>  
  
 <span data-ttu-id="676b6-115">(1 - N 0 N) / ((D 1 - D 0) / F)</span><span class="sxs-lookup"><span data-stu-id="676b6-115">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
