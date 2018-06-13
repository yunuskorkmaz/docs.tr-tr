---
title: 'Hizmet: Güvenlik Doğrulaması ve Kimlik Doğrulaması Hataları'
ms.date: 03/30/2017
ms.assetid: 55c98268-b1ad-459d-851b-25ef52248187
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: e160b014b7aa7586566073b800084d44be15ccaf
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33474408"
---
# <a name="service-security-validation-and-authentication-failures"></a><span data-ttu-id="20b91-102">Hizmet: Güvenlik Doğrulaması ve Kimlik Doğrulaması Hataları</span><span class="sxs-lookup"><span data-stu-id="20b91-102">Service: Security Validation and Authentication Failures</span></span>
<span data-ttu-id="20b91-103">Sayaç adı: güvenlik doğrulaması ve kimlik doğrulama hataları</span><span class="sxs-lookup"><span data-stu-id="20b91-103">Counter name: Security Validation and Authentication Failures</span></span>  
  
## <a name="description"></a><span data-ttu-id="20b91-104">Açıklama</span><span class="sxs-lookup"><span data-stu-id="20b91-104">Description</span></span>  
 <span data-ttu-id="20b91-105">Bir ileti "Güvenlik çağrıları yetkilendirilmedi" sayacı tarafından kapsanmayan bir güvenlik sorunu nedeniyle reddedilen olduğunda bu sayaç artırılır.</span><span class="sxs-lookup"><span data-stu-id="20b91-105">This counter is incremented whenever a message is rejected due to a security problem not covered by the "Security Calls Not Authorized" counter.</span></span> <span data-ttu-id="20b91-106">Bu tür sorunlar içerir:</span><span class="sxs-lookup"><span data-stu-id="20b91-106">Such problems include:</span></span>  
  
-   <span data-ttu-id="20b91-107">İstemci belirteci iletiden okunamıyor.</span><span class="sxs-lookup"><span data-stu-id="20b91-107">Client token cannot be read from the message.</span></span>  
  
-   <span data-ttu-id="20b91-108">İstemci belirteci kimlik doğrulaması (örneğin, hatalı parola) başarısız oldu.</span><span class="sxs-lookup"><span data-stu-id="20b91-108">Client token has failed authentication (for example,, bad password).</span></span>  
  
-   <span data-ttu-id="20b91-109">İmza doğrulaması başarısız oldu (örneğin, ileti değiştirilmiş).</span><span class="sxs-lookup"><span data-stu-id="20b91-109">Signature verification has failed (for example,, the message has been tampered).</span></span>  
  
-   <span data-ttu-id="20b91-110">İleti yeniden yürütme saldırı sırasında gerçekleşebilir bir önceki bir yineleniyor.</span><span class="sxs-lookup"><span data-stu-id="20b91-110">The message is a duplicate from a previous one, which can happen during a replay attack.</span></span>  
  
-   <span data-ttu-id="20b91-111">Bir şifre çözme hatası oluştu.</span><span class="sxs-lookup"><span data-stu-id="20b91-111">A decryption failure has occurred.</span></span>  
  
-   <span data-ttu-id="20b91-112">Gereken bazı iletiden öğeleri (örneğin, eksik zaman damgası veya engelleme şifrelenmiş veriler) eksik.</span><span class="sxs-lookup"><span data-stu-id="20b91-112">Some required elements (for example,, missing timestamp or encrypted data block) are missing from the message.</span></span>  
  
-   <span data-ttu-id="20b91-113">TLSNEGO/SPNEGO anlaşması sırasında hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="20b91-113">Errors have occurred during TLSNEGO/SPNEGO handshake.</span></span>
