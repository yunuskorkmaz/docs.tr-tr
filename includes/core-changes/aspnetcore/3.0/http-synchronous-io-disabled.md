---
ms.openlocfilehash: 53d2c989120c92f4e2d18f50ce4b364bd4c9b604
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/25/2020
ms.locfileid: "96032779"
---
### <a name="http-synchronous-io-disabled-in-all-servers"></a>HTTP: tüm sunucularda zaman uyumlu GÇ devre dışı

ASP.NET Core 3,0 ' den başlayarak, zaman uyumlu sunucu işlemleri varsayılan olarak devre dışıdır.

#### <a name="change-description"></a>Açıklamayı Değiştir

`AllowSynchronousIO` , ve gibi zaman uyumlu GÇ API 'Lerini sağlayan veya devre dışı bırakan her sunucuda bir seçenektir `HttpRequest.Body.Read` `HttpResponse.Body.Write` `Stream.Flush` . Bu API 'Ler, bir iş parçacığı kaynağı ve uygulama askıda kalıyor. ASP.NET Core 3,0 Preview 3 ' te başlayarak bu zaman uyumlu işlemler varsayılan olarak devre dışıdır.

Etkilenen sunucular:

- Kestrel
- HttpSys
- İşlem içi IIS
- TestServer

Şuna benzer hatalar beklenir:

- `Synchronous operations are disallowed. Call ReadAsync or set AllowSynchronousIO to true instead.`
- `Synchronous operations are disallowed. Call WriteAsync or set AllowSynchronousIO to true instead.`
- `Synchronous operations are disallowed. Call FlushAsync or set AllowSynchronousIO to true instead.`

Her sunucu, `AllowSynchronousIO` Bu davranışı denetleyen bir seçeneğe sahiptir ve bunların tümü için varsayılan değer olarak kullanılır `false` .

Davranış, geçici bir risk azaltma olarak istek başına temelinde da geçersiz kılınabilir. Örnek:

```csharp
var syncIOFeature = HttpContext.Features.Get<IHttpBodyControlFeature>();
if (syncIOFeature != null)
{
    syncIOFeature.AllowSynchronousIO = true;
}
```

`TextWriter`İçinde zaman uyumlu API çağıran bir veya başka bir akışta sorun yaşıyorsanız `Dispose` , `DisposeAsync` bunun yerine yeni API 'yi çağırın.

Tartışma için bkz. [DotNet/aspnetcore # 7644](https://github.com/dotnet/aspnetcore/issues/7644).

#### <a name="version-introduced"></a>Sunulan sürüm

3,0

#### <a name="old-behavior"></a>Eski davranış

`HttpRequest.Body.Read`, `HttpResponse.Body.Write` ve `Stream.Flush` Varsayılan olarak izin verilir.

#### <a name="new-behavior"></a>Yeni davranış

Bu zaman uyumlu API 'Lere varsayılan olarak izin verilmez:

Şuna benzer hatalar beklenir:

- `Synchronous operations are disallowed. Call ReadAsync or set AllowSynchronousIO to true instead.`
- `Synchronous operations are disallowed. Call WriteAsync or set AllowSynchronousIO to true instead.`
- `Synchronous operations are disallowed. Call FlushAsync or set AllowSynchronousIO to true instead.`

#### <a name="reason-for-change"></a>Değişiklik nedeni

Bu zaman uyumlu API 'Ler, bir iş parçacığı kaynağı ve uygulama askıda kalıyor. ASP.NET Core 3,0 Preview 3 ' te başlayarak, zaman uyumlu işlemler varsayılan olarak devre dışıdır.

#### <a name="recommended-action"></a>Önerilen eylem

Yöntemlerin zaman uyumsuz sürümlerini kullanın. Davranış, geçici bir risk azaltma olarak istek başına temelinde da geçersiz kılınabilir.

```csharp
var syncIOFeature = HttpContext.Features.Get<IHttpBodyControlFeature>();
if (syncIOFeature != null)
{
    syncIOFeature.AllowSynchronousIO = true;
}
```

#### <a name="category"></a>Kategori

ASP.NET Core

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
