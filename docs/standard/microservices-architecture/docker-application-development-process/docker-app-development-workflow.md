---
title: Docker uygulamaları için geliştirme iş akışı
description: Docker tabanlı uygulamalar geliştirmek için iş akışının ayrıntılarını anlayın. Adım adım başlar ve dockerfile'ları iyileştirmek ve Visual Studio kullanırken kullanılabilir Basitleştirilmiş akışıyla sonlandırmak üzere bazı ayrıntıları alın.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 01/07/2019
ms.openlocfilehash: 97b8c40f0926edaf9ab743ac45ba498c96257622
ms.sourcegitcommit: 680a741667cf6859de71586a0caf6be14f4f7793
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59517986"
---
# <a name="development-workflow-for-docker-apps"></a><span data-ttu-id="f4eed-104">Docker uygulamaları için geliştirme iş akışı</span><span class="sxs-lookup"><span data-stu-id="f4eed-104">Development workflow for Docker apps</span></span>

<span data-ttu-id="f4eed-105">Uygulama geliştirme yaşam döngüsü, tercih ettiğiniz dili kullanarak uygulama kodu ve yerel olarak test bir geliştirici olarak, bilgisayarınızın başında başlatır.</span><span class="sxs-lookup"><span data-stu-id="f4eed-105">The application development life cycle starts at your computer, as a developer, where you code the application using your preferred language and test it locally.</span></span> <span data-ttu-id="f4eed-106">Hangi dil, çerçeve ve seçtiğiniz platform ne olursa olsun bu iş akışı ile her zaman geliştirme ve Docker kapsayıcılarını test, ancak bunun yerel olarak yapılması.</span><span class="sxs-lookup"><span data-stu-id="f4eed-106">With this workflow, no matter which language, framework, and platform you choose, you're always developing and testing Docker containers, but doing so locally.</span></span>

<span data-ttu-id="f4eed-107">Her kapsayıcı (bir Docker görüntüsü örneği), aşağıdaki bileşenleri içerir:</span><span class="sxs-lookup"><span data-stu-id="f4eed-107">Each container (an instance of a Docker image) includes the following components:</span></span>

- <span data-ttu-id="f4eed-108">Bir işletim sistemi seçimi, örneğin, bir Linux dağıtımı, Windows Nano sunucu veya Windows Server Core.</span><span class="sxs-lookup"><span data-stu-id="f4eed-108">An operating system selection, for example, a Linux distribution, Windows Nano Server, or Windows Server Core.</span></span>

- <span data-ttu-id="f4eed-109">Örneğin, kaynak kod ve uygulama ikili dosyalarını geliştirme sırasında eklenen dosyaları.</span><span class="sxs-lookup"><span data-stu-id="f4eed-109">Files added during development, for example, source code and application binaries.</span></span>

- <span data-ttu-id="f4eed-110">Ortam ayarlarını ve bağımlılıklarını gibi yapılandırma bilgileri.</span><span class="sxs-lookup"><span data-stu-id="f4eed-110">Configuration information, such as environment settings and dependencies.</span></span>

## <a name="workflow-for-developing-docker-container-based-applications"></a><span data-ttu-id="f4eed-111">Docker kapsayıcı tabanlı uygulamaları geliştirmek için iş akışı</span><span class="sxs-lookup"><span data-stu-id="f4eed-111">Workflow for developing Docker container-based applications</span></span>

<span data-ttu-id="f4eed-112">Bu bölümde açıklanmaktadır *iç döngü* Docker kapsayıcı tabanlı uygulamaları için geliştirme iş akışı.</span><span class="sxs-lookup"><span data-stu-id="f4eed-112">This section describes the *inner-loop* development workflow for Docker container-based applications.</span></span> <span data-ttu-id="f4eed-113">İç döngü iş akışı, üretim dağıtıma kadar içerebilir ve yalnızca geliştiricinin bilgisayarında geliştirme çalışmanın odaklanır daha geniş DevOps iş akışını dikkate yok anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="f4eed-113">The inner-loop workflow means it's not considering the broader DevOps workflow, that can include up to production deployment, and just focuses on the development work done on the developer's computer.</span></span> <span data-ttu-id="f4eed-114">Bu adımlar yalnızca bir kez gerçekleştirilir beri ortamı ayarlamak için ilk adımlarında dahil değildir.</span><span class="sxs-lookup"><span data-stu-id="f4eed-114">The initial steps to set up the environment aren't included, since those steps are done only once.</span></span>

<span data-ttu-id="f4eed-115">Uygulamanın kendi Hizmetleri ve ek kitaplıklar (bağımlılıklar) karakterlerinden oluşur.</span><span class="sxs-lookup"><span data-stu-id="f4eed-115">An application is composed of your own services plus additional libraries (dependencies).</span></span> <span data-ttu-id="f4eed-116">Aşağıda, genellikle bir Docker uygulaması oluştururken Şekil 5-1'de gösterildiği gibi temel adımlar verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="f4eed-116">The following are the basic steps you usually take when building a Docker application, as illustrated in Figure 5-1.</span></span>

![<span data-ttu-id="f4eed-117">Docker uygulamaları için geliştirme işlemi: 2 - uygulamanızı 1 - kod yazma Dockerfile/sn, 3 - Dockerfile/sn, 4 - (isteğe bağlı) oluşturma hizmetleri docker-compose.yml dosyasında tanımlanan görüntüler oluşturmak, depoyu ve yineleme - kapsayıcı çalıştırın veya docker-compose uygulaması, 6 - uygulama ve mikro hizmetler, 7 Test - 5 anında iletme.</span><span class="sxs-lookup"><span data-stu-id="f4eed-117">The development process for Docker apps: 1 - Code your App, 2 - Write Dockerfile/s, 3 - Create images defined at Dockerfile/s, 4 - (optional) Compose services in the docker-compose.yml file, 5 - Run container or docker-compose app, 6 - Test your app or microservices, 7 - Push to repo and repeat.</span></span> ](./media/image1.png)

<span data-ttu-id="f4eed-118">**Şekil 5-1.**</span><span class="sxs-lookup"><span data-stu-id="f4eed-118">**Figure 5-1.**</span></span> <span data-ttu-id="f4eed-119">Kapsayıcılı Docker uygulamaları geliştirmeye yönelik adım adım iş akışı</span><span class="sxs-lookup"><span data-stu-id="f4eed-119">Step-by-step workflow for developing Docker containerized apps</span></span>

<span data-ttu-id="f4eed-120">Bu bölümde, tüm bu işlemi ayrıntılı olarak verilmiştir ve önemli adım her bir Visual Studio ortamında odaklanarak açıklanmıştır.</span><span class="sxs-lookup"><span data-stu-id="f4eed-120">In this section, this whole process is detailed and every major step is explained by focusing on a Visual Studio environment.</span></span>

