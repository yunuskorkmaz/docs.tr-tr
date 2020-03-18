---
title: dotnet vstest komutu
description: Dotnet vstest komutu bir proje ve tüm bağımlılıklarını oluşturur.
ms.date: 02/27/2020
ms.openlocfilehash: 88e5b6a8966d78d0746f9ea5ccbccab142a2e0f6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "78156939"
---
# <a name="dotnet-vstest"></a>dotnet vstest

**Bu makale şu şekilde dir:** ✔️ .NET Core 2.1 SDK ve sonraki sürümler

## <a name="name"></a>Adı

`dotnet-vstest`- Belirtilen dosyalardan testleri çalıştırın.

## <a name="synopsis"></a>Özet

```dotnetcli
dotnet vstest [<TEST_FILE_NAMES>] [--Settings] [--Tests]
    [--TestAdapterPath] [--Platform] [--Framework] [--Parallel]
    [--TestCaseFilter] [--logger] [-lt|--ListTests]
    [--ParentProcessId] [--Port] [--Diag] [--Blame]
    [--InIsolation] [[--] <args>...]] [-?|--Help]
```

## <a name="description"></a>Açıklama

Komut, `dotnet-vstest` otomatik `VSTest.Console` birim testlerini çalıştırmak için komut satırı uygulamasını çalıştırAr.

## <a name="arguments"></a>Bağımsız Değişkenler

- **`TEST_FILE_NAMES`**

  Belirtilen derlemelerden testleri çalıştırın. Birden çok test derleme adını boşluklarla ayırın. Joker karakterler desteklenir.

## <a name="options"></a>Seçenekler

- **`--Settings <Settings File>`**

  Testleri çalıştırırken kullanılacak ayarlar.

- **`--Tests <Test Names>`**

  Sağlanan değerlerle eşleşen adlarla testleri çalıştırın. Birden çok değeri virgülle ayırın.

- **`--TestAdapterPath`**

  Test çalışmasında belirli bir yoldan (varsa) özel test bağdaştırıcıları kullanın.

- **`--Platform <Platform type>`**

  Test yürütme için kullanılan hedef platform mimarisi. Geçerli değerler `x86` `x64`, `ARM`ve .

- **`--Framework <Framework Version>`**

  Test yürütmesi için kullanılan Hedef .NET Framework sürümü. Geçerli değerlere `.NETFramework,Version=v4.6` örnek `.NETCoreApp,Version=v1.0`olarak . Desteklenen diğer değerler `Framework40` `Framework45`, `FrameworkCore10`, `FrameworkUap10`, ve .

- **`--Parallel`**

  Testleri paralel olarak çalıştırın. Varsayılan olarak, makinedeki tüm kullanılabilir çekirdekler kullanılabilir. Runsettings dosyasındaki `MaxCpuCount` `RunConfiguration` düğümün altındaki özelliği ayarlayarak açık *runsettings* sayıda çekirdek belirtin.

- **`--TestCaseFilter <Expression>`**

  Verilen ifadeyle eşleşen testler çalıştırın. `<Expression>`biçimindedir `<property>Operator<value>[|&<Expression>]`, Operatör biri olduğu `=` `!=`, `~`, veya . İşleç `~` 'içerir' semantik ve gibi `DisplayName`dize özellikleri için geçerlidir. `()` Alt ifadeleri gruplandırmak için parantez kullanılır.

- **`-?|--Help`**

  Komut için kısa bir yardım yazdırır.

- **`--logger <Logger Uri/FriendlyName>`**

  Test sonuçları için bir logger belirtin.

  - Test sonuçlarını Team Foundation Server'da `TfsPublisher` yayımlamak için kaydedici sağlayıcıyı kullanın:

    ```console
    /logger:TfsPublisher;
        Collection=<team project collection url>;
        BuildName=<build name>;
        TeamProject=<team project name>
        [;Platform=<Defaults to "Any CPU">]
        [;Flavor=<Defaults to "Debug">]
        [;RunTitle=<title>]
    ```

  - Sonuçları Visual Studio Test Sonuçları Dosyasına (TRX) kaydetmek için logger sağlayıcısını `trx` kullanın. Bu anahtar, test sonuçları dizininde verilen günlük dosyası adı içeren bir dosya oluşturur. Sağlanmadıysa, `LogFileName` test sonuçlarını tutmak için benzersiz bir dosya adı oluşturulur.

    ```console
    /logger:trx [;LogFileName=<Defaults to unique file name>]
    ```

- **`-lt|--ListTests <File Name>`**

  Verilen test kabından keşfedilen tüm testleri listeler.

- **`--ParentProcessId <ParentProcessId>`**

  Geçerli işlemin başlatılmasından sorumlu ana işlemin işlem kimliği.

- **`--Port <Port>`**

  Soket bağlantısı ve olay iletileri almak için bağlantı noktasını belirtir.

- **`--Diag <Path to log file>`**

  Test platformu için ayrıntılı günlükleri sağlar. Günlükler sağlanan dosyaya yazılır.

- **`--Blame`**

  Testleri suçlama modunda çalıştırır. Bu seçenek, test ana bilgisayar çökmesine neden sorunlu testleri yalıtmak yararlıdır. Bu, çökmeden önce testlerin yürütülmesi sırasını yakalayan *Sequence.xml* olarak geçerli dizinde bir çıktı dosyası oluşturur.

- **`--InIsolation`**

  Testleri yalıtılmış bir işlemle çalıştırın. Bu, *vstest.console.exe* işleminin testlerdeki bir hata da durdurulmasını daha az sağlar, ancak testler daha yavaş çalışabilir.

- **`@<file>`**

  Daha fazla seçenek için yanıt dosyalarını okur.

- **`args`**

  Bağdaştırıcıya geçmek için fazladan bağımsız değişkenler belirtir. Bağımsız değişkenler formun `<n>=<v>`ad değeri çiftleri `<n>` olarak belirtilir, `<v>` bağımsız değişken adı ve bağımsız değişken değeridir. Birden çok bağımsız değişkeni ayırmak için bir boşluk kullanın.

## <a name="examples"></a>Örnekler

*mytestproject.dll*testleri çalıştırın :

```dotnetcli
dotnet vstest mytestproject.dll
```

*Mytestproject.dll'de*testleri çalıştırın, özel adla özel klasöre dışa aktarın:

```dotnetcli
dotnet vstest mytestproject.dll --logger:"trx;LogFileName=custom_file_name.trx" --ResultsDirectory:custom/file/path
```

*mytestproject.dll* ve *myothertestproject.exe*testleri çalıştırın :

```dotnetcli
dotnet vstest mytestproject.dll myothertestproject.exe
```

Testleri `TestMethod1` çalıştırın:

```dotnetcli
dotnet vstest /Tests:TestMethod1
```

Çalıştır `TestMethod1` `TestMethod2` ve testler:

```dotnetcli
dotnet vstest /Tests:TestMethod1,TestMethod2
```
