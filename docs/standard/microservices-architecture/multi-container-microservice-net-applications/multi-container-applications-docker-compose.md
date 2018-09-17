---
title: Docker-compose.yml ile çok Kapsayıcılı uygulamanızı tanımlama
description: Kapsayıcılı .NET uygulamaları için .NET mikro hizmet mimarisi | Docker-compose.yml ile çok Kapsayıcılı uygulamanızı tanımlama
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/30/2017
ms.openlocfilehash: d1c4166129716ccbbc86855e38d631f493b82290
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45750264"
---
# <a name="defining-your-multi-container-application-with-docker-composeyml"></a><span data-ttu-id="7eaaa-103">Docker-compose.yml ile çok Kapsayıcılı uygulamanızı tanımlama</span><span class="sxs-lookup"><span data-stu-id="7eaaa-103">Defining your multi-container application with docker-compose.yml</span></span> 

<span data-ttu-id="7eaaa-104">Bu kılavuzdaki [docker-compose.yml](https://docs.docker.com/compose/compose-file/) dosya bölümünde tanıtılmıştır [4. adım. Çok kapsayıcılı Docker uygulaması oluştururken, hizmetlerinizi docker-compose.yml tanımlamak](#step4_define_svcs_in_docker_compose_yml).</span><span class="sxs-lookup"><span data-stu-id="7eaaa-104">In this guide, the [docker-compose.yml](https://docs.docker.com/compose/compose-file/) file was introduced in the section [Step 4. Define your services in docker-compose.yml when building a multi-container Docker application](#step4_define_svcs_in_docker_compose_yml).</span></span> <span data-ttu-id="7eaaa-105">Ancak, daha ayrıntılı olarak incelenmesi yararlı olan docker-compose dosyaları kullanmak için ek yolu vardır.</span><span class="sxs-lookup"><span data-stu-id="7eaaa-105">However, there are additional ways to use the docker-compose files that are worth exploring in further detail.</span></span>

<span data-ttu-id="7eaaa-106">Örneğin, docker-compose.yml dosyası çok Kapsayıcılı uygulamanızı dağıtmak istediğiniz nasıl açıkça tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7eaaa-106">For example, you can explicitly describe how you want to deploy your multi-container application in the docker-compose.yml file.</span></span> <span data-ttu-id="7eaaa-107">İsteğe bağlı olarak, özel Docker görüntülerinizi oluşturmak için nasıl yükleyeceksiniz tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7eaaa-107">Optionally, you can also describe how you are going to build your custom Docker images.</span></span> <span data-ttu-id="7eaaa-108">(Özel Docker görüntüleri ile Docker CLI'yı da oluşturulabilir.)</span><span class="sxs-lookup"><span data-stu-id="7eaaa-108">(Custom Docker images can also be built with the Docker CLI.)</span></span>

<span data-ttu-id="7eaaa-109">Temel olarak, her kapsayıcıları dağıtmak istediğiniz ek olarak her kapsayıcı dağıtımı için belirli özellikleri tanımlar.</span><span class="sxs-lookup"><span data-stu-id="7eaaa-109">Basically, you define each of the containers you want to deploy plus certain characteristics for each container deployment.</span></span> <span data-ttu-id="7eaaa-110">Bir çoklu kapsayıcı dağıtım açıklama dosyası oluşturduktan sonra tek bir eylem tarafından düzenlenen tüm çözüm dağıtabileceğiniz [docker compose up](https://docs.docker.com/compose/overview/) CLI komutunu veya dağıtabilir, saydam Visual Studio'dan.</span><span class="sxs-lookup"><span data-stu-id="7eaaa-110">Once you have a multi-container deployment description file, you can deploy the whole solution in a single action orchestrated by the [docker-compose up](https://docs.docker.com/compose/overview/) CLI command, or you can deploy it transparently from Visual Studio.</span></span> <span data-ttu-id="7eaaa-111">Aksi takdirde, komutu komut satırından çalıştırın docker'ı kullanarak kapsayıcı tarafından kapsayıcı birden çok adımda dağıtmak için Docker CLI'yı kullanmak gerekir.</span><span class="sxs-lookup"><span data-stu-id="7eaaa-111">Otherwise, you would need to use the Docker CLI to deploy container-by-container in multiple steps by using the docker run command from the command line.</span></span> <span data-ttu-id="7eaaa-112">Bu nedenle, docker-compose.yml tanımlanan her bir hizmet tam olarak bir resim belirtin veya bu yapı gerekir.</span><span class="sxs-lookup"><span data-stu-id="7eaaa-112">Therefore, each service defined in docker-compose.yml must specify exactly one image or build.</span></span> <span data-ttu-id="7eaaa-113">Diğer anahtarlar isteğe bağlıdır ve kendi docker komut satırı ortaklarınıza çalıştırmak için benzer.</span><span class="sxs-lookup"><span data-stu-id="7eaaa-113">Other keys are optional, and are analogous to their docker run command-line counterparts.</span></span>

<span data-ttu-id="7eaaa-114">Aşağıdaki YAML koduna hizmetine örneği için bir olası genel ancak tek docker-compose.yml dosyası tanımıdır.</span><span class="sxs-lookup"><span data-stu-id="7eaaa-114">The following YAML code is the definition of a possible global but single docker-compose.yml file for the eShopOnContainers sample.</span></span> <span data-ttu-id="7eaaa-115">Bu gerçek docker-compose dosyasından hizmetine değildir.</span><span class="sxs-lookup"><span data-stu-id="7eaaa-115">This is not the actual docker-compose file from eShopOnContainers.</span></span> <span data-ttu-id="7eaaa-116">Bunun yerine, tek bir dosyada en iyi değil, bir basit ve birleştirilmiş sürüm olduğu şekilde çalışmak için docker compose dosyaları, daha sonra açıklanacaktır gibi.</span><span class="sxs-lookup"><span data-stu-id="7eaaa-116">Instead, it is a simplified and consolidated version in a single file, which is not the best way to work with docker-compose files, as will be explained later.</span></span>

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

<span data-ttu-id="7eaaa-117">Hizmetler bu dosyadaki kök anahtardır.</span><span class="sxs-lookup"><span data-stu-id="7eaaa-117">The root key in this file is services.</span></span> <span data-ttu-id="7eaaa-118">Bu anahtarın altında dağıtmak ve yürüttüğünüzde çalıştırmak istediğiniz hizmetleri tanımlamakta docker compose up komutu ya da bu docker-compose.yml dosyasını kullanarak Visual Studio'dan dağıtırken.</span><span class="sxs-lookup"><span data-stu-id="7eaaa-118">Under that key you define the services you want to deploy and run when you execute the docker-compose up command or when you deploy from Visual Studio by using this docker-compose.yml file.</span></span> <span data-ttu-id="7eaaa-119">Bu durumda, docker-compose.yml dosyası aşağıdaki listede açıklandığı gibi tanımlı, birden çok hizmet yok.</span><span class="sxs-lookup"><span data-stu-id="7eaaa-119">In this case, the docker-compose.yml file has multiple services defined, as described in the following list.</span></span>

-   <span data-ttu-id="7eaaa-120">Sunucu tarafı c mikro hizmetler kullanan ASP.NET Core MVC uygulaması da dahil olmak üzere kapsayıcı webmvc\#</span><span class="sxs-lookup"><span data-stu-id="7eaaa-120">webmvc Container including the ASP.NET Core MVC application consuming the microservices from server-side C\#</span></span>

-   <span data-ttu-id="7eaaa-121">catalog.api Kataloğu ASP.NET Core Web API'si mikro hizmet de dahil olmak üzere kapsayıcı</span><span class="sxs-lookup"><span data-stu-id="7eaaa-121">catalog.api Container including the Catalog ASP.NET Core Web API microservice</span></span>

-   <span data-ttu-id="7eaaa-122">ASP.NET Core Web API'si sıralama mikro hizmet de dahil olmak üzere kapsayıcı ordering.api</span><span class="sxs-lookup"><span data-stu-id="7eaaa-122">ordering.api Container including the Ordering ASP.NET Core Web API microservice</span></span>

-   <span data-ttu-id="7eaaa-123">Linux için mikro hizmetler veritabanlarını barındıran SQL Server çalıştıran kapsayıcı SQL.Data</span><span class="sxs-lookup"><span data-stu-id="7eaaa-123">sql.data Container running SQL Server for Linux, holding the microservices databases</span></span>

-   <span data-ttu-id="7eaaa-124">Sepet ASP.NET Core Web API'si mikro hizmet ile kapsayıcı Basket.api</span><span class="sxs-lookup"><span data-stu-id="7eaaa-124">basket.api Container with the Basket ASP.NET Core Web API microservice</span></span>

-   <span data-ttu-id="7eaaa-125">Basket.Data sepet veritabanıyla bir REDIS önbelleği olarak REDIS cache hizmeti çalıştıran kapsayıcısı</span><span class="sxs-lookup"><span data-stu-id="7eaaa-125">basket.data Container running the REDIS cache service, with the basket database as a REDIS cache</span></span>

### <a name="a-simple-web-service-api-container"></a><span data-ttu-id="7eaaa-126">Basit bir Web hizmeti API'si kapsayıcı</span><span class="sxs-lookup"><span data-stu-id="7eaaa-126">A simple Web Service API container</span></span>

<span data-ttu-id="7eaaa-127">Tek bir kapsayıcı'na Odaklanıldığında, basit bir tanımı catalog.api container-mikro hizmet vardır:</span><span class="sxs-lookup"><span data-stu-id="7eaaa-127">Focusing on a single container, the catalog.api container-microservice has a straightforward definition:</span></span>

```yml
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
```

<span data-ttu-id="7eaaa-128">Bu kapsayıcı hizmeti, temel yapılandırması aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="7eaaa-128">This containerized service has the following basic configuration:</span></span>

-   <span data-ttu-id="7eaaa-129">Bu özel eshop/catalog.api görüntüye bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="7eaaa-129">It is based on the custom eshop/catalog.api image.</span></span> <span data-ttu-id="7eaaa-130">Basitlik'ın çok için hiçbir derleme yok: anahtar dosyasında ayarı.</span><span class="sxs-lookup"><span data-stu-id="7eaaa-130">For simplicity’s sake, there is no build: key setting in the file.</span></span> <span data-ttu-id="7eaaa-131">Bu görüntü daha önce (docker derleme ile) oluşturulmuş gerekir veya herhangi bir Docker kayıt defterinden (docker pull komutuyla) indirilip anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="7eaaa-131">This means that the image must have been previously built (with docker build) or have been downloaded (with the docker pull command) from any Docker registry.</span></span>

-   <span data-ttu-id="7eaaa-132">ConnectionString Kataloğu veri modeli içeren SQL Server örneğine erişmesi için Entity Framework tarafından kullanılacak bağlantı dizesiyle adlı bir ortam değişkeni tanımlar.</span><span class="sxs-lookup"><span data-stu-id="7eaaa-132">It defines an environment variable named ConnectionString with the connection string to be used by Entity Framework to access the SQL Server instance that contains the catalog data model.</span></span> <span data-ttu-id="7eaaa-133">Bu durumda, aynı SQL Server kapsayıcı birden çok veritabanı tutuyor.</span><span class="sxs-lookup"><span data-stu-id="7eaaa-133">In this case, the same SQL Server container is holding multiple databases.</span></span> <span data-ttu-id="7eaaa-134">Bu nedenle, daha az bellek için Docker geliştirme makinenizde gerekir.</span><span class="sxs-lookup"><span data-stu-id="7eaaa-134">Therefore, you need less memory in your development machine for Docker.</span></span> <span data-ttu-id="7eaaa-135">Ancak, her bir mikro hizmet veritabanı için bir SQL Server kapsayıcı dağıtabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7eaaa-135">However, you could also deploy one SQL Server container for each microservice database.</span></span>

-   <span data-ttu-id="7eaaa-136">SQL Server sql.data, Linux için SQL Server örneğini çalıştıran kapsayıcısı için kullanılan aynı adı olan addır.</span><span class="sxs-lookup"><span data-stu-id="7eaaa-136">The SQL Server name is sql.data, which is the same name used for the container that is running the SQL Server instance for Linux.</span></span> <span data-ttu-id="7eaaa-137">Bu kullanışlıdır; Bu ad çözümlemesi (Docker konağı dahili) kullanabilmek için ağ adresi çözer, bu diğer kapsayıcılardan eriştiğiniz kapsayıcılar için iç IP bilmek zorunda kalmazsınız.</span><span class="sxs-lookup"><span data-stu-id="7eaaa-137">This is convenient; being able to use this name resolution (internal to the Docker host) will resolve the network address so you don’t need to know the internal IP for the containers you are accessing from other containers.</span></span>

<span data-ttu-id="7eaaa-138">Bağlantı dizesi bir ortam değişkeni tarafından tanımlı olduğundan, farklı bir mekanizma aracılığıyla ve farklı bir zamanda bu değişkeni ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7eaaa-138">Because the connection string is defined by an environment variable, you could set that variable through a different mechanism and at a different time.</span></span> <span data-ttu-id="7eaaa-139">Örneğin, son konaklar veya CI/CD işlem hatlarınızı Azure DevOps Hizmetleri veya tercih edilen DevOps sisteminizi gelen yapmakta üretime dağıtırken farklı bağlantı dizesi ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7eaaa-139">For example, you could set a different connection string when deploying to production in the final hosts, or by doing it from your CI/CD pipelines in Azure DevOps Services or your preferred DevOps system.</span></span>

-   <span data-ttu-id="7eaaa-140">Bu, Docker konağının catalog.api hizmetinde iç erişimi için 80 numaralı bağlantı noktasını kullanıma sunar.</span><span class="sxs-lookup"><span data-stu-id="7eaaa-140">It exposes port 80 for internal access to the catalog.api service within the Docker host.</span></span> <span data-ttu-id="7eaaa-141">Konak şu anda bir Linux VM Linux için Docker görüntü temel alan, ancak bunun yerine bir Windows görüntüsü üzerinde çalıştırmak için kapsayıcı yapılandırabilirsiniz olmasıdır.</span><span class="sxs-lookup"><span data-stu-id="7eaaa-141">The host is currently a Linux VM because it is based on a Docker image for Linux, but you could configure the container to run on a Windows image instead.</span></span>

-   <span data-ttu-id="7eaaa-142">Bu, kullanıma sunulan bağlantı noktası (Linux VM) Docker konak makinedeki 5101 numaralı bağlantı noktasına kapsayıcı üzerindeki 80 iletir.</span><span class="sxs-lookup"><span data-stu-id="7eaaa-142">It forwards the exposed port 80 on the container to port 5101 on the Docker host machine (the Linux VM).</span></span>

-   <span data-ttu-id="7eaaa-143">Web hizmeti sql.data hizmet (SQL Server örneği için bir kapsayıcı içinde çalışan Linux veritabanı) bağlar.</span><span class="sxs-lookup"><span data-stu-id="7eaaa-143">It links the web service to the sql.data service (the SQL Server instance for Linux database running in a container).</span></span> <span data-ttu-id="7eaaa-144">Bu bağımlılık belirttiğinizde, sql.data kapsayıcı zaten başlamış catalog.api kapsayıcı tamamlanıncaya kadar çalışmaz; Bu ilk catalog.api SQL Server veritabanına sahip gerektiğinden önemli ve çalışır durumdadır.</span><span class="sxs-lookup"><span data-stu-id="7eaaa-144">When you specify this dependency, the catalog.api container will not start until the sql.data container has already started; this is important because catalog.api needs to have the SQL Server database up and running first.</span></span> <span data-ttu-id="7eaaa-145">Docker kapsayıcı düzeyinde iade ettiğinden ancak, bu tür bir kapsayıcı bağımlılık çoğu durumda, yeterli değildir.</span><span class="sxs-lookup"><span data-stu-id="7eaaa-145">However, this kind of container dependency is not enough in many cases, because Docker checks only at the container level.</span></span> <span data-ttu-id="7eaaa-146">Üstel geri alma ile yeniden deneme mantığı, istemci mikro Hizmetleri uygulamak için önerilir, bu nedenle bazen hizmeti (büyük/küçük harf bu SQL Server) hala hazır olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="7eaaa-146">Sometimes the service (in this case SQL Server) might still not be ready, so it is advisable to implement retry logic with exponential backoff in your client microservices.</span></span> <span data-ttu-id="7eaaa-147">Bu şekilde, bir bağımlılık kapsayıcı kısa bir süre için hazır değilse, uygulama hala dayanıklı olacak.</span><span class="sxs-lookup"><span data-stu-id="7eaaa-147">That way, if a dependency container is not ready for a short time, the application will still be resilient.</span></span>

-   <span data-ttu-id="7eaaa-148">Dış sunucuları erişmesine izin vermek için yapılandırılmış: ek\_konakları ayarlama dış sunucuların ya da Docker konağı dışında makineleri erişmenizi sağlar (diğer bir deyişle, varsayılan bir Docker geliştirme olan bir Linux VM dışında barındırma) gibi bir yerel SQL Sunucu örneği geliştirme koruyun.</span><span class="sxs-lookup"><span data-stu-id="7eaaa-148">It is configured to allow access to external servers: the extra\_hosts setting allows you to access external servers or machines outside of the Docker host (that is, outside the default Linux VM which is a development Docker host), such as a local SQL Server instance on your development PC.</span></span>

<span data-ttu-id="7eaaa-149">Aşağıdaki bölümlerde ele alınacaktır diğer, daha gelişmiş bir docker-compose.yml ayarları vardır.</span><span class="sxs-lookup"><span data-stu-id="7eaaa-149">There are also other, more advanced docker-compose.yml settings that we will discuss in the following sections.</span></span>

### <a name="using-docker-compose-files-to-target-multiple-environments"></a><span data-ttu-id="7eaaa-150">Kullanarak docker-compose dosyaları, birden çok ortama hedeflemek için</span><span class="sxs-lookup"><span data-stu-id="7eaaa-150">Using docker-compose files to target multiple environments</span></span>

<span data-ttu-id="7eaaa-151">Docker-compose.yml dosyaları tanımı dosyaları ve söz konusu biçimini birden çok altyapıları tarafından kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="7eaaa-151">The docker-compose.yml files are definition files and can be used by multiple infrastructures that understand that format.</span></span> <span data-ttu-id="7eaaa-152">En basit araçtır docker-compose komutu, ancak Düzenleyicileri (örneğin, Docker Swarm) Bu dosya ayrıca anlama gibi diğer araçları.</span><span class="sxs-lookup"><span data-stu-id="7eaaa-152">The most straightforward tool is the docker-compose command, but other tools like orchestrators (for example, Docker Swarm) also understand that file.</span></span>

<span data-ttu-id="7eaaa-153">Kullanarak bu nedenle, docker compose komutuyla aşağıdaki ana senaryoları hedefleyebilir.</span><span class="sxs-lookup"><span data-stu-id="7eaaa-153">Therefore, by using the docker-compose command you can target the following main scenarios.</span></span>

#### <a name="development-environments"></a><span data-ttu-id="7eaaa-154">Geliştirme ortamları</span><span class="sxs-lookup"><span data-stu-id="7eaaa-154">Development environments</span></span>

<span data-ttu-id="7eaaa-155">Uygulama geliştirirken, yalıtılmış bir geliştirme ortamında bir uygulamayı çalıştırmak önemlidir.</span><span class="sxs-lookup"><span data-stu-id="7eaaa-155">When you develop applications, it is important to be able to run an application in an isolated development environment.</span></span> <span data-ttu-id="7eaaa-156">Kullanabileceğiniz docker-compose, ortam veya kullandığı docker perde compose Visual Studio kullanmak için CLI komutu.</span><span class="sxs-lookup"><span data-stu-id="7eaaa-156">You can use the docker-compose CLI command to create that environment or use Visual Studio which uses docker-compose under the covers.</span></span>

<span data-ttu-id="7eaaa-157">Docker-compose.yml dosyasını yapılandırın ve hizmeti tüm uygulama bağımlılıklarınızın (diğer hizmetleri, önbellek, veritabanları, kuyruklar, vb.) belge sağlar.</span><span class="sxs-lookup"><span data-stu-id="7eaaa-157">The docker-compose.yml file allows you to configure and document all your application’s service dependencies (other services, cache, databases, queues, etc.).</span></span> <span data-ttu-id="7eaaa-158">Kullanarak CLI komut docker-compose, oluşturabilir ve her bir bağımlılığın için bir veya daha fazla kapsayıcıları tek bir komutla Başlat (docker compose up).</span><span class="sxs-lookup"><span data-stu-id="7eaaa-158">Using the docker-compose CLI command, you can create and start one or more containers for each dependency with a single command (docker-compose up).</span></span>

<span data-ttu-id="7eaaa-159">Docker-compose.yml dosyaları Docker altyapısı tarafından yorumlanan yapılandırma dosyalarını ancak uygun belge dosyaları çok kapsayıcılı bir uygulama, oluşumunu hakkında da görür.</span><span class="sxs-lookup"><span data-stu-id="7eaaa-159">The docker-compose.yml files are configuration files interpreted by Docker engine but also serve as convenient documentation files about the composition of your multi-container application.</span></span>

#### <a name="testing-environments"></a><span data-ttu-id="7eaaa-160">Test ortamları</span><span class="sxs-lookup"><span data-stu-id="7eaaa-160">Testing environments</span></span>

<span data-ttu-id="7eaaa-161">Herhangi bir sürekli dağıtım (CD) veya sürekli tümleştirme (CI) işlem önemli bir parçası olan birim testleri ve tümleştirme testleri.</span><span class="sxs-lookup"><span data-stu-id="7eaaa-161">An important part of any continuous deployment (CD) or continuous integration (CI) process are the unit tests and integration tests.</span></span> <span data-ttu-id="7eaaa-162">Bu otomatik testleri yalıtılmış bir ortam gerektirdiğinden, kullanıcılar ya da herhangi bir değişiklik uygulamanın veri etkilenmez.</span><span class="sxs-lookup"><span data-stu-id="7eaaa-162">These automated tests require an isolated environment so they are not impacted by the users or any other change in the application’s data.</span></span>

<span data-ttu-id="7eaaa-163">Docker Compose ile oluşturabilir ve bu yalıtılmış bir ortamda çok bir kolayca komut istemi veya komut dosyaları, aşağıdaki komutları gibi birkaç komut yok:</span><span class="sxs-lookup"><span data-stu-id="7eaaa-163">With Docker Compose you can create and destroy that isolated environment very easily in a few commands from your command prompt or scripts, like the following commands:</span></span>

```
docker-compose up -d
./run_unit_tests
docker-compose down
```

#### <a name="production-deployments"></a><span data-ttu-id="7eaaa-164">Üretim dağıtımları</span><span class="sxs-lookup"><span data-stu-id="7eaaa-164">Production deployments</span></span>

<span data-ttu-id="7eaaa-165">Oluştur, uzak bir Docker altyapısı dağıtmak için de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7eaaa-165">You can also use Compose to deploy to a remote Docker Engine.</span></span> <span data-ttu-id="7eaaa-166">Tipik bir durumda, tek bir Docker konağı örneği dağıtmaktır (üretim VM veya sunucu ile sağlanan gibi [Docker Machine](https://docs.docker.com/machine/overview/)).</span><span class="sxs-lookup"><span data-stu-id="7eaaa-166">A typical case is to deploy to a single Docker host instance (like a production VM or server provisioned with [Docker Machine](https://docs.docker.com/machine/overview/)).</span></span> <span data-ttu-id="7eaaa-167">Ancak tüm olabilir [Docker Swarm](https://docs.docker.com/swarm/overview/) kümeleri ayrıca docker-compose.yml dosyaları ile uyumlu olmadığından, küme.</span><span class="sxs-lookup"><span data-stu-id="7eaaa-167">But it could also be an entire [Docker Swarm](https://docs.docker.com/swarm/overview/) cluster, because clusters are also compatible with the docker-compose.yml files.</span></span>

<span data-ttu-id="7eaaa-168">Herhangi diğer orchestrator (Azure Service Fabric, Mesos DC/OS, Kubernetes, vb.) kullanıyorsanız, bu docker-compose.yml, ancak diğer orchestrator tarafından gereken biçimde gibi Kurulum ve meta verileri yapılandırma ayarlarını eklemek gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="7eaaa-168">If you are using any other orchestrator (Azure Service Fabric, Mesos DC/OS, Kubernetes, etc.), you might need to add setup and metadata configuration settings like those in docker-compose.yml, but in the format required by the other orchestrator.</span></span>

<span data-ttu-id="7eaaa-169">Her iki durumda da docker-compose geliştirme, test ve üretim iş akışları için kullanışlı bir aracı ve meta veri biçimi, üretim iş akışı, kullanmakta olduğunuz orchestrator üzerinde farklılık gösterebilir ancak.</span><span class="sxs-lookup"><span data-stu-id="7eaaa-169">In any case, docker-compose is a convenient tool and metadata format for development, testing and production workflows, although the production workflow might vary on the orchestrator you are using.</span></span>

### <a name="using-multiple-docker-compose-files-to-handle-several-environments"></a><span data-ttu-id="7eaaa-170">Birden fazla docker-compose birkaç ortamlarını işleyecek şekilde dosyaları</span><span class="sxs-lookup"><span data-stu-id="7eaaa-170">Using multiple docker-compose files to handle several environments</span></span>

<span data-ttu-id="7eaaa-171">Farklı ortamlar hedeflenirken birden çok kullanması gereken compose dosyası.</span><span class="sxs-lookup"><span data-stu-id="7eaaa-171">When targeting different environments, you should use multiple compose files.</span></span> <span data-ttu-id="7eaaa-172">Bu ortama bağlı olarak birden çok yapılandırma çeşitleri oluşturmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="7eaaa-172">This lets you create multiple configuration variants depending on the environment.</span></span>

#### <a name="overriding-the-base-docker-compose-file"></a><span data-ttu-id="7eaaa-173">Temel docker-compose dosyası geçersiz kılma</span><span class="sxs-lookup"><span data-stu-id="7eaaa-173">Overriding the base docker-compose file</span></span>

<span data-ttu-id="7eaaa-174">Önceki bölümlerde gösterildiği Basitleştirilmiş örneklerde gösterildiği gibi bir tek docker-compose.yml dosyası kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7eaaa-174">You could use a single docker-compose.yml file as in the simplified examples shown in previous sections.</span></span> <span data-ttu-id="7eaaa-175">Bununla birlikte, çoğu uygulama için önerilmez.</span><span class="sxs-lookup"><span data-stu-id="7eaaa-175">However, that is not recommended for most applications.</span></span>

<span data-ttu-id="7eaaa-176">Varsayılan olarak, iki dosya, docker-compose.yml ve docker-compose.override.yml isteğe bağlı dosya oluşturma okur.</span><span class="sxs-lookup"><span data-stu-id="7eaaa-176">By default, Compose reads two files, a docker-compose.yml and an optional docker-compose.override.yml file.</span></span> <span data-ttu-id="7eaaa-177">Şekil 8-11'de gösterildiği gibi ne zaman, Visual Studio kullanarak ve Docker desteği, Visual Studio ayrıca etkinleştirme, CI/CD işlem hatlarınızı gibi Azure DevOps hizmetlerinde kullanmak için bir ek docker compose.ci.build,yml dosyası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="7eaaa-177">As shown in Figure 8-11, when you are using Visual Studio and enabling Docker support, Visual Studio also creates an additional docker-compose.ci.build,yml file for you to use from your CI/CD pipelines like in Azure DevOps Services.</span></span>

![](./media/image12.png)

<span data-ttu-id="7eaaa-178">**Şekil 8-11**.</span><span class="sxs-lookup"><span data-stu-id="7eaaa-178">**Figure 8-11**.</span></span> <span data-ttu-id="7eaaa-179">docker-compose dosyası Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="7eaaa-179">docker-compose files in Visual Studio 2017</span></span>

<span data-ttu-id="7eaaa-180">Visual Studio Code veya Sublime, gibi herhangi bir düzenleyici ile docker-compose dosyaları düzenleyin ve uygulamayı çalıştırın docker-compose up komutu.</span><span class="sxs-lookup"><span data-stu-id="7eaaa-180">You can edit the docker-compose files with any editor, like Visual Studio Code or Sublime, and run the application with the docker-compose up command.</span></span>

<span data-ttu-id="7eaaa-181">Kural gereği, docker-compose.yml dosyasını temel yapılandırma ve diğer statik ayarlarını içerir.</span><span class="sxs-lookup"><span data-stu-id="7eaaa-181">By convention, the docker-compose.yml file contains your base configuration and other static settings.</span></span> <span data-ttu-id="7eaaa-182">Hizmet yapılandırması, hedeflediğiniz dağıtım ortamı bağlı olarak değiştirmemelisiniz anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="7eaaa-182">That means that the service configuration should not change depending on the deployment environment you are targeting.</span></span>

<span data-ttu-id="7eaaa-183">Adından da anlaşılacağı gibi docker-compose.override.yml dosyası, dağıtım ortamınıza bağlıdır yapılandırma gibi temel yapılandırma geçersiz yapılandırma ayarlarını içerir.</span><span class="sxs-lookup"><span data-stu-id="7eaaa-183">The docker-compose.override.yml file, as its name suggests, contains configuration settings that override the base configuration, such as configuration that depends on the deployment environment.</span></span> <span data-ttu-id="7eaaa-184">Ayrıca, farklı adlara sahip birden fazla geçersiz kılma dosyası olabilir.</span><span class="sxs-lookup"><span data-stu-id="7eaaa-184">You can have multiple override files with different names also.</span></span> <span data-ttu-id="7eaaa-185">Geçersiz kılma dosyalar genellikle uygulama ancak belirli bir ortam veya bir dağıtım için gerekli ek bilgileri içerir.</span><span class="sxs-lookup"><span data-stu-id="7eaaa-185">The override files usually contain additional information needed by the application but specific to an environment or to a deployment.</span></span>

#### <a name="targeting-multiple-environments"></a><span data-ttu-id="7eaaa-186">Birden çok ortama hedefleme</span><span class="sxs-lookup"><span data-stu-id="7eaaa-186">Targeting multiple environments</span></span>

<span data-ttu-id="7eaaa-187">Tipik bir kullanım örneği olan birden çok tanımlarken compose dosyaları, üretim gibi birden çok ortamı hazırlama, CI veya geliştirme hedefleyebilir.</span><span class="sxs-lookup"><span data-stu-id="7eaaa-187">A typical use case is when you define multiple compose files so you can target multiple environments, like production, staging, CI, or development.</span></span> <span data-ttu-id="7eaaa-188">Bu farklar desteklemek için Şekil 8-12'de gösterildiği gibi birden çok dosyalarına oluşturma yapılandırmanızı bölebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7eaaa-188">To support these differences, you can split your Compose configuration into multiple files, as shown in Figure 8-12.</span></span>

![](./media/image13.png)

<span data-ttu-id="7eaaa-189">**Şekil 8-12**.</span><span class="sxs-lookup"><span data-stu-id="7eaaa-189">**Figure 8-12**.</span></span> <span data-ttu-id="7eaaa-190">Geçersiz kılma değerleri temel docker-compose.yml dosyasındaki dosyaları birden çok docker-compose</span><span class="sxs-lookup"><span data-stu-id="7eaaa-190">Multiple docker-compose files overriding values in the base docker-compose.yml file</span></span>

<span data-ttu-id="7eaaa-191">Temel docker-compose.yml dosyası ile başlayın.</span><span class="sxs-lookup"><span data-stu-id="7eaaa-191">You start with the base docker-compose.yml file.</span></span> <span data-ttu-id="7eaaa-192">Bu temel dosya ortamına bağlı olarak değiştirmeyin temel ya da statik yapılandırma ayarlarını içeren gerekir.</span><span class="sxs-lookup"><span data-stu-id="7eaaa-192">This base file has to contain the base or static configuration settings that do not change depending on the environment.</span></span> <span data-ttu-id="7eaaa-193">Örneğin, hizmetine taban dosyası olarak aşağıdaki docker-compose.yml dosyası vardır.</span><span class="sxs-lookup"><span data-stu-id="7eaaa-193">For example, the eShopOnContainers has the following docker-compose.yml file as the base file.</span></span>

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

<span data-ttu-id="7eaaa-194">Temel docker-compose.yml dosyasındaki değerleri nedeniyle farklı bir hedef dağıtım ortamlarının değiştirmemesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="7eaaa-194">The values in the base docker-compose.yml file should not change because of different target deployment environments.</span></span>

<span data-ttu-id="7eaaa-195">Örneğin, webmvc hizmet tanımı üzerinde odaklanmak, nasıl bu bilgileri çok hedefleyen hangi ortamı ne olursa olsun aynıdır görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7eaaa-195">If you focus on the webmvc service definition, for instance, you can see how that information is much the same no matter what environment you might be targeting.</span></span> <span data-ttu-id="7eaaa-196">Aşağıdaki bilgileri vardır:</span><span class="sxs-lookup"><span data-stu-id="7eaaa-196">You have the following information:</span></span>

-   <span data-ttu-id="7eaaa-197">Hizmet adı: webmvc.</span><span class="sxs-lookup"><span data-stu-id="7eaaa-197">The service name: webmvc.</span></span>

-   <span data-ttu-id="7eaaa-198">Kapsayıcının özel görüntü: Elektronik Mağaza/webmvc.</span><span class="sxs-lookup"><span data-stu-id="7eaaa-198">The container’s custom image: eshop/webmvc.</span></span>

-   <span data-ttu-id="7eaaa-199">Kullanmak için hangi Dockerfile belirten özel Docker görüntüsü oluşturmak için komutu.</span><span class="sxs-lookup"><span data-stu-id="7eaaa-199">The command to build the custom Docker image, indicating which Dockerfile to use.</span></span>

-   <span data-ttu-id="7eaaa-200">Bağımlılıkları diğer hizmetleri, bir bağımlılık kapsayıcıları başlatılıncaya kadar bu kapsayıcı başlamaz.</span><span class="sxs-lookup"><span data-stu-id="7eaaa-200">Dependencies on other services, so this container does not start until the other dependency containers have started.</span></span>

<span data-ttu-id="7eaaa-201">Ek yapılandırma olabilir, ancak önemli temel docker-compose.yml dosyasında, yalnızca ortamlar arasında ortak olan bilgiyi ayarlamak istediğiniz noktasıdır.</span><span class="sxs-lookup"><span data-stu-id="7eaaa-201">You can have additional configuration, but the important point is that in the base docker-compose.yml file, you just want to set the information that is common across environments.</span></span> <span data-ttu-id="7eaaa-202">Ardından docker-compose.override.yml veya benzer dosyaları üretim ya da hazırlık, her ortam için belirli yapılandırma yerleştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="7eaaa-202">Then in the docker-compose.override.yml or similar files for production or staging, you should place configuration that is specific for each environment.</span></span>

<span data-ttu-id="7eaaa-203">Genellikle, docker-compose.override.yml hizmetine aşağıdaki örnekte olduğu gibi geliştirme ortamınız için kullanılır:</span><span class="sxs-lookup"><span data-stu-id="7eaaa-203">Usually, the docker-compose.override.yml is used for your development environment, as in the following example from eShopOnContainers:</span></span>

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

<span data-ttu-id="7eaaa-204">Bu örnekte, geliştirme geçersiz kılma yapılandırmasını konağa bazı bağlantı noktalarını kullanıma sunar, ortam değişkenlerini tanımlar URL'lerini yönlendirmek ve geliştirme ortamı için bağlantı dizelerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="7eaaa-204">In this example, the development override configuration exposes some ports to the host, defines environment variables with redirect URLs, and specifies connection strings for the development environment.</span></span> <span data-ttu-id="7eaaa-205">Bu ayarlar, tüm yeni geliştirme ortamına yöneliktir.</span><span class="sxs-lookup"><span data-stu-id="7eaaa-205">These settings are all just for the development environment.</span></span>

<span data-ttu-id="7eaaa-206">Çalıştırdığınızda `docker-compose up` (veya Visual Studio'dan başlatmak), her iki dosya birleştirme gibi komut geçersiz kılmaları otomatik olarak okur.</span><span class="sxs-lookup"><span data-stu-id="7eaaa-206">When you run `docker-compose up` (or launch it from Visual Studio), the command reads the overrides automatically as if it were merging both files.</span></span>

<span data-ttu-id="7eaaa-207">Farklı yapılandırma değerleri, bağlantı noktası veya bağlantı dizeleri üretim ortamı için başka bir Compose dosyasının istediğinizi varsayalım.</span><span class="sxs-lookup"><span data-stu-id="7eaaa-207">Suppose that you want another Compose file for the production environment, with different configuration values, ports or connection strings.</span></span> <span data-ttu-id="7eaaa-208">Adlı bir dosya gibi başka bir geçersiz kılma dosyası oluşturabilirsiniz `docker-compose.prod.yml` farklı ayarlar ve ortam değişkenleri.</span><span class="sxs-lookup"><span data-stu-id="7eaaa-208">You can create another override file, like file named `docker-compose.prod.yml` with different settings and environment variables.</span></span>  <span data-ttu-id="7eaaa-209">Bu dosyayı farklı bir Git deposunda depolanabilir veya yönetilen ve farklı bir takım tarafından güvenli hale getirilmiş.</span><span class="sxs-lookup"><span data-stu-id="7eaaa-209">That file might be stored in a different Git repo or managed and secured by a different team.</span></span>

#### <a name="how-to-deploy-with-a-specific-override-file"></a><span data-ttu-id="7eaaa-210">Bir özel geçersiz kılma dosyası ile dağıtma</span><span class="sxs-lookup"><span data-stu-id="7eaaa-210">How to deploy with a specific override file</span></span>

<span data-ttu-id="7eaaa-211">Farklı ada sahip birden fazla geçersiz kılma dosyası veya bir geçersiz kılma dosyası kullanmak için -f seçeneğiyle kullanabilirsiniz docker-compose komutu ve dosyaları belirtin.</span><span class="sxs-lookup"><span data-stu-id="7eaaa-211">To use multiple override files, or an override file with a different name, you can use the -f option with the docker-compose command and specify the files.</span></span> <span data-ttu-id="7eaaa-212">Komut satırında belirtildikleri sırada birleştirmeleri dosyalarını oluşturun.</span><span class="sxs-lookup"><span data-stu-id="7eaaa-212">Compose merges files in the order they are specified on the command line.</span></span> <span data-ttu-id="7eaaa-213">Aşağıdaki örnek, geçersiz kılma dosyalarıyla dağıtma gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="7eaaa-213">The following example shows how to deploy with override files.</span></span>

```
docker-compose -f docker-compose.yml -f docker-compose.prod.yml up -d
```

#### <a name="using-environment-variables-in-docker-compose-files"></a><span data-ttu-id="7eaaa-214">Ortam değişkenlerini kullanarak içinde docker-compose dosyası</span><span class="sxs-lookup"><span data-stu-id="7eaaa-214">Using environment variables in docker-compose files</span></span>

<span data-ttu-id="7eaaa-215">Biz önceki örneklerde gösterildiği gibi ortam değişkenlerinden yapılandırma bilgilerini almak için özellikle de üretim ortamlarında, kullanışlı.</span><span class="sxs-lookup"><span data-stu-id="7eaaa-215">It is convenient, especially in production environments, to be able to get configuration information from environment variables, as we have shown in previous examples.</span></span> <span data-ttu-id="7eaaa-216">Docker-compose dosyalarınızı söz dizimini kullanarak bir ortam değişkeni başvurusu \${MY\_VAR}.</span><span class="sxs-lookup"><span data-stu-id="7eaaa-216">You reference an environment variable in your docker-compose files using the syntax \${MY\_VAR}.</span></span> <span data-ttu-id="7eaaa-217">Aşağıdaki satırı bir docker compose.prod.yml dosyasından bir ortam değişkeninin değerini yapmayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="7eaaa-217">The following line from a docker-compose.prod.yml file shows how to reference the value of an environment variable.</span></span>

```yml
IdentityUrl=http://${ESHOP_PROD_EXTERNAL_DNS_NAME_OR_IP}:5105
```

<span data-ttu-id="7eaaa-218">Ortam değişkenlerini oluşturuldu ve ana bilgisayar ortamına bağlı olarak, farklı şekillerde başlatıldı (Linux, Windows, bulut kümesine, vs.).</span><span class="sxs-lookup"><span data-stu-id="7eaaa-218">Environment variables are created and initialized in different ways, depending on your host environment (Linux, Windows, Cloud cluster, etc.).</span></span> <span data-ttu-id="7eaaa-219">Ancak, uygun bir yaklaşım bir .env dosyasında kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="7eaaa-219">However, a convenient approach is to use an .env file.</span></span> <span data-ttu-id="7eaaa-220">.Env dosyasında varsayılan ortam değişkenleri bildirme docker-compose dosyalarını destekler.</span><span class="sxs-lookup"><span data-stu-id="7eaaa-220">The docker-compose files support declaring default environment variables in the .env file.</span></span> <span data-ttu-id="7eaaa-221">Bu değerler ortam değişkenleri için varsayılan değerlerdir.</span><span class="sxs-lookup"><span data-stu-id="7eaaa-221">These values for the environment variables are the default values.</span></span> <span data-ttu-id="7eaaa-222">Ancak, her ortamlarınızda (ana bilgisayar işletim sistemi veya ortam değişkenlerini kümenizden) tanımlamış olabileceği değerlere göre kılınabilir.</span><span class="sxs-lookup"><span data-stu-id="7eaaa-222">But they can be overridden by the values you might have defined in each of your environments (host OS or environment variables from your cluster).</span></span> <span data-ttu-id="7eaaa-223">.Env dosyasında bu klasöre yerleştirdiğiniz yere docker-compose komutu yürütülmediyse.</span><span class="sxs-lookup"><span data-stu-id="7eaaa-223">You place this .env file in the folder where the docker-compose command is executed from.</span></span>

<span data-ttu-id="7eaaa-224">Aşağıdaki örnek, bir .env dosyasında gibi gösterir [.env](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/.env) hizmetine uygulamanın dosyası.</span><span class="sxs-lookup"><span data-stu-id="7eaaa-224">The following example shows an .env file like the [.env](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/.env) file for the eShopOnContainers application.</span></span>

```
# .env file

ESHOP_EXTERNAL_DNS_NAME_OR_IP=localhost

ESHOP_PROD_EXTERNAL_DNS_NAME_OR_IP=10.121.122.92
```

<span data-ttu-id="7eaaa-225">Docker-compose bekliyor biçiminde bir .env dosyasında her satırı &lt;değişkeni&gt;=&lt;değer&gt;.</span><span class="sxs-lookup"><span data-stu-id="7eaaa-225">Docker-compose expects each line in an .env file to be in the format &lt;variable&gt;=&lt;value&gt;.</span></span>

<span data-ttu-id="7eaaa-226">Çalışma zamanı ortamında her zaman ayarlanan değerleri içinde .env dosyasında tanımlı değerlerin üzerine yazılacağını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="7eaaa-226">Note that the values set in the runtime environment always override the values defined inside the .env file.</span></span> <span data-ttu-id="7eaaa-227">Benzer şekilde, geçirilen komut satırı komut bağımsız değişkenlerinin değerleri de .env dosyasında ayarlanan varsayılan değerlerini geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="7eaaa-227">In a similar way, values passed via command-line command arguments also override the default values set in the .env file.</span></span>

#### <a name="additional-resources"></a><span data-ttu-id="7eaaa-228">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="7eaaa-228">Additional resources</span></span>

-   <span data-ttu-id="7eaaa-229">**Genel Bakış docker Compose**
    [*https://docs.docker.com/compose/overview/*](https://docs.docker.com/compose/overview/)</span><span class="sxs-lookup"><span data-stu-id="7eaaa-229">**Overview of Docker Compose**
[*https://docs.docker.com/compose/overview/*](https://docs.docker.com/compose/overview/)</span></span>

-   <span data-ttu-id="7eaaa-230">**Birden çok Compose dosyaları**
    [*https://docs.docker.com/compose/extends/\#multiple-compose-files*](https://docs.docker.com/compose/extends/#multiple-compose-files)</span><span class="sxs-lookup"><span data-stu-id="7eaaa-230">**Multiple Compose files**
[*https://docs.docker.com/compose/extends/\#multiple-compose-files*](https://docs.docker.com/compose/extends/#multiple-compose-files)</span></span>

### <a name="building-optimized-aspnet-core-docker-images"></a><span data-ttu-id="7eaaa-231">ASP.NET Core Docker görüntüleri oluşturma en iyi duruma getirilmiş</span><span class="sxs-lookup"><span data-stu-id="7eaaa-231">Building optimized ASP.NET Core Docker images</span></span>

<span data-ttu-id="7eaaa-232">Internet kaynaklarında Docker ve .NET Core araştırıyorsanız, Basitlik, bir kapsayıcıya kaynağınızı kopyalayarak bir Docker görüntüsü oluşturma gösteren dockerfile'ları bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7eaaa-232">If you are exploring Docker and .NET Core on sources on the Internet, you will find Dockerfiles that demonstrate the simplicity of building a Docker image by copying your source into a container.</span></span> <span data-ttu-id="7eaaa-233">Bu örnekler, basit bir yapılandırma öğesini kullanarak bir Docker görüntüsü, uygulamanızla birlikte paketlenmiş ortamıyla sağlayabilirsiniz önerin.</span><span class="sxs-lookup"><span data-stu-id="7eaaa-233">These examples suggest that by using a simple configuration, you can have a Docker image with the environment packaged with your application.</span></span> <span data-ttu-id="7eaaa-234">Aşağıdaki örnek, basit bir Dockerfile içinde bu damarlı gösterir.</span><span class="sxs-lookup"><span data-stu-id="7eaaa-234">The following example shows a simple Dockerfile in this vein.</span></span>

```
FROM microsoft/dotnet

WORKDIR /app

ENV ASPNETCORE_URLS http://+:80

EXPOSE 80

COPY . .

RUN dotnet restore

ENTRYPOINT ["dotnet", "run"]
```

<span data-ttu-id="7eaaa-235">Böyle bir Dockerfile çalışır.</span><span class="sxs-lookup"><span data-stu-id="7eaaa-235">A Dockerfile like this will work.</span></span> <span data-ttu-id="7eaaa-236">Ancak, özellikle de üretim görüntülerinin görüntülerinizi önemli ölçüde iyileştirebilir.</span><span class="sxs-lookup"><span data-stu-id="7eaaa-236">However, you can substantially optimize your images, especially your production images.</span></span>

<span data-ttu-id="7eaaa-237">Kapsayıcı ve mikro hizmetler modeli sürekli kapsayıcıları başlıyor.</span><span class="sxs-lookup"><span data-stu-id="7eaaa-237">In the container and microservices model, you are constantly starting containers.</span></span> <span data-ttu-id="7eaaa-238">Kapsayıcıları kullanarak normal şekilde kapsayıcı atılabilir olduğundan Uyuyan bir kapsayıcı yeniden başlatmaz.</span><span class="sxs-lookup"><span data-stu-id="7eaaa-238">The typical way of using containers does not restart a sleeping container, because the container is disposable.</span></span> <span data-ttu-id="7eaaa-239">Düzenleyiciler (örneğin, Docker Swarm, Kubernetes, DCOS veya Azure Service Fabric) yalnızca görüntüleri yeni bir örneğini oluşturun.</span><span class="sxs-lookup"><span data-stu-id="7eaaa-239">Orchestrators (like Docker Swarm, Kubernetes, DCOS or Azure Service Fabric) simply create new instances of images.</span></span> <span data-ttu-id="7eaaa-240">Ne bu örnekleme işlemi daha hızlı olacak şekilde nasıl yapılandırıldığında, uygulama ön derleme tarafından en iyi duruma getirme gerektiğini anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="7eaaa-240">What this means is that you would need to optimize by precompiling the application when it is built so the instantiation process will be faster.</span></span> <span data-ttu-id="7eaaa-241">Kapsayıcı başlatıldığında, çalıştırmaya hazır olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="7eaaa-241">When the container is started, it should be ready to run.</span></span> <span data-ttu-id="7eaaa-242">Olmayan geri yükleme ve çalışma zamanında derleme, .NET Core ve Docker birçok blog gönderileri gördüğünüz gibi dotnet kullanarak geri yükleme ve dotnet dotnet CLI komutları, yapı.</span><span class="sxs-lookup"><span data-stu-id="7eaaa-242">You should not restore and compile at run time, using dotnet restore and dotnet build commands from the dotnet CLI that, as you see in many blog posts about .NET Core and Docker.</span></span>

<span data-ttu-id="7eaaa-243">.NET ekibi .NET Core ve ASP.NET Core kapsayıcı iyileştirilmiş bir çerçeve yapmak için önemli işleri yapmak.</span><span class="sxs-lookup"><span data-stu-id="7eaaa-243">The .NET team has been doing important work to make .NET Core and ASP.NET Core a container-optimized framework.</span></span> <span data-ttu-id="7eaaa-244">Yalnızca .NET Core küçük bellek Ayak izi ile basit bir çerçeve olan; Takım başlangıç performansı üzerinde odaklanır ve bazı en iyi duruma getirilmiş Docker görüntüleri gibi üretilen [microsoft/aspnetcore](https://hub.docker.com/r/microsoft/aspnetcore/) görüntü adresinde [Docker Hub](https://hub.docker.com/r/microsoft/aspnetcore/), normal kolaylığına [ Microsoft/dotnet](https://hub.docker.com/r/microsoft/dotnet/) veya [microsoft/nanoserver](https://github.com/dotnet/dotnet-docker/blob/master/1.0/nanoserver/runtime/Dockerfile) görüntüler.</span><span class="sxs-lookup"><span data-stu-id="7eaaa-244">Not only is .NET Core a lightweight framework with a small memory footprint; the team has focused on startup performance and produced some optimized Docker images, like the [microsoft/aspnetcore](https://hub.docker.com/r/microsoft/aspnetcore/) image available at [Docker Hub](https://hub.docker.com/r/microsoft/aspnetcore/), in comparison to the regular [microsoft/dotnet](https://hub.docker.com/r/microsoft/dotnet/) or [microsoft/nanoserver](https://github.com/dotnet/dotnet-docker/blob/master/1.0/nanoserver/runtime/Dockerfile) images.</span></span> <span data-ttu-id="7eaaa-245">[Microsoft/aspnetcore](https://hub.docker.com/r/microsoft/aspnetcore/) otomatik ayarı aspnetcore görüntüsü sağlar\_URL'ler 80 numaralı bağlantı noktasını ve öncesi ngend önbellek derlemelerin; bu ayarların her ikisini de daha hızlı başlangıç neden.</span><span class="sxs-lookup"><span data-stu-id="7eaaa-245">The [microsoft/aspnetcore](https://hub.docker.com/r/microsoft/aspnetcore/) image provides automatic setting of aspnetcore\_urls to port 80 and the pre-ngend cache of assemblies; both of these settings result in faster startup.</span></span>

#### <a name="additional-resources"></a><span data-ttu-id="7eaaa-246">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="7eaaa-246">Additional resources</span></span>

-   <span data-ttu-id="7eaaa-247">**ASP.NET Core ile Docker görüntü oluşturma en iyi duruma getirilmiş**
    [*https://blogs.msdn.microsoft.com/stevelasker/2016/09/29/building-optimized-docker-images-with-asp-net-core/*](https://blogs.msdn.microsoft.com/stevelasker/2016/09/29/building-optimized-docker-images-with-asp-net-core/)</span><span class="sxs-lookup"><span data-stu-id="7eaaa-247">**Building Optimized Docker Images with ASP.NET Core**
[*https://blogs.msdn.microsoft.com/stevelasker/2016/09/29/building-optimized-docker-images-with-asp-net-core/*](https://blogs.msdn.microsoft.com/stevelasker/2016/09/29/building-optimized-docker-images-with-asp-net-core/)</span></span>

### <a name="building-the-application-from-a-build-ci-container"></a><span data-ttu-id="7eaaa-248">Bir derleme (CI) kapsayıcısından uygulama oluşturma</span><span class="sxs-lookup"><span data-stu-id="7eaaa-248">Building the application from a build (CI) container</span></span>

<span data-ttu-id="7eaaa-249">Şekil 8-13'te gösterildiği şekilde, bir derleme makinesi veya uygulamanızı oluşturmak için VM oluşturmak ihtiyacınız yoktur, Docker'ın başka bir avantajı uygulamanızı önceden yapılandırılmış bir kapsayıcı oluşturabilirsiniz içindir.</span><span class="sxs-lookup"><span data-stu-id="7eaaa-249">Another benefit of Docker is that you can build your application from a preconfigured container, as shown in Figure 8-13, so you do not need to create a build machine or VM to build your application.</span></span> <span data-ttu-id="7eaaa-250">Geliştirme makinenizde çalıştırarak test, yapı kapsayıcısı veya kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7eaaa-250">You can use or test that build container by running it at your development machine.</span></span> <span data-ttu-id="7eaaa-251">Ancak daha da ilginç nedir, CI (sürekli tümleştirme) hattından aynı derleme kapsayıcısı kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7eaaa-251">But what is even more interesting is that you can use the same build container from your CI (Continuous Integration) pipeline.</span></span>

![](./media/image14.png)

<span data-ttu-id="7eaaa-252">**Şekil 8-13**.</span><span class="sxs-lookup"><span data-stu-id="7eaaa-252">**Figure 8-13**.</span></span> <span data-ttu-id="7eaaa-253">Docker derleme-kapsayıcı .NET ikili dosyaları derleme</span><span class="sxs-lookup"><span data-stu-id="7eaaa-253">Docker build-container compiling your .NET binaries</span></span> 

<span data-ttu-id="7eaaa-254">Bu senaryo için sağladığımız [microsoft/aspnetcore-build](https://hub.docker.com/r/microsoft/aspnetcore-build/) derlemek ve ASP.NET Core uygulamaları oluşturmak için kullanabileceğiniz bir görüntüsü.</span><span class="sxs-lookup"><span data-stu-id="7eaaa-254">For this scenario, we provide the [microsoft/aspnetcore-build](https://hub.docker.com/r/microsoft/aspnetcore-build/) image, which you can use to compile and build your ASP.NET Core apps.</span></span> <span data-ttu-id="7eaaa-255">Çıkış temel alan bir görüntü yerleştirilir [microsoft/aspnetcore](https://hub.docker.com/r/microsoft/aspnetcore/) da daha önce not ettiğiniz en iyi duruma getirilmiş çalışma zamanı görüntünün görüntü.</span><span class="sxs-lookup"><span data-stu-id="7eaaa-255">The output is placed in an image based on the [microsoft/aspnetcore](https://hub.docker.com/r/microsoft/aspnetcore/) image, which is an optimized runtime image, as previously noted.</span></span>

<span data-ttu-id="7eaaa-256">.NET Core, ASP.NET SDK'sı, npm, dahil olmak üzere bir ASP.NET Core uygulaması derlemek için ihtiyacınız olan her şey aspnetcore-build görüntüsünü içeren Bower, Gulp, vs.</span><span class="sxs-lookup"><span data-stu-id="7eaaa-256">The aspnetcore-build image contains everything you need in order to compile an ASP.NET Core application, including .NET Core, the ASP.NET SDK, npm, Bower, Gulp, etc.</span></span>

<span data-ttu-id="7eaaa-257">Bu bağımlılıklar oluşturma zamanında ihtiyacımız var.</span><span class="sxs-lookup"><span data-stu-id="7eaaa-257">We need these dependencies at build time.</span></span> <span data-ttu-id="7eaaa-258">Ancak görüntü gereksiz derecede büyük hale getirir çünkü bu uygulama ile birlikte çalışma zamanında Yürüt istiyoruz değil.</span><span class="sxs-lookup"><span data-stu-id="7eaaa-258">But we do not want to carry these with the application at runtime, because it would make the image unnecessarily large.</span></span> <span data-ttu-id="7eaaa-259">Hizmetine uygulamada, uygulamayı oluşturmak yalnızca çalıştırarak kapsayıcısından aşağıdaki docker compose komutuyla.</span><span class="sxs-lookup"><span data-stu-id="7eaaa-259">In the eShopOnContainers application, you can build the application from a container by just running the following docker-compose command.</span></span>

```
  docker-compose -f docker-compose.ci.build.yml up
```

<span data-ttu-id="7eaaa-260">Şekil 8-14, bu komut komut satırında çalıştıran gösterir.</span><span class="sxs-lookup"><span data-stu-id="7eaaa-260">Figure 8-14 shows this command running at the command line.</span></span>

![](./media/image15.png)

<span data-ttu-id="7eaaa-261">**Şekil 8-14.**</span><span class="sxs-lookup"><span data-stu-id="7eaaa-261">**Figure 8-14.**</span></span> <span data-ttu-id="7eaaa-262">.NET uygulamanızı bir kapsayıcı oluşturma</span><span class="sxs-lookup"><span data-stu-id="7eaaa-262">Building your .NET application from a container</span></span>

<span data-ttu-id="7eaaa-263">Gördüğünüz gibi çalışmakta olan kapsayıcıyı CI yapısı olduğu\_1 kapsayıcı.</span><span class="sxs-lookup"><span data-stu-id="7eaaa-263">As you can see, the container that is running is the ci-build\_1 container.</span></span> <span data-ttu-id="7eaaa-264">Derleme ve Bilgisayarınızdan yerine ilgili kapsayıcıdaki tüm uygulama içinden yapı bu aspnetcore-build görüntüye bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="7eaaa-264">This is based on the aspnetcore-build image so that it can compile and build your whole application from within that container instead of from your PC.</span></span> <span data-ttu-id="7eaaa-265">Diğer bir deyişle neden gerçekte bu oluşturma ve Linux'ta .NET Core projelerini derlemek — bu kapsayıcı varsayılan Docker Linux ana bilgisayarında çalıştığından.</span><span class="sxs-lookup"><span data-stu-id="7eaaa-265">That is why in reality it is building and compiling the .NET Core projects in Linux—because that container is running on the default Docker Linux host.</span></span>

<span data-ttu-id="7eaaa-266">[Docker-compose.ci.build.yml](https://github.com/dotnet/eShopOnContainers/blob/master/docker-compose.ci.build.yml) için o yansıma (hizmetine parçası) aşağıdaki kodu içeren dosya.</span><span class="sxs-lookup"><span data-stu-id="7eaaa-266">The [docker-compose.ci.build.yml](https://github.com/dotnet/eShopOnContainers/blob/master/docker-compose.ci.build.yml) file for that image (part of eShopOnContainers) contains the following code.</span></span> <span data-ttu-id="7eaaa-267">Kullanarak yapı kapsayıcı başladıktan gördüğünüz [microsoft/aspnetcore-build](https://hub.docker.com/r/microsoft/aspnetcore-build/) görüntü.</span><span class="sxs-lookup"><span data-stu-id="7eaaa-267">You can see that it starts a build container using the [microsoft/aspnetcore-build](https://hub.docker.com/r/microsoft/aspnetcore-build/) image.</span></span>

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

* <span data-ttu-id="7eaaa-268">İle başlayarak **.NET Core 2.0**, `dotnet restore` komutu yürütür otomatik olarak zaman `dotnet publish` komutu yürütülür.</span><span class="sxs-lookup"><span data-stu-id="7eaaa-268">Starting with **.NET Core 2.0**, `dotnet restore` command executes automatically when the `dotnet publish` command is executed.</span></span>

<span data-ttu-id="7eaaa-269">Derleme kapsayıcısı çalışır duruma geldikten sonra .NET SDK'sı dotnet restore çalıştırır ve dotnet .NET bit derle için Çözümdeki tüm projeleri komutları yayımlayın.</span><span class="sxs-lookup"><span data-stu-id="7eaaa-269">Once the build container is up and running, it runs the .NET SDK dotnet restore and dotnet publish commands against all the projects in the solution in order to compile the .NET bits.</span></span> <span data-ttu-id="7eaaa-270">Hizmetine de TypeScript ve Angular için istemci kodu dayalı bir SPA olduğundan, eylem .NET BITS ile ilişkili değildir, ancak bu durumda, bu da npm, JavaScript bağımlılıklarla denetlemesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="7eaaa-270">In this case, because eShopOnContainers also has an SPA based on TypeScript and Angular for the client code, it also needs to check JavaScript dependencies with npm, but that action is not related to the .NET bits.</span></span>

<span data-ttu-id="7eaaa-271">Dotnet komut yapılar yayımlama ve her projesinin klasörüne içinde derlenen Çıkışta yayımlar... Şekil 8-15'te gösterildiği gibi /obj/Docker/publish klasör.</span><span class="sxs-lookup"><span data-stu-id="7eaaa-271">The dotnet publish command builds and publishes the compiled output within each project’s folder to the ../obj/Docker/publish folder, as shown in Figure 8-15.</span></span>

![](./media/image16.png)

<span data-ttu-id="7eaaa-272">**Şekil 8-15.**</span><span class="sxs-lookup"><span data-stu-id="7eaaa-272">**Figure 8-15.**</span></span> <span data-ttu-id="7eaaa-273">Dotnet tarafından oluşturulan ikili dosyaları yayımlama komutu</span><span class="sxs-lookup"><span data-stu-id="7eaaa-273">Binary files generated by the dotnet publish command</span></span>

#### <a name="creating-the-docker-images-from-the-cli"></a><span data-ttu-id="7eaaa-274">CLI'dan Docker görüntüleri oluşturma</span><span class="sxs-lookup"><span data-stu-id="7eaaa-274">Creating the Docker images from the CLI</span></span>

<span data-ttu-id="7eaaa-275">Uygulama çıktısı (her projede) ilgili klasörleri yayımlandıktan sonra sonraki adım gerçekten Docker görüntüleri oluşturmaktır.</span><span class="sxs-lookup"><span data-stu-id="7eaaa-275">Once the application output is published to the related folders (within each project), the next step is to actually build the Docker images.</span></span> <span data-ttu-id="7eaaa-276">Bunu yapmak için docker-compose derleme kullanın ve Şekil 8-16 gösterildiği gibi komutları docker-compose.</span><span class="sxs-lookup"><span data-stu-id="7eaaa-276">To do this, you use the docker-compose build and docker-compose up commands, as shown in Figure 8-16.</span></span>

![](./media/image17.png)

<span data-ttu-id="7eaaa-277">**Şekil 8-16.**</span><span class="sxs-lookup"><span data-stu-id="7eaaa-277">**Figure 8-16.**</span></span> <span data-ttu-id="7eaaa-278">Docker görüntülerinizi oluşturmak ve çalışan kapsayıcılar</span><span class="sxs-lookup"><span data-stu-id="7eaaa-278">Building Docker images and running the containers</span></span>

<span data-ttu-id="7eaaa-279">Şekil 8-17'de nasıl docker-compose komutu çalıştırmaları yapı görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7eaaa-279">In Figure 8-17, you can see how the docker-compose build command runs.</span></span>

![](./media/image18.png)

<span data-ttu-id="7eaaa-280">**Şekil 8-17**.</span><span class="sxs-lookup"><span data-stu-id="7eaaa-280">**Figure 8-17**.</span></span> <span data-ttu-id="7eaaa-281">Docker ile Docker görüntüleri oluşturma-oluşturma komutu oluştur</span><span class="sxs-lookup"><span data-stu-id="7eaaa-281">Building the Docker images with the docker-compose build command</span></span>

<span data-ttu-id="7eaaa-282">Docker-compose arasındaki fark, derleme ve docker compose up komutları olan docker-compose derlemeler ve başlar görüntüleri.</span><span class="sxs-lookup"><span data-stu-id="7eaaa-282">The difference between the docker-compose build and docker-compose up commands is that docker-compose up both builds and starts the images.</span></span>

<span data-ttu-id="7eaaa-283">Visual Studio kullandığınızda, bu adımların tümünü arka planda gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="7eaaa-283">When you use Visual Studio, all these steps are performed under the covers.</span></span> <span data-ttu-id="7eaaa-284">Visual Studio .NET uygulamanızı derleyen, Docker görüntüleri oluşturur ve Docker ana bilgisayar kapsayıcıları dağıtır.</span><span class="sxs-lookup"><span data-stu-id="7eaaa-284">Visual Studio compiles your .NET application, creates the Docker images, and deploys the containers into the Docker host.</span></span> <span data-ttu-id="7eaaa-285">Visual Studio, Docker, doğrudan Visual Studio'dan çalıştırma kapsayıcılarınızı hata ayıklama yapabilme gibi ek özellikler sunar.</span><span class="sxs-lookup"><span data-stu-id="7eaaa-285">Visual Studio offers additional features, like the ability to debug your containers running in Docker, directly from Visual Studio.</span></span>

<span data-ttu-id="7eaaa-286">Genel takeway burada aynı şekilde CI/CD ardışık düzeninizi derleme, uygulamanızı oluşturmak üzere mümkün olduğu — bir yerel makine yerine bir kapsayıcısından.</span><span class="sxs-lookup"><span data-stu-id="7eaaa-286">The overall takeway here is that you are able to build your application the same way your CI/CD pipeline should build it—from a container instead of from a local machine.</span></span> <span data-ttu-id="7eaaa-287">Oluşturulan görüntüleri atandıktan sonra sonra docker kullanarak Docker görüntülerini çalıştırmak yeterlidir-compose komutu.</span><span class="sxs-lookup"><span data-stu-id="7eaaa-287">After having the images created, then you just need to run the Docker images using the docker-compose up command.</span></span>

#### <a name="additional-resources"></a><span data-ttu-id="7eaaa-288">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="7eaaa-288">Additional resources</span></span>

-   <span data-ttu-id="7eaaa-289">**Bir kapsayıcı bitten oluşturma: bir Windows CLI ortamda (dotnet CLI, Docker CLI ve VS Code) hizmetine çözüm ayarlama**
    [*https://github.com/dotnet/eShopOnContainers/wiki/03.-Setting-the-eShopOnContainers-solution-up-in-a-Windows-CLI-environment-(dotnet-CLI, - Docker - CLI- ve -VS-kod)*](https://github.com/dotnet/eShopOnContainers/wiki/03.-Setting-the-eShopOnContainers-solution-up-in-a-Windows-CLI-environment-(dotnet-CLI,-Docker-CLI-and-VS-Code))</span><span class="sxs-lookup"><span data-stu-id="7eaaa-289">**Building bits from a container: Setting the eShopOnContainers solution up in a Windows CLI environment (dotnet CLI, Docker CLI and VS Code)**
[*https://github.com/dotnet/eShopOnContainers/wiki/03.-Setting-the-eShopOnContainers-solution-up-in-a-Windows-CLI-environment-(dotnet-CLI,-Docker-CLI-and-VS-Code)*](https://github.com/dotnet/eShopOnContainers/wiki/03.-Setting-the-eShopOnContainers-solution-up-in-a-Windows-CLI-environment-(dotnet-CLI,-Docker-CLI-and-VS-Code))</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="7eaaa-290">[Önceki](data-driven-crud-microservice.md)
[İleri](database-server-container.md)</span><span class="sxs-lookup"><span data-stu-id="7eaaa-290">[Previous](data-driven-crud-microservice.md)
[Next](database-server-container.md)</span></span>
