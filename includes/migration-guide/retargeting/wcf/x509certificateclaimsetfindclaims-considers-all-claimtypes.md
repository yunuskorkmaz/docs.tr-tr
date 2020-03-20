---
ms.openlocfilehash: 9678c077e278a9d76ffd5c2ce10e63ebe3ad09f7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "68235619"
---
### <a name="x509certificateclaimsetfindclaims-considers-all-claimtypes"></a>X509CertificateClaimSet.FindClaims Tüm claimTypes dikkate

|   |   |
|---|---|
|Ayrıntılar|.NET Framework 4.6.1'i hedefleyen uygulamalarda, Bir X509 talep kümesi SAN alanında birden çok DNS <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims(System.String,System.String)?displayProperty=name> girişi olan bir sertifikadan başharfe atılırsa, yöntem claimType bağımsız değişkenini tüm DNS girişleriyle eşleştirmeye çalışır. .NET Framework'ün önceki sürümlerini hedefleyen <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims(System.String,System.String)?displayProperty=name> uygulamalar için yöntem, claimType bağımsız değişkenini yalnızca son DNS girişiyle eşleştirmeyi dener.|
|Öneri|Bu değişiklik yalnızca .NET Framework 4.6.1'i hedefleyen uygulamaları etkiler. Bu değişiklik Devre Dışı [BırakılmışNSEntries](~/docs/framework/migration-guide/mitigation-x509certificateclaimset-findclaims-method.md#mitigation) uyumluluk anahtarıyla devre dışı bırakılmış (veya 4.6.1 öncesi targetting ise etkinleştirilmiş) olabilir.|
|Kapsam|İkincil|
|Sürüm|4.6.1|
|Tür|Yeniden Hedefleme|
|Etkilenen API’ler|<ul><li><xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims(System.String,System.String)?displayProperty=nameWithType></li></ul>|
