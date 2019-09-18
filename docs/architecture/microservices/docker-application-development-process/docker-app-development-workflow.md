---
title: Docker uygulamaları için geliştirme iş akışı
description: Docker tabanlı uygulamalar geliştirmeye yönelik iş akışının ayrıntılarını anlayın. Adım adım ilerleyin ve Dockerfiles 'ı iyileştirmek ve Visual Studio 'Yu kullanırken kullanılabilecek Basitleştirilmiş iş akışıyla sona erdirmek için bazı ayrıntılara ulaşın.
ms.date: 01/07/2019
ms.openlocfilehash: 36caff247d031b8808ab953ec884b7ce292858eb
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71040298"
---
# <a name="development-workflow-for-docker-apps"></a><span data-ttu-id="a84c5-104">Docker uygulamaları için geliştirme iş akışı</span><span class="sxs-lookup"><span data-stu-id="a84c5-104">Development workflow for Docker apps</span></span>

<span data-ttu-id="a84c5-105">Uygulama geliştirme yaşam döngüsü, bilgisayarınızda tercih ettiğiniz dili kullanarak kodlarınızla ve yerel olarak test ettiğiniz bir geliştirici olarak bilgisayarınızda başlatılır.</span><span class="sxs-lookup"><span data-stu-id="a84c5-105">The application development life cycle starts at your computer, as a developer, where you code the application using your preferred language and test it locally.</span></span> <span data-ttu-id="a84c5-106">Seçtiğiniz dil, çerçeve ve platforma bakılmaksızın, bu iş akışı ile Docker kapsayıcılarını her zaman geliştirip test edersiniz, ancak bunu yerel olarak yapmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="a84c5-106">With this workflow, no matter which language, framework, and platform you choose, you're always developing and testing Docker containers, but doing so locally.</span></span>

<span data-ttu-id="a84c5-107">Her kapsayıcı (bir Docker görüntüsünün örneği) aşağıdaki bileşenleri içerir:</span><span class="sxs-lookup"><span data-stu-id="a84c5-107">Each container (an instance of a Docker image) includes the following components:</span></span>

- <span data-ttu-id="a84c5-108">Bir işletim sistemi seçimi, örneğin bir Linux dağıtımı, Windows nano sunucu veya Windows Server Core.</span><span class="sxs-lookup"><span data-stu-id="a84c5-108">An operating system selection, for example, a Linux distribution, Windows Nano Server, or Windows Server Core.</span></span>

- <span data-ttu-id="a84c5-109">Geliştirme sırasında eklenen dosyalar, örneğin, kaynak kodu ve uygulama ikilileri.</span><span class="sxs-lookup"><span data-stu-id="a84c5-109">Files added during development, for example, source code and application binaries.</span></span>

- <span data-ttu-id="a84c5-110">Ortam ayarları ve bağımlılıklar gibi yapılandırma bilgileri.</span><span class="sxs-lookup"><span data-stu-id="a84c5-110">Configuration information, such as environment settings and dependencies.</span></span>

## <a name="workflow-for-developing-docker-container-based-applications"></a><span data-ttu-id="a84c5-111">Docker kapsayıcı tabanlı uygulamalar geliştirmek için iş akışı</span><span class="sxs-lookup"><span data-stu-id="a84c5-111">Workflow for developing Docker container-based applications</span></span>

<span data-ttu-id="a84c5-112">Bu bölüm, Docker kapsayıcı tabanlı uygulamalar için *iç döngü* geliştirme iş akışını açıklar.</span><span class="sxs-lookup"><span data-stu-id="a84c5-112">This section describes the *inner-loop* development workflow for Docker container-based applications.</span></span> <span data-ttu-id="a84c5-113">İç döngü iş akışı, daha geniş bir DevOps iş akışını düşünmediği anlamına gelir. Bu, üretim dağıtımına kadar dahil olabilir ve yalnızca geliştirici bilgisayarında yapılan geliştirme işlerine odaklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="a84c5-113">The inner-loop workflow means it's not considering the broader DevOps workflow, that can include up to production deployment, and just focuses on the development work done on the developer's computer.</span></span> <span data-ttu-id="a84c5-114">Bu adımlar yalnızca bir kez yapıldığından, ortamı ayarlamaya yönelik ilk adımlar dahil değildir.</span><span class="sxs-lookup"><span data-stu-id="a84c5-114">The initial steps to set up the environment aren't included, since those steps are done only once.</span></span>

<span data-ttu-id="a84c5-115">Bir uygulama, kendi hizmetlerinizin yanı sıra ek kitaplıklarınızdan oluşur (bağımlılıklar).</span><span class="sxs-lookup"><span data-stu-id="a84c5-115">An application is composed of your own services plus additional libraries (dependencies).</span></span> <span data-ttu-id="a84c5-116">Şekil 5-1 ' de gösterildiği gibi, bir Docker uygulaması oluştururken genellikle gereken temel adımlar aşağıda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="a84c5-116">The following are the basic steps you usually take when building a Docker application, as illustrated in Figure 5-1.</span></span>

![<span data-ttu-id="a84c5-117">Docker uygulamaları için geliştirme süreci: 1-uygulamanızı kodlayın, 2-Dockerfile/s, 3-Dockerfile/s 'de tanımlanan görüntüleri oluşturun, 4-(isteğe bağlı) oluşturma hizmetleri Docker-Compose. yıml dosyasında, 5-çalıştırma kapsayıcısı veya Docker-Compose uygulaması, 6-uygulamanızı veya mikro hizmetleri, 7-depoyu depoya gönderin ve tekrarlayın.</span><span class="sxs-lookup"><span data-stu-id="a84c5-117">The development process for Docker apps: 1 - Code your App, 2 - Write Dockerfile/s, 3 - Create images defined at Dockerfile/s, 4 - (optional) Compose services in the docker-compose.yml file, 5 - Run container or docker-compose app, 6 - Test your app or microservices, 7 - Push to repo and repeat.</span></span> ](./media/image1.png)

<span data-ttu-id="a84c5-118">**Şekil 5-1.**</span><span class="sxs-lookup"><span data-stu-id="a84c5-118">**Figure 5-1.**</span></span> <span data-ttu-id="a84c5-119">Docker Kapsayıcılı uygulamalar geliştirmek için adım adım iş akışı</span><span class="sxs-lookup"><span data-stu-id="a84c5-119">Step-by-step workflow for developing Docker containerized apps</span></span>

<span data-ttu-id="a84c5-120">Bu bölümde, bu tüm süreç ayrıntılıdır ve her ana adım bir Visual Studio ortamına odaklanarak açıklanmıştır.</span><span class="sxs-lookup"><span data-stu-id="a84c5-120">In this section, this whole process is detailed and every major step is explained by focusing on a Visual Studio environment.</span></span>

<span data-ttu-id="a84c5-121">Bir düzenleyici/CLı geliştirme yaklaşımı kullandığınızda (örneğin Visual Studio Code, macOS veya Windows üzerinde Docker CLı), Visual Studio 'Yu kullanmaktan daha ayrıntılı olarak, her adımı bilmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="a84c5-121">When you're using an editor/CLI development approach (for example, Visual Studio Code plus Docker CLI on macOS or Windows), you need to know every step, generally in more detail than if you're using Visual Studio.</span></span> <span data-ttu-id="a84c5-122">CLı ortamında çalışma hakkında daha fazla bilgi için bkz. [Microsoft platformları ve araçları ile e-kitap Kapsayıcılı Docker uygulaması yaşam döngüsü](https://aka.ms/dockerlifecycleebook/).</span><span class="sxs-lookup"><span data-stu-id="a84c5-122">For more information about working in a CLI environment, see the e-book [Containerized Docker Application lifecycle with Microsoft Platforms and Tools](https://aka.ms/dockerlifecycleebook/).</span></span>

<span data-ttu-id="a84c5-123">Visual Studio 2017 kullanırken, bu adımların birçoğu sizin için işlenir ve bu da üretkenliğinizi önemli ölçüde geliştirir.</span><span class="sxs-lookup"><span data-stu-id="a84c5-123">When you're using Visual Studio 2017, many of those steps are handled for you, which dramatically improves your productivity.</span></span> <span data-ttu-id="a84c5-124">Visual Studio 2017 kullanırken ve çok Kapsayıcılı uygulamaları hedeflerken bu durum özellikle doğrudur.</span><span class="sxs-lookup"><span data-stu-id="a84c5-124">This is especially true when you're using Visual Studio 2017 and targeting multi-container applications.</span></span> <span data-ttu-id="a84c5-125">Örneğin, yalnızca bir fare tıklaması ile, Visual Studio Dockerfile ve Docker-Compose. yıml dosyasını, uygulamanıza yönelik yapılandırmayla birlikte projenize ekler.</span><span class="sxs-lookup"><span data-stu-id="a84c5-125">For instance, with just one mouse click, Visual Studio adds the Dockerfile and docker-compose.yml file to your projects with the configuration for your application.</span></span> <span data-ttu-id="a84c5-126">Uygulamayı Visual Studio 'da çalıştırdığınızda, Docker görüntüsünü oluşturur ve çok Kapsayıcılı uygulamayı doğrudan Docker içinde çalıştırır; aynı zamanda birkaç kapsayıcıda hata ayıklamanıza da olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="a84c5-126">When you run the application in Visual Studio, it builds the Docker image and runs the multi-container application directly in Docker; it even allows you to debug several containers at once.</span></span> <span data-ttu-id="a84c5-127">Bu özellikler, geliştirme hızınızı artırır.</span><span class="sxs-lookup"><span data-stu-id="a84c5-127">These features will boost your development speed.</span></span>

<span data-ttu-id="a84c5-128">Ancak, yalnızca Visual Studio bu adımları otomatik hale getiren için Docker ile neler olduğunu bilmeniz gerekmez.</span><span class="sxs-lookup"><span data-stu-id="a84c5-128">However, just because Visual Studio makes those steps automatic doesn't mean that you don't need to know what's going on underneath with Docker.</span></span> <span data-ttu-id="a84c5-129">Bu nedenle, aşağıdaki kılavuz her adımda ayrıntılardır.</span><span class="sxs-lookup"><span data-stu-id="a84c5-129">Therefore, the following guidance details every step.</span></span>

![1-uygulamanızı kodlayın](./media/image2.png)

## <a name="step-1-start-coding-and-create-your-initial-application-or-service-baseline"></a><span data-ttu-id="a84c5-131">Adım 1.</span><span class="sxs-lookup"><span data-stu-id="a84c5-131">Step 1.</span></span> <span data-ttu-id="a84c5-132">Kodlamaya başlayın ve başlangıç uygulamanızı veya hizmet temelinizi oluşturun</span><span class="sxs-lookup"><span data-stu-id="a84c5-132">Start coding and create your initial application or service baseline</span></span>

<span data-ttu-id="a84c5-133">Docker uygulaması geliştirmek, Docker olmadan uygulama geliştirme yöntemine benzer.</span><span class="sxs-lookup"><span data-stu-id="a84c5-133">Developing a Docker application is similar to the way you develop an application without Docker.</span></span> <span data-ttu-id="a84c5-134">Bu fark, Docker için geliştirme yaparken, yerel ortamınızdaki Docker Kapsayıcıları içinde çalışan uygulamanızı veya hizmetlerinizi (Windows kapsayıcıları kullanılıyorsa Docker veya doğrudan Windows) bir Linux VM kurulumu) dağıtmakta ve test eteceğiz.</span><span class="sxs-lookup"><span data-stu-id="a84c5-134">The difference is that while developing for Docker, you're deploying and testing your application or services running within Docker containers in your local environment (either a Linux VM setup by Docker or directly Windows if using Windows Containers).</span></span>

### <a name="set-up-your-local-environment-with-visual-studio"></a><span data-ttu-id="a84c5-135">Visual Studio ile yerel ortamınızı ayarlama</span><span class="sxs-lookup"><span data-stu-id="a84c5-135">Set up your local environment with Visual Studio</span></span>

