---
title: Tek dosya uygulaması
description: Tek bir dosya uygulamasının ne olduğunu ve neden bu uygulama dağıtım modelini kullanmayı düşünmeniz gerektiğini öğrenin.
author: lakshanf
ms.author: lakshanf
ms.date: 08/28/2020
ms.openlocfilehash: 0167e62ea46e1c23c3d4ef6ea505ee051ffaf264
ms.sourcegitcommit: d66641bc7c14ad7d02300316e9e7e84a875a0a72
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/05/2020
ms.locfileid: "91712645"
---
# <a name="single-file-deployment-and-executable"></a><span data-ttu-id="e5a2d-103">Tek dosya dağıtımı ve yürütülebilir dosya</span><span class="sxs-lookup"><span data-stu-id="e5a2d-103">Single file deployment and executable</span></span>

<span data-ttu-id="e5a2d-104">Uygulamaya bağımlı tüm dosyaları tek bir ikiliye paketlemek, uygulamayı tek bir dosya olarak dağıtmak ve dağıtmak için çekici bir seçeneğe sahip bir uygulama geliştiricisi sağlar.</span><span class="sxs-lookup"><span data-stu-id="e5a2d-104">Bundling all application-dependent files into a single binary provides an application developer with the attractive option to deploy and distribute the application as a single file.</span></span> <span data-ttu-id="e5a2d-105">Bu dağıtım modeli .NET Core 3,0 ' den beri kullanılabilir ve .NET 5,0 ' de geliştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="e5a2d-105">This deployment model has been available since .NET Core 3.0 and has been enhanced in .NET 5.0.</span></span> <span data-ttu-id="e5a2d-106">Daha önce .NET Core 3,0 ' de, bir kullanıcı tek dosya uygulamanızı çalıştırdığında, .NET Core ana bilgisayarı önce uygulamayı çalıştırmadan önce tüm dosyaları geçici bir dizine ayıklar.</span><span class="sxs-lookup"><span data-stu-id="e5a2d-106">Previously in .NET Core 3.0, when a user runs your single-file app, .NET Core host first extracts all files to a temporary directory before running the application.</span></span> <span data-ttu-id="e5a2d-107">.NET 5,0, dosyaları uygulamadan çıkarmaya gerek olmadan doğrudan kodu çalıştırarak bu deneyimi geliştirir.</span><span class="sxs-lookup"><span data-stu-id="e5a2d-107">.NET 5.0 improves this experience by directly running the code without the need to extract the files from the app.</span></span>

