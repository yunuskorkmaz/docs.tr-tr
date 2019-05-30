---
title: DotNet vstest komutu
description: Dotnet vstest komutu, bir projeyi ve tüm bağımlılıklarını oluşturur.
author: mairaw
ms.date: 05/30/2018
ms.openlocfilehash: 45fda3b34d2649bc6f20cf3f35c65277a9a53cec
ms.sourcegitcommit: 621a5f6df00152006160987395b93b5b55f7ffcd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66300040"
---
# <a name="dotnet-vstest"></a>dotnet vstest

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>Ad

`dotnet-vstest` -Belirtilen dosyalardan testleri çalıştırır.

## <a name="synopsis"></a>Synopsis

# <a name="net-core-21tabnetcore21"></a>[.NET core 2.1](#tab/netcore21)

```
dotnet vstest [<TEST_FILE_NAMES>] [--Settings|/Settings] [--Tests|/Tests] [--TestAdapterPath|/TestAdapterPath]
    [--Platform|/Platform] [--Framework|/Framework] [--Parallel|/Parallel] [--TestCaseFilter|/TestCaseFilter] [--logger|/logger]
    [-lt|--ListTests|/lt|/ListTests] [--ParentProcessId|/ParentProcessId] [--Port|/Port] [--Diag|/Diag] [--Blame|/Blame] [--InIsolation|/InIsolation]
    [[--] <args>...]] [-?|--Help|/?|/Help]
```

# <a name="net-core-20tabnetcore20"></a>[.NET core 2.0](#tab/netcore20)

```
dotnet vstest [<TEST_FILE_NAMES>] [--Settings|/Settings] [--Tests|/Tests] [--TestAdapterPath|/TestAdapterPath] 
    [--Platform|/Platform] [--Framework|/Framework] [--Parallel|/Parallel] [--TestCaseFilter|/TestCaseFilter] [--logger|/logger]
    [-lt|--ListTests|/lt|/ListTests] [--ParentProcessId|/ParentProcessId] [--Port|/Port] [--Diag|/Diag] [[--] <args>...]] [-?|--Help|/?|/Help]
```

# <a name="net-core-1xtabnetcore1x"></a>[.NET core 1.x](#tab/netcore1x)

```
dotnet vstest [<TEST_FILE_NAMES>] [--Settings|/Settings] [--Tests|/Tests] [--TestAdapterPath|/TestAdapterPath]
    [--Platform|/Platform] [--Framework|/Framework] [--Parallel|/Parallel] [--TestCaseFilter|/TestCaseFilter] [--logger|/logger] 
    [-lt|--ListTests|/lt|/ListTests] [--ParentProcessId|/ParentProcessId] [--Port|/Port] [--Diag|/Diag] [[--] <args>...]] [-?|--Help|/?|/Help]
```

---

## <a name="description"></a>Açıklama

`dotnet-vstest` Komutu çalıştırmaları `VSTest.Console` otomatik birim testleri çalıştırmak için komut satırı uygulamasıdır.

## <a name="arguments"></a>Arguments

`TEST_FILE_NAMES`

Belirtilen derlemelerden testleri çalıştırın. Birden çok test derleme adlarının boşluklarla ayırın.

## <a name="options"></a>Seçenekler

# <a name="net-core-21tabnetcore21"></a>[.NET core 2.1](#tab/netcore21)

`--Settings|/Settings:<Settings File>`

Testleri çalıştırırken kullanılacak ayarlar.

`--Tests|/Tests:<Test Names>`

Testleri sağlanan değerlerle eşleşen adlarla çalıştırın. Birden çok değer virgülle ayırın.

`--TestAdapterPath|/TestAdapterPath`

Özel test bağdaştırıcılarını verilen yoldan (varsa) test çalıştırmasında kullanın.

`--Platform|/Platform:<Platform type>`

Hedef platform mimarisi, test yürütmesi için kullanılır. Geçerli değerler `x86`, `x64`, ve `ARM`.

`--Framework|/Framework:<Framework Version>`

Test çalıştırması için kullanılan hedef .NET Framework sürümü. Geçerli değerler örnekler `.NETFramework,Version=v4.6` veya `.NETCoreApp,Version=v1.0`. Desteklenen diğer değerler `Framework40`, `Framework45`, `FrameworkCore10`, ve `FrameworkUap10`.

