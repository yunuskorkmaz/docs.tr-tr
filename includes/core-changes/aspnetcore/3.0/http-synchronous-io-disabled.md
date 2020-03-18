---
ms.openlocfilehash: 53d2c989120c92f4e2d18f50ce4b364bd4c9b604
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75901939"
---
### <a name="http-synchronous-io-disabled-in-all-servers"></a>HTTP: Senkron IO tüm sunucularda devre dışı

Core 3.0 ASP.NET ile başlayarak, senkron sunucu işlemleri varsayılan olarak devre dışı bırakılır.

#### <a name="change-description"></a>Açıklamayı değiştir

`AllowSynchronousIO`her sunucuda senkron IO API'lerini etkinleştiren veya devre `HttpRequest.Body.Read` `HttpResponse.Body.Write`dışı `Stream.Flush`eden bir seçenektir. Bu API'ler uzun iplik açlık kaynağı olmuştur ve uygulama asılı. Core 3.0 Preview 3'ASP.NET başlayarak, bu eşzamanlı işlemler varsayılan olarak devre dışı bırakılır.

Etkilenen sunucular:

- Kestrel
- Http://sys
- IIS süreç içinde
- TestSunucusu

Benzer hatalar bekleyin:

- `Synchronous operations are disallowed. Call ReadAsync or set AllowSynchronousIO to true instead.`
- `Synchronous operations are disallowed. Call WriteAsync or set AllowSynchronousIO to true instead.`
- `Synchronous operations are disallowed. Call FlushAsync or set AllowSynchronousIO to true instead.`

Her sunucubu `AllowSynchronousIO` davranışı kontrol eden bir seçenek vardır ve `false`hepsi için varsayılan şimdi .

Davranış, geçici bir azaltma olarak istek başına olarak geçersiz kılınabilir. Örnek:

```csharp
var syncIOFeature = HttpContext.Features.Get<IHttpBodyControlFeature>();
if (syncIOFeature != null)
{
    syncIOFeature.AllowSynchronousIO = true;
}
```

Senkron API'yi çağıran bir `TextWriter` veya başka bir `Dispose`akışla `DisposeAsync` ilgili sorun yaşıyorsanız, bunun yerine yeni API'yi arayın.

Tartışma için [dotnet/aspnetcore#7644'e](https://github.com/dotnet/aspnetcore/issues/7644)bakın.

#### <a name="version-introduced"></a>Sürüm tanıtıldı

3,0

#### <a name="old-behavior"></a>Eski davranış

`HttpRequest.Body.Read`, `HttpResponse.Body.Write`ve `Stream.Flush` varsayılan olarak izin verildi.

#### <a name="new-behavior"></a>Yeni davranış

Bu eşzamanlı API'ler varsayılan olarak izin verilmez:

Benzer hatalar bekleyin:

- `Synchronous operations are disallowed. Call ReadAsync or set AllowSynchronousIO to true instead.`
- `Synchronous operations are disallowed. Call WriteAsync or set AllowSynchronousIO to true instead.`
- `Synchronous operations are disallowed. Call FlushAsync or set AllowSynchronousIO to true instead.`

#### <a name="reason-for-change"></a>Değişiklik nedeni

Bu senkron API'ler uzun iplik açlık kaynağı olmuştur ve uygulama asılı. Core 3.0 Preview 3ASP.NETden başlayarak, eşzamanlı işlemler varsayılan olarak devre dışı bırakılır.

#### <a name="recommended-action"></a>Önerilen eylem

Yöntemlerin eşzamanlı sürümlerini kullanın. Davranış, geçici bir azaltma olarak istek başına olarak geçersiz kılınabilir.

```csharp
var syncIOFeature = HttpContext.Features.Get<IHttpBodyControlFeature>();
if (syncIOFeature != null)
{
    syncIOFeature.AllowSynchronousIO = true;
}
```

#### <a name="category"></a>Kategori

ASP.NET Çekirdeği

#### <a name="affected-apis"></a>Etkilenen API’ler

- <xref:System.IO.Stream.Flush%2A?displayProperty=nameWithType>
- <xref:System.IO.Stream.Read%2A?displayProperty=nameWithType>
- <xref:System.IO.Stream.Write%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

- `Overload:System.IO.Stream.Flush`
- `Overload:System.IO.Stream.Read`
- `Overload:System.IO.Stream.Write`

-->
