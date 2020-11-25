---
title: 'Son değişiklik: Kestrel: libuv taşıması eski olarak işaretlendi'
description: "Kestrel adlı ASP.NET Core 5,0 ' deki Son değişiklik hakkında bilgi edinin: libuv taşıması eski olarak işaretlendi"
author: scottaddie
ms.author: scaddie
ms.date: 10/01/2020
ms.openlocfilehash: f66b9b646671e07957e6d30a95333d392eb29617
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95761521"
---
# <a name="kestrel-libuv-transport-marked-as-obsolete"></a>Kestrel: libuv taşıması eski olarak işaretlendi

Önceki ASP.NET Core sürümleri, zaman uyumsuz giriş ve çıktının nasıl gerçekleştirildiği hakkında bir uygulama ayrıntısı olarak libuv kullandı. ASP.NET Core 2,0 ' de, alternatif bir <xref:System.Net.Sockets.Socket> tabanlı Aktarım geliştirdik. ASP.NET Core 2,1 ' de, Kestrel `Socket` Varsayılan olarak tabanlı aktarımı kullanmaya geçti. Uyumluluk nedenleriyle libuv desteği korunmıştı.

Bu noktada, tabanlı `Socket` taşımanın kullanımı libuv aktarımından çok daha yaygındır. Bu nedenle, libuv desteği .NET 5,0 ' de kullanılmıyor olarak işaretlenir ve tamamen .NET 6,0 ' de kaldırılır.

Bu değişikliğin bir parçası olarak, .NET 5,0 zaman diliminde yeni işletim sistemi platformları (Windows ARM64 gibi) için libuv desteği eklenmez.

Libuv aktarımının kullanılması gereken sorunları engelleme hakkında tartışmak için, [DotNet/aspnetcore # 23409](https://github.com/dotnet/aspnetcore/issues/23409)adresindeki GitHub sorununa bakın.

## <a name="version-introduced"></a>Sunulan sürüm

5,0 Preview 8

## <a name="old-behavior"></a>Eski davranış

Libuv API 'Leri eski olarak işaretlenmemiş.

## <a name="new-behavior"></a>Yeni davranış

Libuv API 'Leri eski olarak işaretlenir.

## <a name="reason-for-change"></a>Değişiklik nedeni

`Socket`-Tabanlı Aktarım varsayılandır. Libuv taşımasını kullanmaya devam etmek için etkileyici bir neden yoktur.

## <a name="recommended-action"></a>Önerilen eylem

[Libuv paketi](https://www.nuget.org/packages/Libuv) ve genişletme yöntemlerinin kullanımını durdur.

## <a name="affected-apis"></a>Etkilenen API’ler

- [WebHostBuilderLibuvExtensions](/dotnet/api/microsoft.aspnetcore.hosting.webhostbuilderlibuvextensions?view=aspnetcore-3.0)
- [WebHostBuilderLibuvExtensions. UseLibuv](/dotnet/api/microsoft.aspnetcore.hosting.webhostbuilderlibuvextensions.uselibuv?view=aspnetcore-3.0)
- [Microsoft. AspNetCore. Server. Kestrel. Transport. libuv. LibuvTransportOptions](/dotnet/api/microsoft.aspnetcore.server.kestrel.transport.libuv.libuvtransportoptions?view=aspnetcore-3.0)
- [Microsoft. AspNetCore. Server. Kestrel. Transport. libuv. LibuvTransportOptions. ThreadCount](/dotnet/api/microsoft.aspnetcore.server.kestrel.transport.libuv.libuvtransportoptions.threadcount?view=aspnetcore-3.0)
- [Microsoft. AspNetCore. Server. Kestrel. Transport. Lıbuv. LibuvTransportOptions. NoDelay](/dotnet/api/microsoft.aspnetcore.server.kestrel.transport.libuv.libuvtransportoptions.nodelay?view=aspnetcore-3.0)
- [Microsoft. AspNetCore. Server. Kestrel. Transport. libuv. LibuvTransportOptions. MaxWriteBufferSize](/dotnet/api/microsoft.aspnetcore.server.kestrel.transport.libuv.libuvtransportoptions.maxwritebuffersize?view=aspnetcore-3.0)
- [Microsoft. AspNetCore. Server. Kestrel. Transport. libuv. LibuvTransportOptions. MaxReadBufferSize](/dotnet/api/microsoft.aspnetcore.server.kestrel.transport.libuv.libuvtransportoptions.maxreadbuffersize?view=aspnetcore-3.0)
- `Microsoft.AspNetCore.Server.Kestrel.Transport.Libuv.LibuvTransportOptions.Backlog`

<!--

### Category

ASP.NET Core

### Affected APIs

- `T:Microsoft.AspNetCore.Hosting.WebHostBuilderLibuvExtensions`
- `Overload:Microsoft.AspNetCore.Hosting.WebHostBuilderLibuvExtensions.UseLibuv`
- `T:Microsoft.AspNetCore.Server.Kestrel.Transport.Libuv.LibuvTransportOptions`
- `P:Microsoft.AspNetCore.Server.Kestrel.Transport.Libuv.LibuvTransportOptions.ThreadCount`
- `P:Microsoft.AspNetCore.Server.Kestrel.Transport.Libuv.LibuvTransportOptions.NoDelay`
- `P:Microsoft.AspNetCore.Server.Kestrel.Transport.Libuv.LibuvTransportOptions.MaxWriteBufferSize`
- `P:Microsoft.AspNetCore.Server.Kestrel.Transport.Libuv.LibuvTransportOptions.MaxReadBufferSize`
- `P:Microsoft.AspNetCore.Server.Kestrel.Transport.Libuv.LibuvTransportOptions.Backlog`

-->