`--Parallel|/Parallel`

Testleri paralel olarak yürütür. Varsayılan olarak, makinedeki tüm mevcut çekirdekler kullanılabilir duruma gelir. Runsettings dosyasında RunConfiguration düğümü altındaki MaxCpuCount özelliği ayarlayarak açık bir çekirdek sayısını belirtin.

`--TestCaseFilter|/TestCaseFilter:<Expression>`

Verili ifadeyle eşleşen testler çalıştırın. `<Expression>` biçimi `<property>Operator<value>[|&<Expression>]`, burada işleç birini `=`, `!=`, veya `~`. İşleç `~` gibi dize özellikleri için geçerlidir ve 'contains' semantiğe sahip `DisplayName`. Parantez `()` alt ifadeleri gruplamak için kullanılır.

`-?|--Help|/?|/Help`

Komut için kısa bir Yardım yazdırır.

`--logger|/logger:<Logger Uri/FriendlyName>`

Test sonuçları için bir Günlükçü belirtin.

* Team Foundation Server test sonuçlarını yayımlamak için kullanmak `TfsPublisher` Günlükçü sağlayıcısı:

  ```
  /logger:TfsPublisher;
      Collection=<team project collection url>;
      BuildName=<build name>;
      TeamProject=<team project name>
      [;Platform=<Defaults to "Any CPU">]
      [;Flavor=<Defaults to "Debug">]
      [;RunTitle=<title>]
  ```

* Bir Visual Studio Test sonuçları dosyası (TRX) için sonuçlar'ı açmak için kullandığınız `trx` Günlükçü sağlayıcısı. Bu anahtar test sonuçlarında bir dosya oluşturur. günlük dosyası adı verilen ile dizin. Varsa `LogFileName` test sonuçlarını tutmak için benzersiz bir dosya adı oluşturan koşuluyla değil.

  ```
  /logger:trx [;LogFileName=<Defaults to unique file name>]
  ```

`-lt|--ListTests|/lt|/ListTests:<File Name>`

Tüm, verili test kapsayıcısından bulunan testleri listeler.

`--ParentProcessId|/ParentProcessId:<ParentProcessId>`

Geçerli işlem başlatmaktan sorumlu üst işlemin işlem kimliği.

`--Port|/Port:<Port>`

Yuva bağlantısı ve olay iletileri almak için bir bağlantı noktasını belirtir.

`--Diag|/Diag:<Path to log file>`

Ayrıntılı günlükler için test platformu sağlar. Günlükleri, belirtilen dosyaya yazılır.

`--Blame|/Blame`

Testleri sorumluyu modunda çalıştırır. Bu seçenek, sorunlu testleri test ana bilgisayarı kilitlenmesine neden olan sorunları ayırmanıza yardımcı olur. Bir çıkış dosyası geçerli dizinde oluşturur *Sequence.xml* , kilitlenme önce testler yürütme sırası yakalar.

`--InIsolation|/InIsolation`

Testleri yalıtılmış bir işlemde çalıştırır. Böylece *vstest.console.exe* büyük olasılıkla daha az bir hata sırasında durdurulması işlemi, ancak testleri daha yavaş çalışabilir.

`@<file>`

Daha fazla seçenek için yanıt dosyasını okur.

`args`

Bağdaştırıcıya geçirilecek ek bağımsız değişkenleri belirtir. Bağımsız değişkenler formun ad-değer çiftleri olarak belirtilen `<n>=<v>`burada `<n>` bağımsız değişken adıdır ve `<v>` bağımsız değişken değeri. Birden çok bağımsız değişkeni ayırmak için boşluk kullanın.

# <a name="net-core-20tabnetcore20"></a>[.NET core 2.0](#tab/netcore20)

`--Settings|/Settings:<Settings File>`

Testleri çalıştırırken kullanılacak ayarlar.

`--Tests|/Tests:<Test Names>`

Testleri sağlanan değerlerle eşleşen adlarla çalıştırın. Birden çok değer virgülle ayırın.

`--TestAdapterPath|/TestAdapterPath`

