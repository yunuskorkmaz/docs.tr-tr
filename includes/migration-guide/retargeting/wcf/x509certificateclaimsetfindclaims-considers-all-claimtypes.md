---
ms.openlocfilehash: 878aef544b2706bfd10a3dddce1b902655ef003a
ms.sourcegitcommit: 0aca6c5d166d7961a1e354c248495645b97a1dc5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/01/2019
ms.locfileid: "58761132"
---
### <a name="x509certificateclaimsetfindclaims-considers-all-claimtypes"></a>X509CertificateClaimSet.FindClaims Considers All claimTypes

|   |   |
|---|---|
|Ayrıntılar|Birden çok DNS girişi, SAN alanına sahip bir sertifika talep kümesi başlatılan x X509, .NET Framework 4.6.1'i hedefleyen uygulamalarda <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims(System.String,System.String)?displayProperty=name> claimType bağımsız değişkeniyle tüm DNS girişlerini eşleştirilecek yöntem çalışır. .NET Framework'ün önceki sürümlerini hedefleyen uygulamalar için <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims(System.String,System.String)?displayProperty=name> yöntemi claimType bağımsız değişkeni yalnızca son DNS girişi ile eşleşen dener.|
|Öneri|Bu değişiklik, yalnızca .NET Framework 4.6.1'i hedefleyen uygulamaları etkiler. Bu değişiklik devre dışı bırakılabilir (veya öncesi 4.6.1 targeting etkin) ile [DisableMultipleDNSEntries](~/docs/framework/migration-guide/mitigation-x509certificateclaimset-findclaims-method.md#mitigation) uyumluluk anahtarı.|
|Kapsam|İkincil|
|Sürüm|4.6.1|
|Tür|Yeniden Hedefleme|
|Etkilenen API’ler|<ul><li><xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims(System.String,System.String)?displayProperty=nameWithType></li></ul>|

