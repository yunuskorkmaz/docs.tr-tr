---
title: dotnet test komutu
description: Dotnet test komutu, belirli bir projede birim testlerini yürütmek için kullanılır.
ms.date: 02/27/2020
ms.openlocfilehash: a11814f9fdc6326e681a09d7d2654b968014f318
ms.sourcegitcommit: 2514f4e3655081dcfe1b22470c0c28500f952c42
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "79507314"
---
# <a name="dotnet-test"></a>dotnet test

**Bu makale şu şekilde dir:** ✔️ .NET Core 2.1 SDK ve sonraki sürümler

## <a name="name"></a>Adı

`dotnet test`- .NET test sürücüsü birim testleri yürütmek için kullanılır.

## <a name="synopsis"></a>Özet

```dotnetcli
dotnet test [<PROJECT> | <SOLUTION>]
    [-a|--test-adapter-path] [--blame] [-c|--configuration]
    [--collect] [-d|--diag] [-f|--framework] [--filter]
    [--interactive] [-l|--logger] [--no-build] [--nologo]
    [--no-restore] [-o|--output] [-r|--results-directory]
    [--runtime] [-s|--settings] [-t|--list-tests]
    [-v|--verbosity] [[--] <RunSettings arguments>]

dotnet test [-h|--help]
```

## <a name="description"></a>Açıklama

Komut, `dotnet test` belirli bir projede birim testlerini yürütmek için kullanılır. Komut, `dotnet test` proje için belirtilen test runner konsolu uygulamasını başlatır. Test runner bir birim test çerçevesi (örneğin, MSTest, NUnit veya xUnit) için tanımlanan testleri yürütür ve her testin başarısını veya başarısızlığını bildirir. Tüm testler başarılı olursa, test koşucusu çıkış kodu olarak 0 döndürür; aksi takdirde herhangi bir test başarısız olursa, 1 döndürür. Test koşucusu ve birim test kitaplığı NuGet paketleri olarak paketlenir ve proje için olağan bağımlılıklar olarak geri yüklenir.

Test projeleri, aşağıdaki örnek `<PackageReference>` proje dosyasında görüldüğü gibi, sıradan bir öğe kullanarak test koşucusu belirtir:

[!code-xml[XUnit Basic Template](../../../samples/snippets/csharp/xunit-test/xunit-test.csproj)]

## <a name="arguments"></a>Bağımsız Değişkenler

- **`PROJECT | SOLUTION`**

  Test projesine veya çözüme giden yol. Belirtilmemişse, varsayılan olarak geçerli dizini alır.

## <a name="options"></a>Seçenekler

- **`a|--test-adapter-path <PATH_TO_ADAPTER>`**

  Test çalışmasında belirtilen yoldan özel test bağdaştırıcılarını kullanın.

- **`--blame`**

  Testleri suçlama modunda çalıştırır. Bu seçenek, test ana bilgisayarının çökmesine neden olan sorunlu testleri yalıtmada yararlıdır. Bu, çökmeden önce testlerin yürütülmesi sırasını yakalayan *Sequence.xml* olarak geçerli dizinde bir çıktı dosyası oluşturur.

- **`c|--configuration <CONFIGURATION>`**

  Yapı yapılandırmasını tanımlar. Varsayılan değer, `Debug`ancak projenizin yapılandırmabu varsayılan SDK ayarını geçersiz kılabilir.

