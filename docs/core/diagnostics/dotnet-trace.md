---
title: DotNet-Trace Tanılama aracı-.NET CLı
description: .NET EventPipe kullanarak, yerel profil oluşturucu olmadan çalışan bir işlemin .NET izlemelerini toplamak için DotNet-Trace CLı aracını yüklemeyi ve kullanmayı öğrenin.
ms.date: 11/17/2020
ms.openlocfilehash: a3b5748cb2a6c2060971fbad0d81ade00dc83087
ms.sourcegitcommit: 35ca2255c6c86968eaef9e3a251c9739ce8e4288
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2020
ms.locfileid: "97753682"
---
# <a name="dotnet-trace-performance-analysis-utility"></a>DotNet-izleme performansı Analizi yardımcı programı

**Bu makale şu şekilde geçerlidir:** ✔️ .net Core 3,0 SDK ve sonraki sürümleri

## <a name="install"></a>Yükleme

İndirmek ve yüklemek için iki yol vardır `dotnet-trace` :

- **DotNet genel aracı:**

  NuGet paketinin en son sürümünü yüklemek için `dotnet-trace` [](https://www.nuget.org/packages/dotnet-trace) [DotNet aracı install](../tools/dotnet-tool-install.md) komutunu kullanın:

  ```dotnetcli
  dotnet tool install --global dotnet-trace
  ```

- **Doğrudan indirme:**

  Platformunuzla eşleşen araç yürütülebilirini indirin:

  | İşletim Sistemi  | Platform |
  | --- | -------- |
  | Windows | [x86](https://aka.ms/dotnet-trace/win-x86) \| [x64](https://aka.ms/dotnet-trace/win-x64) \| [ARM](https://aka.ms/dotnet-trace/win-arm) \| [ARM-x64](https://aka.ms/dotnet-trace/win-arm64) |
  | macOS   | [x64](https://aka.ms/dotnet-trace/osx-x64) |
  | Linux   | [x64](https://aka.ms/dotnet-trace/linux-x64) \| [ARM](https://aka.ms/dotnet-trace/linux-arm) \| [arm64](https://aka.ms/dotnet-trace/linux-arm64) \| [MUSL-x64](https://aka.ms/dotnet-trace/linux-musl-x64) \| [MUSL-arm64](https://aka.ms/dotnet-trace/linux-musl-arm64) |

## <a name="synopsis"></a>Özeti

```console
dotnet-trace [-h, --help] [--version] <command>
```

## <a name="description"></a>Açıklama

`dotnet-trace`Araç:

* , Platformlar arası bir .NET Core aracıdır.
* Yerel bir profil oluşturucu olmadan çalışan bir işlemin .NET Core izlemelerinin toplanmasını mümkün bir şekilde sunar.
* , [`EventPipe`](./eventpipe.md) .NET Core çalışma zamanı üzerine kurulmuştur.
* Windows, Linux veya macOS 'ta aynı deneyimi sunar.

## <a name="options"></a>Seçenekler

- **`-h|--help`**

  Komut satırı yardımını gösterir.

- **`--version`**

  DotNet-Trace yardımcı programının sürümünü görüntüler.

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
dotnet-trace collect [--buffersize <size>] [--clreventlevel <clreventlevel>] [--clrevents <clrevents>]
    [--format <Chromium|NetTrace|Speedscope>] [-h|--help]
    [-n, --name <name>] [--diagnostic-port] [-o|--output <trace-file-path>] [-p|--process-id <pid>]
    [--profile <profile-name>] [--providers <list-of-comma-separated-providers>]
    [-- <command>] (for target applications running .NET 5.0 or later)
```

### <a name="options"></a>Seçenekler

- **`--buffersize <size>`**

  Bellek içi dairesel arabelleğin boyutunu megabayt cinsinden ayarlar. Varsayılan 256 MB.

- **`--clreventlevel <clreventlevel>`**

  Oluşturulacak CLR olaylarının ayrıntı düzeyi.

- **`--clrevents <clrevents>`**

  Görüntülenecek CLR çalışma zamanı olaylarının listesi.

- **`--format {Chromium|NetTrace|Speedscope}`**

  İzleme dosyası dönüştürmesi için çıkış biçimini ayarlar. Varsayılan değer: `NetTrace`.

- **`-n, --name <name>`**

  İzlemenin toplanacağı işlemin adı.

- **`--diagnostic-port <path-to-port>`**

  Oluşturulacak tanılama bağlantı noktasının adı. Uygulamanın başlangıcında bir izleme toplamak için bu seçeneği nasıl kullanacağınızı öğrenmek için bkz. [Uygulama başlangıcında bir izleme toplamak için tanılama bağlantı noktası kullanma](#use-diagnostic-port-to-collect-a-trace-from-app-startup) .

- **`-o|--output <trace-file-path>`**

  Toplanan izleme verileri için çıkış yolu. Belirtilmemişse, varsayılan olarak olur `trace.nettrace` .

- **`-p|--process-id <PID>`**

  İzlemeyi toplanacak işlem KIMLIĞI.

- **`--profile <profile-name>`**

  Yaygın izleme senaryolarına izin veren önceden tanımlanmış adlandırılmış bir dizi sağlayıcı yapılandırması succinctly. Aşağıdaki profiller mevcuttur:

 | Profil | Açıklama |
 |---------|-------------|
 |`cpu-sampling`|CPU kullanımını ve genel .NET çalışma zamanı bilgilerini izlemek için faydalıdır. Profil veya sağlayıcı belirtilmemişse bu varsayılan seçenektir.|
 |`gc-verbose`|GC koleksiyonlarını izler ve nesne ayırmalarını örnekler.|
 |`gc-collect`|GC koleksiyonlarını yalnızca çok düşük ek yüklerle izler.|

- **`--providers <list-of-comma-separated-providers>`**

  Etkinleştirilecek sağlayıcıların virgülle ayrılmış listesi `EventPipe` . Bu sağlayıcılar tarafından kapsanan tüm sağlayıcıları tamamlar `--profile <profile-name>` . Belirli bir sağlayıcı için herhangi bir tutarsızlık varsa, bu yapılandırma profilden örtük yapılandırmadan önceliklidir.

  Bu sağlayıcı listesi şu biçimdedir:

  - `Provider[,Provider]`
  - `Provider` Şu biçimdedir: `KnownProviderName[:Flags[:Level][:KeyValueArgs]]` .
  - `KeyValueArgs` Şu biçimdedir: `[key1=value1][;key2=value2]` .

- **`-- <command>` (yalnızca .NET 5,0 çalıştıran hedef uygulamalar için)**

  Koleksiyon yapılandırma parametrelerinden sonra, Kullanıcı, `--` en az bir 5,0 çalışma zamanına sahip bir .NET uygulamasını başlatmak için ardından bir komut ekleyebilir. Bu, işlemin başında gerçekleşen, başlangıç performansı sorunu veya derleme yükleyicisi ve bağlayıcı hataları gibi sorunları tanılarken yararlı olabilir.

  > [!NOTE]
  > Bu seçeneğin kullanılması, araca geri iletişim kuran ilk .NET 5,0 işlemini izler, bu da komutunuz birden çok .NET uygulaması başlattığında yalnızca ilk uygulamayı toplayacaktır. Bu nedenle, bu seçeneği kendi içinde bulunan uygulamalarda veya seçeneğini kullanarak kullanmanız önerilir `dotnet exec <app.dll>` .

> [!NOTE]
> İzlemenin durdurulması, büyük uygulamalar için uzun zaman alabilir (en fazla dakika). Çalışma zamanının, izlemede yakalanan tüm yönetilen kodlar için tür önbelleğinin üzerine gönderilmesi gerekir.

## <a name="dotnet-trace-convert"></a>DotNet-Trace Dönüştür

`nettrace`Diğer izleme çözümleme araçlarıyla birlikte kullanmak üzere izlemeleri alternatif biçimlere dönüştürür.

### <a name="synopsis"></a>Özeti

```console
dotnet-trace convert [<input-filename>] [--format <Chromium|NetTrace|Speedscope>] [-h|--help] [-o|--output <output-filename>]
```

### <a name="arguments"></a>Arguments

- **`<input-filename>`**

  Dönüştürülecek giriş izleme dosyası. *Trace. NetTrace* için varsayılanlar.

### <a name="options"></a>Seçenekler

- **`--format <Chromium|NetTrace|Speedscope>`**

  İzleme dosyası dönüştürmesi için çıkış biçimini ayarlar.

- **`-o|--output <output-filename>`**

  Çıkış dosya adı. Hedef biçimin uzantısı eklenecek.

> [!NOTE]
> `nettrace`Dosyaları `chromium` veya dosyaları dönüştürme `speedscope` işlemi geri alınamaz. `speedscope` dosyalar `chromium` , dosyaları yeniden oluşturmak için gereken tüm bilgileri içermez `nettrace` . Ancak, `convert` komut özgün `nettrace` dosyayı korur, bu nedenle daha sonra açmayı planlıyorsanız bu dosyayı silmeyin.

## <a name="dotnet-trace-ps"></a>DotNet-izleme PS 'si

 İzlemelerin toplanabilecek DotNet süreçlerini listeler.

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

- Anahtara basarak toplamayı durdurun `<Enter>` . `dotnet-trace` olayları *izleme. NetTrace* dosyasına kaydetme işlemi tamamlanır.

## <a name="launch-a-child-application-and-collect-a-trace-from-its-startup-using-dotnet-trace"></a>Bir alt uygulama başlatın ve DotNet-Trace kullanarak başlangıçtan bir izleme toplayın

> [!IMPORTANT]
> Bu, yalnızca .NET 5,0 veya sonraki sürümleri çalıştıran uygulamalar için geçerlidir.

Bazen bir işlemin başlangıcında bir izleme toplamak yararlı olabilir. .NET 5,0 veya üzeri sürümlerini çalıştıran uygulamalar için bu, DotNet-Trace kullanılarak yapılabilir.

Bu, `hello.exe` `arg1` ve `arg2` komut satırı bağımsız değişkenleriyle başlatılır ve çalışma zamanı başlangıcında bir izleme toplar:

```console
dotnet-trace collect -- hello.exe arg1 arg2
```

Yukarıdaki komut aşağıdakine benzer bir çıktı oluşturur:

```console
No profile or providers specified, defaulting to trace profile 'cpu-sampling'

Provider Name                           Keywords            Level               Enabled By
Microsoft-DotNETCore-SampleProfiler     0x0000F00000000000  Informational(4)    --profile
Microsoft-Windows-DotNETRuntime         0x00000014C14FCCBD  Informational(4)    --profile

Process        : E:\temp\gcperfsim\bin\Debug\net5.0\gcperfsim.exe
Output File    : E:\temp\gcperfsim\trace.nettrace


[00:00:00:05]   Recording trace 122.244  (KB)
Press <Enter> or <Ctrl+C> to exit...
```

Veya tuşuna basarak izlemenin toplanmasını durdurabilirsiniz `<Enter>` `<Ctrl + C>` . Bunun için de çıkış yapılır `hello.exe` .

> [!NOTE]
> `hello.exe`DotNet-Trace aracılığıyla başlatmak, giriş/çıkışının yeniden yönlendirilmesini sağlar ve stdin/stdout ile etkileşime giremeyeceksiniz.
> CTRL + C veya SIGTERM aracılığıyla araçtan çıkmak, hem aracı hem de alt işlemi güvenle sonlandıracaktır.
> Alt işlem, araçtan önce çıktığında, araç da sonlandırılır ve izlemenin güvenle görüntülenebilir olması gerekir.

## <a name="use-diagnostic-port-to-collect-a-trace-from-app-startup"></a>Uygulama başlangıcında bir izleme toplamak için tanılama bağlantı noktasını kullan

  > [!IMPORTANT]
  > Bu, yalnızca .NET 5,0 veya sonraki sürümleri çalıştıran uygulamalar için geçerlidir.

Tanılama bağlantı noktası, .NET 5 ' te eklenen ve uygulama başlangıcında izlemeye başlayabilmeniz için yeni bir çalışma zamanı özelliğidir. Bunu kullanarak yapmak için `dotnet-trace` `dotnet-trace collect -- <command>` Yukarıdaki örneklerde açıklandığı gibi kullanabilirsiniz veya `--diagnostic-port` seçeneğini kullanabilirsiniz.

`dotnet-trace <collect|monitor> -- <command>`Uygulamayı bir alt işlem olarak başlatmak için kullanmak, bunu başlangıçtan hızlı bir şekilde izlemenin en kolay yoludur.

Ancak, izlenen uygulamanın ömrü boyunca daha ayrıntılı bir denetim elde etmek istediğinizde (örneğin, uygulamayı yalnızca ilk 10 dakika boyunca izleyin ve yürütülmeye devam edin) veya CLı kullanarak uygulamayla etkileşime ihtiyacınız varsa, kullanma `--diagnostic-port` seçeneği, hem izlenen hem de hedef uygulamayı denetlemenize olanak tanır `dotnet-trace` .

1. Aşağıdaki komut `dotnet-trace` adlı bir tanılama yuvası oluşturur `myport.sock` ve bir bağlantı bekler.

    > ```dotnet-cli
    > dotnet-trace collect --diagnostic-port myport.sock
    > ```

    Çıkış:

    > ```bash
    > Waiting for connection on myport.sock
    > Start an application with the following environment variable: DOTNET_DiagnosticPorts=/home/user/myport.sock
    > ```

2. Ayrı bir konsolda, hedef uygulamayı `DOTNET_DiagnosticPorts` Çıkış içindeki değere ayarlanmış ortam değişkeni ile başlatın `dotnet-trace` .

    > ```bash
    > export DOTNET_DiagnosticPorts=/home/user/myport.sock
    > ./my-dotnet-app arg1 arg2
    > ```

    `dotnet-trace`İzlemeye başlamak için bu daha sonra etkinleştirmelisiniz `my-dotnet-app` :

    > ```bash
    > Waiting for connection on myport.sock
    > Start an application with the following environment variable: DOTNET_DiagnosticPorts=myport.sock
    > Starting a counter session. Press Q to quit.
    > ```

    > [!IMPORTANT]
    > `dotnet run`DotNet CLI, uygulamanız olmayan çok sayıda alt işlem oluşturduğundan ve uygulamanızın `dotnet-trace` çalışma zamanında askıya alınması için uygulamadan önce bağlanabildikleri için uygulamanızın ile başlatılması sorunlu olabilir. Uygulamanın otomatik olarak kapsanan bir sürümünü kullanmanız veya `dotnet exec` uygulamayı başlatmak için kullanmanız önerilir.

## <a name="view-the-trace-captured-from-dotnet-trace"></a>DotNet 'den yakalanan izlemeyi görüntüleyin-Trace

Windows 'da *. NetTrace* dosyaları analiz Için [PerfView](https://github.com/microsoft/perfview) üzerinde görüntülenebilir: diğer platformlarda toplanan izlemeler Için, izleme dosyası PerfView 'Da görüntülenmek üzere bir Windows makinesine taşınabilir.

Linux 'ta izleme, ' nin çıkış biçimi değiştirilerek görüntülenebilir `dotnet-trace` `speedscope` . Çıkış dosyası biçimi, seçeneği kullanılarak değiştirilebilir, `-f|--format` `-f speedscope` `dotnet-trace` bir `speedscope` dosya oluşturur. `nettrace`(Varsayılan seçenek) ve arasında seçim yapabilirsiniz `speedscope` . `Speedscope` dosyalar ' de açılabilir <https://www.speedscope.app> .

> [!NOTE]
> .NET Core çalışma zamanı, biçimde izleme oluşturur `nettrace` . İzlemeler, izleme tamamlandıktan sonra speedscope (belirtilmişse) olarak dönüştürülür. Bazı dönüştürmeler veri kaybına neden olabileceğinden, özgün `nettrace` Dosya Dönüştürülen dosyanın yanında korunur.

## <a name="use-dotnet-trace-to-collect-counter-values-over-time"></a>Zaman içinde sayaç değerlerini toplamak için DotNet-Trace kullanın

`dotnet-trace` erişebilirsiniz

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

## <a name="use-rsp-file-to-avoid-typing-long-commands"></a>Uzun komutların yazımasını önlemek için. rsp dosyasını kullanın

`dotnet-trace` `.rsp` Geçirilecek bağımsız değişkenleri içeren bir dosyayla başlatabilirsiniz. Bu, uzun bağımsız değişkenler bekleyen veya karakter şeritleri kullanan bir kabuk ortamını kullanırken yararlı olabilir.

Örneğin, aşağıdaki sağlayıcı, izlemek istediğiniz her seferinde yazmamasız bir şekilde olabilir:

```cmd
dotnet-trace collect --providers Microsoft-Diagnostics-DiagnosticSource:0x3:5:FilterAndPayloadSpecs="SqlClientDiagnosticListener/System.Data.SqlClient.WriteCommandBefore@Activity1Start:-Command;Command.CommandText;ConnectionId;Operation;Command.Connection.ServerVersion;Command.CommandTimeout;Command.CommandType;Command.Connection.ConnectionString;Command.Connection.Database;Command.Connection.DataSource;Command.Connection.PacketSize\r\nSqlClientDiagnosticListener/System.Data.SqlClient.WriteCommandAfter@Activity1Stop:\r\nMicrosoft.EntityFrameworkCore/Microsoft.EntityFrameworkCore.Database.Command.CommandExecuting@Activity2Start:-Command;Command.CommandText;ConnectionId;IsAsync;Command.Connection.ClientConnectionId;Command.Connection.ServerVersion;Command.CommandTimeout;Command.CommandType;Command.Connection.ConnectionString;Command.Connection.Database;Command.Connection.DataSource;Command.Connection.PacketSize\r\nMicrosoft.EntityFrameworkCore/Microsoft.EntityFrameworkCore.Database.Command.CommandExecuted@Activity2Stop:",OtherProvider,AnotherProvider
```

Ayrıca, önceki örnek `"` bağımsız değişkenin bir parçası olarak içerir. Teklifler her kabukta eşit olarak işlenmediğinden, farklı kabuklar kullanırken çeşitli sorunlarla karşılaşabilirsiniz. Örneğin, içine girilecek komut `zsh` içindeki komutuna farklıdır `cmd` .

Bu her seferinde yazmak yerine, aşağıdaki metni adlı bir dosyaya kaydedebilirsiniz `myprofile.rsp` .

```txt
--providers
Microsoft-Diagnostics-DiagnosticSource:0x3:5:FilterAndPayloadSpecs="SqlClientDiagnosticListener/System.Data.SqlClient.WriteCommandBefore@Activity1Start:-Command;Command.CommandText;ConnectionId;Operation;Command.Connection.ServerVersion;Command.CommandTimeout;Command.CommandType;Command.Connection.ConnectionString;Command.Connection.Database;Command.Connection.DataSource;Command.Connection.PacketSize\r\nSqlClientDiagnosticListener/System.Data.SqlClient.WriteCommandAfter@Activity1Stop:\r\nMicrosoft.EntityFrameworkCore/Microsoft.EntityFrameworkCore.Database.Command.CommandExecuting@Activity2Start:-Command;Command.CommandText;ConnectionId;IsAsync;Command.Connection.ClientConnectionId;Command.Connection.ServerVersion;Command.CommandTimeout;Command.CommandType;Command.Connection.ConnectionString;Command.Connection.Database;Command.Connection.DataSource;Command.Connection.PacketSize\r\nMicrosoft.EntityFrameworkCore/Microsoft.EntityFrameworkCore.Database.Command.CommandExecuted@Activity2Stop:",OtherProvider,AnotherProvider
```

Kaydettikten sonra `myprofile.rsp` , `dotnet-trace` aşağıdaki komutu kullanarak bu yapılandırmayla başlatabilirsiniz:

```bash
dotnet-trace @myprofile.rsp
```

## <a name="see-also"></a>Ayrıca bkz.

- [.NET 'ten tanınmış olay sağlayıcıları](well-known-event-providers.md)
