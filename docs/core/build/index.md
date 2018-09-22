---
title: Kaynaktan .NET Core derleme
description: .NET Core ve .NET Core CLI kaynak kodundan oluşturmayı öğrenin.
author: bleroy
ms.author: mairaw
ms.date: 06/28/2017
ms.openlocfilehash: fa9c193ea4088f04745bdadc6040552e18c0858a
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2018
ms.locfileid: "46577509"
---
# <a name="build-net-core-from-source"></a><span data-ttu-id="74720-103">Kaynaktan .NET Core derleme</span><span class="sxs-lookup"><span data-stu-id="74720-103">Build .NET Core from source</span></span>

<span data-ttu-id="74720-104">.NET Core, kaynak koddan oluşturma imkanı birden çok yolla önemlidir: .NET Core numaralı bağlantı noktasına yeni platformlara kolaylaştırır, katkı sağlar ve düzeltmeleri ürüne ve .NET özel sürümlerini oluşturulmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="74720-104">The ability to build .NET Core from its source code is important in multiple ways: it makes it easier to port .NET Core to new platforms, it enables contributions and fixes to the product, and it enables the creation of custom versions of .NET.</span></span>
<span data-ttu-id="74720-105">Bu makalede, derleme ve kendi .NET Core sürümlerini dağıtmak isteyen geliştiriciler için konusunda rehberlik sağlar.</span><span class="sxs-lookup"><span data-stu-id="74720-105">This article gives guidance to developers who want to build and distribute their own versions of .NET Core.</span></span>

## <a name="build-the-clr-from-source"></a><span data-ttu-id="74720-106">CLR kaynağından alınan derleme</span><span class="sxs-lookup"><span data-stu-id="74720-106">Build the CLR from source</span></span>

