---
title: ​.NET Core 3.0’daki yenilikler
description: .NET Core 3.0'da bulunan yeni özellikler hakkında bilgi edinin.
dev_langs:
- csharp
author: thraka
ms.author: adegeo
ms.date: 01/27/2020
ms.openlocfilehash: 6e85c2c3e796ae59a13f944bd4913e4b7316c56a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79398813"
---
# <a name="whats-new-in-net-core-30"></a>​.NET Core 3.0’daki yenilikler

Bu makalede, .NET Core 3.0'da yeni olan açıklanmaktadır. En büyük geliştirmelerden biri Windows masaüstü uygulamaları için destektir (yalnızca Windows). .NET Core 3.0 SDK bileşeni Windows Desktop'ı kullanarak Windows Formlarınızı ve Windows Sunu Vakfı (WPF) uygulamalarınızı taşıabilirsiniz. Açık olmak gerekirse, Windows Masaüstü bileşeni yalnızca desteklenir ve Windows'a dahil edilir. Daha fazla bilgi için bu makalenin ilerleyen bölümlerinde [Windows masaüstü](#windows-desktop) bölümüne bakın.

.NET Core 3.0 C# 8.0 için destek ekler. [Visual Studio 2019 sürüm 16.3](https://visualstudio.microsoft.com/vs/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) veya daha yeni, [Mac 8.3](/visualstudio/mac/install-preview) veya daha yeni için Visual Studio veya en son **C# uzantılı** [Visual Studio Code](https://code.visualstudio.com/) kullanmanız önerilir.

