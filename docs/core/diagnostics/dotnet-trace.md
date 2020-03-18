---
title: dotnet izleme aracı - .NET Core
description: Dotnet izleme komut satırı aracını yüklemek ve kullanmak.
ms.date: 11/21/2019
ms.openlocfilehash: b19b159636fbf57fa2d461b398fcf9234aab491c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "76737652"
---
# <a name="dotnet-trace-performance-analysis-utility"></a>dotnet-trace performans analizi programı

**Bu makale şu şekilde dir:** ✔️ .NET Core 3.0 SDK ve sonraki sürümler

## <a name="install-dotnet-trace"></a>Dotnet izleme yükleme

`dotnet-trace` [Dotnet araç yükleme](../tools/dotnet-tool-install.md) komutu ile [NuGet paketini](https://www.nuget.org/packages/dotnet-trace) yükleyin:

```dotnetcli
dotnet tool install --global dotnet-trace
```

## <a name="synopsis"></a>Özet

```console
dotnet-trace [-h, --help] [--version] <command>
```

## <a name="description"></a>Açıklama

Araç: `dotnet-trace`

* Bir çapraz platform .NET Core aracıdır.
* Yerel profil oluşturucu olmadan çalışan bir işlemin .NET Core izlerinin toplanmasını sağlar.
* .NET Core çalışma `EventPipe` zamanının çapraz platform teknolojisi etrafında oluşturulmuştur.
* Windows, Linux veya macOS'ta da aynı deneyimi sunar.

## <a name="options"></a>Seçenekler

- **`--version`**

  Dotnet sayaçları yardımcı programı sürümünü görüntüler.

- **`-h|--help`**

  Komut satırı yardımlarını gösterir.

## <a name="commands"></a>Komutlar

| Komut                                                     |
| ----------------------------------------------------------- |
| [dotnet-iz toplama](#dotnet-trace-collect)               |
| [dotnet izleme dönüştürme](#dotnet-trace-convert)               |
| [dotnet izleme ps](#dotnet-trace-ps) |
| [dotnet izleme listesi-profilleri](#dotnet-trace-list-profiles)   |

## <a name="dotnet-trace-collect"></a>dotnet-iz toplama

Çalışan bir işlemden tanılama izi toplar.

### <a name="synopsis"></a>Özet

```console
dotnet-trace collect [-h|--help] [-p|--process-id] [--buffersize <size>] [-o|--output]
    [--providers] [--profile <profile-name>] [--format]
```

### <a name="options"></a>Seçenekler

- **`-p|--process-id <PID>`**

  İzi toplama işlemi.

- **`--buffersize <size>`**

  Megabaytlar halinde bellek içi dairesel arabellek boyutunu ayarlar. Varsayılan 256 MB.

- **`-o|--output <trace-file-path>`**

  Toplanan izleme verilerinin çıktı yolu. Belirtilmemişse `trace.nettrace`varsayılan olarak .

- **`--providers <list-of-comma-separated-providers>`**

  Etkinleştirilecek virgülle `EventPipe` ayrılmış sağlayıcılistesi. Bu sağlayıcılar tarafından `--profile <profile-name>`ima herhangi bir sağlayıcılar tamam. Belirli bir sağlayıcı için herhangi bir tutarsızlık varsa, bu yapılandırma profildeki örtük yapılandırmadan önce gelir.

  Bu sağlayıcı listesi şu şekildedir:

  - `Provider[,Provider]`
  - `Provider`şeklindedir: `KnownProviderName[:Flags[:Level][:KeyValueArgs]]`.
  - `KeyValueArgs`şeklindedir: `[key1=value1][;key2=value2]`.

- **`--profile <profile-name>`**

  Ortak izleme senaryolarının kısa bir şekilde belirtilmesine olanak tanıyan önceden tanımlanmış sağlayıcı yapılandırmaları kümesi.

- **`--format {NetTrace|Speedscope}`**

  İzleme dosyası dönüştürmeiçin çıktı biçimini ayarlar. Varsayılan değer: `NetTrace`.

## <a name="dotnet-trace-convert"></a>dotnet izleme dönüştürme

`nettrace` İzlemeleri alternatif izleme çözümleme araçlarıyla kullanılmak üzere alternatif biçimlere dönüştürür.

### <a name="synopsis"></a>Özet

```console
dotnet-trace convert [<input-filename>] [-h|--help] [--format] [-o|--output]
```

### <a name="arguments"></a>Bağımsız Değişkenler

- **`<input-filename>`**

  Dönüştürülecek giriş izleme dosyası. *Trace.nettrace*için varsayılan .

### <a name="options"></a>Seçenekler

- **`--format <NetTrace|Speedscope>`**

  İzleme dosyası dönüştürmeiçin çıktı biçimini ayarlar.

- **`-o|--output <output-filename>`**

  Çıktı dosya adı. Hedef biçiminin uzantısı eklenecektir.

## <a name="dotnet-trace-ps"></a>dotnet izleme ps

Ekilen dotnet işlemlerini listeler.

### <a name="synopsis"></a>Özet

```console
dotnet-trace ps [-h|--help]
```

## <a name="dotnet-trace-list-profiles"></a>dotnet izleme listesi-profilleri

Her profilde hangi sağlayıcıların ve filtrelerin bulunduğuna dikkat içeren önceden oluşturulmuş izleme profillerini listeler.

### <a name="synopsis"></a>Özet

```console
dotnet-trace list-profiles [-h|--help]
```

## <a name="collect-a-trace-with-dotnet-trace"></a>Dotnet-trace ile bir izleme toplamak

Kullanarak `dotnet-trace`izleri toplamak için:

- İzleri toplamak için .NET Core uygulamasının işlem tanımlayıcısını (PID) alın.

  - Windows'da, örneğin Görev Yöneticisi'ni veya komutu `tasklist` kullanabilirsiniz.
  - Linux'ta, örneğin, `ps` komut.
  - [dotnet izleme ps](#dotnet-trace-ps)

- Şu komutu çalıştırın:

  ```console
  dotnet-trace collect --process-id <PID>
  ```

  Önceki komut aşağıdakine benzer çıktı üretir:

  ```console
  Press <Enter> to exit...
  Connecting to process: <Full-Path-To-Process-Being-Profiled>/dotnet.exe
  Collecting to file: <Full-Path-To-Trace>/trace.nettrace
  Session Id: <SessionId>
  Recording trace 721.025 (KB)
  ```

- Tuşa basarak `<Enter>` koleksiyonu durdurun. `dotnet-trace`*trace.nettrace* dosyasına günlüğe kaydetme olayını tamamlayacaktır.

## <a name="view-the-trace-captured-from-dotnet-trace"></a>dotnet-trace'den yakalanan izi görüntüleme

*Windows'da,.nettrace* dosyaları analiz için [PerfView'da](https://github.com/microsoft/perfview) görüntülenebilir: Diğer platformlarda toplanan izlemeler için izleme dosyası PerfView'da görüntülenecek bir Windows makinesine taşınabilir.

Linux'ta, izleme çıkış biçimini `dotnet-trace` değiştirerek `speedscope`görüntülenebilir. Çıktı dosyası biçimi `-f|--format` seçeneği kullanılarak değiştirilebilir `-f speedscope` - `dotnet-trace` bir `speedscope` dosya üretmek yapacaktır. Aralarında `nettrace` (varsayılan seçenek) ve `speedscope`. `Speedscope`dosyaları ' dan <https://www.speedscope.app>açılabilir.

> [!NOTE]
> .NET Core çalışma süresi `nettrace` biçiminde izlemeler oluşturur. İzleme tamamlandıktan sonra izlemeler hız stobuna (belirtilmişse) dönüştürülür. Bazı dönüşümler veri kaybına neden olabileceğinden, özgün `nettrace` dosya dönüştürülen dosyanın yanında korunur.

## <a name="use-dotnet-trace-to-collect-counter-values-over-time"></a>Zaman içinde sayaç değerlerini toplamak için dotnet izleme

`dotnet-trace`-bilirsiniz:

* Performansa duyarlı ortamlarda temel sistem durumu izleme için kullanın. `EventCounter` Örneğin, üretimde.
* Gerçek zamanlı olarak görüntülenmeleri gerekmesin diye izleri toplayın.

Örneğin, çalışma zamanı performans sayacı değerlerini toplamak için aşağıdaki komutu kullanın:

```console
dotnet-trace collect --process-id <PID> --providers System.Runtime:0:1:EventCounterIntervalSec=1
```

Önceki komut, çalışma zamanı sayaçlarına hafif sistem durumu izleme için saniyede bir rapor vermelerini söyler. Daha `EventCounterIntervalSec=1` yüksek bir değerle değiştirme (örneğin, 60) sayaç verilerinde daha az parçalılıkla daha küçük bir izlemenin toplanmasına olanak tanır.

Aşağıdaki komut, yükü ve izleme boyutunu bir öncekinden daha fazla azaltır:

```console
dotnet-trace collect --process-id <PID> --providers System.Runtime:0:1:EventCounterIntervalSec=1,Microsoft-Windows-DotNETRuntime:0:1,Microsoft-DotNETCore-SampleProfiler:0:1
```

Önceki komut çalışma zamanı olaylarını ve yönetilen yığın profiloluşturucuyu devre dışı kılabilir.

## <a name="net-providers"></a>.NET Sağlayıcıları

.NET Core çalışma süresi aşağıdaki .NET sağlayıcılarını destekler. .NET Core, hem hem `Event Tracing for Windows (ETW)` de `EventPipe` izleri etkinleştirmek için aynı anahtar kelimeleri kullanır.

| Sağlayıcı adı                            | Bilgi |
|------------------------------------------|-------------|
| `Microsoft-Windows-DotNETRuntime`        | [Çalışma Zamanı Sağlayıcısı](../../framework/performance/clr-etw-providers.md#the-runtime-provider)<br>[CLR Çalışma Zamanı Anahtar Kelimeleri](../../framework/performance/clr-etw-keywords-and-levels.md#runtime) |
| `Microsoft-Windows-DotNETRuntimeRundown` | [Rundown Sağlayıcı](../../framework/performance/clr-etw-providers.md#the-rundown-provider)<br>[CLR Özeti Anahtar Kelimeler](../../framework/performance/clr-etw-keywords-and-levels.md#rundown) |
| `Microsoft-DotNETCore-SampleProfiler`    | Örnek profil oluşturucuyu etkinleştirir. |
