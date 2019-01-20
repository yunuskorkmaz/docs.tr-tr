---
title: .NET Core 3. 0'yenilikler nelerdir?
description: .NET Core 3. 0 ' bulunan yeni özellikler hakkında bilgi edinin.
dev_langs:
- csharp
- vb
author: thraka
ms.author: adegeo
ms.date: 12/04/2018
ms.openlocfilehash: 26fb7cb25b9bf7f00f87059fbe1848763f7f175d
ms.sourcegitcommit: b56d59ad42140d277f2acbd003b74d655fdbc9f1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2019
ms.locfileid: "54415552"
---
# <a name="whats-new-in-net-core-30-preview-1"></a><span data-ttu-id="73981-103">.NET Core 3.0 (Önizleme 1) yenilikler</span><span class="sxs-lookup"><span data-stu-id="73981-103">What's new in .NET Core 3.0 (Preview 1)</span></span>

<span data-ttu-id="73981-104">Bu makalede, .NET Core 3.0 (Önizleme 1) Yenilikler açıklanır.</span><span class="sxs-lookup"><span data-stu-id="73981-104">This article describes what is new in .NET Core 3.0 (preview 1).</span></span> <span data-ttu-id="73981-105">Büyük iyileştirmeler Windows Masaüstü uygulamaları (yalnızca Windows) için destek biridir.</span><span class="sxs-lookup"><span data-stu-id="73981-105">One of the biggest enhancements is support for Windows desktop applications (Windows only).</span></span> <span data-ttu-id="73981-106">Windows Masaüstü adlı bir .NET Core 3.0 bileşen yararlanarak uygulamalarınızı Windows Formları Windows Presentation Foundation (WPF) bağlantı noktası.</span><span class="sxs-lookup"><span data-stu-id="73981-106">By utilizing a .NET Core 3.0 component called Windows Desktop, you can port your Windows Forms Windows Presentation Foundation (WPF) applications.</span></span> <span data-ttu-id="73981-107">Gerekirse Windows Masaüstü bileşeni yalnızca Windows üzerinde desteklenir.</span><span class="sxs-lookup"><span data-stu-id="73981-107">To be clear, the Windows Desktop component is only supported on Windows.</span></span> <span data-ttu-id="73981-108">Daha fazla bilgi için konudaki [Windows Masaüstü](#windows-desktop) aşağıda.</span><span class="sxs-lookup"><span data-stu-id="73981-108">For more information, see the section [Windows desktop](#windows-desktop) below.</span></span>

<span data-ttu-id="73981-109">.NET core 3.0 için destek ekler C# 8.0.</span><span class="sxs-lookup"><span data-stu-id="73981-109">.NET Core 3.0 adds support for C# 8.0.</span></span>

<span data-ttu-id="73981-110">[İndirin ve .NET Core 3 Önizleme 1 ile çalışmaya başlama](https://aka.ms/netcore3download) şu anda Windows, Mac ve Linux üzerinde.</span><span class="sxs-lookup"><span data-stu-id="73981-110">[Download and get started with .NET Core 3 Preview 1](https://aka.ms/netcore3download) right now on Windows, Mac and Linux.</span></span> <span data-ttu-id="73981-111">Yayın içinde tüm ayrıntılarını görebilirsiniz [.NET Core 3 Önizleme 1 sürüm notları](https://aka.ms/netcore3releasenotes).</span><span class="sxs-lookup"><span data-stu-id="73981-111">You can see complete details of the release in the [.NET Core 3 Preview 1 release notes](https://aka.ms/netcore3releasenotes).</span></span>

<span data-ttu-id="73981-112">Daha fazla bilgi için [.NET Core 3.0 Önizleme 1 Duyurusu](https://blogs.msdn.microsoft.com/dotnet/2018/12/04/announcing-net-core-3-preview-1-and-open-sourcing-windows-desktop-frameworks/).</span><span class="sxs-lookup"><span data-stu-id="73981-112">For more information, see the [.NET Core 3.0 Preview 1 announcement](https://blogs.msdn.microsoft.com/dotnet/2018/12/04/announcing-net-core-3-preview-1-and-open-sourcing-windows-desktop-frameworks/).</span></span>

## <a name="net-standard-21"></a><span data-ttu-id="73981-113">.NET standard 2.1</span><span class="sxs-lookup"><span data-stu-id="73981-113">.NET Standard 2.1</span></span>

<span data-ttu-id="73981-114">.NET core 3.0 .NET standart 2.1 uygular.</span><span class="sxs-lookup"><span data-stu-id="73981-114">.NET Core 3.0 implements .NET Standard 2.1.</span></span>

## <a name="default-executables"></a><span data-ttu-id="73981-115">Varsayılan yürütülebilir dosyalar</span><span class="sxs-lookup"><span data-stu-id="73981-115">Default executables</span></span>

<span data-ttu-id="73981-116">.NET core artık derler [framework bağımlı yürütülebilir dosyaları](../deploying/index.md#framework-dependent-executables-fde) varsayılan olarak.</span><span class="sxs-lookup"><span data-stu-id="73981-116">.NET Core will now build [framework-dependent executables](../deploying/index.md#framework-dependent-executables-fde) by default.</span></span> <span data-ttu-id="73981-117">.NET Core genel olarak yüklenmiş bir sürümünü kullanan uygulamalar için yeni bir özelliktir.</span><span class="sxs-lookup"><span data-stu-id="73981-117">This is new for applications that use a globally installed version of .NET Core.</span></span> <span data-ttu-id="73981-118">Şimdiye kadar yalnızca [müstakil dağıtımları](../deploying/index.md#self-contained-deployments-scd) yürütülebilir bir dosya oluşturur.</span><span class="sxs-lookup"><span data-stu-id="73981-118">Until now, only [self-contained deployments](../deploying/index.md#self-contained-deployments-scd) would produce an executable.</span></span>

<span data-ttu-id="73981-119">Sırasında `dotnet build` veya `dotnet publish`, kullanmakta olduğunuz SDK platform ve ortam ile eşleşen sağlanan yürütülebilir bir dosya oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="73981-119">During `dotnet build` or `dotnet publish`, an executable is created provided that matches the environment and platform of the SDK you are using.</span></span> <span data-ttu-id="73981-120">Diğer yerel yürütülebilir dosyalar gibi olduğu gibi bu yürütülebilir dosyaları ile aynı şey geçerli olacaktır:</span><span class="sxs-lookup"><span data-stu-id="73981-120">You can expect the same things with these executables as you would other native executables, such as:</span></span>

* <span data-ttu-id="73981-121">Yürütülebilir dosya üzerine çift tıklayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="73981-121">You can double-click on the executable.</span></span>
* <span data-ttu-id="73981-122">Doğrudan bir komut isteminden uygulama başlatma gibi `myapp.exe` Windows, şirket ve `./myapp` Linux ve Macos'ta.</span><span class="sxs-lookup"><span data-stu-id="73981-122">You can launch the application from a command prompt directly, such as `myapp.exe` on Windows, and `./myapp` on Linux and macOS.</span></span>

## <a name="build-copies-dependencies"></a><span data-ttu-id="73981-123">Derleme bağımlılıkları kopyalar.</span><span class="sxs-lookup"><span data-stu-id="73981-123">Build copies dependencies</span></span>

<span data-ttu-id="73981-124">`dotnet build` artık uygulamanız için NuGet bağımlılıklarını NuGet önbellekten yapı çıktı klasörüne kopyalar.</span><span class="sxs-lookup"><span data-stu-id="73981-124">`dotnet build` now copies NuGet dependencies for your application from the NuGet cache to the build output folder.</span></span> <span data-ttu-id="73981-125">Daha önce bağımlılıkları parçası olarak yalnızca kopyalanan `dotnet publish`.</span><span class="sxs-lookup"><span data-stu-id="73981-125">Previously, dependencies were only copied as part of `dotnet publish`.</span></span> 

<span data-ttu-id="73981-126">Yayımlama, yayınlama, bağlama ve razor sayfası hala gerektirir gibi bazı işlemler vardır.</span><span class="sxs-lookup"><span data-stu-id="73981-126">There are some operations, like linking and razor page publishing that will still require publishing.</span></span>


## <a name="local-dotnet-tools"></a><span data-ttu-id="73981-127">Yerel dotnet araçları</span><span class="sxs-lookup"><span data-stu-id="73981-127">Local dotnet tools</span></span>

<span data-ttu-id="73981-128">.NET Core 2.1 genel araçları destekleniyorsa, .NET Core 3.0 artık yerel araçlara sahiptir.</span><span class="sxs-lookup"><span data-stu-id="73981-128">While .NET Core 2.1 supported global tools, .NET Core 3.0 now has local tools.</span></span> <span data-ttu-id="73981-129">Yerel Araçlar genel araçları benzerdir, ancak disk üzerindeki belirli bir konum ile ilişkilidir.</span><span class="sxs-lookup"><span data-stu-id="73981-129">Local tools are similar to global tools but are associated with a particular location on disk.</span></span> <span data-ttu-id="73981-130">Bu, proje başına ve havuz başına araçlar sağlar.</span><span class="sxs-lookup"><span data-stu-id="73981-130">This enables per-project and per-repository tooling.</span></span> <span data-ttu-id="73981-131">Yerel olarak yüklü herhangi bir aracı genel olarak kullanılabilir değil.</span><span class="sxs-lookup"><span data-stu-id="73981-131">Any tool installed locally isn't available globally.</span></span>

<span data-ttu-id="73981-132">Yerel Araçlar kullanan bir bildirim dosyası adına `dotnet-tools.json` geçerli dizininizde.</span><span class="sxs-lookup"><span data-stu-id="73981-132">Local tools rely on a manifest file name `dotnet-tools.json` in your current directory.</span></span> <span data-ttu-id="73981-133">Bu bildirim dosyası, kullanılabilir olması için Araçlar tanımlar.</span><span class="sxs-lookup"><span data-stu-id="73981-133">This manifest file defines the tools to be available.</span></span> <span data-ttu-id="73981-134">Bu bildirim dosyası, depo kökünde oluşturarak, herkesin kodunuzu kopyalama geri yükleyebilir ve başarıyla kodunuzla çalışmak için gereken araçları kullanmanız emin olun.</span><span class="sxs-lookup"><span data-stu-id="73981-134">By creating this manifest file at the root of your repository, you ensure anyone cloning your code can restore and use the tools that are needed to successfully work with your code.</span></span>

<span data-ttu-id="73981-135">Bildirim dosyası yerel Araçlar kullanılabilir olduğunda otomatik olarak indirip yerel olarak bu araçları yüklemek için aşağıdaki komutu kullanın:</span><span class="sxs-lookup"><span data-stu-id="73981-135">When the local tools manifest file is available, use the following command to automatically download and install those tools locally:</span></span>

```console
dotnet tool restore
```

<span data-ttu-id="73981-136">Yerel bir aracı ile aşağıdaki komutu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="73981-136">Run a local tool with the following command:</span></span>

```console
dotnet tool run <tool-command-name>
```

<span data-ttu-id="73981-137">Dotnet, yerel aracı çağrıldığında, dizin yapısını bildirim arar.</span><span class="sxs-lookup"><span data-stu-id="73981-137">When a local tool is called, dotnet searches for a manifest up the directory structure.</span></span> <span data-ttu-id="73981-138">Bir aracı bildirim dosyası bulunduğunda, için istenen aracı aranır.</span><span class="sxs-lookup"><span data-stu-id="73981-138">When a tool manifest file is found, it is searched for the requested tool.</span></span> <span data-ttu-id="73981-139">Aracı tespit edilirse, aracı NuGet genel paketleri konumu bulmak için gereken bilgileri içerir.</span><span class="sxs-lookup"><span data-stu-id="73981-139">If the tool is found, it includes the information needed to find the tool in the NuGet global packages location.</span></span> 

<span data-ttu-id="73981-140">Aracı bildirimi, ancak önbellek bulunursa, kullanıcı hata alır.</span><span class="sxs-lookup"><span data-stu-id="73981-140">If the tool is found in the manifest, but not the cache, the user receives an error.</span></span> <span data-ttu-id="73981-141">Kullanıcının çalıştırmasını istemek için Önizleme 1 ileti geliştirilecektir `dotnet tool restore`.</span><span class="sxs-lookup"><span data-stu-id="73981-141">The message will be improved after Preview 1 to request the user run `dotnet tool restore`.</span></span>

<span data-ttu-id="73981-142">Bir dizine yerel araçları eklemek için ilk olarak aracı bildirim dosyası oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="73981-142">To add local tools to a directory, you need to first create the tool manifest file.</span></span> <span data-ttu-id="73981-143">Preview 1'den sonra aracı gibi dotnet yeni bir şablon bildirim dosyalarını oluşturmak için bir mekanizma sunacağız.</span><span class="sxs-lookup"><span data-stu-id="73981-143">After Preview 1, we will offer a mechanism for creating tool manifest files, such as a dotnet new template.</span></span> <span data-ttu-id="73981-144">Preview 1'için adlı bir dosya oluşturmalısınız `dotnet-tools.json` aşağıdaki içeriklerle:</span><span class="sxs-lookup"><span data-stu-id="73981-144">For Preview 1 you must create the file named `dotnet-tools.json` with the following contents:</span></span>

```json
{
  "version": 1,
  "isRoot": true,
  "tools": {}
}
```

<span data-ttu-id="73981-145">Bildirim oluşturulduktan sonra yerel araçlarını kullanarak ekleyebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="73981-145">Once the manifest is created, you can add local tools to it using:</span></span>

```console
dotnet tool install <toolPackageId>
```

<span data-ttu-id="73981-146">Bu komut, başka bir sürümü belirtilmediği sürece aracı en son sürümünü yükler.</span><span class="sxs-lookup"><span data-stu-id="73981-146">This command installs the latest version of the tool, unless another version is specified.</span></span>  <span data-ttu-id="73981-147">En son sürüme otomatik olarak seçilmiş olsa bile, Aracı'nın sürümü geri veya çalıştırmak için aracının doğru sürümü izin vermek için aracı bildirim dosyasına yazılır.</span><span class="sxs-lookup"><span data-stu-id="73981-147">Even if the latest version was automatically chosen, the version of the tool is written into the tool manifest file to allow the correct version of the tool to be restored or run.</span></span>

<span data-ttu-id="73981-148">Aracı bildirim dosyasını elle düzenlemeye – izin vermek için deposuyla çalışmak için gerekli sürümü güncelleştirmek için bunu tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="73981-148">The tool manifest file is designed to allow hand editing – which you might do to update the required version for working with the repository.</span></span>

<span data-ttu-id="73981-149">İşte bir örnek `dotnet-tools.json` dosyası:</span><span class="sxs-lookup"><span data-stu-id="73981-149">Here is an example `dotnet-tools.json` file:</span></span>

```json
{
  "version": 1,
  "isRoot": true,
  "tools": {
    "dotnetsay": {
      "version": "2.1.4",
      "commands": [
        "dotnetsay"
      ]
    },
    "t-rex": {
      "version": "1.0.103",
      "commands": [
        "t-rex"
      ]
    }
  }
}
```

<span data-ttu-id="73981-150">Bir aracı aracı bildirim dosyasından kaldırmak için aşağıdaki komutu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="73981-150">To remove a tool from the tool manifest file, run the following command:</span></span>

```console
dotnet tool uninstall <toolPackageId>
```

<span data-ttu-id="73981-151">Hem genel hem de yerel araçları için çalışma zamanı'nın uyumlu bir sürümü gereklidir.</span><span class="sxs-lookup"><span data-stu-id="73981-151">For both global and local tools, a compatible version of the runtime is required.</span></span> <span data-ttu-id="73981-152">Birçok araç NuGet.org üzerinde şu anda .NET Core çalışma zamanı 2.1 hedefleyin.</span><span class="sxs-lookup"><span data-stu-id="73981-152">Many tools currently on NuGet.org target .NET Core Runtime 2.1.</span></span> <span data-ttu-id="73981-153">Bu genel olarak veya yerel olarak yüklemek için yükleme yine [NET Core 2.1 çalışma zamanı](https://dotnet.microsoft.com/download/dotnet-core/2.1).</span><span class="sxs-lookup"><span data-stu-id="73981-153">To install those globally or locally, you would still need to install the [NET Core 2.1 Runtime](https://dotnet.microsoft.com/download/dotnet-core/2.1).</span></span>

<span data-ttu-id="73981-154">Daha fazla bilgi için [yerel Araçlar erken Önizleme belgeleri](https://github.com/dotnet/cli/issues/10288).</span><span class="sxs-lookup"><span data-stu-id="73981-154">For more information, see [Local Tools Early Preview Documentation](https://github.com/dotnet/cli/issues/10288).</span></span>

## <a name="windows-desktop"></a><span data-ttu-id="73981-155">Windows masaüstü</span><span class="sxs-lookup"><span data-stu-id="73981-155">Windows desktop</span></span>

<span data-ttu-id="73981-156">.NET Core 3.0 Önizleme 1'den başlayarak, WPF ve Windows Forms kullanılarak Windows Masaüstü uygulamaları oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="73981-156">Starting with .NET Core 3.0 Preview 1, you can build Windows desktop applications using WPF and Windows Forms.</span></span> <span data-ttu-id="73981-157">Bu çerçeveler ile modern denetimleri ve Windows kullanıcı Arabirimi XAML kitaplığından (WinUI) Fluent stil kullanarak da destekler [XAML Adaları](/windows/uwp/xaml-platform/xaml-host-controls).</span><span class="sxs-lookup"><span data-stu-id="73981-157">These frameworks also support using modern controls and Fluent styling from the Windows UI XAML Library (WinUI) via [XAML islands](/windows/uwp/xaml-platform/xaml-host-controls).</span></span>

<span data-ttu-id="73981-158">Windows Masaüstü bileşen Windows parçasıdır .NET Core 3.0 SDK.</span><span class="sxs-lookup"><span data-stu-id="73981-158">The Windows Desktop component is part of the Windows .NET Core 3.0 SDK.</span></span>

<span data-ttu-id="73981-159">Şunlarla birlikte yeni bir Windows Forms ve WPF uygulaması oluşturabilirsiniz `dotnet` komutları:</span><span class="sxs-lookup"><span data-stu-id="73981-159">You can create a new WPF or Windows Forms app with the following `dotnet` commands:</span></span>

```console
dotnet new wpf
dotnet new winforms
```

<span data-ttu-id="73981-160">Açmak, başlatmak ve .NET Core 3.0 WPF ve Windows Forms projeleri Visual Studio 2019 Önizleme 1 hata ayıklama.</span><span class="sxs-lookup"><span data-stu-id="73981-160">You can also open, launch, and debug .NET Core 3.0 WPF and Windows Forms projects in Visual Studio 2019 Preview 1.</span></span> <span data-ttu-id="73981-161">Visual Studio 2017 15.9 içinde bu projeleri açmak şu anda mümkündür, ancak bu desteklenen bir senaryo değildir (ve gerekiyorsa [önizlemelerini etkinleştir](https://blogs.msdn.microsoft.com/dotnet/2018/11/13/net-core-tooling-update-for-visual-studio-2017-version-15-9/)).</span><span class="sxs-lookup"><span data-stu-id="73981-161">It's currently possible to open these projects in Visual Studio 2017 15.9, however, it isn't a supported scenario (and you need to [enable previews](https://blogs.msdn.microsoft.com/dotnet/2018/11/13/net-core-tooling-update-for-visual-studio-2017-version-15-9/)).</span></span>

<span data-ttu-id="73981-162">Yeni Proje birkaç eklemelerle mevcut .NET Core projeleri ile aynıdır.</span><span class="sxs-lookup"><span data-stu-id="73981-162">The new projects are the same as existing .NET Core projects, with a couple additions.</span></span> <span data-ttu-id="73981-163">Temel .NET Core konsol projesi ve temel bir Windows Forms ve WPF projesi bir karşılaştırması aşağıdadır.</span><span class="sxs-lookup"><span data-stu-id="73981-163">Here is the comparison of the basic .NET Core console project and a basic Windows Forms and WPF project.</span></span>

<span data-ttu-id="73981-164">Bir .NET Core konsol projesi kullandığından `Microsoft.NET.Sdk` SDK ve .NET Core 3.0 üzerinden üzerinde bir bağımlılık bildirir `netcoreapp3.0` hedef çerçeve.</span><span class="sxs-lookup"><span data-stu-id="73981-164">In a .NET Core console project, the project uses the `Microsoft.NET.Sdk` SDK and declares a dependency on .NET Core 3.0 via the `netcoreapp3.0` target framework.</span></span> <span data-ttu-id="73981-165">Bir Windows masaüstü uygulaması oluşturmak için kullanın `Microsoft.NET.Sdk.WindowsDesktop` SDK ve kullanmak için hangi UI çerçevesi seçin:</span><span class="sxs-lookup"><span data-stu-id="73981-165">To create a Windows Desktop app, use the `Microsoft.NET.Sdk.WindowsDesktop` SDK and choose which UI framework to use:</span></span>

```diff
-<Project Sdk="Microsoft.NET.Sdk">
+<Project Sdk="Microsoft.NET.Sdk.WindowsDesktop">
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp3.0</TargetFramework>
+   <UseWPF>true</UseWPF>
  </PropertyGroup>
</Project>
```

<span data-ttu-id="73981-166">Windows Forms, WPF seçmek için ayarlanmış `UseWindowsForms` yerine `UseWPF`:</span><span class="sxs-lookup"><span data-stu-id="73981-166">To choose Windows Forms over WPF, set `UseWindowsForms` instead of `UseWPF`:</span></span>

```diff
<Project Sdk="Microsoft.NET.Sdk.WindowsDesktop">
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp3.0</TargetFramework>
-   <UseWPF>true</UseWPF>
+   <UseWindowsForms>true</UseWindowsForms>
  </PropertyGroup>
</Project>
```

<span data-ttu-id="73981-167">Her ikisi de `UseWPF` ve `UseWindowsForms` ayarlanabilir `true` uygulama için bir Windows Forms iletişim kutusu, bir WPF denetimi barındırmayla örnek her iki çerçeveleri kullanıyorsa.</span><span class="sxs-lookup"><span data-stu-id="73981-167">Both `UseWPF` and `UseWindowsForms` can be set to `true` if the app uses both frameworks, for example when a Windows Forms dialog is hosting a WPF control.</span></span>

<span data-ttu-id="73981-168">Geri bildiriminizi Lütfen paylaşım [dotnet/winforms](https://github.com/dotnet/winforms/issues), [dotnet/wpf](https://github.com/dotnet/wpf/issues) ve [dotnet/core](https://github.com/dotnet/core/issues) depolar.</span><span class="sxs-lookup"><span data-stu-id="73981-168">Please share your feedback on the [dotnet/winforms](https://github.com/dotnet/winforms/issues),  [dotnet/wpf](https://github.com/dotnet/wpf/issues) and [dotnet/core](https://github.com/dotnet/core/issues) repos.</span></span>

## <a name="fast-built-in-json-support"></a><span data-ttu-id="73981-169">Hızlı yerleşik JSON desteği</span><span class="sxs-lookup"><span data-stu-id="73981-169">Fast built-in JSON support</span></span>

<span data-ttu-id="73981-170">`System.Text.Json.Utf8JsonReader` yüksek performanslı, düşük ayırma, yalnızca iletme Okuyucu için UTF-8 kodlamalı JSON metin okuma, bir `ReadOnlySpan<byte>`.</span><span class="sxs-lookup"><span data-stu-id="73981-170">`System.Text.Json.Utf8JsonReader` is a high-performance, low allocation, forward-only reader for UTF-8 encoded JSON text, read from a `ReadOnlySpan<byte>`.</span></span> <span data-ttu-id="73981-171">`Utf8JsonReader` Özel çözümleyiciler ve deserializers oluşturmak için kullanılan bir temel, alt düzey, türüdür.</span><span class="sxs-lookup"><span data-stu-id="73981-171">The `Utf8JsonReader` is a foundational, low-level type, that can be leveraged to build custom parsers and deserializers.</span></span> <span data-ttu-id="73981-172">Kullanarak yeni bir JSON yükü okuma `Utf8JsonReader` reader'ı kullanarak daha hızlı bir şekilde x 2 [Json.NET](https://www.newtonsoft.com/json).</span><span class="sxs-lookup"><span data-stu-id="73981-172">Reading through a JSON payload using the new `Utf8JsonReader` is 2x faster than using the reader from [Json.NET](https://www.newtonsoft.com/json).</span></span> <span data-ttu-id="73981-173">JSON belirteçleri (UTF-16) dizeler olarak actualize gerekene kadar bırakmaz.</span><span class="sxs-lookup"><span data-stu-id="73981-173">It does not allocate until you need to actualize JSON tokens as (UTF-16) strings.</span></span>

<span data-ttu-id="73981-174">Bu yeni API'yi aşağıdaki bileşenleri içerir:</span><span class="sxs-lookup"><span data-stu-id="73981-174">This new API will include the following components:</span></span>

* <span data-ttu-id="73981-175">Önizleme 1'de: JSON Okuyucu (sıralı erişim)</span><span class="sxs-lookup"><span data-stu-id="73981-175">In Preview 1: JSON reader (sequential access)</span></span>
* <span data-ttu-id="73981-176">Sonraki yakında: JSON yazıcısı, DOM (rastgele erişim) poco serileştirici poco seri durumdan çıkarıcının</span><span class="sxs-lookup"><span data-stu-id="73981-176">Coming next: JSON writer, DOM (random access), poco serializer, poco deserializer</span></span>

<span data-ttu-id="73981-177">Temel bir okuyucu döngü için işte `Utf8JsonReader` başlangıç noktası olarak kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="73981-177">Here is the basic reader loop for the `Utf8JsonReader` that can be used as a starting point:</span></span>

```csharp
using System.Text.Json;

public static void Utf8JsonReaderLoop(ReadOnlySpan<byte> dataUtf8)
{
    var json = new Utf8JsonReader(dataUtf8, isFinalBlock: true, state: default);

    while (json.Read())
    {
        JsonTokenType tokenType = json.TokenType;
        ReadOnlySpan<byte> valueSpan = json.ValueSpan;
        switch (tokenType)
        {
            case JsonTokenType.StartObject:
            case JsonTokenType.EndObject:
                break;
            case JsonTokenType.StartArray:
            case JsonTokenType.EndArray:
                break;
            case JsonTokenType.PropertyName:
                break;
            case JsonTokenType.String:
                string valueString = json.GetStringValue();
                break;
            case JsonTokenType.Number:
                if (!json.TryGetInt32Value(out int valueInteger))
                {
                    throw new FormatException();
                }
                break;
            case JsonTokenType.True:
            case JsonTokenType.False:
                bool valueBool = json.GetBooleanValue();
                break;
            case JsonTokenType.Null:
                break;
            default:
                throw new ArgumentException();
        }
    }

    dataUtf8 = dataUtf8.Slice((int)json.BytesConsumed);
    JsonReaderState state = json.CurrentState;
}
```

<span data-ttu-id="73981-178">.NET ekosisteminin yararlandı [Json.NET](https://www.newtonsoft.com/json) ve iyi seçenekleri olmaya devam diğer popüler JSON kitaplıkları.</span><span class="sxs-lookup"><span data-stu-id="73981-178">The .NET ecosystem has relied on [Json.NET](https://www.newtonsoft.com/json) and other popular JSON libraries, which continue to be good choices.</span></span> <span data-ttu-id="73981-179">JSON.NET UTF-16 başlık altında olan kendi taban datatype .NET dizeleri kullanır.</span><span class="sxs-lookup"><span data-stu-id="73981-179">JSON.NET uses .NET strings as its base datatype, which are UTF-16 under the hood.</span></span> 

<span data-ttu-id="73981-180">.NET Core 2.1 ve 3.0, JSON API yazmayı mümkün kılan yeni API ekledik (gibi `Utf8JsonReader`) kullanarak bağlı olarak, daha az bellek gerektiren `Span<T>` ve UTF-8 dizeleri ve hizmet Kestrel, ASP gibi yüksek performanslı uygulamaları ihtiyaçlarını daha iyi. NET Core web sunucusu.</span><span class="sxs-lookup"><span data-stu-id="73981-180">In .NET Core 2.1 and 3.0, we added new APIs that makes it possible to write JSON APIs (such as `Utf8JsonReader`) that require much less memory, based on using `Span<T>` and UTF-8 strings, and better serve the needs of high-throughput applications like Kestrel, ASP.NET Core web server.</span></span>

## <a name="ranges-and-indices"></a><span data-ttu-id="73981-181">Aralıkları ve dizinler</span><span class="sxs-lookup"><span data-stu-id="73981-181">Ranges and indices</span></span>

<span data-ttu-id="73981-182">Yeni `Index` türü, dizin oluşturma işlemi için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="73981-182">The new `Index` type can be used for indexing.</span></span> <span data-ttu-id="73981-183">Birinden oluşturabileceğiniz bir `int` baştan ya da öneki sayar `^` işleci (C#) sonundan sayar:</span><span class="sxs-lookup"><span data-stu-id="73981-183">You can create one from an `int` that counts from the beginning, or with a prefix `^` operator (C#) that counts from the end:</span></span>

```csharp
Index i1 = 3;  // number 3 from beginning
Index i2 = ^4; // number 4 from end
int[] a = { 0, 1, 2, 3, 4, 5, 6, 7, 8, 9 };
Console.WriteLine($"{a[i1]}, {a[i2]}"); // "3, 6"
```

<span data-ttu-id="73981-184">Ayrıca bir `Range` oluşan iki tür `Index` bir başlangıç ve bitiş için bir değer ve ile yazılmış bir `x..y` aralık ifade (C#).</span><span class="sxs-lookup"><span data-stu-id="73981-184">There is also a `Range` type, which consists of two `Index` values, one for the start and one for the end, and can be written with a `x..y` range expression (C#).</span></span> <span data-ttu-id="73981-185">Ardından ile dizinleyebilirsiniz bir `Range` dilim oluşturmak için:</span><span class="sxs-lookup"><span data-stu-id="73981-185">You can then index with a `Range` in order to produce a slice:</span></span>

```csharp
var slice = a[i1..i2]; // { 3, 4, 5 }
```

> [!NOTE]
> <span data-ttu-id="73981-186">Yalnızca [ C# 8.0](https://blogs.msdn.microsoft.com/dotnet/2018/11/12/building-c-8-0/) sözdizimini destekler `Range` ve `Index`.</span><span class="sxs-lookup"><span data-stu-id="73981-186">Only [C# 8.0](https://blogs.msdn.microsoft.com/dotnet/2018/11/12/building-c-8-0/) supports syntax for `Range` and `Index`.</span></span>

## <a name="async-streams"></a><span data-ttu-id="73981-187">Zaman uyumsuz akışlar</span><span class="sxs-lookup"><span data-stu-id="73981-187">Async streams</span></span>

<span data-ttu-id="73981-188">`IAsyncEnumerable<T>` Türüdür, yeni bir zaman uyumsuz sürümü `IEnumerable<T>`.</span><span class="sxs-lookup"><span data-stu-id="73981-188">The `IAsyncEnumerable<T>` type is a new asynchronous version of `IEnumerable<T>`.</span></span> <span data-ttu-id="73981-189">Dil sağlar `await foreach` üzerinden bu öğeleri, kullanma ve `yield return` öğeleri oluşturmak için onlara.</span><span class="sxs-lookup"><span data-stu-id="73981-189">The language lets you `await foreach` over these to consume their elements, and `yield return` to them to produce elements.</span></span>

<span data-ttu-id="73981-190">Aşağıdaki örnek, hem üretim hem de zaman uyumsuz akışlar kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="73981-190">The following example demonstrates both production and consumption of async streams.</span></span> <span data-ttu-id="73981-191">`foreach` Deyimi, async ve kendisini kullanan `yield return` arayanlar için zaman uyumsuz bir akış oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="73981-191">The `foreach` statement is async and itself uses `yield return` to produce an async stream for callers.</span></span> <span data-ttu-id="73981-192">Bu düzen (kullanarak `yield return`) zaman uyumsuz akışlar oluşturmayı için önerilen modelidir.</span><span class="sxs-lookup"><span data-stu-id="73981-192">This pattern (using `yield return`) is the recommended model for producing async streams.</span></span>

```csharp
async IAsyncEnumerable<int> GetBigResultsAsync()
{
    await foreach (var result in GetResultsAsync())
    {
        if (result > 20) yield return result; 
    }
}
```

> [!WARNING]
> <span data-ttu-id="73981-193">Şu anda sahip bir hata ile .NET core 3.0 Önizleme 1 `await foreach`.</span><span class="sxs-lookup"><span data-stu-id="73981-193">.NET Core 3.0 Preview 1 currently has a bug with `await foreach`.</span></span> <span data-ttu-id="73981-194">Bunun yerine, `GetEnumerator` ve `MoveNext` işlem öğeleri.</span><span class="sxs-lookup"><span data-stu-id="73981-194">Instead, use `GetEnumerator` and `MoveNext` to process elements.</span></span> <span data-ttu-id="73981-195">Daha fazla bilgi için [roslyn / #31268](https://github.com/dotnet/roslyn/issues/31268).</span><span class="sxs-lookup"><span data-stu-id="73981-195">For more information, see [roslyn/#31268](https://github.com/dotnet/roslyn/issues/31268).</span></span>

<span data-ttu-id="73981-196">İmkanına yanı sıra `await foreach`, zaman uyumsuz yineleyiciler, örneğin, döndüren bir yineleyicinin oluşturabilirsiniz bir `IAsyncEnumerable/IAsyncEnumerator` her ikisini yapabilirsiniz `await` ve `yield` içinde.</span><span class="sxs-lookup"><span data-stu-id="73981-196">In addition to being able to `await foreach`, you can also create async iterators, for example, an iterator that returns an `IAsyncEnumerable/IAsyncEnumerator` that you can both `await` and `yield` in.</span></span> <span data-ttu-id="73981-197">Çıkarılması gereken nesneler için kullanabileceğiniz `IAsyncDisposable`, çeşitli BCL türleri uygulayan, gibi `Stream` ve `Timer`.</span><span class="sxs-lookup"><span data-stu-id="73981-197">For objects that need to be disposed, you can use `IAsyncDisposable`, which various BCL types implement, such as `Stream` and `Timer`.</span></span>

> [!NOTE]
> <span data-ttu-id="73981-198">Yalnızca [ C# 8.0](https://blogs.msdn.microsoft.com/dotnet/2018/11/12/building-c-8-0/) destekler `await foreach` söz dizimi.</span><span class="sxs-lookup"><span data-stu-id="73981-198">Only [C# 8.0](https://blogs.msdn.microsoft.com/dotnet/2018/11/12/building-c-8-0/) supports `await foreach` syntax.</span></span>

## <a name="type-sequencereader"></a><span data-ttu-id="73981-199">Tür: SequenceReader</span><span class="sxs-lookup"><span data-stu-id="73981-199">Type: SequenceReader</span></span>

<span data-ttu-id="73981-200">.NET Core 3. 0'da, `System.Buffers.SequenceReader` Okuyucu için olarak kullanılabilecek eklendi `ReadOnlySequence<T>`.</span><span class="sxs-lookup"><span data-stu-id="73981-200">In .NET Core 3.0, `System.Buffers.SequenceReader` has been added which can be used as a reader for `ReadOnlySequence<T>`.</span></span> <span data-ttu-id="73981-201">Hızlı, yüksek performanslı, böylece düşük ayırma çözümlenmesi `System.IO.Pipelines` birden çok yedekleme arabellekler çapraz veri.</span><span class="sxs-lookup"><span data-stu-id="73981-201">This allows easy, high performance, low allocation parsing of `System.IO.Pipelines` data that can cross multiple backing buffers.</span></span> 

<span data-ttu-id="73981-202">Aşağıdaki örnek bir girişi sonu `Sequence` geçerli içine `CR/LF` satırları ayrılmış:</span><span class="sxs-lookup"><span data-stu-id="73981-202">The following example breaks an input `Sequence` into valid `CR/LF` delimited lines:</span></span>

```csharp
private static ReadOnlySpan<byte> CRLF => new byte[] { (byte)'\r', (byte)'\n' };

public static void ReadLines(ReadOnlySequence<byte> sequence)
{
    SequenceReader<byte> reader = new SequenceReader<byte>(sequence);

    while (!reader.End)
    {
        if (!reader.TryReadToAny(out ReadOnlySpan<byte> line, CRLF, advancePastDelimiter:false))
        {
            // Couldn't find another delimiter
            // ...
        }

        if (!reader.IsNext(CRLF, advancePast: true))
        {
            // Not a good CR/LF pair
            // ...
        }

        // line is valid, process
        ProcessLine(line);
    }
}
```

## <a name="type-metadataloadcontext"></a><span data-ttu-id="73981-203">Tür: MetadataLoadContext</span><span class="sxs-lookup"><span data-stu-id="73981-203">Type: MetadataLoadContext</span></span>

<span data-ttu-id="73981-204">`MetadataLoadContext` Türü okuma derleme sağlayan eklenmiş yapanın uygulama etki alanı etkilemeden meta verileri.</span><span class="sxs-lookup"><span data-stu-id="73981-204">The `MetadataLoadContext` type has been added that enables reading assembly metadata without affecting the caller’s application domain.</span></span> <span data-ttu-id="73981-205">Derlemeleri farklı mimariler ve geçerli çalışma zamanı ortamı daha platformlar için oluşturulmuş derlemeler de dahil olmak üzere veriler olarak okunur.</span><span class="sxs-lookup"><span data-stu-id="73981-205">Assemblies are read as data, including assemblies built for different architectures and platforms than the current runtime environment.</span></span> <span data-ttu-id="73981-206">`MetadataLoadContext` ile çakışıyor <xref:System.Reflection.Assembly.ReflectionOnlyLoad*>, hangi, yalnızca .NET Framework içinde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="73981-206">`MetadataLoadContext` overlaps with the <xref:System.Reflection.Assembly.ReflectionOnlyLoad*>, which is only available in the .NET Framework.</span></span>

<span data-ttu-id="73981-207">`MetdataLoadContext` kullanılabilir [System.Reflection.MetadataLoadContext paket](https://www.nuget.org/packages/System.Reflection.MetadataLoadContext).</span><span class="sxs-lookup"><span data-stu-id="73981-207">`MetdataLoadContext` is available in the [System.Reflection.MetadataLoadContext package](https://www.nuget.org/packages/System.Reflection.MetadataLoadContext).</span></span> <span data-ttu-id="73981-208">.NET Standard 2.0 bir pakettir.</span><span class="sxs-lookup"><span data-stu-id="73981-208">It is a .NET Standard 2.0 package.</span></span>

<span data-ttu-id="73981-209">`MetadataLoadContext` Benzer olan API'leri gösterir <xref:System.Runtime.Loader.AssemblyLoadContext> yazın, ancak bu türüne göre değil.</span><span class="sxs-lookup"><span data-stu-id="73981-209">The `MetadataLoadContext` exposes APIs similar to the <xref:System.Runtime.Loader.AssemblyLoadContext> type, but is not based on that type.</span></span> <span data-ttu-id="73981-210">Benzer şekilde <xref:System.Runtime.Loader.AssemblyLoadContext>, `MetadataLoadContext` evreni yükleniyor yalıtılmış bir derlemenin içinden yükleme derlemelerini etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="73981-210">Much like <xref:System.Runtime.Loader.AssemblyLoadContext>, the `MetadataLoadContext` enables loading assemblies within an isolated assembly loading universe.</span></span> <span data-ttu-id="73981-211">`MetdataLoadContext` API'leri dönüş <xref:System.Reflection.Assembly> bilinen yansıma API'leri kullanımını etkinleştirme nesneleri.</span><span class="sxs-lookup"><span data-stu-id="73981-211">`MetdataLoadContext` APIs return <xref:System.Reflection.Assembly> objects, enabling the use of familiar reflection APIs.</span></span> <span data-ttu-id="73981-212">Yürütme API'leri gibi odaklı [MethodBase.Invoke](https://github.com/dotnet/corefx/blob/master/src/System.Reflection.MetadataLoadContext/src/System/Reflection/TypeLoading/Methods/RoMethod.cs#L127), izin verilmeyen ve InvalidOperationException oluşturur.</span><span class="sxs-lookup"><span data-stu-id="73981-212">Execution-oriented APIs, such as [MethodBase.Invoke](https://github.com/dotnet/corefx/blob/master/src/System.Reflection.MetadataLoadContext/src/System/Reflection/TypeLoading/Methods/RoMethod.cs#L127), are not allowed and will throw InvalidOperationException.</span></span>

<span data-ttu-id="73981-213">Aşağıdaki örnek, belirli bir arabirimi uygulayan bir derlemede somut tür bulmak gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="73981-213">The following sample demonstrates how to find concrete types in an assembly that implements a given interface:</span></span>

```csharp
var paths = new string[] {@"C:\myapp\mscorlib.dll", @"C:\myapp\myapp.dll"};
var resolver = new PathAssemblyResolver(paths);
using (var lc = new MetadataLoadContext(resolver))
{
    Assembly a = lc.LoadFromAssemblyName("myapp");
    Type myInterface = a.GetType("MyApp.IPluginInterface");
    foreach (Type t in a.GetTypes())
    {
        if (t.IsClass && myInterface.IsAssignableFrom(t))
            Console.WriteLine($"Class {t.FullName} implements IPluginInterface");
    }
}
```

<span data-ttu-id="73981-214">Senaryolar için `MetadataLoadContext` tasarım zamanı özellikleri, araçları, derleme zamanı ve çalışma zamanı açık'li veri olarak bir derleme kümesi inceleyin ve tüm dosya kilitleri olması gereken özellikleri ve İnceleme sonra serbest bırakılan bellek gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="73981-214">Scenarios for `MetadataLoadContext` include design-time features, build-time tooling, and runtime light-up features that need to inspect a set of assemblies as data and have all file locks and memory freed after inspection is performed.</span></span>

<span data-ttu-id="73981-215">`MetadataLoadContext` Çözümleyici sınıfı geçirilen yapıcısına sahiptir.</span><span class="sxs-lookup"><span data-stu-id="73981-215">The `MetadataLoadContext` has a resolver class passed to its constructor.</span></span> <span data-ttu-id="73981-216">Çözümleyici'nin iş yüklenmesidir bir `Assembly` verilen kendi `AssemblyName`.</span><span class="sxs-lookup"><span data-stu-id="73981-216">The resolver's job is to load an `Assembly` given its `AssemblyName`.</span></span> <span data-ttu-id="73981-217">Özet çözümleyici sınıfı türetilen `MetadataAssemblyResolver` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="73981-217">The resolver class derives from the abstract `MetadataAssemblyResolver` class.</span></span> <span data-ttu-id="73981-218">Yol tabanlı senaryoları için çözümleyici uygulaması ile sağlanan `PathAssemblyResolver`.</span><span class="sxs-lookup"><span data-stu-id="73981-218">An implementation of the resolver for path-based scenarios is provided with `PathAssemblyResolver`.</span></span>

<span data-ttu-id="73981-219">[MetadataLoadContext testleri](https://github.com/dotnet/corefx/tree/master/src/System.Reflection.MetadataLoadContext/tests/src/Tests) birçok kullanım durumları gösterir.</span><span class="sxs-lookup"><span data-stu-id="73981-219">The [MetadataLoadContext tests](https://github.com/dotnet/corefx/tree/master/src/System.Reflection.MetadataLoadContext/tests/src/Tests) demonstrate many use cases.</span></span> <span data-ttu-id="73981-220">[Derleme testleri](https://github.com/dotnet/corefx/blob/master/src/System.Reflection.MetadataLoadContext/tests/src/Tests/Assembly/AssemblyTests.cs) başlatmak için iyi bir yerdir.</span><span class="sxs-lookup"><span data-stu-id="73981-220">The [Assembly tests](https://github.com/dotnet/corefx/blob/master/src/System.Reflection.MetadataLoadContext/tests/src/Tests/Assembly/AssemblyTests.cs) are a good place to start.</span></span>

## <a name="tls-13--openssl-111-on-linux"></a><span data-ttu-id="73981-221">TLS 1.3 & Linux'ta OpenSSL 1.1.1</span><span class="sxs-lookup"><span data-stu-id="73981-221">TLS 1.3 & OpenSSL 1.1.1 on Linux</span></span>

<span data-ttu-id="73981-222">.NET core artık avantajlarından yararlanın [OpenSSL 1.1.1 TLS 1.3 desteği](https://www.openssl.org/blog/blog/2018/09/11/release111/), verilen ortamda kullanılabilir olduğunda.</span><span class="sxs-lookup"><span data-stu-id="73981-222">.NET Core will now take advantage of [TLS 1.3 support in OpenSSL 1.1.1](https://www.openssl.org/blog/blog/2018/09/11/release111/), when it is available in a given environment.</span></span> <span data-ttu-id="73981-223">Her TLS 1,3 birden çok avantaj vardır [OpenSSL takım](https://www.openssl.org/blog/blog/2018/09/11/release111/):</span><span class="sxs-lookup"><span data-stu-id="73981-223">There are multiple benefits of TLS 1.3, per the [OpenSSL team](https://www.openssl.org/blog/blog/2018/09/11/release111/):</span></span>

* <span data-ttu-id="73981-224">Geliştirilmiş bağlantı süreleri nedeniyle bir azalma istemci ve sunucu arasında gerekli gidiş dönüş sayısı.</span><span class="sxs-lookup"><span data-stu-id="73981-224">Improved connection times due to a reduction in the number of round trips required between the client and server.</span></span>

* <span data-ttu-id="73981-225">Geliştirilmiş güvenlik çeşitli eski ve güvenli şifreleme algoritmaları kaldırılmasını ve daha fazla bağlantı el sıkışması şifrelenmesi nedeniyle.</span><span class="sxs-lookup"><span data-stu-id="73981-225">Improved security due to the removal of various obsolete and insecure cryptographic algorithms and encryption of more of the connection handshake.</span></span>

<span data-ttu-id="73981-226">.NET core 3.0 Önizleme 1 yararlanarak özellikli **OpenSSL 1.1.1**, **OpenSSL 1.1.0**, veya **OpenSSL 1.0.2** (ne olursa olsun bulunan en iyi, bir Linux sisteminde sürümüdür).</span><span class="sxs-lookup"><span data-stu-id="73981-226">.NET Core 3.0 Preview 1 is capable of utilizing **OpenSSL 1.1.1**, **OpenSSL 1.1.0**, or **OpenSSL 1.0.2** (whatever the best version found is, on a Linux system).</span></span>  <span data-ttu-id="73981-227">Zaman **OpenSSL 1.1.1** olduğu SslStream ve HttpClient türleri kullanılabilir kullanacağı **TLS 1.3** kullanırken `SslProtocols.None` (sistem varsayılan protokol), istemci ve sunucu desteği varsayılarak**TLS 1.3**.</span><span class="sxs-lookup"><span data-stu-id="73981-227">When **OpenSSL 1.1.1** is available the SslStream and HttpClient types will use **TLS 1.3** when using `SslProtocols.None` (system default protocols), assuming both the client and server support **TLS 1.3**.</span></span>

<span data-ttu-id="73981-228">.NET Core 3.0 Önizleme 1 Ubuntu 18.10 bağlanmak için aşağıdaki örnekte gösterilmiştir <https://www.cloudflare.com>:</span><span class="sxs-lookup"><span data-stu-id="73981-228">The following sample demonstrates .NET Core 3.0 Preview 1 on Ubuntu 18.10 connecting to <https://www.cloudflare.com>:</span></span>

```csharp
using System;
using System.Net.Security;
using System.Net.Sockets;
using System.Threading.Tasks;

namespace tlstest
{
    class Program
    {
        static async Task Main()
        {
            using (TcpClient tcpClient = new TcpClient())
            {
                string targetHost = "www.cloudflare.com";

                await tcpClient.ConnectAsync(targetHost, 443);

                using (SslStream sslStream = new SslStream(tcpClient.GetStream()))
                {
                    await sslStream.AuthenticateAsClientAsync(targetHost);
                    await Console.Out.WriteLineAsync($"Connected to {targetHost} with {sslStream.SslProtocol}");
                }
            }
        }
    }
}
```

```console
user@comp-ubuntu1810:~/tlstest$ dotnet run
Connected to www.cloudflare.com with Tls13
user@comp-ubuntu1810:~/tlstest$ openssl version
OpenSSL 1.1.1  11 Sep 2018
```

>[!IMPORTANT]
><span data-ttu-id="73981-229">Windows ve macOS henüz desteklemediği **TLS 1.3**.</span><span class="sxs-lookup"><span data-stu-id="73981-229">Windows and macOS do not yet support **TLS 1.3**.</span></span> <span data-ttu-id="73981-230">.NET core 3.0 destekleyeceği **TLS 1.3** desteği kullanılabilir olduğunda bu işletim sistemlerinde.</span><span class="sxs-lookup"><span data-stu-id="73981-230">.NET Core 3.0 will support **TLS 1.3** on these operating systems when support becomes available.</span></span>

## <a name="cryptography"></a><span data-ttu-id="73981-231">Şifreleme</span><span class="sxs-lookup"><span data-stu-id="73981-231">Cryptography</span></span>

<span data-ttu-id="73981-232">İçin destek eklenmiştir **AES GCM** ve **AES-CCM** aracılığıyla uygulanan şifrelemeleri, `System.Security.Cryptography.AesGcm` ve `System.Security.Cryptography.AesCcm`.</span><span class="sxs-lookup"><span data-stu-id="73981-232">Support has been added for **AES-GCM** and **AES-CCM** ciphers, implemented via `System.Security.Cryptography.AesGcm` and `System.Security.Cryptography.AesCcm`.</span></span> <span data-ttu-id="73981-233">Her ikisi de bu algoritmalar olan [ilişkilendirme veri (AEAD) algoritmaları ile kimliği doğrulanmış şifreleme](https://en.wikipedia.org/wiki/Authenticated_encryption)ve .NET Core için eklenen ilk kimliği doğrulanmış şifreleme (AE) algoritmaları.</span><span class="sxs-lookup"><span data-stu-id="73981-233">These algorithms are both [Authenticated Encryption with Association Data (AEAD) algorithms](https://en.wikipedia.org/wiki/Authenticated_encryption), and the first Authenticated Encryption (AE) algorithms added to .NET Core.</span></span>

<span data-ttu-id="73981-234">Aşağıdaki kodu **AesGcm** şifrelemek ve rastgele verilerin şifresini çözmek için şifre.</span><span class="sxs-lookup"><span data-stu-id="73981-234">The following code demonstrates using **AesGcm** cipher to encrypt and decrypt random data.</span></span>

<span data-ttu-id="73981-235">Kodu **AesCcm** (sınıf değişken adları farklı olacaktır yalnızca) neredeyse aynı görünür.</span><span class="sxs-lookup"><span data-stu-id="73981-235">The code for **AesCcm** would look almost identical (only the class variable names would be different).</span></span>

```csharp
// key should be: pre-known, derived, or transported via another channel, such as RSA encryption
byte[] key = new byte[16];
RandomNumberGenerator.Fill(key);

byte[] nonce = new byte[12];
RandomNumberGenerator.Fill(nonce);

// normally this would be your data
byte[] dataToEncrypt = new byte[1234];
byte[] associatedData = new byte[333];
RandomNumberGenerator.Fill(dataToEncrypt);
RandomNumberGenerator.Fill(associatedData);

// these will be filled during the encryption
byte[] tag = new byte[16];
byte[] ciphertext = new byte[dataToEncrypt.Length];

using (AesGcm aesGcm = new AesGcm(key))
{
    aesGcm.Encrypt(nonce, dataToEncrypt, ciphertext, tag, associatedData);
}

// tag, nonce, ciphertext, associatedData should be sent to the other part

byte[] decryptedData = new byte[ciphertext.Length];

using (AesGcm aesGcm = new AesGcm(key))
{
    aesGcm.Decrypt(nonce, ciphertext, tag, decryptedData, associatedData);
}

// do something with the data
// this should always print that data is the same
Console.WriteLine($"AES-GCM: Decrypted data is{(dataToEncrypt.SequenceEqual(decryptedData) ? "the same as" : "different than")} original data.");
```

## <a name="cryptographic-key-importexport"></a><span data-ttu-id="73981-236">Şifreleme anahtarı içeri/dışarı aktarma</span><span class="sxs-lookup"><span data-stu-id="73981-236">Cryptographic Key Import/Export</span></span>

<span data-ttu-id="73981-237">.NET core 3.0 Önizleme 1 içeri ve dışarı aktarmayı asimetrik ortak ve özel anahtarlar standart biçimlerinden bir X.509 sertifikası kullanmak zorunda kalmadan destekler.</span><span class="sxs-lookup"><span data-stu-id="73981-237">.NET Core 3.0 Preview 1 supports the import and export of asymmetric public and private keys from standard formats, without needing to use an X.509 certificate.</span></span>

<span data-ttu-id="73981-238">Tüm anahtar türleri (RSA, DSA, ECDsa, ECDiffieHellman) desteği **X.509 SubjectPublicKeyInfo** biçimi için ortak anahtarları ve **PKCS #8 PrivateKeyInfo** ve **PKCS #8 EncryptedPrivateKeyInfo**  biçimleri özel anahtarlar için.</span><span class="sxs-lookup"><span data-stu-id="73981-238">All key types (RSA, DSA, ECDsa, ECDiffieHellman) support the **X.509 SubjectPublicKeyInfo** format for public keys, and the **PKCS#8 PrivateKeyInfo** and **PKCS#8 EncryptedPrivateKeyInfo** formats for private keys.</span></span> <span data-ttu-id="73981-239">RSA ayrıca destekler **PKCS #1 RSAPublicKey** ve **PKCS #1 RSAPrivateKey**.</span><span class="sxs-lookup"><span data-stu-id="73981-239">RSA additionally supports **PKCS#1 RSAPublicKey** and **PKCS#1 RSAPrivateKey**.</span></span> <span data-ttu-id="73981-240">Tüm verme yöntemleri DER ile kodlanmış ikili verileri oluşturmak ve içeri aktarma metotları aynı beklerler.</span><span class="sxs-lookup"><span data-stu-id="73981-240">The export methods all produce DER-encoded binary data, and the import methods expect the same.</span></span> <span data-ttu-id="73981-241">Bir anahtar metin dostu PEM biçiminde depolanır, çağırana base64 gerekir-içerik alma yöntemini çağırmadan önce kod çözme.</span><span class="sxs-lookup"><span data-stu-id="73981-241">If a key is stored in the text-friendly PEM format, the caller will need to base64-decode the content before calling an import method.</span></span>

```csharp
using System;
using System.IO;
using System.Security.Cryptography;

namespace rsakeyprint
{
    class Program
    {
        static void Main(string[] args)
        {
            using (RSA rsa = RSA.Create())
            {
                byte[] keyBytes = File.ReadAllBytes(args[0]);
                rsa.ImportRSAPrivateKey(keyBytes, out int bytesRead);
 
                Console.WriteLine($"Read {bytesRead} bytes, {keyBytes.Length-bytesRead} extra byte(s) in file.");
                RSAParameters rsaParameters = rsa.ExportParameters(true);
                Console.WriteLine(BitConverter.ToString(rsaParameters.D));
            }
        }
    }
}
```

```console
user@comp-ubuntu1810:~/rsakeyprint$ echo Making a small key to save on screen space.
Making a small key to save on screen space.
user@comp-ubuntu1810:~/rsakeyprint$ openssl genrsa 768 | openssl rsa -outform der -out rsa.key
Generating RSA private key, 768 bit long modulus (2 primes)
..+++++++
........+++++++
e is 65537 (0x010001)
writing RSA key
user@comp-ubuntu1810:~/rsakeyprint$ dotnet run rsa.key
Read 461 bytes, 0 extra byte(s) in file.
0F-D0-82-34-F8-13-38-4A-7F-C7-52-4A-F6-93-F8-FB-6D-98-7A-6A-04-3B-BC-35-8C-7D-AC-A5-A3-6E-AD-C1-66-30-81-2C-2A-DE-DA-60-03-6A-2C-D9-76-15-7F-61-97-57-
79-E1-6E-45-62-C3-83-04-97-CB-32-EF-C5-17-5F-99-60-92-AE-B6-34-6F-30-06-03-AC-BF-15-24-43-84-EB-83-60-EF-4D-3B-BD-D9-5D-56-26-F0-51-CE-F1
user@comp-ubuntu1810:~/rsakeyprint$ openssl rsa -in rsa.key -inform der -text -noout | grep -A7 private
privateExponent:
    0f:d0:82:34:f8:13:38:4a:7f:c7:52:4a:f6:93:f8:
    fb:6d:98:7a:6a:04:3b:bc:35:8c:7d:ac:a5:a3:6e:
    ad:c1:66:30:81:2c:2a:de:da:60:03:6a:2c:d9:76:
    15:7f:61:97:57:79:e1:6e:45:62:c3:83:04:97:cb:
    32:ef:c5:17:5f:99:60:92:ae:b6:34:6f:30:06:03:
    ac:bf:15:24:43:84:eb:83:60:ef:4d:3b:bd:d9:5d:
    56:26:f0:51:ce:f1
```

<span data-ttu-id="73981-242">PKCS #8 dosya inceledi ile `System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="73981-242">PKCS#8 files can be inspected with the `System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo` class.</span></span>

<span data-ttu-id="73981-243">PFX/PKCS #12 dosyaları inceledi ve ile yönetilebilir `System.Security.Cryptography.Pkcs.Pkcs12Info` ve `System.Security.Cryptography.Pkcs.Pkcs12Builder`sırasıyla.</span><span class="sxs-lookup"><span data-stu-id="73981-243">PFX/PKCS#12 files can be inspected and manipulated with `System.Security.Cryptography.Pkcs.Pkcs12Info` and `System.Security.Cryptography.Pkcs.Pkcs12Builder`, respectively.</span></span>

## <a name="serialport-for-linux"></a><span data-ttu-id="73981-244">Linux için çevirmek için SerialPort</span><span class="sxs-lookup"><span data-stu-id="73981-244">SerialPort for Linux</span></span>

<span data-ttu-id="73981-245">.NET core 3.0 destekler <xref:System.IO.Ports.SerialPort?displayProperty=nameWithType> Linux üzerinde.</span><span class="sxs-lookup"><span data-stu-id="73981-245">.NET Core 3.0 now supports <xref:System.IO.Ports.SerialPort?displayProperty=nameWithType> on Linux.</span></span>

<span data-ttu-id="73981-246">Daha önce yalnızca kullanarak desteklenen .NET Core `SerialPort` Windows türü.</span><span class="sxs-lookup"><span data-stu-id="73981-246">Previously, .NET Core only supported using the `SerialPort` type on Windows.</span></span>

## <a name="more-bcl-improvements"></a><span data-ttu-id="73981-247">Daha fazla BCL geliştirmeleri</span><span class="sxs-lookup"><span data-stu-id="73981-247">More BCL Improvements</span></span>

<span data-ttu-id="73981-248">`Span<T>`, `Memory<T>`, Ve .NET Core 2.1 içinde tanıtılan ilgili türleri de .NET Core 3.0 için iyileştirilmiş.</span><span class="sxs-lookup"><span data-stu-id="73981-248">The `Span<T>`, `Memory<T>`, and related types that were introduced in .NET Core 2.1, have been optimized in .NET Core 3.0.</span></span> <span data-ttu-id="73981-249">Sık kullanılan işlemler gibi yapı span, dilimleme, ayrıştırma ve biçimlendirme artık daha iyi gerçekleştirin.</span><span class="sxs-lookup"><span data-stu-id="73981-249">Common operations such as span construction, slicing, parsing, and formatting now perform better.</span></span> 

<span data-ttu-id="73981-250">Ayrıca, türleri ister `String` anahtarlarla olarak kullanıldığında daha verimli hale getirmek için altında--kapak geliştirmeleri gördünüz `Dictionary<TKey, TValue>` ve diğer koleksiyonları.</span><span class="sxs-lookup"><span data-stu-id="73981-250">Additionally, types like `String` have seen under-the-cover improvements to make them more efficient when used as keys with `Dictionary<TKey, TValue>` and other collections.</span></span> <span data-ttu-id="73981-251">Kod değişikliği olmadan bu iyileştirmeleri yararlanmak için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="73981-251">No code changes are required to benefit from these improvements.</span></span>

<span data-ttu-id="73981-252">Aşağıdaki geliştirmeler de .NET Core 3 Önizleme 1'de yenidir:</span><span class="sxs-lookup"><span data-stu-id="73981-252">The following improvements are also new in .NET Core 3 Preview 1:</span></span>

* <span data-ttu-id="73981-253">HttpClient için yerleşik Brotli desteği</span><span class="sxs-lookup"><span data-stu-id="73981-253">Brotli support built in to HttpClient</span></span>
* <span data-ttu-id="73981-254">ThreadPool.UnsafeQueueWorkItem(IThreadPoolWorkItem)</span><span class="sxs-lookup"><span data-stu-id="73981-254">ThreadPool.UnsafeQueueWorkItem(IThreadPoolWorkItem)</span></span>
* <span data-ttu-id="73981-255">Unsafe.Unbox</span><span class="sxs-lookup"><span data-stu-id="73981-255">Unsafe.Unbox</span></span>
* <span data-ttu-id="73981-256">CancellationToken.Unregister</span><span class="sxs-lookup"><span data-stu-id="73981-256">CancellationToken.Unregister</span></span>
* <span data-ttu-id="73981-257">Karmaşık aritmetik işleçler</span><span class="sxs-lookup"><span data-stu-id="73981-257">Complex arithmetic operators</span></span>
* <span data-ttu-id="73981-258">TCP için yuva API'leri Canlı</span><span class="sxs-lookup"><span data-stu-id="73981-258">Socket APIs for TCP keep alive</span></span>
* <span data-ttu-id="73981-259">StringBuilder.GetChunks</span><span class="sxs-lookup"><span data-stu-id="73981-259">StringBuilder.GetChunks</span></span>
* <span data-ttu-id="73981-260">Ayrıştırma IPEndPoint</span><span class="sxs-lookup"><span data-stu-id="73981-260">IPEndPoint parsing</span></span>
* <span data-ttu-id="73981-261">RandomNumberGenerator.GetInt32</span><span class="sxs-lookup"><span data-stu-id="73981-261">RandomNumberGenerator.GetInt32</span></span>

## <a name="tiered-compilation"></a><span data-ttu-id="73981-262">Katmanlı derleme</span><span class="sxs-lookup"><span data-stu-id="73981-262">Tiered compilation</span></span>

<span data-ttu-id="73981-263">[Katmanlı derleme](https://blogs.msdn.microsoft.com/dotnet/2018/08/02/tiered-compilation-preview-in-net-core-2-1/) .NET Core 3.0 ile varsayılan olarak açıktır.</span><span class="sxs-lookup"><span data-stu-id="73981-263">[Tiered compilation](https://blogs.msdn.microsoft.com/dotnet/2018/08/02/tiered-compilation-preview-in-net-core-2-1/) is on by default with .NET Core 3.0.</span></span> <span data-ttu-id="73981-264">Daha fazla Desenlerinizi başlangıçta hem de daha iyi performans almak ve aktarım hızını en üst düzeye çıkarmak için tam zamanında (JIT) derleyici kullanmak çalışma zamanı sağlayan bir özelliktir.</span><span class="sxs-lookup"><span data-stu-id="73981-264">It is a feature that enables the runtime to more adaptively use the Just-In-Time (JIT) compiler to get better performance, both at startup and to maximize throughput.</span></span>

<span data-ttu-id="73981-265">Bu özellik bir Tercihli özellik olarak eklenmiştir [.NET Core 2.1](https://blogs.msdn.microsoft.com/dotnet/2018/05/30/announcing-net-core-2-1/) ve varsayılan olarak etkinleştirildi [.NET Core 2.2 Önizleme 2](https://blogs.msdn.microsoft.com/dotnet/2018/09/12/announcing-net-core-2-2-preview-2/).</span><span class="sxs-lookup"><span data-stu-id="73981-265">This feature was added as an opt-in feature in [.NET Core 2.1](https://blogs.msdn.microsoft.com/dotnet/2018/05/30/announcing-net-core-2-1/) and then was enabled by default in [.NET Core 2.2 Preview 2](https://blogs.msdn.microsoft.com/dotnet/2018/09/12/announcing-net-core-2-2-preview-2/).</span></span> <span data-ttu-id="73981-266">Daha sonra yeniden oturum .NET Core 2.2 sürüm geri çevirmek için döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="73981-266">Subsequently, it has been reverted back to opt in with the .NET Core 2.2 release.</span></span>

## <a name="arm64-linux-support"></a><span data-ttu-id="73981-267">ARM64 Linux desteği</span><span class="sxs-lookup"><span data-stu-id="73981-267">ARM64 Linux support</span></span>

<span data-ttu-id="73981-268">ARM64 Linux bu yayın için destek ekliyoruz.</span><span class="sxs-lookup"><span data-stu-id="73981-268">We are adding support for ARM64 for Linux this release.</span></span> <span data-ttu-id="73981-269">Bağlam için .NET Core 2.1 ile Linux ve Windows ile .NET Core 2.2 ARM32 için destek ekledik.</span><span class="sxs-lookup"><span data-stu-id="73981-269">For context, we added support for ARM32 for Linux with .NET Core 2.1 and Windows with .NET Core 2.2.</span></span> <span data-ttu-id="73981-270">ARM64 için birincil kullanım durumu şu anda IOT senaryoları ile aşamasındadır.</span><span class="sxs-lookup"><span data-stu-id="73981-270">The primary use case for ARM64 is currently with IoT scenarios.</span></span>

<span data-ttu-id="73981-271">Alpine, Debian ve Ubuntu [ARM64 için .NET Core için Docker görüntüleri kullanılabilir](https://hub.docker.com/r/microsoft/dotnet/).</span><span class="sxs-lookup"><span data-stu-id="73981-271">Alpine, Debian and Ubuntu [Docker images are available for .NET Core for ARM64](https://hub.docker.com/r/microsoft/dotnet/).</span></span>

<span data-ttu-id="73981-272">Lütfen denetleyin [.NET Core ARM64 durumu](https://github.com/dotnet/announcements/issues/82) daha fazla bilgi için.</span><span class="sxs-lookup"><span data-stu-id="73981-272">Please check [.NET Core ARM64 Status](https://github.com/dotnet/announcements/issues/82) for more information.</span></span>

>[!NOTE]
> <span data-ttu-id="73981-273">**ARM64** Windows Destek işlemi henüz kullanılamıyor.</span><span class="sxs-lookup"><span data-stu-id="73981-273">**ARM64** Windows support isn't yet available.</span></span>
