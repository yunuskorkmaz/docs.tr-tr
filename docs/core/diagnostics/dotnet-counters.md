---
title: DotNet-sayaçlar-.NET Core
description: DotNet-Counter komut satırı aracını yüklemeyi ve kullanmayı öğrenin.
ms.date: 02/26/2020
ms.openlocfilehash: 88f701a60d0ee03dd0236ae54c57679943e14939
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2020
ms.locfileid: "78157888"
---
# <a name="dotnet-counters"></a>dotnet-counters

**Bu makale şu şekilde geçerlidir:** ✔️ .net Core 3,0 SDK ve sonraki sürümleri

## <a name="install-dotnet-counters"></a>DotNet-sayaçlar 'ı yükler

`dotnet-counters` [NuGet paketinin](https://www.nuget.org/packages/dotnet-counters)en son sürümünü yüklemek için [DotNet aracı install](../tools/dotnet-tool-install.md) komutunu kullanın:

```dotnetcli
dotnet tool install --global dotnet-counters
```

## <a name="synopsis"></a>Özeti

```console
dotnet-counters [-h|--help] [--version] <command>
```

## <a name="description"></a>Açıklama

`dotnet-counters`, geçici sistem durumu izleme ve ilk düzey performans araştırması için bir performans izleme aracıdır. <xref:System.Diagnostics.Tracing.EventCounter> API 'SI aracılığıyla yayınlanan performans sayacı değerlerini gözlemleyebilirsiniz. Örneğin, `PerfView` veya `dotnet-trace`kullanarak daha ciddi performans araştırmasına gerek olmadan önce kuşkulu bir sorun olup olmadığını görmek için, CPU kullanımı gibi şeyleri veya .NET Core uygulamanızda oluşturulan özel durumların oranını hızlıca izleyebilirsiniz.

## <a name="options"></a>Seçenekler

- **`--version`**

  DotNet-Counters yardımcı programının sürümünü görüntüler.

- **`-h|--help`**

  Komut satırı yardımını gösterir.

## <a name="commands"></a>Komutlar

| Komut                                             |
| --------------------------------------------------- |
| [DotNet-sayaçlar toplama](#dotnet-counters-collect) |
| [DotNet-sayaçlar listesi](#dotnet-counters-list)       |
| [DotNet-sayaçlar İzleyicisi](#dotnet-counters-monitor) |
| [DotNet-sayaçlar PS 'si](#dotnet-counters-ps) |

## <a name="dotnet-counters-collect"></a>DotNet-sayaçlar toplama

Seçili sayaç değerlerini düzenli olarak toplayın ve işleme sonrası için belirtilen dosya biçimine dışarı aktarın.

### <a name="synopsis"></a>Özeti

```console
dotnet-counters collect [-h|--help] [-p|--process-id] [--refreshInterval] [counter_list] [--format] [-o|--output]
```

### <a name="options"></a>Seçenekler

- **`-p|--process-id <PID>`**

  İzlenecek işlemin KIMLIĞI.

- **`--refresh-interval <SECONDS>`**

  Görüntülenecek sayaçların güncelleştirilmesi arasındaki gecikme süresi (saniye)

- **`counter_list <COUNTERS>`**

  Sayaçların boşlukla ayrılmış bir listesi. `provider_name[:counter_name]`, sayaçlar belirtilebilir. `provider_name` uygun olmayan bir `counter_name`olmadan kullanılırsa, tüm sayaçlar gösterilir. Sağlayıcı ve sayaç adlarını saptamak için [DotNet-Counters listesi](#dotnet-counters-list) komutunu kullanın.

- **`--format <csv|json>`**

  Aktarılacak biçim. Şu anda kullanılabilir: CSV, JSON.

- **`-o|--output <output>`**

  Çıktı dosyasının adı.

### <a name="examples"></a>Örnekler

- Tüm sayaçları 3 saniyelik yenileme aralığında toplayın ve çıkış olarak bir CSV oluşturun:

  ```console
  > dotnet-counters collect --process-id 1902 --refresh-interval 3 --format csv

  counter_list is unspecified. Monitoring all counters by default.
  Starting a counter session. Press Q to quit.
  ```

## <a name="dotnet-counters-list"></a>DotNet-sayaçlar listesi

Sağlayıcıya göre gruplandırılan sayaç adlarının ve açıklamalarının listesini görüntüler.

### <a name="synopsis"></a>Özeti

```console
dotnet-counters list [-h|--help]
```

### <a name="example"></a>Örnek

```console
> dotnet-counters list

    Showing well-known counters only. Specific processes may support additional counters.
    System.Runtime
        cpu-usage                    Amount of time the process has utilized the CPU (ms)
        working-set                  Amount of working set used by the process (MB)
        gc-heap-size                 Total heap size reported by the GC (MB)
        gen-0-gc-count               Number of Gen 0 GCs / sec
        gen-1-gc-count               Number of Gen 1 GCs / sec
        gen-2-gc-count               Number of Gen 2 GCs / sec
        exception-count              Number of Exceptions / sec
```

## <a name="dotnet-counters-monitor"></a>DotNet-sayaçlar İzleyicisi

Seçili sayaçların değerlerini düzenli aralıklarla yenilemeyi görüntüler.

### <a name="synopsis"></a>Özeti

```console
dotnet-counters monitor [-h|--help] [-p|--process-id] [--refreshInterval] [counter_list]
```

### <a name="options"></a>Seçenekler

- **`-p|--process-id <PID>`**

  İzlenecek işlemin KIMLIĞI.

- **`--refresh-interval <SECONDS>`**

  Görüntülenecek sayaçların güncelleştirilmesi arasındaki gecikme süresi (saniye)

- **`counter_list <COUNTERS>`**

  Sayaçların boşlukla ayrılmış bir listesi. `provider_name[:counter_name]`, sayaçlar belirtilebilir. `provider_name` uygun olmayan bir `counter_name`olmadan kullanılırsa, tüm sayaçlar gösterilir. Sağlayıcı ve sayaç adlarını saptamak için [DotNet-Counters listesi](#dotnet-counters-list) komutunu kullanın.

### <a name="examples"></a>Örnekler

- `System.Runtime` tüm sayaçları 3 saniyelik yenileme aralığında izleyin:

  ```console
  > dotnet-counters monitor --process-id 1902  --refresh-interval 3 System.Runtime

  Press p to pause, r to resume, q to quit.
    System.Runtime:
      CPU Usage (%)                                 24
      Working Set (MB)                            1982
      GC Heap Size (MB)                            811
      Gen 0 GC / second                             20
      Gen 1 GC / second                              4
      Gen 2 GC / second                              1
      Number of Exceptions / sec                     4
  ```

- `System.Runtime`yalnızca CPU kullanımı ve GC yığın boyutunu izle:

  ```console
  > dotnet-counters monitor --process-id 1902 System.Runtime[cpu-usage,gc-heap-size]

  Press p to pause, r to resume, q to quit.
    System.Runtime:
      CPU Usage (%)                                 24
      GC Heap Size (MB)                            811
  ```

- Kullanıcı tanımlı `EventSource``EventCounter` değerleri izleyin. Daha fazla bilgi için bkz. [öğretici: EventCounters kullanarak çok sık olaylar için performansı ölçme](https://github.com/dotnet/runtime/blob/master/src/libraries/System.Diagnostics.Tracing/documentation/EventCounterTutorial.md).

  ```console
  > dotnet-counters monitor --process-id 1902 Samples-EventCounterDemos-Minimal

  Press p to pause, r to resume, q to quit.
      request                                      100
  ```
  
## <a name="dotnet-counters-ps"></a>DotNet-sayaçlar PS 'si 

İzlenebilecek DotNet işlemlerinin bir listesini görüntüleyin.

### <a name="synopsis"></a>Özeti

```console
dotnet-counters ps [-h|--help]
```

### <a name="example"></a>Örnek

```console
> dotnet-counters ps
  
  15683 WebApi     /home/suwhang/repos/WebApi/WebApi
  16324 dotnet     /usr/local/share/dotnet/dotnet
```
