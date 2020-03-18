---
ms.openlocfilehash: b0e1d6d720a1c9b827fb4585606e64b545d395d7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "72394373"
---
### <a name="kestrel-request-trailer-headers-moved-to-new-collection"></a>Kerkenez: İstek römork başlıkları yeni koleksiyona taşındı

Önceki sürümlerde Kestrel, istek gövdesi sonuna kadar okunduğunda istek üstbilgikoleksiyonuna HTTP/1.1 ötücü römork başlıklarını eklenmiştir. Bu davranış, üstbilgi ve römorklar arasındaki belirsizlik le ilgili endişelere neden oldu. Römorkların yeni bir koleksiyona taşınmasına karar verildi.

HTTP /2 istek römorkASP.NET Core 2.2 kullanılamaz ama şimdi de ASP.NET Core 3.0 bu yeni koleksiyonda mevcuttur.

Bu fragmanlara erişmek için yeni istek uzatma yöntemleri eklendi.

TÜM istek gövdesi okunduktan sonra HTTP/1.1 fragmanları mevcuttur.

HTTP/2 römorkları istemciden alındıktan sonra kullanılabilir. İstemci, tüm istek gövdesi en azından sunucu tarafından arabelleğe alana gelene kadar römorkları göndermez. Arabellek alanını boşaltmak için istek gövdesini okumanız gerekebilir. İstek gövdesini sonuna kadar okursanız, römorklar her zaman kullanılabilir. Römorklar vücudun sonunu işaret ediyor.

#### <a name="version-introduced"></a>Sürüm tanıtıldı

3,0

#### <a name="old-behavior"></a>Eski davranış

İstek römork başlıkları koleksiyona `HttpRequest.Headers` eklenecek.

#### <a name="new-behavior"></a>Yeni davranış

İstek römork üstbilgisi `HttpRequest.Headers` koleksiyonda **bulunmaz.** Bunlara erişmek `HttpRequest` için aşağıdaki uzantı yöntemlerini kullanın:

- `GetDeclaredTrailers()`- Hangi römorklar vücut sonra beklemek listeler istek "Römork" başlık alır.
- `SupportsTrailers()`- İsteğin römork üstbilgisini almayı destekleyip desteklemeyin gösterir.
- `CheckTrailersAvailable()`- İsteğin römorkları destekleyip desteklemediklerini ve okumaya uygun olup olmadıklarını belirler.
- `GetTrailer(string trailerName)`- İstenilen sondaki üstbilgiyanıttan alır.

#### <a name="reason-for-change"></a>Değişiklik nedeni

Römorklar gRPC gibi senaryolarda önemli bir özelliktir. Römorkları üstbilgi istemek için birleştirmek kullanıcılar için kafa karıştırıcıydı.

#### <a name="recommended-action"></a>Önerilen eylem

Römorklara erişmek `HttpRequest` için römorkla ilgili uzatma yöntemlerini kullanın.

#### <a name="category"></a>Kategori

ASP.NET Çekirdeği

#### <a name="affected-apis"></a>Etkilenen API’ler

<xref:Microsoft.AspNetCore.Http.HttpRequest.Headers?displayProperty=nameWithType>

<!--

#### Affected APIs

`P:Microsoft.AspNetCore.Http.HttpRequest.Headers`

-->
