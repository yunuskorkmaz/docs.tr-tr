---
title: ​.NET Core 3.0’daki yenilikler
description: .NET Core 3,0 ' de bulunan yeni özellikler hakkında bilgi edinin.
dev_langs:
- csharp
author: adegeo
ms.author: adegeo
ms.date: 01/27/2020
ms.openlocfilehash: 60b511adecf37855de91f45245fc55911ba281dc
ms.sourcegitcommit: 4d45bda8cd9558ea8af4be591e3d5a29360c1ece
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/02/2020
ms.locfileid: "91654777"
---
# <a name="whats-new-in-net-core-30"></a><span data-ttu-id="e9711-103">​.NET Core 3.0’daki yenilikler</span><span class="sxs-lookup"><span data-stu-id="e9711-103">What's new in .NET Core 3.0</span></span>

<span data-ttu-id="e9711-104">Bu makalede .NET Core 3,0 ' deki yenilikler açıklanır.</span><span class="sxs-lookup"><span data-stu-id="e9711-104">This article describes what is new in .NET Core 3.0.</span></span> <span data-ttu-id="e9711-105">En büyük geliştirmelerden biri, Windows Masaüstü uygulamaları için destek içerir (yalnızca Windows).</span><span class="sxs-lookup"><span data-stu-id="e9711-105">One of the biggest enhancements is support for Windows desktop applications (Windows only).</span></span> <span data-ttu-id="e9711-106">.NET Core 3,0 SDK bileşeni Windows Masaüstü 'Nü kullanarak Windows Forms ve Windows Presentation Foundation (WPF) uygulamalarınızın bağlantı noktası oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e9711-106">By using the .NET Core 3.0 SDK component Windows Desktop, you can port your Windows Forms and Windows Presentation Foundation (WPF) applications.</span></span> <span data-ttu-id="e9711-107">Temiz olması için, Windows Masaüstü bileşeni yalnızca Windows 'da desteklenir ve Windows 'a dahildir.</span><span class="sxs-lookup"><span data-stu-id="e9711-107">To be clear, the Windows Desktop component is only supported and included on Windows.</span></span> <span data-ttu-id="e9711-108">Daha fazla bilgi için bu makalenin devamındaki [Windows Masaüstü](#windows-desktop) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="e9711-108">For more information, see the [Windows desktop](#windows-desktop) section later in this article.</span></span>

<span data-ttu-id="e9711-109">.NET Core 3,0, C# 8,0 için destek ekler.</span><span class="sxs-lookup"><span data-stu-id="e9711-109">.NET Core 3.0 adds support for C# 8.0.</span></span> <span data-ttu-id="e9711-110">[Visual Studio 2019 sürüm 16,3](https://visualstudio.microsoft.com/vs/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) veya daha yeni bir sürümünü, [Mac için Visual Studio 8,3](/visualstudio/mac/install-preview) veya daha yenisini veya en son **C# uzantısıyla** [Visual Studio Code](https://code.visualstudio.com/) kullanmanız önemle önerilir.</span><span class="sxs-lookup"><span data-stu-id="e9711-110">It's highly recommended that you use [Visual Studio 2019 version 16.3](https://visualstudio.microsoft.com/vs/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) or newer, [Visual Studio for Mac 8.3](/visualstudio/mac/install-preview) or newer, or [Visual Studio Code](https://code.visualstudio.com/) with the latest **C# extension**.</span></span>

