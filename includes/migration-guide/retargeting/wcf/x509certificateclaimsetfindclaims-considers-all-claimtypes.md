---
ms.openlocfilehash: fe5dfa0b8866debd8a6091a264e251f2fd2e4dca
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59234575"
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
