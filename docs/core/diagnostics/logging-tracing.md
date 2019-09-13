---
title: Günlüğe kaydetme ve izleme-.NET Core
description: .NET Core günlüğe kaydetme ve izlemeye giriş.
author: sdmaclea
ms.author: stmaclea
ms.date: 08/05/2019
ms.openlocfilehash: 46e64a7f60b88c26ceef9ac817be885bfa180c8e
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70926358"
---
# <a name="net-core-logging-and-tracing"></a>.NET Core günlüğe kaydetme ve izleme

Günlüğe kaydetme ve izleme aynı teknik için gerçekten iki isimdir. Basit teknik, bilgisayarların erken günlerinde bu yana kullanılmıştır. Bu, daha sonra tüketilen çıktıyı yazmak için bir uygulamanın seçilmesini içerir.

## <a name="reasons-to-use-logging-and-tracing"></a>Günlüğe kaydetme ve izlemeyi kullanma nedenleri

Bu basit teknik, her ne kadar güçlü bir işlemdir. Bir hata ayıklayıcının başarısız olduğu durumlarda kullanılabilir:

- Uzun süreler boyunca oluşan sorunlar, geleneksel hata ayıklayıcı ile hata ayıklama zor olabilir. Günlükler, uzun sürelerle ilgili ayrıntılı son mortem incelemesi için izin verir. Buna karşılık, hata ayıklayıcılar gerçek zamanlı Analize göre kısıtlanmıştır.
- Çok iş parçacıklı uygulamalar ve dağıtılmış uygulamalar genellikle hata ayıklama için zordur.  Hata ayıklayıcı eklemek, davranışları değiştirme eğilimindedir. Ayrıntılı Günlükler, karmaşık sistemleri anlamak için gerektiği şekilde analiz edilebilir.
- Dağıtılmış uygulamalardaki sorunlar birçok bileşen arasındaki karmaşık bir etkileşime neden olabilir ve bir hata ayıklayıcıyı sistemin her bölümüne bağlamak mantıklı olmayabilir.
- Birçok hizmet durdurulmuş olmamalıdır. Hata ayıklayıcı iliştirmek genellikle zaman aşımı hatalarıyla neden olur.
- Sorunlar her zaman öngörülemeyen değildir. Günlüğe kaydetme ve izleme düşük yük için tasarlanmıştır, böylece bir sorun oluşması durumunda programlar her zaman kaydedebilir.

## <a name="net-core-apis"></a>.NET Core API 'Leri

### <a name="print-style-apis"></a>Yazdırma stili API 'Leri

<xref:System.Console?displayProperty=nameWithType>, Ve <xref:System.Diagnostics.Trace?displayProperty=nameWithType> sınıflarınınherbiri,günlüğekaydetmeiçinuygun<xref:System.Diagnostics.Debug?displayProperty=nameWithType> olan benzer yazdırma stili API 'leri sağlar.

Hangi yazdırma stili API 'sinin kullanılması tercih edilir. Temel farklılıklar şunlardır:

- <xref:System.Console?displayProperty=nameWithType>
  - Her zaman etkin ve her zaman konsola yazar.
  - Müşterinizin yayında görmeniz gerekebilecek bilgiler için faydalıdır.
  - En basit yaklaşım olduğundan, genellikle geçici geçici hata ayıklama için kullanılır. Bu hata ayıklama kodu genellikle kaynak denetimine hiçbir zaman iade edilmedi.
- <xref:System.Diagnostics.Trace?displayProperty=nameWithType>
  - Yalnızca tanımlı olduğunda `TRACE` etkindir.
  - Varsayılan olarak, <xref:System.Diagnostics.Trace.Listeners> <xref:System.Diagnostics.DefaultTraceListener>ekli öğesine yazar.
  - Çoğu derlemelerde etkinleştirilecek günlükleri oluştururken bu API 'YI kullanın.
- <xref:System.Diagnostics.Debug?displayProperty=nameWithType>
  - Yalnızca tanımlı olduğunda `DEBUG` etkindir.
  - Ekli bir hata ayıklayıcıya yazar.
  - Ayarlandıysa ,`COMPlus_DebugWriteToStdErr` stderr 'e `*nix` yazma işlemleri yapılır.
  - Yalnızca hata ayıklama yapılarında etkinleştirilecek günlükleri oluştururken bu API 'YI kullanın.

### <a name="logging-events"></a>Olayları günlüğe kaydetme

Aşağıdaki API 'Ler daha fazla olay yönelimlidir. Basit dizeleri günlüğe kaydetmek yerine olay nesnelerini günlüğe kaydeder.

