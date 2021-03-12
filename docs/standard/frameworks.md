---
title: SDK stilindeki projelerde hedef çerçeveler-.NET
description: .NET uygulamaları ve kitaplıkları için hedef çerçeveler hakkında bilgi edinin.
ms.date: 03/03/2021
ms.prod: dotnet
ms.custom: updateeachrelease
ms.technology: dotnet-standard
ms.openlocfilehash: 9e831726a87493b109578a3546a8f29b7b71cb6c
ms.sourcegitcommit: 46cfed35d79d70e08c313b9c664c7e76babab39e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/10/2021
ms.locfileid: "102604612"
---
# <a name="target-frameworks-in-sdk-style-projects"></a>SDK stilindeki projelerde hedef çerçeveler

Bir uygulamayı veya kitaplığı içinde bir çerçeveyi hedeflediğinizde, uygulama veya kitaplık için kullanılabilir hale getirmek istediğiniz API kümesini belirtirsiniz. Hedef Framework 'ü bir hedef Framework bilinen adı (tfd) kullanarak proje dosyanızda belirtirsiniz.

Bir uygulama veya kitaplık [.NET Standard](net-standard.md)bir sürümünü hedefleyebilir. .NET Standard sürümler tüm .NET uygulamalarında standartlaştırılmış API kümelerini temsil eder. Örneğin, bir kitaplık .NET Standard 1,6 ' i hedefleyebilir ve aynı kod tabanını kullanarak .NET Core ve .NET Framework üzerinde çalışır olan API 'lere erişim elde edebilir.

Uygulama veya kitaplık, uygulamaya özel API 'lere erişim kazanmak için belirli bir .NET uygulamasını da hedefleyebilir. Örneğin, Xamarin. iOS 'u hedefleyen bir uygulama (örneğin, `Xamarin.iOS10` ), iOS 10 Için Xamarin tarafından sağlanmış IOS API sarmalayıcılarını veya Evrensel Windows platformu (UWP,) hedefleyen bir uygulamanın `uap10.0` Windows 10 çalıştıran cihazlar için derleme yapan API 'lere erişimi vardır.

.NET Framework gibi bazı hedef çerçeveler için API 'Ler, Framework 'ün bir sisteme yüklediği derlemeler tarafından tanımlanır ve uygulama çerçevesi API 'Lerini (örneğin, ASP.NET) içerebilir.

Paket tabanlı hedef çerçeveler için (örneğin, .NET 5, .NET Core ve .NET Standard), API 'Ler uygulama veya kitaplığa dahil olan NuGet paketleri tarafından tanımlanır.

## <a name="latest-versions"></a>En son sürümler

Aşağıdaki tabloda en yaygın hedef çerçeveler ve bunların nasıl başvurdukları ve hangi [.NET Standard](net-standard.md) sürümü uygulandığı tanımlanmaktadır. Bu hedef Framework sürümleri, en son kararlı sürümleridir. Yayın öncesi sürümler gösterilmez. Hedef çerçeve bilinen adı (tfd), bir .NET uygulaması veya kitaplığının hedef çerçevesini belirtmek için standartlaştırılmış bir belirteç biçimidir.

| Hedef çerçeve      | En son <br/> kararlı sürüm | Hedef çerçeve bilinen adı (tfd) | Uygulanan <br/> .NET Standard sürümü |
| :-: | :-: | :-: | :-: |
| .NET 5                | 5.0                         | NET 5.0                         | Yok                                     |
| .NET Standard         | 2.1                         | Netstandard 2.1                 | Yok                                     |
| .NET Core             | 3,1                         | netcoreapp 3.1                  | 2.1                                     |
| .NET Framework        | 4.8                         | net48                          | 2.0                                     |

## <a name="supported-target-frameworks"></a>Desteklenen hedef çerçeveler

Bir hedef çerçeveye genellikle tfd tarafından başvurulur. Aşağıdaki tabloda .NET SDK ve NuGet istemcisi tarafından desteklenen hedef çerçeveler gösterilmektedir. Eşdeğerleri köşeli ayraç içinde gösterilir. Örneğin, `win81` ile eşdeğer BIR TFı vardır `netcore451` .

