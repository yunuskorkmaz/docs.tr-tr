---
title: DotNet VSTest komutu
description: DotNet VSTest komutu bir proje ve tüm bağımlılıklarını oluşturur.
ms.date: 05/30/2018
ms.openlocfilehash: fc0aa4f9abf069f78e27692ee84aea2559109c98
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/26/2020
ms.locfileid: "77626027"
---
# <a name="dotnet-vstest"></a>dotnet vstest

**Bu makale şu şekilde geçerlidir:** ✔️ .net Core 2,1 SDK ve sonraki sürümleri

## <a name="name"></a>Adı

`dotnet-vstest`, belirtilen dosyalardan testleri çalıştırır.

## <a name="synopsis"></a>Özeti

```dotnetcli
dotnet vstest [<TEST_FILE_NAMES>] [--Settings] [--Tests]
    [--TestAdapterPath] [--Platform] [--Framework] [--Parallel]
    [--TestCaseFilter] [--logger] [-lt|--ListTests]
    [--ParentProcessId] [--Port] [--Diag] [--Blame]
    [--InIsolation] [[--] <args>...]] [-?|--Help]
```

## <a name="description"></a>Açıklama

`dotnet-vstest` komutu, otomatik birim testlerini çalıştırmak için `VSTest.Console` komut satırı uygulamasını çalıştırır.

## <a name="arguments"></a>Bağımsız Değişkenler

- **`TEST_FILE_NAMES`**

  Belirtilen derlemelerdeki testleri çalıştırın. Birden çok test derleme adını boşluklarla ayırın. Joker karakterler desteklenir.

## <a name="options"></a>Seçenekler

- **`--Settings <Settings File>`**

  Testler çalıştırılırken kullanılacak ayarlar.

- **`--Tests <Test Names>`**

  Testleri, belirtilen değerlerle eşleşen adlarla çalıştırın. Birden çok değeri virgülle ayırın.

- **`--TestAdapterPath`**

  Test çalıştırmasında belirli bir yoldan (varsa) özel test bağdaştırıcıları kullanın.

- **`--Platform <Platform type>`**

  Test yürütmesi için kullanılan hedef platform mimarisi. Geçerli değerler `x86`, `x64`ve `ARM`.

- **`--Framework <Framework Version>`**

  Test yürütmesi için kullanılan hedef .NET Framework sürümü. Geçerli değer örnekleri `.NETFramework,Version=v4.6` veya `.NETCoreApp,Version=v1.0`. Desteklenen diğer değerler `Framework40`, `Framework45`, `FrameworkCore10`ve `FrameworkUap10`.

- **`--Parallel`**

  Testleri paralel olarak çalıştırın. Varsayılan olarak, makinedeki tüm kullanılabilir çekirdekler kullanılabilir. *Runsettings* dosyasındaki `RunConfiguration` düğümü altında `MaxCpuCount` özelliğini ayarlayarak, açık sayıda çekirdek belirtin.

- **`--TestCaseFilter <Expression>`**

  Verilen ifadeyle eşleşen testleri çalıştırın. `<Expression>` biçim `<property>Operator<value>[|&<Expression>]`, burada Işleç `=`, `!=`veya `~`biridir. İşleç `~` ' Contains ' semantiğine sahiptir ve `DisplayName`gibi dize özellikleri için geçerlidir. Parantez `()` alt ifadeleri gruplandırmak için kullanılır.

- **`-?|--Help`**

  Komut için kısa bir yardım yazdırır.

- **`--logger <Logger Uri/FriendlyName>`**

  Test sonuçları için bir günlükçü belirtin.

  - Test sonuçlarını Team Foundation Server yayımlamak için `TfsPublisher` günlükçü sağlayıcısını kullanın:

    ```console
    /logger:TfsPublisher;
        Collection=<team project collection url>;
        BuildName=<build name>;
        TeamProject=<team project name>
        [;Platform=<Defaults to "Any CPU">]
        [;Flavor=<Defaults to "Debug">]
        [;RunTitle=<title>]
    ```

  - Sonuçları bir Visual Studio Test Sonuçları dosyasına (TRX) kaydetmek için `trx` günlükçü sağlayıcısını kullanın. Bu anahtar, test sonuçları dizininde verilen günlük dosyası adına sahip bir dosya oluşturur. `LogFileName` sağlanmazsa, test sonuçlarını tutmak için benzersiz bir dosya adı oluşturulur.

    ```console
    /logger:trx [;LogFileName=<Defaults to unique file name>]
    ```

- **`-lt|--ListTests <File Name>`**

  Verilen test kapsayıcısından tüm bulunan testleri listeler.

- **`--ParentProcessId <ParentProcessId>`**

  Geçerli işlemin başlatmasından sorumlu olan üst işlemin işlem KIMLIĞI.

- **`--Port <Port>`**

  Yuva bağlantısı ve olay iletilerini alma bağlantı noktasını belirtir.

- **`--Diag <Path to log file>`**

  Test platformu için ayrıntılı günlükleri etkinleştirilir. Günlükler, belirtilen dosyaya yazılır.

- **`--Blame`**

  Testleri sorumluyu modunda çalıştırır. Bu seçenek, test ana bilgisayarının kilitlenmesine neden olan sorunlu testleri yalıtmak için yararlıdır. Geçerli dizinde, kilitlenmeden önce yürütülen testlerin sırasını yakalayan *Sequence. xml* olarak bir çıktı dosyası oluşturur.

- **`--InIsolation`**

  Testleri yalıtılmış bir işlemde çalıştırır. Bu, *VSTest. Console. exe* işleminin testlerin bir hata üzerinde durdurulması olasılığını azaltır, ancak testler daha yavaş çalışabilir.

- **`@<file>`**

  Daha fazla seçenek için yanıt dosyasını okur.

- **`args`**

  Bağdaştırıcıya geçirilecek ek bağımsız değişkenleri belirtir. Bağımsız değişkenler `<n>=<v>`biçim-değer çiftleri olarak belirtilir; burada `<n>` bağımsız değişken adıdır ve `<v>` bağımsız değişken değeridir. Birden çok bağımsız değişkeni ayırmak için boşluk kullanın.

## <a name="examples"></a>Örnekler

Testleri *MyTestProject. dll*içinde Çalıştır:

```dotnetcli
dotnet vstest mytestproject.dll
```

Testleri *MyTestProject. dll*içinde çalıştırın, özel adla özel klasöre dışarı aktarma:

```dotnetcli
dotnet vstest mytestproject.dll --logger:"trx;LogFileName=custom_file_name.trx" --ResultsDirectory:custom/file/path
```

*Testprojem. dll* ve *myothertestproject. exe*' de testleri çalıştırın:

```dotnetcli
dotnet vstest mytestproject.dll myothertestproject.exe
```

`TestMethod1` testlerini Çalıştır:

```dotnetcli
dotnet vstest /Tests:TestMethod1
```

`TestMethod1` Çalıştır ve Testleri `TestMethod2`:

```dotnetcli
dotnet vstest /Tests:TestMethod1,TestMethod2
```
