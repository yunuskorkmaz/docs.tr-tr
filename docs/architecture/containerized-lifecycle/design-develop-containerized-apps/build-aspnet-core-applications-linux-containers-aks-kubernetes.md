---
title: AKS/Kubernetes kümelerine Linux kapsayıcıları olarak dağıtılan ASP.NET Core uygulamalar oluşturun
description: Microsoft Platformu ve Araçları ile Kapsayıcı Docker Uygulaması Yaşam Döngüsü
ms.date: 08/06/2020
ms.openlocfilehash: 8b3141d79eeb252ec3721d57293bed0e335b41d3
ms.sourcegitcommit: a6bd4cad438fe479cbd112eae10f2cd449f06e40
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/08/2020
ms.locfileid: "91844569"
---
# <a name="build-aspnet-core-applications-deployed-as-linux-containers-into-an-akskubernetes-orchestrator"></a><span data-ttu-id="94702-103">Bir AKS/Kubernetes Orchestrator 'a Linux kapsayıcıları olarak dağıtılan ASP.NET Core uygulamalar oluşturun</span><span class="sxs-lookup"><span data-stu-id="94702-103">Build ASP.NET Core applications deployed as Linux containers into an AKS/Kubernetes orchestrator</span></span>

<span data-ttu-id="94702-104">Azure Kubernetes Hizmetleri (AKS), Azure 'un kapsayıcı dağıtımı ve yönetimini kolaylaştıran yönetilen Kubernetes yönetimi hizmetidir.</span><span class="sxs-lookup"><span data-stu-id="94702-104">Azure Kubernetes Services (AKS) is Azure's managed Kubernetes orchestrations services that simplify container deployment and management.</span></span>

<span data-ttu-id="94702-105">AKS ana özellikleri şunlardır:</span><span class="sxs-lookup"><span data-stu-id="94702-105">AKS main features are:</span></span>

- <span data-ttu-id="94702-106">Azure 'da barındırılan denetim düzlemi</span><span class="sxs-lookup"><span data-stu-id="94702-106">An Azure-hosted control plane</span></span>
- <span data-ttu-id="94702-107">Otomatik yükseltmeler</span><span class="sxs-lookup"><span data-stu-id="94702-107">Automated upgrades</span></span>
- <span data-ttu-id="94702-108">Kendi kendini onarma</span><span class="sxs-lookup"><span data-stu-id="94702-108">Self-healing</span></span>
- <span data-ttu-id="94702-109">Kullanıcı tarafından yapılandırılabilir ölçekleme</span><span class="sxs-lookup"><span data-stu-id="94702-109">User-configurable scaling</span></span>
- <span data-ttu-id="94702-110">Hem geliştiriciler hem de küme işleçleri için daha basit kullanıcı deneyimi.</span><span class="sxs-lookup"><span data-stu-id="94702-110">Simpler user experience for both developers and cluster operators.</span></span>

<span data-ttu-id="94702-111">Aşağıdaki örneklerde, Linux üzerinde çalışan ve Azure 'daki bir AKS kümesine dağıtan ASP.NET Core 3,1 uygulamasının oluşturulması araştırırken Visual Studio 2019 kullanılarak geliştirme yapılır.</span><span class="sxs-lookup"><span data-stu-id="94702-111">The following examples explore the creation of an ASP.NET Core 3.1 application that runs on Linux and deploys to an AKS Cluster in Azure, while development is done using Visual Studio 2019.</span></span>

## <a name="creating-the-aspnet-core-project-using-visual-studio-2019"></a><span data-ttu-id="94702-112">Visual Studio 2019 kullanarak ASP.NET Core projesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="94702-112">Creating the ASP.NET Core Project using Visual Studio 2019</span></span>

<span data-ttu-id="94702-113">ASP.NET Core, GitHub 'da Microsoft ve .NET Community tarafından tutulan genel amaçlı bir geliştirme platformudur.</span><span class="sxs-lookup"><span data-stu-id="94702-113">ASP.NET Core is a general-purpose development platform maintained by Microsoft and the .NET community on GitHub.</span></span> <span data-ttu-id="94702-114">Windows, macOS ve Linux 'un desteklenme ve cihaz, bulut ve katıştırılmış/IoT senaryolarında kullanılabilen platformlar arası bir platformdur.</span><span class="sxs-lookup"><span data-stu-id="94702-114">It's cross-platform, supporting Windows, macOS and Linux, and can be used in device, cloud, and embedded/IoT scenarios.</span></span>

<span data-ttu-id="94702-115">Bu örnek, Visual Studio şablonlarına dayalı birkaç basit proje kullanır, bu nedenle örneği oluşturmak için çok fazla ek bilgiye gerek kalmaz.</span><span class="sxs-lookup"><span data-stu-id="94702-115">This example uses a couple of simple projects based on Visual Studio templates, so you don't need much additional knowledge to create the sample.</span></span> <span data-ttu-id="94702-116">Projeyi, ASP.NET Core 3,1 teknolojisini kullanarak REST API ve Razor sayfaları olan bir Web uygulamasıyla küçük bir proje çalıştırmak için tüm öğeleri içeren standart bir şablon kullanarak oluşturmanız yeterlidir.</span><span class="sxs-lookup"><span data-stu-id="94702-116">You only have to create the project using a standard template that includes all the elements to run a small project with a REST API and a Web App with Razor pages, using ASP.NET Core 3.1 technology.</span></span>

