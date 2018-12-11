---
title: Docker uygulamaları için geliştirme iş akışı
description: Kapsayıcılı .NET uygulamaları için .NET mikro hizmet mimarisi | Docker uygulamaları için geliştirme iş akışı
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/05/2018
ms.openlocfilehash: bc6b1796ed7b12a04affc521ac2efee515c48ae2
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53150556"
---
# <a name="development-workflow-for-docker-apps"></a><span data-ttu-id="05663-103">Docker uygulamaları için geliştirme iş akışı</span><span class="sxs-lookup"><span data-stu-id="05663-103">Development workflow for Docker apps</span></span>

<span data-ttu-id="05663-104">Burada geliştirici kendi tercih edilen dili kullanarak uygulama kodları ve yerel olarak test her geliştiricinin makine uygulama geliştirme yaşam döngüsü başlatır.</span><span class="sxs-lookup"><span data-stu-id="05663-104">The application development life cycle starts at each developer’s machine, where the developer codes the application using their preferred language and tests it locally.</span></span> <span data-ttu-id="05663-105">Hangi dil, çerçeve ve geliştirici seçer, bu iş akışı ile platform ne olursa olsun Geliştirici her zaman geliştirme ve test Docker kapsayıcıları, ancak bunun yerel olarak yapılması.</span><span class="sxs-lookup"><span data-stu-id="05663-105">No matter which language, framework, and platform the developer chooses, with this workflow, the developer is always developing and testing Docker containers, but doing so locally.</span></span>

<span data-ttu-id="05663-106">Her kapsayıcı (bir Docker görüntüsü örneği), aşağıdaki bileşenleri içerir:</span><span class="sxs-lookup"><span data-stu-id="05663-106">Each container (an instance of a Docker image) includes the following components:</span></span>

- <span data-ttu-id="05663-107">Bir işletim sistemi seçimi olduğu (örneğin, bir Linux dağıtımı, Windows Nano sunucu veya Windows Server Core).</span><span class="sxs-lookup"><span data-stu-id="05663-107">An operating system selection (for example, a Linux distribution, Windows Nano Server, or Windows Server Core).</span></span>

- <span data-ttu-id="05663-108">Geliştirici (uygulama ikilileri, vb.) tarafından eklenen dosyalar.</span><span class="sxs-lookup"><span data-stu-id="05663-108">Files added by the developer (application binaries, etc.).</span></span>

- <span data-ttu-id="05663-109">Yapılandırma bilgileri (ortam ayarlarını ve bağımlılıklarını).</span><span class="sxs-lookup"><span data-stu-id="05663-109">Configuration information (environment settings and dependencies).</span></span>

## <a name="workflow-for-developing-docker-container-based-applications"></a><span data-ttu-id="05663-110">Docker kapsayıcı tabanlı uygulamaları geliştirmek için iş akışı</span><span class="sxs-lookup"><span data-stu-id="05663-110">Workflow for developing Docker container-based applications</span></span>

<span data-ttu-id="05663-111">Bu bölümde açıklanmaktadır *iç döngü* Docker kapsayıcı tabanlı uygulamaları için geliştirme iş akışı.</span><span class="sxs-lookup"><span data-stu-id="05663-111">This section describes the *inner-loop* development workflow for Docker container-based applications.</span></span> <span data-ttu-id="05663-112">İç döngü iş akışı, daha geniş DevOps iş akışını dikkate alarak değildir ve yalnızca geliştiricinin bilgisayarında geliştirme çalışmanın odaklanır anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="05663-112">The inner-loop workflow means it is not taking into account the broader DevOps workflow and just focuses on the development work done on the developer’s computer.</span></span> <span data-ttu-id="05663-113">Ortamı ayarlamak için ilk adımlarında bu yalnızca bir kez gerçekleştirilir dahil değildir.</span><span class="sxs-lookup"><span data-stu-id="05663-113">The initial steps to set up the environment are not included, since those are done only once.</span></span>

<span data-ttu-id="05663-114">Uygulamanın kendi Hizmetleri ve ek kitaplıklar (bağımlılıklar) karakterlerinden oluşur.</span><span class="sxs-lookup"><span data-stu-id="05663-114">An application is composed of your own services plus additional libraries (dependencies).</span></span> <span data-ttu-id="05663-115">Aşağıda, genellikle bir Docker uygulaması oluştururken Şekil 5-1'de gösterildiği gibi temel adımlar verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="05663-115">The following are the basic steps you usually take when building a Docker application, as illustrated in Figure 5-1.</span></span>

![Docker kapsayıcı uygulamaları grafik geliştirmek için adım adım iş akışı](./media/image1.png)

<span data-ttu-id="05663-117">**Şekil 5-1.**</span><span class="sxs-lookup"><span data-stu-id="05663-117">**Figure 5-1.**</span></span> <span data-ttu-id="05663-118">Kapsayıcılı Docker uygulamaları geliştirmeye yönelik adım adım iş akışı</span><span class="sxs-lookup"><span data-stu-id="05663-118">Step-by-step workflow for developing Docker containerized apps</span></span>

<span data-ttu-id="05663-119">Bu kılavuzdaki tüm bu işlemi ayrıntılı olarak verilmiştir ve önemli adım her bir Visual Studio ortamında odaklanarak açıklanmıştır.</span><span class="sxs-lookup"><span data-stu-id="05663-119">In this guide, this whole process is detailed and every major step is explained by focusing on a Visual Studio environment.</span></span>

