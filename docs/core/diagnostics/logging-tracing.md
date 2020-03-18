---
title: Günlük ve izleme - .NET Core
description: .NET Core günlüğe kaydetme ve izleme için bir giriş.
ms.date: 08/05/2019
ms.openlocfilehash: 392b88c9ea3c31c919a605ac0a5c886f7d63f79a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75714417"
---
# <a name="net-core-logging-and-tracing"></a>.NET Core günlük ve izleme

Günlük ve izleme gerçekten aynı teknik için iki isim vardır. Basit teknik bilgisayarların ilk günlerinden beri kullanılmaktadır. Sadece daha sonra tüketilecek çıktı yazmak için bir uygulama enstrümante içerir.

## <a name="reasons-to-use-logging-and-tracing"></a>Günlüğe kaydetme ve izleme yi kullanma nedenleri

Bu basit teknik şaşırtıcı derecede güçlüdür. Hata ayıklamanın başarısız olduğu durumlarda kullanılabilir:

- Uzun süreler boyunca meydana gelen sorunlar, geleneksel bir hata ayıklama ile hata ayıklamak zor olabilir. Günlükler, uzun sürelere yayılan ayrıntılı otopsi incelemesine olanak sağlar. Buna karşılık, hata ayıklayıcılar gerçek zamanlı analiz için sınırlıdır.
- Çok iş parçacığı uygulamaları ve dağıtılmış uygulamalar genellikle hata ayıklamak zordur.  Hata ayıklama ekleme, davranışları değiştirme eğilimindedir. Karmaşık sistemleri anlamak için gerektiğinde ayrıntılı günlükler analiz edilebilir.
- Dağıtılmış uygulamalardaki sorunlar birçok bileşen arasındaki karmaşık etkileşimden kaynaklanabilir ve bir hata ayıkıcıyı sistemin her bölümüne bağlamak makul olmayabilir.
- Birçok hizmet oyalanmış olmamalıdır. Hata ayıklama eklemek genellikle zaman arızası hatalarına neden olur.
- Sorunlar her zaman öngörülmüyor. Günlüğe kaydetme ve izleme, bir sorun oluşması durumunda programların her zaman kaydedilebilmeleri için düşük ek iş yükü için tasarlanmıştır.

## <a name="net-core-apis"></a>.NET Çekirdek API'leri

### <a name="print-style-apis"></a>Yazdırma stili API'leri

, <xref:System.Console?displayProperty=nameWithType> <xref:System.Diagnostics.Trace?displayProperty=nameWithType>ve <xref:System.Diagnostics.Debug?displayProperty=nameWithType> sınıfların her biri günlük için uygun benzer yazdırma stili API'leri sağlar.

Hangi yazdırma stili API'sini kullanacağınız seçim size kalmış. Önemli farklar şunlardır:

- <xref:System.Console?displayProperty=nameWithType>
  - Her zaman etkin ve her zaman konsola yazıyor.
  - Müşterinizin sürümde görmesi gerekebileceği bilgiler için yararlıdır.
  - En basit yaklaşım olduğu için, genellikle geçici hata ayıklama için kullanılır. Bu hata ayıklama kodu genellikle kaynak denetimi için iade asla.
- <xref:System.Diagnostics.Trace?displayProperty=nameWithType>
  - Yalnızca tanımlandığında `TRACE` etkindir.
  - Ekli yazar <xref:System.Diagnostics.Trace.Listeners>, varsayılan <xref:System.Diagnostics.DefaultTraceListener>olarak .
  - Çoğu yapıda etkin olacak günlükleri oluştururken bu API'yi kullanın.
- <xref:System.Diagnostics.Debug?displayProperty=nameWithType>
  - Yalnızca tanımlandığında `DEBUG` etkindir.
  - Ekli hata ayıklama için yazıyor.
  - `COMPlus_DebugWriteToStdErr` Ayarlanırsa `*nix` stderr'a yazar.
  - Yalnızca hata ayıklama yapılarında etkinleştirilecek günlükleri oluştururken bu API'yi kullanın.

### <a name="logging-events"></a>Olayları kaydetme

Aşağıdaki API'ler daha fazla olay odaklıdır. Basit dizeleri günlüğe kaydetmek yerine olay nesnelerini kaydederler.