| Hedef Çerçeve           | TFM |
| -------------------------- | --- |
| .NET 5 + (ve .NET Core)    | netcoreapp 1.0<br>netcoreapp 1.1<br>netcoreapp2.0<br>netcoreapp 2.1<br>netcoreapp 2.2<br>netcoreapp 3.0<br>netcoreapp 3.1<br>NET 5.0 *<br> net 6.0* |
| .NET Standard              | Netstandard 1.0<br>Netstandard 1.1<br>Netstandard 1.2<br>Netstandard 1.3<br>Netstandard 1.4<br>Netstandard 1.5<br>Netstandard 1.6<br>Netstandard 2.0<br>Netstandard 2.1 |
| .NET Framework             | net11<br>net20<br>net35<br>net40<br>net403<br>net45<br>net451<br>net452<br>net46<br>net461<br>net462<br>net47<br>net471<br>net472<br>net48 |
| Windows Mağazası              | netcore [netcore45]<br>netcore45 [Win] [Win8]<br>netcore451 [win81] |
| .NET mikro Framework       | netmf |
| Silverlight                | sl4<br>sl5 |
| Windows Phone              | WP [WP7]<br>wp7<br>wp75<br>WP8<br>wp81<br>wpa81 |
| Evrensel Windows Platformu | UAP [UAP 10.0]<br>UAP 10.0 [win10] [netcore50] |

