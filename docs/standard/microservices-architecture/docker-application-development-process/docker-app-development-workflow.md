---
title: Docker uygulamalar için geliştirme iş akışı
description: Kapsayıcılı .NET uygulamaları için .NET mikro mimarisi | Docker uygulamalar için geliştirme iş akışı
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/18/2017
ms.openlocfilehash: 2e29e88a104050230b7816da6793120d61de7bc6
ms.sourcegitcommit: c217b067985905cb21eafc5dd9a83568d7ff4e45
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/22/2018
ms.locfileid: "36314958"
---
# <a name="development-workflow-for-docker-apps"></a><span data-ttu-id="c5756-103">Docker uygulamalar için geliştirme iş akışı</span><span class="sxs-lookup"><span data-stu-id="c5756-103">Development workflow for Docker apps</span></span>

<span data-ttu-id="c5756-104">Burada Geliştirici tercih edilen dillerini kullanarak uygulama kodları ve yerel olarak test her geliştiricinin makinenin, uygulama geliştirme yaşam döngüsü başlatır.</span><span class="sxs-lookup"><span data-stu-id="c5756-104">The application development lifecycle starts at each developer’s machine, where the developer codes the application using their preferred language and tests it locally.</span></span> <span data-ttu-id="c5756-105">Hangi dil, çerçeve ve platform geliştirici, bu iş akışı ile seçer olsun Geliştirici her zaman geliştirme ve Docker kapsayıcıları sınama, ancak yerel olarak böylece.</span><span class="sxs-lookup"><span data-stu-id="c5756-105">No matter which language, framework, and platform the developer chooses, with this workflow, the developer is always developing and testing Docker containers, but doing so locally.</span></span>

<span data-ttu-id="c5756-106">Her kapsayıcı (bir Docker görüntüsü örneğini) aşağıdaki bileşenleri içerir:</span><span class="sxs-lookup"><span data-stu-id="c5756-106">Each container (an instance of a Docker image) includes the following components:</span></span>

-   <span data-ttu-id="c5756-107">Bir işletim sistemi seçimi olduğu (örneğin, bir Linux dağıtımı, Windows Nano Server veya Windows Server Core).</span><span class="sxs-lookup"><span data-stu-id="c5756-107">An operating system selection (for example, a Linux distribution, Windows Nano Server, or Windows Server Core).</span></span>

-   <span data-ttu-id="c5756-108">(Uygulama ikili dosyaları, vb.) geliştirici tarafından eklenen dosyalar.</span><span class="sxs-lookup"><span data-stu-id="c5756-108">Files added by the developer (application binaries, etc.).</span></span>

-   <span data-ttu-id="c5756-109">Yapılandırma bilgileri (ortam ayarlarını ve bağımlılıklarını).</span><span class="sxs-lookup"><span data-stu-id="c5756-109">Configuration information (environment settings and dependencies).</span></span>

## <a name="workflow-for-developing-docker-container-based-applications"></a><span data-ttu-id="c5756-110">Docker kapsayıcısı tabanlı uygulamalar geliştirmek için iş akışı</span><span class="sxs-lookup"><span data-stu-id="c5756-110">Workflow for developing Docker container-based applications</span></span>

<span data-ttu-id="c5756-111">Bu bölümde açıklanmıştır *iç döngü* Docker kapsayıcısı tabanlı uygulamalar için geliştirme iş akışı.</span><span class="sxs-lookup"><span data-stu-id="c5756-111">This section describes the *inner-loop* development workflow for Docker container-based applications.</span></span> <span data-ttu-id="c5756-112">İç döngü iş akışı, daha geniş DevOps iş akışını dikkate alarak değildir ve yalnızca geliştiricinin bilgisayarında geliştirme çalışmanın odaklanır anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="c5756-112">The inner-loop workflow means it is not taking into account the broader DevOps workflow and just focuses on the development work done on the developer’s computer.</span></span> <span data-ttu-id="c5756-113">İlk ortamını ayarlama adımlarını bu yalnızca bir kez gerçekleştirilir dahil değildir.</span><span class="sxs-lookup"><span data-stu-id="c5756-113">The initial steps to set up the environment are not included, since those are done only once.</span></span>

<span data-ttu-id="c5756-114">Uygulamanın kendi Hizmetleri artı ek kitaplıkları (bağımlılıklar) oluşur.</span><span class="sxs-lookup"><span data-stu-id="c5756-114">An application is composed of your own services plus additional libraries (dependencies).</span></span> <span data-ttu-id="c5756-115">Aşağıda, genellikle bir Docker uygulaması oluştururken, Şekil 5-1'de gösterildiği gibi temel adımlar verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="c5756-115">The following are the basic steps you usually take when building a Docker application, as illustrated in Figure 5-1.</span></span>

![](./media/image1.png)

<span data-ttu-id="c5756-116">**Şekil 5-1.**</span><span class="sxs-lookup"><span data-stu-id="c5756-116">**Figure 5-1.**</span></span> <span data-ttu-id="c5756-117">Kapsayıcılı Docker uygulamaları geliştirmek için adım adım iş akışı</span><span class="sxs-lookup"><span data-stu-id="c5756-117">Step-by-step workflow for developing Docker containerized apps</span></span>

<span data-ttu-id="c5756-118">Bu kılavuzda bu sürecin tamamı ayrıntılı ve Visual Studio ortamda Odaklanıldığında her ana adım açıklanmıştır.</span><span class="sxs-lookup"><span data-stu-id="c5756-118">In this guide, this whole process is detailed and every major step is explained by focusing on a Visual Studio environment.</span></span>

