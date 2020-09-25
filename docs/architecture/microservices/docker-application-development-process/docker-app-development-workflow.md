---
title: Docker uygulamaları için geliştirme iş akışı
description: Docker tabanlı uygulamalar geliştirmeye yönelik iş akışının ayrıntılarını anlayın. Adım adım ilerleyin ve Dockerfiles 'ı iyileştirmek ve Visual Studio 'Yu kullanırken kullanılabilecek Basitleştirilmiş iş akışıyla sona erdirmek için bazı ayrıntılara ulaşın.
ms.date: 01/30/2020
ms.openlocfilehash: 04b59a6c30b4fb8f34fe1d0e5cd5328ac77ecb4e
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91172560"
---
# <a name="development-workflow-for-docker-apps"></a><span data-ttu-id="705e9-104">Docker uygulamaları için geliştirme iş akışı</span><span class="sxs-lookup"><span data-stu-id="705e9-104">Development workflow for Docker apps</span></span>

<span data-ttu-id="705e9-105">Uygulama geliştirme yaşam döngüsü, bilgisayarınızda tercih ettiğiniz dili kullanarak kodlarınızla ve yerel olarak test ettiğiniz bir geliştirici olarak bilgisayarınızda başlatılır.</span><span class="sxs-lookup"><span data-stu-id="705e9-105">The application development life cycle starts at your computer, as a developer, where you code the application using your preferred language and test it locally.</span></span> <span data-ttu-id="705e9-106">Seçtiğiniz dil, çerçeve ve platforma bakılmaksızın, bu iş akışı ile Docker kapsayıcılarını her zaman geliştirip test edersiniz, ancak bunu yerel olarak yapmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="705e9-106">With this workflow, no matter which language, framework, and platform you choose, you're always developing and testing Docker containers, but doing so locally.</span></span>

<span data-ttu-id="705e9-107">Her kapsayıcı (bir Docker görüntüsünün örneği) aşağıdaki bileşenleri içerir:</span><span class="sxs-lookup"><span data-stu-id="705e9-107">Each container (an instance of a Docker image) includes the following components:</span></span>

- <span data-ttu-id="705e9-108">Bir işletim sistemi seçimi, örneğin bir Linux dağıtımı, Windows nano sunucu veya Windows Server Core.</span><span class="sxs-lookup"><span data-stu-id="705e9-108">An operating system selection, for example, a Linux distribution, Windows Nano Server, or Windows Server Core.</span></span>

- <span data-ttu-id="705e9-109">Geliştirme sırasında eklenen dosyalar, örneğin, kaynak kodu ve uygulama ikilileri.</span><span class="sxs-lookup"><span data-stu-id="705e9-109">Files added during development, for example, source code and application binaries.</span></span>

- <span data-ttu-id="705e9-110">Ortam ayarları ve bağımlılıklar gibi yapılandırma bilgileri.</span><span class="sxs-lookup"><span data-stu-id="705e9-110">Configuration information, such as environment settings and dependencies.</span></span>

## <a name="workflow-for-developing-docker-container-based-applications"></a><span data-ttu-id="705e9-111">Docker kapsayıcı tabanlı uygulamalar geliştirmek için iş akışı</span><span class="sxs-lookup"><span data-stu-id="705e9-111">Workflow for developing Docker container-based applications</span></span>

<span data-ttu-id="705e9-112">Bu bölüm, Docker kapsayıcı tabanlı uygulamalar için *iç döngü* geliştirme iş akışını açıklar.</span><span class="sxs-lookup"><span data-stu-id="705e9-112">This section describes the *inner-loop* development workflow for Docker container-based applications.</span></span> <span data-ttu-id="705e9-113">İç döngü iş akışı, üretim dağıtımına dahil olabilen daha geniş DevOps iş akışını düşünülmediği anlamına gelir ve yalnızca geliştiricinin bilgisayarında yapılan geliştirme işlerine odaklanır.</span><span class="sxs-lookup"><span data-stu-id="705e9-113">The inner-loop workflow means it's not considering the broader DevOps workflow, which can include up to production deployment, and just focuses on the development work done on the developer's computer.</span></span> <span data-ttu-id="705e9-114">Bu adımlar yalnızca bir kez yapıldığından, ortamı ayarlamaya yönelik ilk adımlar dahil değildir.</span><span class="sxs-lookup"><span data-stu-id="705e9-114">The initial steps to set up the environment aren't included, since those steps are done only once.</span></span>

<span data-ttu-id="705e9-115">Bir uygulama, kendi hizmetlerinizin yanı sıra ek kitaplıklarınızdan oluşur (bağımlılıklar).</span><span class="sxs-lookup"><span data-stu-id="705e9-115">An application is composed of your own services plus additional libraries (dependencies).</span></span> <span data-ttu-id="705e9-116">Şekil 5-1 ' de gösterildiği gibi, bir Docker uygulaması oluştururken genellikle gereken temel adımlar aşağıda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="705e9-116">The following are the basic steps you usually take when building a Docker application, as illustrated in Figure 5-1.</span></span>

:::image type="complex" source="./media/docker-app-development-workflow/life-cycle-containerized-apps-docker-cli.png" alt-text="Kapsayıcılı bir uygulama oluşturmak için gereken 7 adımı gösteren diyagram.":::
<span data-ttu-id="705e9-118">Docker uygulamaları için geliştirme süreci: 1-uygulamanızı kodlayın, 2-Dockerfile/s, 3-Dockerfile/s 'de tanımlanan görüntüleri oluşturun, 4-(isteğe bağlı) oluşturma hizmetleri Docker-Compose. yıml dosyasında, 5-çalıştırma kapsayıcısı veya Docker-Compose uygulaması, 6-uygulamanızı veya mikro hizmetleri, 7-depoyu depoya gönderin ve tekrarlayın.</span><span class="sxs-lookup"><span data-stu-id="705e9-118">The development process for Docker apps: 1 - Code your App, 2 - Write Dockerfile/s, 3 - Create images defined at Dockerfile/s, 4 - (optional) Compose services in the docker-compose.yml file, 5 - Run container or docker-compose app, 6 - Test your app or microservices, 7 - Push to repo and repeat.</span></span>
:::image-end:::

<span data-ttu-id="705e9-119">**Şekil 5-1.**</span><span class="sxs-lookup"><span data-stu-id="705e9-119">**Figure 5-1.**</span></span> <span data-ttu-id="705e9-120">Docker Kapsayıcılı uygulamalar geliştirmek için adım adım iş akışı</span><span class="sxs-lookup"><span data-stu-id="705e9-120">Step-by-step workflow for developing Docker containerized apps</span></span>

<span data-ttu-id="705e9-121">Bu bölümde, bu tüm süreç ayrıntılıdır ve her ana adım bir Visual Studio ortamına odaklanarak açıklanmıştır.</span><span class="sxs-lookup"><span data-stu-id="705e9-121">In this section, this whole process is detailed and every major step is explained by focusing on a Visual Studio environment.</span></span>

<span data-ttu-id="705e9-122">Bir düzenleyici/CLı geliştirme yaklaşımı kullandığınızda (örneğin Visual Studio Code, macOS veya Windows üzerinde Docker CLı), Visual Studio 'Yu kullanmaktan daha ayrıntılı olarak, her adımı bilmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="705e9-122">When you're using an editor/CLI development approach (for example, Visual Studio Code plus Docker CLI on macOS or Windows), you need to know every step, generally in more detail than if you're using Visual Studio.</span></span> <span data-ttu-id="705e9-123">CLı ortamında çalışma hakkında daha fazla bilgi için bkz. [Microsoft platformları ve araçları ile e-kitap Kapsayıcılı Docker uygulaması yaşam döngüsü](https://aka.ms/dockerlifecycleebook/).</span><span class="sxs-lookup"><span data-stu-id="705e9-123">For more information about working in a CLI environment, see the e-book [Containerized Docker Application lifecycle with Microsoft Platforms and Tools](https://aka.ms/dockerlifecycleebook/).</span></span>

<span data-ttu-id="705e9-124">Visual Studio 2019 kullanırken, bu adımların birçoğu sizin için işlenir ve bu da üretkenliğinizi önemli ölçüde geliştirir.</span><span class="sxs-lookup"><span data-stu-id="705e9-124">When you're using Visual Studio 2019, many of those steps are handled for you, which dramatically improves your productivity.</span></span> <span data-ttu-id="705e9-125">Visual Studio 2019 kullanırken ve çok Kapsayıcılı uygulamaları hedeflerken bu durum özellikle doğrudur.</span><span class="sxs-lookup"><span data-stu-id="705e9-125">This is especially true when you're using Visual Studio 2019 and targeting multi-container applications.</span></span> <span data-ttu-id="705e9-126">Örneğin, yalnızca bir fare tıklaması ile Visual Studio, `Dockerfile` `docker-compose.yml` uygulamanıza yönelik yapılandırmayla ve dosyalarını projenize ekler.</span><span class="sxs-lookup"><span data-stu-id="705e9-126">For instance, with just one mouse click, Visual Studio adds the `Dockerfile` and `docker-compose.yml` file to your projects with the configuration for your application.</span></span> <span data-ttu-id="705e9-127">Uygulamayı Visual Studio 'da çalıştırdığınızda, Docker görüntüsünü oluşturur ve çok Kapsayıcılı uygulamayı doğrudan Docker içinde çalıştırır; aynı zamanda birkaç kapsayıcıda hata ayıklamanıza da olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="705e9-127">When you run the application in Visual Studio, it builds the Docker image and runs the multi-container application directly in Docker; it even allows you to debug several containers at once.</span></span> <span data-ttu-id="705e9-128">Bu özellikler, geliştirme hızınızı artırır.</span><span class="sxs-lookup"><span data-stu-id="705e9-128">These features will boost your development speed.</span></span>

<span data-ttu-id="705e9-129">Ancak, yalnızca Visual Studio bu adımları otomatik hale getiren için Docker ile neler olduğunu bilmeniz gerekmez.</span><span class="sxs-lookup"><span data-stu-id="705e9-129">However, just because Visual Studio makes those steps automatic doesn't mean that you don't need to know what's going on underneath with Docker.</span></span> <span data-ttu-id="705e9-130">Bu nedenle, aşağıdaki kılavuz her adımda ayrıntılardır.</span><span class="sxs-lookup"><span data-stu-id="705e9-130">Therefore, the following guidance details every step.</span></span>

![1. adım için görüntü.](./media/docker-app-development-workflow/step-1-code-your-app.png)

## <a name="step-1-start-coding-and-create-your-initial-application-or-service-baseline"></a><span data-ttu-id="705e9-132">Adım 1.</span><span class="sxs-lookup"><span data-stu-id="705e9-132">Step 1.</span></span> <span data-ttu-id="705e9-133">Kodlamaya başlayın ve başlangıç uygulamanızı veya hizmet temelinizi oluşturun</span><span class="sxs-lookup"><span data-stu-id="705e9-133">Start coding and create your initial application or service baseline</span></span>

<span data-ttu-id="705e9-134">Docker uygulaması geliştirmek, Docker olmadan uygulama geliştirme yöntemine benzer.</span><span class="sxs-lookup"><span data-stu-id="705e9-134">Developing a Docker application is similar to the way you develop an application without Docker.</span></span> <span data-ttu-id="705e9-135">Bu fark, Docker için geliştirme yaparken, yerel ortamınızdaki Docker Kapsayıcıları içinde çalışan uygulamanızı veya hizmetlerinizi (Windows kapsayıcıları kullanılıyorsa Docker veya doğrudan Windows) bir Linux VM kurulumu) dağıtmakta ve test eteceğiz.</span><span class="sxs-lookup"><span data-stu-id="705e9-135">The difference is that while developing for Docker, you're deploying and testing your application or services running within Docker containers in your local environment (either a Linux VM setup by Docker or directly Windows if using Windows Containers).</span></span>

### <a name="set-up-your-local-environment-with-visual-studio"></a><span data-ttu-id="705e9-136">Visual Studio ile yerel ortamınızı ayarlama</span><span class="sxs-lookup"><span data-stu-id="705e9-136">Set up your local environment with Visual Studio</span></span>

