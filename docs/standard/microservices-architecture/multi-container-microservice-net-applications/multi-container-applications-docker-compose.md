---
title: Birden çok kapsayıcı uygulamanızla docker-compose.yml tanımlama
description: Kapsayıcılı .NET uygulamaları için .NET mikro mimarisi | Birden çok kapsayıcı uygulamanızla docker-compose.yml tanımlama
keywords: Docker, Microservices, ASP.NET, Container
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/30/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: c4fed5c7ba5c2048d103f22bd2b463c143013280
ms.sourcegitcommit: c883637b41ee028786edceece4fa872939d2e64c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/26/2018
---
# <a name="defining-your-multi-container-application-with-docker-composeyml"></a><span data-ttu-id="7d375-104">Birden çok kapsayıcı uygulamanızla docker-compose.yml tanımlama</span><span class="sxs-lookup"><span data-stu-id="7d375-104">Defining your multi-container application with docker-compose.yml</span></span> 

<span data-ttu-id="7d375-105">Bu kılavuzdaki [docker-compose.yml](https://docs.docker.com/compose/compose-file/) dosya bölümünde sunulmuştur [4. adım. Birden çok kapsayıcı Docker uygulama oluştururken docker-compose.yml hizmetlerinizi tanımlamak](#step4_define_svcs_in_docker_compose_yml).</span><span class="sxs-lookup"><span data-stu-id="7d375-105">In this guide, the [docker-compose.yml](https://docs.docker.com/compose/compose-file/) file was introduced in the section [Step 4. Define your services in docker-compose.yml when building a multi-container Docker application](#step4_define_svcs_in_docker_compose_yml).</span></span> <span data-ttu-id="7d375-106">Ancak, daha ayrıntılı olarak incelenmesi yararlı docker-compose dosyaları kullanmak için ek yöntemler vardır.</span><span class="sxs-lookup"><span data-stu-id="7d375-106">However, there are additional ways to use the docker-compose files that are worth exploring in further detail.</span></span>

<span data-ttu-id="7d375-107">Örneğin, birden çok kapsayıcı uygulamanızda docker-compose.yml dosyası dağıtmak istediğiniz nasıl açıkça tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7d375-107">For example, you can explicitly describe how you want to deploy your multi-container application in the docker-compose.yml file.</span></span> <span data-ttu-id="7d375-108">İsteğe bağlı olarak, nasıl özel Docker görüntülerinizi oluşturmak zorunda kalacaklarını tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7d375-108">Optionally, you can also describe how you are going to build your custom Docker images.</span></span> <span data-ttu-id="7d375-109">(Özel Docker görüntüleri Docker CLI ile de oluşturulabilir.)</span><span class="sxs-lookup"><span data-stu-id="7d375-109">(Custom Docker images can also be built with the Docker CLI.)</span></span>

<span data-ttu-id="7d375-110">Temel olarak, her dağıtmak istediğiniz kapsayıcıları ve her bir kapsayıcı dağıtımı için belirli özellikleri tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="7d375-110">Basically, you define each of the containers you want to deploy plus certain characteristics for each container deployment.</span></span> <span data-ttu-id="7d375-111">Birden çok kapsayıcı dağıtım açıklama dosyasını oluşturduktan sonra tarafından düzenlenmiş tek bir eylem tüm çözümde dağıtabilirsiniz [docker-oluşturmanıza](https://docs.docker.com/compose/overview/) CLI komut veya dağıtabilir, saydam Visual Studio'dan.</span><span class="sxs-lookup"><span data-stu-id="7d375-111">Once you have a multi-container deployment description file, you can deploy the whole solution in a single action orchestrated by the [docker-compose up](https://docs.docker.com/compose/overview/) CLI command, or you can deploy it transparently from Visual Studio.</span></span> <span data-ttu-id="7d375-112">Aksi takdirde, Docker CLI kapsayıcı tarafından kapsayıcı birden çok adımlarda komutu komut satırından çalıştırma docker kullanarak dağıtmak için kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="7d375-112">Otherwise, you would need to use the Docker CLI to deploy container-by-container in multiple steps by using the docker run command from the command line.</span></span> <span data-ttu-id="7d375-113">Bu nedenle, docker-compose.yml tanımlanan her bir hizmet tam olarak bir resim belirtin veya bu yapı gerekir.</span><span class="sxs-lookup"><span data-stu-id="7d375-113">Therefore, each service defined in docker-compose.yml must specify exactly one image or build.</span></span> <span data-ttu-id="7d375-114">Diğer anahtarlar isteğe bağlıdır ve komut satırı ortaklarınıza çalıştırmak, docker benzer.</span><span class="sxs-lookup"><span data-stu-id="7d375-114">Other keys are optional, and are analogous to their docker run command-line counterparts.</span></span>

<span data-ttu-id="7d375-115">Aşağıdaki YAML kodu eShopOnContainers örnek için bir olası genel ancak tek docker-compose.yml dosyası tanımıdır.</span><span class="sxs-lookup"><span data-stu-id="7d375-115">The following YAML code is the definition of a possible global but single docker-compose.yml file for the eShopOnContainers sample.</span></span> <span data-ttu-id="7d375-116">Bu eShopOnContainers gerçek docker-compose dosyasından değildir.</span><span class="sxs-lookup"><span data-stu-id="7d375-116">This is not the actual docker-compose file from eShopOnContainers.</span></span> <span data-ttu-id="7d375-117">Bunun yerine, tek bir en iyi olmayan dosya, Basitleştirilmiş ve birleştirilmiş bir sürümde olduğundan çalışmak için yol docker-oluşturan dosyaları, daha sonra açıklanacaktır gibi.</span><span class="sxs-lookup"><span data-stu-id="7d375-117">Instead, it is a simplified and consolidated version in a single file, which is not the best way to work with docker-compose files, as will be explained later.</span></span>

```yml
version: '2'

services:
  webmvc:
    image: eshop/webmvc
    environment:
      - CatalogUrl=http://catalog.api
      - OrderingUrl=http://ordering.api
      - BasketUrl=http://basket.api
    ports:
      - "5100:80"
    depends_on:
      - catalog.api
      - ordering.api
      - basket.api

  catalog.api:
    image: eshop/catalog.api
    environment:
      - ConnectionString=Server=sql.data;Initial Catalog=CatalogData;User Id=sa;Password=your@password
    expose:
      - "80"
    ports:
      - "5101:80"
    #extra hosts can be used for standalone SQL Server or services at the dev PC
    extra_hosts:
      - "CESARDLSURFBOOK:10.0.75.1"
    depends_on:
      - sql.data

  ordering.api:
    image: eshop/ordering.api
    environment:
      - ConnectionString=Server=sql.data;Database=Services.OrderingDb;User Id=sa;Password=your@password
    ports:
      - "5102:80"
    #extra hosts can be used for standalone SQL Server or services at the dev PC
    extra_hosts:
      - "CESARDLSURFBOOK:10.0.75.1"
    depends_on:
      - sql.data

  basket.api:
    image: eshop/basket.api
    environment:
      - ConnectionString=sql.data
    ports:
      - "5103:80"
    depends_on:
      - sql.data

  sql.data:
    environment:
      - SA_PASSWORD=your@password
      - ACCEPT_EULA=Y
    ports:
      - "5434:1433"

  basket.data:
    image: redis
```

<span data-ttu-id="7d375-118">Hizmetleri bu dosyadaki kök anahtardır.</span><span class="sxs-lookup"><span data-stu-id="7d375-118">The root key in this file is services.</span></span> <span data-ttu-id="7d375-119">Bu anahtarın altında tanımladığınız dağıtmak ve yürüttüğünüzde çalıştırmak istediğiniz hizmetleri docker-oluşturan komut veya ne zaman bu docker-compose.yml dosyası kullanarak Visual Studio'dan dağıtın.</span><span class="sxs-lookup"><span data-stu-id="7d375-119">Under that key you define the services you want to deploy and run when you execute the docker-compose up command or when you deploy from Visual Studio by using this docker-compose.yml file.</span></span> <span data-ttu-id="7d375-120">Bu durumda, docker-compose.yml dosyası aşağıdaki listede açıklandığı gibi tanımlı, birden çok hizmetleri vardır.</span><span class="sxs-lookup"><span data-stu-id="7d375-120">In this case, the docker-compose.yml file has multiple services defined, as described in the following list.</span></span>

-   <span data-ttu-id="7d375-121">webmvc sunucu tarafı c mikro kullanan ASP.NET Core MVC uygulaması da dahil olmak üzere kapsayıcısı\#</span><span class="sxs-lookup"><span data-stu-id="7d375-121">webmvc Container including the ASP.NET Core MVC application consuming the microservices from server-side C\#</span></span>

-   <span data-ttu-id="7d375-122">catalog.api katalog ASP.NET çekirdek Web API mikro hizmet dahil olmak üzere kapsayıcısı</span><span class="sxs-lookup"><span data-stu-id="7d375-122">catalog.api Container including the Catalog ASP.NET Core Web API microservice</span></span>

-   <span data-ttu-id="7d375-123">ordering.api sıralama ASP.NET çekirdek Web API mikro hizmet dahil olmak üzere kapsayıcısı</span><span class="sxs-lookup"><span data-stu-id="7d375-123">ordering.api Container including the Ordering ASP.NET Core Web API microservice</span></span>

-   <span data-ttu-id="7d375-124">SQL.Data mikro veritabanları bulunduran Linux için SQL Server çalıştıran kapsayıcısı</span><span class="sxs-lookup"><span data-stu-id="7d375-124">sql.data Container running SQL Server for Linux, holding the microservices databases</span></span>

-   <span data-ttu-id="7d375-125">Basket.api kapsayıcı Sepeti ASP.NET çekirdek Web API mikro hizmet ile</span><span class="sxs-lookup"><span data-stu-id="7d375-125">basket.api Container with the Basket ASP.NET Core Web API microservice</span></span>

-   <span data-ttu-id="7d375-126">Basket.Data kapsayıcı REDIS önbelleği olarak Sepeti veritabanıyla REDIS önbelleği hizmeti çalışıyor</span><span class="sxs-lookup"><span data-stu-id="7d375-126">basket.data Container running the REDIS cache service, with the basket database as a REDIS cache</span></span>

### <a name="a-simple-web-service-api-container"></a><span data-ttu-id="7d375-127">Basit bir Web hizmeti API'sine kapsayıcı</span><span class="sxs-lookup"><span data-stu-id="7d375-127">A simple Web Service API container</span></span>

<span data-ttu-id="7d375-128">Tek bir kapsayıcıda odaklanan catalog.api kapsayıcı mikro basit bir tanımı vardır:</span><span class="sxs-lookup"><span data-stu-id="7d375-128">Focusing on a single container, the catalog.api container-microservice has a straightforward definition:</span></span>

```yml
  catalog.api:
    image: eshop/catalog.api
    environment:
      - ConnectionString=Server=catalog.data;Initial Catalog=CatalogData;User Id=sa;Password=your@password
    expose:
      - "80"
    ports:
      - "5101:80"
    #extra hosts can be used for standalone SQL Server or services at the dev PC
    extra_hosts:
      - "CESARDLSURFBOOK:10.0.75.1"
    depends_on:
      - sql.data
```

<span data-ttu-id="7d375-129">Bu kapsayıcılı hizmet temel yapılandırması aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="7d375-129">This containerized service has the following basic configuration:</span></span>

-   <span data-ttu-id="7d375-130">Özel eshop/catalog.api görüntüde dayanır.</span><span class="sxs-lookup"><span data-stu-id="7d375-130">It is based on the custom eshop/catalog.api image.</span></span> <span data-ttu-id="7d375-131">Basitlik'ın artırmak amacıyla için hiçbir yapı vardır: anahtar dosyasındaki ayarı.</span><span class="sxs-lookup"><span data-stu-id="7d375-131">For simplicity’s sake, there is no build: key setting in the file.</span></span> <span data-ttu-id="7d375-132">Bu görüntü önceden (docker yapı ile) oluşturulmuş gerekir veya tüm Docker kayıt defterinden (docker çekme komutuyla) yüklenmiş olan anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="7d375-132">This means that the image must have been previously built (with docker build) or have been downloaded (with the docker pull command) from any Docker registry.</span></span>

-   <span data-ttu-id="7d375-133">ConnectionString Kataloğu veri modeli içeren SQL Server örneğine erişmek için Entity Framework tarafından kullanılacak bağlantı dizesinin adlı bir ortam değişkeni tanımlar.</span><span class="sxs-lookup"><span data-stu-id="7d375-133">It defines an environment variable named ConnectionString with the connection string to be used by Entity Framework to access the SQL Server instance that contains the catalog data model.</span></span> <span data-ttu-id="7d375-134">Bu durumda, aynı SQL Server kapsayıcı birden çok veritabanı tutuyor.</span><span class="sxs-lookup"><span data-stu-id="7d375-134">In this case, the same SQL Server container is holding multiple databases.</span></span> <span data-ttu-id="7d375-135">Bu nedenle, daha az bellek için Docker geliştirme makinenizde gerekir.</span><span class="sxs-lookup"><span data-stu-id="7d375-135">Therefore, you need less memory in your development machine for Docker.</span></span> <span data-ttu-id="7d375-136">Bununla birlikte, her mikro hizmet veritabanı için bir SQL Server kapsayıcısı dağıtabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7d375-136">However, you could also deploy one SQL Server container for each microservice database.</span></span>

-   <span data-ttu-id="7d375-137">SQL Server sql.data, SQL Server örneği için Linux çalıştıran kapsayıcısı için kullandığınız aynı adı olan addır.</span><span class="sxs-lookup"><span data-stu-id="7d375-137">The SQL Server name is sql.data, which is the same name used for the container that is running the SQL Server instance for Linux.</span></span> <span data-ttu-id="7d375-138">Bu uygundur; iç IP diğer kapsayıcılardan eriştiğiniz kapsayıcıları için bilmeniz gerek kalmaması (için Docker ana bilgisayar iç) bu ad çözümlemesi kullanabilmek için ağ adresi çözümleyin.</span><span class="sxs-lookup"><span data-stu-id="7d375-138">This is convenient; being able to use this name resolution (internal to the Docker host) will resolve the network address so you don’t need to know the internal IP for the containers you are accessing from other containers.</span></span>

<span data-ttu-id="7d375-139">Bağlantı dizesi bir ortam değişkeni tarafından tanımlı olduğundan farklı mekanizması aracılığıyla ve farklı bir zamanda bu değişkeni ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7d375-139">Because the connection string is defined by an environment variable, you could set that variable through a different mechanism and at a different time.</span></span> <span data-ttu-id="7d375-140">Örneğin, farklı bir bağlantı dizesi üretime son konakları veya CI/CD hatlarınızı VSTS ya da tercih edilen DevOps sisteminizi gelen yapmakta dağıtırken ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7d375-140">For example, you could set a different connection string when deploying to production in the final hosts, or by doing it from your CI/CD pipelines in VSTS or your preferred DevOps system.</span></span>

-   <span data-ttu-id="7d375-141">Bağlantı noktası 80 iç erişim için Docker ana catalog.api Hizmeti'nde gösterir.</span><span class="sxs-lookup"><span data-stu-id="7d375-141">It exposes port 80 for internal access to the catalog.api service within the Docker host.</span></span> <span data-ttu-id="7d375-142">Konak şu anda bir Linux VM Linux için Docker görüntüde dayanır, ancak bunun yerine bir Windows görüntüsünü çalıştırmak için kapsayıcı yapılandırabilirsiniz nedeni.</span><span class="sxs-lookup"><span data-stu-id="7d375-142">The host is currently a Linux VM because it is based on a Docker image for Linux, but you could configure the container to run on a Windows image instead.</span></span>

-   <span data-ttu-id="7d375-143">Kullanıma sunulan bağlantı noktası 80 kapsayıcısındaki (Linux VM'de) Docker ana makinede 5101 numaralı bağlantı noktasına iletir.</span><span class="sxs-lookup"><span data-stu-id="7d375-143">It forwards the exposed port 80 on the container to port 5101 on the Docker host machine (the Linux VM).</span></span>

-   <span data-ttu-id="7d375-144">Web hizmeti (bir kapsayıcıda çalışan Linux veritabanı için SQL Server örneğini) sql.data hizmetine bağlar.</span><span class="sxs-lookup"><span data-stu-id="7d375-144">It links the web service to the sql.data service (the SQL Server instance for Linux database running in a container).</span></span> <span data-ttu-id="7d375-145">Bu bağımlılık belirttiğinizde, sql.data kapsayıcısı zaten başlatıldı kadar catalog.api kapsayıcı başlatılmaz; Bu ilk catalog.api SQL Server veritabanı olmasını gerektiğinden önemli ve çalışır durumdadır.</span><span class="sxs-lookup"><span data-stu-id="7d375-145">When you specify this dependency, the catalog.api container will not start until the sql.data container has already started; this is important because catalog.api needs to have the SQL Server database up and running first.</span></span> <span data-ttu-id="7d375-146">Docker yalnızca kapsayıcı düzeyinde denetler olduğundan ancak, bu tür bir kapsayıcı bağımlılığı birçok durumda yeterli değil.</span><span class="sxs-lookup"><span data-stu-id="7d375-146">However, this kind of container dependency is not enough in many cases, because Docker checks only at the container level.</span></span> <span data-ttu-id="7d375-147">Yeniden deneme mantığı üstel geri alma ile istemci mikro uygulamanız önerilir; böylece bazen hizmetinde (büyük/küçük harfe bu SQL Server) hala hazır olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="7d375-147">Sometimes the service (in this case SQL Server) might still not be ready, so it is advisable to implement retry logic with exponential backoff in your client microservices.</span></span> <span data-ttu-id="7d375-148">Bir bağımlılık kapsayıcı kısa bir süre için hazır değilse, bu şekilde, uygulamayı esnek olmaya devam eder.</span><span class="sxs-lookup"><span data-stu-id="7d375-148">That way, if a dependency container is not ready for a short time, the application will still be resilient.</span></span>

-   <span data-ttu-id="7d375-149">Dış sunucuları erişmesine izin vermek için yapılandırılmış: ek\_ayarı ana dış sunucuların ya da makineleri Docker ana dışında erişmenize olanak tanır (diğer bir deyişle, geliştirme Docker olan bir Linux VM varsayılan dışında barındırma) gibi bir yerel SQL PC Geliştirme Sunucusu örneğinde.</span><span class="sxs-lookup"><span data-stu-id="7d375-149">It is configured to allow access to external servers: the extra\_hosts setting allows you to access external servers or machines outside of the Docker host (that is, outside the default Linux VM which is a development Docker host), such as a local SQL Server instance on your development PC.</span></span>

<span data-ttu-id="7d375-150">Aşağıdaki bölümlerde ele alınacaktır diğer, daha gelişmiş docker-compose.yml ayarları vardır.</span><span class="sxs-lookup"><span data-stu-id="7d375-150">There are also other, more advanced docker-compose.yml settings that we will discuss in the following sections.</span></span>

### <a name="using-docker-compose-files-to-target-multiple-environments"></a><span data-ttu-id="7d375-151">Kullanarak docker-oluşturan birden çok ortamları hedeflemek için dosyaları</span><span class="sxs-lookup"><span data-stu-id="7d375-151">Using docker-compose files to target multiple environments</span></span>

<span data-ttu-id="7d375-152">Docker-compose.yml dosyalar tanım dosyalarını ve bu biçimi anlamak birden çok altyapıları tarafından kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="7d375-152">The docker-compose.yml files are definition files and can be used by multiple infrastructures that understand that format.</span></span> <span data-ttu-id="7d375-153">Docker en kolay araçtır-komutu oluşturmak, ancak bu dosya ayrıca orchestrators (örneğin, Docker Swarm) anlamak gibi diğer araçları.</span><span class="sxs-lookup"><span data-stu-id="7d375-153">The most straightforward tool is the docker-compose command, but other tools like orchestrators (for example, Docker Swarm) also understand that file.</span></span>

<span data-ttu-id="7d375-154">Kullanarak bu nedenle, aşağıdaki ana senaryo hedef komutu docker compose'u.</span><span class="sxs-lookup"><span data-stu-id="7d375-154">Therefore, by using the docker-compose command you can target the following main scenarios.</span></span>

#### <a name="development-environments"></a><span data-ttu-id="7d375-155">Geliştirme ortamları</span><span class="sxs-lookup"><span data-stu-id="7d375-155">Development environments</span></span>

<span data-ttu-id="7d375-156">Uygulamaları geliştirirken, uygulamanın bir yalıtılmış geliştirme ortamında çalıştırılabilmesi için önemlidir.</span><span class="sxs-lookup"><span data-stu-id="7d375-156">When you develop applications, it is important to be able to run an application in an isolated development environment.</span></span> <span data-ttu-id="7d375-157">Kullanabileceğiniz docker compose'u bu ortam oluşturmak veya hangi kullanımlar docker-perde arkasında oluşturan Visual Studio kullanmak için CLI komutu.</span><span class="sxs-lookup"><span data-stu-id="7d375-157">You can use the docker-compose CLI command to create that environment or use Visual Studio which uses docker-compose under the covers.</span></span>

<span data-ttu-id="7d375-158">Docker-compose.yml dosyası, yapılandırmak ve tüm uygulama Hizmet bağımlılıklarını (diğer hizmetler, önbellek, veritabanları, kuyruklar, vb.) belge olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="7d375-158">The docker-compose.yml file allows you to configure and document all your application’s service dependencies (other services, cache, databases, queues, etc.).</span></span> <span data-ttu-id="7d375-159">Kullanarak CLI komutu docker compose'u, oluşturabilir ve her bir bağımlılığın için bir veya daha fazla kapsayıcı tek bir komutla başlatın (docker-oluşturmanıza).</span><span class="sxs-lookup"><span data-stu-id="7d375-159">Using the docker-compose CLI command, you can create and start one or more containers for each dependency with a single command (docker-compose up).</span></span>

<span data-ttu-id="7d375-160">Docker-compose.yml dosyalar Docker altyapısı tarafından yorumlanan yapılandırma dosyaları ancak uygun belge dosyalarını birden çok kapsayıcı uygulamanızı bileşimi hakkında olarak da hizmet.</span><span class="sxs-lookup"><span data-stu-id="7d375-160">The docker-compose.yml files are configuration files interpreted by Docker engine but also serve as convenient documentation files about the composition of your multi-container application.</span></span>

#### <a name="testing-environments"></a><span data-ttu-id="7d375-161">Sınama ortamları</span><span class="sxs-lookup"><span data-stu-id="7d375-161">Testing environments</span></span>

<span data-ttu-id="7d375-162">Herhangi bir sürekli dağıtımı (CD) veya sürekli tümleştirme (CI) işlemi önemli bir parçası olan birim testleri ve tümleştirme testleri.</span><span class="sxs-lookup"><span data-stu-id="7d375-162">An important part of any continuous deployment (CD) or continuous integration (CI) process are the unit tests and integration tests.</span></span> <span data-ttu-id="7d375-163">Bu otomatikleştirilmiş testleri yalıtılmış bir ortamda gerektirdiğinden, kullanıcılar veya herhangi bir değişiklik uygulamanın veri tarafından etkilenmez.</span><span class="sxs-lookup"><span data-stu-id="7d375-163">These automated tests require an isolated environment so they are not impacted by the users or any other change in the application’s data.</span></span>

<span data-ttu-id="7d375-164">Docker Compose ile oluşturun ve o yalıtılmış bir ortamda kolayca komut istemi veya komut dosyaları, aşağıdaki komutları gibi birkaç komutları yok:</span><span class="sxs-lookup"><span data-stu-id="7d375-164">With Docker Compose you can create and destroy that isolated environment very easily in a few commands from your command prompt or scripts, like the following commands:</span></span>

```
docker-compose up -d
./run_unit_tests
docker-compose down
```

#### <a name="production-deployments"></a><span data-ttu-id="7d375-165">Üretim dağıtımları</span><span class="sxs-lookup"><span data-stu-id="7d375-165">Production deployments</span></span>

<span data-ttu-id="7d375-166">Oluştur, uzak bir Docker altyapısına dağıtmak için de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7d375-166">You can also use Compose to deploy to a remote Docker Engine.</span></span> <span data-ttu-id="7d375-167">Tipik bir servis talebi için tek bir Docker ana bilgisayar örneği dağıtmaktır (bir üretim VM veya sunucusu ile sağlanan gibi [Docker makine](https://docs.docker.com/machine/overview/)).</span><span class="sxs-lookup"><span data-stu-id="7d375-167">A typical case is to deploy to a single Docker host instance (like a production VM or server provisioned with [Docker Machine](https://docs.docker.com/machine/overview/)).</span></span> <span data-ttu-id="7d375-168">Ancak tüm olabilir [Docker Swarm](https://docs.docker.com/swarm/overview/) kümeleri de docker-compose.yml dosyaları ile uyumlu olmadığından, küme.</span><span class="sxs-lookup"><span data-stu-id="7d375-168">But it could also be an entire [Docker Swarm](https://docs.docker.com/swarm/overview/) cluster, because clusters are also compatible with the docker-compose.yml files.</span></span>

<span data-ttu-id="7d375-169">Tüm diğer orchestrator (Azure Service Fabric, Mesos DC/OS, Kubernetes, vb.) kullanıyorsanız, docker-compose.yml ancak diğer orchestrator tarafından gerekli olan biçime benzer Kurulum ve meta verileri yapılandırma ayarlarını eklemeniz gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="7d375-169">If you are using any other orchestrator (Azure Service Fabric, Mesos DC/OS, Kubernetes, etc.), you might need to add setup and metadata configuration settings like those in docker-compose.yml, but in the format required by the other orchestrator.</span></span>

<span data-ttu-id="7d375-170">Herhangi bir durumda, docker compose'u geliştirme, test ve üretim iş akışları için kullanışlı bir aracı ve meta veri biçimi olsa üretim iş akışı kullanmakta olduğunuz orchestrator değişebilir.</span><span class="sxs-lookup"><span data-stu-id="7d375-170">In any case, docker-compose is a convenient tool and metadata format for development, testing and production workflows, although the production workflow might vary on the orchestrator you are using.</span></span>

### <a name="using-multiple-docker-compose-files-to-handle-several-environments"></a><span data-ttu-id="7d375-171">Birden fazla docker-oluşturan çeşitli ortamlar işlemek için dosyaları</span><span class="sxs-lookup"><span data-stu-id="7d375-171">Using multiple docker-compose files to handle several environments</span></span>

<span data-ttu-id="7d375-172">Birden çok farklı ortamlarda hedeflerken kullanması gereken dosyaları oluşturun.</span><span class="sxs-lookup"><span data-stu-id="7d375-172">When targeting different environments, you should use multiple compose files.</span></span> <span data-ttu-id="7d375-173">Bu ortam bağlı olarak birden çok yapılandırma çeşitleri oluşturmanıza olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="7d375-173">This lets you create multiple configuration variants depending on the environment.</span></span>

#### <a name="overriding-the-base-docker-compose-file"></a><span data-ttu-id="7d375-174">Temel docker-compose dosya geçersiz kılma</span><span class="sxs-lookup"><span data-stu-id="7d375-174">Overriding the base docker-compose file</span></span>

<span data-ttu-id="7d375-175">Önceki bölümlerde Basitleştirilmiş örneklerde olduğu gibi tek docker-compose.yml dosyası kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7d375-175">You could use a single docker-compose.yml file as in the simplified examples shown in previous sections.</span></span> <span data-ttu-id="7d375-176">Bununla birlikte, çoğu uygulama için önerilmez.</span><span class="sxs-lookup"><span data-stu-id="7d375-176">However, that is not recommended for most applications.</span></span>

<span data-ttu-id="7d375-177">Varsayılan olarak, iki dosya, docker-compose.yml ve isteğe bağlı docker compose.override.yml dosyası oluşturma okur.</span><span class="sxs-lookup"><span data-stu-id="7d375-177">By default, Compose reads two files, a docker-compose.yml and an optional docker-compose.override.yml file.</span></span> <span data-ttu-id="7d375-178">Şekil 8-11'de gösterildiği gibi zaman, Visual Studio kullanarak ve Docker desteği, Visual Studio de etkinleştirme, CI/CD hatlarınızı gibi VSTS içinde kullanmak bir ek docker compose.ci.build,yml dosyası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="7d375-178">As shown in Figure 8-11, when you are using Visual Studio and enabling Docker support, Visual Studio also creates an additional docker-compose.ci.build,yml file for you to use from your CI/CD pipelines like in VSTS.</span></span>

![](./media/image12.png)

<span data-ttu-id="7d375-179">**Şekil 8-11**.</span><span class="sxs-lookup"><span data-stu-id="7d375-179">**Figure 8-11**.</span></span> <span data-ttu-id="7d375-180">Visual Studio 2017 dosyalarında docker compose'u</span><span class="sxs-lookup"><span data-stu-id="7d375-180">docker-compose files in Visual Studio 2017</span></span>

<span data-ttu-id="7d375-181">Visual Studio Code veya Sublime, gibi herhangi bir Düzenleyicisi docker-compose dosyaları düzenleyin ve uygulamayla çalıştırmak docker compose'u up komutu.</span><span class="sxs-lookup"><span data-stu-id="7d375-181">You can edit the docker-compose files with any editor, like Visual Studio Code or Sublime, and run the application with the docker-compose up command.</span></span>

<span data-ttu-id="7d375-182">Kurala göre docker-compose.yml dosyası temel yapılandırma ve diğer statik ayarlarını içerir.</span><span class="sxs-lookup"><span data-stu-id="7d375-182">By convention, the docker-compose.yml file contains your base configuration and other static settings.</span></span> <span data-ttu-id="7d375-183">Hizmet yapılandırması, hedeflediğiniz dağıtım ortamı bağlı olarak değiştirmemelisiniz anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="7d375-183">That means that the service configuration should not change depending on the deployment environment you are targeting.</span></span>

<span data-ttu-id="7d375-184">Adından da anlaşılacağı gibi docker compose.override.yml dosya dağıtım ortamınıza bağlıdır yapılandırma gibi temel yapılandırmasını geçersiz kılma yapılandırma ayarlarını içerir.</span><span class="sxs-lookup"><span data-stu-id="7d375-184">The docker-compose.override.yml file, as its name suggests, contains configuration settings that override the base configuration, such as configuration that depends on the deployment environment.</span></span> <span data-ttu-id="7d375-185">Farklı adlara sahip birden çok geçersiz kılma dosyaları da sahip olabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7d375-185">You can have multiple override files with different names also.</span></span> <span data-ttu-id="7d375-186">Geçersiz kılma dosyalar genellikle uygulama ancak belirli bir ortam veya bir dağıtım için gerekli ek bilgiler içerir.</span><span class="sxs-lookup"><span data-stu-id="7d375-186">The override files usually contain additional information needed by the application but specific to an environment or to a deployment.</span></span>

#### <a name="targeting-multiple-environments"></a><span data-ttu-id="7d375-187">Birden çok ortamları hedefleme</span><span class="sxs-lookup"><span data-stu-id="7d375-187">Targeting multiple environments</span></span>

<span data-ttu-id="7d375-188">Tipik kullanım örneği olan birden çok tanımlarken oluşturan dosyaları hazırlama, CI ya da geliştirme üretim gibi birden çok ortamları hedefleyebilirsiniz şekilde.</span><span class="sxs-lookup"><span data-stu-id="7d375-188">A typical use case is when you define multiple compose files so you can target multiple environments, like production, staging, CI, or development.</span></span> <span data-ttu-id="7d375-189">Bu farklılıklar desteklemek için Şekil 8-12'de gösterildiği gibi birden çok dosyalarına Oluştur yapılandırmanızı bölebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7d375-189">To support these differences, you can split your Compose configuration into multiple files, as shown in Figure 8-12.</span></span>

![](./media/image13.png)

<span data-ttu-id="7d375-190">**Şekil 8-12**.</span><span class="sxs-lookup"><span data-stu-id="7d375-190">**Figure 8-12**.</span></span> <span data-ttu-id="7d375-191">Birden çok oluşturan docker dosyaları temel docker-compose.yml dosyasındaki değerleri geçersiz kılma</span><span class="sxs-lookup"><span data-stu-id="7d375-191">Multiple docker-compose files overriding values in the base docker-compose.yml file</span></span>

<span data-ttu-id="7d375-192">Temel docker-compose.yml dosyası ile başlatın.</span><span class="sxs-lookup"><span data-stu-id="7d375-192">You start with the base docker-compose.yml file.</span></span> <span data-ttu-id="7d375-193">Bu temel dosyanın ortamına bağlı olarak değiştirmeyin temel veya statik yapılandırma ayarlarını içermesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="7d375-193">This base file has to contain the base or static configuration settings that do not change depending on the environment.</span></span> <span data-ttu-id="7d375-194">Örneğin, eShopOnContainers temel dosyası olarak aşağıdaki docker-compose.yml dosyası vardır.</span><span class="sxs-lookup"><span data-stu-id="7d375-194">For example, the eShopOnContainers has the following docker-compose.yml file as the base file.</span></span>

```yml
#docker-compose.yml (Base)
version: '3'
services:
  basket.api:
    image: eshop/basket.api:${TAG:-latest}
    build:
      context: ./src/Services/Basket/Basket.API
      dockerfile: Dockerfile    
    depends_on:
      - basket.data
      - identity.api
      - rabbitmq

  catalog.api:
    image: eshop/catalog.api:${TAG:-latest}
    build:
      context: ./src/Services/Catalog/Catalog.API
      dockerfile: Dockerfile    
    depends_on:
      - sql.data
      - rabbitmq

  marketing.api:
    image: eshop/marketing.api:${TAG:-latest}
    build:
      context: ./src/Services/Marketing/Marketing.API
      dockerfile: Dockerfile    
    depends_on:
      - sql.data
      - nosql.data
      - identity.api
      - rabbitmq

  webmvc:
    image: eshop/webmvc:${TAG:-latest}
    build:
      context: ./src/Web/WebMVC
      dockerfile: Dockerfile    
    depends_on:
      - catalog.api
      - ordering.api
      - identity.api
      - basket.api
      - marketing.api

  sql.data:
    image: microsoft/mssql-server-linux:2017-latest

  nosql.data:
    image: mongo

  basket.data:
    image: redis
      
  rabbitmq:
    image: rabbitmq:3-management

```

<span data-ttu-id="7d375-195">Temel docker-compose.yml dosyası değerler farklı bir hedef dağıtım ortamları nedeniyle değiştirmemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="7d375-195">The values in the base docker-compose.yml file should not change because of different target deployment environments.</span></span>

<span data-ttu-id="7d375-196">Örneğin, webmvc hizmet tanımını odaklanmanıza, nasıl bu bilgileri çok aynı hedefleme hangi ortam olduğunu görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7d375-196">If you focus on the webmvc service definition, for instance, you can see how that information is much the same no matter what environment you might be targeting.</span></span> <span data-ttu-id="7d375-197">Aşağıdaki bilgilere sahip:</span><span class="sxs-lookup"><span data-stu-id="7d375-197">You have the following information:</span></span>

-   <span data-ttu-id="7d375-198">Hizmet adı: webmvc.</span><span class="sxs-lookup"><span data-stu-id="7d375-198">The service name: webmvc.</span></span>

-   <span data-ttu-id="7d375-199">Kapsayıcının özel görüntü: Elektronik Mağaza/webmvc.</span><span class="sxs-lookup"><span data-stu-id="7d375-199">The container’s custom image: eshop/webmvc.</span></span>

-   <span data-ttu-id="7d375-200">Kullanmak için hangi Dockerfile gösteren özel Docker görüntü oluşturmak için komutu.</span><span class="sxs-lookup"><span data-stu-id="7d375-200">The command to build the custom Docker image, indicating which Dockerfile to use.</span></span>

-   <span data-ttu-id="7d375-201">Bir bağımlılık kapsayıcıları başlatılıncaya kadar bu kapsayıcı başlamaz diğer hizmetler bağımlılıkları.</span><span class="sxs-lookup"><span data-stu-id="7d375-201">Dependencies on other services, so this container does not start until the other dependency containers have started.</span></span>

<span data-ttu-id="7d375-202">Ek yapılandırma olabilir, ancak önemli temel docker-compose.yml dosyası, yalnızca ortamlar arasında ortak olan bilgileri ayarlamak istediğinizi noktasıdır.</span><span class="sxs-lookup"><span data-stu-id="7d375-202">You can have additional configuration, but the important point is that in the base docker-compose.yml file, you just want to set the information that is common across environments.</span></span> <span data-ttu-id="7d375-203">Ardından docker compose.override.yml veya üretim veya hazırlama benzer dosyalarını her ortam için belirli yapılandırma yerleştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="7d375-203">Then in the docker-compose.override.yml or similar files for production or staging, you should place configuration that is specific for each environment.</span></span>

<span data-ttu-id="7d375-204">Genellikle, docker compose.override.yml eShopOnContainers aşağıdaki örnekte olduğu gibi geliştirme ortamınız için kullanılır:</span><span class="sxs-lookup"><span data-stu-id="7d375-204">Usually, the docker-compose.override.yml is used for your development environment, as in the following example from eShopOnContainers:</span></span>

```yml
#docker-compose.override.yml (Extended config for DEVELOPMENT env.)
version: '3'

services: 
# Simplified number of services here: 
      
  basket.api:
    environment:
      - ASPNETCORE_ENVIRONMENT=Development
      - ASPNETCORE_URLS=http://0.0.0.0:80
      - ConnectionString=${ESHOP_AZURE_REDIS_BASKET_DB:-basket.data}
      - identityUrl=http://identity.api              
      - IdentityUrlExternal=http://${ESHOP_EXTERNAL_DNS_NAME_OR_IP}:5105
      - EventBusConnection=${ESHOP_AZURE_SERVICE_BUS:-rabbitmq}
      - EventBusUserName=${ESHOP_SERVICE_BUS_USERNAME}
      - EventBusPassword=${ESHOP_SERVICE_BUS_PASSWORD}      
      - AzureServiceBusEnabled=False
      - ApplicationInsights__InstrumentationKey=${INSTRUMENTATION_KEY}
      - OrchestratorType=${ORCHESTRATOR_TYPE}
      - UseLoadTest=${USE_LOADTEST:-False}

    ports:
      - "5103:80"

  catalog.api:
    environment:
      - ASPNETCORE_ENVIRONMENT=Development
      - ASPNETCORE_URLS=http://0.0.0.0:80
      - ConnectionString=${ESHOP_AZURE_CATALOG_DB:-Server=sql.data;Database=Microsoft.eShopOnContainers.Services.CatalogDb;User Id=sa;Password=Pass@word}
      - PicBaseUrl=${ESHOP_AZURE_STORAGE_CATALOG_URL:-http://localhost:5101/api/v1/catalog/items/[0]/pic/}   
      - EventBusConnection=${ESHOP_AZURE_SERVICE_BUS:-rabbitmq}
      - EventBusUserName=${ESHOP_SERVICE_BUS_USERNAME}
      - EventBusPassword=${ESHOP_SERVICE_BUS_PASSWORD}         
      - AzureStorageAccountName=${ESHOP_AZURE_STORAGE_CATALOG_NAME}
      - AzureStorageAccountKey=${ESHOP_AZURE_STORAGE_CATALOG_KEY}
      - UseCustomizationData=True
      - AzureServiceBusEnabled=False
      - AzureStorageEnabled=False
      - ApplicationInsights__InstrumentationKey=${INSTRUMENTATION_KEY}
      - OrchestratorType=${ORCHESTRATOR_TYPE}
    ports:
      - "5101:80"

  marketing.api:
    environment:
      - ASPNETCORE_ENVIRONMENT=Development
      - ASPNETCORE_URLS=http://0.0.0.0:80
      - ConnectionString=${ESHOP_AZURE_MARKETING_DB:-Server=sql.data;Database=Microsoft.eShopOnContainers.Services.MarketingDb;User Id=sa;Password=Pass@word}
      - MongoConnectionString=${ESHOP_AZURE_COSMOSDB:-mongodb://nosql.data}
      - MongoDatabase=MarketingDb
      - EventBusConnection=${ESHOP_AZURE_SERVICE_BUS:-rabbitmq}
      - EventBusUserName=${ESHOP_SERVICE_BUS_USERNAME}
      - EventBusPassword=${ESHOP_SERVICE_BUS_PASSWORD}          
      - identityUrl=http://identity.api              
      - IdentityUrlExternal=http://${ESHOP_EXTERNAL_DNS_NAME_OR_IP}:5105
      - CampaignDetailFunctionUri=${ESHOP_AZUREFUNC_CAMPAIGN_DETAILS_URI}
      - PicBaseUrl=${ESHOP_AZURE_STORAGE_MARKETING_URL:-http://localhost:5110/api/v1/campaigns/[0]/pic/}
      - AzureStorageAccountName=${ESHOP_AZURE_STORAGE_MARKETING_NAME}
      - AzureStorageAccountKey=${ESHOP_AZURE_STORAGE_MARKETING_KEY}
      - AzureServiceBusEnabled=False
      - AzureStorageEnabled=False
      - ApplicationInsights__InstrumentationKey=${INSTRUMENTATION_KEY}
      - OrchestratorType=${ORCHESTRATOR_TYPE}
      - UseLoadTest=${USE_LOADTEST:-False}
    ports:
      - "5110:80"

  webmvc:
    environment:
      - ASPNETCORE_ENVIRONMENT=Development
      - ASPNETCORE_URLS=http://0.0.0.0:80
      - CatalogUrl=http://catalog.api
      - OrderingUrl=http://ordering.api
      - BasketUrl=http://basket.api
      - LocationsUrl=http://locations.api
      - IdentityUrl=http://10.0.75.1:5105
      - MarketingUrl=http://marketing.api                                                    
      - CatalogUrlHC=http://catalog.api/hc
      - OrderingUrlHC=http://ordering.api/hc
      - IdentityUrlHC=http://identity.api/hc     
      - BasketUrlHC=http://basket.api/hc
      - MarketingUrlHC=http://marketing.api/hc
      - PaymentUrlHC=http://payment.api/hc
      - UseCustomizationData=True
      - ApplicationInsights__InstrumentationKey=${INSTRUMENTATION_KEY}
      - OrchestratorType=${ORCHESTRATOR_TYPE}
      - UseLoadTest=${USE_LOADTEST:-False}
    ports:
      - "5100:80"
  sql.data:
    environment:
      - MSSQL_SA_PASSWORD=Pass@word
      - ACCEPT_EULA=Y
      - MSSQL_PID=Developer
    ports:
      - "5433:1433"
  nosql.data:
    ports:
      - "27017:27017"
  basket.data:
    ports:
      - "6379:6379"      
  rabbitmq:
    ports:
      - "15672:15672"
      - "5672:5672"

```

<span data-ttu-id="7d375-205">Bu örnekte, geliştirme geçersiz kılma yapılandırmasını barındırmak için bazı bağlantı noktalarını kullanıma sunar, ortam değişkenleri tanımlar URL'leri yönlendirmek ve geliştirme ortamı için bağlantı dizelerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="7d375-205">In this example, the development override configuration exposes some ports to the host, defines environment variables with redirect URLs, and specifies connection strings for the development environment.</span></span> <span data-ttu-id="7d375-206">Bu ayarlar tüm yalnızca geliştirme ortamına ' dir.</span><span class="sxs-lookup"><span data-stu-id="7d375-206">These settings are all just for the development environment.</span></span>

<span data-ttu-id="7d375-207">Çalıştırdığınızda `docker-compose up` (veya Visual Studio'dan başlatma), her iki dosyaları birleştirme gibi komut geçersiz kılmaları otomatik olarak okur.</span><span class="sxs-lookup"><span data-stu-id="7d375-207">When you run `docker-compose up` (or launch it from Visual Studio), the command reads the overrides automatically as if it were merging both files.</span></span>

<span data-ttu-id="7d375-208">Üretim ortamında, farklı yapılandırma değerlerini, bağlantı noktası veya bağlantı dizeleri için başka bir oluşturma dosyası istediğinizi varsayalım.</span><span class="sxs-lookup"><span data-stu-id="7d375-208">Suppose that you want another Compose file for the production environment, with different configuration values, ports or connection strings.</span></span> <span data-ttu-id="7d375-209">Adlı dosyası gibi başka bir geçersiz kılma dosyası oluşturabilirsiniz `docker-compose.prod.yml` farklı ayarlar ve ortam değişkenleri.</span><span class="sxs-lookup"><span data-stu-id="7d375-209">You can create another override file, like file named `docker-compose.prod.yml` with different settings and environment variables.</span></span>  <span data-ttu-id="7d375-210">Bu dosyayı farklı bir Git deposu içinde depolanan veya yönetilebilir ve farklı bir takım tarafından güvenli hale getirilmiş.</span><span class="sxs-lookup"><span data-stu-id="7d375-210">That file might be stored in a different Git repo or managed and secured by a different team.</span></span>

#### <a name="how-to-deploy-with-a-specific-override-file"></a><span data-ttu-id="7d375-211">Bir özel geçersiz kılma dosyayla dağıtma</span><span class="sxs-lookup"><span data-stu-id="7d375-211">How to deploy with a specific override file</span></span>

<span data-ttu-id="7d375-212">Birden çok geçersiz kılma dosyaları veya bir geçersiz kılma dosyasını farklı bir ad ile kullanmak için -f seçeneğiyle kullanabilirsiniz komutu docker compose'u ve dosyaları belirtin.</span><span class="sxs-lookup"><span data-stu-id="7d375-212">To use multiple override files, or an override file with a different name, you can use the -f option with the docker-compose command and specify the files.</span></span> <span data-ttu-id="7d375-213">Komut satırında belirtilen sırada birleştirmeler dosyaları oluşturun.</span><span class="sxs-lookup"><span data-stu-id="7d375-213">Compose merges files in the order they are specified on the command line.</span></span> <span data-ttu-id="7d375-214">Aşağıdaki örnek, geçersiz kılma dosyalarıyla dağıtma gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="7d375-214">The following example shows how to deploy with override files.</span></span>

```
docker-compose -f docker-compose.yml -f docker-compose.prod.yml up -d
```

#### <a name="using-environment-variables-in-docker-compose-files"></a><span data-ttu-id="7d375-215">Ortam değişkenlerini kullanma, docker-dosyaları oluşturma</span><span class="sxs-lookup"><span data-stu-id="7d375-215">Using environment variables in docker-compose files</span></span>

<span data-ttu-id="7d375-216">Bu, biz önceki örneklerde gösterildiği gibi ortam değişkenlerinin, yapılandırma bilgileri elde edebilmek için özellikle üretim ortamlarında, uygundur.</span><span class="sxs-lookup"><span data-stu-id="7d375-216">It is convenient, especially in production environments, to be able to get configuration information from environment variables, as we have shown in previous examples.</span></span> <span data-ttu-id="7d375-217">Docker-compose dosyalarınızı sözdizimini kullanarak bir ortam değişkeni başvurusu \${MY\_VAR}.</span><span class="sxs-lookup"><span data-stu-id="7d375-217">You reference an environment variable in your docker-compose files using the syntax \${MY\_VAR}.</span></span> <span data-ttu-id="7d375-218">Aşağıdaki satırı docker compose.prod.yml dosyasından bir ortam değişkeni değeri başvuru gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="7d375-218">The following line from a docker-compose.prod.yml file shows how to reference the value of an environment variable.</span></span>

```yml
IdentityUrl=http://${ESHOP_PROD_EXTERNAL_DNS_NAME_OR_IP}:5105
```

<span data-ttu-id="7d375-219">Ortam değişkenleri oluşturuldu ve ana bilgisayar ortamınıza bağlı olarak, farklı şekillerde başlatıldı (Linux, Windows, bulut küme, vs.).</span><span class="sxs-lookup"><span data-stu-id="7d375-219">Environment variables are created and initialized in different ways, depending on your host environment (Linux, Windows, Cloud cluster, etc.).</span></span> <span data-ttu-id="7d375-220">Ancak, uygun bir yaklaşım .env dosya kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="7d375-220">However, a convenient approach is to use an .env file.</span></span> <span data-ttu-id="7d375-221">.Env dosyasındaki varsayılan ortam değişkenleri bildirme docker-compose dosyalarını destekler.</span><span class="sxs-lookup"><span data-stu-id="7d375-221">The docker-compose files support declaring default environment variables in the .env file.</span></span> <span data-ttu-id="7d375-222">Bu ortam değişkenleri için varsayılan değerleri değerlerdir.</span><span class="sxs-lookup"><span data-stu-id="7d375-222">These values for the environment variables are the default values.</span></span> <span data-ttu-id="7d375-223">Ancak her ortamınızı (ana bilgisayar işletim sistemi veya ortam değişkenleri, kümeden) tanımlanmış değeri geçersiz kılınabilir.</span><span class="sxs-lookup"><span data-stu-id="7d375-223">But they can be overridden by the values you might have defined in each of your environments (host OS or environment variables from your cluster).</span></span> <span data-ttu-id="7d375-224">Bu .env dosyasını bu klasöre yerleştirin nerede docker compose'u komutu yürütüldü.</span><span class="sxs-lookup"><span data-stu-id="7d375-224">You place this .env file in the folder where the docker-compose command is executed from.</span></span>

<span data-ttu-id="7d375-225">Aşağıdaki örnek, bir .env dosyası gibi gösterir [.env](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/.env) eShopOnContainers uygulamanın dosyası.</span><span class="sxs-lookup"><span data-stu-id="7d375-225">The following example shows an .env file like the [.env](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/.env) file for the eShopOnContainers application.</span></span>

```
# .env file

ESHOP_EXTERNAL_DNS_NAME_OR_IP=localhost

ESHOP_PROD_EXTERNAL_DNS_NAME_OR_IP=10.121.122.92
```

<span data-ttu-id="7d375-226">Docker compose'u bekliyor biçiminde bir .env dosyasındaki her satırın &lt;değişkeni&gt;=&lt;değeri&gt;.</span><span class="sxs-lookup"><span data-stu-id="7d375-226">Docker-compose expects each line in an .env file to be in the format &lt;variable&gt;=&lt;value&gt;.</span></span>

<span data-ttu-id="7d375-227">Çalışma zamanı ortamında her zaman ayarlanan değerlerle .env dosyanın içinde tanımlanan değerlerden birisini üzerine yazılacağını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="7d375-227">Note that the values set in the runtime environment always override the values defined inside the .env file.</span></span> <span data-ttu-id="7d375-228">Benzer şekilde, komut satırı komut bağımsız değişkenleri geçirilen değerleri de .env dosyasında ayarlanan varsayılan değerlerini geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="7d375-228">In a similar way, values passed via command-line command arguments also override the default values set in the .env file.</span></span>

#### <a name="additional-resources"></a><span data-ttu-id="7d375-229">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="7d375-229">Additional resources</span></span>

-   <span data-ttu-id="7d375-230">**Docker genel bakış oluşturma**
    [*https://docs.docker.com/compose/overview/*](https://docs.docker.com/compose/overview/)</span><span class="sxs-lookup"><span data-stu-id="7d375-230">**Overview of Docker Compose**
[*https://docs.docker.com/compose/overview/*](https://docs.docker.com/compose/overview/)</span></span>

-   <span data-ttu-id="7d375-231">**Birden çok oluşturma dosyaları**
    [*https://docs.docker.com/compose/extends/\#birden çok oluşturan dosyaları*](https://docs.docker.com/compose/extends/#multiple-compose-files)</span><span class="sxs-lookup"><span data-stu-id="7d375-231">**Multiple Compose files**
[*https://docs.docker.com/compose/extends/\#multiple-compose-files*](https://docs.docker.com/compose/extends/#multiple-compose-files)</span></span>

### <a name="building-optimized-aspnet-core-docker-images"></a><span data-ttu-id="7d375-232">ASP.NET Core Docker görüntüleri oluşturma en iyi duruma getirilmiş</span><span class="sxs-lookup"><span data-stu-id="7d375-232">Building optimized ASP.NET Core Docker images</span></span>

<span data-ttu-id="7d375-233">Internet üzerindeki kaynaklarında Docker ve .NET Core araştırırken, bir kapsayıcıya kaynağınız kopyalayarak Docker görüntü oluşturmanın Basitlik göstermek Dockerfiles bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7d375-233">If you are exploring Docker and .NET Core on sources on the Internet, you will find Dockerfiles that demonstrate the simplicity of building a Docker image by copying your source into a container.</span></span> <span data-ttu-id="7d375-234">Bu örnekler, basit bir yapılandırma kullanarak, Docker görüntü uygulamanızla paketlenmiş ortamıyla sağlayabilirsiniz öneririz.</span><span class="sxs-lookup"><span data-stu-id="7d375-234">These examples suggest that by using a simple configuration, you can have a Docker image with the environment packaged with your application.</span></span> <span data-ttu-id="7d375-235">Aşağıdaki örnekte basit bir Dockerfile bu damarlı gösterir.</span><span class="sxs-lookup"><span data-stu-id="7d375-235">The following example shows a simple Dockerfile in this vein.</span></span>

```
FROM microsoft/dotnet

WORKDIR /app

ENV ASPNETCORE_URLS http://+:80

EXPOSE 80

COPY . .

RUN dotnet restore

ENTRYPOINT ["dotnet", "run"]
```

<span data-ttu-id="7d375-236">Böyle bir Dockerfile çalışır.</span><span class="sxs-lookup"><span data-stu-id="7d375-236">A Dockerfile like this will work.</span></span> <span data-ttu-id="7d375-237">Ancak, özellikle üretim görüntülerinizi görüntülerinizi önemli ölçüde iyileştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7d375-237">However, you can substantially optimize your images, especially your production images.</span></span>

<span data-ttu-id="7d375-238">Kapsayıcı ve mikro modeli sürekli kapsayıcıları başlıyor.</span><span class="sxs-lookup"><span data-stu-id="7d375-238">In the container and microservices model, you are constantly starting containers.</span></span> <span data-ttu-id="7d375-239">Kapsayıcı atılabilir olduğundan kapsayıcıları kullanma normal şekilde Uyuyan bir kapsayıcı yeniden başlatmaz.</span><span class="sxs-lookup"><span data-stu-id="7d375-239">The typical way of using containers does not restart a sleeping container, because the container is disposable.</span></span> <span data-ttu-id="7d375-240">Orchestrators (örneğin, Docker Swarm, Kubernetes, DCOS veya Azure Service Fabric) yalnızca yeni örnekleri görüntülerin oluşturun.</span><span class="sxs-lookup"><span data-stu-id="7d375-240">Orchestrators (like Docker Swarm, Kubernetes, DCOS or Azure Service Fabric) simply create new instances of images.</span></span> <span data-ttu-id="7d375-241">Ne Bu örnek oluşturma işlemi daha hızlı olması için derlendikten sonra uygulamayı önceden derleme en iyi duruma getirme gerek olduğu anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="7d375-241">What this means is that you would need to optimize by precompiling the application when it is built so the instantiation process will be faster.</span></span> <span data-ttu-id="7d375-242">Kapsayıcı başlatıldığında, çalıştırılmaya hazır olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="7d375-242">When the container is started, it should be ready to run.</span></span> <span data-ttu-id="7d375-243">Olmayan geri yükleme ve çalışma zamanında derlemek, .NET Core ve Docker ilgili birçok Web günlüğü postaları gördüğünüz gibi dotnet kullanarak geri yükleme ve dotnet dotnet CLI komutları, yapı.</span><span class="sxs-lookup"><span data-stu-id="7d375-243">You should not restore and compile at run time, using dotnet restore and dotnet build commands from the dotnet CLI that, as you see in many blog posts about .NET Core and Docker.</span></span>

<span data-ttu-id="7d375-244">.NET ekibi .NET Core ve ASP.NET Core kapsayıcı özelliği iyileştirilmiş bir çerçeve sağlamak için önemli iş yapmadan.</span><span class="sxs-lookup"><span data-stu-id="7d375-244">The .NET team has been doing important work to make .NET Core and ASP.NET Core a container-optimized framework.</span></span> <span data-ttu-id="7d375-245">Yalnızca .NET Core küçük bellek kaplama alanı için bir basit çerçevesiyle algılanmadığı; Takım başlangıç performans üzerinde odaklanır ve bazı en iyi duruma getirilmiş Docker görüntüleri gibi üretilen [microsoft/aspnetcore](https://hub.docker.com/r/microsoft/aspnetcore/) görüntü adresinde [Docker hub'a](https://hub.docker.com/r/microsoft/aspnetcore/), normal kıyasla [ Microsoft/dotnet](https://hub.docker.com/r/microsoft/dotnet/) veya [microsoft/nanoserver](https://github.com/dotnet/dotnet-docker/blob/master/1.0/nanoserver/runtime/Dockerfile) görüntüler.</span><span class="sxs-lookup"><span data-stu-id="7d375-245">Not only is .NET Core a lightweight framework with a small memory footprint; the team has focused on startup performance and produced some optimized Docker images, like the [microsoft/aspnetcore](https://hub.docker.com/r/microsoft/aspnetcore/) image available at [Docker Hub](https://hub.docker.com/r/microsoft/aspnetcore/), in comparison to the regular [microsoft/dotnet](https://hub.docker.com/r/microsoft/dotnet/) or [microsoft/nanoserver](https://github.com/dotnet/dotnet-docker/blob/master/1.0/nanoserver/runtime/Dockerfile) images.</span></span> <span data-ttu-id="7d375-246">[Microsoft/aspnetcore](https://hub.docker.com/r/microsoft/aspnetcore/) görüntü sağlar aspnetcore otomatik ayarı\_80 numaralı bağlantı noktasını ve derlemeler; öncesi ngend önbelleğini URL'lere bu ayarların her ikisi de daha hızlı başlangıç sonucu.</span><span class="sxs-lookup"><span data-stu-id="7d375-246">The [microsoft/aspnetcore](https://hub.docker.com/r/microsoft/aspnetcore/) image provides automatic setting of aspnetcore\_urls to port 80 and the pre-ngend cache of assemblies; both of these settings result in faster startup.</span></span>

#### <a name="additional-resources"></a><span data-ttu-id="7d375-247">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="7d375-247">Additional resources</span></span>

-   <span data-ttu-id="7d375-248">**Yapı ASP.NET Core Docker görüntülerle en iyi duruma getirilmiş**
    [*https://blogs.msdn.microsoft.com/stevelasker/2016/09/29/building-optimized-docker-images-with-asp-net-core/*](https://blogs.msdn.microsoft.com/stevelasker/2016/09/29/building-optimized-docker-images-with-asp-net-core/)</span><span class="sxs-lookup"><span data-stu-id="7d375-248">**Building Optimized Docker Images with ASP.NET Core**
[*https://blogs.msdn.microsoft.com/stevelasker/2016/09/29/building-optimized-docker-images-with-asp-net-core/*](https://blogs.msdn.microsoft.com/stevelasker/2016/09/29/building-optimized-docker-images-with-asp-net-core/)</span></span>

### <a name="building-the-application-from-a-build-ci-container"></a><span data-ttu-id="7d375-249">Derleme (CI) kapsayıcısından uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="7d375-249">Building the application from a build (CI) container</span></span>

<span data-ttu-id="7d375-250">Bir yapı makine ya da uygulamanızı oluşturmak için VM oluşturmak gerek yoktur Şekil 8-13'te gösterildiği gibi Docker başka bir yararı önceden yapılandırılmış bir kapsayıcı uygulamanızdan oluşturabilirsiniz olur.</span><span class="sxs-lookup"><span data-stu-id="7d375-250">Another benefit of Docker is that you can build your application from a preconfigured container, as shown in Figure 8-13, so you do not need to create a build machine or VM to build your application.</span></span> <span data-ttu-id="7d375-251">Geliştirme makinenizde çalıştırarak test, yapı kapsayıcısı veya kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7d375-251">You can use or test that build container by running it at your development machine.</span></span> <span data-ttu-id="7d375-252">Ancak daha ilginç nedir CI (sürekli tümleştirme) hattınızı aynı yapı kapsayıcı kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7d375-252">But what is even more interesting is that you can use the same build container from your CI (Continuous Integration) pipeline.</span></span>

![](./media/image14.png)

<span data-ttu-id="7d375-253">**Şekil 8-13**.</span><span class="sxs-lookup"><span data-stu-id="7d375-253">**Figure 8-13**.</span></span> <span data-ttu-id="7d375-254">Docker derleme-kapsayıcısı .NET ikili dosyaları derleme</span><span class="sxs-lookup"><span data-stu-id="7d375-254">Docker build-container compiling your .NET binaries</span></span> 

<span data-ttu-id="7d375-255">Bu senaryo için size sağladığımız [aspnetcore/microsoft-yapı](https://hub.docker.com/r/microsoft/aspnetcore-build/) derlemek ve ASP.NET Core uygulamaları oluşturmak için kullanabileceğiniz görüntü.</span><span class="sxs-lookup"><span data-stu-id="7d375-255">For this scenario, we provide the [microsoft/aspnetcore-build](https://hub.docker.com/r/microsoft/aspnetcore-build/) image, which you can use to compile and build your ASP.NET Core apps.</span></span> <span data-ttu-id="7d375-256">Çıktı temel görüntü yerleştirilir [microsoft/aspnetcore](https://hub.docker.com/r/microsoft/aspnetcore/) daha önce not ettiğiniz bir en iyi duruma getirilmiş çalışma zamanı görüntü görüntü.</span><span class="sxs-lookup"><span data-stu-id="7d375-256">The output is placed in an image based on the [microsoft/aspnetcore](https://hub.docker.com/r/microsoft/aspnetcore/) image, which is an optimized runtime image, as previously noted.</span></span>

<span data-ttu-id="7d375-257">Aspnetcore derleme görüntüsünü dahil .NET Core, ASP.NET SDK'sı, npm, bir ASP.NET Core uygulama derlemek için ihtiyaç duyduğunuz her şeyi içeren Bower, Gulp, vs.</span><span class="sxs-lookup"><span data-stu-id="7d375-257">The aspnetcore-build image contains everything you need in order to compile an ASP.NET Core application, including .NET Core, the ASP.NET SDK, npm, Bower, Gulp, etc.</span></span>

<span data-ttu-id="7d375-258">Bu bağımlılıklar derleme zamanında ihtiyacımız var.</span><span class="sxs-lookup"><span data-stu-id="7d375-258">We need these dependencies at build time.</span></span> <span data-ttu-id="7d375-259">Ancak, görüntünün düşükse yapmayacağı Biz bu uygulama ile çalışma zamanında taşımak istemiyorsanız.</span><span class="sxs-lookup"><span data-stu-id="7d375-259">But we do not want to carry these with the application at runtime, because it would make the image unnecessarily large.</span></span> <span data-ttu-id="7d375-260">EShopOnContainers uygulamada uygulama oluşturabilir yalnızca çalıştırarak kapsayıcısından aşağıdaki docker-komutu oluşturun.</span><span class="sxs-lookup"><span data-stu-id="7d375-260">In the eShopOnContainers application, you can build the application from a container by just running the following docker-compose command.</span></span>

```
  docker-compose -f docker-compose.ci.build.yml up
```

<span data-ttu-id="7d375-261">Şekil 8-14 komut satırında çalıştıran bu komut gösterir.</span><span class="sxs-lookup"><span data-stu-id="7d375-261">Figure 8-14 shows this command running at the command line.</span></span>

![](./media/image15.png)

<span data-ttu-id="7d375-262">**Şekil 8-14.**</span><span class="sxs-lookup"><span data-stu-id="7d375-262">**Figure 8-14.**</span></span> <span data-ttu-id="7d375-263">.NET uygulamanızdan bir kapsayıcı oluşturma</span><span class="sxs-lookup"><span data-stu-id="7d375-263">Building your .NET application from a container</span></span>

<span data-ttu-id="7d375-264">Gördüğünüz gibi çalıştıran CI yapı kapsayıcıdır\_1 kapsayıcı.</span><span class="sxs-lookup"><span data-stu-id="7d375-264">As you can see, the container that is running is the ci-build\_1 container.</span></span> <span data-ttu-id="7d375-265">Böylece derlemek ve Bilgisayarınızdan yerine bu kapsayıcıdaki tüm uygulama içinden derleme bu aspnetcore yapı görüntüde temel alır.</span><span class="sxs-lookup"><span data-stu-id="7d375-265">This is based on the aspnetcore-build image so that it can compile and build your whole application from within that container instead of from your PC.</span></span> <span data-ttu-id="7d375-266">Diğer bir deyişle neden gerçekte olduğundan oluşturma ve Linux .NET Core projelerinde derleme — bu kapsayıcı varsayılan Docker Linux ana bilgisayarına çalıştığından.</span><span class="sxs-lookup"><span data-stu-id="7d375-266">That is why in reality it is building and compiling the .NET Core projects in Linux—because that container is running on the default Docker Linux host.</span></span>

<span data-ttu-id="7d375-267">[Docker compose.ci.build.yml](https://github.com/dotnet/eShopOnContainers/blob/master/docker-compose.ci.build.yml) için aşağıdaki kod, görüntü (eShopOnContainers parçası) içeren dosya.</span><span class="sxs-lookup"><span data-stu-id="7d375-267">The [docker-compose.ci.build.yml](https://github.com/dotnet/eShopOnContainers/blob/master/docker-compose.ci.build.yml) file for that image (part of eShopOnContainers) contains the following code.</span></span> <span data-ttu-id="7d375-268">Kullanarak bir yapı kapsayıcı başlayacağını görebilirsiniz [aspnetcore/microsoft-yapı](https://hub.docker.com/r/microsoft/aspnetcore-build/) görüntü.</span><span class="sxs-lookup"><span data-stu-id="7d375-268">You can see that it starts a build container using the [microsoft/aspnetcore-build](https://hub.docker.com/r/microsoft/aspnetcore-build/) image.</span></span>

```yml
version: '3'

services:

  ci-build:

    image: microsoft/aspnetcore-build:2.0

    volumes:
      - .:/src

    working_dir: /src

    command: /bin/bash -c "pushd ./src/Web/WebSPA && npm rebuild node-sass && popd && dotnet restore ./eShopOnContainers-ServicesAndWebApps.sln && dotnet publish ./eShopOnContainers-ServicesAndWebApps.sln -c Release -o ./obj/Docker/publish"

```

* <span data-ttu-id="7d375-269">İle başlayarak **.NET Core 2.0**, `dotnet restore` komutu yürütür otomatik olarak zaman `dotnet publish` komut yürütülürse.</span><span class="sxs-lookup"><span data-stu-id="7d375-269">Starting with **.NET Core 2.0**, `dotnet restore` command executes automatically when the `dotnet publish` command is executed.</span></span>

<span data-ttu-id="7d375-270">Yapı kapsayıcı hazır ve çalışır hale geldikten sonra .NET SDK'sı dotnet geri yükleme çalıştırır ve dotnet .NET BITS derlemek için Çözümdeki tüm projeleri karşı komutları yayımlayın.</span><span class="sxs-lookup"><span data-stu-id="7d375-270">Once the build container is up and running, it runs the .NET SDK dotnet restore and dotnet publish commands against all the projects in the solution in order to compile the .NET bits.</span></span> <span data-ttu-id="7d375-271">EShopOnContainers de TypeScript ve Angular için istemci kodu dayalı bir SPA olduğundan, eylem .NET BITS ile ilgili değildir ancak bu bu durumda, bu da npm, JavaScript bağımlılıklarla denetlemesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="7d375-271">In this case, because eShopOnContainers also has an SPA based on TypeScript and Angular for the client code, it also needs to check JavaScript dependencies with npm, but that action is not related to the .NET bits.</span></span>

<span data-ttu-id="7d375-272">Dotnet komutu derlemeleri yayımlamak ve her projenin klasörüne derlenmiş çıktısı yayımlar... Şekil 8-15'te gösterildiği gibi /obj/Docker/publish klasör.</span><span class="sxs-lookup"><span data-stu-id="7d375-272">The dotnet publish command builds and publishes the compiled output within each project’s folder to the ../obj/Docker/publish folder, as shown in Figure 8-15.</span></span>

![](./media/image16.png)

<span data-ttu-id="7d375-273">**Şekil 8-15.**</span><span class="sxs-lookup"><span data-stu-id="7d375-273">**Figure 8-15.**</span></span> <span data-ttu-id="7d375-274">Komut dotnet tarafından oluşturulan ikili dosyaları yayımlama</span><span class="sxs-lookup"><span data-stu-id="7d375-274">Binary files generated by the dotnet publish command</span></span>

#### <a name="creating-the-docker-images-from-the-cli"></a><span data-ttu-id="7d375-275">CLI üzerinden Docker görüntüleri oluşturma</span><span class="sxs-lookup"><span data-stu-id="7d375-275">Creating the Docker images from the CLI</span></span>

<span data-ttu-id="7d375-276">Uygulama çıkış (içinde her proje) ilgili klasörlere yayımlandığında, sonraki adıma gerçekten Docker görüntüleri oluşturmaktır.</span><span class="sxs-lookup"><span data-stu-id="7d375-276">Once the application output is published to the related folders (within each project), the next step is to actually build the Docker images.</span></span> <span data-ttu-id="7d375-277">Bunu yapmak için docker-compose yapı kullanın ve Şekil 8-16'da gösterildiği gibi komutları docker-oluşturun.</span><span class="sxs-lookup"><span data-stu-id="7d375-277">To do this, you use the docker-compose build and docker-compose up commands, as shown in Figure 8-16.</span></span>

![](./media/image17.png)

<span data-ttu-id="7d375-278">**Şekil 8-16.**</span><span class="sxs-lookup"><span data-stu-id="7d375-278">**Figure 8-16.**</span></span> <span data-ttu-id="7d375-279">Docker görüntülerinizi oluşturmak ve çalışan kapsayıcılar</span><span class="sxs-lookup"><span data-stu-id="7d375-279">Building Docker images and running the containers</span></span>

<span data-ttu-id="7d375-280">Şekil 8-17'de nasıl docker-compose komutu çalıştırır yapı görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7d375-280">In Figure 8-17, you can see how the docker-compose build command runs.</span></span>

![](./media/image18.png)

<span data-ttu-id="7d375-281">**Şekil 8-17**.</span><span class="sxs-lookup"><span data-stu-id="7d375-281">**Figure 8-17**.</span></span> <span data-ttu-id="7d375-282">Docker ile Docker görüntülerinizi oluşturmak-yapı komutu oluşturma</span><span class="sxs-lookup"><span data-stu-id="7d375-282">Building the Docker images with the docker-compose build command</span></span>

<span data-ttu-id="7d375-283">Docker-compose arasındaki farkı oluşturmak ve docker-oluşturmanıza komutları olan docker-oluşturan hem derlemeleri hem de başlatır görüntülerini yedekleyin.</span><span class="sxs-lookup"><span data-stu-id="7d375-283">The difference between the docker-compose build and docker-compose up commands is that docker-compose up both builds and starts the images.</span></span>

<span data-ttu-id="7d375-284">Visual Studio kullandığınızda, tüm bu adımları perde arkasında gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="7d375-284">When you use Visual Studio, all these steps are performed under the covers.</span></span> <span data-ttu-id="7d375-285">Visual Studio .NET uygulamanızı derler, Docker görüntülerini oluşturur ve kapsayıcılar Docker ana bilgisayara dağıtır.</span><span class="sxs-lookup"><span data-stu-id="7d375-285">Visual Studio compiles your .NET application, creates the Docker images, and deploys the containers into the Docker host.</span></span> <span data-ttu-id="7d375-286">Visual Studio Docker içinde doğrudan Visual Studio'dan çalıştırma kapsayıcılarınızı hata ayıklama özelliği gibi ek özellikler sunar.</span><span class="sxs-lookup"><span data-stu-id="7d375-286">Visual Studio offers additional features, like the ability to debug your containers running in Docker, directly from Visual Studio.</span></span>

<span data-ttu-id="7d375-287">Burada genel takeway aynı şekilde CI/CD hattınızı yapı, uygulamanızı mümkün olan — bir yerel makine yerine bir kapsayıcısından.</span><span class="sxs-lookup"><span data-stu-id="7d375-287">The overall takeway here is that you are able to build your application the same way your CI/CD pipeline should build it—from a container instead of from a local machine.</span></span> <span data-ttu-id="7d375-288">Oluşturulan görüntüler sahip sonra sonra Docker görüntüleri docker kullanarak çalıştırmak yeterlidir-komutu oluşturun.</span><span class="sxs-lookup"><span data-stu-id="7d375-288">After having the images created, then you just need to run the Docker images using the docker-compose up command.</span></span>

#### <a name="additional-resources"></a><span data-ttu-id="7d375-289">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="7d375-289">Additional resources</span></span>

-   <span data-ttu-id="7d375-290">**Bir kapsayıcı bitten oluşturma: bir Windows CLI ortamında (dotnet CLI, Docker CLI ve VS Code) eShopOnContainers çözümü kurma**
    [*https://github.com/dotnet/eShopOnContainers/wiki/03.-Setting-the-eShopOnContainers-solution-up-in-a-Windows-CLI-environment-(dotnet-CLI, - Docker - CLI- ve -VS-kodu)*](https://github.com/dotnet/eShopOnContainers/wiki/03.-Setting-the-eShopOnContainers-solution-up-in-a-Windows-CLI-environment-(dotnet-CLI,-Docker-CLI-and-VS-Code))</span><span class="sxs-lookup"><span data-stu-id="7d375-290">**Building bits from a container: Setting the eShopOnContainers solution up in a Windows CLI environment (dotnet CLI, Docker CLI and VS Code)**
[*https://github.com/dotnet/eShopOnContainers/wiki/03.-Setting-the-eShopOnContainers-solution-up-in-a-Windows-CLI-environment-(dotnet-CLI,-Docker-CLI-and-VS-Code)*](https://github.com/dotnet/eShopOnContainers/wiki/03.-Setting-the-eShopOnContainers-solution-up-in-a-Windows-CLI-environment-(dotnet-CLI,-Docker-CLI-and-VS-Code))</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="7d375-291">[Önceki] (veri-güdümlü-crud-microservice.md) [sonraki] (veritabanı sunucu container.md)</span><span class="sxs-lookup"><span data-stu-id="7d375-291">[Previous] (data-driven-crud-microservice.md) [Next] (database-server-container.md)</span></span>
