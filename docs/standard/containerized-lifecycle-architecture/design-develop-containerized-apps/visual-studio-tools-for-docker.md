---
title: Windows üzerinde Docker için Visual Studio Araçları
description: Microsoft Platformu ve araçları ile kapsayıcı Docker uygulaması yaşam
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/12/2018
ms.custom: vs-dotnet
ms.openlocfilehash: cd140c12ef4a0187cce096e013937d5c98cd4b39
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/26/2018
ms.locfileid: "47235721"
---
# <a name="using-visual-studio-tools-for-docker-visual-studio-on-windows"></a><span data-ttu-id="12f32-103">(Windows için Visual Studio) Docker için Visual Studio araçlarını kullanma</span><span class="sxs-lookup"><span data-stu-id="12f32-103">Using Visual Studio Tools for Docker (Visual Studio on Windows)</span></span>

<span data-ttu-id="12f32-104">Docker Geliştirici iş akışı için Visual Studio Araçları, Visual Studio Code ve Docker CLI'yı (aynı Docker CLI'yı temel alır) kullanmaya benzer.</span><span class="sxs-lookup"><span data-stu-id="12f32-104">The Visual Studio Tools for Docker developer workflow is similar to using Visual Studio Code and Docker CLI (it is based on the same Docker CLI).</span></span> <span data-ttu-id="12f32-105">Visual Studio Araçları için Docker kullanmaya başlamak daha da kolay hale getirir, bu süreci kolaylaştırır ve derleme için daha yüksek üretkenlik sağlar çalıştırın ve Görevler oluşturun.</span><span class="sxs-lookup"><span data-stu-id="12f32-105">Visual Studio Tools for Docker makes it even easier to get started, simplifies the process, and provides greater productivity for the build, run, and compose tasks.</span></span> <span data-ttu-id="12f32-106">Yürütme ve kapsayıcılarınızı gibi basit eylemleri aracılığıyla hata ayıklama **F5** ve **Ctrl**+**F5**.</span><span class="sxs-lookup"><span data-stu-id="12f32-106">Execute and debug your containers via simple actions like **F5** and **Ctrl**+**F5**.</span></span>

> [!NOTE]
> <span data-ttu-id="12f32-107">Bu makale Windows üzerinde Visual Studio ve Visual Studio değil, Mac için geçerlidir</span><span class="sxs-lookup"><span data-stu-id="12f32-107">This article applies to Visual Studio on Windows, and not Visual Studio for Mac.</span></span>

## <a name="configure-your-local-environment"></a><span data-ttu-id="12f32-108">Yerel ortamınızı yapılandırma</span><span class="sxs-lookup"><span data-stu-id="12f32-108">Configure your local environment</span></span>

