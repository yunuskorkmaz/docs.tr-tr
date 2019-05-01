---
title: 'Hizmet: Güvenlik Doğrulaması ve Kimlik Doğrulaması Hatası/Saniye'
ms.date: 03/30/2017
ms.assetid: 4af18009-e778-490b-9ba6-e76485285830
ms.openlocfilehash: 97752fbd4ff38c40917c132fddfe3798a7ee6766
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61998328"
---
# <a name="service-security-validation-and-authentication-failures-per-second"></a><span data-ttu-id="47b51-102">Hizmet: Güvenlik Doğrulaması ve Kimlik Doğrulaması Hatası/Saniye</span><span class="sxs-lookup"><span data-stu-id="47b51-102">Service: Security Validation and Authentication Failures Per Second</span></span>
<span data-ttu-id="47b51-103">Sayaç adı: Güvenlik doğrulaması ve saniye başına kimlik doğrulama hataları.</span><span class="sxs-lookup"><span data-stu-id="47b51-103">Counter name: Security Validation and Authentication Failures Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="47b51-104">Açıklama</span><span class="sxs-lookup"><span data-stu-id="47b51-104">Description</span></span>  
 <span data-ttu-id="47b51-105">Her bir ileti "Güvenlik çağrıları yetkilendirilmedi" sayacı tarafından kapsanmayan bir güvenlik sorunu nedeniyle reddedilmesi Bu sayaç artırılır.</span><span class="sxs-lookup"><span data-stu-id="47b51-105">This counter is incremented whenever a message is rejected due to a security problem not covered by the "Security Calls Not Authorized" counter.</span></span> <span data-ttu-id="47b51-106">Bu tür sorunlar şunlardır:</span><span class="sxs-lookup"><span data-stu-id="47b51-106">Such problems include:</span></span>  
  
- <span data-ttu-id="47b51-107">İstemci belirteci iletiden okunamıyor.</span><span class="sxs-lookup"><span data-stu-id="47b51-107">Client token cannot be read from the message.</span></span>  
  
- <span data-ttu-id="47b51-108">İstemci belirteci (örneğin, hatalı parola) kimlik doğrulaması başarısız oldu.</span><span class="sxs-lookup"><span data-stu-id="47b51-108">Client token has failed authentication (for example, bad password).</span></span>  
  
- <span data-ttu-id="47b51-109">İmza doğrulaması başarısız oldu (örneğin, iletiyi oynanmadığını).</span><span class="sxs-lookup"><span data-stu-id="47b51-109">Signature verification has failed (for example, the message has been tampered).</span></span>  
  
- <span data-ttu-id="47b51-110">İleti yeniden yürütme bir saldırı sırasında gerçekleşebilir bir önceki bir yineleniyor.</span><span class="sxs-lookup"><span data-stu-id="47b51-110">The message is a duplicate from a previous one, which can happen during a replay attack.</span></span>  
  
- <span data-ttu-id="47b51-111">Bir şifre çözme hatası oluştu.</span><span class="sxs-lookup"><span data-stu-id="47b51-111">A decryption failure has occurred.</span></span>  
  
- <span data-ttu-id="47b51-112">Gereken bazı öğeleri (örneğin, eksik bir zaman damgası veya şifrelenmiş veriler engelle) gelen iletiyi yok.</span><span class="sxs-lookup"><span data-stu-id="47b51-112">Some required elements (for example, missing timestamp or encrypted data block) are missing from the message.</span></span>  
  
- <span data-ttu-id="47b51-113">TLSNEGO/SPNEGO anlaşması sırasında hatalar oluştu.</span><span class="sxs-lookup"><span data-stu-id="47b51-113">Errors have occurred during TLSNEGO/SPNEGO handshake.</span></span>  
  
 <span data-ttu-id="47b51-114">Bu sayaç performans sayacı türüdür [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), değeri aşağıdaki formül kullanılarak hesaplanır</span><span class="sxs-lookup"><span data-stu-id="47b51-114">This counter is of performance counter type [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula,</span></span>  
  
 <span data-ttu-id="47b51-115">(1 - N 0 N) / ((D 1 - D 0) / F)</span><span class="sxs-lookup"><span data-stu-id="47b51-115">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
