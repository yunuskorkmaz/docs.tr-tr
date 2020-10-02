---
title: ReadyToRun dağıtımına genel bakış
description: .NET 5 ve .NET Core 3,0 ve üzeri ile uygulamanızı yayımlamalarından bir parçası olarak, ReadyToRun dağıtımlarının ne olduğunu ve bu uygulamayı kullanmayı düşünmek zorunda olduğunu öğrenin.
author: davidwr
ms.author: davidwr
ms.date: 09/21/2020
ms.openlocfilehash: b4052a0c0f4ed9f6cfd273abe5ef45d018bd0ae0
ms.sourcegitcommit: 4d45bda8cd9558ea8af4be591e3d5a29360c1ece
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/02/2020
ms.locfileid: "91654965"
---
# <a name="readytorun-compilation"></a><span data-ttu-id="d18f4-103">ReadyToRun derlemesi</span><span class="sxs-lookup"><span data-stu-id="d18f4-103">ReadyToRun Compilation</span></span>

<span data-ttu-id="d18f4-104">.NET uygulama başlangıç süresi ve gecikme süresi, uygulama derlemeleriniz ReadyToRun (R2R) biçimi olarak derlenerek artırılabilir.</span><span class="sxs-lookup"><span data-stu-id="d18f4-104">.NET application startup time and latency can be improved by compiling your application assemblies as ReadyToRun (R2R) format.</span></span> <span data-ttu-id="d18f4-105">R2R, bir süre öncesi (AOT) derleme biçimidir.</span><span class="sxs-lookup"><span data-stu-id="d18f4-105">R2R is a form of ahead-of-time (AOT) compilation.</span></span>

<span data-ttu-id="d18f4-106">R2R ikilileri, tam zamanında (JıT) derleyicisinin uygulamanız yüklenirken yapması gereken iş miktarını azaltarak başlangıç performansını geliştirir.</span><span class="sxs-lookup"><span data-stu-id="d18f4-106">R2R binaries improve startup performance by reducing the amount of work the just-in-time (JIT) compiler needs to do as your application loads.</span></span> <span data-ttu-id="d18f4-107">İkililer, JıT 'in üretmesine kıyasla benzer yerel kod içerir.</span><span class="sxs-lookup"><span data-stu-id="d18f4-107">The binaries contain similar native code compared to what the JIT would produce.</span></span> <span data-ttu-id="d18f4-108">Ancak, R2R ikilileri, bazı senaryolar için hala gerekli olan hem ara dil (IL) kodunu hem de aynı kodun yerel sürümünü içerdiğinden, daha büyüktür.</span><span class="sxs-lookup"><span data-stu-id="d18f4-108">However, R2R binaries are larger because they contain both intermediate language (IL) code, which is still needed for some scenarios, and the native version of the same code.</span></span> <span data-ttu-id="d18f4-109">R2R yalnızca Linux x64 veya Windows x64 gibi belirli çalışma zamanı ortamlarını (RID) hedefleyen bir uygulama yayımladığınızda kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="d18f4-109">R2R is only available when you publish an app that targets specific runtime environments (RID) such as Linux x64 or Windows x64.</span></span>

<span data-ttu-id="d18f4-110">Projenizi ReadyToRun olarak derlemek için, uygulamanın PublishReadyToRun özelliği true olarak ayarlanmış şekilde yayımlanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="d18f4-110">To compile your project as ReadyToRun, the application must be published with the PublishReadyToRun property set to true.</span></span>

<span data-ttu-id="d18f4-111">Uygulamanızı ReadyToRun olarak yayımlamanın iki yolu vardır:</span><span class="sxs-lookup"><span data-stu-id="d18f4-111">There are two ways to publish your app as ReadyToRun:</span></span>

01. <span data-ttu-id="d18f4-112">PublishReadyToRun bayrağını doğrudan dotnet publish komutuna belirtin.</span><span class="sxs-lookup"><span data-stu-id="d18f4-112">Specify the PublishReadyToRun flag directly to the dotnet publish command.</span></span> <span data-ttu-id="d18f4-113">Ayrıntılar için [DotNet Publish](../tools/dotnet-publish.md) bakın.</span><span class="sxs-lookup"><span data-stu-id="d18f4-113">See [dotnet publish](../tools/dotnet-publish.md) for details.</span></span>

    ```dotnetcli
    dotnet publish -c Release -r win-x64 -p:PublishReadyToRun=true
    ```

