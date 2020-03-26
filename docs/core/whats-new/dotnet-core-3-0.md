---
title: ​.NET Core 3.0’daki yenilikler
description: .NET Core 3.0'da bulunan yeni özellikler hakkında bilgi edinin.
dev_langs:
- csharp
author: thraka
ms.author: adegeo
ms.date: 01/27/2020
ms.openlocfilehash: ccb987944af29c170b8d960d7112a13078b67dd1
ms.sourcegitcommit: e48a54ebe62e874500a7043f6ee0b77a744d55b4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/26/2020
ms.locfileid: "80291546"
---
# <a name="whats-new-in-net-core-30"></a><span data-ttu-id="9d76d-103">​.NET Core 3.0’daki yenilikler</span><span class="sxs-lookup"><span data-stu-id="9d76d-103">What's new in .NET Core 3.0</span></span>

<span data-ttu-id="9d76d-104">Bu makalede, .NET Core 3.0'da yeni olan açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="9d76d-104">This article describes what is new in .NET Core 3.0.</span></span> <span data-ttu-id="9d76d-105">En büyük geliştirmelerden biri Windows masaüstü uygulamaları için destektir (yalnızca Windows).</span><span class="sxs-lookup"><span data-stu-id="9d76d-105">One of the biggest enhancements is support for Windows desktop applications (Windows only).</span></span> <span data-ttu-id="9d76d-106">.NET Core 3.0 SDK bileşeni Windows Desktop'ı kullanarak Windows Formlarınızı ve Windows Sunu Vakfı (WPF) uygulamalarınızı taşıabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9d76d-106">By using the .NET Core 3.0 SDK component Windows Desktop, you can port your Windows Forms and Windows Presentation Foundation (WPF) applications.</span></span> <span data-ttu-id="9d76d-107">Açık olmak gerekirse, Windows Masaüstü bileşeni yalnızca desteklenir ve Windows'a dahil edilir.</span><span class="sxs-lookup"><span data-stu-id="9d76d-107">To be clear, the Windows Desktop component is only supported and included on Windows.</span></span> <span data-ttu-id="9d76d-108">Daha fazla bilgi için bu makalenin ilerleyen bölümlerinde [Windows masaüstü](#windows-desktop) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="9d76d-108">For more information, see the [Windows desktop](#windows-desktop) section later in this article.</span></span>

<span data-ttu-id="9d76d-109">.NET Core 3.0 C# 8.0 için destek ekler.</span><span class="sxs-lookup"><span data-stu-id="9d76d-109">.NET Core 3.0 adds support for C# 8.0.</span></span> <span data-ttu-id="9d76d-110">[Visual Studio 2019 sürüm 16.3](https://visualstudio.microsoft.com/vs/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) veya daha yeni, [Mac 8.3](/visualstudio/mac/install-preview) veya daha yeni için Visual Studio veya en son **C# uzantılı** [Visual Studio Code](https://code.visualstudio.com/) kullanmanız önerilir.</span><span class="sxs-lookup"><span data-stu-id="9d76d-110">It's highly recommended that you use [Visual Studio 2019 version 16.3](https://visualstudio.microsoft.com/vs/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) or newer, [Visual Studio for Mac 8.3](/visualstudio/mac/install-preview) or newer, or [Visual Studio Code](https://code.visualstudio.com/) with the latest **C# extension**.</span></span>

