---
ms.openlocfilehash: 7e42a294b151d07a6fdc61308cdf92df7a31a1d6
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614726"
---
### <a name="deflatestream-uses-native-apis-for-decompression"></a>DeflateStream, açma için yerel API 'Ler kullanır

#### <a name="details"></a>Ayrıntılar

.NET Framework 4.7.2 başlayarak, sınıfında açma işlemi, `T:System.IO.Compression.DeflateStream` Varsayılan olarak yerel Windows API 'lerini kullanacak şekilde değiştirilmiştir. Genellikle bu, önemli ölçüde performans geliştirmesine neden olur. .NET Framework sürüm 4.7.2 veya üstünü hedefleyen tüm .NET uygulamaları yerel uygulamayı kullanır. Bu değişiklik davranıştaki bazı farklılıklar oluşmasına neden olur ve şunları içerir:

- Özel durum iletileri farklı olabilir. Ancak, atılan özel durum türü aynı kalır.
- Bir işlemi tamamlamaya yetecek kadar bellek olmaması gibi bazı özel durumlar farklı şekilde işlenebilir.
- Gzip üst bilgisini ayrıştırmak için bilinen farklar vardır (Note: yalnızca `GZipStream` açma için ayarlanan) etkilenir:
- Geçersiz üstbilgileri ayrıştırırken özel durumlar farklı zamanlarda oluşturulabilir.
- Yerel uygulama, gzip üst bilgisindeki (yani [FLG](http://www.zlib.org/rfc-gzip.html#header-trailer)) bazı ayrılmış bayraklar için bu değerleri, daha önce geçersiz değerlerin yoksayıldığı bir özel durum oluşturulmasına neden olabilen, belirtime göre ayarlanır.

#### <a name="suggestion"></a>Öneri

Yerel API 'Ler ile açma, uygulamanızın davranışını olumsuz yönde etkileiyorsa, `Switch.System.IO.Compression.DoNotUseNativeZipLibraryForDecompression` `runtime` app.config dosyanızın bölümüne anahtarı ekleyerek ve ayarlarını yaparak bu özelliği devre dışı bırakabilirsiniz `true` :

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
  <runtime>
    <AppContextSwitchOverrides value="Switch.System.IO.Compression.DoNotUseNativeZipLibraryForDecompression=true" />
  </runtime>
</configuration>
```

| Name    | Değer       |
|:--------|:------------|
| Kapsam   | İkincil       |
| Sürüm | 4.7.2       |
| Tür    | Yeniden Hedefleme |

#### <a name="affected-apis"></a>Etkilenen API’ler

- <xref:System.IO.Compression.DeflateStream?displayProperty=nameWithType>
- <xref:System.IO.Compression.GZipStream?displayProperty=nameWithType>
