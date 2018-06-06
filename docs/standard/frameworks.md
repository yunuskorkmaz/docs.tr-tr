---
title: Hedef Çerçeve
description: .NET Core uygulamaları ve kitaplıklar için bir hedef çerçeveyi hakkında bilgi edinin.
author: richlander
ms.author: mairaw
ms.date: 05/31/2018
ms.custom: updateeachrelease
ms.technology: dotnet-standard
ms.openlocfilehash: 346eece8fdb391fd62b369db6ef65964fcd6e67a
ms.sourcegitcommit: bbf70abe6b46073148f78cbf0619de6092b5800c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34728322"
---
# <a name="target-frameworks"></a>Hedef Çerçeve

Bir uygulama veya kitaplıktaki bir çerçeve hedeflediğinizde, uygulama veya kitaplık kullanılabilir yapmak ister misiniz API kümesi belirlediniz. Hedef Framework'ü hedef Framework adlar (TFMs) kullanarak proje dosyasında belirtin.

Bir uygulama ya da kitaplık sürümü hedefleyebilirsiniz [.NET standart](~/docs/standard/net-standard.md). .NET standart sürümleri API'leri standartlaştırılmış kümeleri tüm .NET uygulamaları arasında temsil eder. Örneğin, bir kitaplık .NET standart 1.6 hedef ve API'leri bu işlev .NET Core ve .NET çerçevesi aynı kod temeli kullanılarak üzerinden erişim.

Ayrıca bir uygulama ya da kitaplık uygulaması özgü API'lerine erişmek için belirli bir .NET uygulaması hedefleyebilirsiniz. Örneğin, bir Xamarin.iOS hedefleyen uygulama (örneğin, `Xamarin.iOS10`) iOS 10 için sağlanan Xamarin iOS API sarmalayıcıları veya evrensel Windows platformu hedefleyen bir uygulama için erişim alır (UWP, `uap10.0`) çalıştıran cihazlar derleme API erişimi Windows 10.

Bazı hedef çerçeveyi (örneğin, .NET Framework) için API'ler framework bir sistemde yükler ve uygulama çerçevesi API'leri (örneğin, ASP.NET) içerebilir derlemeleri tarafından tanımlanır.

Paket tabanlı bir hedef çerçeve için (örneğin, .NET standart ve .NET Core), API uygulaması veya kitaplıkta bulunan paketleri tarafından tanımlanır. A *metapackage* kendi ancak hiçbir içeriği olan bir NuGet paketi bağımlılıkları (diğer paketleri) listesini numarasıdır. Bir NuGet paketi tabanlı hedef framework örtük olarak birlikte çerçevesi olun tüm paketler başvuruda bulunan bir metapackage belirtir.

## <a name="latest-target-framework-versions"></a>Son hedef framework sürümleri

Aşağıdaki tabloda en yaygın hedef çerçeve, nasıl başvurulan ve hangi sürümü tanımlar [.NET standart](~/docs/standard/net-standard.md) uyguladıkları. Bu hedef framework sürümleri en son kararlı sürümleridir. Yayın öncesi sürümleri gösterilmeyen. Bir hedef Framework bilinen ad (TFM) .NET uygulaması veya kitaplık hedef çerçevesini belirtmek için standartlaştırılmış bir belirteci biçimi ' dir.

| Hedef çerçevesi      | En son <br/> Kararlı sürümü | Hedef Framework ad (TFM) | Uygulanmadı <br/> .NET standart sürüm |
| :-------------------: | :-------------------------: | :----------------------------: | :-------------------------------------: |
| .NET standart         | 2,0                         | netstandard2.0                 | Yok                                     |
| .NET Core             | 2.1                         | netcoreapp2.1                  | 2,0                                     |
| .NET Framework        | 4.7.2                       | net472                         | 2,0                                     |

## <a name="supported-target-framework-versions"></a>Desteklenen hedef framework sürümleri

Bir hedef framework genellikle TFM tarafından başvuruluyor. Aşağıdaki tabloda, .NET Core SDK ve NuGet istemcisi tarafından desteklenen bir hedef çerçeveyi gösterir. Eşdeğerleri köşeli ayraç içinde görüntülenir. Örneğin, `win81` için eşdeğer bir TFM olduğu `netcore451`.

