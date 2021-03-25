---
title: Günlüğe kaydetme ve izleme-.NET Core
description: .NET Core günlüğe kaydetme ve izlemeye giriş.
ms.date: 10/12/2020
ms.openlocfilehash: dfecdad4518c79b605eb4fbe991af07fcba7db1c
ms.sourcegitcommit: e16315d9f1ff355f55ff8ab84a28915be0a8e42b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105111094"
---
# <a name="net-core-logging-and-tracing"></a>.NET Core günlüğe kaydetme ve izleme

Günlüğe kaydetme ve izleme aynı teknik için gerçekten iki isimdir. Basit teknik, bilgisayarların erken günlerinde bu yana kullanılmıştır. Bu, daha sonra tüketilen çıktıyı yazmak için bir uygulamanın seçilmesini içerir.

## <a name="reasons-to-use-logging-and-tracing"></a>Günlüğe kaydetme ve izlemeyi kullanma nedenleri

Bu basit teknik şaşırtıcı bir biçimde güçlüdür. Bir hata ayıklayıcının başarısız olduğu durumlarda kullanılabilir:

- Uzun süre boyunca tekrar eden sorunları geleneksel bir hata ayıklayıcısıyla çözmek zor olabilir. Günlükler, uzun sürelere yayılan ayrıntılı son durum incelemeleri yapmanıza olanak verir. Buna karşın, hata ayıklayıcılar gerçek zamanlı analizle sınırlıdır.
- Çok iş parçacıklı ve dağıtılmış uygulamalarda hata ayıklamak genellikle zordur.  Hata ayıklayıcıyı kullanıma açmak, davranışları değiştirebilir. Ayrıntılı günlükler, karmaşık sistemleri anlamak için gerekli şekilde analiz edilebilir.
- Dağıtılmış uygulamalardaki sorunlar, pek çok bileşen arasındaki karmaşık etkileşimden kaynaklanabilir ve sistemin her parçasına bir hata ayıklayıcısı eklemek mantıklı olmayabilir.
- Çok sayıda hizmetin durdurulmaması gerekir. Hata ayıklayıcıyı kullanıma açmak genellikle zaman aşımı sorunlarına neden olur.
- Sorunlar her zaman öngörülemez. Günlüğe kaydetme ve izleme, sorun olması durumunda programların her zaman kayıt yapabilmesi için düşük ek yüke uygun şekilde tasarlanmıştır.

## <a name="net-core-apis"></a>.NET Core API 'Leri

### <a name="print-style-apis"></a>Yazdırma stili API 'Leri

<xref:System.Console?displayProperty=nameWithType>, <xref:System.Diagnostics.Trace?displayProperty=nameWithType> Ve <xref:System.Diagnostics.Debug?displayProperty=nameWithType> sınıflarının her biri, günlüğe kaydetme için uygun olan benzer yazdırma stili API 'leri sağlar.

Kullanılacak yazdırma stili API’si tercihi size bağlıdır. En önemli farklar şunlardır:

- <xref:System.Console?displayProperty=nameWithType>
  - Her zaman etkindir ve konsola yazar.
  - Müşterilerinizin yayında görmeleri gerekebilecek bilgiler için yararlıdır.
  - En basit yaklaşım bu olduğundan, genellikle geçici hata ayıklama için kullanılır. Bu hata ayıklama kodu kaynak denetiminde neredeyse asla kullanılmaz.
- <xref:System.Diagnostics.Trace?displayProperty=nameWithType>
  - Yalnızca `TRACE` , `#define TRACE` kaynağınıza eklenerek veya derlenirken seçeneği belirtilerek tanımlandığında etkindir `/d:TRACE` .
  - <xref:System.Diagnostics.Trace.Listeners>Varsayılan olarak, ekli öğesine yazar <xref:System.Diagnostics.DefaultTraceListener> .
  - Çoğu derlemede etkinleştirilecek olan günlükler oluştururken bu API’yi kullanın.
- <xref:System.Diagnostics.Debug?displayProperty=nameWithType>
  - Yalnızca `DEBUG` , `#define DEBUG` kaynağınıza eklenerek veya derlenirken seçeneği belirtilerek tanımlandığında etkindir `/d:DEBUG` .
  - Kullanıma açılan bir hata ayıklayıcıya yazar.
  - `*nix`Ayarlandıysa, stderr 'e yazma işlemleri `COMPlus_DebugWriteToStdErr` yapılır.
  - Yalnızca hata ayıklama derlemelerinde etkinleştirilecek günlükler oluştururken bu API’yi kullanın.

### <a name="logging-events"></a>Olayları günlüğe kaydetme

Aşağıdaki API 'Ler daha fazla olay yönelimlidir. Basit dizeleri günlüğe kaydetmek yerine olay nesnelerini günlüğe kaydeder.

