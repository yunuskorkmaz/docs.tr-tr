---
title: .NET Core 3.0 WPF uygulaması bağlantı noktası
description: Windows için .NET Core 3.0 için bir .NET Framework Windows Presentation Foundation uygulaması bağlantı noktasına öğretir.
author: Thraka
ms.author: adegeo
ms.date: 03/27/2019
ms.custom: ''
ms.openlocfilehash: 29ea308ee5147cfb18df312887e933615e349803
ms.sourcegitcommit: 0aca6c5d166d7961a1e354c248495645b97a1dc5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/30/2019
ms.locfileid: "58677540"
---
# <a name="how-to-port-a-wpf-desktop-app-to-net-core"></a>Nasıl yapılır: .NET Core için bir WPF masaüstü uygulaması bağlantı noktası

Bu makalede, bağlantı noktası tabanlı Windows Presentation Foundation (WPF) Masaüstü uygulamanızın .NET Framework için .NET Core 3.0 açıklar. .NET Core SDK 3.0 WPF uygulamaları için destek içerir. WPF, yalnızca Windows framework hala geçerli olduğunu ve yalnızca Windows üzerinde çalışır. Bu örnek, oluşturmak ve projenize yönetmek için .NET Core SDK'sı CLI'yı kullanır.

Bu makalede, çeşitli adlar, geçiş için kullanılan dosya türlerini tanımlamak için kullanılır. Projenizi geçirirken, dosyalarınızı farklı şekilde adlandırılmış, bu nedenle akıl aşağıda listelenen olanlarla eşleşmesi:

| Dosya | Açıklama |
| ---- | ----------- |
| **MyApps.sln** | Çözüm dosyasının adı. |
| **MyWPF.csproj** | Bağlantı noktası için .NET Framework WPF projesinin adı. |
| **MyWPFCore.csproj** | Oluşturduğunuz yeni .NET Core projesinin adı. |
| **MyAppCore.exe** | .NET Core WPF uygulaması çalıştırılabilir. |

## <a name="prerequisites"></a>Önkoşullar

