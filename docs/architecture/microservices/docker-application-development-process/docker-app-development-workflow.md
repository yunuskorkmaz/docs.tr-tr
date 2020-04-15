---
title: Docker uygulamaları için geliştirme iş akışı
description: Docker tabanlı uygulamalar geliştirmek için iş akışının ayrıntılarını anlayın. Adım adım başlayın ve Dockerfiles'ı optimize etmek ve Visual Studio'yu kullanırken kullanılabilen basitleştirilmiş iş akışıyla bitirmek için bazı ayrıntılara girin.
ms.date: 01/30/2020
ms.openlocfilehash: 2f380c840e186c345f9222aa6b0cf1097a74874e
ms.sourcegitcommit: c91110ef6ee3fedb591f3d628dc17739c4a7071e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/15/2020
ms.locfileid: "81389196"
---
# <a name="development-workflow-for-docker-apps"></a><span data-ttu-id="e0410-104">Docker uygulamaları için geliştirme iş akışı</span><span class="sxs-lookup"><span data-stu-id="e0410-104">Development workflow for Docker apps</span></span>

<span data-ttu-id="e0410-105">Uygulama geliştirme yaşam döngüsü, uygulamayı tercih ettiğiniz dili kullanarak kodlayıp yerel olarak test ettiğiniz bir geliştirici olarak bilgisayarınızda başlar.</span><span class="sxs-lookup"><span data-stu-id="e0410-105">The application development life cycle starts at your computer, as a developer, where you code the application using your preferred language and test it locally.</span></span> <span data-ttu-id="e0410-106">Bu iş akışıyla, hangi dili, çerçeveyi ve platformu seçerseniz seçin, Docker kapsayıcılarını her zaman geliştiriyor ve test ediyorsunuz, ancak bunu yerel olarak yapıyorsunuz.</span><span class="sxs-lookup"><span data-stu-id="e0410-106">With this workflow, no matter which language, framework, and platform you choose, you're always developing and testing Docker containers, but doing so locally.</span></span>

<span data-ttu-id="e0410-107">Her kapsayıcı (Docker görüntüsünün bir örneği) aşağıdaki bileşenleri içerir:</span><span class="sxs-lookup"><span data-stu-id="e0410-107">Each container (an instance of a Docker image) includes the following components:</span></span>

- <span data-ttu-id="e0410-108">Bir işletim sistemi seçimi, örneğin, bir Linux dağıtımı, Windows Nano Server veya Windows Server Core.</span><span class="sxs-lookup"><span data-stu-id="e0410-108">An operating system selection, for example, a Linux distribution, Windows Nano Server, or Windows Server Core.</span></span>

- <span data-ttu-id="e0410-109">Geliştirme sırasında eklenen dosyalar, örneğin, kaynak kodu ve uygulama ikilileri.</span><span class="sxs-lookup"><span data-stu-id="e0410-109">Files added during development, for example, source code and application binaries.</span></span>

- <span data-ttu-id="e0410-110">Ortam ayarları ve bağımlılıklar gibi yapılandırma bilgileri.</span><span class="sxs-lookup"><span data-stu-id="e0410-110">Configuration information, such as environment settings and dependencies.</span></span>

## <a name="workflow-for-developing-docker-container-based-applications"></a><span data-ttu-id="e0410-111">Docker konteyner tabanlı uygulamalar geliştirmek için iş akışı</span><span class="sxs-lookup"><span data-stu-id="e0410-111">Workflow for developing Docker container-based applications</span></span>

<span data-ttu-id="e0410-112">Bu bölümde Docker kapsayıcı tabanlı uygulamalar için *iç döngü* geliştirme iş akışı açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="e0410-112">This section describes the *inner-loop* development workflow for Docker container-based applications.</span></span> <span data-ttu-id="e0410-113">İç döngü iş akışı, üretim dağıtımına kadar dahil edilebilen ve yalnızca geliştiricinin bilgisayarında yapılan geliştirme çalışmalarına odaklanan daha geniş DevOps iş akışını dikkate almadığı anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="e0410-113">The inner-loop workflow means it's not considering the broader DevOps workflow, which can include up to production deployment, and just focuses on the development work done on the developer's computer.</span></span> <span data-ttu-id="e0410-114">Bu adımlar yalnızca bir kez yapıldığından, ortamı ayarlamak için ilk adımlar dahil değildir.</span><span class="sxs-lookup"><span data-stu-id="e0410-114">The initial steps to set up the environment aren't included, since those steps are done only once.</span></span>

<span data-ttu-id="e0410-115">Bir uygulama kendi hizmetleri ve ek kitaplıklar (bağımlılıklar) oluşur.</span><span class="sxs-lookup"><span data-stu-id="e0410-115">An application is composed of your own services plus additional libraries (dependencies).</span></span> <span data-ttu-id="e0410-116">Aşağıda, Şekil 5-1'de gösterildiği gibi, docker uygulaması yaparken genellikle attığınız temel adımlar verebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e0410-116">The following are the basic steps you usually take when building a Docker application, as illustrated in Figure 5-1.</span></span>

:::image type="complex" source="./media/docker-app-development-workflow/life-cycle-containerized-apps-docker-cli.png" alt-text="Kapsayıcı bir uygulama oluşturmak için gereken 7 adımı gösteren diyagram.":::
<span data-ttu-id="e0410-118">Docker uygulamaları için geliştirme süreci: 1 - Uygulamanızı kodlayın, 2 - Dockerfile/s yazın, 3 - Dockerfile/s'de tanımlanan görüntüleri oluşturun, 4 - (isteğe bağlı) Docker-compose.yml dosyasında hizmetleri oluşturun, 5 - Konteyner veya docker-create app, 6 - Uygulamanızı veya mikro hizmetleri test edin, 7 - Repo'yu tekrarlamak için bastırın ve tekrarlayın.</span><span class="sxs-lookup"><span data-stu-id="e0410-118">The development process for Docker apps: 1 - Code your App, 2 - Write Dockerfile/s, 3 - Create images defined at Dockerfile/s, 4 - (optional) Compose services in the docker-compose.yml file, 5 - Run container or docker-compose app, 6 - Test your app or microservices, 7 - Push to repo and repeat.</span></span>
:::image-end:::

<span data-ttu-id="e0410-119">**Şekil 5-1.**</span><span class="sxs-lookup"><span data-stu-id="e0410-119">**Figure 5-1.**</span></span> <span data-ttu-id="e0410-120">Docker konteyner uygulamaları geliştirmek için adım adım iş akışı</span><span class="sxs-lookup"><span data-stu-id="e0410-120">Step-by-step workflow for developing Docker containerized apps</span></span>

<span data-ttu-id="e0410-121">Bu bölümde, tüm bu süreç ayrıntılı ve her büyük adım bir Visual Studio ortamı odaklanarak açıklanır.</span><span class="sxs-lookup"><span data-stu-id="e0410-121">In this section, this whole process is detailed and every major step is explained by focusing on a Visual Studio environment.</span></span>