02. <span data-ttu-id="d18f4-114">Projede özelliği belirtin</span><span class="sxs-lookup"><span data-stu-id="d18f4-114">Specify the property in the project</span></span>

    - <span data-ttu-id="d18f4-115">`<PublishReadyToRun>`Ayarı projenize ekleyin.</span><span class="sxs-lookup"><span data-stu-id="d18f4-115">Add the `<PublishReadyToRun>` setting to your project.</span></span>

    ```xml
    <PropertyGroup>
      <PublishReadyToRun>true</PublishReadyToRun>
    </PropertyGroup>
    ```

    - <span data-ttu-id="d18f4-116">Uygulamayı özel parametre olmadan yayımlayın.</span><span class="sxs-lookup"><span data-stu-id="d18f4-116">Publish the application without any special parameters.</span></span>

    ```dotnetcli
    dotnet publish -c Release -r win-x64
    ```

## <a name="impact-of-using-the-readytorun-feature"></a><span data-ttu-id="d18f4-117">ReadyToRun özelliğini kullanmanın etkileri</span><span class="sxs-lookup"><span data-stu-id="d18f4-117">Impact of using the ReadyToRun feature</span></span>

<span data-ttu-id="d18f4-118">Güncel derleme, uygulama performansı üzerinde karmaşık performans etkilerine sahiptir ve tahmin edilmesi zor olabilir.</span><span class="sxs-lookup"><span data-stu-id="d18f4-118">Ahead-of-time compilation has complex performance impact on application performance, which may be difficult to predict.</span></span> <span data-ttu-id="d18f4-119">Genel olarak, bir derlemenin boyutu iki ila üç kat daha büyük olacak şekilde artar.</span><span class="sxs-lookup"><span data-stu-id="d18f4-119">In general, the size of an assembly will grow to between two to three times larger.</span></span> <span data-ttu-id="d18f4-120">Dosyanın fiziksel boyutundaki bu artış, derlemeyi diskten yükleme performansını azaltabilir ve işlemin çalışma kümesini artırabilir.</span><span class="sxs-lookup"><span data-stu-id="d18f4-120">This increase in the physical size of the file may reduce the performance of loading the assembly from disk, and increase working set of the process.</span></span> <span data-ttu-id="d18f4-121">Ancak, dönüş sırasında çalışma zamanında derlenen yöntemlerin sayısı genellikle önemli ölçüde azaltılır.</span><span class="sxs-lookup"><span data-stu-id="d18f4-121">However, in return the number of methods compiled at runtime is typically reduced substantially.</span></span> <span data-ttu-id="d18f4-122">Sonuç olarak, büyük miktarlarda kod kullanan uygulamaların, ReadyToRun 'ı etkinleştirmesinin büyük performans avantajları elde edilmesine neden olur.</span><span class="sxs-lookup"><span data-stu-id="d18f4-122">The result is that most applications that large amounts of code receive large performance benefits from enabling ReadyToRun.</span></span> <span data-ttu-id="d18f4-123">.NET çalışma zamanı kitaplıkları zaten ReadyToRun ile önceden derlenmiş olduğundan, az miktarda koda sahip uygulamalar, ReadyToRun 'ı etkinleştirmenin önemli bir geliştirmesini yaşmaz.</span><span class="sxs-lookup"><span data-stu-id="d18f4-123">Applications, which have small amounts of code will likely not experience a significant improvement from enabling ReadyToRun, as the .NET runtime libraries have already been precompiled with ReadyToRun.</span></span>

<span data-ttu-id="d18f4-124">Burada açıklanan başlangıç geliştirmesi yalnızca uygulama başlatma için değil, aynı zamanda uygulamadaki herhangi bir kodun ilk kullanımı için de geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="d18f4-124">The startup improvement discussed here applies not only to application startup, but also to the first use of any code in the application.</span></span> <span data-ttu-id="d18f4-125">Örneğin, ReadyToRun, bir ASP.NET uygulamasında Web API 'sinin ilk kullanımı için yanıt gecikmesini azaltmak üzere kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="d18f4-125">For instance, ReadyToRun can be used to reduce the response latency of the first use  of Web API in an ASP.NET application.</span></span>

