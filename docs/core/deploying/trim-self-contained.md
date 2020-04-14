---
title: Kendi kendine yeten uygulamaları kırpma
description: Boyutlarını azaltmak için bağımsız uygulamaları nasıl kırptığınızı öğrenin. .NET Core, çalışma süresini kendi kendine çalışan bir uygulamayla paketler ve genellikle çalışma süresinin daha fazlasını içerir ve o zaman gereklidir.
author: jamshedd
ms.author: jamshedd
ms.date: 04/03/2020
ms.openlocfilehash: bb8ac88c5e16b7fd20a7670e4ad76dbe4b44da1b
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/13/2020
ms.locfileid: "81242936"
---
# <a name="trim-self-contained-deployments-and-executables"></a><span data-ttu-id="e9113-104">Kendi içinde bulunan dağıtımları ve yürütülebilir dosyaları kırp</span><span class="sxs-lookup"><span data-stu-id="e9113-104">Trim self-contained deployments and executables</span></span>

<span data-ttu-id="e9113-105">Bir uygulama bağımsız yayımlanırken,.NET Core çalışma süresi uygulamayla birlikte paketlenir.</span><span class="sxs-lookup"><span data-stu-id="e9113-105">When publishing an application self-contained, the .NET Core runtime is bundled together with the application.</span></span> <span data-ttu-id="e9113-106">Bu birleştirme, paket uygulamanıza önemli miktarda içerik ekler.</span><span class="sxs-lookup"><span data-stu-id="e9113-106">This bundling adds a significant amount of content to your packaged application.</span></span> <span data-ttu-id="e9113-107">Uygulamanızı dağıtma söz konusu olduğunda, boyut genellikle önemli bir faktördür.</span><span class="sxs-lookup"><span data-stu-id="e9113-107">When it comes to deploying your application, size is often an important factor.</span></span> <span data-ttu-id="e9113-108">Paket uygulamasının boyutunu mümkün olduğunca küçük tutmak genellikle uygulama geliştiricileri için bir hedeftir.</span><span class="sxs-lookup"><span data-stu-id="e9113-108">Keeping the size of the package application as small as possible is typically a goal for application developers.</span></span>

<span data-ttu-id="e9113-109">Uygulamanın karmaşıklığına bağlı olarak, uygulamayı çalıştırmak için yalnızca çalışma zamanının bir alt kümesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="e9113-109">Depending on the complexity of the application, only a subset of the runtime is required to run the application.</span></span> <span data-ttu-id="e9113-110">Çalışma zamanının bu kullanılmayan bölümleri gereksizdir ve paket uygulamadan kesilebilir.</span><span class="sxs-lookup"><span data-stu-id="e9113-110">These unused parts of the runtime are unnecessary and can be trimmed from the packaged application.</span></span>

<span data-ttu-id="e9113-111">Kırpma özelliği, gerekli çalışma zamanı derlemelerinin bir grafiğini keşfetmek ve oluşturmak için uygulama ikililerini inceleyerek çalışır.</span><span class="sxs-lookup"><span data-stu-id="e9113-111">The trimming feature works by examining the application binaries to discover and build a graph of the required runtime assemblies.</span></span> <span data-ttu-id="e9113-112">Başvurulamayan kalan çalışma zamanı derlemeleri hariç tutulur.</span><span class="sxs-lookup"><span data-stu-id="e9113-112">The remaining runtime assemblies that aren't referenced are excluded.</span></span>

> [!NOTE]
> <span data-ttu-id="e9113-113">Kırpma ,NET Core 3.1'de deneysel bir özelliktir ve _yalnızca_ bağımsız olarak yayınlanan uygulamalar için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="e9113-113">Trimming is an experimental feature in .NET Core 3.1 and is _only_ available to applications that are published self-contained.</span></span>

## <a name="prevent-assemblies-from-being-trimmed"></a><span data-ttu-id="e9113-114">Montajların kırpılmasını önleyin</span><span class="sxs-lookup"><span data-stu-id="e9113-114">Prevent assemblies from being trimmed</span></span>

<span data-ttu-id="e9113-115">Kırpma işlevinin başvuruları algılayamadığı senaryolar vardır.</span><span class="sxs-lookup"><span data-stu-id="e9113-115">There are scenarios in which the trimming functionality will fail to detect references.</span></span> <span data-ttu-id="e9113-116">Örneğin, uygulamanız veya uygulamanız tarafından başvurulan bir kitaplık tarafından bir çalışma zamanı derlemesi üzerinde yansıma kullanıldığında, derleme doğrudan başvurulmuyor.</span><span class="sxs-lookup"><span data-stu-id="e9113-116">For example, when reflection is used on a runtime assembly, either by your application or a library that is referenced by your application, the assembly isn't directly referenced.</span></span> <span data-ttu-id="e9113-117">Kırpma bu dolaylı başvurulardan habersizdir ve kitaplığı yayımlanmış klasöründen dışlar.</span><span class="sxs-lookup"><span data-stu-id="e9113-117">Trimming is unaware of these indirect references and would exclude the library from the published folder.</span></span>

