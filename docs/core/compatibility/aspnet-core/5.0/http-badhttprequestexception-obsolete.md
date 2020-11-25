---
title: 'Son değişiklik: HTTP: Kestrel ve IIS BadHttpRequestException türleri artık kullanılmıyor ve değiştirilmiş olarak işaretlendi'
description: "ASP.NET Core 5,0 ' de, HTTP: Kestrel ve IIS Rozhttprequestexception türlerini Kullanımdan kaldırılmış ve değiştirilmiş olarak işaretlenen Son değişiklik hakkında bilgi edinin"
author: scottaddie
ms.author: scaddie
ms.date: 10/01/2020
ms.openlocfilehash: c51b1dd9d708c04bc1bbcfb65ea2e9daea5330b4
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95761473"
---
# <a name="http-kestrel-and-iis-badhttprequestexception-types-marked-obsolete-and-replaced"></a>HTTP: Kestrel ve IIS BadHttpRequestException türleri artık kullanılmıyor ve değiştirilmiş olarak işaretlendi

`Microsoft.AspNetCore.Server.Kestrel.BadHttpRequestException` ve `Microsoft.AspNetCore.Server.IIS.BadHttpRequestException` artık kullanılmıyor olarak işaretlendi ve öğesinden türetilme değiştirildi `Microsoft.AspNetCore.Http.BadHttpRequestException` . Kestrel ve IIS sunucuları geriye dönük uyumluluk için eski özel durum türlerini hala oluşturur. Eski türler gelecek sürümde kaldırılacak.

Tartışma için bkz. [DotNet/aspnetcore # 20614](https://github.com/dotnet/aspnetcore/issues/20614).

## <a name="version-introduced"></a>Sunulan sürüm

5,0 Preview 4

## <a name="old-behavior"></a>Eski davranış

`Microsoft.AspNetCore.Server.Kestrel.BadHttpRequestException` ve `Microsoft.AspNetCore.Server.IIS.BadHttpRequestException` öğesinden türetilir <xref:System.IO.IOException?displayProperty=nameWithType> .

## <a name="new-behavior"></a>Yeni davranış

`Microsoft.AspNetCore.Server.Kestrel.BadHttpRequestException` ve `Microsoft.AspNetCore.Server.IIS.BadHttpRequestException` artık kullanılmıyor. Türler Ayrıca öğesinden türetilir `Microsoft.AspNetCore.Http.BadHttpRequestException` `System.IO.IOException` .

## <a name="reason-for-change"></a>Değişiklik nedeni

Değişikliğin yapıldığı yer:

* Yinelenen türleri birleştirin.
* Sunucu uygulamalarında davranışı bütünleştirme.

Uygulama artık `Microsoft.AspNetCore.Http.BadHttpRequestException` Kestrel veya IIS kullanırken temel özel durumu yakalayabilir.

## <a name="recommended-action"></a>Önerilen eylem

Ve kullanımlarının `Microsoft.AspNetCore.Server.Kestrel.BadHttpRequestException` kullanımlarını `Microsoft.AspNetCore.Server.IIS.BadHttpRequestException` ile değiştirin `Microsoft.AspNetCore.Http.BadHttpRequestException` .

## <a name="affected-apis"></a>Etkilenen API’ler

- [Microsoft. AspNetCore. Server. IIS. BadHttpRequestException](/dotnet/api/microsoft.aspnetcore.server.iis.badhttprequestexception?view=aspnetcore-3.1)
- [Microsoft. AspNetCore. Server. Kestrel. BadHttpRequestException](/dotnet/api/microsoft.aspnetcore.server.kestrel.badhttprequestexception?view=aspnetcore-1.1)

<!--

### Category

ASP.NET Core

### Affected APIs

- `T:Microsoft.AspNetCore.Server.IIS.BadHttpRequestException`
- `T:Microsoft.AspNetCore.Server.Kestrel.BadHttpRequestException`

-->
