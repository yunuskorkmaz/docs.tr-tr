---
title: docker-compose.yml ile çok kapsayıcılı uygulamanızı tanımlama
description: Docker-compose.yml ile çok konteynerli bir uygulama için mikrohizmetler kompozisyonu nasıl belirtilir.
ms.date: 01/30/2020
ms.openlocfilehash: 86d6feda343df7f4b72374f93fc45b3246780cdf
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "77502464"
---
# <a name="defining-your-multi-container-application-with-docker-composeyml"></a><span data-ttu-id="16913-103">docker-compose.yml ile çok kapsayıcılı uygulamanızı tanımlama</span><span class="sxs-lookup"><span data-stu-id="16913-103">Defining your multi-container application with docker-compose.yml</span></span>

<span data-ttu-id="16913-104">Bu kılavuzda [docker-compose.yml](https://docs.docker.com/compose/compose-file/) dosyası Adım 4 bölümünde [tanıtıldı. Çok konteynerli Docker uygulaması oluştururken servislerinizi docker-compose.yml olarak tanımlayın.](../docker-application-development-process/docker-app-development-workflow.md#step-4-define-your-services-in-docker-composeyml-when-building-a-multi-container-docker-application)</span><span class="sxs-lookup"><span data-stu-id="16913-104">In this guide, the [docker-compose.yml](https://docs.docker.com/compose/compose-file/) file was introduced in the section [Step 4. Define your services in docker-compose.yml when building a multi-container Docker application](../docker-application-development-process/docker-app-development-workflow.md#step-4-define-your-services-in-docker-composeyml-when-building-a-multi-container-docker-application).</span></span> <span data-ttu-id="16913-105">Ancak, daha ayrıntılı olarak araştırılmaya değer docker-compose dosyaları kullanmak için ek yollar vardır.</span><span class="sxs-lookup"><span data-stu-id="16913-105">However, there are additional ways to use the docker-compose files that are worth exploring in further detail.</span></span>

<span data-ttu-id="16913-106">Örneğin, docker-compose.yml dosyasında çok kapsayıcı uygulamanızı nasıl dağıtmak istediğinizi açıkça açıklayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="16913-106">For example, you can explicitly describe how you want to deploy your multi-container application in the docker-compose.yml file.</span></span> <span data-ttu-id="16913-107">İsteğe bağlı olarak, özel Docker resimlerinizi nasıl oluşturacağınızaçıklayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="16913-107">Optionally, you can also describe how you are going to build your custom Docker images.</span></span> <span data-ttu-id="16913-108">(Özel Docker görüntüleri de Docker CLI ile oluşturulabilir.)</span><span class="sxs-lookup"><span data-stu-id="16913-108">(Custom Docker images can also be built with the Docker CLI.)</span></span>

<span data-ttu-id="16913-109">Temel olarak, dağıtmak istediğiniz kapsayıcıların her birini ve her kapsayıcı dağıtımı için belirli özellikleri tanımlarsınız.</span><span class="sxs-lookup"><span data-stu-id="16913-109">Basically, you define each of the containers you want to deploy plus certain characteristics for each container deployment.</span></span> <span data-ttu-id="16913-110">Çok kapsayıcılı dağıtım açıklama dosyasına sahip olduktan sonra, tüm çözümü [docker-com to](https://docs.docker.com/compose/overview/) CLI komutu tarafından düzenlenmiş tek bir eylemde dağıtabilir veya Visual Studio'dan saydam olarak dağıtabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="16913-110">Once you have a multi-container deployment description file, you can deploy the whole solution in a single action orchestrated by the [docker-compose up](https://docs.docker.com/compose/overview/) CLI command, or you can deploy it transparently from Visual Studio.</span></span> <span data-ttu-id="16913-111">Aksi takdirde, komut satırından `docker run` komutu kullanarak konteyner-by-konteyner birden çok adımda dağıtmak için Docker CLI kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="16913-111">Otherwise, you would need to use the Docker CLI to deploy container-by-container in multiple steps by using the `docker run` command from the command line.</span></span> <span data-ttu-id="16913-112">Bu nedenle, docker-compose.yml'de tanımlanan her hizmet tam olarak bir görüntü veya yapı belirtmelidir.</span><span class="sxs-lookup"><span data-stu-id="16913-112">Therefore, each service defined in docker-compose.yml must specify exactly one image or build.</span></span> <span data-ttu-id="16913-113">Diğer anahtarlar isteğe bağlıdır ve `docker run` komut satırı benzerlerine benzerdir.</span><span class="sxs-lookup"><span data-stu-id="16913-113">Other keys are optional, and are analogous to their `docker run` command-line counterparts.</span></span>

<span data-ttu-id="16913-114">Aşağıdaki YAML kodu eShopOnContainers örnek için olası bir küresel ama tek docker-compose.yml dosyasının tanımıdır.</span><span class="sxs-lookup"><span data-stu-id="16913-114">The following YAML code is the definition of a possible global but single docker-compose.yml file for the eShopOnContainers sample.</span></span> <span data-ttu-id="16913-115">Bu eShopOnContainers gerçek docker-beste dosyası değildir.</span><span class="sxs-lookup"><span data-stu-id="16913-115">This is not the actual docker-compose file from eShopOnContainers.</span></span> <span data-ttu-id="16913-116">Bunun yerine, daha sonra açıklanacaktır docker-compose dosyaları ile çalışmak için en iyi yol değildir tek bir dosya, basitleştirilmiş ve konsolide sürümüdür.</span><span class="sxs-lookup"><span data-stu-id="16913-116">Instead, it is a simplified and consolidated version in a single file, which is not the best way to work with docker-compose files, as will be explained later.</span></span>

```yml
version: '3.4'

services:
  webmvc:
    image: eshop/webmvc
    environment:
      - CatalogUrl=http://catalog-api
      - OrderingUrl=http://ordering-api
      - BasketUrl=http://basket-api
    ports:
      - "5100:80"
    depends_on:
      - catalog-api
      - ordering-api
      - basket-api

  catalog-api:
    image: eshop/catalog-api
    environment:
      - ConnectionString=Server=sqldata;Initial Catalog=CatalogData;User Id=sa;Password=your@password
    expose:
      - "80"
    ports:
      - "5101:80"
    #extra hosts can be used for standalone SQL Server or services at the dev PC
    extra_hosts:
      - "CESARDLSURFBOOK:10.0.75.1"
    depends_on:
      - sqldata

  ordering-api:
    image: eshop/ordering-api
    environment:
      - ConnectionString=Server=sqldata;Database=Services.OrderingDb;User Id=sa;Password=your@password
    ports:
      - "5102:80"
    #extra hosts can be used for standalone SQL Server or services at the dev PC
    extra_hosts:
      - "CESARDLSURFBOOK:10.0.75.1"
    depends_on:
      - sqldata

  basket-api:
    image: eshop/basket-api
    environment:
      - ConnectionString=sqldata
    ports:
      - "5103:80"
    depends_on:
      - sqldata

  sqldata:
    environment:
      - SA_PASSWORD=your@password
      - ACCEPT_EULA=Y
    ports:
      - "5434:1433"

  basketdata:
    image: redis
```

<span data-ttu-id="16913-117">Bu dosyadaki temel anahtar hizmetlerdir.</span><span class="sxs-lookup"><span data-stu-id="16913-117">The root key in this file is services.</span></span> <span data-ttu-id="16913-118">Bu anahtarın altında, `docker-compose up` bu docker-compose.yml dosyasını kullanarak komutu çalıştırdığınızda veya Visual Studio'dan dağıtırken dağıtmak ve çalıştırmak istediğiniz hizmetleri tanımlarsınız.</span><span class="sxs-lookup"><span data-stu-id="16913-118">Under that key, you define the services you want to deploy and run when you execute the `docker-compose up` command or when you deploy from Visual Studio by using this docker-compose.yml file.</span></span> <span data-ttu-id="16913-119">Bu durumda, docker-compose.yml dosyası, aşağıdaki tabloda açıklandığı gibi, tanımlanan birden çok hizmete sahiptir.</span><span class="sxs-lookup"><span data-stu-id="16913-119">In this case, the docker-compose.yml file has multiple services defined, as described in the following table.</span></span>

| <span data-ttu-id="16913-120">Hizmet adı</span><span class="sxs-lookup"><span data-stu-id="16913-120">Service name</span></span> | <span data-ttu-id="16913-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="16913-121">Description</span></span> |
|--------------|-------------|
| <span data-ttu-id="16913-122">webmvc</span><span class="sxs-lookup"><span data-stu-id="16913-122">webmvc</span></span>       | <span data-ttu-id="16913-123">Sunucu tarafındaki C'den mikro hizmetleri tüketen ASP.NET Core MVC uygulamasını içeren konteyner\#</span><span class="sxs-lookup"><span data-stu-id="16913-123">Container including the ASP.NET Core MVC application consuming the microservices from server-side C\#</span></span>|
| <span data-ttu-id="16913-124">katalog-api</span><span class="sxs-lookup"><span data-stu-id="16913-124">catalog-api</span></span>  | <span data-ttu-id="16913-125">Katalog ASP.NET Core Web API microservice dahil Konteyner</span><span class="sxs-lookup"><span data-stu-id="16913-125">Container including the Catalog ASP.NET Core Web API microservice</span></span> |
| <span data-ttu-id="16913-126">sipariş-api</span><span class="sxs-lookup"><span data-stu-id="16913-126">ordering-api</span></span> | <span data-ttu-id="16913-127">Sipariş ASP.NET Core Web API microservice dahil konteyner</span><span class="sxs-lookup"><span data-stu-id="16913-127">Container including the Ordering ASP.NET Core Web API microservice</span></span> |
| <span data-ttu-id="16913-128">sql data</span><span class="sxs-lookup"><span data-stu-id="16913-128">sqldata</span></span>     | <span data-ttu-id="16913-129">Linux için SQL Server çalıştıran, mikrohizmetler veritabanlarını tutan konteyner</span><span class="sxs-lookup"><span data-stu-id="16913-129">Container running SQL Server for Linux, holding the microservices databases</span></span> |
| <span data-ttu-id="16913-130">sepet-api</span><span class="sxs-lookup"><span data-stu-id="16913-130">basket-api</span></span>   | <span data-ttu-id="16913-131">Core Web API microservice ASP.NET Sepetli Konteyner</span><span class="sxs-lookup"><span data-stu-id="16913-131">Container with the Basket ASP.NET Core Web API microservice</span></span> |
| <span data-ttu-id="16913-132">sepet verileri</span><span class="sxs-lookup"><span data-stu-id="16913-132">basketdata</span></span>  | <span data-ttu-id="16913-133">REDIS önbellek hizmetini çalıştıran kapsayıcı, redis önbelleği olarak sepet veritabanı ile</span><span class="sxs-lookup"><span data-stu-id="16913-133">Container running the REDIS cache service, with the basket database as a REDIS cache</span></span> |

### <a name="a-simple-web-service-api-container"></a><span data-ttu-id="16913-134">Basit bir Web Hizmeti API kapsayıcısı</span><span class="sxs-lookup"><span data-stu-id="16913-134">A simple Web Service API container</span></span>

<span data-ttu-id="16913-135">Tek bir kapsayıcı ya odaklanarak, katalog-api konteyner-microservice basit bir tanımı vardır:</span><span class="sxs-lookup"><span data-stu-id="16913-135">Focusing on a single container, the catalog-api container-microservice has a straightforward definition:</span></span>

```yml
  catalog-api:
    image: eshop/catalog-api
    environment:
      - ConnectionString=Server=sqldata;Initial Catalog=CatalogData;User Id=sa;Password=your@password
    expose:
      - "80"
    ports:
      - "5101:80"
    #extra hosts can be used for standalone SQL Server or services at the dev PC
    extra_hosts:
      - "CESARDLSURFBOOK:10.0.75.1"
    depends_on:
      - sqldata
```

<span data-ttu-id="16913-136">Bu kapsayıcı hizmet aşağıdaki temel yapılandırmaya sahiptir:</span><span class="sxs-lookup"><span data-stu-id="16913-136">This containerized service has the following basic configuration:</span></span>

- <span data-ttu-id="16913-137">Bu özel **eshop / katalog-api** görüntü dayanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="16913-137">It is based on the custom **eshop/catalog-api** image.</span></span> <span data-ttu-id="16913-138">Basitlik aşkına, hiçbir yapı: dosyada anahtar ayarı.</span><span class="sxs-lookup"><span data-stu-id="16913-138">For simplicity’s sake, there is no build: key setting in the file.</span></span> <span data-ttu-id="16913-139">Bu, görüntünün daha önce (docker build ile) oluşturulmuş veya herhangi bir Docker kayıt defterinden (docker çekme komutuyla) indirilmiş olması gerektiği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="16913-139">This means that the image must have been previously built (with docker build) or have been downloaded (with the docker pull command) from any Docker registry.</span></span>

- <span data-ttu-id="16913-140">Katalog veri modelini içeren SQL Server örneğine erişmek için Entity Framework tarafından kullanılacak bağlantı dizesiyle ConnectionString adlı bir ortam değişkeni tanımlar.</span><span class="sxs-lookup"><span data-stu-id="16913-140">It defines an environment variable named ConnectionString with the connection string to be used by Entity Framework to access the SQL Server instance that contains the catalog data model.</span></span> <span data-ttu-id="16913-141">Bu durumda, aynı SQL Server kapsayıcıbirden çok veritabanları tutuyor.</span><span class="sxs-lookup"><span data-stu-id="16913-141">In this case, the same SQL Server container is holding multiple databases.</span></span> <span data-ttu-id="16913-142">Bu nedenle, Docker için geliştirme makinenizde daha az belleğe ihtiyacınız var.</span><span class="sxs-lookup"><span data-stu-id="16913-142">Therefore, you need less memory in your development machine for Docker.</span></span> <span data-ttu-id="16913-143">Ancak, her microservice veritabanı için bir SQL Server kapsayıcıdağıtabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="16913-143">However, you could also deploy one SQL Server container for each microservice database.</span></span>

- <span data-ttu-id="16913-144">SQL Server **adı,** Linux için SQL Server örneğini çalıştıran kapsayıcı için kullanılan adla aynı olan sqldata'dır.</span><span class="sxs-lookup"><span data-stu-id="16913-144">The SQL Server name is **sqldata**, which is the same name used for the container that is running the SQL Server instance for Linux.</span></span> <span data-ttu-id="16913-145">Bu uygundur; Bu ad çözünürlüğünü (Docker ana bilgisayarındahil) kullanabilmek, ağ adresini çözecek, böylece diğer kapsayıcılardan erişmekte olduğunuz kapsayıcıların dahili IP'sini bilmeniz gerekmez.</span><span class="sxs-lookup"><span data-stu-id="16913-145">This is convenient; being able to use this name resolution (internal to the Docker host) will resolve the network address so you don’t need to know the internal IP for the containers you are accessing from other containers.</span></span>

<span data-ttu-id="16913-146">Bağlantı dizesi bir ortam değişkeni tarafından tanımlandığından, bu değişkeni farklı bir mekanizma aracılığıyla ve farklı bir zamanda ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="16913-146">Because the connection string is defined by an environment variable, you could set that variable through a different mechanism and at a different time.</span></span> <span data-ttu-id="16913-147">Örneğin, son ana bilgisayarlarda üretime dağıtılırken veya Azure DevOps Hizmetleri'ndeki CI/CD ardışık hatlarınızdan veya tercih ettiğiniz DevOps sisteminden bunu yaparak farklı bir bağlantı dizesi ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="16913-147">For example, you could set a different connection string when deploying to production in the final hosts, or by doing it from your CI/CD pipelines in Azure DevOps Services or your preferred DevOps system.</span></span>

- <span data-ttu-id="16913-148">Docker ana bilgisayar içindeki **katalog-api** hizmetine dahili erişim için bağlantı noktası 80'i ortaya çıkarır.</span><span class="sxs-lookup"><span data-stu-id="16913-148">It exposes port 80 for internal access to the **catalog-api** service within the Docker host.</span></span> <span data-ttu-id="16913-149">Ana bilgisayar şu anda bir Linux VM'dir, çünkü Linux için bir Docker resmine dayanır, ancak bunun yerine kapsayıcıyı Windows görüntüsünde çalışacak şekilde yapılandırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="16913-149">The host is currently a Linux VM because it is based on a Docker image for Linux, but you could configure the container to run on a Windows image instead.</span></span>

- <span data-ttu-id="16913-150">Konteynerüzerindeki 80 portu Docker ana makinedeki (Linux VM) 5101 portuna iletir.</span><span class="sxs-lookup"><span data-stu-id="16913-150">It forwards the exposed port 80 on the container to port 5101 on the Docker host machine (the Linux VM).</span></span>

- <span data-ttu-id="16913-151">Web hizmetini **sqldata** hizmetine (bir kapsayıcıda çalışan Linux veritabanı için SQL Server örneği) bağlar.</span><span class="sxs-lookup"><span data-stu-id="16913-151">It links the web service to the **sqldata** service (the SQL Server instance for Linux database running in a container).</span></span> <span data-ttu-id="16913-152">Bu bağımlılık belirttiğiniz zaman, katalog-api kapsayıcı sqldata kapsayıcısı zaten başlayana kadar başlamaz; katalog-api'nin önce SQL Server veritabanını çalışır hale alması gerektiğinden bu önemlidir.</span><span class="sxs-lookup"><span data-stu-id="16913-152">When you specify this dependency, the catalog-api container will not start until the sqldata container has already started; this is important because catalog-api needs to have the SQL Server database up and running first.</span></span> <span data-ttu-id="16913-153">Ancak, Docker yalnızca kapsayıcı düzeyinde denetlediği için, bu tür kapsayıcı bağımlılığı birçok durumda yeterli değildir.</span><span class="sxs-lookup"><span data-stu-id="16913-153">However, this kind of container dependency is not enough in many cases, because Docker checks only at the container level.</span></span> <span data-ttu-id="16913-154">Bazen hizmet (bu durumda SQL Server) hala hazır olmayabilir, bu nedenle istemci mikro hizmetlerinde üstel geri çekilme ile yeniden deneme mantığını uygulamak tavsiye edilir.</span><span class="sxs-lookup"><span data-stu-id="16913-154">Sometimes the service (in this case SQL Server) might still not be ready, so it is advisable to implement retry logic with exponential backoff in your client microservices.</span></span> <span data-ttu-id="16913-155">Bu şekilde, bir bağımlılık kapsayıcısı kısa bir süre için hazır değilse, uygulama yine de esnek olacaktır.</span><span class="sxs-lookup"><span data-stu-id="16913-155">That way, if a dependency container is not ready for a short time, the application will still be resilient.</span></span>

- <span data-ttu-id="16913-156">Harici sunuculara erişime izin verecek şekilde\_yapılandırılmıştır: Ekstra ana bilgisayar ayarı, geliştirme bilgisayarınızdaki yerel bir SQL Server örneği gibi, Docker ana bilgisayarının dışında harici sunuculara veya makinelere (diğer bir şekilde geliştirme Docker ana bilgisayarı olan varsayılan Linux VM dışında) erişmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="16913-156">It is configured to allow access to external servers: the extra\_hosts setting allows you to access external servers or machines outside of the Docker host (that is, outside the default Linux VM, which is a development Docker host), such as a local SQL Server instance on your development PC.</span></span>

<span data-ttu-id="16913-157">Ayrıca, aşağıdaki bölümlerde `docker-compose.yml` tartışacağız diğer, daha gelişmiş ayarları vardır.</span><span class="sxs-lookup"><span data-stu-id="16913-157">There are also other, more advanced `docker-compose.yml` settings that we'll discuss in the following sections.</span></span>

### <a name="using-docker-compose-files-to-target-multiple-environments"></a><span data-ttu-id="16913-158">Birden çok ortamı hedeflemek için docker oluşturma dosyalarını kullanma</span><span class="sxs-lookup"><span data-stu-id="16913-158">Using docker-compose files to target multiple environments</span></span>

<span data-ttu-id="16913-159">Dosyalar `docker-compose.*.yml` tanım dosyalarıdır ve bu biçimi anlayan birden çok altyapı tarafından kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="16913-159">The `docker-compose.*.yml` files are definition files and can be used by multiple infrastructures that understand that format.</span></span> <span data-ttu-id="16913-160">En basit araç docker-compose komutudur.</span><span class="sxs-lookup"><span data-stu-id="16913-160">The most straightforward tool is the docker-compose command.</span></span>

<span data-ttu-id="16913-161">Bu nedenle, docker-compose komutunu kullanarak aşağıdaki ana senaryoları hedefleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="16913-161">Therefore, by using the docker-compose command you can target the following main scenarios.</span></span>

#### <a name="development-environments"></a><span data-ttu-id="16913-162">Geliştirme ortamları</span><span class="sxs-lookup"><span data-stu-id="16913-162">Development environments</span></span>

<span data-ttu-id="16913-163">Uygulamaları geliştirirken, bir uygulamayı yalıtılmış bir geliştirme ortamında çalıştırabilmek önemlidir.</span><span class="sxs-lookup"><span data-stu-id="16913-163">When you develop applications, it is important to be able to run an application in an isolated development environment.</span></span> <span data-ttu-id="16913-164">Bu ortamı oluşturmak için docker-create CLI komutunu veya kapakların altında docker-create kullanan Visual Studio'yu kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="16913-164">You can use the docker-compose CLI command to create that environment or Visual Studio, which uses docker-compose under the covers.</span></span>

<span data-ttu-id="16913-165">Docker-compose.yml dosyası, uygulamanızın tüm hizmet bağımlılıklarını (diğer hizmetler, önbellek, veritabanları, kuyruklar, vb.) yapılandırmanızı ve belgelemenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="16913-165">The docker-compose.yml file allows you to configure and document all your application’s service dependencies (other services, cache, databases, queues, etc.).</span></span> <span data-ttu-id="16913-166">Docker-create CLI komutunu kullanarak, her bağımlılık için tek bir komutla (docker-create to up) bir veya daha fazla kapsayıcı oluşturabilir ve başlatabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="16913-166">Using the docker-compose CLI command, you can create and start one or more containers for each dependency with a single command (docker-compose up).</span></span>

<span data-ttu-id="16913-167">Docker-compose.yml dosyaları Docker motoru tarafından yorumlanan yapılandırma dosyaları dır, ancak aynı zamanda çoklu konteyner uygulamanızın bileşimi hakkında uygun dokümantasyon dosyaları olarak hizmet vermektedir.</span><span class="sxs-lookup"><span data-stu-id="16913-167">The docker-compose.yml files are configuration files interpreted by Docker engine but also serve as convenient documentation files about the composition of your multi-container application.</span></span>

#### <a name="testing-environments"></a><span data-ttu-id="16913-168">Test ortamları</span><span class="sxs-lookup"><span data-stu-id="16913-168">Testing environments</span></span>

<span data-ttu-id="16913-169">Herhangi bir sürekli dağıtım (CD) veya sürekli tümleştirme (CI) işleminin önemli bir parçası birim testleri ve tümleştirme testleridir.</span><span class="sxs-lookup"><span data-stu-id="16913-169">An important part of any continuous deployment (CD) or continuous integration (CI) process are the unit tests and integration tests.</span></span> <span data-ttu-id="16913-170">Bu otomatik leştirilmiş testler, kullanıcılardan veya uygulamanın verilerindeki herhangi bir değişiklikten etkilenmemesi için yalıtılmış bir ortam gerektirir.</span><span class="sxs-lookup"><span data-stu-id="16913-170">These automated tests require an isolated environment so they are not impacted by the users or any other change in the application’s data.</span></span>

<span data-ttu-id="16913-171">Docker Compose ile, aşağıdaki komutlar gibi komut istemi veya komut komutları birkaç komutları çok kolay bu yalıtılmış ortamı oluşturabilir ve yok:</span><span class="sxs-lookup"><span data-stu-id="16913-171">With Docker Compose, you can create and destroy that isolated environment very easily in a few commands from your command prompt or scripts, like the following commands:</span></span>

```console
docker-compose -f docker-compose.yml -f docker-compose-test.override.yml up -d
./run_unit_tests
docker-compose -f docker-compose.yml -f docker-compose.test.override.yml down
```

#### <a name="production-deployments"></a><span data-ttu-id="16913-172">Üretim dağıtımları</span><span class="sxs-lookup"><span data-stu-id="16913-172">Production deployments</span></span>

<span data-ttu-id="16913-173">Uzak bir Docker Engine dağıtmak için Oluştur'u da kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="16913-173">You can also use Compose to deploy to a remote Docker Engine.</span></span> <span data-ttu-id="16913-174">Tipik bir durum tek bir Docker ana bilgisayar örneğine dağıtmaktır (üretim VM'si veya [Docker Machine](https://docs.docker.com/machine/overview/)ile birlikte verilen sunucu gibi).</span><span class="sxs-lookup"><span data-stu-id="16913-174">A typical case is to deploy to a single Docker host instance (like a production VM or server provisioned with [Docker Machine](https://docs.docker.com/machine/overview/)).</span></span>

<span data-ttu-id="16913-175">Başka bir orchestrator kullanıyorsanız (Azure Hizmet Kumaşı, Kubernetes, vb.), docker-compose.yml'dekigibi kurulum ve meta veri yapılandırma ayarlarını, ancak diğer orkestratörün gerektirdiği biçimde eklemeniz gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="16913-175">If you are using any other orchestrator (Azure Service Fabric, Kubernetes, etc.), you might need to add setup and metadata configuration settings like those in docker-compose.yml, but in the format required by the other orchestrator.</span></span>

<span data-ttu-id="16913-176">Her durumda, docker-compose geliştirme, test ve üretim iş akışları için uygun bir araç ve meta veri biçimidir, ancak üretim iş akışı kullanmakta olduğunuz orkestratöre göre değişiklik gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="16913-176">In any case, docker-compose is a convenient tool and metadata format for development, testing and production workflows, although the production workflow might vary on the orchestrator you are using.</span></span>

### <a name="using-multiple-docker-compose-files-to-handle-several-environments"></a><span data-ttu-id="16913-177">Çeşitli ortamları işlemek için birden çok docker-beste dosyası kullanma</span><span class="sxs-lookup"><span data-stu-id="16913-177">Using multiple docker-compose files to handle several environments</span></span>

<span data-ttu-id="16913-178">Farklı ortamları hedeflerken, birden çok oluşturma dosyası kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="16913-178">When targeting different environments, you should use multiple compose files.</span></span> <span data-ttu-id="16913-179">Bu, ortama bağlı olarak birden çok yapılandırma varyantı oluşturmanıza olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="16913-179">This lets you create multiple configuration variants depending on the environment.</span></span>

#### <a name="overriding-the-base-docker-compose-file"></a><span data-ttu-id="16913-180">Temel docker oluşturma dosyasını geçersiz kılma</span><span class="sxs-lookup"><span data-stu-id="16913-180">Overriding the base docker-compose file</span></span>

<span data-ttu-id="16913-181">Önceki bölümlerde gösterilen basitleştirilmiş örneklerde olduğu gibi tek bir docker-compose.yml dosyası kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="16913-181">You could use a single docker-compose.yml file as in the simplified examples shown in previous sections.</span></span> <span data-ttu-id="16913-182">Ancak, bu çoğu uygulama için önerilmez.</span><span class="sxs-lookup"><span data-stu-id="16913-182">However, that is not recommended for most applications.</span></span>

<span data-ttu-id="16913-183">Varsayılan olarak, Compose iki dosya, bir docker-compose.yml ve isteğe bağlı docker-compose.override.yml dosyaokur.</span><span class="sxs-lookup"><span data-stu-id="16913-183">By default, Compose reads two files, a docker-compose.yml and an optional docker-compose.override.yml file.</span></span> <span data-ttu-id="16913-184">Şekil 6-11'de gösterildiği gibi, Visual Studio'yu kullanırken ve Docker desteğini etkinleştirirken, Visual Studio ayrıca uygulamanın hata ayıklanması için ek bir docker-compose.vs.debug.g.yml dosyası oluşturur, ana çözüm klasöründe obj\\Docker\\ klasöründe bu dosyaya göz atabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="16913-184">As shown in Figure 6-11, when you are using Visual Studio and enabling Docker support, Visual Studio also creates an additional docker-compose.vs.debug.g.yml file for debugging the application, you can take a look at this file in folder obj\\Docker\\ in the main solution folder.</span></span>

![Bir docker oluşturmak proje dosyaların ekran görüntüsü.](./media/multi-container-applications-docker-compose/docker-compose-file-visual-studio.png)

<span data-ttu-id="16913-186">**Şekil 6-11**.</span><span class="sxs-lookup"><span data-stu-id="16913-186">**Figure 6-11**.</span></span> <span data-ttu-id="16913-187">Visual Studio 2019'da docker-compose dosyaları</span><span class="sxs-lookup"><span data-stu-id="16913-187">docker-compose files in Visual Studio 2019</span></span>

<span data-ttu-id="16913-188">**docker-beste** proje dosya yapısı:</span><span class="sxs-lookup"><span data-stu-id="16913-188">**docker-compose** project file structure:</span></span>

- <span data-ttu-id="16913-189">*.dockerignore* - dosyaları yoksaymak için kullanılır</span><span class="sxs-lookup"><span data-stu-id="16913-189">*.dockerignore* - used to ignore files</span></span>
- <span data-ttu-id="16913-190">*docker-compose.yml* - mikrohizmetler oluşturmak için kullanılan</span><span class="sxs-lookup"><span data-stu-id="16913-190">*docker-compose.yml* - used to compose microservices</span></span>
- <span data-ttu-id="16913-191">*docker-compose.override.yml* - mikro hizmetler ortamı yapılandırmak için kullanılan</span><span class="sxs-lookup"><span data-stu-id="16913-191">*docker-compose.override.yml* - used to configure microservices environment</span></span>

<span data-ttu-id="16913-192">Visual Studio Code veya Sublime gibi herhangi bir düzenleyiciyle docker-beste dosyalarını oluşturabilir ve uygulamayı docker-comto komutuyla çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="16913-192">You can edit the docker-compose files with any editor, like Visual Studio Code or Sublime, and run the application with the docker-compose up command.</span></span>

<span data-ttu-id="16913-193">Sözleşmeye göre docker-compose.yml dosyası temel yapılandırmanızı ve diğer statik ayarları içerir.</span><span class="sxs-lookup"><span data-stu-id="16913-193">By convention, the docker-compose.yml file contains your base configuration and other static settings.</span></span> <span data-ttu-id="16913-194">Bu, hizmet yapılandırmasının hedeflediğiniz dağıtım ortamına bağlı olarak değişmemesi gerektiği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="16913-194">That means that the service configuration should not change depending on the deployment environment you are targeting.</span></span>

<span data-ttu-id="16913-195">Docker-compose.override.yml dosyası, adından da anlaşılacağı gibi, dağıtım ortamına bağlı yapılandırma gibi temel yapılandırmayı geçersiz kılınan yapılandırma ayarlarını içerir.</span><span class="sxs-lookup"><span data-stu-id="16913-195">The docker-compose.override.yml file, as its name suggests, contains configuration settings that override the base configuration, such as configuration that depends on the deployment environment.</span></span> <span data-ttu-id="16913-196">Farklı adlar içeren birden çok geçersiz kılma dosyanız da olabilir.</span><span class="sxs-lookup"><span data-stu-id="16913-196">You can have multiple override files with different names also.</span></span> <span data-ttu-id="16913-197">Geçersiz kılma dosyaları genellikle uygulama tarafından gereken ancak bir ortama veya dağıtıma özgü ek bilgiler içerir.</span><span class="sxs-lookup"><span data-stu-id="16913-197">The override files usually contain additional information needed by the application but specific to an environment or to a deployment.</span></span>

#### <a name="targeting-multiple-environments"></a><span data-ttu-id="16913-198">Birden çok ortamı hedefleme</span><span class="sxs-lookup"><span data-stu-id="16913-198">Targeting multiple environments</span></span>

<span data-ttu-id="16913-199">Tipik bir kullanım örneği, üretim, evreleme, CI veya geliştirme gibi birden çok ortamı hedefleyebilmeniz için birden çok oluşturma dosyası tanımladığınız zamandır.</span><span class="sxs-lookup"><span data-stu-id="16913-199">A typical use case is when you define multiple compose files so you can target multiple environments, like production, staging, CI, or development.</span></span> <span data-ttu-id="16913-200">Bu farklılıkları desteklemek için, Şekil 6-12'de gösterildiği gibi, Oluşturma yapılandırmanızı birden çok dosyaya bölebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="16913-200">To support these differences, you can split your Compose configuration into multiple files, as shown in Figure 6-12.</span></span>

![Temel dosyayı geçersiz kılmak için ayarlanmış üç docker-com-files diyagramı.](./media/multi-container-applications-docker-compose/multiple-docker-compose-files-override-base.png)

<span data-ttu-id="16913-202">**Şekil 6-12**.</span><span class="sxs-lookup"><span data-stu-id="16913-202">**Figure 6-12**.</span></span> <span data-ttu-id="16913-203">Temel docker-compose.yml dosyasındaki değerleri geçersiz kılan birden çok docker-compose dosyaları</span><span class="sxs-lookup"><span data-stu-id="16913-203">Multiple docker-compose files overriding values in the base docker-compose.yml file</span></span>

<span data-ttu-id="16913-204">Farklı ortamları işlemek için birden çok docker-compose\*.yml dosyasını birleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="16913-204">You can combine multiple docker-compose\*.yml files to handle different environments.</span></span> <span data-ttu-id="16913-205">Temel docker-compose.yml dosyası ile başlar.</span><span class="sxs-lookup"><span data-stu-id="16913-205">You start with the base docker-compose.yml file.</span></span> <span data-ttu-id="16913-206">Bu temel dosya, ortama bağlı olarak değişmeden temel veya statik yapılandırma ayarlarını içermelidir.</span><span class="sxs-lookup"><span data-stu-id="16913-206">This base file has to contain the base or static configuration settings that do not change depending on the environment.</span></span> <span data-ttu-id="16913-207">Örneğin, eShopOnContainers temel dosya olarak aşağıdaki docker-compose.yml dosyası (daha az hizmet ile basitleştirilmiş) vardır.</span><span class="sxs-lookup"><span data-stu-id="16913-207">For example, the eShopOnContainers has the following docker-compose.yml file (simplified with fewer services) as the base file.</span></span>

```yml
#docker-compose.yml (Base)
version: '3.4'
services:
  basket-api:
    image: eshop/basket-api:${TAG:-latest}
    build:
      context: .
      dockerfile: src/Services/Basket/Basket.API/Dockerfile
    depends_on:
      - basketdata
      - identity-api
      - rabbitmq

  catalog-api:
    image: eshop/catalog-api:${TAG:-latest}
    build:
      context: .
      dockerfile: src/Services/Catalog/Catalog.API/Dockerfile
    depends_on:
      - sqldata
      - rabbitmq

  marketing-api:
    image: eshop/marketing-api:${TAG:-latest}
    build:
      context: .
      dockerfile: src/Services/Marketing/Marketing.API/Dockerfile
    depends_on:
      - sqldata
      - nosqldata
      - identity-api
      - rabbitmq

  webmvc:
    image: eshop/webmvc:${TAG:-latest}
    build:
      context: .
      dockerfile: src/Web/WebMVC/Dockerfile
    depends_on:
      - catalog-api
      - ordering-api
      - identity-api
      - basket-api
      - marketing-api

  sqldata:
    image: mcr.microsoft.com/mssql/server:2017-latest

  nosqldata:
    image: mongo

  basketdata:
    image: redis

  rabbitmq:
    image: rabbitmq:3-management

```

<span data-ttu-id="16913-208">Temel docker-compose.yml dosyasındaki değerler, farklı hedef dağıtım ortamları nedeniyle değişmemelidir.</span><span class="sxs-lookup"><span data-stu-id="16913-208">The values in the base docker-compose.yml file should not change because of different target deployment environments.</span></span>

<span data-ttu-id="16913-209">Örneğin, webmvc hizmet tanımına odaklanırsanız, hangi ortamı hedefliyor olursanız olun bu bilgilerin nasıl aynı olduğunu görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="16913-209">If you focus on the webmvc service definition, for instance, you can see how that information is much the same no matter what environment you might be targeting.</span></span> <span data-ttu-id="16913-210">Aşağıdaki bilgilere sahipsiniz:</span><span class="sxs-lookup"><span data-stu-id="16913-210">You have the following information:</span></span>

- <span data-ttu-id="16913-211">Hizmet adı: webmvc.</span><span class="sxs-lookup"><span data-stu-id="16913-211">The service name: webmvc.</span></span>

- <span data-ttu-id="16913-212">Konteynerin özel görüntüsü: eshop/webmvc.</span><span class="sxs-lookup"><span data-stu-id="16913-212">The container’s custom image: eshop/webmvc.</span></span>

- <span data-ttu-id="16913-213">Hangi Dockerfile'nin kullanılacağını belirten özel Docker görüntüsünü oluşturma komutu.</span><span class="sxs-lookup"><span data-stu-id="16913-213">The command to build the custom Docker image, indicating which Dockerfile to use.</span></span>

- <span data-ttu-id="16913-214">Diğer hizmetlere bağımlılıklar, bu nedenle bu kapsayıcı diğer bağımlılık kapsayıcıları başlayana kadar başlamaz.</span><span class="sxs-lookup"><span data-stu-id="16913-214">Dependencies on other services, so this container does not start until the other dependency containers have started.</span></span>

<span data-ttu-id="16913-215">Ek yapılandırmanız olabilir, ancak önemli olan nokta, temel docker-compose.yml dosyasında yalnızca ortamlar arasında yaygın olan bilgileri ayarlamak istemenizdir.</span><span class="sxs-lookup"><span data-stu-id="16913-215">You can have additional configuration, but the important point is that in the base docker-compose.yml file, you just want to set the information that is common across environments.</span></span> <span data-ttu-id="16913-216">Daha sonra docker-compose.override.yml veya üretim veya evreleme için benzer dosyalarda, her ortam için özel yapılandırma yerleştirmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="16913-216">Then in the docker-compose.override.yml or similar files for production or staging, you should place configuration that is specific for each environment.</span></span>

<span data-ttu-id="16913-217">Genellikle, docker-compose.override.yml geliştirme ortamı için kullanılır, eShopOnContainers aşağıdaki örnekte olduğu gibi:</span><span class="sxs-lookup"><span data-stu-id="16913-217">Usually, the docker-compose.override.yml is used for your development environment, as in the following example from eShopOnContainers:</span></span>

```yml
#docker-compose.override.yml (Extended config for DEVELOPMENT env.)
version: '3.4'

services:
# Simplified number of services here:

  basket-api:
    environment:
      - ASPNETCORE_ENVIRONMENT=Development
      - ASPNETCORE_URLS=http://0.0.0.0:80
      - ConnectionString=${ESHOP_AZURE_REDIS_BASKET_DB:-basketdata}
      - identityUrl=http://identity-api
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

  catalog-api:
    environment:
      - ASPNETCORE_ENVIRONMENT=Development
      - ASPNETCORE_URLS=http://0.0.0.0:80
      - ConnectionString=${ESHOP_AZURE_CATALOG_DB:-Server=sqldata;Database=Microsoft.eShopOnContainers.Services.CatalogDb;User Id=sa;Password=Pass@word}
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

  marketing-api:
    environment:
      - ASPNETCORE_ENVIRONMENT=Development
      - ASPNETCORE_URLS=http://0.0.0.0:80
      - ConnectionString=${ESHOP_AZURE_MARKETING_DB:-Server=sqldata;Database=Microsoft.eShopOnContainers.Services.MarketingDb;User Id=sa;Password=Pass@word}
      - MongoConnectionString=${ESHOP_AZURE_COSMOSDB:-mongodb://nosqldata}
      - MongoDatabase=MarketingDb
      - EventBusConnection=${ESHOP_AZURE_SERVICE_BUS:-rabbitmq}
      - EventBusUserName=${ESHOP_SERVICE_BUS_USERNAME}
      - EventBusPassword=${ESHOP_SERVICE_BUS_PASSWORD}
      - identityUrl=http://identity-api
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
      - CatalogUrlHC=http://catalog-api/hc
      - OrderingUrlHC=http://ordering-api/hc
      - IdentityUrlHC=http://identity-api/hc
      - BasketUrlHC=http://basket-api/hc
      - MarketingUrlHC=http://marketing-api/hc
      - PaymentUrlHC=http://payment-api/hc
      - SignalrHubUrl=http://${ESHOP_EXTERNAL_DNS_NAME_OR_IP}:5202
      - UseCustomizationData=True
      - ApplicationInsights__InstrumentationKey=${INSTRUMENTATION_KEY}
      - OrchestratorType=${ORCHESTRATOR_TYPE}
      - UseLoadTest=${USE_LOADTEST:-False}
    ports:
      - "5100:80"
  sqldata:
    environment:
      - SA_PASSWORD=Pass@word
      - ACCEPT_EULA=Y
    ports:
      - "5433:1433"
  nosqldata:
    ports:
      - "27017:27017"
  basketdata:
    ports:
      - "6379:6379"
  rabbitmq:
    ports:
      - "15672:15672"
      - "5672:5672"

```

<span data-ttu-id="16913-218">Bu örnekte, geliştirme geçersiz kılma yapılandırması bazı bağlantı noktalarını ana bilgisayara gösterir, yeniden yönlendirme URL'leri olan ortam değişkenlerini tanımlar ve geliştirme ortamı için bağlantı dizeleri belirtir.</span><span class="sxs-lookup"><span data-stu-id="16913-218">In this example, the development override configuration exposes some ports to the host, defines environment variables with redirect URLs, and specifies connection strings for the development environment.</span></span> <span data-ttu-id="16913-219">Bu ayarların tümü sadece geliştirme ortamı içindir.</span><span class="sxs-lookup"><span data-stu-id="16913-219">These settings are all just for the development environment.</span></span>

<span data-ttu-id="16913-220">Çalıştırdığınızda `docker-compose up` (veya Visual Studio'dan başlattığınızda), komut, geçersiz kılmaları her iki dosyayı da birleştiriyormuş gibi otomatik olarak okur.</span><span class="sxs-lookup"><span data-stu-id="16913-220">When you run `docker-compose up` (or launch it from Visual Studio), the command reads the overrides automatically as if it were merging both files.</span></span>

<span data-ttu-id="16913-221">Farklı yapılandırma değerleri, bağlantı noktaları veya bağlantı dizeleri ile üretim ortamı için başka bir Oluşturma dosyası istediğinizi varsayalım.</span><span class="sxs-lookup"><span data-stu-id="16913-221">Suppose that you want another Compose file for the production environment, with different configuration values, ports, or connection strings.</span></span> <span data-ttu-id="16913-222">Farklı ayarlar ve ortam değişkenleri `docker-compose.prod.yml` ile adlı dosya gibi başka bir geçersiz kılma dosyası oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="16913-222">You can create another override file, like file named `docker-compose.prod.yml` with different settings and environment variables.</span></span> <span data-ttu-id="16913-223">Bu dosya farklı bir Git repo'sunda depolanabilir veya farklı bir ekip tarafından yönetilip güvenli hale alınabilir.</span><span class="sxs-lookup"><span data-stu-id="16913-223">That file might be stored in a different Git repo or managed and secured by a different team.</span></span>

#### <a name="how-to-deploy-with-a-specific-override-file"></a><span data-ttu-id="16913-224">Belirli bir geçersiz kılma dosyasıyla nasıl dağıtılır?</span><span class="sxs-lookup"><span data-stu-id="16913-224">How to deploy with a specific override file</span></span>

<span data-ttu-id="16913-225">Birden çok geçersiz kılma dosyasını veya farklı bir ada sahip bir geçersiz kılma dosyasını kullanmak için docker-comoluştur komutuyla -f seçeneğini kullanabilir ve dosyaları belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="16913-225">To use multiple override files, or an override file with a different name, you can use the -f option with the docker-compose command and specify the files.</span></span> <span data-ttu-id="16913-226">Dosyaları komut satırında belirtilen sırayla birleştirin.</span><span class="sxs-lookup"><span data-stu-id="16913-226">Compose merges files in the order they are specified on the command line.</span></span> <span data-ttu-id="16913-227">Aşağıdaki örnek, dosyaları geçersiz kılmakla nasıl dağıtılanın gerektiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="16913-227">The following example shows how to deploy with override files.</span></span>

```console
docker-compose -f docker-compose.yml -f docker-compose.prod.yml up -d
```

#### <a name="using-environment-variables-in-docker-compose-files"></a><span data-ttu-id="16913-228">Docker-compose dosyalarında ortam değişkenlerini kullanma</span><span class="sxs-lookup"><span data-stu-id="16913-228">Using environment variables in docker-compose files</span></span>

<span data-ttu-id="16913-229">Özellikle üretim ortamlarında, önceki örneklerde de gösterdiğimiz gibi, çevre değişkenlerinden yapılandırma bilgileri alabilmek uygundur.</span><span class="sxs-lookup"><span data-stu-id="16913-229">It is convenient, especially in production environments, to be able to get configuration information from environment variables, as we have shown in previous examples.</span></span> <span data-ttu-id="16913-230">${MY\_VAR} sözdizimini kullanarak docker-compose dosyalarınızda bir ortam değişkenine başvuruyapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="16913-230">You can reference an environment variable in your docker-compose files using the syntax ${MY\_VAR}.</span></span> <span data-ttu-id="16913-231">Docker-compose.prod.yml dosyasından aşağıdaki satır, bir ortam değişkeninin değerine nasıl başvurulsüreceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="16913-231">The following line from a docker-compose.prod.yml file shows how to reference the value of an environment variable.</span></span>

```yml
IdentityUrl=http://${ESHOP_PROD_EXTERNAL_DNS_NAME_OR_IP}:5105
```

<span data-ttu-id="16913-232">Ortam değişkenleri, ana bilgisayar ortamınıza (Linux, Windows, Bulut kümesi, vb.) bağlı olarak farklı şekillerde oluşturulur ve başharflere alınır.</span><span class="sxs-lookup"><span data-stu-id="16913-232">Environment variables are created and initialized in different ways, depending on your host environment (Linux, Windows, Cloud cluster, etc.).</span></span> <span data-ttu-id="16913-233">Ancak, uygun bir yaklaşım bir .env dosyası kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="16913-233">However, a convenient approach is to use an .env file.</span></span> <span data-ttu-id="16913-234">Docker-compose dosyaları .env dosyasında varsayılan ortam değişkenlerini bildiren destekler.</span><span class="sxs-lookup"><span data-stu-id="16913-234">The docker-compose files support declaring default environment variables in the .env file.</span></span> <span data-ttu-id="16913-235">Ortam değişkenleri için bu değerler varsayılan değerlerdir.</span><span class="sxs-lookup"><span data-stu-id="16913-235">These values for the environment variables are the default values.</span></span> <span data-ttu-id="16913-236">Ancak bunlar, ortamlarınızın her birinde tanımlamış olabileceğiniz değerler (kümenizden os veya ortam değişkenleri barındırma) tarafından geçersiz kılınabilir.</span><span class="sxs-lookup"><span data-stu-id="16913-236">But they can be overridden by the values you might have defined in each of your environments (host OS or environment variables from your cluster).</span></span> <span data-ttu-id="16913-237">Bu .env dosyasını docker-compose komutunun yürütüldüğü klasöre yersiniz.</span><span class="sxs-lookup"><span data-stu-id="16913-237">You place this .env file in the folder where the docker-compose command is executed from.</span></span>

<span data-ttu-id="16913-238">Aşağıdaki örnekte eShopOnContainers uygulaması için .env dosyası gibi bir [.env](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/.env) dosyası gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="16913-238">The following example shows an .env file like the [.env](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/.env) file for the eShopOnContainers application.</span></span>

```sh
# .env file

ESHOP_EXTERNAL_DNS_NAME_OR_IP=localhost

ESHOP_PROD_EXTERNAL_DNS_NAME_OR_IP=10.121.122.92
```

<span data-ttu-id="16913-239">Docker-compose, .env dosyasındaki her satırın \<biçim\>=\<\>değişken değerinde olmasını bekler.</span><span class="sxs-lookup"><span data-stu-id="16913-239">Docker-compose expects each line in an .env file to be in the format \<variable\>=\<value\>.</span></span>

<span data-ttu-id="16913-240">Çalışma zamanı ortamında ayarlanan değerler her zaman .env dosyasıiçinde tanımlanan değerleri geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="16913-240">The values set in the run-time environment always override the values defined inside the .env file.</span></span> <span data-ttu-id="16913-241">Benzer şekilde, komut satırı bağımsız değişkenleri aracılığıyla geçirilen değerler de .env dosyasında ayarlanan varsayılan değerleri geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="16913-241">In a similar way, values passed via command-line arguments also override the default values set in the .env file.</span></span>

#### <a name="additional-resources"></a><span data-ttu-id="16913-242">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="16913-242">Additional resources</span></span>

- <span data-ttu-id="16913-243">**Docker Compose'a Genel Bakış** </span><span class="sxs-lookup"><span data-stu-id="16913-243">**Overview of Docker Compose** </span></span>\
    <https://docs.docker.com/compose/overview/>

- <span data-ttu-id="16913-244">**Birden Çok Dosya Oluştur** </span><span class="sxs-lookup"><span data-stu-id="16913-244">**Multiple Compose files** </span></span>\
    [https://docs.docker.com/compose/extends/\#multiple-compose-files](https://docs.docker.com/compose/extends/#multiple-compose-files)

### <a name="building-optimized-aspnet-core-docker-images"></a><span data-ttu-id="16913-245">Core Docker görüntüleri ASP.NET optimize edilmiş bina</span><span class="sxs-lookup"><span data-stu-id="16913-245">Building optimized ASP.NET Core Docker images</span></span>

<span data-ttu-id="16913-246">Docker ve .NET Core'u Internet'teki kaynaklarda keşfediyorsanız, kaynağınızı bir konteyneriçine kopyalayarak Docker görüntüsü oluşturmanın basitliğini gösteren Dockerfiles'ı bulacaksınız.</span><span class="sxs-lookup"><span data-stu-id="16913-246">If you are exploring Docker and .NET Core on sources on the Internet, you will find Dockerfiles that demonstrate the simplicity of building a Docker image by copying your source into a container.</span></span> <span data-ttu-id="16913-247">Bu örnekler, basit bir yapılandırma kullanarak, uygulamanızla birlikte çevreyle birlikte bir Docker görüntüsüne sahip olabileceğinizi düşündürmektedir.</span><span class="sxs-lookup"><span data-stu-id="16913-247">These examples suggest that by using a simple configuration, you can have a Docker image with the environment packaged with your application.</span></span> <span data-ttu-id="16913-248">Aşağıdaki örnek, bu ven basit bir Dockerfile gösterir.</span><span class="sxs-lookup"><span data-stu-id="16913-248">The following example shows a simple Dockerfile in this vein.</span></span>

```Dockerfile
FROM mcr.microsoft.com/dotnet/core/sdk:3.1
WORKDIR /app
ENV ASPNETCORE_URLS http://+:80
EXPOSE 80
COPY . .
RUN dotnet restore
ENTRYPOINT ["dotnet", "run"]
```

<span data-ttu-id="16913-249">Böyle bir Dockerdosyası işe yarar.</span><span class="sxs-lookup"><span data-stu-id="16913-249">A Dockerfile like this will work.</span></span> <span data-ttu-id="16913-250">Ancak, resimlerinizi, özellikle de üretim resimlerinizi önemli ölçüde optimize edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="16913-250">However, you can substantially optimize your images, especially your production images.</span></span>

<span data-ttu-id="16913-251">Konteyner ve mikrohizmetler modelinde, sürekli konteyner başlatın.</span><span class="sxs-lookup"><span data-stu-id="16913-251">In the container and microservices model, you are constantly starting containers.</span></span> <span data-ttu-id="16913-252">Kapsayıcı tek kullanımlık olduğundan, kapsayıcıları kullanmanın tipik yolu uyku kabını yeniden başlatmaz.</span><span class="sxs-lookup"><span data-stu-id="16913-252">The typical way of using containers does not restart a sleeping container, because the container is disposable.</span></span> <span data-ttu-id="16913-253">Orkestratörler (Kubernetes ve Azure Hizmet Kumaşı gibi) yeni görüntü örnekleri oluşturur.</span><span class="sxs-lookup"><span data-stu-id="16913-253">Orchestrators (like Kubernetes and Azure Service Fabric) simply create new instances of images.</span></span> <span data-ttu-id="16913-254">Bunun anlamı, uygulama inşa edildiğinde önceden derleyerek en iyi duruma getirmeniz gerektiğidir, böylece anlık işlem daha hızlı olacaktır.</span><span class="sxs-lookup"><span data-stu-id="16913-254">What this means is that you would need to optimize by precompiling the application when it is built so the instantiation process will be faster.</span></span> <span data-ttu-id="16913-255">Kapsayıcı başlatıldığında, çalışmaya hazır olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="16913-255">When the container is started, it should be ready to run.</span></span> <span data-ttu-id="16913-256">.NET Core ve Docker hakkındaki birçok `dotnet restore` `dotnet build` blog gönderisinde gördüğünüz gibi, dotnet CLI'yi kullanarak ve komutları kullanarak çalışma zamanında geri yüklememeli ve derlememelisiniz.</span><span class="sxs-lookup"><span data-stu-id="16913-256">You should not restore and compile at run time, using `dotnet restore` and `dotnet build` commands from the dotnet CLI that, as you see in many blog posts about .NET Core and Docker.</span></span>

<span data-ttu-id="16913-257">.NET ekibi .NET Core ve ASP.NET Core'u konteyner için optimize edilmiş bir çerçeve haline getirmek için önemli çalışmalar yapıyor.</span><span class="sxs-lookup"><span data-stu-id="16913-257">The .NET team has been doing important work to make .NET Core and ASP.NET Core a container-optimized framework.</span></span> <span data-ttu-id="16913-258">Sadece .NET Core küçük bir bellek ayak izi ile hafif bir çerçeve; ekip üç ana senaryo için optimize edilmiş Docker görüntülerine odaklanmıştır ve bunları sürüm 2.1 ile başlayan *dotnet/core*adresindeki Docker Hub kayıt defterinde yayınlamıştır:</span><span class="sxs-lookup"><span data-stu-id="16913-258">Not only is .NET Core a lightweight framework with a small memory footprint; the team has focused on optimized Docker images for three main scenarios and published them in the Docker Hub registry at *dotnet/core*, beginning with version 2.1:</span></span>

1. <span data-ttu-id="16913-259">**Geliştirme**: Önceliğin değişiklikleri hızlı bir şekilde yineleme ve hata ayıklama yeteneği ve boyutun ikincil olduğu yerdir.</span><span class="sxs-lookup"><span data-stu-id="16913-259">**Development**: Where the priority is the ability to quickly iterate and debug changes, and where size is secondary.</span></span>

2. <span data-ttu-id="16913-260">**Yapı**: Öncelik uygulamayı derlemektir ve ikilileri optimize etmek için ikili leri ve diğer bağımlılıkları içerir.</span><span class="sxs-lookup"><span data-stu-id="16913-260">**Build**: The priority is compiling the application and includes binaries and other dependencies to optimize binaries.</span></span>

3. <span data-ttu-id="16913-261">**Üretim**: Odak noktasının konteynerlerin hızlı bir şekilde dağıtılması ve başlatılması dır, bu nedenle bu görüntüler uygulamanın çalıştırılması için gereken ikili ve içerikle sınırlıdır.</span><span class="sxs-lookup"><span data-stu-id="16913-261">**Production**: Where the focus is fast deploying and starting of containers, so these images are limited to the binaries and the content needed to run the application.</span></span>

<span data-ttu-id="16913-262">Bunu başarmak için ,NET ekibi [dotnet/core'da](https://hub.docker.com/_/microsoft-dotnet-core/) (Docker Hub'da) dört temel türevi sağlar:</span><span class="sxs-lookup"><span data-stu-id="16913-262">To achieve this, the .NET team is providing four basic variants in [dotnet/core](https://hub.docker.com/_/microsoft-dotnet-core/) (at Docker Hub):</span></span>

1. <span data-ttu-id="16913-263">**sdk**: geliştirme ve inşa senaryoları için</span><span class="sxs-lookup"><span data-stu-id="16913-263">**sdk**: for development and build scenarios</span></span>
1. <span data-ttu-id="16913-264">**aspnet**: ASP.NET üretim senaryoları için</span><span class="sxs-lookup"><span data-stu-id="16913-264">**aspnet**: for ASP.NET production scenarios</span></span>
1. <span data-ttu-id="16913-265">**runtime**: .NET üretim senaryoları için</span><span class="sxs-lookup"><span data-stu-id="16913-265">**runtime**: for .NET production scenarios</span></span>
1. <span data-ttu-id="16913-266">**runtime-deps**: bağımsız uygulamaların üretim [senaryoları](../../../core/deploying/index.md#publish-self-contained)için.</span><span class="sxs-lookup"><span data-stu-id="16913-266">**runtime-deps**: for production scenarios of [self-contained applications](../../../core/deploying/index.md#publish-self-contained).</span></span>

<span data-ttu-id="16913-267">Daha hızlı başlangıç için, çalışma zamanı görüntüleri\_aspnetcore url'lerini 80 bağlantı noktasına otomatik olarak ayarlar ve yerel bir anagörüntü önbelleği oluşturmak için Ngen'i kullanır.</span><span class="sxs-lookup"><span data-stu-id="16913-267">For faster startup, runtime images also automatically set aspnetcore\_urls to port 80 and use Ngen to create a native image cache of assemblies.</span></span>

#### <a name="additional-resources"></a><span data-ttu-id="16913-268">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="16913-268">Additional resources</span></span>

- <span data-ttu-id="16913-269">**ASP.NET Core ile Optimize Edilmiş Docker Görüntüleri Oluşturma**</span><span class="sxs-lookup"><span data-stu-id="16913-269">**Building Optimized Docker Images with ASP.NET Core**</span></span>  
  <https://docs.microsoft.com/archive/blogs/stevelasker/building-optimized-docker-images-with-asp-net-core>

- <span data-ttu-id="16913-270">**.NET Core Uygulamaları için Docker Görüntülerinizi Derleme**</span><span class="sxs-lookup"><span data-stu-id="16913-270">**Building Docker Images for .NET Core Applications**</span></span>  
  [https://docs.microsoft.com/dotnet/core/docker/building-net-docker-images](/aspnet/core/host-and-deploy/docker/building-net-docker-images)

> [!div class="step-by-step"]
> <span data-ttu-id="16913-271">[Önceki](data-driven-crud-microservice.md)
> [Sonraki](database-server-container.md)</span><span class="sxs-lookup"><span data-stu-id="16913-271">[Previous](data-driven-crud-microservice.md)
[Next](database-server-container.md)</span></span>
