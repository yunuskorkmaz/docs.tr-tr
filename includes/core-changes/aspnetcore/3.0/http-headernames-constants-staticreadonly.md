---
ms.openlocfilehash: e0d0a680915f14c2d33f1864ad5ad05aff3dde5f
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394326"
---
### <a name="http-headernames-constants-changed-to-static-readonly"></a>HTTP: HeaderNames sabitleri statik ReadOnly olarak değiştirildi

ASP.NET Core 3,0 Preview 5 ' ten başlayarak, <xref:Microsoft.Net.Http.Headers.HeaderNames?displayProperty=fullName> alan `const` `static readonly`olarak değişir.

Tartışma için bkz. [ASPNET/AspNetCore # 9514](https://github.com/aspnet/AspNetCore/issues/9514).

#### <a name="version-introduced"></a>Sunulan sürüm

3,0

#### <a name="old-behavior"></a>Eski davranış

Bu alanlar `const`için kullanılır.

#### <a name="new-behavior"></a>Yeni davranış

Bu alanlar artık `static readonly`.

#### <a name="reason-for-change"></a>Değişiklik nedeni

Değişiklik:

* Değerlerin, gerektiğinde değer düzeltmeleri için derleme sınırları arasında gömülmesini önler.
* Daha hızlı başvuru eşitlik denetimleri sağlar.

#### <a name="recommended-action"></a>Önerilen eylem

3,0 ile yeniden derleyin. Aşağıdaki yollarla bu alanları kullanan kaynak kodu bundan böyle devam edebilir:

* Öznitelik bağımsız değişkeni olarak
* `switch` bildiriminde `case` olarak
* Başka bir `const` tanımlarken

Son değişikliği geçici olarak çözmek için, kendi kendine tanımlanmış üst bilgi adı sabitleri veya dize sabit değerlerini kullanmaya geçin.

#### <a name="category"></a>Kategori

ASP.NET Core

#### <a name="affected-apis"></a>Etkilenen API’ler

<xref:Microsoft.Net.Http.Headers.HeaderNames?displayProperty=fullName>

<!-- 

#### Affected APIs

`T:Microsoft.Net.Http.Headers.HeaderNames`

-->