<span data-ttu-id="74720-107">.NET CoreCLR için kaynak kodu bulunabilir [dotnet/coreclr](https://github.com/dotnet/coreclr/) github deposu.</span><span class="sxs-lookup"><span data-stu-id="74720-107">The source code for the .NET CoreCLR can be found in the [dotnet/coreclr](https://github.com/dotnet/coreclr/) repository on GitHub.</span></span>

<span data-ttu-id="74720-108">Derleme şu anda üzerinde aşağıdaki ön koşullara bağlıdır:</span><span class="sxs-lookup"><span data-stu-id="74720-108">The build currently depends on the following prerequisites:</span></span>

* [<span data-ttu-id="74720-109">Git</span><span class="sxs-lookup"><span data-stu-id="74720-109">Git</span></span>](https://git-scm.com/)
* [<span data-ttu-id="74720-110">CMake</span><span class="sxs-lookup"><span data-stu-id="74720-110">CMake</span></span>](https://cmake.org/)
* [<span data-ttu-id="74720-111">Python</span><span class="sxs-lookup"><span data-stu-id="74720-111">Python</span></span>](https://www.python.org/)
* <span data-ttu-id="74720-112">bir C++ derleyicisi.</span><span class="sxs-lookup"><span data-stu-id="74720-112">a C++ compiler.</span></span>

<span data-ttu-id="74720-113">Bu Önkoşullar yükledikten sonra derleme betiğinin çağırarak CLR oluşturabilirsiniz (`build.cmd` Windows, şirket veya `build.sh` Linux ve macOS) temel [dotnet/coreclr](https://github.com/dotnet/coreclr/) depo.</span><span class="sxs-lookup"><span data-stu-id="74720-113">After you've installed these prerequisites, you can build the CLR by invoking the build script (`build.cmd` on Windows, or `build.sh` on Linux and macOS) at the base of the [dotnet/coreclr](https://github.com/dotnet/coreclr/) repository.</span></span>

<span data-ttu-id="74720-114">İşletim sistemi (OS) bağlı olarak farklı bileşenler yükleniyor.</span><span class="sxs-lookup"><span data-stu-id="74720-114">Installing the components differ depending on the operating system (OS).</span></span> <span data-ttu-id="74720-115">Belirli işletim sisteminiz için derleme yönergelere bakın:</span><span class="sxs-lookup"><span data-stu-id="74720-115">See the build instructions for your specific OS:</span></span>

* [<span data-ttu-id="74720-116">Windows</span><span class="sxs-lookup"><span data-stu-id="74720-116">Windows</span></span>](https://github.com/dotnet/coreclr/blob/master/Documentation/building/windows-instructions.md)
* [<span data-ttu-id="74720-117">Linux</span><span class="sxs-lookup"><span data-stu-id="74720-117">Linux</span></span>](https://github.com/dotnet/coreclr/blob/master/Documentation/building/linux-instructions.md)
* [<span data-ttu-id="74720-118">macOS</span><span class="sxs-lookup"><span data-stu-id="74720-118">macOS</span></span>](https://github.com/dotnet/coreclr/blob/master/Documentation/building/osx-instructions.md)
* [<span data-ttu-id="74720-119">FreeBSD</span><span class="sxs-lookup"><span data-stu-id="74720-119">FreeBSD</span></span>](https://github.com/dotnet/coreclr/blob/master/Documentation/building/freebsd-instructions.md)
* [<span data-ttu-id="74720-120">NetBSD</span><span class="sxs-lookup"><span data-stu-id="74720-120">NetBSD</span></span>](https://github.com/dotnet/coreclr/blob/master/Documentation/building/netbsd-instructions.md)

<span data-ttu-id="74720-121">İşletim sistemi (için X64 üzerinde yerleşik yalnızca ARM,) arasında çapraz derleme yok.</span><span class="sxs-lookup"><span data-stu-id="74720-121">There is no cross-building across OS (only for ARM, which is built on X64).</span></span>  
<span data-ttu-id="74720-122">Bu platformu oluşturmak için belirli platform olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="74720-122">You have to be on the particular platform to build that platform.</span></span>  

<span data-ttu-id="74720-123">İki ana derleme sahip `buildTypes`:</span><span class="sxs-lookup"><span data-stu-id="74720-123">The build has two main `buildTypes`:</span></span>

* <span data-ttu-id="74720-124">Hata ayıklama (varsayılan) - en az iyileştirmeleri ve ek çalışma zamanı denetimleri ile çalışma zamanı derleme (bildirimler).</span><span class="sxs-lookup"><span data-stu-id="74720-124">Debug (default)- Compiles the runtime with minimal optimizations and additional runtime checks (asserts).</span></span> <span data-ttu-id="74720-125">Bu iyileştirme düzeyini düşüş ve ek denetimler çalışma zamanı yürütme yavaş ancak hata ayıklama için değerlidir.</span><span class="sxs-lookup"><span data-stu-id="74720-125">This reduction in optimization level and the additional checks slow runtime execution but are valuable for debugging.</span></span> <span data-ttu-id="74720-126">Geliştirme ve test ortamları için Önerilen ayar budur.</span><span class="sxs-lookup"><span data-stu-id="74720-126">This is the recommended setting for development and testing environments.</span></span>
* <span data-ttu-id="74720-127">Yayın - çalışma zamanı tam iyileştirmeler ve ek çalışma zamanı denetimleri olmadan derler.</span><span class="sxs-lookup"><span data-stu-id="74720-127">Release - Compiles the runtime with full optimizations and without the additional runtime checks.</span></span> <span data-ttu-id="74720-128">Bu çok daha hızlı çalıştırma performans verir ancak oluşturmak biraz uzun sürebilir ve hata ayıklaması zor olabilir.</span><span class="sxs-lookup"><span data-stu-id="74720-128">This will yield much faster run time performance but it can take a bit longer to build and can be difficult to debug.</span></span> <span data-ttu-id="74720-129">Geçirmek `release` yapı betiği bunu seçmek için yapı türü.</span><span class="sxs-lookup"><span data-stu-id="74720-129">Pass `release` to the build script to select this build type.</span></span>

<span data-ttu-id="74720-130">Ayrıca, varsayılan yapı yalnızca çalışma zamanı yürütülebilir dosyalar oluşturur, ancak ayrıca tüm testleri oluşturur.</span><span class="sxs-lookup"><span data-stu-id="74720-130">In addition, by default the build not only creates the runtime executables, but it also builds all the tests.</span></span>
<span data-ttu-id="74720-131">Videonuz testleri, önemli miktarda değişikliklerle denemek istiyorsanız, gerekli olmayan zaman ayırdığınız vardır.</span><span class="sxs-lookup"><span data-stu-id="74720-131">There are quite a few tests, taking a significant amount of time that isn't necessary if you just want to experiment with changes.</span></span>
<span data-ttu-id="74720-132">Ekleyerek, test derlemeleri atlayabilirsiniz `skiptests` yapı komut dosyası bağımsız değişkeni aşağıdaki örnekte ister (Değiştir `.\build` ile `./build.sh` Unix makinelerinde):</span><span class="sxs-lookup"><span data-stu-id="74720-132">You can skip the tests builds by adding the `skiptests` argument to the build script, like in the following example (replace `.\build` with `./build.sh` on Unix machines):</span></span>

```bat
    .\build skiptests
```

<span data-ttu-id="74720-133">Önceki örnekte gösterilen nasıl oluşturulacağını `Debug` geliştirme zamanı denetimleri olan bir özellik (onaylar) etkin ve iyileştirmeleri devre dışı.</span><span class="sxs-lookup"><span data-stu-id="74720-133">The previous example showed how to build the `Debug` flavor, which has development time checks (asserts) enabled and optimizations disabled.</span></span> <span data-ttu-id="74720-134">Derleme sürümü (tam hız) türü için aşağıdakileri yapın:</span><span class="sxs-lookup"><span data-stu-id="74720-134">To build the release (full speed) flavor, do the following:</span></span>

```bat
    .\build release skiptests
```

<span data-ttu-id="74720-135">Daha fazla yapı seçeneklerini derleme ile kullanarak bulabilirsiniz?</span><span class="sxs-lookup"><span data-stu-id="74720-135">You can find more build options with build by using the -?</span></span> <span data-ttu-id="74720-136">ya da-niteleyicisi yardımcı olun.</span><span class="sxs-lookup"><span data-stu-id="74720-136">or -help qualifier.</span></span>

### <a name="using-your-build"></a><span data-ttu-id="74720-137">Yapınızı kullanma</span><span class="sxs-lookup"><span data-stu-id="74720-137">Using Your Build</span></span>

<span data-ttu-id="74720-138">Altında oluşturulan dosyalarının tüm yapı yerleştirir `bin` deponun temel dizin.</span><span class="sxs-lookup"><span data-stu-id="74720-138">The build places all of its generated files under the `bin` directory at the base of the repository.</span></span>
<span data-ttu-id="74720-139">Var olan bir *bin\Log* (en derleme başarısız olduğunda yararlıdır) derleme sırasında oluşturulan günlük dosyalarını içeren dizin.</span><span class="sxs-lookup"><span data-stu-id="74720-139">There is a *bin\Log* directory that contains log files generated during the build (Most useful when the build fails).</span></span>
<span data-ttu-id="74720-140">Gerçek çıkış yerleştirilen bir *bin\Product\[platform]. [ CPU mimarisi]. [türü build]*  gibi dizin *bin\Product\Windows_NT.x64.Release*.</span><span class="sxs-lookup"><span data-stu-id="74720-140">The actual output is placed in a *bin\Product\[platform].[CPU architecture].[build type]* directory, such as *bin\Product\Windows_NT.x64.Release*.</span></span>

<span data-ttu-id="74720-141">Derleme 'raw' çıkışı bazen yararlı olsa da, normalde yalnızca yerleştirilir NuGet paketlerini ilgilendiğiniz `.nuget\pkg` önceki çıktı dizininin alt.</span><span class="sxs-lookup"><span data-stu-id="74720-141">While the 'raw' output of the build is sometimes useful, normally you're only interested in the NuGet packages, which are placed in the `.nuget\pkg` subdirectory of the previous output directory.</span></span>

<span data-ttu-id="74720-142">Yeni, çalışma zamanı kullanmak için iki temel teknik vardır:</span><span class="sxs-lookup"><span data-stu-id="74720-142">There are two basic techniques for using your new runtime:</span></span>

 1. <span data-ttu-id="74720-143">**Bir uygulama oluşturmak için dotnet.exe ve NuGet kullanma**.</span><span class="sxs-lookup"><span data-stu-id="74720-143">**Use dotnet.exe and NuGet to compose an application**.</span></span>
    <span data-ttu-id="74720-144">Bkz: [kullanarak yapı](https://github.com/dotnet/coreclr/blob/master/Documentation/workflow/UsingYourBuild.md) kullanarak, yeni bir çalışma zamanı kullanan bir program oluşturma yönergeleri için NuGet oluşturdunuz ve 'dotnet' komut satırı arabirimi (CLI) paketleri.</span><span class="sxs-lookup"><span data-stu-id="74720-144">See [Using Your Build](https://github.com/dotnet/coreclr/blob/master/Documentation/workflow/UsingYourBuild.md) for instructions on creating a program that uses your new runtime by using the NuGet packages you just created and the 'dotnet' command-line interface (CLI).</span></span> <span data-ttu-id="74720-145">Bu, yeni bir çalışma zamanı kullanmak büyük olasılıkla beklenen şekilde çalışma zamanı olmayan geliştiriciler bir tekniktir.</span><span class="sxs-lookup"><span data-stu-id="74720-145">This technique is the expected way non-runtime developers are likely to consume your new runtime.</span></span>

 2. <span data-ttu-id="74720-146">**Corerun.exe paketlenmemiş DLL'leri kullanmanın bir uygulamayı çalıştırmak için kullanmak**.</span><span class="sxs-lookup"><span data-stu-id="74720-146">**Use corerun.exe to run an application using unpackaged DLLs**.</span></span>
    <span data-ttu-id="74720-147">Bu depo, NuGet üzerinde hiçbir bağımlılık almaz corerun.exe adlı basit bir konak da tanımlar.</span><span class="sxs-lookup"><span data-stu-id="74720-147">This repository also defines a simple host called corerun.exe that does NOT take any dependency on NuGet.</span></span>
    <span data-ttu-id="74720-148">El ile araya toplamak zorunda ve gerçekten kullandığınız gerekli DLL'lerin nereden ana bilgisayara bildirmek gerekir.</span><span class="sxs-lookup"><span data-stu-id="74720-148">You need to tell the host where to get the required DLLs you actually use, and you have to manually gather them together.</span></span>
    <span data-ttu-id="74720-149">Bu teknik, tüm testler tarafından kullanılan [dotnet/coreclr](https://github.com/dotnet/coreclr) deponun ve ön birim testi gibi hızlı yerel 'düzenleme-derleme-hata ayıklama' döngüsü için kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="74720-149">This technique is used by all the tests in the [dotnet/coreclr](https://github.com/dotnet/coreclr) repo, and is useful for quick local 'edit-compile-debug' loop such as preliminary unit testing.</span></span>
    <span data-ttu-id="74720-150">Bkz: [CoreRun.exe ile .NET Core uygulamaları çalıştırma](https://github.com/dotnet/coreclr/blob/master/Documentation/workflow/UsingCoreRun.md) bu yöntemi kullanma hakkında bilgi.</span><span class="sxs-lookup"><span data-stu-id="74720-150">See [Executing .NET Core Apps with CoreRun.exe](https://github.com/dotnet/coreclr/blob/master/Documentation/workflow/UsingCoreRun.md) for details on using this technique.</span></span>

## <a name="build-the-cli-from-source"></a><span data-ttu-id="74720-151">Kaynak CLI'dan oluşturun</span><span class="sxs-lookup"><span data-stu-id="74720-151">Build the CLI from source</span></span>

<span data-ttu-id="74720-152">.NET Core CLI için kaynak kodu bulunabilir [dotnet/CLI](https://github.com/dotnet/cli/) github deposu.</span><span class="sxs-lookup"><span data-stu-id="74720-152">The source code for the .NET Core CLI can be found in the [dotnet/cli](https://github.com/dotnet/cli/) repository on GitHub.</span></span>

<span data-ttu-id="74720-153">.NET Core CLI'yı oluşturmak için makinenizde aşağıdaki ihtiyacınız vardır.</span><span class="sxs-lookup"><span data-stu-id="74720-153">In order to build the .NET Core CLI, you need the following installed on your machine.</span></span>

* <span data-ttu-id="74720-154">Windows ve Linux için:</span><span class="sxs-lookup"><span data-stu-id="74720-154">Windows & Linux:</span></span>
  * <span data-ttu-id="74720-155">YOL üzerindeki Git</span><span class="sxs-lookup"><span data-stu-id="74720-155">git on the PATH</span></span>
* <span data-ttu-id="74720-156">macOS:</span><span class="sxs-lookup"><span data-stu-id="74720-156">macOS:</span></span>
  * <span data-ttu-id="74720-157">YOL üzerindeki Git</span><span class="sxs-lookup"><span data-stu-id="74720-157">git on the PATH</span></span>
  * <span data-ttu-id="74720-158">Xcode</span><span class="sxs-lookup"><span data-stu-id="74720-158">Xcode</span></span>
  * <span data-ttu-id="74720-159">Openssl</span><span class="sxs-lookup"><span data-stu-id="74720-159">OpenSSL</span></span>

<span data-ttu-id="74720-160">Derleme için çalıştırmanız `build.cmd` Windows, şirket veya `build.sh` Linux ve Macos'ta kök.</span><span class="sxs-lookup"><span data-stu-id="74720-160">In order to build, run `build.cmd` on Windows, or `build.sh` on Linux and macOS from the root.</span></span> <span data-ttu-id="74720-161">Testleri yürütmek istemiyorsanız çalıştırma `build.cmd -t:Compile` veya `./build.sh -t:Compile`.</span><span class="sxs-lookup"><span data-stu-id="74720-161">If you don't want to execute tests, run `build.cmd -t:Compile` or `./build.sh -t:Compile`.</span></span> <span data-ttu-id="74720-162">MacOS Sierra CLI'daki oluşturmak için çalıştırarak DOTNET_RUNTIME_ID ortam değişkenini ayarlamanız gerekir `export DOTNET_RUNTIME_ID=osx.10.11-x64`.</span><span class="sxs-lookup"><span data-stu-id="74720-162">To build the CLI in macOS Sierra, you need to set the DOTNET_RUNTIME_ID environment variable by running `export DOTNET_RUNTIME_ID=osx.10.11-x64`.</span></span>

### <a name="using-your-build"></a><span data-ttu-id="74720-163">Yapınızı kullanma</span><span class="sxs-lookup"><span data-stu-id="74720-163">Using your build</span></span>

<span data-ttu-id="74720-164">Kullanım `dotnet` gelen yürütülebilir *yapıtları / {os}-{arch} / stage2* yeni oluşturulan CLI'yı denemek için.</span><span class="sxs-lookup"><span data-stu-id="74720-164">Use the `dotnet` executable from *artifacts/{os}-{arch}/stage2* to try out the newly built CLI.</span></span> <span data-ttu-id="74720-165">Derleme çağrılırken çıktısını kullanmak istiyorsanız `dotnet` de ekleyebilirsiniz geçerli konsolundan *yapıtları / {os}-{arch} / stage2* yolu.</span><span class="sxs-lookup"><span data-stu-id="74720-165">If you want to use the build output when invoking `dotnet` from the current console, you can also add *artifacts/{os}-{arch}/stage2* to the PATH.</span></span>

## <a name="see-also"></a><span data-ttu-id="74720-166">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="74720-166">See also</span></span>

* [<span data-ttu-id="74720-167">.NET core ortak dil çalışma zamanı (CoreCLR)</span><span class="sxs-lookup"><span data-stu-id="74720-167">.NET Core Common Language Runtime (CoreCLR)</span></span>](https://github.com/dotnet/coreclr/blob/master/README.md)
* [<span data-ttu-id="74720-168">.NET core CLI Geliştirici Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="74720-168">.NET Core CLI Developer Guide</span></span>](https://github.com/dotnet/cli/blob/master/Documentation/project-docs/developer-guide.md)
* [<span data-ttu-id="74720-169">.NET Core dağıtımı paketleme</span><span class="sxs-lookup"><span data-stu-id="74720-169">.NET Core distribution packaging</span></span>](./distribution-packaging.md)
