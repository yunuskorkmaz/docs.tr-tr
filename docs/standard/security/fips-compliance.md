---
title: FIPS uyumluluğu-.NET Core
description: .NET Core Federal bilgi Işleme standardı (FIPS) uyumluluğunu açıklar.
ms.date: 11/20/2019
author: Rick-Anderson
ms.author: riande
ms.openlocfilehash: 84d6edc6975af0484bb67999ad5891eaf4db057d
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/26/2020
ms.locfileid: "77626964"
---
# <a name="net-core-federal-information-processing-standard-fips-compliance"></a><span data-ttu-id="1bbaf-103">.NET Core Federal bilgi Işleme standardı (FIPS) uyumluluğu</span><span class="sxs-lookup"><span data-stu-id="1bbaf-103">.NET Core Federal Information Processing Standard (FIPS) compliance</span></span>

<span data-ttu-id="1bbaf-104">Federal bilgi Işleme standardı (FIPS) yayını 140-2, bilgilerin 5131 bölümünde tanımlandığı gibi, bilgi teknolojisi ürünlerinde şifreleme modülleri için en düşük güvenlik gereksinimlerini tanımlayan bir ABD devlet standardıdır. Teknoloji Yönetimi 1996 üzerinde çalışır.</span><span class="sxs-lookup"><span data-stu-id="1bbaf-104">The Federal Information Processing Standard (FIPS) Publication 140-2 is a U.S. government standard that defines minimum security requirements for cryptographic modules in information technology products, as defined in Section 5131 of the Information Technology Management Reform Act of 1996.</span></span>

<span data-ttu-id="1bbaf-105">.NET Core:</span><span class="sxs-lookup"><span data-stu-id="1bbaf-105">.NET Core:</span></span>

* <span data-ttu-id="1bbaf-106">, Temel alınan işletim sisteminin sağladığı standart modüllere şifreleme temel öğelerini iletir.</span><span class="sxs-lookup"><span data-stu-id="1bbaf-106">Passes cryptographic primitives calls through to the standard modules the underlying operating system provides.</span></span>
* <span data-ttu-id="1bbaf-107">, .NET Core uygulamalarında FIPS onaylı algoritmaların veya anahtar boyutlarının **kullanımını zorunlu kılmaz** .</span><span class="sxs-lookup"><span data-stu-id="1bbaf-107">Does **not** enforce the use of FIPS Approved algorithms or key sizes in .NET Core apps.</span></span>

<span data-ttu-id="1bbaf-108">Sistem Yöneticisi, bir işletim sistemi için FIPS uyumluluğunu yapılandırmadan sorumludur.</span><span class="sxs-lookup"><span data-stu-id="1bbaf-108">The system administrator is responsible for configuring the FIPS compliance for an operating system.</span></span>

<span data-ttu-id="1bbaf-109">Kod FIPS uyumlu bir ortam için yazılmışsa, uyumlu olmayan FIPS algoritmalarının kullanılmadığından emin olmak için geliştirici sorumludur.</span><span class="sxs-lookup"><span data-stu-id="1bbaf-109">If code is written for a FIPS-compliant environment, the developer is responsible for ensuring that non-compliant FIPS algorithms aren't used.</span></span>

<span data-ttu-id="1bbaf-110">FIPS uyumluluğu hakkında daha fazla bilgi için aşağıdaki makalelere bakın:</span><span class="sxs-lookup"><span data-stu-id="1bbaf-110">For more information on FIPS compliance, see the following articles:</span></span>

* [<span data-ttu-id="1bbaf-111">Windows FIPS uyumluluğu</span><span class="sxs-lookup"><span data-stu-id="1bbaf-111">Windows FIPS Compliance</span></span>](/windows/security/threat-protection/fips-140-validation)
* [<span data-ttu-id="1bbaf-112">Windows 'un FIPS uyumluluğu için yapılandırılması</span><span class="sxs-lookup"><span data-stu-id="1bbaf-112">Configuring Windows for FIPS Compliance</span></span>](/windows/security/threat-protection/security-policy-settings/system-cryptography-use-fips-compliant-algorithms-for-encryption-hashing-and-signing)
* [<span data-ttu-id="1bbaf-113">Bölüm 8. Federal standartlar ve yönetmelikler Red Hat Enterprise Linux 7</span><span class="sxs-lookup"><span data-stu-id="1bbaf-113">Chapter 8. Federal Standards and Regulations Red Hat Enterprise Linux 7</span></span>](https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/7/html/security_guide/chap-federal_standards_and_regulations)
