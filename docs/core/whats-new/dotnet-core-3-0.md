---
title: .NET Core 3. 0'yenilikler nelerdir?
description: .NET Core 3. 0 ' bulunan yeni özellikler hakkında bilgi edinin.
dev_langs:
- csharp
- vb
author: thraka
ms.author: adegeo
ms.date: 12/31/2018
ms.openlocfilehash: 086be4649f4e7e27ff98df6f26d08856683865c8
ms.sourcegitcommit: 438919211260bb415fc8f96ca3eabc33cf2d681d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/16/2019
ms.locfileid: "59611789"
---
# <a name="whats-new-in-net-core-30-preview-2"></a>.NET Core 3.0 (Önizleme 2) yenilikler

Bu makalede, .NET Core 3.0 (Önizleme 2) Yenilikler açıklanır. Büyük iyileştirmeler Windows Masaüstü uygulamaları (yalnızca Windows) için destek biridir. Windows Masaüstü adlı bir .NET Core 3.0 SDK'sı bileşeni yararlanarak, Windows Presentation Foundation (WPF) uygulamaları ve Windows Forms bağlantı noktası. Gerekirse Windows Masaüstü bileşen yalnızca desteklenen ve Windows üzerinde dahil. Daha fazla bilgi için konudaki [Windows Masaüstü](#windows-desktop) aşağıda.

.NET core 3.0 için destek ekler C# 8.0.

