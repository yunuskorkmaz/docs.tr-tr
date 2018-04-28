---
title: .NET core uygulama dağıtımı
description: .NET Core uygulama dağıtma.
author: rpetrusha
ms.author: ronpet
ms.date: 04/18/2017
ms.topic: conceptual
ms.prod: dotnet-core
ms.devlang: dotnet
ms.workload:
- dotnetcore
ms.openlocfilehash: 5b8d49fd70b6e6b136a00aa0f7d7070bdd5a401a
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2018
---
# <a name="net-core-application-deployment"></a><span data-ttu-id="b2d18-103">.NET core uygulama dağıtımı</span><span class="sxs-lookup"><span data-stu-id="b2d18-103">.NET Core application deployment</span></span>

<span data-ttu-id="b2d18-104">Dağıtımları .NET Core uygulamaları için iki tür oluşturabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="b2d18-104">You can create two types of deployments for .NET Core applications:</span></span>

- <span data-ttu-id="b2d18-105">Framework bağımlı dağıtım.</span><span class="sxs-lookup"><span data-stu-id="b2d18-105">Framework-dependent deployment.</span></span> <span data-ttu-id="b2d18-106">Adından da anlaşılacağı gibi framework bağımlı dağıtım (FDD) .NET Core hedef sistemdeki bir paylaşılan sistem genelinde sürümünün varlığına bağımlıdır.</span><span class="sxs-lookup"><span data-stu-id="b2d18-106">As the name implies, framework-dependent deployment (FDD) relies on the presence of a shared system-wide version of .NET Core on the target system.</span></span> <span data-ttu-id="b2d18-107">.NET Core zaten mevcut olduğundan, uygulamanız da .NET Core yüklemeler arasında taşınabilir.</span><span class="sxs-lookup"><span data-stu-id="b2d18-107">Because .NET Core is already present, your app is also portable between installations of .NET Core.</span></span> <span data-ttu-id="b2d18-108">Uygulamanızı yalnızca kendi kodunu ve .NET Core kitaplıkları dışında olan üçüncü taraf bağımlılıkları içerir.</span><span class="sxs-lookup"><span data-stu-id="b2d18-108">Your app contains only its own code and any third-party dependencies that are outside of the .NET Core libraries.</span></span> <span data-ttu-id="b2d18-109">FDDs içeren *.dll* kullanarak başlatılabilir dosyaları [dotnet yardımcı programı](../tools/dotnet.md) komut satırından.</span><span class="sxs-lookup"><span data-stu-id="b2d18-109">FDDs contain *.dll* files that can be launched by using the [dotnet utility](../tools/dotnet.md) from the command line.</span></span> <span data-ttu-id="b2d18-110">Örneğin, `dotnet app.dll` adlı bir uygulamayı çalıştıran `app`.</span><span class="sxs-lookup"><span data-stu-id="b2d18-110">For example, `dotnet app.dll` runs an application named `app`.</span></span>

- <span data-ttu-id="b2d18-111">Kendi içinde bulunan dağıtım.</span><span class="sxs-lookup"><span data-stu-id="b2d18-111">Self-contained deployment.</span></span> <span data-ttu-id="b2d18-112">FDD farklı olarak, hedef sistemde paylaşılan bileşenler varlığına kendi içinde bulunan bir dağıtım (SCD) kullanmaz.</span><span class="sxs-lookup"><span data-stu-id="b2d18-112">Unlike FDD, a self-contained deployment (SCD) doesn't rely on the presence of shared components on the target system.</span></span> <span data-ttu-id="b2d18-113">.NET Core kitaplıkları ve .NET çekirdeği çalışma zamanı dahil olmak üzere tüm bileşenler uygulama ile birlikte ve diğer .NET Core uygulamalardan yalıtılır.</span><span class="sxs-lookup"><span data-stu-id="b2d18-113">All components, including both the .NET Core libraries and the .NET Core runtime, are included with the application and are isolated from other .NET Core applications.</span></span> <span data-ttu-id="b2d18-114">SCDs içeren bir yürütülebilir dosya (gibi *app.exe* adlı bir uygulama için Windows platformlarında `app`), platforma özgü .NET Core ana bilgisayar yeniden adlandırılmış bir sürümünü olduğu ve *.dll* (örneğin, dosya *app.dll*), gerçek uygulama olduğu.</span><span class="sxs-lookup"><span data-stu-id="b2d18-114">SCDs include an executable (such as *app.exe* on Windows platforms for an application named `app`), which is  a renamed version of the platform-specific .NET Core host, and a *.dll* file (such as *app.dll*), which is the actual application.</span></span>

