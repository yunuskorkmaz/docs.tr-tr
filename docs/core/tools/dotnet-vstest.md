---
title: DotNet VSTest komutu
description: DotNet VSTest komutu bir proje ve tüm bağımlılıklarını oluşturur.
ms.date: 05/30/2018
ms.openlocfilehash: 3fdb5443d6d0cfbe1e7e88bc824cbb930f211260
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77451187"
---
# <a name="dotnet-vstest"></a>dotnet vstest

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>Name

`dotnet-vstest`, belirtilen dosyalardan testleri çalıştırır.

## <a name="synopsis"></a>Özeti

<!-- markdownlint-disable MD025 -->

# <a name="net-core-21"></a>[.NET Core 2,1](#tab/netcore21)

```dotnetcli
dotnet vstest [<TEST_FILE_NAMES>] [--Settings|/Settings] [--Tests|/Tests] [--TestAdapterPath|/TestAdapterPath]
    [--Platform|/Platform] [--Framework|/Framework] [--Parallel|/Parallel] [--TestCaseFilter|/TestCaseFilter] [--logger|/logger]
    [-lt|--ListTests|/lt|/ListTests] [--ParentProcessId|/ParentProcessId] [--Port|/Port] [--Diag|/Diag] [--Blame|/Blame] [--InIsolation|/InIsolation]
    [[--] <args>...]] [-?|--Help|/?|/Help]
```

# <a name="net-core-20"></a>[.NET Core 2,0](#tab/netcore20)

```dotnetcli
dotnet vstest [<TEST_FILE_NAMES>] [--Settings|/Settings] [--Tests|/Tests] [--TestAdapterPath|/TestAdapterPath] 
    [--Platform|/Platform] [--Framework|/Framework] [--Parallel|/Parallel] [--TestCaseFilter|/TestCaseFilter] [--logger|/logger]
    [-lt|--ListTests|/lt|/ListTests] [--ParentProcessId|/ParentProcessId] [--Port|/Port] [--Diag|/Diag] [[--] <args>...]] [-?|--Help|/?|/Help]
```

# <a name="net-core-1x"></a>[.NET Core 1. x](#tab/netcore1x)

```dotnetcli
dotnet vstest [<TEST_FILE_NAMES>] [--Settings|/Settings] [--Tests|/Tests] [--TestAdapterPath|/TestAdapterPath]
    [--Platform|/Platform] [--Framework|/Framework] [--Parallel|/Parallel] [--TestCaseFilter|/TestCaseFilter] [--logger|/logger] 
    [-lt|--ListTests|/lt|/ListTests] [--ParentProcessId|/ParentProcessId] [--Port|/Port] [--Diag|/Diag] [[--] <args>...]] [-?|--Help|/?|/Help]
```

---

## <a name="description"></a>Açıklama

`dotnet-vstest` komutu, otomatik birim testlerini çalıştırmak için `VSTest.Console` komut satırı uygulamasını çalıştırır.

## <a name="arguments"></a>Bağımsız Değişkenler

`TEST_FILE_NAMES`

Belirtilen derlemelerdeki testleri çalıştırın. Birden çok test derleme adını boşluklarla ayırın.

## <a name="options"></a>Seçenekler

# <a name="net-core-21"></a>[.NET Core 2,1](#tab/netcore21)

`--Settings|/Settings:<Settings File>`

Testler çalıştırılırken kullanılacak ayarlar.

`--Tests|/Tests:<Test Names>`

Testleri, belirtilen değerlerle eşleşen adlarla çalıştırın. Birden çok değeri virgülle ayırın.

`--TestAdapterPath|/TestAdapterPath`

Test çalıştırmasında belirli bir yoldan (varsa) özel test bağdaştırıcıları kullanın.

`--Platform|/Platform:<Platform type>`

Test yürütmesi için kullanılan hedef platform mimarisi. Geçerli değerler `x86`, `x64`ve `ARM`.

`--Framework|/Framework:<Framework Version>`

Test yürütmesi için kullanılan hedef .NET Framework sürümü. Geçerli değer örnekleri `.NETFramework,Version=v4.6` veya `.NETCoreApp,Version=v1.0`. Desteklenen diğer değerler `Framework40`, `Framework45`, `FrameworkCore10`ve `FrameworkUap10`.

