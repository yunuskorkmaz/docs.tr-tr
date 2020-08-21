---
title: Kendi içindeki uygulamaları kırpma
description: Kendi boyutlarını azaltmak için kendi içindeki uygulamaları nasıl kırpacağınızı öğrenin. .NET Core paketleri kendi içinde yayınlanan ve genellikle çalışma zamanının daha fazlasını içeren bir uygulamayla çalışma zamanı gereklidir.
author: jamshedd
ms.author: jamshedd
ms.date: 04/03/2020
ms.openlocfilehash: 0fde409e9e5911213855ab206368d302b73eebb3
ms.sourcegitcommit: ef86c24c418439b8bb5e3e7d64bbdbe5e11c3e9c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/21/2020
ms.locfileid: "88720130"
---
# <a name="trim-self-contained-deployments-and-executables"></a><span data-ttu-id="b4b79-104">Kendi içinde bulunan dağıtımları ve yürütülebilir dosyaları kırp</span><span class="sxs-lookup"><span data-stu-id="b4b79-104">Trim self-contained deployments and executables</span></span>

<span data-ttu-id="b4b79-105">[Framework 'e bağımlı dağıtım modeli](index.md#publish-framework-dependent) , .net 'in başlangıcından bu yana en başarılı dağıtım modelidir.</span><span class="sxs-lookup"><span data-stu-id="b4b79-105">The [framework-dependent deployment model](index.md#publish-framework-dependent) has been the most successful deployment model since the inception of .NET.</span></span> <span data-ttu-id="b4b79-106">Bu senaryoda, uygulama geliştiricisi yalnızca, .NET çalışma zamanı ve çerçeve kitaplıklarının istemci makinede kullanılabilir olacağı beklentisiyle yalnızca uygulama ve üçüncü taraf derlemeler sunan.</span><span class="sxs-lookup"><span data-stu-id="b4b79-106">In this scenario, the application developer bundles only the application and third-party assemblies with the expectation that the .NET runtime and framework libraries will be available in the client machine.</span></span> <span data-ttu-id="b4b79-107">Bu dağıtım modeli, .NET Core 'da baskın bir tane olmaya devam eder ancak çerçeveye bağımlı modelin en iyi durumda olmadığı bazı senaryolar vardır.</span><span class="sxs-lookup"><span data-stu-id="b4b79-107">This deployment model continues to be the dominant one in .NET Core as well but there are some scenarios where the framework-dependent model is not optimal.</span></span> <span data-ttu-id="b4b79-108">Alternatif olarak, .NET Core çalışma zamanı ve çerçevesinin uygulama ve üçüncü taraf Derlemeleriyle birlikte paketlenmiş olduğu, [kendi kendine içerilen bir uygulama](index.md#publish-self-contained)yayımlamaktır.</span><span class="sxs-lookup"><span data-stu-id="b4b79-108">The alternative is to publish a [self-contained application](index.md#publish-self-contained), where the .NET Core runtime and framework are bundled together with the application and third-party assemblies.</span></span>

<span data-ttu-id="b4b79-109">Kırpma Self-içerilen dağıtım modeli, dağıtım boyutunu azaltmak için optimize edilmiş, kendine dahil edilen dağıtım modelinin özelleşmiş bir sürümüdür.</span><span class="sxs-lookup"><span data-stu-id="b4b79-109">The trim-self-contained deployment model is a specialized version of the self-contained deployment model that is optimized to reduce deployment size.</span></span> <span data-ttu-id="b4b79-110">Dağıtım boyutunu en aza indirmek Blazor uygulamaları gibi bazı istemci tarafı senaryolar için kritik bir gereksinimdir.</span><span class="sxs-lookup"><span data-stu-id="b4b79-110">Minimizing deployment size is a critical requirement for some client-side scenarios like Blazor applications.</span></span> <span data-ttu-id="b4b79-111">Uygulamanın karmaşıklığına bağlı olarak, uygulamayı çalıştırmak için çerçeve derlemelerinin yalnızca bir alt kümesi gereklidir.</span><span class="sxs-lookup"><span data-stu-id="b4b79-111">Depending on the complexity of the application, only a subset of the framework assemblies is required to run the application.</span></span> <span data-ttu-id="b4b79-112">Kitaplığın kullanılmayan bu bölümleri gereksizdir ve paketlenmiş uygulamadan kırpılabilecek.</span><span class="sxs-lookup"><span data-stu-id="b4b79-112">These unused parts of the library are unnecessary and can be trimmed from the packaged application.</span></span> <span data-ttu-id="b4b79-113">Ancak, uygulamanın derleme zamanı analizinin, çeşitli sorunlu kod düzenlerini güvenilir bir şekilde çözümleyemedikleri için çalışma zamanında hatalara neden olabileceği bir risk vardır (büyük ölçüde yansıma kullanımı üzerinde ortalandı).</span><span class="sxs-lookup"><span data-stu-id="b4b79-113">However, there is a risk that the build time analysis of the application can cause failures at runtime, due to not being able to reliably analyze various problematic code patterns (largely centered on reflection use).</span></span> <span data-ttu-id="b4b79-114">Güvenilirlik güvencesi verilmediğinden, bu dağıtım modeli bir önizleme özelliği olarak sunulur.</span><span class="sxs-lookup"><span data-stu-id="b4b79-114">Because reliability can't be guaranteed, this deployment model is offered as a preview feature.</span></span> <span data-ttu-id="b4b79-115">Derleme zamanı Çözümleme altyapısı, sorunlu kod desenlerinin geliştiricisine uyarı sağlar ve bu kod desenlerinin düzeltilme beklentisi olur.</span><span class="sxs-lookup"><span data-stu-id="b4b79-115">The build time analysis engine provides warnings to the developer of code patterns that are problematic, with the expectation that these code patterns will be fixed.</span></span> <span data-ttu-id="b4b79-116">Mümkün olduğunda, aynı gereksinimleri karşılayan kodu kullanarak zaman oluşturmak için uygulamanızdaki çalışma zamanı yansıma bağımlılıklarını taşımanızı öneririz.</span><span class="sxs-lookup"><span data-stu-id="b4b79-116">Where possible, we recommend that you move any runtime reflection dependencies in your application to build time by using code that meets the same requirements.</span></span>

<span data-ttu-id="b4b79-117">Uygulamalar için kırpma modu, Kırım modu aracılığıyla yapılandırılabilir ve `copyused` uygulamada kullanılan derlemeleri paketleyip varsayılan () olur.</span><span class="sxs-lookup"><span data-stu-id="b4b79-117">The trim mode for the applications can be configured via the TrimMode and will default (`copyused`) to bundle assemblies that are used in the application.</span></span> <span data-ttu-id="b4b79-118">Blazor WebAssembly uygulamaları, `link` derlemeler içinde kullanılmayan kodu kırpacak daha agresif bir mod () kullanır.</span><span class="sxs-lookup"><span data-stu-id="b4b79-118">Blazor WebAssembly applications will use a more aggressive mode (`link`) that will trim unused code within assemblies.</span></span> <span data-ttu-id="b4b79-119">Kırpma Analizi uyarıları, tam bağımlılık analizinin mümkün olmadığı kod desenleri hakkında bilgi verir.</span><span class="sxs-lookup"><span data-stu-id="b4b79-119">Trim analysis warnings give information on code patterns where a full dependency analysis was not possible.</span></span> <span data-ttu-id="b4b79-120">Bu uyarılar varsayılan olarak bastırılır ve bayrağı `SuppressTrimAnalysisWarnings` false olarak ayarlanarak açılabilir.</span><span class="sxs-lookup"><span data-stu-id="b4b79-120">These warnings are suppressed by default and can be turned on by setting the flag, `SuppressTrimAnalysisWarnings`, to false.</span></span> <span data-ttu-id="b4b79-121">Kullanılabilir kırpma seçenekleri hakkında daha fazla bilgi için [ılbağlayıcı sayfasında](https://github.com/mono/linker/blob/master/docs/illink-options.md)bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b4b79-121">More information on the trim options available can be found at the [ILLinker page](https://github.com/mono/linker/blob/master/docs/illink-options.md).</span></span>

> [!NOTE]
> <span data-ttu-id="b4b79-122">Kırpma, .NET Core 3,1, 5,0 ' deki deneysel bir özelliktir ve _yalnızca_ kendi içinde yayımlanan uygulamalar tarafından kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="b4b79-122">Trimming is an experimental feature in .NET Core 3.1, 5.0 and is _only_ available to applications that are published self-contained.</span></span>

## <a name="prevent-assemblies-from-being-trimmed"></a><span data-ttu-id="b4b79-123">Derlemelerin kırpılmasına engel</span><span class="sxs-lookup"><span data-stu-id="b4b79-123">Prevent assemblies from being trimmed</span></span>

<span data-ttu-id="b4b79-124">Kırpma işlevinin başvuruları algılayamayacağı senaryolar vardır.</span><span class="sxs-lookup"><span data-stu-id="b4b79-124">There are scenarios in which the trimming functionality will fail to detect references.</span></span> <span data-ttu-id="b4b79-125">Örneğin, yansıma bir çalışma zamanı derlemesinde, uygulamanız veya uygulamanız tarafından başvurulan bir kitaplıkda kullanıldığında, derlemeye doğrudan başvurulmuyor demektir.</span><span class="sxs-lookup"><span data-stu-id="b4b79-125">For example, when reflection is used on a runtime assembly, either by your application or a library that is referenced by your application, the assembly isn't directly referenced.</span></span> <span data-ttu-id="b4b79-126">Kırpma, bu dolaylı başvuruların farkında değildir ve kitaplığı yayımlanan klasörden hariç tutar.</span><span class="sxs-lookup"><span data-stu-id="b4b79-126">Trimming is unaware of these indirect references and would exclude the library from the published folder.</span></span>

<span data-ttu-id="b4b79-127">Kod, yansıma aracılığıyla bir derlemeye dolaylı olarak başvurduğunda, derlemenin ayarla kırpılmasına engel olabilirsiniz `<TrimmerRootAssembly>` .</span><span class="sxs-lookup"><span data-stu-id="b4b79-127">When the code is indirectly referencing an assembly through reflection, you can prevent the assembly from being trimmed with the `<TrimmerRootAssembly>` setting.</span></span> <span data-ttu-id="b4b79-128">Aşağıdaki örnek, derleme adlı derlemenin kırpılmasını nasıl önleyekullanacağınızı gösterir `System.Security` :</span><span class="sxs-lookup"><span data-stu-id="b4b79-128">The following example shows how to prevent an assembly called `System.Security` assembly from being trimmed:</span></span>

```xml
<ItemGroup>
    <TrimmerRootAssembly Include="System.Security" />
</ItemGroup>
```

## <a name="trim-your-app---cli"></a><span data-ttu-id="b4b79-129">Uygulamanızı kırpın-CLı</span><span class="sxs-lookup"><span data-stu-id="b4b79-129">Trim your app - CLI</span></span>

<span data-ttu-id="b4b79-130">[DotNet Publish](../tools/dotnet-publish.md) komutunu kullanarak uygulamanızı kırpın.</span><span class="sxs-lookup"><span data-stu-id="b4b79-130">Trim your application using the [dotnet publish](../tools/dotnet-publish.md) command.</span></span> <span data-ttu-id="b4b79-131">Uygulamanızı yayımladığınızda, aşağıdaki üç ayarı ayarlayın:</span><span class="sxs-lookup"><span data-stu-id="b4b79-131">When you publish your app, set the following three settings:</span></span>

- <span data-ttu-id="b4b79-132">Kendi içinde Yayımla: `--self-contained true`</span><span class="sxs-lookup"><span data-stu-id="b4b79-132">Publish as self-contained: `--self-contained true`</span></span>
- <span data-ttu-id="b4b79-133">Kırpmayı etkinleştir: `p:PublishTrimmed=true`</span><span class="sxs-lookup"><span data-stu-id="b4b79-133">Enable trimming: `p:PublishTrimmed=true`</span></span>

<span data-ttu-id="b4b79-134">Aşağıdaki örnek, Windows için bir uygulamayı kendi içinde yayınlar ve çıktıyı kırpar.</span><span class="sxs-lookup"><span data-stu-id="b4b79-134">The following example publishes an app for Windows as self-contained and trims the output.</span></span>

```xml
<ItemGroup>
    <RuntimeIdentifier>win-x64</RuntimeIdentifier>
    <SelfContained>true</SelfContained>
    <PublishTrimmed>true</PublishTrimmed>
</ItemGroup>
```

<span data-ttu-id="b4b79-135">Aşağıdaki örnek, derleme içinde kullanılmayan kodun kırpılıp kırpılmayabileceği, agresif kırpma modunda bir uygulama yayımlar.</span><span class="sxs-lookup"><span data-stu-id="b4b79-135">The following example publishes an app in the aggressive trim mode where unused code within assemblies will be trimmed and  trimmer warnings enabled.</span></span>

```xml
<ItemGroup>
    <TrimMode>link</TrimMode>
    <SuppressTrimAnalysisWarnings>false</SuppressTrimAnalysisWarnings>
</ItemGroup>
```

<span data-ttu-id="b4b79-136">Daha fazla bilgi için bkz. [.NET Core uygulamalarını .NET Core CLI yayımlama](deploy-with-cli.md).</span><span class="sxs-lookup"><span data-stu-id="b4b79-136">For more information, see [Publish .NET Core apps with .NET Core CLI](deploy-with-cli.md).</span></span>

## <a name="trim-your-app---visual-studio"></a><span data-ttu-id="b4b79-137">Uygulamanızı kırpın-Visual Studio</span><span class="sxs-lookup"><span data-stu-id="b4b79-137">Trim your app - Visual Studio</span></span>

<span data-ttu-id="b4b79-138">Visual Studio, uygulamanızın nasıl yayımlandığını denetleyen yeniden kullanılabilir yayımlama profilleri oluşturur.</span><span class="sxs-lookup"><span data-stu-id="b4b79-138">Visual Studio creates reusable publishing profiles that control how your application is published.</span></span>

01. <span data-ttu-id="b4b79-139">**Çözüm Gezgini** bölmesinde, yayımlamak istediğiniz projeye sağ tıklayın.</span><span class="sxs-lookup"><span data-stu-id="b4b79-139">On the **Solution Explorer** pane, right-click on the project you want to publish.</span></span> <span data-ttu-id="b4b79-140">Yayımla ' yı seçin.. **.**</span><span class="sxs-lookup"><span data-stu-id="b4b79-140">Select **Publish...**.</span></span>

    :::image type="content" source="media/trim-self-contained/visual-studio-solution-explorer.png" alt-text="Yayımla seçeneğini vurgulayan sağ tıklama menüsüyle Çözüm Gezgini.":::

    <span data-ttu-id="b4b79-142">Zaten bir yayımlama profiliniz yoksa, bir tane oluşturmak için yönergeleri izleyin ve hedef türü **klasörünü** seçin.</span><span class="sxs-lookup"><span data-stu-id="b4b79-142">If you don't already have a publishing profile, follow the instructions to create one and choose the **Folder** target-type.</span></span>

01. <span data-ttu-id="b4b79-143">**Düzenle**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="b4b79-143">Choose **Edit**.</span></span>

    :::image type="content" source="media/trim-self-contained/visual-studio-publish-edit-settings.png" alt-text="Visual Studio Profili Düzenle düğmesi ile Yayımla.":::

01. <span data-ttu-id="b4b79-145">**Profil ayarları** iletişim kutusunda, aşağıdaki seçenekleri ayarlayın:</span><span class="sxs-lookup"><span data-stu-id="b4b79-145">In the **Profile settings** dialog, set the following options:</span></span>

    - <span data-ttu-id="b4b79-146">**Dağıtım modunu** **kendi kendine dahil**olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="b4b79-146">Set **Deployment mode** to **Self-contained**.</span></span>
    - <span data-ttu-id="b4b79-147">**Hedef çalışma zamanını** , yayımlamak istediğiniz platforma ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="b4b79-147">Set **Target runtime** to the platform you want to publish to.</span></span>
    - <span data-ttu-id="b4b79-148">**Kullanılmayan derlemeleri Kırp (önizlemede)** seçeneğini belirleyin.</span><span class="sxs-lookup"><span data-stu-id="b4b79-148">Select **Trim unused assemblies (in preview)**.</span></span>

    <span data-ttu-id="b4b79-149">Ayarları kaydetmek ve **Yayımla** iletişim kutusuna dönmek için **Kaydet** ' i seçin.</span><span class="sxs-lookup"><span data-stu-id="b4b79-149">Choose **Save** to save the settings and return to the **Publish** dialog.</span></span>

    :::image type="content" source="media/trim-self-contained/visual-studio-publish-properties.png" alt-text="Dağıtım modu, hedef çalışma zamanı ve kullanılmayan derlemeleri Kırp seçeneklerinin vurgulandığı profil ayarları iletişim kutusu.":::

01. <span data-ttu-id="b4b79-151">Uygulamanızı yayımlamak için **Yayımla** ' yı seçin.</span><span class="sxs-lookup"><span data-stu-id="b4b79-151">Choose **Publish** to publish your app trimmed.</span></span>

<span data-ttu-id="b4b79-152">Daha fazla bilgi için bkz. [Visual Studio ile .NET Core uygulamalarını yayımlama](deploy-with-vs.md).</span><span class="sxs-lookup"><span data-stu-id="b4b79-152">For more information, see [Publish .NET Core apps with Visual Studio](deploy-with-vs.md).</span></span>

## <a name="trim-your-app---visual-studio-for-mac"></a><span data-ttu-id="b4b79-153">Uygulamanızı kırpın-Mac için Visual Studio</span><span class="sxs-lookup"><span data-stu-id="b4b79-153">Trim your app - Visual Studio for Mac</span></span>

<span data-ttu-id="b4b79-154">Mac için Visual Studio yayımlama sırasında uygulamanızı kırpmak için seçenek sağlamıyor.</span><span class="sxs-lookup"><span data-stu-id="b4b79-154">Visual Studio for Mac doesn't provide options to trim your app during publish.</span></span> <span data-ttu-id="b4b79-155">[Uygulamanızı Kırp-CLI](#trim-your-app---cli) bölümündeki yönergeleri izleyerek el ile yayımlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="b4b79-155">You'll need to publish manually by following the instructions from the [Trim your app - CLI](#trim-your-app---cli) section.</span></span> <span data-ttu-id="b4b79-156">Daha fazla bilgi için bkz. [.NET Core uygulamalarını .NET Core CLI yayımlama](deploy-with-cli.md).</span><span class="sxs-lookup"><span data-stu-id="b4b79-156">For more information, see [Publish .NET Core apps with .NET Core CLI](deploy-with-cli.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="b4b79-157">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b4b79-157">See also</span></span>

- <span data-ttu-id="b4b79-158">[.NET Core uygulama dağıtımı](index.md).</span><span class="sxs-lookup"><span data-stu-id="b4b79-158">[.NET Core application deployment](index.md).</span></span>
- <span data-ttu-id="b4b79-159">[.NET Core uygulamalarını .NET Core CLI yayımlayın](deploy-with-cli.md).</span><span class="sxs-lookup"><span data-stu-id="b4b79-159">[Publish .NET Core apps with .NET Core CLI](deploy-with-cli.md).</span></span>
- <span data-ttu-id="b4b79-160">[Visual Studio ile .NET Core uygulamaları yayımlayın](deploy-with-vs.md).</span><span class="sxs-lookup"><span data-stu-id="b4b79-160">[Publish .NET Core apps with Visual Studio](deploy-with-vs.md).</span></span>
- <span data-ttu-id="b4b79-161">[DotNet Publish komutu](../tools/dotnet-publish.md).</span><span class="sxs-lookup"><span data-stu-id="b4b79-161">[dotnet publish command](../tools/dotnet-publish.md).</span></span>
