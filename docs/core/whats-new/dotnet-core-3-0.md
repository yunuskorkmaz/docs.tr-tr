---
title: ​.NET Core 3.0’daki yenilikler
description: .NET Core 3.0 ' de bulunan yeni özellikler hakkında bilgi edinin.
dev_langs:
- csharp
author: thraka
ms.author: adegeo
ms.date: 01/27/2020
ms.openlocfilehash: 60794c4f8a5f9aeb7a4b3cd58c0c9f00e03fa9e7
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77450986"
---
# <a name="whats-new-in-net-core-30"></a><span data-ttu-id="740e2-103">​.NET Core 3.0’daki yenilikler</span><span class="sxs-lookup"><span data-stu-id="740e2-103">What's new in .NET Core 3.0</span></span>

<span data-ttu-id="740e2-104">Bu makalede .NET Core 3.0 ' deki yenilikler açıklanır.</span><span class="sxs-lookup"><span data-stu-id="740e2-104">This article describes what is new in .NET Core 3.0.</span></span> <span data-ttu-id="740e2-105">En büyük geliştirmelerden biri, Windows Masaüstü uygulamaları için destek içerir (yalnızca Windows).</span><span class="sxs-lookup"><span data-stu-id="740e2-105">One of the biggest enhancements is support for Windows desktop applications (Windows only).</span></span> <span data-ttu-id="740e2-106">.NET Core 3.0 SDK bileşeni Windows Masaüstü 'Nü kullanarak Windows Forms ve Windows Presentation Foundation (WPF) uygulamalarınızın bağlantı noktası oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="740e2-106">By using the .NET Core 3.0 SDK component Windows Desktop, you can port your Windows Forms and Windows Presentation Foundation (WPF) applications.</span></span> <span data-ttu-id="740e2-107">Temiz olması için, Windows Masaüstü bileşeni yalnızca Windows 'da desteklenir ve Windows 'a dahildir.</span><span class="sxs-lookup"><span data-stu-id="740e2-107">To be clear, the Windows Desktop component is only supported and included on Windows.</span></span> <span data-ttu-id="740e2-108">Daha fazla bilgi için bu makalenin devamındaki [Windows Masaüstü](#windows-desktop) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="740e2-108">For more information, see the [Windows desktop](#windows-desktop) section later in this article.</span></span>

<span data-ttu-id="740e2-109">.NET Core 3.0, 8.0 için C# destek ekler.</span><span class="sxs-lookup"><span data-stu-id="740e2-109">.NET Core 3.0 adds support for C# 8.0.</span></span> <span data-ttu-id="740e2-110">[Visual Studio 2019 sürüm 16,3](https://visualstudio.microsoft.com/vs/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) veya daha yeni bir sürümünü, [Mac için Visual Studio 8,3](/visualstudio/mac/install-preview) veya daha yenisini veya en son  **C# uzantıya**sahip [Visual Studio Code](https://code.visualstudio.com/) kullanmanız kesinlikle önerilir.</span><span class="sxs-lookup"><span data-stu-id="740e2-110">It's highly recommended that you use [Visual Studio 2019 version 16.3](https://visualstudio.microsoft.com/vs/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) or newer, [Visual Studio for Mac 8.3](/visualstudio/mac/install-preview) or newer, or [Visual Studio Code](https://code.visualstudio.com/) with the latest **C# extension**.</span></span>

<span data-ttu-id="740e2-111">Şimdi Windows, macOS veya Linux 'ta [.NET Core 3,0 'Yi indirin ve](https://aka.ms/netcore3download) kullanmaya başlayın.</span><span class="sxs-lookup"><span data-stu-id="740e2-111">[Download and get started with .NET Core 3.0](https://aka.ms/netcore3download) right now on Windows, macOS, or Linux.</span></span>

<span data-ttu-id="740e2-112">Yayın hakkında daha fazla bilgi için bkz. [.NET Core 3,0 duyurusu](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-0/).</span><span class="sxs-lookup"><span data-stu-id="740e2-112">For more information about the release, see the [.NET Core 3.0 announcement](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-0/).</span></span>

<span data-ttu-id="740e2-113">.NET Core RC1, Microsoft tarafından önceden hazırlanmıştı ve tam olarak desteklenmektedir.</span><span class="sxs-lookup"><span data-stu-id="740e2-113">.NET Core RC1 was considered production ready by Microsoft and was fully supported.</span></span> <span data-ttu-id="740e2-114">Önizleme sürümü kullanıyorsanız, devam eden destek için RTM sürümüne geçmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="740e2-114">If you're using a preview release, you must move to the RTM version for continued support.</span></span>

## <a name="language-improvements-c-80"></a><span data-ttu-id="740e2-115">Dil geliştirmeleri C# 8,0</span><span class="sxs-lookup"><span data-stu-id="740e2-115">Language improvements C# 8.0</span></span>

<span data-ttu-id="740e2-116">C#8,0 Ayrıca, [null yapılabilir başvuru türleri](../../csharp/tutorials/nullable-reference-types.md) özelliği, [zaman uyumsuz akışlar](../../csharp/tutorials/generate-consume-asynchronous-stream.md)ve [daha fazla desen](../../csharp/tutorials/pattern-matching.md)içeren bu sürümün bir parçasıdır.</span><span class="sxs-lookup"><span data-stu-id="740e2-116">C# 8.0 is also part of this release, which includes the [nullable reference types](../../csharp/tutorials/nullable-reference-types.md) feature, [async streams](../../csharp/tutorials/generate-consume-asynchronous-stream.md), and [more patterns](../../csharp/tutorials/pattern-matching.md).</span></span> <span data-ttu-id="740e2-117">8,0 özellikleri hakkında C# daha fazla bilgi için bkz. [ C# 8,0](../../csharp/whats-new/csharp-8.md)sürümündeki yenilikler.</span><span class="sxs-lookup"><span data-stu-id="740e2-117">For more information about C# 8.0 features, see [What's new in C# 8.0](../../csharp/whats-new/csharp-8.md).</span></span>

<span data-ttu-id="740e2-118">Aşağıda ayrıntılı olarak açıklanan aşağıdaki API özelliklerini desteklemek için dil geliştirmeleri eklenmiştir:</span><span class="sxs-lookup"><span data-stu-id="740e2-118">Language enhancements were added to support the following API features detailed below:</span></span>

- [<span data-ttu-id="740e2-119">Aralıklar ve dizinler</span><span class="sxs-lookup"><span data-stu-id="740e2-119">Ranges and indices</span></span>](#ranges-and-indices)
- [<span data-ttu-id="740e2-120">Zaman uyumsuz akışlar</span><span class="sxs-lookup"><span data-stu-id="740e2-120">Async streams</span></span>](#async-streams)

## <a name="net-standard-21"></a><span data-ttu-id="740e2-121">.NET Standard 2,1</span><span class="sxs-lookup"><span data-stu-id="740e2-121">.NET Standard 2.1</span></span>

<span data-ttu-id="740e2-122">.NET Core 3,0 **.NET Standard 2,1**uygular.</span><span class="sxs-lookup"><span data-stu-id="740e2-122">.NET Core 3.0 implements **.NET Standard 2.1**.</span></span> <span data-ttu-id="740e2-123">Ancak, varsayılan `dotnet new classlib` şablonu, hala **2,0 .NET Standard**hedefleyen bir proje oluşturur.</span><span class="sxs-lookup"><span data-stu-id="740e2-123">However, the default `dotnet new classlib` template generates a project that still targets **.NET Standard 2.0**.</span></span> <span data-ttu-id="740e2-124">**.NET Standard 2,1**' i hedeflemek için proje dosyanızı düzenleyin ve `TargetFramework` özelliğini `netstandard2.1`olarak değiştirin:</span><span class="sxs-lookup"><span data-stu-id="740e2-124">To target **.NET Standard 2.1**, edit your project file and change the `TargetFramework` property to `netstandard2.1`:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <TargetFramework>netstandard2.1</TargetFramework>
  </PropertyGroup>

</Project>
```

<span data-ttu-id="740e2-125">Visual Studio kullanıyorsanız, Visual Studio 2017 **.NET Standard 2,1** veya **.NET Core 3,0**' i desteklemediğinden [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019)gerekir.</span><span class="sxs-lookup"><span data-stu-id="740e2-125">If you're using Visual Studio, you need [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019), as Visual Studio 2017 doesn't support **.NET Standard 2.1** or **.NET Core 3.0**.</span></span>

## <a name="compiledeploy"></a><span data-ttu-id="740e2-126">Derle/dağıt</span><span class="sxs-lookup"><span data-stu-id="740e2-126">Compile/Deploy</span></span>

### <a name="default-executables"></a><span data-ttu-id="740e2-127">Varsayılan yürütülebilir dosyalar</span><span class="sxs-lookup"><span data-stu-id="740e2-127">Default executables</span></span>

<span data-ttu-id="740e2-128">.NET Core artık [çerçeveye bağlı yürütülebilir dosyaları](../deploying/index.md#publish-runtime-dependent) varsayılan olarak oluşturur.</span><span class="sxs-lookup"><span data-stu-id="740e2-128">.NET Core now builds [framework-dependent executables](../deploying/index.md#publish-runtime-dependent) by default.</span></span> <span data-ttu-id="740e2-129">Bu davranış, .NET Core 'un küresel olarak yüklenen bir sürümünü kullanan uygulamalar için yenidir.</span><span class="sxs-lookup"><span data-stu-id="740e2-129">This behavior is new for applications that use a globally installed version of .NET Core.</span></span> <span data-ttu-id="740e2-130">Daha önce yalnızca [kendi kendine kapsanan dağıtımlar](../deploying/index.md#publish-self-contained) yürütülebilir bir dosya üretecektir.</span><span class="sxs-lookup"><span data-stu-id="740e2-130">Previously, only [self-contained deployments](../deploying/index.md#publish-self-contained) would produce an executable.</span></span>

<span data-ttu-id="740e2-131">`dotnet build` veya `dotnet publish`sırasında, kullanmakta olduğunuz SDK ortamı ve platformuyla eşleşen bir yürütülebilir dosya oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="740e2-131">During `dotnet build` or `dotnet publish`, an executable is created that matches the environment and platform of the SDK you're using.</span></span> <span data-ttu-id="740e2-132">Bu yürütülebilir dosyalarla aynı şeyleri, diğer yerel yürütülebilir dosyaları gibi bekleyebilir, örneğin:</span><span class="sxs-lookup"><span data-stu-id="740e2-132">You can expect the same things with these executables as you would other native executables, such as:</span></span>

- <span data-ttu-id="740e2-133">Yürütülebilir dosyaya çift tıklayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="740e2-133">You can double-click on the executable.</span></span>
- <span data-ttu-id="740e2-134">Uygulamayı Windows üzerinde `myapp.exe`, Linux ve macOS 'ta `./myapp` gibi doğrudan bir komut isteminden başlatabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="740e2-134">You can launch the application from a command prompt directly, such as `myapp.exe` on Windows, and `./myapp` on Linux and macOS.</span></span>

### <a name="single-file-executables"></a><span data-ttu-id="740e2-135">Tek dosya yürütülebilir dosyaları</span><span class="sxs-lookup"><span data-stu-id="740e2-135">Single-file executables</span></span>

<span data-ttu-id="740e2-136">`dotnet publish` komutu, uygulamanızı platforma özgü tek dosya yürütülebilir dosyasına paketlemeyi destekler.</span><span class="sxs-lookup"><span data-stu-id="740e2-136">The `dotnet publish` command supports packaging your app into a platform-specific single-file executable.</span></span> <span data-ttu-id="740e2-137">Yürütülebilir dosya kendiliğinden ayıklanıyor ve uygulamanızı çalıştırmak için gerekli tüm bağımlılıkları (yerel dahil) içerir.</span><span class="sxs-lookup"><span data-stu-id="740e2-137">The executable is self-extracting and contains all dependencies (including native) that are required to run your app.</span></span> <span data-ttu-id="740e2-138">Uygulama ilk kez çalıştırıldığında uygulama adı ve derleme tanımlayıcısı temelinde bir dizine çıkarılır.</span><span class="sxs-lookup"><span data-stu-id="740e2-138">When the app is first run, the application is extracted to a directory based on the app name and build identifier.</span></span> <span data-ttu-id="740e2-139">Uygulama yeniden çalıştırıldığında başlatma daha hızlıdır.</span><span class="sxs-lookup"><span data-stu-id="740e2-139">Startup is faster when the application is run again.</span></span> <span data-ttu-id="740e2-140">Yeni bir sürüm kullanılmadığı takdirde uygulamanın kendisi ikinci kez ayıklanmasına gerek yoktur.</span><span class="sxs-lookup"><span data-stu-id="740e2-140">The application doesn't need to extract itself a second time unless a new version was used.</span></span>

<span data-ttu-id="740e2-141">Tek dosya yürütülebiliri yayımlamak için, projenizdeki `PublishSingleFile` veya komut satırında `dotnet publish` komutuyla ayarlayın:</span><span class="sxs-lookup"><span data-stu-id="740e2-141">To publish a single-file executable, set the `PublishSingleFile` in your project or on the command line with the `dotnet publish` command:</span></span>

```xml
<PropertyGroup>
  <RuntimeIdentifier>win10-x64</RuntimeIdentifier>
  <PublishSingleFile>true</PublishSingleFile>
</PropertyGroup>
```

<span data-ttu-id="740e2-142">veya</span><span class="sxs-lookup"><span data-stu-id="740e2-142">-or-</span></span>

```dotnetcli
dotnet publish -r win10-x64 -p:PublishSingleFile=true
```

<span data-ttu-id="740e2-143">Tek dosya yayınlama hakkında daha fazla bilgi için bkz. [tek dosya paketcisi tasarım belgesi](https://github.com/dotnet/designs/blob/master/accepted/single-file/design.md).</span><span class="sxs-lookup"><span data-stu-id="740e2-143">For more information about single-file publishing, see the [single-file bundler design document](https://github.com/dotnet/designs/blob/master/accepted/single-file/design.md).</span></span>

### <a name="assembly-linking"></a><span data-ttu-id="740e2-144">Bütünleştirilmiş kod bağlama</span><span class="sxs-lookup"><span data-stu-id="740e2-144">Assembly linking</span></span>

<span data-ttu-id="740e2-145">.NET Core 3.0 SDK, Il 'yi çözümleyerek ve kullanılmayan derlemeleri kırparak uygulamaların boyutunu azaltan bir araçla birlikte gelir.</span><span class="sxs-lookup"><span data-stu-id="740e2-145">The .NET core 3.0 SDK comes with a tool that can reduce the size of apps by analyzing IL and trimming unused assemblies.</span></span>

<span data-ttu-id="740e2-146">Bağımsız uygulamalar, kodunuzun çalıştırılması için gereken her şeyi, ana bilgisayara .NET yüklenmesini gerektirmeden içerir.</span><span class="sxs-lookup"><span data-stu-id="740e2-146">Self-contained apps include everything needed to run your code, without requiring .NET to be installed on the host computer.</span></span> <span data-ttu-id="740e2-147">Ancak, çoğu zaman uygulamanın çalışması için yalnızca küçük bir çerçeve alt kümesi gerekir ve kullanılmayan diğer kitaplıklar da kaldırılabilir.</span><span class="sxs-lookup"><span data-stu-id="740e2-147">However, many times the app only requires a small subset of the framework to function, and other unused libraries could be removed.</span></span>

<span data-ttu-id="740e2-148">.NET Core artık uygulamanızın Il 'sini taramak için [Il bağlayıcı](https://github.com/mono/linker) aracını kullanacak bir ayar içeriyor.</span><span class="sxs-lookup"><span data-stu-id="740e2-148">.NET Core now includes a setting that will use the [IL linker](https://github.com/mono/linker) tool to scan the IL of your app.</span></span> <span data-ttu-id="740e2-149">Bu araç hangi kodun gerekli olduğunu algılar ve ardından kullanılmayan kitaplıkları kırpar.</span><span class="sxs-lookup"><span data-stu-id="740e2-149">This tool detects what code is required, and then trims unused libraries.</span></span> <span data-ttu-id="740e2-150">Bu araç bazı uygulamaların dağıtım boyutunu önemli ölçüde azaltabilir.</span><span class="sxs-lookup"><span data-stu-id="740e2-150">This tool can significantly reduce the deployment size of some apps.</span></span>

<span data-ttu-id="740e2-151">Bu aracı etkinleştirmek için projenize `<PublishTrimmed>` ayarını ekleyin ve kendi içinde olan bir uygulamayı yayımlayın:</span><span class="sxs-lookup"><span data-stu-id="740e2-151">To enable this tool, add the `<PublishTrimmed>` setting in your project and publish a self-contained app:</span></span>

```xml
<PropertyGroup>
  <PublishTrimmed>true</PublishTrimmed>
</PropertyGroup>
```

```dotnetcli
dotnet publish -r <rid> -c Release
```

<span data-ttu-id="740e2-152">Örnek olarak, yayımlanan temel "Merhaba Dünya" yeni konsol projesi şablonu, yayımlandığında 70 MB ile çarpılır.</span><span class="sxs-lookup"><span data-stu-id="740e2-152">As an example, the basic "hello world" new console project template that is included, when published, hits about 70 MB in size.</span></span> <span data-ttu-id="740e2-153">`<PublishTrimmed>`kullanarak, bu boyut yaklaşık 30 MB 'ye indirilir.</span><span class="sxs-lookup"><span data-stu-id="740e2-153">By using `<PublishTrimmed>`, that size is reduced to about 30 MB.</span></span>

<span data-ttu-id="740e2-154">Yansıma veya ilgili dinamik özellikleri kullanan uygulamaların veya çerçevelerin (ASP.NET Core ve WPF dahil) genellikle kırpıldığına göre kesilmesini göz önünde bulundurmanız önemlidir.</span><span class="sxs-lookup"><span data-stu-id="740e2-154">It's important to consider that applications or frameworks (including ASP.NET Core and WPF) that use reflection or related dynamic features, will often break when trimmed.</span></span> <span data-ttu-id="740e2-155">Bu ayırıcı, bağlayıcının bu dinamik davranış hakkında bilgi sahibi olmadığı ve yansıma için hangi çerçeve türlerinin gerekli olduğunu belirleyemediği için oluşur.</span><span class="sxs-lookup"><span data-stu-id="740e2-155">This breakage occurs because the linker doesn't know about this dynamic behavior and can't determine which framework types are required for reflection.</span></span> <span data-ttu-id="740e2-156">Il bağlayıcı aracı, bu senaryonun farkında olacak şekilde yapılandırılabilir.</span><span class="sxs-lookup"><span data-stu-id="740e2-156">The IL Linker tool can be configured to be aware of this scenario.</span></span>

<span data-ttu-id="740e2-157">Tüm diğerleri üzerinde, kırpdıktan sonra uygulamanızı test ettiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="740e2-157">Above all else, be sure to test your app after trimming.</span></span>

<span data-ttu-id="740e2-158">Il bağlayıcı aracı hakkında daha fazla bilgi için [belgelere](https://aka.ms/dotnet-illink) bakın veya [mono/bağlayıcı]( https://github.com/mono/linker) deposunu ziyaret edin.</span><span class="sxs-lookup"><span data-stu-id="740e2-158">For more information about the IL Linker tool, see the [documentation](https://aka.ms/dotnet-illink) or visit the [mono/linker]( https://github.com/mono/linker) repo.</span></span>

### <a name="tiered-compilation"></a><span data-ttu-id="740e2-159">Katmanlı derleme</span><span class="sxs-lookup"><span data-stu-id="740e2-159">Tiered compilation</span></span>

<span data-ttu-id="740e2-160">[Katmanlı derleme](https://github.com/dotnet/runtime/blob/master/docs/design/features/tiered-compilation-guide.md) (TC), .net Core 3,0 ile varsayılan olarak açık olur.</span><span class="sxs-lookup"><span data-stu-id="740e2-160">[Tiered compilation](https://github.com/dotnet/runtime/blob/master/docs/design/features/tiered-compilation-guide.md) (TC) is on by default with .NET Core 3.0.</span></span> <span data-ttu-id="740e2-161">Bu özellik, çalışma zamanının daha iyi performans elde etmek için tam zamanında (JıT) derleyicisini daha kolay bir şekilde kullanmasına olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="740e2-161">This feature enables the runtime to more adaptively use the just-in-time (JIT) compiler to achieve better performance.</span></span>

<span data-ttu-id="740e2-162">Katmanlı derlemenin başlıca avantajı, daha düşük kalitede, ancak daha hızlı bir katmanda ya da daha yüksek kalitede, ancak daha yavaş bir katmanda çeşitli yöntemler elde etmenin iki yolunu sağlamaktır.</span><span class="sxs-lookup"><span data-stu-id="740e2-162">The main benefit of tiered compilation is to provide two ways of jitting methods: in a lower-quality-but-faster tier or a higher-quality-but-slower tier.</span></span> <span data-ttu-id="740e2-163">Kalite, yöntemin en iyi duruma getirilmiş olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="740e2-163">The quality refers to how well the method is optimized.</span></span> <span data-ttu-id="740e2-164">TC, düzenli bir durum aracılığıyla başlangıçtan itibaren çeşitli yürütme aşamalarından geçen bir uygulamanın performansını artırmaya yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="740e2-164">TC helps to improve the performance of an application as it goes through various stages of execution, from startup through steady state.</span></span> <span data-ttu-id="740e2-165">Katmanlı derleme devre dışı bırakıldığında, her yöntem, başlangıç performansı üzerinden düzenli durum performansına yol gösteren tek bir şekilde derlenir.</span><span class="sxs-lookup"><span data-stu-id="740e2-165">When tiered compilation is disabled, every method is compiled in a single way that's biased to steady-state performance over startup performance.</span></span>

<span data-ttu-id="740e2-166">TC etkinleştirildiğinde, bir uygulama başlatıldığında Yöntem derlemesi için aşağıdaki davranış geçerlidir:</span><span class="sxs-lookup"><span data-stu-id="740e2-166">When TC is enabled, the following behavior applies for method compilation when an app starts up:</span></span>

- <span data-ttu-id="740e2-167">Metodun önceden derlenen kodu veya [Readytorun](#readytorun-images)varsa, önceden oluşturulan kod kullanılır.</span><span class="sxs-lookup"><span data-stu-id="740e2-167">If the method has ahead-of-time-compiled code, or [ReadyToRun](#readytorun-images), the pregenerated code is used.</span></span>
- <span data-ttu-id="740e2-168">Aksi halde, yöntemi jmesdir.</span><span class="sxs-lookup"><span data-stu-id="740e2-168">Otherwise, the method is jitted.</span></span> <span data-ttu-id="740e2-169">Genellikle, bu yöntemler değer türleri üzerinde genel türlerdir.</span><span class="sxs-lookup"><span data-stu-id="740e2-169">Typically, these methods are generics over value types.</span></span>
  - <span data-ttu-id="740e2-170">*Hızlı JIT* daha hızlı (veya daha az iyileştirilmiş) kod üretir.</span><span class="sxs-lookup"><span data-stu-id="740e2-170">*Quick JIT* produces lower-quality (or less optimized) code more quickly.</span></span> <span data-ttu-id="740e2-171">.NET Core 3,0 ' de hızlı JıT, döngüler içermeyen ve başlangıç sırasında tercih edilen yöntemler için varsayılan olarak etkindir.</span><span class="sxs-lookup"><span data-stu-id="740e2-171">In .NET Core 3.0, Quick JIT is enabled by default for methods that don't contain loops and is preferred during startup.</span></span>
  - <span data-ttu-id="740e2-172">JıT 'i tamamen en iyi duruma getirmek daha yavaş daha yavaş (veya daha iyileştirilmiş) kod üretir.</span><span class="sxs-lookup"><span data-stu-id="740e2-172">The fully optimizing JIT produces higher-quality (or more optimized) code more slowly.</span></span> <span data-ttu-id="740e2-173">Hızlı JıT 'in kullanılacağı yöntemler için (örneğin, yöntem <xref:System.Runtime.CompilerServices.MethodImplOptions.AggressiveOptimization?displayProperty=nameWithType>ile ilişkilendirilebildiği), JıT tam olarak iyileştiriliyor kullanılır.</span><span class="sxs-lookup"><span data-stu-id="740e2-173">For methods where Quick JIT would not be used (for example, if the method is attributed with <xref:System.Runtime.CompilerServices.MethodImplOptions.AggressiveOptimization?displayProperty=nameWithType>), the fully optimizing JIT is used.</span></span>

<span data-ttu-id="740e2-174">Sık çağrılan yöntemler için, tam zamanında derleyici arka planda tamamen iyileştirilmiş kod oluşturur.</span><span class="sxs-lookup"><span data-stu-id="740e2-174">For frequently called methods, the just-in-time compiler eventually creates fully optimized code in the background.</span></span> <span data-ttu-id="740e2-175">En iyi duruma getirilmiş kod daha sonra bu yöntem için önceden derlenmiş kodun yerini alır.</span><span class="sxs-lookup"><span data-stu-id="740e2-175">The optimized code then replaces the pre-compiled code for that method.</span></span>

<span data-ttu-id="740e2-176">Hızlı JıT tarafından oluşturulan kod daha yavaş çalışabilir, daha fazla bellek ayırabilir veya daha fazla yığın alanı kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="740e2-176">Code generated by Quick JIT may run slower, allocate more memory, or use more stack space.</span></span> <span data-ttu-id="740e2-177">Sorunlar varsa, proje dosyasında bu MSBuild özelliğini kullanarak hızlı JıT 'i devre dışı bırakabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="740e2-177">If there are issues, you can disabled Quick JIT using this MSBuild property in the project file:</span></span>

```xml
<PropertyGroup>
  <TieredCompilationQuickJit>false</TieredCompilationQuickJit>
</PropertyGroup>
```

<span data-ttu-id="740e2-178">TC 'yi tamamen devre dışı bırakmak için, proje dosyanızda bu MSBuild özelliğini kullanın:</span><span class="sxs-lookup"><span data-stu-id="740e2-178">To disable TC completely, use this MSBuild property in your project file:</span></span>

```xml
<PropertyGroup>
  <TieredCompilation>false</TieredCompilation>
</PropertyGroup>
```

> [!TIP]
> <span data-ttu-id="740e2-179">Bu ayarları proje dosyasında değiştirirseniz, yeni ayarların yansıtılması için temiz bir derleme gerçekleştirmeniz gerekebilir (`obj` ve dizinleri `bin` ve yeniden derle).</span><span class="sxs-lookup"><span data-stu-id="740e2-179">If you change these settings in the project file, you may need to perform a clean build for the new settings to be reflected (delete the `obj` and `bin` directories and rebuild).</span></span>

<span data-ttu-id="740e2-180">Çalışma zamanında derlemeyi yapılandırma hakkında daha fazla bilgi için bkz. [derleme Için çalışma zamanı yapılandırma seçenekleri](../run-time-config/compilation.md).</span><span class="sxs-lookup"><span data-stu-id="740e2-180">For more information about configuring compilation at run time, see [Run-time configuration options for compilation](../run-time-config/compilation.md).</span></span>

### <a name="readytorun-images"></a><span data-ttu-id="740e2-181">ReadyToRun görüntüleri</span><span class="sxs-lookup"><span data-stu-id="740e2-181">ReadyToRun images</span></span>

<span data-ttu-id="740e2-182">Uygulama derlemelerinizi ReadyToRun (R2R) biçiminde derleyerek .NET Core uygulamanızın başlama süresini geliştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="740e2-182">You can improve the startup time of your .NET Core application by compiling your application assemblies as ReadyToRun (R2R) format.</span></span> <span data-ttu-id="740e2-183">R2R, bir süre öncesi (AOT) derleme biçimidir.</span><span class="sxs-lookup"><span data-stu-id="740e2-183">R2R is a form of ahead-of-time (AOT) compilation.</span></span>

<span data-ttu-id="740e2-184">R2R ikilileri, tam zamanında (JıT) derleyicisinin uygulamanız yüklenirken yapması gereken iş miktarını azaltarak başlangıç performansını geliştirir.</span><span class="sxs-lookup"><span data-stu-id="740e2-184">R2R binaries improve startup performance by reducing the amount of work the just-in-time (JIT) compiler needs to do as your application loads.</span></span> <span data-ttu-id="740e2-185">İkililer, JıT 'in üretmesine kıyasla benzer yerel kod içerir.</span><span class="sxs-lookup"><span data-stu-id="740e2-185">The binaries contain similar native code compared to what the JIT would produce.</span></span> <span data-ttu-id="740e2-186">Ancak, R2R ikilileri, bazı senaryolar için hala gerekli olan hem ara dil (IL) kodunu hem de aynı kodun yerel sürümünü içerdiğinden, daha büyüktür.</span><span class="sxs-lookup"><span data-stu-id="740e2-186">However, R2R binaries are larger because they contain both intermediate language (IL) code, which is still needed for some scenarios, and the native version of the same code.</span></span> <span data-ttu-id="740e2-187">R2R yalnızca, Linux x64 veya Windows x64 gibi belirli çalışma zamanı ortamlarını (RID) hedefleyen bir kendi içinde bulunan uygulamayı yayımladığınızda kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="740e2-187">R2R is only available when you publish a self-contained app that targets specific runtime environments (RID) such as Linux x64 or Windows x64.</span></span>

<span data-ttu-id="740e2-188">Projenizi ReadyToRun olarak derlemek için aşağıdakileri yapın:</span><span class="sxs-lookup"><span data-stu-id="740e2-188">To compile your project as ReadyToRun, do the following:</span></span>

01. <span data-ttu-id="740e2-189">`<PublishReadyToRun>` ayarını projenize ekleyin:</span><span class="sxs-lookup"><span data-stu-id="740e2-189">Add the `<PublishReadyToRun>` setting to your project:</span></span>

    ```xml
    <PropertyGroup>
      <PublishReadyToRun>true</PublishReadyToRun>
    </PropertyGroup>
    ```

01. <span data-ttu-id="740e2-190">Kendi içinde bir uygulama yayımlayın.</span><span class="sxs-lookup"><span data-stu-id="740e2-190">Publish a self-contained app.</span></span> <span data-ttu-id="740e2-191">Örneğin, bu komut Windows 'un 64 bit sürümü için kendi kendine içerilen bir uygulama oluşturur:</span><span class="sxs-lookup"><span data-stu-id="740e2-191">For example, this command creates a self-contained app for the 64-bit version of Windows:</span></span>

    ```dotnetcli
    dotnet publish -c Release -r win-x64 --self-contained
    ```

#### <a name="cross-platformarchitecture-restrictions"></a><span data-ttu-id="740e2-192">Platformlar arası/mimari kısıtlamaları</span><span class="sxs-lookup"><span data-stu-id="740e2-192">Cross platform/architecture restrictions</span></span>

<span data-ttu-id="740e2-193">ReadyToRun derleyicisi Şu anda çapraz hedefleme 'yi desteklememektedir.</span><span class="sxs-lookup"><span data-stu-id="740e2-193">The ReadyToRun compiler doesn't currently support cross-targeting.</span></span> <span data-ttu-id="740e2-194">Belirli bir hedefte derleme yapmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="740e2-194">You must compile on a given target.</span></span> <span data-ttu-id="740e2-195">Örneğin, R2R görüntülerini Windows x64 için istiyorsanız, bu ortamda Yayımla komutunu çalıştırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="740e2-195">For example, if you want R2R images for Windows x64, you need to run the publish command on that environment.</span></span>

<span data-ttu-id="740e2-196">Çapraz hedefleme için özel durumlar:</span><span class="sxs-lookup"><span data-stu-id="740e2-196">Exceptions to cross-targeting:</span></span>

- <span data-ttu-id="740e2-197">Windows x64, Windows ARM32, ARM64 ve x86 görüntülerini derlemek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="740e2-197">Windows x64 can be used to compile Windows ARM32, ARM64, and x86 images.</span></span>
- <span data-ttu-id="740e2-198">Windows x86, Windows ARM32 görüntülerini derlemek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="740e2-198">Windows x86 can be used to compile Windows ARM32 images.</span></span>
- <span data-ttu-id="740e2-199">Linux x64, Linux ARM32 ve ARM64 görüntülerini derlemek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="740e2-199">Linux x64 can be used to compile Linux ARM32 and ARM64 images.</span></span>

## <a name="runtimesdk"></a><span data-ttu-id="740e2-200">Çalışma zamanı/SDK</span><span class="sxs-lookup"><span data-stu-id="740e2-200">Runtime/SDK</span></span>

### <a name="major-version-runtime-roll-forward"></a><span data-ttu-id="740e2-201">Büyük sürüm çalışma zamanı ileri</span><span class="sxs-lookup"><span data-stu-id="740e2-201">Major-version runtime roll forward</span></span>

<span data-ttu-id="740e2-202">.NET Core 3.0, uygulamanızın .NET Core 'un en son ana sürümüne iletmesini sağlayan bir katılım özelliği sunar.</span><span class="sxs-lookup"><span data-stu-id="740e2-202">.NET Core 3.0 introduces an opt-in feature that allows your app to roll forward to the latest major version of .NET Core.</span></span> <span data-ttu-id="740e2-203">Ayrıca, geri alma 'nın uygulamanıza nasıl uygulandığını denetlemek için yeni bir ayar eklenmiştir.</span><span class="sxs-lookup"><span data-stu-id="740e2-203">Additionally, a new setting has been added to control how roll forward is applied to your app.</span></span> <span data-ttu-id="740e2-204">Bu, aşağıdaki yollarla yapılandırılabilir:</span><span class="sxs-lookup"><span data-stu-id="740e2-204">This can be configured in the following ways:</span></span>

- <span data-ttu-id="740e2-205">Proje dosyası özelliği: `RollForward`</span><span class="sxs-lookup"><span data-stu-id="740e2-205">Project file property: `RollForward`</span></span>
- <span data-ttu-id="740e2-206">Çalışma zamanı yapılandırma dosyası özelliği: `rollForward`</span><span class="sxs-lookup"><span data-stu-id="740e2-206">Run-time configuration file property: `rollForward`</span></span>
- <span data-ttu-id="740e2-207">Ortam değişkeni: `DOTNET_ROLL_FORWARD`</span><span class="sxs-lookup"><span data-stu-id="740e2-207">Environment variable: `DOTNET_ROLL_FORWARD`</span></span>
- <span data-ttu-id="740e2-208">Komut satırı bağımsız değişkeni: `--roll-forward`</span><span class="sxs-lookup"><span data-stu-id="740e2-208">Command-line argument: `--roll-forward`</span></span>

<span data-ttu-id="740e2-209">Aşağıdaki değerlerden biri belirtilmelidir.</span><span class="sxs-lookup"><span data-stu-id="740e2-209">One of the following values must be specified.</span></span> <span data-ttu-id="740e2-210">Ayar atlanırsa, **İkincil** varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="740e2-210">If the setting is omitted, **Minor** is the default.</span></span>

- <span data-ttu-id="740e2-211">**Latestpatch**</span><span class="sxs-lookup"><span data-stu-id="740e2-211">**LatestPatch**</span></span>\
<span data-ttu-id="740e2-212">En yüksek düzeltme eki sürümüne ilet.</span><span class="sxs-lookup"><span data-stu-id="740e2-212">Roll forward to the highest patch version.</span></span> <span data-ttu-id="740e2-213">Bu, ikincil sürüm iletmeyi devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="740e2-213">This disables minor version roll forward.</span></span>
- <span data-ttu-id="740e2-214">**Küçük**</span><span class="sxs-lookup"><span data-stu-id="740e2-214">**Minor**</span></span>\
<span data-ttu-id="740e2-215">İstenen alt sürüm eksikse, en düşük düzeydeki sürüme ilet.</span><span class="sxs-lookup"><span data-stu-id="740e2-215">Roll forward to the lowest higher minor version, if requested minor version is missing.</span></span> <span data-ttu-id="740e2-216">İstenen ikincil sürüm varsa, **Latestpatch** ilkesi kullanılır.</span><span class="sxs-lookup"><span data-stu-id="740e2-216">If the requested minor version is present, then the **LatestPatch** policy is used.</span></span>
- <span data-ttu-id="740e2-217">**Ana**</span><span class="sxs-lookup"><span data-stu-id="740e2-217">**Major**</span></span>\
<span data-ttu-id="740e2-218">İstenen ana sürüm eksikse, en düşük büyük sürüme ve en düşük alt sürüme ileri doğru alın.</span><span class="sxs-lookup"><span data-stu-id="740e2-218">Roll forward to lowest higher major version, and lowest minor version, if requested major version is missing.</span></span> <span data-ttu-id="740e2-219">İstenen ana sürüm varsa, **İkincil** ilke kullanılır.</span><span class="sxs-lookup"><span data-stu-id="740e2-219">If the requested major version is present, then the **Minor** policy is used.</span></span>
- <span data-ttu-id="740e2-220">**Latestminor**</span><span class="sxs-lookup"><span data-stu-id="740e2-220">**LatestMinor**</span></span>\
<span data-ttu-id="740e2-221">İstenen alt sürüm mevcut olsa bile en yüksek düzeyde alt sürüme ilet.</span><span class="sxs-lookup"><span data-stu-id="740e2-221">Roll forward to highest minor version, even if requested minor version is present.</span></span> <span data-ttu-id="740e2-222">Bileşen barındırma senaryolarına yöneliktir.</span><span class="sxs-lookup"><span data-stu-id="740e2-222">Intended for component hosting scenarios.</span></span>
- <span data-ttu-id="740e2-223">**Latestana**</span><span class="sxs-lookup"><span data-stu-id="740e2-223">**LatestMajor**</span></span>\
<span data-ttu-id="740e2-224">İstenen ana mevcut olsa bile, en yüksek büyük ve en yüksek düzeyde alt sürüme ilet.</span><span class="sxs-lookup"><span data-stu-id="740e2-224">Roll forward to highest major and highest minor version, even if requested major is present.</span></span> <span data-ttu-id="740e2-225">Bileşen barındırma senaryolarına yöneliktir.</span><span class="sxs-lookup"><span data-stu-id="740e2-225">Intended for component hosting scenarios.</span></span>
- <span data-ttu-id="740e2-226">\ **devre dışı bırak**</span><span class="sxs-lookup"><span data-stu-id="740e2-226">**Disable**\</span></span>
<span data-ttu-id="740e2-227">İleri alma.</span><span class="sxs-lookup"><span data-stu-id="740e2-227">Don't roll forward.</span></span> <span data-ttu-id="740e2-228">Yalnızca belirtilen sürüme bağlayın.</span><span class="sxs-lookup"><span data-stu-id="740e2-228">Only bind to specified version.</span></span> <span data-ttu-id="740e2-229">Bu ilke, en son düzeltme eklerine iletme özelliğini devre dışı bıraktığından genel kullanım için önerilmez.</span><span class="sxs-lookup"><span data-stu-id="740e2-229">This policy isn't recommended for general use because it disables the ability to roll forward to the latest patches.</span></span> <span data-ttu-id="740e2-230">Bu değer yalnızca test için önerilir.</span><span class="sxs-lookup"><span data-stu-id="740e2-230">This value is only recommended for testing.</span></span>

<span data-ttu-id="740e2-231">**Devre dışı bırak** ayarının yanı sıra, tüm ayarlar kullanılabilir en yüksek düzeltme eki sürümünü kullanacaktır.</span><span class="sxs-lookup"><span data-stu-id="740e2-231">Besides the **Disable** setting, all settings will use the highest available patch version.</span></span>

### <a name="build-copies-dependencies"></a><span data-ttu-id="740e2-232">Derleme kopyaları bağımlılıkları</span><span class="sxs-lookup"><span data-stu-id="740e2-232">Build copies dependencies</span></span>

<span data-ttu-id="740e2-233">`dotnet build` komutu artık, NuGet önbelleğinden uygulamanızın NuGet bağımlılıklarını yapı çıkış klasörüne kopyalar.</span><span class="sxs-lookup"><span data-stu-id="740e2-233">The `dotnet build` command now copies NuGet dependencies for your application from the NuGet cache to the build output folder.</span></span> <span data-ttu-id="740e2-234">Daha önce bağımlılıklar yalnızca `dotnet publish`bir parçası olarak kopyalandı.</span><span class="sxs-lookup"><span data-stu-id="740e2-234">Previously, dependencies were only copied as part of `dotnet publish`.</span></span>

<span data-ttu-id="740e2-235">Bağlama ve Razor sayfası yayımlama gibi bazı işlemler, yayımlamayı gerektirecek şekilde devam eder.</span><span class="sxs-lookup"><span data-stu-id="740e2-235">There are some operations, like linking and razor page publishing that will still require publishing.</span></span>

### <a name="local-tools"></a><span data-ttu-id="740e2-236">Yerel Araçlar</span><span class="sxs-lookup"><span data-stu-id="740e2-236">Local tools</span></span>

<span data-ttu-id="740e2-237">.NET Core 3.0 yerel araçları tanıtır.</span><span class="sxs-lookup"><span data-stu-id="740e2-237">.NET Core 3.0 introduces local tools.</span></span> <span data-ttu-id="740e2-238">Yerel Araçlar [genel araçlara](../tools/global-tools.md) benzerdir, ancak diskte belirli bir konum ile ilişkilendirilir.</span><span class="sxs-lookup"><span data-stu-id="740e2-238">Local tools are similar to [global tools](../tools/global-tools.md) but are associated with a particular location on disk.</span></span> <span data-ttu-id="740e2-239">Yerel araçlar küresel olarak kullanılabilir değildir ve NuGet paketleri olarak dağıtılır.</span><span class="sxs-lookup"><span data-stu-id="740e2-239">Local tools aren't available globally and are distributed as NuGet packages.</span></span>

> [!WARNING]
> <span data-ttu-id="740e2-240">.NET Core 3,0 Preview 1 ' de `dotnet tool restore` veya `dotnet tool install`çalıştırma gibi yerel araçlar denemediyseniz, yerel araçlar önbellek klasörünü silin.</span><span class="sxs-lookup"><span data-stu-id="740e2-240">If you tried local tools in .NET Core 3.0 Preview 1, such as running `dotnet tool restore` or `dotnet tool install`, delete the local tools cache folder.</span></span> <span data-ttu-id="740e2-241">Aksi takdirde, yerel araçlar yeni bir sürümde çalışmaz.</span><span class="sxs-lookup"><span data-stu-id="740e2-241">Otherwise, local tools won't work on any newer release.</span></span> <span data-ttu-id="740e2-242">Bu klasör şu konumda bulunur:</span><span class="sxs-lookup"><span data-stu-id="740e2-242">This folder is located at:</span></span>
>
> <span data-ttu-id="740e2-243">MacOS 'ta Linux: `rm -r $HOME/.dotnet/toolResolverCache`</span><span class="sxs-lookup"><span data-stu-id="740e2-243">On macOS, Linux: `rm -r $HOME/.dotnet/toolResolverCache`</span></span>
>
> <span data-ttu-id="740e2-244">Windows üzerinde: `rmdir /s %USERPROFILE%\.dotnet\toolResolverCache`</span><span class="sxs-lookup"><span data-stu-id="740e2-244">On Windows: `rmdir /s %USERPROFILE%\.dotnet\toolResolverCache`</span></span>

<span data-ttu-id="740e2-245">Yerel araçlar, geçerli dizininizde `dotnet-tools.json` bir bildirim dosyası adına güvenir.</span><span class="sxs-lookup"><span data-stu-id="740e2-245">Local tools rely on a manifest file name `dotnet-tools.json` in your current directory.</span></span> <span data-ttu-id="740e2-246">Bu bildirim dosyası, bu klasörde ve altında kullanılabilecek araçları tanımlar.</span><span class="sxs-lookup"><span data-stu-id="740e2-246">This manifest file defines the tools to be available at that folder and below.</span></span> <span data-ttu-id="740e2-247">Kodunuzla çalışan herkesin aynı araçları geri yükleyip kullanabilmesini sağlamak için, bildirim dosyasını kodunuzla dağıtabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="740e2-247">You can distribute the manifest file with your code to ensure that anyone who works with your code can restore and use the same tools.</span></span>

<span data-ttu-id="740e2-248">Hem genel hem de yerel araçlar için, çalışma zamanının uyumlu bir sürümü gereklidir.</span><span class="sxs-lookup"><span data-stu-id="740e2-248">For both global and local tools, a compatible version of the runtime is required.</span></span> <span data-ttu-id="740e2-249">Şu anda NuGet.org hedef .NET Core çalışma zamanı 2.1 ' de birçok araç.</span><span class="sxs-lookup"><span data-stu-id="740e2-249">Many tools currently on NuGet.org target .NET Core Runtime 2.1.</span></span> <span data-ttu-id="740e2-250">Bu araçları küresel olarak veya yerel olarak yüklemek için, hala [NET Core 2,1 çalışma zamanını](https://dotnet.microsoft.com/download/dotnet-core/2.1)yüklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="740e2-250">To install these tools globally or locally, you would still need to install the [NET Core 2.1 Runtime](https://dotnet.microsoft.com/download/dotnet-core/2.1).</span></span>

### <a name="new-globaljson-options"></a><span data-ttu-id="740e2-251">Yeni Global. JSON seçenekleri</span><span class="sxs-lookup"><span data-stu-id="740e2-251">New global.json options</span></span>

<span data-ttu-id="740e2-252">*Global. JSON* dosyası, hangi .NET Core SDK sürümünün kullanıldığını tanımlamaya çalışırken daha fazla esneklik sağlayan yeni seçeneklere sahiptir.</span><span class="sxs-lookup"><span data-stu-id="740e2-252">The *global.json* file has new options that provide more flexibility when you're trying to define which version of the .NET Core SDK is used.</span></span> <span data-ttu-id="740e2-253">Yeni seçenekler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="740e2-253">The new options are:</span></span>

- <span data-ttu-id="740e2-254">`allowPrerelease`: SDK Çözümleyicisinin kullanılacak SDK sürümünü seçerken yayın öncesi sürümlerini düşünmesinin gerekip gerekmediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="740e2-254">`allowPrerelease`: Indicates whether the SDK resolver should consider prerelease versions when selecting the SDK version to use.</span></span>
- <span data-ttu-id="740e2-255">`rollForward`: bir SDK sürümü seçerken kullanılacak yuvarlama ilkesini, belirli bir SDK sürümü eksik olduğunda geri dönüş olarak veya daha yüksek bir sürümü kullanmak için bir yönerge olarak gösterir.</span><span class="sxs-lookup"><span data-stu-id="740e2-255">`rollForward`: Indicates the roll-forward policy to use when selecting an SDK version, either as a fallback when a specific SDK version is missing or as a directive to use a higher version.</span></span>

<span data-ttu-id="740e2-256">Varsayılan değerler, desteklenen değerler ve yeni eşleştirme kuralları gibi değişiklikler hakkında daha fazla bilgi için bkz. [Global. JSON genel bakış](../tools/global-json.md).</span><span class="sxs-lookup"><span data-stu-id="740e2-256">For more information about the changes including default values, supported values, and new matching rules, see [global.json overview](../tools/global-json.md).</span></span>

### <a name="smaller-garbage-collection-heap-sizes"></a><span data-ttu-id="740e2-257">Daha küçük atık toplama yığın boyutları</span><span class="sxs-lookup"><span data-stu-id="740e2-257">Smaller Garbage Collection heap sizes</span></span>

<span data-ttu-id="740e2-258">Atık toplayıcısının varsayılan yığın boyutu daha az bellek kullanan .NET Core ile sonuçlanır.</span><span class="sxs-lookup"><span data-stu-id="740e2-258">The Garbage Collector's default heap size has been reduced resulting in .NET Core using less memory.</span></span> <span data-ttu-id="740e2-259">Bu değişiklik, modern işlemci önbelleği boyutları ile nesil 0 ayırma bütçesine göre daha iyi hizalanır.</span><span class="sxs-lookup"><span data-stu-id="740e2-259">This change better aligns with the generation 0 allocation budget with modern processor cache sizes.</span></span>

### <a name="garbage-collection-large-page-support"></a><span data-ttu-id="740e2-260">Çöp toplama büyük sayfa desteği</span><span class="sxs-lookup"><span data-stu-id="740e2-260">Garbage Collection Large Page support</span></span>

<span data-ttu-id="740e2-261">Büyük sayfalar (Linux 'ta çok büyük sayfalar olarak da bilinir), işletim sisteminin bu büyük sayfaları isteyen uygulamanın performansını artırmak için yerel sayfa boyutundan (genellikle 4K) daha büyük bellek bölgeleri ayarlayabildiği bir özelliktir.</span><span class="sxs-lookup"><span data-stu-id="740e2-261">Large Pages (also known as Huge Pages on Linux) is a feature where the operating system is able to establish memory regions larger than the native page size (often 4K) to improve performance of the application requesting these large pages.</span></span>

<span data-ttu-id="740e2-262">Çöp toplayıcı artık Windows üzerinde büyük sayfalar ayırmayı seçmek için bir katılım özelliği olarak **Gclargepages** ayarıyla yapılandırılabilir.</span><span class="sxs-lookup"><span data-stu-id="740e2-262">The Garbage Collector can now be configured with the **GCLargePages** setting as an opt-in feature to choose to allocate large pages on Windows.</span></span>

## <a name="windows-desktop--com"></a><span data-ttu-id="740e2-263">Windows Masaüstü & COM</span><span class="sxs-lookup"><span data-stu-id="740e2-263">Windows Desktop & COM</span></span>

### <a name="net-core-sdk-windows-installer"></a><span data-ttu-id="740e2-264">.NET Core SDK Windows Installer</span><span class="sxs-lookup"><span data-stu-id="740e2-264">.NET Core SDK Windows Installer</span></span>

<span data-ttu-id="740e2-265">Windows için MSI Yükleyicisi, .NET Core 3.0 ile başlayarak değiştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="740e2-265">The MSI installer for Windows has changed starting with .NET Core 3.0.</span></span> <span data-ttu-id="740e2-266">SDK yükleyicileri artık SDK özelliği bant sürümlerini yerinde yükseltecektir.</span><span class="sxs-lookup"><span data-stu-id="740e2-266">The SDK installers will now upgrade SDK feature-band releases in place.</span></span> <span data-ttu-id="740e2-267">Özellik bantları, sürüm numarasının *Patch* bölümündeki *yüzlerce* grupta tanımlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="740e2-267">Feature bands are defined in the *hundreds* groups in the *patch* section of the version number.</span></span> <span data-ttu-id="740e2-268">Örneğin, **3,0. _101_**  ve **3,0. _201_**  , 3,0 sırasında iki farklı özellik bantlarındaki sürümleridir **. _101_**  ve **3,0. _199_**  aynı özellik bandında.</span><span class="sxs-lookup"><span data-stu-id="740e2-268">For example, **3.0._101_** and **3.0._201_** are versions in two different feature bands while **3.0._101_** and **3.0._199_** are in the same feature band.</span></span> <span data-ttu-id="740e2-269">.NET Core SDK **3,0 olduğunda. _101_**  .NET Core SDK yüklendi, **3,0. _100_**  , varsa makineden kaldırılacak.</span><span class="sxs-lookup"><span data-stu-id="740e2-269">And, when .NET Core SDK **3.0._101_** is installed, .NET Core SDK **3.0._100_** will be removed from the machine if it exists.</span></span> <span data-ttu-id="740e2-270">.NET Core SDK **3,0. _200_**  , .NET Core SDK 3,0 ' de aynı makineye yüklendi **. _101_**  kaldırılmaz.</span><span class="sxs-lookup"><span data-stu-id="740e2-270">When .NET Core SDK **3.0._200_** is installed on the same machine, .NET Core SDK **3.0._101_** won't be removed.</span></span>

<span data-ttu-id="740e2-271">Sürüm oluşturma hakkında daha fazla bilgi için bkz. [.NET Core 'un sürümü oluşturma konusuna genel bakış](../versions/index.md).</span><span class="sxs-lookup"><span data-stu-id="740e2-271">For more information about versioning, see [Overview of how .NET Core is versioned](../versions/index.md).</span></span>

### <a name="windows-desktop"></a><span data-ttu-id="740e2-272">Windows masaüstü</span><span class="sxs-lookup"><span data-stu-id="740e2-272">Windows desktop</span></span>

<span data-ttu-id="740e2-273">.NET Core 3.0, Windows Presentation Foundation (WPF) ve Windows Forms kullanarak Windows masaüstü uygulamalarını destekler.</span><span class="sxs-lookup"><span data-stu-id="740e2-273">.NET Core 3.0 supports Windows desktop applications using Windows Presentation Foundation (WPF) and Windows Forms.</span></span> <span data-ttu-id="740e2-274">Bu çerçeveler ayrıca, Windows UI XAML kitaplığı 'ndan (WinUI) [xaml Adaları](/windows/uwp/xaml-platform/xaml-host-controls)aracılığıyla modern denetimleri ve akıcı stil oluşturmayı da destekler.</span><span class="sxs-lookup"><span data-stu-id="740e2-274">These frameworks also support using modern controls and Fluent styling from the Windows UI XAML Library (WinUI) via [XAML islands](/windows/uwp/xaml-platform/xaml-host-controls).</span></span>

<span data-ttu-id="740e2-275">Windows Masaüstü bileşeni, Windows .NET Core 3.0 SDK 'sının bir parçasıdır.</span><span class="sxs-lookup"><span data-stu-id="740e2-275">The Windows Desktop component is part of the Windows .NET Core 3.0 SDK.</span></span>

<span data-ttu-id="740e2-276">Aşağıdaki `dotnet` komutlarla yeni bir WPF veya Windows Forms uygulaması oluşturabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="740e2-276">You can create a new WPF or Windows Forms app with the following `dotnet` commands:</span></span>

```dotnetcli
dotnet new wpf
dotnet new winforms
```

<span data-ttu-id="740e2-277">Visual Studio 2019, .NET Core 3,0 Windows Forms ve WPF için **Yeni proje** şablonları ekler.</span><span class="sxs-lookup"><span data-stu-id="740e2-277">Visual Studio 2019 adds **New Project** templates for .NET Core 3.0 Windows Forms and WPF.</span></span>

<span data-ttu-id="740e2-278">Mevcut bir .NET Framework uygulamasının bağlantı noktası hakkında daha fazla bilgi için bkz. [bağlantı noktası WPF projeleri](../../desktop-wpf/migration/convert-project-from-net-framework.md) ve [bağlantı noktası Windows Forms projeleri](../porting/winforms.md).</span><span class="sxs-lookup"><span data-stu-id="740e2-278">For more information about how to port an existing .NET Framework application, see [Port WPF projects](../../desktop-wpf/migration/convert-project-from-net-framework.md) and [Port Windows Forms projects](../porting/winforms.md).</span></span>

#### <a name="winforms-high-dpi"></a><span data-ttu-id="740e2-279">WinForms yüksek DPı</span><span class="sxs-lookup"><span data-stu-id="740e2-279">WinForms high DPI</span></span>

<span data-ttu-id="740e2-280">.NET Core Windows Forms uygulamaları, <xref:System.Windows.Forms.Application.SetHighDpiMode(System.Windows.Forms.HighDpiMode)?displayProperty=nameWithType>yüksek DPı modunu ayarlayabilir.</span><span class="sxs-lookup"><span data-stu-id="740e2-280">.NET Core Windows Forms applications can set high DPI mode with <xref:System.Windows.Forms.Application.SetHighDpiMode(System.Windows.Forms.HighDpiMode)?displayProperty=nameWithType>.</span></span> <span data-ttu-id="740e2-281">`SetHighDpiMode` yöntemi `Application.Run`önce `App.Manifest` veya P/Invoke gibi başka yollarla ayarlanmamışsa, karşılık gelen yüksek DPı modunu ayarlar.</span><span class="sxs-lookup"><span data-stu-id="740e2-281">The `SetHighDpiMode` method sets the corresponding high DPI mode unless the setting has been set by other means like `App.Manifest` or P/Invoke before `Application.Run`.</span></span>

<span data-ttu-id="740e2-282"><xref:System.Windows.Forms.HighDpiMode?displayProperty=nameWithType> numaralandırmasında gösterildiği gibi olası `highDpiMode` değerleri şunlardır:</span><span class="sxs-lookup"><span data-stu-id="740e2-282">The possible `highDpiMode` values, as expressed by the <xref:System.Windows.Forms.HighDpiMode?displayProperty=nameWithType> enum are:</span></span>

- `DpiUnaware`
- `SystemAware`
- `PerMonitor`
- `PerMonitorV2`
- `DpiUnawareGdiScaled`

<span data-ttu-id="740e2-283">Yüksek DPı modları hakkında daha fazla bilgi için bkz. [Windows 'Da yüksek DPI Masaüstü uygulama geliştirme](/windows/desktop/hidpi/high-dpi-desktop-application-development-on-windows).</span><span class="sxs-lookup"><span data-stu-id="740e2-283">For more information about high DPI modes, see [High DPI Desktop Application Development on Windows](/windows/desktop/hidpi/high-dpi-desktop-application-development-on-windows).</span></span>

### <a name="create-com-components"></a><span data-ttu-id="740e2-284">COM bileşenleri oluşturma</span><span class="sxs-lookup"><span data-stu-id="740e2-284">Create COM components</span></span>

<span data-ttu-id="740e2-285">Windows 'ta artık COM çağrılabilir yönetilen bileşenler oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="740e2-285">On Windows, you can now create COM-callable managed components.</span></span> <span data-ttu-id="740e2-286">Bu özellik, .NET Core 'un COM eklenti modelleriyle kullanılması ve ayrıca .NET Framework eşlik sağlanması açısından önemlidir.</span><span class="sxs-lookup"><span data-stu-id="740e2-286">This capability is critical to use .NET Core with COM add-in models and also to provide parity with .NET Framework.</span></span>

<span data-ttu-id="740e2-287">*Mscoree. dll* ' nin com sunucusu olarak kullanıldığı .NET Framework aksine, .NET Core, com bileşenini oluştururken *bin* dizinine yerel bir başlatıcı dll 'si ekler.</span><span class="sxs-lookup"><span data-stu-id="740e2-287">Unlike .NET Framework where the *mscoree.dll* was used as the COM server, .NET Core will add a native launcher dll to the *bin* directory when you build your COM component.</span></span>

<span data-ttu-id="740e2-288">COM bileşeni oluşturma ve kullanma hakkında bir örnek için bkz. [com tanıtımı](https://github.com/dotnet/samples/tree/master/core/extensions/COMServerDemo).</span><span class="sxs-lookup"><span data-stu-id="740e2-288">For an example of how to create a COM component and consume it, see the [COM Demo](https://github.com/dotnet/samples/tree/master/core/extensions/COMServerDemo).</span></span>

### <a name="windows-native-interop"></a><span data-ttu-id="740e2-289">Windows yerel birlikte çalışma</span><span class="sxs-lookup"><span data-stu-id="740e2-289">Windows Native Interop</span></span>

<span data-ttu-id="740e2-290">Windows, düz C API 'Leri, COM ve WinRT biçiminde zengin bir yerel API sunar.</span><span class="sxs-lookup"><span data-stu-id="740e2-290">Windows offers a rich native API in the form of flat C APIs, COM, and WinRT.</span></span> <span data-ttu-id="740e2-291">.NET Core **P/Invoke**'ı destekleirken, .net Core 3,0, **com API 'Leri oluşturma** ve **WinRT API 'leri etkinleştirme**özelliğini ekler.</span><span class="sxs-lookup"><span data-stu-id="740e2-291">While .NET Core supports **P/Invoke**, .NET Core 3.0 adds the ability to **CoCreate COM APIs** and **Activate WinRT APIs**.</span></span> <span data-ttu-id="740e2-292">Kod örneği için bkz. [Excel tanıtımı](https://github.com/dotnet/samples/tree/master/core/extensions/ExcelDemo).</span><span class="sxs-lookup"><span data-stu-id="740e2-292">For a code example, see the [Excel Demo](https://github.com/dotnet/samples/tree/master/core/extensions/ExcelDemo).</span></span>

### <a name="msix-deployment"></a><span data-ttu-id="740e2-293">MSIX dağıtımı</span><span class="sxs-lookup"><span data-stu-id="740e2-293">MSIX Deployment</span></span>

<span data-ttu-id="740e2-294">[Msix](https://docs.microsoft.com/windows/msix/) yeni bir Windows uygulama paketi biçimidir.</span><span class="sxs-lookup"><span data-stu-id="740e2-294">[MSIX](https://docs.microsoft.com/windows/msix/) is a new Windows application package format.</span></span> <span data-ttu-id="740e2-295">.NET Core 3.0 masaüstü uygulamalarını Windows 10 ' a dağıtmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="740e2-295">It can be used to deploy .NET Core 3.0 desktop applications to Windows 10.</span></span>

<span data-ttu-id="740e2-296">Visual Studio 2019 ' de bulunan [Windows uygulama paketleme projesi](https://docs.microsoft.com/windows/uwp/porting/desktop-to-uwp-packaging-dot-net), [kendi kendine içerilen](../deploying/index.md#publish-self-contained) .NET Core uygulamalarıyla msix paketi oluşturmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="740e2-296">The [Windows Application Packaging Project](https://docs.microsoft.com/windows/uwp/porting/desktop-to-uwp-packaging-dot-net), available in Visual Studio 2019, allows you to create MSIX packages with [self-contained](../deploying/index.md#publish-self-contained) .NET Core applications.</span></span>

<span data-ttu-id="740e2-297">.NET Core proje dosyası `<RuntimeIdentifiers>` özelliğindeki desteklenen çalışma zamanlarını belirtmelidir:</span><span class="sxs-lookup"><span data-stu-id="740e2-297">The .NET Core project file must specify the supported runtimes in the `<RuntimeIdentifiers>` property:</span></span>

```xml
<RuntimeIdentifiers>win-x86;win-x64</RuntimeIdentifiers>
```

## <a name="linux-improvements"></a><span data-ttu-id="740e2-298">Linux geliştirmeleri</span><span class="sxs-lookup"><span data-stu-id="740e2-298">Linux improvements</span></span>

### <a name="serialport-for-linux"></a><span data-ttu-id="740e2-299">Linux için SerialPort</span><span class="sxs-lookup"><span data-stu-id="740e2-299">SerialPort for Linux</span></span>

<span data-ttu-id="740e2-300">.NET Core 3,0, Linux üzerinde <xref:System.IO.Ports.SerialPort?displayProperty=nameWithType> için temel destek sağlar.</span><span class="sxs-lookup"><span data-stu-id="740e2-300">.NET Core 3.0 provides basic support for <xref:System.IO.Ports.SerialPort?displayProperty=nameWithType> on Linux.</span></span>

<span data-ttu-id="740e2-301">Daha önce .NET Core yalnızca Windows üzerinde `SerialPort` kullanılarak desteklenir.</span><span class="sxs-lookup"><span data-stu-id="740e2-301">Previously, .NET Core only supported using `SerialPort` on Windows.</span></span>

<span data-ttu-id="740e2-302">Linux 'ta seri bağlantı noktası için sınırlı destek hakkında daha fazla bilgi için bkz. [GitHub sorun #33146](https://github.com/dotnet/corefx/issues/33146).</span><span class="sxs-lookup"><span data-stu-id="740e2-302">For more information about the limited support for the serial port on Linux, see [GitHub issue #33146](https://github.com/dotnet/corefx/issues/33146).</span></span>

### <a name="docker-and-cgroup-memory-limits"></a><span data-ttu-id="740e2-303">Docker ve cgroup bellek sınırları</span><span class="sxs-lookup"><span data-stu-id="740e2-303">Docker and cgroup memory Limits</span></span>

<span data-ttu-id="740e2-304">Docker ile Linux üzerinde .NET Core 3.0 çalıştırmak, cgroup bellek limitleriyle daha iyi çalışır.</span><span class="sxs-lookup"><span data-stu-id="740e2-304">Running .NET Core 3.0 on Linux with Docker works better with cgroup memory limits.</span></span> <span data-ttu-id="740e2-305">`docker run -m`gibi bellek limitleriyle Docker kapsayıcısını çalıştırmak, .NET Core 'un davranış şeklini değiştirir.</span><span class="sxs-lookup"><span data-stu-id="740e2-305">Running a Docker container with memory limits, such as with `docker run -m`, changes how .NET Core behaves.</span></span>

- <span data-ttu-id="740e2-306">Varsayılan atık toplayıcı (GC) yığın boyutu: kapsayıcıda bellek sınırının en fazla 20 MB veya %75 ' si.</span><span class="sxs-lookup"><span data-stu-id="740e2-306">Default Garbage Collector (GC) heap size: maximum of 20 mb or 75% of the memory limit on the container.</span></span>
- <span data-ttu-id="740e2-307">Açık Boyut, mutlak bir sayı veya cgroup sınırının yüzdesi olarak ayarlanabilir.</span><span class="sxs-lookup"><span data-stu-id="740e2-307">Explicit size can be set as an absolute number or percentage of cgroup limit.</span></span>
- <span data-ttu-id="740e2-308">GC yığını başına en düşük ayrılmış kesim boyutu 16 MB 'tır.</span><span class="sxs-lookup"><span data-stu-id="740e2-308">Minimum reserved segment size per GC heap is 16 mb.</span></span> <span data-ttu-id="740e2-309">Bu boyut, makinelerde oluşturulan Heap sayısını azaltır.</span><span class="sxs-lookup"><span data-stu-id="740e2-309">This size reduces the number of heaps that are created on machines.</span></span>

### <a name="gpio-support-for-raspberry-pi"></a><span data-ttu-id="740e2-310">Raspberry PI için GıO desteği</span><span class="sxs-lookup"><span data-stu-id="740e2-310">GPIO Support for Raspberry Pi</span></span>

<span data-ttu-id="740e2-311">NuGet 'e GıO programlama için kullanabileceğiniz iki paket yayımlanmıştır:</span><span class="sxs-lookup"><span data-stu-id="740e2-311">Two packages have been released to NuGet that you can use for GPIO programming:</span></span>

- [<span data-ttu-id="740e2-312">System. Device. GIO</span><span class="sxs-lookup"><span data-stu-id="740e2-312">System.Device.Gpio</span></span>](https://www.nuget.org/packages/System.Device.Gpio)
- [<span data-ttu-id="740e2-313">IoT. Device. Bindings</span><span class="sxs-lookup"><span data-stu-id="740e2-313">Iot.Device.Bindings</span></span>](https://www.nuget.org/packages/Iot.Device.Bindings)

<span data-ttu-id="740e2-314">GPıO paketleri, *GIO*, *SPI*, *I2C*ve *PWM* cihazları için API 'ler içerir.</span><span class="sxs-lookup"><span data-stu-id="740e2-314">The GPIO packages include APIs for *GPIO*, *SPI*, *I2C*, and *PWM* devices.</span></span> <span data-ttu-id="740e2-315">IoT bağlamaları paketi cihaz bağlamalarını içerir.</span><span class="sxs-lookup"><span data-stu-id="740e2-315">The IoT bindings package includes device bindings.</span></span> <span data-ttu-id="740e2-316">Daha fazla bilgi için bkz. [cihaz GitHub deposu](https://github.com/dotnet/iot/blob/master/src/devices/).</span><span class="sxs-lookup"><span data-stu-id="740e2-316">For more information, see the [devices GitHub repo](https://github.com/dotnet/iot/blob/master/src/devices/).</span></span>

### <a name="arm64-linux-support"></a><span data-ttu-id="740e2-317">ARM64 Linux desteği</span><span class="sxs-lookup"><span data-stu-id="740e2-317">ARM64 Linux support</span></span>

<span data-ttu-id="740e2-318">.NET Core 3.0, Linux için ARM64 desteği ekler.</span><span class="sxs-lookup"><span data-stu-id="740e2-318">.NET Core 3.0 adds support for ARM64 for Linux.</span></span> <span data-ttu-id="740e2-319">ARM64 için birincil kullanım örneği şu anda IoT senaryolarıyla birlikte.</span><span class="sxs-lookup"><span data-stu-id="740e2-319">The primary use case for ARM64 is currently with IoT scenarios.</span></span> <span data-ttu-id="740e2-320">Daha fazla bilgi için bkz. [.NET Core ARM64 Status](https://github.com/dotnet/announcements/issues/82).</span><span class="sxs-lookup"><span data-stu-id="740e2-320">For more information, see [.NET Core ARM64 Status](https://github.com/dotnet/announcements/issues/82).</span></span>

<span data-ttu-id="740e2-321">[ARM64 üzerinde .NET Core Için Docker görüntüleri](https://hub.docker.com/r/microsoft/dotnet/) alp, de, ve Ubuntu için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="740e2-321">[Docker images for .NET Core on ARM64](https://hub.docker.com/r/microsoft/dotnet/) are available for Alpine, Debian, and Ubuntu.</span></span>

> [!NOTE]
> <span data-ttu-id="740e2-322">**ARM64** Windows desteği henüz kullanılamıyor.</span><span class="sxs-lookup"><span data-stu-id="740e2-322">**ARM64** Windows support isn't yet available.</span></span>

## <a name="security"></a><span data-ttu-id="740e2-323">Güvenlik</span><span class="sxs-lookup"><span data-stu-id="740e2-323">Security</span></span>

### <a name="tls-13--openssl-111-on-linux"></a><span data-ttu-id="740e2-324">TLS 1.3 & Linux üzerinde OpenSSL 1.1.1</span><span class="sxs-lookup"><span data-stu-id="740e2-324">TLS 1.3 & OpenSSL 1.1.1 on Linux</span></span>

<span data-ttu-id="740e2-325">.NET Core artık, belirli bir ortamda kullanılabildiği [OpenSSL 1.1.1 Içindeki TLS 1,3 desteğinin](https://www.openssl.org/blog/blog/2018/09/11/release111/)avantajlarından yararlanır.</span><span class="sxs-lookup"><span data-stu-id="740e2-325">.NET Core now takes advantage of [TLS 1.3 support in OpenSSL 1.1.1](https://www.openssl.org/blog/blog/2018/09/11/release111/), when it's available in a given environment.</span></span> <span data-ttu-id="740e2-326">TLS 1.3:</span><span class="sxs-lookup"><span data-stu-id="740e2-326">With TLS 1.3:</span></span>

- <span data-ttu-id="740e2-327">İstemci ve sunucu arasında gereken azaltılan gidiş dönüşlerle bağlantı süreleri geliştirildi.</span><span class="sxs-lookup"><span data-stu-id="740e2-327">Connection times are improved with reduced round trips required between the client and server.</span></span>
- <span data-ttu-id="740e2-328">Kullanılmayan ve güvenli olmayan şifreleme algoritmalarının kaldırılması nedeniyle güvenlik geliştirildi.</span><span class="sxs-lookup"><span data-stu-id="740e2-328">Improved security because of the removal of various obsolete and insecure cryptographic algorithms.</span></span>

<span data-ttu-id="740e2-329">Kullanılabilir olduğunda, .NET Core 3,0 bir Linux sisteminde **OpenSSL 1.1.1**, **OpenSSL 1.1.0**veya **OpenSSL 1.0.2** kullanır.</span><span class="sxs-lookup"><span data-stu-id="740e2-329">When available, .NET Core 3.0 uses **OpenSSL 1.1.1**, **OpenSSL 1.1.0**, or **OpenSSL 1.0.2** on a Linux system.</span></span> <span data-ttu-id="740e2-330">**OpenSSL 1.1.1** kullanılabilir olduğunda, hem <xref:System.Net.Security.SslStream?displayProperty=nameWithType> hem de <xref:System.Net.Http.HttpClient?displayProperty=nameWithType> türleri **TLS 1,3** kullanır (istemci ve sunucunun **TLS 1,3**' i desteklediği varsayılır).</span><span class="sxs-lookup"><span data-stu-id="740e2-330">When **OpenSSL 1.1.1** is available, both <xref:System.Net.Security.SslStream?displayProperty=nameWithType> and <xref:System.Net.Http.HttpClient?displayProperty=nameWithType> types will use **TLS 1.3** (assuming both the client and server support **TLS 1.3**).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="740e2-331">Windows ve macOS henüz **TLS 1,3**' i desteklemez.</span><span class="sxs-lookup"><span data-stu-id="740e2-331">Windows and macOS do not yet support **TLS 1.3**.</span></span> <span data-ttu-id="740e2-332">.NET Core 3,0, destek kullanılabilir hale geldiğinde bu işletim sistemlerinde **TLS 1,3** ' i destekleyecektir.</span><span class="sxs-lookup"><span data-stu-id="740e2-332">.NET Core 3.0 will support **TLS 1.3** on these operating systems when support becomes available.</span></span>

<span data-ttu-id="740e2-333">Aşağıdaki C# 8,0 örneği, <https://www.cloudflare.com>bağlanan Ubuntu 18,10 üzerinde .net Core 3,0 ' i göstermektedir:</span><span class="sxs-lookup"><span data-stu-id="740e2-333">The following C# 8.0 example demonstrates .NET Core 3.0 on Ubuntu 18.10 connecting to <https://www.cloudflare.com>:</span></span>

[!code-csharp[TLSExample](~/samples/snippets/core/whats-new/whats-new-in-30/cs/TLS.cs#TLS)]

### <a name="cryptography-ciphers"></a><span data-ttu-id="740e2-334">Şifreleme şifrelemeleri</span><span class="sxs-lookup"><span data-stu-id="740e2-334">Cryptography ciphers</span></span>

<span data-ttu-id="740e2-335">.NET 3,0, sırasıyla <xref:System.Security.Cryptography.AesGcm?displayProperty=nameWithType> ve <xref:System.Security.Cryptography.AesCcm?displayProperty=nameWithType> ile uygulanan **AES-GCM** ve **AES-CCM** şifrelemeleri için destek ekler.</span><span class="sxs-lookup"><span data-stu-id="740e2-335">.NET 3.0 adds support for **AES-GCM** and **AES-CCM** ciphers, implemented with <xref:System.Security.Cryptography.AesGcm?displayProperty=nameWithType> and <xref:System.Security.Cryptography.AesCcm?displayProperty=nameWithType> respectively.</span></span> <span data-ttu-id="740e2-336">Bu algoritmalar, [Ilişki verileri (AEAD) algoritmalarıyla kimliği doğrulanmış şifrelemedir](https://en.wikipedia.org/wiki/Authenticated_encryption).</span><span class="sxs-lookup"><span data-stu-id="740e2-336">These algorithms are both [Authenticated Encryption with Association Data (AEAD) algorithms](https://en.wikipedia.org/wiki/Authenticated_encryption).</span></span>

<span data-ttu-id="740e2-337">Aşağıdaki kod, rastgele verileri şifrelemek ve şifrelerini çözmek için `AesGcm` şifre kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="740e2-337">The following code demonstrates using `AesGcm` cipher to encrypt and decrypt random data.</span></span>

[!code-csharp[AesGcm](~/samples/snippets/core/whats-new/whats-new-in-30/cs/Cipher.cs#AesGcm)]

### <a name="cryptographic-key-importexport"></a><span data-ttu-id="740e2-338">Şifreleme anahtarı Içeri/dışarı aktarma</span><span class="sxs-lookup"><span data-stu-id="740e2-338">Cryptographic Key Import/Export</span></span>

<span data-ttu-id="740e2-339">.NET Core 3.0, asimetrik ortak ve özel anahtarların standart biçimlerden içeri ve dışarı aktarılmasını destekler.</span><span class="sxs-lookup"><span data-stu-id="740e2-339">.NET Core 3.0 supports the import and export of asymmetric public and private keys from standard formats.</span></span> <span data-ttu-id="740e2-340">X. 509.440 sertifikası kullanmanız gerekmez.</span><span class="sxs-lookup"><span data-stu-id="740e2-340">You don't need to use an X.509 certificate.</span></span>

<span data-ttu-id="740e2-341">*RSA*, *dsa*, *ECDSA*ve *ecdıfıfiehellman*gibi tüm anahtar türleri aşağıdaki biçimleri destekler:</span><span class="sxs-lookup"><span data-stu-id="740e2-341">All key types, such as *RSA*, *DSA*, *ECDsa*, and *ECDiffieHellman*, support the following formats:</span></span>

- <span data-ttu-id="740e2-342">**Ortak anahtar**</span><span class="sxs-lookup"><span data-stu-id="740e2-342">**Public Key**</span></span>
  - <span data-ttu-id="740e2-343">X. 509.440 Subjectpublickeyınfo</span><span class="sxs-lookup"><span data-stu-id="740e2-343">X.509 SubjectPublicKeyInfo</span></span>

- <span data-ttu-id="740e2-344">**Özel anahtar**</span><span class="sxs-lookup"><span data-stu-id="740e2-344">**Private key**</span></span>
  - <span data-ttu-id="740e2-345">PKCS # 8 Privatekeyınfo</span><span class="sxs-lookup"><span data-stu-id="740e2-345">PKCS#8 PrivateKeyInfo</span></span>
  - <span data-ttu-id="740e2-346">PKCS # 8 Encryptedprivatekeyınfo</span><span class="sxs-lookup"><span data-stu-id="740e2-346">PKCS#8 EncryptedPrivateKeyInfo</span></span>

<span data-ttu-id="740e2-347">RSA anahtarları da şunları destekler:</span><span class="sxs-lookup"><span data-stu-id="740e2-347">RSA keys also support:</span></span>

- <span data-ttu-id="740e2-348">**Ortak anahtar**</span><span class="sxs-lookup"><span data-stu-id="740e2-348">**Public Key**</span></span>
  - <span data-ttu-id="740e2-349">PKCS # 1 RSAPublicKey</span><span class="sxs-lookup"><span data-stu-id="740e2-349">PKCS#1 RSAPublicKey</span></span>

- <span data-ttu-id="740e2-350">**Özel anahtar**</span><span class="sxs-lookup"><span data-stu-id="740e2-350">**Private key**</span></span>
  - <span data-ttu-id="740e2-351">PKCS # 1 RSAPrivateKey</span><span class="sxs-lookup"><span data-stu-id="740e2-351">PKCS#1 RSAPrivateKey</span></span>

<span data-ttu-id="740e2-352">Dışarı aktarma yöntemleri DER kodlu ikili veriler oluşturur ve içeri aktarma yöntemleri aynı şekilde bekler.</span><span class="sxs-lookup"><span data-stu-id="740e2-352">The export methods produce DER-encoded binary data, and the import methods expect the same.</span></span> <span data-ttu-id="740e2-353">Bir anahtar, metin kullanımı kolay pek biçiminde depolanıyorsa, bir içeri aktarma yöntemi çağrılmadan önce çağıranın içerik Base64 olarak çözülmesi gerekecektir.</span><span class="sxs-lookup"><span data-stu-id="740e2-353">If a key is stored in the text-friendly PEM format, the caller will need to base64-decode the content before calling an import method.</span></span>

[!code-csharp[RSA](~/samples/snippets/core/whats-new/whats-new-in-30/cs/RSA.cs#Rsa)]

<span data-ttu-id="740e2-354">**PKCS # 8** dosyaları <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo?displayProperty=nameWithType> ile incelenebilir ve **PFX/PKCS # 12** dosyaları <xref:System.Security.Cryptography.Pkcs.Pkcs12Info?displayProperty=nameWithType>ile incelenebilir.</span><span class="sxs-lookup"><span data-stu-id="740e2-354">**PKCS#8** files can be inspected with <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo?displayProperty=nameWithType> and **PFX/PKCS#12** files can be inspected with <xref:System.Security.Cryptography.Pkcs.Pkcs12Info?displayProperty=nameWithType>.</span></span> <span data-ttu-id="740e2-355">**PFX/PKCS # 12** dosyaları <xref:System.Security.Cryptography.Pkcs.Pkcs12Builder?displayProperty=nameWithType>ile yönetilebilir.</span><span class="sxs-lookup"><span data-stu-id="740e2-355">**PFX/PKCS#12** files can be manipulated with <xref:System.Security.Cryptography.Pkcs.Pkcs12Builder?displayProperty=nameWithType>.</span></span>

## <a name="net-core-30-api-changes"></a><span data-ttu-id="740e2-356">.NET Core 3,0 API değişiklikleri</span><span class="sxs-lookup"><span data-stu-id="740e2-356">.NET Core 3.0 API changes</span></span>

### <a name="ranges-and-indices"></a><span data-ttu-id="740e2-357">Aralıklar ve dizinler</span><span class="sxs-lookup"><span data-stu-id="740e2-357">Ranges and indices</span></span>

<span data-ttu-id="740e2-358">Yeni <xref:System.Index?displayProperty=nameWithType> türü dizin oluşturmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="740e2-358">The new <xref:System.Index?displayProperty=nameWithType> type can be used for indexing.</span></span> <span data-ttu-id="740e2-359">Baştan itibaren sayı olan bir `int` veya sonuna kadar olan önek `^` işleci (C#) ile bir tane oluşturabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="740e2-359">You can create one from an `int` that counts from the beginning, or with a prefix `^` operator (C#) that counts from the end:</span></span>

```csharp
Index i1 = 3;  // number 3 from beginning
Index i2 = ^4; // number 4 from end
int[] a = { 0, 1, 2, 3, 4, 5, 6, 7, 8, 9 };
Console.WriteLine($"{a[i1]}, {a[i2]}"); // "3, 6"
```

<span data-ttu-id="740e2-360">Ayrıca, biri başlangıç ve diğeri son için olmak üzere iki `Index` değerinden oluşan <xref:System.Range?displayProperty=nameWithType> türü de vardır ve bir `x..y` Range ifadesiyle (C#) yazılabilir.</span><span class="sxs-lookup"><span data-stu-id="740e2-360">There's also the <xref:System.Range?displayProperty=nameWithType> type, which consists of two `Index` values, one for the start and one for the end, and can be written with a `x..y` range expression (C#).</span></span> <span data-ttu-id="740e2-361">Daha sonra bir dilim üreten `Range`dizin oluşturabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="740e2-361">You can then index with a `Range`, which produces a slice:</span></span>

```csharp
var slice = a[i1..i2]; // { 3, 4, 5 }
```

<span data-ttu-id="740e2-362">Daha fazla bilgi için [aralıklar ve dizinler öğreticisine](../../csharp/tutorials/ranges-indexes.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="740e2-362">For more information, see the [ranges and indices tutorial](../../csharp/tutorials/ranges-indexes.md).</span></span>

### <a name="async-streams"></a><span data-ttu-id="740e2-363">Zaman uyumsuz akışlar</span><span class="sxs-lookup"><span data-stu-id="740e2-363">Async streams</span></span>

<span data-ttu-id="740e2-364"><xref:System.Collections.Generic.IAsyncEnumerable%601> türü, <xref:System.Collections.Generic.IEnumerable%601>yeni bir zaman uyumsuz sürümüdür.</span><span class="sxs-lookup"><span data-stu-id="740e2-364">The <xref:System.Collections.Generic.IAsyncEnumerable%601> type is a new asynchronous version of <xref:System.Collections.Generic.IEnumerable%601>.</span></span> <span data-ttu-id="740e2-365">Dil, öğelerini tüketmek için `IAsyncEnumerable<T>` `await foreach` ve öğeleri oluşturmak için `yield return` kullanmayı sağlar.</span><span class="sxs-lookup"><span data-stu-id="740e2-365">The language lets you `await foreach` over `IAsyncEnumerable<T>` to consume their elements, and use `yield return` to them to produce elements.</span></span>

<span data-ttu-id="740e2-366">Aşağıdaki örnek, zaman uyumsuz akışların hem üretimini hem de tüketimini gösterir.</span><span class="sxs-lookup"><span data-stu-id="740e2-366">The following example demonstrates both production and consumption of async streams.</span></span> <span data-ttu-id="740e2-367">`foreach` deyimleri zaman uyumsuz ve kendisi çağıranlar için zaman uyumsuz akış üretmek için `yield return` kullanır.</span><span class="sxs-lookup"><span data-stu-id="740e2-367">The `foreach` statement is async and itself uses `yield return` to produce an async stream for callers.</span></span> <span data-ttu-id="740e2-368">Bu model (`yield return`kullanarak), zaman uyumsuz akışlar üretmek için önerilen modeldir.</span><span class="sxs-lookup"><span data-stu-id="740e2-368">This pattern (using `yield return`) is the recommended model for producing async streams.</span></span>

```csharp
async IAsyncEnumerable<int> GetBigResultsAsync()
{
    await foreach (var result in GetResultsAsync())
    {
        if (result > 20) yield return result;
    }
}
```

<span data-ttu-id="740e2-369">`await foreach`Ayrıca, zaman uyumsuz yineleyiciler oluşturabilirsiniz, örneğin, hem `await` hem de `yield` `IAsyncEnumerable/IAsyncEnumerator` döndüren bir yineleyici.</span><span class="sxs-lookup"><span data-stu-id="740e2-369">In addition to being able to `await foreach`, you can also create async iterators, for example, an iterator that returns an `IAsyncEnumerable/IAsyncEnumerator` that you can both `await` and `yield` in.</span></span> <span data-ttu-id="740e2-370">Atılmalıdır nesneler için, `Stream` ve `Timer`gibi çeşitli BCL türlerini uygulayan `IAsyncDisposable`kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="740e2-370">For objects that need to be disposed, you can use `IAsyncDisposable`, which various BCL types implement, such as `Stream` and `Timer`.</span></span>

<span data-ttu-id="740e2-371">Daha fazla bilgi için bkz. [zaman uyumsuz akışlar öğreticisi](../../csharp/tutorials/generate-consume-asynchronous-stream.md).</span><span class="sxs-lookup"><span data-stu-id="740e2-371">For more information, see the [async streams tutorial](../../csharp/tutorials/generate-consume-asynchronous-stream.md).</span></span>

### <a name="ieee-floating-point"></a><span data-ttu-id="740e2-372">IEEE kayan nokta</span><span class="sxs-lookup"><span data-stu-id="740e2-372">IEEE Floating-point</span></span>

<span data-ttu-id="740e2-373">Kayan nokta API 'Leri, [ıeee 754-2008 düzeltmesine](https://en.wikipedia.org/wiki/IEEE_754-2008_revision)uymak üzere güncelleştiriliyor.</span><span class="sxs-lookup"><span data-stu-id="740e2-373">Floating point APIs are being updated to comply with [IEEE 754-2008 revision](https://en.wikipedia.org/wiki/IEEE_754-2008_revision).</span></span> <span data-ttu-id="740e2-374">Bu değişikliklerin amacı, tüm **gerekli** işlemleri kullanıma sunmaktır ve DAVRANıŞSAL 'in IEEE spec ile uyumlu olduklarından emin olmaktır. Kayan nokta iyileştirmeleri hakkında daha fazla bilgi için bkz. [.NET Core 3,0 blog gönderisine kayan nokta ayrıştırma ve biçimlendirme geliştirmeleri](https://devblogs.microsoft.com/dotnet/floating-point-parsing-and-formatting-improvements-in-net-core-3-0/) .</span><span class="sxs-lookup"><span data-stu-id="740e2-374">The goal of these changes is to expose all **required** operations and ensure that they're behaviorally compliant with the IEEE spec. For more information about floating-point improvements, see the [Floating-Point Parsing and Formatting improvements in .NET Core 3.0](https://devblogs.microsoft.com/dotnet/floating-point-parsing-and-formatting-improvements-in-net-core-3-0/) blog post.</span></span>

<span data-ttu-id="740e2-375">Ayrıştırma ve biçimlendirme düzeltmeleri şunları içerir:</span><span class="sxs-lookup"><span data-stu-id="740e2-375">Parsing and formatting fixes include:</span></span>

- <span data-ttu-id="740e2-376">Her uzunlukta doğru şekilde ayrıştırma ve yuvarlama girişleri.</span><span class="sxs-lookup"><span data-stu-id="740e2-376">Correctly parse and round inputs of any length.</span></span>
- <span data-ttu-id="740e2-377">Doğru şekilde ayrıştırır ve negatif sıfır biçimlendirir.</span><span class="sxs-lookup"><span data-stu-id="740e2-377">Correctly parse and format negative zero.</span></span>
- <span data-ttu-id="740e2-378">Büyük/küçük harfe duyarsız bir denetim yaparak `Infinity` ve `NaN` doğru bir şekilde ayrıştırarak uygun yerlerde daha önce isteğe bağlı bir `+` sağlar.</span><span class="sxs-lookup"><span data-stu-id="740e2-378">Correctly parse `Infinity` and `NaN` by doing a case-insensitive check and allowing an optional preceding `+` where applicable.</span></span>

<span data-ttu-id="740e2-379">Yeni <xref:System.Math?displayProperty=nameWithType> API 'Leri şunlardır:</span><span class="sxs-lookup"><span data-stu-id="740e2-379">New <xref:System.Math?displayProperty=nameWithType> APIs include:</span></span>

- <span data-ttu-id="740e2-380"><xref:System.Math.BitIncrement(System.Double)> ve <xref:System.Math.BitDecrement(System.Double)></span><span class="sxs-lookup"><span data-stu-id="740e2-380"><xref:System.Math.BitIncrement(System.Double)> and <xref:System.Math.BitDecrement(System.Double)></span></span>\
<span data-ttu-id="740e2-381">`nextUp` ve `nextDown` IEEE işlemlerine karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="740e2-381">Corresponds to the `nextUp` and `nextDown` IEEE operations.</span></span> <span data-ttu-id="740e2-382">Bunlar, girdiden daha büyük veya daha az (sırasıyla) karşılaştıran en küçük kayan nokta numarasını döndürür.</span><span class="sxs-lookup"><span data-stu-id="740e2-382">They return the smallest floating-point number that compares greater or lesser than the input (respectively).</span></span> <span data-ttu-id="740e2-383">Örneğin, `Math.BitIncrement(0.0)` `double.Epsilon`döndürür.</span><span class="sxs-lookup"><span data-stu-id="740e2-383">For example, `Math.BitIncrement(0.0)` would return `double.Epsilon`.</span></span>

- <span data-ttu-id="740e2-384"><xref:System.Math.MaxMagnitude(System.Double,System.Double)> ve <xref:System.Math.MinMagnitude(System.Double,System.Double)></span><span class="sxs-lookup"><span data-stu-id="740e2-384"><xref:System.Math.MaxMagnitude(System.Double,System.Double)> and <xref:System.Math.MinMagnitude(System.Double,System.Double)></span></span>\
<span data-ttu-id="740e2-385">`maxNumMag` ve `minNumMag` IEEE işlemlerine karşılık gelir, iki girişin (sırasıyla) büyüklüğüne eşit veya daha küçük olan değeri döndürür.</span><span class="sxs-lookup"><span data-stu-id="740e2-385">Corresponds to the `maxNumMag` and `minNumMag` IEEE operations, they return the value that is greater or lesser in magnitude of the two inputs (respectively).</span></span> <span data-ttu-id="740e2-386">Örneğin, `Math.MaxMagnitude(2.0, -3.0)` `-3.0`döndürür.</span><span class="sxs-lookup"><span data-stu-id="740e2-386">For example, `Math.MaxMagnitude(2.0, -3.0)` would return `-3.0`.</span></span>

- <xref:System.Math.ILogB(System.Double)>\
<span data-ttu-id="740e2-387">Bir integral değer döndüren `logB` IEEE işlemine karşılık gelir, giriş parametresinin tamsayı tabanı 2 günlüğünü döndürür.</span><span class="sxs-lookup"><span data-stu-id="740e2-387">Corresponds to the `logB` IEEE operation that returns an integral value, it returns the integral base-2 log of the input parameter.</span></span> <span data-ttu-id="740e2-388">Bu yöntem `floor(log2(x))`ile aynı şekilde, ancak en az yuvarlama hatasıyla yapılır.</span><span class="sxs-lookup"><span data-stu-id="740e2-388">This method is effectively the same as `floor(log2(x))`, but done with minimal rounding error.</span></span>

- <xref:System.Math.ScaleB(System.Double,System.Int32)>\
<span data-ttu-id="740e2-389">Tamsayı değer alan `scaleB` IEEE işlemine karşılık gelir, etkin `x * pow(2, n)`döndürür, ancak en az yuvarlama hatasıyla yapılır.</span><span class="sxs-lookup"><span data-stu-id="740e2-389">Corresponds to the `scaleB` IEEE operation that takes an integral value, it returns effectively `x * pow(2, n)`, but is done with minimal rounding error.</span></span>

- <xref:System.Math.Log2(System.Double)>\
<span data-ttu-id="740e2-390">`log2` IEEE işlemine karşılık gelen, Base-2 logaritmasını döndürür.</span><span class="sxs-lookup"><span data-stu-id="740e2-390">Corresponds to the `log2` IEEE operation, it returns the base-2 logarithm.</span></span> <span data-ttu-id="740e2-391">Yuvarlama hatasını en aza indirir.</span><span class="sxs-lookup"><span data-stu-id="740e2-391">It minimizes rounding error.</span></span>

- <xref:System.Math.FusedMultiplyAdd(System.Double,System.Double,System.Double)>\
<span data-ttu-id="740e2-392">`fma` IEEE işlemine karşılık gelir, bir fkullanılan çarpma eklemesi gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="740e2-392">Corresponds to the `fma` IEEE operation, it performs a fused multiply add.</span></span> <span data-ttu-id="740e2-393">Yani, tek bir işlem olarak `(x * y) + z`, böylece yuvarlama hatasını en aza indirir.</span><span class="sxs-lookup"><span data-stu-id="740e2-393">That is, it does `(x * y) + z` as a single operation, thereby minimizing the rounding error.</span></span> <span data-ttu-id="740e2-394">Örnek, `1e308`döndüren `FusedMultiplyAdd(1e308, 2.0, -1e308)`.</span><span class="sxs-lookup"><span data-stu-id="740e2-394">An example is `FusedMultiplyAdd(1e308, 2.0, -1e308)`, which returns `1e308`.</span></span> <span data-ttu-id="740e2-395">Normal `(1e308 * 2.0) - 1e308` `double.PositiveInfinity`döndürür.</span><span class="sxs-lookup"><span data-stu-id="740e2-395">The regular `(1e308 * 2.0) - 1e308` returns `double.PositiveInfinity`.</span></span>

- <xref:System.Math.CopySign(System.Double,System.Double)>\
<span data-ttu-id="740e2-396">`copySign` IEEE işlemine karşılık gelen `x`değerini, ancak `y`işaretini döndürür.</span><span class="sxs-lookup"><span data-stu-id="740e2-396">Corresponds to the `copySign` IEEE operation, it returns the value of `x`, but with the sign of `y`.</span></span>

### <a name="net-platform-dependent-intrinsics"></a><span data-ttu-id="740e2-397">.NET platforma bağımlı Iç bilgiler</span><span class="sxs-lookup"><span data-stu-id="740e2-397">.NET Platform-Dependent Intrinsics</span></span>

<span data-ttu-id="740e2-398">**SIMD** veya **bit işleme yönergesi** kümeleri gıbı belirli performans yönelimli CPU yönergelerine erişime izin veren API 'ler eklenmiştir.</span><span class="sxs-lookup"><span data-stu-id="740e2-398">APIs have been added that allow access to certain perf-oriented CPU instructions, such as the **SIMD** or **Bit Manipulation instruction** sets.</span></span> <span data-ttu-id="740e2-399">Bu yönergeler, verileri paralel şekilde işleme gibi belirli senaryolarda önemli performans geliştirmeleri elde etmenize yardımcı olabilir.</span><span class="sxs-lookup"><span data-stu-id="740e2-399">These instructions can help achieve significant performance improvements in certain scenarios, such as processing data efficiently in parallel.</span></span>

<span data-ttu-id="740e2-400">Uygun durumlarda, .NET kitaplıkları performansı artırmak için bu yönergeleri kullanmaya başlamıştır.</span><span class="sxs-lookup"><span data-stu-id="740e2-400">Where appropriate, the .NET libraries have begun using these instructions to improve performance.</span></span>

<span data-ttu-id="740e2-401">Daha fazla bilgi için bkz. [.NET platformu bağımlı iç](https://github.com/dotnet/designs/blob/master/accepted/platform-intrinsics.md)öğeleri.</span><span class="sxs-lookup"><span data-stu-id="740e2-401">For more information, see [.NET Platform Dependent Intrinsics](https://github.com/dotnet/designs/blob/master/accepted/platform-intrinsics.md).</span></span>

### <a name="improved-net-core-version-apis"></a><span data-ttu-id="740e2-402">Geliştirilmiş .NET Core sürümü API 'Leri</span><span class="sxs-lookup"><span data-stu-id="740e2-402">Improved .NET Core Version APIs</span></span>

<span data-ttu-id="740e2-403">.NET Core 3.0 ile başlayarak, .NET Core ile birlikte sunulan sürüm API 'Leri artık istediğiniz bilgileri döndürür.</span><span class="sxs-lookup"><span data-stu-id="740e2-403">Starting with .NET Core 3.0, the version APIs provided with .NET Core now return the information you expect.</span></span> <span data-ttu-id="740e2-404">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="740e2-404">For example:</span></span>

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
// New result (notice the value includes any preview release information)
//   RuntimeInformation.FrameworkDescription: .NET Core 3.0.0-preview4-27615-11
```

> [!WARNING]
> <span data-ttu-id="740e2-405">Son değişiklik.</span><span class="sxs-lookup"><span data-stu-id="740e2-405">Breaking change.</span></span> <span data-ttu-id="740e2-406">Bu teknik açıdan önemli bir değişiklik olduğundan, sürüm oluşturma düzeni değişti.</span><span class="sxs-lookup"><span data-stu-id="740e2-406">This is technically a breaking change because the versioning scheme has changed.</span></span>

### <a name="fast-built-in-json-support"></a><span data-ttu-id="740e2-407">Hızlı yerleşik JSON desteği</span><span class="sxs-lookup"><span data-stu-id="740e2-407">Fast built-in JSON support</span></span>

<span data-ttu-id="740e2-408">.NET Kullanıcıları [Newtonsoft. JSON](https://www.newtonsoft.com/json) ve DIĞER popüler JSON kitaplıklarına büyük ölçüde güvendi ve bu da iyi seçimler olmaya devam eder.</span><span class="sxs-lookup"><span data-stu-id="740e2-408">.NET users have largely relied on [Newtonsoft.Json](https://www.newtonsoft.com/json) and other popular JSON libraries, which continue to be good choices.</span></span> <span data-ttu-id="740e2-409">`Newtonsoft.Json`, temel veri türü olarak .NET dizelerini kullanır, bu da arada bulunan UTF-16 ' dır.</span><span class="sxs-lookup"><span data-stu-id="740e2-409">`Newtonsoft.Json` uses .NET strings as its base datatype, which is UTF-16 under the hood.</span></span>

<span data-ttu-id="740e2-410">Yeni yerleşik JSON desteği yüksek performanslı, düşük ayırma, UTF-8 kodlu JSON metniyle birlikte çalışıyor.</span><span class="sxs-lookup"><span data-stu-id="740e2-410">The new built-in JSON support is high-performance, low allocation, and works with UTF-8 encoded JSON text.</span></span> <span data-ttu-id="740e2-411"><xref:System.Text.Json> ad alanı ve türleri hakkında daha fazla bilgi için aşağıdaki makalelere bakın:</span><span class="sxs-lookup"><span data-stu-id="740e2-411">For more information about the <xref:System.Text.Json> namespace and types, see the following articles:</span></span>

* [<span data-ttu-id="740e2-412">.NET 'te JSON serileştirme-genel bakış</span><span class="sxs-lookup"><span data-stu-id="740e2-412">JSON serialization in .NET - overview</span></span>](../../standard/serialization/system-text-json-overview.md)
* <span data-ttu-id="740e2-413">[.Net 'TE JSON serileştirmek ve serisini kaldırma](../../standard/serialization/system-text-json-how-to.md).</span><span class="sxs-lookup"><span data-stu-id="740e2-413">[How to serialize and deserialize JSON in .NET](../../standard/serialization/system-text-json-how-to.md).</span></span>
* [<span data-ttu-id="740e2-414">Newtonsoft. JSON 'dan System. Text. JSON 'a geçiş</span><span class="sxs-lookup"><span data-stu-id="740e2-414">How to migrate from Newtonsoft.Json to System.Text.Json</span></span>](../../standard/serialization/system-text-json-migrate-from-newtonsoft-how-to.md)

### <a name="http2-support"></a><span data-ttu-id="740e2-415">HTTP/2 desteği</span><span class="sxs-lookup"><span data-stu-id="740e2-415">HTTP/2 support</span></span>

<span data-ttu-id="740e2-416"><xref:System.Net.Http.HttpClient?displayProperty=nameWithType> türü HTTP/2 protokolünü destekler.</span><span class="sxs-lookup"><span data-stu-id="740e2-416">The <xref:System.Net.Http.HttpClient?displayProperty=nameWithType> type supports the HTTP/2 protocol.</span></span> <span data-ttu-id="740e2-417">HTTP/2 etkinse HTTP protokol sürümü TLS/ALPN aracılığıyla görüşülür ve sunucunun bunu kullanabilmesi durumunda HTTP/2 kullanılır.</span><span class="sxs-lookup"><span data-stu-id="740e2-417">If HTTP/2 is enabled, the HTTP protocol version is negotiated via TLS/ALPN, and HTTP/2 is used if the server elects to use it.</span></span>

<span data-ttu-id="740e2-418">Varsayılan protokol HTTP/1.1 olarak kalır, ancak HTTP/2 iki farklı şekilde etkinleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="740e2-418">The default protocol remains HTTP/1.1, but HTTP/2 can be enabled in two different ways.</span></span> <span data-ttu-id="740e2-419">İlk olarak http istek iletisini HTTP/2 kullanacak şekilde ayarlayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="740e2-419">First, you can set the HTTP request message to use HTTP/2:</span></span>

[!code-csharp[Http2Request](~/samples/snippets/core/whats-new/whats-new-in-30/cs/http.cs#Request)]

<span data-ttu-id="740e2-420">İkinci olarak, <xref:System.Net.Http.HttpClient> varsayılan olarak HTTP/2 kullanacak şekilde değiştirebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="740e2-420">Second, you can change <xref:System.Net.Http.HttpClient> to use HTTP/2 by default:</span></span>

[!code-csharp[Http2Client](~/samples/snippets/core/whats-new/whats-new-in-30/cs/http.cs#Client)]

<span data-ttu-id="740e2-421">Uygulama geliştirirken birçok kez şifrelenmemiş bağlantı kullanmak istersiniz.</span><span class="sxs-lookup"><span data-stu-id="740e2-421">Many times when you're developing an application, you want to use an unencrypted connection.</span></span> <span data-ttu-id="740e2-422">Hedef uç noktanın HTTP/2 kullanacağınızı biliyorsanız, HTTP/2 için şifrelenmemiş bağlantıları açabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="740e2-422">If you know the target endpoint will be using HTTP/2, you can turn on unencrypted connections for HTTP/2.</span></span> <span data-ttu-id="740e2-423">`DOTNET_SYSTEM_NET_HTTP_SOCKETSHTTPHANDLER_HTTP2UNENCRYPTEDSUPPORT` ortam değişkenini `1` ya da uygulama bağlamında etkinleştirerek etkinleştirebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="740e2-423">You can turn it on by setting the `DOTNET_SYSTEM_NET_HTTP_SOCKETSHTTPHANDLER_HTTP2UNENCRYPTEDSUPPORT` environment variable to `1` or by enabling it in the app context:</span></span>

[!code-csharp[Http2Context](~/samples/snippets/core/whats-new/whats-new-in-30/cs/http.cs#AppContext)]

## <a name="next-steps"></a><span data-ttu-id="740e2-424">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="740e2-424">Next steps</span></span>

- [<span data-ttu-id="740e2-425">.NET Core 2,2 ve 3,0 arasındaki son değişiklikleri gözden geçirin.</span><span class="sxs-lookup"><span data-stu-id="740e2-425">Review the breaking changes between .NET Core 2.2 and 3.0.</span></span>](../compatibility/2.2-3.0.md)
- [<span data-ttu-id="740e2-426">Windows Forms uygulamalar için .NET Core 3,0 'deki son değişiklikleri gözden geçirin.</span><span class="sxs-lookup"><span data-stu-id="740e2-426">Review the breaking changes in .NET Core 3.0 for Windows Forms apps.</span></span>](../compatibility/winforms.md#net-core-30)
