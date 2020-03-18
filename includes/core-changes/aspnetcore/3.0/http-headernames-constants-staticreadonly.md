---
ms.openlocfilehash: 31e7f84a787d255a474f4c2b1fa3068903dbed52
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75901700"
---
### <a name="http-headernames-constants-changed-to-static-readonly"></a>HTTP: BaşlıkAdları sabitleri yalnızca statik okunur olarak değiştirildi

Core 3.0 Preview 5ASP.NET'den <xref:Microsoft.Net.Http.Headers.HeaderNames?displayProperty=fullName> `const` başlayarak, `static readonly`'deki alanlar .

Tartışma için [dotnet/aspnetcore#9514'e](https://github.com/dotnet/aspnetcore/issues/9514)bakın.

#### <a name="version-introduced"></a>Sürüm tanıtıldı

3,0

#### <a name="old-behavior"></a>Eski davranış

Bu alanlar `const`eskiden.

#### <a name="new-behavior"></a>Yeni davranış

Bu alanlar `static readonly`artık.

#### <a name="reason-for-change"></a>Değişiklik nedeni

Değişiklik:

* Değerlerin montaj sınırları nın ötesine gömülmesini önler ve gerektiğinde değer düzeltmelerine olanak sağlar.
* Daha hızlı başvuru eşitliği denetimleri sağlar.

#### <a name="recommended-action"></a>Önerilen eylem

3.0'a karşı yeniden derle. Bu alanları aşağıdaki yollarla kullanan kaynak kodu artık bunu yapamaz:

* Öznitelik bağımsız değişkeni olarak
* `case` Bir `switch` açıklamada olduğu gibi
* Başka bir tanımlama`const`

Kesme değişikliğini aşmak için, kendi tanımladığı üstbilgi adı sabitlerini veya dize gerçeklerini kullanmaya geçin.

#### <a name="category"></a>Kategori

ASP.NET Çekirdeği

#### <a name="affected-apis"></a>Etkilenen API’ler

<xref:Microsoft.Net.Http.Headers.HeaderNames?displayProperty=fullName>

<!-- 

#### Affected APIs

`T:Microsoft.Net.Http.Headers.HeaderNames`

-->