## <a name="framework-dependent-deployments-fdd"></a><span data-ttu-id="b2d18-115">Framework bağımlı dağıtımları (FDD)</span><span class="sxs-lookup"><span data-stu-id="b2d18-115">Framework-dependent deployments (FDD)</span></span>

<span data-ttu-id="b2d18-116">Bir FDD için yalnızca uygulamanızı ve üçüncü taraf bağımlılıkları dağıtın.</span><span class="sxs-lookup"><span data-stu-id="b2d18-116">For an FDD, you deploy only your app and any third-party dependencies.</span></span> <span data-ttu-id="b2d18-117">Uygulamanızı hedef sistemde mevcut .NET Core sürümünü kullanacak beri .NET Core dağıtmak zorunda değilsiniz.</span><span class="sxs-lookup"><span data-stu-id="b2d18-117">You don't have to deploy .NET Core, since your app will use the version of .NET Core that's present on the target system.</span></span> <span data-ttu-id="b2d18-118">.NET Core uygulamaları için varsayılan dağıtım modeli budur.</span><span class="sxs-lookup"><span data-stu-id="b2d18-118">This is the default deployment model for .NET Core apps.</span></span>

### <a name="why-create-a-framework-dependent-deployment"></a><span data-ttu-id="b2d18-119">Neden framework bağımlı dağıtım oluşturulsun mu?</span><span class="sxs-lookup"><span data-stu-id="b2d18-119">Why create a framework-dependent deployment?</span></span>

<span data-ttu-id="b2d18-120">Bir FDD dağıtma, çok sayıda avantaj vardır:</span><span class="sxs-lookup"><span data-stu-id="b2d18-120">Deploying an FDD has a number of advantages:</span></span>

- <span data-ttu-id="b2d18-121">.NET Core uygulamanızı önceden çalışacak hedef işletim sistemleri tanımlamanız gerekmez.</span><span class="sxs-lookup"><span data-stu-id="b2d18-121">You don't have to define the target operating systems that your .NET Core app will run on in advance.</span></span> <span data-ttu-id="b2d18-122">.NET Core yürütülebilir dosyaları ve kitaplıkları bakılmaksızın işletim sistemi için ortak bir PE dosya biçimi kullandığından, .NET Core uygulamanızı temel işletim sistemini bağımsız olarak çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b2d18-122">Because .NET Core uses a common PE file format for executables and libraries regardless of operating system, .NET Core can execute your app regardless of the underlying operating system.</span></span> <span data-ttu-id="b2d18-123">PE dosya biçimi hakkında daha fazla bilgi için bkz: [.NET derleme dosyası biçimi](../../standard/assembly-format.md).</span><span class="sxs-lookup"><span data-stu-id="b2d18-123">For more information on the PE file format, see [.NET Assembly File Format](../../standard/assembly-format.md).</span></span>

- <span data-ttu-id="b2d18-124">Dağıtım paketi boyutu küçüktür.</span><span class="sxs-lookup"><span data-stu-id="b2d18-124">The size of your deployment package is small.</span></span> <span data-ttu-id="b2d18-125">Yalnızca uygulamanızı ve bağımlılıklarını, .NET Core kendisini dağıttığınız.</span><span class="sxs-lookup"><span data-stu-id="b2d18-125">You only deploy your app and its dependencies, not .NET Core itself.</span></span>

- <span data-ttu-id="b2d18-126">Birden fazla uygulama ana bilgisayar sistemlerinde her iki disk alanı ve bellek kullanımını azaltır aynı .NET Core yüklemesi kullanın.</span><span class="sxs-lookup"><span data-stu-id="b2d18-126">Multiple apps use the same .NET Core installation, which reduces both disk space and memory usage on host systems.</span></span>

<span data-ttu-id="b2d18-127">Birkaç dezavantajları vardır:</span><span class="sxs-lookup"><span data-stu-id="b2d18-127">There are also a few disadvantages:</span></span>

- <span data-ttu-id="b2d18-128">Yalnızca hedef .NET Core sürümü veya sonraki bir sürümü zaten ana bilgisayar sisteminde yüklü değilse, uygulamanızın çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b2d18-128">Your app can run only if the version of .NET Core that you target, or a later version, is already installed on the host system.</span></span>

