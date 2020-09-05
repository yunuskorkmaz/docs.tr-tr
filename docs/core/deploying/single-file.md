---
title: Tek dosya uygulaması
description: Tek bir dosya uygulamasının ne olduğunu ve neden bu uygulama dağıtım modelini kullanmayı düşünmeniz gerektiğini öğrenin.
author: lakshanf
ms.author: lakshanf
ms.date: 08/28/2020
ms.openlocfilehash: 795ea98a9fd9d672b199eb2d9b24151340ef8246
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89495814"
---
# <a name="single-file-deployment-and-executable"></a><span data-ttu-id="ed50a-103">Tek dosya dağıtımı ve yürütülebilir</span><span class="sxs-lookup"><span data-stu-id="ed50a-103">Single file deployment and executable</span></span>

<span data-ttu-id="ed50a-104">Uygulamaya bağımlı tüm dosyaları tek bir ikiliye paketlemek, uygulamayı tek bir dosya olarak dağıtmak ve dağıtmak için çekici bir seçeneğe sahip bir uygulama geliştiricisi sağlar.</span><span class="sxs-lookup"><span data-stu-id="ed50a-104">Bundling all application-dependent files into a single binary provides an application developer with the attractive option to deploy and distribute the application as a single file.</span></span> <span data-ttu-id="ed50a-105">Bu dağıtım modeli .NET Core 3,0 ' den beri kullanılabilir ve .NET 5,0 ' de geliştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="ed50a-105">This deployment model has been available since .NET Core 3.0 and has been enhanced in .NET 5.0.</span></span> <span data-ttu-id="ed50a-106">Daha önce .NET Core 3,0 ' de, bir kullanıcı tek dosya uygulamanızı çalıştırdığında, .NET Core ana bilgisayarı önce uygulamayı çalıştırmadan önce tüm dosyaları geçici bir dizine ayıklar.</span><span class="sxs-lookup"><span data-stu-id="ed50a-106">Previously in .NET Core 3.0, when a user runs your single-file app, .NET Core host first extracts all files to a temporary directory before running the application.</span></span> <span data-ttu-id="ed50a-107">.NET 5,0, dosyaları uygulamadan çıkarmaya gerek olmadan doğrudan kodu çalıştırarak bu deneyimi geliştirir.</span><span class="sxs-lookup"><span data-stu-id="ed50a-107">.NET 5.0 improves this experience by directly running the code without the need to extract the files from the app.</span></span>

