---
title: Bir WPF uygulamasının .NET Core 3,0 bağlantı noktası
description: .NET Framework Windows Presentation Foundation uygulamasının Windows için .NET Core 3,0 'e nasıl bağlantı alınacağını öğretir.
author: Thraka
ms.author: adegeo
ms.date: 03/27/2019
ms.custom: ''
ms.openlocfilehash: 4ff3ca9610e7fa9355931ca2013def1157fab8b2
ms.sourcegitcommit: 56f1d1203d0075a461a10a301459d3aa452f4f47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71216189"
---
# <a name="how-to-port-a-wpf-desktop-app-to-net-core"></a>Nasıl yapılır: .NET Core 'a bir WPF Masaüstü uygulaması bağlantı noktası

Bu makalede, .NET Framework Windows Presentation Foundation tabanlı (WPF) Masaüstü uygulamanızın .NET Core 3,0 ' ye nasıl bağlantı kurulacağı açıklanmaktadır. .NET Core 3,0 SDK, WPF uygulamaları için destek içerir. WPF hala yalnızca Windows Framework 'ü ve Windows üzerinde çalışır. Bu örnek, projenizi oluşturmak ve yönetmek için .NET Core SDK CLı kullanır.

Bu makalede, geçiş için kullanılan dosya türlerini tanımlamak için çeşitli adlar kullanılır. Projeniz geçirilirken dosyalarınız farklı şekilde adlandırılır, bu sayede bunları aşağıda listelenen adlarla eşleştirin:

| Dosya | Açıklama |
| ---- | ----------- |
| **Uygps. sln** | Çözüm dosyasının adı. |
| **MyWPF. csproj** | Bağlantı noktasına .NET Framework WPF projesinin adı. |
| **MyWPFCore. csproj** | Oluşturduğunuz yeni .NET Core projesinin adı. |
| **MyAppCore. exe** | .NET Core WPF uygulaması yürütülebilir dosyası. |

>[!IMPORTANT]
>Bu makalede C# hedef dil olarak kullanılsa da, vb.net, sırasıyla. *csproj* ve. *CS* dosyaları yerine *. vbproj* ve. *vb* dosyalarını kullanması dışında, vb.NET için de aynıdır.

## <a name="prerequisites"></a>Önkoşullar

- İstediğiniz tasarımcı çalışması için [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) .

  Aşağıdaki Visual Studio iş yüklerini yükler:
  - .NET masaüstü geliştirme
  - .NET platformlar arası geliştirme

