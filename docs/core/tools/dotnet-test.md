---
title: DotNet testi command - .NET Core CLI
description: Dotnet testi komut, belirli bir projede birim testleri yürütmek için kullanılır.
author: mairaw
ms.author: mairaw
ms.date: 05/29/2018
ms.openlocfilehash: 7946196b27489870da1c16b15cbf5f078ae89c61
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2018
ms.locfileid: "45518340"
---
# <a name="dotnet-test"></a>DotNet testi

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>Ad

`dotnet test` -.NET birim testleri yürütmek için kullanılan sürücü test edin.

## <a name="synopsis"></a>Özeti

# <a name="net-core-21tabnetcore21"></a>[.NET core 2.1](#tab/netcore21)

```console
dotnet test [<PROJECT>] [-a|--test-adapter-path] [--blame] [-c|--configuration] [--collect] [-d|--diag] [-f|--framework] [--filter]
    [-l|--logger] [--no-build] [--no-restore] [-o|--output] [-r|--results-directory] [-s|--settings] [-t|--list-tests] [-v|--verbosity]
dotnet test [-h|--help]
```

# <a name="net-core-20tabnetcore20"></a>[.NET core 2.0](#tab/netcore20)

```console
dotnet test [<PROJECT>] [-a|--test-adapter-path] [-c|--configuration] [--collect] [-d|--diag] [-f|--framework] [--filter]
    [-l|--logger] [--no-build] [--no-restore] [-o|--output] [-r|--results-directory] [-s|--settings] [-t|--list-tests] [-v|--verbosity]
dotnet test [-h|--help]
```

# <a name="net-core-1xtabnetcore1x"></a>[.NET core 1.x](#tab/netcore1x)

```console
dotnet test [<PROJECT>] [-a|--test-adapter-path] [-c|--configuration] [-d|--diag] [-f|--framework] [--filter] [-l|--logger] [--no-build] [-o|--output] [-s|--settings] [-t|--list-tests]  [-v|--verbosity]
dotnet test [-h|--help]
```

---

## <a name="description"></a>Açıklama

`dotnet test` Komutu, belirli bir projede birim testleri yürütmek için kullanılır. `dotnet test` Test Çalıştırıcısı konsol uygulaması projesi için belirtilen komutu çalıştırır. Test Çalıştırıcısı, birim test çerçevesi (örneğin, MSTest, NUnit veya xUnit) için tanımlanan testleri yürütür ve başarılı veya başarısız her test raporlar. Test Çalıştırıcısı ve birim testi kitaplığı NuGet paketleri olarak paketlenir ve proje için sıradan bağımlılık olarak geri yüklenir.

Test projeleri belirtmek sıradan kullanarak test Çalıştırıcısı `<PackageReference>` aşağıdaki örnek proje dosyasında görülen öğe:

[!code-xml[XUnit Basic Template](../../../samples/snippets/csharp/xunit-test/xunit-test.csproj)]

## <a name="arguments"></a>Arguments

`PROJECT`

Test projesinin yolu. Belirtilmezse, geçerli dizin için varsayılan olarak.

## <a name="options"></a>Seçenekler

# <a name="net-core-21tabnetcore21"></a>[.NET core 2.1](#tab/netcore21)

`-a|--test-adapter-path <PATH_TO_ADAPTER>`

Belirtilen yoldan özel test bağdaştırıcılarını test çalıştırmasında kullanın.

`--blame`

Testleri sorumluyu modunda çalıştırır. Bu seçenek, sorunlu testleri test ana bilgisayarı kilitlenmesine neden olan sorunları ayırmanıza yardımcı olur. Bir çıkış dosyası geçerli dizinde oluşturur *Sequence.xml* , kilitlenme önce testler yürütme sırası yakalar.

`-c|--configuration {Debug|Release}`

Derleme yapılandırmasını tanımlar. Varsayılan değer `Debug`, ancak bu ayarın SDK proje yapılandırmasını geçersiz kılar.

`--collect <DATA_COLLECTOR_FRIENDLY_NAME>`