Özel test bağdaştırıcılarını verilen yoldan (varsa) test çalıştırmasında kullanın.

`--Platform|/Platform:<Platform type>`

Hedef platform mimarisi, test yürütmesi için kullanılır. Geçerli değerler `x86`, `x64`, ve `ARM`.

`--Framework|/Framework:<Framework Version>`

Test çalıştırması için kullanılan hedef .NET Framework sürümü. Geçerli değerler örnekler `.NETFramework,Version=v4.6` veya `.NETCoreApp,Version=v1.0`. Desteklenen diğer değerler `Framework40`, `Framework45`, ve `FrameworkCore10`.

`--Parallel|/Parallel`

Testleri paralel olarak yürütür. Varsayılan olarak, makinedeki tüm mevcut çekirdekler kullanılabilir duruma gelir. Runsettings dosyasında RunConfiguration düğümü altındaki MaxCpuCount özelliği ayarlayarak açık bir çekirdek sayısını belirtin.

`--TestCaseFilter|/TestCaseFilter:<Expression>`

Verili ifadeyle eşleşen testler çalıştırın. `<Expression>` biçimi `<property>Operator<value>[|&<Expression>]`, burada işleç birini `=`, `!=`, veya `~`. İşleç `~` gibi dize özellikleri için geçerlidir ve 'contains' semantiğe sahip `DisplayName`. Parantez `()` alt ifadeleri gruplamak için kullanılır.

`-?|--Help|/?|/Help`

Komut için kısa bir Yardım yazdırır.

`--logger|/logger:<Logger Uri/FriendlyName>`

Test sonuçları için bir Günlükçü belirtin.

* Team Foundation Server test sonuçlarını yayımlamak için kullanmak `TfsPublisher` Günlükçü sağlayıcısı:

  ```
  /logger:TfsPublisher;
      Collection=<team project collection url>;
      BuildName=<build name>;
      TeamProject=<team project name>
      [;Platform=<Defaults to "Any CPU">]
      [;Flavor=<Defaults to "Debug">]
      [;RunTitle=<title>]
  ```

* Bir Visual Studio Test sonuçları dosyası (TRX) için sonuçlar'ı açmak için kullandığınız `trx` Günlükçü sağlayıcısı. Bu anahtar test sonuçlarında bir dosya oluşturur. günlük dosyası adı verilen ile dizin. Varsa `LogFileName` test sonuçlarını tutmak için benzersiz bir dosya adı oluşturan koşuluyla değil.

  ```
  /logger:trx [;LogFileName=<Defaults to unique file name>]
  ```

`-lt|--ListTests|/lt|/ListTests:<File Name>`

Tüm, verili test kapsayıcısından bulunan testleri listeler.

`--ParentProcessId|/ParentProcessId:<ParentProcessId>`

Geçerli işlem başlatmaktan sorumlu üst işlemin işlem kimliği.

`--Port|/Port:<Port>`

Yuva bağlantısı ve olay iletileri almak için bir bağlantı noktasını belirtir.

`--Diag|/Diag:<Path to log file>`

Ayrıntılı günlükler için test platformu sağlar. Günlükleri, belirtilen dosyaya yazılır.

`args`

Bağdaştırıcıya geçirilecek ek bağımsız değişkenleri belirtir. Bağımsız değişkenler formun ad-değer çiftleri olarak belirtilen `<n>=<v>`burada `<n>` bağımsız değişken adıdır ve `<v>` bağımsız değişken değeri. Birden çok bağımsız değişkeni ayırmak için boşluk kullanın.

# <a name="net-core-1xtabnetcore1x"></a>[.NET core 1.x](#tab/netcore1x)

`--Settings|/Settings:<Settings File>`

Testleri çalıştırırken kullanılacak ayarlar.

`--Tests|/Tests:<Test Names>`

Testleri sağlanan değerlerle eşleşen adlarla çalıştırın. Birden çok değer virgülle ayırın.

`--TestAdapterPath|/TestAdapterPath`

Özel test bağdaştırıcılarını verilen yoldan (varsa) test çalıştırmasında kullanın.

`--Platform|/Platform:<Platform type>`

