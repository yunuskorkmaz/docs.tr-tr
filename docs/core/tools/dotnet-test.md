---
title: DotNet test komutu
description: DotNet test komutu, belirli bir projedeki birim testlerini yürütmek için kullanılır.
ms.date: 05/29/2018
ms.openlocfilehash: 49926b35b418e93237a159758903c535ec6c4006
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/14/2019
ms.locfileid: "70988538"
---
# <a name="dotnet-test"></a>dotnet test

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>Ad

`dotnet test`-Birim testlerini yürütmek için kullanılan .NET test sürücüsü.

## <a name="synopsis"></a>Özeti

<!-- markdownlint-disable MD025 -->

# <a name="net-core-21tabnetcore21"></a>[.NET Core 2,1](#tab/netcore21)

```console
dotnet test [<PROJECT>] [-a|--test-adapter-path] [--blame] [-c|--configuration] [--collect] [-d|--diag] [-f|--framework] [--filter]
    [-l|--logger] [--no-build] [--no-restore] [-o|--output] [-r|--results-directory] [-s|--settings] [-t|--list-tests] 
    [-v|--verbosity] [-- <RunSettings arguments>]

dotnet test [-h|--help]
```

# <a name="net-core-20tabnetcore20"></a>[.NET Core 2,0](#tab/netcore20)

