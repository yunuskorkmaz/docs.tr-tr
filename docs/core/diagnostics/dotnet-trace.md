---
title: DotNet-izleme aracı-.NET Core
description: DotNet-Trace komut satırı aracını yükleme ve kullanma.
ms.date: 11/21/2019
ms.openlocfilehash: 6dd968dc49522229dca02c0dc6f3de898026dd82
ms.sourcegitcommit: 40de8df14289e1e05b40d6e5c1daabd3c286d70c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/22/2020
ms.locfileid: "86924857"
---
# <a name="dotnet-trace-performance-analysis-utility"></a>DotNet-izleme performansı Analizi yardımcı programı

**Bu makale şu şekilde geçerlidir:** ✔️ .net Core 3,0 SDK ve sonraki sürümleri

## <a name="install-dotnet-trace"></a>DotNet 'yi Install-Trace

`dotnet-trace` [DotNet aracı install](../tools/dotnet-tool-install.md) komutuyla [NuGet paketini](https://www.nuget.org/packages/dotnet-trace) yükler:

```dotnetcli
dotnet tool install --global dotnet-trace
```

## <a name="synopsis"></a>Özeti

```console
dotnet-trace [-h, --help] [--version] <command>
```

## <a name="description"></a>Açıklama

`dotnet-trace`Araç:

* , Platformlar arası bir .NET Core aracıdır.
* Yerel bir profil oluşturucu olmadan çalışan bir işlemin .NET Core izlemelerinin toplanmasını mümkün bir şekilde sunar.
* , `EventPipe` .NET Core çalışma zamanının platformlar arası teknolojisi etrafında oluşturulmuştur.
* Windows, Linux veya macOS 'ta aynı deneyimi sunar.

## <a name="options"></a>Seçenekler

- **`--version`**

  DotNet-Trace yardımcı programının sürümünü görüntüler.

- **`-h|--help`**

  Komut satırı yardımını gösterir.

## <a name="commands"></a>Komutlar

| Komut                                                   |
|-----------------------------------------------------------|
| [DotNet-izleme toplama](#dotnet-trace-collect)             |
| [DotNet-Trace Dönüştür](#dotnet-trace-convert)             |
| [DotNet-izleme PS 'si](#dotnet-trace-ps)                       |
| [DotNet-izleme listesi-profiller](#dotnet-trace-list-profiles) |

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

  Toplanan izleme verileri için çıkış yolu. Belirtilmemişse, varsayılan olarak `trace.nettrace` .

- **`--providers <list-of-comma-separated-providers>`**

  Etkinleştirilecek sağlayıcıların virgülle ayrılmış listesi `EventPipe` . Bu sağlayıcılar tarafından kapsanan tüm sağlayıcıları tamamlar `--profile <profile-name>` . Belirli bir sağlayıcı için herhangi bir tutarsızlık varsa, bu yapılandırma profilden örtük yapılandırmadan önceliklidir.

  Bu sağlayıcı listesi şu biçimdedir:

  - `Provider[,Provider]`
  - `Provider`Şu biçimdedir: `KnownProviderName[:Flags[:Level][:KeyValueArgs]]` .
  - `KeyValueArgs`Şu biçimdedir: `[key1=value1][;key2=value2]` .

- **`--profile <profile-name>`**

  Yaygın izleme senaryolarına izin veren önceden tanımlanmış adlandırılmış bir dizi sağlayıcı yapılandırması succinctly.

- **`--format {NetTrace|Speedscope}`**

  İzleme dosyası dönüştürmesi için çıkış biçimini ayarlar. Varsayılan değer: `NetTrace`.

## <a name="dotnet-trace-convert"></a>DotNet-Trace Dönüştür

`nettrace`Diğer izleme çözümleme araçlarıyla birlikte kullanmak üzere izlemeleri alternatif biçimlere dönüştürür.

### <a name="synopsis"></a>Özeti

```console
dotnet-trace convert [<input-filename>] [-h|--help] [--format] [-o|--output]
```

### <a name="arguments"></a>Arguments

- **`<input-filename>`**

  Dönüştürülecek giriş izleme dosyası. *Trace. NetTrace*için varsayılanlar.

### <a name="options"></a>Seçenekler

- **`--format <NetTrace|Speedscope>`**

  İzleme dosyası dönüştürmesi için çıkış biçimini ayarlar.

- **`-o|--output <output-filename>`**

  Çıkış dosya adı. Hedef biçimin uzantısı eklenecek.

## <a name="dotnet-trace-ps"></a>DotNet-izleme PS 'si

İliştirilebilecek DotNet süreçlerini listeler.

### <a name="synopsis"></a>Özeti

```console
dotnet-trace ps [-h|--help]
```

## <a name="dotnet-trace-list-profiles"></a>DotNet-izleme listesi-profiller

Her profilde hangi sağlayıcıların ve filtrelerin olduğuna ilişkin bir açıklama ile önceden oluşturulmuş izleme profillerini listeler.

### <a name="synopsis"></a>Özeti

```console
dotnet-trace list-profiles [-h|--help]
```

## <a name="collect-a-trace-with-dotnet-trace"></a>DotNet-Trace ile izleme toplama

Kullanarak izlemeleri toplamak için `dotnet-trace` :

- İzlemeleri toplanacak .NET Core uygulamasının işlem tanımlayıcısını (PID) alın.

  - Windows üzerinde, örneğin, Görev Yöneticisi 'ni veya `tasklist` komutunu kullanabilirsiniz.
  - Linux 'ta, örneğin, `ps` komutu.
  - [DotNet-izleme PS 'si](#dotnet-trace-ps)

- Şu komutu çalıştırın:

  ```console
  dotnet-trace collect --process-id <PID>
  ```

  Yukarıdaki komut aşağıdakine benzer bir çıktı oluşturur:

  ```console
  Press <Enter> to exit...
  Connecting to process: <Full-Path-To-Process-Being-Profiled>/dotnet.exe
  Collecting to file: <Full-Path-To-Trace>/trace.nettrace
  Session Id: <SessionId>
  Recording trace 721.025 (KB)
  ```

- Anahtara basarak toplamayı durdurun `<Enter>` . `dotnet-trace`olayları *izleme. NetTrace* dosyasına kaydetme işlemi tamamlanır.

## <a name="view-the-trace-captured-from-dotnet-trace"></a>DotNet 'den yakalanan izlemeyi görüntüleyin-Trace

Windows 'da *. NetTrace* dosyaları analiz Için [PerfView](https://github.com/microsoft/perfview) üzerinde görüntülenebilir: diğer platformlarda toplanan izlemeler Için, izleme dosyası PerfView 'Da görüntülenmek üzere bir Windows makinesine taşınabilir.

Linux 'ta izleme, ' nin çıkış biçimi değiştirilerek görüntülenebilir `dotnet-trace` `speedscope` . Çıkış dosyası biçimi, seçeneği kullanılarak değiştirilebilir, `-f|--format` `-f speedscope` `dotnet-trace` bir `speedscope` dosya oluşturur. `nettrace`(Varsayılan seçenek) ve arasında seçim yapabilirsiniz `speedscope` . `Speedscope`dosyalar ' de açılabilir <https://www.speedscope.app> .

> [!NOTE]
> .NET Core çalışma zamanı, biçimde izleme oluşturur `nettrace` . İzlemeler, izleme tamamlandıktan sonra speedscope (belirtilmişse) olarak dönüştürülür. Bazı dönüştürmeler veri kaybına neden olabileceğinden, özgün `nettrace` Dosya Dönüştürülen dosyanın yanında korunur.

## <a name="use-dotnet-trace-to-collect-counter-values-over-time"></a>Zaman içinde sayaç değerlerini toplamak için DotNet-Trace kullanın

`dotnet-trace`erişebilirsiniz

* `EventCounter`Performans duyarlı ortamlarda temel sistem durumu izleme için kullanın. Örneğin, üretimde.
* İzlemeleri toplayın, böylece gerçek zamanlı olarak görüntülenmesi gerekmez.

Örneğin, çalışma zamanı performans sayacı değerlerini toplamak için aşağıdaki komutu kullanın:

```console
dotnet-trace collect --process-id <PID> --providers System.Runtime:0:1:EventCounterIntervalSec=1
```

Yukarıdaki komut, hafif sistem durumu izleme için çalışma zamanı sayaçlarına her saniye bir kez rapor vermesini söyler. `EventCounterIntervalSec=1`Daha yüksek bir değerle değiştirme (örneğin, 60) sayaç verilerinde daha az ayrıntı düzeyi olan daha küçük bir izlemenin toplanmasını sağlar.

Aşağıdaki komut ek yükü ve izleme boyutunu önceki olandan daha fazla azaltır:

```console
dotnet-trace collect --process-id <PID> --providers System.Runtime:0:1:EventCounterIntervalSec=1,Microsoft-Windows-DotNETRuntime:0:1,Microsoft-DotNETCore-SampleProfiler:0:1
```

Yukarıdaki komut, çalışma zamanı olaylarını ve yönetilen yığın profil oluşturucuyu devre dışı bırakır.

## <a name="net-providers"></a>.NET sağlayıcıları

.NET Core çalışma zamanı, aşağıdaki .NET sağlayıcılarını destekler. .NET Core, `Event Tracing for Windows (ETW)` ve izlemelerinin etkinleştirilmesi için aynı anahtar kelimeleri kullanır `EventPipe` .

| Sağlayıcı adı                            | Bilgi |
|------------------------------------------|-------------|
| `Microsoft-Windows-DotNETRuntime`        | [Çalışma zamanı sağlayıcısı](../../framework/performance/clr-etw-providers.md#the-runtime-provider)<br>[CLR çalışma zamanı anahtar sözcükleri](../../framework/performance/clr-etw-keywords-and-levels.md#runtime) |
| `Microsoft-Windows-DotNETRuntimeRundown` | [Özet sağlayıcı](../../framework/performance/clr-etw-providers.md#the-rundown-provider)<br>[CLR Özeti anahtar sözcükleri](../../framework/performance/clr-etw-keywords-and-levels.md#rundown) |
| `Microsoft-DotNETCore-SampleProfiler`    | Örnek profil oluşturucuyu etkinleştirilir. |
