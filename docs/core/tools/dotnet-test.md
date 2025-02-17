---
title: DotNet test komutu
description: DotNet test komutu, belirli bir projedeki birim testlerini yürütmek için kullanılır.
ms.date: 04/29/2020
ms.openlocfilehash: 2671cbe6f610cfa8aa98e63e67f3240a1650cd6b
ms.sourcegitcommit: 2b878d7011306b215dbf3d5dc9c1e78355a6dcd5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/25/2021
ms.locfileid: "98757882"
---
# <a name="dotnet-test"></a>dotnet test

**Bu makale şu şekilde geçerlidir:** ✔️ .net Core 2,1 SDK ve sonraki sürümleri

## <a name="name"></a>Name

`dotnet test` -Birim testlerini yürütmek için kullanılan .NET test sürücüsü.

## <a name="synopsis"></a>Özeti

```dotnetcli
dotnet test [<PROJECT> | <SOLUTION> | <DIRECTORY> | <DLL>]
    [-a|--test-adapter-path <ADAPTER_PATH>] [--blame] [--blame-crash]
    [--blame-crash-dump-type <DUMP_TYPE>] [--blame-crash-collect-always]
    [--blame-hang] [--blame-hang-dump-type <DUMP_TYPE>]
    [--blame-hang-timeout <TIMESPAN>]
    [-c|--configuration <CONFIGURATION>]
    [--collect <DATA_COLLECTOR_NAME>]
    [-d|--diag <LOG_FILE>] [-f|--framework <FRAMEWORK>]
    [--filter <EXPRESSION>] [--interactive]
    [-l|--logger <LOGGER>] [--no-build]
    [--nologo] [--no-restore] [-o|--output <OUTPUT_DIRECTORY>]
    [-r|--results-directory <RESULTS_DIR>] [--runtime <RUNTIME_IDENTIFIER>]
    [-s|--settings <SETTINGS_FILE>] [-t|--list-tests]
    [-v|--verbosity <LEVEL>] [[--] <RunSettings arguments>]

dotnet test -h|--help
```

## <a name="description"></a>Açıklama

`dotnet test`Komut, belirli bir çözümde birim testlerini yürütmek için kullanılır. `dotnet test`Komut çözümü oluşturur ve çözümdeki her test projesi için bir test ana bilgisayarı uygulaması çalıştırır. Test ana bilgisayarı, test çerçevesini (örneğin, MSTest, NUnit veya xUnit) kullanarak belirtilen projedeki testleri yürütür ve her testin başarısını veya başarısızlığını bildirir. Tüm testler başarılı olursa, Test Çalıştırıcısı çıkış kodu olarak 0 döndürür; Aksi takdirde, herhangi bir test başarısız olursa, 1 döndürür.

Çok hedefli projeler için testler hedeflenen her çerçeve için çalıştırılır. Test Konağı ve birim testi çerçevesi, NuGet paketleri olarak paketlenir ve proje için sıradan bağımlılıklar olarak geri yüklenir.

Test projeleri, `<PackageReference>` Aşağıdaki örnek proje dosyasında görüldüğü gibi sıradan bir öğe kullanarak Test Çalıştırıcısı belirtir:

[!code-xml[XUnit Basic Template](../../../samples/snippets/csharp/xunit-test/xunit-test.csproj)]

`Microsoft.NET.Test.Sdk`Test Konağı nerede, `xunit` Test çerçevesidir. Ve `xunit.runner.visualstudio` , xUnit Framework 'ün test ana bilgisayarı ile çalışmasına izin veren bir test bağdaştırıcısıdır.

### <a name="implicit-restore"></a>Örtük geri yükleme

[!INCLUDE[dotnet restore note](~/includes/dotnet-restore-note.md)]

## <a name="arguments"></a>Bağımsız değişkenler

- **`PROJECT | SOLUTION | DIRECTORY | DLL`**

  - Test projesinin yolu.
  - Çözümün yolu.
  - Proje veya çözüm içeren bir dizinin yolu.
  - Test projesi *. dll* dosyasının yolu.

  Belirtilmemişse, geçerli dizinde bir proje veya çözüm arar.

