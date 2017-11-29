---
title: .NET Core 2. 0 ' yenilikler nelerdir?
description: ".NET Core bulunan yeni özellikler hakkında bilgi edinin."
keywords: .NET, .NET core
author: rpetrusha
ms.author: ronpet
ms.date: 08/13/2017
ms.topic: article
ms.prod: .net-core
ms.openlocfilehash: e54cabe67558300b5c5fb9552d78397850d4c782
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="whats-new-in-net-core"></a><span data-ttu-id="bf162-104">.NET Core yenilikler nelerdir?</span><span class="sxs-lookup"><span data-stu-id="bf162-104">What's new in .NET Core</span></span>

<span data-ttu-id="bf162-105">.NET core 2.0 aşağıdaki alanlarda geliştirmeler ve yeni özellikleri içerir:</span><span class="sxs-lookup"><span data-stu-id="bf162-105">.NET Core 2.0 includes enhancements and new features in the following areas:</span></span>

- [<span data-ttu-id="bf162-106">Araçları</span><span class="sxs-lookup"><span data-stu-id="bf162-106">Tooling</span></span>](#tooling)
- [<span data-ttu-id="bf162-107">Dil desteği</span><span class="sxs-lookup"><span data-stu-id="bf162-107">Language support</span></span>](#language-support)
- [<span data-ttu-id="bf162-108">Platform geliştirmeleri</span><span class="sxs-lookup"><span data-stu-id="bf162-108">Platform improvements</span></span>](#platform-improvements)
- [<span data-ttu-id="bf162-109">API değişiklikleri</span><span class="sxs-lookup"><span data-stu-id="bf162-109">API changes</span></span>](#api-changes-and-library-support)
- [<span data-ttu-id="bf162-110">Visual Studio tümleştirmesi</span><span class="sxs-lookup"><span data-stu-id="bf162-110">Visual Studio integration</span></span>](#visual-studio-integration)
- [<span data-ttu-id="bf162-111">Belge geliştirmeleri</span><span class="sxs-lookup"><span data-stu-id="bf162-111">Documentation improvements</span></span>](#documentation-improvements)

## <a name="tooling"></a><span data-ttu-id="bf162-112">Araçları</span><span class="sxs-lookup"><span data-stu-id="bf162-112">Tooling</span></span>

### <a name="dotnet-restore-runs-implicitly"></a><span data-ttu-id="bf162-113">DotNet geri yükleme örtük olarak çalışır</span><span class="sxs-lookup"><span data-stu-id="bf162-113">dotnet restore runs implicitly</span></span>

<span data-ttu-id="bf162-114">.NET Core önceki sürümlerini çalıştıran gerekiyordu [dotnet geri yükleme](../tools/dotnet-restore.md) yeni bir proje ile oluşturulan hemen sonra bağımlılıklarını karşıdan yüklemek için komut [dotnet yeni](../tools/dotnet-new.md) yanı sıra her komut, Yeni bir bağımlılık projenize eklenir.</span><span class="sxs-lookup"><span data-stu-id="bf162-114">In previous versions of .NET Core, you had to run the [dotnet restore](../tools/dotnet-restore.md) command to download dependencies immediately after you created a new project with the [dotnet new](../tools/dotnet-new.md) command, as well as whenever you added a new dependency to your project.</span></span>

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

<span data-ttu-id="bf162-115">Ayrıca otomatik çağrılmasını devre dışı bırakabilirsiniz `dotnet restore` geçirerek `--no-restore` geçiş `new`, `run`, `build`, `publish`, `pack`, ve `test` komutları.</span><span class="sxs-lookup"><span data-stu-id="bf162-115">You can also disable the automatic invocation of `dotnet restore` by passing the `--no-restore` switch to the `new`, `run`, `build`, `publish`, `pack`, and `test` commands.</span></span> 

### <a name="retargeting-to-net-core-20"></a><span data-ttu-id="bf162-116">.NET Core 2.0 yeniden hedefleme</span><span class="sxs-lookup"><span data-stu-id="bf162-116">Retargeting to .NET Core 2.0</span></span>

<span data-ttu-id="bf162-117">.NET Core 2.0 SDK'sı yüklü ise, projeler, .NET Core 1.x .NET Core 2.0 yönlendirilebilir hedefleyin.</span><span class="sxs-lookup"><span data-stu-id="bf162-117">If the .NET Core 2.0 SDK is installed, projects that target .NET Core 1.x can be retargeted to .NET Core 2.0.</span></span>

<span data-ttu-id="bf162-118">.NET Core 2.0 yeniden hedefleyin için değerini değiştirerek proje dosyanızı düzenleyin `<TargetFramework>` öğesi (veya `<TargetFrameworks>` proje dosyanızda birden fazla hedef varsa öğe) 2.0 1.x gelen:</span><span class="sxs-lookup"><span data-stu-id="bf162-118">To retarget to .NET Core 2.0, edit your project file by changing the value of the `<TargetFramework>` element (or the `<TargetFrameworks>` element if you have more than one target in your project file) from 1.x to 2.0:</span></span>

```xml
<PropertyGroup>
    <TargetFramework>netcoreapp2.0</TargetFramework>
 </PropertyGroup>
```

<span data-ttu-id="bf162-119">Ayrıca aynı şekilde .NET standart 2.0 için .NET standart kitaplıkları yeniden hedefleyin da:</span><span class="sxs-lookup"><span data-stu-id="bf162-119">You can also retarget .NET Standard libraries to .NET Standard 2.0 the same way:</span></span>

```xml
<PropertyGroup>
    <TargetFramework>netstandard2.0</TargetFramework>
 </PropertyGroup>
```

<span data-ttu-id="bf162-120">Projeniz .NET Core 2.0 geçirme hakkında daha fazla bilgi için bkz: [ASP.NET çekirdek geçirme 1.x ASP.NET Core 2.0](/aspnet/core/migration/1x-to-2x/index).</span><span class="sxs-lookup"><span data-stu-id="bf162-120">For more information about migrating your project to .NET Core 2.0, see [Migrating from ASP.NET Core 1.x to ASP.NET Core 2.0](/aspnet/core/migration/1x-to-2x/index).</span></span>

## <a name="language-support"></a><span data-ttu-id="bf162-121">Dil desteği</span><span class="sxs-lookup"><span data-stu-id="bf162-121">Language support</span></span>

<span data-ttu-id="bf162-122">C# ve F # destekleyen ek olarak, .NET Core 2.0 Visual Basic de destekler.</span><span class="sxs-lookup"><span data-stu-id="bf162-122">In addition to supporting C# and F#, .NET Core 2.0 also supports Visual Basic.</span></span>

### <a name="visual-basic"></a><span data-ttu-id="bf162-123">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="bf162-123">Visual Basic</span></span>

<span data-ttu-id="bf162-124">Sürüm 2.0 .NET Core artık Visual Basic 2017 destekler.</span><span class="sxs-lookup"><span data-stu-id="bf162-124">With version 2.0, .NET Core now supports Visual Basic 2017.</span></span> <span data-ttu-id="bf162-125">Visual Basic aşağıdaki proje türleri oluşturmak için kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="bf162-125">You can use Visual Basic to create the following project types:</span></span>

- <span data-ttu-id="bf162-126">.NET core konsol uygulamaları</span><span class="sxs-lookup"><span data-stu-id="bf162-126">.NET Core console apps</span></span>
- <span data-ttu-id="bf162-127">.NET core sınıf kitaplıkları</span><span class="sxs-lookup"><span data-stu-id="bf162-127">.NET Core class libraries</span></span>
- <span data-ttu-id="bf162-128">Standart .NET sınıf kitaplıkları</span><span class="sxs-lookup"><span data-stu-id="bf162-128">.NET Standard class libraries</span></span>
- <span data-ttu-id="bf162-129">.NET core birim testi projelerini</span><span class="sxs-lookup"><span data-stu-id="bf162-129">.NET Core unit test projects</span></span>
- <span data-ttu-id="bf162-130">.NET core xUnit test projeleri</span><span class="sxs-lookup"><span data-stu-id="bf162-130">.NET Core xUnit test projects</span></span>

<span data-ttu-id="bf162-131">Örneğin, bir Visual Basic "Hello World" uygulaması oluşturmak için komut satırından aşağıdaki adımları uygulayın:</span><span class="sxs-lookup"><span data-stu-id="bf162-131">For example, to create a Visual Basic "Hello World" application, do the following steps from the command line:</span></span>

1. <span data-ttu-id="bf162-132">Bir konsol penceresi açın, projeniz için bir dizin oluşturun ve geçerli dizin yapın.</span><span class="sxs-lookup"><span data-stu-id="bf162-132">Open a console window, create a directory for your project, and make it the current directory.</span></span>

1. <span data-ttu-id="bf162-133">Aşağıdaki komutu girin `dotnet new console -lang vb`.</span><span class="sxs-lookup"><span data-stu-id="bf162-133">Enter the command `dotnet new console -lang vb`.</span></span>

   <span data-ttu-id="bf162-134">Komut bir proje dosyası ile oluşturur bir `.vbproj` adlı bir Visual Basic kaynak kodu dosyasının yanı sıra dosya uzantısı, *Program.vb*.</span><span class="sxs-lookup"><span data-stu-id="bf162-134">The command creates a project file with a `.vbproj` file extension, along with a Visual Basic source code file named *Program.vb*.</span></span> <span data-ttu-id="bf162-135">Bu dosyayı "Hello World!" dizesini yazmak için kaynak kodunu içerir</span><span class="sxs-lookup"><span data-stu-id="bf162-135">This file contains the source code to write the string "Hello World!"</span></span> <span data-ttu-id="bf162-136">Konsol penceresine.</span><span class="sxs-lookup"><span data-stu-id="bf162-136">to the console window.</span></span>

1.  <span data-ttu-id="bf162-137">Aşağıdaki komutu girin `dotnet run`.</span><span class="sxs-lookup"><span data-stu-id="bf162-137">Enter the command `dotnet run`.</span></span> <span data-ttu-id="bf162-138">[.NET Core CLI araçlarını](../tools/index.md) otomatik olarak derleyin ve "Hello World!" iletisi görüntüler ve uygulamanın yürütme</span><span class="sxs-lookup"><span data-stu-id="bf162-138">The [.NET Core CLI tools](../tools/index.md) automatically compile and execute the application, which displays the message "Hello World!"</span></span> <span data-ttu-id="bf162-139">Konsol penceresinde.</span><span class="sxs-lookup"><span data-stu-id="bf162-139">in the console window.</span></span>

### <a name="support-for-c-71"></a><span data-ttu-id="bf162-140">C# 7.1 desteği</span><span class="sxs-lookup"><span data-stu-id="bf162-140">Support for C# 7.1</span></span>

<span data-ttu-id="bf162-141">.NET core 2.0 C# gibi yeni özellikler sayısı ekleyen 7.1, destekler:</span><span class="sxs-lookup"><span data-stu-id="bf162-141">.NET Core 2.0 supports C# 7.1, which adds a number of new features, including:</span></span>

- <span data-ttu-id="bf162-142">`Main` Yöntemi, uygulama giriş noktası işaretlenir ile [zaman uyumsuz](../../csharp/language-reference/keywords/async.md) anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="bf162-142">The `Main` method, the application entry point, can be marked with the [async](../../csharp/language-reference/keywords/async.md) keyword.</span></span>
- <span data-ttu-id="bf162-143">Tanımlama grubu adları sonuçlandı.</span><span class="sxs-lookup"><span data-stu-id="bf162-143">Inferred tuple names.</span></span>
- <span data-ttu-id="bf162-144">Varsayılan ifadeler.</span><span class="sxs-lookup"><span data-stu-id="bf162-144">Default expressions.</span></span>

<!-- For more information see [link to C# what's new](url). -->

## <a name="platform-improvements"></a><span data-ttu-id="bf162-145">Platform geliştirmeleri</span><span class="sxs-lookup"><span data-stu-id="bf162-145">Platform improvements</span></span>

<span data-ttu-id="bf162-146">.NET core 2.0, .NET Core yüklemek kolaylaştıran özellikler içerir ve desteklenen işletim sistemleri üzerinde kullanmak için.</span><span class="sxs-lookup"><span data-stu-id="bf162-146">.NET Core 2.0 includes a number of features that make it easier to install .NET Core and to use it on supported operating systems.</span></span>

### <a name="net-core-for-linux-is-a-single-implementation"></a><span data-ttu-id="bf162-147">.NET core Linux için tek bir uygulamasıdır</span><span class="sxs-lookup"><span data-stu-id="bf162-147">.NET Core for Linux is a single implementation</span></span>

<span data-ttu-id="bf162-148">.NET core 2.0 birden çok Linux dağıtımları üzerinde çalışan tek bir Linux uygulama sunar.</span><span class="sxs-lookup"><span data-stu-id="bf162-148">.NET Core 2.0 offers a single Linux implementation that works on multiple Linux distributions.</span></span> <span data-ttu-id="bf162-149">.NET core 1.x gereken bir dağıtım özgü Linux uygulamasını indirin.</span><span class="sxs-lookup"><span data-stu-id="bf162-149">.NET Core 1.x required that you download a distribution-specific Linux implementation.</span></span>

<span data-ttu-id="bf162-150">Ayrıca, tek bir işletim sistemi olarak Linux hedef uygulamaları geliştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bf162-150">You can also develop apps that target Linux as a single operating system.</span></span> <span data-ttu-id="bf162-151">.NET core 1.x gerekli her Linux dağıtım ayrı olarak hedefleyin.</span><span class="sxs-lookup"><span data-stu-id="bf162-151">.NET Core 1.x required that you target each Linux distribution separately.</span></span>

### <a name="support-for-the-apple-cryptographic-libraries"></a><span data-ttu-id="bf162-152">Apple şifreleme kitaplıkları için desteği</span><span class="sxs-lookup"><span data-stu-id="bf162-152">Support for the Apple cryptographic libraries</span></span>

<span data-ttu-id="bf162-153">.NET core üzerinde macOS 1.x OpenSSL Toolkit'in şifreleme kitaplığı gerekli.</span><span class="sxs-lookup"><span data-stu-id="bf162-153">.NET Core 1.x on macOS required the OpenSSL toolkit's cryptographic library.</span></span> <span data-ttu-id="bf162-154">.NET core 2.0 Apple şifreleme kitaplıklarını kullanır ve böylece yüklemek gerek OpenSSL, gerektirmez.</span><span class="sxs-lookup"><span data-stu-id="bf162-154">.NET Core 2.0 uses the Apple cryptographic libraries and doesn't require OpenSSL, so you no longer need to install it.</span></span>

## <a name="api-changes-and-library-support"></a><span data-ttu-id="bf162-155">API değişiklikleri ve kitaplık desteği</span><span class="sxs-lookup"><span data-stu-id="bf162-155">API changes and library support</span></span>

### <a name="support-for-net-standard-20"></a><span data-ttu-id="bf162-156">.NET standart 2.0 desteği</span><span class="sxs-lookup"><span data-stu-id="bf162-156">Support for .NET Standard 2.0</span></span>

<span data-ttu-id="bf162-157">.NET standart bu standart sürümü ile uyumlu .NET uygulamaları üzerinde kullanılabilir olması gereken API sürümü tutulan kümesini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="bf162-157">The .NET Standard defines a versioned set of APIs that must be available on .NET implementations that comply with that version of the standard.</span></span> <span data-ttu-id="bf162-158">.NET standart kitaplığı geliştiricileri yöneliktir.</span><span class="sxs-lookup"><span data-stu-id="bf162-158">The .NET Standard is targeted at library developers.</span></span> <span data-ttu-id="bf162-159">Her .NET uygulaması .NET standart sürümü hedefleyen bir kitaplık için kullanılabilir olan işlevselliği garanti amaçlar.</span><span class="sxs-lookup"><span data-stu-id="bf162-159">It aims to guarantee the functionality that is available to a library that targets a version of the .NET Standard on each .NET implementation.</span></span> <span data-ttu-id="bf162-160">.NET core 1.x .NET Standard sürüm 1.6 destekler; .NET Core 2.0 .NET standart 2.0 en son sürümünü destekler.</span><span class="sxs-lookup"><span data-stu-id="bf162-160">.NET Core 1.x supports the .NET Standard version 1.6; .NET Core 2.0 supports the latest version, .NET Standard 2.0.</span></span> <span data-ttu-id="bf162-161">Daha fazla bilgi için bkz: [.NET standart](../../standard/net-standard.md).</span><span class="sxs-lookup"><span data-stu-id="bf162-161">For more information, see [.NET Standard](../../standard/net-standard.md).</span></span>

<span data-ttu-id="bf162-162">.NET standart 2.0, .NET standart 1.6 içinde bulunmamaktaydı daha üzerinde 20.000 daha fazla API'leri içerir.</span><span class="sxs-lookup"><span data-stu-id="bf162-162">.NET Standard 2.0 includes over 20,000 more APIs than were available in the .NET Standard 1.6.</span></span> <span data-ttu-id="bf162-163">Bu çoğunu .NET standart içine Xamarin ve .NET Framework için ortak API'ler ekleme yüzey alanını sonuçları genişletilmiştir.</span><span class="sxs-lookup"><span data-stu-id="bf162-163">Much of this expanded surface area results from incorporating APIs that are common to the .NET Framework and Xamarin into .NET Standard.</span></span>

<span data-ttu-id="bf162-164">.NET standart 2.0 mevcut API çağrısı koşuluyla standart 2.0 .NET sınıf kitaplıkları da .NET Framework sınıf kitaplıkları başvuruda bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="bf162-164">.NET Standard 2.0 class libraries can also reference .NET Framework class libraries, provided that they call APIs that are present in the .NET Standard 2.0.</span></span> <span data-ttu-id="bf162-165">.NET Framework kitaplıkların hiçbir yeniden derlenmek gereklidir.</span><span class="sxs-lookup"><span data-stu-id="bf162-165">No recompilation of the .NET Framework libraries is required.</span></span>

<span data-ttu-id="bf162-166">Son sürümünden bu yana .NET standart 1.6 için .NET standart eklenmiş API'ları listesi için bkz: [.NET standart 2.0 vs. 1.6](https://raw.githubusercontent.com/dotnet/standard/master/docs/versions/netstandard2.0_diff.md).</span><span class="sxs-lookup"><span data-stu-id="bf162-166">For a list of the APIs that have been added to the .NET Standard since its last version, the .NET Standard 1.6, see [.NET Standard 2.0 vs. 1.6](https://raw.githubusercontent.com/dotnet/standard/master/docs/versions/netstandard2.0_diff.md).</span></span>

### <a name="expanded-surface-area"></a><span data-ttu-id="bf162-167">Yüzey alanını genişletilmiş</span><span class="sxs-lookup"><span data-stu-id="bf162-167">Expanded surface area</span></span>

<span data-ttu-id="bf162-168">.NET Core 2.0 kullanılabilen API'lerin toplam sayısı birden fazla .NET Core 1.1 karşılaştırıldığında iki katına.</span><span class="sxs-lookup"><span data-stu-id="bf162-168">The total number of APIs available on .NET Core 2.0 has more than doubled in comparison with .NET Core 1.1.</span></span>

<span data-ttu-id="bf162-169">İle [Windows Uyumluluk Paketi](../porting/windows-compat-pack.md) .NET Framework'bağlantı noktası oluşturma da duruma çok daha kolaydır.</span><span class="sxs-lookup"><span data-stu-id="bf162-169">And with the [Windows Compatibility Pack](../porting/windows-compat-pack.md) porting from .NET Framework has also become much simpler.</span></span>

### <a name="support-for-net-framework-libraries"></a><span data-ttu-id="bf162-170">.NET Framework kitaplıkları için desteği</span><span class="sxs-lookup"><span data-stu-id="bf162-170">Support for .NET Framework libraries</span></span>

<span data-ttu-id="bf162-171">.NET core kodu mevcut NuGet paketleri de dahil olmak üzere var olan .NET Framework kitaplıkları başvuruda bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="bf162-171">.NET Core code can reference existing .NET Framework libraries, including existing NuGet packages.</span></span> <span data-ttu-id="bf162-172">Kitaplıkları .NET Standard sürümünde bulunan API'lerini kullanmanız gerektiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="bf162-172">Note that the libraries must use APIs that are found in .NET Standard.</span></span>

## <a name="visual-studio-integration"></a><span data-ttu-id="bf162-173">Visual Studio tümleştirmesi</span><span class="sxs-lookup"><span data-stu-id="bf162-173">Visual Studio integration</span></span>

<span data-ttu-id="bf162-174">Visual Studio 2017 sürüm 15.3 ve bazı durumlarda Mac için Visual Studio birkaç .NET Core geliştiricilere yönelik önemli geliştirmeler sunar.</span><span class="sxs-lookup"><span data-stu-id="bf162-174">Visual Studio 2017 version 15.3 and in some cases Visual Studio for Mac offer a number of significant enhancements for .NET Core developers.</span></span>

### <a name="retargeting-net-core-apps-and-net-standard-libraries"></a><span data-ttu-id="bf162-175">Yeniden hedefleme .NET Core uygulamaları ve .NET standart kitaplıkları</span><span class="sxs-lookup"><span data-stu-id="bf162-175">Retargeting .NET Core apps and .NET Standard libraries</span></span>

<span data-ttu-id="bf162-176">.NET Core 2.0 SDK'yı yüklediyseniz, .NET Core 1.x projeleri .NET standart 2.0 için .NET Core 2.0 ve .NET standart 1.x kitaplıklara yeniden hedefleyin.</span><span class="sxs-lookup"><span data-stu-id="bf162-176">If the .NET Core 2.0 SDK is installed, you can retarget .NET Core 1.x projects to .NET Core 2.0 and .NET Standard 1.x libraries to .NET Standard 2.0.</span></span>

<span data-ttu-id="bf162-177">Visual Studio, projenizin hedefini için açmanız **uygulama** projenin özellikleri iletişim kutusu ve değişiklik sekmesinde **hedef framework** değeri **.NET Core 2.0** veya **.NET standart 2.0**.</span><span class="sxs-lookup"><span data-stu-id="bf162-177">To retarget your project in Visual Studio, you open the **Application** tab of the project's properties dialog and change the **Target framework** value to **.NET Core 2.0** or **.NET Standard 2.0**.</span></span> <span data-ttu-id="bf162-178">Ayrıca, projeye sağ tıklayıp seçerek değiştirebilirsiniz **Düzenle \*.csproj dosya** seçeneği.</span><span class="sxs-lookup"><span data-stu-id="bf162-178">You can also change it by right-clicking on the project and selecting the **Edit \*.csproj file** option.</span></span> <span data-ttu-id="bf162-179">Daha fazla bilgi için bkz: [Tooling](#tooling) bu konunun önceki kısımlarında.</span><span class="sxs-lookup"><span data-stu-id="bf162-179">For more information, see the [Tooling](#tooling) section earlier in this topic.</span></span>

### <a name="live-unit-testing-support-for-net-core"></a><span data-ttu-id="bf162-180">.NET Core için Live Unit Testing</span><span class="sxs-lookup"><span data-stu-id="bf162-180">Live Unit Testing support for .NET Core</span></span>

<span data-ttu-id="bf162-181">Kodunuzu değiştirmek her birim testi Canlı otomatik olarak arka planda tüm etkilenen ünite testleri çalıştırır ve sonuçları ve kod kapsamı Visual Studio ortamında canlı görüntüler.</span><span class="sxs-lookup"><span data-stu-id="bf162-181">Whenever you modify your code, Live Unit Testing automatically runs any affected unit tests in the background and displays the results and code coverage live in the Visual Studio environment.</span></span> <span data-ttu-id="bf162-182">.NET core 2.0 artık canlı birim testi destekler.</span><span class="sxs-lookup"><span data-stu-id="bf162-182">.NET Core 2.0 now supports Live Unit Testing.</span></span> <span data-ttu-id="bf162-183">Daha önce Canlı birim testi yalnızca .NET Framework uygulamaları için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="bf162-183">Previously, Live Unit Testing was available only for .NET Framework applications.</span></span>

<span data-ttu-id="bf162-184">Daha fazla bilgi için bkz: [Canlı birim testi Visual Studio 2017](/visualstudio/test/live-unit-testing) ve [Canlı birim testi SSS](/visualstudio/test/live-unit-testing-faq).</span><span class="sxs-lookup"><span data-stu-id="bf162-184">For more information, see [Live Unit Testing with Visual Studio 2017](/visualstudio/test/live-unit-testing) and the [Live Unit Testing FAQ](/visualstudio/test/live-unit-testing-faq).</span></span>

### <a name="better-support-for-multiple-target-frameworks"></a><span data-ttu-id="bf162-185">Birden çok hedef çerçeve için daha iyi destek</span><span class="sxs-lookup"><span data-stu-id="bf162-185">Better support for multiple target frameworks</span></span>

<span data-ttu-id="bf162-186">Birden çok hedef çerçeve için bir proje oluşturuyorsanız, üst düzey menüsünden artık hedef platformu seçebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bf162-186">If you're building a project for multiple target frameworks, you can now select the target platform from the top-level menu.</span></span> <span data-ttu-id="bf162-187">Aşağıdaki şekilde, 64-bit Mac OS X 10.11 sürümünü SCD1 adlı projesi hedefler (`osx.10.11-x64`) ve 64 bit Windows 10/Windows Server 2016 (`win10-x64`).</span><span class="sxs-lookup"><span data-stu-id="bf162-187">In the following figure, a project named SCD1 targets 64-bit Mac OS X 10.11 (`osx.10.11-x64`) and 64-bit Windows 10/Windows Server 2016 (`win10-x64`).</span></span> <span data-ttu-id="bf162-188">Proje düğmesi, bu durumda bir hata ayıklama derlemesini çalışmasına seçmeden önce hedef Framework'ü seçebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bf162-188">You can select the target framework before selecting the project button, in this case to run a debug build.</span></span>

![Proje derleme hedef Framework'ü seçme](media/multitarget.png)

### <a name="side-by-side-support-for-net-core-sdks"></a><span data-ttu-id="bf162-190">.NET Core SDK'ları için yan yana desteği</span><span class="sxs-lookup"><span data-stu-id="bf162-190">Side-by-side support for .NET Core SDKs</span></span>

<span data-ttu-id="bf162-191">Visual Studio bağımsız olarak .NET Core SDK şimdi yükleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bf162-191">You can now install the .NET Core SDK independently of Visual Studio.</span></span> <span data-ttu-id="bf162-192">Bu, tek bir .NET Core bu hedef farklı sürümlerini projeler derlemek için Visual Studio sürümü için mümkün kılar.</span><span class="sxs-lookup"><span data-stu-id="bf162-192">This makes it possible for a single version of Visual Studio to build projects that target different versions of .NET Core.</span></span> <span data-ttu-id="bf162-193">Daha önce Visual Studio ve .NET Core SDK sıkı şekilde bağlı; belirli bir SDK sürümü Visual Studio belirli bir sürümü eşlik.</span><span class="sxs-lookup"><span data-stu-id="bf162-193">Previously, Visual Studio and the .NET Core SDK were tightly coupled; a particular version of the SDK accompanied a particular version of Visual Studio.</span></span>

## <a name="documentation-improvements"></a><span data-ttu-id="bf162-194">Belge geliştirmeleri</span><span class="sxs-lookup"><span data-stu-id="bf162-194">Documentation improvements</span></span>

### <a name="net-application-architecture"></a><span data-ttu-id="bf162-195">.NET uygulama mimarisi</span><span class="sxs-lookup"><span data-stu-id="bf162-195">.NET Application Architecture</span></span>

<span data-ttu-id="bf162-196">[.NET uygulama mimarisi](https://www.microsoft.com/net/learn/architecture) en iyi yöntemler ve .NET derleme için kullanırken uygulamaları örnek kılavuzluk, e-kitap kümesine erişim sağlar:</span><span class="sxs-lookup"><span data-stu-id="bf162-196">[.NET Application Architecture](https://www.microsoft.com/net/learn/architecture) gives you access to a set of e-books that provide guidance, best practices, and sample applications when using .NET to build:</span></span>

- <span data-ttu-id="bf162-197">Mikro ve Docker kapsayıcıları.</span><span class="sxs-lookup"><span data-stu-id="bf162-197">Microservices and Docker containers.</span></span>
- <span data-ttu-id="bf162-198">ASP.NET ile Web uygulamaları.</span><span class="sxs-lookup"><span data-stu-id="bf162-198">Web applications with ASP.NET.</span></span>
- <span data-ttu-id="bf162-199">Xamarin ile mobil uygulamaları.</span><span class="sxs-lookup"><span data-stu-id="bf162-199">Mobile applications with Xamarin.</span></span>
- <span data-ttu-id="bf162-200">Azure ile bulutta dağıtılan uygulamalar.</span><span class="sxs-lookup"><span data-stu-id="bf162-200">Applications that are deployed to the Cloud with Azure.</span></span>

## <a name="see-also"></a><span data-ttu-id="bf162-201">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bf162-201">See also</span></span>
 [<span data-ttu-id="bf162-202">ASP.NET Core 2. 0 ' yenilikler nelerdir?</span><span class="sxs-lookup"><span data-stu-id="bf162-202">What's new in ASP.NET Core 2.0</span></span>](/aspnet/core/aspnetcore-2.0)