![Visual Studio 'da ASP.NET Core Web uygulaması ' nı seçerek yeni proje penceresi ekleyin.](media/build-aspnet-core-applications-linux-containers-aks-kubernetes/create-aspnet-core-application.png)

<span data-ttu-id="94702-118">**Şekil 4-35**.</span><span class="sxs-lookup"><span data-stu-id="94702-118">**Figure 4-35**.</span></span> <span data-ttu-id="94702-119">Visual Studio 2019 ' de ASP.NET Core Web uygulaması oluşturma.</span><span class="sxs-lookup"><span data-stu-id="94702-119">Creating an ASP.NET Core Web Application in Visual Studio 2019.</span></span>

<span data-ttu-id="94702-120">Visual Studio 'da örnek proje oluşturmak için **Dosya**  >  **Yeni**  >  **Proje**' yi seçin, **Web** projesi türünü ve ardından **ASP.NET Core Web uygulaması** şablonunu seçin.</span><span class="sxs-lookup"><span data-stu-id="94702-120">To create the sample project in Visual Studio, select **File** > **New** > **Project**, select the **Web** project type and then the **ASP.NET Core Web Application** template.</span></span> <span data-ttu-id="94702-121">Ayrıca, gerekirse şablon için arama yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="94702-121">You can also search for the template if you need it.</span></span>

<span data-ttu-id="94702-122">Ardından, sonraki görüntüde gösterildiği gibi uygulama adını ve konumunu girin.</span><span class="sxs-lookup"><span data-stu-id="94702-122">Then enter the application name and location as shown in the next image.</span></span>

![Proje adını ve konumunu girin.](media/build-aspnet-core-applications-linux-containers-aks-kubernetes/enter-project-name-and-location.png)

<span data-ttu-id="94702-124">**Şekil 4-36**.</span><span class="sxs-lookup"><span data-stu-id="94702-124">**Figure 4-36**.</span></span> <span data-ttu-id="94702-125">Visual Studio 2019 ' de proje adını ve konumunu girin.</span><span class="sxs-lookup"><span data-stu-id="94702-125">Enter the project name and location in Visual Studio 2019.</span></span>

<span data-ttu-id="94702-126">Framework olarak ASP.NET Core 3,1 ' i seçtiğinizi doğrulayın.</span><span class="sxs-lookup"><span data-stu-id="94702-126">Verify that you've selected ASP.NET Core 3.1 as the framework.</span></span> <span data-ttu-id="94702-127">.NET Core 3,1, Visual Studio 2019 ' nin en son sürümüne dahildir ve Visual Studio 'Yu yüklediğinizde sizin için otomatik olarak yüklenir ve yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="94702-127">.NET Core 3.1 is included in the latest release of Visual Studio 2019 and is automatically installed and configured for you when you install Visual Studio.</span></span>

![API seçeneği seçili ASP.NET Core Web uygulaması türünü seçmek için Visual Studio iletişim kutusu.](media/build-aspnet-core-applications-linux-containers-aks-kubernetes/create-web-api-application.png)

<span data-ttu-id="94702-129">**Şekil 4-37**.</span><span class="sxs-lookup"><span data-stu-id="94702-129">**Figure 4-37**.</span></span> <span data-ttu-id="94702-130">ASP.NET CORE 3,1 ve Web API proje türünü seçme</span><span class="sxs-lookup"><span data-stu-id="94702-130">Selecting ASP.NET CORE 3.1 and Web API project type</span></span>

<span data-ttu-id="94702-131">Artık Docker desteğinin, Proje oluşturulduktan sonra yapılabileceğini göstermek için etkin olmadığına dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="94702-131">Notice Docker support is not enabled now, just to show it can be done after project creation.</span></span>

<span data-ttu-id="94702-132">.NET Core 'un önceki bir sürümüne sahipseniz, 3,1 sürümünü indirip yükleyebilirsiniz <https://dotnet.microsoft.com/download> .</span><span class="sxs-lookup"><span data-stu-id="94702-132">If you have any previous version of .NET Core, you can download and install the 3.1 version from <https://dotnet.microsoft.com/download>.</span></span>

<span data-ttu-id="94702-133">Projenizi dilediğiniz zaman "Dockerize" gösterebilmeniz için artık Docker desteği ekleyeceğiz.</span><span class="sxs-lookup"><span data-stu-id="94702-133">To show you can "Dockerize" your project at any time, you'll add Docker support now.</span></span> <span data-ttu-id="94702-134">Bu nedenle Çözüm Gezgini içindeki proje düğümüne sağ tıklayın ve **Add**  >  bağlam menüsünde**Docker desteği** Ekle ' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="94702-134">So right-click on the project node in Solution Explorer and select **Add** > **Docker support** on the context menu.</span></span>

![Mevcut bir projeye Docker desteği eklemek için bağlam menü seçeneği: > Docker desteği eklemek > (projede) öğesine sağ tıklayın.](media/build-aspnet-core-applications-linux-containers-aks-kubernetes/add-docker-support-to-project.png)

<span data-ttu-id="94702-136">**Şekil 4-38**.</span><span class="sxs-lookup"><span data-stu-id="94702-136">**Figure 4-38**.</span></span> <span data-ttu-id="94702-137">Mevcut bir projeye Docker desteği ekleme</span><span class="sxs-lookup"><span data-stu-id="94702-137">Adding Docker support to an existing project</span></span>

