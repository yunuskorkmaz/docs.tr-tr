---
title: SDK tarzı projelerde hedef çerçeveler - .NET
description: .NET Core uygulamaları ve kitaplıkları için hedef çerçeveler hakkında bilgi edinin.
ms.date: 12/03/2019
ms.custom: updateeachrelease
ms.technology: dotnet-standard
ms.openlocfilehash: 33beb5606cbf857cc41b739f256482b0298f1fb1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "79400556"
---
# <a name="target-frameworks-in-sdk-style-projects"></a>SDK tarzı projelerde hedef çerçeveler

Bir uygulama veya kitaplıktaki bir çerçeveyi hedeflediğinizde, uygulama veya kitaplık için kullanılabilir hale getirmek istediğiniz API kümesini belirtirsiniz. Hedef Çerçeve Monikers (TFM) kullanarak proje dosyanızda hedef çerçeveyi belirtirsiniz.

Bir uygulama veya kitaplık [.NET Standard'ın](net-standard.md)bir sürümünü hedefleyebilir. .NET Standart sürümleri, tüm .NET uygulamalarında standartlaştırılmış API kümelerini temsil eder. Örneğin, bir kitaplık .NET Standart 1.6'yı hedefleyebilir ve aynı kod tabanını kullanarak .NET Core ve .NET Framework genelinde işlev gören API'lere erişebilir.

Uygulama veya kitaplık, uygulamaya özgü API'lere erişmek için belirli bir .NET uygulamasını da hedefleyebilir. Örneğin, Xamarin.iOS'u hedefleyen bir uygulama `Xamarin.iOS10`(örneğin,) iOS 10 için Xamarin tarafından sağlanan iOS API paketleyicilerine veya `uap10.0`Evrensel Windows Platformu'nu (UWP, UWP) hedefleyen bir uygulamanın Windows 10 çalıştıran aygıtlar için derlenen API'lere erişimi vardır.

Bazı hedef çerçeveler için (örneğin, .NET Framework), API'ler çerçevenin bir sisteme yükettiği derlemeler tarafından tanımlanır ve uygulama çerçevesi API'leri içerebilir (örneğin, ASP.NET).

Paket tabanlı hedef çerçeveler (örneğin, .NET Standard ve .NET Core) için API'ler uygulama veya kitaplıkta yer alan paketler tarafından tanımlanır. *Metapaket,* kendi içeriği olmayan ancak bağımlılıkların (diğer paketler) bir listesi olan bir NuGet paketidir. NuGet paket tabanlı hedef çerçevesi, çerçeveyi oluşturan tüm paketlere atıfta bulunan bir meta paketi dolaylı olarak belirtir.

## <a name="latest-target-framework-versions"></a>En son hedef çerçeve sürümleri

Aşağıdaki tabloda en yaygın hedef çerçeveler, nasıl başvuruldıkları ve [.NET Standard'ın](net-standard.md) hangi sürümünü uyguladıkları tanımlanır. Bu hedef çerçeve sürümleri en son kararlı sürümleridir. Ön sürüm sürümleri gösterilmez. Hedef Çerçeve Takma Adı (TFM), bir .NET uygulamasının veya kitaplığın hedef çerçevesini belirtmek için standartlaştırılmış bir belirteç biçimidir.

| Hedef Çerçeve      | En son <br/> Kararlı Sürüm | Hedef Çerçeve Takma (TFM) | Uygulanan <br/> .NET Standart Sürüm |
| :-------------------: | :-------------------------: | :----------------------------: | :-------------------------------------: |
| .NET Standard         | 2.1                         | netstandard2.1                 | Yok                                     |
| .NET Core             | 3.1                         | netcoreapp3.1                  | 2.1                                     |
| .NET Framework        | 4.8                         | net48                          | 2,0                                     |

## <a name="supported-target-framework-versions"></a>Desteklenen hedef çerçeve sürümleri

Hedef çerçeve genellikle bir TFM tarafından başvurulan. Aşağıdaki tabloda .NET Core SDK ve NuGet istemcisi tarafından desteklenen hedef çerçeveler gösterilmektedir. Eşdeğerleri parantez içinde gösterilir. Örneğin, `win81` eşdeğer bir TFM `netcore451`olduğunu .

| Hedef Çerçeve           | Tfm |
| -------------------------- | --- |
| .NET Standard              | netstandard1.0<br>netstandart1.1<br>netstandart1.2<br>netstandart1.3<br>netstandart1.4<br>netstandart1.5<br>netstandart1.6<br>netstandard2.0<br>netstandard2.1 |
| .NET Core                  | netcoreapp1.0<br>netcoreapp1.1<br>netcoreapp2.0<br>netcoreapp2.1<br>netcoreapp2.2<br>netcoreapp3.0<br>netcoreapp3.1 |
| .NET Framework             | net11<br>net20<br>net35<br>net40<br>net403<br>net45<br>net451<br>net452<br>net46<br>net461<br>net462<br>net47<br>net471<br>net472<br>net48 |
| Windows Mağazası              | netcore [netcore45]<br>netcore45 [kazanmak] [win8]<br>netcore451 [win81] |
| .NET Mikro Çerçeve       | netmf |
| Silverlight                | sl4<br>sl5 |
| Windows Phone              | wp [wp7]<br>wp7<br>wp75<br>wp8<br>wp81<br>wpa81 |
| Evrensel Windows Platformu | uap [uap10.0]<br>uap10.0 [win10] [netcore50] |

## <a name="how-to-specify-target-frameworks"></a>Hedef çerçeveler nasıl belirtilir?

Hedef çerçeveler proje dosyanızda belirtilir. Tek bir hedef çerçevesi belirtildiğinde, **TargetFramework** öğesini kullanın. Aşağıdaki konsol uygulaması proje dosyası ,NET Core 3.0'ı nasıl hedeflenebildiğini gösterir:

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp3.0</TargetFramework>
  </PropertyGroup>

</Project>
```

Birden çok hedef çerçevesi belirttiğiniz zaman, her hedef çerçeve için koşullu başvuru derlemeleri olabilir. Kodunuzda, *if-then-else* mantığına sahip önişlemci sembolleri kullanarak bu derlemelere karşı koşullu olarak derleyebilirsiniz.

Aşağıdaki kitaplık proje dosyası ,NET Standard`netstandard1.4`( ) api'lerini`net40` ve `net45`.NET Framework (ve) API'lerini hedefler. Birden çok hedef çerçevesi olan çoğul **TargetFrameworks** öğesini kullanın. Kitaplık `Condition` iki .NET Framework TFMs için derlendiğinde özniteliklerin uygulamaya özgü paketleri nasıl içerdiğine dikkat edin:

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

Kitaplığınız veya uygulamanızda, her hedef çerçeve için derlemek üzere koşullu kod yazarsınız:

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

Yapı sistemi, SDK tarzı projeleri kullanırken [Desteklenen hedef çerçeve sürümleri](#supported-target-framework-versions) tablosunda gösterilen hedef çerçeveleri temsil eden önişlemci simgelerinin farkındadır. .NET Standard veya .NET Core TFM'yi temsil eden bir simge kullanırken, noktayı alt bir alt noktayla `netstandard1.4` `NETSTANDARD1_4`değiştirin ve küçük harfleri büyük harfe çevirin (örneğin, sembolü.

.NET Core hedef çerçeveleri için önişlemci sembollerinin tam listesi:

[!INCLUDE [Preprocessor symbols](../../includes/preprocessor-symbols.md)]

## <a name="deprecated-target-frameworks"></a>Amortismana yönelik hedef çerçeveler

Aşağıdaki hedef çerçeveler amortismana alınır. Bu hedef çerçeveleri hedefleyen paketler belirtilen değiştirmelere geçirilmelidir.

| Amortismana uyan TFM                                                                             | Değiştirme |
| ------------------------------------------------------------------------------------------ | ----------- |
| aspnet50<br>aspnetcore50<br>dnxcore50<br>Dnx<br>dnx45<br>dnx451<br>dnx452                  | netcoreapp  |
| dotnet<br>dotnet50<br>dotnet51<br>dotnet52<br>dotnet53<br>dotnet54<br>dotnet55<br>dotnet56 | netstandart |
| netcore50                                                                                  | uap10.0     |
| Kazanmak                                                                                        | netcore45   |
| win8                                                                                       | netcore45   |
| win81                                                                                      | netcore451  |
| kazanmak10                                                                                      | uap10.0     |
| winrt                                                                                      | netcore45   |

## <a name="see-also"></a>Ayrıca bkz.

- [Paketler, Metapaketler ve Çerçeveler](../core/packages.md)
- [Platformlar Arası Araçlarla Kitaplık Geliştirme](../core/tutorials/libraries.md)
- [.NET Standard](net-standard.md)
- [.NET Çekirdek Versiyon](../core/versions/index.md)
- [dotnet/standart GitHub deposu](https://github.com/dotnet/standard)
- [NuGet Araçları GitHub Deposu](https://github.com/joelverhagen/NuGetTools)
- [.NET'teki Çerçeve Profiller](https://blog.stephencleary.com/2012/05/framework-profiles-in-net.html)
