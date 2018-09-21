---
title: (Windows için Visual Studio) Docker için Visual Studio araçlarını kullanma
description: Microsoft Platformu ve araçları ile kapsayıcı Docker uygulaması yaşam
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/12/2018
ms.custom: vs-dotnet
ms.openlocfilehash: af14c92ab27885deec878dc33e7b94035f43e65b
ms.sourcegitcommit: 3ab9254890a52a50762995fa6d7d77a00348db7e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/20/2018
ms.locfileid: "46488957"
---
# <a name="using-visual-studio-tools-for-docker-visual-studio-on-windows"></a><span data-ttu-id="617cd-103">(Windows için Visual Studio) Docker için Visual Studio araçlarını kullanma</span><span class="sxs-lookup"><span data-stu-id="617cd-103">Using Visual Studio Tools for Docker (Visual Studio on Windows)</span></span>

<span data-ttu-id="617cd-104">Docker için Visual Studio araçları kullanarak, geliştirme iş akışı, Visual Studio Code ve Docker CLI'yı kullanırken iş akışına benzerdir.</span><span class="sxs-lookup"><span data-stu-id="617cd-104">The development workflow when using Visual Studio Tools for Docker is similar to the workflow when using Visual Studio Code and Docker CLI.</span></span> <span data-ttu-id="617cd-105">Aslında, aynı Docker CLI'yı dayanır ancak başlamak kolaydır, bu süreci kolaylaştırır ve daha yüksek üretkenlik sağlar, derleme için çalıştırın ve Görevler oluşturun.</span><span class="sxs-lookup"><span data-stu-id="617cd-105">In fact, it's based on the same Docker CLI, but it's easier to get started, simplifies the process, and provides greater productivity for the build, run, and compose tasks.</span></span> <span data-ttu-id="617cd-106">Ayrıca, yürütün ve kapsayıcılarınızı F5 ve Ctrl + F5 Visual Studio'dan gibi basit eylemleri aracılığıyla hata ayıklama mümkün değildir.</span><span class="sxs-lookup"><span data-stu-id="617cd-106">It's also able to execute and debug your containers via simple actions like F5 and Ctrl+F5 from Visual Studio.</span></span> <span data-ttu-id="617cd-107">Çalıştırın ve tek bir kapsayıcı hata ayıklama ek olarak isteğe bağlı bir kapsayıcı düzenleme desteği, çalıştırın ve bir grup kapsayıcının (tam çözüm) aynı anda hata ayıklama.</span><span class="sxs-lookup"><span data-stu-id="617cd-107">With the optional container orchestration support, in addition to being able to run and debug a single container, you can run and debug a group of containers (a whole solution) at the same time.</span></span> <span data-ttu-id="617cd-108">Aynı kapsayıcıları tanımlamak *docker-compose.yml* çözüm düzeyinde dosya.</span><span class="sxs-lookup"><span data-stu-id="617cd-108">Just define the containers in the same *docker-compose.yml* file at the solution level.</span></span>

## <a name="configuring-your-local-environment"></a><span data-ttu-id="617cd-109">Yerel ortamınızı yapılandırma</span><span class="sxs-lookup"><span data-stu-id="617cd-109">Configuring your local environment</span></span>

<span data-ttu-id="617cd-110">Docker desteği, herhangi bir yüklü .NET ve .NET Core iş yükleri ile Visual Studio 2017'de dahil edilmiştir.</span><span class="sxs-lookup"><span data-stu-id="617cd-110">Docker support is included in Visual Studio 2017 with any of the .NET and .NET Core workloads installed.</span></span> <span data-ttu-id="617cd-111">Docker için Windows ayrı yükleyin.</span><span class="sxs-lookup"><span data-stu-id="617cd-111">Install Docker for Windows separately.</span></span>

<span data-ttu-id="617cd-112">Docker için Windows en son sürümleri ile Kurulumu aşağıdaki başvuruları açıklandığı gibi basit, çünkü Docker uygulamaları geliştirmek için her zamankinden daha kolaydır.</span><span class="sxs-lookup"><span data-stu-id="617cd-112">With the latest versions of Docker for Windows, it is easier than ever to develop Docker applications because the setup is straightforward, as explained in the following references.</span></span>

<span data-ttu-id="617cd-113">**Daha fazla bilgi:** için Docker Windows yükleme hakkında daha fazla bilgi edinmek için Git <https://docs.docker.com/docker-for-windows/>.</span><span class="sxs-lookup"><span data-stu-id="617cd-113">**More info:** To learn more about installing Docker for Windows, go to <https://docs.docker.com/docker-for-windows/>.</span></span>

<span data-ttu-id="617cd-114">**Daha fazla bilgi:** Visual Studio'yu yükleme ile ilgili yönergeler için Git [ https://visualstudio.microsoft.com/downloads/ ](https://visualstudio.microsoft.com/downloads/).</span><span class="sxs-lookup"><span data-stu-id="617cd-114">**More info:** For instructions on installing Visual Studio, go to [https://visualstudio.microsoft.com/downloads/](https://visualstudio.microsoft.com/downloads/).</span></span>