`--Parallel|/Parallel`

Testleri paralel olarak yürütün. Varsayılan olarak, makinedeki tüm kullanılabilir çekirdekler kullanılabilir. Runsettings dosyasındaki RunConfiguration düğümü altında MaxCpuCount özelliğini ayarlayarak açık sayıda çekirdek belirtin.

`--TestCaseFilter|/TestCaseFilter:<Expression>`

Verilen ifadeyle eşleşen testleri çalıştırın. `<Expression>` biçim `<property>Operator<value>[|&<Expression>]`, burada Işleç `=`, `!=`veya `~`biridir. İşleç `~` ' Contains ' semantiğine sahiptir ve `DisplayName`gibi dize özellikleri için geçerlidir. Parantez `()` alt ifadeleri gruplandırmak için kullanılır.

`-?|--Help|/?|/Help`

Komut için kısa bir yardım yazdırır.

`--logger|/logger:<Logger Uri/FriendlyName>`

Test sonuçları için bir günlükçü belirtin.

* Test sonuçlarını Team Foundation Server yayımlamak için `TfsPublisher` günlükçü sağlayıcısını kullanın:

  ```console
  /logger:TfsPublisher;
      Collection=<team project collection url>;
      BuildName=<build name>;
      TeamProject=<team project name>
      [;Platform=<Defaults to "Any CPU">]
      [;Flavor=<Defaults to "Debug">]
      [;RunTitle=<title>]
  ```

* Sonuçları bir Visual Studio Test Sonuçları dosyasına (TRX) kaydetmek için `trx` günlükçü sağlayıcısını kullanın. Bu anahtar, test sonuçları dizininde verilen günlük dosyası adına sahip bir dosya oluşturur. `LogFileName` sağlanmazsa, test sonuçlarını tutmak için benzersiz bir dosya adı oluşturulur.

  ```console
  /logger:trx [;LogFileName=<Defaults to unique file name>]
  ```

`-lt|--ListTests|/lt|/ListTests:<File Name>`

Verilen test kapsayıcısından tüm bulunan testleri listeler.

`--ParentProcessId|/ParentProcessId:<ParentProcessId>`

Geçerli işlemin başlatmasından sorumlu olan üst işlemin işlem KIMLIĞI.

`--Port|/Port:<Port>`

Yuva bağlantısı ve olay iletilerini alma bağlantı noktasını belirtir.

`--Diag|/Diag:<Path to log file>`

Test platformu için ayrıntılı günlükleri etkinleştirilir. Günlükler, belirtilen dosyaya yazılır.

`--Blame|/Blame`

Testleri sorumluyu modunda çalıştırır. Bu seçenek, test ana bilgisayarının kilitlenmesine neden olan sorunlu testleri yalıtmak için yararlıdır. Geçerli dizinde, kilitlenmeden önce yürütülen testlerin sırasını yakalayan *Sequence. xml* olarak bir çıktı dosyası oluşturur.

`--InIsolation|/InIsolation`

Testleri yalıtılmış bir işlemde çalıştırır. Bu, *VSTest. Console. exe* işleminin testlerin bir hata üzerinde durdurulması olasılığını azaltır, ancak testler daha yavaş çalışabilir.

`@<file>`

Daha fazla seçenek için yanıt dosyasını okur.

`args`

Bağdaştırıcıya geçirilecek ek bağımsız değişkenleri belirtir. Bağımsız değişkenler `<n>=<v>`biçim-değer çiftleri olarak belirtilir; burada `<n>` bağımsız değişken adıdır ve `<v>` bağımsız değişken değeridir. Birden çok bağımsız değişkeni ayırmak için boşluk kullanın.

# <a name="net-core-20"></a>[.NET Core 2,0](#tab/netcore20)

`--Settings|/Settings:<Settings File>`

Testler çalıştırılırken kullanılacak ayarlar.

`--Tests|/Tests:<Test Names>`

Testleri, belirtilen değerlerle eşleşen adlarla çalıştırın. Birden çok değeri virgülle ayırın.

`--TestAdapterPath|/TestAdapterPath`

