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
* [Bölüm 8. Federal standartlar ve yönetmelikler Red Hat Enterprise Linux 7](https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/7/html/security_guide/chap-federal_standards_and_regulations)