<span data-ttu-id="e9113-118">Kod dolaylı olarak yansıma yoluyla bir derlemeye başvururken, derlemenin `<TrimmerRootAssembly>` ayarla birlikte kırpılmasını engelleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e9113-118">When the code is indirectly referencing an assembly through reflection, you can prevent the assembly from being trimmed with the `<TrimmerRootAssembly>` setting.</span></span> <span data-ttu-id="e9113-119">Aşağıdaki örnek, derleme adı verilen `System.Security` bir derlemenin nasıl kırpılmasının önlenişretilenin ilerler:</span><span class="sxs-lookup"><span data-stu-id="e9113-119">The following example shows how to prevent an assembly called `System.Security` assembly from being trimmed:</span></span>

```xml
<ItemGroup>
    <TrimmerRootAssembly Include="System.Security" />
</ItemGroup>
```

## <a name="trim-your-app---cli"></a><span data-ttu-id="e9113-120">Uygulamanızı kırpın - CLI</span><span class="sxs-lookup"><span data-stu-id="e9113-120">Trim your app - CLI</span></span>

<span data-ttu-id="e9113-121">[Dotnet yayımlama](../tools/dotnet-publish.md) komutunu kullanarak uygulamanızı kırpın.</span><span class="sxs-lookup"><span data-stu-id="e9113-121">Trim your application using the [dotnet publish](../tools/dotnet-publish.md) command.</span></span> <span data-ttu-id="e9113-122">Uygulamanızı yayımladığınızda aşağıdaki üç ayarı ayarlayın:</span><span class="sxs-lookup"><span data-stu-id="e9113-122">When you publish your app, set the following three settings:</span></span>

- <span data-ttu-id="e9113-123">Bağımsız olarak yayımlayın:`--self-contained true`</span><span class="sxs-lookup"><span data-stu-id="e9113-123">Publish as self-contained: `--self-contained true`</span></span>
- <span data-ttu-id="e9113-124">Tek dosyalı yayımlamayı devre dışı:`-p:PublishSingleFile=false`</span><span class="sxs-lookup"><span data-stu-id="e9113-124">Disable single-file publishing: `-p:PublishSingleFile=false`</span></span>
- <span data-ttu-id="e9113-125">Kırpma yı etkinleştirme:`p:PublishTrimmed=true`</span><span class="sxs-lookup"><span data-stu-id="e9113-125">Enable trimming: `p:PublishTrimmed=true`</span></span>

<span data-ttu-id="e9113-126">Aşağıdaki örnek, Windows 10 için bir uygulamayı bağımsız olarak yayımlar ve çıktıyı kırpar.</span><span class="sxs-lookup"><span data-stu-id="e9113-126">The following example publishes an app for Windows 10 as self-contained and trims the output.</span></span>

```dotnetcli
dotnet publish -c Release -r win10-x64 --self-contained true -p:PublishSingleFile=false -p:PublishTrimmed=true
```

<span data-ttu-id="e9113-127">Daha fazla bilgi için [bkz.](deploy-with-cli.md)</span><span class="sxs-lookup"><span data-stu-id="e9113-127">For more information, see [Publish .NET Core apps with .NET Core CLI](deploy-with-cli.md).</span></span>

## <a name="trim-your-app---visual-studio"></a><span data-ttu-id="e9113-128">Uygulamanızı kırpın - Visual Studio</span><span class="sxs-lookup"><span data-stu-id="e9113-128">Trim your app - Visual Studio</span></span>

<span data-ttu-id="e9113-129">Visual Studio, uygulamanızın nasıl yayımlandığını denetleyen yeniden kullanılabilir yayımlama profilleri oluşturur.</span><span class="sxs-lookup"><span data-stu-id="e9113-129">Visual Studio creates reusable publishing profiles that control how your application is published.</span></span>

01. <span data-ttu-id="e9113-130">Çözüm **Gezgini** bölmesine, yayımlamak istediğiniz projeye sağ tıklayın.</span><span class="sxs-lookup"><span data-stu-id="e9113-130">On the **Solution Explorer** pane, right-click on the project you want to publish.</span></span> <span data-ttu-id="e9113-131">**Yayımla'yı seçin...**.</span><span class="sxs-lookup"><span data-stu-id="e9113-131">Select **Publish...**.</span></span>

    :::image type="content" source="media/trim-self-contained/visual-studio-solution-explorer.png" alt-text="Yayımla seçeneğini vurgulayan sağ tıklama menüsüyle Çözüm Gezgini.":::

    <span data-ttu-id="e9113-133">Zaten bir yayımlama profiliniz yoksa, bir tane oluşturmak için yönergeleri izleyin ve **Klasör** hedef türünü seçin.</span><span class="sxs-lookup"><span data-stu-id="e9113-133">If you don't already have a publishing profile, follow the instructions to create one and choose the **Folder** target-type.</span></span>

