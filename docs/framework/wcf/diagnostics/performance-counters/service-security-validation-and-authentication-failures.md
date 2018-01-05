---
title: "Hizmet: Güvenlik Doğrulaması ve Kimlik Doğrulaması Hataları"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 55c98268-b1ad-459d-851b-25ef52248187
caps.latest.revision: "7"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 50944c55525150868e5ddac9730792c10f6b975c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="service-security-validation-and-authentication-failures"></a><span data-ttu-id="9f5de-102">Hizmet: Güvenlik Doğrulaması ve Kimlik Doğrulaması Hataları</span><span class="sxs-lookup"><span data-stu-id="9f5de-102">Service: Security Validation and Authentication Failures</span></span>
<span data-ttu-id="9f5de-103">Sayaç adı: güvenlik doğrulaması ve kimlik doğrulama hataları</span><span class="sxs-lookup"><span data-stu-id="9f5de-103">Counter name: Security Validation and Authentication Failures</span></span>  
  
## <a name="description"></a><span data-ttu-id="9f5de-104">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9f5de-104">Description</span></span>  
 <span data-ttu-id="9f5de-105">Bir ileti "Güvenlik çağrıları yetkilendirilmedi" sayacı tarafından kapsanmayan bir güvenlik sorunu nedeniyle reddedilen olduğunda bu sayaç artırılır.</span><span class="sxs-lookup"><span data-stu-id="9f5de-105">This counter is incremented whenever a message is rejected due to a security problem not covered by the "Security Calls Not Authorized" counter.</span></span> <span data-ttu-id="9f5de-106">Bu tür sorunlar içerir:</span><span class="sxs-lookup"><span data-stu-id="9f5de-106">Such problems include:</span></span>  
  
-   <span data-ttu-id="9f5de-107">İstemci belirteci iletiden okunamıyor.</span><span class="sxs-lookup"><span data-stu-id="9f5de-107">Client token cannot be read from the message.</span></span>  
  
-   <span data-ttu-id="9f5de-108">İstemci belirteci kimlik doğrulaması (örneğin, hatalı parola) başarısız oldu.</span><span class="sxs-lookup"><span data-stu-id="9f5de-108">Client token has failed authentication (for example,, bad password).</span></span>  
  
-   <span data-ttu-id="9f5de-109">İmza doğrulaması başarısız oldu (örneğin, ileti değiştirilmiş).</span><span class="sxs-lookup"><span data-stu-id="9f5de-109">Signature verification has failed (for example,, the message has been tampered).</span></span>  
  
-   <span data-ttu-id="9f5de-110">İleti yeniden yürütme saldırı sırasında gerçekleşebilir bir önceki bir yineleniyor.</span><span class="sxs-lookup"><span data-stu-id="9f5de-110">The message is a duplicate from a previous one, which can happen during a replay attack.</span></span>  
  
-   <span data-ttu-id="9f5de-111">Bir şifre çözme hatası oluştu.</span><span class="sxs-lookup"><span data-stu-id="9f5de-111">A decryption failure has occurred.</span></span>  
  
-   <span data-ttu-id="9f5de-112">Gereken bazı iletiden öğeleri (örneğin, eksik zaman damgası veya engelleme şifrelenmiş veriler) eksik.</span><span class="sxs-lookup"><span data-stu-id="9f5de-112">Some required elements (for example,, missing timestamp or encrypted data block) are missing from the message.</span></span>  
  
-   <span data-ttu-id="9f5de-113">TLSNEGO/SPNEGO anlaşması sırasında hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="9f5de-113">Errors have occurred during TLSNEGO/SPNEGO handshake.</span></span>
