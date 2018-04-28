### <a name="systemuriiswellformeduristring-method-returns-false-for-relative-uris-with-a-colon-char-in-first-segment"></a>İki nokta üst üste char ilk kesimdeki ile göreli URI'ler için System.Uri.IsWellFormedUriString yöntemi false döndürür

|   |   |
|---|---|
|Ayrıntılar|.NET Framework 4.5 ile başlayan <xref:System.Uri.IsWellFormedUriString(System.String,System.UriKind)> ile göreli URI'ler değerlendirir bir <code>:</code> düzgün biçimlendirilmemiş gibi kendi ilk kesimindeki. Bu farklıdır <xref:System.Uri.IsWellFormedUriString(System.String,System.UriKind)?displayProperty=name> RFC3986 için uygun olması için yapılan .NET Framework 4.0 davranışı.|
|Öneri|Bu değişikliği (gibi diğer birçok URI değişikliği), yalnızca .NET Framework 4.5 (veya üzeri) hedefleme uygulamaları etkiler. Eski davranışı kullanmaya devam etmek için uygulamayı .NET Framework 4.0 karşı hedefleyin. Alternatif olarak, önce arama URI'si tarama <xref:System.Uri.IsWellFormedUriString(System.String,System.UriKind)?displayProperty=name> aramakta <code>:</code> eski davranışı arzu ise, doğrulama amacıyla, kaldırmak istediğiniz karakterler.|
|Kapsam|Küçük|
|Sürüm|4,5|
|Tür|Yeniden hedefleme|
|Etkilenen API'leri|<ul><li><xref:System.Uri.IsWellFormedUriString(System.String,System.UriKind)?displayProperty=nameWithType></li></ul>|