<span data-ttu-id="f4eed-121">Bir düzenleyici/CLI geliştirme yaklaşımını (örneğin, Visual Studio Code ve Docker CLI'yı MacOS ya da Windows) kullanırken, her adım genellikle Visual Studio kullanıyorsanız, daha ayrıntılı biçimde bilmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="f4eed-121">When you're using an editor/CLI development approach (for example, Visual Studio Code plus Docker CLI on macOS or Windows), you need to know every step, generally in more detail than if you're using Visual Studio.</span></span> <span data-ttu-id="f4eed-122">E-kitabı CLI ortamda çalışma hakkında daha fazla bilgi için bkz. [Microsoft Platforms ve araçlarla kapsayıcılı Docker uygulaması yaşam döngüsü](https://aka.ms/dockerlifecycleebook/).</span><span class="sxs-lookup"><span data-stu-id="f4eed-122">For more information about working in a CLI environment, see the e-book [Containerized Docker Application lifecycle with Microsoft Platforms and Tools](https://aka.ms/dockerlifecycleebook/).</span></span>

<span data-ttu-id="f4eed-123">Visual Studio 2017 kullanırken, bu adımların çoğunu sizin yerinize üretkenliğinizi önemli ölçüde artıran işlenir.</span><span class="sxs-lookup"><span data-stu-id="f4eed-123">When you're using Visual Studio 2017, many of those steps are handled for you, which dramatically improves your productivity.</span></span> <span data-ttu-id="f4eed-124">Bu, özellikle kullandığınız Visual Studio 2017 ve çok kapsayıcılı uygulamalar hedefleme olduğunda geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="f4eed-124">This is especially true when you're using Visual Studio 2017 and targeting multi-container applications.</span></span> <span data-ttu-id="f4eed-125">Örneğin, yalnızca tek bir tıklatmayla projelerinize uygulamanız için yapılandırma ile Dockerfile ve docker-compose.yml dosyası Visual Studio ekler.</span><span class="sxs-lookup"><span data-stu-id="f4eed-125">For instance, with just one mouse click, Visual Studio adds the Dockerfile and docker-compose.yml file to your projects with the configuration for your application.</span></span> <span data-ttu-id="f4eed-126">Visual Studio'da uygulamayı çalıştırdığınızda, Docker görüntüsünü oluşturur ve çok kapsayıcılı bir uygulama doğrudan Docker'da çalıştırılır; bile aynı anda birden fazla kapsayıcılar ayıklamanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="f4eed-126">When you run the application in Visual Studio, it builds the Docker image and runs the multi-container application directly in Docker; it even allows you to debug several containers at once.</span></span> <span data-ttu-id="f4eed-127">Bu özellikler, geliştirme hızını çok artırır.</span><span class="sxs-lookup"><span data-stu-id="f4eed-127">These features will boost your development speed.</span></span>

<span data-ttu-id="f4eed-128">Yalnızca Visual Studio bu adımlar otomatik hale getirir ancak neler olduğunu bilmeniz gerekmez gelmez üzerinde underneath Docker ile.</span><span class="sxs-lookup"><span data-stu-id="f4eed-128">However, just because Visual Studio makes those steps automatic doesn't mean that you don't need to know what's going on underneath with Docker.</span></span> <span data-ttu-id="f4eed-129">Bu nedenle, aşağıdaki yönergeleri her adım ayrıntılı olarak açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="f4eed-129">Therefore, the following guidance details every step.</span></span>

![1 - uygulamanızı kodlayın](./media/image2.png)

## <a name="step-1-start-coding-and-create-your-initial-application-or-service-baseline"></a><span data-ttu-id="f4eed-131">Adım 1.</span><span class="sxs-lookup"><span data-stu-id="f4eed-131">Step 1.</span></span> <span data-ttu-id="f4eed-132">Kodlamaya başlayın ve ilk uygulama veya hizmet taban çizgisi oluşturma</span><span class="sxs-lookup"><span data-stu-id="f4eed-132">Start coding and create your initial application or service baseline</span></span>

<span data-ttu-id="f4eed-133">Docker uygulaması geliştirmek, Docker olmadan uygulama geliştirme şekilde benzerdir.</span><span class="sxs-lookup"><span data-stu-id="f4eed-133">Developing a Docker application is similar to the way you develop an application without Docker.</span></span> <span data-ttu-id="f4eed-134">Docker için geliştirmeye devam ederken, dağıtma ve uygulama ya da Windows kapsayıcıları kullanıyorsanız, yerel ortamınızda (Docker ile bir Linux VM Kurulumu) ya da doğrudan Windows Docker kapsayıcıları içinde çalışan hizmetleri test etme, farktır.</span><span class="sxs-lookup"><span data-stu-id="f4eed-134">The difference is that while developing for Docker, you're deploying and testing your application or services running within Docker containers in your local environment (either a Linux VM setup by Docker or directly Windows if using Windows Containers).</span></span>

### <a name="set-up-your-local-environment-with-visual-studio"></a><span data-ttu-id="f4eed-135">Visual Studio ile yerel ortamınızı ayarlayın</span><span class="sxs-lookup"><span data-stu-id="f4eed-135">Set up your local environment with Visual Studio</span></span>

<span data-ttu-id="f4eed-136">Başlamak için sahip olduğunuzdan emin olun [Docker Community Edition'ı (CE)](https://docs.docker.com/docker-for-windows/) aşağıdaki yönergelerinde açıklandığı gibi yüklü Windows için:</span><span class="sxs-lookup"><span data-stu-id="f4eed-136">To begin, make sure you have [Docker Community Edition (CE)](https://docs.docker.com/docker-for-windows/) for Windows installed, as explained in the following instructions:</span></span>

[<span data-ttu-id="f4eed-137">İçin Docker CE Windows ile çalışmaya başlama</span><span class="sxs-lookup"><span data-stu-id="f4eed-137">Get started with Docker CE for Windows</span></span>](https://docs.docker.com/docker-for-windows/)

<span data-ttu-id="f4eed-138">Ayrıca, Visual Studio 2017 sürüm 15.7 veya üzeri ile ihtiyacınız **.NET Core çoklu platform geliştirme** yüklüyse, Şekil 5-2'de gösterildiği gibi iş yükü.</span><span class="sxs-lookup"><span data-stu-id="f4eed-138">In addition, you need Visual Studio 2017 version 15.7 or later, with the **.NET Core cross-platform development** workload installed, as shown in Figure 5-2.</span></span>

![.NET core çoklu platform geliştirme iş yükü seçimi, Visual Studio yüklemesi sırasında.](./media/image3.png)

<span data-ttu-id="f4eed-140">**Şekil 5-2**.</span><span class="sxs-lookup"><span data-stu-id="f4eed-140">**Figure 5-2**.</span></span> <span data-ttu-id="f4eed-141">Seçme **.NET Core çoklu platform geliştirme** Visual Studio 2017 Kurulum sırasında iş yükü</span><span class="sxs-lookup"><span data-stu-id="f4eed-141">Selecting the **.NET Core cross-platform development** workload during Visual Studio 2017 setup</span></span>

<span data-ttu-id="f4eed-142">Uygulamanızda Docker'ı etkinleştirme ve Docker sınama dağıtımı önce (genellikle, kapsayıcıları kullanmayı planlıyorsanız, .NET Core) düz .NET uygulamanızda kodlamaya başlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f4eed-142">You can start coding your application in plain .NET (usually in .NET Core if you're planning to use containers) even before enabling Docker in your application and deploying and testing in Docker.</span></span> <span data-ttu-id="f4eed-143">Ancak, üzerinde Docker olabildiğince çabuk, çünkü gerçek ortam olacak ve sorunları olabildiğince çabuk bulunabileceğini çalışma başlangıç önerilir.</span><span class="sxs-lookup"><span data-stu-id="f4eed-143">However, it is recommended that you start working on Docker as soon as possible, because that will be the real environment and any issues can be discovered as soon as possible.</span></span> <span data-ttu-id="f4eed-144">Visual Studio, bu nedenle, neredeyse saydam hissettiği Docker'la çalışmak kolaylaştırır çünkü bu teşvik edilir — çok kapsayıcılı uygulamalar Visual Studio'dan hata ayıklama sırasında en iyi örnek.</span><span class="sxs-lookup"><span data-stu-id="f4eed-144">This is encouraged because Visual Studio makes it so easy to work with Docker that it almost feels transparent—the best example when debugging multi-container applications from Visual Studio.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="f4eed-145">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="f4eed-145">Additional resources</span></span>

- <span data-ttu-id="f4eed-146">**İçin Docker CE Windows ile çalışmaya başlama** \\</span><span class="sxs-lookup"><span data-stu-id="f4eed-146">**Get started with Docker CE for Windows** \\</span></span>
  [https://docs.docker.com/docker-for-windows/](https://docs.docker.com/docker-for-windows/)

- <span data-ttu-id="f4eed-147">**Visual Studio 2017** \\</span><span class="sxs-lookup"><span data-stu-id="f4eed-147">**Visual Studio 2017** \\</span></span>
  [https://visualstudio.microsoft.com/downloads/](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017)

![2 - dockerfile'ları yazma](./media/image4.png)

## <a name="step-2-create-a-dockerfile-related-to-an-existing-net-base-image"></a><span data-ttu-id="f4eed-149">Adım 2.</span><span class="sxs-lookup"><span data-stu-id="f4eed-149">Step 2.</span></span> <span data-ttu-id="f4eed-150">Mevcut bir .NET temel görüntü için ilgili bir Dockerfile'ı oluşturma</span><span class="sxs-lookup"><span data-stu-id="f4eed-150">Create a Dockerfile related to an existing .NET base image</span></span>

<span data-ttu-id="f4eed-151">Derlemek istediğiniz her özel görüntü için bir Dockerfile ihtiyacınız; Ayrıca Visual Studio veya el ile Docker CLI'yı kullanarak otomatik olarak dağıtıp dağıtmamak dağıtılması için her kapsayıcı için bir Dockerfile gerekir (docker run ve docker-compose komutları).</span><span class="sxs-lookup"><span data-stu-id="f4eed-151">You need a Dockerfile for each custom image you want to build; you also need a Dockerfile for each container to be deployed, whether you deploy automatically from Visual Studio or manually using the Docker CLI (docker run and docker-compose commands).</span></span> <span data-ttu-id="f4eed-152">Uygulamanızda tek bir özel hizmet varsa, tek bir Dockerfile gerekir.</span><span class="sxs-lookup"><span data-stu-id="f4eed-152">If your application contains a single custom service, you need a single Dockerfile.</span></span> <span data-ttu-id="f4eed-153">Uygulamanız birden çok hizmeti (olduğu gibi bir mikro hizmetler mimarisinde) içeriyorsa, her hizmet için bir Dockerfile gerekir.</span><span class="sxs-lookup"><span data-stu-id="f4eed-153">If your application contains multiple services (as in a microservices architecture), you need one Dockerfile for each service.</span></span>

<span data-ttu-id="f4eed-154">Dockerfile, uygulamanızın veya hizmetinizin kök klasöründe yer alır.</span><span class="sxs-lookup"><span data-stu-id="f4eed-154">The Dockerfile is placed in the root folder of your application or service.</span></span> <span data-ttu-id="f4eed-155">Bu, Docker ayarlama ve bir kapsayıcıdaki uygulama veya hizmetinizin çalıştırma bildiririz komutlar içerir.</span><span class="sxs-lookup"><span data-stu-id="f4eed-155">It contains the commands that tell Docker how to set up and run your application or service in a container.</span></span> <span data-ttu-id="f4eed-156">El ile bir Dockerfile içinde kod oluşturma ve birlikte .NET bağımlılıklarınızı projenize ekleyin.</span><span class="sxs-lookup"><span data-stu-id="f4eed-156">You can manually create a Dockerfile in code and add it to your project along with your .NET dependencies.</span></span>

<span data-ttu-id="f4eed-157">Bu görevi, Visual Studio ve araçları için Docker ile yalnızca birkaç tıklamayla gerektirir.</span><span class="sxs-lookup"><span data-stu-id="f4eed-157">With Visual Studio and its tools for Docker, this task requires only a few mouse clicks.</span></span> <span data-ttu-id="f4eed-158">Visual Studio 2017'de yeni bir proje oluşturduğunuzda, adlı bir seçenek yoktur **kapsayıcı etkinleştir (Docker) desteği**Şekil 5-3'te gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="f4eed-158">When you create a new project in Visual Studio 2017, there's an option named **Enable Container (Docker) Support**, as shown in Figure 5-3.</span></span>

![Visual Studio 2017'de yeni bir ASP.NET Core projesi oluştururken, Docker desteği onay kutusunu etkinleştir](./media/image5.png)

<span data-ttu-id="f4eed-160">**Şekil 5-3**.</span><span class="sxs-lookup"><span data-stu-id="f4eed-160">**Figure 5-3**.</span></span> <span data-ttu-id="f4eed-161">Visual Studio 2017'de yeni bir ASP.NET Core projesi oluştururken, Docker desteğini etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="f4eed-161">Enabling Docker Support when creating a new ASP.NET Core project in Visual Studio 2017</span></span>

<span data-ttu-id="f4eed-162">Projeye sağ tıklayarak mevcut bir ASP.NET Core web uygulaması projesini Docker desteğini de etkinleştirebilirsiniz **Çözüm Gezgini** seçerek **Ekle** > **Docker desteği** Şekil 5-4'te gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="f4eed-162">You can also enable Docker support on an existing ASP.NET Core web app project by right-clicking the project in **Solution Explorer** and selecting **Add** > **Docker Support**, as shown in Figure 5-4.</span></span>

![Visual Studio'da Docker desteği menü seçeneği ekleyin](./media/image6.png)

<span data-ttu-id="f4eed-164">**Şekil 5-4**.</span><span class="sxs-lookup"><span data-stu-id="f4eed-164">**Figure 5-4**.</span></span> <span data-ttu-id="f4eed-165">Mevcut bir Visual Studio 2017 projesinde Docker desteğini etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="f4eed-165">Enabling Docker support in an existing Visual Studio 2017 project</span></span>

<span data-ttu-id="f4eed-166">Bu eylem ekler bir *Dockerfile* gerekli yapılandırmayla projeye ve ASP.NET Core projelerinde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="f4eed-166">This action adds a *Dockerfile* to the project with the required configuration, and is only available on ASP.NET Core projects.</span></span>

<span data-ttu-id="f4eed-167">Benzer şekilde, Visual Studio da çözümün tamamının seçeneğiyle için bir docker-compose.yml dosyası ekleyebilirsiniz **Ekle > kapsayıcı Düzenleyicisi desteği**.</span><span class="sxs-lookup"><span data-stu-id="f4eed-167">In a similar fashion, Visual Studio can also add a docker-compose.yml file for the whole solution with the option **Add > Container Orchestrator Support**.</span></span> <span data-ttu-id="f4eed-168">4. adımda bu seçenek daha ayrıntılı şunları keşfedeceğiz.</span><span class="sxs-lookup"><span data-stu-id="f4eed-168">In step 4, we'll explore this option in greater detail.</span></span>

### <a name="using-an-existing-official-net-docker-image"></a><span data-ttu-id="f4eed-169">Mevcut bir resmi .NET Docker görüntüsü kullanma</span><span class="sxs-lookup"><span data-stu-id="f4eed-169">Using an existing official .NET Docker image</span></span>

<span data-ttu-id="f4eed-170">Alma gibi resmi bir depodan bir temel görüntünün üstüne kapsayıcınız için genellikle özel bir görüntü oluşturun [Docker Hub](https://hub.docker.com/) kayıt defteri.</span><span class="sxs-lookup"><span data-stu-id="f4eed-170">You usually build a custom image for your container on top of a base image you get from an official repository like the [Docker Hub](https://hub.docker.com/) registry.</span></span> <span data-ttu-id="f4eed-171">Visual Studio'da Docker desteğini etkinleştirmek ne olacağını perde tam olarak olmasıdır.</span><span class="sxs-lookup"><span data-stu-id="f4eed-171">That is precisely what happens under the covers when you enable Docker support in Visual Studio.</span></span> <span data-ttu-id="f4eed-172">Mevcut bir Dockerfile kullanacağı `aspnetcore` görüntü.</span><span class="sxs-lookup"><span data-stu-id="f4eed-172">Your Dockerfile will use an existing `aspnetcore` image.</span></span>

<span data-ttu-id="f4eed-173">Daha önce hangi Docker görüntülerini ve seçtiğiniz işletim sistemi ve framework bağlı olarak kullanabilirsiniz depoları açıklanmıştır.</span><span class="sxs-lookup"><span data-stu-id="f4eed-173">Earlier we explained which Docker images and repos you can use, depending on the framework and OS you have chosen.</span></span> <span data-ttu-id="f4eed-174">Örneğin, ASP.NET Core (Linux veya Windows) kullanmak istiyorsanız, kullanılacak görüntüyü olan `mcr.microsoft.com/dotnet/core/aspnet:2.2`.</span><span class="sxs-lookup"><span data-stu-id="f4eed-174">For instance, if you want to use ASP.NET Core (Linux or Windows), the image to use is `mcr.microsoft.com/dotnet/core/aspnet:2.2`.</span></span> <span data-ttu-id="f4eed-175">Bu nedenle, kapsayıcınız için kullanacağınız hangi temel Docker görüntüsüne belirtmeniz yeterlidir.</span><span class="sxs-lookup"><span data-stu-id="f4eed-175">Therefore, you just need to specify what base Docker image you will use for your container.</span></span> <span data-ttu-id="f4eed-176">Ekleyerek bunu `FROM mcr.microsoft.com/dotnet/core/aspnet:2.2` Dockerfile için.</span><span class="sxs-lookup"><span data-stu-id="f4eed-176">You do that by adding `FROM mcr.microsoft.com/dotnet/core/aspnet:2.2` to your Dockerfile.</span></span> <span data-ttu-id="f4eed-177">Bu Visual Studio tarafından otomatik olarak gerçekleştirilir, ancak sürüm olsaydı, bu değeri güncelleştirin.</span><span class="sxs-lookup"><span data-stu-id="f4eed-177">This will be automatically performed by Visual Studio, but if you were to update the version, you update this value.</span></span>

<span data-ttu-id="f4eed-178">Bir sürüm numarası ile Docker Hub resmi bir .NET görüntü deposundan kullanarak aynı dil özellikleri (geliştirme, test ve üretim dahil) tüm makinelerde kullanılabilir olmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="f4eed-178">Using an official .NET image repository from Docker Hub with a version number ensures that the same language features are available on all machines (including development, testing, and production).</span></span>

<span data-ttu-id="f4eed-179">Aşağıdaki örnek bir ASP.NET Core kapsayıcı için bir örnek Dockerfile gösterir.</span><span class="sxs-lookup"><span data-stu-id="f4eed-179">The following example shows a sample Dockerfile for an ASP.NET Core container.</span></span>

```Dockerfile
FROM mcr.microsoft.com/dotnet/core/aspnet:2.2
ARG source
WORKDIR /app
EXPOSE 80
COPY ${source:-obj/Docker/publish} .
ENTRYPOINT ["dotnet", " MySingleContainerWebApp.dll "]
```

<span data-ttu-id="f4eed-180">Bu durumda, görüntü resmi ASP.NET Core Docker görüntü (Linux ve Windows için çok arch) 2.2 sürümünü temel alır.</span><span class="sxs-lookup"><span data-stu-id="f4eed-180">In this case, the image is based on version 2.2 of the official ASP.NET Core Docker image (multi-arch for Linux and Windows).</span></span> <span data-ttu-id="f4eed-181">Ayar budur `FROM mcr.microsoft.com/dotnet/core/aspnet:2.2`.</span><span class="sxs-lookup"><span data-stu-id="f4eed-181">This is the setting `FROM mcr.microsoft.com/dotnet/core/aspnet:2.2`.</span></span> <span data-ttu-id="f4eed-182">(Bu temel görüntü hakkında daha fazla bilgi için bkz: [.NET Core, Docker görüntüsü](https://hub.docker.com/_/microsoft-dotnet-core/) sayfası.) Dockerfile içinde ayrıca isteyin (Bu durumda, SUNMAYA ayarı ile yapılandırılmış olarak 80 numaralı bağlantı noktası) çalışma zamanında kullanacağınız TCP bağlantı noktasında dinlemek için Docker gerekir.</span><span class="sxs-lookup"><span data-stu-id="f4eed-182">(For more information about this base image, see the [.NET Core Docker Image](https://hub.docker.com/_/microsoft-dotnet-core/) page.) In the Dockerfile, you also need to instruct Docker to listen on the TCP port you will use at runtime (in this case, port 80, as configured with the EXPOSE setting).</span></span>

<span data-ttu-id="f4eed-183">Dil ve çerçeve kullanmakta olduğunuz bağlı olarak bir Dockerfile içinde ek yapılandırma ayarları belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f4eed-183">You can specify additional configuration settings in the Dockerfile, depending on the language and framework you're using.</span></span> <span data-ttu-id="f4eed-184">Örneğin, giriş noktası satırla `["dotnet", "MySingleContainerWebApp.dll"]` bir .NET Core uygulamasını çalıştırmak için Docker söyler.</span><span class="sxs-lookup"><span data-stu-id="f4eed-184">For instance, the ENTRYPOINT line with `["dotnet", "MySingleContainerWebApp.dll"]` tells Docker to run a .NET Core application.</span></span> <span data-ttu-id="f4eed-185">.NET uygulaması derleme ve çalıştırma için SDK ve .NET Core CLI (dotnet CLI) kullanıyorsanız, bu ayar farklı olacaktır.</span><span class="sxs-lookup"><span data-stu-id="f4eed-185">If you're using the SDK and the .NET Core CLI (dotnet CLI) to build and run the .NET application, this setting would be different.</span></span> <span data-ttu-id="f4eed-186">ENTRYPOINT satır ve diğer ayarları uygulamanız için seçtiğiniz dile ve platforma bağlı olarak farklı olacaktır alt çizgidir.</span><span class="sxs-lookup"><span data-stu-id="f4eed-186">The bottom line is that the ENTRYPOINT line and other settings will be different depending on the language and platform you choose for your application.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="f4eed-187">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="f4eed-187">Additional resources</span></span>

- <span data-ttu-id="f4eed-188">**.NET Core uygulamaları için Docker görüntüleri oluşturma** \\</span><span class="sxs-lookup"><span data-stu-id="f4eed-188">**Building Docker Images for .NET Core Applications** \\</span></span>
  [https://docs.microsoft.com/dotnet/core/docker/building-net-docker-images](../../../core/docker/building-net-docker-images.md)

- <span data-ttu-id="f4eed-189">**Kendi görüntünüzü**.</span><span class="sxs-lookup"><span data-stu-id="f4eed-189">**Build your own image**.</span></span> <span data-ttu-id="f4eed-190">Resmi Docker belgelerinde. \\</span><span class="sxs-lookup"><span data-stu-id="f4eed-190">In the official Docker documentation.\\</span></span>
  [https://docs.docker.com/engine/tutorials/dockerimages/](https://docs.docker.com/engine/tutorials/dockerimages/)

- <span data-ttu-id="f4eed-191">**.NET ile kapsayıcı görüntülerini güncel kalma** \\</span><span class="sxs-lookup"><span data-stu-id="f4eed-191">**Staying up-to-date with .NET Container Images** \\</span></span>
  <https://devblogs.microsoft.com/dotnet/staying-up-to-date-with-net-container-images/>

- <span data-ttu-id="f4eed-192">**.NET ve Docker'a DockerCon 2018 güncelleştirmesi birlikte - kullanma** \\</span><span class="sxs-lookup"><span data-stu-id="f4eed-192">**Using .NET and Docker Together - DockerCon 2018 Update** \\</span></span>
  <https://devblogs.microsoft.com/dotnet/using-net-and-docker-together-dockercon-2018-update/>

### <a name="using-multi-arch-image-repositories"></a><span data-ttu-id="f4eed-193">Çok yay görüntü depolarını kullanarak</span><span class="sxs-lookup"><span data-stu-id="f4eed-193">Using multi-arch image repositories</span></span>

<span data-ttu-id="f4eed-194">Tek bir depoda bir Linux görüntüsü ve bir Windows görüntüsünü gibi platformu çeşitleri içerebilir.</span><span class="sxs-lookup"><span data-stu-id="f4eed-194">A single repo can contain platform variants, such as a Linux image and a Windows image.</span></span> <span data-ttu-id="f4eed-195">Bu özellik, (yani Linux ve Windows) birden çok platform karşılamak için tek depo oluşturmak Microsoft (temel Görüntü Oluşturucu) gibi satıcıları sağlar.</span><span class="sxs-lookup"><span data-stu-id="f4eed-195">This feature allows vendors like Microsoft (base image creators) to create a single repo to cover multiple platforms (that is Linux and Windows).</span></span> <span data-ttu-id="f4eed-196">Örneğin, [dotnet/core](https://hub.docker.com/_/microsoft-dotnet-core/) Docker Hub kayıt defterinde depo aynı depo adını kullanarak Linux ve Windows Nano sunucu için destek sağlar.</span><span class="sxs-lookup"><span data-stu-id="f4eed-196">For example, the [dotnet/core](https://hub.docker.com/_/microsoft-dotnet-core/) repository available in the Docker Hub registry provides support for Linux and Windows Nano Server by using the same repo name.</span></span>

<span data-ttu-id="f4eed-197">Açık bir platformu hedefleyen bir etiket belirtirseniz, aşağıdaki durumlarda ister:</span><span class="sxs-lookup"><span data-stu-id="f4eed-197">If you specify a tag, targeting a platform that is explicit like in the following cases:</span></span>

- `microsoft/dotnet:2.2-aspnetcore-runtime-stretch-slim` \
  <span data-ttu-id="f4eed-198">Hedefleri: .NET Core çalışma zamanı Linux üzerinde yalnızca 2.2</span><span class="sxs-lookup"><span data-stu-id="f4eed-198">Targets: .NET Core 2.2 runtime-only on Linux</span></span>

- `microsoft/dotnet:2.2-aspnetcore-runtime-nanoserver-1809` \
  <span data-ttu-id="f4eed-199">Hedefleri: .NET Core çalışma zamanı Windows Nano Sunucu'da yalnızca 2.2</span><span class="sxs-lookup"><span data-stu-id="f4eed-199">Targets: .NET Core 2.2 runtime-only on Windows Nano Server</span></span>

<span data-ttu-id="f4eed-200">Ancak, görüntü adının aynısını bile aynı etiketi ile çok yay görüntüleri belirtirseniz (gibi `aspnetcore` görüntü) dağıtmakta, Linux veya Windows sürümü işletim sistemi Docker konağı bağlı olarak aşağıdaki örnekte gösterildiği gibi kullanın:</span><span class="sxs-lookup"><span data-stu-id="f4eed-200">But, if you specify the same image name, even with the same tag, the multi-arch images (like the `aspnetcore` image) will use the Linux or Windows version depending on the Docker host OS you're deploying, as shown in the following example:</span></span>

- `microsoft/dotnet:2.2-aspnetcore-runtime` \
  <span data-ttu-id="f4eed-201">Çok arch: .NET Core çalışma zamanı Linux veya Windows Nano sunucu üzerinde Docker ana bilgisayar işletim sistemi bağlı olarak yalnızca 2.2</span><span class="sxs-lookup"><span data-stu-id="f4eed-201">Multi-arch: .NET Core 2.2 runtime-only on Linux or Windows Nano Server depending on the Docker host OS</span></span>

<span data-ttu-id="f4eed-202">Windows konaktan görüntü çekme bu şekilde, Windows değişken çeker ve bir Linux ana bilgisayarından görüntü adının aynısını çekme Linux değişken çeker.</span><span class="sxs-lookup"><span data-stu-id="f4eed-202">This way, when you pull an image from a Windows host, it will pull the Windows variant, and pulling the same image name from a Linux host will pull the Linux variant.</span></span>

### <a name="multi-stage-builds-in-dockerfile"></a><span data-ttu-id="f4eed-203">Çok aşamalı Dockerfile içinde oluşturur.</span><span class="sxs-lookup"><span data-stu-id="f4eed-203">Multi-stage builds in Dockerfile</span></span>

<span data-ttu-id="f4eed-204">Dockerfile, bir batch betiğiyle aynıdır.</span><span class="sxs-lookup"><span data-stu-id="f4eed-204">The Dockerfile is similar to a batch script.</span></span> <span data-ttu-id="f4eed-205">Benzer komut satırından makine kurmak tablonuz varsa ne yapmanız.</span><span class="sxs-lookup"><span data-stu-id="f4eed-205">Similar to what you would do if you had to set up the machine from the command line.</span></span>

<span data-ttu-id="f4eed-206">Başlangıç bağlamı ayarlar temel bir görüntü ile başlar, konak işletim sistemi en üstünde yer alan başlangıç dosya sistemi gibidir.</span><span class="sxs-lookup"><span data-stu-id="f4eed-206">It starts with a base image that sets up the initial context, it's like the startup filesystem, that sits on top of the host OS.</span></span> <span data-ttu-id="f4eed-207">Bir işletim sistemi değil, ancak kapsayıcı içinde "" işletim sistemi, gibi düşünebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f4eed-207">It's not an OS, but you can think of if like "the" OS inside the container.</span></span>

<span data-ttu-id="f4eed-208">Her komut satırı yürütme, Öncekine değişikliklerle sisteminde yeni bir katman oluşturur. böylece, birleştirildiğinde, sonuçta elde edilen dosya sistemi üretir.</span><span class="sxs-lookup"><span data-stu-id="f4eed-208">The execution of every command line creates a new layer on the filesystem with the changes from the previous one, so that, when combined, produce the resulting filesystem.</span></span>

<span data-ttu-id="f4eed-209">Her yeni katmanı "ye dayanıyorsa eskisinin üzerine" ve her komut ile elde edilen görüntü boyutunu artırır olduğundan, görüntüleri içerecek şekilde oluşturulduysa Örneğin, SDK'sı geliştirmek ve uygulama yayımlamak için gereken çok büyük alabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f4eed-209">Since every new layer "rests" on top of the previous one and the resulting image size increases with every command, images can get very large if they have to include, for example, the SDK needed to build and publish an application.</span></span>

<span data-ttu-id="f4eed-210">Çok aşamalı yapılar (Docker 17.05 ve üzeri) çizim kendi Sihirli yapmak nereden budur.</span><span class="sxs-lookup"><span data-stu-id="f4eed-210">This is where multi-stage builds get into the plot (from Docker 17.05 and higher) to do their magic.</span></span>

<span data-ttu-id="f4eed-211">Dockerfile yürütme işlemi burada ilk görüntü bir veya daha fazla komut tarafından izlenen bir aşamayı ifade eder ve son aşamasında son görüntü boyutunu belirler. aşamada ayırabilirsiniz çekirdek olur.</span><span class="sxs-lookup"><span data-stu-id="f4eed-211">The core idea is that you can separate the Dockerfile execution process in stages, where a stage is an initial image followed by one or more commands, and the last stage determines the final image size.</span></span>

<span data-ttu-id="f4eed-212">Kısacası, çok aşamalı yapılar farklı "aşamaları" içindeki oluşturma bölme izin vermek ve ardından Ara aşamaları yalnızca ilgili dizinlerden alma son görüntü birleştirin.</span><span class="sxs-lookup"><span data-stu-id="f4eed-212">In short, multi-stage builds allow splitting the creation in different "phases" and then assemble the final image taking only the relevant directories from the intermediate stages.</span></span> <span data-ttu-id="f4eed-213">Bu özelliği kullanmak için genel stratejisidir:</span><span class="sxs-lookup"><span data-stu-id="f4eed-213">The general strategy to use this feature is:</span></span>

1. <span data-ttu-id="f4eed-214">Temel bir SDK görüntüsünü kullanın (olması fark etmez ne kadar büyük), derleme ve uygulamayı bir klasöre yayımlamak için gereken her şeyi birlikte ve ardından</span><span class="sxs-lookup"><span data-stu-id="f4eed-214">Use a base SDK image (doesn't matter how large), with everything needed to build and publish the application to a folder and then</span></span>

2. <span data-ttu-id="f4eed-215">Temel, küçük, yalnızca çalışma zamanı bir görüntüyü kullanmak ve küçük bir son görüntü üretmek için önceki aşamadan yayımlama klasörüne kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="f4eed-215">Use a base, small, runtime-only image and copy the publishing folder from the previous stage to produce a small final image.</span></span>

<span data-ttu-id="f4eed-216">Büyük olasılıkla çok aşamalı bir Dockerfile içinde ayrıntılı olarak üzerinden geçiyor anlamak için en iyi yolu satır şimdi başlayın Docker'ı eklerken bir proje için destek ve bazı iyileştirmeler daha sonra alırsınız, Visual Studio tarafından oluşturulan ilk Dockerfile ile.</span><span class="sxs-lookup"><span data-stu-id="f4eed-216">Probably the best way to understand multi-stage is going through a Dockerfile in detail, line by line, so let's begin with the initial Dockerfile created by Visual Studio when adding Docker support to a project and will get into some optimizations later.</span></span>

<span data-ttu-id="f4eed-217">İlk Dockerfile aşağıdakine benzeyebilir:</span><span class="sxs-lookup"><span data-stu-id="f4eed-217">The initial Dockerfile might look something like this:</span></span>

```Dockerfile
 1  FROM mcr.microsoft.com/dotnet/core/aspnet:2.2 AS base
 2  WORKDIR /app
 3  EXPOSE 80
 4
 5  FROM mcr.microsoft.com/dotnet/core/sdk:2.2 AS build
 6  WORKDIR /src
 7  COPY src/Services/Catalog/Catalog.API/Catalog.API.csproj …
 8  COPY src/BuildingBlocks/HealthChecks/src/Microsoft.AspNetCore.HealthChecks … 
 9  COPY src/BuildingBlocks/HealthChecks/src/Microsoft.Extensions.HealthChecks …
10  COPY src/BuildingBlocks/EventBus/IntegrationEventLogEF/ …
11  COPY src/BuildingBlocks/EventBus/EventBus/EventBus.csproj …
12  COPY src/BuildingBlocks/EventBus/EventBusRabbitMQ/EventBusRabbitMQ.csproj …
13  COPY src/BuildingBlocks/EventBus/EventBusServiceBus/EventBusServiceBus.csproj …
14  COPY src/BuildingBlocks/WebHostCustomization/WebHost.Customization …
15  COPY src/BuildingBlocks/HealthChecks/src/Microsoft.Extensions …
16  COPY src/BuildingBlocks/HealthChecks/src/Microsoft.Extensions …
17  RUN dotnet restore src/Services/Catalog/Catalog.API/Catalog.API.csproj
18  COPY . .
19  WORKDIR /src/src/Services/Catalog/Catalog.API
20  RUN dotnet build Catalog.API.csproj -c Release -0 /app
21
22  FROM build AS publish
23  RUN dotnet publish Catalog.API.csproj -c Release -0 /app
24
25  FROM base AS final
26  WORKDIR /app
27  COPY --from=publish /app
28  ENTRYPOINT ["dotnet", "Catalog.API.dll"]
```

<span data-ttu-id="f4eed-218">Ve Ayrıntılar, satır satır şunlardır:</span><span class="sxs-lookup"><span data-stu-id="f4eed-218">And these are the details, line by line:</span></span>

1. <span data-ttu-id="f4eed-219">"Küçük" yalnızca çalışma zamanı temel görüntü ile bir aşama başlamak için bu çağrı **temel** başvuru.</span><span class="sxs-lookup"><span data-stu-id="f4eed-219">Begin a stage with a "small" runtime-only base image, call it **base** for reference.</span></span>
2. <span data-ttu-id="f4eed-220">Oluşturma **/app** görüntünün dizin.</span><span class="sxs-lookup"><span data-stu-id="f4eed-220">Create **/app** directory in the image.</span></span>
3. <span data-ttu-id="f4eed-221">Bağlantı noktasını kullanıma sunma **80**.</span><span class="sxs-lookup"><span data-stu-id="f4eed-221">Expose port **80**.</span></span>
<!-- skip -->
5. <span data-ttu-id="f4eed-222">"Büyük" görüntü ile yeni bir aşama oluşturma/yayımlama için başlangıç çağrısı **derleme** başvuru.</span><span class="sxs-lookup"><span data-stu-id="f4eed-222">Begin a new stage with "large" image for building/publishing, call it **build** for reference.</span></span>
6. <span data-ttu-id="f4eed-223">Dizin oluşturma **/src** görüntüde.</span><span class="sxs-lookup"><span data-stu-id="f4eed-223">Create directory **/src** in the image.</span></span>
7. <span data-ttu-id="f4eed-224">Satır en çok 16, başvurulan projeler kopyalama **.csproj** paketleri daha sonra geri yüklenmesi mümkün dosyaları gibi.</span><span class="sxs-lookup"><span data-stu-id="f4eed-224">Up to line 16, copy referenced projects **.csproj** files, to be able to restore packages later.</span></span>
<!-- skip -->
17. <span data-ttu-id="f4eed-225">Paketleri geri **Catalog.API** proje ve başvurulan proje.</span><span class="sxs-lookup"><span data-stu-id="f4eed-225">Restore packages for the **Catalog.API** project and the referenced projects.</span></span>
18. <span data-ttu-id="f4eed-226">Kopyalama **çözüm için tüm dizin ağacı** (içerdiği dosyaları veya dizinleri hariç **.dockerignore** dosya) öğesinden için **/src** görüntünün dizin.</span><span class="sxs-lookup"><span data-stu-id="f4eed-226">Copy **all directory tree for the solution** (except the files/directories included in the **.dockerignore** file) from to the **/src** directory in the image.</span></span>
19. <span data-ttu-id="f4eed-227">Geçerli klasörü Değiştir **Catalog.API** proje.</span><span class="sxs-lookup"><span data-stu-id="f4eed-227">Change current folder to **Catalog.API** project.</span></span>
20. <span data-ttu-id="f4eed-228">Proje (ve diğer proje bağımlılıkları) oluşturun ve çıkış için **/app** görüntünün dizin.</span><span class="sxs-lookup"><span data-stu-id="f4eed-228">Build project (and other project dependencies) and output to **/app** directory in the image.</span></span>
<!-- skip -->
22. <span data-ttu-id="f4eed-229">Derlemeden etmeden yeni aşama başlamak için bu çağrı **yayımlama** başvuru.</span><span class="sxs-lookup"><span data-stu-id="f4eed-229">Begin a new stage continuing from build, call it **publish** for reference.</span></span>
23. <span data-ttu-id="f4eed-230">Proje (ve bağımlılıkları) yayımlama ve çıkış için **/app** görüntünün dizin.</span><span class="sxs-lookup"><span data-stu-id="f4eed-230">Publish project (and dependencies) and output to **/app** directory in the image.</span></span>
<!-- skip -->
25. <span data-ttu-id="f4eed-231">Gelen etmeden yeni aşama başlamak **temel** ve onu çağırmak **son**</span><span class="sxs-lookup"><span data-stu-id="f4eed-231">Begin a new stage continuing from **base** and call it **final**</span></span>
26. <span data-ttu-id="f4eed-232">Geçerli dizini **/app**</span><span class="sxs-lookup"><span data-stu-id="f4eed-232">Change current directory to **/app**</span></span>
27. <span data-ttu-id="f4eed-233">Kopyalama **/app** aşamadaki dizin **yayımlama** geçerli dizinde</span><span class="sxs-lookup"><span data-stu-id="f4eed-233">Copy the **/app** directory from stage **publish** to the current directory</span></span>
28. <span data-ttu-id="f4eed-234">Kapsayıcı başlatıldığında çalıştırılacak komut tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="f4eed-234">Define the command to run when the container is started.</span></span>

<span data-ttu-id="f4eed-235">Artık hizmetine söz konusu olduğunda, yaklaşık 22 dakika veya daha fazla Linux kapsayıcıları tam çözümde oluşturulacak anlamına gelir, tüm işlem performansını artırmak için bazı iyileştirmeler inceleyelim.</span><span class="sxs-lookup"><span data-stu-id="f4eed-235">Now let's explore some optimizations to improve the whole process performance that, in the case of eShopOnContainers, means about 22 minutes or more to build the complete solution in Linux containers.</span></span>

<span data-ttu-id="f4eed-236">Oldukça basittir Docker'ın katmanı önbellek özelliğin avantajlarından yararlanmak: temel görüntü ve komutlar bazı önceden yürütülmüş aynı ise, bu yalnızca gerek kalmadan elde edilen katman süre vermeyip komutları yürütmek için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f4eed-236">You'll take advantage of Docker's layer cache feature, which is quite simple: if the base image and the commands are the same as some previously executed, it can just use the resulting layer without the need to execute the commands, thus saving some time.</span></span>

<span data-ttu-id="f4eed-237">Bunu odaklanalım **derleme** aşama, Satır 5-6 çoğunlukla aynı, ancak satırları 7-17 farklı tek her zaman yürütmek sahip oldukları için değiştirdiyseniz her hizmetinden hizmetine, ancak 7-16 dizesine satırlar için:</span><span class="sxs-lookup"><span data-stu-id="f4eed-237">So, let's focus on the **build** stage, lines 5-6 are mostly the same, but lines 7-17 are different for every service from eShopOnContainers, so they have to execute every single time, however if you changed lines 7-16 to:</span></span>

```
COPY . .
```

<span data-ttu-id="f4eed-238">Her hizmet için yalnızca aynı olacaktır sonra tüm çözüm kopyalanır ve daha büyük bir katman oluşturacak ancak:</span><span class="sxs-lookup"><span data-stu-id="f4eed-238">Then it would be just the same for every service, it would copy the whole solution and would create a larger layer but:</span></span>

1) <span data-ttu-id="f4eed-239">Kopyalama işlemine yalnızca ilk (ve bir dosya değiştirildiğinde yeniden oluştururken) yürütülmesi ve önbelleğe diğer tüm hizmetler için kullanacağınız ve</span><span class="sxs-lookup"><span data-stu-id="f4eed-239">The copy process would only be executed the first time (and when rebuilding if a file is changed) and would use the cache for all other services and</span></span>

2) <span data-ttu-id="f4eed-240">Bir ara aşamasında daha büyük resmi gerçekleşir olduğundan, son görüntü boyutunu etkilemez.</span><span class="sxs-lookup"><span data-stu-id="f4eed-240">Since the larger image occurs in an intermediate stage it, doesn't affect the final image size.</span></span>

<span data-ttu-id="f4eed-241">Sonraki önemli iyileştirme içerir `restore` hizmetine her bir hizmet için farklı olan komut satırında 17 yürütüldü.</span><span class="sxs-lookup"><span data-stu-id="f4eed-241">The next significant optimization involves the `restore` command executed in line 17, which is also different for every service of eShopOnContainers.</span></span> <span data-ttu-id="f4eed-242">Bu satırı yalnızca değiştirirseniz:</span><span class="sxs-lookup"><span data-stu-id="f4eed-242">If you change that line to just:</span></span>

```console
RUN dotnet restore
```

<span data-ttu-id="f4eed-243">Tüm çözüm için paketler geri yüklenebilir, ancak daha sonra tekrar bu yalnızca bir kez geçerli stratejisi ile 15 saatleri yerine bunu.</span><span class="sxs-lookup"><span data-stu-id="f4eed-243">It would restore the packages for the whole solution, but then again, it would do it just once, instead of the 15 times with the current strategy.</span></span>

<span data-ttu-id="f4eed-244">Ancak, `dotnet restore` tek proje veya çözüm dosyası klasöründe yoksa çalıştırmaları yalnızca, bu nedenle bunu elde etmenin biraz daha karmaşıktır ve çok fazla ayrıntılarına almadan bunu çözmenin bir yolu budur:</span><span class="sxs-lookup"><span data-stu-id="f4eed-244">However, `dotnet restore` only runs if there's a single project or solution file in the folder, so achieving this is a bit more complicated and the way to solve it, without getting into too many details, is this:</span></span>

1) <span data-ttu-id="f4eed-245">Aşağıdaki satırları ekleyin **.dockerignore**:</span><span class="sxs-lookup"><span data-stu-id="f4eed-245">Add the following lines to **.dockerignore**:</span></span>

   - <span data-ttu-id="f4eed-246">`*.sln`, ana klasörü ağacında, tüm çözüm dosyaları yoksaymak için</span><span class="sxs-lookup"><span data-stu-id="f4eed-246">`*.sln`, to ignore all solution files in the main folder tree</span></span>

   - <span data-ttu-id="f4eed-247">`!eShopOnContainers-ServicesAndWebApps.sln`, yalnızca bu çözüm dosyası eklenecek.</span><span class="sxs-lookup"><span data-stu-id="f4eed-247">`!eShopOnContainers-ServicesAndWebApps.sln`, to include only this solution file.</span></span>

2) <span data-ttu-id="f4eed-248">Dahil `/ignoreprojectextensions:.dcproj` bağımsız değişkeni `dotnet restore`, bu nedenle de docker-compose proje yok sayar ve yalnızca hizmetine ServicesAndWebApps çözüm için paketler geri yükler.</span><span class="sxs-lookup"><span data-stu-id="f4eed-248">Include the `/ignoreprojectextensions:.dcproj` argument to `dotnet restore`, so it also ignores the docker-compose project and only restores the packages for the eShopOnContainers-ServicesAndWebApps solution.</span></span>

<span data-ttu-id="f4eed-249">Son iyileştirme için yalnızca böyle satırı 20 gereksizdir, satır olarak 23 Ayrıca uygulama oluşturur ve orada gider başka bir zaman komutu, esas olarak, sağ 20 satırın sonunda sunulur; böylece.</span><span class="sxs-lookup"><span data-stu-id="f4eed-249">For the final optimization, it just happens that line 20 is redundant, as line 23 also builds the application and comes, in essence, right after line 20, so there goes another time-consuming command.</span></span>

<span data-ttu-id="f4eed-250">Sonuç dosyası ise:</span><span class="sxs-lookup"><span data-stu-id="f4eed-250">The resulting file is then:</span></span>

```Dockerfile
 1  FROM mcr.microsoft.com/dotnet/core/aspnet:2.2 AS base
 2  WORKDIR /app
 3  EXPOSE 80
 4
 5  FROM mcr.microsoft.com/dotnet/core/sdk:2.2 AS publish
 6  WORKDIR /src
 7  COPY . .
 8  RUN dotnet restore /ignoreprojectextensions:.dcproj
 9  WORKDIR /src/src/Services/Catalog/Catalog.API
10  RUN dotnet publish Catalog.API.csproj -c Release -0 /app
11
12  FROM base AS final
13  WORKDIR /app
14  COPY --from=publish /app
15  ENTRYPOINT ["dotnet", "Catalog.API.dll"]
```

### <a name="creating-your-base-image-from-scratch"></a><span data-ttu-id="f4eed-251">Temel görüntünüzü sıfırdan oluşturma</span><span class="sxs-lookup"><span data-stu-id="f4eed-251">Creating your base image from scratch</span></span>

<span data-ttu-id="f4eed-252">Kendi Docker temel görüntüsünde sıfırdan oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f4eed-252">You can create your own Docker base image from scratch.</span></span> <span data-ttu-id="f4eed-253">Bu senaryo için Docker ile başlayan bir kişinin önerilmez, ancak kendi temel görüntü belirli bitlerini ayarlamak istiyorsanız, bunu yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f4eed-253">This scenario is not recommended for someone who is starting with Docker, but if you want to set the specific bits of your own base image, you can do so.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="f4eed-254">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="f4eed-254">Additional resources</span></span>

- <span data-ttu-id="f4eed-255">**.NET Core görüntüleri çok yay**. \\</span><span class="sxs-lookup"><span data-stu-id="f4eed-255">**Multi-arch .NET Core images**.\\</span></span>
  [https://github.com/dotnet/announcements/issues/14](https://github.com/dotnet/announcements/issues/14)

- <span data-ttu-id="f4eed-256">**Temel görüntü oluşturma**.</span><span class="sxs-lookup"><span data-stu-id="f4eed-256">**Create a base image**.</span></span> <span data-ttu-id="f4eed-257">Resmi Docker belgelerine. \\</span><span class="sxs-lookup"><span data-stu-id="f4eed-257">Official Docker documentation.\\</span></span>
  [https://docs.docker.com/engine/userguide/eng-image/baseimages/](https://docs.docker.com/engine/userguide/eng-image/baseimages/)

![3 - dockerfile'ları tanımlanan görüntüleri oluşturma](./media/image7.png)

## <a name="step-3-create-your-custom-docker-images-and-embed-your-application-or-service-in-them"></a><span data-ttu-id="f4eed-259">Adım 3.</span><span class="sxs-lookup"><span data-stu-id="f4eed-259">Step 3.</span></span> <span data-ttu-id="f4eed-260">Özel Docker görüntülerinizi oluşturmak ve uygulamanızın veya hizmetinizin bunları ekleme</span><span class="sxs-lookup"><span data-stu-id="f4eed-260">Create your custom Docker images and embed your application or service in them</span></span>

<span data-ttu-id="f4eed-261">Uygulamanızdaki her hizmet için ilgili görüntü oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="f4eed-261">For each service in your application, you need to create a related image.</span></span> <span data-ttu-id="f4eed-262">Uygulamanızı bir tek bir hizmeti veya web uygulaması oluşur, tek bir görüntü yeterlidir.</span><span class="sxs-lookup"><span data-stu-id="f4eed-262">If your application is made up of a single service or web application, you just need a single image.</span></span>

<span data-ttu-id="f4eed-263">Docker görüntülerini otomatik olarak sizin için Visual Studio'da oluşturulan unutmayın.</span><span class="sxs-lookup"><span data-stu-id="f4eed-263">Note that the Docker images are built automatically for you in Visual Studio.</span></span> <span data-ttu-id="f4eed-264">Aşağıdaki adımlar yalnızca Düzenleyici/CLI iş akışı için gereken ve altında olabilecekler açıklık için açıklanmıştır.</span><span class="sxs-lookup"><span data-stu-id="f4eed-264">The following steps are only needed for the editor/CLI workflow and explained for clarity about what happens underneath.</span></span>

<span data-ttu-id="f4eed-265">Geliştirme ve yerel olarak bir tamamlanmış itinceye kadar test için bir geliştirici olarak, ihtiyaç duyduğunuz, özelliği veya kaynak denetim sisteminize (örneğin GitHub) değiştirin.</span><span class="sxs-lookup"><span data-stu-id="f4eed-265">You, as a developer, need to develop and test locally until you push a completed feature or change to your source control system (for example, to GitHub).</span></span> <span data-ttu-id="f4eed-266">Bu, Docker görüntüleri oluşturun ve kapsayıcıları yerel Docker konağı için (Windows veya Linux VM) dağıtın ve çalıştırın, test ve yerel kapsayıcıların karşı hata ayıklama gerektiği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="f4eed-266">This means that you need to create the Docker images and deploy containers to a local Docker host (Windows or Linux VM) and run, test, and debug against those local containers.</span></span>

<span data-ttu-id="f4eed-267">Özel bir görüntü yerel ortamınızda Docker CLI ve Dockerfile'ı kullanarak oluşturmak için docker oluşturma komutu, Şekil 5-5'olduğu gibi kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f4eed-267">To create a custom image in your local environment by using Docker CLI and your Dockerfile, you can use the docker build command, as in Figure 5-5.</span></span>

![Bir Docker görüntüsü oluşturmak için ilerleme durumu ekranı](./media/image8.png)

<span data-ttu-id="f4eed-269">**Şekil 5-5**.</span><span class="sxs-lookup"><span data-stu-id="f4eed-269">**Figure 5-5**.</span></span> <span data-ttu-id="f4eed-270">Özel bir Docker görüntüsü oluşturma</span><span class="sxs-lookup"><span data-stu-id="f4eed-270">Creating a custom Docker image</span></span>

<span data-ttu-id="f4eed-271">İsteğe bağlı olarak, docker derleme proje klasöründen doğrudan çalıştırmak yerine, önce gerekli .NET kitaplıkları ve ikili dosyaları ile dağıtılabilir bir klasör çalıştırarak oluşturabileceğiniz `dotnet publish`ve ardından `docker build` komutu.</span><span class="sxs-lookup"><span data-stu-id="f4eed-271">Optionally, instead of directly running docker build from the project folder, you can first generate a deployable folder with the required .NET libraries and binaries by running `dotnet publish`, and then use the `docker build` command.</span></span>

<span data-ttu-id="f4eed-272">Bu ada sahip bir Docker görüntüsü oluşturacak `cesardl/netcore-webapi-microservice-docker:first`.</span><span class="sxs-lookup"><span data-stu-id="f4eed-272">This will create a Docker image with the name `cesardl/netcore-webapi-microservice-docker:first`.</span></span> <span data-ttu-id="f4eed-273">Bu durumda: öncelikle, belirli bir sürümü temsil eden bir etiketi olan.</span><span class="sxs-lookup"><span data-stu-id="f4eed-273">In this case, :first is a tag representing a specific version.</span></span> <span data-ttu-id="f4eed-274">Oluşturulmuş Docker uygulamanız için oluşturmak için gereken her özel bir görüntü için bu adımı yineleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f4eed-274">You can repeat this step for each custom image you need to create for your composed Docker application.</span></span>

<span data-ttu-id="f4eed-275">Bir uygulama birden çok kapsayıcılardan yapılan ne zaman (diğer bir deyişle, çok kapsayıcılı bir uygulama olduğu), ayrıca `docker-compose up --build` ilgili docker-compose.yml dosyaları kullanıma sunulan meta verileri kullanarak tek bir komutla ilgili tüm görüntüleri oluşturmak için komutu .</span><span class="sxs-lookup"><span data-stu-id="f4eed-275">When an application is made of multiple containers (that is, it is a multi-container application), you can also use the `docker-compose up --build` command to build all the related images with a single command by using the metadata exposed in the related docker-compose.yml files.</span></span>

<span data-ttu-id="f4eed-276">Var olan görüntülerden yerel deponuzda docker'ı kullanarak görüntü komutu, Şekil 5-6'da gösterildiği gibi bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f4eed-276">You can find the existing images in your local repository by using the docker images command, as shown in Figure 5-6.</span></span>

![Ekran görünümünü görüntü komutu docker görüntüleri listeleme](./media/image9.png)

<span data-ttu-id="f4eed-278">**Şekil 5-6.**</span><span class="sxs-lookup"><span data-stu-id="f4eed-278">**Figure 5-6.**</span></span> <span data-ttu-id="f4eed-279">Docker görüntüleri komutunu kullanarak var olan görüntüleri görüntüleme</span><span class="sxs-lookup"><span data-stu-id="f4eed-279">Viewing existing images using the docker images command</span></span>

### <a name="creating-docker-images-with-visual-studio"></a><span data-ttu-id="f4eed-280">Visual Studio ile Docker görüntüleri oluşturma</span><span class="sxs-lookup"><span data-stu-id="f4eed-280">Creating Docker images with Visual Studio</span></span>

<span data-ttu-id="f4eed-281">Docker desteği bir proje oluşturmak için Visual Studio kullandığınızda, bir görüntü açıkça oluşturmayın.</span><span class="sxs-lookup"><span data-stu-id="f4eed-281">When you use Visual Studio to create a project with Docker support, you don't explicitly create an image.</span></span> <span data-ttu-id="f4eed-282">Bastığınızda bunun yerine, görüntünün sizin için oluşturulan **F5** (veya **Ctrl-F5**) dockerized uygulamaya veya hizmete çalıştırılacak.</span><span class="sxs-lookup"><span data-stu-id="f4eed-282">Instead, the image is created for you when you press **F5** (or **Ctrl-F5**) to run the dockerized application or service.</span></span> <span data-ttu-id="f4eed-283">Bu adım Visual Studio'da otomatik olarak yapılır ve durum göremezsiniz ancak neler olduğunu bilmeniz önemlidir üzerinde underneath.</span><span class="sxs-lookup"><span data-stu-id="f4eed-283">This step is automatic in Visual Studio and you won't see it happen, but it's important that you know what's going on underneath.</span></span>

![4 - (docker-compose.yml dosyası oluşturma hizmetleri isteğe bağlı)](./media/image10.png)

## <a name="step-4-define-your-services-in-docker-composeyml-when-building-a-multi-container-docker-application"></a><span data-ttu-id="f4eed-285">4. adımı.</span><span class="sxs-lookup"><span data-stu-id="f4eed-285">Step 4.</span></span> <span data-ttu-id="f4eed-286">Çok kapsayıcılı Docker uygulaması oluştururken, docker-compose.yml hizmetlerinizi tanımlayın</span><span class="sxs-lookup"><span data-stu-id="f4eed-286">Define your services in docker-compose.yml when building a multi-container Docker application</span></span>

<span data-ttu-id="f4eed-287">[Docker-compose.yml](https://docs.docker.com/compose/compose-file/) dosya dağıtım komutları ile oluşturulmuş bir uygulama olarak dağıtılması için ilgili bir hizmetler kümesi tanımlamanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="f4eed-287">The [docker-compose.yml](https://docs.docker.com/compose/compose-file/) file lets you define a set of related services to be deployed as a composed application with deployment commands.</span></span> <span data-ttu-id="f4eed-288">Ayrıca, çalışma zamanı yapılandırma ve bağımlılık ilişkilerinin yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="f4eed-288">It also configures its dependency relations and run-time configuration.</span></span>

<span data-ttu-id="f4eed-289">Docker-compose.yml dosyası kullanmak için aşağıdaki örnekte benzer içeriğe sahip ana dosyasında veya kök Çözüm klasörü'ı oluşturmanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="f4eed-289">To use a docker-compose.yml file, you need to create the file in your main or root solution folder, with content similar to that in the following example:</span></span>

```yml
version: '3.4'

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
      - ConnectionString=Server=sql.data;Port=1433;Database=CatalogDB;…
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

<span data-ttu-id="f4eed-290">Bu docker-compose.yml dosyası basit ve birleştirilmiş bir sürümüdür.</span><span class="sxs-lookup"><span data-stu-id="f4eed-290">This docker-compose.yml file is a simplified and merged version.</span></span> <span data-ttu-id="f4eed-291">Bu, her kapsayıcı (adı gibi özel görüntü), her zaman gerekli olan ve bağlantı dizesi gibi dağıtım ortamı bağımlı olabileceği yapılandırma bilgileri için statik yapılandırma verilerini içerir.</span><span class="sxs-lookup"><span data-stu-id="f4eed-291">It contains static configuration data for each container (like the name of the custom image), which is always required, and configuration information that might depend on the deployment environment, like the connection string.</span></span> <span data-ttu-id="f4eed-292">Sonraki bölümlerde nasıl docker-compose.yml bölme için birden çok yapılandırma docker compose dosyaları ve geçersiz kılma değerleri (hata ayıklama veya sürüm) ortamını ve yürütme türüne bağlı olarak öğreneceksiniz.</span><span class="sxs-lookup"><span data-stu-id="f4eed-292">In later sections, you will learn how to split the docker-compose.yml configuration into multiple docker-compose files and override values depending on the environment and execution type (debug or release).</span></span>

<span data-ttu-id="f4eed-293">Docker-compose.yml dosyası örneği dört hizmet tanımlar: `webmvc` hizmeti (web uygulaması), iki mikro hizmetler (`ordering.api` ve `basket.api`) ve bir veri kaynağı kapsayıcı `sql.data`olarak çalışan Linux SQL Server göre bir kapsayıcı.</span><span class="sxs-lookup"><span data-stu-id="f4eed-293">The docker-compose.yml file example defines four services: the `webmvc` service (a web application), two microservices (`ordering.api` and `basket.api`), and one data source container, `sql.data`, based on SQL Server for Linux running as a container.</span></span> <span data-ttu-id="f4eed-294">Her biri için gerekli bir Docker görüntüsü, bu nedenle, her hizmetin bir kapsayıcı olarak dağıtılır.</span><span class="sxs-lookup"><span data-stu-id="f4eed-294">Each service will be deployed as a container, so a Docker image is required for each.</span></span>

<span data-ttu-id="f4eed-295">Docker-compose.yml dosyası, yalnızca kapsayıcıların ne kullanılır, ancak ayrı ayrı yapılandırmaya belirtir.</span><span class="sxs-lookup"><span data-stu-id="f4eed-295">The docker-compose.yml file specifies not only what containers are being used, but how they are individually configured.</span></span> <span data-ttu-id="f4eed-296">Örneğin, `webmvc` kapsayıcısı tanımında .yml dosyası:</span><span class="sxs-lookup"><span data-stu-id="f4eed-296">For instance, the `webmvc` container definition in the .yml file:</span></span>

- <span data-ttu-id="f4eed-297">Önceden oluşturulmuş kullanan `eshop/web:latest` görüntü.</span><span class="sxs-lookup"><span data-stu-id="f4eed-297">Uses a pre-built `eshop/web:latest` image.</span></span> <span data-ttu-id="f4eed-298">Ancak, aynı zamanda bir parçası olarak oluşturulacak görüntünün yapılandırabilirsiniz docker-compose temelli bir derleme üzerinde yürütme ek bir yapılandırma: docker-compose dosyasındaki bölümü.</span><span class="sxs-lookup"><span data-stu-id="f4eed-298">However, you could also configure the image to be built as part of the docker-compose execution with an additional configuration based on a build: section in the docker-compose file.</span></span>

- <span data-ttu-id="f4eed-299">İki ortam değişkenlerini (katalog URL'si ve OrderingUrl) başlatır.</span><span class="sxs-lookup"><span data-stu-id="f4eed-299">Initializes two environment variables (CatalogUrl and OrderingUrl).</span></span>

- <span data-ttu-id="f4eed-300">Konak makinedeki dış bağlantı noktası 80 kapsayıcı üzerindeki 80 kullanıma sunulan bağlantı noktası iletir.</span><span class="sxs-lookup"><span data-stu-id="f4eed-300">Forwards the exposed port 80 on the container to the external port 80 on the host machine.</span></span>

- <span data-ttu-id="f4eed-301">Web uygulama kataloğu ve hizmet depends_on ayarıyla sıralama bağlantılarını içerir.</span><span class="sxs-lookup"><span data-stu-id="f4eed-301">Links the web app to the catalog and ordering service with the depends_on setting.</span></span> <span data-ttu-id="f4eed-302">Bu hizmet, bu hizmetleri yeniden başlatılana kadar beklenecek neden olur.</span><span class="sxs-lookup"><span data-stu-id="f4eed-302">This causes the service to wait until those services are started.</span></span>

<span data-ttu-id="f4eed-303">Mikro hizmetler ve çok kapsayıcılı uygulamalar uygulamak nasıl ele, biz bir sonraki bölümde docker-compose.yml dosyası yeniden ziyaret.</span><span class="sxs-lookup"><span data-stu-id="f4eed-303">We will revisit the docker-compose.yml file in a later section when we cover how to implement microservices and multi-container apps.</span></span>

### <a name="working-with-docker-composeyml-in-visual-studio-2017"></a><span data-ttu-id="f4eed-304">Visual Studio 2017'de docker-compose.yml ile çalışma</span><span class="sxs-lookup"><span data-stu-id="f4eed-304">Working with docker-compose.yml in Visual Studio 2017</span></span>

<span data-ttu-id="f4eed-305">Biz daha önce bahsedildiği gibi bir proje için bir Dockerfile eklemenin yanı sıra, Visual Studio 2017 (15,8 üzerinde) Docker Compose için orchestrator desteği bir çözüme ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f4eed-305">Besides adding a Dockerfile to a project, as we mentioned before, Visual Studio 2017 (from 15.8 on) can add orchestrator support for Docker Compose to a solution.</span></span>

<span data-ttu-id="f4eed-306">Kapsayıcı Düzenleyicisi desteği, ilk kez, Şekil 5-7'de gösterildiği gibi eklediğinizde Visual Studio projesi için bir Dockerfile ve yeni bir (hizmet bölümü) projesi çözümünüzdeki birkaç ile genel oluşturur `docker-compose*.yml` dosyaları ve ekler Bu dosyalar için proje.</span><span class="sxs-lookup"><span data-stu-id="f4eed-306">When you add container orchestrator support, as shown in Figure 5-7, for the first time, Visual Studio creates the Dockerfile for the project and creates a new (service section) project in your solution with several global `docker-compose*.yml` files, and then adds the project to those files.</span></span> <span data-ttu-id="f4eed-307">Docker-compose.yml dosyaları açmak ve bunları ek özellikler ile güncelleştirin.</span><span class="sxs-lookup"><span data-stu-id="f4eed-307">You can then open the docker-compose.yml files and update them with additional features.</span></span>

<span data-ttu-id="f4eed-308">Bu işlem formu docker-compose.yml dosyasında dahil etmek istediğiniz her proje yinelemek zorunda.</span><span class="sxs-lookup"><span data-stu-id="f4eed-308">You have to repeat this operation form every project you want to include in the docker-compose.yml file.</span></span>

<span data-ttu-id="f4eed-309">Bu makalenin yazıldığı sırada, Visual Studio, Docker Compose ve Service Fabric düzenleyicileri destekler.</span><span class="sxs-lookup"><span data-stu-id="f4eed-309">At the time of this writing, Visual Studio supports Docker Compose and Service Fabric orchestrators.</span></span>

![Bir ASP.NET Core projesi için orchestrator desteği eklemek için bağlam menüsü seçeneği](./media/image21.png)

<span data-ttu-id="f4eed-311">**Şekil 5-7**.</span><span class="sxs-lookup"><span data-stu-id="f4eed-311">**Figure 5-7**.</span></span> <span data-ttu-id="f4eed-312">Bir ASP.NET Core projesi sağ tıklayarak Visual Studio 2017'de Docker desteği ekleme</span><span class="sxs-lookup"><span data-stu-id="f4eed-312">Adding Docker support in Visual Studio 2017 by right-clicking an ASP.NET Core project</span></span>

<span data-ttu-id="f4eed-313">Visual Studio çözümünüzde Düzenleyicisi desteği ekledikten sonra yeni bir düğüm ayrıca görürsünüz (içinde `docker-compose.dcproj` proje dosyası) Çözüm Gezgini'nde, Şekil 5-8'de gösterildiği gibi eklenen docker-compose.yml dosyaları içerir.</span><span class="sxs-lookup"><span data-stu-id="f4eed-313">After you add orchestrator support to your solution in Visual Studio, you will also see a new node (in the `docker-compose.dcproj` project file) in Solution Explorer that contains the added docker-compose.yml files, as shown in Figure 5-8.</span></span>

![Çözüm Gezgininde docker-compose](./media/image11.png)

<span data-ttu-id="f4eed-315">**Şekil 5-8**.</span><span class="sxs-lookup"><span data-stu-id="f4eed-315">**Figure 5-8**.</span></span> <span data-ttu-id="f4eed-316">**Docker-compose** Visual Studio 2017 Çözüm Gezgini'nde eklenen ağaç düğümü</span><span class="sxs-lookup"><span data-stu-id="f4eed-316">The **docker-compose** tree node added in Visual Studio 2017 Solution Explorer</span></span>

<span data-ttu-id="f4eed-317">Kullanarak bir docker-compose.yml dosyası ile çok kapsayıcılı bir uygulama dağıtabilirsiniz `docker-compose up` komutu.</span><span class="sxs-lookup"><span data-stu-id="f4eed-317">You could deploy a multi-container application with a single docker-compose.yml file by using the `docker-compose up` command.</span></span> <span data-ttu-id="f4eed-318">Ancak, ortam (geliştirme veya üretim) ve yürütme türü (yayınlama veya hata ayıklama) bağlı olarak değerleri geçersiz kılmak için Visual Studio bunları grubu ekler.</span><span class="sxs-lookup"><span data-stu-id="f4eed-318">However, Visual Studio adds a group of them so you can override values depending on the environment (development or production) and execution type (release or debug).</span></span> <span data-ttu-id="f4eed-319">Bu özellik, sonraki bölümlerde açıklanacaktır.</span><span class="sxs-lookup"><span data-stu-id="f4eed-319">This capability will be explained in later sections.</span></span>

![5 - kapsayıcıları çalıştırmak veya uygulama oluşur](./media/image12.png)

## <a name="step-5-build-and-run-your-docker-application"></a><span data-ttu-id="f4eed-321">5. adımı.</span><span class="sxs-lookup"><span data-stu-id="f4eed-321">Step 5.</span></span> <span data-ttu-id="f4eed-322">Kendi Docker uygulaması derleme ve çalıştırma</span><span class="sxs-lookup"><span data-stu-id="f4eed-322">Build and run your Docker application</span></span>

<span data-ttu-id="f4eed-323">Uygulamanız yalnızca tek bir kapsayıcıya sahip değilse, Docker Konağı (VM veya fiziksel sunucu) dağıtarak çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f4eed-323">If your application only has a single container, you can run it by deploying it to your Docker host (VM or physical server).</span></span> <span data-ttu-id="f4eed-324">Uygulamanız birden fazla hizmet içeriyor, ancak bunu oluşan bir uygulama olarak ya da tek bir CLI komutu kullanarak dağıtabilirsiniz (docker-compose ayarlama), veya Visual Studio ile bu komut aslında altında kullanacak.</span><span class="sxs-lookup"><span data-stu-id="f4eed-324">However, if your application contains multiple services, you can deploy it as a composed application, either using a single CLI command (docker-compose up), or with Visual Studio, which will use that command under the covers.</span></span> <span data-ttu-id="f4eed-325">Farklı seçenekleri göz atalım.</span><span class="sxs-lookup"><span data-stu-id="f4eed-325">Let's look at the different options.</span></span>

### <a name="option-a-running-a-single-container-application"></a><span data-ttu-id="f4eed-326">Seçenek A: Tek kapsayıcı uygulaması çalıştırma</span><span class="sxs-lookup"><span data-stu-id="f4eed-326">Option A: Running a single-container application</span></span>

#### <a name="using-docker-cli"></a><span data-ttu-id="f4eed-327">Docker CLI kullanma</span><span class="sxs-lookup"><span data-stu-id="f4eed-327">Using Docker CLI</span></span>

<span data-ttu-id="f4eed-328">Kullanarak bir Docker kapsayıcısı çalıştırabilirsiniz `docker run` Şekil 5-9'da gösterildiği gibi komut:</span><span class="sxs-lookup"><span data-stu-id="f4eed-328">You can run a Docker container using the `docker run` command, as shown in Figure 5-9:</span></span>

```console
  docker run -t -d -p 80:5000 cesardl/netcore-webapi-microservice-docker:first
```

<span data-ttu-id="f4eed-329">Yukarıdaki komutu her çalıştırıldığında yeni bir kapsayıcı örneği belirtilen görüntüden oluşturacaksınız.</span><span class="sxs-lookup"><span data-stu-id="f4eed-329">The above command will create a new container instance from the specified image, every time it's run.</span></span> <span data-ttu-id="f4eed-330">Kullanabileceğiniz `--name` kapsayıcıya bir ad verin ve ardından parametre `docker start {name}` (veya kapsayıcı kimliği veya otomatik adı kullanın) var olan bir kapsayıcı örneği çalıştırmak için.</span><span class="sxs-lookup"><span data-stu-id="f4eed-330">You can use the `--name` parameter to give a name to the container and then use `docker start {name}` (or use the container id or automatic name) to run an existing container instance.</span></span>

![Docker kullanarak Docker kapsayıcı çalışırken ekran görünümünü komutunu çalıştırın](./media/image13.png)

<span data-ttu-id="f4eed-332">**Şekil 5-9**.</span><span class="sxs-lookup"><span data-stu-id="f4eed-332">**Figure 5-9**.</span></span> <span data-ttu-id="f4eed-333">Komutu çalıştırarak docker kullanarak Docker kapsayıcı çalıştırma</span><span class="sxs-lookup"><span data-stu-id="f4eed-333">Running a Docker container using the docker run command</span></span>

<span data-ttu-id="f4eed-334">Bu durumda, komut kapsayıcının iç bağlantı noktası 5000 ana makinenin 80 numaralı bağlantı noktasına bağlar.</span><span class="sxs-lookup"><span data-stu-id="f4eed-334">In this case, the command binds the internal port 5000 of the container to port 80 of the host machine.</span></span> <span data-ttu-id="f4eed-335">Bu konak 80 numaralı bağlantı noktasında dinleme ve kapsayıcıda genericread 5000 numaralı bağlantı noktasına ileten anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="f4eed-335">This means that the host is listening on port 80 and forwarding to port 5000 on the container.</span></span>

<span data-ttu-id="f4eed-336">Gösterilen karma kapsayıcı kimliği olduğunu ve bunu ayrıca bir rastgele okunabilir ad varsa atadığı `--name` seçeneği kullanılamıyor.</span><span class="sxs-lookup"><span data-stu-id="f4eed-336">The hash shown is the container id and it’s also assigned a random readable name if the `--name` option is not used.</span></span>

#### <a name="using-visual-studio"></a><span data-ttu-id="f4eed-337">Visual Studio kullanarak</span><span class="sxs-lookup"><span data-stu-id="f4eed-337">Using Visual Studio</span></span>

<span data-ttu-id="f4eed-338">Kapsayıcı Düzenleyicisi desteği eklemediyseniz, ayrıca bir çoklu kapsayıcı uygulaması Visual Studio'da tuşlarına basarak çalıştırabileceğiniz **Ctrl-F5** ve ayrıca **F5** uygulama kapsayıcı içinde hata ayıklamak için.</span><span class="sxs-lookup"><span data-stu-id="f4eed-338">If you haven't added container orchestrator support, you can also run a single container app in Visual Studio by pressing **Ctrl-F5** and you can also use **F5** to debug the application within the container.</span></span> <span data-ttu-id="f4eed-339">Kapsayıcı, docker run kullanarak yerel olarak çalışır.</span><span class="sxs-lookup"><span data-stu-id="f4eed-339">The container runs locally using docker run.</span></span>

### <a name="option-b-running-a-multi-container-application"></a><span data-ttu-id="f4eed-340">Seçenek B: Çok kapsayıcılı bir uygulama çalıştırma</span><span class="sxs-lookup"><span data-stu-id="f4eed-340">Option B: Running a multi-container application</span></span>

<span data-ttu-id="f4eed-341">Çoğu Kurumsal senaryolarda, Docker uygulaması birden çok Hizmetleri, Şekil 5-10'da gösterildiği gibi çok kapsayıcılı bir uygulama çalıştırmak gereken yani oluşacaktır.</span><span class="sxs-lookup"><span data-stu-id="f4eed-341">In most enterprise scenarios, a Docker application will be composed of multiple services, which means you need to run a multi-container application, as shown in Figure 5-10.</span></span>

![VM birkaç Docker kapsayıcıları ile](./media/image14.png)

<span data-ttu-id="f4eed-343">**Şekil 5-10**.</span><span class="sxs-lookup"><span data-stu-id="f4eed-343">**Figure 5-10**.</span></span> <span data-ttu-id="f4eed-344">Dağıtılmış Docker kapsayıcıları ile VM</span><span class="sxs-lookup"><span data-stu-id="f4eed-344">VM with Docker containers deployed</span></span>

#### <a name="using-docker-cli"></a><span data-ttu-id="f4eed-345">Docker CLI kullanma</span><span class="sxs-lookup"><span data-stu-id="f4eed-345">Using Docker CLI</span></span>

<span data-ttu-id="f4eed-346">Docker CLI ile çok kapsayıcılı bir uygulama çalıştırmak için kullandığınız `docker-compose up` komutu.</span><span class="sxs-lookup"><span data-stu-id="f4eed-346">To run a multi-container application with the Docker CLI, you use the `docker-compose up` command.</span></span> <span data-ttu-id="f4eed-347">Bu komut **docker-compose.yml** çok kapsayıcılı bir uygulama dağıtmak için çözüm düzeyinde sahip dosya.</span><span class="sxs-lookup"><span data-stu-id="f4eed-347">This command uses the **docker-compose.yml** file that you have at the solution level to deploy a multi-container application.</span></span> <span data-ttu-id="f4eed-348">Şekil 5-11 komut docker-compose.yml dosyasını içeren ana çözüm dizinden çalıştırılırken sonuçları gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="f4eed-348">Figure 5-11 shows the results when running the command from your main solution directory, which contains the docker-compose.yml file.</span></span>

![Ekran görünümünü çalıştırırken docker-compose komutu](./media/image15.png)

<span data-ttu-id="f4eed-350">**Şekil 5-11**.</span><span class="sxs-lookup"><span data-stu-id="f4eed-350">**Figure 5-11**.</span></span> <span data-ttu-id="f4eed-351">Örnek sonuçları çalıştırırken docker-compose komutu</span><span class="sxs-lookup"><span data-stu-id="f4eed-351">Example results when running the docker-compose up command</span></span>

<span data-ttu-id="f4eed-352">Sonra docker-compose komutu çalıştırmaları, uygulama ve onun ilişkili kapsayıcılar, Docker konağı Şekil 5-10'da görüldüğü gibi dağıtılır.</span><span class="sxs-lookup"><span data-stu-id="f4eed-352">After the docker-compose up command runs, the application and its related containers are deployed into your Docker host, as depicted in Figure 5-10.</span></span>

#### <a name="using-visual-studio"></a><span data-ttu-id="f4eed-353">Visual Studio kullanarak</span><span class="sxs-lookup"><span data-stu-id="f4eed-353">Using Visual Studio</span></span>

<span data-ttu-id="f4eed-354">Visual Studio 2017'yi kullanarak çok kapsayıcılı bir uygulama çalıştıran any daha basit alınamıyor.</span><span class="sxs-lookup"><span data-stu-id="f4eed-354">Running a multi-container application using Visual Studio 2017 can't get any simpler.</span></span> <span data-ttu-id="f4eed-355">Yalnızca tuşuna **Ctrl-F5** çalıştırmak için veya **F5** hata ayıklama, ayarlama gibi normal **docker-compose** projeyi başlangıç projesi olarak.</span><span class="sxs-lookup"><span data-stu-id="f4eed-355">You just press **Ctrl-F5** to run or **F5** to debug, as usual, setting up the **docker-compose** project as the startup project.</span></span>  <span data-ttu-id="f4eed-356">Visual Studio, kesme noktaları zamanki gibi oluşturabilir ve ne gibi "uzak sunucular", yalnızca çalışan bağımsız işlemler son haline hata ayıklama için tüm gerekli Kurulum işler.</span><span class="sxs-lookup"><span data-stu-id="f4eed-356">Visual Studio handles all needed setup, so you can create breakpoints as usual and debug what finally become independent processes running in "remote servers", just like that.</span></span>

<span data-ttu-id="f4eed-357">Her bir çözüm içinde bir proje için Docker çözüm desteğini eklemeden önce belirtildiği gibi proje çalıştırın veya çözümün tamamının aynı anda hata ayıklama olanak sağlayan genel (Çözüm düzeyinde) docker-compose.yml dosyasında yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="f4eed-357">As mentioned before, each time you add Docker solution support to a project within a solution, that project is configured in the global (solution-level) docker-compose.yml file, which lets you run or debug the whole solution at once.</span></span> <span data-ttu-id="f4eed-358">Visual Studio Docker çözümü desteği etkin olan her proje için bir kapsayıcı başlatın ve iç tüm adımları gerçekleştirdiğiniz (dotnet yayımlama, docker derleme, vs.).</span><span class="sxs-lookup"><span data-stu-id="f4eed-358">Visual Studio will start one container for each project that has Docker solution support enabled, and perform all the internal steps for you (dotnet publish, docker build, etc.).</span></span>

<span data-ttu-id="f4eed-359">Bir Özet drudgery hiç katılmak istiyorsanız, dosyaya göz atın:</span><span class="sxs-lookup"><span data-stu-id="f4eed-359">If you want to take a peek at all the drudgery, take a look at the file:</span></span>

`{root solution folder}\obj\Docker\docker-compose.vs.debug.g.yml`

<span data-ttu-id="f4eed-360">Burada önemli olan nokta Şekil 5-12'de gösterildiği gibi Visual Studio 2017'de, ek bir yoktur **Docker** F5 anahtar eylemi için komutu.</span><span class="sxs-lookup"><span data-stu-id="f4eed-360">The important point here is that, as shown in Figure 5-12, in Visual Studio 2017 there is an additional **Docker** command for the F5 key action.</span></span> <span data-ttu-id="f4eed-361">Bu seçenek çalıştırın ya da docker-compose.yml dosyaları çözüm düzeyinde tanımlanan tüm kapsayıcıları çalıştırarak çok kapsayıcılı bir uygulama hata ayıklama sağlar.</span><span class="sxs-lookup"><span data-stu-id="f4eed-361">This option lets you run or debug a multi-container application by running all the containers that are defined in the docker-compose.yml files at the solution level.</span></span> <span data-ttu-id="f4eed-362">Birden çok kapsayıcı çözümleri hata ayıklama özelliği (kapsayıcı) farklı bir projede birkaç kesme noktaları, her bir kesme noktası ayarlayın ve Visual Studio'dan hata ayıklama sırasında farklı projelerde tanımlanan ve çalıştırılan kesme noktalarında durdurur anlamına gelir. farklı kapsayıcılar.</span><span class="sxs-lookup"><span data-stu-id="f4eed-362">The ability to debug multiple-container solutions means that you can set several breakpoints, each breakpoint in a different project (container), and while debugging from Visual Studio you will stop at breakpoints defined in different projects and running on different containers.</span></span>

![Proje visual Studio hata ayıklama araç çalışan docker-compose](./media/image16.png)

<span data-ttu-id="f4eed-364">**Şekil 5-12**.</span><span class="sxs-lookup"><span data-stu-id="f4eed-364">**Figure 5-12**.</span></span> <span data-ttu-id="f4eed-365">Visual Studio 2017'de çalışan çok kapsayıcılı uygulamalar</span><span class="sxs-lookup"><span data-stu-id="f4eed-365">Running multi-container apps in Visual Studio 2017</span></span>

### <a name="additional-resources"></a><span data-ttu-id="f4eed-366">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="f4eed-366">Additional resources</span></span>

- <span data-ttu-id="f4eed-367">**ASP.NET kapsayıcısını uzak Docker konağı için dağıtma** \\</span><span class="sxs-lookup"><span data-stu-id="f4eed-367">**Deploy an ASP.NET container to a remote Docker host** \\</span></span>
  [https://docs.microsoft.com/azure/vs-azure-tools-docker-hosting-web-apps-in-docker](https://docs.microsoft.com/azure/vs-azure-tools-docker-hosting-web-apps-in-docker)

### <a name="a-note-about-testing-and-deploying-with-orchestrators"></a><span data-ttu-id="f4eed-368">Test etme ve dağıtma düzenleyicilerle hakkında bir Not</span><span class="sxs-lookup"><span data-stu-id="f4eed-368">A note about testing and deploying with orchestrators</span></span>

<span data-ttu-id="f4eed-369">Docker compose up ve docker run komutları (veya çalışan ve kapsayıcıları Visual Studio'da hata ayıklama) kapsayıcıları geliştirme ortamınızda test etmek için yeterli.</span><span class="sxs-lookup"><span data-stu-id="f4eed-369">The docker-compose up and docker run commands (or running and debugging the containers in Visual Studio) are adequate for testing containers in your development environment.</span></span> <span data-ttu-id="f4eed-370">Ancak burada hedef gibi düzenleyicileri, üretim dağıtımları için bu yaklaşım kullanmamalısınız [Kubernetes](https://kubernetes.io/) veya [Service Fabric](https://azure.microsoft.com/services/service-fabric/).</span><span class="sxs-lookup"><span data-stu-id="f4eed-370">But you should not use this approach for production deployments, where you should target orchestrators like [Kubernetes](https://kubernetes.io/) or [Service Fabric](https://azure.microsoft.com/services/service-fabric/).</span></span> <span data-ttu-id="f4eed-371">Kubernetes kullanıyorsanız kullanmak zorunda [pod'ların](https://kubernetes.io/docs/concepts/workloads/pods/pod/) kapsayıcıları düzenlemek için ve [Hizmetleri](https://kubernetes.io/docs/concepts/services-networking/service/) bunları ağ.</span><span class="sxs-lookup"><span data-stu-id="f4eed-371">If you're using Kubernetes you have to use [pods](https://kubernetes.io/docs/concepts/workloads/pods/pod/) to organize containers and [services](https://kubernetes.io/docs/concepts/services-networking/service/) to network them.</span></span> <span data-ttu-id="f4eed-372">Ayrıca [dağıtımları](https://kubernetes.io/docs/concepts/workloads/controllers/deployment/) pod oluşturulmasını ve değiştirilmesini düzenlemek için.</span><span class="sxs-lookup"><span data-stu-id="f4eed-372">You also use [deployments](https://kubernetes.io/docs/concepts/workloads/controllers/deployment/) to organize pod creation and modification.</span></span>

![6 - uygulamanızı veya mikro Hizmetleri test etme](./media/image17.png)

## <a name="step-6-test-your-docker-application-using-your-local-docker-host"></a><span data-ttu-id="f4eed-374">6. adım.</span><span class="sxs-lookup"><span data-stu-id="f4eed-374">Step 6.</span></span> <span data-ttu-id="f4eed-375">Kullanarak yerel bir Docker ana bilgisayarınızda Docker uygulamanızı test edin</span><span class="sxs-lookup"><span data-stu-id="f4eed-375">Test your Docker application using your local Docker host</span></span>

<span data-ttu-id="f4eed-376">Bu adım, uygulamanızın yapılması bağlı olarak değişir.</span><span class="sxs-lookup"><span data-stu-id="f4eed-376">This step will vary depending on what your application is doing.</span></span> <span data-ttu-id="f4eed-377">Tek kapsayıcı veya hizmet olarak dağıtılan bir basit .NET Core Web uygulamasında, Docker konağı üzerinde bir tarayıcı açıp bu siteye gezinme, Şekil 5-13'te gösterildiği gibi hizmete erişebilir.</span><span class="sxs-lookup"><span data-stu-id="f4eed-377">In a simple .NET Core Web application that is deployed as a single container or service, you can access the service by opening a browser on the Docker host and navigating to that site, as shown in Figure 5-13.</span></span> <span data-ttu-id="f4eed-378">(Dockerfile içinde yapılandırma kapsayıcı 80 dışında her şey, konağa bağlantı noktasına eşler. ana bilgisayar bağlantı noktası URL'ye dahil edin.)</span><span class="sxs-lookup"><span data-stu-id="f4eed-378">(If the configuration in the Dockerfile maps the container to a port on the host that is anything other than 80, include the host port in the URL.)</span></span>

![Bir API uç noktası yanıtının tarayıcı görünümü](./media/image18.png)

<span data-ttu-id="f4eed-380">**Şekil 5-13**.</span><span class="sxs-lookup"><span data-stu-id="f4eed-380">**Figure 5-13**.</span></span> <span data-ttu-id="f4eed-381">Örneği yerel olarak localhost kullanarak Docker uygulamanızı test etme</span><span class="sxs-lookup"><span data-stu-id="f4eed-381">Example of testing your Docker application locally using localhost</span></span>

<span data-ttu-id="f4eed-382">Docker için localhost işaret etmiyorsa IP ana bilgisayar (Bu varsayılan Docker CE kullanırken, gerekir), hizmetinize gidin ve makinenizin Ağ kartının IP adresini kullanın.</span><span class="sxs-lookup"><span data-stu-id="f4eed-382">If localhost is not pointing to the Docker host IP (by default, when using Docker CE, it should), to navigate to your service, use the IP address of your machine's network card.</span></span>

<span data-ttu-id="f4eed-383">Bu URL tarayıcıda tartışılan belirli bir kapsayıcı örneği için 80 numaralı bağlantı noktasını kullandığını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="f4eed-383">Note that this URL in the browser uses port 80 for the particular container example being discussed.</span></span> <span data-ttu-id="f4eed-384">Nasıl bu komutu çalıştırın: docker ile bir önceki adımda açıklandığı gibi dağıtılmış olduğu için ancak, dahili olarak istekleri 5000, bağlantı noktası için Rehbere yönlendiriliyorsunuz.</span><span class="sxs-lookup"><span data-stu-id="f4eed-384">However, internally the requests are being redirected to port 5000, because that was how it was deployed with the docker run command, as explained in a previous step.</span></span>

<span data-ttu-id="f4eed-385">Ayrıca, Şekil 5-14'te gösterildiği gibi terminalden curl kullanarak uygulamayı test edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f4eed-385">You can also test the application using curl from the terminal, as shown in Figure 5-14.</span></span> <span data-ttu-id="f4eed-386">Bir Docker yüklemesinde Windows üzerindeki Docker ana bilgisayar IP her zaman 10.0.75.1 makinenizin gerçek IP adresinin yanı sıra varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="f4eed-386">In a Docker installation on Windows, the default Docker Host IP is always 10.0.75.1 in addition to your machine's actual IP address.</span></span>

![Curl ile bir API uç noktası yanıtının ekran görünümü](./media/image19.png)

<span data-ttu-id="f4eed-388">**Şekil 5-14**.</span><span class="sxs-lookup"><span data-stu-id="f4eed-388">**Figure 5-14**.</span></span> <span data-ttu-id="f4eed-389">Docker uygulamanızı yerel olarak curl kullanarak test etme örneği</span><span class="sxs-lookup"><span data-stu-id="f4eed-389">Example of testing your Docker application locally using curl</span></span>

### <a name="testing-and-debugging-containers-with-visual-studio-2017"></a><span data-ttu-id="f4eed-390">Test ve hata ayıklama Visual Studio 2017 ile kapsayıcıları</span><span class="sxs-lookup"><span data-stu-id="f4eed-390">Testing and debugging containers with Visual Studio 2017</span></span>

<span data-ttu-id="f4eed-391">Çalışan kapsayıcılar, olduğu gibi çalışan kapsayıcılar Visual Studio 2017 ile hata ayıklama, .NET uygulama kadar aynı şekilde ayıklayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f4eed-391">When running and debugging the containers with Visual Studio 2017, you can debug the .NET application in much the same way as you would when running without containers.</span></span>

### <a name="testing-and-debugging-without-visual-studio"></a><span data-ttu-id="f4eed-392">Test ve hata ayıklama Visual Studio</span><span class="sxs-lookup"><span data-stu-id="f4eed-392">Testing and debugging without Visual Studio</span></span>

<span data-ttu-id="f4eed-393">Düzenleyici/CLI yaklaşımı kullanarak geliştiriyorsanız kapsayıcılarında hata ayıklama daha zordur ve izlemeleri oluşturarak hata ayıklama isteyeceksiniz.</span><span class="sxs-lookup"><span data-stu-id="f4eed-393">If you're developing using the editor/CLI approach, debugging containers is more difficult and you will want to debug by generating traces.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="f4eed-394">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="f4eed-394">Additional resources</span></span>

- <span data-ttu-id="f4eed-395">**Yerel bir Docker kapsayıcısı uygulamalarında hata ayıklama** \\</span><span class="sxs-lookup"><span data-stu-id="f4eed-395">**Debugging apps in a local Docker container** \\</span></span>
  [https://docs.microsoft.com/azure/vs-azure-tools-docker-edit-and-refresh](https://docs.microsoft.com/azure/vs-azure-tools-docker-edit-and-refresh)

- <span data-ttu-id="f4eed-396">**Steve Lasker. Derleme, hata ayıklama, Docker ile ASP.NET Core uygulamaları dağıtın.**</span><span class="sxs-lookup"><span data-stu-id="f4eed-396">**Steve Lasker. Build, Debug, Deploy ASP.NET Core Apps with Docker.**</span></span> <span data-ttu-id="f4eed-397">Video.</span><span class="sxs-lookup"><span data-stu-id="f4eed-397">Video.</span></span> \
  [https://channel9.msdn.com/Events/Visual-Studio/Visual-Studio-2017-Launch/T115](https://channel9.msdn.com/Events/Visual-Studio/Visual-Studio-2017-Launch/T115)

## <a name="simplified-workflow-when-developing-containers-with-visual-studio"></a><span data-ttu-id="f4eed-398">Visual Studio ile kapsayıcıları geliştirirken basitleştirilmiş bir iş akışı</span><span class="sxs-lookup"><span data-stu-id="f4eed-398">Simplified workflow when developing containers with Visual Studio</span></span>

<span data-ttu-id="f4eed-399">Etkili bir şekilde, Visual Studio kullanarak iş akışı Düzenleyicisi'ni / CLI yaklaşımı kullanırsanız, çok daha kolay olacaktır.</span><span class="sxs-lookup"><span data-stu-id="f4eed-399">Effectively, the workflow when using Visual Studio is a lot simpler than if you use the editor/CLI approach.</span></span> <span data-ttu-id="f4eed-400">Docker tarafından gerekli adımların çoğu için Dockerfile ilgili ve gizli ya da Visual Studio tarafından Şekil 5-15'te gösterildiği gibi Basitleştirilmiş docker-compose.yml dosyaları.</span><span class="sxs-lookup"><span data-stu-id="f4eed-400">Most of the steps required by Docker related to the Dockerfile and docker-compose.yml files are hidden or simplified by Visual Studio, as shown in Figure 5-15.</span></span>

![Visual Studio ile Basitleştirilmiş kapsayıcı geliştirme iş akışı: 1 - 2 - Docker ekleme desteği projelerine (yalnızca bir kez), 3 - çalışma kapsayıcı ya da docker uygulama kodu-uygulama oluşturma, 4 - Test uygulama veya mikro hizmetler, 5 - anında iletme depo ve yineleyin.](./media/image20.png)

<span data-ttu-id="f4eed-402">**Şekil 5-15**.</span><span class="sxs-lookup"><span data-stu-id="f4eed-402">**Figure 5-15**.</span></span> <span data-ttu-id="f4eed-403">Visual Studio ile geliştirirken basitleştirilmiş bir iş akışı</span><span class="sxs-lookup"><span data-stu-id="f4eed-403">Simplified workflow when developing with Visual Studio</span></span>

<span data-ttu-id="f4eed-404">Ayrıca, yalnızca bir kez (Docker desteği ekleme projelerinize) 2. adım gerçekleştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="f4eed-404">In addition, you need to perform step 2 (adding Docker support to your projects) just once.</span></span> <span data-ttu-id="f4eed-405">Bu nedenle, iş akışı herhangi bir geliştirme için .NET kullanarak normal geliştirme görevlerine benzer şekildedir.</span><span class="sxs-lookup"><span data-stu-id="f4eed-405">Therefore, the workflow is similar to your usual development tasks when using .NET for any other development.</span></span> <span data-ttu-id="f4eed-406">Kapsar (görüntü oluşturma işlemi, hangi kullandığınız temel görüntüleri, kapsayıcılar, vb. dağıtımını) altında ve bazen de davranışları özelleştirmek için Dockerfile veya docker-compose.yml dosyasını düzenlemeniz gerekir neler olduğunu bilmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="f4eed-406">You need to know what is going on under the covers (the image build process, what base images you're using, deployment of containers, etc.) and sometimes you will also need to edit the Dockerfile or docker-compose.yml file to customize behaviors.</span></span> <span data-ttu-id="f4eed-407">Ancak işin çoğunu, çok daha üretken hale Visual Studio kullanılarak büyük ölçüde basitleştirilir.</span><span class="sxs-lookup"><span data-stu-id="f4eed-407">But most of the work is greatly simplified by using Visual Studio, making you a lot more productive.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="f4eed-408">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="f4eed-408">Additional resources</span></span>

- <span data-ttu-id="f4eed-409">**Steve Lasker. Visual Studio 2017 ile .NET docker geliştirme** \\</span><span class="sxs-lookup"><span data-stu-id="f4eed-409">**Steve Lasker. .NET Docker Development with Visual Studio 2017** \\</span></span>
  [https://channel9.msdn.com/Events/Visual-Studio/Visual-Studio-2017-Launch/T111](https://channel9.msdn.com/Events/Visual-Studio/Visual-Studio-2017-Launch/T111)

## <a name="using-powershell-commands-in-a-dockerfile-to-set-up-windows-containers"></a><span data-ttu-id="f4eed-410">Windows kapsayıcıları ayarlamak için bir Dockerfile içinde PowerShell komutlarını kullanarak</span><span class="sxs-lookup"><span data-stu-id="f4eed-410">Using PowerShell commands in a Dockerfile to set up Windows Containers</span></span> 

<span data-ttu-id="f4eed-411">[Windows kapsayıcıları](https://docs.microsoft.com/virtualization/windowscontainers/about/index) mevcut Windows uygulamalarınızı Docker görüntüleri olarak dönüştürmek ve Docker ekosistemi sayesinde geri kalanı gibi aynı araçları ile dağıtmaya olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="f4eed-411">[Windows Containers](https://docs.microsoft.com/virtualization/windowscontainers/about/index) allow you to convert your existing Windows applications into Docker images and deploy them with the same tools as the rest of the Docker ecosystem.</span></span> <span data-ttu-id="f4eed-412">Windows kapsayıcıları kullanmak için aşağıdaki örnekte gösterildiği gibi bir Dockerfile içinde PowerShell komutlarını çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="f4eed-412">To use Windows Containers, you run PowerShell commands in the Dockerfile, as shown in the following example:</span></span>

```Dockerfile
FROM microsoft/windowsservercore
LABEL Description="IIS" Vendor="Microsoft" Version="10"
RUN powershell -Command Add-WindowsFeature Web-Server
CMD [ "ping", "localhost", "-t" ]
```

<span data-ttu-id="f4eed-413">Bu durumda, biz bir Windows Server Core temel görüntüyü (FROM ayar) kullanarak ve bir (çalışma ayarı) PowerShell komutuyla IIS'yi yükleme.</span><span class="sxs-lookup"><span data-stu-id="f4eed-413">In this case, we are using a Windows Server Core base image (the FROM setting) and installing IIS with a PowerShell command (the RUN setting).</span></span> <span data-ttu-id="f4eed-414">Benzer şekilde, ASP.NET 4.x, .NET 4.6 veya herhangi bir Windows yazılımı gibi ek bileşenler ayarlamak için PowerShell komutlarını kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f4eed-414">In a similar way, you could also use PowerShell commands to set up additional components like ASP.NET 4.x, .NET 4.6, or any other Windows software.</span></span> <span data-ttu-id="f4eed-415">Örneğin, aşağıdaki komut bir Dockerfile içinde ASP.NET 4.5 ' ayarlar:</span><span class="sxs-lookup"><span data-stu-id="f4eed-415">For example, the following command in a Dockerfile sets up ASP.NET 4.5:</span></span>

```Dockerfile
RUN powershell add-windowsfeature web-asp-net45
```

### <a name="additional-resources"></a><span data-ttu-id="f4eed-416">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="f4eed-416">Additional resources</span></span>

- <span data-ttu-id="f4eed-417">**aspnet-docker/Dockerfile.**</span><span class="sxs-lookup"><span data-stu-id="f4eed-417">**aspnet-docker/Dockerfile.**</span></span> <span data-ttu-id="f4eed-418">Windows özellikleri içerecek şekilde dockerfile'ları için örnek PowerShell komutları. \\</span><span class="sxs-lookup"><span data-stu-id="f4eed-418">Example PowerShell commands to run from dockerfiles to include Windows features.\\</span></span>
  [https://github.com/Microsoft/aspnet-docker/blob/master/4.7.1-windowsservercore-ltsc2016/runtime/Dockerfile](https://github.com/Microsoft/aspnet-docker/blob/master/4.7.1-windowsservercore-ltsc2016/runtime/Dockerfile)

>[!div class="step-by-step"]
><span data-ttu-id="f4eed-419">[Önceki](index.md)
>[İleri](../multi-container-microservice-net-applications/index.md)</span><span class="sxs-lookup"><span data-stu-id="f4eed-419">[Previous](index.md)
[Next](../multi-container-microservice-net-applications/index.md)</span></span>