<span data-ttu-id="a84c5-136">Başlamak için, aşağıdaki yönergelerde açıklandığı gibi Windows için [Docker Community Edition 'ın (CE)](https://docs.docker.com/docker-for-windows/) yüklü olduğundan emin olun:</span><span class="sxs-lookup"><span data-stu-id="a84c5-136">To begin, make sure you have [Docker Community Edition (CE)](https://docs.docker.com/docker-for-windows/) for Windows installed, as explained in the following instructions:</span></span>

[<span data-ttu-id="a84c5-137">Docker CE for Windows kullanmaya başlayın</span><span class="sxs-lookup"><span data-stu-id="a84c5-137">Get started with Docker CE for Windows</span></span>](https://docs.docker.com/docker-for-windows/)

<span data-ttu-id="a84c5-138">Ayrıca, Şekil 5-2 ' de gösterildiği gibi, **.NET Core platformlar arası geliştirme** iş yükü yüklüyken Visual Studio 2017 sürüm 15,7 veya üzeri bir sürüme ihtiyacınız vardır.</span><span class="sxs-lookup"><span data-stu-id="a84c5-138">In addition, you need Visual Studio 2017 version 15.7 or later, with the **.NET Core cross-platform development** workload installed, as shown in Figure 5-2.</span></span>

![Visual Studio yüklemesi sırasında .NET Core platformlar arası geliştirme iş yükü seçimi.](./media/image3.png)

<span data-ttu-id="a84c5-140">**Şekil 5-2**.</span><span class="sxs-lookup"><span data-stu-id="a84c5-140">**Figure 5-2**.</span></span> <span data-ttu-id="a84c5-141">Visual Studio 2017 kurulumu sırasında **.NET Core platformlar arası geliştirme** iş yükünü seçme</span><span class="sxs-lookup"><span data-stu-id="a84c5-141">Selecting the **.NET Core cross-platform development** workload during Visual Studio 2017 setup</span></span>

<span data-ttu-id="a84c5-142">Uygulamanızda Docker 'ı etkinleştirmeden ve Docker 'da dağıtıp test etmeden önce bile, uygulamanızı basit .NET (genellikle .NET Core 'da) kodlamaya başlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a84c5-142">You can start coding your application in plain .NET (usually in .NET Core if you're planning to use containers) even before enabling Docker in your application and deploying and testing in Docker.</span></span> <span data-ttu-id="a84c5-143">Ancak, gerçek ortam olacağı ve herhangi bir sorun mümkün olan en kısa sürede keşfedilebilir olduğundan, Docker üzerinde en kısa sürede çalışmaya başlamanız önerilir.</span><span class="sxs-lookup"><span data-stu-id="a84c5-143">However, it is recommended that you start working on Docker as soon as possible, because that will be the real environment and any issues can be discovered as soon as possible.</span></span> <span data-ttu-id="a84c5-144">Visual Studio, Visual Studio 'daki çok Kapsayıcılı uygulamalarda hata ayıklarken en iyi örnek olan Docker ile neredeyse oldukça kolay bir şekilde çalışmasını sağlayan bu, önerilir.</span><span class="sxs-lookup"><span data-stu-id="a84c5-144">This is encouraged because Visual Studio makes it so easy to work with Docker that it almost feels transparent—the best example when debugging multi-container applications from Visual Studio.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="a84c5-145">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="a84c5-145">Additional resources</span></span>

- <span data-ttu-id="a84c5-146">**Docker CE for Windows kullanmaya başlayın** </span><span class="sxs-lookup"><span data-stu-id="a84c5-146">**Get started with Docker CE for Windows** </span></span>\
  <https://docs.docker.com/docker-for-windows/>

- <span data-ttu-id="a84c5-147">**Visual Studio 2017** </span><span class="sxs-lookup"><span data-stu-id="a84c5-147">**Visual Studio 2017** </span></span>\
  [https://visualstudio.microsoft.com/downloads/](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017)

![2-Dockerfiles yazma](./media/image4.png)

## <a name="step-2-create-a-dockerfile-related-to-an-existing-net-base-image"></a><span data-ttu-id="a84c5-149">Adım 2.</span><span class="sxs-lookup"><span data-stu-id="a84c5-149">Step 2.</span></span> <span data-ttu-id="a84c5-150">Mevcut bir .NET temel görüntüsüyle ilişkili bir Dockerfile oluşturma</span><span class="sxs-lookup"><span data-stu-id="a84c5-150">Create a Dockerfile related to an existing .NET base image</span></span>

<span data-ttu-id="a84c5-151">Derlemek istediğiniz her özel görüntü için bir Dockerfile gerekir; Ayrıca, Visual Studio 'dan otomatik olarak veya Docker CLı (Docker Run ve Docker-Compose komutları) kullanarak el ile dağıtım yapıp etmeksizin her bir kapsayıcının dağıtılması için bir Dockerfile gerekir.</span><span class="sxs-lookup"><span data-stu-id="a84c5-151">You need a Dockerfile for each custom image you want to build; you also need a Dockerfile for each container to be deployed, whether you deploy automatically from Visual Studio or manually using the Docker CLI (docker run and docker-compose commands).</span></span> <span data-ttu-id="a84c5-152">Uygulamanız tek bir özel hizmet içeriyorsa, tek bir Dockerfile gerekir.</span><span class="sxs-lookup"><span data-stu-id="a84c5-152">If your application contains a single custom service, you need a single Dockerfile.</span></span> <span data-ttu-id="a84c5-153">Uygulamanız birden çok hizmet içeriyorsa (bir mikro hizmet mimarisinde olduğu gibi), her hizmet için bir Dockerfile gerekir.</span><span class="sxs-lookup"><span data-stu-id="a84c5-153">If your application contains multiple services (as in a microservices architecture), you need one Dockerfile for each service.</span></span>

<span data-ttu-id="a84c5-154">Dockerfile, uygulamanızın veya hizmetinizin kök klasörüne yerleştirilir.</span><span class="sxs-lookup"><span data-stu-id="a84c5-154">The Dockerfile is placed in the root folder of your application or service.</span></span> <span data-ttu-id="a84c5-155">Bu, Docker 'a uygulamanızı veya hizmetinizi bir kapsayıcıda ayarlamayı ve çalıştırmayı söyleyen komutları içerir.</span><span class="sxs-lookup"><span data-stu-id="a84c5-155">It contains the commands that tell Docker how to set up and run your application or service in a container.</span></span> <span data-ttu-id="a84c5-156">Kodda el ile Dockerfile oluşturabilir ve bunları .NET bağımlılıklarınızla birlikte projenize ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a84c5-156">You can manually create a Dockerfile in code and add it to your project along with your .NET dependencies.</span></span>

<span data-ttu-id="a84c5-157">Visual Studio ve Docker Araçları ile bu görev yalnızca birkaç fare tıklamasını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="a84c5-157">With Visual Studio and its tools for Docker, this task requires only a few mouse clicks.</span></span> <span data-ttu-id="a84c5-158">Visual Studio 2017 ' de yeni bir proje oluşturduğunuzda, Şekil 5-3 ' de gösterildiği gibi, **kapsayıcı (Docker) desteğini etkinleştir**adlı bir seçenek vardır.</span><span class="sxs-lookup"><span data-stu-id="a84c5-158">When you create a new project in Visual Studio 2017, there's an option named **Enable Container (Docker) Support**, as shown in Figure 5-3.</span></span>

![Visual Studio 2017 'de yeni bir ASP.NET Core projesi oluştururken Docker desteği onay kutusunu Etkinleştir](./media/image5.png)

<span data-ttu-id="a84c5-160">**Şekil 5-3**.</span><span class="sxs-lookup"><span data-stu-id="a84c5-160">**Figure 5-3**.</span></span> <span data-ttu-id="a84c5-161">Visual Studio 2017 'de yeni bir ASP.NET Core projesi oluştururken Docker desteğini etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="a84c5-161">Enabling Docker Support when creating a new ASP.NET Core project in Visual Studio 2017</span></span>

<span data-ttu-id="a84c5-162">Ayrıca, Şekil 5-4 ' de gösterildiği gibi, mevcut bir ASP.NET Core Web uygulaması projesinde, **Çözüm Gezgini** projeye sağ tıklayıp**Docker desteği** **Ekle** > ' yi seçerek Docker desteğini etkinleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a84c5-162">You can also enable Docker support on an existing ASP.NET Core web app project by right-clicking the project in **Solution Explorer** and selecting **Add** > **Docker Support**, as shown in Figure 5-4.</span></span>

![Visual Studio 'da Docker desteği Ekle menü seçeneği](./media/image6.png)

<span data-ttu-id="a84c5-164">**Şekil 5-4**.</span><span class="sxs-lookup"><span data-stu-id="a84c5-164">**Figure 5-4**.</span></span> <span data-ttu-id="a84c5-165">Mevcut bir Visual Studio 2017 projesinde Docker desteğini etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="a84c5-165">Enabling Docker support in an existing Visual Studio 2017 project</span></span>

<span data-ttu-id="a84c5-166">Bu eylem, gerekli yapılandırmayla projeye bir *Dockerfile* ekler ve yalnızca ASP.NET Core projelerinde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="a84c5-166">This action adds a *Dockerfile* to the project with the required configuration, and is only available on ASP.NET Core projects.</span></span>

<span data-ttu-id="a84c5-167">Benzer bir şekilde, Visual Studio, **> kapsayıcı Orchestrator desteği**seçeneğine sahip tüm çözüme yönelik bir Docker-Compose. yıml dosyası da ekleyebilir.</span><span class="sxs-lookup"><span data-stu-id="a84c5-167">In a similar fashion, Visual Studio can also add a docker-compose.yml file for the whole solution with the option **Add > Container Orchestrator Support**.</span></span> <span data-ttu-id="a84c5-168">4\. adımda bu seçeneği daha ayrıntılı bir şekilde araştıracağız.</span><span class="sxs-lookup"><span data-stu-id="a84c5-168">In step 4, we'll explore this option in greater detail.</span></span>

### <a name="using-an-existing-official-net-docker-image"></a><span data-ttu-id="a84c5-169">Mevcut bir resmi .NET Docker görüntüsünü kullanma</span><span class="sxs-lookup"><span data-stu-id="a84c5-169">Using an existing official .NET Docker image</span></span>

<span data-ttu-id="a84c5-170">Genellikle, [Docker Hub](https://hub.docker.com/) kayıt defteri gibi resmi bir depodan aldığınız temel görüntünün en üstünde Kapsayıcınız için özel bir görüntü oluşturursunuz.</span><span class="sxs-lookup"><span data-stu-id="a84c5-170">You usually build a custom image for your container on top of a base image you get from an official repository like the [Docker Hub](https://hub.docker.com/) registry.</span></span> <span data-ttu-id="a84c5-171">Visual Studio 'da Docker desteğini etkinleştirdiğinizde bu durum kesin olarak ne olur?</span><span class="sxs-lookup"><span data-stu-id="a84c5-171">That is precisely what happens under the covers when you enable Docker support in Visual Studio.</span></span> <span data-ttu-id="a84c5-172">Dockerfile, var olan `aspnetcore` bir görüntüyü kullanacaktır.</span><span class="sxs-lookup"><span data-stu-id="a84c5-172">Your Dockerfile will use an existing `aspnetcore` image.</span></span>

<span data-ttu-id="a84c5-173">Daha önce seçtiğiniz çerçeveye ve işletim sistemine bağlı olarak, hangi Docker görüntülerini ve depolarınızı kullanacağınızı anlatılmıştır.</span><span class="sxs-lookup"><span data-stu-id="a84c5-173">Earlier we explained which Docker images and repos you can use, depending on the framework and OS you have chosen.</span></span> <span data-ttu-id="a84c5-174">Örneğin, ASP.NET Core (Linux veya Windows) kullanmak istiyorsanız kullanılacak `mcr.microsoft.com/dotnet/core/aspnet:2.2`görüntü.</span><span class="sxs-lookup"><span data-stu-id="a84c5-174">For instance, if you want to use ASP.NET Core (Linux or Windows), the image to use is `mcr.microsoft.com/dotnet/core/aspnet:2.2`.</span></span> <span data-ttu-id="a84c5-175">Bu nedenle, yalnızca Kapsayıcınız için kullanacağınız temel Docker görüntüsünü belirtmeniz yeterlidir.</span><span class="sxs-lookup"><span data-stu-id="a84c5-175">Therefore, you just need to specify what base Docker image you will use for your container.</span></span> <span data-ttu-id="a84c5-176">Bunu, dockerfile `FROM mcr.microsoft.com/dotnet/core/aspnet:2.2` dosyanıza ekleyerek yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a84c5-176">You do that by adding `FROM mcr.microsoft.com/dotnet/core/aspnet:2.2` to your Dockerfile.</span></span> <span data-ttu-id="a84c5-177">Bu, Visual Studio tarafından otomatik olarak gerçekleştirilir, ancak sürümü güncelleştirirseniz, bu değeri güncelleştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="a84c5-177">This will be automatically performed by Visual Studio, but if you were to update the version, you update this value.</span></span>

<span data-ttu-id="a84c5-178">Docker Hub 'dan sürüm numarası olan resmi bir .NET görüntü deposu kullanmak, tüm makinelerde (geliştirme, test ve üretim dahil) aynı dil özelliklerinin kullanılabilmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="a84c5-178">Using an official .NET image repository from Docker Hub with a version number ensures that the same language features are available on all machines (including development, testing, and production).</span></span>

<span data-ttu-id="a84c5-179">Aşağıdaki örnekte, bir ASP.NET Core kapsayıcısı için örnek bir Dockerfile gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="a84c5-179">The following example shows a sample Dockerfile for an ASP.NET Core container.</span></span>

```Dockerfile
FROM mcr.microsoft.com/dotnet/core/aspnet:2.2
ARG source
WORKDIR /app
EXPOSE 80
COPY ${source:-obj/Docker/publish} .
ENTRYPOINT ["dotnet", " MySingleContainerWebApp.dll "]
```

<span data-ttu-id="a84c5-180">Bu durumda, görüntü, resmi ASP.NET Core Docker görüntüsünün 2,2 sürümünü temel alır (Linux ve Windows için çoklu mimari).</span><span class="sxs-lookup"><span data-stu-id="a84c5-180">In this case, the image is based on version 2.2 of the official ASP.NET Core Docker image (multi-arch for Linux and Windows).</span></span> <span data-ttu-id="a84c5-181">Bu ayar `FROM mcr.microsoft.com/dotnet/core/aspnet:2.2`budur.</span><span class="sxs-lookup"><span data-stu-id="a84c5-181">This is the setting `FROM mcr.microsoft.com/dotnet/core/aspnet:2.2`.</span></span> <span data-ttu-id="a84c5-182">(Bu temel görüntü hakkında daha fazla bilgi için bkz. [.NET Core Docker Image](https://hub.docker.com/_/microsoft-dotnet-core/) sayfası.) Dockerfile 'da, çalışma zamanında kullanacağınız TCP bağlantı noktasını dinlemek için Docker 'a (Bu durumda, "kullanıma hazır ayarıyla yapılandırıldığı şekilde, bağlantı noktası 80) da sahip olmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="a84c5-182">(For more information about this base image, see the [.NET Core Docker Image](https://hub.docker.com/_/microsoft-dotnet-core/) page.) In the Dockerfile, you also need to instruct Docker to listen on the TCP port you will use at runtime (in this case, port 80, as configured with the EXPOSE setting).</span></span>

<span data-ttu-id="a84c5-183">Kullanmakta olduğunuz dile ve çerçeveye bağlı olarak Dockerfile içinde ek yapılandırma ayarları belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a84c5-183">You can specify additional configuration settings in the Dockerfile, depending on the language and framework you're using.</span></span> <span data-ttu-id="a84c5-184">Örneğin, giriş noktası satırı `["dotnet", "MySingleContainerWebApp.dll"]` , Docker 'ın bir .NET Core uygulaması çalıştırmasını söyler.</span><span class="sxs-lookup"><span data-stu-id="a84c5-184">For instance, the ENTRYPOINT line with `["dotnet", "MySingleContainerWebApp.dll"]` tells Docker to run a .NET Core application.</span></span> <span data-ttu-id="a84c5-185">.NET uygulamasını derlemek ve çalıştırmak için SDK ve .NET Core CLI (DotNet CLı) kullanıyorsanız, bu ayar farklı olur.</span><span class="sxs-lookup"><span data-stu-id="a84c5-185">If you're using the SDK and the .NET Core CLI (dotnet CLI) to build and run the .NET application, this setting would be different.</span></span> <span data-ttu-id="a84c5-186">Alt çizgi, GIRIŞ noktası çizgisi ve diğer ayarların, uygulamanız için seçtiğiniz dile ve platforma bağlı olarak farklı olacaktır.</span><span class="sxs-lookup"><span data-stu-id="a84c5-186">The bottom line is that the ENTRYPOINT line and other settings will be different depending on the language and platform you choose for your application.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="a84c5-187">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="a84c5-187">Additional resources</span></span>

- <span data-ttu-id="a84c5-188">**.NET Core uygulamaları için Docker görüntüleri oluşturma** </span><span class="sxs-lookup"><span data-stu-id="a84c5-188">**Building Docker Images for .NET Core Applications** </span></span>\
  [https://docs.microsoft.com/dotnet/core/docker/building-net-docker-images](../../../core/docker/building-net-docker-images.md)

- <span data-ttu-id="a84c5-189">**Kendi görüntünüzü oluşturun**.</span><span class="sxs-lookup"><span data-stu-id="a84c5-189">**Build your own image**.</span></span> <span data-ttu-id="a84c5-190">Resmi Docker belgelerinde. </span><span class="sxs-lookup"><span data-stu-id="a84c5-190">In the official Docker documentation.</span></span>\
  <https://docs.docker.com/engine/tutorials/dockerimages/>

- <span data-ttu-id="a84c5-191">**.NET kapsayıcı görüntüleriyle güncel kalarak** </span><span class="sxs-lookup"><span data-stu-id="a84c5-191">**Staying up-to-date with .NET Container Images** </span></span>\
  <https://devblogs.microsoft.com/dotnet/staying-up-to-date-with-net-container-images/>

- <span data-ttu-id="a84c5-192">**.NET ve Docker birlikte kullanma-DockerCon 2018 güncelleştirmesi** </span><span class="sxs-lookup"><span data-stu-id="a84c5-192">**Using .NET and Docker Together - DockerCon 2018 Update** </span></span>\
  <https://devblogs.microsoft.com/dotnet/using-net-and-docker-together-dockercon-2018-update/>

### <a name="using-multi-arch-image-repositories"></a><span data-ttu-id="a84c5-193">Multi-Arch Image depoları kullanma</span><span class="sxs-lookup"><span data-stu-id="a84c5-193">Using multi-arch image repositories</span></span>

<span data-ttu-id="a84c5-194">Tek bir depo, Linux görüntüsü ve Windows görüntüsü gibi platform türevlerini içerebilir.</span><span class="sxs-lookup"><span data-stu-id="a84c5-194">A single repo can contain platform variants, such as a Linux image and a Windows image.</span></span> <span data-ttu-id="a84c5-195">Bu özellik, Microsoft (temel görüntü oluşturucuları) gibi satıcıların birden çok platformu (Linux ve Windows) kapsayan tek bir depoyu oluşturmalarına olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="a84c5-195">This feature allows vendors like Microsoft (base image creators) to create a single repo to cover multiple platforms (that is Linux and Windows).</span></span> <span data-ttu-id="a84c5-196">Örneğin, Docker Hub kayıt defterinde bulunan [DotNet/Core](https://hub.docker.com/_/microsoft-dotnet-core/) deposu, aynı depo adını kullanarak Linux ve Windows nano sunucu desteği sağlar.</span><span class="sxs-lookup"><span data-stu-id="a84c5-196">For example, the [dotnet/core](https://hub.docker.com/_/microsoft-dotnet-core/) repository available in the Docker Hub registry provides support for Linux and Windows Nano Server by using the same repo name.</span></span>

<span data-ttu-id="a84c5-197">Bir etiketi belirtirseniz, aşağıdaki durumlarda açık olan bir platformu hedefliyorsanız:</span><span class="sxs-lookup"><span data-stu-id="a84c5-197">If you specify a tag, targeting a platform that is explicit like in the following cases:</span></span>

- `microsoft/dotnet:2.2-aspnetcore-runtime-stretch-slim` \
  <span data-ttu-id="a84c5-198">Hedefler: .NET Core 2,2 çalışma zamanı-yalnızca Linux üzerinde</span><span class="sxs-lookup"><span data-stu-id="a84c5-198">Targets: .NET Core 2.2 runtime-only on Linux</span></span>

- `microsoft/dotnet:2.2-aspnetcore-runtime-nanoserver-1809` \
  <span data-ttu-id="a84c5-199">Hedefler: .NET Core 2,2 çalışma zamanı-yalnızca Windows nano Server üzerinde</span><span class="sxs-lookup"><span data-stu-id="a84c5-199">Targets: .NET Core 2.2 runtime-only on Windows Nano Server</span></span>

<span data-ttu-id="a84c5-200">Ancak, aynı etiketle birlikte aynı görüntü adını belirtirseniz, çok katmanlı görüntüler ( `aspnetcore` görüntü gibi), aşağıdaki örnekte gösterildiği gibi, dağıttığınız Docker ana bilgisayar işletim sistemine bağlı olarak Linux veya Windows sürümünü kullanır:</span><span class="sxs-lookup"><span data-stu-id="a84c5-200">But, if you specify the same image name, even with the same tag, the multi-arch images (like the `aspnetcore` image) will use the Linux or Windows version depending on the Docker host OS you're deploying, as shown in the following example:</span></span>

- `microsoft/dotnet:2.2-aspnetcore-runtime` \
  <span data-ttu-id="a84c5-201">Multi-Arch: .NET Core 2,2 Runtime-yalnızca Docker Konağı işletim sistemine bağlı olarak Linux veya Windows nano Server</span><span class="sxs-lookup"><span data-stu-id="a84c5-201">Multi-arch: .NET Core 2.2 runtime-only on Linux or Windows Nano Server depending on the Docker host OS</span></span>

<span data-ttu-id="a84c5-202">Bu şekilde, bir Windows ana bilgisayardan bir görüntü çektiğinizde Windows türevini çeker ve aynı görüntü adının bir Linux ana bilgisayardan çekilerek Linux varyantı alınır.</span><span class="sxs-lookup"><span data-stu-id="a84c5-202">This way, when you pull an image from a Windows host, it will pull the Windows variant, and pulling the same image name from a Linux host will pull the Linux variant.</span></span>

### <a name="multi-stage-builds-in-dockerfile"></a><span data-ttu-id="a84c5-203">Dockerfile 'da çok aşamalı derlemeler</span><span class="sxs-lookup"><span data-stu-id="a84c5-203">Multi-stage builds in Dockerfile</span></span>

<span data-ttu-id="a84c5-204">Dockerfile, bir Batch betiğine benzer.</span><span class="sxs-lookup"><span data-stu-id="a84c5-204">The Dockerfile is similar to a batch script.</span></span> <span data-ttu-id="a84c5-205">Makineyi komut satırından kurmak zorunda kaldıysanız, yapabileceklerinize benzer.</span><span class="sxs-lookup"><span data-stu-id="a84c5-205">Similar to what you would do if you had to set up the machine from the command line.</span></span>

<span data-ttu-id="a84c5-206">Başlangıç bağlamını ayarlayan bir temel görüntüyle başlar, bu, ana bilgisayar işletim sisteminin üst kısmında yer alan başlangıç dosya sistemi gibidir.</span><span class="sxs-lookup"><span data-stu-id="a84c5-206">It starts with a base image that sets up the initial context, it's like the startup filesystem, that sits on top of the host OS.</span></span> <span data-ttu-id="a84c5-207">Bu bir işletim sistemi değildir, ancak kapsayıcının içindeki "The" OS gibi düşünün.</span><span class="sxs-lookup"><span data-stu-id="a84c5-207">It's not an OS, but you can think of if like "the" OS inside the container.</span></span>

<span data-ttu-id="a84c5-208">Her komut satırının yürütülmesi, bir önceki bir değişiklikten değişikliklerle dosya sisteminde yeni bir katman oluşturur; böylece, birleştirildiğinde, sonuçta elde edilen dosya sistemi oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="a84c5-208">The execution of every command line creates a new layer on the filesystem with the changes from the previous one, so that, when combined, produce the resulting filesystem.</span></span>

<span data-ttu-id="a84c5-209">Her yeni katman, önceki birinin üzerine "oturduğu" ve sonuçta elde edilen görüntü boyutu her komutla arttığı için, örneğin, bir uygulama oluşturmak ve yayımlamak için gerekli SDK 'yi içermesi gerekiyorsa görüntüler çok büyük alabilir.</span><span class="sxs-lookup"><span data-stu-id="a84c5-209">Since every new layer "rests" on top of the previous one and the resulting image size increases with every command, images can get very large if they have to include, for example, the SDK needed to build and publish an application.</span></span>

<span data-ttu-id="a84c5-210">Bu, çok aşamalı derlemelerin, Magic 'i yapmak için çizim içine (Docker 17,05 ve üzeri) sahip olduğu yerdir.</span><span class="sxs-lookup"><span data-stu-id="a84c5-210">This is where multi-stage builds get into the plot (from Docker 17.05 and higher) to do their magic.</span></span>

<span data-ttu-id="a84c5-211">Temel fikir, bir aşamanın ilk görüntü olduğu ve ardından bir veya daha fazla komutun ardından son aşamanın son görüntü boyutunu belirlediği aşamalar halinde Dockerfile yürütme işlemini ayırabilmeniz için de kullanılır.</span><span class="sxs-lookup"><span data-stu-id="a84c5-211">The core idea is that you can separate the Dockerfile execution process in stages, where a stage is an initial image followed by one or more commands, and the last stage determines the final image size.</span></span>

<span data-ttu-id="a84c5-212">Kısaca, çok aşamalı derlemeler, oluşturma işleminin farklı "aşamalarda" bölünmesini sağlar ve ardından son görüntüyü ara aşamaların yalnızca ilgili dizinleri ele alarak birleştirir.</span><span class="sxs-lookup"><span data-stu-id="a84c5-212">In short, multi-stage builds allow splitting the creation in different "phases" and then assemble the final image taking only the relevant directories from the intermediate stages.</span></span> <span data-ttu-id="a84c5-213">Bu özelliği kullanmaya yönelik genel strateji şunlardır:</span><span class="sxs-lookup"><span data-stu-id="a84c5-213">The general strategy to use this feature is:</span></span>

1. <span data-ttu-id="a84c5-214">Uygulamayı oluşturmak ve bir klasöre yayımlamak için gereken her şeyi içeren bir temel SDK görüntüsünü (ne kadar büyük değildir) kullanın ve ardından</span><span class="sxs-lookup"><span data-stu-id="a84c5-214">Use a base SDK image (doesn't matter how large), with everything needed to build and publish the application to a folder and then</span></span>

2. <span data-ttu-id="a84c5-215">Küçük bir son görüntü oluşturmak için, yalnızca bir temel, küçük, çalışma zamanı görüntüsü kullanın ve önceki aşamada yayımlama klasörünü kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="a84c5-215">Use a base, small, runtime-only image and copy the publishing folder from the previous stage to produce a small final image.</span></span>

<span data-ttu-id="a84c5-216">Çoklu aşamayı anlamanın en iyi yolu, bir Dockerfile 'ın ayrıntılı ve satıra göre ayrıntılıdır. böylece, bir projeye Docker desteği eklerken Visual Studio tarafından oluşturulan ilk Dockerfile ile başlayalım ve daha sonra bazı iyileştirmeler elde edilir.</span><span class="sxs-lookup"><span data-stu-id="a84c5-216">Probably the best way to understand multi-stage is going through a Dockerfile in detail, line by line, so let's begin with the initial Dockerfile created by Visual Studio when adding Docker support to a project and will get into some optimizations later.</span></span>

<span data-ttu-id="a84c5-217">İlk Dockerfile şuna benzer görünebilir:</span><span class="sxs-lookup"><span data-stu-id="a84c5-217">The initial Dockerfile might look something like this:</span></span>

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
20  RUN dotnet build Catalog.API.csproj -c Release -o /app
21
22  FROM build AS publish
23  RUN dotnet publish Catalog.API.csproj -c Release -o /app
24
25  FROM base AS final
26  WORKDIR /app
27  COPY --from=publish /app .
28  ENTRYPOINT ["dotnet", "Catalog.API.dll"]
```

<span data-ttu-id="a84c5-218">Ayrıntılar, satır satır:</span><span class="sxs-lookup"><span data-stu-id="a84c5-218">And these are the details, line by line:</span></span>

- <span data-ttu-id="a84c5-219">**Satır #1:** Yalnızca bir "küçük" çalışma zamanı temel görüntüsü ile bir aşama başlatın, başvuru için **temel** çağırın.</span><span class="sxs-lookup"><span data-stu-id="a84c5-219">**Line #1:** Begin a stage with a "small" runtime-only base image, call it **base** for reference.</span></span>

- <span data-ttu-id="a84c5-220">**Satır #2:** Görüntüde **/App** dizinini oluşturun.</span><span class="sxs-lookup"><span data-stu-id="a84c5-220">**Line #2:** Create the **/app** directory in the image.</span></span>

- <span data-ttu-id="a84c5-221">**Satır #3:** **80**numaralı bağlantı noktasını kullanıma sunun.</span><span class="sxs-lookup"><span data-stu-id="a84c5-221">**Line #3:** Expose port **80**.</span></span>

- <span data-ttu-id="a84c5-222">**Satır #5:** Oluşturma/yayımlama için "büyük" görüntüyle yeni bir aşama başlatın.</span><span class="sxs-lookup"><span data-stu-id="a84c5-222">**Line #5:** Begin a new stage with the "large" image for building/publishing.</span></span> <span data-ttu-id="a84c5-223">Başvuru için **derlemeyi** çağırın.</span><span class="sxs-lookup"><span data-stu-id="a84c5-223">Call it **build** for reference.</span></span>

- <span data-ttu-id="a84c5-224">**Satır #6:** Görüntüde **/src** dizini oluşturun.</span><span class="sxs-lookup"><span data-stu-id="a84c5-224">**Line #6:** Create directory **/src** in the image.</span></span>

- <span data-ttu-id="a84c5-225">**Satır #7:** 16. satıra kadar, paketleri daha sonra geri yükleyebilmeleri için başvurulan **. csproj** proje dosyalarını kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="a84c5-225">**Line #7:** Up to line 16, copy referenced **.csproj** project files to be able to restore packages later.</span></span>

- <span data-ttu-id="a84c5-226">**Satır #17:** **Catalog. API** projesi ve başvurulan projeler için paketleri geri yükleyin.</span><span class="sxs-lookup"><span data-stu-id="a84c5-226">**Line #17:** Restore packages for the **Catalog.API** project and the referenced projects.</span></span>

- <span data-ttu-id="a84c5-227">**Satır #18:** **Çözüme yönelik tüm dizin ağacını** ( **. dockerıgnore** dosyasına dahil edilen dosyalar/dizinler hariç) görüntüdeki **/src** dizinine kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="a84c5-227">**Line #18:** Copy **all directory tree for the solution** (except the files/directories included in the **.dockerignore** file) to the **/src** directory in the image.</span></span>

- <span data-ttu-id="a84c5-228">**Satır #19:** Geçerli klasörü **Catalog. API** projesi olarak değiştirin.</span><span class="sxs-lookup"><span data-stu-id="a84c5-228">**Line #19:** Change the current folder to the **Catalog.API** project.</span></span>

- <span data-ttu-id="a84c5-229">**Satır #20:** Projeyi (ve diğer proje bağımlılıklarını) ve görüntüdeki **/App** dizinine çıkışı oluşturun.</span><span class="sxs-lookup"><span data-stu-id="a84c5-229">**Line #20:** Build the project (and other project dependencies) and output to the **/app** directory in the image.</span></span>

- <span data-ttu-id="a84c5-230">**Satır #22:** Derlemeden devam eden yeni bir aşama başlatın.</span><span class="sxs-lookup"><span data-stu-id="a84c5-230">**Line #22:** Begin a new stage continuing from the build.</span></span> <span data-ttu-id="a84c5-231">Başvuru için **Yayımla** ' yı çağırın.</span><span class="sxs-lookup"><span data-stu-id="a84c5-231">Call it **publish** for reference.</span></span>

- <span data-ttu-id="a84c5-232">**Satır #23:** Projeyi (ve bağımlılıkları) ve çıktıyı görüntüdeki **/App** dizinine yayımlayın.</span><span class="sxs-lookup"><span data-stu-id="a84c5-232">**Line #23:** Publish the project (and dependencies) and output to the **/app** directory in the image.</span></span>

- <span data-ttu-id="a84c5-233">**Satır #25:** **Temel** 'den devam eden yeni bir aşama başlatın ve **nihai**çağrı yapın.</span><span class="sxs-lookup"><span data-stu-id="a84c5-233">**Line #25:** Begin a new stage continuing from **base** and call it **final**.</span></span>

- <span data-ttu-id="a84c5-234">**Satır #26:** Geçerli dizini **/App**olarak değiştirin.</span><span class="sxs-lookup"><span data-stu-id="a84c5-234">**Line #26:** Change the current directory to **/app**.</span></span>

- <span data-ttu-id="a84c5-235">**Satır #27:** **/App** dizinini aşama **Yayımla** ' dan geçerli dizine kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="a84c5-235">**Line #27:** Copy the **/app** directory from stage **publish** to the current directory.</span></span>

- <span data-ttu-id="a84c5-236">**Satır #28:** Kapsayıcı başlatıldığında çalıştırılacak komutu tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="a84c5-236">**Line #28:** Define the command to run when the container is started.</span></span>

<span data-ttu-id="a84c5-237">Şimdi, eShopOnContainers söz konusu olduğunda tüm işlem performansını geliştirmek için bazı iyileştirmeleri keşfedelim, Linux kapsayıcılarında eksiksiz çözümü oluşturmak için 22 dakika veya daha uzun bir süre anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="a84c5-237">Now let's explore some optimizations to improve the whole process performance that, in the case of eShopOnContainers, means about 22 minutes or more to build the complete solution in Linux containers.</span></span>

<span data-ttu-id="a84c5-238">Oldukça basit olan Docker 'ın katman önbelleği özelliğinden faydalanabilirsiniz: temel görüntü ve komutlar daha önce yürütülmüş gibi aynıysa, yalnızca komutları yürütmeye gerek kalmadan elde edilen katmanı kullanabilir ve bu nedenle bir süre tasarruf edebilir.</span><span class="sxs-lookup"><span data-stu-id="a84c5-238">You'll take advantage of Docker's layer cache feature, which is quite simple: if the base image and the commands are the same as some previously executed, it can just use the resulting layer without the need to execute the commands, thus saving some time.</span></span>

<span data-ttu-id="a84c5-239">Bu nedenle, **oluşturma** aşamasına odaklanalım, satırlar 5-6, genellikle aynıdır, ancak her iki satır 7-17, eShopOnContainers 'dan her bir hizmet için farklıdır, ancak satırları 7-16, her zaman yürütülmesi gerekir, ancak satırları:</span><span class="sxs-lookup"><span data-stu-id="a84c5-239">So, let's focus on the **build** stage, lines 5-6 are mostly the same, but lines 7-17 are different for every service from eShopOnContainers, so they have to execute every single time, however if you changed lines 7-16 to:</span></span>

```Dockerfile
COPY . .
```

<span data-ttu-id="a84c5-240">Böylece, her hizmet için yalnızca aynı olacak, tüm çözümü kopyalayacak ve daha büyük bir katman oluşturacak ancak:</span><span class="sxs-lookup"><span data-stu-id="a84c5-240">Then it would be just the same for every service, it would copy the whole solution and would create a larger layer but:</span></span>

1. <span data-ttu-id="a84c5-241">Kopyalama işlemi yalnızca ilk kez yürütülür (bir dosya değiştirildiğinde ve yeniden oluşturulduğunda) ve diğer tüm hizmetler için önbelleği kullanacaksanız</span><span class="sxs-lookup"><span data-stu-id="a84c5-241">The copy process would only be executed the first time (and when rebuilding if a file is changed) and would use the cache for all other services and</span></span>

2. <span data-ttu-id="a84c5-242">Büyük görüntü bir ara aşamada gerçekleştiği için, son görüntü boyutunu etkilemez.</span><span class="sxs-lookup"><span data-stu-id="a84c5-242">Since the larger image occurs in an intermediate stage it, doesn't affect the final image size.</span></span>

<span data-ttu-id="a84c5-243">Sonraki önemli iyileştirme, her eshoponcontainers hizmeti için de farklı olan 17. satırda yürütülen `restore` komutu içerir.</span><span class="sxs-lookup"><span data-stu-id="a84c5-243">The next significant optimization involves the `restore` command executed in line 17, which is also different for every service of eShopOnContainers.</span></span> <span data-ttu-id="a84c5-244">Bu satırı yalnızca öğesine değiştirirseniz:</span><span class="sxs-lookup"><span data-stu-id="a84c5-244">If you change that line to just:</span></span>

```Dockerfile
RUN dotnet restore
```

<span data-ttu-id="a84c5-245">Tüm çözüm için paketleri geri yükler, ancak yeniden geçerli stratejiyle 15 kez yerine yalnızca bir kez yapılır.</span><span class="sxs-lookup"><span data-stu-id="a84c5-245">It would restore the packages for the whole solution, but then again, it would do it just once, instead of the 15 times with the current strategy.</span></span>

<span data-ttu-id="a84c5-246">Ancak, `dotnet restore` yalnızca klasörde tek bir proje veya çözüm dosyası varsa çalışır, bu nedenle bu, çok fazla ayrıntıya ulaşmadan bu bir bit daha karmaşıktır ve bunu çözmek için bir yoldur:</span><span class="sxs-lookup"><span data-stu-id="a84c5-246">However, `dotnet restore` only runs if there's a single project or solution file in the folder, so achieving this is a bit more complicated and the way to solve it, without getting into too many details, is this:</span></span>

1. <span data-ttu-id="a84c5-247">Aşağıdaki satırları **. dockerıgnore**öğesine ekleyin:</span><span class="sxs-lookup"><span data-stu-id="a84c5-247">Add the following lines to **.dockerignore**:</span></span>

   - <span data-ttu-id="a84c5-248">`*.sln`, ana klasör ağacındaki tüm çözüm dosyalarını yoksaymak için</span><span class="sxs-lookup"><span data-stu-id="a84c5-248">`*.sln`, to ignore all solution files in the main folder tree</span></span>

   - <span data-ttu-id="a84c5-249">`!eShopOnContainers-ServicesAndWebApps.sln`, yalnızca bu çözüm dosyasını dahil etmek için.</span><span class="sxs-lookup"><span data-stu-id="a84c5-249">`!eShopOnContainers-ServicesAndWebApps.sln`, to include only this solution file.</span></span>

2. <span data-ttu-id="a84c5-250">Bağımsızdeğişkeninidedahilederek,Docker-Composeprojesinideyoksayarveyalnızcaeshoponcontainers-ServicesAndWebAppsçözümüiçinpaketlerigeriyükler.`/ignoreprojectextensions:.dcproj` `dotnet restore`</span><span class="sxs-lookup"><span data-stu-id="a84c5-250">Include the `/ignoreprojectextensions:.dcproj` argument to `dotnet restore`, so it also ignores the docker-compose project and only restores the packages for the eShopOnContainers-ServicesAndWebApps solution.</span></span>

<span data-ttu-id="a84c5-251">Son iyileştirme için, satır 23 ' ün aynı zamanda uygulama oluşturup 20 ' den sonra da bir zaman alan komutla birlikte geldiğinden emin olmak yeterlidir.</span><span class="sxs-lookup"><span data-stu-id="a84c5-251">For the final optimization, it just happens that line 20 is redundant, as line 23 also builds the application and comes, in essence, right after line 20, so there goes another time-consuming command.</span></span>

<span data-ttu-id="a84c5-252">Elde edilen dosya bundan sonra:</span><span class="sxs-lookup"><span data-stu-id="a84c5-252">The resulting file is then:</span></span>

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

### <a name="creating-your-base-image-from-scratch"></a><span data-ttu-id="a84c5-253">Sıfırdan taban görüntünüzü oluşturma</span><span class="sxs-lookup"><span data-stu-id="a84c5-253">Creating your base image from scratch</span></span>

<span data-ttu-id="a84c5-254">Sıfırdan kendi Docker temel görüntünüzü oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a84c5-254">You can create your own Docker base image from scratch.</span></span> <span data-ttu-id="a84c5-255">Bu senaryo, Docker ile başlayan birisi için önerilmez, ancak kendi temel görüntününsün belirli bitleri ayarlamak istiyorsanız bunu yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a84c5-255">This scenario is not recommended for someone who is starting with Docker, but if you want to set the specific bits of your own base image, you can do so.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="a84c5-256">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="a84c5-256">Additional resources</span></span>

- <span data-ttu-id="a84c5-257">**Çoklu mimari .NET Core görüntüleri**. </span><span class="sxs-lookup"><span data-stu-id="a84c5-257">**Multi-arch .NET Core images**.</span></span>\
  <https://github.com/dotnet/announcements/issues/14>

- <span data-ttu-id="a84c5-258">**Temel görüntü oluşturun**.</span><span class="sxs-lookup"><span data-stu-id="a84c5-258">**Create a base image**.</span></span> <span data-ttu-id="a84c5-259">Resmi Docker belgeleri. </span><span class="sxs-lookup"><span data-stu-id="a84c5-259">Official Docker documentation.</span></span>\
  <https://docs.docker.com/develop/develop-images/baseimages/>

![3-Dockerfiles 'da tanımlanan görüntüleri oluşturma](./media/image7.png)

## <a name="step-3-create-your-custom-docker-images-and-embed-your-application-or-service-in-them"></a><span data-ttu-id="a84c5-261">Adım 3.</span><span class="sxs-lookup"><span data-stu-id="a84c5-261">Step 3.</span></span> <span data-ttu-id="a84c5-262">Özel Docker görüntülerinizi oluşturun ve uygulamanızı veya hizmetinizi bunlara ekleyin</span><span class="sxs-lookup"><span data-stu-id="a84c5-262">Create your custom Docker images and embed your application or service in them</span></span>

<span data-ttu-id="a84c5-263">Uygulamanızdaki her hizmet için ilgili bir görüntü oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="a84c5-263">For each service in your application, you need to create a related image.</span></span> <span data-ttu-id="a84c5-264">Uygulamanız tek bir hizmetten veya Web uygulamasından yapılırsa yalnızca tek bir görüntüye ihtiyacınız vardır.</span><span class="sxs-lookup"><span data-stu-id="a84c5-264">If your application is made up of a single service or web application, you just need a single image.</span></span>

<span data-ttu-id="a84c5-265">Docker görüntülerinin Visual Studio 'da sizin için otomatik olarak oluşturulup oluşturulmadığını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="a84c5-265">Note that the Docker images are built automatically for you in Visual Studio.</span></span> <span data-ttu-id="a84c5-266">Aşağıdaki adımlar yalnızca Düzenleyici/CLı iş akışı için gereklidir ve altında neler olacağı hakkında netlik için açıklanır.</span><span class="sxs-lookup"><span data-stu-id="a84c5-266">The following steps are only needed for the editor/CLI workflow and explained for clarity about what happens underneath.</span></span>

<span data-ttu-id="a84c5-267">Bir geliştirici olarak, tamamlanmış bir özelliği veya kaynak denetim sisteminize (örneğin, GitHub) değişene kadar yerel olarak geliştirme ve test yapmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="a84c5-267">You, as a developer, need to develop and test locally until you push a completed feature or change to your source control system (for example, to GitHub).</span></span> <span data-ttu-id="a84c5-268">Bu, Docker görüntülerini oluşturmanız ve kapsayıcıları yerel bir Docker konağına (Windows veya Linux VM) dağıtmanız ve bu yerel kapsayıcılara karşı çalıştırmak, test etmeniz ve hata ayıklaması yapmanız gerektiği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="a84c5-268">This means that you need to create the Docker images and deploy containers to a local Docker host (Windows or Linux VM) and run, test, and debug against those local containers.</span></span>

<span data-ttu-id="a84c5-269">Docker CLı ve Dockerfile kullanarak yerel ortamınızda özel bir görüntü oluşturmak için, Şekil 5-5 ' de olduğu gibi Docker Build komutunu kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a84c5-269">To create a custom image in your local environment by using Docker CLI and your Dockerfile, you can use the docker build command, as in Figure 5-5.</span></span>

![Docker görüntüsü oluşturmak için ilerleme ekranı](./media/image8.png)

<span data-ttu-id="a84c5-271">**Şekil 5-5**.</span><span class="sxs-lookup"><span data-stu-id="a84c5-271">**Figure 5-5**.</span></span> <span data-ttu-id="a84c5-272">Özel bir Docker görüntüsü oluşturma</span><span class="sxs-lookup"><span data-stu-id="a84c5-272">Creating a custom Docker image</span></span>

<span data-ttu-id="a84c5-273">İsteğe bağlı olarak, proje klasöründen Docker derlemesini doğrudan çalıştırmak yerine, çalıştırmadan `dotnet publish`önce gerekli .NET kitaplıkları ve ikili dosyaları içeren dağıtılabilir bir klasör oluşturabilir ve sonra `docker build` komutunu kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a84c5-273">Optionally, instead of directly running docker build from the project folder, you can first generate a deployable folder with the required .NET libraries and binaries by running `dotnet publish`, and then use the `docker build` command.</span></span>

<span data-ttu-id="a84c5-274">Bu, adıyla `cesardl/netcore-webapi-microservice-docker:first`bir Docker görüntüsü oluşturur.</span><span class="sxs-lookup"><span data-stu-id="a84c5-274">This will create a Docker image with the name `cesardl/netcore-webapi-microservice-docker:first`.</span></span> <span data-ttu-id="a84c5-275">Bu durumda, ilk olarak belirli bir sürümü temsil eden bir etikettir.</span><span class="sxs-lookup"><span data-stu-id="a84c5-275">In this case, :first is a tag representing a specific version.</span></span> <span data-ttu-id="a84c5-276">Bu adımı, oluşturulan Docker uygulamanız için oluşturmanız gereken her özel görüntü için yineleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a84c5-276">You can repeat this step for each custom image you need to create for your composed Docker application.</span></span>

<span data-ttu-id="a84c5-277">Bir uygulama birden fazla kapsayıcıda yapıldığında (yani çok kapsayıcılı bir uygulamadır) ilgili Docker-Compose. yıml dosyalarında kullanıma sunulan meta verileri kullanarak tek `docker-compose up --build` bir komutla ilgili tüm görüntüleri oluşturmak için komutunu da kullanabilirsiniz. .</span><span class="sxs-lookup"><span data-stu-id="a84c5-277">When an application is made of multiple containers (that is, it is a multi-container application), you can also use the `docker-compose up --build` command to build all the related images with a single command by using the metadata exposed in the related docker-compose.yml files.</span></span>

<span data-ttu-id="a84c5-278">Şekil 5-6 ' de gösterildiği gibi Docker görüntüleri komutunu kullanarak yerel deponuzda mevcut görüntüleri bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a84c5-278">You can find the existing images in your local repository by using the docker images command, as shown in Figure 5-6.</span></span>

![Docker görüntüleri komutundan resim listesinin ekran görünümü](./media/image9.png)

<span data-ttu-id="a84c5-280">**Şekil 5-6.**</span><span class="sxs-lookup"><span data-stu-id="a84c5-280">**Figure 5-6.**</span></span> <span data-ttu-id="a84c5-281">Docker görüntüleri komutunu kullanarak mevcut görüntüleri görüntüleme</span><span class="sxs-lookup"><span data-stu-id="a84c5-281">Viewing existing images using the docker images command</span></span>

### <a name="creating-docker-images-with-visual-studio"></a><span data-ttu-id="a84c5-282">Visual Studio ile Docker görüntüleri oluşturma</span><span class="sxs-lookup"><span data-stu-id="a84c5-282">Creating Docker images with Visual Studio</span></span>

<span data-ttu-id="a84c5-283">Docker desteğiyle bir proje oluşturmak için Visual Studio kullandığınızda, açıkça bir görüntü oluşturmazsınız.</span><span class="sxs-lookup"><span data-stu-id="a84c5-283">When you use Visual Studio to create a project with Docker support, you don't explicitly create an image.</span></span> <span data-ttu-id="a84c5-284">Bunun yerine, dockerte veya hizmeti çalıştırmak için **F5** tuşuna bastığınızda (veya **CTRL + F5**), görüntü sizin için oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="a84c5-284">Instead, the image is created for you when you press **F5** (or **Ctrl-F5**) to run the dockerized application or service.</span></span> <span data-ttu-id="a84c5-285">Bu adım, Visual Studio 'da otomatiktir ve bunun gerçekleşmediğini görmezsiniz, ancak nelerin altında olduğunu bilmeniz önemlidir.</span><span class="sxs-lookup"><span data-stu-id="a84c5-285">This step is automatic in Visual Studio and you won't see it happen, but it's important that you know what's going on underneath.</span></span>

![4-(isteğe bağlı) Docker-Compose. yıml dosyasındaki hizmetleri oluşturma](./media/image10.png)

## <a name="step-4-define-your-services-in-docker-composeyml-when-building-a-multi-container-docker-application"></a><span data-ttu-id="a84c5-287">4\. adımı.</span><span class="sxs-lookup"><span data-stu-id="a84c5-287">Step 4.</span></span> <span data-ttu-id="a84c5-288">Çok kapsayıcılı bir Docker uygulaması oluştururken hizmetlerinizi Docker-Compose. yıml 'de tanımlama</span><span class="sxs-lookup"><span data-stu-id="a84c5-288">Define your services in docker-compose.yml when building a multi-container Docker application</span></span>

<span data-ttu-id="a84c5-289">[Docker-Compose. yıml](https://docs.docker.com/compose/compose-file/) dosyası, dağıtım komutlarıyla oluşturulmuş bir uygulama olarak dağıtılacak bir ilgili hizmet kümesi tanımlamanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="a84c5-289">The [docker-compose.yml](https://docs.docker.com/compose/compose-file/) file lets you define a set of related services to be deployed as a composed application with deployment commands.</span></span> <span data-ttu-id="a84c5-290">Ayrıca, bağımlılık ilişkilerini ve çalışma zamanı yapılandırmasını yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="a84c5-290">It also configures its dependency relations and run-time configuration.</span></span>

<span data-ttu-id="a84c5-291">Bir Docker-Compose. yml dosyası kullanmak için, dosyayı ana veya kök çözüm klasörünüzde aşağıdaki örnekteki gibi içerikle birlikte oluşturmanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="a84c5-291">To use a docker-compose.yml file, you need to create the file in your main or root solution folder, with content similar to that in the following example:</span></span>

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

<span data-ttu-id="a84c5-292">Bu Docker-Compose. yıml dosyası Basitleştirilmiş ve birleştirilmiş bir sürümdür.</span><span class="sxs-lookup"><span data-stu-id="a84c5-292">This docker-compose.yml file is a simplified and merged version.</span></span> <span data-ttu-id="a84c5-293">Her bir kapsayıcı için (özel görüntünün adı gibi) statik yapılandırma verilerini, her zaman gerekli olan ve bağlantı dizesi gibi dağıtım ortamına bağlı olabilecek yapılandırma bilgilerini içerir.</span><span class="sxs-lookup"><span data-stu-id="a84c5-293">It contains static configuration data for each container (like the name of the custom image), which is always required, and configuration information that might depend on the deployment environment, like the connection string.</span></span> <span data-ttu-id="a84c5-294">Sonraki bölümlerde, Docker-Compose. yıml yapılandırmasını birden çok Docker-Compose dosyasına nasıl böleyeceğinizi ve ortam ve yürütme türüne (hata ayıklama veya sürüm) göre değerleri nasıl geçersiz kılacağınızı öğreneceksiniz.</span><span class="sxs-lookup"><span data-stu-id="a84c5-294">In later sections, you will learn how to split the docker-compose.yml configuration into multiple docker-compose files and override values depending on the environment and execution type (debug or release).</span></span>

<span data-ttu-id="a84c5-295">Docker-Compose `webmvc` . yml dosyası örneği dört hizmeti tanımlar: hizmet (bir Web uygulaması), iki mikro hizmet (`ordering.api` ve `basket.api` `sql.data`) ve bir veri kaynağı kapsayıcısı, bir olarak çalışan Linux için SQL Server tabanlı kapsayıcı.</span><span class="sxs-lookup"><span data-stu-id="a84c5-295">The docker-compose.yml file example defines four services: the `webmvc` service (a web application), two microservices (`ordering.api` and `basket.api`), and one data source container, `sql.data`, based on SQL Server for Linux running as a container.</span></span> <span data-ttu-id="a84c5-296">Her hizmet bir kapsayıcı olarak dağıtılır, bu nedenle her biri için bir Docker görüntüsü gerekir.</span><span class="sxs-lookup"><span data-stu-id="a84c5-296">Each service will be deployed as a container, so a Docker image is required for each.</span></span>

<span data-ttu-id="a84c5-297">Docker-Compose. yıml dosyası yalnızca hangi kapsayıcıların kullanıldığını, ancak bunların ayrı ayrı nasıl yapılandırıldığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="a84c5-297">The docker-compose.yml file specifies not only what containers are being used, but how they are individually configured.</span></span> <span data-ttu-id="a84c5-298">Örneğin, `webmvc` . yml dosyasındaki kapsayıcı tanımı:</span><span class="sxs-lookup"><span data-stu-id="a84c5-298">For instance, the `webmvc` container definition in the .yml file:</span></span>

- <span data-ttu-id="a84c5-299">Önceden oluşturulmuş `eshop/web:latest` bir görüntü kullanır.</span><span class="sxs-lookup"><span data-stu-id="a84c5-299">Uses a pre-built `eshop/web:latest` image.</span></span> <span data-ttu-id="a84c5-300">Ancak, Docker-Compose dosyasındaki bir derlemeyi temel alan ek bir yapılandırma ile Docker-Compose yürütmesinin bir parçası olarak oluşturulacak görüntüyü de yapılandırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a84c5-300">However, you could also configure the image to be built as part of the docker-compose execution with an additional configuration based on a build: section in the docker-compose file.</span></span>

- <span data-ttu-id="a84c5-301">İki ortam değişkenini başlatır (CatalogUrl ve OrderingUrl).</span><span class="sxs-lookup"><span data-stu-id="a84c5-301">Initializes two environment variables (CatalogUrl and OrderingUrl).</span></span>

- <span data-ttu-id="a84c5-302">Kapsayıcıda açığa çıkarılan 80 numaralı bağlantı noktasını ana makinedeki 80 dış bağlantı noktasına iletir.</span><span class="sxs-lookup"><span data-stu-id="a84c5-302">Forwards the exposed port 80 on the container to the external port 80 on the host machine.</span></span>

- <span data-ttu-id="a84c5-303">Web uygulamasını Katalog ve sıralama hizmetine depends_on ayarıyla bağlar.</span><span class="sxs-lookup"><span data-stu-id="a84c5-303">Links the web app to the catalog and ordering service with the depends_on setting.</span></span> <span data-ttu-id="a84c5-304">Bu, hizmetin bu hizmetler başlatılmadan beklemesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="a84c5-304">This causes the service to wait until those services are started.</span></span>

<span data-ttu-id="a84c5-305">Mikro hizmetleri ve çok Kapsayıcılı uygulamaları nasıl uygulayacağınızı kapsadığımızda, Docker-Compose. yıml dosyasını sonraki bir bölümde geri ziyaret edeceğiz.</span><span class="sxs-lookup"><span data-stu-id="a84c5-305">We will revisit the docker-compose.yml file in a later section when we cover how to implement microservices and multi-container apps.</span></span>

### <a name="working-with-docker-composeyml-in-visual-studio-2017"></a><span data-ttu-id="a84c5-306">Visual Studio 2017 ' de Docker-Compose. yıml ile çalışma</span><span class="sxs-lookup"><span data-stu-id="a84c5-306">Working with docker-compose.yml in Visual Studio 2017</span></span>

<span data-ttu-id="a84c5-307">Daha önce bahsedildiği gibi, bir projeye Dockerfile eklemenin yanı sıra, Visual Studio 2017 (15,8 ' den itibaren) bir çözüme Docker Compose için Orchestrator desteği ekleyebilir.</span><span class="sxs-lookup"><span data-stu-id="a84c5-307">Besides adding a Dockerfile to a project, as we mentioned before, Visual Studio 2017 (from 15.8 on) can add orchestrator support for Docker Compose to a solution.</span></span>

<span data-ttu-id="a84c5-308">Şekil 5-7 ' de gösterildiği gibi, kapsayıcı Orchestrator desteğini ilk kez eklediğinizde, Visual Studio proje için dockerfile 'ı oluşturur ve çeşitli Global `docker-compose*.yml` dosyalarla çözümünüzde yeni bir (hizmet bölümü) projesi oluşturur ve ardından şunu ekler Bu dosyalara proje.</span><span class="sxs-lookup"><span data-stu-id="a84c5-308">When you add container orchestrator support, as shown in Figure 5-7, for the first time, Visual Studio creates the Dockerfile for the project and creates a new (service section) project in your solution with several global `docker-compose*.yml` files, and then adds the project to those files.</span></span> <span data-ttu-id="a84c5-309">Daha sonra Docker-Compose. yıml dosyalarını açabilir ve bunları ek özelliklerle güncelleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a84c5-309">You can then open the docker-compose.yml files and update them with additional features.</span></span>

<span data-ttu-id="a84c5-310">Bu işlemi, Docker-Compose. yıml dosyasına eklemek istediğiniz her proje için tekrarlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="a84c5-310">You have to repeat this operation form every project you want to include in the docker-compose.yml file.</span></span>

<span data-ttu-id="a84c5-311">Bu yazma sırasında, Visual Studio Docker Compose ve Service Fabric düzenleyiciler destekler.</span><span class="sxs-lookup"><span data-stu-id="a84c5-311">At the time of this writing, Visual Studio supports Docker Compose and Service Fabric orchestrators.</span></span>

![ASP.NET Core projesine Orchestrator desteği eklemek için bağlam menüsü seçeneği](./media/image21.png)

<span data-ttu-id="a84c5-313">**Şekil 5-7**.</span><span class="sxs-lookup"><span data-stu-id="a84c5-313">**Figure 5-7**.</span></span> <span data-ttu-id="a84c5-314">ASP.NET Core projesine sağ tıklayarak Visual Studio 2017 ' de Docker desteği ekleme</span><span class="sxs-lookup"><span data-stu-id="a84c5-314">Adding Docker support in Visual Studio 2017 by right-clicking an ASP.NET Core project</span></span>

<span data-ttu-id="a84c5-315">Visual Studio 'daki çözümünüze Orchestrator desteği ekledikten sonra, Şekil 5-8 ' de gösterildiği gibi eklenen Docker-Compose. yıml dosyalarını içeren `docker-compose.dcproj` Çözüm Gezgini yeni bir düğüm (proje dosyasında) görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="a84c5-315">After you add orchestrator support to your solution in Visual Studio, you will also see a new node (in the `docker-compose.dcproj` project file) in Solution Explorer that contains the added docker-compose.yml files, as shown in Figure 5-8.</span></span>

![Çözüm Gezgini Docker-oluşturma düğümü](./media/image11.png)

<span data-ttu-id="a84c5-317">**Şekil 5-8**.</span><span class="sxs-lookup"><span data-stu-id="a84c5-317">**Figure 5-8**.</span></span> <span data-ttu-id="a84c5-318">Visual Studio 2017 Çözüm Gezgini eklenen **Docker-Compose** ağacı düğümü</span><span class="sxs-lookup"><span data-stu-id="a84c5-318">The **docker-compose** tree node added in Visual Studio 2017 Solution Explorer</span></span>

<span data-ttu-id="a84c5-319">`docker-compose up` Komutunu kullanarak tek bir Docker-Compose. yıml dosyası ile çok kapsayıcılı bir uygulama dağıtabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a84c5-319">You could deploy a multi-container application with a single docker-compose.yml file by using the `docker-compose up` command.</span></span> <span data-ttu-id="a84c5-320">Ancak, Visual Studio bu grubun bir grubunu ekleyerek ortama (geliştirme veya üretim) ve yürütme türüne (yayın veya hata ayıklama) bağlı olarak değerleri geçersiz kılabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a84c5-320">However, Visual Studio adds a group of them so you can override values depending on the environment (development or production) and execution type (release or debug).</span></span> <span data-ttu-id="a84c5-321">Bu özellik sonraki bölümlerde açıklanacaktır.</span><span class="sxs-lookup"><span data-stu-id="a84c5-321">This capability will be explained in later sections.</span></span>

![5-kapsayıcıları veya oluşturulmuş uygulamayı çalıştırma](./media/image12.png)

## <a name="step-5-build-and-run-your-docker-application"></a><span data-ttu-id="a84c5-323">5\. adımı.</span><span class="sxs-lookup"><span data-stu-id="a84c5-323">Step 5.</span></span> <span data-ttu-id="a84c5-324">Docker uygulamanızı derleyin ve çalıştırın</span><span class="sxs-lookup"><span data-stu-id="a84c5-324">Build and run your Docker application</span></span>

<span data-ttu-id="a84c5-325">Uygulamanızın yalnızca tek bir kapsayıcısı varsa, bunu Docker konağına (VM veya fiziksel sunucu) dağıtarak çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a84c5-325">If your application only has a single container, you can run it by deploying it to your Docker host (VM or physical server).</span></span> <span data-ttu-id="a84c5-326">Bununla birlikte, uygulamanız birden çok hizmet içeriyorsa, tek bir CLı komutu (Docker-Compose) veya Visual Studio ile birlikte bulunan ve bu komutu kapakları altında kullanacak şekilde oluşturulan bir uygulama olarak dağıtabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a84c5-326">However, if your application contains multiple services, you can deploy it as a composed application, either using a single CLI command (docker-compose up), or with Visual Studio, which will use that command under the covers.</span></span> <span data-ttu-id="a84c5-327">Farklı seçeneklere göz atalım.</span><span class="sxs-lookup"><span data-stu-id="a84c5-327">Let's look at the different options.</span></span>

### <a name="option-a-running-a-single-container-application"></a><span data-ttu-id="a84c5-328">Seçenek A: Tek kapsayıcılı bir uygulama çalıştırma</span><span class="sxs-lookup"><span data-stu-id="a84c5-328">Option A: Running a single-container application</span></span>

#### <a name="using-docker-cli"></a><span data-ttu-id="a84c5-329">Docker CLı 'yi kullanma</span><span class="sxs-lookup"><span data-stu-id="a84c5-329">Using Docker CLI</span></span>

<span data-ttu-id="a84c5-330">Şekil 5-9 ' de gösterildiği gibi, `docker run` komutunu kullanarak bir Docker kapsayıcısı çalıştırabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="a84c5-330">You can run a Docker container using the `docker run` command, as shown in Figure 5-9:</span></span>

```console
  docker run -t -d -p 80:5000 cesardl/netcore-webapi-microservice-docker:first
```

<span data-ttu-id="a84c5-331">Yukarıdaki komut, her çalıştırılışında belirtilen görüntüden yeni bir kapsayıcı örneği oluşturur.</span><span class="sxs-lookup"><span data-stu-id="a84c5-331">The above command will create a new container instance from the specified image, every time it's run.</span></span> <span data-ttu-id="a84c5-332">Kapsayıcıya bir ad vermek `--name` için parametresini kullanabilir ve `docker start {name}` sonra var olan bir kapsayıcı örneğini çalıştırmak için (ya da kapsayıcı kimliğini veya otomatik adı kullanabilirsiniz) kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a84c5-332">You can use the `--name` parameter to give a name to the container and then use `docker start {name}` (or use the container id or automatic name) to run an existing container instance.</span></span>

![Docker Run komutunu kullanarak bir Docker kapsayıcısı çalıştırırken ekran görünümü](./media/image13.png)

<span data-ttu-id="a84c5-334">**Şekil 5-9**.</span><span class="sxs-lookup"><span data-stu-id="a84c5-334">**Figure 5-9**.</span></span> <span data-ttu-id="a84c5-335">Docker Run komutunu kullanarak Docker kapsayıcısı çalıştırma</span><span class="sxs-lookup"><span data-stu-id="a84c5-335">Running a Docker container using the docker run command</span></span>

<span data-ttu-id="a84c5-336">Bu durumda, komut kapsayıcının 5000 iç bağlantı noktasını ana makinenin 80 numaralı bağlantı noktasına bağlar.</span><span class="sxs-lookup"><span data-stu-id="a84c5-336">In this case, the command binds the internal port 5000 of the container to port 80 of the host machine.</span></span> <span data-ttu-id="a84c5-337">Bu, konağın 80 numaralı bağlantı noktasını dinlediği ve kapsayıcıda bağlantı noktası 5000 ' e ileten anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="a84c5-337">This means that the host is listening on port 80 and forwarding to port 5000 on the container.</span></span>

<span data-ttu-id="a84c5-338">Gösterilen karma kapsayıcı kimliğidir ve `--name` seçenek kullanılmazsa rastgele okunabilir bir ad atanır.</span><span class="sxs-lookup"><span data-stu-id="a84c5-338">The hash shown is the container id and it’s also assigned a random readable name if the `--name` option is not used.</span></span>

#### <a name="using-visual-studio"></a><span data-ttu-id="a84c5-339">Visual Studio 'Yu kullanma</span><span class="sxs-lookup"><span data-stu-id="a84c5-339">Using Visual Studio</span></span>

<span data-ttu-id="a84c5-340">Kapsayıcı Orchestrator desteği eklemediyseniz, Visual Studio 'da **CTRL-F5** tuşlarına basarak tek bir kapsayıcı uygulamasını da çalıştırabilirsiniz ve ayrıca **F5** 'i kullanarak kapsayıcıda uygulamada hata ayıklaması yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a84c5-340">If you haven't added container orchestrator support, you can also run a single container app in Visual Studio by pressing **Ctrl-F5** and you can also use **F5** to debug the application within the container.</span></span> <span data-ttu-id="a84c5-341">Kapsayıcı, Docker Run kullanarak yerel olarak çalışır.</span><span class="sxs-lookup"><span data-stu-id="a84c5-341">The container runs locally using docker run.</span></span>

### <a name="option-b-running-a-multi-container-application"></a><span data-ttu-id="a84c5-342">Seçenek B: Çok kapsayıcılı bir uygulama çalıştırma</span><span class="sxs-lookup"><span data-stu-id="a84c5-342">Option B: Running a multi-container application</span></span>

<span data-ttu-id="a84c5-343">Çoğu kurumsal senaryoda, bir Docker uygulaması birden çok hizmetten oluşur. Bu, Şekil 5-10 ' de gösterildiği gibi çok kapsayıcılı bir uygulama çalıştırmanız gerektiği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="a84c5-343">In most enterprise scenarios, a Docker application will be composed of multiple services, which means you need to run a multi-container application, as shown in Figure 5-10.</span></span>

![Birkaç Docker kapsayıcı içeren VM](./media/image14.png)

<span data-ttu-id="a84c5-345">**Şekil 5-10**.</span><span class="sxs-lookup"><span data-stu-id="a84c5-345">**Figure 5-10**.</span></span> <span data-ttu-id="a84c5-346">Docker Kapsayıcıları dağıtılan VM</span><span class="sxs-lookup"><span data-stu-id="a84c5-346">VM with Docker containers deployed</span></span>

#### <a name="using-docker-cli"></a><span data-ttu-id="a84c5-347">Docker CLı 'yi kullanma</span><span class="sxs-lookup"><span data-stu-id="a84c5-347">Using Docker CLI</span></span>

<span data-ttu-id="a84c5-348">Docker CLI ile çok kapsayıcılı bir uygulama çalıştırmak için `docker-compose up` komutunu kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="a84c5-348">To run a multi-container application with the Docker CLI, you use the `docker-compose up` command.</span></span> <span data-ttu-id="a84c5-349">Bu komut, çok kapsayıcılı bir uygulama dağıtmak için çözüm düzeyinde bulunan **Docker-Compose. yıml** dosyasını kullanır.</span><span class="sxs-lookup"><span data-stu-id="a84c5-349">This command uses the **docker-compose.yml** file that you have at the solution level to deploy a multi-container application.</span></span> <span data-ttu-id="a84c5-350">Şekil 5-11, Docker-Compose. yıml dosyasını içeren ana çözüm dizininizden komut çalıştırırken sonuçları gösterir.</span><span class="sxs-lookup"><span data-stu-id="a84c5-350">Figure 5-11 shows the results when running the command from your main solution directory, which contains the docker-compose.yml file.</span></span>

![Docker-Compose up komutu çalıştırılırken ekran görünümü](./media/image15.png)

<span data-ttu-id="a84c5-352">**Şekil 5-11**.</span><span class="sxs-lookup"><span data-stu-id="a84c5-352">**Figure 5-11**.</span></span> <span data-ttu-id="a84c5-353">Docker-Compose up komutunu çalıştırırken örnek sonuçlar</span><span class="sxs-lookup"><span data-stu-id="a84c5-353">Example results when running the docker-compose up command</span></span>

<span data-ttu-id="a84c5-354">Docker-Compose komutu çalıştıktan sonra, uygulama ve ilgili kapsayıcıları Şekil 5-10 ' de gösterildiği gibi Docker ana bilgisayarınıza dağıtılır.</span><span class="sxs-lookup"><span data-stu-id="a84c5-354">After the docker-compose up command runs, the application and its related containers are deployed into your Docker host, as depicted in Figure 5-10.</span></span>

#### <a name="using-visual-studio"></a><span data-ttu-id="a84c5-355">Visual Studio 'Yu kullanma</span><span class="sxs-lookup"><span data-stu-id="a84c5-355">Using Visual Studio</span></span>

<span data-ttu-id="a84c5-356">Visual Studio 2017 kullanarak çok kapsayıcılı bir uygulama çalıştırmak daha basit olamaz.</span><span class="sxs-lookup"><span data-stu-id="a84c5-356">Running a multi-container application using Visual Studio 2017 can't get any simpler.</span></span> <span data-ttu-id="a84c5-357">Hata ayıklamak için **CTRL-F5** tuşlarına **basın veya her** zamanki gibi, **Docker-Compose** projesini başlangıç projesi olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="a84c5-357">You just press **Ctrl-F5** to run or **F5** to debug, as usual, setting up the **docker-compose** project as the startup project.</span></span>  <span data-ttu-id="a84c5-358">Visual Studio tüm gerekli kurulumu işler, bu nedenle her zamanki gibi kesme noktaları oluşturabilir ve son olarak "uzak sunucular" içinde çalışan bağımsız işlemlere (tıpkı bunun gibi) hata ayıklaması yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a84c5-358">Visual Studio handles all needed setup, so you can create breakpoints as usual and debug what finally become independent processes running in "remote servers", just like that.</span></span>

<span data-ttu-id="a84c5-359">Daha önce bahsedildiği gibi, bir çözüm içindeki bir projeye Docker çözüm desteği eklediğinizde, bu proje genel (çözüm düzeyi) Docker-Compose. yıml dosyasında yapılandırılmıştır ve bu, tüm çözümü tek seferde çalıştırmanıza veya hata ayıklamanıza olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="a84c5-359">As mentioned before, each time you add Docker solution support to a project within a solution, that project is configured in the global (solution-level) docker-compose.yml file, which lets you run or debug the whole solution at once.</span></span> <span data-ttu-id="a84c5-360">Visual Studio, Docker çözüm desteğinin etkinleştirildiği her proje için bir kapsayıcı başlatır ve tüm iç adımları (dotnet publish, Docker Build, vb.) gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="a84c5-360">Visual Studio will start one container for each project that has Docker solution support enabled, and perform all the internal steps for you (dotnet publish, docker build, etc.).</span></span>

<span data-ttu-id="a84c5-361">Tüm drudgery göz atmak istiyorsanız, dosyaya göz atın:</span><span class="sxs-lookup"><span data-stu-id="a84c5-361">If you want to take a peek at all the drudgery, take a look at the file:</span></span>

`{root solution folder}\obj\Docker\docker-compose.vs.debug.g.yml`

<span data-ttu-id="a84c5-362">Buradaki önemli nokta, Şekil 5-12 ' de gösterildiği gibi, Visual Studio 2017 ' de gösterildiği gibi, F5 tuşu eylemi için ek bir **Docker** komutu vardır.</span><span class="sxs-lookup"><span data-stu-id="a84c5-362">The important point here is that, as shown in Figure 5-12, in Visual Studio 2017 there is an additional **Docker** command for the F5 key action.</span></span> <span data-ttu-id="a84c5-363">Bu seçenek, çözüm düzeyindeki Docker-Compose. yıml dosyalarında tanımlanan tüm kapsayıcıları çalıştırarak çok kapsayıcılı bir uygulamayı çalıştırmanızı veya hata ayıklamanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="a84c5-363">This option lets you run or debug a multi-container application by running all the containers that are defined in the docker-compose.yml files at the solution level.</span></span> <span data-ttu-id="a84c5-364">Birden çok Kapsayıcılı çözüm için hata ayıklama özelliği, çeşitli kesme noktaları, farklı bir projede (kapsayıcı) ve Visual Studio 'dan hata ayıklama yaparken, farklı projelerde tanımlanan kesme noktalarında durulacağınız ve üzerinde çalışırken durdurulacak anlamına gelir. farklı kapsayıcılar.</span><span class="sxs-lookup"><span data-stu-id="a84c5-364">The ability to debug multiple-container solutions means that you can set several breakpoints, each breakpoint in a different project (container), and while debugging from Visual Studio you will stop at breakpoints defined in different projects and running on different containers.</span></span>

![Docker-Compose projesi çalıştıran Visual Studio hata ayıklama araç çubuğu](./media/image16.png)

<span data-ttu-id="a84c5-366">**Şekil 5-12**.</span><span class="sxs-lookup"><span data-stu-id="a84c5-366">**Figure 5-12**.</span></span> <span data-ttu-id="a84c5-367">Visual Studio 2017 'de çok Kapsayıcılı uygulamalar çalıştırma</span><span class="sxs-lookup"><span data-stu-id="a84c5-367">Running multi-container apps in Visual Studio 2017</span></span>

### <a name="additional-resources"></a><span data-ttu-id="a84c5-368">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="a84c5-368">Additional resources</span></span>

- <span data-ttu-id="a84c5-369">**ASP.NET kapsayıcısını uzak bir Docker konağına dağıtma** </span><span class="sxs-lookup"><span data-stu-id="a84c5-369">**Deploy an ASP.NET container to a remote Docker host** </span></span>\
  <https://docs.microsoft.com/azure/vs-azure-tools-docker-hosting-web-apps-in-docker>

### <a name="a-note-about-testing-and-deploying-with-orchestrators"></a><span data-ttu-id="a84c5-370">Düzenleyiciler ile test ve dağıtma hakkında bir bilgi</span><span class="sxs-lookup"><span data-stu-id="a84c5-370">A note about testing and deploying with orchestrators</span></span>

<span data-ttu-id="a84c5-371">Docker-Compose ve Docker çalıştırma komutları (ya da Visual Studio 'da kapsayıcıları çalıştırmak ve hata ayıklamak) geliştirme ortamınızda kapsayıcıları test etmek için yeterlidir.</span><span class="sxs-lookup"><span data-stu-id="a84c5-371">The docker-compose up and docker run commands (or running and debugging the containers in Visual Studio) are adequate for testing containers in your development environment.</span></span> <span data-ttu-id="a84c5-372">Ancak, [Kubernetes](https://kubernetes.io/) veya [Service Fabric](https://azure.microsoft.com/services/service-fabric/)gibi düzenleyicilerinin hedeflemesini yapmanız gereken üretim dağıtımları için bu yaklaşımı kullanmamalısınız.</span><span class="sxs-lookup"><span data-stu-id="a84c5-372">But you should not use this approach for production deployments, where you should target orchestrators like [Kubernetes](https://kubernetes.io/) or [Service Fabric](https://azure.microsoft.com/services/service-fabric/).</span></span> <span data-ttu-id="a84c5-373">Kubernetes kullanıyorsanız, kapsayıcıları ve [Hizmetleri](https://kubernetes.io/docs/concepts/services-networking/service/) ağa göre düzenlemek için [Pod](https://kubernetes.io/docs/concepts/workloads/pods/pod/) 'yi kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="a84c5-373">If you're using Kubernetes you have to use [pods](https://kubernetes.io/docs/concepts/workloads/pods/pod/) to organize containers and [services](https://kubernetes.io/docs/concepts/services-networking/service/) to network them.</span></span> <span data-ttu-id="a84c5-374">Ayrıca, Pod oluşturma ve değişiklik düzenlemek için [dağıtımları](https://kubernetes.io/docs/concepts/workloads/controllers/deployment/) da kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a84c5-374">You also use [deployments](https://kubernetes.io/docs/concepts/workloads/controllers/deployment/) to organize pod creation and modification.</span></span>

![6-uygulamanızı veya mikro hizmetlerinizi test edin](./media/image17.png)

## <a name="step-6-test-your-docker-application-using-your-local-docker-host"></a><span data-ttu-id="a84c5-376">6\. adım.</span><span class="sxs-lookup"><span data-stu-id="a84c5-376">Step 6.</span></span> <span data-ttu-id="a84c5-377">Yerel Docker konağını kullanarak Docker uygulamanızı test etme</span><span class="sxs-lookup"><span data-stu-id="a84c5-377">Test your Docker application using your local Docker host</span></span>

<span data-ttu-id="a84c5-378">Bu adım, uygulamanızın yaptığı işe göre farklılık gösterir.</span><span class="sxs-lookup"><span data-stu-id="a84c5-378">This step will vary depending on what your application is doing.</span></span> <span data-ttu-id="a84c5-379">Tek bir kapsayıcı veya hizmet olarak dağıtılan basit bir .NET Core Web uygulamasında, Şekil 5-13 ' de gösterildiği gibi, Docker ana bilgisayarında bir tarayıcı açarak ve bu siteye giderek hizmete erişebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a84c5-379">In a simple .NET Core Web application that is deployed as a single container or service, you can access the service by opening a browser on the Docker host and navigating to that site, as shown in Figure 5-13.</span></span> <span data-ttu-id="a84c5-380">(Dockerfile içindeki yapılandırma kapsayıcıyı 80 dışında bir şey olan konaktaki bir bağlantı noktasıyla eşleiyorsa, URL 'ye ana bilgisayar bağlantı noktasını ekleyin.)</span><span class="sxs-lookup"><span data-stu-id="a84c5-380">(If the configuration in the Dockerfile maps the container to a port on the host that is anything other than 80, include the host port in the URL.)</span></span>

![API uç noktası yanıtının tarayıcı görünümü](./media/image18.png)

<span data-ttu-id="a84c5-382">**Şekil 5-13**.</span><span class="sxs-lookup"><span data-stu-id="a84c5-382">**Figure 5-13**.</span></span> <span data-ttu-id="a84c5-383">Docker uygulamanızı localhost kullanarak yerel olarak test etme örneği</span><span class="sxs-lookup"><span data-stu-id="a84c5-383">Example of testing your Docker application locally using localhost</span></span>

<span data-ttu-id="a84c5-384">Localhost, Docker ana bilgisayar IP 'sini işaret etmiyor (varsayılan olarak, Docker CE kullanırken), hizmetinize gitmek için makinenizin ağ kartının IP adresini kullanın.</span><span class="sxs-lookup"><span data-stu-id="a84c5-384">If localhost is not pointing to the Docker host IP (by default, when using Docker CE, it should), to navigate to your service, use the IP address of your machine's network card.</span></span>

<span data-ttu-id="a84c5-385">Tarayıcıdaki bu URL 'nin incelenen belirli kapsayıcı örneği için 80 bağlantı noktasını kullandığını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="a84c5-385">Note that this URL in the browser uses port 80 for the particular container example being discussed.</span></span> <span data-ttu-id="a84c5-386">Ancak, dahili olarak istekler 5000 numaralı bağlantı noktasına yönlendirilmekte, çünkü bu, önceki adımda açıklandığı gibi Docker Run komutuyla dağıtılmıştı.</span><span class="sxs-lookup"><span data-stu-id="a84c5-386">However, internally the requests are being redirected to port 5000, because that was how it was deployed with the docker run command, as explained in a previous step.</span></span>

<span data-ttu-id="a84c5-387">Ayrıca Şekil 5-14 ' de gösterildiği gibi, terminalden kıvrımlı kullanarak uygulamayı test edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a84c5-387">You can also test the application using curl from the terminal, as shown in Figure 5-14.</span></span> <span data-ttu-id="a84c5-388">Windows 'daki bir Docker yüklemesinde, makinenizin gerçek IP adresine ek olarak varsayılan Docker ana bilgisayar IP 'si her zaman 10.0.75.1.</span><span class="sxs-lookup"><span data-stu-id="a84c5-388">In a Docker installation on Windows, the default Docker Host IP is always 10.0.75.1 in addition to your machine's actual IP address.</span></span>

![Kıvrımlı bir API uç noktası yanıtının ekran görünümü](./media/image19.png)

<span data-ttu-id="a84c5-390">**Şekil 5-14**.</span><span class="sxs-lookup"><span data-stu-id="a84c5-390">**Figure 5-14**.</span></span> <span data-ttu-id="a84c5-391">Docker uygulamanızı kıvrımlı kullanarak yerel olarak test etme örneği</span><span class="sxs-lookup"><span data-stu-id="a84c5-391">Example of testing your Docker application locally using curl</span></span>

### <a name="testing-and-debugging-containers-with-visual-studio-2017"></a><span data-ttu-id="a84c5-392">Visual Studio 2017 ile kapsayıcıları test etme ve hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="a84c5-392">Testing and debugging containers with Visual Studio 2017</span></span>

<span data-ttu-id="a84c5-393">Visual Studio 2017 ile kapsayıcıları çalıştırırken ve hata ayıklarken, kapsayıcılar olmadan çalıştırırken kullandığınız şekilde .NET uygulamasında hata ayıklaması yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a84c5-393">When running and debugging the containers with Visual Studio 2017, you can debug the .NET application in much the same way as you would when running without containers.</span></span>

### <a name="testing-and-debugging-without-visual-studio"></a><span data-ttu-id="a84c5-394">Visual Studio olmadan test etme ve hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="a84c5-394">Testing and debugging without Visual Studio</span></span>

<span data-ttu-id="a84c5-395">Düzenleyici/CLı yaklaşımını kullanarak geliştiriyorsanız, hata ayıklama kapsayıcıları daha zordur ve izleme oluşturarak hata ayıklama yapmak isteyeceksiniz.</span><span class="sxs-lookup"><span data-stu-id="a84c5-395">If you're developing using the editor/CLI approach, debugging containers is more difficult and you will want to debug by generating traces.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="a84c5-396">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="a84c5-396">Additional resources</span></span>

- <span data-ttu-id="a84c5-397">**Yerel bir Docker kapsayıcısında uygulamalarda hata ayıklama** </span><span class="sxs-lookup"><span data-stu-id="a84c5-397">**Debugging apps in a local Docker container** </span></span>\
  [https://docs.microsoft.com/visualstudio/containers/edit-and-refresh](/visualstudio/containers/edit-and-refresh)

- <span data-ttu-id="a84c5-398">**Steve Lasker. Docker ile ASP.NET Core uygulamalar oluşturun, hata ayıklayın, dağıtın.**</span><span class="sxs-lookup"><span data-stu-id="a84c5-398">**Steve Lasker. Build, Debug, Deploy ASP.NET Core Apps with Docker.**</span></span> <span data-ttu-id="a84c5-399">Video.</span><span class="sxs-lookup"><span data-stu-id="a84c5-399">Video.</span></span> \
  <https://channel9.msdn.com/Events/Visual-Studio/Visual-Studio-2017-Launch/T115>

## <a name="simplified-workflow-when-developing-containers-with-visual-studio"></a><span data-ttu-id="a84c5-400">Visual Studio ile kapsayıcılar geliştirirken Basitleştirilmiş iş akışı</span><span class="sxs-lookup"><span data-stu-id="a84c5-400">Simplified workflow when developing containers with Visual Studio</span></span>

<span data-ttu-id="a84c5-401">Etkin olarak, Visual Studio 'Yu kullanırken iş akışı, düzenleyici/CLı yaklaşımını kullanmaktan daha basittir.</span><span class="sxs-lookup"><span data-stu-id="a84c5-401">Effectively, the workflow when using Visual Studio is a lot simpler than if you use the editor/CLI approach.</span></span> <span data-ttu-id="a84c5-402">Docker ve Docker-Compose. yıml dosyalarıyla ilgili Docker için gereken adımların çoğu Şekil 5-15 ' de gösterildiği gibi Visual Studio tarafından gizlenir veya basitleştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="a84c5-402">Most of the steps required by Docker related to the Dockerfile and docker-compose.yml files are hidden or simplified by Visual Studio, as shown in Figure 5-15.</span></span>

![Visual Studio ile basitleştirilmiş kapsayıcı geliştirme iş akışı: 1-uygulamanızı kodlayın, 2-projelere Docker desteği ekleyin (tek bir kez), 3-çalıştırma kapsayıcısı veya Docker-Compose uygulaması, 4-uygulamanızı veya mikro hizmetlerinizi, 5-depoyu depoya gönderin ve tekrarlayın.](./media/image20.png)

<span data-ttu-id="a84c5-404">**Şekil 5-15**.</span><span class="sxs-lookup"><span data-stu-id="a84c5-404">**Figure 5-15**.</span></span> <span data-ttu-id="a84c5-405">Visual Studio ile geliştirme yaparken Basitleştirilmiş iş akışı</span><span class="sxs-lookup"><span data-stu-id="a84c5-405">Simplified workflow when developing with Visual Studio</span></span>

<span data-ttu-id="a84c5-406">Ayrıca, adım 2 ' yi (projelerinize Docker desteği ekleme) yalnızca bir kez gerçekleştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="a84c5-406">In addition, you need to perform step 2 (adding Docker support to your projects) just once.</span></span> <span data-ttu-id="a84c5-407">Bu nedenle, iş akışı herhangi bir geliştirme için .NET kullanırken normal geliştirme görevlerinizde benzerdir.</span><span class="sxs-lookup"><span data-stu-id="a84c5-407">Therefore, the workflow is similar to your usual development tasks when using .NET for any other development.</span></span> <span data-ttu-id="a84c5-408">Kapakların (görüntü oluşturma işlemi, kullandığınız temel görüntüler, kapsayıcıların dağıtımı vb.) altında neler olduğunu bilmeniz gerekir ve bazı durumlarda, davranışları özelleştirmek için Dockerfile veya Docker-Compose. yıml dosyasını düzenlemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="a84c5-408">You need to know what is going on under the covers (the image build process, what base images you're using, deployment of containers, etc.) and sometimes you will also need to edit the Dockerfile or docker-compose.yml file to customize behaviors.</span></span> <span data-ttu-id="a84c5-409">Ancak işin çoğu Visual Studio kullanarak büyük ölçüde basitleştirilerek çok daha üretken hale getirirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a84c5-409">But most of the work is greatly simplified by using Visual Studio, making you a lot more productive.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="a84c5-410">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="a84c5-410">Additional resources</span></span>

- <span data-ttu-id="a84c5-411">**Steve Lasker. Visual Studio 2017 ile .NET Docker geliştirme** </span><span class="sxs-lookup"><span data-stu-id="a84c5-411">**Steve Lasker. .NET Docker Development with Visual Studio 2017** </span></span>\
  <https://channel9.msdn.com/Events/Visual-Studio/Visual-Studio-2017-Launch/T111>

## <a name="using-powershell-commands-in-a-dockerfile-to-set-up-windows-containers"></a><span data-ttu-id="a84c5-412">Windows kapsayıcıları ayarlamak için bir Dockerfile içinde PowerShell komutlarını kullanma</span><span class="sxs-lookup"><span data-stu-id="a84c5-412">Using PowerShell commands in a Dockerfile to set up Windows Containers</span></span>

<span data-ttu-id="a84c5-413">[Windows kapsayıcıları](https://docs.microsoft.com/virtualization/windowscontainers/about/index) , mevcut Windows uygulamalarınızı Docker görüntülerine dönüştürmenize ve bunları Docker ekosisteminin geri kalanıyla aynı araçlarla dağıtmanıza imkan tanır.</span><span class="sxs-lookup"><span data-stu-id="a84c5-413">[Windows Containers](https://docs.microsoft.com/virtualization/windowscontainers/about/index) allow you to convert your existing Windows applications into Docker images and deploy them with the same tools as the rest of the Docker ecosystem.</span></span> <span data-ttu-id="a84c5-414">Windows kapsayıcılarını kullanmak için aşağıdaki örnekte gösterildiği gibi, Dockerfile içinde PowerShell komutlarını çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="a84c5-414">To use Windows Containers, you run PowerShell commands in the Dockerfile, as shown in the following example:</span></span>

```Dockerfile
FROM microsoft/windowsservercore
LABEL Description="IIS" Vendor="Microsoft" Version="10"
RUN powershell -Command Add-WindowsFeature Web-Server
CMD [ "ping", "localhost", "-t" ]
```

<span data-ttu-id="a84c5-415">Bu durumda, bir Windows Server çekirdek temel görüntüsü (başlangıç ayarı) kullanıyorsunuz ve IIS 'yi bir PowerShell komutuyla (çalıştırma ayarı) kullanıyoruz.</span><span class="sxs-lookup"><span data-stu-id="a84c5-415">In this case, we are using a Windows Server Core base image (the FROM setting) and installing IIS with a PowerShell command (the RUN setting).</span></span> <span data-ttu-id="a84c5-416">Benzer bir şekilde, ASP.NET 4. x, .NET 4,6 veya başka herhangi bir Windows yazılımı gibi ek bileşenler ayarlamak için de PowerShell komutlarını kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a84c5-416">In a similar way, you could also use PowerShell commands to set up additional components like ASP.NET 4.x, .NET 4.6, or any other Windows software.</span></span> <span data-ttu-id="a84c5-417">Örneğin, bir Dockerfile dosyasında aşağıdaki komut ASP.NET 4,5 ' u ayarlar:</span><span class="sxs-lookup"><span data-stu-id="a84c5-417">For example, the following command in a Dockerfile sets up ASP.NET 4.5:</span></span>

```Dockerfile
RUN powershell add-windowsfeature web-asp-net45
```

### <a name="additional-resources"></a><span data-ttu-id="a84c5-418">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="a84c5-418">Additional resources</span></span>

- <span data-ttu-id="a84c5-419">**aspnet-docker/Dockerfile.**</span><span class="sxs-lookup"><span data-stu-id="a84c5-419">**aspnet-docker/Dockerfile.**</span></span> <span data-ttu-id="a84c5-420">Windows özelliklerini dahil etmek için dockerfile 'ları destekliyor 'tan çalıştırılacak örnek PowerShell komutları. </span><span class="sxs-lookup"><span data-stu-id="a84c5-420">Example PowerShell commands to run from dockerfiles to include Windows features.</span></span>\
  <https://github.com/Microsoft/aspnet-docker/blob/master/4.7.1-windowsservercore-ltsc2016/runtime/Dockerfile>

>[!div class="step-by-step"]
><span data-ttu-id="a84c5-421">[Önceki](index.md)İleri
>[](../multi-container-microservice-net-applications/index.md)</span><span class="sxs-lookup"><span data-stu-id="a84c5-421">[Previous](index.md)
[Next](../multi-container-microservice-net-applications/index.md)</span></span>
