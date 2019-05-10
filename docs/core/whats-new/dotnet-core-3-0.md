---
title: .NET Core 3. 0'yenilikler nelerdir?
description: .NET Core 3. 0 ' bulunan yeni özellikler hakkında bilgi edinin.
dev_langs:
- csharp
- vb
author: thraka
ms.author: adegeo
ms.date: 05/06/2019
ms.openlocfilehash: 8d6ff6bc55384281119600f2323212441c1815e9
ms.sourcegitcommit: 4c10802ad003374641a2c2373b8a92e3c88babc8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/08/2019
ms.locfileid: "65452473"
---
# <a name="whats-new-in-net-core-30-preview-5"></a><span data-ttu-id="bccc1-103">.NET Core 3.0 (Preview 5) yenilikler</span><span class="sxs-lookup"><span data-stu-id="bccc1-103">What's new in .NET Core 3.0 (Preview 5)</span></span>

<span data-ttu-id="bccc1-104">Bu makalede, .NET Core 3.0 içinde yeni (Önizleme 5) Yenilikler açıklanır.</span><span class="sxs-lookup"><span data-stu-id="bccc1-104">This article describes what is new in .NET Core 3.0 (through preview 5).</span></span> <span data-ttu-id="bccc1-105">Büyük iyileştirmeler Windows Masaüstü uygulamaları (yalnızca Windows) için destek biridir.</span><span class="sxs-lookup"><span data-stu-id="bccc1-105">One of the biggest enhancements is support for Windows desktop applications (Windows only).</span></span> <span data-ttu-id="bccc1-106">Windows Masaüstü .NET Core 3.0 SDK'sı bileşenini kullanarak, Windows Forms ve Windows Presentation Foundation (WPF), uygulamalarınızın bağlantı noktası.</span><span class="sxs-lookup"><span data-stu-id="bccc1-106">By using the .NET Core 3.0 SDK component Windows Desktop, you can port your Windows Forms and Windows Presentation Foundation (WPF) applications.</span></span> <span data-ttu-id="bccc1-107">Gerekirse Windows Masaüstü bileşen yalnızca desteklenen ve Windows üzerinde dahil.</span><span class="sxs-lookup"><span data-stu-id="bccc1-107">To be clear, the Windows Desktop component is only supported and included on Windows.</span></span> <span data-ttu-id="bccc1-108">Daha fazla bilgi için [Windows Masaüstü](#windows-desktop) bu makalenin devamındaki bölümü.</span><span class="sxs-lookup"><span data-stu-id="bccc1-108">For more information, see the [Windows desktop](#windows-desktop) section later in this article.</span></span>

<span data-ttu-id="bccc1-109">.NET core 3.0 için destek ekler C# 8.0.</span><span class="sxs-lookup"><span data-stu-id="bccc1-109">.NET Core 3.0 adds support for C# 8.0.</span></span> <span data-ttu-id="bccc1-110">OmniSharp uzantısıyla Visual Studio 2019 güncelleştirme 1 Preview veya VSCode en son sürümünü kullanmanız önerilir.</span><span class="sxs-lookup"><span data-stu-id="bccc1-110">It's highly recommended that you use the latest release of Visual Studio 2019 Update 1 Preview or VSCode with the OmniSharp extension.</span></span>

