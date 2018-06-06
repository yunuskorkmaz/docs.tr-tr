---
title: DotNet test command - .NET Core CLI
description: Dotnet test komutu, belirli bir proje ile birim testleri yürütmek için kullanılır.
author: mairaw
ms.author: mairaw
ms.date: 05/29/2018
ms.openlocfilehash: 8a10ac9175ee5fcf8649efbb07d8d382ac3afdc7
ms.sourcegitcommit: bbf70abe6b46073148f78cbf0619de6092b5800c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34696276"
---
# <a name="dotnet-test"></a>DotNet test

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>Ad

`dotnet test` -.NET birim testleri çalıştırmak için kullanılan sürücü sınayın.

## <a name="synopsis"></a>Özet

# <a name="net-core-21tabnetcore21"></a>[.NET core 2.1](#tab/netcore21)
```
dotnet test [<PROJECT>] [-a|--test-adapter-path] [--blame] [-c|--configuration] [--collect] [-d|--diag] [-f|--framework] [--filter]
    [-l|--logger] [--no-build] [--no-restore] [-o|--output] [-r|--results-directory] [-s|--settings] [-t|--list-tests] [-v|--verbosity]
dotnet test [-h|--help]
```
# <a name="net-core-20tabnetcore20"></a>[.NET core 2.0](#tab/netcore20)
```
dotnet test [<PROJECT>] [-a|--test-adapter-path] [-c|--configuration] [--collect] [-d|--diag] [-f|--framework] [--filter]
    [-l|--logger] [--no-build] [--no-restore] [-o|--output] [-r|--results-directory] [-s|--settings] [-t|--list-tests] [-v|--verbosity]
dotnet test [-h|--help]
```
# <a name="net-core-1xtabnetcore1x"></a>[.NET core 1.x](#tab/netcore1x)
```
dotnet test [<PROJECT>] [-a|--test-adapter-path] [-c|--configuration] [-d|--diag] [-f|--framework] [--filter] [-l|--logger] [--no-build] [-o|--output] [-s|--settings] [-t|--list-tests]  [-v|--verbosity]
dotnet test [-h|--help]
```
---

## <a name="description"></a>Açıklama

