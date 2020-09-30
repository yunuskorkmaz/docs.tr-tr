---
title: Tek dosya uygulaması
description: Tek bir dosya uygulamasının ne olduğunu ve neden bu uygulama dağıtım modelini kullanmayı düşünmeniz gerektiğini öğrenin.
author: lakshanf
ms.author: lakshanf
ms.date: 08/28/2020
ms.openlocfilehash: 8149f912c2d92c3eff8d248353e11c01bcfc24ba
ms.sourcegitcommit: 665f8fc55258356f4d2f4a6585b750c974b26675
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/30/2020
ms.locfileid: "91573676"
---
# <a name="single-file-deployment-and-executable"></a><span data-ttu-id="1ea74-103">Tek dosya dağıtımı ve yürütülebilir dosya</span><span class="sxs-lookup"><span data-stu-id="1ea74-103">Single file deployment and executable</span></span>

<span data-ttu-id="1ea74-104">Uygulamaya bağımlı tüm dosyaları tek bir ikiliye paketlemek, uygulamayı tek bir dosya olarak dağıtmak ve dağıtmak için çekici bir seçeneğe sahip bir uygulama geliştiricisi sağlar.</span><span class="sxs-lookup"><span data-stu-id="1ea74-104">Bundling all application-dependent files into a single binary provides an application developer with the attractive option to deploy and distribute the application as a single file.</span></span> <span data-ttu-id="1ea74-105">Bu dağıtım modeli .NET Core 3,0 ' den beri kullanılabilir ve .NET 5,0 ' de geliştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="1ea74-105">This deployment model has been available since .NET Core 3.0 and has been enhanced in .NET 5.0.</span></span> <span data-ttu-id="1ea74-106">Daha önce .NET Core 3,0 ' de, bir kullanıcı tek dosya uygulamanızı çalıştırdığında, .NET Core ana bilgisayarı önce uygulamayı çalıştırmadan önce tüm dosyaları geçici bir dizine ayıklar.</span><span class="sxs-lookup"><span data-stu-id="1ea74-106">Previously in .NET Core 3.0, when a user runs your single-file app, .NET Core host first extracts all files to a temporary directory before running the application.</span></span> <span data-ttu-id="1ea74-107">.NET 5,0, dosyaları uygulamadan çıkarmaya gerek olmadan doğrudan kodu çalıştırarak bu deneyimi geliştirir.</span><span class="sxs-lookup"><span data-stu-id="1ea74-107">.NET 5.0 improves this experience by directly running the code without the need to extract the files from the app.</span></span>

