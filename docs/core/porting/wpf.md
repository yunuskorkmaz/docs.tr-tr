---
title: .NET Core 3.0 WPF uygulaması bağlantı noktası
description: Windows için .NET Core 3.0 için bir .NET Framework Windows Presentation Foundation uygulaması bağlantı noktasına öğretir.
author: Thraka
ms.author: adegeo
ms.date: 03/27/2019
ms.custom: ''
ms.openlocfilehash: 5c7e3aca0a473abb831693244d1b194985f2ef7f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61614563"
---
# <a name="how-to-port-a-wpf-desktop-app-to-net-core"></a><span data-ttu-id="661d5-103">Nasıl yapılır: .NET Core için bir WPF masaüstü uygulaması bağlantı noktası</span><span class="sxs-lookup"><span data-stu-id="661d5-103">How to: Port a WPF desktop app to .NET Core</span></span>

<span data-ttu-id="661d5-104">Bu makalede, bağlantı noktası tabanlı Windows Presentation Foundation (WPF) Masaüstü uygulamanızın .NET Framework için .NET Core 3.0 açıklar.</span><span class="sxs-lookup"><span data-stu-id="661d5-104">This article describes how to port your Windows Presentation Foundation-based (WPF) desktop app from .NET Framework to .NET Core 3.0.</span></span> <span data-ttu-id="661d5-105">.NET Core SDK 3.0 WPF uygulamaları için destek içerir.</span><span class="sxs-lookup"><span data-stu-id="661d5-105">The .NET Core 3.0 SDK includes support for WPF applications.</span></span> <span data-ttu-id="661d5-106">WPF, yalnızca Windows framework hala geçerli olduğunu ve yalnızca Windows üzerinde çalışır.</span><span class="sxs-lookup"><span data-stu-id="661d5-106">WPF is still a Windows-only framework and only runs on Windows.</span></span> <span data-ttu-id="661d5-107">Bu örnek, oluşturmak ve projenize yönetmek için .NET Core SDK'sı CLI'yı kullanır.</span><span class="sxs-lookup"><span data-stu-id="661d5-107">This example uses the .NET Core SDK CLI to create and manage your project.</span></span>

<span data-ttu-id="661d5-108">Bu makalede, çeşitli adlar, geçiş için kullanılan dosya türlerini tanımlamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="661d5-108">In this article, various names are used to identify types of files used for migration.</span></span> <span data-ttu-id="661d5-109">Projenizi geçirirken, dosyalarınızı farklı şekilde adlandırılmış, bu nedenle akıl aşağıda listelenen olanlarla eşleşmesi:</span><span class="sxs-lookup"><span data-stu-id="661d5-109">When migrating your project, your files will be named differently, so mentally match them to the ones listed below:</span></span>

| <span data-ttu-id="661d5-110">Dosya</span><span class="sxs-lookup"><span data-stu-id="661d5-110">File</span></span> | <span data-ttu-id="661d5-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="661d5-111">Description</span></span> |
| ---- | ----------- |
| <span data-ttu-id="661d5-112">**MyApps.sln**</span><span class="sxs-lookup"><span data-stu-id="661d5-112">**MyApps.sln**</span></span> | <span data-ttu-id="661d5-113">Çözüm dosyasının adı.</span><span class="sxs-lookup"><span data-stu-id="661d5-113">The name of the solution file.</span></span> |
| <span data-ttu-id="661d5-114">**MyWPF.csproj**</span><span class="sxs-lookup"><span data-stu-id="661d5-114">**MyWPF.csproj**</span></span> | <span data-ttu-id="661d5-115">Bağlantı noktası için .NET Framework WPF projesinin adı.</span><span class="sxs-lookup"><span data-stu-id="661d5-115">The name of the .NET Framework WPF project to port.</span></span> |
| <span data-ttu-id="661d5-116">**MyWPFCore.csproj**</span><span class="sxs-lookup"><span data-stu-id="661d5-116">**MyWPFCore.csproj**</span></span> | <span data-ttu-id="661d5-117">Oluşturduğunuz yeni .NET Core projesinin adı.</span><span class="sxs-lookup"><span data-stu-id="661d5-117">The name of the new .NET Core project you create.</span></span> |
| <span data-ttu-id="661d5-118">**MyAppCore.exe**</span><span class="sxs-lookup"><span data-stu-id="661d5-118">**MyAppCore.exe**</span></span> | <span data-ttu-id="661d5-119">.NET Core WPF uygulaması çalıştırılabilir.</span><span class="sxs-lookup"><span data-stu-id="661d5-119">The .NET Core WPF app executable.</span></span> |