<span data-ttu-id="94702-138">Docker desteği ekleme işleminin tamamlanabilmesi için Windows veya Linux ' u seçebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="94702-138">To complete adding Docker support, you can choose Windows or Linux.</span></span> <span data-ttu-id="94702-139">Bu durumda, **Linux**' u seçin.</span><span class="sxs-lookup"><span data-stu-id="94702-139">In this case, select **Linux**.</span></span>

![Dockerfile için hedef işletim sistemini seçmek üzere seçenek iletişim kutusu.](media/build-aspnet-core-applications-linux-containers-aks-kubernetes/select-linux-docker-support.png)

<span data-ttu-id="94702-141">**Şekil 4-39**.</span><span class="sxs-lookup"><span data-stu-id="94702-141">**Figure 4-39**.</span></span> <span data-ttu-id="94702-142">Linux kapsayıcıları seçiliyor.</span><span class="sxs-lookup"><span data-stu-id="94702-142">Selecting Linux containers.</span></span>

<span data-ttu-id="94702-143">Bu basit adımlarla bir Linux kapsayıcısında çalışan ASP.NET Core 3,1 uygulamanız vardır.</span><span class="sxs-lookup"><span data-stu-id="94702-143">With these simple steps, you have your ASP.NET Core 3.1 application running on a Linux container.</span></span>

<span data-ttu-id="94702-144">Benzer bir şekilde, Web API uç noktasını kullanmak için çok basit bir **WebApp** projesi (Şekil 4-40) ekleyebilirsiniz, ancak Ayrıntılar burada açıklanmaz.</span><span class="sxs-lookup"><span data-stu-id="94702-144">In a similar way, you can also add a very simple **WebApp** project (Figure 4-40) to consume the web API endpoint, although the details are not discussed here.</span></span>

<span data-ttu-id="94702-145">Bundan sonra, görüntü 4-40 ' de aşağıda gösterildiği gibi, **WebApi** projeniz için Orchestrator desteği eklersiniz.</span><span class="sxs-lookup"><span data-stu-id="94702-145">After that, you add orchestrator support for your **WebApi** project as shown next, in image 4-40.</span></span>

![WebApi projesine Orchestrator desteği ekleniyor](media/build-aspnet-core-applications-linux-containers-aks-kubernetes/add-orchestrator-support.png)

<span data-ttu-id="94702-147">**Şekil 4-40**.</span><span class="sxs-lookup"><span data-stu-id="94702-147">**Figure 4-40**.</span></span> <span data-ttu-id="94702-148">*WebApi* projesine Orchestrator desteği ekleniyor.</span><span class="sxs-lookup"><span data-stu-id="94702-148">Adding orchestrator support to *WebApi* project.</span></span>

<span data-ttu-id="94702-149">`Docker Compose`Yerel geliştirme için iyi olan seçeneğini belirlediğinizde, Visual Studio Docker-Compose projesini, görüntü 4-41 ' de gösterildiği gibi Docker-Compose dosyaları ile ekler.</span><span class="sxs-lookup"><span data-stu-id="94702-149">When you choose the `Docker Compose` option, which is fine for local development, Visual Studio adds the docker-compose project, with the docker-compose files as shown in image 4-41.</span></span>

![Docker-Compose çözüme eklendi](media/build-aspnet-core-applications-linux-containers-aks-kubernetes/docker-compose-project-in-visual-studio.png)

<span data-ttu-id="94702-151">**Şekil 4-41**.</span><span class="sxs-lookup"><span data-stu-id="94702-151">**Figure 4-41**.</span></span> <span data-ttu-id="94702-152">*WebApi* projesine Orchestrator desteği ekleniyor.</span><span class="sxs-lookup"><span data-stu-id="94702-152">Adding orchestrator support to *WebApi* project.</span></span>

<span data-ttu-id="94702-153">Eklenen ilk dosyalar bunlara benzerdir:</span><span class="sxs-lookup"><span data-stu-id="94702-153">The initial files added are similar to these ones:</span></span>

`docker-compose.yml`

```yml
version: "3.4"

services:
  webapi:
    image: ${DOCKER_REGISTRY-}webapi
    build:
      context: .
      dockerfile: WebApi/Dockerfile

  webapp:
    image: ${DOCKER_REGISTRY-}webapp
    build:
      context: .
      dockerfile: WebApp/Dockerfile
```

`docker-compose.override.yml`

```yml
version: "3.4"

services:
  webapi:
    environment:
      - ASPNETCORE_ENVIRONMENT=Development
      - ASPNETCORE_URLS=https://+:443;http://+:80
    ports:
      - "80"
      - "443"
    volumes:
      - ${APPDATA}/Microsoft/UserSecrets:/root/.microsoft/usersecrets:ro
      - ${APPDATA}/ASP.NET/Https:/root/.aspnet/https:ro
  webapp:
    environment:
      - ASPNETCORE_ENVIRONMENT=Development
      - ASPNETCORE_URLS=https://+:443;http://+:80
    ports:
      - "80"
      - "443"
    volumes:
      - ${APPDATA}/Microsoft/UserSecrets:/root/.microsoft/usersecrets:ro
      - ${APPDATA}/ASP.NET/Https:/root/.aspnet/https:ro
```

<span data-ttu-id="94702-154">Uygulamanızı çalıştırmak için Docker Compose yalnızca birkaç tdalgalı KS yapmanız gerekir `docker-compose.override.yml`</span><span class="sxs-lookup"><span data-stu-id="94702-154">To have you app running with Docker Compose you just have to make a few tweaks to `docker-compose.override.yml`</span></span>