- <xref:System.Diagnostics.Tracing.EventSource?displayProperty=nameWithType>
  - EventSource birincil kök .NET Core izleme API 'sidir.
  - Tüm .NET Standard sürümlerde kullanılabilir.
  - Yalnızca seri hale getirilebilir nesnelerin izlenmesini sağlar.
  - , EventSource öğesini kullanmak için yapılandırılmış herhangi bir [EventListener](xref:System.Diagnostics.Tracing.EventListener) örneği aracılığıyla işlem içi tüketilebilir.
  - Şu yollarla işlem dışı tüketilebilir:
    - Tüm platformlarda [.NET Core EventPipe](./eventpipe.md)
    - [Windows için olay Izleme (ETW)](/windows/win32/etw/event-tracing-portal)
    - [Linux için LTTng izleme çerçevesi](https://lttng.org/)
      - İzlenecek yol: [PerfCollect kullanarak bir LTTng Izlemesi toplayın](trace-perfcollect-lttng.md).

- <xref:System.Diagnostics.DiagnosticSource?displayProperty=nameWithType>
  - .NET Core 'a ve .NET Framework için bir [NuGet paketi](https://www.nuget.org/packages/System.Diagnostics.DiagnosticSource) olarak eklenmiştir.
  - Seri hale getirilebilir olmayan nesnelerin işlem içi izlenmesini sağlar.
  - Günlüğe kaydedilen nesnelerin seçili alanlarının bir öğesine yazılmasına izin veren bir köprü içerir <xref:System.Diagnostics.Tracing.EventSource> .

- <xref:System.Diagnostics.EventLog?displayProperty=nameWithType>
  - Yalnızca Windows.
  - İletileri Windows olay günlüğü 'ne yazar.
  - Sistem yöneticileri, önemli uygulama hata iletilerinin Windows olay günlüğünde görünmesini bekler.

## <a name="distributed-tracing"></a>Dağıtılmış Izleme

[Dağıtılmış izleme](./distributed-tracing.md) , özellikle birden çok makineye veya işleme dağılmış olabilecek uygulamalarda hataları ve performans sorunlarını yerelleştirebilmenizi sağlayan bir tanılama tekniğidir. Bu teknik, farklı uygulama bileşenleri tarafından yapılan bir uygulamayla bir araya geçen ve başka bir iş tarafından, uygulamanın eşzamanlı istekler için yapmakta olabileceği diğer çalışmalardan ayıran istekleri izler.

## <a name="ilogger-and-logging-frameworks"></a>ILogger ve günlük çerçeveleri

Düşük düzey API 'Ler, günlük gereksinimleriniz için doğru seçim olmayabilir. Bir günlük çerçevesini düşünmek isteyebilirsiniz.

<xref:Microsoft.Extensions.Logging.ILogger>Arabirim, günlükçülerin bağımlılık ekleme yoluyla eklenebileceği ortak bir günlüğe kaydetme arabirimi oluşturmak için kullanılır.

Örneğin, uygulamanızın .NET için en iyi seçimi yapmanıza olanak tanımak üzere yerleşik ve üçüncü taraf çerçeveler için destek sunar:

- [.NET yerleşik günlüğe kaydetme sağlayıcıları](../extensions/logging-providers.md#built-in-logging-providers)
- [.NET üçüncü taraf günlüğü sağlayıcıları](../extensions/logging-providers.md#third-party-logging-providers)

## <a name="logging-related-references"></a>Günlüğe kaydetme ilgili başvurular

- [Nasıl yapılır: İzleme ve Hata Ayıklama ile Koşullu Derleme](../../framework/debug-trace-profile/how-to-compile-conditionally-with-trace-and-debug.md)

- [Nasıl yapılır: Uygulama Koduna İzleme Deyimleri Ekleme](../../framework/debug-trace-profile/how-to-add-trace-statements-to-application-code.md)

- [.Net ' te oturum açmak](../extensions/logging.md) , desteklediği günlük tekniklerine genel bir bakış sağlar.

- [C# dize ilişkilendirme](../../csharp/language-reference/tokens/interpolated.md) , günlük kodu yazmayı kolaylaştırabilir.

- [Çalışma zamanı sağlayıcısı olay listesi](../../fundamentals/diagnostics/runtime-events.md)

- [.NET 'teki iyi bilinen olay sağlayıcıları](well-known-event-providers.md)

- <xref:System.Exception.Message?displayProperty=nameWithType>Özelliği, özel durumları günlüğe kaydetmek için yararlıdır.

- Bu <xref:System.Diagnostics.StackTrace?displayProperty=nameWithType> sınıf, günlüklerinizi yığın bilgileri sağlamak için yararlı olabilir.

## <a name="performance-considerations"></a>Performansla ilgili önemli noktalar

Dize biçimlendirmesi, fark edilebilir CPU işlem süresini alabilir.

Performans açısından kritik uygulamalarda şunları yapmanız önerilir:

- Hiç kimse dinlemediğinde çok fazla günlük tutulmasını önleyin. Önce günlük kaydının etkin olup olmadığını denetleyerek maliyetli günlük mesajları oluşturmaktan kaçının.
- Yalnızca yararlı olanları günlüğe kaydedin.
- Süslü biçimlendirmeyi analiz aşamasına erteleyin.