Hedef platform mimarisi, test yürütmesi için kullanılır. Geçerli değerler `x86`, `x64`, ve `ARM`.

`--Framework|/Framework:<Framework Version>`

Test çalıştırması için kullanılan hedef .NET Framework sürümü. Geçerli değerler örnekler `.NETFramework,Version=v4.6` veya `.NETCoreApp,Version=v1.0`. Desteklenen diğer değerler `Framework40`, `Framework45`, ve `FrameworkCore10`.

`--Parallel|/Parallel`

Testleri paralel olarak yürütür. Varsayılan olarak, makinedeki tüm mevcut çekirdekler kullanılabilir duruma gelir. Runsettings dosyasında RunConfiguration düğümü altındaki MaxCpuCount özelliği ayarlayarak açık bir çekirdek sayısını belirtin.

`--TestCaseFilter|/TestCaseFilter:<Expression>`

Verili ifadeyle eşleşen testler çalıştırın. `<Expression>` biçimi `<property>Operator<value>[|&<Expression>]`, burada işleç birini `=`, `!=`, veya `~`. İşleç `~` gibi dize özellikleri için geçerlidir ve 'contains' semantiğe sahip `DisplayName`. Parantez `()` alt ifadeleri gruplamak için kullanılır.

`-?|--Help|/?|/Help`

Komut için kısa bir Yardım yazdırır.

`--logger|/logger:<Logger Uri/FriendlyName>`

Test sonuçları için bir Günlükçü belirtin.

* Team Foundation Server test sonuçlarını yayımlamak için kullanmak `TfsPublisher` Günlükçü sağlayıcısı:

  ```
  /logger:TfsPublisher;
      Collection=<team project collection url>;
      BuildName=<build name>;
      TeamProject=<team project name>
      [;Platform=<Defaults to "Any CPU">]
      [;Flavor=<Defaults to "Debug">]
      [;RunTitle=<title>]
  ```

* Bir Visual Studio Test sonuçları dosyası (TRX) için sonuçlar'ı açmak için kullandığınız `trx` Günlükçü sağlayıcısı. Bu anahtar test sonuçlarında bir dosya oluşturur. günlük dosyası adı verilen ile dizin. Varsa `LogFileName` test sonuçlarını tutmak için benzersiz bir dosya adı oluşturan koşuluyla değil.

  ```
  /logger:trx [;LogFileName=<Defaults to unique file name>]
  ```

`-lt|--ListTests|/lt|/ListTests:<File Name>`

Tüm, verili test kapsayıcısından bulunan testleri listeler.

`--ParentProcessId|/ParentProcessId:<ParentProcessId>`

Geçerli işlem başlatmaktan sorumlu üst işlemin işlem kimliği.

`--Port|/Port:<Port>`

Yuva bağlantısı ve olay iletileri almak için bir bağlantı noktasını belirtir.

`--Diag|/Diag:<Path to log file>`

Ayrıntılı günlükler için test platformu sağlar. Günlükleri, belirtilen dosyaya yazılır.

`args`

Bağdaştırıcıya geçirilecek ek bağımsız değişkenleri belirtir. Bağımsız değişkenler formun ad-değer çiftleri olarak belirtilen `<n>=<v>`burada `<n>` bağımsız değişken adıdır ve `<v>` bağımsız değişken değeri. Birden çok bağımsız değişkeni ayırmak için boşluk kullanın.

---

## <a name="examples"></a>Örnekler

Testleri Çalıştır `mytestproject.dll`:

`dotnet vstest mytestproject.dll`

Testleri Çalıştır `mytestproject.dll`, dışa aktarma için özel bir ada sahip özel klasör:

`dotnet vstest mytestproject.dll --logger:"trx;LogFileName=custom_file_name.trx" --ResultsDirectory:custom/file/path`

Testleri Çalıştır `mytestproject.dll` ve `myothertestproject.exe`:

`dotnet vstest mytestproject.dll myothertestproject.exe`

Çalıştırma `TestMethod1` testler:

`dotnet vstest /Tests:TestMethod1`

Çalıştırma `TestMethod1` ve `TestMethod2` testler:

`dotnet vstest /Tests:TestMethod1,TestMethod2`
