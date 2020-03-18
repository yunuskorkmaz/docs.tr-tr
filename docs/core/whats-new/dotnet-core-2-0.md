---
title: ​.NET Core 2.0’deki yenilikler
description: .NET Core'da bulunan yeni özellikler hakkında bilgi edinin.
ms.date: 08/13/2017
ms.openlocfilehash: 115b3adc72b6798c6a7bac9cc18044a8822808a6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79398834"
---
# <a name="whats-new-in-net-core-20"></a><span data-ttu-id="4ffc1-103">​.NET Core 2.0’deki yenilikler</span><span class="sxs-lookup"><span data-stu-id="4ffc1-103">What's new in .NET Core 2.0</span></span>

<span data-ttu-id="4ffc1-104">.NET Core 2.0 aşağıdaki alanlarda ki geliştirmeleri ve yeni özellikleri içerir:</span><span class="sxs-lookup"><span data-stu-id="4ffc1-104">.NET Core 2.0 includes enhancements and new features in the following areas:</span></span>

- [<span data-ttu-id="4ffc1-105">Araçlar</span><span class="sxs-lookup"><span data-stu-id="4ffc1-105">Tooling</span></span>](#tooling)
- [<span data-ttu-id="4ffc1-106">Dil desteği</span><span class="sxs-lookup"><span data-stu-id="4ffc1-106">Language support</span></span>](#language-support)
- [<span data-ttu-id="4ffc1-107">Platform geliştirmeleri</span><span class="sxs-lookup"><span data-stu-id="4ffc1-107">Platform improvements</span></span>](#platform-improvements)
- [<span data-ttu-id="4ffc1-108">API değişiklikleri</span><span class="sxs-lookup"><span data-stu-id="4ffc1-108">API changes</span></span>](#api-changes-and-library-support)
- [<span data-ttu-id="4ffc1-109">Visual Studio ile tümleştirme</span><span class="sxs-lookup"><span data-stu-id="4ffc1-109">Visual Studio integration</span></span>](#visual-studio-integration)
- [<span data-ttu-id="4ffc1-110">Dokümantasyon geliştirmeleri</span><span class="sxs-lookup"><span data-stu-id="4ffc1-110">Documentation improvements</span></span>](#documentation-improvements)

## <a name="tooling"></a><span data-ttu-id="4ffc1-111">Araçlar</span><span class="sxs-lookup"><span data-stu-id="4ffc1-111">Tooling</span></span>

### <a name="dotnet-restore-runs-implicitly"></a><span data-ttu-id="4ffc1-112">dotnet geri yükleme örtülü çalışır</span><span class="sxs-lookup"><span data-stu-id="4ffc1-112">dotnet restore runs implicitly</span></span>

<span data-ttu-id="4ffc1-113">.NET Core'un önceki sürümlerinde, [dotnet](../tools/dotnet-restore.md) yeni komutuyla yeni bir proje oluşturduktan hemen sonra ve projenize yeni bir bağımlılık eklediğinizde bağımlılıkları indirmek için [dotnet](../tools/dotnet-new.md) geri yükleme komutunu çalıştırmanız gerekiyordu.</span><span class="sxs-lookup"><span data-stu-id="4ffc1-113">In previous versions of .NET Core, you had to run the [dotnet restore](../tools/dotnet-restore.md) command to download dependencies immediately after you created a new project with the [dotnet new](../tools/dotnet-new.md) command, as well as whenever you added a new dependency to your project.</span></span>

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

<span data-ttu-id="4ffc1-114">`--no-restore` Ayrıca, `new`, , `run` `build` `publish` `pack`, , , ve `test` komutları anahtarı `dotnet restore` geçirerek otomatik çağırma devre dışı leyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4ffc1-114">You can also disable the automatic invocation of `dotnet restore` by passing the `--no-restore` switch to the `new`, `run`, `build`, `publish`, `pack`, and `test` commands.</span></span>

### <a name="retargeting-to-net-core-20"></a><span data-ttu-id="4ffc1-115">.NET Core 2.0'a yeniden hedefleme</span><span class="sxs-lookup"><span data-stu-id="4ffc1-115">Retargeting to .NET Core 2.0</span></span>

<span data-ttu-id="4ffc1-116">.NET Core 2.0 SDK kuruluysa, .NET Core 1.x'i hedefleyen projeler .NET Core 2.0'a yeniden hedeflenebilir.</span><span class="sxs-lookup"><span data-stu-id="4ffc1-116">If the .NET Core 2.0 SDK is installed, projects that target .NET Core 1.x can be retargeted to .NET Core 2.0.</span></span>

<span data-ttu-id="4ffc1-117">.NET Core 2.0'ı yeniden hedeflemek için, öğenin `<TargetFramework>` (veya proje `<TargetFrameworks>` dosyanızda birden fazla hedefiniz varsa öğeyi) 1,x'ten 2.0'a değiştirerek proje dosyanızı düzenleme:</span><span class="sxs-lookup"><span data-stu-id="4ffc1-117">To retarget to .NET Core 2.0, edit your project file by changing the value of the `<TargetFramework>` element (or the `<TargetFrameworks>` element if you have more than one target in your project file) from 1.x to 2.0:</span></span>

```xml
<PropertyGroup>
    <TargetFramework>netcoreapp2.0</TargetFramework>
 </PropertyGroup>
```

<span data-ttu-id="4ffc1-118">.NET Standart kitaplıklarını aynı şekilde .NET Standart 2.0'a da yeniden hedefleyebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="4ffc1-118">You can also retarget .NET Standard libraries to .NET Standard 2.0 the same way:</span></span>

```xml
<PropertyGroup>
    <TargetFramework>netstandard2.0</TargetFramework>
 </PropertyGroup>
```

<span data-ttu-id="4ffc1-119">Projenizi .NET Core 2.0'a geçirme hakkında daha fazla bilgi ASP.NET [ASP.NET](/aspnet/core/migration/1x-to-2x/index)için bkz.</span><span class="sxs-lookup"><span data-stu-id="4ffc1-119">For more information about migrating your project to .NET Core 2.0, see [Migrating from ASP.NET Core 1.x to ASP.NET Core 2.0](/aspnet/core/migration/1x-to-2x/index).</span></span>

## <a name="language-support"></a><span data-ttu-id="4ffc1-120">Dil desteği</span><span class="sxs-lookup"><span data-stu-id="4ffc1-120">Language support</span></span>

<span data-ttu-id="4ffc1-121">C# ve F#'ı desteklemenin yanı sıra .NET Core 2.0 Visual Basic'i de destekler.</span><span class="sxs-lookup"><span data-stu-id="4ffc1-121">In addition to supporting C# and F#, .NET Core 2.0 also supports Visual Basic.</span></span>

### <a name="visual-basic"></a><span data-ttu-id="4ffc1-122">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="4ffc1-122">Visual Basic</span></span>

<span data-ttu-id="4ffc1-123">.NET Core, sürüm 2.0 ile Visual Basic 2017'yi destekliyor.</span><span class="sxs-lookup"><span data-stu-id="4ffc1-123">With version 2.0, .NET Core now supports Visual Basic 2017.</span></span> <span data-ttu-id="4ffc1-124">Aşağıdaki proje türlerini oluşturmak için Visual Basic'i kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="4ffc1-124">You can use Visual Basic to create the following project types:</span></span>

- <span data-ttu-id="4ffc1-125">.NET Core konsol uygulamaları</span><span class="sxs-lookup"><span data-stu-id="4ffc1-125">.NET Core console apps</span></span>
- <span data-ttu-id="4ffc1-126">.NET Çekirdek sınıf kitaplıkları</span><span class="sxs-lookup"><span data-stu-id="4ffc1-126">.NET Core class libraries</span></span>
- <span data-ttu-id="4ffc1-127">.NET Standart sınıf kitaplıkları</span><span class="sxs-lookup"><span data-stu-id="4ffc1-127">.NET Standard class libraries</span></span>
- <span data-ttu-id="4ffc1-128">.NET Çekirdek ünite test projeleri</span><span class="sxs-lookup"><span data-stu-id="4ffc1-128">.NET Core unit test projects</span></span>
- <span data-ttu-id="4ffc1-129">.NET Core xUnit test projeleri</span><span class="sxs-lookup"><span data-stu-id="4ffc1-129">.NET Core xUnit test projects</span></span>

<span data-ttu-id="4ffc1-130">Örneğin, Visual Basic "Hello World" uygulaması oluşturmak için komut satırından aşağıdaki adımları yapın:</span><span class="sxs-lookup"><span data-stu-id="4ffc1-130">For example, to create a Visual Basic "Hello World" application, do the following steps from the command line:</span></span>

1. <span data-ttu-id="4ffc1-131">Konsol penceresi açın, projeniz için bir dizin oluşturun ve geçerli dizini yapın.</span><span class="sxs-lookup"><span data-stu-id="4ffc1-131">Open a console window, create a directory for your project, and make it the current directory.</span></span>

1. <span data-ttu-id="4ffc1-132">Komutu `dotnet new console -lang vb`girin.</span><span class="sxs-lookup"><span data-stu-id="4ffc1-132">Enter the command `dotnet new console -lang vb`.</span></span>

   <span data-ttu-id="4ffc1-133">Komut, *Program.vb*adlı `.vbproj` Visual Basic kaynak kodu dosyasıyla birlikte dosya uzantısı olan bir proje dosyası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="4ffc1-133">The command creates a project file with a `.vbproj` file extension, along with a Visual Basic source code file named *Program.vb*.</span></span> <span data-ttu-id="4ffc1-134">Bu dosya "Merhaba Dünya!" dizesini yazmak için kaynak kodu içerir.</span><span class="sxs-lookup"><span data-stu-id="4ffc1-134">This file contains the source code to write the string "Hello World!"</span></span> <span data-ttu-id="4ffc1-135">konsol penceresine.</span><span class="sxs-lookup"><span data-stu-id="4ffc1-135">to the console window.</span></span>

1. <span data-ttu-id="4ffc1-136">Komutu `dotnet run`girin.</span><span class="sxs-lookup"><span data-stu-id="4ffc1-136">Enter the command `dotnet run`.</span></span> <span data-ttu-id="4ffc1-137">[.NET Core CLI,](../tools/index.md) "Hello World!" mesajını görüntüleyen uygulamayı otomatik olarak derler ve yürütür.</span><span class="sxs-lookup"><span data-stu-id="4ffc1-137">The [.NET Core CLI](../tools/index.md) automatically compiles and executes the application, which displays the message "Hello World!"</span></span> <span data-ttu-id="4ffc1-138">konsol penceresinde.</span><span class="sxs-lookup"><span data-stu-id="4ffc1-138">in the console window.</span></span>

### <a name="support-for-c-71"></a><span data-ttu-id="4ffc1-139">C# 7.1 desteği</span><span class="sxs-lookup"><span data-stu-id="4ffc1-139">Support for C# 7.1</span></span>

<span data-ttu-id="4ffc1-140">.NET Core 2.0, c# 7.1'i destekler ve bu özellikler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="4ffc1-140">.NET Core 2.0 supports C# 7.1, which adds a number of new features, including:</span></span>

- <span data-ttu-id="4ffc1-141">Yöntem, `Main` uygulama giriş noktası, [async](../../csharp/language-reference/keywords/async.md) anahtar sözcüğü ile işaretlenebilir.</span><span class="sxs-lookup"><span data-stu-id="4ffc1-141">The `Main` method, the application entry point, can be marked with the [async](../../csharp/language-reference/keywords/async.md) keyword.</span></span>
- <span data-ttu-id="4ffc1-142">Çıkarılan tuple adları.</span><span class="sxs-lookup"><span data-stu-id="4ffc1-142">Inferred tuple names.</span></span>
- <span data-ttu-id="4ffc1-143">Varsayılan ifadeler.</span><span class="sxs-lookup"><span data-stu-id="4ffc1-143">Default expressions.</span></span>

<!-- For more information see [link to C# what's new](url). -->

## <a name="platform-improvements"></a><span data-ttu-id="4ffc1-144">Platform geliştirmeleri</span><span class="sxs-lookup"><span data-stu-id="4ffc1-144">Platform improvements</span></span>

<span data-ttu-id="4ffc1-145">.NET Core 2.0, .NET Core'un yüklenmesini ve desteklenen işletim sistemlerinde kullanılmasını kolaylaştıran bir dizi özellik içerir.</span><span class="sxs-lookup"><span data-stu-id="4ffc1-145">.NET Core 2.0 includes a number of features that make it easier to install .NET Core and to use it on supported operating systems.</span></span>

### <a name="net-core-for-linux-is-a-single-implementation"></a><span data-ttu-id="4ffc1-146">Linux için .NET Core tek bir uygulamadır</span><span class="sxs-lookup"><span data-stu-id="4ffc1-146">.NET Core for Linux is a single implementation</span></span>

<span data-ttu-id="4ffc1-147">.NET Core 2.0, birden fazla Linux dağıtımı nda çalışan tek bir Linux uygulaması sunar.</span><span class="sxs-lookup"><span data-stu-id="4ffc1-147">.NET Core 2.0 offers a single Linux implementation that works on multiple Linux distributions.</span></span> <span data-ttu-id="4ffc1-148">.NET Core 1.x, dağıtıma özel bir Linux uygulamasını indirmenizi zorunlu kattı.</span><span class="sxs-lookup"><span data-stu-id="4ffc1-148">.NET Core 1.x required that you download a distribution-specific Linux implementation.</span></span>

<span data-ttu-id="4ffc1-149">Linux'u tek bir işletim sistemi olarak hedefleyen uygulamalar da geliştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4ffc1-149">You can also develop apps that target Linux as a single operating system.</span></span> <span data-ttu-id="4ffc1-150">.NET Core 1.x, her Linux dağıtımına ayrı ayrı hedeflemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="4ffc1-150">.NET Core 1.x required that you target each Linux distribution separately.</span></span>

### <a name="support-for-the-apple-cryptographic-libraries"></a><span data-ttu-id="4ffc1-151">Apple şifreleme kitaplıkları için destek</span><span class="sxs-lookup"><span data-stu-id="4ffc1-151">Support for the Apple cryptographic libraries</span></span>

<span data-ttu-id="4ffc1-152">MacOS'ta .NET Core 1.x, OpenSSL araç setinin şifreleme kitaplığını gerekli kattı.</span><span class="sxs-lookup"><span data-stu-id="4ffc1-152">.NET Core 1.x on macOS required the OpenSSL toolkit's cryptographic library.</span></span> <span data-ttu-id="4ffc1-153">.NET Core 2.0, Apple şifreleme kitaplıklarını kullanır ve OpenSSL gerektirmez, bu nedenle artık yüklemeniz gerekmez.</span><span class="sxs-lookup"><span data-stu-id="4ffc1-153">.NET Core 2.0 uses the Apple cryptographic libraries and doesn't require OpenSSL, so you no longer need to install it.</span></span>

## <a name="api-changes-and-library-support"></a><span data-ttu-id="4ffc1-154">API değişiklikleri ve kitaplık desteği</span><span class="sxs-lookup"><span data-stu-id="4ffc1-154">API changes and library support</span></span>

### <a name="support-for-net-standard-20"></a><span data-ttu-id="4ffc1-155">.NET Standard 2.0 desteği</span><span class="sxs-lookup"><span data-stu-id="4ffc1-155">Support for .NET Standard 2.0</span></span>

<span data-ttu-id="4ffc1-156">.NET Standardı, standardın bu sürümüne uygun .NET uygulamalarında bulunması gereken sürümlenmiş bir API kümesi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="4ffc1-156">The .NET Standard defines a versioned set of APIs that must be available on .NET implementations that comply with that version of the standard.</span></span> <span data-ttu-id="4ffc1-157">.NET Standardı kitaplık geliştiricileri hedeflenebilmektedir.</span><span class="sxs-lookup"><span data-stu-id="4ffc1-157">The .NET Standard is targeted at library developers.</span></span> <span data-ttu-id="4ffc1-158">Her .NET uygulamasında .NET Standardının bir sürümünü hedefleyen bir kitaplığın kullanabileceği işlevselliği garanti etmeyi amaçlar.</span><span class="sxs-lookup"><span data-stu-id="4ffc1-158">It aims to guarantee the functionality that is available to a library that targets a version of the .NET Standard on each .NET implementation.</span></span> <span data-ttu-id="4ffc1-159">.NET Core 1.x .NET Standart sürüm 1.6 destekler; .NET Core 2.0 en son sürümü destekler, .NET Standart 2.0.</span><span class="sxs-lookup"><span data-stu-id="4ffc1-159">.NET Core 1.x supports the .NET Standard version 1.6; .NET Core 2.0 supports the latest version, .NET Standard 2.0.</span></span> <span data-ttu-id="4ffc1-160">Daha fazla bilgi için [.NET Standard](../../standard/net-standard.md)' a bakın.</span><span class="sxs-lookup"><span data-stu-id="4ffc1-160">For more information, see [.NET Standard](../../standard/net-standard.md).</span></span>

<span data-ttu-id="4ffc1-161">.NET Standart 2.0, .NET Standart 1.6'da bulunandan 20.000'den fazla API içerir.</span><span class="sxs-lookup"><span data-stu-id="4ffc1-161">.NET Standard 2.0 includes over 20,000 more APIs than were available in the .NET Standard 1.6.</span></span> <span data-ttu-id="4ffc1-162">Bu genişletilmiş yüzey alanının çoğu,.NET Framework ve Xamarin'de ortak olan API'lerin .NET Standardına dahil edilmesinden kaynaklanır.</span><span class="sxs-lookup"><span data-stu-id="4ffc1-162">Much of this expanded surface area results from incorporating APIs that are common to the .NET Framework and Xamarin into .NET Standard.</span></span>

<span data-ttu-id="4ffc1-163">.NET Standart 2.0 sınıf kitaplıkları, .NET Standart 2.0'da bulunan API'leri aramaları koşuluyla .NET Framework sınıf kitaplıklarına da başvuruyapabilir.</span><span class="sxs-lookup"><span data-stu-id="4ffc1-163">.NET Standard 2.0 class libraries can also reference .NET Framework class libraries, provided that they call APIs that are present in the .NET Standard 2.0.</span></span> <span data-ttu-id="4ffc1-164">.NET Framework kitaplıklarının yeniden derlemesi gerekmez.</span><span class="sxs-lookup"><span data-stu-id="4ffc1-164">No recompilation of the .NET Framework libraries is required.</span></span>

<span data-ttu-id="4ffc1-165">Son sürümünden bu yana .NET Standardına eklenen API'lerin listesi için .NET Standart 1.6'ya [bakın.NET Standart 2.0 vs. 1.6.](https://raw.githubusercontent.com/dotnet/standard/master/docs/versions/netstandard2.0_diff.md)</span><span class="sxs-lookup"><span data-stu-id="4ffc1-165">For a list of the APIs that have been added to the .NET Standard since its last version, the .NET Standard 1.6, see [.NET Standard 2.0 vs. 1.6](https://raw.githubusercontent.com/dotnet/standard/master/docs/versions/netstandard2.0_diff.md).</span></span>

### <a name="expanded-surface-area"></a><span data-ttu-id="4ffc1-166">Genişletilmiş yüzey alanı</span><span class="sxs-lookup"><span data-stu-id="4ffc1-166">Expanded surface area</span></span>

<span data-ttu-id="4ffc1-167">.NET Core 2.0'da bulunan toplam API sayısı .NET Core 1.1 ile karşılaştırıldığında iki kattan fazla artmıştır.</span><span class="sxs-lookup"><span data-stu-id="4ffc1-167">The total number of APIs available on .NET Core 2.0 has more than doubled in comparison with .NET Core 1.1.</span></span>

<span data-ttu-id="4ffc1-168">Ve [.NET](../porting/windows-compat-pack.md) Framework'den windows uyumluluk paketi taşıma ile de çok daha basit hale gelmiştir.</span><span class="sxs-lookup"><span data-stu-id="4ffc1-168">And with the [Windows Compatibility Pack](../porting/windows-compat-pack.md) porting from .NET Framework has also become much simpler.</span></span>

### <a name="support-for-net-framework-libraries"></a><span data-ttu-id="4ffc1-169">.NET Framework kitaplıkları için destek</span><span class="sxs-lookup"><span data-stu-id="4ffc1-169">Support for .NET Framework libraries</span></span>

<span data-ttu-id="4ffc1-170">.NET Core kodu, mevcut NuGet paketleri de dahil olmak üzere varolan .NET Framework kitaplıkları referans olabilir.</span><span class="sxs-lookup"><span data-stu-id="4ffc1-170">.NET Core code can reference existing .NET Framework libraries, including existing NuGet packages.</span></span> <span data-ttu-id="4ffc1-171">Kitaplıkların .NET Standardı'nda bulunan API'leri kullanması gerektiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="4ffc1-171">Note that the libraries must use APIs that are found in .NET Standard.</span></span>

## <a name="visual-studio-integration"></a><span data-ttu-id="4ffc1-172">Visual Studio ile tümleştirme</span><span class="sxs-lookup"><span data-stu-id="4ffc1-172">Visual Studio integration</span></span>

<span data-ttu-id="4ffc1-173">Visual Studio 2017 sürüm 15.3 ve bazı durumlarda Mac için Visual Studio .NET Core geliştiricileri için önemli geliştirmeler sunar.</span><span class="sxs-lookup"><span data-stu-id="4ffc1-173">Visual Studio 2017 version 15.3 and in some cases Visual Studio for Mac offer a number of significant enhancements for .NET Core developers.</span></span>

### <a name="retargeting-net-core-apps-and-net-standard-libraries"></a><span data-ttu-id="4ffc1-174">.NET Core uygulamalarını ve .NET Standart kitaplıklarını yeniden hedefleme</span><span class="sxs-lookup"><span data-stu-id="4ffc1-174">Retargeting .NET Core apps and .NET Standard libraries</span></span>

<span data-ttu-id="4ffc1-175">.NET Core 2.0 SDK yüklüyse, .NET Core 1.x projelerini .NET Core 2.0 ve .NET Standard 1.x kitaplıklarını .NET Standard 2.0'a yeniden hedefleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4ffc1-175">If the .NET Core 2.0 SDK is installed, you can retarget .NET Core 1.x projects to .NET Core 2.0 and .NET Standard 1.x libraries to .NET Standard 2.0.</span></span>

<span data-ttu-id="4ffc1-176">Visual Studio'da projenizi yeniden hedeflemek için, projenin özellikleri iletişim kutusunun **Uygulama** sekmesini açar ve **Hedef çerçeve** değerini **.NET Core 2.0** veya **.NET Standard 2.0**olarak değiştirirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4ffc1-176">To retarget your project in Visual Studio, you open the **Application** tab of the project's properties dialog and change the **Target framework** value to **.NET Core 2.0** or **.NET Standard 2.0**.</span></span> <span data-ttu-id="4ffc1-177">Ayrıca, projeye sağ tıklayarak ve **Düzenleme \*.csproj dosya** seçeneğini seçerek değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4ffc1-177">You can also change it by right-clicking on the project and selecting the **Edit \*.csproj file** option.</span></span> <span data-ttu-id="4ffc1-178">Daha fazla bilgi için, bu konunun daha önceki [Araçlama](#tooling) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="4ffc1-178">For more information, see the [Tooling](#tooling) section earlier in this topic.</span></span>

### <a name="live-unit-testing-support-for-net-core"></a><span data-ttu-id="4ffc1-179">.NET Core için Live Unit Testing</span><span class="sxs-lookup"><span data-stu-id="4ffc1-179">Live Unit Testing support for .NET Core</span></span>

<span data-ttu-id="4ffc1-180">Kodunuzu her değiştirdiğinizde, Canlı Birim Testi etkilenen birim testlerini arka planda otomatik olarak çalıştırArak sonuçları ve kod kapsamını Visual Studio ortamında canlı olarak görüntüler.</span><span class="sxs-lookup"><span data-stu-id="4ffc1-180">Whenever you modify your code, Live Unit Testing automatically runs any affected unit tests in the background and displays the results and code coverage live in the Visual Studio environment.</span></span> <span data-ttu-id="4ffc1-181">.NET Core 2.0 artık Canlı Birim Testini destekliyor.</span><span class="sxs-lookup"><span data-stu-id="4ffc1-181">.NET Core 2.0 now supports Live Unit Testing.</span></span> <span data-ttu-id="4ffc1-182">Daha önce, Canlı Birim Testi yalnızca .NET Framework uygulamaları için mevcuttu.</span><span class="sxs-lookup"><span data-stu-id="4ffc1-182">Previously, Live Unit Testing was available only for .NET Framework applications.</span></span>

<span data-ttu-id="4ffc1-183">Daha fazla bilgi için [Visual Studio ile Canlı Birim Testi](/visualstudio/test/live-unit-testing) ve Canlı Birim Test [SSS'ye](/visualstudio/test/live-unit-testing-faq)bakın.</span><span class="sxs-lookup"><span data-stu-id="4ffc1-183">For more information, see [Live Unit Testing with Visual Studio](/visualstudio/test/live-unit-testing) and the [Live Unit Testing FAQ](/visualstudio/test/live-unit-testing-faq).</span></span>

### <a name="better-support-for-multiple-target-frameworks"></a><span data-ttu-id="4ffc1-184">Birden çok hedef çerçeve için daha iyi destek</span><span class="sxs-lookup"><span data-stu-id="4ffc1-184">Better support for multiple target frameworks</span></span>

<span data-ttu-id="4ffc1-185">Birden çok hedef çerçevesi için bir proje oluşturuyorsanız, artık üst düzey menüden hedef platformu seçebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4ffc1-185">If you're building a project for multiple target frameworks, you can now select the target platform from the top-level menu.</span></span> <span data-ttu-id="4ffc1-186">Aşağıdaki şekilde, SCD1 adlı bir proje 64-bit macOS X`osx.10.11-x64`10.11 ( ) ve 64-bit`win10-x64`Windows 10/Windows Server 2016 ( hedefliyor.</span><span class="sxs-lookup"><span data-stu-id="4ffc1-186">In the following figure, a project named SCD1 targets 64-bit macOS X 10.11 (`osx.10.11-x64`) and 64-bit Windows 10/Windows Server 2016 (`win10-x64`).</span></span> <span data-ttu-id="4ffc1-187">Bu durumda hata ayıklama oluşturma yı çalıştırmak için proje düğmesini seçmeden önce hedef çerçeveyi seçebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4ffc1-187">You can select the target framework before selecting the project button, in this case to run a debug build.</span></span>

![Proje inşa ederken hedef çerçeve seçimini gösteren ekran görüntüsü.](./media/dotnet-core-2-0/target-framework-selection.png)

### <a name="side-by-side-support-for-net-core-sdks"></a><span data-ttu-id="4ffc1-189">.NET Core SDK'lar için yan yana destek</span><span class="sxs-lookup"><span data-stu-id="4ffc1-189">Side-by-side support for .NET Core SDKs</span></span>

<span data-ttu-id="4ffc1-190">Artık .NET Core SDK'yı Visual Studio'dan bağımsız olarak yükleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4ffc1-190">You can now install the .NET Core SDK independently of Visual Studio.</span></span> <span data-ttu-id="4ffc1-191">Bu, Visual Studio'nun tek bir sürümünün .NET Core'un farklı sürümlerini hedefleyen projeler oluşturmasını mümkün kılar.</span><span class="sxs-lookup"><span data-stu-id="4ffc1-191">This makes it possible for a single version of Visual Studio to build projects that target different versions of .NET Core.</span></span> <span data-ttu-id="4ffc1-192">Daha önce, Visual Studio ve .NET Core SDK sıkıca birleştirilmiş; SDK'nın belirli bir versiyonu Visual Studio'nun belirli bir sürümüne eşlik etti.</span><span class="sxs-lookup"><span data-stu-id="4ffc1-192">Previously, Visual Studio and the .NET Core SDK were tightly coupled; a particular version of the SDK accompanied a particular version of Visual Studio.</span></span>

## <a name="documentation-improvements"></a><span data-ttu-id="4ffc1-193">Dokümantasyon geliştirmeleri</span><span class="sxs-lookup"><span data-stu-id="4ffc1-193">Documentation improvements</span></span>

### <a name="net-application-architecture"></a><span data-ttu-id="4ffc1-194">.NET Uygulama Mimarisi</span><span class="sxs-lookup"><span data-stu-id="4ffc1-194">.NET Application Architecture</span></span>

<span data-ttu-id="4ffc1-195">[.NET Application Architecture,](https://dotnet.microsoft.com/learn/dotnet/architecture-guides) oluşturmak için .NET'i kullanırken rehberlik, en iyi uygulamalar ve örnek uygulamalar sağlayan bir dizi e-kitap'a erişmenizi sağlar:</span><span class="sxs-lookup"><span data-stu-id="4ffc1-195">[.NET Application Architecture](https://dotnet.microsoft.com/learn/dotnet/architecture-guides) gives you access to a set of e-books that provide guidance, best practices, and sample applications when using .NET to build:</span></span>

- [<span data-ttu-id="4ffc1-196">Mikrohizmetler ve Docker konteynerleri</span><span class="sxs-lookup"><span data-stu-id="4ffc1-196">Microservices and Docker containers</span></span>](../../architecture/microservices/index.md)
- [<span data-ttu-id="4ffc1-197">ASP.NET ile Web uygulamaları</span><span class="sxs-lookup"><span data-stu-id="4ffc1-197">Web applications with ASP.NET</span></span>](../../architecture/modern-web-apps-azure/index.md)
- [<span data-ttu-id="4ffc1-198">Xamarin ile mobil uygulamalar</span><span class="sxs-lookup"><span data-stu-id="4ffc1-198">Mobile applications with Xamarin</span></span>](/xamarin/xamarin-forms/enterprise-application-patterns/index)
- [<span data-ttu-id="4ffc1-199">Azure ile Bulut'a dağıtılan uygulamalar</span><span class="sxs-lookup"><span data-stu-id="4ffc1-199">Applications that are deployed to the Cloud with Azure</span></span>](/azure/architecture/reference-architectures/index)

## <a name="see-also"></a><span data-ttu-id="4ffc1-200">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4ffc1-200">See also</span></span>

- [<span data-ttu-id="4ffc1-201">ASP.NET Core 2.0'daki yenilikler</span><span class="sxs-lookup"><span data-stu-id="4ffc1-201">What's new in ASP.NET Core 2.0</span></span>](/aspnet/core/aspnetcore-2.0)
