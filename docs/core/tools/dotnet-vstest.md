---
title: DotNet VSTest komutu
description: DotNet VSTest komutu bir proje ve tüm bağımlılıklarını oluşturur.
ms.date: 02/27/2020
ms.openlocfilehash: f7db58f4aab59354b8c69ce0371324c23482dafe
ms.sourcegitcommit: fff146ba3fd1762c8c432d95c8b877825ae536fc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/08/2020
ms.locfileid: "82975400"
---
# <a name="dotnet-vstest"></a>dotnet vstest

**Bu makale şu şekilde geçerlidir:** ✔️ .net Core 2,1 SDK ve sonraki sürümleri

> [!IMPORTANT]
> Bu `dotnet vstest` komut, artık derlemeleri `dotnet test`çalıştırmak için kullanılabilecek tarafından değiştirildi. Bkz [`dotnet test`](dotnet-test.md)..

## <a name="name"></a>Name

`dotnet-vstest`-Belirtilen derlemelerdeki testleri çalıştırır.

## <a name="synopsis"></a>Özeti

```dotnetcli
dotnet vstest [<TEST_FILE_NAMES>] [--Blame] [--Diag <PATH_TO_LOG_FILE>]
    [--Framework <FRAMEWORK>] [--InIsolation] [-lt|--ListTests <FILE_NAME>]
    [--logger <LOGGER_URI/FRIENDLY_NAME>] [--Parallel]
    [--ParentProcessId <PROCESS_ID>] [--Platform] <PLATFORM_TYPE>
    [--Port <PORT>] [--ResultsDirectory<PATH>] [--Settings <SETTINGS_FILE>]
    [--TestAdapterPath <PATH>] [--TestCaseFilter <EXPRESSION>]
    [--Tests <TEST_NAMES>] [[--] <args>...]]

dotnet vstest -?|--Help
```

## <a name="description"></a>Açıklama

Komut `dotnet-vstest` , otomatik birim `VSTest.Console` testlerini çalıştırmak için komut satırı uygulamasını çalıştırır.

## <a name="arguments"></a>Arguments

- **`TEST_FILE_NAMES`**

  Belirtilen derlemelerdeki testleri çalıştırın. Birden çok test derleme adını boşluklarla ayırın. Joker karakterler desteklenir.

## <a name="options"></a>Seçenekler

- **`--Blame`**

  Testleri sorumluyu modunda çalıştırır. Bu seçenek, test ana bilgisayarının kilitlenmesine neden olan sorunlu testleri yalıtmak için yararlıdır. Geçerli dizinde, kilitlenmeden önce yürütülen testlerin sırasını yakalayan *Sequence. xml* olarak bir çıktı dosyası oluşturur.

- **`--Diag <PATH_TO_LOG_FILE>`**

  Test platformu için ayrıntılı günlükleri etkinleştirilir. Günlükler, belirtilen dosyaya yazılır.

- **`--Framework <FRAMEWORK>`**

  Test yürütmesi için kullanılan hedef .NET Framework sürümü. Geçerli değer örnekleri `.NETFramework,Version=v4.6` veya `.NETCoreApp,Version=v1.0`. Desteklenen diğer değerler, `Framework40` `Framework45` `FrameworkCore10`, ve `FrameworkUap10`' dir.

- **`--InIsolation`**

  Testleri yalıtılmış bir işlemde çalıştırır. Bu, *VSTest. Console. exe* işleminin testlerin bir hata üzerinde durdurulması olasılığını azaltır, ancak testler daha yavaş çalışabilir.

- **`-lt|--ListTests <FILE_NAME>`**

  Verilen test kapsayıcısından tüm bulunan testleri listeler.

