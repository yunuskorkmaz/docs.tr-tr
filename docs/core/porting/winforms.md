---
title: Bağlantı noktası bir Windows Forms uygulaması .NET Core 3.0
description: Windows için .NET Core 3.0 bir .NET Framework Windows Forms uygulamasına bağlantı noktasına öğretir.
author: Thraka
ms.author: adegeo
ms.date: 03/01/2019
ms.custom: ''
ms.openlocfilehash: aebfaa85338e014ca47256b85a1bd6529ad803bb
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61663095"
---
# <a name="how-to-port-a-windows-forms-desktop-app-to-net-core"></a><span data-ttu-id="23baf-103">Nasıl yapılır: .NET Core için bir Windows Forms masaüstü uygulaması bağlantı noktası</span><span class="sxs-lookup"><span data-stu-id="23baf-103">How to: Port a Windows Forms desktop app to .NET Core</span></span>

<span data-ttu-id="23baf-104">Bu makalede, Windows Forms tabanlı masaüstü uygulamanızın .NET Framework .NET Core 3.0 için bağlantı noktası açıklar.</span><span class="sxs-lookup"><span data-stu-id="23baf-104">This article describes how to port your Windows Forms-based desktop app from .NET Framework to .NET Core 3.0.</span></span> <span data-ttu-id="23baf-105">.NET Core SDK 3.0, Windows Forms uygulamaları için destek içerir.</span><span class="sxs-lookup"><span data-stu-id="23baf-105">The .NET Core 3.0 SDK includes support for Windows Forms applications.</span></span> <span data-ttu-id="23baf-106">Windows Formları yalnızca Windows framework hala geçerli olduğunu ve yalnızca Windows üzerinde çalışır.</span><span class="sxs-lookup"><span data-stu-id="23baf-106">Windows Forms is still a Windows-only framework and only runs on Windows.</span></span> <span data-ttu-id="23baf-107">Bu örnek, oluşturmak ve projenize yönetmek için .NET Core SDK'sı CLI'yı kullanır.</span><span class="sxs-lookup"><span data-stu-id="23baf-107">This example uses the .NET Core SDK CLI to create and manage your project.</span></span>

<span data-ttu-id="23baf-108">Bu makalede, çeşitli adlar, geçiş için kullanılan dosya türlerini tanımlamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="23baf-108">In this article, various names are used to identify types of files used for migration.</span></span> <span data-ttu-id="23baf-109">Projenizi geçirirken, dosyalarınızı farklı şekilde adlandırılmış, bu nedenle akıl aşağıda listelenen olanlarla eşleşmesi:</span><span class="sxs-lookup"><span data-stu-id="23baf-109">When migrating your project, your files will be named differently, so mentally match them to the ones listed below:</span></span>

| <span data-ttu-id="23baf-110">Dosya</span><span class="sxs-lookup"><span data-stu-id="23baf-110">File</span></span> | <span data-ttu-id="23baf-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="23baf-111">Description</span></span> |
| ---- | ----------- |
| <span data-ttu-id="23baf-112">**MyApps.sln**</span><span class="sxs-lookup"><span data-stu-id="23baf-112">**MyApps.sln**</span></span> | <span data-ttu-id="23baf-113">Çözüm dosyasının adı.</span><span class="sxs-lookup"><span data-stu-id="23baf-113">The name of the solution file.</span></span> |
| <span data-ttu-id="23baf-114">**MyForms.csproj**</span><span class="sxs-lookup"><span data-stu-id="23baf-114">**MyForms.csproj**</span></span> | <span data-ttu-id="23baf-115">Bağlantı noktası için .NET Framework Windows Forms projesinin adı.</span><span class="sxs-lookup"><span data-stu-id="23baf-115">The name of the .NET Framework Windows Forms project to port.</span></span> |
| <span data-ttu-id="23baf-116">**MyFormsCore.csproj**</span><span class="sxs-lookup"><span data-stu-id="23baf-116">**MyFormsCore.csproj**</span></span> | <span data-ttu-id="23baf-117">Oluşturduğunuz yeni .NET Core projesinin adı.</span><span class="sxs-lookup"><span data-stu-id="23baf-117">The name of the new .NET Core project you create.</span></span> |
| <span data-ttu-id="23baf-118">**MyAppCore.exe**</span><span class="sxs-lookup"><span data-stu-id="23baf-118">**MyAppCore.exe**</span></span> | <span data-ttu-id="23baf-119">.NET Core Windows Forms uygulaması çalıştırılabilir.</span><span class="sxs-lookup"><span data-stu-id="23baf-119">The .NET Core Windows Forms app executable.</span></span> |

## <a name="prerequisites"></a><span data-ttu-id="23baf-120">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="23baf-120">Prerequisites</span></span>

