---
title: Güvenlik Doğrulama ve Kimlik Doğrulama Hataları
ms.date: 03/30/2017
ms.assetid: 0d4e3666-dfc6-421c-baf8-9479c22f7050
ms.openlocfilehash: 32a7d41f93dd99f1950a073e1cac1b62177ff6c3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61916051"
---
# <a name="security-validation-and-authentication-failures"></a><span data-ttu-id="83ee1-102">Güvenlik Doğrulama ve Kimlik Doğrulama Hataları</span><span class="sxs-lookup"><span data-stu-id="83ee1-102">Security Validation and Authentication Failures</span></span>
<span data-ttu-id="83ee1-103">Sayaç adı: Güvenlik Doğrulama ve Kimlik Doğrulama Hataları</span><span class="sxs-lookup"><span data-stu-id="83ee1-103">Counter name: Security Validation and Authentication Failures</span></span>  
  
## <a name="description"></a><span data-ttu-id="83ee1-104">Açıklama</span><span class="sxs-lookup"><span data-stu-id="83ee1-104">Description</span></span>  
 <span data-ttu-id="83ee1-105">Her bir ileti "Güvenlik çağrıları yetkilendirilmedi" sayacı tarafından kapsanmayan bir güvenlik sorunu nedeniyle reddedilmesi Bu sayaç artırılır.</span><span class="sxs-lookup"><span data-stu-id="83ee1-105">This counter is incremented whenever a message is rejected due to a security problem not covered by the "Security Calls Not Authorized" counter.</span></span> <span data-ttu-id="83ee1-106">Bu tür sorunlar şunlardır:</span><span class="sxs-lookup"><span data-stu-id="83ee1-106">Such problems include:</span></span>  
  
- <span data-ttu-id="83ee1-107">İstemci belirteci iletiden okunamıyor.</span><span class="sxs-lookup"><span data-stu-id="83ee1-107">Client token cannot be read from the message.</span></span>  
  
- <span data-ttu-id="83ee1-108">İstemci belirteci (örneğin, hatalı parola) kimlik doğrulaması başarısız oldu.</span><span class="sxs-lookup"><span data-stu-id="83ee1-108">Client token has failed authentication (for example, bad password).</span></span>  
  
- <span data-ttu-id="83ee1-109">İmza doğrulaması başarısız oldu (örneğin, iletiyi oynanmadığını).</span><span class="sxs-lookup"><span data-stu-id="83ee1-109">Signature verification has failed (for example, the message has been tampered).</span></span>  
  
- <span data-ttu-id="83ee1-110">İleti yeniden yürütme bir saldırı sırasında gerçekleşebilir bir önceki bir yineleniyor.</span><span class="sxs-lookup"><span data-stu-id="83ee1-110">The message is a duplicate from a previous one, which can happen during a replay attack.</span></span>  
  
- <span data-ttu-id="83ee1-111">Bir şifre çözme hatası oluştu.</span><span class="sxs-lookup"><span data-stu-id="83ee1-111">A decryption failure has occurred.</span></span>  
  
- <span data-ttu-id="83ee1-112">Gereken bazı öğeleri (örneğin, eksik bir zaman damgası veya şifrelenmiş veriler engelle) gelen iletiyi yok.</span><span class="sxs-lookup"><span data-stu-id="83ee1-112">Some required elements (for example, missing timestamp or encrypted data block) are missing from the message.</span></span>  
  
- <span data-ttu-id="83ee1-113">TLSNEGO/SPNEGO anlaşması sırasında hatalar oluştu.</span><span class="sxs-lookup"><span data-stu-id="83ee1-113">Errors have occurred during TLSNEGO/SPNEGO handshake.</span></span>
