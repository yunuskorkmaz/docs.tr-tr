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
# <a name="how-to-port-a-windows-forms-desktop-app-to-net-core"></a><span data-ttu-id="7aef0-103">Windows Forms masaüstü uygulamasını .NET Core'a taşıma</span><span class="sxs-lookup"><span data-stu-id="7aef0-103">How to port a Windows Forms desktop app to .NET Core</span></span>

<span data-ttu-id="7aef0-104">Bu makalede, Windows Forms tabanlı masaüstü uygulamanızı .NET Framework'den .NET Core 3.0 veya daha sonrasına nasıl çıkarılacanız açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="7aef0-104">This article describes how to port your Windows Forms-based desktop app from .NET Framework to .NET Core 3.0 or later.</span></span> <span data-ttu-id="7aef0-105">.NET Core 3.0 SDK, Windows Forms uygulamaları için destek içerir.</span><span class="sxs-lookup"><span data-stu-id="7aef0-105">The .NET Core 3.0 SDK includes support for Windows Forms applications.</span></span> <span data-ttu-id="7aef0-106">Windows Forms hala yalnızca Windows'a yönelik bir çerçevedir ve yalnızca Windows'da çalışır.</span><span class="sxs-lookup"><span data-stu-id="7aef0-106">Windows Forms is still a Windows-only framework and only runs on Windows.</span></span> <span data-ttu-id="7aef0-107">Bu örnek, projenizi oluşturmak ve yönetmek için .NET Core SDK CLI'yi kullanır.</span><span class="sxs-lookup"><span data-stu-id="7aef0-107">This example uses the .NET Core SDK CLI to create and manage your project.</span></span>

<span data-ttu-id="7aef0-108">Bu makalede, geçiş için kullanılan dosya türlerini tanımlamak için çeşitli adlar kullanılır.</span><span class="sxs-lookup"><span data-stu-id="7aef0-108">In this article, various names are used to identify types of files used for migration.</span></span> <span data-ttu-id="7aef0-109">Projenizi geçirdiğinizde, dosyalarınız farklı adlar verilmiştir, bu nedenle zihinsel olarak bunları aşağıda listelenenler ile eşleşir:</span><span class="sxs-lookup"><span data-stu-id="7aef0-109">When migrating your project, your files will be named differently, so mentally match them to the ones listed below:</span></span>

| <span data-ttu-id="7aef0-110">Dosya</span><span class="sxs-lookup"><span data-stu-id="7aef0-110">File</span></span> | <span data-ttu-id="7aef0-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7aef0-111">Description</span></span> |
| ---- | ----------- |
| <span data-ttu-id="7aef0-112">**MyApps.sln**</span><span class="sxs-lookup"><span data-stu-id="7aef0-112">**MyApps.sln**</span></span> | <span data-ttu-id="7aef0-113">Çözüm dosyasının adı.</span><span class="sxs-lookup"><span data-stu-id="7aef0-113">The name of the solution file.</span></span> |
| <span data-ttu-id="7aef0-114">**MyForms.csproj**</span><span class="sxs-lookup"><span data-stu-id="7aef0-114">**MyForms.csproj**</span></span> | <span data-ttu-id="7aef0-115">.NET Framework Windows Forms projesinin adı bağlantı noktasına.</span><span class="sxs-lookup"><span data-stu-id="7aef0-115">The name of the .NET Framework Windows Forms project to port.</span></span> |
| <span data-ttu-id="7aef0-116">**MyFormsCore.csproj**</span><span class="sxs-lookup"><span data-stu-id="7aef0-116">**MyFormsCore.csproj**</span></span> | <span data-ttu-id="7aef0-117">Oluşturduğunuz yeni .NET Core projesinin adı.</span><span class="sxs-lookup"><span data-stu-id="7aef0-117">The name of the new .NET Core project you create.</span></span> |
| <span data-ttu-id="7aef0-118">**MyAppCore.exe**</span><span class="sxs-lookup"><span data-stu-id="7aef0-118">**MyAppCore.exe**</span></span> | <span data-ttu-id="7aef0-119">.NET Core Windows Forms uygulaması çalıştırılabilir.</span><span class="sxs-lookup"><span data-stu-id="7aef0-119">The .NET Core Windows Forms app executable.</span></span> |

## <a name="prerequisites"></a><span data-ttu-id="7aef0-120">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="7aef0-120">Prerequisites</span></span>

- <span data-ttu-id="7aef0-121">Yapmak istediğiniz herhangi bir tasarımcı çalışması için [Visual Studio 2019.](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019)</span><span class="sxs-lookup"><span data-stu-id="7aef0-121">[Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) for any designer work you want to do.</span></span>

  <span data-ttu-id="7aef0-122">Aşağıdaki Visual Studio iş yüklerini yükleyin:</span><span class="sxs-lookup"><span data-stu-id="7aef0-122">Install the following Visual Studio workloads:</span></span>
  - <span data-ttu-id="7aef0-123">.NET masaüstü geliştirme</span><span class="sxs-lookup"><span data-stu-id="7aef0-123">.NET desktop development</span></span>
  - <span data-ttu-id="7aef0-124">.NET Core çoklu platform geliştirme</span><span class="sxs-lookup"><span data-stu-id="7aef0-124">.NET Core cross-platform development</span></span>

