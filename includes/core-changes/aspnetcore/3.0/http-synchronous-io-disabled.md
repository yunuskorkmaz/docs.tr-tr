---
ms.openlocfilehash: 53d2c989120c92f4e2d18f50ce4b364bd4c9b604
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/11/2020
ms.locfileid: "75901939"
---
### <a name="http-synchronous-io-disabled-in-all-servers"></a>HTTP: tüm sunucularda zaman uyumlu GÇ devre dışı

ASP.NET Core 3,0 ' den başlayarak, zaman uyumlu sunucu işlemleri varsayılan olarak devre dışıdır.

#### <a name="change-description"></a>Açıklamayı Değiştir

`AllowSynchronousIO`, her bir sunucuda `HttpRequest.Body.Read`, `HttpResponse.Body.Write`ve `Stream.Flush`gibi zaman uyumlu GÇ API 'Lerini sağlayan veya devre dışı bırakan bir seçenektir. Bu API 'Ler, bir iş parçacığı kaynağı ve uygulama askıda kalıyor. ASP.NET Core 3,0 Preview 3 ' te başlayarak bu zaman uyumlu işlemler varsayılan olarak devre dışıdır.

Etkilenen sunucular:

- Kestrel
- HttpSys
- İşlem içi IIS
- TestServer

Şuna benzer hatalar beklenir:

- `Synchronous operations are disallowed. Call ReadAsync or set AllowSynchronousIO to true instead.`
- `Synchronous operations are disallowed. Call WriteAsync or set AllowSynchronousIO to true instead.`
- `Synchronous operations are disallowed. Call FlushAsync or set AllowSynchronousIO to true instead.`

Her sunucu, bu davranışı denetleyen bir `AllowSynchronousIO` seçeneğine sahiptir ve bunların tümü için varsayılan olarak `false`.

Davranış, geçici bir risk azaltma olarak istek başına temelinde da geçersiz kılınabilir. Örneğin:

```csharp
var syncIOFeature = HttpContext.Features.Get<IHttpBodyControlFeature>();
if (syncIOFeature != null)
{
    syncIOFeature.AllowSynchronousIO = true;
}
```

`Dispose`içinde zaman uyumlu bir API çağıran `TextWriter` veya başka bir akış ile ilgili sorun yaşıyorsanız, bunun yerine yeni `DisposeAsync` API 'sini çağırın.

Tartışma için bkz. [DotNet/aspnetcore # 7644](https://github.com/dotnet/aspnetcore/issues/7644).

#### <a name="version-introduced"></a>Sunulan sürüm

3.0

#### <a name="old-behavior"></a>Eski davranış

`HttpRequest.Body.Read`, `HttpResponse.Body.Write`ve `Stream.Flush` varsayılan olarak izin verilir.

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
