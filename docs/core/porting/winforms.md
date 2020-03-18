---
title: Windows Forms uygulamasını .NET Core'a taşıma
description: .NET Framework Windows Forms uygulamasını Windows için .NET Core'a nasıl ileteceklerini öğretir.
author: Thraka
ms.author: adegeo
ms.date: 03/01/2019
ms.openlocfilehash: dbd522851faa0a4fe435199914a034ee230d3455
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "76116031"
---
# <a name="how-to-port-a-windows-forms-desktop-app-to-net-core"></a>Windows Forms masaüstü uygulamasını .NET Core'a taşıma

Bu makalede, Windows Forms tabanlı masaüstü uygulamanızı .NET Framework'den .NET Core 3.0 veya daha sonrasına nasıl çıkarılacanız açıklanmaktadır. .NET Core 3.0 SDK, Windows Forms uygulamaları için destek içerir. Windows Forms hala yalnızca Windows'a yönelik bir çerçevedir ve yalnızca Windows'da çalışır. Bu örnek, projenizi oluşturmak ve yönetmek için .NET Core SDK CLI'yi kullanır.

Bu makalede, geçiş için kullanılan dosya türlerini tanımlamak için çeşitli adlar kullanılır. Projenizi geçirdiğinizde, dosyalarınız farklı adlar verilmiştir, bu nedenle zihinsel olarak bunları aşağıda listelenenler ile eşleşir:

| Dosya | Açıklama |
| ---- | ----------- |
| **MyApps.sln** | Çözüm dosyasının adı. |
| **MyForms.csproj** | .NET Framework Windows Forms projesinin adı bağlantı noktasına. |
| **MyFormsCore.csproj** | Oluşturduğunuz yeni .NET Core projesinin adı. |
| **MyAppCore.exe** | .NET Core Windows Forms uygulaması çalıştırılabilir. |

## <a name="prerequisites"></a>Önkoşullar

- Yapmak istediğiniz herhangi bir tasarımcı çalışması için [Visual Studio 2019.](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019)

  Aşağıdaki Visual Studio iş yüklerini yükleyin:
  - .NET masaüstü geliştirme
  - .NET Core çoklu platform geliştirme