```yml
services:
  webapi:
    #...
    ports:
      - "51080:80"
      - "51443:443"
    #...
  webapp:
    environment:
      #...
      - WebApiBaseAddress=http://webapi
    ports:
      - "50080:80"
      - "50443:443"
    #...
```

<span data-ttu-id="94702-155">Artık, görüntü 4-42 ' de gösterildiği gibi, uygulamanızı **F5** tuşuyla veya **oynat** düğmesini ya da **CTRL + F5** tuşunu kullanarak Docker-Compose projesini seçerek çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="94702-155">Now you can run your application with the **F5** key, or by using the **Play** button, or the **Ctrl+F5** key, selecting the docker-compose project, as shown in image 4-42.</span></span>

![Visual Studio ile Docker-Compose projesi çalıştırma](media/build-aspnet-core-applications-linux-containers-aks-kubernetes/running-docker-compose-with-visual-studio.png)

<span data-ttu-id="94702-157">**Şekil 4-42**.</span><span class="sxs-lookup"><span data-stu-id="94702-157">**Figure 4-42**.</span></span> <span data-ttu-id="94702-158">*WebApi* projesine Orchestrator desteği ekleniyor.</span><span class="sxs-lookup"><span data-stu-id="94702-158">Adding orchestrator support to *WebApi* project.</span></span>

<span data-ttu-id="94702-159">Docker-Compose uygulamasını açıklandığı şekilde çalıştırırken şunları alırsınız:</span><span class="sxs-lookup"><span data-stu-id="94702-159">When running the docker-compose application as explained, you get:</span></span>

1. <span data-ttu-id="94702-160">Docker-Compose dosyasına göre oluşturulan ve kapsayıcı görüntüleri.</span><span class="sxs-lookup"><span data-stu-id="94702-160">The images built and containers created as per the docker-compose file.</span></span>
2. <span data-ttu-id="94702-161">Tarayıcı, proje için "Özellikler" iletişim kutusunda yapılandırılan adreste açılır `docker-compose` .</span><span class="sxs-lookup"><span data-stu-id="94702-161">The browser open in the address configured in the "Properties" dialog for the `docker-compose` project.</span></span>
3. <span data-ttu-id="94702-162">**Kapsayıcı** penceresi açık (Visual Studio 2019 sürüm 16,4 ve sonraki sürümlerde).</span><span class="sxs-lookup"><span data-stu-id="94702-162">The **Container** window open (in Visual Studio 2019 version 16.4 and later).</span></span>
4. <span data-ttu-id="94702-163">Aşağıdaki resimlerde gösterildiği gibi, Çözümdeki tüm projeler için hata ayıklayıcı desteği.</span><span class="sxs-lookup"><span data-stu-id="94702-163">Debugger support for all projects in the solution, as shown in the following images.</span></span>

<span data-ttu-id="94702-164">Tarayıcı açıldı:</span><span class="sxs-lookup"><span data-stu-id="94702-164">Browser opened:</span></span>

![Web uygulamasının çalıştığı tarayıcı görünümü](media/build-aspnet-core-applications-linux-containers-aks-kubernetes/browser-opened.png)

<span data-ttu-id="94702-166">**Şekil 4-43**.</span><span class="sxs-lookup"><span data-stu-id="94702-166">**Figure 4-43**.</span></span> <span data-ttu-id="94702-167">Birden çok kapsayıcı üzerinde çalışan bir uygulamayla tarayıcı penceresi.</span><span class="sxs-lookup"><span data-stu-id="94702-167">Browser window with an application running on multiple containers.</span></span>

<span data-ttu-id="94702-168">Kapsayıcılar penceresi:</span><span class="sxs-lookup"><span data-stu-id="94702-168">Containers window:</span></span>

![Visual Studio "kapsayıcılar" penceresi](media/build-aspnet-core-applications-linux-containers-aks-kubernetes/visual-studio-containers-window.png)

<span data-ttu-id="94702-170">**Şekil 4-44**.</span><span class="sxs-lookup"><span data-stu-id="94702-170">**Figure 4-44**.</span></span> <span data-ttu-id="94702-171">Visual Studio "kapsayıcılar" penceresi</span><span class="sxs-lookup"><span data-stu-id="94702-171">Visual Studio "Containers" window</span></span>

<span data-ttu-id="94702-172">**Kapsayıcılar** penceresi, çalışan kapsayıcıları görüntülemenize, kullanılabilir görüntülere gözatmanıza, ortam değişkenlerini, günlüklere ve bağlantı noktası eşlemelerini görüntülemenize, dosya sistemini incelemenize, hata ayıklayıcı eklemenize veya kapsayıcı ortamının içinde bir Terminal penceresi açmaya olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="94702-172">The **Containers** window lets you view running containers, browse available images, view environment variables, logs, and port mappings, inspect the filesystem, attach a debugger, or open a terminal window inside the container environment.</span></span>

<span data-ttu-id="94702-173">Gördüğünüz gibi, Visual Studio 2019 ile Docker arasındaki tümleştirme, geliştiricinin verimliliğine tamamen dayalıdır.</span><span class="sxs-lookup"><span data-stu-id="94702-173">As you can see, the integration between Visual Studio 2019 and Docker is completely oriented to the developer's productivity.</span></span>

