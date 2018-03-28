---
title: DotNet test command - .NET Core CLI
description: Dotnet test komutu, belirli bir proje ile birim testleri yürütmek için kullanılır.
author: mairaw
ms.author: mairaw
ms.date: 08/14/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.workload:
- dotnetcore
ms.openlocfilehash: 6102281c4daf149f31e65ef8360831fe9e0ef4f6
ms.sourcegitcommit: 935d5267c44f9bce801468ef95f44572f1417e8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/28/2018
---
# <a name="dotnet-test"></a>DotNet test

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>Ad

`dotnet test` -.NET birim testleri çalıştırmak için kullanılan sürücü sınayın.

## <a name="synopsis"></a>Özet

# <a name="net-core-2xtabnetcore2x"></a>[.NET core 2.x](#tab/netcore2x)


```
dotnet test [<PROJECT>] [-a|--test-adapter-path] [-c|--configuration] [--collect] [-d|--diag] [-f|--framework] [--filter] [-l|--logger] [--no-build] [--no-restore] [-o|--output] [-r|--results-directory] [-s|--settings] [-t|--list-tests] [-v|--verbosity]
dotnet test [-h|--help]
```

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

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

Oluşturduğunuz test projesinin yolunu belirtir. Atlanırsa, geçerli dizin için varsayılanları.

## <a name="options"></a>Seçenekler

# <a name="net-core-2xtabnetcore2x"></a>[.NET core 2.x](#tab/netcore2x)

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

Verilen ifade kullanarak geçerli proje testlerinde kullanıma filtreler. Daha fazla bilgi için bkz: [filtre seçeneği ayrıntıları](#filter-option-details) bölümü. Ek bilgi ve seçmeli birim testi filtreleme kullanma hakkında örnekler için bkz: [seçmeli birim testlerini çalıştırma](../testing/selective-unit-tests.md).

`-h|--help`

Komutu için kısa bir Yardım yazdırır.

`-l|--logger <LoggerUri/FriendlyName>`

Test sonuçları için Günlükçü belirtir.

`--no-build`

Bunu çalıştırılmadan önce test projesi oluşmuyor.

`--no-restore`

Örtük bir geri yükleme komutu çalıştırırken gerçekleştirmez.

`-o|--output <OUTPUT_DIRECTORY>`

Çalıştırmak için ikili dosyaları bulmak dizin.

`-r|--results-directory <PATH>`

Test sonuçları yerleştirilmesi nerede bulunacağını dizin. Belirtilen dizin yoksa oluşturulur.

`-s|--settings <SETTINGS_FILE>`

Testleri çalıştırırken kullanılacak ayarları.

`-t|--list-tests`

Tüm geçerli projede bulunan testleri listeler.

`-v|--verbosity <LEVEL>`

Komutun ayrıntı düzeyi ayarlar. İzin verilen değerler `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, ve `diag[nostic]`.

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

`-a|--test-adapter-path <PATH_TO_ADAPTER>`

Belirtilen yol özel test bağdaştırıcılarından test çalışması kullanın.

`-c|--configuration {Debug|Release}`

Derleme yapılandırması tanımlar. Varsayılan değer `Debug`, ancak bu ayarın SDK projenizin yapılandırmasını geçersiz kılar.

`-d|--diag <PATH_TO_DIAGNOSTICS_FILE>`

Test platform ve yazma tanılama iletileri belirtilen dosya için tanılama modunu etkinleştirir.

`-f|--framework <FRAMEWORK>`

Belirli bir test ikili dosyaları arar [framework](../../standard/frameworks.md).

`--filter <EXPRESSION>`

Verilen ifade kullanarak geçerli proje testlerinde kullanıma filtreler. Daha fazla bilgi için bkz: [filtre seçeneği ayrıntıları](#filter-option-details) bölümü. Ek bilgi ve seçmeli birim testi filtreleme kullanma hakkında örnekler için bkz: [seçmeli birim testlerini çalıştırma](../testing/selective-unit-tests.md).

`-h|--help`

Komutu için kısa bir Yardım yazdırır.

`-l|--logger <LoggerUri/FriendlyName>`

Test sonuçları için Günlükçü belirtir.

`--no-build`

Bunu çalıştırılmadan önce test projesi oluşmuyor.

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
| :------------: | --------------------------------------------------------------------------------------------------------- |
| MSTest         | <ul><li>FullyQualifiedName</li><li>Ad</li><li>className</li><li>Öncelik</li><li>TestCategory</li></ul> |
| Xunit          | <ul><li>FullyQualifiedName</li><li>Görünen adı</li><li>Özellikleri</li></ul>                                   |

`<operator>` Özellik ve değer arasındaki ilişkiyi açıklar:

| İşleç | İşlev        |
| :------: | --------------- |
| `=`      | Tam eşleşme     |
| `!=`     | Değil tam eşleşme |
| `~`      | İçerir        |

`<value>` bir dizedir. Tüm arama büyük/küçük harfe duyarsızdır.

Bir ifade olmadan bir `<operator>` otomatik olarak kabul bir `contains` üzerinde `FullyQualifiedName` özelliği (örneğin, `dotnet test --filter xyz` aynı `dotnet test --filter FullyQualifiedName~xyz`).

İfadeler ile Koşullu işleçler katılabilir:

| İşleç | İşlev |
| :------: | :------: |
| <code>&#124;</code>      | VEYA       |
| `&`      | AND      |

İfadeler parantez içine Koşullu işleçler kullanırken içine aldığınız (örneğin, `(Name~TestMethod1) | (Name~TestMethod2)`).

Ek bilgi ve seçmeli birim testi filtreleme kullanma hakkında örnekler için bkz: [seçmeli birim testlerini çalıştırma](../testing/selective-unit-tests.md).

## <a name="see-also"></a>Ayrıca bkz.

 [Çerçeveler ve hedefler](../../standard/frameworks.md)  
 [.NET çekirdeği çalışma zamanı tanımlayıcı (RID) Kataloğu](../rid-catalog.md)
