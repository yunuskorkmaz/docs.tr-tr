---
title: ​.NET Core 3.0’daki yenilikler
description: .NET Core 3,0 ' de bulunan yeni özellikler hakkında bilgi edinin.
dev_langs:
- csharp
- vb
author: thraka
ms.author: adegeo
ms.date: 08/21/2019
ms.openlocfilehash: f62afe79ec3ace98a3bd8997e20672bef81b89c4
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70037843"
---
# <a name="whats-new-in-net-core-30-preview-8"></a><span data-ttu-id="eb2bd-103">.NET Core 3,0 'deki yenilikler (Önizleme 8)</span><span class="sxs-lookup"><span data-stu-id="eb2bd-103">What's new in .NET Core 3.0 (Preview 8)</span></span>

<span data-ttu-id="eb2bd-104">Bu makalede .NET Core 3,0 'deki yenilikler açıklanmaktadır (Preview 8 ' den fazla).</span><span class="sxs-lookup"><span data-stu-id="eb2bd-104">This article describes what is new in .NET Core 3.0 (through preview 8).</span></span> <span data-ttu-id="eb2bd-105">En büyük geliştirmelerden biri, Windows Masaüstü uygulamaları için destek içerir (yalnızca Windows).</span><span class="sxs-lookup"><span data-stu-id="eb2bd-105">One of the biggest enhancements is support for Windows desktop applications (Windows only).</span></span> <span data-ttu-id="eb2bd-106">.NET Core 3,0 SDK bileşeni Windows Masaüstü 'Nü kullanarak Windows Forms ve Windows Presentation Foundation (WPF) uygulamalarınızın bağlantı noktası oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="eb2bd-106">By using the .NET Core 3.0 SDK component Windows Desktop, you can port your Windows Forms and Windows Presentation Foundation (WPF) applications.</span></span> <span data-ttu-id="eb2bd-107">Temiz olması için, Windows Masaüstü bileşeni yalnızca Windows 'da desteklenir ve Windows 'a dahildir.</span><span class="sxs-lookup"><span data-stu-id="eb2bd-107">To be clear, the Windows Desktop component is only supported and included on Windows.</span></span> <span data-ttu-id="eb2bd-108">Daha fazla bilgi için bu makalenin devamındaki [Windows Masaüstü](#windows-desktop) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="eb2bd-108">For more information, see the [Windows desktop](#windows-desktop) section later in this article.</span></span>

<span data-ttu-id="eb2bd-109">.NET Core 3,0, 8,0 için C# destek ekler.</span><span class="sxs-lookup"><span data-stu-id="eb2bd-109">.NET Core 3.0 adds support for C# 8.0.</span></span> <span data-ttu-id="eb2bd-110">[En son Visual Studio Preview](https://visualstudio.microsoft.com/vs/preview/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+preview)sürümünü kullanmanız veya OmniSharp uzantısıyla Visual Studio Code önerilir.</span><span class="sxs-lookup"><span data-stu-id="eb2bd-110">It's highly recommended that you use the [latest release of Visual Studio Preview](https://visualstudio.microsoft.com/vs/preview/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+preview), or Visual Studio Code with the OmniSharp extension.</span></span>