## <a name="options"></a>Seçenekler

- **`-a|--test-adapter-path <ADAPTER_PATH>`**

  Ek test bağdaştırıcıları için aranacak bir dizin yolu. Yalnızca soneki olan *. dll* dosyaları `.TestAdapter.dll` denetlenir. Belirtilmemişse, test *. dll* dizininde arama yapılır.

- **`--blame`**

  Testleri sorumluyu modunda çalıştırır. Bu seçenek, test ana bilgisayarının kilitlenmesine neden olan sorunlu testleri yalıtmak için yararlıdır. Kilitlenme algılandığında, `TestResults/<Guid>/<Guid>_Sequence.xml` çökmeden önce çalıştırılan testlerin sırasını yakalayan bir sıra dosyası oluşturur.

- **`--blame-crash`** (.NET 5,0 Preview SDK sürümünden itibaren kullanılabilir)

  Testleri sorumluyu modunda çalıştırır ve test ana bilgisayarı beklenmedik bir şekilde çıktığında kilitlenme dökümünü toplar. Bu seçenek, kullanılan .NET sürümüne, hata türüne ve işletim sistemine bağlıdır.
  
  Yönetilen koddaki özel durumlar için, .NET 5,0 ve sonraki sürümlerinde otomatik olarak bir döküm alınacaktır. Testhost veya .NET 5,0 ' de çalıştırılan ve kilitlenen herhangi bir alt işlem için bir döküm oluşturur. Yerel koddaki kilitlenmeler, döküm oluşturmaz. Bu seçenek Windows, macOS ve Linux 'ta kullanılabilir.
  
  Yerel koddaki kilitlenme dökümleri veya .NET Core 3,1 veya önceki sürümleri kullanıldığında, yalnızca Windows üzerinde ProcDump kullanılarak toplanabilir. *procdump.exe* ve *procdump64.exe* IÇEREN bir dizin, yol veya PROCDUMP_PATH ortam değişkeninde olmalıdır. [Araçları indirin](/sysinternals/downloads/procdump). Şunu gösterir `--blame` .
  
  .NET 5,0 veya üzeri sürümlerde çalışan bir yerel uygulamadan kilitlenme dökümü toplamak için, ortam değişkeni olarak ayarlanarak ProcDump kullanımı zorunlu olabilir `VSTEST_DUMP_FORCEPROCDUMP` `1` .

- **`--blame-crash-dump-type <DUMP_TYPE>`** (.NET 5,0 Preview SDK sürümünden itibaren kullanılabilir)

  Toplanacak kilitlenme bilgi dökümü türü. Şunu gösterir `--blame-crash` .

- **`--blame-crash-collect-always`** (.NET 5,0 Preview SDK sürümünden itibaren kullanılabilir)

  Beklenen ve beklenmeyen test ana bilgisayarı çıkışında oluşan kilitlenme dökümünü toplar.

- **`--blame-hang`** (.NET 5,0 Preview SDK sürümünden itibaren kullanılabilir)

  Testleri sorumluyu modunda çalıştırın ve bir test verilen zaman aşımını aştığında bir askıda kalma dökümü toplar.

- **`--blame-hang-dump-type <DUMP_TYPE>`** (.NET 5,0 Preview SDK sürümünden itibaren kullanılabilir)

  Toplanacak kilitlenme bilgi dökümü türü. `full`, `mini` Veya olmalıdır `none` . `none`Belirtildiğinde, test ana bilgisayarı zaman aşımında sonlandırılır, ancak hiçbir döküm toplanmaz. Şunu gösterir `--blame-hang` .

