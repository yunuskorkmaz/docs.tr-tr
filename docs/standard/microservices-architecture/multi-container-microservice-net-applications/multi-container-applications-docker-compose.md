---
title: Docker-compose.yml ile çok Kapsayıcılı uygulamanızı tanımlama
description: Kapsayıcılı .NET uygulamaları için .NET mikro hizmet mimarisi | Nasıl yapılır docker-compose.yml ile çok kapsayıcılı bir uygulama için mikro hizmetler oluşturma belirtin.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/02/2018
ms.openlocfilehash: 9ce8d64dbd481d30c6687b8747b2091733ea76db
ms.sourcegitcommit: 35316b768394e56087483cde93f854ba607b63bc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2018
ms.locfileid: "52297185"
---
# <a name="defining-your-multi-container-application-with-docker-composeyml"></a><span data-ttu-id="479f2-103">Docker-compose.yml ile çok Kapsayıcılı uygulamanızı tanımlama</span><span class="sxs-lookup"><span data-stu-id="479f2-103">Defining your multi-container application with docker-compose.yml</span></span> 

<span data-ttu-id="479f2-104">Bu kılavuzdaki [docker-compose.yml](https://docs.docker.com/compose/compose-file/) dosya bölümünde tanıtılmıştır [4. adım. Çok kapsayıcılı Docker uygulaması oluştururken, hizmetlerinizi docker-compose.yml tanımlamak](../docker-application-development-process/docker-app-development-workflow.md#step-4-define-your-services-in-docker-composeyml-when-building-a-multi-container-docker-application).</span><span class="sxs-lookup"><span data-stu-id="479f2-104">In this guide, the [docker-compose.yml](https://docs.docker.com/compose/compose-file/) file was introduced in the section [Step 4. Define your services in docker-compose.yml when building a multi-container Docker application](../docker-application-development-process/docker-app-development-workflow.md#step-4-define-your-services-in-docker-composeyml-when-building-a-multi-container-docker-application).</span></span> <span data-ttu-id="479f2-105">Ancak, daha ayrıntılı olarak incelenmesi yararlı olan docker-compose dosyaları kullanmak için ek yolu vardır.</span><span class="sxs-lookup"><span data-stu-id="479f2-105">However, there are additional ways to use the docker-compose files that are worth exploring in further detail.</span></span>

<span data-ttu-id="479f2-106">Örneğin, docker-compose.yml dosyası çok Kapsayıcılı uygulamanızı dağıtmak istediğiniz nasıl açıkça tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="479f2-106">For example, you can explicitly describe how you want to deploy your multi-container application in the docker-compose.yml file.</span></span> <span data-ttu-id="479f2-107">İsteğe bağlı olarak, özel Docker görüntülerinizi oluşturmak için nasıl yükleyeceksiniz tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="479f2-107">Optionally, you can also describe how you are going to build your custom Docker images.</span></span> <span data-ttu-id="479f2-108">(Özel Docker görüntüleri ile Docker CLI'yı da oluşturulabilir.)</span><span class="sxs-lookup"><span data-stu-id="479f2-108">(Custom Docker images can also be built with the Docker CLI.)</span></span>

<span data-ttu-id="479f2-109">Temel olarak, her kapsayıcıları dağıtmak istediğiniz ek olarak her kapsayıcı dağıtımı için belirli özellikleri tanımlar.</span><span class="sxs-lookup"><span data-stu-id="479f2-109">Basically, you define each of the containers you want to deploy plus certain characteristics for each container deployment.</span></span> <span data-ttu-id="479f2-110">Bir çoklu kapsayıcı dağıtım açıklama dosyası oluşturduktan sonra tek bir eylem tarafından düzenlenen tüm çözüm dağıtabileceğiniz [docker compose up](https://docs.docker.com/compose/overview/) CLI komutunu veya dağıtabilir, saydam Visual Studio'dan.</span><span class="sxs-lookup"><span data-stu-id="479f2-110">Once you have a multi-container deployment description file, you can deploy the whole solution in a single action orchestrated by the [docker-compose up](https://docs.docker.com/compose/overview/) CLI command, or you can deploy it transparently from Visual Studio.</span></span> <span data-ttu-id="479f2-111">Aksi takdirde, Docker CLI'yı kullanarak kapsayıcı tarafından kapsayıcı birden çok adımda dağıtmak için kullanmanız gerekecektir `docker run` komut satırından komutu.</span><span class="sxs-lookup"><span data-stu-id="479f2-111">Otherwise, you would need to use the Docker CLI to deploy container-by-container in multiple steps by using the `docker run` command from the command line.</span></span> <span data-ttu-id="479f2-112">Bu nedenle, docker-compose.yml tanımlanan her bir hizmet tam olarak bir resim belirtin veya bu yapı gerekir.</span><span class="sxs-lookup"><span data-stu-id="479f2-112">Therefore, each service defined in docker-compose.yml must specify exactly one image or build.</span></span> <span data-ttu-id="479f2-113">Diğer anahtarlar isteğe bağlıdır ve alınmak üzere kendi `docker run` komut satırı ortaklarınıza.</span><span class="sxs-lookup"><span data-stu-id="479f2-113">Other keys are optional, and are analogous to their `docker run` command-line counterparts.</span></span>

<span data-ttu-id="479f2-114">Aşağıdaki YAML koduna hizmetine örneği için bir olası genel ancak tek docker-compose.yml dosyası tanımıdır.</span><span class="sxs-lookup"><span data-stu-id="479f2-114">The following YAML code is the definition of a possible global but single docker-compose.yml file for the eShopOnContainers sample.</span></span> <span data-ttu-id="479f2-115">Bu gerçek docker-compose dosyasından hizmetine değildir.</span><span class="sxs-lookup"><span data-stu-id="479f2-115">This is not the actual docker-compose file from eShopOnContainers.</span></span> <span data-ttu-id="479f2-116">Bunun yerine, tek bir dosyada en iyi değil, bir basit ve birleştirilmiş sürüm olduğu şekilde çalışmak için docker compose dosyaları, daha sonra açıklanacaktır gibi.</span><span class="sxs-lookup"><span data-stu-id="479f2-116">Instead, it is a simplified and consolidated version in a single file, which is not the best way to work with docker-compose files, as will be explained later.</span></span>

```yml
version: '3.4'

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

<span data-ttu-id="479f2-117">Hizmetler bu dosyadaki kök anahtardır.</span><span class="sxs-lookup"><span data-stu-id="479f2-117">The root key in this file is services.</span></span> <span data-ttu-id="479f2-118">Bu anahtarın altında dağıtmak ve yürüttüğünüzde çalıştırmak istediğiniz hizmetleri tanımlamakta `docker-compose up` komut ya da bu docker-compose.yml dosyasını kullanarak Visual Studio'dan dağıtırken.</span><span class="sxs-lookup"><span data-stu-id="479f2-118">Under that key you define the services you want to deploy and run when you execute the `docker-compose up` command or when you deploy from Visual Studio by using this docker-compose.yml file.</span></span> <span data-ttu-id="479f2-119">Bu durumda, docker-compose.yml dosyası aşağıdaki tabloda açıklandığı gibi tanımlı, birden çok hizmet yok.</span><span class="sxs-lookup"><span data-stu-id="479f2-119">In this case, the docker-compose.yml file has multiple services defined, as described in the following table.</span></span>

| <span data-ttu-id="479f2-120">Hizmet adı</span><span class="sxs-lookup"><span data-stu-id="479f2-120">Service name</span></span> | <span data-ttu-id="479f2-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="479f2-121">Description</span></span> |
|--------------|-------------|
| <span data-ttu-id="479f2-122">webmvc</span><span class="sxs-lookup"><span data-stu-id="479f2-122">webmvc</span></span>       | <span data-ttu-id="479f2-123">Sunucu tarafı c mikro hizmetler kullanan ASP.NET Core MVC uygulaması da dahil olmak üzere kapsayıcı\#</span><span class="sxs-lookup"><span data-stu-id="479f2-123">Container including the ASP.NET Core MVC application consuming the microservices from server-side C\#</span></span>|
| <span data-ttu-id="479f2-124">catalog.api</span><span class="sxs-lookup"><span data-stu-id="479f2-124">catalog.api</span></span>  | <span data-ttu-id="479f2-125">Katalog ASP.NET Core Web API'si mikro hizmet de dahil olmak üzere kapsayıcı</span><span class="sxs-lookup"><span data-stu-id="479f2-125">Container including the Catalog ASP.NET Core Web API microservice</span></span> |
| <span data-ttu-id="479f2-126">ordering.api</span><span class="sxs-lookup"><span data-stu-id="479f2-126">ordering.api</span></span> | <span data-ttu-id="479f2-127">ASP.NET Core Web API'si sıralama mikro hizmet de dahil olmak üzere kapsayıcı</span><span class="sxs-lookup"><span data-stu-id="479f2-127">Container including the Ordering ASP.NET Core Web API microservice</span></span> |
| <span data-ttu-id="479f2-128">SQL.Data</span><span class="sxs-lookup"><span data-stu-id="479f2-128">sql.data</span></span>     | <span data-ttu-id="479f2-129">Linux için mikro hizmetler veritabanlarını barındıran SQL Server çalıştıran kapsayıcı</span><span class="sxs-lookup"><span data-stu-id="479f2-129">Container running SQL Server for Linux, holding the microservices databases</span></span> |
| <span data-ttu-id="479f2-130">Basket.api</span><span class="sxs-lookup"><span data-stu-id="479f2-130">basket.api</span></span>   | <span data-ttu-id="479f2-131">Sepet ASP.NET Core Web API'si mikro hizmet ile kapsayıcı</span><span class="sxs-lookup"><span data-stu-id="479f2-131">Container with the Basket ASP.NET Core Web API microservice</span></span> |
| <span data-ttu-id="479f2-132">Basket.Data</span><span class="sxs-lookup"><span data-stu-id="479f2-132">basket.data</span></span>  | <span data-ttu-id="479f2-133">REDIS çalıştıran kapsayıcısı önbellek hizmeti, sepet veritabanı olarak REDIS önbelleği ile</span><span class="sxs-lookup"><span data-stu-id="479f2-133">Container running the REDIS cache service, with the basket database as a REDIS cache</span></span> |

### <a name="a-simple-web-service-api-container"></a><span data-ttu-id="479f2-134">Basit bir Web hizmeti API'si kapsayıcı</span><span class="sxs-lookup"><span data-stu-id="479f2-134">A simple Web Service API container</span></span>

<span data-ttu-id="479f2-135">Tek bir kapsayıcı'na Odaklanıldığında, basit bir tanımı catalog.api container-mikro hizmet vardır:</span><span class="sxs-lookup"><span data-stu-id="479f2-135">Focusing on a single container, the catalog.api container-microservice has a straightforward definition:</span></span>

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

<span data-ttu-id="479f2-136">Bu kapsayıcı hizmeti, temel yapılandırması aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="479f2-136">This containerized service has the following basic configuration:</span></span>

-   <span data-ttu-id="479f2-137">Bu özel eshop/catalog.api görüntüye bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="479f2-137">It is based on the custom eshop/catalog.api image.</span></span> <span data-ttu-id="479f2-138">Basitlik'ın çok için hiçbir derleme yok: anahtar dosyasında ayarı.</span><span class="sxs-lookup"><span data-stu-id="479f2-138">For simplicity’s sake, there is no build: key setting in the file.</span></span> <span data-ttu-id="479f2-139">Bu görüntü daha önce (docker derleme ile) oluşturulmuş gerekir veya herhangi bir Docker kayıt defterinden (docker pull komutuyla) indirilip anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="479f2-139">This means that the image must have been previously built (with docker build) or have been downloaded (with the docker pull command) from any Docker registry.</span></span>

-   <span data-ttu-id="479f2-140">ConnectionString Kataloğu veri modeli içeren SQL Server örneğine erişmesi için Entity Framework tarafından kullanılacak bağlantı dizesiyle adlı bir ortam değişkeni tanımlar.</span><span class="sxs-lookup"><span data-stu-id="479f2-140">It defines an environment variable named ConnectionString with the connection string to be used by Entity Framework to access the SQL Server instance that contains the catalog data model.</span></span> <span data-ttu-id="479f2-141">Bu durumda, aynı SQL Server kapsayıcı birden çok veritabanı tutuyor.</span><span class="sxs-lookup"><span data-stu-id="479f2-141">In this case, the same SQL Server container is holding multiple databases.</span></span> <span data-ttu-id="479f2-142">Bu nedenle, daha az bellek için Docker geliştirme makinenizde gerekir.</span><span class="sxs-lookup"><span data-stu-id="479f2-142">Therefore, you need less memory in your development machine for Docker.</span></span> <span data-ttu-id="479f2-143">Ancak, her bir mikro hizmet veritabanı için bir SQL Server kapsayıcı dağıtabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="479f2-143">However, you could also deploy one SQL Server container for each microservice database.</span></span>

-   <span data-ttu-id="479f2-144">SQL Server sql.data, Linux için SQL Server örneğini çalıştıran kapsayıcısı için kullanılan aynı adı olan addır.</span><span class="sxs-lookup"><span data-stu-id="479f2-144">The SQL Server name is sql.data, which is the same name used for the container that is running the SQL Server instance for Linux.</span></span> <span data-ttu-id="479f2-145">Bu kullanışlıdır; Bu ad çözümlemesi (Docker konağı dahili) kullanabilmek için ağ adresi çözer, bu diğer kapsayıcılardan eriştiğiniz kapsayıcılar için iç IP bilmek zorunda kalmazsınız.</span><span class="sxs-lookup"><span data-stu-id="479f2-145">This is convenient; being able to use this name resolution (internal to the Docker host) will resolve the network address so you don’t need to know the internal IP for the containers you are accessing from other containers.</span></span>

<span data-ttu-id="479f2-146">Bağlantı dizesi bir ortam değişkeni tarafından tanımlı olduğundan, farklı bir mekanizma aracılığıyla ve farklı bir zamanda bu değişkeni ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="479f2-146">Because the connection string is defined by an environment variable, you could set that variable through a different mechanism and at a different time.</span></span> <span data-ttu-id="479f2-147">Örneğin, son konaklar veya CI/CD işlem hatlarınızı Azure DevOps Hizmetleri veya tercih edilen DevOps sisteminizi gelen yapmakta üretime dağıtırken farklı bağlantı dizesi ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="479f2-147">For example, you could set a different connection string when deploying to production in the final hosts, or by doing it from your CI/CD pipelines in Azure DevOps Services or your preferred DevOps system.</span></span>

-   <span data-ttu-id="479f2-148">Bu, Docker konağının catalog.api hizmetinde iç erişimi için 80 numaralı bağlantı noktasını kullanıma sunar.</span><span class="sxs-lookup"><span data-stu-id="479f2-148">It exposes port 80 for internal access to the catalog.api service within the Docker host.</span></span> <span data-ttu-id="479f2-149">Konak şu anda bir Linux VM Linux için Docker görüntü temel alan, ancak bunun yerine bir Windows görüntüsü üzerinde çalıştırmak için kapsayıcı yapılandırabilirsiniz olmasıdır.</span><span class="sxs-lookup"><span data-stu-id="479f2-149">The host is currently a Linux VM because it is based on a Docker image for Linux, but you could configure the container to run on a Windows image instead.</span></span>

-   <span data-ttu-id="479f2-150">Bu, kullanıma sunulan bağlantı noktası (Linux VM) Docker konak makinedeki 5101 numaralı bağlantı noktasına kapsayıcı üzerindeki 80 iletir.</span><span class="sxs-lookup"><span data-stu-id="479f2-150">It forwards the exposed port 80 on the container to port 5101 on the Docker host machine (the Linux VM).</span></span>

-   <span data-ttu-id="479f2-151">Web hizmeti sql.data hizmet (SQL Server örneği için bir kapsayıcı içinde çalışan Linux veritabanı) bağlar.</span><span class="sxs-lookup"><span data-stu-id="479f2-151">It links the web service to the sql.data service (the SQL Server instance for Linux database running in a container).</span></span> <span data-ttu-id="479f2-152">Bu bağımlılık belirttiğinizde, sql.data kapsayıcı zaten başlamış catalog.api kapsayıcı tamamlanıncaya kadar çalışmaz; Bu ilk catalog.api SQL Server veritabanına sahip gerektiğinden önemli ve çalışır durumdadır.</span><span class="sxs-lookup"><span data-stu-id="479f2-152">When you specify this dependency, the catalog.api container will not start until the sql.data container has already started; this is important because catalog.api needs to have the SQL Server database up and running first.</span></span> <span data-ttu-id="479f2-153">Docker kapsayıcı düzeyinde iade ettiğinden ancak, bu tür bir kapsayıcı bağımlılık çoğu durumda, yeterli değildir.</span><span class="sxs-lookup"><span data-stu-id="479f2-153">However, this kind of container dependency is not enough in many cases, because Docker checks only at the container level.</span></span> <span data-ttu-id="479f2-154">Üstel geri alma ile yeniden deneme mantığı, istemci mikro Hizmetleri uygulamak için önerilir, bu nedenle bazen hizmeti (büyük/küçük harf bu SQL Server) hala hazır olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="479f2-154">Sometimes the service (in this case SQL Server) might still not be ready, so it is advisable to implement retry logic with exponential backoff in your client microservices.</span></span> <span data-ttu-id="479f2-155">Bu şekilde, bir bağımlılık kapsayıcı kısa bir süre için hazır değilse, uygulama hala dayanıklı olacak.</span><span class="sxs-lookup"><span data-stu-id="479f2-155">That way, if a dependency container is not ready for a short time, the application will still be resilient.</span></span>

-   <span data-ttu-id="479f2-156">Dış sunucuları erişmesine izin vermek için yapılandırılmış: ek\_konakları ayarlama dış sunucuların ya da Docker konağı dışında makineleri erişmenizi sağlar (diğer bir deyişle, varsayılan bir Docker geliştirme olan bir Linux VM dışında barındırma) gibi bir yerel SQL Sunucu örneği geliştirme koruyun.</span><span class="sxs-lookup"><span data-stu-id="479f2-156">It is configured to allow access to external servers: the extra\_hosts setting allows you to access external servers or machines outside of the Docker host (that is, outside the default Linux VM which is a development Docker host), such as a local SQL Server instance on your development PC.</span></span>

<span data-ttu-id="479f2-157">Aşağıdaki bölümlerde ele alınacaktır diğer, daha gelişmiş bir docker-compose.yml ayarları vardır.</span><span class="sxs-lookup"><span data-stu-id="479f2-157">There are also other, more advanced docker-compose.yml settings that we will discuss in the following sections.</span></span>

### <a name="using-docker-compose-files-to-target-multiple-environments"></a><span data-ttu-id="479f2-158">Kullanarak docker-compose dosyaları, birden çok ortama hedeflemek için</span><span class="sxs-lookup"><span data-stu-id="479f2-158">Using docker-compose files to target multiple environments</span></span>

<span data-ttu-id="479f2-159">Docker-compose.yml dosyaları tanımı dosyaları ve söz konusu biçimini birden çok altyapıları tarafından kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="479f2-159">The docker-compose.yml files are definition files and can be used by multiple infrastructures that understand that format.</span></span> <span data-ttu-id="479f2-160">En basit bir araçtır docker-compose komutu.</span><span class="sxs-lookup"><span data-stu-id="479f2-160">The most straightforward tool is the docker-compose command.</span></span>

<span data-ttu-id="479f2-161">Kullanarak bu nedenle, docker compose komutuyla aşağıdaki ana senaryoları hedefleyebilir.</span><span class="sxs-lookup"><span data-stu-id="479f2-161">Therefore, by using the docker-compose command you can target the following main scenarios.</span></span>

#### <a name="development-environments"></a><span data-ttu-id="479f2-162">Geliştirme ortamları</span><span class="sxs-lookup"><span data-stu-id="479f2-162">Development environments</span></span>

<span data-ttu-id="479f2-163">Uygulama geliştirirken, yalıtılmış bir geliştirme ortamında bir uygulamayı çalıştırmak önemlidir.</span><span class="sxs-lookup"><span data-stu-id="479f2-163">When you develop applications, it is important to be able to run an application in an isolated development environment.</span></span> <span data-ttu-id="479f2-164">Kullanabileceğiniz docker-compose, ortam veya kullandığı docker perde compose Visual Studio kullanmak için CLI komutu.</span><span class="sxs-lookup"><span data-stu-id="479f2-164">You can use the docker-compose CLI command to create that environment or use Visual Studio which uses docker-compose under the covers.</span></span>

<span data-ttu-id="479f2-165">Docker-compose.yml dosyasını yapılandırın ve hizmeti tüm uygulama bağımlılıklarınızın (diğer hizmetleri, önbellek, veritabanları, kuyruklar, vb.) belge sağlar.</span><span class="sxs-lookup"><span data-stu-id="479f2-165">The docker-compose.yml file allows you to configure and document all your application’s service dependencies (other services, cache, databases, queues, etc.).</span></span> <span data-ttu-id="479f2-166">Kullanarak CLI komut docker-compose, oluşturabilir ve her bir bağımlılığın için bir veya daha fazla kapsayıcıları tek bir komutla Başlat (docker compose up).</span><span class="sxs-lookup"><span data-stu-id="479f2-166">Using the docker-compose CLI command, you can create and start one or more containers for each dependency with a single command (docker-compose up).</span></span>

<span data-ttu-id="479f2-167">Docker-compose.yml dosyaları Docker altyapısı tarafından yorumlanan yapılandırma dosyalarını ancak uygun belge dosyaları çok kapsayıcılı bir uygulama, oluşumunu hakkında da görür.</span><span class="sxs-lookup"><span data-stu-id="479f2-167">The docker-compose.yml files are configuration files interpreted by Docker engine but also serve as convenient documentation files about the composition of your multi-container application.</span></span>

#### <a name="testing-environments"></a><span data-ttu-id="479f2-168">Test ortamları</span><span class="sxs-lookup"><span data-stu-id="479f2-168">Testing environments</span></span>

<span data-ttu-id="479f2-169">Herhangi bir sürekli dağıtım (CD) veya sürekli tümleştirme (CI) işlem önemli bir parçası olan birim testleri ve tümleştirme testleri.</span><span class="sxs-lookup"><span data-stu-id="479f2-169">An important part of any continuous deployment (CD) or continuous integration (CI) process are the unit tests and integration tests.</span></span> <span data-ttu-id="479f2-170">Bu otomatik testleri yalıtılmış bir ortam gerektirdiğinden, kullanıcılar ya da herhangi bir değişiklik uygulamanın veri etkilenmez.</span><span class="sxs-lookup"><span data-stu-id="479f2-170">These automated tests require an isolated environment so they are not impacted by the users or any other change in the application’s data.</span></span>

<span data-ttu-id="479f2-171">Docker Compose ile oluşturabilir ve bu yalıtılmış bir ortamda çok bir kolayca komut istemi veya komut dosyaları, aşağıdaki komutları gibi birkaç komut yok:</span><span class="sxs-lookup"><span data-stu-id="479f2-171">With Docker Compose you can create and destroy that isolated environment very easily in a few commands from your command prompt or scripts, like the following commands:</span></span>

```
docker-compose -f docker-compose.yml -f docker-compose-test.override.yml up -d
./run_unit_tests
docker-compose -f docker-compose.yml -f docker-compose.test.override.yml down
```

#### <a name="production-deployments"></a><span data-ttu-id="479f2-172">Üretim dağıtımları</span><span class="sxs-lookup"><span data-stu-id="479f2-172">Production deployments</span></span>

<span data-ttu-id="479f2-173">Oluştur, uzak bir Docker altyapısı dağıtmak için de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="479f2-173">You can also use Compose to deploy to a remote Docker Engine.</span></span> <span data-ttu-id="479f2-174">Tipik bir durumda, tek bir Docker konağı örneği dağıtmaktır (üretim VM veya sunucu ile sağlanan gibi [Docker Machine](https://docs.docker.com/machine/overview/)).</span><span class="sxs-lookup"><span data-stu-id="479f2-174">A typical case is to deploy to a single Docker host instance (like a production VM or server provisioned with [Docker Machine](https://docs.docker.com/machine/overview/)).</span></span>

<span data-ttu-id="479f2-175">Herhangi diğer orchestrator (Azure Service Fabric, Kubernetes, vb.) kullanıyorsanız, bu docker-compose.yml, ancak diğer orchestrator tarafından gereken biçimde gibi Kurulum ve meta verileri yapılandırma ayarlarını eklemek gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="479f2-175">If you are using any other orchestrator (Azure Service Fabric, Kubernetes, etc.), you might need to add setup and metadata configuration settings like those in docker-compose.yml, but in the format required by the other orchestrator.</span></span>

<span data-ttu-id="479f2-176">Her iki durumda da docker-compose geliştirme, test ve üretim iş akışları için kullanışlı bir aracı ve meta veri biçimi, üretim iş akışı, kullanmakta olduğunuz orchestrator üzerinde farklılık gösterebilir ancak.</span><span class="sxs-lookup"><span data-stu-id="479f2-176">In any case, docker-compose is a convenient tool and metadata format for development, testing and production workflows, although the production workflow might vary on the orchestrator you are using.</span></span>

### <a name="using-multiple-docker-compose-files-to-handle-several-environments"></a><span data-ttu-id="479f2-177">Birden fazla docker-compose birkaç ortamlarını işleyecek şekilde dosyaları</span><span class="sxs-lookup"><span data-stu-id="479f2-177">Using multiple docker-compose files to handle several environments</span></span>

<span data-ttu-id="479f2-178">Farklı ortamlar hedeflenirken birden çok kullanması gereken compose dosyası.</span><span class="sxs-lookup"><span data-stu-id="479f2-178">When targeting different environments, you should use multiple compose files.</span></span> <span data-ttu-id="479f2-179">Bu ortama bağlı olarak birden çok yapılandırma çeşitleri oluşturmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="479f2-179">This lets you create multiple configuration variants depending on the environment.</span></span>

#### <a name="overriding-the-base-docker-compose-file"></a><span data-ttu-id="479f2-180">Temel docker-compose dosyası geçersiz kılma</span><span class="sxs-lookup"><span data-stu-id="479f2-180">Overriding the base docker-compose file</span></span>

<span data-ttu-id="479f2-181">Önceki bölümlerde gösterildiği Basitleştirilmiş örneklerde gösterildiği gibi bir tek docker-compose.yml dosyası kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="479f2-181">You could use a single docker-compose.yml file as in the simplified examples shown in previous sections.</span></span> <span data-ttu-id="479f2-182">Bununla birlikte, çoğu uygulama için önerilmez.</span><span class="sxs-lookup"><span data-stu-id="479f2-182">However, that is not recommended for most applications.</span></span>

<span data-ttu-id="479f2-183">Varsayılan olarak, iki dosya, docker-compose.yml ve docker-compose.override.yml isteğe bağlı dosya oluşturma okur.</span><span class="sxs-lookup"><span data-stu-id="479f2-183">By default, Compose reads two files, a docker-compose.yml and an optional docker-compose.override.yml file.</span></span> <span data-ttu-id="479f2-184">Visual Studio kullanıyorsanız ve Docker desteğini etkinleştirme, Visual Studio ayrıca uygulamayı hata ayıklama için bir ek docker compose.vs.debug.g.yml dosyası oluşturur, Şekil 6-11'de gösterildiği gibi bu klasör obj dosyasında bir göz atabilirsiniz\\Docker \\ ana çözüm klasöründe.</span><span class="sxs-lookup"><span data-stu-id="479f2-184">As shown in Figure 6-11, when you are using Visual Studio and enabling Docker support, Visual Studio also creates an additional docker-compose.vs.debug.g.yml file for debugging the application, you can take a look at this file in folder obj\\Docker\\ in the main solution folder.</span></span>

![docker-compose proje dosya yapısı: .dockerignore dosyaları yoksaymak için docker-compose mikro hizmetler için compose.yml, docker-mikro hizmetler ortamını yapılandırmak için compose.override.yml.](./media/image12.png)

<span data-ttu-id="479f2-186">**Şekil 6-11**.</span><span class="sxs-lookup"><span data-stu-id="479f2-186">**Figure 6-11**.</span></span> <span data-ttu-id="479f2-187">docker-compose dosyası Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="479f2-187">docker-compose files in Visual Studio 2017</span></span>

<span data-ttu-id="479f2-188">Visual Studio Code veya Sublime, gibi herhangi bir düzenleyici ile docker-compose dosyaları düzenleyin ve uygulamayı çalıştırın docker-compose up komutu.</span><span class="sxs-lookup"><span data-stu-id="479f2-188">You can edit the docker-compose files with any editor, like Visual Studio Code or Sublime, and run the application with the docker-compose up command.</span></span>

<span data-ttu-id="479f2-189">Kural gereği, docker-compose.yml dosyasını temel yapılandırma ve diğer statik ayarlarını içerir.</span><span class="sxs-lookup"><span data-stu-id="479f2-189">By convention, the docker-compose.yml file contains your base configuration and other static settings.</span></span> <span data-ttu-id="479f2-190">Hizmet yapılandırması, hedeflediğiniz dağıtım ortamı bağlı olarak değiştirmemelisiniz anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="479f2-190">That means that the service configuration should not change depending on the deployment environment you are targeting.</span></span>

<span data-ttu-id="479f2-191">Adından da anlaşılacağı gibi docker-compose.override.yml dosyası, dağıtım ortamınıza bağlıdır yapılandırma gibi temel yapılandırma geçersiz yapılandırma ayarlarını içerir.</span><span class="sxs-lookup"><span data-stu-id="479f2-191">The docker-compose.override.yml file, as its name suggests, contains configuration settings that override the base configuration, such as configuration that depends on the deployment environment.</span></span> <span data-ttu-id="479f2-192">Ayrıca, farklı adlara sahip birden fazla geçersiz kılma dosyası olabilir.</span><span class="sxs-lookup"><span data-stu-id="479f2-192">You can have multiple override files with different names also.</span></span> <span data-ttu-id="479f2-193">Geçersiz kılma dosyalar genellikle uygulama ancak belirli bir ortam veya bir dağıtım için gerekli ek bilgileri içerir.</span><span class="sxs-lookup"><span data-stu-id="479f2-193">The override files usually contain additional information needed by the application but specific to an environment or to a deployment.</span></span>

#### <a name="targeting-multiple-environments"></a><span data-ttu-id="479f2-194">Birden çok ortama hedefleme</span><span class="sxs-lookup"><span data-stu-id="479f2-194">Targeting multiple environments</span></span>

<span data-ttu-id="479f2-195">Tipik bir kullanım örneği olan birden çok tanımlarken compose dosyaları, üretim gibi birden çok ortamı hazırlama, CI veya geliştirme hedefleyebilir.</span><span class="sxs-lookup"><span data-stu-id="479f2-195">A typical use case is when you define multiple compose files so you can target multiple environments, like production, staging, CI, or development.</span></span> <span data-ttu-id="479f2-196">Bu farklar desteklemek için Şekil 6-12'de gösterildiği gibi birden çok dosyalarına oluşturma yapılandırmanızı bölebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="479f2-196">To support these differences, you can split your Compose configuration into multiple files, as shown in Figure 6-12.</span></span>

![Farklı ortamlar işlemek için birden fazla docker compose\*.fml dosyaları birleştirebilirsiniz.](./media/image13.png)

<span data-ttu-id="479f2-198">**Şekil 6-12**.</span><span class="sxs-lookup"><span data-stu-id="479f2-198">**Figure 6-12**.</span></span> <span data-ttu-id="479f2-199">Geçersiz kılma değerleri temel docker-compose.yml dosyasındaki dosyaları birden çok docker-compose</span><span class="sxs-lookup"><span data-stu-id="479f2-199">Multiple docker-compose files overriding values in the base docker-compose.yml file</span></span>

<span data-ttu-id="479f2-200">Temel docker-compose.yml dosyası ile başlayın.</span><span class="sxs-lookup"><span data-stu-id="479f2-200">You start with the base docker-compose.yml file.</span></span> <span data-ttu-id="479f2-201">Bu temel dosya ortamına bağlı olarak değiştirmeyin temel ya da statik yapılandırma ayarlarını içeren gerekir.</span><span class="sxs-lookup"><span data-stu-id="479f2-201">This base file has to contain the base or static configuration settings that do not change depending on the environment.</span></span> <span data-ttu-id="479f2-202">Örneğin, hizmetine taban dosyası olarak (daha az Hizmetleri ile Basitleştirilmiş) aşağıdaki docker-compose.yml dosyası vardır.</span><span class="sxs-lookup"><span data-stu-id="479f2-202">For example, the eShopOnContainers has the following docker-compose.yml file (simplified with less services) as the base file.</span></span>

```yml
#docker-compose.yml (Base)
version: '3.4'
services:
  basket.api:
    image: eshop/basket.api:${TAG:-latest}
    build:
      context: .
      dockerfile: src/Services/Basket/Basket.API/Dockerfile    
    depends_on:
      - basket.data
      - identity.api
      - rabbitmq

  catalog.api:
    image: eshop/catalog.api:${TAG:-latest}
    build:
      context: .
      dockerfile: src/Services/Catalog/Catalog.API/Dockerfile    
    depends_on:
      - sql.data
      - rabbitmq

  marketing.api:
    image: eshop/marketing.api:${TAG:-latest}
    build:
      context: .
      dockerfile: src/Services/Marketing/Marketing.API/Dockerfile    
    depends_on:
      - sql.data
      - nosql.data
      - identity.api
      - rabbitmq

  webmvc:
    image: eshop/webmvc:${TAG:-latest}
    build:
      context: .
      dockerfile: src/Web/WebMVC/Dockerfile    
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

<span data-ttu-id="479f2-203">Temel docker-compose.yml dosyasındaki değerleri nedeniyle farklı bir hedef dağıtım ortamlarının değiştirmemesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="479f2-203">The values in the base docker-compose.yml file should not change because of different target deployment environments.</span></span>

<span data-ttu-id="479f2-204">Örneğin, webmvc hizmet tanımı üzerinde odaklanmak, nasıl bu bilgileri çok hedefleyen hangi ortamı ne olursa olsun aynıdır görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="479f2-204">If you focus on the webmvc service definition, for instance, you can see how that information is much the same no matter what environment you might be targeting.</span></span> <span data-ttu-id="479f2-205">Aşağıdaki bilgileri vardır:</span><span class="sxs-lookup"><span data-stu-id="479f2-205">You have the following information:</span></span>

-   <span data-ttu-id="479f2-206">Hizmet adı: webmvc.</span><span class="sxs-lookup"><span data-stu-id="479f2-206">The service name: webmvc.</span></span>

-   <span data-ttu-id="479f2-207">Kapsayıcının özel görüntü: Elektronik Mağaza/webmvc.</span><span class="sxs-lookup"><span data-stu-id="479f2-207">The container’s custom image: eshop/webmvc.</span></span>

-   <span data-ttu-id="479f2-208">Kullanmak için hangi Dockerfile belirten özel Docker görüntüsü oluşturmak için komutu.</span><span class="sxs-lookup"><span data-stu-id="479f2-208">The command to build the custom Docker image, indicating which Dockerfile to use.</span></span>

-   <span data-ttu-id="479f2-209">Bağımlılıkları diğer hizmetleri, bir bağımlılık kapsayıcıları başlatılıncaya kadar bu kapsayıcı başlamaz.</span><span class="sxs-lookup"><span data-stu-id="479f2-209">Dependencies on other services, so this container does not start until the other dependency containers have started.</span></span>

<span data-ttu-id="479f2-210">Ek yapılandırma olabilir, ancak önemli temel docker-compose.yml dosyasında, yalnızca ortamlar arasında ortak olan bilgiyi ayarlamak istediğiniz noktasıdır.</span><span class="sxs-lookup"><span data-stu-id="479f2-210">You can have additional configuration, but the important point is that in the base docker-compose.yml file, you just want to set the information that is common across environments.</span></span> <span data-ttu-id="479f2-211">Ardından docker-compose.override.yml veya benzer dosyaları üretim ya da hazırlık, her ortam için belirli yapılandırma yerleştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="479f2-211">Then in the docker-compose.override.yml or similar files for production or staging, you should place configuration that is specific for each environment.</span></span>

<span data-ttu-id="479f2-212">Genellikle, docker-compose.override.yml hizmetine aşağıdaki örnekte olduğu gibi geliştirme ortamınız için kullanılır:</span><span class="sxs-lookup"><span data-stu-id="479f2-212">Usually, the docker-compose.override.yml is used for your development environment, as in the following example from eShopOnContainers:</span></span>

```yml
#docker-compose.override.yml (Extended config for DEVELOPMENT env.)
version: '3.4'

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
      - PicBaseUrl=${ESHOP_AZURE_STORAGE_CATALOG_URL:-http://localhost:5202/api/v1/catalog/items/[0]/pic/}   
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
      - PurchaseUrl=http://webshoppingapigw
      - IdentityUrl=http://10.0.75.1:5105
      - MarketingUrl=http://webmarketingapigw
      - CatalogUrlHC=http://catalog.api/hc
      - OrderingUrlHC=http://ordering.api/hc
      - IdentityUrlHC=http://identity.api/hc
      - BasketUrlHC=http://basket.api/hc
      - MarketingUrlHC=http://marketing.api/hc
      - PaymentUrlHC=http://payment.api/hc
      - SignalrHubUrl=http://${ESHOP_EXTERNAL_DNS_NAME_OR_IP}:5202
      - UseCustomizationData=True
      - ApplicationInsights__InstrumentationKey=${INSTRUMENTATION_KEY}
      - OrchestratorType=${ORCHESTRATOR_TYPE}
      - UseLoadTest=${USE_LOADTEST:-False}
    ports:
      - "5100:80"
  sql.data:
    environment:
      - SA_PASSWORD=Pass@word
      - ACCEPT_EULA=Y
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

<span data-ttu-id="479f2-213">Bu örnekte, geliştirme geçersiz kılma yapılandırmasını konağa bazı bağlantı noktalarını kullanıma sunar, ortam değişkenlerini tanımlar URL'lerini yönlendirmek ve geliştirme ortamı için bağlantı dizelerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="479f2-213">In this example, the development override configuration exposes some ports to the host, defines environment variables with redirect URLs, and specifies connection strings for the development environment.</span></span> <span data-ttu-id="479f2-214">Bu ayarlar, tüm yeni geliştirme ortamına yöneliktir.</span><span class="sxs-lookup"><span data-stu-id="479f2-214">These settings are all just for the development environment.</span></span>

<span data-ttu-id="479f2-215">Çalıştırdığınızda `docker-compose up` (veya Visual Studio'dan başlatmak), her iki dosya birleştirme gibi komut geçersiz kılmaları otomatik olarak okur.</span><span class="sxs-lookup"><span data-stu-id="479f2-215">When you run `docker-compose up` (or launch it from Visual Studio), the command reads the overrides automatically as if it were merging both files.</span></span>

<span data-ttu-id="479f2-216">Farklı yapılandırma değerleri, bağlantı noktası veya bağlantı dizeleri üretim ortamı için başka bir Compose dosyasının istediğinizi varsayalım.</span><span class="sxs-lookup"><span data-stu-id="479f2-216">Suppose that you want another Compose file for the production environment, with different configuration values, ports or connection strings.</span></span> <span data-ttu-id="479f2-217">Adlı bir dosya gibi başka bir geçersiz kılma dosyası oluşturabilirsiniz `docker-compose.prod.yml` farklı ayarlar ve ortam değişkenleri.</span><span class="sxs-lookup"><span data-stu-id="479f2-217">You can create another override file, like file named `docker-compose.prod.yml` with different settings and environment variables.</span></span>  <span data-ttu-id="479f2-218">Bu dosyayı farklı bir Git deposunda depolanabilir veya yönetilen ve farklı bir takım tarafından güvenli hale getirilmiş.</span><span class="sxs-lookup"><span data-stu-id="479f2-218">That file might be stored in a different Git repo or managed and secured by a different team.</span></span>

#### <a name="how-to-deploy-with-a-specific-override-file"></a><span data-ttu-id="479f2-219">Bir özel geçersiz kılma dosyası ile dağıtma</span><span class="sxs-lookup"><span data-stu-id="479f2-219">How to deploy with a specific override file</span></span>

<span data-ttu-id="479f2-220">Farklı ada sahip birden fazla geçersiz kılma dosyası veya bir geçersiz kılma dosyası kullanmak için -f seçeneğiyle kullanabilirsiniz docker-compose komutu ve dosyaları belirtin.</span><span class="sxs-lookup"><span data-stu-id="479f2-220">To use multiple override files, or an override file with a different name, you can use the -f option with the docker-compose command and specify the files.</span></span> <span data-ttu-id="479f2-221">Komut satırında belirtildikleri sırada birleştirmeleri dosyalarını oluşturun.</span><span class="sxs-lookup"><span data-stu-id="479f2-221">Compose merges files in the order they are specified on the command line.</span></span> <span data-ttu-id="479f2-222">Aşağıdaki örnek, geçersiz kılma dosyalarıyla dağıtma gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="479f2-222">The following example shows how to deploy with override files.</span></span>

```
docker-compose -f docker-compose.yml -f docker-compose.prod.yml up -d
```

#### <a name="using-environment-variables-in-docker-compose-files"></a><span data-ttu-id="479f2-223">Ortam değişkenlerini kullanarak içinde docker-compose dosyası</span><span class="sxs-lookup"><span data-stu-id="479f2-223">Using environment variables in docker-compose files</span></span>

<span data-ttu-id="479f2-224">Biz önceki örneklerde gösterildiği gibi ortam değişkenlerinden yapılandırma bilgilerini almak için özellikle de üretim ortamlarında, kullanışlı.</span><span class="sxs-lookup"><span data-stu-id="479f2-224">It is convenient, especially in production environments, to be able to get configuration information from environment variables, as we have shown in previous examples.</span></span> <span data-ttu-id="479f2-225">Bir ortam değişkeni kullanarak söz dizimi $ docker-compose dosyalarınızda başvurabilirsiniz {MY\_VAR}.</span><span class="sxs-lookup"><span data-stu-id="479f2-225">You can reference an environment variable in your docker-compose files using the syntax ${MY\_VAR}.</span></span> <span data-ttu-id="479f2-226">Aşağıdaki satırı bir docker compose.prod.yml dosyasından bir ortam değişkeninin değerini yapmayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="479f2-226">The following line from a docker-compose.prod.yml file shows how to reference the value of an environment variable.</span></span>

```yml
IdentityUrl=http://${ESHOP_PROD_EXTERNAL_DNS_NAME_OR_IP}:5105
```

<span data-ttu-id="479f2-227">Ortam değişkenlerini oluşturuldu ve ana bilgisayar ortamına bağlı olarak, farklı şekillerde başlatıldı (Linux, Windows, bulut kümesine, vs.).</span><span class="sxs-lookup"><span data-stu-id="479f2-227">Environment variables are created and initialized in different ways, depending on your host environment (Linux, Windows, Cloud cluster, etc.).</span></span> <span data-ttu-id="479f2-228">Ancak, uygun bir yaklaşım bir .env dosyasında kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="479f2-228">However, a convenient approach is to use an .env file.</span></span> <span data-ttu-id="479f2-229">.Env dosyasında varsayılan ortam değişkenleri bildirme docker-compose dosyalarını destekler.</span><span class="sxs-lookup"><span data-stu-id="479f2-229">The docker-compose files support declaring default environment variables in the .env file.</span></span> <span data-ttu-id="479f2-230">Bu değerler ortam değişkenleri için varsayılan değerlerdir.</span><span class="sxs-lookup"><span data-stu-id="479f2-230">These values for the environment variables are the default values.</span></span> <span data-ttu-id="479f2-231">Ancak, her ortamlarınızda (ana bilgisayar işletim sistemi veya ortam değişkenlerini kümenizden) tanımlamış olabileceği değerlere göre kılınabilir.</span><span class="sxs-lookup"><span data-stu-id="479f2-231">But they can be overridden by the values you might have defined in each of your environments (host OS or environment variables from your cluster).</span></span> <span data-ttu-id="479f2-232">.Env dosyasında bu klasöre yerleştirdiğiniz yere docker-compose komutu yürütülmediyse.</span><span class="sxs-lookup"><span data-stu-id="479f2-232">You place this .env file in the folder where the docker-compose command is executed from.</span></span>

<span data-ttu-id="479f2-233">Aşağıdaki örnek, bir .env dosyasında gibi gösterir [.env](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/.env) hizmetine uygulamanın dosyası.</span><span class="sxs-lookup"><span data-stu-id="479f2-233">The following example shows an .env file like the [.env](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/.env) file for the eShopOnContainers application.</span></span>

```
# .env file

ESHOP_EXTERNAL_DNS_NAME_OR_IP=localhost

ESHOP_PROD_EXTERNAL_DNS_NAME_OR_IP=10.121.122.92
```

<span data-ttu-id="479f2-234">Docker-compose bekliyor biçiminde bir .env dosyasında her satırı \<değişkeni\>=\<değer\>.</span><span class="sxs-lookup"><span data-stu-id="479f2-234">Docker-compose expects each line in an .env file to be in the format \<variable\>=\<value\>.</span></span>

<span data-ttu-id="479f2-235">Çalışma zamanı ortamında her zaman ayarlanan değerleri içinde .env dosyasında tanımlı değerlerin üzerine yazılacağını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="479f2-235">Note that the values set in the runtime environment always override the values defined inside the .env file.</span></span> <span data-ttu-id="479f2-236">Benzer şekilde, geçirilen komut satırı komut bağımsız değişkenlerinin değerleri de .env dosyasında ayarlanan varsayılan değerlerini geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="479f2-236">In a similar way, values passed via command-line command arguments also override the default values set in the .env file.</span></span>

#### <a name="additional-resources"></a><span data-ttu-id="479f2-237">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="479f2-237">Additional resources</span></span>

-   <span data-ttu-id="479f2-238">**Genel Bakış docker Compose**</span><span class="sxs-lookup"><span data-stu-id="479f2-238">**Overview of Docker Compose**</span></span> <br/>
    [*https://docs.docker.com/compose/overview/*](https://docs.docker.com/compose/overview/)

-   <span data-ttu-id="479f2-239">**Birden çok Compose dosyaları**</span><span class="sxs-lookup"><span data-stu-id="479f2-239">**Multiple Compose files**</span></span> <br/>
    [*https://docs.docker.com/compose/extends/\#multiple-compose-files*](https://docs.docker.com/compose/extends/#multiple-compose-files)

### <a name="building-optimized-aspnet-core-docker-images"></a><span data-ttu-id="479f2-240">ASP.NET Core Docker görüntüleri oluşturma en iyi duruma getirilmiş</span><span class="sxs-lookup"><span data-stu-id="479f2-240">Building optimized ASP.NET Core Docker images</span></span>

<span data-ttu-id="479f2-241">Internet kaynaklarında Docker ve .NET Core araştırıyorsanız, Basitlik, bir kapsayıcıya kaynağınızı kopyalayarak bir Docker görüntüsü oluşturma gösteren dockerfile'ları bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="479f2-241">If you are exploring Docker and .NET Core on sources on the Internet, you will find Dockerfiles that demonstrate the simplicity of building a Docker image by copying your source into a container.</span></span> <span data-ttu-id="479f2-242">Bu örnekler, basit bir yapılandırma öğesini kullanarak bir Docker görüntüsü, uygulamanızla birlikte paketlenmiş ortamıyla sağlayabilirsiniz önerin.</span><span class="sxs-lookup"><span data-stu-id="479f2-242">These examples suggest that by using a simple configuration, you can have a Docker image with the environment packaged with your application.</span></span> <span data-ttu-id="479f2-243">Aşağıdaki örnek, basit bir Dockerfile içinde bu damarlı gösterir.</span><span class="sxs-lookup"><span data-stu-id="479f2-243">The following example shows a simple Dockerfile in this vein.</span></span>

```
FROM microsoft/dotnet
WORKDIR /app
ENV ASPNETCORE_URLS http://+:80
EXPOSE 80
COPY . .
RUN dotnet restore
ENTRYPOINT ["dotnet", "run"]
```

<span data-ttu-id="479f2-244">Böyle bir Dockerfile çalışır.</span><span class="sxs-lookup"><span data-stu-id="479f2-244">A Dockerfile like this will work.</span></span> <span data-ttu-id="479f2-245">Ancak, özellikle de üretim görüntülerinin görüntülerinizi önemli ölçüde iyileştirebilir.</span><span class="sxs-lookup"><span data-stu-id="479f2-245">However, you can substantially optimize your images, especially your production images.</span></span>

<span data-ttu-id="479f2-246">Kapsayıcı ve mikro hizmetler modeli sürekli kapsayıcıları başlıyor.</span><span class="sxs-lookup"><span data-stu-id="479f2-246">In the container and microservices model, you are constantly starting containers.</span></span> <span data-ttu-id="479f2-247">Kapsayıcıları kullanarak normal şekilde kapsayıcı atılabilir olduğundan Uyuyan bir kapsayıcı yeniden başlatmaz.</span><span class="sxs-lookup"><span data-stu-id="479f2-247">The typical way of using containers does not restart a sleeping container, because the container is disposable.</span></span> <span data-ttu-id="479f2-248">Düzenleyiciler (gibi Kubernetes ve Azure Service Fabric) yalnızca görüntüleri yeni bir örneğini oluşturun.</span><span class="sxs-lookup"><span data-stu-id="479f2-248">Orchestrators (like Kubernetes and Azure Service Fabric) simply create new instances of images.</span></span> <span data-ttu-id="479f2-249">Ne bu örnekleme işlemi daha hızlı olacak şekilde nasıl yapılandırıldığında, uygulama ön derleme tarafından en iyi duruma getirme gerektiğini anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="479f2-249">What this means is that you would need to optimize by precompiling the application when it is built so the instantiation process will be faster.</span></span> <span data-ttu-id="479f2-250">Kapsayıcı başlatıldığında, çalıştırmaya hazır olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="479f2-250">When the container is started, it should be ready to run.</span></span> <span data-ttu-id="479f2-251">Olmayan geri yükleme ve çalışma zamanında derleme kullandığınızdan `dotnet restore` ve `dotnet build` dotnet CLI komutları bu, .NET Core ve Docker birçok blog gönderileri gördüğünüz gibi.</span><span class="sxs-lookup"><span data-stu-id="479f2-251">You should not restore and compile at run time, using `dotnet restore` and `dotnet build` commands from the dotnet CLI that, as you see in many blog posts about .NET Core and Docker.</span></span>

<span data-ttu-id="479f2-252">.NET ekibi .NET Core ve ASP.NET Core kapsayıcı iyileştirilmiş bir çerçeve yapmak için önemli işleri yapmak.</span><span class="sxs-lookup"><span data-stu-id="479f2-252">The .NET team has been doing important work to make .NET Core and ASP.NET Core a container-optimized framework.</span></span> <span data-ttu-id="479f2-253">Yalnızca .NET Core küçük bellek Ayak izi ile basit bir çerçeve olan; Takım üç ana senaryo için en iyi duruma getirilmiş Docker görüntüleri odaklanan ve bunları Docker Hub kayıt defterinde yayımlanan <span class="underline">microsoft/dotnet</span>, sürüm 2.1 ile başlangıç:</span><span class="sxs-lookup"><span data-stu-id="479f2-253">Not only is .NET Core a lightweight framework with a small memory footprint; the team has focused on optimized Docker images for three main scenarios and published them in the Docker Hub registry at <span class="underline">microsoft/dotnet</span>, beginning with version 2.1:</span></span>

1.  <span data-ttu-id="479f2-254">**Geliştirme**: öncelik yeteneği hızla olduğu interate ve hata ayıklama değişiklikleri ve boyutu ikincil.</span><span class="sxs-lookup"><span data-stu-id="479f2-254">**Development**: Where the priority is the ability to quickly interate and debug changes and size is secondary.</span></span>

2.  <span data-ttu-id="479f2-255">**Derleme**: öncelikli uygulama derlemek ve ikili dosyalar ve ikili dosyaları iyileştirmek için diğer bağımlılıklar içerir.</span><span class="sxs-lookup"><span data-stu-id="479f2-255">**Build**: The priority is compiling the application and includes binaries and other dependencies to optimize binaries.</span></span>

3.  <span data-ttu-id="479f2-256">**Üretim**: odağı hızlı dağıtma ve kapsayıcılar başlangıç olduğunda, böylece bu görüntüleri ikili dosyaları ve uygulamayı çalıştırmak için içerik nedded ile sınırlıdır.</span><span class="sxs-lookup"><span data-stu-id="479f2-256">**Production**: Where the focus is fast deploying and starting of containers, so these images are limited to the binaries and the content nedded to run the application.</span></span>

<span data-ttu-id="479f2-257">Bunu başarmak için .NET ekibi üç temel çeşitlere sağlayan [microsoft/dotnet](https://hub.docker.com/r/microsoft/dotnet/) (en Docker hub'ı):</span><span class="sxs-lookup"><span data-stu-id="479f2-257">To achieve this, the .NET team is providing three basic variants in [microsoft/dotnet](https://hub.docker.com/r/microsoft/dotnet/) (at Docker Hub):</span></span>

1.  <span data-ttu-id="479f2-258">**SDK'sı**: geliştirme ve derleme senaryolar için.</span><span class="sxs-lookup"><span data-stu-id="479f2-258">**sdk**: for the development and build scenarios.</span></span>
2.  <span data-ttu-id="479f2-259">**çalışma zamanı**: üretim senaryosu için ve</span><span class="sxs-lookup"><span data-stu-id="479f2-259">**runtime**: for the production scenario and</span></span>
3.  <span data-ttu-id="479f2-260">**çalışma zamanı deps**: üretim bir senaryo için [kendi içindeki uygulamaları](https://docs.microsoft.com/dotnet/core/deploying/index#self-contained-deployments-scd).</span><span class="sxs-lookup"><span data-stu-id="479f2-260">**runtime-deps**: for the production scenario of [self-contained applications](https://docs.microsoft.com/dotnet/core/deploying/index#self-contained-deployments-scd).</span></span>

<span data-ttu-id="479f2-261">Çalışma zamanı görüntüleri de aspnetcore otomatik ayarı sağlar\_URL'ler 80 numaralı bağlantı noktasını ve daha hızlı başlatma alınırken yardımcı olmak için derleme; öncesi ngend önbellek.</span><span class="sxs-lookup"><span data-stu-id="479f2-261">Runtime images also provides automatic setting of aspnetcore\_urls to port 80 and the pre-ngend cache of assemblies; to help in getting faster startup.</span></span>

#### <a name="additional-resources"></a><span data-ttu-id="479f2-262">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="479f2-262">Additional resources</span></span>

-   <span data-ttu-id="479f2-263">**ASP.NET Core ile Docker görüntü oluşturma en iyi duruma getirilmiş**</span><span class="sxs-lookup"><span data-stu-id="479f2-263">**Building Optimized Docker Images with ASP.NET Core**</span></span> <br/>
    [*https://blogs.msdn.microsoft.com/stevelasker/2016/09/29/building-optimized-docker-images-with-asp-net-core/*](https://blogs.msdn.microsoft.com/stevelasker/2016/09/29/building-optimized-docker-images-with-asp-net-core/)

-   <span data-ttu-id="479f2-264">**.NET Core Uygulamaları için Docker Görüntülerinizi Derleme**</span><span class="sxs-lookup"><span data-stu-id="479f2-264">**Building Docker Images for .NET Core Applications**</span></span> <br/>
    [*https://docs.microsoft.com/en-us/dotnet/core/docker/building-net-docker-images*](https://docs.microsoft.com/en-us/dotnet/core/docker/building-net-docker-images)

>[!div class="step-by-step"]
<span data-ttu-id="479f2-265">[Önceki](data-driven-crud-microservice.md)
[İleri](database-server-container.md)</span><span class="sxs-lookup"><span data-stu-id="479f2-265">[Previous](data-driven-crud-microservice.md)
[Next](database-server-container.md)</span></span>