| Hedef çerçevesi           | TFM |
| -------------------------- | --- |
| .NET standart              | netstandard1.0<br>netstandard1.1<br>netstandard1.2<br>netstandard1.3<br>netstandard1.4<br>netstandard1.5<br>netstandard1.6<br>netstandard2.0 |
| .NET Core                  | netcoreapp1.0<br>netcoreapp1.1<br>netcoreapp2.0<br>netcoreapp2.1 |
| .NET Framework             | net11<br>net20<br>Net35<br>net40<br>net403<br>net45<br>net451<br>net452<br>net46<br>net461<br>net462<br>net47<br>net471<br>net472 |
| Windows Mağazası              | netcore [netcore45]<br>netcore45 [win] [olduğu win8]<br>netcore451 [win81] |
| Mikro .NET Framework       | netmf |
| Silverlight                | sl4<br>sl5 |
| Windows Phone              | WB [wp7]<br>wp7<br>wp75<br>wp8<br>wp81<br>wpa81 |
| Evrensel Windows Platformu | uap [uap10.0]<br>uap10.0 [win10] [netcore50] |

## <a name="how-to-specify-target-frameworks"></a>Bir hedef çerçeveyi belirtme

Bir hedef çerçeveyi, proje dosyasında belirtilir. Bir tek hedef framework belirtildiğinde kullanmak **TargetFramework** öğesi. Aşağıdaki konsol uygulama projesi dosyasını .NET Core 2.0 hedef gösterilmiştir:

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp2.0</TargetFramework>
  </PropertyGroup>

</Project>
```

Birden çok hedef çerçeveyi belirttiğinizde, her hedef çerçevesi için derlemeleri koşullu başvurabilir. Kodunuzda, koşullu bu derlemeler karşı önişlemci sembolleriyle kullanarak derleyebilir *IF-then-else* mantığı.

Aşağıdaki kitaplığı proje dosyası .NET standart API'leri, hedefler (`netstandard1.4`) ve API'ler .NET Framework'ün (`net40` ve `net45`). Çoğul kullanmak **TargetFrameworks** birden çok hedef çerçeveyi sahip öğe. Not nasıl `Condition` öznitelikler, kitaplık için iki .NET Framework TFMs derlendiğinde uygulamaya özel paketleri içerir:

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

Kitaplığı veya uygulama içinde her hedef çerçeve için derlemek için koşullu bir kod yazın:

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

Derleme Sistemi gösterildiği bir hedef çerçeveyi temsil eden önişlemci simgelerin bilmez [desteklenen hedef framework sürümlerini](#supported-target-framework-versions) tablo. Bir .NET standart veya .NET Core TFM temsil eden bir simge kullanırken, nokta bir alt çizgi ve küçük harfleri büyük harfe değiştirebilirsiniz (örneğin, simge için `netstandard1.4` olan `NETSTANDARD1_4`).

.NET Core hedef çerçeveyi önişlemci simgelerini tam listesi verilmiştir:

[!INCLUDE [Preprocessor symbols](~/includes/preprocessor-symbols.md)]

## <a name="deprecated-target-frameworks"></a>Kullanım dışı hedef çerçeveler

Aşağıdaki hedef çerçeveyi kullanım dışı bırakılmıştır. Bu bir hedef çerçeveyi hedefleme paketleri için belirtilen değiştirmeler geçirmeniz gerekir.

| Kullanım dışı TFM                                                                             | Değiştirme |
| ------------------------------------------------------------------------------------------ | ----------- |
| aspnet50<br>aspnetcore50<br>dnxcore50<br>dnx<br>dnx45<br>dnx451<br>dnx452                  | netcoreapp  |
| DotNet<br>dotnet50<br>dotnet51<br>dotnet52<br>dotnet53<br>dotnet54<br>dotnet55<br>dotnet56 | netstandard |
| netcore50                                                                                  | uap10.0     |
| Win                                                                                        | netcore45   |
| olduğu win8                                                                                       | netcore45   |
| win81                                                                                      | netcore451  |
| win10                                                                                      | uap10.0     |
| winrt                                                                                      | netcore45   |

## <a name="see-also"></a>Ayrıca bkz.

[Paketler, Meta Paketler ve Çerçeveler](../core/packages.md)  
[Platformlar Arası Araçlarla Kitaplık Geliştirme](../core/tutorials/libraries.md)  
[.NET Standard](net-standard.md)  
[.NET core sürüm oluşturma](../core/versions/index.md)  
[DotNet/standart GitHub deposunu](https://github.com/dotnet/standard)  
[GitHub depo NuGet araçları](https://github.com/joelverhagen/NuGetTools)  
[.NET Framework profilleri](https://blog.stephencleary.com/2012/05/framework-profiles-in-net.html)