- Çalışan bir Windows Forms projesi, sorunsuz bir şekilde bir çözüm oluşturur ve çalışır.
- C# kodlu bir proje.
- [.NET Core](https://dotnet.microsoft.com/download/dotnet-core) 3.0 veya sonrası.

> [!NOTE]
> **Visual Studio 2017** .NET Core 3.0 projelerini desteklemiyor. **Visual Studio 2019** .NET Core 3.0 projelerini destekler, ancak .NET Core 3.0 Windows Forms projelerinin görsel tasarımcısını henüz desteklemez. Görsel tasarımcıyı kullanmak için, form dosyalarını .NET Core projesiyle paylaşan bir çözümde bir .NET Windows Forms projeniz olması gerekir.

### <a name="consider"></a>Düşünün

Bir .NET Framework Windows Forms uygulamasını taşımanız gerekirken, göz önünde bulundurmanız gereken birkaç şey vardır.

01. Uygulamanızın geçiş için iyi bir aday olup olmadığını kontrol edin.

    Projenizin .NET Core 3.0'a geçirip geçirmeyeceğini belirlemek için [.NET Taşınabilirlik Çözümleyicisini](../../standard/analyzers/portability-analyzer.md) kullanın. Projenizde .NET Core 3.0 ile ilgili sorunlar varsa, çözümleyici bu sorunları belirlemenize yardımcı olur.

01. Windows Formlar'ın farklı bir sürümünü kullanıyorsunuz.

    .NET Core 3.0 Preview 1 yayımlandığında, Windows Forms GitHub'da açık kaynak gitti. .NET Çekirdek Windows Formları için kod .NET Framework Windows Forms codebase bir çatal. Bazı farklılıklar olabilir ve uygulamanız bağlantı noktası olmaz.

01. [Windows Uyumluluk Paketi][compat-pack] geçiş yaptığınızda yardımcı olabilir.

    .NET Framework'de bulunan bazı API'ler .NET Core 3.0'da kullanılamaz. [Windows Uyumluluk Paketi][compat-pack] bu API'lerin çoğunu ekler ve Windows Forms uygulamanızın .NET Core ile uyumlu hale gelmesine yardımcı olabilir.

01. Projeniz tarafından kullanılan NuGet paketlerini güncelleştirin.

    Herhangi bir geçişten önce NuGet paketlerinin en son sürümlerini kullanmak her zaman iyi bir uygulamadır. Uygulamanız herhangi bir NuGet paketine atıfta bulunuyorsa, bunları en son sürüme güncelleştirin. Uygulamanızın başarılı bir şekilde oluşturulmasını sağlayın. Yükseltmeden sonra, paket hataları varsa, paketi kodunuzu bozmayan en son sürüme indirin.

01. Visual Studio 2019 henüz .NET Core 3.0 için Forms Designer desteklemiyor

    Şu anda, Visual Studio'dan Formtasarımcısını kullanmak istiyorsanız varolan .NET Framework Windows Forms proje dosyanızı saklamanız gerekir.

## <a name="create-a-new-sdk-project"></a>Yeni bir SDK projesi oluşturma

Oluşturduğunuz yeni .NET Core 3.0 projesi ,NET Framework projenizden farklı bir dizinde olmalıdır. Her ikisi de aynı dizindeyse, **obj** dizininde oluşturulan dosyalarla çakışmalarla karşılaşabilirsiniz. Bu örnekte, **SolutionFolder** dizininde **MyFormsAppCore** adında bir dizin oluştururuz:

```
SolutionFolder
├───MyApps.sln
├───MyFormsApp
│   └───MyForms.csproj
└───MyFormsAppCore      <--- New folder for core project
```

Sonra, **MyFormsAppCore dizininde MyFormsCore.csproj** projesini oluşturmanız gerekir. **MyFormsAppCore** Bu dosyayı seçtiğiniz metin düzenleyicisini kullanarak el ile oluşturabilirsiniz. Aşağıdaki XML yapıştırın:

```xml
<Project Sdk="Microsoft.NET.Sdk.WindowsDesktop">

  <PropertyGroup>
    <OutputType>WinExe</OutputType>
    <TargetFramework>netcoreapp3.0</TargetFramework>
    <UseWindowsForms>true</UseWindowsForms>
  </PropertyGroup>

</Project>
```

Proje dosyasını el ile oluşturmak istemiyorsanız, projeyi oluşturmak için Visual Studio'yu veya .NET Core SDK'yı kullanabilirsiniz. Ancak, proje dosyası dışında proje şablonu tarafından oluşturulan diğer tüm dosyaları silmeniz gerekir. SDK'yı kullanmak için **SolutionFolder** dizininden aşağıdaki komutu çalıştırın:

```dotnetcli
dotnet new winforms -o MyFormsAppCore -n MyFormsCore
```

**MyFormsCore.csproj**oluşturduktan sonra, dizin yapıaşağıdaki gibi görünmelidir:

```
SolutionFolder
├───MyApps.sln
├───MyFormsApp
│   └───MyForms.csproj
└───MyFormsAppCore
    └───MyFormsCore.csproj
```

**MyFormsCore.csproj** projesini Visual Studio veya **SolutionFolder** dizininden .NET Core CLI ile **MyApps.sln'ye** ekleyin:

```dotnetcli
dotnet sln add .\MyFormsAppCore\MyFormsCore.csproj
```

## <a name="fix-assembly-info-generation"></a>Montaj bilgisi oluşturma düzeltme

.NET Framework ile oluşturulan Windows Forms `AssemblyInfo.cs` projeleri, oluşturulacak derleme sürümü gibi derleme özniteliklerini içeren bir dosya içerir. SDK tarzı projeler, SDK proje dosyasına göre bu bilgileri sizin için otomatik olarak oluşturur. Her iki türde "derleme bilgisi" olması bir çakışma oluşturur. Projeyi varolan `AssemblyInfo.cs` dosyanızı kullanmaya zorlayan otomatik oluşturmayı devre dışı bırakarak bu sorunu giderin.

Ana `<PropertyGroup>` düğüme eklenecek üç ayar vardır.

- **AssemblyInfo oluşturma**\
Bu özelliği `false`ayarladiğinizde, derleme öznitelikleri oluşturmaz. Bu, .NET Framework `AssemblyInfo.cs` projesindeki varolan dosyayla çakışmayı önler.

- **Assemblyname**\
Bu özelliğin değeri, derlediğinizde oluşturulan çıktı ikilisidir. Adın ekbir uzantıya ihtiyacı yoktur. Örneğin, üretir `MyCoreApp` `MyCoreApp.exe`kullanarak .

- **RootNamespace**\
Projeniz tarafından kullanılan varsayılan ad alanı. Bu, .NET Framework projesinin varsayılan ad alanıyla eşleşmelidir.

Bu üç öğeyi `<PropertyGroup>` dosyadaki düğüme ekleyin: `MyFormsCore.csproj`

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

Şu anda, **MyFormsCore.csproj** proje herhangi bir kod derlemek değildir. Varsayılan olarak, .NET Core projeleri otomatik olarak geçerli dizindeki tüm kaynak kodunu ve alt dizini içerir. Projeyi,.NET Framework projesinden kod içerecek şekilde göreceli bir yol kullanarak yapılandırmanız gerekir. .NET Framework projenizde formlarınız için simgeler ve kaynaklar için **.resx** dosyaları kullanıldıysa, bunları da eklemeniz gerekir.

Projenize `<ItemGroup>` aşağıdaki düğümü ekleyin. Her deyim, alt dizinleri içeren bir dosya glob deseni içerir.

```xml
  <ItemGroup>
    <Compile Include="..\MyFormsApp\**\*.cs" />
    <EmbeddedResource Include="..\MyFormsApp\**\*.resx" />
  </ItemGroup>
```

Alternatif olarak, .NET `<Compile>` `<EmbeddedResource>` Framework projenizdeki her dosya için bir veya giriş oluşturabilirsiniz.

## <a name="add-nuget-packages"></a>NuGet paketlerini ekleme

.NET Framework projesi tarafından başvurulan her NuGet paketini .NET Core projesine ekleyin.

Büyük olasılıkla .NET Framework Windows Forms uygulamanızda, projeniz tarafından başvurulan tüm NuGet paketlerinin listesini içeren bir **packages.config** dosyası vardır. .NET Core projesine hangi NuGet paketlerinin ekleyeceğini belirlemek için bu listeye bakabilirsiniz. Örneğin, .NET Framework projesi `MetroFramework`,, `MetroFramework.Design`ve `MetroFramework.Fonts` NuGet paketlerine atıfta bulunduysa, **solutionFolder** dizininden Visual Studio veya .NET Core CLI ile projeye her birini ekleyin:

```dotnetcli
dotnet add .\MyFormsAppCore\MyFormsCore.csproj package MetroFramework
dotnet add .\MyFormsAppCore\MyFormsCore.csproj package MetroFramework.Design
dotnet add .\MyFormsAppCore\MyFormsCore.csproj package MetroFramework.Fonts
```

Önceki komutlar **MyFormsCore.csproj** projesine aşağıdaki NuGet referansları ekler:

```xml
  <ItemGroup>
    <PackageReference Include="MetroFramework" Version="1.2.0.3" />
    <PackageReference Include="MetroFramework.Design" Version="1.2.0.3" />
    <PackageReference Include="MetroFramework.Fonts" Version="1.2.0.3" />
  </ItemGroup>
```

## <a name="port-control-libraries"></a>Bağlantı noktası kontrol kitaplıkları

Bağlantı noktasına giden bir Windows Forms Controls kitaplığınız varsa, yol tarifleri birkaç ayar dışında bir .NET Framework Windows Forms uygulama projesini taşımayla aynıdır. Ve yürütülebilir bir derleme yerine, bir kitaplık için derlemek. Yürütülebilir proje ile kitaplık projesi arasındaki fark, kaynak kodunuzu içeren dosya globs yollarının yanı sıra en az düzeydedir.

Önceki adımın örneğini kullanarak, hangi projelerle çalıştığımızı ve dosyaları genişletmemizi sağlar.

| Dosya | Açıklama |
| ---- | ----------- |
| **MyApps.sln** | Çözüm dosyasının adı. |
| **MyControls.csproj** | .NET Framework Windows Forms Controls projesinin adı bağlantı noktasına. |
| **MyControlsCore.csproj** | Oluşturduğunuz yeni .NET Core kitaplık projesinin adı. |
| **MyCoreControls.dll** | .NET Core Windows Forms Denetimleri kitaplığı. |

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

`MyControlsCore.csproj` Proje ile daha önce oluşturulmuş `MyFormsCore.csproj` proje arasındaki farkları göz önünde bulundurun.

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

Aşağıda ,.NET Core Windows Forms Controls kitaplık proje dosyasının nasıl görüneceğine bir örnek verilmiştir:

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

Gördüğünüz gibi, `<OutputType>` düğüm kaldırıldı ve bu da derleyicinin yürütülebilir yerine kitaplık oluşturması için varsayılan olarak varsayılan olarak. Ve `<AssemblyName>` `<RootNamespace>` değiştirildi. Özellikle `<RootNamespace>` taşıma yaptığınız Windows Forms Denetimleri kitaplığı ad alanı yla eşleşmelidir. Ve son `<Compile>` olarak, düğümler, `<EmbeddedResource>` taşıma yaptığınız Windows Forms Denetimleri kitaplığı klasörüne işaret edecek şekilde ayarlandı.

Ardından, ana .NET Core **MyFormsCore.csproj** projesinde, yeni .NET Core Windows Formlar Kontrol kitaplığına bir başvuru ekleyin. **SolutionFolder** dizininden Visual Studio veya .NET Core CLI ile bir başvuru ekleyin:

```dotnetcli
dotnet add .\MyFormsAppCore\MyFormsCore.csproj reference .\MyFormsControlsCore\MyControlsCore.csproj
```

Önceki komut **MyFormsCore.csproj** projesine aşağıdakileri ekler:

```xml
  <ItemGroup>
    <ProjectReference Include="..\MyFormsControlsCore\MyControlsCore.csproj" />
  </ItemGroup>
```

## <a name="compilation-problems"></a>Derleme sorunları

Projelerinizi derlemede sorun yaşıyorsanız, .NET Framework'de kullanılabilen ancak .NET Core'da bulunmayan yalnızca Windows'a özel API'ler kullanıyor olabilirsiniz. Projenize Windows [Uyumluluk Paketi][compat-pack] NuGet paketini eklemeyi deneyebilirsiniz. Bu paket yalnızca Windows'da çalışır ve .NET Core ve .NET Standard projelerine yaklaşık 20.000 Windows API'si ekler.

```dotnetcli
dotnet add .\MyFormsAppCore\MyFormsCore.csproj package Microsoft.Windows.Compatibility
```

Önceki komut **MyFormsCore.csproj** projesine aşağıdakileri ekler:

```xml
  <ItemGroup>
    <PackageReference Include="Microsoft.Windows.Compatibility" Version="3.1.0" />
  </ItemGroup>
```

## <a name="windows-forms-designer"></a>Windows Form Tasarımcısı

Bu makalede ayrıntılı olarak belirtildiği gibi Visual Studio 2019 sadece .NET Framework projelerinde Form Tasarımcısı'nı destekler. Yan yana .NET Core projesi oluşturarak, formları tasarlamak için .NET Framework projesini kullanırken projenizi .NET Core ile test edebilirsiniz. Çözüm dosyanız hem .NET Framework hem de .NET Core projelerini içerir. .NET Framework projesinde formlarınızı ve kontrollerinizi ekleyin ve tasarlayın ve .NET Core projelerine eklediğimiz dosya glob desenlerine göre, yeni veya değiştirilen dosyalar otomatik olarak .NET Core projelerine dahil edilir.

Visual Studio 2019 Windows Forms Designer'ı destekledikten sonra .NET Core proje dosyanızın içeriğini .NET Framework proje dosyasına kopyalayabilir/yapıştırabilirsiniz. Sonra dosya glob desenleri `<Source>` ve `<EmbeddedResource>` öğeleri ile ekledi silin. Uygulamanız tarafından kullanılan herhangi bir proje başvurusuna giden yolları düzeltin. Bu, .NET Framework projesini bir .NET Core projesine etkin bir şekilde yükseltir.

## <a name="next-steps"></a>Sonraki adımlar

- [.NET Framework'den .NET Core'a değişiklik kırma](../compatibility/fx-core.md)hakkında bilgi edinin.
- Windows Uyumluluk [Paketi][compat-pack]hakkında daha fazla bilgi edinin.
- .NET Framework Windows Forms projenizi .NET Core'a [taşıma yla ilgili](https://www.youtube.com/watch?v=upVQEUc_KwU) bir video izleyin.

[compat-pack]: windows-compat-pack.md