- Sorun olmadan oluşturulup çalışan bir çözümde çalışan bir WPF projesi.
- En son [.NET Core 3,0](https://aka.ms/netcore3download) önizlemeyi yükler.

>[!NOTE]
>**Visual Studio 2017** , .net Core 3,0 projelerini desteklemez. **Visual Studio 2019** , .net Core 3,0 projelerini destekler, ancak .NET Core WPF görsel Tasarımcısı için sınırlı destek içerir. Tam olarak desteklenen bir görsel tasarımcı kullanmak için, çözümünüzde dosyalarını .NET Core projesiyle paylaşan bir .NET Framework WPF projeniz olmalıdır.

### <a name="consider"></a>Seçmeyi

.NET Framework WPF uygulaması taşıma sırasında göz önünde bulundurmanız gereken birkaç nokta vardır.

01. Uygulamanızın geçiş için iyi bir aday olduğunu kontrol edin.

    Projenizin .NET Core 3,0 ' e geçiş olacağını öğrenmek için [.net taşınabilirlik Çözümleyicisi](../../standard/analyzers/portability-analyzer.md) ' ni kullanın. Projenizde .NET Core 3,0 ile ilgili sorunlar varsa, çözümleyici bu sorunları belirlemenize yardımcı olur.

01. Farklı bir WPF sürümü kullanıyorsunuz.

    .NET Core 3,0 Preview 1 yayınlandığında, WPF GitHub 'da açık kaynak olarak oluştu. .NET Core WPF kodu, .NET Framework WPF kod temelinin çatalından oluşur. Bazı farklılıklar olabilir ve uygulamanızın bağlantı noktası olmayacaktır.

01. [Windows Uyumluluk Paketi][compat-pack] , geçiş yapmanıza yardımcı olabilir.

    .NET Framework ' de kullanılabilen bazı API 'Ler .NET Core 3,0 ' de kullanılamaz. [Windows Uyumluluk Paketi][compat-pack] bu API 'lerin çoğunu ekler ve WPF uygulamanızın .NET Core ile uyumlu olmasına yardımcı olabilir.

01. Projeniz tarafından kullanılan NuGet paketlerini güncelleştirin.

    Herhangi bir geçişten önce NuGet paketlerinin en son sürümlerini kullanmak her zaman iyi bir uygulamadır. Uygulamanız herhangi bir NuGet paketine başvuruyorsa, bunları en son sürüme güncelleştirin. Uygulamanızın başarıyla derlemediğinden emin olun. Yükseltmeden sonra, herhangi bir paket hatası varsa, paketi, kodunuzu kesen en son sürüme indirgeymelisiniz.

01. Visual Studio 2019 henüz .NET Core 3,0 için WPF tasarımcısını desteklemiyor

    Şu anda, Visual Studio 'da WPF tasarımcısını kullanmak istiyorsanız mevcut .NET Framework WPF proje dosyanızı saklamanız gerekir.

## <a name="create-a-new-sdk-project"></a>Yeni bir SDK projesi oluştur

Oluşturduğunuz yeni .NET Core 3,0 projesi .NET Framework projenizden farklı bir dizinde olmalıdır. İkisi de aynı dizinde ise, **obj** dizininde oluşturulan dosyalarla çakışmalarıyla karşılaşabilirsiniz. Bu örnekte, **SolutionFolder** dizininde **MyWPFAppCore** adlı bir dizin oluşturacaksınız:

```
SolutionFolder
├───MyApps.sln
├───MyWPFApp
│   └───MyWPF.csproj
└───MyWPFAppCore      <--- New folder for core project
```

Sonra, **MyWPFAppCore** dizininde **mywpfcore. csproj** projesini oluşturmanız gerekir. Bu dosyayı tercih ettiğiniz metin düzenleyicisini kullanarak el ile oluşturabilirsiniz. Aşağıdaki XML 'e yapıştırın:

```xml
<Project Sdk="Microsoft.NET.Sdk.WindowsDesktop">

  <PropertyGroup>
    <OutputType>WinExe</OutputType>
    <TargetFramework>netcoreapp3.0</TargetFramework>
    <UseWPF>true</UseWPF>
  </PropertyGroup>

</Project>
```

Proje dosyasını el ile oluşturmak istemiyorsanız, projeyi oluşturmak için Visual Studio 'Yu veya .NET Core SDK kullanabilirsiniz. Ancak proje dosyası hariç proje şablonu tarafından oluşturulan diğer tüm dosyaları silmeniz gerekir. SDK 'yı kullanmak için **SolutionFolder** dizininden aşağıdaki komutu çalıştırın:

```dotnetcli
dotnet new wpf -o MyWPFAppCore -n MyWPFCore
```

**Mywpfcore. csproj**öğesini oluşturduktan sonra, dizin yapınız aşağıdaki gibi görünmelidir:

```
SolutionFolder
├───MyApps.sln
├───MyWPFApp
│   └───MyWPF.csproj
└───MyWPFAppCore
    └───MyWPFCore.csproj
```

Visual Studio ya da **SolutionFolder** dizininden .NET Core CLI **mywpfcore. csproj** projesini **uygulamaps. sln** ' ye eklemek isteyeceksiniz:

```dotnetcli
dotnet sln add .\MyWPFAppCore\MyWPFCore.csproj
```

## <a name="fix-assembly-info-generation"></a>Derleme bilgileri oluşturmayı çözme

.NET Framework ile oluşturulan Windows Presentation Foundation projeler, oluşturulacak derlemenin sürümü `AssemblyInfo.cs` gibi derleme özniteliklerini içeren bir dosya içerir. SDK stilindeki projeler, SDK proje dosyasını temel alarak bu bilgileri sizin için otomatik olarak oluşturur. Her iki tür "derleme bilgisi" de bir çakışma oluşturur. Otomatik oluşturmayı devre dışı bırakarak bu sorunu çözün. Bu, projeyi mevcut `AssemblyInfo.cs` dosyanızı kullanmaya zorlar.

Ana `<PropertyGroup>` düğüme eklemenin üç ayarı vardır. 

- **Generateassemblyınfo**\
Bu özelliği `false`' a ayarladığınızda, derleme özniteliklerini oluşturmaz. Bu, .NET Framework projesinden mevcut `AssemblyInfo.cs` dosya ile çakışmayı önler.

- **AssemblyName**\
Bu özelliğin değeri, derlerken oluşturulan çıkış ikilisi olur. Ada eklenen bir uzantıya gerek yoktur. Örneğin, kullanılarak `MyCoreApp` üretir `MyCoreApp.exe`.

- **RootNamespace**\
Projeniz tarafından kullanılan varsayılan ad alanı. Bu, .NET Framework projesinin varsayılan ad alanıyla eşleşmelidir.

Bu üç öğeyi `<PropertyGroup>` `MyWPFCore.csproj` dosyadaki düğümüne ekleyin:

```xml
<Project Sdk="Microsoft.NET.Sdk.WindowsDesktop">

  <PropertyGroup>
    <OutputType>WinExe</OutputType>
    <TargetFramework>netcoreapp3.0</TargetFramework>
    <UseWPF>true</UseWPF>

    <GenerateAssemblyInfo>false</GenerateAssemblyInfo>
    <AssemblyName>MyCoreApp</AssemblyName>
    <RootNamespace>MyWPF</RootNamespace>
  </PropertyGroup>

</Project>
```

## <a name="add-source-code"></a>Kaynak kodu ekle
Şu anda **Mywpfcore. csproj** projesi hiçbir kodu derlemez. Varsayılan olarak, .NET Core projeleri geçerli dizine ve tüm alt dizinlere tüm kaynak kodlarını otomatik olarak ekler. Projeyi, .NET Framework projesinden bir göreli yol kullanarak kod içerecek şekilde yapılandırmanız gerekir. .NET Framework projeniz Windows ve denetimlerinizin simgeleri ve kaynakları için **. resx** dosyalarını kullandıysanız, bunları da eklemeniz gerekir. 

Projenize eklemeniz `<ItemGroup>` gereken ilk düğüm, uygulamanızın kullandığı başlangıç yapılandırmasını ve kaynaklarını temsil eden **app. xaml** dosyasını içerir. **App. xaml** dosyasında Ayrıca eşlik eden bir **app.xaml.cs** dosyası bulunur, ancak otomatik olarak farklı `<ItemGroup>`bir şekilde dahil edilir.

```xml
  <ItemGroup>
    <ApplicationDefinition Include="..\MyWPFApp\App.xaml">
      <Generator>MSBuild:Compile</Generator>
    </ApplicationDefinition>
  </ItemGroup>
```

Ardından, aşağıdaki `<ItemGroup>` düğümü projenize ekleyin. Her bir bildirimde alt dizinler içeren bir dosya glob kalıbı bulunur. Projeniz, herhangi bir ayar dosyası ve tüm kaynaklar için kaynak kodunu içerir. **Obj** dizini açıkça dışarıda bırakılır.

```xml
  <ItemGroup>
    <Compile Include="..\MyWPFApp\**\*.cs" Exclude="..\MyWPFApp\obj\**" />
    <None Include="..\MyWPFApp\**\*.settings" />
    <EmbeddedResource Include="..\MyWPFApp\**\*.resx" />
  </ItemGroup>
```

Daha sonra, **app. xaml** dosyası hariç `<Page>` , projenizdeki her **xaml** dosyası için bir giriş içeren başka bir `<ItemGroup>` düğüm ekleyin. Bunlar **xaml** biçiminde olan tüm Windows, sayfa ve kaynakları içerir. Burada bir glob modelini kullanamazsınız ve her dosya için bir giriş eklemeli ve `<Generator>` kullanılan ' i belirtmeniz gerekir.

```xml
  <ItemGroup>
    <Page Include="..\MyWPFApp\MainWindow.xaml">
      <Generator>MSBuild:Compile</Generator>
    </Page>
  </ItemGroup>
```

## <a name="add-nuget-packages"></a>NuGet paketleri Ekle

.NET Framework projesi tarafından başvurulan her bir NuGet paketini .NET Core projesine ekleyin. 

Büyük olasılıkla .NET Framework WPF uygulamanız, projeniz tarafından başvurulan tüm NuGet paketlerinin listesini içeren bir **Packages. config** dosyasına sahiptir. .NET Core projesine hangi NuGet paketlerinin ekleneceğini öğrenmek için bu listeye bakabilirsiniz. Örneğin, .NET Framework projesi `MahApps.Metro` NuGet paketine başvuruyorsa, Visual Studio ile projeye ekleyin. Ayrıca, **SolutionFolder** dizininden .NET Core CLI paket başvurusunu ekleyebilirsiniz:

```dotnetcli
dotnet add .\MyWPFAppCore\MyWPFCore.csproj package MahApps.Metro -v 2.0.0-alpha0262
```

Önceki komut **Mywpfcore. csproj** projesine aşağıdaki NuGet başvurusunu ekler:

```xml
  <ItemGroup>
    <PackageReference Include="MahApps.Metro" Version="2.0.0-alpha0262" />
  </ItemGroup>
```

## <a name="problems-compiling"></a>Derleme sorunları

Projelerinizi derlerken sorunlarla karşılaşırsanız, .NET Core 'da .NET Framework, ancak kullanılamayan yalnızca Windows salt Windows API 'Lerini kullanıyor olabilirsiniz. [Windows Uyumluluk Paketi][compat-pack] NuGet paketini projenize eklemeyi deneyebilirsiniz. Bu paket yalnızca Windows üzerinde çalışır ve .NET Core ve .NET Standard projelerine 20.000 Windows API 'Leri ekler.

```dotnetcli
dotnet add .\MyWPFAppCore\MyWPFCore.csproj package Microsoft.Windows.Compatibility
```

Önceki komut **Mywpfcore. csproj** projesine aşağıdakini ekler:

```xml
  <ItemGroup>
    <PackageReference Include="Microsoft.Windows.Compatibility" Version="2.0.1" />
  </ItemGroup>
```

## <a name="wpf-designer"></a>WPF Tasarımcısı

Bu makalede açıklandığı gibi, Visual Studio 2019 yalnızca .NET Framework projelerinde WPF tasarımcısını destekler. Yan yana .NET Core projesi oluşturarak, formları tasarlamak için .NET Framework projesi kullanırken projenizi .NET Core ile test edebilirsiniz. Çözüm dosyanız hem .NET Framework hem de .NET Core projelerini içerir. .NET Framework projesindeki formlarınızı ve denetimlerinizi ekleyin ve tasarlayın ve .NET Core projelerine eklediğimiz dosya glob desenlerine bağlı olarak, .NET Core projelerine yeni veya değiştirilmiş dosyalar otomatik olarak dahil edilir.

Visual Studio 2019 WPF tasarımcısını destekledikten sonra, .NET Core proje dosyanızın içeriğini .NET Framework proje dosyasına kopyalayabilir/yapıştırabilirsiniz. Sonra `<Source>` ve`<EmbeddedResource>` öğeleriyle eklenen glob düzenlerini silin. Uygulamanız tarafından kullanılan herhangi bir proje başvurusunun yolunu düzeltin. Bu, .NET Framework projesini bir .NET Core projesine etkin bir şekilde yükseltir.

## <a name="next-steps"></a>Sonraki adımlar

- [Windows Uyumluluk Paketi][compat-pack]hakkında daha fazla bilgi edinin.
- .NET Framework WPF projenizi .NET Core 'a [taşıma hakkında bir video](https://www.youtube.com/watch?v=5MomsgkWkVw&list=PLS__JrkRveTMiWxG-Lv4cBwYfMQ6m2gmt) izleyin.

[compat-pack]: windows-compat-pack.md
