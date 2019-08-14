---
title: ​.NET Core 3.0’daki yenilikler
description: .NET Core 3,0 ' de bulunan yeni özellikler hakkında bilgi edinin.
dev_langs:
- csharp
- vb
author: thraka
ms.author: adegeo
ms.date: 07/25/2019
ms.openlocfilehash: 477aecec4381f26e505e88f7df38f68a85e8f70d
ms.sourcegitcommit: d98fdb087d9c8aba7d2cb93fe4b4ee35a2308cee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/14/2019
ms.locfileid: "69012836"
---
# <a name="whats-new-in-net-core-30-preview-7"></a>.NET Core 3,0 'deki yenilikler (Önizleme 7)

Bu makalede .NET Core 3,0 'deki yenilikler açıklanmaktadır (Preview 7 üzerinden). En büyük geliştirmelerden biri, Windows Masaüstü uygulamaları için destek içerir (yalnızca Windows). .NET Core 3,0 SDK bileşeni Windows Masaüstü 'Nü kullanarak Windows Forms ve Windows Presentation Foundation (WPF) uygulamalarınızın bağlantı noktası oluşturabilirsiniz. Temiz olması için, Windows Masaüstü bileşeni yalnızca Windows 'da desteklenir ve Windows 'a dahildir. Daha fazla bilgi için bu makalenin devamındaki [Windows Masaüstü](#windows-desktop) bölümüne bakın.

.NET Core 3,0, 8,0 için C# destek ekler. [En son Visual Studio Preview](https://visualstudio.microsoft.com/vs/preview/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+preview)sürümünü kullanmanız veya OmniSharp uzantısıyla Visual Studio Code önerilir.

Şimdi Windows, Mac ve Linux 'ta [.NET Core 3,0 Preview 7 ' yi indirip kullanmaya](https://aka.ms/netcore3download) başlayın.

Her önizleme sürümü hakkında daha fazla bilgi için aşağıdaki duyurulara bakın:

- [.NET Core 3,0 Preview 7 duyurusu](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-0-preview-7/)
- [.NET Core 3,0 Preview 6 duyurusu](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-0-preview-6/)
- [.NET Core 3,0 Preview 5 duyurusu](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-0-preview-5/)
- [.NET Core 3,0 Preview 4 duyurusu](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-preview-4/)
- [.NET Core 3,0 Preview 3 duyurusu](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-preview-3/)
- [.NET Core 3,0 Preview 2 duyurusu](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-preview-2/)
- [.NET Core 3,0 Preview 1 ilanı](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-preview-1-and-open-sourcing-windows-desktop-frameworks/)

## <a name="production-supported-preview"></a>Üretim için desteklenen Önizleme

.NET Core Preview 7, Microsoft tarafından önceden hazırlanarak üretim olarak kabul edilir ve tam olarak desteklenmektedir. Sürüm 7 ' den itibaren, yayınlar yeni özellikler eklemek yerine polishing .NET Core 3,0 ' ye odaklanacaktır. Preview 7 ' de nelerin değiştiği hakkında daha fazla bilgi için [Preview 7 duyurusuna](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-0-preview-7/)bakın.

## <a name="net-core-sdk-windows-installer"></a>.NET Core SDK Windows Installer

Windows için MSI Yükleyicisi, .NET Core 3,0 ile başlayarak değiştirilmiştir. SDK yükleyicileri artık SDK özelliği bant sürümlerini yerinde yükseltecektir. Özellik bantları, sürüm numarasının *Patch* bölümündeki *yüzlerce* grupta tanımlanmıştır. Örneğin, **3,0. _101_**  ve **3,0. _201_**  , 3,0 sırasında iki farklı özellik bantlarındaki sürümleridir **. _101_**  ve **3,0. _199_**  aynı özellik bandında. .NET Core SDK **3,0 olduğunda. _101_**  .NET Core SDK yüklendi, **3,0. _100_**  , varsa makineden kaldırılacak. .NET Core SDK **3,0. _200_**  , .NET Core SDK 3,0 ' de aynı makineye yüklendi **. _101_**  kaldırılmaz.

Sürüm oluşturma hakkında daha fazla bilgi için bkz. [.NET Core 'un sürümü oluşturma konusuna genel bakış](../versions/index.md).

## <a name="c-80-preview"></a>C#8,0 Önizleme

.NET Core 3,0, C# 8 önizlemeyi destekler. 8,0 özellikleri hakkında C# daha fazla bilgi için bkz. [ C# 8,0](../../csharp/whats-new/csharp-8.md)sürümündeki yenilikler.

## <a name="net-standard-21"></a>.NET Standard 2,1

.NET Core 3,0 **.NET Standard 2,1**' yi desteklese de, `dotnet new classlib` varsayılan şablon **.NET Standard 2,0**' i hedefleyen bir proje oluşturur. **.NET Standard 2,1**' i hedeflemek için proje dosyanızı düzenleyin ve `TargetFramework` özelliği şu şekilde `netstandard2.1`değiştirin:

```xml
<Project Sdk="Microsoft.NET.Sdk">
 
  <PropertyGroup>
    <TargetFramework>netstandard2.1</TargetFramework>
  </PropertyGroup>
 
</Project>
```

Visual Studio kullanıyorsanız, Visual Studio 2017 **.NET Standard 2,1** veya **.NET Core 3,0**' i desteklemediğinden [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019)gerekir.

## <a name="improved-net-core-version-apis"></a>Geliştirilmiş .NET Core sürümü API 'Leri

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
// New result
//   RuntimeInformation.FrameworkDescription: .NET Core 3.0.0-preview4-27615-11
```

> [!WARNING]
> Son değişiklik. Bu teknik açıdan önemli bir değişiklik olduğundan, sürüm oluşturma düzeni değişti.

## <a name="net-platform-dependent-intrinsics"></a>.NET platforma bağımlı Iç bilgiler

**SIMD** veya **bit işleme yönergesi** kümeleri gıbı belirli performans yönelimli CPU yönergelerine erişime izin veren API 'ler eklenmiştir. Bu yönergeler, verileri paralel şekilde işleme gibi belirli senaryolarda önemli performans geliştirmeleri elde etmenize yardımcı olabilir. 

Uygun durumlarda, .NET kitaplıkları performansı artırmak için bu yönergeleri kullanmaya başlamıştır.

Daha fazla bilgi için bkz. [.NET platformu bağımlı iç](https://github.com/dotnet/designs/blob/master/accepted/platform-intrinsics.md)öğeleri.

## <a name="default-executables"></a>Varsayılan yürütülebilir dosyalar

.NET Core artık [çerçeveye bağlı yürütülebilir dosyaları](../deploying/index.md#framework-dependent-executables-fde) varsayılan olarak oluşturur. Bu davranış, .NET Core 'un küresel olarak yüklenen bir sürümünü kullanan uygulamalar için yenidir. Daha önce yalnızca [kendi kendine kapsanan dağıtımlar](../deploying/index.md#self-contained-deployments-scd) yürütülebilir bir dosya üretecektir.

`dotnet build` Veya`dotnet publish`sırasında, kullanmakta olduğunuz SDK ortamı ve platformuyla eşleşen bir yürütülebilir dosya oluşturulur. Bu yürütülebilir dosyalarla aynı şeyleri, diğer yerel yürütülebilir dosyaları gibi bekleyebilir, örneğin:

* Yürütülebilir dosyaya çift tıklayabilirsiniz.
* Uygulamayı Windows ve `myapp.exe` `./myapp` Linux ve MacOS gibi bir komut isteminden doğrudan başlatabilirsiniz.

## <a name="single-file-executables"></a>Tek dosya yürütülebilir dosyaları

Komut `dotnet publish` , uygulamanızı platforma özgü tek dosya yürütülebilir dosyasına paketlemeyi destekler. Yürütülebilir dosya kendiliğinden ayıklanıyor ve uygulamanızı çalıştırmak için gerekli tüm bağımlılıkları (yerel dahil) içerir. Uygulama ilk kez çalıştırıldığında uygulama adı ve derleme tanımlayıcısı temelinde bir dizine çıkarılır. Uygulama yeniden çalıştırıldığında başlatma daha hızlıdır. Yeni bir sürüm kullanılmadığı takdirde uygulamanın kendisi ikinci kez ayıklanmasına gerek yoktur.

Tek dosya yürütülebiliri yayımlamak için, projenizdeki öğesini veya `PublishSingleFile` komut satırında `dotnet publish` komutunu komutuyla ayarlayın:

```xml
<PropertyGroup>
  <RuntimeIdentifier>win10-x64</RuntimeIdentifier>
  <PublishSingleFile>true</PublishSingleFile>
</PropertyGroup>
```

-veya-

```console
dotnet publish -r win10-x64 /p:PublishSingleFile=true
```

Tek dosya yayınlama hakkında daha fazla bilgi için bkz. [tek dosya paketcisi tasarım belgesi](https://github.com/dotnet/designs/blob/master/accepted/single-file/design.md).

## <a name="assembly-linking"></a>Bütünleştirilmiş kod bağlama

.NET Core 3,0 SDK, Il 'yi çözümleyerek ve kullanılmayan derlemeleri kırparak uygulamaların boyutunu azaltan bir araçla birlikte gelir.

Bağımsız uygulamalar, kodunuzun çalıştırılması için gereken her şeyi, ana bilgisayara .NET yüklenmesini gerektirmeden içerir. Ancak, çoğu zaman uygulamanın çalışması için yalnızca küçük bir çerçeve alt kümesi gerekir ve kullanılmayan diğer kitaplıklar da kaldırılabilir.

.NET Core artık uygulamanızın Il 'sini taramak için [Il bağlayıcı](https://github.com/mono/linker) aracını kullanacak bir ayar içeriyor. Bu araç hangi kodun gerekli olduğunu algılar ve ardından kullanılmayan kitaplıkları kırpar. Bu araç bazı uygulamaların dağıtım boyutunu önemli ölçüde azaltabilir.

Bu aracı etkinleştirmek için projenize `<PublishTrimmed>` ayarı ekleyin ve kendi içinde bulunan bir uygulamayı yayımlayın:

```xml
<PropertyGroup>
  <PublishTrimmed>true</PublishTrimmed>
</PropertyGroup>
```

```console
dotnet publish -r <rid> -c Release
```

Örnek olarak, yayımlanan temel "Merhaba Dünya" yeni konsol projesi şablonu, yayımlandığında 70 MB ile çarpılır. Kullanarak `<PublishTrimmed>`, bu boyut yaklaşık 30 MB 'ye indirilir.

Yansıma veya ilgili dinamik özellikleri kullanan uygulamaların veya çerçevelerin (ASP.NET Core ve WPF dahil) genellikle kırpıldığına göre kesilmesini göz önünde bulundurmanız önemlidir. Bu ayırıcı, bağlayıcının bu dinamik davranış hakkında bilgi sahibi olmadığı ve yansıma için hangi çerçeve türlerinin gerekli olduğunu belirleyemediği için oluşur. Il bağlayıcı aracı, bu senaryonun farkında olacak şekilde yapılandırılabilir.

Tüm diğerleri üzerinde, kırpdıktan sonra uygulamanızı test ettiğinizden emin olun.

Il bağlayıcı aracı hakkında daha fazla bilgi için [belgelere](https://aka.ms/dotnet-illink) bakın veya [mono/bağlayıcı]( https://github.com/mono/linker) deposunu ziyaret edin.

## <a name="tiered-compilation"></a>Katmanlı derleme

[Katmanlı derleme](https://devblogs.microsoft.com/dotnet/tiered-compilation-preview-in-net-core-2-1/) (TC), .NET Core 3,0 ile varsayılan olarak açık olur. Bu özellik, çalışma zamanının daha iyi performans almak için tam zamanında (JıT) derleyicisini daha kolay bir şekilde kullanmasına olanak sağlar.

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

## <a name="readytorun-images"></a>ReadyToRun görüntüleri

Uygulama derlemelerinizi ReadyToRun (R2R) biçiminde derleyerek .NET Core uygulamanızın başlama süresini geliştirebilirsiniz. R2R, bir süre öncesi (AOT) derleme biçimidir.

R2R ikilileri, tam zamanında (JıT) derleyicisinin uygulamanız yüklenirken yapması gereken iş miktarını azaltarak başlangıç performansını geliştirir. İkililer, JıT 'in üretmesine kıyasla benzer yerel kod içerir. Ancak, R2R ikilileri, bazı senaryolar için hala gerekli olan hem ara dil (IL) kodunu hem de aynı kodun yerel sürümünü içerdiğinden, daha büyüktür. R2R yalnızca, Linux x64 veya Windows x64 gibi belirli çalışma zamanı ortamlarını (RID) hedefleyen bir kendi içinde bulunan uygulamayı yayımladığınızda kullanılabilir.

Projenizi ReadyToRun olarak derlemek için aşağıdakileri yapın:

01. `<PublishReadyToRun>` Ayarı projenize ekleyin

    ```xml
    <PropertyGroup>
      <PublishReadyToRun>true</PublishReadyToRun>
    </PropertyGroup>
    ```

01. Kendi içinde bir uygulama yayımlayın. Örneğin, bu komut Windows 'un 64 bit sürümü için kendi kendine içerilen bir uygulama oluşturur:

    ```console
    dotnet publish -c Release -r win-x64 --self-contained true
    ```

### <a name="cross-platformarchitecture-restrictions"></a>Platformlar arası/mimari kısıtlamaları

ReadyToRun derleyicisi Şu anda çapraz hedefleme 'yi desteklememektedir. Belirli bir hedefte derleme yapmanız gerekir. Örneğin, R2R görüntülerini Windows x64 için istiyorsanız, bu ortamda Yayımla komutunu çalıştırmanız gerekir.

Çapraz hedefleme için özel durumlar:

- Windows x64, Windows ARM32, ARM64 ve x86 görüntülerini derlemek için kullanılabilir.
- Windows x86, Windows ARM32 görüntülerini derlemek için kullanılabilir.
- Linux x64, Linux ARM32 ve ARM64 görüntülerini derlemek için kullanılabilir.

## <a name="build-copies-dependencies"></a>Derleme kopyaları bağımlılıkları

Komut `dotnet build` artık, NuGet önbelleğinden uygulamanızın NuGet bağımlılıklarını yapı çıkış klasörüne kopyalar. Daha önce bağımlılıklar yalnızca bir `dotnet publish`parçası olarak kopyalandı.

Bağlama ve Razor sayfası yayımlama gibi bazı işlemler, yayımlamayı gerektirecek şekilde devam eder.

## <a name="local-tools"></a>Yerel Araçlar

.NET Core 3,0 yerel araçları tanıtır. Yerel Araçlar [genel araçlara](../tools/global-tools.md) benzerdir, ancak diskte belirli bir konum ile ilişkilendirilir. Yerel araçlar küresel olarak kullanılabilir değildir ve NuGet paketleri olarak dağıtılır.

> [!WARNING]
> .NET Core 3,0 Preview 1 ' de veya `dotnet tool restore` `dotnet tool install`çalıştıran gibi yerel araçlara çalıştıysanız, yerel araçlar önbellek klasörünü silin. Aksi takdirde, yerel araçlar yeni bir sürümde çalışmaz. Bu klasör şu konumda bulunur:
>
> MacOS 'ta Linux:`rm -r $HOME/.dotnet/toolResolverCache`
>
> Windows 'da:`rmdir /s %USERPROFILE%\.dotnet\toolResolverCache`

Yerel araçlar, geçerli dizininizde bir bildirim dosyası `dotnet-tools.json` adına bağımlıdır. Bu bildirim dosyası, bu klasörde ve altında kullanılabilecek araçları tanımlar. Kodunuzla çalışan herkesin aynı araçları geri yükleyip kullanabilmesini sağlamak için, bildirim dosyasını kodunuzla dağıtabilirsiniz.

Hem genel hem de yerel araçlar için, çalışma zamanının uyumlu bir sürümü gereklidir. Şu anda NuGet.org hedef .NET Core çalışma zamanı 2,1 ' de birçok araç. Bu araçları küresel olarak veya yerel olarak yüklemek için, hala [NET Core 2,1 çalışma zamanını](https://dotnet.microsoft.com/download/dotnet-core/2.1)yüklemeniz gerekir.

## <a name="major-version-roll-forward"></a>Büyük sürüm Ileri

.NET Core 3,0, uygulamanızın .NET Core 'un en son ana sürümüne iletmesini sağlayan bir katılım özelliği sunar. Ayrıca, geri alma 'nın uygulamanıza nasıl uygulandığını denetlemek için yeni bir ayar eklenmiştir. Bu, aşağıdaki yollarla yapılandırılabilir:

- Proje dosyası özelliği:`RollForward`
- Çalışma zamanı yapılandırma dosyası özelliği:`rollForward`
- Ortam değişkeni:`DOTNET_ROLL_FORWARD`
- Komut satırı bağımsız değişkeni:`--roll-forward`

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

## <a name="windows-desktop"></a>Windows masaüstü

.NET Core 3,0, Windows Presentation Foundation (WPF) ve Windows Forms kullanarak Windows masaüstü uygulamalarını destekler. Bu çerçeveler ayrıca, Windows UI XAML kitaplığı 'ndan (WinUI) [xaml Adaları](/windows/uwp/xaml-platform/xaml-host-controls)aracılığıyla modern denetimleri ve akıcı stil oluşturmayı da destekler.

Windows Masaüstü bileşeni, Windows .NET Core 3,0 SDK 'sının bir parçasıdır.

Aşağıdaki `dotnet` komutlarla yeni bir WPF veya Windows Forms uygulaması oluşturabilirsiniz:

```console
dotnet new wpf
dotnet new winforms
```

Visual Studio 2019, .NET Core 3,0 Windows Forms ve WPF için **Yeni proje** şablonları ekler.

Mevcut bir .NET Framework uygulamasının bağlantı noktası hakkında daha fazla bilgi için bkz. [bağlantı noktası WPF projeleri](../porting/wpf.md) ve [bağlantı noktası Windows Forms projeleri](../porting/winforms.md).

## <a name="com-callable-components---windows-desktop"></a>COM çağrılabilir bileşenler-Windows Masaüstü

Windows 'ta artık COM çağrılabilir yönetilen bileşenler oluşturabilirsiniz. Bu özellik, .NET Core 'un COM eklenti modelleriyle kullanılması ve ayrıca .NET Framework eşlik sağlanması açısından önemlidir.

*Mscoree. dll* ' nin com sunucusu olarak kullanıldığı .NET Framework aksine, .NET Core, com bileşenini oluştururken *bin* dizinine yerel bir başlatıcı dll 'si ekler.

COM bileşeni oluşturma ve kullanma hakkında bir örnek için bkz. [com tanıtımı](https://github.com/dotnet/samples/tree/master/core/extensions/COMServerDemo).

## <a name="msix-deployment---windows-desktop"></a>MSIX dağıtımı-Windows Masaüstü

[Msix](https://docs.microsoft.com/windows/msix/) yeni bir Windows uygulama paketi biçimidir. .NET Core 3,0 masaüstü uygulamalarını Windows 10 ' a dağıtmak için kullanılabilir.

Visual Studio 2019 ' de bulunan [Windows uygulama paketleme projesi](https://docs.microsoft.com/windows/uwp/porting/desktop-to-uwp-packaging-dot-net), [kendi kendine içerilen](../deploying/index.md#self-contained-deployments-scd) .NET Core uygulamalarıyla msix paketi oluşturmanıza olanak sağlar.

.NET Core proje dosyası, `<RuntimeIdentifiers>` özelliğindeki desteklenen çalışma zamanlarını belirtmelidir:

```xml
<RuntimeIdentifiers>win-x86;win-x64</RuntimeIdentifiers>
```

## <a name="winforms-highdpi"></a>WinForms HighDPI

.NET Core Windows Forms uygulamaları, ile <xref:System.Windows.Forms.Application.SetHighDpiMode(System.Windows.Forms.HighDpiMode)?displayProperty=nameWithType>yüksek DPI modunu ayarlayabilir. Bu `SetHighDpiMode` Yöntem, daha önce `Application.Run`veya P/Invoke gibi `App.Manifest` diğer yollarla ayarlanmadığı takdirde, karşılık gelen yüksek DPI modunu ayarlar.

Sabit<xref:System.Windows.Forms.HighDpiMode?displayProperty=nameWithType> listesi `highDpiMode` tarafından ifade edilen olası değerler şunlardır:

* `DpiUnaware`
* `SystemAware`
* `PerMonitor`
* `PerMonitorV2`
* `DpiUnawareGdiScaled`

Yüksek DPı modları hakkında daha fazla bilgi için bkz. [Windows 'Da yüksek DPI Masaüstü uygulama geliştirme](/windows/desktop/hidpi/high-dpi-desktop-application-development-on-windows).

## <a name="ranges-and-indices"></a>Aralıklar ve dizinler

Yeni <xref:System.Index?displayProperty=nameWithType> tür dizin oluşturmak için kullanılabilir. Başlangıçtan itibaren bir veya sonuna kadar `int` olan önek `^` işleci (C#) ile bir tane oluşturabilirsiniz:

```csharp
Index i1 = 3;  // number 3 from beginning
Index i2 = ^4; // number 4 from end
int[] a = { 0, 1, 2, 3, 4, 5, 6, 7, 8, 9 };
Console.WriteLine($"{a[i1]}, {a[i2]}"); // "3, 6"
```

Ayrıca <xref:System.Range?displayProperty=nameWithType> , biri başlangıç ve diğeri bitiş için olmak üzere `Index` iki değerden oluşan tür ve bir `x..y` Aralık ifadesiyle (C#) yazılabilir. Daha sonra bir dilim üreten bir `Range`ile dizin oluşturabilirsiniz:

```csharp
var slice = a[i1..i2]; // { 3, 4, 5 }
```

Daha fazla bilgi için [aralıklar ve dizinler öğreticisine](../../csharp/tutorials/ranges-indexes.md)bakın.

## <a name="async-streams"></a>Zaman uyumsuz akışlar

Türü yeni bir zaman uyumsuz <xref:System.Collections.Generic.IEnumerable%601>sürümüdür. <xref:System.Collections.Generic.IAsyncEnumerable%601> `yield return` Dil `await foreach` ,öğelerinitüketmekveöğelerioluşturmakiçinbunlarıkullanmakiçinkullanabilirsiniz.`IAsyncEnumerable<T>`

Aşağıdaki örnek, zaman uyumsuz akışların hem üretimini hem de tüketimini gösterir. Bildirim zaman uyumsuz ve kendisi çağıranlar için zaman uyumsuz akış üretmek için kullanır `yield return`. `foreach` Bu model (kullanılarak `yield return`), zaman uyumsuz akışlar üretmek için önerilen modeldir.

```csharp
async IAsyncEnumerable<int> GetBigResultsAsync()
{
    await foreach (var result in GetResultsAsync())
    {
        if (result > 20) yield return result; 
    }
}
```

Ayrıca, zaman uyumsuz yineleyiciler da oluşturabilirsiniz, örneğin, hem `await` hem `yield` de içinde kullanabileceğiniz bir `IAsyncEnumerable/IAsyncEnumerator` Yineleyici. `await foreach` Atılmalıdır, `IAsyncDisposable` `Stream` ve `Timer`gibi çeşitli BCL türlerini uygulayan ' i kullanabilirsiniz.

Daha fazla bilgi için bkz. [zaman uyumsuz akışlar öğreticisi](../../csharp/tutorials/generate-consume-asynchronous-stream.md).

## <a name="ieee-floating-point-improvements"></a>IEEE kayan nokta iyileştirmeleri

Kayan nokta API 'Leri, [ıeee 754-2008 düzeltmesine](https://en.wikipedia.org/wiki/IEEE_754-2008_revision)uymak üzere güncelleştiriliyor. Bu değişikliklerin amacı, tüm **gerekli** işlemleri kullanıma sunmaktır ve DAVRANıŞSAL 'in IEEE spec ile uyumlu olduklarından emin olmaktır. Kayan nokta iyileştirmeleri hakkında daha fazla bilgi için bkz. [.NET Core 3,0 blog gönderisine kayan nokta ayrıştırma ve biçimlendirme geliştirmeleri](https://devblogs.microsoft.com/dotnet/floating-point-parsing-and-formatting-improvements-in-net-core-3-0/) .

Ayrıştırma ve biçimlendirme düzeltmeleri şunları içerir:

* Her uzunlukta doğru şekilde ayrıştırma ve yuvarlama girişleri.
* Doğru şekilde ayrıştırır ve negatif sıfır biçimlendirir.
* Büyük/ `Infinity` küçük `NaN` harfe duyarsız bir denetim yaparak ve uygunsa isteğe bağlı olarak daha önce `+` izin vererek doğru şekilde ayrıştırılabilir.

Yeni <xref:System.Math?displayProperty=nameWithType> API 'ler şunlardır:

* <xref:System.Math.BitIncrement(System.Double)>'<xref:System.Math.BitDecrement(System.Double)>\
`nextUp` Ve`nextDown` IEEE işlemlerine karşılık gelir. Bunlar, girdiden daha büyük veya daha az (sırasıyla) karşılaştıran en küçük kayan nokta numarasını döndürür. Örneğin, `Math.BitIncrement(0.0)` döndürür `double.Epsilon`.

* <xref:System.Math.MaxMagnitude(System.Double,System.Double)>'<xref:System.Math.MinMagnitude(System.Double,System.Double)>\
`maxNumMag` Ve`minNumMag` IEEE işlemlerine karşılık gelen değeri, iki girişin büyüklüğüne daha büyük veya daha az (sırasıyla) döndürür. Örneğin, `Math.MaxMagnitude(2.0, -3.0)` döndürür `-3.0`.

* <xref:System.Math.ILogB(System.Double)>\
Bir integral değeri döndüren IEEEişleminekarşılıkgelir,girişparametresinintamsayıtaban2günlüğünüdöndürür.`logB` Bu yöntem `floor(log2(x))`, ile aynı şekilde, ancak en az yuvarlama hatasıyla yapılır.

* <xref:System.Math.ScaleB(System.Double,System.Int32)>\
Bir tamsayı değeri alan `x * pow(2, n)` IEEEişleminekarşılıkgelir,etkinolarakdöner,ancakenazyuvarlamahatasıylayapılır.`scaleB`

* <xref:System.Math.Log2(System.Double)>\
`log2` IEEE işlemine karşılık gelen 2 tabanında logaritmasını döndürür. Yuvarlama hatasını en aza indirir.

* <xref:System.Math.FusedMultiplyAdd(System.Double,System.Double,System.Double)>\
`fma` IEEE işlemine karşılık gelen bir fkullandınız çarpma eklemesi gerçekleştirir. Yani, tek bir işlem `(x * y) + z` olarak yapılır, böylece yuvarlama hatasını en aza indirir. Örnek `FusedMultiplyAdd(1e308, 2.0, -1e308)` , döndürür `1e308`. Normal `(1e308 * 2.0) - 1e308` dönüşler `double.PositiveInfinity`.

* <xref:System.Math.CopySign(System.Double,System.Double)>\
IEEE işlemine karşılık gelir, `x`, `y`ancak işaretini döndürür. `copySign`

## <a name="fast-built-in-json-support"></a>Hızlı yerleşik JSON desteği

.NET kullanıcıları, [**JSON.net**](https://www.newtonsoft.com/json) ve DIĞER popüler JSON kitaplıklarına büyük ölçüde güvenmeye devam eder ve bu da iyi seçeneklere sahip olur. **JSON.net** , temel veri türü olarak .net dizelerini kullanır, bu da arada bulunan UTF-16 ' dır.

Yeni yerleşik JSON desteği yüksek performanslı, düşük ayırma ve temel alınarak `Span<byte>`gerçekleştirilir. .NET Core 3,0 ad alanına yeni, <xref:System.Text.Json?displayProperty=nameWithType> JSON ile ilgili üç tür eklendi. Bu türler *henüz* düz eski CLR nesne (POCO) serileştirme ve serisini desteklemez.

### <a name="utf8jsonreader"></a>Utf8JsonReader

<xref:System.Text.Json.Utf8JsonReader?displayProperty=nameWithType>, ' dan okunan UTF-8 kodlu JSON metin için yüksek performanslı, düşük bir `ReadOnlySpan<byte>`ayırma, Salt ilet okuyucu olur. `Utf8JsonReader` , Özel Çözümleyicileri ve seri hale getiriciler oluşturmak için kullanılabilen, temel bir alt düzey türüdür. New `Utf8JsonReader` kullanarak JSON yükünün okunması, **JSON.net**'den okuyucu kullanmaktan daha hızlıdır. JSON belirteçlerini (UTF-16) dizeleri olarak oluşturmanız gerekene kadar ayırmaz.

Visual Studio Code tarafından oluşturulan [**Launch. JSON**](https://github.com/dotnet/samples/blob/master/snippets/core/whats-new/whats-new-in-30/cs/launch.json) dosyası aracılığıyla okuma örneği aşağıda verilmiştir:

[!CODE-csharp[Utf8JsonReader](~/samples/snippets/core/whats-new/whats-new-in-30/cs/program.cs#PrintJson)]

[!CODE-csharp[Utf8JsonReader](~/samples/snippets/core/whats-new/whats-new-in-30/cs/program.cs#PrintJsonCall)]

### <a name="utf8jsonwriter"></a>Utf8JsonWriter

<xref:System.Text.Json.Utf8JsonWriter?displayProperty=nameWithType>, `String` `Int32`ve gibiortak.nettürlerindenUTF-8kodluJSONmetniyazmakiçinyüksekperformanslı,önbelleğealınmamışvesaltileribiryolsağlar.`DateTime` Okuyucu gibi, yazıcı ise özel serileştiriciler oluşturmak için kullanılabilen temel bir alt düzey tür olur. Yeni `Utf8JsonWriter` % 30-80 daha hızlı bir JSON yükü yazmak, **JSON.net** adresinden yazıcı kullanmaktan daha hızlıdır ve ayrılmaz.

### <a name="jsondocument"></a>JsonDocument

<xref:System.Text.Json.JsonDocument?displayProperty=nameWithType>, `Utf8JsonReader`üzerine kurulmuştur. , `JsonDocument` JSON verilerini ayrıştırabilme ve rasgele erişimi ve numaralandırmayı desteklemek için sorgulanabilen salt okunurdur belge nesne modeli (DOM) oluşturma olanağı sağlar. Verileri oluşturan JSON öğelerine, adlı <xref:System.Text.Json.JsonElement> `RootElement`bir özellik `JsonDocument` olarak kullanıma sunulan tür aracılığıyla erişilebilir. JSON metnini ortak .net türlerine dönüştürmek için API 'lerle birlikte JSON dizisini ve nesne numaralandırıcıları içerir.`JsonElement` Tipik bir JSON yükünü ayrıştırma ve ' ı kullanarak `JsonDocument` tüm üyelerine erişme, makul ölçüde boyutlandırılabilir (yani , < 1 MB) veriler için çok az ayırmayla 3x ' den daha hızlıdır.

Başlangıç noktası olarak kullanılabilecek `JsonDocument` ve ' `JsonElement` nin örnek kullanımı aşağıda verilmiştir:

[!CODE-csharp[JsonDocument](~/samples/snippets/core/whats-new/whats-new-in-30/cs/program.cs#ReadJson)]

İşte Visual Studio Code tarafından C# oluşturulan [Launch. JSON](https://github.com/dotnet/samples/blob/master/snippets/core/whats-new/whats-new-in-30/cs/launch.json) dosyası aracılığıyla okuma için 8,0 bir örnek:

[!CODE-csharp[JsonDocument](~/samples/snippets/core/whats-new/whats-new-in-30/cs/program.cs#ReadJsonCall)]

### <a name="jsonserializer"></a>JsonSerializer

<xref:System.Text.Json.JsonSerializer?displayProperty=nameWithType>, ve ' nin <xref:System.Text.Json.Utf8JsonReader> üzerine kurulmuştur ve <xref:System.Text.Json.Utf8JsonWriter> JSON belgeleri ve parçaları ile çalışırken hızlı, düşük bellek serileştirme seçeneği sağlar.

JSON için bir nesneyi serileştirmede bir örnek aşağıda verilmiştir:

[!CODE-csharp[JsonSerializer](~/samples/snippets/core/whats-new/whats-new-in-30/cs/JSON.cs#JsonSerialize)]

Bir JSON dizesinin bir nesneye serisini kaldırma örneği aşağıda verilmiştir. Önceki örnek tarafından üretilen JSON dizesini kullanabilirsiniz:

[!CODE-csharp[JsonDeserializer](~/samples/snippets/core/whats-new/whats-new-in-30/cs/JSON.cs#JsonDeserialize)]

## <a name="interop-improvements"></a>Birlikte çalışma geliştirmeleri

.NET Core 3,0, yerel API birlikte çalışabilirliği geliştirir.

### <a name="type-nativelibrary"></a>Tür: NativeLibrary

<xref:System.Runtime.InteropServices.NativeLibrary?displayProperty=nameWithType>Yerel bir kitaplığı (.NET Core P/Invoke ile aynı yük mantığını kullanarak) yüklemek ve gibi ilgili yardımcı işlevleri `getSymbol`sağlamak için bir kapsülleme sağlar. Kod örneği için bkz. [Dllmap tanıtımı](https://github.com/dotnet/samples/tree/master/core/extensions/AppWithPlugin).

### <a name="windows-native-interop"></a>Windows yerel birlikte çalışma

Windows, düz C API 'Leri, COM ve WinRT biçiminde zengin bir yerel API sunar. .NET Core **P/Invoke**'ı destekleirken, .net Core 3,0, **com API 'Leri oluşturma** ve **WinRT API 'leri etkinleştirme**özelliğini ekler. Kod örneği için bkz. [Excel tanıtımı](https://github.com/dotnet/samples/tree/master/core/extensions/ExcelDemo).

## <a name="http2-support"></a>HTTP/2 desteği

<xref:System.Net.Http.HttpClient?displayProperty=nameWithType> Tür http/2 protokolünü destekler. HTTP/2 etkinse HTTP protokol sürümü TLS/ALPN aracılığıyla görüşülür ve sunucunun bunu kullanabilmesi durumunda HTTP/2 kullanılır.

Varsayılan protokol HTTP/1.1 olarak kalır, ancak HTTP/2 iki farklı şekilde etkinleştirilebilir. İlk olarak http istek iletisini HTTP/2 kullanacak şekilde ayarlayabilirsiniz:

[!CODE-csharp[Http2Request](~/samples/snippets/core/whats-new/whats-new-in-30/cs/http.cs#Request)]

İkincisi, varsayılan olarak http <xref:System.Net.Http.HttpClient> /2 kullan seçeneğini kullanabilirsiniz:

[!CODE-csharp[Http2Client](~/samples/snippets/core/whats-new/whats-new-in-30/cs/http.cs#Client)]

Uygulama geliştirirken birçok kez şifrelenmemiş bağlantı kullanmak istersiniz. Hedef uç noktanın HTTP/2 kullanacağınızı biliyorsanız, HTTP/2 için şifrelenmemiş bağlantıları açabilirsiniz. `DOTNET_SYSTEM_NET_HTTP_SOCKETSHTTPHANDLER_HTTP2UNENCRYPTEDSUPPORT` Ortam değişkenini uygulama bağlamında etkinleştirerek veya olarak `1` ayarlayarak bu ayarı açabilirsiniz:

[!CODE-csharp[Http2Context](~/samples/snippets/core/whats-new/whats-new-in-30/cs/http.cs#AppContext)]

## <a name="tls-13--openssl-111-on-linux"></a>TLS 1,3 & Linux üzerinde OpenSSL 1.1.1

.NET Core artık, belirli bir ortamda kullanılabildiği [OpenSSL 1.1.1 Içindeki TLS 1,3 desteğinin](https://www.openssl.org/blog/blog/2018/09/11/release111/)avantajlarından yararlanır. TLS 1,3:

* İstemci ve sunucu arasında gereken azaltılan gidiş dönüşlerle bağlantı süreleri geliştirildi.
* Kullanılmayan ve güvenli olmayan şifreleme algoritmalarının kaldırılması nedeniyle güvenlik geliştirildi.

Kullanılabilir olduğunda, .NET Core 3,0 bir Linux sisteminde **OpenSSL 1.1.1**, **OpenSSL 1.1.0**veya **OpenSSL 1.0.2** kullanır. **OpenSSL 1.1.1** kullanılabilir olduğunda, her ikisi <xref:System.Net.Security.SslStream?displayProperty=nameWithType> de <xref:System.Net.Http.HttpClient?displayProperty=nameWithType> tür **TLS 1,3** kullanır (istemci ve sunucunun **TLS 1,3**' i desteklediği varsayıldığında).

>[!IMPORTANT]
>Windows ve macOS henüz **TLS 1,3**' i desteklemez. .NET Core 3,0, destek kullanılabilir hale geldiğinde bu işletim sistemlerinde **TLS 1,3** ' i destekleyecektir.

Aşağıdaki C# 8,0 örneği, ' a bağlanan <https://www.cloudflare.com>Ubuntu 18,10 üzerinde .NET Core 3,0 ' i göstermektedir:

[!CODE-csharp[TLSExample](~/samples/snippets/core/whats-new/whats-new-in-30/cs/TLS.cs#TLS)]

## <a name="cryptography-ciphers"></a>Şifreleme şifrelemeleri

.NET 3,0, ile <xref:System.Security.Cryptography.AesGcm?displayProperty=nameWithType> ve <xref:System.Security.Cryptography.AesCcm?displayProperty=nameWithType> sırasıyla uygulanan **AES-GCM** ve **AES-CCM** şifrelemeleri için destek ekler. Bu algoritmalar, [Ilişki verileri (AEAD) algoritmalarıyla kimliği doğrulanmış şifrelemedir](https://en.wikipedia.org/wiki/Authenticated_encryption).

Aşağıdaki kod, rastgele verileri `AesGcm` şifrelemek ve şifrelerini çözmek için şifre kullanımını gösterir.

[!CODE-csharp[AesGcm](~/samples/snippets/core/whats-new/whats-new-in-30/cs/Cipher.cs#AesGcm)]

## <a name="cryptographic-key-importexport"></a>Şifreleme anahtarı Içeri/dışarı aktarma

.NET Core 3,0, asimetrik ortak ve özel anahtarların standart biçimlerden içeri ve dışarı aktarılmasını destekler. X. 509.440 sertifikası kullanmanız gerekmez.

*RSA*, *dsa*, *ECDSA*ve *ecdıfıfiehellman*gibi tüm anahtar türleri aşağıdaki biçimleri destekler:

* **Ortak anahtar**
  * X. 509.440 Subjectpublickeyınfo

* **Özel anahtar**
  * PKCS # 8 Privatekeyınfo
  * PKCS # 8 Encryptedprivatekeyınfo

RSA anahtarları da şunları destekler:

* **Ortak anahtar**
  * PKCS # 1 RSAPublicKey

* **Özel anahtar**
  * PKCS # 1 RSAPrivateKey

Dışarı aktarma yöntemleri DER kodlu ikili veriler oluşturur ve içeri aktarma yöntemleri aynı şekilde bekler. Bir anahtar, metin kullanımı kolay pek biçiminde depolanıyorsa, bir içeri aktarma yöntemi çağrılmadan önce çağıranın içerik Base64 olarak çözülmesi gerekecektir.

[!CODE-csharp[RSA](~/samples/snippets/core/whats-new/whats-new-in-30/cs/RSA.cs#Rsa)]

**PKCS # 8** dosyaları ile <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo?displayProperty=nameWithType> incelenebilir ve **PFX/PKCS # 12** dosyaları ile <xref:System.Security.Cryptography.Pkcs.Pkcs12Info?displayProperty=nameWithType>incelenebilir. **PFX/PKCS # 12** dosyaları ile <xref:System.Security.Cryptography.Pkcs.Pkcs12Builder?displayProperty=nameWithType>değiştirilebilir.

## <a name="serialport-for-linux"></a>Linux için SerialPort

.NET Core 3,0, <xref:System.IO.Ports.SerialPort?displayProperty=nameWithType> Linux üzerinde desteklenir.

Daha önce, .NET Core yalnızca Windows `SerialPort` 'da kullanımı desteklenir.

## <a name="docker-and-cgroup-memory-limits"></a>Docker ve cgroup bellek sınırları

Preview 3 ' ü kullanmaya başlamadan, Docker ile Linux üzerinde .NET Core 3,0 çalıştırmak, cgroup bellek limitleriyle daha iyi çalışır. İle `docker run -m`gibi bellek limitleriyle bir Docker kapsayıcısı çalıştırmak, .NET Core 'un davranış şeklini değiştirir.

* Varsayılan atık toplayıcı (GC) yığın boyutu: kapsayıcıda bellek sınırının en fazla 20 MB veya% 75 ' si.
* Açık Boyut, mutlak bir sayı veya cgroup sınırının yüzdesi olarak ayarlanabilir.
* GC yığını başına en düşük ayrılmış kesim boyutu 16 MB 'tır. Bu boyut, makinelerde oluşturulan Heap sayısını azaltır.

## <a name="smaller-garbage-collection-heap-sizes"></a>Daha küçük atık toplama yığın boyutları

Atık toplayıcısının varsayılan yığın boyutu daha az bellek kullanan .NET Core ile sonuçlanır. Bu değişiklik, modern işlemci önbelleği boyutları ile nesil 0 ayırma bütçesine göre daha iyi hizalanır.

## <a name="garbage-collection-large-page-support"></a>Çöp toplama büyük sayfa desteği

Büyük sayfalar (Linux 'ta çok büyük sayfalar olarak da bilinir), işletim sisteminin bu büyük sayfaları isteyen uygulamanın performansını artırmak için yerel sayfa boyutundan (genellikle 4K) daha büyük bellek bölgeleri ayarlayabildiği bir özelliktir.

Çöp toplayıcı artık Windows üzerinde büyük sayfalar ayırmayı seçmek için bir katılım özelliği olarak **Gclargepages** ayarıyla yapılandırılabilir.

## <a name="gpio-support-for-raspberry-pi"></a>Raspberry PI için GıO desteği

NuGet 'e GıO programlama için kullanabileceğiniz iki paket yayımlanmıştır:

* [System. Device. GIO](https://www.nuget.org/packages/System.Device.Gpio)
* [IoT. Device. Bindings](https://www.nuget.org/packages/Iot.Device.Bindings)

GPıO paketleri, *GIO*, *SPI*, *I2C*ve *PWM* cihazları için API 'ler içerir. IoT bağlamaları paketi cihaz bağlamalarını içerir. Daha fazla bilgi için bkz. [cihaz GitHub deposu](https://github.com/dotnet/iot/blob/master/src/devices/).

## <a name="arm64-linux-support"></a>ARM64 Linux desteği

.NET Core 3,0, Linux için ARM64 desteği ekler. ARM64 için birincil kullanım örneği şu anda IoT senaryolarıyla birlikte. Daha fazla bilgi için bkz. [.NET Core ARM64 Status](https://github.com/dotnet/announcements/issues/82).

[ARM64 üzerinde .NET Core Için Docker görüntüleri](https://hub.docker.com/r/microsoft/dotnet/) alp, de, ve Ubuntu için kullanılabilir.

> [!NOTE]
> **ARM64** Windows desteği henüz kullanılamıyor.