`dotnet test` Komutu, belirli bir proje ile birim testleri çalıştırmak için kullanılır. `dotnet test` Komutu proje için belirtilen test Çalıştırıcısı konsol uygulaması başlatır. Sınama Çalıştırıcısı birim test çerçevesi (örneğin, mstest'i, NUnit veya xUnit) için tanımlanan testleri yürütür ve başarı veya başarısızlık her sınamanın raporlar. Sınama Çalıştırıcısı ve birim testi kitaplığı NuGet paketleri olarak paketlenir ve proje için sıradan bağımlılıklar olarak geri yüklenir.

Test projeleri belirtin sıradan kullanarak test Çalıştırıcısı `<PackageReference>` aşağıdaki örnek proje dosyasında görülen öğe:

[!code-xml[XUnit Basic Template](../../../samples/snippets/csharp/xunit-test/xunit-test.csproj)]

## <a name="arguments"></a>Arguments

`PROJECT`

Oluşturduğunuz test projesinin yolu. Belirtilmezse, geçerli dizine varsayılan olur.

## <a name="options"></a>Seçenekler

# <a name="net-core-21tabnetcore21"></a>[.NET core 2.1](#tab/netcore21)

`-a|--test-adapter-path <PATH_TO_ADAPTER>`

Belirtilen yol özel test bağdaştırıcılarından test çalışması kullanın.

`--blame`

Testleri nedenlerle modunda çalıştırır. Bu seçenek test ana çökmesine neden sorunlu testleri yalıtmaya yardımcı olur. Bir çıktı dosyası geçerli dizinde oluşturur *Sequence.xml* kilitlenme önce testleri yürütme sırasını yakalar.

`-c|--configuration {Debug|Release}`

Derleme yapılandırması tanımlar. Varsayılan değer `Debug`, ancak bu ayarın SDK projenizin yapılandırmasını geçersiz kılar.

`--collect <DATA_COLLECTOR_FRIENDLY_NAME>`

Test çalışması için veri toplayıcı sağlar. Daha fazla bilgi için bkz: [İzleyici ve test çalışmasını çözümlemek](https://aka.ms/vstest-collect).

`-d|--diag <PATH_TO_DIAGNOSTICS_FILE>`

Test platform ve yazma tanılama iletileri belirtilen dosya için tanılama modunu etkinleştirir.

`-f|--framework <FRAMEWORK>`

Belirli bir test ikili dosyaları arar [framework](../../standard/frameworks.md).

`--filter <EXPRESSION>`

Verilen ifade kullanarak geçerli proje testlerinde kullanıma filtreler. Daha fazla bilgi için bkz: [filtre seçeneği ayrıntıları](#filter-option-details) bölümü. Daha fazla bilgi ve seçmeli birim testi filtreleme kullanma hakkında örnekler için bkz: [seçmeli birim testlerini çalıştırma](../testing/selective-unit-tests.md).

`-h|--help`

Komutu için kısa bir Yardım yazdırır.

`-l|--logger <LoggerUri/FriendlyName>`

Test sonuçları için Günlükçü belirtir.

`--no-build`

Oluşturduğunuz test projesinin çalıştırmadan önce derleme değil. Ayrıca örtük ayarlar `--no-restore` bayrağı.

`--no-restore`

Örtük bir geri yükleme komutu çalıştırırken yürütmez.

`-o|--output <OUTPUT_DIRECTORY>`

Çalıştırmak için ikili dosyaları bulmak dizin.

`-r|--results-directory <PATH>`

Test sonuçları yerleştirilmesi nerede bulunacağını dizin. Belirtilen dizin yoksa, oluşturulur.

`-s|--settings <SETTINGS_FILE>`

Testleri çalıştırırken kullanılacak ayarları.

`-t|--list-tests`

Tüm geçerli projede bulunan testleri listeler.

`-v|--verbosity <LEVEL>`

Komutun ayrıntı düzeyi ayarlar. İzin verilen değerler `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, ve `diag[nostic]`.

# <a name="net-core-20tabnetcore20"></a>[.NET core 2.0](#tab/netcore20)

`-a|--test-adapter-path <PATH_TO_ADAPTER>`

Belirtilen yol özel test bağdaştırıcılarından test çalışması kullanın.

`-c|--configuration {Debug|Release}`

Derleme yapılandırması tanımlar. Varsayılan değer `Debug`, ancak bu ayarın SDK projenizin yapılandırmasını geçersiz kılar.

`--collect <DATA_COLLECTOR_FRIENDLY_NAME>`

Test çalışması için veri toplayıcı sağlar. Daha fazla bilgi için bkz: [İzleyici ve test çalışmasını çözümlemek](https://aka.ms/vstest-collect).

`-d|--diag <PATH_TO_DIAGNOSTICS_FILE>`

Test platform ve yazma tanılama iletileri belirtilen dosya için tanılama modunu etkinleştirir.

`-f|--framework <FRAMEWORK>`

Belirli bir test ikili dosyaları arar [framework](../../standard/frameworks.md).

`--filter <EXPRESSION>`

Verilen ifade kullanarak geçerli proje testlerinde kullanıma filtreler. Daha fazla bilgi için bkz: [filtre seçeneği ayrıntıları](#filter-option-details) bölümü. Daha fazla bilgi ve seçmeli birim testi filtreleme kullanma hakkında örnekler için bkz: [seçmeli birim testlerini çalıştırma](../testing/selective-unit-tests.md).

`-h|--help`

Komutu için kısa bir Yardım yazdırır.

`-l|--logger <LoggerUri/FriendlyName>`

Test sonuçları için Günlükçü belirtir.

`--no-build`

Oluşturduğunuz test projesinin çalıştırmadan önce derleme değil. Ayrıca örtük ayarlar `--no-restore` bayrağı.

`--no-restore`

Örtük bir geri yükleme komutu çalıştırırken yürütmez.

`-o|--output <OUTPUT_DIRECTORY>`

Çalıştırmak için ikili dosyaları bulmak dizin.

`-r|--results-directory <PATH>`

Test sonuçları yerleştirilmesi nerede bulunacağını dizin. Belirtilen dizin yoksa, oluşturulur.

`-s|--settings <SETTINGS_FILE>`

Testleri çalıştırırken kullanılacak ayarları.

`-t|--list-tests`

Tüm geçerli projede bulunan testleri listeler.

`-v|--verbosity <LEVEL>`

Komutun ayrıntı düzeyi ayarlar. İzin verilen değerler `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, ve `diag[nostic]`.

# <a name="net-core-1xtabnetcore1x"></a>[.NET core 1.x](#tab/netcore1x)

`-a|--test-adapter-path <PATH_TO_ADAPTER>`

Belirtilen yol özel test bağdaştırıcılarından test çalışması kullanın.

`-c|--configuration {Debug|Release}`

Derleme yapılandırması tanımlar. Varsayılan değer `Debug`, ancak bu ayarın SDK projenizin yapılandırmasını geçersiz kılar.

`-d|--diag <PATH_TO_DIAGNOSTICS_FILE>`

Test platform ve yazma tanılama iletileri belirtilen dosya için tanılama modunu etkinleştirir.

`-f|--framework <FRAMEWORK>`

Belirli bir test ikili dosyaları arar [framework](../../standard/frameworks.md).

`--filter <EXPRESSION>`

Verilen ifade kullanarak geçerli proje testlerinde kullanıma filtreler. Daha fazla bilgi için bkz: [filtre seçeneği ayrıntıları](#filter-option-details) bölümü. Daha fazla bilgi ve seçmeli birim testi filtreleme kullanma hakkında örnekler için bkz: [seçmeli birim testlerini çalıştırma](../testing/selective-unit-tests.md).

`-h|--help`

Komutu için kısa bir Yardım yazdırır.

`-l|--logger <LoggerUri/FriendlyName>`

Test sonuçları için Günlükçü belirtir.

`--no-build`

Oluşturduğunuz test projesinin çalıştırmadan önce derleme değil.

`-o|--output <OUTPUT_DIRECTORY>`

Çalıştırmak için ikili dosyaları bulmak dizin.

`-s|--settings <SETTINGS_FILE>`

Testleri çalıştırırken kullanılacak ayarları.

`-t|--list-tests`

Tüm geçerli projede bulunan testleri listeler.

`-v|--verbosity <LEVEL>`

Komutun ayrıntı düzeyi ayarlar. İzin verilen değerler `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, ve `diag[nostic]`.

---

## <a name="examples"></a>Örnekler

Geçerli dizin projede Testleri Çalıştır:

`dotnet test`

Testleri çalıştırmak `test1` proje:

`dotnet test ~/projects/test1/test1.csproj`

## <a name="filter-option-details"></a>Filtre seçeneği ayrıntıları

`--filter <EXPRESSION>`

`<Expression>` biçimdedir `<property><operator><value>[|&<Expression>]`.

`<property>` bir özniteliği olan `Test Case`. Popüler birim test çerçevelerini tarafından desteklenen özellikler şunlardır:

| Test çerçevesi | Desteklenen özellikler                                                                                      |
| -------------- | --------------------------------------------------------------------------------------------------------- |
| MSTest         | <ul><li>Karşılık gelen fullyqualifiedname öğesi</li><li>Ad</li><li>className</li><li>Öncelik</li><li>TestCategory</li></ul> |
| xUnit          | <ul><li>Karşılık gelen fullyqualifiedname öğesi</li><li>Görünen adı</li><li>Özellikleri</li></ul>                                   |

`<operator>` Özellik ve değer arasındaki ilişkiyi açıklar:

| İşleç | İşlev        |
| :------: | --------------- |
| `=`      | Tam eşleşme     |
| `!=`     | Değil tam eşleşme |
| `~`      | İçerir        |

`<value>` bir dizedir. Tüm arama büyük/küçük harfe duyarsızdır.

Bir ifade olmadan bir `<operator>` otomatik olarak kabul bir `contains` üzerinde `FullyQualifiedName` özelliği (örneğin, `dotnet test --filter xyz` aynı `dotnet test --filter FullyQualifiedName~xyz`).

İfadeler ile Koşullu işleçler katılabilir:

| İşleç            | İşlev |
| ------------------- | -------- |
| <code>&#124;</code> | VEYA       |
| `&`                 | AND      |

İfadeler parantez içine Koşullu işleçler kullanırken içine aldığınız (örneğin, `(Name~TestMethod1) | (Name~TestMethod2)`).

Daha fazla bilgi ve seçmeli birim testi filtreleme kullanma hakkında örnekler için bkz: [seçmeli birim testlerini çalıştırma](../testing/selective-unit-tests.md).

## <a name="see-also"></a>Ayrıca bkz.

[Çerçeveler ve hedefler](../../standard/frameworks.md)  
[.NET çekirdeği çalışma zamanı tanımlayıcı (RID) Kataloğu](../rid-catalog.md)
