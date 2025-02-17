---
ms.openlocfilehash: b0e1d6d720a1c9b827fb4585606e64b545d395d7
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/25/2020
ms.locfileid: "96032812"
---
### <a name="kestrel-request-trailer-headers-moved-to-new-collection"></a>Kestrel: yeni koleksiyona taşınan artbilgisi üstbilgileri ıste

Önceki sürümlerde, istek gövdesi sonuna kadar okurken istek üstbilgileri koleksiyonuna HTTP/1.1 öbekli treyler üst bilgileri eklenmiş Kestrel. Bu davranış, üstbilgiler ve tanıtımları arasındaki belirsizlik hakkında kaygılara neden oldu. Tanıtım listesini yeni bir koleksiyona taşımak için karar yapıldı.

HTTP/2 istek fragmanları ASP.NET Core 2,2 ' de yoktu, ancak artık ASP.NET Core 3,0 ' de bu yeni koleksiyonda de kullanılabiliyor.

Bu treylara erişmek için yeni istek uzantısı yöntemleri eklenmiştir.

İstek gövdesinin tamamı okunduktan sonra HTTP/1.1 Treyi kullanılabilir.

HTTP/2 treyler istemciden alındıkları bir kez kullanılabilir. İstemci, tüm istek gövdesinin sunucu tarafından en az arabelleğe alınana kadar Treyi göndermez. Arabellek alanını boşaltmak için istek gövdesini okumanız gerekebilir. İstek gövdesini sonuna okuduğunuzda, Treyi her zaman kullanılabilir. Treyi, gövdenin sonunu işaret eden bir değer.

#### <a name="version-introduced"></a>Sunulan sürüm

3,0

#### <a name="old-behavior"></a>Eski davranış

İstek artbilgisi üst bilgileri `HttpRequest.Headers` koleksiyona eklenir.

#### <a name="new-behavior"></a>Yeni davranış

Koleksiyonda istek Fragmanı üstbilgileri **yok** `HttpRequest.Headers` . Bunlara erişmek için aşağıdaki uzantı yöntemlerini kullanın `HttpRequest` :

- `GetDeclaredTrailers()` -Gövdeden sonra beklenme hakkında bilgi sağlayan istek "artbilgisi" üst bilgisini alır.
- `SupportsTrailers()` -İsteğin treyler üst bilgilerini almayı destekleyip desteklemediğini gösterir.
- `CheckTrailersAvailable()` -İsteğin treyleri destekleyip desteklemediğini ve okuma için kullanılabilir olup olmadığını belirler.
- `GetTrailer(string trailerName)` -İstemciden istenen sondaki üstbilgiyi alır.

#### <a name="reason-for-change"></a>Değişiklik nedeni

Treyde gRPC gibi senaryolarda önemli bir özelliktir. İstek üst bilgilerinde tanıtımları birleştirme, kullanıcılar için kafa karıştırıcı.

#### <a name="recommended-action"></a>Önerilen eylem

Treyler ile ilgili genişletme yöntemlerini kullanarak `HttpRequest` treyleri erişin.

#### <a name="category"></a>Kategori

ASP.NET Core

#### <a name="affected-apis"></a>Etkilenen API’ler

<xref:Microsoft.AspNetCore.Http.HttpRequest.Headers?displayProperty=nameWithType>

<!--

#### Affected APIs

`P:Microsoft.AspNetCore.Http.HttpRequest.Headers`

-->
