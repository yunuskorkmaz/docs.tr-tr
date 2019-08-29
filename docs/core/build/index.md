---
title: Kaynaktan .NET Core derleme
description: Kaynak koddan .NET Core ve .NET Core CLI oluşturmayı öğrenin.
author: bleroy
ms.date: 06/28/2017
ms.custom: seodec18
ms.openlocfilehash: dcd7c909325eec5a79db74098d7ac880000eafa1
ms.sourcegitcommit: 6f28b709592503d27077b16fff2e2eacca569992
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/28/2019
ms.locfileid: "70105394"
---
# <a name="build-net-core-from-source"></a><span data-ttu-id="b83c7-103">Kaynaktan .NET Core derleme</span><span class="sxs-lookup"><span data-stu-id="b83c7-103">Build .NET Core from source</span></span>

<span data-ttu-id="b83c7-104">Kaynak kodundan .NET Core oluşturma özelliği, birden çok şekilde önemlidir: .NET Core 'u yeni platformlar için bağlantı noktasını daha kolay hale getirir, ürüne katkı ve düzeltmeler sağlar ve .NET 'in özel sürümlerinin oluşturulmasına olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="b83c7-104">The ability to build .NET Core from its source code is important in multiple ways: it makes it easier to port .NET Core to new platforms, it enables contributions and fixes to the product, and it enables the creation of custom versions of .NET.</span></span>
<span data-ttu-id="b83c7-105">Bu makale, kendi .NET Core sürümlerini derlemek ve dağıtmak isteyen geliştiricilere kılavuzluk sağlar.</span><span class="sxs-lookup"><span data-stu-id="b83c7-105">This article gives guidance to developers who want to build and distribute their own versions of .NET Core.</span></span>

## <a name="build-the-clr-from-source"></a><span data-ttu-id="b83c7-106">Kaynaktan CLR oluşturma</span><span class="sxs-lookup"><span data-stu-id="b83c7-106">Build the CLR from source</span></span>

