---
title: Kendi içindeki uygulamaları kırpma
description: Kendi boyutlarını azaltmak için kendi içindeki uygulamaları nasıl kırpacağınızı öğrenin. .NET Core paketleri kendi içinde yayınlanan ve genellikle çalışma zamanının daha fazlasını içeren bir uygulamayla çalışma zamanı gereklidir.
author: jamshedd
ms.author: jamshedd
ms.date: 04/03/2020
ms.openlocfilehash: b5e2650d8240648aa05eaa9026a57b926f63b4de
ms.sourcegitcommit: c7f0beaa2bd66ebca86362ca17d673f7e8256ca6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/23/2021
ms.locfileid: "104872879"
---
# <a name="trim-self-contained-deployments-and-executables"></a><span data-ttu-id="99848-104">Kendi içinde bulunan dağıtımları ve yürütülebilir dosyaları kırp</span><span class="sxs-lookup"><span data-stu-id="99848-104">Trim self-contained deployments and executables</span></span>

<span data-ttu-id="99848-105">[Framework 'e bağımlı dağıtım modeli](index.md#publish-framework-dependent) , .net 'in başlangıcından bu yana en başarılı dağıtım modelidir.</span><span class="sxs-lookup"><span data-stu-id="99848-105">The [framework-dependent deployment model](index.md#publish-framework-dependent) has been the most successful deployment model since the inception of .NET.</span></span> <span data-ttu-id="99848-106">Bu senaryoda, uygulama geliştiricisi yalnızca, .NET çalışma zamanı ve çerçeve kitaplıklarının istemci makinede kullanılabilir olacağı beklentisiyle yalnızca uygulama ve üçüncü taraf derlemeler sunan.</span><span class="sxs-lookup"><span data-stu-id="99848-106">In this scenario, the application developer bundles only the application and third-party assemblies with the expectation that the .NET runtime and framework libraries will be available in the client machine.</span></span> <span data-ttu-id="99848-107">Bu dağıtım modeli, .NET Core 'da baskın bir tane olmaya devam eder ancak çerçeveye bağımlı modelin en iyi durumda olmadığı bazı senaryolar vardır.</span><span class="sxs-lookup"><span data-stu-id="99848-107">This deployment model continues to be the dominant one in .NET Core as well but there are some scenarios where the framework-dependent model is not optimal.</span></span> <span data-ttu-id="99848-108">Alternatif olarak, .NET Core çalışma zamanı ve çerçevesinin uygulama ve üçüncü taraf Derlemeleriyle birlikte paketlenmiş olduğu, [kendi kendine içerilen bir uygulama](index.md#publish-self-contained)yayımlamaktır.</span><span class="sxs-lookup"><span data-stu-id="99848-108">The alternative is to publish a [self-contained application](index.md#publish-self-contained), where the .NET Core runtime and framework are bundled together with the application and third-party assemblies.</span></span>

<span data-ttu-id="99848-109">Kırpma Self-içerilen dağıtım modeli, dağıtım boyutunu azaltmak için optimize edilmiş, kendine dahil edilen dağıtım modelinin özelleşmiş bir sürümüdür.</span><span class="sxs-lookup"><span data-stu-id="99848-109">The trim-self-contained deployment model is a specialized version of the self-contained deployment model that is optimized to reduce deployment size.</span></span> <span data-ttu-id="99848-110">Dağıtım boyutunu en aza indirmek Blazor uygulamaları gibi bazı istemci tarafı senaryolar için kritik bir gereksinimdir.</span><span class="sxs-lookup"><span data-stu-id="99848-110">Minimizing deployment size is a critical requirement for some client-side scenarios like Blazor applications.</span></span> <span data-ttu-id="99848-111">Uygulamanın karmaşıklığına bağlı olarak, yalnızca çerçeve derlemelerinin bir alt kümesine başvurulur ve uygulamayı çalıştırmak için her derleme içindeki kodun bir alt kümesi gereklidir.</span><span class="sxs-lookup"><span data-stu-id="99848-111">Depending on the complexity of the application, only a subset of the framework assemblies are referenced, and a subset of the code within each assembly is required to run the application.</span></span> <span data-ttu-id="99848-112">Kitaplıkların kullanılmayan bölümleri gereksizdir ve paketlenmiş uygulamadan kırpılabilecek.</span><span class="sxs-lookup"><span data-stu-id="99848-112">The unused parts of the libraries are unnecessary and can be trimmed from the packaged application.</span></span>

<span data-ttu-id="99848-113">Ancak, uygulamanın derleme zamanı analizinin, çeşitli sorunlu kod düzenlerini güvenilir bir şekilde çözümleyemedikleri için çalışma zamanında hatalara neden olabileceği bir risk vardır (büyük ölçüde yansıma kullanımı üzerinde ortalandı).</span><span class="sxs-lookup"><span data-stu-id="99848-113">However, there is a risk that the build time analysis of the application can cause failures at runtime, due to not being able to reliably analyze various problematic code patterns (largely centered on reflection use).</span></span> <span data-ttu-id="99848-114">Güvenilirlik güvencesi verilmediğinden, bu dağıtım modeli bir önizleme özelliği olarak sunulur.</span><span class="sxs-lookup"><span data-stu-id="99848-114">Because reliability can't be guaranteed, this deployment model is offered as a preview feature.</span></span>

<span data-ttu-id="99848-115">Derleme zamanı Çözümleme altyapısı, hangi diğer kodun gerekli olduğunu tespit etmek için sorunlu kod desenlerinin geliştiricisine uyarı sağlar.</span><span class="sxs-lookup"><span data-stu-id="99848-115">The build time analysis engine provides warnings to the developer of code patterns that are problematic to detect which other code is required.</span></span> <span data-ttu-id="99848-116">Koda, başka nelerin dahil edileceğini söylemek için koda açıklama eklenebilir.</span><span class="sxs-lookup"><span data-stu-id="99848-116">Code can be annotated with attributes to tell the trimmer what else to include.</span></span> <span data-ttu-id="99848-117">Birçok yansıma deseni, [kaynak](https://github.com/dotnet/roslyn/blob/main/docs/features/source-generators.md)oluşturucuları kullanılarak derleme zamanı kod üretimi ile değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="99848-117">Many reflection patterns can be replaced with build-time code generation using [Source Generators](https://github.com/dotnet/roslyn/blob/main/docs/features/source-generators.md).</span></span>

<span data-ttu-id="99848-118">Uygulamalar için kırpma modu ayarı ile yapılandırılır `TrimMode` .</span><span class="sxs-lookup"><span data-stu-id="99848-118">The trim mode for the applications is configured with the `TrimMode` setting.</span></span> <span data-ttu-id="99848-119">Varsayılan değer ve, `copyused` uygulamayla birlikte başvurulan derlemelerdir.</span><span class="sxs-lookup"><span data-stu-id="99848-119">The default value is `copyused` and bundles referenced assemblies with the application.</span></span> <span data-ttu-id="99848-120">`link`Değer, Blazor WebAssembly uygulamalarıyla kullanılır ve derlemeler içinde kullanılmayan kodu kırpar.</span><span class="sxs-lookup"><span data-stu-id="99848-120">The `link` value is used with Blazor WebAssembly applications and trims unused code within assemblies.</span></span> <span data-ttu-id="99848-121">Kırpma Analizi uyarıları, tam bağımlılık analizinin mümkün olmadığı kod desenleri hakkında bilgi verir.</span><span class="sxs-lookup"><span data-stu-id="99848-121">Trim analysis warnings give information on code patterns where a full dependency analysis was not possible.</span></span> <span data-ttu-id="99848-122">Bu uyarılar varsayılan olarak bastırılır ve bayrağı olarak ayarlanarak açılabilir `SuppressTrimAnalysisWarnings` `false` .</span><span class="sxs-lookup"><span data-stu-id="99848-122">These warnings are suppressed by default and can be turned on by setting the flag `SuppressTrimAnalysisWarnings` to `false`.</span></span> <span data-ttu-id="99848-123">Kullanılabilir kırpma seçenekleri hakkında daha fazla bilgi için bkz. [kırpma seçenekleri](trimming-options.md).</span><span class="sxs-lookup"><span data-stu-id="99848-123">For more information about the trim options available, see [Trimming options](trimming-options.md).</span></span>

> [!NOTE]
> <span data-ttu-id="99848-124">Kırpma, .NET Core 3,1 ve .NET 5,0 ' de deneysel bir özelliktir.</span><span class="sxs-lookup"><span data-stu-id="99848-124">Trimming is an experimental feature in .NET Core 3.1 and .NET 5.0.</span></span> <span data-ttu-id="99848-125">Kırpma _yalnızca_ kendi içinde yayımlanan uygulamalar için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="99848-125">Trimming is _only_ available to applications that are published self-contained.</span></span>

## <a name="prevent-assemblies-from-being-trimmed"></a><span data-ttu-id="99848-126">Derlemelerin kırpılmasına engel</span><span class="sxs-lookup"><span data-stu-id="99848-126">Prevent assemblies from being trimmed</span></span>

<span data-ttu-id="99848-127">Kırpma işlevinin başvuruları algılayamayacağı senaryolar vardır.</span><span class="sxs-lookup"><span data-stu-id="99848-127">There are scenarios in which the trimming functionality will fail to detect references.</span></span> <span data-ttu-id="99848-128">Örneğin, yansıma bir çalışma zamanı derlemesinde, uygulamanız veya uygulamanız tarafından başvurulan bir kitaplıkda kullanıldığında, derlemeye doğrudan başvurulmuyor demektir.</span><span class="sxs-lookup"><span data-stu-id="99848-128">For example, when reflection is used on a runtime assembly, either by your application or a library that is referenced by your application, the assembly isn't directly referenced.</span></span> <span data-ttu-id="99848-129">Kırpma, bu dolaylı başvuruların farkında değildir ve kitaplığı yayımlanan klasörden hariç tutar.</span><span class="sxs-lookup"><span data-stu-id="99848-129">Trimming is unaware of these indirect references and would exclude the library from the published folder.</span></span>

<span data-ttu-id="99848-130">Kod, yansıma aracılığıyla bir derlemeye dolaylı olarak başvurduğunda, derlemenin ayarla kırpılmasına engel olabilirsiniz `<TrimmerRootAssembly>` .</span><span class="sxs-lookup"><span data-stu-id="99848-130">When the code is indirectly referencing an assembly through reflection, you can prevent the assembly from being trimmed with the `<TrimmerRootAssembly>` setting.</span></span> <span data-ttu-id="99848-131">Aşağıdaki örnek, derleme adlı derlemenin kırpılmasını nasıl önleyekullanacağınızı gösterir `System.Security` :</span><span class="sxs-lookup"><span data-stu-id="99848-131">The following example shows how to prevent an assembly called `System.Security` assembly from being trimmed:</span></span>

```xml
<ItemGroup>
    <TrimmerRootAssembly Include="System.Security" />
</ItemGroup>
```

### <a name="support-for-ssl-certificates"></a><span data-ttu-id="99848-132">SSL sertifikaları için destek</span><span class="sxs-lookup"><span data-stu-id="99848-132">Support for SSL certificates</span></span>

<span data-ttu-id="99848-133">Uygulamanız, ASP.NET Core bir uygulamada olduğu gibi SSL sertifikaları yüklerse, kırpılırken, SSL sertifikalarını yüklemeye yardımcı olacak olan derlemeleri kırpmaya engel olmanızı sağlamak isteyeceksiniz.</span><span class="sxs-lookup"><span data-stu-id="99848-133">If your app loads SSL certificates, such as in an ASP.NET Core app, you'll want to ensure that when trimming you prevent trimming assemblies that will help with loading SSL certificates.</span></span>

<span data-ttu-id="99848-134">Proje dosyanızı, ASP.NET Core 3,1 için aşağıdakileri içerecek şekilde güncelleştirebiliriz:</span><span class="sxs-lookup"><span data-stu-id="99848-134">We can update our project file to include the following for ASP.NET Core 3.1:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk.Web">
  <PropertyGroup>...</PropertyGroup>
  <!--Include the following for .aspnetcore 3.1-->
  <ItemGroup>
    <TrimmerRootAssembly Include="System.Net" />
    <TrimmerRootAssembly Include="System.Net.Security" />
    <TrimmerRootAssembly Include="System.Security" />
  </ItemGroup>
  ...
</Project>
```

<span data-ttu-id="99848-135">.NET 5,0 kullanıyorsanız, proje dosyasını aşağıdakileri içerecek şekilde güncelleştirebiliriz:</span><span class="sxs-lookup"><span data-stu-id="99848-135">If we're using .Net 5.0, we can update our project file to include the following:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk.Web">
 <PropertyGroup>...</PropertyGroup>
 <!--Include the following for .net 5.0-->
 <ItemGroup>
    <TrimmerRootAssembly Include="System.Net.Security" />
    <TrimmerRootAssembly Include="System.Security" />
  </ItemGroup>
  ...
</Project>
```

## <a name="trim-your-app---cli"></a><span data-ttu-id="99848-136">Uygulamanızı kırpın-CLı</span><span class="sxs-lookup"><span data-stu-id="99848-136">Trim your app - CLI</span></span>

<span data-ttu-id="99848-137">[DotNet Publish](../tools/dotnet-publish.md) komutunu kullanarak uygulamanızı kırpın.</span><span class="sxs-lookup"><span data-stu-id="99848-137">Trim your application using the [dotnet publish](../tools/dotnet-publish.md) command.</span></span> <span data-ttu-id="99848-138">Uygulamanızı yayımladığınızda, aşağıdaki özellikleri ayarlayın:</span><span class="sxs-lookup"><span data-stu-id="99848-138">When you publish your app, set the following properties:</span></span>

- <span data-ttu-id="99848-139">Belirli bir çalışma zamanı için kendi kendine kapsanan uygulama olarak yayımla: `-r win-x64`</span><span class="sxs-lookup"><span data-stu-id="99848-139">Publish as a self-contained app for a specific runtime: `-r win-x64`</span></span>
- <span data-ttu-id="99848-140">Kırpmayı etkinleştir: `/p:PublishTrimmed=true`</span><span class="sxs-lookup"><span data-stu-id="99848-140">Enable trimming: `/p:PublishTrimmed=true`</span></span>

<span data-ttu-id="99848-141">Aşağıdaki örnek, Windows için bir uygulamayı kendi içinde yayınlar ve çıktıyı kırpar.</span><span class="sxs-lookup"><span data-stu-id="99848-141">The following example publishes an app for Windows as self-contained and trims the output.</span></span>

```xml
<PropertyGroup>
    <RuntimeIdentifier>win-x64</RuntimeIdentifier>
    <PublishTrimmed>true</PublishTrimmed>
</PropertyGroup>
```

<span data-ttu-id="99848-142">Aşağıdaki örnek, derleme içinde kullanılmayan kodun kırpılıp kırpılmayabileceği, agresif kırpma modunda bir uygulama yayımlar.</span><span class="sxs-lookup"><span data-stu-id="99848-142">The following example publishes an app in the aggressive trim mode where unused code within assemblies will be trimmed and trimmer warnings enabled.</span></span>

```xml
<PropertyGroup>
    <RuntimeIdentifier>win-x64</RuntimeIdentifier>
    <PublishTrimmed>true</PublishTrimmed>
    <TrimMode>link</TrimMode>
    <SuppressTrimAnalysisWarnings>false</SuppressTrimAnalysisWarnings>
</PropertyGroup>
```

<span data-ttu-id="99848-143">Daha fazla bilgi için bkz. [.NET Core uygulamalarını .NET Core CLI yayımlama](deploy-with-cli.md).</span><span class="sxs-lookup"><span data-stu-id="99848-143">For more information, see [Publish .NET Core apps with .NET Core CLI](deploy-with-cli.md).</span></span>

## <a name="trim-your-app---visual-studio"></a><span data-ttu-id="99848-144">Uygulamanızı kırpın-Visual Studio</span><span class="sxs-lookup"><span data-stu-id="99848-144">Trim your app - Visual Studio</span></span>

<span data-ttu-id="99848-145">Visual Studio, uygulamanızın nasıl yayımlandığını denetleyen yeniden kullanılabilir yayımlama profilleri oluşturur.</span><span class="sxs-lookup"><span data-stu-id="99848-145">Visual Studio creates reusable publishing profiles that control how your application is published.</span></span>

01. <span data-ttu-id="99848-146">**Çözüm Gezgini** bölmesinde, yayımlamak istediğiniz projeye sağ tıklayın.</span><span class="sxs-lookup"><span data-stu-id="99848-146">On the **Solution Explorer** pane, right-click on the project you want to publish.</span></span> <span data-ttu-id="99848-147">Yayımla ' yı seçin.. **.**</span><span class="sxs-lookup"><span data-stu-id="99848-147">Select **Publish...**.</span></span>

    :::image type="content" source="media/trim-self-contained/visual-studio-solution-explorer.png" alt-text="Yayımla seçeneğini vurgulayan sağ tıklama menüsüyle Çözüm Gezgini.":::

    <span data-ttu-id="99848-149">Zaten bir yayımlama profiliniz yoksa, bir tane oluşturmak için yönergeleri izleyin ve hedef türü **klasörünü** seçin.</span><span class="sxs-lookup"><span data-stu-id="99848-149">If you don't already have a publishing profile, follow the instructions to create one and choose the **Folder** target-type.</span></span>

01. <span data-ttu-id="99848-150">**Düzenle**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="99848-150">Choose **Edit**.</span></span>

    :::image type="content" source="media/trim-self-contained/visual-studio-publish-edit-settings.png" alt-text="Visual Studio Profili Düzenle düğmesi ile Yayımla.":::

01. <span data-ttu-id="99848-152">**Profil ayarları** iletişim kutusunda, aşağıdaki seçenekleri ayarlayın:</span><span class="sxs-lookup"><span data-stu-id="99848-152">In the **Profile settings** dialog, set the following options:</span></span>

    - <span data-ttu-id="99848-153">**Dağıtım modunu** **kendi kendine dahil** olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="99848-153">Set **Deployment mode** to **Self-contained**.</span></span>
    - <span data-ttu-id="99848-154">**Hedef çalışma zamanını** , yayımlamak istediğiniz platforma ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="99848-154">Set **Target runtime** to the platform you want to publish to.</span></span>
    - <span data-ttu-id="99848-155">**Kullanılmayan derlemeleri Kırp (önizlemede)** seçeneğini belirleyin.</span><span class="sxs-lookup"><span data-stu-id="99848-155">Select **Trim unused assemblies (in preview)**.</span></span>

    <span data-ttu-id="99848-156">Ayarları kaydetmek ve **Yayımla** iletişim kutusuna dönmek için **Kaydet** ' i seçin.</span><span class="sxs-lookup"><span data-stu-id="99848-156">Choose **Save** to save the settings and return to the **Publish** dialog.</span></span>

    :::image type="content" source="media/trim-self-contained/visual-studio-publish-properties.png" alt-text="Dağıtım modu, hedef çalışma zamanı ve kullanılmayan derlemeleri Kırp seçeneklerinin vurgulandığı profil ayarları iletişim kutusu.":::

01. <span data-ttu-id="99848-158">Uygulamanızı yayımlamak için **Yayımla** ' yı seçin.</span><span class="sxs-lookup"><span data-stu-id="99848-158">Choose **Publish** to publish your app trimmed.</span></span>

<span data-ttu-id="99848-159">Daha fazla bilgi için bkz. [Visual Studio ile .NET Core uygulamalarını yayımlama](deploy-with-vs.md).</span><span class="sxs-lookup"><span data-stu-id="99848-159">For more information, see [Publish .NET Core apps with Visual Studio](deploy-with-vs.md).</span></span>

## <a name="trim-your-app---visual-studio-for-mac"></a><span data-ttu-id="99848-160">Uygulamanızı kırpın-Mac için Visual Studio</span><span class="sxs-lookup"><span data-stu-id="99848-160">Trim your app - Visual Studio for Mac</span></span>

<span data-ttu-id="99848-161">Mac için Visual Studio yayımlama sırasında uygulamanızı kırpmak için seçenek sağlamıyor.</span><span class="sxs-lookup"><span data-stu-id="99848-161">Visual Studio for Mac doesn't provide options to trim your app during publish.</span></span> <span data-ttu-id="99848-162">[Uygulamanızı Kırp-CLI](#trim-your-app---cli) bölümündeki yönergeleri izleyerek el ile yayımlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="99848-162">You'll need to publish manually by following the instructions from the [Trim your app - CLI](#trim-your-app---cli) section.</span></span> <span data-ttu-id="99848-163">Daha fazla bilgi için bkz. [.NET Core uygulamalarını .NET Core CLI yayımlama](deploy-with-cli.md).</span><span class="sxs-lookup"><span data-stu-id="99848-163">For more information, see [Publish .NET Core apps with .NET Core CLI](deploy-with-cli.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="99848-164">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="99848-164">See also</span></span>

- <span data-ttu-id="99848-165">[.NET Core uygulama dağıtımı](index.md).</span><span class="sxs-lookup"><span data-stu-id="99848-165">[.NET Core application deployment](index.md).</span></span>
- <span data-ttu-id="99848-166">[.NET Core uygulamalarını .NET Core CLI yayımlayın](deploy-with-cli.md).</span><span class="sxs-lookup"><span data-stu-id="99848-166">[Publish .NET Core apps with .NET Core CLI](deploy-with-cli.md).</span></span>
- <span data-ttu-id="99848-167">[Visual Studio ile .NET Core uygulamaları yayımlayın](deploy-with-vs.md).</span><span class="sxs-lookup"><span data-stu-id="99848-167">[Publish .NET Core apps with Visual Studio](deploy-with-vs.md).</span></span>
- <span data-ttu-id="99848-168">[DotNet Publish komutu](../tools/dotnet-publish.md).</span><span class="sxs-lookup"><span data-stu-id="99848-168">[dotnet publish command](../tools/dotnet-publish.md).</span></span>
