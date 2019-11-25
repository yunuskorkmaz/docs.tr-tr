---
title: .NET Core 3,0 için Windows Forms uygulaması bağlantı noktası
description: .NET Framework Windows Forms uygulamasının Windows için .NET Core 3,0 'e nasıl bağlantı alınacağını öğretir.
author: Thraka
ms.author: adegeo
ms.date: 03/01/2019
ms.custom: ''
ms.openlocfilehash: 64920f1d226fcc8265d0be252d4751f2ba278cc1
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73973284"
---
# <a name="how-to-port-a-windows-forms-desktop-app-to-net-core"></a><span data-ttu-id="56461-103">Windows Forms masaüstü uygulamasının .NET Core 'a bağlantı noktası oluşturma</span><span class="sxs-lookup"><span data-stu-id="56461-103">How to port a Windows Forms desktop app to .NET Core</span></span>

<span data-ttu-id="56461-104">Bu makalede Windows Forms tabanlı masaüstü uygulamanızın .NET Framework .NET Core 3,0 ' ye nasıl bağlantı kurulacağı açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="56461-104">This article describes how to port your Windows Forms-based desktop app from .NET Framework to .NET Core 3.0.</span></span> <span data-ttu-id="56461-105">.NET Core 3,0 SDK Windows Forms uygulamaları için destek içerir.</span><span class="sxs-lookup"><span data-stu-id="56461-105">The .NET Core 3.0 SDK includes support for Windows Forms applications.</span></span> <span data-ttu-id="56461-106">Windows Forms hala yalnızca Windows Framework ' ü ve Windows üzerinde çalışır.</span><span class="sxs-lookup"><span data-stu-id="56461-106">Windows Forms is still a Windows-only framework and only runs on Windows.</span></span> <span data-ttu-id="56461-107">Bu örnek, projenizi oluşturmak ve yönetmek için .NET Core SDK CLı kullanır.</span><span class="sxs-lookup"><span data-stu-id="56461-107">This example uses the .NET Core SDK CLI to create and manage your project.</span></span>

<span data-ttu-id="56461-108">Bu makalede, geçiş için kullanılan dosya türlerini tanımlamak için çeşitli adlar kullanılır.</span><span class="sxs-lookup"><span data-stu-id="56461-108">In this article, various names are used to identify types of files used for migration.</span></span> <span data-ttu-id="56461-109">Projeniz geçirilirken dosyalarınız farklı şekilde adlandırılır, bu sayede bunları aşağıda listelenen adlarla eşleştirin:</span><span class="sxs-lookup"><span data-stu-id="56461-109">When migrating your project, your files will be named differently, so mentally match them to the ones listed below:</span></span>

| <span data-ttu-id="56461-110">Dosya</span><span class="sxs-lookup"><span data-stu-id="56461-110">File</span></span> | <span data-ttu-id="56461-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="56461-111">Description</span></span> |
| ---- | ----------- |
| <span data-ttu-id="56461-112">**Uygps. sln**</span><span class="sxs-lookup"><span data-stu-id="56461-112">**MyApps.sln**</span></span> | <span data-ttu-id="56461-113">Çözüm dosyasının adı.</span><span class="sxs-lookup"><span data-stu-id="56461-113">The name of the solution file.</span></span> |
| <span data-ttu-id="56461-114">**MyForms. csproj**</span><span class="sxs-lookup"><span data-stu-id="56461-114">**MyForms.csproj**</span></span> | <span data-ttu-id="56461-115">.NET Framework Windows Forms projenin bağlantı noktasına adı.</span><span class="sxs-lookup"><span data-stu-id="56461-115">The name of the .NET Framework Windows Forms project to port.</span></span> |
| <span data-ttu-id="56461-116">**MyFormsCore. csproj**</span><span class="sxs-lookup"><span data-stu-id="56461-116">**MyFormsCore.csproj**</span></span> | <span data-ttu-id="56461-117">Oluşturduğunuz yeni .NET Core projesinin adı.</span><span class="sxs-lookup"><span data-stu-id="56461-117">The name of the new .NET Core project you create.</span></span> |
| <span data-ttu-id="56461-118">**MyAppCore. exe**</span><span class="sxs-lookup"><span data-stu-id="56461-118">**MyAppCore.exe**</span></span> | <span data-ttu-id="56461-119">.NET Core Windows Forms uygulaması çalıştırılabilir.</span><span class="sxs-lookup"><span data-stu-id="56461-119">The .NET Core Windows Forms app executable.</span></span> |

## <a name="prerequisites"></a><span data-ttu-id="56461-120">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="56461-120">Prerequisites</span></span>