- <xref:System.Diagnostics.Tracing.EventSource?displayProperty=nameWithType>
  - EventSource birincil kök .NET Çekirdek izleme API'si.
  - Tüm .NET Standart sürümlerinde mevcuttur.
  - Yalnızca seri leştirilebilir nesnelerin izlenmesine izin verir.
  - Ekli [olay dinleyicilerine](xref:System.Diagnostics.Tracing.EventListener)yazar.
  - .NET Core dinleyici sağlar:
    - .NET Core'un EventPipe'ı tüm platformlarda
    - [Windows için Olay İzleme (ETW)](/windows/win32/etw/event-tracing-portal)
    - [LTTng Linux için izleme çerçevesi](https://lttng.org/)

- <xref:System.Diagnostics.DiagnosticSource?displayProperty=nameWithType>
  - .NET Core'a ve .NET Framework için [NuGet paketine](https://www.nuget.org/packages/System.Diagnostics.DiagnosticSource) dahildir.
  - Seri olmayan nesnelerin işlem içinde izlenmesini sağlar.
  - Günlüğe kaydedilmiş nesnelerin seçili alanlarının bir 'e <xref:System.Diagnostics.Tracing.EventSource>yazılmasına izin veren bir köprü içerir.

- <xref:System.Diagnostics.Activity?displayProperty=nameWithType>
  - Belirli bir etkinlik veya işlemden kaynaklanan günlük iletilerini tanımlamak için kesin bir yol sağlar. Bu nesne, farklı hizmetler arasında günlükleri ilişkilendirmek için kullanılabilir.

- <xref:System.Diagnostics.EventLog?displayProperty=nameWithType>
  - Yalnızca Windows.
  - Windows Olay Günlüğü'ne ileti yazar.
  - Sistem yöneticileri, Windows Olay Günlüğü'nde önemli uygulama hatası iletilerinin görünmesini bekler.

## <a name="ilogger-and-logging-frameworks"></a>ILogger ve günlük çerçeveleri

Düşük düzeyli API'ler günlük gereksinimleriniz için doğru seçim olmayabilir. Bir günlük çerçevesi düşünebilirsiniz.

Arabirim, <xref:Microsoft.Extensions.Logging.ILogger> loggers bağımlılık enjeksiyonu ile takılabilir ortak bir günlük arabirimi oluşturmak için kullanılmıştır.

Örneğin, uygulamanız `ASP.NET` için en iyi seçimi yapabilmenize izin vermek için yerleşik ve üçüncü taraf çerçeveleri bir seçim için destek sunar:

- [ASP.NET günlük sağlayıcılar yerleşik](/aspnet/core/fundamentals/logging/#built-in-logging-providers)
- [ASP.NET Üçüncü taraf günlük sağlayıcıları](/aspnet/core/fundamentals/logging/#third-party-logging-providers)

## <a name="logging-related-references"></a>İlgili başvuruları günlüğe kaydetme

- [Nasıl yapılır: İzleme ve Hata Ayıklama ile Koşullu Derleme](../../framework/debug-trace-profile/how-to-compile-conditionally-with-trace-and-debug.md)

- [Nasıl yapılır: Uygulama Koduna İzleme Deyimleri Ekleme](../../framework/debug-trace-profile/how-to-add-trace-statements-to-application-code.md)

- [ASP.NET Günlük,](/aspnet/core/fundamentals/logging) desteklediği günlük leme tekniklerine genel bir bakış sağlar.

- [C# String Enterpolasyonu](../../csharp/language-reference/tokens/interpolated.md) günlük kodu yazmayı basitleştirebilir.

- Özellik, <xref:System.Exception.Message?displayProperty=nameWithType> özel durumlar günlüğe kaydetme için yararlıdır.

- Sınıf <xref:System.Diagnostics.StackTrace?displayProperty=nameWithType> günlükleri yığın bilgi sağlamak için yararlı olabilir.

## <a name="performance-considerations"></a>Performansla ilgili önemli noktalar

Dize biçimlendirme fark edilir CPU işleme süresi alabilir.

Performans açısından kritik uygulamalarda şunları önermeniz önerilir:

- Kimse dinlemezken çok sayıda günlüğe kaydetmekten kaçının. Önce günlüğe kaydetme nin etkin olup olmadığını denetleyerek maliyetli günlük iletileri oluşturmaktan kaçının.
- Yalnızca yararlı olanı kaydedin.
- Süslü biçimlendirmeyi analiz aşamasına erteler.