<span data-ttu-id="12f32-109">Docker için Windows en son sürümlerinde ([https://docs.docker.com/docker-for-windows/](https://docs.docker.com/docker-for-windows/)), basit kurulum Docker uygulamaları geliştirmek kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="12f32-109">With the latest versions of Docker for Windows ([https://docs.docker.com/docker-for-windows/](https://docs.docker.com/docker-for-windows/)), the straightforward setup makes it easy to develop Docker applications.</span></span>

<span data-ttu-id="12f32-110">Docker desteği, Visual Studio 2017'de dahildir.</span><span class="sxs-lookup"><span data-stu-id="12f32-110">Docker support is included in Visual Studio 2017.</span></span> <span data-ttu-id="12f32-111">Visual Studio 2017'ı buradan indirin: [https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs)</span><span class="sxs-lookup"><span data-stu-id="12f32-111">Download Visual Studio 2017 here: [https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs)</span></span>

## <a name="use-docker-tools-in-visual-studio-2017"></a><span data-ttu-id="12f32-112">Visual Studio 2017'de Docker araçları kullanın</span><span class="sxs-lookup"><span data-stu-id="12f32-112">Use Docker Tools in Visual Studio 2017</span></span>

<span data-ttu-id="12f32-113">Bir projeye ekleyebilirsiniz Docker desteği iki düzeyi vardır.</span><span class="sxs-lookup"><span data-stu-id="12f32-113">There are two levels of Docker support you can add to a project.</span></span> <span data-ttu-id="12f32-114">.NET Core web uygulaması projelerinde yalnızca ekleyebilirsiniz bir *Dockerfile* Docker desteği etkinleştirerek projeye dosya.</span><span class="sxs-lookup"><span data-stu-id="12f32-114">In .NET Core web app projects, you can just add a *Dockerfile* file to the project by enabling Docker support.</span></span> <span data-ttu-id="12f32-115">İleri düzey ekler kapsayıcı Düzenleyicisi desteği olan bir *Dockerfile* (zaten yoksa) projeye ve *docker-compose.yml* çözüm düzeyinde dosya.</span><span class="sxs-lookup"><span data-stu-id="12f32-115">The next level is container orchestrator support, which adds a *Dockerfile* to the project (if it doesn't already exist) and a *docker-compose.yml* file at the solution level.</span></span>

<span data-ttu-id="12f32-116">**Ekle** > **Docker desteği** ve **Ekle** > **kapsayıcı Düzenleyicisi desteği** komutlar bir web uygulaması projesi için proje düğümünü sağ tıklama menüsünü (veya bağlam menüsü) bulunan **Çözüm Gezgini**, Şekil 4-26 gösterildiği gibi:</span><span class="sxs-lookup"><span data-stu-id="12f32-116">The **Add** > **Docker Support** and **Add** > **Container Orchestrator Support** commands are located on the right-click menu (or context menu) of the project node for a web app project in **Solution Explorer**, as shown in Figure 4-26:</span></span>

![Visual Studio'da Docker desteği menü seçeneği ekleyin](media/add-docker-support-menu.png)

<span data-ttu-id="12f32-118">Şekil 4-26: Visual Studio 2017 projeye Docker desteği ekleme</span><span class="sxs-lookup"><span data-stu-id="12f32-118">Figure 4-26: Adding Docker support to a Visual Studio 2017 project</span></span>

### <a name="add-docker-support"></a><span data-ttu-id="12f32-119">Docker desteği Ekle</span><span class="sxs-lookup"><span data-stu-id="12f32-119">Add Docker support</span></span>

<span data-ttu-id="12f32-120">Docker desteği seçerek mevcut bir .NET Core web uygulaması projesine ekleyebilirsiniz **Ekle** > **Docker desteği** içinde **Çözüm Gezgini**.</span><span class="sxs-lookup"><span data-stu-id="12f32-120">You can add Docker support to an existing .NET Core web app project by selecting **Add** > **Docker Support** in **Solution Explorer**.</span></span> <span data-ttu-id="12f32-121">Seçerek proje oluşturma sırasında Docker desteğini etkinleştirebilirsiniz **Docker desteği etkinleştirme** içinde **yeni ASP.NET Core Web uygulaması** tıkladığınızda açılan iletişim kutusunda **Tamam** içinde **yeni proje** iletişim kutusu, Şekil 4-27'de gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="12f32-121">You can also enable Docker support during project creation by selecting **Enable Docker Support** in the **New ASP.NET Core Web Application** dialog box that opens after you click **OK** in the **New Project** dialog box, as shown in Figure 4-27.</span></span>

![Visual Studio'da yeni bir ASP.NET Core web uygulaması için Docker desteğini etkinleştir](./media/enable-docker-support-visual-studio.png)

<span data-ttu-id="12f32-123">Visual Studio 2017'de proje oluşturma sırasında Şekil 4-27: Docker desteğini etkinleştir</span><span class="sxs-lookup"><span data-stu-id="12f32-123">Figure 4-27: Enable Docker support during project creation in Visual Studio 2017</span></span>

<span data-ttu-id="12f32-124">Visual Studio ekleyin ya da Docker desteğini etkinleştirmek ekler bir *Dockerfile* projeye dosya.</span><span class="sxs-lookup"><span data-stu-id="12f32-124">When you add or enable Docker support, Visual Studio adds a *Dockerfile* file to the project.</span></span>

> [!NOTE]
> <span data-ttu-id="12f32-125">Bilgisayarınızda Docker Compose desteği proje oluştururken bir .NET Framework web uygulaması projesi (olmayan bir .NET Core web uygulaması projesi) için Şekil 4-28 gösterildiği etkinleştirdiğinizde, kapsayıcı Düzenleyicisi desteği de eklenir.</span><span class="sxs-lookup"><span data-stu-id="12f32-125">When you enable Docker Compose support during project creation for a .NET Framework web app project (not a .NET Core web app project) as shown in Figure 4-28, container orchestrator support is also added.</span></span>
>
> ![Docker'ı etkinleştirme desteği için bir .NET Framework web uygulaması projesi oluşturma](media/enable-docker-compose-support.png)

> <span data-ttu-id="12f32-127">Şekil 4-28: Visual Studio 2017'de .NET Framework web uygulaması projesi üzerinde Docker Compose desteği etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="12f32-127">Figure 4-28: Enabling Docker Compose support on a .NET Framework web app project in Visual Studio 2017</span></span>

### <a name="add-container-orchestrator-support"></a><span data-ttu-id="12f32-128">Kapsayıcı Düzenleyicisi desteği Ekle</span><span class="sxs-lookup"><span data-stu-id="12f32-128">Add container orchestrator support</span></span>

<span data-ttu-id="12f32-129">Çok kapsayıcılı bir çözüm oluşturmak istediğinizde, kapsayıcı Düzenleyicisi desteği, projenize ekleyin.</span><span class="sxs-lookup"><span data-stu-id="12f32-129">When you want to compose a multicontainer solution, add container orchestrator support to your projects.</span></span> <span data-ttu-id="12f32-130">Kapsayıcı Düzenleyicisi desteği eklediğinizde, Visual Studio ekler bir *Dockerfile* (zaten yoksa) proje ile genel *docker-compose.yml* çözüm düzeyinde dosya.</span><span class="sxs-lookup"><span data-stu-id="12f32-130">When you add container orchestrator support, Visual Studio adds a *Dockerfile* to the project (if it doesn't already exist) and a global *docker-compose.yml* file at the solution level.</span></span> <span data-ttu-id="12f32-131">Bu, çalıştırma ve aynı tanımlanan bir grup kapsayıcının (tam çözüm) aynı anda hata ayıklaması sağlar *docker-compose.yml* dosya.</span><span class="sxs-lookup"><span data-stu-id="12f32-131">This lets you run and debug a group of containers (a whole solution) at the same time if they're defined in the same *docker-compose.yml* file.</span></span> <span data-ttu-id="12f32-132">Varsa *docker-compose.yml* zaten var, Visual Studio yalnızca ekler gerekli yapılandırma kod satırı için.</span><span class="sxs-lookup"><span data-stu-id="12f32-132">If *docker-compose.yml* already exists, Visual Studio just adds the required lines of configuration code to it.</span></span>

<span data-ttu-id="12f32-133">Kapsayıcı düzenleme desteği projenize ekledikten sonra projeye eklenen bir Dockerfile bakın ve **docker-compose** çözümüne eklenmiş klasör **Çözüm Gezgini**, Şekil 4-29 gösterildiği gibi:</span><span class="sxs-lookup"><span data-stu-id="12f32-133">After you add container orchestration support to your project, you see a Dockerfile added to the project and a **docker-compose** folder added to the solution in **Solution Explorer**, as shown in Figure 4-29:</span></span>

![Visual Studio'daki Çözüm Gezgini'nde docker dosyaları](media/docker-support-solution-explorer.png)

<span data-ttu-id="12f32-135">Şekil 4-29: Docker dosyaları Çözüm Gezgini'nde Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="12f32-135">Figure 4-29: Docker files in Solution Explorer in Visual Studio 2017</span></span>

<span data-ttu-id="12f32-136">**Daha fazla bilgi:** Hizmetleri uygulaması ve Docker için Visual Studio Araçları'nın kullanımı hakkında daha ayrıntılı bilgi için bu makaleleri okuyun:</span><span class="sxs-lookup"><span data-stu-id="12f32-136">**More information:** For further details on the services implementation and use of Visual Studio Tools for Docker, read the following articles:</span></span>

<span data-ttu-id="12f32-137">Derleme, hata ayıklama, güncelleştirme ve uygulamaları yerel bir Docker kapsayıcısında Yenile: [https://docs.microsoft.com/azure/vs-azure-tools-docker-edit-and-refresh/](https://docs.microsoft.com/azure/vs-azure-tools-docker-edit-and-refresh)</span><span class="sxs-lookup"><span data-stu-id="12f32-137">Build, debug, update, and refresh apps in a local Docker container: [https://docs.microsoft.com/azure/vs-azure-tools-docker-edit-and-refresh/](https://docs.microsoft.com/azure/vs-azure-tools-docker-edit-and-refresh)</span></span>

<span data-ttu-id="12f32-138">Bir ASP.NET Core Docker kapsayıcısını bir kapsayıcı kayıt defterine dağıtın: [https://docs.microsoft.com/azure/vs-azure-tools-docker-hosting-web-apps-in-docker/](https://docs.microsoft.com/azure/vs-azure-tools-docker-hosting-web-apps-in-docker)</span><span class="sxs-lookup"><span data-stu-id="12f32-138">Deploy an ASP.NET Core Docker container to a container registry: [https://docs.microsoft.com/azure/vs-azure-tools-docker-hosting-web-apps-in-docker/](https://docs.microsoft.com/azure/vs-azure-tools-docker-hosting-web-apps-in-docker)</span></span>

>[!div class="step-by-step"]
<span data-ttu-id="12f32-139">[Önceki](docker-apps-inner-loop-workflow.md)
[İleri](set-up-windows-containers-with-powershell.md)</span><span class="sxs-lookup"><span data-stu-id="12f32-139">[Previous](docker-apps-inner-loop-workflow.md)
[Next](set-up-windows-containers-with-powershell.md)</span></span>