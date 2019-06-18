---
title: ​.NET Core 3.0’daki yenilikler
description: .NET Core 3. 0 ' bulunan yeni özellikler hakkında bilgi edinin.
dev_langs:
- csharp
- vb
author: thraka
ms.author: adegeo
ms.date: 05/06/2019
ms.openlocfilehash: 369c74d2d8e82f157de0eec4294a5ee50542292b
ms.sourcegitcommit: a8d3504f0eae1a40bda2b06bd441ba01f1631ef0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/18/2019
ms.locfileid: "67169781"
---
# <a name="whats-new-in-net-core-30-preview-5"></a>.NET Core 3.0 (Preview 5) yenilikler

Bu makalede, .NET Core 3.0 içinde yeni (Önizleme 5) Yenilikler açıklanır. Büyük iyileştirmeler Windows Masaüstü uygulamaları (yalnızca Windows) için destek biridir. Windows Masaüstü .NET Core 3.0 SDK'sı bileşenini kullanarak, Windows Forms ve Windows Presentation Foundation (WPF), uygulamalarınızın bağlantı noktası. Gerekirse Windows Masaüstü bileşen yalnızca desteklenen ve Windows üzerinde dahil. Daha fazla bilgi için [Windows Masaüstü](#windows-desktop) bu makalenin devamındaki bölümü.

.NET core 3.0 için destek ekler C# 8.0. OmniSharp uzantısıyla Visual Studio 2019 güncelleştirme 1 Preview veya VSCode en son sürümünü kullanmanız önerilir.

