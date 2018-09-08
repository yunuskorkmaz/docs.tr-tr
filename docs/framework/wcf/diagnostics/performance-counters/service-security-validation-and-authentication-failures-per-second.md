---
title: 'Hizmet: Saniyede Güvenlik Doğrulaması ve Kimlik Doğrulaması Hatası'
ms.date: 03/30/2017
ms.assetid: 4af18009-e778-490b-9ba6-e76485285830
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: fb0d4fdebf07dacfa7f33d8645332348270128e4
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2018
ms.locfileid: "44179513"
---
# <a name="service-security-validation-and-authentication-failures-per-second"></a><span data-ttu-id="02e12-102">Hizmet: Saniyede Güvenlik Doğrulaması ve Kimlik Doğrulaması Hatası</span><span class="sxs-lookup"><span data-stu-id="02e12-102">Service: Security Validation and Authentication Failures Per Second</span></span>
<span data-ttu-id="02e12-103">Sayaç adı: güvenlik doğrulaması ve kimlik doğrulama hataları saniye başına.</span><span class="sxs-lookup"><span data-stu-id="02e12-103">Counter name: Security Validation and Authentication Failures Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="02e12-104">Açıklama</span><span class="sxs-lookup"><span data-stu-id="02e12-104">Description</span></span>  
 <span data-ttu-id="02e12-105">Her bir ileti "Güvenlik çağrıları yetkilendirilmedi" sayacı tarafından kapsanmayan bir güvenlik sorunu nedeniyle reddedilmesi Bu sayaç artırılır.</span><span class="sxs-lookup"><span data-stu-id="02e12-105">This counter is incremented whenever a message is rejected due to a security problem not covered by the "Security Calls Not Authorized" counter.</span></span> <span data-ttu-id="02e12-106">Bu tür sorunlar şunlardır:</span><span class="sxs-lookup"><span data-stu-id="02e12-106">Such problems include:</span></span>  
  
-   <span data-ttu-id="02e12-107">İstemci belirteci iletiden okunamıyor.</span><span class="sxs-lookup"><span data-stu-id="02e12-107">Client token cannot be read from the message.</span></span>  
  
-   <span data-ttu-id="02e12-108">İstemci belirteci (örneğin, hatalı parola) kimlik doğrulaması başarısız oldu.</span><span class="sxs-lookup"><span data-stu-id="02e12-108">Client token has failed authentication (for example, bad password).</span></span>  
  
-   <span data-ttu-id="02e12-109">İmza doğrulaması başarısız oldu (örneğin, iletiyi oynanmadığını).</span><span class="sxs-lookup"><span data-stu-id="02e12-109">Signature verification has failed (for example, the message has been tampered).</span></span>  
  
-   <span data-ttu-id="02e12-110">İleti yeniden yürütme bir saldırı sırasında gerçekleşebilir bir önceki bir yineleniyor.</span><span class="sxs-lookup"><span data-stu-id="02e12-110">The message is a duplicate from a previous one, which can happen during a replay attack.</span></span>  
  
-   <span data-ttu-id="02e12-111">Bir şifre çözme hatası oluştu.</span><span class="sxs-lookup"><span data-stu-id="02e12-111">A decryption failure has occurred.</span></span>  
  
-   <span data-ttu-id="02e12-112">Gereken bazı öğeleri (örneğin, eksik bir zaman damgası veya şifrelenmiş veriler engelle) gelen iletiyi yok.</span><span class="sxs-lookup"><span data-stu-id="02e12-112">Some required elements (for example, missing timestamp or encrypted data block) are missing from the message.</span></span>  
  
-   <span data-ttu-id="02e12-113">TLSNEGO/SPNEGO anlaşması sırasında hatalar oluştu.</span><span class="sxs-lookup"><span data-stu-id="02e12-113">Errors have occurred during TLSNEGO/SPNEGO handshake.</span></span>  
  
 <span data-ttu-id="02e12-114">Bu sayaç performans sayacı türüdür [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), değeri aşağıdaki formül kullanılarak hesaplanır</span><span class="sxs-lookup"><span data-stu-id="02e12-114">This counter is of performance counter type [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula,</span></span>  
  
 <span data-ttu-id="02e12-115">(1 - N 0 N) / ((D 1 - D 0) / F)</span><span class="sxs-lookup"><span data-stu-id="02e12-115">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