- **`--blame-hang-timeout <TIMESPAN>`** (.NET 5,0 Preview SDK sürümünden itibaren kullanılabilir)

  Test başına zaman aşımı, bir askıda kalma dökümü tetiklendikten sonra test ana bilgisayarı işlemi ve tüm alt işlemleri dökülür ve sonlandırılmalıdır. Zaman aşımı değeri aşağıdaki biçimlerden birinde belirtilir:
  
  - 1.5 h, 1,5 saat, 1,5 saat
  - 90 milyon, 90min, 90 dakika, 90 dakika
  - 5400s, 5400sn, 5400second, 5400saniye
  - 5400000ms, 5400000mil, 5400000milisaniyelik, 5400000milliseconds

  Hiçbir birim kullanılmazsa (örneğin, 5400000), değerin milisaniye cinsinden olduğu varsayılır. Veri odaklı testlerle birlikte kullanıldığında, zaman aşımı davranışı kullanılan test bağdaştırıcısına bağlıdır. XUnit ve NUnit için zaman aşımı her test çalışmasının ardından yenilenir. MSTest için zaman aşımı tüm test çalışmaları için kullanılır. Bu seçenek netcoreapp 2.1 ve üzeri sürümlerde, netcoreapp 3.1 ve üzeri ile Linux 'ta ve net 5.0 veya üzeri ile macOS 'ta desteklenir. Ve anlamına gelir `--blame` `--blame-hang` .

- **`-c|--configuration <CONFIGURATION>`**

  Yapı yapılandırmasını tanımlar. Varsayılan değer `Debug` , ancak projenizin yapılandırması bu varsayılan SDK ayarını geçersiz kılabilir.