### <a name="interaction-with-tiered-compilation"></a><span data-ttu-id="d18f4-126">Katmanlı derleme ile etkileşim</span><span class="sxs-lookup"><span data-stu-id="d18f4-126">Interaction with tiered compilation</span></span>

<span data-ttu-id="d18f4-127">Oluşturulma Zamanı, JıT tarafından üretilen kod olarak en iyi duruma getirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="d18f4-127">Ahead-of-time generated is not as highly optimized as code produced by the JIT.</span></span> <span data-ttu-id="d18f4-128">Bu sorunu gidermek için katmanlı derleme yaygın olarak kullanılan ReadyToRun yöntemlerini JıT tarafından oluşturulan yöntemlerle değiştirecektir.</span><span class="sxs-lookup"><span data-stu-id="d18f4-128">To address this issue, tiered compilation will replace commonly used ReadyToRun methods with JIT-generated methods.</span></span>

## <a name="how-is-the-set-of-precompiled-assemblies-chosen"></a><span data-ttu-id="d18f4-129">Önceden derlenmiş derlemeler kümesi nasıl seçilir?</span><span class="sxs-lookup"><span data-stu-id="d18f4-129">How is the set of precompiled assemblies chosen?</span></span>

<span data-ttu-id="d18f4-130">SDK, uygulamayla dağıtılan derlemeleri önceden derler.</span><span class="sxs-lookup"><span data-stu-id="d18f4-130">The SDK will precompile the assemblies that are distributed with the application.</span></span> <span data-ttu-id="d18f4-131">Kendi içinde bulunan uygulamalar için, bu derleme kümesi Framework 'ü içerir.</span><span class="sxs-lookup"><span data-stu-id="d18f4-131">For self-contained applications, this set of assemblies will include the framework.</span></span> <span data-ttu-id="d18f4-132">C++/CLı ikilileri, ReadyToRun derlemesi için uygun değildir.</span><span class="sxs-lookup"><span data-stu-id="d18f4-132">C++/CLI binaries are not eligible for ReadyToRun compilation.</span></span>

## <a name="how-is-the-set-of-methods-to-precompile-chosen"></a><span data-ttu-id="d18f4-133">Nasıl önceden derlenecek yöntemler kümesi seçildi?</span><span class="sxs-lookup"><span data-stu-id="d18f4-133">How is the set of methods to precompile chosen?</span></span>

<span data-ttu-id="d18f4-134">Derleyici, mümkün olduğunca çok metodu önceden derlemeye çalışır.</span><span class="sxs-lookup"><span data-stu-id="d18f4-134">The compiler will attempt to pre-compile as many methods as it can.</span></span> <span data-ttu-id="d18f4-135">Ancak, ReadyToRun özelliğinin kullanılması beklenmediğinden, JıT 'in yürütülmesini engellemesine neden olur.</span><span class="sxs-lookup"><span data-stu-id="d18f4-135">However various reasons it is not expected that using the ReadyToRun feature will result in preventing the JIT from executing.</span></span>

<span data-ttu-id="d18f4-136">Bu nedenlerden bazıları şunlar olabilir ancak bunlarla sınırlı değildir:</span><span class="sxs-lookup"><span data-stu-id="d18f4-136">Such reasons may include, but are not limited to:</span></span>