- **`-collect <DATA_COLLECTOR_FRIENDLY_NAME>`**

  Test çalışması için veri toplayıcısını sağlar. Daha fazla bilgi için, [bkz.](https://aka.ms/vstest-collect)

- **`d|--diag <PATH_TO_DIAGNOSTICS_FILE>`**

  Test platformu için tanılama modunu etkinleştirin ve belirtilen dosyaya tanılama iletileri yazar.

- **`f|--framework <FRAMEWORK>`**

  Belirli bir [çerçeve](../../standard/frameworks.md)için test ikilileri arar.

- **`--filter <EXPRESSION>`**

  Verilen ifadeyi kullanarak geçerli projedeki testleri filtreler. Daha fazla bilgi için [Filtre seçeneği ayrıntıları](#filter-option-details) bölümüne bakın. Seçici birim test filtrelemenin nasıl kullanılacağı hakkında daha fazla bilgi ve örnekler için seçici [birim testlerini çalıştırma'ya](../testing/selective-unit-tests.md)bakın.

- **`h|--help`**

  Komut için kısa bir yardım yazdırır.

- **`--interactive`**

  Komutun durmasını ve kullanıcı girişi veya eylemini beklemesini sağlar. Örneğin, kimlik doğrulamasını tamamlamak için. .NET Core 3.0 SDK'dan beri mevcuttur.

- **`l|--logger <LoggerUri/FriendlyName>`**

  Test sonuçları için bir logger belirtir.

- **`--no-build`**

  Çalıştırmadan önce test projesini oluşturmaz. Ayrıca örtülü olarak - `--no-restore` bayrak ayarlar.

- **`--nologo`**

  Microsoft TestPlatform banner'ını görüntülemeden testleri çalıştırın. .NET Core 3.0 SDK'dan beri mevcuttur.

- **`--no-restore`**

  Komutu çalıştırırken örtük bir geri yükleme yürütmez.

- **`-o|--output <OUTPUT_DIRECTORY>`**

  Hangi çalıştırmak için ikili bulmak için dizin.

- **`-r|--results-directory <PATH>`**

  Test sonuçlarının yerleştirilebileceği dizin. Belirtilen dizin yoksa oluşturulur.

- **`--runtime <RUNTIME_IDENTIFIER>`**

  Test etmek için hedef çalışma zamanı.

- **`-s|--settings <SETTINGS_FILE>`**

  Testleri `.runsettings` çalıştırmak için kullanılacak dosya. [Birim testlerini bir `.runsettings` dosya kullanarak yapılandırın.](/visualstudio/test/configure-unit-tests-by-using-a-dot-runsettings-file)

- **`-t|--list-tests`**

  Geçerli projede keşfedilen tüm testleri listele.

- **`-v|--verbosity <LEVEL>`**

  Komutun ayrıntılı düzeyini ayarlar. İzin verilen `q[uiet]` `m[inimal]`değerler `n[ormal]` `d[etailed]`, `diag[nostic]`, , , ve .

- `RunSettings`Bağımsız değişken

  Bağımsız değişkenler `RunSettings` test için yapılandırmaolarak geçirilir. Bağımsız değişkenler `[name]=[value]` "-- " (sonra daki boşluğa dikkat ...... Bir boşluk birden çok `[name]=[value]` çifti ayırmak için kullanılır.

  Örnek: `dotnet test -- MSTest.DeploymentEnabled=false MSTest.MapInconclusiveToFailed=True`

  Daha fazla bilgi için [vstest.console.exe: RunSettings args'ı geçmek](https://github.com/Microsoft/vstest-docs/blob/master/docs/RunSettingsArguments.md).

## <a name="examples"></a>Örnekler

- Projedeki testleri geçerli dizinde çalıştırın:

  ```dotnetcli
  dotnet test
  ```

- Projedeki testleri `test1` çalıştırın:

  ```dotnetcli
  dotnet test ~/projects/test1/test1.csproj
  ```

- Projedeki testleri geçerli dizinde çalıştırın ve trx formatında bir test sonuçları dosyası oluşturun:

  ```dotnetcli
  dotnet test --logger trx
  ```

## <a name="filter-option-details"></a>Filtre seçeneği ayrıntıları

`--filter <EXPRESSION>`

`<Expression>`biçimi `<property><operator><value>[|&<Expression>]`vardır.

`<property>`bir `Test Case`özelliktir. Popüler birim test çerçeveleri tarafından desteklenen özellikler şunlardır:

| Test Çerçevesi | Desteklenen özellikler                                                                                      |
| -------------- | --------------------------------------------------------------------------------------------------------- |
| MSTest         | <ul><li>Fullyqualifiedname</li><li>Adı</li><li>Classname</li><li>Öncelik</li><li>TestKategorisi</li></ul> |
| xBirim          | <ul><li>Fullyqualifiedname</li><li>DisplayName</li><li>Özellik</li></ul>                                   |

Özellik `<operator>` ve değer arasındaki ilişkiyi açıklar:

| İşleç | İşlev        |
| :------: | --------------- |
| `=`      | Tam eşleşme     |
| `!=`     | Tam eşleşme yok |
| `~`      | Contains        |
| `!~`     | İçermez    |

`<value>`bir dizedir. Tüm aramalar duyarsız.

Bir ifadesi `<operator>` olmayan bir `contains` ifade otomatik `FullyQualifiedName` olarak açık `dotnet test --filter xyz` özellik olarak `dotnet test --filter FullyQualifiedName~xyz`kabul edilir (örneğin, aynıdır).

İfadeler koşullu işleçlerle birleşebilir:

| İşleç            | İşlev |
| ------------------- | -------- |
| <code>&#124;</code> | OR       |
| `&`                 | AND      |

Koşullu işleçleri kullanırken ifadeleri parantez içine alabilirsiniz (örneğin, `(Name~TestMethod1) | (Name~TestMethod2)`).

Seçici birim test filtrelemenin nasıl kullanılacağı hakkında daha fazla bilgi ve örnekler için seçici [birim testlerini çalıştırma'ya](../testing/selective-unit-tests.md)bakın.

## <a name="see-also"></a>Ayrıca bkz.

- [Çerçeveler ve Hedefler](../../standard/frameworks.md)
- [.NET Core Runtime Tanımlayıcı (RID) kataloğu](../rid-catalog.md)