<span data-ttu-id="617cd-115">Docker için Visual Studio Araçları'nı yükleme hakkında daha fazla bilgi görmek için Git <http://aka.ms/vstoolsfordocker> ve <https://docs.microsoft.com/aspnet/core/host-and-deploy/docker/visual-studio-tools-for-docker>.</span><span class="sxs-lookup"><span data-stu-id="617cd-115">To see more about installing Visual Studio Tools for Docker, go to <http://aka.ms/vstoolsfordocker> and <https://docs.microsoft.com/aspnet/core/host-and-deploy/docker/visual-studio-tools-for-docker>.</span></span>

## <a name="using-docker-tools-in-visual-studio-2017"></a><span data-ttu-id="617cd-116">Visual Studio 2017'de Docker araçları kullanma</span><span class="sxs-lookup"><span data-stu-id="617cd-116">Using Docker Tools in Visual Studio 2017</span></span>

<span data-ttu-id="617cd-117">Docker desteği bir projeye eklerken (bkz. Şekil 4-26), Visual Studio ekler bir *Dockerfile* proje kök dizini.</span><span class="sxs-lookup"><span data-stu-id="617cd-117">When adding Docker support to a project (see Figure 4-26), Visual Studio adds a *Dockerfile* to the project root.</span></span>

![Docker çözümü desteği Visual Studio 2017 proje açma](./media/image32.png)

<span data-ttu-id="617cd-119">Şekil 4-26: Docker çözümü desteği Visual Studio 2017 proje açma</span><span class="sxs-lookup"><span data-stu-id="617cd-119">Figure 4-26: Turning on Docker Solution support in a Visual Studio 2017 project</span></span>

 <span data-ttu-id="617cd-120">Docker Compose, aracılığıyla kapsayıcı düzenleme desteği, varsayılan olarak Visual Studio 2017 sürüm 15.7 veya önceki eklenir.</span><span class="sxs-lookup"><span data-stu-id="617cd-120">Container orchestration support, via Docker Compose, is added by default in Visual Studio 2017 versions 15.7 or earlier.</span></span> <span data-ttu-id="617cd-121">Kapsayıcı düzenleme desteği Tercihli özellik Visual Studio 2017 sürümlerinde 15,8 ya da daha sonra bu durumda Docker Compose ve Service Fabric desteklenir.</span><span class="sxs-lookup"><span data-stu-id="617cd-121">Container orchestration support is an opt-in feature in Visual Studio 2017 versions 15.8 or later, in which case Docker Compose and Service Fabric are supported.</span></span>

<span data-ttu-id="617cd-122">Visual Studio sürüm 15,8 ve üzeri ile her ilişkili bir kapsayıcıya sahip olduğunuzu bir çözümde birden çok proje için destek ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="617cd-122">With Visual Studio version 15.8 and later, you can add support for multiple projects in a solution that each have an associated container.</span></span> <span data-ttu-id="617cd-123">İçinde çözüm veya proje düğümünü sağ **Çözüm Gezgini**ve **Ekle** > **kapsayıcı düzenleme desteği**.</span><span class="sxs-lookup"><span data-stu-id="617cd-123">Right-click on the solution or project node in **Solution Explorer**, and choose **Add** > **Container Orchestration Support**.</span></span>  <span data-ttu-id="617cd-124">Ardından **Docker Compose** veya **Service Fabric** kapsayıcıları yönetmek için.</span><span class="sxs-lookup"><span data-stu-id="617cd-124">Then choose **Docker Compose** or **Service Fabric** to manage the containers.</span></span>

<span data-ttu-id="617cd-125">Seçeneğini belirlediğinizde **Docker Compose**, Visual Studio çözümünüze ait bir hizmet bölümü ekler *docker-compose.yml* dosyaları (veya siz varsa dosyaları oluşturur).</span><span class="sxs-lookup"><span data-stu-id="617cd-125">When you choose **Docker Compose**, Visual Studio adds a service section in your solution's *docker-compose.yml* files (or creates the files if they didn't exist).</span></span> <span data-ttu-id="617cd-126">Çok kapsayıcılı çözümünüzü oluşturmaya başlamak için kolay bir yoludur; Daha sonra açabilirsiniz *docker-compose.yml* dosyaları ve ek özellikler ile güncelleştirin.</span><span class="sxs-lookup"><span data-stu-id="617cd-126">It's an easy way to begin composing your multi-container solution; you then can open the *docker-compose.yml* files and update them with additional features.</span></span>

<span data-ttu-id="617cd-127">Bu eylem için kod gerekli yapılandırma satırlarını ekler bir *docker-compose.yml* çözüm düzeyinde ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="617cd-127">This action adds the required configuration lines of code to a *docker-compose.yml* set at the solution level.</span></span>

<span data-ttu-id="617cd-128">Ayrıca Docker desteğini Visual Studio 2017'de bir ASP.NET Core projesi oluştururken, Şekil 4-27'de gösterildiği gibi kapatabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="617cd-128">You also can turn on Docker support when creating an ASP.NET Core project in Visual Studio 2017, as shown in Figure 4-27.</span></span>