Şu anda Windows, macOS veya Linux'ta [.NET Core 3.0'ı indirin](https://aka.ms/netcore3download) ve başlayın.

Sürüm hakkında daha fazla bilgi için [.NET Core 3.0 duyurusuna](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-0/)bakın.

.NET Core RC1, Microsoft tarafından üretime hazır kabul edildi ve tam olarak desteklendi. Bir önizleme sürümü kullanıyorsanız, sürekli destek için RTM sürümüne geçmeniz gerekir.

## <a name="language-improvements-c-80"></a>Dil geliştirmeleri C# 8.0

C# 8.0 da [nullable başvuru türleri](../../csharp/tutorials/nullable-reference-types.md) özelliği, [async akışları](../../csharp/tutorials/generate-consume-asynchronous-stream.md)ve daha fazla desen içeren bu sürümün [bir](../../csharp/tutorials/pattern-matching.md)parçasıdır. C# 8.0 özellikleri hakkında daha fazla bilgi için [C# 8.0'daki yeniliklere](../../csharp/whats-new/csharp-8.md)bakın.

Aşağıda ayrıntılı olarak belirtilen aşağıdaki API özelliklerini desteklemek için dil geliştirmeleri eklendi:

- [Aralıklar ve endeksler](#ranges-and-indices)
- [Async akışları](#async-streams)

## <a name="net-standard-21"></a>.NET Standart 2.1

.NET Core 3.0 uygular **.NET Standart 2.1**. Ancak, varsayılan `dotnet new classlib` şablon hala **.NET Standart 2.0**hedefleyen bir proje oluşturur. **.NET Standart 2.1'i**hedeflemek için proje `TargetFramework` dosyanızı düzenlemesi ve özelliği `netstandard2.1`ni :

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <TargetFramework>netstandard2.1</TargetFramework>
  </PropertyGroup>

</Project>
```

Visual Studio kullanıyorsanız Visual [Studio 2019'a](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019)ihtiyacınız vardır, çünkü Visual Studio 2017 **.NET Standard 2.1** veya **.NET Core 3.0'ı**desteklemez.

## <a name="compiledeploy"></a>Derle/Dağıt

### <a name="default-executables"></a>Varsayılan yürütülebilir

.NET Core artık varsayılan olarak [çalışma süresine bağlı yürütülebilir ler](../deploying/index.md#publish-runtime-dependent) oluşturur. Bu davranış, .NET Core'un genel olarak yüklenmiş sürümünü kullanan uygulamalar için yenidir. Önceden, yalnızca [bağımsız dağıtımlar](../deploying/index.md#publish-self-contained) yürütülebilir bir üretebilme yi doğurabilir.

Sırasında `dotnet build` `dotnet publish`veya, bir yürütülebilir **(appHost**olarak da bilinir) kullandığınız SDK ortamı ve platformu eşleşen oluşturulur. Bu yürütülebilir kişilerle, aşağıdakiler gibi diğer yerel yürütülebilir kişilerle aynı şeyleri bekleyebilirsiniz:

- Çalıştırılabilir'e çift tıklayabilirsiniz.
- Uygulamayı doğrudan Windows ve Linux ve `myapp.exe` `./myapp` macOS'ta olduğu gibi bir komut isteminden başlatabilirsiniz.

### <a name="macos-apphost-and-notarization"></a>macOS appHost ve noterizasyon

*yalnızca macOS*

macOS için noterize .NET Core SDK 3.0 ile başlayarak, varsayılan yürütülebilir (appHost olarak da bilinir) üretmek için ayar varsayılan olarak devre dışı bırakılır. Daha fazla bilgi için [macOS Catalina Notarization ve .NET Core indirme ve projeleri üzerindeki etkisine](../install/macos-notarization-issues.md)bakın.

appHost ayarı etkinleştirildiğinde, .NET Core, oluşturduğunuzda veya yayımladığınızda yerel bir Mach-O çalıştırılabilir oluşturur. `dotnet run` Uygulamanız, komutla kaynak kodundan çalıştırıldığında veya doğrudan Yürütülebilir Mach-O'yu başlatarak appHost bağlamında çalışır.

appHost olmadan, bir kullanıcının çalışma [süresine bağlı](../deploying/index.md#publish-runtime-dependent) bir uygulamayı `dotnet <filename.dll>` başlatmasının tek yolu komuttur. Uygulamanızı [bağımsız](../deploying/index.md#publish-self-contained)olarak yayımladığınızda her zaman bir appHost oluşturulur.

Ya proje düzeyinde appHost yapılandırabilirsiniz, ya da `dotnet` `-p:UseAppHost` parametre ile belirli bir komut için appHost geçiş:

- Proje dosyası

  ```xml
  <PropertyGroup>
    <UseAppHost>true</UseAppHost>
  </PropertyGroup>
  ```

- Komut satırı parametresi

  ```dotnetcli
  dotnet run -p:UseAppHost=true
  ```

`UseAppHost` Ayar hakkında daha fazla bilgi için [Microsoft.NET.Sdk için MSBuild özelliklerine](../project-sdk/msbuild-props.md#useapphost)bakın.

### <a name="single-file-executables"></a>Tek dosyalı yürütülebilir

Komut, `dotnet publish` uygulamanızı platforma özgü tek dosyalı yürütülebilir bir şekilde paketlemenizi destekler. Yürütülebilir kendi kendini ayıklama ve uygulamanızı çalıştırmak için gerekli olan tüm bağımlılıkları (yerel dahil) içerir. Uygulama ilk çalıştırıldığında, uygulama uygulama adına ve yapı tanımlayıcısına göre bir dizine ayıklanır. Uygulama yeniden çalıştırıldığında başlatma daha hızlıdır. Yeni bir sürüm kullanılmadığı sürece uygulamanın kendisini ikinci kez ayıklaması gerekmez.

Tek dosyalı yürütülebilir yayımlamak `PublishSingleFile` için, projenizdeki veya komut `dotnet publish` satırında komut satırında komut satırında komut u belirleyin:

```xml
<PropertyGroup>
  <RuntimeIdentifier>win10-x64</RuntimeIdentifier>
  <PublishSingleFile>true</PublishSingleFile>
</PropertyGroup>
```

-veya-

```dotnetcli
dotnet publish -r win10-x64 -p:PublishSingleFile=true
```

Tek dosyalı yayımlama hakkında daha fazla bilgi için [tek dosyalı paketleyici tasarım belgesine](https://github.com/dotnet/designs/blob/master/accepted/single-file/design.md)bakın.

### <a name="assembly-linking"></a>Montaj bağlama

.NET core 3.0 SDK, IL'yi analiz ederek ve kullanılmayan derlemeleri kırparak uygulamaların boyutunu küçültebilen bir araçla birlikte gelir.

Bağımsız uygulamalar, .NET'in ana bilgisayara yüklenmesini gerektirmeden kodunuzu çalıştırmak için gereken her şeyi içerir. Ancak, çoğu zaman uygulama yalnızca işlev için çerçevenin küçük bir alt kümesi gerektirir ve diğer kullanılmayan kitaplıklar kaldırılabilir.

.NET Core artık uygulamanızın IL'sini tmak için [IL bağlayıcı](https://github.com/mono/linker) aracını kullanacak bir ayar içerir. Bu araç hangi kodun gerekli olduğunu algılar ve kullanılmayan kitaplıkları kırpar. Bu araç, bazı uygulamaların dağıtım boyutunu önemli ölçüde azaltabilir.

Bu aracı etkinleştirmek `<PublishTrimmed>` için projenize ayarı ekleyin ve bağımsız bir uygulama yayımlayın:

```xml
<PropertyGroup>
  <PublishTrimmed>true</PublishTrimmed>
</PropertyGroup>
```

```dotnetcli
dotnet publish -r <rid> -c Release
```

Örnek olarak, yayınlandığında, yaklaşık 70 MB boyutuna isabet eden temel "merhaba dünya" yeni konsol proje şablonu. Kullanılarak, `<PublishTrimmed>`bu boyut yaklaşık 30 MB azalır.

Yansıma veya ilgili dinamik özellikleri kullanan uygulamaların veya çerçevelerin (ASP.NET Core ve WPF dahil) genellikle kırıldığında kırılacak larını göz önünde bulundurmanız önemlidir. Bağlayıcının bu dinamik davranışı bilmediği ve yansıma için hangi çerçeve türlerinin gerekli olduğunu belirleyemediği için bu kırılma oluşur. IL Bağlayıcı aracı bu senaryonun farkında olacak şekilde yapılandırılabilir.

Her şeyden önce, kırpma sonra uygulamatest emin olun.

IL Bağlayıcı aracı hakkında daha fazla bilgi için [belgelere](https://aka.ms/dotnet-illink) bakın veya [mono/linker]( https://github.com/mono/linker) repo'yu ziyaret edin.

### <a name="tiered-compilation"></a>Katmanlı derleme

[Katmanlı derleme](https://github.com/dotnet/runtime/blob/master/docs/design/features/tiered-compilation-guide.md) (TC) varsayılan olarak .NET Core 3.0 ile açıktır. Bu özellik, daha iyi performans elde etmek için çalışma süresinin tam zamanında (JIT) derleyiciyi daha uyumlu bir şekilde kullanmasını sağlar.

Katmanlı derlemenin temel avantajı, daha düşük kaliteli ama daha hızlı bir katmanda veya daha yüksek kalitede ama daha yavaş bir katmanda iki farklı jitting yöntemi sağlamaktır. Kalite, yöntemin ne kadar iyi optimize edildiklerine işaret eder. TC, başlangıçtan sabit duruma kadar yürütmenin çeşitli aşamalarından geçerken bir uygulamanın performansını artırmaya yardımcı olur. Katmanlı derleme devre dışı bırakıldığında, her yöntem başlangıç performansına göre sabit durum performansına bağlı tek bir şekilde derlenir.

TC etkinleştirildiğinde, bir uygulama başlatıldığında yöntem derlemesi için aşağıdaki davranış uygulanır:

- Yöntemde zaman önceden derlenmiş kod veya [ReadyToRun](#readytorun-images)varsa, önceden oluşturulmuş kod kullanılır.
- Aksi takdirde, yöntem jitted. Genellikle, bu yöntemler değer türleri üzerinde genel vardır.
  - *Hızlı JIT* daha hızlı düşük kaliteli (veya daha az optimize edilmiş) kod üretir. .NET Core 3.0'da, Quick JIT döngü içermeyen yöntemler için varsayılan olarak etkinleştirilir ve başlangıç sırasında tercih edilir.
  - Tam olarak optimize edilen JIT daha yüksek kaliteli (veya daha iyi optimize edilmiş) kod üretir. Hızlı JIT'nin kullanılmayacağı yöntemler için (örneğin, yöntem <xref:System.Runtime.CompilerServices.MethodImplOptions.AggressiveOptimization?displayProperty=nameWithType>atfedilirse), tam olarak optimize edilen JIT kullanılır.

Sık çağrılan yöntemler için, tam zamanında derleyici sonunda arka planda tam olarak optimize edilmiş kod oluşturur. Daha sonra en iyi duruma getirilmiş kod, bu yöntem için önceden derlenmiş kodun yerini alır.

Hızlı JIT tarafından oluşturulan kod daha yavaş çalışabilir, daha fazla bellek tahsis edebilir veya daha fazla yığın alanı kullanabilir. Sorunlar varsa, proje dosyasındaki bu MSBuild özelliğini kullanarak Hızlı JIT'yi devre dışı kullanabilirsiniz:

```xml
<PropertyGroup>
  <TieredCompilationQuickJit>false</TieredCompilationQuickJit>
</PropertyGroup>
```

TC'yi tamamen devre dışı kullanabilirsiniz, proje dosyanızdaki bu MSBuild özelliğini kullanın:

```xml
<PropertyGroup>
  <TieredCompilation>false</TieredCompilation>
</PropertyGroup>
```

> [!TIP]
> Proje dosyasındaki bu ayarları değiştirirseniz, yeni ayarların yansıtılması için temiz bir yapı `obj` gerçekleştirmeniz gerekebilir (ve `bin` dizinleri silin ve yeniden oluşturun).

Derlemeyi çalışma zamanında yapılandırma hakkında daha fazla bilgi [için derleme için Çalışma zamanı yapılandırma seçeneklerine](../run-time-config/compilation.md)bakın.

### <a name="readytorun-images"></a>ReadyToRun görüntüleri

.NET Core uygulamanızın başlangıç süresini ReadyToRun (R2R) formatında uygulama derlemelerinizi derleyerek geliştirebilirsiniz. R2R, ileri zaman (AOT) derlemesinin bir şeklidir.

R2R ikilileri, uygulamanız yüklerken tam zamanında (JIT) derleyicisinin yapması gereken iş miktarını azaltarak başlangıç performansını artırır. İkili, JIT'nin üreteceği kodla karşılaştırıldığında benzer yerel kodlar içerir. Ancak, R2R ikilileri, bazı senaryolar için hala gerekli olan ara dil (IL) kodu ve aynı kodun yerel sürümünü içerdiğinden daha büyüktür. R2R yalnızca Linux x64 veya Windows x64 gibi belirli çalışma zamanı ortamlarını (RID) hedefleyen bağımsız bir uygulama yayımladığınızda kullanılabilir.

Projenizi ReadyToRun olarak derlemek için aşağıdakileri yapın:

01. Projenize `<PublishReadyToRun>` ayarı ekleyin:

    ```xml
    <PropertyGroup>
      <PublishReadyToRun>true</PublishReadyToRun>
    </PropertyGroup>
    ```

01. Bağımsız bir uygulama yayımlayın. Örneğin, bu komut Windows'un 64 bit sürümü için bağımsız bir uygulama oluşturur:

    ```dotnetcli
    dotnet publish -c Release -r win-x64 --self-contained
    ```

#### <a name="cross-platformarchitecture-restrictions"></a>Çapraz platform/mimari kısıtlamaları

ReadyToRun derleyicisi şu anda çapraz hedeflemeyi desteklemiyor. Belirli bir hedef üzerinde derlemek gerekir. Örneğin, Windows x64 için R2R görüntüleri istiyorsanız, bu ortamda yayımlama komutunu çalıştırmanız gerekir.

Çapraz hedefleme için özel durumlar:

- Windows x64, Windows ARM32, ARM64 ve x86 görüntülerini derlemek için kullanılabilir.
- Windows x86, Windows ARM32 görüntülerini derlemek için kullanılabilir.
- Linux x64, Linux ARM32 ve ARM64 görüntülerini derlemek için kullanılabilir.

## <a name="runtimesdk"></a>Çalışma Süresi/SDK

### <a name="major-version-runtime-roll-forward"></a>Ana sürüm runtime roll forward

.NET Core 3.0, uygulamanızın .NET Core'un en son ana sürümüne ilerlemesini sağlayan bir tercih özelliği sunar. Ayrıca, uygulamanıza nasıl ileri sarma uygulandığını denetlemek için yeni bir ayar eklendi. Bu, aşağıdaki şekillerde yapılandırılabilir:

- Proje dosyası özelliği:`RollForward`
- Çalışma zamanı yapılandırma dosyası özelliği:`rollForward`
- Ortam değişkeni:`DOTNET_ROLL_FORWARD`
- Komut satırı bağımsız değişkeni:`--roll-forward`

Aşağıdaki değerlerden biri belirtilmelidir. Ayar atlanırsa, **Küçük** varsayılandır.

- **En Son Yama**\
En yüksek yama sürümüne doğru yuvarlan. Bu, küçük sürümün devrilmelerini devre dışı kılabilir.
- **Küçük**\
İstenen küçük sürüm eksikse, en düşük yüksek küçük sürüme ilerleyin. İstenen küçük sürüm varsa, **En Son Yama** ilkesi kullanılır.
- **Büyük**\
İstenen ana sürüm eksikse, en düşük yüksek ana sürüme ve en düşük küçük sürüme ilerleyin. İstenen ana sürüm varsa, **Küçük** ilke kullanılır.
- **Son Küçük**\
İstenen küçük sürüm mevcut olsa bile, en yüksek küçük sürüme ilerleyin. Bileşen barındırma senaryoları için tasarlanmıştır.
- **Son Major**\
İstenen büyük sürüm mevcut olsa bile, en yüksek majör ve en yüksek minör sürüme ilerleyin. Bileşen barındırma senaryoları için tasarlanmıştır.
- **Devre dışı bırakmak**\
Öne doğru yuvarlanma. Yalnızca belirtilen sürüme bağla. Bu ilke, en son düzeltme ekilerine ilerleme yitirme özelliğini devre dışı kattığı için genel kullanım için önerilmez. Bu değer yalnızca sınama için önerilir.

Devre **Dışı Atanın** yanı sıra, tüm ayarlar kullanılabilir en yüksek yama sürümünü kullanır.

### <a name="build-copies-dependencies"></a>Kopya bağımlılıkları oluşturma

Komut `dotnet build` artık NuGet önbelleğinden yapı çıktıklasörüne uygulamanız için NuGet bağımlılıklarını kopyalar. Daha önce, bağımlılıklar yalnızca `dotnet publish`bir parçası olarak kopyalandı.

Bağlantı ve jilet sayfası yayımlama gibi hala yayımlama gerektiren bazı işlemler vardır.

### <a name="local-tools"></a>Yerel araçlar

.NET Core 3.0 yerel araçları tanıttı. Yerel araçlar [genel araçlara](../tools/global-tools.md) benzer, ancak diskteki belirli bir konumla ilişkilidir. Yerel araçlar genel olarak kullanılamaz ve NuGet paketleri olarak dağıtılır.

> [!WARNING]
> .NET Core 3.0 Preview 1'de yerel araçları `dotnet tool restore` `dotnet tool install`denediyseniz, örneğin çalışma veya yerel araçlar önbelleği klasörünü silin. Aksi takdirde, yerel araçlar daha yeni sürümde çalışmaz. Bu klasör şu adreste bulunur:
>
> macOS,Linux'ta:`rm -r $HOME/.dotnet/toolResolverCache`
>
> Windows'da:`rmdir /s %USERPROFILE%\.dotnet\toolResolverCache`

Yerel araçlar, geçerli dizininizdeki bir bildirim dosya adına `dotnet-tools.json` dayanır. Bu bildirim dosyası, o klasörde ve aşağıda bulunabilecek araçları tanımlar. Kodunla çalışan herkesin aynı araçları geri yükleyip kullanabileceğinden emin olmak için bildirim dosyasını kodunuzla birlikte dağıtabilirsiniz.

Hem genel hem de yerel araçlar için çalışma zamanının uyumlu bir sürümü gereklidir. Şu anda hedef NuGet.org .NET Core Runtime 2.1'de birçok araç. Bu araçları genel olarak veya yerel olarak yüklemek için [NET Core 2.1 Çalışma Zamanı'nı](https://dotnet.microsoft.com/download/dotnet-core/2.1)yüklemeniz gerekir.

### <a name="new-globaljson-options"></a>Yeni global.json seçenekleri

*global.json* dosyası, .NET Core SDK'nın hangi sürümünün kullanıldığını tanımlamaya çalışırken daha fazla esneklik sağlayan yeni seçeneklere sahiptir. Yeni seçenekler şunlardır:

- `allowPrerelease`: SDK çözümleyicisinin kullanılacak SDK sürümünü seçerken yayın öncesi sürümleri ni göz önünde bulundurması gerekip gerekmediğini gösterir.
- `rollForward`: Belirli bir SDK sürümü eksikolduğunda veya daha yüksek bir sürümü kullanma yönergesi olarak bir geri dönüş olarak, bir SDK sürümünü seçerken kullanılacak roll-forward ilkesini gösterir.

Varsayılan değerler, desteklenen değerler ve yeni eşleşen kurallar gibi değişiklikler hakkında daha fazla bilgi için [global.json genel bakış](../tools/global-json.md)bilgisine bakın.

### <a name="smaller-garbage-collection-heap-sizes"></a>Küçük Çöp Toplama yığın boyutları

Çöp Toplayıcı'nın varsayılan yığın boyutu azaltıldı ve daha az bellek kullanılarak .NET Core'a neden oldu. Bu değişiklik, modern işlemci önbelleği boyutlarıyla nesil 0 ayırma bütçesiyle daha iyi hizalanır.

### <a name="garbage-collection-large-page-support"></a>Çöp Toplama Büyük Sayfa desteği

Büyük Sayfalar (Linux'taki Büyük Sayfalar olarak da bilinir), işletim sisteminin bu büyük sayfaları isteyen uygulamanın performansını artırmak için yerel sayfa boyutundan (genellikle 4K) daha büyük bellek bölgeleri oluşturabildiği bir özelliktir.

Çöp Toplayıcı artık Windows'da büyük sayfaları ayırmayı seçmek için bir opt-in özelliği olarak **GCLargePages** ayarı ile yapılandırılabilir.

## <a name="windows-desktop--com"></a>Windows Masaüstü & COM

### <a name="net-core-sdk-windows-installer"></a>.NET Core SDK Windows Yükleyici

Windows için MSI yükleyicisi .NET Core 3.0 ile başlayarak değişti. SDK yükleyiciler artık SDK özellik bant sürümlerini yerinde yükseltecektir. Özellik bantları, sürüm numarasının *yama* bölümündeki *yüzlerce* grupta tanımlanır. Örneğin, **3.0._ 101_ ** ve **3.0._ 201_ ** iki farklı özellik bantları sürümleri ise **3.0 vardır._ 101_ ** ve **3.0._ 199_ ** aynı özellik grubunda. Ve, ne zaman .NET Çekirdek SDK **3.0._ 101_ ** yüklü, .NET Çekirdek SDK **3.0._ Varsa 100_ ** makineden çıkarılır. Ne zaman .NET Çekirdek SDK **3.0._ 200_ ** aynı makineye yüklenir, .NET Core SDK **3.0._ 101_ ** kaldırılmayacak.

Sürüm hakkında daha fazla bilgi için [.NET Core'un nasıl sürümlendirilebildiğini](../versions/index.md)öğrenin.

### <a name="windows-desktop"></a>Windows masaüstü

.NET Core 3.0, Windows Presentation Foundation (WPF) ve Windows Formlarını kullanarak Windows masaüstü uygulamalarını destekler. Bu çerçeveler aynı zamanda [XAML adaları](/windows/uwp/xaml-platform/xaml-host-controls)üzerinden Windows UI XAML Kütüphanesi (WinUI) modern denetimler ve Akıcı stil kullanarak destek.

Windows Desktop bileşeni, Windows .NET Core 3.0 SDK'nın bir parçasıdır.

Aşağıdaki `dotnet` komutlarla yeni bir WPF veya Windows Forms uygulaması oluşturabilirsiniz:

```dotnetcli
dotnet new wpf
dotnet new winforms
```

Visual Studio 2019 ,NET Core 3.0 Windows Forms ve WPF için **Yeni Proje** şablonları ekler.

Varolan bir .NET Framework uygulamasının bağlantı noktası hakkında daha fazla bilgi için Port [WPF projeleri](../../desktop-wpf/migration/convert-project-from-net-framework.md) ve [Bağlantı Noktası Windows Formları projelerine](../porting/winforms.md)bakın.

#### <a name="winforms-high-dpi"></a>WinForms yüksek DPI

.NET Core Windows Forms uygulamaları ile yüksek <xref:System.Windows.Forms.Application.SetHighDpiMode(System.Windows.Forms.HighDpiMode)?displayProperty=nameWithType>DPI modu ayarlayabilirsiniz. Yöntem, `SetHighDpiMode` ayarı daha önce `App.Manifest` `Application.Run`P/Invoke gibi başka yollarla ayarlanmadıkça ilgili yüksek DPI modunu ayarlar.

Enum `highDpiMode` tarafından ifade edilen olası değerler şunlardır: <xref:System.Windows.Forms.HighDpiMode?displayProperty=nameWithType>

- `DpiUnaware`
- `SystemAware`
- `PerMonitor`
- `PerMonitorV2`
- `DpiUnawareGdiScaled`

Yüksek DPI modları hakkında daha fazla bilgi için [Windows'da Yüksek DPI Masaüstü Uygulama Geliştirme'ye](/windows/desktop/hidpi/high-dpi-desktop-application-development-on-windows)bakın.

### <a name="create-com-components"></a>COM bileşenleri oluşturma

Windows'da artık COM çağrılabilir yönetilen bileşenler oluşturabilirsiniz. Bu özellik, .NET Core'u COM eklenti modelleri ile kullanmak ve aynı zamanda .NET Framework ile eşlik sağlamak için çok önemlidir.

*Mscoree.dll'nin* COM sunucusu olarak kullanıldığı .NET Framework'ün aksine, .NET Core, COM bileşeninizi oluşturduğunuzda *depo* gözüne yerel bir başlatıcı dll ekler.

Com bileşeninin nasıl oluşturulup tüketilmesine bir örnek [için, COM](https://github.com/dotnet/samples/tree/master/core/extensions/COMServerDemo)Demosu'na bakın.

### <a name="windows-native-interop"></a>Windows Native Interop

Windows düz C API'leri, COM ve WinRT şeklinde zengin bir yerel API sunar. .NET Core **P/Invoke'ı**desteklerken , .NET Core 3.0, **COM API'lerini CoCreate** ve **Activate WinRT API'lerini**etkinleştirme özelliğini ekler. Kod örneği için [Excel Demosu'na](https://github.com/dotnet/samples/tree/master/core/extensions/ExcelDemo)bakın.

### <a name="msix-deployment"></a>MSIX Dağıtım

[MSIX](https://docs.microsoft.com/windows/msix/) yeni bir Windows uygulama paketi biçimidir. .NET Core 3.0 masaüstü uygulamalarını Windows 10'a dağıtmak için kullanılabilir.

Visual Studio 2019'da bulunan [Windows Uygulama Paketleme Projesi,](https://docs.microsoft.com/windows/uwp/porting/desktop-to-uwp-packaging-dot-net) [bağımsız](../deploying/index.md#publish-self-contained) .NET Core uygulamalarıyla MSIX paketleri oluşturmanıza olanak tanır.

.NET Core proje `<RuntimeIdentifiers>` dosyasında, özellikteki desteklenen çalışma sürelerini belirtilmelidir:

```xml
<RuntimeIdentifiers>win-x86;win-x64</RuntimeIdentifiers>
```

## <a name="linux-improvements"></a>Linux geliştirmeleri

### <a name="serialport-for-linux"></a>Linux için SerialPort

.NET Core 3.0 Linux <xref:System.IO.Ports.SerialPort?displayProperty=nameWithType> için temel destek sağlar.

Daha önce,.NET Core yalnızca `SerialPort` Windows'da kullanılarak desteklenirdi.

Linux'taki seri bağlantı noktası için sınırlı destek hakkında daha fazla bilgi için [#33146 GitHub sorununa](https://github.com/dotnet/corefx/issues/33146)bakın.

### <a name="docker-and-cgroup-memory-limits"></a>Docker ve cgroup bellek Sınırları

Docker ile Linux'ta .NET Core 3.0'ı çalıştırmak cgroup bellek limitleri ile daha iyi çalışır. .NET Core gibi bellek sınırları `docker run -m`içeren bir Docker kapsayıcısı çalıştırmak, .NET Core'un nasıl çalıştığını değiştirir.

- Varsayılan Çöp Toplayıcı (GC) yığın boyutu: en fazla 20 mb veya kapsayıcıdaki bellek sınırının %75'i.
- Açık boyut mutlak bir sayı veya cgroup sınırı yüzdesi olarak ayarlanabilir.
- GC yığını başına en az ayrılmış segment boyutu 16 mb'dır. Bu boyut, makinelerde oluşturulan yığın sayısını azaltır.

### <a name="gpio-support-for-raspberry-pi"></a>Raspberry Pi için GPIO Desteği

GPIO programlama için kullanabileceğiniz NuGet'e iki paket yayımlanmıştır:

- [System.Device.Gpio](https://www.nuget.org/packages/System.Device.Gpio)
- [Iot.Device.Bindings](https://www.nuget.org/packages/Iot.Device.Bindings)

GPIO paketleri *GPIO,* *SPI,* *I2C*ve *PWM* cihazları için API'leri içerir. IoT bağlama paketi aygıt bağlamalarını içerir. Daha fazla bilgi için [GitHub repo cihazlarına](https://github.com/dotnet/iot/blob/master/src/devices/)bakın.

### <a name="arm64-linux-support"></a>ARM64 Linux desteği

.NET Core 3.0, Linux için ARM64 desteği ne kadar ekler. ARM64 için birincil kullanım örneği şu anda IoT senaryoları ile. Daha fazla bilgi için [bkz.](https://github.com/dotnet/announcements/issues/82)

[ARM64'teki .NET Core için Docker görüntüleri](https://hub.docker.com/r/microsoft/dotnet/) Alpine, Debian ve Ubuntu için kullanılabilir.

> [!NOTE]
> **ARM64** Windows desteği henüz kullanılamıyor.

## <a name="security"></a>Güvenlik

### <a name="tls-13--openssl-111-on-linux"></a>TLS 1.3 & Linux'ta OpenSSL 1.1.1

.NET Core artık [OpenSSL 1.1.1'de belirli](https://www.openssl.org/blog/blog/2018/09/11/release111/)bir ortamda mevcut olduğunda TLS 1.3 desteğinden yararlanıyor. TLS 1.3 ile:

- Bağlantı süreleri, istemci ve sunucu arasında gereken azaltılmış gidiş dönüşlerle iyileştirilir.
- Çeşitli eski ve güvensiz şifreleme algoritmalarının kaldırılması nedeniyle geliştirilmiş güvenlik.

Kullanılabilir olduğunda, .NET Core 3.0, Linux sisteminde **OpenSSL 1.1.1**, **OpenSSL 1.1.0**veya **OpenSSL 1.0.2** kullanır. **OpenSSL 1.1.1** kullanılabilir <xref:System.Net.Security.SslStream?displayProperty=nameWithType> olduğunda, <xref:System.Net.Http.HttpClient?displayProperty=nameWithType> hem **tls 1.3'ü** hem de türleri kullanır (hem istemci hem de sunucu nun **TLS 1.3'ü**desteklediğini varsayarsak).

> [!IMPORTANT]
> Windows ve macOS henüz **TLS 1.3'u**destekletmiyor. .NET Core 3.0, destek sunulduğunda bu işletim sistemlerinde **TLS 1.3'u** destekleyecektir.

Aşağıdaki C# 8.0 örneği Ubuntu 18.10'da .NET Core <https://www.cloudflare.com>3.0'ı gösterir:

[!code-csharp[TLSExample](~/samples/snippets/core/whats-new/whats-new-in-30/cs/TLS.cs#TLS)]

### <a name="cryptography-ciphers"></a>Şifreleme şifreleri

.NET <xref:System.Security.Cryptography.AesGcm?displayProperty=nameWithType> 3.0, <xref:System.Security.Cryptography.AesCcm?displayProperty=nameWithType> sırasıyla ve sırasıyla uygulanan **AES-GCM** ve **AES-CCM** şifreleri için destek ekler. Bu algoritmalar, [ilişkilendirme verileri (AEAD) algoritmaları ile kimlik doğrulaması şifreleme vardır.](https://en.wikipedia.org/wiki/Authenticated_encryption)

Aşağıdaki kod, rasgele `AesGcm` verileri şifrelemek ve çözmek için şifreyi kullanarak gösterir.

[!code-csharp[AesGcm](~/samples/snippets/core/whats-new/whats-new-in-30/cs/Cipher.cs#AesGcm)]

### <a name="cryptographic-key-importexport"></a>Şifreleme Anahtarı İthalat/Verme

.NET Core 3.0, standart biçimlerden asimetrik ortak ve özel anahtarların ithalat ve dışa aktarını destekler. X.509 sertifikası kullanmanız gerekmez.

*RSA,* *DSA,* *ECDsa*ve *ECDiffieHellman*gibi tüm anahtar türleri aşağıdaki biçimleri destekler:

- **Ortak Anahtar**
  - X.509 KonuPublicKeyInfo

- **Özel anahtar**
  - PKCS#8 PrivateKeyInfo
  - PKCS#8 ŞifreliPrivateKeyInfo

RSA tuşları da destekler:

- **Ortak Anahtar**
  - PKCS#1 RSAPublicKey

- **Özel anahtar**
  - PKCS#1 RSAPrivateKey

Dışa aktarma yöntemleri DER kodlu ikili veri üretir ve alma yöntemleri de aynı şeyi bekler. Bir anahtar metin dostu PEM biçiminde depolanırsa, arayanın alma yöntemini aramadan önce içeriği temel olarak 64-decode'u çözmesi gerekir.

[!code-csharp[RSA](~/samples/snippets/core/whats-new/whats-new-in-30/cs/RSA.cs#Rsa)]

**PKCS#8** dosyaları ile <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo?displayProperty=nameWithType> kontrol edilebilir ve **PFX/PKCS#12** dosyaları <xref:System.Security.Cryptography.Pkcs.Pkcs12Info?displayProperty=nameWithType>ile kontrol edilebilir. **PFX/PKCS#12** dosyaları ile <xref:System.Security.Cryptography.Pkcs.Pkcs12Builder?displayProperty=nameWithType>manipüle edilebilir.

## <a name="net-core-30-api-changes"></a>.NET Core 3.0 API değişiklikleri

### <a name="ranges-and-indices"></a>Aralıklar ve endeksler

Yeni <xref:System.Index?displayProperty=nameWithType> tür dizin oluşturma için kullanılabilir. En başından veya `int` sondan sayılan bir önek `^` işlecinden (C#) bir tane oluşturabilirsiniz:

```csharp
Index i1 = 3;  // number 3 from beginning
Index i2 = ^4; // number 4 from end
int[] a = { 0, 1, 2, 3, 4, 5, 6, 7, 8, 9 };
Console.WriteLine($"{a[i1]}, {a[i2]}"); // "3, 6"
```

Ayrıca, <xref:System.Range?displayProperty=nameWithType> biri başlangıç, diğeri bitiş `Index` için olmak üzere iki değerden oluşan ve `x..y` aralık ifadesi (C#) ile yazılabilir. Daha sonra bir `Range`dilim üreten bir , ile dizine yapabilirsiniz:

```csharp
var slice = a[i1..i2]; // { 3, 4, 5 }
```

Daha fazla bilgi [için, aralıkları ve endeksleri öğretici](../../csharp/tutorials/ranges-indexes.md)bakın.

### <a name="async-streams"></a>Zaman uyumsuz akışlar

Türü <xref:System.Collections.Generic.IAsyncEnumerable%601> yeni bir asynchronous <xref:System.Collections.Generic.IEnumerable%601>sürümüdür. Dil, `await foreach` öğelerini `IAsyncEnumerable<T>` tüketmenizi ve `yield return` bunları kullanarak öğeleri oluşturmanızı sağlar.

Aşağıdaki örnek, async akışlarının hem üretimini hem de tüketimini göstermektedir. `foreach` İfade async ve kendisi `yield return` arayanlar için bir async akışı oluşturmak için kullanır. Bu desen `yield return`(kullanarak) async akışları üretmek için önerilen modeldir.

```csharp
async IAsyncEnumerable<int> GetBigResultsAsync()
{
    await foreach (var result in GetResultsAsync())
    {
        if (result > 20) yield return result;
    }
}
```

Yapabilmenin `await foreach`yanı sıra, async yineleyicileri de oluşturabilirsiniz, örneğin, hem de `IAsyncEnumerable/IAsyncEnumerator` `await` `yield` içinde oluşturabileceğiniz bir yineleme yi döndürebilir. Atılması gereken nesneler için, `IAsyncDisposable`çeşitli BCL türlerinin uyguladığı `Stream` ve . `Timer`

Daha fazla bilgi [için, async akışları öğretici](../../csharp/tutorials/generate-consume-asynchronous-stream.md)bakın.

### <a name="ieee-floating-point"></a>IEEE Kayan nokta

Kayan nokta API'leri [IEEE 754-2008 revizyonuna](https://en.wikipedia.org/wiki/IEEE_754-2008_revision)uyacak şekilde güncellenmektedir. Bu değişikliklerin amacı, **gerekli** tüm işlemleri ortaya çıkarmak ve iEEE spec ile davranışsal olarak uyumlu olduğundan emin olmaktır. Kayan nokta iyileştirmeleri hakkında daha fazla bilgi için [.NET Core 3.0 blog gönderisindeki Kayan Nokta Ayrıştırma ve Biçimlendirme geliştirmelerine](https://devblogs.microsoft.com/dotnet/floating-point-parsing-and-formatting-improvements-in-net-core-3-0/) bakın.

Ayrışma ve biçimlendirme düzeltmeleri şunlardır:

- Herhangi bir uzunluktaki girişleri doğru bir şekilde ayrıştın ve yuvarlatın.
- Doğru ayrışdırın ve biçim negatif sıfır.
- Doğru `Infinity` ayrışdırma `NaN` ve büyük/küçük harf duyarsız kontrol yaparak `+` ve varsa isteğe bağlı bir önceki izin.

Yeni <xref:System.Math?displayProperty=nameWithType> API'ler şunlardır:

- <xref:System.Math.BitIncrement(System.Double)>Ve<xref:System.Math.BitDecrement(System.Double)>\
IEEE `nextDown` ve `nextUp` IEEE işlemlerine karşılık gelir. Girişten (sırasıyla) daha büyük veya daha az olan en küçük kayan nokta numarasını döndürerler. Örneğin, `Math.BitIncrement(0.0)` döndürecek. `double.Epsilon`

- <xref:System.Math.MaxMagnitude(System.Double,System.Double)>Ve<xref:System.Math.MinMagnitude(System.Double,System.Double)>\
Ve `minNumMag` IEEE `maxNumMag` işlemlerine karşılık gelir, iki girdinin (sırasıyla) büyüklüğü daha büyük veya daha az olan değeri döndürerler. Örneğin, `Math.MaxMagnitude(2.0, -3.0)` döndürecek. `-3.0`

- <xref:System.Math.ILogB(System.Double)>\
İntegral `logB` değeri döndüren IEEE işlemine karşılık gelir, giriş parametresinin integral taban-2 log'u verir. Bu yöntem, etkili olarak `floor(log2(x))`aynıdır , ancak en az yuvarlama hatası ile yapılır.

- <xref:System.Math.ScaleB(System.Double,System.Int32)>\
Ayrılmaz bir `scaleB` değer alan IEEE işlemine karşılık gelir, etkili bir şekilde `x * pow(2, n)`döner, ancak en az yuvarlama hatası ile yapılır.

- <xref:System.Math.Log2(System.Double)>\
`log2` IEEE işlemine karşılık gelir, baz-2 logaritmasını döndürür. Yuvarlama hatalarını en aza indirir.

- <xref:System.Math.FusedMultiplyAdd(System.Double,System.Double,System.Double)>\
`fma` IEEE işlemine karşılık gelir, erimiş çarpma ekleme gerçekleştirir. Diğer bir şey, tek bir işlem olarak, `(x * y) + z` yuvarlama hatasını en aza indirir. Bir örnek `FusedMultiplyAdd(1e308, 2.0, -1e308)`, `1e308`hangi döner . Düzenli `(1e308 * 2.0) - 1e308` döner `double.PositiveInfinity`.

- <xref:System.Math.CopySign(System.Double,System.Double)>\
`copySign` IEEE işlemine karşılık gelir, değerini `x`döndürür, ancak `y`işareti ile .

### <a name="net-platform-dependent-intrinsics"></a>.NET Platformuna Bağımlı İçsel

**SIMD** veya **Bit İşleme yönergesi** kümeleri gibi belirli perf odaklı CPU yönergelerine erişime izin veren API'ler eklendi. Bu yönergeler, verileri paralel olarak verimli bir şekilde işleme gibi belirli senaryolarda önemli performans iyileştirmeleri elde edilebilebilir.

Uygun olduğu durumlarda, .NET kitaplıkları performansı artırmak için bu yönergeleri kullanmaya başladı.

Daha fazla bilgi için [bkz.](https://github.com/dotnet/designs/blob/master/accepted/platform-intrinsics.md)

### <a name="improved-net-core-version-apis"></a>Geliştirilmiş .NET Çekirdek Sürüm API'leri

.NET Core 3.0 ile başlayarak,.NET Core ile sağlanan sürüm API'leri artık beklediğiniz bilgileri döndürün. Örnek:

```csharp
System.Console.WriteLine($"Environment.Version: {System.Environment.Version}");

// Old result
//   Environment.Version: 4.0.30319.42000
//
// New result
//   Environment.Version: 3.0.0
```

```csharp
System.Console.WriteLine($"RuntimeInformation.FrameworkDescription: {System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription}");

// Old result
//   RuntimeInformation.FrameworkDescription: .NET Core 4.6.27415.71
//
// New result (notice the value includes any preview release information)
//   RuntimeInformation.FrameworkDescription: .NET Core 3.0.0-preview4-27615-11
```

> [!WARNING]
> Değişimi bozuyor. Sürüm düzeni değiştiğinden, bu teknik olarak bir son landırma değişikliğidir.

### <a name="fast-built-in-json-support"></a>Hızlı dahili JSON desteği

.NET kullanıcıları büyük ölçüde [newtonsoft.Json](https://www.newtonsoft.com/json) ve diğer popüler JSON kütüphaneler, iyi seçimler olmaya devam güvendi. `Newtonsoft.Json`kaputun altındaki UTF-16 olan temel veri türü olarak .NET dizeleri kullanır.

Yeni yerleşik JSON desteği yüksek performanslı, düşük tahsisat ve UTF-8 kodlanmış JSON metni ile çalışır. <xref:System.Text.Json> Ad alanı ve türleri hakkında daha fazla bilgi için aşağıdaki makalelere bakın:

* [.NET'te JSON serileştirme - genel bakış](../../standard/serialization/system-text-json-overview.md)
* [JSON'u .NET'te seri hale getirmek ve deserialize etmek için .](../../standard/serialization/system-text-json-how-to.md)
* [Newtonsoft.Json'dan System.Text.Json'a nasıl göç edilir?](../../standard/serialization/system-text-json-migrate-from-newtonsoft-how-to.md)

### <a name="http2-support"></a>HTTP/2 desteği

Tür <xref:System.Net.Http.HttpClient?displayProperty=nameWithType> HTTP/2 protokolünü destekler. HTTP/2 etkinse, HTTP protokol sürümü TLS/ALPN üzerinden görüşülür ve sunucu kullanmayı seçerse HTTP/2 kullanılır.

Varsayılan protokol HTTP/1.1 olarak kalır, ancak HTTP/2 iki farklı şekilde etkinleştirilebilir. İlk olarak, HTTP/2'yi kullanacak şekilde HTTP istek iletisini ayarlayabilirsiniz:

[!code-csharp[Http2Request](~/samples/snippets/core/whats-new/whats-new-in-30/cs/http.cs#Request)]

İkinci olarak, <xref:System.Net.Http.HttpClient> varsayılan olarak HTTP/2'yi kullanmak üzere değiştirebilirsiniz:

[!code-csharp[Http2Client](~/samples/snippets/core/whats-new/whats-new-in-30/cs/http.cs#Client)]

Çoğu zaman bir uygulama geliştirirken, şifrelenmemiş bir bağlantı kullanmak istersiniz. Hedef uç noktanın HTTP/2'yi kullandığını biliyorsanız, HTTP/2 için şifrelenmemiş bağlantıları açabilirsiniz. Ortam değişkenini `DOTNET_SYSTEM_NET_HTTP_SOCKETSHTTPHANDLER_HTTP2UNENCRYPTEDSUPPORT` ayarlayarak `1` veya uygulama bağlamında etkinleştirerek açabilirsiniz:

[!code-csharp[Http2Context](~/samples/snippets/core/whats-new/whats-new-in-30/cs/http.cs#AppContext)]

## <a name="next-steps"></a>Sonraki adımlar

- [.NET Core 2.2 ve 3.0 arasındaki kesme değişikliklerini gözden geçirin.](../compatibility/2.2-3.0.md)
- [Windows Forms uygulamaları için .NET Core 3.0'daki son dakika değişikliklerini gözden geçirin.](../compatibility/winforms.md#net-core-30)