[İndirin ve .NET Core 3.0 Önizleme 2 ile çalışmaya başlama](https://aka.ms/netcore3download) şu anda Windows, Mac ve Linux üzerinde. Yayın içinde tüm ayrıntılarını görebilirsiniz [.NET Core 3.0 Preview 2 sürüm notları](https://aka.ms/netcore3releasenotes).

Her sürümü ile yayımlanmış olan hakkında daha fazla bilgi için aşağıdaki duyuruları bakın:

- [.NET core 3.0 Önizleme 1 Duyurusu](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-preview-1-and-open-sourcing-windows-desktop-frameworks/)
- [.NET core 3.0 Önizleme 2 Duyurusu](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-preview-2/)

## <a name="c-8"></a>C# 8

.NET core 3.0 destekleyen C# 8 ve .NET Core 3.0 Önizleme 2'den itibaren bu yeni özellikleri destekler. Hakkında daha fazla bilgi için C# 8.0 özellikler, aşağıdaki blog gönderilerine bakın:

- [Desenler ile daha fazlasını yapın C# 8.0](https://devblogs.microsoft.com/dotnet/do-more-with-patterns-in-c-8-0/)
- [Ele C# 8.0 bir döngü için](https://devblogs.microsoft.com/dotnet/take-c-8-0-for-a-spin/)
- [Building C# 8.0](https://devblogs.microsoft.com/dotnet/building-c-8-0/)

### <a name="ranges-and-indices"></a>Aralıkları ve dizinler

Yeni `Index` türü, dizin oluşturma işlemi için kullanılabilir. Birinden oluşturabileceğiniz bir `int` baştan ya da öneki sayar `^` işleci (C#) sonundan sayar:

```csharp
Index i1 = 3;  // number 3 from beginning
Index i2 = ^4; // number 4 from end
int[] a = { 0, 1, 2, 3, 4, 5, 6, 7, 8, 9 };
Console.WriteLine($"{a[i1]}, {a[i2]}"); // "3, 6"
```

Ayrıca bir `Range` oluşan iki tür `Index` bir başlangıç ve bitiş için bir değer ve ile yazılmış bir `x..y` aralık ifade (C#). Ardından ile dizinleyebilirsiniz bir `Range` dilim oluşturmak için:

```csharp
var slice = a[i1..i2]; // { 3, 4, 5 }
```

### <a name="async-streams"></a>Zaman uyumsuz akışlar

`IAsyncEnumerable<T>` Türüdür, yeni bir zaman uyumsuz sürümü `IEnumerable<T>`. Dil sayesinde `await foreach` üzerinden `IAsyncEnumerable<T>` öğeleri kullanma ve `yield return` öğeleri oluşturmak için onlara.

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

> [!NOTE]
> Zaman uyumsuz akışlar ile ya da Visual Studio 2019 geliştirmek istiyorsanız kullanmak için .NET Core 3.0 Önizleme 2 veya en son önizlemesi ihtiyacınız [ C# Visual Studio Code uzantısı](https://github.com/OmniSharp/omnisharp-vscode/releases/tag/v1.18.0-beta5). Komut satırından .NET Core 3.0 Önizleme 2 kullanıyorsanız, daha sonra her şeyin beklendiği gibi çalışır.

### <a name="using-declarations"></a>Bildirimi kullanarak

*Bildirimi kullanarak* nesnenizin emin olmak için yeni bir yolunu düzgün bir şekilde elden olan. A *using bildirimi* kapsamda devam ederken nesne etkin tutar. Nesne kapsam dışına sunulduktan sonra otomatik olarak kapatılır. Bu iç içe geçmiş azaltır *using deyimlerini* ve kodunuzu daha temiz yapın.

```csharp
static void Main(string[] args)
{
    using var options = Parse(args);
    if (options["verbose"]) { WriteLine("Logging..."); }

} // options disposed here
```

### <a name="switch-expressions"></a>Anahtar ifadeler

*Anahtar ifadeleri* daha net bir şekilde yöntemlerinden biri olan bir *geçiş deyimi* olduğundan bir ifade, ancak bir değer döndürür. *Anahtar ifadeler* desen eşleştirme ile de tamamen tümleşiktir ve atma deseni kullanın `_`temsil etmek için `default` değeri.

Sözdizimi gördüğünüz *anahtar ifadeleri* aşağıdaki örnekte:

```csharp
static string Display(object o) => o switch
{
    Point { X: 0, Y: 0 }         => "origin",
    Point { X: var x, Y: var y } => $"({x}, {y})",
    _                            => "unknown"
};
```

Bu örnekte yürütme sırasında iki deseni vardır. `o` ilk ile eşleşen `Point` *türü deseni* ve ardından *özelliği desenini* içinde *{kaşlı ayraçlar}*. `_` Açıklar `discard pattern`, aynı olduğu `default` için *switch ifadeleri*.

Desenleri yakalar amacınızla testleri için uygulayan yordam kodu yerine bildirim temelli bir kod yazmanızı sağlar. Derleyici bence Bu yordam kodu uygulamak için sorumlu olur ve doğru şekilde her zaman yapmak için sağlanır.

Hala olacaktır burada *switch ifadeleri* daha iyi bir seçim olacaktır *anahtar ifadeleri* ve desenleri, her iki sözdizimi stilleri ile kullanılabilir.

Daha fazla bilgi için [desenleri ile daha fazlasını yapın C# 8.0](https://devblogs.microsoft.com/dotnet/do-more-with-patterns-in-c-8-0/).

## <a name="ieee-floating-point-improvements"></a>IEEE kayan nokta geliştirmeleri

Kayan nokta API'leri olan uymak için güncelleştirilme sürecindedir [IEEE 754-2008 düzeltme](https://en.wikipedia.org/wiki/IEEE_754-2008_revision). Bu değişikliklerin amacı, davranışsal IEEE belirtimi ile uyumlu olduklarından emin olun ve tüm "required" işlemlerinin açığa sağlamaktır.

Ayrıştırma ve biçimlendirme düzeltmeleri:

* Doğru ayrıştırma ve herhangi bir uzunluktaki girişleri yuvarlar.
* Doğru ayrıştırma ve negatif sıfır biçimlendirin.
* Büyük küçük harf duyarsız bir denetimi gerçekleştirmek ve isteğe bağlı bir önceki vererek sonsuzluk ve NaN düzgün ayrıştırılamadı `+` uygunsa.

Yeni matematik API'ye sahiptir:

* `BitIncrement/BitDecrement`\
Karşılık gelen `nextUp` ve `nextDown` IEEE operations. Karşılaştıran en küçük kayan noktalı sayı (sırasıyla) giriş'den küçük veya büyük döndürürler. Örneğin, `Math.BitIncrement(0.0)` döndürecekti `double.Epsilon`.

* `MaxMagnitude/MinMagnitude`\
Karşılık gelen `maxNumMag` ve `minNumMag` IEEE işlemleri, bunlar döndürür (sırasıyla) büyük ya da büyüklük açısından iki girişe daha düşük olan değer. Örneğin, `Math.MaxMagnitude(2.0, -3.0)` döndürecekti `-3.0`.

* `ILogB`\
Karşılık gelen `logB` bir tamsayı değeri döndüren IEEE işlemi giriş parametresinin tamsayı 2 tabanında günlük döndürür. Bu etkili bir şekilde aynıdır `floor(log2(x))`, ancak en az yuvarlama hatası işler bitti.

* `ScaleB`\
Karşılık gelen `scaleB` bir tamsayı değeri alan IEEE işlemi döndürür etkili bir şekilde `x * pow(2, n)`, yuvarlama en az bir hata ile tamamlandı ancak.

* `Log2`\
Karşılık gelen `log2` IEEE işlemi 2 tabanlı logaritmasını döndürür. Yuvarlama hata en aza indirir.

* `FusedMultiplyAdd`\
Karşılık gelen `fma` IEEE işlem gerçekleştirdiği bir çarpım Çarp. Diğer bir deyişle, mevcut `(x * y) + z` tek bir işlem olarak, var-tarafından yuvarlama hata en aza indirir. Örnek verilebilir `FusedMultiplyAdd(1e308, 2.0, -1e308)` döndüren `1e308`. Normal `(1e308 * 2.0) - 1e308` döndürür `double.PositiveInfinity`.

* `CopySign`\
Karşılık gelen `copySign` IEEE işlemi değerini döndürür `x`, ancak işaretini `y`.

## <a name="net-platform-dependent-intrinsics"></a>.NET platform bağımlı iç bilgileri

Gibi belirli performans odaklı CPU yönergeleri için erişime izin API'ler eklenmiştir **SIMD** veya **Bit işleme yönerge** ayarlar. Bu yönergeler, verileri verimli bir şekilde paralel işleme gibi bazı senaryolarda büyük performans geliştirmeleri elde etmeye yardımcı olabilir. Kullanılacak API'ler programlarınızın gösterme ek olarak, performansı artırmak için bu yönergeleri kullanarak .NET kitaplıklarına başlamıştır.

Aşağıdaki CoreCLR Pr'ler birkaç uygulama veya kullanımı aracılığıyla iç bilgileri gösterir:

* [Basit SSE2 donanım iç uygulama](https://github.com/dotnet/coreclr/pull/15585)
* [SSE donanım iç uygulama](https://github.com/dotnet/coreclr/pull/15538)
* [Arm64 temel donanım iç bilgileri](https://github.com/dotnet/coreclr/pull/16822)
* [Bul için TZCNT ve LZCNT kullanma {ilk | En son} bulunamadı {bayt | Char}](https://github.com/dotnet/coreclr/pull/21073)

Daha fazla bilgi için [.NET platformu bağımlı yapı içleri](https://github.com/dotnet/designs/blob/master/accepted/platform-intrinsics.md), Microsoft, yonga satıcılar veya tüm diğer şirket veya tek yongası/tanımlamak bu donanım altyapısını tanımlamak için bir yaklaşım tanımlar .NET kodu için sunulan API'ler.

## <a name="default-executables"></a>Varsayılan yürütülebilir dosyalar

.NET core artık derler [framework bağımlı yürütülebilir dosyaları](../deploying/index.md#framework-dependent-executables-fde) varsayılan olarak. .NET Core genel olarak yüklenmiş bir sürümünü kullanan uygulamalar için yeni bir özelliktir. Şimdiye kadar yalnızca [müstakil dağıtımları](../deploying/index.md#self-contained-deployments-scd) yürütülebilir bir dosya oluşturur.

Sırasında `dotnet build` veya `dotnet publish`, kullanmakta olduğunuz SDK platform ve ortam ile eşleşen sağlanan yürütülebilir bir dosya oluşturulur. Diğer yerel yürütülebilir dosyalar gibi olduğu gibi bu yürütülebilir dosyaları ile aynı şey geçerli olacaktır:

* Yürütülebilir dosya üzerine çift tıklayabilirsiniz.
* Doğrudan bir komut isteminden uygulama başlatma gibi `myapp.exe` Windows, şirket ve `./myapp` Linux ve Macos'ta.

## <a name="build-copies-dependencies"></a>Derleme bağımlılıkları kopyalar.

`dotnet build` artık uygulamanız için NuGet bağımlılıklarını NuGet önbellekten yapı çıktı klasörüne kopyalar. Daha önce bağımlılıkları parçası olarak yalnızca kopyalanan `dotnet publish`.

Yayımlama, yayınlama, bağlama ve razor sayfası hala gerektirir gibi bazı işlemler vardır.

## <a name="local-dotnet-tools"></a>Yerel dotnet araçları

> [!WARNING]
> .NET Core 3.0 Önizleme 2 ile .NET Core 3.0 Önizleme 1 ila yerel .NET Core Araçları'nda bir değişiklik yoktu.  Yerel araçları Preview 1'çıkış gibi bir komut çalıştırarak çalıştığınız varsa `dotnet tool restore` veya `dotnet tool install`, yerel araçları Önizleme 2'de doğru çalışmadan önce yerel Araçlar önbellek klasörünü silin gerekir. Bu klasör şu konumdadır:
>
> Mac, Linux: `rm -r $HOME/.dotnet/toolResolverCache`
>
> Windows üzerinde: `rmdir /s %USERPROFILE%\.dotnet\toolResolverCache`
>
> Bu klasör silmezseniz, hata alırsınız.

.NET Core 2.1 genel araçları destekleniyorsa, .NET Core 3.0 artık yerel araçlara sahiptir. Yerel Araçlar genel araçları benzerdir, ancak disk üzerindeki belirli bir konum ile ilişkilidir. Bu, proje başına ve havuz başına araçlar sağlar. Yerel olarak yüklü herhangi bir aracı genel olarak kullanılabilir değil. Araçlar NuGet paketleri olarak dağıtılır.

Yerel Araçlar kullanan bir bildirim dosyası adına `dotnet-tools.json` geçerli dizininizde. Bu bildirim dosyası, bu klasörü ve altındaki kullanılabilir olması için Araçlar tanımlar. Bu bildirim dosyası, depo kökünde oluşturarak, herkesin kodunuzu kopyalama geri yükleyebilir ve başarıyla kodunuzla çalışmak için gereken araçları kullanmanız emin olun.

Oluşturmak için bir `dotnet-tools.json` bildirim dosyası, kullanın:

```console
dotnet new tool-manifest
```

Yeni bir aracı ile yerel bildirimi ekleyin:

```console
dotnet tool install <packageId>
```

Ayrıca, yerel bildirimi ile araçları listeleyebilirsiniz:

```console
dotnet tool list
```

Genel olarak hangi araçları yüklü olduğunu görmek için bu seçeneği kullanın:

```console
dotnet tool list -g
```

Yerel Araçlar bildirim, dosya kullanılabilir, ancak bildiriminde tanımlanan araçları yüklü değil, otomatik olarak indirip bu araçları yüklemek için aşağıdaki komutu kullanın:

```console
dotnet tool restore
```

Yerel bir aracı ile aşağıdaki komutu çalıştırın:

```console
dotnet tool run <tool-command-name>
```

Dotnet, yerel aracı çalıştırdığınızda, bir bildirim geçerli dizin yapısını arar. Bir aracı bildirim dosyası bulunduğunda, için istenen aracı aranır. Aracı bildirimi, ancak önbellek bulunursa, kullanıcı hata alır ve çalıştırmaya gerek duymadığı `dotnet tool restore`.

Bir aracı yerel aracı bildirim dosyasından kaldırmak için aşağıdaki komutu çalıştırın:

```console
dotnet tool uninstall <packageId>
```

Aracı bildirim dosyasını elle düzenlemeye – izin vermek için deposuyla çalışmak için gerekli sürümü güncelleştirmek için bunu tasarlanmıştır. İşte bir örnek `dotnet-tools.json` dosyası:

```json
{
  "version": 1,
  "isRoot": true,
  "tools": {
    "dotnetsay": {
      "version": "2.1.4",
      "commands": [
        "dotnetsay"
      ]
    },
    "t-rex": {
      "version": "1.0.103",
      "commands": [
        "t-rex"
      ]
    }
  }
}
```

Hem genel hem de yerel araçları için çalışma zamanı'nın uyumlu bir sürümü gereklidir. Birçok araç NuGet.org üzerinde şu anda .NET Core çalışma zamanı 2.1 hedefleyin. Bu genel olarak veya yerel olarak yüklemek için yükleme yine [NET Core 2.1 çalışma zamanı](https://dotnet.microsoft.com/download/dotnet-core/2.1).

## <a name="windows-desktop"></a>Windows masaüstü

.NET Core 3.0 Önizleme 1'den başlayarak, WPF ve Windows Forms kullanılarak Windows Masaüstü uygulamaları oluşturabilirsiniz. Bu çerçeveler ile modern denetimleri ve Windows kullanıcı Arabirimi XAML kitaplığından (WinUI) Fluent stil kullanarak da destekler [XAML Adaları](/windows/uwp/xaml-platform/xaml-host-controls).

Windows Masaüstü bileşen Windows parçasıdır .NET Core 3.0 SDK.

Şunlarla birlikte yeni bir Windows Forms ve WPF uygulaması oluşturabilirsiniz `dotnet` komutları:

```console
dotnet new wpf
dotnet new winforms
```

Visual Studio 2019 ekler **yeni proje** .NET Core 3.0, Windows Forms ve WPF şablonları. Tasarımcılar henüz yine de desteklenir. Ve açmak, başlatmak ve Visual Studio 2019 bu projelerde hata ayıklama.

Visual Studio 2017 15.9 yeteneği ekler [.NET Core önizlemelerini etkinleştir](https://devblogs.microsoft.com/dotnet/net-core-tooling-update-for-visual-studio-2017-version-15-9/), ancak bu özelliği etkinleştirmek gereken ve desteklenen bir senaryo değildir.

Yeni Proje birkaç eklemelerle mevcut .NET Core projeleri ile aynıdır. Temel .NET Core konsol projesi ve temel bir Windows Forms ve WPF projesi bir karşılaştırması aşağıdadır.

Bir .NET Core konsol projesi kullandığından `Microsoft.NET.Sdk` SDK ve .NET Core 3.0 üzerinden üzerinde bir bağımlılık bildirir `netcoreapp3.0` hedef çerçeve. Bir Windows masaüstü uygulaması oluşturmak için kullanın `Microsoft.NET.Sdk.WindowsDesktop` SDK ve kullanmak için hangi UI çerçevesi seçin:

```diff
-<Project Sdk="Microsoft.NET.Sdk">
+<Project Sdk="Microsoft.NET.Sdk.WindowsDesktop">
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp3.0</TargetFramework>
+   <UseWPF>true</UseWPF>
  </PropertyGroup>
</Project>
```

Windows Forms, WPF seçmek için ayarlanmış `UseWindowsForms` yerine `UseWPF`:

```diff
<Project Sdk="Microsoft.NET.Sdk.WindowsDesktop">
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp3.0</TargetFramework>
-   <UseWPF>true</UseWPF>
+   <UseWindowsForms>true</UseWindowsForms>
  </PropertyGroup>
</Project>
```

Her ikisi de `UseWPF` ve `UseWindowsForms` ayarlanabilir `true` uygulama için bir Windows Forms iletişim kutusu, bir WPF denetimi barındırmayla örnek her iki çerçeveleri kullanıyorsa.

Geri bildiriminizi Lütfen paylaşım [dotnet/winforms](https://github.com/dotnet/winforms/issues), [dotnet/wpf](https://github.com/dotnet/wpf/issues) ve [dotnet/core](https://github.com/dotnet/core/issues) depolar.

## <a name="msix-deployment-for-windows-desktop"></a>Windows Masaüstü için MSIX dağıtım

[MSIX](https://docs.microsoft.com/windows/msix/) yeni bir Windows uygulama paketi biçimi. .NET Core 3.0 Windows 10 Masaüstü uygulamaları dağıtmak için kullanılabilir.

[Windows uygulaması paketleme projesi](https://docs.microsoft.com/windows/uwp/porting/desktop-to-uwp-packaging-dot-net), Visual Studio 2019 bulunan MSIX paketlerle oluşturmanıza olanak tanır [müstakil](../deploying/index.md#self-contained-deployments-scd) .NET Core uygulamaları.

> [!NOTE]
> .NET Core proje dosyası içinde desteklenen çalışma zamanları belirtmelisiniz `<RuntimeIdentifiers>` özelliği:
>
> ```xml
> <RuntimeIdentifiers>win-x86;win-x64</RuntimeIdentifiers>
> ```

## <a name="fast-built-in-json-support"></a>Hızlı yerleşik JSON desteği

.NET ekosisteminin yararlandı [ **Json.NET** ](https://www.newtonsoft.com/json) ve iyi seçenekleri olmaya devam diğer popüler JSON kitaplıkları. **Json.NET** UTF-16 başlık altında olan kendi taban datatype .NET dizeleri kullanır.

Yeni yerleşik JSON desteği, yüksek performanslı, düşük ayırma ve temel `Span<byte>`. .NET Core 3.0 için yeni ana JSON ile ilgili üç eklenmiştir `System.Text.Json` ad alanı.

### <a name="utf8jsonreader"></a>Utf8JsonReader

`System.Text.Json.Utf8JsonReader` yüksek performanslı, düşük ayırma, yalnızca iletme Okuyucu için UTF-8 kodlamalı JSON metin okuma, bir `ReadOnlySpan<byte>`. `Utf8JsonReader` Özel çözümleyiciler ve deserializers oluşturmak için kullanılan bir temel, alt düzey, türüdür. Kullanarak yeni bir JSON yükü okuma `Utf8JsonReader` reader'ı kullanarak daha hızlı bir şekilde x 2 **Json.NET**. JSON belirteçleri (UTF-16) dizeler olarak actualize gerekene kadar bırakmaz.

Bu yeni API'yi aşağıdaki bileşenleri içerir:

* Önizleme 1'de: JSON Okuyucu (sıralı erişim)
* Sonraki yakında: JSON yazıcısı, DOM (rastgele erişim) poco serileştirici poco seri durumdan çıkarıcının

Temel bir okuyucu döngü için işte `Utf8JsonReader` başlangıç noktası olarak kullanılabilir:

```csharp
using System.Text.Json;

public static void Utf8JsonReaderLoop(ReadOnlySpan<byte> dataUtf8)
{
    var json = new Utf8JsonReader(dataUtf8, isFinalBlock: true, state: default);

    while (json.Read())
    {
        JsonTokenType tokenType = json.TokenType;
        ReadOnlySpan<byte> valueSpan = json.ValueSpan;
        switch (tokenType)
        {
            case JsonTokenType.StartObject:
            case JsonTokenType.EndObject:
                break;
            case JsonTokenType.StartArray:
            case JsonTokenType.EndArray:
                break;
            case JsonTokenType.PropertyName:
                break;
            case JsonTokenType.String:
                string valueString = json.GetStringValue();
                break;
            case JsonTokenType.Number:
                if (!json.TryGetInt32Value(out int valueInteger))
                {
                    throw new FormatException();
                }
                break;
            case JsonTokenType.True:
            case JsonTokenType.False:
                bool valueBool = json.GetBooleanValue();
                break;
            case JsonTokenType.Null:
                break;
            default:
                throw new ArgumentException();
        }
    }

    dataUtf8 = dataUtf8.Slice((int)json.BytesConsumed);
    JsonReaderState state = json.CurrentState;
}
```

### <a name="utf8jsonwriter"></a>Utf8JsonWriter

`System.Text.Json.Utf8JsonWriter` bir yüksek performanslı, genel .NET türleri JSON metni yalnızca iletme UTF-8 olarak kodlanmış biçimde yazmak ister önbelleğe alınmamış, sağlar `String`, `Int32`, ve `DateTime`. Okuyucu gibi özel seri hale getiricileri genişletme oluşturmak için kullanılan bir temel, alt düzey türü, yazardır. Kullanarak yeni bir JSON yükünü yazmayı `Utf8JsonWriter` yazıcıdan kullanarak daha hızlı % 30-80'idir **Json.NET** ve ayrılamadı.

İşte bir örnek kullanımı `Utf8JsonWriter` başlangıç noktası olarak kullanılabilir:

```csharp
static int WriteJson(IBufferWriter<byte> output, long[] extraData)
{
    var json = new Utf8JsonWriter(output, state: default);

    json.WriteStartObject();

    json.WriteNumber("age", 15, escape: false);
    json.WriteString("date", DateTime.Now);
    json.WriteString("first", "John");
    json.WriteString("last", "Smith");

    json.WriteStartArray("phoneNumbers", escape: false);
    json.WriteStringValue("425-000-1212", escape: false);
    json.WriteStringValue("425-000-1213");
    json.WriteEndArray();

    json.WriteStartObject("address");
    json.WriteString("street", "1 Microsoft Way");
    json.WriteString("city", "Redmond");
    json.WriteNumber("zip", 98052);
    json.WriteEndObject();

    json.WriteStartArray("ExtraArray");
    for (var i = 0; i < extraData.Length; i++)
    {
        json.WriteNumberValue(extraData[i]);
    }
    json.WriteEndArray();

    json.WriteEndObject();

    json.Flush(isFinalBlock: true);

    return (int)json.BytesWritten;
}
```

`Utf8JsonWriter` Kabul `IBufferWriter<byte>` zaman uyumlu olarak json verilerini yazmak için çıkış konumunu ve çağıran olarak gibi somut bir uygulama sunmak amacıyla gerekir. Platform şu anda bu arabirimi uygulaması içermez. Bir örneği `IBufferWriter<byte>`, bkz: <https://gist.github.com/ahsonkhan/c76a1cc4dc7107537c3fdc0079a68b35>.

### <a name="jsondocument"></a>JsonDocument

`System.Text.Json.JsonDocument` üst kısmındaki yerleşik `Utf8JsonReader`. `JsonDocument` JSON verilerini ayrıştırma ve bir salt okunur belge nesne modeli (DOM), derleme olanağı, rastgele erişim ve numaralandırma desteklemek için sorgulanabilir sağlar. Verileri oluşturan JSON öğeleri aracılığıyla erişilebilir `JsonElement` tarafından sunulan tür `JsonDocument` adlı bir özellik olarak `RootElement`. `JsonElement` Ortak .NET türlerine JSON metnine dönüştürmek için API'leri ile birlikte JSON dizi ve nesne numaralandırıcıları içerir. Tipik bir JSON yükü ayrıştırma ve tüm kullanarak üyelerine erişilmesi `JsonDocument` 2-3 x daha hızlı bir şekilde **Json.NET** çok az ayırmaları ile verileri (örneğin < 1 MB) makul bir şekilde boyutlandırılmış için.

İşte bir örnek kullanımı `JsonDocument` ve `JsonElement` başlangıç noktası olarak kullanılabilir:

```csharp
static double ParseJson()
{
    const string json = " [ { \"name\": \"John\" }, [ \"425-000-1212\", 15 ], { \"grades\": [ 90, 80, 100, 75 ] } ]";

    double average = -1;

    using (JsonDocument doc = JsonDocument.Parse(json))
    {
        JsonElement root = doc.RootElement;
        JsonElement info = root[1];

        string phoneNumber = info[0].GetString();
        int age = info[1].GetInt32();

        JsonElement grades = root[2].GetProperty("grades");

        double sum = 0;
        foreach (JsonElement grade in grades.EnumerateArray())
        {
            sum += grade.GetInt32();
        }

        int numberOfCourses = grades.GetArrayLength();
        average = sum / numberOfCourses;
    }

    return average;
}
```

## <a name="assembly-unloadability"></a>Derleme Unloadability

Derleme unloadability, yeni bir özellik olan `AssemblyLoadContext`. Bu yeni özellik, yalnızca birkaç yeni API'ler ile kullanıma sunulan bir API açısından büyük ölçüde saydamdır. Bu, örneklenen türü statik alanları ve derlemenin kendisini tüm bellek serbest bırakma kaldırılacak bir yükleyici bağlamı sağlar. Bir uygulama, yükleme ve bu mekanizma aracılığıyla derlemeler sonsuza kadar bir bellek sızıntısı almadan kaldırma başlatabilmeniz gerekir.

Bu yeni özellik, benzer senaryoları için kullanılabilir:

* Yükleme ve kaldırma dinamik eklenti gerekli olduğu senaryolar eklentisi.
* Dinamik derleme, çalışan ve sonra kodu temizleme. Web siteleri, komut dosyası motorları, vb. için kullanışlıdır.
* Derlemeler için iç denetim (gibi ReflectionOnlyLoad), ancak Yükleniyor [MetadataLoadContext](#type-metadataloadcontext) (Önizleme 1'de yayımlanan) daha iyi bir seçenek çoğu durumda olacaktır.

Daha fazla bilgi için [kullanarak Unloadability](https://github.com/dotnet/coreclr/pull/22221) belge.

Derleme kaldırılması, yönetilen nesneleri bir yükleyici bağlamı dışında tüm başvurularını anladım ve yönetilen emin olmak için önemli dikkat gerektirir. Yükleyici bağlamı kaldırılacak istendiğinde herhangi bir dış başvuruları yükleyici bağlamı yalnızca kendisine tutarlı olmasını başvurulmayan verilmiş olması gerekir.

Derleme unloadability .NET Framework'teki uygulama, .NET Core ile desteklenmeyen etki alanları (uygulama etki alanları) tarafından sağlandı. Uygulama etki alanları, hem avantajları ve sınırlamaları yeni Bu modele kıyasla vardı. Uygulama etki alanları için karşılaştırıldığında daha esnek ve yüksek performanslı olmasını bu yeni yükleyici model göz önünde bulundurun.

## <a name="windows-native-interop"></a>Windows yerel birlikte çalışabilirliği

Windows formunda düz C API'leri, COM ve WinRT zengin bir yerel API sunar. .NET Core 1.0 sürümünden itibaren **P/Invoke** destek içerir. Özelliği artık .NET Core 3.0 ile desteği **COM API işlemi** ve **etkinleştirme WinRT API'lar** eklendi.

COM ile kullanma örneği gördüğünüz [Excel Demo kaynak kodu](https://github.com/dotnet/samples/tree/master/core/extensions/ExcelDemo).

## <a name="type-sequencereader"></a>Tür: SequenceReader

.NET Core 3. 0'da, `System.Buffers.SequenceReader` Okuyucu için olarak kullanılabilecek eklendi `ReadOnlySequence<T>`. Hızlı, yüksek performanslı, böylece düşük ayırma çözümlenmesi `System.IO.Pipelines` birden çok yedekleme arabellekler çapraz veri.

Aşağıdaki örnek bir girişi sonu `Sequence` geçerli içine `CR/LF` satırları ayrılmış:

```csharp
private static ReadOnlySpan<byte> CRLF => new byte[] { (byte)'\r', (byte)'\n' };

public static void ReadLines(ReadOnlySequence<byte> sequence)
{
    SequenceReader<byte> reader = new SequenceReader<byte>(sequence);

    while (!reader.End)
    {
        if (!reader.TryReadToAny(out ReadOnlySpan<byte> line, CRLF, advancePastDelimiter:false))
        {
            // Couldn't find another delimiter
            // ...
        }

        if (!reader.IsNext(CRLF, advancePast: true))
        {
            // Not a good CR/LF pair
            // ...
        }

        // line is valid, process
        ProcessLine(line);
    }
}
```

## <a name="type-metadataloadcontext"></a>Tür: MetadataLoadContext

`MetadataLoadContext` Türü okuma derleme sağlayan eklenmiş yapanın uygulama etki alanı etkilemeden meta verileri. Derlemeleri farklı mimariler ve geçerli çalışma zamanı ortamı daha platformlar için oluşturulmuş derlemeler de dahil olmak üzere veriler olarak okunur. `MetadataLoadContext` ile çakışıyor <xref:System.Reflection.Assembly.ReflectionOnlyLoad*>, hangi, yalnızca .NET Framework içinde kullanılabilir.

`MetdataLoadContext` kullanılabilir [System.Reflection.MetadataLoadContext paket](https://www.nuget.org/packages/System.Reflection.MetadataLoadContext). .NET Standard 2.0 bir pakettir.

`MetadataLoadContext` Benzer olan API'leri gösterir <xref:System.Runtime.Loader.AssemblyLoadContext> yazın, ancak bu türüne göre değil. Benzer şekilde <xref:System.Runtime.Loader.AssemblyLoadContext>, `MetadataLoadContext` evreni yükleniyor yalıtılmış bir derlemenin içinden yükleme derlemelerini etkinleştirir. `MetdataLoadContext` API'leri dönüş <xref:System.Reflection.Assembly> bilinen yansıma API'leri kullanımını etkinleştirme nesneleri. Yürütme API'leri gibi odaklı [MethodBase.Invoke](https://github.com/dotnet/corefx/blob/master/src/System.Reflection.MetadataLoadContext/src/System/Reflection/TypeLoading/Methods/RoMethod.cs#L127), izin verilmeyen ve InvalidOperationException oluşturur.

Aşağıdaki örnek, belirli bir arabirimi uygulayan bir derlemede somut tür bulmak gösterilmektedir:

```csharp
var paths = new string[] {@"C:\myapp\mscorlib.dll", @"C:\myapp\myapp.dll"};
var resolver = new PathAssemblyResolver(paths);
using (var lc = new MetadataLoadContext(resolver))
{
    Assembly a = lc.LoadFromAssemblyName("myapp");
    Type myInterface = a.GetType("MyApp.IPluginInterface");
    foreach (Type t in a.GetTypes())
    {
        if (t.IsClass && myInterface.IsAssignableFrom(t))
            Console.WriteLine($"Class {t.FullName} implements IPluginInterface");
    }
}
```

Senaryolar için `MetadataLoadContext` tasarım zamanı özellikleri, araçları, derleme zamanı ve çalışma zamanı açık'li veri olarak bir derleme kümesi inceleyin ve tüm dosya kilitleri olması gereken özellikleri ve İnceleme sonra serbest bırakılan bellek gerçekleştirilir.

`MetadataLoadContext` Çözümleyici sınıfı geçirilen yapıcısına sahiptir. Çözümleyici'nin iş yüklenmesidir bir `Assembly` verilen kendi `AssemblyName`. Özet çözümleyici sınıfı türetilen `MetadataAssemblyResolver` sınıfı. Yol tabanlı senaryoları için çözümleyici uygulaması ile sağlanan `PathAssemblyResolver`.

[MetadataLoadContext testleri](https://github.com/dotnet/corefx/tree/master/src/System.Reflection.MetadataLoadContext/tests/src/Tests) birçok kullanım durumları gösterir. [Derleme testleri](https://github.com/dotnet/corefx/blob/master/src/System.Reflection.MetadataLoadContext/tests/src/Tests/Assembly/AssemblyTests.cs) başlatmak için iyi bir yerdir.

## <a name="tls-13--openssl-111-on-linux"></a>TLS 1.3 & Linux'ta OpenSSL 1.1.1

.NET core artık avantajlarından yararlanın [OpenSSL 1.1.1 TLS 1.3 desteği](https://www.openssl.org/blog/blog/2018/09/11/release111/), verilen ortamda kullanılabilir olduğunda. Her TLS 1,3 birden çok avantaj vardır [OpenSSL takım](https://www.openssl.org/blog/blog/2018/09/11/release111/):

* Geliştirilmiş bağlantı süreleri nedeniyle bir azalma istemci ve sunucu arasında gerekli gidiş dönüş sayısı.

* Geliştirilmiş güvenlik çeşitli eski ve güvenli şifreleme algoritmaları kaldırılmasını ve daha fazla bağlantı el sıkışması şifrelenmesi nedeniyle.

.NET core 3.0 Önizleme 1 yararlanarak özellikli **OpenSSL 1.1.1**, **OpenSSL 1.1.0**, veya **OpenSSL 1.0.2** (ne olursa olsun bulunan en iyi, bir Linux sisteminde sürümüdür).  Zaman **OpenSSL 1.1.1** olduğu SslStream ve HttpClient türleri kullanılabilir kullanacağı **TLS 1.3** kullanırken `SslProtocols.None` (sistem varsayılan protokol), istemci ve sunucu desteği varsayılarak**TLS 1.3**.

.NET Core 3.0 Önizleme 1 Ubuntu 18.10 bağlanmak için aşağıdaki örnekte gösterilmiştir <https://www.cloudflare.com>:

```csharp
using System;
using System.Net.Security;
using System.Net.Sockets;
using System.Threading.Tasks;

namespace tlstest
{
    class Program
    {
        static async Task Main()
        {
            using (TcpClient tcpClient = new TcpClient())
            {
                string targetHost = "www.cloudflare.com";

                await tcpClient.ConnectAsync(targetHost, 443);

                using (SslStream sslStream = new SslStream(tcpClient.GetStream()))
                {
                    await sslStream.AuthenticateAsClientAsync(targetHost);
                    await Console.Out.WriteLineAsync($"Connected to {targetHost} with {sslStream.SslProtocol}");
                }
            }
        }
    }
}
```

```console
user@comp-ubuntu1810:~/tlstest$ dotnet run
Connected to www.cloudflare.com with Tls13
user@comp-ubuntu1810:~/tlstest$ openssl version
OpenSSL 1.1.1  11 Sep 2018
```

>[!IMPORTANT]
>Windows ve macOS henüz desteklemediği **TLS 1.3**. .NET core 3.0 destekleyeceği **TLS 1.3** desteği kullanılabilir olduğunda bu işletim sistemlerinde.

## <a name="cryptography"></a>Şifreleme

İçin destek eklenmiştir **AES GCM** ve **AES-CCM** aracılığıyla uygulanan şifrelemeleri, `System.Security.Cryptography.AesGcm` ve `System.Security.Cryptography.AesCcm`. Her ikisi de bu algoritmalar olan [ilişkilendirme veri (AEAD) algoritmaları ile kimliği doğrulanmış şifreleme](https://en.wikipedia.org/wiki/Authenticated_encryption)ve .NET Core için eklenen ilk kimliği doğrulanmış şifreleme (AE) algoritmaları.

Aşağıdaki kodu **AesGcm** şifrelemek ve rastgele verilerin şifresini çözmek için şifre.

Kodu **AesCcm** (sınıf değişken adları farklı olacaktır yalnızca) neredeyse aynı görünür.

```csharp
// key should be: pre-known, derived, or transported via another channel, such as RSA encryption
byte[] key = new byte[16];
RandomNumberGenerator.Fill(key);

byte[] nonce = new byte[12];
RandomNumberGenerator.Fill(nonce);

// normally this would be your data
byte[] dataToEncrypt = new byte[1234];
byte[] associatedData = new byte[333];
RandomNumberGenerator.Fill(dataToEncrypt);
RandomNumberGenerator.Fill(associatedData);

// these will be filled during the encryption
byte[] tag = new byte[16];
byte[] ciphertext = new byte[dataToEncrypt.Length];

using (AesGcm aesGcm = new AesGcm(key))
{
    aesGcm.Encrypt(nonce, dataToEncrypt, ciphertext, tag, associatedData);
}

// tag, nonce, ciphertext, associatedData should be sent to the other part

byte[] decryptedData = new byte[ciphertext.Length];

using (AesGcm aesGcm = new AesGcm(key))
{
    aesGcm.Decrypt(nonce, ciphertext, tag, decryptedData, associatedData);
}

// do something with the data
// this should always print that data is the same
Console.WriteLine($"AES-GCM: Decrypted data is{(dataToEncrypt.SequenceEqual(decryptedData) ? "the same as" : "different than")} original data.");
```

## <a name="cryptographic-key-importexport"></a>Şifreleme anahtarı içeri/dışarı aktarma

.NET core 3.0 Önizleme 1 içeri ve dışarı aktarmayı asimetrik ortak ve özel anahtarlar standart biçimlerinden bir X.509 sertifikası kullanmak zorunda kalmadan destekler.

Tüm anahtar türleri (RSA, DSA, ECDsa, ECDiffieHellman) desteği **X.509 SubjectPublicKeyInfo** biçimi için ortak anahtarları ve **PKCS #8 PrivateKeyInfo** ve **PKCS #8 EncryptedPrivateKeyInfo**  biçimleri özel anahtarlar için. RSA ayrıca destekler **PKCS #1 RSAPublicKey** ve **PKCS #1 RSAPrivateKey**. Tüm verme yöntemleri DER ile kodlanmış ikili verileri oluşturmak ve içeri aktarma metotları aynı beklerler. Bir anahtar metin dostu PEM biçiminde depolanır, çağırana base64 gerekir-içerik alma yöntemini çağırmadan önce kod çözme.

```csharp
using System;
using System.IO;
using System.Security.Cryptography;

namespace rsakeyprint
{
    class Program
    {
        static void Main(string[] args)
        {
            using (RSA rsa = RSA.Create())
            {
                byte[] keyBytes = File.ReadAllBytes(args[0]);
                rsa.ImportRSAPrivateKey(keyBytes, out int bytesRead);

                Console.WriteLine($"Read {bytesRead} bytes, {keyBytes.Length-bytesRead} extra byte(s) in file.");
                RSAParameters rsaParameters = rsa.ExportParameters(true);
                Console.WriteLine(BitConverter.ToString(rsaParameters.D));
            }
        }
    }
}
```

```console
user@comp-ubuntu1810:~/rsakeyprint$ echo Making a small key to save on screen space.
Making a small key to save on screen space.
user@comp-ubuntu1810:~/rsakeyprint$ openssl genrsa 768 | openssl rsa -outform der -out rsa.key
Generating RSA private key, 768 bit long modulus (2 primes)
..+++++++
........+++++++
e is 65537 (0x010001)
writing RSA key
user@comp-ubuntu1810:~/rsakeyprint$ dotnet run rsa.key
Read 461 bytes, 0 extra byte(s) in file.
0F-D0-82-34-F8-13-38-4A-7F-C7-52-4A-F6-93-F8-FB-6D-98-7A-6A-04-3B-BC-35-8C-7D-AC-A5-A3-6E-AD-C1-66-30-81-2C-2A-DE-DA-60-03-6A-2C-D9-76-15-7F-61-97-57-
79-E1-6E-45-62-C3-83-04-97-CB-32-EF-C5-17-5F-99-60-92-AE-B6-34-6F-30-06-03-AC-BF-15-24-43-84-EB-83-60-EF-4D-3B-BD-D9-5D-56-26-F0-51-CE-F1
user@comp-ubuntu1810:~/rsakeyprint$ openssl rsa -in rsa.key -inform der -text -noout | grep -A7 private
privateExponent:
    0f:d0:82:34:f8:13:38:4a:7f:c7:52:4a:f6:93:f8:
    fb:6d:98:7a:6a:04:3b:bc:35:8c:7d:ac:a5:a3:6e:
    ad:c1:66:30:81:2c:2a:de:da:60:03:6a:2c:d9:76:
    15:7f:61:97:57:79:e1:6e:45:62:c3:83:04:97:cb:
    32:ef:c5:17:5f:99:60:92:ae:b6:34:6f:30:06:03:
    ac:bf:15:24:43:84:eb:83:60:ef:4d:3b:bd:d9:5d:
    56:26:f0:51:ce:f1
```

PKCS #8 dosya inceledi ile `System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo` sınıfı.

PFX/PKCS #12 dosyaları inceledi ve ile yönetilebilir `System.Security.Cryptography.Pkcs.Pkcs12Info` ve `System.Security.Cryptography.Pkcs.Pkcs12Builder`sırasıyla.

## <a name="serialport-for-linux"></a>Linux için çevirmek için SerialPort

.NET core 3.0 destekler <xref:System.IO.Ports.SerialPort?displayProperty=nameWithType> Linux üzerinde.

Daha önce yalnızca kullanarak desteklenen .NET Core `SerialPort` Windows türü.

## <a name="more-bcl-improvements"></a>Daha fazla BCL geliştirmeleri

`Span<T>`, `Memory<T>`, Ve .NET Core 2.1 içinde tanıtılan ilgili türleri de .NET Core 3.0 için iyileştirilmiş. Sık kullanılan işlemler gibi yapı span, dilimleme, ayrıştırma ve biçimlendirme artık daha iyi gerçekleştirin.

Ayrıca, türleri ister `String` anahtarlarla olarak kullanıldığında daha verimli hale getirmek için altında--kapak geliştirmeleri gördünüz `Dictionary<TKey, TValue>` ve diğer koleksiyonları. Kod değişikliği olmadan bu iyileştirmeleri yararlanmak için gereklidir.

Aşağıdaki geliştirmeler de .NET Core 3 Önizleme 1'de yenidir:

* HttpClient için yerleşik Brotli desteği
* ThreadPool.UnsafeQueueWorkItem(IThreadPoolWorkItem)
* Unsafe.Unbox
* CancellationToken.Unregister
* Karmaşık aritmetik işleçler
* TCP için yuva API'leri Canlı
* StringBuilder.GetChunks
* Ayrıştırma IPEndPoint
* RandomNumberGenerator.GetInt32

## <a name="tiered-compilation"></a>Katmanlı derleme

[Katmanlı derleme](https://devblogs.microsoft.com/dotnet/tiered-compilation-preview-in-net-core-2-1/) .NET Core 3.0 ile varsayılan olarak açıktır. Daha fazla Desenlerinizi başlangıçta hem de daha iyi performans almak ve aktarım hızını en üst düzeye çıkarmak için tam zamanında (JIT) derleyici kullanmak çalışma zamanı sağlayan bir özelliktir.

Bu özellik bir Tercihli özellik olarak eklenmiştir [.NET Core 2.1](https://devblogs.microsoft.com/dotnet/announcing-net-core-2-1/) ve varsayılan olarak etkinleştirildi [.NET Core 2.2 Önizleme 2](https://devblogs.microsoft.com/dotnet/announcing-net-core-2-2-preview-2/). Daha sonra yeniden oturum .NET Core 2.2 sürüm geri çevirmek için döndürüldü.

## <a name="arm64-linux-support"></a>ARM64 Linux desteği

Destek için Linux ARM64 için eklendi. ARM64 için birincil kullanım durumu şu anda IOT senaryoları ile aşamasındadır.

Alpine, Debian ve Ubuntu [ARM64 için .NET Core için Docker görüntüleri kullanılabilir](https://hub.docker.com/r/microsoft/dotnet/).

Lütfen denetleyin [.NET Core ARM64 durumu](https://github.com/dotnet/announcements/issues/82) daha fazla bilgi için.

>[!NOTE]
> **ARM64** Windows Destek işlemi henüz kullanılamıyor.

## <a name="install-net-core-30-previews-on-linux-with-snap"></a>Ek ile Linux üzerinde .NET Core 3.0 önizlemeleri yükleme

Ek, tercih edilen yoludur yükleyin ve .NET Core önizlemeler deneyin [ek destekleyen Linux dağıtımları](https://docs.snapcraft.io/installing-snapd/6735).

Sisteminizde ek yapılandırdıktan sonra yüklemek için aşağıdaki komutu çalıştırın [.NET Core SDK 3.0 Önizleme SDK'sı](https://snapcraft.io/dotnet-sdk).

```console
sudo snap install dotnet-sdk --beta --classic
```

Ek paket yüklü kullanarak .NET Core, varsayılan .NET Core komut olduğunda `dotnet-sdk.dotnet`tam olarak `dotnet`. Namespaced komutun etkinleştirmiş olabilirsiniz genel olarak yüklenmiş bir .NET Core sürümle çakışmayacağı avantajdır. Bu komut için diğer adlı olarak `dotnet` ile:

```console
sudo snap alias dotnet-sdk.dotnet dotnet
```

Bazı dağıtımlarda, SSL sertifikası erişimi etkinleştirmek için ek bir adım gerektirir. Bkz. bizim [Linux Kurulumu](https://github.com/dotnet/core/blob/master/Documentation/linux-setup.md) Ayrıntılar için.

## <a name="gpio-support-for-raspberry-pi"></a>Raspberry Pi GPIO'yu desteği

İki yeni paket için GPIO programlama için kullanabileceğiniz NuGet yayımlanmıştır.

* [System.Device.Gpio](https://www.nuget.org/packages/System.Device.Gpio/0.1.0-prerelease.19078.2)
* [Iot.Device.Bindings](https://www.nuget.org/packages/Iot.Device.Bindings/0.1.0-prerelease.19078.2)

Bir GPIO'yu paketleri GPIO, SPI, I2C ve PWM cihazlar için APIleri içerir. IOT bağlamaları paketi içerir [cihaz bağlamaları](https://github.com/dotnet/iot/blob/master/src/devices/README.md) çeşitli yongaları ve algılayıcılar, aynı anda [dotnet/IOT-src/cihazlar](https://github.com/dotnet/iot/tree/master/src/devices).

Güncelleştirilmiş seri bağlantı noktası .NET Core 3.0 Preview 1 kapsamında duyurulan API'leri bu paketlerin bir parçası değildir ancak mevcut .NET Core platformu bir parçası olarak.

## <a name="platform-support"></a>Platform Desteği

.NET core 3 aşağıdaki işletim sistemlerinde desteklenir:

* Windows İstemcisi: 7, 8.1, 10 (1607+)
* Windows Server için: 2012 R2 SP1+
* macOS: 10.12+
* RHEL: 6+
* Fedora: 26+
* Ubuntu: 16.04+
* Debian: 9+
* SLES: 12+
* openSUSE: 42.3+
* Alpine: 3.8+

Yonga desteği aşağıdaki gibidir:

* Windows, macOS ve Linux'ta x64
* Windows üzerinde x86
* Windows ve Linux'ta ARM32
* Linux üzerinde ARM64

Linux için ARM32 Debian 9 + ve Ubuntu 16.04 + desteklenir. ARM64 için bunu ARM32 Alpine 3.8 eklenmesi ile aynıdır. Bunlar X64 için desteklenmediğinden bu distro'lara aynı sürümleridir.

.NET Core 3.0 için docker görüntüleri kullanılabilir [microsoft/dotnet Docker hub'da](https://hub.docker.com/r/microsoft/dotnet/). Microsoft şu anda kullandığı sürecinde [Microsoft kapsayıcı kayıt defteri (MCR)](https://cloudblogs.microsoft.com/opensource/2019/01/17/improved-discovery-experience-microsoft-containers-docker-hub/) ve son .NET Core 3.0 görüntüleri için MCR yalnızca yayımlanacak beklenmektedir.
