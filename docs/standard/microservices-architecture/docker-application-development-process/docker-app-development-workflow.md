---
title: Docker uygulamaları için geliştirme iş akışı
description: Kapsayıcılı .NET uygulamaları için .NET mikro hizmet mimarisi | Docker uygulamaları için geliştirme iş akışı
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/18/2017
ms.openlocfilehash: b7115530c44321dc2a10be3996c14429591b611f
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43864832"
---
# <a name="development-workflow-for-docker-apps"></a><span data-ttu-id="bed48-103">Docker uygulamaları için geliştirme iş akışı</span><span class="sxs-lookup"><span data-stu-id="bed48-103">Development workflow for Docker apps</span></span>

<span data-ttu-id="bed48-104">Burada geliştirici kendi tercih edilen dili kullanarak uygulama kodları ve yerel olarak test her geliştiricinin makine uygulama geliştirme yaşam döngüsünü başlatır.</span><span class="sxs-lookup"><span data-stu-id="bed48-104">The application development lifecycle starts at each developer’s machine, where the developer codes the application using their preferred language and tests it locally.</span></span> <span data-ttu-id="bed48-105">Hangi dil, çerçeve ve geliştirici seçer, bu iş akışı ile platform ne olursa olsun Geliştirici her zaman geliştirme ve test Docker kapsayıcıları, ancak bunun yerel olarak yapılması.</span><span class="sxs-lookup"><span data-stu-id="bed48-105">No matter which language, framework, and platform the developer chooses, with this workflow, the developer is always developing and testing Docker containers, but doing so locally.</span></span>

<span data-ttu-id="bed48-106">Her kapsayıcı (bir Docker görüntüsü örneği), aşağıdaki bileşenleri içerir:</span><span class="sxs-lookup"><span data-stu-id="bed48-106">Each container (an instance of a Docker image) includes the following components:</span></span>

-   <span data-ttu-id="bed48-107">Bir işletim sistemi seçimi olduğu (örneğin, bir Linux dağıtımı, Windows Nano sunucu veya Windows Server Core).</span><span class="sxs-lookup"><span data-stu-id="bed48-107">An operating system selection (for example, a Linux distribution, Windows Nano Server, or Windows Server Core).</span></span>

-   <span data-ttu-id="bed48-108">Geliştirici (uygulama ikilileri, vb.) tarafından eklenen dosyalar.</span><span class="sxs-lookup"><span data-stu-id="bed48-108">Files added by the developer (application binaries, etc.).</span></span>

-   <span data-ttu-id="bed48-109">Yapılandırma bilgileri (ortam ayarlarını ve bağımlılıklarını).</span><span class="sxs-lookup"><span data-stu-id="bed48-109">Configuration information (environment settings and dependencies).</span></span>

## <a name="workflow-for-developing-docker-container-based-applications"></a><span data-ttu-id="bed48-110">Docker kapsayıcı tabanlı uygulamaları geliştirmek için iş akışı</span><span class="sxs-lookup"><span data-stu-id="bed48-110">Workflow for developing Docker container-based applications</span></span>

<span data-ttu-id="bed48-111">Bu bölümde açıklanmaktadır *iç döngü* Docker kapsayıcı tabanlı uygulamaları için geliştirme iş akışı.</span><span class="sxs-lookup"><span data-stu-id="bed48-111">This section describes the *inner-loop* development workflow for Docker container-based applications.</span></span> <span data-ttu-id="bed48-112">İç döngü iş akışı, daha geniş DevOps iş akışını dikkate alarak değildir ve yalnızca geliştiricinin bilgisayarında geliştirme çalışmanın odaklanır anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="bed48-112">The inner-loop workflow means it is not taking into account the broader DevOps workflow and just focuses on the development work done on the developer’s computer.</span></span> <span data-ttu-id="bed48-113">Ortamı ayarlamak için ilk adımlarında bu yalnızca bir kez gerçekleştirilir dahil değildir.</span><span class="sxs-lookup"><span data-stu-id="bed48-113">The initial steps to set up the environment are not included, since those are done only once.</span></span>

<span data-ttu-id="bed48-114">Uygulamanın kendi Hizmetleri ve ek kitaplıklar (bağımlılıklar) karakterlerinden oluşur.</span><span class="sxs-lookup"><span data-stu-id="bed48-114">An application is composed of your own services plus additional libraries (dependencies).</span></span> <span data-ttu-id="bed48-115">Aşağıda, genellikle bir Docker uygulaması oluştururken Şekil 5-1'de gösterildiği gibi temel adımlar verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="bed48-115">The following are the basic steps you usually take when building a Docker application, as illustrated in Figure 5-1.</span></span>

![](./media/image1.png)

<span data-ttu-id="bed48-116">**Şekil 5-1.**</span><span class="sxs-lookup"><span data-stu-id="bed48-116">**Figure 5-1.**</span></span> <span data-ttu-id="bed48-117">Kapsayıcılı Docker uygulamaları geliştirmeye yönelik adım adım iş akışı</span><span class="sxs-lookup"><span data-stu-id="bed48-117">Step-by-step workflow for developing Docker containerized apps</span></span>

<span data-ttu-id="bed48-118">Bu kılavuzdaki tüm bu işlemi ayrıntılı olarak verilmiştir ve önemli adım her bir Visual Studio ortamında odaklanarak açıklanmıştır.</span><span class="sxs-lookup"><span data-stu-id="bed48-118">In this guide, this whole process is detailed and every major step is explained by focusing on a Visual Studio environment.</span></span>

