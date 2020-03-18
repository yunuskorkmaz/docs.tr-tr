---
title: dotnet sayaçları - .NET Core
description: Dotnet-counter komut satırı aracını nasıl yükleyip kullanacağınızı öğrenin.
ms.date: 02/26/2020
ms.openlocfilehash: dc95297478784ca06fe442a939f8489a40b29da7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79147184"
---
# <a name="dotnet-counters"></a>dotnet-counters

**Bu makale şu şekilde dir:** ✔️ .NET Core 3.0 SDK ve sonraki sürümler

## <a name="install-dotnet-counters"></a>dotnet sayaçları yükleme

`dotnet-counters` [NuGet paketinin](https://www.nuget.org/packages/dotnet-counters)en son sürüm sürümünü yüklemek [için, dotnet aracı yükleme](../tools/dotnet-tool-install.md) komutunu kullanın:

```dotnetcli
dotnet tool install --global dotnet-counters
```

## <a name="synopsis"></a>Özet

```console
dotnet-counters [-h|--help] [--version] <command>
```

## <a name="description"></a>Açıklama

`dotnet-counters`özel sağlık izleme ve birinci düzey performans araştırması için bir performans izleme aracıdır. <xref:System.Diagnostics.Tracing.EventCounter> API üzerinden yayınlanan performans sayacı değerlerini gözlemleyebilir. Örneğin, CPU kullanımı veya .NET Core uygulamanızda atılan özel durumlar gibi şeyleri hızlı bir şekilde izleyerek daha ciddi bir performans `PerfView` `dotnet-trace`araştırması yapmadan önce şüpheli bir şey olup olmadığını görebilirsiniz.

## <a name="options"></a>Seçenekler

- **`--version`**

  Dotnet sayaçları yardımcı programı sürümünü görüntüler.

- **`-h|--help`**

  Komut satırı yardımlarını gösterir.

## <a name="commands"></a>Komutlar

| Komut                                             |
| --------------------------------------------------- |
| [dotnet sayaçları toplamak](#dotnet-counters-collect) |
| [dotnet sayaçları listesi](#dotnet-counters-list)       |
| [dotnet sayaçları monitör](#dotnet-counters-monitor) |
| [dotnet sayaçları ps](#dotnet-counters-ps) |

## <a name="dotnet-counters-collect"></a>dotnet sayaçları toplamak

Seçili sayaç değerlerini düzenli aralıklarla toplayın ve işlem sonrası için belirli bir dosya biçimine aktarın.

### <a name="synopsis"></a>Özet

```console
dotnet-counters collect [-h|--help] [-p|--process-id] [--refreshInterval] [counter_list] [--format] [-o|--output]
```

### <a name="options"></a>Seçenekler

- **`-p|--process-id <PID>`**

  İzlenecek işlemin kimliği.

- **`--refresh-interval <SECONDS>`**

  Görüntülenen sayaçları güncelleştirmek arasında geciktirecek saniye sayısı

- **`counter_list <COUNTERS>`**

  Sayaçların ayrılmış bir boşluk listesi. Sayaçlar belirtilebilir. `provider_name[:counter_name]` Bir `provider_name` eleme olmadan `counter_name`kullanılırsa, o zaman tüm sayaçları gösterilir. Sağlayıcı ve sayaç adlarını bulmak için [dotnet sayaçları liste](#dotnet-counters-list) komutunu kullanın.

- **`--format <csv|json>`**

  TThe biçimi dışa aktarılacak. Şu anda kullanılabilir: csv, json.

- **`-o|--output <output>`**

  Çıktı dosyasının adı.

### <a name="examples"></a>Örnekler

- Tüm sayaçları 3 saniyelik bir yenileme aralığında toplayın ve çıktı olarak bir csv oluşturun:

  ```console
  > dotnet-counters collect --process-id 1902 --refresh-interval 3 --format csv

  counter_list is unspecified. Monitoring all counters by default.
  Starting a counter session. Press Q to quit.
  ```

## <a name="dotnet-counters-list"></a>dotnet sayaçları listesi

Sağlayıcıya göre gruplanmış sayaç adlarının ve açıklamaların listesini görüntüler.

### <a name="synopsis"></a>Özet

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

## <a name="dotnet-counters-monitor"></a>dotnet sayaçları monitör

Seçili sayaçların periyodik olarak yenilenme değerlerini görüntüler.

### <a name="synopsis"></a>Özet

```console
dotnet-counters monitor [-h|--help] [-p|--process-id] [--refreshInterval] [counter_list]
```

### <a name="options"></a>Seçenekler

- **`-p|--process-id <PID>`**

  İzlenecek işlemin kimliği.

- **`--refresh-interval <SECONDS>`**

  Görüntülenen sayaçları güncelleştirmek arasında geciktirecek saniye sayısı

- **`counter_list <COUNTERS>`**

  Sayaçların ayrılmış bir boşluk listesi. Sayaçlar belirtilebilir. `provider_name[:counter_name]` Bir `provider_name` eleme olmadan `counter_name`kullanılırsa, o zaman tüm sayaçları gösterilir. Sağlayıcı ve sayaç adlarını bulmak için [dotnet sayaçları liste](#dotnet-counters-list) komutunu kullanın.

### <a name="examples"></a>Örnekler

- Tüm sayaçları `System.Runtime` 3 saniyelik bir yenileme aralığından izleyin:

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

- Monitör sadece CPU kullanımı ve GC yığın boyutu: `System.Runtime`

  ```console
  > dotnet-counters monitor --process-id 1902 System.Runtime[cpu-usage,gc-heap-size]

  Press p to pause, r to resume, q to quit.
    System.Runtime:
      CPU Usage (%)                                 24
      GC Heap Size (MB)                            811
  ```

- `EventCounter` Değerleri kullanıcı tanımlı `EventSource`olarak izleyin. Daha fazla bilgi için [Bkz. Öğretici: EventCounters'ı kullanarak çok sık karşılaşılan olaylar için performans nasıl ölçülür?](https://github.com/dotnet/runtime/blob/master/src/libraries/System.Diagnostics.Tracing/documentation/EventCounterTutorial.md)

  ```console
  > dotnet-counters monitor --process-id 1902 Samples-EventCounterDemos-Minimal

  Press p to pause, r to resume, q to quit.
      request                                      100
  ```
  
## <a name="dotnet-counters-ps"></a>dotnet sayaçları ps

İzlenebilen dotnet işlemlerinin listesini görüntüleyin.

### <a name="synopsis"></a>Özet

```console
dotnet-counters ps [-h|--help]
```

### <a name="example"></a>Örnek

```console
> dotnet-counters ps
  
  15683 WebApi     /home/suwhang/repos/WebApi/WebApi
  16324 dotnet     /usr/local/share/dotnet/dotnet
```