- <span data-ttu-id="d18f4-137">Ayrı derlemelerde tanımlanmış genel türlerin kullanımı</span><span class="sxs-lookup"><span data-stu-id="d18f4-137">Use of generic types defined in separate assemblies</span></span>
- <span data-ttu-id="d18f4-138">Yerel kodla birlikte çalışma</span><span class="sxs-lookup"><span data-stu-id="d18f4-138">Interop with native code</span></span>
- <span data-ttu-id="d18f4-139">Derleyicinin bir hedef makinede kullanımı kanıtlayamadığını donanım iç bilgileri kullanımı</span><span class="sxs-lookup"><span data-stu-id="d18f4-139">Use of hardware intrinsics that the compiler cannot prove are safe to use on a target machine</span></span>
- <span data-ttu-id="d18f4-140">Belirli olağandışı Il desenleri</span><span class="sxs-lookup"><span data-stu-id="d18f4-140">Certain unusual IL patterns</span></span>
- <span data-ttu-id="d18f4-141">Yansıma veya LINQ aracılığıyla dinamik yöntem oluşturma</span><span class="sxs-lookup"><span data-stu-id="d18f4-141">Dynamic method creation via reflection, or LINQ</span></span>

## <a name="cross-platformarchitecture-restrictions"></a><span data-ttu-id="d18f4-142">Platformlar arası/mimari kısıtlamaları</span><span class="sxs-lookup"><span data-stu-id="d18f4-142">Cross platform/architecture restrictions</span></span>

<span data-ttu-id="d18f4-143">Bazı SDK platformları için, ReadyToRun derleyicisi diğer hedef platformlar için çapraz derlenebilecek bir derlemedir.</span><span class="sxs-lookup"><span data-stu-id="d18f4-143">For some SDK platforms, the ReadyToRun compiler is capable of cross-compiling for other target platforms.</span></span> <span data-ttu-id="d18f4-144">Desteklenen derleme hedefleri aşağıdaki tabloda açıklanmıştır.</span><span class="sxs-lookup"><span data-stu-id="d18f4-144">Supported compilation targets are described in the table below.</span></span>

| <span data-ttu-id="d18f4-145">SDK Platformu</span><span class="sxs-lookup"><span data-stu-id="d18f4-145">SDK platform</span></span> | <span data-ttu-id="d18f4-146">Desteklenen hedef platformlar</span><span class="sxs-lookup"><span data-stu-id="d18f4-146">Supported target platforms</span></span> |
| ------------ | --------------------------- |
| <span data-ttu-id="d18f4-147">Windows X64</span><span class="sxs-lookup"><span data-stu-id="d18f4-147">Windows X64</span></span>  | <span data-ttu-id="d18f4-148">Windows x86, Windows x64, Windows ARM32, Windows ARM64</span><span class="sxs-lookup"><span data-stu-id="d18f4-148">Windows X86, Windows X64, Windows ARM32, Windows ARM64</span></span> |
| <span data-ttu-id="d18f4-149">Windows x86</span><span class="sxs-lookup"><span data-stu-id="d18f4-149">Windows X86</span></span>  | <span data-ttu-id="d18f4-150">Windows x86, Windows ARM32</span><span class="sxs-lookup"><span data-stu-id="d18f4-150">Windows X86, Windows ARM32</span></span> |
| <span data-ttu-id="d18f4-151">Linux X64</span><span class="sxs-lookup"><span data-stu-id="d18f4-151">Linux X64</span></span>    | <span data-ttu-id="d18f4-152">Linux x86, Linux x64, Linux ARM32, Linux ARM64</span><span class="sxs-lookup"><span data-stu-id="d18f4-152">Linux X86, Linux X64, Linux ARM32, Linux ARM64</span></span> |
| <span data-ttu-id="d18f4-153">Linux ARM32</span><span class="sxs-lookup"><span data-stu-id="d18f4-153">Linux ARM32</span></span>  | <span data-ttu-id="d18f4-154">Linux ARM32</span><span class="sxs-lookup"><span data-stu-id="d18f4-154">Linux ARM32</span></span> |
| <span data-ttu-id="d18f4-155">Linux ARM64</span><span class="sxs-lookup"><span data-stu-id="d18f4-155">Linux ARM64</span></span>  | <span data-ttu-id="d18f4-156">Linux ARM64</span><span class="sxs-lookup"><span data-stu-id="d18f4-156">Linux ARM64</span></span> |
| <span data-ttu-id="d18f4-157">macOS x64</span><span class="sxs-lookup"><span data-stu-id="d18f4-157">macOS X64</span></span>    | <span data-ttu-id="d18f4-158">macOS x64</span><span class="sxs-lookup"><span data-stu-id="d18f4-158">macOS X64</span></span> |