<span data-ttu-id="bed48-119">Bir düzenleyici/CLI geliştirme yaklaşımını (örneğin, Visual Studio Code ve Docker CLI'yı MacOS ya da Windows) kullandığınızda, her adım genellikle Visual Studio kullanıyorsanız, daha ayrıntılı biçimde bilmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="bed48-119">When you are using an editor/CLI development approach (for example, Visual Studio Code plus Docker CLI on macOS or Windows), you need to know every step, generally in more detail than if you are using Visual Studio.</span></span> <span data-ttu-id="bed48-120">CLI ortamda çalışma hakkında daha fazla ayrıntı için e-kitap başvurun [Microsoft Platforms ve araçlarla kapsayıcılı Docker uygulaması yaşam döngüsü](https://aka.ms/dockerlifecycleebook/).</span><span class="sxs-lookup"><span data-stu-id="bed48-120">For more details about working in a CLI environment, refer to the e-book [Containerized Docker Application lifecycle with Microsoft Platforms and Tools](https://aka.ms/dockerlifecycleebook/).</span></span>

<span data-ttu-id="bed48-121">Visual Studio 2015 veya Visual Studio 2017'yi kullandığınızda, bu adımların çoğunu sizin yerinize üretkenliğinizi önemli ölçüde artıran işlenir.</span><span class="sxs-lookup"><span data-stu-id="bed48-121">When you are using Visual Studio 2015 or Visual Studio 2017, many of those steps are handled for you, which dramatically improves your productivity.</span></span> <span data-ttu-id="bed48-122">Visual Studio 2017 kullanılarak ve çok kapsayıcılı uygulamaları hedefleyen bu özellikle doğrudur.</span><span class="sxs-lookup"><span data-stu-id="bed48-122">This is especially true when you are using Visual Studio 2017 and targeting multi-container applications.</span></span> <span data-ttu-id="bed48-123">Örneğin, yalnızca tek bir tıklatmayla projelerinize uygulamanız için yapılandırma ile Dockerfile ve docker-compose.yml dosyası Visual Studio ekler.</span><span class="sxs-lookup"><span data-stu-id="bed48-123">For instance, with just one mouse click, Visual Studio adds the Dockerfile and docker-compose.yml file to your projects with the configuration for your application.</span></span> <span data-ttu-id="bed48-124">Visual Studio'da uygulamayı çalıştırdığınızda, Docker görüntüsünü oluşturur ve çok kapsayıcılı bir uygulama doğrudan Docker'da çalıştırılır; bile aynı anda birden fazla kapsayıcılar ayıklamanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="bed48-124">When you run the application in Visual Studio, it builds the Docker image and runs the multi-container application directly in Docker; it even allows you to debug several containers at once.</span></span> <span data-ttu-id="bed48-125">Bu özellikler, geliştirme hızını çok artırır.</span><span class="sxs-lookup"><span data-stu-id="bed48-125">These features will boost your development speed.</span></span>

<span data-ttu-id="bed48-126">Yalnızca Visual Studio bu adımlar otomatik hale getirir ancak neler olduğunu bilmeniz gerekmez gelmez üzerinde underneath Docker ile.</span><span class="sxs-lookup"><span data-stu-id="bed48-126">However, just because Visual Studio makes those steps automatic does not mean that you do not need to know what is going on underneath with Docker.</span></span> <span data-ttu-id="bed48-127">Bu nedenle, aşağıdaki kılavuzda, size her adım ayrıntılı olarak açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="bed48-127">Therefore, in the guidance that follows, we detail every step.</span></span>

![](./media/image2.png)

## <a name="step-1-start-coding-and-create-your-initial-application-or-service-baseline"></a><span data-ttu-id="bed48-128">Adım 1.</span><span class="sxs-lookup"><span data-stu-id="bed48-128">Step 1.</span></span> <span data-ttu-id="bed48-129">Kodlamaya başlayın ve ilk uygulama veya hizmet taban çizgisi oluşturma</span><span class="sxs-lookup"><span data-stu-id="bed48-129">Start coding and create your initial application or service baseline</span></span>

<span data-ttu-id="bed48-130">Docker uygulaması geliştirmek, Docker olmadan uygulama geliştirme şekilde benzerdir.</span><span class="sxs-lookup"><span data-stu-id="bed48-130">Developing a Docker application is similar to the way you develop an application without Docker.</span></span> <span data-ttu-id="bed48-131">Docker için geliştirmeye devam ederken, dağıtan ve uygulamanızı veya yerel ortamınızda Docker kapsayıcıları içinde çalışan hizmetleri test etme, farktır.</span><span class="sxs-lookup"><span data-stu-id="bed48-131">The difference is that while developing for Docker, you are deploying and testing your application or services running within Docker containers in your local environment.</span></span> <span data-ttu-id="bed48-132">Kapsayıcı, bir Linux kapsayıcı ya da bir Windows kapsayıcı olabilir.</span><span class="sxs-lookup"><span data-stu-id="bed48-132">The container can be either a Linux container or a Windows container.</span></span>

### <a name="set-up-your-local-environment-with-visual-studio"></a><span data-ttu-id="bed48-133">Visual Studio ile yerel ortamınızı ayarlayın</span><span class="sxs-lookup"><span data-stu-id="bed48-133">Set up your local environment with Visual Studio</span></span>

<span data-ttu-id="bed48-134">Başlamak için sahip olduğunuzdan emin olun [Docker Community Edition'ı (CE)](https://www.docker.com/community-edition) aşağıdaki yönergelerinde açıklandığı gibi yüklü Windows için:</span><span class="sxs-lookup"><span data-stu-id="bed48-134">To begin, make sure you have [Docker Community Edition (CE)](https://www.docker.com/community-edition) for Windows installed, as explained in the following instructions:</span></span>

[<span data-ttu-id="bed48-135">İçin Docker CE Windows ile çalışmaya başlama</span><span class="sxs-lookup"><span data-stu-id="bed48-135">Get started with Docker CE for Windows</span></span>](https://docs.docker.com/docker-for-windows/)

<span data-ttu-id="bed48-136">Ayrıca, Visual Studio 2017 gerekir.</span><span class="sxs-lookup"><span data-stu-id="bed48-136">In addition, you will need Visual Studio 2017 installed.</span></span> <span data-ttu-id="bed48-137">Visual Studio 2017 desteği Docker, kapsayıcılar hata ayıklama desteği gibi daha gelişmiş üzerinden Visual Studio 2015 için Docker eklentisi, Visual Studio Araçları ile tercih edilen olmasıdır.</span><span class="sxs-lookup"><span data-stu-id="bed48-137">This is preferred over Visual Studio 2015 with the Visual Studio Tools for Docker add-in, because Visual Studio 2017 has more advanced support for Docker, like support for debugging containers.</span></span> <span data-ttu-id="bed48-138">Visual Studio 2017 için Docker araçları seçtiyseniz içerir **.NET Core ve Docker** iş yükü yüklenirken, Şekil 5-2'de gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="bed48-138">Visual Studio 2017 includes the tooling for Docker if you selected the **.NET Core and Docker** workload during installation, as shown in Figure 5-2.</span></span>

![](./media/image3.png)

<span data-ttu-id="bed48-139">**Şekil 5-2**.</span><span class="sxs-lookup"><span data-stu-id="bed48-139">**Figure 5-2**.</span></span> <span data-ttu-id="bed48-140">Seçme **.NET Core ve Docker** Visual Studio 2017 Kurulum sırasında iş yükü</span><span class="sxs-lookup"><span data-stu-id="bed48-140">Selecting the **.NET Core and Docker** workload during Visual Studio 2017 setup</span></span>

<span data-ttu-id="bed48-141">Uygulamanızda Docker'ı etkinleştirme ve Docker sınama dağıtımı önce (genellikle, .NET Core kapsayıcıları kullanmayı planlıyorsanız) düz .NET uygulamanızda kodlamaya başlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bed48-141">You can start coding your application in plain .NET (usually in .NET Core if you are planning to use containers) even before enabling Docker in your application and deploying and testing in Docker.</span></span> <span data-ttu-id="bed48-142">Ancak, üzerinde Docker olabildiğince çabuk, çünkü gerçek ortam olacak ve sorunları olabildiğince çabuk bulunabileceğini çalışma başlangıç önerilir.</span><span class="sxs-lookup"><span data-stu-id="bed48-142">However, it is recommended that you start working on Docker as soon as possible, because that will be the real environment and any issues can be discovered as soon as possible.</span></span> <span data-ttu-id="bed48-143">Visual Studio, bu nedenle, neredeyse saydam hissettiği Docker'la çalışmak kolaylaştırır çünkü bu teşvik edilir — çok kapsayıcılı uygulamalar Visual Studio'dan hata ayıklama sırasında en iyi örnek.</span><span class="sxs-lookup"><span data-stu-id="bed48-143">This is encouraged because Visual Studio makes it so easy to work with Docker that it almost feels transparent—the best example when debugging multi-container applications from Visual Studio.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="bed48-144">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="bed48-144">Additional resources</span></span>

-   <span data-ttu-id="bed48-145">**İçin Docker CE Windows ile çalışmaya başlama**
    [*https://docs.docker.com/docker-for-windows/*](https://docs.docker.com/docker-for-windows/)</span><span class="sxs-lookup"><span data-stu-id="bed48-145">**Get started with Docker CE for Windows**
[*https://docs.docker.com/docker-for-windows/*](https://docs.docker.com/docker-for-windows/)</span></span>

-   <span data-ttu-id="bed48-146">**Visual Studio 2017**
    [*https://visualstudio.microsoft.com/downloads/*](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs)</span><span class="sxs-lookup"><span data-stu-id="bed48-146">**Visual Studio 2017**
[*https://visualstudio.microsoft.com/downloads/*](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs)</span></span>

![](./media/image4.png)

## <a name="step-2-create-a-dockerfile-related-to-an-existing-net-base-image"></a><span data-ttu-id="bed48-147">Adım 2.</span><span class="sxs-lookup"><span data-stu-id="bed48-147">Step 2.</span></span> <span data-ttu-id="bed48-148">Mevcut bir .NET temel görüntü için ilgili bir Dockerfile'ı oluşturma</span><span class="sxs-lookup"><span data-stu-id="bed48-148">Create a Dockerfile related to an existing .NET base image</span></span>

<span data-ttu-id="bed48-149">Derlemek istediğiniz her özel görüntü için bir Dockerfile ihtiyacınız; Ayrıca Visual Studio veya el ile Docker CLI'yı kullanarak otomatik olarak dağıtıp dağıtmamak dağıtılması için her kapsayıcı için bir Dockerfile gerekir (docker run ve docker-compose komutları).</span><span class="sxs-lookup"><span data-stu-id="bed48-149">You need a Dockerfile for each custom image you want to build; you also need a Dockerfile for each container to be deployed, whether you deploy automatically from Visual Studio or manually using the Docker CLI (docker run and docker-compose commands).</span></span> <span data-ttu-id="bed48-150">Uygulamanızda tek bir özel hizmet varsa, tek bir Dockerfile gerekir.</span><span class="sxs-lookup"><span data-stu-id="bed48-150">If your application contains a single custom service, you need a single Dockerfile.</span></span> <span data-ttu-id="bed48-151">Uygulamanız birden çok hizmeti (olduğu gibi bir mikro hizmetler mimarisinde) içeriyorsa, her hizmet için bir Dockerfile gerekir.</span><span class="sxs-lookup"><span data-stu-id="bed48-151">If your application contains multiple services (as in a microservices architecture), you need one Dockerfile for each service.</span></span>

<span data-ttu-id="bed48-152">Dockerfile, uygulamanızın veya hizmetinizin kök klasöründe yer alır.</span><span class="sxs-lookup"><span data-stu-id="bed48-152">The Dockerfile is placed in the root folder of your application or service.</span></span> <span data-ttu-id="bed48-153">Bu, Docker ayarlama ve bir kapsayıcıdaki uygulama veya hizmetinizin çalıştırma bildiririz komutlar içerir.</span><span class="sxs-lookup"><span data-stu-id="bed48-153">It contains the commands that tell Docker how to set up and run your application or service in a container.</span></span> <span data-ttu-id="bed48-154">El ile bir Dockerfile içinde kod oluşturma ve birlikte .NET bağımlılıklarınızı projenize ekleyin.</span><span class="sxs-lookup"><span data-stu-id="bed48-154">You can manually create a Dockerfile in code and add it to your project along with your .NET dependencies.</span></span>

<span data-ttu-id="bed48-155">Bu görevi, Visual Studio ve araçları için Docker ile yalnızca birkaç tıklamayla gerektirir.</span><span class="sxs-lookup"><span data-stu-id="bed48-155">With Visual Studio and its tools for Docker, this task requires only a few mouse clicks.</span></span> <span data-ttu-id="bed48-156">Visual Studio 2017'de yeni bir proje oluşturduğunuzda, adlı bir seçenek yoktur **kapsayıcı etkinleştir (Docker) desteği**Şekil 5-3'te gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="bed48-156">When you create a new project in Visual Studio 2017, there is an option named **Enable Container (Docker) Support**, as shown in Figure 5-3.</span></span>

![](./media/image5.png)

<span data-ttu-id="bed48-157">**Şekil 5-3**.</span><span class="sxs-lookup"><span data-stu-id="bed48-157">**Figure 5-3**.</span></span> <span data-ttu-id="bed48-158">Visual Studio 2017'de yeni bir proje oluştururken, Docker desteğini etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="bed48-158">Enabling Docker Support when creating a new project in Visual Studio 2017</span></span>

<span data-ttu-id="bed48-159">Visual Studio proje dosyanıza sağ tıklayın ve seçeneğini belirleyerek de yeni veya mevcut bir proje üzerinde Docker desteğini etkinleştirebilirsiniz **Proje Ekle-Docker desteği**Şekil 5-4'te gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="bed48-159">You can also enable Docker support on a new or existing project by right-clicking your project file in Visual Studio and selecting the option **Add-Docker Project Support**, as shown in Figure 5-4.</span></span>

![](./media/image6.png)

<span data-ttu-id="bed48-160">**Şekil 5-4**.</span><span class="sxs-lookup"><span data-stu-id="bed48-160">**Figure 5-4**.</span></span> <span data-ttu-id="bed48-161">Mevcut bir Visual Studio 2017 projesinde Docker desteğini etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="bed48-161">Enabling Docker support in an existing Visual Studio 2017 project</span></span>

<span data-ttu-id="bed48-162">Bu eylem (örneğin, bir ASP.NET Web uygulaması veya Web API hizmeti) bir projede bir Dockerfile gerekli yapılandırmayla projeye ekler.</span><span class="sxs-lookup"><span data-stu-id="bed48-162">This action on a project (like an ASP.NET Web application or Web API service) adds a Dockerfile to the project with the required configuration.</span></span> <span data-ttu-id="bed48-163">Ayrıca, tüm çözüm için bir docker-compose.yml dosyası ekler.</span><span class="sxs-lookup"><span data-stu-id="bed48-163">It also adds a docker-compose.yml file for the whole solution.</span></span> <span data-ttu-id="bed48-164">Aşağıdaki bölümlerde, biz bu dosyaların her giden bilgiler açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="bed48-164">In the following sections, we describe the information that goes into each of those files.</span></span> <span data-ttu-id="bed48-165">Visual Studio bu işi sizin yerinize bunları yapar, ancak bir Dockerfile içinde unsurları anlamak kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="bed48-165">Visual Studio can do this work for you, but it is useful to understand what goes into a Dockerfile.</span></span>

### <a name="option-a-creating-a-project-using-an-existing-official-net-docker-image"></a><span data-ttu-id="bed48-166">Seçenek A: var olan resmi .NET Docker görüntüsünü kullanarak bir proje oluşturma</span><span class="sxs-lookup"><span data-stu-id="bed48-166">Option A: Creating a project using an existing official .NET Docker image</span></span>

<span data-ttu-id="bed48-167">Genellikle resmi bir depodan alabilirsiniz bir temel görüntünün üstüne kapsayıcınızın özel bir görüntü oluşturun [Docker Hub](https://hub.docker.com/) kayıt defteri.</span><span class="sxs-lookup"><span data-stu-id="bed48-167">You usually build a custom image for your container on top of a base image you can get from an official repository at the [Docker Hub](https://hub.docker.com/) registry.</span></span> <span data-ttu-id="bed48-168">Visual Studio'da Docker desteğini etkinleştirmek ne olacağını perde tam olarak olmasıdır.</span><span class="sxs-lookup"><span data-stu-id="bed48-168">That is precisely what happens under the covers when you enable Docker support in Visual Studio.</span></span> <span data-ttu-id="bed48-169">Dockerfile, var olan bir aspnetcore görüntüsü kullanır.</span><span class="sxs-lookup"><span data-stu-id="bed48-169">Your Dockerfile will use an existing aspnetcore image.</span></span>

<span data-ttu-id="bed48-170">Daha önce hangi Docker görüntülerini ve seçtiğiniz işletim sistemi ve framework bağlı olarak kullanabilirsiniz depoları açıklanmıştır.</span><span class="sxs-lookup"><span data-stu-id="bed48-170">Earlier we explained which Docker images and repos you can use, depending on the framework and OS you have chosen.</span></span> <span data-ttu-id="bed48-171">Örneğin, ASP.NET Core (Linux veya Windows) kullanmak istiyorsanız, kullanılacak görüntüyü microsoft, / aspnetcore:2.0.</span><span class="sxs-lookup"><span data-stu-id="bed48-171">For instance, if you want to use ASP.NET Core (Linux or Windows), the image to use is microsoft/aspnetcore:2.0.</span></span> <span data-ttu-id="bed48-172">Bu nedenle, kapsayıcınız için kullanacağınız hangi temel Docker görüntüsüne belirtmeniz yeterlidir.</span><span class="sxs-lookup"><span data-stu-id="bed48-172">Therefore, you just need to specify what base Docker image you will use for your container.</span></span> <span data-ttu-id="bed48-173">Microsoft'tan ekleyerek bunu / Dockerfile için aspnetcore:2.0.</span><span class="sxs-lookup"><span data-stu-id="bed48-173">You do that by adding FROM microsoft/aspnetcore:2.0 to your Dockerfile.</span></span> <span data-ttu-id="bed48-174">Bu Visual Studio tarafından otomatik olarak gerçekleştirilir, ancak sürüm olsaydı, bu değeri güncelleştirin.</span><span class="sxs-lookup"><span data-stu-id="bed48-174">This will be automatically performed by Visual Studio, but if you were to update the version, you update this value.</span></span>

<span data-ttu-id="bed48-175">Bir sürüm numarası ile Docker Hub resmi bir .NET görüntü deposundan kullanarak aynı dil özellikleri (geliştirme, test ve üretim dahil) tüm makinelerde kullanılabilir olmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="bed48-175">Using an official .NET image repository from Docker Hub with a version number ensures that the same language features are available on all machines (including development, testing, and production).</span></span>

<span data-ttu-id="bed48-176">Aşağıdaki örnek bir ASP.NET Core kapsayıcı için bir örnek Dockerfile gösterir.</span><span class="sxs-lookup"><span data-stu-id="bed48-176">The following example shows a sample Dockerfile for an ASP.NET Core container.</span></span>

```Dockerfile
FROM microsoft/aspnetcore:2.0
  
ARG source
  
WORKDIR /app
  
EXPOSE 80
  
COPY ${source:-obj/Docker/publish} .
  
ENTRYPOINT ["dotnet", " MySingleContainerWebApp.dll "]
```

<span data-ttu-id="bed48-177">Bu durumda, kapsayıcı resmi ASP.NET Core Docker görüntü (Linux ve Windows için çok arch) 2.0 sürümünü temel alır.</span><span class="sxs-lookup"><span data-stu-id="bed48-177">In this case, the container is based on version 2.0 of the official ASP.NET Core Docker image (multi-arch for Linux and Windows).</span></span> <span data-ttu-id="bed48-178">Ayar budur `FROM microsoft/aspnetcore:2.0`.</span><span class="sxs-lookup"><span data-stu-id="bed48-178">This is the setting `FROM microsoft/aspnetcore:2.0`.</span></span> <span data-ttu-id="bed48-179">(Bu temel görüntü hakkında daha fazla ayrıntı için bkz. [ASP.NET Core, Docker görüntüsü](https://hub.docker.com/r/microsoft/aspnetcore/) sayfası ve [.NET Core, Docker görüntüsü](https://hub.docker.com/r/microsoft/dotnet/) sayfası.) Dockerfile içinde ayrıca isteyin (Bu durumda, SUNMAYA ayarı ile yapılandırılmış olarak 80 numaralı bağlantı noktası) çalışma zamanında kullanacağınız TCP bağlantı noktasında dinlemek için Docker gerekir.</span><span class="sxs-lookup"><span data-stu-id="bed48-179">(For further details about this base image, see the [ASP.NET Core Docker Image](https://hub.docker.com/r/microsoft/aspnetcore/) page and the [.NET Core Docker Image](https://hub.docker.com/r/microsoft/dotnet/) page.) In the Dockerfile, you also need to instruct Docker to listen on the TCP port you will use at runtime (in this case, port 80, as configured with the EXPOSE setting).</span></span>

<span data-ttu-id="bed48-180">Dil ve çerçeve kullanmakta olduğunuz bağlı olarak bir Dockerfile içinde ek yapılandırma ayarları belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bed48-180">You can specify additional configuration settings in the Dockerfile, depending on the language and framework you are using.</span></span> <span data-ttu-id="bed48-181">Örneğin, giriş noktası satırla \["dotnet", "MySingleContainerWebApp.dll"\] bir .NET Core uygulamasını çalıştırmak için Docker söyler.</span><span class="sxs-lookup"><span data-stu-id="bed48-181">For instance, the ENTRYPOINT line with \["dotnet", "MySingleContainerWebApp.dll"\] tells Docker to run a .NET Core application.</span></span> <span data-ttu-id="bed48-182">.NET uygulaması derleme ve çalıştırma için SDK ve .NET Core CLI (dotnet CLI) kullanıyorsanız, bu ayar farklı olacaktır.</span><span class="sxs-lookup"><span data-stu-id="bed48-182">If you are using the SDK and the .NET Core CLI (dotnet CLI) to build and run the .NET application, this setting would be different.</span></span> <span data-ttu-id="bed48-183">ENTRYPOINT satır ve diğer ayarları uygulamanız için seçtiğiniz dile ve platforma bağlı olarak farklı olacaktır alt çizgidir.</span><span class="sxs-lookup"><span data-stu-id="bed48-183">The bottom line is that the ENTRYPOINT line and other settings will be different depending on the language and platform you choose for your application.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="bed48-184">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="bed48-184">Additional resources</span></span>

-   <span data-ttu-id="bed48-185">**.NET Core uygulamaları için Docker görüntüleri oluşturma**
    [*https://docs.microsoft.com/dotnet/core/docker/building-net-docker-images*](../../../core/docker/building-net-docker-images.md)</span><span class="sxs-lookup"><span data-stu-id="bed48-185">**Building Docker Images for .NET Core Applications**
[*https://docs.microsoft.com/dotnet/core/docker/building-net-docker-images*](../../../core/docker/building-net-docker-images.md)</span></span>

-   <span data-ttu-id="bed48-186">**Kendi görüntünüzü**.</span><span class="sxs-lookup"><span data-stu-id="bed48-186">**Build your own image**.</span></span> <span data-ttu-id="bed48-187">Resmi Docker belgelerinde.</span><span class="sxs-lookup"><span data-stu-id="bed48-187">In the official Docker documentation.</span></span>
    [*https://docs.docker.com/engine/tutorials/dockerimages/*](https://docs.docker.com/engine/tutorials/dockerimages/)

### <a name="using-multi-arch-image-repositories"></a><span data-ttu-id="bed48-188">Çok yay görüntü depolarını kullanarak</span><span class="sxs-lookup"><span data-stu-id="bed48-188">Using multi-arch image repositories</span></span>

<span data-ttu-id="bed48-189">Tek bir depoda bir Linux görüntüsü ve bir Windows görüntüsünü gibi platformu çeşitleri içerebilir.</span><span class="sxs-lookup"><span data-stu-id="bed48-189">A single repo can contain platform variants, such as a Linux image and a Windows image.</span></span> <span data-ttu-id="bed48-190">Bu özellik, (yani Linux ve Windows) birden çok platform karşılamak için tek depo oluşturmak Microsoft (temel Görüntü Oluşturucu) gibi satıcıları sağlar.</span><span class="sxs-lookup"><span data-stu-id="bed48-190">This feature allows vendors like Microsoft (base image creators) to create a single repo to cover multiple platforms (that is Linux and Windows).</span></span> <span data-ttu-id="bed48-191">Örneğin, [microsoft/dotnet](https://hub.docker.com/r/microsoft/aspnetcore/) Docker Hub kayıt defterinde depo aynı depo adını kullanarak Linux ve Windows Nano sunucu için destek sağlar.</span><span class="sxs-lookup"><span data-stu-id="bed48-191">For example, the [microsoft/dotnet](https://hub.docker.com/r/microsoft/aspnetcore/) repository available in the Docker Hub registry provides support for Linux and Windows Nano Server by using the same repo name.</span></span>

<span data-ttu-id="bed48-192">Açık bir platformu hedefleyen bir etiket belirtirseniz, aşağıdaki durumlarda ister:</span><span class="sxs-lookup"><span data-stu-id="bed48-192">If you specify a tag, targeting a platform that is explicit like in the following cases:</span></span>

-   <span data-ttu-id="bed48-193">**Microsoft/aspnetcore:2.0.0-jessie**</span><span class="sxs-lookup"><span data-stu-id="bed48-193">**microsoft/aspnetcore:2.0.0-jessie**</span></span>

        .NET Core 2.0 runtime-only on Linux 

-   <span data-ttu-id="bed48-194">**Microsoft/aspnetcore:2.0.0-nanoserver**</span><span class="sxs-lookup"><span data-stu-id="bed48-194">**microsoft/aspnetcore:2.0.0-nanoserver**</span></span>

        .NET Core 2.0 runtime-only on Windows Nano Server

<span data-ttu-id="bed48-195">Ancak ve belirtirseniz bu yeni mid-2017 itibarıyla, hatta aynı etiketi ile aynı görüntü adı, yeni çok yay görüntülerini (gibi çok arch destekleyen aspnetcore görüntüsü) bağlı dağıttığınız Docker ana bilgisayar işletim sistemi olarak Linux veya Windows sürümü kullanır , aşağıdaki örnekte gösterildiği gibi:</span><span class="sxs-lookup"><span data-stu-id="bed48-195">But, and this is new since mid-2017, if you specify the same image name, even with the same tag, the new multi-arch images (like the aspnetcore image which supports multi-arch) will use the Linux or Windows version depending on the Docker host OS you are deploying, as shown in the following example:</span></span>

-   <span data-ttu-id="bed48-196">**Microsoft / aspnetcore:2.0**</span><span class="sxs-lookup"><span data-stu-id="bed48-196">**microsoft/aspnetcore:2.0**</span></span>

        Multi-arch: .NET Core 2.0 runtime-only on Linux or Windows Nano Server depending on the Docker host OS

<span data-ttu-id="bed48-197">Windows konaktan görüntü çekme bu şekilde, Windows değişken çeker ve bir Linux ana bilgisayarından görüntü adının aynısını çekme Linux değişken çeker.</span><span class="sxs-lookup"><span data-stu-id="bed48-197">This way, when you pull an image from a Windows host, it will pull the Windows variant, and pulling the same image name from a Linux host will pull the Linux variant.</span></span>

### <a name="option-b-creating-your-base-image-from-scratch"></a><span data-ttu-id="bed48-198">Seçenek B: temel görüntünüzü sıfırdan oluşturma</span><span class="sxs-lookup"><span data-stu-id="bed48-198">Option B: Creating your base image from scratch</span></span>

<span data-ttu-id="bed48-199">Kendi Docker temel görüntüsünde sıfırdan oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bed48-199">You can create your own Docker base image from scratch.</span></span> <span data-ttu-id="bed48-200">Bu senaryo için Docker ile başlayan bir kişinin önerilmez, ancak kendi temel görüntü belirli bitlerini ayarlamak istiyorsanız, bunu yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bed48-200">This scenario is not recommended for someone who is starting with Docker, but if you want to set the specific bits of your own base image, you can do so.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="bed48-201">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="bed48-201">Additional resources</span></span>

-   <span data-ttu-id="bed48-202">**.NET Core görüntüleri çok yay**.</span><span class="sxs-lookup"><span data-stu-id="bed48-202">**Multi-arch .NET Core images**.</span></span>
<span data-ttu-id="bed48-203">https://github.com/dotnet/announcements/issues/14</span><span class="sxs-lookup"><span data-stu-id="bed48-203">https://github.com/dotnet/announcements/issues/14</span></span> 
-   <span data-ttu-id="bed48-204">**Temel görüntü oluşturma**.</span><span class="sxs-lookup"><span data-stu-id="bed48-204">**Create a base image**.</span></span> <span data-ttu-id="bed48-205">Resmi Docker belgeleri.</span><span class="sxs-lookup"><span data-stu-id="bed48-205">Official Docker documentation.</span></span>
    [*https://docs.docker.com/engine/userguide/eng-image/baseimages/*](https://docs.docker.com/engine/userguide/eng-image/baseimages/)

![](./media/image7.png)

## <a name="step-3-create-your-custom-docker-images-and-embed-your-application-or-service-in-them"></a><span data-ttu-id="bed48-206">Adım 3.</span><span class="sxs-lookup"><span data-stu-id="bed48-206">Step 3.</span></span> <span data-ttu-id="bed48-207">Özel Docker görüntülerinizi oluşturmak ve uygulamanızın veya hizmetinizin bunları ekleme</span><span class="sxs-lookup"><span data-stu-id="bed48-207">Create your custom Docker images and embed your application or service in them</span></span>

<span data-ttu-id="bed48-208">Uygulamanızdaki her hizmet için ilgili görüntü oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="bed48-208">For each service in your application, you need to create a related image.</span></span> <span data-ttu-id="bed48-209">Uygulamanızı bir tek bir hizmeti veya web uygulaması oluşur, tek bir görüntü yeterlidir.</span><span class="sxs-lookup"><span data-stu-id="bed48-209">If your application is made up of a single service or web application, you just need a single image.</span></span>

<span data-ttu-id="bed48-210">Docker görüntülerini otomatik olarak sizin için Visual Studio'da oluşturulan unutmayın.</span><span class="sxs-lookup"><span data-stu-id="bed48-210">Note that the Docker images are built automatically for you in Visual Studio.</span></span> <span data-ttu-id="bed48-211">Aşağıdaki adımlar yalnızca Düzenleyici/CLI iş akışı için gereken ve altında olabilecekler açıklık için açıklanmıştır.</span><span class="sxs-lookup"><span data-stu-id="bed48-211">The following steps are only needed for the editor/CLI workflow and explained for clarity about what happens underneath.</span></span>

<span data-ttu-id="bed48-212">Geliştirme ve yerel olarak bir tamamlanmış itinceye kadar test için geliştirici olarak, ihtiyaç duyduğunuz, özelliği veya kaynak denetim sisteminize (örneğin GitHub) değiştirin.</span><span class="sxs-lookup"><span data-stu-id="bed48-212">You, as developer, need to develop and test locally until you push a completed feature or change to your source control system (for example, to GitHub).</span></span> <span data-ttu-id="bed48-213">Bu, Docker görüntüleri oluşturun ve kapsayıcıları yerel Docker konağı için (Windows veya Linux VM) dağıtın ve çalıştırın, test ve yerel kapsayıcıların karşı hata ayıklama gerektiği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="bed48-213">This means that you need to create the Docker images and deploy containers to a local Docker host (Windows or Linux VM) and run, test, and debug against those local containers.</span></span>

<span data-ttu-id="bed48-214">Özel bir görüntü yerel ortamınızda Docker CLI ve Dockerfile'ı kullanarak oluşturmak için docker oluşturma komutu, Şekil 5-5'olduğu gibi kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bed48-214">To create a custom image in your local environment by using Docker CLI and your Dockerfile, you can use the docker build command, as in Figure 5-5.</span></span>

![](./media/image8.png)

<span data-ttu-id="bed48-215">**Şekil 5-5**.</span><span class="sxs-lookup"><span data-stu-id="bed48-215">**Figure 5-5**.</span></span> <span data-ttu-id="bed48-216">Özel bir Docker görüntüsü oluşturma</span><span class="sxs-lookup"><span data-stu-id="bed48-216">Creating a custom Docker image</span></span>

<span data-ttu-id="bed48-217">İsteğe bağlı olarak, doğrudan docker derleme proje klasöründen çalıştırmak, yerine, önce gerekli .NET kitaplıkları ile dağıtılabilir bir klasör oluşturabilirsiniz ve dotnet çalıştırarak ikili dosyaları yayımlayın ve ardından docker derleme komutunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="bed48-217">Optionally, instead of directly running docker build from the project folder, you can first generate a deployable folder with the required .NET libraries and binaries by running dotnet publish, and then use the docker build command.</span></span>

<span data-ttu-id="bed48-218">Bu ad cesardl/netcore-webapı-mikro hizmet ile bir Docker görüntüsü oluşturur-docker: ilk.</span><span class="sxs-lookup"><span data-stu-id="bed48-218">This will create a Docker image with the name cesardl/netcore-webapi-microservice-docker:first.</span></span> <span data-ttu-id="bed48-219">Bu durumda: öncelikle, belirli bir sürümü temsil eden bir etiketi olan.</span><span class="sxs-lookup"><span data-stu-id="bed48-219">In this case, :first is a tag representing a specific version.</span></span> <span data-ttu-id="bed48-220">Oluşturulmuş Docker uygulamanız için oluşturmak için gereken her özel bir görüntü için bu adımı yineleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bed48-220">You can repeat this step for each custom image you need to create for your composed Docker application.</span></span>

<span data-ttu-id="bed48-221">Bir uygulama birden çok kapsayıcılardan yapılan ne zaman (diğer bir deyişle, çok kapsayıcılı bir uygulama olduğu), ayrıca docker compose up--ilgili kullanıma sunulan meta verileri kullanarak tek bir komutla ilgili tüm görüntüleri oluşturmak için yapı komutu docker-compose.yml dosyaları.</span><span class="sxs-lookup"><span data-stu-id="bed48-221">When an application is made of multiple containers (that is, it is a multi-container application), you can also use the docker-compose up --build command to build all the related images with a single command by using the metadata exposed in the related docker-compose.yml files.</span></span>

<span data-ttu-id="bed48-222">Var olan görüntülerden yerel deponuzda docker'ı kullanarak görüntü komutu, Şekil 5-6'da gösterildiği gibi bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bed48-222">You can find the existing images in your local repository by using the docker images command, as shown in Figure 5-6.</span></span>

![](./media/image9.png)

<span data-ttu-id="bed48-223">**Şekil 5-6.**</span><span class="sxs-lookup"><span data-stu-id="bed48-223">**Figure 5-6.**</span></span> <span data-ttu-id="bed48-224">Docker görüntüleri komutunu kullanarak var olan görüntüleri görüntüleme</span><span class="sxs-lookup"><span data-stu-id="bed48-224">Viewing existing images using the docker images command</span></span>

### <a name="creating-docker-images-with-visual-studio"></a><span data-ttu-id="bed48-225">Visual Studio ile Docker görüntüleri oluşturma</span><span class="sxs-lookup"><span data-stu-id="bed48-225">Creating Docker images with Visual Studio</span></span>

<span data-ttu-id="bed48-226">Docker desteği bir proje oluşturmak için Visual Studio kullanıyorsanız, görüntü açıkça oluşturmayın.</span><span class="sxs-lookup"><span data-stu-id="bed48-226">When you are using Visual Studio to create a project with Docker support, you do not explicitly create an image.</span></span> <span data-ttu-id="bed48-227">Bunun yerine, F5 tuşuna basın ve dockerized uygulama veya hizmet çalıştırma görüntü sizin için oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="bed48-227">Instead, the image is created for you when you press F5 and run the dockerized application or service.</span></span> <span data-ttu-id="bed48-228">Bu adım Visual Studio'da otomatik olarak yapılır ve bu durum görmezsiniz ancak neler olduğunu bilmeniz önemlidir üzerinde underneath.</span><span class="sxs-lookup"><span data-stu-id="bed48-228">This step is automatic in Visual Studio, and you will not see it happen, but it is important that you know what is going on underneath.</span></span>

![](./media/image10.png)

## <a name="step-4-define-your-services-in-docker-composeyml-when-building-a-multi-container-docker-application"></a><span data-ttu-id="bed48-229">4. adımı.</span><span class="sxs-lookup"><span data-stu-id="bed48-229">Step 4.</span></span> <span data-ttu-id="bed48-230">Çok kapsayıcılı Docker uygulaması oluştururken, docker-compose.yml hizmetlerinizi tanımlayın</span><span class="sxs-lookup"><span data-stu-id="bed48-230">Define your services in docker-compose.yml when building a multi-container Docker application</span></span>

<span data-ttu-id="bed48-231">[Docker-compose.yml](https://docs.docker.com/compose/compose-file/) dosya dağıtım komutları ile oluşturulmuş bir uygulama olarak dağıtılması için ilgili bir hizmetler kümesi tanımlamanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="bed48-231">The [docker-compose.yml](https://docs.docker.com/compose/compose-file/) file lets you define a set of related services to be deployed as a composed application with deployment commands.</span></span>

<span data-ttu-id="bed48-232">Docker-compose.yml dosyası kullanmak için aşağıdaki örnekte benzer içeriğe sahip ana dosyasında veya kök Çözüm klasörü'ı oluşturmanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="bed48-232">To use a docker-compose.yml file, you need to create the file in your main or root solution folder, with content similar to that in the following example:</span></span>

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

<span data-ttu-id="bed48-233">Bu docker-compose.yml dosyası basit ve birleştirilmiş bir sürüm olduğuna dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="bed48-233">Note that this docker-compose.yml file is a simplified and merged version.</span></span> <span data-ttu-id="bed48-234">Bu, her zaman, bağlantı dizesi gibi dağıtım ortamı bağımlı olabileceği yapılandırma bilgilerini artı uygulanan her bir kapsayıcı (adı gibi özel görüntü), statik yapılandırma verilerini içerir.</span><span class="sxs-lookup"><span data-stu-id="bed48-234">It contains static configuration data for each container (like the name of the custom image), which always applies, plus configuration information that might depend on the deployment environment, like the connection string.</span></span> <span data-ttu-id="bed48-235">Sonraki bölümlerde, docker-compose.yml yapılandırmanın birden çok nasıl bölebilirsiniz öğreneceksiniz docker compose dosyaları ve geçersiz kılma değerleri (hata ayıklama veya sürüm) ortamını ve yürütme türüne bağlı olarak.</span><span class="sxs-lookup"><span data-stu-id="bed48-235">In later sections, you will learn how you can split the docker-compose.yml configuration into multiple docker-compose files and override values depending on the environment and execution type (debug or release).</span></span>

<span data-ttu-id="bed48-236">Docker-compose.yml dosyası örneği dört hizmet tanımlar: webmvc service (web uygulaması), (catalog.api ve ordering.api) iki mikro hizmet ve kapsayıcı olarak çalışan Linux SQL Server tabanlı bir veri kaynağı kapsayıcı, sql.data,.</span><span class="sxs-lookup"><span data-stu-id="bed48-236">The docker-compose.yml file example defines four services: the webmvc service (a web application), two microservices (catalog.api and ordering.api), and one data source container, sql.data, based on SQL Server for Linux running as a container.</span></span> <span data-ttu-id="bed48-237">Her biri için gerekli bir Docker görüntüsü, bu nedenle, her hizmetin bir kapsayıcı olarak dağıtılır.</span><span class="sxs-lookup"><span data-stu-id="bed48-237">Each service is deployed as a container, so a Docker image is required for each.</span></span>

<span data-ttu-id="bed48-238">Docker-compose.yml dosyası, yalnızca kapsayıcıların ne kullanılır, ancak ayrı ayrı yapılandırmaya belirtir.</span><span class="sxs-lookup"><span data-stu-id="bed48-238">The docker-compose.yml file specifies not only what containers are being used, but how they are individually configured.</span></span> <span data-ttu-id="bed48-239">Örneğin, webmvc kapsayıcısı tanımında .yml dosyası:</span><span class="sxs-lookup"><span data-stu-id="bed48-239">For instance, the webmvc container definition in the .yml file:</span></span>

-   <span data-ttu-id="bed48-240">Önceden oluşturulmuş bir elektronik mağaza kullanan / web: son görüntü.</span><span class="sxs-lookup"><span data-stu-id="bed48-240">Uses a pre-built eshop/web:latest image.</span></span> <span data-ttu-id="bed48-241">Ancak, aynı zamanda bir parçası olarak oluşturulacak görüntünün yapılandırabilirsiniz docker-compose temelli bir derleme üzerinde yürütme ek bir yapılandırma: docker-compose dosyasındaki bölümü.</span><span class="sxs-lookup"><span data-stu-id="bed48-241">However, you could also configure the image to be built as part of the docker-compose execution with an additional configuration based on a build: section in the docker-compose file.</span></span>

-   <span data-ttu-id="bed48-242">İki ortam değişkenlerini (katalog URL'si ve OrderingUrl) başlatır.</span><span class="sxs-lookup"><span data-stu-id="bed48-242">Initializes two environment variables (CatalogUrl and OrderingUrl).</span></span>

-   <span data-ttu-id="bed48-243">Konak makinedeki dış bağlantı noktası 80 kapsayıcı üzerindeki 80 kullanıma sunulan bağlantı noktası iletir.</span><span class="sxs-lookup"><span data-stu-id="bed48-243">Forwards the exposed port 80 on the container to the external port 80 on the host machine.</span></span>

-   <span data-ttu-id="bed48-244">Web uygulaması katalog ve sıralama hizmetiyle bağlantı bağlıdır\_ayarı.</span><span class="sxs-lookup"><span data-stu-id="bed48-244">Links the web app to the catalog and ordering service with the depends\_on setting.</span></span> <span data-ttu-id="bed48-245">Bu hizmet, bu hizmetleri yeniden başlatılana kadar beklenecek neden olur.</span><span class="sxs-lookup"><span data-stu-id="bed48-245">This causes the service to wait until those services are started.</span></span>

<span data-ttu-id="bed48-246">Mikro hizmetler ve çok kapsayıcılı uygulamalar uygulamak nasıl ele, biz bir sonraki bölümde docker-compose.yml dosyası yeniden ziyaret.</span><span class="sxs-lookup"><span data-stu-id="bed48-246">We will revisit the docker-compose.yml file in a later section when we cover how to implement microservices and multi-container apps.</span></span>

### <a name="working-with-docker-composeyml-in-visual-studio-2017"></a><span data-ttu-id="bed48-247">Visual Studio 2017'de docker-compose.yml ile çalışma</span><span class="sxs-lookup"><span data-stu-id="bed48-247">Working with docker-compose.yml in Visual Studio 2017</span></span>

<span data-ttu-id="bed48-248">Docker çözümü desteği için bir Visual Studio çözümü içinde bir hizmet projesi Şekil 5-7'de gösterildiği gibi eklediğinizde, Visual Studio projenize bir Dockerfile ekler ve hizmet bölümü (Proje) çözümünüzde docker-compose.yml dosyaları ekler.</span><span class="sxs-lookup"><span data-stu-id="bed48-248">When you add Docker solution support to a service project in a Visual Studio solution, as shown in Figure 5-7, Visual Studio adds a Dockerfile to your project, and it adds a service section (project) in your solution with the docker-compose.yml files.</span></span> <span data-ttu-id="bed48-249">Birden çok kapsayıcı çözümünüzü oluşturmaya başlamak için kolay bir yoludur.</span><span class="sxs-lookup"><span data-stu-id="bed48-249">It is an easy way to start composing your multiple-container solution.</span></span> <span data-ttu-id="bed48-250">Docker-compose.yml dosyaları açmak ve bunları ek özellikler ile güncelleştirin.</span><span class="sxs-lookup"><span data-stu-id="bed48-250">You can then open the docker-compose.yml files and update them with additional features.</span></span>

![](./media/image6.png)

<span data-ttu-id="bed48-251">**Şekil 5-7**.</span><span class="sxs-lookup"><span data-stu-id="bed48-251">**Figure 5-7**.</span></span> <span data-ttu-id="bed48-252">Bir ASP.NET Core projesi sağ tıklayarak Visual Studio 2017'de Docker desteği ekleme</span><span class="sxs-lookup"><span data-stu-id="bed48-252">Adding Docker support in Visual Studio 2017 by right-clicking an ASP.NET Core project</span></span>

<span data-ttu-id="bed48-253">Visual Studio'da Docker desteği ekleme yalnızca Dockerfile projenize ekler, ancak çözüm düzeyinde ayarlanan birkaç genel docker-compose.yml dosyaları için yapılandırma bilgilerini ekler.</span><span class="sxs-lookup"><span data-stu-id="bed48-253">Adding Docker support in Visual Studio not only adds the Dockerfile to your project, but adds the configuration information to several global docker-compose.yml files that are set at the solution level.</span></span>

<span data-ttu-id="bed48-254">Visual Studio çözümünüzde Docker desteğini ekleyin, sonra da Çözüm Gezgini'nde, Şekil 5-8'de gösterildiği gibi eklenen docker-compose.yml dosyaları içeren yeni bir düğüm (docker compose.dcproj proje dosyasındaki) görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="bed48-254">After you add Docker support to your solution in Visual Studio, you will also see a new node (in the docker-compose.dcproj project file) in Solution Explorer that contains the added docker-compose.yml files, as shown in Figure 5-8.</span></span>

![](./media/image11.PNG)

<span data-ttu-id="bed48-255">**Şekil 5-8**.</span><span class="sxs-lookup"><span data-stu-id="bed48-255">**Figure 5-8**.</span></span> <span data-ttu-id="bed48-256">**Docker-compose** Visual Studio 2017 Çözüm Gezgini'nde eklenen ağaç düğümü</span><span class="sxs-lookup"><span data-stu-id="bed48-256">The **docker-compose** tree node added in Visual Studio 2017 Solution Explorer</span></span>

<span data-ttu-id="bed48-257">Kullanarak bir docker-compose.yml dosyası ile çok kapsayıcılı bir uygulama dağıtabilirsiniz docker-compose komutu.</span><span class="sxs-lookup"><span data-stu-id="bed48-257">You could deploy a multi-container application with a single docker-compose.yml file by using the docker-compose up command.</span></span> <span data-ttu-id="bed48-258">Ancak, yürütme ve ortamı (üretim ve geliştirme) bağlı olarak değerleri geçersiz kılmak için Visual Studio bunları bir grup ekler türü (hata ayıklama ve yayın).</span><span class="sxs-lookup"><span data-stu-id="bed48-258">However, Visual Studio adds a group of them so you can override values depending on the environment (development versus production) and execution type (release versus debug).</span></span> <span data-ttu-id="bed48-259">Bu özellik, sonraki bölümlerde açıklanacaktır.</span><span class="sxs-lookup"><span data-stu-id="bed48-259">This capability will be explained in later sections.</span></span>

![](./media/image12.png)

## <a name="step-5-build-and-run-your-docker-application"></a><span data-ttu-id="bed48-260">5. adımı.</span><span class="sxs-lookup"><span data-stu-id="bed48-260">Step 5.</span></span> <span data-ttu-id="bed48-261">Kendi Docker uygulaması derleme ve çalıştırma</span><span class="sxs-lookup"><span data-stu-id="bed48-261">Build and run your Docker application</span></span>

<span data-ttu-id="bed48-262">Uygulamanız yalnızca tek bir kapsayıcıya sahip değilse, Docker Konağı (VM veya fiziksel sunucu) dağıtarak çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bed48-262">If your application only has a single container, you can run it by deploying it to your Docker host (VM or physical server).</span></span> <span data-ttu-id="bed48-263">Uygulamanız birden fazla hizmet içeriyor, ancak bunu oluşan bir uygulama olarak ya da tek bir CLI komutu kullanarak dağıtabilirsiniz (docker-compose ayarlama), veya Visual Studio ile bu komut aslında altında kullanacak.</span><span class="sxs-lookup"><span data-stu-id="bed48-263">However, if your application contains multiple services, you can deploy it as a composed application, either using a single CLI command (docker-compose up), or with Visual Studio, which will use that command under the covers.</span></span> <span data-ttu-id="bed48-264">Farklı seçenekleri göz atalım.</span><span class="sxs-lookup"><span data-stu-id="bed48-264">Let’s look at the different options.</span></span>

### <a name="option-a-running-a-single-container-with-docker-cli"></a><span data-ttu-id="bed48-265">Seçenek A: tek-kapsayıcı ile Docker CLI'yı çalıştırma</span><span class="sxs-lookup"><span data-stu-id="bed48-265">Option A: Running a single-container with Docker CLI</span></span>

<span data-ttu-id="bed48-266">Şekil 5-9'olduğu gibi komutu çalıştırın: docker kullanarak Docker kapsayıcısı çalıştırabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="bed48-266">You can run a Docker container using the docker run command, as in Figure 5-9:</span></span>

```console
  docker run -t -d -p 80:5000 cesardl/netcore-webapi-microservice-docker:first
```

![](./media/image13.png)

<span data-ttu-id="bed48-267">**Şekil 5-9**.</span><span class="sxs-lookup"><span data-stu-id="bed48-267">**Figure 5-9**.</span></span> <span data-ttu-id="bed48-268">Komutu çalıştırarak docker kullanarak Docker kapsayıcı çalıştırma</span><span class="sxs-lookup"><span data-stu-id="bed48-268">Running a Docker container using the docker run command</span></span>

<span data-ttu-id="bed48-269">Bu durumda, komut kapsayıcının iç bağlantı noktası 5000 ana makinenin 80 numaralı bağlantı noktasına bağlar.</span><span class="sxs-lookup"><span data-stu-id="bed48-269">In this case, the command binds the internal port 5000 of the container to port 80 of the host machine.</span></span> <span data-ttu-id="bed48-270">Bu konak 80 numaralı bağlantı noktasında dinleme ve kapsayıcıda genericread 5000 numaralı bağlantı noktasına ileten anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="bed48-270">This means that the host is listening on port 80 and forwarding to port 5000 on the container.</span></span>

### <a name="option-b-running-a-multi-container-application"></a><span data-ttu-id="bed48-271">Seçenek B: çok kapsayıcılı bir uygulama çalıştırma</span><span class="sxs-lookup"><span data-stu-id="bed48-271">Option B: Running a multi-container application</span></span>

<span data-ttu-id="bed48-272">Çoğu Kurumsal senaryolarda, Docker uygulaması birden çok Hizmetleri, Şekil 5-10'da gösterildiği gibi çok kapsayıcılı bir uygulama çalıştırmak gereken yani oluşacaktır.</span><span class="sxs-lookup"><span data-stu-id="bed48-272">In most enterprise scenarios, a Docker application will be composed of multiple services, which means you need to run a multi-container application, as shown in Figure 5-10.</span></span>

![](./media/image14.png)

<span data-ttu-id="bed48-273">**Şekil 5-10**.</span><span class="sxs-lookup"><span data-stu-id="bed48-273">**Figure 5-10**.</span></span> <span data-ttu-id="bed48-274">Dağıtılmış Docker kapsayıcıları ile VM</span><span class="sxs-lookup"><span data-stu-id="bed48-274">VM with Docker containers deployed</span></span>

#### <a name="running-a-multi-container-application-with-the-docker-cli"></a><span data-ttu-id="bed48-275">Docker CLI ile çok kapsayıcılı bir uygulama çalıştırma</span><span class="sxs-lookup"><span data-stu-id="bed48-275">Running a multi-container application with the Docker CLI</span></span>

<span data-ttu-id="bed48-276">Docker CLI ile çok kapsayıcılı bir uygulama çalıştırmak için docker çalıştırabilirsiniz-compose komutu.</span><span class="sxs-lookup"><span data-stu-id="bed48-276">To run a multi-container application with the Docker CLI, you can run the docker-compose up command.</span></span> <span data-ttu-id="bed48-277">Bu komut kullandığı docker-compose.yml dosyası çok kapsayıcılı bir uygulama dağıtmak için çözüm düzeyinde olması.</span><span class="sxs-lookup"><span data-stu-id="bed48-277">This command uses the docker-compose.yml file that you have at the solution level to deploy a multi-container application.</span></span> <span data-ttu-id="bed48-278">Şekil 5-11 komut docker-compose.yml dosyasını içeren ana proje dizininden çalıştırılırken sonuçları gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="bed48-278">Figure 5-11 shows the results when running the command from your main project directory, which contains the docker-compose.yml file.</span></span>

![](./media/image15.png)

<span data-ttu-id="bed48-279">**Şekil 5-11**.</span><span class="sxs-lookup"><span data-stu-id="bed48-279">**Figure 5-11**.</span></span> <span data-ttu-id="bed48-280">Örnek sonuçları çalıştırırken docker-compose komutu</span><span class="sxs-lookup"><span data-stu-id="bed48-280">Example results when running the docker-compose up command</span></span>

<span data-ttu-id="bed48-281">Sonra docker-compose komutu çalıştırmaları, uygulama ve onun ilişkili kapsayıcılar, Docker konağı VM gösteriminde Şekil 5-10 gösterildiği şekilde dağıtılır.</span><span class="sxs-lookup"><span data-stu-id="bed48-281">After the docker-compose up command runs, the application and its related containers are deployed into your Docker host, as illustrated in the VM representation in Figure 5-10.</span></span>

#### <a name="running-and-debugging-a-multi-container-application-with-visual-studio"></a><span data-ttu-id="bed48-282">Çalıştıran ve Visual Studio ile çok kapsayıcılı bir uygulama hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="bed48-282">Running and debugging a multi-container application with Visual Studio</span></span> 

<span data-ttu-id="bed48-283">Visual Studio 2017'yi kullanarak çok kapsayıcılı bir uygulama çalıştıran basit alınamıyor.</span><span class="sxs-lookup"><span data-stu-id="bed48-283">Running a multi-container application using Visual Studio 2017 cannot get simpler.</span></span> <span data-ttu-id="bed48-284">Çok kapsayıcılı bir uygulama yalnızca çalıştırılamaz, ancak normal kesme noktaları ayarlayarak tüm kapsayıcılarında doğrudan Visual Studio'dan hata ayıklamanız mümkün.</span><span class="sxs-lookup"><span data-stu-id="bed48-284">You can not only run the multi-container application, but you are able to debug all its containers directly from Visual Studio by setting regular breakpoints.</span></span>

<span data-ttu-id="bed48-285">Her bir çözüm içinde bir proje için Docker çözüm desteğini eklemeden önce belirtildiği gibi proje çalıştırın veya çözümün tamamının aynı anda hata ayıklama olanak sağlayan genel (Çözüm düzeyinde) docker-compose.yml dosyasında yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="bed48-285">As mentioned before, each time you add Docker solution support to a project within a solution, that project is configured in the global (solution-level) docker-compose.yml file, which lets you run or debug the whole solution at once.</span></span> <span data-ttu-id="bed48-286">Visual Studio Docker çözümü desteği etkin olan her proje için bir kapsayıcı başlatın ve iç tüm adımları gerçekleştirdiğiniz (dotnet yayımlama, docker derleme, vs.).</span><span class="sxs-lookup"><span data-stu-id="bed48-286">Visual Studio will start one container for each project that has Docker solution support enabled, and perform all the internal steps for you (dotnet publish, docker build, etc.).</span></span>

<span data-ttu-id="bed48-287">Burada önemli olan nokta Şekil 5-12'de gösterildiği gibi Visual Studio 2017'de, ek bir yoktur **Docker** F5 anahtar eylemi için komutu.</span><span class="sxs-lookup"><span data-stu-id="bed48-287">The important point here is that, as shown in Figure 5-12, in Visual Studio 2017 there is an additional **Docker** command for the F5 key action.</span></span> <span data-ttu-id="bed48-288">Bu seçenek çalıştırın ya da docker-compose.yml dosyaları çözüm düzeyinde tanımlanan tüm kapsayıcıları çalıştırarak çok kapsayıcılı bir uygulama hata ayıklama sağlar.</span><span class="sxs-lookup"><span data-stu-id="bed48-288">This option lets you run or debug a multi-container application by running all the containers that are defined in the docker-compose.yml files at the solution level.</span></span> <span data-ttu-id="bed48-289">Birden çok kapsayıcı çözümleri hata ayıklama özelliği (kapsayıcı) farklı bir projede birkaç kesme noktaları, her bir kesme noktası ayarlayın ve Visual Studio'dan hata ayıklama sırasında farklı projelerde tanımlanan ve çalıştırılan kesme noktalarında durdurur anlamına gelir. farklı kapsayıcılar.</span><span class="sxs-lookup"><span data-stu-id="bed48-289">The ability to debug multiple-container solutions means that you can set several breakpoints, each breakpoint in a different project (container), and while debugging from Visual Studio you will stop at breakpoints defined in different projects and running on different containers.</span></span>

![](./media/image16.png)

<span data-ttu-id="bed48-290">**Şekil 5-12**.</span><span class="sxs-lookup"><span data-stu-id="bed48-290">**Figure 5-12**.</span></span> <span data-ttu-id="bed48-291">Visual Studio 2017'de çalışan çok kapsayıcılı uygulamalar</span><span class="sxs-lookup"><span data-stu-id="bed48-291">Running multi-container apps in Visual Studio 2017</span></span>

### <a name="additional-resources"></a><span data-ttu-id="bed48-292">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="bed48-292">Additional resources</span></span>

-   <span data-ttu-id="bed48-293">**ASP.NET kapsayıcısını uzak Docker konağı için dağıtma**
    [*https://docs.microsoft.com/azure/vs-azure-tools-docker-hosting-web-apps-in-docker*](https://docs.microsoft.com/azure/vs-azure-tools-docker-hosting-web-apps-in-docker)</span><span class="sxs-lookup"><span data-stu-id="bed48-293">**Deploy an ASP.NET container to a remote Docker host**
[*https://docs.microsoft.com/azure/vs-azure-tools-docker-hosting-web-apps-in-docker*](https://docs.microsoft.com/azure/vs-azure-tools-docker-hosting-web-apps-in-docker)</span></span>

### <a name="a-note-about-testing-and-deploying-with-orchestrators"></a><span data-ttu-id="bed48-294">Test etme ve dağıtma düzenleyicilerle hakkında bir Not</span><span class="sxs-lookup"><span data-stu-id="bed48-294">A note about testing and deploying with orchestrators</span></span>

<span data-ttu-id="bed48-295">Docker compose up ve docker run komutları (veya çalışan ve kapsayıcıları Visual Studio'da hata ayıklama) kapsayıcıları geliştirme ortamınızda test etmek için yeterli.</span><span class="sxs-lookup"><span data-stu-id="bed48-295">The docker-compose up and docker run commands (or running and debugging the containers in Visual Studio) are adequate for testing containers in your development environment.</span></span> <span data-ttu-id="bed48-296">Ancak, bu yaklaşım Docker kümeleri hedefleniyorsa ve Docker Swarm, Mesosphere DC/OS veya Kubernetes düzenleyicileri gibi kullanmamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="bed48-296">But you should not use this approach if you are targeting Docker clusters and orchestrators like Docker Swarm, Mesosphere DC/OS, or Kubernetes.</span></span> <span data-ttu-id="bed48-297">Gibi bir küme kullanıyorsanız [Docker Swarm modu](https://docs.docker.com/engine/swarm/) dağıtmak ve test gibi ek komutlar gerekir (kullanılabilir için Docker CE Windows ve Mac sürümü 1.12 itibaren), [docker hizmeti oluşturulur](https://docs.docker.com/engine/reference/commandline/service_create/) için tek hizmetler.</span><span class="sxs-lookup"><span data-stu-id="bed48-297">If you are using a cluster like [Docker Swarm mode](https://docs.docker.com/engine/swarm/) (available in Docker CE for Windows and Mac since version 1.12), you need to deploy and test with additional commands like [docker service create](https://docs.docker.com/engine/reference/commandline/service_create/) for single services.</span></span> <span data-ttu-id="bed48-298">Birden çok kapsayıcılardan oluşan bir uygulama dağıtıyorsanız, kullandığınız [docker compose paket](https://docs.docker.com/compose/reference/bundle/) ve [docker dağıtma myBundleFile](https://docs.docker.com/engine/reference/commandline/deploy/) olarak oluşturulan uygulamayı dağıtmak için bir *Yığını*.</span><span class="sxs-lookup"><span data-stu-id="bed48-298">If you are deploying an application composed of several containers, you use [docker compose bundle](https://docs.docker.com/compose/reference/bundle/) and [docker deploy myBundleFile](https://docs.docker.com/engine/reference/commandline/deploy/) to deploy the composed application as a *stack*.</span></span> <span data-ttu-id="bed48-299">Daha fazla bilgi için bkz. blog gönderisine [giriş Deneysel dağıtılmış uygulama paketleri](https://blog.docker.com/2016/06/docker-app-bundle/) Docker belgelerinde.</span><span class="sxs-lookup"><span data-stu-id="bed48-299">For more information, see the blog post [Introducing Experimental Distributed Application Bundles](https://blog.docker.com/2016/06/docker-app-bundle/) in the Docker documentation.</span></span> <span data-ttu-id="bed48-300">Docker sitesi.</span><span class="sxs-lookup"><span data-stu-id="bed48-300">on the Docker site.</span></span>

<span data-ttu-id="bed48-301">İçin [DC/OS](https://mesosphere.com/blog/2015/09/02/dcos-cli-command-line-tool-datacenter/) ve [Kubernetes](http://kubernetes.io/docs/user-guide/deployments/) farklı dağıtım komutları ve komut dosyaları da kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="bed48-301">For [DC/OS](https://mesosphere.com/blog/2015/09/02/dcos-cli-command-line-tool-datacenter/) and [Kubernetes](http://kubernetes.io/docs/user-guide/deployments/) you would use different deployment commands and scripts as well.</span></span>

![](./media/image17.png)

## <a name="step-6-test-your-docker-application-using-your-local-docker-host"></a><span data-ttu-id="bed48-302">6. adım.</span><span class="sxs-lookup"><span data-stu-id="bed48-302">Step 6.</span></span> <span data-ttu-id="bed48-303">Kullanarak yerel bir Docker ana bilgisayarınızda Docker uygulamanızı test edin</span><span class="sxs-lookup"><span data-stu-id="bed48-303">Test your Docker application using your local Docker host</span></span>

<span data-ttu-id="bed48-304">Bu adım, uygulamanızın yapılması bağlı olarak değişir.</span><span class="sxs-lookup"><span data-stu-id="bed48-304">This step will vary depending on what your application is doing.</span></span> <span data-ttu-id="bed48-305">Tek kapsayıcı veya hizmet olarak dağıtılan bir basit .NET Core Web uygulamasında, Docker konağı üzerinde bir tarayıcı açıp Şekil 5-13'te gösterildiği gibi bu siteye gezinme hizmete erişebilir.</span><span class="sxs-lookup"><span data-stu-id="bed48-305">In a simple .NET Core Web application that is deployed as a single container or service, you can access the service by opening a browser on the Docker host and navigating to that site as shown in Figure 5-13.</span></span> <span data-ttu-id="bed48-306">(Dockerfile içinde yapılandırma kapsayıcı 80 dışında her şey, konağa bağlantı noktasına eşler. ana bilgisayar bağlantı noktası URL'ye dahil edin.)</span><span class="sxs-lookup"><span data-stu-id="bed48-306">(If the configuration in the Dockerfile maps the container to a port on the host that is anything other than 80, include the host port in the URL.)</span></span>

![](./media/image18.png)

<span data-ttu-id="bed48-307">**Şekil 5-13**.</span><span class="sxs-lookup"><span data-stu-id="bed48-307">**Figure 5-13**.</span></span> <span data-ttu-id="bed48-308">Örneği yerel olarak localhost kullanarak Docker uygulamanızı test etme</span><span class="sxs-lookup"><span data-stu-id="bed48-308">Example of testing your Docker application locally using localhost</span></span>

<span data-ttu-id="bed48-309">Docker için localhost işaret etmiyorsa IP ana bilgisayar (Bu varsayılan Docker CE kullanırken, gerekir), hizmetinize gidin ve makinenizin Ağ kartının IP adresini kullanın.</span><span class="sxs-lookup"><span data-stu-id="bed48-309">If localhost is not pointing to the Docker host IP (by default, when using Docker CE, it should), to navigate to your service, use the IP address of your machine’s network card.</span></span>

<span data-ttu-id="bed48-310">Bu URL tarayıcıda tartışılan belirli bir kapsayıcı örneği için 80 numaralı bağlantı noktasını kullandığını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="bed48-310">Note that this URL in the browser uses port 80 for the particular container example being discussed.</span></span> <span data-ttu-id="bed48-311">Nasıl bu komutu çalıştırın: docker ile bir önceki adımda açıklandığı gibi dağıtılmış olduğu için ancak, dahili olarak istekleri 5000, bağlantı noktası için Rehbere yönlendiriliyorsunuz.</span><span class="sxs-lookup"><span data-stu-id="bed48-311">However, internally the requests are being redirected to port 5000, because that was how it was deployed with the docker run command, as explained in a previous step.</span></span>

<span data-ttu-id="bed48-312">Ayrıca, Şekil 5-14'te gösterildiği gibi terminalden curl kullanarak uygulamayı test edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bed48-312">You can also test the application using curl from the terminal, as shown in Figure 5-14.</span></span> <span data-ttu-id="bed48-313">Bir Docker yüklemesinde Windows üzerindeki Docker ana bilgisayar IP her zaman 10.0.75.1 makinenizin gerçek IP adresinin yanı sıra varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="bed48-313">In a Docker installation on Windows, the default Docker Host IP is always 10.0.75.1 in addition to your machine’s actual IP address.</span></span>

![](./media/image19.png)

<span data-ttu-id="bed48-314">**Şekil 5-14**.</span><span class="sxs-lookup"><span data-stu-id="bed48-314">**Figure 5-14**.</span></span> <span data-ttu-id="bed48-315">Docker uygulamanızı yerel olarak curl kullanarak test etme örneği</span><span class="sxs-lookup"><span data-stu-id="bed48-315">Example of testing your Docker application locally using curl</span></span>

### <a name="testing-and-debugging-containers-with-visual-studio-2017"></a><span data-ttu-id="bed48-316">Test ve hata ayıklama Visual Studio 2017 ile kapsayıcıları</span><span class="sxs-lookup"><span data-stu-id="bed48-316">Testing and debugging containers with Visual Studio 2017</span></span>

<span data-ttu-id="bed48-317">Çalışan kapsayıcılar, olduğu gibi çalışan kapsayıcılar Visual Studio 2017 ile hata ayıklama, .NET uygulama kadar aynı şekilde ayıklayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bed48-317">When running and debugging the containers with Visual Studio 2017, you can debug the .NET application in much the same way as you would when running without containers.</span></span>

### <a name="testing-and-debugging-without-visual-studio"></a><span data-ttu-id="bed48-318">Test ve hata ayıklama Visual Studio</span><span class="sxs-lookup"><span data-stu-id="bed48-318">Testing and debugging without Visual Studio</span></span>

<span data-ttu-id="bed48-319">Düzenleyici/CLI yaklaşımı kullanarak geliştiriyorsanız kapsayıcılarında hata ayıklama daha zordur ve izlemeleri oluşturarak hata ayıklama isteyeceksiniz.</span><span class="sxs-lookup"><span data-stu-id="bed48-319">If you are developing using the editor/CLI approach, debugging containers is more difficult and you will want to debug by generating traces.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="bed48-320">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="bed48-320">Additional resources</span></span>

-   <span data-ttu-id="bed48-321">**Yerel bir Docker kapsayıcısı uygulamalarında hata ayıklama**
    [*https://docs.microsoft.com/azure/vs-azure-tools-docker-edit-and-refresh*](https://docs.microsoft.com/azure/vs-azure-tools-docker-edit-and-refresh)</span><span class="sxs-lookup"><span data-stu-id="bed48-321">**Debugging apps in a local Docker container**
[*https://docs.microsoft.com/azure/vs-azure-tools-docker-edit-and-refresh*](https://docs.microsoft.com/azure/vs-azure-tools-docker-edit-and-refresh)</span></span>

-   <span data-ttu-id="bed48-322">**Steve Lasker. Derleme, hata ayıklama, Docker ile ASP.NET Core uygulamaları dağıtın.**</span><span class="sxs-lookup"><span data-stu-id="bed48-322">**Steve Lasker. Build, Debug, Deploy ASP.NET Core Apps with Docker.**</span></span> <span data-ttu-id="bed48-323">Video.</span><span class="sxs-lookup"><span data-stu-id="bed48-323">Video.</span></span>
    [*https://channel9.msdn.com/Events/Visual-Studio/Visual-Studio-2017-Launch/T115*](https://channel9.msdn.com/Events/Visual-Studio/Visual-Studio-2017-Launch/T115)

## <a name="simplified-workflow-when-developing-containers-with-visual-studio"></a><span data-ttu-id="bed48-324">Visual Studio ile kapsayıcıları geliştirirken basitleştirilmiş bir iş akışı</span><span class="sxs-lookup"><span data-stu-id="bed48-324">Simplified workflow when developing containers with Visual Studio</span></span>

<span data-ttu-id="bed48-325">Etkili bir şekilde, Visual Studio kullanarak iş akışı Düzenleyicisi'ni / CLI yaklaşımı kullanırsanız, çok daha kolay olacaktır.</span><span class="sxs-lookup"><span data-stu-id="bed48-325">Effectively, the workflow when using Visual Studio is a lot simpler than if you use the editor/CLI approach.</span></span> <span data-ttu-id="bed48-326">Docker tarafından gerekli adımların çoğu için Dockerfile ilgili ve gizli ya da Visual Studio tarafından Şekil 5-15'te gösterildiği gibi Basitleştirilmiş docker-compose.yml dosyaları.</span><span class="sxs-lookup"><span data-stu-id="bed48-326">Most of the steps required by Docker related to the Dockerfile and docker-compose.yml files are hidden or simplified by Visual Studio, as shown in Figure 5-15.</span></span>

![](./media/image20.png)

<span data-ttu-id="bed48-327">**Şekil 5-15**.</span><span class="sxs-lookup"><span data-stu-id="bed48-327">**Figure 5-15**.</span></span> <span data-ttu-id="bed48-328">Visual Studio ile geliştirirken basitleştirilmiş bir iş akışı</span><span class="sxs-lookup"><span data-stu-id="bed48-328">Simplified workflow when developing with Visual Studio</span></span>

<span data-ttu-id="bed48-329">Ayrıca, yalnızca bir kez (Docker desteği ekleme projelerinize) 2. adım gerçekleştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="bed48-329">In addition, you need to perform step 2 (adding Docker support to your projects) just once.</span></span> <span data-ttu-id="bed48-330">Bu nedenle, iş akışı herhangi bir geliştirme için .NET kullanarak normal geliştirme görevlerine benzer şekildedir.</span><span class="sxs-lookup"><span data-stu-id="bed48-330">Therefore, the workflow is similar to your usual development tasks when using .NET for any other development.</span></span> <span data-ttu-id="bed48-331">Kapsar (görüntü oluşturma işlemi, hangi kullandığınız temel görüntüleri, kapsayıcılar, vb. dağıtımını) altında ve bazen de davranışları özelleştirmek için Dockerfile veya docker-compose.yml dosyasını düzenlemeniz gerekir neler olduğunu bilmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="bed48-331">You need to know what is going on under the covers (the image build process, what base images you are using, deployment of containers, etc.) and sometimes you will also need to edit the Dockerfile or docker-compose.yml file to customize behaviors.</span></span> <span data-ttu-id="bed48-332">Ancak işin çoğunu, çok daha üretken hale Visual Studio kullanılarak büyük ölçüde basitleştirilir.</span><span class="sxs-lookup"><span data-stu-id="bed48-332">But most of the work is greatly simplified by using Visual Studio, making you a lot more productive.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="bed48-333">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="bed48-333">Additional resources</span></span>

-   <span data-ttu-id="bed48-334">**Steve Lasker. Visual Studio 2017 ile .NET docker geliştirme**
    [*https://channel9.msdn.com/Events/Visual-Studio/Visual-Studio-2017-Launch/T111*](https://channel9.msdn.com/Events/Visual-Studio/Visual-Studio-2017-Launch/T111)</span><span class="sxs-lookup"><span data-stu-id="bed48-334">**Steve Lasker. .NET Docker Development with Visual Studio 2017**
[*https://channel9.msdn.com/Events/Visual-Studio/Visual-Studio-2017-Launch/T111*](https://channel9.msdn.com/Events/Visual-Studio/Visual-Studio-2017-Launch/T111)</span></span>

-   <span data-ttu-id="bed48-335">**Jeffrey t Fritz. Visual Studio için bir kapsayıcı yeni Docker araçları ile .NET Core uygulaması yerleştirin**
    [*https://blogs.msdn.microsoft.com/webdev/2016/11/16/new-docker-tools-for-visual-studio/*](https://blogs.msdn.microsoft.com/webdev/2016/11/16/new-docker-tools-for-visual-studio/)</span><span class="sxs-lookup"><span data-stu-id="bed48-335">**Jeffrey T. Fritz. Put a .NET Core App in a Container with the new Docker Tools for Visual Studio**
[*https://blogs.msdn.microsoft.com/webdev/2016/11/16/new-docker-tools-for-visual-studio/*](https://blogs.msdn.microsoft.com/webdev/2016/11/16/new-docker-tools-for-visual-studio/)</span></span>

## <a name="using-powershell-commands-in-a-dockerfile-to-set-up-windows-containers"></a><span data-ttu-id="bed48-336">Windows kapsayıcıları ayarlamak için bir Dockerfile içinde PowerShell komutlarını kullanarak</span><span class="sxs-lookup"><span data-stu-id="bed48-336">Using PowerShell commands in a Dockerfile to set up Windows Containers</span></span> 

<span data-ttu-id="bed48-337">[Windows kapsayıcıları](https://msdn.microsoft.com/en-us/virtualization/windowscontainers/about/about_overview) mevcut Windows uygulamalarınızı Docker görüntüleri olarak dönüştürmek ve Docker ekosistemi sayesinde geri kalanı gibi aynı araçları ile dağıtmaya olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="bed48-337">[Windows Containers](https://msdn.microsoft.com/en-us/virtualization/windowscontainers/about/about_overview) allow you to convert your existing Windows applications into Docker images and deploy them with the same tools as the rest of the Docker ecosystem.</span></span> <span data-ttu-id="bed48-338">Windows kapsayıcıları kullanmak için aşağıdaki örnekte gösterildiği gibi bir Dockerfile içinde PowerShell komutlarını çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="bed48-338">To use Windows Containers, you run PowerShell commands in the Dockerfile, as shown in the following example:</span></span>

```Dockerfile
FROM microsoft/windowsservercore
  
LABEL Description="IIS" Vendor="Microsoft" Version="10"
  
RUN powershell -Command Add-WindowsFeature Web-Server
  
CMD [ "ping", "localhost", "-t" ]
```

<span data-ttu-id="bed48-339">Bu durumda, biz bir Windows Server Core temel görüntüyü (FROM ayar) kullanarak ve bir (çalışma ayarı) PowerShell komutuyla IIS'yi yükleme.</span><span class="sxs-lookup"><span data-stu-id="bed48-339">In this case, we are using a Windows Server Core base image (the FROM setting) and installing IIS with a PowerShell command (the RUN setting).</span></span> <span data-ttu-id="bed48-340">Benzer şekilde, ASP.NET 4.x, .NET 4.6 veya herhangi bir Windows yazılımı gibi ek bileşenler ayarlamak için PowerShell komutlarını kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bed48-340">In a similar way, you could also use PowerShell commands to set up additional components like ASP.NET 4.x, .NET 4.6, or any other Windows software.</span></span> <span data-ttu-id="bed48-341">Örneğin, aşağıdaki komut bir Dockerfile içinde ASP.NET 4.5 ' ayarlar:</span><span class="sxs-lookup"><span data-stu-id="bed48-341">For example, the following command in a Dockerfile sets up ASP.NET 4.5:</span></span>

```Dockerfile
RUN powershell add-windowsfeature web-asp-net45
```

### <a name="additional-resources"></a><span data-ttu-id="bed48-342">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="bed48-342">Additional resources</span></span>

-   <span data-ttu-id="bed48-343">**aspnet-docker/Dockerfile.**</span><span class="sxs-lookup"><span data-stu-id="bed48-343">**aspnet-docker/Dockerfile.**</span></span> <span data-ttu-id="bed48-344">Windows özellikleri içerecek şekilde dockerfile'ları için örnek Powershell komutları.</span><span class="sxs-lookup"><span data-stu-id="bed48-344">Example Powershell commands to run from dockerfiles to include Windows features.</span></span>
    [*https://github.com/Microsoft/aspnet-docker/blob/master/4.6.2/Dockerfile*](https://github.com/Microsoft/aspnet-docker/blob/master/4.6.2/Dockerfile)

>[!div class="step-by-step"]
<span data-ttu-id="bed48-345">[Önceki](index.md)
[İleri](../net-core-single-containers-linux-windows-server-hosts/index.md)</span><span class="sxs-lookup"><span data-stu-id="bed48-345">[Previous](index.md)
[Next](../net-core-single-containers-linux-windows-server-hosts/index.md)</span></span>