<span data-ttu-id="ed50a-108">Tek dosya dağıtımı, hem [çerçeveye bağımlı dağıtım modeli](index.md#publish-framework-dependent) hem de [kendi içinde bulunan uygulamalar](index.md#publish-self-contained)için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="ed50a-108">Single File deployment is available for both the [framework-dependent deployment model](index.md#publish-framework-dependent) and [self-contained applications](index.md#publish-self-contained).</span></span> <span data-ttu-id="ed50a-109">Bağımsız bir uygulamadaki tek dosyanın boyutu, çalışma zamanı ve çerçeve kitaplıklarını dahil edecek şekilde büyük olacaktır.</span><span class="sxs-lookup"><span data-stu-id="ed50a-109">The size of the single file in a self-contained application will be large since it will include the runtime and the framework libraries.</span></span> <span data-ttu-id="ed50a-110">Tek dosya dağıtım seçeneği, [Readytorun](../tools/dotnet-publish.md) ve [Trim (.NET 5,0 ' de deneysel bir özellik)](trim-self-contained.md) yayımlama seçenekleri ile birleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="ed50a-110">The single file deployment option can be combined with [ReadyToRun](../tools/dotnet-publish.md) and [Trim (an experimental feature in .NET 5.0)](trim-self-contained.md) publish options.</span></span>

<span data-ttu-id="ed50a-111">Tek dosya kullanımı için bilmeniz gereken bazı uyarılar vardır. Bu, ilk olarak, uygulamanın konumuyla ilgili bir dosyayı bulmak için yol bilgilerinin kullanılması olan bazı uyarılar vardır.</span><span class="sxs-lookup"><span data-stu-id="ed50a-111">There are some caveats that you need to be aware for single-file use, first of which is the use of path information to locate a file relative to the location of your application.</span></span> <span data-ttu-id="ed50a-112"><xref:System.Reflection.Assembly.Location?displayProperty=nameWithType>API, bellekten yüklenen derlemeler için varsayılan davranış olan boş bir dize döndürür.</span><span class="sxs-lookup"><span data-stu-id="ed50a-112">The <xref:System.Reflection.Assembly.Location?displayProperty=nameWithType> API will return an empty string, which is the default behavior for assemblies loaded from memory.</span></span> <span data-ttu-id="ed50a-113">Derleyici, derlemeyi belirli davranışa uyarmak için derleme zamanında bu API 'ye bir uyarı verir.</span><span class="sxs-lookup"><span data-stu-id="ed50a-113">The compiler will give a warning for this API during build time to alert the developer to the specific behavior.</span></span> <span data-ttu-id="ed50a-114">Uygulama dizini yolu gerekliyse, <xref:System.AppContext.BaseDirectory?displayProperty=nameWithType> API, apphost 'nın (tek dosya paketinin kendisi) bulunduğu dizini döndürür.</span><span class="sxs-lookup"><span data-stu-id="ed50a-114">If the path to the application directory is needed, the <xref:System.AppContext.BaseDirectory?displayProperty=nameWithType> API will return the directory where the AppHost (the single-file bundle itself) resides.</span></span> <span data-ttu-id="ed50a-115">Yönetilen C++ uygulamaları tek dosya dağıtımına uygun değildir ve C# ' deki uygulamaları tek dosya uyumlu olacak şekilde yazmanızı öneririz.</span><span class="sxs-lookup"><span data-stu-id="ed50a-115">Managed C++ applications aren't well suited for single-file deployment and we recommend that you write applications in C# to be single-file compatible.</span></span>

<span data-ttu-id="ed50a-116">Tek dosya varsayılan olarak yerel kitaplıkları paketetmez.</span><span class="sxs-lookup"><span data-stu-id="ed50a-116">Single-file doesn't bundle native libraries by default.</span></span> <span data-ttu-id="ed50a-117">Linux 'ta çalışma zamanını pakete önceden bağlayacağız ve yalnızca uygulama yerel kitaplıkları tek dosya uygulamasıyla aynı dizine dağıtılır.</span><span class="sxs-lookup"><span data-stu-id="ed50a-117">On Linux, we prelink the runtime into the bundle and only application native libraries are deployed to the same directory as the single-file app.</span></span> <span data-ttu-id="ed50a-118">Windows 'da, yalnızca barındırma kodunu ön bağlantımız ve hem çalışma zamanı hem de uygulama yerel kitaplıkları tek dosya uygulamasıyla aynı dizine dağıtılır.</span><span class="sxs-lookup"><span data-stu-id="ed50a-118">On Windows, we prelink only the hosting code and both the runtime and application native libraries are deployed to the same directory as the single-file app.</span></span> <span data-ttu-id="ed50a-119">Bu, yerel dosyaların tek dosyadan dışlanması gereken iyi bir hata ayıklama deneyimi sağlamaktır.</span><span class="sxs-lookup"><span data-stu-id="ed50a-119">This is to ensure a good debugging experience, which requires native files to be excluded from the single file.</span></span> <span data-ttu-id="ed50a-120">`IncludeNativeLibrariesForSelfExtract`Tek dosya paketine yerel kitaplıkları dahil etmek için bir bayrak ayarlama seçeneği vardır, ancak tek dosya uygulaması çalıştırıldığında bu dosyalar istemci makinesindeki geçici bir dizine çıkarılır.</span><span class="sxs-lookup"><span data-stu-id="ed50a-120">There is an option to set a flag, `IncludeNativeLibrariesForSelfExtract`, to include native libraries in the single file bundle, but these files will be extracted to a temporary directory in the client machine when the single file application is run.</span></span>

## <a name="exclude-files-from-being-embedded"></a><span data-ttu-id="ed50a-121">Dosyaların gömülmesini hariç tut</span><span class="sxs-lookup"><span data-stu-id="ed50a-121">Exclude files from being embedded</span></span>

<span data-ttu-id="ed50a-122">Belirli dosyalar, aşağıdaki meta veriler ayarlanarak tek dosyaya katıştırılmayana açık bir şekilde dışlanamaz:</span><span class="sxs-lookup"><span data-stu-id="ed50a-122">Certain files can be explicitly excluded from being embedded in the single-file by setting following metadata:</span></span>

```xml
<ExcludeFromSingleFile>true</ExcludeFromSingleFile>
```

<span data-ttu-id="ed50a-123">Örneğin, yayınlama dizinine bazı dosyalar yerleştirmek, ancak onları tek dosyada paketlemenize izin vermek için:</span><span class="sxs-lookup"><span data-stu-id="ed50a-123">For example, to place some files in the publish directory but not bundle them in the single-file:</span></span>

```xml
<ItemGroup>
  <Content Update="Plugin.dll">
    <CopyToPublishDirectory>PreserveNewest</CopyToPublishDirectory>
    <ExcludeFromSingleFile>true</ExcludeFromSingleFile>
  </Content>
</ItemGroup>
```

## <a name="publish-a-single-file-app---cli"></a><span data-ttu-id="ed50a-124">Tek bir dosya uygulaması yayımlama-CLı</span><span class="sxs-lookup"><span data-stu-id="ed50a-124">Publish a single file app - CLI</span></span>

<span data-ttu-id="ed50a-125">[DotNet Publish](../tools/dotnet-publish.md) komutunu kullanarak tek bir dosya uygulaması yayımlayın.</span><span class="sxs-lookup"><span data-stu-id="ed50a-125">Publish a single file application using the [dotnet publish](../tools/dotnet-publish.md) command.</span></span> <span data-ttu-id="ed50a-126">Uygulamanızı yayımladığınızda, aşağıdaki özellikleri ayarlayın:</span><span class="sxs-lookup"><span data-stu-id="ed50a-126">When you publish your app, set the following properties:</span></span>

- <span data-ttu-id="ed50a-127">Belirli bir çalışma zamanı için yayımlama: `-r win-x64`</span><span class="sxs-lookup"><span data-stu-id="ed50a-127">Publish for a specific runtime: `-r win-x64`</span></span>
- <span data-ttu-id="ed50a-128">Tek dosya olarak yayımla: `-p:PublishSingleFile=true`</span><span class="sxs-lookup"><span data-stu-id="ed50a-128">Publish as a single-file: `-p:PublishSingleFile=true`</span></span>

<span data-ttu-id="ed50a-129">Aşağıdaki örnek, Windows için bir uygulamayı kendi içinde tek bir dosya uygulaması olarak yayımlar.</span><span class="sxs-lookup"><span data-stu-id="ed50a-129">The following example publishes an app for Windows as a self-contained single file application.</span></span>

```dotnetcli
dotnet publish -r win-x64 -p:PublishSingleFile=true --self-contained true
```

<span data-ttu-id="ed50a-130">Aşağıdaki örnek, Framework 'e bağımlı tek dosya uygulaması olarak Linux için bir uygulama yayımlar.</span><span class="sxs-lookup"><span data-stu-id="ed50a-130">The following example publishes an app for Linux as a framework dependent single file application.</span></span>

```dotnetcli
dotnet publish -r linux-x64 -p:PublishSingleFile=true --self-contained false
```

<span data-ttu-id="ed50a-131">Daha fazla bilgi için bkz. [.NET Core uygulamalarını .NET Core CLI yayımlama](deploy-with-cli.md).</span><span class="sxs-lookup"><span data-stu-id="ed50a-131">For more information, see [Publish .NET Core apps with .NET Core CLI](deploy-with-cli.md).</span></span>

## <a name="publish-a-single-file-app---visual-studio"></a><span data-ttu-id="ed50a-132">Tek bir dosya uygulaması yayımlama-Visual Studio</span><span class="sxs-lookup"><span data-stu-id="ed50a-132">Publish a single file app - Visual Studio</span></span>

<span data-ttu-id="ed50a-133">Visual Studio, uygulamanızın nasıl yayımlandığını denetleyen yeniden kullanılabilir yayımlama profilleri oluşturur.</span><span class="sxs-lookup"><span data-stu-id="ed50a-133">Visual Studio creates reusable publishing profiles that control how your application is published.</span></span>

01. <span data-ttu-id="ed50a-134">**Çözüm Gezgini** bölmesinde, yayımlamak istediğiniz projeye sağ tıklayın.</span><span class="sxs-lookup"><span data-stu-id="ed50a-134">On the **Solution Explorer** pane, right-click on the project you want to publish.</span></span> <span data-ttu-id="ed50a-135">**Yayımla**’yı seçin.</span><span class="sxs-lookup"><span data-stu-id="ed50a-135">Select **Publish**.</span></span>

    :::image type="content" source="media/single-file/visual-studio-solution-explorer.png" alt-text="Yayımla seçeneğini vurgulayan sağ tıklama menüsüyle Çözüm Gezgini.":::

    <span data-ttu-id="ed50a-137">Zaten bir yayımlama profiliniz yoksa, bir tane oluşturmak için yönergeleri izleyin ve hedef türü **klasörünü** seçin.</span><span class="sxs-lookup"><span data-stu-id="ed50a-137">If you don't already have a publishing profile, follow the instructions to create one and choose the **Folder** target-type.</span></span>

01. <span data-ttu-id="ed50a-138">**Düzenle**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="ed50a-138">Choose **Edit**.</span></span>

    :::image type="content" source="media/single-file/visual-studio-publish-edit-settings.png" alt-text="Visual Studio Profili Düzenle düğmesi ile Yayımla.":::

01. <span data-ttu-id="ed50a-140">**Profil ayarları** iletişim kutusunda, aşağıdaki seçenekleri ayarlayın:</span><span class="sxs-lookup"><span data-stu-id="ed50a-140">In the **Profile settings** dialog, set the following options:</span></span>

    - <span data-ttu-id="ed50a-141">**Dağıtım modunu** **kendi kendine dahil**olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="ed50a-141">Set **Deployment mode** to **Self-contained**.</span></span>
    - <span data-ttu-id="ed50a-142">**Hedef çalışma zamanını** , yayımlamak istediğiniz platforma ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="ed50a-142">Set **Target runtime** to the platform you want to publish to.</span></span>
    - <span data-ttu-id="ed50a-143">**Tek bir dosya üret**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="ed50a-143">Select **Produce single file**.</span></span>

    <span data-ttu-id="ed50a-144">Ayarları kaydetmek ve **Yayımla** iletişim kutusuna dönmek için **Kaydet** ' i seçin.</span><span class="sxs-lookup"><span data-stu-id="ed50a-144">Choose **Save** to save the settings and return to the **Publish** dialog.</span></span>

    :::image type="content" source="media/single-file/visual-studio-publish-single-file-properties.png" alt-text="Dağıtım modu, hedef çalışma zamanı ve tek dosya seçenekleri vurgulanmış şekilde profil ayarları iletişim kutusu.":::

01. <span data-ttu-id="ed50a-146">Uygulamanızı tek bir dosya olarak yayımlamak için **Yayımla** ' yı seçin.</span><span class="sxs-lookup"><span data-stu-id="ed50a-146">Choose **Publish** to publish your app as a single file.</span></span>

<span data-ttu-id="ed50a-147">Daha fazla bilgi için bkz. [Visual Studio ile .NET Core uygulamalarını yayımlama](deploy-with-vs.md).</span><span class="sxs-lookup"><span data-stu-id="ed50a-147">For more information, see [Publish .NET Core apps with Visual Studio](deploy-with-vs.md).</span></span>

## <a name="publish-a-single-file-app---visual-studio-for-mac"></a><span data-ttu-id="ed50a-148">Tek bir dosya uygulaması yayımlama-Mac için Visual Studio</span><span class="sxs-lookup"><span data-stu-id="ed50a-148">Publish a single file app - Visual Studio for Mac</span></span>

<span data-ttu-id="ed50a-149">Mac için Visual Studio uygulamanızı tek bir dosya olarak yayımlamak için seçenek sağlamıyor.</span><span class="sxs-lookup"><span data-stu-id="ed50a-149">Visual Studio for Mac doesn't provide options to publish your app as a single file.</span></span> <span data-ttu-id="ed50a-150">[Tek dosya App-CLI Yayımla](#publish-a-single-file-app---cli) bölümündeki yönergeleri izleyerek el ile yayımlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="ed50a-150">You'll need to publish manually by following the instructions from the [Publish a single file app - CLI](#publish-a-single-file-app---cli) section.</span></span> <span data-ttu-id="ed50a-151">Daha fazla bilgi için bkz. [.NET Core uygulamalarını .NET Core CLI yayımlama](deploy-with-cli.md).</span><span class="sxs-lookup"><span data-stu-id="ed50a-151">For more information, see [Publish .NET Core apps with .NET Core CLI](deploy-with-cli.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="ed50a-152">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ed50a-152">See also</span></span>

- <span data-ttu-id="ed50a-153">[.NET Core uygulama dağıtımı](index.md).</span><span class="sxs-lookup"><span data-stu-id="ed50a-153">[.NET Core application deployment](index.md).</span></span>
- <span data-ttu-id="ed50a-154">[.NET Core uygulamalarını .NET Core CLI yayımlayın](deploy-with-cli.md).</span><span class="sxs-lookup"><span data-stu-id="ed50a-154">[Publish .NET Core apps with .NET Core CLI](deploy-with-cli.md).</span></span>
- <span data-ttu-id="ed50a-155">[Visual Studio ile .NET Core uygulamaları yayımlayın](deploy-with-vs.md).</span><span class="sxs-lookup"><span data-stu-id="ed50a-155">[Publish .NET Core apps with Visual Studio](deploy-with-vs.md).</span></span>
- <span data-ttu-id="ed50a-156">[ `dotnet publish` komutu](../tools/dotnet-publish.md).</span><span class="sxs-lookup"><span data-stu-id="ed50a-156">[`dotnet publish` command](../tools/dotnet-publish.md).</span></span>
