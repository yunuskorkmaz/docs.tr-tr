---
title: Bir WPF uygulamasının .NET Core 3,0 bağlantı noktası
description: .NET Framework Windows Presentation Foundation uygulamasının Windows için .NET Core 3,0 'e nasıl bağlantı alınacağını öğretir.
author: Thraka
ms.author: adegeo
ms.date: 03/27/2019
ms.custom: ''
ms.openlocfilehash: 1528e578a978de38998b3f3f4b7beb72ff7422d4
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/19/2019
ms.locfileid: "71117065"
---
# <a name="how-to-port-a-wpf-desktop-app-to-net-core"></a><span data-ttu-id="27c88-103">Nasıl yapılır: .NET Core 'a bir WPF Masaüstü uygulaması bağlantı noktası</span><span class="sxs-lookup"><span data-stu-id="27c88-103">How to: Port a WPF desktop app to .NET Core</span></span>

<span data-ttu-id="27c88-104">Bu makalede, .NET Framework Windows Presentation Foundation tabanlı (WPF) Masaüstü uygulamanızın .NET Core 3,0 ' ye nasıl bağlantı kurulacağı açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="27c88-104">This article describes how to port your Windows Presentation Foundation-based (WPF) desktop app from .NET Framework to .NET Core 3.0.</span></span> <span data-ttu-id="27c88-105">.NET Core 3,0 SDK, WPF uygulamaları için destek içerir.</span><span class="sxs-lookup"><span data-stu-id="27c88-105">The .NET Core 3.0 SDK includes support for WPF applications.</span></span> <span data-ttu-id="27c88-106">WPF hala yalnızca Windows Framework 'ü ve Windows üzerinde çalışır.</span><span class="sxs-lookup"><span data-stu-id="27c88-106">WPF is still a Windows-only framework and only runs on Windows.</span></span> <span data-ttu-id="27c88-107">Bu örnek, projenizi oluşturmak ve yönetmek için .NET Core SDK CLı kullanır.</span><span class="sxs-lookup"><span data-stu-id="27c88-107">This example uses the .NET Core SDK CLI to create and manage your project.</span></span>

<span data-ttu-id="27c88-108">Bu makalede, geçiş için kullanılan dosya türlerini tanımlamak için çeşitli adlar kullanılır.</span><span class="sxs-lookup"><span data-stu-id="27c88-108">In this article, various names are used to identify types of files used for migration.</span></span> <span data-ttu-id="27c88-109">Projeniz geçirilirken dosyalarınız farklı şekilde adlandırılır, bu sayede bunları aşağıda listelenen adlarla eşleştirin:</span><span class="sxs-lookup"><span data-stu-id="27c88-109">When migrating your project, your files will be named differently, so mentally match them to the ones listed below:</span></span>

| <span data-ttu-id="27c88-110">Dosya</span><span class="sxs-lookup"><span data-stu-id="27c88-110">File</span></span> | <span data-ttu-id="27c88-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="27c88-111">Description</span></span> |
| ---- | ----------- |
| <span data-ttu-id="27c88-112">**Uygps. sln**</span><span class="sxs-lookup"><span data-stu-id="27c88-112">**MyApps.sln**</span></span> | <span data-ttu-id="27c88-113">Çözüm dosyasının adı.</span><span class="sxs-lookup"><span data-stu-id="27c88-113">The name of the solution file.</span></span> |
| <span data-ttu-id="27c88-114">**MyWPF. csproj**</span><span class="sxs-lookup"><span data-stu-id="27c88-114">**MyWPF.csproj**</span></span> | <span data-ttu-id="27c88-115">Bağlantı noktasına .NET Framework WPF projesinin adı.</span><span class="sxs-lookup"><span data-stu-id="27c88-115">The name of the .NET Framework WPF project to port.</span></span> |
| <span data-ttu-id="27c88-116">**MyWPFCore. csproj**</span><span class="sxs-lookup"><span data-stu-id="27c88-116">**MyWPFCore.csproj**</span></span> | <span data-ttu-id="27c88-117">Oluşturduğunuz yeni .NET Core projesinin adı.</span><span class="sxs-lookup"><span data-stu-id="27c88-117">The name of the new .NET Core project you create.</span></span> |
| <span data-ttu-id="27c88-118">**MyAppCore. exe**</span><span class="sxs-lookup"><span data-stu-id="27c88-118">**MyAppCore.exe**</span></span> | <span data-ttu-id="27c88-119">.NET Core WPF uygulaması yürütülebilir dosyası.</span><span class="sxs-lookup"><span data-stu-id="27c88-119">The .NET Core WPF app executable.</span></span> |