![Bir proje oluştururken, Docker desteği açma](./media/image33.png)

<span data-ttu-id="617cd-130">Bir proje oluştururken, Docker desteği Şekil 4-27: açma</span><span class="sxs-lookup"><span data-stu-id="617cd-130">Figure 4-27: Turning on Docker support when creating a project</span></span>

<span data-ttu-id="617cd-131">Visual Studio çözümünüzde Docker desteği ekledikten sonra ayrıca yeni bir düğüm ağaçta görürsünüz **Çözüm Gezgini** eklenen ile *docker-compose.yml* dosyaları, Şekil 4-28'de gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="617cd-131">After you add Docker support to your solution in Visual Studio, you also will see a new node tree in **Solution Explorer** with the added *docker-compose.yml* files, as depicted in Figure 4-28.</span></span>

![docker-compose.yml dosyaları şimdi Çözüm Gezgininde görüntüle](./media/image34.PNG)

<span data-ttu-id="617cd-133">Şekil 4-28: docker-compose.yml dosyaları artık öne **Çözüm Gezgini**</span><span class="sxs-lookup"><span data-stu-id="617cd-133">Figure 4-28: docker-compose.yml files now display in **Solution Explorer**</span></span>

<span data-ttu-id="617cd-134">Tek bir kullanarak çok kapsayıcılı bir uygulama dağıtabilirsiniz *docker-compose.yml* dosyasını çalıştırdığınızda `docker-compose up`; ancak, Visual Studio (karşı geliştirme ortamına bağlı olarak değerleri geçersiz kılmak için bir grubu ekler Üretim) ve yürütme (hata ayıklama ve yayın) yazın.</span><span class="sxs-lookup"><span data-stu-id="617cd-134">You could deploy a multi-container app by using a single *docker-compose.yml* file when you run `docker-compose up`; however, Visual Studio adds a group of them, so you can override values depending on the environment (development versus production) and the execution type (release versus debug).</span></span> <span data-ttu-id="617cd-135">Bu özellik, daha iyi ilerleyen bölümlerde açıklanmıştır.</span><span class="sxs-lookup"><span data-stu-id="617cd-135">This capability is better explained in later chapters.</span></span>

<span data-ttu-id="617cd-136">Service Fabric Docker Compose yerine birden çok kapsayıcı yönetmek için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="617cd-136">You can also use Service Fabric instead of Docker Compose to manage multiple containers.</span></span> <span data-ttu-id="617cd-137">Bkz: [öğretici: Azure Service Fabric'e Windows kapsayıcısındaki bir .NET uygulaması dağıtma](https://docs.microsoft.com/azure/service-fabric/service-fabric-host-app-in-a-container).</span><span class="sxs-lookup"><span data-stu-id="617cd-137">See [Tutorial: Deploy a .NET application in a Windows container to Azure Service Fabric](https://docs.microsoft.com/azure/service-fabric/service-fabric-host-app-in-a-container).</span></span>

<span data-ttu-id="617cd-138">**Daha fazla bilgi:** Hizmetleri uygulaması ve Docker için Visual Studio Araçları'nın kullanımı hakkında daha ayrıntılı bilgi için bu makaleleri okuyun:</span><span class="sxs-lookup"><span data-stu-id="617cd-138">**More info:** For further details on the services implementation and use of Visual Studio Tools for Docker, read the following articles:</span></span>

<span data-ttu-id="617cd-139">Derleme, hata ayıklama, güncelleştirme ve uygulamaları yerel bir Docker kapsayıcısında Yenile: [https://docs.microsoft.com/azure/vs-azure-tools-docker-edit-and-refresh/](https://docs.microsoft.com/azure/vs-azure-tools-docker-edit-and-refresh)</span><span class="sxs-lookup"><span data-stu-id="617cd-139">Build, debug, update, and refresh apps in a local Docker container: [https://docs.microsoft.com/azure/vs-azure-tools-docker-edit-and-refresh/](https://docs.microsoft.com/azure/vs-azure-tools-docker-edit-and-refresh)</span></span>

<span data-ttu-id="617cd-140">Bir ASP.NET Core Docker kapsayıcısını bir kapsayıcı kayıt defterine dağıtın: [https://docs.microsoft.com/azure/vs-azure-tools-docker-hosting-web-apps-in-docker/](https://docs.microsoft.com/azure/vs-azure-tools-docker-hosting-web-apps-in-docker)</span><span class="sxs-lookup"><span data-stu-id="617cd-140">Deploy an ASP.NET Core Docker container to a container registry: [https://docs.microsoft.com/azure/vs-azure-tools-docker-hosting-web-apps-in-docker/](https://docs.microsoft.com/azure/vs-azure-tools-docker-hosting-web-apps-in-docker)</span></span>

>[!div class="step-by-step"]
<span data-ttu-id="617cd-141">[Önceki](docker-apps-inner-loop-workflow.md)
[İleri](set-up-windows-containers-with-powershell.md)</span><span class="sxs-lookup"><span data-stu-id="617cd-141">[Previous](docker-apps-inner-loop-workflow.md)
[Next](set-up-windows-containers-with-powershell.md)</span></span>
