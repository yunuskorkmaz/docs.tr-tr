---
title: ​.NET Core 3.0’daki yenilikler
description: .NET Core 3,0 ' de bulunan yeni özellikler hakkında bilgi edinin.
dev_langs:
- csharp
- vb
author: thraka
ms.author: adegeo
ms.date: 10/22/2019
ms.openlocfilehash: dcbf1073c12650101efdcf6022db0b29ace2eb3f
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73420765"
---
# <a name="whats-new-in-net-core-30"></a>​.NET Core 3.0’daki yenilikler

Bu makalede .NET Core 3,0 ' deki yenilikler açıklanır. En büyük geliştirmelerden biri, Windows Masaüstü uygulamaları için destek içerir (yalnızca Windows). .NET Core 3,0 SDK bileşeni Windows Masaüstü 'Nü kullanarak Windows Forms ve Windows Presentation Foundation (WPF) uygulamalarınızın bağlantı noktası oluşturabilirsiniz. Temiz olması için, Windows Masaüstü bileşeni yalnızca Windows 'da desteklenir ve Windows 'a dahildir. Daha fazla bilgi için bu makalenin devamındaki [Windows Masaüstü](#windows-desktop) bölümüne bakın.

.NET Core 3,0, 8,0 için C# destek ekler. [Visual Studio 2019 sürüm 16,3](https://visualstudio.microsoft.com/vs/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) veya daha yeni bir sürümünü, [Mac için Visual Studio 8,3](/visualstudio/mac/install-preview) veya daha yenisini veya en son  **C# uzantıya**sahip [Visual Studio Code](https://code.visualstudio.com/) kullanmanız kesinlikle önerilir.

Şimdi Windows, macOS veya Linux 'ta [.NET Core 3,0 'Yi indirin ve](https://aka.ms/netcore3download) kullanmaya başlayın.

Yayın hakkında daha fazla bilgi için bkz. [.NET Core 3,0 duyurusu](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-0/).

.NET Core RC1, Microsoft tarafından önceden hazırlanmıştı ve tam olarak desteklenmektedir. Önizleme sürümü kullanıyorsanız, devam eden destek için RTM sürümüne geçmeniz gerekir.

## <a name="language-improvements-c-80"></a>Dil geliştirmeleri C# 8,0

C#8,0 Ayrıca, [null yapılabilir başvuru türleri](../../csharp/tutorials/nullable-reference-types.md) özelliği, [zaman uyumsuz akışlar](../../csharp/tutorials/generate-consume-asynchronous-stream.md)ve [daha fazla desen](../../csharp/tutorials/pattern-matching.md)içeren bu sürümün bir parçasıdır. 8,0 özellikleri hakkında C# daha fazla bilgi için bkz. [ C# 8,0](../../csharp/whats-new/csharp-8.md)sürümündeki yenilikler.

Aşağıda ayrıntılı olarak açıklanan aşağıdaki API özelliklerini desteklemek için dil geliştirmeleri eklenmiştir:

- [Aralıklar ve dizinler](#ranges-and-indices)
- [Zaman uyumsuz akışlar](#async-streams)

## <a name="net-standard-21"></a>.NET Standard 2,1

.NET Core 3,0 **.NET Standard 2,1**uygular. Ancak, varsayılan `dotnet new classlib` şablonu, hala **2,0 .NET Standard**hedefleyen bir proje oluşturur. **.NET Standard 2,1**' i hedeflemek için, proje dosyanızı düzenleyin ve `TargetFramework` özelliğini `netstandard2.1` olarak değiştirin:

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

.NET Core artık [çerçeveye bağlı yürütülebilir dosyaları](../deploying/index.md#framework-dependent-executables-fde) varsayılan olarak oluşturur. Bu davranış, .NET Core 'un küresel olarak yüklenen bir sürümünü kullanan uygulamalar için yenidir. Daha önce yalnızca [kendi kendine kapsanan dağıtımlar](../deploying/index.md#self-contained-deployments-scd) yürütülebilir bir dosya üretecektir.

`dotnet build` veya `dotnet publish`sırasında, kullanmakta olduğunuz SDK ortamı ve platformuyla eşleşen bir yürütülebilir dosya oluşturulur. Bu yürütülebilir dosyalarla aynı şeyleri, diğer yerel yürütülebilir dosyaları gibi bekleyebilir, örneğin:

- Yürütülebilir dosyaya çift tıklayabilirsiniz.
- Uygulamayı Windows üzerinde `myapp.exe` ve Linux ve macOS üzerinde `./myapp` gibi bir komut isteminden doğrudan başlatabilirsiniz.

### <a name="single-file-executables"></a>Tek dosya yürütülebilir dosyaları

`dotnet publish` komutu, uygulamanızı platforma özgü tek dosya yürütülebilir dosyasına paketlemeyi destekler. Yürütülebilir dosya kendiliğinden ayıklanıyor ve uygulamanızı çalıştırmak için gerekli tüm bağımlılıkları (yerel dahil) içerir. Uygulama ilk kez çalıştırıldığında uygulama adı ve derleme tanımlayıcısı temelinde bir dizine çıkarılır. Uygulama yeniden çalıştırıldığında başlatma daha hızlıdır. Yeni bir sürüm kullanılmadığı takdirde uygulamanın kendisi ikinci kez ayıklanmasına gerek yoktur.

Tek dosya yürütülebiliri yayımlamak için, projenizdeki `PublishSingleFile` ' ı veya komut satırında `dotnet publish` komutu ile ayarlayın:

```xml
<PropertyGroup>
  <RuntimeIdentifier>win10-x64</RuntimeIdentifier>
  <PublishSingleFile>true</PublishSingleFile>
</PropertyGroup>
```

veya

```dotnetcli
dotnet publish -r win10-x64 -p:PublishSingleFile=true
```

Tek dosya yayınlama hakkında daha fazla bilgi için bkz. [tek dosya paketcisi tasarım belgesi](https://github.com/dotnet/designs/blob/master/accepted/single-file/design.md).

### <a name="assembly-linking"></a>Bütünleştirilmiş kod bağlama

.NET Core 3,0 SDK, Il 'yi çözümleyerek ve kullanılmayan derlemeleri kırparak uygulamaların boyutunu azaltan bir araçla birlikte gelir.

Bağımsız uygulamalar, kodunuzun çalıştırılması için gereken her şeyi, ana bilgisayara .NET yüklenmesini gerektirmeden içerir. Ancak, çoğu zaman uygulamanın çalışması için yalnızca küçük bir çerçeve alt kümesi gerekir ve kullanılmayan diğer kitaplıklar da kaldırılabilir.

.NET Core artık uygulamanızın Il 'sini taramak için [Il bağlayıcı](https://github.com/mono/linker) aracını kullanacak bir ayar içeriyor. Bu araç hangi kodun gerekli olduğunu algılar ve ardından kullanılmayan kitaplıkları kırpar. Bu araç bazı uygulamaların dağıtım boyutunu önemli ölçüde azaltabilir.

Bu aracı etkinleştirmek için projenize `<PublishTrimmed>` ayarını ekleyin ve kendi içinde olan bir uygulamayı yayımlayın:

```xml
<PropertyGroup>
  <PublishTrimmed>true</PublishTrimmed>
</PropertyGroup>
```

```dotnetcli
dotnet publish -r <rid> -c Release
```

Örnek olarak, yayımlanan temel "Merhaba Dünya" yeni konsol projesi şablonu, yayımlandığında 70 MB ile çarpılır. `<PublishTrimmed>`kullanarak, bu boyut yaklaşık 30 MB 'ye indirilir.

Yansıma veya ilgili dinamik özellikleri kullanan uygulamaların veya çerçevelerin (ASP.NET Core ve WPF dahil) genellikle kırpıldığına göre kesilmesini göz önünde bulundurmanız önemlidir. Bu ayırıcı, bağlayıcının bu dinamik davranış hakkında bilgi sahibi olmadığı ve yansıma için hangi çerçeve türlerinin gerekli olduğunu belirleyemediği için oluşur. Il bağlayıcı aracı, bu senaryonun farkında olacak şekilde yapılandırılabilir.

Tüm diğerleri üzerinde, kırpdıktan sonra uygulamanızı test ettiğinizden emin olun.

Il bağlayıcı aracı hakkında daha fazla bilgi için [belgelere](https://aka.ms/dotnet-illink) bakın veya [mono/bağlayıcı]( https://github.com/mono/linker) deposunu ziyaret edin.

### <a name="tiered-compilation"></a>Katmanlı derleme

[Katmanlı derleme](https://devblogs.microsoft.com/dotnet/tiered-compilation-preview-in-net-core-2-1/) (TC), .net Core 3,0 ile varsayılan olarak açık olur. Bu özellik, çalışma zamanının daha iyi performans almak için tam zamanında (JıT) derleyicisini daha kolay bir şekilde kullanmasına olanak sağlar.

TC 'nin başlıca avantajı, daha düşük kaliteli, ancak daha hızlı bir katman veya daha yüksek kaliteli, ancak daha yavaş bir katman ile yöntemleri etkinleştirmektir (yeniden). Bu, bir uygulamanın, düzenli durum aracılığıyla başlangıçtan itibaren çeşitli yürütme aşamalarından geçerek performansını artırmaya yardımcı olur. Bu, her yöntemin tek bir şekilde (yüksek kaliteli katmanla aynı) derlenmesi ve bu durum, başlangıç performansı üzerinden kararlı bir duruma yol gösteren TC olmayan yaklaşımla karşıtdır.

Hızlı JıT 'i etkinleştirmek için (Katman 0 ile derlenen kod), proje dosyanızda bu ayarı kullanın:

```xml
<PropertyGroup>
  <TieredCompilationQuickJit>true</TieredCompilationQuickJit>
</PropertyGroup>
```

TC 'yi tamamen devre dışı bırakmak için, proje dosyanızda bu ayarı kullanın:

```xml
<TieredCompilation>false</TieredCompilation>
```

### <a name="readytorun-images"></a>ReadyToRun görüntüleri

Uygulama derlemelerinizi ReadyToRun (R2R) biçiminde derleyerek .NET Core uygulamanızın başlama süresini geliştirebilirsiniz. R2R, bir süre öncesi (AOT) derleme biçimidir.

R2R ikilileri, tam zamanında (JıT) derleyicisinin uygulamanız yüklenirken yapması gereken iş miktarını azaltarak başlangıç performansını geliştirir. İkililer, JıT 'in üretmesine kıyasla benzer yerel kod içerir. Ancak, R2R ikilileri, bazı senaryolar için hala gerekli olan hem ara dil (IL) kodunu hem de aynı kodun yerel sürümünü içerdiğinden, daha büyüktür. R2R yalnızca, Linux x64 veya Windows x64 gibi belirli çalışma zamanı ortamlarını (RID) hedefleyen bir kendi içinde bulunan uygulamayı yayımladığınızda kullanılabilir.

Projenizi ReadyToRun olarak derlemek için aşağıdakileri yapın:

01. `<PublishReadyToRun>` ayarını projenize ekleyin:

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

### <a name="major-version-roll-forward"></a>Büyük sürüm Ileri

.NET Core 3,0, uygulamanızın .NET Core 'un en son ana sürümüne iletmesini sağlayan bir katılım özelliği sunar. Ayrıca, geri alma 'nın uygulamanıza nasıl uygulandığını denetlemek için yeni bir ayar eklenmiştir. Bu, aşağıdaki yollarla yapılandırılabilir:

- Proje dosyası özelliği: `RollForward`
- Çalışma zamanı yapılandırma dosyası özelliği: `rollForward`
- Ortam değişkeni: `DOTNET_ROLL_FORWARD`
- Komut satırı bağımsız değişkeni: `--roll-forward`

Aşağıdaki değerlerden biri belirtilmelidir. Ayar atlanırsa, **İkincil** varsayılandır.

- **Latestpatch**\
En yüksek düzeltme eki sürümüne ilet. Bu, ikincil sürüm iletmeyi devre dışı bırakır.
- **Küçük**\
İstenen alt sürüm eksikse, en düşük düzeydeki sürüme ilet. İstenen ikincil sürüm varsa, **Latestpatch** ilkesi kullanılır.
- **Ana**\
İstenen ana sürüm eksikse, en düşük büyük sürüme ve en düşük alt sürüme ileri doğru alın. İstenen ana sürüm varsa, **İkincil** ilke kullanılır.
- **Latestminor**\
İstenen alt sürüm mevcut olsa bile en yüksek düzeyde alt sürüme ilet. Bileşen barındırma senaryolarına yöneliktir.
- **Latestana**\
İstenen ana mevcut olsa bile, en yüksek büyük ve en yüksek düzeyde alt sürüme ilet. Bileşen barındırma senaryolarına yöneliktir.
- \ **devre dışı bırak**
İleri alma. Yalnızca belirtilen sürüme bağlayın. Bu ilke, en son düzeltme eklerine iletme özelliğini devre dışı bıraktığından genel kullanım için önerilmez. Bu değer yalnızca test için önerilir.

**Devre dışı bırak** ayarının yanı sıra, tüm ayarlar kullanılabilir en yüksek düzeltme eki sürümünü kullanacaktır.

### <a name="build-copies-dependencies"></a>Derleme kopyaları bağımlılıkları

`dotnet build` komutu artık, NuGet önbelleğinden uygulamanızın NuGet bağımlılıklarını yapı çıkış klasörüne kopyalar. Daha önce bağımlılıklar yalnızca `dotnet publish` ' ın parçası olarak kopyalandı.

Bağlama ve Razor sayfası yayımlama gibi bazı işlemler, yayımlamayı gerektirecek şekilde devam eder.

### <a name="local-tools"></a>Yerel Araçlar

.NET Core 3,0 yerel araçları tanıtır. Yerel Araçlar [genel araçlara](../tools/global-tools.md) benzerdir, ancak diskte belirli bir konum ile ilişkilendirilir. Yerel araçlar küresel olarak kullanılabilir değildir ve NuGet paketleri olarak dağıtılır.

> [!WARNING]
> .NET Core 3,0 Preview 1 ' de `dotnet tool restore` veya `dotnet tool install` ' i çalıştırmak gibi yerel araçlar denemediyseniz, yerel araçlar önbellek klasörünü silin. Aksi takdirde, yerel araçlar yeni bir sürümde çalışmaz. Bu klasör şu konumda bulunur:
>
> MacOS 'ta Linux: `rm -r $HOME/.dotnet/toolResolverCache`
>
> Windows üzerinde: `rmdir /s %USERPROFILE%\.dotnet\toolResolverCache`

Yerel araçlar geçerli dizininizde `dotnet-tools.json` olan bir bildirim dosyası adına güvenir. Bu bildirim dosyası, bu klasörde ve altında kullanılabilecek araçları tanımlar. Kodunuzla çalışan herkesin aynı araçları geri yükleyip kullanabilmesini sağlamak için, bildirim dosyasını kodunuzla dağıtabilirsiniz.

Hem genel hem de yerel araçlar için, çalışma zamanının uyumlu bir sürümü gereklidir. Şu anda NuGet.org hedef .NET Core çalışma zamanı 2,1 ' de birçok araç. Bu araçları küresel olarak veya yerel olarak yüklemek için, hala [NET Core 2,1 çalışma zamanını](https://dotnet.microsoft.com/download/dotnet-core/2.1)yüklemeniz gerekir.

### <a name="smaller-garbage-collection-heap-sizes"></a>Daha küçük atık toplama yığın boyutları

Atık toplayıcısının varsayılan yığın boyutu daha az bellek kullanan .NET Core ile sonuçlanır. Bu değişiklik, modern işlemci önbelleği boyutları ile nesil 0 ayırma bütçesine göre daha iyi hizalanır.

### <a name="garbage-collection-large-page-support"></a>Çöp toplama büyük sayfa desteği

Büyük sayfalar (Linux 'ta çok büyük sayfalar olarak da bilinir), işletim sisteminin bu büyük sayfaları isteyen uygulamanın performansını artırmak için yerel sayfa boyutundan (genellikle 4K) daha büyük bellek bölgeleri ayarlayabildiği bir özelliktir.

Çöp toplayıcı artık Windows üzerinde büyük sayfalar ayırmayı seçmek için bir katılım özelliği olarak **Gclargepages** ayarıyla yapılandırılabilir.

## <a name="windows-desktop--com"></a>Windows Masaüstü & COM

### <a name="net-core-sdk-windows-installer"></a>.NET Core SDK Windows Installer

Windows için MSI Yükleyicisi, .NET Core 3,0 ile başlayarak değiştirilmiştir. SDK yükleyicileri artık SDK özelliği bant sürümlerini yerinde yükseltecektir. Özellik bantları, sürüm numarasının *Patch* bölümündeki *yüzlerce* grupta tanımlanmıştır. Örneğin, **3,0. _101_**  ve **3,0. _201_**  , 3,0 sırasında iki farklı özellik bantlarındaki sürümleridir **. _101_**  ve **3,0. _199_**  aynı özellik bandında. .NET Core SDK **3,0 olduğunda. _101_**  .NET Core SDK yüklendi, **3,0. _100_**  , varsa makineden kaldırılacak. .NET Core SDK **3,0. _200_**  , .NET Core SDK 3,0 ' de aynı makineye yüklendi **. _101_**  kaldırılmaz.

Sürüm oluşturma hakkında daha fazla bilgi için bkz. [.NET Core 'un sürümü oluşturma konusuna genel bakış](../versions/index.md).

### <a name="windows-desktop"></a>Windows Masaüstü

.NET Core 3,0, Windows Presentation Foundation (WPF) ve Windows Forms kullanarak Windows masaüstü uygulamalarını destekler. Bu çerçeveler ayrıca, Windows UI XAML kitaplığı 'ndan (WinUI) [xaml Adaları](/windows/uwp/xaml-platform/xaml-host-controls)aracılığıyla modern denetimleri ve akıcı stil oluşturmayı da destekler.

Windows Masaüstü bileşeni, Windows .NET Core 3,0 SDK 'sının bir parçasıdır.

Aşağıdaki `dotnet` komutlarıyla yeni bir WPF veya Windows Forms uygulaması oluşturabilirsiniz:

```dotnetcli
dotnet new wpf
dotnet new winforms
```

Visual Studio 2019, .NET Core 3,0 Windows Forms ve WPF için **Yeni proje** şablonları ekler.

Mevcut bir .NET Framework uygulamasının bağlantı noktası hakkında daha fazla bilgi için bkz. [bağlantı noktası WPF projeleri](../../desktop-wpf/migration/convert-project-from-net-framework.md) ve [bağlantı noktası Windows Forms projeleri](../porting/winforms.md).

#### <a name="winforms-high-dpi"></a>WinForms yüksek DPı

.NET Core Windows Forms uygulamaları, <xref:System.Windows.Forms.Application.SetHighDpiMode(System.Windows.Forms.HighDpiMode)?displayProperty=nameWithType> ile yüksek DPı modunu ayarlayabilir. `SetHighDpiMode` yöntemi `Application.Run`önce `App.Manifest` veya P/Invoke gibi başka yollarla ayarlanmamışsa, karşılık gelen yüksek DPı modunu ayarlar.

<xref:System.Windows.Forms.HighDpiMode?displayProperty=nameWithType> numaralandırmasında gösterildiği gibi olası `highDpiMode` değerleri şunlardır:

- `DpiUnaware`
- `SystemAware`
- `PerMonitor`
- `PerMonitorV2`
- `DpiUnawareGdiScaled`

Yüksek DPı modları hakkında daha fazla bilgi için bkz. [Windows 'Da yüksek DPI Masaüstü uygulama geliştirme](/windows/desktop/hidpi/high-dpi-desktop-application-development-on-windows).

### <a name="create-com-components"></a>COM bileşenleri oluşturma

Windows 'ta artık COM çağrılabilir yönetilen bileşenler oluşturabilirsiniz. Bu özellik, .NET Core 'un COM eklenti modelleriyle kullanılması ve ayrıca .NET Framework eşlik sağlanması açısından önemlidir.

*Mscoree. dll* ' nin com sunucusu olarak kullanıldığı .NET Framework aksine, .NET Core, com bileşenini oluştururken *bin* dizinine yerel bir başlatıcı dll 'si ekler.

COM bileşeni oluşturma ve kullanma hakkında bir örnek için bkz. [com tanıtımı](https://github.com/dotnet/samples/tree/master/core/extensions/COMServerDemo).

### <a name="windows-native-interop"></a>Windows yerel birlikte çalışma

Windows, düz C API 'Leri, COM ve WinRT biçiminde zengin bir yerel API sunar. .NET Core **P/Invoke**'ı destekleirken, .net Core 3,0, **com API 'Leri oluşturma** ve **WinRT API 'leri etkinleştirme**özelliğini ekler. Kod örneği için bkz. [Excel tanıtımı](https://github.com/dotnet/samples/tree/master/core/extensions/ExcelDemo).

### <a name="msix-deployment"></a>MSIX dağıtımı

[Msix](https://docs.microsoft.com/windows/msix/) yeni bir Windows uygulama paketi biçimidir. .NET Core 3,0 masaüstü uygulamalarını Windows 10 ' a dağıtmak için kullanılabilir.

Visual Studio 2019 ' de bulunan [Windows uygulama paketleme projesi](https://docs.microsoft.com/windows/uwp/porting/desktop-to-uwp-packaging-dot-net), [kendi kendine içerilen](../deploying/index.md#self-contained-deployments-scd) .NET Core uygulamalarıyla msix paketi oluşturmanıza olanak sağlar.

.NET Core proje dosyası `<RuntimeIdentifiers>` özelliğinde desteklenen çalışma zamanlarını belirtmelidir:

```xml
<RuntimeIdentifiers>win-x86;win-x64</RuntimeIdentifiers>
```

## <a name="linux-improvements"></a>Linux geliştirmeleri

### <a name="serialport-for-linux"></a>Linux için SerialPort

.NET Core 3,0, Linux üzerinde <xref:System.IO.Ports.SerialPort?displayProperty=nameWithType> için temel destek sağlar.

Daha önce .NET Core yalnızca Windows üzerinde `SerialPort` kullanılarak desteklenir.

Linux 'ta seri bağlantı noktası için sınırlı destek hakkında daha fazla bilgi için bkz. [GitHub sorun #33146](https://github.com/dotnet/corefx/issues/33146).

### <a name="docker-and-cgroup-memory-limits"></a>Docker ve cgroup bellek sınırları

Docker ile Linux üzerinde .NET Core 3,0 çalıştırmak, cgroup bellek limitleriyle daha iyi çalışır. `docker run -m`gibi bellek limitleriyle Docker kapsayıcısını çalıştırmak, .NET Core 'un davranış şeklini değiştirir.

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

Kullanılabilir olduğunda, .NET Core 3,0 bir Linux sisteminde **OpenSSL 1.1.1**, **OpenSSL 1.1.0**veya **OpenSSL 1.0.2** kullanır. **OpenSSL 1.1.1** kullanılabilir olduğunda, hem <xref:System.Net.Security.SslStream?displayProperty=nameWithType> hem de <xref:System.Net.Http.HttpClient?displayProperty=nameWithType> türü **TLS 1,3** kullanır (istemci ve sunucunun **TLS 1,3**' i desteklediği varsayıldığında).

>[!IMPORTANT]
>Windows ve macOS henüz **TLS 1,3**' i desteklemez. .NET Core 3,0, destek kullanılabilir hale geldiğinde bu işletim sistemlerinde **TLS 1,3** ' i destekleyecektir.

Aşağıdaki C# 8,0 örnek, <https://www.cloudflare.com> ' e bağlanırken Ubuntu 18,10 üzerinde .net Core 3,0 ' i göstermektedir:

[!CODE-csharp[TLSExample](~/samples/snippets/core/whats-new/whats-new-in-30/cs/TLS.cs#TLS)]

### <a name="cryptography-ciphers"></a>Şifreleme şifrelemeleri

.NET 3,0, sırasıyla <xref:System.Security.Cryptography.AesGcm?displayProperty=nameWithType> ve <xref:System.Security.Cryptography.AesCcm?displayProperty=nameWithType> ile uygulanan **AES-GCM** ve **AES-CCM** şifrelemeleri için destek ekler. Bu algoritmalar, [Ilişki verileri (AEAD) algoritmalarıyla kimliği doğrulanmış şifrelemedir](https://en.wikipedia.org/wiki/Authenticated_encryption).

Aşağıdaki kod, rastgele verileri şifrelemek ve şifrelerini çözmek için `AesGcm` şifre kullanımını gösterir.

[!CODE-csharp[AesGcm](~/samples/snippets/core/whats-new/whats-new-in-30/cs/Cipher.cs#AesGcm)]

### <a name="cryptographic-key-importexport"></a>Şifreleme anahtarı Içeri/dışarı aktarma

.NET Core 3,0, asimetrik ortak ve özel anahtarların standart biçimlerden içeri ve dışarı aktarılmasını destekler. X. 509.440 sertifikası kullanmanız gerekmez.

*RSA*, *dsa*, *ECDSA*ve *ecdıfıfiehellman*gibi tüm anahtar türleri aşağıdaki biçimleri destekler:

- **Ortak anahtar**
  - X. 509.440 Subjectpublickeyınfo

- **Özel anahtar**
  - PKCS # 8 Privatekeyınfo
  - PKCS # 8 Encryptedprivatekeyınfo

RSA anahtarları da şunları destekler:

- **Ortak anahtar**
  - PKCS # 1 RSAPublicKey

- **Özel anahtar**
  - PKCS # 1 RSAPrivateKey

Dışarı aktarma yöntemleri DER kodlu ikili veriler oluşturur ve içeri aktarma yöntemleri aynı şekilde bekler. Bir anahtar, metin kullanımı kolay pek biçiminde depolanıyorsa, bir içeri aktarma yöntemi çağrılmadan önce çağıranın içerik Base64 olarak çözülmesi gerekecektir.

[!CODE-csharp[RSA](~/samples/snippets/core/whats-new/whats-new-in-30/cs/RSA.cs#Rsa)]

**PKCS # 8** dosyaları <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo?displayProperty=nameWithType> ile incelenebilir ve **PFX/PKCS # 12** dosyaları <xref:System.Security.Cryptography.Pkcs.Pkcs12Info?displayProperty=nameWithType> ile incelenebilir. **PFX/PKCS # 12** dosyaları <xref:System.Security.Cryptography.Pkcs.Pkcs12Builder?displayProperty=nameWithType> ile değiştirilebilir.

## <a name="net-core-30-api-changes"></a>.NET Core 3,0 API değişiklikleri

### <a name="ranges-and-indices"></a>Aralıklar ve dizinler

Yeni <xref:System.Index?displayProperty=nameWithType> türü dizin oluşturmak için kullanılabilir. Baştan itibaren sayı olan bir `int` veya sonuna kadar olan önek `^` işleci (C#) ile bir tane oluşturabilirsiniz:

```csharp
Index i1 = 3;  // number 3 from beginning
Index i2 = ^4; // number 4 from end
int[] a = { 0, 1, 2, 3, 4, 5, 6, 7, 8, 9 };
Console.WriteLine($"{a[i1]}, {a[i2]}"); // "3, 6"
```

Ayrıca, biri başlangıç ve diğeri End için olmak üzere iki `Index` değerinden oluşan <xref:System.Range?displayProperty=nameWithType> türü de vardır ve bir `x..y` Aralık ifadesiyle (C#) yazılabilir. Daha sonra bir dilim üreten `Range` ile dizin oluşturabilirsiniz:

```csharp
var slice = a[i1..i2]; // { 3, 4, 5 }
```

Daha fazla bilgi için [aralıklar ve dizinler öğreticisine](../../csharp/tutorials/ranges-indexes.md)bakın.

### <a name="async-streams"></a>Zaman uyumsuz akışlar

<xref:System.Collections.Generic.IAsyncEnumerable%601> türü, <xref:System.Collections.Generic.IEnumerable%601>yeni bir zaman uyumsuz sürümüdür. Dil, öğelerini tüketmek için `IAsyncEnumerable<T>` `await foreach` ve öğeleri oluşturmak için `yield return` kullanmayı sağlar.

Aşağıdaki örnek, zaman uyumsuz akışların hem üretimini hem de tüketimini gösterir. `foreach` deyimleri zaman uyumsuz ve kendisi çağıranlar için zaman uyumsuz akış üretmek için `yield return` kullanır. Bu model (`yield return` kullanılarak), zaman uyumsuz akışlar üretmek için önerilen modeldir.

```csharp
async IAsyncEnumerable<int> GetBigResultsAsync()
{
    await foreach (var result in GetResultsAsync())
    {
        if (result > 20) yield return result;
    }
}
```

`await foreach`Ayrıca, zaman uyumsuz yineleyiciler oluşturabilirsiniz, örneğin, hem `await` hem de `yield` `IAsyncEnumerable/IAsyncEnumerator` döndüren bir yineleyici. Atılmalıdır nesneler için, `Stream` ve `Timer` gibi çeşitli BCL türlerini uygulayan `IAsyncDisposable` ' ı kullanabilirsiniz.

Daha fazla bilgi için bkz. [zaman uyumsuz akışlar öğreticisi](../../csharp/tutorials/generate-consume-asynchronous-stream.md).

### <a name="ieee-floating-point"></a>IEEE kayan nokta

Kayan nokta API 'Leri, [ıeee 754-2008 düzeltmesine](https://en.wikipedia.org/wiki/IEEE_754-2008_revision)uymak üzere güncelleştiriliyor. Bu değişikliklerin amacı, tüm **gerekli** işlemleri kullanıma sunmaktır ve DAVRANıŞSAL 'in IEEE spec ile uyumlu olduklarından emin olmaktır. Kayan nokta iyileştirmeleri hakkında daha fazla bilgi için bkz. [.NET Core 3,0 blog gönderisine kayan nokta ayrıştırma ve biçimlendirme geliştirmeleri](https://devblogs.microsoft.com/dotnet/floating-point-parsing-and-formatting-improvements-in-net-core-3-0/) .

Ayrıştırma ve biçimlendirme düzeltmeleri şunları içerir:

- Her uzunlukta doğru şekilde ayrıştırma ve yuvarlama girişleri.
- Doğru şekilde ayrıştırır ve negatif sıfır biçimlendirir.
- Büyük/küçük harfe duyarsız bir denetim yaparak ve uygunsa isteğe bağlı `+` ' ye izin vererek `Infinity` ve `NaN` ' i doğru ayrıştırın.

Yeni <xref:System.Math?displayProperty=nameWithType> API 'Leri şunlardır:

- <xref:System.Math.BitIncrement(System.Double)> ve <xref:System.Math.BitDecrement(System.Double)> \
`nextUp` ve `nextDown` IEEE işlemlerine karşılık gelir. Bunlar, girdiden daha büyük veya daha az (sırasıyla) karşılaştıran en küçük kayan nokta numarasını döndürür. Örneğin, `Math.BitIncrement(0.0)` `double.Epsilon` döndürür.

- <xref:System.Math.MaxMagnitude(System.Double,System.Double)> ve <xref:System.Math.MinMagnitude(System.Double,System.Double)> \
`maxNumMag` ve `minNumMag` IEEE işlemlerine karşılık gelir, iki girişin (sırasıyla) büyüklüğüne eşit veya daha küçük olan değeri döndürür. Örneğin, `Math.MaxMagnitude(2.0, -3.0)` `-3.0` döndürür.

- <xref:System.Math.ILogB(System.Double)>\
Tamsayı değer döndüren `logB` IEEE işlemine karşılık gelir, giriş parametresinin tam sayı taban-2 günlüğünü döndürür. Bu yöntem `floor(log2(x))` ile aynı şekilde aynıdır, ancak en az yuvarlama hatasıyla yapılır.

- <xref:System.Math.ScaleB(System.Double,System.Int32)>\
Tamsayı değer alan `scaleB` IEEE işlemine karşılık gelir, etkin bir `x * pow(2, n)` döndürür, ancak en az yuvarlama hatasıyla yapılır.

- <xref:System.Math.Log2(System.Double)>\
`log2` IEEE işlemine karşılık gelen, Base-2 logaritmasını döndürür. Yuvarlama hatasını en aza indirir.

- <xref:System.Math.FusedMultiplyAdd(System.Double,System.Double,System.Double)>\
`fma` IEEE işlemine karşılık gelir, bir fkullanılan çarpma eklemesi gerçekleştirir. Yani, tek bir işlem olarak `(x * y) + z`, böylece yuvarlama hatasını en aza indirir. Örneğin, `1e308` döndüren `FusedMultiplyAdd(1e308, 2.0, -1e308)` olabilir. Normal `(1e308 * 2.0) - 1e308` `double.PositiveInfinity` döndürür.

- <xref:System.Math.CopySign(System.Double,System.Double)>\
`copySign` IEEE işlemine karşılık gelen `x`değerini, ancak `y`işaretini döndürür.

### <a name="net-platform-dependent-intrinsics"></a>.NET platforma bağımlı Iç bilgiler

**SIMD** veya **bit işleme yönergesi** kümeleri gıbı belirli performans yönelimli CPU yönergelerine erişime izin veren API 'ler eklenmiştir. Bu yönergeler, verileri paralel şekilde işleme gibi belirli senaryolarda önemli performans geliştirmeleri elde etmenize yardımcı olabilir.

Uygun durumlarda, .NET kitaplıkları performansı artırmak için bu yönergeleri kullanmaya başlamıştır.

Daha fazla bilgi için bkz. [.NET platformu bağımlı iç](https://github.com/dotnet/designs/blob/master/accepted/platform-intrinsics.md)öğeleri.

### <a name="improved-net-core-version-apis"></a>Geliştirilmiş .NET Core sürümü API 'Leri

.NET Core 3,0 ile başlayarak, .NET Core ile birlikte sunulan sürüm API 'Leri artık istediğiniz bilgileri döndürür. Örneğin:

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

.NET kullanıcıları, [**JSON.net**](https://www.newtonsoft.com/json) ve DIĞER popüler JSON kitaplıklarına büyük ölçüde güvenmeye devam eder ve bu da iyi seçeneklere sahip olur. **JSON.net** , temel veri türü olarak .net dizelerini kullanır, bu da arada bulunan UTF-16 ' dır.

Yeni yerleşik JSON desteği yüksek performanslı, düşük tahsisdir ve `Span<byte>` ' ı temel alır. <xref:System.Text.Json> ad alanı ve türleri hakkında daha fazla bilgi için bkz. [.net 'Te JSON serileştirme](../../standard/serialization/system-text-json-overview.md). Yaygın JSON serileştirme senaryolarında öğreticiler için bkz. [.net 'TE JSON serileştirme ve seri durumdan çıkarma](../../standard/serialization/system-text-json-how-to.md).

### <a name="http2-support"></a>HTTP/2 desteği

<xref:System.Net.Http.HttpClient?displayProperty=nameWithType> türü HTTP/2 protokolünü destekler. HTTP/2 etkinse HTTP protokol sürümü TLS/ALPN aracılığıyla görüşülür ve sunucunun bunu kullanabilmesi durumunda HTTP/2 kullanılır.

Varsayılan protokol HTTP/1.1 olarak kalır, ancak HTTP/2 iki farklı şekilde etkinleştirilebilir. İlk olarak http istek iletisini HTTP/2 kullanacak şekilde ayarlayabilirsiniz:

[!CODE-csharp[Http2Request](~/samples/snippets/core/whats-new/whats-new-in-30/cs/http.cs#Request)]

İkincisi, varsayılan olarak <xref:System.Net.Http.HttpClient> ' ı HTTP/2 kullanacak şekilde değiştirebilirsiniz:

[!CODE-csharp[Http2Client](~/samples/snippets/core/whats-new/whats-new-in-30/cs/http.cs#Client)]

Uygulama geliştirirken birçok kez şifrelenmemiş bağlantı kullanmak istersiniz. Hedef uç noktanın HTTP/2 kullanacağınızı biliyorsanız, HTTP/2 için şifrelenmemiş bağlantıları açabilirsiniz. `DOTNET_SYSTEM_NET_HTTP_SOCKETSHTTPHANDLER_HTTP2UNENCRYPTEDSUPPORT` ortam değişkenini `1` ya da uygulama bağlamında etkinleştirerek etkinleştirebilirsiniz:

[!CODE-csharp[Http2Context](~/samples/snippets/core/whats-new/whats-new-in-30/cs/http.cs#AppContext)]

## <a name="next-steps"></a>Sonraki adımlar

- [.NET Core 2,2 ve 3,0 arasındaki son değişiklikleri gözden geçirin.](../compatibility/2.2-3.0.md)
- [.NET Framework ve .NET Core 3,0 arasındaki son değişiklikleri gözden geçirin.](../compatibility/framework-core.md)
