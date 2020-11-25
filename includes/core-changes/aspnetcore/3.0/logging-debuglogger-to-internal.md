---
ms.openlocfilehash: 958dede03e1c15f69f4ee676f13713ff43c29e96
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/25/2020
ms.locfileid: "96032820"
---
### <a name="logging-debuglogger-class-made-internal"></a>Günlüğe kaydetme: Debuggünlükçü sınıfı iç oluşturulmuş

ASP.NET Core 3,0 ' den önce `DebugLogger` erişim değiştiricisi idi `public` . ASP.NET Core 3,0 ' de, erişim değiştiricisi olarak değiştirilmiştir `internal` .

#### <a name="version-introduced"></a>Sunulan sürüm

3,0

#### <a name="reason-for-change"></a>Değişiklik nedeni

Değişiklik şu şekilde yapılıyor:

* Gibi diğer günlükçü uygulamalarıyla tutarlılığı zorunlu tutun `ConsoleLogger` .
* API yüzeyini küçültün.

#### <a name="recommended-action"></a>Önerilen eylem

<xref:Microsoft.Extensions.Logging.DebugLoggerFactoryExtensions.AddDebug%2A> `ILoggingBuilder` Hata ayıklama günlüğünü etkinleştirmek için genişletme yöntemini kullanın. <xref:Microsoft.Extensions.Logging.Debug.DebugLoggerProvider> Ayrıca `public` hizmetin el ile kaydedilmesi gereken bir olaydır.

#### <a name="category"></a>Kategori

ASP.NET Core

#### <a name="affected-apis"></a>Etkilenen API’ler

<xref:Microsoft.Extensions.Logging.Debug.DebugLogger?displayProperty=nameWithType>

<!--

#### Affected APIs

`T:Microsoft.Extensions.Logging.Debug.DebugLogger`

-->
