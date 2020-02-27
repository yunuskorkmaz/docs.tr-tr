---
title: DotNet test komutu
description: DotNet test komutu, belirli bir projedeki birim testlerini yürütmek için kullanılır.
ms.date: 05/29/2018
ms.openlocfilehash: 890d1fc3fd9d47f2bdcd63f2a25248c3edd705e4
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/26/2020
ms.locfileid: "77626053"
---
# <a name="dotnet-test"></a>dotnet test

**Bu makale şu şekilde geçerlidir:** ✔️ .net Core 2,1 SDK ve sonraki sürümleri

## <a name="name"></a>Adı

birim testlerini yürütmek için kullanılan `dotnet test` .NET test sürücüsü.

## <a name="synopsis"></a>Özeti

```dotnetcli
dotnet test [<PROJECT>] [-a|--test-adapter-path] [--blame]
    [-c|--configuration] [--collect] [-d|--diag] [-f|--framework]
    [--filter] [-l|--logger] [--no-build] [--no-restore]
    [-o|--output] [-r|--results-directory] [-s|--settings]
    [-t|--list-tests] [-v|--verbosity] [-- <RunSettings arguments>]

dotnet test [-h|--help]
```

## <a name="description"></a>Açıklama

`dotnet test` komutu, belirli bir projedeki birim testlerini yürütmek için kullanılır. `dotnet test` komutu, bir proje için belirtilen Test Çalıştırıcısı konsol uygulamasını başlatır. Test Çalıştırıcısı, bir birim test çerçevesi (örneğin, MSTest, NUnit veya xUnit) için tanımlanan testleri yürütür ve her testin başarısını veya başarısızlığını bildirir. Tüm testler başarılı olursa, Test Çalıştırıcısı çıkış kodu olarak 0 döndürür; Aksi takdirde, herhangi bir test başarısız olursa, 1 döndürür. Test Çalıştırıcısı ve birim testi kitaplığı, NuGet paketleri olarak paketlenir ve proje için sıradan bağımlılıklar olarak geri yüklenir.

Test projeleri, aşağıdaki örnek proje dosyasında görüldüğü gibi sıradan bir `<PackageReference>` öğesi kullanarak Test Çalıştırıcısı belirtir:

[!code-xml[XUnit Basic Template](../../../samples/snippets/csharp/xunit-test/xunit-test.csproj)]

## <a name="arguments"></a>Bağımsız Değişkenler

- **`PROJECT`**

  Test projesinin yolu. Belirtilmezse, varsayılan olarak geçerli dizin olur.

## <a name="options"></a>Seçenekler

- **`a|--test-adapter-path <PATH_TO_ADAPTER>`**

  Test çalıştırmasında belirtilen yoldan özel test bağdaştırıcılarını kullanın.

- **`-blame`**

  Testleri sorumluyu modunda çalıştırır. Bu seçenek, test ana bilgisayarının kilitlenmesine neden olan sorunlu testleri yalıtmak için yararlıdır. Geçerli dizinde, kilitlenmeden önce yürütülen testlerin sırasını yakalayan *Sequence. xml* olarak bir çıktı dosyası oluşturur.

- **`c|--configuration {Debug|Release}`**

  Yapı yapılandırmasını tanımlar. Varsayılan değer `Debug`, ancak projenizin yapılandırması bu varsayılan SDK ayarını geçersiz kılabilir.