<span data-ttu-id="e5a2d-108">Tek dosya dağıtımı, hem [çerçeveye bağımlı dağıtım modeli](index.md#publish-framework-dependent) hem de [kendi içinde bulunan uygulamalar](index.md#publish-self-contained)için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="e5a2d-108">Single File deployment is available for both the [framework-dependent deployment model](index.md#publish-framework-dependent) and [self-contained applications](index.md#publish-self-contained).</span></span> <span data-ttu-id="e5a2d-109">Bağımsız bir uygulamadaki tek dosyanın boyutu, çalışma zamanı ve çerçeve kitaplıklarını dahil edecek şekilde büyük olacaktır.</span><span class="sxs-lookup"><span data-stu-id="e5a2d-109">The size of the single file in a self-contained application will be large since it will include the runtime and the framework libraries.</span></span> <span data-ttu-id="e5a2d-110">Tek dosya dağıtım seçeneği, [Readytorun](../tools/dotnet-publish.md) ve [Trim (.NET 5,0 ' de deneysel bir özellik)](trim-self-contained.md) yayımlama seçenekleri ile birleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="e5a2d-110">The single file deployment option can be combined with [ReadyToRun](../tools/dotnet-publish.md) and [Trim (an experimental feature in .NET 5.0)](trim-self-contained.md) publish options.</span></span>

## <a name="api-incompatibility"></a><span data-ttu-id="e5a2d-111">API uyumsuzluğu</span><span class="sxs-lookup"><span data-stu-id="e5a2d-111">API incompatibility</span></span>

<span data-ttu-id="e5a2d-112">Bazı API 'Ler tek dosya dağıtımıyla uyumlu değildir ve uygulamalar bu API 'Leri kullanıyorsa değişiklik yapılmasını gerektirebilir.</span><span class="sxs-lookup"><span data-stu-id="e5a2d-112">Some APIs are not compatible with single-file deployment and applications may require modification if they use these APIs.</span></span> <span data-ttu-id="e5a2d-113">Üçüncü taraf bir Framework veya paket kullanıyorsanız, bu API 'lerden birini de kullanabilir ve değişiklik yapmanız gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="e5a2d-113">If you use a third-party framework or package, it's possible that they may also use one of these APIs and need modification.</span></span> <span data-ttu-id="e5a2d-114">Sorunların en yaygın nedeni, uygulamayla birlikte gelen dosyalar veya dll 'Ler için dosya yollarında bağımlılığını temel alır.</span><span class="sxs-lookup"><span data-stu-id="e5a2d-114">The most common cause of problems is dependence on file paths for files or DLLs shipped with the application.</span></span>

<span data-ttu-id="e5a2d-115">Aşağıdaki tabloda, tek dosya kullanımı için ilgili çalışma zamanı kitaplığı API 'SI ayrıntıları bulunur.</span><span class="sxs-lookup"><span data-stu-id="e5a2d-115">The table below has the relevant runtime library API details for single-file use.</span></span>

| <span data-ttu-id="e5a2d-116">API</span><span class="sxs-lookup"><span data-stu-id="e5a2d-116">API</span></span>                            | <span data-ttu-id="e5a2d-117">Not</span><span class="sxs-lookup"><span data-stu-id="e5a2d-117">Note</span></span>                                                                   |
|--------------------------------|------------------------------------------------------------------------|
| `Assembly.Location`            | <span data-ttu-id="e5a2d-118">Boş bir dize döndürür.</span><span class="sxs-lookup"><span data-stu-id="e5a2d-118">Returns an empty string.</span></span>                                               |
| `Module.FullyQualifiedName`    | <span data-ttu-id="e5a2d-119">Değerine sahip bir dize döndürür `<Unknown>` veya bir özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="e5a2d-119">Returns a string with the value of `<Unknown>` or throws an exception.</span></span> |
| `Module.Name`                  | <span data-ttu-id="e5a2d-120">Değerine sahip bir dize döndürür `<Unknown>` .</span><span class="sxs-lookup"><span data-stu-id="e5a2d-120">Returns a string with the value of `<Unknown>`.</span></span>                        |
| `Assembly.GetFile`             | <span data-ttu-id="e5a2d-121">Atar <xref:System.IO.IOException> .</span><span class="sxs-lookup"><span data-stu-id="e5a2d-121">Throws <xref:System.IO.IOException>.</span></span>                                   |
| `Assembly.GetFiles`            | <span data-ttu-id="e5a2d-122">Atar <xref:System.IO.IOException> .</span><span class="sxs-lookup"><span data-stu-id="e5a2d-122">Throws <xref:System.IO.IOException>.</span></span>                                   |
| `Assembly.CodeBase`            | <span data-ttu-id="e5a2d-123">Atar <xref:System.PlatformNotSupportedException> .</span><span class="sxs-lookup"><span data-stu-id="e5a2d-123">Throws <xref:System.PlatformNotSupportedException>.</span></span>                    |
| `Assembly.EscapedCodeBase`     | <span data-ttu-id="e5a2d-124">Atar <xref:System.PlatformNotSupportedException> .</span><span class="sxs-lookup"><span data-stu-id="e5a2d-124">Throws <xref:System.PlatformNotSupportedException>.</span></span>                    |
| `AssemblyName.CodeBase`        | <span data-ttu-id="e5a2d-125">`null` döndürür.</span><span class="sxs-lookup"><span data-stu-id="e5a2d-125">Returns `null`.</span></span>                                                        |
| `AssemblyName.EscapedCodeBase` | <span data-ttu-id="e5a2d-126">`null` döndürür.</span><span class="sxs-lookup"><span data-stu-id="e5a2d-126">Returns `null`.</span></span>                                                        |

<span data-ttu-id="e5a2d-127">Yaygın senaryoları düzeltmeye yönelik bazı önerileriniz var:</span><span class="sxs-lookup"><span data-stu-id="e5a2d-127">We have some recommendations for fixing common scenarios:</span></span>

* <span data-ttu-id="e5a2d-128">Yürütülebilir dosyanın yanındaki dosyalara erişmek için kullanın <xref:System.AppContext.BaseDirectory?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="e5a2d-128">To access files next to the executable, use <xref:System.AppContext.BaseDirectory?displayProperty=nameWithType>.</span></span>

* <span data-ttu-id="e5a2d-129">Yürütülebilir dosyanın dosya adını bulmak için ilk öğesini kullanın <xref:System.Environment.GetCommandLineArgs?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="e5a2d-129">To find the file name of the executable, use the first element of <xref:System.Environment.GetCommandLineArgs?displayProperty=nameWithType>.</span></span>

* <span data-ttu-id="e5a2d-130">Gevşek dosyaları tamamen sevk etmeyi önlemek için, [gömülü kaynakları](../../framework/resources/creating-resource-files-for-desktop-apps.md)kullanmayı düşünün.</span><span class="sxs-lookup"><span data-stu-id="e5a2d-130">To avoid shipping loose files entirely, consider using [embedded resources](../../framework/resources/creating-resource-files-for-desktop-apps.md).</span></span>

## <a name="attaching-a-debugger"></a><span data-ttu-id="e5a2d-131">Hata ayıklayıcı iliştirme</span><span class="sxs-lookup"><span data-stu-id="e5a2d-131">Attaching a debugger</span></span>

<span data-ttu-id="e5a2d-132">Linux 'ta, kendi içinde tek dosya işlemlerine veya hata ayıklama kilitlenme dökümlerine ekleyebileceğiniz tek hata ayıklayıcı [LLDB Ile sos](../diagnostics/dotnet-sos.md)olur.</span><span class="sxs-lookup"><span data-stu-id="e5a2d-132">On Linux, the only debugger which can attach to self-contained single-file processes or debug crash dumps is [SOS with LLDB](../diagnostics/dotnet-sos.md).</span></span>

<span data-ttu-id="e5a2d-133">Windows ve Mac 'te, kilitlenme dökümlerinde hata ayıklamak için Visual Studio ve VS Code kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="e5a2d-133">On Windows and Mac, Visual Studio and VS Code can be used to debug crash dumps.</span></span> <span data-ttu-id="e5a2d-134">Çalışan bir bağımsız tek dosya yürütülebiliri eklemek için ek bir dosya gerekir: _mscordbi. { dll, so}_.</span><span class="sxs-lookup"><span data-stu-id="e5a2d-134">Attaching to a running self-contained single-file executable requires an extra file: _mscordbi.{dll,so}_.</span></span>

<span data-ttu-id="e5a2d-135">Bu dosya olmadan, Visual Studio "işleme iliştirilemiyor" hatasını verebilir.</span><span class="sxs-lookup"><span data-stu-id="e5a2d-135">Without this file Visual Studio may produce the error "Unable to attach to the process.</span></span> <span data-ttu-id="e5a2d-136">Bir hata ayıklama bileşeni yüklü değil. "</span><span class="sxs-lookup"><span data-stu-id="e5a2d-136">A debug component is not installed."</span></span> <span data-ttu-id="e5a2d-137">VS Code, "işleme iliştirilemedi: bilinmeyen hata: 0x80131c3c" hatasını verebilir.</span><span class="sxs-lookup"><span data-stu-id="e5a2d-137">and VS Code may produce the error "Failed to attach to process: Unknown Error: 0x80131c3c."</span></span>

<span data-ttu-id="e5a2d-138">Bu hataları onarmak için, _mscordbi_ 'nin yürütülebilir dosyanın yanına kopyalanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="e5a2d-138">To fix these errors, _mscordbi_ needs to be copied next to the executable.</span></span> <span data-ttu-id="e5a2d-139">_mscordbi_ , `publish` Varsayılan olarak UYGULAMANıN çalışma zamanı kimliğine sahip alt dizinde oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="e5a2d-139">_mscordbi_ is `publish`ed by default in the subdirectory with the application's runtime ID.</span></span> <span data-ttu-id="e5a2d-140">Bu nedenle, örneğin, parametreleri kullanarak Windows için CLI kullanarak kendi kendini içeren tek dosya yürütülebilir dosyası `dotnet` `-r win-x64` yayımlamasaydı, yürütülebilir dosya _bin/Debug/net 5.0/Win-x64/Publish_öğesine yerleştirilir.</span><span class="sxs-lookup"><span data-stu-id="e5a2d-140">So, for example, if one were to publish a self-contained single-file executable using the `dotnet` CLI for Windows using the parameters `-r win-x64`, the executable would be placed in _bin/Debug/net5.0/win-x64/publish_.</span></span> <span data-ttu-id="e5a2d-141">_Bin/Debug/net 5.0/Win-x64_içinde _mscordbi.dll_ bir kopyası var olabilir.</span><span class="sxs-lookup"><span data-stu-id="e5a2d-141">A copy of _mscordbi.dll_ would be present in _bin/Debug/net5.0/win-x64_.</span></span>

## <a name="other-considerations"></a><span data-ttu-id="e5a2d-142">Diğer önemli noktalar</span><span class="sxs-lookup"><span data-stu-id="e5a2d-142">Other considerations</span></span>

<span data-ttu-id="e5a2d-143">Tek dosya varsayılan olarak yerel kitaplıkları paketetmez.</span><span class="sxs-lookup"><span data-stu-id="e5a2d-143">Single-file doesn't bundle native libraries by default.</span></span> <span data-ttu-id="e5a2d-144">Linux 'ta çalışma zamanını pakete önceden bağlayacağız ve yalnızca uygulama yerel kitaplıkları tek dosya uygulamasıyla aynı dizine dağıtılır.</span><span class="sxs-lookup"><span data-stu-id="e5a2d-144">On Linux, we prelink the runtime into the bundle and only application native libraries are deployed to the same directory as the single-file app.</span></span> <span data-ttu-id="e5a2d-145">Windows 'da, yalnızca barındırma kodunu ön bağlantımız ve hem çalışma zamanı hem de uygulama yerel kitaplıkları tek dosya uygulamasıyla aynı dizine dağıtılır.</span><span class="sxs-lookup"><span data-stu-id="e5a2d-145">On Windows, we prelink only the hosting code and both the runtime and application native libraries are deployed to the same directory as the single-file app.</span></span> <span data-ttu-id="e5a2d-146">Bu, yerel dosyaların tek dosyadan dışlanması gereken iyi bir hata ayıklama deneyimi sağlamaktır.</span><span class="sxs-lookup"><span data-stu-id="e5a2d-146">This is to ensure a good debugging experience, which requires native files to be excluded from the single file.</span></span> <span data-ttu-id="e5a2d-147">`IncludeNativeLibrariesForSelfExtract`Tek dosya paketine yerel kitaplıkları dahil etmek için bir bayrak ayarlama seçeneği vardır, ancak tek dosya uygulaması çalıştırıldığında bu dosyalar istemci makinesindeki geçici bir dizine çıkarılır.</span><span class="sxs-lookup"><span data-stu-id="e5a2d-147">There is an option to set a flag, `IncludeNativeLibrariesForSelfExtract`, to include native libraries in the single file bundle, but these files will be extracted to a temporary directory in the client machine when the single file application is run.</span></span>

<span data-ttu-id="e5a2d-148">Tek dosya uygulama onunla ilgili tüm PDB dosyalarını ve varsayılan olarak paketlendirilecektir.</span><span class="sxs-lookup"><span data-stu-id="e5a2d-148">Single-file application will have all related PDB files alongside it and will not be bundled by default.</span></span> <span data-ttu-id="e5a2d-149">Oluşturduğunuz projeler için derlemenin içine pdb 'leri eklemek istiyorsanız, ' yi `DebugType` `embedded` [aşağıda](#include-pdb-files-inside-the-bundle) açıklandığı gibi olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="e5a2d-149">If you want to include PDBs inside the assembly for projects you build, set the `DebugType` to `embedded` as described [below](#include-pdb-files-inside-the-bundle) in detail.</span></span>

<span data-ttu-id="e5a2d-150">Yönetilen C++ bileşenleri tek dosya dağıtımına uygun değildir ve tek dosya uyumlu olması için C# veya yönetilmeyen bir C++ dilinde uygulama yazmanızı öneririz.</span><span class="sxs-lookup"><span data-stu-id="e5a2d-150">Managed C++ components aren't well suited for single-file deployment and we recommend that you write applications in C# or another non-managed C++ language to be single-file compatible.</span></span>

## <a name="exclude-files-from-being-embedded"></a><span data-ttu-id="e5a2d-151">Dosyaların gömülmesini hariç tut</span><span class="sxs-lookup"><span data-stu-id="e5a2d-151">Exclude files from being embedded</span></span>

<span data-ttu-id="e5a2d-152">Belirli dosyalar, aşağıdaki meta veriler ayarlanarak tek dosyaya katıştırılmayana açık bir şekilde dışlanamaz:</span><span class="sxs-lookup"><span data-stu-id="e5a2d-152">Certain files can be explicitly excluded from being embedded in the single-file by setting following metadata:</span></span>

```xml
<ExcludeFromSingleFile>true</ExcludeFromSingleFile>
```

<span data-ttu-id="e5a2d-153">Örneğin, yayınlama dizinine bazı dosyalar yerleştirmek, ancak onları tek dosyada paketlemenize izin vermek için:</span><span class="sxs-lookup"><span data-stu-id="e5a2d-153">For example, to place some files in the publish directory but not bundle them in the single-file:</span></span>

```xml
<ItemGroup>
  <Content Update="Plugin.dll">
    <CopyToPublishDirectory>PreserveNewest</CopyToPublishDirectory>
    <ExcludeFromSingleFile>true</ExcludeFromSingleFile>
  </Content>
</ItemGroup>
```

## <a name="include-pdb-files-inside-the-bundle"></a><span data-ttu-id="e5a2d-154">Paket içine PDB dosyalarını dahil et</span><span class="sxs-lookup"><span data-stu-id="e5a2d-154">Include PDB files inside the bundle</span></span>

<span data-ttu-id="e5a2d-155">Bir bütünleştirilmiş kod için PDB dosyası, aşağıdaki ayarı kullanılarak derlemeye gömülebilir ( `.dll` ).</span><span class="sxs-lookup"><span data-stu-id="e5a2d-155">The PDB file for an assembly can be embedded into the assembly itself (the `.dll`) using the setting below.</span></span> <span data-ttu-id="e5a2d-156">Semboller derlemenin bir parçası olduğundan, tek dosya uygulamasının bir parçası de olur:</span><span class="sxs-lookup"><span data-stu-id="e5a2d-156">Since the symbols are part of the assembly, they will be part of the single-file application as well:</span></span>

```xml
<DebugType>embedded</DebugType>
```

<span data-ttu-id="e5a2d-157">Örneğin, bu derlemeye PDB dosyasını katıştırmak için bir derlemenin proje dosyasına aşağıdaki özelliği ekleyin:</span><span class="sxs-lookup"><span data-stu-id="e5a2d-157">For example, add the following property to the project file of an assembly to embed the PDB file to that assembly:</span></span>

```xml
<PropertyGroup>
  <DebugType>embedded</DebugType>
</PropertyGroup>
```

## <a name="publish-a-single-file-app---cli"></a><span data-ttu-id="e5a2d-158">Tek bir dosya uygulaması yayımlama-CLı</span><span class="sxs-lookup"><span data-stu-id="e5a2d-158">Publish a single file app - CLI</span></span>

<span data-ttu-id="e5a2d-159">[DotNet Publish](../tools/dotnet-publish.md) komutunu kullanarak tek bir dosya uygulaması yayımlayın.</span><span class="sxs-lookup"><span data-stu-id="e5a2d-159">Publish a single file application using the [dotnet publish](../tools/dotnet-publish.md) command.</span></span> <span data-ttu-id="e5a2d-160">Uygulamanızı yayımladığınızda, aşağıdaki özellikleri ayarlayın:</span><span class="sxs-lookup"><span data-stu-id="e5a2d-160">When you publish your app, set the following properties:</span></span>

- <span data-ttu-id="e5a2d-161">Belirli bir çalışma zamanı için yayımlama: `-r win-x64`</span><span class="sxs-lookup"><span data-stu-id="e5a2d-161">Publish for a specific runtime: `-r win-x64`</span></span>
- <span data-ttu-id="e5a2d-162">Tek dosya olarak yayımla: `-p:PublishSingleFile=true`</span><span class="sxs-lookup"><span data-stu-id="e5a2d-162">Publish as a single-file: `-p:PublishSingleFile=true`</span></span>

<span data-ttu-id="e5a2d-163">Aşağıdaki örnek, Windows için bir uygulamayı kendi içinde tek bir dosya uygulaması olarak yayımlar.</span><span class="sxs-lookup"><span data-stu-id="e5a2d-163">The following example publishes an app for Windows as a self-contained single file application.</span></span>

```dotnetcli
dotnet publish -r win-x64 -p:PublishSingleFile=true --self-contained true
```

<span data-ttu-id="e5a2d-164">Aşağıdaki örnek, Framework 'e bağımlı tek dosya uygulaması olarak Linux için bir uygulama yayımlar.</span><span class="sxs-lookup"><span data-stu-id="e5a2d-164">The following example publishes an app for Linux as a framework dependent single file application.</span></span>

```dotnetcli
dotnet publish -r linux-x64 -p:PublishSingleFile=true --self-contained false
```

<span data-ttu-id="e5a2d-165">Daha fazla bilgi için bkz. [.NET Core uygulamalarını .NET Core CLI yayımlama](deploy-with-cli.md).</span><span class="sxs-lookup"><span data-stu-id="e5a2d-165">For more information, see [Publish .NET Core apps with .NET Core CLI](deploy-with-cli.md).</span></span>

## <a name="publish-a-single-file-app---visual-studio"></a><span data-ttu-id="e5a2d-166">Tek bir dosya uygulaması yayımlama-Visual Studio</span><span class="sxs-lookup"><span data-stu-id="e5a2d-166">Publish a single file app - Visual Studio</span></span>

<span data-ttu-id="e5a2d-167">Visual Studio, uygulamanızın nasıl yayımlandığını denetleyen yeniden kullanılabilir yayımlama profilleri oluşturur.</span><span class="sxs-lookup"><span data-stu-id="e5a2d-167">Visual Studio creates reusable publishing profiles that control how your application is published.</span></span>

01. <span data-ttu-id="e5a2d-168">**Çözüm Gezgini** bölmesinde, yayımlamak istediğiniz projeye sağ tıklayın.</span><span class="sxs-lookup"><span data-stu-id="e5a2d-168">On the **Solution Explorer** pane, right-click on the project you want to publish.</span></span> <span data-ttu-id="e5a2d-169">**Yayımla**’yı seçin.</span><span class="sxs-lookup"><span data-stu-id="e5a2d-169">Select **Publish**.</span></span>

    :::image type="content" source="media/single-file/visual-studio-solution-explorer.png" alt-text="Yayımla seçeneğini vurgulayan sağ tıklama menüsüyle Çözüm Gezgini.":::

    <span data-ttu-id="e5a2d-171">Zaten bir yayımlama profiliniz yoksa, bir tane oluşturmak için yönergeleri izleyin ve hedef türü **klasörünü** seçin.</span><span class="sxs-lookup"><span data-stu-id="e5a2d-171">If you don't already have a publishing profile, follow the instructions to create one and choose the **Folder** target-type.</span></span>

01. <span data-ttu-id="e5a2d-172">**Düzenle**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="e5a2d-172">Choose **Edit**.</span></span>

    :::image type="content" source="media/single-file/visual-studio-publish-edit-settings.png" alt-text="Yayımla seçeneğini vurgulayan sağ tıklama menüsüyle Çözüm Gezgini.":::

01. <span data-ttu-id="e5a2d-174">**Profil ayarları** iletişim kutusunda, aşağıdaki seçenekleri ayarlayın:</span><span class="sxs-lookup"><span data-stu-id="e5a2d-174">In the **Profile settings** dialog, set the following options:</span></span>

    - <span data-ttu-id="e5a2d-175">**Dağıtım modunu** **kendi kendine dahil**olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="e5a2d-175">Set **Deployment mode** to **Self-contained**.</span></span>
    - <span data-ttu-id="e5a2d-176">**Hedef çalışma zamanını** , yayımlamak istediğiniz platforma ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="e5a2d-176">Set **Target runtime** to the platform you want to publish to.</span></span>
    - <span data-ttu-id="e5a2d-177">**Tek bir dosya üret**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="e5a2d-177">Select **Produce single file**.</span></span>

    <span data-ttu-id="e5a2d-178">Ayarları kaydetmek ve **Yayımla** iletişim kutusuna dönmek için **Kaydet** ' i seçin.</span><span class="sxs-lookup"><span data-stu-id="e5a2d-178">Choose **Save** to save the settings and return to the **Publish** dialog.</span></span>

    :::image type="content" source="media/single-file/visual-studio-publish-single-file-properties.png" alt-text="Yayımla seçeneğini vurgulayan sağ tıklama menüsüyle Çözüm Gezgini.":::

01. <span data-ttu-id="e5a2d-180">Uygulamanızı tek bir dosya olarak yayımlamak için **Yayımla** ' yı seçin.</span><span class="sxs-lookup"><span data-stu-id="e5a2d-180">Choose **Publish** to publish your app as a single file.</span></span>

<span data-ttu-id="e5a2d-181">Daha fazla bilgi için bkz. [Visual Studio ile .NET Core uygulamalarını yayımlama](deploy-with-vs.md).</span><span class="sxs-lookup"><span data-stu-id="e5a2d-181">For more information, see [Publish .NET Core apps with Visual Studio](deploy-with-vs.md).</span></span>

## <a name="publish-a-single-file-app---visual-studio-for-mac"></a><span data-ttu-id="e5a2d-182">Tek bir dosya uygulaması yayımlama-Mac için Visual Studio</span><span class="sxs-lookup"><span data-stu-id="e5a2d-182">Publish a single file app - Visual Studio for Mac</span></span>

<span data-ttu-id="e5a2d-183">Mac için Visual Studio uygulamanızı tek bir dosya olarak yayımlamak için seçenek sağlamıyor.</span><span class="sxs-lookup"><span data-stu-id="e5a2d-183">Visual Studio for Mac doesn't provide options to publish your app as a single file.</span></span> <span data-ttu-id="e5a2d-184">[Tek dosya App-CLI Yayımla](#publish-a-single-file-app---cli) bölümündeki yönergeleri izleyerek el ile yayımlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="e5a2d-184">You'll need to publish manually by following the instructions from the [Publish a single file app - CLI](#publish-a-single-file-app---cli) section.</span></span> <span data-ttu-id="e5a2d-185">Daha fazla bilgi için bkz. [.NET Core uygulamalarını .NET Core CLI yayımlama](deploy-with-cli.md).</span><span class="sxs-lookup"><span data-stu-id="e5a2d-185">For more information, see [Publish .NET Core apps with .NET Core CLI](deploy-with-cli.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="e5a2d-186">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e5a2d-186">See also</span></span>

- <span data-ttu-id="e5a2d-187">[.NET Core uygulama dağıtımı](index.md).</span><span class="sxs-lookup"><span data-stu-id="e5a2d-187">[.NET Core application deployment](index.md).</span></span>
- <span data-ttu-id="e5a2d-188">[.NET Core uygulamalarını .NET Core CLI yayımlayın](deploy-with-cli.md).</span><span class="sxs-lookup"><span data-stu-id="e5a2d-188">[Publish .NET Core apps with .NET Core CLI](deploy-with-cli.md).</span></span>
- <span data-ttu-id="e5a2d-189">[Visual Studio ile .NET Core uygulamaları yayımlayın](deploy-with-vs.md).</span><span class="sxs-lookup"><span data-stu-id="e5a2d-189">[Publish .NET Core apps with Visual Studio](deploy-with-vs.md).</span></span>
- <span data-ttu-id="e5a2d-190">[ `dotnet publish` komutu](../tools/dotnet-publish.md).</span><span class="sxs-lookup"><span data-stu-id="e5a2d-190">[`dotnet publish` command](../tools/dotnet-publish.md).</span></span>
