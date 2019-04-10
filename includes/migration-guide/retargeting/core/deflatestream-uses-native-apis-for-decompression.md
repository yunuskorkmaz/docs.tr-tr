---
ms.openlocfilehash: 897bb0b0650c633b87a792516c62566f491ec3fd
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59234058"
---
### <a name="deflatestream-uses-native-apis-for-decompression"></a>DeflateStream yerel API'leri için sıkıştırmayı kullanır.

|   |   |
|---|---|
|Ayrıntılar|4.7.2, .NET Framework içinde açma uygulamasını başlayarak <code>T:System.IO.Compression.DeflateStream</code> sınıfı, varsayılan olarak yerel Windows API'ları kullanacak şekilde değiştirildi. Genellikle, bu önemli performans geliştirmeyle sonuçlanır. .NET Framework sürümünü 4.7.2 ya da daha yüksek kullanım yerel uygulama hedefleyen tüm .NET uygulamalar. Bu değişiklik içeren bazı farklılıklar davranış, neden olabilir:<ul><li>Özel durum iletileri farklı olabilir. Ancak, özel durum türü, aynı kalır.</li><li>Bir işlemi tamamlamak için yeterli bellek olmaması gibi bazı özel durumlarda farklı şekilde ele alınabilir.</li><li>Gzip üst bilgi ayrıştırmak için farkları bilinen vardır (Not: yalnızca <code>GZipStream</code> açma etkilenen ayarlayın):</li><li>Farklı zamanlarda özel geçersiz üstbilgileri ayrıştırılırken durumlar.</li><li>Yerel uygulama için bazı değerler bayrakları gzip üst bilgisi içinde ayrılmış uygular (yani [süre](http://www.zlib.org/rfc-gzip.html#header-trailer)) geçersiz değerler burada daha önce yoksayıldı bir özel durum oluşturmasına neden olabilecek belirtimine göre ayarlanır.</li></ul>|
|Öneri|Açma yerel API'ler ile uygulamanızın davranışını olumsuz etkilediği, bu özelliği ekleyerek seçebilirsiniz <code>Switch.System.IO.Compression.DoNotUseNativeZipLibraryForDecompression</code> geçin <code>runtime</code> app.config dosyanızı ve ayarlamak bölümünü <code>true</code>:<pre><code class="lang-xml">&lt;?xml version=&quot;1.0&quot; encoding=&quot;utf-8&quot; ?&gt;&#13;&#10;&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides&#13;&#10;value=&quot;Switch.System.IO.Compression.DoNotUseNativeZipLibraryForDecompression=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|Kapsam|İkincil|
|Sürüm|4.7.2|
|Tür|Yeniden Hedefleme|
|Etkilenen API’ler|<ul><li><xref:System.IO.Compression.DeflateStream?displayProperty=nameWithType></li><li><xref:System.IO.Compression.GZipStream?displayProperty=nameWithType></li></ul>|
