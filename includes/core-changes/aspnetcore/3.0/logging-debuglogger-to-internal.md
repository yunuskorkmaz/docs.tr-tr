---
ms.openlocfilehash: 958dede03e1c15f69f4ee676f13713ff43c29e96
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "72393920"
---
### <a name="logging-debuglogger-class-made-internal"></a>Günlük: DebugLogger sınıfı dahili yaptı

Core 3.0ASP.NET önce, `DebugLogger`'erişim değiştirici `public`oldu. ASP.NET Core 3.0'da erişim değiştirici `internal`.'

#### <a name="version-introduced"></a>Sürüm tanıtıldı

3,0

#### <a name="reason-for-change"></a>Değişiklik nedeni

Değişiklik şu şekilde yapılmaktadır:

* `ConsoleLogger`Diğer logger uygulamaları yla tutarlılığı zorlar.
* API yüzeyini azaltın.

#### <a name="recommended-action"></a>Önerilen eylem

Hata <xref:Microsoft.Extensions.Logging.DebugLoggerFactoryExtensions.AddDebug%2A> `ILoggingBuilder` ayıklama günlüğe kaydetmeyi etkinleştirmek için uzantı yöntemini kullanın. <xref:Microsoft.Extensions.Logging.Debug.DebugLoggerProvider>hizmetin `public` el ile kaydedilmesi gerektiğinde de devam etmektedir.

#### <a name="category"></a>Kategori

ASP.NET Çekirdeği

#### <a name="affected-apis"></a>Etkilenen API’ler

<xref:Microsoft.Extensions.Logging.Debug.DebugLogger?displayProperty=nameWithType>

<!--

#### Affected APIs

`T:Microsoft.Extensions.Logging.Debug.DebugLogger`

-->