<span data-ttu-id="9d76d-111">Şu anda Windows, macOS veya Linux'ta [.NET Core 3.0'ı indirin](https://aka.ms/netcore3download) ve başlayın.</span><span class="sxs-lookup"><span data-stu-id="9d76d-111">[Download and get started with .NET Core 3.0](https://aka.ms/netcore3download) right now on Windows, macOS, or Linux.</span></span>

<span data-ttu-id="9d76d-112">Sürüm hakkında daha fazla bilgi için [.NET Core 3.0 duyurusuna](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-0/)bakın.</span><span class="sxs-lookup"><span data-stu-id="9d76d-112">For more information about the release, see the [.NET Core 3.0 announcement](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-0/).</span></span>

<span data-ttu-id="9d76d-113">.NET Core RC1, Microsoft tarafından üretime hazır kabul edildi ve tam olarak desteklendi.</span><span class="sxs-lookup"><span data-stu-id="9d76d-113">.NET Core RC1 was considered production ready by Microsoft and was fully supported.</span></span> <span data-ttu-id="9d76d-114">Bir önizleme sürümü kullanıyorsanız, sürekli destek için RTM sürümüne geçmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="9d76d-114">If you're using a preview release, you must move to the RTM version for continued support.</span></span>

## <a name="language-improvements-c-80"></a><span data-ttu-id="9d76d-115">Dil geliştirmeleri C# 8.0</span><span class="sxs-lookup"><span data-stu-id="9d76d-115">Language improvements C# 8.0</span></span>

<span data-ttu-id="9d76d-116">C# 8.0 da [nullable başvuru türleri](../../csharp/tutorials/nullable-reference-types.md) özelliği, [async akışları](../../csharp/tutorials/generate-consume-asynchronous-stream.md)ve daha fazla desen içeren bu sürümün [bir](../../csharp/tutorials/pattern-matching.md)parçasıdır.</span><span class="sxs-lookup"><span data-stu-id="9d76d-116">C# 8.0 is also part of this release, which includes the [nullable reference types](../../csharp/tutorials/nullable-reference-types.md) feature, [async streams](../../csharp/tutorials/generate-consume-asynchronous-stream.md), and [more patterns](../../csharp/tutorials/pattern-matching.md).</span></span> <span data-ttu-id="9d76d-117">C# 8.0 özellikleri hakkında daha fazla bilgi için [C# 8.0'daki yeniliklere](../../csharp/whats-new/csharp-8.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="9d76d-117">For more information about C# 8.0 features, see [What's new in C# 8.0](../../csharp/whats-new/csharp-8.md).</span></span>

<span data-ttu-id="9d76d-118">Aşağıda ayrıntılı olarak belirtilen aşağıdaki API özelliklerini desteklemek için dil geliştirmeleri eklendi:</span><span class="sxs-lookup"><span data-stu-id="9d76d-118">Language enhancements were added to support the following API features detailed below:</span></span>

- [<span data-ttu-id="9d76d-119">Aralıklar ve endeksler</span><span class="sxs-lookup"><span data-stu-id="9d76d-119">Ranges and indices</span></span>](#ranges-and-indices)
- [<span data-ttu-id="9d76d-120">Async akışları</span><span class="sxs-lookup"><span data-stu-id="9d76d-120">Async streams</span></span>](#async-streams)

## <a name="net-standard-21"></a><span data-ttu-id="9d76d-121">.NET Standart 2.1</span><span class="sxs-lookup"><span data-stu-id="9d76d-121">.NET Standard 2.1</span></span>

<span data-ttu-id="9d76d-122">.NET Core 3.0 uygular **.NET Standart 2.1**.</span><span class="sxs-lookup"><span data-stu-id="9d76d-122">.NET Core 3.0 implements **.NET Standard 2.1**.</span></span> <span data-ttu-id="9d76d-123">Ancak, varsayılan `dotnet new classlib` şablon hala **.NET Standart 2.0**hedefleyen bir proje oluşturur.</span><span class="sxs-lookup"><span data-stu-id="9d76d-123">However, the default `dotnet new classlib` template generates a project that still targets **.NET Standard 2.0**.</span></span> <span data-ttu-id="9d76d-124">**.NET Standart 2.1'i**hedeflemek için proje `TargetFramework` dosyanızı düzenlemesi ve özelliği `netstandard2.1`ni :</span><span class="sxs-lookup"><span data-stu-id="9d76d-124">To target **.NET Standard 2.1**, edit your project file and change the `TargetFramework` property to `netstandard2.1`:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <TargetFramework>netstandard2.1</TargetFramework>
  </PropertyGroup>

</Project>
```

<span data-ttu-id="9d76d-125">Visual Studio kullanıyorsanız Visual [Studio 2019'a](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019)ihtiyacınız vardır, çünkü Visual Studio 2017 **.NET Standard 2.1** veya **.NET Core 3.0'ı**desteklemez.</span><span class="sxs-lookup"><span data-stu-id="9d76d-125">If you're using Visual Studio, you need [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019), as Visual Studio 2017 doesn't support **.NET Standard 2.1** or **.NET Core 3.0**.</span></span>

## <a name="compiledeploy"></a><span data-ttu-id="9d76d-126">Derle/Dağıt</span><span class="sxs-lookup"><span data-stu-id="9d76d-126">Compile/Deploy</span></span>

### <a name="default-executables"></a><span data-ttu-id="9d76d-127">Varsayılan yürütülebilir</span><span class="sxs-lookup"><span data-stu-id="9d76d-127">Default executables</span></span>

<span data-ttu-id="9d76d-128">.NET Core artık varsayılan olarak [çalışma süresine bağlı yürütülebilir ler](../deploying/index.md#publish-runtime-dependent) oluşturur.</span><span class="sxs-lookup"><span data-stu-id="9d76d-128">.NET Core now builds [runtime-dependent executables](../deploying/index.md#publish-runtime-dependent) by default.</span></span> <span data-ttu-id="9d76d-129">Bu davranış, .NET Core'un genel olarak yüklenmiş sürümünü kullanan uygulamalar için yenidir.</span><span class="sxs-lookup"><span data-stu-id="9d76d-129">This behavior is new for applications that use a globally installed version of .NET Core.</span></span> <span data-ttu-id="9d76d-130">Önceden, yalnızca [bağımsız dağıtımlar](../deploying/index.md#publish-self-contained) yürütülebilir bir üretebilme yi doğurabilir.</span><span class="sxs-lookup"><span data-stu-id="9d76d-130">Previously, only [self-contained deployments](../deploying/index.md#publish-self-contained) would produce an executable.</span></span>

<span data-ttu-id="9d76d-131">Sırasında `dotnet build` `dotnet publish`veya, bir yürütülebilir **(appHost**olarak da bilinir) kullandığınız SDK ortamı ve platformu eşleşen oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="9d76d-131">During `dotnet build` or `dotnet publish`, an executable (known as the **appHost**) is created that matches the environment and platform of the SDK you're using.</span></span> <span data-ttu-id="9d76d-132">Bu yürütülebilir kişilerle, aşağıdakiler gibi diğer yerel yürütülebilir kişilerle aynı şeyleri bekleyebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="9d76d-132">You can expect the same things with these executables as you would other native executables, such as:</span></span>

- <span data-ttu-id="9d76d-133">Çalıştırılabilir'e çift tıklayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9d76d-133">You can double-click on the executable.</span></span>
- <span data-ttu-id="9d76d-134">Uygulamayı doğrudan Windows ve Linux ve `myapp.exe` `./myapp` macOS'ta olduğu gibi bir komut isteminden başlatabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9d76d-134">You can launch the application from a command prompt directly, such as `myapp.exe` on Windows, and `./myapp` on Linux and macOS.</span></span>

### <a name="macos-apphost-and-notarization"></a><span data-ttu-id="9d76d-135">macOS appHost ve noterizasyon</span><span class="sxs-lookup"><span data-stu-id="9d76d-135">macOS appHost and notarization</span></span>

<span data-ttu-id="9d76d-136">*yalnızca macOS*</span><span class="sxs-lookup"><span data-stu-id="9d76d-136">*macOS only*</span></span>

<span data-ttu-id="9d76d-137">macOS için noterize .NET Core SDK 3.0 ile başlayarak, varsayılan yürütülebilir (appHost olarak da bilinir) üretmek için ayar varsayılan olarak devre dışı bırakılır.</span><span class="sxs-lookup"><span data-stu-id="9d76d-137">Starting with the notarized .NET Core SDK 3.0 for macOS, the setting to produce a default executable (known as the appHost) is disabled by default.</span></span> <span data-ttu-id="9d76d-138">Daha fazla bilgi için [macOS Catalina Notarization ve .NET Core indirme ve projeleri üzerindeki etkisine](../install/macos-notarization-issues.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="9d76d-138">For more information, see [macOS Catalina Notarization and the impact on .NET Core downloads and projects](../install/macos-notarization-issues.md).</span></span>

<span data-ttu-id="9d76d-139">appHost ayarı etkinleştirildiğinde, .NET Core, oluşturduğunuzda veya yayımladığınızda yerel bir Mach-O çalıştırılabilir oluşturur.</span><span class="sxs-lookup"><span data-stu-id="9d76d-139">When the appHost setting is enabled, .NET Core generates a native Mach-O executable when you build or publish.</span></span> <span data-ttu-id="9d76d-140">`dotnet run` Uygulamanız, komutla kaynak kodundan çalıştırıldığında veya doğrudan Yürütülebilir Mach-O'yu başlatarak appHost bağlamında çalışır.</span><span class="sxs-lookup"><span data-stu-id="9d76d-140">Your app runs in the context of the appHost when it is run from source code with the `dotnet run` command, or by starting the Mach-O executable directly.</span></span>

<span data-ttu-id="9d76d-141">appHost olmadan, bir kullanıcının çalışma [süresine bağlı](../deploying/index.md#publish-runtime-dependent) bir uygulamayı `dotnet <filename.dll>` başlatmasının tek yolu komuttur.</span><span class="sxs-lookup"><span data-stu-id="9d76d-141">Without the appHost, the only way a user can start a [runtime-dependent](../deploying/index.md#publish-runtime-dependent) app is with the `dotnet <filename.dll>` command.</span></span> <span data-ttu-id="9d76d-142">Uygulamanızı [bağımsız](../deploying/index.md#publish-self-contained)olarak yayımladığınızda her zaman bir appHost oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="9d76d-142">An appHost is always created when you publish your app [self-contained](../deploying/index.md#publish-self-contained).</span></span>

<span data-ttu-id="9d76d-143">Ya proje düzeyinde appHost yapılandırabilirsiniz, ya da `dotnet` `-p:UseAppHost` parametre ile belirli bir komut için appHost geçiş:</span><span class="sxs-lookup"><span data-stu-id="9d76d-143">You can either configure the appHost at the project level, or toggle the appHost for a specific `dotnet` command with the `-p:UseAppHost` parameter:</span></span>

- <span data-ttu-id="9d76d-144">Proje dosyası</span><span class="sxs-lookup"><span data-stu-id="9d76d-144">Project file</span></span>

  ```xml
  <PropertyGroup>
    <UseAppHost>true</UseAppHost>
  </PropertyGroup>
  ```

- <span data-ttu-id="9d76d-145">Komut satırı parametresi</span><span class="sxs-lookup"><span data-stu-id="9d76d-145">Command-line parameter</span></span>

  ```dotnetcli
  dotnet run -p:UseAppHost=true
  ```

<span data-ttu-id="9d76d-146">`UseAppHost` Ayar hakkında daha fazla bilgi için [Microsoft.NET.Sdk için MSBuild özelliklerine](../project-sdk/msbuild-props.md#useapphost)bakın.</span><span class="sxs-lookup"><span data-stu-id="9d76d-146">For more information about the `UseAppHost` setting, see [MSBuild properties for Microsoft.NET.Sdk](../project-sdk/msbuild-props.md#useapphost).</span></span>

### <a name="single-file-executables"></a><span data-ttu-id="9d76d-147">Tek dosyalı yürütülebilir</span><span class="sxs-lookup"><span data-stu-id="9d76d-147">Single-file executables</span></span>

<span data-ttu-id="9d76d-148">Komut, `dotnet publish` uygulamanızı platforma özgü tek dosyalı yürütülebilir bir şekilde paketlemenizi destekler.</span><span class="sxs-lookup"><span data-stu-id="9d76d-148">The `dotnet publish` command supports packaging your app into a platform-specific single-file executable.</span></span> <span data-ttu-id="9d76d-149">Yürütülebilir kendi kendini ayıklama ve uygulamanızı çalıştırmak için gerekli olan tüm bağımlılıkları (yerel dahil) içerir.</span><span class="sxs-lookup"><span data-stu-id="9d76d-149">The executable is self-extracting and contains all dependencies (including native) that are required to run your app.</span></span> <span data-ttu-id="9d76d-150">Uygulama ilk çalıştırıldığında, uygulama uygulama adına ve yapı tanımlayıcısına göre bir dizine ayıklanır.</span><span class="sxs-lookup"><span data-stu-id="9d76d-150">When the app is first run, the application is extracted to a directory based on the app name and build identifier.</span></span> <span data-ttu-id="9d76d-151">Uygulama yeniden çalıştırıldığında başlatma daha hızlıdır.</span><span class="sxs-lookup"><span data-stu-id="9d76d-151">Startup is faster when the application is run again.</span></span> <span data-ttu-id="9d76d-152">Yeni bir sürüm kullanılmadığı sürece uygulamanın kendisini ikinci kez ayıklaması gerekmez.</span><span class="sxs-lookup"><span data-stu-id="9d76d-152">The application doesn't need to extract itself a second time unless a new version was used.</span></span>

<span data-ttu-id="9d76d-153">Tek dosyalı yürütülebilir yayımlamak `PublishSingleFile` için, projenizdeki veya komut `dotnet publish` satırında komut satırında komut satırında komut u belirleyin:</span><span class="sxs-lookup"><span data-stu-id="9d76d-153">To publish a single-file executable, set the `PublishSingleFile` in your project or on the command line with the `dotnet publish` command:</span></span>

```xml
<PropertyGroup>
  <RuntimeIdentifier>win10-x64</RuntimeIdentifier>
  <PublishSingleFile>true</PublishSingleFile>
</PropertyGroup>
```

<span data-ttu-id="9d76d-154">-veya-</span><span class="sxs-lookup"><span data-stu-id="9d76d-154">-or-</span></span>

```dotnetcli
dotnet publish -r win10-x64 -p:PublishSingleFile=true
```

<span data-ttu-id="9d76d-155">Tek dosyalı yayımlama hakkında daha fazla bilgi için [tek dosyalı paketleyici tasarım belgesine](https://github.com/dotnet/designs/blob/master/accepted/2020/single-file/design_3_0.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="9d76d-155">For more information about single-file publishing, see the [single-file bundler design document](https://github.com/dotnet/designs/blob/master/accepted/2020/single-file/design_3_0.md).</span></span>

### <a name="assembly-linking"></a><span data-ttu-id="9d76d-156">Montaj bağlama</span><span class="sxs-lookup"><span data-stu-id="9d76d-156">Assembly linking</span></span>

<span data-ttu-id="9d76d-157">.NET core 3.0 SDK, IL'yi analiz ederek ve kullanılmayan derlemeleri kırparak uygulamaların boyutunu küçültebilen bir araçla birlikte gelir.</span><span class="sxs-lookup"><span data-stu-id="9d76d-157">The .NET core 3.0 SDK comes with a tool that can reduce the size of apps by analyzing IL and trimming unused assemblies.</span></span>

<span data-ttu-id="9d76d-158">Bağımsız uygulamalar, .NET'in ana bilgisayara yüklenmesini gerektirmeden kodunuzu çalıştırmak için gereken her şeyi içerir.</span><span class="sxs-lookup"><span data-stu-id="9d76d-158">Self-contained apps include everything needed to run your code, without requiring .NET to be installed on the host computer.</span></span> <span data-ttu-id="9d76d-159">Ancak, çoğu zaman uygulama yalnızca işlev için çerçevenin küçük bir alt kümesi gerektirir ve diğer kullanılmayan kitaplıklar kaldırılabilir.</span><span class="sxs-lookup"><span data-stu-id="9d76d-159">However, many times the app only requires a small subset of the framework to function, and other unused libraries could be removed.</span></span>

<span data-ttu-id="9d76d-160">.NET Core artık uygulamanızın IL'sini tmak için [IL bağlayıcı](https://github.com/mono/linker) aracını kullanacak bir ayar içerir.</span><span class="sxs-lookup"><span data-stu-id="9d76d-160">.NET Core now includes a setting that will use the [IL linker](https://github.com/mono/linker) tool to scan the IL of your app.</span></span> <span data-ttu-id="9d76d-161">Bu araç hangi kodun gerekli olduğunu algılar ve kullanılmayan kitaplıkları kırpar.</span><span class="sxs-lookup"><span data-stu-id="9d76d-161">This tool detects what code is required, and then trims unused libraries.</span></span> <span data-ttu-id="9d76d-162">Bu araç, bazı uygulamaların dağıtım boyutunu önemli ölçüde azaltabilir.</span><span class="sxs-lookup"><span data-stu-id="9d76d-162">This tool can significantly reduce the deployment size of some apps.</span></span>

<span data-ttu-id="9d76d-163">Bu aracı etkinleştirmek `<PublishTrimmed>` için projenize ayarı ekleyin ve bağımsız bir uygulama yayımlayın:</span><span class="sxs-lookup"><span data-stu-id="9d76d-163">To enable this tool, add the `<PublishTrimmed>` setting in your project and publish a self-contained app:</span></span>

```xml
<PropertyGroup>
  <PublishTrimmed>true</PublishTrimmed>
</PropertyGroup>
```

```dotnetcli
dotnet publish -r <rid> -c Release
```

<span data-ttu-id="9d76d-164">Örnek olarak, yayınlandığında, yaklaşık 70 MB boyutuna isabet eden temel "merhaba dünya" yeni konsol proje şablonu.</span><span class="sxs-lookup"><span data-stu-id="9d76d-164">As an example, the basic "hello world" new console project template that is included, when published, hits about 70 MB in size.</span></span> <span data-ttu-id="9d76d-165">Kullanılarak, `<PublishTrimmed>`bu boyut yaklaşık 30 MB azalır.</span><span class="sxs-lookup"><span data-stu-id="9d76d-165">By using `<PublishTrimmed>`, that size is reduced to about 30 MB.</span></span>

<span data-ttu-id="9d76d-166">Yansıma veya ilgili dinamik özellikleri kullanan uygulamaların veya çerçevelerin (ASP.NET Core ve WPF dahil) genellikle kırıldığında kırılacak larını göz önünde bulundurmanız önemlidir.</span><span class="sxs-lookup"><span data-stu-id="9d76d-166">It's important to consider that applications or frameworks (including ASP.NET Core and WPF) that use reflection or related dynamic features, will often break when trimmed.</span></span> <span data-ttu-id="9d76d-167">Bağlayıcının bu dinamik davranışı bilmediği ve yansıma için hangi çerçeve türlerinin gerekli olduğunu belirleyemediği için bu kırılma oluşur.</span><span class="sxs-lookup"><span data-stu-id="9d76d-167">This breakage occurs because the linker doesn't know about this dynamic behavior and can't determine which framework types are required for reflection.</span></span> <span data-ttu-id="9d76d-168">IL Bağlayıcı aracı bu senaryonun farkında olacak şekilde yapılandırılabilir.</span><span class="sxs-lookup"><span data-stu-id="9d76d-168">The IL Linker tool can be configured to be aware of this scenario.</span></span>

<span data-ttu-id="9d76d-169">Her şeyden önce, kırpma sonra uygulamatest emin olun.</span><span class="sxs-lookup"><span data-stu-id="9d76d-169">Above all else, be sure to test your app after trimming.</span></span>

<span data-ttu-id="9d76d-170">IL Bağlayıcı aracı hakkında daha fazla bilgi için [belgelere](https://aka.ms/dotnet-illink) bakın veya [mono/linker]( https://github.com/mono/linker) repo'yu ziyaret edin.</span><span class="sxs-lookup"><span data-stu-id="9d76d-170">For more information about the IL Linker tool, see the [documentation](https://aka.ms/dotnet-illink) or visit the [mono/linker]( https://github.com/mono/linker) repo.</span></span>

### <a name="tiered-compilation"></a><span data-ttu-id="9d76d-171">Katmanlı derleme</span><span class="sxs-lookup"><span data-stu-id="9d76d-171">Tiered compilation</span></span>

<span data-ttu-id="9d76d-172">[Katmanlı derleme](https://github.com/dotnet/runtime/blob/master/docs/design/features/tiered-compilation-guide.md) (TC) varsayılan olarak .NET Core 3.0 ile açıktır.</span><span class="sxs-lookup"><span data-stu-id="9d76d-172">[Tiered compilation](https://github.com/dotnet/runtime/blob/master/docs/design/features/tiered-compilation-guide.md) (TC) is on by default with .NET Core 3.0.</span></span> <span data-ttu-id="9d76d-173">Bu özellik, daha iyi performans elde etmek için çalışma süresinin tam zamanında (JIT) derleyiciyi daha uyumlu bir şekilde kullanmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="9d76d-173">This feature enables the runtime to more adaptively use the just-in-time (JIT) compiler to achieve better performance.</span></span>

<span data-ttu-id="9d76d-174">Katmanlı derlemenin temel avantajı, daha düşük kaliteli ama daha hızlı bir katmanda veya daha yüksek kalitede ama daha yavaş bir katmanda iki farklı jitting yöntemi sağlamaktır.</span><span class="sxs-lookup"><span data-stu-id="9d76d-174">The main benefit of tiered compilation is to provide two ways of jitting methods: in a lower-quality-but-faster tier or a higher-quality-but-slower tier.</span></span> <span data-ttu-id="9d76d-175">Kalite, yöntemin ne kadar iyi optimize edildiklerine işaret eder.</span><span class="sxs-lookup"><span data-stu-id="9d76d-175">The quality refers to how well the method is optimized.</span></span> <span data-ttu-id="9d76d-176">TC, başlangıçtan sabit duruma kadar yürütmenin çeşitli aşamalarından geçerken bir uygulamanın performansını artırmaya yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="9d76d-176">TC helps to improve the performance of an application as it goes through various stages of execution, from startup through steady state.</span></span> <span data-ttu-id="9d76d-177">Katmanlı derleme devre dışı bırakıldığında, her yöntem başlangıç performansına göre sabit durum performansına bağlı tek bir şekilde derlenir.</span><span class="sxs-lookup"><span data-stu-id="9d76d-177">When tiered compilation is disabled, every method is compiled in a single way that's biased to steady-state performance over startup performance.</span></span>

<span data-ttu-id="9d76d-178">TC etkinleştirildiğinde, bir uygulama başlatıldığında yöntem derlemesi için aşağıdaki davranış uygulanır:</span><span class="sxs-lookup"><span data-stu-id="9d76d-178">When TC is enabled, the following behavior applies for method compilation when an app starts up:</span></span>

- <span data-ttu-id="9d76d-179">Yöntemde zaman önceden derlenmiş kod veya [ReadyToRun](#readytorun-images)varsa, önceden oluşturulmuş kod kullanılır.</span><span class="sxs-lookup"><span data-stu-id="9d76d-179">If the method has ahead-of-time-compiled code, or [ReadyToRun](#readytorun-images), the pregenerated code is used.</span></span>
- <span data-ttu-id="9d76d-180">Aksi takdirde, yöntem jitted.</span><span class="sxs-lookup"><span data-stu-id="9d76d-180">Otherwise, the method is jitted.</span></span> <span data-ttu-id="9d76d-181">Genellikle, bu yöntemler değer türleri üzerinde genel vardır.</span><span class="sxs-lookup"><span data-stu-id="9d76d-181">Typically, these methods are generics over value types.</span></span>
  - <span data-ttu-id="9d76d-182">*Hızlı JIT* daha hızlı düşük kaliteli (veya daha az optimize edilmiş) kod üretir.</span><span class="sxs-lookup"><span data-stu-id="9d76d-182">*Quick JIT* produces lower-quality (or less optimized) code more quickly.</span></span> <span data-ttu-id="9d76d-183">.NET Core 3.0'da, Quick JIT döngü içermeyen yöntemler için varsayılan olarak etkinleştirilir ve başlangıç sırasında tercih edilir.</span><span class="sxs-lookup"><span data-stu-id="9d76d-183">In .NET Core 3.0, Quick JIT is enabled by default for methods that don't contain loops and is preferred during startup.</span></span>
  - <span data-ttu-id="9d76d-184">Tam olarak optimize edilen JIT daha yüksek kaliteli (veya daha iyi optimize edilmiş) kod üretir.</span><span class="sxs-lookup"><span data-stu-id="9d76d-184">The fully optimizing JIT produces higher-quality (or more optimized) code more slowly.</span></span> <span data-ttu-id="9d76d-185">Hızlı JIT'nin kullanılmayacağı yöntemler için (örneğin, yöntem <xref:System.Runtime.CompilerServices.MethodImplOptions.AggressiveOptimization?displayProperty=nameWithType>atfedilirse), tam olarak optimize edilen JIT kullanılır.</span><span class="sxs-lookup"><span data-stu-id="9d76d-185">For methods where Quick JIT would not be used (for example, if the method is attributed with <xref:System.Runtime.CompilerServices.MethodImplOptions.AggressiveOptimization?displayProperty=nameWithType>), the fully optimizing JIT is used.</span></span>

<span data-ttu-id="9d76d-186">Sık çağrılan yöntemler için, tam zamanında derleyici sonunda arka planda tam olarak optimize edilmiş kod oluşturur.</span><span class="sxs-lookup"><span data-stu-id="9d76d-186">For frequently called methods, the just-in-time compiler eventually creates fully optimized code in the background.</span></span> <span data-ttu-id="9d76d-187">Daha sonra en iyi duruma getirilmiş kod, bu yöntem için önceden derlenmiş kodun yerini alır.</span><span class="sxs-lookup"><span data-stu-id="9d76d-187">The optimized code then replaces the pre-compiled code for that method.</span></span>

<span data-ttu-id="9d76d-188">Hızlı JIT tarafından oluşturulan kod daha yavaş çalışabilir, daha fazla bellek tahsis edebilir veya daha fazla yığın alanı kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="9d76d-188">Code generated by Quick JIT may run slower, allocate more memory, or use more stack space.</span></span> <span data-ttu-id="9d76d-189">Sorunlar varsa, proje dosyasındaki bu MSBuild özelliğini kullanarak Hızlı JIT'yi devre dışı kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="9d76d-189">If there are issues, you can disabled Quick JIT using this MSBuild property in the project file:</span></span>

```xml
<PropertyGroup>
  <TieredCompilationQuickJit>false</TieredCompilationQuickJit>
</PropertyGroup>
```

<span data-ttu-id="9d76d-190">TC'yi tamamen devre dışı kullanabilirsiniz, proje dosyanızdaki bu MSBuild özelliğini kullanın:</span><span class="sxs-lookup"><span data-stu-id="9d76d-190">To disable TC completely, use this MSBuild property in your project file:</span></span>

```xml
<PropertyGroup>
  <TieredCompilation>false</TieredCompilation>
</PropertyGroup>
```

> [!TIP]
> <span data-ttu-id="9d76d-191">Proje dosyasındaki bu ayarları değiştirirseniz, yeni ayarların yansıtılması için temiz bir yapı `obj` gerçekleştirmeniz gerekebilir (ve `bin` dizinleri silin ve yeniden oluşturun).</span><span class="sxs-lookup"><span data-stu-id="9d76d-191">If you change these settings in the project file, you may need to perform a clean build for the new settings to be reflected (delete the `obj` and `bin` directories and rebuild).</span></span>

<span data-ttu-id="9d76d-192">Derlemeyi çalışma zamanında yapılandırma hakkında daha fazla bilgi [için derleme için Çalışma zamanı yapılandırma seçeneklerine](../run-time-config/compilation.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="9d76d-192">For more information about configuring compilation at run time, see [Run-time configuration options for compilation](../run-time-config/compilation.md).</span></span>

### <a name="readytorun-images"></a><span data-ttu-id="9d76d-193">ReadyToRun görüntüleri</span><span class="sxs-lookup"><span data-stu-id="9d76d-193">ReadyToRun images</span></span>

<span data-ttu-id="9d76d-194">.NET Core uygulamanızın başlangıç süresini ReadyToRun (R2R) formatında uygulama derlemelerinizi derleyerek geliştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9d76d-194">You can improve the startup time of your .NET Core application by compiling your application assemblies as ReadyToRun (R2R) format.</span></span> <span data-ttu-id="9d76d-195">R2R, ileri zaman (AOT) derlemesinin bir şeklidir.</span><span class="sxs-lookup"><span data-stu-id="9d76d-195">R2R is a form of ahead-of-time (AOT) compilation.</span></span>

<span data-ttu-id="9d76d-196">R2R ikilileri, uygulamanız yüklerken tam zamanında (JIT) derleyicisinin yapması gereken iş miktarını azaltarak başlangıç performansını artırır.</span><span class="sxs-lookup"><span data-stu-id="9d76d-196">R2R binaries improve startup performance by reducing the amount of work the just-in-time (JIT) compiler needs to do as your application loads.</span></span> <span data-ttu-id="9d76d-197">İkili, JIT'nin üreteceği kodla karşılaştırıldığında benzer yerel kodlar içerir.</span><span class="sxs-lookup"><span data-stu-id="9d76d-197">The binaries contain similar native code compared to what the JIT would produce.</span></span> <span data-ttu-id="9d76d-198">Ancak, R2R ikilileri, bazı senaryolar için hala gerekli olan ara dil (IL) kodu ve aynı kodun yerel sürümünü içerdiğinden daha büyüktür.</span><span class="sxs-lookup"><span data-stu-id="9d76d-198">However, R2R binaries are larger because they contain both intermediate language (IL) code, which is still needed for some scenarios, and the native version of the same code.</span></span> <span data-ttu-id="9d76d-199">R2R yalnızca Linux x64 veya Windows x64 gibi belirli çalışma zamanı ortamlarını (RID) hedefleyen bağımsız bir uygulama yayımladığınızda kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="9d76d-199">R2R is only available when you publish a self-contained app that targets specific runtime environments (RID) such as Linux x64 or Windows x64.</span></span>

<span data-ttu-id="9d76d-200">Projenizi ReadyToRun olarak derlemek için aşağıdakileri yapın:</span><span class="sxs-lookup"><span data-stu-id="9d76d-200">To compile your project as ReadyToRun, do the following:</span></span>

01. <span data-ttu-id="9d76d-201">Projenize `<PublishReadyToRun>` ayarı ekleyin:</span><span class="sxs-lookup"><span data-stu-id="9d76d-201">Add the `<PublishReadyToRun>` setting to your project:</span></span>

    ```xml
    <PropertyGroup>
      <PublishReadyToRun>true</PublishReadyToRun>
    </PropertyGroup>
    ```

01. <span data-ttu-id="9d76d-202">Bağımsız bir uygulama yayımlayın.</span><span class="sxs-lookup"><span data-stu-id="9d76d-202">Publish a self-contained app.</span></span> <span data-ttu-id="9d76d-203">Örneğin, bu komut Windows'un 64 bit sürümü için bağımsız bir uygulama oluşturur:</span><span class="sxs-lookup"><span data-stu-id="9d76d-203">For example, this command creates a self-contained app for the 64-bit version of Windows:</span></span>

    ```dotnetcli
    dotnet publish -c Release -r win-x64 --self-contained
    ```

#### <a name="cross-platformarchitecture-restrictions"></a><span data-ttu-id="9d76d-204">Çapraz platform/mimari kısıtlamaları</span><span class="sxs-lookup"><span data-stu-id="9d76d-204">Cross platform/architecture restrictions</span></span>

<span data-ttu-id="9d76d-205">ReadyToRun derleyicisi şu anda çapraz hedeflemeyi desteklemiyor.</span><span class="sxs-lookup"><span data-stu-id="9d76d-205">The ReadyToRun compiler doesn't currently support cross-targeting.</span></span> <span data-ttu-id="9d76d-206">Belirli bir hedef üzerinde derlemek gerekir.</span><span class="sxs-lookup"><span data-stu-id="9d76d-206">You must compile on a given target.</span></span> <span data-ttu-id="9d76d-207">Örneğin, Windows x64 için R2R görüntüleri istiyorsanız, bu ortamda yayımlama komutunu çalıştırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="9d76d-207">For example, if you want R2R images for Windows x64, you need to run the publish command on that environment.</span></span>

<span data-ttu-id="9d76d-208">Çapraz hedefleme için özel durumlar:</span><span class="sxs-lookup"><span data-stu-id="9d76d-208">Exceptions to cross-targeting:</span></span>

- <span data-ttu-id="9d76d-209">Windows x64, Windows ARM32, ARM64 ve x86 görüntülerini derlemek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="9d76d-209">Windows x64 can be used to compile Windows ARM32, ARM64, and x86 images.</span></span>
- <span data-ttu-id="9d76d-210">Windows x86, Windows ARM32 görüntülerini derlemek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="9d76d-210">Windows x86 can be used to compile Windows ARM32 images.</span></span>
- <span data-ttu-id="9d76d-211">Linux x64, Linux ARM32 ve ARM64 görüntülerini derlemek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="9d76d-211">Linux x64 can be used to compile Linux ARM32 and ARM64 images.</span></span>

## <a name="runtimesdk"></a><span data-ttu-id="9d76d-212">Çalışma Süresi/SDK</span><span class="sxs-lookup"><span data-stu-id="9d76d-212">Runtime/SDK</span></span>

### <a name="major-version-runtime-roll-forward"></a><span data-ttu-id="9d76d-213">Ana sürüm runtime roll forward</span><span class="sxs-lookup"><span data-stu-id="9d76d-213">Major-version runtime roll forward</span></span>

<span data-ttu-id="9d76d-214">.NET Core 3.0, uygulamanızın .NET Core'un en son ana sürümüne ilerlemesini sağlayan bir tercih özelliği sunar.</span><span class="sxs-lookup"><span data-stu-id="9d76d-214">.NET Core 3.0 introduces an opt-in feature that allows your app to roll forward to the latest major version of .NET Core.</span></span> <span data-ttu-id="9d76d-215">Ayrıca, uygulamanıza nasıl ileri sarma uygulandığını denetlemek için yeni bir ayar eklendi.</span><span class="sxs-lookup"><span data-stu-id="9d76d-215">Additionally, a new setting has been added to control how roll forward is applied to your app.</span></span> <span data-ttu-id="9d76d-216">Bu, aşağıdaki şekillerde yapılandırılabilir:</span><span class="sxs-lookup"><span data-stu-id="9d76d-216">This can be configured in the following ways:</span></span>

- <span data-ttu-id="9d76d-217">Proje dosyası özelliği:`RollForward`</span><span class="sxs-lookup"><span data-stu-id="9d76d-217">Project file property: `RollForward`</span></span>
- <span data-ttu-id="9d76d-218">Çalışma zamanı yapılandırma dosyası özelliği:`rollForward`</span><span class="sxs-lookup"><span data-stu-id="9d76d-218">Run-time configuration file property: `rollForward`</span></span>
- <span data-ttu-id="9d76d-219">Ortam değişkeni:`DOTNET_ROLL_FORWARD`</span><span class="sxs-lookup"><span data-stu-id="9d76d-219">Environment variable: `DOTNET_ROLL_FORWARD`</span></span>
- <span data-ttu-id="9d76d-220">Komut satırı bağımsız değişkeni:`--roll-forward`</span><span class="sxs-lookup"><span data-stu-id="9d76d-220">Command-line argument: `--roll-forward`</span></span>

<span data-ttu-id="9d76d-221">Aşağıdaki değerlerden biri belirtilmelidir.</span><span class="sxs-lookup"><span data-stu-id="9d76d-221">One of the following values must be specified.</span></span> <span data-ttu-id="9d76d-222">Ayar atlanırsa, **Küçük** varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="9d76d-222">If the setting is omitted, **Minor** is the default.</span></span>

- <span data-ttu-id="9d76d-223">**En Son Yama**</span><span class="sxs-lookup"><span data-stu-id="9d76d-223">**LatestPatch**</span></span>\
<span data-ttu-id="9d76d-224">En yüksek yama sürümüne doğru yuvarlan.</span><span class="sxs-lookup"><span data-stu-id="9d76d-224">Roll forward to the highest patch version.</span></span> <span data-ttu-id="9d76d-225">Bu, küçük sürümün devrilmelerini devre dışı kılabilir.</span><span class="sxs-lookup"><span data-stu-id="9d76d-225">This disables minor version roll forward.</span></span>
- <span data-ttu-id="9d76d-226">**Küçük**</span><span class="sxs-lookup"><span data-stu-id="9d76d-226">**Minor**</span></span>\
<span data-ttu-id="9d76d-227">İstenen küçük sürüm eksikse, en düşük yüksek küçük sürüme ilerleyin.</span><span class="sxs-lookup"><span data-stu-id="9d76d-227">Roll forward to the lowest higher minor version, if requested minor version is missing.</span></span> <span data-ttu-id="9d76d-228">İstenen küçük sürüm varsa, **En Son Yama** ilkesi kullanılır.</span><span class="sxs-lookup"><span data-stu-id="9d76d-228">If the requested minor version is present, then the **LatestPatch** policy is used.</span></span>
- <span data-ttu-id="9d76d-229">**Büyük**</span><span class="sxs-lookup"><span data-stu-id="9d76d-229">**Major**</span></span>\
<span data-ttu-id="9d76d-230">İstenen ana sürüm eksikse, en düşük yüksek ana sürüme ve en düşük küçük sürüme ilerleyin.</span><span class="sxs-lookup"><span data-stu-id="9d76d-230">Roll forward to lowest higher major version, and lowest minor version, if requested major version is missing.</span></span> <span data-ttu-id="9d76d-231">İstenen ana sürüm varsa, **Küçük** ilke kullanılır.</span><span class="sxs-lookup"><span data-stu-id="9d76d-231">If the requested major version is present, then the **Minor** policy is used.</span></span>
- <span data-ttu-id="9d76d-232">**Son Küçük**</span><span class="sxs-lookup"><span data-stu-id="9d76d-232">**LatestMinor**</span></span>\
<span data-ttu-id="9d76d-233">İstenen küçük sürüm mevcut olsa bile, en yüksek küçük sürüme ilerleyin.</span><span class="sxs-lookup"><span data-stu-id="9d76d-233">Roll forward to highest minor version, even if requested minor version is present.</span></span> <span data-ttu-id="9d76d-234">Bileşen barındırma senaryoları için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="9d76d-234">Intended for component hosting scenarios.</span></span>
- <span data-ttu-id="9d76d-235">**Son Major**</span><span class="sxs-lookup"><span data-stu-id="9d76d-235">**LatestMajor**</span></span>\
<span data-ttu-id="9d76d-236">İstenen büyük sürüm mevcut olsa bile, en yüksek majör ve en yüksek minör sürüme ilerleyin.</span><span class="sxs-lookup"><span data-stu-id="9d76d-236">Roll forward to highest major and highest minor version, even if requested major is present.</span></span> <span data-ttu-id="9d76d-237">Bileşen barındırma senaryoları için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="9d76d-237">Intended for component hosting scenarios.</span></span>
- <span data-ttu-id="9d76d-238">**Devre dışı bırakmak**</span><span class="sxs-lookup"><span data-stu-id="9d76d-238">**Disable**</span></span>\
<span data-ttu-id="9d76d-239">Öne doğru yuvarlanma.</span><span class="sxs-lookup"><span data-stu-id="9d76d-239">Don't roll forward.</span></span> <span data-ttu-id="9d76d-240">Yalnızca belirtilen sürüme bağla.</span><span class="sxs-lookup"><span data-stu-id="9d76d-240">Only bind to specified version.</span></span> <span data-ttu-id="9d76d-241">Bu ilke, en son düzeltme ekilerine ilerleme yitirme özelliğini devre dışı kattığı için genel kullanım için önerilmez.</span><span class="sxs-lookup"><span data-stu-id="9d76d-241">This policy isn't recommended for general use because it disables the ability to roll forward to the latest patches.</span></span> <span data-ttu-id="9d76d-242">Bu değer yalnızca sınama için önerilir.</span><span class="sxs-lookup"><span data-stu-id="9d76d-242">This value is only recommended for testing.</span></span>

<span data-ttu-id="9d76d-243">Devre **Dışı Atanın** yanı sıra, tüm ayarlar kullanılabilir en yüksek yama sürümünü kullanır.</span><span class="sxs-lookup"><span data-stu-id="9d76d-243">Besides the **Disable** setting, all settings will use the highest available patch version.</span></span>

### <a name="build-copies-dependencies"></a><span data-ttu-id="9d76d-244">Kopya bağımlılıkları oluşturma</span><span class="sxs-lookup"><span data-stu-id="9d76d-244">Build copies dependencies</span></span>

<span data-ttu-id="9d76d-245">Komut `dotnet build` artık NuGet önbelleğinden yapı çıktıklasörüne uygulamanız için NuGet bağımlılıklarını kopyalar.</span><span class="sxs-lookup"><span data-stu-id="9d76d-245">The `dotnet build` command now copies NuGet dependencies for your application from the NuGet cache to the build output folder.</span></span> <span data-ttu-id="9d76d-246">Daha önce, bağımlılıklar yalnızca `dotnet publish`bir parçası olarak kopyalandı.</span><span class="sxs-lookup"><span data-stu-id="9d76d-246">Previously, dependencies were only copied as part of `dotnet publish`.</span></span>

<span data-ttu-id="9d76d-247">Bağlantı ve jilet sayfası yayımlama gibi hala yayımlama gerektiren bazı işlemler vardır.</span><span class="sxs-lookup"><span data-stu-id="9d76d-247">There are some operations, like linking and razor page publishing that will still require publishing.</span></span>

### <a name="local-tools"></a><span data-ttu-id="9d76d-248">Yerel araçlar</span><span class="sxs-lookup"><span data-stu-id="9d76d-248">Local tools</span></span>

<span data-ttu-id="9d76d-249">.NET Core 3.0 yerel araçları tanıttı.</span><span class="sxs-lookup"><span data-stu-id="9d76d-249">.NET Core 3.0 introduces local tools.</span></span> <span data-ttu-id="9d76d-250">Yerel araçlar [genel araçlara](../tools/global-tools.md) benzer, ancak diskteki belirli bir konumla ilişkilidir.</span><span class="sxs-lookup"><span data-stu-id="9d76d-250">Local tools are similar to [global tools](../tools/global-tools.md) but are associated with a particular location on disk.</span></span> <span data-ttu-id="9d76d-251">Yerel araçlar genel olarak kullanılamaz ve NuGet paketleri olarak dağıtılır.</span><span class="sxs-lookup"><span data-stu-id="9d76d-251">Local tools aren't available globally and are distributed as NuGet packages.</span></span>

> [!WARNING]
> <span data-ttu-id="9d76d-252">.NET Core 3.0 Preview 1'de yerel araçları `dotnet tool restore` `dotnet tool install`denediyseniz, örneğin çalışma veya yerel araçlar önbelleği klasörünü silin.</span><span class="sxs-lookup"><span data-stu-id="9d76d-252">If you tried local tools in .NET Core 3.0 Preview 1, such as running `dotnet tool restore` or `dotnet tool install`, delete the local tools cache folder.</span></span> <span data-ttu-id="9d76d-253">Aksi takdirde, yerel araçlar daha yeni sürümde çalışmaz.</span><span class="sxs-lookup"><span data-stu-id="9d76d-253">Otherwise, local tools won't work on any newer release.</span></span> <span data-ttu-id="9d76d-254">Bu klasör şu adreste bulunur:</span><span class="sxs-lookup"><span data-stu-id="9d76d-254">This folder is located at:</span></span>
>
> <span data-ttu-id="9d76d-255">macOS,Linux'ta:`rm -r $HOME/.dotnet/toolResolverCache`</span><span class="sxs-lookup"><span data-stu-id="9d76d-255">On macOS, Linux: `rm -r $HOME/.dotnet/toolResolverCache`</span></span>
>
> <span data-ttu-id="9d76d-256">Windows'da:`rmdir /s %USERPROFILE%\.dotnet\toolResolverCache`</span><span class="sxs-lookup"><span data-stu-id="9d76d-256">On Windows: `rmdir /s %USERPROFILE%\.dotnet\toolResolverCache`</span></span>

<span data-ttu-id="9d76d-257">Yerel araçlar, geçerli dizininizdeki bir bildirim dosya adına `dotnet-tools.json` dayanır.</span><span class="sxs-lookup"><span data-stu-id="9d76d-257">Local tools rely on a manifest file name `dotnet-tools.json` in your current directory.</span></span> <span data-ttu-id="9d76d-258">Bu bildirim dosyası, o klasörde ve aşağıda bulunabilecek araçları tanımlar.</span><span class="sxs-lookup"><span data-stu-id="9d76d-258">This manifest file defines the tools to be available at that folder and below.</span></span> <span data-ttu-id="9d76d-259">Kodunla çalışan herkesin aynı araçları geri yükleyip kullanabileceğinden emin olmak için bildirim dosyasını kodunuzla birlikte dağıtabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9d76d-259">You can distribute the manifest file with your code to ensure that anyone who works with your code can restore and use the same tools.</span></span>

<span data-ttu-id="9d76d-260">Hem genel hem de yerel araçlar için çalışma zamanının uyumlu bir sürümü gereklidir.</span><span class="sxs-lookup"><span data-stu-id="9d76d-260">For both global and local tools, a compatible version of the runtime is required.</span></span> <span data-ttu-id="9d76d-261">Şu anda hedef NuGet.org .NET Core Runtime 2.1'de birçok araç.</span><span class="sxs-lookup"><span data-stu-id="9d76d-261">Many tools currently on NuGet.org target .NET Core Runtime 2.1.</span></span> <span data-ttu-id="9d76d-262">Bu araçları genel olarak veya yerel olarak yüklemek için [NET Core 2.1 Çalışma Zamanı'nı](https://dotnet.microsoft.com/download/dotnet-core/2.1)yüklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="9d76d-262">To install these tools globally or locally, you would still need to install the [NET Core 2.1 Runtime](https://dotnet.microsoft.com/download/dotnet-core/2.1).</span></span>

### <a name="new-globaljson-options"></a><span data-ttu-id="9d76d-263">Yeni global.json seçenekleri</span><span class="sxs-lookup"><span data-stu-id="9d76d-263">New global.json options</span></span>

<span data-ttu-id="9d76d-264">*global.json* dosyası, .NET Core SDK'nın hangi sürümünün kullanıldığını tanımlamaya çalışırken daha fazla esneklik sağlayan yeni seçeneklere sahiptir.</span><span class="sxs-lookup"><span data-stu-id="9d76d-264">The *global.json* file has new options that provide more flexibility when you're trying to define which version of the .NET Core SDK is used.</span></span> <span data-ttu-id="9d76d-265">Yeni seçenekler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="9d76d-265">The new options are:</span></span>

- <span data-ttu-id="9d76d-266">`allowPrerelease`: SDK çözümleyicisinin kullanılacak SDK sürümünü seçerken yayın öncesi sürümleri ni göz önünde bulundurması gerekip gerekmediğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="9d76d-266">`allowPrerelease`: Indicates whether the SDK resolver should consider prerelease versions when selecting the SDK version to use.</span></span>
- <span data-ttu-id="9d76d-267">`rollForward`: Belirli bir SDK sürümü eksikolduğunda veya daha yüksek bir sürümü kullanma yönergesi olarak bir geri dönüş olarak, bir SDK sürümünü seçerken kullanılacak roll-forward ilkesini gösterir.</span><span class="sxs-lookup"><span data-stu-id="9d76d-267">`rollForward`: Indicates the roll-forward policy to use when selecting an SDK version, either as a fallback when a specific SDK version is missing or as a directive to use a higher version.</span></span>

<span data-ttu-id="9d76d-268">Varsayılan değerler, desteklenen değerler ve yeni eşleşen kurallar gibi değişiklikler hakkında daha fazla bilgi için [global.json genel bakış](../tools/global-json.md)bilgisine bakın.</span><span class="sxs-lookup"><span data-stu-id="9d76d-268">For more information about the changes including default values, supported values, and new matching rules, see [global.json overview](../tools/global-json.md).</span></span>

### <a name="smaller-garbage-collection-heap-sizes"></a><span data-ttu-id="9d76d-269">Küçük Çöp Toplama yığın boyutları</span><span class="sxs-lookup"><span data-stu-id="9d76d-269">Smaller Garbage Collection heap sizes</span></span>

<span data-ttu-id="9d76d-270">Çöp Toplayıcı'nın varsayılan yığın boyutu azaltıldı ve daha az bellek kullanılarak .NET Core'a neden oldu.</span><span class="sxs-lookup"><span data-stu-id="9d76d-270">The Garbage Collector's default heap size has been reduced resulting in .NET Core using less memory.</span></span> <span data-ttu-id="9d76d-271">Bu değişiklik, modern işlemci önbelleği boyutlarıyla nesil 0 ayırma bütçesiyle daha iyi hizalanır.</span><span class="sxs-lookup"><span data-stu-id="9d76d-271">This change better aligns with the generation 0 allocation budget with modern processor cache sizes.</span></span>

### <a name="garbage-collection-large-page-support"></a><span data-ttu-id="9d76d-272">Çöp Toplama Büyük Sayfa desteği</span><span class="sxs-lookup"><span data-stu-id="9d76d-272">Garbage Collection Large Page support</span></span>

<span data-ttu-id="9d76d-273">Büyük Sayfalar (Linux'taki Büyük Sayfalar olarak da bilinir), işletim sisteminin bu büyük sayfaları isteyen uygulamanın performansını artırmak için yerel sayfa boyutundan (genellikle 4K) daha büyük bellek bölgeleri oluşturabildiği bir özelliktir.</span><span class="sxs-lookup"><span data-stu-id="9d76d-273">Large Pages (also known as Huge Pages on Linux) is a feature where the operating system is able to establish memory regions larger than the native page size (often 4K) to improve performance of the application requesting these large pages.</span></span>

<span data-ttu-id="9d76d-274">Çöp Toplayıcı artık Windows'da büyük sayfaları ayırmayı seçmek için bir opt-in özelliği olarak **GCLargePages** ayarı ile yapılandırılabilir.</span><span class="sxs-lookup"><span data-stu-id="9d76d-274">The Garbage Collector can now be configured with the **GCLargePages** setting as an opt-in feature to choose to allocate large pages on Windows.</span></span>

## <a name="windows-desktop--com"></a><span data-ttu-id="9d76d-275">Windows Masaüstü & COM</span><span class="sxs-lookup"><span data-stu-id="9d76d-275">Windows Desktop & COM</span></span>

### <a name="net-core-sdk-windows-installer"></a><span data-ttu-id="9d76d-276">.NET Core SDK Windows Yükleyici</span><span class="sxs-lookup"><span data-stu-id="9d76d-276">.NET Core SDK Windows Installer</span></span>

<span data-ttu-id="9d76d-277">Windows için MSI yükleyicisi .NET Core 3.0 ile başlayarak değişti.</span><span class="sxs-lookup"><span data-stu-id="9d76d-277">The MSI installer for Windows has changed starting with .NET Core 3.0.</span></span> <span data-ttu-id="9d76d-278">SDK yükleyiciler artık SDK özellik bant sürümlerini yerinde yükseltecektir.</span><span class="sxs-lookup"><span data-stu-id="9d76d-278">The SDK installers will now upgrade SDK feature-band releases in place.</span></span> <span data-ttu-id="9d76d-279">Özellik bantları, sürüm numarasının *yama* bölümündeki *yüzlerce* grupta tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="9d76d-279">Feature bands are defined in the *hundreds* groups in the *patch* section of the version number.</span></span> <span data-ttu-id="9d76d-280">Örneğin, \*\*3.0._ 101_ \*\* ve \*\*3.0._ 201_ \*\* iki farklı özellik bantları sürümleri ise \*\*3.0 vardır._ 101_ \*\* ve \*\*3.0._ 199_ \*\* aynı özellik grubunda.</span><span class="sxs-lookup"><span data-stu-id="9d76d-280">For example, **3.0._101_** and **3.0._201_** are versions in two different feature bands while **3.0._101_** and **3.0._199_** are in the same feature band.</span></span> <span data-ttu-id="9d76d-281">Ve, ne zaman .NET Çekirdek SDK \*\*3.0._ 101_ \*\* yüklü, .NET Çekirdek SDK \*\*3.0._ Varsa 100_ \*\* makineden çıkarılır.</span><span class="sxs-lookup"><span data-stu-id="9d76d-281">And, when .NET Core SDK **3.0._101_** is installed, .NET Core SDK **3.0._100_** will be removed from the machine if it exists.</span></span> <span data-ttu-id="9d76d-282">Ne zaman .NET Çekirdek SDK \*\*3.0._ 200_ \*\* aynı makineye yüklenir, .NET Core SDK \*\*3.0._ 101_ \*\* kaldırılmayacak.</span><span class="sxs-lookup"><span data-stu-id="9d76d-282">When .NET Core SDK **3.0._200_** is installed on the same machine, .NET Core SDK **3.0._101_** won't be removed.</span></span>

<span data-ttu-id="9d76d-283">Sürüm hakkında daha fazla bilgi için [.NET Core'un nasıl sürümlendirilebildiğini](../versions/index.md)öğrenin.</span><span class="sxs-lookup"><span data-stu-id="9d76d-283">For more information about versioning, see [Overview of how .NET Core is versioned](../versions/index.md).</span></span>

### <a name="windows-desktop"></a><span data-ttu-id="9d76d-284">Windows masaüstü</span><span class="sxs-lookup"><span data-stu-id="9d76d-284">Windows desktop</span></span>

<span data-ttu-id="9d76d-285">.NET Core 3.0, Windows Presentation Foundation (WPF) ve Windows Formlarını kullanarak Windows masaüstü uygulamalarını destekler.</span><span class="sxs-lookup"><span data-stu-id="9d76d-285">.NET Core 3.0 supports Windows desktop applications using Windows Presentation Foundation (WPF) and Windows Forms.</span></span> <span data-ttu-id="9d76d-286">Bu çerçeveler aynı zamanda [XAML adaları](/windows/uwp/xaml-platform/xaml-host-controls)üzerinden Windows UI XAML Kütüphanesi (WinUI) modern denetimler ve Akıcı stil kullanarak destek.</span><span class="sxs-lookup"><span data-stu-id="9d76d-286">These frameworks also support using modern controls and Fluent styling from the Windows UI XAML Library (WinUI) via [XAML islands](/windows/uwp/xaml-platform/xaml-host-controls).</span></span>

<span data-ttu-id="9d76d-287">Windows Desktop bileşeni, Windows .NET Core 3.0 SDK'nın bir parçasıdır.</span><span class="sxs-lookup"><span data-stu-id="9d76d-287">The Windows Desktop component is part of the Windows .NET Core 3.0 SDK.</span></span>

<span data-ttu-id="9d76d-288">Aşağıdaki `dotnet` komutlarla yeni bir WPF veya Windows Forms uygulaması oluşturabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="9d76d-288">You can create a new WPF or Windows Forms app with the following `dotnet` commands:</span></span>

```dotnetcli
dotnet new wpf
dotnet new winforms
```

<span data-ttu-id="9d76d-289">Visual Studio 2019 ,NET Core 3.0 Windows Forms ve WPF için **Yeni Proje** şablonları ekler.</span><span class="sxs-lookup"><span data-stu-id="9d76d-289">Visual Studio 2019 adds **New Project** templates for .NET Core 3.0 Windows Forms and WPF.</span></span>

<span data-ttu-id="9d76d-290">Varolan bir .NET Framework uygulamasının bağlantı noktası hakkında daha fazla bilgi için Port [WPF projeleri](../../desktop-wpf/migration/convert-project-from-net-framework.md) ve [Bağlantı Noktası Windows Formları projelerine](../porting/winforms.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="9d76d-290">For more information about how to port an existing .NET Framework application, see [Port WPF projects](../../desktop-wpf/migration/convert-project-from-net-framework.md) and [Port Windows Forms projects](../porting/winforms.md).</span></span>

#### <a name="winforms-high-dpi"></a><span data-ttu-id="9d76d-291">WinForms yüksek DPI</span><span class="sxs-lookup"><span data-stu-id="9d76d-291">WinForms high DPI</span></span>

<span data-ttu-id="9d76d-292">.NET Core Windows Forms uygulamaları ile yüksek <xref:System.Windows.Forms.Application.SetHighDpiMode(System.Windows.Forms.HighDpiMode)?displayProperty=nameWithType>DPI modu ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9d76d-292">.NET Core Windows Forms applications can set high DPI mode with <xref:System.Windows.Forms.Application.SetHighDpiMode(System.Windows.Forms.HighDpiMode)?displayProperty=nameWithType>.</span></span> <span data-ttu-id="9d76d-293">Yöntem, `SetHighDpiMode` ayarı daha önce `App.Manifest` `Application.Run`P/Invoke gibi başka yollarla ayarlanmadıkça ilgili yüksek DPI modunu ayarlar.</span><span class="sxs-lookup"><span data-stu-id="9d76d-293">The `SetHighDpiMode` method sets the corresponding high DPI mode unless the setting has been set by other means like `App.Manifest` or P/Invoke before `Application.Run`.</span></span>

<span data-ttu-id="9d76d-294">Enum `highDpiMode` tarafından ifade edilen olası değerler şunlardır: <xref:System.Windows.Forms.HighDpiMode?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="9d76d-294">The possible `highDpiMode` values, as expressed by the <xref:System.Windows.Forms.HighDpiMode?displayProperty=nameWithType> enum are:</span></span>

- `DpiUnaware`
- `SystemAware`
- `PerMonitor`
- `PerMonitorV2`
- `DpiUnawareGdiScaled`

<span data-ttu-id="9d76d-295">Yüksek DPI modları hakkında daha fazla bilgi için [Windows'da Yüksek DPI Masaüstü Uygulama Geliştirme'ye](/windows/desktop/hidpi/high-dpi-desktop-application-development-on-windows)bakın.</span><span class="sxs-lookup"><span data-stu-id="9d76d-295">For more information about high DPI modes, see [High DPI Desktop Application Development on Windows](/windows/desktop/hidpi/high-dpi-desktop-application-development-on-windows).</span></span>

### <a name="create-com-components"></a><span data-ttu-id="9d76d-296">COM bileşenleri oluşturma</span><span class="sxs-lookup"><span data-stu-id="9d76d-296">Create COM components</span></span>

<span data-ttu-id="9d76d-297">Windows'da artık COM çağrılabilir yönetilen bileşenler oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9d76d-297">On Windows, you can now create COM-callable managed components.</span></span> <span data-ttu-id="9d76d-298">Bu özellik, .NET Core'u COM eklenti modelleri ile kullanmak ve aynı zamanda .NET Framework ile eşlik sağlamak için çok önemlidir.</span><span class="sxs-lookup"><span data-stu-id="9d76d-298">This capability is critical to use .NET Core with COM add-in models and also to provide parity with .NET Framework.</span></span>

<span data-ttu-id="9d76d-299">*Mscoree.dll'nin* COM sunucusu olarak kullanıldığı .NET Framework'ün aksine, .NET Core, COM bileşeninizi oluşturduğunuzda *depo* gözüne yerel bir başlatıcı dll ekler.</span><span class="sxs-lookup"><span data-stu-id="9d76d-299">Unlike .NET Framework where the *mscoree.dll* was used as the COM server, .NET Core will add a native launcher dll to the *bin* directory when you build your COM component.</span></span>

<span data-ttu-id="9d76d-300">Com bileşeninin nasıl oluşturulup tüketilmesine bir örnek [için, COM](https://github.com/dotnet/samples/tree/master/core/extensions/COMServerDemo)Demosu'na bakın.</span><span class="sxs-lookup"><span data-stu-id="9d76d-300">For an example of how to create a COM component and consume it, see the [COM Demo](https://github.com/dotnet/samples/tree/master/core/extensions/COMServerDemo).</span></span>

### <a name="windows-native-interop"></a><span data-ttu-id="9d76d-301">Windows Native Interop</span><span class="sxs-lookup"><span data-stu-id="9d76d-301">Windows Native Interop</span></span>

<span data-ttu-id="9d76d-302">Windows düz C API'leri, COM ve WinRT şeklinde zengin bir yerel API sunar.</span><span class="sxs-lookup"><span data-stu-id="9d76d-302">Windows offers a rich native API in the form of flat C APIs, COM, and WinRT.</span></span> <span data-ttu-id="9d76d-303">.NET Core **P/Invoke'ı**desteklerken , .NET Core 3.0, **COM API'lerini CoCreate** ve **Activate WinRT API'lerini**etkinleştirme özelliğini ekler.</span><span class="sxs-lookup"><span data-stu-id="9d76d-303">While .NET Core supports **P/Invoke**, .NET Core 3.0 adds the ability to **CoCreate COM APIs** and **Activate WinRT APIs**.</span></span> <span data-ttu-id="9d76d-304">Kod örneği için [Excel Demosu'na](https://github.com/dotnet/samples/tree/master/core/extensions/ExcelDemo)bakın.</span><span class="sxs-lookup"><span data-stu-id="9d76d-304">For a code example, see the [Excel Demo](https://github.com/dotnet/samples/tree/master/core/extensions/ExcelDemo).</span></span>

### <a name="msix-deployment"></a><span data-ttu-id="9d76d-305">MSIX Dağıtım</span><span class="sxs-lookup"><span data-stu-id="9d76d-305">MSIX Deployment</span></span>

<span data-ttu-id="9d76d-306">[MSIX](https://docs.microsoft.com/windows/msix/) yeni bir Windows uygulama paketi biçimidir.</span><span class="sxs-lookup"><span data-stu-id="9d76d-306">[MSIX](https://docs.microsoft.com/windows/msix/) is a new Windows application package format.</span></span> <span data-ttu-id="9d76d-307">.NET Core 3.0 masaüstü uygulamalarını Windows 10'a dağıtmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="9d76d-307">It can be used to deploy .NET Core 3.0 desktop applications to Windows 10.</span></span>

<span data-ttu-id="9d76d-308">Visual Studio 2019'da bulunan [Windows Uygulama Paketleme Projesi,](https://docs.microsoft.com/windows/uwp/porting/desktop-to-uwp-packaging-dot-net) [bağımsız](../deploying/index.md#publish-self-contained) .NET Core uygulamalarıyla MSIX paketleri oluşturmanıza olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="9d76d-308">The [Windows Application Packaging Project](https://docs.microsoft.com/windows/uwp/porting/desktop-to-uwp-packaging-dot-net), available in Visual Studio 2019, allows you to create MSIX packages with [self-contained](../deploying/index.md#publish-self-contained) .NET Core applications.</span></span>

<span data-ttu-id="9d76d-309">.NET Core proje `<RuntimeIdentifiers>` dosyasında, özellikteki desteklenen çalışma sürelerini belirtilmelidir:</span><span class="sxs-lookup"><span data-stu-id="9d76d-309">The .NET Core project file must specify the supported runtimes in the `<RuntimeIdentifiers>` property:</span></span>

```xml
<RuntimeIdentifiers>win-x86;win-x64</RuntimeIdentifiers>
```

## <a name="linux-improvements"></a><span data-ttu-id="9d76d-310">Linux geliştirmeleri</span><span class="sxs-lookup"><span data-stu-id="9d76d-310">Linux improvements</span></span>

### <a name="serialport-for-linux"></a><span data-ttu-id="9d76d-311">Linux için SerialPort</span><span class="sxs-lookup"><span data-stu-id="9d76d-311">SerialPort for Linux</span></span>

<span data-ttu-id="9d76d-312">.NET Core 3.0 Linux <xref:System.IO.Ports.SerialPort?displayProperty=nameWithType> için temel destek sağlar.</span><span class="sxs-lookup"><span data-stu-id="9d76d-312">.NET Core 3.0 provides basic support for <xref:System.IO.Ports.SerialPort?displayProperty=nameWithType> on Linux.</span></span>

<span data-ttu-id="9d76d-313">Daha önce,.NET Core yalnızca `SerialPort` Windows'da kullanılarak desteklenirdi.</span><span class="sxs-lookup"><span data-stu-id="9d76d-313">Previously, .NET Core only supported using `SerialPort` on Windows.</span></span>

<span data-ttu-id="9d76d-314">Linux'taki seri bağlantı noktası için sınırlı destek hakkında daha fazla bilgi için [#33146 GitHub sorununa](https://github.com/dotnet/corefx/issues/33146)bakın.</span><span class="sxs-lookup"><span data-stu-id="9d76d-314">For more information about the limited support for the serial port on Linux, see [GitHub issue #33146](https://github.com/dotnet/corefx/issues/33146).</span></span>

### <a name="docker-and-cgroup-memory-limits"></a><span data-ttu-id="9d76d-315">Docker ve cgroup bellek Sınırları</span><span class="sxs-lookup"><span data-stu-id="9d76d-315">Docker and cgroup memory Limits</span></span>

<span data-ttu-id="9d76d-316">Docker ile Linux'ta .NET Core 3.0'ı çalıştırmak cgroup bellek limitleri ile daha iyi çalışır.</span><span class="sxs-lookup"><span data-stu-id="9d76d-316">Running .NET Core 3.0 on Linux with Docker works better with cgroup memory limits.</span></span> <span data-ttu-id="9d76d-317">.NET Core gibi bellek sınırları `docker run -m`içeren bir Docker kapsayıcısı çalıştırmak, .NET Core'un nasıl çalıştığını değiştirir.</span><span class="sxs-lookup"><span data-stu-id="9d76d-317">Running a Docker container with memory limits, such as with `docker run -m`, changes how .NET Core behaves.</span></span>

- <span data-ttu-id="9d76d-318">Varsayılan Çöp Toplayıcı (GC) yığın boyutu: en fazla 20 mb veya kapsayıcıdaki bellek sınırının %75'i.</span><span class="sxs-lookup"><span data-stu-id="9d76d-318">Default Garbage Collector (GC) heap size: maximum of 20 mb or 75% of the memory limit on the container.</span></span>
- <span data-ttu-id="9d76d-319">Açık boyut mutlak bir sayı veya cgroup sınırı yüzdesi olarak ayarlanabilir.</span><span class="sxs-lookup"><span data-stu-id="9d76d-319">Explicit size can be set as an absolute number or percentage of cgroup limit.</span></span>
- <span data-ttu-id="9d76d-320">GC yığını başına en az ayrılmış segment boyutu 16 mb'dır.</span><span class="sxs-lookup"><span data-stu-id="9d76d-320">Minimum reserved segment size per GC heap is 16 mb.</span></span> <span data-ttu-id="9d76d-321">Bu boyut, makinelerde oluşturulan yığın sayısını azaltır.</span><span class="sxs-lookup"><span data-stu-id="9d76d-321">This size reduces the number of heaps that are created on machines.</span></span>

### <a name="gpio-support-for-raspberry-pi"></a><span data-ttu-id="9d76d-322">Raspberry Pi için GPIO Desteği</span><span class="sxs-lookup"><span data-stu-id="9d76d-322">GPIO Support for Raspberry Pi</span></span>

<span data-ttu-id="9d76d-323">GPIO programlama için kullanabileceğiniz NuGet'e iki paket yayımlanmıştır:</span><span class="sxs-lookup"><span data-stu-id="9d76d-323">Two packages have been released to NuGet that you can use for GPIO programming:</span></span>

- [<span data-ttu-id="9d76d-324">System.Device.Gpio</span><span class="sxs-lookup"><span data-stu-id="9d76d-324">System.Device.Gpio</span></span>](https://www.nuget.org/packages/System.Device.Gpio)
- [<span data-ttu-id="9d76d-325">Iot.Device.Bindings</span><span class="sxs-lookup"><span data-stu-id="9d76d-325">Iot.Device.Bindings</span></span>](https://www.nuget.org/packages/Iot.Device.Bindings)

<span data-ttu-id="9d76d-326">GPIO paketleri *GPIO,* *SPI,* *I2C*ve *PWM* cihazları için API'leri içerir.</span><span class="sxs-lookup"><span data-stu-id="9d76d-326">The GPIO packages include APIs for *GPIO*, *SPI*, *I2C*, and *PWM* devices.</span></span> <span data-ttu-id="9d76d-327">IoT bağlama paketi aygıt bağlamalarını içerir.</span><span class="sxs-lookup"><span data-stu-id="9d76d-327">The IoT bindings package includes device bindings.</span></span> <span data-ttu-id="9d76d-328">Daha fazla bilgi için [GitHub repo cihazlarına](https://github.com/dotnet/iot/blob/master/src/devices/)bakın.</span><span class="sxs-lookup"><span data-stu-id="9d76d-328">For more information, see the [devices GitHub repo](https://github.com/dotnet/iot/blob/master/src/devices/).</span></span>

### <a name="arm64-linux-support"></a><span data-ttu-id="9d76d-329">ARM64 Linux desteği</span><span class="sxs-lookup"><span data-stu-id="9d76d-329">ARM64 Linux support</span></span>

<span data-ttu-id="9d76d-330">.NET Core 3.0, Linux için ARM64 desteği ne kadar ekler.</span><span class="sxs-lookup"><span data-stu-id="9d76d-330">.NET Core 3.0 adds support for ARM64 for Linux.</span></span> <span data-ttu-id="9d76d-331">ARM64 için birincil kullanım örneği şu anda IoT senaryoları ile.</span><span class="sxs-lookup"><span data-stu-id="9d76d-331">The primary use case for ARM64 is currently with IoT scenarios.</span></span> <span data-ttu-id="9d76d-332">Daha fazla bilgi için [bkz.](https://github.com/dotnet/announcements/issues/82)</span><span class="sxs-lookup"><span data-stu-id="9d76d-332">For more information, see [.NET Core ARM64 Status](https://github.com/dotnet/announcements/issues/82).</span></span>

<span data-ttu-id="9d76d-333">[ARM64'teki .NET Core için Docker görüntüleri](https://hub.docker.com/r/microsoft/dotnet/) Alpine, Debian ve Ubuntu için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="9d76d-333">[Docker images for .NET Core on ARM64](https://hub.docker.com/r/microsoft/dotnet/) are available for Alpine, Debian, and Ubuntu.</span></span>

> [!NOTE]
> <span data-ttu-id="9d76d-334">**ARM64** Windows desteği henüz kullanılamıyor.</span><span class="sxs-lookup"><span data-stu-id="9d76d-334">**ARM64** Windows support isn't yet available.</span></span>

## <a name="security"></a><span data-ttu-id="9d76d-335">Güvenlik</span><span class="sxs-lookup"><span data-stu-id="9d76d-335">Security</span></span>

### <a name="tls-13--openssl-111-on-linux"></a><span data-ttu-id="9d76d-336">TLS 1.3 & Linux'ta OpenSSL 1.1.1</span><span class="sxs-lookup"><span data-stu-id="9d76d-336">TLS 1.3 & OpenSSL 1.1.1 on Linux</span></span>

<span data-ttu-id="9d76d-337">.NET Core artık [OpenSSL 1.1.1'de belirli](https://www.openssl.org/blog/blog/2018/09/11/release111/)bir ortamda mevcut olduğunda TLS 1.3 desteğinden yararlanıyor.</span><span class="sxs-lookup"><span data-stu-id="9d76d-337">.NET Core now takes advantage of [TLS 1.3 support in OpenSSL 1.1.1](https://www.openssl.org/blog/blog/2018/09/11/release111/), when it's available in a given environment.</span></span> <span data-ttu-id="9d76d-338">TLS 1.3 ile:</span><span class="sxs-lookup"><span data-stu-id="9d76d-338">With TLS 1.3:</span></span>

- <span data-ttu-id="9d76d-339">Bağlantı süreleri, istemci ve sunucu arasında gereken azaltılmış gidiş dönüşlerle iyileştirilir.</span><span class="sxs-lookup"><span data-stu-id="9d76d-339">Connection times are improved with reduced round trips required between the client and server.</span></span>
- <span data-ttu-id="9d76d-340">Çeşitli eski ve güvensiz şifreleme algoritmalarının kaldırılması nedeniyle geliştirilmiş güvenlik.</span><span class="sxs-lookup"><span data-stu-id="9d76d-340">Improved security because of the removal of various obsolete and insecure cryptographic algorithms.</span></span>

<span data-ttu-id="9d76d-341">Kullanılabilir olduğunda, .NET Core 3.0, Linux sisteminde **OpenSSL 1.1.1**, **OpenSSL 1.1.0**veya **OpenSSL 1.0.2** kullanır.</span><span class="sxs-lookup"><span data-stu-id="9d76d-341">When available, .NET Core 3.0 uses **OpenSSL 1.1.1**, **OpenSSL 1.1.0**, or **OpenSSL 1.0.2** on a Linux system.</span></span> <span data-ttu-id="9d76d-342">**OpenSSL 1.1.1** kullanılabilir <xref:System.Net.Security.SslStream?displayProperty=nameWithType> olduğunda, <xref:System.Net.Http.HttpClient?displayProperty=nameWithType> hem **tls 1.3'ü** hem de türleri kullanır (hem istemci hem de sunucu nun **TLS 1.3'ü**desteklediğini varsayarsak).</span><span class="sxs-lookup"><span data-stu-id="9d76d-342">When **OpenSSL 1.1.1** is available, both <xref:System.Net.Security.SslStream?displayProperty=nameWithType> and <xref:System.Net.Http.HttpClient?displayProperty=nameWithType> types will use **TLS 1.3** (assuming both the client and server support **TLS 1.3**).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="9d76d-343">Windows ve macOS henüz **TLS 1.3'u**destekletmiyor.</span><span class="sxs-lookup"><span data-stu-id="9d76d-343">Windows and macOS do not yet support **TLS 1.3**.</span></span> <span data-ttu-id="9d76d-344">.NET Core 3.0, destek sunulduğunda bu işletim sistemlerinde **TLS 1.3'u** destekleyecektir.</span><span class="sxs-lookup"><span data-stu-id="9d76d-344">.NET Core 3.0 will support **TLS 1.3** on these operating systems when support becomes available.</span></span>

<span data-ttu-id="9d76d-345">Aşağıdaki C# 8.0 örneği Ubuntu 18.10'da .NET Core <https://www.cloudflare.com>3.0'ı gösterir:</span><span class="sxs-lookup"><span data-stu-id="9d76d-345">The following C# 8.0 example demonstrates .NET Core 3.0 on Ubuntu 18.10 connecting to <https://www.cloudflare.com>:</span></span>

[!code-csharp[TLSExample](~/samples/snippets/core/whats-new/whats-new-in-30/cs/TLS.cs#TLS)]

### <a name="cryptography-ciphers"></a><span data-ttu-id="9d76d-346">Şifreleme şifreleri</span><span class="sxs-lookup"><span data-stu-id="9d76d-346">Cryptography ciphers</span></span>

<span data-ttu-id="9d76d-347">.NET <xref:System.Security.Cryptography.AesGcm?displayProperty=nameWithType> 3.0, <xref:System.Security.Cryptography.AesCcm?displayProperty=nameWithType> sırasıyla ve sırasıyla uygulanan **AES-GCM** ve **AES-CCM** şifreleri için destek ekler.</span><span class="sxs-lookup"><span data-stu-id="9d76d-347">.NET 3.0 adds support for **AES-GCM** and **AES-CCM** ciphers, implemented with <xref:System.Security.Cryptography.AesGcm?displayProperty=nameWithType> and <xref:System.Security.Cryptography.AesCcm?displayProperty=nameWithType> respectively.</span></span> <span data-ttu-id="9d76d-348">Bu algoritmalar, [ilişkilendirme verileri (AEAD) algoritmaları ile kimlik doğrulaması şifreleme vardır.](https://en.wikipedia.org/wiki/Authenticated_encryption)</span><span class="sxs-lookup"><span data-stu-id="9d76d-348">These algorithms are both [Authenticated Encryption with Association Data (AEAD) algorithms](https://en.wikipedia.org/wiki/Authenticated_encryption).</span></span>

<span data-ttu-id="9d76d-349">Aşağıdaki kod, rasgele `AesGcm` verileri şifrelemek ve çözmek için şifreyi kullanarak gösterir.</span><span class="sxs-lookup"><span data-stu-id="9d76d-349">The following code demonstrates using `AesGcm` cipher to encrypt and decrypt random data.</span></span>

[!code-csharp[AesGcm](~/samples/snippets/core/whats-new/whats-new-in-30/cs/Cipher.cs#AesGcm)]

### <a name="cryptographic-key-importexport"></a><span data-ttu-id="9d76d-350">Şifreleme Anahtarı İthalat/Verme</span><span class="sxs-lookup"><span data-stu-id="9d76d-350">Cryptographic Key Import/Export</span></span>

<span data-ttu-id="9d76d-351">.NET Core 3.0, standart biçimlerden asimetrik ortak ve özel anahtarların ithalat ve dışa aktarını destekler.</span><span class="sxs-lookup"><span data-stu-id="9d76d-351">.NET Core 3.0 supports the import and export of asymmetric public and private keys from standard formats.</span></span> <span data-ttu-id="9d76d-352">X.509 sertifikası kullanmanız gerekmez.</span><span class="sxs-lookup"><span data-stu-id="9d76d-352">You don't need to use an X.509 certificate.</span></span>

<span data-ttu-id="9d76d-353">*RSA,* *DSA,* *ECDsa*ve *ECDiffieHellman*gibi tüm anahtar türleri aşağıdaki biçimleri destekler:</span><span class="sxs-lookup"><span data-stu-id="9d76d-353">All key types, such as *RSA*, *DSA*, *ECDsa*, and *ECDiffieHellman*, support the following formats:</span></span>

- <span data-ttu-id="9d76d-354">**Ortak Anahtar**</span><span class="sxs-lookup"><span data-stu-id="9d76d-354">**Public Key**</span></span>
  - <span data-ttu-id="9d76d-355">X.509 KonuPublicKeyInfo</span><span class="sxs-lookup"><span data-stu-id="9d76d-355">X.509 SubjectPublicKeyInfo</span></span>

- <span data-ttu-id="9d76d-356">**Özel anahtar**</span><span class="sxs-lookup"><span data-stu-id="9d76d-356">**Private key**</span></span>
  - <span data-ttu-id="9d76d-357">PKCS#8 PrivateKeyInfo</span><span class="sxs-lookup"><span data-stu-id="9d76d-357">PKCS#8 PrivateKeyInfo</span></span>
  - <span data-ttu-id="9d76d-358">PKCS#8 ŞifreliPrivateKeyInfo</span><span class="sxs-lookup"><span data-stu-id="9d76d-358">PKCS#8 EncryptedPrivateKeyInfo</span></span>

<span data-ttu-id="9d76d-359">RSA tuşları da destekler:</span><span class="sxs-lookup"><span data-stu-id="9d76d-359">RSA keys also support:</span></span>

- <span data-ttu-id="9d76d-360">**Ortak Anahtar**</span><span class="sxs-lookup"><span data-stu-id="9d76d-360">**Public Key**</span></span>
  - <span data-ttu-id="9d76d-361">PKCS#1 RSAPublicKey</span><span class="sxs-lookup"><span data-stu-id="9d76d-361">PKCS#1 RSAPublicKey</span></span>

- <span data-ttu-id="9d76d-362">**Özel anahtar**</span><span class="sxs-lookup"><span data-stu-id="9d76d-362">**Private key**</span></span>
  - <span data-ttu-id="9d76d-363">PKCS#1 RSAPrivateKey</span><span class="sxs-lookup"><span data-stu-id="9d76d-363">PKCS#1 RSAPrivateKey</span></span>

<span data-ttu-id="9d76d-364">Dışa aktarma yöntemleri DER kodlu ikili veri üretir ve alma yöntemleri de aynı şeyi bekler.</span><span class="sxs-lookup"><span data-stu-id="9d76d-364">The export methods produce DER-encoded binary data, and the import methods expect the same.</span></span> <span data-ttu-id="9d76d-365">Bir anahtar metin dostu PEM biçiminde depolanırsa, arayanın alma yöntemini aramadan önce içeriği temel olarak 64-decode'u çözmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="9d76d-365">If a key is stored in the text-friendly PEM format, the caller will need to base64-decode the content before calling an import method.</span></span>

[!code-csharp[RSA](~/samples/snippets/core/whats-new/whats-new-in-30/cs/RSA.cs#Rsa)]

<span data-ttu-id="9d76d-366">**PKCS#8** dosyaları ile <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo?displayProperty=nameWithType> kontrol edilebilir ve **PFX/PKCS#12** dosyaları <xref:System.Security.Cryptography.Pkcs.Pkcs12Info?displayProperty=nameWithType>ile kontrol edilebilir.</span><span class="sxs-lookup"><span data-stu-id="9d76d-366">**PKCS#8** files can be inspected with <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo?displayProperty=nameWithType> and **PFX/PKCS#12** files can be inspected with <xref:System.Security.Cryptography.Pkcs.Pkcs12Info?displayProperty=nameWithType>.</span></span> <span data-ttu-id="9d76d-367">**PFX/PKCS#12** dosyaları ile <xref:System.Security.Cryptography.Pkcs.Pkcs12Builder?displayProperty=nameWithType>manipüle edilebilir.</span><span class="sxs-lookup"><span data-stu-id="9d76d-367">**PFX/PKCS#12** files can be manipulated with <xref:System.Security.Cryptography.Pkcs.Pkcs12Builder?displayProperty=nameWithType>.</span></span>

## <a name="net-core-30-api-changes"></a><span data-ttu-id="9d76d-368">.NET Core 3.0 API değişiklikleri</span><span class="sxs-lookup"><span data-stu-id="9d76d-368">.NET Core 3.0 API changes</span></span>

### <a name="ranges-and-indices"></a><span data-ttu-id="9d76d-369">Aralıklar ve endeksler</span><span class="sxs-lookup"><span data-stu-id="9d76d-369">Ranges and indices</span></span>

<span data-ttu-id="9d76d-370">Yeni <xref:System.Index?displayProperty=nameWithType> tür dizin oluşturma için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="9d76d-370">The new <xref:System.Index?displayProperty=nameWithType> type can be used for indexing.</span></span> <span data-ttu-id="9d76d-371">En başından veya `int` sondan sayılan bir önek `^` işlecinden (C#) bir tane oluşturabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="9d76d-371">You can create one from an `int` that counts from the beginning, or with a prefix `^` operator (C#) that counts from the end:</span></span>

```csharp
Index i1 = 3;  // number 3 from beginning
Index i2 = ^4; // number 4 from end
int[] a = { 0, 1, 2, 3, 4, 5, 6, 7, 8, 9 };
Console.WriteLine($"{a[i1]}, {a[i2]}"); // "3, 6"
```

<span data-ttu-id="9d76d-372">Ayrıca, <xref:System.Range?displayProperty=nameWithType> biri başlangıç, diğeri bitiş `Index` için olmak üzere iki değerden oluşan ve `x..y` aralık ifadesi (C#) ile yazılabilir.</span><span class="sxs-lookup"><span data-stu-id="9d76d-372">There's also the <xref:System.Range?displayProperty=nameWithType> type, which consists of two `Index` values, one for the start and one for the end, and can be written with a `x..y` range expression (C#).</span></span> <span data-ttu-id="9d76d-373">Daha sonra bir `Range`dilim üreten bir , ile dizine yapabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="9d76d-373">You can then index with a `Range`, which produces a slice:</span></span>

```csharp
var slice = a[i1..i2]; // { 3, 4, 5 }
```

<span data-ttu-id="9d76d-374">Daha fazla bilgi [için, aralıkları ve endeksleri öğretici](../../csharp/tutorials/ranges-indexes.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="9d76d-374">For more information, see the [ranges and indices tutorial](../../csharp/tutorials/ranges-indexes.md).</span></span>

### <a name="async-streams"></a><span data-ttu-id="9d76d-375">Zaman uyumsuz akışlar</span><span class="sxs-lookup"><span data-stu-id="9d76d-375">Async streams</span></span>

<span data-ttu-id="9d76d-376">Türü <xref:System.Collections.Generic.IAsyncEnumerable%601> yeni bir asynchronous <xref:System.Collections.Generic.IEnumerable%601>sürümüdür.</span><span class="sxs-lookup"><span data-stu-id="9d76d-376">The <xref:System.Collections.Generic.IAsyncEnumerable%601> type is a new asynchronous version of <xref:System.Collections.Generic.IEnumerable%601>.</span></span> <span data-ttu-id="9d76d-377">Dil, `await foreach` öğelerini `IAsyncEnumerable<T>` tüketmenizi ve `yield return` bunları kullanarak öğeleri oluşturmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="9d76d-377">The language lets you `await foreach` over `IAsyncEnumerable<T>` to consume their elements, and use `yield return` to them to produce elements.</span></span>

<span data-ttu-id="9d76d-378">Aşağıdaki örnek, async akışlarının hem üretimini hem de tüketimini göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="9d76d-378">The following example demonstrates both production and consumption of async streams.</span></span> <span data-ttu-id="9d76d-379">`foreach` İfade async ve kendisi `yield return` arayanlar için bir async akışı oluşturmak için kullanır.</span><span class="sxs-lookup"><span data-stu-id="9d76d-379">The `foreach` statement is async and itself uses `yield return` to produce an async stream for callers.</span></span> <span data-ttu-id="9d76d-380">Bu desen `yield return`(kullanarak) async akışları üretmek için önerilen modeldir.</span><span class="sxs-lookup"><span data-stu-id="9d76d-380">This pattern (using `yield return`) is the recommended model for producing async streams.</span></span>

```csharp
async IAsyncEnumerable<int> GetBigResultsAsync()
{
    await foreach (var result in GetResultsAsync())
    {
        if (result > 20) yield return result;
    }
}
```

<span data-ttu-id="9d76d-381">Yapabilmenin `await foreach`yanı sıra, async yineleyicileri de oluşturabilirsiniz, örneğin, hem de `IAsyncEnumerable/IAsyncEnumerator` `await` `yield` içinde oluşturabileceğiniz bir yineleme yi döndürebilir.</span><span class="sxs-lookup"><span data-stu-id="9d76d-381">In addition to being able to `await foreach`, you can also create async iterators, for example, an iterator that returns an `IAsyncEnumerable/IAsyncEnumerator` that you can both `await` and `yield` in.</span></span> <span data-ttu-id="9d76d-382">Atılması gereken nesneler için, `IAsyncDisposable`çeşitli BCL türlerinin uyguladığı `Stream` ve . `Timer`</span><span class="sxs-lookup"><span data-stu-id="9d76d-382">For objects that need to be disposed, you can use `IAsyncDisposable`, which various BCL types implement, such as `Stream` and `Timer`.</span></span>

<span data-ttu-id="9d76d-383">Daha fazla bilgi [için, async akışları öğretici](../../csharp/tutorials/generate-consume-asynchronous-stream.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="9d76d-383">For more information, see the [async streams tutorial](../../csharp/tutorials/generate-consume-asynchronous-stream.md).</span></span>

### <a name="ieee-floating-point"></a><span data-ttu-id="9d76d-384">IEEE Kayan nokta</span><span class="sxs-lookup"><span data-stu-id="9d76d-384">IEEE Floating-point</span></span>

<span data-ttu-id="9d76d-385">Kayan nokta API'leri [IEEE 754-2008 revizyonuna](https://en.wikipedia.org/wiki/IEEE_754-2008_revision)uyacak şekilde güncellenmektedir.</span><span class="sxs-lookup"><span data-stu-id="9d76d-385">Floating point APIs are being updated to comply with [IEEE 754-2008 revision](https://en.wikipedia.org/wiki/IEEE_754-2008_revision).</span></span> <span data-ttu-id="9d76d-386">Bu değişikliklerin amacı, **gerekli** tüm işlemleri ortaya çıkarmak ve iEEE spec ile davranışsal olarak uyumlu olduğundan emin olmaktır. Kayan nokta iyileştirmeleri hakkında daha fazla bilgi için [.NET Core 3.0 blog gönderisindeki Kayan Nokta Ayrıştırma ve Biçimlendirme geliştirmelerine](https://devblogs.microsoft.com/dotnet/floating-point-parsing-and-formatting-improvements-in-net-core-3-0/) bakın.</span><span class="sxs-lookup"><span data-stu-id="9d76d-386">The goal of these changes is to expose all **required** operations and ensure that they're behaviorally compliant with the IEEE spec. For more information about floating-point improvements, see the [Floating-Point Parsing and Formatting improvements in .NET Core 3.0](https://devblogs.microsoft.com/dotnet/floating-point-parsing-and-formatting-improvements-in-net-core-3-0/) blog post.</span></span>

<span data-ttu-id="9d76d-387">Ayrışma ve biçimlendirme düzeltmeleri şunlardır:</span><span class="sxs-lookup"><span data-stu-id="9d76d-387">Parsing and formatting fixes include:</span></span>

- <span data-ttu-id="9d76d-388">Herhangi bir uzunluktaki girişleri doğru bir şekilde ayrıştın ve yuvarlatın.</span><span class="sxs-lookup"><span data-stu-id="9d76d-388">Correctly parse and round inputs of any length.</span></span>
- <span data-ttu-id="9d76d-389">Doğru ayrışdırın ve biçim negatif sıfır.</span><span class="sxs-lookup"><span data-stu-id="9d76d-389">Correctly parse and format negative zero.</span></span>
- <span data-ttu-id="9d76d-390">Doğru `Infinity` ayrışdırma `NaN` ve büyük/küçük harf duyarsız kontrol yaparak `+` ve varsa isteğe bağlı bir önceki izin.</span><span class="sxs-lookup"><span data-stu-id="9d76d-390">Correctly parse `Infinity` and `NaN` by doing a case-insensitive check and allowing an optional preceding `+` where applicable.</span></span>

<span data-ttu-id="9d76d-391">Yeni <xref:System.Math?displayProperty=nameWithType> API'ler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="9d76d-391">New <xref:System.Math?displayProperty=nameWithType> APIs include:</span></span>

- <span data-ttu-id="9d76d-392"><xref:System.Math.BitIncrement(System.Double)>Ve<xref:System.Math.BitDecrement(System.Double)></span><span class="sxs-lookup"><span data-stu-id="9d76d-392"><xref:System.Math.BitIncrement(System.Double)> and <xref:System.Math.BitDecrement(System.Double)></span></span>\
<span data-ttu-id="9d76d-393">IEEE `nextDown` ve `nextUp` IEEE işlemlerine karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="9d76d-393">Corresponds to the `nextUp` and `nextDown` IEEE operations.</span></span> <span data-ttu-id="9d76d-394">Girişten (sırasıyla) daha büyük veya daha az olan en küçük kayan nokta numarasını döndürerler.</span><span class="sxs-lookup"><span data-stu-id="9d76d-394">They return the smallest floating-point number that compares greater or lesser than the input (respectively).</span></span> <span data-ttu-id="9d76d-395">Örneğin, `Math.BitIncrement(0.0)` döndürecek. `double.Epsilon`</span><span class="sxs-lookup"><span data-stu-id="9d76d-395">For example, `Math.BitIncrement(0.0)` would return `double.Epsilon`.</span></span>

- <span data-ttu-id="9d76d-396"><xref:System.Math.MaxMagnitude(System.Double,System.Double)>Ve<xref:System.Math.MinMagnitude(System.Double,System.Double)></span><span class="sxs-lookup"><span data-stu-id="9d76d-396"><xref:System.Math.MaxMagnitude(System.Double,System.Double)> and <xref:System.Math.MinMagnitude(System.Double,System.Double)></span></span>\
<span data-ttu-id="9d76d-397">Ve `minNumMag` IEEE `maxNumMag` işlemlerine karşılık gelir, iki girdinin (sırasıyla) büyüklüğü daha büyük veya daha az olan değeri döndürerler.</span><span class="sxs-lookup"><span data-stu-id="9d76d-397">Corresponds to the `maxNumMag` and `minNumMag` IEEE operations, they return the value that is greater or lesser in magnitude of the two inputs (respectively).</span></span> <span data-ttu-id="9d76d-398">Örneğin, `Math.MaxMagnitude(2.0, -3.0)` döndürecek. `-3.0`</span><span class="sxs-lookup"><span data-stu-id="9d76d-398">For example, `Math.MaxMagnitude(2.0, -3.0)` would return `-3.0`.</span></span>

- <xref:System.Math.ILogB(System.Double)>\
<span data-ttu-id="9d76d-399">İntegral `logB` değeri döndüren IEEE işlemine karşılık gelir, giriş parametresinin integral taban-2 log'u verir.</span><span class="sxs-lookup"><span data-stu-id="9d76d-399">Corresponds to the `logB` IEEE operation that returns an integral value, it returns the integral base-2 log of the input parameter.</span></span> <span data-ttu-id="9d76d-400">Bu yöntem, etkili olarak `floor(log2(x))`aynıdır , ancak en az yuvarlama hatası ile yapılır.</span><span class="sxs-lookup"><span data-stu-id="9d76d-400">This method is effectively the same as `floor(log2(x))`, but done with minimal rounding error.</span></span>

- <xref:System.Math.ScaleB(System.Double,System.Int32)>\
<span data-ttu-id="9d76d-401">Ayrılmaz bir `scaleB` değer alan IEEE işlemine karşılık gelir, etkili bir şekilde `x * pow(2, n)`döner, ancak en az yuvarlama hatası ile yapılır.</span><span class="sxs-lookup"><span data-stu-id="9d76d-401">Corresponds to the `scaleB` IEEE operation that takes an integral value, it returns effectively `x * pow(2, n)`, but is done with minimal rounding error.</span></span>

- <xref:System.Math.Log2(System.Double)>\
<span data-ttu-id="9d76d-402">`log2` IEEE işlemine karşılık gelir, baz-2 logaritmasını döndürür.</span><span class="sxs-lookup"><span data-stu-id="9d76d-402">Corresponds to the `log2` IEEE operation, it returns the base-2 logarithm.</span></span> <span data-ttu-id="9d76d-403">Yuvarlama hatalarını en aza indirir.</span><span class="sxs-lookup"><span data-stu-id="9d76d-403">It minimizes rounding error.</span></span>

- <xref:System.Math.FusedMultiplyAdd(System.Double,System.Double,System.Double)>\
<span data-ttu-id="9d76d-404">`fma` IEEE işlemine karşılık gelir, erimiş çarpma ekleme gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="9d76d-404">Corresponds to the `fma` IEEE operation, it performs a fused multiply add.</span></span> <span data-ttu-id="9d76d-405">Diğer bir şey, tek bir işlem olarak, `(x * y) + z` yuvarlama hatasını en aza indirir.</span><span class="sxs-lookup"><span data-stu-id="9d76d-405">That is, it does `(x * y) + z` as a single operation, thereby minimizing the rounding error.</span></span> <span data-ttu-id="9d76d-406">Bir örnek `FusedMultiplyAdd(1e308, 2.0, -1e308)`, `1e308`hangi döner .</span><span class="sxs-lookup"><span data-stu-id="9d76d-406">An example is `FusedMultiplyAdd(1e308, 2.0, -1e308)`, which returns `1e308`.</span></span> <span data-ttu-id="9d76d-407">Düzenli `(1e308 * 2.0) - 1e308` döner `double.PositiveInfinity`.</span><span class="sxs-lookup"><span data-stu-id="9d76d-407">The regular `(1e308 * 2.0) - 1e308` returns `double.PositiveInfinity`.</span></span>

- <xref:System.Math.CopySign(System.Double,System.Double)>\
<span data-ttu-id="9d76d-408">`copySign` IEEE işlemine karşılık gelir, değerini `x`döndürür, ancak `y`işareti ile .</span><span class="sxs-lookup"><span data-stu-id="9d76d-408">Corresponds to the `copySign` IEEE operation, it returns the value of `x`, but with the sign of `y`.</span></span>

### <a name="net-platform-dependent-intrinsics"></a><span data-ttu-id="9d76d-409">.NET Platformuna Bağımlı İçsel</span><span class="sxs-lookup"><span data-stu-id="9d76d-409">.NET Platform-Dependent Intrinsics</span></span>

<span data-ttu-id="9d76d-410">**SIMD** veya **Bit İşleme yönergesi** kümeleri gibi belirli perf odaklı CPU yönergelerine erişime izin veren API'ler eklendi.</span><span class="sxs-lookup"><span data-stu-id="9d76d-410">APIs have been added that allow access to certain perf-oriented CPU instructions, such as the **SIMD** or **Bit Manipulation instruction** sets.</span></span> <span data-ttu-id="9d76d-411">Bu yönergeler, verileri paralel olarak verimli bir şekilde işleme gibi belirli senaryolarda önemli performans iyileştirmeleri elde edilebilebilir.</span><span class="sxs-lookup"><span data-stu-id="9d76d-411">These instructions can help achieve significant performance improvements in certain scenarios, such as processing data efficiently in parallel.</span></span>

<span data-ttu-id="9d76d-412">Uygun olduğu durumlarda, .NET kitaplıkları performansı artırmak için bu yönergeleri kullanmaya başladı.</span><span class="sxs-lookup"><span data-stu-id="9d76d-412">Where appropriate, the .NET libraries have begun using these instructions to improve performance.</span></span>

<span data-ttu-id="9d76d-413">Daha fazla bilgi için [bkz.](https://github.com/dotnet/designs/blob/master/accepted/platform-intrinsics.md)</span><span class="sxs-lookup"><span data-stu-id="9d76d-413">For more information, see [.NET Platform Dependent Intrinsics](https://github.com/dotnet/designs/blob/master/accepted/platform-intrinsics.md).</span></span>

### <a name="improved-net-core-version-apis"></a><span data-ttu-id="9d76d-414">Geliştirilmiş .NET Çekirdek Sürüm API'leri</span><span class="sxs-lookup"><span data-stu-id="9d76d-414">Improved .NET Core Version APIs</span></span>

<span data-ttu-id="9d76d-415">.NET Core 3.0 ile başlayarak,.NET Core ile sağlanan sürüm API'leri artık beklediğiniz bilgileri döndürün.</span><span class="sxs-lookup"><span data-stu-id="9d76d-415">Starting with .NET Core 3.0, the version APIs provided with .NET Core now return the information you expect.</span></span> <span data-ttu-id="9d76d-416">Örnek:</span><span class="sxs-lookup"><span data-stu-id="9d76d-416">For example:</span></span>

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
> <span data-ttu-id="9d76d-417">Değişimi bozuyor.</span><span class="sxs-lookup"><span data-stu-id="9d76d-417">Breaking change.</span></span> <span data-ttu-id="9d76d-418">Sürüm düzeni değiştiğinden, bu teknik olarak bir son landırma değişikliğidir.</span><span class="sxs-lookup"><span data-stu-id="9d76d-418">This is technically a breaking change because the versioning scheme has changed.</span></span>

### <a name="fast-built-in-json-support"></a><span data-ttu-id="9d76d-419">Hızlı dahili JSON desteği</span><span class="sxs-lookup"><span data-stu-id="9d76d-419">Fast built-in JSON support</span></span>

<span data-ttu-id="9d76d-420">.NET kullanıcıları büyük ölçüde [newtonsoft.Json](https://www.newtonsoft.com/json) ve diğer popüler JSON kütüphaneler, iyi seçimler olmaya devam güvendi.</span><span class="sxs-lookup"><span data-stu-id="9d76d-420">.NET users have largely relied on [Newtonsoft.Json](https://www.newtonsoft.com/json) and other popular JSON libraries, which continue to be good choices.</span></span> <span data-ttu-id="9d76d-421">`Newtonsoft.Json`kaputun altındaki UTF-16 olan temel veri türü olarak .NET dizeleri kullanır.</span><span class="sxs-lookup"><span data-stu-id="9d76d-421">`Newtonsoft.Json` uses .NET strings as its base datatype, which is UTF-16 under the hood.</span></span>

<span data-ttu-id="9d76d-422">Yeni yerleşik JSON desteği yüksek performanslı, düşük tahsisat ve UTF-8 kodlanmış JSON metni ile çalışır.</span><span class="sxs-lookup"><span data-stu-id="9d76d-422">The new built-in JSON support is high-performance, low allocation, and works with UTF-8 encoded JSON text.</span></span> <span data-ttu-id="9d76d-423"><xref:System.Text.Json> Ad alanı ve türleri hakkında daha fazla bilgi için aşağıdaki makalelere bakın:</span><span class="sxs-lookup"><span data-stu-id="9d76d-423">For more information about the <xref:System.Text.Json> namespace and types, see the following articles:</span></span>

* [<span data-ttu-id="9d76d-424">.NET'te JSON serileştirme - genel bakış</span><span class="sxs-lookup"><span data-stu-id="9d76d-424">JSON serialization in .NET - overview</span></span>](../../standard/serialization/system-text-json-overview.md)
* <span data-ttu-id="9d76d-425">[JSON'u .NET'te seri hale getirmek ve deserialize etmek için .](../../standard/serialization/system-text-json-how-to.md)</span><span class="sxs-lookup"><span data-stu-id="9d76d-425">[How to serialize and deserialize JSON in .NET](../../standard/serialization/system-text-json-how-to.md).</span></span>
* [<span data-ttu-id="9d76d-426">Newtonsoft.Json'dan System.Text.Json'a nasıl göç edilir?</span><span class="sxs-lookup"><span data-stu-id="9d76d-426">How to migrate from Newtonsoft.Json to System.Text.Json</span></span>](../../standard/serialization/system-text-json-migrate-from-newtonsoft-how-to.md)

### <a name="http2-support"></a><span data-ttu-id="9d76d-427">HTTP/2 desteği</span><span class="sxs-lookup"><span data-stu-id="9d76d-427">HTTP/2 support</span></span>

<span data-ttu-id="9d76d-428">Tür <xref:System.Net.Http.HttpClient?displayProperty=nameWithType> HTTP/2 protokolünü destekler.</span><span class="sxs-lookup"><span data-stu-id="9d76d-428">The <xref:System.Net.Http.HttpClient?displayProperty=nameWithType> type supports the HTTP/2 protocol.</span></span> <span data-ttu-id="9d76d-429">HTTP/2 etkinse, HTTP protokol sürümü TLS/ALPN üzerinden görüşülür ve sunucu kullanmayı seçerse HTTP/2 kullanılır.</span><span class="sxs-lookup"><span data-stu-id="9d76d-429">If HTTP/2 is enabled, the HTTP protocol version is negotiated via TLS/ALPN, and HTTP/2 is used if the server elects to use it.</span></span>

<span data-ttu-id="9d76d-430">Varsayılan protokol HTTP/1.1 olarak kalır, ancak HTTP/2 iki farklı şekilde etkinleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="9d76d-430">The default protocol remains HTTP/1.1, but HTTP/2 can be enabled in two different ways.</span></span> <span data-ttu-id="9d76d-431">İlk olarak, HTTP/2'yi kullanacak şekilde HTTP istek iletisini ayarlayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="9d76d-431">First, you can set the HTTP request message to use HTTP/2:</span></span>

[!code-csharp[Http2Request](~/samples/snippets/core/whats-new/whats-new-in-30/cs/http.cs#Request)]

<span data-ttu-id="9d76d-432">İkinci olarak, <xref:System.Net.Http.HttpClient> varsayılan olarak HTTP/2'yi kullanmak üzere değiştirebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="9d76d-432">Second, you can change <xref:System.Net.Http.HttpClient> to use HTTP/2 by default:</span></span>

[!code-csharp[Http2Client](~/samples/snippets/core/whats-new/whats-new-in-30/cs/http.cs#Client)]

<span data-ttu-id="9d76d-433">Çoğu zaman bir uygulama geliştirirken, şifrelenmemiş bir bağlantı kullanmak istersiniz.</span><span class="sxs-lookup"><span data-stu-id="9d76d-433">Many times when you're developing an application, you want to use an unencrypted connection.</span></span> <span data-ttu-id="9d76d-434">Hedef uç noktanın HTTP/2'yi kullandığını biliyorsanız, HTTP/2 için şifrelenmemiş bağlantıları açabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9d76d-434">If you know the target endpoint will be using HTTP/2, you can turn on unencrypted connections for HTTP/2.</span></span> <span data-ttu-id="9d76d-435">Ortam değişkenini `DOTNET_SYSTEM_NET_HTTP_SOCKETSHTTPHANDLER_HTTP2UNENCRYPTEDSUPPORT` ayarlayarak `1` veya uygulama bağlamında etkinleştirerek açabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="9d76d-435">You can turn it on by setting the `DOTNET_SYSTEM_NET_HTTP_SOCKETSHTTPHANDLER_HTTP2UNENCRYPTEDSUPPORT` environment variable to `1` or by enabling it in the app context:</span></span>

[!code-csharp[Http2Context](~/samples/snippets/core/whats-new/whats-new-in-30/cs/http.cs#AppContext)]

## <a name="next-steps"></a><span data-ttu-id="9d76d-436">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="9d76d-436">Next steps</span></span>

- [<span data-ttu-id="9d76d-437">.NET Core 2.2 ve 3.0 arasındaki kesme değişikliklerini gözden geçirin.</span><span class="sxs-lookup"><span data-stu-id="9d76d-437">Review the breaking changes between .NET Core 2.2 and 3.0.</span></span>](../compatibility/2.2-3.0.md)
- [<span data-ttu-id="9d76d-438">Windows Forms uygulamaları için .NET Core 3.0'daki son dakika değişikliklerini gözden geçirin.</span><span class="sxs-lookup"><span data-stu-id="9d76d-438">Review the breaking changes in .NET Core 3.0 for Windows Forms apps.</span></span>](../compatibility/winforms.md#net-core-30)