<span data-ttu-id="e0410-122">Bir düzenleyici/CLI geliştirme yaklaşımı (örneğin, visual studio code artı Docker CLI macOS veya Windows'da) kullanırken, genellikle Visual Studio'yu kullandığınızdan daha ayrıntılı olarak her adımı bilmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="e0410-122">When you're using an editor/CLI development approach (for example, Visual Studio Code plus Docker CLI on macOS or Windows), you need to know every step, generally in more detail than if you're using Visual Studio.</span></span> <span data-ttu-id="e0410-123">CLI ortamında çalışma hakkında daha fazla bilgi için, Microsoft Platformları ve Araçları ile e-kitap [Containerized Docker Uygulama yaşam döngüsüne](https://aka.ms/dockerlifecycleebook/)bakın.</span><span class="sxs-lookup"><span data-stu-id="e0410-123">For more information about working in a CLI environment, see the e-book [Containerized Docker Application lifecycle with Microsoft Platforms and Tools](https://aka.ms/dockerlifecycleebook/).</span></span>

<span data-ttu-id="e0410-124">Visual Studio 2019'u kullanırken, bu adımların çoğu sizin için işlenir ve bu da üretkenliğinizi önemli ölçüde artırır.</span><span class="sxs-lookup"><span data-stu-id="e0410-124">When you're using Visual Studio 2019, many of those steps are handled for you, which dramatically improves your productivity.</span></span> <span data-ttu-id="e0410-125">Bu özellikle Visual Studio 2019'u kullanırken ve çoklu konteyner uygulamalarını hedefliyorsanız geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="e0410-125">This is especially true when you're using Visual Studio 2019 and targeting multi-container applications.</span></span> <span data-ttu-id="e0410-126">Örneğin, tek bir fare tıklamasıyla Visual `Dockerfile` `docker-compose.yml` Studio, uygulamanızın yapılandırmasıyla projelerinizi ve dosyayı ve dosyayı ekler.</span><span class="sxs-lookup"><span data-stu-id="e0410-126">For instance, with just one mouse click, Visual Studio adds the `Dockerfile` and `docker-compose.yml` file to your projects with the configuration for your application.</span></span> <span data-ttu-id="e0410-127">Visual Studio'da uygulamayı çalıştırdığınızda, Docker görüntüsünü oluşturur ve çoklu konteyner uygulamasını doğrudan Docker'da çalıştırAr; hatta aynı anda birden fazla kapsayıcı hata ayıklama sağlar.</span><span class="sxs-lookup"><span data-stu-id="e0410-127">When you run the application in Visual Studio, it builds the Docker image and runs the multi-container application directly in Docker; it even allows you to debug several containers at once.</span></span> <span data-ttu-id="e0410-128">Bu özellikler geliştirme hızınızı artırır.</span><span class="sxs-lookup"><span data-stu-id="e0410-128">These features will boost your development speed.</span></span>

<span data-ttu-id="e0410-129">Ancak Visual Studio'nun bu adımları otomatik hale getiriyor olması Docker'ın altında neler olup bittiğini bilmeniz edemek değildir.</span><span class="sxs-lookup"><span data-stu-id="e0410-129">However, just because Visual Studio makes those steps automatic doesn't mean that you don't need to know what's going on underneath with Docker.</span></span> <span data-ttu-id="e0410-130">Bu nedenle, aşağıdaki kılavuz her adımı ayrıntıları.</span><span class="sxs-lookup"><span data-stu-id="e0410-130">Therefore, the following guidance details every step.</span></span>

![Adım 1 için görüntü.](./media/docker-app-development-workflow/step-1-code-your-app.png)

## <a name="step-1-start-coding-and-create-your-initial-application-or-service-baseline"></a><span data-ttu-id="e0410-132">1. Adım.</span><span class="sxs-lookup"><span data-stu-id="e0410-132">Step 1.</span></span> <span data-ttu-id="e0410-133">Kodlamaya başlayın ve ilk uygulama nızı veya hizmet temelinizi oluşturun</span><span class="sxs-lookup"><span data-stu-id="e0410-133">Start coding and create your initial application or service baseline</span></span>

<span data-ttu-id="e0410-134">Docker uygulaması geliştirmek, Docker olmadan bir uygulama geliştirme şeklinize benzer.</span><span class="sxs-lookup"><span data-stu-id="e0410-134">Developing a Docker application is similar to the way you develop an application without Docker.</span></span> <span data-ttu-id="e0410-135">Aradaki fark, Docker için geliştirme sırasında, uygulamanızı veya hizmetlerinizi yerel ortamınızda Docker kapsayıcıları içinde (Docker tarafından linux VM kurulumu veya Windows Kapsayıcıları kullanıyorsanız doğrudan Windows tarafından bir Linux VM kurulumu) dağıtıyor ve test ediyor olmasıdır.</span><span class="sxs-lookup"><span data-stu-id="e0410-135">The difference is that while developing for Docker, you're deploying and testing your application or services running within Docker containers in your local environment (either a Linux VM setup by Docker or directly Windows if using Windows Containers).</span></span>

### <a name="set-up-your-local-environment-with-visual-studio"></a><span data-ttu-id="e0410-136">Visual Studio ile yerel ortamınızı ayarlama</span><span class="sxs-lookup"><span data-stu-id="e0410-136">Set up your local environment with Visual Studio</span></span>

<span data-ttu-id="e0410-137">Başlamak için, aşağıdaki talimatlarda açıklandığı gibi Windows için [Docker Community Edition (CE)](https://docs.docker.com/docker-for-windows/) yüklü olduğundan emin olun:</span><span class="sxs-lookup"><span data-stu-id="e0410-137">To begin, make sure you have [Docker Community Edition (CE)](https://docs.docker.com/docker-for-windows/) for Windows installed, as explained in the following instructions:</span></span>

[<span data-ttu-id="e0410-138">Windows için Docker CE ile başlayın</span><span class="sxs-lookup"><span data-stu-id="e0410-138">Get started with Docker CE for Windows</span></span>](https://docs.docker.com/docker-for-windows/)

<span data-ttu-id="e0410-139">Buna ek olarak, Şekil 5-2'de gösterildiği gibi **.NET Core çapraz platform geliştirme** iş yükünün yüklü olduğu Visual Studio 2019 sürüm 16.4 veya daha sonrasına ihtiyacınız vardır.</span><span class="sxs-lookup"><span data-stu-id="e0410-139">In addition, you need Visual Studio 2019 version 16.4 or later, with the **.NET Core cross-platform development** workload installed, as shown in Figure 5-2.</span></span>

![.NET Core çapraz platform geliştirme seçiminin ekran görüntüsü.](./media/docker-app-development-workflow/dotnet-core-cross-platform-development.png)

<span data-ttu-id="e0410-141">**Şekil 5-2**.</span><span class="sxs-lookup"><span data-stu-id="e0410-141">**Figure 5-2**.</span></span> <span data-ttu-id="e0410-142">Visual Studio 2019 kurulumu sırasında **.NET Core platform lar arası geliştirme** iş yükünü seçme</span><span class="sxs-lookup"><span data-stu-id="e0410-142">Selecting the **.NET Core cross-platform development** workload during Visual Studio 2019 setup</span></span>

<span data-ttu-id="e0410-143">Docker'ı uygulamanızda etkinleştirmeden ve Docker'da dağıtmadan ve test etmeden önce uygulamanızı düz .NET'te (genellikle kapsayıcıkullanmayı planlıyorsanız .NET Core'da) kodlamaya başlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e0410-143">You can start coding your application in plain .NET (usually in .NET Core if you're planning to use containers) even before enabling Docker in your application and deploying and testing in Docker.</span></span> <span data-ttu-id="e0410-144">Ancak, docker üzerinde mümkün olan en kısa sürede çalışmaya başlamanız önerilir, çünkü bu gerçek ortam olacaktır ve herhangi bir sorun en kısa sürede keşfedilebilir.</span><span class="sxs-lookup"><span data-stu-id="e0410-144">However, it is recommended that you start working on Docker as soon as possible, because that will be the real environment and any issues can be discovered as soon as possible.</span></span> <span data-ttu-id="e0410-145">Visual Studio Docker ile çalışmayı o kadar kolaylaştırır ki, Visual Studio'dan çoklu konteyner uygulamalarını hata ayıklarken en iyi örnek neredeyse saydam dır.</span><span class="sxs-lookup"><span data-stu-id="e0410-145">This is encouraged because Visual Studio makes it so easy to work with Docker that it almost feels transparent—the best example when debugging multi-container applications from Visual Studio.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="e0410-146">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="e0410-146">Additional resources</span></span>

- <span data-ttu-id="e0410-147">**Windows için Docker CE ile başlayın** </span><span class="sxs-lookup"><span data-stu-id="e0410-147">**Get started with Docker CE for Windows** </span></span>\
  <https://docs.docker.com/docker-for-windows/>

- <span data-ttu-id="e0410-148">**Visual Studio 2019** </span><span class="sxs-lookup"><span data-stu-id="e0410-148">**Visual Studio 2019** </span></span>\
  [https://visualstudio.microsoft.com/downloads/](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019)

![Adım 2 için görüntü.](./media/docker-app-development-workflow/step-2-write-dockerfile.png)

## <a name="step-2-create-a-dockerfile-related-to-an-existing-net-base-image"></a><span data-ttu-id="e0410-150">2. Adım</span><span class="sxs-lookup"><span data-stu-id="e0410-150">Step 2.</span></span> <span data-ttu-id="e0410-151">Varolan bir .NET taban görüntüsüyle ilgili dockerdosyası oluşturma</span><span class="sxs-lookup"><span data-stu-id="e0410-151">Create a Dockerfile related to an existing .NET base image</span></span>

<span data-ttu-id="e0410-152">Oluşturmak istediğiniz her özel görüntü için bir Dockerfile gerekir; Ayrıca, Visual Studio'dan otomatik olarak veya Docker CLI'yi (docker run and docker-compose komutları) kullanarak otomatik olarak dağıtın, dağıtılacak her bir konteyner için bir Dockerfile'a da ihtiyacınız vardır.</span><span class="sxs-lookup"><span data-stu-id="e0410-152">You need a Dockerfile for each custom image you want to build; you also need a Dockerfile for each container to be deployed, whether you deploy automatically from Visual Studio or manually using the Docker CLI (docker run and docker-compose commands).</span></span> <span data-ttu-id="e0410-153">Uygulamanız tek bir özel hizmet içeriyorsa, tek bir Dockerfile gerekir.</span><span class="sxs-lookup"><span data-stu-id="e0410-153">If your application contains a single custom service, you need a single Dockerfile.</span></span> <span data-ttu-id="e0410-154">Uygulamanız birden çok hizmet içeriyorsa (mikro hizmetler mimarisinde olduğu gibi), her hizmet için bir Dockerfile gerekir.</span><span class="sxs-lookup"><span data-stu-id="e0410-154">If your application contains multiple services (as in a microservices architecture), you need one Dockerfile for each service.</span></span>

<span data-ttu-id="e0410-155">Dockerfile, uygulamanızın veya hizmetinizin kök klasörüne yerleştirilir.</span><span class="sxs-lookup"><span data-stu-id="e0410-155">The Dockerfile is placed in the root folder of your application or service.</span></span> <span data-ttu-id="e0410-156">Docker'a uygulamanızı veya hizmetinizi bir kapsayıcıda nasıl ayarlayıp çalıştıreceğini söyleyen komutları içerir.</span><span class="sxs-lookup"><span data-stu-id="e0410-156">It contains the commands that tell Docker how to set up and run your application or service in a container.</span></span> <span data-ttu-id="e0410-157">Kod halinde bir Dockerfile oluşturabilir ve .NET bağımlılıklarınizle birlikte projenize ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e0410-157">You can manually create a Dockerfile in code and add it to your project along with your .NET dependencies.</span></span>

<span data-ttu-id="e0410-158">Visual Studio ve Docker için araçları ile, bu görev sadece birkaç fare tıklaması gerektirir.</span><span class="sxs-lookup"><span data-stu-id="e0410-158">With Visual Studio and its tools for Docker, this task requires only a few mouse clicks.</span></span> <span data-ttu-id="e0410-159">Visual Studio 2019'da yeni bir proje oluşturduğunuzda, Şekil 5-3'te gösterildiği gibi **Docker Desteğini Etkinleştir**adlı bir seçenek vardır.</span><span class="sxs-lookup"><span data-stu-id="e0410-159">When you create a new project in Visual Studio 2019, there's an option named **Enable Docker Support**, as shown in Figure 5-3.</span></span>

![Docker Destek onay kutusunu etkinleştir'i gösteren ekran görüntüsü.](./media/docker-app-development-workflow/enable-docker-support-check-box.png)

<span data-ttu-id="e0410-161">**Şekil 5-3**.</span><span class="sxs-lookup"><span data-stu-id="e0410-161">**Figure 5-3**.</span></span> <span data-ttu-id="e0410-162">Visual Studio 2019'da yeni bir ASP.NET Core projesi oluştururken Docker Desteğini etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="e0410-162">Enabling Docker Support when creating a new ASP.NET Core project in Visual Studio 2019</span></span>

<span data-ttu-id="e0410-163">Ayrıca, **Solution Explorer'daki** projeyi sağ tıklatarak ve Şekil 5-4'te gösterildiği gibi**Docker Desteği Ekle'yi** **Add** > seçerek mevcut bir ASP.NET Core web uygulaması projesinde Docker desteğini de etkinleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e0410-163">You can also enable Docker support on an existing ASP.NET Core web app project by right-clicking the project in **Solution Explorer** and selecting **Add** > **Docker Support...**, as shown in Figure 5-4.</span></span>

![Ekle menüsünde Docker Destek seçeneğini gösteren ekran görüntüsü.](./media/docker-app-development-workflow/add-docker-support-option.png)

<span data-ttu-id="e0410-165">**Şekil 5-4**.</span><span class="sxs-lookup"><span data-stu-id="e0410-165">**Figure 5-4**.</span></span> <span data-ttu-id="e0410-166">Mevcut bir Visual Studio 2019 projesinde Docker desteğini etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="e0410-166">Enabling Docker support in an existing Visual Studio 2019 project</span></span>

<span data-ttu-id="e0410-167">Bu eylem, projeye gerekli yapılandırmayla bir *Dockerfile* ekler ve yalnızca ASP.NET Core projelerinde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="e0410-167">This action adds a *Dockerfile* to the project with the required configuration, and is only available on ASP.NET Core projects.</span></span>

<span data-ttu-id="e0410-168">Benzer bir şekilde, Visual Studio `docker-compose.yml` da seçenek > Konteyner **Orchestrator Destek ekle**ile tüm çözüm için bir dosya ekleyebilirsiniz ... . Adım 4'te, bu seçeneği daha ayrıntılı olarak inceleyeceğiz.</span><span class="sxs-lookup"><span data-stu-id="e0410-168">In a similar fashion, Visual Studio can also add a `docker-compose.yml` file for the whole solution with the option **Add > Container Orchestrator Support...**. In step 4, we'll explore this option in greater detail.</span></span>

### <a name="using-an-existing-official-net-docker-image"></a><span data-ttu-id="e0410-169">Varolan bir resmi .NET Docker görüntüsünü kullanma</span><span class="sxs-lookup"><span data-stu-id="e0410-169">Using an existing official .NET Docker image</span></span>

<span data-ttu-id="e0410-170">Genellikle [Docker Hub](https://hub.docker.com/) kayıt defteri gibi resmi bir depodan aldığınız temel görüntünün üzerine kapsayıcınız için özel bir resim oluşturursunuz.</span><span class="sxs-lookup"><span data-stu-id="e0410-170">You usually build a custom image for your container on top of a base image you get from an official repository like the [Docker Hub](https://hub.docker.com/) registry.</span></span> <span data-ttu-id="e0410-171">Visual Studio'da Docker desteğini etkinleştirdiğinizde örtünün altında tam olarak böyle olur.</span><span class="sxs-lookup"><span data-stu-id="e0410-171">That is precisely what happens under the covers when you enable Docker support in Visual Studio.</span></span> <span data-ttu-id="e0410-172">Dockerfile'ınız varolan `dotnet/core/aspnet` bir görüntü kullanır.</span><span class="sxs-lookup"><span data-stu-id="e0410-172">Your Dockerfile will use an existing `dotnet/core/aspnet` image.</span></span>

<span data-ttu-id="e0410-173">Daha önce seçtiğiniz çerçeve ye ve işletim sistemi ne bağlı olarak hangi Docker görüntüleri ve repos kullanabileceğinizi açıkladı.</span><span class="sxs-lookup"><span data-stu-id="e0410-173">Earlier we explained which Docker images and repos you can use, depending on the framework and OS you have chosen.</span></span> <span data-ttu-id="e0410-174">Örneğin, ASP.NET Core (Linux veya Windows) kullanmak istiyorsanız, `mcr.microsoft.com/dotnet/core/aspnet:3.1`kullanılacak görüntü .</span><span class="sxs-lookup"><span data-stu-id="e0410-174">For instance, if you want to use ASP.NET Core (Linux or Windows), the image to use is `mcr.microsoft.com/dotnet/core/aspnet:3.1`.</span></span> <span data-ttu-id="e0410-175">Bu nedenle, sadece konteyner için kullanacağınız temel Docker görüntü belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="e0410-175">Therefore, you just need to specify what base Docker image you will use for your container.</span></span> <span data-ttu-id="e0410-176">Bunu Dockerfile'ınıza ekleyerek `FROM mcr.microsoft.com/dotnet/core/aspnet:3.1` yaparsınız.</span><span class="sxs-lookup"><span data-stu-id="e0410-176">You do that by adding `FROM mcr.microsoft.com/dotnet/core/aspnet:3.1` to your Dockerfile.</span></span> <span data-ttu-id="e0410-177">Bu işlem Visual Studio tarafından otomatik olarak gerçekleştirilir, ancak sürümü güncellerseniz, bu değeri güncellersiniz.</span><span class="sxs-lookup"><span data-stu-id="e0410-177">This will be automatically performed by Visual Studio, but if you were to update the version, you update this value.</span></span>

<span data-ttu-id="e0410-178">Docker Hub'ın sürüm numarasıyla resmi bir .NET görüntü deposunun kullanılması, aynı dil özelliklerinin tüm makinelerde (geliştirme, test ve üretim dahil) kullanılabilmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="e0410-178">Using an official .NET image repository from Docker Hub with a version number ensures that the same language features are available on all machines (including development, testing, and production).</span></span>

<span data-ttu-id="e0410-179">Aşağıdaki örnekte, ASP.NET Core kapsayıcısı için örnek bir Dockerfile gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="e0410-179">The following example shows a sample Dockerfile for an ASP.NET Core container.</span></span>

```Dockerfile
FROM mcr.microsoft.com/dotnet/core/aspnet:3.1
ARG source
WORKDIR /app
EXPOSE 80
COPY ${source:-obj/Docker/publish} .
ENTRYPOINT ["dotnet", " MySingleContainerWebApp.dll "]
```

<span data-ttu-id="e0410-180">Bu durumda, görüntü resmi ASP.NET Core Docker görüntüsünün (Linux ve Windows için çoklu kemer) 3.1 sürümüne dayanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="e0410-180">In this case, the image is based on version 3.1 of the official ASP.NET Core Docker image (multi-arch for Linux and Windows).</span></span> <span data-ttu-id="e0410-181">Bu ayardır. `FROM mcr.microsoft.com/dotnet/core/aspnet:3.1`</span><span class="sxs-lookup"><span data-stu-id="e0410-181">This is the setting `FROM mcr.microsoft.com/dotnet/core/aspnet:3.1`.</span></span> <span data-ttu-id="e0410-182">(Bu temel resim hakkında daha fazla bilgi için [.NET Core Docker Resim](https://hub.docker.com/_/microsoft-dotnet-core/) sayfasına bakın.) Dockerfile'da, Docker'a çalışma zamanında kullanacağınız TCP bağlantı noktasını dinlemesi için talimat vermeniz gerekir (bu durumda, port 80, EXPOSE ayarı ile yapılandırıldığı gibi).</span><span class="sxs-lookup"><span data-stu-id="e0410-182">(For more information about this base image, see the [.NET Core Docker Image](https://hub.docker.com/_/microsoft-dotnet-core/) page.) In the Dockerfile, you also need to instruct Docker to listen on the TCP port you will use at runtime (in this case, port 80, as configured with the EXPOSE setting).</span></span>

<span data-ttu-id="e0410-183">Kullandığınız dile ve çerçeveye bağlı olarak Dockerfile'da ek yapılandırma ayarları belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e0410-183">You can specify additional configuration settings in the Dockerfile, depending on the language and framework you're using.</span></span> <span data-ttu-id="e0410-184">Örneğin, entrypoint satırı `["dotnet", "MySingleContainerWebApp.dll"]` Docker'a bir .NET Core uygulaması çalıştırmasını söyler.</span><span class="sxs-lookup"><span data-stu-id="e0410-184">For instance, the ENTRYPOINT line with `["dotnet", "MySingleContainerWebApp.dll"]` tells Docker to run a .NET Core application.</span></span> <span data-ttu-id="e0410-185">.NET uygulamasını oluşturmak ve çalıştırmak için SDK ve .NET Core CLI 'yi (dotnet CLI) kullanıyorsanız, bu ayar farklı olacaktır.</span><span class="sxs-lookup"><span data-stu-id="e0410-185">If you're using the SDK and the .NET Core CLI (dotnet CLI) to build and run the .NET application, this setting would be different.</span></span> <span data-ttu-id="e0410-186">Alt satırda ENTRYPOINT satırı ve diğer ayarları uygulamanız için seçtiğiniz dil ve platforma bağlı olarak farklı olacaktır.</span><span class="sxs-lookup"><span data-stu-id="e0410-186">The bottom line is that the ENTRYPOINT line and other settings will be different depending on the language and platform you choose for your application.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="e0410-187">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="e0410-187">Additional resources</span></span>

- <span data-ttu-id="e0410-188">**.NET Çekirdek Uygulamaları için Docker Görüntüleri Oluşturma** </span><span class="sxs-lookup"><span data-stu-id="e0410-188">**Building Docker Images for .NET Core Applications** </span></span>\
  [https://docs.microsoft.com/dotnet/core/docker/building-net-docker-images](/aspnet/core/host-and-deploy/docker/building-net-docker-images)

- <span data-ttu-id="e0410-189">**Kendi resminizi oluşturun.**</span><span class="sxs-lookup"><span data-stu-id="e0410-189">**Build your own image**.</span></span> <span data-ttu-id="e0410-190">Resmi Docker belgelerinde.</span><span class="sxs-lookup"><span data-stu-id="e0410-190">In the official Docker documentation.</span></span>\
  <https://docs.docker.com/engine/tutorials/dockerimages/>

- <span data-ttu-id="e0410-191">**.NET Konteyner Görüntüleri ile güncel kalma** </span><span class="sxs-lookup"><span data-stu-id="e0410-191">**Staying up-to-date with .NET Container Images** </span></span>\
  <https://devblogs.microsoft.com/dotnet/staying-up-to-date-with-net-container-images/>

- <span data-ttu-id="e0410-192">**.NET ve Docker'ı Birlikte Kullanma - DockerCon 2018 Güncellemesi** </span><span class="sxs-lookup"><span data-stu-id="e0410-192">**Using .NET and Docker Together - DockerCon 2018 Update** </span></span>\
  <https://devblogs.microsoft.com/dotnet/using-net-and-docker-together-dockercon-2018-update/>

### <a name="using-multi-arch-image-repositories"></a><span data-ttu-id="e0410-193">Çok kemerli görüntü depolarını kullanma</span><span class="sxs-lookup"><span data-stu-id="e0410-193">Using multi-arch image repositories</span></span>

<span data-ttu-id="e0410-194">Tek bir repo, Linux görüntüsü ve Windows görüntüsü gibi platform türevlerini içerebilir.</span><span class="sxs-lookup"><span data-stu-id="e0410-194">A single repo can contain platform variants, such as a Linux image and a Windows image.</span></span> <span data-ttu-id="e0410-195">Bu özellik, Microsoft (temel görüntü oluşturucular) gibi satıcıların birden çok platformu (Linux ve Windows) kapsayacak şekilde tek bir repo oluşturmasına olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="e0410-195">This feature allows vendors like Microsoft (base image creators) to create a single repo to cover multiple platforms (that is Linux and Windows).</span></span> <span data-ttu-id="e0410-196">Örneğin, Docker Hub kayıt defterinde bulunan [dotnet/core](https://hub.docker.com/_/microsoft-dotnet-core/) deposu, aynı repo adını kullanarak Linux ve Windows Nano Server için destek sağlar.</span><span class="sxs-lookup"><span data-stu-id="e0410-196">For example, the [dotnet/core](https://hub.docker.com/_/microsoft-dotnet-core/) repository available in the Docker Hub registry provides support for Linux and Windows Nano Server by using the same repo name.</span></span>

<span data-ttu-id="e0410-197">Bir etiket belirtirseniz, aşağıdaki durumlarda olduğu gibi açık olan bir platformu hedeflemek:</span><span class="sxs-lookup"><span data-stu-id="e0410-197">If you specify a tag, targeting a platform that is explicit like in the following cases:</span></span>

- `mcr.microsoft.com/dotnet/core/aspnet:3.1-buster-slim` \
  <span data-ttu-id="e0410-198">Hedefler: .NET Core 3.1 yalnızca Linux'ta çalışma zamanı</span><span class="sxs-lookup"><span data-stu-id="e0410-198">Targets: .NET Core 3.1 runtime-only on Linux</span></span>

- `mcr.microsoft.com/dotnet/core/aspnet:3.1-nanoserver-1909` \
  <span data-ttu-id="e0410-199">Hedefler: .NET Core 3.1 yalnızca Windows Nano Server'da çalışma zamanı</span><span class="sxs-lookup"><span data-stu-id="e0410-199">Targets: .NET Core 3.1 runtime-only on Windows Nano Server</span></span>

<span data-ttu-id="e0410-200">Ancak, aynı görüntü adını belirtirseniz, aynı etiketle bile, çok kemerli görüntüler `aspnet` (resim gibi) aşağıdaki örnekte gösterildiği gibi, dağıttAcağınız Docker ana bilgisayar işletim sistemi'ne bağlı olarak Linux veya Windows sürümünü kullanır:</span><span class="sxs-lookup"><span data-stu-id="e0410-200">But, if you specify the same image name, even with the same tag, the multi-arch images (like the `aspnet` image) will use the Linux or Windows version depending on the Docker host OS you're deploying, as shown in the following example:</span></span>

- `mcr.microsoft.com/dotnet/core/aspnet:3.1` \
  <span data-ttu-id="e0410-201">Çok kemerli: .NET Core 3.1 docker ana bilgisayar işletim sistemi bağlı olarak Linux veya Windows Nano Server üzerinde yalnızca çalışma süresi</span><span class="sxs-lookup"><span data-stu-id="e0410-201">Multi-arch: .NET Core 3.1 runtime-only on Linux or Windows Nano Server depending on the Docker host OS</span></span>

<span data-ttu-id="e0410-202">Bu şekilde, bir Windows ana bilgisayardan bir görüntü çektiğinde, Windows varyantını çeker ve linux ana bilgisayardan aynı görüntü adını çekerek Linux varyantını çeker.</span><span class="sxs-lookup"><span data-stu-id="e0410-202">This way, when you pull an image from a Windows host, it will pull the Windows variant, and pulling the same image name from a Linux host will pull the Linux variant.</span></span>

### <a name="multi-stage-builds-in-dockerfile"></a><span data-ttu-id="e0410-203">Dockerfile'de çok aşamalı yapılar</span><span class="sxs-lookup"><span data-stu-id="e0410-203">Multi-stage builds in Dockerfile</span></span>

<span data-ttu-id="e0410-204">Dockerfile toplu komut dosyasına benzer.</span><span class="sxs-lookup"><span data-stu-id="e0410-204">The Dockerfile is similar to a batch script.</span></span> <span data-ttu-id="e0410-205">Makineyi komut satırından ayarlamanız gerekirse yapacağınız şeye benzer.</span><span class="sxs-lookup"><span data-stu-id="e0410-205">Similar to what you would do if you had to set up the machine from the command line.</span></span>

<span data-ttu-id="e0410-206">Bu ilk bağlamı oluşturan bir temel görüntü ile başlar, bu başlangıç dosya sistemi gibi, bu ana işletim sisteminin üstüne oturur.</span><span class="sxs-lookup"><span data-stu-id="e0410-206">It starts with a base image that sets up the initial context, it's like the startup filesystem, that sits on top of the host OS.</span></span> <span data-ttu-id="e0410-207">Bir işletim sistemi değil, ama kapsayıcı içinde "" işletim sistemi gibi düşünebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e0410-207">It's not an OS, but you can think of it like "the" OS inside the container.</span></span>

<span data-ttu-id="e0410-208">Her komut satırının yürütülmesi, bir öncekinden gelen değişikliklerle dosya sisteminde yeni bir katman oluşturur, böylece birleştiğinde ortaya çıkan dosya sistemini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="e0410-208">The execution of every command line creates a new layer on the filesystem with the changes from the previous one, so that, when combined, produce the resulting filesystem.</span></span>

<span data-ttu-id="e0410-209">Her yeni katman bir öncekinin üstüne "dayanıyor" ve ortaya çıkan görüntü boyutu her komutla arttığı için, örneğin Bir uygulama oluşturmak ve yayınlamak için gereken SDK'yı eklemek zorunda kalırlarsa görüntüler çok büyük olabilir.</span><span class="sxs-lookup"><span data-stu-id="e0410-209">Since every new layer "rests" on top of the previous one and the resulting image size increases with every command, images can get very large if they have to include, for example, the SDK needed to build and publish an application.</span></span>

<span data-ttu-id="e0410-210">Bu çok aşamalı yapılar arsa içine almak (Docker 17,05 ve daha yüksek) kendi sihirli yapmaktır.</span><span class="sxs-lookup"><span data-stu-id="e0410-210">This is where multi-stage builds get into the plot (from Docker 17.05 and higher) to do their magic.</span></span>

<span data-ttu-id="e0410-211">Temel fikir, Dockerfile yürütme işlemini aşamalı olarak ayırabildiğiniz, bir aşamanın bir veya daha fazla komutla izlenen ilk görüntü olduğu ve son aşamanın son görüntü boyutunu belirleyebileceğidir.</span><span class="sxs-lookup"><span data-stu-id="e0410-211">The core idea is that you can separate the Dockerfile execution process in stages, where a stage is an initial image followed by one or more commands, and the last stage determines the final image size.</span></span>

<span data-ttu-id="e0410-212">Kısacası, çok aşamalı yapılar, oluşturmanın farklı "aşamalarda" bölünmesine izin verir ve ardından yalnızca ara aşamalardan yalnızca ilgili dizinleri alarak son görüntüyü birleştirir.</span><span class="sxs-lookup"><span data-stu-id="e0410-212">In short, multi-stage builds allow splitting the creation in different "phases" and then assemble the final image taking only the relevant directories from the intermediate stages.</span></span> <span data-ttu-id="e0410-213">Bu özelliği kullanmak için genel strateji:</span><span class="sxs-lookup"><span data-stu-id="e0410-213">The general strategy to use this feature is:</span></span>

1. <span data-ttu-id="e0410-214">Uygulamayı oluşturmak ve bir klasöre yayınlamak için gereken her şey ile temel SDK görüntüsü (ne kadar büyük olursa olsun) kullanın ve ardından</span><span class="sxs-lookup"><span data-stu-id="e0410-214">Use a base SDK image (doesn't matter how large), with everything needed to build and publish the application to a folder and then</span></span>

2. <span data-ttu-id="e0410-215">Temel, küçük, yalnızca çalışma zamanı görüntü kullanın ve yayımlama klasörünü önceki aşamadan kopyalayarak küçük bir son görüntü oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e0410-215">Use a base, small, runtime-only image and copy the publishing folder from the previous stage to produce a small final image.</span></span>

<span data-ttu-id="e0410-216">Muhtemelen çok aşamalı anlamak için en iyi yolu ayrıntılı bir Dockerfile geçiyor, satır satır, bu yüzden bir projeye Docker desteği eklerken Visual Studio tarafından oluşturulan ilk Dockerfile ile başlayalım ve daha sonra bazı optimizasyonlar içine alacak.</span><span class="sxs-lookup"><span data-stu-id="e0410-216">Probably the best way to understand multi-stage is going through a Dockerfile in detail, line by line, so let's begin with the initial Dockerfile created by Visual Studio when adding Docker support to a project and will get into some optimizations later.</span></span>

<span data-ttu-id="e0410-217">İlk Dockerfile şuna benzer:</span><span class="sxs-lookup"><span data-stu-id="e0410-217">The initial Dockerfile might look something like this:</span></span>

```Dockerfile
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

<span data-ttu-id="e0410-218">Ve bunlar da satır satır detaylar:</span><span class="sxs-lookup"><span data-stu-id="e0410-218">And these are the details, line by line:</span></span>

- <span data-ttu-id="e0410-219">**Satır #1:** Bir "küçük" çalışma zamanı yalnızca temel görüntü ile bir sahne başlayın, referans için **temel** çağırın.</span><span class="sxs-lookup"><span data-stu-id="e0410-219">**Line #1:** Begin a stage with a "small" runtime-only base image, call it **base** for reference.</span></span>

- <span data-ttu-id="e0410-220">**Satır #2:** Görüntüdeki **/uygulama** dizinini oluşturun.</span><span class="sxs-lookup"><span data-stu-id="e0410-220">**Line #2:** Create the **/app** directory in the image.</span></span>

- <span data-ttu-id="e0410-221">**Satır #3:** Bağlantı noktası **80'i**açığa çıkar.</span><span class="sxs-lookup"><span data-stu-id="e0410-221">**Line #3:** Expose port **80**.</span></span>

- <span data-ttu-id="e0410-222">**Satır #5:** Bina /yayımlama için "büyük" görüntü ile yeni bir aşamaya başlayın.</span><span class="sxs-lookup"><span data-stu-id="e0410-222">**Line #5:** Begin a new stage with the "large" image for building/publishing.</span></span> <span data-ttu-id="e0410-223">Referans için **inşa** deyin.</span><span class="sxs-lookup"><span data-stu-id="e0410-223">Call it **build** for reference.</span></span>

- <span data-ttu-id="e0410-224">**Satır #6:** Görüntüde dizin **/src** oluşturun.</span><span class="sxs-lookup"><span data-stu-id="e0410-224">**Line #6:** Create directory **/src** in the image.</span></span>

- <span data-ttu-id="e0410-225">**Satır #7:** Satır 16'ya kadar, paketleri daha sonra geri yükleyebilmek için başvurulan **.csproj** proje dosyalarını kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="e0410-225">**Line #7:** Up to line 16, copy referenced **.csproj** project files to be able to restore packages later.</span></span>

- <span data-ttu-id="e0410-226">**Satır #17:** **Catalog.API** projesi ve başvurulan projeler için paketleri geri yükleyin.</span><span class="sxs-lookup"><span data-stu-id="e0410-226">**Line #17:** Restore packages for the **Catalog.API** project and the referenced projects.</span></span>

- <span data-ttu-id="e0410-227">**Satır #18:** **Çözüm için tüm dizin ağacını** **(.dockerignore** dosyasında yer alan dosyalar/dizinler hariç) görüntüdeki **/src** dizinine kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="e0410-227">**Line #18:** Copy **all directory tree for the solution** (except the files/directories included in the **.dockerignore** file) to the **/src** directory in the image.</span></span>

- <span data-ttu-id="e0410-228">**Satır #19:** Geçerli klasörü **Catalog.API** projesiyle değiştirin.</span><span class="sxs-lookup"><span data-stu-id="e0410-228">**Line #19:** Change the current folder to the **Catalog.API** project.</span></span>

- <span data-ttu-id="e0410-229">**Satır #20:** Projeyi (ve diğer proje bağımlılıklarını) oluşturun ve görüntüdeki **/uygulama** dizinine çıktı oluşturun.</span><span class="sxs-lookup"><span data-stu-id="e0410-229">**Line #20:** Build the project (and other project dependencies) and output to the **/app** directory in the image.</span></span>

- <span data-ttu-id="e0410-230">**Satır #22:** Yapıdan devam eden yeni bir aşamaya başlayın.</span><span class="sxs-lookup"><span data-stu-id="e0410-230">**Line #22:** Begin a new stage continuing from the build.</span></span> <span data-ttu-id="e0410-231">Referans için **yayımlayın** deyin.</span><span class="sxs-lookup"><span data-stu-id="e0410-231">Call it **publish** for reference.</span></span>

- <span data-ttu-id="e0410-232">**Satır #23:** Projeyi (ve bağımlılıkları) yayımlayın ve çıktıyı görüntüdeki **/uygulama** dizinine yayınlayın.</span><span class="sxs-lookup"><span data-stu-id="e0410-232">**Line #23:** Publish the project (and dependencies) and output to the **/app** directory in the image.</span></span>

- <span data-ttu-id="e0410-233">**Satır #25:** **Üsten** devam eden yeni bir aşamaya başlayın ve **buna son**deyin.</span><span class="sxs-lookup"><span data-stu-id="e0410-233">**Line #25:** Begin a new stage continuing from **base** and call it **final**.</span></span>

- <span data-ttu-id="e0410-234">**Satır #26:** Geçerli dizini **/app**olarak değiştirin.</span><span class="sxs-lookup"><span data-stu-id="e0410-234">**Line #26:** Change the current directory to **/app**.</span></span>

- <span data-ttu-id="e0410-235">**Satır #27:** **/app** dizinini sahne **yayımından** geçerli dizine kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="e0410-235">**Line #27:** Copy the **/app** directory from stage **publish** to the current directory.</span></span>

- <span data-ttu-id="e0410-236">**Satır #28:** Kapsayıcı başlatıldığında çalışacak komutu tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="e0410-236">**Line #28:** Define the command to run when the container is started.</span></span>

<span data-ttu-id="e0410-237">Şimdi, eShopOnContainers durumunda, Linux kapkaplarında tam bir çözüm oluşturmak için yaklaşık 22 dakika veya daha fazla anlamına gelen tüm işlem performansını artırmak için bazı optimizasyonları inceleyelim.</span><span class="sxs-lookup"><span data-stu-id="e0410-237">Now let's explore some optimizations to improve the whole process performance that, in the case of eShopOnContainers, means about 22 minutes or more to build the complete solution in Linux containers.</span></span>

<span data-ttu-id="e0410-238">Docker'ın katman önbellek özelliğinden yararlanırsınız, ki bu oldukça basittir: temel görüntü ve komutlar daha önce yürütülmüş bazı komutlarla aynıysa, yalnızca komutları yürütmeye gerek kalmadan ortaya çıkan katmanı kullanabilir ve böylece biraz zaman kazandırır.</span><span class="sxs-lookup"><span data-stu-id="e0410-238">You'll take advantage of Docker's layer cache feature, which is quite simple: if the base image and the commands are the same as some previously executed, it can just use the resulting layer without the need to execute the commands, thus saving some time.</span></span>

<span data-ttu-id="e0410-239">Yani, **inşa** aşamasında odaklanalım, satır 5-6 çoğunlukla aynıdır, ama satır 7-17 eShopOnContainers her hizmet için farklıdır, bu yüzden her zaman yürütmek zorunda, ancak satır 7-16 değişti:</span><span class="sxs-lookup"><span data-stu-id="e0410-239">So, let's focus on the **build** stage, lines 5-6 are mostly the same, but lines 7-17 are different for every service from eShopOnContainers, so they have to execute every single time, however if you changed lines 7-16 to:</span></span>

```Dockerfile
COPY . .
```

<span data-ttu-id="e0410-240">Sonra her hizmet için sadece aynı olurdu, tüm çözüm kopyalamak ve daha büyük bir katman yaratacak ama:</span><span class="sxs-lookup"><span data-stu-id="e0410-240">Then it would be just the same for every service, it would copy the whole solution and would create a larger layer but:</span></span>

1. <span data-ttu-id="e0410-241">Kopyalama işlemi yalnızca ilk kez yürütülür (ve bir dosya değiştirilirse yeniden oluşturma) ve önbelleği diğer tüm hizmetler için kullanır ve</span><span class="sxs-lookup"><span data-stu-id="e0410-241">The copy process would only be executed the first time (and when rebuilding if a file is changed) and would use the cache for all other services and</span></span>

2. <span data-ttu-id="e0410-242">Daha büyük görüntü bir ara aşamada oluştuğundan, son görüntü boyutunu etkilemez.</span><span class="sxs-lookup"><span data-stu-id="e0410-242">Since the larger image occurs in an intermediate stage it, doesn't affect the final image size.</span></span>

<span data-ttu-id="e0410-243">Bir sonraki önemli optimizasyon, `restore` eShopOnContainers'ın her hizmeti için de farklı olan satır 17'de gerçekleştirilen komutu içerir.</span><span class="sxs-lookup"><span data-stu-id="e0410-243">The next significant optimization involves the `restore` command executed in line 17, which is also different for every service of eShopOnContainers.</span></span> <span data-ttu-id="e0410-244">Bu satırı sadece olarak değiştirirseniz:</span><span class="sxs-lookup"><span data-stu-id="e0410-244">If you change that line to just:</span></span>

```Dockerfile
RUN dotnet restore
```

<span data-ttu-id="e0410-245">Tüm çözüm için paketleri geri, ama sonra tekrar, sadece bir kez yerine mevcut strateji ile 15 kez yapardı.</span><span class="sxs-lookup"><span data-stu-id="e0410-245">It would restore the packages for the whole solution, but then again, it would do it just once, instead of the 15 times with the current strategy.</span></span>

<span data-ttu-id="e0410-246">Ancak, `dotnet restore` yalnızca klasörde tek bir proje veya çözüm dosyası varsa çalışır, bu nedenle bunu başarmak biraz daha karmaşıktır ve çok fazla ayrıntıya girmeden çözmenin yolu şudur:</span><span class="sxs-lookup"><span data-stu-id="e0410-246">However, `dotnet restore` only runs if there's a single project or solution file in the folder, so achieving this is a bit more complicated and the way to solve it, without getting into too many details, is this:</span></span>

1. <span data-ttu-id="e0410-247">**.dockerignore**için aşağıdaki satırları ekleyin:</span><span class="sxs-lookup"><span data-stu-id="e0410-247">Add the following lines to **.dockerignore**:</span></span>

   - <span data-ttu-id="e0410-248">`*.sln`, ana klasör ağacındaki tüm çözüm dosyalarını yoksaymak</span><span class="sxs-lookup"><span data-stu-id="e0410-248">`*.sln`, to ignore all solution files in the main folder tree</span></span>

   - <span data-ttu-id="e0410-249">`!eShopOnContainers-ServicesAndWebApps.sln`, yalnızca bu çözüm dosyasını eklemek için.</span><span class="sxs-lookup"><span data-stu-id="e0410-249">`!eShopOnContainers-ServicesAndWebApps.sln`, to include only this solution file.</span></span>

2. <span data-ttu-id="e0410-250">Argüman `/ignoreprojectextensions:.dcproj` dahil `dotnet restore`, bu yüzden de docker-compose proje yok sayar ve sadece eShopOnContainers-ServicesAndWebApps çözümü için paketleri geri yükler.</span><span class="sxs-lookup"><span data-stu-id="e0410-250">Include the `/ignoreprojectextensions:.dcproj` argument to `dotnet restore`, so it also ignores the docker-compose project and only restores the packages for the eShopOnContainers-ServicesAndWebApps solution.</span></span>

<span data-ttu-id="e0410-251">Son optimizasyon için, sadece satır 20 gereksiz olduğunu olur, satır 23 de uygulama oluşturur ve gelir, özünde, satır 20 hemen sonra, bu yüzden başka bir zaman alıcı komut gider.</span><span class="sxs-lookup"><span data-stu-id="e0410-251">For the final optimization, it just happens that line 20 is redundant, as line 23 also builds the application and comes, in essence, right after line 20, so there goes another time-consuming command.</span></span>

<span data-ttu-id="e0410-252">Ortaya çıkan dosya daha sonra:</span><span class="sxs-lookup"><span data-stu-id="e0410-252">The resulting file is then:</span></span>

```Dockerfile
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

### <a name="creating-your-base-image-from-scratch"></a><span data-ttu-id="e0410-253">Temel görüntünüzsıfırdan oluşturma</span><span class="sxs-lookup"><span data-stu-id="e0410-253">Creating your base image from scratch</span></span>

<span data-ttu-id="e0410-254">Sıfırdan kendi Docker temel görüntü oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e0410-254">You can create your own Docker base image from scratch.</span></span> <span data-ttu-id="e0410-255">Bu senaryo Docker ile başlayan biri için önerilmez, ancak kendi temel görüntünüzün belirli bitlerini ayarlamak istiyorsanız, bunu yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e0410-255">This scenario is not recommended for someone who is starting with Docker, but if you want to set the specific bits of your own base image, you can do so.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="e0410-256">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="e0410-256">Additional resources</span></span>

- <span data-ttu-id="e0410-257">**Multi-arch .NET Core görüntüleri**.</span><span class="sxs-lookup"><span data-stu-id="e0410-257">**Multi-arch .NET Core images**.</span></span>\
  <https://github.com/dotnet/announcements/issues/14>

- <span data-ttu-id="e0410-258">**Temel görüntü oluşturun.**</span><span class="sxs-lookup"><span data-stu-id="e0410-258">**Create a base image**.</span></span> <span data-ttu-id="e0410-259">Resmi Docker belgeleri.</span><span class="sxs-lookup"><span data-stu-id="e0410-259">Official Docker documentation.</span></span>\
  <https://docs.docker.com/develop/develop-images/baseimages/>

![Adım 3 için görüntü.](./media/docker-app-development-workflow/step-3-create-dockerfile-defined-images.png)

## <a name="step-3-create-your-custom-docker-images-and-embed-your-application-or-service-in-them"></a><span data-ttu-id="e0410-261">3. Adım</span><span class="sxs-lookup"><span data-stu-id="e0410-261">Step 3.</span></span> <span data-ttu-id="e0410-262">Özel Docker resimlerinizi oluşturun ve uygulamanızı veya hizmetinizi bunlara göm</span><span class="sxs-lookup"><span data-stu-id="e0410-262">Create your custom Docker images and embed your application or service in them</span></span>

<span data-ttu-id="e0410-263">Uygulamanızdaki her hizmet için ilgili bir resim oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="e0410-263">For each service in your application, you need to create a related image.</span></span> <span data-ttu-id="e0410-264">Uygulamanız tek bir hizmet veya web uygulamasından oluşuyorsa, tek bir görüntüye ihtiyacınız vardır.</span><span class="sxs-lookup"><span data-stu-id="e0410-264">If your application is made up of a single service or web application, you just need a single image.</span></span>

<span data-ttu-id="e0410-265">Docker görüntülerinin Visual Studio'da sizin için otomatik olarak üretilediğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="e0410-265">Note that the Docker images are built automatically for you in Visual Studio.</span></span> <span data-ttu-id="e0410-266">Aşağıdaki adımlar yalnızca düzenleyici/CLI iş akışı için gereklidir ve altında ne olduğu hakkında netlik için açıklanmıştır.</span><span class="sxs-lookup"><span data-stu-id="e0410-266">The following steps are only needed for the editor/CLI workflow and explained for clarity about what happens underneath.</span></span>

<span data-ttu-id="e0410-267">Bir geliştirici olarak, tamamlanmış bir özelliği itene veya kaynak denetim sisteminizde (örneğin, GitHub'a) geçene kadar yerel olarak geliştirmeniz ve test etmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="e0410-267">You, as a developer, need to develop and test locally until you push a completed feature or change to your source control system (for example, to GitHub).</span></span> <span data-ttu-id="e0410-268">Bu, Docker görüntülerini oluşturmanız ve kapsayıcıları yerel bir Docker ana bilgisayara (Windows veya Linux VM) dağıtmanız ve bu yerel kapsayıcılara karşı çalıştırmanız, test etmeniz ve hata ayıklamanız gerektiği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="e0410-268">This means that you need to create the Docker images and deploy containers to a local Docker host (Windows or Linux VM) and run, test, and debug against those local containers.</span></span>

<span data-ttu-id="e0410-269">Docker CLI ve Dockerfile'ınızı kullanarak yerel ortamınızda özel bir görüntü oluşturmak için Şekil 5-5'te olduğu gibi docker build komutunu kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e0410-269">To create a custom image in your local environment by using Docker CLI and your Dockerfile, you can use the docker build command, as in Figure 5-5.</span></span>

![Docker build komutunun konsol çıktısını gösteren ekran görüntüsü.](./media/docker-app-development-workflow/run-docker-build-command.png)

<span data-ttu-id="e0410-271">**Şekil 5-5**.</span><span class="sxs-lookup"><span data-stu-id="e0410-271">**Figure 5-5**.</span></span> <span data-ttu-id="e0410-272">Özel Docker görüntüsü oluşturma</span><span class="sxs-lookup"><span data-stu-id="e0410-272">Creating a custom Docker image</span></span>

<span data-ttu-id="e0410-273">İsteğe bağlı olarak, proje klasöründen doğrudan docker build çalıştırmak yerine, önce gerekli .NET kitaplıkları ve ikilileri çalıştırarak `dotnet publish`dağıtılabilir bir klasör oluşturabilir ve ardından komutu `docker build` kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e0410-273">Optionally, instead of directly running docker build from the project folder, you can first generate a deployable folder with the required .NET libraries and binaries by running `dotnet publish`, and then use the `docker build` command.</span></span>

<span data-ttu-id="e0410-274">Bu, adında `cesardl/netcore-webapi-microservice-docker:first`bir Docker görüntüsü oluşturur.</span><span class="sxs-lookup"><span data-stu-id="e0410-274">This will create a Docker image with the name `cesardl/netcore-webapi-microservice-docker:first`.</span></span> <span data-ttu-id="e0410-275">Bu durumda: birincisi belirli bir sürümü temsil eden bir etikettir.</span><span class="sxs-lookup"><span data-stu-id="e0410-275">In this case, :first is a tag representing a specific version.</span></span> <span data-ttu-id="e0410-276">Oluşturduğunuz Docker uygulaması için oluşturmanız gereken her özel görüntü için bu adımı yineleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e0410-276">You can repeat this step for each custom image you need to create for your composed Docker application.</span></span>

<span data-ttu-id="e0410-277">Bir uygulama birden çok kapsayıcıdan yapıldığında (yani çok kapsayıcılı bir uygulamadır), ilgili docker-compose.yml dosyalarında açıkta bulunan meta verileri kullanarak ilgili tüm görüntüleri tek bir komutla oluşturmak için `docker-compose up --build` komutu da kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e0410-277">When an application is made of multiple containers (that is, it is a multi-container application), you can also use the `docker-compose up --build` command to build all the related images with a single command by using the metadata exposed in the related docker-compose.yml files.</span></span>

<span data-ttu-id="e0410-278">Mevcut görüntüleri Şekil 5-6'da gösterildiği gibi docker images komutunu kullanarak yerel deponuzda bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e0410-278">You can find the existing images in your local repository by using the docker images command, as shown in Figure 5-6.</span></span>

![Varolan görüntüleri gösteren komut docker görüntüleri konsol çıkışı.](./media/docker-app-development-workflow/view-existing-images-with-docker-images.png)

<span data-ttu-id="e0410-280">**Şekil 5-6.**</span><span class="sxs-lookup"><span data-stu-id="e0410-280">**Figure 5-6.**</span></span> <span data-ttu-id="e0410-281">Docker görüntüleri komutunu kullanarak varolan görüntüleri görüntüleme</span><span class="sxs-lookup"><span data-stu-id="e0410-281">Viewing existing images using the docker images command</span></span>

### <a name="creating-docker-images-with-visual-studio"></a><span data-ttu-id="e0410-282">Visual Studio ile Docker görüntüleri oluşturma</span><span class="sxs-lookup"><span data-stu-id="e0410-282">Creating Docker images with Visual Studio</span></span>

<span data-ttu-id="e0410-283">Docker destekli bir proje oluşturmak için Visual Studio'yı kullandığınızda, açıkça bir görüntü oluşturmazsınız.</span><span class="sxs-lookup"><span data-stu-id="e0410-283">When you use Visual Studio to create a project with Docker support, you don't explicitly create an image.</span></span> <span data-ttu-id="e0410-284">Bunun yerine, dockerized uygulama veya hizmeti çalıştırmak için **F5** (veya **Ctrl-F5)** tuşuna bastığında görüntü sizin için oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="e0410-284">Instead, the image is created for you when you press **F5** (or **Ctrl-F5**) to run the dockerized application or service.</span></span> <span data-ttu-id="e0410-285">Bu adım Visual Studio'da otomatiktir ve bunun olduğunu görmezsiniz, ancak altında neler olup bittiğini bilmeniz önemlidir.</span><span class="sxs-lookup"><span data-stu-id="e0410-285">This step is automatic in Visual Studio and you won't see it happen, but it's important that you know what's going on underneath.</span></span>

![İsteğe bağlı Adım 4 için görüntü.](./media/docker-app-development-workflow/step-4-define-services-docker-compose-yml.png)

## <a name="step-4-define-your-services-in-docker-composeyml-when-building-a-multi-container-docker-application"></a><span data-ttu-id="e0410-287">4. Adım.</span><span class="sxs-lookup"><span data-stu-id="e0410-287">Step 4.</span></span> <span data-ttu-id="e0410-288">Çok konteynerli Docker uygulaması oluştururken docker-compose.yml'de hizmetlerinizi tanımlayın</span><span class="sxs-lookup"><span data-stu-id="e0410-288">Define your services in docker-compose.yml when building a multi-container Docker application</span></span>

<span data-ttu-id="e0410-289">[Docker-compose.yml](https://docs.docker.com/compose/compose-file/) dosyası, dağıtım komutları içeren oluşturulmuş bir uygulama olarak dağıtılacak ilgili hizmetler kümesini tanımlamanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="e0410-289">The [docker-compose.yml](https://docs.docker.com/compose/compose-file/) file lets you define a set of related services to be deployed as a composed application with deployment commands.</span></span> <span data-ttu-id="e0410-290">Ayrıca bağımlılık ilişkilerini ve çalışma zamanı yapılandırmasını da yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="e0410-290">It also configures its dependency relations and run-time configuration.</span></span>

<span data-ttu-id="e0410-291">Docker-compose.yml dosyasını kullanmak için, aşağıdaki örnekte benzer içeriğe sahip ana veya kök çözüm klasörünüzde dosyaoluşturmanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="e0410-291">To use a docker-compose.yml file, you need to create the file in your main or root solution folder, with content similar to that in the following example:</span></span>

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
    image: mssql-server-linux:latest
    environment:
      - SA_PASSWORD=Pass@word
      - ACCEPT_EULA=Y
    ports:
      - "5433:1433"
```

<span data-ttu-id="e0410-292">Bu docker-compose.yml dosyası basitleştirilmiş ve birleştirilmiş bir sürümüdür.</span><span class="sxs-lookup"><span data-stu-id="e0410-292">This docker-compose.yml file is a simplified and merged version.</span></span> <span data-ttu-id="e0410-293">Her zaman gerekli olan her kapsayıcı için statik yapılandırma verileri (özel görüntünün adı gibi) ve bağlantı dizesi gibi dağıtım ortamına bağlı olabilecek yapılandırma bilgileri içerir.</span><span class="sxs-lookup"><span data-stu-id="e0410-293">It contains static configuration data for each container (like the name of the custom image), which is always required, and configuration information that might depend on the deployment environment, like the connection string.</span></span> <span data-ttu-id="e0410-294">Daha sonraki bölümlerde, docker-compose.yml yapılandırmasını birden çok docker-compose dosyasına nasıl böleceğinizi ve ortam adedine ve yürütme türüne (hata ayıklama veya sürüm) bağlı olarak değerleri geçersiz kılmayı öğreneceksiniz.</span><span class="sxs-lookup"><span data-stu-id="e0410-294">In later sections, you will learn how to split the docker-compose.yml configuration into multiple docker-compose files and override values depending on the environment and execution type (debug or release).</span></span>

<span data-ttu-id="e0410-295">Docker-compose.yml dosya örneği dört hizmeti `webmvc` tanımlar: hizmet (bir web`ordering-api` uygulaması), iki mikro hizmet (ve), `basket-api`ve bir veri kaynağı kapsayıcı, `sqldata`Linux için SQL Server'a dayalı bir kapsayıcı olarak çalışır.</span><span class="sxs-lookup"><span data-stu-id="e0410-295">The docker-compose.yml file example defines four services: the `webmvc` service (a web application), two microservices (`ordering-api` and `basket-api`), and one data source container, `sqldata`, based on SQL Server for Linux running as a container.</span></span> <span data-ttu-id="e0410-296">Her hizmet bir kapsayıcı olarak dağıtılır, bu nedenle her hizmet için bir Docker görüntüsü gerekir.</span><span class="sxs-lookup"><span data-stu-id="e0410-296">Each service will be deployed as a container, so a Docker image is required for each.</span></span>

<span data-ttu-id="e0410-297">Docker-compose.yml dosyası, yalnızca hangi kapsayıcıların kullanıldığını değil, aynı zamanda bunların tek tek nasıl yapılandırıldığını da belirtir.</span><span class="sxs-lookup"><span data-stu-id="e0410-297">The docker-compose.yml file specifies not only what containers are being used, but how they are individually configured.</span></span> <span data-ttu-id="e0410-298">Örneğin, .yml dosyasındaki `webmvc` kapsayıcı tanımı:</span><span class="sxs-lookup"><span data-stu-id="e0410-298">For instance, the `webmvc` container definition in the .yml file:</span></span>

- <span data-ttu-id="e0410-299">Önceden oluşturulmuş `eshop/web:latest` bir görüntü kullanır.</span><span class="sxs-lookup"><span data-stu-id="e0410-299">Uses a pre-built `eshop/web:latest` image.</span></span> <span data-ttu-id="e0410-300">Ancak, docker-com-yürütmenin bir parçası olarak oluşturulacak görüntüyü, bir yapıya dayalı ek bir yapılandırmayla da yapılandırabilirsiniz: docker-compose dosyasındaki bölüm.</span><span class="sxs-lookup"><span data-stu-id="e0410-300">However, you could also configure the image to be built as part of the docker-compose execution with an additional configuration based on a build: section in the docker-compose file.</span></span>

- <span data-ttu-id="e0410-301">İki ortam değişkenini (CatalogUrl ve OrderingUrl) başharfe getirir.</span><span class="sxs-lookup"><span data-stu-id="e0410-301">Initializes two environment variables (CatalogUrl and OrderingUrl).</span></span>

- <span data-ttu-id="e0410-302">Konteynerüzerindeki 80 portu ana makinedeki harici bağlantı noktasına 80 iletir.</span><span class="sxs-lookup"><span data-stu-id="e0410-302">Forwards the exposed port 80 on the container to the external port 80 on the host machine.</span></span>

- <span data-ttu-id="e0410-303">Web uygulamasını katalog ve sipariş hizmetine depends_on ayarı ile bağlar.</span><span class="sxs-lookup"><span data-stu-id="e0410-303">Links the web app to the catalog and ordering service with the depends_on setting.</span></span> <span data-ttu-id="e0410-304">Bu, hizmetin bu hizmetler başlatılana kadar beklemesine neden olur.</span><span class="sxs-lookup"><span data-stu-id="e0410-304">This causes the service to wait until those services are started.</span></span>

<span data-ttu-id="e0410-305">Mikro hizmetlerin ve çoklu konteyner uygulamalarının nasıl uygulanacağını ele aldığımızda docker-compose.yml dosyasını daha sonraki bir bölümde tekrar ziyaret edeceğiz.</span><span class="sxs-lookup"><span data-stu-id="e0410-305">We will revisit the docker-compose.yml file in a later section when we cover how to implement microservices and multi-container apps.</span></span>

### <a name="working-with-docker-composeyml-in-visual-studio-2019"></a><span data-ttu-id="e0410-306">Visual Studio 2019'da docker-compose.yml ile çalışma</span><span class="sxs-lookup"><span data-stu-id="e0410-306">Working with docker-compose.yml in Visual Studio 2019</span></span>

<span data-ttu-id="e0410-307">Daha önce de belirttiğimiz gibi, bir projeye Dockerfile eklemenin yanı sıra, Visual Studio 2017 (15.8 sürümünden itibaren) Docker Compose için bir çözüme orkestratör desteği ekleyebilir.</span><span class="sxs-lookup"><span data-stu-id="e0410-307">Besides adding a Dockerfile to a project, as we mentioned before, Visual Studio 2017 (from version 15.8 on) can add orchestrator support for Docker Compose to a solution.</span></span>

<span data-ttu-id="e0410-308">Şekil 5-7'de gösterildiği gibi konteyner orkestratör desteği eklediğinizde, Visual Studio ilk kez proje için Dockerfile oluşturur ve çözümünüzde birkaç `docker-compose*.yml` genel dosyayla birlikte yeni bir (hizmet bölümü) proje oluşturur ve projeyi bu dosyalara ekler.</span><span class="sxs-lookup"><span data-stu-id="e0410-308">When you add container orchestrator support, as shown in Figure 5-7, for the first time, Visual Studio creates the Dockerfile for the project and creates a new (service section) project in your solution with several global `docker-compose*.yml` files, and then adds the project to those files.</span></span> <span data-ttu-id="e0410-309">Daha sonra docker-compose.yml dosyalarını açabilir ve ek özelliklerle güncelleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e0410-309">You can then open the docker-compose.yml files and update them with additional features.</span></span>

<span data-ttu-id="e0410-310">Docker-compose.yml dosyasına eklemek istediğiniz her projeyi bu işlem formunu yinelemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="e0410-310">You have to repeat this operation form every project you want to include in the docker-compose.yml file.</span></span>

<span data-ttu-id="e0410-311">Bu yazının yazıldığı sırada Visual Studio, **Docker Compose** ve **Kubernetes/Helm** orkestratörlerini desteklemektedir.</span><span class="sxs-lookup"><span data-stu-id="e0410-311">At the time of this writing, Visual Studio supports **Docker Compose** and **Kubernetes/Helm** orchestrators.</span></span>

![Proje bağlamı menüsünde Konteyner Orchestrator Desteği seçeneğini gösteren ekran görüntüsü.](./media/docker-app-development-workflow/add-container-orchestrator-support-option.png)

<span data-ttu-id="e0410-313">**Şekil 5-7**.</span><span class="sxs-lookup"><span data-stu-id="e0410-313">**Figure 5-7**.</span></span> <span data-ttu-id="e0410-314">Visual Studio 2019'da ASP.NET Core projesine sağ tıklayarak Docker desteği ekleme</span><span class="sxs-lookup"><span data-stu-id="e0410-314">Adding Docker support in Visual Studio 2019 by right-clicking an ASP.NET Core project</span></span>

<span data-ttu-id="e0410-315">Visual Studio'da çözümünüze orchestrator desteği ekledikten sonra, Solution Explorer'da `docker-compose.dcproj` Şekil 5-8'de gösterildiği gibi eklenen docker-compose.yml dosyalarını içeren yeni bir düğüm de görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="e0410-315">After you add orchestrator support to your solution in Visual Studio, you will also see a new node (in the `docker-compose.dcproj` project file) in Solution Explorer that contains the added docker-compose.yml files, as shown in Figure 5-8.</span></span>

![Solution Explorer'da docker-compose düğümünün ekran görüntüsü.](./media/docker-app-development-workflow/docker-compose-tree-node.png)

<span data-ttu-id="e0410-317">**Şekil 5-8**.</span><span class="sxs-lookup"><span data-stu-id="e0410-317">**Figure 5-8**.</span></span> <span data-ttu-id="e0410-318">Visual Studio 2019 Solution Explorer'da eklenen **docker-compose** ağaç düğümü</span><span class="sxs-lookup"><span data-stu-id="e0410-318">The **docker-compose** tree node added in Visual Studio 2019 Solution Explorer</span></span>

<span data-ttu-id="e0410-319">`docker-compose up` Komutu kullanarak tek bir docker-compose.yml dosyası ile çok kapsayıcı uygulama dağıtabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e0410-319">You could deploy a multi-container application with a single docker-compose.yml file by using the `docker-compose up` command.</span></span> <span data-ttu-id="e0410-320">Ancak Visual Studio, ortama (geliştirme veya üretim) ve yürütme türüne (sürüm veya hata ayıklama) bağlı olarak değerleri geçersiz kılabilmeniz için bunlardan bir grup ekler.</span><span class="sxs-lookup"><span data-stu-id="e0410-320">However, Visual Studio adds a group of them so you can override values depending on the environment (development or production) and execution type (release or debug).</span></span> <span data-ttu-id="e0410-321">Bu özellik sonraki bölümlerde açıklanacaktır.</span><span class="sxs-lookup"><span data-stu-id="e0410-321">This capability will be explained in later sections.</span></span>

![Adım 5 için görüntü.](./media/docker-app-development-workflow/step-5-run-containers-compose-app.png)

## <a name="step-5-build-and-run-your-docker-application"></a><span data-ttu-id="e0410-323">5. Adım.</span><span class="sxs-lookup"><span data-stu-id="e0410-323">Step 5.</span></span> <span data-ttu-id="e0410-324">Docker uygulamanızı oluşturun ve çalıştırın</span><span class="sxs-lookup"><span data-stu-id="e0410-324">Build and run your Docker application</span></span>

<span data-ttu-id="e0410-325">Uygulamanızda yalnızca tek bir kapsayıcı varsa, docker ana bilgisayarınıza (VM veya fiziksel sunucu) dağıtarak uygulamayı çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e0410-325">If your application only has a single container, you can run it by deploying it to your Docker host (VM or physical server).</span></span> <span data-ttu-id="e0410-326">Ancak, uygulamanız birden çok hizmet içeriyorsa, tek bir CLI komutu`docker-compose up)`kullanarak (veya kapakların altında bu komutu kullanacak Visual Studio ile) oluşturulmuş bir uygulama olarak dağıtabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e0410-326">However, if your application contains multiple services, you can deploy it as a composed application, either using a single CLI command (`docker-compose up)`, or with Visual Studio, which will use that command under the covers.</span></span> <span data-ttu-id="e0410-327">Farklı seçeneklere bakalım.</span><span class="sxs-lookup"><span data-stu-id="e0410-327">Let's look at the different options.</span></span>

### <a name="option-a-running-a-single-container-application"></a><span data-ttu-id="e0410-328">Seçenek A: Tek kapsayıcı uygulaması çalıştırma</span><span class="sxs-lookup"><span data-stu-id="e0410-328">Option A: Running a single-container application</span></span>

#### <a name="using-docker-cli"></a><span data-ttu-id="e0410-329">Docker CLI kullanma</span><span class="sxs-lookup"><span data-stu-id="e0410-329">Using Docker CLI</span></span>

<span data-ttu-id="e0410-330">Şekil 5-9'da `docker run` gösterildiği gibi komutu kullanarak docker kapsayıcısı çalıştırabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="e0410-330">You can run a Docker container using the `docker run` command, as shown in Figure 5-9:</span></span>

```console
docker run -t -d -p 80:5000 cesardl/netcore-webapi-microservice-docker:first
```

<span data-ttu-id="e0410-331">Yukarıdaki komut, her çalıştırışta belirtilen görüntüden yeni bir kapsayıcı örneği oluşturur.</span><span class="sxs-lookup"><span data-stu-id="e0410-331">The above command will create a new container instance from the specified image, every time it's run.</span></span> <span data-ttu-id="e0410-332">Parametreyi `--name` kapsayıcıya ad vermek için kullanabilir ve `docker start {name}` ardından varolan bir kapsayıcı örneğini çalıştırmak için kapsayıcı kimliğini veya otomatik adı kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e0410-332">You can use the `--name` parameter to give a name to the container and then use `docker start {name}` (or use the container ID or automatic name) to run an existing container instance.</span></span>

![Docker çalıştır komutunu kullanarak Docker kapsayıcısını çalıştıran ekran görüntüsü.](./media/docker-app-development-workflow/use-docker-run-command.png)

<span data-ttu-id="e0410-334">**Şekil 5-9**.</span><span class="sxs-lookup"><span data-stu-id="e0410-334">**Figure 5-9**.</span></span> <span data-ttu-id="e0410-335">Docker çalıştır komutunu kullanarak Docker kapsayıcısı çalıştırma</span><span class="sxs-lookup"><span data-stu-id="e0410-335">Running a Docker container using the docker run command</span></span>

<span data-ttu-id="e0410-336">Bu durumda, komut, kapsayıcının iç bağlantı noktası 5000'i ana makinenin 80 bağlantı noktasına bağlar.</span><span class="sxs-lookup"><span data-stu-id="e0410-336">In this case, the command binds the internal port 5000 of the container to port 80 of the host machine.</span></span> <span data-ttu-id="e0410-337">Bu, ana bilgisayar bağlantı noktasının 80 bağlantı noktasını dinlediği ve konteynerüzerindeki 5000 portuna iletilmesi anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="e0410-337">This means that the host is listening on port 80 and forwarding to port 5000 on the container.</span></span>

<span data-ttu-id="e0410-338">Gösterilen karma kapsayıcı kimliğidir ve `--name` seçenek kullanılmazsa rasgele okunabilir bir ad da atanır.</span><span class="sxs-lookup"><span data-stu-id="e0410-338">The hash shown is the container ID and it’s also assigned a random readable name if the `--name` option is not used.</span></span>

#### <a name="using-visual-studio"></a><span data-ttu-id="e0410-339">Visual Studio’yu kullanma</span><span class="sxs-lookup"><span data-stu-id="e0410-339">Using Visual Studio</span></span>

<span data-ttu-id="e0410-340">Konteyner orkestrator desteği eklemediyseniz, **Ctrl-F5** tuşuna basarak Visual Studio'da tek bir kapsayıcı uygulaması çalıştırabilir ve konteynır içindeki uygulamayı hata ayıklamak için **F5'i** de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e0410-340">If you haven't added container orchestrator support, you can also run a single container app in Visual Studio by pressing **Ctrl-F5** and you can also use **F5** to debug the application within the container.</span></span> <span data-ttu-id="e0410-341">Kapsayıcı docker run kullanarak yerel olarak çalışır.</span><span class="sxs-lookup"><span data-stu-id="e0410-341">The container runs locally using docker run.</span></span>

### <a name="option-b-running-a-multi-container-application"></a><span data-ttu-id="e0410-342">Seçenek B: Çok kapsayıcılı bir uygulama çalıştırma</span><span class="sxs-lookup"><span data-stu-id="e0410-342">Option B: Running a multi-container application</span></span>

<span data-ttu-id="e0410-343">Çoğu kurumsal senaryoda, Docker uygulaması birden çok hizmetiçeren olacaktır, bu da Şekil 5-10'da gösterildiği gibi çok kapsayıcılı bir uygulama çalıştırmanız gerektiği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="e0410-343">In most enterprise scenarios, a Docker application will be composed of multiple services, which means you need to run a multi-container application, as shown in Figure 5-10.</span></span>

![Birkaç Docker konteynerli VM](./media/docker-app-development-workflow/vm-with-docker-containers-deployed.png)

<span data-ttu-id="e0410-345">**Şekil 5-10**.</span><span class="sxs-lookup"><span data-stu-id="e0410-345">**Figure 5-10**.</span></span> <span data-ttu-id="e0410-346">Docker konteynerleri dağıtılan VM</span><span class="sxs-lookup"><span data-stu-id="e0410-346">VM with Docker containers deployed</span></span>

#### <a name="using-docker-cli"></a><span data-ttu-id="e0410-347">Docker CLI kullanma</span><span class="sxs-lookup"><span data-stu-id="e0410-347">Using Docker CLI</span></span>

<span data-ttu-id="e0410-348">Docker CLI ile çok kapsayıcılı bir uygulama `docker-compose up` çalıştırmak için komutu kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="e0410-348">To run a multi-container application with the Docker CLI, you use the `docker-compose up` command.</span></span> <span data-ttu-id="e0410-349">Bu komut, çok kapsayıcılı bir uygulama dağıtmak için çözüm düzeyinde sahip olduğunuz **docker-compose.yml** dosyasını kullanır.</span><span class="sxs-lookup"><span data-stu-id="e0410-349">This command uses the **docker-compose.yml** file that you have at the solution level to deploy a multi-container application.</span></span> <span data-ttu-id="e0410-350">Şekil 5-11, docker-compose.yml dosyasını içeren ana çözüm dizininizden komutu çalıştırırken sonuçları gösterir.</span><span class="sxs-lookup"><span data-stu-id="e0410-350">Figure 5-11 shows the results when running the command from your main solution directory, which contains the docker-compose.yml file.</span></span>

![Docker-comto command komutunu çalıştırırken ekran görünümü](./media/docker-app-development-workflow/results-docker-compose-up.png)

<span data-ttu-id="e0410-352">**Şekil 5-11**.</span><span class="sxs-lookup"><span data-stu-id="e0410-352">**Figure 5-11**.</span></span> <span data-ttu-id="e0410-353">Docker-comto komutunu çalıştırırken örnek sonuçlar</span><span class="sxs-lookup"><span data-stu-id="e0410-353">Example results when running the docker-compose up command</span></span>

<span data-ttu-id="e0410-354">Docker-compose up komutu çalıştırıldıktan sonra, uygulama ve ilgili kapsayıcılar Şekil 5-10'da belirtildiği gibi Docker ana cihazınıza dağıtılır.</span><span class="sxs-lookup"><span data-stu-id="e0410-354">After the docker-compose up command runs, the application and its related containers are deployed into your Docker host, as depicted in Figure 5-10.</span></span>

#### <a name="using-visual-studio"></a><span data-ttu-id="e0410-355">Visual Studio’yu kullanma</span><span class="sxs-lookup"><span data-stu-id="e0410-355">Using Visual Studio</span></span>

<span data-ttu-id="e0410-356">Visual Studio 2019'u kullanarak çok konteynerli bir uygulama çalıştırmak daha kolay olamaz.</span><span class="sxs-lookup"><span data-stu-id="e0410-356">Running a multi-container application using Visual Studio 2019 can't get any simpler.</span></span> <span data-ttu-id="e0410-357">Her zamanki gibi hata ayıklamak için **ctrl-F5** tuşuna veya **F5'e** basarak başlangıç projesi olarak **docker-compose** projesini ayarlamanız gerekiyor.</span><span class="sxs-lookup"><span data-stu-id="e0410-357">You just press **Ctrl-F5** to run or **F5** to debug, as usual, setting up the **docker-compose** project as the startup project.</span></span>  <span data-ttu-id="e0410-358">Visual Studio, her zamanki gibi kesme noktaları oluşturabilir ve sonunda "uzak sunucularda" çalışan bağımsız işlemler haline ne hata ayıklama, hata ayıklama zaten bağlı, sadece bunun gibi işler.</span><span class="sxs-lookup"><span data-stu-id="e0410-358">Visual Studio handles all needed setup, so you can create breakpoints as usual and debug what finally become independent processes running in "remote servers", with the debugger already attached, just like that.</span></span>

<span data-ttu-id="e0410-359">Daha önce de belirtildiği gibi, bir çözüm içinde bir projeye Docker çözüm desteği eklediğinizde, bu proje tüm çözümü aynı anda çalıştırmanızı veya hata ayıklamanızı sağlayan genel (çözüm düzeyinde) docker-compose.yml dosyasında yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="e0410-359">As mentioned before, each time you add Docker solution support to a project within a solution, that project is configured in the global (solution-level) docker-compose.yml file, which lets you run or debug the whole solution at once.</span></span> <span data-ttu-id="e0410-360">Visual Studio, Docker çözüm desteği etkin olan her proje için bir konteyner başlatacak ve sizin için tüm dahili adımları gerçekleştirecektir (dotnet yayımlama, docker build, vb.).</span><span class="sxs-lookup"><span data-stu-id="e0410-360">Visual Studio will start one container for each project that has Docker solution support enabled, and perform all the internal steps for you (dotnet publish, docker build, etc.).</span></span>

<span data-ttu-id="e0410-361">Tüm angarya bir göz atmak istiyorsanız, dosyaya bir göz atın:</span><span class="sxs-lookup"><span data-stu-id="e0410-361">If you want to take a peek at all the drudgery, take a look at the file:</span></span>

`{root solution folder}\obj\Docker\docker-compose.vs.debug.g.yml`

<span data-ttu-id="e0410-362">Burada önemli olan nokta, Şekil 5-12'de gösterildiği gibi Visual Studio 2019'da F5 anahtar eylemi için ek bir **Docker** komutu olmasıdır.</span><span class="sxs-lookup"><span data-stu-id="e0410-362">The important point here is that, as shown in Figure 5-12, in Visual Studio 2019 there is an additional **Docker** command for the F5 key action.</span></span> <span data-ttu-id="e0410-363">Bu seçenek, docker-compose.yml dosyalarında tanımlanan tüm kapsayıcıları çözüm düzeyinde çalıştırarak çok kapsayıcılı bir uygulamayı çalıştırmanızı veya hata ayıklamanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="e0410-363">This option lets you run or debug a multi-container application by running all the containers that are defined in the docker-compose.yml files at the solution level.</span></span> <span data-ttu-id="e0410-364">Birden çok kapsayıcı çözümlerini hata ayıklama yeteneği, her bir kesme noktası farklı bir projede (kapsayıcı) birkaç kesme noktası ayarlayabileceğiniz anlamına gelir ve Visual Studio'dan hata ayıklama sırasında farklı projelerde tanımlanan ve farklı kapsayıcılarda çalışan kesme noktalarında duracağınız anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="e0410-364">The ability to debug multiple-container solutions means that you can set several breakpoints, each breakpoint in a different project (container), and while debugging from Visual Studio you will stop at breakpoints defined in different projects and running on different containers.</span></span>

![Docker-compose projesini çalıştıran hata ayıklama araç çubuğunun ekran görüntüsü.](./media/docker-app-development-workflow/debug-toolbar-docker-compose-project.png)

<span data-ttu-id="e0410-366">**Şekil 5-12**.</span><span class="sxs-lookup"><span data-stu-id="e0410-366">**Figure 5-12**.</span></span> <span data-ttu-id="e0410-367">Visual Studio 2019'da çoklu konteyner uygulamaları çalıştırma</span><span class="sxs-lookup"><span data-stu-id="e0410-367">Running multi-container apps in Visual Studio 2019</span></span>

### <a name="additional-resources"></a><span data-ttu-id="e0410-368">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="e0410-368">Additional resources</span></span>

- <span data-ttu-id="e0410-369">**Uzak bir Docker ana bilgisayara ASP.NET kapsayıcısı dağıtma** </span><span class="sxs-lookup"><span data-stu-id="e0410-369">**Deploy an ASP.NET container to a remote Docker host** </span></span>\
  <https://docs.microsoft.com/azure/vs-azure-tools-docker-hosting-web-apps-in-docker>

### <a name="a-note-about-testing-and-deploying-with-orchestrators"></a><span data-ttu-id="e0410-370">Orkestratörlerle test etme ve dağıtma hakkında bir not</span><span class="sxs-lookup"><span data-stu-id="e0410-370">A note about testing and deploying with orchestrators</span></span>

<span data-ttu-id="e0410-371">Docker-compose up ve docker run komutları (veya Visual Studio'daki kapsayıcıları çalıştırma ve hata ayıklama) geliştirme ortamınızdaki kapsayıcıları test etmek için yeterlidir.</span><span class="sxs-lookup"><span data-stu-id="e0410-371">The docker-compose up and docker run commands (or running and debugging the containers in Visual Studio) are adequate for testing containers in your development environment.</span></span> <span data-ttu-id="e0410-372">Ancak bu yaklaşımı, [Kubernetes](https://kubernetes.io/) veya [Service Fabric](https://azure.microsoft.com/services/service-fabric/)gibi orkestratörleri hedeflemeniz gereken üretim dağıtımları için kullanmamalısınız.</span><span class="sxs-lookup"><span data-stu-id="e0410-372">But you should not use this approach for production deployments, where you should target orchestrators like [Kubernetes](https://kubernetes.io/) or [Service Fabric](https://azure.microsoft.com/services/service-fabric/).</span></span> <span data-ttu-id="e0410-373">Kubernetes kullanıyorsanız, bunları ağ için kapsayıcılar ve [hizmetleri](https://kubernetes.io/docs/concepts/services-networking/service/) düzenlemek için [bölmeleri](https://kubernetes.io/docs/concepts/workloads/pods/pod/) kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="e0410-373">If you're using Kubernetes, you have to use [pods](https://kubernetes.io/docs/concepts/workloads/pods/pod/) to organize containers and [services](https://kubernetes.io/docs/concepts/services-networking/service/) to network them.</span></span> <span data-ttu-id="e0410-374">Pod oluşturma ve modifikasyondüzenlemek için dağıtımları da [kullanırsınız.](https://kubernetes.io/docs/concepts/workloads/controllers/deployment/)</span><span class="sxs-lookup"><span data-stu-id="e0410-374">You also use [deployments](https://kubernetes.io/docs/concepts/workloads/controllers/deployment/) to organize pod creation and modification.</span></span>

![Adım 6 için görüntü.](./media/docker-app-development-workflow/step-6-test-app-microservices.png)

## <a name="step-6-test-your-docker-application-using-your-local-docker-host"></a><span data-ttu-id="e0410-376">6. Adım.</span><span class="sxs-lookup"><span data-stu-id="e0410-376">Step 6.</span></span> <span data-ttu-id="e0410-377">Docker uygulamanızı yerel Docker ana bilgisayarınızı kullanarak test edin</span><span class="sxs-lookup"><span data-stu-id="e0410-377">Test your Docker application using your local Docker host</span></span>

<span data-ttu-id="e0410-378">Bu adım, uygulamanızın ne yaptığına bağlı olarak değişir.</span><span class="sxs-lookup"><span data-stu-id="e0410-378">This step will vary depending on what your application is doing.</span></span> <span data-ttu-id="e0410-379">Tek bir kapsayıcı veya hizmet olarak dağıtılan basit bir .NET Core Web uygulamasında, Docker ana bilgisayarında bir tarayıcı açarak ve Şekil 5-13'te gösterildiği gibi bu siteye yönlendirerek hizmete erişebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e0410-379">In a simple .NET Core Web application that is deployed as a single container or service, you can access the service by opening a browser on the Docker host and navigating to that site, as shown in Figure 5-13.</span></span> <span data-ttu-id="e0410-380">(Dockerfile'deki yapılandırma kapsayıcıyı 80'den başka bir bağlantı noktasıyla eşlerse, ANA Bilgisayar bağlantı noktasını URL'ye ekleyin.)</span><span class="sxs-lookup"><span data-stu-id="e0410-380">(If the configuration in the Dockerfile maps the container to a port on the host that is anything other than 80, include the host port in the URL.)</span></span>

![Localhost/API/values'den yanıtın ekran görüntüsü.](./media/docker-app-development-workflow/test-docker-app-locally-localhost.png)

<span data-ttu-id="e0410-382">**Şekil 5-13**.</span><span class="sxs-lookup"><span data-stu-id="e0410-382">**Figure 5-13**.</span></span> <span data-ttu-id="e0410-383">Docker uygulamanızı localhost kullanarak yerel olarak test etme örneği</span><span class="sxs-lookup"><span data-stu-id="e0410-383">Example of testing your Docker application locally using localhost</span></span>

<span data-ttu-id="e0410-384">Localhost Docker ana bilgisayar IP'sini işaret etmiyorsa (varsayılan olarak, Docker CE kullanırken, olmalıdır), hizmetinize gitmek için makinenizin ağ kartının IP adresini kullanın.</span><span class="sxs-lookup"><span data-stu-id="e0410-384">If localhost is not pointing to the Docker host IP (by default, when using Docker CE, it should), to navigate to your service, use the IP address of your machine's network card.</span></span>

<span data-ttu-id="e0410-385">Tarayıcıdaki bu URL'nin tartışılan belirli kapsayıcı örneği için 80 no'lu bağlantı noktasını kullandığını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="e0410-385">Note that this URL in the browser uses port 80 for the particular container example being discussed.</span></span> <span data-ttu-id="e0410-386">Ancak, önceki adımda açıklandığı gibi, docker run komutu yla bu şekilde dağıtıldığı için, istekler dahili olarak 5000 portuna yönlendiriliyor.</span><span class="sxs-lookup"><span data-stu-id="e0410-386">However, internally the requests are being redirected to port 5000, because that was how it was deployed with the docker run command, as explained in a previous step.</span></span>

<span data-ttu-id="e0410-387">Ayrıca, Şekil 5-14'te gösterildiği gibi, terminalden kıvrılma kullanarak uygulamayı test edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e0410-387">You can also test the application using curl from the terminal, as shown in Figure 5-14.</span></span> <span data-ttu-id="e0410-388">Windows'daki Docker yüklemesinde, varsayılan Docker Host IP'si makinenizin gerçek IP adresine ek olarak her zaman 10.0.75.1'dir.</span><span class="sxs-lookup"><span data-stu-id="e0410-388">In a Docker installation on Windows, the default Docker Host IP is always 10.0.75.1 in addition to your machine's actual IP address.</span></span>

![Kıvrılma http://10.0.75.1/API/values ile almaktan konsol çıkışı.](./media/docker-app-development-workflow/test-docker-app-locally-curl.png)

<span data-ttu-id="e0410-390">**Şekil 5-14**.</span><span class="sxs-lookup"><span data-stu-id="e0410-390">**Figure 5-14**.</span></span> <span data-ttu-id="e0410-391">Docker uygulamanızı curl kullanarak yerel olarak test etme örneği</span><span class="sxs-lookup"><span data-stu-id="e0410-391">Example of testing your Docker application locally using curl</span></span>

### <a name="testing-and-debugging-containers-with-visual-studio-2019"></a><span data-ttu-id="e0410-392">Visual Studio 2019 ile konteynerleri test etme ve hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="e0410-392">Testing and debugging containers with Visual Studio 2019</span></span>

<span data-ttu-id="e0410-393">Visual Studio 2019 ile kapsayıcıları çalıştırıp hata ayıklarken,.NET uygulamasını, kapsayıcıolmadan çalışırken yaptığınız gibi hata ayıklayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e0410-393">When running and debugging the containers with Visual Studio 2019, you can debug the .NET application in much the same way as you would when running without containers.</span></span>

### <a name="testing-and-debugging-without-visual-studio"></a><span data-ttu-id="e0410-394">Visual Studio olmadan test ve hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="e0410-394">Testing and debugging without Visual Studio</span></span>

<span data-ttu-id="e0410-395">Düzenleyici/CLI yaklaşımını kullanarak geliştiriyorsanız, hata ayıklama kapsayıcıları daha zordur ve büyük olasılıkla izleme ler oluşturarak hata ayıklamak istersiniz.</span><span class="sxs-lookup"><span data-stu-id="e0410-395">If you're developing using the editor/CLI approach, debugging containers is more difficult and you'll probably want to debug by generating traces.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="e0410-396">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="e0410-396">Additional resources</span></span>

- <span data-ttu-id="e0410-397">**Uygulamaları yerel bir Docker konteynerinde hata ayıklama** </span><span class="sxs-lookup"><span data-stu-id="e0410-397">**Debugging apps in a local Docker container** </span></span>\
  [https://docs.microsoft.com/visualstudio/containers/edit-and-refresh](/visualstudio/containers/edit-and-refresh)

- <span data-ttu-id="e0410-398">**Steve Lasker' ı. Docker ile Core Apps ASP.NET oluşturun, hata ayıklayın, dağıtın.**</span><span class="sxs-lookup"><span data-stu-id="e0410-398">**Steve Lasker. Build, Debug, Deploy ASP.NET Core Apps with Docker.**</span></span> <span data-ttu-id="e0410-399">Video.</span><span class="sxs-lookup"><span data-stu-id="e0410-399">Video.</span></span> \
  <https://channel9.msdn.com/Events/Visual-Studio/Visual-Studio-2017-Launch/T115>

## <a name="simplified-workflow-when-developing-containers-with-visual-studio"></a><span data-ttu-id="e0410-400">Visual Studio ile kaplar geliştirirken basitleştirilmiş iş akışı</span><span class="sxs-lookup"><span data-stu-id="e0410-400">Simplified workflow when developing containers with Visual Studio</span></span>

<span data-ttu-id="e0410-401">Visual Studio'yu kullanırken iş akışı, editör/CLI yaklaşımını kullandığınızdan çok daha basittir.</span><span class="sxs-lookup"><span data-stu-id="e0410-401">Effectively, the workflow when using Visual Studio is a lot simpler than if you use the editor/CLI approach.</span></span> <span data-ttu-id="e0410-402">Dockerfile ve docker-compose.yml dosyaları yla ilgili Docker tarafından gerekli olan adımların çoğu Şekil 5-15'te gösterildiği gibi Visual Studio tarafından gizlenir veya basitleştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="e0410-402">Most of the steps required by Docker related to the Dockerfile and docker-compose.yml files are hidden or simplified by Visual Studio, as shown in Figure 5-15.</span></span>

:::image type="complex" source="./media/docker-app-development-workflow/simplified-life-cycle-containerized-apps-docker-cli.png" alt-text="Bir uygulama oluşturmak için gereken beş basitleştirilmiş adımı gösteren diyagram.":::
<span data-ttu-id="e0410-404">Docker uygulamaları için geliştirme süreci: 1 - Uygulamanızı kodlayın, 2 - Dockerfile/s yazın, 3 - Dockerfile/s'de tanımlanan görüntüleri oluşturun, 4 - (isteğe bağlı) Docker-compose.yml dosyasında hizmetleri oluşturun, 5 - Konteyner veya docker-create app, 6 - Uygulamanızı veya mikro hizmetleri test edin, 7 - Repo'yu tekrarlamak için bastırın ve tekrarlayın.</span><span class="sxs-lookup"><span data-stu-id="e0410-404">The development process for Docker apps: 1 - Code your App, 2 - Write Dockerfile/s, 3 - Create images defined at Dockerfile/s, 4 - (optional) Compose services in the docker-compose.yml file, 5 - Run container or docker-compose app, 6 - Test your app or microservices, 7 - Push to repo and repeat.</span></span>
:::image-end:::

<span data-ttu-id="e0410-405">**Şekil 5-15**.</span><span class="sxs-lookup"><span data-stu-id="e0410-405">**Figure 5-15**.</span></span> <span data-ttu-id="e0410-406">Visual Studio ile gelişirken basitleştirilmiş iş akışı</span><span class="sxs-lookup"><span data-stu-id="e0410-406">Simplified workflow when developing with Visual Studio</span></span>

<span data-ttu-id="e0410-407">Buna ek olarak, adım 2 (projelerinize Docker desteği ekleyerek) sadece bir kez gerçekleştirmek gerekir.</span><span class="sxs-lookup"><span data-stu-id="e0410-407">In addition, you need to perform step 2 (adding Docker support to your projects) just once.</span></span> <span data-ttu-id="e0410-408">Bu nedenle, iş akışı, başka bir geliştirme için .NET kullanırken olağan geliştirme görevlerine benzer.</span><span class="sxs-lookup"><span data-stu-id="e0410-408">Therefore, the workflow is similar to your usual development tasks when using .NET for any other development.</span></span> <span data-ttu-id="e0410-409">Kapakların altında neler olup bittiğini (görüntü oluşturma işlemi, kullandığınız temel görüntüler, kapsayıcıların dağıtımı, vb.) bilmeniz gerekir ve bazen davranışları özelleştirmek için Dockerfile veya docker-compose.yml dosyasını da kaldırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="e0410-409">You need to know what is going on under the covers (the image build process, what base images you're using, deployment of containers, etc.) and sometimes you will also need to edit the Dockerfile or docker-compose.yml file to customize behaviors.</span></span> <span data-ttu-id="e0410-410">Ama işin çoğu büyük ölçüde Visual Studio kullanarak basitleştirilmiş, çok daha üretken hale.</span><span class="sxs-lookup"><span data-stu-id="e0410-410">But most of the work is greatly simplified by using Visual Studio, making you a lot more productive.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="e0410-411">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="e0410-411">Additional resources</span></span>

- <span data-ttu-id="e0410-412">**Steve Lasker' ı. .NET Docker Geliştirme Visual Studio (2017)** </span><span class="sxs-lookup"><span data-stu-id="e0410-412">**Steve Lasker. .NET Docker Development with Visual Studio (2017)** </span></span>\
  <https://channel9.msdn.com/Events/Visual-Studio/Visual-Studio-2017-Launch/T111>

## <a name="using-powershell-commands-in-a-dockerfile-to-set-up-windows-containers"></a><span data-ttu-id="e0410-413">Windows Kapsayıcıları kurmak için Dockerfile'daki PowerShell komutlarını kullanma</span><span class="sxs-lookup"><span data-stu-id="e0410-413">Using PowerShell commands in a Dockerfile to set up Windows Containers</span></span>

<span data-ttu-id="e0410-414">[Windows Kapsayıcıları,](https://docs.microsoft.com/virtualization/windowscontainers/about/index) mevcut Windows uygulamalarınızı Docker görüntülerine dönüştürmenize ve bunları Docker ekosisteminin geri kalanıyla aynı araçlarla dağıtmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="e0410-414">[Windows Containers](https://docs.microsoft.com/virtualization/windowscontainers/about/index) allow you to convert your existing Windows applications into Docker images and deploy them with the same tools as the rest of the Docker ecosystem.</span></span> <span data-ttu-id="e0410-415">Windows Kapsayıcıları'nı kullanmak için, aşağıdaki örnekte gösterildiği gibi Dockerfile'da PowerShell komutlarını çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="e0410-415">To use Windows Containers, you run PowerShell commands in the Dockerfile, as shown in the following example:</span></span>

```Dockerfile
FROM mcr.microsoft.com/windows/servercore
LABEL Description="IIS" Vendor="Microsoft" Version="10"
RUN powershell -Command Add-WindowsFeature Web-Server
CMD [ "ping", "localhost", "-t" ]
```

<span data-ttu-id="e0410-416">Bu durumda, bir Windows Server Core temel görüntüsü (FROM ayarı) kullanıyoruz ve PowerShell komutu (RUN ayarı) ile IIS yüklüyoruz.</span><span class="sxs-lookup"><span data-stu-id="e0410-416">In this case, we are using a Windows Server Core base image (the FROM setting) and installing IIS with a PowerShell command (the RUN setting).</span></span> <span data-ttu-id="e0410-417">Benzer bir şekilde, powershell komutlarını kullanarak ASP.NET 4.x, .NET 4.6 veya başka bir Windows yazılımı gibi ek bileşenler de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e0410-417">In a similar way, you could also use PowerShell commands to set up additional components like ASP.NET 4.x, .NET 4.6, or any other Windows software.</span></span> <span data-ttu-id="e0410-418">Örneğin, Dockerfile'deki aşağıdaki komut 4,5'ASP.NET ayarlar:</span><span class="sxs-lookup"><span data-stu-id="e0410-418">For example, the following command in a Dockerfile sets up ASP.NET 4.5:</span></span>

```Dockerfile
RUN powershell add-windowsfeature web-asp-net45
```

### <a name="additional-resources"></a><span data-ttu-id="e0410-419">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="e0410-419">Additional resources</span></span>

- <span data-ttu-id="e0410-420">**aspnet-docker/Dockerfile.**</span><span class="sxs-lookup"><span data-stu-id="e0410-420">**aspnet-docker/Dockerfile.**</span></span> <span data-ttu-id="e0410-421">Örnek PowerShell komutları dockerdosyalarından Windows özelliklerini içerecek şekilde çalıştırılabilmektedir.</span><span class="sxs-lookup"><span data-stu-id="e0410-421">Example PowerShell commands to run from dockerfiles to include Windows features.</span></span>\
  <https://github.com/Microsoft/aspnet-docker/blob/master/4.7.1-windowsservercore-ltsc2016/runtime/Dockerfile>

>[!div class="step-by-step"]
><span data-ttu-id="e0410-422">[Önceki](index.md)
>[Sonraki](../multi-container-microservice-net-applications/index.md)</span><span class="sxs-lookup"><span data-stu-id="e0410-422">[Previous](index.md)
[Next](../multi-container-microservice-net-applications/index.md)</span></span>