Test çalıştırması için veri toplayıcısını etkinleştirir. Daha fazla bilgi için [izleme ve test çalışmasını çözümlemek](https://aka.ms/vstest-collect).

`-d|--diag <PATH_TO_DIAGNOSTICS_FILE>`

Test platformu ve yazma tanılama iletileri için belirtilen dosyaya tanılama modunu etkinleştirir.

`-f|--framework <FRAMEWORK>`

Belirli bir test ikililerinin arar [framework](../../standard/frameworks.md).

`--filter <EXPRESSION>`

Testleri kullanarak belirtilen ifade geçerli projede filtreler. Daha fazla bilgi için [filtre seçeneği ayrıntıları](#filter-option-details) bölümü. Daha fazla bilgi ve seçmeli birim testi filtreleme kullanma hakkında daha fazla örnek için bkz. [seçmeli birim testleri çalıştırma](../testing/selective-unit-tests.md).

`-h|--help`

Komut için kısa bir Yardım yazdırır.

`-l|--logger <LoggerUri/FriendlyName>`

Test sonuçları için bir Günlükçü belirtir.

`--no-build`

Test projesi çalıştırmadan önce derleme değil. Ayrıca örtülü ayarlar `--no-restore` bayrağı.

`--no-restore`

Örtük bir geri yükleme komutu çalıştırırken yürütülmez.

`-o|--output <OUTPUT_DIRECTORY>`

Çalıştırmak için ikili dosyaları bulmak dizin.

`-r|--results-directory <PATH>`

Test sonuçlarını yerleştirilmesi nerede bulunacağını dizin. Belirtilen dizin yoksa, oluşturulur.

`-s|--settings <SETTINGS_FILE>`

Testleri çalıştırırken kullanılacak ayarlar.

`-t|--list-tests`

Tüm geçerli projede bulunan testleri listeler.

`-v|--verbosity <LEVEL>`

Komutun ayrıntı düzeyini ayarlar. İzin verilen değerler `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, ve `diag[nostic]`.

# <a name="net-core-20tabnetcore20"></a>[.NET core 2.0](#tab/netcore20)

`-a|--test-adapter-path <PATH_TO_ADAPTER>`

Belirtilen yoldan özel test bağdaştırıcılarını test çalıştırmasında kullanın.

`-c|--configuration {Debug|Release}`

Derleme yapılandırmasını tanımlar. Varsayılan değer `Debug`, ancak bu ayarın SDK proje yapılandırmasını geçersiz kılar.

`--collect <DATA_COLLECTOR_FRIENDLY_NAME>`

Test çalıştırması için veri toplayıcısını etkinleştirir. Daha fazla bilgi için [izleme ve test çalışmasını çözümlemek](https://aka.ms/vstest-collect).

`-d|--diag <PATH_TO_DIAGNOSTICS_FILE>`

Test platformu ve yazma tanılama iletileri için belirtilen dosyaya tanılama modunu etkinleştirir.

`-f|--framework <FRAMEWORK>`

Belirli bir test ikililerinin arar [framework](../../standard/frameworks.md).

`--filter <EXPRESSION>`

Testleri kullanarak belirtilen ifade geçerli projede filtreler. Daha fazla bilgi için [filtre seçeneği ayrıntıları](#filter-option-details) bölümü. Daha fazla bilgi ve seçmeli birim testi filtreleme kullanma hakkında daha fazla örnek için bkz. [seçmeli birim testleri çalıştırma](../testing/selective-unit-tests.md).

`-h|--help`

Komut için kısa bir Yardım yazdırır.

`-l|--logger <LoggerUri/FriendlyName>`

Test sonuçları için bir Günlükçü belirtir.

`--no-build`

Test projesi çalıştırmadan önce derleme değil. Ayrıca örtülü ayarlar `--no-restore` bayrağı.

`--no-restore`

Örtük bir geri yükleme komutu çalıştırırken yürütülmez.

`-o|--output <OUTPUT_DIRECTORY>`

Çalıştırmak için ikili dosyaları bulmak dizin.

`-r|--results-directory <PATH>`

Test sonuçlarını yerleştirilmesi nerede bulunacağını dizin. Belirtilen dizin yoksa, oluşturulur.

`-s|--settings <SETTINGS_FILE>`

Testleri çalıştırırken kullanılacak ayarlar.

`-t|--list-tests`

Tüm geçerli projede bulunan testleri listeler.

`-v|--verbosity <LEVEL>`

Komutun ayrıntı düzeyini ayarlar. İzin verilen değerler `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, ve `diag[nostic]`.

# <a name="net-core-1xtabnetcore1x"></a>[.NET core 1.x](#tab/netcore1x)

`-a|--test-adapter-path <PATH_TO_ADAPTER>`

Belirtilen yoldan özel test bağdaştırıcılarını test çalıştırmasında kullanın.

`-c|--configuration {Debug|Release}`

Derleme yapılandırmasını tanımlar. Varsayılan değer `Debug`, ancak bu ayarın SDK proje yapılandırmasını geçersiz kılar.

`-d|--diag <PATH_TO_DIAGNOSTICS_FILE>`

Test platformu ve yazma tanılama iletileri için belirtilen dosyaya tanılama modunu etkinleştirir.

`-f|--framework <FRAMEWORK>`

Belirli bir test ikililerinin arar [framework](../../standard/frameworks.md).

`--filter <EXPRESSION>`

Testleri kullanarak belirtilen ifade geçerli projede filtreler. Daha fazla bilgi için [filtre seçeneği ayrıntıları](#filter-option-details) bölümü. Daha fazla bilgi ve seçmeli birim testi filtreleme kullanma hakkında daha fazla örnek için bkz. [seçmeli birim testleri çalıştırma](../testing/selective-unit-tests.md).

`-h|--help`

Komut için kısa bir Yardım yazdırır.

`-l|--logger <LoggerUri/FriendlyName>`

Test sonuçları için bir Günlükçü belirtir.

`--no-build`

Test projesi çalıştırmadan önce derleme değil.

`-o|--output <OUTPUT_DIRECTORY>`

Çalıştırmak için ikili dosyaları bulmak dizin.

`-s|--settings <SETTINGS_FILE>`

Testleri çalıştırırken kullanılacak ayarlar.

`-t|--list-tests`

Tüm geçerli projede bulunan testleri listeler.

`-v|--verbosity <LEVEL>`

Komutun ayrıntı düzeyini ayarlar. İzin verilen değerler `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, ve `diag[nostic]`.

---

## <a name="examples"></a>Örnekler

Geçerli dizindeki projedeki Testleri Çalıştır:

`dotnet test`

Testleri çalıştırmak `test1` proje:

`dotnet test ~/projects/test1/test1.csproj`

Geçerli dizindeki projedeki testleri çalıştırmak ve trx biçiminde bir test sonuçları dosyası oluşturun:

`dotnet test --logger:trx`

## <a name="filter-option-details"></a>Filtre seçeneği ayrıntıları

`--filter <EXPRESSION>`

`<Expression>` şu biçimdedir `<property><operator><value>[|&<Expression>]`.

`<property>` bir özniteliğidir `Test Case`. Popüler birim testi çerçevelerini tarafından desteklenen özellikler şunlardır:

| Test çerçevesi | Desteklenen özellikler                                                                                      |
| -------------- | --------------------------------------------------------------------------------------------------------- |
| MSTest         | <ul><li>Karşılık gelen fullyqualifiedname öğesi</li><li>Ad</li><li>className</li><li>Öncelik</li><li>TestCategory</li></ul> |
| xUnit          | <ul><li>Karşılık gelen fullyqualifiedname öğesi</li><li>displayName</li><li>Nitelikler</li></ul>                                   |

`<operator>` Özellik ve değer arasındaki ilişkiyi açıklar:

| İşleç | İşlev        |
| :------: | --------------- |
| `=`      | Tam eşleşme     |
| `!=`     | Değil tam eşleşme |
| `~`      | İçerir        |

`<value>` bir dizedir. Tüm aramalar büyük/küçük harfe duyarsızdır.

Bir ifade olmadan bir `<operator>` otomatik olarak kabul edilir bir `contains` üzerinde `FullyQualifiedName` özelliği (örneğin, `dotnet test --filter xyz` aynı `dotnet test --filter FullyQualifiedName~xyz`).

Koşullu işleçler ile ifadeler katılabilir:

| İşleç            | İşlev |
| ------------------- | -------- |
| <code>&#124;</code> | VEYA       |
| `&`                 | AND      |

İfadeleri parantez içinde Koşullu işleçler kullanırken içine aldığınız (örneğin, `(Name~TestMethod1) | (Name~TestMethod2)`).

Daha fazla bilgi ve seçmeli birim testi filtreleme kullanma hakkında daha fazla örnek için bkz. [seçmeli birim testleri çalıştırma](../testing/selective-unit-tests.md).

## <a name="see-also"></a>Ayrıca bkz.

* [Çerçeveler ve hedefler](../../standard/frameworks.md)  
* [.NET core çalışma zamanı tanımlayıcı (RID) Kataloğu](../rid-catalog.md)