<span data-ttu-id="94702-174">Kuşkusuz, komutunu kullanarak da görüntüleri listeleyebilirsiniz `docker images` .</span><span class="sxs-lookup"><span data-stu-id="94702-174">Of course, you can also list the images using the `docker images` command.</span></span> <span data-ttu-id="94702-175">`webapi` `webapp` `dev` Visual Studio 2019 ile projemizin otomatik dağıtımı tarafından oluşturulan etiketlerle ve görüntülerini görmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="94702-175">You should see the `webapi` and `webapp` images with the `dev` tags created by the automatic deployment of our project with Visual Studio 2019.</span></span>

```console
docker images
```

![Docker görüntüleri komutundan konsol çıktısı: depo, etiket, görüntü KIMLIĞI, oluşturulan (Tarih) ve boyut içeren bir liste gösterir.](media/build-aspnet-core-applications-linux-containers-aks-kubernetes/docker-images-command.png)

<span data-ttu-id="94702-177">**Şekil 4-45**.</span><span class="sxs-lookup"><span data-stu-id="94702-177">**Figure 4-45**.</span></span> <span data-ttu-id="94702-178">Docker görüntülerinin görünümü</span><span class="sxs-lookup"><span data-stu-id="94702-178">View of Docker images</span></span>

## <a name="register-the-solution-in-an-azure-container-registry-acr"></a><span data-ttu-id="94702-179">Çözümü bir Azure Container Registry kaydetme (ACR)</span><span class="sxs-lookup"><span data-stu-id="94702-179">Register the Solution in an Azure Container Registry (ACR)</span></span>

