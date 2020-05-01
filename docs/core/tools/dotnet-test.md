---
title: DotNet test komutu
description: DotNet test komutu, belirli bir projedeki birim testlerini yürütmek için kullanılır.
ms.date: 04/29/2020
ms.openlocfilehash: a8218b6596601069b89a60ad018adf89a1f47cf6
ms.sourcegitcommit: e09dbff13f0b21b569a101f3b3c5efa174aec204
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/01/2020
ms.locfileid: "82624897"
---
# <a name="dotnet-test"></a>dotnet test

**Bu makale şu şekilde geçerlidir:** ✔️ .net Core 2,1 SDK ve sonraki sürümleri

## <a name="name"></a>Adı

`dotnet test`-Birim testlerini yürütmek için kullanılan .NET test sürücüsü.

## <a name="synopsis"></a>Özeti

```dotnetcli
dotnet test [<PROJECT> | <SOLUTION>]
    [-a|--test-adapter-path <PATH_TO_ADAPTER>] [--blame]
    [-c|--configuration <CONFIGURATION>]
    [--collect <DATA_COLLECTOR_FRIENDLY_NAME>]
    [-d|--diag <PATH_TO_DIAGNOSTICS_FILE>] [-f|--framework <FRAMEWORK>]
    [--filter <EXPRESSION>] [--interactive]
    [-l|--logger <LOGGER_URI/FRIENDLY_NAME>] [--no-build]
    [--nologo] [--no-restore] [-o|--output <OUTPUT_DIRECTORY>]
    [-r|--results-directory <PATH>] [--runtime <RUNTIME_IDENTIFIER>]
    [-s|--settings <SETTINGS_FILE>] [-t|--list-tests]
    [-v|--verbosity <LEVEL>] [[--] <RunSettings arguments>]

dotnet test -h|--help
```

## <a name="description"></a>Açıklama

Komut `dotnet test` , belirli bir projedeki birim testlerini yürütmek için kullanılır. Komut `dotnet test` , bir proje için belirtilen Test Çalıştırıcısı konsol uygulamasını başlatır. Test Çalıştırıcısı, bir birim test çerçevesi (örneğin, MSTest, NUnit veya xUnit) için tanımlanan testleri yürütür ve her testin başarısını veya başarısızlığını bildirir. Tüm testler başarılı olursa, Test Çalıştırıcısı çıkış kodu olarak 0 döndürür; Aksi takdirde, herhangi bir test başarısız olursa, 1 döndürür. Çok hedefli projeler için testler hedeflenen her çerçeve için çalıştırılır. Test Çalıştırıcısı ve birim testi kitaplığı, NuGet paketleri olarak paketlenir ve proje için sıradan bağımlılıklar olarak geri yüklenir.

Test projeleri, aşağıdaki örnek proje dosyasında görüldüğü gibi `<PackageReference>` sıradan bir öğe kullanarak Test Çalıştırıcısı belirtir:

[!code-xml[XUnit Basic Template](../../../samples/snippets/csharp/xunit-test/xunit-test.csproj)]

### <a name="implicit-restore"></a>Örtük geri yükleme

[!INCLUDE[dotnet restore note](~/includes/dotnet-restore-note.md)]

## <a name="arguments"></a>Bağımsız Değişkenler

- **`PROJECT | SOLUTION`**

  Test projesinin veya çözümünün yolu. Belirtilmezse, varsayılan olarak geçerli dizin olur.

## <a name="options"></a>Seçenekler

- **`-a|--test-adapter-path <PATH_TO_ADAPTER>`**

  Test çalıştırmasında belirtilen yoldan özel test bağdaştırıcılarını kullanın.

- **`--blame`**

  Testleri sorumluyu modunda çalıştırır. Bu seçenek, test ana bilgisayarının kilitlenmesine neden olan sorunlu testleri yalıtmak için yararlıdır. Geçerli dizinde, kilitlenmeden önce yürütülen testlerin sırasını yakalayan *Sequence. xml* olarak bir çıktı dosyası oluşturur.

- **`-c|--configuration <CONFIGURATION>`**

  Yapı yapılandırmasını tanımlar. Varsayılan değer `Debug`, ancak projenizin yapılandırması bu varsayılan SDK ayarını geçersiz kılabilir.

