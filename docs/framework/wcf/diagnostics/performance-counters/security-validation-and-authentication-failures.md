---
title: Güvenlik Doğrulama ve Kimlik Doğrulama Hataları
ms.date: 03/30/2017
ms.assetid: 0d4e3666-dfc6-421c-baf8-9479c22f7050
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 5d7964c59f28f33d6ec7bc3ba605b84e6a201b14
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33474265"
---
# <a name="security-validation-and-authentication-failures"></a><span data-ttu-id="307d4-102">Güvenlik Doğrulama ve Kimlik Doğrulama Hataları</span><span class="sxs-lookup"><span data-stu-id="307d4-102">Security Validation and Authentication Failures</span></span>
<span data-ttu-id="307d4-103">Sayaç adı: güvenlik doğrulaması ve kimlik doğrulama hataları</span><span class="sxs-lookup"><span data-stu-id="307d4-103">Counter name: Security Validation and Authentication Failures</span></span>  
  
## <a name="description"></a><span data-ttu-id="307d4-104">Açıklama</span><span class="sxs-lookup"><span data-stu-id="307d4-104">Description</span></span>  
 <span data-ttu-id="307d4-105">Bir ileti "Güvenlik çağrıları yetkilendirilmedi" sayacı tarafından kapsanmayan bir güvenlik sorunu nedeniyle reddedilen olduğunda bu sayaç artırılır.</span><span class="sxs-lookup"><span data-stu-id="307d4-105">This counter is incremented whenever a message is rejected due to a security problem not covered by the "Security Calls Not Authorized" counter.</span></span> <span data-ttu-id="307d4-106">Bu tür sorunlar içerir:</span><span class="sxs-lookup"><span data-stu-id="307d4-106">Such problems include:</span></span>  
  
-   <span data-ttu-id="307d4-107">İstemci belirteci iletiden okunamıyor.</span><span class="sxs-lookup"><span data-stu-id="307d4-107">Client token cannot be read from the message.</span></span>  
  
-   <span data-ttu-id="307d4-108">İstemci belirteci kimlik doğrulaması (örneğin, hatalı parola) başarısız oldu.</span><span class="sxs-lookup"><span data-stu-id="307d4-108">Client token has failed authentication (for example, bad password).</span></span>  
  
-   <span data-ttu-id="307d4-109">İmza doğrulaması başarısız oldu (örneğin, ileti değiştirilmiş).</span><span class="sxs-lookup"><span data-stu-id="307d4-109">Signature verification has failed (for example, the message has been tampered).</span></span>  
  
-   <span data-ttu-id="307d4-110">İleti yeniden yürütme saldırı sırasında gerçekleşebilir bir önceki bir yineleniyor.</span><span class="sxs-lookup"><span data-stu-id="307d4-110">The message is a duplicate from a previous one, which can happen during a replay attack.</span></span>  
  
-   <span data-ttu-id="307d4-111">Bir şifre çözme hatası oluştu.</span><span class="sxs-lookup"><span data-stu-id="307d4-111">A decryption failure has occurred.</span></span>  
  
-   <span data-ttu-id="307d4-112">Gereken bazı iletiden öğeleri (örneğin, eksik zaman damgası veya engelleme şifrelenmiş veriler) eksik.</span><span class="sxs-lookup"><span data-stu-id="307d4-112">Some required elements (for example, missing timestamp or encrypted data block) are missing from the message.</span></span>  
  
-   <span data-ttu-id="307d4-113">TLSNEGO/SPNEGO anlaşması sırasında hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="307d4-113">Errors have occurred during TLSNEGO/SPNEGO handshake.</span></span>