Test çalıştırmasında belirli bir yoldan (varsa) özel test bağdaştırıcıları kullanın.

`--Platform|/Platform:<Platform type>`

Test yürütmesi için kullanılan hedef platform mimarisi. Geçerli değerler `x86`, `x64`ve `ARM`.

`--Framework|/Framework:<Framework Version>`

Test yürütmesi için kullanılan hedef .NET Framework sürümü. Geçerli değer örnekleri `.NETFramework,Version=v4.6` veya `.NETCoreApp,Version=v1.0`. Desteklenen diğer değerler `Framework40`, `Framework45`ve `FrameworkCore10`.

`--Parallel|/Parallel`

Testleri paralel olarak yürütün. Varsayılan olarak, makinedeki tüm kullanılabilir çekirdekler kullanılabilir. Runsettings dosyasındaki RunConfiguration düğümü altında MaxCpuCount özelliğini ayarlayarak açık sayıda çekirdek belirtin.

`--TestCaseFilter|/TestCaseFilter:<Expression>`

Verilen ifadeyle eşleşen testleri çalıştırın. `<Expression>` biçim `<property>Operator<value>[|&<Expression>]`, burada Işleç `=`, `!=`veya `~`biridir. İşleç `~` ' Contains ' semantiğine sahiptir ve `DisplayName`gibi dize özellikleri için geçerlidir. Parantez `()` alt ifadeleri gruplandırmak için kullanılır.

`-?|--Help|/?|/Help`

Komut için kısa bir yardım yazdırır.

`--logger|/logger:<Logger Uri/FriendlyName>`

Test sonuçları için bir günlükçü belirtin.

* Test sonuçlarını Team Foundation Server yayımlamak için `TfsPublisher` günlükçü sağlayıcısını kullanın:

  ```console
  /logger:TfsPublisher;
      Collection=<team project collection url>;
      BuildName=<build name>;
      TeamProject=<team project name>
      [;Platform=<Defaults to "Any CPU">]
      [;Flavor=<Defaults to "Debug">]
      [;RunTitle=<title>]
  ```

* Sonuçları bir Visual Studio Test Sonuçları dosyasına (TRX) kaydetmek için `trx` günlükçü sağlayıcısını kullanın. Bu anahtar, test sonuçları dizininde verilen günlük dosyası adına sahip bir dosya oluşturur. `LogFileName` sağlanmazsa, test sonuçlarını tutmak için benzersiz bir dosya adı oluşturulur.

  ```console
  /logger:trx [;LogFileName=<Defaults to unique file name>]
  ```

`-lt|--ListTests|/lt|/ListTests:<File Name>`

Verilen test kapsayıcısından tüm bulunan testleri listeler.

`--ParentProcessId|/ParentProcessId:<ParentProcessId>`

Geçerli işlemin başlatmasından sorumlu olan üst işlemin işlem KIMLIĞI.

`--Port|/Port:<Port>`

Yuva bağlantısı ve olay iletilerini alma bağlantı noktasını belirtir.

`--Diag|/Diag:<Path to log file>`

Test platformu için ayrıntılı günlükleri etkinleştirilir. Günlükler, belirtilen dosyaya yazılır.

`args`

Bağdaştırıcıya geçirilecek ek bağımsız değişkenleri belirtir. Bağımsız değişkenler `<n>=<v>`biçim-değer çiftleri olarak belirtilir; burada `<n>` bağımsız değişken adıdır ve `<v>` bağımsız değişken değeridir. Birden çok bağımsız değişkeni ayırmak için boşluk kullanın.

# <a name="net-core-1x"></a>[.NET Core 1. x](#tab/netcore1x)

`--Settings|/Settings:<Settings File>`

Testler çalıştırılırken kullanılacak ayarlar.

`--Tests|/Tests:<Test Names>`

Testleri, belirtilen değerlerle eşleşen adlarla çalıştırın. Birden çok değeri virgülle ayırın.

`--TestAdapterPath|/TestAdapterPath`

Test çalıştırmasında belirli bir yoldan (varsa) özel test bağdaştırıcıları kullanın.

`--Platform|/Platform:<Platform type>`