- <span data-ttu-id="23baf-121">[Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) yapmak istediğiniz herhangi bir tasarımcı iş için.</span><span class="sxs-lookup"><span data-stu-id="23baf-121">[Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) for any designer work you want to do.</span></span>

  <span data-ttu-id="23baf-122">Aşağıdaki Visual Studio iş yüklerini yükleyin:</span><span class="sxs-lookup"><span data-stu-id="23baf-122">Install the following Visual Studio workloads:</span></span>
  - <span data-ttu-id="23baf-123">.NET masaüstü geliştirme</span><span class="sxs-lookup"><span data-stu-id="23baf-123">.NET desktop development</span></span>
  - <span data-ttu-id="23baf-124">.NET platformlar arası geliştirme</span><span class="sxs-lookup"><span data-stu-id="23baf-124">.NET cross-platform development</span></span>

- <span data-ttu-id="23baf-125">Çalışan bir Windows Forms projesi oluşturan ve sorun çalışır bir çözümde.</span><span class="sxs-lookup"><span data-stu-id="23baf-125">A working Windows Forms project in a solution that builds and runs without issue.</span></span>
- <span data-ttu-id="23baf-126">İçinde projenizin kodlanmasını C#.</span><span class="sxs-lookup"><span data-stu-id="23baf-126">Your project must be coded in C#.</span></span> 
- <span data-ttu-id="23baf-127">Son yükleme [.NET Core 3.0](https://aka.ms/netcore3download) Önizleme.</span><span class="sxs-lookup"><span data-stu-id="23baf-127">Install the latest [.NET Core 3.0](https://aka.ms/netcore3download) preview.</span></span>

>[!NOTE]
><span data-ttu-id="23baf-128">**Visual Studio 2017** .NET Core 3.0 projeleri desteklemiyor.</span><span class="sxs-lookup"><span data-stu-id="23baf-128">**Visual Studio 2017** doesn't support .NET Core 3.0 projects.</span></span> <span data-ttu-id="23baf-129">**Visual Studio 2019** .NET Core 3.0 projeleri destekler ancak görsel tasarımcı için .NET Core 3.0, Windows Forms projeleri henüz desteklememektedir.</span><span class="sxs-lookup"><span data-stu-id="23baf-129">**Visual Studio 2019** supports .NET Core 3.0 projects but doesn't yet support the visual designer for .NET Core 3.0 Windows Forms projects.</span></span> <span data-ttu-id="23baf-130">Görsel tasarımcıyı kullanmak için çözümünüzdeki forms dosyaları ile .NET Core projesi paylaşan bir .NET Windows Forms projesi olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="23baf-130">To use the visual designer, you must have a .NET Windows Forms project in your solution that shares the forms files with the .NET Core project.</span></span>

### <a name="consider"></a><span data-ttu-id="23baf-131">Göz önünde bulundurun</span><span class="sxs-lookup"><span data-stu-id="23baf-131">Consider</span></span>

<span data-ttu-id="23baf-132">Bir .NET Framework Windows Forms uygulaması taşırken dikkate almanız gereken birkaç nokta vardır.</span><span class="sxs-lookup"><span data-stu-id="23baf-132">When porting a .NET Framework Windows Forms application, there are a few things you must consider.</span></span>

01. <span data-ttu-id="23baf-133">Uygulamanızı geçişi için iyi bir aday olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="23baf-133">Check that your application is a good candidate for migration.</span></span>

    <span data-ttu-id="23baf-134">Kullanım [.NET Portability Analyzer](../../standard/analyzers/portability-analyzer.md) projeniz için .NET Core 3.0 geçirirseniz belirlemek için.</span><span class="sxs-lookup"><span data-stu-id="23baf-134">Use the [.NET Portability Analyzer](../../standard/analyzers/portability-analyzer.md) to determine if your project will migrate to .NET Core 3.0.</span></span> <span data-ttu-id="23baf-135">Projeniz .NET Core 3.0 ile ilgili sorunlar varsa, Çözümleyicisi bu sorunları belirlemenize yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="23baf-135">If your project has issues with .NET Core 3.0, the analyzer helps you identify those problems.</span></span>

01. <span data-ttu-id="23baf-136">Windows Forms farklı bir sürümünü kullanıyorsunuz.</span><span class="sxs-lookup"><span data-stu-id="23baf-136">You're using a different version of Windows Forms.</span></span>

    <span data-ttu-id="23baf-137">.NET Core 3.0 Önizleme 1 yayımlandığında, Windows Forms, açık kaynaklı oluştu. GitHub üzerinde.</span><span class="sxs-lookup"><span data-stu-id="23baf-137">When .NET Core 3.0 Preview 1 was released, Windows Forms went open-source on GitHub.</span></span> <span data-ttu-id="23baf-138">.NET Core Windows formları için .NET Framework Windows Forms kod tabanı deponun bir çatalını kodudur.</span><span class="sxs-lookup"><span data-stu-id="23baf-138">The code for .NET Core Windows Forms is a fork of the .NET Framework Windows Forms code base.</span></span> <span data-ttu-id="23baf-139">Bu, bazı farklılıklar mevcuttur ve uygulamanızı bağlantı noktası olmaz mümkündür.</span><span class="sxs-lookup"><span data-stu-id="23baf-139">It's possible some differences exist and your app won't port.</span></span>

01. <span data-ttu-id="23baf-140">[Windows Uyumluluk Paketi] [ compat-pack] geçirmenize yardımcı olabilir.</span><span class="sxs-lookup"><span data-stu-id="23baf-140">The [Windows Compatibility Pack][compat-pack] may help you migrate.</span></span>

    <span data-ttu-id="23baf-141">.NET Framework'te bulunan bazı API'leri, .NET Core 3. 0'kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="23baf-141">Some APIs that are available in .NET Framework aren't available in .NET Core 3.0.</span></span> <span data-ttu-id="23baf-142">[Windows Uyumluluk Paketi] [ compat-pack] bu API'lerin birçoğu ekler ve .NET Core ile uyumlu hale Windows Form uygulamanıza yardımcı olabilir.</span><span class="sxs-lookup"><span data-stu-id="23baf-142">The [Windows Compatibility Pack][compat-pack] adds many of these APIs and may help your Windows Forms app become compatible with .NET Core.</span></span>

01. <span data-ttu-id="23baf-143">Projeniz tarafından kullanılan NuGet paketlerini güncelleştirin.</span><span class="sxs-lookup"><span data-stu-id="23baf-143">Update the NuGet packages used by your project.</span></span>

    <span data-ttu-id="23baf-144">Tüm geçiş işleminden önce NuGet paketlerini en son sürümlerini kullanmak için her zaman iyi bir uygulamadır.</span><span class="sxs-lookup"><span data-stu-id="23baf-144">It's always a good practice to use the latest versions of NuGet packages before any migration.</span></span> <span data-ttu-id="23baf-145">Uygulamanızı herhangi bir NuGet paketinin başvuruyorsa, bunları en son sürüme güncelleştirin.</span><span class="sxs-lookup"><span data-stu-id="23baf-145">If your application is referencing any NuGet packages, update them to the latest version.</span></span> <span data-ttu-id="23baf-146">Uygulamanız başarıyla derlendiğinden emin olun.</span><span class="sxs-lookup"><span data-stu-id="23baf-146">Ensure your application builds successfully.</span></span> <span data-ttu-id="23baf-147">Herhangi bir paket hata varsa, yükselttikten sonra paketi kodunuzu kesmeyecektir en son sürüme düşürme.</span><span class="sxs-lookup"><span data-stu-id="23baf-147">After upgrading, if there are any package errors, downgrade the package to the latest version that doesn't break your code.</span></span>

01. <span data-ttu-id="23baf-148">.NET Core 3.0 için Visual Studio 2019 henüz Form Tasarımcısı desteklemiyor</span><span class="sxs-lookup"><span data-stu-id="23baf-148">Visual Studio 2019 doesn't yet support the Forms Designer for .NET Core 3.0</span></span>

    <span data-ttu-id="23baf-149">Şu anda, Visual Studio'da Forms Tasarımcısı'nı kullanmak istiyorsanız, var olan .NET Framework Windows Forms projesi dosyanızı çalışır durumda bulundurmanıza gerek.</span><span class="sxs-lookup"><span data-stu-id="23baf-149">Currently, you need to keep your existing .NET Framework Windows Forms project file if you want to use the Forms Designer from Visual Studio.</span></span>

## <a name="create-a-new-sdk-project"></a><span data-ttu-id="23baf-150">Yeni SDK projesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="23baf-150">Create a new SDK project</span></span>

<span data-ttu-id="23baf-151">Oluşturduğunuz yeni .NET Core 3.0 proje .NET Framework projenizden farklı bir dizinde olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="23baf-151">The new .NET Core 3.0 project you create must be in a different directory from your .NET Framework project.</span></span> <span data-ttu-id="23baf-152">Her ikisi de aynı dizinde iseler, içinde oluşturulan dosyalar ile çakışma çalışabilir **obj** dizin.</span><span class="sxs-lookup"><span data-stu-id="23baf-152">If they're both in the same directory, you may run into conflicts with the files that are generated in the **obj** directory.</span></span> <span data-ttu-id="23baf-153">Bu örnekte, adlı bir dizin oluşturacağız **MyFormsAppCore** içinde **SolutionFolder** dizini:</span><span class="sxs-lookup"><span data-stu-id="23baf-153">In this example, we'll create a directory named **MyFormsAppCore** in the **SolutionFolder** directory:</span></span>

```
SolutionFolder
├───MyApps.sln
├───MyFormsApp
│   └───MyForms.csproj
└───MyFormsAppCore      <--- New folder for core project
```

<span data-ttu-id="23baf-154">Ardından, oluşturmak için ihtiyacınız **MyFormsCore.csproj** projesi **MyFormsAppCore** dizin.</span><span class="sxs-lookup"><span data-stu-id="23baf-154">Next, you need to create the **MyFormsCore.csproj** project in the **MyFormsAppCore** directory.</span></span> <span data-ttu-id="23baf-155">Bu dosyayı el ile metni kullanarak dilediğiniz düzenleyicisinde oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="23baf-155">You can create this file manually by using the text editor of choice.</span></span> <span data-ttu-id="23baf-156">Aşağıdaki XML yapıştırın:</span><span class="sxs-lookup"><span data-stu-id="23baf-156">Paste in the following XML:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk.WindowsDesktop">

  <PropertyGroup>
    <OutputType>WinExe</OutputType>
    <TargetFramework>netcoreapp3.0</TargetFramework>
    <UseWindowsForms>true</UseWindowsForms>
  </PropertyGroup>

</Project>
```

<span data-ttu-id="23baf-157">Proje dosyasını el ile oluşturmak istemiyorsanız, projeyi oluşturmak için Visual Studio veya .NET Core SDK'sını kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="23baf-157">If you don't want to create the project file manually, you can use Visual Studio or the .NET Core SDK to generate the project.</span></span> <span data-ttu-id="23baf-158">Ancak, proje dosyasının dışında proje şablonu tarafından oluşturulan tüm dosyalar silmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="23baf-158">However, you must delete all other files generated by the project template except for the project file.</span></span> <span data-ttu-id="23baf-159">SDK'yı kullanmak için aşağıdaki komutu çalıştırın. **SolutionFolder** dizini:</span><span class="sxs-lookup"><span data-stu-id="23baf-159">To use the SDK, run the following command from the **SolutionFolder** directory:</span></span>

```cli
dotnet new winforms -o MyFormsAppCore -n MyFormsCore
```

<span data-ttu-id="23baf-160">Oluşturduktan sonra **MyFormsCore.csproj**, dizin yapısını aşağıdaki gibi görünmelidir:</span><span class="sxs-lookup"><span data-stu-id="23baf-160">After you create the **MyFormsCore.csproj**, your directory structure should look like the following:</span></span>

```
SolutionFolder
├───MyApps.sln
├───MyFormsApp
│   └───MyForms.csproj
└───MyFormsAppCore
    └───MyFormsCore.csproj
```

<span data-ttu-id="23baf-161">Eklemek istediğiniz **MyFormsCore.csproj** için proje **MyApps.sln** Visual Studio veya .NET Core CLI üzerinden **SolutionFolder** dizini:</span><span class="sxs-lookup"><span data-stu-id="23baf-161">You'll want to add the **MyFormsCore.csproj** project to **MyApps.sln** with either Visual Studio or the .NET Core CLI from the **SolutionFolder** directory:</span></span>

```cli
dotnet sln add .\MyFormsAppCore\MyFormsCore.csproj
```

## <a name="fix-assembly-info-generation"></a><span data-ttu-id="23baf-162">Düzeltme derleme bilgileri oluşturma</span><span class="sxs-lookup"><span data-stu-id="23baf-162">Fix assembly info generation</span></span>

<span data-ttu-id="23baf-163">.NET Framework ile oluşturulan Windows Forms projeleri içeren bir `AssemblyInfo.cs` oluşturulacak derlemenin sürümü gibi derleme özniteliklerinin içeren dosya.</span><span class="sxs-lookup"><span data-stu-id="23baf-163">Windows Forms projects that were created with .NET Framework include an `AssemblyInfo.cs` file, which contains assembly attributes such as the version of the assembly to be generated.</span></span> <span data-ttu-id="23baf-164">SDK stili projeleri, bu bilgileri size SDK proje dosyasını temel alarak otomatik olarak oluşturur.</span><span class="sxs-lookup"><span data-stu-id="23baf-164">SDK-style projects automatically generate this information for you based on the SDK project file.</span></span> <span data-ttu-id="23baf-165">Her iki "bütünleştirilmiş kod bilgileri" türüne sahip olan bir çakışma oluşturur.</span><span class="sxs-lookup"><span data-stu-id="23baf-165">Having both types of "assembly info" creates a conflict.</span></span> <span data-ttu-id="23baf-166">Mevcut kullanmak için projeyi otomatik oluşturma devre dışı bırakarak bu sorunu gidermek `AssemblyInfo.cs` dosya.</span><span class="sxs-lookup"><span data-stu-id="23baf-166">Resolve this problem by disabling automatic generation, which forces the project to use your existing `AssemblyInfo.cs` file.</span></span>

<span data-ttu-id="23baf-167">Ana eklemek için üç seçenek vardır `<PropertyGroup>` düğümü.</span><span class="sxs-lookup"><span data-stu-id="23baf-167">There are three settings to add to the main `<PropertyGroup>` node.</span></span> 

- <span data-ttu-id="23baf-168">**GenerateAssemblyInfo**\\</span><span class="sxs-lookup"><span data-stu-id="23baf-168">**GenerateAssemblyInfo**\\</span></span>
<span data-ttu-id="23baf-169">Bu özelliği ayarlandığında `false`, derleme öznitelikleri üretmeyeceğini.</span><span class="sxs-lookup"><span data-stu-id="23baf-169">When you set this property to `false`, it won't generate the assembly attributes.</span></span> <span data-ttu-id="23baf-170">Bu mevcut çakışmayı önler `AssemblyInfo.cs` .NET Framework proje dosyası.</span><span class="sxs-lookup"><span data-stu-id="23baf-170">This avoids the conflict with the existing `AssemblyInfo.cs` file from the .NET Framework project.</span></span>

- <span data-ttu-id="23baf-171">**AssemblyName**\\</span><span class="sxs-lookup"><span data-stu-id="23baf-171">**AssemblyName**\\</span></span>
<span data-ttu-id="23baf-172">Bu özellik, derlerken oluşturulan çıktıyı ikili değerdir.</span><span class="sxs-lookup"><span data-stu-id="23baf-172">The value of this property is the output binary created when you compile.</span></span> <span data-ttu-id="23baf-173">Ad, kendisine eklenmiş bir uzantı gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="23baf-173">The name doesn't need an extension added to it.</span></span> <span data-ttu-id="23baf-174">Örneğin, kullanarak `MyCoreApp` üretir `MyCoreApp.exe`.</span><span class="sxs-lookup"><span data-stu-id="23baf-174">For example, using `MyCoreApp` produces `MyCoreApp.exe`.</span></span>

- <span data-ttu-id="23baf-175">**RootNamespace**\\</span><span class="sxs-lookup"><span data-stu-id="23baf-175">**RootNamespace**\\</span></span>
<span data-ttu-id="23baf-176">Projeniz tarafından kullanılan varsayılan ad alanı.</span><span class="sxs-lookup"><span data-stu-id="23baf-176">The default namespace used by your project.</span></span> <span data-ttu-id="23baf-177">Bu, .NET Framework projenin varsayılan ad alanı eşleşmelidir.</span><span class="sxs-lookup"><span data-stu-id="23baf-177">This should match the default namespace of the .NET Framework project.</span></span>

<span data-ttu-id="23baf-178">Bu üç öğelerine ekleme `<PropertyGroup>` düğümünde `MyFormsCore.csproj` dosyası:</span><span class="sxs-lookup"><span data-stu-id="23baf-178">Add these three elements to the `<PropertyGroup>` node in the `MyFormsCore.csproj` file:</span></span>

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

## <a name="add-source-code"></a><span data-ttu-id="23baf-179">Kaynak kodu ekleme</span><span class="sxs-lookup"><span data-stu-id="23baf-179">Add source code</span></span>

<span data-ttu-id="23baf-180">Şu anda **MyFormsCore.csproj** herhangi bir kod projesi derleme değil.</span><span class="sxs-lookup"><span data-stu-id="23baf-180">Right now, the **MyFormsCore.csproj** project doesn't compile any code.</span></span> <span data-ttu-id="23baf-181">Varsayılan olarak, .NET Core projeleri otomatik olarak geçerli dizin ve alt dizinleri içinde tüm kaynak kodu içerir.</span><span class="sxs-lookup"><span data-stu-id="23baf-181">By default, .NET Core projects automatically include all source code in the current directory and any child directories.</span></span> <span data-ttu-id="23baf-182">Proje göreli yolu kullanarak .NET Framework projesinin koddan içerecek şekilde yapılandırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="23baf-182">You must configure the project to include code from the .NET Framework project using a relative path.</span></span> <span data-ttu-id="23baf-183">.NET Framework projenizin kullandıysanız **.resx** simgeler için dosyaları ve kaynaklar formlarınızı için gereken çok içerir.</span><span class="sxs-lookup"><span data-stu-id="23baf-183">If your .NET Framework project used **.resx** files for icons and resources for your forms, you'll need to include those too.</span></span> 

<span data-ttu-id="23baf-184">Aşağıdaki `<ItemGroup>` projenize düğümü.</span><span class="sxs-lookup"><span data-stu-id="23baf-184">Add the following `<ItemGroup>` node to your project.</span></span> <span data-ttu-id="23baf-185">Her deyim alt dizinleri içeren bir dosya glob deseni içerir.</span><span class="sxs-lookup"><span data-stu-id="23baf-185">Each statement includes a file glob pattern that includes child directories.</span></span>

```xml
  <ItemGroup>
    <Compile Include="..\MyFormsApp\**\*.cs" />
    <EmbeddedResource Include="..\MyFormsApp\**\*.resx" />
  </ItemGroup>
```

<span data-ttu-id="23baf-186">Alternatif olarak, oluşturabileceğiniz bir `<Compile>` veya `<EmbeddedResource>` zaman.NET Framework projenizin her dosya için giriş.</span><span class="sxs-lookup"><span data-stu-id="23baf-186">Alternatively, you can create a `<Compile>` or `<EmbeddedResource>` entry for each file in your .NET Framework project.</span></span>

## <a name="add-nuget-packages"></a><span data-ttu-id="23baf-187">NuGet paketleri Ekle</span><span class="sxs-lookup"><span data-stu-id="23baf-187">Add NuGet packages</span></span>

<span data-ttu-id="23baf-188">.NET Core projesi .NET Framework proje tarafından başvurulan her NuGet paketini ekleyin.</span><span class="sxs-lookup"><span data-stu-id="23baf-188">Add each NuGet package referenced by the .NET Framework project to the .NET Core project.</span></span> 

<span data-ttu-id="23baf-189">Büyük olasılıkla, .NET Framework Windows Forms uygulaması olan bir **packages.config** projeniz tarafından başvurulan NuGet paketlerinin bir listesini içeren dosya.</span><span class="sxs-lookup"><span data-stu-id="23baf-189">Most likely your .NET Framework Windows Forms app has a **packages.config** file that contains a list of all of the NuGet packages that are referenced by your project.</span></span> <span data-ttu-id="23baf-190">.NET Core projesine eklemek için hangi NuGet paketlerini belirlemek için bu listeye bakabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="23baf-190">You can look at this list to determine which NuGet packages to add to the .NET Core project.</span></span> <span data-ttu-id="23baf-191">Örneğin, .NET Framework projesinin başvurulan `MetroFramework`, `MetroFramework.Design`, ve `MetroFramework.Fonts` NuGet paketleri Ekle her projeye sahip Visual Studio veya .NET Core CLI üzerinden **SolutionFolder** dizini :</span><span class="sxs-lookup"><span data-stu-id="23baf-191">For example, if the .NET Framework project referenced the `MetroFramework`, `MetroFramework.Design`, and `MetroFramework.Fonts` NuGet packages, add each to the project with either Visual Studio or the .NET Core CLI from the **SolutionFolder** directory:</span></span>

```cli
dotnet add .\MyFormsAppCore\MyFormsCore.csproj package MetroFramework
dotnet add .\MyFormsAppCore\MyFormsCore.csproj package MetroFramework.Design
dotnet add .\MyFormsAppCore\MyFormsCore.csproj package MetroFramework.Fonts
```

<span data-ttu-id="23baf-192">Yukarıdaki komutları aşağıdaki NuGet başvuruları eklersiniz **MyFormsCore.csproj** proje:</span><span class="sxs-lookup"><span data-stu-id="23baf-192">The previous commands would add the following NuGet references to the **MyFormsCore.csproj** project:</span></span>

```xml
  <ItemGroup>
    <PackageReference Include="MetroFramework" Version="1.2.0.3" />
    <PackageReference Include="MetroFramework.Design" Version="1.2.0.3" />
    <PackageReference Include="MetroFramework.Fonts" Version="1.2.0.3" />
  </ItemGroup>
```

## <a name="port-control-libraries"></a><span data-ttu-id="23baf-193">Bağlantı noktası denetimi kitaplıkları</span><span class="sxs-lookup"><span data-stu-id="23baf-193">Port control libraries</span></span>

<span data-ttu-id="23baf-194">Bağlantı noktası için bir Windows Forms Denetim Kitaplığı projesi varsa, yönergeleri birkaç ayarı dışında bir .NET Framework Windows Forms uygulaması projesi taşıma ile aynı olur.</span><span class="sxs-lookup"><span data-stu-id="23baf-194">If you have a Windows Forms Controls library project to port, the directions are the same as porting a .NET Framework Windows Forms app project, except for a few settings.</span></span> <span data-ttu-id="23baf-195">Ve bir yürütülebilir dosya için derleme yerine, bir kitaplık için derleyin.</span><span class="sxs-lookup"><span data-stu-id="23baf-195">And instead of compiling to an executable, you compile to a library.</span></span> <span data-ttu-id="23baf-196">Yürütülebilir projeyi, kaynak kodunuzu içeren dosyayı eğik çizgi genelleştirmeler yolları yanı sıra kitaplık projesi arasındaki fark, en alt düzeydedir.</span><span class="sxs-lookup"><span data-stu-id="23baf-196">The difference between the executable project and the library project, besides paths for the file globs that include your source code, is minimal.</span></span>

<span data-ttu-id="23baf-197">Önceki adım örneği kullanarak, hangi projeleri ve dosyaları ile çalışıyoruz genişletin olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="23baf-197">Using the previous step's example, lets expand what projects and files we're working with.</span></span>

| <span data-ttu-id="23baf-198">Dosya</span><span class="sxs-lookup"><span data-stu-id="23baf-198">File</span></span> | <span data-ttu-id="23baf-199">Açıklama</span><span class="sxs-lookup"><span data-stu-id="23baf-199">Description</span></span> |
| ---- | ----------- |
| <span data-ttu-id="23baf-200">**MyApps.sln**</span><span class="sxs-lookup"><span data-stu-id="23baf-200">**MyApps.sln**</span></span> | <span data-ttu-id="23baf-201">Çözüm dosyasının adı.</span><span class="sxs-lookup"><span data-stu-id="23baf-201">The name of the solution file.</span></span> |
| <span data-ttu-id="23baf-202">**MyControls.csproj**</span><span class="sxs-lookup"><span data-stu-id="23baf-202">**MyControls.csproj**</span></span> | <span data-ttu-id="23baf-203">Bağlantı noktası için .NET Framework Windows Forms denetimleri projesinin adı.</span><span class="sxs-lookup"><span data-stu-id="23baf-203">The name of the .NET Framework Windows Forms Controls project to port.</span></span> |
| <span data-ttu-id="23baf-204">**MyControlsCore.csproj**</span><span class="sxs-lookup"><span data-stu-id="23baf-204">**MyControlsCore.csproj**</span></span> | <span data-ttu-id="23baf-205">Oluşturduğunuz yeni .NET Core kitaplığı proje adı.</span><span class="sxs-lookup"><span data-stu-id="23baf-205">The name of the new .NET Core library project you create.</span></span> |
| <span data-ttu-id="23baf-206">**MyCoreControls.dll**</span><span class="sxs-lookup"><span data-stu-id="23baf-206">**MyCoreControls.dll**</span></span> | <span data-ttu-id="23baf-207">.NET Core Windows Forms Denetim Kitaplığı.</span><span class="sxs-lookup"><span data-stu-id="23baf-207">The .NET Core Windows Forms Controls library.</span></span> |

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

<span data-ttu-id="23baf-208">Arasındaki farklılıkları dikkate `MyControlsCore.csproj` proje ve önceden oluşturulmuş `MyFormsCore.csproj` proje.</span><span class="sxs-lookup"><span data-stu-id="23baf-208">Consider the differences between the `MyControlsCore.csproj` project and the previously created `MyFormsCore.csproj` project.</span></span>

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

<span data-ttu-id="23baf-209">.NET Core Windows Forms Denetim Kitaplığı proje dosyası aşağıdaki gibi görünür bir örnek aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="23baf-209">Here is an example of what the .NET Core Windows Forms Controls library project file would look like:</span></span>

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

<span data-ttu-id="23baf-210">Gördüğünüz gibi `<OutputType>` düğüm kaldırıldı, bunun yerine bir yürütülebilir dosya bir kitaplığı oluşturmak için derleyicinin varsayılan.</span><span class="sxs-lookup"><span data-stu-id="23baf-210">As you can see, the `<OutputType>` node was removed, which defaults the compiler to produce a library instead of an executable.</span></span> <span data-ttu-id="23baf-211">`<AssemblyName>` Ve `<RootNamespace>` değiştirildi.</span><span class="sxs-lookup"><span data-stu-id="23baf-211">The `<AssemblyName>` and `<RootNamespace>` were changed.</span></span> <span data-ttu-id="23baf-212">Özellikle `<RootNamespace>` taşıma Windows Forms denetimleri kitaplığının ad alanı ile eşleşmelidir.</span><span class="sxs-lookup"><span data-stu-id="23baf-212">Specifically the `<RootNamespace>` should match the namespace of the Windows Forms Controls library you are porting.</span></span> <span data-ttu-id="23baf-213">Son olarak, `<Compile>` ve `<EmbeddedResource>` düğümleri taşıma Windows Forms denetimleri Kitaplık klasörüne işaret edecek şekilde ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="23baf-213">And finally, the `<Compile>` and `<EmbeddedResource>` nodes were adjusted to point to the folder of the Windows Forms Controls library you are porting.</span></span>

<span data-ttu-id="23baf-214">Sonra ana .NET core'da **MyFormsCore.csproj** projeye yeni .NET Core Windows Forms Denetim Kitaplığı için başvuru ekleyin.</span><span class="sxs-lookup"><span data-stu-id="23baf-214">Next, in the main .NET Core **MyFormsCore.csproj** project add reference to the new .NET Core Windows Forms Control library.</span></span> <span data-ttu-id="23baf-215">Visual Studio veya .NET Core CLI ile bir başvuru ekleyin **SolutionFolder** dizini:</span><span class="sxs-lookup"><span data-stu-id="23baf-215">Add a reference with either Visual Studio or the .NET Core CLI from the **SolutionFolder** directory:</span></span>

```cli
dotnet add .\MyFormsAppCore\MyFormsCore.csproj reference .\MyFormsControlsCore\MyControlsCore.csproj
```

<span data-ttu-id="23baf-216">Önceki komutta aşağıdaki ekler **MyFormsCore.csproj** proje:</span><span class="sxs-lookup"><span data-stu-id="23baf-216">The previous command adds the following to the **MyFormsCore.csproj** project:</span></span>

```xml
  <ItemGroup>
    <ProjectReference Include="..\MyFormsControlsCore\MyControlsCore.csproj" />
  </ItemGroup>
```

## <a name="problems-compiling"></a><span data-ttu-id="23baf-217">Derleme sorunları</span><span class="sxs-lookup"><span data-stu-id="23baf-217">Problems compiling</span></span>

<span data-ttu-id="23baf-218">Projelerinizi derleme sorunlarla karşılaşırsanız, .NET Framework'de kullanılabilen ancak .NET core'da kullanılamaz olan bazı yalnızca Windows API'leri kullanıyor olabilir.</span><span class="sxs-lookup"><span data-stu-id="23baf-218">If you have problems compiling your projects, you may be using some Windows-only APIs that are available in .NET Framework but not available in .NET Core.</span></span> <span data-ttu-id="23baf-219">Eklemeyi deneyin [Windows Uyumluluk Paketi] [ compat-pack] NuGet paketini projenize.</span><span class="sxs-lookup"><span data-stu-id="23baf-219">You can try adding the [Windows Compatibility Pack][compat-pack] NuGet package to your project.</span></span> <span data-ttu-id="23baf-220">Bu paket, yalnızca Windows üzerinde çalışır ve yaklaşık 20.000 Windows API'leri, .NET Core ve .NET Standard projelerine ekler.</span><span class="sxs-lookup"><span data-stu-id="23baf-220">This package only runs on Windows and adds about 20,000 Windows APIs to .NET Core and .NET Standard projects.</span></span>

```cli
dotnet add .\MyFormsAppCore\MyFormsCore.csproj package Microsoft.Windows.Compatibility
```

<span data-ttu-id="23baf-221">Önceki komutta aşağıdaki ekler **MyFormsCore.csproj** proje:</span><span class="sxs-lookup"><span data-stu-id="23baf-221">The previous command adds the following to the **MyFormsCore.csproj** project:</span></span>

```xml
  <ItemGroup>
    <PackageReference Include="Microsoft.Windows.Compatibility" Version="2.0.1" />
  </ItemGroup>
```

## <a name="windows-forms-designer"></a><span data-ttu-id="23baf-222">Windows Form Tasarımcısı</span><span class="sxs-lookup"><span data-stu-id="23baf-222">Windows Forms Designer</span></span>

<span data-ttu-id="23baf-223">Ayrıntılı olarak açıklanan bu makalede, Visual Studio 2019 yalnızca Form Tasarımcısı .NET Framework projelerinde destekler.</span><span class="sxs-lookup"><span data-stu-id="23baf-223">As detailed in this article, Visual Studio 2019 only supports the Forms Designer in .NET Framework projects.</span></span> <span data-ttu-id="23baf-224">Yan yana .NET Core projesi oluşturarak, .NET Framework projesinin tasarım formlara kullanırken projeniz .NET Core ile test edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="23baf-224">By creating a side-by-side .NET Core project, you can test your project with .NET Core while you use the .NET Framework project to design forms.</span></span> <span data-ttu-id="23baf-225">Çözüm dosyanız .NET Framework ve .NET Core projeleri içerir.</span><span class="sxs-lookup"><span data-stu-id="23baf-225">Your solution file includes both the .NET Framework and .NET Core projects.</span></span> <span data-ttu-id="23baf-226">Ekleme, formlar ve denetimler .NET Framework projesinde tasarım ve üzerinde dosya glob desenlerinin ekledik .NET Core projeleri için herhangi bir yeni veya değiştirilen dosyaları otomatik olarak .NET Core projelerinde dahil edilir.</span><span class="sxs-lookup"><span data-stu-id="23baf-226">Add and design your forms and controls in the .NET Framework project, and based on the file glob patterns we added to the .NET Core projects, any new or changed files will automatically be included in the .NET Core projects.</span></span>

<span data-ttu-id="23baf-227">Visual Studio 2019 Windows Form Tasarımcısı'nı destekler. sonra kopyalama/.NET Core proje dosyanızın içeriğini .NET Framework proje dosyasına yapıştırma.</span><span class="sxs-lookup"><span data-stu-id="23baf-227">Once Visual Studio 2019 supports the Windows Forms Designer, you can copy/paste the content of your .NET Core project file into the .NET Framework project file.</span></span> <span data-ttu-id="23baf-228">Eklenen dosya glob desenlerinin delete `<Source>` ve `<EmbeddedResource>` öğeleri.</span><span class="sxs-lookup"><span data-stu-id="23baf-228">Then delete the file glob patterns added with the `<Source>` and `<EmbeddedResource>` items.</span></span> <span data-ttu-id="23baf-229">Uygulamanız tarafından kullanılan herhangi bir proje başvurusu yolları düzeltin.</span><span class="sxs-lookup"><span data-stu-id="23baf-229">Fix the paths to any project reference used by your app.</span></span> <span data-ttu-id="23baf-230">Bu .NET Framework projesi bir .NET Core projesinden etkili bir şekilde yükseltir.</span><span class="sxs-lookup"><span data-stu-id="23baf-230">This effectively upgrades the .NET Framework project to a .NET Core project.</span></span>
 
## <a name="next-steps"></a><span data-ttu-id="23baf-231">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="23baf-231">Next steps</span></span>

* <span data-ttu-id="23baf-232">Daha fazla bilgi edinin [Windows Uyumluluk Paketi][compat-pack].</span><span class="sxs-lookup"><span data-stu-id="23baf-232">Read more about the [Windows Compatibility Pack][compat-pack].</span></span>
* <span data-ttu-id="23baf-233">İzleme bir [taşıma video](https://www.youtube.com/watch?v=upVQEUc_KwU) .NET Core, .NET Framework Windows Forms projesi.</span><span class="sxs-lookup"><span data-stu-id="23baf-233">Watch a [video on porting](https://www.youtube.com/watch?v=upVQEUc_KwU) your .NET Framework Windows Forms project to .NET Core.</span></span>

[compat-pack]: windows-compat-pack.md
