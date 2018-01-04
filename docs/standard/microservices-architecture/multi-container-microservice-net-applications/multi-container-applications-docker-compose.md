---
title: "Birden çok kapsayıcı uygulamanızla docker-compose.yml tanımlama"
description: "Kapsayıcılı .NET uygulamaları için .NET mikro mimarisi | Birden çok kapsayıcı uygulamanızla docker-compose.yml tanımlama"
keywords: "Docker, mikro, ASP.NET, kapsayıcı"
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
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="defining-your-multi-container-application-with-docker-composeyml"></a>Birden çok kapsayıcı uygulamanızla docker-compose.yml tanımlama 

Bu kılavuzdaki [docker-compose.yml](https://docs.docker.com/compose/compose-file/) dosya bölümünde sunulmuştur [4. adım. Birden çok kapsayıcı Docker uygulama oluştururken docker-compose.yml hizmetlerinizi tanımlamak](#step4_define_svcs_in_docker_compose_yml). Ancak, daha ayrıntılı olarak incelenmesi yararlı docker-compose dosyaları kullanmak için ek yöntemler vardır.

Örneğin, birden çok kapsayıcı uygulamanızda docker-compose.yml dosyası dağıtmak istediğiniz nasıl açıkça tanımlayabilirsiniz. İsteğe bağlı olarak, nasıl özel Docker görüntülerinizi oluşturmak zorunda kalacaklarını tanımlayabilirsiniz. (Özel Docker görüntüleri Docker CLI ile de oluşturulabilir.)

Temel olarak, her dağıtmak istediğiniz kapsayıcıları ve her bir kapsayıcı dağıtımı için belirli özellikleri tanımlayın. Birden çok kapsayıcı dağıtım açıklama dosyasını oluşturduktan sonra tarafından düzenlenmiş tek bir eylem tüm çözümde dağıtabilirsiniz [docker-oluşturmanıza](https://docs.docker.com/compose/overview/) CLI komut veya dağıtabilir, saydam Visual Studio'dan. Aksi takdirde, Docker CLI kapsayıcı tarafından kapsayıcı birden çok adımlarda komutu komut satırından çalıştırma docker kullanarak dağıtmak için kullanmanız gerekir. Bu nedenle, docker-compose.yml tanımlanan her bir hizmet tam olarak bir resim belirtin veya bu yapı gerekir. Diğer anahtarlar isteğe bağlıdır ve komut satırı ortaklarınıza çalıştırmak, docker benzer.

Aşağıdaki YAML kodu eShopOnContainers örnek için bir olası genel ancak tek docker-compose.yml dosyası tanımıdır. Bu eShopOnContainers gerçek docker-compose dosyasından değildir. Bunun yerine, tek bir en iyi olmayan dosya, Basitleştirilmiş ve birleştirilmiş bir sürümde olduğundan çalışmak için yol docker-oluşturan dosyaları, daha sonra açıklanacaktır gibi.

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

Hizmetleri bu dosyadaki kök anahtardır. Bu anahtarın altında tanımladığınız dağıtmak ve yürüttüğünüzde çalıştırmak istediğiniz hizmetleri docker-oluşturan komut veya ne zaman bu docker-compose.yml dosyası kullanarak Visual Studio'dan dağıtın. Bu durumda, docker-compose.yml dosyası aşağıdaki listede açıklandığı gibi tanımlı, birden çok hizmetleri vardır.

-   webmvc sunucu tarafı c mikro kullanan ASP.NET Core MVC uygulaması da dahil olmak üzere kapsayıcısı\#

-   catalog.api katalog ASP.NET çekirdek Web API mikro hizmet dahil olmak üzere kapsayıcısı

-   ordering.api sıralama ASP.NET çekirdek Web API mikro hizmet dahil olmak üzere kapsayıcısı

-   SQL.Data mikro veritabanları bulunduran Linux için SQL Server çalıştıran kapsayıcısı

-   Basket.api kapsayıcı Sepeti ASP.NET çekirdek Web API mikro hizmet ile

-   Basket.Data kapsayıcı REDIS önbelleği olarak Sepeti veritabanıyla REDIS önbelleği hizmeti çalışıyor

### <a name="a-simple-web-service-api-container"></a>Basit bir Web hizmeti API'sine kapsayıcı

Tek bir kapsayıcıda odaklanan catalog.api kapsayıcı mikro basit bir tanımı vardır:

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

Bu kapsayıcılı hizmet temel yapılandırması aşağıdaki gibidir:

-   Özel eshop/catalog.api görüntüde dayanır. Basitlik'ın artırmak amacıyla için hiçbir yapı vardır: anahtar dosyasındaki ayarı. Bu görüntü önceden (docker yapı ile) oluşturulmuş gerekir veya tüm Docker kayıt defterinden (docker çekme komutuyla) yüklenmiş olan anlamına gelir.

-   ConnectionString Kataloğu veri modeli içeren SQL Server örneğine erişmek için Entity Framework tarafından kullanılacak bağlantı dizesinin adlı bir ortam değişkeni tanımlar. Bu durumda, aynı SQL Server kapsayıcı birden çok veritabanı tutuyor. Bu nedenle, daha az bellek için Docker geliştirme makinenizde gerekir. Bununla birlikte, her mikro hizmet veritabanı için bir SQL Server kapsayıcısı dağıtabilirsiniz.

-   SQL Server sql.data, SQL Server örneği için Linux çalıştıran kapsayıcısı için kullandığınız aynı adı olan addır. Bu uygundur; iç IP diğer kapsayıcılardan eriştiğiniz kapsayıcıları için bilmeniz gerek kalmaması (için Docker ana bilgisayar iç) bu ad çözümlemesi kullanabilmek için ağ adresi çözümleyin.

Bağlantı dizesi bir ortam değişkeni tarafından tanımlı olduğundan farklı mekanizması aracılığıyla ve farklı bir zamanda bu değişkeni ayarlayabilirsiniz. Örneğin, farklı bir bağlantı dizesi üretime son konakları veya CI/CD hatlarınızı VSTS ya da tercih edilen DevOps sisteminizi gelen yapmakta dağıtırken ayarlayabilirsiniz.

-   Bağlantı noktası 80 iç erişim için Docker ana catalog.api Hizmeti'nde gösterir. Konak şu anda bir Linux VM Linux için Docker görüntüde dayanır, ancak bunun yerine bir Windows görüntüsünü çalıştırmak için kapsayıcı yapılandırabilirsiniz nedeni.

-   Kullanıma sunulan bağlantı noktası 80 kapsayıcısındaki (Linux VM'de) Docker ana makinede 5101 numaralı bağlantı noktasına iletir.

-   Web hizmeti (bir kapsayıcıda çalışan Linux veritabanı için SQL Server örneğini) sql.data hizmetine bağlar. Bu bağımlılık belirttiğinizde, sql.data kapsayıcısı zaten başlatıldı kadar catalog.api kapsayıcı başlatılmaz; Bu ilk catalog.api SQL Server veritabanı olmasını gerektiğinden önemli ve çalışır durumdadır. Docker yalnızca kapsayıcı düzeyinde denetler olduğundan ancak, bu tür bir kapsayıcı bağımlılığı birçok durumda yeterli değil. Yeniden deneme mantığı üstel geri alma ile istemci mikro uygulamanız önerilir; böylece bazen hizmetinde (büyük/küçük harfe bu SQL Server) hala hazır olmayabilir. Bir bağımlılık kapsayıcı kısa bir süre için hazır değilse, bu şekilde, uygulamayı esnek olmaya devam eder.

-   Dış sunucuları erişmesine izin vermek için yapılandırılmış: ek\_ayarı ana dış sunucuların ya da makineleri Docker ana dışında erişmenize olanak tanır (diğer bir deyişle, geliştirme Docker olan bir Linux VM varsayılan dışında barındırma) gibi bir yerel SQL PC Geliştirme Sunucusu örneğinde.

Aşağıdaki bölümlerde ele alınacaktır diğer, daha gelişmiş docker-compose.yml ayarları vardır.

### <a name="using-docker-compose-files-to-target-multiple-environments"></a>Kullanarak docker-oluşturan birden çok ortamları hedeflemek için dosyaları

Docker-compose.yml dosyalar tanım dosyalarını ve bu biçimi anlamak birden çok altyapıları tarafından kullanılabilir. Docker en kolay araçtır-komutu oluşturmak, ancak bu dosya ayrıca orchestrators (örneğin, Docker Swarm) anlamak gibi diğer araçları.

Kullanarak bu nedenle, aşağıdaki ana senaryo hedef komutu docker compose'u.

#### <a name="development-environments"></a>Geliştirme ortamları

Uygulamaları geliştirirken, uygulamanın bir yalıtılmış geliştirme ortamında çalıştırılabilmesi için önemlidir. Kullanabileceğiniz docker compose'u bu ortam oluşturmak veya hangi kullanımlar docker-perde arkasında oluşturan Visual Studio kullanmak için CLI komutu.

Docker-compose.yml dosyası, yapılandırmak ve tüm uygulama Hizmet bağımlılıklarını (diğer hizmetler, önbellek, veritabanları, kuyruklar, vb.) belge olanak sağlar. Kullanarak CLI komutu docker compose'u, oluşturabilir ve her bir bağımlılığın için bir veya daha fazla kapsayıcı tek bir komutla başlatın (docker-oluşturmanıza).

Docker-compose.yml dosyalar Docker altyapısı tarafından yorumlanan yapılandırma dosyaları ancak uygun belge dosyalarını birden çok kapsayıcı uygulamanızı bileşimi hakkında olarak da hizmet.

#### <a name="testing-environments"></a>Sınama ortamları

Herhangi bir sürekli dağıtımı (CD) veya sürekli tümleştirme (CI) işlemi önemli bir parçası olan birim testleri ve tümleştirme testleri. Bu otomatikleştirilmiş testleri yalıtılmış bir ortamda gerektirdiğinden, kullanıcılar veya herhangi bir değişiklik uygulamanın veri tarafından etkilenmez.

Docker Compose ile oluşturun ve o yalıtılmış bir ortamda kolayca komut istemi veya komut dosyaları, aşağıdaki komutları gibi birkaç komutları yok:

```
docker-compose up -d
./run_unit_tests
docker-compose down
```

#### <a name="production-deployments"></a>Üretim dağıtımları

Oluştur, uzak bir Docker altyapısına dağıtmak için de kullanabilirsiniz. Tipik bir servis talebi için tek bir Docker ana bilgisayar örneği dağıtmaktır (bir üretim VM veya sunucusu ile sağlanan gibi [Docker makine](https://docs.docker.com/machine/overview/)). Ancak tüm olabilir [Docker Swarm](https://docs.docker.com/swarm/overview/) kümeleri de docker-compose.yml dosyaları ile uyumlu olmadığından, küme.

Tüm diğer orchestrator (Azure Service Fabric, Mesos DC/OS, Kubernetes, vb.) kullanıyorsanız, docker-compose.yml ancak diğer orchestrator tarafından gerekli olan biçime benzer Kurulum ve meta verileri yapılandırma ayarlarını eklemeniz gerekebilir.

Herhangi bir durumda, docker compose'u geliştirme, test ve üretim iş akışları için kullanışlı bir aracı ve meta veri biçimi olsa üretim iş akışı kullanmakta olduğunuz orchestrator değişebilir.

### <a name="using-multiple-docker-compose-files-to-handle-several-environments"></a>Birden fazla docker-oluşturan çeşitli ortamlar işlemek için dosyaları

Birden çok farklı ortamlarda hedeflerken kullanması gereken dosyaları oluşturun. Bu ortam bağlı olarak birden çok yapılandırma çeşitleri oluşturmanıza olanak tanır.

#### <a name="overriding-the-base-docker-compose-file"></a>Temel docker-compose dosya geçersiz kılma

Önceki bölümlerde Basitleştirilmiş örneklerde olduğu gibi tek docker-compose.yml dosyası kullanabilirsiniz. Bununla birlikte, çoğu uygulama için önerilmez.

Varsayılan olarak, iki dosya, docker-compose.yml ve isteğe bağlı docker compose.override.yml dosyası oluşturma okur. Şekil 8-11'de gösterildiği gibi zaman, Visual Studio kullanarak ve Docker desteği, Visual Studio de etkinleştirme, CI/CD hatlarınızı gibi VSTS içinde kullanmak bir ek docker compose.ci.build,yml dosyası oluşturur.

![](./media/image12.png)

**Şekil 8-11**. Visual Studio 2017 dosyalarında docker compose'u

Visual Studio Code veya Sublime, gibi herhangi bir Düzenleyicisi docker-compose dosyaları düzenleyin ve uygulamayla çalıştırmak docker compose'u up komutu.

Kurala göre docker-compose.yml dosyası temel yapılandırma ve diğer statik ayarlarını içerir. Hizmet yapılandırması, hedeflediğiniz dağıtım ortamı bağlı olarak değiştirmemelisiniz anlamına gelir.

Adından da anlaşılacağı gibi docker compose.override.yml dosya dağıtım ortamınıza bağlıdır yapılandırma gibi temel yapılandırmasını geçersiz kılma yapılandırma ayarlarını içerir. Farklı adlara sahip birden çok geçersiz kılma dosyaları da sahip olabilirsiniz. Geçersiz kılma dosyalar genellikle uygulama ancak belirli bir ortam veya bir dağıtım için gerekli ek bilgiler içerir.

#### <a name="targeting-multiple-environments"></a>Birden çok ortamları hedefleme

Tipik kullanım örneği olan birden çok tanımlarken oluşturan dosyaları hazırlama, CI ya da geliştirme üretim gibi birden çok ortamları hedefleyebilirsiniz şekilde. Bu farklılıklar desteklemek için Şekil 8-12'de gösterildiği gibi birden çok dosyalarına Oluştur yapılandırmanızı bölebilirsiniz.

![](./media/image13.png)

**Şekil 8-12**. Birden çok oluşturan docker dosyaları temel docker-compose.yml dosyasındaki değerleri geçersiz kılma

Temel docker-compose.yml dosyası ile başlatın. Bu temel dosyanın ortamına bağlı olarak değiştirmeyin temel veya statik yapılandırma ayarlarını içermesi gerekir. Örneğin, eShopOnContainers temel dosyası olarak aşağıdaki docker-compose.yml dosyası vardır.

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

Temel docker-compose.yml dosyası değerler farklı bir hedef dağıtım ortamları nedeniyle değiştirmemeniz gerekir.

Örneğin, webmvc hizmet tanımını odaklanmanıza, nasıl bu bilgileri çok aynı hedefleme hangi ortam olduğunu görebilirsiniz. Aşağıdaki bilgilere sahip:

-   Hizmet adı: webmvc.

-   Kapsayıcının özel görüntü: Elektronik Mağaza/webmvc.

-   Kullanmak için hangi Dockerfile gösteren özel Docker görüntü oluşturmak için komutu.

-   Bir bağımlılık kapsayıcıları başlatılıncaya kadar bu kapsayıcı başlamaz diğer hizmetler bağımlılıkları.

Ek yapılandırma olabilir, ancak önemli temel docker-compose.yml dosyası, yalnızca ortamlar arasında ortak olan bilgileri ayarlamak istediğinizi noktasıdır. Ardından docker compose.override.yml veya üretim veya hazırlama benzer dosyalarını her ortam için belirli yapılandırma yerleştirmeniz gerekir.

Genellikle, docker compose.override.yml eShopOnContainers aşağıdaki örnekte olduğu gibi geliştirme ortamınız için kullanılır:

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

Bu örnekte, geliştirme geçersiz kılma yapılandırmasını barındırmak için bazı bağlantı noktalarını kullanıma sunar, ortam değişkenleri tanımlar URL'leri yönlendirmek ve geliştirme ortamı için bağlantı dizelerini belirtir. Bu ayarlar tüm yalnızca geliştirme ortamına ' dir.

Çalıştırdığınızda `docker-compose up` (veya Visual Studio'dan başlatma), her iki dosyaları birleştirme gibi komut geçersiz kılmaları otomatik olarak okur.

Üretim ortamında, farklı yapılandırma değerlerini, bağlantı noktası veya bağlantı dizeleri için başka bir oluşturma dosyası istediğinizi varsayalım. Adlı dosyası gibi başka bir geçersiz kılma dosyası oluşturabilirsiniz `docker-compose.prod.yml` farklı ayarlar ve ortam değişkenleri.  Bu dosyayı farklı bir Git deposu içinde depolanan veya yönetilebilir ve farklı bir takım tarafından güvenli hale getirilmiş.

#### <a name="how-to-deploy-with-a-specific-override-file"></a>Bir özel geçersiz kılma dosyayla dağıtma

Birden çok geçersiz kılma dosyaları veya bir geçersiz kılma dosyasını farklı bir ad ile kullanmak için -f seçeneğiyle kullanabilirsiniz komutu docker compose'u ve dosyaları belirtin. Komut satırında belirtilen sırada birleştirmeler dosyaları oluşturun. Aşağıdaki örnek, geçersiz kılma dosyalarıyla dağıtma gösterilmektedir.

```
docker-compose -f docker-compose.yml -f docker-compose.prod.yml up -d
```

#### <a name="using-environment-variables-in-docker-compose-files"></a>Ortam değişkenlerini kullanma, docker-dosyaları oluşturma

Bu, biz önceki örneklerde gösterildiği gibi ortam değişkenlerinin, yapılandırma bilgileri elde edebilmek için özellikle üretim ortamlarında, uygundur. Docker-compose dosyalarınızı sözdizimini kullanarak bir ortam değişkeni başvurusu \${MY\_VAR}. Aşağıdaki satırı docker compose.prod.yml dosyasından bir ortam değişkeni değeri başvuru gösterilmektedir.

```yml
IdentityUrl=http://${ESHOP_PROD_EXTERNAL_DNS_NAME_OR_IP}:5105
```

Ortam değişkenleri oluşturuldu ve ana bilgisayar ortamınıza bağlı olarak, farklı şekillerde başlatıldı (Linux, Windows, bulut küme, vs.). Ancak, uygun bir yaklaşım .env dosya kullanmaktır. .Env dosyasındaki varsayılan ortam değişkenleri bildirme docker-compose dosyalarını destekler. Bu ortam değişkenleri için varsayılan değerleri değerlerdir. Ancak her ortamınızı (ana bilgisayar işletim sistemi veya ortam değişkenleri, kümeden) tanımlanmış değeri geçersiz kılınabilir. Bu .env dosyasını bu klasöre yerleştirin nerede docker compose'u komutu yürütüldü.

Aşağıdaki örnek, bir .env dosyası gibi gösterir [.env](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/.env) eShopOnContainers uygulamanın dosyası.

```
# .env file

ESHOP_EXTERNAL_DNS_NAME_OR_IP=localhost

ESHOP_PROD_EXTERNAL_DNS_NAME_OR_IP=10.121.122.92
```

Docker compose'u bekliyor biçiminde bir .env dosyasındaki her satırın &lt;değişkeni&gt;=&lt;değeri&gt;.

Çalışma zamanı ortamında her zaman ayarlanan değerlerle .env dosyanın içinde tanımlanan değerlerden birisini üzerine yazılacağını unutmayın. Benzer şekilde, komut satırı komut bağımsız değişkenleri geçirilen değerleri de .env dosyasında ayarlanan varsayılan değerlerini geçersiz kılar.

#### <a name="additional-resources"></a>Ek kaynaklar

-   **Docker genel bakış oluşturan**
    [*https://docs.docker.com/compose/overview/*](https://docs.docker.com/compose/overview/)

-   **Birden çok oluşturma dosyaları**
    [*https://docs.docker.com/compose/extends/\#birden çok oluşturan dosyaları*](https://docs.docker.com/compose/extends/#multiple-compose-files)

### <a name="building-optimized-aspnet-core-docker-images"></a>ASP.NET Core Docker görüntüleri oluşturma en iyi duruma getirilmiş

Internet üzerindeki kaynaklarında Docker ve .NET Core araştırırken, bir kapsayıcıya kaynağınız kopyalayarak Docker görüntü oluşturmanın Basitlik göstermek Dockerfiles bulabilirsiniz. Bu örnekler, basit bir yapılandırma kullanarak, Docker görüntü uygulamanızla paketlenmiş ortamıyla sağlayabilirsiniz öneririz. Aşağıdaki örnekte basit bir Dockerfile bu damarlı gösterir.

```
FROM microsoft/dotnet

WORKDIR /app

ENV ASPNETCORE_URLS http://+:80

EXPOSE 80

COPY . .

RUN dotnet restore

ENTRYPOINT ["dotnet", "run"]
```

Böyle bir Dockerfile çalışır. Ancak, özellikle üretim görüntülerinizi görüntülerinizi önemli ölçüde iyileştirebilirsiniz.

Kapsayıcı ve mikro modeli sürekli kapsayıcıları başlıyor. Kapsayıcı atılabilir olduğundan kapsayıcıları kullanma normal şekilde Uyuyan bir kapsayıcı yeniden başlatmaz. Orchestrators (örneğin, Docker Swarm, Kubernetes, DCOS veya Azure Service Fabric) yalnızca yeni örnekleri görüntülerin oluşturun. Ne Bu örnek oluşturma işlemi daha hızlı olması için derlendikten sonra uygulamayı önceden derleme en iyi duruma getirme gerek olduğu anlamına gelir. Kapsayıcı başlatıldığında, çalıştırılmaya hazır olması gerekir. Olmayan geri yükleme ve çalışma zamanında derlemek, .NET Core ve Docker ilgili birçok Web günlüğü postaları gördüğünüz gibi dotnet kullanarak geri yükleme ve dotnet dotnet CLI komutları, yapı.

.NET ekibi .NET Core ve ASP.NET Core kapsayıcı özelliği iyileştirilmiş bir çerçeve sağlamak için önemli iş yapmadan. Yalnızca .NET Core küçük bellek kaplama alanı için bir basit çerçevesiyle algılanmadığı; Takım başlangıç performans üzerinde odaklanır ve bazı en iyi duruma getirilmiş Docker görüntüleri gibi üretilen [microsoft/aspnetcore](https://hub.docker.com/r/microsoft/aspnetcore/) görüntü adresinde [Docker hub'a](https://hub.docker.com/r/microsoft/aspnetcore/), normal kıyasla [ Microsoft/dotnet](https://hub.docker.com/r/microsoft/dotnet/) veya [microsoft/nanoserver](https://github.com/dotnet/dotnet-docker/blob/master/1.0/nanoserver/runtime/Dockerfile) görüntüler. [Microsoft/aspnetcore](https://hub.docker.com/r/microsoft/aspnetcore/) görüntü sağlar aspnetcore otomatik ayarı\_80 numaralı bağlantı noktasını ve derlemeler; öncesi ngend önbelleğini URL'lere bu ayarların her ikisi de daha hızlı başlangıç sonucu.

#### <a name="additional-resources"></a>Ek kaynaklar

-   **Yapı en iyi duruma getirilmiş ASP.NET Core Docker görüntülerle**
    [*https://blogs.msdn.microsoft.com/stevelasker/2016/09/29/building-optimized-docker-images-with-asp-net-core/*](https://blogs.msdn.microsoft.com/stevelasker/2016/09/29/building-optimized-docker-images-with-asp-net-core/)

### <a name="building-the-application-from-a-build-ci-container"></a>Derleme (CI) kapsayıcısından uygulaması oluşturma

Bir yapı makine ya da uygulamanızı oluşturmak için VM oluşturmak gerek yoktur Şekil 8-13'te gösterildiği gibi Docker başka bir yararı önceden yapılandırılmış bir kapsayıcı uygulamanızdan oluşturabilirsiniz olur. Geliştirme makinenizde çalıştırarak test, yapı kapsayıcısı veya kullanabilirsiniz. Ancak daha ilginç nedir CI (sürekli tümleştirme) hattınızı aynı yapı kapsayıcı kullanabilirsiniz.

![](./media/image14.png)

**Şekil 8-13**. Docker derleme-kapsayıcısı .NET ikili dosyaları derleme 

Bu senaryo için size sağladığımız [aspnetcore/microsoft-yapı](https://hub.docker.com/r/microsoft/aspnetcore-build/) derlemek ve ASP.NET Core uygulamaları oluşturmak için kullanabileceğiniz görüntü. Çıktı temel görüntü yerleştirilir [microsoft/aspnetcore](https://hub.docker.com/r/microsoft/aspnetcore/) daha önce not ettiğiniz bir en iyi duruma getirilmiş çalışma zamanı görüntü görüntü.

Aspnetcore derleme görüntüsünü dahil .NET Core, ASP.NET SDK'sı, npm, bir ASP.NET Core uygulama derlemek için ihtiyaç duyduğunuz her şeyi içeren Bower, Gulp, vs.

Bu bağımlılıklar derleme zamanında ihtiyacımız var. Ancak, görüntünün düşükse yapmayacağı Biz bu uygulama ile çalışma zamanında taşımak istemiyorsanız. EShopOnContainers uygulamada uygulama oluşturabilir yalnızca çalıştırarak kapsayıcısından aşağıdaki docker-komutu oluşturun.

```
  docker-compose -f docker-compose.ci.build.yml up
```

Şekil 8-14 komut satırında çalıştıran bu komut gösterir.

![](./media/image15.png)

**Şekil 8-14.** .NET uygulamanızdan bir kapsayıcı oluşturma

Gördüğünüz gibi çalıştıran CI yapı kapsayıcıdır\_1 kapsayıcı. Böylece derlemek ve Bilgisayarınızdan yerine bu kapsayıcıdaki tüm uygulama içinden derleme bu aspnetcore yapı görüntüde temel alır. Diğer bir deyişle neden gerçekte olduğundan oluşturma ve Linux .NET Core projelerinde derleme — bu kapsayıcı varsayılan Docker Linux ana bilgisayarına çalıştığından.

[Docker compose.ci.build.yml](https://github.com/dotnet/eShopOnContainers/blob/master/docker-compose.ci.build.yml) için aşağıdaki kod, görüntü (eShopOnContainers parçası) içeren dosya. Kullanarak bir yapı kapsayıcı başlayacağını görebilirsiniz [aspnetcore/microsoft-yapı](https://hub.docker.com/r/microsoft/aspnetcore-build/) görüntü.

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

* İle başlayarak **.NET Core 2.0**, `dotnet restore` komutu yürütür otomatik olarak zaman `dotnet publish` komut yürütülürse.

Yapı kapsayıcı hazır ve çalışır hale geldikten sonra .NET SDK'sı dotnet geri yükleme çalıştırır ve dotnet .NET BITS derlemek için Çözümdeki tüm projeleri karşı komutları yayımlayın. EShopOnContainers de TypeScript ve Angular için istemci kodu dayalı bir SPA olduğundan, eylem .NET BITS ile ilgili değildir ancak bu bu durumda, bu da npm, JavaScript bağımlılıklarla denetlemesi gerekir.

Dotnet komutu derlemeleri yayımlamak ve her projenin klasörüne derlenmiş çıktısı yayımlar... Şekil 8-15'te gösterildiği gibi /obj/Docker/publish klasör.

![](./media/image16.png)

**Şekil 8-15.** Komut dotnet tarafından oluşturulan ikili dosyaları yayımlama

#### <a name="creating-the-docker-images-from-the-cli"></a>CLI üzerinden Docker görüntüleri oluşturma

Uygulama çıkış (içinde her proje) ilgili klasörlere yayımlandığında, sonraki adıma gerçekten Docker görüntüleri oluşturmaktır. Bunu yapmak için docker-compose yapı kullanın ve Şekil 8-16'da gösterildiği gibi komutları docker-oluşturun.

![](./media/image17.png)

**Şekil 8-16.** Docker görüntülerinizi oluşturmak ve çalışan kapsayıcılar

Şekil 8-17'de nasıl docker-compose komutu çalıştırır yapı görebilirsiniz.

![](./media/image18.png)

**Şekil 8-17**. Docker ile Docker görüntülerinizi oluşturmak-yapı komutu oluşturma

Docker-compose arasındaki farkı oluşturmak ve docker-oluşturmanıza komutları olan docker-oluşturan hem derlemeleri hem de başlatır görüntülerini yedekleyin.

Visual Studio kullandığınızda, tüm bu adımları perde arkasında gerçekleştirilir. Visual Studio .NET uygulamanızı derler, Docker görüntülerini oluşturur ve kapsayıcılar Docker ana bilgisayara dağıtır. Visual Studio Docker içinde doğrudan Visual Studio'dan çalıştırma kapsayıcılarınızı hata ayıklama özelliği gibi ek özellikler sunar.

Burada genel takeway aynı şekilde CI/CD hattınızı yapı, uygulamanızı mümkün olan — bir yerel makine yerine bir kapsayıcısından. Oluşturulan görüntüler sahip sonra sonra Docker görüntüleri docker kullanarak çalıştırmak yeterlidir-komutu oluşturun.

#### <a name="additional-resources"></a>Ek kaynaklar

-   **Bir kapsayıcı bitten oluşturma: bir Windows CLI ortamında (dotnet CLI, Docker CLI ve VS Code) eShopOnContainers çözümü kurma**
    [*https://github.com/dotnet/eShopOnContainers/wiki/ 03.-Setting-the-eShopOnContainers-Solution-Up-in-a-Windows-CLI-Environment-(dotnet-CLI,-Docker-CLI-and-VS-Code)*](https://github.com/dotnet/eShopOnContainers/wiki/03.-Setting-the-eShopOnContainers-solution-up-in-a-Windows-CLI-environment-(dotnet-CLI,-Docker-CLI-and-VS-Code))


>[!div class="step-by-step"]
[Önceki] (veri-güdümlü-crud-microservice.md) [sonraki] (veritabanı sunucu container.md)