<span data-ttu-id="94702-180">Görüntüleri [Azure Container Registry (ACR)](https://azure.microsoft.com/services/container-registry/)yükleyebilirsiniz, ancak Docker Hub veya başka bir kayıt defteri de kullanabilirsiniz. bu sayede, görüntüler bu kayıt defterinden aks kümesine dağıtılabilir.</span><span class="sxs-lookup"><span data-stu-id="94702-180">You can upload the images to the [Azure Container Registry (ACR)](https://azure.microsoft.com/services/container-registry/), but you could also use Docker Hub or any other registry, so the images can be deployed to the AKS cluster from that registry.</span></span>

### <a name="create-an-acr-instance"></a><span data-ttu-id="94702-181">ACR örneği oluşturma</span><span class="sxs-lookup"><span data-stu-id="94702-181">Create an ACR instance</span></span>

<span data-ttu-id="94702-182">**Az CLI**konumundan şu komutu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="94702-182">Run the following command from the **az cli**:</span></span>

```powershell
az acr create --name exploredocker --resource-group explore-docker-aks-rg --sku basic --admin-enabled
```

> [!NOTE]
> <span data-ttu-id="94702-183">Kapsayıcı kayıt defteri adı (ör. `exploredocker` ) Azure içinde benzersiz olmalı ve 5-50 alfasayısal karakter içermelidir.</span><span class="sxs-lookup"><span data-stu-id="94702-183">The container registry name (e.g `exploredocker`) must be unique within Azure, and contain 5-50 alphanumeric characters.</span></span> <span data-ttu-id="94702-184">Daha ayrıntılı bilgi için bkz. [kapsayıcı kayıt defteri oluşturma](https://docs.microsoft.com/azure/container-registry/container-registry-get-started-azure-cli#create-a-container-registry)</span><span class="sxs-lookup"><span data-stu-id="94702-184">For more details, refer [Create a container registry](https://docs.microsoft.com/azure/container-registry/container-registry-get-started-azure-cli#create-a-container-registry)</span></span>

### <a name="create-the-image-in-release-mode"></a><span data-ttu-id="94702-185">Görüntüyü yayın modunda oluşturma</span><span class="sxs-lookup"><span data-stu-id="94702-185">Create the image in Release mode</span></span>

<span data-ttu-id="94702-186">Şimdi, Şekil 4-46 ' de gösterildiği gibi, **yayın**moduna geçiş yaparak ve uygulamayı daha önce yaptığınız gibi çalıştırarak **yayın** modunda (üretim için hazır) görüntüyü oluşturacaksınız.</span><span class="sxs-lookup"><span data-stu-id="94702-186">You'll now create the image in **Release** mode (ready for production) by changing to **Release**, as shown in Figure 4-46, and running the application as you did before.</span></span>

![Yayın modunda derleme ' deki araç çubuğu seçeneği.](media/build-aspnet-core-applications-linux-containers-aks-kubernetes/select-release-mode.png)

<span data-ttu-id="94702-188">**Şekil 4-46**.</span><span class="sxs-lookup"><span data-stu-id="94702-188">**Figure 4-46**.</span></span> <span data-ttu-id="94702-189">Yayın modunu seçme</span><span class="sxs-lookup"><span data-stu-id="94702-189">Selecting Release Mode</span></span>

<span data-ttu-id="94702-190">`docker images`Komutu çalıştırırsanız, bir tane `debug` (**geliştirme**) ve diğeri `release` (**en son**) modu için oluşturulan görüntüleri görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="94702-190">If you execute the `docker images` command, you'll see both images created, one for `debug` (**dev**) and the other for `release` (**latest**) mode.</span></span>

### <a name="create-a-new-tag-for-the-image"></a><span data-ttu-id="94702-191">Görüntü için yeni bir etiket oluşturun</span><span class="sxs-lookup"><span data-stu-id="94702-191">Create a new Tag for the Image</span></span>

<span data-ttu-id="94702-192">Her kapsayıcı görüntüsünün kayıt defteri adıyla etiketlenmesi gerekir `loginServer` .</span><span class="sxs-lookup"><span data-stu-id="94702-192">Each container image needs to be tagged with the `loginServer` name of the registry.</span></span> <span data-ttu-id="94702-193">Bu etiket, görüntü kayıt defterine kapsayıcı görüntüleri gönderilirken kullanılır.</span><span class="sxs-lookup"><span data-stu-id="94702-193">This tag is used for routing when pushing container images to an image registry.</span></span>

<span data-ttu-id="94702-194">`loginServer`Azure Container Registry bilgileri alarak Azure Portal adı görüntüleyebilirsiniz</span><span class="sxs-lookup"><span data-stu-id="94702-194">You can view the `loginServer` name from the Azure portal, taking the information from the Azure Container Registry</span></span>

![Azure Container kayıt defteri adının sağ üst tarafındaki tarayıcı görünümü.](media/build-aspnet-core-applications-linux-containers-aks-kubernetes/loginServer-name.png)

<span data-ttu-id="94702-196">**Şekil 4-47**.</span><span class="sxs-lookup"><span data-stu-id="94702-196">**Figure 4-47**.</span></span> <span data-ttu-id="94702-197">Kayıt defterinin adının görünümü</span><span class="sxs-lookup"><span data-stu-id="94702-197">View of the name of the Registry</span></span>

<span data-ttu-id="94702-198">Ya da aşağıdaki komutu çalıştırarak:</span><span class="sxs-lookup"><span data-stu-id="94702-198">Or by running the following command:</span></span>

```console
az acr list --resource-group <resource-group-name> --query "[].{acrLoginServer:loginServer}" --output table
```

![Yukarıdaki komuttan konsol çıktısı.](media/build-aspnet-core-applications-linux-containers-aks-kubernetes/az-cli-loginServer-name.png)

<span data-ttu-id="94702-200">**Şekil 4-48**.</span><span class="sxs-lookup"><span data-stu-id="94702-200">**Figure 4-48**.</span></span> <span data-ttu-id="94702-201">**Az CLI** kullanarak kayıt defterinin adını alın</span><span class="sxs-lookup"><span data-stu-id="94702-201">Get the name of the registry using **az cli**</span></span>

<span data-ttu-id="94702-202">Her iki durumda da adı elde edersiniz.</span><span class="sxs-lookup"><span data-stu-id="94702-202">In both cases, you'll obtain the name.</span></span> <span data-ttu-id="94702-203">Örneğimizde, `exploredocker.azurecr.io` .</span><span class="sxs-lookup"><span data-stu-id="94702-203">In our example, `exploredocker.azurecr.io`.</span></span>

<span data-ttu-id="94702-204">Artık, şu komutla birlikte en son görüntüyü (yayın görüntüsü) alarak resmi etiketleyebilir:</span><span class="sxs-lookup"><span data-stu-id="94702-204">Now you can tag the image, taking the latest image (the Release image), with the command:</span></span>

```console
docker tag <image-name>:latest <login-server-name>/<image-name>:v1
```

<span data-ttu-id="94702-205">Komutunu çalıştırdıktan sonra, `docker tag` komutuyla görüntüleri listeleyin `docker images` ve yeni etiketiyle birlikte resmi görmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="94702-205">After running the `docker tag` command, list the images with the `docker images` command, and you should see the image with the new tag.</span></span>

![Docker görüntüleri komutundan konsol çıktısı.](media/build-aspnet-core-applications-linux-containers-aks-kubernetes/tagged-docker-images-list.png)

<span data-ttu-id="94702-207">**Şekil 4-49**.</span><span class="sxs-lookup"><span data-stu-id="94702-207">**Figure 4-49**.</span></span> <span data-ttu-id="94702-208">Etiketli görüntülerin görünümü</span><span class="sxs-lookup"><span data-stu-id="94702-208">View of tagged images</span></span>

### <a name="push-the-image-into-the-azure-acr"></a><span data-ttu-id="94702-209">Görüntüyü Azure ACR 'ye gönderme</span><span class="sxs-lookup"><span data-stu-id="94702-209">Push the image into the Azure ACR</span></span>

<span data-ttu-id="94702-210">Azure Container Registry oturum açın</span><span class="sxs-lookup"><span data-stu-id="94702-210">Log in to the Azure Container Registry</span></span>

```console
az acr login --name exploredocker
```

<span data-ttu-id="94702-211">Aşağıdaki komutu kullanarak görüntüyü Azure ACR 'ye gönderin:</span><span class="sxs-lookup"><span data-stu-id="94702-211">Push the image into the Azure ACR, using the following command:</span></span>

```console
docker push <login-server-name>/<image-name>:v1
```

<span data-ttu-id="94702-212">Bu komut, görüntüleri karşıya yüklerken bir işlem gerçekleştirir, ancak işlemde geri bildirim sağlar.</span><span class="sxs-lookup"><span data-stu-id="94702-212">This command takes a while uploading the images but gives you feedback in the process.</span></span> <span data-ttu-id="94702-213">Aşağıdaki görüntüde, bir görüntüden alınan çıktıyı ve devam eden başka bir görüntüyü görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="94702-213">In the following image, you can see the output from one image completed and another in progress.</span></span>

![Docker Push komutundan konsol çıktısı.](media/build-aspnet-core-applications-linux-containers-aks-kubernetes/uploading-docker-images-complete.png)

<span data-ttu-id="94702-215">**Şekil 4-50**.</span><span class="sxs-lookup"><span data-stu-id="94702-215">**Figure 4-50**.</span></span> <span data-ttu-id="94702-216">Push komutundan konsol çıktısı.</span><span class="sxs-lookup"><span data-stu-id="94702-216">Console output from the push command.</span></span>

<span data-ttu-id="94702-217">Çok Kapsayıcılı uygulamanızı AKS kümenize dağıtmak için, `.yaml` ve dosyalarından alınan özelliklerin büyük bir bölümü olan bazı bildirim dosyalarına ihtiyacınız vardır `docker-compose.yml` `docker-compose.override.yml` .</span><span class="sxs-lookup"><span data-stu-id="94702-217">To deploy your multi-container app into your AKS cluster you need some manifest `.yaml` files that have, most of the properties taken from the `docker-compose.yml` and `docker-compose.override.yml` files.</span></span>

#### `deploy-webapi.yml`

```yml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: webapi
  labels:
    app: weather-forecast
spec:
  replicas: 1
  selector:
    matchLabels:
      service: webapi
  template:
    metadata:
      labels:
        app: weather-forecast
        service: webapi
    spec:
      containers:
        - name: webapi
          image: exploredocker.azurecr.io/webapi:v1
          imagePullPolicy: IfNotPresent
          ports:
            - containerPort: 80
              protocol: TCP
          env:
            - name: ASPNETCORE_URLS
              value: http://+:80
---
apiVersion: v1
kind: Service
metadata:
  name: webapi
  labels:
    app: weather-forecast
    service: webapi
spec:
  ports:
    - port: 80
      targetPort: 80
      protocol: TCP
  selector:
    service: webapi
```

#### `deploy-webapp.yml`

```yml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: webapp
  labels:
    app: weather-forecast
spec:
  replicas: 1
  selector:
    matchLabels:
      service: webapp
  template:
    metadata:
      labels:
        app: weather-forecast
        service: webapp
    spec:
      containers:
        - name: webapp
          image: exploredocker.azurecr.io/webapp:v1
          imagePullPolicy: IfNotPresent
          ports:
            - containerPort: 80
              protocol: TCP
          env:
            - name: ASPNETCORE_URLS
              value: http://+:80
            - name: WebApiBaseAddress
              value: http://webapi
---
apiVersion: v1
kind: Service
metadata:
  name: webapp
  labels:
    app: weather-forecast
    service: webapp
spec:
  type: LoadBalancer
  ports:
    - port: 80
      targetPort: 80
      protocol: TCP
  selector:
    service: webapp
```

> [!NOTE]
> <span data-ttu-id="94702-218">Önceki `.yml` dosyalar, `HTTP` `ASPNETCORE_URLS` örnek uygulamadaki eksik sertifikayla ilgili sorunları önlemek için, yalnızca parametresini kullanarak bağlantı noktalarını etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="94702-218">The previous `.yml` files only enable the `HTTP` ports, using the `ASPNETCORE_URLS` parameter, to avoid issues with the missing certificate in the sample app.</span></span>

> [!TIP]
> <span data-ttu-id="94702-219">Bu kılavuzda [**Azure Kubernetes Service 'e (aks) dağıtım**](deploy-azure-kubernetes-service.md) bölümünde bu örnek için aks kümesini nasıl oluşturacağınız hakkında bilgi alabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="94702-219">You can see how to create the AKS Cluster for this sample in section [**Deploy to Azure Kubernetes Service (AKS)**](deploy-azure-kubernetes-service.md) on this guide.</span></span>

<span data-ttu-id="94702-220">Artık, **kubectl**kullanarak dağıtıma hazırsınız, ancak ilk olarak aks kümesindeki kimlik bilgilerini şu komutla almalısınız:</span><span class="sxs-lookup"><span data-stu-id="94702-220">Now you're almost ready to deploy using **kubectl**, but first you must get the credentials from the AKS Cluster with this command:</span></span>

```console
az aks get-credentials --resource-group explore-docker-aks-rg --name explore-docker-aks
```

![Yukarıdaki komuttan konsol çıkışı: "keşfet-Docker-aks" değerini C:\users\mıguel.exe Kube\config içinde geçerli bağlam olarak birleştirildi](media/build-aspnet-core-applications-linux-containers-aks-kubernetes/getting-aks-credentials.png)

<span data-ttu-id="94702-222">**Şekil 4-51**.</span><span class="sxs-lookup"><span data-stu-id="94702-222">**Figure 4-51**.</span></span> <span data-ttu-id="94702-223">AKS 'ten kubectl ortamına kimlik bilgileri alma.</span><span class="sxs-lookup"><span data-stu-id="94702-223">Getting credentials from AKS into the kubectl environment.</span></span>

<span data-ttu-id="94702-224">Ayrıca, AKS kümesinin bu komutu kullanarak ACR 'den görüntü çekmesine de izin vermeniz gerekir:</span><span class="sxs-lookup"><span data-stu-id="94702-224">You also have to allow the AKS cluster to pull images from the ACR, using this command:</span></span>

```console
az aks update --name explore-docker-aks --resource-group explore-docker-aks-rg --attach-acr exploredocker
```

<span data-ttu-id="94702-225">Önceki komutun tamamlanması birkaç dakika sürebilir.</span><span class="sxs-lookup"><span data-stu-id="94702-225">The previous command might take a couple of minutes to complete.</span></span> <span data-ttu-id="94702-226">Ardından, `kubectl apply` dağıtımları başlatmak için komutunu kullanın ve ardından `kubectl get all` küme nesnelerini listeleyin.</span><span class="sxs-lookup"><span data-stu-id="94702-226">Then, use the `kubectl apply` command to launch the deployments, and then `kubectl get all` get list the cluster objects.</span></span>

```console
kubectl apply -f deploy-webapi.yml
kubectl apply -f deploy-webapp.yml

kubectl get all
```

![Yukarıdaki komutlardan konsol çıkışı: dağıtımlar uygulandı.](media/build-aspnet-core-applications-linux-containers-aks-kubernetes/kubectl-apply-command.png)

<span data-ttu-id="94702-229">**Şekil 4-52**.</span><span class="sxs-lookup"><span data-stu-id="94702-229">**Figure 4-52**.</span></span> <span data-ttu-id="94702-230">Kubernetes 'e dağıtım</span><span class="sxs-lookup"><span data-stu-id="94702-230">Deployment to Kubernetes</span></span>

<span data-ttu-id="94702-231">Yük dengeleyici dış IP 'yi alıncaya kadar beklemeniz gerekir, ile kontrol edin `kubectl get services` ve ardından sonraki görüntüde gösterildiği gibi uygulamanın o adreste kullanılabilir olması gerekir:</span><span class="sxs-lookup"><span data-stu-id="94702-231">You'll have to wait a while until the load balancer gets the external IP, checking with `kubectl get services`, and then the application should be available at that address, as shown in the next image:</span></span>

![AKS 'e dağıtılan uygulamanın tarayıcı görünümü](media/build-aspnet-core-applications-linux-containers-aks-kubernetes/aks-deployed-application.png)

<span data-ttu-id="94702-233">**Şekil 4-53**.</span><span class="sxs-lookup"><span data-stu-id="94702-233">**Figure 4-53**.</span></span> <span data-ttu-id="94702-234">Kubernetes 'e dağıtım</span><span class="sxs-lookup"><span data-stu-id="94702-234">Deployment to Kubernetes</span></span>

<span data-ttu-id="94702-235">Dağıtım tamamlandığında, bir SSH tüneli kullanarak [Kubernetes Web Kullanıcı arabirimine](https://kubernetes.io/docs/tasks/access-application-cluster/web-ui-dashboard/) yerel bir ara sunucu ile erişebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="94702-235">When the deployment completes, you can access the [Kubernetes Web UI](https://kubernetes.io/docs/tasks/access-application-cluster/web-ui-dashboard/) with a local proxy, using an ssh tunnel.</span></span>

<span data-ttu-id="94702-236">Önce aşağıdaki komutla bir ClusterRoleBinding oluşturmanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="94702-236">First you must create a ClusterRoleBinding with the following command:</span></span>

```console
kubectl create clusterrolebinding kubernetes-dashboard --clusterrole=cluster-admin --serviceaccount=kube-system:kubernetes-dashboard
```

<span data-ttu-id="94702-237">Ardından, proxy 'yi başlatmak için şu komutu kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="94702-237">And then this command to start the proxy:</span></span>

```console
az aks browse --resource-group exploredocker-aks-rg --name explore-docker-aks
```

<span data-ttu-id="94702-238">Bir tarayıcı penceresi `http://127.0.0.1:8001` Şuna benzer bir görünümle birlikte açılmalıdır:</span><span class="sxs-lookup"><span data-stu-id="94702-238">A browser window should open at `http://127.0.0.1:8001` with a view similar to this one:</span></span>

![Dağıtım, dizin, çoğaltma kümesi ve hizmet gösteren Kubernetes panosunun tarayıcı görünümü.](media/build-aspnet-core-applications-linux-containers-aks-kubernetes/kubernetes-cluster-information.png)

<span data-ttu-id="94702-240">**Şekil 4-54**.</span><span class="sxs-lookup"><span data-stu-id="94702-240">**Figure 4-54**.</span></span> <span data-ttu-id="94702-241">Kubernetes kümesi bilgilerini görüntüle</span><span class="sxs-lookup"><span data-stu-id="94702-241">View Kubernetes cluster information</span></span>

<span data-ttu-id="94702-242">Artık ASP.NET Core uygulamanız var, Linux kapsayıcılarında çalışıyor ve Azure 'da bir AKS kümesine dağıtıldı.</span><span class="sxs-lookup"><span data-stu-id="94702-242">Now you have your ASP.NET Core application, running in Linux containers, and deployed to an AKS cluster on Azure.</span></span>

> [!NOTE]
> <span data-ttu-id="94702-243">Kubernetes ile dağıtım hakkında daha fazla bilgi için bkz: <https://kubernetes.io/docs/reference/kubectl/cheatsheet/></span><span class="sxs-lookup"><span data-stu-id="94702-243">For more information on deployment with Kubernetes see: <https://kubernetes.io/docs/reference/kubectl/cheatsheet/></span></span>

> [!div class="step-by-step"]
> <span data-ttu-id="94702-244">[Önceki](set-up-windows-containers-with-powershell.md) 
>  [Sonraki](../docker-devops-workflow/index.md)</span><span class="sxs-lookup"><span data-stu-id="94702-244">[Previous](set-up-windows-containers-with-powershell.md)
[Next](../docker-devops-workflow/index.md)</span></span>