- <xref:System.Diagnostics.Tracing.EventSource?displayProperty=nameWithType>
  - EventSource birincil kök .NET Core izleme API 'sidir.
  - Tüm .NET Standard sürümlerde kullanılabilir.
  - Yalnızca seri hale getirilebilir nesnelerin izlenmesini sağlar.
  - Ekli [olay dinleyicilerine](xref:System.Diagnostics.Tracing.EventListener)yazar.
  - .NET Core için dinleyicileri sağlar:
    - Tüm platformlarda .NET Core EventPipe
    - [Windows için olay Izleme (ETW)](/windows/win32/etw/event-tracing-portal)
    - [Linux için LTTng izleme çerçevesi](https://lttng.org/)

- <xref:System.Diagnostics.DiagnosticSource?displayProperty=nameWithType>
  - .NET Core 'a ve .NET Framework için bir [NuGet paketi](https://www.nuget.org/packages/System.Diagnostics.DiagnosticSource) olarak eklenmiştir.
  - Seri hale getirilebilir olmayan nesnelerin işlem içi izlenmesini sağlar.
  - Günlüğe kaydedilen nesnelerin seçili alanlarının bir <xref:System.Diagnostics.Tracing.EventSource>öğesine yazılmasına izin veren bir köprü içerir.

- <xref:System.Diagnostics.Activity?displayProperty=nameWithType>
  - Belirli bir etkinlik veya işlemden kaynaklanan günlük iletilerini belirlemek için kesin bir yol sağlar. Bu nesne, farklı hizmetlerde günlükleri ilişkilendirmek için kullanılabilir.

- <xref:System.Diagnostics.EventLog?displayProperty=nameWithType>
  - Yalnızca Windows.
  - İletileri Windows olay günlüğü 'ne yazar.
  - Sistem yöneticileri, önemli uygulama hata iletilerinin Windows olay günlüğünde görünmesini bekler.

## <a name="ilogger-and-logging-frameworks"></a>ILogger ve günlük çerçeveleri

Düşük düzey API 'Ler, günlük gereksinimleriniz için doğru seçim olmayabilir. Bir günlük çerçevesini düşünmek isteyebilirsiniz.

<xref:Microsoft.Extensions.Logging.ILogger> Arabirim, günlükçülerin bağımlılık ekleme yoluyla eklenebileceği ortak bir günlüğe kaydetme arabirimi oluşturmak için kullanılır.

Örneğin, uygulamanız `ASP.NET` için en iyi seçimi yapmanıza olanak tanımak için yerleşik ve üçüncü taraf çerçeveler için destek sunar:

- [ASP.NET yerleşik günlük sağlayıcıları](/aspnet/core/fundamentals/logging/#built-in-logging-providers)
- [ASP.NET üçüncü taraf günlüğü sağlayıcıları](/aspnet/core/fundamentals/logging/#third-party-logging-providers)

## <a name="logging-related-references"></a>Günlüğe kaydetme ilgili başvurular

- [Nasıl yapılır: Izleme ve hata ayıklama ile koşullu derleme](../../framework/debug-trace-profile/how-to-compile-conditionally-with-trace-and-debug.md)

- [Nasıl yapılır: Uygulama koduna Izleme deyimleri ekleme](../../framework/debug-trace-profile/how-to-add-trace-statements-to-application-code.md)

- [ASP.net günlüğü](/aspnet/core/fundamentals/logging) , desteklediği günlük tekniklerine genel bir bakış sağlar.

- Dize ilişkilendirme, günlük kodu yazmayı kolaylaştırabilir. [ C# ](../../csharp/language-reference/tokens/interpolated.md)

- Özelliği <xref:System.Exception.Message?displayProperty=nameWithType> , özel durumları günlüğe kaydetmek için yararlıdır.

- Bu <xref:System.Diagnostics.StackTrace?displayProperty=nameWithType> sınıf, günlüklerinizi yığın bilgileri sağlamak için yararlı olabilir.

## <a name="performance-considerations"></a>Performans değerlendirmeleri

Dize biçimlendirmesi, fark edilebilir CPU işlem süresini alabilir.

Performans açısından kritik uygulamalarda şunları yapmanız önerilir:

- Hiç kimse dinlemediğinde çok fazla günlük tutulmasını önleyin. Önce günlük kaydının etkin olup olmadığını denetleyerek maliyetli günlük mesajları oluşturmaktan kaçının.
- Yalnızca yararlı olanları günlüğe kaydedin.
- Süslü biçimlendirmeyi analiz aşamasına erteleyin.
