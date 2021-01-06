---
title: DotNet-sayaçlar Tanılama aracı-.NET CLı
description: Ad hoc sistem durumu izleme ve ilk düzey performans araştırması için DotNet-Counter CLı aracını yüklemeyi ve kullanmayı öğrenin.
ms.date: 11/17/2020
ms.openlocfilehash: 89695c77e7913d41f030890be7cc00947e42fa3a
ms.sourcegitcommit: e395fabeeea5c705d243d246fa64446839ac85b6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/03/2021
ms.locfileid: "97856061"
---
# <a name="investigate-performance-counters-dotnet-counters"></a>Performans sayaçlarını araştırın (DotNet-sayaçlar)

**Bu makale şu şekilde geçerlidir:** ✔️ .net Core 3,0 SDK ve sonraki sürümleri

## <a name="install"></a>Yükleme

İndirmek ve yüklemek için iki yol vardır `dotnet-counters` :

- **DotNet genel aracı:**

  NuGet paketinin en son sürümünü yüklemek için `dotnet-counters` [](https://www.nuget.org/packages/dotnet-counters) [DotNet aracı install](../tools/dotnet-tool-install.md) komutunu kullanın:

  ```dotnetcli
  dotnet tool install --global dotnet-counters
  ```

- **Doğrudan indirme:**

  Platformunuzla eşleşen araç yürütülebilirini indirin:

  | İşletim Sistemi  | Platform |
  | --- | -------- |
  | Windows | [x86](https://aka.ms/dotnet-counters/win-x86) \| [x64](https://aka.ms/dotnet-counters/win-x64) \| [ARM](https://aka.ms/dotnet-counters/win-arm) \| [ARM-x64](https://aka.ms/dotnet-counters/win-arm64) |
  | macOS   | [x64](https://aka.ms/dotnet-counters/osx-x64) |
  | Linux   | [x64](https://aka.ms/dotnet-counters/linux-x64) \| [ARM](https://aka.ms/dotnet-counters/linux-arm) \| [arm64](https://aka.ms/dotnet-counters/linux-arm64) \| [MUSL-x64](https://aka.ms/dotnet-counters/linux-musl-x64) \| [MUSL-arm64](https://aka.ms/dotnet-counters/linux-musl-arm64) |

## <a name="synopsis"></a>Özeti

```console
dotnet-counters [-h|--help] [--version] <command>
```

## <a name="description"></a>Açıklama

`dotnet-counters` , geçici sistem durumu izleme ve ilk düzey performans araştırması için bir performans izleme aracıdır. API aracılığıyla yayınlanan performans sayacı değerlerini gözlemleyebilirsiniz <xref:System.Diagnostics.Tracing.EventCounter> . Örneğin, veya kullanarak daha ciddi performans araştırmasına gerek olmadan önce kuşkulu bir şey olup olmadığını görmek için, CPU kullanımı veya .NET Core uygulamanızda oluşturulan özel durumların oranı gibi şeyleri hızlıca izleyebilirsiniz `PerfView` `dotnet-trace` .

## <a name="options"></a>Seçenekler

- **`--version`**

  DotNet-Counters yardımcı programının sürümünü görüntüler.

- **`-h|--help`**

  Komut satırı yardımını gösterir.

## <a name="commands"></a>Komutlar

| Komut                                             |
|-----------------------------------------------------|
| [DotNet-sayaçlar toplama](#dotnet-counters-collect) |
| [DotNet-sayaçlar listesi](#dotnet-counters-list)       |
| [DotNet-sayaçlar İzleyicisi](#dotnet-counters-monitor) |
| [DotNet-sayaçlar PS 'si](#dotnet-counters-ps)           |

## <a name="dotnet-counters-collect"></a>DotNet-sayaçlar toplama

Seçili sayaç değerlerini düzenli olarak toplayın ve işleme sonrası için belirtilen dosya biçimine dışarı aktarın.

### <a name="synopsis"></a>Özeti

```console
dotnet-counters collect [-h|--help] [-p|--process-id] [-n|--name] [--diagnostic-port] [--refresh-interval] [--counters <COUNTERS>] [--format] [-o|--output] [-- <command>]
```

### <a name="options"></a>Seçenekler

- **`-p|--process-id <PID>`**

  Sayaç verilerinin toplanacağı işlemin KIMLIĞI.

- **`-n|--name <name>`**

  Sayaç verilerinin toplanacağı işlemin adı.

- **`--diagnostic-port`**

  Oluşturulacak tanılama bağlantı noktasının adı. Uygulama başlangıcında sayaçları izlemeye başlamak için bu seçeneğin nasıl kullanılacağı hakkında bilgi için bkz. [Tanılama bağlantı noktası kullanma](#using-diagnostic-port) .

- **`--refresh-interval <SECONDS>`**

  Görüntülenecek sayaçların güncelleştirilmesi arasındaki gecikme süresi (saniye)

- **`--counters <COUNTERS>`**

  Sayaçların virgülle ayrılmış bir listesi. Sayaçlar belirtilebilir `provider_name[:counter_name]` . , `provider_name` Uygun sayaçların bir listesi olmadan kullanılırsa, sağlayıcıdan gelen tüm sayaçlar gösterilir. Sağlayıcı ve sayaç adlarını saptamak için [DotNet-Counters listesi](#dotnet-counters-list) komutunu kullanın.

- **`--format <csv|json>`**

  Aktarılacak biçim. Şu anda kullanılabilir: CSV, JSON.

- **`-o|--output <output>`**

  Çıktı dosyasının adı.

- **`-- <command>` (yalnızca .NET 5,0 veya üzeri sürümleri çalıştıran hedef uygulamalar için)**

  Koleksiyon yapılandırma parametrelerinden sonra, Kullanıcı, `--` en az bir 5,0 çalışma zamanına sahip bir .NET uygulamasını başlatmak için ardından bir komut ekleyebilir. `dotnet-counters` , belirtilen komutla bir işlem başlatır ve istenen ölçümleri toplar. Bu, genellikle uygulamanın başlangıç yolu için ölçümleri toplamak ve ana giriş noktasından önce veya kısa bir süre sonra ortaya çıkan sorunları tanılamak veya izlemek için kullanılabilir.

  > [!NOTE]
  > Bu seçeneğin kullanılması, araca geri iletişim kuran ilk .NET 5,0 işlemini izler, bu da komutunuz birden çok .NET uygulaması başlattığında yalnızca ilk uygulamayı toplayacaktır. Bu nedenle, bu seçeneği kendi içinde bulunan uygulamalarda veya seçeneğini kullanarak kullanmanız önerilir `dotnet exec <app.dll>` .

  > [!NOTE]
  > DotNet sayaçları aracılığıyla bir .NET yürütülebiliri başlatmak, giriş/çıkışının yeniden yönlendirilmesini sağlar ve stdin/stdout ile etkileşime giremeyeceksiniz. CTRL + C veya SIGTERM aracılığıyla araçtan çıkmak, hem aracı hem de alt işlemi güvenle sonlandıracaktır. Alt işlem, araçtan önce çıktığında, araç da sonlandırılır ve izlemenin güvenle görüntülenebilir olması gerekir. STDIN/STDOUT kullanmanız gerekiyorsa `--diagnostic-port` seçeneğini kullanabilirsiniz. Daha fazla bilgi için bkz. [Tanılama bağlantı noktası kullanma](#using-diagnostic-port) .

### <a name="examples"></a>Örnekler

- Tüm sayaçları 3 saniyelik yenileme aralığında toplayın ve çıkış olarak bir CSV oluşturun:

  ```console
  > dotnet-counters collect --process-id 1902 --refresh-interval 3 --format csv

  counter_list is unspecified. Monitoring all counters by default.
  Starting a counter session. Press Q to quit.
  ```

- `dotnet mvc.dll`Bir alt işlem olarak başlatın ve çalışma zamanı sayaçlarını toplamaya başlayın ve başlatma işleminden ASP.NET Core barındırma sayaçlarını başlatın ve bunu BIR JSON çıkışı olarak kaydedin:

  ```console
  > dotnet-counters collect --format json --counters System.Runtime,Microsoft.AspNetCore.Hosting -- dotnet mvc.dll
  Starting a counter session. Press Q to quit.
  File saved to counter.json
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
    cpu-usage                                    Amount of time the process has utilized the CPU (ms)
    working-set                                  Amount of working set used by the process (MB)
    gc-heap-size                                 Total heap size reported by the GC (MB)
    gen-0-gc-count                               Number of Gen 0 GCs per interval
    gen-1-gc-count                               Number of Gen 1 GCs per interval
    gen-2-gc-count                               Number of Gen 2 GCs per interval
    time-in-gc                                   % time in GC since the last GC
    gen-0-size                                   Gen 0 Heap Size
    gen-1-size                                   Gen 1 Heap Size
    gen-2-size                                   Gen 2 Heap Size
    loh-size                                     LOH Heap Size
    alloc-rate                                   Allocation Rate
    assembly-count                               Number of Assemblies Loaded
    exception-count                              Number of Exceptions per interval
    threadpool-thread-count                      Number of ThreadPool Threads
    monitor-lock-contention-count                Monitor Lock Contention Count
    threadpool-queue-length                      ThreadPool Work Items Queue Length
    threadpool-completed-items-count             ThreadPool Completed Work Items Count
    active-timer-count                           Active Timers Count

Microsoft.AspNetCore.Hosting
    requests-per-second                  Request rate
    total-requests                       Total number of requests
    current-requests                     Current number of requests
    failed-requests                      Failed number of requests
```

> [!NOTE]
> `Microsoft.AspNetCore.Hosting`Sayaçlar, bu sayaçları destekleyen bir işlem olduğunda (örneğin, konak makinede bir ASP.NET Core uygulama çalışırken) görüntülenir.

## <a name="dotnet-counters-monitor"></a>DotNet-sayaçlar İzleyicisi

Seçili sayaçların değerlerini düzenli aralıklarla yenilemeyi görüntüler.

### <a name="synopsis"></a>Özeti

```console
dotnet-counters monitor [-h|--help] [-p|--process-id] [-n|--name] [--diagnostic-port] [--refresh-interval] [--counters] [-- <command>]
```

### <a name="options"></a>Seçenekler

- **`-p|--process-id <PID>`**

  İzlenecek işlemin KIMLIĞI.

- **`-n|--name <name>`**

  İzlenecek işlemin adı.

- **`--diagnostic-port`**

  Oluşturulacak tanılama bağlantı noktasının adı. Uygulama başlangıcında sayaçları izlemeye başlamak için bu seçeneğin nasıl kullanılacağı hakkında bilgi için bkz. [Tanılama bağlantı noktası kullanma](#using-diagnostic-port) .

- **`--refresh-interval <SECONDS>`**

  Görüntülenecek sayaçların güncelleştirilmesi arasındaki gecikme süresi (saniye)

- **`--counters <COUNTERS>`**

  Sayaçların virgülle ayrılmış bir listesi. Sayaçlar belirtilebilir `provider_name[:counter_name]` . , `provider_name` Uygun sayaçların bir listesi olmadan kullanılırsa, sağlayıcıdan gelen tüm sayaçlar gösterilir. Sağlayıcı ve sayaç adlarını saptamak için [DotNet-Counters listesi](#dotnet-counters-list) komutunu kullanın.

 **`-- <command>` (yalnızca .NET 5,0 veya üzeri sürümleri çalıştıran hedef uygulamalar için)**

  Koleksiyon yapılandırma parametrelerinden sonra, Kullanıcı, `--` en az bir 5,0 çalışma zamanına sahip bir .NET uygulamasını başlatmak için ardından bir komut ekleyebilir. `dotnet-counters` , belirtilen komutla bir işlem başlatır ve istenen ölçümleri izler. Bu, genellikle uygulamanın başlangıç yolu için ölçümleri toplamak ve ana giriş noktasından önce veya kısa bir süre sonra ortaya çıkan sorunları tanılamak veya izlemek için kullanılabilir.

  > [!NOTE]
  > Bu seçeneğin kullanılması, araca geri iletişim kuran ilk .NET 5,0 işlemini izler, bu da komutunuz birden çok .NET uygulaması başlattığında yalnızca ilk uygulamayı toplayacaktır. Bu nedenle, bu seçeneği kendi içinde bulunan uygulamalarda veya seçeneğini kullanarak kullanmanız önerilir `dotnet exec <app.dll>` .

  > [!NOTE]
  > DotNet sayaçları aracılığıyla bir .NET yürütülebiliri başlatmak, giriş/çıkışının yeniden yönlendirilmesini sağlar ve stdin/stdout ile etkileşime giremeyeceksiniz. CTRL + C veya SIGTERM aracılığıyla araçtan çıkmak, hem aracı hem de alt işlemi güvenle sonlandıracaktır. Alt işlem, araçtan önce çıktığında, araç da sonlandırılır ve izlemenin güvenle görüntülenebilir olması gerekir. STDIN/STDOUT kullanmanız gerekiyorsa `--diagnostic-port` seçeneğini kullanabilirsiniz. Daha fazla bilgi için bkz. [Tanılama bağlantı noktası kullanma](#using-diagnostic-port) .

### <a name="examples"></a>Örnekler

- Tüm sayaçları `System.Runtime` 3 saniyelik yenileme aralığından izleyin:

  ```console
  > dotnet-counters monitor --process-id 1902  --refresh-interval 3 --counters System.Runtime
  Press p to pause, r to resume, q to quit.
      Status: Running

  [System.Runtime]
      % Time in GC since last GC (%)                                 0
      Allocation Rate (B / 1 sec)                                5,376
      CPU Usage (%)                                                  0
      Exception Count (Count / 1 sec)                                0
      GC Fragmentation (%)                                          48.467
      GC Heap Size (MB)                                              0
      Gen 0 GC Count (Count / 1 sec)                                 1
      Gen 0 Size (B)                                                24
      Gen 1 GC Count (Count / 1 sec)                                 1
      Gen 1 Size (B)                                                24
      Gen 2 GC Count (Count / 1 sec)                                 1
      Gen 2 Size (B)                                           272,000
      IL Bytes Jitted (B)                                       19,449
      LOH Size (B)                                              19,640
      Monitor Lock Contention Count (Count / 1 sec)                  0
      Number of Active Timers                                        0
      Number of Assemblies Loaded                                    7
      Number of Methods Jitted                                     166
      POH (Pinned Object Heap) Size (B)                             24
      ThreadPool Completed Work Item Count (Count / 1 sec)           0
      ThreadPool Queue Length                                        0
      ThreadPool Thread Count                                        2
      Working Set (MB)                                              19
  ```

- Yalnızca CPU kullanımı ve GC yığın boyutunu izle `System.Runtime` :

  ```console
  > dotnet-counters monitor --process-id 1902 --counters System.Runtime[cpu-usage,gc-heap-size]

  Press p to pause, r to resume, q to quit.
    Status: Running

  [System.Runtime]
      CPU Usage (%)                                 24
      GC Heap Size (MB)                            811
  ```

- `EventCounter`Kullanıcı tanımlı değerleri izleme `EventSource` . Daha fazla bilgi için bkz. [öğretici: .NET Core 'Da EventCounters kullanarak performansı ölçme](event-counter-perf.md).

  ```console
  > dotnet-counters monitor --process-id 1902 --counters Samples-EventCounterDemos-Minimal

  Press p to pause, r to resume, q to quit.
      request                                      100
  ```

- ' De kullanılabilen tüm iyi bilinen sayaçları görüntüleyin `dotnet-counters` :

  ```console
  > dotnet-counters list

  Showing well-known counters for .NET (Core) version 3.1 only. Specific processes may support additional counters.
  System.Runtime              
      cpu-usage                          The percent of process' CPU usage relative to all of the system CPU resources [0-100]
      working-set                        Amount of working set used by the process (MB)
      gc-heap-size                       Total heap size reported by the GC (MB)
      gen-0-gc-count                     Number of Gen 0 GCs between update intervals
      gen-1-gc-count                     Number of Gen 1 GCs between update intervals
      gen-2-gc-count                     Number of Gen 2 GCs between update intervals
      time-in-gc                         % time in GC since the last GC
      gen-0-size                         Gen 0 Heap Size
      gen-1-size                         Gen 1 Heap Size
      gen-2-size                         Gen 2 Heap Size
      loh-size                           LOH Size
      alloc-rate                         Number of bytes allocated in the managed heap between update intervals
      assembly-count                     Number of Assemblies Loaded
      exception-count                    Number of Exceptions / sec
      threadpool-thread-count            Number of ThreadPool Threads
      monitor-lock-contention-count      Number of times there were contention when trying to take the monitor lock between update intervals
      threadpool-queue-length            ThreadPool Work Items Queue Length
      threadpool-completed-items-count   ThreadPool Completed Work Items Count
      active-timer-count                 Number of timers that are currently active

  Microsoft.AspNetCore.Hosting
      requests-per-second                Number of requests between update intervals
      total-requests                     Total number of requests
      current-requests                   Current number of requests
      failed-requests                    Failed number of requests
  ```

- .NET 5 uygulamaları için ' de kullanılabilen tüm iyi bilinen sayaçları görüntüleyin `dotnet-counters` :

  ```console
  > dotnet-counters list --runtime-version 5.0

  Showing well-known counters for .NET (Core) version 5.0 only. Specific processes may support additional counters.
  System.Runtime                     
      cpu-usage                          The percent of process' CPU usage relative to all of the system CPU resources [0-100]
      working-set                        Amount of working set used by the process (MB)
      gc-heap-size                       Total heap size reported by the GC (MB)
      gen-0-gc-count                     Number of Gen 0 GCs between update intervals
      gen-1-gc-count                     Number of Gen 1 GCs between update intervals
      gen-2-gc-count                     Number of Gen 2 GCs between update intervals
      time-in-gc                         % time in GC since the last GC
      gen-0-size                         Gen 0 Heap Size
      gen-1-size                         Gen 1 Heap Size
      gen-2-size                         Gen 2 Heap Size
      loh-size                           LOH Size
      poh-size                           POH (Pinned Object Heap) Size
      alloc-rate                         Number of bytes allocated in the managed heap between update intervals
      gc-fragmentation                   GC Heap Fragmentation
      assembly-count                     Number of Assemblies Loaded
      exception-count                    Number of Exceptions / sec
      threadpool-thread-count            Number of ThreadPool Threads
      monitor-lock-contention-count      Number of times there were contention when trying to take the monitor lock between update intervals
      threadpool-queue-length            ThreadPool Work Items Queue Length
      threadpool-completed-items-count   ThreadPool Completed Work Items Count
      active-timer-count                 Number of timers that are currently active
      il-bytes-jitted                    Total IL bytes jitted
      methods-jitted-count               Number of methods jitted

  Microsoft.AspNetCore.Hosting       
      requests-per-second   Number of requests between update intervals
      total-requests        Total number of requests
      current-requests      Current number of requests
      failed-requests       Failed number of requests

  Microsoft-AspNetCore-Server-Kestrel
      connections-per-second      Number of connections between update intervals
      total-connections           Total Connections
      tls-handshakes-per-second   Number of TLS Handshakes made between update intervals
      total-tls-handshakes        Total number of TLS handshakes made
      current-tls-handshakes      Number of currently active TLS handshakes
      failed-tls-handshakes       Total number of failed TLS handshakes
      current-connections         Number of current connections
      connection-queue-length     Length of Kestrel Connection Queue
      request-queue-length        Length total HTTP request queue

  System.Net.Http                    
      requests-started        Total Requests Started
      requests-started-rate   Number of Requests Started between update intervals
      requests-aborted        Total Requests Aborted
      requests-aborted-rate   Number of Requests Aborted between update intervals
      current-requests        Current Requests
  ```

- `my-aspnet-server.exe`Başlangıçtan yüklenen derlemelerin sayısını başlatın ve izleyin (yalnızca .net 5,0 veya üzeri):

  > [!IMPORTANT]
  > Bu, yalnızca .NET 5,0 veya sonraki sürümleri çalıştıran uygulamalar için geçerlidir.

  ```console
  > dotnet-counters monitor --counters System.Runtime[assembly-count] -- my-aspnet-server.exe

  Press p to pause, r to resume, q to quit.
    Status: Running

  [System.Runtime]
      Number of Assemblies Loaded                   24
  ```
  
- `my-aspnet-server.exe` `arg1` Ve `arg2` komut satırı bağımsız değişkenleri ile başlatın ve çalışma kümesi ve GC yığın boyutunu başlangıçtan (yalnızca .NET 5,0 veya üzeri) izleyin:

  > [!IMPORTANT]
  > Bu, yalnızca .NET 5,0 veya sonraki sürümleri çalıştıran uygulamalar için geçerlidir.

  ```console
  > dotnet-counters monitor --counters System.Runtime[working-set,gc-heap-size] -- my-aspnet-server.exe arg1 arg2
  ```

  ```console
  Press p to pause, r to resume, q to quit.
    Status: Running

  [System.Runtime]
      GC Heap Size (MB)                                 39
      Working Set (MB)                                  59
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
  
  15683 WebApi     /home/user/repos/WebApi/WebApi
  16324 dotnet     /usr/local/share/dotnet/dotnet
```

## <a name="using-diagnostic-port"></a>Tanılama bağlantı noktasını kullanma

  > [!IMPORTANT]
  > Bu, yalnızca .NET 5,0 veya sonraki sürümleri çalıştıran uygulamalar için geçerlidir.

Tanılama bağlantı noktası, .NET 5 ' te eklenen ve uygulama başlangıcında sayaç izlemeye veya toplamaya başlayabilmeniz için yeni bir çalışma zamanı özelliğidir. Bunu kullanarak yapmak için `dotnet-counters` `dotnet-counters <collect|monitor> -- <command>` Yukarıdaki örneklerde açıklandığı gibi kullanabilirsiniz veya `--diagnostic-port` seçeneğini kullanabilirsiniz.

`dotnet-counters <collect|monitor> -- <command>`Uygulamayı bir alt işlem olarak başlatmak için kullanmak, bunu başlangıçtan hızlı bir şekilde izlemenin en kolay yoludur.

Bununla birlikte, izlenen uygulamanın ömrü boyunca daha ayrıntılı bir denetim elde etmek istediğinizde (örneğin, uygulamayı yalnızca ilk 10 dakika boyunca izleyin ve yürütülmeye devam edin) veya CLı kullanarak uygulamayla etkileşime ihtiyacınız varsa, kullanma `--diagnostic-port` seçeneği, hem izlenen hem de hedef uygulamayı denetlemenize olanak tanır `dotnet-counters` .

1. Aşağıdaki komut, DotNet-Counters adlı bir tanılama yuvası oluşturur `myport.sock` ve bir bağlantı bekler.

    > ```dotnet-cli
    > dotnet-counters collect --diagnostic-port myport.sock
    > ```

    Çıkış:

    > ```bash
    > Waiting for connection on myport.sock
    > Start an application with the following environment variable: DOTNET_DiagnosticPorts=/home/user/myport.sock
    > ```

2. Ayrı bir konsolda, hedef uygulamayı `DOTNET_DiagnosticPorts` Çıkış içindeki değere ayarlanmış ortam değişkeni ile başlatın `dotnet-counters` .

    > ```bash
    > export DOTNET_DiagnosticPorts=/home/user/myport.sock
    > ./my-dotnet-app arg1 arg2
    > ```

    Bu, daha sonra `dotnet-counters` sayaçların toplanmasına başlaması gerekir `my-dotnet-app` :

    > ```bash
    > Waiting for connection on myport.sock
    > Start an application with the following environment variable: DOTNET_DiagnosticPorts=myport.sock
    > Starting a counter session. Press Q to quit.
    > ```

    > [!IMPORTANT]
    > `dotnet run`DotNet CLI, uygulamanız olmayan çok sayıda alt işlem oluşturduğundan ve uygulamanızın `dotnet-counters` çalışma zamanında askıya alınması için uygulamadan önce bağlanabildikleri için uygulamanızın ile başlatılması sorunlu olabilir. Uygulamanın otomatik olarak kapsanan bir sürümünü kullanmanız veya `dotnet exec` uygulamayı başlatmak için kullanmanız önerilir.
