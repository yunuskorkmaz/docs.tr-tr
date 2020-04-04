---
title: Kendi kendine yeten uygulamaları kırpma
description: Boyutlarını azaltmak için bağımsız uygulamaları nasıl kırptığınızı öğrenin. .NET Core, çalışma süresini kendi kendine çalışan bir uygulamayla paketler ve genellikle çalışma süresinin daha fazlasını içerir ve o zaman gereklidir.
author: jamshedd
ms.author: jamshedd
ms.date: 01/23/2020
ms.openlocfilehash: 5206ca255c500b382402ac4e7dd3300b7face1cf
ms.sourcegitcommit: 45cced471d59d5dac3f0c92abc9d4849716098a2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/04/2020
ms.locfileid: "80665637"
---
# <a name="trim-self-contained-deployments-and-executables"></a><span data-ttu-id="87618-104">Bağımsız dağıtımları ve çalıştırılabilir leri kırpın</span><span class="sxs-lookup"><span data-stu-id="87618-104">Trim self-contained deployments and executables</span></span>

<span data-ttu-id="87618-105">Bir uygulama bağımsız yayımlanırken,.NET Core çalışma süresi uygulamayla birlikte paketlenir.</span><span class="sxs-lookup"><span data-stu-id="87618-105">When publishing an application self-contained, the .NET Core runtime is bundled together with the application.</span></span> <span data-ttu-id="87618-106">Bu birleştirme, paket uygulamanıza önemli miktarda içerik ekler.</span><span class="sxs-lookup"><span data-stu-id="87618-106">This bundling adds a significant amount of content to your packaged application.</span></span>

<span data-ttu-id="87618-107">Uygulamanızı dağıtma söz konusu olduğunda, boyut genellikle önemli bir faktördür.</span><span class="sxs-lookup"><span data-stu-id="87618-107">When it comes to deploying your application, size is often an important factor.</span></span> <span data-ttu-id="87618-108">Paket uygulamasının boyutunu mümkün olduğunca küçük tutmak genellikle uygulama geliştiricileri için bir hedeftir.</span><span class="sxs-lookup"><span data-stu-id="87618-108">Keeping the size of the package application as small as possible is typically a goal for application developers.</span></span>

<span data-ttu-id="87618-109">Uygulamanın karmaşıklığına bağlı olarak, uygulamayı çalıştırmak için yalnızca çalışma zamanının bir alt kümesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="87618-109">Depending on the complexity of the application, only a subset of the runtime is required to run the application.</span></span> <span data-ttu-id="87618-110">Çalışma zamanının bu kullanılmayan bölümleri gereksizdir ve paket uygulamadan kesilebilir.</span><span class="sxs-lookup"><span data-stu-id="87618-110">These unused parts of the runtime are unnecessary and can be trimmed from the packaged application.</span></span>

> [!NOTE]
> <span data-ttu-id="87618-111">Kırpma ,NET Core 3.1'de deneysel bir özelliktir ve _yalnızca_ bağımsız olarak yayınlanan uygulamalar için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="87618-111">Trimming is an experimental feature in .NET Core 3.1 and is _only_ available to applications that are published self-contained.</span></span>

## <a name="trim-your-application"></a><span data-ttu-id="87618-112">Başvurunuzu kırpın</span><span class="sxs-lookup"><span data-stu-id="87618-112">Trim your application</span></span>

<span data-ttu-id="87618-113">Aşağıdaki örnek, [dotnet yayımlama](../tools/dotnet-publish.md) komutunu kullanarak uygulamanızın nasıl kırpılabildiğini gösterir:</span><span class="sxs-lookup"><span data-stu-id="87618-113">The following example shows how to trim your application using the [dotnet publish](../tools/dotnet-publish.md) command:</span></span>

```dotnetcli
dotnet publish -c Release -r win10-x64 --self-contained true /p:PublishSingleFile=false /p:PublishTrimmed=true
```

<span data-ttu-id="87618-114">Kırpma özelliği, gerekli çalışma zamanı derlemelerinin bir grafiğini keşfetmek ve oluşturmak için uygulama ikililerini inceleyerek çalışır.</span><span class="sxs-lookup"><span data-stu-id="87618-114">The trimming feature works by examining the application binaries to discover and build a graph of the required runtime assemblies.</span></span> <span data-ttu-id="87618-115">Başvurulamayan kalan çalışma zamanı derlemeleri kırpılır.</span><span class="sxs-lookup"><span data-stu-id="87618-115">The remaining runtime assemblies that aren't referenced are trimmed.</span></span>

## <a name="trimming-issues-when-using-reflection"></a><span data-ttu-id="87618-116">Yansıma kullanırken sorunları kırpma</span><span class="sxs-lookup"><span data-stu-id="87618-116">Trimming issues when using reflection</span></span>

<span data-ttu-id="87618-117">Kırpma işlevinin başvuruları algılayamadığı senaryolar vardır.</span><span class="sxs-lookup"><span data-stu-id="87618-117">There are scenarios in which the trimming functionality will fail to detect references.</span></span> <span data-ttu-id="87618-118">Örneğin, yansıma kullanan bir uygulama bu sorunla ilgili olarak, derlemeye bağımlılık yalnızca çalışma zamanında bilinecektir.</span><span class="sxs-lookup"><span data-stu-id="87618-118">For example, an application that uses reflection could run into this issue because the dependency on the assembly will only be known at run time.</span></span>

<span data-ttu-id="87618-119">Kırpma yalnızca yansıma kullanımı doğrudan başvurulamayan bir çalışma zamanı derlemesi bağlıysa bir sorundur.</span><span class="sxs-lookup"><span data-stu-id="87618-119">Trimming is only a problem if the reflection usage depends on a runtime assembly that isn't referenced directly.</span></span> <span data-ttu-id="87618-120">Uygulama kodunuzu doğrudan yansıtma yı kullanmıyor olabilir, ancak başvuruda bulunduğunuz üçüncü taraf derlemenin bu kodu kullandığını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="87618-120">Keep in mind that your application code may not be using reflection directly, but a third-party assembly you're referencing may be using it.</span></span>

<span data-ttu-id="87618-121">Kod bir API'ye yansıma yoluyla başvuruyorsa ve bağlayıcının bu API'yi içeren derlemeyi kırpmasını istemiyorsanız, proje dosyanızı derlemeyi kırpma işleminden hariç tutmak için değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="87618-121">When the code is referencing an API through reflection and you don't want the linker to trim the assembly that contains that API, you can modify your project file to exclude the assembly from the trimming process.</span></span> <span data-ttu-id="87618-122">Aşağıdaki örnek, çağrılan `System.Security` bir derlemenin nasıl kırpılmasının önlenişretedildiğini gösterir:</span><span class="sxs-lookup"><span data-stu-id="87618-122">The following example shows how to prevent an assembly called `System.Security` from being trimmed:</span></span>

```xml
<ItemGroup>
    <TrimmerRootAssembly Include="System.Security" />
</ItemGroup>
```

## <a name="see-also"></a><span data-ttu-id="87618-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="87618-123">See also</span></span>

- [<span data-ttu-id="87618-124">.NET Core uygulama dağıtımı</span><span class="sxs-lookup"><span data-stu-id="87618-124">.NET Core application deployment</span></span>](index.md)
