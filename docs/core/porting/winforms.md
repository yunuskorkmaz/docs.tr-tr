---
title: Bağlantı noktası bir Windows Forms uygulaması .NET Core 3.0
description: Windows için .NET Core 3.0 bir .NET Framework Windows Forms uygulamasına bağlantı noktasına öğretir.
author: Thraka
ms.author: adegeo
ms.date: 03/01/2019
ms.custom: ''
ms.openlocfilehash: 0f45c053311885c779d394a97f5845119e2b5c82
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59186160"
---
# <a name="how-to-port-a-windows-forms-desktop-app-to-net-core"></a>Nasıl yapılır: .NET Core için bir Windows Forms masaüstü uygulaması bağlantı noktası

Bu makalede, Windows Forms tabanlı masaüstü uygulamanızın .NET Framework .NET Core 3.0 için bağlantı noktası açıklar. .NET Core SDK 3.0, Windows Forms uygulamaları için destek içerir. Windows Formları yalnızca Windows framework hala geçerli olduğunu ve yalnızca Windows üzerinde çalışır. Bu örnek, oluşturmak ve projenize yönetmek için .NET Core SDK'sı CLI'yı kullanır.

Bu makalede, çeşitli adlar, geçiş için kullanılan dosya türlerini tanımlamak için kullanılır. Projenizi geçirirken, dosyalarınızı farklı şekilde adlandırılmış, bu nedenle akıl aşağıda listelenen olanlarla eşleşmesi:

| Dosya | Açıklama |
| ---- | ----------- |
| **MyApps.sln** | Çözüm dosyasının adı. |
| **MyForms.csproj** | Bağlantı noktası için .NET Framework Windows Forms projesinin adı. |
| **MyFormsCore.csproj** | Oluşturduğunuz yeni .NET Core projesinin adı. |
| **MyAppCore.exe** | .NET Core Windows Forms uygulaması çalıştırılabilir. |

## <a name="prerequisites"></a>Önkoşullar