<span data-ttu-id="bccc1-111">[İndirin ve .NET Core 3.0 Preview 5 ile çalışmaya başlama](https://aka.ms/netcore3download) şu anda Windows, Mac ve Linux üzerinde.</span><span class="sxs-lookup"><span data-stu-id="bccc1-111">[Download and get started with .NET Core 3.0 Preview 5](https://aka.ms/netcore3download) right now on Windows, Mac, and Linux.</span></span>

<span data-ttu-id="bccc1-112">Her önizleme sürümü hakkında daha fazla bilgi için aşağıdaki duyuruları bakın:</span><span class="sxs-lookup"><span data-stu-id="bccc1-112">For more information about each preview release, see the following announcements:</span></span>

- [<span data-ttu-id="bccc1-113">.NET core 3.0 Preview 5 Duyurusu</span><span class="sxs-lookup"><span data-stu-id="bccc1-113">.NET Core 3.0 Preview 5 announcement</span></span>](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-0-preview-5/)
- [<span data-ttu-id="bccc1-114">.NET core 3.0 Önizleme 4 Duyurusu</span><span class="sxs-lookup"><span data-stu-id="bccc1-114">.NET Core 3.0 Preview 4 announcement</span></span>](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-preview-4/)
- [<span data-ttu-id="bccc1-115">.NET core 3.0 Preview 3 Duyurusu</span><span class="sxs-lookup"><span data-stu-id="bccc1-115">.NET Core 3.0 Preview 3 announcement</span></span>](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-preview-3/)
- [<span data-ttu-id="bccc1-116">.NET core 3.0 Önizleme 2 Duyurusu</span><span class="sxs-lookup"><span data-stu-id="bccc1-116">.NET Core 3.0 Preview 2 announcement</span></span>](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-preview-2/)
- [<span data-ttu-id="bccc1-117">.NET core 3.0 Önizleme 1 Duyurusu</span><span class="sxs-lookup"><span data-stu-id="bccc1-117">.NET Core 3.0 Preview 1 announcement</span></span>](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-preview-1-and-open-sourcing-windows-desktop-frameworks/)

## <a name="net-core-sdk-windows-installer"></a><span data-ttu-id="bccc1-118">.NET core SDK'sı, Windows Yükleyicisi</span><span class="sxs-lookup"><span data-stu-id="bccc1-118">.NET Core SDK Windows Installer</span></span>

<span data-ttu-id="bccc1-119">MSI yükleyicisini Windows için .NET Core 3. 0'ile başlayan değişti.</span><span class="sxs-lookup"><span data-stu-id="bccc1-119">The MSI installer for Windows has changed starting with .NET Core 3.0.</span></span> <span data-ttu-id="bccc1-120">SDK'sı yükleyicileri artık yerinde SDK bant dışı yayınlar yükseltir.</span><span class="sxs-lookup"><span data-stu-id="bccc1-120">The SDK installers will now upgrade SDK feature-band releases in place.</span></span> <span data-ttu-id="bccc1-121">Özellik bantları tanımlanmış *yüzlerce* içindeki gruplara *düzeltme eki* sürüm numarasının bölümü.</span><span class="sxs-lookup"><span data-stu-id="bccc1-121">Feature bands are defined in the *hundreds* groups in the *patch* section of the version number.</span></span> <span data-ttu-id="bccc1-122">Örneğin, **3.0. \* 101**\* ve **3.0. \* 201**\* sırasında iki farklı özellik bantları sürümlerinde olan **3.0. \* 101**\* ve **3.0. \* 199**\* bulunan aynı özellik bant.</span><span class="sxs-lookup"><span data-stu-id="bccc1-122">For example, **3.0.\*101**\* and **3.0.\*201**\* are versions in two different feature bands while **3.0.\*101**\* and **3.0.\*199**\* are in the same feature band.</span></span> <span data-ttu-id="bccc1-123">Ve ne zaman .NET Core SDK'sı **3.0. \* 101**\* olan .NET Core SDK'sı yüklü **3.0. \* 100**\* varsa makineden kaldırılacak.</span><span class="sxs-lookup"><span data-stu-id="bccc1-123">And, when .NET Core SDK **3.0.\*101**\* is installed, .NET Core SDK **3.0.\*100**\* will be removed from the machine if it exists.</span></span> <span data-ttu-id="bccc1-124">.NET Core SDK'sı **3.0. \* 200**\* aynı makinede, .NET Core SDK'sı yüklü **3.0. \* 101**\* kaldırılmaz.</span><span class="sxs-lookup"><span data-stu-id="bccc1-124">When .NET Core SDK **3.0.\*200**\* is installed on the same machine, .NET Core SDK **3.0.\*101**\* won't be removed.</span></span>

<span data-ttu-id="bccc1-125">Sürüm oluşturma hakkında daha fazla bilgi için bkz. [nasıl .NET Core tutulan genel bakış](../versions/index.md).</span><span class="sxs-lookup"><span data-stu-id="bccc1-125">For more information about versioning, see [Overview of how .NET Core is versioned](../versions/index.md).</span></span>

## <a name="c-80-preview"></a><span data-ttu-id="bccc1-126">C#8.0 Önizleme</span><span class="sxs-lookup"><span data-stu-id="bccc1-126">C# 8.0 preview</span></span>

<span data-ttu-id="bccc1-127">.NET core 3.0 destekleyen C# 8 önizleme.</span><span class="sxs-lookup"><span data-stu-id="bccc1-127">.NET Core 3.0 supports C# 8 preview.</span></span> <span data-ttu-id="bccc1-128">Hakkında daha fazla bilgi için C# 8.0 özellikler bkz [yenilikler C# 8.0](../../csharp/whats-new/csharp-8.md).</span><span class="sxs-lookup"><span data-stu-id="bccc1-128">For more information about C# 8.0 features, see [What's new in C# 8.0](../../csharp/whats-new/csharp-8.md).</span></span>

## <a name="net-standard-21"></a><span data-ttu-id="bccc1-129">.NET standard 2.1</span><span class="sxs-lookup"><span data-stu-id="bccc1-129">.NET Standard 2.1</span></span>

<span data-ttu-id="bccc1-130">.NET Core 3.0 desteklemesine rağmen **.NET standart 2.1**, varsayılan `dotnet new classlib` şablon hedefleyen bir proje oluşturur **.NET Standard 2.0**.</span><span class="sxs-lookup"><span data-stu-id="bccc1-130">Even though .NET Core 3.0 supports **.NET Standard 2.1**, the default `dotnet new classlib` template generates a project that targets **.NET Standard 2.0**.</span></span> <span data-ttu-id="bccc1-131">Hedef **.NET standart 2.1**, proje dosyanızı düzenleyin ve değiştirin `TargetFramework` özelliğini `netstandard2.1`:</span><span class="sxs-lookup"><span data-stu-id="bccc1-131">To target **.NET Standard 2.1**, edit your project file and change the `TargetFramework` property to `netstandard2.1`:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
 
  <PropertyGroup>
    <TargetFramework>netstandard2.1</TargetFramework>
  </PropertyGroup>
 
</Project>
```

<span data-ttu-id="bccc1-132">Visual Studio kullanıyorsanız, Visual Studio 2017'yi desteklemediğinden Visual Studio 2019 gereken **.NET standart 2.1** veya **.NET Core 3.0**.</span><span class="sxs-lookup"><span data-stu-id="bccc1-132">If you're using Visual Studio, you need Visual Studio 2019, as Visual Studio 2017 doesn't support **.NET Standard 2.1** or **.NET Core 3.0**.</span></span> <span data-ttu-id="bccc1-133">Kullanmanızı öneririz [Visual Studio 2019 güncelleştirme 1 Preview](https://visualstudio.microsoft.com/vs/preview/).</span><span class="sxs-lookup"><span data-stu-id="bccc1-133">We highly recommend that you use [Visual Studio 2019 Update 1 Preview](https://visualstudio.microsoft.com/vs/preview/).</span></span>

## <a name="improved-net-core-version-apis"></a><span data-ttu-id="bccc1-134">Geliştirilmiş .NET Core sürümü API'leri</span><span class="sxs-lookup"><span data-stu-id="bccc1-134">Improved .NET Core Version APIs</span></span>

<span data-ttu-id="bccc1-135">.NET Core 3.0 API'leri bilgileri dönüş artık .NET Core ile sağlanan sürüm başlangıç beklediğiniz.</span><span class="sxs-lookup"><span data-stu-id="bccc1-135">Starting with .NET Core 3.0, the version APIs provided with .NET Core now return the information you expect.</span></span> <span data-ttu-id="bccc1-136">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="bccc1-136">For example:</span></span>

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
> <span data-ttu-id="bccc1-137">Yeni değişiklik.</span><span class="sxs-lookup"><span data-stu-id="bccc1-137">Breaking change.</span></span> <span data-ttu-id="bccc1-138">Sürüm oluşturma düzeni değiştirdiği için teknik bir değişiklik budur.</span><span class="sxs-lookup"><span data-stu-id="bccc1-138">This is technically a breaking change because the versioning scheme has changed.</span></span>

## <a name="net-platform-dependent-intrinsics"></a><span data-ttu-id="bccc1-139">.NET platform bağımlı iç bilgileri</span><span class="sxs-lookup"><span data-stu-id="bccc1-139">.NET Platform-Dependent Intrinsics</span></span>

<span data-ttu-id="bccc1-140">Gibi belirli performans odaklı CPU yönergeleri için erişime izin API'ler eklenmiştir **SIMD** veya **Bit işleme yönerge** ayarlar.</span><span class="sxs-lookup"><span data-stu-id="bccc1-140">APIs have been added that allow access to certain perf-oriented CPU instructions, such as the **SIMD** or **Bit Manipulation instruction** sets.</span></span> <span data-ttu-id="bccc1-141">Bu yönergeler, verileri verimli bir şekilde paralel işleme gibi bazı senaryolarda, önemli performans geliştirmeleri elde etmeye yardımcı olabilir.</span><span class="sxs-lookup"><span data-stu-id="bccc1-141">These instructions can help achieve significant performance improvements in certain scenarios, such as processing data efficiently in parallel.</span></span> 

<span data-ttu-id="bccc1-142">Uygun olan yerlerde, performansı artırmak için bu yönergeleri kullanarak .NET kitaplıklarına başlamıştır.</span><span class="sxs-lookup"><span data-stu-id="bccc1-142">Where appropriate, the .NET libraries have begun using these instructions to improve performance.</span></span>

<span data-ttu-id="bccc1-143">Daha fazla bilgi için [.NET platformu bağımlı yapı içleri](https://github.com/dotnet/designs/blob/master/accepted/platform-intrinsics.md).</span><span class="sxs-lookup"><span data-stu-id="bccc1-143">For more information, see [.NET Platform Dependent Intrinsics](https://github.com/dotnet/designs/blob/master/accepted/platform-intrinsics.md).</span></span>

## <a name="default-executables"></a><span data-ttu-id="bccc1-144">Varsayılan yürütülebilir dosyalar</span><span class="sxs-lookup"><span data-stu-id="bccc1-144">Default executables</span></span>

<span data-ttu-id="bccc1-145">.NET core şimdi yapılar [framework bağımlı yürütülebilir dosyaları](../deploying/index.md#framework-dependent-executables-fde) varsayılan olarak.</span><span class="sxs-lookup"><span data-stu-id="bccc1-145">.NET Core now builds [framework-dependent executables](../deploying/index.md#framework-dependent-executables-fde) by default.</span></span> <span data-ttu-id="bccc1-146">Bu davranış, .NET Core genel olarak yüklenmiş bir sürümünü kullanan uygulamalar için yeni bir özelliktir.</span><span class="sxs-lookup"><span data-stu-id="bccc1-146">This behavior is new for applications that use a globally installed version of .NET Core.</span></span> <span data-ttu-id="bccc1-147">Daha önce yalnızca [müstakil dağıtımları](../deploying/index.md#self-contained-deployments-scd) yürütülebilir bir dosya oluşturur.</span><span class="sxs-lookup"><span data-stu-id="bccc1-147">Previously, only [self-contained deployments](../deploying/index.md#self-contained-deployments-scd) would produce an executable.</span></span>

<span data-ttu-id="bccc1-148">Sırasında `dotnet build` veya `dotnet publish`, kullandığınız SDK platform ve ortam ile eşleşen bir yürütülebilir dosya oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="bccc1-148">During `dotnet build` or `dotnet publish`, an executable is created that matches the environment and platform of the SDK you're using.</span></span> <span data-ttu-id="bccc1-149">Diğer yerel yürütülebilir dosyalar gibi olduğu gibi bu yürütülebilir dosyaları ile aynı şey geçerli olacaktır:</span><span class="sxs-lookup"><span data-stu-id="bccc1-149">You can expect the same things with these executables as you would other native executables, such as:</span></span>

* <span data-ttu-id="bccc1-150">Yürütülebilir dosya üzerine çift tıklayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bccc1-150">You can double-click on the executable.</span></span>
* <span data-ttu-id="bccc1-151">Doğrudan bir komut isteminden uygulama başlatma gibi `myapp.exe` Windows, şirket ve `./myapp` Linux ve Macos'ta.</span><span class="sxs-lookup"><span data-stu-id="bccc1-151">You can launch the application from a command prompt directly, such as `myapp.exe` on Windows, and `./myapp` on Linux and macOS.</span></span>

## <a name="single-file-executables"></a><span data-ttu-id="bccc1-152">Tek Dosyalı yürütülebilir dosyalar</span><span class="sxs-lookup"><span data-stu-id="bccc1-152">Single-file executables</span></span>

<span data-ttu-id="bccc1-153">`dotnet publish` Komutu, platforma özgü tek dosyalı yürütülebilir dosyanın içine uygulamanızı paketleme destekler.</span><span class="sxs-lookup"><span data-stu-id="bccc1-153">The `dotnet publish` command supports packaging your app into a platform-specific single-file executable.</span></span> <span data-ttu-id="bccc1-154">Yürütülebilir dosya, kendiliğinden ve uygulamanızı çalıştırmak için gereken tüm bağımlılıkları (yerel dahil) içerir.</span><span class="sxs-lookup"><span data-stu-id="bccc1-154">The executable is self-extracting and contains all dependencies (including native) that are required to run your app.</span></span> <span data-ttu-id="bccc1-155">Uygulamayı ilk kez çalıştırdığınızda, uygulama üzerinde uygulama tabanlı bir dizine ayıklanır ad ve tanımlayıcı oluşturun.</span><span class="sxs-lookup"><span data-stu-id="bccc1-155">When the app is first run, the application is extracted to a directory based on the app name and build identifier.</span></span> <span data-ttu-id="bccc1-156">Uygulamayı yeniden çalıştırdığınızda başlangıç daha hızlıdır.</span><span class="sxs-lookup"><span data-stu-id="bccc1-156">Startup is faster when the application is run again.</span></span> <span data-ttu-id="bccc1-157">Uygulamanın yeni bir sürüm kullanılmadığı sürece kendisini ikinci kez ayıklamak gerekmez.</span><span class="sxs-lookup"><span data-stu-id="bccc1-157">The application doesn't need to extract itself a second time unless a new version was used.</span></span>

<span data-ttu-id="bccc1-158">Tek dosyalı bir yürütülebilir dosya yayımlamayı ayarlamak `PublishSingleFile` projenizdeki veya komut satırı ile `dotnet publish` komutu:</span><span class="sxs-lookup"><span data-stu-id="bccc1-158">To publish a single-file executable, set the `PublishSingleFile` in your project or on the command line with the `dotnet publish` command:</span></span>

```console
dotnet publish -r win10-x64 /p:PublishSingleFile=true
```

<span data-ttu-id="bccc1-159">Tek dosya yayımlama hakkında daha fazla bilgi için bkz. [tek dosyalı bundler tasarım belge](https://github.com/dotnet/designs/blob/master/accepted/single-file/design.md).</span><span class="sxs-lookup"><span data-stu-id="bccc1-159">For more information about single-file publishing, see the [single-file bundler design document](https://github.com/dotnet/designs/blob/master/accepted/single-file/design.md).</span></span>

## <a name="tiered-compilation"></a><span data-ttu-id="bccc1-160">Katmanlı derleme</span><span class="sxs-lookup"><span data-stu-id="bccc1-160">Tiered compilation</span></span>

<span data-ttu-id="bccc1-161">[Katmanlı derleme](https://devblogs.microsoft.com/dotnet/tiered-compilation-preview-in-net-core-2-1/) .NET Core 3.0 ile varsayılan olarak (TC) etkin.</span><span class="sxs-lookup"><span data-stu-id="bccc1-161">[Tiered compilation](https://devblogs.microsoft.com/dotnet/tiered-compilation-preview-in-net-core-2-1/) (TC) is on by default with .NET Core 3.0.</span></span> <span data-ttu-id="bccc1-162">Bu özellik daha Desenlerinizi daha iyi performans için tam zamanında (JIT) derleyici kullanmak çalışma zamanı sağlar.</span><span class="sxs-lookup"><span data-stu-id="bccc1-162">This feature enables the runtime to more adaptively use the Just-In-Time (JIT) compiler to get better performance.</span></span>

<span data-ttu-id="bccc1-163">TC ana Avantajı (re-) jitting yöntemleriyle daha yavaş ancak-daha hızlı kod üretmek için ya da daha yüksek-kalite-ancak-yavaş kod üretmek için etkinleştirmektir.</span><span class="sxs-lookup"><span data-stu-id="bccc1-163">The main benefit of TC is to enable (re-)jitting methods with slower-but-faster to produce code or higher-quality-but-slower to produce code.</span></span> <span data-ttu-id="bccc1-164">Bu, çeşitli aşamaları boyunca yürütmesinin kararlı bir duruma başlatmanın geçebileceği bir uygulamanın performansını artırmaya yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="bccc1-164">This helps increase performance of an application as it goes through various stages of execution, from startup through steady-state.</span></span> <span data-ttu-id="bccc1-165">Bu, burada her yöntem derlendiğinde TC olmayan yaklaşım ile karşılaştırır, kararlı durum için başlatma performansını güçlü eğilimi nedeniyle bir tek yolu (aynı yüksek kaliteli katmanı).</span><span class="sxs-lookup"><span data-stu-id="bccc1-165">This contrasts with the non-TC approach, where every method is compiled a single way (the same as the high-quality tier), which is biased to steady-state over startup performance.</span></span>

<span data-ttu-id="bccc1-166">Hızlı JIT (katman 0 jıtted kodu) etkinleştirmek için proje dosyanızda bu ayarı kullanın:</span><span class="sxs-lookup"><span data-stu-id="bccc1-166">To enable Quick JIT (tier 0 jitted code), use this setting in your project file:</span></span>

```xml
<PropertyGroup>
  <TieredCompilationQuickJit>true</TieredCompilationQuickJit>
</PropertyGroup>
```

<span data-ttu-id="bccc1-167">TC tamamen devre dışı bırakmak için proje dosyanızda bu ayarı kullanın:</span><span class="sxs-lookup"><span data-stu-id="bccc1-167">To disable TC completely, use this setting in your project file:</span></span>

```xml
<TieredCompilation>false</TieredCompilation>
```

## <a name="build-copies-dependencies"></a><span data-ttu-id="bccc1-168">Derleme bağımlılıkları kopyalar.</span><span class="sxs-lookup"><span data-stu-id="bccc1-168">Build copies dependencies</span></span>

<span data-ttu-id="bccc1-169">`dotnet build` Komutu artık kopyalar NuGet bağımlılıklarını uygulamanız için NuGet önbellekten için derleme çıktısı klasörü.</span><span class="sxs-lookup"><span data-stu-id="bccc1-169">The `dotnet build` command now copies NuGet dependencies for your application from the NuGet cache to the build output folder.</span></span> <span data-ttu-id="bccc1-170">Daha önce bağımlılıkları parçası olarak yalnızca kopyalanan `dotnet publish`.</span><span class="sxs-lookup"><span data-stu-id="bccc1-170">Previously, dependencies were only copied as part of `dotnet publish`.</span></span>

<span data-ttu-id="bccc1-171">Yayımlama, yayınlama, bağlama ve razor sayfası hala gerektirir gibi bazı işlemler vardır.</span><span class="sxs-lookup"><span data-stu-id="bccc1-171">There are some operations, like linking and razor page publishing that will still require publishing.</span></span>

## <a name="local-tools"></a><span data-ttu-id="bccc1-172">Yerel Araçlar</span><span class="sxs-lookup"><span data-stu-id="bccc1-172">Local tools</span></span>

<span data-ttu-id="bccc1-173">.NET core 3.0 yerel araçlar sunar.</span><span class="sxs-lookup"><span data-stu-id="bccc1-173">.NET Core 3.0 introduces local tools.</span></span> <span data-ttu-id="bccc1-174">Yerel Araçlar benzer [genel Araçları](../tools/global-tools.md) ancak disk üzerindeki belirli bir konum ile ilişkilidir.</span><span class="sxs-lookup"><span data-stu-id="bccc1-174">Local tools are similar to [global tools](../tools/global-tools.md) but are associated with a particular location on disk.</span></span> <span data-ttu-id="bccc1-175">Yerel araçları, küresel olarak kullanılabilir değildir ve NuGet paketleri olarak dağıtılır.</span><span class="sxs-lookup"><span data-stu-id="bccc1-175">Local tools aren't available globally and are distributed as NuGet packages.</span></span>

> [!WARNING]
> <span data-ttu-id="bccc1-176">Çalıştırma gibi .NET Core 3.0 Önizleme 1 ' yerel Araçlar çalıştıysanız `dotnet tool restore` veya `dotnet tool install`, yerel Araçlar önbellek klasörünü silin.</span><span class="sxs-lookup"><span data-stu-id="bccc1-176">If you tried local tools in .NET Core 3.0 Preview 1, such as running `dotnet tool restore` or `dotnet tool install`, delete the local tools cache folder.</span></span> <span data-ttu-id="bccc1-177">Aksi takdirde, yerel Araçlar üzerinde daha yeni bir sürüm çalışmaz.</span><span class="sxs-lookup"><span data-stu-id="bccc1-177">Otherwise, local tools won't work on any newer release.</span></span> <span data-ttu-id="bccc1-178">Bu klasör şu konumdadır:</span><span class="sxs-lookup"><span data-stu-id="bccc1-178">This folder is located at:</span></span>
>
> <span data-ttu-id="bccc1-179">MacOS, Linux: `rm -r $HOME/.dotnet/toolResolverCache`</span><span class="sxs-lookup"><span data-stu-id="bccc1-179">On macOS, Linux: `rm -r $HOME/.dotnet/toolResolverCache`</span></span>
>
> <span data-ttu-id="bccc1-180">Windows üzerinde: `rmdir /s %USERPROFILE%\.dotnet\toolResolverCache`</span><span class="sxs-lookup"><span data-stu-id="bccc1-180">On Windows: `rmdir /s %USERPROFILE%\.dotnet\toolResolverCache`</span></span>

<span data-ttu-id="bccc1-181">Yerel Araçlar kullanan bir bildirim dosyası adına `dotnet-tools.json` geçerli dizininizde.</span><span class="sxs-lookup"><span data-stu-id="bccc1-181">Local tools rely on a manifest file name `dotnet-tools.json` in your current directory.</span></span> <span data-ttu-id="bccc1-182">Bu bildirim dosyası, bu klasörü ve altındaki kullanılabilir olması için Araçlar tanımlar.</span><span class="sxs-lookup"><span data-stu-id="bccc1-182">This manifest file defines the tools to be available at that folder and below.</span></span> <span data-ttu-id="bccc1-183">Bildirim dosyası ile kodunuzu çalışır herkes geri yükleme ve böylelikle aynı araçlarını kullanın emin olmak için kodunuzla dağıtabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bccc1-183">You can distribute the manifest file with your code to ensure that anyone who works with your code can restore and use the same tools.</span></span>

<span data-ttu-id="bccc1-184">Hem genel hem de yerel araçları için çalışma zamanı'nın uyumlu bir sürümü gereklidir.</span><span class="sxs-lookup"><span data-stu-id="bccc1-184">For both global and local tools, a compatible version of the runtime is required.</span></span> <span data-ttu-id="bccc1-185">Birçok araç NuGet.org üzerinde şu anda .NET Core çalışma zamanı 2.1 hedefleyin.</span><span class="sxs-lookup"><span data-stu-id="bccc1-185">Many tools currently on NuGet.org target .NET Core Runtime 2.1.</span></span> <span data-ttu-id="bccc1-186">Bu araçlar genel veya yerel olarak yüklemek için yükleme yine [NET Core 2.1 çalışma zamanı](https://dotnet.microsoft.com/download/dotnet-core/2.1).</span><span class="sxs-lookup"><span data-stu-id="bccc1-186">To install these tools globally or locally, you would still need to install the [NET Core 2.1 Runtime](https://dotnet.microsoft.com/download/dotnet-core/2.1).</span></span>

## <a name="major-version-roll-forward"></a><span data-ttu-id="bccc1-187">Ana sürüm ileri sarma</span><span class="sxs-lookup"><span data-stu-id="bccc1-187">Major-version Roll Forward</span></span>

<span data-ttu-id="bccc1-188">.NET core 3.0, .NET Core için en son ana sürüm ileriye işlem gerçekleştirilebilmesi için uygulamanızı sağlayan bir Tercihli özellik sunmaktadır.</span><span class="sxs-lookup"><span data-stu-id="bccc1-188">.NET Core 3.0 introduces an opt-in feature that allows your app to roll forward to the latest major version of .NET Core.</span></span> <span data-ttu-id="bccc1-189">Ayrıca, yeni bir ayar ileri sarma uygulamanıza nasıl uygulanacağını denetlemek için eklendi.</span><span class="sxs-lookup"><span data-stu-id="bccc1-189">Additionally, a new setting has been added to control how roll forward is applied to your app.</span></span> <span data-ttu-id="bccc1-190">Bunu aşağıdaki yöntemlerle yapılandırılabilir:</span><span class="sxs-lookup"><span data-stu-id="bccc1-190">This can be configured in the following ways:</span></span>

- <span data-ttu-id="bccc1-191">Proje dosyası özelliği: `RollForward`</span><span class="sxs-lookup"><span data-stu-id="bccc1-191">Project file property: `RollForward`</span></span>
- <span data-ttu-id="bccc1-192">Çalışma zamanı yapılandırma dosyası özelliği: `rollForward`</span><span class="sxs-lookup"><span data-stu-id="bccc1-192">Runtime configuration file property: `rollForward`</span></span>
- <span data-ttu-id="bccc1-193">Ortam değişkeni: `DOTNET_ROLL_FORWARD`</span><span class="sxs-lookup"><span data-stu-id="bccc1-193">Environment variable: `DOTNET_ROLL_FORWARD`</span></span>
- <span data-ttu-id="bccc1-194">Komut satırı bağımsız değişkeni: `--roll-forward`</span><span class="sxs-lookup"><span data-stu-id="bccc1-194">Command-line argument: `--roll-forward`</span></span>

<span data-ttu-id="bccc1-195">Aşağıdaki değerlerden biri belirtilmelidir.</span><span class="sxs-lookup"><span data-stu-id="bccc1-195">One of the following values must be specified.</span></span> <span data-ttu-id="bccc1-196">Ayar atlanırsa **küçük** varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="bccc1-196">If the setting is omitted, **Minor** is the default.</span></span>

- <span data-ttu-id="bccc1-197">**LatestPatch**\\</span><span class="sxs-lookup"><span data-stu-id="bccc1-197">**LatestPatch**\\</span></span>
<span data-ttu-id="bccc1-198">İleriye işlem gerçekleştirilebilmesi için en yüksek düzeltme eki sürümü.</span><span class="sxs-lookup"><span data-stu-id="bccc1-198">Roll forward to the highest patch version.</span></span> <span data-ttu-id="bccc1-199">Bu, alt sürüm ileri sarma devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="bccc1-199">This disables minor version roll forward.</span></span>
- <span data-ttu-id="bccc1-200">**Küçük**\\</span><span class="sxs-lookup"><span data-stu-id="bccc1-200">**Minor**\\</span></span>
<span data-ttu-id="bccc1-201">En düşük daha alt sürümü için İleri istenen alt sürümü eksik sarabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bccc1-201">Roll forward to the lowest higher minor version, if requested minor version is missing.</span></span> <span data-ttu-id="bccc1-202">İstenen alt sürümü varsa, ardından **LatestPatch** İlkesi kullanılır.</span><span class="sxs-lookup"><span data-stu-id="bccc1-202">If the requested minor version is present, then the **LatestPatch** policy is used.</span></span>
- <span data-ttu-id="bccc1-203">**Büyük**\\</span><span class="sxs-lookup"><span data-stu-id="bccc1-203">**Major**\\</span></span>
<span data-ttu-id="bccc1-204">İstenen sürümle eksik olması durumunda yüksek ana sürüm en düşük ve en düşük alt sürüm İleri sarmanın.</span><span class="sxs-lookup"><span data-stu-id="bccc1-204">Roll forward to lowest higher major version, and lowest minor version, if requested major version is missing.</span></span> <span data-ttu-id="bccc1-205">İstenen ana sürüm varsa, ardından **küçük** İlkesi kullanılır.</span><span class="sxs-lookup"><span data-stu-id="bccc1-205">If the requested major version is present, then the **Minor** policy is used.</span></span>
- <span data-ttu-id="bccc1-206">**LatestMinor**\\</span><span class="sxs-lookup"><span data-stu-id="bccc1-206">**LatestMinor**\\</span></span>
<span data-ttu-id="bccc1-207">İstenen alt sürümü mevcut olsa bile, İleri en yüksek ikincil sürümüne geri almak.</span><span class="sxs-lookup"><span data-stu-id="bccc1-207">Roll forward to highest minor version, even if requested minor version is present.</span></span> <span data-ttu-id="bccc1-208">Bileşeni için barındırma senaryolarında yöneliktir.</span><span class="sxs-lookup"><span data-stu-id="bccc1-208">Intended for component hosting scenarios.</span></span>
- <span data-ttu-id="bccc1-209">**latestMajor**\\</span><span class="sxs-lookup"><span data-stu-id="bccc1-209">**LatestMajor**\\</span></span>
<span data-ttu-id="bccc1-210">İstenen ana olsa bile iletmek için en büyük ve en yüksek ikincil sürüm döndürün.</span><span class="sxs-lookup"><span data-stu-id="bccc1-210">Roll forward to highest major and highest minor version, even if requested major is present.</span></span> <span data-ttu-id="bccc1-211">Bileşeni için barındırma senaryolarında yöneliktir.</span><span class="sxs-lookup"><span data-stu-id="bccc1-211">Intended for component hosting scenarios.</span></span>
- <span data-ttu-id="bccc1-212">**Devre dışı bırak**\\</span><span class="sxs-lookup"><span data-stu-id="bccc1-212">**Disable**\\</span></span>
<span data-ttu-id="bccc1-213">İleri sarmanın yok.</span><span class="sxs-lookup"><span data-stu-id="bccc1-213">Don't roll forward.</span></span> <span data-ttu-id="bccc1-214">Yalnızca belirtilen sürüme bağlayın.</span><span class="sxs-lookup"><span data-stu-id="bccc1-214">Only bind to specified version.</span></span> <span data-ttu-id="bccc1-215">Bu ilke, en son düzeltme eklerini İleri sarmanın özelliği devre dışı bırakır çünkü genel kullanım için önerilmez.</span><span class="sxs-lookup"><span data-stu-id="bccc1-215">This policy isn't recommended for general use because it disables the ability to roll forward to the latest patches.</span></span> <span data-ttu-id="bccc1-216">Bu değer, yalnızca test etmek için önerilir.</span><span class="sxs-lookup"><span data-stu-id="bccc1-216">This value is only recommended for testing.</span></span>

<span data-ttu-id="bccc1-217">Yanında **devre dışı** ayarlama, tüm ayarlarını yüksek kullanılabilir bir düzeltme eki sürümü kullanır.</span><span class="sxs-lookup"><span data-stu-id="bccc1-217">Besides the **Disable** setting, all settings will use the highest available patch version.</span></span>

## <a name="windows-desktop"></a><span data-ttu-id="bccc1-218">Windows masaüstü</span><span class="sxs-lookup"><span data-stu-id="bccc1-218">Windows desktop</span></span>

<span data-ttu-id="bccc1-219">.NET core 3.0, Windows Presentation Foundation (WPF) ve Windows Forms kullanılarak Windows Masaüstü uygulamaları destekler.</span><span class="sxs-lookup"><span data-stu-id="bccc1-219">.NET Core 3.0 supports Windows desktop applications using Windows Presentation Foundation (WPF) and Windows Forms.</span></span> <span data-ttu-id="bccc1-220">Bu çerçeveler ile modern denetimleri ve Windows kullanıcı Arabirimi XAML kitaplığından (WinUI) Fluent stil kullanarak da destekler [XAML Adaları](/windows/uwp/xaml-platform/xaml-host-controls).</span><span class="sxs-lookup"><span data-stu-id="bccc1-220">These frameworks also support using modern controls and Fluent styling from the Windows UI XAML Library (WinUI) via [XAML islands](/windows/uwp/xaml-platform/xaml-host-controls).</span></span>

<span data-ttu-id="bccc1-221">Windows Masaüstü bileşen Windows parçasıdır .NET Core 3.0 SDK.</span><span class="sxs-lookup"><span data-stu-id="bccc1-221">The Windows Desktop component is part of the Windows .NET Core 3.0 SDK.</span></span>

<span data-ttu-id="bccc1-222">Şunlarla birlikte yeni bir Windows Forms ve WPF uygulaması oluşturabilirsiniz `dotnet` komutları:</span><span class="sxs-lookup"><span data-stu-id="bccc1-222">You can create a new WPF or Windows Forms app with the following `dotnet` commands:</span></span>

```console
dotnet new wpf
dotnet new winforms
```

<span data-ttu-id="bccc1-223">Visual Studio 2019 ekler **yeni proje** .NET Core 3.0, Windows Forms ve WPF şablonları.</span><span class="sxs-lookup"><span data-stu-id="bccc1-223">Visual Studio 2019 adds **New Project** templates for .NET Core 3.0 Windows Forms and WPF.</span></span>

<span data-ttu-id="bccc1-224">Mevcut bir .NET Framework uygulaması bağlantı noktası hakkında daha fazla bilgi için bkz. [bağlantı noktası WPF projeleri](../porting/wpf.md) ve [bağlantı noktası Windows Forms projeleri](../porting/winforms.md).</span><span class="sxs-lookup"><span data-stu-id="bccc1-224">For more information about how to port an existing .NET Framework application, see [Port WPF projects](../porting/wpf.md) and [Port Windows Forms projects](../porting/winforms.md).</span></span>

## <a name="com-callable-components---windows-desktop"></a><span data-ttu-id="bccc1-225">COM çağrılabilir bileşenleri - Windows Masaüstü</span><span class="sxs-lookup"><span data-stu-id="bccc1-225">COM-callable components - Windows Desktop</span></span>

<span data-ttu-id="bccc1-226">Windows üzerinde COM-yönetilen çağrılabilir bileşenler oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bccc1-226">On Windows, you can now create COM-callable managed components.</span></span> <span data-ttu-id="bccc1-227">Bu özellik, .NET Core ile COM Eklentisi modelleri kullanın ve .NET Framework ile eşlik sağlamak önemlidir.</span><span class="sxs-lookup"><span data-stu-id="bccc1-227">This capability is critical to use .NET Core with COM add-in models and also to provide parity with .NET Framework.</span></span>

<span data-ttu-id="bccc1-228">.NET Framework aksine burada *mscoree.dll* kullanılan COM sunucusu olarak yerel Başlatıcısı DLL'ye .NET Core ekleyeceksiniz *bin* , COM bileşeni oluşturma sırasında dizin.</span><span class="sxs-lookup"><span data-stu-id="bccc1-228">Unlike .NET Framework where the *mscoree.dll* was used as the COM server, .NET Core will add a native launcher dll to the *bin* directory when you build your COM component.</span></span>

<span data-ttu-id="bccc1-229">Bir COM bileşeni oluşturma ve bunu kullanma örneği için bkz: [COM tanıtım](https://github.com/dotnet/samples/tree/master/core/extensions/COMServerDemo).</span><span class="sxs-lookup"><span data-stu-id="bccc1-229">For an example of how to create a COM component and consume it, see the [COM Demo](https://github.com/dotnet/samples/tree/master/core/extensions/COMServerDemo).</span></span>

## <a name="msix-deployment---windows-desktop"></a><span data-ttu-id="bccc1-230">MSIX dağıtım - Windows Masaüstü</span><span class="sxs-lookup"><span data-stu-id="bccc1-230">MSIX Deployment - Windows Desktop</span></span>

<span data-ttu-id="bccc1-231">[MSIX](https://docs.microsoft.com/windows/msix/) yeni bir Windows uygulama paketi biçimi.</span><span class="sxs-lookup"><span data-stu-id="bccc1-231">[MSIX](https://docs.microsoft.com/windows/msix/) is a new Windows application package format.</span></span> <span data-ttu-id="bccc1-232">.NET Core 3.0 Windows 10 Masaüstü uygulamaları dağıtmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="bccc1-232">It can be used to deploy .NET Core 3.0 desktop applications to Windows 10.</span></span>

<span data-ttu-id="bccc1-233">[Windows uygulaması paketleme projesi](https://docs.microsoft.com/windows/uwp/porting/desktop-to-uwp-packaging-dot-net), Visual Studio 2019 bulunan MSIX paketlerle oluşturmanıza olanak tanır [müstakil](../deploying/index.md#self-contained-deployments-scd) .NET Core uygulamaları.</span><span class="sxs-lookup"><span data-stu-id="bccc1-233">The [Windows Application Packaging Project](https://docs.microsoft.com/windows/uwp/porting/desktop-to-uwp-packaging-dot-net), available in Visual Studio 2019, allows you to create MSIX packages with [self-contained](../deploying/index.md#self-contained-deployments-scd) .NET Core applications.</span></span>

<span data-ttu-id="bccc1-234">.NET Core proje dosyası içinde desteklenen çalışma zamanları belirtmelisiniz `<RuntimeIdentifiers>` özelliği:</span><span class="sxs-lookup"><span data-stu-id="bccc1-234">The .NET Core project file must specify the supported runtimes in the `<RuntimeIdentifiers>` property:</span></span>

```xml
<RuntimeIdentifiers>win-x86;win-x64</RuntimeIdentifiers>
```

## <a name="winforms-highdpi"></a><span data-ttu-id="bccc1-235">WinForms HighDPI</span><span class="sxs-lookup"><span data-stu-id="bccc1-235">WinForms HighDPI</span></span>

<span data-ttu-id="bccc1-236">.NET core Windows Forms uygulamaları, yüksek DPI moduyla ayarlayabilirsiniz <xref:System.Windows.Forms.Application.SetHighDpiMode(System.Windows.Forms.HighDpiMode)?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="bccc1-236">.NET Core Windows Forms applications can set High DPI mode with <xref:System.Windows.Forms.Application.SetHighDpiMode(System.Windows.Forms.HighDpiMode)?displayProperty=nameWithType>.</span></span> <span data-ttu-id="bccc1-237">`SetHighDpiMode` Yöntemini ayarlar karşılık gelen yüksek DPI modu ayarı gibi diğer yollarla ayarlanmadığı sürece `App.Manifest` veya P/Invoke önce `Application.Run`.</span><span class="sxs-lookup"><span data-stu-id="bccc1-237">The `SetHighDpiMode` method sets the corresponding High DPI mode unless the setting has been set by other means like `App.Manifest` or P/Invoke before `Application.Run`.</span></span>

<span data-ttu-id="bccc1-238">Olası `highDpiMode` değerler olarak ifade edilen <xref:System.Windows.Forms.HighDpiMode?displayProperty=nameWithType> enum şunlardır:</span><span class="sxs-lookup"><span data-stu-id="bccc1-238">The possible `highDpiMode` values, as expressed by the <xref:System.Windows.Forms.HighDpiMode?displayProperty=nameWithType> enum are:</span></span>

* `DpiUnaware`
* `SystemAware`
* `PerMonitor`
* `PerMonitorV2`
* `DpiUnawareGdiScaled`

<span data-ttu-id="bccc1-239">Yüksek DPI modları hakkında daha fazla bilgi için bkz. [Windows üzerinde yüksek DPI Masaüstü uygulama geliştirme](/windows/desktop/hidpi/high-dpi-desktop-application-development-on-windows).</span><span class="sxs-lookup"><span data-stu-id="bccc1-239">For more information about High DPI modes, see [High DPI Desktop Application Development on Windows](/windows/desktop/hidpi/high-dpi-desktop-application-development-on-windows).</span></span>

### <a name="ranges-and-indices"></a><span data-ttu-id="bccc1-240">Aralıkları ve dizinler</span><span class="sxs-lookup"><span data-stu-id="bccc1-240">Ranges and indices</span></span>

<span data-ttu-id="bccc1-241">Yeni <xref:System.Index?displayProperty=nameWithType> türü, dizin oluşturma işlemi için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="bccc1-241">The new <xref:System.Index?displayProperty=nameWithType> type can be used for indexing.</span></span> <span data-ttu-id="bccc1-242">Birinden oluşturabileceğiniz bir `int` baştan ya da öneki sayar `^` işleci (C#) sonundan sayar:</span><span class="sxs-lookup"><span data-stu-id="bccc1-242">You can create one from an `int` that counts from the beginning, or with a prefix `^` operator (C#) that counts from the end:</span></span>

```csharp
Index i1 = 3;  // number 3 from beginning
Index i2 = ^4; // number 4 from end
int[] a = { 0, 1, 2, 3, 4, 5, 6, 7, 8, 9 };
Console.WriteLine($"{a[i1]}, {a[i2]}"); // "3, 6"
```

<span data-ttu-id="bccc1-243">Ayrıca <xref:System.Range?displayProperty=nameWithType> oluşan iki tür `Index` bir başlangıç ve bitiş için bir değer ve ile yazılmış bir `x..y` aralık ifade (C#).</span><span class="sxs-lookup"><span data-stu-id="bccc1-243">There's also the <xref:System.Range?displayProperty=nameWithType> type, which consists of two `Index` values, one for the start and one for the end, and can be written with a `x..y` range expression (C#).</span></span> <span data-ttu-id="bccc1-244">Ardından ile dizinleyebilirsiniz bir `Range`, dilim oluşturur:</span><span class="sxs-lookup"><span data-stu-id="bccc1-244">You can then index with a `Range`, which produces a slice:</span></span>

```csharp
var slice = a[i1..i2]; // { 3, 4, 5 }
```

<span data-ttu-id="bccc1-245">Daha fazla bilgi için [aralıkları ve dizinlerini öğretici](../../csharp/tutorials/ranges-indexes.md).</span><span class="sxs-lookup"><span data-stu-id="bccc1-245">For more information, see the [ranges and indices tutorial](../../csharp/tutorials/ranges-indexes.md).</span></span>

### <a name="async-streams"></a><span data-ttu-id="bccc1-246">Zaman uyumsuz akışlar</span><span class="sxs-lookup"><span data-stu-id="bccc1-246">Async streams</span></span>

<span data-ttu-id="bccc1-247"><xref:System.Collections.Generic.IAsyncEnumerable%601> Türüdür, yeni bir zaman uyumsuz sürümü <xref:System.Collections.Generic.IEnumerable%601>.</span><span class="sxs-lookup"><span data-stu-id="bccc1-247">The <xref:System.Collections.Generic.IAsyncEnumerable%601> type is a new asynchronous version of <xref:System.Collections.Generic.IEnumerable%601>.</span></span> <span data-ttu-id="bccc1-248">Dil sayesinde `await foreach` üzerinden `IAsyncEnumerable<T>` öğeleri kullanma ve `yield return` öğeleri oluşturmak için onlara.</span><span class="sxs-lookup"><span data-stu-id="bccc1-248">The language lets you `await foreach` over `IAsyncEnumerable<T>` to consume their elements, and use `yield return` to them to produce elements.</span></span>

<span data-ttu-id="bccc1-249">Aşağıdaki örnek, hem üretim hem de zaman uyumsuz akışlar kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="bccc1-249">The following example demonstrates both production and consumption of async streams.</span></span> <span data-ttu-id="bccc1-250">`foreach` Deyimi, async ve kendisini kullanan `yield return` arayanlar için zaman uyumsuz bir akış oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="bccc1-250">The `foreach` statement is async and itself uses `yield return` to produce an async stream for callers.</span></span> <span data-ttu-id="bccc1-251">Bu düzen (kullanarak `yield return`) zaman uyumsuz akışlar oluşturmayı için önerilen modelidir.</span><span class="sxs-lookup"><span data-stu-id="bccc1-251">This pattern (using `yield return`) is the recommended model for producing async streams.</span></span>

```csharp
async IAsyncEnumerable<int> GetBigResultsAsync()
{
    await foreach (var result in GetResultsAsync())
    {
        if (result > 20) yield return result; 
    }
}
```

<span data-ttu-id="bccc1-252">İmkanına yanı sıra `await foreach`, zaman uyumsuz yineleyiciler, örneğin, döndüren bir yineleyicinin oluşturabilirsiniz bir `IAsyncEnumerable/IAsyncEnumerator` her ikisini yapabilirsiniz `await` ve `yield` içinde.</span><span class="sxs-lookup"><span data-stu-id="bccc1-252">In addition to being able to `await foreach`, you can also create async iterators, for example, an iterator that returns an `IAsyncEnumerable/IAsyncEnumerator` that you can both `await` and `yield` in.</span></span> <span data-ttu-id="bccc1-253">Çıkarılması gereken nesneler için kullanabileceğiniz `IAsyncDisposable`, çeşitli BCL türleri uygulayan, gibi `Stream` ve `Timer`.</span><span class="sxs-lookup"><span data-stu-id="bccc1-253">For objects that need to be disposed, you can use `IAsyncDisposable`, which various BCL types implement, such as `Stream` and `Timer`.</span></span>

<span data-ttu-id="bccc1-254">Daha fazla bilgi için [zaman uyumsuz akışlar öğretici](../../csharp/tutorials/generate-consume-asynchronous-stream.md).</span><span class="sxs-lookup"><span data-stu-id="bccc1-254">For more information, see the [async streams tutorial](../../csharp/tutorials/generate-consume-asynchronous-stream.md).</span></span>

## <a name="ieee-floating-point-improvements"></a><span data-ttu-id="bccc1-255">IEEE kayan nokta geliştirmeleri</span><span class="sxs-lookup"><span data-stu-id="bccc1-255">IEEE Floating-point improvements</span></span>

<span data-ttu-id="bccc1-256">Kayan nokta API'leri güncelleştiriliyor uymak için [IEEE 754-2008 düzeltme](https://en.wikipedia.org/wiki/IEEE_754-2008_revision).</span><span class="sxs-lookup"><span data-stu-id="bccc1-256">Floating point APIs are being updated to comply with [IEEE 754-2008 revision](https://en.wikipedia.org/wiki/IEEE_754-2008_revision).</span></span> <span data-ttu-id="bccc1-257">Tüm kullanıma sunmak için bu değişikliklerin amacı olan **gerekli** işlemleri ve davranışsal IEEE belirtimi ile uyumlu olduğunuzdan emin olun. Kayan nokta iyileştirmeleri hakkında daha fazla bilgi için bkz. [Floating-Point ayrıştırma ve biçimlendirme geliştirmeleri .NET Core 3. 0'ı](https://devblogs.microsoft.com/dotnet/floating-point-parsing-and-formatting-improvements-in-net-core-3-0/) blog gönderisi.</span><span class="sxs-lookup"><span data-stu-id="bccc1-257">The goal of these changes is to expose all **required** operations and ensure that they're behaviorally compliant with the IEEE spec. For more information about floating-point improvements, see the [Floating-Point Parsing and Formatting improvements in .NET Core 3.0](https://devblogs.microsoft.com/dotnet/floating-point-parsing-and-formatting-improvements-in-net-core-3-0/) blog post.</span></span>

<span data-ttu-id="bccc1-258">Ayrıştırma ve biçimlendirme düzeltmeleri içerir:</span><span class="sxs-lookup"><span data-stu-id="bccc1-258">Parsing and formatting fixes include:</span></span>

* <span data-ttu-id="bccc1-259">Doğru ayrıştırma ve herhangi bir uzunluktaki girişleri yuvarlar.</span><span class="sxs-lookup"><span data-stu-id="bccc1-259">Correctly parse and round inputs of any length.</span></span>
* <span data-ttu-id="bccc1-260">Doğru ayrıştırma ve negatif sıfır biçimlendirin.</span><span class="sxs-lookup"><span data-stu-id="bccc1-260">Correctly parse and format negative zero.</span></span>
* <span data-ttu-id="bccc1-261">Düzgün ayrıştırılamadı `Infinity` ve `NaN` büyük küçük harf duyarsız bir denetimi yapmak ve isteğe bağlı bir önceki izin vererek `+` uygunsa.</span><span class="sxs-lookup"><span data-stu-id="bccc1-261">Correctly parse `Infinity` and `NaN` by doing a case-insensitive check and allowing an optional preceding `+` where applicable.</span></span>

<span data-ttu-id="bccc1-262">Yeni <xref:System.Math?displayProperty=nameWithType> API'leri içerir:</span><span class="sxs-lookup"><span data-stu-id="bccc1-262">New <xref:System.Math?displayProperty=nameWithType> APIs include:</span></span>

* <span data-ttu-id="bccc1-263"><xref:System.Math.BitIncrement(System.Double)> ve <xref:System.Math.BitDecrement(System.Double)>\\</span><span class="sxs-lookup"><span data-stu-id="bccc1-263"><xref:System.Math.BitIncrement(System.Double)> and <xref:System.Math.BitDecrement(System.Double)>\\</span></span>
<span data-ttu-id="bccc1-264">Karşılık gelen `nextUp` ve `nextDown` IEEE operations.</span><span class="sxs-lookup"><span data-stu-id="bccc1-264">Corresponds to the `nextUp` and `nextDown` IEEE operations.</span></span> <span data-ttu-id="bccc1-265">Karşılaştıran en küçük kayan noktalı sayı (sırasıyla) giriş'den küçük veya büyük döndürürler.</span><span class="sxs-lookup"><span data-stu-id="bccc1-265">They return the smallest floating-point number that compares greater or lesser than the input (respectively).</span></span> <span data-ttu-id="bccc1-266">Örneğin, `Math.BitIncrement(0.0)` döndürecekti `double.Epsilon`.</span><span class="sxs-lookup"><span data-stu-id="bccc1-266">For example, `Math.BitIncrement(0.0)` would return `double.Epsilon`.</span></span>

* <span data-ttu-id="bccc1-267"><xref:System.Math.MaxMagnitude(System.Double,System.Double)> ve <xref:System.Math.MinMagnitude(System.Double,System.Double)>\\</span><span class="sxs-lookup"><span data-stu-id="bccc1-267"><xref:System.Math.MaxMagnitude(System.Double,System.Double)> and <xref:System.Math.MinMagnitude(System.Double,System.Double)>\\</span></span>
<span data-ttu-id="bccc1-268">Karşılık gelen `maxNumMag` ve `minNumMag` IEEE işlemleri, bunlar döndürür (sırasıyla) büyük ya da büyüklük açısından iki girişe daha düşük olan değer.</span><span class="sxs-lookup"><span data-stu-id="bccc1-268">Corresponds to the `maxNumMag` and `minNumMag` IEEE operations, they return the value that is greater or lesser in magnitude of the two inputs (respectively).</span></span> <span data-ttu-id="bccc1-269">Örneğin, `Math.MaxMagnitude(2.0, -3.0)` döndürecekti `-3.0`.</span><span class="sxs-lookup"><span data-stu-id="bccc1-269">For example, `Math.MaxMagnitude(2.0, -3.0)` would return `-3.0`.</span></span>

* <xref:System.Math.ILogB(System.Double)>\
<span data-ttu-id="bccc1-270">Karşılık gelen `logB` bir tamsayı değeri döndüren IEEE işlemi, giriş parametresinin tamsayı 2 tabanında günlük döndürür.</span><span class="sxs-lookup"><span data-stu-id="bccc1-270">Corresponds to the `logB` IEEE operation that returns an integral value, it returns the integral base-2 log of the input parameter.</span></span> <span data-ttu-id="bccc1-271">Bu yöntem etkili bir şekilde aynıdır `floor(log2(x))`, ancak en az yuvarlama hatası işler bitti.</span><span class="sxs-lookup"><span data-stu-id="bccc1-271">This method is effectively the same as `floor(log2(x))`, but done with minimal rounding error.</span></span>

* <xref:System.Math.ScaleB(System.Double,System.Int32)>\
<span data-ttu-id="bccc1-272">Karşılık gelen `scaleB` bir tamsayı değeri alan IEEE işlemi döndürür etkili bir şekilde `x * pow(2, n)`, yuvarlama en az bir hata ile tamamlandı ancak.</span><span class="sxs-lookup"><span data-stu-id="bccc1-272">Corresponds to the `scaleB` IEEE operation that takes an integral value, it returns effectively `x * pow(2, n)`, but is done with minimal rounding error.</span></span>

* <xref:System.Math.Log2(System.Double)>\
<span data-ttu-id="bccc1-273">Karşılık gelen `log2` IEEE işlemi 2 tabanlı logaritmasını döndürür.</span><span class="sxs-lookup"><span data-stu-id="bccc1-273">Corresponds to the `log2` IEEE operation, it returns the base-2 logarithm.</span></span> <span data-ttu-id="bccc1-274">Yuvarlama hata en aza indirir.</span><span class="sxs-lookup"><span data-stu-id="bccc1-274">It minimizes rounding error.</span></span>

* <xref:System.Math.FusedMultiplyAdd(System.Double,System.Double,System.Double)>\
<span data-ttu-id="bccc1-275">Karşılık gelen `fma` IEEE işlem gerçekleştirdiği bir çarpım Çarp.</span><span class="sxs-lookup"><span data-stu-id="bccc1-275">Corresponds to the `fma` IEEE operation, it performs a fused multiply add.</span></span> <span data-ttu-id="bccc1-276">Diğer bir deyişle, mevcut `(x * y) + z` tek bir işlem olarak, var-tarafından yuvarlama hata en aza indirir.</span><span class="sxs-lookup"><span data-stu-id="bccc1-276">That is, it does `(x * y) + z` as a single operation, there-by minimizing the rounding error.</span></span> <span data-ttu-id="bccc1-277">Örnek verilebilir `FusedMultiplyAdd(1e308, 2.0, -1e308)` döndüren `1e308`.</span><span class="sxs-lookup"><span data-stu-id="bccc1-277">An example would be `FusedMultiplyAdd(1e308, 2.0, -1e308)` which returns `1e308`.</span></span> <span data-ttu-id="bccc1-278">Normal `(1e308 * 2.0) - 1e308` döndürür `double.PositiveInfinity`.</span><span class="sxs-lookup"><span data-stu-id="bccc1-278">The regular `(1e308 * 2.0) - 1e308` returns `double.PositiveInfinity`.</span></span>

* <xref:System.Math.CopySign(System.Double,System.Double)>\
<span data-ttu-id="bccc1-279">Karşılık gelen `copySign` IEEE işlemi değerini döndürür `x`, ancak işaretini `y`.</span><span class="sxs-lookup"><span data-stu-id="bccc1-279">Corresponds to the `copySign` IEEE operation, it returns the value of `x`, but with the sign of `y`.</span></span>

## <a name="fast-built-in-json-support"></a><span data-ttu-id="bccc1-280">Hızlı yerleşik JSON desteği</span><span class="sxs-lookup"><span data-stu-id="bccc1-280">Fast built-in JSON support</span></span>

<span data-ttu-id="bccc1-281">.NET kullanıcıları büyük ölçüde üzerinde yararlandı [ **Json.NET** ](https://www.newtonsoft.com/json) ve iyi seçenekleri olmaya devam diğer popüler JSON kitaplıkları.</span><span class="sxs-lookup"><span data-stu-id="bccc1-281">.NET users have largely relied on [**Json.NET**](https://www.newtonsoft.com/json) and other popular JSON libraries, which continue to be good choices.</span></span> <span data-ttu-id="bccc1-282">**Json.NET** UTF-16 başlık altında olduğu temel veri türü, .NET dizeleri kullanır.</span><span class="sxs-lookup"><span data-stu-id="bccc1-282">**Json.NET** uses .NET strings as its base datatype, which is UTF-16 under the hood.</span></span>

<span data-ttu-id="bccc1-283">Yeni yerleşik JSON desteği, yüksek performanslı, düşük ayırma ve temel `Span<byte>`.</span><span class="sxs-lookup"><span data-stu-id="bccc1-283">The new built-in JSON support is high-performance, low allocation, and based on `Span<byte>`.</span></span> <span data-ttu-id="bccc1-284">.NET Core 3.0 için yeni ana JSON ile ilgili üç eklenmiştir <xref:System.Text.Json?displayProperty=nameWithType> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="bccc1-284">Three new main JSON-related types have been added to .NET Core 3.0 the <xref:System.Text.Json?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="bccc1-285">Bu tür olmayan *henüz* düz eski CLR nesnesi (POCO) serileştirme ve seri durumundan çıkarma destekler.</span><span class="sxs-lookup"><span data-stu-id="bccc1-285">These types don't *yet* support plain old CLR object (POCO) serialization and deserialization.</span></span>

### <a name="utf8jsonreader"></a><span data-ttu-id="bccc1-286">Utf8JsonReader</span><span class="sxs-lookup"><span data-stu-id="bccc1-286">Utf8JsonReader</span></span>

<span data-ttu-id="bccc1-287"><xref:System.Text.Json.Utf8JsonReader?displayProperty=nameWithType> yüksek performanslı, düşük ayırma, yalnızca iletme Okuyucu için UTF-8 kodlamalı JSON metin okuma, bir `ReadOnlySpan<byte>`.</span><span class="sxs-lookup"><span data-stu-id="bccc1-287"><xref:System.Text.Json.Utf8JsonReader?displayProperty=nameWithType> is a high-performance, low allocation, forward-only reader for UTF-8 encoded JSON text, read from a `ReadOnlySpan<byte>`.</span></span> <span data-ttu-id="bccc1-288">`Utf8JsonReader` Özel çözümleyiciler ve deserializers oluşturmak için kullanılan bir temel, alt düzey türüdür.</span><span class="sxs-lookup"><span data-stu-id="bccc1-288">The `Utf8JsonReader` is a foundational, low-level type, that can be used to build custom parsers and deserializers.</span></span> <span data-ttu-id="bccc1-289">Kullanarak yeni bir JSON yükü okuma `Utf8JsonReader` reader'ı kullanarak daha hızlı bir şekilde x 2 **Json.NET**.</span><span class="sxs-lookup"><span data-stu-id="bccc1-289">Reading through a JSON payload using the new `Utf8JsonReader` is 2x faster than using the reader from **Json.NET**.</span></span> <span data-ttu-id="bccc1-290">JSON belirteçleri (UTF-16) dizeler olarak actualize gerekene kadar tahsis etmez.</span><span class="sxs-lookup"><span data-stu-id="bccc1-290">It doesn't allocate until you need to actualize JSON tokens as (UTF-16) strings.</span></span>

<span data-ttu-id="bccc1-291">İşte bir örnek üzerinden okuma [ **launch.json** ](https://github.com/dotnet/samples/blob/master/snippets/core/whats-new/whats-new-in-30/cs/launch.json) Visual Studio Code tarafından oluşturulan dosya:</span><span class="sxs-lookup"><span data-stu-id="bccc1-291">Here is an example of reading through the [**launch.json**](https://github.com/dotnet/samples/blob/master/snippets/core/whats-new/whats-new-in-30/cs/launch.json) file created by Visual Studio Code:</span></span>

[!CODE-csharp[Utf8JsonReader](~/samples/snippets/core/whats-new/whats-new-in-30/cs/program.cs#PrintJson)]

[!CODE-csharp[Utf8JsonReader](~/samples/snippets/core/whats-new/whats-new-in-30/cs/program.cs#PrintJsonCall)]

### <a name="utf8jsonwriter"></a><span data-ttu-id="bccc1-292">Utf8JsonWriter</span><span class="sxs-lookup"><span data-stu-id="bccc1-292">Utf8JsonWriter</span></span>

<span data-ttu-id="bccc1-293"><xref:System.Text.Json.Utf8JsonWriter?displayProperty=nameWithType> bir yüksek performanslı, genel .NET türleri JSON metni yalnızca iletme UTF-8 olarak kodlanmış biçimde yazmak ister önbelleğe alınmamış, sağlar `String`, `Int32`, ve `DateTime`.</span><span class="sxs-lookup"><span data-stu-id="bccc1-293"><xref:System.Text.Json.Utf8JsonWriter?displayProperty=nameWithType> provides a high-performance, non-cached, forward-only way to write UTF-8 encoded JSON text from common .NET types like `String`, `Int32`, and `DateTime`.</span></span> <span data-ttu-id="bccc1-294">Okuyucu gibi yazıcı özel seri hale getiricileri genişletme oluşturmak için kullanılan bir temel, alt düzey türüdür.</span><span class="sxs-lookup"><span data-stu-id="bccc1-294">Like the reader, the writer is a foundational, low-level type, that can be used to build custom serializers.</span></span> <span data-ttu-id="bccc1-295">Kullanarak yeni bir JSON yükünü yazmayı `Utf8JsonWriter` yazıcıdan kullanarak daha hızlı % 30-80'idir **Json.NET** ve tahsis etmez.</span><span class="sxs-lookup"><span data-stu-id="bccc1-295">Writing a JSON payload using the new `Utf8JsonWriter` is 30-80% faster than using the writer from **Json.NET** and doesn't allocate.</span></span>

### <a name="jsondocument"></a><span data-ttu-id="bccc1-296">JsonDocument</span><span class="sxs-lookup"><span data-stu-id="bccc1-296">JsonDocument</span></span>

<span data-ttu-id="bccc1-297"><xref:System.Text.Json.JsonDocument?displayProperty=nameWithType> üst kısmındaki yerleşik `Utf8JsonReader`.</span><span class="sxs-lookup"><span data-stu-id="bccc1-297"><xref:System.Text.Json.JsonDocument?displayProperty=nameWithType> is built on top of the `Utf8JsonReader`.</span></span> <span data-ttu-id="bccc1-298">`JsonDocument` JSON verilerini ayrıştırma ve bir salt okunur belge nesne modeli (DOM), derleme olanağı, rastgele erişim ve numaralandırma desteklemek için sorgulanabilir sağlar.</span><span class="sxs-lookup"><span data-stu-id="bccc1-298">The `JsonDocument` provides the ability to parse JSON data and build a read-only Document Object Model (DOM) that can be queried to support random access and enumeration.</span></span> <span data-ttu-id="bccc1-299">Verileri oluşturan JSON öğeleri aracılığıyla erişilebilir <xref:System.Text.Json.JsonElement> tarafından sunulan tür `JsonDocument` adlı bir özellik olarak `RootElement`.</span><span class="sxs-lookup"><span data-stu-id="bccc1-299">The JSON elements that compose the data can be accessed via the <xref:System.Text.Json.JsonElement> type that is exposed by the `JsonDocument` as a property called `RootElement`.</span></span> <span data-ttu-id="bccc1-300">`JsonElement` Ortak .NET türlerine JSON metnine dönüştürmek için API'leri ile birlikte JSON dizi ve nesne numaralandırıcıları içerir.</span><span class="sxs-lookup"><span data-stu-id="bccc1-300">The `JsonElement` contains the JSON array and object enumerators along with APIs to convert JSON text to common .NET types.</span></span> <span data-ttu-id="bccc1-301">Tipik bir JSON yükü ayrıştırma ve tüm kullanarak üyelerine erişilmesi `JsonDocument` 2-3 x daha hızlı bir şekilde **Json.NET** makul boyutlu veriler için biraz ayırmaları ile (yani, < 1 MB).</span><span class="sxs-lookup"><span data-stu-id="bccc1-301">Parsing a typical JSON payload and accessing all its members using the `JsonDocument` is 2-3x faster than **Json.NET** with little allocations for data that is reasonably sized (that is, < 1 MB).</span></span>

<span data-ttu-id="bccc1-302">İşte bir örnek kullanımı `JsonDocument` ve `JsonElement` başlangıç noktası olarak kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="bccc1-302">Here is a sample usage of the `JsonDocument` and `JsonElement` that can be used as a starting point:</span></span>

<span data-ttu-id="bccc1-303">İşte bir C# 8.0 örneği aracılığıyla okuma [ **launch.json** ](https://github.com/dotnet/samples/blob/master/snippets/core/whats-new/whats-new-in-30/cs/launch.json) Visual Studio Code tarafından oluşturulan dosya:</span><span class="sxs-lookup"><span data-stu-id="bccc1-303">Here is a C# 8.0 example of reading through the [**launch.json**](https://github.com/dotnet/samples/blob/master/snippets/core/whats-new/whats-new-in-30/cs/launch.json) file created by Visual Studio Code:</span></span>

[!CODE-csharp[JsonDocument](~/samples/snippets/core/whats-new/whats-new-in-30/cs/program.cs#ReadJson)]

[!CODE-csharp[JsonDocument](~/samples/snippets/core/whats-new/whats-new-in-30/cs/program.cs#ReadJsonCall)]

### <a name="jsonserializer"></a><span data-ttu-id="bccc1-304">JsonSerializer</span><span class="sxs-lookup"><span data-stu-id="bccc1-304">JsonSerializer</span></span>

<span data-ttu-id="bccc1-305"><xref:System.Text.Json.Serialization.JsonSerializer?displayProperty=nameWithType> üst kısmındaki yerleşik <xref:System.Text.Json.Utf8JsonReader> ve <xref:System.Text.Json.Utf8JsonWriter> JSON belgeleri ve parçaları çalışırken hızlı düşük bellek serileştirme seçeneği sağlamak.</span><span class="sxs-lookup"><span data-stu-id="bccc1-305"><xref:System.Text.Json.Serialization.JsonSerializer?displayProperty=nameWithType> is built on top of <xref:System.Text.Json.Utf8JsonReader> and <xref:System.Text.Json.Utf8JsonWriter> to provide a fast low-memory serialization option when working with JSON documents and fragments.</span></span>

<span data-ttu-id="bccc1-306">İNCELEME: https://github.com/dotnet/corefx/blob/master/src/System.Text.Json/docs/SerializerProgrammingModel.md bu makaleye bağlantı örneği</span><span class="sxs-lookup"><span data-stu-id="bccc1-306">EXAMINE: https://github.com/dotnet/corefx/blob/master/src/System.Text.Json/docs/SerializerProgrammingModel.md for an example to port to this article</span></span>

<span data-ttu-id="bccc1-307">Bir nesne json'a serileştirilirken bir örnek aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="bccc1-307">Here is an example of serializing an object to JSON:</span></span>

[!CODE-csharp[JsonSerializer](~/samples/snippets/core/whats-new/whats-new-in-30/cs/JSON.cs#JsonSerialize)]

<span data-ttu-id="bccc1-308">Bir nesne için bir JSON dizesini seri durumdan çıkarılırken bir örnek aşağıda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="bccc1-308">Here is an example of deserializing a JSON string to an object.</span></span> <span data-ttu-id="bccc1-309">Önceki örnek tarafından oluşturulanla JSON dizesi kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="bccc1-309">You can use the JSON string produced by the previous example:</span></span>

[!CODE-csharp[JsonDeserializer](~/samples/snippets/core/whats-new/whats-new-in-30/cs/JSON.cs#JsonDeserialize)]

## <a name="interop-improvements"></a><span data-ttu-id="bccc1-310">Birlikte çalışma geliştirmeleri</span><span class="sxs-lookup"><span data-stu-id="bccc1-310">Interop improvements</span></span>

<span data-ttu-id="bccc1-311">.NET core 3.0 yerel API Interop artırır.</span><span class="sxs-lookup"><span data-stu-id="bccc1-311">.NET Core 3.0 improves native API interop.</span></span>

### <a name="type-nativelibrary"></a><span data-ttu-id="bccc1-312">Tür: NativeLibrary</span><span class="sxs-lookup"><span data-stu-id="bccc1-312">Type: NativeLibrary</span></span>

<span data-ttu-id="bccc1-313"><xref:System.Runtime.InteropServices.NativeLibrary?displayProperty=nameWithType> (.NET Core P/Invoke olarak aynı yük mantığı kullanarak) yerel bir kitaplığı yüklemeye yönelik bir kapsülleme sağlar ve ilgili yardımcı işlevleri gibi sağlayarak `getSymbol`.</span><span class="sxs-lookup"><span data-stu-id="bccc1-313"><xref:System.Runtime.InteropServices.NativeLibrary?displayProperty=nameWithType> provides an encapsulation for loading a native library (using the same load logic as .NET Core P/Invoke) and providing the relevant helper functions such as `getSymbol`.</span></span> <span data-ttu-id="bccc1-314">Kod örneği için bkz: [DLLMap tanıtım](https://github.com/dotnet/samples/tree/master/core/extensions/AppWithPlugin).</span><span class="sxs-lookup"><span data-stu-id="bccc1-314">For a code example, see the [DLLMap Demo](https://github.com/dotnet/samples/tree/master/core/extensions/AppWithPlugin).</span></span>

### <a name="windows-native-interop"></a><span data-ttu-id="bccc1-315">Windows yerel birlikte çalışabilirliği</span><span class="sxs-lookup"><span data-stu-id="bccc1-315">Windows Native Interop</span></span>

<span data-ttu-id="bccc1-316">Windows formunda düz C API'leri, COM ve WinRT zengin yerel bir API sunar.</span><span class="sxs-lookup"><span data-stu-id="bccc1-316">Windows offers a rich native API in the form of flat C APIs, COM, and WinRT.</span></span> <span data-ttu-id="bccc1-317">.NET Core destekler while **P/Invoke**, .NET Core 3.0 yeteneği ekler **COM API işlemi** ve **WinRT API'lar etkinleştirme**.</span><span class="sxs-lookup"><span data-stu-id="bccc1-317">While .NET Core supports **P/Invoke**, .NET Core 3.0 adds the ability to **CoCreate COM APIs** and **Activate WinRT APIs**.</span></span> <span data-ttu-id="bccc1-318">Kod örneği için bkz: [Excel Demo](https://github.com/dotnet/samples/tree/master/core/extensions/ExcelDemo).</span><span class="sxs-lookup"><span data-stu-id="bccc1-318">For a code example, see the [Excel Demo](https://github.com/dotnet/samples/tree/master/core/extensions/ExcelDemo).</span></span>

## <a name="http2-support"></a><span data-ttu-id="bccc1-319">HTTP/2 desteği</span><span class="sxs-lookup"><span data-stu-id="bccc1-319">HTTP/2 support</span></span>

<span data-ttu-id="bccc1-320"><xref:System.Net.Http.HttpClient?displayProperty=nameWithType> HTTP/2 protokolüne türünü destekler.</span><span class="sxs-lookup"><span data-stu-id="bccc1-320">The <xref:System.Net.Http.HttpClient?displayProperty=nameWithType> type supports the HTTP/2 protocol.</span></span> <span data-ttu-id="bccc1-321">Destek şu anda devre dışıdır, ancak çağırarak açılabilir `AppContext.SetSwitch("System.Net.Http.SocketsHttpHandler.Http2Support", true);` kullanmadan önce <xref:System.Net.Http.HttpClient>.</span><span class="sxs-lookup"><span data-stu-id="bccc1-321">Support is currently disabled but can be turned on by calling `AppContext.SetSwitch("System.Net.Http.SocketsHttpHandler.Http2Support", true);` before you use <xref:System.Net.Http.HttpClient>.</span></span> <span data-ttu-id="bccc1-322">HTTP/2 desteği ayarlayarak da etkinleştirebilirsiniz `DOTNET_SYSTEM_NET_HTTP_SOCKETSHTTPHANDLER_HTTP2SUPPORT` ortam değişkenine `true` uygulamanızı çalıştırmadan önce.</span><span class="sxs-lookup"><span data-stu-id="bccc1-322">You can also enable HTTP/2 support by setting the `DOTNET_SYSTEM_NET_HTTP_SOCKETSHTTPHANDLER_HTTP2SUPPORT` environment variable to `true` before you run your app.</span></span>

<span data-ttu-id="bccc1-323">HTTP/2 etkinleştirilirse, HTTP protokolü sürümünü TLS/ALPN gerçekleştirilir ve sunucu kullanılacağını seçerse, yalnızca HTTP/2 kullanılır.</span><span class="sxs-lookup"><span data-stu-id="bccc1-323">If HTTP/2 is enabled, the HTTP protocol version will be negotiated via TLS/ALPN, and HTTP/2 will only be used if the server selects to use it.</span></span>

## <a name="tls-13--openssl-111-on-linux"></a><span data-ttu-id="bccc1-324">TLS 1.3 & Linux'ta OpenSSL 1.1.1</span><span class="sxs-lookup"><span data-stu-id="bccc1-324">TLS 1.3 & OpenSSL 1.1.1 on Linux</span></span>

<span data-ttu-id="bccc1-325">.NET core artık avantajlarından yararlanır [OpenSSL 1.1.1 TLS 1.3 desteği](https://www.openssl.org/blog/blog/2018/09/11/release111/), verilen ortamda kullanılabilir olduğunda.</span><span class="sxs-lookup"><span data-stu-id="bccc1-325">.NET Core now takes advantage of [TLS 1.3 support in OpenSSL 1.1.1](https://www.openssl.org/blog/blog/2018/09/11/release111/), when it's available in a given environment.</span></span> <span data-ttu-id="bccc1-326">1.3 TLS ile:</span><span class="sxs-lookup"><span data-stu-id="bccc1-326">With TLS 1.3:</span></span>

* <span data-ttu-id="bccc1-327">Defa bağlantı azaltılmış gidiş dönüş istemci ve sunucu arasında gerekli ile geliştirildi.</span><span class="sxs-lookup"><span data-stu-id="bccc1-327">Connection times are improved with reduced round trips required between the client and server.</span></span>
* <span data-ttu-id="bccc1-328">Geliştirilmiş güvenlik çeşitli eski ve güvenli şifreleme algoritmaları kaldırılmasını nedeniyle.</span><span class="sxs-lookup"><span data-stu-id="bccc1-328">Improved security because of the removal of various obsolete and insecure cryptographic algorithms.</span></span>

<span data-ttu-id="bccc1-329">Kullanılabilir olduğunda, .NET Core 3.0 kullanan **OpenSSL 1.1.1**, **OpenSSL 1.1.0**, veya **OpenSSL 1.0.2** bir Linux sisteminde.</span><span class="sxs-lookup"><span data-stu-id="bccc1-329">When available, .NET Core 3.0 uses **OpenSSL 1.1.1**, **OpenSSL 1.1.0**, or **OpenSSL 1.0.2** on a Linux system.</span></span> <span data-ttu-id="bccc1-330">Zaman **OpenSSL 1.1.1** kullanılabilir, her ikisi de <xref:System.Net.Security.SslStream?displayProperty=nameWithType> ve <xref:System.Net.Http.HttpClient?displayProperty=nameWithType> türleri kullanırsınız **TLS 1.3** (istemci ve sunucu desteği varsayılarak **TLS 1.3**).</span><span class="sxs-lookup"><span data-stu-id="bccc1-330">When **OpenSSL 1.1.1** is available, both <xref:System.Net.Security.SslStream?displayProperty=nameWithType> and <xref:System.Net.Http.HttpClient?displayProperty=nameWithType> types will use **TLS 1.3** (assuming both the client and server support **TLS 1.3**).</span></span>

>[!IMPORTANT]
><span data-ttu-id="bccc1-331">Windows ve macOS henüz desteklemediği **TLS 1.3**.</span><span class="sxs-lookup"><span data-stu-id="bccc1-331">Windows and macOS do not yet support **TLS 1.3**.</span></span> <span data-ttu-id="bccc1-332">.NET core 3.0 destekleyeceği **TLS 1.3** desteği kullanılabilir olduğunda bu işletim sistemlerinde.</span><span class="sxs-lookup"><span data-stu-id="bccc1-332">.NET Core 3.0 will support **TLS 1.3** on these operating systems when support becomes available.</span></span>

<span data-ttu-id="bccc1-333">Aşağıdaki C# 8.0 örnek gösterir Ubuntu bağlanma 18.10 üzerinde .NET Core 3.0 <https://www.cloudflare.com>:</span><span class="sxs-lookup"><span data-stu-id="bccc1-333">The following C# 8.0 example demonstrates .NET Core 3.0 on Ubuntu 18.10 connecting to <https://www.cloudflare.com>:</span></span>

[!CODE-csharp[TLSExample](~/samples/snippets/core/whats-new/whats-new-in-30/cs/TLS.cs#TLS)]

## <a name="cryptography-ciphers"></a><span data-ttu-id="bccc1-334">Şifreleme şifrelemeleri</span><span class="sxs-lookup"><span data-stu-id="bccc1-334">Cryptography ciphers</span></span>

<span data-ttu-id="bccc1-335">.NET 3.0 için destek ekler **AES GCM** ve **AES-CCM** ile uygulanan şifrelemeleri, <xref:System.Security.Cryptography.AesGcm?displayProperty=nameWithType> ve <xref:System.Security.Cryptography.AesCcm?displayProperty=nameWithType> sırasıyla.</span><span class="sxs-lookup"><span data-stu-id="bccc1-335">.NET 3.0 adds support for **AES-GCM** and **AES-CCM** ciphers, implemented with <xref:System.Security.Cryptography.AesGcm?displayProperty=nameWithType> and <xref:System.Security.Cryptography.AesCcm?displayProperty=nameWithType> respectively.</span></span> <span data-ttu-id="bccc1-336">Her ikisi de bu algoritmalar olan [ilişkilendirme veri (AEAD) algoritmaları ile kimliği doğrulanmış şifreleme](https://en.wikipedia.org/wiki/Authenticated_encryption).</span><span class="sxs-lookup"><span data-stu-id="bccc1-336">These algorithms are both [Authenticated Encryption with Association Data (AEAD) algorithms](https://en.wikipedia.org/wiki/Authenticated_encryption).</span></span>

<span data-ttu-id="bccc1-337">Aşağıdaki kodu `AesGcm` şifrelemek ve rastgele verilerin şifresini çözmek için şifre.</span><span class="sxs-lookup"><span data-stu-id="bccc1-337">The following code demonstrates using `AesGcm` cipher to encrypt and decrypt random data.</span></span>

[!CODE-csharp[AesGcm](~/samples/snippets/core/whats-new/whats-new-in-30/cs/Cipher.cs#AesGcm)]

## <a name="cryptographic-key-importexport"></a><span data-ttu-id="bccc1-338">Şifreleme anahtarı içeri/dışarı aktarma</span><span class="sxs-lookup"><span data-stu-id="bccc1-338">Cryptographic Key Import/Export</span></span>

<span data-ttu-id="bccc1-339">.NET core 3.0 standart biçimlerinden asimetrik ortak ve özel anahtarı dışarı aktarma ve içeri aktarma destekler.</span><span class="sxs-lookup"><span data-stu-id="bccc1-339">.NET Core 3.0 supports the import and export of asymmetric public and private keys from standard formats.</span></span> <span data-ttu-id="bccc1-340">X.509 sertifikası kullanmanız gerekmez.</span><span class="sxs-lookup"><span data-stu-id="bccc1-340">You don't need to use an X.509 certificate.</span></span>

<span data-ttu-id="bccc1-341">Tüm anahtar türleri gibi *RSA*, *DSA*, *ECDsa*, ve *ECDiffieHellman*, aşağıdaki biçimlerde destekler:</span><span class="sxs-lookup"><span data-stu-id="bccc1-341">All key types, such as *RSA*, *DSA*, *ECDsa*, and *ECDiffieHellman*, support the following formats:</span></span>

* <span data-ttu-id="bccc1-342">**Ortak anahtar**</span><span class="sxs-lookup"><span data-stu-id="bccc1-342">**Public Key**</span></span>
  * <span data-ttu-id="bccc1-343">X.509 SubjectPublicKeyInfo</span><span class="sxs-lookup"><span data-stu-id="bccc1-343">X.509 SubjectPublicKeyInfo</span></span>

* <span data-ttu-id="bccc1-344">**özel anahtar**</span><span class="sxs-lookup"><span data-stu-id="bccc1-344">**Private key**</span></span>
  * <span data-ttu-id="bccc1-345">PKCS #8 PrivateKeyInfo</span><span class="sxs-lookup"><span data-stu-id="bccc1-345">PKCS#8 PrivateKeyInfo</span></span>
  * <span data-ttu-id="bccc1-346">PKCS #8 EncryptedPrivateKeyInfo</span><span class="sxs-lookup"><span data-stu-id="bccc1-346">PKCS#8 EncryptedPrivateKeyInfo</span></span>

<span data-ttu-id="bccc1-347">RSA desteği de anahtarları:</span><span class="sxs-lookup"><span data-stu-id="bccc1-347">RSA keys also support:</span></span>

* <span data-ttu-id="bccc1-348">**Ortak anahtar**</span><span class="sxs-lookup"><span data-stu-id="bccc1-348">**Public Key**</span></span>
  * <span data-ttu-id="bccc1-349">PKCS#1 RSAPublicKey</span><span class="sxs-lookup"><span data-stu-id="bccc1-349">PKCS#1 RSAPublicKey</span></span>

* <span data-ttu-id="bccc1-350">**özel anahtar**</span><span class="sxs-lookup"><span data-stu-id="bccc1-350">**Private key**</span></span>
  * <span data-ttu-id="bccc1-351">PKCS #1 RSAPrivateKey</span><span class="sxs-lookup"><span data-stu-id="bccc1-351">PKCS#1 RSAPrivateKey</span></span>

<span data-ttu-id="bccc1-352">Dışarı aktarma yöntemleri DER ile kodlanmış ikili verileri oluşturmak ve içeri aktarma metotları aynı beklerler.</span><span class="sxs-lookup"><span data-stu-id="bccc1-352">The export methods produce DER-encoded binary data, and the import methods expect the same.</span></span> <span data-ttu-id="bccc1-353">Bir anahtar metin dostu PEM biçiminde depolanır, çağırana base64 gerekir-içerik alma yöntemini çağırmadan önce kod çözme.</span><span class="sxs-lookup"><span data-stu-id="bccc1-353">If a key is stored in the text-friendly PEM format, the caller will need to base64-decode the content before calling an import method.</span></span>

[!CODE-csharp[RSA](~/samples/snippets/core/whats-new/whats-new-in-30/cs/RSA.cs#Rsa)]

<span data-ttu-id="bccc1-354">**PKCS #8** dosyaları inceledi ile <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo?displayProperty=nameWithType> ve **PFX/PKCS #12** dosyaları inceledi ile <xref:System.Security.Cryptography.Pkcs.Pkcs12Info?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="bccc1-354">**PKCS#8** files can be inspected with <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo?displayProperty=nameWithType> and **PFX/PKCS#12** files can be inspected with <xref:System.Security.Cryptography.Pkcs.Pkcs12Info?displayProperty=nameWithType>.</span></span> <span data-ttu-id="bccc1-355">**PFX/PKCS #12** dosyalar işlenebilir <xref:System.Security.Cryptography.Pkcs.Pkcs12Builder?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="bccc1-355">**PFX/PKCS#12** files can be manipulated with <xref:System.Security.Cryptography.Pkcs.Pkcs12Builder?displayProperty=nameWithType>.</span></span>

## <a name="serialport-for-linux"></a><span data-ttu-id="bccc1-356">Linux için çevirmek için SerialPort</span><span class="sxs-lookup"><span data-stu-id="bccc1-356">SerialPort for Linux</span></span>

<span data-ttu-id="bccc1-357">.NET core 3.0 destekleyen <xref:System.IO.Ports.SerialPort?displayProperty=nameWithType> Linux üzerinde.</span><span class="sxs-lookup"><span data-stu-id="bccc1-357">.NET Core 3.0 supports <xref:System.IO.Ports.SerialPort?displayProperty=nameWithType> on Linux.</span></span>

<span data-ttu-id="bccc1-358">Daha önce yalnızca kullanarak desteklenen .NET Core `SerialPort` Windows üzerinde.</span><span class="sxs-lookup"><span data-stu-id="bccc1-358">Previously, .NET Core only supported using `SerialPort` on Windows.</span></span>

## <a name="docker-and-cgroup-memory-limits"></a><span data-ttu-id="bccc1-359">Docker ve cgroup bellek sınırları</span><span class="sxs-lookup"><span data-stu-id="bccc1-359">Docker and cgroup memory Limits</span></span>

<span data-ttu-id="bccc1-360">Preview 3'ten itibaren Docker ile Linux üzerinde .NET Core 3.0 çalıştıran daha iyi cgroup bellek sınırlarını ile çalışır.</span><span class="sxs-lookup"><span data-stu-id="bccc1-360">Starting with Preview 3, running .NET Core 3.0 on Linux with Docker works better with cgroup memory limits.</span></span> <span data-ttu-id="bccc1-361">Bellek sınırları, Docker kapsayıcısı gibi çalışan `docker run -m`, .NET Core nasıl davranacağını değiştirir.</span><span class="sxs-lookup"><span data-stu-id="bccc1-361">Running a Docker container with memory limits, such as with `docker run -m`, changes how .NET Core behaves.</span></span>

* <span data-ttu-id="bccc1-362">Varsayılan çöp toplayıcı (GC) yığın boyutu: en fazla 20 mb veya bellek sınırı kapsayıcı üzerindeki %75.</span><span class="sxs-lookup"><span data-stu-id="bccc1-362">Default Garbage Collector (GC) heap size: maximum of 20 mb or 75% of the memory limit on the container.</span></span>
* <span data-ttu-id="bccc1-363">Açık boyut bir mutlak sayı veya cgroup sınırı yüzdesi ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bccc1-363">Explicit size can be set as an absolute number or percentage of cgroup limit.</span></span>
* <span data-ttu-id="bccc1-364">GC yığınında başına en az ayrılmış kesim boyutu 16 mb'tır.</span><span class="sxs-lookup"><span data-stu-id="bccc1-364">Minimum reserved segment size per GC heap is 16 mb.</span></span> <span data-ttu-id="bccc1-365">Bu boyut makinelerde oluşturulan yığınlar sayısını azaltır.</span><span class="sxs-lookup"><span data-stu-id="bccc1-365">This size reduces the number of heaps that are created on machines.</span></span>

## <a name="smaller-garbage-collection-heap-sizes"></a><span data-ttu-id="bccc1-366">Küçük çöp toplama, öbek boyutları</span><span class="sxs-lookup"><span data-stu-id="bccc1-366">Smaller Garbage Collection heap sizes</span></span>

<span data-ttu-id="bccc1-367">.NET Core kullanarak daha az bellek kaynaklanan Atık toplayıcısının varsayılan öbek boyutu azaltıldı.</span><span class="sxs-lookup"><span data-stu-id="bccc1-367">The Garbage Collector's default heap size has been reduced resulting in .NET Core using less memory.</span></span> <span data-ttu-id="bccc1-368">Bu değişiklik, daha iyi modern işlemci önbellek boyutu nesil 0 ayırma bütçeyle ile uyumludur.</span><span class="sxs-lookup"><span data-stu-id="bccc1-368">This change better aligns with the generation 0 allocation budget with modern processor cache sizes.</span></span>

## <a name="garbage-collection-large-page-support"></a><span data-ttu-id="bccc1-369">Çöp toplama büyük sayfa desteği</span><span class="sxs-lookup"><span data-stu-id="bccc1-369">Garbage Collection Large Page support</span></span>

<span data-ttu-id="bccc1-370">Büyük sayfaları (diğer adıyla büyük Linux üzerinde), işletim sisteminin bu büyük sayfalar isteyen uygulama performansını artırmak için yerel sayfa boyutundan büyük (genellikle 4 K) bellek bölümlerinin oluşturmak mümkün olduğu bir özelliğidir.</span><span class="sxs-lookup"><span data-stu-id="bccc1-370">Large Pages (also known as Huge Pages on Linux) is a feature where the operating system is able to establish memory regions larger than the native page size (often 4K) to improve performance of the application requesting these large pages.</span></span>

<span data-ttu-id="bccc1-371">Çöp toplayıcı ile artık yapılandırılabilir **GCLargePages** Tercihli özellik ayarlanması büyük sayfalarında Windows ayırmak seçin.</span><span class="sxs-lookup"><span data-stu-id="bccc1-371">The Garbage Collector can now be configured with the **GCLargePages** setting as an opt-in feature to choose to allocate large pages on Windows.</span></span>

## <a name="gpio-support-for-raspberry-pi"></a><span data-ttu-id="bccc1-372">Raspberry Pi GPIO'yu desteği</span><span class="sxs-lookup"><span data-stu-id="bccc1-372">GPIO Support for Raspberry Pi</span></span>

<span data-ttu-id="bccc1-373">İki paket GPIO'yu programlama için kullanabileceğiniz NuGet yayımlanmış olan:</span><span class="sxs-lookup"><span data-stu-id="bccc1-373">Two packages have been released to NuGet that you can use for GPIO programming:</span></span>

* [<span data-ttu-id="bccc1-374">System.Device.Gpio</span><span class="sxs-lookup"><span data-stu-id="bccc1-374">System.Device.Gpio</span></span>](https://www.nuget.org/packages/System.Device.Gpio)
* [<span data-ttu-id="bccc1-375">Iot.Device.Bindings</span><span class="sxs-lookup"><span data-stu-id="bccc1-375">Iot.Device.Bindings</span></span>](https://www.nuget.org/packages/Iot.Device.Bindings)

<span data-ttu-id="bccc1-376">API'leri için GPIO paketleri dahil *GPIO'yu*, *SPI*, *I2C*, ve *PWM* cihazlar.</span><span class="sxs-lookup"><span data-stu-id="bccc1-376">The GPIO packages include APIs for *GPIO*, *SPI*, *I2C*, and *PWM* devices.</span></span> <span data-ttu-id="bccc1-377">IOT bağlamaları paketi, cihaz bağlamaları içerir.</span><span class="sxs-lookup"><span data-stu-id="bccc1-377">The IoT bindings package includes device bindings.</span></span> <span data-ttu-id="bccc1-378">Daha fazla bilgi için [cihazları GitHub deposunu](https://github.com/dotnet/iot/blob/master/src/devices/).</span><span class="sxs-lookup"><span data-stu-id="bccc1-378">For more information, see the [devices GitHub repo](https://github.com/dotnet/iot/blob/master/src/devices/).</span></span>

## <a name="arm64-linux-support"></a><span data-ttu-id="bccc1-379">ARM64 Linux desteği</span><span class="sxs-lookup"><span data-stu-id="bccc1-379">ARM64 Linux support</span></span>

<span data-ttu-id="bccc1-380">.NET core 3.0 Linux ARM64 için desteği ekler.</span><span class="sxs-lookup"><span data-stu-id="bccc1-380">.NET Core 3.0 adds support for ARM64 for Linux.</span></span> <span data-ttu-id="bccc1-381">ARM64 için birincil kullanım durumu şu anda IOT senaryoları ile aşamasındadır.</span><span class="sxs-lookup"><span data-stu-id="bccc1-381">The primary use case for ARM64 is currently with IoT scenarios.</span></span> <span data-ttu-id="bccc1-382">Daha fazla bilgi için [.NET Core ARM64 durumu](https://github.com/dotnet/announcements/issues/82).</span><span class="sxs-lookup"><span data-stu-id="bccc1-382">For more information, see [.NET Core ARM64 Status](https://github.com/dotnet/announcements/issues/82).</span></span>

<span data-ttu-id="bccc1-383">[ARM64 üzerinde .NET Core için docker görüntülerini](https://hub.docker.com/r/microsoft/dotnet/) kullanılabilir Alpine, Debian ve Ubuntu.</span><span class="sxs-lookup"><span data-stu-id="bccc1-383">[Docker images for .NET Core on ARM64](https://hub.docker.com/r/microsoft/dotnet/) are available for Alpine, Debian, and Ubuntu.</span></span>

> [!NOTE]
> <span data-ttu-id="bccc1-384">**ARM64** Windows Destek işlemi henüz kullanılamıyor.</span><span class="sxs-lookup"><span data-stu-id="bccc1-384">**ARM64** Windows support isn't yet available.</span></span>
