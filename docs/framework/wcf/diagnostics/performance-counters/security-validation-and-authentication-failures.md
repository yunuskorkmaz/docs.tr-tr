---
title: "Güvenlik Doğrulaması ve Kimlik Doğrulaması Hataları"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0d4e3666-dfc6-421c-baf8-9479c22f7050
caps.latest.revision: "8"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: c1d448d709c7ad20e9d08a291f5a38546cd93ce4
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="security-validation-and-authentication-failures"></a><span data-ttu-id="6f65d-102">Güvenlik Doğrulaması ve Kimlik Doğrulaması Hataları</span><span class="sxs-lookup"><span data-stu-id="6f65d-102">Security Validation and Authentication Failures</span></span>
<span data-ttu-id="6f65d-103">Sayaç adı: güvenlik doğrulaması ve kimlik doğrulama hataları</span><span class="sxs-lookup"><span data-stu-id="6f65d-103">Counter name: Security Validation and Authentication Failures</span></span>  
  
## <a name="description"></a><span data-ttu-id="6f65d-104">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6f65d-104">Description</span></span>  
 <span data-ttu-id="6f65d-105">Bir ileti "Güvenlik çağrıları yetkilendirilmedi" sayacı tarafından kapsanmayan bir güvenlik sorunu nedeniyle reddedilen olduğunda bu sayaç artırılır.</span><span class="sxs-lookup"><span data-stu-id="6f65d-105">This counter is incremented whenever a message is rejected due to a security problem not covered by the "Security Calls Not Authorized" counter.</span></span> <span data-ttu-id="6f65d-106">Bu tür sorunlar içerir:</span><span class="sxs-lookup"><span data-stu-id="6f65d-106">Such problems include:</span></span>  
  
-   <span data-ttu-id="6f65d-107">İstemci belirteci iletiden okunamıyor.</span><span class="sxs-lookup"><span data-stu-id="6f65d-107">Client token cannot be read from the message.</span></span>  
  
-   <span data-ttu-id="6f65d-108">İstemci belirteci kimlik doğrulaması (örneğin, hatalı parola) başarısız oldu.</span><span class="sxs-lookup"><span data-stu-id="6f65d-108">Client token has failed authentication (for example, bad password).</span></span>  
  
-   <span data-ttu-id="6f65d-109">İmza doğrulaması başarısız oldu (örneğin, ileti değiştirilmiş).</span><span class="sxs-lookup"><span data-stu-id="6f65d-109">Signature verification has failed (for example, the message has been tampered).</span></span>  
  
-   <span data-ttu-id="6f65d-110">İleti yeniden yürütme saldırı sırasında gerçekleşebilir bir önceki bir yineleniyor.</span><span class="sxs-lookup"><span data-stu-id="6f65d-110">The message is a duplicate from a previous one, which can happen during a replay attack.</span></span>  
  
-   <span data-ttu-id="6f65d-111">Bir şifre çözme hatası oluştu.</span><span class="sxs-lookup"><span data-stu-id="6f65d-111">A decryption failure has occurred.</span></span>  
  
-   <span data-ttu-id="6f65d-112">Gereken bazı iletiden öğeleri (örneğin, eksik zaman damgası veya engelleme şifrelenmiş veriler) eksik.</span><span class="sxs-lookup"><span data-stu-id="6f65d-112">Some required elements (for example, missing timestamp or encrypted data block) are missing from the message.</span></span>  
  
-   <span data-ttu-id="6f65d-113">TLSNEGO/SPNEGO anlaşması sırasında hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="6f65d-113">Errors have occurred during TLSNEGO/SPNEGO handshake.</span></span>
