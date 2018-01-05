---
title: "Güvenlik Doğrulama ve Kimlik Doğrulama Hataları"
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
ms.workload: dotnet
ms.openlocfilehash: c52b54d2be2e824de478e0ee9ec2452c57e181b4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="security-validation-and-authentication-failures"></a><span data-ttu-id="a30b3-102">Güvenlik Doğrulama ve Kimlik Doğrulama Hataları</span><span class="sxs-lookup"><span data-stu-id="a30b3-102">Security Validation and Authentication Failures</span></span>
<span data-ttu-id="a30b3-103">Sayaç adı: güvenlik doğrulaması ve kimlik doğrulama hataları</span><span class="sxs-lookup"><span data-stu-id="a30b3-103">Counter name: Security Validation and Authentication Failures</span></span>  
  
## <a name="description"></a><span data-ttu-id="a30b3-104">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a30b3-104">Description</span></span>  
 <span data-ttu-id="a30b3-105">Bir ileti "Güvenlik çağrıları yetkilendirilmedi" sayacı tarafından kapsanmayan bir güvenlik sorunu nedeniyle reddedilen olduğunda bu sayaç artırılır.</span><span class="sxs-lookup"><span data-stu-id="a30b3-105">This counter is incremented whenever a message is rejected due to a security problem not covered by the "Security Calls Not Authorized" counter.</span></span> <span data-ttu-id="a30b3-106">Bu tür sorunlar içerir:</span><span class="sxs-lookup"><span data-stu-id="a30b3-106">Such problems include:</span></span>  
  
-   <span data-ttu-id="a30b3-107">İstemci belirteci iletiden okunamıyor.</span><span class="sxs-lookup"><span data-stu-id="a30b3-107">Client token cannot be read from the message.</span></span>  
  
-   <span data-ttu-id="a30b3-108">İstemci belirteci kimlik doğrulaması (örneğin, hatalı parola) başarısız oldu.</span><span class="sxs-lookup"><span data-stu-id="a30b3-108">Client token has failed authentication (for example, bad password).</span></span>  
  
-   <span data-ttu-id="a30b3-109">İmza doğrulaması başarısız oldu (örneğin, ileti değiştirilmiş).</span><span class="sxs-lookup"><span data-stu-id="a30b3-109">Signature verification has failed (for example, the message has been tampered).</span></span>  
  
-   <span data-ttu-id="a30b3-110">İleti yeniden yürütme saldırı sırasında gerçekleşebilir bir önceki bir yineleniyor.</span><span class="sxs-lookup"><span data-stu-id="a30b3-110">The message is a duplicate from a previous one, which can happen during a replay attack.</span></span>  
  
-   <span data-ttu-id="a30b3-111">Bir şifre çözme hatası oluştu.</span><span class="sxs-lookup"><span data-stu-id="a30b3-111">A decryption failure has occurred.</span></span>  
  
-   <span data-ttu-id="a30b3-112">Gereken bazı iletiden öğeleri (örneğin, eksik zaman damgası veya engelleme şifrelenmiş veriler) eksik.</span><span class="sxs-lookup"><span data-stu-id="a30b3-112">Some required elements (for example, missing timestamp or encrypted data block) are missing from the message.</span></span>  
  
-   <span data-ttu-id="a30b3-113">TLSNEGO/SPNEGO anlaşması sırasında hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="a30b3-113">Errors have occurred during TLSNEGO/SPNEGO handshake.</span></span>