## <a name="prerequisites"></a><span data-ttu-id="661d5-120">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="661d5-120">Prerequisites</span></span>

- <span data-ttu-id="661d5-121">[Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) yapmak istediğiniz herhangi bir tasarımcı iş için.</span><span class="sxs-lookup"><span data-stu-id="661d5-121">[Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) for any designer work you want to do.</span></span>

  <span data-ttu-id="661d5-122">Aşağıdaki Visual Studio iş yüklerini yükleyin:</span><span class="sxs-lookup"><span data-stu-id="661d5-122">Install the following Visual Studio workloads:</span></span>
  - <span data-ttu-id="661d5-123">.NET masaüstü geliştirme</span><span class="sxs-lookup"><span data-stu-id="661d5-123">.NET desktop development</span></span>
  - <span data-ttu-id="661d5-124">.NET platformlar arası geliştirme</span><span class="sxs-lookup"><span data-stu-id="661d5-124">.NET cross-platform development</span></span>

- <span data-ttu-id="661d5-125">Çalışan WPF projesi oluşturan ve sorun çalışır bir çözümde.</span><span class="sxs-lookup"><span data-stu-id="661d5-125">A working WPF project in a solution that builds and runs without issue.</span></span>
- <span data-ttu-id="661d5-126">İçinde projenizin kodlanmasını C#.</span><span class="sxs-lookup"><span data-stu-id="661d5-126">Your project must be coded in C#.</span></span> 
- <span data-ttu-id="661d5-127">Son yükleme [.NET Core 3.0](https://aka.ms/netcore3download) Önizleme.</span><span class="sxs-lookup"><span data-stu-id="661d5-127">Install the latest [.NET Core 3.0](https://aka.ms/netcore3download) preview.</span></span>

>[!NOTE]
><span data-ttu-id="661d5-128">**Visual Studio 2017** .NET Core 3.0 projeleri desteklemiyor.</span><span class="sxs-lookup"><span data-stu-id="661d5-128">**Visual Studio 2017** doesn't support .NET Core 3.0 projects.</span></span> <span data-ttu-id="661d5-129">**Visual Studio 2019** .NET Core 3.0 projeleri destekler ancak görsel tasarımcı için .NET Core 3.0 WPF projeleri henüz desteklememektedir.</span><span class="sxs-lookup"><span data-stu-id="661d5-129">**Visual Studio 2019** supports .NET Core 3.0 projects but doesn't yet support the visual designer for .NET Core 3.0 WPF projects.</span></span> <span data-ttu-id="661d5-130">Görsel tasarımcıyı kullanmak için çözümünüzdeki ile .NET Core proje dosyaları paylaşan bir .NET WPF projesi olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="661d5-130">To use the visual designer, you must have a .NET WPF project in your solution that shares its files with the .NET Core project.</span></span>

### <a name="consider"></a><span data-ttu-id="661d5-131">Göz önünde bulundurun</span><span class="sxs-lookup"><span data-stu-id="661d5-131">Consider</span></span>

<span data-ttu-id="661d5-132">.NET Framework WPF uygulaması taşırken dikkate almanız gereken birkaç nokta vardır.</span><span class="sxs-lookup"><span data-stu-id="661d5-132">When porting a .NET Framework WPF application, there are a few things you must consider.</span></span>

01. <span data-ttu-id="661d5-133">Uygulamanızı geçişi için iyi bir aday olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="661d5-133">Check that your application is a good candidate for migration.</span></span>

    <span data-ttu-id="661d5-134">Kullanım [.NET Portability Analyzer](../../standard/analyzers/portability-analyzer.md) projeniz için .NET Core 3.0 geçirirseniz belirlemek için.</span><span class="sxs-lookup"><span data-stu-id="661d5-134">Use the [.NET Portability Analyzer](../../standard/analyzers/portability-analyzer.md) to determine if your project will migrate to .NET Core 3.0.</span></span> <span data-ttu-id="661d5-135">Projeniz .NET Core 3.0 ile ilgili sorunlar varsa, Çözümleyicisi bu sorunları belirlemenize yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="661d5-135">If your project has issues with .NET Core 3.0, the analyzer helps you identify those problems.</span></span>

01. <span data-ttu-id="661d5-136">WPF farklı bir sürümünü kullanıyorsunuz.</span><span class="sxs-lookup"><span data-stu-id="661d5-136">You're using a different version of WPF.</span></span>

    <span data-ttu-id="661d5-137">.NET Core 3.0 Önizleme 1 yayımlandığında, WPF, açık kaynaklı oluştu. GitHub üzerinde.</span><span class="sxs-lookup"><span data-stu-id="661d5-137">When .NET Core 3.0 Preview 1 was released, WPF went open-source on GitHub.</span></span> <span data-ttu-id="661d5-138">.NET Framework WPF kod tabanı deponun bir çatalını .NET Core WPF kodudur.</span><span class="sxs-lookup"><span data-stu-id="661d5-138">The code for .NET Core WPF is a fork of the .NET Framework WPF code base.</span></span> <span data-ttu-id="661d5-139">Bu, bazı farklılıklar mevcuttur ve uygulamanızı bağlantı noktası olmaz mümkündür.</span><span class="sxs-lookup"><span data-stu-id="661d5-139">It's possible some differences exist and your app won't port.</span></span>

01. <span data-ttu-id="661d5-140">[Windows Uyumluluk Paketi] [ compat-pack] geçirmenize yardımcı olabilir.</span><span class="sxs-lookup"><span data-stu-id="661d5-140">The [Windows Compatibility Pack][compat-pack] may help you migrate.</span></span>

    <span data-ttu-id="661d5-141">.NET Framework'te bulunan bazı API'leri, .NET Core 3. 0'kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="661d5-141">Some APIs that are available in .NET Framework aren't available in .NET Core 3.0.</span></span> <span data-ttu-id="661d5-142">[Windows Uyumluluk Paketi] [ compat-pack] bu API'lerin birçoğu ekler ve .NET Core ile uyumlu hale WPF uygulamanıza yardımcı olabilir.</span><span class="sxs-lookup"><span data-stu-id="661d5-142">The [Windows Compatibility Pack][compat-pack] adds many of these APIs and may help your WPF app become compatible with .NET Core.</span></span>

01. <span data-ttu-id="661d5-143">Projeniz tarafından kullanılan NuGet paketlerini güncelleştirin.</span><span class="sxs-lookup"><span data-stu-id="661d5-143">Update the NuGet packages used by your project.</span></span>

    <span data-ttu-id="661d5-144">Tüm geçiş işleminden önce NuGet paketlerini en son sürümlerini kullanmak için her zaman iyi bir uygulamadır.</span><span class="sxs-lookup"><span data-stu-id="661d5-144">It's always a good practice to use the latest versions of NuGet packages before any migration.</span></span> <span data-ttu-id="661d5-145">Uygulamanızı herhangi bir NuGet paketinin başvuruyorsa, bunları en son sürüme güncelleştirin.</span><span class="sxs-lookup"><span data-stu-id="661d5-145">If your application is referencing any NuGet packages, update them to the latest version.</span></span> <span data-ttu-id="661d5-146">Uygulamanız başarıyla derlendiğinden emin olun.</span><span class="sxs-lookup"><span data-stu-id="661d5-146">Ensure your application builds successfully.</span></span> <span data-ttu-id="661d5-147">Herhangi bir paket hata varsa, yükselttikten sonra paketi kodunuzu kesmeyecektir en son sürüme düşürme.</span><span class="sxs-lookup"><span data-stu-id="661d5-147">After upgrading, if there are any package errors, downgrade the package to the latest version that doesn't break your code.</span></span>

01. <span data-ttu-id="661d5-148">Visual Studio 2019 .NET Core 3.0 için WPF Tasarımcısı henüz desteklemiyor</span><span class="sxs-lookup"><span data-stu-id="661d5-148">Visual Studio 2019 doesn't yet support the WPF Designer for .NET Core 3.0</span></span>

    <span data-ttu-id="661d5-149">Şu anda, Visual Studio'da WPF Tasarımcısı kullanmak istiyorsanız, var olan .NET Framework WPF projesi dosyanızı çalışır durumda bulundurmanıza gerek.</span><span class="sxs-lookup"><span data-stu-id="661d5-149">Currently, you need to keep your existing .NET Framework WPF project file if you want to use the WPF Designer from Visual Studio.</span></span>

## <a name="create-a-new-sdk-project"></a><span data-ttu-id="661d5-150">Yeni SDK projesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="661d5-150">Create a new SDK project</span></span>

<span data-ttu-id="661d5-151">Oluşturduğunuz yeni .NET Core 3.0 proje .NET Framework projenizden farklı bir dizinde olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="661d5-151">The new .NET Core 3.0 project you create must be in a different directory from your .NET Framework project.</span></span> <span data-ttu-id="661d5-152">Her ikisi de aynı dizinde iseler, içinde oluşturulan dosyalar ile çakışma çalışabilir **obj** dizin.</span><span class="sxs-lookup"><span data-stu-id="661d5-152">If they're both in the same directory, you may run into conflicts with the files that are generated in the **obj** directory.</span></span> <span data-ttu-id="661d5-153">Adlı bir dizin oluşturma Bu örnekte, **MyWPFAppCore** içinde **SolutionFolder** dizini:</span><span class="sxs-lookup"><span data-stu-id="661d5-153">In this example, you'll create a directory named **MyWPFAppCore** in the **SolutionFolder** directory:</span></span>

```
SolutionFolder
├───MyApps.sln
├───MyWPFApp
│   └───MyWPF.csproj
└───MyWPFAppCore      <--- New folder for core project
```

<span data-ttu-id="661d5-154">Ardından, oluşturmak için ihtiyacınız **MyWPFCore.csproj** projesi **MyWPFAppCore** dizin.</span><span class="sxs-lookup"><span data-stu-id="661d5-154">Next, you need to create the **MyWPFCore.csproj** project in the **MyWPFAppCore** directory.</span></span> <span data-ttu-id="661d5-155">Bu dosyayı el ile metni kullanarak dilediğiniz düzenleyicisinde oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="661d5-155">You can create this file manually by using the text editor of choice.</span></span> <span data-ttu-id="661d5-156">Aşağıdaki XML yapıştırın:</span><span class="sxs-lookup"><span data-stu-id="661d5-156">Paste in the following XML:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk.WindowsDesktop">

  <PropertyGroup>
    <OutputType>WinExe</OutputType>
    <TargetFramework>netcoreapp3.0</TargetFramework>
    <UseWPF>true</UseWPF>
  </PropertyGroup>

</Project>
```

<span data-ttu-id="661d5-157">Proje dosyasını el ile oluşturmak istemiyorsanız, projeyi oluşturmak için Visual Studio veya .NET Core SDK'sını kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="661d5-157">If you don't want to create the project file manually, you can use Visual Studio or the .NET Core SDK to generate the project.</span></span> <span data-ttu-id="661d5-158">Ancak, proje dosyasının dışında proje şablonu tarafından oluşturulan tüm dosyalar silmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="661d5-158">However, you must delete all other files generated by the project template except for the project file.</span></span> <span data-ttu-id="661d5-159">SDK'yı kullanmak için aşağıdaki komutu çalıştırın. **SolutionFolder** dizini:</span><span class="sxs-lookup"><span data-stu-id="661d5-159">To use the SDK, run the following command from the **SolutionFolder** directory:</span></span>

```cli
dotnet new wpf -o MyWPFAppCore -n MyWPFCore
```

<span data-ttu-id="661d5-160">Oluşturduktan sonra **MyWPFCore.csproj**, dizin yapısını aşağıdaki gibi görünmelidir:</span><span class="sxs-lookup"><span data-stu-id="661d5-160">After you create the **MyWPFCore.csproj**, your directory structure should look like the following:</span></span>

```
SolutionFolder
├───MyApps.sln
├───MyWPFApp
│   └───MyWPF.csproj
└───MyWPFAppCore
    └───MyWPFCore.csproj
```

<span data-ttu-id="661d5-161">Eklemek istediğiniz **MyWPFCore.csproj** için proje **MyApps.sln** Visual Studio veya .NET Core CLI üzerinden **SolutionFolder** dizini:</span><span class="sxs-lookup"><span data-stu-id="661d5-161">You'll want to add the **MyWPFCore.csproj** project to **MyApps.sln** with either Visual Studio or the .NET Core CLI from the **SolutionFolder** directory:</span></span>

```cli
dotnet sln add .\MyWPFAppCore\MyWPFCore.csproj
```

## <a name="fix-assembly-info-generation"></a><span data-ttu-id="661d5-162">Düzeltme derleme bilgileri oluşturma</span><span class="sxs-lookup"><span data-stu-id="661d5-162">Fix assembly info generation</span></span>

<span data-ttu-id="661d5-163">.NET Framework ile oluşturulan Windows Presentation Foundation projeleri içeren bir `AssemblyInfo.cs` oluşturulacak derlemenin sürümü gibi derleme özniteliklerinin içeren dosya.</span><span class="sxs-lookup"><span data-stu-id="661d5-163">Windows Presentation Foundation projects that were created with .NET Framework include an `AssemblyInfo.cs` file, which contains assembly attributes such as the version of the assembly to be generated.</span></span> <span data-ttu-id="661d5-164">SDK stili projeleri, bu bilgileri size SDK proje dosyasını temel alarak otomatik olarak oluşturur.</span><span class="sxs-lookup"><span data-stu-id="661d5-164">SDK-style projects automatically generate this information for you based on the SDK project file.</span></span> <span data-ttu-id="661d5-165">Her iki "bütünleştirilmiş kod bilgileri" türüne sahip olan bir çakışma oluşturur.</span><span class="sxs-lookup"><span data-stu-id="661d5-165">Having both types of "assembly info" creates a conflict.</span></span> <span data-ttu-id="661d5-166">Mevcut kullanmak için projeyi otomatik oluşturma devre dışı bırakarak bu sorunu gidermek `AssemblyInfo.cs` dosya.</span><span class="sxs-lookup"><span data-stu-id="661d5-166">Resolve this problem by disabling automatic generation, which forces the project to use your existing `AssemblyInfo.cs` file.</span></span>

<span data-ttu-id="661d5-167">Ana eklemek için üç seçenek vardır `<PropertyGroup>` düğümü.</span><span class="sxs-lookup"><span data-stu-id="661d5-167">There are three settings to add to the main `<PropertyGroup>` node.</span></span> 

- <span data-ttu-id="661d5-168">**GenerateAssemblyInfo**\\</span><span class="sxs-lookup"><span data-stu-id="661d5-168">**GenerateAssemblyInfo**\\</span></span>
<span data-ttu-id="661d5-169">Bu özelliği ayarlandığında `false`, derleme öznitelikleri üretmeyeceğini.</span><span class="sxs-lookup"><span data-stu-id="661d5-169">When you set this property to `false`, it won't generate the assembly attributes.</span></span> <span data-ttu-id="661d5-170">Bu mevcut çakışmayı önler `AssemblyInfo.cs` .NET Framework proje dosyası.</span><span class="sxs-lookup"><span data-stu-id="661d5-170">This avoids the conflict with the existing `AssemblyInfo.cs` file from the .NET Framework project.</span></span>

- <span data-ttu-id="661d5-171">**AssemblyName**\\</span><span class="sxs-lookup"><span data-stu-id="661d5-171">**AssemblyName**\\</span></span>
<span data-ttu-id="661d5-172">Bu özellik, derlerken oluşturulan çıktıyı ikili değerdir.</span><span class="sxs-lookup"><span data-stu-id="661d5-172">The value of this property is the output binary created when you compile.</span></span> <span data-ttu-id="661d5-173">Ad, kendisine eklenmiş bir uzantı gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="661d5-173">The name doesn't need an extension added to it.</span></span> <span data-ttu-id="661d5-174">Örneğin, kullanarak `MyCoreApp` üretir `MyCoreApp.exe`.</span><span class="sxs-lookup"><span data-stu-id="661d5-174">For example, using `MyCoreApp` produces `MyCoreApp.exe`.</span></span>

- <span data-ttu-id="661d5-175">**RootNamespace**\\</span><span class="sxs-lookup"><span data-stu-id="661d5-175">**RootNamespace**\\</span></span>
<span data-ttu-id="661d5-176">Projeniz tarafından kullanılan varsayılan ad alanı.</span><span class="sxs-lookup"><span data-stu-id="661d5-176">The default namespace used by your project.</span></span> <span data-ttu-id="661d5-177">Bu, .NET Framework projenin varsayılan ad alanı eşleşmelidir.</span><span class="sxs-lookup"><span data-stu-id="661d5-177">This should match the default namespace of the .NET Framework project.</span></span>

<span data-ttu-id="661d5-178">Bu üç öğelerine ekleme `<PropertyGroup>` düğümünde `MyWPFCore.csproj` dosyası:</span><span class="sxs-lookup"><span data-stu-id="661d5-178">Add these three elements to the `<PropertyGroup>` node in the `MyWPFCore.csproj` file:</span></span>

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

## <a name="add-source-code"></a><span data-ttu-id="661d5-179">Kaynak kodu ekleme</span><span class="sxs-lookup"><span data-stu-id="661d5-179">Add source code</span></span>
<span data-ttu-id="661d5-180">Şu anda **MyWPFCore.csproj** herhangi bir kod projesi derleme değil.</span><span class="sxs-lookup"><span data-stu-id="661d5-180">Right now, the **MyWPFCore.csproj** project doesn't compile any code.</span></span> <span data-ttu-id="661d5-181">Varsayılan olarak, .NET Core projeleri otomatik olarak geçerli dizin ve alt dizinleri içinde tüm kaynak kodu içerir.</span><span class="sxs-lookup"><span data-stu-id="661d5-181">By default, .NET Core projects automatically include all source code in the current directory and any child directories.</span></span> <span data-ttu-id="661d5-182">Proje göreli yolu kullanarak .NET Framework projesinin koddan içerecek şekilde yapılandırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="661d5-182">You must configure the project to include code from the .NET Framework project using a relative path.</span></span> <span data-ttu-id="661d5-183">.NET Framework projenizin kullandıysanız **.resx** simgeler için dosyaları ve kaynaklar windows ve denetimler için gereken çok içerir.</span><span class="sxs-lookup"><span data-stu-id="661d5-183">If your .NET Framework project used **.resx** files for icons and resources for your windows and controls, you'll need to include those too.</span></span> 

<span data-ttu-id="661d5-184">İlk `<ItemGroup>` projenize eklemeniz düğüm içerir **App.xaml** başlangıç yapılandırması ve kaynak dosyası, uygulama kullanır.</span><span class="sxs-lookup"><span data-stu-id="661d5-184">The first `<ItemGroup>` node you need to add to your project includes the **App.xaml** file that represents the startup config and resources your app uses.</span></span> <span data-ttu-id="661d5-185">**App.xaml** dosya de sahip bir eşlik eden **App.xaml.cs** dosyası, ancak otomatik olarak dahil edilecek farklı bir `<ItemGroup>`.</span><span class="sxs-lookup"><span data-stu-id="661d5-185">The **App.xaml** file also has an accompanying **App.xaml.cs** file, but it will be automatically included in a different `<ItemGroup>`.</span></span>

```xml
  <ItemGroup>
    <ApplicationDefinition Include="..\MyWPFApp\App.xaml">
      <Generator>MSBuild:Compile</Generator>
    </ApplicationDefinition>
  </ItemGroup>
```

<span data-ttu-id="661d5-186">Ardından, aşağıdaki ekleyin `<ItemGroup>` projenize düğümü.</span><span class="sxs-lookup"><span data-stu-id="661d5-186">Next, add the following `<ItemGroup>` node to your project.</span></span> <span data-ttu-id="661d5-187">Her deyim alt dizinleri içeren bir dosya glob deseni içerir.</span><span class="sxs-lookup"><span data-stu-id="661d5-187">Each statement includes a file glob pattern that includes child directories.</span></span> <span data-ttu-id="661d5-188">Bu proje, herhangi bir ayar dosyaları ve tüm kaynakları kaynak kodunu içerir.</span><span class="sxs-lookup"><span data-stu-id="661d5-188">It includes the source code for your project, any settings files, and any resources.</span></span> <span data-ttu-id="661d5-189">**Obj** dizin açıkça hariç.</span><span class="sxs-lookup"><span data-stu-id="661d5-189">The **obj** directory is explicitly excluded.</span></span>

```xml
  <ItemGroup>
    <Compile Include="..\MyWPFApp\**\*.cs" Exclude="..\MyWPFApp\obj\**" />
    <None Include="..\MyWPFApp\**\*.settings" />
    <EmbeddedResource Include="..\MyWPFApp\**\*.resx" />
  </ItemGroup>
```

<span data-ttu-id="661d5-190">Ardından, başka dahil `<ItemGroup>` içeren düğümü bir `<Page>` girişi için her **xaml** , proje dosyasında **App.xaml** dosya.</span><span class="sxs-lookup"><span data-stu-id="661d5-190">Next, include another `<ItemGroup>` node that contains a `<Page>` entry for every **xaml** file in your project except the **App.xaml** file.</span></span> <span data-ttu-id="661d5-191">Bunlar tüm windows, sayfalar ve bulunan kaynaklar içeren **xaml** biçimi.</span><span class="sxs-lookup"><span data-stu-id="661d5-191">These contain all of the windows, pages, and resources that are in **xaml** format.</span></span> <span data-ttu-id="661d5-192">Glob deseni burada kullanın ve gereken her dosya için bir giriş ekleyemez ve belirtmek `<Generator>` kullanılır.</span><span class="sxs-lookup"><span data-stu-id="661d5-192">You cannot use a glob pattern here and must add an entry for every file and indicate the `<Generator>` used.</span></span>

```xml
  <ItemGroup>
    <Page Include="..\MyWPFApp\MainWindow.xaml">
      <Generator>MSBuild:Compile</Generator>
    </Page>
  </ItemGroup>
```

## <a name="add-nuget-packages"></a><span data-ttu-id="661d5-193">NuGet paketleri Ekle</span><span class="sxs-lookup"><span data-stu-id="661d5-193">Add NuGet packages</span></span>

<span data-ttu-id="661d5-194">.NET Core projesi .NET Framework proje tarafından başvurulan her NuGet paketini ekleyin.</span><span class="sxs-lookup"><span data-stu-id="661d5-194">Add each NuGet package referenced by the .NET Framework project to the .NET Core project.</span></span> 

<span data-ttu-id="661d5-195">Büyük olasılıkla .NET Framework WPF uygulamanızı sahip bir **packages.config** projeniz tarafından başvurulan NuGet paketlerinin bir listesini içeren dosya.</span><span class="sxs-lookup"><span data-stu-id="661d5-195">Most likely your .NET Framework WPF app has a **packages.config** file that contains a list of all of the NuGet packages that are referenced by your project.</span></span> <span data-ttu-id="661d5-196">.NET Core projesine eklemek için hangi NuGet paketlerini belirlemek için bu listeye bakabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="661d5-196">You can look at this list to determine which NuGet packages to add to the .NET Core project.</span></span> <span data-ttu-id="661d5-197">Örneğin, .NET Framework projesinin başvuruyorsa `MahApps.Metro` NuGet paketi, Visual Studio ile projeye ekleyin.</span><span class="sxs-lookup"><span data-stu-id="661d5-197">For example, if the .NET Framework project references the `MahApps.Metro` NuGet package, add it to the project with Visual Studio.</span></span> <span data-ttu-id="661d5-198">.NET Core CLI üzerinden sahip paket başvurusu da ekleyebilirsiniz **SolutionFolder** dizini:</span><span class="sxs-lookup"><span data-stu-id="661d5-198">You can also add the package reference with the .NET Core CLI from the **SolutionFolder** directory:</span></span>

```cli
dotnet add .\MyWPFAppCore\MyWPFCore.csproj package MahApps.Metro -v 2.0.0-alpha0262
```

<span data-ttu-id="661d5-199">Önceki komutta aşağıdaki NuGet başvuru eklersiniz **MyWPFCore.csproj** proje:</span><span class="sxs-lookup"><span data-stu-id="661d5-199">The previous command would add the following NuGet reference to the **MyWPFCore.csproj** project:</span></span>

```xml
  <ItemGroup>
    <PackageReference Include="MahApps.Metro" Version="2.0.0-alpha0262" />
  </ItemGroup>
```

## <a name="problems-compiling"></a><span data-ttu-id="661d5-200">Derleme sorunları</span><span class="sxs-lookup"><span data-stu-id="661d5-200">Problems compiling</span></span>

<span data-ttu-id="661d5-201">Projelerinizi derleme sorunlarla karşılaşırsanız, .NET Framework'de kullanılabilen ancak .NET core'da kullanılamaz olan bazı yalnızca Windows API'leri kullanıyor olabilir.</span><span class="sxs-lookup"><span data-stu-id="661d5-201">If you have problems compiling your projects, you may be using some Windows-only APIs that are available in .NET Framework but not available in .NET Core.</span></span> <span data-ttu-id="661d5-202">Eklemeyi deneyin [Windows Uyumluluk Paketi] [ compat-pack] NuGet paketini projenize.</span><span class="sxs-lookup"><span data-stu-id="661d5-202">You can try adding the [Windows Compatibility Pack][compat-pack] NuGet package to your project.</span></span> <span data-ttu-id="661d5-203">Bu paket, yalnızca Windows üzerinde çalışır ve yaklaşık 20.000 Windows API'leri, .NET Core ve .NET Standard projelerine ekler.</span><span class="sxs-lookup"><span data-stu-id="661d5-203">This package only runs on Windows and adds about 20,000 Windows APIs to .NET Core and .NET Standard projects.</span></span>

```cli
dotnet add .\MyWPFAppCore\MyWPFCore.csproj package Microsoft.Windows.Compatibility
```

<span data-ttu-id="661d5-204">Önceki komutta aşağıdaki ekler **MyWPFCore.csproj** proje:</span><span class="sxs-lookup"><span data-stu-id="661d5-204">The previous command adds the following to the **MyWPFCore.csproj** project:</span></span>

```xml
  <ItemGroup>
    <PackageReference Include="Microsoft.Windows.Compatibility" Version="2.0.1" />
  </ItemGroup>
```

## <a name="wpf-designer"></a><span data-ttu-id="661d5-205">WPF Tasarımcısı</span><span class="sxs-lookup"><span data-stu-id="661d5-205">WPF Designer</span></span>

<span data-ttu-id="661d5-206">Ayrıntılı olarak açıklanan bu makalede, Visual Studio 2019 yalnızca WPF Tasarımcısı .NET Framework projelerinde destekler.</span><span class="sxs-lookup"><span data-stu-id="661d5-206">As detailed in this article, Visual Studio 2019 only supports the WPF Designer in .NET Framework projects.</span></span> <span data-ttu-id="661d5-207">Yan yana .NET Core projesi oluşturarak, .NET Framework projesinin tasarım formlara kullanırken projeniz .NET Core ile test edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="661d5-207">By creating a side-by-side .NET Core project, you can test your project with .NET Core while you use the .NET Framework project to design forms.</span></span> <span data-ttu-id="661d5-208">Çözüm dosyanız .NET Framework ve .NET Core projeleri içerir.</span><span class="sxs-lookup"><span data-stu-id="661d5-208">Your solution file includes both the .NET Framework and .NET Core projects.</span></span> <span data-ttu-id="661d5-209">Ekleme, formlar ve denetimler .NET Framework projesinde tasarım ve üzerinde dosya glob desenlerinin ekledik .NET Core projeleri için herhangi bir yeni veya değiştirilen dosyaları otomatik olarak .NET Core projelerinde dahil edilir.</span><span class="sxs-lookup"><span data-stu-id="661d5-209">Add and design your forms and controls in the .NET Framework project, and based on the file glob patterns we added to the .NET Core projects, any new or changed files will automatically be included in the .NET Core projects.</span></span>

<span data-ttu-id="661d5-210">Visual Studio 2019 WPF Tasarımcısı destekler. sonra kopyalama/.NET Core proje dosyanızın içeriğini .NET Framework proje dosyasına yapıştırma.</span><span class="sxs-lookup"><span data-stu-id="661d5-210">Once Visual Studio 2019 supports the WPF Designer, you can copy/paste the content of your .NET Core project file into the .NET Framework project file.</span></span> <span data-ttu-id="661d5-211">Eklenen dosya glob desenlerinin delete `<Source>` ve `<EmbeddedResource>` öğeleri.</span><span class="sxs-lookup"><span data-stu-id="661d5-211">Then delete the file glob patterns added with the `<Source>` and `<EmbeddedResource>` items.</span></span> <span data-ttu-id="661d5-212">Uygulamanız tarafından kullanılan herhangi bir proje başvurusu yolları düzeltin.</span><span class="sxs-lookup"><span data-stu-id="661d5-212">Fix the paths to any project reference used by your app.</span></span> <span data-ttu-id="661d5-213">Bu .NET Framework projesi bir .NET Core projesinden etkili bir şekilde yükseltir.</span><span class="sxs-lookup"><span data-stu-id="661d5-213">This effectively upgrades the .NET Framework project to a .NET Core project.</span></span>
 
## <a name="next-steps"></a><span data-ttu-id="661d5-214">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="661d5-214">Next steps</span></span>

* <span data-ttu-id="661d5-215">Daha fazla bilgi edinin [Windows Uyumluluk Paketi][compat-pack].</span><span class="sxs-lookup"><span data-stu-id="661d5-215">Read more about the [Windows Compatibility Pack][compat-pack].</span></span>
* <span data-ttu-id="661d5-216">İzleme bir [taşıma video](https://www.youtube.com/watch?v=5MomsgkWkVw&list=PLS__JrkRveTMiWxG-Lv4cBwYfMQ6m2gmt) .NET Core, .NET Framework WPF projesi.</span><span class="sxs-lookup"><span data-stu-id="661d5-216">Watch a [video on porting](https://www.youtube.com/watch?v=5MomsgkWkVw&list=PLS__JrkRveTMiWxG-Lv4cBwYfMQ6m2gmt) your .NET Framework WPF project to .NET Core.</span></span>

[compat-pack]: windows-compat-pack.md
