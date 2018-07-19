### <a name="x509certificateclaimsetfindclaims-considers-all-claimtypes"></a>Tüm claimTypes X509CertificateClaimSet.FindClaims göz önünde bulundurur

|   |   |
|---|---|
|Ayrıntılar|Birden çok DNS girişi, SAN alanına sahip bir sertifika talep kümesi başlatılan x X509, .NET Framework 4.6.1'i hedefleyen uygulamalarda <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims(System.String,System.String)?displayProperty=name> claimType bağımsız değişkeniyle tüm DNS girişlerini eşleştirilecek yöntem çalışır. .NET Framework'ün önceki sürümlerini hedefleyen uygulamalar için <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims(System.String,System.String)?displayProperty=name> yöntemi claimType bağımsız değişkeni yalnızca son DNS girişi ile eşleşen dener.|
|Öneri|Bu değişiklik, yalnızca .NET Framework 4.6.1'i hedefleyen uygulamaları etkiler. Bu değişiklik devre dışı bırakılabilir (veya etkin hedefleyen pre-4.6.1) ile [DisableMultipleDNSEntries](~/docs/framework/migration-guide/mitigation-x509certificateclaimset-findclaims-method.md#mitigation) uyumluluk anahtarı.|
|Kapsam|Küçük|
|Sürüm|4.6.1|
|Tür|Yeniden hedefleme|
|Etkilenen API'leri|<ul><li><xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims(System.String,System.String)?displayProperty=nameWithType></li></ul>|

