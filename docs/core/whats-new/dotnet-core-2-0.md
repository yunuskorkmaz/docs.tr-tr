---
title: ​.NET Core 2.0’deki yenilikler
description: .NET Core 'da bulunan yeni özellikler hakkında bilgi edinin.
ms.date: 08/13/2017
ms.openlocfilehash: 115b3adc72b6798c6a7bac9cc18044a8822808a6
ms.sourcegitcommit: 32a575bf4adccc901f00e264f92b759ced633379
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/04/2019
ms.locfileid: "74801899"
---
# <a name="whats-new-in-net-core-20"></a><span data-ttu-id="aad5c-103">​.NET Core 2.0’deki yenilikler</span><span class="sxs-lookup"><span data-stu-id="aad5c-103">What's new in .NET Core 2.0</span></span>

<span data-ttu-id="aad5c-104">.NET Core 2,0, aşağıdaki alanlarda geliştirmeler ve yeni özellikler içerir:</span><span class="sxs-lookup"><span data-stu-id="aad5c-104">.NET Core 2.0 includes enhancements and new features in the following areas:</span></span>

- [<span data-ttu-id="aad5c-105">Araçları</span><span class="sxs-lookup"><span data-stu-id="aad5c-105">Tooling</span></span>](#tooling)
- [<span data-ttu-id="aad5c-106">Dil desteği</span><span class="sxs-lookup"><span data-stu-id="aad5c-106">Language support</span></span>](#language-support)
- [<span data-ttu-id="aad5c-107">Platform geliştirmeleri</span><span class="sxs-lookup"><span data-stu-id="aad5c-107">Platform improvements</span></span>](#platform-improvements)
- [<span data-ttu-id="aad5c-108">API değişiklikleri</span><span class="sxs-lookup"><span data-stu-id="aad5c-108">API changes</span></span>](#api-changes-and-library-support)
- [<span data-ttu-id="aad5c-109">Visual Studio tümleştirmesi</span><span class="sxs-lookup"><span data-stu-id="aad5c-109">Visual Studio integration</span></span>](#visual-studio-integration)
- [<span data-ttu-id="aad5c-110">Belge geliştirmeleri</span><span class="sxs-lookup"><span data-stu-id="aad5c-110">Documentation improvements</span></span>](#documentation-improvements)

## <a name="tooling"></a><span data-ttu-id="aad5c-111">Araçlar</span><span class="sxs-lookup"><span data-stu-id="aad5c-111">Tooling</span></span>

### <a name="dotnet-restore-runs-implicitly"></a><span data-ttu-id="aad5c-112">dotnet restore örtük olarak çalıştırılır</span><span class="sxs-lookup"><span data-stu-id="aad5c-112">dotnet restore runs implicitly</span></span>

<span data-ttu-id="aad5c-113">.NET Core 'un önceki sürümlerinde, [DotNet New](../tools/dotnet-new.md) komutuyla yeni bir proje oluşturduktan sonra ve projenize yeni bir bağımlılık eklediğiniz her seferinde bağımlılıkları indirmek için [DotNet restore](../tools/dotnet-restore.md) komutunu çalıştırmanız gerekiyordu.</span><span class="sxs-lookup"><span data-stu-id="aad5c-113">In previous versions of .NET Core, you had to run the [dotnet restore](../tools/dotnet-restore.md) command to download dependencies immediately after you created a new project with the [dotnet new](../tools/dotnet-new.md) command, as well as whenever you added a new dependency to your project.</span></span>

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

<span data-ttu-id="aad5c-114">Ayrıca, `--no-restore` anahtarını `new`, `run`, `build`, `publish`, `pack`ve `test` komutlarına geçirerek `dotnet restore` otomatik olarak çağrılmasını devre dışı bırakabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="aad5c-114">You can also disable the automatic invocation of `dotnet restore` by passing the `--no-restore` switch to the `new`, `run`, `build`, `publish`, `pack`, and `test` commands.</span></span>

### <a name="retargeting-to-net-core-20"></a><span data-ttu-id="aad5c-115">.NET Core 2,0 için yeniden hedefleme</span><span class="sxs-lookup"><span data-stu-id="aad5c-115">Retargeting to .NET Core 2.0</span></span>

<span data-ttu-id="aad5c-116">.NET Core 2,0 SDK 'Sı yüklüyse, .NET Core 1. x 'i hedefleyen projeler .NET Core 2,0 ' e yeniden hedeflenebilir.</span><span class="sxs-lookup"><span data-stu-id="aad5c-116">If the .NET Core 2.0 SDK is installed, projects that target .NET Core 1.x can be retargeted to .NET Core 2.0.</span></span>

<span data-ttu-id="aad5c-117">.NET Core 2,0 ' ye yeniden hedeflemesini sağlamak için, `<TargetFramework>` öğesinin değerini değiştirerek (veya proje dosyanızda birden fazla hedef varsa `<TargetFrameworks>` öğesi) 1. x ile 2,0 arasında bir proje dosyası düzenleyin:</span><span class="sxs-lookup"><span data-stu-id="aad5c-117">To retarget to .NET Core 2.0, edit your project file by changing the value of the `<TargetFramework>` element (or the `<TargetFrameworks>` element if you have more than one target in your project file) from 1.x to 2.0:</span></span>

```xml
<PropertyGroup>
    <TargetFramework>netcoreapp2.0</TargetFramework>
 </PropertyGroup>
```

<span data-ttu-id="aad5c-118">Ayrıca, .NET Standard kitaplıklarını aynı şekilde .NET Standard 2,0 olarak yeniden hedefleyebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="aad5c-118">You can also retarget .NET Standard libraries to .NET Standard 2.0 the same way:</span></span>

```xml
<PropertyGroup>
    <TargetFramework>netstandard2.0</TargetFramework>
 </PropertyGroup>
```

<span data-ttu-id="aad5c-119">Projenizi .NET Core 2,0 ' e geçirme hakkında daha fazla bilgi için, bkz [. asp.NET Core 1. x ' den ASP.NET Core 2,0 ' ye](/aspnet/core/migration/1x-to-2x/index)geçme.</span><span class="sxs-lookup"><span data-stu-id="aad5c-119">For more information about migrating your project to .NET Core 2.0, see [Migrating from ASP.NET Core 1.x to ASP.NET Core 2.0](/aspnet/core/migration/1x-to-2x/index).</span></span>

## <a name="language-support"></a><span data-ttu-id="aad5c-120">Dil desteği</span><span class="sxs-lookup"><span data-stu-id="aad5c-120">Language support</span></span>

<span data-ttu-id="aad5c-121">Ve C# F#' nin desteklenmesinin yanı sıra, .net Core 2,0 de Visual Basic destekler.</span><span class="sxs-lookup"><span data-stu-id="aad5c-121">In addition to supporting C# and F#, .NET Core 2.0 also supports Visual Basic.</span></span>

### <a name="visual-basic"></a><span data-ttu-id="aad5c-122">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="aad5c-122">Visual Basic</span></span>

<span data-ttu-id="aad5c-123">Sürüm 2,0 ile, .NET Core artık Visual Basic 2017 ' yi desteklemektedir.</span><span class="sxs-lookup"><span data-stu-id="aad5c-123">With version 2.0, .NET Core now supports Visual Basic 2017.</span></span> <span data-ttu-id="aad5c-124">Visual Basic, aşağıdaki proje türlerini oluşturmak için kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="aad5c-124">You can use Visual Basic to create the following project types:</span></span>

- <span data-ttu-id="aad5c-125">.NET Core konsol uygulamaları</span><span class="sxs-lookup"><span data-stu-id="aad5c-125">.NET Core console apps</span></span>
- <span data-ttu-id="aad5c-126">.NET Core sınıf kitaplıkları</span><span class="sxs-lookup"><span data-stu-id="aad5c-126">.NET Core class libraries</span></span>
- <span data-ttu-id="aad5c-127">.NET Standard sınıf kitaplıkları</span><span class="sxs-lookup"><span data-stu-id="aad5c-127">.NET Standard class libraries</span></span>
- <span data-ttu-id="aad5c-128">.NET Core birim testi projeleri</span><span class="sxs-lookup"><span data-stu-id="aad5c-128">.NET Core unit test projects</span></span>
- <span data-ttu-id="aad5c-129">.NET Core xUnit test projeleri</span><span class="sxs-lookup"><span data-stu-id="aad5c-129">.NET Core xUnit test projects</span></span>

<span data-ttu-id="aad5c-130">Örneğin, bir Visual Basic "Merhaba Dünya" uygulaması oluşturmak için komut satırından aşağıdaki adımları uygulayın:</span><span class="sxs-lookup"><span data-stu-id="aad5c-130">For example, to create a Visual Basic "Hello World" application, do the following steps from the command line:</span></span>

1. <span data-ttu-id="aad5c-131">Bir konsol penceresi açın, projeniz için bir dizin oluşturun ve geçerli dizin yapın.</span><span class="sxs-lookup"><span data-stu-id="aad5c-131">Open a console window, create a directory for your project, and make it the current directory.</span></span>

1. <span data-ttu-id="aad5c-132">`dotnet new console -lang vb`komutunu girin.</span><span class="sxs-lookup"><span data-stu-id="aad5c-132">Enter the command `dotnet new console -lang vb`.</span></span>

   <span data-ttu-id="aad5c-133">Komut, *program. vb*adlı bir Visual Basic kaynak kodu dosyası ile birlikte `.vbproj` dosya uzantısına sahip bir proje dosyası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="aad5c-133">The command creates a project file with a `.vbproj` file extension, along with a Visual Basic source code file named *Program.vb*.</span></span> <span data-ttu-id="aad5c-134">Bu dosya, "Merhaba Dünya!" dizesinin yazılacağı kaynak kodunu içerir</span><span class="sxs-lookup"><span data-stu-id="aad5c-134">This file contains the source code to write the string "Hello World!"</span></span> <span data-ttu-id="aad5c-135">Konsol penceresine.</span><span class="sxs-lookup"><span data-stu-id="aad5c-135">to the console window.</span></span>

1. <span data-ttu-id="aad5c-136">`dotnet run`komutunu girin.</span><span class="sxs-lookup"><span data-stu-id="aad5c-136">Enter the command `dotnet run`.</span></span> <span data-ttu-id="aad5c-137">[.NET Core CLI](../tools/index.md) , uygulamayı otomatik olarak derler ve yürütür ve "Merhaba Dünya!" iletisini görüntüler.</span><span class="sxs-lookup"><span data-stu-id="aad5c-137">The [.NET Core CLI](../tools/index.md) automatically compiles and executes the application, which displays the message "Hello World!"</span></span> <span data-ttu-id="aad5c-138">Konsol penceresinde.</span><span class="sxs-lookup"><span data-stu-id="aad5c-138">in the console window.</span></span>

### <a name="support-for-c-71"></a><span data-ttu-id="aad5c-139">7,1 için C# destek</span><span class="sxs-lookup"><span data-stu-id="aad5c-139">Support for C# 7.1</span></span>

<span data-ttu-id="aad5c-140">.NET Core 2,0, C# aşağıdakiler de dahil olmak üzere çeşitli yeni özellikler ekleyen 7,1 ' i destekler:</span><span class="sxs-lookup"><span data-stu-id="aad5c-140">.NET Core 2.0 supports C# 7.1, which adds a number of new features, including:</span></span>

- <span data-ttu-id="aad5c-141">Uygulama giriş noktası `Main` yöntemi, [Async](../../csharp/language-reference/keywords/async.md) anahtar sözcüğüyle işaretlenebilir.</span><span class="sxs-lookup"><span data-stu-id="aad5c-141">The `Main` method, the application entry point, can be marked with the [async](../../csharp/language-reference/keywords/async.md) keyword.</span></span>
- <span data-ttu-id="aad5c-142">Çıkarsanan demet adları.</span><span class="sxs-lookup"><span data-stu-id="aad5c-142">Inferred tuple names.</span></span>
- <span data-ttu-id="aad5c-143">Varsayılan ifadeler.</span><span class="sxs-lookup"><span data-stu-id="aad5c-143">Default expressions.</span></span>

<!-- For more information see [link to C# what's new](url). -->

## <a name="platform-improvements"></a><span data-ttu-id="aad5c-144">Platform geliştirmeleri</span><span class="sxs-lookup"><span data-stu-id="aad5c-144">Platform improvements</span></span>

<span data-ttu-id="aad5c-145">.NET Core 2,0, .NET Core 'u yüklemeyi ve desteklenen işletim sistemlerinde kullanmayı kolaylaştıran birçok özellik içerir.</span><span class="sxs-lookup"><span data-stu-id="aad5c-145">.NET Core 2.0 includes a number of features that make it easier to install .NET Core and to use it on supported operating systems.</span></span>

### <a name="net-core-for-linux-is-a-single-implementation"></a><span data-ttu-id="aad5c-146">Linux için .NET Core tek bir uygulama</span><span class="sxs-lookup"><span data-stu-id="aad5c-146">.NET Core for Linux is a single implementation</span></span>

<span data-ttu-id="aad5c-147">.NET Core 2,0, birden çok Linux dağıtımı üzerinde çalışabilen tek bir Linux uygulamasını sunmaktadır.</span><span class="sxs-lookup"><span data-stu-id="aad5c-147">.NET Core 2.0 offers a single Linux implementation that works on multiple Linux distributions.</span></span> <span data-ttu-id="aad5c-148">.NET Core 1. x, dağıtıma özgü bir Linux uygulamasını indirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="aad5c-148">.NET Core 1.x required that you download a distribution-specific Linux implementation.</span></span>

<span data-ttu-id="aad5c-149">Ayrıca, Linux 'u tek bir işletim sistemi olarak hedefleyen uygulamalar da geliştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="aad5c-149">You can also develop apps that target Linux as a single operating system.</span></span> <span data-ttu-id="aad5c-150">.NET Core 1. x, her bir Linux dağıtımını ayrı olarak hedeflediğiniz için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="aad5c-150">.NET Core 1.x required that you target each Linux distribution separately.</span></span>

### <a name="support-for-the-apple-cryptographic-libraries"></a><span data-ttu-id="aad5c-151">Apple şifreleme kitaplıkları için destek</span><span class="sxs-lookup"><span data-stu-id="aad5c-151">Support for the Apple cryptographic libraries</span></span>

<span data-ttu-id="aad5c-152">MacOS üzerinde .NET Core 1. x, OpenSSL araç setinin şifreleme kitaplığını gerektirdi.</span><span class="sxs-lookup"><span data-stu-id="aad5c-152">.NET Core 1.x on macOS required the OpenSSL toolkit's cryptographic library.</span></span> <span data-ttu-id="aad5c-153">.NET Core 2,0, Apple şifreleme kitaplıklarını kullanır ve OpenSSL gerektirmez, bu nedenle artık yüklemeniz gerekmez.</span><span class="sxs-lookup"><span data-stu-id="aad5c-153">.NET Core 2.0 uses the Apple cryptographic libraries and doesn't require OpenSSL, so you no longer need to install it.</span></span>

## <a name="api-changes-and-library-support"></a><span data-ttu-id="aad5c-154">API değişiklikleri ve kitaplık desteği</span><span class="sxs-lookup"><span data-stu-id="aad5c-154">API changes and library support</span></span>

### <a name="support-for-net-standard-20"></a><span data-ttu-id="aad5c-155">.NET Standard 2,0 desteği</span><span class="sxs-lookup"><span data-stu-id="aad5c-155">Support for .NET Standard 2.0</span></span>

<span data-ttu-id="aad5c-156">.NET Standard, Standard 'ın bu sürümüyle uyumlu .NET uygulamalarında kullanılabilmesi gereken sürümlenmiş bir API kümesini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="aad5c-156">The .NET Standard defines a versioned set of APIs that must be available on .NET implementations that comply with that version of the standard.</span></span> <span data-ttu-id="aad5c-157">.NET Standard, kitaplık geliştiricileri 'ne yöneliktir.</span><span class="sxs-lookup"><span data-stu-id="aad5c-157">The .NET Standard is targeted at library developers.</span></span> <span data-ttu-id="aad5c-158">Her bir .NET uygulamasındaki .NET Standard bir sürümünü hedefleyen bir kitaplık için kullanılabilen işlevselliği garanti etmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="aad5c-158">It aims to guarantee the functionality that is available to a library that targets a version of the .NET Standard on each .NET implementation.</span></span> <span data-ttu-id="aad5c-159">.NET Core 1. x .NET Standard sürüm 1,6 ' ü destekler; .NET Core 2,0, en son sürümü .NET Standard 2,0.</span><span class="sxs-lookup"><span data-stu-id="aad5c-159">.NET Core 1.x supports the .NET Standard version 1.6; .NET Core 2.0 supports the latest version, .NET Standard 2.0.</span></span> <span data-ttu-id="aad5c-160">Daha fazla bilgi için [.NET Standard](../../standard/net-standard.md).</span><span class="sxs-lookup"><span data-stu-id="aad5c-160">For more information, see [.NET Standard](../../standard/net-standard.md).</span></span>

<span data-ttu-id="aad5c-161">.NET Standard 2,0, .NET Standard 1,6 ' de kullanılabilir olandan daha fazla 20.000 API 'ye sahiptir.</span><span class="sxs-lookup"><span data-stu-id="aad5c-161">.NET Standard 2.0 includes over 20,000 more APIs than were available in the .NET Standard 1.6.</span></span> <span data-ttu-id="aad5c-162">Bu genişletilmiş yüzey alanının büyük bölümü, .NET Framework ve Xamarin için ortak olan API 'Leri .NET Standard ' ye ekleme sonucu oluşur.</span><span class="sxs-lookup"><span data-stu-id="aad5c-162">Much of this expanded surface area results from incorporating APIs that are common to the .NET Framework and Xamarin into .NET Standard.</span></span>

<span data-ttu-id="aad5c-163">.NET Standard 2,0 sınıf kitaplıkları ayrıca .NET Standard 2,0 ' de bulunan API 'Leri çağırmak kaydıyla .NET Framework sınıf kitaplıklarına başvurabilir.</span><span class="sxs-lookup"><span data-stu-id="aad5c-163">.NET Standard 2.0 class libraries can also reference .NET Framework class libraries, provided that they call APIs that are present in the .NET Standard 2.0.</span></span> <span data-ttu-id="aad5c-164">.NET Framework kitaplıklarının yeniden derlenmesi gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="aad5c-164">No recompilation of the .NET Framework libraries is required.</span></span>

<span data-ttu-id="aad5c-165">Son sürümü bu yana .NET Standard eklenen API 'lerin bir listesi için, .NET Standard 1,6, bkz. [.NET Standard 2,0 vs. 1,6](https://raw.githubusercontent.com/dotnet/standard/master/docs/versions/netstandard2.0_diff.md).</span><span class="sxs-lookup"><span data-stu-id="aad5c-165">For a list of the APIs that have been added to the .NET Standard since its last version, the .NET Standard 1.6, see [.NET Standard 2.0 vs. 1.6](https://raw.githubusercontent.com/dotnet/standard/master/docs/versions/netstandard2.0_diff.md).</span></span>

### <a name="expanded-surface-area"></a><span data-ttu-id="aad5c-166">Genişletilmiş yüzey alanı</span><span class="sxs-lookup"><span data-stu-id="aad5c-166">Expanded surface area</span></span>

<span data-ttu-id="aad5c-167">.NET Core 2,0 ' de mevcut olan API 'lerin toplam sayısı, .NET Core 1,1 ile karşılaştırıldığında iki katına çıkar.</span><span class="sxs-lookup"><span data-stu-id="aad5c-167">The total number of APIs available on .NET Core 2.0 has more than doubled in comparison with .NET Core 1.1.</span></span>

<span data-ttu-id="aad5c-168">[Windows Uyumluluk paketi](../porting/windows-compat-pack.md) .NET Framework 'den taşıma işlemi de çok daha kolay hale geldi.</span><span class="sxs-lookup"><span data-stu-id="aad5c-168">And with the [Windows Compatibility Pack](../porting/windows-compat-pack.md) porting from .NET Framework has also become much simpler.</span></span>

### <a name="support-for-net-framework-libraries"></a><span data-ttu-id="aad5c-169">.NET Framework kitaplıkları için destek</span><span class="sxs-lookup"><span data-stu-id="aad5c-169">Support for .NET Framework libraries</span></span>

<span data-ttu-id="aad5c-170">.NET Core Code var olan NuGet paketleri de dahil olmak üzere mevcut .NET Framework kitaplıklarına başvurabilir.</span><span class="sxs-lookup"><span data-stu-id="aad5c-170">.NET Core code can reference existing .NET Framework libraries, including existing NuGet packages.</span></span> <span data-ttu-id="aad5c-171">Kitaplıkların .NET Standard bulunan API 'Leri kullanması gerektiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="aad5c-171">Note that the libraries must use APIs that are found in .NET Standard.</span></span>

## <a name="visual-studio-integration"></a><span data-ttu-id="aad5c-172">Visual Studio tümleştirmesi</span><span class="sxs-lookup"><span data-stu-id="aad5c-172">Visual Studio integration</span></span>

<span data-ttu-id="aad5c-173">Visual Studio 2017 sürüm 15,3 ve bazı durumlarda Mac için Visual Studio .NET Core geliştiricileri için çeşitli önemli geliştirmeler sunar.</span><span class="sxs-lookup"><span data-stu-id="aad5c-173">Visual Studio 2017 version 15.3 and in some cases Visual Studio for Mac offer a number of significant enhancements for .NET Core developers.</span></span>

### <a name="retargeting-net-core-apps-and-net-standard-libraries"></a><span data-ttu-id="aad5c-174">.NET Core uygulamalarını ve .NET Standard kitaplıklarını yeniden hedefleme</span><span class="sxs-lookup"><span data-stu-id="aad5c-174">Retargeting .NET Core apps and .NET Standard libraries</span></span>

<span data-ttu-id="aad5c-175">.NET Core 2,0 SDK 'Sı yüklüyse, .NET Core 1. x projelerini .NET Core 2,0 ve .NET Standard 1. x kitaplıklarını .NET Standard 2,0 olarak yeniden hedefleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="aad5c-175">If the .NET Core 2.0 SDK is installed, you can retarget .NET Core 1.x projects to .NET Core 2.0 and .NET Standard 1.x libraries to .NET Standard 2.0.</span></span>

<span data-ttu-id="aad5c-176">Projenizi Visual Studio 'da yeniden hedeflemek için projenin Özellikler iletişim kutusunun **uygulama** sekmesini açın ve **hedef Framework** değerini **.net Core 2,0** veya **2,0 .NET Standard**olarak değiştirirsiniz.</span><span class="sxs-lookup"><span data-stu-id="aad5c-176">To retarget your project in Visual Studio, you open the **Application** tab of the project's properties dialog and change the **Target framework** value to **.NET Core 2.0** or **.NET Standard 2.0**.</span></span> <span data-ttu-id="aad5c-177">Ayrıca, projeye sağ tıklayıp **\*. csproj dosyasını Düzenle** seçeneğini belirleyerek bunu değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="aad5c-177">You can also change it by right-clicking on the project and selecting the **Edit \*.csproj file** option.</span></span> <span data-ttu-id="aad5c-178">Daha fazla bilgi için bu konunun önceki kısımlarında yer alan [Araçlar bölümüne bakın](#tooling) .</span><span class="sxs-lookup"><span data-stu-id="aad5c-178">For more information, see the [Tooling](#tooling) section earlier in this topic.</span></span>

### <a name="live-unit-testing-support-for-net-core"></a><span data-ttu-id="aad5c-179">.NET Core için Live Unit Testing</span><span class="sxs-lookup"><span data-stu-id="aad5c-179">Live Unit Testing support for .NET Core</span></span>

<span data-ttu-id="aad5c-180">Kodunuzu her değiştirdiğinizde Live Unit Testing otomatik olarak etkilenen birim testlerini arka planda çalıştırır ve Visual Studio ortamında sonuçları ve kod kapsamını canlı olarak görüntüler.</span><span class="sxs-lookup"><span data-stu-id="aad5c-180">Whenever you modify your code, Live Unit Testing automatically runs any affected unit tests in the background and displays the results and code coverage live in the Visual Studio environment.</span></span> <span data-ttu-id="aad5c-181">.NET Core 2,0 artık Live Unit Testing desteklemektedir.</span><span class="sxs-lookup"><span data-stu-id="aad5c-181">.NET Core 2.0 now supports Live Unit Testing.</span></span> <span data-ttu-id="aad5c-182">Daha önce Live Unit Testing yalnızca .NET Framework uygulamalar için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="aad5c-182">Previously, Live Unit Testing was available only for .NET Framework applications.</span></span>

<span data-ttu-id="aad5c-183">Daha fazla bilgi için bkz. [Visual Studio ile Live Unit Testing](/visualstudio/test/live-unit-testing) ve [Live Unit Testing SSS](/visualstudio/test/live-unit-testing-faq).</span><span class="sxs-lookup"><span data-stu-id="aad5c-183">For more information, see [Live Unit Testing with Visual Studio](/visualstudio/test/live-unit-testing) and the [Live Unit Testing FAQ](/visualstudio/test/live-unit-testing-faq).</span></span>

### <a name="better-support-for-multiple-target-frameworks"></a><span data-ttu-id="aad5c-184">Birden çok hedef çerçeve için daha iyi destek</span><span class="sxs-lookup"><span data-stu-id="aad5c-184">Better support for multiple target frameworks</span></span>

<span data-ttu-id="aad5c-185">Birden çok hedef çerçeve için bir proje oluşturuyorsanız, artık üst düzey menüden hedef platformu seçebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="aad5c-185">If you're building a project for multiple target frameworks, you can now select the target platform from the top-level menu.</span></span> <span data-ttu-id="aad5c-186">Aşağıdaki şekilde, SCD1 adlı bir proje 64-bit macOS X 10,11 (`osx.10.11-x64`) ve 64-bit Windows 10/Windows Server 2016 (`win10-x64`) hedeflerini hedefliyor.</span><span class="sxs-lookup"><span data-stu-id="aad5c-186">In the following figure, a project named SCD1 targets 64-bit macOS X 10.11 (`osx.10.11-x64`) and 64-bit Windows 10/Windows Server 2016 (`win10-x64`).</span></span> <span data-ttu-id="aad5c-187">Bu durumda bir hata ayıklama yapısı çalıştırmak için proje düğmesini seçmeden önce hedef Framework 'ü seçebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="aad5c-187">You can select the target framework before selecting the project button, in this case to run a debug build.</span></span>

![Proje oluşturulurken hedef çerçeve seçimini gösteren ekran görüntüsü.](./media/dotnet-core-2-0/target-framework-selection.png)

### <a name="side-by-side-support-for-net-core-sdks"></a><span data-ttu-id="aad5c-189">.NET Core SDK 'Ları için yan yana destek</span><span class="sxs-lookup"><span data-stu-id="aad5c-189">Side-by-side support for .NET Core SDKs</span></span>

<span data-ttu-id="aad5c-190">Artık .NET Core SDK Visual Studio 'dan bağımsız olarak yükleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="aad5c-190">You can now install the .NET Core SDK independently of Visual Studio.</span></span> <span data-ttu-id="aad5c-191">Bu, Visual Studio 'nun tek bir sürümünün .NET Core 'un farklı sürümlerini hedefleyen projeler oluşturmasına olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="aad5c-191">This makes it possible for a single version of Visual Studio to build projects that target different versions of .NET Core.</span></span> <span data-ttu-id="aad5c-192">Daha önce, Visual Studio ve .NET Core SDK sıkı bir şekilde bağlanmış. Visual Studio 'nun belirli bir sürümüne eşlik eden belirli bir SDK sürümü.</span><span class="sxs-lookup"><span data-stu-id="aad5c-192">Previously, Visual Studio and the .NET Core SDK were tightly coupled; a particular version of the SDK accompanied a particular version of Visual Studio.</span></span>

## <a name="documentation-improvements"></a><span data-ttu-id="aad5c-193">Belge geliştirmeleri</span><span class="sxs-lookup"><span data-stu-id="aad5c-193">Documentation improvements</span></span>

### <a name="net-application-architecture"></a><span data-ttu-id="aad5c-194">.NET uygulama mimarisi</span><span class="sxs-lookup"><span data-stu-id="aad5c-194">.NET Application Architecture</span></span>

<span data-ttu-id="aad5c-195">[.NET uygulama mimarisi](https://dotnet.microsoft.com/learn/dotnet/architecture-guides) , oluşturmak için .net kullanırken rehberlik, en iyi uygulamalar ve örnek uygulamalar sağlayan bir dizi e-kitap için erişmenizi sağlar:</span><span class="sxs-lookup"><span data-stu-id="aad5c-195">[.NET Application Architecture](https://dotnet.microsoft.com/learn/dotnet/architecture-guides) gives you access to a set of e-books that provide guidance, best practices, and sample applications when using .NET to build:</span></span>

- [<span data-ttu-id="aad5c-196">Mikro hizmetler ve Docker Kapsayıcıları</span><span class="sxs-lookup"><span data-stu-id="aad5c-196">Microservices and Docker containers</span></span>](../../architecture/microservices/index.md)
- [<span data-ttu-id="aad5c-197">ASP.NET ile Web uygulamaları</span><span class="sxs-lookup"><span data-stu-id="aad5c-197">Web applications with ASP.NET</span></span>](../../architecture/modern-web-apps-azure/index.md)
- [<span data-ttu-id="aad5c-198">Xamarin ile mobil uygulamalar</span><span class="sxs-lookup"><span data-stu-id="aad5c-198">Mobile applications with Xamarin</span></span>](/xamarin/xamarin-forms/enterprise-application-patterns/index)
- [<span data-ttu-id="aad5c-199">Azure ile buluta dağıtılan uygulamalar</span><span class="sxs-lookup"><span data-stu-id="aad5c-199">Applications that are deployed to the Cloud with Azure</span></span>](/azure/architecture/reference-architectures/index)

## <a name="see-also"></a><span data-ttu-id="aad5c-200">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="aad5c-200">See also</span></span>

- [<span data-ttu-id="aad5c-201">ASP.NET Core 2,0 ' deki yenilikler</span><span class="sxs-lookup"><span data-stu-id="aad5c-201">What's new in ASP.NET Core 2.0</span></span>](/aspnet/core/aspnetcore-2.0)