<span data-ttu-id="eb2bd-111">Şimdi Windows, macOS veya Linux 'ta [.NET Core 3,0 Preview 8 ' i indirin ve kullanmaya](https://aka.ms/netcore3download) başlayın.</span><span class="sxs-lookup"><span data-stu-id="eb2bd-111">[Download and get started with .NET Core 3.0 preview 8](https://aka.ms/netcore3download) right now on Windows, macOS, or Linux.</span></span>

<span data-ttu-id="eb2bd-112">Her önizleme sürümü hakkında daha fazla bilgi için aşağıdaki duyurulara bakın:</span><span class="sxs-lookup"><span data-stu-id="eb2bd-112">For more information about each preview release, see the following announcements:</span></span>

- [<span data-ttu-id="eb2bd-113">.NET Core 3,0 Preview 8 duyurusu</span><span class="sxs-lookup"><span data-stu-id="eb2bd-113">.NET Core 3.0 Preview 8 announcement</span></span>](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-0-preview-8/)
- [<span data-ttu-id="eb2bd-114">.NET Core 3,0 Preview 7 duyurusu</span><span class="sxs-lookup"><span data-stu-id="eb2bd-114">.NET Core 3.0 Preview 7 announcement</span></span>](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-0-preview-7/)
- [<span data-ttu-id="eb2bd-115">.NET Core 3,0 Preview 6 duyurusu</span><span class="sxs-lookup"><span data-stu-id="eb2bd-115">.NET Core 3.0 Preview 6 announcement</span></span>](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-0-preview-6/)
- [<span data-ttu-id="eb2bd-116">.NET Core 3,0 Preview 5 duyurusu</span><span class="sxs-lookup"><span data-stu-id="eb2bd-116">.NET Core 3.0 Preview 5 announcement</span></span>](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-0-preview-5/)
- [<span data-ttu-id="eb2bd-117">.NET Core 3,0 Preview 4 duyurusu</span><span class="sxs-lookup"><span data-stu-id="eb2bd-117">.NET Core 3.0 Preview 4 announcement</span></span>](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-preview-4/)
- [<span data-ttu-id="eb2bd-118">.NET Core 3,0 Preview 3 duyurusu</span><span class="sxs-lookup"><span data-stu-id="eb2bd-118">.NET Core 3.0 Preview 3 announcement</span></span>](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-preview-3/)
- [<span data-ttu-id="eb2bd-119">.NET Core 3,0 Preview 2 duyurusu</span><span class="sxs-lookup"><span data-stu-id="eb2bd-119">.NET Core 3.0 Preview 2 announcement</span></span>](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-preview-2/)
- [<span data-ttu-id="eb2bd-120">.NET Core 3,0 Preview 1 ilanı</span><span class="sxs-lookup"><span data-stu-id="eb2bd-120">.NET Core 3.0 Preview 1 announcement</span></span>](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-preview-1-and-open-sourcing-windows-desktop-frameworks/)

## <a name="production-supported-preview"></a><span data-ttu-id="eb2bd-121">Üretim için desteklenen Önizleme</span><span class="sxs-lookup"><span data-stu-id="eb2bd-121">Production supported preview</span></span>

<span data-ttu-id="eb2bd-122">.NET Core Preview 8, Microsoft tarafından önceden hazırlanarak üretim olarak kabul edilir ve tam olarak desteklenmektedir.</span><span class="sxs-lookup"><span data-stu-id="eb2bd-122">.NET Core Preview 8 is considered production ready by Microsoft and is fully supported.</span></span> <span data-ttu-id="eb2bd-123">Sürüm 7 ' den itibaren, yayınlar yeni özellikler eklemek yerine polishing .NET Core 3,0 ' ye odaklanacaktır.</span><span class="sxs-lookup"><span data-stu-id="eb2bd-123">Starting with preview 7, releases will focus on polishing .NET Core 3.0 instead of adding new features.</span></span> <span data-ttu-id="eb2bd-124">Preview 8 ' de nelerin değiştiği hakkında daha fazla bilgi için, [Preview 8 duyurusu](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-0-preview-8/)' ne bakın.</span><span class="sxs-lookup"><span data-stu-id="eb2bd-124">For more information about what has changed in preview 8, see the [preview 8 announcement](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-0-preview-8/).</span></span>

<span data-ttu-id="eb2bd-125">Önceki bir önizleme sürümünü kullanıyorsanız devam eden "canlı çalış" desteği için Preview 8 ' e geçmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="eb2bd-125">If you're using a previous preview release, you must move to Preview 8 for continued "Go Live" support.</span></span>

## <a name="net-core-sdk-windows-installer"></a><span data-ttu-id="eb2bd-126">.NET Core SDK Windows Installer</span><span class="sxs-lookup"><span data-stu-id="eb2bd-126">.NET Core SDK Windows Installer</span></span>

<span data-ttu-id="eb2bd-127">Windows için MSI Yükleyicisi, .NET Core 3,0 ile başlayarak değiştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="eb2bd-127">The MSI installer for Windows has changed starting with .NET Core 3.0.</span></span> <span data-ttu-id="eb2bd-128">SDK yükleyicileri artık SDK özelliği bant sürümlerini yerinde yükseltecektir.</span><span class="sxs-lookup"><span data-stu-id="eb2bd-128">The SDK installers will now upgrade SDK feature-band releases in place.</span></span> <span data-ttu-id="eb2bd-129">Özellik bantları, sürüm numarasının *Patch* bölümündeki *yüzlerce* grupta tanımlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="eb2bd-129">Feature bands are defined in the *hundreds* groups in the *patch* section of the version number.</span></span> <span data-ttu-id="eb2bd-130">Örneğin, **3,0. _101_**  ve **3,0. _201_**  , 3,0 sırasında iki farklı özellik bantlarındaki sürümleridir **. _101_**  ve **3,0. _199_**  aynı özellik bandında.</span><span class="sxs-lookup"><span data-stu-id="eb2bd-130">For example, **3.0._101_** and **3.0._201_** are versions in two different feature bands while **3.0._101_** and **3.0._199_** are in the same feature band.</span></span> <span data-ttu-id="eb2bd-131">.NET Core SDK **3,0 olduğunda. _101_**  .NET Core SDK yüklendi, **3,0. _100_**  , varsa makineden kaldırılacak.</span><span class="sxs-lookup"><span data-stu-id="eb2bd-131">And, when .NET Core SDK **3.0._101_** is installed, .NET Core SDK **3.0._100_** will be removed from the machine if it exists.</span></span> <span data-ttu-id="eb2bd-132">.NET Core SDK **3,0. _200_**  , .NET Core SDK 3,0 ' de aynı makineye yüklendi **. _101_**  kaldırılmaz.</span><span class="sxs-lookup"><span data-stu-id="eb2bd-132">When .NET Core SDK **3.0._200_** is installed on the same machine, .NET Core SDK **3.0._101_** won't be removed.</span></span>

<span data-ttu-id="eb2bd-133">Sürüm oluşturma hakkında daha fazla bilgi için bkz. [.NET Core 'un sürümü oluşturma konusuna genel bakış](../versions/index.md).</span><span class="sxs-lookup"><span data-stu-id="eb2bd-133">For more information about versioning, see [Overview of how .NET Core is versioned](../versions/index.md).</span></span>

## <a name="c-80-preview"></a><span data-ttu-id="eb2bd-134">C#8,0 Önizleme</span><span class="sxs-lookup"><span data-stu-id="eb2bd-134">C# 8.0 preview</span></span>

<span data-ttu-id="eb2bd-135">.NET Core 3,0, C# 8 önizlemeyi destekler.</span><span class="sxs-lookup"><span data-stu-id="eb2bd-135">.NET Core 3.0 supports C# 8 preview.</span></span> <span data-ttu-id="eb2bd-136">8,0 özellikleri hakkında C# daha fazla bilgi için bkz. [ C# 8,0](../../csharp/whats-new/csharp-8.md)sürümündeki yenilikler.</span><span class="sxs-lookup"><span data-stu-id="eb2bd-136">For more information about C# 8.0 features, see [What's new in C# 8.0](../../csharp/whats-new/csharp-8.md).</span></span>

## <a name="net-standard-21"></a><span data-ttu-id="eb2bd-137">.NET Standard 2,1</span><span class="sxs-lookup"><span data-stu-id="eb2bd-137">.NET Standard 2.1</span></span>

<span data-ttu-id="eb2bd-138">.NET Core 3,0 **.NET Standard 2,1**' yi desteklese de, `dotnet new classlib` varsayılan şablon **.NET Standard 2,0**' i hedefleyen bir proje oluşturur.</span><span class="sxs-lookup"><span data-stu-id="eb2bd-138">Even though .NET Core 3.0 supports **.NET Standard 2.1**, the default `dotnet new classlib` template generates a project that targets **.NET Standard 2.0**.</span></span> <span data-ttu-id="eb2bd-139">**.NET Standard 2,1**' i hedeflemek için proje dosyanızı düzenleyin ve `TargetFramework` özelliği şu şekilde `netstandard2.1`değiştirin:</span><span class="sxs-lookup"><span data-stu-id="eb2bd-139">To target **.NET Standard 2.1**, edit your project file and change the `TargetFramework` property to `netstandard2.1`:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <TargetFramework>netstandard2.1</TargetFramework>
  </PropertyGroup>

</Project>
```

<span data-ttu-id="eb2bd-140">Visual Studio kullanıyorsanız, Visual Studio 2017 **.NET Standard 2,1** veya **.NET Core 3,0**' i desteklemediğinden [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019)gerekir.</span><span class="sxs-lookup"><span data-stu-id="eb2bd-140">If you're using Visual Studio, you need [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019), as Visual Studio 2017 doesn't support **.NET Standard 2.1** or **.NET Core 3.0**.</span></span>

## <a name="improved-net-core-version-apis"></a><span data-ttu-id="eb2bd-141">Geliştirilmiş .NET Core sürümü API 'Leri</span><span class="sxs-lookup"><span data-stu-id="eb2bd-141">Improved .NET Core Version APIs</span></span>

<span data-ttu-id="eb2bd-142">.NET Core 3,0 ile başlayarak, .NET Core ile birlikte sunulan sürüm API 'Leri artık istediğiniz bilgileri döndürür.</span><span class="sxs-lookup"><span data-stu-id="eb2bd-142">Starting with .NET Core 3.0, the version APIs provided with .NET Core now return the information you expect.</span></span> <span data-ttu-id="eb2bd-143">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="eb2bd-143">For example:</span></span>

```csharp
System.Console.WriteLine($"Environment.Version: {System.Environment.Version}");

// Old result
//   Environment.Version: 4.0.30319.42000
//
// New result
//   Environment.Version: 3.0.0
```

```csharp
System.Console.WriteLine($"RuntimeInformation.FrameworkDescription: {System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription}");

// Old result
//   RuntimeInformation.FrameworkDescription: .NET Core 4.6.27415.71
//
// New result
//   RuntimeInformation.FrameworkDescription: .NET Core 3.0.0-preview4-27615-11
```

> [!WARNING]
> <span data-ttu-id="eb2bd-144">Son değişiklik.</span><span class="sxs-lookup"><span data-stu-id="eb2bd-144">Breaking change.</span></span> <span data-ttu-id="eb2bd-145">Bu teknik açıdan önemli bir değişiklik olduğundan, sürüm oluşturma düzeni değişti.</span><span class="sxs-lookup"><span data-stu-id="eb2bd-145">This is technically a breaking change because the versioning scheme has changed.</span></span>

## <a name="net-platform-dependent-intrinsics"></a><span data-ttu-id="eb2bd-146">.NET platforma bağımlı Iç bilgiler</span><span class="sxs-lookup"><span data-stu-id="eb2bd-146">.NET Platform-Dependent Intrinsics</span></span>

<span data-ttu-id="eb2bd-147">**SIMD** veya **bit işleme yönergesi** kümeleri gıbı belirli performans yönelimli CPU yönergelerine erişime izin veren API 'ler eklenmiştir.</span><span class="sxs-lookup"><span data-stu-id="eb2bd-147">APIs have been added that allow access to certain perf-oriented CPU instructions, such as the **SIMD** or **Bit Manipulation instruction** sets.</span></span> <span data-ttu-id="eb2bd-148">Bu yönergeler, verileri paralel şekilde işleme gibi belirli senaryolarda önemli performans geliştirmeleri elde etmenize yardımcı olabilir.</span><span class="sxs-lookup"><span data-stu-id="eb2bd-148">These instructions can help achieve significant performance improvements in certain scenarios, such as processing data efficiently in parallel.</span></span>

<span data-ttu-id="eb2bd-149">Uygun durumlarda, .NET kitaplıkları performansı artırmak için bu yönergeleri kullanmaya başlamıştır.</span><span class="sxs-lookup"><span data-stu-id="eb2bd-149">Where appropriate, the .NET libraries have begun using these instructions to improve performance.</span></span>

<span data-ttu-id="eb2bd-150">Daha fazla bilgi için bkz. [.NET platformu bağımlı iç](https://github.com/dotnet/designs/blob/master/accepted/platform-intrinsics.md)öğeleri.</span><span class="sxs-lookup"><span data-stu-id="eb2bd-150">For more information, see [.NET Platform Dependent Intrinsics](https://github.com/dotnet/designs/blob/master/accepted/platform-intrinsics.md).</span></span>

## <a name="default-executables"></a><span data-ttu-id="eb2bd-151">Varsayılan yürütülebilir dosyalar</span><span class="sxs-lookup"><span data-stu-id="eb2bd-151">Default executables</span></span>

<span data-ttu-id="eb2bd-152">.NET Core artık [çerçeveye bağlı yürütülebilir dosyaları](../deploying/index.md#framework-dependent-executables-fde) varsayılan olarak oluşturur.</span><span class="sxs-lookup"><span data-stu-id="eb2bd-152">.NET Core now builds [framework-dependent executables](../deploying/index.md#framework-dependent-executables-fde) by default.</span></span> <span data-ttu-id="eb2bd-153">Bu davranış, .NET Core 'un küresel olarak yüklenen bir sürümünü kullanan uygulamalar için yenidir.</span><span class="sxs-lookup"><span data-stu-id="eb2bd-153">This behavior is new for applications that use a globally installed version of .NET Core.</span></span> <span data-ttu-id="eb2bd-154">Daha önce yalnızca [kendi kendine kapsanan dağıtımlar](../deploying/index.md#self-contained-deployments-scd) yürütülebilir bir dosya üretecektir.</span><span class="sxs-lookup"><span data-stu-id="eb2bd-154">Previously, only [self-contained deployments](../deploying/index.md#self-contained-deployments-scd) would produce an executable.</span></span>

<span data-ttu-id="eb2bd-155">`dotnet build` Veya`dotnet publish`sırasında, kullanmakta olduğunuz SDK ortamı ve platformuyla eşleşen bir yürütülebilir dosya oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="eb2bd-155">During `dotnet build` or `dotnet publish`, an executable is created that matches the environment and platform of the SDK you're using.</span></span> <span data-ttu-id="eb2bd-156">Bu yürütülebilir dosyalarla aynı şeyleri, diğer yerel yürütülebilir dosyaları gibi bekleyebilir, örneğin:</span><span class="sxs-lookup"><span data-stu-id="eb2bd-156">You can expect the same things with these executables as you would other native executables, such as:</span></span>

- <span data-ttu-id="eb2bd-157">Yürütülebilir dosyaya çift tıklayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="eb2bd-157">You can double-click on the executable.</span></span>
- <span data-ttu-id="eb2bd-158">Uygulamayı Windows ve `myapp.exe` `./myapp` Linux ve MacOS gibi bir komut isteminden doğrudan başlatabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="eb2bd-158">You can launch the application from a command prompt directly, such as `myapp.exe` on Windows, and `./myapp` on Linux and macOS.</span></span>

## <a name="single-file-executables"></a><span data-ttu-id="eb2bd-159">Tek dosya yürütülebilir dosyaları</span><span class="sxs-lookup"><span data-stu-id="eb2bd-159">Single-file executables</span></span>

<span data-ttu-id="eb2bd-160">Komut `dotnet publish` , uygulamanızı platforma özgü tek dosya yürütülebilir dosyasına paketlemeyi destekler.</span><span class="sxs-lookup"><span data-stu-id="eb2bd-160">The `dotnet publish` command supports packaging your app into a platform-specific single-file executable.</span></span> <span data-ttu-id="eb2bd-161">Yürütülebilir dosya kendiliğinden ayıklanıyor ve uygulamanızı çalıştırmak için gerekli tüm bağımlılıkları (yerel dahil) içerir.</span><span class="sxs-lookup"><span data-stu-id="eb2bd-161">The executable is self-extracting and contains all dependencies (including native) that are required to run your app.</span></span> <span data-ttu-id="eb2bd-162">Uygulama ilk kez çalıştırıldığında uygulama adı ve derleme tanımlayıcısı temelinde bir dizine çıkarılır.</span><span class="sxs-lookup"><span data-stu-id="eb2bd-162">When the app is first run, the application is extracted to a directory based on the app name and build identifier.</span></span> <span data-ttu-id="eb2bd-163">Uygulama yeniden çalıştırıldığında başlatma daha hızlıdır.</span><span class="sxs-lookup"><span data-stu-id="eb2bd-163">Startup is faster when the application is run again.</span></span> <span data-ttu-id="eb2bd-164">Yeni bir sürüm kullanılmadığı takdirde uygulamanın kendisi ikinci kez ayıklanmasına gerek yoktur.</span><span class="sxs-lookup"><span data-stu-id="eb2bd-164">The application doesn't need to extract itself a second time unless a new version was used.</span></span>

<span data-ttu-id="eb2bd-165">Tek dosya yürütülebiliri yayımlamak için, projenizdeki öğesini veya `PublishSingleFile` komut satırında `dotnet publish` komutunu komutuyla ayarlayın:</span><span class="sxs-lookup"><span data-stu-id="eb2bd-165">To publish a single-file executable, set the `PublishSingleFile` in your project or on the command line with the `dotnet publish` command:</span></span>

```xml
<PropertyGroup>
  <RuntimeIdentifier>win10-x64</RuntimeIdentifier>
  <PublishSingleFile>true</PublishSingleFile>
</PropertyGroup>
```

<span data-ttu-id="eb2bd-166">-veya-</span><span class="sxs-lookup"><span data-stu-id="eb2bd-166">-or-</span></span>

```console
dotnet publish -r win10-x64 /p:PublishSingleFile=true
```

<span data-ttu-id="eb2bd-167">Tek dosya yayınlama hakkında daha fazla bilgi için bkz. [tek dosya paketcisi tasarım belgesi](https://github.com/dotnet/designs/blob/master/accepted/single-file/design.md).</span><span class="sxs-lookup"><span data-stu-id="eb2bd-167">For more information about single-file publishing, see the [single-file bundler design document](https://github.com/dotnet/designs/blob/master/accepted/single-file/design.md).</span></span>

## <a name="assembly-linking"></a><span data-ttu-id="eb2bd-168">Bütünleştirilmiş kod bağlama</span><span class="sxs-lookup"><span data-stu-id="eb2bd-168">Assembly linking</span></span>

<span data-ttu-id="eb2bd-169">.NET Core 3,0 SDK, Il 'yi çözümleyerek ve kullanılmayan derlemeleri kırparak uygulamaların boyutunu azaltan bir araçla birlikte gelir.</span><span class="sxs-lookup"><span data-stu-id="eb2bd-169">The .NET core 3.0 SDK comes with a tool that can reduce the size of apps by analyzing IL and trimming unused assemblies.</span></span>

<span data-ttu-id="eb2bd-170">Bağımsız uygulamalar, kodunuzun çalıştırılması için gereken her şeyi, ana bilgisayara .NET yüklenmesini gerektirmeden içerir.</span><span class="sxs-lookup"><span data-stu-id="eb2bd-170">Self-contained apps include everything needed to run your code, without requiring .NET to be installed on the host computer.</span></span> <span data-ttu-id="eb2bd-171">Ancak, çoğu zaman uygulamanın çalışması için yalnızca küçük bir çerçeve alt kümesi gerekir ve kullanılmayan diğer kitaplıklar da kaldırılabilir.</span><span class="sxs-lookup"><span data-stu-id="eb2bd-171">However, many times the app only requires a small subset of the framework to function, and other unused libraries could be removed.</span></span>

<span data-ttu-id="eb2bd-172">.NET Core artık uygulamanızın Il 'sini taramak için [Il bağlayıcı](https://github.com/mono/linker) aracını kullanacak bir ayar içeriyor.</span><span class="sxs-lookup"><span data-stu-id="eb2bd-172">.NET Core now includes a setting that will use the [IL linker](https://github.com/mono/linker) tool to scan the IL of your app.</span></span> <span data-ttu-id="eb2bd-173">Bu araç hangi kodun gerekli olduğunu algılar ve ardından kullanılmayan kitaplıkları kırpar.</span><span class="sxs-lookup"><span data-stu-id="eb2bd-173">this tool detects what code is required, and then trims unused libraries.</span></span> <span data-ttu-id="eb2bd-174">Bu araç bazı uygulamaların dağıtım boyutunu önemli ölçüde azaltabilir.</span><span class="sxs-lookup"><span data-stu-id="eb2bd-174">This tool can significantly reduce the deployment size of some apps.</span></span>

<span data-ttu-id="eb2bd-175">Bu aracı etkinleştirmek için projenize `<PublishTrimmed>` ayarı ekleyin ve kendi içinde bulunan bir uygulamayı yayımlayın:</span><span class="sxs-lookup"><span data-stu-id="eb2bd-175">To enable this tool, add the `<PublishTrimmed>` setting in your project and publish a self-contained app:</span></span>

```xml
<PropertyGroup>
  <PublishTrimmed>true</PublishTrimmed>
</PropertyGroup>
```

```console
dotnet publish -r <rid> -c Release
```

<span data-ttu-id="eb2bd-176">Örnek olarak, yayımlanan temel "Merhaba Dünya" yeni konsol projesi şablonu, yayımlandığında 70 MB ile çarpılır.</span><span class="sxs-lookup"><span data-stu-id="eb2bd-176">As an example, the basic "hello world" new console project template that is included, when published, hits about 70 MB in size.</span></span> <span data-ttu-id="eb2bd-177">Kullanarak `<PublishTrimmed>`, bu boyut yaklaşık 30 MB 'ye indirilir.</span><span class="sxs-lookup"><span data-stu-id="eb2bd-177">By using `<PublishTrimmed>`, that size is reduced to about 30 MB.</span></span>

<span data-ttu-id="eb2bd-178">Yansıma veya ilgili dinamik özellikleri kullanan uygulamaların veya çerçevelerin (ASP.NET Core ve WPF dahil) genellikle kırpıldığına göre kesilmesini göz önünde bulundurmanız önemlidir.</span><span class="sxs-lookup"><span data-stu-id="eb2bd-178">It's important to consider that applications or frameworks (including ASP.NET Core and WPF) that use reflection or related dynamic features, will often break when trimmed.</span></span> <span data-ttu-id="eb2bd-179">Bu ayırıcı, bağlayıcının bu dinamik davranış hakkında bilgi sahibi olmadığı ve yansıma için hangi çerçeve türlerinin gerekli olduğunu belirleyemediği için oluşur.</span><span class="sxs-lookup"><span data-stu-id="eb2bd-179">This breakage occurs because the linker doesn't know about this dynamic behavior and can't determine which framework types are required for reflection.</span></span> <span data-ttu-id="eb2bd-180">Il bağlayıcı aracı, bu senaryonun farkında olacak şekilde yapılandırılabilir.</span><span class="sxs-lookup"><span data-stu-id="eb2bd-180">The IL Linker tool can be configured to be aware of this scenario.</span></span>

<span data-ttu-id="eb2bd-181">Tüm diğerleri üzerinde, kırpdıktan sonra uygulamanızı test ettiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="eb2bd-181">Above all else, be sure to test your app after trimming.</span></span>

<span data-ttu-id="eb2bd-182">Il bağlayıcı aracı hakkında daha fazla bilgi için [belgelere](https://aka.ms/dotnet-illink) bakın veya [mono/bağlayıcı]( https://github.com/mono/linker) deposunu ziyaret edin.</span><span class="sxs-lookup"><span data-stu-id="eb2bd-182">For more information about the IL Linker tool, see the [documentation](https://aka.ms/dotnet-illink) or visit the [mono/linker]( https://github.com/mono/linker) repo.</span></span>

## <a name="tiered-compilation"></a><span data-ttu-id="eb2bd-183">Katmanlı derleme</span><span class="sxs-lookup"><span data-stu-id="eb2bd-183">Tiered compilation</span></span>

<span data-ttu-id="eb2bd-184">[Katmanlı derleme](https://devblogs.microsoft.com/dotnet/tiered-compilation-preview-in-net-core-2-1/) (TC), .NET Core 3,0 ile varsayılan olarak açık olur.</span><span class="sxs-lookup"><span data-stu-id="eb2bd-184">[Tiered compilation](https://devblogs.microsoft.com/dotnet/tiered-compilation-preview-in-net-core-2-1/) (TC) is on by default with .NET Core 3.0.</span></span> <span data-ttu-id="eb2bd-185">Bu özellik, çalışma zamanının daha iyi performans almak için tam zamanında (JıT) derleyicisini daha kolay bir şekilde kullanmasına olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="eb2bd-185">This feature enables the runtime to more adaptively use the Just-In-Time (JIT) compiler to get better performance.</span></span>

<span data-ttu-id="eb2bd-186">TC 'nin başlıca avantajı, daha düşük kaliteli, ancak daha hızlı bir katman veya daha yüksek kaliteli, ancak daha yavaş bir katman ile yöntemleri etkinleştirmektir (yeniden).</span><span class="sxs-lookup"><span data-stu-id="eb2bd-186">The main benefit of TC is to enable (re-)jitting methods with a lower-quality-but-faster tier or a higher-quality-but-slower tier.</span></span> <span data-ttu-id="eb2bd-187">Bu, bir uygulamanın, düzenli durum aracılığıyla başlangıçtan itibaren çeşitli yürütme aşamalarından geçerek performansını artırmaya yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="eb2bd-187">This helps increase performance of an application as it goes through various stages of execution, from startup through steady-state.</span></span> <span data-ttu-id="eb2bd-188">Bu, her yöntemin tek bir şekilde (yüksek kaliteli katmanla aynı) derlenmesi ve bu durum, başlangıç performansı üzerinden kararlı bir duruma yol gösteren TC olmayan yaklaşımla karşıtdır.</span><span class="sxs-lookup"><span data-stu-id="eb2bd-188">This contrasts with the non-TC approach, where every method is compiled a single way (the same as the high-quality tier), which is biased to steady-state over startup performance.</span></span>

<span data-ttu-id="eb2bd-189">Hızlı JıT 'i etkinleştirmek için (Katman 0 ile derlenen kod), proje dosyanızda bu ayarı kullanın:</span><span class="sxs-lookup"><span data-stu-id="eb2bd-189">To enable Quick JIT (tier 0 jitted code), use this setting in your project file:</span></span>

```xml
<PropertyGroup>
  <TieredCompilationQuickJit>true</TieredCompilationQuickJit>
</PropertyGroup>
```

<span data-ttu-id="eb2bd-190">TC 'yi tamamen devre dışı bırakmak için, proje dosyanızda bu ayarı kullanın:</span><span class="sxs-lookup"><span data-stu-id="eb2bd-190">To disable TC completely, use this setting in your project file:</span></span>

```xml
<TieredCompilation>false</TieredCompilation>
```

## <a name="readytorun-images"></a><span data-ttu-id="eb2bd-191">ReadyToRun görüntüleri</span><span class="sxs-lookup"><span data-stu-id="eb2bd-191">ReadyToRun images</span></span>

<span data-ttu-id="eb2bd-192">Uygulama derlemelerinizi ReadyToRun (R2R) biçiminde derleyerek .NET Core uygulamanızın başlama süresini geliştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="eb2bd-192">You can improve the startup time of your .NET Core application by compiling your application assemblies as ReadyToRun (R2R) format.</span></span> <span data-ttu-id="eb2bd-193">R2R, bir süre öncesi (AOT) derleme biçimidir.</span><span class="sxs-lookup"><span data-stu-id="eb2bd-193">R2R is a form of ahead-of-time (AOT) compilation.</span></span>

<span data-ttu-id="eb2bd-194">R2R ikilileri, tam zamanında (JıT) derleyicisinin uygulamanız yüklenirken yapması gereken iş miktarını azaltarak başlangıç performansını geliştirir.</span><span class="sxs-lookup"><span data-stu-id="eb2bd-194">R2R binaries improve startup performance by reducing the amount of work the just-in-time (JIT) compiler needs to do as your application loads.</span></span> <span data-ttu-id="eb2bd-195">İkililer, JıT 'in üretmesine kıyasla benzer yerel kod içerir.</span><span class="sxs-lookup"><span data-stu-id="eb2bd-195">The binaries contain similar native code compared to what the JIT would produce.</span></span> <span data-ttu-id="eb2bd-196">Ancak, R2R ikilileri, bazı senaryolar için hala gerekli olan hem ara dil (IL) kodunu hem de aynı kodun yerel sürümünü içerdiğinden, daha büyüktür.</span><span class="sxs-lookup"><span data-stu-id="eb2bd-196">However, R2R binaries are larger because they contain both intermediate language (IL) code, which is still needed for some scenarios, and the native version of the same code.</span></span> <span data-ttu-id="eb2bd-197">R2R yalnızca, Linux x64 veya Windows x64 gibi belirli çalışma zamanı ortamlarını (RID) hedefleyen bir kendi içinde bulunan uygulamayı yayımladığınızda kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="eb2bd-197">R2R is only available when you publish a self-contained app that targets specific runtime environments (RID) such as Linux x64 or Windows x64.</span></span>

<span data-ttu-id="eb2bd-198">Projenizi ReadyToRun olarak derlemek için aşağıdakileri yapın:</span><span class="sxs-lookup"><span data-stu-id="eb2bd-198">To compile your project as ReadyToRun, do the following:</span></span>

01. <span data-ttu-id="eb2bd-199">`<PublishReadyToRun>` Ayarı projenize ekleyin</span><span class="sxs-lookup"><span data-stu-id="eb2bd-199">Add the `<PublishReadyToRun>` setting to your project</span></span>

    ```xml
    <PropertyGroup>
      <PublishReadyToRun>true</PublishReadyToRun>
    </PropertyGroup>
    ```

01. <span data-ttu-id="eb2bd-200">Kendi içinde bir uygulama yayımlayın.</span><span class="sxs-lookup"><span data-stu-id="eb2bd-200">Publish a self-contained app.</span></span> <span data-ttu-id="eb2bd-201">Örneğin, bu komut Windows 'un 64 bit sürümü için kendi kendine içerilen bir uygulama oluşturur:</span><span class="sxs-lookup"><span data-stu-id="eb2bd-201">For example, this command creates a self-contained app for the 64-bit version of Windows:</span></span>

    ```console
    dotnet publish -c Release -r win-x64 --self-contained true
    ```

### <a name="cross-platformarchitecture-restrictions"></a><span data-ttu-id="eb2bd-202">Platformlar arası/mimari kısıtlamaları</span><span class="sxs-lookup"><span data-stu-id="eb2bd-202">Cross platform/architecture restrictions</span></span>

<span data-ttu-id="eb2bd-203">ReadyToRun derleyicisi Şu anda çapraz hedefleme 'yi desteklememektedir.</span><span class="sxs-lookup"><span data-stu-id="eb2bd-203">The ReadyToRun compiler doesn't currently support cross-targeting.</span></span> <span data-ttu-id="eb2bd-204">Belirli bir hedefte derleme yapmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="eb2bd-204">You must compile on a given target.</span></span> <span data-ttu-id="eb2bd-205">Örneğin, R2R görüntülerini Windows x64 için istiyorsanız, bu ortamda Yayımla komutunu çalıştırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="eb2bd-205">For example, if you want R2R images for Windows x64, you need to run the publish command on that environment.</span></span>

<span data-ttu-id="eb2bd-206">Çapraz hedefleme için özel durumlar:</span><span class="sxs-lookup"><span data-stu-id="eb2bd-206">Exceptions to cross-targeting:</span></span>

- <span data-ttu-id="eb2bd-207">Windows x64, Windows ARM32, ARM64 ve x86 görüntülerini derlemek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="eb2bd-207">Windows x64 can be used to compile Windows ARM32, ARM64, and x86 images.</span></span>
- <span data-ttu-id="eb2bd-208">Windows x86, Windows ARM32 görüntülerini derlemek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="eb2bd-208">Windows x86 can be used to compile Windows ARM32 images.</span></span>
- <span data-ttu-id="eb2bd-209">Linux x64, Linux ARM32 ve ARM64 görüntülerini derlemek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="eb2bd-209">Linux x64 can be used to compile Linux ARM32 and ARM64 images.</span></span>

## <a name="build-copies-dependencies"></a><span data-ttu-id="eb2bd-210">Derleme kopyaları bağımlılıkları</span><span class="sxs-lookup"><span data-stu-id="eb2bd-210">Build copies dependencies</span></span>

<span data-ttu-id="eb2bd-211">Komut `dotnet build` artık, NuGet önbelleğinden uygulamanızın NuGet bağımlılıklarını yapı çıkış klasörüne kopyalar.</span><span class="sxs-lookup"><span data-stu-id="eb2bd-211">The `dotnet build` command now copies NuGet dependencies for your application from the NuGet cache to the build output folder.</span></span> <span data-ttu-id="eb2bd-212">Daha önce bağımlılıklar yalnızca bir `dotnet publish`parçası olarak kopyalandı.</span><span class="sxs-lookup"><span data-stu-id="eb2bd-212">Previously, dependencies were only copied as part of `dotnet publish`.</span></span>

<span data-ttu-id="eb2bd-213">Bağlama ve Razor sayfası yayımlama gibi bazı işlemler, yayımlamayı gerektirecek şekilde devam eder.</span><span class="sxs-lookup"><span data-stu-id="eb2bd-213">There are some operations, like linking and razor page publishing that will still require publishing.</span></span>

## <a name="local-tools"></a><span data-ttu-id="eb2bd-214">Yerel Araçlar</span><span class="sxs-lookup"><span data-stu-id="eb2bd-214">Local tools</span></span>

<span data-ttu-id="eb2bd-215">.NET Core 3,0 yerel araçları tanıtır.</span><span class="sxs-lookup"><span data-stu-id="eb2bd-215">.NET Core 3.0 introduces local tools.</span></span> <span data-ttu-id="eb2bd-216">Yerel Araçlar [genel araçlara](../tools/global-tools.md) benzerdir, ancak diskte belirli bir konum ile ilişkilendirilir.</span><span class="sxs-lookup"><span data-stu-id="eb2bd-216">Local tools are similar to [global tools](../tools/global-tools.md) but are associated with a particular location on disk.</span></span> <span data-ttu-id="eb2bd-217">Yerel araçlar küresel olarak kullanılabilir değildir ve NuGet paketleri olarak dağıtılır.</span><span class="sxs-lookup"><span data-stu-id="eb2bd-217">Local tools aren't available globally and are distributed as NuGet packages.</span></span>

> [!WARNING]
> <span data-ttu-id="eb2bd-218">.NET Core 3,0 Preview 1 ' de veya `dotnet tool restore` `dotnet tool install`çalıştıran gibi yerel araçlara çalıştıysanız, yerel araçlar önbellek klasörünü silin.</span><span class="sxs-lookup"><span data-stu-id="eb2bd-218">If you tried local tools in .NET Core 3.0 Preview 1, such as running `dotnet tool restore` or `dotnet tool install`, delete the local tools cache folder.</span></span> <span data-ttu-id="eb2bd-219">Aksi takdirde, yerel araçlar yeni bir sürümde çalışmaz.</span><span class="sxs-lookup"><span data-stu-id="eb2bd-219">Otherwise, local tools won't work on any newer release.</span></span> <span data-ttu-id="eb2bd-220">Bu klasör şu konumda bulunur:</span><span class="sxs-lookup"><span data-stu-id="eb2bd-220">This folder is located at:</span></span>
>
> <span data-ttu-id="eb2bd-221">MacOS 'ta Linux:`rm -r $HOME/.dotnet/toolResolverCache`</span><span class="sxs-lookup"><span data-stu-id="eb2bd-221">On macOS, Linux: `rm -r $HOME/.dotnet/toolResolverCache`</span></span>
>
> <span data-ttu-id="eb2bd-222">Windows 'da:`rmdir /s %USERPROFILE%\.dotnet\toolResolverCache`</span><span class="sxs-lookup"><span data-stu-id="eb2bd-222">On Windows: `rmdir /s %USERPROFILE%\.dotnet\toolResolverCache`</span></span>

<span data-ttu-id="eb2bd-223">Yerel araçlar, geçerli dizininizde bir bildirim dosyası `dotnet-tools.json` adına bağımlıdır.</span><span class="sxs-lookup"><span data-stu-id="eb2bd-223">Local tools rely on a manifest file name `dotnet-tools.json` in your current directory.</span></span> <span data-ttu-id="eb2bd-224">Bu bildirim dosyası, bu klasörde ve altında kullanılabilecek araçları tanımlar.</span><span class="sxs-lookup"><span data-stu-id="eb2bd-224">This manifest file defines the tools to be available at that folder and below.</span></span> <span data-ttu-id="eb2bd-225">Kodunuzla çalışan herkesin aynı araçları geri yükleyip kullanabilmesini sağlamak için, bildirim dosyasını kodunuzla dağıtabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="eb2bd-225">You can distribute the manifest file with your code to ensure that anyone who works with your code can restore and use the same tools.</span></span>

<span data-ttu-id="eb2bd-226">Hem genel hem de yerel araçlar için, çalışma zamanının uyumlu bir sürümü gereklidir.</span><span class="sxs-lookup"><span data-stu-id="eb2bd-226">For both global and local tools, a compatible version of the runtime is required.</span></span> <span data-ttu-id="eb2bd-227">Şu anda NuGet.org hedef .NET Core çalışma zamanı 2,1 ' de birçok araç.</span><span class="sxs-lookup"><span data-stu-id="eb2bd-227">Many tools currently on NuGet.org target .NET Core Runtime 2.1.</span></span> <span data-ttu-id="eb2bd-228">Bu araçları küresel olarak veya yerel olarak yüklemek için, hala [NET Core 2,1 çalışma zamanını](https://dotnet.microsoft.com/download/dotnet-core/2.1)yüklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="eb2bd-228">To install these tools globally or locally, you would still need to install the [NET Core 2.1 Runtime](https://dotnet.microsoft.com/download/dotnet-core/2.1).</span></span>

## <a name="major-version-roll-forward"></a><span data-ttu-id="eb2bd-229">Büyük sürüm Ileri</span><span class="sxs-lookup"><span data-stu-id="eb2bd-229">Major-version Roll Forward</span></span>

<span data-ttu-id="eb2bd-230">.NET Core 3,0, uygulamanızın .NET Core 'un en son ana sürümüne iletmesini sağlayan bir katılım özelliği sunar.</span><span class="sxs-lookup"><span data-stu-id="eb2bd-230">.NET Core 3.0 introduces an opt-in feature that allows your app to roll forward to the latest major version of .NET Core.</span></span> <span data-ttu-id="eb2bd-231">Ayrıca, geri alma 'nın uygulamanıza nasıl uygulandığını denetlemek için yeni bir ayar eklenmiştir.</span><span class="sxs-lookup"><span data-stu-id="eb2bd-231">Additionally, a new setting has been added to control how roll forward is applied to your app.</span></span> <span data-ttu-id="eb2bd-232">Bu, aşağıdaki yollarla yapılandırılabilir:</span><span class="sxs-lookup"><span data-stu-id="eb2bd-232">This can be configured in the following ways:</span></span>

- <span data-ttu-id="eb2bd-233">Proje dosyası özelliği:`RollForward`</span><span class="sxs-lookup"><span data-stu-id="eb2bd-233">Project file property: `RollForward`</span></span>
- <span data-ttu-id="eb2bd-234">Çalışma zamanı yapılandırma dosyası özelliği:`rollForward`</span><span class="sxs-lookup"><span data-stu-id="eb2bd-234">Runtime configuration file property: `rollForward`</span></span>
- <span data-ttu-id="eb2bd-235">Ortam değişkeni:`DOTNET_ROLL_FORWARD`</span><span class="sxs-lookup"><span data-stu-id="eb2bd-235">Environment variable: `DOTNET_ROLL_FORWARD`</span></span>
- <span data-ttu-id="eb2bd-236">Komut satırı bağımsız değişkeni:`--roll-forward`</span><span class="sxs-lookup"><span data-stu-id="eb2bd-236">Command-line argument: `--roll-forward`</span></span>

<span data-ttu-id="eb2bd-237">Aşağıdaki değerlerden biri belirtilmelidir.</span><span class="sxs-lookup"><span data-stu-id="eb2bd-237">One of the following values must be specified.</span></span> <span data-ttu-id="eb2bd-238">Ayar atlanırsa, **İkincil** varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="eb2bd-238">If the setting is omitted, **Minor** is the default.</span></span>

- <span data-ttu-id="eb2bd-239">**LatestPatch**</span><span class="sxs-lookup"><span data-stu-id="eb2bd-239">**LatestPatch**</span></span>\
<span data-ttu-id="eb2bd-240">En yüksek düzeltme eki sürümüne ilet.</span><span class="sxs-lookup"><span data-stu-id="eb2bd-240">Roll forward to the highest patch version.</span></span> <span data-ttu-id="eb2bd-241">Bu, ikincil sürüm iletmeyi devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="eb2bd-241">This disables minor version roll forward.</span></span>
- <span data-ttu-id="eb2bd-242">**Bazı**</span><span class="sxs-lookup"><span data-stu-id="eb2bd-242">**Minor**</span></span>\
<span data-ttu-id="eb2bd-243">İstenen alt sürüm eksikse, en düşük düzeydeki sürüme ilet.</span><span class="sxs-lookup"><span data-stu-id="eb2bd-243">Roll forward to the lowest higher minor version, if requested minor version is missing.</span></span> <span data-ttu-id="eb2bd-244">İstenen ikincil sürüm varsa, **Latestpatch** ilkesi kullanılır.</span><span class="sxs-lookup"><span data-stu-id="eb2bd-244">If the requested minor version is present, then the **LatestPatch** policy is used.</span></span>
- <span data-ttu-id="eb2bd-245">**Leri**</span><span class="sxs-lookup"><span data-stu-id="eb2bd-245">**Major**</span></span>\
<span data-ttu-id="eb2bd-246">İstenen ana sürüm eksikse, en düşük büyük sürüme ve en düşük alt sürüme ileri doğru alın.</span><span class="sxs-lookup"><span data-stu-id="eb2bd-246">Roll forward to lowest higher major version, and lowest minor version, if requested major version is missing.</span></span> <span data-ttu-id="eb2bd-247">İstenen ana sürüm varsa, **İkincil** ilke kullanılır.</span><span class="sxs-lookup"><span data-stu-id="eb2bd-247">If the requested major version is present, then the **Minor** policy is used.</span></span>
- <span data-ttu-id="eb2bd-248">**LatestMinor**</span><span class="sxs-lookup"><span data-stu-id="eb2bd-248">**LatestMinor**</span></span>\
<span data-ttu-id="eb2bd-249">İstenen alt sürüm mevcut olsa bile en yüksek düzeyde alt sürüme ilet.</span><span class="sxs-lookup"><span data-stu-id="eb2bd-249">Roll forward to highest minor version, even if requested minor version is present.</span></span> <span data-ttu-id="eb2bd-250">Bileşen barındırma senaryolarına yöneliktir.</span><span class="sxs-lookup"><span data-stu-id="eb2bd-250">Intended for component hosting scenarios.</span></span>
- <span data-ttu-id="eb2bd-251">**Latestana**</span><span class="sxs-lookup"><span data-stu-id="eb2bd-251">**LatestMajor**</span></span>\
<span data-ttu-id="eb2bd-252">İstenen ana mevcut olsa bile, en yüksek büyük ve en yüksek düzeyde alt sürüme ilet.</span><span class="sxs-lookup"><span data-stu-id="eb2bd-252">Roll forward to highest major and highest minor version, even if requested major is present.</span></span> <span data-ttu-id="eb2bd-253">Bileşen barındırma senaryolarına yöneliktir.</span><span class="sxs-lookup"><span data-stu-id="eb2bd-253">Intended for component hosting scenarios.</span></span>
- <span data-ttu-id="eb2bd-254">**Dıı**</span><span class="sxs-lookup"><span data-stu-id="eb2bd-254">**Disable**</span></span>\
<span data-ttu-id="eb2bd-255">İleri alma.</span><span class="sxs-lookup"><span data-stu-id="eb2bd-255">Don't roll forward.</span></span> <span data-ttu-id="eb2bd-256">Yalnızca belirtilen sürüme bağlayın.</span><span class="sxs-lookup"><span data-stu-id="eb2bd-256">Only bind to specified version.</span></span> <span data-ttu-id="eb2bd-257">Bu ilke, en son düzeltme eklerine iletme özelliğini devre dışı bıraktığından genel kullanım için önerilmez.</span><span class="sxs-lookup"><span data-stu-id="eb2bd-257">This policy isn't recommended for general use because it disables the ability to roll forward to the latest patches.</span></span> <span data-ttu-id="eb2bd-258">Bu değer yalnızca test için önerilir.</span><span class="sxs-lookup"><span data-stu-id="eb2bd-258">This value is only recommended for testing.</span></span>

<span data-ttu-id="eb2bd-259">**Devre dışı bırak** ayarının yanı sıra, tüm ayarlar kullanılabilir en yüksek düzeltme eki sürümünü kullanacaktır.</span><span class="sxs-lookup"><span data-stu-id="eb2bd-259">Besides the **Disable** setting, all settings will use the highest available patch version.</span></span>

## <a name="windows-desktop"></a><span data-ttu-id="eb2bd-260">Windows masaüstü</span><span class="sxs-lookup"><span data-stu-id="eb2bd-260">Windows desktop</span></span>

<span data-ttu-id="eb2bd-261">.NET Core 3,0, Windows Presentation Foundation (WPF) ve Windows Forms kullanarak Windows masaüstü uygulamalarını destekler.</span><span class="sxs-lookup"><span data-stu-id="eb2bd-261">.NET Core 3.0 supports Windows desktop applications using Windows Presentation Foundation (WPF) and Windows Forms.</span></span> <span data-ttu-id="eb2bd-262">Bu çerçeveler ayrıca, Windows UI XAML kitaplığı 'ndan (WinUI) [xaml Adaları](/windows/uwp/xaml-platform/xaml-host-controls)aracılığıyla modern denetimleri ve akıcı stil oluşturmayı da destekler.</span><span class="sxs-lookup"><span data-stu-id="eb2bd-262">These frameworks also support using modern controls and Fluent styling from the Windows UI XAML Library (WinUI) via [XAML islands](/windows/uwp/xaml-platform/xaml-host-controls).</span></span>

<span data-ttu-id="eb2bd-263">Windows Masaüstü bileşeni, Windows .NET Core 3,0 SDK 'sının bir parçasıdır.</span><span class="sxs-lookup"><span data-stu-id="eb2bd-263">The Windows Desktop component is part of the Windows .NET Core 3.0 SDK.</span></span>

<span data-ttu-id="eb2bd-264">Aşağıdaki `dotnet` komutlarla yeni bir WPF veya Windows Forms uygulaması oluşturabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="eb2bd-264">You can create a new WPF or Windows Forms app with the following `dotnet` commands:</span></span>

```console
dotnet new wpf
dotnet new winforms
```

<span data-ttu-id="eb2bd-265">Visual Studio 2019, .NET Core 3,0 Windows Forms ve WPF için **Yeni proje** şablonları ekler.</span><span class="sxs-lookup"><span data-stu-id="eb2bd-265">Visual Studio 2019 adds **New Project** templates for .NET Core 3.0 Windows Forms and WPF.</span></span>

<span data-ttu-id="eb2bd-266">Mevcut bir .NET Framework uygulamasının bağlantı noktası hakkında daha fazla bilgi için bkz. [bağlantı noktası WPF projeleri](../porting/wpf.md) ve [bağlantı noktası Windows Forms projeleri](../porting/winforms.md).</span><span class="sxs-lookup"><span data-stu-id="eb2bd-266">For more information about how to port an existing .NET Framework application, see [Port WPF projects](../porting/wpf.md) and [Port Windows Forms projects](../porting/winforms.md).</span></span>

## <a name="com-callable-components---windows-desktop"></a><span data-ttu-id="eb2bd-267">COM çağrılabilir bileşenler-Windows Masaüstü</span><span class="sxs-lookup"><span data-stu-id="eb2bd-267">COM-callable components - Windows Desktop</span></span>

<span data-ttu-id="eb2bd-268">Windows 'ta artık COM çağrılabilir yönetilen bileşenler oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="eb2bd-268">On Windows, you can now create COM-callable managed components.</span></span> <span data-ttu-id="eb2bd-269">Bu özellik, .NET Core 'un COM eklenti modelleriyle kullanılması ve ayrıca .NET Framework eşlik sağlanması açısından önemlidir.</span><span class="sxs-lookup"><span data-stu-id="eb2bd-269">This capability is critical to use .NET Core with COM add-in models and also to provide parity with .NET Framework.</span></span>

<span data-ttu-id="eb2bd-270">*Mscoree. dll* ' nin com sunucusu olarak kullanıldığı .NET Framework aksine, .NET Core, com bileşenini oluştururken *bin* dizinine yerel bir başlatıcı dll 'si ekler.</span><span class="sxs-lookup"><span data-stu-id="eb2bd-270">Unlike .NET Framework where the *mscoree.dll* was used as the COM server, .NET Core will add a native launcher dll to the *bin* directory when you build your COM component.</span></span>

<span data-ttu-id="eb2bd-271">COM bileşeni oluşturma ve kullanma hakkında bir örnek için bkz. [com tanıtımı](https://github.com/dotnet/samples/tree/master/core/extensions/COMServerDemo).</span><span class="sxs-lookup"><span data-stu-id="eb2bd-271">For an example of how to create a COM component and consume it, see the [COM Demo](https://github.com/dotnet/samples/tree/master/core/extensions/COMServerDemo).</span></span>

## <a name="msix-deployment---windows-desktop"></a><span data-ttu-id="eb2bd-272">MSIX dağıtımı-Windows Masaüstü</span><span class="sxs-lookup"><span data-stu-id="eb2bd-272">MSIX Deployment - Windows Desktop</span></span>

<span data-ttu-id="eb2bd-273">[Msix](https://docs.microsoft.com/windows/msix/) yeni bir Windows uygulama paketi biçimidir.</span><span class="sxs-lookup"><span data-stu-id="eb2bd-273">[MSIX](https://docs.microsoft.com/windows/msix/) is a new Windows application package format.</span></span> <span data-ttu-id="eb2bd-274">.NET Core 3,0 masaüstü uygulamalarını Windows 10 ' a dağıtmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="eb2bd-274">It can be used to deploy .NET Core 3.0 desktop applications to Windows 10.</span></span>

<span data-ttu-id="eb2bd-275">Visual Studio 2019 ' de bulunan [Windows uygulama paketleme projesi](https://docs.microsoft.com/windows/uwp/porting/desktop-to-uwp-packaging-dot-net), [kendi kendine içerilen](../deploying/index.md#self-contained-deployments-scd) .NET Core uygulamalarıyla msix paketi oluşturmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="eb2bd-275">The [Windows Application Packaging Project](https://docs.microsoft.com/windows/uwp/porting/desktop-to-uwp-packaging-dot-net), available in Visual Studio 2019, allows you to create MSIX packages with [self-contained](../deploying/index.md#self-contained-deployments-scd) .NET Core applications.</span></span>

<span data-ttu-id="eb2bd-276">.NET Core proje dosyası, `<RuntimeIdentifiers>` özelliğindeki desteklenen çalışma zamanlarını belirtmelidir:</span><span class="sxs-lookup"><span data-stu-id="eb2bd-276">The .NET Core project file must specify the supported runtimes in the `<RuntimeIdentifiers>` property:</span></span>

```xml
<RuntimeIdentifiers>win-x86;win-x64</RuntimeIdentifiers>
```

## <a name="winforms-high-dpi"></a><span data-ttu-id="eb2bd-277">WinForms yüksek DPı</span><span class="sxs-lookup"><span data-stu-id="eb2bd-277">WinForms high DPI</span></span>

<span data-ttu-id="eb2bd-278">.NET Core Windows Forms uygulamaları, ile <xref:System.Windows.Forms.Application.SetHighDpiMode(System.Windows.Forms.HighDpiMode)?displayProperty=nameWithType>yüksek DPI modunu ayarlayabilir.</span><span class="sxs-lookup"><span data-stu-id="eb2bd-278">.NET Core Windows Forms applications can set high DPI mode with <xref:System.Windows.Forms.Application.SetHighDpiMode(System.Windows.Forms.HighDpiMode)?displayProperty=nameWithType>.</span></span> <span data-ttu-id="eb2bd-279">Bu `SetHighDpiMode` Yöntem, daha önce `Application.Run`veya P/Invoke gibi `App.Manifest` diğer yollarla ayarlanmadığı takdirde, karşılık gelen yüksek DPI modunu ayarlar.</span><span class="sxs-lookup"><span data-stu-id="eb2bd-279">The `SetHighDpiMode` method sets the corresponding high DPI mode unless the setting has been set by other means like `App.Manifest` or P/Invoke before `Application.Run`.</span></span>

<span data-ttu-id="eb2bd-280">Sabit<xref:System.Windows.Forms.HighDpiMode?displayProperty=nameWithType> listesi `highDpiMode` tarafından ifade edilen olası değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="eb2bd-280">The possible `highDpiMode` values, as expressed by the <xref:System.Windows.Forms.HighDpiMode?displayProperty=nameWithType> enum are:</span></span>

- `DpiUnaware`
- `SystemAware`
- `PerMonitor`
- `PerMonitorV2`
- `DpiUnawareGdiScaled`

<span data-ttu-id="eb2bd-281">Yüksek DPı modları hakkında daha fazla bilgi için bkz. [Windows 'Da yüksek DPI Masaüstü uygulama geliştirme](/windows/desktop/hidpi/high-dpi-desktop-application-development-on-windows).</span><span class="sxs-lookup"><span data-stu-id="eb2bd-281">For more information about high DPI modes, see [High DPI Desktop Application Development on Windows](/windows/desktop/hidpi/high-dpi-desktop-application-development-on-windows).</span></span>

## <a name="ranges-and-indices"></a><span data-ttu-id="eb2bd-282">Aralıklar ve dizinler</span><span class="sxs-lookup"><span data-stu-id="eb2bd-282">Ranges and indices</span></span>

<span data-ttu-id="eb2bd-283">Yeni <xref:System.Index?displayProperty=nameWithType> tür dizin oluşturmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="eb2bd-283">The new <xref:System.Index?displayProperty=nameWithType> type can be used for indexing.</span></span> <span data-ttu-id="eb2bd-284">Başlangıçtan itibaren bir veya sonuna kadar `int` olan önek `^` işleci (C#) ile bir tane oluşturabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="eb2bd-284">You can create one from an `int` that counts from the beginning, or with a prefix `^` operator (C#) that counts from the end:</span></span>

```csharp
Index i1 = 3;  // number 3 from beginning
Index i2 = ^4; // number 4 from end
int[] a = { 0, 1, 2, 3, 4, 5, 6, 7, 8, 9 };
Console.WriteLine($"{a[i1]}, {a[i2]}"); // "3, 6"
```

<span data-ttu-id="eb2bd-285">Ayrıca <xref:System.Range?displayProperty=nameWithType> , biri başlangıç ve diğeri bitiş için olmak üzere `Index` iki değerden oluşan tür ve bir `x..y` Aralık ifadesiyle (C#) yazılabilir.</span><span class="sxs-lookup"><span data-stu-id="eb2bd-285">There's also the <xref:System.Range?displayProperty=nameWithType> type, which consists of two `Index` values, one for the start and one for the end, and can be written with a `x..y` range expression (C#).</span></span> <span data-ttu-id="eb2bd-286">Daha sonra bir dilim üreten bir `Range`ile dizin oluşturabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="eb2bd-286">You can then index with a `Range`, which produces a slice:</span></span>

```csharp
var slice = a[i1..i2]; // { 3, 4, 5 }
```

<span data-ttu-id="eb2bd-287">Daha fazla bilgi için [aralıklar ve dizinler öğreticisine](../../csharp/tutorials/ranges-indexes.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="eb2bd-287">For more information, see the [ranges and indices tutorial](../../csharp/tutorials/ranges-indexes.md).</span></span>

## <a name="async-streams"></a><span data-ttu-id="eb2bd-288">Zaman uyumsuz akışlar</span><span class="sxs-lookup"><span data-stu-id="eb2bd-288">Async streams</span></span>

<span data-ttu-id="eb2bd-289">Türü yeni bir zaman uyumsuz <xref:System.Collections.Generic.IEnumerable%601>sürümüdür. <xref:System.Collections.Generic.IAsyncEnumerable%601></span><span class="sxs-lookup"><span data-stu-id="eb2bd-289">The <xref:System.Collections.Generic.IAsyncEnumerable%601> type is a new asynchronous version of <xref:System.Collections.Generic.IEnumerable%601>.</span></span> <span data-ttu-id="eb2bd-290">`yield return` Dil `await foreach` ,öğelerinitüketmekveöğelerioluşturmakiçinbunlarıkullanmakiçinkullanabilirsiniz.`IAsyncEnumerable<T>`</span><span class="sxs-lookup"><span data-stu-id="eb2bd-290">The language lets you `await foreach` over `IAsyncEnumerable<T>` to consume their elements, and use `yield return` to them to produce elements.</span></span>

<span data-ttu-id="eb2bd-291">Aşağıdaki örnek, zaman uyumsuz akışların hem üretimini hem de tüketimini gösterir.</span><span class="sxs-lookup"><span data-stu-id="eb2bd-291">The following example demonstrates both production and consumption of async streams.</span></span> <span data-ttu-id="eb2bd-292">Bildirim zaman uyumsuz ve kendisi çağıranlar için zaman uyumsuz akış üretmek için kullanır `yield return`. `foreach`</span><span class="sxs-lookup"><span data-stu-id="eb2bd-292">The `foreach` statement is async and itself uses `yield return` to produce an async stream for callers.</span></span> <span data-ttu-id="eb2bd-293">Bu model (kullanılarak `yield return`), zaman uyumsuz akışlar üretmek için önerilen modeldir.</span><span class="sxs-lookup"><span data-stu-id="eb2bd-293">This pattern (using `yield return`) is the recommended model for producing async streams.</span></span>

```csharp
async IAsyncEnumerable<int> GetBigResultsAsync()
{
    await foreach (var result in GetResultsAsync())
    {
        if (result > 20) yield return result;
    }
}
```

<span data-ttu-id="eb2bd-294">Ayrıca, zaman uyumsuz yineleyiciler da oluşturabilirsiniz, örneğin, hem `await` hem `yield` de içinde kullanabileceğiniz bir `IAsyncEnumerable/IAsyncEnumerator` Yineleyici. `await foreach`</span><span class="sxs-lookup"><span data-stu-id="eb2bd-294">In addition to being able to `await foreach`, you can also create async iterators, for example, an iterator that returns an `IAsyncEnumerable/IAsyncEnumerator` that you can both `await` and `yield` in.</span></span> <span data-ttu-id="eb2bd-295">Atılmalıdır, `IAsyncDisposable` `Stream` ve `Timer`gibi çeşitli BCL türlerini uygulayan ' i kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="eb2bd-295">For objects that need to be disposed, you can use `IAsyncDisposable`, which various BCL types implement, such as `Stream` and `Timer`.</span></span>

<span data-ttu-id="eb2bd-296">Daha fazla bilgi için bkz. [zaman uyumsuz akışlar öğreticisi](../../csharp/tutorials/generate-consume-asynchronous-stream.md).</span><span class="sxs-lookup"><span data-stu-id="eb2bd-296">For more information, see the [async streams tutorial](../../csharp/tutorials/generate-consume-asynchronous-stream.md).</span></span>

## <a name="ieee-floating-point-improvements"></a><span data-ttu-id="eb2bd-297">IEEE kayan nokta iyileştirmeleri</span><span class="sxs-lookup"><span data-stu-id="eb2bd-297">IEEE Floating-point improvements</span></span>

<span data-ttu-id="eb2bd-298">Kayan nokta API 'Leri, [ıeee 754-2008 düzeltmesine](https://en.wikipedia.org/wiki/IEEE_754-2008_revision)uymak üzere güncelleştiriliyor.</span><span class="sxs-lookup"><span data-stu-id="eb2bd-298">Floating point APIs are being updated to comply with [IEEE 754-2008 revision](https://en.wikipedia.org/wiki/IEEE_754-2008_revision).</span></span> <span data-ttu-id="eb2bd-299">Bu değişikliklerin amacı, tüm **gerekli** işlemleri kullanıma sunmaktır ve DAVRANıŞSAL 'in IEEE spec ile uyumlu olduklarından emin olmaktır. Kayan nokta iyileştirmeleri hakkında daha fazla bilgi için bkz. [.NET Core 3,0 blog gönderisine kayan nokta ayrıştırma ve biçimlendirme geliştirmeleri](https://devblogs.microsoft.com/dotnet/floating-point-parsing-and-formatting-improvements-in-net-core-3-0/) .</span><span class="sxs-lookup"><span data-stu-id="eb2bd-299">The goal of these changes is to expose all **required** operations and ensure that they're behaviorally compliant with the IEEE spec. For more information about floating-point improvements, see the [Floating-Point Parsing and Formatting improvements in .NET Core 3.0](https://devblogs.microsoft.com/dotnet/floating-point-parsing-and-formatting-improvements-in-net-core-3-0/) blog post.</span></span>

<span data-ttu-id="eb2bd-300">Ayrıştırma ve biçimlendirme düzeltmeleri şunları içerir:</span><span class="sxs-lookup"><span data-stu-id="eb2bd-300">Parsing and formatting fixes include:</span></span>

- <span data-ttu-id="eb2bd-301">Her uzunlukta doğru şekilde ayrıştırma ve yuvarlama girişleri.</span><span class="sxs-lookup"><span data-stu-id="eb2bd-301">Correctly parse and round inputs of any length.</span></span>
- <span data-ttu-id="eb2bd-302">Doğru şekilde ayrıştırır ve negatif sıfır biçimlendirir.</span><span class="sxs-lookup"><span data-stu-id="eb2bd-302">Correctly parse and format negative zero.</span></span>
- <span data-ttu-id="eb2bd-303">Büyük/ `Infinity` küçük `NaN` harfe duyarsız bir denetim yaparak ve uygunsa isteğe bağlı olarak daha önce `+` izin vererek doğru şekilde ayrıştırılabilir.</span><span class="sxs-lookup"><span data-stu-id="eb2bd-303">Correctly parse `Infinity` and `NaN` by doing a case-insensitive check and allowing an optional preceding `+` where applicable.</span></span>

<span data-ttu-id="eb2bd-304">Yeni <xref:System.Math?displayProperty=nameWithType> API 'ler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="eb2bd-304">New <xref:System.Math?displayProperty=nameWithType> APIs include:</span></span>

- <span data-ttu-id="eb2bd-305"><xref:System.Math.BitIncrement(System.Double)>'<xref:System.Math.BitDecrement(System.Double)></span><span class="sxs-lookup"><span data-stu-id="eb2bd-305"><xref:System.Math.BitIncrement(System.Double)> and <xref:System.Math.BitDecrement(System.Double)></span></span>\
<span data-ttu-id="eb2bd-306">`nextUp` Ve`nextDown` IEEE işlemlerine karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="eb2bd-306">Corresponds to the `nextUp` and `nextDown` IEEE operations.</span></span> <span data-ttu-id="eb2bd-307">Bunlar, girdiden daha büyük veya daha az (sırasıyla) karşılaştıran en küçük kayan nokta numarasını döndürür.</span><span class="sxs-lookup"><span data-stu-id="eb2bd-307">They return the smallest floating-point number that compares greater or lesser than the input (respectively).</span></span> <span data-ttu-id="eb2bd-308">Örneğin, `Math.BitIncrement(0.0)` döndürür `double.Epsilon`.</span><span class="sxs-lookup"><span data-stu-id="eb2bd-308">For example, `Math.BitIncrement(0.0)` would return `double.Epsilon`.</span></span>

- <span data-ttu-id="eb2bd-309"><xref:System.Math.MaxMagnitude(System.Double,System.Double)>'<xref:System.Math.MinMagnitude(System.Double,System.Double)></span><span class="sxs-lookup"><span data-stu-id="eb2bd-309"><xref:System.Math.MaxMagnitude(System.Double,System.Double)> and <xref:System.Math.MinMagnitude(System.Double,System.Double)></span></span>\
<span data-ttu-id="eb2bd-310">`maxNumMag` Ve`minNumMag` IEEE işlemlerine karşılık gelen değeri, iki girişin büyüklüğüne daha büyük veya daha az (sırasıyla) döndürür.</span><span class="sxs-lookup"><span data-stu-id="eb2bd-310">Corresponds to the `maxNumMag` and `minNumMag` IEEE operations, they return the value that is greater or lesser in magnitude of the two inputs (respectively).</span></span> <span data-ttu-id="eb2bd-311">Örneğin, `Math.MaxMagnitude(2.0, -3.0)` döndürür `-3.0`.</span><span class="sxs-lookup"><span data-stu-id="eb2bd-311">For example, `Math.MaxMagnitude(2.0, -3.0)` would return `-3.0`.</span></span>

- <xref:System.Math.ILogB(System.Double)>\
<span data-ttu-id="eb2bd-312">Bir integral değeri döndüren IEEEişleminekarşılıkgelir,girişparametresinintamsayıtaban2günlüğünüdöndürür.`logB`</span><span class="sxs-lookup"><span data-stu-id="eb2bd-312">Corresponds to the `logB` IEEE operation that returns an integral value, it returns the integral base-2 log of the input parameter.</span></span> <span data-ttu-id="eb2bd-313">Bu yöntem `floor(log2(x))`, ile aynı şekilde, ancak en az yuvarlama hatasıyla yapılır.</span><span class="sxs-lookup"><span data-stu-id="eb2bd-313">This method is effectively the same as `floor(log2(x))`, but done with minimal rounding error.</span></span>

- <xref:System.Math.ScaleB(System.Double,System.Int32)>\
<span data-ttu-id="eb2bd-314">Bir tamsayı değeri alan `x * pow(2, n)` IEEEişleminekarşılıkgelir,etkinolarakdöner,ancakenazyuvarlamahatasıylayapılır.`scaleB`</span><span class="sxs-lookup"><span data-stu-id="eb2bd-314">Corresponds to the `scaleB` IEEE operation that takes an integral value, it returns effectively `x * pow(2, n)`, but is done with minimal rounding error.</span></span>

- <xref:System.Math.Log2(System.Double)>\
<span data-ttu-id="eb2bd-315">`log2` IEEE işlemine karşılık gelen 2 tabanında logaritmasını döndürür.</span><span class="sxs-lookup"><span data-stu-id="eb2bd-315">Corresponds to the `log2` IEEE operation, it returns the base-2 logarithm.</span></span> <span data-ttu-id="eb2bd-316">Yuvarlama hatasını en aza indirir.</span><span class="sxs-lookup"><span data-stu-id="eb2bd-316">It minimizes rounding error.</span></span>

- <xref:System.Math.FusedMultiplyAdd(System.Double,System.Double,System.Double)>\
<span data-ttu-id="eb2bd-317">`fma` IEEE işlemine karşılık gelen bir fkullandınız çarpma eklemesi gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="eb2bd-317">Corresponds to the `fma` IEEE operation, it performs a fused multiply add.</span></span> <span data-ttu-id="eb2bd-318">Yani, tek bir işlem `(x * y) + z` olarak yapılır, böylece yuvarlama hatasını en aza indirir.</span><span class="sxs-lookup"><span data-stu-id="eb2bd-318">That is, it does `(x * y) + z` as a single operation, thereby minimizing the rounding error.</span></span> <span data-ttu-id="eb2bd-319">Örnek `FusedMultiplyAdd(1e308, 2.0, -1e308)` , döndürür `1e308`.</span><span class="sxs-lookup"><span data-stu-id="eb2bd-319">An example would be `FusedMultiplyAdd(1e308, 2.0, -1e308)` which returns `1e308`.</span></span> <span data-ttu-id="eb2bd-320">Normal `(1e308 * 2.0) - 1e308` dönüşler `double.PositiveInfinity`.</span><span class="sxs-lookup"><span data-stu-id="eb2bd-320">The regular `(1e308 * 2.0) - 1e308` returns `double.PositiveInfinity`.</span></span>

- <xref:System.Math.CopySign(System.Double,System.Double)>\
<span data-ttu-id="eb2bd-321">IEEE işlemine karşılık gelir, `x`, `y`ancak işaretini döndürür. `copySign`</span><span class="sxs-lookup"><span data-stu-id="eb2bd-321">Corresponds to the `copySign` IEEE operation, it returns the value of `x`, but with the sign of `y`.</span></span>

## <a name="fast-built-in-json-support"></a><span data-ttu-id="eb2bd-322">Hızlı yerleşik JSON desteği</span><span class="sxs-lookup"><span data-stu-id="eb2bd-322">Fast built-in JSON support</span></span>

<span data-ttu-id="eb2bd-323">.NET kullanıcıları, [**JSON.net**](https://www.newtonsoft.com/json) ve DIĞER popüler JSON kitaplıklarına büyük ölçüde güvenmeye devam eder ve bu da iyi seçeneklere sahip olur.</span><span class="sxs-lookup"><span data-stu-id="eb2bd-323">.NET users have largely relied on [**Json.NET**](https://www.newtonsoft.com/json) and other popular JSON libraries, which continue to be good choices.</span></span> <span data-ttu-id="eb2bd-324">**JSON.net** , temel veri türü olarak .net dizelerini kullanır, bu da arada bulunan UTF-16 ' dır.</span><span class="sxs-lookup"><span data-stu-id="eb2bd-324">**Json.NET** uses .NET strings as its base datatype, which is UTF-16 under the hood.</span></span>

<span data-ttu-id="eb2bd-325">Yeni yerleşik JSON desteği yüksek performanslı, düşük ayırma ve temel alınarak `Span<byte>`gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="eb2bd-325">The new built-in JSON support is high-performance, low allocation, and based on `Span<byte>`.</span></span> <span data-ttu-id="eb2bd-326">.NET Core 3,0 ad alanına yeni, <xref:System.Text.Json?displayProperty=nameWithType> JSON ile ilgili üç tür eklendi.</span><span class="sxs-lookup"><span data-stu-id="eb2bd-326">Three new main JSON-related types have been added to .NET Core 3.0 the <xref:System.Text.Json?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="eb2bd-327">Bu türler *henüz* düz eski CLR nesne (POCO) serileştirme ve serisini desteklemez.</span><span class="sxs-lookup"><span data-stu-id="eb2bd-327">These types don't *yet* support plain old CLR object (POCO) serialization and deserialization.</span></span>

### <a name="utf8jsonreader"></a><span data-ttu-id="eb2bd-328">Utf8JsonReader</span><span class="sxs-lookup"><span data-stu-id="eb2bd-328">Utf8JsonReader</span></span>

<span data-ttu-id="eb2bd-329"><xref:System.Text.Json.Utf8JsonReader?displayProperty=nameWithType>, ' dan okunan UTF-8 kodlu JSON metin için yüksek performanslı, düşük bir `ReadOnlySpan<byte>`ayırma, Salt ilet okuyucu olur.</span><span class="sxs-lookup"><span data-stu-id="eb2bd-329"><xref:System.Text.Json.Utf8JsonReader?displayProperty=nameWithType> is a high-performance, low allocation, forward-only reader for UTF-8 encoded JSON text, read from a `ReadOnlySpan<byte>`.</span></span> <span data-ttu-id="eb2bd-330">`Utf8JsonReader` , Özel Çözümleyicileri ve seri hale getiriciler oluşturmak için kullanılabilen, temel bir alt düzey türüdür.</span><span class="sxs-lookup"><span data-stu-id="eb2bd-330">The `Utf8JsonReader` is a foundational, low-level type, that can be used to build custom parsers and deserializers.</span></span> <span data-ttu-id="eb2bd-331">New `Utf8JsonReader` kullanarak JSON yükünün okunması, **JSON.net**'den okuyucu kullanmaktan daha hızlıdır.</span><span class="sxs-lookup"><span data-stu-id="eb2bd-331">Reading through a JSON payload using the new `Utf8JsonReader` is 2x faster than using the reader from **Json.NET**.</span></span> <span data-ttu-id="eb2bd-332">JSON belirteçlerini (UTF-16) dizeleri olarak oluşturmanız gerekene kadar ayırmaz.</span><span class="sxs-lookup"><span data-stu-id="eb2bd-332">It doesn't allocate until you need to actualize JSON tokens as (UTF-16) strings.</span></span>

<span data-ttu-id="eb2bd-333">Visual Studio Code tarafından oluşturulan [**Launch. JSON**](https://github.com/dotnet/samples/blob/master/snippets/core/whats-new/whats-new-in-30/cs/launch.json) dosyası aracılığıyla okuma örneği aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="eb2bd-333">Here is an example of reading through the [**launch.json**](https://github.com/dotnet/samples/blob/master/snippets/core/whats-new/whats-new-in-30/cs/launch.json) file created by Visual Studio Code:</span></span>

[!CODE-csharp[Utf8JsonReader](~/samples/snippets/core/whats-new/whats-new-in-30/cs/program.cs#PrintJson)]

[!CODE-csharp[Utf8JsonReader](~/samples/snippets/core/whats-new/whats-new-in-30/cs/program.cs#PrintJsonCall)]

### <a name="utf8jsonwriter"></a><span data-ttu-id="eb2bd-334">Utf8JsonWriter</span><span class="sxs-lookup"><span data-stu-id="eb2bd-334">Utf8JsonWriter</span></span>

<span data-ttu-id="eb2bd-335"><xref:System.Text.Json.Utf8JsonWriter?displayProperty=nameWithType>, `String` `Int32`ve gibiortak.nettürlerindenUTF-8kodluJSONmetniyazmakiçinyüksekperformanslı,önbelleğealınmamışvesaltileribiryolsağlar.`DateTime`</span><span class="sxs-lookup"><span data-stu-id="eb2bd-335"><xref:System.Text.Json.Utf8JsonWriter?displayProperty=nameWithType> provides a high-performance, non-cached, forward-only way to write UTF-8 encoded JSON text from common .NET types like `String`, `Int32`, and `DateTime`.</span></span> <span data-ttu-id="eb2bd-336">Okuyucu gibi, yazıcı ise özel serileştiriciler oluşturmak için kullanılabilen temel bir alt düzey tür olur.</span><span class="sxs-lookup"><span data-stu-id="eb2bd-336">Like the reader, the writer is a foundational, low-level type, that can be used to build custom serializers.</span></span> <span data-ttu-id="eb2bd-337">Yeni `Utf8JsonWriter` % 30-80 daha hızlı bir JSON yükü yazmak, **JSON.net** adresinden yazıcı kullanmaktan daha hızlıdır ve ayrılmaz.</span><span class="sxs-lookup"><span data-stu-id="eb2bd-337">Writing a JSON payload using the new `Utf8JsonWriter` is 30-80% faster than using the writer from **Json.NET** and doesn't allocate.</span></span>

### <a name="jsondocument"></a><span data-ttu-id="eb2bd-338">JsonDocument</span><span class="sxs-lookup"><span data-stu-id="eb2bd-338">JsonDocument</span></span>

<span data-ttu-id="eb2bd-339"><xref:System.Text.Json.JsonDocument?displayProperty=nameWithType>, `Utf8JsonReader`üzerine kurulmuştur.</span><span class="sxs-lookup"><span data-stu-id="eb2bd-339"><xref:System.Text.Json.JsonDocument?displayProperty=nameWithType> is built on top of the `Utf8JsonReader`.</span></span> <span data-ttu-id="eb2bd-340">, `JsonDocument` JSON verilerini ayrıştırabilme ve rasgele erişimi ve numaralandırmayı desteklemek için sorgulanabilen salt okunurdur belge nesne modeli (DOM) oluşturma olanağı sağlar.</span><span class="sxs-lookup"><span data-stu-id="eb2bd-340">The `JsonDocument` provides the ability to parse JSON data and build a read-only Document Object Model (DOM) that can be queried to support random access and enumeration.</span></span> <span data-ttu-id="eb2bd-341">Verileri oluşturan JSON öğelerine, adlı <xref:System.Text.Json.JsonElement> `RootElement`bir özellik `JsonDocument` olarak kullanıma sunulan tür aracılığıyla erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="eb2bd-341">The JSON elements that compose the data can be accessed via the <xref:System.Text.Json.JsonElement> type that is exposed by the `JsonDocument` as a property called `RootElement`.</span></span> <span data-ttu-id="eb2bd-342">JSON metnini ortak .net türlerine dönüştürmek için API 'lerle birlikte JSON dizisini ve nesne numaralandırıcıları içerir.`JsonElement`</span><span class="sxs-lookup"><span data-stu-id="eb2bd-342">The `JsonElement` contains the JSON array and object enumerators along with APIs to convert JSON text to common .NET types.</span></span> <span data-ttu-id="eb2bd-343">Tipik bir JSON yükünü ayrıştırma ve ' ı kullanarak `JsonDocument` tüm üyelerine erişme, makul ölçüde boyutlandırılabilir (yani , < 1 MB) veriler için çok az ayırmayla 3x ' den daha hızlıdır.</span><span class="sxs-lookup"><span data-stu-id="eb2bd-343">Parsing a typical JSON payload and accessing all its members using the `JsonDocument` is 2-3x faster than **Json.NET** with little allocations for data that is reasonably sized (that is, < 1 MB).</span></span>

<span data-ttu-id="eb2bd-344">Başlangıç noktası olarak kullanılabilecek `JsonDocument` ve ' `JsonElement` nin örnek kullanımı aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="eb2bd-344">Here is a sample usage of the `JsonDocument` and `JsonElement` that can be used as a starting point:</span></span>

[!CODE-csharp[JsonDocument](~/samples/snippets/core/whats-new/whats-new-in-30/cs/program.cs#ReadJson)]

<span data-ttu-id="eb2bd-345">İşte Visual Studio Code tarafından C# oluşturulan [Launch. JSON](https://github.com/dotnet/samples/blob/master/snippets/core/whats-new/whats-new-in-30/cs/launch.json) dosyası aracılığıyla okuma için 8,0 bir örnek:</span><span class="sxs-lookup"><span data-stu-id="eb2bd-345">Here is a C# 8.0 example of reading through the [**launch.json**](https://github.com/dotnet/samples/blob/master/snippets/core/whats-new/whats-new-in-30/cs/launch.json) file created by Visual Studio Code:</span></span>

[!CODE-csharp[JsonDocument](~/samples/snippets/core/whats-new/whats-new-in-30/cs/program.cs#ReadJsonCall)]

### <a name="jsonserializer"></a><span data-ttu-id="eb2bd-346">JsonSerializer</span><span class="sxs-lookup"><span data-stu-id="eb2bd-346">JsonSerializer</span></span>

<span data-ttu-id="eb2bd-347"><xref:System.Text.Json.JsonSerializer?displayProperty=nameWithType>, ve ' nin <xref:System.Text.Json.Utf8JsonReader> üzerine kurulmuştur ve <xref:System.Text.Json.Utf8JsonWriter> JSON belgeleri ve parçaları ile çalışırken hızlı, düşük bellek serileştirme seçeneği sağlar.</span><span class="sxs-lookup"><span data-stu-id="eb2bd-347"><xref:System.Text.Json.JsonSerializer?displayProperty=nameWithType> is built on top of <xref:System.Text.Json.Utf8JsonReader> and <xref:System.Text.Json.Utf8JsonWriter> to provide a fast, low-memory serialization option when working with JSON documents and fragments.</span></span>

<span data-ttu-id="eb2bd-348">JSON için bir nesneyi serileştirmede bir örnek aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="eb2bd-348">Here is an example of serializing an object to JSON:</span></span>

[!CODE-csharp[JsonSerializer](~/samples/snippets/core/whats-new/whats-new-in-30/cs/JSON.cs#JsonSerialize)]

<span data-ttu-id="eb2bd-349">Bir JSON dizesinin bir nesneye serisini kaldırma örneği aşağıda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="eb2bd-349">Here is an example of deserializing a JSON string to an object.</span></span> <span data-ttu-id="eb2bd-350">Önceki örnek tarafından üretilen JSON dizesini kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="eb2bd-350">You can use the JSON string produced by the previous example:</span></span>

[!CODE-csharp[JsonDeserializer](~/samples/snippets/core/whats-new/whats-new-in-30/cs/JSON.cs#JsonDeserialize)]

## <a name="interop-improvements"></a><span data-ttu-id="eb2bd-351">Birlikte çalışma geliştirmeleri</span><span class="sxs-lookup"><span data-stu-id="eb2bd-351">Interop improvements</span></span>

<span data-ttu-id="eb2bd-352">.NET Core 3,0, yerel API birlikte çalışabilirliği geliştirir.</span><span class="sxs-lookup"><span data-stu-id="eb2bd-352">.NET Core 3.0 improves native API interop.</span></span>

### <a name="type-nativelibrary"></a><span data-ttu-id="eb2bd-353">Tür: NativeLibrary</span><span class="sxs-lookup"><span data-stu-id="eb2bd-353">Type: NativeLibrary</span></span>

<span data-ttu-id="eb2bd-354"><xref:System.Runtime.InteropServices.NativeLibrary?displayProperty=nameWithType>Yerel bir kitaplığı (.NET Core P/Invoke ile aynı yük mantığını kullanarak) yüklemek ve gibi ilgili yardımcı işlevleri `getSymbol`sağlamak için bir kapsülleme sağlar.</span><span class="sxs-lookup"><span data-stu-id="eb2bd-354"><xref:System.Runtime.InteropServices.NativeLibrary?displayProperty=nameWithType> provides an encapsulation for loading a native library (using the same load logic as .NET Core P/Invoke) and providing the relevant helper functions such as `getSymbol`.</span></span> <span data-ttu-id="eb2bd-355">Kod örneği için bkz. [Dllmap tanıtımı](https://github.com/dotnet/samples/tree/master/core/extensions/DllMapDemo).</span><span class="sxs-lookup"><span data-stu-id="eb2bd-355">For a code example, see the [DLLMap Demo](https://github.com/dotnet/samples/tree/master/core/extensions/DllMapDemo).</span></span>

### <a name="windows-native-interop"></a><span data-ttu-id="eb2bd-356">Windows yerel birlikte çalışma</span><span class="sxs-lookup"><span data-stu-id="eb2bd-356">Windows Native Interop</span></span>

<span data-ttu-id="eb2bd-357">Windows, düz C API 'Leri, COM ve WinRT biçiminde zengin bir yerel API sunar.</span><span class="sxs-lookup"><span data-stu-id="eb2bd-357">Windows offers a rich native API in the form of flat C APIs, COM, and WinRT.</span></span> <span data-ttu-id="eb2bd-358">.NET Core **P/Invoke**'ı destekleirken, .net Core 3,0, **com API 'Leri oluşturma** ve **WinRT API 'leri etkinleştirme**özelliğini ekler.</span><span class="sxs-lookup"><span data-stu-id="eb2bd-358">While .NET Core supports **P/Invoke**, .NET Core 3.0 adds the ability to **CoCreate COM APIs** and **Activate WinRT APIs**.</span></span> <span data-ttu-id="eb2bd-359">Kod örneği için bkz. [Excel tanıtımı](https://github.com/dotnet/samples/tree/master/core/extensions/ExcelDemo).</span><span class="sxs-lookup"><span data-stu-id="eb2bd-359">For a code example, see the [Excel Demo](https://github.com/dotnet/samples/tree/master/core/extensions/ExcelDemo).</span></span>

## <a name="http2-support"></a><span data-ttu-id="eb2bd-360">HTTP/2 desteği</span><span class="sxs-lookup"><span data-stu-id="eb2bd-360">HTTP/2 support</span></span>

<span data-ttu-id="eb2bd-361"><xref:System.Net.Http.HttpClient?displayProperty=nameWithType> Tür http/2 protokolünü destekler.</span><span class="sxs-lookup"><span data-stu-id="eb2bd-361">The <xref:System.Net.Http.HttpClient?displayProperty=nameWithType> type supports the HTTP/2 protocol.</span></span> <span data-ttu-id="eb2bd-362">HTTP/2 etkinse HTTP protokol sürümü TLS/ALPN aracılığıyla görüşülür ve sunucunun bunu kullanabilmesi durumunda HTTP/2 kullanılır.</span><span class="sxs-lookup"><span data-stu-id="eb2bd-362">If HTTP/2 is enabled, the HTTP protocol version is negotiated via TLS/ALPN, and HTTP/2 is used if the server elects to use it.</span></span>

<span data-ttu-id="eb2bd-363">Varsayılan protokol HTTP/1.1 olarak kalır, ancak HTTP/2 iki farklı şekilde etkinleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="eb2bd-363">The default protocol remains HTTP/1.1, but HTTP/2 can be enabled in two different ways.</span></span> <span data-ttu-id="eb2bd-364">İlk olarak http istek iletisini HTTP/2 kullanacak şekilde ayarlayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="eb2bd-364">First, you can set the HTTP request message to use HTTP/2:</span></span>

[!CODE-csharp[Http2Request](~/samples/snippets/core/whats-new/whats-new-in-30/cs/http.cs#Request)]

<span data-ttu-id="eb2bd-365">İkincisi, varsayılan olarak http <xref:System.Net.Http.HttpClient> /2 kullan seçeneğini kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="eb2bd-365">Second, you can change <xref:System.Net.Http.HttpClient> to use HTTP/2 by default:</span></span>

[!CODE-csharp[Http2Client](~/samples/snippets/core/whats-new/whats-new-in-30/cs/http.cs#Client)]

<span data-ttu-id="eb2bd-366">Uygulama geliştirirken birçok kez şifrelenmemiş bağlantı kullanmak istersiniz.</span><span class="sxs-lookup"><span data-stu-id="eb2bd-366">Many times when you're developing an application, you want to use an unencrypted connection.</span></span> <span data-ttu-id="eb2bd-367">Hedef uç noktanın HTTP/2 kullanacağınızı biliyorsanız, HTTP/2 için şifrelenmemiş bağlantıları açabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="eb2bd-367">If you know the target endpoint will be using HTTP/2, you can turn on unencrypted connections for HTTP/2.</span></span> <span data-ttu-id="eb2bd-368">`DOTNET_SYSTEM_NET_HTTP_SOCKETSHTTPHANDLER_HTTP2UNENCRYPTEDSUPPORT` Ortam değişkenini uygulama bağlamında etkinleştirerek veya olarak `1` ayarlayarak bu ayarı açabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="eb2bd-368">You can turn it on by setting the `DOTNET_SYSTEM_NET_HTTP_SOCKETSHTTPHANDLER_HTTP2UNENCRYPTEDSUPPORT` environment variable to `1` or by enabling it in the app context:</span></span>

[!CODE-csharp[Http2Context](~/samples/snippets/core/whats-new/whats-new-in-30/cs/http.cs#AppContext)]

## <a name="tls-13--openssl-111-on-linux"></a><span data-ttu-id="eb2bd-369">TLS 1,3 & Linux üzerinde OpenSSL 1.1.1</span><span class="sxs-lookup"><span data-stu-id="eb2bd-369">TLS 1.3 & OpenSSL 1.1.1 on Linux</span></span>

<span data-ttu-id="eb2bd-370">.NET Core artık, belirli bir ortamda kullanılabildiği [OpenSSL 1.1.1 Içindeki TLS 1,3 desteğinin](https://www.openssl.org/blog/blog/2018/09/11/release111/)avantajlarından yararlanır.</span><span class="sxs-lookup"><span data-stu-id="eb2bd-370">.NET Core now takes advantage of [TLS 1.3 support in OpenSSL 1.1.1](https://www.openssl.org/blog/blog/2018/09/11/release111/), when it's available in a given environment.</span></span> <span data-ttu-id="eb2bd-371">TLS 1,3:</span><span class="sxs-lookup"><span data-stu-id="eb2bd-371">With TLS 1.3:</span></span>

- <span data-ttu-id="eb2bd-372">İstemci ve sunucu arasında gereken azaltılan gidiş dönüşlerle bağlantı süreleri geliştirildi.</span><span class="sxs-lookup"><span data-stu-id="eb2bd-372">Connection times are improved with reduced round trips required between the client and server.</span></span>
- <span data-ttu-id="eb2bd-373">Kullanılmayan ve güvenli olmayan şifreleme algoritmalarının kaldırılması nedeniyle güvenlik geliştirildi.</span><span class="sxs-lookup"><span data-stu-id="eb2bd-373">Improved security because of the removal of various obsolete and insecure cryptographic algorithms.</span></span>

<span data-ttu-id="eb2bd-374">Kullanılabilir olduğunda, .NET Core 3,0 bir Linux sisteminde **OpenSSL 1.1.1**, **OpenSSL 1.1.0**veya **OpenSSL 1.0.2** kullanır.</span><span class="sxs-lookup"><span data-stu-id="eb2bd-374">When available, .NET Core 3.0 uses **OpenSSL 1.1.1**, **OpenSSL 1.1.0**, or **OpenSSL 1.0.2** on a Linux system.</span></span> <span data-ttu-id="eb2bd-375">**OpenSSL 1.1.1** kullanılabilir olduğunda, her ikisi <xref:System.Net.Security.SslStream?displayProperty=nameWithType> de <xref:System.Net.Http.HttpClient?displayProperty=nameWithType> tür **TLS 1,3** kullanır (istemci ve sunucunun **TLS 1,3**' i desteklediği varsayıldığında).</span><span class="sxs-lookup"><span data-stu-id="eb2bd-375">When **OpenSSL 1.1.1** is available, both <xref:System.Net.Security.SslStream?displayProperty=nameWithType> and <xref:System.Net.Http.HttpClient?displayProperty=nameWithType> types will use **TLS 1.3** (assuming both the client and server support **TLS 1.3**).</span></span>

>[!IMPORTANT]
><span data-ttu-id="eb2bd-376">Windows ve macOS henüz **TLS 1,3**' i desteklemez.</span><span class="sxs-lookup"><span data-stu-id="eb2bd-376">Windows and macOS do not yet support **TLS 1.3**.</span></span> <span data-ttu-id="eb2bd-377">.NET Core 3,0, destek kullanılabilir hale geldiğinde bu işletim sistemlerinde **TLS 1,3** ' i destekleyecektir.</span><span class="sxs-lookup"><span data-stu-id="eb2bd-377">.NET Core 3.0 will support **TLS 1.3** on these operating systems when support becomes available.</span></span>

<span data-ttu-id="eb2bd-378">Aşağıdaki C# 8,0 örneği, ' a bağlanan <https://www.cloudflare.com>Ubuntu 18,10 üzerinde .NET Core 3,0 ' i göstermektedir:</span><span class="sxs-lookup"><span data-stu-id="eb2bd-378">The following C# 8.0 example demonstrates .NET Core 3.0 on Ubuntu 18.10 connecting to <https://www.cloudflare.com>:</span></span>

[!CODE-csharp[TLSExample](~/samples/snippets/core/whats-new/whats-new-in-30/cs/TLS.cs#TLS)]

## <a name="cryptography-ciphers"></a><span data-ttu-id="eb2bd-379">Şifreleme şifrelemeleri</span><span class="sxs-lookup"><span data-stu-id="eb2bd-379">Cryptography ciphers</span></span>

<span data-ttu-id="eb2bd-380">.NET 3,0, ile <xref:System.Security.Cryptography.AesGcm?displayProperty=nameWithType> ve <xref:System.Security.Cryptography.AesCcm?displayProperty=nameWithType> sırasıyla uygulanan **AES-GCM** ve **AES-CCM** şifrelemeleri için destek ekler.</span><span class="sxs-lookup"><span data-stu-id="eb2bd-380">.NET 3.0 adds support for **AES-GCM** and **AES-CCM** ciphers, implemented with <xref:System.Security.Cryptography.AesGcm?displayProperty=nameWithType> and <xref:System.Security.Cryptography.AesCcm?displayProperty=nameWithType> respectively.</span></span> <span data-ttu-id="eb2bd-381">Bu algoritmalar, [Ilişki verileri (AEAD) algoritmalarıyla kimliği doğrulanmış şifrelemedir](https://en.wikipedia.org/wiki/Authenticated_encryption).</span><span class="sxs-lookup"><span data-stu-id="eb2bd-381">These algorithms are both [Authenticated Encryption with Association Data (AEAD) algorithms](https://en.wikipedia.org/wiki/Authenticated_encryption).</span></span>

<span data-ttu-id="eb2bd-382">Aşağıdaki kod, rastgele verileri `AesGcm` şifrelemek ve şifrelerini çözmek için şifre kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="eb2bd-382">The following code demonstrates using `AesGcm` cipher to encrypt and decrypt random data.</span></span>

[!CODE-csharp[AesGcm](~/samples/snippets/core/whats-new/whats-new-in-30/cs/Cipher.cs#AesGcm)]

## <a name="cryptographic-key-importexport"></a><span data-ttu-id="eb2bd-383">Şifreleme anahtarı Içeri/dışarı aktarma</span><span class="sxs-lookup"><span data-stu-id="eb2bd-383">Cryptographic Key Import/Export</span></span>

<span data-ttu-id="eb2bd-384">.NET Core 3,0, asimetrik ortak ve özel anahtarların standart biçimlerden içeri ve dışarı aktarılmasını destekler.</span><span class="sxs-lookup"><span data-stu-id="eb2bd-384">.NET Core 3.0 supports the import and export of asymmetric public and private keys from standard formats.</span></span> <span data-ttu-id="eb2bd-385">X. 509.440 sertifikası kullanmanız gerekmez.</span><span class="sxs-lookup"><span data-stu-id="eb2bd-385">You don't need to use an X.509 certificate.</span></span>

<span data-ttu-id="eb2bd-386">*RSA*, *dsa*, *ECDSA*ve *ecdıfıfiehellman*gibi tüm anahtar türleri aşağıdaki biçimleri destekler:</span><span class="sxs-lookup"><span data-stu-id="eb2bd-386">All key types, such as *RSA*, *DSA*, *ECDsa*, and *ECDiffieHellman*, support the following formats:</span></span>

- <span data-ttu-id="eb2bd-387">**Ortak anahtar**</span><span class="sxs-lookup"><span data-stu-id="eb2bd-387">**Public Key**</span></span>
  - <span data-ttu-id="eb2bd-388">X. 509.440 Subjectpublickeyınfo</span><span class="sxs-lookup"><span data-stu-id="eb2bd-388">X.509 SubjectPublicKeyInfo</span></span>

- <span data-ttu-id="eb2bd-389">**Özel anahtar**</span><span class="sxs-lookup"><span data-stu-id="eb2bd-389">**Private key**</span></span>
  - <span data-ttu-id="eb2bd-390">PKCS # 8 Privatekeyınfo</span><span class="sxs-lookup"><span data-stu-id="eb2bd-390">PKCS#8 PrivateKeyInfo</span></span>
  - <span data-ttu-id="eb2bd-391">PKCS # 8 Encryptedprivatekeyınfo</span><span class="sxs-lookup"><span data-stu-id="eb2bd-391">PKCS#8 EncryptedPrivateKeyInfo</span></span>

<span data-ttu-id="eb2bd-392">RSA anahtarları da şunları destekler:</span><span class="sxs-lookup"><span data-stu-id="eb2bd-392">RSA keys also support:</span></span>

- <span data-ttu-id="eb2bd-393">**Ortak anahtar**</span><span class="sxs-lookup"><span data-stu-id="eb2bd-393">**Public Key**</span></span>
  - <span data-ttu-id="eb2bd-394">PKCS # 1 RSAPublicKey</span><span class="sxs-lookup"><span data-stu-id="eb2bd-394">PKCS#1 RSAPublicKey</span></span>

- <span data-ttu-id="eb2bd-395">**Özel anahtar**</span><span class="sxs-lookup"><span data-stu-id="eb2bd-395">**Private key**</span></span>
  - <span data-ttu-id="eb2bd-396">PKCS # 1 RSAPrivateKey</span><span class="sxs-lookup"><span data-stu-id="eb2bd-396">PKCS#1 RSAPrivateKey</span></span>

<span data-ttu-id="eb2bd-397">Dışarı aktarma yöntemleri DER kodlu ikili veriler oluşturur ve içeri aktarma yöntemleri aynı şekilde bekler.</span><span class="sxs-lookup"><span data-stu-id="eb2bd-397">The export methods produce DER-encoded binary data, and the import methods expect the same.</span></span> <span data-ttu-id="eb2bd-398">Bir anahtar, metin kullanımı kolay pek biçiminde depolanıyorsa, bir içeri aktarma yöntemi çağrılmadan önce çağıranın içerik Base64 olarak çözülmesi gerekecektir.</span><span class="sxs-lookup"><span data-stu-id="eb2bd-398">If a key is stored in the text-friendly PEM format, the caller will need to base64-decode the content before calling an import method.</span></span>

[!CODE-csharp[RSA](~/samples/snippets/core/whats-new/whats-new-in-30/cs/RSA.cs#Rsa)]

<span data-ttu-id="eb2bd-399">**PKCS # 8** dosyaları ile <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo?displayProperty=nameWithType> incelenebilir ve **PFX/PKCS # 12** dosyaları ile <xref:System.Security.Cryptography.Pkcs.Pkcs12Info?displayProperty=nameWithType>incelenebilir.</span><span class="sxs-lookup"><span data-stu-id="eb2bd-399">**PKCS#8** files can be inspected with <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo?displayProperty=nameWithType> and **PFX/PKCS#12** files can be inspected with <xref:System.Security.Cryptography.Pkcs.Pkcs12Info?displayProperty=nameWithType>.</span></span> <span data-ttu-id="eb2bd-400">**PFX/PKCS # 12** dosyaları ile <xref:System.Security.Cryptography.Pkcs.Pkcs12Builder?displayProperty=nameWithType>değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="eb2bd-400">**PFX/PKCS#12** files can be manipulated with <xref:System.Security.Cryptography.Pkcs.Pkcs12Builder?displayProperty=nameWithType>.</span></span>

## <a name="serialport-for-linux"></a><span data-ttu-id="eb2bd-401">Linux için SerialPort</span><span class="sxs-lookup"><span data-stu-id="eb2bd-401">SerialPort for Linux</span></span>

<span data-ttu-id="eb2bd-402">.NET Core 3,0, Linux üzerinde için <xref:System.IO.Ports.SerialPort?displayProperty=nameWithType> temel desteği sağlar.</span><span class="sxs-lookup"><span data-stu-id="eb2bd-402">.NET Core 3.0 provides basic support for <xref:System.IO.Ports.SerialPort?displayProperty=nameWithType> on Linux.</span></span>

<span data-ttu-id="eb2bd-403">Daha önce, .NET Core yalnızca Windows `SerialPort` 'da kullanımı desteklenir.</span><span class="sxs-lookup"><span data-stu-id="eb2bd-403">Previously, .NET Core only supported using `SerialPort` on Windows.</span></span>

<span data-ttu-id="eb2bd-404">Linux 'ta seri bağlantı noktası için sınırlı destek hakkında daha fazla bilgi için bkz. [GitHub sorun #33146](https://github.com/dotnet/corefx/issues/33146).</span><span class="sxs-lookup"><span data-stu-id="eb2bd-404">For more information about the limited support for the serial port on Linux, see [GitHub issue #33146](https://github.com/dotnet/corefx/issues/33146).</span></span>

## <a name="docker-and-cgroup-memory-limits"></a><span data-ttu-id="eb2bd-405">Docker ve cgroup bellek sınırları</span><span class="sxs-lookup"><span data-stu-id="eb2bd-405">Docker and cgroup memory Limits</span></span>

<span data-ttu-id="eb2bd-406">Preview 3 ' ü kullanmaya başlamadan, Docker ile Linux üzerinde .NET Core 3,0 çalıştırmak, cgroup bellek limitleriyle daha iyi çalışır.</span><span class="sxs-lookup"><span data-stu-id="eb2bd-406">Starting with Preview 3, running .NET Core 3.0 on Linux with Docker works better with cgroup memory limits.</span></span> <span data-ttu-id="eb2bd-407">İle `docker run -m`gibi bellek limitleriyle bir Docker kapsayıcısı çalıştırmak, .NET Core 'un davranış şeklini değiştirir.</span><span class="sxs-lookup"><span data-stu-id="eb2bd-407">Running a Docker container with memory limits, such as with `docker run -m`, changes how .NET Core behaves.</span></span>

- <span data-ttu-id="eb2bd-408">Varsayılan atık toplayıcı (GC) yığın boyutu: kapsayıcıda bellek sınırının en fazla 20 MB veya% 75 ' si.</span><span class="sxs-lookup"><span data-stu-id="eb2bd-408">Default Garbage Collector (GC) heap size: maximum of 20 mb or 75% of the memory limit on the container.</span></span>
- <span data-ttu-id="eb2bd-409">Açık Boyut, mutlak bir sayı veya cgroup sınırının yüzdesi olarak ayarlanabilir.</span><span class="sxs-lookup"><span data-stu-id="eb2bd-409">Explicit size can be set as an absolute number or percentage of cgroup limit.</span></span>
- <span data-ttu-id="eb2bd-410">GC yığını başına en düşük ayrılmış kesim boyutu 16 MB 'tır.</span><span class="sxs-lookup"><span data-stu-id="eb2bd-410">Minimum reserved segment size per GC heap is 16 mb.</span></span> <span data-ttu-id="eb2bd-411">Bu boyut, makinelerde oluşturulan Heap sayısını azaltır.</span><span class="sxs-lookup"><span data-stu-id="eb2bd-411">This size reduces the number of heaps that are created on machines.</span></span>

## <a name="smaller-garbage-collection-heap-sizes"></a><span data-ttu-id="eb2bd-412">Daha küçük atık toplama yığın boyutları</span><span class="sxs-lookup"><span data-stu-id="eb2bd-412">Smaller Garbage Collection heap sizes</span></span>

<span data-ttu-id="eb2bd-413">Atık toplayıcısının varsayılan yığın boyutu daha az bellek kullanan .NET Core ile sonuçlanır.</span><span class="sxs-lookup"><span data-stu-id="eb2bd-413">The Garbage Collector's default heap size has been reduced resulting in .NET Core using less memory.</span></span> <span data-ttu-id="eb2bd-414">Bu değişiklik, modern işlemci önbelleği boyutları ile nesil 0 ayırma bütçesine göre daha iyi hizalanır.</span><span class="sxs-lookup"><span data-stu-id="eb2bd-414">This change better aligns with the generation 0 allocation budget with modern processor cache sizes.</span></span>

## <a name="garbage-collection-large-page-support"></a><span data-ttu-id="eb2bd-415">Çöp toplama büyük sayfa desteği</span><span class="sxs-lookup"><span data-stu-id="eb2bd-415">Garbage Collection Large Page support</span></span>

<span data-ttu-id="eb2bd-416">Büyük sayfalar (Linux 'ta çok büyük sayfalar olarak da bilinir), işletim sisteminin bu büyük sayfaları isteyen uygulamanın performansını artırmak için yerel sayfa boyutundan (genellikle 4K) daha büyük bellek bölgeleri ayarlayabildiği bir özelliktir.</span><span class="sxs-lookup"><span data-stu-id="eb2bd-416">Large Pages (also known as Huge Pages on Linux) is a feature where the operating system is able to establish memory regions larger than the native page size (often 4K) to improve performance of the application requesting these large pages.</span></span>

<span data-ttu-id="eb2bd-417">Çöp toplayıcı artık Windows üzerinde büyük sayfalar ayırmayı seçmek için bir katılım özelliği olarak **Gclargepages** ayarıyla yapılandırılabilir.</span><span class="sxs-lookup"><span data-stu-id="eb2bd-417">The Garbage Collector can now be configured with the **GCLargePages** setting as an opt-in feature to choose to allocate large pages on Windows.</span></span>

## <a name="gpio-support-for-raspberry-pi"></a><span data-ttu-id="eb2bd-418">Raspberry PI için GıO desteği</span><span class="sxs-lookup"><span data-stu-id="eb2bd-418">GPIO Support for Raspberry Pi</span></span>

<span data-ttu-id="eb2bd-419">NuGet 'e GıO programlama için kullanabileceğiniz iki paket yayımlanmıştır:</span><span class="sxs-lookup"><span data-stu-id="eb2bd-419">Two packages have been released to NuGet that you can use for GPIO programming:</span></span>

- [<span data-ttu-id="eb2bd-420">System. Device. GIO</span><span class="sxs-lookup"><span data-stu-id="eb2bd-420">System.Device.Gpio</span></span>](https://www.nuget.org/packages/System.Device.Gpio)
- [<span data-ttu-id="eb2bd-421">IoT. Device. Bindings</span><span class="sxs-lookup"><span data-stu-id="eb2bd-421">Iot.Device.Bindings</span></span>](https://www.nuget.org/packages/Iot.Device.Bindings)

<span data-ttu-id="eb2bd-422">GPıO paketleri, *GIO*, *SPI*, *I2C*ve *PWM* cihazları için API 'ler içerir.</span><span class="sxs-lookup"><span data-stu-id="eb2bd-422">The GPIO packages include APIs for *GPIO*, *SPI*, *I2C*, and *PWM* devices.</span></span> <span data-ttu-id="eb2bd-423">IoT bağlamaları paketi cihaz bağlamalarını içerir.</span><span class="sxs-lookup"><span data-stu-id="eb2bd-423">The IoT bindings package includes device bindings.</span></span> <span data-ttu-id="eb2bd-424">Daha fazla bilgi için bkz. [cihaz GitHub deposu](https://github.com/dotnet/iot/blob/master/src/devices/).</span><span class="sxs-lookup"><span data-stu-id="eb2bd-424">For more information, see the [devices GitHub repo](https://github.com/dotnet/iot/blob/master/src/devices/).</span></span>

## <a name="arm64-linux-support"></a><span data-ttu-id="eb2bd-425">ARM64 Linux desteği</span><span class="sxs-lookup"><span data-stu-id="eb2bd-425">ARM64 Linux support</span></span>

<span data-ttu-id="eb2bd-426">.NET Core 3,0, Linux için ARM64 desteği ekler.</span><span class="sxs-lookup"><span data-stu-id="eb2bd-426">.NET Core 3.0 adds support for ARM64 for Linux.</span></span> <span data-ttu-id="eb2bd-427">ARM64 için birincil kullanım örneği şu anda IoT senaryolarıyla birlikte.</span><span class="sxs-lookup"><span data-stu-id="eb2bd-427">The primary use case for ARM64 is currently with IoT scenarios.</span></span> <span data-ttu-id="eb2bd-428">Daha fazla bilgi için bkz. [.NET Core ARM64 Status](https://github.com/dotnet/announcements/issues/82).</span><span class="sxs-lookup"><span data-stu-id="eb2bd-428">For more information, see [.NET Core ARM64 Status](https://github.com/dotnet/announcements/issues/82).</span></span>

<span data-ttu-id="eb2bd-429">[ARM64 üzerinde .NET Core Için Docker görüntüleri](https://hub.docker.com/r/microsoft/dotnet/) alp, de, ve Ubuntu için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="eb2bd-429">[Docker images for .NET Core on ARM64](https://hub.docker.com/r/microsoft/dotnet/) are available for Alpine, Debian, and Ubuntu.</span></span>

> [!NOTE]
> <span data-ttu-id="eb2bd-430">**ARM64** Windows desteği henüz kullanılamıyor.</span><span class="sxs-lookup"><span data-stu-id="eb2bd-430">**ARM64** Windows support isn't yet available.</span></span>
