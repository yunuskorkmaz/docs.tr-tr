---
ms.openlocfilehash: abef47c64a7cfd99c5b50bf2100401a2d5fcc5c3
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614738"
---
### <a name="x509certificateclaimsetfindclaims-considers-all-claimtypes"></a>X509CertificateClaimSet. Findclaim tüm claimTypes 'ı kabul eder

#### <a name="details"></a>Ayrıntılar

.NET Framework 4.6.1 hedefleyen uygulamalarda, bir x509 talep kümesi, SAN alanında birden çok DNS girişi olan bir sertifikadan başlatılmışsa, <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims(System.String,System.String)?displayProperty=fullName> yöntemi tüm DNS girişleriyle birlikte ClaimType bağımsız değişkenini eşleştirmeye çalışır. .NET Framework önceki sürümlerini hedefleyen uygulamalar için, <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims(System.String,System.String)?displayProperty=fullName> yöntemi yalnızca son DNS girdisiyle birlikte ClaimType bağımsız değişkenini eşleştirmeye çalışır.

#### <a name="suggestion"></a>Öneri

Bu değişiklik yalnızca .NET Framework 4.6.1 hedefleyen uygulamaları etkiler. Bu değişiklik, [Disablemultiplednsendenemeler](~/docs/framework/migration-guide/mitigation-x509certificateclaimset-findclaims-method.md#mitigation) uyumluluk anahtarıyla devre dışı bırakılabilir (veya ön 4.6.1 hedefleniyorsa etkinleştirilebilir).

| Name    | Değer       |
|:--------|:------------|
| Kapsam   | İkincil       |
| Sürüm | 4.6.1       |
| Tür    | Yeniden Hedefleme |

#### <a name="affected-apis"></a>Etkilenen API’ler

- <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims(System.String,System.String)?displayProperty=nameWithType>
