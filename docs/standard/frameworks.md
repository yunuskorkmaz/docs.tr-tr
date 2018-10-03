---
title: Hedef Çerçeve
description: Hedef çerçeve için .NET Core uygulamaları ve kitaplıkları hakkında bilgi edinin.
author: richlander
ms.author: mairaw
ms.date: 05/31/2018
ms.custom: updateeachrelease
ms.technology: dotnet-standard
ms.openlocfilehash: 76bf496e957022f4d97d3cf3f3975f334b1d5c45
ms.sourcegitcommit: ea00c05e0995dae928d48ead99ddab6296097b4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48046662"
---
# <a name="target-frameworks"></a>Hedef Çerçeve

Bir uygulama veya kitaplık bir çerçeve hedeflediğinizde, uygulama veya kitaplık için kullanılabilir hale getirmek istediğiniz API kümesi belirlediniz. Hedef Çerçeve bilinen adlar (Tfm'ler) kullanarak proje dosyanızda hedef Framework'ü belirt

Bir uygulama veya kitaplık bir sürümünü hedefleyebilirsiniz [.NET Standard](~/docs/standard/net-standard.md). .NET standard sürümleri standartlaştırılmış API'leri kümelerindeki tüm .NET uygulamalarında temsil eder. Örneğin, bir kitaplık .NET standart 1.6 hedef ve bu .NET Core ve .NET Framework kullanarak aynı kod temeli üzerinde bu işlev API'lerine erişimi elde edebilirsiniz.

Ayrıca, bir uygulama veya kitaplık uygulamaya özel API'lere erişim elde etmek için belirli bir .NET uygulaması hedefleyebilirsiniz. Örneğin, Xamarin.iOS hedefleyen bir uygulama (örneğin, `Xamarin.iOS10`) sağlanan Xamarin iOS API sarmalayıcıları iOS 10 veya evrensel Windows platformu hedefleyen bir uygulama için erişim alır (UWP, `uap10.0`) çalıştıran cihazlar derleme API'lerine erişebilir Windows 10.

Bazı hedef çerçeveleri (örneğin, .NET Framework) için API framework bir sistemine yükler ve uygulama çerçevesi API'leri (örneğin, ASP.NET) içerebilir derlemeler tarafından tanımlanır.

Paket tabanlı hedef çerçeve (örneğin, .NET Standard ve .NET Core), API'ler, uygulama veya kitaplık dahil edilen paketler tarafından tanımlanır. A *metapackage* kendi ancak hiçbir içeriği olan bir NuGet paketi bağımlılıkları (diğer paketleri) listesini olmasıdır. Bir NuGet paketi tabanlı hedef çerçeve birlikte framework yaptığınız tüm paketleri başvuran bir metapackage örtük olarak belirtir.

## <a name="latest-target-framework-versions"></a>En yeni hedef framework sürümleri

Aşağıdaki tabloda en yaygın hedef çerçeveleri, nasıl başvurulan ve hangi sürümünü tanımlar [.NET Standard](~/docs/standard/net-standard.md) uyguladıkları. Bu hedef framework sürümlerini en son kararlı sürümleridir. Yayın öncesi sürümleri gösterilmez. Hedef Çerçeve adı (TFM) bir .NET uygulaması veya kitaplığı hedef Framework'ü belirtmek için standartlaştırılmış bir belirteci biçimi ' dir.

| Hedef Çerçeve      | En son <br/> Kararlı bir sürüm | Hedef Çerçeve adı (TFM) | Uygulanmadı <br/> .NET standard sürümü |
| :-------------------: | :-------------------------: | :----------------------------: | :-------------------------------------: |
| .NET standard         | 2,0                         | netstandard2.0                 | Yok                                     |
| .NET Core             | 2.1                         | netcoreapp2.1                  | 2,0                                     |
| .NET Framework        | 4.7.2                       | net472                         | 2,0                                     |

## <a name="supported-target-framework-versions"></a>Desteklenen hedef framework sürümü

Hedef Framework'ü genellikle bir TFM tarafından başvuruluyor. Aşağıdaki tablo, .NET Core SDK'sını ve NuGet istemcisi tarafından desteklenen hedef çerçeveleri gösterir. Eşdeğerleri parantez içinde gösterilmektedir. Örneğin, `win81` olduğu için bir eşdeğer TFM `netcore451`.

| Hedef Çerçeve           | TFM |
| -------------------------- | --- |
| .NET standard              | netstandard1.0<br>netstandard1.1<br>netstandard1.2<br>netstandard1.3<br>netstandard1.4<br>netstandard1.5<br>netstandard1.6<br>netstandard2.0 |
| .NET Core                  | netcoreapp1.0<br>netcoreapp1.1<br>netcoreapp2.0<br>netcoreapp2.1 |
| .NET Framework             | net11<br>net20<br>net35<br>net40<br>net403<br>net45<br>net451<br>net452<br>net46<br>net461<br>net462<br>net47<br>net471<br>net472 |
| Windows Mağazası              | netcore [netcore45]<br>netcore45 [win] [win8]<br>netcore451 [win81] |
| .NET mikro Framework       | netmf |
| Silverlight                | sl4<br>sl5 |
| Windows Phone              | WP [wp7]<br>wp7<br>wp75<br>wp8<br>wp81<br>wpa81 |
| Evrensel Windows Platformu | uap [uap10.0]<br>uap10.0 [win10] [netcore50] |

## <a name="how-to-specify-target-frameworks"></a>Hedef Çerçeve belirtme

Hedef Çerçeve proje dosyanızda belirtilir. Tek hedef Framework'ü belirtildiğinde kullanın **TargetFramework** öğesi. Aşağıdaki konsol uygulama projesi dosyası, .NET Core 2.0 hedef gösterilmektedir:

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp2.0</TargetFramework>
  </PropertyGroup>

</Project>
```

Birden çok hedef çerçeve belirttiğinizde, her hedef çerçeve için derlemeleri koşullu başvurabilir. Kodunuzda, koşullu olarak karşı bu derlemeler ile önişlemci sembolleri kullanarak derleyebilirsiniz *if-then-else* mantığı.

Aşağıdaki kitaplık projesi dosyası .NET Standard API'leri, hedefler (`netstandard1.4`) ve API'leri .NET Framework'ün (`net40` ve `net45`). Çoğul kullanın **TargetFrameworks** birden fazla hedef Framework'e sahip öğe. Not nasıl `Condition` öznitelikler, kitaplık için iki .NET Framework Tfm'ler derlendiğinde uygulama paketleri içerir:

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

Kitaplık veya uygulama içinde her hedef çerçeve için derlemek için koşullu bir kod yazın:

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

Derleme Sistemi gösterilen hedef çerçeveyi temsil eden önişlemci sembolleri farkında [desteklenen hedef framework sürümü](#supported-target-framework-versions) tablo. .NET Standard veya .NET Core TFM temsil eden bir simge kullanırken, nokta, alt çizgi ile değiştirin ve küçük harfleri büyük harfe Değiştir (örneğin, simgesi `netstandard1.4` olan `NETSTANDARD1_4`).

.NET Core hedef çerçeve önişlemci sembolleri tam listesi verilmiştir:

[!INCLUDE [Preprocessor symbols](~/includes/preprocessor-symbols.md)]

## <a name="deprecated-target-frameworks"></a>Kullanım dışı hedef çerçeve

Aşağıdaki hedef çerçeveleri kullanım dışı bırakılmıştır. Bu hedef çerçeve hedefleme paketleri için belirtilen değişiklik geçirmeniz gerekir.

| Kullanım dışı TFM                                                                             | Değiştirme |
| ------------------------------------------------------------------------------------------ | ----------- |
| aspnet50<br>aspnetcore50 olarak<br>dnxcore50<br>dnx<br>dnx45<br>dnx451<br>dnx452                  | netcoreapp  |
| DotNet<br>dotnet50<br>dotnet51<br>dotnet52<br>dotnet53<br>dotnet54<br>dotnet55<br>dotnet56 | netstandard |
| netcore50                                                                                  | uap10.0     |
| Win                                                                                        | netcore45   |
| win8                                                                                       | netcore45   |
| win81                                                                                      | netcore451  |
| win10                                                                                      | uap10.0     |
| winrt                                                                                      | netcore45   |

## <a name="see-also"></a>Ayrıca bkz.

- [Paketler, Meta Paketler ve Çerçeveler](../core/packages.md)  
- [Platformlar Arası Araçlarla Kitaplık Geliştirme](../core/tutorials/libraries.md)  
- [.NET Standard](net-standard.md)  
- [.NET core sürüm oluşturma](../core/versions/index.md)  
- [DotNet/standart GitHub deposu](https://github.com/dotnet/standard)  
- [NuGet araçları GitHub deposu](https://github.com/joelverhagen/NuGetTools)  
- [.NET Framework profillerinde](https://blog.stephencleary.com/2012/05/framework-profiles-in-net.html)