- [Visual Studio 2019](https://visualstudio.microsoft.com/vs/preview/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=wpf+core) yapmak istediğiniz herhangi bir tasarımcı iş için.

  Aşağıdaki Visual Studio iş yüklerini yükleyin:
  - .NET masaüstü geliştirme
  - .NET platformlar arası geliştirme

- Çalışan WPF projesi oluşturan ve sorun çalışır bir çözümde.
- İçinde projenizin kodlanmasını C#. 
- Son yükleme [.NET Core 3.0](https://aka.ms/netcore3download) Önizleme.


>[!NOTE]
>**Visual Studio 2017** .NET Core 3.0 projeleri desteklemiyor. **Visual Studio 2019 Önizleme/RC** .NET Core 3.0 projeleri destekler ancak görsel tasarımcı için .NET Core 3.0 WPF projeleri henüz desteklememektedir. Görsel tasarımcıyı kullanmak için çözümünüzdeki ile .NET Core proje dosyaları paylaşan bir .NET WPF projesi olması gerekir.

### <a name="consider"></a>Göz önünde bulundurun

.NET Framework WPF uygulaması taşırken dikkate almanız gereken birkaç nokta vardır.

01. Uygulamanızı geçişi için iyi bir aday olduğundan emin olun.

    Kullanım [.NET Portability Analyzer](../../standard/analyzers/portability-analyzer.md) projeniz için .NET Core 3.0 geçirirseniz belirlemek için. Projeniz .NET Core 3.0 ile ilgili sorunlar varsa, Çözümleyicisi bu sorunları belirlemenize yardımcı olur.

01. WPF farklı bir sürümünü kullanıyorsunuz.

    .NET Core 3.0 Önizleme 1 yayımlandığında, WPF, açık kaynaklı oluştu. GitHub üzerinde. .NET Framework WPF kod tabanı deponun bir çatalını .NET Core WPF kodudur. Bu, bazı farklılıklar mevcuttur ve uygulamanızı bağlantı noktası olmaz mümkündür.

01. [Windows Uyumluluk Paketi] [ compat-pack] geçirmenize yardımcı olabilir.

    .NET Framework'te bulunan bazı API'leri, .NET Core 3. 0'kullanılamaz. [Windows Uyumluluk Paketi] [ compat-pack] bu API'lerin birçoğu ekler ve .NET Core ile uyumlu hale WPF uygulamanıza yardımcı olabilir.

01. Projeniz tarafından kullanılan NuGet paketlerini güncelleştirin.

    Tüm geçiş işleminden önce NuGet paketlerini en son sürümlerini kullanmak için her zaman iyi bir uygulamadır. Uygulamanızı herhangi bir NuGet paketinin başvuruyorsa, bunları en son sürüme güncelleştirin. Uygulamanız başarıyla derlendiğinden emin olun. Herhangi bir paket hata varsa, yükselttikten sonra paketi kodunuzu kesmeyecektir en son sürüme düşürme.

01. Visual Studio 2019 Önizleme/RC .NET Core 3.0 için WPF Tasarımcısı henüz desteklemiyor

    Şu anda, Visual Studio'da WPF Tasarımcısı kullanmak istiyorsanız, var olan .NET Framework WPF projesi dosyanızı çalışır durumda bulundurmanıza gerek.

## <a name="create-a-new-sdk-project"></a>Yeni SDK projesi oluşturma

Oluşturduğunuz yeni .NET Core 3.0 proje .NET Framework projenizden farklı bir dizinde olması gerekir. Her ikisi de aynı dizinde iseler, içinde oluşturulan dosyalar ile çakışma çalışabilir **obj** dizin. Adlı bir dizin oluşturma Bu örnekte, **MyWPFAppCore** içinde **SolutionFolder** dizini:

```
SolutionFolder
├───MyApps.sln
├───MyWPFApp
│   └───MyWPF.csproj
└───MyWPFAppCore      <--- New folder for core project
```

Ardından, oluşturmak için ihtiyacınız **MyWPFCore.csproj** projesi **MyWPFAppCore** dizin. Bu dosyayı el ile metni kullanarak dilediğiniz düzenleyicisinde oluşturabilirsiniz. Aşağıdaki XML yapıştırın:

```xml
<Project Sdk="Microsoft.NET.Sdk.WindowsDesktop">

  <PropertyGroup>
    <OutputType>WinExe</OutputType>
    <TargetFramework>netcoreapp3.0</TargetFramework>
    <UseWPF>true</UseWPF>
  </PropertyGroup>

</Project>
```

Proje dosyasını el ile oluşturmak istemiyorsanız, projeyi oluşturmak için Visual Studio veya .NET Core SDK'sını kullanabilirsiniz. Ancak, proje dosyasının dışında proje şablonu tarafından oluşturulan tüm dosyalar silmeniz gerekir. SDK'yı kullanmak için aşağıdaki komutu çalıştırın. **SolutionFolder** dizini:

```cli
dotnet new wpf -o MyWPFAppCore -n MyWPFCore
```

Oluşturduktan sonra **MyWPFCore.csproj**, dizin yapısını aşağıdaki gibi görünmelidir:

```
SolutionFolder
├───MyApps.sln
├───MyWPFApp
│   └───MyWPF.csproj
└───MyWPFAppCore
    └───MyWPFCore.csproj
```

Eklemek istediğiniz **MyWPFCore.csproj** için proje **MyApps.sln** Visual Studio veya .NET Core CLI üzerinden **SolutionFolder** dizini:

```cli
dotnet sln add .\MyWPFAppCore\MyWPFCore.csproj
```

## <a name="fix-assembly-info-generation"></a>Düzeltme derleme bilgileri oluşturma

.NET Framework ile oluşturulan Windows Presentation Foundation projeleri içeren bir `AssemblyInfo.cs` oluşturulacak derlemenin sürümü gibi derleme özniteliklerinin içeren dosya. SDK stili projeleri, bu bilgileri size SDK proje dosyasını temel alarak otomatik olarak oluşturur. Her iki "bütünleştirilmiş kod bilgileri" türüne sahip olan bir çakışma oluşturur. Mevcut kullanmak için projeyi otomatik oluşturma devre dışı bırakarak bu sorunu gidermek `AssemblyInfo.cs` dosya.

Ana eklemek için üç seçenek vardır `<PropertyGroup>` düğümü. 

- **GenerateAssemblyInfo**\
Bu özelliği ayarlandığında `false`, derleme öznitelikleri üretmeyeceğini. Bu mevcut çakışmayı önler `AssemblyInfo.cs` .NET Framework proje dosyası.

- **AssemblyName**\
Bu özellik, derlerken oluşturulan çıktıyı ikili değerdir. Ad, kendisine eklenmiş bir uzantı gerekli değildir. Örneğin, kullanarak `MyCoreApp` üretir `MyCoreApp.exe`.

- **RootNamespace**\
Projeniz tarafından kullanılan varsayılan ad alanı. Bu, .NET Framework projenin varsayılan ad alanı eşleşmelidir.

Bu üç öğelerine ekleme `<PropertyGroup>` düğümünde `MyWPFCore.csproj` dosyası:

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

## <a name="add-source-code"></a>Kaynak kodu ekleme
Şu anda **MyWPFCore.csproj** herhangi bir kod projesi derleme değil. Varsayılan olarak, .NET Core projeleri otomatik olarak geçerli dizin ve alt dizinleri içinde tüm kaynak kodu içerir. Proje göreli yolu kullanarak .NET Framework projesinin koddan içerecek şekilde yapılandırmanız gerekir. .NET Framework projenizin kullandıysanız **.resx** simgeler için dosyaları ve kaynaklar windows ve denetimler için gereken çok içerir. 

İlk `<ItemGroup>` projenize eklemeniz düğüm içerir **App.xaml** başlangıç yapılandırması ve kaynak dosyası, uygulama kullanır. **App.xaml** dosya de sahip bir eşlik eden **App.xaml.cs** dosyası, ancak otomatik olarak dahil edilecek farklı bir `<ItemGroup>`.

```xml
  <ItemGroup>
    <ApplicationDefinition Include="..\MyWPFApp\App.xaml">
      <Generator>MSBuild:Compile</Generator>
    </ApplicationDefinition>
  </ItemGroup>
```

Ardından, aşağıdaki ekleyin `<ItemGroup>` projenize düğümü. Her deyim alt dizinleri içeren bir dosya glob deseni içerir. Bu proje, herhangi bir ayar dosyaları ve tüm kaynakları kaynak kodunu içerir. **Obj** dizin açıkça hariç.

```xml
  <ItemGroup>
    <Compile Include="..\MyWPFApp\**\*.cs" Exclude="..\MyWPFApp\obj\**" />
    <None Include="..\MyWPFApp\**\*.settings" />
    <EmbeddedResource Include="..\MyWPFApp\**\*.resx" />
  </ItemGroup>
```

Ardından, başka dahil `<ItemGroup>` içeren düğümü bir `<Page>` girişi için her **xaml** , proje dosyasında **App.xaml** dosya. Bunlar tüm windows, sayfalar ve bulunan kaynaklar içeren **xaml** biçimi. Glob deseni burada kullanın ve gereken her dosya için bir giriş ekleyemez ve belirtmek `<Generator>` kullanılır.

```xml
  <ItemGroup>
    <Page Include="..\MyWPFApp\MainWindow.xaml">
      <Generator>MSBuild:Compile</Generator>
    </Page>
  </ItemGroup>
```

## <a name="add-nuget-packages"></a>NuGet paketleri Ekle

.NET Core projesi .NET Framework proje tarafından başvurulan her NuGet paketini ekleyin. 

Büyük olasılıkla .NET Framework WPF uygulamanızı sahip bir **packages.config** projeniz tarafından başvurulan NuGet paketlerinin bir listesini içeren dosya. .NET Core projesine eklemek için hangi NuGet paketlerini belirlemek için bu listeye bakabilirsiniz. Örneğin, .NET Framework projesinin başvuruyorsa `MahApps.Metro` NuGet paketi, Visual Studio ile projeye ekleyin. .NET Core CLI üzerinden sahip paket başvurusu da ekleyebilirsiniz **SolutionFolder** dizini:

```cli
dotnet add .\MyWPFAppCore\MyWPFCore.csproj package MahApps.Metro -v 2.0.0-alpha0262
```

Önceki komutta aşağıdaki NuGet başvuru eklersiniz **MyWPFCore.csproj** proje:

```xml
  <ItemGroup>
    <PackageReference Include="MahApps.Metro" Version="2.0.0-alpha0262" />
  </ItemGroup>
```

## <a name="problems-compiling"></a>Derleme sorunları

Projelerinizi derleme sorunlarla karşılaşırsanız, .NET Framework'de kullanılabilen ancak .NET core'da kullanılamaz olan bazı yalnızca Windows API'leri kullanıyor olabilir. Eklemeyi deneyin [Windows Uyumluluk Paketi] [ compat-pack] NuGet paketini projenize. Bu paket, yalnızca Windows üzerinde çalışır ve yaklaşık 20.000 Windows API'leri, .NET Core ve .NET Standard projelerine ekler.

```cli
dotnet add .\MyWPFAppCore\MyWPFCore.csproj package Microsoft.Windows.Compatibility
```

Önceki komutta aşağıdaki ekler **MyWPFCore.csproj** proje:

```xml
  <ItemGroup>
    <PackageReference Include="Microsoft.Windows.Compatibility" Version="2.0.1" />
  </ItemGroup>
```

## <a name="wpf-designer"></a>WPF Tasarımcısı

Ayrıntılı olarak açıklanan bu makalede, Visual Studio 2019 Önizleme/RC yalnızca WPF Tasarımcısı .NET Framework projelerinde destekler. Yan yana .NET Core projesi oluşturarak, .NET Framework projesinin tasarım formlara kullanırken projeniz .NET Core ile test edebilirsiniz. Çözüm dosyanız .NET Framework ve .NET Core projeleri içerir. Ekleme, formlar ve denetimler .NET Framework projesinde tasarım ve üzerinde dosya glob desenlerinin ekledik .NET Core projeleri için herhangi bir yeni veya değiştirilen dosyaları otomatik olarak .NET Core projelerinde dahil edilir.

Visual Studio 2019 WPF Tasarımcısı destekler. sonra kopyalama/.NET Core proje dosyanızın içeriğini .NET Framework proje dosyasına yapıştırma. Eklenen dosya glob desenlerinin delete `<Source>` ve `<EmbeddedResource>` öğeleri. Uygulamanız tarafından kullanılan herhangi bir proje başvurusu yolları düzeltin. Bu .NET Framework projesi bir .NET Core projesinden etkili bir şekilde yükseltir.
 
## <a name="next-steps"></a>Sonraki adımlar

* Daha fazla bilgi edinin [Windows Uyumluluk Paketi][compat-pack].
* İzleme bir [taşıma video](https://www.youtube.com/watch?v=5MomsgkWkVw&list=PLS__JrkRveTMiWxG-Lv4cBwYfMQ6m2gmt) .NET Core, .NET Framework WPF projesi.

[compat-pack]: windows-compat-pack.md
