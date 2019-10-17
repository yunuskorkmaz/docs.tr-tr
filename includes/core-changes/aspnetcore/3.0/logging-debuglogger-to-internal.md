---
ms.openlocfilehash: 958dede03e1c15f69f4ee676f13713ff43c29e96
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72393920"
---
### <a name="logging-debuglogger-class-made-internal"></a>Günlüğe kaydetme: Debuggünlükçü sınıfı iç oluşturulmuş

ASP.NET Core 3,0 ' dan önce `DebugLogger` ' dan `public` ' e kadar olan erişim değiştiricisi. ASP.NET Core 3,0 ' de, erişim değiştiricisi `internal` olarak değiştirilmiştir.

#### <a name="version-introduced"></a>Sunulan sürüm

3.0

#### <a name="reason-for-change"></a>Değişiklik nedeni

Değişiklik şu şekilde yapılıyor:

* @No__t-0 gibi diğer günlükçü uygulamalarıyla tutarlılığı zorunlu tutun.
* API yüzeyini küçültün.

#### <a name="recommended-action"></a>Önerilen eylem

Hata ayıklama günlüğünü etkinleştirmek için <xref:Microsoft.Extensions.Logging.DebugLoggerFactoryExtensions.AddDebug%2A> `ILoggingBuilder` genişletme yöntemini kullanın. <xref:Microsoft.Extensions.Logging.Debug.DebugLoggerProvider>, hizmetin el ile kaydedilmesi gereken olayda hala `public` ' i de.

#### <a name="category"></a>Kategori

ASP.NET Core

#### <a name="affected-apis"></a>Etkilenen API’ler

<xref:Microsoft.Extensions.Logging.Debug.DebugLogger?displayProperty=nameWithType>

<!--

#### Affected APIs

`T:Microsoft.Extensions.Logging.Debug.DebugLogger`

-->