- <span data-ttu-id="7aef0-125">Çalışan bir Windows Forms projesi, sorunsuz bir şekilde bir çözüm oluşturur ve çalışır.</span><span class="sxs-lookup"><span data-stu-id="7aef0-125">A working Windows Forms project in a solution that builds and runs without issue.</span></span>
- <span data-ttu-id="7aef0-126">C# kodlu bir proje.</span><span class="sxs-lookup"><span data-stu-id="7aef0-126">A project coded in C#.</span></span>
- <span data-ttu-id="7aef0-127">[.NET Core](https://dotnet.microsoft.com/download/dotnet-core) 3.0 veya sonrası.</span><span class="sxs-lookup"><span data-stu-id="7aef0-127">[.NET Core](https://dotnet.microsoft.com/download/dotnet-core) 3.0 or later.</span></span>

> [!NOTE]
> <span data-ttu-id="7aef0-128">**Visual Studio 2017** .NET Core 3.0 projelerini desteklemiyor.</span><span class="sxs-lookup"><span data-stu-id="7aef0-128">**Visual Studio 2017** doesn't support .NET Core 3.0 projects.</span></span> <span data-ttu-id="7aef0-129">**Visual Studio 2019** .NET Core 3.0 projelerini destekler, ancak .NET Core 3.0 Windows Forms projelerinin görsel tasarımcısını henüz desteklemez.</span><span class="sxs-lookup"><span data-stu-id="7aef0-129">**Visual Studio 2019** supports .NET Core 3.0 projects but doesn't yet support the visual designer for .NET Core 3.0 Windows Forms projects.</span></span> <span data-ttu-id="7aef0-130">Görsel tasarımcıyı kullanmak için, form dosyalarını .NET Core projesiyle paylaşan bir çözümde bir .NET Windows Forms projeniz olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="7aef0-130">To use the visual designer, you must have a .NET Windows Forms project in a solution that shares the forms files with the .NET Core project.</span></span>

### <a name="consider"></a><span data-ttu-id="7aef0-131">Düşünün</span><span class="sxs-lookup"><span data-stu-id="7aef0-131">Consider</span></span>

<span data-ttu-id="7aef0-132">Bir .NET Framework Windows Forms uygulamasını taşımanız gerekirken, göz önünde bulundurmanız gereken birkaç şey vardır.</span><span class="sxs-lookup"><span data-stu-id="7aef0-132">When porting a .NET Framework Windows Forms application, there are a few things you must consider.</span></span>

01. <span data-ttu-id="7aef0-133">Uygulamanızın geçiş için iyi bir aday olup olmadığını kontrol edin.</span><span class="sxs-lookup"><span data-stu-id="7aef0-133">Check that your application is a good candidate for migration.</span></span>

    <span data-ttu-id="7aef0-134">Projenizin .NET Core 3.0'a geçirip geçirmeyeceğini belirlemek için [.NET Taşınabilirlik Çözümleyicisini](../../standard/analyzers/portability-analyzer.md) kullanın.</span><span class="sxs-lookup"><span data-stu-id="7aef0-134">Use the [.NET Portability Analyzer](../../standard/analyzers/portability-analyzer.md) to determine if your project will migrate to .NET Core 3.0.</span></span> <span data-ttu-id="7aef0-135">Projenizde .NET Core 3.0 ile ilgili sorunlar varsa, çözümleyici bu sorunları belirlemenize yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="7aef0-135">If your project has issues with .NET Core 3.0, the analyzer helps you identify those problems.</span></span>

01. <span data-ttu-id="7aef0-136">Windows Formlar'ın farklı bir sürümünü kullanıyorsunuz.</span><span class="sxs-lookup"><span data-stu-id="7aef0-136">You're using a different version of Windows Forms.</span></span>

    <span data-ttu-id="7aef0-137">.NET Core 3.0 Preview 1 yayımlandığında, Windows Forms GitHub'da açık kaynak gitti.</span><span class="sxs-lookup"><span data-stu-id="7aef0-137">When .NET Core 3.0 Preview 1 was released, Windows Forms went open source on GitHub.</span></span> <span data-ttu-id="7aef0-138">.NET Çekirdek Windows Formları için kod .NET Framework Windows Forms codebase bir çatal.</span><span class="sxs-lookup"><span data-stu-id="7aef0-138">The code for .NET Core Windows Forms is a fork of the .NET Framework Windows Forms codebase.</span></span> <span data-ttu-id="7aef0-139">Bazı farklılıklar olabilir ve uygulamanız bağlantı noktası olmaz.</span><span class="sxs-lookup"><span data-stu-id="7aef0-139">It's possible some differences exist and your app won't port.</span></span>

01. <span data-ttu-id="7aef0-140">[Windows Uyumluluk Paketi][compat-pack] geçiş yaptığınızda yardımcı olabilir.</span><span class="sxs-lookup"><span data-stu-id="7aef0-140">The [Windows Compatibility Pack][compat-pack] may help you migrate.</span></span>

    <span data-ttu-id="7aef0-141">.NET Framework'de bulunan bazı API'ler .NET Core 3.0'da kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="7aef0-141">Some APIs that are available in .NET Framework aren't available in .NET Core 3.0.</span></span> <span data-ttu-id="7aef0-142">[Windows Uyumluluk Paketi][compat-pack] bu API'lerin çoğunu ekler ve Windows Forms uygulamanızın .NET Core ile uyumlu hale gelmesine yardımcı olabilir.</span><span class="sxs-lookup"><span data-stu-id="7aef0-142">The [Windows Compatibility Pack][compat-pack] adds many of these APIs and may help your Windows Forms app become compatible with .NET Core.</span></span>

01. <span data-ttu-id="7aef0-143">Projeniz tarafından kullanılan NuGet paketlerini güncelleştirin.</span><span class="sxs-lookup"><span data-stu-id="7aef0-143">Update the NuGet packages used by your project.</span></span>

    <span data-ttu-id="7aef0-144">Herhangi bir geçişten önce NuGet paketlerinin en son sürümlerini kullanmak her zaman iyi bir uygulamadır.</span><span class="sxs-lookup"><span data-stu-id="7aef0-144">It's always a good practice to use the latest versions of NuGet packages before any migration.</span></span> <span data-ttu-id="7aef0-145">Uygulamanız herhangi bir NuGet paketine atıfta bulunuyorsa, bunları en son sürüme güncelleştirin.</span><span class="sxs-lookup"><span data-stu-id="7aef0-145">If your application is referencing any NuGet packages, update them to the latest version.</span></span> <span data-ttu-id="7aef0-146">Uygulamanızın başarılı bir şekilde oluşturulmasını sağlayın.</span><span class="sxs-lookup"><span data-stu-id="7aef0-146">Ensure your application builds successfully.</span></span> <span data-ttu-id="7aef0-147">Yükseltmeden sonra, paket hataları varsa, paketi kodunuzu bozmayan en son sürüme indirin.</span><span class="sxs-lookup"><span data-stu-id="7aef0-147">After upgrading, if there are any package errors, downgrade the package to the latest version that doesn't break your code.</span></span>

01. <span data-ttu-id="7aef0-148">Visual Studio 2019 henüz .NET Core 3.0 için Forms Designer desteklemiyor</span><span class="sxs-lookup"><span data-stu-id="7aef0-148">Visual Studio 2019 doesn't yet support the Forms Designer for .NET Core 3.0</span></span>

    <span data-ttu-id="7aef0-149">Şu anda, Visual Studio'dan Formtasarımcısını kullanmak istiyorsanız varolan .NET Framework Windows Forms proje dosyanızı saklamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="7aef0-149">Currently, you need to keep your existing .NET Framework Windows Forms project file if you want to use the Forms Designer from Visual Studio.</span></span>

## <a name="create-a-new-sdk-project"></a><span data-ttu-id="7aef0-150">Yeni bir SDK projesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="7aef0-150">Create a new SDK project</span></span>

<span data-ttu-id="7aef0-151">Oluşturduğunuz yeni .NET Core 3.0 projesi ,NET Framework projenizden farklı bir dizinde olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="7aef0-151">The new .NET Core 3.0 project you create must be in a different directory from your .NET Framework project.</span></span> <span data-ttu-id="7aef0-152">Her ikisi de aynı dizindeyse, **obj** dizininde oluşturulan dosyalarla çakışmalarla karşılaşabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7aef0-152">If they're both in the same directory, you may run into conflicts with the files that are generated in the **obj** directory.</span></span> <span data-ttu-id="7aef0-153">Bu örnekte, **SolutionFolder** dizininde **MyFormsAppCore** adında bir dizin oluştururuz:</span><span class="sxs-lookup"><span data-stu-id="7aef0-153">In this example, we'll create a directory named **MyFormsAppCore** in the **SolutionFolder** directory:</span></span>

```
SolutionFolder
├───MyApps.sln
├───MyFormsApp
│   └───MyForms.csproj
└───MyFormsAppCore      <--- New folder for core project
```

<span data-ttu-id="7aef0-154">Sonra, **MyFormsAppCore dizininde MyFormsCore.csproj** projesini oluşturmanız gerekir. **MyFormsAppCore**</span><span class="sxs-lookup"><span data-stu-id="7aef0-154">Next, you need to create the **MyFormsCore.csproj** project in the **MyFormsAppCore** directory.</span></span> <span data-ttu-id="7aef0-155">Bu dosyayı seçtiğiniz metin düzenleyicisini kullanarak el ile oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7aef0-155">You can create this file manually by using the text editor of choice.</span></span> <span data-ttu-id="7aef0-156">Aşağıdaki XML yapıştırın:</span><span class="sxs-lookup"><span data-stu-id="7aef0-156">Paste in the following XML:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk.WindowsDesktop">

  <PropertyGroup>
    <OutputType>WinExe</OutputType>
    <TargetFramework>netcoreapp3.0</TargetFramework>
    <UseWindowsForms>true</UseWindowsForms>
  </PropertyGroup>

</Project>
```

<span data-ttu-id="7aef0-157">Proje dosyasını el ile oluşturmak istemiyorsanız, projeyi oluşturmak için Visual Studio'yu veya .NET Core SDK'yı kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7aef0-157">If you don't want to create the project file manually, you can use Visual Studio or the .NET Core SDK to generate the project.</span></span> <span data-ttu-id="7aef0-158">Ancak, proje dosyası dışında proje şablonu tarafından oluşturulan diğer tüm dosyaları silmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="7aef0-158">However, you must delete all other files generated by the project template except for the project file.</span></span> <span data-ttu-id="7aef0-159">SDK'yı kullanmak için **SolutionFolder** dizininden aşağıdaki komutu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="7aef0-159">To use the SDK, run the following command from the **SolutionFolder** directory:</span></span>

```dotnetcli
dotnet new winforms -o MyFormsAppCore -n MyFormsCore
```

<span data-ttu-id="7aef0-160">**MyFormsCore.csproj**oluşturduktan sonra, dizin yapıaşağıdaki gibi görünmelidir:</span><span class="sxs-lookup"><span data-stu-id="7aef0-160">After you create the **MyFormsCore.csproj**, your directory structure should look like the following:</span></span>

```
SolutionFolder
├───MyApps.sln
├───MyFormsApp
│   └───MyForms.csproj
└───MyFormsAppCore
    └───MyFormsCore.csproj
```

<span data-ttu-id="7aef0-161">**MyFormsCore.csproj** projesini Visual Studio veya **SolutionFolder** dizininden .NET Core CLI ile **MyApps.sln'ye** ekleyin:</span><span class="sxs-lookup"><span data-stu-id="7aef0-161">Add the **MyFormsCore.csproj** project to **MyApps.sln** with either Visual Studio or the .NET Core CLI from the **SolutionFolder** directory:</span></span>

```dotnetcli
dotnet sln add .\MyFormsAppCore\MyFormsCore.csproj
```

## <a name="fix-assembly-info-generation"></a><span data-ttu-id="7aef0-162">Montaj bilgisi oluşturma düzeltme</span><span class="sxs-lookup"><span data-stu-id="7aef0-162">Fix assembly info generation</span></span>

<span data-ttu-id="7aef0-163">.NET Framework ile oluşturulan Windows Forms `AssemblyInfo.cs` projeleri, oluşturulacak derleme sürümü gibi derleme özniteliklerini içeren bir dosya içerir.</span><span class="sxs-lookup"><span data-stu-id="7aef0-163">Windows Forms projects that were created with .NET Framework include an `AssemblyInfo.cs` file, which contains assembly attributes such as the version of the assembly to be generated.</span></span> <span data-ttu-id="7aef0-164">SDK tarzı projeler, SDK proje dosyasına göre bu bilgileri sizin için otomatik olarak oluşturur.</span><span class="sxs-lookup"><span data-stu-id="7aef0-164">SDK-style projects automatically generate this information for you based on the SDK project file.</span></span> <span data-ttu-id="7aef0-165">Her iki türde "derleme bilgisi" olması bir çakışma oluşturur.</span><span class="sxs-lookup"><span data-stu-id="7aef0-165">Having both types of "assembly info" creates a conflict.</span></span> <span data-ttu-id="7aef0-166">Projeyi varolan `AssemblyInfo.cs` dosyanızı kullanmaya zorlayan otomatik oluşturmayı devre dışı bırakarak bu sorunu giderin.</span><span class="sxs-lookup"><span data-stu-id="7aef0-166">Resolve this problem by disabling automatic generation, which forces the project to use your existing `AssemblyInfo.cs` file.</span></span>

<span data-ttu-id="7aef0-167">Ana `<PropertyGroup>` düğüme eklenecek üç ayar vardır.</span><span class="sxs-lookup"><span data-stu-id="7aef0-167">There are three settings to add to the main `<PropertyGroup>` node.</span></span>

- <span data-ttu-id="7aef0-168">**AssemblyInfo oluşturma**</span><span class="sxs-lookup"><span data-stu-id="7aef0-168">**GenerateAssemblyInfo**</span></span>\
<span data-ttu-id="7aef0-169">Bu özelliği `false`ayarladiğinizde, derleme öznitelikleri oluşturmaz.</span><span class="sxs-lookup"><span data-stu-id="7aef0-169">When you set this property to `false`, it won't generate the assembly attributes.</span></span> <span data-ttu-id="7aef0-170">Bu, .NET Framework `AssemblyInfo.cs` projesindeki varolan dosyayla çakışmayı önler.</span><span class="sxs-lookup"><span data-stu-id="7aef0-170">This avoids the conflict with the existing `AssemblyInfo.cs` file from the .NET Framework project.</span></span>

- <span data-ttu-id="7aef0-171">**Assemblyname**</span><span class="sxs-lookup"><span data-stu-id="7aef0-171">**AssemblyName**</span></span>\
<span data-ttu-id="7aef0-172">Bu özelliğin değeri, derlediğinizde oluşturulan çıktı ikilisidir.</span><span class="sxs-lookup"><span data-stu-id="7aef0-172">The value of this property is the output binary created when you compile.</span></span> <span data-ttu-id="7aef0-173">Adın ekbir uzantıya ihtiyacı yoktur.</span><span class="sxs-lookup"><span data-stu-id="7aef0-173">The name doesn't need an extension added to it.</span></span> <span data-ttu-id="7aef0-174">Örneğin, üretir `MyCoreApp` `MyCoreApp.exe`kullanarak .</span><span class="sxs-lookup"><span data-stu-id="7aef0-174">For example, using `MyCoreApp` produces `MyCoreApp.exe`.</span></span>

- <span data-ttu-id="7aef0-175">**RootNamespace**</span><span class="sxs-lookup"><span data-stu-id="7aef0-175">**RootNamespace**</span></span>\
<span data-ttu-id="7aef0-176">Projeniz tarafından kullanılan varsayılan ad alanı.</span><span class="sxs-lookup"><span data-stu-id="7aef0-176">The default namespace used by your project.</span></span> <span data-ttu-id="7aef0-177">Bu, .NET Framework projesinin varsayılan ad alanıyla eşleşmelidir.</span><span class="sxs-lookup"><span data-stu-id="7aef0-177">This should match the default namespace of the .NET Framework project.</span></span>

<span data-ttu-id="7aef0-178">Bu üç öğeyi `<PropertyGroup>` dosyadaki düğüme ekleyin: `MyFormsCore.csproj`</span><span class="sxs-lookup"><span data-stu-id="7aef0-178">Add these three elements to the `<PropertyGroup>` node in the `MyFormsCore.csproj` file:</span></span>

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

## <a name="add-source-code"></a><span data-ttu-id="7aef0-179">Kaynak kodu ekleme</span><span class="sxs-lookup"><span data-stu-id="7aef0-179">Add source code</span></span>

<span data-ttu-id="7aef0-180">Şu anda, **MyFormsCore.csproj** proje herhangi bir kod derlemek değildir.</span><span class="sxs-lookup"><span data-stu-id="7aef0-180">Right now, the **MyFormsCore.csproj** project doesn't compile any code.</span></span> <span data-ttu-id="7aef0-181">Varsayılan olarak, .NET Core projeleri otomatik olarak geçerli dizindeki tüm kaynak kodunu ve alt dizini içerir.</span><span class="sxs-lookup"><span data-stu-id="7aef0-181">By default, .NET Core projects automatically include all source code in the current directory and any child directories.</span></span> <span data-ttu-id="7aef0-182">Projeyi,.NET Framework projesinden kod içerecek şekilde göreceli bir yol kullanarak yapılandırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="7aef0-182">You must configure the project to include code from the .NET Framework project using a relative path.</span></span> <span data-ttu-id="7aef0-183">.NET Framework projenizde formlarınız için simgeler ve kaynaklar için **.resx** dosyaları kullanıldıysa, bunları da eklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="7aef0-183">If your .NET Framework project used **.resx** files for icons and resources for your forms, you'll need to include those too.</span></span>

<span data-ttu-id="7aef0-184">Projenize `<ItemGroup>` aşağıdaki düğümü ekleyin.</span><span class="sxs-lookup"><span data-stu-id="7aef0-184">Add the following `<ItemGroup>` node to your project.</span></span> <span data-ttu-id="7aef0-185">Her deyim, alt dizinleri içeren bir dosya glob deseni içerir.</span><span class="sxs-lookup"><span data-stu-id="7aef0-185">Each statement includes a file glob pattern that includes child directories.</span></span>

```xml
  <ItemGroup>
    <Compile Include="..\MyFormsApp\**\*.cs" />
    <EmbeddedResource Include="..\MyFormsApp\**\*.resx" />
  </ItemGroup>
```

<span data-ttu-id="7aef0-186">Alternatif olarak, .NET `<Compile>` `<EmbeddedResource>` Framework projenizdeki her dosya için bir veya giriş oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7aef0-186">Alternatively, you can create a `<Compile>` or `<EmbeddedResource>` entry for each file in your .NET Framework project.</span></span>

## <a name="add-nuget-packages"></a><span data-ttu-id="7aef0-187">NuGet paketlerini ekleme</span><span class="sxs-lookup"><span data-stu-id="7aef0-187">Add NuGet packages</span></span>

<span data-ttu-id="7aef0-188">.NET Framework projesi tarafından başvurulan her NuGet paketini .NET Core projesine ekleyin.</span><span class="sxs-lookup"><span data-stu-id="7aef0-188">Add each NuGet package referenced by the .NET Framework project to the .NET Core project.</span></span>

<span data-ttu-id="7aef0-189">Büyük olasılıkla .NET Framework Windows Forms uygulamanızda, projeniz tarafından başvurulan tüm NuGet paketlerinin listesini içeren bir **packages.config** dosyası vardır.</span><span class="sxs-lookup"><span data-stu-id="7aef0-189">Most likely your .NET Framework Windows Forms app has a **packages.config** file that contains a list of all of the NuGet packages that are referenced by your project.</span></span> <span data-ttu-id="7aef0-190">.NET Core projesine hangi NuGet paketlerinin ekleyeceğini belirlemek için bu listeye bakabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7aef0-190">You can look at this list to determine which NuGet packages to add to the .NET Core project.</span></span> <span data-ttu-id="7aef0-191">Örneğin, .NET Framework projesi `MetroFramework`,, `MetroFramework.Design`ve `MetroFramework.Fonts` NuGet paketlerine atıfta bulunduysa, **solutionFolder** dizininden Visual Studio veya .NET Core CLI ile projeye her birini ekleyin:</span><span class="sxs-lookup"><span data-stu-id="7aef0-191">For example, if the .NET Framework project referenced the `MetroFramework`, `MetroFramework.Design`, and `MetroFramework.Fonts` NuGet packages, add each to the project with either Visual Studio or the .NET Core CLI from the **SolutionFolder** directory:</span></span>

```dotnetcli
dotnet add .\MyFormsAppCore\MyFormsCore.csproj package MetroFramework
dotnet add .\MyFormsAppCore\MyFormsCore.csproj package MetroFramework.Design
dotnet add .\MyFormsAppCore\MyFormsCore.csproj package MetroFramework.Fonts
```

<span data-ttu-id="7aef0-192">Önceki komutlar **MyFormsCore.csproj** projesine aşağıdaki NuGet referansları ekler:</span><span class="sxs-lookup"><span data-stu-id="7aef0-192">The previous commands would add the following NuGet references to the **MyFormsCore.csproj** project:</span></span>

```xml
  <ItemGroup>
    <PackageReference Include="MetroFramework" Version="1.2.0.3" />
    <PackageReference Include="MetroFramework.Design" Version="1.2.0.3" />
    <PackageReference Include="MetroFramework.Fonts" Version="1.2.0.3" />
  </ItemGroup>
```

## <a name="port-control-libraries"></a><span data-ttu-id="7aef0-193">Bağlantı noktası kontrol kitaplıkları</span><span class="sxs-lookup"><span data-stu-id="7aef0-193">Port control libraries</span></span>

<span data-ttu-id="7aef0-194">Bağlantı noktasına giden bir Windows Forms Controls kitaplığınız varsa, yol tarifleri birkaç ayar dışında bir .NET Framework Windows Forms uygulama projesini taşımayla aynıdır.</span><span class="sxs-lookup"><span data-stu-id="7aef0-194">If you have a Windows Forms Controls library project to port, the directions are the same as porting a .NET Framework Windows Forms app project, except for a few settings.</span></span> <span data-ttu-id="7aef0-195">Ve yürütülebilir bir derleme yerine, bir kitaplık için derlemek.</span><span class="sxs-lookup"><span data-stu-id="7aef0-195">And instead of compiling to an executable, you compile to a library.</span></span> <span data-ttu-id="7aef0-196">Yürütülebilir proje ile kitaplık projesi arasındaki fark, kaynak kodunuzu içeren dosya globs yollarının yanı sıra en az düzeydedir.</span><span class="sxs-lookup"><span data-stu-id="7aef0-196">The difference between the executable project and the library project, besides paths for the file globs that include your source code, is minimal.</span></span>

<span data-ttu-id="7aef0-197">Önceki adımın örneğini kullanarak, hangi projelerle çalıştığımızı ve dosyaları genişletmemizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="7aef0-197">Using the previous step's example, lets expand what projects and files we're working with.</span></span>

| <span data-ttu-id="7aef0-198">Dosya</span><span class="sxs-lookup"><span data-stu-id="7aef0-198">File</span></span> | <span data-ttu-id="7aef0-199">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7aef0-199">Description</span></span> |
| ---- | ----------- |
| <span data-ttu-id="7aef0-200">**MyApps.sln**</span><span class="sxs-lookup"><span data-stu-id="7aef0-200">**MyApps.sln**</span></span> | <span data-ttu-id="7aef0-201">Çözüm dosyasının adı.</span><span class="sxs-lookup"><span data-stu-id="7aef0-201">The name of the solution file.</span></span> |
| <span data-ttu-id="7aef0-202">**MyControls.csproj**</span><span class="sxs-lookup"><span data-stu-id="7aef0-202">**MyControls.csproj**</span></span> | <span data-ttu-id="7aef0-203">.NET Framework Windows Forms Controls projesinin adı bağlantı noktasına.</span><span class="sxs-lookup"><span data-stu-id="7aef0-203">The name of the .NET Framework Windows Forms Controls project to port.</span></span> |
| <span data-ttu-id="7aef0-204">**MyControlsCore.csproj**</span><span class="sxs-lookup"><span data-stu-id="7aef0-204">**MyControlsCore.csproj**</span></span> | <span data-ttu-id="7aef0-205">Oluşturduğunuz yeni .NET Core kitaplık projesinin adı.</span><span class="sxs-lookup"><span data-stu-id="7aef0-205">The name of the new .NET Core library project you create.</span></span> |
| <span data-ttu-id="7aef0-206">**MyCoreControls.dll**</span><span class="sxs-lookup"><span data-stu-id="7aef0-206">**MyCoreControls.dll**</span></span> | <span data-ttu-id="7aef0-207">.NET Core Windows Forms Denetimleri kitaplığı.</span><span class="sxs-lookup"><span data-stu-id="7aef0-207">The .NET Core Windows Forms Controls library.</span></span> |

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

<span data-ttu-id="7aef0-208">`MyControlsCore.csproj` Proje ile daha önce oluşturulmuş `MyFormsCore.csproj` proje arasındaki farkları göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="7aef0-208">Consider the differences between the `MyControlsCore.csproj` project and the previously created `MyFormsCore.csproj` project.</span></span>

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

<span data-ttu-id="7aef0-209">Aşağıda ,.NET Core Windows Forms Controls kitaplık proje dosyasının nasıl görüneceğine bir örnek verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="7aef0-209">Here is an example of what the .NET Core Windows Forms Controls library project file would look like:</span></span>

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

<span data-ttu-id="7aef0-210">Gördüğünüz gibi, `<OutputType>` düğüm kaldırıldı ve bu da derleyicinin yürütülebilir yerine kitaplık oluşturması için varsayılan olarak varsayılan olarak.</span><span class="sxs-lookup"><span data-stu-id="7aef0-210">As you can see, the `<OutputType>` node was removed, which defaults the compiler to produce a library instead of an executable.</span></span> <span data-ttu-id="7aef0-211">Ve `<AssemblyName>` `<RootNamespace>` değiştirildi.</span><span class="sxs-lookup"><span data-stu-id="7aef0-211">The `<AssemblyName>` and `<RootNamespace>` were changed.</span></span> <span data-ttu-id="7aef0-212">Özellikle `<RootNamespace>` taşıma yaptığınız Windows Forms Denetimleri kitaplığı ad alanı yla eşleşmelidir.</span><span class="sxs-lookup"><span data-stu-id="7aef0-212">Specifically the `<RootNamespace>` should match the namespace of the Windows Forms Controls library you are porting.</span></span> <span data-ttu-id="7aef0-213">Ve son `<Compile>` olarak, düğümler, `<EmbeddedResource>` taşıma yaptığınız Windows Forms Denetimleri kitaplığı klasörüne işaret edecek şekilde ayarlandı.</span><span class="sxs-lookup"><span data-stu-id="7aef0-213">And finally, the `<Compile>` and `<EmbeddedResource>` nodes were adjusted to point to the folder of the Windows Forms Controls library you are porting.</span></span>

<span data-ttu-id="7aef0-214">Ardından, ana .NET Core **MyFormsCore.csproj** projesinde, yeni .NET Core Windows Formlar Kontrol kitaplığına bir başvuru ekleyin.</span><span class="sxs-lookup"><span data-stu-id="7aef0-214">Next, in the main .NET Core **MyFormsCore.csproj** project, add a reference to the new .NET Core Windows Forms Control library.</span></span> <span data-ttu-id="7aef0-215">**SolutionFolder** dizininden Visual Studio veya .NET Core CLI ile bir başvuru ekleyin:</span><span class="sxs-lookup"><span data-stu-id="7aef0-215">Add a reference with either Visual Studio or the .NET Core CLI from the **SolutionFolder** directory:</span></span>

```dotnetcli
dotnet add .\MyFormsAppCore\MyFormsCore.csproj reference .\MyFormsControlsCore\MyControlsCore.csproj
```

<span data-ttu-id="7aef0-216">Önceki komut **MyFormsCore.csproj** projesine aşağıdakileri ekler:</span><span class="sxs-lookup"><span data-stu-id="7aef0-216">The previous command adds the following to the **MyFormsCore.csproj** project:</span></span>

```xml
  <ItemGroup>
    <ProjectReference Include="..\MyFormsControlsCore\MyControlsCore.csproj" />
  </ItemGroup>
```

## <a name="compilation-problems"></a><span data-ttu-id="7aef0-217">Derleme sorunları</span><span class="sxs-lookup"><span data-stu-id="7aef0-217">Compilation problems</span></span>

<span data-ttu-id="7aef0-218">Projelerinizi derlemede sorun yaşıyorsanız, .NET Framework'de kullanılabilen ancak .NET Core'da bulunmayan yalnızca Windows'a özel API'ler kullanıyor olabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7aef0-218">If you have problems compiling your projects, you may be using some Windows-only APIs that are available in .NET Framework but not available in .NET Core.</span></span> <span data-ttu-id="7aef0-219">Projenize Windows [Uyumluluk Paketi][compat-pack] NuGet paketini eklemeyi deneyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7aef0-219">You can try adding the [Windows Compatibility Pack][compat-pack] NuGet package to your project.</span></span> <span data-ttu-id="7aef0-220">Bu paket yalnızca Windows'da çalışır ve .NET Core ve .NET Standard projelerine yaklaşık 20.000 Windows API'si ekler.</span><span class="sxs-lookup"><span data-stu-id="7aef0-220">This package only runs on Windows and adds about 20,000 Windows APIs to .NET Core and .NET Standard projects.</span></span>

```dotnetcli
dotnet add .\MyFormsAppCore\MyFormsCore.csproj package Microsoft.Windows.Compatibility
```

<span data-ttu-id="7aef0-221">Önceki komut **MyFormsCore.csproj** projesine aşağıdakileri ekler:</span><span class="sxs-lookup"><span data-stu-id="7aef0-221">The previous command adds the following to the **MyFormsCore.csproj** project:</span></span>

```xml
  <ItemGroup>
    <PackageReference Include="Microsoft.Windows.Compatibility" Version="3.1.0" />
  </ItemGroup>
```

## <a name="windows-forms-designer"></a><span data-ttu-id="7aef0-222">Windows Form Tasarımcısı</span><span class="sxs-lookup"><span data-stu-id="7aef0-222">Windows Forms Designer</span></span>

<span data-ttu-id="7aef0-223">Bu makalede ayrıntılı olarak belirtildiği gibi Visual Studio 2019 sadece .NET Framework projelerinde Form Tasarımcısı'nı destekler.</span><span class="sxs-lookup"><span data-stu-id="7aef0-223">As detailed in this article, Visual Studio 2019 only supports the Forms Designer in .NET Framework projects.</span></span> <span data-ttu-id="7aef0-224">Yan yana .NET Core projesi oluşturarak, formları tasarlamak için .NET Framework projesini kullanırken projenizi .NET Core ile test edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7aef0-224">By creating a side-by-side .NET Core project, you can test your project with .NET Core while you use the .NET Framework project to design forms.</span></span> <span data-ttu-id="7aef0-225">Çözüm dosyanız hem .NET Framework hem de .NET Core projelerini içerir.</span><span class="sxs-lookup"><span data-stu-id="7aef0-225">Your solution file includes both the .NET Framework and .NET Core projects.</span></span> <span data-ttu-id="7aef0-226">.NET Framework projesinde formlarınızı ve kontrollerinizi ekleyin ve tasarlayın ve .NET Core projelerine eklediğimiz dosya glob desenlerine göre, yeni veya değiştirilen dosyalar otomatik olarak .NET Core projelerine dahil edilir.</span><span class="sxs-lookup"><span data-stu-id="7aef0-226">Add and design your forms and controls in the .NET Framework project, and based on the file glob patterns we added to the .NET Core projects, any new or changed files will automatically be included in the .NET Core projects.</span></span>

<span data-ttu-id="7aef0-227">Visual Studio 2019 Windows Forms Designer'ı destekledikten sonra .NET Core proje dosyanızın içeriğini .NET Framework proje dosyasına kopyalayabilir/yapıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7aef0-227">Once Visual Studio 2019 supports the Windows Forms Designer, you can copy/paste the content of your .NET Core project file into the .NET Framework project file.</span></span> <span data-ttu-id="7aef0-228">Sonra dosya glob desenleri `<Source>` ve `<EmbeddedResource>` öğeleri ile ekledi silin.</span><span class="sxs-lookup"><span data-stu-id="7aef0-228">Then delete the file glob patterns added with the `<Source>` and `<EmbeddedResource>` items.</span></span> <span data-ttu-id="7aef0-229">Uygulamanız tarafından kullanılan herhangi bir proje başvurusuna giden yolları düzeltin.</span><span class="sxs-lookup"><span data-stu-id="7aef0-229">Fix the paths to any project reference used by your app.</span></span> <span data-ttu-id="7aef0-230">Bu, .NET Framework projesini bir .NET Core projesine etkin bir şekilde yükseltir.</span><span class="sxs-lookup"><span data-stu-id="7aef0-230">This effectively upgrades the .NET Framework project to a .NET Core project.</span></span>

## <a name="next-steps"></a><span data-ttu-id="7aef0-231">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="7aef0-231">Next steps</span></span>

- <span data-ttu-id="7aef0-232">[.NET Framework'den .NET Core'a değişiklik kırma](../compatibility/fx-core.md)hakkında bilgi edinin.</span><span class="sxs-lookup"><span data-stu-id="7aef0-232">Learn about [breaking changes from .NET Framework to .NET Core](../compatibility/fx-core.md).</span></span>
- <span data-ttu-id="7aef0-233">Windows Uyumluluk [Paketi][compat-pack]hakkında daha fazla bilgi edinin.</span><span class="sxs-lookup"><span data-stu-id="7aef0-233">Read more about the [Windows Compatibility Pack][compat-pack].</span></span>
- <span data-ttu-id="7aef0-234">.NET Framework Windows Forms projenizi .NET Core'a [taşıma yla ilgili](https://www.youtube.com/watch?v=upVQEUc_KwU) bir video izleyin.</span><span class="sxs-lookup"><span data-stu-id="7aef0-234">Watch a [video on porting](https://www.youtube.com/watch?v=upVQEUc_KwU) your .NET Framework Windows Forms project to .NET Core.</span></span>

[compat-pack]: windows-compat-pack.md