Test yürütmesi için kullanılan hedef platform mimarisi. Geçerli değerler `x86`, `x64`ve `ARM`.

`--Framework|/Framework:<Framework Version>`

Test yürütmesi için kullanılan hedef .NET Framework sürümü. Geçerli değer örnekleri `.NETFramework,Version=v4.6` veya `.NETCoreApp,Version=v1.0`. Desteklenen diğer değerler `Framework40`, `Framework45`ve `FrameworkCore10`.

`--Parallel|/Parallel`

Testleri paralel olarak yürütün. Varsayılan olarak, makinedeki tüm kullanılabilir çekirdekler kullanılabilir. Runsettings dosyasındaki RunConfiguration düğümü altında MaxCpuCount özelliğini ayarlayarak açık sayıda çekirdek belirtin.

`--TestCaseFilter|/TestCaseFilter:<Expression>`

Verilen ifadeyle eşleşen testleri çalıştırın. `<Expression>` biçim `<property>Operator<value>[|&<Expression>]`, burada Işleç `=`, `!=`veya `~`biridir. İşleç `~` ' Contains ' semantiğine sahiptir ve `DisplayName`gibi dize özellikleri için geçerlidir. Parantez `()` alt ifadeleri gruplandırmak için kullanılır.

`-?|--Help|/?|/Help`

Komut için kısa bir yardım yazdırır.

`--logger|/logger:<Logger Uri/FriendlyName>`

Test sonuçları için bir günlükçü belirtin.

* Test sonuçlarını Team Foundation Server yayımlamak için `TfsPublisher` günlükçü sağlayıcısını kullanın:

  ```console
  /logger:TfsPublisher;
      Collection=<team project collection url>;
      BuildName=<build name>;
      TeamProject=<team project name>
      [;Platform=<Defaults to "Any CPU">]
      [;Flavor=<Defaults to "Debug">]
      [;RunTitle=<title>]
  ```

* Sonuçları bir Visual Studio Test Sonuçları dosyasına (TRX) kaydetmek için `trx` günlükçü sağlayıcısını kullanın. Bu anahtar, test sonuçları dizininde verilen günlük dosyası adına sahip bir dosya oluşturur. `LogFileName` sağlanmazsa, test sonuçlarını tutmak için benzersiz bir dosya adı oluşturulur.

  ```console
  /logger:trx [;LogFileName=<Defaults to unique file name>]
  ```

`-lt|--ListTests|/lt|/ListTests:<File Name>`

Verilen test kapsayıcısından tüm bulunan testleri listeler.

`--ParentProcessId|/ParentProcessId:<ParentProcessId>`

Geçerli işlemin başlatmasından sorumlu olan üst işlemin işlem KIMLIĞI.

`--Port|/Port:<Port>`

Yuva bağlantısı ve olay iletilerini alma bağlantı noktasını belirtir.

`--Diag|/Diag:<Path to log file>`

Test platformu için ayrıntılı günlükleri etkinleştirilir. Günlükler, belirtilen dosyaya yazılır.

`args`

Bağdaştırıcıya geçirilecek ek bağımsız değişkenleri belirtir. Bağımsız değişkenler `<n>=<v>`biçim-değer çiftleri olarak belirtilir; burada `<n>` bağımsız değişken adıdır ve `<v>` bağımsız değişken değeridir. Birden çok bağımsız değişkeni ayırmak için boşluk kullanın.

---

## <a name="examples"></a>Örnekler

`mytestproject.dll`Testleri Çalıştır:

`dotnet vstest mytestproject.dll`

Testleri `mytestproject.dll`' de Çalıştır, özel bir klasöre dışarı aktarma özel adı:

`dotnet vstest mytestproject.dll --logger:"trx;LogFileName=custom_file_name.trx" --ResultsDirectory:custom/file/path`

`mytestproject.dll` ve `myothertestproject.exe`testleri çalıştırın:

`dotnet vstest mytestproject.dll myothertestproject.exe`

`TestMethod1` testlerini Çalıştır:

`dotnet vstest /Tests:TestMethod1`

`TestMethod1` Çalıştır ve Testleri `TestMethod2`:

`dotnet vstest /Tests:TestMethod1,TestMethod2`
