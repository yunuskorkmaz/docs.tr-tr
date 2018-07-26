### <a name="allow-unicode-in-uris-that-resemble-unc-shares"></a>Unicode UNC paylaşımlarını benzer bir URI'leri izin ver

|   |   |
|---|---|
|Ayrıntılar|İçinde <xref:System.Uri?displayProperty=fullName>, bir dosya oluşturmak URI içeren iki UNC paylaşım adını ve Unicode karakterler artık sonuçlanır geçersiz iç durum ile bir URI. Yalnızca aşağıdakilerin tümü doğru olduğunda davranışı değiştirir:<ul><li>URI şeması bulunuyor <code>file:</code> ve dört veya daha fazla eğik çizgiyle izlenir.</li><li>Ana bilgisayar adı, alt çizgi veya başka ayrılmamış bir simge ile başlar.</li><li>URI, Unicode karakterler içeriyor.</li></ul>|
|Öneri|Tutarlı bir şekilde Unicode karakterler içeren URI'leri ile çalışan uygulamalar, kısıtlanmamışsa UNC paylaşımlarına başvuruları engellemek için bu davranışı kullanabilirdiniz. Bu uygulamaların kullanması gereken <xref:System.Uri.IsUnc> yerine.|
|Kapsam|Kenar|
|Sürüm|4.7.2|
|Tür|Çalışma zamanı|
|Etkilenen API'leri|<ul><li><xref:System.Uri?displayProperty=nameWithType></li></ul>|

