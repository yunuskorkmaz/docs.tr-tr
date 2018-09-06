---
title: .NET Core 2.0 yenilikleri
description: "' De .NET Core bulunan yeni özellikler hakkında bilgi edinin."
author: rpetrusha
ms.author: ronpet
ms.date: 08/13/2017
ms.openlocfilehash: 02aac2dab2b892927c0c98fae30bb287a6e24ad6
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43748641"
---
# <a name="whats-new-in-net-core-20"></a><span data-ttu-id="0ce0b-103">.NET Core 2.0 yenilikleri</span><span class="sxs-lookup"><span data-stu-id="0ce0b-103">What's new in .NET Core 2.0</span></span>

<span data-ttu-id="0ce0b-104">.NET core 2.0, aşağıdaki alanlarda geliştirmeler ve yeni özellikler içerir:</span><span class="sxs-lookup"><span data-stu-id="0ce0b-104">.NET Core 2.0 includes enhancements and new features in the following areas:</span></span>

- [<span data-ttu-id="0ce0b-105">Araç kullanımı</span><span class="sxs-lookup"><span data-stu-id="0ce0b-105">Tooling</span></span>](#tooling)
- [<span data-ttu-id="0ce0b-106">Dil desteği</span><span class="sxs-lookup"><span data-stu-id="0ce0b-106">Language support</span></span>](#language-support)
- [<span data-ttu-id="0ce0b-107">Platform geliştirmeleri</span><span class="sxs-lookup"><span data-stu-id="0ce0b-107">Platform improvements</span></span>](#platform-improvements)
- [<span data-ttu-id="0ce0b-108">API değişiklikleri</span><span class="sxs-lookup"><span data-stu-id="0ce0b-108">API changes</span></span>](#api-changes-and-library-support)
- [<span data-ttu-id="0ce0b-109">Visual Studio tümleştirmesi</span><span class="sxs-lookup"><span data-stu-id="0ce0b-109">Visual Studio integration</span></span>](#visual-studio-integration)
- [<span data-ttu-id="0ce0b-110">Belgeleri geliştirmeleri</span><span class="sxs-lookup"><span data-stu-id="0ce0b-110">Documentation improvements</span></span>](#documentation-improvements)

## <a name="tooling"></a><span data-ttu-id="0ce0b-111">Araç kullanımı</span><span class="sxs-lookup"><span data-stu-id="0ce0b-111">Tooling</span></span>

### <a name="dotnet-restore-runs-implicitly"></a><span data-ttu-id="0ce0b-112">DotNet restore örtük olarak çalışır</span><span class="sxs-lookup"><span data-stu-id="0ce0b-112">dotnet restore runs implicitly</span></span>

<span data-ttu-id="0ce0b-113">Çalıştırılacak olan .NET Core önceki sürümlerinde, [dotnet restore](../tools/dotnet-restore.md) bağımlılıkları ile yeni bir proje oluşturduğunuz hemen sonra yüklemek için komut [yeni dotnet](../tools/dotnet-new.md) yanı sıra her komut, Yeni bir bağımlılık projenize eklenir.</span><span class="sxs-lookup"><span data-stu-id="0ce0b-113">In previous versions of .NET Core, you had to run the [dotnet restore](../tools/dotnet-restore.md) command to download dependencies immediately after you created a new project with the [dotnet new](../tools/dotnet-new.md) command, as well as whenever you added a new dependency to your project.</span></span>

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

<span data-ttu-id="0ce0b-114">Ayrıca otomatik çağrılmasını devre dışı bırakabilirsiniz `dotnet restore` geçirerek `--no-restore` geçin `new`, `run`, `build`, `publish`, `pack`, ve `test` komutları.</span><span class="sxs-lookup"><span data-stu-id="0ce0b-114">You can also disable the automatic invocation of `dotnet restore` by passing the `--no-restore` switch to the `new`, `run`, `build`, `publish`, `pack`, and `test` commands.</span></span>

### <a name="retargeting-to-net-core-20"></a><span data-ttu-id="0ce0b-115">.NET Core 2.0 yeniden hedefleme</span><span class="sxs-lookup"><span data-stu-id="0ce0b-115">Retargeting to .NET Core 2.0</span></span>

<span data-ttu-id="0ce0b-116">.NET Core 2.0 SDK'sı yüklü değilse, projeler, .NET Core, .NET Core 2.0 için hedeflenmesi 1.x hedefleyin.</span><span class="sxs-lookup"><span data-stu-id="0ce0b-116">If the .NET Core 2.0 SDK is installed, projects that target .NET Core 1.x can be retargeted to .NET Core 2.0.</span></span>

<span data-ttu-id="0ce0b-117">.NET Core 2.0 için yeniden hedeflemek için değerini değiştirerek proje dosyanızı düzenlemeniz `<TargetFramework>` öğesi (veya `<TargetFrameworks>` proje dosyanızda birden fazla hedef varsa öğe) 1.x sürümünden 2.0 sürümüne'nden:</span><span class="sxs-lookup"><span data-stu-id="0ce0b-117">To retarget to .NET Core 2.0, edit your project file by changing the value of the `<TargetFramework>` element (or the `<TargetFrameworks>` element if you have more than one target in your project file) from 1.x to 2.0:</span></span>

```xml
<PropertyGroup>
    <TargetFramework>netcoreapp2.0</TargetFramework>
 </PropertyGroup>
```

<span data-ttu-id="0ce0b-118">Ayrıca, .NET Standard 2.0 .NET standart kitaplıklarına aynı şekilde hedefleyebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="0ce0b-118">You can also retarget .NET Standard libraries to .NET Standard 2.0 the same way:</span></span>

```xml
<PropertyGroup>
    <TargetFramework>netstandard2.0</TargetFramework>
 </PropertyGroup>
```

<span data-ttu-id="0ce0b-119">Projeniz .NET Core 2.0 için geçirme hakkında daha fazla bilgi için bkz. [ASP.NET Core geçiş ASP.NET Core 2.0 için 1.x](/aspnet/core/migration/1x-to-2x/index).</span><span class="sxs-lookup"><span data-stu-id="0ce0b-119">For more information about migrating your project to .NET Core 2.0, see [Migrating from ASP.NET Core 1.x to ASP.NET Core 2.0](/aspnet/core/migration/1x-to-2x/index).</span></span>

## <a name="language-support"></a><span data-ttu-id="0ce0b-120">Dil desteği</span><span class="sxs-lookup"><span data-stu-id="0ce0b-120">Language support</span></span>

<span data-ttu-id="0ce0b-121">.NET Core 2.0 C# ve F # hizmetinin yanı sıra, Visual Basic de destekler.</span><span class="sxs-lookup"><span data-stu-id="0ce0b-121">In addition to supporting C# and F#, .NET Core 2.0 also supports Visual Basic.</span></span>

### <a name="visual-basic"></a><span data-ttu-id="0ce0b-122">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="0ce0b-122">Visual Basic</span></span>

<span data-ttu-id="0ce0b-123">Sürüm 2.0 ile .NET Core, Visual Basic 2017 artık desteklemektedir.</span><span class="sxs-lookup"><span data-stu-id="0ce0b-123">With version 2.0, .NET Core now supports Visual Basic 2017.</span></span> <span data-ttu-id="0ce0b-124">Visual Basic, aşağıdaki proje türlerini oluşturmak için kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="0ce0b-124">You can use Visual Basic to create the following project types:</span></span>

- <span data-ttu-id="0ce0b-125">.NET core konsol uygulamaları</span><span class="sxs-lookup"><span data-stu-id="0ce0b-125">.NET Core console apps</span></span>
- <span data-ttu-id="0ce0b-126">.NET core sınıf kitaplıkları</span><span class="sxs-lookup"><span data-stu-id="0ce0b-126">.NET Core class libraries</span></span>
- <span data-ttu-id="0ce0b-127">.NET standart sınıf kitaplıkları</span><span class="sxs-lookup"><span data-stu-id="0ce0b-127">.NET Standard class libraries</span></span>
- <span data-ttu-id="0ce0b-128">.NET core birim testi projeleri</span><span class="sxs-lookup"><span data-stu-id="0ce0b-128">.NET Core unit test projects</span></span>
- <span data-ttu-id="0ce0b-129">.NET core xUnit test projesi</span><span class="sxs-lookup"><span data-stu-id="0ce0b-129">.NET Core xUnit test projects</span></span>

<span data-ttu-id="0ce0b-130">Örneğin, bir Visual Basic "Hello World" uygulaması oluşturmak için komut satırından aşağıdaki adımları uygulayın:</span><span class="sxs-lookup"><span data-stu-id="0ce0b-130">For example, to create a Visual Basic "Hello World" application, do the following steps from the command line:</span></span>

1. <span data-ttu-id="0ce0b-131">Bir konsol penceresi açın, projeniz için bir dizin oluşturun ve bunu geçerli dizine yapın.</span><span class="sxs-lookup"><span data-stu-id="0ce0b-131">Open a console window, create a directory for your project, and make it the current directory.</span></span>

1. <span data-ttu-id="0ce0b-132">Komutu girdikten `dotnet new console -lang vb`.</span><span class="sxs-lookup"><span data-stu-id="0ce0b-132">Enter the command `dotnet new console -lang vb`.</span></span>

   <span data-ttu-id="0ce0b-133">Komutu ile bir proje dosyası oluşturur bir `.vbproj` dosya uzantısı, adlı bir Visual Basic kaynak kod dosyası ile birlikte *Program.vb*.</span><span class="sxs-lookup"><span data-stu-id="0ce0b-133">The command creates a project file with a `.vbproj` file extension, along with a Visual Basic source code file named *Program.vb*.</span></span> <span data-ttu-id="0ce0b-134">Bu dosya "Hello World!" dize yazmak için kaynak kodunu içerir.</span><span class="sxs-lookup"><span data-stu-id="0ce0b-134">This file contains the source code to write the string "Hello World!"</span></span> <span data-ttu-id="0ce0b-135">Konsol penceresinde.</span><span class="sxs-lookup"><span data-stu-id="0ce0b-135">to the console window.</span></span>

1. <span data-ttu-id="0ce0b-136">Komutu girdikten `dotnet run`.</span><span class="sxs-lookup"><span data-stu-id="0ce0b-136">Enter the command `dotnet run`.</span></span> <span data-ttu-id="0ce0b-137">[.NET Core CLI](../tools/index.md) otomatik olarak derler ve "Hello World!" iletisini görüntüler uygulama yürütür</span><span class="sxs-lookup"><span data-stu-id="0ce0b-137">The [.NET Core CLI](../tools/index.md) automatically compiles and executes the application, which displays the message "Hello World!"</span></span> <span data-ttu-id="0ce0b-138">Konsol penceresinde.</span><span class="sxs-lookup"><span data-stu-id="0ce0b-138">in the console window.</span></span>

### <a name="support-for-c-71"></a><span data-ttu-id="0ce0b-139">C# 7.1 desteği</span><span class="sxs-lookup"><span data-stu-id="0ce0b-139">Support for C# 7.1</span></span>

<span data-ttu-id="0ce0b-140">.NET core 2.0 C# bir dizi gibi yeni özellikler ekleyen 7.1, destekler:</span><span class="sxs-lookup"><span data-stu-id="0ce0b-140">.NET Core 2.0 supports C# 7.1, which adds a number of new features, including:</span></span>

- <span data-ttu-id="0ce0b-141">`Main` Yöntemi, uygulama giriş noktası ile işaretlenebilir [zaman uyumsuz](../../csharp/language-reference/keywords/async.md) anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="0ce0b-141">The `Main` method, the application entry point, can be marked with the [async](../../csharp/language-reference/keywords/async.md) keyword.</span></span>
- <span data-ttu-id="0ce0b-142">Çıkarsanan demet adları.</span><span class="sxs-lookup"><span data-stu-id="0ce0b-142">Inferred tuple names.</span></span>
- <span data-ttu-id="0ce0b-143">Varsayılan ifade.</span><span class="sxs-lookup"><span data-stu-id="0ce0b-143">Default expressions.</span></span>

<!-- For more information see [link to C# what's new](url). -->

## <a name="platform-improvements"></a><span data-ttu-id="0ce0b-144">Platform geliştirmeleri</span><span class="sxs-lookup"><span data-stu-id="0ce0b-144">Platform improvements</span></span>

<span data-ttu-id="0ce0b-145">.NET core 2.0, .NET Core yükleyin daha kolay hale getirmek özellikleri içerir ve desteklenen işletim sistemleri üzerinde kullanın.</span><span class="sxs-lookup"><span data-stu-id="0ce0b-145">.NET Core 2.0 includes a number of features that make it easier to install .NET Core and to use it on supported operating systems.</span></span>

### <a name="net-core-for-linux-is-a-single-implementation"></a><span data-ttu-id="0ce0b-146">Linux için .NET core tek bir uygulamasıdır</span><span class="sxs-lookup"><span data-stu-id="0ce0b-146">.NET Core for Linux is a single implementation</span></span>

<span data-ttu-id="0ce0b-147">.NET core 2.0 birden çok Linux dağıtımlarında çalışır tek bir Linux uygulaması sunar.</span><span class="sxs-lookup"><span data-stu-id="0ce0b-147">.NET Core 2.0 offers a single Linux implementation that works on multiple Linux distributions.</span></span> <span data-ttu-id="0ce0b-148">.NET core 1.x gerekli dağıtım özel Linux uygulamasını indirin.</span><span class="sxs-lookup"><span data-stu-id="0ce0b-148">.NET Core 1.x required that you download a distribution-specific Linux implementation.</span></span>

<span data-ttu-id="0ce0b-149">Tek bir işletim sistemi olarak Linux'ı hedefleyen uygulamaları da geliştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0ce0b-149">You can also develop apps that target Linux as a single operating system.</span></span> <span data-ttu-id="0ce0b-150">.NET core 1.x gerekli ayrı ayrı her bir Linux dağıtımı hedefleyin.</span><span class="sxs-lookup"><span data-stu-id="0ce0b-150">.NET Core 1.x required that you target each Linux distribution separately.</span></span>

### <a name="support-for-the-apple-cryptographic-libraries"></a><span data-ttu-id="0ce0b-151">Apple şifreleme kitaplıkları için desteği</span><span class="sxs-lookup"><span data-stu-id="0ce0b-151">Support for the Apple cryptographic libraries</span></span>

<span data-ttu-id="0ce0b-152">.NET core 1.x macos'ta OpenSSL Toolkit'in şifreleme kitaplığı gerekli.</span><span class="sxs-lookup"><span data-stu-id="0ce0b-152">.NET Core 1.x on macOS required the OpenSSL toolkit's cryptographic library.</span></span> <span data-ttu-id="0ce0b-153">.NET core 2.0 Apple şifreleme kitaplıklarını kullanır ve artık yüklemeniz gerekmez, OpenSSL gerektirmez.</span><span class="sxs-lookup"><span data-stu-id="0ce0b-153">.NET Core 2.0 uses the Apple cryptographic libraries and doesn't require OpenSSL, so you no longer need to install it.</span></span>

## <a name="api-changes-and-library-support"></a><span data-ttu-id="0ce0b-154">API değişiklikleri ve kitaplık desteği</span><span class="sxs-lookup"><span data-stu-id="0ce0b-154">API changes and library support</span></span>

### <a name="support-for-net-standard-20"></a><span data-ttu-id="0ce0b-155">.NET Standard 2.0 desteği</span><span class="sxs-lookup"><span data-stu-id="0ce0b-155">Support for .NET Standard 2.0</span></span>

<span data-ttu-id="0ce0b-156">.NET Standard tutulan bir standart'ın bu sürümü ile uyumlu .NET uygulamaları üzerinde kullanılabilir API kümesi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="0ce0b-156">The .NET Standard defines a versioned set of APIs that must be available on .NET implementations that comply with that version of the standard.</span></span> <span data-ttu-id="0ce0b-157">.NET Standard kitaplığı geliştiricilere yöneliktir.</span><span class="sxs-lookup"><span data-stu-id="0ce0b-157">The .NET Standard is targeted at library developers.</span></span> <span data-ttu-id="0ce0b-158">.NET Standard'ı her .NET uygulama sürümünü hedefleyen bir kitaplık için kullanılabilir olan işlevsellik garantisi için amaçlar.</span><span class="sxs-lookup"><span data-stu-id="0ce0b-158">It aims to guarantee the functionality that is available to a library that targets a version of the .NET Standard on each .NET implementation.</span></span> <span data-ttu-id="0ce0b-159">.NET core 1.x .NET Standard sürüm 1.6 destekler; .NET Core 2.0, .NET Standard 2.0 en son sürümünü destekler.</span><span class="sxs-lookup"><span data-stu-id="0ce0b-159">.NET Core 1.x supports the .NET Standard version 1.6; .NET Core 2.0 supports the latest version, .NET Standard 2.0.</span></span> <span data-ttu-id="0ce0b-160">Daha fazla bilgi için [.NET Standard](../../standard/net-standard.md).</span><span class="sxs-lookup"><span data-stu-id="0ce0b-160">For more information, see [.NET Standard](../../standard/net-standard.md).</span></span>

<span data-ttu-id="0ce0b-161">.NET standard 2.0, .NET standart 1.6 içinde kullanılabilir olan çok 20. 000'den daha fazla APIleri içerir.</span><span class="sxs-lookup"><span data-stu-id="0ce0b-161">.NET Standard 2.0 includes over 20,000 more APIs than were available in the .NET Standard 1.6.</span></span> <span data-ttu-id="0ce0b-162">Bu çok ortak Xamarin uygulamasına .NET Standard ve .NET Framework API'ları ekleme yüzey alanını sonuçları genişletildi.</span><span class="sxs-lookup"><span data-stu-id="0ce0b-162">Much of this expanded surface area results from incorporating APIs that are common to the .NET Framework and Xamarin into .NET Standard.</span></span>

<span data-ttu-id="0ce0b-163">Bunlar, .NET Standard 2.0 sürümünde mevcut olan API'lerini çağırma koşuluyla .NET standard 2.0 sınıf kitaplıkları da .NET Framework sınıf kitaplıkları, başvurabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0ce0b-163">.NET Standard 2.0 class libraries can also reference .NET Framework class libraries, provided that they call APIs that are present in the .NET Standard 2.0.</span></span> <span data-ttu-id="0ce0b-164">.NET Framework kitaplıkları, herhangi bir yeniden derleme gereklidir.</span><span class="sxs-lookup"><span data-stu-id="0ce0b-164">No recompilation of the .NET Framework libraries is required.</span></span>

<span data-ttu-id="0ce0b-165">Son sürümünden bu yana .NET standart 1.6 için .NET Standard eklenmiş API'lerin bir listesi için bkz: [.NET Standard 2.0 vs. 1.6](https://raw.githubusercontent.com/dotnet/standard/master/docs/versions/netstandard2.0_diff.md).</span><span class="sxs-lookup"><span data-stu-id="0ce0b-165">For a list of the APIs that have been added to the .NET Standard since its last version, the .NET Standard 1.6, see [.NET Standard 2.0 vs. 1.6](https://raw.githubusercontent.com/dotnet/standard/master/docs/versions/netstandard2.0_diff.md).</span></span>

### <a name="expanded-surface-area"></a><span data-ttu-id="0ce0b-166">Genişletilmiş yüzey alanı</span><span class="sxs-lookup"><span data-stu-id="0ce0b-166">Expanded surface area</span></span>

<span data-ttu-id="0ce0b-167">API'ler .NET Core 2.0 kullanılabilir toplam sayısı, birden fazla .NET Core 1.1 karşılaştırıldığında katladı.</span><span class="sxs-lookup"><span data-stu-id="0ce0b-167">The total number of APIs available on .NET Core 2.0 has more than doubled in comparison with .NET Core 1.1.</span></span>

<span data-ttu-id="0ce0b-168">İle [Windows Uyumluluk Paketi](../porting/windows-compat-pack.md) .NET Framework'ten taşıma ayrıca haline gelmiştir çok daha kolaydır.</span><span class="sxs-lookup"><span data-stu-id="0ce0b-168">And with the [Windows Compatibility Pack](../porting/windows-compat-pack.md) porting from .NET Framework has also become much simpler.</span></span>

### <a name="support-for-net-framework-libraries"></a><span data-ttu-id="0ce0b-169">.NET Framework kitaplıkları için desteği</span><span class="sxs-lookup"><span data-stu-id="0ce0b-169">Support for .NET Framework libraries</span></span>

<span data-ttu-id="0ce0b-170">.NET core kodu mevcut NuGet paketlerini de dahil olmak üzere var olan .NET Framework kitaplıkları başvurabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0ce0b-170">.NET Core code can reference existing .NET Framework libraries, including existing NuGet packages.</span></span> <span data-ttu-id="0ce0b-171">.NET Standard sürümünde bulunan API kitaplıklarını kullanması gerektiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="0ce0b-171">Note that the libraries must use APIs that are found in .NET Standard.</span></span>

## <a name="visual-studio-integration"></a><span data-ttu-id="0ce0b-172">Visual Studio tümleştirmesi</span><span class="sxs-lookup"><span data-stu-id="0ce0b-172">Visual Studio integration</span></span>

<span data-ttu-id="0ce0b-173">Visual Studio 2017 sürüm 15.3 ve bazı durumlarda Mac için Visual Studio, .NET Core geliştiricileri için önemli geliştirmeleri sunar.</span><span class="sxs-lookup"><span data-stu-id="0ce0b-173">Visual Studio 2017 version 15.3 and in some cases Visual Studio for Mac offer a number of significant enhancements for .NET Core developers.</span></span>

### <a name="retargeting-net-core-apps-and-net-standard-libraries"></a><span data-ttu-id="0ce0b-174">.NET Core uygulamaları ve .NET standart kitaplıkları yeniden hedefleme</span><span class="sxs-lookup"><span data-stu-id="0ce0b-174">Retargeting .NET Core apps and .NET Standard libraries</span></span>

<span data-ttu-id="0ce0b-175">.NET Core 2.0 SDK'sı yüklü değilse, .NET Core 1.x projelerini .NET Standard 2.0 için .NET Core 2.0 ve .NET Standard 1.x kitaplıklara hedefleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0ce0b-175">If the .NET Core 2.0 SDK is installed, you can retarget .NET Core 1.x projects to .NET Core 2.0 and .NET Standard 1.x libraries to .NET Standard 2.0.</span></span>

<span data-ttu-id="0ce0b-176">Visual Studio projeleri yeniden hedeflemek için açtığınız **uygulama** sekmesi Proje Özellikleri iletişim kutusu ile değiştirin **hedef Framework'ü** değerini **.NET Core 2.0** veya **.NET standard 2.0**.</span><span class="sxs-lookup"><span data-stu-id="0ce0b-176">To retarget your project in Visual Studio, you open the **Application** tab of the project's properties dialog and change the **Target framework** value to **.NET Core 2.0** or **.NET Standard 2.0**.</span></span> <span data-ttu-id="0ce0b-177">Ayrıca, proje üzerinde sağ tıklatıp seçerek değiştirebilirsiniz **Düzenle \*.csproj dosyasını** seçeneği.</span><span class="sxs-lookup"><span data-stu-id="0ce0b-177">You can also change it by right-clicking on the project and selecting the **Edit \*.csproj file** option.</span></span> <span data-ttu-id="0ce0b-178">Daha fazla bilgi için [Tooling](#tooling) bölümü bu konuda.</span><span class="sxs-lookup"><span data-stu-id="0ce0b-178">For more information, see the [Tooling](#tooling) section earlier in this topic.</span></span>

### <a name="live-unit-testing-support-for-net-core"></a><span data-ttu-id="0ce0b-179">.NET Core için Live Unit Testing</span><span class="sxs-lookup"><span data-stu-id="0ce0b-179">Live Unit Testing support for .NET Core</span></span>

<span data-ttu-id="0ce0b-180">Kodunuzu değiştirmeniz her Live Unit Testing otomatik olarak tüm etkilenen birim testlerini arka planda çalıştırır ve sonuçları ve kod kapsamını Canlı Visual Studio ortamında görüntüler.</span><span class="sxs-lookup"><span data-stu-id="0ce0b-180">Whenever you modify your code, Live Unit Testing automatically runs any affected unit tests in the background and displays the results and code coverage live in the Visual Studio environment.</span></span> <span data-ttu-id="0ce0b-181">.NET core 2.0, Live Unit Testing artık desteklemektedir.</span><span class="sxs-lookup"><span data-stu-id="0ce0b-181">.NET Core 2.0 now supports Live Unit Testing.</span></span> <span data-ttu-id="0ce0b-182">Daha önce Live Unit Testing yalnızca .NET Framework uygulamaları için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="0ce0b-182">Previously, Live Unit Testing was available only for .NET Framework applications.</span></span>

<span data-ttu-id="0ce0b-183">Daha fazla bilgi için [Visual Studio 2017 ile Live Unit Testing](/visualstudio/test/live-unit-testing) ve [Live Unit Testing SSS](/visualstudio/test/live-unit-testing-faq).</span><span class="sxs-lookup"><span data-stu-id="0ce0b-183">For more information, see [Live Unit Testing with Visual Studio 2017](/visualstudio/test/live-unit-testing) and the [Live Unit Testing FAQ](/visualstudio/test/live-unit-testing-faq).</span></span>

### <a name="better-support-for-multiple-target-frameworks"></a><span data-ttu-id="0ce0b-184">Birden çok hedef çerçeve için daha iyi destek</span><span class="sxs-lookup"><span data-stu-id="0ce0b-184">Better support for multiple target frameworks</span></span>

<span data-ttu-id="0ce0b-185">Birden çok hedef çerçeve için bir proje oluşturuyorsanız, hedef platformu artık üst düzey menüsünden seçebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0ce0b-185">If you're building a project for multiple target frameworks, you can now select the target platform from the top-level menu.</span></span> <span data-ttu-id="0ce0b-186">Aşağıdaki resimde, bir proje adlı SCD1 hedefleri 64-bit macOS X 10.11 (`osx.10.11-x64`) ve 64-bit Windows 10/Windows Server 2016 (`win10-x64`).</span><span class="sxs-lookup"><span data-stu-id="0ce0b-186">In the following figure, a project named SCD1 targets 64-bit macOS X 10.11 (`osx.10.11-x64`) and 64-bit Windows 10/Windows Server 2016 (`win10-x64`).</span></span> <span data-ttu-id="0ce0b-187">Hedef Çerçeve proje düğmesi, bu durumda hata ayıklama derlemesi çalıştırılacak seçmeden önce seçebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0ce0b-187">You can select the target framework before selecting the project button, in this case to run a debug build.</span></span>

![Hedef Framework'ü bir proje derlenirken seçme](media/multitarget.png)

### <a name="side-by-side-support-for-net-core-sdks"></a><span data-ttu-id="0ce0b-189">.NET Core SDK'ları için yan yana desteği</span><span class="sxs-lookup"><span data-stu-id="0ce0b-189">Side-by-side support for .NET Core SDKs</span></span>

<span data-ttu-id="0ce0b-190">Artık Visual Studio bağımsız olarak .NET Core SDK'sını yükleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0ce0b-190">You can now install the .NET Core SDK independently of Visual Studio.</span></span> <span data-ttu-id="0ce0b-191">Bu, tek bir sürüm farklı sürümlerini hedefleyen .NET Core projeleri derlemek için Visual Studio'nun mümkün kılar.</span><span class="sxs-lookup"><span data-stu-id="0ce0b-191">This makes it possible for a single version of Visual Studio to build projects that target different versions of .NET Core.</span></span> <span data-ttu-id="0ce0b-192">Daha önce Visual Studio ve .NET Core SDK'sını sıkı şekilde bağlı; belirli bir SDK sürümü Visual Studio'nun belirli bir sürümü eşlik.</span><span class="sxs-lookup"><span data-stu-id="0ce0b-192">Previously, Visual Studio and the .NET Core SDK were tightly coupled; a particular version of the SDK accompanied a particular version of Visual Studio.</span></span>

## <a name="documentation-improvements"></a><span data-ttu-id="0ce0b-193">Belgeleri geliştirmeleri</span><span class="sxs-lookup"><span data-stu-id="0ce0b-193">Documentation improvements</span></span>

### <a name="net-application-architecture"></a><span data-ttu-id="0ce0b-194">.NET uygulama mimarisi</span><span class="sxs-lookup"><span data-stu-id="0ce0b-194">.NET Application Architecture</span></span>

<span data-ttu-id="0ce0b-195">[.NET uygulama mimarisi](https://www.microsoft.com/net/learn/architecture) rehberlik, e-Kitapları kümesine erişim sağlar, en iyi uygulamalar ve örnek uygulamalar oluşturmak için .NET kullanırken:</span><span class="sxs-lookup"><span data-stu-id="0ce0b-195">[.NET Application Architecture](https://www.microsoft.com/net/learn/architecture) gives you access to a set of e-books that provide guidance, best practices, and sample applications when using .NET to build:</span></span>

- [<span data-ttu-id="0ce0b-196">Mikro hizmetler ve Docker kapsayıcıları</span><span class="sxs-lookup"><span data-stu-id="0ce0b-196">Microservices and Docker containers</span></span>](../../standard/microservices-architecture/index.md)
- [<span data-ttu-id="0ce0b-197">ASP.NET ile Web uygulamaları</span><span class="sxs-lookup"><span data-stu-id="0ce0b-197">Web applications with ASP.NET</span></span>](../../standard/modern-web-apps-azure-architecture/index.md)
- [<span data-ttu-id="0ce0b-198">Xamarin ile mobil uygulamalar</span><span class="sxs-lookup"><span data-stu-id="0ce0b-198">Mobile applications with Xamarin</span></span>](/xamarin/xamarin-forms/enterprise-application-patterns/index.md)
- [<span data-ttu-id="0ce0b-199">Azure ile buluta dağıtılan uygulamalar</span><span class="sxs-lookup"><span data-stu-id="0ce0b-199">Applications that are deployed to the Cloud with Azure</span></span>](/azure/architecture/reference-architectures/index.md)

## <a name="see-also"></a><span data-ttu-id="0ce0b-200">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0ce0b-200">See also</span></span>

* [<span data-ttu-id="0ce0b-201">ASP.NET Core 2.0 yenilikleri</span><span class="sxs-lookup"><span data-stu-id="0ce0b-201">What's new in ASP.NET Core 2.0</span></span>](/aspnet/core/aspnetcore-2.0)