- **`--collect <DATA_COLLECTOR_NAME>`**

  Test çalıştırması için veri toplayıcıyı etkinleştirilir. Daha fazla bilgi için bkz. [test çalıştırmasını izleme ve çözümleme](https://aka.ms/vstest-collect).
  
  .NET Core tarafından desteklenen herhangi bir platformda kod kapsamı toplamak için, [Kapak](https://github.com/coverlet-coverage/coverlet/blob/master/README.md) ' i yükleyip `--collect:"XPlat Code Coverage"` seçeneğini kullanın.

  Windows üzerinde, seçeneğini kullanarak kod kapsamını toplayabilirsiniz `--collect "Code Coverage"` . Bu seçenek, Visual Studio 2019 Enterprise 'ta açılabilen bir *. Coverage* dosyası üretir. Daha fazla bilgi için bkz. [kod kapsamını kullanma](/visualstudio/test/using-code-coverage-to-determine-how-much-code-is-being-tested) ve [kod kapsamı analizini özelleştirme](/visualstudio/test/customizing-code-coverage-analysis).

- **`-d|--diag <LOG_FILE>`**

  Test platformu için tanılama modunu sağlar ve belirtilen dosyaya ve bunun yanındaki dosyalara tanılama iletileri yazar. İletileri günlüğe kaydeden işlem, `*.host_<date>.txt` Test ana bilgisayar günlüğü için ve veri toplayıcı günlüğü için oluşturulan dosyaları belirler `*.datacollector_<date>.txt` .

- **`-f|--framework <FRAMEWORK>`**

  `dotnet`Test ikilileri için veya .NET Framework test ana bilgisayarının kullanımını zorlar. Bu seçenek yalnızca kullanılacak ana bilgisayar türünü belirler. Kullanılacak gerçek Framework sürümü, Test projesindeki *runtimeconfig.js* tarafından belirlenir. Belirtilmediğinde, [TargetFramework derleme özniteliği](/dotnet/api/system.runtime.versioning.targetframeworkattribute) konak türünü belirlemekte kullanılır. Bu öznitelik *. dll*' den çıkarılır .NET Framework ana bilgisayar kullanılır.

- **`--filter <EXPRESSION>`**

  Geçerli projede verilen ifadeyi kullanarak testleri filtreler. Daha fazla bilgi için, [filtre seçeneği ayrıntıları](#filter-option-details) bölümüne bakın. Seçmeli birim testi filtrelemeyi kullanma hakkında daha fazla bilgi ve örnekler için bkz. [Seçmeli birim testlerini çalıştırma](../testing/selective-unit-tests.md).

- **`-h|--help`**

  Komut için kısa bir yardım yazdırır.

- **`--interactive`**

  Komutun Kullanıcı girişini veya eylemini durdurmasına ve beklemesine izin verir. Örneğin, kimlik doğrulamasını tamamlamaya yönelik. .NET Core 3,0 SDK 'dan beri kullanılabilir.

- **`-l|--logger <LOGGER>`**

  Test sonuçları için bir günlükçü belirtir. MSBuild 'in aksine, DotNet testi kısaltmalar kabul etmez: `-l "console;v=d"` kullanım yerine `-l "console;verbosity=detailed"` . Birden çok günlüğü etkinleştirmek için parametreyi birden çok kez belirtin.

- **`--no-build`**

  Test projesi çalıştırılmadan önce derlenmez. Ayrıca,-bayrağını örtülü olarak ayarlar `--no-restore` .

- **`--nologo`**

  Testleri, Microsoft TestPlatform başlığını görüntülemeden çalıştırın. .NET Core 3,0 SDK 'dan beri kullanılabilir.

- **`--no-restore`**

  Komutu çalıştırılırken örtük geri yükleme yürütülmez.

- **`-o|--output <OUTPUT_DIRECTORY>`**

  Çalıştırılacak ikililerin bulunacağı dizin. Belirtilmemişse, varsayılan yol olur `./bin/<configuration>/<framework>/` .  Birden çok hedef çerçevesi olan projeler için ( `TargetFrameworks` özelliği aracılığıyla), `--framework` Bu seçeneği ne zaman belirttiğinizde de tanımlamanız gerekir. `dotnet test` her zaman çıkış dizininden testleri çalıştırır. <xref:System.AppDomain.BaseDirectory%2A?displayProperty=nameWithType>' I, çıkış dizininde test varlıklarını kullanmak için kullanabilirsiniz.

- **`-r|--results-directory <RESULTS_DIR>`**

  Test sonuçlarının yerleştirileceği dizin. Belirtilen dizin yoksa, oluşturulur. Varsayılan değer `TestResults` Proje dosyasını içeren dizindir.

- **`--runtime <RUNTIME_IDENTIFIER>`**

  Sınanacak hedef çalışma zamanı.

- **`-s|--settings <SETTINGS_FILE>`**

  `.runsettings`Testleri çalıştırmak için kullanılacak dosya. `TargetPlatform`Öğesinin (x86 | x64) için bir etkisi yoktur `dotnet test` . X86 'yı hedefleyen testleri çalıştırmak için .NET Core 'un x86 sürümünü yükler. Yoldaki *dotnet.exe* bit genişliği, testleri çalıştırmak için kullanılacak şeydir. Daha fazla bilgi için aşağıdaki kaynaklara bakın:

  - [Birim testlerini bir dosya kullanarak yapılandırın `.runsettings` .](/visualstudio/test/configure-unit-tests-by-using-a-dot-runsettings-file)
  - [Test çalıştırması yapılandırma](https://github.com/Microsoft/vstest-docs/blob/master/docs/configure.md)

- **`-t|--list-tests`**

  Testleri çalıştırmak yerine bulunan testleri listeleyin.

- **`-v|--verbosity <LEVEL>`**

  Komutun ayrıntı düzeyini ayarlar. İzin verilen değerler,,, `q[uiet]` `m[inimal]` `n[ormal]` `d[etailed]` ve `diag[nostic]` . Varsayılan değer: `minimal`. Daha fazla bilgi için bkz. <xref:Microsoft.Build.Framework.LoggerVerbosity>.

- **`RunSettings`** değişkenlerinden

 Satır içi, `RunSettings` "--" sonra komut satırındaki son bağımsız değişkenler olarak geçirilir (--sonra boşluğu aklınızda bırakın). Satır içi `RunSettings` çiftler olarak belirtilir `[name]=[value]` . Birden çok çifti ayırmak için bir boşluk kullanılır `[name]=[value]` .

  Örnek: `dotnet test -- MSTest.DeploymentEnabled=false MSTest.MapInconclusiveToFailed=True`

  Daha fazla bilgi için bkz. [komut satırı aracılığıyla RunSettings bağımsız değişkenlerini geçirme](https://github.com/Microsoft/vstest-docs/blob/master/docs/RunSettingsArguments.md).

## <a name="examples"></a>Örnekler

- Projedeki testleri geçerli dizinde çalıştırın:

  ```dotnetcli
  dotnet test
  ```

- Projedeki testleri çalıştırın `test1` :

  ```dotnetcli
  dotnet test ~/projects/test1/test1.csproj
  ```

- Projedeki testleri geçerli dizinde çalıştırın ve TRX biçiminde bir test sonuçları dosyası oluşturun:

  ```dotnetcli
  dotnet test --logger trx
  ```

- Projedeki testleri geçerli dizinde çalıştırın ve bir kod kapsamı dosyası oluşturun ( [Kapak Let](https://github.com/coverlet-coverage/coverlet/blob/master/Documentation/VSTestIntegration.md) toplayıcılarını yükledikten sonra):

  ```dotnetcli
  dotnet test --collect:"XPlat Code Coverage"
  ```

- Projedeki testleri geçerli dizinde çalıştırın ve bir kod kapsamı dosyası oluşturun (yalnızca Windows):

  ```dotnetcli
  dotnet test --collect "Code Coverage"
  ```

- Projedeki testleri geçerli dizinde çalıştırın ve konsolun ayrıntılı ayrıntı düzeyi ile günlüğe kaydedin:

  ```dotnetcli
  dotnet test --logger "console;verbosity=detailed"
  ```

- Projedeki testleri geçerli dizinde çalıştırın ve test ana bilgisayarı kilitlenirse sürmekte olan testleri rapor edin:

  ```dotnetcli
  dotnet test --blame
  ```

## <a name="filter-option-details"></a>Filtre seçeneği ayrıntıları

`--filter <EXPRESSION>`

`<Expression>` biçimindedir `<property><operator><value>[|&<Expression>]` .

`<property>` , öğesinin bir özniteliğidir `Test Case` . Popüler birim testi çerçeveleri tarafından desteklenen özellikler aşağıda verilmiştir:

| Test çerçevesi | Desteklenen özellikler                                                                                      |
| -------------- | --------------------------------------------------------------------------------------------------------- |
| MSTest         | <ul><li>FullyQualifiedName</li><li>Name</li><li>Sınıf</li><li>Öncelik</li><li>TestCategory</li></ul> |
| xUnit          | <ul><li>FullyQualifiedName</li><li>DisplayName</li><li>Kategori</li></ul>                                 |
| NUnit          | <ul><li>FullyQualifiedName</li><li>Name</li><li>TestCategory</li><li>Öncelik</li></ul>                                   |

, `<operator>` Özelliği ve değeri arasındaki ilişkiyi açıklar:

| Operatör | İşlev        |
| :------: | --------------- |
| `=`      | Tam eşleşme     |
| `!=`     | Tam eşleşme yok |
| `~`      | Contains        |
| `!~`     | İçermez    |

`<value>` bir dizedir. Tüm aramalar büyük/küçük harfe duyarlıdır.

Bir ifadesi `<operator>` , otomatik olarak on özelliği olarak kabul `contains` edilir `FullyQualifiedName` (örneğin, `dotnet test --filter xyz` ile aynıdır `dotnet test --filter FullyQualifiedName~xyz` ).

İfadeler koşullu işleçlerle birleştirilebilecek:

| Operatör            | İşlev |
| ------------------- | -------- |
| <code>&#124;</code> | VEYA       |
| `&`                 | AND      |

Koşullu işleçler kullandığınızda (örneğin,) ifadeleri parantez içine alabilirsiniz `(Name~TestMethod1) | (Name~TestMethod2)` .

Seçmeli birim testi filtrelemeyi kullanma hakkında daha fazla bilgi ve örnekler için bkz. [Seçmeli birim testlerini çalıştırma](../testing/selective-unit-tests.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Çerçeveler ve hedefler](../../standard/frameworks.md)
- [.NET çalışma zamanı tanımlayıcısı (RID) kataloğu](../rid-catalog.md)
- [Komut satırı aracılığıyla runsettings bağımsız değişkenlerini geçirme](https://github.com/Microsoft/vstest-docs/blob/master/docs/RunSettingsArguments.md)
