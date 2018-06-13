---
title: 'Uç Noktası: Güvenlik Doğrulaması ve Kimlik Doğrulaması Hataları'
ms.date: 03/30/2017
ms.assetid: 5bad60aa-6084-4c7b-aefd-9b581f04382e
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 8c46354fac11f5f0b46ef1b5629157f6da455fcb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33471813"
---
# <a name="endpoint-security-validation-and-authentication-failures"></a><span data-ttu-id="2159a-102">Uç Noktası: Güvenlik Doğrulaması ve Kimlik Doğrulaması Hataları</span><span class="sxs-lookup"><span data-stu-id="2159a-102">Endpoint: Security Validation and Authentication Failures</span></span>
<span data-ttu-id="2159a-103">Sayaç adı: güvenlik doğrulaması ve kimlik doğrulama hataları</span><span class="sxs-lookup"><span data-stu-id="2159a-103">Counter name: Security Validation and Authentication Failures</span></span>  
  
## <a name="description"></a><span data-ttu-id="2159a-104">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2159a-104">Description</span></span>  
 <span data-ttu-id="2159a-105">Bir ileti "Güvenlik çağrıları yetkilendirilmedi" sayacı tarafından kapsanmayan bir güvenlik sorunu nedeniyle reddedilen olduğunda bu sayaç artırılır.</span><span class="sxs-lookup"><span data-stu-id="2159a-105">This counter is incremented whenever a message is rejected due to a security problem not covered by the "Security Calls Not Authorized" counter.</span></span> <span data-ttu-id="2159a-106">Bu tür sorunlar içerir:</span><span class="sxs-lookup"><span data-stu-id="2159a-106">Such problems include:</span></span>  
  
-   <span data-ttu-id="2159a-107">İstemci belirteci iletiden okunamıyor.</span><span class="sxs-lookup"><span data-stu-id="2159a-107">Client token cannot be read from the message.</span></span>  
  
-   <span data-ttu-id="2159a-108">İstemci belirteci kimlik doğrulaması (hatalı parola) başarısız oldu.</span><span class="sxs-lookup"><span data-stu-id="2159a-108">Client token has failed authentication (bad password).</span></span>  
  
-   <span data-ttu-id="2159a-109">İmza doğrulaması başarısız oldu (ileti oynanmış).</span><span class="sxs-lookup"><span data-stu-id="2159a-109">Signature verification has failed (the message has been tampered).</span></span>  
  
-   <span data-ttu-id="2159a-110">İleti yeniden yürütme saldırı sırasında gerçekleşebilir bir önceki bir yineleniyor.</span><span class="sxs-lookup"><span data-stu-id="2159a-110">The message is a duplicate from a previous one, which can happen during a replay attack.</span></span>  
  
-   <span data-ttu-id="2159a-111">Bir şifre çözme hatası oluştu.</span><span class="sxs-lookup"><span data-stu-id="2159a-111">A decryption failure has occurred.</span></span>  
  
-   <span data-ttu-id="2159a-112">Gelen iletiyi (zaman damgası veya şifrelenmiş veri bloğunu eksik) bazı gerekli öğeleri eksik.</span><span class="sxs-lookup"><span data-stu-id="2159a-112">Some required elements (missing timestamp or encrypted data block) are missing from the message.</span></span>  
  
-   <span data-ttu-id="2159a-113">TLSNEGO/SPNEGO anlaşması sırasında hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="2159a-113">Errors have occurred during TLSNEGO/SPNEGO handshake.</span></span>