- **`--logger <LOGGER_URI/FRIENDLY_NAME>`**

  Test sonuçları için bir günlükçü belirtin.

  - Team Foundation Server için test sonuçlarını yayınlamak için `TfsPublisher` günlükçü sağlayıcısını kullanın:

    ```console
    /logger:TfsPublisher;
        Collection=<team project collection url>;
        BuildName=<build name>;
        TeamProject=<team project name>
        [;Platform=<Defaults to "Any CPU">]
        [;Flavor=<Defaults to "Debug">]
        [;RunTitle=<title>]
    ```

  - Sonuçları bir Visual Studio Test Sonuçları dosyasına (TRX) kaydetmek için `trx` günlükçü sağlayıcısını kullanın. Bu anahtar, test sonuçları dizininde verilen günlük dosyası adına sahip bir dosya oluşturur. `LogFileName` Sağlanmazsa, test sonuçlarını tutmak için benzersiz bir dosya adı oluşturulur.

    ```console
    /logger:trx [;LogFileName=<Defaults to unique file name>]
    ```

- **`--Parallel`**

  Testleri paralel olarak çalıştırın. Varsayılan olarak, makinedeki tüm kullanılabilir çekirdekler kullanılabilir. `MaxCpuCount` *Runsettings* dosyasındaki `RunConfiguration` düğümü altında özelliğini ayarlayarak açık sayıda çekirdek belirtin.

- **`--ParentProcessId <PROCESS_ID>`**

  Geçerli işlemin başlatmasından sorumlu olan üst işlemin işlem KIMLIĞI.

- **`--Platform <PLATFORM_TYPE>`**

  Test yürütmesi için kullanılan hedef platform mimarisi. Geçerli değerler `x86`, `x64`, ve. `ARM`

- **`--Port <PORT>`**

  Yuva bağlantısı ve olay iletilerini alma bağlantı noktasını belirtir.

- **`--ResultsDirectory:<PATH>`**

  Mevcut değilse, belirtilen yolda test sonuçları dizini oluşturulur.

- **`--Settings <SETTINGS_FILE>`**

  Testler çalıştırılırken kullanılacak ayarlar.

- **`--TestAdapterPath <PATH>`**

  Test çalıştırmasında belirli bir yoldan (varsa) özel test bağdaştırıcıları kullanın.

- **`--TestCaseFilter <EXPRESSION>`**

  Verilen ifadeyle eşleşen testleri çalıştırın. `<EXPRESSION>`biçimindedir `<property>Operator<value>[|&<EXPRESSION>]`, burada işleci `=`, `!=`veya `~`' den biridir. İşlecinde `~` ' Contains ' semantiği var ve gibi `DisplayName`dize özellikleri için geçerlidir. Parantezler `()` , alt ifadeleri gruplandırmak için kullanılır. Daha fazla bilgi için bkz. [TestCase filtresi](https://github.com/Microsoft/vstest-docs/blob/master/docs/filter.md).

- **`--Tests <TEST_NAMES>`**

  Testleri, belirtilen değerlerle eşleşen adlarla çalıştırın. Birden çok değeri virgülle ayırın.

- **`-?|--Help`**

  Komut için kısa bir yardım yazdırır.

- **`@<file>`**

  Daha fazla seçenek için yanıt dosyasını okur.

- **`args`**

  Bağdaştırıcıya geçirilecek ek bağımsız değişkenleri belirtir. Bağımsız değişkenler, formun `<n>=<v>`ad-değer çiftleri olarak belirtilir, burada `<n>` bağımsız değişken adıdır ve `<v>` bağımsız değişken değeridir. Birden çok bağımsız değişkeni ayırmak için boşluk kullanın.

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

Testleri `TestMethod1` Çalıştır:

```dotnetcli
dotnet vstest /Tests:TestMethod1
```

Çalıştır `TestMethod1` ve `TestMethod2` testler:

```dotnetcli
dotnet vstest /Tests:TestMethod1,TestMethod2
```

## <a name="see-also"></a>Ayrıca bkz.

- [VSTest.Console.exe komut satırı seçenekleri](/visualstudio/test/vstest-console-options)
