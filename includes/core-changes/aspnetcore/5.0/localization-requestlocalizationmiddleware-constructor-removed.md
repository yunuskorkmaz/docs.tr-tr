---
ms.openlocfilehash: db941229e02064ee856829417d6762aa17b0b926
ms.sourcegitcommit: 0fa2b7b658bf137e813a7f4d09589d64c148ebf5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/14/2020
ms.locfileid: "86309175"
---
### <a name="localization-obsolete-constructor-removed-in-request-localization-middleware"></a>Yerelleştirme: gereksiz Oluşturucu istek yerelleştirme ara yazılım ortamında kaldırıldı

<xref:Microsoft.AspNetCore.Localization.RequestLocalizationMiddleware>Parametresi olmayan Oluşturucu <xref:Microsoft.Extensions.Logging.ILoggerFactory> [Bu işlemede](https://github.com/dotnet/aspnetcore/commit/ba8c6ccf6fd3eeb7fc42a159d362b15eae4fb3a0)kullanılmıyor olarak işaretlendi. ASP.NET Core 5,0 ' de, eski Oluşturucu kaldırılmıştır. Tartışma için bkz. [DotNet/aspnetcore # 23785](https://github.com/dotnet/aspnetcore/issues/23785).

#### <a name="version-introduced"></a>Sunulan sürüm

5,0 Preview 8

#### <a name="old-behavior"></a>Eski davranış

Eski `RequestLocalizationMiddleware.ctor(RequestDelegate, IOptions<RequestLocalizationOptions>)` Oluşturucu var.

#### <a name="new-behavior"></a>Yeni davranış

Eski `RequestLocalizationMiddleware.ctor(RequestDelegate, IOptions<RequestLocalizationOptions>)` Oluşturucu yok.

#### <a name="reason-for-change"></a>Değişiklik nedeni

Bu değişiklik, istek yerelleştirme ara yazılımı 'nın her zaman bir günlükçü erişimine sahip olmasını sağlar.

#### <a name="recommended-action"></a>Önerilen eylem

Bir örneğini el ile oluştururken `RequestLocalizationMiddleware` oluşturucuda bir örnek geçirin `ILoggerFactory` . `ILoggerFactory`Bu bağlamda geçerli bir örnek yoksa, ara yazılım oluşturucusunu bir örnek olarak geçirmeyi düşünün <xref:Microsoft.Extensions.Logging.Abstractions.NullLoggerFactory> .

#### <a name="category"></a>Kategori

ASP.NET Core

#### <a name="affected-apis"></a>Etkilenen API’ler

[Requestlocalizationara yazılımı. ctor (RequestDelegate, IOptions \<RequestLocalizationOptions> )](/dotnet/api/microsoft.aspnetcore.localization.requestlocalizationmiddleware.-ctor?view=aspnetcore-3.1#Microsoft_AspNetCore_Localization_RequestLocalizationMiddleware__ctor_Microsoft_AspNetCore_Http_RequestDelegate_Microsoft_Extensions_Options_IOptions_Microsoft_AspNetCore_Builder_RequestLocalizationOptions__)

<!--

#### Affected APIs

`M:Microsoft.AspNetCore.Localization.RequestLocalizationMiddleware.#ctor(Microsoft.AspNetCore.Http.RequestDelegate,Microsoft.Extensions.Options.IOptions{Microsoft.AspNetCore.Builder.RequestLocalizationOptions})`

-->
