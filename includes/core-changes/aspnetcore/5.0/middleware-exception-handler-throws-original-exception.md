---
ms.openlocfilehash: 26e521a86b504824f035ad5d40e4a04d2ea26abc
ms.sourcegitcommit: 6d4ee46871deb9ea1e45bb5f3784474e240bbc26
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/11/2020
ms.locfileid: "90022979"
---
### <a name="middleware-exception-handler-middleware-throws-original-exception-if-handler-not-found"></a>Ara yazılım: özel durum Işleyicisi ara yazılımı, işleyici bulunmazsa özgün özel durum oluşturur

5,0 ASP.NET Core önce, [özel durum Işleyici ara yazılımı](xref:Microsoft.AspNetCore.Builder.ExceptionHandlerExtensions.UseExceptionHandler%2A) yapılandırılmış özel durum işleyicisini bir özel durum oluştuğunda yürütür. Aracılığıyla yapılandırılan özel durum işleyicisi bulunamazsa, <xref:Microsoft.AspNetCore.Builder.ExceptionHandlerOptions.ExceptionHandlingPath> BIR HTTP 404 yanıtı üretilir. Yanıt şu şekilde yanıltıcıdır:

* Kullanıcı hatası gibi görünüyor.
* Sunucu üzerinde bir özel durumun gerçekleştiği gerçeğini gizler.

ASP.NET Core 5,0 ' deki yanıltıcı hatayı gidermek için, `ExceptionHandlerMiddleware` özel durum işleyicisi bulunamazsa özgün özel durumu oluşturur. Sonuç olarak, sunucu tarafından bir HTTP 500 yanıtı üretilir. Yanıt, oluşan hata ayıklanırken sunucu günlüklerinde İncelenme daha kolay olacaktır.

Tartışma için bkz. GitHub sorunu [DotNet/aspnetcore # 25288](https://github.com/dotnet/aspnetcore/issues/25288).

#### <a name="version-introduced"></a>Sunulan sürüm

5,0 RC 1

#### <a name="old-behavior"></a>Eski davranış

Yapılandırılmış özel durum işleyicisi bulunamazsa, özel durum Işleyicisi ara yazılımı bir HTTP 404 yanıtı üretir.

#### <a name="new-behavior"></a>Yeni davranış

Özel durum Işleyici ara yazılımı, yapılandırılmış özel durum işleyicisi bulunamazsa özgün özel durumu oluşturur.

#### <a name="reason-for-change"></a>Değişiklik nedeni

HTTP 404 hatası, sunucuda bir özel durumun gerçekleşmediğini açık hale getirir. Bu değişiklik şunları açık hale getirmek için bir HTTP 500 hatası üretir:

* Sorun bir kullanıcı hatasından kaynaklanmıyor.
* Sunucuda bir özel durumla karşılaşıldı.

#### <a name="recommended-action"></a>Önerilen eylem

API değişikliği yok. Tüm mevcut uygulamalar derlenmeye ve çalıştırmaya devam edecektir. Oluşturulan özel durum sunucu tarafından işlenir. Örneğin, özel durum [Kestrel](/aspnet/core/fundamentals/servers/kestrel) veya [HTTP.sys](/aspnet/core/fundamentals/servers/httpsys)tarafından http 500 hata yanıtına dönüştürülür.

#### <a name="category"></a>Kategori

ASP.NET Core

#### <a name="affected-apis"></a>Etkilenen API’ler

Yok

<!--

#### Affected APIs

Not detectable via API analysis

-->
