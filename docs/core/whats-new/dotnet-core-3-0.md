---
title: ​.NET Core 3.0’daki yenilikler
description: .NET Core 3,0 ' de bulunan yeni özellikler hakkında bilgi edinin.
dev_langs:
- csharp
author: adegeo
ms.author: adegeo
ms.date: 01/27/2020
ms.openlocfilehash: ac2b4193849c56002c5bba35932f2882b987a0d6
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90537502"
---
# <a name="whats-new-in-net-core-30"></a>​.NET Core 3.0’daki yenilikler

Bu makalede .NET Core 3,0 ' deki yenilikler açıklanır. En büyük geliştirmelerden biri, Windows Masaüstü uygulamaları için destek içerir (yalnızca Windows). .NET Core 3,0 SDK bileşeni Windows Masaüstü 'Nü kullanarak Windows Forms ve Windows Presentation Foundation (WPF) uygulamalarınızın bağlantı noktası oluşturabilirsiniz. Temiz olması için, Windows Masaüstü bileşeni yalnızca Windows 'da desteklenir ve Windows 'a dahildir. Daha fazla bilgi için bu makalenin devamındaki [Windows Masaüstü](#windows-desktop) bölümüne bakın.

.NET Core 3,0, C# 8,0 için destek ekler. [Visual Studio 2019 sürüm 16,3](https://visualstudio.microsoft.com/vs/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) veya daha yeni bir sürümünü, [Mac için Visual Studio 8,3](/visualstudio/mac/install-preview) veya daha yenisini veya en son **C# uzantısıyla** [Visual Studio Code](https://code.visualstudio.com/) kullanmanız önemle önerilir.

Şimdi Windows, macOS veya Linux 'ta [.NET Core 3,0 'Yi indirin ve](https://aka.ms/netcore3download) kullanmaya başlayın.

Yayın hakkında daha fazla bilgi için bkz. [.NET Core 3,0 duyurusu](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-0/).

.NET Core RC1, Microsoft tarafından önceden hazırlanmıştı ve tam olarak desteklenmektedir. Önizleme sürümü kullanıyorsanız, devam eden destek için RTM sürümüne geçmeniz gerekir.

## <a name="language-improvements-c-80"></a>Dil geliştirmeleri C# 8,0

C# 8,0, [null olabilen başvuru türleri](../../csharp/tutorials/nullable-reference-types.md) özelliği, [zaman uyumsuz akışlar](../../csharp/tutorials/generate-consume-asynchronous-stream.md)ve [daha fazla desen](../../csharp/tutorials/pattern-matching.md)içeren bu sürümün bir parçasıdır. C# 8,0 özellikleri hakkında daha fazla bilgi için bkz. [c# 8,0 ' deki](../../csharp/whats-new/csharp-8.md)yenilikler.

Aşağıda ayrıntılı olarak açıklanan aşağıdaki API özelliklerini desteklemek için dil geliştirmeleri eklenmiştir:

- [Aralıklar ve dizinler](#ranges-and-indices)
- [Zaman uyumsuz akışlar](#async-streams)

## <a name="net-standard-21"></a>.NET Standard 2,1

.NET Core 3,0 **.NET Standard 2,1**uygular. Ancak, varsayılan `dotnet new classlib` şablon hala **.NET Standard 2,0**' i hedefleyen bir proje oluşturur. **.NET Standard 2,1**' i hedeflemek için proje dosyanızı düzenleyin ve özelliği şu `TargetFramework` şekilde değiştirin `netstandard2.1` :

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <TargetFramework>netstandard2.1</TargetFramework>
  </PropertyGroup>

</Project>
```

Visual Studio kullanıyorsanız, Visual Studio 2017 **.NET Standard 2,1** veya **.NET Core 3,0**' i desteklemediğinden [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019)gerekir.

## <a name="compiledeploy"></a>Derle/dağıt

### <a name="default-executables"></a>Varsayılan yürütülebilir dosyalar

.NET Core artık [çerçeveye bağlı yürütülebilir dosyaları](../deploying/index.md#publish-framework-dependent) varsayılan olarak oluşturur. Bu davranış, .NET Core 'un küresel olarak yüklenen bir sürümünü kullanan uygulamalar için yenidir. Daha önce yalnızca [kendi kendine kapsanan dağıtımlar](../deploying/index.md#publish-self-contained) yürütülebilir bir dosya üretecektir.

`dotnet build`Veya sırasında `dotnet publish` , kullanmakta olduğunuz SDK ortamı ve platformuyla eşleşen bir çalıştırılabilir ( **appHost**olarak bilinir) oluşturulur. Bu yürütülebilir dosyalarla aynı şeyleri, diğer yerel yürütülebilir dosyaları gibi bekleyebilir, örneğin:

- Yürütülebilir dosyaya çift tıklayabilirsiniz.
- Uygulamayı `myapp.exe` Windows ve `./myapp` Linux ve MacOS gibi bir komut isteminden doğrudan başlatabilirsiniz.

### <a name="macos-apphost-and-notarization"></a>macOS appHost ve notarlama

*yalnızca macOS*

MacOS için .NET Core SDK 3,0 ' den başlayarak, varsayılan bir yürütülebilir dosya (appHost olarak bilinir) oluşturma ayarı varsayılan olarak devre dışıdır. Daha fazla bilgi için bkz. [MacOS Catalina Notarleştirme ve .NET Core indirmeleri ve projeleri üzerindeki etki](../install/macos-notarization-issues.md).

AppHost ayarı etkinleştirildiğinde, .NET Core, oluşturduğunuzda veya yayımladığınızda yerel bir MAK-O çalıştırılabilir dosyası oluşturur. Uygulamanız, komutuyla kaynak koddan çalıştırıldığında `dotnet run` veya mak-O yürütülebilir dosyasını doğrudan başlatarak appHost bağlamında çalışır.

AppHost olmadan, bir kullanıcıya [çerçeveye bağımlı](../deploying/index.md#publish-framework-dependent) bir uygulama başlatabilir tek yöntem `dotnet <filename.dll>` komutunu kullanabilirsiniz. Uygulamanızı [kendi içinde](../deploying/index.md#publish-self-contained)yayımladığınızda her zaman bir appHost oluşturulur.

AppHost 'yi proje düzeyinde yapılandırabilir veya parametresi ile belirli bir komut için appHost ' ı kapatabilirsiniz `dotnet` `-p:UseAppHost` :

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

Ayarı hakkında daha fazla bilgi için `UseAppHost` bkz. [MICROSOFT. net. SDK için MSBuild özellikleri](../project-sdk/msbuild-props.md#useapphost).

### <a name="single-file-executables"></a>Tek dosya yürütülebilir dosyaları

`dotnet publish`Komut, uygulamanızı platforma özgü tek dosya yürütülebilir dosyasına paketlemeyi destekler. Yürütülebilir dosya kendiliğinden ayıklanıyor ve uygulamanızı çalıştırmak için gerekli tüm bağımlılıkları (yerel dahil) içerir. Uygulama ilk kez çalıştırıldığında uygulama adı ve derleme tanımlayıcısı temelinde bir dizine çıkarılır. Uygulama yeniden çalıştırıldığında başlatma daha hızlıdır. Yeni bir sürüm kullanılmadığı takdirde uygulamanın kendisi ikinci kez ayıklanmasına gerek yoktur.

Tek dosya yürütülebiliri yayımlamak için, `PublishSingleFile` projenizdeki öğesini veya komut satırında `dotnet publish` komutunu komutuyla ayarlayın:

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

Tek dosya yayınlama hakkında daha fazla bilgi için bkz. [tek dosya paketcisi tasarım belgesi](https://github.com/dotnet/designs/blob/master/accepted/2020/single-file/design.md).

### <a name="assembly-linking"></a>Bütünleştirilmiş kod bağlama

.NET Core 3,0 SDK, Il 'yi çözümleyerek ve kullanılmayan derlemeleri kırparak uygulamaların boyutunu azaltan bir araçla birlikte gelir.

Bağımsız uygulamalar, kodunuzun çalıştırılması için gereken her şeyi, ana bilgisayara .NET yüklenmesini gerektirmeden içerir. Ancak, çoğu zaman uygulamanın çalışması için yalnızca küçük bir çerçeve alt kümesi gerekir ve kullanılmayan diğer kitaplıklar da kaldırılabilir.

.NET Core artık uygulamanızın Il 'sini taramak için [Il bağlayıcı](https://github.com/mono/linker) aracını kullanacak bir ayar içeriyor. Bu araç hangi kodun gerekli olduğunu algılar ve ardından kullanılmayan kitaplıkları kırpar. Bu araç bazı uygulamaların dağıtım boyutunu önemli ölçüde azaltabilir.

Bu aracı etkinleştirmek için `<PublishTrimmed>` projenize ayarı ekleyin ve kendi içinde bulunan bir uygulamayı yayımlayın:

```xml
<PropertyGroup>
  <PublishTrimmed>true</PublishTrimmed>
</PropertyGroup>
```

```dotnetcli
dotnet publish -r <rid> -c Release
```

Örnek olarak, yayımlanan temel "Merhaba Dünya" yeni konsol projesi şablonu, yayımlandığında 70 MB ile çarpılır. Kullanarak `<PublishTrimmed>` , bu boyut yaklaşık 30 MB 'ye indirilir.

Yansıma veya ilgili dinamik özellikleri kullanan uygulamaların veya çerçevelerin (ASP.NET Core ve WPF dahil) genellikle kırpıldığına göre kesilmesini göz önünde bulundurmanız önemlidir. Bu ayırıcı, bağlayıcının bu dinamik davranış hakkında bilgi sahibi olmadığı ve yansıma için hangi çerçeve türlerinin gerekli olduğunu belirleyemediği için oluşur. Il bağlayıcı aracı, bu senaryonun farkında olacak şekilde yapılandırılabilir.

Tüm diğerleri üzerinde, kırpdıktan sonra uygulamanızı test ettiğinizden emin olun.

Il bağlayıcı aracı hakkında daha fazla bilgi için [belgelere](../deploying/trim-self-contained.md) bakın veya [mono/bağlayıcı]( https://github.com/mono/linker) deposunu ziyaret edin.

### <a name="tiered-compilation"></a>Katmanlı derleme

[Katmanlı derleme](https://github.com/dotnet/runtime/blob/master/docs/design/features/tiered-compilation.md) (TC), .net Core 3,0 ile varsayılan olarak açık olur. Bu özellik, çalışma zamanının daha iyi performans elde etmek için tam zamanında (JıT) derleyicisini daha kolay bir şekilde kullanmasına olanak sağlar.

Katmanlı derlemenin başlıca avantajı, daha düşük kalitede, ancak daha hızlı bir katmanda ya da daha yüksek kalitede, ancak daha yavaş bir katmanda çeşitli yöntemler elde etmenin iki yolunu sağlamaktır. Kalite, yöntemin en iyi duruma getirilmiş olduğunu gösterir. TC, düzenli bir durum aracılığıyla başlangıçtan itibaren çeşitli yürütme aşamalarından geçen bir uygulamanın performansını artırmaya yardımcı olur. Katmanlı derleme devre dışı bırakıldığında, her yöntem, başlangıç performansı üzerinden düzenli durum performansına yol gösteren tek bir şekilde derlenir.

TC etkinleştirildiğinde, bir uygulama başlatıldığında Yöntem derlemesi için aşağıdaki davranış geçerlidir:

- Metodun önceden derlenen kodu veya [Readytorun](#readytorun-images)varsa, önceden oluşturulan kod kullanılır.
- Aksi halde, yöntemi jmesdir. Genellikle, bu yöntemler değer türleri üzerinde genel türlerdir.
  - *Hızlı JIT* daha hızlı (veya daha az iyileştirilmiş) kod üretir. .NET Core 3,0 ' de hızlı JıT, döngüler içermeyen ve başlangıç sırasında tercih edilen yöntemler için varsayılan olarak etkindir.
  - JıT 'i tamamen en iyi duruma getirmek daha yavaş daha yavaş (veya daha iyileştirilmiş) kod üretir. Hızlı JıT 'in kullanılacağı yöntemler için (örneğin, yöntemi ile ilişkilendirilebildiği <xref:System.Runtime.CompilerServices.MethodImplOptions.AggressiveOptimization?displayProperty=nameWithType> ), JIT tam olarak iyileştiriliyor kullanılır.

Sık çağrılan yöntemler için, tam zamanında derleyici arka planda tamamen iyileştirilmiş kod oluşturur. En iyi duruma getirilmiş kod daha sonra bu yöntem için önceden derlenmiş kodun yerini alır.

Hızlı JıT tarafından oluşturulan kod daha yavaş çalışabilir, daha fazla bellek ayırabilir veya daha fazla yığın alanı kullanabilir. Sorunlar varsa, proje dosyasında bu MSBuild özelliğini kullanarak hızlı JıT 'i devre dışı bırakabilirsiniz:

```xml
<PropertyGroup>
  <TieredCompilationQuickJit>false</TieredCompilationQuickJit>
</PropertyGroup>
```

TC 'yi tamamen devre dışı bırakmak için, proje dosyanızda bu MSBuild özelliğini kullanın:

```xml
<PropertyGroup>
  <TieredCompilation>false</TieredCompilation>
</PropertyGroup>
```

> [!TIP]
> Bu ayarları proje dosyasında değiştirirseniz, yeni ayarların yansıtılması için temiz bir derleme gerçekleştirmeniz gerekebilir ( `obj` ve `bin` dizinleri silin ve yeniden oluşturun).

Çalışma zamanında derlemeyi yapılandırma hakkında daha fazla bilgi için bkz. [derleme Için çalışma zamanı yapılandırma seçenekleri](../run-time-config/compilation.md).

### <a name="readytorun-images"></a>ReadyToRun görüntüleri

Uygulama derlemelerinizi ReadyToRun (R2R) biçiminde derleyerek .NET Core uygulamanızın başlama süresini geliştirebilirsiniz. R2R, bir süre öncesi (AOT) derleme biçimidir.

R2R ikilileri, tam zamanında (JıT) derleyicisinin uygulamanız yüklenirken yapması gereken iş miktarını azaltarak başlangıç performansını geliştirir. İkililer, JıT 'in üretmesine kıyasla benzer yerel kod içerir. Ancak, R2R ikilileri, bazı senaryolar için hala gerekli olan hem ara dil (IL) kodunu hem de aynı kodun yerel sürümünü içerdiğinden, daha büyüktür. R2R yalnızca, Linux x64 veya Windows x64 gibi belirli çalışma zamanı ortamlarını (RID) hedefleyen bir kendi içinde bulunan uygulamayı yayımladığınızda kullanılabilir.

Projenizi ReadyToRun olarak derlemek için aşağıdakileri yapın:

01. `<PublishReadyToRun>`Ayarı projenize ekleyin:

    ```xml
    <PropertyGroup>
      <PublishReadyToRun>true</PublishReadyToRun>
    </PropertyGroup>
    ```

01. Kendi içinde bir uygulama yayımlayın. Örneğin, bu komut Windows 'un 64 bit sürümü için kendi kendine içerilen bir uygulama oluşturur:

    ```dotnetcli
    dotnet publish -c Release -r win-x64 --self-contained
    ```

#### <a name="cross-platformarchitecture-restrictions"></a>Platformlar arası/mimari kısıtlamaları

ReadyToRun derleyicisi Şu anda çapraz hedefleme 'yi desteklememektedir. Belirli bir hedefte derleme yapmanız gerekir. Örneğin, R2R görüntülerini Windows x64 için istiyorsanız, bu ortamda Yayımla komutunu çalıştırmanız gerekir.

Çapraz hedefleme için özel durumlar:

- Windows x64, Windows ARM32, ARM64 ve x86 görüntülerini derlemek için kullanılabilir.
- Windows x86, Windows ARM32 görüntülerini derlemek için kullanılabilir.
- Linux x64, Linux ARM32 ve ARM64 görüntülerini derlemek için kullanılabilir.

## <a name="runtimesdk"></a>Çalışma zamanı/SDK

### <a name="major-version-runtime-roll-forward"></a>Büyük sürüm çalışma zamanı ileri

.NET Core 3,0, uygulamanızın .NET Core 'un en son ana sürümüne iletmesini sağlayan bir katılım özelliği sunar. Ayrıca, geri alma 'nın uygulamanıza nasıl uygulandığını denetlemek için yeni bir ayar eklenmiştir. Bu, aşağıdaki yollarla yapılandırılabilir:

- Proje dosyası özelliği: `RollForward`
- Çalışma zamanı yapılandırma dosyası özelliği: `rollForward`
- Ortam değişkeni: `DOTNET_ROLL_FORWARD`
- Komut satırı bağımsız değişkeni: `--roll-forward`

Aşağıdaki değerlerden biri belirtilmelidir. Ayar atlanırsa, **İkincil** varsayılandır.

- **LatestPatch**\
En yüksek düzeltme eki sürümüne ilet. Bu, ikincil sürüm iletmeyi devre dışı bırakır.
- **Bazı**\
İstenen alt sürüm eksikse, en düşük düzeydeki sürüme ilet. İstenen ikincil sürüm varsa, **Latestpatch** ilkesi kullanılır.
- **Leri**\
İstenen ana sürüm eksikse, en düşük büyük sürüme ve en düşük alt sürüme ileri doğru alın. İstenen ana sürüm varsa, **İkincil** ilke kullanılır.
- **LatestMinor**\
İstenen alt sürüm mevcut olsa bile en yüksek düzeyde alt sürüme ilet. Bileşen barındırma senaryolarına yöneliktir.
- **Latestana**\
İstenen ana mevcut olsa bile, en yüksek büyük ve en yüksek düzeyde alt sürüme ilet. Bileşen barındırma senaryolarına yöneliktir.
- **Dıı**\
İleri alma. Yalnızca belirtilen sürüme bağlayın. Bu ilke, en son düzeltme eklerine iletme özelliğini devre dışı bıraktığından genel kullanım için önerilmez. Bu değer yalnızca test için önerilir.

**Devre dışı bırak** ayarının yanı sıra, tüm ayarlar kullanılabilir en yüksek düzeltme eki sürümünü kullanacaktır.

Varsayılan olarak, istenen sürüm ( `.runtimeconfig.json` uygulama için belirtilen şekilde) bir yayın sürümündedir, yalnızca yayın sürümleri öne çıkarak kabul edilir. Yayın öncesi sürümler yok sayılır. Eşleşen bir yayın sürümü yoksa, yayın öncesi sürümler hesaba alınır. Bu davranış ayarıyla değiştirilebilir `DOTNET_ROLL_FORWARD_TO_PRERELEASE=1` , bu durumda tüm sürümler her zaman göz önünde bulundurulmalıdır.

### <a name="build-copies-dependencies"></a>Derleme kopyaları bağımlılıkları

`dotnet build`Komut artık, NuGet önbelleğinden uygulamanızın NuGet bağımlılıklarını yapı çıkış klasörüne kopyalar. Daha önce bağımlılıklar yalnızca bir parçası olarak kopyalandı `dotnet publish` .

Bağlama ve Razor sayfası yayımlama gibi bazı işlemler, yayımlamayı gerektirecek şekilde devam eder.

### <a name="local-tools"></a>Yerel Araçlar

.NET Core 3,0 yerel araçları tanıtır. Yerel Araçlar [genel araçlara](../tools/global-tools.md) benzerdir, ancak diskte belirli bir konum ile ilişkilendirilir. Yerel araçlar küresel olarak kullanılabilir değildir ve NuGet paketleri olarak dağıtılır.

> [!WARNING]
> .NET Core 3,0 Preview 1 ' de veya çalıştıran gibi yerel araçlara çalıştıysanız, `dotnet tool restore` `dotnet tool install` Yerel araçlar önbellek klasörünü silin. Aksi takdirde, yerel araçlar yeni bir sürümde çalışmaz. Bu klasör şu konumda bulunur:
>
> MacOS 'ta Linux: `rm -r $HOME/.dotnet/toolResolverCache`
>
> Windows 'da: `rmdir /s %USERPROFILE%\.dotnet\toolResolverCache`

Yerel araçlar, geçerli dizininizde bir bildirim dosyası adına bağımlıdır `dotnet-tools.json` . Bu bildirim dosyası, bu klasörde ve altında kullanılabilecek araçları tanımlar. Kodunuzla çalışan herkesin aynı araçları geri yükleyip kullanabilmesini sağlamak için, bildirim dosyasını kodunuzla dağıtabilirsiniz.

Hem genel hem de yerel araçlar için, çalışma zamanının uyumlu bir sürümü gereklidir. Şu anda NuGet.org hedef .NET Core çalışma zamanı 2,1 ' de birçok araç. Bu araçları küresel olarak veya yerel olarak yüklemek için, hala [NET Core 2,1 çalışma zamanını](https://dotnet.microsoft.com/download/dotnet-core/2.1)yüklemeniz gerekir.

### <a name="new-globaljson-options"></a>Seçenekler üzerinde yeni global.js

Dosya *global.js* , .NET Core SDK hangi sürümünün kullanıldığını tanımlamaya çalışırken daha fazla esneklik sağlayan yeni seçeneklere sahiptir. Yeni seçenekler şunlardır:

- `allowPrerelease`: SDK Çözümleyicisinin kullanılacak SDK sürümünü seçerken yayın öncesi sürümlerini düşünmesinin gerekip gerekmediğini belirtir.
- `rollForward`: Bir SDK sürümü seçerken kullanılacak yuvarlama ilkesini, belirli bir SDK sürümü eksik olduğunda geri dönüş olarak veya daha yüksek bir sürümü kullanmak için bir yönerge olarak gösterir.

Varsayılan değerler, desteklenen değerler ve yeni eşleştirme kuralları gibi değişiklikler hakkında daha fazla bilgi için bkz. [global.jsgenel bakış](../tools/global-json.md).

### <a name="smaller-garbage-collection-heap-sizes"></a>Daha küçük atık toplama yığın boyutları

Atık toplayıcısının varsayılan yığın boyutu daha az bellek kullanan .NET Core ile sonuçlanır. Bu değişiklik, modern işlemci önbelleği boyutları ile nesil 0 ayırma bütçesine göre daha iyi hizalanır.

### <a name="garbage-collection-large-page-support"></a>Çöp toplama büyük sayfa desteği

Büyük sayfalar (Linux 'ta çok büyük sayfalar olarak da bilinir), işletim sisteminin bu büyük sayfaları isteyen uygulamanın performansını artırmak için yerel sayfa boyutundan (genellikle 4K) daha büyük bellek bölgeleri ayarlayabildiği bir özelliktir.

Çöp toplayıcı artık Windows üzerinde büyük sayfalar ayırmayı seçmek için bir katılım özelliği olarak **Gclargepages** ayarıyla yapılandırılabilir.

## <a name="windows-desktop--com"></a>Windows Masaüstü & COM

### <a name="net-core-sdk-windows-installer"></a>.NET Core SDK Windows Installer

Windows için MSI Yükleyicisi, .NET Core 3,0 ile başlayarak değiştirilmiştir. SDK yükleyicileri artık SDK özelliği bant sürümlerini yerinde yükseltecektir. Özellik bantları, sürüm numarasının *Patch* bölümündeki *yüzlerce* grupta tanımlanmıştır. Örneğin, **3,0._ 101_ ** ve **3,0._ 201_ ** , 3,0 sırasında iki farklı özellik bantlarındaki sürümleridir **._ 101_ ** ve **3,0._ 199_ ** aynı özellik bandında. .NET Core SDK **3,0 olduğunda._ 101_ ** .NET Core SDK yüklendi, **3,0._ 100_ ** , varsa makineden kaldırılacak. .NET Core SDK **3,0._ 200_ ** , .NET Core SDK 3,0 ' de aynı makineye yüklendi **._ 101_ ** kaldırılmaz.

Sürüm oluşturma hakkında daha fazla bilgi için bkz. [.NET Core 'un sürümü oluşturma konusuna genel bakış](../versions/index.md).

### <a name="windows-desktop"></a>Windows masaüstü

.NET Core 3,0, Windows Presentation Foundation (WPF) ve Windows Forms kullanarak Windows masaüstü uygulamalarını destekler. Bu çerçeveler ayrıca, Windows UI XAML kitaplığı 'ndan (WinUI) [xaml Adaları](/windows/uwp/xaml-platform/xaml-host-controls)aracılığıyla modern denetimleri ve akıcı stil oluşturmayı da destekler.

Windows Masaüstü bileşeni, Windows .NET Core 3,0 SDK 'sının bir parçasıdır.

Aşağıdaki komutlarla yeni bir WPF veya Windows Forms uygulaması oluşturabilirsiniz `dotnet` :

```dotnetcli
dotnet new wpf
dotnet new winforms
```

Visual Studio 2019, .NET Core 3,0 Windows Forms ve WPF için **Yeni proje** şablonları ekler.

Mevcut bir .NET Framework uygulamasının bağlantı noktası hakkında daha fazla bilgi için bkz. [bağlantı noktası WPF projeleri](../../desktop-wpf/migration/convert-project-from-net-framework.md) ve [bağlantı noktası Windows Forms projeleri](../porting/winforms.md).

#### <a name="winforms-high-dpi"></a>WinForms yüksek DPı

.NET Core Windows Forms uygulamaları, ile yüksek DPı modunu ayarlayabilir <xref:System.Windows.Forms.Application.SetHighDpiMode(System.Windows.Forms.HighDpiMode)?displayProperty=nameWithType> . Bu `SetHighDpiMode` Yöntem, daha `App.Manifest` önce veya P/Invoke gibi diğer yollarla ayarlanmadığı takdirde, karşılık gelen yüksek DPI modunu ayarlar `Application.Run` .

`highDpiMode`Sabit listesi tarafından ifade edilen olası değerler <xref:System.Windows.Forms.HighDpiMode?displayProperty=nameWithType> şunlardır:

- `DpiUnaware`
- `SystemAware`
- `PerMonitor`
- `PerMonitorV2`
- `DpiUnawareGdiScaled`

Yüksek DPı modları hakkında daha fazla bilgi için bkz. [Windows 'Da yüksek DPI Masaüstü uygulama geliştirme](/windows/desktop/hidpi/high-dpi-desktop-application-development-on-windows).

### <a name="create-com-components"></a>COM bileşenleri oluşturma

Windows 'ta artık COM çağrılabilir yönetilen bileşenler oluşturabilirsiniz. Bu özellik, .NET Core 'un COM eklenti modelleriyle kullanılması ve ayrıca .NET Framework eşlik sağlanması açısından önemlidir.

*mscoree.dll* com sunucusu olarak kullanıldığı .NET Framework aksine, .NET Core, com bileşenini oluştururken *bin* dizinine yerel bir başlatıcı dll 'si ekler.

COM bileşeni oluşturma ve kullanma hakkında bir örnek için bkz. [com tanıtımı](https://github.com/dotnet/samples/tree/master/core/extensions/COMServerDemo).

### <a name="windows-native-interop"></a>Windows yerel birlikte çalışma

Windows, düz C API 'Leri, COM ve WinRT biçiminde zengin bir yerel API sunar. .NET Core **P/Invoke**'ı destekleirken, .net Core 3,0, **com API 'Leri oluşturma** ve **WinRT API 'leri etkinleştirme**özelliğini ekler. Kod örneği için bkz. [Excel tanıtımı](https://github.com/dotnet/samples/tree/master/core/extensions/ExcelDemo).

### <a name="msix-deployment"></a>MSIX dağıtımı

[Msix](/windows/msix/) yeni bir Windows uygulama paketi biçimidir. .NET Core 3,0 masaüstü uygulamalarını Windows 10 ' a dağıtmak için kullanılabilir.

Visual Studio 2019 ' de bulunan [Windows uygulama paketleme projesi](/windows/uwp/porting/desktop-to-uwp-packaging-dot-net), [kendi kendine içerilen](../deploying/index.md#publish-self-contained) .NET Core uygulamalarıyla msix paketi oluşturmanıza olanak sağlar.

.NET Core proje dosyası, özelliğindeki desteklenen çalışma zamanlarını belirtmelidir `<RuntimeIdentifiers>` :

```xml
<RuntimeIdentifiers>win-x86;win-x64</RuntimeIdentifiers>
```

## <a name="linux-improvements"></a>Linux geliştirmeleri

### <a name="serialport-for-linux"></a>Linux için SerialPort

.NET Core 3,0, Linux üzerinde için temel desteği sağlar <xref:System.IO.Ports.SerialPort?displayProperty=nameWithType> .

Daha önce, .NET Core yalnızca `SerialPort` Windows 'da kullanımı desteklenir.

Linux 'ta seri bağlantı noktası için sınırlı destek hakkında daha fazla bilgi için bkz. [GitHub sorun #33146](https://github.com/dotnet/corefx/issues/33146).

### <a name="docker-and-cgroup-memory-limits"></a>Docker ve cgroup bellek sınırları

Docker ile Linux üzerinde .NET Core 3,0 çalıştırmak, cgroup bellek limitleriyle daha iyi çalışır. İle gibi bellek limitleriyle bir Docker kapsayıcısı çalıştırmak `docker run -m` , .NET Core 'un davranış şeklini değiştirir.

- Varsayılan atık toplayıcı (GC) yığın boyutu: kapsayıcıda bellek sınırının en fazla 20 MB veya %75 ' si.
- Açık Boyut, mutlak bir sayı veya cgroup sınırının yüzdesi olarak ayarlanabilir.
- GC yığını başına en düşük ayrılmış kesim boyutu 16 MB 'tır. Bu boyut, makinelerde oluşturulan Heap sayısını azaltır.

### <a name="gpio-support-for-raspberry-pi"></a>Raspberry PI için GıO desteği

NuGet 'e GıO programlama için kullanabileceğiniz iki paket yayımlanmıştır:

- [System. Device. GIO](https://www.nuget.org/packages/System.Device.Gpio)
- [IoT. Device. Bindings](https://www.nuget.org/packages/Iot.Device.Bindings)

GPıO paketleri, *GIO*, *SPI*, *I2C*ve *PWM* cihazları için API 'ler içerir. IoT bağlamaları paketi cihaz bağlamalarını içerir. Daha fazla bilgi için bkz. [cihaz GitHub deposu](https://github.com/dotnet/iot/blob/master/src/devices/).

### <a name="arm64-linux-support"></a>ARM64 Linux desteği

.NET Core 3,0, Linux için ARM64 desteği ekler. ARM64 için birincil kullanım örneği şu anda IoT senaryolarıyla birlikte. Daha fazla bilgi için bkz. [.NET Core ARM64 Status](https://github.com/dotnet/announcements/issues/82).

[ARM64 üzerinde .NET Core Için Docker görüntüleri](https://hub.docker.com/r/microsoft/dotnet/) alp, de, ve Ubuntu için kullanılabilir.

> [!NOTE]
> **ARM64** Windows desteği henüz kullanılamıyor.

## <a name="security"></a>Güvenlik

### <a name="tls-13--openssl-111-on-linux"></a>TLS 1,3 & Linux üzerinde OpenSSL 1.1.1

.NET Core artık, belirli bir ortamda kullanılabildiği [OpenSSL 1.1.1 Içindeki TLS 1,3 desteğinin](https://www.openssl.org/blog/blog/2018/09/11/release111/)avantajlarından yararlanır. TLS 1,3:

- İstemci ve sunucu arasında gereken azaltılan gidiş dönüşlerle bağlantı süreleri geliştirildi.
- Kullanılmayan ve güvenli olmayan şifreleme algoritmalarının kaldırılması nedeniyle güvenlik geliştirildi.

Kullanılabilir olduğunda, .NET Core 3,0 bir Linux sisteminde **OpenSSL 1.1.1**, **OpenSSL 1.1.0**veya **OpenSSL 1.0.2** kullanır. **OpenSSL 1.1.1** kullanılabilir olduğunda, her ikisi <xref:System.Net.Security.SslStream?displayProperty=nameWithType> de <xref:System.Net.Http.HttpClient?displayProperty=nameWithType> tür **TLS 1,3** kullanır (istemci ve sunucunun **TLS 1,3**' i desteklediği varsayıldığında).

> [!IMPORTANT]
> Windows ve macOS henüz **TLS 1,3**' i desteklemez. .NET Core 3,0, destek kullanılabilir hale geldiğinde bu işletim sistemlerinde **TLS 1,3** ' i destekleyecektir.

Aşağıdaki C# 8,0 örneği, ' a bağlanan Ubuntu 18,10 üzerinde .NET Core 3,0 ' i göstermektedir <https://www.cloudflare.com> :

[!code-csharp[TLSExample](./snippets/dotnet-core-3-0/csharp/TLS.cs#TLS)]

### <a name="cryptography-ciphers"></a>Şifreleme şifrelemeleri

.NET 3,0, ile ve sırasıyla uygulanan **AES-GCM** ve **AES-CCM** şifrelemeleri için destek ekler <xref:System.Security.Cryptography.AesGcm?displayProperty=nameWithType> <xref:System.Security.Cryptography.AesCcm?displayProperty=nameWithType> . Bu algoritmalar, [Ilişki verileri (AEAD) algoritmalarıyla kimliği doğrulanmış şifrelemedir](https://en.wikipedia.org/wiki/Authenticated_encryption).

Aşağıdaki kod, `AesGcm` rastgele verileri şifrelemek ve şifrelerini çözmek için şifre kullanımını gösterir.

[!code-csharp[AesGcm](./snippets/dotnet-core-3-0/csharp/Cipher.cs#AesGcm)]

### <a name="cryptographic-key-importexport"></a>Şifreleme anahtarı Içeri/dışarı aktarma

.NET Core 3,0, asimetrik ortak ve özel anahtarların standart biçimlerden içeri ve dışarı aktarılmasını destekler. X. 509.440 sertifikası kullanmanız gerekmez.

*RSA*, *dsa*, *ECDSA*ve *ecdıfıfiehellman*gibi tüm anahtar türleri aşağıdaki biçimleri destekler:

- **Ortak Anahtar**
  - X. 509.440 Subjectpublickeyınfo

- **Özel anahtar**
  - PKCS # 8 Privatekeyınfo
  - PKCS # 8 Encryptedprivatekeyınfo

RSA anahtarları da şunları destekler:

- **Ortak Anahtar**
  - PKCS # 1 RSAPublicKey

- **Özel anahtar**
  - PKCS # 1 RSAPrivateKey

Dışarı aktarma yöntemleri DER kodlu ikili veriler oluşturur ve içeri aktarma yöntemleri aynı şekilde bekler. Bir anahtar, metin kullanımı kolay pek biçiminde depolanıyorsa, bir içeri aktarma yöntemi çağrılmadan önce çağıranın içerik Base64 olarak çözülmesi gerekecektir.

[!code-csharp[RSA](./snippets/dotnet-core-3-0/csharp/RSA.cs#Rsa)]

**PKCS # 8** dosyaları ile incelenebilir <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo?displayProperty=nameWithType> ve **PFX/PKCS # 12** dosyaları ile incelenebilir <xref:System.Security.Cryptography.Pkcs.Pkcs12Info?displayProperty=nameWithType> . **PFX/PKCS # 12** dosyaları ile değiştirilebilir <xref:System.Security.Cryptography.Pkcs.Pkcs12Builder?displayProperty=nameWithType> .

## <a name="net-core-30-api-changes"></a>.NET Core 3,0 API değişiklikleri

### <a name="ranges-and-indices"></a>Aralıklar ve dizinler

Yeni <xref:System.Index?displayProperty=nameWithType> tür dizin oluşturmak için kullanılabilir. `int`Başlangıçtan başlayarak bu saylardan bir tane veya sonundan daha fazla `^` sayan bir önek Işleci (C#) oluşturabilirsiniz:

```csharp
Index i1 = 3;  // number 3 from beginning
Index i2 = ^4; // number 4 from end
int[] a = { 0, 1, 2, 3, 4, 5, 6, 7, 8, 9 };
Console.WriteLine($"{a[i1]}, {a[i2]}"); // "3, 6"
```

Ayrıca, <xref:System.Range?displayProperty=nameWithType> `Index` biri başlangıç ve diğeri bitiş için olmak üzere iki değerden oluşan ve bir `x..y` Aralık Ifadesiyle (C#) yazılabilir bir tür de vardır. Daha sonra bir dilim üreten bir ile dizin oluşturabilirsiniz `Range` :

```csharp
var slice = a[i1..i2]; // { 3, 4, 5 }
```

Daha fazla bilgi için [aralıklar ve dizinler öğreticisine](../../csharp/tutorials/ranges-indexes.md)bakın.

### <a name="async-streams"></a>Zaman uyumsuz akışlar

<xref:System.Collections.Generic.IAsyncEnumerable%601>Türü yeni bir zaman uyumsuz sürümüdür <xref:System.Collections.Generic.IEnumerable%601> . Dil, `await foreach` `IAsyncEnumerable<T>` öğelerini tüketmek ve `yield return` öğeleri oluşturmak için bunları kullanmak için kullanabilirsiniz.

Aşağıdaki örnek, zaman uyumsuz akışların hem üretimini hem de tüketimini gösterir. `foreach`Bildirim zaman uyumsuz ve kendisi `yield return` çağıranlar için zaman uyumsuz akış üretmek için kullanır. Bu model (kullanılarak `yield return` ), zaman uyumsuz akışlar üretmek için önerilen modeldir.

```csharp
async IAsyncEnumerable<int> GetBigResultsAsync()
{
    await foreach (var result in GetResultsAsync())
    {
        if (result > 20) yield return result;
    }
}
```

`await foreach`Ayrıca, zaman uyumsuz yineleyiciler da oluşturabilirsiniz, örneğin, `IAsyncEnumerable/IAsyncEnumerator` hem hem `await` de içinde kullanabileceğiniz bir yineleyici `yield` . Atılmalıdır, `IAsyncDisposable` ve gibi ÇEŞITLI BCL türlerini uygulayan ' i kullanabilirsiniz `Stream` `Timer` .

Daha fazla bilgi için bkz. [zaman uyumsuz akışlar öğreticisi](../../csharp/tutorials/generate-consume-asynchronous-stream.md).

### <a name="ieee-floating-point"></a>IEEE kayan nokta

Kayan nokta API 'Leri, [ıeee 754-2008 düzeltmesine](https://en.wikipedia.org/wiki/IEEE_754-2008_revision)uymak üzere güncelleştiriliyor. Bu değişikliklerin amacı, tüm **gerekli** işlemleri kullanıma sunmaktır ve DAVRANıŞSAL 'in IEEE spec ile uyumlu olduklarından emin olmaktır. Kayan nokta iyileştirmeleri hakkında daha fazla bilgi için bkz. [.NET Core 3,0 blog gönderisine kayan nokta ayrıştırma ve biçimlendirme geliştirmeleri](https://devblogs.microsoft.com/dotnet/floating-point-parsing-and-formatting-improvements-in-net-core-3-0/) .

Ayrıştırma ve biçimlendirme düzeltmeleri şunları içerir:

- Her uzunlukta doğru şekilde ayrıştırma ve yuvarlama girişleri.
- Doğru şekilde ayrıştırır ve negatif sıfır biçimlendirir.
- `Infinity` `NaN` Büyük/küçük harfe duyarsız bir denetim yaparak ve uygunsa isteğe bağlı olarak daha önce izin vererek doğru şekilde ayrıştırılabilir `+` .

Yeni <xref:System.Math?displayProperty=nameWithType> API 'ler şunlardır:

- <xref:System.Math.BitIncrement(System.Double)> ' <xref:System.Math.BitDecrement(System.Double)>\
`nextUp`Ve `nextDown` IEEE işlemlerine karşılık gelir. Bunlar, girdiden daha büyük veya daha az (sırasıyla) karşılaştıran en küçük kayan nokta numarasını döndürür. Örneğin, `Math.BitIncrement(0.0)` döndürür `double.Epsilon` .

- <xref:System.Math.MaxMagnitude(System.Double,System.Double)> ' <xref:System.Math.MinMagnitude(System.Double,System.Double)>\
`maxNumMag`Ve `minNumMag` IEEE işlemlerine karşılık gelen değeri, iki girişin büyüklüğüne daha büyük veya daha az (sırasıyla) döndürür. Örneğin, `Math.MaxMagnitude(2.0, -3.0)` döndürür `-3.0` .

- <xref:System.Math.ILogB(System.Double)>\
`logB`Bir integral değeri döndüren IEEE işlemine karşılık gelir, giriş parametresinin tamsayı taban 2 günlüğünü döndürür. Bu yöntem, ile aynı şekilde, `floor(log2(x))` ancak en az yuvarlama hatasıyla yapılır.

- <xref:System.Math.ScaleB(System.Double,System.Int32)>\
`scaleB`Bir tamsayı değeri alan IEEE işlemine karşılık gelir, etkin `x * pow(2, n)` olarak döner, ancak en az yuvarlama hatasıyla yapılır.

- <xref:System.Math.Log2(System.Double)>\
`log2`IEEE işlemine karşılık gelen 2 tabanında logaritmasını döndürür. Yuvarlama hatasını en aza indirir.

- <xref:System.Math.FusedMultiplyAdd(System.Double,System.Double,System.Double)>\
`fma`IEEE işlemine karşılık gelen bir fkullandınız çarpma eklemesi gerçekleştirir. Yani, `(x * y) + z` tek bir işlem olarak yapılır, böylece yuvarlama hatasını en aza indirir. Bir örnek `FusedMultiplyAdd(1e308, 2.0, -1e308)` , döndürür `1e308` . Normal `(1e308 * 2.0) - 1e308` dönüşler `double.PositiveInfinity` .

- <xref:System.Math.CopySign(System.Double,System.Double)>\
`copySign`IEEE işlemine karşılık gelir, `x` , ancak işaretini döndürür `y` .

### <a name="net-platform-dependent-intrinsics"></a>.NET platforma bağımlı Iç bilgiler

**SIMD** veya **bit işleme yönergesi** kümeleri gıbı belirli performans yönelimli CPU yönergelerine erişime izin veren API 'ler eklenmiştir. Bu yönergeler, verileri paralel şekilde işleme gibi belirli senaryolarda önemli performans geliştirmeleri elde etmenize yardımcı olabilir.

Uygun durumlarda, .NET kitaplıkları performansı artırmak için bu yönergeleri kullanmaya başlamıştır.

Daha fazla bilgi için bkz. [.net platforma bağımlı iç](https://github.com/dotnet/designs/blob/master/accepted/2018/platform-intrinsics.md)bilgiler.

### <a name="improved-net-core-version-apis"></a>Geliştirilmiş .NET Core sürümü API 'Leri

.NET Core 3,0 ile başlayarak, .NET Core ile birlikte sunulan sürüm API 'Leri artık istediğiniz bilgileri döndürür. Örnek:

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
> Son değişiklik. Bu teknik açıdan önemli bir değişiklik olduğundan, sürüm oluşturma düzeni değişti.

### <a name="fast-built-in-json-support"></a>Hızlı yerleşik JSON desteği

.NET kullanıcıları büyük ölçüde [Newtonsoft.Js](https://www.newtonsoft.com/json) ve DIĞER popüler JSON kitaplıklarında büyük bir seçenek olmaya devam eder. `Newtonsoft.Json` temel veri türü olarak .NET dizelerini kullanır, bu da arada bulunan UTF-16 ' dır.

Yeni yerleşik JSON desteği yüksek performanslı, düşük ayırma, UTF-8 kodlu JSON metniyle birlikte çalışıyor. Ad alanı ve türleri hakkında daha fazla bilgi için <xref:System.Text.Json> aşağıdaki makalelere bakın:

* [.NET 'te JSON serileştirme-genel bakış](../../standard/serialization/system-text-json-overview.md)
* [.Net 'TE JSON serileştirmek ve serisini kaldırma](../../standard/serialization/system-text-json-how-to.md).
* [Newtonsoft.Jsüzerinde System.Text.Jsüzerine geçiş](../../standard/serialization/system-text-json-migrate-from-newtonsoft-how-to.md)

### <a name="http2-support"></a>HTTP/2 desteği

<xref:System.Net.Http.HttpClient?displayProperty=nameWithType>Tür http/2 protokolünü destekler. HTTP/2 etkinse HTTP protokol sürümü TLS/ALPN aracılığıyla görüşülür ve sunucunun bunu kullanabilmesi durumunda HTTP/2 kullanılır.

Varsayılan protokol HTTP/1.1 olarak kalır, ancak HTTP/2 iki farklı şekilde etkinleştirilebilir. İlk olarak http istek iletisini HTTP/2 kullanacak şekilde ayarlayabilirsiniz:

[!code-csharp[Http2Request](./snippets/dotnet-core-3-0/csharp/http.cs#Request)]

İkincisi, <xref:System.Net.Http.HttpClient> Varsayılan olarak http/2 kullan seçeneğini kullanabilirsiniz:

[!code-csharp[Http2Client](./snippets/dotnet-core-3-0/csharp/http.cs#Client)]

Uygulama geliştirirken birçok kez şifrelenmemiş bağlantı kullanmak istersiniz. Hedef uç noktanın HTTP/2 kullanacağınızı biliyorsanız, HTTP/2 için şifrelenmemiş bağlantıları açabilirsiniz. `DOTNET_SYSTEM_NET_HTTP_SOCKETSHTTPHANDLER_HTTP2UNENCRYPTEDSUPPORT`Ortam değişkenini `1` uygulama bağlamında etkinleştirerek veya olarak ayarlayarak bu ayarı açabilirsiniz:

[!code-csharp[Http2Context](./snippets/dotnet-core-3-0/csharp/http.cs#AppContext)]

## <a name="next-steps"></a>Sonraki adımlar

- [.NET Core 2,2 ve 3,0 arasındaki son değişiklikleri gözden geçirin.](../compatibility/2.2-3.0.md)
- [Windows Forms uygulamalar için .NET Core 3,0 'deki son değişiklikleri gözden geçirin.](../compatibility/winforms.md#net-core-30)