<span data-ttu-id="05663-120">Bir düzenleyici/CLI geliştirme yaklaşımını (örneğin, Visual Studio Code ve Docker CLI'yı MacOS ya da Windows) kullandığınızda, her adım genellikle Visual Studio kullanıyorsanız, daha ayrıntılı biçimde bilmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="05663-120">When you are using an editor/CLI development approach (for example, Visual Studio Code plus Docker CLI on macOS or Windows), you need to know every step, generally in more detail than if you are using Visual Studio.</span></span> <span data-ttu-id="05663-121">E-kitabı CLI ortamda çalışma hakkında daha fazla bilgi için bkz. [Microsoft Platforms ve araçlarla kapsayıcılı Docker uygulaması yaşam döngüsü](https://aka.ms/dockerlifecycleebook/).</span><span class="sxs-lookup"><span data-stu-id="05663-121">For more information about working in a CLI environment, see the e-book [Containerized Docker Application lifecycle with Microsoft Platforms and Tools](https://aka.ms/dockerlifecycleebook/).</span></span>

<span data-ttu-id="05663-122">Visual Studio kullanıyorsanız, bu adımların çoğunu sizin yerinize üretkenliğinizi önemli ölçüde artıran işlenir.</span><span class="sxs-lookup"><span data-stu-id="05663-122">When you're using Visual Studio, many of those steps are handled for you, which dramatically improves your productivity.</span></span> <span data-ttu-id="05663-123">Visual Studio 2017 kullanılarak ve çok kapsayıcılı uygulamaları hedefleyen bu özellikle doğrudur.</span><span class="sxs-lookup"><span data-stu-id="05663-123">This is especially true when you are using Visual Studio 2017 and targeting multi-container applications.</span></span> <span data-ttu-id="05663-124">Örneğin, Visual Studio yalnızca tek bir tıklatmayla ekler *Dockerfile* ve *docker-compose.yml* uygulamanız için dosyaları projelerinize yapılandırmasına sahip.</span><span class="sxs-lookup"><span data-stu-id="05663-124">For instance, with just one mouse click, Visual Studio adds the *Dockerfile* and *docker-compose.yml* files to your projects with the configuration for your application.</span></span> <span data-ttu-id="05663-125">Visual Studio'da uygulamayı çalıştırdığınızda, Docker görüntüsünü oluşturur ve çok kapsayıcılı bir uygulama doğrudan Docker'da çalıştırılır.</span><span class="sxs-lookup"><span data-stu-id="05663-125">When you run the application in Visual Studio, it builds the Docker image and runs the multi-container application directly in Docker.</span></span> <span data-ttu-id="05663-126">Bile aynı anda birden fazla kapsayıcılar ayıklamanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="05663-126">It even allows you to debug several containers at once.</span></span> <span data-ttu-id="05663-127">Bu özellikler, geliştirme hızını artırın.</span><span class="sxs-lookup"><span data-stu-id="05663-127">These features boost your development speed.</span></span>

<span data-ttu-id="05663-128">Aşağıdaki kılavuzda, "perde" Docker ile neler olduğunu açıklar.</span><span class="sxs-lookup"><span data-stu-id="05663-128">In the guidance that follows, we explain what's happening "under the covers" with Docker.</span></span>

![1. adım - uygulama grafiği kod](./media/image2.png)

## <a name="step-1-start-coding-and-create-your-initial-application-or-service-baseline"></a><span data-ttu-id="05663-130">Adım 1.</span><span class="sxs-lookup"><span data-stu-id="05663-130">Step 1.</span></span> <span data-ttu-id="05663-131">Kodlamaya başlayın ve ilk uygulama veya hizmet taban çizgisi oluşturma</span><span class="sxs-lookup"><span data-stu-id="05663-131">Start coding and create your initial application or service baseline</span></span>

<span data-ttu-id="05663-132">Docker uygulaması geliştirmek, Docker olmadan uygulama geliştirme şekilde benzerdir.</span><span class="sxs-lookup"><span data-stu-id="05663-132">Developing a Docker application is similar to the way you develop an application without Docker.</span></span> <span data-ttu-id="05663-133">Docker için geliştirmeye devam ederken, dağıtan ve uygulamanızı veya yerel ortamınızda Docker kapsayıcıları içinde çalışan hizmetleri test etme, farktır.</span><span class="sxs-lookup"><span data-stu-id="05663-133">The difference is that while developing for Docker, you are deploying and testing your application or services running within Docker containers in your local environment.</span></span> <span data-ttu-id="05663-134">Kapsayıcı, bir Linux kapsayıcı ya da bir Windows kapsayıcı olabilir.</span><span class="sxs-lookup"><span data-stu-id="05663-134">The container can be either a Linux container or a Windows container.</span></span>

### <a name="set-up-your-local-environment-with-visual-studio"></a><span data-ttu-id="05663-135">Visual Studio ile yerel ortamınızı ayarlayın</span><span class="sxs-lookup"><span data-stu-id="05663-135">Set up your local environment with Visual Studio</span></span>

<span data-ttu-id="05663-136">Başlamak için sahip olduğunuzdan emin olun [Docker Community Edition'ı (CE)](https://www.docker.com/community-edition) aşağıdaki yönergelerinde açıklandığı gibi yüklü Windows için:</span><span class="sxs-lookup"><span data-stu-id="05663-136">To begin, make sure you have [Docker Community Edition (CE)](https://www.docker.com/community-edition) for Windows installed, as explained in the following instructions:</span></span>

[<span data-ttu-id="05663-137">İçin Docker CE Windows ile çalışmaya başlama</span><span class="sxs-lookup"><span data-stu-id="05663-137">Get started with Docker CE for Windows</span></span>](https://docs.docker.com/docker-for-windows/)

<span data-ttu-id="05663-138">Visual Studio 2017 ile buna ihtiyacınız **.NET Core çoklu platform geliştirme** yüklüyse, Şekil 5-2'de gösterildiği gibi iş yükü.</span><span class="sxs-lookup"><span data-stu-id="05663-138">In addition, you need Visual Studio 2017 with the **.NET Core cross-platform development** workload installed, as shown in Figure 5-2.</span></span>

![](./media/image3.png)

<span data-ttu-id="05663-139">**Şekil 5-2**.</span><span class="sxs-lookup"><span data-stu-id="05663-139">**Figure 5-2**.</span></span> <span data-ttu-id="05663-140">Seçme **.NET Core ve Docker** Visual Studio 2017 Kurulum sırasında iş yükü</span><span class="sxs-lookup"><span data-stu-id="05663-140">Selecting the **.NET Core and Docker** workload during Visual Studio 2017 setup</span></span>

<span data-ttu-id="05663-141">Uygulamanızda Docker'ı etkinleştirme ve Docker sınama dağıtımı önce (genellikle, .NET Core kapsayıcıları kullanmayı planlıyorsanız) düz .NET uygulamanızda kodlamaya başlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="05663-141">You can start coding your application in plain .NET (usually in .NET Core if you are planning to use containers) even before enabling Docker in your application and deploying and testing in Docker.</span></span> <span data-ttu-id="05663-142">Ancak, üzerinde Docker olabildiğince çabuk, çünkü gerçek ortam olacak ve sorunları olabildiğince çabuk bulunabileceğini çalışma başlangıç önerilir.</span><span class="sxs-lookup"><span data-stu-id="05663-142">However, it is recommended that you start working on Docker as soon as possible, because that will be the real environment and any issues can be discovered as soon as possible.</span></span> <span data-ttu-id="05663-143">Visual Studio, bu nedenle, neredeyse saydam hissettiği Docker'la çalışmak kolaylaştırır çünkü bu teşvik edilir — çok kapsayıcılı uygulamalar Visual Studio'dan hata ayıklama sırasında en iyi örnek.</span><span class="sxs-lookup"><span data-stu-id="05663-143">This is encouraged because Visual Studio makes it so easy to work with Docker that it almost feels transparent — the best example when debugging multi-container applications from Visual Studio.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="05663-144">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="05663-144">Additional resources</span></span>

- <span data-ttu-id="05663-145">**İçin Docker CE Windows ile çalışmaya başlama**</span><span class="sxs-lookup"><span data-stu-id="05663-145">**Get started with Docker CE for Windows**</span></span>

   [*https://docs.docker.com/docker-for-windows/*](https://docs.docker.com/docker-for-windows/)

- <span data-ttu-id="05663-146">**Visual Studio 2017**</span><span class="sxs-lookup"><span data-stu-id="05663-146">**Visual Studio 2017**</span></span>

   [*https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs*](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs)

![2. adım - dockerfile'ları grafik yazma](./media/image4.png)

## <a name="step-2-create-a-dockerfile-related-to-an-existing-net-base-image"></a><span data-ttu-id="05663-148">Adım 2.</span><span class="sxs-lookup"><span data-stu-id="05663-148">Step 2.</span></span> <span data-ttu-id="05663-149">Mevcut bir .NET temel görüntü için ilgili bir Dockerfile'ı oluşturma</span><span class="sxs-lookup"><span data-stu-id="05663-149">Create a Dockerfile related to an existing .NET base image</span></span>

<span data-ttu-id="05663-150">Derlemek istediğiniz her özel görüntü için bir Dockerfile ihtiyacınız; Ayrıca Visual Studio veya el ile Docker CLI'yı kullanarak otomatik olarak dağıtıp dağıtmamak dağıtılması için her kapsayıcı için bir Dockerfile gerekir (docker run ve docker-compose komutları).</span><span class="sxs-lookup"><span data-stu-id="05663-150">You need a Dockerfile for each custom image you want to build; you also need a Dockerfile for each container to be deployed, whether you deploy automatically from Visual Studio or manually using the Docker CLI (docker run and docker-compose commands).</span></span> <span data-ttu-id="05663-151">Uygulamanızda tek bir özel hizmet varsa, tek bir Dockerfile gerekir.</span><span class="sxs-lookup"><span data-stu-id="05663-151">If your application contains a single custom service, you need a single Dockerfile.</span></span> <span data-ttu-id="05663-152">Uygulamanız birden çok hizmeti (olduğu gibi bir mikro hizmetler mimarisinde) içeriyorsa, her hizmet için bir Dockerfile gerekir.</span><span class="sxs-lookup"><span data-stu-id="05663-152">If your application contains multiple services (as in a microservices architecture), you need one Dockerfile for each service.</span></span>

<span data-ttu-id="05663-153">Dockerfile, uygulamanızın veya hizmetinizin kök klasöründe yer alır.</span><span class="sxs-lookup"><span data-stu-id="05663-153">The Dockerfile is placed in the root folder of your application or service.</span></span> <span data-ttu-id="05663-154">Bu, Docker ayarlama ve bir kapsayıcıdaki uygulama veya hizmetinizin çalıştırma bildiririz komutlar içerir.</span><span class="sxs-lookup"><span data-stu-id="05663-154">It contains the commands that tell Docker how to set up and run your application or service in a container.</span></span> <span data-ttu-id="05663-155">El ile bir Dockerfile içinde kod oluşturma ve birlikte .NET bağımlılıklarınızı projenize ekleyin.</span><span class="sxs-lookup"><span data-stu-id="05663-155">You can manually create a Dockerfile in code and add it to your project along with your .NET dependencies.</span></span>

<span data-ttu-id="05663-156">Docker için Visual Studio Araçları sayesinde, bu görevi yalnızca birkaç tıklamayla gerektirir.</span><span class="sxs-lookup"><span data-stu-id="05663-156">With Visual Studio Tools for Docker, this task requires only a few mouse clicks.</span></span> <span data-ttu-id="05663-157">Visual Studio 2017'de yeni bir proje oluşturduğunuzda, adlı bir seçenek yoktur **Docker desteğini etkinleştir**Şekil 5-3'te gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="05663-157">When you create a new project in Visual Studio 2017, there's an option named **Enable Docker Support**, as shown in Figure 5-3.</span></span>

![Visual Studio 2017'de yeni bir proje oluştururken, Docker desteğini etkinleştirme](./media/image5.png)

<span data-ttu-id="05663-159">**Şekil 5-3**.</span><span class="sxs-lookup"><span data-stu-id="05663-159">**Figure 5-3**.</span></span> <span data-ttu-id="05663-160">Visual Studio 2017'de yeni bir proje oluştururken, Docker desteğini etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="05663-160">Enabling Docker Support when creating a new project in Visual Studio 2017</span></span>

<span data-ttu-id="05663-161">Projeye sağ tıklayarak mevcut bir .NET Core web uygulaması projesini Docker desteğini de etkinleştirebilirsiniz **Çözüm Gezgini** seçerek **Ekle** > **Docker desteği** Şekil 5-4'te gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="05663-161">You can also enable Docker support on an existing .NET Core web app project by right-clicking the project in **Solution Explorer** and selecting **Add** > **Docker Support**, as shown in Figure 5-4.</span></span>

![Visual Studio'da Docker desteği menü seçeneği ekleyin](./media/add-docker-support.png)

<span data-ttu-id="05663-163">**Şekil 5-4**.</span><span class="sxs-lookup"><span data-stu-id="05663-163">**Figure 5-4**.</span></span> <span data-ttu-id="05663-164">Mevcut bir Visual Studio 2017 projesinde Docker desteğini etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="05663-164">Enabling Docker support in an existing Visual Studio 2017 project</span></span>

<span data-ttu-id="05663-165">Bu eylem ekler bir *Dockerfile* gerekli yapılandırmayla projeye ve yalnızca .NET Core web uygulaması projelerinde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="05663-165">This action adds a *Dockerfile* to the project with the required configuration, and is only available on .NET Core web app projects.</span></span>

<span data-ttu-id="05663-166">Eklemek için bir *docker-compose.yml* bölümünde projeye sağ tıklayın, tüm çözüm için dosya **Çözüm Gezgini** seçip **Ekle**  >   **Kapsayıcı Düzenleyicisi desteği**Şekil 5-5'te gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="05663-166">To add a *docker-compose.yml* file for the whole solution, right-click on the project in **Solution Explorer** and select **Add** > **Container Orchestrator Support**, as shown in Figure 5-5.</span></span>

![Visual Studio'da kapsayıcı orchestrator destek menü seçeneği ekleyin](./media/add-container-orchestrator-support.png)

<span data-ttu-id="05663-168">**Şekil 5-5**.</span><span class="sxs-lookup"><span data-stu-id="05663-168">**Figure 5-5**.</span></span> <span data-ttu-id="05663-169">Visual Studio 2017'de var olan bir projeye eklenirken kapsayıcı Düzenleyicisi desteği.</span><span class="sxs-lookup"><span data-stu-id="05663-169">Adding container orchestrator support to an existing project in Visual Studio 2017.</span></span>

<span data-ttu-id="05663-170">Aşağıdaki bölümlerde, biz bu dosyaların her giden bilgiler açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="05663-170">In the following sections, we describe the information that goes into each of those files.</span></span> <span data-ttu-id="05663-171">Visual Studio bu işi sizin yerinize bunları yapar, ancak bir Dockerfile içinde unsurları anlamak kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="05663-171">Visual Studio can do this work for you, but it is useful to understand what goes into a Dockerfile.</span></span>

### <a name="option-a-creating-a-project-using-an-existing-official-net-docker-image"></a><span data-ttu-id="05663-172">Seçenek A: Var olan resmi .NET Docker görüntüsünü kullanarak bir proje oluşturma</span><span class="sxs-lookup"><span data-stu-id="05663-172">Option A: Creating a project using an existing official .NET Docker image</span></span>

<span data-ttu-id="05663-173">Genellikle resmi bir depodan alabilirsiniz bir temel görüntünün üstüne kapsayıcınızın özel bir görüntü oluşturun [Docker Hub](https://hub.docker.com/) kayıt defteri.</span><span class="sxs-lookup"><span data-stu-id="05663-173">You usually build a custom image for your container on top of a base image you can get from an official repository at the [Docker Hub](https://hub.docker.com/) registry.</span></span> <span data-ttu-id="05663-174">Visual Studio'da Docker desteğini etkinleştirmek ne olacağını perde tam olarak olmasıdır.</span><span class="sxs-lookup"><span data-stu-id="05663-174">That is precisely what happens under the covers when you enable Docker support in Visual Studio.</span></span> <span data-ttu-id="05663-175">Dockerfile, var olan bir aspnetcore görüntüsü kullanır.</span><span class="sxs-lookup"><span data-stu-id="05663-175">The Dockerfile uses an existing aspnetcore image.</span></span>

<span data-ttu-id="05663-176">Daha önce hangi Docker görüntülerini ve seçtiğiniz işletim sistemi ve framework bağlı olarak kullanabilirsiniz depoları açıklanmıştır.</span><span class="sxs-lookup"><span data-stu-id="05663-176">Earlier we explained which Docker images and repos you can use, depending on the framework and OS you have chosen.</span></span> <span data-ttu-id="05663-177">Örneğin, ASP.NET Core (Linux veya Windows) kullanmak istiyorsanız, kullanılacak görüntüyü microsoft, / aspnetcore:2.0.</span><span class="sxs-lookup"><span data-stu-id="05663-177">For instance, if you want to use ASP.NET Core (Linux or Windows), the image to use is microsoft/aspnetcore:2.0.</span></span> <span data-ttu-id="05663-178">Bu nedenle, kapsayıcınız için kullanacağınız hangi temel Docker görüntüsüne belirtmeniz yeterlidir.</span><span class="sxs-lookup"><span data-stu-id="05663-178">Therefore, you just need to specify what base Docker image you will use for your container.</span></span> <span data-ttu-id="05663-179">Microsoft'tan ekleyerek bunu / Dockerfile için aspnetcore:2.0.</span><span class="sxs-lookup"><span data-stu-id="05663-179">You do that by adding FROM microsoft/aspnetcore:2.0 to your Dockerfile.</span></span> <span data-ttu-id="05663-180">Bu Visual Studio tarafından otomatik olarak gerçekleştirilir, ancak sürüm olsaydı, bu değeri güncelleştirin.</span><span class="sxs-lookup"><span data-stu-id="05663-180">This is automatically performed by Visual Studio, but if you were to update the version, you update this value.</span></span>

<span data-ttu-id="05663-181">Bir sürüm numarası ile Docker Hub resmi bir .NET görüntü deposundan kullanarak aynı dil özellikleri (geliştirme, test ve üretim dahil) tüm makinelerde kullanılabilir olmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="05663-181">Using an official .NET image repository from Docker Hub with a version number ensures that the same language features are available on all machines (including development, testing, and production).</span></span>

<span data-ttu-id="05663-182">Aşağıdaki örnek bir ASP.NET Core kapsayıcı için bir örnek Dockerfile gösterir.</span><span class="sxs-lookup"><span data-stu-id="05663-182">The following example shows a sample Dockerfile for an ASP.NET Core container.</span></span>

```Dockerfile
FROM microsoft/aspnetcore:2.0

ARG source

WORKDIR /app

EXPOSE 80

COPY ${source:-obj/Docker/publish} .

ENTRYPOINT ["dotnet", " MySingleContainerWebApp.dll "]
```

<span data-ttu-id="05663-183">Bu durumda, kapsayıcı resmi ASP.NET Core Docker görüntü (Linux ve Windows için çok arch) 2.0 sürümünü temel alır.</span><span class="sxs-lookup"><span data-stu-id="05663-183">In this case, the container is based on version 2.0 of the official ASP.NET Core Docker image (multi-arch for Linux and Windows).</span></span> <span data-ttu-id="05663-184">Ayar budur `FROM microsoft/aspnetcore:2.0`.</span><span class="sxs-lookup"><span data-stu-id="05663-184">This is the setting `FROM microsoft/aspnetcore:2.0`.</span></span> <span data-ttu-id="05663-185">(Bu temel görüntü hakkında daha fazla bilgi için bkz: [ASP.NET Core, Docker görüntüsü](https://hub.docker.com/r/microsoft/aspnetcore/) sayfası ve [.NET Core, Docker görüntüsü](https://hub.docker.com/r/microsoft/dotnet/) sayfası.) Dockerfile içinde ayrıca isteyin (Bu durumda, SUNMAYA ayarı ile yapılandırılmış olarak 80 numaralı bağlantı noktası) çalışma zamanında kullanacağınız TCP bağlantı noktasında dinlemek için Docker gerekir.</span><span class="sxs-lookup"><span data-stu-id="05663-185">(For more information about this base image, see the [ASP.NET Core Docker Image](https://hub.docker.com/r/microsoft/aspnetcore/) page and the [.NET Core Docker Image](https://hub.docker.com/r/microsoft/dotnet/) page.) In the Dockerfile, you also need to instruct Docker to listen on the TCP port you will use at runtime (in this case, port 80, as configured with the EXPOSE setting).</span></span>

<span data-ttu-id="05663-186">Dil ve çerçeve kullanmakta olduğunuz bağlı olarak bir Dockerfile içinde ek yapılandırma ayarları belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="05663-186">You can specify additional configuration settings in the Dockerfile, depending on the language and framework you are using.</span></span> <span data-ttu-id="05663-187">Örneğin, giriş noktası satırla \["dotnet", "MySingleContainerWebApp.dll"\] bir .NET Core uygulamasını çalıştırmak için Docker söyler.</span><span class="sxs-lookup"><span data-stu-id="05663-187">For instance, the ENTRYPOINT line with \["dotnet", "MySingleContainerWebApp.dll"\] tells Docker to run a .NET Core application.</span></span> <span data-ttu-id="05663-188">.NET uygulaması derleme ve çalıştırma için SDK ve .NET Core CLI (dotnet CLI) kullanıyorsanız, bu ayar farklı olacaktır.</span><span class="sxs-lookup"><span data-stu-id="05663-188">If you are using the SDK and the .NET Core CLI (dotnet CLI) to build and run the .NET application, this setting would be different.</span></span> <span data-ttu-id="05663-189">ENTRYPOINT satır ve diğer ayarları uygulamanız için seçtiğiniz dile ve platforma bağlı olarak farklı olacaktır alt çizgidir.</span><span class="sxs-lookup"><span data-stu-id="05663-189">The bottom line is that the ENTRYPOINT line and other settings will be different depending on the language and platform you choose for your application.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="05663-190">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="05663-190">Additional resources</span></span>

- <span data-ttu-id="05663-191">**.NET Core Uygulamaları için Docker Görüntülerinizi Derleme**</span><span class="sxs-lookup"><span data-stu-id="05663-191">**Building Docker Images for .NET Core Applications**</span></span>

   [*https://docs.microsoft.com/dotnet/core/docker/building-net-docker-images*](../../../core/docker/building-net-docker-images.md)

- <span data-ttu-id="05663-192">**Kendi görüntünüzü**.</span><span class="sxs-lookup"><span data-stu-id="05663-192">**Build your own image**.</span></span> <span data-ttu-id="05663-193">Resmi Docker belgelerinde.</span><span class="sxs-lookup"><span data-stu-id="05663-193">In the official Docker documentation.</span></span>

   [*https://docs.docker.com/engine/tutorials/dockerimages/*](https://docs.docker.com/engine/tutorials/dockerimages/)

### <a name="using-multi-arch-image-repositories"></a><span data-ttu-id="05663-194">Çok yay görüntü depolarını kullanarak</span><span class="sxs-lookup"><span data-stu-id="05663-194">Using multi-arch image repositories</span></span>

<span data-ttu-id="05663-195">Tek bir depoda bir Linux görüntüsü ve bir Windows görüntüsünü gibi platformu çeşitleri içerebilir.</span><span class="sxs-lookup"><span data-stu-id="05663-195">A single repo can contain platform variants, such as a Linux image and a Windows image.</span></span> <span data-ttu-id="05663-196">Bu özellik, (yani Linux ve Windows) birden çok platform karşılamak için tek depo oluşturmak Microsoft (temel Görüntü Oluşturucu) gibi satıcıları sağlar.</span><span class="sxs-lookup"><span data-stu-id="05663-196">This feature allows vendors like Microsoft (base image creators) to create a single repo to cover multiple platforms (that is Linux and Windows).</span></span> <span data-ttu-id="05663-197">Örneğin, [microsoft/dotnet](https://hub.docker.com/r/microsoft/aspnetcore/) Docker Hub kayıt defterinde depo aynı depo adını kullanarak Linux ve Windows Nano sunucu için destek sağlar.</span><span class="sxs-lookup"><span data-stu-id="05663-197">For example, the [microsoft/dotnet](https://hub.docker.com/r/microsoft/aspnetcore/) repository available in the Docker Hub registry provides support for Linux and Windows Nano Server by using the same repo name.</span></span>

<span data-ttu-id="05663-198">Açık bir platformu hedefleyen bir etiket belirtirseniz, aşağıdaki durumlarda ister:</span><span class="sxs-lookup"><span data-stu-id="05663-198">If you specify a tag, targeting a platform that is explicit like in the following cases:</span></span>

- <span data-ttu-id="05663-199">**Microsoft/aspnetcore:2.0.0-jessie**</span><span class="sxs-lookup"><span data-stu-id="05663-199">**microsoft/aspnetcore:2.0.0-jessie**</span></span>

        .NET Core 2.0 runtime-only on Linux

- <span data-ttu-id="05663-200">**Microsoft/aspnetcore:2.0.0-nanoserver**</span><span class="sxs-lookup"><span data-stu-id="05663-200">**microsoft/aspnetcore:2.0.0-nanoserver**</span></span>

        .NET Core 2.0 runtime-only on Windows Nano Server

<span data-ttu-id="05663-201">Ancak ve belirtirseniz bu yeni mid-2017 itibarıyla, hatta aynı etiketi ile aynı görüntü adı, yeni çok yay görüntülerini (gibi çok arch destekler aspnetcore görüntüsü) bağlı dağıttığınız Docker ana bilgisayar işletim sistemi olarak Linux veya Windows sürümü kullanır , aşağıdaki örnekte gösterildiği gibi:</span><span class="sxs-lookup"><span data-stu-id="05663-201">But, and this is new since mid-2017, if you specify the same image name, even with the same tag, the new multi-arch images (like the aspnetcore image, which supports multi-arch) will use the Linux or Windows version depending on the Docker host OS you are deploying, as shown in the following example:</span></span>

- <span data-ttu-id="05663-202">**Microsoft / aspnetcore:2.0**</span><span class="sxs-lookup"><span data-stu-id="05663-202">**microsoft/aspnetcore:2.0**</span></span>

        Multi-arch: .NET Core 2.0 runtime-only on Linux or Windows Nano Server depending on the Docker host OS

<span data-ttu-id="05663-203">Windows konaktan görüntü çekme bu şekilde, Windows değişken çeker ve bir Linux ana bilgisayarından görüntü adının aynısını çekme Linux değişken çeker.</span><span class="sxs-lookup"><span data-stu-id="05663-203">This way, when you pull an image from a Windows host, it will pull the Windows variant, and pulling the same image name from a Linux host will pull the Linux variant.</span></span>

### <a name="option-b-creating-your-base-image-from-scratch"></a><span data-ttu-id="05663-204">Seçenek B: Temel görüntünüzü sıfırdan oluşturma</span><span class="sxs-lookup"><span data-stu-id="05663-204">Option B: Creating your base image from scratch</span></span>

<span data-ttu-id="05663-205">Kendi Docker temel görüntüsünde sıfırdan oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="05663-205">You can create your own Docker base image from scratch.</span></span> <span data-ttu-id="05663-206">Bu senaryo için Docker ile başlayan bir kişinin önerilmez, ancak kendi temel görüntü belirli bitlerini ayarlamak istiyorsanız, bunu yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="05663-206">This scenario is not recommended for someone who is starting with Docker, but if you want to set the specific bits of your own base image, you can do so.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="05663-207">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="05663-207">Additional resources</span></span>

- <span data-ttu-id="05663-208">**.NET Core görüntüleri çok yay**.</span><span class="sxs-lookup"><span data-stu-id="05663-208">**Multi-arch .NET Core images**.</span></span>

   https://github.com/dotnet/announcements/issues/14

- <span data-ttu-id="05663-209">**Temel görüntü oluşturma**.</span><span class="sxs-lookup"><span data-stu-id="05663-209">**Create a base image**.</span></span> <span data-ttu-id="05663-210">Resmi Docker belgeleri.</span><span class="sxs-lookup"><span data-stu-id="05663-210">Official Docker documentation.</span></span>

   [*https://docs.docker.com/engine/userguide/eng-image/baseimages/*](https://docs.docker.com/engine/userguide/eng-image/baseimages/)

![3. adım - görüntü grafiğini oluşturun](./media/image7.png)

## <a name="step-3-create-your-custom-docker-images-and-embed-your-application-or-service-in-them"></a><span data-ttu-id="05663-212">Adım 3.</span><span class="sxs-lookup"><span data-stu-id="05663-212">Step 3.</span></span> <span data-ttu-id="05663-213">Özel Docker görüntülerinizi oluşturmak ve uygulamanızın veya hizmetinizin bunları ekleme</span><span class="sxs-lookup"><span data-stu-id="05663-213">Create your custom Docker images and embed your application or service in them</span></span>

<span data-ttu-id="05663-214">Uygulamanızdaki her hizmet için ilgili görüntü oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="05663-214">For each service in your application, you need to create a related image.</span></span> <span data-ttu-id="05663-215">Uygulamanızı bir tek bir hizmeti veya web uygulaması oluşur, tek bir görüntü yeterlidir.</span><span class="sxs-lookup"><span data-stu-id="05663-215">If your application is made up of a single service or web application, you just need a single image.</span></span>

<span data-ttu-id="05663-216">Docker görüntülerini otomatik olarak sizin için Visual Studio'da yerleşiktir.</span><span class="sxs-lookup"><span data-stu-id="05663-216">The Docker images are built automatically for you in Visual Studio.</span></span> <span data-ttu-id="05663-217">Aşağıdaki adımlar yalnızca Düzenleyici/CLI iş akışı için gereken ve altında olabilecekler açıklık için açıklanmıştır.</span><span class="sxs-lookup"><span data-stu-id="05663-217">The following steps are only needed for the editor/CLI workflow and explained for clarity about what happens underneath.</span></span>

<span data-ttu-id="05663-218">Geliştirme ve yerel olarak bir tamamlanmış itinceye kadar test için geliştirici olarak, ihtiyaç duyduğunuz, özelliği veya kaynak denetim sisteminize (örneğin GitHub) değiştirin.</span><span class="sxs-lookup"><span data-stu-id="05663-218">You, as developer, need to develop and test locally until you push a completed feature or change to your source control system (for example, to GitHub).</span></span> <span data-ttu-id="05663-219">Bu, Docker görüntüleri oluşturun ve kapsayıcıları yerel Docker konağı için (Windows veya Linux VM) dağıtın ve çalıştırın, test ve yerel kapsayıcıların karşı hata ayıklama gerektiği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="05663-219">This means that you need to create the Docker images and deploy containers to a local Docker host (Windows or Linux VM) and run, test, and debug against those local containers.</span></span>

<span data-ttu-id="05663-220">Özel bir görüntü yerel ortamınızda Docker CLI ve Dockerfile'ı kullanarak oluşturmak için docker oluşturma komutu, Şekil 5-5'olduğu gibi kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="05663-220">To create a custom image in your local environment by using Docker CLI and your Dockerfile, you can use the docker build command, as in Figure 5-5.</span></span>

![Özel bir Docker görüntüsü oluşturma](./media/image8.png)

<span data-ttu-id="05663-222">**Şekil 5-5**.</span><span class="sxs-lookup"><span data-stu-id="05663-222">**Figure 5-5**.</span></span> <span data-ttu-id="05663-223">Özel bir Docker görüntüsü oluşturma</span><span class="sxs-lookup"><span data-stu-id="05663-223">Creating a custom Docker image</span></span>

<span data-ttu-id="05663-224">İsteğe bağlı olarak, doğrudan docker derleme proje klasöründen çalıştırmak, yerine, önce gerekli .NET kitaplıkları ile dağıtılabilir bir klasör oluşturabilirsiniz ve dotnet çalıştırarak ikili dosyaları yayımlayın ve ardından docker derleme komutunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="05663-224">Optionally, instead of directly running docker build from the project folder, you can first generate a deployable folder with the required .NET libraries and binaries by running dotnet publish, and then use the docker build command.</span></span>

<span data-ttu-id="05663-225">Bu ada sahip bir Docker görüntüsü oluşturacak **cesardl/netcore-webapı-mikro hizmet-docker: ilk**.</span><span class="sxs-lookup"><span data-stu-id="05663-225">This will create a Docker image with the name **cesardl/netcore-webapi-microservice-docker:first**.</span></span> <span data-ttu-id="05663-226">Bu durumda: öncelikle, belirli bir sürümü temsil eden bir etiketi olan.</span><span class="sxs-lookup"><span data-stu-id="05663-226">In this case, :first is a tag representing a specific version.</span></span> <span data-ttu-id="05663-227">Oluşturulmuş Docker uygulamanız için oluşturmak için gereken her özel bir görüntü için bu adımı yineleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="05663-227">You can repeat this step for each custom image you need to create for your composed Docker application.</span></span>

<span data-ttu-id="05663-228">Bir uygulama birden çok kapsayıcılardan yapılan ne zaman (diğer bir deyişle, çok kapsayıcılı bir uygulama olduğu), ayrıca docker compose up--ilgili kullanıma sunulan meta verileri kullanarak tek bir komutla ilgili tüm görüntüleri oluşturmak için yapı komutu docker-compose.yml dosyaları.</span><span class="sxs-lookup"><span data-stu-id="05663-228">When an application is made of multiple containers (that is, it is a multi-container application), you can also use the docker-compose up --build command to build all the related images with a single command by using the metadata exposed in the related docker-compose.yml files.</span></span>

<span data-ttu-id="05663-229">Var olan görüntülerden yerel deponuzda docker'ı kullanarak görüntü komutu, Şekil 5-6'da gösterildiği gibi bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="05663-229">You can find the existing images in your local repository by using the docker images command, as shown in Figure 5-6.</span></span>

![Docker görüntüleri komutunu kullanarak var olan görüntüleri görüntüleme](./media/image9.png)

<span data-ttu-id="05663-231">**Şekil 5-6.**</span><span class="sxs-lookup"><span data-stu-id="05663-231">**Figure 5-6.**</span></span> <span data-ttu-id="05663-232">Docker görüntüleri komutunu kullanarak var olan görüntüleri görüntüleme</span><span class="sxs-lookup"><span data-stu-id="05663-232">Viewing existing images using the docker images command</span></span>

### <a name="creating-docker-images-with-visual-studio"></a><span data-ttu-id="05663-233">Visual Studio ile Docker görüntüleri oluşturma</span><span class="sxs-lookup"><span data-stu-id="05663-233">Creating Docker images with Visual Studio</span></span>

<span data-ttu-id="05663-234">Docker desteği bir proje oluşturmak için Visual Studio kullandığınızda, bir görüntü açıkça oluşturmayın.</span><span class="sxs-lookup"><span data-stu-id="05663-234">When you use Visual Studio to create a project with Docker support, you don't explicitly create an image.</span></span> <span data-ttu-id="05663-235">Bastığınızda bunun yerine, görüntünün sizin için oluşturulan **F5** dockerized uygulamaya veya hizmete çalıştırılacak.</span><span class="sxs-lookup"><span data-stu-id="05663-235">Instead, the image is created for you when you press **F5** to run the dockerized application or service.</span></span> <span data-ttu-id="05663-236">Bu adım Visual Studio'da otomatik olarak yapılır ve durum göremezsiniz ancak neler olduğunu bilmeniz önemlidir üzerinde underneath.</span><span class="sxs-lookup"><span data-stu-id="05663-236">This step is automatic in Visual Studio and you won't see it happen, but it's important that you know what's going on underneath.</span></span>

![4. adım - services grafiği tanımlayın](./media/image10.png)

## <a name="step-4-define-your-services-in-docker-composeyml-when-building-a-multi-container-docker-application"></a><span data-ttu-id="05663-238">4. adımı.</span><span class="sxs-lookup"><span data-stu-id="05663-238">Step 4.</span></span> <span data-ttu-id="05663-239">Çok kapsayıcılı Docker uygulaması oluştururken, docker-compose.yml hizmetlerinizi tanımlayın</span><span class="sxs-lookup"><span data-stu-id="05663-239">Define your services in docker-compose.yml when building a multi-container Docker application</span></span>

<span data-ttu-id="05663-240">[Docker-compose.yml](https://docs.docker.com/compose/compose-file/) dosya dağıtım komutları ile oluşturulmuş bir uygulama olarak dağıtılması için ilgili bir hizmetler kümesi tanımlamanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="05663-240">The [docker-compose.yml](https://docs.docker.com/compose/compose-file/) file lets you define a set of related services to be deployed as a composed application with deployment commands.</span></span>

<span data-ttu-id="05663-241">Docker-compose.yml dosyası kullanmak için aşağıdaki örnekte benzer içeriğe sahip ana dosyasında veya kök Çözüm klasörü'ı oluşturmanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="05663-241">To use a docker-compose.yml file, you need to create the file in your main or root solution folder, with content similar to that in the following example:</span></span>

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

<span data-ttu-id="05663-242">Bu docker-compose.yml dosyası basit ve birleştirilmiş bir sürümüdür.</span><span class="sxs-lookup"><span data-stu-id="05663-242">This docker-compose.yml file is a simplified and merged version.</span></span> <span data-ttu-id="05663-243">Bu, her zaman, bağlantı dizesi gibi dağıtım ortamı bağımlı olabileceği yapılandırma bilgilerini artı uygulanan her bir kapsayıcı (adı gibi özel görüntü), statik yapılandırma verilerini içerir.</span><span class="sxs-lookup"><span data-stu-id="05663-243">It contains static configuration data for each container (like the name of the custom image), which always applies, plus configuration information that might depend on the deployment environment, like the connection string.</span></span> <span data-ttu-id="05663-244">Sonraki bölümlerde, docker-compose.yml yapılandırmanın birden çok nasıl bölebilirsiniz öğreneceksiniz docker compose dosyaları ve geçersiz kılma değerleri (hata ayıklama veya sürüm) ortamını ve yürütme türüne bağlı olarak.</span><span class="sxs-lookup"><span data-stu-id="05663-244">In later sections, you will learn how you can split the docker-compose.yml configuration into multiple docker-compose files and override values depending on the environment and execution type (debug or release).</span></span>

<span data-ttu-id="05663-245">Docker-compose.yml dosyası örneği dört hizmet tanımlar: webmvc service (web uygulaması), (catalog.api ve ordering.api) iki mikro hizmet ve kapsayıcı olarak çalışan Linux SQL Server tabanlı bir veri kaynağı kapsayıcı, sql.data,.</span><span class="sxs-lookup"><span data-stu-id="05663-245">The docker-compose.yml file example defines four services: the webmvc service (a web application), two microservices (catalog.api and ordering.api), and one data source container, sql.data, based on SQL Server for Linux running as a container.</span></span> <span data-ttu-id="05663-246">Her biri için gerekli bir Docker görüntüsü, bu nedenle, her hizmetin bir kapsayıcı olarak dağıtılır.</span><span class="sxs-lookup"><span data-stu-id="05663-246">Each service is deployed as a container, so a Docker image is required for each.</span></span>

<span data-ttu-id="05663-247">Docker-compose.yml dosyası, yalnızca kapsayıcıların ne kullanılır, ancak ayrı ayrı yapılandırmaya belirtir.</span><span class="sxs-lookup"><span data-stu-id="05663-247">The docker-compose.yml file specifies not only what containers are being used, but how they are individually configured.</span></span> <span data-ttu-id="05663-248">Örneğin, webmvc kapsayıcısı tanımında .yml dosyası:</span><span class="sxs-lookup"><span data-stu-id="05663-248">For instance, the webmvc container definition in the .yml file:</span></span>

- <span data-ttu-id="05663-249">Önceden oluşturulmuş bir elektronik mağaza kullanan / web: son görüntü.</span><span class="sxs-lookup"><span data-stu-id="05663-249">Uses a pre-built eshop/web:latest image.</span></span> <span data-ttu-id="05663-250">Ancak, aynı zamanda bir parçası olarak oluşturulacak görüntünün yapılandırabilirsiniz docker-compose temelli bir derleme üzerinde yürütme ek bir yapılandırma: docker-compose dosyasındaki bölümü.</span><span class="sxs-lookup"><span data-stu-id="05663-250">However, you could also configure the image to be built as part of the docker-compose execution with an additional configuration based on a build: section in the docker-compose file.</span></span>

- <span data-ttu-id="05663-251">İki ortam değişkenlerini (katalog URL'si ve OrderingUrl) başlatır.</span><span class="sxs-lookup"><span data-stu-id="05663-251">Initializes two environment variables (CatalogUrl and OrderingUrl).</span></span>

- <span data-ttu-id="05663-252">Konak makinedeki dış bağlantı noktası 80 kapsayıcı üzerindeki 80 kullanıma sunulan bağlantı noktası iletir.</span><span class="sxs-lookup"><span data-stu-id="05663-252">Forwards the exposed port 80 on the container to the external port 80 on the host machine.</span></span>

- <span data-ttu-id="05663-253">Web uygulaması katalog ve sıralama hizmetiyle bağlantı bağlıdır\_ayarı.</span><span class="sxs-lookup"><span data-stu-id="05663-253">Links the web app to the catalog and ordering service with the depends\_on setting.</span></span> <span data-ttu-id="05663-254">Bu hizmet, bu hizmetleri yeniden başlatılana kadar beklenecek neden olur.</span><span class="sxs-lookup"><span data-stu-id="05663-254">This causes the service to wait until those services are started.</span></span>

<span data-ttu-id="05663-255">Mikro hizmetler ve çok kapsayıcılı uygulamalar uygulamak nasıl ele, biz bir sonraki bölümde docker-compose.yml dosyası yeniden ziyaret.</span><span class="sxs-lookup"><span data-stu-id="05663-255">We will revisit the docker-compose.yml file in a later section when we cover how to implement microservices and multi-container apps.</span></span>

### <a name="working-with-docker-composeyml-in-visual-studio-2017"></a><span data-ttu-id="05663-256">Visual Studio 2017'de docker-compose.yml ile çalışma</span><span class="sxs-lookup"><span data-stu-id="05663-256">Working with docker-compose.yml in Visual Studio 2017</span></span>

<span data-ttu-id="05663-257">Şekil 5-7'de gösterildiği gibi bir web uygulaması projesine kapsayıcı Düzenleyicisi desteği eklediğinizde, Visual Studio bir hizmet bölümü (Proje) docker-compose.yml dosyasını içeren çözüme ekler.</span><span class="sxs-lookup"><span data-stu-id="05663-257">When you add container orchestrator support to a web app project, as shown in Figure 5-7, Visual Studio adds a service section (project) to the solution that contains a docker-compose.yml file.</span></span> <span data-ttu-id="05663-258">Bu, bir çoklu kapsayıcı çözümü düzenlemeye başlamanın kolay bir yoludur.</span><span class="sxs-lookup"><span data-stu-id="05663-258">This is an easy way to start composing a multiple-container solution.</span></span>

![Visual Studio'da kapsayıcı orchestrator destek menü öğesi ekleme](./media/add-container-orchestrator-support.png)

<span data-ttu-id="05663-260">**Şekil 5-7**.</span><span class="sxs-lookup"><span data-stu-id="05663-260">**Figure 5-7**.</span></span> <span data-ttu-id="05663-261">Bir ASP.NET Core projesi sağ tıklayarak Visual Studio 2017'de Docker desteği ekleme</span><span class="sxs-lookup"><span data-stu-id="05663-261">Adding Docker support in Visual Studio 2017 by right-clicking an ASP.NET Core project</span></span>

<span data-ttu-id="05663-262">Kapsayıcı Düzenleyicisi desteği ekleme (zaten yoksa) Dockerfile, projenize ekler.</span><span class="sxs-lookup"><span data-stu-id="05663-262">Adding container orchestrator support adds the Dockerfile to your project (if it doesn't already exist).</span></span> <span data-ttu-id="05663-263">Ayrıca çözüm düzeyinde bir genel docker-compose.yml dosyası için yapılandırma bilgilerini ekler.</span><span class="sxs-lookup"><span data-stu-id="05663-263">It also adds configuration information to a global docker-compose.yml file at the solution level.</span></span> <span data-ttu-id="05663-264">Yeni bir proje düğümünü göreceksiniz ( *docker compose.dcproj* proje dosyası) içinde **Çözüm Gezgini** Şekil 5-8'de gösterildiği gibi docker-compose.yml dosyasını içeren.</span><span class="sxs-lookup"><span data-stu-id="05663-264">You'll see a new project node (the *docker-compose.dcproj* project file) in **Solution Explorer** that contains the docker-compose.yml file, as shown in Figure 5-8.</span></span>

![Çözüm Gezgininde docker-compose](./media/docker-compose-files.png)

<span data-ttu-id="05663-266">**Şekil 5-8**.</span><span class="sxs-lookup"><span data-stu-id="05663-266">**Figure 5-8**.</span></span> <span data-ttu-id="05663-267">**Docker-compose** Visual Studio 2017 Çözüm Gezgini'nde eklenen ağaç düğümü</span><span class="sxs-lookup"><span data-stu-id="05663-267">The **docker-compose** tree node added in Visual Studio 2017 Solution Explorer</span></span>

<span data-ttu-id="05663-268">Ardından, docker-compose.yml dosyasını açın ve ek özellikler ile güncelleştirin.</span><span class="sxs-lookup"><span data-stu-id="05663-268">You can then open the docker-compose.yml file and update it with additional features.</span></span>

<span data-ttu-id="05663-269">Kullanarak bir docker-compose.yml dosyası ile çok kapsayıcılı bir uygulama dağıtabilirsiniz `docker-compose up` komutu.</span><span class="sxs-lookup"><span data-stu-id="05663-269">You can deploy a multi-container application with a single docker-compose.yml file by using the `docker-compose up` command.</span></span>

![Adım 5 - çalışma uygulama grafiği](./media/image12.png)

## <a name="step-5-build-and-run-your-docker-application"></a><span data-ttu-id="05663-271">5. adımı.</span><span class="sxs-lookup"><span data-stu-id="05663-271">Step 5.</span></span> <span data-ttu-id="05663-272">Kendi Docker uygulaması derleme ve çalıştırma</span><span class="sxs-lookup"><span data-stu-id="05663-272">Build and run your Docker application</span></span>

<span data-ttu-id="05663-273">Uygulamanız yalnızca tek bir kapsayıcıya sahip değilse, Docker Konağı (VM veya fiziksel sunucu) dağıtarak çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="05663-273">If your application only has a single container, you can run it by deploying it to your Docker host (VM or physical server).</span></span> <span data-ttu-id="05663-274">Uygulamanız birden fazla hizmet içeriyor, ancak bunu oluşan bir uygulama olarak ya da tek bir CLI komutu kullanarak dağıtabilirsiniz (docker-compose ayarlama), veya Visual Studio ile bu komut aslında altında kullanacak.</span><span class="sxs-lookup"><span data-stu-id="05663-274">However, if your application contains multiple services, you can deploy it as a composed application, either using a single CLI command (docker-compose up), or with Visual Studio, which will use that command under the covers.</span></span> <span data-ttu-id="05663-275">Farklı seçenekleri göz atalım.</span><span class="sxs-lookup"><span data-stu-id="05663-275">Let’s look at the different options.</span></span>

### <a name="option-a-run-a-single-container-app"></a><span data-ttu-id="05663-276">Seçenek A: Tek kapsayıcı uygulamasını çalıştırma</span><span class="sxs-lookup"><span data-stu-id="05663-276">Option A: Run a single-container app</span></span>

#### <a name="docker-cli"></a><span data-ttu-id="05663-277">Docker CLI</span><span class="sxs-lookup"><span data-stu-id="05663-277">Docker CLI</span></span>

<span data-ttu-id="05663-278">Şekil 5-9'olduğu gibi komutu çalıştırın: docker kullanarak Docker kapsayıcısı çalıştırabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="05663-278">You can run a Docker container using the docker run command, as in Figure 5-9:</span></span>

```console
  docker run -t -d -p 80:5000 cesardl/netcore-webapi-microservice-docker:first
```

![Komutu çalıştırarak docker kullanarak Docker kapsayıcı çalıştırma](./media/image13.png)

<span data-ttu-id="05663-280">**Şekil 5-9**.</span><span class="sxs-lookup"><span data-stu-id="05663-280">**Figure 5-9**.</span></span> <span data-ttu-id="05663-281">Komutu çalıştırarak docker kullanarak Docker kapsayıcı çalıştırma</span><span class="sxs-lookup"><span data-stu-id="05663-281">Running a Docker container using the docker run command</span></span>

<span data-ttu-id="05663-282">Bu durumda, komut kapsayıcının iç bağlantı noktası 5000 ana makinenin 80 numaralı bağlantı noktasına bağlar.</span><span class="sxs-lookup"><span data-stu-id="05663-282">In this case, the command binds the internal port 5000 of the container to port 80 of the host machine.</span></span> <span data-ttu-id="05663-283">Bu konak 80 numaralı bağlantı noktasında dinleme ve kapsayıcıda genericread 5000 numaralı bağlantı noktasına ileten anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="05663-283">This means that the host is listening on port 80 and forwarding to port 5000 on the container.</span></span>

#### <a name="visual-studio"></a><span data-ttu-id="05663-284">Visual Studio</span><span class="sxs-lookup"><span data-stu-id="05663-284">Visual Studio</span></span>

<span data-ttu-id="05663-285">Kapsayıcı Düzenleyicisi desteği eklemediyseniz, ayrıca bir çoklu kapsayıcı uygulaması Visual Studio'da tuşlarına basarak çalıştırabileceğiniz **F5**.</span><span class="sxs-lookup"><span data-stu-id="05663-285">If you haven't added container orchestrator support, you can also run a single container app in Visual Studio by pressing **F5**.</span></span> <span data-ttu-id="05663-286">Kapsayıcı, docker run kullanarak yerel olarak çalışır.</span><span class="sxs-lookup"><span data-stu-id="05663-286">The container runs locally using docker run.</span></span>

### <a name="option-b-run-a-multi-container-app"></a><span data-ttu-id="05663-287">Seçenek B: Bir çoklu kapsayıcı uygulaması</span><span class="sxs-lookup"><span data-stu-id="05663-287">Option B: Run a multi-container app</span></span>

<span data-ttu-id="05663-288">Çoğu Kurumsal senaryolarda, Docker uygulaması birden çok Hizmetleri, Şekil 5-10'da gösterildiği gibi çok kapsayıcılı bir uygulama çalıştırmak gereken yani oluşacaktır.</span><span class="sxs-lookup"><span data-stu-id="05663-288">In most enterprise scenarios, a Docker application will be composed of multiple services, which means you need to run a multi-container application, as shown in Figure 5-10.</span></span>

![VM ile dağıtılan Docker kapsayıcılarının gösteren grafik](./media/image14.png)

<span data-ttu-id="05663-290">**Şekil 5-10**.</span><span class="sxs-lookup"><span data-stu-id="05663-290">**Figure 5-10**.</span></span> <span data-ttu-id="05663-291">Dağıtılmış Docker kapsayıcıları ile VM</span><span class="sxs-lookup"><span data-stu-id="05663-291">VM with Docker containers deployed</span></span>

#### <a name="docker-cli"></a><span data-ttu-id="05663-292">Docker CLI</span><span class="sxs-lookup"><span data-stu-id="05663-292">Docker CLI</span></span>

<span data-ttu-id="05663-293">Docker CLI ile çok kapsayıcılı bir uygulama çalıştırmak için docker çalıştırabilirsiniz-compose komutu.</span><span class="sxs-lookup"><span data-stu-id="05663-293">To run a multi-container application with the Docker CLI, you can run the docker-compose up command.</span></span> <span data-ttu-id="05663-294">Bu komut kullandığı docker-compose.yml dosyası çok kapsayıcılı bir uygulama dağıtmak için çözüm düzeyinde olması.</span><span class="sxs-lookup"><span data-stu-id="05663-294">This command uses the docker-compose.yml file that you have at the solution level to deploy a multi-container application.</span></span> <span data-ttu-id="05663-295">Şekil 5-11 komut docker-compose.yml dosyasını içeren ana proje dizininden çalıştırılırken sonuçları gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="05663-295">Figure 5-11 shows the results when running the command from your main project directory, which contains the docker-compose.yml file.</span></span>

![Örnek sonuçları çalıştırırken docker-compose komutu](./media/image15.png)

<span data-ttu-id="05663-297">**Şekil 5-11**.</span><span class="sxs-lookup"><span data-stu-id="05663-297">**Figure 5-11**.</span></span> <span data-ttu-id="05663-298">Örnek sonuçları çalıştırırken docker-compose komutu</span><span class="sxs-lookup"><span data-stu-id="05663-298">Example results when running the docker-compose up command</span></span>

<span data-ttu-id="05663-299">Sonra docker-compose komutu çalıştırmaları, uygulama ve onun ilişkili kapsayıcılar, Docker ana bilgisayara dağıtılır.</span><span class="sxs-lookup"><span data-stu-id="05663-299">After the docker-compose up command runs, the application and its related containers are deployed into your Docker host.</span></span>

#### <a name="visual-studio"></a><span data-ttu-id="05663-300">Visual Studio</span><span class="sxs-lookup"><span data-stu-id="05663-300">Visual Studio</span></span>

<span data-ttu-id="05663-301">Visual Studio 2017'yi kullanarak çok kapsayıcılı bir uygulama çalıştıran basit bir işlemdir.</span><span class="sxs-lookup"><span data-stu-id="05663-301">Running a multi-container application using Visual Studio 2017 is simple.</span></span> <span data-ttu-id="05663-302">Yalnızca, çok kapsayıcılı bir uygulama çalıştırabilirsiniz, ancak doğrudan Visual Studio'dan tüm kapsayıcıları ayarı tarafından normal kesme noktaları hata ayıklamanız mümkün.</span><span class="sxs-lookup"><span data-stu-id="05663-302">Not only can you run the multi-container application, but you're able to debug all its containers directly from Visual Studio by setting regular breakpoints.</span></span>

<span data-ttu-id="05663-303">Her bir çözüm içinde bir proje için kapsayıcı Düzenleyicisi desteği eklemeden önce belirtildiği gibi proje çalıştırın veya çözümün tamamının aynı anda hata ayıklama olanak sağlayan genel (Çözüm düzeyinde) docker-compose.yml dosyasında yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="05663-303">As mentioned before, each time you add container orchestrator support to a project within a solution, that project is configured in the global (solution-level) docker-compose.yml file, which lets you run or debug the whole solution at once.</span></span> <span data-ttu-id="05663-304">Visual Studio Docker çözümü desteği etkin olan her proje için bir kapsayıcı başlatın ve iç tüm adımları gerçekleştirdiğiniz (dotnet yayımlama, docker derleme, vs.).</span><span class="sxs-lookup"><span data-stu-id="05663-304">Visual Studio will start one container for each project that has Docker solution support enabled and perform all the internal steps for you (dotnet publish, docker build, etc.).</span></span>

<span data-ttu-id="05663-305">Burada önemli olan nokta Şekil 5-12'de gösterildiği gibi Visual Studio 2017'de, ek bir yoktur **Docker** komutunu **F5** anahtar eylem.</span><span class="sxs-lookup"><span data-stu-id="05663-305">The important point here is that, as shown in Figure 5-12, in Visual Studio 2017 there's an additional **Docker** command for the **F5** key action.</span></span> <span data-ttu-id="05663-306">Bu seçenek çalıştırın ya da docker-compose.yml dosyaları çözüm düzeyinde tanımlanan tüm kapsayıcıları çalıştırarak çok kapsayıcılı bir uygulama hata ayıklama sağlar.</span><span class="sxs-lookup"><span data-stu-id="05663-306">This option lets you run or debug a multi-container application by running all the containers that are defined in the docker-compose.yml files at the solution level.</span></span> <span data-ttu-id="05663-307">Birden çok kapsayıcı çözümleri hata ayıklama özelliği (kapsayıcı) farklı bir projede birkaç kesme noktaları, her bir kesme noktası ayarlayın ve Visual Studio'dan hata ayıklama sırasında farklı projelerde tanımlanan ve çalıştırılan kesme noktalarında durdurur anlamına gelir. farklı kapsayıcılar.</span><span class="sxs-lookup"><span data-stu-id="05663-307">The ability to debug multiple-container solutions means that you can set several breakpoints, each breakpoint in a different project (container), and while debugging from Visual Studio you will stop at breakpoints defined in different projects and running on different containers.</span></span>

![Visual Studio 2017'de çalışan çok kapsayıcılı uygulamalar](./media/image16.png)

<span data-ttu-id="05663-309">**Şekil 5-12**.</span><span class="sxs-lookup"><span data-stu-id="05663-309">**Figure 5-12**.</span></span> <span data-ttu-id="05663-310">Visual Studio 2017'de çalışan çok kapsayıcılı uygulamalar</span><span class="sxs-lookup"><span data-stu-id="05663-310">Running multi-container apps in Visual Studio 2017</span></span>

### <a name="additional-resources"></a><span data-ttu-id="05663-311">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="05663-311">Additional resources</span></span>

-  <span data-ttu-id="05663-312">**ASP.NET kapsayıcısını uzak Docker konağı için dağıtma**</span><span class="sxs-lookup"><span data-stu-id="05663-312">**Deploy an ASP.NET container to a remote Docker host**</span></span>

   [*https://docs.microsoft.com/azure/vs-azure-tools-docker-hosting-web-apps-in-docker*](https://docs.microsoft.com/azure/vs-azure-tools-docker-hosting-web-apps-in-docker)

### <a name="a-note-about-testing-and-deploying-with-orchestrators"></a><span data-ttu-id="05663-313">Test etme ve dağıtma düzenleyicilerle hakkında bir Not</span><span class="sxs-lookup"><span data-stu-id="05663-313">A note about testing and deploying with orchestrators</span></span>

<span data-ttu-id="05663-314">Docker compose up ve docker run komutları (veya çalışan ve kapsayıcıları Visual Studio'da hata ayıklama) kapsayıcıları geliştirme ortamınızda test etmek için yeterli.</span><span class="sxs-lookup"><span data-stu-id="05663-314">The docker-compose up and docker run commands (or running and debugging the containers in Visual Studio) are adequate for testing containers in your development environment.</span></span> <span data-ttu-id="05663-315">Ancak, bu yaklaşım Docker kümeleri hedefleniyorsa ve Docker Swarm, Mesosphere DC/OS veya Kubernetes düzenleyicileri gibi kullanmamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="05663-315">But you should not use this approach if you are targeting Docker clusters and orchestrators like Docker Swarm, Mesosphere DC/OS, or Kubernetes.</span></span> <span data-ttu-id="05663-316">Gibi bir küme kullanıyorsanız [Docker Swarm modu](https://docs.docker.com/engine/swarm/) dağıtmak ve test gibi ek komutlar gerekir (kullanılabilir için Docker CE Windows ve Mac sürümü 1.12 itibaren), [docker hizmeti oluşturulur](https://docs.docker.com/engine/reference/commandline/service_create/) için tek hizmetler.</span><span class="sxs-lookup"><span data-stu-id="05663-316">If you are using a cluster like [Docker Swarm mode](https://docs.docker.com/engine/swarm/) (available in Docker CE for Windows and Mac since version 1.12), you need to deploy and test with additional commands like [docker service create](https://docs.docker.com/engine/reference/commandline/service_create/) for single services.</span></span> <span data-ttu-id="05663-317">Birden çok kapsayıcılardan oluşan bir uygulama dağıtıyorsanız, kullandığınız [docker compose paket](https://docs.docker.com/compose/reference/bundle/) ve [docker dağıtma myBundleFile](https://docs.docker.com/engine/reference/commandline/deploy/) olarak oluşturulan uygulamayı dağıtmak için bir *Yığını*.</span><span class="sxs-lookup"><span data-stu-id="05663-317">If you are deploying an application composed of several containers, you use [docker compose bundle](https://docs.docker.com/compose/reference/bundle/) and [docker deploy myBundleFile](https://docs.docker.com/engine/reference/commandline/deploy/) to deploy the composed application as a *stack*.</span></span> <span data-ttu-id="05663-318">Daha fazla bilgi için bkz. blog gönderisine [giriş Deneysel dağıtılmış uygulama paketleri](https://blog.docker.com/2016/06/docker-app-bundle/) Docker belgelerinde.</span><span class="sxs-lookup"><span data-stu-id="05663-318">For more information, see the blog post [Introducing Experimental Distributed Application Bundles](https://blog.docker.com/2016/06/docker-app-bundle/) in the Docker documentation.</span></span> <span data-ttu-id="05663-319">Docker sitesi.</span><span class="sxs-lookup"><span data-stu-id="05663-319">on the Docker site.</span></span>

<span data-ttu-id="05663-320">İçin [DC/OS](https://mesosphere.com/blog/2015/09/02/dcos-cli-command-line-tool-datacenter/) ve [Kubernetes](https://kubernetes.io/docs/user-guide/deployments/) farklı dağıtım komutları ve komut dosyaları da kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="05663-320">For [DC/OS](https://mesosphere.com/blog/2015/09/02/dcos-cli-command-line-tool-datacenter/) and [Kubernetes](https://kubernetes.io/docs/user-guide/deployments/) you would use different deployment commands and scripts as well.</span></span>

![6. adım grafiği](./media/image17.png)

## <a name="step-6-test-your-docker-application-using-your-local-docker-host"></a><span data-ttu-id="05663-322">6. adım.</span><span class="sxs-lookup"><span data-stu-id="05663-322">Step 6.</span></span> <span data-ttu-id="05663-323">Kullanarak yerel bir Docker ana bilgisayarınızda Docker uygulamanızı test edin</span><span class="sxs-lookup"><span data-stu-id="05663-323">Test your Docker application using your local Docker host</span></span>

<span data-ttu-id="05663-324">Bu adım, uygulamanızın yapılması bağlı olarak değişir.</span><span class="sxs-lookup"><span data-stu-id="05663-324">This step will vary depending on what your application is doing.</span></span> <span data-ttu-id="05663-325">Tek kapsayıcı veya hizmet olarak dağıtılan bir basit .NET Core Web uygulamasında, Docker konağı üzerinde bir tarayıcı açıp bu siteye gezinme, Şekil 5-13'te gösterildiği gibi hizmete erişebilir.</span><span class="sxs-lookup"><span data-stu-id="05663-325">In a simple .NET Core Web application that is deployed as a single container or service, you can access the service by opening a browser on the Docker host and navigating to that site, as shown in Figure 5-13.</span></span> <span data-ttu-id="05663-326">(Dockerfile içinde yapılandırma kapsayıcı 80 dışında her şey, konağa bağlantı noktasına eşler. ana bilgisayar bağlantı noktası URL'ye dahil edin.)</span><span class="sxs-lookup"><span data-stu-id="05663-326">(If the configuration in the Dockerfile maps the container to a port on the host that is anything other than 80, include the host port in the URL.)</span></span>

![Örneği yerel olarak localhost kullanarak Docker uygulamanızı test etme](./media/image18.png)

<span data-ttu-id="05663-328">**Şekil 5-13**.</span><span class="sxs-lookup"><span data-stu-id="05663-328">**Figure 5-13**.</span></span> <span data-ttu-id="05663-329">Örneği yerel olarak localhost kullanarak Docker uygulamanızı test etme</span><span class="sxs-lookup"><span data-stu-id="05663-329">Example of testing your Docker application locally using localhost</span></span>

<span data-ttu-id="05663-330">Docker için localhost işaret etmiyorsa IP ana bilgisayar (Bu varsayılan Docker CE kullanırken, gerekir), hizmetinize gidin ve makinenizin Ağ kartının IP adresini kullanın.</span><span class="sxs-lookup"><span data-stu-id="05663-330">If localhost is not pointing to the Docker host IP (by default, when using Docker CE, it should), to navigate to your service, use the IP address of your machine’s network card.</span></span>

<span data-ttu-id="05663-331">Bu URL tarayıcıda tartışılan belirli bir kapsayıcı örneği için 80 numaralı bağlantı noktasını kullanır.</span><span class="sxs-lookup"><span data-stu-id="05663-331">This URL in the browser uses port 80 for the particular container example being discussed.</span></span> <span data-ttu-id="05663-332">Nasıl bu komutu çalıştırın: docker ile bir önceki adımda açıklandığı gibi dağıtılmış olduğu için ancak, dahili olarak istekleri 5000, bağlantı noktası için Rehbere yönlendiriliyorsunuz.</span><span class="sxs-lookup"><span data-stu-id="05663-332">However, internally the requests are being redirected to port 5000, because that was how it was deployed with the docker run command, as explained in a previous step.</span></span>

<span data-ttu-id="05663-333">Ayrıca, Şekil 5-14'te gösterildiği gibi terminalden curl kullanarak uygulamayı test edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="05663-333">You can also test the application using curl from the terminal, as shown in Figure 5-14.</span></span> <span data-ttu-id="05663-334">Bir Docker yüklemesinde Windows üzerindeki Docker ana bilgisayar IP her zaman 10.0.75.1 makinenizin gerçek IP adresinin yanı sıra varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="05663-334">In a Docker installation on Windows, the default Docker Host IP is always 10.0.75.1 in addition to your machine’s actual IP address.</span></span>

![Docker uygulamanızı yerel olarak curl kullanarak test etme örneği](./media/image19.png)

<span data-ttu-id="05663-336">**Şekil 5-14**.</span><span class="sxs-lookup"><span data-stu-id="05663-336">**Figure 5-14**.</span></span> <span data-ttu-id="05663-337">Docker uygulamanızı yerel olarak curl kullanarak test etme örneği</span><span class="sxs-lookup"><span data-stu-id="05663-337">Example of testing your Docker application locally using curl</span></span>

### <a name="testing-and-debugging-containers-with-visual-studio-2017"></a><span data-ttu-id="05663-338">Test ve hata ayıklama Visual Studio 2017 ile kapsayıcıları</span><span class="sxs-lookup"><span data-stu-id="05663-338">Testing and debugging containers with Visual Studio 2017</span></span>

<span data-ttu-id="05663-339">Çalışan kapsayıcılar, olduğu gibi çalışan kapsayıcılar Visual Studio 2017 ile hata ayıklama, .NET uygulama kadar aynı şekilde ayıklayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="05663-339">When running and debugging the containers with Visual Studio 2017, you can debug the .NET application in much the same way as you would when running without containers.</span></span>

### <a name="testing-and-debugging-without-visual-studio"></a><span data-ttu-id="05663-340">Test ve hata ayıklama Visual Studio</span><span class="sxs-lookup"><span data-stu-id="05663-340">Testing and debugging without Visual Studio</span></span>

<span data-ttu-id="05663-341">Düzenleyici/CLI yaklaşımı kullanarak geliştiriyorsanız kapsayıcılarında hata ayıklama daha zordur ve izlemeleri oluşturarak hata ayıklama isteyeceksiniz.</span><span class="sxs-lookup"><span data-stu-id="05663-341">If you are developing using the editor/CLI approach, debugging containers is more difficult and you will want to debug by generating traces.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="05663-342">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="05663-342">Additional resources</span></span>

- <span data-ttu-id="05663-343">**Yerel bir Docker kapsayıcısı uygulamalarında hata ayıklama**</span><span class="sxs-lookup"><span data-stu-id="05663-343">**Debugging apps in a local Docker container**</span></span>

   [*https://docs.microsoft.com/azure/vs-azure-tools-docker-edit-and-refresh*](https://docs.microsoft.com/azure/vs-azure-tools-docker-edit-and-refresh)

- <span data-ttu-id="05663-344">**Steve Lasker. Derleme, hata ayıklama, Docker ile ASP.NET Core uygulamaları dağıtın.**</span><span class="sxs-lookup"><span data-stu-id="05663-344">**Steve Lasker. Build, Debug, Deploy ASP.NET Core Apps with Docker.**</span></span> <span data-ttu-id="05663-345">Video.</span><span class="sxs-lookup"><span data-stu-id="05663-345">Video.</span></span>

   [*https://channel9.msdn.com/Events/Visual-Studio/Visual-Studio-2017-Launch/T115*](https://channel9.msdn.com/Events/Visual-Studio/Visual-Studio-2017-Launch/T115)

## <a name="simplified-workflow-when-developing-containers-with-visual-studio"></a><span data-ttu-id="05663-346">Visual Studio ile kapsayıcıları geliştirirken basitleştirilmiş bir iş akışı</span><span class="sxs-lookup"><span data-stu-id="05663-346">Simplified workflow when developing containers with Visual Studio</span></span>

<span data-ttu-id="05663-347">Etkili bir şekilde, Visual Studio kullanarak iş akışı Düzenleyicisi'ni / CLI yaklaşımı kullanırsanız, çok daha kolay olacaktır.</span><span class="sxs-lookup"><span data-stu-id="05663-347">Effectively, the workflow when using Visual Studio is a lot simpler than if you use the editor/CLI approach.</span></span> <span data-ttu-id="05663-348">Docker tarafından gerekli adımların çoğu için Dockerfile ilgili ve gizli ya da Visual Studio tarafından Şekil 5-15'te gösterildiği gibi Basitleştirilmiş docker-compose.yml dosyaları.</span><span class="sxs-lookup"><span data-stu-id="05663-348">Most of the steps required by Docker related to the Dockerfile and docker-compose.yml files are hidden or simplified by Visual Studio, as shown in Figure 5-15.</span></span>

![Visual Studio ile geliştirirken basitleştirilmiş bir iş akışı](./media/image20.png)

<span data-ttu-id="05663-350">**Şekil 5-15**.</span><span class="sxs-lookup"><span data-stu-id="05663-350">**Figure 5-15**.</span></span> <span data-ttu-id="05663-351">Visual Studio ile geliştirirken basitleştirilmiş bir iş akışı</span><span class="sxs-lookup"><span data-stu-id="05663-351">Simplified workflow when developing with Visual Studio</span></span>

<span data-ttu-id="05663-352">Ayrıca, yalnızca bir kez (Docker desteği ekleme projelerinize) 2. adım gerçekleştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="05663-352">In addition, you need to perform step 2 (adding Docker support to your projects) just once.</span></span> <span data-ttu-id="05663-353">Bu nedenle, iş akışı herhangi bir geliştirme için .NET kullanarak normal geliştirme görevlerine benzer şekildedir.</span><span class="sxs-lookup"><span data-stu-id="05663-353">Therefore, the workflow is similar to your usual development tasks when using .NET for any other development.</span></span> <span data-ttu-id="05663-354">Kapsar (görüntü oluşturma işlemi, hangi kullandığınız temel görüntüleri, kapsayıcılar, vb. dağıtımını) altında ve bazen de davranışları özelleştirmek için Dockerfile veya docker-compose.yml dosyasını düzenlemeniz gerekir neler olduğunu bilmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="05663-354">You need to know what is going on under the covers (the image build process, what base images you are using, deployment of containers, etc.) and sometimes you will also need to edit the Dockerfile or docker-compose.yml file to customize behaviors.</span></span> <span data-ttu-id="05663-355">Ancak işin çoğunu, çok daha üretken hale Visual Studio kullanılarak büyük ölçüde basitleştirilir.</span><span class="sxs-lookup"><span data-stu-id="05663-355">But most of the work is greatly simplified by using Visual Studio, making you a lot more productive.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="05663-356">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="05663-356">Additional resources</span></span>

- <span data-ttu-id="05663-357">**Steve Lasker. Visual Studio 2017 ile .NET docker geliştirme**</span><span class="sxs-lookup"><span data-stu-id="05663-357">**Steve Lasker. .NET Docker Development with Visual Studio 2017**</span></span>

   [*https://channel9.msdn.com/Events/Visual-Studio/Visual-Studio-2017-Launch/T111*](https://channel9.msdn.com/Events/Visual-Studio/Visual-Studio-2017-Launch/T111)

- <span data-ttu-id="05663-358">**Jeffrey t Fritz. Visual Studio için bir kapsayıcı yeni Docker araçları ile .NET Core uygulaması yerleştirin**</span><span class="sxs-lookup"><span data-stu-id="05663-358">**Jeffrey T. Fritz. Put a .NET Core App in a Container with the new Docker Tools for Visual Studio**</span></span>

   [*https://blogs.msdn.microsoft.com/webdev/2016/11/16/new-docker-tools-for-visual-studio/*](https://blogs.msdn.microsoft.com/webdev/2016/11/16/new-docker-tools-for-visual-studio/)

## <a name="using-powershell-commands-in-a-dockerfile-to-set-up-windows-containers"></a><span data-ttu-id="05663-359">Windows kapsayıcıları ayarlamak için bir Dockerfile içinde PowerShell komutlarını kullanarak</span><span class="sxs-lookup"><span data-stu-id="05663-359">Using PowerShell commands in a Dockerfile to set up Windows Containers</span></span>

<span data-ttu-id="05663-360">[Windows kapsayıcıları](/virtualization/windowscontainers/about/) mevcut Windows uygulamalarınızı Docker görüntüleri olarak dönüştürmek ve Docker ekosistemi sayesinde geri kalanı gibi aynı araçları ile dağıtmaya olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="05663-360">[Windows Containers](/virtualization/windowscontainers/about/) allow you to convert your existing Windows applications into Docker images and deploy them with the same tools as the rest of the Docker ecosystem.</span></span> <span data-ttu-id="05663-361">Windows kapsayıcıları kullanmak için aşağıdaki örnekte gösterildiği gibi bir Dockerfile içinde PowerShell komutlarını çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="05663-361">To use Windows Containers, you run PowerShell commands in the Dockerfile, as shown in the following example:</span></span>

```Dockerfile
FROM microsoft/windowsservercore

LABEL Description="IIS" Vendor="Microsoft" Version="10"

RUN powershell -Command Add-WindowsFeature Web-Server

CMD [ "ping", "localhost", "-t" ]
```

<span data-ttu-id="05663-362">Bu durumda, biz bir Windows Server Core temel görüntüyü (FROM ayar) kullanarak ve bir (çalışma ayarı) PowerShell komutuyla IIS'yi yükleme.</span><span class="sxs-lookup"><span data-stu-id="05663-362">In this case, we are using a Windows Server Core base image (the FROM setting) and installing IIS with a PowerShell command (the RUN setting).</span></span> <span data-ttu-id="05663-363">Benzer şekilde, ASP.NET 4.x, .NET 4.6 veya herhangi bir Windows yazılımı gibi ek bileşenler ayarlamak için PowerShell komutlarını kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="05663-363">In a similar way, you could also use PowerShell commands to set up additional components like ASP.NET 4.x, .NET 4.6, or any other Windows software.</span></span> <span data-ttu-id="05663-364">Örneğin, aşağıdaki komut bir Dockerfile içinde ASP.NET 4.5 ' ayarlar:</span><span class="sxs-lookup"><span data-stu-id="05663-364">For example, the following command in a Dockerfile sets up ASP.NET 4.5:</span></span>

```Dockerfile
RUN powershell add-windowsfeature web-asp-net45
```

### <a name="additional-resources"></a><span data-ttu-id="05663-365">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="05663-365">Additional resources</span></span>

- <span data-ttu-id="05663-366">**aspnet-docker/Dockerfile.**</span><span class="sxs-lookup"><span data-stu-id="05663-366">**aspnet-docker/Dockerfile.**</span></span> <span data-ttu-id="05663-367">Windows özellikleri içerecek şekilde dockerfile'ları için örnek Powershell komutları.</span><span class="sxs-lookup"><span data-stu-id="05663-367">Example Powershell commands to run from dockerfiles to include Windows features.</span></span>

   [*https://github.com/Microsoft/aspnet-docker/blob/master/4.6.2/Dockerfile*](https://github.com/Microsoft/aspnet-docker/blob/master/4.6.2/Dockerfile)

>[!div class="step-by-step"]
><span data-ttu-id="05663-368">[Önceki](index.md)
>[İleri](../multi-container-microservice-net-applications/index.md)</span><span class="sxs-lookup"><span data-stu-id="05663-368">[Previous](index.md)
[Next](../multi-container-microservice-net-applications/index.md)</span></span>