<span data-ttu-id="e9711-111">Şimdi Windows, macOS veya Linux 'ta [.NET Core 3,0 'Yi indirin ve](https://aka.ms/netcore3download) kullanmaya başlayın.</span><span class="sxs-lookup"><span data-stu-id="e9711-111">[Download and get started with .NET Core 3.0](https://aka.ms/netcore3download) right now on Windows, macOS, or Linux.</span></span>

<span data-ttu-id="e9711-112">Yayın hakkında daha fazla bilgi için bkz. [.NET Core 3,0 duyurusu](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-0/).</span><span class="sxs-lookup"><span data-stu-id="e9711-112">For more information about the release, see the [.NET Core 3.0 announcement](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-0/).</span></span>

<span data-ttu-id="e9711-113">.NET Core RC1, Microsoft tarafından önceden hazırlanmıştı ve tam olarak desteklenmektedir.</span><span class="sxs-lookup"><span data-stu-id="e9711-113">.NET Core RC1 was considered production ready by Microsoft and was fully supported.</span></span> <span data-ttu-id="e9711-114">Önizleme sürümü kullanıyorsanız, devam eden destek için RTM sürümüne geçmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="e9711-114">If you're using a preview release, you must move to the RTM version for continued support.</span></span>

## <a name="language-improvements-c-80"></a><span data-ttu-id="e9711-115">Dil geliştirmeleri C# 8,0</span><span class="sxs-lookup"><span data-stu-id="e9711-115">Language improvements C# 8.0</span></span>

<span data-ttu-id="e9711-116">C# 8,0, [null olabilen başvuru türleri](../../csharp/language-reference/builtin-types/nullable-reference-types.md) özelliği, zaman uyumsuz akışlar ve daha fazla desen içeren bu sürümün bir parçasıdır.</span><span class="sxs-lookup"><span data-stu-id="e9711-116">C# 8.0 is also part of this release, which includes the [nullable reference types](../../csharp/language-reference/builtin-types/nullable-reference-types.md) feature, async streams, and more patterns.</span></span> <span data-ttu-id="e9711-117">C# 8,0 özellikleri hakkında daha fazla bilgi için bkz. [c# 8,0 ' deki](../../csharp/whats-new/csharp-8.md)yenilikler.</span><span class="sxs-lookup"><span data-stu-id="e9711-117">For more information about C# 8.0 features, see [What's new in C# 8.0](../../csharp/whats-new/csharp-8.md).</span></span>

<span data-ttu-id="e9711-118">C# 8,0 Dil özellikleriyle ilgili öğreticiler:</span><span class="sxs-lookup"><span data-stu-id="e9711-118">Tutorials related to C# 8.0 language features:</span></span>

- [<span data-ttu-id="e9711-119">Öğretici: tasarım amacınızı null olabilen ve null yapılamayan başvuru türleriyle daha net bir şekilde Ifade edin</span><span class="sxs-lookup"><span data-stu-id="e9711-119">Tutorial: Express your design intent more clearly with nullable and non-nullable reference types</span></span>](../../csharp/tutorials/nullable-reference-types.md)
- [<span data-ttu-id="e9711-120">Öğretici: C# 8,0 ve .NET Core 3,0 kullanarak zaman uyumsuz akışlar oluşturma ve kullanma</span><span class="sxs-lookup"><span data-stu-id="e9711-120">Tutorial: Generate and consume async streams using C# 8.0 and .NET Core 3.0</span></span>](../../csharp/tutorials/generate-consume-asynchronous-stream.md)
- [<span data-ttu-id="e9711-121">Öğretici: tür odaklı ve veri odaklı algoritmalar oluşturmak için model eşleştirmeyi kullanın</span><span class="sxs-lookup"><span data-stu-id="e9711-121">Tutorial: Use pattern matching to build type-driven and data-driven algorithms</span></span>](../../csharp/tutorials/pattern-matching.md)

<span data-ttu-id="e9711-122">Aşağıda ayrıntılı olarak açıklanan aşağıdaki API özelliklerini desteklemek için dil geliştirmeleri eklenmiştir:</span><span class="sxs-lookup"><span data-stu-id="e9711-122">Language enhancements were added to support the following API features detailed below:</span></span>

- [<span data-ttu-id="e9711-123">Aralıklar ve dizinler</span><span class="sxs-lookup"><span data-stu-id="e9711-123">Ranges and indices</span></span>](#ranges-and-indices)
- [<span data-ttu-id="e9711-124">Zaman uyumsuz akışlar</span><span class="sxs-lookup"><span data-stu-id="e9711-124">Async streams</span></span>](#async-streams)

## <a name="net-standard-21"></a><span data-ttu-id="e9711-125">.NET Standard 2,1</span><span class="sxs-lookup"><span data-stu-id="e9711-125">.NET Standard 2.1</span></span>

<span data-ttu-id="e9711-126">.NET Core 3,0 **.NET Standard 2,1**uygular.</span><span class="sxs-lookup"><span data-stu-id="e9711-126">.NET Core 3.0 implements **.NET Standard 2.1**.</span></span> <span data-ttu-id="e9711-127">Ancak, varsayılan `dotnet new classlib` şablon hala **.NET Standard 2,0**' i hedefleyen bir proje oluşturur.</span><span class="sxs-lookup"><span data-stu-id="e9711-127">However, the default `dotnet new classlib` template generates a project that still targets **.NET Standard 2.0**.</span></span> <span data-ttu-id="e9711-128">**.NET Standard 2,1**' i hedeflemek için proje dosyanızı düzenleyin ve özelliği şu `TargetFramework` şekilde değiştirin `netstandard2.1` :</span><span class="sxs-lookup"><span data-stu-id="e9711-128">To target **.NET Standard 2.1**, edit your project file and change the `TargetFramework` property to `netstandard2.1`:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <TargetFramework>netstandard2.1</TargetFramework>
  </PropertyGroup>

</Project>
```

<span data-ttu-id="e9711-129">Visual Studio kullanıyorsanız, Visual Studio 2017 **.NET Standard 2,1** veya **.NET Core 3,0**' i desteklemediğinden [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019)gerekir.</span><span class="sxs-lookup"><span data-stu-id="e9711-129">If you're using Visual Studio, you need [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019), as Visual Studio 2017 doesn't support **.NET Standard 2.1** or **.NET Core 3.0**.</span></span>

## <a name="compiledeploy"></a><span data-ttu-id="e9711-130">Derle/dağıt</span><span class="sxs-lookup"><span data-stu-id="e9711-130">Compile/Deploy</span></span>

### <a name="default-executables"></a><span data-ttu-id="e9711-131">Varsayılan yürütülebilir dosyalar</span><span class="sxs-lookup"><span data-stu-id="e9711-131">Default executables</span></span>

<span data-ttu-id="e9711-132">.NET Core artık [çerçeveye bağlı yürütülebilir dosyaları](../deploying/index.md#publish-framework-dependent) varsayılan olarak oluşturur.</span><span class="sxs-lookup"><span data-stu-id="e9711-132">.NET Core now builds [framework-dependent executables](../deploying/index.md#publish-framework-dependent) by default.</span></span> <span data-ttu-id="e9711-133">Bu davranış, .NET Core 'un küresel olarak yüklenen bir sürümünü kullanan uygulamalar için yenidir.</span><span class="sxs-lookup"><span data-stu-id="e9711-133">This behavior is new for applications that use a globally installed version of .NET Core.</span></span> <span data-ttu-id="e9711-134">Daha önce yalnızca [kendi kendine kapsanan dağıtımlar](../deploying/index.md#publish-self-contained) yürütülebilir bir dosya üretecektir.</span><span class="sxs-lookup"><span data-stu-id="e9711-134">Previously, only [self-contained deployments](../deploying/index.md#publish-self-contained) would produce an executable.</span></span>

<span data-ttu-id="e9711-135">`dotnet build`Veya sırasında `dotnet publish` , kullanmakta olduğunuz SDK ortamı ve platformuyla eşleşen bir çalıştırılabilir ( **appHost**olarak bilinir) oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="e9711-135">During `dotnet build` or `dotnet publish`, an executable (known as the **appHost**) is created that matches the environment and platform of the SDK you're using.</span></span> <span data-ttu-id="e9711-136">Bu yürütülebilir dosyalarla aynı şeyleri, diğer yerel yürütülebilir dosyaları gibi bekleyebilir, örneğin:</span><span class="sxs-lookup"><span data-stu-id="e9711-136">You can expect the same things with these executables as you would other native executables, such as:</span></span>

- <span data-ttu-id="e9711-137">Yürütülebilir dosyaya çift tıklayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e9711-137">You can double-click on the executable.</span></span>
- <span data-ttu-id="e9711-138">Uygulamayı `myapp.exe` Windows ve `./myapp` Linux ve MacOS gibi bir komut isteminden doğrudan başlatabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e9711-138">You can launch the application from a command prompt directly, such as `myapp.exe` on Windows, and `./myapp` on Linux and macOS.</span></span>

### <a name="macos-apphost-and-notarization"></a><span data-ttu-id="e9711-139">macOS appHost ve notarlama</span><span class="sxs-lookup"><span data-stu-id="e9711-139">macOS appHost and notarization</span></span>

<span data-ttu-id="e9711-140">*Yalnızca macOS*</span><span class="sxs-lookup"><span data-stu-id="e9711-140">*macOS only*</span></span>

<span data-ttu-id="e9711-141">MacOS için .NET Core SDK 3,0 ' den başlayarak, varsayılan bir yürütülebilir dosya (appHost olarak bilinir) oluşturma ayarı varsayılan olarak devre dışıdır.</span><span class="sxs-lookup"><span data-stu-id="e9711-141">Starting with the notarized .NET Core SDK 3.0 for macOS, the setting to produce a default executable (known as the appHost) is disabled by default.</span></span> <span data-ttu-id="e9711-142">Daha fazla bilgi için bkz. [MacOS Catalina Notarleştirme ve .NET Core indirmeleri ve projeleri üzerindeki etki](../install/macos-notarization-issues.md).</span><span class="sxs-lookup"><span data-stu-id="e9711-142">For more information, see [macOS Catalina Notarization and the impact on .NET Core downloads and projects](../install/macos-notarization-issues.md).</span></span>

<span data-ttu-id="e9711-143">AppHost ayarı etkinleştirildiğinde, .NET Core, oluşturduğunuzda veya yayımladığınızda yerel bir MAK-O çalıştırılabilir dosyası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="e9711-143">When the appHost setting is enabled, .NET Core generates a native Mach-O executable when you build or publish.</span></span> <span data-ttu-id="e9711-144">Uygulamanız, komutuyla kaynak koddan çalıştırıldığında `dotnet run` veya mak-O yürütülebilir dosyasını doğrudan başlatarak appHost bağlamında çalışır.</span><span class="sxs-lookup"><span data-stu-id="e9711-144">Your app runs in the context of the appHost when it is run from source code with the `dotnet run` command, or by starting the Mach-O executable directly.</span></span>

<span data-ttu-id="e9711-145">AppHost olmadan, bir kullanıcıya [çerçeveye bağımlı](../deploying/index.md#publish-framework-dependent) bir uygulama başlatabilir tek yöntem `dotnet <filename.dll>` komutunu kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e9711-145">Without the appHost, the only way a user can start a [framework-dependent](../deploying/index.md#publish-framework-dependent) app is with the `dotnet <filename.dll>` command.</span></span> <span data-ttu-id="e9711-146">Uygulamanızı [kendi içinde](../deploying/index.md#publish-self-contained)yayımladığınızda her zaman bir appHost oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="e9711-146">An appHost is always created when you publish your app [self-contained](../deploying/index.md#publish-self-contained).</span></span>

<span data-ttu-id="e9711-147">AppHost 'yi proje düzeyinde yapılandırabilir veya parametresi ile belirli bir komut için appHost ' ı kapatabilirsiniz `dotnet` `-p:UseAppHost` :</span><span class="sxs-lookup"><span data-stu-id="e9711-147">You can either configure the appHost at the project level, or toggle the appHost for a specific `dotnet` command with the `-p:UseAppHost` parameter:</span></span>

- <span data-ttu-id="e9711-148">Proje dosyası</span><span class="sxs-lookup"><span data-stu-id="e9711-148">Project file</span></span>

  ```xml
  <PropertyGroup>
    <UseAppHost>true</UseAppHost>
  </PropertyGroup>
  ```

- <span data-ttu-id="e9711-149">Komut satırı parametresi</span><span class="sxs-lookup"><span data-stu-id="e9711-149">Command-line parameter</span></span>

  ```dotnetcli
  dotnet run -p:UseAppHost=true
  ```

<span data-ttu-id="e9711-150">Ayarı hakkında daha fazla bilgi için `UseAppHost` bkz. [MICROSOFT. net. SDK için MSBuild özellikleri](../project-sdk/msbuild-props.md#useapphost).</span><span class="sxs-lookup"><span data-stu-id="e9711-150">For more information about the `UseAppHost` setting, see [MSBuild properties for Microsoft.NET.Sdk](../project-sdk/msbuild-props.md#useapphost).</span></span>

### <a name="single-file-executables"></a><span data-ttu-id="e9711-151">Tek dosya yürütülebilir dosyaları</span><span class="sxs-lookup"><span data-stu-id="e9711-151">Single-file executables</span></span>

<span data-ttu-id="e9711-152">`dotnet publish`Komut, uygulamanızı platforma özgü tek dosya yürütülebilir dosyasına paketlemeyi destekler.</span><span class="sxs-lookup"><span data-stu-id="e9711-152">The `dotnet publish` command supports packaging your app into a platform-specific single-file executable.</span></span> <span data-ttu-id="e9711-153">Yürütülebilir dosya kendiliğinden ayıklanıyor ve uygulamanızı çalıştırmak için gerekli tüm bağımlılıkları (yerel dahil) içerir.</span><span class="sxs-lookup"><span data-stu-id="e9711-153">The executable is self-extracting and contains all dependencies (including native) that are required to run your app.</span></span> <span data-ttu-id="e9711-154">Uygulama ilk kez çalıştırıldığında uygulama adı ve derleme tanımlayıcısı temelinde bir dizine çıkarılır.</span><span class="sxs-lookup"><span data-stu-id="e9711-154">When the app is first run, the application is extracted to a directory based on the app name and build identifier.</span></span> <span data-ttu-id="e9711-155">Uygulama yeniden çalıştırıldığında başlatma daha hızlıdır.</span><span class="sxs-lookup"><span data-stu-id="e9711-155">Startup is faster when the application is run again.</span></span> <span data-ttu-id="e9711-156">Yeni bir sürüm kullanılmadığı takdirde uygulamanın kendisi ikinci kez ayıklanmasına gerek yoktur.</span><span class="sxs-lookup"><span data-stu-id="e9711-156">The application doesn't need to extract itself a second time unless a new version was used.</span></span>

<span data-ttu-id="e9711-157">Tek dosya yürütülebiliri yayımlamak için, `PublishSingleFile` projenizdeki öğesini veya komut satırında `dotnet publish` komutunu komutuyla ayarlayın:</span><span class="sxs-lookup"><span data-stu-id="e9711-157">To publish a single-file executable, set the `PublishSingleFile` in your project or on the command line with the `dotnet publish` command:</span></span>

```xml
<PropertyGroup>
  <RuntimeIdentifier>win10-x64</RuntimeIdentifier>
  <PublishSingleFile>true</PublishSingleFile>
</PropertyGroup>
```

<span data-ttu-id="e9711-158">-veya-</span><span class="sxs-lookup"><span data-stu-id="e9711-158">-or-</span></span>

```dotnetcli
dotnet publish -r win10-x64 -p:PublishSingleFile=true
```

<span data-ttu-id="e9711-159">Tek dosya yayınlama hakkında daha fazla bilgi için bkz. [tek dosya paketcisi tasarım belgesi](https://github.com/dotnet/designs/blob/master/accepted/2020/single-file/design.md).</span><span class="sxs-lookup"><span data-stu-id="e9711-159">For more information about single-file publishing, see the [single-file bundler design document](https://github.com/dotnet/designs/blob/master/accepted/2020/single-file/design.md).</span></span>

### <a name="assembly-linking"></a><span data-ttu-id="e9711-160">Bütünleştirilmiş kod bağlama</span><span class="sxs-lookup"><span data-stu-id="e9711-160">Assembly linking</span></span>

<span data-ttu-id="e9711-161">.NET Core 3,0 SDK, Il 'yi çözümleyerek ve kullanılmayan derlemeleri kırparak uygulamaların boyutunu azaltan bir araçla birlikte gelir.</span><span class="sxs-lookup"><span data-stu-id="e9711-161">The .NET core 3.0 SDK comes with a tool that can reduce the size of apps by analyzing IL and trimming unused assemblies.</span></span>

<span data-ttu-id="e9711-162">Bağımsız uygulamalar, kodunuzun çalıştırılması için gereken her şeyi, ana bilgisayara .NET yüklenmesini gerektirmeden içerir.</span><span class="sxs-lookup"><span data-stu-id="e9711-162">Self-contained apps include everything needed to run your code, without requiring .NET to be installed on the host computer.</span></span> <span data-ttu-id="e9711-163">Ancak, çoğu zaman uygulamanın çalışması için yalnızca küçük bir çerçeve alt kümesi gerekir ve kullanılmayan diğer kitaplıklar da kaldırılabilir.</span><span class="sxs-lookup"><span data-stu-id="e9711-163">However, many times the app only requires a small subset of the framework to function, and other unused libraries could be removed.</span></span>

<span data-ttu-id="e9711-164">.NET Core artık uygulamanızın Il 'sini taramak için [Il bağlayıcı](https://github.com/mono/linker) aracını kullanacak bir ayar içeriyor.</span><span class="sxs-lookup"><span data-stu-id="e9711-164">.NET Core now includes a setting that will use the [IL linker](https://github.com/mono/linker) tool to scan the IL of your app.</span></span> <span data-ttu-id="e9711-165">Bu araç hangi kodun gerekli olduğunu algılar ve ardından kullanılmayan kitaplıkları kırpar.</span><span class="sxs-lookup"><span data-stu-id="e9711-165">This tool detects what code is required, and then trims unused libraries.</span></span> <span data-ttu-id="e9711-166">Bu araç bazı uygulamaların dağıtım boyutunu önemli ölçüde azaltabilir.</span><span class="sxs-lookup"><span data-stu-id="e9711-166">This tool can significantly reduce the deployment size of some apps.</span></span>

<span data-ttu-id="e9711-167">Bu aracı etkinleştirmek için `<PublishTrimmed>` projenize ayarı ekleyin ve kendi içinde bulunan bir uygulamayı yayımlayın:</span><span class="sxs-lookup"><span data-stu-id="e9711-167">To enable this tool, add the `<PublishTrimmed>` setting in your project and publish a self-contained app:</span></span>

```xml
<PropertyGroup>
  <PublishTrimmed>true</PublishTrimmed>
</PropertyGroup>
```

```dotnetcli
dotnet publish -r <rid> -c Release
```

<span data-ttu-id="e9711-168">Örnek olarak, yayımlanan temel "Merhaba Dünya" yeni konsol projesi şablonu, yayımlandığında 70 MB ile çarpılır.</span><span class="sxs-lookup"><span data-stu-id="e9711-168">As an example, the basic "hello world" new console project template that is included, when published, hits about 70 MB in size.</span></span> <span data-ttu-id="e9711-169">Kullanarak `<PublishTrimmed>` , bu boyut yaklaşık 30 MB 'ye indirilir.</span><span class="sxs-lookup"><span data-stu-id="e9711-169">By using `<PublishTrimmed>`, that size is reduced to about 30 MB.</span></span>

<span data-ttu-id="e9711-170">Yansıma veya ilgili dinamik özellikleri kullanan uygulamaların veya çerçevelerin (ASP.NET Core ve WPF dahil) genellikle kırpıldığına göre kesilmesini göz önünde bulundurmanız önemlidir.</span><span class="sxs-lookup"><span data-stu-id="e9711-170">It's important to consider that applications or frameworks (including ASP.NET Core and WPF) that use reflection or related dynamic features, will often break when trimmed.</span></span> <span data-ttu-id="e9711-171">Bu ayırıcı, bağlayıcının bu dinamik davranış hakkında bilgi sahibi olmadığı ve yansıma için hangi çerçeve türlerinin gerekli olduğunu belirleyemediği için oluşur.</span><span class="sxs-lookup"><span data-stu-id="e9711-171">This breakage occurs because the linker doesn't know about this dynamic behavior and can't determine which framework types are required for reflection.</span></span> <span data-ttu-id="e9711-172">Il bağlayıcı aracı, bu senaryonun farkında olacak şekilde yapılandırılabilir.</span><span class="sxs-lookup"><span data-stu-id="e9711-172">The IL Linker tool can be configured to be aware of this scenario.</span></span>

<span data-ttu-id="e9711-173">Tüm diğerleri üzerinde, kırpdıktan sonra uygulamanızı test ettiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="e9711-173">Above all else, be sure to test your app after trimming.</span></span>

<span data-ttu-id="e9711-174">Il bağlayıcı aracı hakkında daha fazla bilgi için [belgelere](../deploying/trim-self-contained.md) bakın veya [mono/bağlayıcı]( https://github.com/mono/linker) deposunu ziyaret edin.</span><span class="sxs-lookup"><span data-stu-id="e9711-174">For more information about the IL Linker tool, see the [documentation](../deploying/trim-self-contained.md) or visit the [mono/linker]( https://github.com/mono/linker) repo.</span></span>

### <a name="tiered-compilation"></a><span data-ttu-id="e9711-175">Katmanlı derleme</span><span class="sxs-lookup"><span data-stu-id="e9711-175">Tiered compilation</span></span>

<span data-ttu-id="e9711-176">[Katmanlı derleme](https://github.com/dotnet/runtime/blob/master/docs/design/features/tiered-compilation.md) (TC), .net Core 3,0 ile varsayılan olarak açık olur.</span><span class="sxs-lookup"><span data-stu-id="e9711-176">[Tiered compilation](https://github.com/dotnet/runtime/blob/master/docs/design/features/tiered-compilation.md) (TC) is on by default with .NET Core 3.0.</span></span> <span data-ttu-id="e9711-177">Bu özellik, çalışma zamanının daha iyi performans elde etmek için tam zamanında (JıT) derleyicisini daha kolay bir şekilde kullanmasına olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="e9711-177">This feature enables the runtime to more adaptively use the just-in-time (JIT) compiler to achieve better performance.</span></span>

<span data-ttu-id="e9711-178">Katmanlı derlemenin başlıca avantajı, daha düşük kalitede, ancak daha hızlı bir katmanda ya da daha yüksek kalitede, ancak daha yavaş bir katmanda çeşitli yöntemler elde etmenin iki yolunu sağlamaktır.</span><span class="sxs-lookup"><span data-stu-id="e9711-178">The main benefit of tiered compilation is to provide two ways of jitting methods: in a lower-quality-but-faster tier or a higher-quality-but-slower tier.</span></span> <span data-ttu-id="e9711-179">Kalite, yöntemin en iyi duruma getirilmiş olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="e9711-179">The quality refers to how well the method is optimized.</span></span> <span data-ttu-id="e9711-180">TC, düzenli bir durum aracılığıyla başlangıçtan itibaren çeşitli yürütme aşamalarından geçen bir uygulamanın performansını artırmaya yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="e9711-180">TC helps to improve the performance of an application as it goes through various stages of execution, from startup through steady state.</span></span> <span data-ttu-id="e9711-181">Katmanlı derleme devre dışı bırakıldığında, her yöntem, başlangıç performansı üzerinden düzenli durum performansına yol gösteren tek bir şekilde derlenir.</span><span class="sxs-lookup"><span data-stu-id="e9711-181">When tiered compilation is disabled, every method is compiled in a single way that's biased to steady-state performance over startup performance.</span></span>

<span data-ttu-id="e9711-182">TC etkinleştirildiğinde, bir uygulama başlatıldığında Yöntem derlemesi için aşağıdaki davranış geçerlidir:</span><span class="sxs-lookup"><span data-stu-id="e9711-182">When TC is enabled, the following behavior applies for method compilation when an app starts up:</span></span>

- <span data-ttu-id="e9711-183">Metodun önceden derlenen kodu veya [Readytorun](#readytorun-images)varsa, önceden oluşturulan kod kullanılır.</span><span class="sxs-lookup"><span data-stu-id="e9711-183">If the method has ahead-of-time-compiled code, or [ReadyToRun](#readytorun-images), the pregenerated code is used.</span></span>
- <span data-ttu-id="e9711-184">Aksi halde, yöntemi jmesdir.</span><span class="sxs-lookup"><span data-stu-id="e9711-184">Otherwise, the method is jitted.</span></span> <span data-ttu-id="e9711-185">Genellikle, bu yöntemler değer türleri üzerinde genel türlerdir.</span><span class="sxs-lookup"><span data-stu-id="e9711-185">Typically, these methods are generics over value types.</span></span>
  - <span data-ttu-id="e9711-186">*Hızlı JIT* daha hızlı (veya daha az iyileştirilmiş) kod üretir.</span><span class="sxs-lookup"><span data-stu-id="e9711-186">*Quick JIT* produces lower-quality (or less optimized) code more quickly.</span></span> <span data-ttu-id="e9711-187">.NET Core 3,0 ' de hızlı JıT, döngüler içermeyen ve başlangıç sırasında tercih edilen yöntemler için varsayılan olarak etkindir.</span><span class="sxs-lookup"><span data-stu-id="e9711-187">In .NET Core 3.0, Quick JIT is enabled by default for methods that don't contain loops and is preferred during startup.</span></span>
  - <span data-ttu-id="e9711-188">JıT 'i tamamen en iyi duruma getirmek daha yavaş daha yavaş (veya daha iyileştirilmiş) kod üretir.</span><span class="sxs-lookup"><span data-stu-id="e9711-188">The fully optimizing JIT produces higher-quality (or more optimized) code more slowly.</span></span> <span data-ttu-id="e9711-189">Hızlı JıT 'in kullanılacağı yöntemler için (örneğin, yöntemi ile ilişkilendirilebildiği <xref:System.Runtime.CompilerServices.MethodImplOptions.AggressiveOptimization?displayProperty=nameWithType> ), JIT tam olarak iyileştiriliyor kullanılır.</span><span class="sxs-lookup"><span data-stu-id="e9711-189">For methods where Quick JIT would not be used (for example, if the method is attributed with <xref:System.Runtime.CompilerServices.MethodImplOptions.AggressiveOptimization?displayProperty=nameWithType>), the fully optimizing JIT is used.</span></span>

<span data-ttu-id="e9711-190">Sık çağrılan yöntemler için, tam zamanında derleyici arka planda tamamen iyileştirilmiş kod oluşturur.</span><span class="sxs-lookup"><span data-stu-id="e9711-190">For frequently called methods, the just-in-time compiler eventually creates fully optimized code in the background.</span></span> <span data-ttu-id="e9711-191">En iyi duruma getirilmiş kod daha sonra bu yöntem için önceden derlenmiş kodun yerini alır.</span><span class="sxs-lookup"><span data-stu-id="e9711-191">The optimized code then replaces the pre-compiled code for that method.</span></span>

<span data-ttu-id="e9711-192">Hızlı JıT tarafından oluşturulan kod daha yavaş çalışabilir, daha fazla bellek ayırabilir veya daha fazla yığın alanı kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="e9711-192">Code generated by Quick JIT may run slower, allocate more memory, or use more stack space.</span></span> <span data-ttu-id="e9711-193">Sorunlar varsa, proje dosyasında bu MSBuild özelliğini kullanarak hızlı JıT 'i devre dışı bırakabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="e9711-193">If there are issues, you can disabled Quick JIT using this MSBuild property in the project file:</span></span>

```xml
<PropertyGroup>
  <TieredCompilationQuickJit>false</TieredCompilationQuickJit>
</PropertyGroup>
```

<span data-ttu-id="e9711-194">TC 'yi tamamen devre dışı bırakmak için, proje dosyanızda bu MSBuild özelliğini kullanın:</span><span class="sxs-lookup"><span data-stu-id="e9711-194">To disable TC completely, use this MSBuild property in your project file:</span></span>

```xml
<PropertyGroup>
  <TieredCompilation>false</TieredCompilation>
</PropertyGroup>
```

> [!TIP]
> <span data-ttu-id="e9711-195">Bu ayarları proje dosyasında değiştirirseniz, yeni ayarların yansıtılması için temiz bir derleme gerçekleştirmeniz gerekebilir ( `obj` ve `bin` dizinleri silin ve yeniden oluşturun).</span><span class="sxs-lookup"><span data-stu-id="e9711-195">If you change these settings in the project file, you may need to perform a clean build for the new settings to be reflected (delete the `obj` and `bin` directories and rebuild).</span></span>

<span data-ttu-id="e9711-196">Çalışma zamanında derlemeyi yapılandırma hakkında daha fazla bilgi için bkz. [derleme Için çalışma zamanı yapılandırma seçenekleri](../run-time-config/compilation.md).</span><span class="sxs-lookup"><span data-stu-id="e9711-196">For more information about configuring compilation at run time, see [Run-time configuration options for compilation](../run-time-config/compilation.md).</span></span>

### <a name="readytorun-images"></a><span data-ttu-id="e9711-197">ReadyToRun görüntüleri</span><span class="sxs-lookup"><span data-stu-id="e9711-197">ReadyToRun images</span></span>

<span data-ttu-id="e9711-198">Uygulama derlemelerinizi ReadyToRun (R2R) biçiminde derleyerek .NET Core uygulamanızın başlama süresini geliştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e9711-198">You can improve the startup time of your .NET Core application by compiling your application assemblies as ReadyToRun (R2R) format.</span></span> <span data-ttu-id="e9711-199">R2R, bir süre öncesi (AOT) derleme biçimidir.</span><span class="sxs-lookup"><span data-stu-id="e9711-199">R2R is a form of ahead-of-time (AOT) compilation.</span></span>

<span data-ttu-id="e9711-200">R2R ikilileri, tam zamanında (JıT) derleyicisinin uygulamanız yüklenirken yapması gereken iş miktarını azaltarak başlangıç performansını geliştirir.</span><span class="sxs-lookup"><span data-stu-id="e9711-200">R2R binaries improve startup performance by reducing the amount of work the just-in-time (JIT) compiler needs to do as your application loads.</span></span> <span data-ttu-id="e9711-201">İkililer, JıT 'in üretmesine kıyasla benzer yerel kod içerir.</span><span class="sxs-lookup"><span data-stu-id="e9711-201">The binaries contain similar native code compared to what the JIT would produce.</span></span> <span data-ttu-id="e9711-202">Ancak, R2R ikilileri, bazı senaryolar için hala gerekli olan hem ara dil (IL) kodunu hem de aynı kodun yerel sürümünü içerdiğinden, daha büyüktür.</span><span class="sxs-lookup"><span data-stu-id="e9711-202">However, R2R binaries are larger because they contain both intermediate language (IL) code, which is still needed for some scenarios, and the native version of the same code.</span></span> <span data-ttu-id="e9711-203">R2R yalnızca, Linux x64 veya Windows x64 gibi belirli çalışma zamanı ortamlarını (RID) hedefleyen bir kendi içinde bulunan uygulamayı yayımladığınızda kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="e9711-203">R2R is only available when you publish a self-contained app that targets specific runtime environments (RID) such as Linux x64 or Windows x64.</span></span>

<span data-ttu-id="e9711-204">Projenizi ReadyToRun olarak derlemek için aşağıdakileri yapın:</span><span class="sxs-lookup"><span data-stu-id="e9711-204">To compile your project as ReadyToRun, do the following:</span></span>

01. <span data-ttu-id="e9711-205">`<PublishReadyToRun>`Ayarı projenize ekleyin:</span><span class="sxs-lookup"><span data-stu-id="e9711-205">Add the `<PublishReadyToRun>` setting to your project:</span></span>

    ```xml
    <PropertyGroup>
      <PublishReadyToRun>true</PublishReadyToRun>
    </PropertyGroup>
    ```

01. <span data-ttu-id="e9711-206">Kendi içinde bir uygulama yayımlayın.</span><span class="sxs-lookup"><span data-stu-id="e9711-206">Publish a self-contained app.</span></span> <span data-ttu-id="e9711-207">Örneğin, bu komut Windows 'un 64 bit sürümü için kendi kendine içerilen bir uygulama oluşturur:</span><span class="sxs-lookup"><span data-stu-id="e9711-207">For example, this command creates a self-contained app for the 64-bit version of Windows:</span></span>

    ```dotnetcli
    dotnet publish -c Release -r win-x64 --self-contained
    ```

#### <a name="cross-platformarchitecture-restrictions"></a><span data-ttu-id="e9711-208">Platformlar arası/mimari kısıtlamaları</span><span class="sxs-lookup"><span data-stu-id="e9711-208">Cross platform/architecture restrictions</span></span>

<span data-ttu-id="e9711-209">ReadyToRun derleyicisi Şu anda çapraz hedefleme 'yi desteklememektedir.</span><span class="sxs-lookup"><span data-stu-id="e9711-209">The ReadyToRun compiler doesn't currently support cross-targeting.</span></span> <span data-ttu-id="e9711-210">Belirli bir hedefte derleme yapmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="e9711-210">You must compile on a given target.</span></span> <span data-ttu-id="e9711-211">Örneğin, R2R görüntülerini Windows x64 için istiyorsanız, bu ortamda Yayımla komutunu çalıştırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="e9711-211">For example, if you want R2R images for Windows x64, you need to run the publish command on that environment.</span></span>

<span data-ttu-id="e9711-212">Çapraz hedefleme için özel durumlar:</span><span class="sxs-lookup"><span data-stu-id="e9711-212">Exceptions to cross-targeting:</span></span>

- <span data-ttu-id="e9711-213">Windows x64, Windows ARM32, ARM64 ve x86 görüntülerini derlemek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="e9711-213">Windows x64 can be used to compile Windows ARM32, ARM64, and x86 images.</span></span>
- <span data-ttu-id="e9711-214">Windows x86, Windows ARM32 görüntülerini derlemek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="e9711-214">Windows x86 can be used to compile Windows ARM32 images.</span></span>
- <span data-ttu-id="e9711-215">Linux x64, Linux ARM32 ve ARM64 görüntülerini derlemek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="e9711-215">Linux x64 can be used to compile Linux ARM32 and ARM64 images.</span></span>

<span data-ttu-id="e9711-216">Daha fazla bilgi için bkz. [çalıştırılmaya hazırlanma](../deploying/ready-to-run.md).</span><span class="sxs-lookup"><span data-stu-id="e9711-216">For more information, see [Ready to Run](../deploying/ready-to-run.md).</span></span>

## <a name="runtimesdk"></a><span data-ttu-id="e9711-217">Çalışma zamanı/SDK</span><span class="sxs-lookup"><span data-stu-id="e9711-217">Runtime/SDK</span></span>

### <a name="major-version-runtime-roll-forward"></a><span data-ttu-id="e9711-218">Büyük sürüm çalışma zamanı ileri</span><span class="sxs-lookup"><span data-stu-id="e9711-218">Major-version runtime roll forward</span></span>

<span data-ttu-id="e9711-219">.NET Core 3,0, uygulamanızın .NET Core 'un en son ana sürümüne iletmesini sağlayan bir katılım özelliği sunar.</span><span class="sxs-lookup"><span data-stu-id="e9711-219">.NET Core 3.0 introduces an opt-in feature that allows your app to roll forward to the latest major version of .NET Core.</span></span> <span data-ttu-id="e9711-220">Ayrıca, geri alma 'nın uygulamanıza nasıl uygulandığını denetlemek için yeni bir ayar eklenmiştir.</span><span class="sxs-lookup"><span data-stu-id="e9711-220">Additionally, a new setting has been added to control how roll forward is applied to your app.</span></span> <span data-ttu-id="e9711-221">Bu, aşağıdaki yollarla yapılandırılabilir:</span><span class="sxs-lookup"><span data-stu-id="e9711-221">This can be configured in the following ways:</span></span>

- <span data-ttu-id="e9711-222">Proje dosyası özelliği: `RollForward`</span><span class="sxs-lookup"><span data-stu-id="e9711-222">Project file property: `RollForward`</span></span>
- <span data-ttu-id="e9711-223">Çalışma zamanı yapılandırma dosyası özelliği: `rollForward`</span><span class="sxs-lookup"><span data-stu-id="e9711-223">Run-time configuration file property: `rollForward`</span></span>
- <span data-ttu-id="e9711-224">Ortam değişkeni: `DOTNET_ROLL_FORWARD`</span><span class="sxs-lookup"><span data-stu-id="e9711-224">Environment variable: `DOTNET_ROLL_FORWARD`</span></span>
- <span data-ttu-id="e9711-225">Komut satırı bağımsız değişkeni: `--roll-forward`</span><span class="sxs-lookup"><span data-stu-id="e9711-225">Command-line argument: `--roll-forward`</span></span>

<span data-ttu-id="e9711-226">Aşağıdaki değerlerden biri belirtilmelidir.</span><span class="sxs-lookup"><span data-stu-id="e9711-226">One of the following values must be specified.</span></span> <span data-ttu-id="e9711-227">Ayar atlanırsa, **İkincil** varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="e9711-227">If the setting is omitted, **Minor** is the default.</span></span>

- <span data-ttu-id="e9711-228">**LatestPatch**</span><span class="sxs-lookup"><span data-stu-id="e9711-228">**LatestPatch**</span></span>\
<span data-ttu-id="e9711-229">En yüksek düzeltme eki sürümüne ilet.</span><span class="sxs-lookup"><span data-stu-id="e9711-229">Roll forward to the highest patch version.</span></span> <span data-ttu-id="e9711-230">Bu, ikincil sürüm iletmeyi devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="e9711-230">This disables minor version roll forward.</span></span>
- <span data-ttu-id="e9711-231">**Bazı**</span><span class="sxs-lookup"><span data-stu-id="e9711-231">**Minor**</span></span>\
<span data-ttu-id="e9711-232">İstenen alt sürüm eksikse, en düşük düzeydeki sürüme ilet.</span><span class="sxs-lookup"><span data-stu-id="e9711-232">Roll forward to the lowest higher minor version, if requested minor version is missing.</span></span> <span data-ttu-id="e9711-233">İstenen ikincil sürüm varsa, **Latestpatch** ilkesi kullanılır.</span><span class="sxs-lookup"><span data-stu-id="e9711-233">If the requested minor version is present, then the **LatestPatch** policy is used.</span></span>
- <span data-ttu-id="e9711-234">**Leri**</span><span class="sxs-lookup"><span data-stu-id="e9711-234">**Major**</span></span>\
<span data-ttu-id="e9711-235">İstenen ana sürüm eksikse, en düşük büyük sürüme ve en düşük alt sürüme ileri doğru alın.</span><span class="sxs-lookup"><span data-stu-id="e9711-235">Roll forward to lowest higher major version, and lowest minor version, if requested major version is missing.</span></span> <span data-ttu-id="e9711-236">İstenen ana sürüm varsa, **İkincil** ilke kullanılır.</span><span class="sxs-lookup"><span data-stu-id="e9711-236">If the requested major version is present, then the **Minor** policy is used.</span></span>
- <span data-ttu-id="e9711-237">**LatestMinor**</span><span class="sxs-lookup"><span data-stu-id="e9711-237">**LatestMinor**</span></span>\
<span data-ttu-id="e9711-238">İstenen alt sürüm mevcut olsa bile en yüksek düzeyde alt sürüme ilet.</span><span class="sxs-lookup"><span data-stu-id="e9711-238">Roll forward to highest minor version, even if requested minor version is present.</span></span> <span data-ttu-id="e9711-239">Bileşen barındırma senaryolarına yöneliktir.</span><span class="sxs-lookup"><span data-stu-id="e9711-239">Intended for component hosting scenarios.</span></span>
- <span data-ttu-id="e9711-240">**Latestana**</span><span class="sxs-lookup"><span data-stu-id="e9711-240">**LatestMajor**</span></span>\
<span data-ttu-id="e9711-241">İstenen ana mevcut olsa bile, en yüksek büyük ve en yüksek düzeyde alt sürüme ilet.</span><span class="sxs-lookup"><span data-stu-id="e9711-241">Roll forward to highest major and highest minor version, even if requested major is present.</span></span> <span data-ttu-id="e9711-242">Bileşen barındırma senaryolarına yöneliktir.</span><span class="sxs-lookup"><span data-stu-id="e9711-242">Intended for component hosting scenarios.</span></span>
- <span data-ttu-id="e9711-243">**Dıı**</span><span class="sxs-lookup"><span data-stu-id="e9711-243">**Disable**</span></span>\
<span data-ttu-id="e9711-244">İleri alma.</span><span class="sxs-lookup"><span data-stu-id="e9711-244">Don't roll forward.</span></span> <span data-ttu-id="e9711-245">Yalnızca belirtilen sürüme bağlayın.</span><span class="sxs-lookup"><span data-stu-id="e9711-245">Only bind to specified version.</span></span> <span data-ttu-id="e9711-246">Bu ilke, en son düzeltme eklerine iletme özelliğini devre dışı bıraktığından genel kullanım için önerilmez.</span><span class="sxs-lookup"><span data-stu-id="e9711-246">This policy isn't recommended for general use because it disables the ability to roll forward to the latest patches.</span></span> <span data-ttu-id="e9711-247">Bu değer yalnızca test için önerilir.</span><span class="sxs-lookup"><span data-stu-id="e9711-247">This value is only recommended for testing.</span></span>

<span data-ttu-id="e9711-248">**Devre dışı bırak** ayarının yanı sıra, tüm ayarlar kullanılabilir en yüksek düzeltme eki sürümünü kullanacaktır.</span><span class="sxs-lookup"><span data-stu-id="e9711-248">Besides the **Disable** setting, all settings will use the highest available patch version.</span></span>

<span data-ttu-id="e9711-249">Varsayılan olarak, istenen sürüm ( `.runtimeconfig.json` uygulama için belirtilen şekilde) bir yayın sürümündedir, yalnızca yayın sürümleri öne çıkarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="e9711-249">By default, if the requested version (as specified in `.runtimeconfig.json` for the application) is a release version, only release versions are considered for roll forward.</span></span> <span data-ttu-id="e9711-250">Yayın öncesi sürümler yok sayılır.</span><span class="sxs-lookup"><span data-stu-id="e9711-250">Any pre-release versions are ignored.</span></span> <span data-ttu-id="e9711-251">Eşleşen bir yayın sürümü yoksa, yayın öncesi sürümler hesaba alınır.</span><span class="sxs-lookup"><span data-stu-id="e9711-251">If there is no matching release version, then pre-release versions are taken into account.</span></span> <span data-ttu-id="e9711-252">Bu davranış ayarıyla değiştirilebilir `DOTNET_ROLL_FORWARD_TO_PRERELEASE=1` , bu durumda tüm sürümler her zaman göz önünde bulundurulmalıdır.</span><span class="sxs-lookup"><span data-stu-id="e9711-252">This behavior can be changed by setting `DOTNET_ROLL_FORWARD_TO_PRERELEASE=1`, in which case all versions are always considered.</span></span>

### <a name="build-copies-dependencies"></a><span data-ttu-id="e9711-253">Derleme kopyaları bağımlılıkları</span><span class="sxs-lookup"><span data-stu-id="e9711-253">Build copies dependencies</span></span>

<span data-ttu-id="e9711-254">`dotnet build`Komut artık, NuGet önbelleğinden uygulamanızın NuGet bağımlılıklarını yapı çıkış klasörüne kopyalar.</span><span class="sxs-lookup"><span data-stu-id="e9711-254">The `dotnet build` command now copies NuGet dependencies for your application from the NuGet cache to the build output folder.</span></span> <span data-ttu-id="e9711-255">Daha önce bağımlılıklar yalnızca bir parçası olarak kopyalandı `dotnet publish` .</span><span class="sxs-lookup"><span data-stu-id="e9711-255">Previously, dependencies were only copied as part of `dotnet publish`.</span></span>

<span data-ttu-id="e9711-256">Bağlama ve Razor sayfası yayımlama gibi bazı işlemler, yayımlamayı gerektirecek şekilde devam eder.</span><span class="sxs-lookup"><span data-stu-id="e9711-256">There are some operations, like linking and razor page publishing that will still require publishing.</span></span>

### <a name="local-tools"></a><span data-ttu-id="e9711-257">Yerel Araçlar</span><span class="sxs-lookup"><span data-stu-id="e9711-257">Local tools</span></span>

<span data-ttu-id="e9711-258">.NET Core 3,0 yerel araçları tanıtır.</span><span class="sxs-lookup"><span data-stu-id="e9711-258">.NET Core 3.0 introduces local tools.</span></span> <span data-ttu-id="e9711-259">Yerel Araçlar [genel araçlara](../tools/global-tools.md) benzerdir, ancak diskte belirli bir konum ile ilişkilendirilir.</span><span class="sxs-lookup"><span data-stu-id="e9711-259">Local tools are similar to [global tools](../tools/global-tools.md) but are associated with a particular location on disk.</span></span> <span data-ttu-id="e9711-260">Yerel araçlar küresel olarak kullanılabilir değildir ve NuGet paketleri olarak dağıtılır.</span><span class="sxs-lookup"><span data-stu-id="e9711-260">Local tools aren't available globally and are distributed as NuGet packages.</span></span>

> [!WARNING]
> <span data-ttu-id="e9711-261">.NET Core 3,0 Preview 1 ' de veya çalıştıran gibi yerel araçlara çalıştıysanız, `dotnet tool restore` `dotnet tool install` Yerel araçlar önbellek klasörünü silin.</span><span class="sxs-lookup"><span data-stu-id="e9711-261">If you tried local tools in .NET Core 3.0 Preview 1, such as running `dotnet tool restore` or `dotnet tool install`, delete the local tools cache folder.</span></span> <span data-ttu-id="e9711-262">Aksi takdirde, yerel araçlar yeni bir sürümde çalışmaz.</span><span class="sxs-lookup"><span data-stu-id="e9711-262">Otherwise, local tools won't work on any newer release.</span></span> <span data-ttu-id="e9711-263">Bu klasör şu konumda bulunur:</span><span class="sxs-lookup"><span data-stu-id="e9711-263">This folder is located at:</span></span>
>
> <span data-ttu-id="e9711-264">MacOS 'ta Linux: `rm -r $HOME/.dotnet/toolResolverCache`</span><span class="sxs-lookup"><span data-stu-id="e9711-264">On macOS, Linux: `rm -r $HOME/.dotnet/toolResolverCache`</span></span>
>
> <span data-ttu-id="e9711-265">Windows 'da: `rmdir /s %USERPROFILE%\.dotnet\toolResolverCache`</span><span class="sxs-lookup"><span data-stu-id="e9711-265">On Windows: `rmdir /s %USERPROFILE%\.dotnet\toolResolverCache`</span></span>

<span data-ttu-id="e9711-266">Yerel araçlar, geçerli dizininizde bir bildirim dosyası adına bağımlıdır `dotnet-tools.json` .</span><span class="sxs-lookup"><span data-stu-id="e9711-266">Local tools rely on a manifest file name `dotnet-tools.json` in your current directory.</span></span> <span data-ttu-id="e9711-267">Bu bildirim dosyası, bu klasörde ve altında kullanılabilecek araçları tanımlar.</span><span class="sxs-lookup"><span data-stu-id="e9711-267">This manifest file defines the tools to be available at that folder and below.</span></span> <span data-ttu-id="e9711-268">Kodunuzla çalışan herkesin aynı araçları geri yükleyip kullanabilmesini sağlamak için, bildirim dosyasını kodunuzla dağıtabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e9711-268">You can distribute the manifest file with your code to ensure that anyone who works with your code can restore and use the same tools.</span></span>

<span data-ttu-id="e9711-269">Hem genel hem de yerel araçlar için, çalışma zamanının uyumlu bir sürümü gereklidir.</span><span class="sxs-lookup"><span data-stu-id="e9711-269">For both global and local tools, a compatible version of the runtime is required.</span></span> <span data-ttu-id="e9711-270">Şu anda NuGet.org hedef .NET Core çalışma zamanı 2,1 ' de birçok araç.</span><span class="sxs-lookup"><span data-stu-id="e9711-270">Many tools currently on NuGet.org target .NET Core Runtime 2.1.</span></span> <span data-ttu-id="e9711-271">Bu araçları küresel olarak veya yerel olarak yüklemek için, hala [NET Core 2,1 çalışma zamanını](https://dotnet.microsoft.com/download/dotnet-core/2.1)yüklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="e9711-271">To install these tools globally or locally, you would still need to install the [NET Core 2.1 Runtime](https://dotnet.microsoft.com/download/dotnet-core/2.1).</span></span>

### <a name="new-globaljson-options"></a><span data-ttu-id="e9711-272">Seçenekler üzerinde yeni global.js</span><span class="sxs-lookup"><span data-stu-id="e9711-272">New global.json options</span></span>

<span data-ttu-id="e9711-273">Dosya *global.js* , .NET Core SDK hangi sürümünün kullanıldığını tanımlamaya çalışırken daha fazla esneklik sağlayan yeni seçeneklere sahiptir.</span><span class="sxs-lookup"><span data-stu-id="e9711-273">The *global.json* file has new options that provide more flexibility when you're trying to define which version of the .NET Core SDK is used.</span></span> <span data-ttu-id="e9711-274">Yeni seçenekler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="e9711-274">The new options are:</span></span>

- <span data-ttu-id="e9711-275">`allowPrerelease`: SDK Çözümleyicisinin kullanılacak SDK sürümünü seçerken yayın öncesi sürümlerini düşünmesinin gerekip gerekmediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="e9711-275">`allowPrerelease`: Indicates whether the SDK resolver should consider prerelease versions when selecting the SDK version to use.</span></span>
- <span data-ttu-id="e9711-276">`rollForward`: Bir SDK sürümü seçerken kullanılacak yuvarlama ilkesini, belirli bir SDK sürümü eksik olduğunda geri dönüş olarak veya daha yüksek bir sürümü kullanmak için bir yönerge olarak gösterir.</span><span class="sxs-lookup"><span data-stu-id="e9711-276">`rollForward`: Indicates the roll-forward policy to use when selecting an SDK version, either as a fallback when a specific SDK version is missing or as a directive to use a higher version.</span></span>

<span data-ttu-id="e9711-277">Varsayılan değerler, desteklenen değerler ve yeni eşleştirme kuralları gibi değişiklikler hakkında daha fazla bilgi için bkz. [global.jsgenel bakış](../tools/global-json.md).</span><span class="sxs-lookup"><span data-stu-id="e9711-277">For more information about the changes including default values, supported values, and new matching rules, see [global.json overview](../tools/global-json.md).</span></span>

### <a name="smaller-garbage-collection-heap-sizes"></a><span data-ttu-id="e9711-278">Daha küçük atık toplama yığın boyutları</span><span class="sxs-lookup"><span data-stu-id="e9711-278">Smaller Garbage Collection heap sizes</span></span>

<span data-ttu-id="e9711-279">Atık toplayıcısının varsayılan yığın boyutu daha az bellek kullanan .NET Core ile sonuçlanır.</span><span class="sxs-lookup"><span data-stu-id="e9711-279">The Garbage Collector's default heap size has been reduced resulting in .NET Core using less memory.</span></span> <span data-ttu-id="e9711-280">Bu değişiklik, modern işlemci önbelleği boyutları ile nesil 0 ayırma bütçesine göre daha iyi hizalanır.</span><span class="sxs-lookup"><span data-stu-id="e9711-280">This change better aligns with the generation 0 allocation budget with modern processor cache sizes.</span></span>

### <a name="garbage-collection-large-page-support"></a><span data-ttu-id="e9711-281">Çöp toplama büyük sayfa desteği</span><span class="sxs-lookup"><span data-stu-id="e9711-281">Garbage Collection Large Page support</span></span>

<span data-ttu-id="e9711-282">Büyük sayfalar (Linux 'ta çok büyük sayfalar olarak da bilinir), işletim sisteminin bu büyük sayfaları isteyen uygulamanın performansını artırmak için yerel sayfa boyutundan (genellikle 4K) daha büyük bellek bölgeleri ayarlayabildiği bir özelliktir.</span><span class="sxs-lookup"><span data-stu-id="e9711-282">Large Pages (also known as Huge Pages on Linux) is a feature where the operating system is able to establish memory regions larger than the native page size (often 4K) to improve performance of the application requesting these large pages.</span></span>

<span data-ttu-id="e9711-283">Çöp toplayıcı artık Windows üzerinde büyük sayfalar ayırmayı seçmek için bir katılım özelliği olarak **Gclargepages** ayarıyla yapılandırılabilir.</span><span class="sxs-lookup"><span data-stu-id="e9711-283">The Garbage Collector can now be configured with the **GCLargePages** setting as an opt-in feature to choose to allocate large pages on Windows.</span></span>

## <a name="windows-desktop--com"></a><span data-ttu-id="e9711-284">Windows Masaüstü & COM</span><span class="sxs-lookup"><span data-stu-id="e9711-284">Windows Desktop & COM</span></span>

### <a name="net-core-sdk-windows-installer"></a><span data-ttu-id="e9711-285">.NET Core SDK Windows Installer</span><span class="sxs-lookup"><span data-stu-id="e9711-285">.NET Core SDK Windows Installer</span></span>

<span data-ttu-id="e9711-286">Windows için MSI Yükleyicisi, .NET Core 3,0 ile başlayarak değiştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="e9711-286">The MSI installer for Windows has changed starting with .NET Core 3.0.</span></span> <span data-ttu-id="e9711-287">SDK yükleyicileri artık SDK özelliği bant sürümlerini yerinde yükseltecektir.</span><span class="sxs-lookup"><span data-stu-id="e9711-287">The SDK installers will now upgrade SDK feature-band releases in place.</span></span> <span data-ttu-id="e9711-288">Özellik bantları, sürüm numarasının *Patch* bölümündeki *yüzlerce* grupta tanımlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="e9711-288">Feature bands are defined in the *hundreds* groups in the *patch* section of the version number.</span></span> <span data-ttu-id="e9711-289">Örneğin, \*\*3,0._ 101_ \*\* ve \*\*3,0._ 201_ \*\* , 3,0 sırasında iki farklı özellik bantlarındaki sürümleridir \*\*._ 101_ \*\* ve \*\*3,0._ 199_ \*\* aynı özellik bandında.</span><span class="sxs-lookup"><span data-stu-id="e9711-289">For example, **3.0._101_** and **3.0._201_** are versions in two different feature bands while **3.0._101_** and **3.0._199_** are in the same feature band.</span></span> <span data-ttu-id="e9711-290">.NET Core SDK \*\*3,0 olduğunda._ 101_ \*\* .NET Core SDK yüklendi, \*\*3,0._ 100_ \*\* , varsa makineden kaldırılacak.</span><span class="sxs-lookup"><span data-stu-id="e9711-290">And, when .NET Core SDK **3.0._101_** is installed, .NET Core SDK **3.0._100_** will be removed from the machine if it exists.</span></span> <span data-ttu-id="e9711-291">.NET Core SDK \*\*3,0._ 200_ \*\* , .NET Core SDK 3,0 ' de aynı makineye yüklendi \*\*._ 101_ \*\* kaldırılmaz.</span><span class="sxs-lookup"><span data-stu-id="e9711-291">When .NET Core SDK **3.0._200_** is installed on the same machine, .NET Core SDK **3.0._101_** won't be removed.</span></span>

<span data-ttu-id="e9711-292">Sürüm oluşturma hakkında daha fazla bilgi için bkz. [.NET Core 'un sürümü oluşturma konusuna genel bakış](../versions/index.md).</span><span class="sxs-lookup"><span data-stu-id="e9711-292">For more information about versioning, see [Overview of how .NET Core is versioned](../versions/index.md).</span></span>

### <a name="windows-desktop"></a><span data-ttu-id="e9711-293">Windows masaüstü</span><span class="sxs-lookup"><span data-stu-id="e9711-293">Windows desktop</span></span>

<span data-ttu-id="e9711-294">.NET Core 3,0, Windows Presentation Foundation (WPF) ve Windows Forms kullanarak Windows masaüstü uygulamalarını destekler.</span><span class="sxs-lookup"><span data-stu-id="e9711-294">.NET Core 3.0 supports Windows desktop applications using Windows Presentation Foundation (WPF) and Windows Forms.</span></span> <span data-ttu-id="e9711-295">Bu çerçeveler ayrıca, Windows UI XAML kitaplığı 'ndan (WinUI) [xaml Adaları](/windows/uwp/xaml-platform/xaml-host-controls)aracılığıyla modern denetimleri ve akıcı stil oluşturmayı da destekler.</span><span class="sxs-lookup"><span data-stu-id="e9711-295">These frameworks also support using modern controls and Fluent styling from the Windows UI XAML Library (WinUI) via [XAML islands](/windows/uwp/xaml-platform/xaml-host-controls).</span></span>

<span data-ttu-id="e9711-296">Windows Masaüstü bileşeni, Windows .NET Core 3,0 SDK 'sının bir parçasıdır.</span><span class="sxs-lookup"><span data-stu-id="e9711-296">The Windows Desktop component is part of the Windows .NET Core 3.0 SDK.</span></span>

<span data-ttu-id="e9711-297">Aşağıdaki komutlarla yeni bir WPF veya Windows Forms uygulaması oluşturabilirsiniz `dotnet` :</span><span class="sxs-lookup"><span data-stu-id="e9711-297">You can create a new WPF or Windows Forms app with the following `dotnet` commands:</span></span>

```dotnetcli
dotnet new wpf
dotnet new winforms
```

<span data-ttu-id="e9711-298">Visual Studio 2019, .NET Core 3,0 Windows Forms ve WPF için **Yeni proje** şablonları ekler.</span><span class="sxs-lookup"><span data-stu-id="e9711-298">Visual Studio 2019 adds **New Project** templates for .NET Core 3.0 Windows Forms and WPF.</span></span>

<span data-ttu-id="e9711-299">Mevcut bir .NET Framework uygulamasının bağlantı noktası hakkında daha fazla bilgi için bkz. [bağlantı noktası WPF projeleri](../../desktop-wpf/migration/convert-project-from-net-framework.md) ve [bağlantı noktası Windows Forms projeleri](../porting/winforms.md).</span><span class="sxs-lookup"><span data-stu-id="e9711-299">For more information about how to port an existing .NET Framework application, see [Port WPF projects](../../desktop-wpf/migration/convert-project-from-net-framework.md) and [Port Windows Forms projects](../porting/winforms.md).</span></span>

#### <a name="winforms-high-dpi"></a><span data-ttu-id="e9711-300">WinForms yüksek DPı</span><span class="sxs-lookup"><span data-stu-id="e9711-300">WinForms high DPI</span></span>

<span data-ttu-id="e9711-301">.NET Core Windows Forms uygulamaları, ile yüksek DPı modunu ayarlayabilir <xref:System.Windows.Forms.Application.SetHighDpiMode(System.Windows.Forms.HighDpiMode)?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="e9711-301">.NET Core Windows Forms applications can set high DPI mode with <xref:System.Windows.Forms.Application.SetHighDpiMode(System.Windows.Forms.HighDpiMode)?displayProperty=nameWithType>.</span></span> <span data-ttu-id="e9711-302">Bu `SetHighDpiMode` Yöntem, daha `App.Manifest` önce veya P/Invoke gibi diğer yollarla ayarlanmadığı takdirde, karşılık gelen yüksek DPI modunu ayarlar `Application.Run` .</span><span class="sxs-lookup"><span data-stu-id="e9711-302">The `SetHighDpiMode` method sets the corresponding high DPI mode unless the setting has been set by other means like `App.Manifest` or P/Invoke before `Application.Run`.</span></span>

<span data-ttu-id="e9711-303">`highDpiMode`Sabit listesi tarafından ifade edilen olası değerler <xref:System.Windows.Forms.HighDpiMode?displayProperty=nameWithType> şunlardır:</span><span class="sxs-lookup"><span data-stu-id="e9711-303">The possible `highDpiMode` values, as expressed by the <xref:System.Windows.Forms.HighDpiMode?displayProperty=nameWithType> enum are:</span></span>

- `DpiUnaware`
- `SystemAware`
- `PerMonitor`
- `PerMonitorV2`
- `DpiUnawareGdiScaled`

<span data-ttu-id="e9711-304">Yüksek DPı modları hakkında daha fazla bilgi için bkz. [Windows 'Da yüksek DPI Masaüstü uygulama geliştirme](/windows/desktop/hidpi/high-dpi-desktop-application-development-on-windows).</span><span class="sxs-lookup"><span data-stu-id="e9711-304">For more information about high DPI modes, see [High DPI Desktop Application Development on Windows](/windows/desktop/hidpi/high-dpi-desktop-application-development-on-windows).</span></span>

### <a name="create-com-components"></a><span data-ttu-id="e9711-305">COM bileşenleri oluşturma</span><span class="sxs-lookup"><span data-stu-id="e9711-305">Create COM components</span></span>

<span data-ttu-id="e9711-306">Windows 'ta artık COM çağrılabilir yönetilen bileşenler oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e9711-306">On Windows, you can now create COM-callable managed components.</span></span> <span data-ttu-id="e9711-307">Bu özellik, .NET Core 'un COM eklenti modelleriyle kullanılması ve ayrıca .NET Framework eşlik sağlanması açısından önemlidir.</span><span class="sxs-lookup"><span data-stu-id="e9711-307">This capability is critical to use .NET Core with COM add-in models and also to provide parity with .NET Framework.</span></span>

<span data-ttu-id="e9711-308">*mscoree.dll* com sunucusu olarak kullanıldığı .NET Framework aksine, .NET Core, com bileşenini oluştururken *bin* dizinine yerel bir başlatıcı dll 'si ekler.</span><span class="sxs-lookup"><span data-stu-id="e9711-308">Unlike .NET Framework where the *mscoree.dll* was used as the COM server, .NET Core will add a native launcher dll to the *bin* directory when you build your COM component.</span></span>

<span data-ttu-id="e9711-309">COM bileşeni oluşturma ve kullanma hakkında bir örnek için bkz. [com tanıtımı](https://github.com/dotnet/samples/tree/master/core/extensions/COMServerDemo).</span><span class="sxs-lookup"><span data-stu-id="e9711-309">For an example of how to create a COM component and consume it, see the [COM Demo](https://github.com/dotnet/samples/tree/master/core/extensions/COMServerDemo).</span></span>

### <a name="windows-native-interop"></a><span data-ttu-id="e9711-310">Windows yerel birlikte çalışma</span><span class="sxs-lookup"><span data-stu-id="e9711-310">Windows Native Interop</span></span>

<span data-ttu-id="e9711-311">Windows, düz C API 'Leri, COM ve WinRT biçiminde zengin bir yerel API sunar.</span><span class="sxs-lookup"><span data-stu-id="e9711-311">Windows offers a rich native API in the form of flat C APIs, COM, and WinRT.</span></span> <span data-ttu-id="e9711-312">.NET Core **P/Invoke**'ı destekleirken, .net Core 3,0, **com API 'Leri oluşturma** ve **WinRT API 'leri etkinleştirme**özelliğini ekler.</span><span class="sxs-lookup"><span data-stu-id="e9711-312">While .NET Core supports **P/Invoke**, .NET Core 3.0 adds the ability to **CoCreate COM APIs** and **Activate WinRT APIs**.</span></span> <span data-ttu-id="e9711-313">Kod örneği için bkz. [Excel tanıtımı](https://github.com/dotnet/samples/tree/master/core/extensions/ExcelDemo).</span><span class="sxs-lookup"><span data-stu-id="e9711-313">For a code example, see the [Excel Demo](https://github.com/dotnet/samples/tree/master/core/extensions/ExcelDemo).</span></span>

### <a name="msix-deployment"></a><span data-ttu-id="e9711-314">MSIX dağıtımı</span><span class="sxs-lookup"><span data-stu-id="e9711-314">MSIX Deployment</span></span>

<span data-ttu-id="e9711-315">[Msix](/windows/msix/) yeni bir Windows uygulama paketi biçimidir.</span><span class="sxs-lookup"><span data-stu-id="e9711-315">[MSIX](/windows/msix/) is a new Windows application package format.</span></span> <span data-ttu-id="e9711-316">.NET Core 3,0 masaüstü uygulamalarını Windows 10 ' a dağıtmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="e9711-316">It can be used to deploy .NET Core 3.0 desktop applications to Windows 10.</span></span>

<span data-ttu-id="e9711-317">Visual Studio 2019 ' de bulunan [Windows uygulama paketleme projesi](/windows/uwp/porting/desktop-to-uwp-packaging-dot-net), [kendi kendine içerilen](../deploying/index.md#publish-self-contained) .NET Core uygulamalarıyla msix paketi oluşturmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="e9711-317">The [Windows Application Packaging Project](/windows/uwp/porting/desktop-to-uwp-packaging-dot-net), available in Visual Studio 2019, allows you to create MSIX packages with [self-contained](../deploying/index.md#publish-self-contained) .NET Core applications.</span></span>

<span data-ttu-id="e9711-318">.NET Core proje dosyası, özelliğindeki desteklenen çalışma zamanlarını belirtmelidir `<RuntimeIdentifiers>` :</span><span class="sxs-lookup"><span data-stu-id="e9711-318">The .NET Core project file must specify the supported runtimes in the `<RuntimeIdentifiers>` property:</span></span>

```xml
<RuntimeIdentifiers>win-x86;win-x64</RuntimeIdentifiers>
```

## <a name="linux-improvements"></a><span data-ttu-id="e9711-319">Linux geliştirmeleri</span><span class="sxs-lookup"><span data-stu-id="e9711-319">Linux improvements</span></span>

### <a name="serialport-for-linux"></a><span data-ttu-id="e9711-320">Linux için SerialPort</span><span class="sxs-lookup"><span data-stu-id="e9711-320">SerialPort for Linux</span></span>

<span data-ttu-id="e9711-321">.NET Core 3,0, Linux üzerinde için temel desteği sağlar <xref:System.IO.Ports.SerialPort?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="e9711-321">.NET Core 3.0 provides basic support for <xref:System.IO.Ports.SerialPort?displayProperty=nameWithType> on Linux.</span></span>

<span data-ttu-id="e9711-322">Daha önce, .NET Core yalnızca `SerialPort` Windows 'da kullanımı desteklenir.</span><span class="sxs-lookup"><span data-stu-id="e9711-322">Previously, .NET Core only supported using `SerialPort` on Windows.</span></span>

<span data-ttu-id="e9711-323">Linux 'ta seri bağlantı noktası için sınırlı destek hakkında daha fazla bilgi için bkz. [GitHub sorun #33146](https://github.com/dotnet/corefx/issues/33146).</span><span class="sxs-lookup"><span data-stu-id="e9711-323">For more information about the limited support for the serial port on Linux, see [GitHub issue #33146](https://github.com/dotnet/corefx/issues/33146).</span></span>

### <a name="docker-and-cgroup-memory-limits"></a><span data-ttu-id="e9711-324">Docker ve cgroup bellek sınırları</span><span class="sxs-lookup"><span data-stu-id="e9711-324">Docker and cgroup memory Limits</span></span>

<span data-ttu-id="e9711-325">Docker ile Linux üzerinde .NET Core 3,0 çalıştırmak, cgroup bellek limitleriyle daha iyi çalışır.</span><span class="sxs-lookup"><span data-stu-id="e9711-325">Running .NET Core 3.0 on Linux with Docker works better with cgroup memory limits.</span></span> <span data-ttu-id="e9711-326">İle gibi bellek limitleriyle bir Docker kapsayıcısı çalıştırmak `docker run -m` , .NET Core 'un davranış şeklini değiştirir.</span><span class="sxs-lookup"><span data-stu-id="e9711-326">Running a Docker container with memory limits, such as with `docker run -m`, changes how .NET Core behaves.</span></span>

- <span data-ttu-id="e9711-327">Varsayılan atık toplayıcı (GC) yığın boyutu: kapsayıcıda bellek sınırının en fazla 20 MB veya %75 ' si.</span><span class="sxs-lookup"><span data-stu-id="e9711-327">Default Garbage Collector (GC) heap size: maximum of 20 mb or 75% of the memory limit on the container.</span></span>
- <span data-ttu-id="e9711-328">Açık Boyut, mutlak bir sayı veya cgroup sınırının yüzdesi olarak ayarlanabilir.</span><span class="sxs-lookup"><span data-stu-id="e9711-328">Explicit size can be set as an absolute number or percentage of cgroup limit.</span></span>
- <span data-ttu-id="e9711-329">GC yığını başına en düşük ayrılmış kesim boyutu 16 MB 'tır.</span><span class="sxs-lookup"><span data-stu-id="e9711-329">Minimum reserved segment size per GC heap is 16 mb.</span></span> <span data-ttu-id="e9711-330">Bu boyut, makinelerde oluşturulan Heap sayısını azaltır.</span><span class="sxs-lookup"><span data-stu-id="e9711-330">This size reduces the number of heaps that are created on machines.</span></span>

### <a name="gpio-support-for-raspberry-pi"></a><span data-ttu-id="e9711-331">Raspberry PI için GıO desteği</span><span class="sxs-lookup"><span data-stu-id="e9711-331">GPIO Support for Raspberry Pi</span></span>

<span data-ttu-id="e9711-332">NuGet 'e GıO programlama için kullanabileceğiniz iki paket yayımlanmıştır:</span><span class="sxs-lookup"><span data-stu-id="e9711-332">Two packages have been released to NuGet that you can use for GPIO programming:</span></span>

- [<span data-ttu-id="e9711-333">System. Device. GIO</span><span class="sxs-lookup"><span data-stu-id="e9711-333">System.Device.Gpio</span></span>](https://www.nuget.org/packages/System.Device.Gpio)
- [<span data-ttu-id="e9711-334">IoT. Device. Bindings</span><span class="sxs-lookup"><span data-stu-id="e9711-334">Iot.Device.Bindings</span></span>](https://www.nuget.org/packages/Iot.Device.Bindings)

<span data-ttu-id="e9711-335">GPıO paketleri, *GIO*, *SPI*, *I2C*ve *PWM* cihazları için API 'ler içerir.</span><span class="sxs-lookup"><span data-stu-id="e9711-335">The GPIO packages include APIs for *GPIO*, *SPI*, *I2C*, and *PWM* devices.</span></span> <span data-ttu-id="e9711-336">IoT bağlamaları paketi cihaz bağlamalarını içerir.</span><span class="sxs-lookup"><span data-stu-id="e9711-336">The IoT bindings package includes device bindings.</span></span> <span data-ttu-id="e9711-337">Daha fazla bilgi için bkz. [cihaz GitHub deposu](https://github.com/dotnet/iot/blob/master/src/devices/).</span><span class="sxs-lookup"><span data-stu-id="e9711-337">For more information, see the [devices GitHub repo](https://github.com/dotnet/iot/blob/master/src/devices/).</span></span>

### <a name="arm64-linux-support"></a><span data-ttu-id="e9711-338">ARM64 Linux desteği</span><span class="sxs-lookup"><span data-stu-id="e9711-338">ARM64 Linux support</span></span>

<span data-ttu-id="e9711-339">.NET Core 3,0, Linux için ARM64 desteği ekler.</span><span class="sxs-lookup"><span data-stu-id="e9711-339">.NET Core 3.0 adds support for ARM64 for Linux.</span></span> <span data-ttu-id="e9711-340">ARM64 için birincil kullanım örneği şu anda IoT senaryolarıyla birlikte.</span><span class="sxs-lookup"><span data-stu-id="e9711-340">The primary use case for ARM64 is currently with IoT scenarios.</span></span> <span data-ttu-id="e9711-341">Daha fazla bilgi için bkz. [.NET Core ARM64 Status](https://github.com/dotnet/announcements/issues/82).</span><span class="sxs-lookup"><span data-stu-id="e9711-341">For more information, see [.NET Core ARM64 Status](https://github.com/dotnet/announcements/issues/82).</span></span>

<span data-ttu-id="e9711-342">[ARM64 üzerinde .NET Core Için Docker görüntüleri](https://hub.docker.com/r/microsoft/dotnet/) alp, de, ve Ubuntu için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="e9711-342">[Docker images for .NET Core on ARM64](https://hub.docker.com/r/microsoft/dotnet/) are available for Alpine, Debian, and Ubuntu.</span></span>

> [!NOTE]
> <span data-ttu-id="e9711-343">**ARM64** Windows desteği henüz kullanılamıyor.</span><span class="sxs-lookup"><span data-stu-id="e9711-343">**ARM64** Windows support isn't yet available.</span></span>

## <a name="security"></a><span data-ttu-id="e9711-344">Güvenlik</span><span class="sxs-lookup"><span data-stu-id="e9711-344">Security</span></span>

### <a name="tls-13--openssl-111-on-linux"></a><span data-ttu-id="e9711-345">TLS 1,3 & Linux üzerinde OpenSSL 1.1.1</span><span class="sxs-lookup"><span data-stu-id="e9711-345">TLS 1.3 & OpenSSL 1.1.1 on Linux</span></span>

<span data-ttu-id="e9711-346">.NET Core artık, belirli bir ortamda kullanılabildiği [OpenSSL 1.1.1 Içindeki TLS 1,3 desteğinin](https://www.openssl.org/blog/blog/2018/09/11/release111/)avantajlarından yararlanır.</span><span class="sxs-lookup"><span data-stu-id="e9711-346">.NET Core now takes advantage of [TLS 1.3 support in OpenSSL 1.1.1](https://www.openssl.org/blog/blog/2018/09/11/release111/), when it's available in a given environment.</span></span> <span data-ttu-id="e9711-347">TLS 1,3:</span><span class="sxs-lookup"><span data-stu-id="e9711-347">With TLS 1.3:</span></span>

- <span data-ttu-id="e9711-348">İstemci ve sunucu arasında gereken azaltılan gidiş dönüşlerle bağlantı süreleri geliştirildi.</span><span class="sxs-lookup"><span data-stu-id="e9711-348">Connection times are improved with reduced round trips required between the client and server.</span></span>
- <span data-ttu-id="e9711-349">Kullanılmayan ve güvenli olmayan şifreleme algoritmalarının kaldırılması nedeniyle güvenlik geliştirildi.</span><span class="sxs-lookup"><span data-stu-id="e9711-349">Improved security because of the removal of various obsolete and insecure cryptographic algorithms.</span></span>

<span data-ttu-id="e9711-350">Kullanılabilir olduğunda, .NET Core 3,0 bir Linux sisteminde **OpenSSL 1.1.1**, **OpenSSL 1.1.0**veya **OpenSSL 1.0.2** kullanır.</span><span class="sxs-lookup"><span data-stu-id="e9711-350">When available, .NET Core 3.0 uses **OpenSSL 1.1.1**, **OpenSSL 1.1.0**, or **OpenSSL 1.0.2** on a Linux system.</span></span> <span data-ttu-id="e9711-351">**OpenSSL 1.1.1** kullanılabilir olduğunda, her ikisi <xref:System.Net.Security.SslStream?displayProperty=nameWithType> de <xref:System.Net.Http.HttpClient?displayProperty=nameWithType> tür **TLS 1,3** kullanır (istemci ve sunucunun **TLS 1,3**' i desteklediği varsayıldığında).</span><span class="sxs-lookup"><span data-stu-id="e9711-351">When **OpenSSL 1.1.1** is available, both <xref:System.Net.Security.SslStream?displayProperty=nameWithType> and <xref:System.Net.Http.HttpClient?displayProperty=nameWithType> types will use **TLS 1.3** (assuming both the client and server support **TLS 1.3**).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e9711-352">Windows ve macOS henüz **TLS 1,3**' i desteklemez.</span><span class="sxs-lookup"><span data-stu-id="e9711-352">Windows and macOS do not yet support **TLS 1.3**.</span></span> <span data-ttu-id="e9711-353">.NET Core 3,0, destek kullanılabilir hale geldiğinde bu işletim sistemlerinde **TLS 1,3** ' i destekleyecektir.</span><span class="sxs-lookup"><span data-stu-id="e9711-353">.NET Core 3.0 will support **TLS 1.3** on these operating systems when support becomes available.</span></span>

<span data-ttu-id="e9711-354">Aşağıdaki C# 8,0 örneği, ' a bağlanan Ubuntu 18,10 üzerinde .NET Core 3,0 ' i göstermektedir <https://www.cloudflare.com> :</span><span class="sxs-lookup"><span data-stu-id="e9711-354">The following C# 8.0 example demonstrates .NET Core 3.0 on Ubuntu 18.10 connecting to <https://www.cloudflare.com>:</span></span>

[!code-csharp[TLSExample](./snippets/dotnet-core-3-0/csharp/TLS.cs#TLS)]

### <a name="cryptography-ciphers"></a><span data-ttu-id="e9711-355">Şifreleme şifrelemeleri</span><span class="sxs-lookup"><span data-stu-id="e9711-355">Cryptography ciphers</span></span>

<span data-ttu-id="e9711-356">.NET 3,0, ile ve sırasıyla uygulanan **AES-GCM** ve **AES-CCM** şifrelemeleri için destek ekler <xref:System.Security.Cryptography.AesGcm?displayProperty=nameWithType> <xref:System.Security.Cryptography.AesCcm?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="e9711-356">.NET 3.0 adds support for **AES-GCM** and **AES-CCM** ciphers, implemented with <xref:System.Security.Cryptography.AesGcm?displayProperty=nameWithType> and <xref:System.Security.Cryptography.AesCcm?displayProperty=nameWithType> respectively.</span></span> <span data-ttu-id="e9711-357">Bu algoritmalar, [Ilişki verileri (AEAD) algoritmalarıyla kimliği doğrulanmış şifrelemedir](https://en.wikipedia.org/wiki/Authenticated_encryption).</span><span class="sxs-lookup"><span data-stu-id="e9711-357">These algorithms are both [Authenticated Encryption with Association Data (AEAD) algorithms](https://en.wikipedia.org/wiki/Authenticated_encryption).</span></span>

<span data-ttu-id="e9711-358">Aşağıdaki kod, `AesGcm` rastgele verileri şifrelemek ve şifrelerini çözmek için şifre kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="e9711-358">The following code demonstrates using `AesGcm` cipher to encrypt and decrypt random data.</span></span>

[!code-csharp[AesGcm](./snippets/dotnet-core-3-0/csharp/Cipher.cs#AesGcm)]

### <a name="cryptographic-key-importexport"></a><span data-ttu-id="e9711-359">Şifreleme anahtarı Içeri/dışarı aktarma</span><span class="sxs-lookup"><span data-stu-id="e9711-359">Cryptographic Key Import/Export</span></span>

<span data-ttu-id="e9711-360">.NET Core 3,0, asimetrik ortak ve özel anahtarların standart biçimlerden içeri ve dışarı aktarılmasını destekler.</span><span class="sxs-lookup"><span data-stu-id="e9711-360">.NET Core 3.0 supports the import and export of asymmetric public and private keys from standard formats.</span></span> <span data-ttu-id="e9711-361">X. 509.440 sertifikası kullanmanız gerekmez.</span><span class="sxs-lookup"><span data-stu-id="e9711-361">You don't need to use an X.509 certificate.</span></span>

<span data-ttu-id="e9711-362">*RSA*, *dsa*, *ECDSA*ve *ecdıfıfiehellman*gibi tüm anahtar türleri aşağıdaki biçimleri destekler:</span><span class="sxs-lookup"><span data-stu-id="e9711-362">All key types, such as *RSA*, *DSA*, *ECDsa*, and *ECDiffieHellman*, support the following formats:</span></span>

- <span data-ttu-id="e9711-363">**Ortak Anahtar**</span><span class="sxs-lookup"><span data-stu-id="e9711-363">**Public Key**</span></span>
  - <span data-ttu-id="e9711-364">X. 509.440 Subjectpublickeyınfo</span><span class="sxs-lookup"><span data-stu-id="e9711-364">X.509 SubjectPublicKeyInfo</span></span>

- <span data-ttu-id="e9711-365">**Özel anahtar**</span><span class="sxs-lookup"><span data-stu-id="e9711-365">**Private key**</span></span>
  - <span data-ttu-id="e9711-366">PKCS # 8 Privatekeyınfo</span><span class="sxs-lookup"><span data-stu-id="e9711-366">PKCS#8 PrivateKeyInfo</span></span>
  - <span data-ttu-id="e9711-367">PKCS # 8 Encryptedprivatekeyınfo</span><span class="sxs-lookup"><span data-stu-id="e9711-367">PKCS#8 EncryptedPrivateKeyInfo</span></span>

<span data-ttu-id="e9711-368">RSA anahtarları da şunları destekler:</span><span class="sxs-lookup"><span data-stu-id="e9711-368">RSA keys also support:</span></span>

- <span data-ttu-id="e9711-369">**Ortak Anahtar**</span><span class="sxs-lookup"><span data-stu-id="e9711-369">**Public Key**</span></span>
  - <span data-ttu-id="e9711-370">PKCS # 1 RSAPublicKey</span><span class="sxs-lookup"><span data-stu-id="e9711-370">PKCS#1 RSAPublicKey</span></span>

- <span data-ttu-id="e9711-371">**Özel anahtar**</span><span class="sxs-lookup"><span data-stu-id="e9711-371">**Private key**</span></span>
  - <span data-ttu-id="e9711-372">PKCS # 1 RSAPrivateKey</span><span class="sxs-lookup"><span data-stu-id="e9711-372">PKCS#1 RSAPrivateKey</span></span>

<span data-ttu-id="e9711-373">Dışarı aktarma yöntemleri DER kodlu ikili veriler oluşturur ve içeri aktarma yöntemleri aynı şekilde bekler.</span><span class="sxs-lookup"><span data-stu-id="e9711-373">The export methods produce DER-encoded binary data, and the import methods expect the same.</span></span> <span data-ttu-id="e9711-374">Bir anahtar, metin kullanımı kolay pek biçiminde depolanıyorsa, bir içeri aktarma yöntemi çağrılmadan önce çağıranın içerik Base64 olarak çözülmesi gerekecektir.</span><span class="sxs-lookup"><span data-stu-id="e9711-374">If a key is stored in the text-friendly PEM format, the caller will need to base64-decode the content before calling an import method.</span></span>

[!code-csharp[RSA](./snippets/dotnet-core-3-0/csharp/RSA.cs#Rsa)]

<span data-ttu-id="e9711-375">**PKCS # 8** dosyaları ile incelenebilir <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo?displayProperty=nameWithType> ve **PFX/PKCS # 12** dosyaları ile incelenebilir <xref:System.Security.Cryptography.Pkcs.Pkcs12Info?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="e9711-375">**PKCS#8** files can be inspected with <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo?displayProperty=nameWithType> and **PFX/PKCS#12** files can be inspected with <xref:System.Security.Cryptography.Pkcs.Pkcs12Info?displayProperty=nameWithType>.</span></span> <span data-ttu-id="e9711-376">**PFX/PKCS # 12** dosyaları ile değiştirilebilir <xref:System.Security.Cryptography.Pkcs.Pkcs12Builder?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="e9711-376">**PFX/PKCS#12** files can be manipulated with <xref:System.Security.Cryptography.Pkcs.Pkcs12Builder?displayProperty=nameWithType>.</span></span>

## <a name="net-core-30-api-changes"></a><span data-ttu-id="e9711-377">.NET Core 3,0 API değişiklikleri</span><span class="sxs-lookup"><span data-stu-id="e9711-377">.NET Core 3.0 API changes</span></span>

### <a name="ranges-and-indices"></a><span data-ttu-id="e9711-378">Aralıklar ve dizinler</span><span class="sxs-lookup"><span data-stu-id="e9711-378">Ranges and indices</span></span>

<span data-ttu-id="e9711-379">Yeni <xref:System.Index?displayProperty=nameWithType> tür dizin oluşturmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="e9711-379">The new <xref:System.Index?displayProperty=nameWithType> type can be used for indexing.</span></span> <span data-ttu-id="e9711-380">`int`Başlangıçtan başlayarak bu saylardan bir tane veya sonundan daha fazla `^` sayan bir önek Işleci (C#) oluşturabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="e9711-380">You can create one from an `int` that counts from the beginning, or with a prefix `^` operator (C#) that counts from the end:</span></span>

```csharp
Index i1 = 3;  // number 3 from beginning
Index i2 = ^4; // number 4 from end
int[] a = { 0, 1, 2, 3, 4, 5, 6, 7, 8, 9 };
Console.WriteLine($"{a[i1]}, {a[i2]}"); // "3, 6"
```

<span data-ttu-id="e9711-381">Ayrıca, <xref:System.Range?displayProperty=nameWithType> `Index` biri başlangıç ve diğeri bitiş için olmak üzere iki değerden oluşan ve bir `x..y` Aralık Ifadesiyle (C#) yazılabilir bir tür de vardır.</span><span class="sxs-lookup"><span data-stu-id="e9711-381">There's also the <xref:System.Range?displayProperty=nameWithType> type, which consists of two `Index` values, one for the start and one for the end, and can be written with a `x..y` range expression (C#).</span></span> <span data-ttu-id="e9711-382">Daha sonra bir dilim üreten bir ile dizin oluşturabilirsiniz `Range` :</span><span class="sxs-lookup"><span data-stu-id="e9711-382">You can then index with a `Range`, which produces a slice:</span></span>

```csharp
var slice = a[i1..i2]; // { 3, 4, 5 }
```

<span data-ttu-id="e9711-383">Daha fazla bilgi için [aralıklar ve dizinler öğreticisine](../../csharp/tutorials/ranges-indexes.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="e9711-383">For more information, see the [ranges and indices tutorial](../../csharp/tutorials/ranges-indexes.md).</span></span>

### <a name="async-streams"></a><span data-ttu-id="e9711-384">Zaman uyumsuz akışlar</span><span class="sxs-lookup"><span data-stu-id="e9711-384">Async streams</span></span>

<span data-ttu-id="e9711-385"><xref:System.Collections.Generic.IAsyncEnumerable%601>Türü yeni bir zaman uyumsuz sürümüdür <xref:System.Collections.Generic.IEnumerable%601> .</span><span class="sxs-lookup"><span data-stu-id="e9711-385">The <xref:System.Collections.Generic.IAsyncEnumerable%601> type is a new asynchronous version of <xref:System.Collections.Generic.IEnumerable%601>.</span></span> <span data-ttu-id="e9711-386">Dil, `await foreach` `IAsyncEnumerable<T>` öğelerini tüketmek ve `yield return` öğeleri oluşturmak için bunları kullanmak için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e9711-386">The language lets you `await foreach` over `IAsyncEnumerable<T>` to consume their elements, and use `yield return` to them to produce elements.</span></span>

<span data-ttu-id="e9711-387">Aşağıdaki örnek, zaman uyumsuz akışların hem üretimini hem de tüketimini gösterir.</span><span class="sxs-lookup"><span data-stu-id="e9711-387">The following example demonstrates both production and consumption of async streams.</span></span> <span data-ttu-id="e9711-388">`foreach`Bildirim zaman uyumsuz ve kendisi `yield return` çağıranlar için zaman uyumsuz akış üretmek için kullanır.</span><span class="sxs-lookup"><span data-stu-id="e9711-388">The `foreach` statement is async and itself uses `yield return` to produce an async stream for callers.</span></span> <span data-ttu-id="e9711-389">Bu model (kullanılarak `yield return` ), zaman uyumsuz akışlar üretmek için önerilen modeldir.</span><span class="sxs-lookup"><span data-stu-id="e9711-389">This pattern (using `yield return`) is the recommended model for producing async streams.</span></span>

```csharp
async IAsyncEnumerable<int> GetBigResultsAsync()
{
    await foreach (var result in GetResultsAsync())
    {
        if (result > 20) yield return result;
    }
}
```

<span data-ttu-id="e9711-390">`await foreach`Ayrıca, zaman uyumsuz yineleyiciler da oluşturabilirsiniz, örneğin, `IAsyncEnumerable/IAsyncEnumerator` hem hem `await` de içinde kullanabileceğiniz bir yineleyici `yield` .</span><span class="sxs-lookup"><span data-stu-id="e9711-390">In addition to being able to `await foreach`, you can also create async iterators, for example, an iterator that returns an `IAsyncEnumerable/IAsyncEnumerator` that you can both `await` and `yield` in.</span></span> <span data-ttu-id="e9711-391">Atılmalıdır, `IAsyncDisposable` ve gibi ÇEŞITLI BCL türlerini uygulayan ' i kullanabilirsiniz `Stream` `Timer` .</span><span class="sxs-lookup"><span data-stu-id="e9711-391">For objects that need to be disposed, you can use `IAsyncDisposable`, which various BCL types implement, such as `Stream` and `Timer`.</span></span>

<span data-ttu-id="e9711-392">Daha fazla bilgi için bkz. [zaman uyumsuz akışlar öğreticisi](../../csharp/tutorials/generate-consume-asynchronous-stream.md).</span><span class="sxs-lookup"><span data-stu-id="e9711-392">For more information, see the [async streams tutorial](../../csharp/tutorials/generate-consume-asynchronous-stream.md).</span></span>

### <a name="ieee-floating-point"></a><span data-ttu-id="e9711-393">IEEE kayan nokta</span><span class="sxs-lookup"><span data-stu-id="e9711-393">IEEE Floating-point</span></span>

<span data-ttu-id="e9711-394">Kayan nokta API 'Leri, [ıeee 754-2008 düzeltmesine](https://en.wikipedia.org/wiki/IEEE_754-2008_revision)uymak üzere güncelleştiriliyor.</span><span class="sxs-lookup"><span data-stu-id="e9711-394">Floating point APIs are being updated to comply with [IEEE 754-2008 revision](https://en.wikipedia.org/wiki/IEEE_754-2008_revision).</span></span> <span data-ttu-id="e9711-395">Bu değişikliklerin amacı, tüm **gerekli** işlemleri kullanıma sunmaktır ve DAVRANıŞSAL 'in IEEE spec ile uyumlu olduklarından emin olmaktır. Kayan nokta iyileştirmeleri hakkında daha fazla bilgi için bkz. [.NET Core 3,0 blog gönderisine kayan nokta ayrıştırma ve biçimlendirme geliştirmeleri](https://devblogs.microsoft.com/dotnet/floating-point-parsing-and-formatting-improvements-in-net-core-3-0/) .</span><span class="sxs-lookup"><span data-stu-id="e9711-395">The goal of these changes is to expose all **required** operations and ensure that they're behaviorally compliant with the IEEE spec. For more information about floating-point improvements, see the [Floating-Point Parsing and Formatting improvements in .NET Core 3.0](https://devblogs.microsoft.com/dotnet/floating-point-parsing-and-formatting-improvements-in-net-core-3-0/) blog post.</span></span>

<span data-ttu-id="e9711-396">Ayrıştırma ve biçimlendirme düzeltmeleri şunları içerir:</span><span class="sxs-lookup"><span data-stu-id="e9711-396">Parsing and formatting fixes include:</span></span>

- <span data-ttu-id="e9711-397">Her uzunlukta doğru şekilde ayrıştırma ve yuvarlama girişleri.</span><span class="sxs-lookup"><span data-stu-id="e9711-397">Correctly parse and round inputs of any length.</span></span>
- <span data-ttu-id="e9711-398">Doğru şekilde ayrıştırır ve negatif sıfır biçimlendirir.</span><span class="sxs-lookup"><span data-stu-id="e9711-398">Correctly parse and format negative zero.</span></span>
- <span data-ttu-id="e9711-399">`Infinity` `NaN` Büyük/küçük harfe duyarsız bir denetim yaparak ve uygunsa isteğe bağlı olarak daha önce izin vererek doğru şekilde ayrıştırılabilir `+` .</span><span class="sxs-lookup"><span data-stu-id="e9711-399">Correctly parse `Infinity` and `NaN` by doing a case-insensitive check and allowing an optional preceding `+` where applicable.</span></span>

<span data-ttu-id="e9711-400">Yeni <xref:System.Math?displayProperty=nameWithType> API 'ler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="e9711-400">New <xref:System.Math?displayProperty=nameWithType> APIs include:</span></span>

- <span data-ttu-id="e9711-401"><xref:System.Math.BitIncrement(System.Double)> ' <xref:System.Math.BitDecrement(System.Double)></span><span class="sxs-lookup"><span data-stu-id="e9711-401"><xref:System.Math.BitIncrement(System.Double)> and <xref:System.Math.BitDecrement(System.Double)></span></span>\
<span data-ttu-id="e9711-402">`nextUp`Ve `nextDown` IEEE işlemlerine karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="e9711-402">Corresponds to the `nextUp` and `nextDown` IEEE operations.</span></span> <span data-ttu-id="e9711-403">Bunlar, girdiden daha büyük veya daha az (sırasıyla) karşılaştıran en küçük kayan nokta numarasını döndürür.</span><span class="sxs-lookup"><span data-stu-id="e9711-403">They return the smallest floating-point number that compares greater or lesser than the input (respectively).</span></span> <span data-ttu-id="e9711-404">Örneğin, `Math.BitIncrement(0.0)` döndürür `double.Epsilon` .</span><span class="sxs-lookup"><span data-stu-id="e9711-404">For example, `Math.BitIncrement(0.0)` would return `double.Epsilon`.</span></span>

- <span data-ttu-id="e9711-405"><xref:System.Math.MaxMagnitude(System.Double,System.Double)> ' <xref:System.Math.MinMagnitude(System.Double,System.Double)></span><span class="sxs-lookup"><span data-stu-id="e9711-405"><xref:System.Math.MaxMagnitude(System.Double,System.Double)> and <xref:System.Math.MinMagnitude(System.Double,System.Double)></span></span>\
<span data-ttu-id="e9711-406">`maxNumMag`Ve `minNumMag` IEEE işlemlerine karşılık gelen değeri, iki girişin büyüklüğüne daha büyük veya daha az (sırasıyla) döndürür.</span><span class="sxs-lookup"><span data-stu-id="e9711-406">Corresponds to the `maxNumMag` and `minNumMag` IEEE operations, they return the value that is greater or lesser in magnitude of the two inputs (respectively).</span></span> <span data-ttu-id="e9711-407">Örneğin, `Math.MaxMagnitude(2.0, -3.0)` döndürür `-3.0` .</span><span class="sxs-lookup"><span data-stu-id="e9711-407">For example, `Math.MaxMagnitude(2.0, -3.0)` would return `-3.0`.</span></span>

- <xref:System.Math.ILogB(System.Double)>\
<span data-ttu-id="e9711-408">`logB`Bir integral değeri döndüren IEEE işlemine karşılık gelir, giriş parametresinin tamsayı taban 2 günlüğünü döndürür.</span><span class="sxs-lookup"><span data-stu-id="e9711-408">Corresponds to the `logB` IEEE operation that returns an integral value, it returns the integral base-2 log of the input parameter.</span></span> <span data-ttu-id="e9711-409">Bu yöntem, ile aynı şekilde, `floor(log2(x))` ancak en az yuvarlama hatasıyla yapılır.</span><span class="sxs-lookup"><span data-stu-id="e9711-409">This method is effectively the same as `floor(log2(x))`, but done with minimal rounding error.</span></span>

- <xref:System.Math.ScaleB(System.Double,System.Int32)>\
<span data-ttu-id="e9711-410">`scaleB`Bir tamsayı değeri alan IEEE işlemine karşılık gelir, etkin `x * pow(2, n)` olarak döner, ancak en az yuvarlama hatasıyla yapılır.</span><span class="sxs-lookup"><span data-stu-id="e9711-410">Corresponds to the `scaleB` IEEE operation that takes an integral value, it returns effectively `x * pow(2, n)`, but is done with minimal rounding error.</span></span>

- <xref:System.Math.Log2(System.Double)>\
<span data-ttu-id="e9711-411">`log2`IEEE işlemine karşılık gelen 2 tabanında logaritmasını döndürür.</span><span class="sxs-lookup"><span data-stu-id="e9711-411">Corresponds to the `log2` IEEE operation, it returns the base-2 logarithm.</span></span> <span data-ttu-id="e9711-412">Yuvarlama hatasını en aza indirir.</span><span class="sxs-lookup"><span data-stu-id="e9711-412">It minimizes rounding error.</span></span>

- <xref:System.Math.FusedMultiplyAdd(System.Double,System.Double,System.Double)>\
<span data-ttu-id="e9711-413">`fma`IEEE işlemine karşılık gelen bir fkullandınız çarpma eklemesi gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="e9711-413">Corresponds to the `fma` IEEE operation, it performs a fused multiply add.</span></span> <span data-ttu-id="e9711-414">Yani, `(x * y) + z` tek bir işlem olarak yapılır, böylece yuvarlama hatasını en aza indirir.</span><span class="sxs-lookup"><span data-stu-id="e9711-414">That is, it does `(x * y) + z` as a single operation, thereby minimizing the rounding error.</span></span> <span data-ttu-id="e9711-415">Bir örnek `FusedMultiplyAdd(1e308, 2.0, -1e308)` , döndürür `1e308` .</span><span class="sxs-lookup"><span data-stu-id="e9711-415">An example is `FusedMultiplyAdd(1e308, 2.0, -1e308)`, which returns `1e308`.</span></span> <span data-ttu-id="e9711-416">Normal `(1e308 * 2.0) - 1e308` dönüşler `double.PositiveInfinity` .</span><span class="sxs-lookup"><span data-stu-id="e9711-416">The regular `(1e308 * 2.0) - 1e308` returns `double.PositiveInfinity`.</span></span>

- <xref:System.Math.CopySign(System.Double,System.Double)>\
<span data-ttu-id="e9711-417">`copySign`IEEE işlemine karşılık gelir, `x` , ancak işaretini döndürür `y` .</span><span class="sxs-lookup"><span data-stu-id="e9711-417">Corresponds to the `copySign` IEEE operation, it returns the value of `x`, but with the sign of `y`.</span></span>

### <a name="net-platform-dependent-intrinsics"></a><span data-ttu-id="e9711-418">.NET platforma bağımlı Iç bilgiler</span><span class="sxs-lookup"><span data-stu-id="e9711-418">.NET Platform-Dependent Intrinsics</span></span>

<span data-ttu-id="e9711-419">**SIMD** veya **bit işleme yönergesi** kümeleri gıbı belirli performans yönelimli CPU yönergelerine erişime izin veren API 'ler eklenmiştir.</span><span class="sxs-lookup"><span data-stu-id="e9711-419">APIs have been added that allow access to certain perf-oriented CPU instructions, such as the **SIMD** or **Bit Manipulation instruction** sets.</span></span> <span data-ttu-id="e9711-420">Bu yönergeler, verileri paralel şekilde işleme gibi belirli senaryolarda önemli performans geliştirmeleri elde etmenize yardımcı olabilir.</span><span class="sxs-lookup"><span data-stu-id="e9711-420">These instructions can help achieve significant performance improvements in certain scenarios, such as processing data efficiently in parallel.</span></span>

<span data-ttu-id="e9711-421">Uygun durumlarda, .NET kitaplıkları performansı artırmak için bu yönergeleri kullanmaya başlamıştır.</span><span class="sxs-lookup"><span data-stu-id="e9711-421">Where appropriate, the .NET libraries have begun using these instructions to improve performance.</span></span>

<span data-ttu-id="e9711-422">Daha fazla bilgi için bkz. [.net platforma bağımlı iç](https://github.com/dotnet/designs/blob/master/accepted/2018/platform-intrinsics.md)bilgiler.</span><span class="sxs-lookup"><span data-stu-id="e9711-422">For more information, see [.NET Platform-Dependent Intrinsics](https://github.com/dotnet/designs/blob/master/accepted/2018/platform-intrinsics.md).</span></span>

### <a name="improved-net-core-version-apis"></a><span data-ttu-id="e9711-423">Geliştirilmiş .NET Core sürümü API 'Leri</span><span class="sxs-lookup"><span data-stu-id="e9711-423">Improved .NET Core Version APIs</span></span>

<span data-ttu-id="e9711-424">.NET Core 3,0 ile başlayarak, .NET Core ile birlikte sunulan sürüm API 'Leri artık istediğiniz bilgileri döndürür.</span><span class="sxs-lookup"><span data-stu-id="e9711-424">Starting with .NET Core 3.0, the version APIs provided with .NET Core now return the information you expect.</span></span> <span data-ttu-id="e9711-425">Örnek:</span><span class="sxs-lookup"><span data-stu-id="e9711-425">For example:</span></span>

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
> <span data-ttu-id="e9711-426">Son değişiklik.</span><span class="sxs-lookup"><span data-stu-id="e9711-426">Breaking change.</span></span> <span data-ttu-id="e9711-427">Bu teknik açıdan önemli bir değişiklik olduğundan, sürüm oluşturma düzeni değişti.</span><span class="sxs-lookup"><span data-stu-id="e9711-427">This is technically a breaking change because the versioning scheme has changed.</span></span>

### <a name="fast-built-in-json-support"></a><span data-ttu-id="e9711-428">Hızlı yerleşik JSON desteği</span><span class="sxs-lookup"><span data-stu-id="e9711-428">Fast built-in JSON support</span></span>

<span data-ttu-id="e9711-429">.NET kullanıcıları büyük ölçüde [Newtonsoft.Js](https://www.newtonsoft.com/json) ve DIĞER popüler JSON kitaplıklarında büyük bir seçenek olmaya devam eder.</span><span class="sxs-lookup"><span data-stu-id="e9711-429">.NET users have largely relied on [Newtonsoft.Json](https://www.newtonsoft.com/json) and other popular JSON libraries, which continue to be good choices.</span></span> <span data-ttu-id="e9711-430">`Newtonsoft.Json` temel veri türü olarak .NET dizelerini kullanır, bu da arada bulunan UTF-16 ' dır.</span><span class="sxs-lookup"><span data-stu-id="e9711-430">`Newtonsoft.Json` uses .NET strings as its base datatype, which is UTF-16 under the hood.</span></span>

<span data-ttu-id="e9711-431">Yeni yerleşik JSON desteği yüksek performanslı, düşük ayırma, UTF-8 kodlu JSON metniyle birlikte çalışıyor.</span><span class="sxs-lookup"><span data-stu-id="e9711-431">The new built-in JSON support is high-performance, low allocation, and works with UTF-8 encoded JSON text.</span></span> <span data-ttu-id="e9711-432">Ad alanı ve türleri hakkında daha fazla bilgi için <xref:System.Text.Json> aşağıdaki makalelere bakın:</span><span class="sxs-lookup"><span data-stu-id="e9711-432">For more information about the <xref:System.Text.Json> namespace and types, see the following articles:</span></span>

* [<span data-ttu-id="e9711-433">.NET 'te JSON serileştirme-genel bakış</span><span class="sxs-lookup"><span data-stu-id="e9711-433">JSON serialization in .NET - overview</span></span>](../../standard/serialization/system-text-json-overview.md)
* <span data-ttu-id="e9711-434">[.Net 'TE JSON serileştirmek ve serisini kaldırma](../../standard/serialization/system-text-json-how-to.md).</span><span class="sxs-lookup"><span data-stu-id="e9711-434">[How to serialize and deserialize JSON in .NET](../../standard/serialization/system-text-json-how-to.md).</span></span>
* [<span data-ttu-id="e9711-435">Newtonsoft.Jsüzerinde System.Text.Jsüzerine geçiş</span><span class="sxs-lookup"><span data-stu-id="e9711-435">How to migrate from Newtonsoft.Json to System.Text.Json</span></span>](../../standard/serialization/system-text-json-migrate-from-newtonsoft-how-to.md)

### <a name="http2-support"></a><span data-ttu-id="e9711-436">HTTP/2 desteği</span><span class="sxs-lookup"><span data-stu-id="e9711-436">HTTP/2 support</span></span>

<span data-ttu-id="e9711-437"><xref:System.Net.Http.HttpClient?displayProperty=nameWithType>Tür http/2 protokolünü destekler.</span><span class="sxs-lookup"><span data-stu-id="e9711-437">The <xref:System.Net.Http.HttpClient?displayProperty=nameWithType> type supports the HTTP/2 protocol.</span></span> <span data-ttu-id="e9711-438">HTTP/2 etkinse HTTP protokol sürümü TLS/ALPN aracılığıyla görüşülür ve sunucunun bunu kullanabilmesi durumunda HTTP/2 kullanılır.</span><span class="sxs-lookup"><span data-stu-id="e9711-438">If HTTP/2 is enabled, the HTTP protocol version is negotiated via TLS/ALPN, and HTTP/2 is used if the server elects to use it.</span></span>

<span data-ttu-id="e9711-439">Varsayılan protokol HTTP/1.1 olarak kalır, ancak HTTP/2 iki farklı şekilde etkinleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="e9711-439">The default protocol remains HTTP/1.1, but HTTP/2 can be enabled in two different ways.</span></span> <span data-ttu-id="e9711-440">İlk olarak http istek iletisini HTTP/2 kullanacak şekilde ayarlayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="e9711-440">First, you can set the HTTP request message to use HTTP/2:</span></span>

[!code-csharp[Http2Request](./snippets/dotnet-core-3-0/csharp/http.cs#Request)]

<span data-ttu-id="e9711-441">İkincisi, <xref:System.Net.Http.HttpClient> Varsayılan olarak http/2 kullan seçeneğini kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="e9711-441">Second, you can change <xref:System.Net.Http.HttpClient> to use HTTP/2 by default:</span></span>

[!code-csharp[Http2Client](./snippets/dotnet-core-3-0/csharp/http.cs#Client)]

<span data-ttu-id="e9711-442">Uygulama geliştirirken birçok kez şifrelenmemiş bağlantı kullanmak istersiniz.</span><span class="sxs-lookup"><span data-stu-id="e9711-442">Many times when you're developing an application, you want to use an unencrypted connection.</span></span> <span data-ttu-id="e9711-443">Hedef uç noktanın HTTP/2 kullanacağınızı biliyorsanız, HTTP/2 için şifrelenmemiş bağlantıları açabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e9711-443">If you know the target endpoint will be using HTTP/2, you can turn on unencrypted connections for HTTP/2.</span></span> <span data-ttu-id="e9711-444">`DOTNET_SYSTEM_NET_HTTP_SOCKETSHTTPHANDLER_HTTP2UNENCRYPTEDSUPPORT`Ortam değişkenini `1` uygulama bağlamında etkinleştirerek veya olarak ayarlayarak bu ayarı açabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="e9711-444">You can turn it on by setting the `DOTNET_SYSTEM_NET_HTTP_SOCKETSHTTPHANDLER_HTTP2UNENCRYPTEDSUPPORT` environment variable to `1` or by enabling it in the app context:</span></span>

[!code-csharp[Http2Context](./snippets/dotnet-core-3-0/csharp/http.cs#AppContext)]

## <a name="next-steps"></a><span data-ttu-id="e9711-445">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="e9711-445">Next steps</span></span>

- [<span data-ttu-id="e9711-446">.NET Core 2,2 ve 3,0 arasındaki son değişiklikleri gözden geçirin.</span><span class="sxs-lookup"><span data-stu-id="e9711-446">Review the breaking changes between .NET Core 2.2 and 3.0.</span></span>](../compatibility/2.2-3.0.md)
- [<span data-ttu-id="e9711-447">Windows Forms uygulamalar için .NET Core 3,0 'deki son değişiklikleri gözden geçirin.</span><span class="sxs-lookup"><span data-stu-id="e9711-447">Review the breaking changes in .NET Core 3.0 for Windows Forms apps.</span></span>](../compatibility/winforms.md#net-core-30)
