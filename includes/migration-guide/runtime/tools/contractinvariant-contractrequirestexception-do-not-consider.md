### <a name="contractinvariant-or-contractrequirestexception-do-not-consider-stringisnullorempty-to-be-pure"></a>Contract.Invariant veya Contract.Requires<TException> saf olmasını String.IsNullOrEmpty dikkate almaz

|   |   |
|---|---|
|Ayrıntılar|Değişmez değer için Sözleşme, .NET Framework 4.6.1, hedefleyen uygulamalar için <xref:System.Diagnostics.Contracts.Contract.Invariant%2A?displayProperty=nameWithType> veya önkoşulu sözleşmesine <xref:System.Diagnostics.Contracts.Contract.Requires%2A?displayProperty=nameWithType)> çağrıları <xref:System.String.IsNullOrEmpty%2A?displayProperty=nameWithType> yöntemi, yeniden yazan yayar CC1036 uyarı derleyici: &quot;algılanan yöntemine yapılan çağrı ' System.String.IsNullOrWhteSpace(System.String)' [saf] olmadan yöntemi.&quot; Derleyici Hatası yerine uyarı derleyici budur.|
|Öneri|Bu davranış, giderilmiş [GitHub sorunu #339](https://github.com/Microsoft/CodeContracts/issues/339). Bu uyarı ortadan kaldırmak için indirebilir ve güncelleştirilmiş sürümünü kod sözleşmeleri aracından için kaynak kodu derleme [GitHub](https://github.com/Microsoft/CodeContracts/blob/master/README.md). İndirme bilgileri sayfasının en altında bulundu.|
|Kapsam|Küçük|
|Sürüm|4.6.1|
|Tür|Çalışma zamanı|
|Etkilenen API'leri|<ul><li><xref:System.Diagnostics.Contracts.Contract.Invariant(System.Boolean)?displayProperty=nameWithType></li><li><xref:System.Diagnostics.Contracts.Contract.Requires(System.Boolean)?displayProperty=nameWithType></li></ul>|