- <span data-ttu-id="b2d18-129">.NET çekirdeği çalışma zamanı ve bilginiz gelecekteki Sunumlarda olmadan değiştirmek için kitaplıklar için mümkündür.</span><span class="sxs-lookup"><span data-stu-id="b2d18-129">It's possible for the .NET Core runtime and libraries to change without your knowledge in future releases.</span></span> <span data-ttu-id="b2d18-130">Nadir durumlarda bu, uygulamanızın davranışını değiştirebilir.</span><span class="sxs-lookup"><span data-stu-id="b2d18-130">In rare cases, this may change the behavior of your app.</span></span>

## <a name="self-contained-deployments-scd"></a><span data-ttu-id="b2d18-131">Kendi içinde bulunan dağıtımları (SCD)</span><span class="sxs-lookup"><span data-stu-id="b2d18-131">Self-contained deployments (SCD)</span></span>

<span data-ttu-id="b2d18-132">Kendi içinde bulunan bir dağıtım için uygulamanızı ve uygulama oluşturmak için kullanılan .NET Core sürümü ile birlikte gerekli üçüncü taraf bağımlılıkları dağıtın.</span><span class="sxs-lookup"><span data-stu-id="b2d18-132">For a self-contained deployment, you deploy your app and any required third-party dependencies along with the version of .NET Core that you used to build the app.</span></span> <span data-ttu-id="b2d18-133">Bir SCD oluşturma içermez [.NET Core yerel bağımlılıkları](https://github.com/dotnet/core/blob/master/Documentation/prereqs.md) çeşitli platformlarda, bu nedenle bu uygulama çalışmadan önce mevcut olmalı.</span><span class="sxs-lookup"><span data-stu-id="b2d18-133">Creating an SCD doesn't include the [native dependencies of .NET Core](https://github.com/dotnet/core/blob/master/Documentation/prereqs.md) on various platforms, so these must be present before the app runs.</span></span>

<span data-ttu-id="b2d18-134">Yayımcı imza ile yürütülebilir bir ana bilgisayar için bir SCD oturum şekilde FDD ve SCD dağıtımları ayrı konak yürütülebilir dosyaları, kullanın.</span><span class="sxs-lookup"><span data-stu-id="b2d18-134">FDD and SCD deployments use separate host executables, so you can sign a host executable for an SCD with your publisher signature.</span></span>

### <a name="why-deploy-a-self-contained-deployment"></a><span data-ttu-id="b2d18-135">Neden bir müstakil dağıtım?</span><span class="sxs-lookup"><span data-stu-id="b2d18-135">Why deploy a self-contained deployment?</span></span>

<span data-ttu-id="b2d18-136">Kendi içinde bulunan bir dağıtım dağıtma iki ana avantajları vardır:</span><span class="sxs-lookup"><span data-stu-id="b2d18-136">Deploying a Self-contained deployment has two major advantages:</span></span>

- <span data-ttu-id="b2d18-137">Uygulamanız ile dağıtılan .NET Core sürümü tek denetime sahiptir.</span><span class="sxs-lookup"><span data-stu-id="b2d18-137">You have sole control of the version of .NET Core that is deployed with your app.</span></span> <span data-ttu-id="b2d18-138">.NET core yalnızca sizin tarafınızdan hizmet verebilir.</span><span class="sxs-lookup"><span data-stu-id="b2d18-138">.NET Core can be serviced only by you.</span></span>

- <span data-ttu-id="b2d18-139">Üzerinde çalışacağı .NET Core sürümü sağlama hedef sistem .NET Core uygulamanızı çalışabilir emin olabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b2d18-139">You can be assured that the target system can run your .NET Core app, since you're providing the version of .NET Core that it will run on.</span></span>

<span data-ttu-id="b2d18-140">Ayrıca, bir dizi dezavantajları vardır:</span><span class="sxs-lookup"><span data-stu-id="b2d18-140">It also has a number of disadvantages:</span></span>

- <span data-ttu-id="b2d18-141">.NET Core dağıtım paketinde yer aldığından, kendisi için dağıtım paketleri önceden oluşturduğunuz hedef platformlar seçmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="b2d18-141">Because .NET Core is included in your deployment package, you must select the target platforms for which you build deployment packages in advance.</span></span>

- <span data-ttu-id="b2d18-142">.NET Core yanı sıra, uygulamanızı ve üçüncü taraf bağımlılıkları içerecek şekilde sahip olduğundan, dağıtım paketi görece büyük boyutudur.</span><span class="sxs-lookup"><span data-stu-id="b2d18-142">The size of your deployment package is relatively large, since you have to include .NET Core as well as your app and its third-party dependencies.</span></span>

- <span data-ttu-id="b2d18-143">Çok sayıda müstakil .NET Core uygulamaları bir sisteme dağıtmaya önemli miktarda disk alanı, her uygulama çoğaltmaları .NET Core dosyaları bu yana kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="b2d18-143">Deploying numerous self-contained .NET Core apps to a system can consume significant amounts of disk space, since each app duplicates .NET Core files.</span></span>

## <a name="step-by-step-examples"></a><span data-ttu-id="b2d18-144">Adım adım örnekler</span><span class="sxs-lookup"><span data-stu-id="b2d18-144">Step-by-step examples</span></span>

<span data-ttu-id="b2d18-145">CLI araçlarını ile .NET Core uygulamaları dağıtma hakkında adım adım örnekler için bkz [CLI araçlarını ile .NET Core uygulamaları dağıtma](deploy-with-cli.md).</span><span class="sxs-lookup"><span data-stu-id="b2d18-145">For step-by-step examples of deploying .NET Core apps with CLI tools, see [Deploying .NET Core Apps with CLI Tools](deploy-with-cli.md).</span></span> <span data-ttu-id="b2d18-146">Visual Studio ile .NET Core uygulamaları dağıtma hakkında adım adım örnekler için bkz [Visual Studio ile .NET Core uygulamaları dağıtma](deploy-with-vs.md).</span><span class="sxs-lookup"><span data-stu-id="b2d18-146">For step-by-step examples of deploying .NET Core apps with Visual Studio, see [Deploying .NET Core Apps with Visual Studio](deploy-with-vs.md).</span></span> <span data-ttu-id="b2d18-147">Her konunun aşağıdaki dağıtımları örnekleri içerir:</span><span class="sxs-lookup"><span data-stu-id="b2d18-147">Each topic includes examples of the following deployments:</span></span>

- <span data-ttu-id="b2d18-148">Framework bağımlı dağıtım</span><span class="sxs-lookup"><span data-stu-id="b2d18-148">Framework-dependent deployment</span></span>
- <span data-ttu-id="b2d18-149">Üçüncü taraf bağımlılıkları Framework bağımlı dağıtım</span><span class="sxs-lookup"><span data-stu-id="b2d18-149">Framework-dependent deployment with third-party dependencies</span></span>
- <span data-ttu-id="b2d18-150">Kendi içinde bulunan dağıtım</span><span class="sxs-lookup"><span data-stu-id="b2d18-150">Self-contained deployment</span></span>
- <span data-ttu-id="b2d18-151">Üçüncü taraf bağımlılıkları kendi içinde bulunan dağıtım</span><span class="sxs-lookup"><span data-stu-id="b2d18-151">Self-contained deployment with third-party dependencies</span></span>

# <a name="see-also"></a><span data-ttu-id="b2d18-152">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b2d18-152">See also</span></span>

<span data-ttu-id="b2d18-153">[CLI araçlarını ile .NET Core uygulamaları dağıtma](deploy-with-cli.md) </span><span class="sxs-lookup"><span data-stu-id="b2d18-153">[Deploying .NET Core Apps with CLI Tools](deploy-with-cli.md) </span></span>  
<span data-ttu-id="b2d18-154">[Visual Studio ile .NET Core uygulamaları dağıtma](deploy-with-vs.md) </span><span class="sxs-lookup"><span data-stu-id="b2d18-154">[Deploying .NET Core Apps with Visual Studio](deploy-with-vs.md) </span></span>  
<span data-ttu-id="b2d18-155">[Paketler, Metapackages ve çerçeveleri](../packages.md) </span><span class="sxs-lookup"><span data-stu-id="b2d18-155">[Packages, Metapackages and Frameworks](../packages.md) </span></span>  
[<span data-ttu-id="b2d18-156">.NET çekirdeği çalışma zamanı tanımlayıcı (RID) Kataloğu</span><span class="sxs-lookup"><span data-stu-id="b2d18-156">.NET Core Runtime IDentifier (RID) catalog</span></span>](../rid-catalog.md)