\* .NET 5 ve üzeri TFMs, işletim sistemine özgü bazı Çeşitlemeler içerir. Daha fazla bilgi için, [.NET 5 + OS 'e özgü TFMs](#net-5-os-specific-tfms)bölümüne bakın.

### <a name="net-5-os-specific-tfms"></a>.NET 5 + işletim sistemine özgü TFMs

`net5.0`Ve `net6.0` tfms, farklı platformlarda çalışan teknolojiler içerir. İşletim sistemine *özgü TFI* belirtme, uygulamanız için kullanılabilen bir işletim sistemine özgü API 'leri, örneğin Windows Forms veya IOS bağlamalarını belirtir. İşletim sistemine özgü TFMs Ayrıca, her API 'yi kendi temel TFM için de (örneğin, TFM) de devralır `net5.0` .

.NET 5 `net5.0-windows` , WinForms, WPF ve UWP API 'lerine yönelik Windows 'a özgü bağlamaları içeren, işletim sistemine özgü tfd 'yi kullanıma sunmuştur. .NET 6, işletim sistemine özgü TFMs 'Leri tanıtır.

Aşağıdaki tabloda .NET 5 + TFMs 'nin uyumluluğu gösterilmektedir.

| TFM                | İle uyumlu                                                                                                         |
|--------------------|-------------------------------------------------------------------------------------------------------------------------|
| NET 5.0             | net1.. 4 (NU1701 uyarıyla birlikte)<br />netcoreapp1.. 3,1 (WinForms veya WPF 'ye başvurulduğunda uyarı)<br />netstandard1.. 2,1 |
| NET 5.0-Windows     | netcoreapp1.. 3,1 (artı diğer her şey `net5.0` )                                                         |
| NET 6.0             | (sonraki sürümü `net5.0` )                                                                                        |
| NET 6.0-Android     | `xamarin.android` (+ devralınan diğer her şey `net6.0` )                                                            |
| NET 6.0-iOS         | `xamarin.ios` (+ devralınan diğer her şey `net6.0` )                                                                |
| NET 6.0-MacOS       | `xamarin.mac` (+ devralınan diğer her şey `net6.0` )                                                                |
| NET 6.0-maccatalyst | `xamarin.ios` (+ devralınan diğer her şey `net6.0` )                                                                |
| NET 6.0-tvOS        | `xamarin.tvos` (+ devralınan diğer her şey `net6.0` )                                                               |
| NET 6.0-Windows     | (sonraki sürümü `net5.0-windows` )                                                                                |

Uygulamanızı farklı platformlarda taşınabilir hale getirmek, ancak işletim sistemine özgü API 'lere erişim sağlamak için, birden çok işletim sistemine özgü TFMs 'yi hedefleyebilir ve önişlemci yönergelerini kullanarak işletim sistemine özgü API çağrılarını kapsayan platform koruyucuları ekleyebilirsiniz `#if` .

#### <a name="suggested-targets"></a>Önerilen hedefler

Uygulamanızda hangi tfd kullanacağınızı öğrenmek için bu yönergeleri kullanın:

- Birden çok platforma taşınabilir uygulamalar, örneğin, bir temel tfd 'yi hedeflemelidir `net5.0` . Bu, çoğu kitaplığı içerir, aynı zamanda ASP.NET Core ve Entity Framework.

- Platforma özgü kitaplıklar platforma özgü türleri hedeflemelidir. Örneğin, WinForms ve WPF projeleri veya ' i hedeflemelidir `net5.0-windows` `net6.0-windows` .

- Platformlar arası uygulama modelleri (Xamarin Forms, ASP.NET Core) ve köprü paketleri (Xamarin Essentials) en azından temel TFı 'yi hedeflemelidir, örneğin, `net6.0` ancak daha fazla API veya özellik için ek platforma özgü türleri de hedefleyebilir.

#### <a name="os-version-in-tfms"></a>TFMs içindeki işletim sistemi sürümü

Ayrıca, TFı 'nin sonunda, `net6.0-ios13.0` uygulamanızda hangi API 'lerin kullanılabildiğini belirten isteğe bağlı bir işletim sistemi sürümü belirtebilirsiniz. (Karşılık gelen .NET SDK, yayımlandıklarında daha yeni işletim sistemi sürümleri için destek içerecek şekilde güncelleştirilecektir.) Yeni yayınlanan API 'lere erişim kazanmak için TFM 'deki işletim sistemi sürümünü artırın. Uygulamanızı, daha önceki işletim sistemi sürümleriyle uyumlu hale getirebilirsiniz (ve sonraki sürüm API 'Lerine yapılan çağrılar için), `SupportedOSPlatformVersion` öğeyi proje dosyanıza ekleyerek. `SupportedOSPlatformVersion`Öğesi, uygulamanızı çalıştırmak için gereken en düşük işletim sistemi sürümünü gösterir.

Örneğin, aşağıdaki proje dosyası alıntısı iOS 14 API 'Lerinin uygulama için kullanılabilir olduğunu, ancak iOS 13 veya üzeri makinelerde çalışacağını belirtir.

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <TargetFramework>net6.0-ios14.0</TargetFramework>
    <SupportedOSPlatformVersion>13.0</SupportedOSPlatformVersion> (minimum os platform version)
  </PropertyGroup>

  ...

</Project>
```

## <a name="how-to-specify-a-target-framework"></a>Hedef çerçeve belirtme

Hedef çerçeveler bir proje dosyasında belirtilir. Tek bir hedef çerçeve belirtildiğinde, [TargetFramework öğesini](../core/project-sdk/msbuild-props.md#targetframework)kullanın. Aşağıdaki konsol uygulaması proje dosyası, .NET 5,0 'in nasıl hedefleyeceğinizi göstermektedir:

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>net5.0</TargetFramework>
  </PropertyGroup>

</Project>
```

Birden çok hedef çerçeve belirttiğinizde, her bir hedef çerçeve için derlemelere koşullu başvuru yapabilirsiniz. Kodunuzda, *if-then-else* mantığıyla önişlemci sembolleri kullanarak bu derlemelerde koşullu olarak derleyebilirsiniz.

Aşağıdaki kitaplık projesi .NET Standard ( `netstandard1.4` ) ve .NET Framework (ve) API 'lerini `net40` hedefler `net45` . Birden çok hedef çerçeve ile çoğul [Targetçerçeveler öğesini](../core/project-sdk/msbuild-props.md#targetframeworks) kullanın. Bu `Condition` öznitelikler, kitaplık iki .NET Framework TFMs için derlendiğinde uygulamaya özgü paketleri içerir:

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <TargetFrameworks>netstandard1.4;net40;net45</TargetFrameworks>
  </PropertyGroup>

  <!-- Conditionally obtain references for the .NET Framework 4.0 target -->
  <ItemGroup Condition=" '$(TargetFramework)' == 'net40' ">
    <Reference Include="System.Net" />
  </ItemGroup>

  <!-- Conditionally obtain references for the .NET Framework 4.5 target -->
  <ItemGroup Condition=" '$(TargetFramework)' == 'net45' ">
    <Reference Include="System.Net.Http" />
    <Reference Include="System.Threading.Tasks" />
  </ItemGroup>

</Project>
```

Kitaplığınızda veya uygulamanızda, her bir hedef çerçeve için derlemek üzere [önişlemci yönergelerini](../csharp/language-reference/preprocessor-directives/preprocessor-if.md) kullanarak koşullu kod yazarsınız:

```csharp
public class MyClass
{
    static void Main()
    {
#if NET40
        Console.WriteLine("Target framework: .NET Framework 4.0");
#elif NET45
        Console.WriteLine("Target framework: .NET Framework 4.5");
#else
        Console.WriteLine("Target framework: .NET Standard 1.4");
#endif
    }
}
```

Yapı sistemi, SDK stili projeler kullanırken [desteklenen hedef Framework sürümleri](#supported-target-frameworks) tablosunda gösterilen hedef çerçeveleri temsil eden Önişlemci sembollerinin farkındadır. .NET Standard, .NET Core veya .NET 5 tfd 'yi temsil eden bir sembol kullanırken, nokta ve kısa çizgileri alt çizgiyle değiştirin ve küçük harfleri büyük harfe değiştirin (örneğin, sembolü `netstandard1.4` `NETSTANDARD1_4` ).

.NET hedef çerçeveleri için Önişlemci simgelerinin tüm listesi şunlardır:

[!INCLUDE [Preprocessor symbols](../../includes/preprocessor-symbols.md)]

## <a name="deprecated-target-frameworks"></a>Kullanım dışı hedef çerçeveler

Aşağıdaki hedef çerçeveler kullanım dışıdır. Bu hedef çerçeveleri hedefleyen paketlerin belirtilen değişikliklere geçirilmesi gerekir.

| Kullanımdan kaldırılan TFA                                                                             | Değiştirme |
| ------------------------------------------------------------------------------------------ | ----------- |
| aspnet50<br>aspnetcore50<br>adlar<br>DNX<br>dnx45<br>dnx451<br>dnx452                  | netcoreapp  |
| dotnet<br>dotnet50<br>dotnet51<br>dotnet52<br>dotnet53<br>dotnet54<br>dotnet55<br>dotnet56 | Netstandard |
| netcore50                                                                                  | UAP 10.0     |
| kazanırsınız                                                                                        | netcore45   |
| Win8                                                                                       | netcore45   |
| win81                                                                                      | netcore451  |
| win10                                                                                      | UAP 10.0     |
| wınrt                                                                                      | netcore45   |

## <a name="see-also"></a>Ayrıca bkz.

- [.NET 5 ' te hedef çerçeve adları](https://github.com/dotnet/designs/blob/master/accepted/2020/net5/net5.md)
- [Masaüstü uygulamalarında Windows Çalışma Zamanı API 'Leri çağırma](/windows/apps/desktop/modernize/desktop-to-uwp-enhance)
- [Platformlar Arası Araçlarla Kitaplık Geliştirme](../core/tutorials/libraries.md)
- [.NET Standard](net-standard.md)
- [.NET Core sürümü oluşturma](../core/versions/index.md)
- [DotNet/standart GitHub deposu](https://github.com/dotnet/standard)
- [NuGet araçları GitHub deposu](https://github.com/joelverhagen/NuGetTools)
- [.NET 'teki Framework profilleri](https://blog.stephencleary.com/2012/05/framework-profiles-in-net.html)
- [Platform uyumluluk çözümleyicisi](analyzers/platform-compat-analyzer.md)
