### <a name="allow-unicode-in-uris-that-resemble-unc-shares"></a>Unicode içinde UNC paylaşımlarına benzer URI'ler izin ver

|   |   |
|---|---|
|Ayrıntılar|İçinde <xref:System.Uri?displayProperty=fullName>, hem de bir UNC içeren URI'ye paylaşım adı bir dosya oluşturmak ve Unicode karakterler geçersiz iç durum ile bir URI artık sonuçlanır. Yalnızca aşağıdakilerin tümü doğru olduğunda davranışı değişir:<ul><li>URI şeması sahip <code>file:</code> ve dört veya daha fazla eğik çizgiyle izlenir.</li><li>Ana bilgisayar adı alt çizgi veya diğer ayrılmış simge ile başlar.</li><li>URI Unicode karakterler içeriyor.</li></ul>|
|Öneri|Uygulamaları tutarlı bir şekilde Unicode karakterler içeren URI ile çalışma alanlara bu davranış UNC paylaşımlarına başvuruları izin vermeyecek şekilde kullanmış. Bu uygulamaların kullanması gereken <xref:System.Uri.IsUnc> yerine.|
|Kapsam|Kenar|
|Sürüm|4.7.2|
|Tür|çalışma zamanı|
|Etkilenen API'leri|<ul><li><xref:System.Uri?displayProperty=nameWithType></li></ul>|