- **`-collect <DATA_COLLECTOR_FRIENDLY_NAME>`**

  Test çalıştırması için veri toplayıcıyı etkinleştirilir. Daha fazla bilgi için bkz. [test çalıştırmasını izleme ve çözümleme](https://aka.ms/vstest-collect).

- **`d|--diag <PATH_TO_DIAGNOSTICS_FILE>`**

  Test platformu için tanılama modunu sağlar ve belirtilen dosyaya tanılama iletileri yazar.

- **`f|--framework <FRAMEWORK>`**

  Belirli bir [çerçeve](../../standard/frameworks.md)için test ikililerini arar.

- **`--filter <EXPRESSION>`**

  Geçerli projede verilen ifadeyi kullanarak testleri filtreler. Daha fazla bilgi için, [filtre seçeneği ayrıntıları](#filter-option-details) bölümüne bakın. Seçmeli birim testi filtrelemeyi kullanma hakkında daha fazla bilgi ve örnekler için bkz. [Seçmeli birim testlerini çalıştırma](../testing/selective-unit-tests.md).

- **`h|--help`**

  Komut için kısa bir yardım yazdırır.

- **`l|--logger <LoggerUri/FriendlyName>`**

  Test sonuçları için bir günlükçü belirtir.

- **`--no-build`**

  Test projesi çalıştırılmadan önce derlenmez. Ayrıca,-`--no-restore` bayrağını örtülü olarak ayarlar.

- **`--no-restore`**

  Komutu çalıştırılırken örtük geri yükleme yürütülmez.

- **`-o|--output <OUTPUT_DIRECTORY>`**

  Çalıştırılacak ikililerin bulunacağı dizin.

- **`-r|--results-directory <PATH>`**

  Test sonuçlarının yerleştirileceği dizin. Belirtilen dizin yoksa, oluşturulur.

- **`-s|--settings <SETTINGS_FILE>`**

  Testleri çalıştırmak için kullanılacak `.runsettings` dosyası. [`.runsettings` bir dosya kullanarak birim testlerini yapılandırın.](/visualstudio/test/configure-unit-tests-by-using-a-dot-runsettings-file)

- **`-t|--list-tests`**

  Geçerli projedeki tüm bulunan testlerin listesini listeleyin.

- **`-v|--verbosity <LEVEL>`**

  Komutun ayrıntı düzeyini ayarlar. İzin verilen değerler `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`ve `diag[nostic]`.

- `RunSettings` bağımsız değişkenleri

  Bağımsız değişkenler test için `RunSettings` yapılandırma olarak geçirilir. Bağımsız değişkenler "--" sonra `[name]=[value]` çiftleri olarak belirtilir (--After--------- Birden çok `[name]=[value]` çiftini ayırmak için bir boşluk kullanılır.

  Örnek: `dotnet test -- MSTest.DeploymentEnabled=false MSTest.MapInconclusiveToFailed=True`

  Daha fazla bilgi için bkz. [VSTest. Console. exe: RunSettings args geçirme](https://github.com/Microsoft/vstest-docs/blob/master/docs/RunSettingsArguments.md).

## <a name="examples"></a>Örnekler

- Projedeki testleri geçerli dizinde çalıştırın:

  ```dotnetcli
  dotnet test
  ```

- `test1` projesindeki testleri çalıştırın:

  ```dotnetcli
  dotnet test ~/projects/test1/test1.csproj
  ```

- Projedeki testleri geçerli dizinde çalıştırın ve TRX biçiminde bir test sonuçları dosyası oluşturun:

  ```dotnetcli
  dotnet test --logger trx
  ```

## <a name="filter-option-details"></a>Filtre seçeneği ayrıntıları

`--filter <EXPRESSION>`

`<Expression>` `<property><operator><value>[|&<Expression>]`biçimine sahiptir.

`<property>`, `Test Case`özniteliğidir. Popüler birim testi çerçeveleri tarafından desteklenen özellikler aşağıda verilmiştir:

| Test çerçevesi | Desteklenen özellikler                                                                                      |
| -------------- | --------------------------------------------------------------------------------------------------------- |
| MSTest         | <ul><li>TamAdı</li><li>Adı</li><li>Sınıf</li><li>Öncelik</li><li>TestCategory</li></ul> |
| xUnit          | <ul><li>TamAdı</li><li>DisplayName</li><li>Lerdir</li></ul>                                   |

`<operator>`, özelliği ve değeri arasındaki ilişkiyi açıklar:

| İşleç | İşlev        |
| :------: | --------------- |
| `=`      | Tam eşleşme     |
| `!=`     | Tam eşleşme yok |
| `~`      | Contains        |
| `!~`     | İçermez    |

`<value>` bir dizedir. Tüm aramalar büyük/küçük harfe duyarlıdır.

`<operator>` olmayan bir ifade `FullyQualifiedName` özelliğinde `contains` olarak kabul edilir (örneğin, `dotnet test --filter xyz` `dotnet test --filter FullyQualifiedName~xyz`aynıdır).

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
