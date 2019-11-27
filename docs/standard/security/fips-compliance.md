---
title: FIPS uyumluluğu-.NET Core
description: .NET Core Federal bilgi Işleme standardı (FIPS) uyumluluğunu açıklar.
ms.date: 11/20/2019
author: Rick-Anderson
ms.author: riande
ms.openlocfilehash: cf640c857e79ae811dd38d57a0e5301b7bc96572
ms.sourcegitcommit: 81ad1f09b93f3b3e6706a7f2e4ddf50ef229ea3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/20/2019
ms.locfileid: "74205068"
---
# <a name="net-core-federal-information-processing-standard-fips-compliance"></a>.NET Core Federal bilgi Işleme standardı (FIPS) uyumluluğu

Federal bilgi Işleme standardı (FIPS) yayını 140-2, bilgilerin 5131 bölümünde tanımlandığı gibi, bilgi teknolojisi ürünlerinde şifreleme modülleri için en düşük güvenlik gereksinimlerini tanımlayan bir ABD devlet standardıdır. Teknoloji Yönetimi 1996 üzerinde çalışır.

.NET Core:

* , Temel alınan işletim sisteminin sağladığı standart modüllere şifreleme temel öğelerini iletir.
* , .NET Core uygulamalarında FIPS onaylı algoritmaların veya anahtar boyutlarının **kullanımını zorunlu kılmaz** .

Sistem Yöneticisi, bir işletim sistemi için FIPS uyumluluğunu yapılandırmadan sorumludur.

Kod FIPS uyumlu bir ortam için yazılmışsa, uyumlu olmayan FIPS algoritmalarının kullanılmadığından emin olmak için geliştirici sorumludur.

FIPS uyumluluğu hakkında daha fazla bilgi için aşağıdaki makalelere bakın:

* [Windows FIPS uyumluluğu](/windows/security/threat-protection/fips-140-validation)
* [Windows 'un FIPS uyumluluğu için yapılandırılması](/windows/security/threat-protection/security-policy-settings/system-cryptography-use-fips-compliant-algorithms-for-encryption-hashing-and-signing)
* [10,2. FEDERAL BILGI IŞLEME STANDARDı (FıPS)](https://access.redhat.com/documentation/red_hat_enterprise_linux/6/html/security_guide/sect-security_guide-federal_standards_and_regulations-federal_information_processing_standard)