<span data-ttu-id="1ea74-108">Tek dosya dağıtımı, hem [çerçeveye bağımlı dağıtım modeli](index.md#publish-framework-dependent) hem de [kendi içinde bulunan uygulamalar](index.md#publish-self-contained)için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="1ea74-108">Single File deployment is available for both the [framework-dependent deployment model](index.md#publish-framework-dependent) and [self-contained applications](index.md#publish-self-contained).</span></span> <span data-ttu-id="1ea74-109">Bağımsız bir uygulamadaki tek dosyanın boyutu, çalışma zamanı ve çerçeve kitaplıklarını dahil edecek şekilde büyük olacaktır.</span><span class="sxs-lookup"><span data-stu-id="1ea74-109">The size of the single file in a self-contained application will be large since it will include the runtime and the framework libraries.</span></span> <span data-ttu-id="1ea74-110">Tek dosya dağıtım seçeneği, [Readytorun](../tools/dotnet-publish.md) ve [Trim (.NET 5,0 ' de deneysel bir özellik)](trim-self-contained.md) yayımlama seçenekleri ile birleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="1ea74-110">The single file deployment option can be combined with [ReadyToRun](../tools/dotnet-publish.md) and [Trim (an experimental feature in .NET 5.0)](trim-self-contained.md) publish options.</span></span>

## <a name="api-incompatibility"></a><span data-ttu-id="1ea74-111">API uyumsuzluğu</span><span class="sxs-lookup"><span data-stu-id="1ea74-111">API incompatibility</span></span>

<span data-ttu-id="1ea74-112">Bazı API 'Ler tek dosya dağıtımıyla uyumlu değildir ve uygulamalar bu API 'Leri kullanıyorsa değişiklik yapılmasını gerektirebilir.</span><span class="sxs-lookup"><span data-stu-id="1ea74-112">Some APIs are not compatible with single-file deployment and applications may require modification if they use these APIs.</span></span> <span data-ttu-id="1ea74-113">Üçüncü taraf bir Framework veya paket kullanıyorsanız, bu API 'lerden birini de kullanabilir ve değişiklik yapmanız gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="1ea74-113">If you use a third-party framework or package, it's possible that they may also use one of these APIs and need modification.</span></span> <span data-ttu-id="1ea74-114">Sorunların en yaygın nedeni, uygulamayla birlikte gelen dosyalar veya dll 'Ler için dosya yollarında bağımlılığını temel alır.</span><span class="sxs-lookup"><span data-stu-id="1ea74-114">The most common cause of problems is dependence on file paths for files or DLLs shipped with the application.</span></span>

<span data-ttu-id="1ea74-115">Aşağıdaki tabloda, tek dosya kullanımı için ilgili çalışma zamanı kitaplığı API 'SI ayrıntıları bulunur.</span><span class="sxs-lookup"><span data-stu-id="1ea74-115">The table below has the relevant runtime library API details for single-file use.</span></span>

| <span data-ttu-id="1ea74-116">API</span><span class="sxs-lookup"><span data-stu-id="1ea74-116">API</span></span>                            | <span data-ttu-id="1ea74-117">Not</span><span class="sxs-lookup"><span data-stu-id="1ea74-117">Note</span></span>                                                                   |
|--------------------------------|------------------------------------------------------------------------|
| `Assembly.Location`            | <span data-ttu-id="1ea74-118">Boş bir dize döndürür.</span><span class="sxs-lookup"><span data-stu-id="1ea74-118">Returns an empty string.</span></span>                                               |
| `Module.FullyQualifiedName`    | <span data-ttu-id="1ea74-119">Değerine sahip bir dize döndürür `<Unknown>` veya bir özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="1ea74-119">Returns a string with the value of `<Unknown>` or throws an exception.</span></span> |
| `Module.Name`                  | <span data-ttu-id="1ea74-120">Değerine sahip bir dize döndürür `<Unknown>` .</span><span class="sxs-lookup"><span data-stu-id="1ea74-120">Returns a string with the value of `<Unknown>`.</span></span>                        |
| `Assembly.GetFile`             | <span data-ttu-id="1ea74-121">Atar <xref:System.IO.IOException> .</span><span class="sxs-lookup"><span data-stu-id="1ea74-121">Throws <xref:System.IO.IOException>.</span></span>                                   |
| `Assembly.GetFiles`            | <span data-ttu-id="1ea74-122">Atar <xref:System.IO.IOException> .</span><span class="sxs-lookup"><span data-stu-id="1ea74-122">Throws <xref:System.IO.IOException>.</span></span>                                   |
| `Assembly.CodeBase`            | <span data-ttu-id="1ea74-123">Atar <xref:System.PlatformNotSupportedException> .</span><span class="sxs-lookup"><span data-stu-id="1ea74-123">Throws <xref:System.PlatformNotSupportedException>.</span></span>                    |
| `Assembly.EscapedCodeBase`     | <span data-ttu-id="1ea74-124">Atar <xref:System.PlatformNotSupportedException> .</span><span class="sxs-lookup"><span data-stu-id="1ea74-124">Throws <xref:System.PlatformNotSupportedException>.</span></span>                    |
| `AssemblyName.CodeBase`        | <span data-ttu-id="1ea74-125">`null` döndürür.</span><span class="sxs-lookup"><span data-stu-id="1ea74-125">Returns `null`.</span></span>                                                        |
| `AssemblyName.EscapedCodeBase` | <span data-ttu-id="1ea74-126">`null` döndürür.</span><span class="sxs-lookup"><span data-stu-id="1ea74-126">Returns `null`.</span></span>                                                        |

<span data-ttu-id="1ea74-127">Yaygın senaryoları düzeltmeye yönelik bazı önerileriniz var:</span><span class="sxs-lookup"><span data-stu-id="1ea74-127">We have some recommendations for fixing common scenarios:</span></span>

* <span data-ttu-id="1ea74-128">Yürütülebilir dosyanın yanındaki dosyalara erişmek için şunu kullanın <xref:System.AppContext.BaseDirectory?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="1ea74-128">To access files next to the executable, use <xref:System.AppContext.BaseDirectory?displayProperty=nameWithType></span></span>

* <span data-ttu-id="1ea74-129">Yürütülebilir dosyanın dosya adını bulmak için ilk öğesini kullanın <xref:System.Environment.GetCommandLineArgs()?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="1ea74-129">To find the file name of the executable, use the first element of <xref:System.Environment.GetCommandLineArgs()?displayProperty=nameWithType></span></span>

* <span data-ttu-id="1ea74-130">Gevşek dosyaları tamamen sevk etmeyi önlemek için, [ekli kaynakları](https://docs.microsoft.com/en-us/dotnet/framework/resources/creating-resource-files-for-desktop-apps) kullanmayı düşünün</span><span class="sxs-lookup"><span data-stu-id="1ea74-130">To avoid shipping loose files entirely, consider using [embedded resources](https://docs.microsoft.com/en-us/dotnet/framework/resources/creating-resource-files-for-desktop-apps)</span></span>

## <a name="other-considerations"></a><span data-ttu-id="1ea74-131">Diğer önemli noktalar</span><span class="sxs-lookup"><span data-stu-id="1ea74-131">Other considerations</span></span>

<span data-ttu-id="1ea74-132">Tek dosya varsayılan olarak yerel kitaplıkları paketetmez.</span><span class="sxs-lookup"><span data-stu-id="1ea74-132">Single-file doesn't bundle native libraries by default.</span></span> <span data-ttu-id="1ea74-133">Linux 'ta çalışma zamanını pakete önceden bağlayacağız ve yalnızca uygulama yerel kitaplıkları tek dosya uygulamasıyla aynı dizine dağıtılır.</span><span class="sxs-lookup"><span data-stu-id="1ea74-133">On Linux, we prelink the runtime into the bundle and only application native libraries are deployed to the same directory as the single-file app.</span></span> <span data-ttu-id="1ea74-134">Windows 'da, yalnızca barındırma kodunu ön bağlantımız ve hem çalışma zamanı hem de uygulama yerel kitaplıkları tek dosya uygulamasıyla aynı dizine dağıtılır.</span><span class="sxs-lookup"><span data-stu-id="1ea74-134">On Windows, we prelink only the hosting code and both the runtime and application native libraries are deployed to the same directory as the single-file app.</span></span> <span data-ttu-id="1ea74-135">Bu, yerel dosyaların tek dosyadan dışlanması gereken iyi bir hata ayıklama deneyimi sağlamaktır.</span><span class="sxs-lookup"><span data-stu-id="1ea74-135">This is to ensure a good debugging experience, which requires native files to be excluded from the single file.</span></span> <span data-ttu-id="1ea74-136">`IncludeNativeLibrariesForSelfExtract`Tek dosya paketine yerel kitaplıkları dahil etmek için bir bayrak ayarlama seçeneği vardır, ancak tek dosya uygulaması çalıştırıldığında bu dosyalar istemci makinesindeki geçici bir dizine çıkarılır.</span><span class="sxs-lookup"><span data-stu-id="1ea74-136">There is an option to set a flag, `IncludeNativeLibrariesForSelfExtract`, to include native libraries in the single file bundle, but these files will be extracted to a temporary directory in the client machine when the single file application is run.</span></span>

<span data-ttu-id="1ea74-137">Tek dosya uygulama onunla ilgili tüm PDB dosyalarını ve varsayılan olarak paketlendirilecektir.</span><span class="sxs-lookup"><span data-stu-id="1ea74-137">Single-file application will have all related PDB files alongside it and will not be bundled by default.</span></span> <span data-ttu-id="1ea74-138">Oluşturduğunuz projeler için derlemenin içine pdb 'leri eklemek istiyorsanız, ' yi `DebugType` `embedded` [aşağıda](#include-pdb-files-inside-the-bundle) açıklandığı gibi olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="1ea74-138">If you want to include PDBs inside the assembly for projects you build, set the `DebugType` to `embedded` as described [below](#include-pdb-files-inside-the-bundle) in detail.</span></span>

<span data-ttu-id="1ea74-139">Yönetilen C++ bileşenleri tek dosya dağıtımına uygun değildir ve tek dosya uyumlu olması için C# veya yönetilmeyen bir C++ dilinde uygulama yazmanızı öneririz.</span><span class="sxs-lookup"><span data-stu-id="1ea74-139">Managed C++ components aren't well suited for single-file deployment and we recommend that you write applications in C# or another non-managed C++ language to be single-file compatible.</span></span>

## <a name="exclude-files-from-being-embedded"></a><span data-ttu-id="1ea74-140">Dosyaların gömülmesini hariç tut</span><span class="sxs-lookup"><span data-stu-id="1ea74-140">Exclude files from being embedded</span></span>

<span data-ttu-id="1ea74-141">Belirli dosyalar, aşağıdaki meta veriler ayarlanarak tek dosyaya katıştırılmayana açık bir şekilde dışlanamaz:</span><span class="sxs-lookup"><span data-stu-id="1ea74-141">Certain files can be explicitly excluded from being embedded in the single-file by setting following metadata:</span></span>

```xml
<ExcludeFromSingleFile>true</ExcludeFromSingleFile>
```

<span data-ttu-id="1ea74-142">Örneğin, yayınlama dizinine bazı dosyalar yerleştirmek, ancak onları tek dosyada paketlemenize izin vermek için:</span><span class="sxs-lookup"><span data-stu-id="1ea74-142">For example, to place some files in the publish directory but not bundle them in the single-file:</span></span>

```xml
<ItemGroup>
  <Content Update="Plugin.dll">
    <CopyToPublishDirectory>PreserveNewest</CopyToPublishDirectory>
    <ExcludeFromSingleFile>true</ExcludeFromSingleFile>
  </Content>
</ItemGroup>
```

## <a name="include-pdb-files-inside-the-bundle"></a><span data-ttu-id="1ea74-143">Paket içine PDB dosyalarını dahil et</span><span class="sxs-lookup"><span data-stu-id="1ea74-143">Include PDB files inside the bundle</span></span>

<span data-ttu-id="1ea74-144">Bir bütünleştirilmiş kod için PDB dosyası, aşağıdaki ayarı kullanılarak derlemeye gömülebilir ( `.dll` ).</span><span class="sxs-lookup"><span data-stu-id="1ea74-144">The PDB file for an assembly can be embedded into the assembly itself (the `.dll`) using the setting below.</span></span> <span data-ttu-id="1ea74-145">Semboller derlemenin bir parçası olduğundan, tek dosya uygulamasının bir parçası de olur:</span><span class="sxs-lookup"><span data-stu-id="1ea74-145">Since the symbols are part of the assembly, they will be part of the single-file application as well:</span></span>

```xml
<DebugType>embedded</DebugType>
```

<span data-ttu-id="1ea74-146">Örneğin, bu derlemeye PDB dosyasını katıştırmak için bir derlemenin proje dosyasına aşağıdaki özelliği ekleyin:</span><span class="sxs-lookup"><span data-stu-id="1ea74-146">For example, add the following property to the project file of an assembly to embed the PDB file to that assembly:</span></span>

```xml
<PropertyGroup>
  <DebugType>embedded</DebugType>
</PropertyGroup>
```

## <a name="publish-a-single-file-app---cli"></a><span data-ttu-id="1ea74-147">Tek bir dosya uygulaması yayımlama-CLı</span><span class="sxs-lookup"><span data-stu-id="1ea74-147">Publish a single file app - CLI</span></span>

<span data-ttu-id="1ea74-148">[DotNet Publish](../tools/dotnet-publish.md) komutunu kullanarak tek bir dosya uygulaması yayımlayın.</span><span class="sxs-lookup"><span data-stu-id="1ea74-148">Publish a single file application using the [dotnet publish](../tools/dotnet-publish.md) command.</span></span> <span data-ttu-id="1ea74-149">Uygulamanızı yayımladığınızda, aşağıdaki özellikleri ayarlayın:</span><span class="sxs-lookup"><span data-stu-id="1ea74-149">When you publish your app, set the following properties:</span></span>

- <span data-ttu-id="1ea74-150">Belirli bir çalışma zamanı için yayımlama: `-r win-x64`</span><span class="sxs-lookup"><span data-stu-id="1ea74-150">Publish for a specific runtime: `-r win-x64`</span></span>
- <span data-ttu-id="1ea74-151">Tek dosya olarak yayımla: `-p:PublishSingleFile=true`</span><span class="sxs-lookup"><span data-stu-id="1ea74-151">Publish as a single-file: `-p:PublishSingleFile=true`</span></span>

<span data-ttu-id="1ea74-152">Aşağıdaki örnek, Windows için bir uygulamayı kendi içinde tek bir dosya uygulaması olarak yayımlar.</span><span class="sxs-lookup"><span data-stu-id="1ea74-152">The following example publishes an app for Windows as a self-contained single file application.</span></span>

```dotnetcli
dotnet publish -r win-x64 -p:PublishSingleFile=true --self-contained true
```

<span data-ttu-id="1ea74-153">Aşağıdaki örnek, Framework 'e bağımlı tek dosya uygulaması olarak Linux için bir uygulama yayımlar.</span><span class="sxs-lookup"><span data-stu-id="1ea74-153">The following example publishes an app for Linux as a framework dependent single file application.</span></span>

```dotnetcli
dotnet publish -r linux-x64 -p:PublishSingleFile=true --self-contained false
```

<span data-ttu-id="1ea74-154">Daha fazla bilgi için bkz. [.NET Core uygulamalarını .NET Core CLI yayımlama](deploy-with-cli.md).</span><span class="sxs-lookup"><span data-stu-id="1ea74-154">For more information, see [Publish .NET Core apps with .NET Core CLI](deploy-with-cli.md).</span></span>

## <a name="publish-a-single-file-app---visual-studio"></a><span data-ttu-id="1ea74-155">Tek bir dosya uygulaması yayımlama-Visual Studio</span><span class="sxs-lookup"><span data-stu-id="1ea74-155">Publish a single file app - Visual Studio</span></span>

<span data-ttu-id="1ea74-156">Visual Studio, uygulamanızın nasıl yayımlandığını denetleyen yeniden kullanılabilir yayımlama profilleri oluşturur.</span><span class="sxs-lookup"><span data-stu-id="1ea74-156">Visual Studio creates reusable publishing profiles that control how your application is published.</span></span>

01. <span data-ttu-id="1ea74-157">**Çözüm Gezgini** bölmesinde, yayımlamak istediğiniz projeye sağ tıklayın.</span><span class="sxs-lookup"><span data-stu-id="1ea74-157">On the **Solution Explorer** pane, right-click on the project you want to publish.</span></span> <span data-ttu-id="1ea74-158">**Yayımla**’yı seçin.</span><span class="sxs-lookup"><span data-stu-id="1ea74-158">Select **Publish**.</span></span>

    :::image type="content" source="media/single-file/visual-studio-solution-explorer.png" alt-text="Yayımla seçeneğini vurgulayan sağ tıklama menüsüyle Çözüm Gezgini.":::

    <span data-ttu-id="1ea74-160">Zaten bir yayımlama profiliniz yoksa, bir tane oluşturmak için yönergeleri izleyin ve hedef türü **klasörünü** seçin.</span><span class="sxs-lookup"><span data-stu-id="1ea74-160">If you don't already have a publishing profile, follow the instructions to create one and choose the **Folder** target-type.</span></span>

01. <span data-ttu-id="1ea74-161">**Düzenle**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="1ea74-161">Choose **Edit**.</span></span>

    :::image type="content" source="media/single-file/visual-studio-publish-edit-settings.png" alt-text="Yayımla seçeneğini vurgulayan sağ tıklama menüsüyle Çözüm Gezgini.":::

01. <span data-ttu-id="1ea74-163">**Profil ayarları** iletişim kutusunda, aşağıdaki seçenekleri ayarlayın:</span><span class="sxs-lookup"><span data-stu-id="1ea74-163">In the **Profile settings** dialog, set the following options:</span></span>

    - <span data-ttu-id="1ea74-164">**Dağıtım modunu** **kendi kendine dahil**olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="1ea74-164">Set **Deployment mode** to **Self-contained**.</span></span>
    - <span data-ttu-id="1ea74-165">**Hedef çalışma zamanını** , yayımlamak istediğiniz platforma ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="1ea74-165">Set **Target runtime** to the platform you want to publish to.</span></span>
    - <span data-ttu-id="1ea74-166">**Tek bir dosya üret**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="1ea74-166">Select **Produce single file**.</span></span>

    <span data-ttu-id="1ea74-167">Ayarları kaydetmek ve **Yayımla** iletişim kutusuna dönmek için **Kaydet** ' i seçin.</span><span class="sxs-lookup"><span data-stu-id="1ea74-167">Choose **Save** to save the settings and return to the **Publish** dialog.</span></span>

    :::image type="content" source="media/single-file/visual-studio-publish-single-file-properties.png" alt-text="Yayımla seçeneğini vurgulayan sağ tıklama menüsüyle Çözüm Gezgini.":::

01. <span data-ttu-id="1ea74-169">Uygulamanızı tek bir dosya olarak yayımlamak için **Yayımla** ' yı seçin.</span><span class="sxs-lookup"><span data-stu-id="1ea74-169">Choose **Publish** to publish your app as a single file.</span></span>

<span data-ttu-id="1ea74-170">Daha fazla bilgi için bkz. [Visual Studio ile .NET Core uygulamalarını yayımlama](deploy-with-vs.md).</span><span class="sxs-lookup"><span data-stu-id="1ea74-170">For more information, see [Publish .NET Core apps with Visual Studio](deploy-with-vs.md).</span></span>

## <a name="publish-a-single-file-app---visual-studio-for-mac"></a><span data-ttu-id="1ea74-171">Tek bir dosya uygulaması yayımlama-Mac için Visual Studio</span><span class="sxs-lookup"><span data-stu-id="1ea74-171">Publish a single file app - Visual Studio for Mac</span></span>

<span data-ttu-id="1ea74-172">Mac için Visual Studio uygulamanızı tek bir dosya olarak yayımlamak için seçenek sağlamıyor.</span><span class="sxs-lookup"><span data-stu-id="1ea74-172">Visual Studio for Mac doesn't provide options to publish your app as a single file.</span></span> <span data-ttu-id="1ea74-173">[Tek dosya App-CLI Yayımla](#publish-a-single-file-app---cli) bölümündeki yönergeleri izleyerek el ile yayımlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="1ea74-173">You'll need to publish manually by following the instructions from the [Publish a single file app - CLI](#publish-a-single-file-app---cli) section.</span></span> <span data-ttu-id="1ea74-174">Daha fazla bilgi için bkz. [.NET Core uygulamalarını .NET Core CLI yayımlama](deploy-with-cli.md).</span><span class="sxs-lookup"><span data-stu-id="1ea74-174">For more information, see [Publish .NET Core apps with .NET Core CLI](deploy-with-cli.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="1ea74-175">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1ea74-175">See also</span></span>

- <span data-ttu-id="1ea74-176">[.NET Core uygulama dağıtımı](index.md).</span><span class="sxs-lookup"><span data-stu-id="1ea74-176">[.NET Core application deployment](index.md).</span></span>
- <span data-ttu-id="1ea74-177">[.NET Core uygulamalarını .NET Core CLI yayımlayın](deploy-with-cli.md).</span><span class="sxs-lookup"><span data-stu-id="1ea74-177">[Publish .NET Core apps with .NET Core CLI](deploy-with-cli.md).</span></span>
- <span data-ttu-id="1ea74-178">[Visual Studio ile .NET Core uygulamaları yayımlayın](deploy-with-vs.md).</span><span class="sxs-lookup"><span data-stu-id="1ea74-178">[Publish .NET Core apps with Visual Studio](deploy-with-vs.md).</span></span>
- <span data-ttu-id="1ea74-179">[ `dotnet publish` komutu](../tools/dotnet-publish.md).</span><span class="sxs-lookup"><span data-stu-id="1ea74-179">[`dotnet publish` command](../tools/dotnet-publish.md).</span></span>