<span data-ttu-id="705e9-137">Başlamak için, aşağıdaki yönergelerde açıklandığı gibi Windows için [Docker Community Edition 'ın (CE)](https://docs.docker.com/docker-for-windows/) yüklü olduğundan emin olun:</span><span class="sxs-lookup"><span data-stu-id="705e9-137">To begin, make sure you have [Docker Community Edition (CE)](https://docs.docker.com/docker-for-windows/) for Windows installed, as explained in the following instructions:</span></span>

[<span data-ttu-id="705e9-138">Docker CE for Windows kullanmaya başlayın</span><span class="sxs-lookup"><span data-stu-id="705e9-138">Get started with Docker CE for Windows</span></span>](https://docs.docker.com/docker-for-windows/)

<span data-ttu-id="705e9-139">Ayrıca, Şekil 5-2 ' de gösterildiği gibi, **.NET Core platformlar arası geliştirme** iş yükü yüklüyken Visual Studio 2019 sürüm 16,4 veya üzeri bir sürüme ihtiyacınız vardır.</span><span class="sxs-lookup"><span data-stu-id="705e9-139">In addition, you need Visual Studio 2019 version 16.4 or later, with the **.NET Core cross-platform development** workload installed, as shown in Figure 5-2.</span></span>

![.NET Core platformlar arası geliştirme seçiminin ekran görüntüsü.](./media/docker-app-development-workflow/dotnet-core-cross-platform-development.png)

<span data-ttu-id="705e9-141">**Şekil 5-2**.</span><span class="sxs-lookup"><span data-stu-id="705e9-141">**Figure 5-2**.</span></span> <span data-ttu-id="705e9-142">Visual Studio 2019 kurulumu sırasında **.NET Core platformlar arası geliştirme** iş yükünü seçme</span><span class="sxs-lookup"><span data-stu-id="705e9-142">Selecting the **.NET Core cross-platform development** workload during Visual Studio 2019 setup</span></span>

<span data-ttu-id="705e9-143">Uygulamanızda Docker 'ı etkinleştirmeden ve Docker 'da dağıtıp test etmeden önce bile, uygulamanızı basit .NET (genellikle .NET Core 'da) kodlamaya başlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="705e9-143">You can start coding your application in plain .NET (usually in .NET Core if you're planning to use containers) even before enabling Docker in your application and deploying and testing in Docker.</span></span> <span data-ttu-id="705e9-144">Ancak, gerçek ortam olacağı ve herhangi bir sorun mümkün olan en kısa sürede keşfedilebilir olduğundan, Docker üzerinde en kısa sürede çalışmaya başlamanız önerilir.</span><span class="sxs-lookup"><span data-stu-id="705e9-144">However, it is recommended that you start working on Docker as soon as possible, because that will be the real environment and any issues can be discovered as soon as possible.</span></span> <span data-ttu-id="705e9-145">Visual Studio, Visual Studio 'daki çok Kapsayıcılı uygulamalarda hata ayıklarken en iyi örnek olan Docker ile neredeyse oldukça kolay bir şekilde çalışmasını sağlayan bu, önerilir.</span><span class="sxs-lookup"><span data-stu-id="705e9-145">This is encouraged because Visual Studio makes it so easy to work with Docker that it almost feels transparent—the best example when debugging multi-container applications from Visual Studio.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="705e9-146">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="705e9-146">Additional resources</span></span>

- <span data-ttu-id="705e9-147">**Docker CE for Windows kullanmaya başlayın** </span><span class="sxs-lookup"><span data-stu-id="705e9-147">**Get started with Docker CE for Windows** </span></span>\
  <https://docs.docker.com/docker-for-windows/>

- <span data-ttu-id="705e9-148">**Visual Studio 2019** </span><span class="sxs-lookup"><span data-stu-id="705e9-148">**Visual Studio 2019** </span></span>\
  [https://visualstudio.microsoft.com/downloads/](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019)

![2. adım için görüntü.](./media/docker-app-development-workflow/step-2-write-dockerfile.png)

## <a name="step-2-create-a-dockerfile-related-to-an-existing-net-base-image"></a><span data-ttu-id="705e9-150">Adım 2.</span><span class="sxs-lookup"><span data-stu-id="705e9-150">Step 2.</span></span> <span data-ttu-id="705e9-151">Mevcut bir .NET temel görüntüsüyle ilişkili bir Dockerfile oluşturma</span><span class="sxs-lookup"><span data-stu-id="705e9-151">Create a Dockerfile related to an existing .NET base image</span></span>

<span data-ttu-id="705e9-152">Derlemek istediğiniz her özel görüntü için bir Dockerfile gerekir; Ayrıca, Visual Studio 'dan otomatik olarak veya Docker CLı (Docker Run ve Docker-Compose komutları) kullanarak el ile dağıtım yapıp etmeksizin her bir kapsayıcının dağıtılması için bir Dockerfile gerekir.</span><span class="sxs-lookup"><span data-stu-id="705e9-152">You need a Dockerfile for each custom image you want to build; you also need a Dockerfile for each container to be deployed, whether you deploy automatically from Visual Studio or manually using the Docker CLI (docker run and docker-compose commands).</span></span> <span data-ttu-id="705e9-153">Uygulamanız tek bir özel hizmet içeriyorsa, tek bir Dockerfile gerekir.</span><span class="sxs-lookup"><span data-stu-id="705e9-153">If your application contains a single custom service, you need a single Dockerfile.</span></span> <span data-ttu-id="705e9-154">Uygulamanız birden çok hizmet içeriyorsa (bir mikro hizmet mimarisinde olduğu gibi), her hizmet için bir Dockerfile gerekir.</span><span class="sxs-lookup"><span data-stu-id="705e9-154">If your application contains multiple services (as in a microservices architecture), you need one Dockerfile for each service.</span></span>

<span data-ttu-id="705e9-155">Dockerfile, uygulamanızın veya hizmetinizin kök klasörüne yerleştirilir.</span><span class="sxs-lookup"><span data-stu-id="705e9-155">The Dockerfile is placed in the root folder of your application or service.</span></span> <span data-ttu-id="705e9-156">Bu, Docker 'a uygulamanızı veya hizmetinizi bir kapsayıcıda ayarlamayı ve çalıştırmayı söyleyen komutları içerir.</span><span class="sxs-lookup"><span data-stu-id="705e9-156">It contains the commands that tell Docker how to set up and run your application or service in a container.</span></span> <span data-ttu-id="705e9-157">Kodda el ile Dockerfile oluşturabilir ve bunları .NET bağımlılıklarınızla birlikte projenize ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="705e9-157">You can manually create a Dockerfile in code and add it to your project along with your .NET dependencies.</span></span>

<span data-ttu-id="705e9-158">Visual Studio ve Docker Araçları ile bu görev yalnızca birkaç fare tıklamasını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="705e9-158">With Visual Studio and its tools for Docker, this task requires only a few mouse clicks.</span></span> <span data-ttu-id="705e9-159">Visual Studio 2019 ' de yeni bir proje oluşturduğunuzda, Şekil 5-3 ' de gösterildiği gibi **Docker desteğini etkinleştir**adlı bir seçenek vardır.</span><span class="sxs-lookup"><span data-stu-id="705e9-159">When you create a new project in Visual Studio 2019, there's an option named **Enable Docker Support**, as shown in Figure 5-3.</span></span>

![Docker desteğini etkinleştir onay kutusunu gösteren ekran görüntüsü.](./media/docker-app-development-workflow/enable-docker-support-check-box.png)

<span data-ttu-id="705e9-161">**Şekil 5-3**.</span><span class="sxs-lookup"><span data-stu-id="705e9-161">**Figure 5-3**.</span></span> <span data-ttu-id="705e9-162">Visual Studio 2019 'de yeni bir ASP.NET Core projesi oluştururken Docker desteğini etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="705e9-162">Enabling Docker Support when creating a new ASP.NET Core project in Visual Studio 2019</span></span>

<span data-ttu-id="705e9-163">Ayrıca, Şekil 5-4 ' de gösterildiği gibi, mevcut bir ASP.NET Core Web uygulaması projesinde, **Çözüm Gezgini** projeye sağ tıklayıp **Add**  >  **Docker desteği ekle...** seçeneğini belirleyerek Docker desteğini de etkinleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="705e9-163">You can also enable Docker support on an existing ASP.NET Core web app project by right-clicking the project in **Solution Explorer** and selecting **Add** > **Docker Support...**, as shown in Figure 5-4.</span></span>

![Ekle menüsündeki Docker desteği seçeneğini gösteren ekran görüntüsü.](./media/docker-app-development-workflow/add-docker-support-option.png)

<span data-ttu-id="705e9-165">**Şekil 5-4**.</span><span class="sxs-lookup"><span data-stu-id="705e9-165">**Figure 5-4**.</span></span> <span data-ttu-id="705e9-166">Mevcut bir Visual Studio 2019 projesinde Docker desteğini etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="705e9-166">Enabling Docker support in an existing Visual Studio 2019 project</span></span>

<span data-ttu-id="705e9-167">Bu eylem, gerekli yapılandırmayla projeye bir *Dockerfile* ekler ve yalnızca ASP.NET Core projelerinde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="705e9-167">This action adds a *Dockerfile* to the project with the required configuration, and is only available on ASP.NET Core projects.</span></span>

<span data-ttu-id="705e9-168">Benzer bir şekilde, Visual Studio `docker-compose.yml` tüm çözüm için **> kapsayıcı Orchestrator desteği ekle**seçeneğine sahip bir dosya ekleyebilir... 4. adımda bu seçeneği daha ayrıntılı bir şekilde araştıracağız.</span><span class="sxs-lookup"><span data-stu-id="705e9-168">In a similar fashion, Visual Studio can also add a `docker-compose.yml` file for the whole solution with the option **Add > Container Orchestrator Support...**. In step 4, we'll explore this option in greater detail.</span></span>

### <a name="using-an-existing-official-net-docker-image"></a><span data-ttu-id="705e9-169">Mevcut bir resmi .NET Docker görüntüsünü kullanma</span><span class="sxs-lookup"><span data-stu-id="705e9-169">Using an existing official .NET Docker image</span></span>

<span data-ttu-id="705e9-170">Genellikle, [Docker Hub](https://hub.docker.com/) kayıt defteri gibi resmi bir depodan aldığınız temel görüntünün en üstünde Kapsayıcınız için özel bir görüntü oluşturursunuz.</span><span class="sxs-lookup"><span data-stu-id="705e9-170">You usually build a custom image for your container on top of a base image you get from an official repository like the [Docker Hub](https://hub.docker.com/) registry.</span></span> <span data-ttu-id="705e9-171">Visual Studio 'da Docker desteğini etkinleştirdiğinizde bu durum kesin olarak ne olur?</span><span class="sxs-lookup"><span data-stu-id="705e9-171">That is precisely what happens under the covers when you enable Docker support in Visual Studio.</span></span> <span data-ttu-id="705e9-172">Dockerfile, var olan bir `dotnet/core/aspnet` görüntüyü kullanacaktır.</span><span class="sxs-lookup"><span data-stu-id="705e9-172">Your Dockerfile will use an existing `dotnet/core/aspnet` image.</span></span>

<span data-ttu-id="705e9-173">Daha önce seçtiğiniz çerçeveye ve işletim sistemine bağlı olarak, hangi Docker görüntülerini ve depolarınızı kullanacağınızı anlatılmıştır.</span><span class="sxs-lookup"><span data-stu-id="705e9-173">Earlier we explained which Docker images and repos you can use, depending on the framework and OS you have chosen.</span></span> <span data-ttu-id="705e9-174">Örneğin, ASP.NET Core (Linux veya Windows) kullanmak istiyorsanız kullanılacak görüntü `mcr.microsoft.com/dotnet/core/aspnet:3.1` .</span><span class="sxs-lookup"><span data-stu-id="705e9-174">For instance, if you want to use ASP.NET Core (Linux or Windows), the image to use is `mcr.microsoft.com/dotnet/core/aspnet:3.1`.</span></span> <span data-ttu-id="705e9-175">Bu nedenle, yalnızca Kapsayıcınız için kullanacağınız temel Docker görüntüsünü belirtmeniz yeterlidir.</span><span class="sxs-lookup"><span data-stu-id="705e9-175">Therefore, you just need to specify what base Docker image you will use for your container.</span></span> <span data-ttu-id="705e9-176">Bunu, `FROM mcr.microsoft.com/dotnet/core/aspnet:3.1` Dockerfile dosyanıza ekleyerek yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="705e9-176">You do that by adding `FROM mcr.microsoft.com/dotnet/core/aspnet:3.1` to your Dockerfile.</span></span> <span data-ttu-id="705e9-177">Bu, Visual Studio tarafından otomatik olarak gerçekleştirilir, ancak sürümü güncelleştirirseniz, bu değeri güncelleştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="705e9-177">This will be automatically performed by Visual Studio, but if you were to update the version, you update this value.</span></span>

<span data-ttu-id="705e9-178">Docker Hub 'dan sürüm numarası olan resmi bir .NET görüntü deposu kullanmak, tüm makinelerde (geliştirme, test ve üretim dahil) aynı dil özelliklerinin kullanılabilmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="705e9-178">Using an official .NET image repository from Docker Hub with a version number ensures that the same language features are available on all machines (including development, testing, and production).</span></span>

<span data-ttu-id="705e9-179">Aşağıdaki örnekte, bir ASP.NET Core kapsayıcısı için örnek bir Dockerfile gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="705e9-179">The following example shows a sample Dockerfile for an ASP.NET Core container.</span></span>

```dockerfile
FROM mcr.microsoft.com/dotnet/core/aspnet:3.1
ARG source
WORKDIR /app
EXPOSE 80
COPY ${source:-obj/Docker/publish} .
ENTRYPOINT ["dotnet", " MySingleContainerWebApp.dll "]
```

<span data-ttu-id="705e9-180">Bu durumda, görüntü, resmi ASP.NET Core Docker görüntüsünün 3,1 sürümünü temel alır (Linux ve Windows için çoklu mimari).</span><span class="sxs-lookup"><span data-stu-id="705e9-180">In this case, the image is based on version 3.1 of the official ASP.NET Core Docker image (multi-arch for Linux and Windows).</span></span> <span data-ttu-id="705e9-181">Bu ayar budur `FROM mcr.microsoft.com/dotnet/core/aspnet:3.1` .</span><span class="sxs-lookup"><span data-stu-id="705e9-181">This is the setting `FROM mcr.microsoft.com/dotnet/core/aspnet:3.1`.</span></span> <span data-ttu-id="705e9-182">(Bu temel görüntü hakkında daha fazla bilgi için bkz. [.NET Core Docker Image](https://hub.docker.com/_/microsoft-dotnet-core/) sayfası.) Dockerfile 'da, çalışma zamanında kullanacağınız TCP bağlantı noktasını dinlemek için Docker 'a (Bu durumda, "kullanıma hazır ayarıyla yapılandırıldığı şekilde, bağlantı noktası 80) da sahip olmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="705e9-182">(For more information about this base image, see the [.NET Core Docker Image](https://hub.docker.com/_/microsoft-dotnet-core/) page.) In the Dockerfile, you also need to instruct Docker to listen on the TCP port you will use at runtime (in this case, port 80, as configured with the EXPOSE setting).</span></span>

<span data-ttu-id="705e9-183">Kullanmakta olduğunuz dile ve çerçeveye bağlı olarak Dockerfile içinde ek yapılandırma ayarları belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="705e9-183">You can specify additional configuration settings in the Dockerfile, depending on the language and framework you're using.</span></span> <span data-ttu-id="705e9-184">Örneğin, GIRIŞ noktası satırı, `["dotnet", "MySingleContainerWebApp.dll"]` Docker 'ın bir .NET Core uygulaması çalıştırmasını söyler.</span><span class="sxs-lookup"><span data-stu-id="705e9-184">For instance, the ENTRYPOINT line with `["dotnet", "MySingleContainerWebApp.dll"]` tells Docker to run a .NET Core application.</span></span> <span data-ttu-id="705e9-185">.NET uygulamasını derlemek ve çalıştırmak için SDK ve .NET Core CLI (DotNet CLı) kullanıyorsanız, bu ayar farklı olur.</span><span class="sxs-lookup"><span data-stu-id="705e9-185">If you're using the SDK and the .NET Core CLI (dotnet CLI) to build and run the .NET application, this setting would be different.</span></span> <span data-ttu-id="705e9-186">Alt çizgi, GIRIŞ noktası çizgisi ve diğer ayarların, uygulamanız için seçtiğiniz dile ve platforma bağlı olarak farklı olacaktır.</span><span class="sxs-lookup"><span data-stu-id="705e9-186">The bottom line is that the ENTRYPOINT line and other settings will be different depending on the language and platform you choose for your application.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="705e9-187">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="705e9-187">Additional resources</span></span>

- <span data-ttu-id="705e9-188">**.NET Core uygulamaları için Docker görüntüleri oluşturma** </span><span class="sxs-lookup"><span data-stu-id="705e9-188">**Building Docker Images for .NET Core Applications** </span></span>\
  [https://docs.microsoft.com/dotnet/core/docker/building-net-docker-images](/aspnet/core/host-and-deploy/docker/building-net-docker-images)

- <span data-ttu-id="705e9-189">**Kendi görüntünüzü oluşturun**.</span><span class="sxs-lookup"><span data-stu-id="705e9-189">**Build your own image**.</span></span> <span data-ttu-id="705e9-190">Resmi Docker belgelerinde. </span><span class="sxs-lookup"><span data-stu-id="705e9-190">In the official Docker documentation.</span></span>\
  <https://docs.docker.com/engine/tutorials/dockerimages/>

- <span data-ttu-id="705e9-191">**.NET kapsayıcı görüntüleriyle güncel kalarak** </span><span class="sxs-lookup"><span data-stu-id="705e9-191">**Staying up-to-date with .NET Container Images** </span></span>\
  <https://devblogs.microsoft.com/dotnet/staying-up-to-date-with-net-container-images/>

- <span data-ttu-id="705e9-192">**.NET ve Docker birlikte kullanma-DockerCon 2018 güncelleştirmesi** </span><span class="sxs-lookup"><span data-stu-id="705e9-192">**Using .NET and Docker Together - DockerCon 2018 Update** </span></span>\
  <https://devblogs.microsoft.com/dotnet/using-net-and-docker-together-dockercon-2018-update/>

### <a name="using-multi-arch-image-repositories"></a><span data-ttu-id="705e9-193">Multi-Arch Image depoları kullanma</span><span class="sxs-lookup"><span data-stu-id="705e9-193">Using multi-arch image repositories</span></span>

<span data-ttu-id="705e9-194">Tek bir depo, Linux görüntüsü ve Windows görüntüsü gibi platform türevlerini içerebilir.</span><span class="sxs-lookup"><span data-stu-id="705e9-194">A single repo can contain platform variants, such as a Linux image and a Windows image.</span></span> <span data-ttu-id="705e9-195">Bu özellik, Microsoft (temel görüntü oluşturucuları) gibi satıcıların birden çok platformu (Linux ve Windows) kapsayan tek bir depoyu oluşturmalarına olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="705e9-195">This feature allows vendors like Microsoft (base image creators) to create a single repo to cover multiple platforms (that is Linux and Windows).</span></span> <span data-ttu-id="705e9-196">Örneğin, Docker Hub kayıt defterinde bulunan [DotNet/Core](https://hub.docker.com/_/microsoft-dotnet-core/) deposu, aynı depo adını kullanarak Linux ve Windows nano sunucu desteği sağlar.</span><span class="sxs-lookup"><span data-stu-id="705e9-196">For example, the [dotnet/core](https://hub.docker.com/_/microsoft-dotnet-core/) repository available in the Docker Hub registry provides support for Linux and Windows Nano Server by using the same repo name.</span></span>

<span data-ttu-id="705e9-197">Bir etiketi belirtirseniz, aşağıdaki durumlarda açık olan bir platformu hedefliyorsanız:</span><span class="sxs-lookup"><span data-stu-id="705e9-197">If you specify a tag, targeting a platform that is explicit like in the following cases:</span></span>

- `mcr.microsoft.com/dotnet/core/aspnet:3.1-buster-slim` \
  <span data-ttu-id="705e9-198">Hedefler: .NET Core 3,1 çalışma zamanı-yalnızca Linux üzerinde</span><span class="sxs-lookup"><span data-stu-id="705e9-198">Targets: .NET Core 3.1 runtime-only on Linux</span></span>

- `mcr.microsoft.com/dotnet/core/aspnet:3.1-nanoserver-1909` \
  <span data-ttu-id="705e9-199">Hedefler: .NET Core 3,1 çalışma zamanı-yalnızca Windows nano Server üzerinde</span><span class="sxs-lookup"><span data-stu-id="705e9-199">Targets: .NET Core 3.1 runtime-only on Windows Nano Server</span></span>

<span data-ttu-id="705e9-200">Ancak, aynı etiketle birlikte aynı görüntü adını belirtirseniz, çok katmanlı görüntüler ( `aspnet` görüntü gibi), aşağıdaki örnekte gösterildiği gibi, dağıttığınız Docker ana bilgisayar işletim sistemine bağlı olarak Linux veya Windows sürümünü kullanır:</span><span class="sxs-lookup"><span data-stu-id="705e9-200">But, if you specify the same image name, even with the same tag, the multi-arch images (like the `aspnet` image) will use the Linux or Windows version depending on the Docker host OS you're deploying, as shown in the following example:</span></span>

- `mcr.microsoft.com/dotnet/core/aspnet:3.1` \
  <span data-ttu-id="705e9-201">Multi-Arch: .NET Core 3,1 Runtime-yalnızca Docker Konağı işletim sistemine bağlı olarak Linux veya Windows nano Server</span><span class="sxs-lookup"><span data-stu-id="705e9-201">Multi-arch: .NET Core 3.1 runtime-only on Linux or Windows Nano Server depending on the Docker host OS</span></span>

<span data-ttu-id="705e9-202">Bu şekilde, bir Windows ana bilgisayardan bir görüntü çektiğinizde Windows türevini çeker ve aynı görüntü adının bir Linux ana bilgisayardan çekilerek Linux varyantı alınır.</span><span class="sxs-lookup"><span data-stu-id="705e9-202">This way, when you pull an image from a Windows host, it will pull the Windows variant, and pulling the same image name from a Linux host will pull the Linux variant.</span></span>

### <a name="multi-stage-builds-in-dockerfile"></a><span data-ttu-id="705e9-203">Dockerfile 'da çok aşamalı derlemeler</span><span class="sxs-lookup"><span data-stu-id="705e9-203">Multi-stage builds in Dockerfile</span></span>

<span data-ttu-id="705e9-204">Dockerfile, bir Batch betiğine benzer.</span><span class="sxs-lookup"><span data-stu-id="705e9-204">The Dockerfile is similar to a batch script.</span></span> <span data-ttu-id="705e9-205">Makineyi komut satırından kurmak zorunda kaldıysanız, yapabileceklerinize benzer.</span><span class="sxs-lookup"><span data-stu-id="705e9-205">Similar to what you would do if you had to set up the machine from the command line.</span></span>

<span data-ttu-id="705e9-206">Başlangıç bağlamını ayarlayan bir temel görüntüyle başlar, bu, ana bilgisayar işletim sisteminin üst kısmında yer alan başlangıç dosya sistemi gibidir.</span><span class="sxs-lookup"><span data-stu-id="705e9-206">It starts with a base image that sets up the initial context, it's like the startup filesystem, that sits on top of the host OS.</span></span> <span data-ttu-id="705e9-207">Bu bir işletim sistemi değildir ancak onu kapsayıcının içindeki "bir" işletim sistemi gibi düşünebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="705e9-207">It's not an OS, but you can think of it like "the" OS inside the container.</span></span>

<span data-ttu-id="705e9-208">Her komut satırının yürütülmesi, bir önceki bir değişiklikten değişikliklerle dosya sisteminde yeni bir katman oluşturur; böylece, birleştirildiğinde, sonuçta elde edilen dosya sistemi oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="705e9-208">The execution of every command line creates a new layer on the filesystem with the changes from the previous one, so that, when combined, produce the resulting filesystem.</span></span>

<span data-ttu-id="705e9-209">Her yeni katman, önceki birinin üzerine "oturduğu" ve sonuçta elde edilen görüntü boyutu her komutla arttığı için, örneğin, bir uygulama oluşturmak ve yayımlamak için gerekli SDK 'yi içermesi gerekiyorsa görüntüler çok büyük alabilir.</span><span class="sxs-lookup"><span data-stu-id="705e9-209">Since every new layer "rests" on top of the previous one and the resulting image size increases with every command, images can get very large if they have to include, for example, the SDK needed to build and publish an application.</span></span>

<span data-ttu-id="705e9-210">Bu, çok aşamalı derlemelerin, Magic 'i yapmak için çizim içine (Docker 17,05 ve üzeri) sahip olduğu yerdir.</span><span class="sxs-lookup"><span data-stu-id="705e9-210">This is where multi-stage builds get into the plot (from Docker 17.05 and higher) to do their magic.</span></span>

<span data-ttu-id="705e9-211">Temel fikir, bir aşamanın ilk görüntü olduğu ve ardından bir veya daha fazla komutun ardından son aşamanın son görüntü boyutunu belirlediği aşamalar halinde Dockerfile yürütme işlemini ayırabilmeniz için de kullanılır.</span><span class="sxs-lookup"><span data-stu-id="705e9-211">The core idea is that you can separate the Dockerfile execution process in stages, where a stage is an initial image followed by one or more commands, and the last stage determines the final image size.</span></span>

<span data-ttu-id="705e9-212">Kısaca, çok aşamalı derlemeler, oluşturma işleminin farklı "aşamalarda" bölünmesini sağlar ve ardından son görüntüyü ara aşamaların yalnızca ilgili dizinleri ele alarak birleştirir.</span><span class="sxs-lookup"><span data-stu-id="705e9-212">In short, multi-stage builds allow splitting the creation in different "phases" and then assemble the final image taking only the relevant directories from the intermediate stages.</span></span> <span data-ttu-id="705e9-213">Bu özelliği kullanmaya yönelik genel strateji şunlardır:</span><span class="sxs-lookup"><span data-stu-id="705e9-213">The general strategy to use this feature is:</span></span>

1. <span data-ttu-id="705e9-214">Uygulamayı oluşturmak ve bir klasöre yayımlamak için gereken her şeyi içeren bir temel SDK görüntüsünü (ne kadar büyük değildir) kullanın ve ardından</span><span class="sxs-lookup"><span data-stu-id="705e9-214">Use a base SDK image (doesn't matter how large), with everything needed to build and publish the application to a folder and then</span></span>

2. <span data-ttu-id="705e9-215">Küçük bir son görüntü oluşturmak için, yalnızca bir temel, küçük, çalışma zamanı görüntüsü kullanın ve önceki aşamada yayımlama klasörünü kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="705e9-215">Use a base, small, runtime-only image and copy the publishing folder from the previous stage to produce a small final image.</span></span>

<span data-ttu-id="705e9-216">Çoklu aşamayı anlamanın en iyi yolu, bir Dockerfile 'ın ayrıntılı ve satıra göre ayrıntılıdır. böylece, bir projeye Docker desteği eklerken Visual Studio tarafından oluşturulan ilk Dockerfile ile başlayalım ve daha sonra bazı iyileştirmeler elde edilir.</span><span class="sxs-lookup"><span data-stu-id="705e9-216">Probably the best way to understand multi-stage is going through a Dockerfile in detail, line by line, so let's begin with the initial Dockerfile created by Visual Studio when adding Docker support to a project and will get into some optimizations later.</span></span>

<span data-ttu-id="705e9-217">İlk Dockerfile şuna benzer görünebilir:</span><span class="sxs-lookup"><span data-stu-id="705e9-217">The initial Dockerfile might look something like this:</span></span>

```dockerfile
 1  FROM mcr.microsoft.com/dotnet/core/aspnet:3.1 AS base
 2  WORKDIR /app
 3  EXPOSE 80
 4
 5  FROM mcr.microsoft.com/dotnet/core/sdk:3.1 AS build
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

<span data-ttu-id="705e9-218">Ayrıntılar, satır satır:</span><span class="sxs-lookup"><span data-stu-id="705e9-218">And these are the details, line by line:</span></span>

- <span data-ttu-id="705e9-219">**Satır #1:** Yalnızca bir "küçük" çalışma zamanı temel görüntüsü ile bir aşama başlatın, başvuru için **temel** çağırın.</span><span class="sxs-lookup"><span data-stu-id="705e9-219">**Line #1:** Begin a stage with a "small" runtime-only base image, call it **base** for reference.</span></span>

- <span data-ttu-id="705e9-220">**Satır #2:** Görüntüde **/App** dizinini oluşturun.</span><span class="sxs-lookup"><span data-stu-id="705e9-220">**Line #2:** Create the **/app** directory in the image.</span></span>

- <span data-ttu-id="705e9-221">**Satır #3:** **80**numaralı bağlantı noktasını kullanıma sunun.</span><span class="sxs-lookup"><span data-stu-id="705e9-221">**Line #3:** Expose port **80**.</span></span>

- <span data-ttu-id="705e9-222">**Satır #5:** Oluşturma/yayımlama için "büyük" görüntüyle yeni bir aşama başlatın.</span><span class="sxs-lookup"><span data-stu-id="705e9-222">**Line #5:** Begin a new stage with the "large" image for building/publishing.</span></span> <span data-ttu-id="705e9-223">Başvuru için **derlemeyi** çağırın.</span><span class="sxs-lookup"><span data-stu-id="705e9-223">Call it **build** for reference.</span></span>

- <span data-ttu-id="705e9-224">**Satır #6:** Görüntüde **/src** dizini oluşturun.</span><span class="sxs-lookup"><span data-stu-id="705e9-224">**Line #6:** Create directory **/src** in the image.</span></span>

- <span data-ttu-id="705e9-225">**Satır #7:** 16. satıra kadar, paketleri daha sonra geri yükleyebilmeleri için başvurulan **. csproj** proje dosyalarını kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="705e9-225">**Line #7:** Up to line 16, copy referenced **.csproj** project files to be able to restore packages later.</span></span>

- <span data-ttu-id="705e9-226">**Satır #17:** **Catalog. API** projesi ve başvurulan projeler için paketleri geri yükleyin.</span><span class="sxs-lookup"><span data-stu-id="705e9-226">**Line #17:** Restore packages for the **Catalog.API** project and the referenced projects.</span></span>

- <span data-ttu-id="705e9-227">**Satır #18:** **Çözüme yönelik tüm dizin ağacını** ( **. dockerıgnore** dosyasına dahil edilen dosyalar/dizinler hariç) görüntüdeki **/src** dizinine kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="705e9-227">**Line #18:** Copy **all directory tree for the solution** (except the files/directories included in the **.dockerignore** file) to the **/src** directory in the image.</span></span>

- <span data-ttu-id="705e9-228">**Satır #19:** Geçerli klasörü **Catalog. API** projesi olarak değiştirin.</span><span class="sxs-lookup"><span data-stu-id="705e9-228">**Line #19:** Change the current folder to the **Catalog.API** project.</span></span>

- <span data-ttu-id="705e9-229">**Satır #20:** Projeyi (ve diğer proje bağımlılıklarını) ve görüntüdeki **/App** dizinine çıkışı oluşturun.</span><span class="sxs-lookup"><span data-stu-id="705e9-229">**Line #20:** Build the project (and other project dependencies) and output to the **/app** directory in the image.</span></span>

- <span data-ttu-id="705e9-230">**Satır #22:** Derlemeden devam eden yeni bir aşama başlatın.</span><span class="sxs-lookup"><span data-stu-id="705e9-230">**Line #22:** Begin a new stage continuing from the build.</span></span> <span data-ttu-id="705e9-231">Başvuru için **Yayımla** ' yı çağırın.</span><span class="sxs-lookup"><span data-stu-id="705e9-231">Call it **publish** for reference.</span></span>

- <span data-ttu-id="705e9-232">**Satır #23:** Projeyi (ve bağımlılıkları) ve çıktıyı görüntüdeki **/App** dizinine yayımlayın.</span><span class="sxs-lookup"><span data-stu-id="705e9-232">**Line #23:** Publish the project (and dependencies) and output to the **/app** directory in the image.</span></span>

- <span data-ttu-id="705e9-233">**Satır #25:** **Temel** 'den devam eden yeni bir aşama başlatın ve **nihai**çağrı yapın.</span><span class="sxs-lookup"><span data-stu-id="705e9-233">**Line #25:** Begin a new stage continuing from **base** and call it **final**.</span></span>

- <span data-ttu-id="705e9-234">**Satır #26:** Geçerli dizini **/App**olarak değiştirin.</span><span class="sxs-lookup"><span data-stu-id="705e9-234">**Line #26:** Change the current directory to **/app**.</span></span>

- <span data-ttu-id="705e9-235">**Satır #27:** **/App** dizinini aşama **Yayımla** ' dan geçerli dizine kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="705e9-235">**Line #27:** Copy the **/app** directory from stage **publish** to the current directory.</span></span>

- <span data-ttu-id="705e9-236">**Satır #28:** Kapsayıcı başlatıldığında çalıştırılacak komutu tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="705e9-236">**Line #28:** Define the command to run when the container is started.</span></span>

<span data-ttu-id="705e9-237">Şimdi, eShopOnContainers söz konusu olduğunda tüm işlem performansını geliştirmek için bazı iyileştirmeleri keşfedelim, Linux kapsayıcılarında eksiksiz çözümü oluşturmak için 22 dakika veya daha uzun bir süre anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="705e9-237">Now let's explore some optimizations to improve the whole process performance that, in the case of eShopOnContainers, means about 22 minutes or more to build the complete solution in Linux containers.</span></span>

<span data-ttu-id="705e9-238">Oldukça basit olan Docker 'ın katman önbelleği özelliğinden faydalanabilirsiniz: temel görüntü ve komutlar daha önce yürütülmüş gibi aynıysa, yalnızca komutları yürütmeye gerek kalmadan elde edilen katmanı kullanabilir ve bu nedenle bir süre tasarruf edebilir.</span><span class="sxs-lookup"><span data-stu-id="705e9-238">You'll take advantage of Docker's layer cache feature, which is quite simple: if the base image and the commands are the same as some previously executed, it can just use the resulting layer without the need to execute the commands, thus saving some time.</span></span>

<span data-ttu-id="705e9-239">Bu nedenle, **oluşturma** aşamasına odaklanalım, satırlar 5-6, genellikle aynıdır, ancak her iki satır 7-17, eShopOnContainers 'dan her bir hizmet için farklıdır, ancak satırları 7-16, her zaman yürütülmesi gerekir, ancak satırları:</span><span class="sxs-lookup"><span data-stu-id="705e9-239">So, let's focus on the **build** stage, lines 5-6 are mostly the same, but lines 7-17 are different for every service from eShopOnContainers, so they have to execute every single time, however if you changed lines 7-16 to:</span></span>

```dockerfile
COPY . .
```

<span data-ttu-id="705e9-240">Böylece, her hizmet için yalnızca aynı olacak, tüm çözümü kopyalayacak ve daha büyük bir katman oluşturacak ancak:</span><span class="sxs-lookup"><span data-stu-id="705e9-240">Then it would be just the same for every service, it would copy the whole solution and would create a larger layer but:</span></span>

1. <span data-ttu-id="705e9-241">Kopyalama işlemi yalnızca ilk kez yürütülür (bir dosya değiştirildiğinde ve yeniden oluşturulduğunda) ve diğer tüm hizmetler için önbelleği kullanacaksanız</span><span class="sxs-lookup"><span data-stu-id="705e9-241">The copy process would only be executed the first time (and when rebuilding if a file is changed) and would use the cache for all other services and</span></span>

2. <span data-ttu-id="705e9-242">Bir ara aşamada daha büyük görüntü bulunduğundan, son görüntü boyutunu etkilemez.</span><span class="sxs-lookup"><span data-stu-id="705e9-242">Since the larger image occurs in an intermediate stage, it doesn't affect the final image size.</span></span>

<span data-ttu-id="705e9-243">Sonraki önemli iyileştirme, `restore` her eShopOnContainers hizmeti için de farklı olan 17. satırda yürütülen komutu içerir.</span><span class="sxs-lookup"><span data-stu-id="705e9-243">The next significant optimization involves the `restore` command executed in line 17, which is also different for every service of eShopOnContainers.</span></span> <span data-ttu-id="705e9-244">Bu satırı yalnızca öğesine değiştirirseniz:</span><span class="sxs-lookup"><span data-stu-id="705e9-244">If you change that line to just:</span></span>

```dockerfile
RUN dotnet restore
```

<span data-ttu-id="705e9-245">Tüm çözüm için paketleri geri yükler, ancak yeniden geçerli stratejiyle 15 kez yerine yalnızca bir kez yapılır.</span><span class="sxs-lookup"><span data-stu-id="705e9-245">It would restore the packages for the whole solution, but then again, it would do it just once, instead of the 15 times with the current strategy.</span></span>

<span data-ttu-id="705e9-246">Ancak, `dotnet restore` yalnızca klasörde tek bir proje veya çözüm dosyası varsa çalışır, bu nedenle bu, çok fazla ayrıntıya ulaşmadan bu bir bit daha karmaşıktır ve bunu çözmek için bir yoldur:</span><span class="sxs-lookup"><span data-stu-id="705e9-246">However, `dotnet restore` only runs if there's a single project or solution file in the folder, so achieving this is a bit more complicated and the way to solve it, without getting into too many details, is this:</span></span>

1. <span data-ttu-id="705e9-247">Aşağıdaki satırları **. dockerıgnore**öğesine ekleyin:</span><span class="sxs-lookup"><span data-stu-id="705e9-247">Add the following lines to **.dockerignore**:</span></span>

   - <span data-ttu-id="705e9-248">`*.sln`, ana klasör ağacındaki tüm çözüm dosyalarını yoksaymak için</span><span class="sxs-lookup"><span data-stu-id="705e9-248">`*.sln`, to ignore all solution files in the main folder tree</span></span>

   - <span data-ttu-id="705e9-249">`!eShopOnContainers-ServicesAndWebApps.sln`, yalnızca bu çözüm dosyasını dahil etmek için.</span><span class="sxs-lookup"><span data-stu-id="705e9-249">`!eShopOnContainers-ServicesAndWebApps.sln`, to include only this solution file.</span></span>

2. <span data-ttu-id="705e9-250">`/ignoreprojectextensions:.dcproj`Bağımsız değişkenini de dahil `dotnet restore` ederek, Docker-Compose projesini de yoksayar ve yalnızca eShopOnContainers-ServicesAndWebApps çözümü için paketleri geri yükler.</span><span class="sxs-lookup"><span data-stu-id="705e9-250">Include the `/ignoreprojectextensions:.dcproj` argument to `dotnet restore`, so it also ignores the docker-compose project and only restores the packages for the eShopOnContainers-ServicesAndWebApps solution.</span></span>

<span data-ttu-id="705e9-251">Son iyileştirme için, satır 23 ' ün aynı zamanda uygulama oluşturup 20 ' den sonra da bir zaman alan komutla birlikte geldiğinden emin olmak yeterlidir.</span><span class="sxs-lookup"><span data-stu-id="705e9-251">For the final optimization, it just happens that line 20 is redundant, as line 23 also builds the application and comes, in essence, right after line 20, so there goes another time-consuming command.</span></span>

<span data-ttu-id="705e9-252">Elde edilen dosya bundan sonra:</span><span class="sxs-lookup"><span data-stu-id="705e9-252">The resulting file is then:</span></span>

```dockerfile
 1  FROM mcr.microsoft.com/dotnet/core/aspnet:3.1 AS base
 2  WORKDIR /app
 3  EXPOSE 80
 4
 5  FROM mcr.microsoft.com/dotnet/core/sdk:3.1 AS publish
 6  WORKDIR /src
 7  COPY . .
 8  RUN dotnet restore /ignoreprojectextensions:.dcproj
 9  WORKDIR /src/src/Services/Catalog/Catalog.API
10  RUN dotnet publish Catalog.API.csproj -c Release -o /app
11
12  FROM base AS final
13  WORKDIR /app
14  COPY --from=publish /app
15  ENTRYPOINT ["dotnet", "Catalog.API.dll"]
```

### <a name="creating-your-base-image-from-scratch"></a><span data-ttu-id="705e9-253">Sıfırdan taban görüntünüzü oluşturma</span><span class="sxs-lookup"><span data-stu-id="705e9-253">Creating your base image from scratch</span></span>

<span data-ttu-id="705e9-254">Sıfırdan kendi Docker temel görüntünüzü oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="705e9-254">You can create your own Docker base image from scratch.</span></span> <span data-ttu-id="705e9-255">Bu senaryo, Docker ile başlayan birisi için önerilmez, ancak kendi temel görüntününsün belirli bitleri ayarlamak istiyorsanız bunu yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="705e9-255">This scenario is not recommended for someone who is starting with Docker, but if you want to set the specific bits of your own base image, you can do so.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="705e9-256">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="705e9-256">Additional resources</span></span>

- <span data-ttu-id="705e9-257">**Çoklu mimari .NET Core görüntüleri**. </span><span class="sxs-lookup"><span data-stu-id="705e9-257">**Multi-arch .NET Core images**.</span></span>\
  <https://github.com/dotnet/announcements/issues/14>

- <span data-ttu-id="705e9-258">**Temel görüntü oluşturun**.</span><span class="sxs-lookup"><span data-stu-id="705e9-258">**Create a base image**.</span></span> <span data-ttu-id="705e9-259">Resmi Docker belgeleri. </span><span class="sxs-lookup"><span data-stu-id="705e9-259">Official Docker documentation.</span></span>\
  <https://docs.docker.com/develop/develop-images/baseimages/>

![3. adım için görüntü.](./media/docker-app-development-workflow/step-3-create-dockerfile-defined-images.png)

## <a name="step-3-create-your-custom-docker-images-and-embed-your-application-or-service-in-them"></a><span data-ttu-id="705e9-261">3. Adım</span><span class="sxs-lookup"><span data-stu-id="705e9-261">Step 3.</span></span> <span data-ttu-id="705e9-262">Özel Docker görüntülerinizi oluşturun ve uygulamanızı veya hizmetinizi bunlara ekleyin</span><span class="sxs-lookup"><span data-stu-id="705e9-262">Create your custom Docker images and embed your application or service in them</span></span>

<span data-ttu-id="705e9-263">Uygulamanızdaki her hizmet için ilgili bir görüntü oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="705e9-263">For each service in your application, you need to create a related image.</span></span> <span data-ttu-id="705e9-264">Uygulamanız tek bir hizmetten veya Web uygulamasından yapılırsa yalnızca tek bir görüntüye ihtiyacınız vardır.</span><span class="sxs-lookup"><span data-stu-id="705e9-264">If your application is made up of a single service or web application, you just need a single image.</span></span>

<span data-ttu-id="705e9-265">Docker görüntülerinin Visual Studio 'da sizin için otomatik olarak oluşturulup oluşturulmadığını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="705e9-265">Note that the Docker images are built automatically for you in Visual Studio.</span></span> <span data-ttu-id="705e9-266">Aşağıdaki adımlar yalnızca Düzenleyici/CLı iş akışı için gereklidir ve altında neler olacağı hakkında netlik için açıklanır.</span><span class="sxs-lookup"><span data-stu-id="705e9-266">The following steps are only needed for the editor/CLI workflow and explained for clarity about what happens underneath.</span></span>

<span data-ttu-id="705e9-267">Bir geliştirici olarak, tamamlanmış bir özelliği veya kaynak denetim sisteminize (örneğin, GitHub) değişene kadar yerel olarak geliştirme ve test yapmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="705e9-267">You, as a developer, need to develop and test locally until you push a completed feature or change to your source control system (for example, to GitHub).</span></span> <span data-ttu-id="705e9-268">Bu, Docker görüntülerini oluşturmanız ve kapsayıcıları yerel bir Docker konağına (Windows veya Linux VM) dağıtmanız ve bu yerel kapsayıcılara karşı çalıştırmak, test etmeniz ve hata ayıklaması yapmanız gerektiği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="705e9-268">This means that you need to create the Docker images and deploy containers to a local Docker host (Windows or Linux VM) and run, test, and debug against those local containers.</span></span>

<span data-ttu-id="705e9-269">Docker CLı ve Dockerfile kullanarak yerel ortamınızda özel bir görüntü oluşturmak için, Şekil 5-5 ' de olduğu gibi Docker Build komutunu kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="705e9-269">To create a custom image in your local environment by using Docker CLI and your Dockerfile, you can use the docker build command, as in Figure 5-5.</span></span>

![Docker Build komutunun konsol çıkışını gösteren ekran görüntüsü.](./media/docker-app-development-workflow/run-docker-build-command.png)

<span data-ttu-id="705e9-271">**Şekil 5-5**.</span><span class="sxs-lookup"><span data-stu-id="705e9-271">**Figure 5-5**.</span></span> <span data-ttu-id="705e9-272">Özel bir Docker görüntüsü oluşturma</span><span class="sxs-lookup"><span data-stu-id="705e9-272">Creating a custom Docker image</span></span>

<span data-ttu-id="705e9-273">İsteğe bağlı olarak, proje klasöründen Docker derlemesini doğrudan çalıştırmak yerine, çalıştırmadan önce gerekli .NET kitaplıkları ve ikili dosyaları içeren dağıtılabilir bir klasör oluşturabilir `dotnet publish` ve sonra `docker build` komutunu kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="705e9-273">Optionally, instead of directly running docker build from the project folder, you can first generate a deployable folder with the required .NET libraries and binaries by running `dotnet publish`, and then use the `docker build` command.</span></span>

<span data-ttu-id="705e9-274">Bu, adıyla bir Docker görüntüsü oluşturur `cesardl/netcore-webapi-microservice-docker:first` .</span><span class="sxs-lookup"><span data-stu-id="705e9-274">This will create a Docker image with the name `cesardl/netcore-webapi-microservice-docker:first`.</span></span> <span data-ttu-id="705e9-275">Bu durumda, ilk olarak belirli bir sürümü temsil eden bir etikettir.</span><span class="sxs-lookup"><span data-stu-id="705e9-275">In this case, :first is a tag representing a specific version.</span></span> <span data-ttu-id="705e9-276">Bu adımı, oluşturulan Docker uygulamanız için oluşturmanız gereken her özel görüntü için yineleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="705e9-276">You can repeat this step for each custom image you need to create for your composed Docker application.</span></span>

<span data-ttu-id="705e9-277">Bir uygulama birden çok kapsayıcıyla yapıldığında (yani çok kapsayıcılı bir uygulamadır), `docker-compose up --build` ilgili Docker-Compose. yıml dosyalarında kullanıma sunulan meta verileri kullanarak tek bir komutla ilgili tüm görüntüleri oluşturmak için komutunu da kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="705e9-277">When an application is made of multiple containers (that is, it is a multi-container application), you can also use the `docker-compose up --build` command to build all the related images with a single command by using the metadata exposed in the related docker-compose.yml files.</span></span>

<span data-ttu-id="705e9-278">Şekil 5-6 ' de gösterildiği gibi Docker görüntüleri komutunu kullanarak yerel deponuzda mevcut görüntüleri bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="705e9-278">You can find the existing images in your local repository by using the docker images command, as shown in Figure 5-6.</span></span>

![Mevcut görüntüleri gösteren komut Docker görüntülerinin konsol çıktısı.](./media/docker-app-development-workflow/view-existing-images-with-docker-images.png)

<span data-ttu-id="705e9-280">**Şekil 5-6.**</span><span class="sxs-lookup"><span data-stu-id="705e9-280">**Figure 5-6.**</span></span> <span data-ttu-id="705e9-281">Docker görüntüleri komutunu kullanarak mevcut görüntüleri görüntüleme</span><span class="sxs-lookup"><span data-stu-id="705e9-281">Viewing existing images using the docker images command</span></span>

### <a name="creating-docker-images-with-visual-studio"></a><span data-ttu-id="705e9-282">Visual Studio ile Docker görüntüleri oluşturma</span><span class="sxs-lookup"><span data-stu-id="705e9-282">Creating Docker images with Visual Studio</span></span>

<span data-ttu-id="705e9-283">Docker desteğiyle bir proje oluşturmak için Visual Studio kullandığınızda, açıkça bir görüntü oluşturmazsınız.</span><span class="sxs-lookup"><span data-stu-id="705e9-283">When you use Visual Studio to create a project with Docker support, you don't explicitly create an image.</span></span> <span data-ttu-id="705e9-284">Bunun yerine, dockerte veya hizmeti çalıştırmak için **F5** tuşuna bastığınızda (veya **CTRL + F5**), görüntü sizin için oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="705e9-284">Instead, the image is created for you when you press **F5** (or **Ctrl-F5**) to run the dockerized application or service.</span></span> <span data-ttu-id="705e9-285">Bu adım, Visual Studio 'da otomatiktir ve bunun gerçekleşmediğini görmezsiniz, ancak nelerin altında olduğunu bilmeniz önemlidir.</span><span class="sxs-lookup"><span data-stu-id="705e9-285">This step is automatic in Visual Studio and you won't see it happen, but it's important that you know what's going on underneath.</span></span>

![İsteğe bağlı 4. adım için görüntü.](./media/docker-app-development-workflow/step-4-define-services-docker-compose-yml.png)

## <a name="step-4-define-your-services-in-docker-composeyml-when-building-a-multi-container-docker-application"></a><span data-ttu-id="705e9-287">4. Adım:</span><span class="sxs-lookup"><span data-stu-id="705e9-287">Step 4.</span></span> <span data-ttu-id="705e9-288">Çok kapsayıcılı bir Docker uygulaması oluştururken hizmetlerinizi Docker-Compose. yıml 'de tanımlama</span><span class="sxs-lookup"><span data-stu-id="705e9-288">Define your services in docker-compose.yml when building a multi-container Docker application</span></span>

<span data-ttu-id="705e9-289">[Docker-Compose. yıml](https://docs.docker.com/compose/compose-file/) dosyası, dağıtım komutlarıyla oluşturulmuş bir uygulama olarak dağıtılacak bir ilgili hizmet kümesi tanımlamanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="705e9-289">The [docker-compose.yml](https://docs.docker.com/compose/compose-file/) file lets you define a set of related services to be deployed as a composed application with deployment commands.</span></span> <span data-ttu-id="705e9-290">Ayrıca, bağımlılık ilişkilerini ve çalışma zamanı yapılandırmasını yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="705e9-290">It also configures its dependency relations and run-time configuration.</span></span>

<span data-ttu-id="705e9-291">Bir Docker-Compose. yml dosyası kullanmak için, dosyayı ana veya kök çözüm klasörünüzde aşağıdaki örnekteki gibi içerikle birlikte oluşturmanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="705e9-291">To use a docker-compose.yml file, you need to create the file in your main or root solution folder, with content similar to that in the following example:</span></span>

```yml
version: '3.4'

services:

  webmvc:
    image: eshop/web
    environment:
      - CatalogUrl=http://catalog-api
      - OrderingUrl=http://ordering-api
    ports:
      - "80:80"
    depends_on:
      - catalog-api
      - ordering-api

  catalog-api:
    image: eshop/catalog-api
    environment:
      - ConnectionString=Server=sqldata;Port=1433;Database=CatalogDB;…
    ports:
      - "81:80"
    depends_on:
      - sqldata

  ordering-api:
    image: eshop/ordering-api
    environment:
      - ConnectionString=Server=sqldata;Database=OrderingDb;…
    ports:
      - "82:80"
    extra_hosts:
      - "CESARDLBOOKVHD:10.0.75.1"
    depends_on:
      - sqldata

  sqldata:
    image: mcr.microsoft.com/mssql/server:latest
    environment:
      - SA_PASSWORD=Pass@word
      - ACCEPT_EULA=Y
    ports:
      - "5433:1433"
```

<span data-ttu-id="705e9-292">Bu Docker-Compose. yıml dosyası Basitleştirilmiş ve birleştirilmiş bir sürümdür.</span><span class="sxs-lookup"><span data-stu-id="705e9-292">This docker-compose.yml file is a simplified and merged version.</span></span> <span data-ttu-id="705e9-293">Her bir kapsayıcı için (özel görüntünün adı gibi) statik yapılandırma verilerini, her zaman gerekli olan ve bağlantı dizesi gibi dağıtım ortamına bağlı olabilecek yapılandırma bilgilerini içerir.</span><span class="sxs-lookup"><span data-stu-id="705e9-293">It contains static configuration data for each container (like the name of the custom image), which is always required, and configuration information that might depend on the deployment environment, like the connection string.</span></span> <span data-ttu-id="705e9-294">Sonraki bölümlerde, Docker-Compose. yıml yapılandırmasını birden çok Docker-Compose dosyasına nasıl böleyeceğinizi ve ortam ve yürütme türüne (hata ayıklama veya sürüm) göre değerleri nasıl geçersiz kılacağınızı öğreneceksiniz.</span><span class="sxs-lookup"><span data-stu-id="705e9-294">In later sections, you will learn how to split the docker-compose.yml configuration into multiple docker-compose files and override values depending on the environment and execution type (debug or release).</span></span>

<span data-ttu-id="705e9-295">Docker-Compose. yml dosyası örneği dört hizmeti tanımlar: `webmvc` hizmet (bir Web uygulaması), iki mikro hizmet ( `ordering-api` ve `basket-api` ) ve bir veri kaynağı kapsayıcısı, `sqldata` kapsayıcı olarak çalışan Linux için SQL Server temel alır.</span><span class="sxs-lookup"><span data-stu-id="705e9-295">The docker-compose.yml file example defines four services: the `webmvc` service (a web application), two microservices (`ordering-api` and `basket-api`), and one data source container, `sqldata`, based on SQL Server for Linux running as a container.</span></span> <span data-ttu-id="705e9-296">Her hizmet bir kapsayıcı olarak dağıtılır, bu nedenle her biri için bir Docker görüntüsü gerekir.</span><span class="sxs-lookup"><span data-stu-id="705e9-296">Each service will be deployed as a container, so a Docker image is required for each.</span></span>

<span data-ttu-id="705e9-297">Docker-Compose. yıml dosyası yalnızca hangi kapsayıcıların kullanıldığını, ancak bunların ayrı ayrı nasıl yapılandırıldığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="705e9-297">The docker-compose.yml file specifies not only what containers are being used, but how they are individually configured.</span></span> <span data-ttu-id="705e9-298">Örneğin, `webmvc` . yml dosyasındaki kapsayıcı tanımı:</span><span class="sxs-lookup"><span data-stu-id="705e9-298">For instance, the `webmvc` container definition in the .yml file:</span></span>

- <span data-ttu-id="705e9-299">Önceden oluşturulmuş bir görüntü kullanır `eshop/web:latest` .</span><span class="sxs-lookup"><span data-stu-id="705e9-299">Uses a pre-built `eshop/web:latest` image.</span></span> <span data-ttu-id="705e9-300">Ancak, Docker-Compose dosyasındaki bir derlemeyi temel alan ek bir yapılandırma ile Docker-Compose yürütmesinin bir parçası olarak oluşturulacak görüntüyü de yapılandırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="705e9-300">However, you could also configure the image to be built as part of the docker-compose execution with an additional configuration based on a build: section in the docker-compose file.</span></span>

- <span data-ttu-id="705e9-301">İki ortam değişkenini başlatır (CatalogUrl ve OrderingUrl).</span><span class="sxs-lookup"><span data-stu-id="705e9-301">Initializes two environment variables (CatalogUrl and OrderingUrl).</span></span>

- <span data-ttu-id="705e9-302">Kapsayıcıda açığa çıkarılan 80 numaralı bağlantı noktasını ana makinedeki 80 dış bağlantı noktasına iletir.</span><span class="sxs-lookup"><span data-stu-id="705e9-302">Forwards the exposed port 80 on the container to the external port 80 on the host machine.</span></span>

- <span data-ttu-id="705e9-303">Web uygulamasını Katalog ve sıralama hizmetine depends_on ayarıyla bağlar.</span><span class="sxs-lookup"><span data-stu-id="705e9-303">Links the web app to the catalog and ordering service with the depends_on setting.</span></span> <span data-ttu-id="705e9-304">Bu, hizmetin bu hizmetler başlatılmadan beklemesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="705e9-304">This causes the service to wait until those services are started.</span></span>

<span data-ttu-id="705e9-305">Mikro hizmetleri ve çok Kapsayıcılı uygulamaları nasıl uygulayacağınızı kapsadığımızda, Docker-Compose. yıml dosyasını sonraki bir bölümde geri ziyaret edeceğiz.</span><span class="sxs-lookup"><span data-stu-id="705e9-305">We will revisit the docker-compose.yml file in a later section when we cover how to implement microservices and multi-container apps.</span></span>

### <a name="working-with-docker-composeyml-in-visual-studio-2019"></a><span data-ttu-id="705e9-306">Visual Studio 2019 ' de Docker-Compose. yıml ile çalışma</span><span class="sxs-lookup"><span data-stu-id="705e9-306">Working with docker-compose.yml in Visual Studio 2019</span></span>

<span data-ttu-id="705e9-307">Daha önce bahsedildiği gibi, bir projeye Dockerfile eklemenin yanı sıra, Visual Studio 2017 (sürüm 15,8 ' den itibaren) bir çözüme Docker Compose için Orchestrator desteği ekleyebilirler.</span><span class="sxs-lookup"><span data-stu-id="705e9-307">Besides adding a Dockerfile to a project, as we mentioned before, Visual Studio 2017 (from version 15.8 on) can add orchestrator support for Docker Compose to a solution.</span></span>

<span data-ttu-id="705e9-308">Şekil 5-7 ' de gösterildiği gibi, kapsayıcı Orchestrator desteğini ilk kez eklediğinizde, Visual Studio proje için Dockerfile 'ı oluşturur ve çeşitli Global dosyalarla çözümünüzde yeni bir (hizmet bölümü) projesi oluşturur `docker-compose*.yml` ve ardından projeyi bu dosyalara ekler.</span><span class="sxs-lookup"><span data-stu-id="705e9-308">When you add container orchestrator support, as shown in Figure 5-7, for the first time, Visual Studio creates the Dockerfile for the project and creates a new (service section) project in your solution with several global `docker-compose*.yml` files, and then adds the project to those files.</span></span> <span data-ttu-id="705e9-309">Daha sonra Docker-Compose. yıml dosyalarını açabilir ve bunları ek özelliklerle güncelleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="705e9-309">You can then open the docker-compose.yml files and update them with additional features.</span></span>

<span data-ttu-id="705e9-310">Bu işlemi, Docker-Compose. yıml dosyasına eklemek istediğiniz her proje için tekrarlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="705e9-310">You have to repeat this operation form every project you want to include in the docker-compose.yml file.</span></span>

<span data-ttu-id="705e9-311">Bu yazma sırasında, Visual Studio **Docker Compose** ve **Kubernetes/Held** düzenleyiciler destekler.</span><span class="sxs-lookup"><span data-stu-id="705e9-311">At the time of this writing, Visual Studio supports **Docker Compose** and **Kubernetes/Helm** orchestrators.</span></span>

![Proje bağlam menüsündeki kapsayıcı Orchestrator desteği seçeneğini gösteren ekran görüntüsü.](./media/docker-app-development-workflow/add-container-orchestrator-support-option.png)

<span data-ttu-id="705e9-313">**Şekil 5-7**.</span><span class="sxs-lookup"><span data-stu-id="705e9-313">**Figure 5-7**.</span></span> <span data-ttu-id="705e9-314">ASP.NET Core projesine sağ tıklayarak Visual Studio 2019 ' de Docker desteği ekleme</span><span class="sxs-lookup"><span data-stu-id="705e9-314">Adding Docker support in Visual Studio 2019 by right-clicking an ASP.NET Core project</span></span>

<span data-ttu-id="705e9-315">Visual Studio 'daki çözümünüze Orchestrator desteği ekledikten sonra, `docker-compose.dcproj` şekil 5-8 ' de gösterildiği gibi eklenen Docker-Compose. yıml dosyalarını içeren Çözüm Gezgini yeni bir düğüm (proje dosyasında) görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="705e9-315">After you add orchestrator support to your solution in Visual Studio, you will also see a new node (in the `docker-compose.dcproj` project file) in Solution Explorer that contains the added docker-compose.yml files, as shown in Figure 5-8.</span></span>

![Çözüm Gezgini Docker-Compose düğümünün ekran görüntüsü.](./media/docker-app-development-workflow/docker-compose-tree-node.png)

<span data-ttu-id="705e9-317">**Şekil 5-8**.</span><span class="sxs-lookup"><span data-stu-id="705e9-317">**Figure 5-8**.</span></span> <span data-ttu-id="705e9-318">Visual Studio 2019 Çözüm Gezgini eklenen **Docker-Compose** ağacı düğümü</span><span class="sxs-lookup"><span data-stu-id="705e9-318">The **docker-compose** tree node added in Visual Studio 2019 Solution Explorer</span></span>

<span data-ttu-id="705e9-319">Komutunu kullanarak tek bir Docker-Compose. yıml dosyası ile çok kapsayıcılı bir uygulama dağıtabilirsiniz `docker-compose up` .</span><span class="sxs-lookup"><span data-stu-id="705e9-319">You could deploy a multi-container application with a single docker-compose.yml file by using the `docker-compose up` command.</span></span> <span data-ttu-id="705e9-320">Ancak, Visual Studio bu grubun bir grubunu ekleyerek ortama (geliştirme veya üretim) ve yürütme türüne (yayın veya hata ayıklama) bağlı olarak değerleri geçersiz kılabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="705e9-320">However, Visual Studio adds a group of them so you can override values depending on the environment (development or production) and execution type (release or debug).</span></span> <span data-ttu-id="705e9-321">Bu özellik sonraki bölümlerde açıklanacaktır.</span><span class="sxs-lookup"><span data-stu-id="705e9-321">This capability will be explained in later sections.</span></span>

![5. adım için görüntü.](./media/docker-app-development-workflow/step-5-run-containers-compose-app.png)

## <a name="step-5-build-and-run-your-docker-application"></a><span data-ttu-id="705e9-323">5. Adım.</span><span class="sxs-lookup"><span data-stu-id="705e9-323">Step 5.</span></span> <span data-ttu-id="705e9-324">Docker uygulamanızı derleyin ve çalıştırın</span><span class="sxs-lookup"><span data-stu-id="705e9-324">Build and run your Docker application</span></span>

<span data-ttu-id="705e9-325">Uygulamanızın yalnızca tek bir kapsayıcısı varsa, bunu Docker konağına (VM veya fiziksel sunucu) dağıtarak çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="705e9-325">If your application only has a single container, you can run it by deploying it to your Docker host (VM or physical server).</span></span> <span data-ttu-id="705e9-326">Bununla birlikte, uygulamanız birden çok hizmet içeriyorsa, tek bir CLı komutu (veya Visual Studio ile) kullanarak bu komutu, kapsayan bir uygulama olarak dağıtabilirsiniz `docker-compose up)` .</span><span class="sxs-lookup"><span data-stu-id="705e9-326">However, if your application contains multiple services, you can deploy it as a composed application, either using a single CLI command (`docker-compose up)`, or with Visual Studio, which will use that command under the covers.</span></span> <span data-ttu-id="705e9-327">Farklı seçeneklere göz atalım.</span><span class="sxs-lookup"><span data-stu-id="705e9-327">Let's look at the different options.</span></span>

### <a name="option-a-running-a-single-container-application"></a><span data-ttu-id="705e9-328">Seçenek A: tek kapsayıcılı bir uygulama çalıştırma</span><span class="sxs-lookup"><span data-stu-id="705e9-328">Option A: Running a single-container application</span></span>

#### <a name="using-docker-cli"></a><span data-ttu-id="705e9-329">Docker CLı 'yi kullanma</span><span class="sxs-lookup"><span data-stu-id="705e9-329">Using Docker CLI</span></span>

<span data-ttu-id="705e9-330">`docker run`Şekil 5-9 ' de gösterildiği gibi, komutunu kullanarak bir Docker kapsayıcısı çalıştırabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="705e9-330">You can run a Docker container using the `docker run` command, as shown in Figure 5-9:</span></span>

```console
docker run -t -d -p 80:5000 cesardl/netcore-webapi-microservice-docker:first
```

<span data-ttu-id="705e9-331">Yukarıdaki komut, her çalıştırılışında belirtilen görüntüden yeni bir kapsayıcı örneği oluşturur.</span><span class="sxs-lookup"><span data-stu-id="705e9-331">The above command will create a new container instance from the specified image, every time it's run.</span></span> <span data-ttu-id="705e9-332">`--name`Kapsayıcıya bir ad vermek için parametresini kullanabilir ve sonra `docker start {name}` var olan bir kapsayıcı örneğini çalıştırmak için (ya da kapsayıcı kimliğini veya otomatik adı kullanabilirsiniz) kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="705e9-332">You can use the `--name` parameter to give a name to the container and then use `docker start {name}` (or use the container ID or automatic name) to run an existing container instance.</span></span>

![Docker Run komutunu kullanarak Docker kapsayıcısı çalıştıran ekran görüntüsü.](./media/docker-app-development-workflow/use-docker-run-command.png)

<span data-ttu-id="705e9-334">**Şekil 5-9**.</span><span class="sxs-lookup"><span data-stu-id="705e9-334">**Figure 5-9**.</span></span> <span data-ttu-id="705e9-335">Docker Run komutunu kullanarak Docker kapsayıcısı çalıştırma</span><span class="sxs-lookup"><span data-stu-id="705e9-335">Running a Docker container using the docker run command</span></span>

<span data-ttu-id="705e9-336">Bu durumda, komut kapsayıcının 5000 iç bağlantı noktasını ana makinenin 80 numaralı bağlantı noktasına bağlar.</span><span class="sxs-lookup"><span data-stu-id="705e9-336">In this case, the command binds the internal port 5000 of the container to port 80 of the host machine.</span></span> <span data-ttu-id="705e9-337">Bu, konağın 80 numaralı bağlantı noktasını dinlediği ve kapsayıcıda bağlantı noktası 5000 ' e ileten anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="705e9-337">This means that the host is listening on port 80 and forwarding to port 5000 on the container.</span></span>

<span data-ttu-id="705e9-338">Gösterilen karma kapsayıcı KIMLIĞIDIR ve seçenek kullanılmazsa rastgele okunabilir bir ad atanır `--name` .</span><span class="sxs-lookup"><span data-stu-id="705e9-338">The hash shown is the container ID and it's also assigned a random readable name if the `--name` option is not used.</span></span>

#### <a name="using-visual-studio"></a><span data-ttu-id="705e9-339">Visual Studio’yu kullanma</span><span class="sxs-lookup"><span data-stu-id="705e9-339">Using Visual Studio</span></span>

<span data-ttu-id="705e9-340">Kapsayıcı Orchestrator desteği eklemediyseniz, Visual Studio 'da **CTRL-F5** tuşlarına basarak tek bir kapsayıcı uygulamasını da çalıştırabilirsiniz ve ayrıca **F5** 'i kullanarak kapsayıcıda uygulamada hata ayıklaması yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="705e9-340">If you haven't added container orchestrator support, you can also run a single container app in Visual Studio by pressing **Ctrl-F5** and you can also use **F5** to debug the application within the container.</span></span> <span data-ttu-id="705e9-341">Kapsayıcı, Docker Run kullanarak yerel olarak çalışır.</span><span class="sxs-lookup"><span data-stu-id="705e9-341">The container runs locally using docker run.</span></span>

### <a name="option-b-running-a-multi-container-application"></a><span data-ttu-id="705e9-342">Seçenek B: çok kapsayıcılı bir uygulama çalıştırma</span><span class="sxs-lookup"><span data-stu-id="705e9-342">Option B: Running a multi-container application</span></span>

<span data-ttu-id="705e9-343">Çoğu kurumsal senaryoda, bir Docker uygulaması birden çok hizmetten oluşur. Bu, Şekil 5-10 ' de gösterildiği gibi çok kapsayıcılı bir uygulama çalıştırmanız gerektiği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="705e9-343">In most enterprise scenarios, a Docker application will be composed of multiple services, which means you need to run a multi-container application, as shown in Figure 5-10.</span></span>

![Birkaç Docker kapsayıcı içeren VM](./media/docker-app-development-workflow/vm-with-docker-containers-deployed.png)

<span data-ttu-id="705e9-345">**Şekil 5-10**.</span><span class="sxs-lookup"><span data-stu-id="705e9-345">**Figure 5-10**.</span></span> <span data-ttu-id="705e9-346">Docker Kapsayıcıları dağıtılan VM</span><span class="sxs-lookup"><span data-stu-id="705e9-346">VM with Docker containers deployed</span></span>

#### <a name="using-docker-cli"></a><span data-ttu-id="705e9-347">Docker CLı 'yi kullanma</span><span class="sxs-lookup"><span data-stu-id="705e9-347">Using Docker CLI</span></span>

<span data-ttu-id="705e9-348">Docker CLı ile çok kapsayıcılı bir uygulama çalıştırmak için `docker-compose up` komutunu kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="705e9-348">To run a multi-container application with the Docker CLI, you use the `docker-compose up` command.</span></span> <span data-ttu-id="705e9-349">Bu komut, çok kapsayıcılı bir uygulama dağıtmak için çözüm düzeyinde bulunan **Docker-Compose. yıml** dosyasını kullanır.</span><span class="sxs-lookup"><span data-stu-id="705e9-349">This command uses the **docker-compose.yml** file that you have at the solution level to deploy a multi-container application.</span></span> <span data-ttu-id="705e9-350">Şekil 5-11, Docker-Compose. yıml dosyasını içeren ana çözüm dizininizden komut çalıştırırken sonuçları gösterir.</span><span class="sxs-lookup"><span data-stu-id="705e9-350">Figure 5-11 shows the results when running the command from your main solution directory, which contains the docker-compose.yml file.</span></span>

![Docker-Compose up komutu çalıştırılırken ekran görünümü](./media/docker-app-development-workflow/results-docker-compose-up.png)

<span data-ttu-id="705e9-352">**Şekil 5-11**.</span><span class="sxs-lookup"><span data-stu-id="705e9-352">**Figure 5-11**.</span></span> <span data-ttu-id="705e9-353">Docker-Compose up komutunu çalıştırırken örnek sonuçlar</span><span class="sxs-lookup"><span data-stu-id="705e9-353">Example results when running the docker-compose up command</span></span>

<span data-ttu-id="705e9-354">Docker-Compose komutu çalıştıktan sonra, uygulama ve ilgili kapsayıcıları Şekil 5-10 ' de gösterildiği gibi Docker ana bilgisayarınıza dağıtılır.</span><span class="sxs-lookup"><span data-stu-id="705e9-354">After the docker-compose up command runs, the application and its related containers are deployed into your Docker host, as depicted in Figure 5-10.</span></span>

#### <a name="using-visual-studio"></a><span data-ttu-id="705e9-355">Visual Studio’yu kullanma</span><span class="sxs-lookup"><span data-stu-id="705e9-355">Using Visual Studio</span></span>

<span data-ttu-id="705e9-356">Visual Studio 2019 kullanarak çok kapsayıcılı bir uygulama çalıştırmak daha basit olamaz.</span><span class="sxs-lookup"><span data-stu-id="705e9-356">Running a multi-container application using Visual Studio 2019 can't get any simpler.</span></span> <span data-ttu-id="705e9-357">Hata ayıklamak için **CTRL-F5** tuşlarına **basın veya her** zamanki gibi, **Docker-Compose** projesini başlangıç projesi olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="705e9-357">You just press **Ctrl-F5** to run or **F5** to debug, as usual, setting up the **docker-compose** project as the startup project.</span></span>  <span data-ttu-id="705e9-358">Visual Studio tüm gerekli kurulumu işler, bu nedenle her zamanki gibi kesme noktaları oluşturabilir ve son olarak "uzak sunucular" içinde çalışan ve hata ayıklamada olduğu gibi "uzak sunucularda" hata ayıklaması yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="705e9-358">Visual Studio handles all needed setup, so you can create breakpoints as usual and debug what finally become independent processes running in "remote servers", with the debugger already attached, just like that.</span></span>

<span data-ttu-id="705e9-359">Daha önce bahsedildiği gibi, bir çözüm içindeki bir projeye Docker çözüm desteği eklediğinizde, bu proje genel (çözüm düzeyi) Docker-Compose. yıml dosyasında yapılandırılmıştır ve bu, tüm çözümü tek seferde çalıştırmanıza veya hata ayıklamanıza olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="705e9-359">As mentioned before, each time you add Docker solution support to a project within a solution, that project is configured in the global (solution-level) docker-compose.yml file, which lets you run or debug the whole solution at once.</span></span> <span data-ttu-id="705e9-360">Visual Studio, Docker çözüm desteğinin etkinleştirildiği her proje için bir kapsayıcı başlatır ve tüm iç adımları (dotnet publish, Docker Build, vb.) gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="705e9-360">Visual Studio will start one container for each project that has Docker solution support enabled, and perform all the internal steps for you (dotnet publish, docker build, etc.).</span></span>

<span data-ttu-id="705e9-361">Tüm drudgery göz atmak istiyorsanız, dosyaya göz atın:</span><span class="sxs-lookup"><span data-stu-id="705e9-361">If you want to take a peek at all the drudgery, take a look at the file:</span></span>

`{root solution folder}\obj\Docker\docker-compose.vs.debug.g.yml`

<span data-ttu-id="705e9-362">Buradaki önemli nokta, Şekil 5-12 ' de gösterildiği gibi, Visual Studio 2019 ' de gösterildiği gibi, F5 tuşu eylemi için ek bir **Docker** komutu vardır.</span><span class="sxs-lookup"><span data-stu-id="705e9-362">The important point here is that, as shown in Figure 5-12, in Visual Studio 2019 there is an additional **Docker** command for the F5 key action.</span></span> <span data-ttu-id="705e9-363">Bu seçenek, çözüm düzeyindeki Docker-Compose. yıml dosyalarında tanımlanan tüm kapsayıcıları çalıştırarak çok kapsayıcılı bir uygulamayı çalıştırmanızı veya hata ayıklamanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="705e9-363">This option lets you run or debug a multi-container application by running all the containers that are defined in the docker-compose.yml files at the solution level.</span></span> <span data-ttu-id="705e9-364">Birden çok Kapsayıcılı çözüm için hata ayıklama özelliği, çeşitli kesme noktaları, farklı bir projede (kapsayıcı) ve Visual Studio 'dan hata ayıklama yaparken, farklı projelerde tanımlanmış ve farklı kapsayıcılarda çalışan kesme noktalarında durduğunuz anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="705e9-364">The ability to debug multiple-container solutions means that you can set several breakpoints, each breakpoint in a different project (container), and while debugging from Visual Studio you will stop at breakpoints defined in different projects and running on different containers.</span></span>

![Docker-Compose projesi çalıştıran hata ayıklama araç çubuğunun ekran görüntüsü.](./media/docker-app-development-workflow/debug-toolbar-docker-compose-project.png)

<span data-ttu-id="705e9-366">**Şekil 5-12**.</span><span class="sxs-lookup"><span data-stu-id="705e9-366">**Figure 5-12**.</span></span> <span data-ttu-id="705e9-367">Visual Studio 2019 'de çok Kapsayıcılı uygulamalar çalıştırma</span><span class="sxs-lookup"><span data-stu-id="705e9-367">Running multi-container apps in Visual Studio 2019</span></span>

### <a name="additional-resources"></a><span data-ttu-id="705e9-368">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="705e9-368">Additional resources</span></span>

- <span data-ttu-id="705e9-369">**ASP.NET kapsayıcısını uzak bir Docker konağına dağıtma** </span><span class="sxs-lookup"><span data-stu-id="705e9-369">**Deploy an ASP.NET container to a remote Docker host** </span></span>\
  <https://docs.microsoft.com/visualstudio/containers/hosting-web-apps-in-docker>

### <a name="a-note-about-testing-and-deploying-with-orchestrators"></a><span data-ttu-id="705e9-370">Düzenleyiciler ile test ve dağıtma hakkında bir bilgi</span><span class="sxs-lookup"><span data-stu-id="705e9-370">A note about testing and deploying with orchestrators</span></span>

<span data-ttu-id="705e9-371">Docker-Compose ve Docker çalıştırma komutları (ya da Visual Studio 'da kapsayıcıları çalıştırmak ve hata ayıklamak) geliştirme ortamınızda kapsayıcıları test etmek için yeterlidir.</span><span class="sxs-lookup"><span data-stu-id="705e9-371">The docker-compose up and docker run commands (or running and debugging the containers in Visual Studio) are adequate for testing containers in your development environment.</span></span> <span data-ttu-id="705e9-372">Ancak, [Kubernetes](https://kubernetes.io/) veya [Service Fabric](https://azure.microsoft.com/services/service-fabric/)gibi düzenleyicilerinin hedeflemesini yapmanız gereken üretim dağıtımları için bu yaklaşımı kullanmamalısınız.</span><span class="sxs-lookup"><span data-stu-id="705e9-372">But you should not use this approach for production deployments, where you should target orchestrators like [Kubernetes](https://kubernetes.io/) or [Service Fabric](https://azure.microsoft.com/services/service-fabric/).</span></span> <span data-ttu-id="705e9-373">Kubernetes kullanıyorsanız, kapsayıcıları ve [Hizmetleri](https://kubernetes.io/docs/concepts/services-networking/service/) ağa göre düzenlemek için [Pod](https://kubernetes.io/docs/concepts/workloads/pods/pod/) 'yi kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="705e9-373">If you're using Kubernetes, you have to use [pods](https://kubernetes.io/docs/concepts/workloads/pods/pod/) to organize containers and [services](https://kubernetes.io/docs/concepts/services-networking/service/) to network them.</span></span> <span data-ttu-id="705e9-374">Ayrıca, Pod oluşturma ve değişiklik düzenlemek için [dağıtımları](https://kubernetes.io/docs/concepts/workloads/controllers/deployment/) da kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="705e9-374">You also use [deployments](https://kubernetes.io/docs/concepts/workloads/controllers/deployment/) to organize pod creation and modification.</span></span>

![6. adım için görüntü.](./media/docker-app-development-workflow/step-6-test-app-microservices.png)

## <a name="step-6-test-your-docker-application-using-your-local-docker-host"></a><span data-ttu-id="705e9-376">6. Adım.</span><span class="sxs-lookup"><span data-stu-id="705e9-376">Step 6.</span></span> <span data-ttu-id="705e9-377">Yerel Docker konağını kullanarak Docker uygulamanızı test etme</span><span class="sxs-lookup"><span data-stu-id="705e9-377">Test your Docker application using your local Docker host</span></span>

<span data-ttu-id="705e9-378">Bu adım, uygulamanızın yaptığı işe göre farklılık gösterir.</span><span class="sxs-lookup"><span data-stu-id="705e9-378">This step will vary depending on what your application is doing.</span></span> <span data-ttu-id="705e9-379">Tek bir kapsayıcı veya hizmet olarak dağıtılan basit bir .NET Core Web uygulamasında, Şekil 5-13 ' de gösterildiği gibi, Docker ana bilgisayarında bir tarayıcı açarak ve bu siteye giderek hizmete erişebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="705e9-379">In a simple .NET Core Web application that is deployed as a single container or service, you can access the service by opening a browser on the Docker host and navigating to that site, as shown in Figure 5-13.</span></span> <span data-ttu-id="705e9-380">(Dockerfile içindeki yapılandırma kapsayıcıyı 80 dışında bir şey olan konaktaki bir bağlantı noktasıyla eşleiyorsa, URL 'ye ana bilgisayar bağlantı noktasını ekleyin.)</span><span class="sxs-lookup"><span data-stu-id="705e9-380">(If the configuration in the Dockerfile maps the container to a port on the host that is anything other than 80, include the host port in the URL.)</span></span>

![Localhost/API/Values yanıtının ekran görüntüsü.](./media/docker-app-development-workflow/test-docker-app-locally-localhost.png)

<span data-ttu-id="705e9-382">**Şekil 5-13**.</span><span class="sxs-lookup"><span data-stu-id="705e9-382">**Figure 5-13**.</span></span> <span data-ttu-id="705e9-383">Docker uygulamanızı localhost kullanarak yerel olarak test etme örneği</span><span class="sxs-lookup"><span data-stu-id="705e9-383">Example of testing your Docker application locally using localhost</span></span>

<span data-ttu-id="705e9-384">Localhost, Docker ana bilgisayar IP 'sini işaret etmiyor (varsayılan olarak, Docker CE kullanırken), hizmetinize gitmek için makinenizin ağ kartının IP adresini kullanın.</span><span class="sxs-lookup"><span data-stu-id="705e9-384">If localhost is not pointing to the Docker host IP (by default, when using Docker CE, it should), to navigate to your service, use the IP address of your machine's network card.</span></span>

<span data-ttu-id="705e9-385">Tarayıcıdaki bu URL 'nin incelenen belirli kapsayıcı örneği için 80 bağlantı noktasını kullandığını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="705e9-385">Note that this URL in the browser uses port 80 for the particular container example being discussed.</span></span> <span data-ttu-id="705e9-386">Ancak, dahili olarak istekler 5000 numaralı bağlantı noktasına yönlendirilmekte, çünkü bu, önceki adımda açıklandığı gibi Docker Run komutuyla dağıtılmıştı.</span><span class="sxs-lookup"><span data-stu-id="705e9-386">However, internally the requests are being redirected to port 5000, because that was how it was deployed with the docker run command, as explained in a previous step.</span></span>

<span data-ttu-id="705e9-387">Ayrıca Şekil 5-14 ' de gösterildiği gibi, terminalden kıvrımlı kullanarak uygulamayı test edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="705e9-387">You can also test the application using curl from the terminal, as shown in Figure 5-14.</span></span> <span data-ttu-id="705e9-388">Windows 'daki bir Docker yüklemesinde, makinenizin gerçek IP adresine ek olarak varsayılan Docker ana bilgisayar IP 'si her zaman 10.0.75.1.</span><span class="sxs-lookup"><span data-stu-id="705e9-388">In a Docker installation on Windows, the default Docker Host IP is always 10.0.75.1 in addition to your machine's actual IP address.</span></span>

![Konsol çıkışı, http://10.0.75.1/API/values kıvrımlı ile elde.](./media/docker-app-development-workflow/test-docker-app-locally-curl.png)

<span data-ttu-id="705e9-390">**Şekil 5-14**.</span><span class="sxs-lookup"><span data-stu-id="705e9-390">**Figure 5-14**.</span></span> <span data-ttu-id="705e9-391">Docker uygulamanızı kıvrımlı kullanarak yerel olarak test etme örneği</span><span class="sxs-lookup"><span data-stu-id="705e9-391">Example of testing your Docker application locally using curl</span></span>

### <a name="testing-and-debugging-containers-with-visual-studio-2019"></a><span data-ttu-id="705e9-392">Visual Studio 2019 ile kapsayıcıları test etme ve hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="705e9-392">Testing and debugging containers with Visual Studio 2019</span></span>

<span data-ttu-id="705e9-393">Visual Studio 2019 ile kapsayıcıları çalıştırırken ve hata ayıklarken, kapsayıcılar olmadan çalıştırırken kullandığınız şekilde .NET uygulamasında hata ayıklaması yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="705e9-393">When running and debugging the containers with Visual Studio 2019, you can debug the .NET application in much the same way as you would when running without containers.</span></span>

### <a name="testing-and-debugging-without-visual-studio"></a><span data-ttu-id="705e9-394">Visual Studio olmadan test etme ve hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="705e9-394">Testing and debugging without Visual Studio</span></span>

<span data-ttu-id="705e9-395">Düzenleyici/CLı yaklaşımını kullanarak geliştiriyorsanız, hata ayıklama kapsayıcıları daha zordur ve büyük olasılıkla izlemeler oluşturarak hata ayıklama isteyeceksiniz.</span><span class="sxs-lookup"><span data-stu-id="705e9-395">If you're developing using the editor/CLI approach, debugging containers is more difficult and you'll probably want to debug by generating traces.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="705e9-396">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="705e9-396">Additional resources</span></span>

- <span data-ttu-id="705e9-397">**Yerel bir Docker kapsayıcısında uygulamalarda hata ayıklama** </span><span class="sxs-lookup"><span data-stu-id="705e9-397">**Debugging apps in a local Docker container** </span></span>\
  [https://docs.microsoft.com/visualstudio/containers/edit-and-refresh](/visualstudio/containers/edit-and-refresh)

- <span data-ttu-id="705e9-398">**Steve Lasker. Docker ile ASP.NET Core uygulamalar oluşturun, hata ayıklayın, dağıtın.**</span><span class="sxs-lookup"><span data-stu-id="705e9-398">**Steve Lasker. Build, Debug, Deploy ASP.NET Core Apps with Docker.**</span></span> <span data-ttu-id="705e9-399">Video.</span><span class="sxs-lookup"><span data-stu-id="705e9-399">Video.</span></span> \
  <https://channel9.msdn.com/Events/Visual-Studio/Visual-Studio-2017-Launch/T115>

## <a name="simplified-workflow-when-developing-containers-with-visual-studio"></a><span data-ttu-id="705e9-400">Visual Studio ile kapsayıcılar geliştirirken Basitleştirilmiş iş akışı</span><span class="sxs-lookup"><span data-stu-id="705e9-400">Simplified workflow when developing containers with Visual Studio</span></span>

<span data-ttu-id="705e9-401">Etkin olarak, Visual Studio 'Yu kullanırken iş akışı, düzenleyici/CLı yaklaşımını kullanmaktan daha basittir.</span><span class="sxs-lookup"><span data-stu-id="705e9-401">Effectively, the workflow when using Visual Studio is a lot simpler than if you use the editor/CLI approach.</span></span> <span data-ttu-id="705e9-402">Docker ve Docker-Compose. yıml dosyalarıyla ilgili Docker için gereken adımların çoğu Şekil 5-15 ' de gösterildiği gibi Visual Studio tarafından gizlenir veya basitleştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="705e9-402">Most of the steps required by Docker related to the Dockerfile and docker-compose.yml files are hidden or simplified by Visual Studio, as shown in Figure 5-15.</span></span>

:::image type="complex" source="./media/docker-app-development-workflow/simplified-life-cycle-containerized-apps-docker-cli.png" alt-text="Uygulama oluşturmak için gereken beş Basitleştirilmiş adımı gösteren diyagram.":::
<span data-ttu-id="705e9-404">Docker uygulamaları için geliştirme süreci: 1-uygulamanızı kodlayın, 2-Dockerfile/s, 3-Dockerfile/s 'de tanımlanan görüntüleri oluşturun, 4-(isteğe bağlı) oluşturma hizmetleri Docker-Compose. yıml dosyasında, 5-çalıştırma kapsayıcısı veya Docker-Compose uygulaması, 6-uygulamanızı veya mikro hizmetleri, 7-depoyu depoya gönderin ve tekrarlayın.</span><span class="sxs-lookup"><span data-stu-id="705e9-404">The development process for Docker apps: 1 - Code your App, 2 - Write Dockerfile/s, 3 - Create images defined at Dockerfile/s, 4 - (optional) Compose services in the docker-compose.yml file, 5 - Run container or docker-compose app, 6 - Test your app or microservices, 7 - Push to repo and repeat.</span></span>
:::image-end:::

<span data-ttu-id="705e9-405">**Şekil 5-15**.</span><span class="sxs-lookup"><span data-stu-id="705e9-405">**Figure 5-15**.</span></span> <span data-ttu-id="705e9-406">Visual Studio ile geliştirme yaparken Basitleştirilmiş iş akışı</span><span class="sxs-lookup"><span data-stu-id="705e9-406">Simplified workflow when developing with Visual Studio</span></span>

<span data-ttu-id="705e9-407">Ayrıca, adım 2 ' yi (projelerinize Docker desteği ekleme) yalnızca bir kez gerçekleştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="705e9-407">In addition, you need to perform step 2 (adding Docker support to your projects) just once.</span></span> <span data-ttu-id="705e9-408">Bu nedenle, iş akışı herhangi bir geliştirme için .NET kullanırken normal geliştirme görevlerinizde benzerdir.</span><span class="sxs-lookup"><span data-stu-id="705e9-408">Therefore, the workflow is similar to your usual development tasks when using .NET for any other development.</span></span> <span data-ttu-id="705e9-409">Kapakların (görüntü oluşturma işlemi, kullandığınız temel görüntüler, kapsayıcıların dağıtımı vb.) altında neler olduğunu bilmeniz gerekir ve bazı durumlarda, davranışları özelleştirmek için Dockerfile veya Docker-Compose. yıml dosyasını düzenlemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="705e9-409">You need to know what is going on under the covers (the image build process, what base images you're using, deployment of containers, etc.) and sometimes you will also need to edit the Dockerfile or docker-compose.yml file to customize behaviors.</span></span> <span data-ttu-id="705e9-410">Ancak işin çoğu Visual Studio kullanarak büyük ölçüde basitleştirilerek çok daha üretken hale getirirsiniz.</span><span class="sxs-lookup"><span data-stu-id="705e9-410">But most of the work is greatly simplified by using Visual Studio, making you a lot more productive.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="705e9-411">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="705e9-411">Additional resources</span></span>

- <span data-ttu-id="705e9-412">**Steve Lasker. Visual Studio ile .NET Docker geliştirme (2017)** </span><span class="sxs-lookup"><span data-stu-id="705e9-412">**Steve Lasker. .NET Docker Development with Visual Studio (2017)** </span></span>\
  <https://channel9.msdn.com/Events/Visual-Studio/Visual-Studio-2017-Launch/T111>

## <a name="using-powershell-commands-in-a-dockerfile-to-set-up-windows-containers"></a><span data-ttu-id="705e9-413">Windows kapsayıcıları ayarlamak için bir Dockerfile içinde PowerShell komutlarını kullanma</span><span class="sxs-lookup"><span data-stu-id="705e9-413">Using PowerShell commands in a Dockerfile to set up Windows Containers</span></span>

<span data-ttu-id="705e9-414">[Windows kapsayıcıları](/virtualization/windowscontainers/about/index) , mevcut Windows uygulamalarınızı Docker görüntülerine dönüştürmenize ve bunları Docker ekosisteminin geri kalanıyla aynı araçlarla dağıtmanıza imkan tanır.</span><span class="sxs-lookup"><span data-stu-id="705e9-414">[Windows Containers](/virtualization/windowscontainers/about/index) allow you to convert your existing Windows applications into Docker images and deploy them with the same tools as the rest of the Docker ecosystem.</span></span> <span data-ttu-id="705e9-415">Windows kapsayıcılarını kullanmak için aşağıdaki örnekte gösterildiği gibi, Dockerfile içinde PowerShell komutlarını çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="705e9-415">To use Windows Containers, you run PowerShell commands in the Dockerfile, as shown in the following example:</span></span>

```dockerfile
FROM mcr.microsoft.com/windows/servercore
LABEL Description="IIS" Vendor="Microsoft" Version="10"
RUN powershell -Command Add-WindowsFeature Web-Server
CMD [ "ping", "localhost", "-t" ]
```

<span data-ttu-id="705e9-416">Bu durumda, bir Windows Server çekirdek temel görüntüsü (başlangıç ayarı) kullanıyorsunuz ve IIS 'yi bir PowerShell komutuyla (çalıştırma ayarı) kullanıyoruz.</span><span class="sxs-lookup"><span data-stu-id="705e9-416">In this case, we are using a Windows Server Core base image (the FROM setting) and installing IIS with a PowerShell command (the RUN setting).</span></span> <span data-ttu-id="705e9-417">Benzer bir şekilde, ASP.NET 4. x, .NET 4,6 veya başka herhangi bir Windows yazılımı gibi ek bileşenler ayarlamak için de PowerShell komutlarını kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="705e9-417">In a similar way, you could also use PowerShell commands to set up additional components like ASP.NET 4.x, .NET 4.6, or any other Windows software.</span></span> <span data-ttu-id="705e9-418">Örneğin, bir Dockerfile dosyasında aşağıdaki komut ASP.NET 4,5 ' u ayarlar:</span><span class="sxs-lookup"><span data-stu-id="705e9-418">For example, the following command in a Dockerfile sets up ASP.NET 4.5:</span></span>

```dockerfile
RUN powershell add-windowsfeature web-asp-net45
```

### <a name="additional-resources"></a><span data-ttu-id="705e9-419">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="705e9-419">Additional resources</span></span>

- <span data-ttu-id="705e9-420">**ASPNET-Docker/Dockerfile.**</span><span class="sxs-lookup"><span data-stu-id="705e9-420">**aspnet-docker/Dockerfile.**</span></span> <span data-ttu-id="705e9-421">Windows özelliklerini dahil etmek için dockerfile 'ları destekliyor 'tan çalıştırılacak örnek PowerShell komutları. </span><span class="sxs-lookup"><span data-stu-id="705e9-421">Example PowerShell commands to run from dockerfiles to include Windows features.</span></span>\
  <https://github.com/Microsoft/aspnet-docker/blob/master/4.7.1-windowsservercore-ltsc2016/runtime/Dockerfile>

>[!div class="step-by-step"]
><span data-ttu-id="705e9-422">[Önceki](index.md) 
> [Sonraki](../multi-container-microservice-net-applications/index.md)</span><span class="sxs-lookup"><span data-stu-id="705e9-422">[Previous](index.md)
[Next](../multi-container-microservice-net-applications/index.md)</span></span>
