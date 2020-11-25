---
ms.openlocfilehash: 31e7f84a787d255a474f4c2b1fa3068903dbed52
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/25/2020
ms.locfileid: "96032764"
---
### <a name="http-headernames-constants-changed-to-static-readonly"></a>HTTP: HeaderNames sabitleri statik ReadOnly olarak değiştirildi

ASP.NET Core 3,0 Preview 5 ' ten başlayarak, içindeki alanlar <xref:Microsoft.Net.Http.Headers.HeaderNames?displayProperty=fullName> olarak değişir `const` `static readonly` .

Tartışma için bkz. [DotNet/aspnetcore # 9514](https://github.com/dotnet/aspnetcore/issues/9514).

#### <a name="version-introduced"></a>Sunulan sürüm

3,0

#### <a name="old-behavior"></a>Eski davranış

Bu alanlar için kullanılır `const` .

#### <a name="new-behavior"></a>Yeni davranış

Bu alanlar artık `static readonly` .

#### <a name="reason-for-change"></a>Değişiklik nedeni

Değişiklik:

* Değerlerin, gerektiğinde değer düzeltmeleri için derleme sınırları arasında gömülmesini önler.
* Daha hızlı başvuru eşitlik denetimleri sağlar.

#### <a name="recommended-action"></a>Önerilen eylem

3,0 ile yeniden derleyin. Aşağıdaki yollarla bu alanları kullanan kaynak kodu bundan böyle devam edebilir:

* Öznitelik bağımsız değişkeni olarak
* Bir `case` `switch` bildirimde olarak
* Başka bir tanımlama `const`

Son değişikliği geçici olarak çözmek için, kendi kendine tanımlanmış üst bilgi adı sabitleri veya dize sabit değerlerini kullanmaya geçin.

#### <a name="category"></a>Kategori

ASP.NET Core

#### <a name="affected-apis"></a>Etkilenen API’ler

<xref:Microsoft.Net.Http.Headers.HeaderNames?displayProperty=fullName>

<!-- 

#### Affected APIs

`T:Microsoft.Net.Http.Headers.HeaderNames`

-->