- **`--collect <DATA_COLLECTOR_FRIENDLY_NAME>`**

  Test çalıştırması için veri toplayıcıyı etkinleştirilir. Daha fazla bilgi için bkz. [test çalıştırmasını izleme ve çözümleme](https://aka.ms/vstest-collect).

- **`-d|--diag <PATH_TO_DIAGNOSTICS_FILE>`**

  Test platformu için tanılama modunu sağlar ve tanılama iletilerini belirtilen dosyaya yazar.

- **`-f|--framework <FRAMEWORK>`**

  Belirli bir [çerçeve](../../standard/frameworks.md)için test ikililerini arar.

- **`--filter <EXPRESSION>`**

  Geçerli projede verilen ifadeyi kullanarak testleri filtreler. Daha fazla bilgi için, [filtre seçeneği ayrıntıları](#filter-option-details) bölümüne bakın. Seçmeli birim testi filtrelemeyi kullanma hakkında daha fazla bilgi ve örnekler için bkz. [Seçmeli birim testlerini çalıştırma](../testing/selective-unit-tests.md).

- **`-h|--help`**

  Komut için kısa bir yardım yazdırır.

- **`--interactive`**

  Komutun Kullanıcı girişini veya eylemini durdurmasına ve beklemesine izin verir. Örneğin, kimlik doğrulamasını tamamlamaya yönelik. .NET Core 3,0 SDK 'dan beri kullanılabilir.

- **`-l|--logger <LOGGER_URI/FRIENDLY_NAME>`**

  Test sonuçları için bir günlükçü belirtir. MSBuild 'in `-l "console;v=d"` aksine, DotNet testi kısaltmalar kabul etmez: kullanım `-l "console;verbosity=detailed"`yerine.

- **`--no-build`**

  Test projesi çalıştırılmadan önce derlenmez. Ayrıca,- `--no-restore` bayrağını örtülü olarak ayarlar.

- **`--nologo`**

  Testleri, Microsoft TestPlatform başlığını görüntülemeden çalıştırın. .NET Core 3,0 SDK 'dan beri kullanılabilir.

- **`--no-restore`**

  Komutu çalıştırılırken örtük geri yükleme yürütülmez.

- **`-o|--output <OUTPUT_DIRECTORY>`**

  Çalıştırılacak ikililerin bulunacağı dizin. Belirtilmemişse, varsayılan yol olur `./bin/<configuration>/<framework>/`.  Birden çok hedef çerçevesi olan projeler için ( `TargetFrameworks` özelliği aracılığıyla), bu seçeneği ne zaman belirttiğinizde `--framework` de tanımlamanız gerekir. `dotnet test`testleri her zaman çıkış dizininden çalıştırın. ' I, <xref:System.AppDomain.BaseDirectory%2A?displayProperty=nameWithType> çıkış dizininde test varlıklarını kullanmak için kullanabilirsiniz.

- **`-r|--results-directory <PATH>`**

  Test sonuçlarının yerleştirileceği dizin. Belirtilen dizin yoksa, oluşturulur. Varsayılan değer `TestResults` proje dosyasını içeren dizindir.

- **`--runtime <RUNTIME_IDENTIFIER>`**

  Sınanacak hedef çalışma zamanı.

- **`-s|--settings <SETTINGS_FILE>`**

  Testleri `.runsettings` çalıştırmak için kullanılacak dosya. `TargetPlatform` Öğesinin (x86 | x64) için `dotnet test`hiçbir etkisi olmadığını unutmayın. X86 'yı hedefleyen testleri çalıştırmak için .NET Core 'un x86 sürümünü yükler. Yoldaki *DotNet. exe* ' nin bit genişliği, testleri çalıştırmak için kullanılacak şeydir. daha fazla bilgi için aşağıdaki kaynaklara bakın:

  - [Birim testlerini bir `.runsettings` dosya kullanarak yapılandırın.](/visualstudio/test/configure-unit-tests-by-using-a-dot-runsettings-file)
  - [Test çalıştırması yapılandırma](https://github.com/Microsoft/vstest-docs/blob/master/docs/configure.md)

- **`-t|--list-tests`**

  Geçerli projedeki tüm bulunan testlerin listesini listeleyin.

- **`-v|--verbosity <LEVEL>`**

  Komutun ayrıntı düzeyini ayarlar. İzin verilen değerler `q[uiet]` `m[inimal]` `n[ormal]` `d[etailed]`,,, ve `diag[nostic]`. Varsayılan değer: `minimal`. Daha fazla bilgi için bkz. <xref:Microsoft.Build.Framework.LoggerVerbosity>.

- **`RunSettings`** değişkenlerinden

  Bağımsız değişkenler test için `RunSettings` yapılandırma olarak geçirilir. Bağımsız değişkenler "- `[name]=[value]` -" sonra çift olarak belirtilir (--sonra boşluk bırakın). Birden çok `[name]=[value]` çifti ayırmak için bir boşluk kullanılır.

  Örnek: `dotnet test -- MSTest.DeploymentEnabled=false MSTest.MapInconclusiveToFailed=True`

  Daha fazla bilgi için bkz. [komut satırı aracılığıyla RunSettings bağımsız değişkenlerini geçirme](https://github.com/Microsoft/vstest-docs/blob/master/docs/RunSettingsArguments.md).

## <a name="examples"></a>Örnekler

- Projedeki testleri geçerli dizinde çalıştırın:

  ```dotnetcli
  dotnet test
  ```

- `test1` Projedeki testleri çalıştırın:

  ```dotnetcli
  dotnet test ~/projects/test1/test1.csproj
  ```

- Projedeki testleri geçerli dizinde çalıştırın ve TRX biçiminde bir test sonuçları dosyası oluşturun:

  ```dotnetcli
  dotnet test --logger trx
  ```

- Projedeki testleri geçerli dizinde çalıştırın ve konsolun ayrıntılı ayrıntı düzeyi ile günlüğe kaydedin:

  ```dotnetcli
  dotnet test --logger "console;verbosity=detailed"
  ```

## <a name="filter-option-details"></a>Filtre seçeneği ayrıntıları

`--filter <EXPRESSION>`

`<Expression>`biçimindedir `<property><operator><value>[|&<Expression>]`.

`<property>`, `Test Case`öğesinin bir özniteliğidir. Popüler birim testi çerçeveleri tarafından desteklenen özellikler aşağıda verilmiştir:

| Test çerçevesi | Desteklenen özellikler                                                                                      |
| -------------- | --------------------------------------------------------------------------------------------------------- |
| MSTest         | <ul><li>FullyQualifiedName</li><li>Adı</li><li>Sınıf</li><li>Öncelik</li><li>TestCategory</li></ul> |
| xUnit          | <ul><li>FullyQualifiedName</li><li>DisplayName</li><li>Lerdir</li></ul>                                   |

, `<operator>` Özelliği ve değeri arasındaki ilişkiyi açıklar:

| İşleç | İşlev        |
| :------: | --------------- |
| `=`      | Tam eşleşme     |
| `!=`     | Tam eşleşme yok |
| `~`      | Contains        |
| `!~`     | İçermez    |

`<value>`bir dizedir. Tüm aramalar büyük/küçük harfe duyarlıdır.

`<operator>` Bir ifadesi, otomatik olarak `contains` on `FullyQualifiedName` özelliği olarak kabul edilir (örneğin, `dotnet test --filter xyz` ile `dotnet test --filter FullyQualifiedName~xyz`aynıdır).

İfadeler koşullu işleçlerle birleştirilebilecek:

| İşleç            | İşlev |
| ------------------- | -------- |
| <code>&#124;</code> | OR       |
| `&`                 | AND      |

Koşullu işleçler kullandığınızda (örneğin, `(Name~TestMethod1) | (Name~TestMethod2)`) ifadeleri parantez içine alabilirsiniz.

Seçmeli birim testi filtrelemeyi kullanma hakkında daha fazla bilgi ve örnekler için bkz. [Seçmeli birim testlerini çalıştırma](../testing/selective-unit-tests.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Çerçeveler ve hedefler](../../standard/frameworks.md)
- [.NET Core çalışma zamanı tanımlayıcısı (RID) kataloğu](../rid-catalog.md)
- [Komut satırı aracılığıyla runsettings bağımsız değişkenlerini geçirme](https://github.com/Microsoft/vstest-docs/blob/master/docs/RunSettingsArguments.md)