>[!IMPORTANT]
><span data-ttu-id="27c88-120">Bu makalede C# hedef dil olarak kullanılsa da, vb.net, sırasıyla. *csproj* ve. *CS* dosyaları yerine *. vbproj* ve. *vb* dosyalarını kullanması dışında, vb.NET için de aynıdır.</span><span class="sxs-lookup"><span data-stu-id="27c88-120">Even though this article uses C# as the target language, the steps are the same for VB.NET, except that VB.NET uses *.vbproj* and *.vb* files instead of *.csproj* and *.cs* files, respectively.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="27c88-121">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="27c88-121">Prerequisites</span></span>

- <span data-ttu-id="27c88-122">İstediğiniz tasarımcı çalışması için [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) .</span><span class="sxs-lookup"><span data-stu-id="27c88-122">[Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) for any designer work you want to do.</span></span>

  <span data-ttu-id="27c88-123">Aşağıdaki Visual Studio iş yüklerini yükler:</span><span class="sxs-lookup"><span data-stu-id="27c88-123">Install the following Visual Studio workloads:</span></span>
  - <span data-ttu-id="27c88-124">.NET masaüstü geliştirme</span><span class="sxs-lookup"><span data-stu-id="27c88-124">.NET desktop development</span></span>
  - <span data-ttu-id="27c88-125">.NET platformlar arası geliştirme</span><span class="sxs-lookup"><span data-stu-id="27c88-125">.NET cross-platform development</span></span>