- [Visual Studio 2019](https://visualstudio.microsoft.com/vs/preview/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=winforms+core) yapmak istediğiniz herhangi bir tasarımcı iş için.

  Aşağıdaki Visual Studio iş yüklerini yükleyin:
  - .NET masaüstü geliştirme
  - .NET platformlar arası geliştirme

- Çalışan bir Windows Forms projesi oluşturan ve sorun çalışır bir çözümde.
- İçinde projenizin kodlanmasını C#. 
- Son yükleme [.NET Core 3.0](https://aka.ms/netcore3download) Önizleme.

>[!NOTE]
>**Visual Studio 2017** .NET Core 3.0 projeleri desteklemiyor. **Visual Studio 2019 Önizleme/RC** .NET Core 3.0 projeleri destekler ancak görsel tasarımcı için .NET Core 3.0, Windows Forms projeleri henüz desteklememektedir. Görsel tasarımcıyı kullanmak için çözümünüzdeki forms dosyaları ile .NET Core projesi paylaşan bir .NET Windows Forms projesi olması gerekir.

### <a name="consider"></a>Göz önünde bulundurun

Bir .NET Framework Windows Forms uygulaması taşırken dikkate almanız gereken birkaç nokta vardır.

01. Uygulamanızı geçişi için iyi bir aday olduğundan emin olun.

    Kullanım [.NET Portability Analyzer](../../standard/analyzers/portability-analyzer.md) projeniz için .NET Core 3.0 geçirirseniz belirlemek için. Projeniz .NET Core 3.0 ile ilgili sorunlar varsa, Çözümleyicisi bu sorunları belirlemenize yardımcı olur.

01. Windows Forms farklı bir sürümünü kullanıyorsunuz.

    .NET Core 3.0 Önizleme 1 yayımlandığında, Windows Forms, açık kaynaklı oluştu. GitHub üzerinde. .NET Core Windows formları için .NET Framework Windows Forms kod tabanı deponun bir çatalını kodudur. Bu, bazı farklılıklar mevcuttur ve uygulamanızı bağlantı noktası olmaz mümkündür.

01. [Windows Uyumluluk Paketi] [ compat-pack] geçirmenize yardımcı olabilir.

    .NET Framework'te bulunan bazı API'leri, .NET Core 3. 0'kullanılamaz. [Windows Uyumluluk Paketi] [ compat-pack] bu API'lerin birçoğu ekler ve .NET Core ile uyumlu hale Windows Form uygulamanıza yardımcı olabilir.

01. Projeniz tarafından kullanılan NuGet paketlerini güncelleştirin.

    Tüm geçiş işleminden önce NuGet paketlerini en son sürümlerini kullanmak için her zaman iyi bir uygulamadır. Uygulamanızı herhangi bir NuGet paketinin başvuruyorsa, bunları en son sürüme güncelleştirin. Uygulamanız başarıyla derlendiğinden emin olun. Herhangi bir paket hata varsa, yükselttikten sonra paketi kodunuzu kesmeyecektir en son sürüme düşürme.

01. Visual Studio 2019 Önizleme/RC için .NET Core 3.0 Form Tasarımcısı henüz desteklemiyor

    Şu anda, Visual Studio'da Forms Tasarımcısı'nı kullanmak istiyorsanız, var olan .NET Framework Windows Forms projesi dosyanızı çalışır durumda bulundurmanıza gerek.

## <a name="create-a-new-sdk-project"></a>Yeni SDK projesi oluşturma

Oluşturduğunuz yeni .NET Core 3.0 proje .NET Framework projenizden farklı bir dizinde olması gerekir. Her ikisi de aynı dizinde iseler, içinde oluşturulan dosyalar ile çakışma çalışabilir **obj** dizin. Bu örnekte, adlı bir dizin oluşturacağız **MyFormsAppCore** içinde **SolutionFolder** dizini:

```
SolutionFolder
├───MyApps.sln
├───MyFormsApp
│   └───MyForms.csproj
└───MyFormsAppCore      <--- New folder for core project
```

Ardından, oluşturmak için ihtiyacınız **MyFormsCore.csproj** projesi **MyFormsAppCore** dizin. Bu dosyayı el ile metni kullanarak dilediğiniz düzenleyicisinde oluşturabilirsiniz. Aşağıdaki XML yapıştırın:

```xml
<Project Sdk="Microsoft.NET.Sdk.WindowsDesktop">

  <PropertyGroup>
    <OutputType>WinExe</OutputType>
    <TargetFramework>netcoreapp3.0</TargetFramework>
    <UseWindowsForms>true</UseWindowsForms>
  </PropertyGroup>

</Project>
```

Proje dosyasını el ile oluşturmak istemiyorsanız, projeyi oluşturmak için Visual Studio veya .NET Core SDK'sını kullanabilirsiniz. Ancak, proje dosyasının dışında proje şablonu tarafından oluşturulan tüm dosyalar silmeniz gerekir. SDK'yı kullanmak için aşağıdaki komutu çalıştırın. **SolutionFolder** dizini:

```cli
dotnet new winforms -o MyFormsAppCore -n MyFormsCore
```

Oluşturduktan sonra **MyFormsCore.csproj**, dizin yapısını aşağıdaki gibi görünmelidir:

```
SolutionFolder
├───MyApps.sln
├───MyFormsApp
│   └───MyForms.csproj
└───MyFormsAppCore
    └───MyFormsCore.csproj
```

Eklemek istediğiniz **MyFormsCore.csproj** için proje **MyApps.sln** Visual Studio veya .NET Core CLI üzerinden **SolutionFolder** dizini:

```cli
dotnet sln add .\MyFormsAppCore\MyFormsCore.csproj
```

## <a name="fix-assembly-info-generation"></a>Düzeltme derleme bilgileri oluşturma

.NET Framework ile oluşturulan Windows Forms projeleri içeren bir `AssemblyInfo.cs` oluşturulacak derlemenin sürümü gibi derleme özniteliklerinin içeren dosya. SDK stili projeleri, bu bilgileri size SDK proje dosyasını temel alarak otomatik olarak oluşturur. Her iki "bütünleştirilmiş kod bilgileri" türüne sahip olan bir çakışma oluşturur. Mevcut kullanmak için projeyi otomatik oluşturma devre dışı bırakarak bu sorunu gidermek `AssemblyInfo.cs` dosya.

Ana eklemek için üç seçenek vardır `<PropertyGroup>` düğümü. 

- **GenerateAssemblyInfo**\
Bu özelliği ayarlandığında `false`, derleme öznitelikleri üretmeyeceğini. Bu mevcut çakışmayı önler `AssemblyInfo.cs` .NET Framework proje dosyası.

- **AssemblyName**\
Bu özellik, derlerken oluşturulan çıktıyı ikili değerdir. Ad, kendisine eklenmiş bir uzantı gerekli değildir. Örneğin, kullanarak `MyCoreApp` üretir `MyCoreApp.exe`.

- **RootNamespace**\
Projeniz tarafından kullanılan varsayılan ad alanı. Bu, .NET Framework projenin varsayılan ad alanı eşleşmelidir.

Bu üç öğelerine ekleme `<PropertyGroup>` düğümünde `MyFormsCore.csproj` dosyası:

```xml
<Project Sdk="Microsoft.NET.Sdk.WindowsDesktop">

  <PropertyGroup>
    <OutputType>WinExe</OutputType>
    <TargetFramework>netcoreapp3.0</TargetFramework>
    <UseWindowsForms>true</UseWindowsForms>

    <GenerateAssemblyInfo>false</GenerateAssemblyInfo>
    <AssemblyName>MyCoreApp</AssemblyName>
    <RootNamespace>WindowsFormsApp1</RootNamespace>
  </PropertyGroup>

</Project>
```

## <a name="add-source-code"></a>Kaynak kodu ekleme

Şu anda **MyFormsCore.csproj** herhangi bir kod projesi derleme değil. Varsayılan olarak, .NET Core projeleri otomatik olarak geçerli dizin ve alt dizinleri içinde tüm kaynak kodu içerir. Proje göreli yolu kullanarak .NET Framework projesinin koddan içerecek şekilde yapılandırmanız gerekir. .NET Framework projenizin kullandıysanız **.resx** simgeler için dosyaları ve kaynaklar formlarınızı için gereken çok içerir. 

Aşağıdaki `<ItemGroup>` projenize düğümü. Her deyim alt dizinleri içeren bir dosya glob deseni içerir.

```xml
  <ItemGroup>
    <Compile Include="..\MyFormsApp\**\*.cs" />
    <EmbeddedResource Include="..\MyFormsApp\**\*.resx" />
  </ItemGroup>
```

Alternatif olarak, oluşturabileceğiniz bir `<Compile>` veya `<EmbeddedResource>` zaman.NET Framework projenizin her dosya için giriş.

## <a name="add-nuget-packages"></a>NuGet paketleri Ekle

.NET Core projesi .NET Framework proje tarafından başvurulan her NuGet paketini ekleyin. 

Büyük olasılıkla, .NET Framework Windows Forms uygulaması olan bir **packages.config** projeniz tarafından başvurulan NuGet paketlerinin bir listesini içeren dosya. .NET Core projesine eklemek için hangi NuGet paketlerini belirlemek için bu listeye bakabilirsiniz. Örneğin, .NET Framework projesinin başvurulan `MetroFramework`, `MetroFramework.Design`, ve `MetroFramework.Fonts` NuGet paketleri Ekle her projeye sahip Visual Studio veya .NET Core CLI üzerinden **SolutionFolder** dizini :

```cli
dotnet add .\MyFormsAppCore\MyFormsCore.csproj package MetroFramework
dotnet add .\MyFormsAppCore\MyFormsCore.csproj package MetroFramework.Design
dotnet add .\MyFormsAppCore\MyFormsCore.csproj package MetroFramework.Fonts
```

Yukarıdaki komutları aşağıdaki NuGet başvuruları eklersiniz **MyFormsCore.csproj** proje:

```xml
  <ItemGroup>
    <PackageReference Include="MetroFramework" Version="1.2.0.3" />
    <PackageReference Include="MetroFramework.Design" Version="1.2.0.3" />
    <PackageReference Include="MetroFramework.Fonts" Version="1.2.0.3" />
  </ItemGroup>
```

## <a name="port-control-libraries"></a>Bağlantı noktası denetimi kitaplıkları

Bağlantı noktası için bir Windows Forms Denetim Kitaplığı projesi varsa, yönergeleri birkaç ayarı dışında bir .NET Framework Windows Forms uygulaması projesi taşıma ile aynı olur. Ve bir yürütülebilir dosya için derleme yerine, bir kitaplık için derleyin. Yürütülebilir projeyi, kaynak kodunuzu içeren dosyayı eğik çizgi genelleştirmeler yolları yanı sıra kitaplık projesi arasındaki fark, en alt düzeydedir.

Önceki adım örneği kullanarak, hangi projeleri ve dosyaları ile çalışıyoruz genişletin olanak tanır.

| Dosya | Açıklama |
| ---- | ----------- |
| **MyApps.sln** | Çözüm dosyasının adı. |
| **MyControls.csproj** | Bağlantı noktası için .NET Framework Windows Forms denetimleri projesinin adı. |
| **MyControlsCore.csproj** | Oluşturduğunuz yeni .NET Core kitaplığı proje adı. |
| **MyCoreControls.dll** | .NET Core Windows Forms Denetim Kitaplığı. |

```
SolutionFolder
├───MyApps.sln
├───MyFormsApp
│   └───MyForms.csproj
├───MyFormsAppCore
│   └───MyFormsCore.csproj
│
├───MyFormsControls
│   └───MyControls.csproj
└───MyFormsControlsCore
    └───MyControlsCore.csproj   <--- New project for core controls
```

Arasındaki farklılıkları dikkate `MyControlsCore.csproj` proje ve önceden oluşturulmuş `MyFormsCore.csproj` proje.

```diff
 <Project Sdk="Microsoft.NET.Sdk.WindowsDesktop">

   <PropertyGroup>
-    <OutputType>WinExe</OutputType>
     <TargetFramework>netcoreapp3.0</TargetFramework>
     <UseWindowsForms>true</UseWindowsForms>

     <GenerateAssemblyInfo>false</GenerateAssemblyInfo>
-    <AssemblyName>MyCoreApp</AssemblyName>
-    <RootNamespace>WindowsFormsApp1</RootNamespace>
+    <AssemblyName>MyControlsCore</AssemblyName>
+    <RootNamespace>WindowsFormsControlLibrary1</RootNamespace>
   </PropertyGroup>

   <ItemGroup>
-    <Compile Include="..\MyFormsApp\**\*.cs" />
-    <EmbeddedResource Include="..\MyFormsApp\**\*.resx" />
+    <Compile Include="..\MyFormsControls\**\*.cs" />
+    <EmbeddedResource Include="..\MyFormsControls\**\*.resx" />
   </ItemGroup>

 </Project>
```

.NET Core Windows Forms Denetim Kitaplığı proje dosyası aşağıdaki gibi görünür bir örnek aşağıda verilmiştir:

```xml
<Project Sdk="Microsoft.NET.Sdk.WindowsDesktop">

  <PropertyGroup>
    
    <TargetFramework>netcoreapp3.0</TargetFramework>
    <UseWindowsForms>true</UseWindowsForms>

    <GenerateAssemblyInfo>false</GenerateAssemblyInfo>
    <AssemblyName>MyCoreControls</AssemblyName>
    <RootNamespace>WindowsFormsControlLibrary1</RootNamespace>
  </PropertyGroup>
  
  <ItemGroup>
    <Compile Include="..\MyFormsControls\**\*.cs" />
    <EmbeddedResource Include="..\MyFormsControls\**\*.resx" />
  </ItemGroup>
  
</Project>
```

Gördüğünüz gibi `<OutputType>` düğüm kaldırıldı, bunun yerine bir yürütülebilir dosya bir kitaplığı oluşturmak için derleyicinin varsayılan. `<AssemblyName>` Ve `<RootNamespace>` değiştirildi. Özellikle `<RootNamespace>` taşıma Windows Forms denetimleri kitaplığının ad alanı ile eşleşmelidir. Son olarak, `<Compile>` ve `<EmbeddedResource>` düğümleri taşıma Windows Forms denetimleri Kitaplık klasörüne işaret edecek şekilde ayarlanır.

Sonra ana .NET core'da **MyFormsCore.csproj** projeye yeni .NET Core Windows Forms Denetim Kitaplığı için başvuru ekleyin. Visual Studio veya .NET Core CLI ile bir başvuru ekleyin **SolutionFolder** dizini:

```cli
dotnet add .\MyFormsAppCore\MyFormsCore.csproj reference .\MyFormsControlsCore\MyControlsCore.csproj
```

Önceki komutta aşağıdaki ekler **MyFormsCore.csproj** proje:

```xml
  <ItemGroup>
    <ProjectReference Include="..\MyFormsControlsCore\MyControlsCore.csproj" />
  </ItemGroup>
```

## <a name="problems-compiling"></a>Derleme sorunları

Projelerinizi derleme sorunlarla karşılaşırsanız, .NET Framework'de kullanılabilen ancak .NET core'da kullanılamaz olan bazı yalnızca Windows API'leri kullanıyor olabilir. Eklemeyi deneyin [Windows Uyumluluk Paketi] [ compat-pack] NuGet paketini projenize. Bu paket, yalnızca Windows üzerinde çalışır ve yaklaşık 20.000 Windows API'leri, .NET Core ve .NET Standard projelerine ekler.

```cli
dotnet add .\MyFormsAppCore\MyFormsCore.csproj package Microsoft.Windows.Compatibility
```

Önceki komutta aşağıdaki ekler **MyFormsCore.csproj** proje:

```xml
  <ItemGroup>
    <PackageReference Include="Microsoft.Windows.Compatibility" Version="2.0.1" />
  </ItemGroup>
```

## <a name="windows-forms-designer"></a>Windows Form Tasarımcısı

Ayrıntılı olarak açıklanan bu makalede, Visual Studio 2019 Önizleme/RC yalnızca Form Tasarımcısı .NET Framework projelerinde destekler. Yan yana .NET Core projesi oluşturarak, .NET Framework projesinin tasarım formlara kullanırken projeniz .NET Core ile test edebilirsiniz. Çözüm dosyanız .NET Framework ve .NET Core projeleri içerir. Ekleme, formlar ve denetimler .NET Framework projesinde tasarım ve üzerinde dosya glob desenlerinin ekledik .NET Core projeleri için herhangi bir yeni veya değiştirilen dosyaları otomatik olarak .NET Core projelerinde dahil edilir.

Visual Studio 2019 Windows Form Tasarımcısı'nı destekler. sonra kopyalama/.NET Core proje dosyanızın içeriğini .NET Framework proje dosyasına yapıştırma. Eklenen dosya glob desenlerinin delete `<Source>` ve `<EmbeddedResource>` öğeleri. Uygulamanız tarafından kullanılan herhangi bir proje başvurusu yolları düzeltin. Bu .NET Framework projesi bir .NET Core projesinden etkili bir şekilde yükseltir.
 
## <a name="next-steps"></a>Sonraki adımlar

* Daha fazla bilgi edinin [Windows Uyumluluk Paketi][compat-pack].
* İzleme bir [taşıma video](https://www.youtube.com/watch?v=upVQEUc_KwU) .NET Core, .NET Framework Windows Forms projesi.

[compat-pack]: windows-compat-pack.md