[İndirin ve .NET Core 3.0 Önizleme 6 ile çalışmaya başlama](https://aka.ms/netcore3download) şu anda Windows, Mac ve Linux üzerinde.

Her önizleme sürümü hakkında daha fazla bilgi için aşağıdaki duyuruları bakın:

- [.NET core 3.0 Önizleme 6 Duyurusu](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-0-preview-6/)
- [.NET core 3.0 Preview 5 Duyurusu](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-0-preview-5/)
- [.NET core 3.0 Önizleme 4 Duyurusu](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-preview-4/)
- [.NET core 3.0 Preview 3 Duyurusu](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-preview-3/)
- [.NET core 3.0 Önizleme 2 Duyurusu](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-preview-2/)
- [.NET core 3.0 Önizleme 1 Duyurusu](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-preview-1-and-open-sourcing-windows-desktop-frameworks/)

## <a name="net-core-sdk-windows-installer"></a>.NET core SDK'sı, Windows Yükleyicisi

MSI yükleyicisini Windows için .NET Core 3. 0'ile başlayan değişti. SDK'sı yükleyicileri artık yerinde SDK bant dışı yayınlar yükseltir. Özellik bantları tanımlanmış *yüzlerce* içindeki gruplara *düzeltme eki* sürüm numarasının bölümü. Örneğin, **3.0. * 101*** ve **3.0. * 201*** sırasında iki farklı özellik bantları sürümlerinde olan **3.0. * 101*** ve **3.0. * 199*** bulunan aynı özellik bant. Ve ne zaman .NET Core SDK'sı **3.0. * 101*** olan .NET Core SDK'sı yüklü **3.0. * 100*** varsa makineden kaldırılacak. .NET Core SDK'sı **3.0. * 200*** aynı makinede, .NET Core SDK'sı yüklü **3.0. * 101*** kaldırılmaz.

Sürüm oluşturma hakkında daha fazla bilgi için bkz. [nasıl .NET Core tutulan genel bakış](../versions/index.md).

## <a name="c-80-preview"></a>C#8.0 Önizleme

.NET core 3.0 destekleyen C# 8 önizleme. Hakkında daha fazla bilgi için C# 8.0 özellikler bkz [yenilikler C# 8.0](../../csharp/whats-new/csharp-8.md).

## <a name="net-standard-21"></a>.NET standard 2.1

.NET Core 3.0 desteklemesine rağmen **.NET standart 2.1**, varsayılan `dotnet new classlib` şablon hedefleyen bir proje oluşturur **.NET Standard 2.0**. Hedef **.NET standart 2.1**, proje dosyanızı düzenleyin ve değiştirin `TargetFramework` özelliğini `netstandard2.1`:

```xml
<Project Sdk="Microsoft.NET.Sdk">
 
  <PropertyGroup>
    <TargetFramework>netstandard2.1</TargetFramework>
  </PropertyGroup>
 
</Project>
```

Visual Studio kullanıyorsanız, Visual Studio 2017'yi desteklemediğinden Visual Studio 2019 gereken **.NET standart 2.1** veya **.NET Core 3.0**. Kullanmanızı öneririz [Visual Studio 2019 güncelleştirme 1 Preview](https://visualstudio.microsoft.com/vs/preview/).

## <a name="improved-net-core-version-apis"></a>Geliştirilmiş .NET Core sürümü API'leri

.NET Core 3.0 API'leri bilgileri dönüş artık .NET Core ile sağlanan sürüm başlangıç beklediğiniz. Örneğin:

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
> Yeni değişiklik. Sürüm oluşturma düzeni değiştirdiği için teknik bir değişiklik budur.

## <a name="net-platform-dependent-intrinsics"></a>.NET platform bağımlı iç bilgileri

Gibi belirli performans odaklı CPU yönergeleri için erişime izin API'ler eklenmiştir **SIMD** veya **Bit işleme yönerge** ayarlar. Bu yönergeler, verileri verimli bir şekilde paralel işleme gibi bazı senaryolarda, önemli performans geliştirmeleri elde etmeye yardımcı olabilir. 

Uygun olan yerlerde, performansı artırmak için bu yönergeleri kullanarak .NET kitaplıklarına başlamıştır.

Daha fazla bilgi için [.NET platformu bağımlı yapı içleri](https://github.com/dotnet/designs/blob/master/accepted/platform-intrinsics.md).

## <a name="default-executables"></a>Varsayılan yürütülebilir dosyalar

.NET core şimdi yapılar [framework bağımlı yürütülebilir dosyaları](../deploying/index.md#framework-dependent-executables-fde) varsayılan olarak. Bu davranış, .NET Core genel olarak yüklenmiş bir sürümünü kullanan uygulamalar için yeni bir özelliktir. Daha önce yalnızca [müstakil dağıtımları](../deploying/index.md#self-contained-deployments-scd) yürütülebilir bir dosya oluşturur.

Sırasında `dotnet build` veya `dotnet publish`, kullandığınız SDK platform ve ortam ile eşleşen bir yürütülebilir dosya oluşturulur. Diğer yerel yürütülebilir dosyalar gibi olduğu gibi bu yürütülebilir dosyaları ile aynı şey geçerli olacaktır:

* Yürütülebilir dosya üzerine çift tıklayabilirsiniz.
* Doğrudan bir komut isteminden uygulama başlatma gibi `myapp.exe` Windows, şirket ve `./myapp` Linux ve Macos'ta.

## <a name="single-file-executables"></a>Tek Dosyalı yürütülebilir dosyalar

`dotnet publish` Komutu, platforma özgü tek dosyalı yürütülebilir dosyanın içine uygulamanızı paketleme destekler. Yürütülebilir dosya, kendiliğinden ve uygulamanızı çalıştırmak için gereken tüm bağımlılıkları (yerel dahil) içerir. Uygulamayı ilk kez çalıştırdığınızda, uygulama üzerinde uygulama tabanlı bir dizine ayıklanır ad ve tanımlayıcı oluşturun. Uygulamayı yeniden çalıştırdığınızda başlangıç daha hızlıdır. Uygulamanın yeni bir sürüm kullanılmadığı sürece kendisini ikinci kez ayıklamak gerekmez.

Tek dosyalı bir yürütülebilir dosya yayımlamayı ayarlamak `PublishSingleFile` projenizdeki veya komut satırı ile `dotnet publish` komutu:

```console
dotnet publish -r win10-x64 /p:PublishSingleFile=true
```

Tek dosya yayımlama hakkında daha fazla bilgi için bkz. [tek dosyalı bundler tasarım belge](https://github.com/dotnet/designs/blob/master/accepted/single-file/design.md).

## <a name="assembly-linking"></a>Derleme bağlama

.NET core SDK 3.0 IL analiz etme ve kullanılmayan derlemeleri kırpma uygulamaları boyutunu azaltabilirsiniz bir aracı ile gelir.

Kendi içindeki uygulamaları ana bilgisayara yüklenmesi .NET gerek kalmadan kodunuzu çalıştırmak için gereken her şeyi içerir. Ancak, birçok kez uygulamayı yalnızca framework işlevi için küçük bir kısmı gerektirir ve diğer kullanılmayan kitaplıklar kaldırılamadı.

.NET core kullanan bir ayarı artık içerir [IL bağlayıcı](https://github.com/mono/linker) uygulamanızın IL Tarama Aracı. Bu araç, hangi kod gereklidir ve kullanılmayan kitaplıkları ardından kırpar algılar. Bu araç, bazı uygulama dağıtım boyutunu önemli ölçüde azaltabilir.

Bu aracı etkinleştirmek için `<PublishTrimmed>` projenizde ayarlama ve kendi başına bir uygulama yayımlama:

```xml
<PropertyGroup>
  <PublishTrimmed>true</PublishTrimmed>
</PropertyGroup>
```

```console
dotnet publish -r <rid> -c Release
```

Örnek olarak, yaklaşık olarak 70 MB boyutunda yayımlandığında, verilen temel "Merhaba Dünya" yeni konsol projesi şablonu denk gelir. Kullanarak `<PublishTrimmed>`, boyutu yaklaşık 30 MB küçültülür.

Uygulamalar veya yansıtma ya da ilgili dinamik özellikleri kullanın (ASP.NET Core ve WPF dahil) çerçeveleri genellikle durumunda, kırpılmış zaman göz önünde bulundurmanız önemlidir. Bu arıza bağlayıcı bu dinamik davranış hakkında bilmez ve hangi framework türlerinin yansıma için gerekli olup olmadığını belirleyemez oluşur. IL bağlayıcı aracı, bu senaryonun farkında olması için yapılandırılabilir.

Aksi takdirde tüm kırpma sonra uygulamanızı test etmek emin olun.

IL bağlayıcı aracı hakkında daha fazla bilgi için bkz. [belgeleri](https://aka.ms/dotnet-illink) veya ziyaret [mono/bağlayıcı]( https://github.com/mono/linker) depo.

## <a name="tiered-compilation"></a>Katmanlı derleme

[Katmanlı derleme](https://devblogs.microsoft.com/dotnet/tiered-compilation-preview-in-net-core-2-1/) .NET Core 3.0 ile varsayılan olarak (TC) etkin. Bu özellik daha Desenlerinizi daha iyi performans için tam zamanında (JIT) derleyici kullanmak çalışma zamanı sağlar.

TC ana Avantajı (re-) jitting yöntemleriyle daha yavaş ancak-daha hızlı kod üretmek için ya da daha yüksek-kalite-ancak-yavaş kod üretmek için etkinleştirmektir. Bu, çeşitli aşamaları boyunca yürütmesinin kararlı bir duruma başlatmanın geçebileceği bir uygulamanın performansını artırmaya yardımcı olur. Bu, burada her yöntem derlendiğinde TC olmayan yaklaşım ile karşılaştırır, kararlı durum için başlatma performansını güçlü eğilimi nedeniyle bir tek yolu (aynı yüksek kaliteli katmanı).

Hızlı JIT (katman 0 jıtted kodu) etkinleştirmek için proje dosyanızda bu ayarı kullanın:

```xml
<PropertyGroup>
  <TieredCompilationQuickJit>true</TieredCompilationQuickJit>
</PropertyGroup>
```

TC tamamen devre dışı bırakmak için proje dosyanızda bu ayarı kullanın:

```xml
<TieredCompilation>false</TieredCompilation>
```

## <a name="readytorun-images"></a>ReadyToRun görüntüleri

Uygulama derlemeleriniz ReadyToRun (R2R) biçiminde derleme tarafından .NET Core uygulamanızın başlangıç süresini iyileştirebilir. R2R, zaman üretim (AOT) derlemesi bir biçimidir.

R2R ikili dosyaları, just-ın-time (JIT) derleyici, uygulama yükleri yapmanız gereken iş miktarını azaltarak başlangıç performansı artırın. İkili dosyaları, JIT oluşturmak için karşılaştırıldığında benzer yerel kod içerir.

R2R ikili dosyaları yine de bazı senaryolar ve aynı kodu yerel sürümü için gerekli olan iki ara dil (IL) kodu içerdiğinden daha büyüktür. Hedefleyen x64 Linux veya Windows x64 gibi belirli çalışma zamanı ortamları (RID) kendi içinde bir uygulama yayımladığınızda R2R yalnızca kullanılabilir.

Uygulamanızı R2R olarak derlemek için ekleme `<PublishReadyToRun>` ayarı:

```xml
<PropertyGroup>
  <PublishReadyToRun>true</PublishReadyToRun>
</PropertyGroup>
```

Kendi içinde bir uygulama yayımlayın. Örneğin, bu komut Windows 64-bit sürümü için kendi içinde bir uygulama oluşturur:

```console
dotnet publish -c Release -r win-x64 --self-contained true
```

### <a name="cross-platformarchitecture-restrictions"></a>Çapraz Platform/mimari kısıtlamaları

ReadyToRun derleyici, şu anda çapraz hedefleme desteklememektedir. Belirli bir hedef derlemeniz gerekir. Örneğin, Windows için x64 R2R görüntüleri istiyorsanız, o ortamda publish komutunu çalıştırmak gerekir.

Çapraz-hedefleyen için özel durumlar:

- Windows x64 Windows ARM32 ve ARM64 x86 derlemek için kullanılabilir görüntüler.
- Windows x86 Windows ARM32 görüntüleri derlemek için kullanılabilir.
- Linux x64 Linux ARM32 ve ARM64 görüntüleri derlemek için kullanılabilir.

## <a name="build-copies-dependencies"></a>Derleme bağımlılıkları kopyalar.

`dotnet build` Komutu artık kopyalar NuGet bağımlılıklarını uygulamanız için NuGet önbellekten için derleme çıktısı klasörü. Daha önce bağımlılıkları parçası olarak yalnızca kopyalanan `dotnet publish`.

Yayımlama, yayınlama, bağlama ve razor sayfası hala gerektirir gibi bazı işlemler vardır.

## <a name="local-tools"></a>Yerel Araçlar

.NET core 3.0 yerel araçlar sunar. Yerel Araçlar benzer [genel Araçları](../tools/global-tools.md) ancak disk üzerindeki belirli bir konum ile ilişkilidir. Yerel araçları, küresel olarak kullanılabilir değildir ve NuGet paketleri olarak dağıtılır.

> [!WARNING]
> Çalıştırma gibi .NET Core 3.0 Önizleme 1 ' yerel Araçlar çalıştıysanız `dotnet tool restore` veya `dotnet tool install`, yerel Araçlar önbellek klasörünü silin. Aksi takdirde, yerel Araçlar üzerinde daha yeni bir sürüm çalışmaz. Bu klasör şu konumdadır:
>
> MacOS, Linux: `rm -r $HOME/.dotnet/toolResolverCache`
>
> Windows üzerinde: `rmdir /s %USERPROFILE%\.dotnet\toolResolverCache`

Yerel Araçlar kullanan bir bildirim dosyası adına `dotnet-tools.json` geçerli dizininizde. Bu bildirim dosyası, bu klasörü ve altındaki kullanılabilir olması için Araçlar tanımlar. Bildirim dosyası ile kodunuzu çalışır herkes geri yükleme ve böylelikle aynı araçlarını kullanın emin olmak için kodunuzla dağıtabilirsiniz.

Hem genel hem de yerel araçları için çalışma zamanı'nın uyumlu bir sürümü gereklidir. Birçok araç NuGet.org üzerinde şu anda .NET Core çalışma zamanı 2.1 hedefleyin. Bu araçlar genel veya yerel olarak yüklemek için yükleme yine [NET Core 2.1 çalışma zamanı](https://dotnet.microsoft.com/download/dotnet-core/2.1).

## <a name="major-version-roll-forward"></a>Ana sürüm ileri sarma

.NET core 3.0, .NET Core için en son ana sürüm ileriye işlem gerçekleştirilebilmesi için uygulamanızı sağlayan bir Tercihli özellik sunmaktadır. Ayrıca, yeni bir ayar ileri sarma uygulamanıza nasıl uygulanacağını denetlemek için eklendi. Bunu aşağıdaki yöntemlerle yapılandırılabilir:

- Proje dosyası özelliği: `RollForward`
- Çalışma zamanı yapılandırma dosyası özelliği: `rollForward`
- Ortam değişkeni: `DOTNET_ROLL_FORWARD`
- Komut satırı bağımsız değişkeni: `--roll-forward`

Aşağıdaki değerlerden biri belirtilmelidir. Ayar atlanırsa **küçük** varsayılandır.

- **LatestPatch**\
İleriye işlem gerçekleştirilebilmesi için en yüksek düzeltme eki sürümü. Bu, alt sürüm ileri sarma devre dışı bırakır.
- **Küçük**\
En düşük daha alt sürümü için İleri istenen alt sürümü eksik sarabilirsiniz. İstenen alt sürümü varsa, ardından **LatestPatch** İlkesi kullanılır.
- **Büyük**\
İstenen sürümle eksik olması durumunda yüksek ana sürüm en düşük ve en düşük alt sürüm İleri sarmanın. İstenen ana sürüm varsa, ardından **küçük** İlkesi kullanılır.
- **LatestMinor**\
İstenen alt sürümü mevcut olsa bile, İleri en yüksek ikincil sürümüne geri almak. Bileşeni için barındırma senaryolarında yöneliktir.
- **latestMajor**\
İstenen ana olsa bile iletmek için en büyük ve en yüksek ikincil sürüm döndürün. Bileşeni için barındırma senaryolarında yöneliktir.
- **Devre dışı bırak**\
İleri sarmanın yok. Yalnızca belirtilen sürüme bağlayın. Bu ilke, en son düzeltme eklerini İleri sarmanın özelliği devre dışı bırakır çünkü genel kullanım için önerilmez. Bu değer, yalnızca test etmek için önerilir.

Yanında **devre dışı** ayarlama, tüm ayarlarını yüksek kullanılabilir bir düzeltme eki sürümü kullanır.

## <a name="windows-desktop"></a>Windows masaüstü

.NET core 3.0, Windows Presentation Foundation (WPF) ve Windows Forms kullanılarak Windows Masaüstü uygulamaları destekler. Bu çerçeveler ile modern denetimleri ve Windows kullanıcı Arabirimi XAML kitaplığından (WinUI) Fluent stil kullanarak da destekler [XAML Adaları](/windows/uwp/xaml-platform/xaml-host-controls).

Windows Masaüstü bileşen Windows parçasıdır .NET Core 3.0 SDK.

Şunlarla birlikte yeni bir Windows Forms ve WPF uygulaması oluşturabilirsiniz `dotnet` komutları:

```console
dotnet new wpf
dotnet new winforms
```

Visual Studio 2019 ekler **yeni proje** .NET Core 3.0, Windows Forms ve WPF şablonları.

Mevcut bir .NET Framework uygulaması bağlantı noktası hakkında daha fazla bilgi için bkz. [bağlantı noktası WPF projeleri](../porting/wpf.md) ve [bağlantı noktası Windows Forms projeleri](../porting/winforms.md).

## <a name="com-callable-components---windows-desktop"></a>COM çağrılabilir bileşenleri - Windows Masaüstü

Windows üzerinde COM-yönetilen çağrılabilir bileşenler oluşturabilirsiniz. Bu özellik, .NET Core ile COM Eklentisi modelleri kullanın ve .NET Framework ile eşlik sağlamak önemlidir.

.NET Framework aksine burada *mscoree.dll* kullanılan COM sunucusu olarak yerel Başlatıcısı DLL'ye .NET Core ekleyeceksiniz *bin* , COM bileşeni oluşturma sırasında dizin.

Bir COM bileşeni oluşturma ve bunu kullanma örneği için bkz: [COM tanıtım](https://github.com/dotnet/samples/tree/master/core/extensions/COMServerDemo).

## <a name="msix-deployment---windows-desktop"></a>MSIX dağıtım - Windows Masaüstü

[MSIX](https://docs.microsoft.com/windows/msix/) yeni bir Windows uygulama paketi biçimi. .NET Core 3.0 Windows 10 Masaüstü uygulamaları dağıtmak için kullanılabilir.

[Windows uygulaması paketleme projesi](https://docs.microsoft.com/windows/uwp/porting/desktop-to-uwp-packaging-dot-net), Visual Studio 2019 bulunan MSIX paketlerle oluşturmanıza olanak tanır [müstakil](../deploying/index.md#self-contained-deployments-scd) .NET Core uygulamaları.

.NET Core proje dosyası içinde desteklenen çalışma zamanları belirtmelisiniz `<RuntimeIdentifiers>` özelliği:

```xml
<RuntimeIdentifiers>win-x86;win-x64</RuntimeIdentifiers>
```

## <a name="winforms-highdpi"></a>WinForms HighDPI

.NET core Windows Forms uygulamaları, yüksek DPI moduyla ayarlayabilirsiniz <xref:System.Windows.Forms.Application.SetHighDpiMode(System.Windows.Forms.HighDpiMode)?displayProperty=nameWithType>. `SetHighDpiMode` Yöntemini ayarlar karşılık gelen yüksek DPI modu ayarı gibi diğer yollarla ayarlanmadığı sürece `App.Manifest` veya P/Invoke önce `Application.Run`.

Olası `highDpiMode` değerler olarak ifade edilen <xref:System.Windows.Forms.HighDpiMode?displayProperty=nameWithType> enum şunlardır:

* `DpiUnaware`
* `SystemAware`
* `PerMonitor`
* `PerMonitorV2`
* `DpiUnawareGdiScaled`

Yüksek DPI modları hakkında daha fazla bilgi için bkz. [Windows üzerinde yüksek DPI Masaüstü uygulama geliştirme](/windows/desktop/hidpi/high-dpi-desktop-application-development-on-windows).

### <a name="ranges-and-indices"></a>Aralıkları ve dizinler

Yeni <xref:System.Index?displayProperty=nameWithType> türü, dizin oluşturma işlemi için kullanılabilir. Birinden oluşturabileceğiniz bir `int` baştan ya da öneki sayar `^` işleci (C#) sonundan sayar:

```csharp
Index i1 = 3;  // number 3 from beginning
Index i2 = ^4; // number 4 from end
int[] a = { 0, 1, 2, 3, 4, 5, 6, 7, 8, 9 };
Console.WriteLine($"{a[i1]}, {a[i2]}"); // "3, 6"
```

Ayrıca <xref:System.Range?displayProperty=nameWithType> oluşan iki tür `Index` bir başlangıç ve bitiş için bir değer ve ile yazılmış bir `x..y` aralık ifade (C#). Ardından ile dizinleyebilirsiniz bir `Range`, dilim oluşturur:

```csharp
var slice = a[i1..i2]; // { 3, 4, 5 }
```

Daha fazla bilgi için [aralıkları ve dizinlerini öğretici](../../csharp/tutorials/ranges-indexes.md).

### <a name="async-streams"></a>Zaman uyumsuz akışlar

<xref:System.Collections.Generic.IAsyncEnumerable%601> Türüdür, yeni bir zaman uyumsuz sürümü <xref:System.Collections.Generic.IEnumerable%601>. Dil sayesinde `await foreach` üzerinden `IAsyncEnumerable<T>` öğeleri kullanma ve `yield return` öğeleri oluşturmak için onlara.

Aşağıdaki örnek, hem üretim hem de zaman uyumsuz akışlar kullanımını gösterir. `foreach` Deyimi, async ve kendisini kullanan `yield return` arayanlar için zaman uyumsuz bir akış oluşturmak için. Bu düzen (kullanarak `yield return`) zaman uyumsuz akışlar oluşturmayı için önerilen modelidir.

```csharp
async IAsyncEnumerable<int> GetBigResultsAsync()
{
    await foreach (var result in GetResultsAsync())
    {
        if (result > 20) yield return result; 
    }
}
```

İmkanına yanı sıra `await foreach`, zaman uyumsuz yineleyiciler, örneğin, döndüren bir yineleyicinin oluşturabilirsiniz bir `IAsyncEnumerable/IAsyncEnumerator` her ikisini yapabilirsiniz `await` ve `yield` içinde. Çıkarılması gereken nesneler için kullanabileceğiniz `IAsyncDisposable`, çeşitli BCL türleri uygulayan, gibi `Stream` ve `Timer`.

Daha fazla bilgi için [zaman uyumsuz akışlar öğretici](../../csharp/tutorials/generate-consume-asynchronous-stream.md).

## <a name="ieee-floating-point-improvements"></a>IEEE kayan nokta geliştirmeleri

Kayan nokta API'leri güncelleştiriliyor uymak için [IEEE 754-2008 düzeltme](https://en.wikipedia.org/wiki/IEEE_754-2008_revision). Tüm kullanıma sunmak için bu değişikliklerin amacı olan **gerekli** işlemleri ve davranışsal IEEE belirtimi ile uyumlu olduğunuzdan emin olun. Kayan nokta iyileştirmeleri hakkında daha fazla bilgi için bkz. [Floating-Point ayrıştırma ve biçimlendirme geliştirmeleri .NET Core 3. 0'ı](https://devblogs.microsoft.com/dotnet/floating-point-parsing-and-formatting-improvements-in-net-core-3-0/) blog gönderisi.

Ayrıştırma ve biçimlendirme düzeltmeleri içerir:

* Doğru ayrıştırma ve herhangi bir uzunluktaki girişleri yuvarlar.
* Doğru ayrıştırma ve negatif sıfır biçimlendirin.
* Düzgün ayrıştırılamadı `Infinity` ve `NaN` büyük küçük harf duyarsız bir denetimi yapmak ve isteğe bağlı bir önceki izin vererek `+` uygunsa.

Yeni <xref:System.Math?displayProperty=nameWithType> API'leri içerir:

* <xref:System.Math.BitIncrement(System.Double)> ve <xref:System.Math.BitDecrement(System.Double)>\
Karşılık gelen `nextUp` ve `nextDown` IEEE operations. Karşılaştıran en küçük kayan noktalı sayı (sırasıyla) giriş'den küçük veya büyük döndürürler. Örneğin, `Math.BitIncrement(0.0)` döndürecekti `double.Epsilon`.

* <xref:System.Math.MaxMagnitude(System.Double,System.Double)> ve <xref:System.Math.MinMagnitude(System.Double,System.Double)>\
Karşılık gelen `maxNumMag` ve `minNumMag` IEEE işlemleri, bunlar döndürür (sırasıyla) büyük ya da büyüklük açısından iki girişe daha düşük olan değer. Örneğin, `Math.MaxMagnitude(2.0, -3.0)` döndürecekti `-3.0`.

* <xref:System.Math.ILogB(System.Double)>\
Karşılık gelen `logB` bir tamsayı değeri döndüren IEEE işlemi, giriş parametresinin tamsayı 2 tabanında günlük döndürür. Bu yöntem etkili bir şekilde aynıdır `floor(log2(x))`, ancak en az yuvarlama hatası işler bitti.

* <xref:System.Math.ScaleB(System.Double,System.Int32)>\
Karşılık gelen `scaleB` bir tamsayı değeri alan IEEE işlemi döndürür etkili bir şekilde `x * pow(2, n)`, yuvarlama en az bir hata ile tamamlandı ancak.

* <xref:System.Math.Log2(System.Double)>\
Karşılık gelen `log2` IEEE işlemi 2 tabanlı logaritmasını döndürür. Yuvarlama hata en aza indirir.

* <xref:System.Math.FusedMultiplyAdd(System.Double,System.Double,System.Double)>\
Karşılık gelen `fma` IEEE işlem gerçekleştirdiği bir çarpım Çarp. Diğer bir deyişle, mevcut `(x * y) + z` tek bir işlem olarak, var-tarafından yuvarlama hata en aza indirir. Örnek verilebilir `FusedMultiplyAdd(1e308, 2.0, -1e308)` döndüren `1e308`. Normal `(1e308 * 2.0) - 1e308` döndürür `double.PositiveInfinity`.

* <xref:System.Math.CopySign(System.Double,System.Double)>\
Karşılık gelen `copySign` IEEE işlemi değerini döndürür `x`, ancak işaretini `y`.

## <a name="fast-built-in-json-support"></a>Hızlı yerleşik JSON desteği

.NET kullanıcıları büyük ölçüde üzerinde yararlandı [ **Json.NET** ](https://www.newtonsoft.com/json) ve iyi seçenekleri olmaya devam diğer popüler JSON kitaplıkları. **Json.NET** UTF-16 başlık altında olduğu temel veri türü, .NET dizeleri kullanır.

Yeni yerleşik JSON desteği, yüksek performanslı, düşük ayırma ve temel `Span<byte>`. .NET Core 3.0 için yeni ana JSON ile ilgili üç eklenmiştir <xref:System.Text.Json?displayProperty=nameWithType> ad alanı. Bu tür olmayan *henüz* düz eski CLR nesnesi (POCO) serileştirme ve seri durumundan çıkarma destekler.

### <a name="utf8jsonreader"></a>Utf8JsonReader

<xref:System.Text.Json.Utf8JsonReader?displayProperty=nameWithType> yüksek performanslı, düşük ayırma, yalnızca iletme Okuyucu için UTF-8 kodlamalı JSON metin okuma, bir `ReadOnlySpan<byte>`. `Utf8JsonReader` Özel çözümleyiciler ve deserializers oluşturmak için kullanılan bir temel, alt düzey türüdür. Kullanarak yeni bir JSON yükü okuma `Utf8JsonReader` reader'ı kullanarak daha hızlı bir şekilde x 2 **Json.NET**. JSON belirteçleri (UTF-16) dizeler olarak actualize gerekene kadar tahsis etmez.

İşte bir örnek üzerinden okuma [ **launch.json** ](https://github.com/dotnet/samples/blob/master/snippets/core/whats-new/whats-new-in-30/cs/launch.json) Visual Studio Code tarafından oluşturulan dosya:

[!CODE-csharp[Utf8JsonReader](~/samples/snippets/core/whats-new/whats-new-in-30/cs/program.cs#PrintJson)]

[!CODE-csharp[Utf8JsonReader](~/samples/snippets/core/whats-new/whats-new-in-30/cs/program.cs#PrintJsonCall)]

### <a name="utf8jsonwriter"></a>Utf8JsonWriter

<xref:System.Text.Json.Utf8JsonWriter?displayProperty=nameWithType> bir yüksek performanslı, genel .NET türleri JSON metni yalnızca iletme UTF-8 olarak kodlanmış biçimde yazmak ister önbelleğe alınmamış, sağlar `String`, `Int32`, ve `DateTime`. Okuyucu gibi yazıcı özel seri hale getiricileri genişletme oluşturmak için kullanılan bir temel, alt düzey türüdür. Kullanarak yeni bir JSON yükünü yazmayı `Utf8JsonWriter` yazıcıdan kullanarak daha hızlı % 30-80'idir **Json.NET** ve tahsis etmez.

### <a name="jsondocument"></a>JsonDocument

<xref:System.Text.Json.JsonDocument?displayProperty=nameWithType> üst kısmındaki yerleşik `Utf8JsonReader`. `JsonDocument` JSON verilerini ayrıştırma ve bir salt okunur belge nesne modeli (DOM), derleme olanağı, rastgele erişim ve numaralandırma desteklemek için sorgulanabilir sağlar. Verileri oluşturan JSON öğeleri aracılığıyla erişilebilir <xref:System.Text.Json.JsonElement> tarafından sunulan tür `JsonDocument` adlı bir özellik olarak `RootElement`. `JsonElement` Ortak .NET türlerine JSON metnine dönüştürmek için API'leri ile birlikte JSON dizi ve nesne numaralandırıcıları içerir. Tipik bir JSON yükü ayrıştırma ve tüm kullanarak üyelerine erişilmesi `JsonDocument` 2-3 x daha hızlı bir şekilde **Json.NET** makul boyutlu veriler için biraz ayırmaları ile (yani, < 1 MB).

İşte bir örnek kullanımı `JsonDocument` ve `JsonElement` başlangıç noktası olarak kullanılabilir:

İşte bir C# 8.0 örneği aracılığıyla okuma [ **launch.json** ](https://github.com/dotnet/samples/blob/master/snippets/core/whats-new/whats-new-in-30/cs/launch.json) Visual Studio Code tarafından oluşturulan dosya:

[!CODE-csharp[JsonDocument](~/samples/snippets/core/whats-new/whats-new-in-30/cs/program.cs#ReadJson)]

[!CODE-csharp[JsonDocument](~/samples/snippets/core/whats-new/whats-new-in-30/cs/program.cs#ReadJsonCall)]

### <a name="jsonserializer"></a>JsonSerializer

<xref:System.Text.Json.Serialization.JsonSerializer?displayProperty=nameWithType> üst kısmındaki yerleşik <xref:System.Text.Json.Utf8JsonReader> ve <xref:System.Text.Json.Utf8JsonWriter> JSON belgeleri ve parçaları çalışırken hızlı düşük bellek serileştirme seçeneği sağlamak.

İNCELEME: https://github.com/dotnet/corefx/blob/master/src/System.Text.Json/docs/SerializerProgrammingModel.md bu makaleye bağlantı örneği

Bir nesne json'a serileştirilirken bir örnek aşağıda verilmiştir:

[!CODE-csharp[JsonSerializer](~/samples/snippets/core/whats-new/whats-new-in-30/cs/JSON.cs#JsonSerialize)]

Bir nesne için bir JSON dizesini seri durumdan çıkarılırken bir örnek aşağıda verilmiştir. Önceki örnek tarafından oluşturulanla JSON dizesi kullanabilirsiniz:

[!CODE-csharp[JsonDeserializer](~/samples/snippets/core/whats-new/whats-new-in-30/cs/JSON.cs#JsonDeserialize)]

## <a name="interop-improvements"></a>Birlikte çalışma geliştirmeleri

.NET core 3.0 yerel API Interop artırır.

### <a name="type-nativelibrary"></a>Tür: NativeLibrary

<xref:System.Runtime.InteropServices.NativeLibrary?displayProperty=nameWithType> (.NET Core P/Invoke olarak aynı yük mantığı kullanarak) yerel bir kitaplığı yüklemeye yönelik bir kapsülleme sağlar ve ilgili yardımcı işlevleri gibi sağlayarak `getSymbol`. Kod örneği için bkz: [DLLMap tanıtım](https://github.com/dotnet/samples/tree/master/core/extensions/AppWithPlugin).

### <a name="windows-native-interop"></a>Windows yerel birlikte çalışabilirliği

Windows formunda düz C API'leri, COM ve WinRT zengin yerel bir API sunar. .NET Core destekler while **P/Invoke**, .NET Core 3.0 yeteneği ekler **COM API işlemi** ve **WinRT API'lar etkinleştirme**. Kod örneği için bkz: [Excel Demo](https://github.com/dotnet/samples/tree/master/core/extensions/ExcelDemo).

## <a name="http2-support"></a>HTTP/2 desteği

<xref:System.Net.Http.HttpClient?displayProperty=nameWithType> HTTP/2 protokolüne türünü destekler. HTTP/2 etkinleştirilirse, HTTP protokolü sürümünü TLS/ALPN belirlenir ve kullanmak sunucu seçerse HTTP/2 kullanılır.

Varsayılan protokol HTTP/1.1 kalır, ancak HTTP/2 iki farklı şekilde etkinleştirilebilir. İlk olarak, HTTP/2 kullanmak için HTTP istek iletisi ayarlayabilirsiniz:

[!CODE-csharp[Http2Request](~/samples/snippets/core/whats-new/whats-new-in-30/cs/http.cs#Request)]

İkinci olarak, değiştirebileceğiniz <xref:System.Net.Http.HttpClient> HTTP/2 varsayılan olarak kullanmak üzere:

[!CODE-csharp[Http2Client](~/samples/snippets/core/whats-new/whats-new-in-30/cs/http.cs#Client)]

Birden çok kez bir uygulama geliştirirken, şifrelenmemiş bir bağlantı kullanmak istediğiniz. Hedef uç noktası, HTTP/2 kullanacaklardır biliyorsanız, şifrelenmemiş HTTP/2 bağlantılarında etkinleştirebilirsiniz. Bu ayarlayarak etkinleştirebilirsiniz `DOTNET_SYSTEM_NET_HTTP_SOCKETSHTTPHANDLER_HTTP2UNENCRYPTEDSUPPORT` ortam değişkenine `1` veya uygulama bağlamında etkinleştirerek:

[!CODE-csharp[Http2Context](~/samples/snippets/core/whats-new/whats-new-in-30/cs/http.cs#AppContext)]

## <a name="tls-13--openssl-111-on-linux"></a>TLS 1.3 & Linux'ta OpenSSL 1.1.1

.NET core artık avantajlarından yararlanır [OpenSSL 1.1.1 TLS 1.3 desteği](https://www.openssl.org/blog/blog/2018/09/11/release111/), verilen ortamda kullanılabilir olduğunda. 1\.3 TLS ile:

* Defa bağlantı azaltılmış gidiş dönüş istemci ve sunucu arasında gerekli ile geliştirildi.
* Geliştirilmiş güvenlik çeşitli eski ve güvenli şifreleme algoritmaları kaldırılmasını nedeniyle.

Kullanılabilir olduğunda, .NET Core 3.0 kullanan **OpenSSL 1.1.1**, **OpenSSL 1.1.0**, veya **OpenSSL 1.0.2** bir Linux sisteminde. Zaman **OpenSSL 1.1.1** kullanılabilir, her ikisi de <xref:System.Net.Security.SslStream?displayProperty=nameWithType> ve <xref:System.Net.Http.HttpClient?displayProperty=nameWithType> türleri kullanırsınız **TLS 1.3** (istemci ve sunucu desteği varsayılarak **TLS 1.3**).

>[!IMPORTANT]
>Windows ve macOS henüz desteklemediği **TLS 1.3**. .NET core 3.0 destekleyeceği **TLS 1.3** desteği kullanılabilir olduğunda bu işletim sistemlerinde.

Aşağıdaki C# 8.0 örnek gösterir Ubuntu bağlanma 18.10 üzerinde .NET Core 3.0 <https://www.cloudflare.com>:

[!CODE-csharp[TLSExample](~/samples/snippets/core/whats-new/whats-new-in-30/cs/TLS.cs#TLS)]

## <a name="cryptography-ciphers"></a>Şifreleme şifrelemeleri

.NET 3.0 için destek ekler **AES GCM** ve **AES-CCM** ile uygulanan şifrelemeleri, <xref:System.Security.Cryptography.AesGcm?displayProperty=nameWithType> ve <xref:System.Security.Cryptography.AesCcm?displayProperty=nameWithType> sırasıyla. Her ikisi de bu algoritmalar olan [ilişkilendirme veri (AEAD) algoritmaları ile kimliği doğrulanmış şifreleme](https://en.wikipedia.org/wiki/Authenticated_encryption).

Aşağıdaki kodu `AesGcm` şifrelemek ve rastgele verilerin şifresini çözmek için şifre.

[!CODE-csharp[AesGcm](~/samples/snippets/core/whats-new/whats-new-in-30/cs/Cipher.cs#AesGcm)]

## <a name="cryptographic-key-importexport"></a>Şifreleme anahtarı içeri/dışarı aktarma

.NET core 3.0 standart biçimlerinden asimetrik ortak ve özel anahtarı dışarı aktarma ve içeri aktarma destekler. X.509 sertifikası kullanmanız gerekmez.

Tüm anahtar türleri gibi *RSA*, *DSA*, *ECDsa*, ve *ECDiffieHellman*, aşağıdaki biçimlerde destekler:

* **Ortak anahtar**
  * X.509 SubjectPublicKeyInfo

* **özel anahtar**
  * PKCS #8 PrivateKeyInfo
  * PKCS #8 EncryptedPrivateKeyInfo

RSA desteği de anahtarları:

* **Ortak anahtar**
  * PKCS#1 RSAPublicKey

* **özel anahtar**
  * PKCS #1 RSAPrivateKey

Dışarı aktarma yöntemleri DER ile kodlanmış ikili verileri oluşturmak ve içeri aktarma metotları aynı beklerler. Bir anahtar metin dostu PEM biçiminde depolanır, çağırana base64 gerekir-içerik alma yöntemini çağırmadan önce kod çözme.

[!CODE-csharp[RSA](~/samples/snippets/core/whats-new/whats-new-in-30/cs/RSA.cs#Rsa)]

**PKCS #8** dosyaları inceledi ile <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo?displayProperty=nameWithType> ve **PFX/PKCS #12** dosyaları inceledi ile <xref:System.Security.Cryptography.Pkcs.Pkcs12Info?displayProperty=nameWithType>. **PFX/PKCS #12** dosyalar işlenebilir <xref:System.Security.Cryptography.Pkcs.Pkcs12Builder?displayProperty=nameWithType>.

## <a name="serialport-for-linux"></a>Linux için çevirmek için SerialPort

.NET core 3.0 destekleyen <xref:System.IO.Ports.SerialPort?displayProperty=nameWithType> Linux üzerinde.

Daha önce yalnızca kullanarak desteklenen .NET Core `SerialPort` Windows üzerinde.

## <a name="docker-and-cgroup-memory-limits"></a>Docker ve cgroup bellek sınırları

Preview 3'ten itibaren Docker ile Linux üzerinde .NET Core 3.0 çalıştıran daha iyi cgroup bellek sınırlarını ile çalışır. Bellek sınırları, Docker kapsayıcısı gibi çalışan `docker run -m`, .NET Core nasıl davranacağını değiştirir.

* Varsayılan çöp toplayıcı (GC) yığın boyutu: en fazla 20 mb veya bellek sınırı kapsayıcı üzerindeki %75.
* Açık boyut bir mutlak sayı veya cgroup sınırı yüzdesi ayarlayabilirsiniz.
* GC yığınında başına en az ayrılmış kesim boyutu 16 mb'tır. Bu boyut makinelerde oluşturulan yığınlar sayısını azaltır.

## <a name="smaller-garbage-collection-heap-sizes"></a>Küçük çöp toplama, öbek boyutları

.NET Core kullanarak daha az bellek kaynaklanan Atık toplayıcısının varsayılan öbek boyutu azaltıldı. Bu değişiklik, daha iyi modern işlemci önbellek boyutu nesil 0 ayırma bütçeyle ile uyumludur.

## <a name="garbage-collection-large-page-support"></a>Çöp toplama büyük sayfa desteği

Büyük sayfaları (diğer adıyla büyük Linux üzerinde), işletim sisteminin bu büyük sayfalar isteyen uygulama performansını artırmak için yerel sayfa boyutundan büyük (genellikle 4 K) bellek bölümlerinin oluşturmak mümkün olduğu bir özelliğidir.

Çöp toplayıcı ile artık yapılandırılabilir **GCLargePages** Tercihli özellik ayarlanması büyük sayfalarında Windows ayırmak seçin.

## <a name="gpio-support-for-raspberry-pi"></a>Raspberry Pi GPIO'yu desteği

İki paket GPIO'yu programlama için kullanabileceğiniz NuGet yayımlanmış olan:

* [System.Device.Gpio](https://www.nuget.org/packages/System.Device.Gpio)
* [Iot.Device.Bindings](https://www.nuget.org/packages/Iot.Device.Bindings)

API'leri için GPIO paketleri dahil *GPIO'yu*, *SPI*, *I2C*, ve *PWM* cihazlar. IOT bağlamaları paketi, cihaz bağlamaları içerir. Daha fazla bilgi için [cihazları GitHub deposunu](https://github.com/dotnet/iot/blob/master/src/devices/).

## <a name="arm64-linux-support"></a>ARM64 Linux desteği

.NET core 3.0 Linux ARM64 için desteği ekler. ARM64 için birincil kullanım durumu şu anda IOT senaryoları ile aşamasındadır. Daha fazla bilgi için [.NET Core ARM64 durumu](https://github.com/dotnet/announcements/issues/82).

[ARM64 üzerinde .NET Core için docker görüntülerini](https://hub.docker.com/r/microsoft/dotnet/) kullanılabilir Alpine, Debian ve Ubuntu.

> [!NOTE]
> **ARM64** Windows Destek işlemi henüz kullanılamıyor.