01. <span data-ttu-id="e9113-134">**Edit'i**seçin.</span><span class="sxs-lookup"><span data-stu-id="e9113-134">Choose **Edit**.</span></span>

    :::image type="content" source="media/trim-self-contained/visual-studio-publish-edit-settings.png" alt-text="Visual studio, profili edit düğmesiyle yayımlar.":::

01. <span data-ttu-id="e9113-136">Profil **ayarları** iletişim kutusunda aşağıdaki seçenekleri ayarlayın:</span><span class="sxs-lookup"><span data-stu-id="e9113-136">In the **Profile settings** dialog, set the following options:</span></span>

    - <span data-ttu-id="e9113-137">**Dağıtım modunu** **Bağımsız**olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="e9113-137">Set **Deployment mode** to **Self-contained**.</span></span>
    - <span data-ttu-id="e9113-138">**Hedef çalışma zamanını** yayınlamak istediğiniz platforma ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="e9113-138">Set **Target runtime** to the platform you want to publish to.</span></span>
    - <span data-ttu-id="e9113-139">**Kullanılmayan derlemeleri Kırp'ı (önizlemede)** seçin.</span><span class="sxs-lookup"><span data-stu-id="e9113-139">Select **Trim unused assemblies (in preview)**.</span></span>

    <span data-ttu-id="e9113-140">Ayarları kaydetmek ve **Yayımla** iletişim kutusuna dönmek için **Kaydet'i** seçin.</span><span class="sxs-lookup"><span data-stu-id="e9113-140">Choose **Save** to save the settings and return to the **Publish** dialog.</span></span>

    :::image type="content" source="media/trim-self-contained/visual-studio-publish-properties.png" alt-text="Dağıtım modu, hedef çalışma zamanı ve kullanılmayan derlemeleri kırpma seçenekleri vurgulanan profil ayarları iletişim kutusu.":::

01. <span data-ttu-id="e9113-142">Kesilmiş uygulamanızı yayınlamak için **Yayımla'yı** seçin.</span><span class="sxs-lookup"><span data-stu-id="e9113-142">Choose **Publish** to publish your app trimmed.</span></span>

<span data-ttu-id="e9113-143">Daha fazla bilgi için [bkz.](deploy-with-vs.md)</span><span class="sxs-lookup"><span data-stu-id="e9113-143">For more information, see [Publish .NET Core apps with Visual Studio](deploy-with-vs.md).</span></span>

## <a name="trim-your-app---visual-studio-for-mac"></a><span data-ttu-id="e9113-144">Uygulamanızı kırpın - Mac için Visual Studio</span><span class="sxs-lookup"><span data-stu-id="e9113-144">Trim your app - Visual Studio for Mac</span></span>

<span data-ttu-id="e9113-145">Mac için Visual Studio, yayın sırasında uygulamanızı kırpma seçenekleri sağlamaz.</span><span class="sxs-lookup"><span data-stu-id="e9113-145">Visual Studio for Mac doesn't provide options to trim your app during publish.</span></span> <span data-ttu-id="e9113-146">[Uygulamanızı Kırpma - CLI](#trim-your-app---cli) bölümündeki yönergeleri izleyerek el ile yayınlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="e9113-146">You'll need to publish manually by following the instructions from the [Trim your app - CLI](#trim-your-app---cli) section.</span></span> <span data-ttu-id="e9113-147">Daha fazla bilgi için [bkz.](deploy-with-cli.md)</span><span class="sxs-lookup"><span data-stu-id="e9113-147">For more information, see [Publish .NET Core apps with .NET Core CLI](deploy-with-cli.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="e9113-148">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e9113-148">See also</span></span>

- <span data-ttu-id="e9113-149">[.NET Çekirdek uygulama dağıtımı](index.md).</span><span class="sxs-lookup"><span data-stu-id="e9113-149">[.NET Core application deployment](index.md).</span></span>
- <span data-ttu-id="e9113-150">[.NET Core CLI ile .NET Core uygulamalarını yayımlayın.](deploy-with-cli.md)</span><span class="sxs-lookup"><span data-stu-id="e9113-150">[Publish .NET Core apps with .NET Core CLI](deploy-with-cli.md).</span></span>
- <span data-ttu-id="e9113-151">[.NET Core uygulamalarını Visual Studio ile yayımlayın.](deploy-with-vs.md)</span><span class="sxs-lookup"><span data-stu-id="e9113-151">[Publish .NET Core apps with Visual Studio](deploy-with-vs.md).</span></span>
- <span data-ttu-id="e9113-152">[dotnet yayımlama komutu](../tools/dotnet-publish.md).</span><span class="sxs-lookup"><span data-stu-id="e9113-152">[dotnet publish command](../tools/dotnet-publish.md).</span></span>
