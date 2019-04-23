---
ms.openlocfilehash: fe5dfa0b8866debd8a6091a264e251f2fd2e4dca
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59805291"
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