<span data-ttu-id="c5756-119">Bir düzenleyici/CLI geliştirme yaklaşım (örneğin, Visual Studio Code artı Docker CLI macOS üzerinde ya da Windows) kullanırken, her adım, Visual Studio kullanıyorsanız, daha ayrıntılı biçimde genellikle bilmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="c5756-119">When you are using an editor/CLI development approach (for example, Visual Studio Code plus Docker CLI on macOS or Windows), you need to know every step, generally in more detail than if you are using Visual Studio.</span></span> <span data-ttu-id="c5756-120">CLI ortamında çalışma hakkında daha fazla ayrıntı için e-kitap başvuran [kapsayıcılı Docker uygulama yaşam döngüsü Microsoft Platforms ve araçları ile](http://aka.ms/dockerlifecycleebook/).</span><span class="sxs-lookup"><span data-stu-id="c5756-120">For more details about working in a CLI environment, refer to the e-book [Containerized Docker Application lifecycle with Microsoft Platforms and Tools](http://aka.ms/dockerlifecycleebook/).</span></span>

<span data-ttu-id="c5756-121">Visual Studio 2015 veya Visual Studio 2017 kullanırken, bu adımların çoğunu sizin yerinize üretkenliğinizi önemli ölçüde artıran işlenir.</span><span class="sxs-lookup"><span data-stu-id="c5756-121">When you are using Visual Studio 2015 or Visual Studio 2017, many of those steps are handled for you, which dramatically improves your productivity.</span></span> <span data-ttu-id="c5756-122">Visual Studio 2017 kullanarak ve birden çok kapsayıcı uygulamaları hedefleme durumlarda özellikle geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="c5756-122">This is especially true when you are using Visual Studio 2017 and targeting multi-container applications.</span></span> <span data-ttu-id="c5756-123">Örneğin, yalnızca tek bir tıklatmayla Visual Studio Dockerfile ve docker-compose.yml dosyası uygulamanız için yapılandırma projelerinizi ekler.</span><span class="sxs-lookup"><span data-stu-id="c5756-123">For instance, with just one mouse click, Visual Studio adds the Dockerfile and docker-compose.yml file to your projects with the configuration for your application.</span></span> <span data-ttu-id="c5756-124">Visual Studio'da uygulamayı çalıştırdığınızda, Docker görüntüsünü oluşturur ve doğrudan Docker içinde birden çok kapsayıcı uygulama çalışır; bile aynı anda birden fazla kapsayıcı ayıklamanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="c5756-124">When you run the application in Visual Studio, it builds the Docker image and runs the multi-container application directly in Docker; it even allows you to debug several containers at once.</span></span> <span data-ttu-id="c5756-125">Bu özellikleri kullanarak geliştirme hızını artırır.</span><span class="sxs-lookup"><span data-stu-id="c5756-125">These features will boost your development speed.</span></span>

<span data-ttu-id="c5756-126">Yalnızca Visual Studio bu adımları otomatik hale getirir ancak neler olduğunu bilmeniz gerekmez gelmez docker'la üzerinde underneath.</span><span class="sxs-lookup"><span data-stu-id="c5756-126">However, just because Visual Studio makes those steps automatic does not mean that you do not need to know what is going on underneath with Docker.</span></span> <span data-ttu-id="c5756-127">Bu nedenle, aşağıdaki kılavuzunda biz her adım ayrıntılı olarak açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="c5756-127">Therefore, in the guidance that follows, we detail every step.</span></span>

![](./media/image2.png)

## <a name="step-1-start-coding-and-create-your-initial-application-or-service-baseline"></a><span data-ttu-id="c5756-128">Adım 1.</span><span class="sxs-lookup"><span data-stu-id="c5756-128">Step 1.</span></span> <span data-ttu-id="c5756-129">Kod yazmaya başlayın ve başlangıç uygulaması veya hizmeti taban çizgisi oluşturma</span><span class="sxs-lookup"><span data-stu-id="c5756-129">Start coding and create your initial application or service baseline</span></span>

<span data-ttu-id="c5756-130">Docker uygulama geliştirme, Docker olmadan uygulama geliştirme şekilde benzer.</span><span class="sxs-lookup"><span data-stu-id="c5756-130">Developing a Docker application is similar to the way you develop an application without Docker.</span></span> <span data-ttu-id="c5756-131">Docker için geliştirirken, dağıtma ve uygulama veya yerel ortamınızdaki Docker kapsayıcıları içinde çalışan hizmetler sınama olduğundan farktır.</span><span class="sxs-lookup"><span data-stu-id="c5756-131">The difference is that while developing for Docker, you are deploying and testing your application or services running within Docker containers in your local environment.</span></span> <span data-ttu-id="c5756-132">Kapsayıcı, bir Linux kapsayıcı veya bir Windows kapsayıcı olabilir.</span><span class="sxs-lookup"><span data-stu-id="c5756-132">The container can be either a Linux container or a Windows container.</span></span>

### <a name="set-up-your-local-environment-with-visual-studio"></a><span data-ttu-id="c5756-133">Visual Studio ile yerel ortamınızı ayarlayın</span><span class="sxs-lookup"><span data-stu-id="c5756-133">Set up your local environment with Visual Studio</span></span>

<span data-ttu-id="c5756-134">Başlamak için olduğundan emin olun [Docker Community Edition (CE)](https://www.docker.com/community-edition) aşağıdaki yönergelerde yer açıklandığı gibi yüklü Windows için:</span><span class="sxs-lookup"><span data-stu-id="c5756-134">To begin, make sure you have [Docker Community Edition (CE)](https://www.docker.com/community-edition) for Windows installed, as explained in the following instructions:</span></span>

[<span data-ttu-id="c5756-135">Docker Windows CE ile çalışmaya başlama</span><span class="sxs-lookup"><span data-stu-id="c5756-135">Get started with Docker CE for Windows</span></span>](https://docs.docker.com/docker-for-windows/)

<span data-ttu-id="c5756-136">Ayrıca, Visual Studio yüklü 2017 gerekir.</span><span class="sxs-lookup"><span data-stu-id="c5756-136">In addition, you will need Visual Studio 2017 installed.</span></span> <span data-ttu-id="c5756-137">Visual Studio 2017 Docker, desteği kapsayıcılarında hata ayıklama desteği gibi daha gelişmiş olduğundan bu için Docker eklentisi, Visual Studio Araçları ile Visual Studio 2015 üzerinden tercih edilir.</span><span class="sxs-lookup"><span data-stu-id="c5756-137">This is preferred over Visual Studio 2015 with the Visual Studio Tools for Docker add-in, because Visual Studio 2017 has more advanced support for Docker, like support for debugging containers.</span></span> <span data-ttu-id="c5756-138">Visual Studio 2017 seçtiyseniz, Docker araç içerir **.NET Core ve Docker** Şekil 5-2'de gösterildiği gibi yükleme sırasında iş yükü.</span><span class="sxs-lookup"><span data-stu-id="c5756-138">Visual Studio 2017 includes the tooling for Docker if you selected the **.NET Core and Docker** workload during installation, as shown in Figure 5-2.</span></span>

![](./media/image3.png)

<span data-ttu-id="c5756-139">**Şekil 5-2**.</span><span class="sxs-lookup"><span data-stu-id="c5756-139">**Figure 5-2**.</span></span> <span data-ttu-id="c5756-140">Seçme **.NET Core ve Docker** Visual Studio 2017 Kurulum sırasında iş yükü</span><span class="sxs-lookup"><span data-stu-id="c5756-140">Selecting the **.NET Core and Docker** workload during Visual Studio 2017 setup</span></span>

<span data-ttu-id="c5756-141">Docker uygulamanızda etkinleştirme ve dağıtma ve Docker içinde test önce bile düz .NET (genellikle kapsayıcılar kullanma planlıyorsanız, .NET Core) uygulamanızda kodlama başlatabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c5756-141">You can start coding your application in plain .NET (usually in .NET Core if you are planning to use containers) even before enabling Docker in your application and deploying and testing in Docker.</span></span> <span data-ttu-id="c5756-142">Ancak, Docker üzerinde olabildiğince çabuk, çünkü gerçek ortamı olacaktır ve sorunları mümkün olan en kısa sürede keşfedilmesini çalışmaya başlamak önerilir.</span><span class="sxs-lookup"><span data-stu-id="c5756-142">However, it is recommended that you start working on Docker as soon as possible, because that will be the real environment and any issues can be discovered as soon as possible.</span></span> <span data-ttu-id="c5756-143">Visual Studio, bu nedenle, neredeyse saydam hissi, Docker ile çalışmak kolaylaştırır çünkü bu teşvik — birden çok kapsayıcı uygulamaları Visual Studio'da hata ayıklama sırasında en iyi örnek.</span><span class="sxs-lookup"><span data-stu-id="c5756-143">This is encouraged because Visual Studio makes it so easy to work with Docker that it almost feels transparent—the best example when debugging multi-container applications from Visual Studio.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="c5756-144">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="c5756-144">Additional resources</span></span>

-   <span data-ttu-id="c5756-145">**Docker Windows CE ile çalışmaya başlama**
    [*https://docs.docker.com/docker-for-windows/*](https://docs.docker.com/docker-for-windows/)</span><span class="sxs-lookup"><span data-stu-id="c5756-145">**Get started with Docker CE for Windows**
[*https://docs.docker.com/docker-for-windows/*](https://docs.docker.com/docker-for-windows/)</span></span>

-   <span data-ttu-id="c5756-146">**Visual Studio 2017**
    [*https://visualstudio.microsoft.com/downloads/*](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs)</span><span class="sxs-lookup"><span data-stu-id="c5756-146">**Visual Studio 2017**
[*https://visualstudio.microsoft.com/downloads/*](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs)</span></span>

![](./media/image4.png)

## <a name="step-2-create-a-dockerfile-related-to-an-existing-net-base-image"></a><span data-ttu-id="c5756-147">Adım 2.</span><span class="sxs-lookup"><span data-stu-id="c5756-147">Step 2.</span></span> <span data-ttu-id="c5756-148">Varolan bir .NET temel görüntüsü için ilgili bir Dockerfile oluşturma</span><span class="sxs-lookup"><span data-stu-id="c5756-148">Create a Dockerfile related to an existing .NET base image</span></span>

<span data-ttu-id="c5756-149">Oluşturmak istediğiniz her özel görüntü için bir Dockerfile gerekir; Visual Studio veya Docker CLI kullanarak el ile otomatik olarak dağıtmak isteyip dağıtılması için bir Dockerfile her kapsayıcı için de gerekir (docker çalıştırın ve docker-komutları oluşturma).</span><span class="sxs-lookup"><span data-stu-id="c5756-149">You need a Dockerfile for each custom image you want to build; you also need a Dockerfile for each container to be deployed, whether you deploy automatically from Visual Studio or manually using the Docker CLI (docker run and docker-compose commands).</span></span> <span data-ttu-id="c5756-150">Uygulamanızın tek bir özel hizmet içeriyorsa, tek bir Dockerfile gerekir.</span><span class="sxs-lookup"><span data-stu-id="c5756-150">If your application contains a single custom service, you need a single Dockerfile.</span></span> <span data-ttu-id="c5756-151">Uygulamanız birden çok hizmet (olduğu gibi bir mikro mimarisi) içeriyorsa, her hizmet için bir Dockerfile gerekir.</span><span class="sxs-lookup"><span data-stu-id="c5756-151">If your application contains multiple services (as in a microservices architecture), you need one Dockerfile for each service.</span></span>

<span data-ttu-id="c5756-152">Dockerfile uygulama veya hizmet kök klasöründe yer alır.</span><span class="sxs-lookup"><span data-stu-id="c5756-152">The Dockerfile is placed in the root folder of your application or service.</span></span> <span data-ttu-id="c5756-153">Docker ayarlama ve uygulama veya hizmet bir kapsayıcıda çalıştırmak nasıl anlatın komutları içerir.</span><span class="sxs-lookup"><span data-stu-id="c5756-153">It contains the commands that tell Docker how to set up and run your application or service in a container.</span></span> <span data-ttu-id="c5756-154">El ile bir Dockerfile kodda oluşturun ve yanı sıra, .NET bağımlılıkları projenize ekleyin.</span><span class="sxs-lookup"><span data-stu-id="c5756-154">You can manually create a Dockerfile in code and add it to your project along with your .NET dependencies.</span></span>

<span data-ttu-id="c5756-155">Visual Studio ve Docker için kendi araçları ile bu görevi yalnızca birkaç kere fareyi tıklatarak gerektirir.</span><span class="sxs-lookup"><span data-stu-id="c5756-155">With Visual Studio and its tools for Docker, this task requires only a few mouse clicks.</span></span> <span data-ttu-id="c5756-156">Visual Studio 2017 içinde yeni bir proje oluşturduğunuzda, adında bir seçenek yoktur **etkinleştirmek kapsayıcı (Docker) desteği**Şekil 5-3'te gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="c5756-156">When you create a new project in Visual Studio 2017, there is an option named **Enable Container (Docker) Support**, as shown in Figure 5-3.</span></span>

![](./media/image5.png)

<span data-ttu-id="c5756-157">**Şekil 5-3**.</span><span class="sxs-lookup"><span data-stu-id="c5756-157">**Figure 5-3**.</span></span> <span data-ttu-id="c5756-158">Visual Studio 2017 içinde yeni bir proje oluştururken, Docker desteğini etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="c5756-158">Enabling Docker Support when creating a new project in Visual Studio 2017</span></span>

<span data-ttu-id="c5756-159">Yeni veya var olan bir proje üzerinde Docker desteği, Visual Studio Proje dosyasında sağ tıklayıp seçeneğini seçerek etkinleştirebilirsiniz **Proje Ekle Docker Destek**Şekil 5-4'te gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="c5756-159">You can also enable Docker support on a new or existing project by right-clicking your project file in Visual Studio and selecting the option **Add-Docker Project Support**, as shown in Figure 5-4.</span></span>

![](./media/image6.png)

<span data-ttu-id="c5756-160">**Şekil 5-4**.</span><span class="sxs-lookup"><span data-stu-id="c5756-160">**Figure 5-4**.</span></span> <span data-ttu-id="c5756-161">Varolan bir Visual Studio 2017 projesinde Docker desteğini etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="c5756-161">Enabling Docker support in an existing Visual Studio 2017 project</span></span>

<span data-ttu-id="c5756-162">Bu eylem (bir ASP.NET Web uygulaması veya Web API hizmeti gibi) bir proje üzerinde bir Dockerfile gerekli yapılandırma ile projeye ekler.</span><span class="sxs-lookup"><span data-stu-id="c5756-162">This action on a project (like an ASP.NET Web application or Web API service) adds a Dockerfile to the project with the required configuration.</span></span> <span data-ttu-id="c5756-163">Ayrıca, tüm çözüm için docker-compose.yml dosyası ekler.</span><span class="sxs-lookup"><span data-stu-id="c5756-163">It also adds a docker-compose.yml file for the whole solution.</span></span> <span data-ttu-id="c5756-164">Aşağıdaki bölümlerde, bu dosyaların her giden bilgileri açıklar.</span><span class="sxs-lookup"><span data-stu-id="c5756-164">In the following sections, we describe the information that goes into each of those files.</span></span> <span data-ttu-id="c5756-165">Visual Studio sizin için bu iş yapmak, ancak bir Dockerfile unsurları anlamak kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="c5756-165">Visual Studio can do this work for you, but it is useful to understand what goes into a Dockerfile.</span></span>

### <a name="option-a-creating-a-project-using-an-existing-official-net-docker-image"></a><span data-ttu-id="c5756-166">Seçenek A: var olan bir resmi .NET Docker görüntüsünü kullanarak bir proje oluşturma</span><span class="sxs-lookup"><span data-stu-id="c5756-166">Option A: Creating a project using an existing official .NET Docker image</span></span>

<span data-ttu-id="c5756-167">Genellikle, kapsayıcısının üstünde resmi bir depodan alma temel görüntü için özel bir görüntü yapı [Docker hub'a](https://hub.docker.com/) kayıt defteri.</span><span class="sxs-lookup"><span data-stu-id="c5756-167">You usually build a custom image for your container on top of a base image you can get from an official repository at the [Docker Hub](https://hub.docker.com/) registry.</span></span> <span data-ttu-id="c5756-168">Visual Studio'da Docker desteğini etkinleştirme ne olur perde arkasında tam olarak olmasıdır.</span><span class="sxs-lookup"><span data-stu-id="c5756-168">That is precisely what happens under the covers when you enable Docker support in Visual Studio.</span></span> <span data-ttu-id="c5756-169">Dockerfile var olan bir aspnetcore görüntüsünü kullanır.</span><span class="sxs-lookup"><span data-stu-id="c5756-169">Your Dockerfile will use an existing aspnetcore image.</span></span>

<span data-ttu-id="c5756-170">Daha önce hangi Docker görüntüler ve seçtiğiniz işletim sistemi ve framework bağlı olarak kullanabilirsiniz depoları açıklanmıştır.</span><span class="sxs-lookup"><span data-stu-id="c5756-170">Earlier we explained which Docker images and repos you can use, depending on the framework and OS you have chosen.</span></span> <span data-ttu-id="c5756-171">ASP.NET Core (Linux veya Windows) kullanmak istiyorsanız, örneğin, kullanılacak microsoft görüntüdür / aspnetcore:2.0.</span><span class="sxs-lookup"><span data-stu-id="c5756-171">For instance, if you want to use ASP.NET Core (Linux or Windows), the image to use is microsoft/aspnetcore:2.0.</span></span> <span data-ttu-id="c5756-172">Bu nedenle, kapsayıcı için kullanacağınız temel hangi Docker görüntüyü belirtmek yeterlidir.</span><span class="sxs-lookup"><span data-stu-id="c5756-172">Therefore, you just need to specify what base Docker image you will use for your container.</span></span> <span data-ttu-id="c5756-173">Microsoft'tan ekleyerek bunu / aspnetcore:2.0, Dockerfile için.</span><span class="sxs-lookup"><span data-stu-id="c5756-173">You do that by adding FROM microsoft/aspnetcore:2.0 to your Dockerfile.</span></span> <span data-ttu-id="c5756-174">Bu Visual Studio tarafından otomatik olarak gerçekleştirilir, ancak sürüm güncelleştirme olsaydı, bu değeri güncelleştirin.</span><span class="sxs-lookup"><span data-stu-id="c5756-174">This will be automatically performed by Visual Studio, but if you were to update the version, you update this value.</span></span>

<span data-ttu-id="c5756-175">Docker hub'a resmi bir .NET görüntü deposundan sürüm numarasıyla kullanarak (geliştirme, test ve üretim dahil) tüm makinelerde aynı dil özellikleri kullanılabilir olmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="c5756-175">Using an official .NET image repository from Docker Hub with a version number ensures that the same language features are available on all machines (including development, testing, and production).</span></span>

<span data-ttu-id="c5756-176">Aşağıdaki örnek, bir ASP.NET Core kapsayıcı için bir örnek Dockerfile gösterir.</span><span class="sxs-lookup"><span data-stu-id="c5756-176">The following example shows a sample Dockerfile for an ASP.NET Core container.</span></span>

```Dockerfile
FROM microsoft/aspnetcore:2.0
  
ARG source
  
WORKDIR /app
  
EXPOSE 80
  
COPY ${source:-obj/Docker/publish} .
  
ENTRYPOINT ["dotnet", " MySingleContainerWebApp.dll "]
```

<span data-ttu-id="c5756-177">Bu durumda, kapsayıcı resmi ASP.NET Core Docker görüntü (Linux ve Windows için çok arch) 2.0 sürümünü temel alır.</span><span class="sxs-lookup"><span data-stu-id="c5756-177">In this case, the container is based on version 2.0 of the official ASP.NET Core Docker image (multi-arch for Linux and Windows).</span></span> <span data-ttu-id="c5756-178">Ayar budur `FROM microsoft/aspnetcore:2.0`.</span><span class="sxs-lookup"><span data-stu-id="c5756-178">This is the setting `FROM microsoft/aspnetcore:2.0`.</span></span> <span data-ttu-id="c5756-179">(Bu temel görüntü hakkında daha fazla ayrıntı için bkz: [ASP.NET Core Docker görüntü](https://hub.docker.com/r/microsoft/aspnetcore/) sayfa ve [.NET Core Docker görüntü](https://hub.docker.com/r/microsoft/dotnet/) sayfası.) Dockerfile içinde de (Bu durumda, bağlantı noktası 80 ' SUNMAYA ayarıyla yapılandırıldığı gibi) çalışma zamanında kullanacağı TCP bağlantı noktasında dinlemek için Docker istemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="c5756-179">(For further details about this base image, see the [ASP.NET Core Docker Image](https://hub.docker.com/r/microsoft/aspnetcore/) page and the [.NET Core Docker Image](https://hub.docker.com/r/microsoft/dotnet/) page.) In the Dockerfile, you also need to instruct Docker to listen on the TCP port you will use at runtime (in this case, port 80, as configured with the EXPOSE setting).</span></span>

<span data-ttu-id="c5756-180">Ek yapılandırma ayarlarını dil ve kullandığınız framework bağlı olarak Dockerfile belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c5756-180">You can specify additional configuration settings in the Dockerfile, depending on the language and framework you are using.</span></span> <span data-ttu-id="c5756-181">Örneğin, ENTRYPOINT satırıyla \["dotnet", "MySingleContainerWebApp.dll"\] .NET Core uygulamayı çalıştırmak için Docker söyler.</span><span class="sxs-lookup"><span data-stu-id="c5756-181">For instance, the ENTRYPOINT line with \["dotnet", "MySingleContainerWebApp.dll"\] tells Docker to run a .NET Core application.</span></span> <span data-ttu-id="c5756-182">Derleme ve çalıştırma .NET uygulaması için SDK ve .NET Core CLI (dotnet CLI) kullanıyorsanız bu ayar farklı olacaktır.</span><span class="sxs-lookup"><span data-stu-id="c5756-182">If you are using the SDK and the .NET Core CLI (dotnet CLI) to build and run the .NET application, this setting would be different.</span></span> <span data-ttu-id="c5756-183">ENTRYPOINT satır ve diğer ayarları uygulamanız için seçtiğiniz dil ve platforma bağlı olarak farklı olacaktır alt çizgidir.</span><span class="sxs-lookup"><span data-stu-id="c5756-183">The bottom line is that the ENTRYPOINT line and other settings will be different depending on the language and platform you choose for your application.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="c5756-184">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="c5756-184">Additional resources</span></span>

-   <span data-ttu-id="c5756-185">**.NET Core uygulamaları için Docker görüntülerinizi oluşturmak**
    [*https://docs.microsoft.com/dotnet/core/docker/building-net-docker-images*](../../../core/docker/building-net-docker-images.md)</span><span class="sxs-lookup"><span data-stu-id="c5756-185">**Building Docker Images for .NET Core Applications**
[*https://docs.microsoft.com/dotnet/core/docker/building-net-docker-images*](../../../core/docker/building-net-docker-images.md)</span></span>

-   <span data-ttu-id="c5756-186">**Kendi görüntünüzü yapı**.</span><span class="sxs-lookup"><span data-stu-id="c5756-186">**Build your own image**.</span></span> <span data-ttu-id="c5756-187">Resmi Docker belgelerinde.</span><span class="sxs-lookup"><span data-stu-id="c5756-187">In the official Docker documentation.</span></span>
    [*https://docs.docker.com/engine/tutorials/dockerimages/*](https://docs.docker.com/engine/tutorials/dockerimages/)

### <a name="using-multi-arch-image-repositories"></a><span data-ttu-id="c5756-188">Birden çok yay görüntü depoları kullanma</span><span class="sxs-lookup"><span data-stu-id="c5756-188">Using multi-arch image repositories</span></span>

<span data-ttu-id="c5756-189">Tek bir depodaki Linux görüntüsü ve bir Windows görüntüsü gibi platform çeşitleri içerebilir.</span><span class="sxs-lookup"><span data-stu-id="c5756-189">A single repo can contain platform variants, such as a Linux image and a Windows image.</span></span> <span data-ttu-id="c5756-190">Bu özellik, (yani Linux ve Windows) birden çok platform kapsayacak şekilde bir tek depodaki satıcılarının Microsoft (temel görüntü oluşturucuları) gibi sağlar.</span><span class="sxs-lookup"><span data-stu-id="c5756-190">This feature allows vendors like Microsoft (base image creators) to create a single repo to cover multiple platforms (that is Linux and Windows).</span></span> <span data-ttu-id="c5756-191">Örneğin, [microsoft/dotnet](https://hub.docker.com/r/microsoft/aspnetcore/) Docker hub'a kayıt defterinde depo aynı depodaki adı kullanarak Linux ve Windows Nano Server desteği sağlar.</span><span class="sxs-lookup"><span data-stu-id="c5756-191">For example, the [microsoft/dotnet](https://hub.docker.com/r/microsoft/aspnetcore/) repository available in the Docker Hub registry provides support for Linux and Windows Nano Server by using the same repo name.</span></span>

<span data-ttu-id="c5756-192">Açık bir platform desteği bir etiket belirtirseniz aşağıdaki durumlarda ister:</span><span class="sxs-lookup"><span data-stu-id="c5756-192">If you specify a tag, targeting a platform that is explicit like in the following cases:</span></span>

-   <span data-ttu-id="c5756-193">**Microsoft/aspnetcore:2.0.0-jessie**</span><span class="sxs-lookup"><span data-stu-id="c5756-193">**microsoft/aspnetcore:2.0.0-jessie**</span></span>

        .NET Core 2.0 runtime-only on Linux 

-   <span data-ttu-id="c5756-194">**Microsoft/aspnetcore:2.0.0-nanoserver**</span><span class="sxs-lookup"><span data-stu-id="c5756-194">**microsoft/aspnetcore:2.0.0-nanoserver**</span></span>

        .NET Core 2.0 runtime-only on Windows Nano Server

<span data-ttu-id="c5756-195">Ancak ve belirtirseniz, bu yeni mid-2017 itibaren bile aynı etiketi ile aynı görüntü adı, Linux veya Windows sürümü dağıttığınız Docker ana bilgisayar işletim sistemi bağlı olarak yeni çok yay görüntüleri (gibi çok arch destekleyen aspnetcore görüntü) kullanır , aşağıdaki örnekte gösterildiği gibi:</span><span class="sxs-lookup"><span data-stu-id="c5756-195">But, and this is new since mid-2017, if you specify the same image name, even with the same tag, the new multi-arch images (like the aspnetcore image which supports multi-arch) will use the Linux or Windows version depending on the Docker host OS you are deploying, as shown in the following example:</span></span>

-   <span data-ttu-id="c5756-196">**Microsoft / aspnetcore:2.0**</span><span class="sxs-lookup"><span data-stu-id="c5756-196">**microsoft/aspnetcore:2.0**</span></span>

        Multi-arch: .NET Core 2.0 runtime-only on Linux or Windows Nano Server depending on the Docker host OS

<span data-ttu-id="c5756-197">Bir Windows ana bilgisayardan bir görüntü istek olduğunda bu şekilde, Windows değişken çeker ve aynı görüntü adı Linux ana bilgisayardan çekme Linux değişken çeker.</span><span class="sxs-lookup"><span data-stu-id="c5756-197">This way, when you pull an image from a Windows host, it will pull the Windows variant, and pulling the same image name from a Linux host will pull the Linux variant.</span></span>

### <a name="option-b-creating-your-base-image-from-scratch"></a><span data-ttu-id="c5756-198">Seçenek B: temel görüntünüzde sıfırdan oluşturma</span><span class="sxs-lookup"><span data-stu-id="c5756-198">Option B: Creating your base image from scratch</span></span>

<span data-ttu-id="c5756-199">Kendi Docker temel görüntü sıfırdan oluşturabilir.</span><span class="sxs-lookup"><span data-stu-id="c5756-199">You can create your own Docker base image from scratch.</span></span> <span data-ttu-id="c5756-200">Bu senaryo ile Docker başlangıç birinin önerilmez, ancak temel görüntünüzün belirli BITS ayarlamak istiyorsanız, bunu yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c5756-200">This scenario is not recommended for someone who is starting with Docker, but if you want to set the specific bits of your own base image, you can do so.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="c5756-201">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="c5756-201">Additional resources</span></span>

-   <span data-ttu-id="c5756-202">**Birden çok yay .NET Core görüntüleri**.</span><span class="sxs-lookup"><span data-stu-id="c5756-202">**Multi-arch .NET Core images**.</span></span>
<span data-ttu-id="c5756-203">https://github.com/dotnet/announcements/issues/14</span><span class="sxs-lookup"><span data-stu-id="c5756-203">https://github.com/dotnet/announcements/issues/14</span></span> 
-   <span data-ttu-id="c5756-204">**Temel görüntü oluşturma**.</span><span class="sxs-lookup"><span data-stu-id="c5756-204">**Create a base image**.</span></span> <span data-ttu-id="c5756-205">Resmi Docker belge.</span><span class="sxs-lookup"><span data-stu-id="c5756-205">Official Docker documentation.</span></span>
    [*https://docs.docker.com/engine/userguide/eng-image/baseimages/*](https://docs.docker.com/engine/userguide/eng-image/baseimages/)

![](./media/image7.png)

## <a name="step-3-create-your-custom-docker-images-and-embed-your-application-or-service-in-them"></a><span data-ttu-id="c5756-206">Adım 3.</span><span class="sxs-lookup"><span data-stu-id="c5756-206">Step 3.</span></span> <span data-ttu-id="c5756-207">Özel Docker görüntülerinizi oluşturmak ve uygulama veya hizmet bunları katıştırma</span><span class="sxs-lookup"><span data-stu-id="c5756-207">Create your custom Docker images and embed your application or service in them</span></span>

<span data-ttu-id="c5756-208">Uygulamanızdaki her hizmet için ilgili bir görüntüsü oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="c5756-208">For each service in your application, you need to create a related image.</span></span> <span data-ttu-id="c5756-209">Uygulamanızı bir tek hizmeti veya web uygulaması oluşuyorsa, tek bir görüntü yeterlidir.</span><span class="sxs-lookup"><span data-stu-id="c5756-209">If your application is made up of a single service or web application, you just need a single image.</span></span>

<span data-ttu-id="c5756-210">Docker görüntüleri otomatik olarak sizin için Visual Studio'da oluşturulan unutmayın.</span><span class="sxs-lookup"><span data-stu-id="c5756-210">Note that the Docker images are built automatically for you in Visual Studio.</span></span> <span data-ttu-id="c5756-211">Aşağıdaki adımlar yalnızca Düzenleyicisi/CLI iş akışı için gereken ve daha anlaşılır olması için ne altında olduğu hakkında açıklanmıştır.</span><span class="sxs-lookup"><span data-stu-id="c5756-211">The following steps are only needed for the editor/CLI workflow and explained for clarity about what happens underneath.</span></span>

<span data-ttu-id="c5756-212">Geliştirici olarak geliştirmek ve yerel olarak tamamlanmış bir itme kadar test yapmanız özellik veya kaynak denetimi sisteminize (örneğin, GitHub) değiştirin.</span><span class="sxs-lookup"><span data-stu-id="c5756-212">You, as developer, need to develop and test locally until you push a completed feature or change to your source control system (for example, to GitHub).</span></span> <span data-ttu-id="c5756-213">Bu, Docker görüntülerini oluşturmak ve bir yerel Docker konağına (Windows veya Linux VM) kapsayıcıları dağıtın ve çalıştırın, test ve bu yerel kapsayıcıları karşı hata ayıklama gerektiği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="c5756-213">This means that you need to create the Docker images and deploy containers to a local Docker host (Windows or Linux VM) and run, test, and debug against those local containers.</span></span>

<span data-ttu-id="c5756-214">Docker CLI ve, Dockerfile kullanarak yerel ortamınıza özel bir görüntü oluşturmak için docker yapı komutu, Şekil 5-5'olduğu gibi kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c5756-214">To create a custom image in your local environment by using Docker CLI and your Dockerfile, you can use the docker build command, as in Figure 5-5.</span></span>

![](./media/image8.png)

<span data-ttu-id="c5756-215">**Şekil 5-5**.</span><span class="sxs-lookup"><span data-stu-id="c5756-215">**Figure 5-5**.</span></span> <span data-ttu-id="c5756-216">Özel bir Docker görüntü oluşturma</span><span class="sxs-lookup"><span data-stu-id="c5756-216">Creating a custom Docker image</span></span>

<span data-ttu-id="c5756-217">İsteğe bağlı olarak, doğrudan docker yapı proje klasöründen çalıştırmak, yerine, önce gerekli .NET kitaplıklarına dağıtılabilir bir klasör oluşturabilirsiniz ve dotnet çalıştırarak ikili dosyaları yayımlayın ve sonra docker yapı komutunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="c5756-217">Optionally, instead of directly running docker build from the project folder, you can first generate a deployable folder with the required .NET libraries and binaries by running dotnet publish, and then use the docker build command.</span></span>

<span data-ttu-id="c5756-218">Bu bir Docker görüntüsü cesardl/netcore-webapı-mikro adı ile oluşturur-docker: ilk.</span><span class="sxs-lookup"><span data-stu-id="c5756-218">This will create a Docker image with the name cesardl/netcore-webapi-microservice-docker:first.</span></span> <span data-ttu-id="c5756-219">Bu durumda: öncelikle, belirli bir sürümü temsil eden bir etiketi olan.</span><span class="sxs-lookup"><span data-stu-id="c5756-219">In this case, :first is a tag representing a specific version.</span></span> <span data-ttu-id="c5756-220">Oluşturulan Docker uygulamanız için oluşturmanıza gerek her özel görüntü için bu adımı yineleyin.</span><span class="sxs-lookup"><span data-stu-id="c5756-220">You can repeat this step for each custom image you need to create for your composed Docker application.</span></span>

<span data-ttu-id="c5756-221">Bir uygulama birden çok kapsayıcı yapılan zaman (diğer bir deyişle, bu çok kapsayıcı uygulama'dir), aynı zamanda docker---ilgili kullanıma sunulan meta verileri kullanarak tek bir komutla ilgili tüm görüntüleri oluşturmak için yapı komutu oluşturmanıza docker-compose.yml dosyaları.</span><span class="sxs-lookup"><span data-stu-id="c5756-221">When an application is made of multiple containers (that is, it is a multi-container application), you can also use the docker-compose up --build command to build all the related images with a single command by using the metadata exposed in the related docker-compose.yml files.</span></span>

<span data-ttu-id="c5756-222">Var olan görüntüleri yerel depoda docker kullanarak görüntüleri komutu, Şekil 5-6'da gösterildiği gibi bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c5756-222">You can find the existing images in your local repository by using the docker images command, as shown in Figure 5-6.</span></span>

![](./media/image9.png)

<span data-ttu-id="c5756-223">**Şekil 5-6.**</span><span class="sxs-lookup"><span data-stu-id="c5756-223">**Figure 5-6.**</span></span> <span data-ttu-id="c5756-224">Docker görüntüleri komutunu kullanarak var olan görüntüleri görüntüleme</span><span class="sxs-lookup"><span data-stu-id="c5756-224">Viewing existing images using the docker images command</span></span>

### <a name="creating-docker-images-with-visual-studio"></a><span data-ttu-id="c5756-225">Visual Studio ile Docker görüntüleri oluşturma</span><span class="sxs-lookup"><span data-stu-id="c5756-225">Creating Docker images with Visual Studio</span></span>

<span data-ttu-id="c5756-226">Docker desteği olan bir proje oluşturmak için Visual Studio kullanırken, görüntüyü açıkça oluşturmayın.</span><span class="sxs-lookup"><span data-stu-id="c5756-226">When you are using Visual Studio to create a project with Docker support, you do not explicitly create an image.</span></span> <span data-ttu-id="c5756-227">Bunun yerine, F5 tuşuna basın ve dockerized uygulaması veya hizmeti çalıştırdığınızda görüntü sizin için oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="c5756-227">Instead, the image is created for you when you press F5 and run the dockerized application or service.</span></span> <span data-ttu-id="c5756-228">Bu adım Visual Studio'da otomatik olarak yapılır ve bunu durum göremez ancak neler olduğunu bilmeniz önemlidir üzerinde underneath.</span><span class="sxs-lookup"><span data-stu-id="c5756-228">This step is automatic in Visual Studio, and you will not see it happen, but it is important that you know what is going on underneath.</span></span>

![](./media/image10.png)

## <a name="step-4-define-your-services-in-docker-composeyml-when-building-a-multi-container-docker-application"></a><span data-ttu-id="c5756-229">4. adım.</span><span class="sxs-lookup"><span data-stu-id="c5756-229">Step 4.</span></span> <span data-ttu-id="c5756-230">Birden çok kapsayıcı Docker uygulama oluştururken hizmetlerinizi docker-compose.yml tanımlayın</span><span class="sxs-lookup"><span data-stu-id="c5756-230">Define your services in docker-compose.yml when building a multi-container Docker application</span></span>

<span data-ttu-id="c5756-231">[Docker-compose.yml](https://docs.docker.com/compose/compose-file/) dosyası dağıtım komutları ile oluşturulmuş bir uygulama olarak dağıtılması için ilgili hizmetler kümesini tanımlamak imkan tanır.</span><span class="sxs-lookup"><span data-stu-id="c5756-231">The [docker-compose.yml](https://docs.docker.com/compose/compose-file/) file lets you define a set of related services to be deployed as a composed application with deployment commands.</span></span>

<span data-ttu-id="c5756-232">Docker-compose.yml dosyası kullanmak için aşağıdaki örneğe benzer içerikle, ana dosyasında veya kök Çözüm klasörü oluşturmanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="c5756-232">To use a docker-compose.yml file, you need to create the file in your main or root solution folder, with content similar to that in the following example:</span></span>

```yml
version: '3'
  
services:

  webmvc:
    image: eshop/web
    environment:
      - CatalogUrl=http://catalog.api
      - OrderingUrl=http://ordering.api
    ports:
      - "80:80"
    depends_on:
      - catalog.api
      - ordering.api

  catalog.api:
    image: eshop/catalog.api
    environment: 
      - ConnectionString=Server=sql.data;Database=CatalogDB;…
    ports:
      - "81:80"
    depends_on:
      - sql.data

  ordering.api:
    image: eshop/ordering.api
    environment:
      - ConnectionString=Server=sql.data;Database=OrderingDb;…
    ports:
      - "82:80"
    extra_hosts:
      - "CESARDLBOOKVHD:10.0.75.1"
    depends_on:
      - sql.data

  sql.data:
    image: mssql-server-linux:latest
    environment:
      - SA_PASSWORD=Pass@word
      - ACCEPT_EULA=Y
    ports:
      - "5433:1433"

```

<span data-ttu-id="c5756-233">Bu docker-compose.yml dosyası Basitleştirilmiş ve birleştirilmiş bir sürüm olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="c5756-233">Note that this docker-compose.yml file is a simplified and merged version.</span></span> <span data-ttu-id="c5756-234">Her zaman, bağlantı dizesi gibi dağıtım ortamı bağlı olabilir yapılandırma bilgilerini artı geçerli her kapsayıcı (gibi özel görüntü adı), statik yapılandırma verilerini içerir.</span><span class="sxs-lookup"><span data-stu-id="c5756-234">It contains static configuration data for each container (like the name of the custom image), which always applies, plus configuration information that might depend on the deployment environment, like the connection string.</span></span> <span data-ttu-id="c5756-235">Sonraki bölümlerde, birden çok docker-compose.yml yapılandırmaya nasıl bölebilirsiniz öğreneceksiniz dosyaları ve geçersiz kılma değerleri (hata ayıklama veya yayın) ortamını ve yürütme türüne bağlı olarak docker compose'u.</span><span class="sxs-lookup"><span data-stu-id="c5756-235">In later sections, you will learn how you can split the docker-compose.yml configuration into multiple docker-compose files and override values depending on the environment and execution type (debug or release).</span></span>

<span data-ttu-id="c5756-236">Docker-compose.yml dosyası örneği beş hizmetleri tanımlar: webmvc hizmeti (web uygulaması), iki mikro (catalog.api ve ordering.api) ve bir kapsayıcı olarak çalıştırılan Linux için SQL Server tabanlı bir veri kaynağı kapsayıcı, sql.data,.</span><span class="sxs-lookup"><span data-stu-id="c5756-236">The docker-compose.yml file example defines five services: the webmvc service (a web application), two microservices (catalog.api and ordering.api), and one data source container, sql.data, based on SQL Server for Linux running as a container.</span></span> <span data-ttu-id="c5756-237">Docker görüntü her biri için gerekli olacak şekilde, her hizmetin bir kapsayıcı olarak dağıtılır.</span><span class="sxs-lookup"><span data-stu-id="c5756-237">Each service is deployed as a container, so a Docker image is required for each.</span></span>

<span data-ttu-id="c5756-238">Docker-compose.yml dosyası yalnızca hangi kapsayıcılar kullanılır, ancak bunlar ayrı ayrı nasıl yapılandırılacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="c5756-238">The docker-compose.yml file specifies not only what containers are being used, but how they are individually configured.</span></span> <span data-ttu-id="c5756-239">Örneğin, webmvc kapsayıcı tanımına .yml dosyasında:</span><span class="sxs-lookup"><span data-stu-id="c5756-239">For instance, the webmvc container definition in the .yml file:</span></span>

-   <span data-ttu-id="c5756-240">Önceden oluşturulmuş Elektronik Mağaza kullanan / web: son görüntü.</span><span class="sxs-lookup"><span data-stu-id="c5756-240">Uses a pre-built eshop/web:latest image.</span></span> <span data-ttu-id="c5756-241">Ancak, aynı zamanda bir parçası olarak oluşturulacak görüntü yapılandırabilirsiniz docker compose'u yürütme ek bir yapılandırma temel yapıyı: docker-compose dosyasındaki bölümü.</span><span class="sxs-lookup"><span data-stu-id="c5756-241">However, you could also configure the image to be built as part of the docker-compose execution with an additional configuration based on a build: section in the docker-compose file.</span></span>

-   <span data-ttu-id="c5756-242">İki ortam değişkenlerini (katalog URL'si ve OrderingUrl) başlatır.</span><span class="sxs-lookup"><span data-stu-id="c5756-242">Initializes two environment variables (CatalogUrl and OrderingUrl).</span></span>

-   <span data-ttu-id="c5756-243">Kullanıma sunulan bağlantı noktası 80 kapsayıcısı konak makinedeki dış bağlantı noktası 80 üzerinde iletir.</span><span class="sxs-lookup"><span data-stu-id="c5756-243">Forwards the exposed port 80 on the container to the external port 80 on the host machine.</span></span>

-   <span data-ttu-id="c5756-244">Web uygulama kataloğu ve hizmetiyle sıralama bağlar bağlıdır\_ayarı.</span><span class="sxs-lookup"><span data-stu-id="c5756-244">Links the web app to the catalog and ordering service with the depends\_on setting.</span></span> <span data-ttu-id="c5756-245">Bu, bu hizmetleri yeniden başlatılana kadar beklenecek hizmeti neden olur.</span><span class="sxs-lookup"><span data-stu-id="c5756-245">This causes the service to wait until those services are started.</span></span>

<span data-ttu-id="c5756-246">Biz mikro ve birden çok kapsayıcı uygulamaları uygulama konularını olduğunda sizi bir sonraki bölümde docker-compose.yml dosyası yeniden ziyaret.</span><span class="sxs-lookup"><span data-stu-id="c5756-246">We will revisit the docker-compose.yml file in a later section when we cover how to implement microservices and multi-container apps.</span></span>

### <a name="working-with-docker-composeyml-in-visual-studio-2017"></a><span data-ttu-id="c5756-247">Visual Studio 2017 docker-compose.yml ile çalışma</span><span class="sxs-lookup"><span data-stu-id="c5756-247">Working with docker-compose.yml in Visual Studio 2017</span></span>

<span data-ttu-id="c5756-248">Docker çözüm destek hizmeti proje bir Visual Studio çözümü ile Şekil 5-7'de gösterildiği gibi eklediğinizde, Visual Studio bir Dockerfile projenize ekler ve hizmet bölümü (Proje) docker-compose.yml dosyalarıyla çözümünüzde ekler.</span><span class="sxs-lookup"><span data-stu-id="c5756-248">When you add Docker solution support to a service project in a Visual Studio solution, as shown in Figure 5-7, Visual Studio adds a Dockerfile to your project, and it adds a service section (project) in your solution with the docker-compose.yml files.</span></span> <span data-ttu-id="c5756-249">Birden çok kapsayıcı çözümünüzü oluşturmaya başlamak için kolay bir yoludur.</span><span class="sxs-lookup"><span data-stu-id="c5756-249">It is an easy way to start composing your multiple-container solution.</span></span> <span data-ttu-id="c5756-250">Ardından, docker-compose.yml dosyaları açmak ve bunları ile ek özellikler güncelleştirin.</span><span class="sxs-lookup"><span data-stu-id="c5756-250">You can then open the docker-compose.yml files and update them with additional features.</span></span>

![](./media/image6.png)

<span data-ttu-id="c5756-251">**Şekil 5-7**.</span><span class="sxs-lookup"><span data-stu-id="c5756-251">**Figure 5-7**.</span></span> <span data-ttu-id="c5756-252">ASP.NET Core projesinde sağ tıklayarak Visual Studio 2017 Docker desteği ekleme</span><span class="sxs-lookup"><span data-stu-id="c5756-252">Adding Docker support in Visual Studio 2017 by right-clicking an ASP.NET Core project</span></span>

<span data-ttu-id="c5756-253">Visual Studio'da Docker desteği ekleme yalnızca Dockerfile projenize ekler, ancak yapılandırma bilgilerini çözüm düzeyinde ayarlanan birkaç genel docker-compose.yml dosyaları ekler.</span><span class="sxs-lookup"><span data-stu-id="c5756-253">Adding Docker support in Visual Studio not only adds the Dockerfile to your project, but adds the configuration information to several global docker-compose.yml files that are set at the solution level.</span></span>

<span data-ttu-id="c5756-254">Visual Studio çözümünüzde Docker destek ekledikten sonra Çözüm Gezgini'nde, Şekil 5-8'de gösterildiği gibi eklenen docker-compose.yml dosyaları içeren yeni bir düğüm (docker compose.dcproj proje dosyasında) de görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="c5756-254">After you add Docker support to your solution in Visual Studio, you will also see a new node (in the docker-compose.dcproj project file) in Solution Explorer that contains the added docker-compose.yml files, as shown in Figure 5-8.</span></span>

![](./media/image11.PNG)

<span data-ttu-id="c5756-255">**Şekil 5-8**.</span><span class="sxs-lookup"><span data-stu-id="c5756-255">**Figure 5-8**.</span></span> <span data-ttu-id="c5756-256">**Docker compose'u** Visual Studio 2017 Çözüm Gezgini'nde eklenen ağaç düğümü</span><span class="sxs-lookup"><span data-stu-id="c5756-256">The **docker-compose** tree node added in Visual Studio 2017 Solution Explorer</span></span>

<span data-ttu-id="c5756-257">Kullanarak tek docker-compose.yml dosyası ile birden çok kapsayıcı uygulama dağıtabilirsiniz docker compose'u komutu.</span><span class="sxs-lookup"><span data-stu-id="c5756-257">You could deploy a multi-container application with a single docker-compose.yml file by using the docker-compose up command.</span></span> <span data-ttu-id="c5756-258">Ortam (geliştirme üretim karşı) ve yürütme bağlı olarak değerleri kılabilir ancak, Visual Studio onları bir grup ekler türü (hata ayıklama ve yayın).</span><span class="sxs-lookup"><span data-stu-id="c5756-258">However, Visual Studio adds a group of them so you can override values depending on the environment (development versus production) and execution type (release versus debug).</span></span> <span data-ttu-id="c5756-259">Bu özellik, sonraki bölümlerde açıklandığı.</span><span class="sxs-lookup"><span data-stu-id="c5756-259">This capability will be explained in later sections.</span></span>

![](./media/image12.png)

## <a name="step-5-build-and-run-your-docker-application"></a><span data-ttu-id="c5756-260">5. adım.</span><span class="sxs-lookup"><span data-stu-id="c5756-260">Step 5.</span></span> <span data-ttu-id="c5756-261">Derleme ve Docker uygulamanızı çalıştırma</span><span class="sxs-lookup"><span data-stu-id="c5756-261">Build and run your Docker application</span></span>

<span data-ttu-id="c5756-262">Uygulamanız yalnızca tek bir kapsayıcı varsa, Docker ana (VM veya fiziksel sunucu) dağıtarak çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c5756-262">If your application only has a single container, you can run it by deploying it to your Docker host (VM or physical server).</span></span> <span data-ttu-id="c5756-263">Uygulamanız birden çok hizmet içeriyorsa, ancak bunu oluşan bir uygulama olarak ya da tek bir CLI komutu kullanarak dağıtabilirsiniz (docker-compose yukarı) ya da Visual Studio ile bu komutu kapsar altında kullanacak.</span><span class="sxs-lookup"><span data-stu-id="c5756-263">However, if your application contains multiple services, you can deploy it as a composed application, either using a single CLI command (docker-compose up), or with Visual Studio, which will use that command under the covers.</span></span> <span data-ttu-id="c5756-264">Farklı seçenekleri bakalım.</span><span class="sxs-lookup"><span data-stu-id="c5756-264">Let’s look at the different options.</span></span>

### <a name="option-a-running-a-single-container-with-docker-cli"></a><span data-ttu-id="c5756-265">Seçenek A: tek kapsayıcı Docker CLI ile çalıştırma</span><span class="sxs-lookup"><span data-stu-id="c5756-265">Option A: Running a single-container with Docker CLI</span></span>

<span data-ttu-id="c5756-266">Komutu, Şekil 5-9'olduğu gibi çalıştırın docker kullanarak bir Docker kapsayıcısı çalıştırabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="c5756-266">You can run a Docker container using the docker run command, as in Figure 5-9:</span></span>

```console
  docker run -t -d -p 80:5000 cesardl/netcore-webapi-microservice-docker:first
```

![](./media/image13.png)

<span data-ttu-id="c5756-267">**Şekil 5-9**.</span><span class="sxs-lookup"><span data-stu-id="c5756-267">**Figure 5-9**.</span></span> <span data-ttu-id="c5756-268">Komutu çalıştırın docker kullanarak bir Docker kapsayıcısı çalıştırma</span><span class="sxs-lookup"><span data-stu-id="c5756-268">Running a Docker container using the docker run command</span></span>

<span data-ttu-id="c5756-269">Bu durumda, komut kapsayıcısının dahili bağlantı noktası 5000 konak makine 80 noktasına bağlar.</span><span class="sxs-lookup"><span data-stu-id="c5756-269">In this case, the command binds the internal port 5000 of the container to port 80 of the host machine.</span></span> <span data-ttu-id="c5756-270">Bu, ana bilgisayar bağlantı noktası 80 üzerinde dinleme ve kapsayıcısı üzerinde 5000 numaralı bağlantı noktasına ileten anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="c5756-270">This means that the host is listening on port 80 and forwarding to port 5000 on the container.</span></span>

### <a name="option-b-running-a-multi-container-application"></a><span data-ttu-id="c5756-271">Seçenek B: birden çok kapsayıcı uygulama çalıştırma</span><span class="sxs-lookup"><span data-stu-id="c5756-271">Option B: Running a multi-container application</span></span>

<span data-ttu-id="c5756-272">Çoğu Kurumsal senaryoda, Docker uygulama birden fazla hizmet Şekil 5-10'da gösterildiği gibi bir çok kapsayıcı uygulamayı çalıştırmak gereken anlamı oluşacaktır.</span><span class="sxs-lookup"><span data-stu-id="c5756-272">In most enterprise scenarios, a Docker application will be composed of multiple services, which means you need to run a multi-container application, as shown in Figure 5-10.</span></span>

![](./media/image14.png)

<span data-ttu-id="c5756-273">**Şekil 5-10**.</span><span class="sxs-lookup"><span data-stu-id="c5756-273">**Figure 5-10**.</span></span> <span data-ttu-id="c5756-274">Docker kapsayıcıları dağıtılan VM</span><span class="sxs-lookup"><span data-stu-id="c5756-274">VM with Docker containers deployed</span></span>

#### <a name="running-a-multi-container-application-with-the-docker-cli"></a><span data-ttu-id="c5756-275">Birden çok kapsayıcı uygulama Docker CLI ile çalıştırma</span><span class="sxs-lookup"><span data-stu-id="c5756-275">Running a multi-container application with the Docker CLI</span></span>

<span data-ttu-id="c5756-276">Docker CLI ile birden çok kapsayıcı uygulamayı çalıştırmak için docker çalıştırabilirsiniz-komutu oluşturun.</span><span class="sxs-lookup"><span data-stu-id="c5756-276">To run a multi-container application with the Docker CLI, you can run the docker-compose up command.</span></span> <span data-ttu-id="c5756-277">Birden çok kapsayıcı uygulama dağıtmak için çözüm düzeyinde sahip olmanız bu komutu kullanan docker-compose.yml dosyası.</span><span class="sxs-lookup"><span data-stu-id="c5756-277">This command uses the docker-compose.yml file that you have at the solution level to deploy a multi-container application.</span></span> <span data-ttu-id="c5756-278">Şekil 5-11 komutu docker-compose.yml dosyası içeren ana proje dizininden çalışırken sonuçları gösterir.</span><span class="sxs-lookup"><span data-stu-id="c5756-278">Figure 5-11 shows the results when running the command from your main project directory, which contains the docker-compose.yml file.</span></span>

![](./media/image15.png)

<span data-ttu-id="c5756-279">**Şekil 5-11**.</span><span class="sxs-lookup"><span data-stu-id="c5756-279">**Figure 5-11**.</span></span> <span data-ttu-id="c5756-280">Örnek sonuçları çalıştırırken docker compose'u komutu</span><span class="sxs-lookup"><span data-stu-id="c5756-280">Example results when running the docker-compose up command</span></span>

<span data-ttu-id="c5756-281">Docker sonra-komutu çalıştırır oluşturma, uygulama ve ilgili kapsayıcılarında VM gösteriminde Şekil 5-10'de gösterildiği gibi Docker ana bilgisayara dağıtılır.</span><span class="sxs-lookup"><span data-stu-id="c5756-281">After the docker-compose up command runs, the application and its related containers are deployed into your Docker host, as illustrated in the VM representation in Figure 5-10.</span></span>

#### <a name="running-and-debugging-a-multi-container-application-with-visual-studio"></a><span data-ttu-id="c5756-282">Çalıştıran ve Visual Studio ile birden çok kapsayıcı uygulamasında hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="c5756-282">Running and debugging a multi-container application with Visual Studio</span></span> 

<span data-ttu-id="c5756-283">Visual Studio 2017 kullanarak bir çok kapsayıcı uygulaması çalıştıran daha basit alınamıyor.</span><span class="sxs-lookup"><span data-stu-id="c5756-283">Running a multi-container application using Visual Studio 2017 cannot get simpler.</span></span> <span data-ttu-id="c5756-284">Yalnızca birden çok kapsayıcı uygulama çalıştırabilirsiniz değil, ancak normal kesme noktalarını ayarlama doğrudan Visual Studio'dan tüm kapsayıcılarında hata ayıklama mümkün.</span><span class="sxs-lookup"><span data-stu-id="c5756-284">You can not only run the multi-container application, but you are able to debug all its containers directly from Visual Studio by setting regular breakpoints.</span></span>

<span data-ttu-id="c5756-285">Her bir çözüm içinde projeye Docker çözüm desteğini eklemeden önce belirtildiği gibi bu proje çalıştırmak veya tam çözüm aynı anda hata ayıklama imkan tanıyan genel (Çözüm düzeyi) docker-compose.yml dosyası içinde yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="c5756-285">As mentioned before, each time you add Docker solution support to a project within a solution, that project is configured in the global (solution-level) docker-compose.yml file, which lets you run or debug the whole solution at once.</span></span> <span data-ttu-id="c5756-286">Visual Studio Docker çözümü desteği etkin olan her proje için bir kapsayıcı başlatmak ve tüm iç adımları gerçekleştirdiğiniz (dotnet yayımladığınızda, docker yapı, vs.).</span><span class="sxs-lookup"><span data-stu-id="c5756-286">Visual Studio will start one container for each project that has Docker solution support enabled, and perform all the internal steps for you (dotnet publish, docker build, etc.).</span></span>

<span data-ttu-id="c5756-287">Burada önemli olan nokta Şekil 5-12'de gösterildiği gibi Visual Studio 2017 içinde ek bir olmasıdır **Docker** F5 anahtar eylemi için komutu.</span><span class="sxs-lookup"><span data-stu-id="c5756-287">The important point here is that, as shown in Figure 5-12, in Visual Studio 2017 there is an additional **Docker** command for the F5 key action.</span></span> <span data-ttu-id="c5756-288">Bu seçenek, çalıştırmak veya docker-compose.yml dosyalarında çözüm düzeyinde tanımlanan tüm kapsayıcıları çalıştırarak birden çok kapsayıcı uygulama hata ayıklama sağlar.</span><span class="sxs-lookup"><span data-stu-id="c5756-288">This option lets you run or debug a multi-container application by running all the containers that are defined in the docker-compose.yml files at the solution level.</span></span> <span data-ttu-id="c5756-289">Birden çok kapsayıcı çözümleri hata ayıklama özelliği anlamına gelir (kapsayıcı) farklı bir projedeki çeşitli kesme noktaları, her kesme noktası ayarlayabilirsiniz ve Visual Studio'da hata ayıklarken, farklı projelerde tanımlanan ve üzerinde çalışan kesme noktaları adresindeki durdurur farklı kapsayıcılar.</span><span class="sxs-lookup"><span data-stu-id="c5756-289">The ability to debug multiple-container solutions means that you can set several breakpoints, each breakpoint in a different project (container), and while debugging from Visual Studio you will stop at breakpoints defined in different projects and running on different containers.</span></span>

![](./media/image16.png)

<span data-ttu-id="c5756-290">**Şekil 5-12**.</span><span class="sxs-lookup"><span data-stu-id="c5756-290">**Figure 5-12**.</span></span> <span data-ttu-id="c5756-291">Visual Studio 2017 içinde çalışan birden çok kapsayıcı uygulamalar</span><span class="sxs-lookup"><span data-stu-id="c5756-291">Running multi-container apps in Visual Studio 2017</span></span>

### <a name="additional-resources"></a><span data-ttu-id="c5756-292">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="c5756-292">Additional resources</span></span>

-   <span data-ttu-id="c5756-293">**Bir ASP.NET kapsayıcısı uzak bir Docker konağına dağıtın**
    [*https://docs.microsoft.com/azure/vs-azure-tools-docker-hosting-web-apps-in-docker*](https://docs.microsoft.com/azure/vs-azure-tools-docker-hosting-web-apps-in-docker)</span><span class="sxs-lookup"><span data-stu-id="c5756-293">**Deploy an ASP.NET container to a remote Docker host**
[*https://docs.microsoft.com/azure/vs-azure-tools-docker-hosting-web-apps-in-docker*](https://docs.microsoft.com/azure/vs-azure-tools-docker-hosting-web-apps-in-docker)</span></span>

### <a name="a-note-about-testing-and-deploying-with-orchestrators"></a><span data-ttu-id="c5756-294">Test etme ve orchestrators ile dağıtma hakkında bir Not</span><span class="sxs-lookup"><span data-stu-id="c5756-294">A note about testing and deploying with orchestrators</span></span>

<span data-ttu-id="c5756-295">Docker-oluşturmanıza ve docker çalıştırma komutları (veya çalıştıran ve Visual Studio kapsayıcılarında hata ayıklama) kapsayıcıları geliştirme ortamında test etmek için yeterli.</span><span class="sxs-lookup"><span data-stu-id="c5756-295">The docker-compose up and docker run commands (or running and debugging the containers in Visual Studio) are adequate for testing containers in your development environment.</span></span> <span data-ttu-id="c5756-296">Ancak, bu yaklaşım, Docker kümeleri hedeflediğiniz ve Docker Swarm, Mesosphere DC/OS veya Kubernetes orchestrators gibi kullanmamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="c5756-296">But you should not use this approach if you are targeting Docker clusters and orchestrators like Docker Swarm, Mesosphere DC/OS, or Kubernetes.</span></span> <span data-ttu-id="c5756-297">Gibi bir küme kullanıyorsanız [Docker Swarm modu](https://docs.docker.com/engine/swarm/) dağıtıp gibi ek komutlarla test gerekir (Docker Windows CE ve Mac sürümünden itibaren kullanılabilir sürüm 1.12), [docker hizmet oluşturma](https://docs.docker.com/engine/reference/commandline/service_create/) için tek Hizmetleri.</span><span class="sxs-lookup"><span data-stu-id="c5756-297">If you are using a cluster like [Docker Swarm mode](https://docs.docker.com/engine/swarm/) (available in Docker CE for Windows and Mac since version 1.12), you need to deploy and test with additional commands like [docker service create](https://docs.docker.com/engine/reference/commandline/service_create/) for single services.</span></span> <span data-ttu-id="c5756-298">Birkaç kapsayıcıları için oluşan bir uygulama dağıtıyorsanız, kullandığınız [docker compose'u paket](https://docs.docker.com/compose/reference/bundle/) ve [docker dağıtmak myBundleFile](https://docs.docker.com/engine/reference/commandline/deploy/) olarak oluşturulmuş uygulama dağıtmak için bir *yığın*.</span><span class="sxs-lookup"><span data-stu-id="c5756-298">If you are deploying an application composed of several containers, you use [docker compose bundle](https://docs.docker.com/compose/reference/bundle/) and [docker deploy myBundleFile](https://docs.docker.com/engine/reference/commandline/deploy/) to deploy the composed application as a *stack*.</span></span> <span data-ttu-id="c5756-299">Daha fazla bilgi için blog gönderisine bakın [Tanıtımı Deneysel dağıtılmış uygulama paketleri](https://blog.docker.com/2016/06/docker-app-bundle/) Docker belgelerinde.</span><span class="sxs-lookup"><span data-stu-id="c5756-299">For more information, see the blog post [Introducing Experimental Distributed Application Bundles](https://blog.docker.com/2016/06/docker-app-bundle/) in the Docker documentation.</span></span> <span data-ttu-id="c5756-300">Docker sitesinde.</span><span class="sxs-lookup"><span data-stu-id="c5756-300">on the Docker site.</span></span>

<span data-ttu-id="c5756-301">İçin [DC/OS](https://mesosphere.com/blog/2015/09/02/dcos-cli-command-line-tool-datacenter/) ve [Kubernetes](http://kubernetes.io/docs/user-guide/deployments/) farklı dağıtım komutları ve komut dosyaları da kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="c5756-301">For [DC/OS](https://mesosphere.com/blog/2015/09/02/dcos-cli-command-line-tool-datacenter/) and [Kubernetes](http://kubernetes.io/docs/user-guide/deployments/) you would use different deployment commands and scripts as well.</span></span>

![](./media/image17.png)

## <a name="step-6-test-your-docker-application-using-your-local-docker-host"></a><span data-ttu-id="c5756-302">6. adım.</span><span class="sxs-lookup"><span data-stu-id="c5756-302">Step 6.</span></span> <span data-ttu-id="c5756-303">Yerel Docker ana bilgisayarınız kullanarak Docker uygulamanızı test etme</span><span class="sxs-lookup"><span data-stu-id="c5756-303">Test your Docker application using your local Docker host</span></span>

<span data-ttu-id="c5756-304">Bu adımı uygulamanız yapılması bağlı olarak değişir.</span><span class="sxs-lookup"><span data-stu-id="c5756-304">This step will vary depending on what your application is doing.</span></span> <span data-ttu-id="c5756-305">Bir tek kapsayıcı ya da hizmet olarak dağıtılan basit bir .NET Core Web uygulama, hizmet Docker ana bilgisayardaki bir tarayıcı açıp Şekil 5-13'te gösterildiği gibi bu siteye gezinme erişebilir.</span><span class="sxs-lookup"><span data-stu-id="c5756-305">In a simple .NET Core Web application that is deployed as a single container or service, you can access the service by opening a browser on the Docker host and navigating to that site as shown in Figure 5-13.</span></span> <span data-ttu-id="c5756-306">(Dockerfile yapılandırmasında bir bağlantı noktası 80'dışındaki herhangi bir ana bilgisayarda kapsayıcı eşlendiği, ana bilgisayar bağlantı noktası URL'de içerir.)</span><span class="sxs-lookup"><span data-stu-id="c5756-306">(If the configuration in the Dockerfile maps the container to a port on the host that is anything other than 80, include the host port in the URL.)</span></span>

![](./media/image18.png)

<span data-ttu-id="c5756-307">**Şekil 5-13**.</span><span class="sxs-lookup"><span data-stu-id="c5756-307">**Figure 5-13**.</span></span> <span data-ttu-id="c5756-308">Docker uygulamanızı localhost kullanarak yerel olarak test örneği</span><span class="sxs-lookup"><span data-stu-id="c5756-308">Example of testing your Docker application locally using localhost</span></span>

<span data-ttu-id="c5756-309">Localhost için Docker işaret etmiyor, IP ana bilgisayar (Bu varsayılan Docker CE kullanırken, gerekir), hizmetinize gezinmek için makinenizin ağ kartı IP adresini kullanın.</span><span class="sxs-lookup"><span data-stu-id="c5756-309">If localhost is not pointing to the Docker host IP (by default, when using Docker CE, it should), to navigate to your service, use the IP address of your machine’s network card.</span></span>

<span data-ttu-id="c5756-310">Bu URL tarayıcıda tartışılan belirli kapsayıcı örnek için 80 numaralı bağlantı noktasını kullandığını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="c5756-310">Note that this URL in the browser uses port 80 for the particular container example being discussed.</span></span> <span data-ttu-id="c5756-311">Nasıl bu komutu çalıştırmak docker ile bir önceki adımda açıklandığı gibi dağıtılmış olduğundan ancak, dahili olarak istekleri 5000 bağlantı noktasına yönlendirilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c5756-311">However, internally the requests are being redirected to port 5000, because that was how it was deployed with the docker run command, as explained in a previous step.</span></span>

<span data-ttu-id="c5756-312">Ayrıca, Şekil 5-14'te gösterildiği gibi terminalde, curl kullanarak uygulamayı test edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c5756-312">You can also test the application using curl from the terminal, as shown in Figure 5-14.</span></span> <span data-ttu-id="c5756-313">Windows Docker yüklemesinde Docker ana bilgisayar IP her zaman makinenizin gerçek IP adresinin yanı sıra 10.0.75.1 varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="c5756-313">In a Docker installation on Windows, the default Docker Host IP is always 10.0.75.1 in addition to your machine’s actual IP address.</span></span>

![](./media/image19.png)

<span data-ttu-id="c5756-314">**Şekil 5-14**.</span><span class="sxs-lookup"><span data-stu-id="c5756-314">**Figure 5-14**.</span></span> <span data-ttu-id="c5756-315">Curl kullanarak yerel olarak Docker uygulamanızı test örneği</span><span class="sxs-lookup"><span data-stu-id="c5756-315">Example of testing your Docker application locally using curl</span></span>

### <a name="testing-and-debugging-containers-with-visual-studio-2017"></a><span data-ttu-id="c5756-316">Test ve Visual Studio 2017 ile kapsayıcıları hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="c5756-316">Testing and debugging containers with Visual Studio 2017</span></span>

<span data-ttu-id="c5756-317">Kapsayıcıları çalışırken olduğu gibi çalıştıran ve Visual Studio 2017 kapsayıcılarla hata ayıklama, benzer şekilde .NET uygulama ayıklayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c5756-317">When running and debugging the containers with Visual Studio 2017, you can debug the .NET application in much the same way as you would when running without containers.</span></span>

### <a name="testing-and-debugging-without-visual-studio"></a><span data-ttu-id="c5756-318">Test ve hata ayıklama Visual Studio</span><span class="sxs-lookup"><span data-stu-id="c5756-318">Testing and debugging without Visual Studio</span></span>

<span data-ttu-id="c5756-319">Düzenleyici/CLI yaklaşımı kullanarak geliştiriyorsanız kapsayıcılarında hata ayıklama daha zordur ve izlemeleri oluşturarak hata ayıklama isteyeceksiniz.</span><span class="sxs-lookup"><span data-stu-id="c5756-319">If you are developing using the editor/CLI approach, debugging containers is more difficult and you will want to debug by generating traces.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="c5756-320">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="c5756-320">Additional resources</span></span>

-   <span data-ttu-id="c5756-321">**Yerel bir Docker kapsayıcısı uygulamalarında hata ayıklama**
    [*https://docs.microsoft.com/azure/vs-azure-tools-docker-edit-and-refresh*](https://docs.microsoft.com/azure/vs-azure-tools-docker-edit-and-refresh)</span><span class="sxs-lookup"><span data-stu-id="c5756-321">**Debugging apps in a local Docker container**
[*https://docs.microsoft.com/azure/vs-azure-tools-docker-edit-and-refresh*](https://docs.microsoft.com/azure/vs-azure-tools-docker-edit-and-refresh)</span></span>

-   <span data-ttu-id="c5756-322">**Steve Lasker. Yapı, hata ayıklama, Docker ile ASP.NET Core uygulamaları dağıtma.**</span><span class="sxs-lookup"><span data-stu-id="c5756-322">**Steve Lasker. Build, Debug, Deploy ASP.NET Core Apps with Docker.**</span></span> <span data-ttu-id="c5756-323">Video.</span><span class="sxs-lookup"><span data-stu-id="c5756-323">Video.</span></span>
    [*https://channel9.msdn.com/Events/Visual-Studio/Visual-Studio-2017-Launch/T115*](https://channel9.msdn.com/Events/Visual-Studio/Visual-Studio-2017-Launch/T115)

## <a name="simplified-workflow-when-developing-containers-with-visual-studio"></a><span data-ttu-id="c5756-324">Visual Studio ile kapsayıcıları geliştirirken Basitleştirilmiş iş akışı</span><span class="sxs-lookup"><span data-stu-id="c5756-324">Simplified workflow when developing containers with Visual Studio</span></span>

<span data-ttu-id="c5756-325">Visual Studio kullanarak Düzenleyicisi/CLI yaklaşımı kullanırsanız, çok daha basit olduğunda etkili bir şekilde, iş akışı.</span><span class="sxs-lookup"><span data-stu-id="c5756-325">Effectively, the workflow when using Visual Studio is a lot simpler than if you use the editor/CLI approach.</span></span> <span data-ttu-id="c5756-326">Dockerfile Docker tarafından gerekli olan adımları çoğunu ilgili ve gizli ya da Visual Studio tarafından Şekil 5-15'te gösterildiği gibi Basitleştirilmiş docker-compose.yml dosyaları.</span><span class="sxs-lookup"><span data-stu-id="c5756-326">Most of the steps required by Docker related to the Dockerfile and docker-compose.yml files are hidden or simplified by Visual Studio, as shown in Figure 5-15.</span></span>

![](./media/image20.png)

<span data-ttu-id="c5756-327">**Şekil 5-15**.</span><span class="sxs-lookup"><span data-stu-id="c5756-327">**Figure 5-15**.</span></span> <span data-ttu-id="c5756-328">Visual Studio ile geliştirirken Basitleştirilmiş iş akışı</span><span class="sxs-lookup"><span data-stu-id="c5756-328">Simplified workflow when developing with Visual Studio</span></span>

<span data-ttu-id="c5756-329">Ayrıca, adım 2 (Docker destek eklenmesi projelerinize) yalnızca bir kez gerçekleştirmek için gerekir.</span><span class="sxs-lookup"><span data-stu-id="c5756-329">In addition, you need to perform step 2 (adding Docker support to your projects) just once.</span></span> <span data-ttu-id="c5756-330">Bu nedenle, iş akışı .NET herhangi bir geliştirme için kullanılırken normal geliştirme görevlerinizi benzer.</span><span class="sxs-lookup"><span data-stu-id="c5756-330">Therefore, the workflow is similar to your usual development tasks when using .NET for any other development.</span></span> <span data-ttu-id="c5756-331">Kapak (görüntü oluşturma işlemi, hangi kullanmakta olduğunuz temel görüntüler, kapsayıcıları, vb. dağıtımını) altında ve bazen de davranışları özelleştirmek için Dockerfile veya docker-compose.yml dosyasını düzenlemeniz gerekir neler olduğunu bilmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="c5756-331">You need to know what is going on under the covers (the image build process, what base images you are using, deployment of containers, etc.) and sometimes you will also need to edit the Dockerfile or docker-compose.yml file to customize behaviors.</span></span> <span data-ttu-id="c5756-332">Ancak, işlerin çoğunu büyük ölçüde basitleştirilmiştir çok daha verimli hale Visual Studio kullanarak.</span><span class="sxs-lookup"><span data-stu-id="c5756-332">But most of the work is greatly simplified by using Visual Studio, making you a lot more productive.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="c5756-333">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="c5756-333">Additional resources</span></span>

-   <span data-ttu-id="c5756-334">**Steve Lasker. Visual Studio 2017 ile .NET docker geliştirme**
    [*https://channel9.msdn.com/Events/Visual-Studio/Visual-Studio-2017-Launch/T111*](https://channel9.msdn.com/Events/Visual-Studio/Visual-Studio-2017-Launch/T111)</span><span class="sxs-lookup"><span data-stu-id="c5756-334">**Steve Lasker. .NET Docker Development with Visual Studio 2017**
[*https://channel9.msdn.com/Events/Visual-Studio/Visual-Studio-2017-Launch/T111*](https://channel9.msdn.com/Events/Visual-Studio/Visual-Studio-2017-Launch/T111)</span></span>

-   <span data-ttu-id="c5756-335">**Gamze T. Fritz. .NET Core uygulaması bir kapsayıcıda yeni Docker araçları ile Visual Studio için yerleştirin.**
    [*https://blogs.msdn.microsoft.com/webdev/2016/11/16/new-docker-tools-for-visual-studio/*](https://blogs.msdn.microsoft.com/webdev/2016/11/16/new-docker-tools-for-visual-studio/)</span><span class="sxs-lookup"><span data-stu-id="c5756-335">**Jeffrey T. Fritz. Put a .NET Core App in a Container with the new Docker Tools for Visual Studio**
[*https://blogs.msdn.microsoft.com/webdev/2016/11/16/new-docker-tools-for-visual-studio/*](https://blogs.msdn.microsoft.com/webdev/2016/11/16/new-docker-tools-for-visual-studio/)</span></span>

## <a name="using-powershell-commands-in-a-dockerfile-to-set-up-windows-containers"></a><span data-ttu-id="c5756-336">Windows kapsayıcıları ayarlamak için bir Dockerfile PowerShell komutlarını kullanma</span><span class="sxs-lookup"><span data-stu-id="c5756-336">Using PowerShell commands in a Dockerfile to set up Windows Containers</span></span> 

<span data-ttu-id="c5756-337">[Windows kapsayıcıları](https://msdn.microsoft.com/en-us/virtualization/windowscontainers/about/about_overview) var olan Windows uygulamalarınız Docker görüntülere dönüştürmek ve Docker ekosistemi geri kalanı ile aynı araçlarıyla dağıtmadan olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="c5756-337">[Windows Containers](https://msdn.microsoft.com/en-us/virtualization/windowscontainers/about/about_overview) allow you to convert your existing Windows applications into Docker images and deploy them with the same tools as the rest of the Docker ecosystem.</span></span> <span data-ttu-id="c5756-338">Windows kapsayıcılar kullanmak için aşağıdaki örnekte gösterildiği gibi Dockerfile, PowerShell komutlarını çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="c5756-338">To use Windows Containers, you run PowerShell commands in the Dockerfile, as shown in the following example:</span></span>

```Dockerfile
FROM microsoft/windowsservercore
  
LABEL Description="IIS" Vendor="Microsoft" Version="10"
  
RUN powershell -Command Add-WindowsFeature Web-Server
  
CMD [ "ping", "localhost", "-t" ]
```

<span data-ttu-id="c5756-339">Bu durumda, biz bir Windows Server Core temel görüntü (FROM ayarı) kullanarak ve PowerShell komutuyla (çalışma ayarı) IIS yükleniyor.</span><span class="sxs-lookup"><span data-stu-id="c5756-339">In this case, we are using a Windows Server Core base image (the FROM setting) and installing IIS with a PowerShell command (the RUN setting).</span></span> <span data-ttu-id="c5756-340">Benzer şekilde, ASP.NET 4.x, .NET 4.6 veya herhangi bir Windows yazılımı gibi ek bileşenleri ayarlamak için PowerShell komutlarını kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c5756-340">In a similar way, you could also use PowerShell commands to set up additional components like ASP.NET 4.x, .NET 4.6, or any other Windows software.</span></span> <span data-ttu-id="c5756-341">Örneğin, bir Dockerfile aşağıdaki komutta ASP.NET 4.5 ayarlar:</span><span class="sxs-lookup"><span data-stu-id="c5756-341">For example, the following command in a Dockerfile sets up ASP.NET 4.5:</span></span>

```Dockerfile
RUN powershell add-windowsfeature web-asp-net45
```

### <a name="additional-resources"></a><span data-ttu-id="c5756-342">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="c5756-342">Additional resources</span></span>

-   <span data-ttu-id="c5756-343">**aspnet-docker/Dockerfile.**</span><span class="sxs-lookup"><span data-stu-id="c5756-343">**aspnet-docker/Dockerfile.**</span></span> <span data-ttu-id="c5756-344">Windows özellikleri içerecek şekilde dockerfiles çalıştırmak için Powershell komutlarını örnek.</span><span class="sxs-lookup"><span data-stu-id="c5756-344">Example Powershell commands to run from dockerfiles to include Windows features.</span></span>
    [*https://github.com/Microsoft/aspnet-docker/blob/master/4.6.2/Dockerfile*](https://github.com/Microsoft/aspnet-docker/blob/master/4.6.2/Dockerfile)

>[!div class="step-by-step"]
<span data-ttu-id="c5756-345">[Önceki] (index.md) [sonraki] (.. / net-core-single-containers-linux-windows-server-hosts/index.md)</span><span class="sxs-lookup"><span data-stu-id="c5756-345">[Previous] (index.md) [Next] (../net-core-single-containers-linux-windows-server-hosts/index.md)</span></span>
