---
title: 'Son değişiklik: ara yazılım: veritabanı hatası sayfası eski olarak işaretlendi'
description: "ASP.NET Core 5,0 ' daki Son değişiklik hakkında bilgi edinin ara yazılım: eski olarak işaretlenen veritabanı hatası sayfası"
author: scottaddie
ms.author: scaddie
ms.date: 10/01/2020
ms.openlocfilehash: f828b5e20c2a9a709d675e435caa99727aebd5b6
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95761602"
---
# <a name="middleware-database-error-page-marked-as-obsolete"></a>Ara yazılım: veritabanı hatası sayfası eski olarak işaretlendi

[Databaseerrorpageara yazılımı](/dotnet/api/microsoft.aspnetcore.diagnostics.entityframeworkcore.databaseerrorpagemiddleware?view=aspnetcore-3.0) ve ilişkili uzantı yöntemleri ASP.NET Core 5,0 ' de kullanılmıyor olarak işaretlendi. Ara yazılım ve uzantı yöntemleri ASP.NET Core 6,0 ' de kaldırılır. Bu işlevsellik, `DatabaseDeveloperPageExceptionFilter` ve uzantı yöntemleri tarafından sağlanacak.

Tartışma için, [DotNet/aspnetcore # 24987](https://github.com/dotnet/aspnetcore/issues/24987)konumundaki GitHub sorununa bakın.

## <a name="version-introduced"></a>Sunulan sürüm

5,0 RC 1

## <a name="old-behavior"></a>Eski davranış

`DatabaseErrorPageMiddleware` ve ilişkili uzantı yöntemleri artık kullanılmıyor.

## <a name="new-behavior"></a>Yeni davranış

`DatabaseErrorPageMiddleware` ve ilişkili genişletme yöntemleri artık kullanılmıyor.

## <a name="reason-for-change"></a>Değişiklik nedeni

`DatabaseErrorPageMiddleware`[Geliştirici özel durum sayfası](/aspnet/core/fundamentals/error-handling#developer-exception-page)için GENIŞLETILEBILIR bir API 'ye geçirildi. Genişletilebilir API hakkında daha fazla bilgi için bkz. GitHub sorunu [DotNet/aspnetcore # 8536](https://github.com/dotnet/aspnetcore/issues/8536).

## <a name="recommended-action"></a>Önerilen eylem

Aşağıdaki adımları tamamlayın:

1. Projenizde kullanmayı durdurun `DatabaseErrorPageMiddleware` . Örneğin, `UseDatabaseErrorPage` öğesinden yöntem çağrısını kaldırın `Startup.Configure` :

    ```csharp
    public void Configure(IApplicationBuilder app, IWebHostEnvironment env)
    {
        if (env.IsDevelopment())
        {
            app.UseDatabaseErrorPage();
        }
    }
    ```

1. Geliştirici özel durum sayfasını projenize ekleyin. Örneğin, <xref:Microsoft.AspNetCore.Builder.DeveloperExceptionPageExtensions.UseDeveloperExceptionPage%2A> içinde yöntemini çağırın `Startup.Configure` :

    ```csharp
    public void Configure(IApplicationBuilder app, IWebHostEnvironment env)
    {
        if (env.IsDevelopment())
        {
            app.UseDeveloperExceptionPage();
        }
    }
    ```

1. Proje dosyasına [Microsoft. AspNetCore. Diagnostics. EntityFrameworkCore](https://www.nuget.org/packages/Microsoft.AspNetCore.Diagnostics.EntityFrameworkCore) NuGet paketini ekleyin.

1. Veritabanı Geliştirici sayfası özel durum filtresini hizmetler koleksiyonuna ekleyin. Örneğin, `AddDatabaseDeveloperPageExceptionFilter` içinde yöntemini çağırın `Startup.ConfigureServices` :

    ```csharp
    public void ConfigureServices(IServiceCollection services)
    {
        services.AddDatabaseDeveloperPageExceptionFilter();
    }
    ```

## <a name="affected-apis"></a>Etkilenen API’ler

- [Microsoft. AspNetCore. Builder. DatabaseErrorPageExtensions. UseDatabaseErrorPage](/dotnet/api/microsoft.aspnetcore.builder.databaseerrorpageextensions.usedatabaseerrorpage?view=aspnetcore-3.0)
- [Microsoft. AspNetCore. Diagnostics. EntityFrameworkCore. Databaseerrorpageara yazılımı](/dotnet/api/microsoft.aspnetcore.diagnostics.entityframeworkcore.databaseerrorpagemiddleware?view=aspnetcore-3.0)

<!--

### Category

ASP.NET Core

### Affected APIs

- `Overload:Microsoft.AspNetCore.Builder.DatabaseErrorPageExtensions.UseDatabaseErrorPage`
- `T:Microsoft.AspNetCore.Diagnostics.EntityFrameworkCore.DatabaseErrorPageMiddleware`

-->
