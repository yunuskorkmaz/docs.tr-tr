---
title: 'Son değişiklik: yerelleştirme: gereksiz Oluşturucu istek için yerelleştirme ara yazılımı kaldırıldı'
description: "Yerelleştirme başlıklı ASP.NET Core 5,0 ' deki Son değişiklik hakkında bilgi edinin: gereksiz Oluşturucu, yerelleştirme ara yazılım isteğine kaldırıldı"
author: scottaddie
ms.author: scaddie
ms.date: 10/01/2020
ms.openlocfilehash: 53dd0f25078dae140d34d6d21d66983f78b8bdb0
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95761642"
---
# <a name="localization-obsolete-constructor-removed-in-request-localization-middleware"></a>Yerelleştirme: gereksiz Oluşturucu istek yerelleştirme ara yazılım ortamında kaldırıldı

<xref:Microsoft.AspNetCore.Localization.RequestLocalizationMiddleware>Parametresi olmayan Oluşturucu <xref:Microsoft.Extensions.Logging.ILoggerFactory> [Bu işlemede](https://github.com/dotnet/aspnetcore/commit/ba8c6ccf6fd3eeb7fc42a159d362b15eae4fb3a0)kullanılmıyor olarak işaretlendi. ASP.NET Core 5,0 ' de, eski Oluşturucu kaldırılmıştır. Tartışma için bkz. [DotNet/aspnetcore # 23785](https://github.com/dotnet/aspnetcore/issues/23785).

## <a name="version-introduced"></a>Sunulan sürüm

5,0 Preview 8

## <a name="old-behavior"></a>Eski davranış

Eski `RequestLocalizationMiddleware.ctor(RequestDelegate, IOptions<RequestLocalizationOptions>)` Oluşturucu var.

## <a name="new-behavior"></a>Yeni davranış

Eski `RequestLocalizationMiddleware.ctor(RequestDelegate, IOptions<RequestLocalizationOptions>)` Oluşturucu yok.

## <a name="reason-for-change"></a>Değişiklik nedeni

Bu değişiklik, istek yerelleştirme ara yazılımı 'nın her zaman bir günlükçü erişimine sahip olmasını sağlar.

## <a name="recommended-action"></a>Önerilen eylem

Bir örneğini el ile oluştururken `RequestLocalizationMiddleware` oluşturucuda bir örnek geçirin `ILoggerFactory` . `ILoggerFactory`Bu bağlamda geçerli bir örnek yoksa, ara yazılım oluşturucusunu bir örnek olarak geçirmeyi düşünün <xref:Microsoft.Extensions.Logging.Abstractions.NullLoggerFactory> .

## <a name="affected-apis"></a>Etkilenen API’ler

[Requestlocalizationara yazılımı. ctor (RequestDelegate, IOptions \<RequestLocalizationOptions> )](/dotnet/api/microsoft.aspnetcore.localization.requestlocalizationmiddleware.-ctor?view=aspnetcore-3.1#Microsoft_AspNetCore_Localization_RequestLocalizationMiddleware__ctor_Microsoft_AspNetCore_Http_RequestDelegate_Microsoft_Extensions_Options_IOptions_Microsoft_AspNetCore_Builder_RequestLocalizationOptions__)

<!--

### Category

ASP.NET Core

### Affected APIs

`M:Microsoft.AspNetCore.Localization.RequestLocalizationMiddleware.#ctor(Microsoft.AspNetCore.Http.RequestDelegate,Microsoft.Extensions.Options.IOptions{Microsoft.AspNetCore.Builder.RequestLocalizationOptions})`

-->
