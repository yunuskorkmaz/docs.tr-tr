---
title: DotNet-Trace-.NET Core
description: DotNet-Trace komut satırı aracını yükleme ve kullanma.
author: sdmaclea
ms.author: stmaclea
ms.date: 10/14/2019
ms.openlocfilehash: 6513cf63070bc1984006da75313e9912d76a6c95
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72321584"
---
# <a name="trace-for-performance-analysis-utility-dotnet-trace"></a>Performans Analizi yardımcı programı için izleme (`dotnet-trace`)

**Bu makale şu şekilde geçerlidir:** .net Core 3,0 SDK ve sonraki sürümleri

## <a name="installing-dotnet-trace"></a>`dotnet-trace` yükleme

`dotnet-trace` [NuGet paketinin](https://www.nuget.org/packages/dotnet-trace)en son sürümünü yüklemek için [DotNet aracı install](../tools/dotnet-tool-install.md) komutunu kullanın:

```dotnetcli
dotnet tool install --global dotnet-trace
```

## <a name="synopsis"></a>Özeti

```console
dotnet-trace [-h, --help] [--version] <command>
```

## <a name="description"></a>Açıklama

`dotnet-trace` Aracı, herhangi bir yerel profil oluşturucu olmadan çalışan bir işlemin .NET Core izlemelerinin toplanmasını sağlayan platformlar arası CLı genel aracıdır. .NET Core çalışma zamanının platformlar arası `EventPipe` teknolojisi etrafında oluşturulmuştur. `dotnet-trace`, Windows, Linux veya macOS 'ta aynı deneyimi sunar.

## <a name="options"></a>Seçenekler

- **`--version`**

DotNet-Counters yardımcı programının sürümünü görüntüleyin.

- **`-h|--help`**

Komut satırı yardımını göster.

## <a name="commands"></a>Komutlar

| Komut                                                     |
| ----------------------------------------------------------- |
| [DotNet-izleme toplama](#dotnet-trace-collect)               |
| [DotNet-Trace Dönüştür](#dotnet-trace-convert)               |
| [DotNet-izleme listesi-süreçler](#dotnet-trace-list-processes) |
| [DotNet-izleme listesi-profiller](#dotnet-trace-list-profiles)   |

## <a name="dotnet-trace-collect"></a>DotNet-izleme toplama

Çalışan bir işlemden bir tanılama izlemesi toplar.

### <a name="synopsis"></a>Özeti

```console
dotnet-trace collect [-h|--help] [-p|--process-id] [--buffersize <size>] [-o|--output]
    [--providers] [--profile <profile-name>] [--format]
```

### <a name="options"></a>Seçenekler

- **`-p|--process-id <PID>`**

  İzlemeyi toplama işlemi.

- **`--buffersize <size>`**

  Bellek içi dairesel arabelleğin boyutunu megabayt cinsinden ayarlar. Varsayılan 256 MB.

- **`-o|--output <trace-file-path>`**

  Toplanan izleme verileri için çıkış yolu. Belirtilmemişse, varsayılan olarak `trace.nettrace`olur.

- **`--providers <list-of-comma-separated-providers>`**

  Etkinleştirilecek `EventPipe` sağlayıcılarının virgülle ayrılmış listesi. Bu sağlayıcılar `--profile <profile-name>`tarafından kapsanan tüm sağlayıcıları tamamlar. Belirli bir sağlayıcı için herhangi bir tutarsızlık varsa, buradaki yapılandırma profilden örtük yapılandırma üzerinden önceliklidir.

  Bu sağlayıcı listesi şu biçimdedir:

  - `Provider[,Provider]`
  - `Provider` şu biçimdedir: `KnownProviderName[:Flags[:Level][:KeyValueArgs]]`.
  - `KeyValueArgs` şu biçimdedir: `[key1=value1][;key2=value2]`.

- **`--profile <profile-name>`**

  Yaygın izleme senaryolarına izin veren önceden tanımlanmış adlandırılmış bir dizi sağlayıcı yapılandırması succinctly.

- **`--format <NetTrace|Speedscope>`**

  İzleme dosyası dönüştürmesi için çıkış biçimini ayarlar.

## <a name="dotnet-trace-convert"></a>DotNet-Trace Dönüştür

Alternatif izleme çözümleme araçlarıyla kullanılmak üzere `nettrace` izlemelerini alternatif biçimlere dönüştürür.

### <a name="synopsis"></a>Özeti

```console
dotnet-trace convert [<input-filename>] [-h|--help] [--format] [-o|--output]
```

### <a name="arguments"></a>Bağımsız Değişkenler

- **`<input-filename>`**

  Dönüştürülecek giriş izleme dosyası. *Trace. NetTrace*için varsayılanlar.

### <a name="options"></a>Seçenekler

- **`--format <NetTrace|Speedscope>`**

  İzleme dosyası dönüştürmesi için çıkış biçimini ayarlar.

- **`-o|--output <output-filename>`**

  Çıkış dosya adı. Hedef biçimin uzantısı eklenecek.

## <a name="dotnet-trace-list-processes"></a>DotNet-izleme listesi-süreçler

İzlenebilir DotNet süreçlerini listeler.

### <a name="synopsis"></a>Özeti

```console
dotnet-trace list-processes [-h|--help]
```

## <a name="dotnet-trace-list-profiles"></a>DotNet-izleme listesi-profiller

Her profilde hangi sağlayıcıların ve filtrelerin olduğuna ilişkin bir açıklama ile önceden oluşturulmuş izleme profillerini listeler.

### <a name="synopsis"></a>Özeti

```console
dotnet-trace list-profiles [-h|--help]
```

## <a name="collect-a-trace-with-dotnet-trace"></a>`dotnet-trace` bir izleme toplayın

- `dotnet-trace`kullanarak izlemeleri toplamak için öncelikle .NET Core uygulamasının işlem tanımlayıcısını (PID), izlemeleri toplanacak şekilde bulmanız gerekir.

  - Windows 'ta, Görev Yöneticisi veya `tasklist` komutunu kullanma gibi seçenekler vardır.
  - Linux 'ta, önemsiz seçeneği `ps` komutu kullanıyor olabilir.

Ayrıca, hangi .NET Core işlemlerinin çalıştığını, bunların PID 'leri ile birlikte öğrenmek için [DotNet-Trace List-Processes](#dotnet-trace-list-processes) komutunu da kullanabilirsiniz.

- Ardından, aşağıdaki komutu çalıştırın:

```console
> dotnet-trace collect --process-id <PID>

Press <Enter> to exit...
Connecting to process: <Full-Path-To-Process-Being-Profiled>/dotnet.exe
Collecting to file: <Full-Path-To-Trace>/trace.nettrace
  Session Id: <SessionId>
  Recording trace 721.025 (KB)
```

- Son olarak, `<Enter>` tuşuna basarak toplamayı durdurun ve `dotnet-trace` `trace.nettrace` dosyasına günlük olaylarını tamamlayacak.

## <a name="viewing-the-trace-captured-from-dotnet-trace"></a>`dotnet-trace` yakalanan izlemeyi görüntüleme

Windows 'da, `.nettrace` dosyaları yalnızca ETW veya LTTng ile toplanan izlemeler gibi, analiz için [PerfView](https://github.com/microsoft/perfview) üzerinde görüntülenebilir. Linux 'ta toplanan izlemeler için, izlemeyi PerfView 'da görüntülenmek üzere bir Windows makinesine taşıyabilirsiniz.

Ayrıca, `dotnet-trace` çıkış biçimini `speedscope`olarak değiştirerek bir Linux makinesinde izlemeyi görüntüleyebilirsiniz. `-f|--format` seçeneğini kullanarak çıkış dosyası biçimini değiştirebilirsiniz-`-f speedscope`, `dotnet-trace` `speedscope` bir dosya üretmesine yol açabilir. Şu anda `nettrace` (varsayılan seçenek) ve `speedscope`arasından seçim yapabilirsiniz. `Speedscope` dosyalar <https://www.speedscope.app>açılabilirler.

> [!NOTE]
> .NET Core çalışma zamanı, izlemeleri `nettrace` biçiminde oluşturur ve izleme tamamlandıktan sonra speedscope (belirtilmişse) olarak dönüştürülür. Bazı dönüştürmeler veri kaybına neden olabileceğinden, özgün `nettrace` dosyası Dönüştürülen dosyanın yanında korunur.

## <a name="using-dotnet-trace-to-collect-counter-values-over-time"></a>Zaman içinde sayaç değerlerini toplamak için `dotnet-trace` kullanma

Üretim ortamları gibi performans duyarlı ayarlarda temel sistem durumu izleme için `EventCounter` kullanmaya çalışıyorsanız ve bunları gerçek zamanlı olarak izlemek yerine izlemeleri toplamak istiyorsanız, bunu `dotnet-trace` da yapabilirsiniz.

Örneğin, çalışma zamanı performans sayacı değerlerini toplamak istiyorsanız aşağıdaki komutu kullanabilirsiniz:

```console
dotnet-trace collect --process-id <PID> --providers System.Runtime:0:1:EventCounterIntervalSec=1
```

Bu komut, hafif sistem durumu izleme için çalışma zamanı sayaçlarına her saniye bir kez rapor vermesini söyler. `EventCounterIntervalSec=1` daha yüksek bir değerle değiştirmek (örneğin, 60) sayaç verilerinde daha az ayrıntı düzeyi olan daha küçük bir izleme toplamanıza olanak tanır.

Ek yükü (ve izleme boyutunu) daha da azaltmak üzere çalışma zamanı olaylarını devre dışı bırakmak istiyorsanız, çalışma zamanı olaylarını ve yönetilen yığın profil oluşturucuyu devre dışı bırakmak için aşağıdaki komutu kullanabilirsiniz.

```console
dotnet-trace collect --process-id <PID> --providers System.Runtime:0:1:EventCounterIntervalSec=1,Microsoft-Windows-DotNETRuntime:0:1,Microsoft-DotNETCore-SampleProfiler:0:1
```

## <a name="net-providers"></a>.NET sağlayıcıları

.NET Core çalışma zamanı, aşağıdaki .NET sağlayıcılarını destekler. .NET Core hem `Event Tracing for Windows (ETW)` hem de `EventPipe` izlemelerini etkinleştirmek için aynı anahtar kelimeleri kullanır.

| Sağlayıcı adı                            | Bilgiler |
|------------------------------------------|-------------|
| `Microsoft-Windows-DotNETRuntime`        | [Çalışma zamanı sağlayıcısı](../../framework/performance/clr-etw-providers.md#the-runtime-provider)<br>[CLR çalışma zamanı anahtar sözcükleri](../../framework/performance/clr-etw-keywords-and-levels.md#runtime) |
| `Microsoft-Windows-DotNETRuntimeRundown` | [Özet sağlayıcı](../../framework/performance/clr-etw-providers.md#the-rundown-provider)<br>[CLR Özeti anahtar sözcükleri](../../framework/performance/clr-etw-keywords-and-levels.md#rundown) |
| `Microsoft-DotNETCore-SampleProfiler`    | Örnek profil oluşturucuyu etkinleştirilir. |