- <span data-ttu-id="56461-121">İstediğiniz tasarımcı çalışması için [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) .</span><span class="sxs-lookup"><span data-stu-id="56461-121">[Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) for any designer work you want to do.</span></span>

  <span data-ttu-id="56461-122">Aşağıdaki Visual Studio iş yüklerini yükler:</span><span class="sxs-lookup"><span data-stu-id="56461-122">Install the following Visual Studio workloads:</span></span>
  - <span data-ttu-id="56461-123">.NET masaüstü geliştirme</span><span class="sxs-lookup"><span data-stu-id="56461-123">.NET desktop development</span></span>
  - <span data-ttu-id="56461-124">.NET platformlar arası geliştirme</span><span class="sxs-lookup"><span data-stu-id="56461-124">.NET cross-platform development</span></span>

- <span data-ttu-id="56461-125">Sorun olmadan oluşturulup çalışan bir çözümde çalışan bir Windows Forms projesi.</span><span class="sxs-lookup"><span data-stu-id="56461-125">A working Windows Forms project in a solution that builds and runs without issue.</span></span>
- <span data-ttu-id="56461-126">Projenizin ' de C#kodlanmış olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="56461-126">Your project must be coded in C#.</span></span> 
- <span data-ttu-id="56461-127">En son [.NET Core 3,0](https://aka.ms/netcore3download) önizlemeyi yükler.</span><span class="sxs-lookup"><span data-stu-id="56461-127">Install the latest [.NET Core 3.0](https://aka.ms/netcore3download) preview.</span></span>

>[!NOTE]
><span data-ttu-id="56461-128">**Visual Studio 2017** , .net Core 3,0 projelerini desteklemez.</span><span class="sxs-lookup"><span data-stu-id="56461-128">**Visual Studio 2017** doesn't support .NET Core 3.0 projects.</span></span> <span data-ttu-id="56461-129">**Visual Studio 2019** , .net Core 3,0 projelerini destekler, ancak henüz .net core 3,0 Windows Forms projeleri için görsel tasarımcıyı desteklemez.</span><span class="sxs-lookup"><span data-stu-id="56461-129">**Visual Studio 2019** supports .NET Core 3.0 projects but doesn't yet support the visual designer for .NET Core 3.0 Windows Forms projects.</span></span> <span data-ttu-id="56461-130">Visual Designer 'ı kullanmak için, çözümünüzde .NET Core projesiyle Forms dosyalarını paylaşan bir .NET Windows Forms projesi olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="56461-130">To use the visual designer, you must have a .NET Windows Forms project in your solution that shares the forms files with the .NET Core project.</span></span>

### <a name="consider"></a><span data-ttu-id="56461-131">Seçmeyi</span><span class="sxs-lookup"><span data-stu-id="56461-131">Consider</span></span>

<span data-ttu-id="56461-132">Bir .NET Framework Windows Forms uygulamasının taşıma sırasında göz önünde bulundurmanız gereken birkaç nokta vardır.</span><span class="sxs-lookup"><span data-stu-id="56461-132">When porting a .NET Framework Windows Forms application, there are a few things you must consider.</span></span>

01. <span data-ttu-id="56461-133">Uygulamanızın geçiş için iyi bir aday olduğunu kontrol edin.</span><span class="sxs-lookup"><span data-stu-id="56461-133">Check that your application is a good candidate for migration.</span></span>

    <span data-ttu-id="56461-134">Projenizin .NET Core 3,0 ' e geçiş olacağını öğrenmek için [.net taşınabilirlik Çözümleyicisi](../../standard/analyzers/portability-analyzer.md) ' ni kullanın.</span><span class="sxs-lookup"><span data-stu-id="56461-134">Use the [.NET Portability Analyzer](../../standard/analyzers/portability-analyzer.md) to determine if your project will migrate to .NET Core 3.0.</span></span> <span data-ttu-id="56461-135">Projenizde .NET Core 3,0 ile ilgili sorunlar varsa, çözümleyici bu sorunları belirlemenize yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="56461-135">If your project has issues with .NET Core 3.0, the analyzer helps you identify those problems.</span></span>

01. <span data-ttu-id="56461-136">Farklı bir Windows Forms sürümü kullanıyorsunuz.</span><span class="sxs-lookup"><span data-stu-id="56461-136">You're using a different version of Windows Forms.</span></span>

    <span data-ttu-id="56461-137">.NET Core 3,0 Preview 1 yayınlandığında, Windows Forms GitHub 'da açık kaynak olarak gitti.</span><span class="sxs-lookup"><span data-stu-id="56461-137">When .NET Core 3.0 Preview 1 was released, Windows Forms went open source on GitHub.</span></span> <span data-ttu-id="56461-138">.NET Core Windows Forms kodu, .NET Framework Windows Forms kod temelinin çatalından oluşur.</span><span class="sxs-lookup"><span data-stu-id="56461-138">The code for .NET Core Windows Forms is a fork of the .NET Framework Windows Forms codebase.</span></span> <span data-ttu-id="56461-139">Bazı farklılıklar olabilir ve uygulamanızın bağlantı noktası olmayacaktır.</span><span class="sxs-lookup"><span data-stu-id="56461-139">It's possible some differences exist and your app won't port.</span></span>

01. <span data-ttu-id="56461-140">[Windows Uyumluluk Paketi][compat-pack] , geçiş yapmanıza yardımcı olabilir.</span><span class="sxs-lookup"><span data-stu-id="56461-140">The [Windows Compatibility Pack][compat-pack] may help you migrate.</span></span>

    <span data-ttu-id="56461-141">.NET Framework ' de kullanılabilen bazı API 'Ler .NET Core 3,0 ' de kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="56461-141">Some APIs that are available in .NET Framework aren't available in .NET Core 3.0.</span></span> <span data-ttu-id="56461-142">[Windows Uyumluluk Paketi][compat-pack] , bu API 'lerin çoğunu ekler ve Windows Forms uygulamanızın .NET Core ile uyumlu hale gelmesine yardımcı olabilir.</span><span class="sxs-lookup"><span data-stu-id="56461-142">The [Windows Compatibility Pack][compat-pack] adds many of these APIs and may help your Windows Forms app become compatible with .NET Core.</span></span>

01. <span data-ttu-id="56461-143">Projeniz tarafından kullanılan NuGet paketlerini güncelleştirin.</span><span class="sxs-lookup"><span data-stu-id="56461-143">Update the NuGet packages used by your project.</span></span>

    <span data-ttu-id="56461-144">Herhangi bir geçişten önce NuGet paketlerinin en son sürümlerini kullanmak her zaman iyi bir uygulamadır.</span><span class="sxs-lookup"><span data-stu-id="56461-144">It's always a good practice to use the latest versions of NuGet packages before any migration.</span></span> <span data-ttu-id="56461-145">Uygulamanız herhangi bir NuGet paketine başvuruyorsa, bunları en son sürüme güncelleştirin.</span><span class="sxs-lookup"><span data-stu-id="56461-145">If your application is referencing any NuGet packages, update them to the latest version.</span></span> <span data-ttu-id="56461-146">Uygulamanızın başarıyla derlemediğinden emin olun.</span><span class="sxs-lookup"><span data-stu-id="56461-146">Ensure your application builds successfully.</span></span> <span data-ttu-id="56461-147">Yükseltmeden sonra, herhangi bir paket hatası varsa, paketi, kodunuzu kesen en son sürüme indirgeymelisiniz.</span><span class="sxs-lookup"><span data-stu-id="56461-147">After upgrading, if there are any package errors, downgrade the package to the latest version that doesn't break your code.</span></span>

01. <span data-ttu-id="56461-148">Visual Studio 2019, .NET Core 3,0 için form tasarımcısını henüz desteklemiyor</span><span class="sxs-lookup"><span data-stu-id="56461-148">Visual Studio 2019 doesn't yet support the Forms Designer for .NET Core 3.0</span></span>

    <span data-ttu-id="56461-149">Şu anda, Visual Studio 'dan form tasarımcısını kullanmak istiyorsanız, mevcut .NET Framework Windows Forms proje dosyanızı saklamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="56461-149">Currently, you need to keep your existing .NET Framework Windows Forms project file if you want to use the Forms Designer from Visual Studio.</span></span>

## <a name="create-a-new-sdk-project"></a><span data-ttu-id="56461-150">Yeni bir SDK projesi oluştur</span><span class="sxs-lookup"><span data-stu-id="56461-150">Create a new SDK project</span></span>

<span data-ttu-id="56461-151">Oluşturduğunuz yeni .NET Core 3,0 projesi .NET Framework projenizden farklı bir dizinde olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="56461-151">The new .NET Core 3.0 project you create must be in a different directory from your .NET Framework project.</span></span> <span data-ttu-id="56461-152">İkisi de aynı dizinde ise, **obj** dizininde oluşturulan dosyalarla çakışmalarıyla karşılaşabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="56461-152">If they're both in the same directory, you may run into conflicts with the files that are generated in the **obj** directory.</span></span> <span data-ttu-id="56461-153">Bu örnekte, **SolutionFolder** dizininde **Myformsappcore** adlı bir dizin oluşturacağız:</span><span class="sxs-lookup"><span data-stu-id="56461-153">In this example, we'll create a directory named **MyFormsAppCore** in the **SolutionFolder** directory:</span></span>

```
SolutionFolder
├───MyApps.sln
├───MyFormsApp
│   └───MyForms.csproj
└───MyFormsAppCore      <--- New folder for core project
```

<span data-ttu-id="56461-154">Sonra, **Myformscore. csproj** projesini **Myformsappcore** dizininde oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="56461-154">Next, you need to create the **MyFormsCore.csproj** project in the **MyFormsAppCore** directory.</span></span> <span data-ttu-id="56461-155">Bu dosyayı tercih ettiğiniz metin düzenleyicisini kullanarak el ile oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="56461-155">You can create this file manually by using the text editor of choice.</span></span> <span data-ttu-id="56461-156">Aşağıdaki XML 'e yapıştırın:</span><span class="sxs-lookup"><span data-stu-id="56461-156">Paste in the following XML:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk.WindowsDesktop">

  <PropertyGroup>
    <OutputType>WinExe</OutputType>
    <TargetFramework>netcoreapp3.0</TargetFramework>
    <UseWindowsForms>true</UseWindowsForms>
  </PropertyGroup>

</Project>
```

<span data-ttu-id="56461-157">Proje dosyasını el ile oluşturmak istemiyorsanız, projeyi oluşturmak için Visual Studio 'Yu veya .NET Core SDK kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="56461-157">If you don't want to create the project file manually, you can use Visual Studio or the .NET Core SDK to generate the project.</span></span> <span data-ttu-id="56461-158">Ancak proje dosyası hariç proje şablonu tarafından oluşturulan diğer tüm dosyaları silmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="56461-158">However, you must delete all other files generated by the project template except for the project file.</span></span> <span data-ttu-id="56461-159">SDK 'yı kullanmak için **SolutionFolder** dizininden aşağıdaki komutu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="56461-159">To use the SDK, run the following command from the **SolutionFolder** directory:</span></span>

```dotnetcli
dotnet new winforms -o MyFormsAppCore -n MyFormsCore
```

<span data-ttu-id="56461-160">**Myformscore. csproj**öğesini oluşturduktan sonra, dizin yapınız aşağıdaki gibi görünmelidir:</span><span class="sxs-lookup"><span data-stu-id="56461-160">After you create the **MyFormsCore.csproj**, your directory structure should look like the following:</span></span>

```
SolutionFolder
├───MyApps.sln
├───MyFormsApp
│   └───MyForms.csproj
└───MyFormsAppCore
    └───MyFormsCore.csproj
```

<span data-ttu-id="56461-161">**Myformscore. csproj** projesini, Visual Studio ya da **solutionfolder** dizininden .NET Core CLI **uygulamalılar. sln** öğesine eklemek isteyeceksiniz:</span><span class="sxs-lookup"><span data-stu-id="56461-161">You'll want to add the **MyFormsCore.csproj** project to **MyApps.sln** with either Visual Studio or the .NET Core CLI from the **SolutionFolder** directory:</span></span>

```dotnetcli
dotnet sln add .\MyFormsAppCore\MyFormsCore.csproj
```

## <a name="fix-assembly-info-generation"></a><span data-ttu-id="56461-162">Derleme bilgileri oluşturmayı çözme</span><span class="sxs-lookup"><span data-stu-id="56461-162">Fix assembly info generation</span></span>

<span data-ttu-id="56461-163">.NET Framework ile oluşturulan Windows Forms projeleri, oluşturulacak derlemenin sürümü gibi derleme özniteliklerini içeren bir `AssemblyInfo.cs` dosyası içerir.</span><span class="sxs-lookup"><span data-stu-id="56461-163">Windows Forms projects that were created with .NET Framework include an `AssemblyInfo.cs` file, which contains assembly attributes such as the version of the assembly to be generated.</span></span> <span data-ttu-id="56461-164">SDK stilindeki projeler, SDK proje dosyasını temel alarak bu bilgileri sizin için otomatik olarak oluşturur.</span><span class="sxs-lookup"><span data-stu-id="56461-164">SDK-style projects automatically generate this information for you based on the SDK project file.</span></span> <span data-ttu-id="56461-165">Her iki tür "derleme bilgisi" de bir çakışma oluşturur.</span><span class="sxs-lookup"><span data-stu-id="56461-165">Having both types of "assembly info" creates a conflict.</span></span> <span data-ttu-id="56461-166">Otomatik oluşturmayı devre dışı bırakarak bu sorunu çözün. Bu, projeyi mevcut `AssemblyInfo.cs` dosyanızı kullanmaya zorlar.</span><span class="sxs-lookup"><span data-stu-id="56461-166">Resolve this problem by disabling automatic generation, which forces the project to use your existing `AssemblyInfo.cs` file.</span></span>

<span data-ttu-id="56461-167">Ana `<PropertyGroup>` düğümüne eklemek için üç ayar vardır.</span><span class="sxs-lookup"><span data-stu-id="56461-167">There are three settings to add to the main `<PropertyGroup>` node.</span></span> 

- <span data-ttu-id="56461-168">**Generateassemblyınfo**</span><span class="sxs-lookup"><span data-stu-id="56461-168">**GenerateAssemblyInfo**</span></span>\
<span data-ttu-id="56461-169">Bu özelliği `false`ayarladığınızda, derleme özniteliklerini oluşturmaz.</span><span class="sxs-lookup"><span data-stu-id="56461-169">When you set this property to `false`, it won't generate the assembly attributes.</span></span> <span data-ttu-id="56461-170">Bu, .NET Framework projeden varolan `AssemblyInfo.cs` dosyası ile çakışmayı önler.</span><span class="sxs-lookup"><span data-stu-id="56461-170">This avoids the conflict with the existing `AssemblyInfo.cs` file from the .NET Framework project.</span></span>

- <span data-ttu-id="56461-171">**AssemblyName**</span><span class="sxs-lookup"><span data-stu-id="56461-171">**AssemblyName**</span></span>\
<span data-ttu-id="56461-172">Bu özelliğin değeri, derlerken oluşturulan çıkış ikilisi olur.</span><span class="sxs-lookup"><span data-stu-id="56461-172">The value of this property is the output binary created when you compile.</span></span> <span data-ttu-id="56461-173">Ada eklenen bir uzantıya gerek yoktur.</span><span class="sxs-lookup"><span data-stu-id="56461-173">The name doesn't need an extension added to it.</span></span> <span data-ttu-id="56461-174">Örneğin, `MyCoreApp` kullanmak `MyCoreApp.exe`üretir.</span><span class="sxs-lookup"><span data-stu-id="56461-174">For example, using `MyCoreApp` produces `MyCoreApp.exe`.</span></span>

- <span data-ttu-id="56461-175">**RootNamespace**</span><span class="sxs-lookup"><span data-stu-id="56461-175">**RootNamespace**</span></span>\
<span data-ttu-id="56461-176">Projeniz tarafından kullanılan varsayılan ad alanı.</span><span class="sxs-lookup"><span data-stu-id="56461-176">The default namespace used by your project.</span></span> <span data-ttu-id="56461-177">Bu, .NET Framework projesinin varsayılan ad alanıyla eşleşmelidir.</span><span class="sxs-lookup"><span data-stu-id="56461-177">This should match the default namespace of the .NET Framework project.</span></span>

<span data-ttu-id="56461-178">Bu üç öğeyi `MyFormsCore.csproj` dosyasındaki `<PropertyGroup>` düğümüne ekleyin:</span><span class="sxs-lookup"><span data-stu-id="56461-178">Add these three elements to the `<PropertyGroup>` node in the `MyFormsCore.csproj` file:</span></span>

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

## <a name="add-source-code"></a><span data-ttu-id="56461-179">Kaynak kodu ekle</span><span class="sxs-lookup"><span data-stu-id="56461-179">Add source code</span></span>

<span data-ttu-id="56461-180">Şu anda **Myformscore. csproj** projesi hiçbir kodu derlemez.</span><span class="sxs-lookup"><span data-stu-id="56461-180">Right now, the **MyFormsCore.csproj** project doesn't compile any code.</span></span> <span data-ttu-id="56461-181">Varsayılan olarak, .NET Core projeleri geçerli dizine ve tüm alt dizinlere tüm kaynak kodlarını otomatik olarak ekler.</span><span class="sxs-lookup"><span data-stu-id="56461-181">By default, .NET Core projects automatically include all source code in the current directory and any child directories.</span></span> <span data-ttu-id="56461-182">Projeyi, .NET Framework projesinden bir göreli yol kullanarak kod içerecek şekilde yapılandırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="56461-182">You must configure the project to include code from the .NET Framework project using a relative path.</span></span> <span data-ttu-id="56461-183">.NET Framework projeniz, formlarınızın simgeleri ve kaynakları için **. resx** dosyalarını kullandıysanız, bunları da eklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="56461-183">If your .NET Framework project used **.resx** files for icons and resources for your forms, you'll need to include those too.</span></span> 

<span data-ttu-id="56461-184">Aşağıdaki `<ItemGroup>` düğümünü projenize ekleyin.</span><span class="sxs-lookup"><span data-stu-id="56461-184">Add the following `<ItemGroup>` node to your project.</span></span> <span data-ttu-id="56461-185">Her bir bildirimde alt dizinler içeren bir dosya glob kalıbı bulunur.</span><span class="sxs-lookup"><span data-stu-id="56461-185">Each statement includes a file glob pattern that includes child directories.</span></span>

```xml
  <ItemGroup>
    <Compile Include="..\MyFormsApp\**\*.cs" />
    <EmbeddedResource Include="..\MyFormsApp\**\*.resx" />
  </ItemGroup>
```

<span data-ttu-id="56461-186">Alternatif olarak, .NET Framework projenizdeki her dosya için bir `<Compile>` veya `<EmbeddedResource>` girişi oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="56461-186">Alternatively, you can create a `<Compile>` or `<EmbeddedResource>` entry for each file in your .NET Framework project.</span></span>

## <a name="add-nuget-packages"></a><span data-ttu-id="56461-187">NuGet paketleri Ekle</span><span class="sxs-lookup"><span data-stu-id="56461-187">Add NuGet packages</span></span>

<span data-ttu-id="56461-188">.NET Framework projesi tarafından başvurulan her bir NuGet paketini .NET Core projesine ekleyin.</span><span class="sxs-lookup"><span data-stu-id="56461-188">Add each NuGet package referenced by the .NET Framework project to the .NET Core project.</span></span> 

<span data-ttu-id="56461-189">Büyük olasılıkla .NET Framework Windows Forms uygulamanızın, projeniz tarafından başvurulan tüm NuGet paketlerinin listesini içeren bir **Packages. config** dosyası vardır.</span><span class="sxs-lookup"><span data-stu-id="56461-189">Most likely your .NET Framework Windows Forms app has a **packages.config** file that contains a list of all of the NuGet packages that are referenced by your project.</span></span> <span data-ttu-id="56461-190">.NET Core projesine hangi NuGet paketlerinin ekleneceğini öğrenmek için bu listeye bakabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="56461-190">You can look at this list to determine which NuGet packages to add to the .NET Core project.</span></span> <span data-ttu-id="56461-191">Örneğin, .NET Framework projesi `MetroFramework`, `MetroFramework.Design`ve `MetroFramework.Fonts` NuGet paketlerine başvuruyorsa, her birini Visual Studio ya da **SolutionFolder** dizinindeki .NET Core CLI ile projeye ekleyin:</span><span class="sxs-lookup"><span data-stu-id="56461-191">For example, if the .NET Framework project referenced the `MetroFramework`, `MetroFramework.Design`, and `MetroFramework.Fonts` NuGet packages, add each to the project with either Visual Studio or the .NET Core CLI from the **SolutionFolder** directory:</span></span>

```dotnetcli
dotnet add .\MyFormsAppCore\MyFormsCore.csproj package MetroFramework
dotnet add .\MyFormsAppCore\MyFormsCore.csproj package MetroFramework.Design
dotnet add .\MyFormsAppCore\MyFormsCore.csproj package MetroFramework.Fonts
```

<span data-ttu-id="56461-192">Önceki komutlar **Myformscore. csproj** projesine aşağıdaki NuGet başvurularını ekler:</span><span class="sxs-lookup"><span data-stu-id="56461-192">The previous commands would add the following NuGet references to the **MyFormsCore.csproj** project:</span></span>

```xml
  <ItemGroup>
    <PackageReference Include="MetroFramework" Version="1.2.0.3" />
    <PackageReference Include="MetroFramework.Design" Version="1.2.0.3" />
    <PackageReference Include="MetroFramework.Fonts" Version="1.2.0.3" />
  </ItemGroup>
```

## <a name="port-control-libraries"></a><span data-ttu-id="56461-193">Bağlantı noktası denetim kitaplıkları</span><span class="sxs-lookup"><span data-stu-id="56461-193">Port control libraries</span></span>

<span data-ttu-id="56461-194">Bağlantı noktası için bir Windows Forms denetimleri kitaplığı projeniz varsa, yönergeler birkaç ayar haricinde bir .NET Framework Windows Forms uygulama projesinin taşıma ile aynıdır.</span><span class="sxs-lookup"><span data-stu-id="56461-194">If you have a Windows Forms Controls library project to port, the directions are the same as porting a .NET Framework Windows Forms app project, except for a few settings.</span></span> <span data-ttu-id="56461-195">Bir yürütülebilir dosyaya derlemek yerine bir kitaplığa derleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="56461-195">And instead of compiling to an executable, you compile to a library.</span></span> <span data-ttu-id="56461-196">Kaynak kodunuzu içeren genelleştirmeler dosya yollarının yanı sıra, yürütülebilir proje ve kitaplık projesi arasındaki fark en düşük düzeydedir.</span><span class="sxs-lookup"><span data-stu-id="56461-196">The difference between the executable project and the library project, besides paths for the file globs that include your source code, is minimal.</span></span>

<span data-ttu-id="56461-197">Önceki adımın örneğini kullanarak, üzerinde çalıştığımız proje ve dosyaları genişletmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="56461-197">Using the previous step's example, lets expand what projects and files we're working with.</span></span>

| <span data-ttu-id="56461-198">Dosya</span><span class="sxs-lookup"><span data-stu-id="56461-198">File</span></span> | <span data-ttu-id="56461-199">Açıklama</span><span class="sxs-lookup"><span data-stu-id="56461-199">Description</span></span> |
| ---- | ----------- |
| <span data-ttu-id="56461-200">**Uygps. sln**</span><span class="sxs-lookup"><span data-stu-id="56461-200">**MyApps.sln**</span></span> | <span data-ttu-id="56461-201">Çözüm dosyasının adı.</span><span class="sxs-lookup"><span data-stu-id="56461-201">The name of the solution file.</span></span> |
| <span data-ttu-id="56461-202">**MyControls. csproj**</span><span class="sxs-lookup"><span data-stu-id="56461-202">**MyControls.csproj**</span></span> | <span data-ttu-id="56461-203">.NET Framework Windows Forms adı, projeyi bağlantı noktasına denetler.</span><span class="sxs-lookup"><span data-stu-id="56461-203">The name of the .NET Framework Windows Forms Controls project to port.</span></span> |
| <span data-ttu-id="56461-204">**MyControlsCore. csproj**</span><span class="sxs-lookup"><span data-stu-id="56461-204">**MyControlsCore.csproj**</span></span> | <span data-ttu-id="56461-205">Oluşturduğunuz yeni .NET Core kitaplığı projesinin adı.</span><span class="sxs-lookup"><span data-stu-id="56461-205">The name of the new .NET Core library project you create.</span></span> |
| <span data-ttu-id="56461-206">**MyCoreControls. dll**</span><span class="sxs-lookup"><span data-stu-id="56461-206">**MyCoreControls.dll**</span></span> | <span data-ttu-id="56461-207">.NET Core Windows Forms denetimleri kitaplığı.</span><span class="sxs-lookup"><span data-stu-id="56461-207">The .NET Core Windows Forms Controls library.</span></span> |

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

<span data-ttu-id="56461-208">`MyControlsCore.csproj` projesi ile daha önce oluşturulan `MyFormsCore.csproj` projesi arasındaki farkları göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="56461-208">Consider the differences between the `MyControlsCore.csproj` project and the previously created `MyFormsCore.csproj` project.</span></span>

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

<span data-ttu-id="56461-209">.NET Core Windows Forms denetimleri kitaplığı proje dosyasının nasıl görüneceğine ilişkin bir örnek aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="56461-209">Here is an example of what the .NET Core Windows Forms Controls library project file would look like:</span></span>

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

<span data-ttu-id="56461-210">Gördüğünüz gibi, `<OutputType>` düğümü kaldırılmıştır ve bu, derleyicinin çalıştırılabilir yerine bir kitaplık oluşturmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="56461-210">As you can see, the `<OutputType>` node was removed, which defaults the compiler to produce a library instead of an executable.</span></span> <span data-ttu-id="56461-211">`<AssemblyName>` ve `<RootNamespace>` değiştirildi.</span><span class="sxs-lookup"><span data-stu-id="56461-211">The `<AssemblyName>` and `<RootNamespace>` were changed.</span></span> <span data-ttu-id="56461-212">Özellikle `<RootNamespace>`, taşıma yaptığınız Windows Forms denetimleri kitaplığı ad alanıyla eşleşmelidir.</span><span class="sxs-lookup"><span data-stu-id="56461-212">Specifically the `<RootNamespace>` should match the namespace of the Windows Forms Controls library you are porting.</span></span> <span data-ttu-id="56461-213">Son olarak, `<Compile>` ve `<EmbeddedResource>` düğümleri, taşıma yaptığınız Windows Forms denetimleri kitaplığının klasörünü işaret etmek üzere ayarlanmıştı.</span><span class="sxs-lookup"><span data-stu-id="56461-213">And finally, the `<Compile>` and `<EmbeddedResource>` nodes were adjusted to point to the folder of the Windows Forms Controls library you are porting.</span></span>

<span data-ttu-id="56461-214">Ardından, ana .NET Core **Myformscore. csproj** projesinde yeni .net Core Windows Forms denetim kitaplığına başvuru ekleyin.</span><span class="sxs-lookup"><span data-stu-id="56461-214">Next, in the main .NET Core **MyFormsCore.csproj** project add reference to the new .NET Core Windows Forms Control library.</span></span> <span data-ttu-id="56461-215">Visual Studio ya da **SolutionFolder** dizininden .NET Core CLI bir başvuru ekleyin:</span><span class="sxs-lookup"><span data-stu-id="56461-215">Add a reference with either Visual Studio or the .NET Core CLI from the **SolutionFolder** directory:</span></span>

```dotnetcli
dotnet add .\MyFormsAppCore\MyFormsCore.csproj reference .\MyFormsControlsCore\MyControlsCore.csproj
```

<span data-ttu-id="56461-216">Önceki komut **Myformscore. csproj** projesine aşağıdakini ekler:</span><span class="sxs-lookup"><span data-stu-id="56461-216">The previous command adds the following to the **MyFormsCore.csproj** project:</span></span>

```xml
  <ItemGroup>
    <ProjectReference Include="..\MyFormsControlsCore\MyControlsCore.csproj" />
  </ItemGroup>
```

## <a name="problems-compiling"></a><span data-ttu-id="56461-217">Derleme sorunları</span><span class="sxs-lookup"><span data-stu-id="56461-217">Problems compiling</span></span>

<span data-ttu-id="56461-218">Projelerinizi derlerken sorunlarla karşılaşırsanız, .NET Core 'da .NET Framework, ancak kullanılamayan yalnızca Windows salt Windows API 'Lerini kullanıyor olabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="56461-218">If you have problems compiling your projects, you may be using some Windows-only APIs that are available in .NET Framework but not available in .NET Core.</span></span> <span data-ttu-id="56461-219">[Windows Uyumluluk Paketi][compat-pack] NuGet paketini projenize eklemeyi deneyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="56461-219">You can try adding the [Windows Compatibility Pack][compat-pack] NuGet package to your project.</span></span> <span data-ttu-id="56461-220">Bu paket yalnızca Windows üzerinde çalışır ve .NET Core ve .NET Standard projelerine 20.000 Windows API 'Leri ekler.</span><span class="sxs-lookup"><span data-stu-id="56461-220">This package only runs on Windows and adds about 20,000 Windows APIs to .NET Core and .NET Standard projects.</span></span>

```dotnetcli
dotnet add .\MyFormsAppCore\MyFormsCore.csproj package Microsoft.Windows.Compatibility
```

<span data-ttu-id="56461-221">Önceki komut **Myformscore. csproj** projesine aşağıdakini ekler:</span><span class="sxs-lookup"><span data-stu-id="56461-221">The previous command adds the following to the **MyFormsCore.csproj** project:</span></span>

```xml
  <ItemGroup>
    <PackageReference Include="Microsoft.Windows.Compatibility" Version="2.0.1" />
  </ItemGroup>
```

## <a name="windows-forms-designer"></a><span data-ttu-id="56461-222">Windows Form Tasarımcısı</span><span class="sxs-lookup"><span data-stu-id="56461-222">Windows Forms Designer</span></span>

<span data-ttu-id="56461-223">Bu makalede açıklandığı gibi, Visual Studio 2019 yalnızca .NET Framework projelerinde form tasarımcısını destekler.</span><span class="sxs-lookup"><span data-stu-id="56461-223">As detailed in this article, Visual Studio 2019 only supports the Forms Designer in .NET Framework projects.</span></span> <span data-ttu-id="56461-224">Yan yana .NET Core projesi oluşturarak, formları tasarlamak için .NET Framework projesi kullanırken projenizi .NET Core ile test edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="56461-224">By creating a side-by-side .NET Core project, you can test your project with .NET Core while you use the .NET Framework project to design forms.</span></span> <span data-ttu-id="56461-225">Çözüm dosyanız hem .NET Framework hem de .NET Core projelerini içerir.</span><span class="sxs-lookup"><span data-stu-id="56461-225">Your solution file includes both the .NET Framework and .NET Core projects.</span></span> <span data-ttu-id="56461-226">.NET Framework projesindeki formlarınızı ve denetimlerinizi ekleyin ve tasarlayın ve .NET Core projelerine eklediğimiz dosya glob desenlerine bağlı olarak, .NET Core projelerine yeni veya değiştirilmiş dosyalar otomatik olarak dahil edilir.</span><span class="sxs-lookup"><span data-stu-id="56461-226">Add and design your forms and controls in the .NET Framework project, and based on the file glob patterns we added to the .NET Core projects, any new or changed files will automatically be included in the .NET Core projects.</span></span>

<span data-ttu-id="56461-227">Visual Studio 2019 Windows Form Tasarımcısı desteklediğinde, .NET Core proje dosyanızın içeriğini kopyalayabilir/.NET Framework proje dosyasına yapıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="56461-227">Once Visual Studio 2019 supports the Windows Forms Designer, you can copy/paste the content of your .NET Core project file into the .NET Framework project file.</span></span> <span data-ttu-id="56461-228">Ardından `<Source>` ve `<EmbeddedResource>` öğeleriyle eklenen glob düzenlerini silin.</span><span class="sxs-lookup"><span data-stu-id="56461-228">Then delete the file glob patterns added with the `<Source>` and `<EmbeddedResource>` items.</span></span> <span data-ttu-id="56461-229">Uygulamanız tarafından kullanılan herhangi bir proje başvurusunun yolunu düzeltin.</span><span class="sxs-lookup"><span data-stu-id="56461-229">Fix the paths to any project reference used by your app.</span></span> <span data-ttu-id="56461-230">Bu, .NET Framework projesini bir .NET Core projesine etkin bir şekilde yükseltir.</span><span class="sxs-lookup"><span data-stu-id="56461-230">This effectively upgrades the .NET Framework project to a .NET Core project.</span></span>
 
## <a name="next-steps"></a><span data-ttu-id="56461-231">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="56461-231">Next steps</span></span>

- <span data-ttu-id="56461-232">[Windows Uyumluluk Paketi][compat-pack]hakkında daha fazla bilgi edinin.</span><span class="sxs-lookup"><span data-stu-id="56461-232">Read more about the [Windows Compatibility Pack][compat-pack].</span></span>
- <span data-ttu-id="56461-233">.NET Framework Windows Forms projenizi .NET Core 'a [taşıma hakkında bir video](https://www.youtube.com/watch?v=upVQEUc_KwU) izleyin.</span><span class="sxs-lookup"><span data-stu-id="56461-233">Watch a [video on porting](https://www.youtube.com/watch?v=upVQEUc_KwU) your .NET Framework Windows Forms project to .NET Core.</span></span>

[compat-pack]: windows-compat-pack.md