- <span data-ttu-id="27c88-126">Sorun olmadan oluşturulup çalışan bir çözümde çalışan bir WPF projesi.</span><span class="sxs-lookup"><span data-stu-id="27c88-126">A working WPF project in a solution that builds and runs without issue.</span></span>
- <span data-ttu-id="27c88-127">En son [.NET Core 3,0](https://aka.ms/netcore3download) önizlemeyi yükler.</span><span class="sxs-lookup"><span data-stu-id="27c88-127">Install the latest [.NET Core 3.0](https://aka.ms/netcore3download) preview.</span></span>

>[!NOTE]
><span data-ttu-id="27c88-128">**Visual Studio 2017** , .net Core 3,0 projelerini desteklemez.</span><span class="sxs-lookup"><span data-stu-id="27c88-128">**Visual Studio 2017** doesn't support .NET Core 3.0 projects.</span></span> <span data-ttu-id="27c88-129">**Visual Studio 2019** , .net Core 3,0 projelerini destekler, ancak .NET Core WPF görsel Tasarımcısı için sınırlı destek içerir.</span><span class="sxs-lookup"><span data-stu-id="27c88-129">**Visual Studio 2019** supports .NET Core 3.0 projects but has limited support for the .NET Core WPF visual designer.</span></span> <span data-ttu-id="27c88-130">Tam olarak desteklenen bir görsel tasarımcı kullanmak için, çözümünüzde dosyalarını .NET Core projesiyle paylaşan bir .NET Framework WPF projeniz olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="27c88-130">To use a fully-supported visual designer, you must have a .NET Framework WPF project in your solution that shares its files with the .NET Core project.</span></span>

### <a name="consider"></a><span data-ttu-id="27c88-131">Seçmeyi</span><span class="sxs-lookup"><span data-stu-id="27c88-131">Consider</span></span>

<span data-ttu-id="27c88-132">.NET Framework WPF uygulaması taşıma sırasında göz önünde bulundurmanız gereken birkaç nokta vardır.</span><span class="sxs-lookup"><span data-stu-id="27c88-132">When porting a .NET Framework WPF application, there are a few things you must consider.</span></span>

01. <span data-ttu-id="27c88-133">Uygulamanızın geçiş için iyi bir aday olduğunu kontrol edin.</span><span class="sxs-lookup"><span data-stu-id="27c88-133">Check that your application is a good candidate for migration.</span></span>

    <span data-ttu-id="27c88-134">Projenizin .NET Core 3,0 ' e geçiş olacağını öğrenmek için [.net taşınabilirlik Çözümleyicisi](../../standard/analyzers/portability-analyzer.md) ' ni kullanın.</span><span class="sxs-lookup"><span data-stu-id="27c88-134">Use the [.NET Portability Analyzer](../../standard/analyzers/portability-analyzer.md) to determine if your project will migrate to .NET Core 3.0.</span></span> <span data-ttu-id="27c88-135">Projenizde .NET Core 3,0 ile ilgili sorunlar varsa, çözümleyici bu sorunları belirlemenize yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="27c88-135">If your project has issues with .NET Core 3.0, the analyzer helps you identify those problems.</span></span>

01. <span data-ttu-id="27c88-136">Farklı bir WPF sürümü kullanıyorsunuz.</span><span class="sxs-lookup"><span data-stu-id="27c88-136">You're using a different version of WPF.</span></span>

    <span data-ttu-id="27c88-137">.NET Core 3,0 Preview 1 yayınlanmışsa, WPF GitHub üzerinde açık kaynak olarak çıktı.</span><span class="sxs-lookup"><span data-stu-id="27c88-137">When .NET Core 3.0 Preview 1 was released, WPF went open-source on GitHub.</span></span> <span data-ttu-id="27c88-138">.NET Core WPF kodu, .NET Framework WPF kod tabanının çatalından oluşur.</span><span class="sxs-lookup"><span data-stu-id="27c88-138">The code for .NET Core WPF is a fork of the .NET Framework WPF code base.</span></span> <span data-ttu-id="27c88-139">Bazı farklılıklar olabilir ve uygulamanızın bağlantı noktası olmayacaktır.</span><span class="sxs-lookup"><span data-stu-id="27c88-139">It's possible some differences exist and your app won't port.</span></span>

01. <span data-ttu-id="27c88-140">[Windows Uyumluluk Paketi][compat-pack] , geçiş yapmanıza yardımcı olabilir.</span><span class="sxs-lookup"><span data-stu-id="27c88-140">The [Windows Compatibility Pack][compat-pack] may help you migrate.</span></span>

    <span data-ttu-id="27c88-141">.NET Framework ' de kullanılabilen bazı API 'Ler .NET Core 3,0 ' de kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="27c88-141">Some APIs that are available in .NET Framework aren't available in .NET Core 3.0.</span></span> <span data-ttu-id="27c88-142">[Windows Uyumluluk Paketi][compat-pack] bu API 'lerin çoğunu ekler ve WPF uygulamanızın .NET Core ile uyumlu olmasına yardımcı olabilir.</span><span class="sxs-lookup"><span data-stu-id="27c88-142">The [Windows Compatibility Pack][compat-pack] adds many of these APIs and may help your WPF app become compatible with .NET Core.</span></span>

01. <span data-ttu-id="27c88-143">Projeniz tarafından kullanılan NuGet paketlerini güncelleştirin.</span><span class="sxs-lookup"><span data-stu-id="27c88-143">Update the NuGet packages used by your project.</span></span>

    <span data-ttu-id="27c88-144">Herhangi bir geçişten önce NuGet paketlerinin en son sürümlerini kullanmak her zaman iyi bir uygulamadır.</span><span class="sxs-lookup"><span data-stu-id="27c88-144">It's always a good practice to use the latest versions of NuGet packages before any migration.</span></span> <span data-ttu-id="27c88-145">Uygulamanız herhangi bir NuGet paketine başvuruyorsa, bunları en son sürüme güncelleştirin.</span><span class="sxs-lookup"><span data-stu-id="27c88-145">If your application is referencing any NuGet packages, update them to the latest version.</span></span> <span data-ttu-id="27c88-146">Uygulamanızın başarıyla derlemediğinden emin olun.</span><span class="sxs-lookup"><span data-stu-id="27c88-146">Ensure your application builds successfully.</span></span> <span data-ttu-id="27c88-147">Yükseltmeden sonra, herhangi bir paket hatası varsa, paketi, kodunuzu kesen en son sürüme indirgeymelisiniz.</span><span class="sxs-lookup"><span data-stu-id="27c88-147">After upgrading, if there are any package errors, downgrade the package to the latest version that doesn't break your code.</span></span>

01. <span data-ttu-id="27c88-148">Visual Studio 2019 henüz .NET Core 3,0 için WPF tasarımcısını desteklemiyor</span><span class="sxs-lookup"><span data-stu-id="27c88-148">Visual Studio 2019 doesn't yet support the WPF Designer for .NET Core 3.0</span></span>

    <span data-ttu-id="27c88-149">Şu anda, Visual Studio 'da WPF tasarımcısını kullanmak istiyorsanız mevcut .NET Framework WPF proje dosyanızı saklamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="27c88-149">Currently, you need to keep your existing .NET Framework WPF project file if you want to use the WPF Designer from Visual Studio.</span></span>

## <a name="create-a-new-sdk-project"></a><span data-ttu-id="27c88-150">Yeni bir SDK projesi oluştur</span><span class="sxs-lookup"><span data-stu-id="27c88-150">Create a new SDK project</span></span>

<span data-ttu-id="27c88-151">Oluşturduğunuz yeni .NET Core 3,0 projesi .NET Framework projenizden farklı bir dizinde olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="27c88-151">The new .NET Core 3.0 project you create must be in a different directory from your .NET Framework project.</span></span> <span data-ttu-id="27c88-152">İkisi de aynı dizinde ise, **obj** dizininde oluşturulan dosyalarla çakışmalarıyla karşılaşabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="27c88-152">If they're both in the same directory, you may run into conflicts with the files that are generated in the **obj** directory.</span></span> <span data-ttu-id="27c88-153">Bu örnekte, **SolutionFolder** dizininde **MyWPFAppCore** adlı bir dizin oluşturacaksınız:</span><span class="sxs-lookup"><span data-stu-id="27c88-153">In this example, you'll create a directory named **MyWPFAppCore** in the **SolutionFolder** directory:</span></span>

```
SolutionFolder
├───MyApps.sln
├───MyWPFApp
│   └───MyWPF.csproj
└───MyWPFAppCore      <--- New folder for core project
```

<span data-ttu-id="27c88-154">Sonra, **MyWPFAppCore** dizininde **mywpfcore. csproj** projesini oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="27c88-154">Next, you need to create the **MyWPFCore.csproj** project in the **MyWPFAppCore** directory.</span></span> <span data-ttu-id="27c88-155">Bu dosyayı tercih ettiğiniz metin düzenleyicisini kullanarak el ile oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="27c88-155">You can create this file manually by using the text editor of choice.</span></span> <span data-ttu-id="27c88-156">Aşağıdaki XML 'e yapıştırın:</span><span class="sxs-lookup"><span data-stu-id="27c88-156">Paste in the following XML:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk.WindowsDesktop">

  <PropertyGroup>
    <OutputType>WinExe</OutputType>
    <TargetFramework>netcoreapp3.0</TargetFramework>
    <UseWPF>true</UseWPF>
  </PropertyGroup>

</Project>
```

<span data-ttu-id="27c88-157">Proje dosyasını el ile oluşturmak istemiyorsanız, projeyi oluşturmak için Visual Studio 'Yu veya .NET Core SDK kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="27c88-157">If you don't want to create the project file manually, you can use Visual Studio or the .NET Core SDK to generate the project.</span></span> <span data-ttu-id="27c88-158">Ancak proje dosyası hariç proje şablonu tarafından oluşturulan diğer tüm dosyaları silmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="27c88-158">However, you must delete all other files generated by the project template except for the project file.</span></span> <span data-ttu-id="27c88-159">SDK 'yı kullanmak için **SolutionFolder** dizininden aşağıdaki komutu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="27c88-159">To use the SDK, run the following command from the **SolutionFolder** directory:</span></span>

```dotnetcli
dotnet new wpf -o MyWPFAppCore -n MyWPFCore
```

<span data-ttu-id="27c88-160">**Mywpfcore. csproj**öğesini oluşturduktan sonra, dizin yapınız aşağıdaki gibi görünmelidir:</span><span class="sxs-lookup"><span data-stu-id="27c88-160">After you create the **MyWPFCore.csproj**, your directory structure should look like the following:</span></span>

```
SolutionFolder
├───MyApps.sln
├───MyWPFApp
│   └───MyWPF.csproj
└───MyWPFAppCore
    └───MyWPFCore.csproj
```

<span data-ttu-id="27c88-161">Visual Studio ya da **SolutionFolder** dizininden .NET Core CLI **mywpfcore. csproj** projesini **uygulamaps. sln** ' ye eklemek isteyeceksiniz:</span><span class="sxs-lookup"><span data-stu-id="27c88-161">You'll want to add the **MyWPFCore.csproj** project to **MyApps.sln** with either Visual Studio or the .NET Core CLI from the **SolutionFolder** directory:</span></span>

```dotnetcli
dotnet sln add .\MyWPFAppCore\MyWPFCore.csproj
```

## <a name="fix-assembly-info-generation"></a><span data-ttu-id="27c88-162">Derleme bilgileri oluşturmayı çözme</span><span class="sxs-lookup"><span data-stu-id="27c88-162">Fix assembly info generation</span></span>

<span data-ttu-id="27c88-163">.NET Framework ile oluşturulan Windows Presentation Foundation projeler, oluşturulacak derlemenin sürümü `AssemblyInfo.cs` gibi derleme özniteliklerini içeren bir dosya içerir.</span><span class="sxs-lookup"><span data-stu-id="27c88-163">Windows Presentation Foundation projects that were created with .NET Framework include an `AssemblyInfo.cs` file, which contains assembly attributes such as the version of the assembly to be generated.</span></span> <span data-ttu-id="27c88-164">SDK stilindeki projeler, SDK proje dosyasını temel alarak bu bilgileri sizin için otomatik olarak oluşturur.</span><span class="sxs-lookup"><span data-stu-id="27c88-164">SDK-style projects automatically generate this information for you based on the SDK project file.</span></span> <span data-ttu-id="27c88-165">Her iki tür "derleme bilgisi" de bir çakışma oluşturur.</span><span class="sxs-lookup"><span data-stu-id="27c88-165">Having both types of "assembly info" creates a conflict.</span></span> <span data-ttu-id="27c88-166">Otomatik oluşturmayı devre dışı bırakarak bu sorunu çözün. Bu, projeyi mevcut `AssemblyInfo.cs` dosyanızı kullanmaya zorlar.</span><span class="sxs-lookup"><span data-stu-id="27c88-166">Resolve this problem by disabling automatic generation, which forces the project to use your existing `AssemblyInfo.cs` file.</span></span>

<span data-ttu-id="27c88-167">Ana `<PropertyGroup>` düğüme eklemenin üç ayarı vardır.</span><span class="sxs-lookup"><span data-stu-id="27c88-167">There are three settings to add to the main `<PropertyGroup>` node.</span></span> 

- <span data-ttu-id="27c88-168">**Generateassemblyınfo**</span><span class="sxs-lookup"><span data-stu-id="27c88-168">**GenerateAssemblyInfo**</span></span>\
<span data-ttu-id="27c88-169">Bu özelliği `false`' a ayarladığınızda, derleme özniteliklerini oluşturmaz.</span><span class="sxs-lookup"><span data-stu-id="27c88-169">When you set this property to `false`, it won't generate the assembly attributes.</span></span> <span data-ttu-id="27c88-170">Bu, .NET Framework projesinden mevcut `AssemblyInfo.cs` dosya ile çakışmayı önler.</span><span class="sxs-lookup"><span data-stu-id="27c88-170">This avoids the conflict with the existing `AssemblyInfo.cs` file from the .NET Framework project.</span></span>

- <span data-ttu-id="27c88-171">**AssemblyName**</span><span class="sxs-lookup"><span data-stu-id="27c88-171">**AssemblyName**</span></span>\
<span data-ttu-id="27c88-172">Bu özelliğin değeri, derlerken oluşturulan çıkış ikilisi olur.</span><span class="sxs-lookup"><span data-stu-id="27c88-172">The value of this property is the output binary created when you compile.</span></span> <span data-ttu-id="27c88-173">Ada eklenen bir uzantıya gerek yoktur.</span><span class="sxs-lookup"><span data-stu-id="27c88-173">The name doesn't need an extension added to it.</span></span> <span data-ttu-id="27c88-174">Örneğin, kullanılarak `MyCoreApp` üretir `MyCoreApp.exe`.</span><span class="sxs-lookup"><span data-stu-id="27c88-174">For example, using `MyCoreApp` produces `MyCoreApp.exe`.</span></span>

- <span data-ttu-id="27c88-175">**RootNamespace**</span><span class="sxs-lookup"><span data-stu-id="27c88-175">**RootNamespace**</span></span>\
<span data-ttu-id="27c88-176">Projeniz tarafından kullanılan varsayılan ad alanı.</span><span class="sxs-lookup"><span data-stu-id="27c88-176">The default namespace used by your project.</span></span> <span data-ttu-id="27c88-177">Bu, .NET Framework projesinin varsayılan ad alanıyla eşleşmelidir.</span><span class="sxs-lookup"><span data-stu-id="27c88-177">This should match the default namespace of the .NET Framework project.</span></span>

<span data-ttu-id="27c88-178">Bu üç öğeyi `<PropertyGroup>` `MyWPFCore.csproj` dosyadaki düğümüne ekleyin:</span><span class="sxs-lookup"><span data-stu-id="27c88-178">Add these three elements to the `<PropertyGroup>` node in the `MyWPFCore.csproj` file:</span></span>

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

## <a name="add-source-code"></a><span data-ttu-id="27c88-179">Kaynak kodu ekle</span><span class="sxs-lookup"><span data-stu-id="27c88-179">Add source code</span></span>
<span data-ttu-id="27c88-180">Şu anda **Mywpfcore. csproj** projesi hiçbir kodu derlemez.</span><span class="sxs-lookup"><span data-stu-id="27c88-180">Right now, the **MyWPFCore.csproj** project doesn't compile any code.</span></span> <span data-ttu-id="27c88-181">Varsayılan olarak, .NET Core projeleri geçerli dizine ve tüm alt dizinlere tüm kaynak kodlarını otomatik olarak ekler.</span><span class="sxs-lookup"><span data-stu-id="27c88-181">By default, .NET Core projects automatically include all source code in the current directory and any child directories.</span></span> <span data-ttu-id="27c88-182">Projeyi, .NET Framework projesinden bir göreli yol kullanarak kod içerecek şekilde yapılandırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="27c88-182">You must configure the project to include code from the .NET Framework project using a relative path.</span></span> <span data-ttu-id="27c88-183">.NET Framework projeniz Windows ve denetimlerinizin simgeleri ve kaynakları için **. resx** dosyalarını kullandıysanız, bunları da eklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="27c88-183">If your .NET Framework project used **.resx** files for icons and resources for your windows and controls, you'll need to include those too.</span></span> 

<span data-ttu-id="27c88-184">Projenize eklemeniz `<ItemGroup>` gereken ilk düğüm, uygulamanızın kullandığı başlangıç yapılandırmasını ve kaynaklarını temsil eden **app. xaml** dosyasını içerir.</span><span class="sxs-lookup"><span data-stu-id="27c88-184">The first `<ItemGroup>` node you need to add to your project includes the **App.xaml** file that represents the startup config and resources your app uses.</span></span> <span data-ttu-id="27c88-185">**App. xaml** dosyasında Ayrıca eşlik eden bir **app.xaml.cs** dosyası bulunur, ancak otomatik olarak farklı `<ItemGroup>`bir şekilde dahil edilir.</span><span class="sxs-lookup"><span data-stu-id="27c88-185">The **App.xaml** file also has an accompanying **App.xaml.cs** file, but it will be automatically included in a different `<ItemGroup>`.</span></span>

```xml
  <ItemGroup>
    <ApplicationDefinition Include="..\MyWPFApp\App.xaml">
      <Generator>MSBuild:Compile</Generator>
    </ApplicationDefinition>
  </ItemGroup>
```

<span data-ttu-id="27c88-186">Ardından, aşağıdaki `<ItemGroup>` düğümü projenize ekleyin.</span><span class="sxs-lookup"><span data-stu-id="27c88-186">Next, add the following `<ItemGroup>` node to your project.</span></span> <span data-ttu-id="27c88-187">Her bir bildirimde alt dizinler içeren bir dosya glob kalıbı bulunur.</span><span class="sxs-lookup"><span data-stu-id="27c88-187">Each statement includes a file glob pattern that includes child directories.</span></span> <span data-ttu-id="27c88-188">Projeniz, herhangi bir ayar dosyası ve tüm kaynaklar için kaynak kodunu içerir.</span><span class="sxs-lookup"><span data-stu-id="27c88-188">It includes the source code for your project, any settings files, and any resources.</span></span> <span data-ttu-id="27c88-189">**Obj** dizini açıkça dışarıda bırakılır.</span><span class="sxs-lookup"><span data-stu-id="27c88-189">The **obj** directory is explicitly excluded.</span></span>

```xml
  <ItemGroup>
    <Compile Include="..\MyWPFApp\**\*.cs" Exclude="..\MyWPFApp\obj\**" />
    <None Include="..\MyWPFApp\**\*.settings" />
    <EmbeddedResource Include="..\MyWPFApp\**\*.resx" />
  </ItemGroup>
```

<span data-ttu-id="27c88-190">Daha sonra, **app. xaml** dosyası hariç `<Page>` , projenizdeki her **xaml** dosyası için bir giriş içeren başka bir `<ItemGroup>` düğüm ekleyin.</span><span class="sxs-lookup"><span data-stu-id="27c88-190">Next, include another `<ItemGroup>` node that contains a `<Page>` entry for every **xaml** file in your project except the **App.xaml** file.</span></span> <span data-ttu-id="27c88-191">Bunlar **xaml** biçiminde olan tüm Windows, sayfa ve kaynakları içerir.</span><span class="sxs-lookup"><span data-stu-id="27c88-191">These contain all of the windows, pages, and resources that are in **xaml** format.</span></span> <span data-ttu-id="27c88-192">Burada bir glob modelini kullanamazsınız ve her dosya için bir giriş eklemeli ve `<Generator>` kullanılan ' i belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="27c88-192">You cannot use a glob pattern here and must add an entry for every file and indicate the `<Generator>` used.</span></span>

```xml
  <ItemGroup>
    <Page Include="..\MyWPFApp\MainWindow.xaml">
      <Generator>MSBuild:Compile</Generator>
    </Page>
  </ItemGroup>
```

## <a name="add-nuget-packages"></a><span data-ttu-id="27c88-193">NuGet paketleri Ekle</span><span class="sxs-lookup"><span data-stu-id="27c88-193">Add NuGet packages</span></span>

<span data-ttu-id="27c88-194">.NET Framework projesi tarafından başvurulan her bir NuGet paketini .NET Core projesine ekleyin.</span><span class="sxs-lookup"><span data-stu-id="27c88-194">Add each NuGet package referenced by the .NET Framework project to the .NET Core project.</span></span> 

<span data-ttu-id="27c88-195">Büyük olasılıkla .NET Framework WPF uygulamanız, projeniz tarafından başvurulan tüm NuGet paketlerinin listesini içeren bir **Packages. config** dosyasına sahiptir.</span><span class="sxs-lookup"><span data-stu-id="27c88-195">Most likely your .NET Framework WPF app has a **packages.config** file that contains a list of all of the NuGet packages that are referenced by your project.</span></span> <span data-ttu-id="27c88-196">.NET Core projesine hangi NuGet paketlerinin ekleneceğini öğrenmek için bu listeye bakabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="27c88-196">You can look at this list to determine which NuGet packages to add to the .NET Core project.</span></span> <span data-ttu-id="27c88-197">Örneğin, .NET Framework projesi `MahApps.Metro` NuGet paketine başvuruyorsa, Visual Studio ile projeye ekleyin.</span><span class="sxs-lookup"><span data-stu-id="27c88-197">For example, if the .NET Framework project references the `MahApps.Metro` NuGet package, add it to the project with Visual Studio.</span></span> <span data-ttu-id="27c88-198">Ayrıca, **SolutionFolder** dizininden .NET Core CLI paket başvurusunu ekleyebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="27c88-198">You can also add the package reference with the .NET Core CLI from the **SolutionFolder** directory:</span></span>

```dotnetcli
dotnet add .\MyWPFAppCore\MyWPFCore.csproj package MahApps.Metro -v 2.0.0-alpha0262
```

<span data-ttu-id="27c88-199">Önceki komut **Mywpfcore. csproj** projesine aşağıdaki NuGet başvurusunu ekler:</span><span class="sxs-lookup"><span data-stu-id="27c88-199">The previous command would add the following NuGet reference to the **MyWPFCore.csproj** project:</span></span>

```xml
  <ItemGroup>
    <PackageReference Include="MahApps.Metro" Version="2.0.0-alpha0262" />
  </ItemGroup>
```

## <a name="problems-compiling"></a><span data-ttu-id="27c88-200">Derleme sorunları</span><span class="sxs-lookup"><span data-stu-id="27c88-200">Problems compiling</span></span>

<span data-ttu-id="27c88-201">Projelerinizi derlerken sorunlarla karşılaşırsanız, .NET Core 'da .NET Framework, ancak kullanılamayan yalnızca Windows salt Windows API 'Lerini kullanıyor olabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="27c88-201">If you have problems compiling your projects, you may be using some Windows-only APIs that are available in .NET Framework but not available in .NET Core.</span></span> <span data-ttu-id="27c88-202">[Windows Uyumluluk Paketi][compat-pack] NuGet paketini projenize eklemeyi deneyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="27c88-202">You can try adding the [Windows Compatibility Pack][compat-pack] NuGet package to your project.</span></span> <span data-ttu-id="27c88-203">Bu paket yalnızca Windows üzerinde çalışır ve .NET Core ve .NET Standard projelerine 20.000 Windows API 'Leri ekler.</span><span class="sxs-lookup"><span data-stu-id="27c88-203">This package only runs on Windows and adds about 20,000 Windows APIs to .NET Core and .NET Standard projects.</span></span>

```dotnetcli
dotnet add .\MyWPFAppCore\MyWPFCore.csproj package Microsoft.Windows.Compatibility
```

<span data-ttu-id="27c88-204">Önceki komut **Mywpfcore. csproj** projesine aşağıdakini ekler:</span><span class="sxs-lookup"><span data-stu-id="27c88-204">The previous command adds the following to the **MyWPFCore.csproj** project:</span></span>

```xml
  <ItemGroup>
    <PackageReference Include="Microsoft.Windows.Compatibility" Version="2.0.1" />
  </ItemGroup>
```

## <a name="wpf-designer"></a><span data-ttu-id="27c88-205">WPF Tasarımcısı</span><span class="sxs-lookup"><span data-stu-id="27c88-205">WPF Designer</span></span>

<span data-ttu-id="27c88-206">Bu makalede açıklandığı gibi, Visual Studio 2019 yalnızca .NET Framework projelerinde WPF tasarımcısını destekler.</span><span class="sxs-lookup"><span data-stu-id="27c88-206">As detailed in this article, Visual Studio 2019 only supports the WPF Designer in .NET Framework projects.</span></span> <span data-ttu-id="27c88-207">Yan yana .NET Core projesi oluşturarak, formları tasarlamak için .NET Framework projesi kullanırken projenizi .NET Core ile test edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="27c88-207">By creating a side-by-side .NET Core project, you can test your project with .NET Core while you use the .NET Framework project to design forms.</span></span> <span data-ttu-id="27c88-208">Çözüm dosyanız hem .NET Framework hem de .NET Core projelerini içerir.</span><span class="sxs-lookup"><span data-stu-id="27c88-208">Your solution file includes both the .NET Framework and .NET Core projects.</span></span> <span data-ttu-id="27c88-209">.NET Framework projesindeki formlarınızı ve denetimlerinizi ekleyin ve tasarlayın ve .NET Core projelerine eklediğimiz dosya glob desenlerine bağlı olarak, .NET Core projelerine yeni veya değiştirilmiş dosyalar otomatik olarak dahil edilir.</span><span class="sxs-lookup"><span data-stu-id="27c88-209">Add and design your forms and controls in the .NET Framework project, and based on the file glob patterns we added to the .NET Core projects, any new or changed files will automatically be included in the .NET Core projects.</span></span>

<span data-ttu-id="27c88-210">Visual Studio 2019 WPF tasarımcısını destekledikten sonra, .NET Core proje dosyanızın içeriğini .NET Framework proje dosyasına kopyalayabilir/yapıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="27c88-210">Once Visual Studio 2019 supports the WPF Designer, you can copy/paste the content of your .NET Core project file into the .NET Framework project file.</span></span> <span data-ttu-id="27c88-211">Sonra `<Source>` ve`<EmbeddedResource>` öğeleriyle eklenen glob düzenlerini silin.</span><span class="sxs-lookup"><span data-stu-id="27c88-211">Then delete the file glob patterns added with the `<Source>` and `<EmbeddedResource>` items.</span></span> <span data-ttu-id="27c88-212">Uygulamanız tarafından kullanılan herhangi bir proje başvurusunun yolunu düzeltin.</span><span class="sxs-lookup"><span data-stu-id="27c88-212">Fix the paths to any project reference used by your app.</span></span> <span data-ttu-id="27c88-213">Bu, .NET Framework projesini bir .NET Core projesine etkin bir şekilde yükseltir.</span><span class="sxs-lookup"><span data-stu-id="27c88-213">This effectively upgrades the .NET Framework project to a .NET Core project.</span></span>

## <a name="next-steps"></a><span data-ttu-id="27c88-214">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="27c88-214">Next steps</span></span>

- <span data-ttu-id="27c88-215">[Windows Uyumluluk Paketi][compat-pack]hakkında daha fazla bilgi edinin.</span><span class="sxs-lookup"><span data-stu-id="27c88-215">Read more about the [Windows Compatibility Pack][compat-pack].</span></span>
- <span data-ttu-id="27c88-216">.NET Framework WPF projenizi .NET Core 'a [taşıma hakkında bir video](https://www.youtube.com/watch?v=5MomsgkWkVw&list=PLS__JrkRveTMiWxG-Lv4cBwYfMQ6m2gmt) izleyin.</span><span class="sxs-lookup"><span data-stu-id="27c88-216">Watch a [video on porting](https://www.youtube.com/watch?v=5MomsgkWkVw&list=PLS__JrkRveTMiWxG-Lv4cBwYfMQ6m2gmt) your .NET Framework WPF project to .NET Core.</span></span>

[compat-pack]: windows-compat-pack.md
