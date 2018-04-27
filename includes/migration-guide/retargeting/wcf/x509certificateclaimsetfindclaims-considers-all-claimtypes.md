### <a name="x509certificateclaimsetfindclaims-considers-all-claimtypes"></a>X509CertificateClaimSet.FindClaims tüm claimTypes göz önünde bulundurur.

|   |   |
|---|---|
|Ayrıntılar|.NET Framework 4.6.1, talep kümesi, birden çok DNS girişlerini, SAN alanında bulunan bir sertifikadan başlatılır X509 hedef uygulamalarda <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims(System.String,System.String)?displayProperty=name> yöntemi, tüm DNS girişlerini claimType değişkeniyle eşleşecek şekilde çalışır. .NET Framework'ün önceki sürümlerini hedefleyen uygulamalar için <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims(System.String,System.String)?displayProperty=name> yöntemi claimType bağımsız değişkeni yalnızca son DNS girişi ile eşleşen dener.|
|Öneri|Bu değişiklik, yalnızca .NET Framework 4.6.1 hedefleme uygulamaları etkiler. Bu değişiklik devre dışı olabilir (veya etkin atamak pre-4.6.1) ile [DisableMultipleDNSEntries](~/docs/framework/migration-guide/mitigation-x509certificateclaimset-findclaims-method.md#mitigation) uyumluluk anahtarı.|
|Kapsam|Küçük|
|Sürüm|4.6.1|
|Tür|Yeniden hedefleme|
|Etkilenen API'leri|<ul><li><xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims(System.String,System.String)?displayProperty=nameWithType></li></ul>|