<span data-ttu-id="b83c7-107">.NET CoreCLR 'ın kaynak kodu GitHub 'daki [DotNet/CoreCLR](https://github.com/dotnet/coreclr/) deposunda bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="b83c7-107">The source code for the .NET CoreCLR can be found in the [dotnet/coreclr](https://github.com/dotnet/coreclr/) repository on GitHub.</span></span>

<span data-ttu-id="b83c7-108">Yapı şu anda aşağıdaki önkoşullara bağımlıdır:</span><span class="sxs-lookup"><span data-stu-id="b83c7-108">The build currently depends on the following prerequisites:</span></span>

- [<span data-ttu-id="b83c7-109">Git</span><span class="sxs-lookup"><span data-stu-id="b83c7-109">Git</span></span>](https://git-scm.com/)
- [<span data-ttu-id="b83c7-110">CMake</span><span class="sxs-lookup"><span data-stu-id="b83c7-110">CMake</span></span>](https://cmake.org/)
- [<span data-ttu-id="b83c7-111">Python</span><span class="sxs-lookup"><span data-stu-id="b83c7-111">Python</span></span>](https://www.python.org/)
- <span data-ttu-id="b83c7-112">C++ derleyici.</span><span class="sxs-lookup"><span data-stu-id="b83c7-112">a C++ compiler.</span></span>

<span data-ttu-id="b83c7-113">Bu önkoşulları yükledikten sonra,`build.cmd` [DotNet/CoreCLR](https://github.com/dotnet/coreclr/) deposunun tabanında derleme betiğini (Windows veya `build.sh` Linux ve MacOS 'ta) çağırarak clr 'yi oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b83c7-113">After you've installed these prerequisites, you can build the CLR by invoking the build script (`build.cmd` on Windows, or `build.sh` on Linux and macOS) at the base of the [dotnet/coreclr](https://github.com/dotnet/coreclr/) repository.</span></span>

<span data-ttu-id="b83c7-114">Bileşenleri yüklemek, işletim sistemine (OS) göre farklılık gösterir.</span><span class="sxs-lookup"><span data-stu-id="b83c7-114">Installing the components differ depending on the operating system (OS).</span></span> <span data-ttu-id="b83c7-115">Belirli işletim sistemi için derleme yönergelerine bakın:</span><span class="sxs-lookup"><span data-stu-id="b83c7-115">See the build instructions for your specific OS:</span></span>

- [<span data-ttu-id="b83c7-116">Windows</span><span class="sxs-lookup"><span data-stu-id="b83c7-116">Windows</span></span>](https://github.com/dotnet/coreclr/blob/master/Documentation/building/windows-instructions.md)
- [<span data-ttu-id="b83c7-117">Linux</span><span class="sxs-lookup"><span data-stu-id="b83c7-117">Linux</span></span>](https://github.com/dotnet/coreclr/blob/master/Documentation/building/linux-instructions.md)
- [<span data-ttu-id="b83c7-118">macOS</span><span class="sxs-lookup"><span data-stu-id="b83c7-118">macOS</span></span>](https://github.com/dotnet/coreclr/blob/master/Documentation/building/osx-instructions.md)
- [<span data-ttu-id="b83c7-119">FreeBSD</span><span class="sxs-lookup"><span data-stu-id="b83c7-119">FreeBSD</span></span>](https://github.com/dotnet/coreclr/blob/master/Documentation/building/freebsd-instructions.md)
- [<span data-ttu-id="b83c7-120">NetBSD</span><span class="sxs-lookup"><span data-stu-id="b83c7-120">NetBSD</span></span>](https://github.com/dotnet/coreclr/blob/master/Documentation/building/netbsd-instructions.md)

<span data-ttu-id="b83c7-121">İşletim sistemi genelinde çapraz oluşturma yoktur (yalnızca x64 üzerinde oluşturulan ARM için).</span><span class="sxs-lookup"><span data-stu-id="b83c7-121">There is no cross-building across OS (only for ARM, which is built on X64).</span></span>  
<span data-ttu-id="b83c7-122">Bu platformu oluşturmak için belirli bir platformda olmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="b83c7-122">You have to be on the particular platform to build that platform.</span></span>  

<span data-ttu-id="b83c7-123">Derleme iki ana `buildTypes`öğesine sahiptir:</span><span class="sxs-lookup"><span data-stu-id="b83c7-123">The build has two main `buildTypes`:</span></span>

- <span data-ttu-id="b83c7-124">Hata ayıklama (varsayılan)-çalışma zamanını en az iyileştirmeler ve ek çalışma zamanı denetimleri (onaylar) ile derler.</span><span class="sxs-lookup"><span data-stu-id="b83c7-124">Debug (default)- Compiles the runtime with minimal optimizations and additional runtime checks (asserts).</span></span> <span data-ttu-id="b83c7-125">En iyi duruma getirme düzeyi ve ek denetimler, çalışma zamanı yürütmesinin yavaşlamasına karşın hata ayıklama için değerlidir.</span><span class="sxs-lookup"><span data-stu-id="b83c7-125">This reduction in optimization level and the additional checks slow runtime execution but are valuable for debugging.</span></span> <span data-ttu-id="b83c7-126">Bu, geliştirme ve test ortamları için önerilen ayardır.</span><span class="sxs-lookup"><span data-stu-id="b83c7-126">This is the recommended setting for development and testing environments.</span></span>
- <span data-ttu-id="b83c7-127">Release-çalışma zamanını, ek çalışma zamanı denetimleri olmadan tam iyileştirmelere göre derler.</span><span class="sxs-lookup"><span data-stu-id="b83c7-127">Release - Compiles the runtime with full optimizations and without the additional runtime checks.</span></span> <span data-ttu-id="b83c7-128">Bu çok daha hızlı çalışma süresi performansına sahiptir, ancak oluşturulması biraz daha uzun sürebilir ve hata ayıklaması zor olabilir.</span><span class="sxs-lookup"><span data-stu-id="b83c7-128">This will yield much faster run time performance but it can take a bit longer to build and can be difficult to debug.</span></span> <span data-ttu-id="b83c7-129">Bu `release` derleme türünü seçmek için derleme betiğine iletin.</span><span class="sxs-lookup"><span data-stu-id="b83c7-129">Pass `release` to the build script to select this build type.</span></span>

<span data-ttu-id="b83c7-130">Buna ek olarak, yapı varsayılan olarak yalnızca çalışma zamanı yürütülebilir dosyalarını oluşturur, ancak tüm testleri de oluşturur.</span><span class="sxs-lookup"><span data-stu-id="b83c7-130">In addition, by default the build not only creates the runtime executables, but it also builds all the tests.</span></span>
<span data-ttu-id="b83c7-131">Az sayıda test vardır ve yalnızca değişikliklerle denemeler yapmak istiyorsanız gerekli olmayan önemli miktarda zaman elde edersiniz.</span><span class="sxs-lookup"><span data-stu-id="b83c7-131">There are quite a few tests, taking a significant amount of time that isn't necessary if you just want to experiment with changes.</span></span>
<span data-ttu-id="b83c7-132">Aşağıdaki örnekte olduğu gibi derleme betiğine `skiptests` bağımsız değişkeni ekleyerek test yapılarını atlayabilirsiniz (UNIX makinelerinde ile `./build.sh` değiştirin `.\build` ):</span><span class="sxs-lookup"><span data-stu-id="b83c7-132">You can skip the tests builds by adding the `skiptests` argument to the build script, like in the following example (replace `.\build` with `./build.sh` on Unix machines):</span></span>

```bat
    .\build skiptests
```

<span data-ttu-id="b83c7-133">Önceki örnekte, geliştirme zamanı denetimleri (onaylar `Debug` ) etkin ve iyileştirmeler devre dışı olan Flavor 'nin nasıl oluşturulacağı gösterildi.</span><span class="sxs-lookup"><span data-stu-id="b83c7-133">The previous example showed how to build the `Debug` flavor, which has development time checks (asserts) enabled and optimizations disabled.</span></span> <span data-ttu-id="b83c7-134">Yayın (tam hız) türü oluşturmak için aşağıdakileri yapın:</span><span class="sxs-lookup"><span data-stu-id="b83c7-134">To build the release (full speed) flavor, do the following:</span></span>

```bat
    .\build release skiptests
```

<span data-ttu-id="b83c7-135">-? Kullanarak derleme ile daha fazla derleme seçeneği bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b83c7-135">You can find more build options with build by using the -?</span></span> <span data-ttu-id="b83c7-136">veya-help niteleyicisi.</span><span class="sxs-lookup"><span data-stu-id="b83c7-136">or -help qualifier.</span></span>

### <a name="using-your-build"></a><span data-ttu-id="b83c7-137">Yapınızı kullanma</span><span class="sxs-lookup"><span data-stu-id="b83c7-137">Using Your Build</span></span>

<span data-ttu-id="b83c7-138">Yapı, oluşturulan tüm dosyalarını deponun tabanında `bin` dizin altında koyar.</span><span class="sxs-lookup"><span data-stu-id="b83c7-138">The build places all of its generated files under the `bin` directory at the base of the repository.</span></span>
<span data-ttu-id="b83c7-139">Derleme sırasında oluşturulan günlük dosyalarını içeren bir *bin\log* dizini vardır (en çok derleme başarısız olduğunda yararlıdır).</span><span class="sxs-lookup"><span data-stu-id="b83c7-139">There is a *bin\Log* directory that contains log files generated during the build (Most useful when the build fails).</span></span>
<span data-ttu-id="b83c7-140">Gerçek çıktı bir *bin\product\[platformuna yerleştirildi]. [ CPU mimarisi]. [derleme türü]* Dizin, örneğin *bin\Product\Windows_NT.x64.Release*.</span><span class="sxs-lookup"><span data-stu-id="b83c7-140">The actual output is placed in a *bin\Product\[platform].[CPU architecture].[build type]* directory, such as *bin\Product\Windows_NT.x64.Release*.</span></span>

<span data-ttu-id="b83c7-141">Derleme ' Ham ' çıkışı bazen yararlı olsa da, normalde yalnızca önceki çıkış dizininin `.nuget\pkg` alt dizinine yerleştirilmiş olan NuGet paketlerini ilgileniyorsunuz.</span><span class="sxs-lookup"><span data-stu-id="b83c7-141">While the 'raw' output of the build is sometimes useful, normally you're only interested in the NuGet packages, which are placed in the `.nuget\pkg` subdirectory of the previous output directory.</span></span>

<span data-ttu-id="b83c7-142">Yeni çalışma zamanını kullanmanın iki temel tekniği vardır:</span><span class="sxs-lookup"><span data-stu-id="b83c7-142">There are two basic techniques for using your new runtime:</span></span>

 1. <span data-ttu-id="b83c7-143">**Bir uygulama oluşturmak için DotNet. exe ve NuGet kullanın**.</span><span class="sxs-lookup"><span data-stu-id="b83c7-143">**Use dotnet.exe and NuGet to compose an application**.</span></span>
    <span data-ttu-id="b83c7-144">Yeni oluşturduğunuz NuGet paketlerini ve ' DotNet ' komut satırı arabirimini (CLı) kullanarak yeni çalışma zamanı kullanan bir program oluşturma yönergeleri için [yapınızı kullanma](https://github.com/dotnet/coreclr/blob/master/Documentation/workflow/UsingYourBuild.md) konusuna bakın.</span><span class="sxs-lookup"><span data-stu-id="b83c7-144">See [Using Your Build](https://github.com/dotnet/coreclr/blob/master/Documentation/workflow/UsingYourBuild.md) for instructions on creating a program that uses your new runtime by using the NuGet packages you just created and the 'dotnet' command-line interface (CLI).</span></span> <span data-ttu-id="b83c7-145">Bu teknik, çalışma zamanı olmayan geliştiricilerin yeni çalışma zamanını tüketmesi olasılığını tahmin eden bir yöntemdir.</span><span class="sxs-lookup"><span data-stu-id="b83c7-145">This technique is the expected way non-runtime developers are likely to consume your new runtime.</span></span>

 2. <span data-ttu-id="b83c7-146">**Paket olmayan dll 'leri kullanarak bir uygulamayı çalıştırmak için corerun. exe**' yi kullanın.</span><span class="sxs-lookup"><span data-stu-id="b83c7-146">**Use corerun.exe to run an application using unpackaged DLLs**.</span></span>
    <span data-ttu-id="b83c7-147">Bu depo Ayrıca, NuGet üzerinde hiçbir bağımlılığı olmayan corerun. exe adlı basit bir ana bilgisayarı tanımlar.</span><span class="sxs-lookup"><span data-stu-id="b83c7-147">This repository also defines a simple host called corerun.exe that does NOT take any dependency on NuGet.</span></span>
    <span data-ttu-id="b83c7-148">Ana bilgisayara gerçekten kullandığınız gerekli dll 'Leri nereden alınacağını ve bunları birlikte el ile toplamanız gerektiğini söylemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="b83c7-148">You need to tell the host where to get the required DLLs you actually use, and you have to manually gather them together.</span></span>
    <span data-ttu-id="b83c7-149">Bu teknik, [DotNet/CoreCLR](https://github.com/dotnet/coreclr) deposunda bulunan tüm testler tarafından kullanılır ve hızlı yerel ' düzenleme-derleme-hata ayıklama ' döngüsü için, ön birim testi gibi yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="b83c7-149">This technique is used by all the tests in the [dotnet/coreclr](https://github.com/dotnet/coreclr) repo, and is useful for quick local 'edit-compile-debug' loop such as preliminary unit testing.</span></span>
    <span data-ttu-id="b83c7-150">Bu tekniği kullanma hakkında ayrıntılı bilgi için bkz. [CoreRun. exe ile .NET Core uygulamaları yürütme](https://github.com/dotnet/coreclr/blob/master/Documentation/workflow/UsingCoreRun.md) .</span><span class="sxs-lookup"><span data-stu-id="b83c7-150">See [Executing .NET Core Apps with CoreRun.exe](https://github.com/dotnet/coreclr/blob/master/Documentation/workflow/UsingCoreRun.md) for details on using this technique.</span></span>

## <a name="build-the-cli-from-source"></a><span data-ttu-id="b83c7-151">Kaynaktan CLı oluştur</span><span class="sxs-lookup"><span data-stu-id="b83c7-151">Build the CLI from source</span></span>

<span data-ttu-id="b83c7-152">.NET Core CLI kaynak kodu GitHub 'daki [DotNet/CLI](https://github.com/dotnet/cli/) deposunda bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="b83c7-152">The source code for the .NET Core CLI can be found in the [dotnet/cli](https://github.com/dotnet/cli/) repository on GitHub.</span></span>

<span data-ttu-id="b83c7-153">.NET Core CLI derlemek için makinenizde aşağıdakilerin yüklü olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="b83c7-153">In order to build the .NET Core CLI, you need the following installed on your machine.</span></span>

- <span data-ttu-id="b83c7-154">Windows & Linux:</span><span class="sxs-lookup"><span data-stu-id="b83c7-154">Windows & Linux:</span></span>
  - <span data-ttu-id="b83c7-155">YOLDAKI git</span><span class="sxs-lookup"><span data-stu-id="b83c7-155">git on the PATH</span></span>
- <span data-ttu-id="b83c7-156">MacOS</span><span class="sxs-lookup"><span data-stu-id="b83c7-156">macOS:</span></span>
  - <span data-ttu-id="b83c7-157">YOLDAKI git</span><span class="sxs-lookup"><span data-stu-id="b83c7-157">git on the PATH</span></span>
  - <span data-ttu-id="b83c7-158">Xcode</span><span class="sxs-lookup"><span data-stu-id="b83c7-158">Xcode</span></span>
  - <span data-ttu-id="b83c7-159">Openssl</span><span class="sxs-lookup"><span data-stu-id="b83c7-159">OpenSSL</span></span>

<span data-ttu-id="b83c7-160">Kök veya `build.cmd` `build.sh` Linux ve MacOS üzerinde derlemek, çalıştırmak için.</span><span class="sxs-lookup"><span data-stu-id="b83c7-160">In order to build, run `build.cmd` on Windows, or `build.sh` on Linux and macOS from the root.</span></span> <span data-ttu-id="b83c7-161">Testleri yürütmek istemiyorsanız, veya `build.cmd -t:Compile` `./build.sh -t:Compile`çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="b83c7-161">If you don't want to execute tests, run `build.cmd -t:Compile` or `./build.sh -t:Compile`.</span></span> <span data-ttu-id="b83c7-162">MacOS Sierra CLı 'yi oluşturmak için, DOTNET_RUNTIME_ID ortam değişkenini çalıştırarak `export DOTNET_RUNTIME_ID=osx.10.11-x64`ayarlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="b83c7-162">To build the CLI in macOS Sierra, you need to set the DOTNET_RUNTIME_ID environment variable by running `export DOTNET_RUNTIME_ID=osx.10.11-x64`.</span></span>

### <a name="using-your-build"></a><span data-ttu-id="b83c7-163">Yapınızı kullanma</span><span class="sxs-lookup"><span data-stu-id="b83c7-163">Using your build</span></span>

<span data-ttu-id="b83c7-164">Yeni oluşturulan CLI 'yı denemek için *yapıtlar/{OS}-{Arch}/STAGE2* içindeki yürütülebilirdosyayıkullanın.`dotnet`</span><span class="sxs-lookup"><span data-stu-id="b83c7-164">Use the `dotnet` executable from *artifacts/{os}-{arch}/stage2* to try out the newly built CLI.</span></span> <span data-ttu-id="b83c7-165">Yapı çıkışını geçerli konsolundan çağırırken `dotnet` kullanmak istiyorsanız, yolu */{OS}-{Arch}/STAGE2* da yola ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b83c7-165">If you want to use the build output when invoking `dotnet` from the current console, you can also add *artifacts/{os}-{arch}/stage2* to the PATH.</span></span>

## <a name="see-also"></a><span data-ttu-id="b83c7-166">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b83c7-166">See also</span></span>

- [<span data-ttu-id="b83c7-167">.NET Core ortak dil çalışma zamanı (CoreCLR)</span><span class="sxs-lookup"><span data-stu-id="b83c7-167">.NET Core Common Language Runtime (CoreCLR)</span></span>](https://github.com/dotnet/coreclr/blob/master/README.md)
- [<span data-ttu-id="b83c7-168">.NET Core CLI geliştirici kılavuzu</span><span class="sxs-lookup"><span data-stu-id="b83c7-168">.NET Core CLI Developer Guide</span></span>](https://github.com/dotnet/cli/blob/master/Documentation/project-docs/developer-guide.md)
- [<span data-ttu-id="b83c7-169">.NET Core dağıtımı paketleme</span><span class="sxs-lookup"><span data-stu-id="b83c7-169">.NET Core distribution packaging</span></span>](./distribution-packaging.md)