```console
dotnet test [<PROJECT>] [-a|--test-adapter-path] [-c|--configuration] [--collect] [-d|--diag] [-f|--framework] [--filter]
    [-l|--logger] [--no-build] [--no-restore] [-o|--output] [-r|--results-directory] [-s|--settings] [-t|--list-tests] [-v|--verbosity]

dotnet test [-h|--help]
```

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1. x](#tab/netcore1x)

```console
dotnet test [<PROJECT>] [-a|--test-adapter-path] [-c|--configuration] [-d|--diag] [-f|--framework] [--filter] [-l|--logger] [--no-build] [-o|--output] [-s|--settings] [-t|--list-tests]  [-v|--verbosity]

dotnet test [-h|--help]
```

---

## <a name="description"></a>Açıklama

Komut `dotnet test` , belirli bir projedeki birim testlerini yürütmek için kullanılır. Komut `dotnet test` , bir proje için belirtilen Test Çalıştırıcısı konsol uygulamasını başlatır. Test Çalıştırıcısı, bir birim test çerçevesi (örneğin, MSTest, NUnit veya xUnit) için tanımlanan testleri yürütür ve her testin başarısını veya başarısızlığını bildirir. Tüm testler başarılı olursa, Test Çalıştırıcısı çıkış kodu olarak 0 döndürür; Aksi takdirde, herhangi bir test başarısız olursa, 1 döndürür. Test Çalıştırıcısı ve birim testi kitaplığı, NuGet paketleri olarak paketlenir ve proje için sıradan bağımlılıklar olarak geri yüklenir.

Test projeleri, aşağıdaki örnek proje dosyasında görüldüğü gibi `<PackageReference>` sıradan bir öğe kullanarak Test Çalıştırıcısı belirtir:

[!code-xml[XUnit Basic Template](../../../samples/snippets/csharp/xunit-test/xunit-test.csproj)]

## <a name="arguments"></a>Arguments

`PROJECT`

Test projesinin yolu. Belirtilmezse, varsayılan olarak geçerli dizin olur.

## <a name="options"></a>Seçenekler

# <a name="net-core-21tabnetcore21"></a>[.NET Core 2,1](#tab/netcore21)

`-a|--test-adapter-path <PATH_TO_ADAPTER>`

Test çalıştırmasında belirtilen yoldan özel test bağdaştırıcılarını kullanın.

`--blame`

Testleri sorumluyu modunda çalıştırır. Bu seçenek, test ana bilgisayarının kilitlenmesine neden olan sorunlu testleri yalıtmak için yararlıdır. Geçerli dizinde, kilitlenmeden önce yürütülen testlerin sırasını yakalayan *Sequence. xml* olarak bir çıktı dosyası oluşturur.

`-c|--configuration {Debug|Release}`

Yapı yapılandırmasını tanımlar. Varsayılan değer `Debug`, ancak projenizin yapılandırması bu varsayılan SDK ayarını geçersiz kılabilir.

`--collect <DATA_COLLECTOR_FRIENDLY_NAME>`

Test çalıştırması için veri toplayıcıyı etkinleştirilir. Daha fazla bilgi için bkz. [test çalıştırmasını izleme ve çözümleme](https://aka.ms/vstest-collect).

`-d|--diag <PATH_TO_DIAGNOSTICS_FILE>`

Test platformu için tanılama modunu sağlar ve belirtilen dosyaya tanılama iletileri yazar.

`-f|--framework <FRAMEWORK>`

Belirli bir [çerçeve](../../standard/frameworks.md)için test ikililerini arar.

`--filter <EXPRESSION>`

Geçerli projede verilen ifadeyi kullanarak testleri filtreler. Daha fazla bilgi için, [filtre seçeneği ayrıntıları](#filter-option-details) bölümüne bakın. Seçmeli birim testi filtrelemeyi kullanma hakkında daha fazla bilgi ve örnekler için bkz. [Seçmeli birim testlerini çalıştırma](../testing/selective-unit-tests.md).

`-h|--help`

Komut için kısa bir yardım yazdırır.

`-l|--logger <LoggerUri/FriendlyName>`

Test sonuçları için bir günlükçü belirtir.

`--no-build`

Test projesi çalıştırılmadan önce derlenmez. `--no-restore` Bayrak de örtülü olarak ayarlanır.

`--no-restore`

Komutu çalıştırılırken örtük geri yükleme yürütülmez.

`-o|--output <OUTPUT_DIRECTORY>`

Çalıştırılacak ikililerin bulunacağı dizin.

`-r|--results-directory <PATH>`

Test sonuçlarının yerleştirileceği dizin. Belirtilen dizin yoksa, oluşturulur.

`-s|--settings <SETTINGS_FILE>`

Testleri çalıştırmak için kullanılacak dosya.`.runsettings` [Birim testlerini bir `.runsettings` dosya kullanarak yapılandırın.](/visualstudio/test/configure-unit-tests-by-using-a-dot-runsettings-file?view=vs-2019)

`-t|--list-tests`

Geçerli projedeki tüm bulunan testlerin listesini listeleyin.

`-v|--verbosity <LEVEL>`

Komutun ayrıntı düzeyini ayarlar. İzin verilen değerler `q[uiet]` `m[inimal]` ,`n[ormal]`,, ve .`diag[nostic]` `d[etailed]`

`RunSettings arguments`

Test için RunSettings yapılandırması olarak geçirilen bağımsız değişkenler. Bağımsız değişkenler "- `[name]=[value]` -" sonra çift olarak belirtilir (--sonra boşluk bırakın). Birden çok `[name]=[value]` çifti ayırmak için bir boşluk kullanılır.

Örnek: `dotnet test -- MSTest.DeploymentEnabled=false MSTest.MapInconclusiveToFailed=True`

Runsettings hakkında daha fazla bilgi için bkz [. VSTest. Console. exe: RunSettings bağımsız değişkenleri](https://github.com/Microsoft/vstest-docs/blob/master/docs/RunSettingsArguments.md)geçiliyor.

# <a name="net-core-20tabnetcore20"></a>[.NET Core 2,0](#tab/netcore20)

`-a|--test-adapter-path <PATH_TO_ADAPTER>`

Test çalıştırmasında belirtilen yoldan özel test bağdaştırıcılarını kullanın.

`-c|--configuration {Debug|Release}`

Yapı yapılandırmasını tanımlar. Varsayılan değer `Debug`, ancak projenizin yapılandırması bu varsayılan SDK ayarını geçersiz kılabilir.

`--collect <DATA_COLLECTOR_FRIENDLY_NAME>`

Test çalıştırması için veri toplayıcıyı etkinleştirilir. Daha fazla bilgi için bkz. [test çalıştırmasını izleme ve çözümleme](https://aka.ms/vstest-collect).

`-d|--diag <PATH_TO_DIAGNOSTICS_FILE>`

Test platformu için tanılama modunu sağlar ve belirtilen dosyaya tanılama iletileri yazar.

`-f|--framework <FRAMEWORK>`

Belirli bir [çerçeve](../../standard/frameworks.md)için test ikililerini arar.

`--filter <EXPRESSION>`

Geçerli projede verilen ifadeyi kullanarak testleri filtreler. Daha fazla bilgi için, [filtre seçeneği ayrıntıları](#filter-option-details) bölümüne bakın. Seçmeli birim testi filtrelemeyi kullanma hakkında daha fazla bilgi ve örnekler için bkz. [Seçmeli birim testlerini çalıştırma](../testing/selective-unit-tests.md).

`-h|--help`

Komut için kısa bir yardım yazdırır.

`-l|--logger <LoggerUri/FriendlyName>`

Test sonuçları için bir günlükçü belirtir.

`--no-build`

Test projesi çalıştırılmadan önce derlenmez. `--no-restore` Bayrak de örtülü olarak ayarlanır.

`--no-restore`

Komutu çalıştırılırken örtük geri yükleme yürütülmez.

`-o|--output <OUTPUT_DIRECTORY>`

Çalıştırılacak ikililerin bulunacağı dizin.

`-r|--results-directory <PATH>`

Test sonuçlarının yerleştirileceği dizin. Belirtilen dizin yoksa, oluşturulur.

`-s|--settings <SETTINGS_FILE>`

Testleri çalıştırmak için kullanılacak dosya.`.runsettings` [Birim testlerini bir `.runsettings` dosya kullanarak yapılandırın.](/visualstudio/test/configure-unit-tests-by-using-a-dot-runsettings-file?view=vs-2019)

`-t|--list-tests`

Geçerli projedeki tüm bulunan testlerin listesini listeleyin.

`-v|--verbosity <LEVEL>`

Komutun ayrıntı düzeyini ayarlar. İzin verilen değerler `q[uiet]` `m[inimal]` ,`n[ormal]`,, ve .`diag[nostic]` `d[etailed]`

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1. x](#tab/netcore1x)

`-a|--test-adapter-path <PATH_TO_ADAPTER>`

Test çalıştırmasında belirtilen yoldan özel test bağdaştırıcılarını kullanın.

`-c|--configuration {Debug|Release}`

Yapı yapılandırmasını tanımlar. Varsayılan değer `Debug`, ancak projenizin yapılandırması bu varsayılan SDK ayarını geçersiz kılabilir.

`-d|--diag <PATH_TO_DIAGNOSTICS_FILE>`

Test platformu için tanılama modunu sağlar ve belirtilen dosyaya tanılama iletileri yazar.

`-f|--framework <FRAMEWORK>`

Belirli bir [çerçeve](../../standard/frameworks.md)için test ikililerini arar.

`--filter <EXPRESSION>`

Geçerli projede verilen ifadeyi kullanarak testleri filtreler. Daha fazla bilgi için, [filtre seçeneği ayrıntıları](#filter-option-details) bölümüne bakın. Seçmeli birim testi filtrelemeyi kullanma hakkında daha fazla bilgi ve örnekler için bkz. [Seçmeli birim testlerini çalıştırma](../testing/selective-unit-tests.md).

`-h|--help`

Komut için kısa bir yardım yazdırır.

`-l|--logger <LoggerUri/FriendlyName>`

Test sonuçları için bir günlükçü belirtir.

`--no-build`

Test projesi çalıştırılmadan önce derlenmez.

`-o|--output <OUTPUT_DIRECTORY>`

Çalıştırılacak ikililerin bulunacağı dizin.

`-s|--settings <SETTINGS_FILE>`

Testleri çalıştırmak için kullanılacak dosya.`.runsettings` [Birim testlerini bir `.runsettings` dosya kullanarak yapılandırın.](/visualstudio/test/configure-unit-tests-by-using-a-dot-runsettings-file?view=vs-2019)

`-t|--list-tests`

Geçerli projedeki tüm bulunan testlerin listesini listeleyin.

`-v|--verbosity <LEVEL>`

Komutun ayrıntı düzeyini ayarlar. İzin verilen değerler `q[uiet]` `m[inimal]` ,`n[ormal]`,, ve .`diag[nostic]` `d[etailed]`

---

## <a name="examples"></a>Örnekler

Projedeki testleri geçerli dizinde çalıştırın:

`dotnet test`

`test1` Projedeki testleri çalıştırın:

`dotnet test ~/projects/test1/test1.csproj`

Projedeki testleri geçerli dizinde çalıştırın ve TRX biçiminde bir test sonuçları dosyası oluşturun:

`dotnet test --logger trx`

## <a name="filter-option-details"></a>Filtre seçeneği ayrıntıları

`--filter <EXPRESSION>`

`<Expression>`biçimindedir `<property><operator><value>[|&<Expression>]`.

`<property>`, `Test Case`öğesinin bir özniteliğidir. Popüler birim testi çerçeveleri tarafından desteklenen özellikler aşağıda verilmiştir:

| Test çerçevesi | Desteklenen özellikler                                                                                      |
| -------------- | --------------------------------------------------------------------------------------------------------- |
| MSTest         | <ul><li>FullyQualifiedName</li><li>Ad</li><li>Sınıf</li><li>Priority</li><li>TestCategory</li></ul> |
| xUnit          | <ul><li>FullyQualifiedName</li><li>DisplayName</li><li>Lerdir</li></ul>                                   |

, `<operator>` Özelliği ve değeri arasındaki ilişkiyi açıklar:

| İşleç | İşlev        |
| :------: | --------------- |
| `=`      | Tam eşleşme     |
| `!=`     | Tam eşleşme yok |
| `~`      | İçerir        |

`<value>`bir dizedir. Tüm aramalar büyük/küçük harfe duyarlıdır.

Bir `<operator>` ifadesi, otomatik olarak `contains` on `FullyQualifiedName` özelliği olarak kabul edilir (örneğin, `dotnet test --filter xyz` ile `dotnet test --filter FullyQualifiedName~xyz`aynıdır).

İfadeler koşullu işleçlerle birleştirilebilecek:

| İşleç            | İşlev |
| ------------------- | -------- |
| <code>&#124;</code> | VEYA       |
| `&`                 | AND      |

Koşullu işleçler kullandığınızda (örneğin, `(Name~TestMethod1) | (Name~TestMethod2)`) ifadeleri parantez içine alabilirsiniz.

Seçmeli birim testi filtrelemeyi kullanma hakkında daha fazla bilgi ve örnekler için bkz. [Seçmeli birim testlerini çalıştırma](../testing/selective-unit-tests.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Çerçeveler ve hedefler](../../standard/frameworks.md)
- [.NET Core çalışma zamanı tanımlayıcısı (RID) kataloğu](../rid-catalog.md)
