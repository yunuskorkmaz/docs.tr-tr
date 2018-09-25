---
title: Docker-compose.yml ile çok Kapsayıcılı uygulamanızı tanımlama
description: Kapsayıcılı .NET uygulamaları için .NET mikro hizmet mimarisi | Docker-compose.yml ile çok Kapsayıcılı uygulamanızı tanımlama
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/30/2017
ms.openlocfilehash: d1c4166129716ccbbc86855e38d631f493b82290
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2018
ms.locfileid: "46937611"
---
# <a name="defining-your-multi-container-application-with-docker-composeyml"></a>Docker-compose.yml ile çok Kapsayıcılı uygulamanızı tanımlama 

Bu kılavuzdaki [docker-compose.yml](https://docs.docker.com/compose/compose-file/) dosya bölümünde tanıtılmıştır [4. adım. Çok kapsayıcılı Docker uygulaması oluştururken, hizmetlerinizi docker-compose.yml tanımlamak](#step4_define_svcs_in_docker_compose_yml). Ancak, daha ayrıntılı olarak incelenmesi yararlı olan docker-compose dosyaları kullanmak için ek yolu vardır.

Örneğin, docker-compose.yml dosyası çok Kapsayıcılı uygulamanızı dağıtmak istediğiniz nasıl açıkça tanımlayabilirsiniz. İsteğe bağlı olarak, özel Docker görüntülerinizi oluşturmak için nasıl yükleyeceksiniz tanımlayabilirsiniz. (Özel Docker görüntüleri ile Docker CLI'yı da oluşturulabilir.)

Temel olarak, her kapsayıcıları dağıtmak istediğiniz ek olarak her kapsayıcı dağıtımı için belirli özellikleri tanımlar. Bir çoklu kapsayıcı dağıtım açıklama dosyası oluşturduktan sonra tek bir eylem tarafından düzenlenen tüm çözüm dağıtabileceğiniz [docker compose up](https://docs.docker.com/compose/overview/) CLI komutunu veya dağıtabilir, saydam Visual Studio'dan. Aksi takdirde, komutu komut satırından çalıştırın docker'ı kullanarak kapsayıcı tarafından kapsayıcı birden çok adımda dağıtmak için Docker CLI'yı kullanmak gerekir. Bu nedenle, docker-compose.yml tanımlanan her bir hizmet tam olarak bir resim belirtin veya bu yapı gerekir. Diğer anahtarlar isteğe bağlıdır ve kendi docker komut satırı ortaklarınıza çalıştırmak için benzer.

Aşağıdaki YAML koduna hizmetine örneği için bir olası genel ancak tek docker-compose.yml dosyası tanımıdır. Bu gerçek docker-compose dosyasından hizmetine değildir. Bunun yerine, tek bir dosyada en iyi değil, bir basit ve birleştirilmiş sürüm olduğu şekilde çalışmak için docker compose dosyaları, daha sonra açıklanacaktır gibi.

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

Hizmetler bu dosyadaki kök anahtardır. Bu anahtarın altında dağıtmak ve yürüttüğünüzde çalıştırmak istediğiniz hizmetleri tanımlamakta docker compose up komutu ya da bu docker-compose.yml dosyasını kullanarak Visual Studio'dan dağıtırken. Bu durumda, docker-compose.yml dosyası aşağıdaki listede açıklandığı gibi tanımlı, birden çok hizmet yok.

-   Sunucu tarafı c mikro hizmetler kullanan ASP.NET Core MVC uygulaması da dahil olmak üzere kapsayıcı webmvc\#

-   catalog.api Kataloğu ASP.NET Core Web API'si mikro hizmet de dahil olmak üzere kapsayıcı

-   ASP.NET Core Web API'si sıralama mikro hizmet de dahil olmak üzere kapsayıcı ordering.api

-   Linux için mikro hizmetler veritabanlarını barındıran SQL Server çalıştıran kapsayıcı SQL.Data

-   Sepet ASP.NET Core Web API'si mikro hizmet ile kapsayıcı Basket.api

-   Basket.Data sepet veritabanıyla bir REDIS önbelleği olarak REDIS cache hizmeti çalıştıran kapsayıcısı

### <a name="a-simple-web-service-api-container"></a>Basit bir Web hizmeti API'si kapsayıcı

Tek bir kapsayıcı'na Odaklanıldığında, basit bir tanımı catalog.api container-mikro hizmet vardır:

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

Bu kapsayıcı hizmeti, temel yapılandırması aşağıdaki gibidir:

-   Bu özel eshop/catalog.api görüntüye bağlıdır. Basitlik'ın çok için hiçbir derleme yok: anahtar dosyasında ayarı. Bu görüntü daha önce (docker derleme ile) oluşturulmuş gerekir veya herhangi bir Docker kayıt defterinden (docker pull komutuyla) indirilip anlamına gelir.

-   ConnectionString Kataloğu veri modeli içeren SQL Server örneğine erişmesi için Entity Framework tarafından kullanılacak bağlantı dizesiyle adlı bir ortam değişkeni tanımlar. Bu durumda, aynı SQL Server kapsayıcı birden çok veritabanı tutuyor. Bu nedenle, daha az bellek için Docker geliştirme makinenizde gerekir. Ancak, her bir mikro hizmet veritabanı için bir SQL Server kapsayıcı dağıtabilirsiniz.

-   SQL Server sql.data, Linux için SQL Server örneğini çalıştıran kapsayıcısı için kullanılan aynı adı olan addır. Bu kullanışlıdır; Bu ad çözümlemesi (Docker konağı dahili) kullanabilmek için ağ adresi çözer, bu diğer kapsayıcılardan eriştiğiniz kapsayıcılar için iç IP bilmek zorunda kalmazsınız.

Bağlantı dizesi bir ortam değişkeni tarafından tanımlı olduğundan, farklı bir mekanizma aracılığıyla ve farklı bir zamanda bu değişkeni ayarlayabilirsiniz. Örneğin, son konaklar veya CI/CD işlem hatlarınızı Azure DevOps Hizmetleri veya tercih edilen DevOps sisteminizi gelen yapmakta üretime dağıtırken farklı bağlantı dizesi ayarlayabilirsiniz.

-   Bu, Docker konağının catalog.api hizmetinde iç erişimi için 80 numaralı bağlantı noktasını kullanıma sunar. Konak şu anda bir Linux VM Linux için Docker görüntü temel alan, ancak bunun yerine bir Windows görüntüsü üzerinde çalıştırmak için kapsayıcı yapılandırabilirsiniz olmasıdır.

-   Bu, kullanıma sunulan bağlantı noktası (Linux VM) Docker konak makinedeki 5101 numaralı bağlantı noktasına kapsayıcı üzerindeki 80 iletir.

-   Web hizmeti sql.data hizmet (SQL Server örneği için bir kapsayıcı içinde çalışan Linux veritabanı) bağlar. Bu bağımlılık belirttiğinizde, sql.data kapsayıcı zaten başlamış catalog.api kapsayıcı tamamlanıncaya kadar çalışmaz; Bu ilk catalog.api SQL Server veritabanına sahip gerektiğinden önemli ve çalışır durumdadır. Docker kapsayıcı düzeyinde iade ettiğinden ancak, bu tür bir kapsayıcı bağımlılık çoğu durumda, yeterli değildir. Üstel geri alma ile yeniden deneme mantığı, istemci mikro Hizmetleri uygulamak için önerilir, bu nedenle bazen hizmeti (büyük/küçük harf bu SQL Server) hala hazır olmayabilir. Bu şekilde, bir bağımlılık kapsayıcı kısa bir süre için hazır değilse, uygulama hala dayanıklı olacak.

-   Dış sunucuları erişmesine izin vermek için yapılandırılmış: ek\_konakları ayarlama dış sunucuların ya da Docker konağı dışında makineleri erişmenizi sağlar (diğer bir deyişle, varsayılan bir Docker geliştirme olan bir Linux VM dışında barındırma) gibi bir yerel SQL Sunucu örneği geliştirme koruyun.

Aşağıdaki bölümlerde ele alınacaktır diğer, daha gelişmiş bir docker-compose.yml ayarları vardır.

### <a name="using-docker-compose-files-to-target-multiple-environments"></a>Kullanarak docker-compose dosyaları, birden çok ortama hedeflemek için

Docker-compose.yml dosyaları tanımı dosyaları ve söz konusu biçimini birden çok altyapıları tarafından kullanılabilir. En basit araçtır docker-compose komutu, ancak Düzenleyicileri (örneğin, Docker Swarm) Bu dosya ayrıca anlama gibi diğer araçları.

Kullanarak bu nedenle, docker compose komutuyla aşağıdaki ana senaryoları hedefleyebilir.

#### <a name="development-environments"></a>Geliştirme ortamları

Uygulama geliştirirken, yalıtılmış bir geliştirme ortamında bir uygulamayı çalıştırmak önemlidir. Kullanabileceğiniz docker-compose, ortam veya kullandığı docker perde compose Visual Studio kullanmak için CLI komutu.

Docker-compose.yml dosyasını yapılandırın ve hizmeti tüm uygulama bağımlılıklarınızın (diğer hizmetleri, önbellek, veritabanları, kuyruklar, vb.) belge sağlar. Kullanarak CLI komut docker-compose, oluşturabilir ve her bir bağımlılığın için bir veya daha fazla kapsayıcıları tek bir komutla Başlat (docker compose up).

Docker-compose.yml dosyaları Docker altyapısı tarafından yorumlanan yapılandırma dosyalarını ancak uygun belge dosyaları çok kapsayıcılı bir uygulama, oluşumunu hakkında da görür.

#### <a name="testing-environments"></a>Test ortamları

Herhangi bir sürekli dağıtım (CD) veya sürekli tümleştirme (CI) işlem önemli bir parçası olan birim testleri ve tümleştirme testleri. Bu otomatik testleri yalıtılmış bir ortam gerektirdiğinden, kullanıcılar ya da herhangi bir değişiklik uygulamanın veri etkilenmez.

Docker Compose ile oluşturabilir ve bu yalıtılmış bir ortamda çok bir kolayca komut istemi veya komut dosyaları, aşağıdaki komutları gibi birkaç komut yok:

```
docker-compose up -d
./run_unit_tests
docker-compose down
```

#### <a name="production-deployments"></a>Üretim dağıtımları

Oluştur, uzak bir Docker altyapısı dağıtmak için de kullanabilirsiniz. Tipik bir durumda, tek bir Docker konağı örneği dağıtmaktır (üretim VM veya sunucu ile sağlanan gibi [Docker Machine](https://docs.docker.com/machine/overview/)). Ancak tüm olabilir [Docker Swarm](https://docs.docker.com/swarm/overview/) kümeleri ayrıca docker-compose.yml dosyaları ile uyumlu olmadığından, küme.

Herhangi diğer orchestrator (Azure Service Fabric, Mesos DC/OS, Kubernetes, vb.) kullanıyorsanız, bu docker-compose.yml, ancak diğer orchestrator tarafından gereken biçimde gibi Kurulum ve meta verileri yapılandırma ayarlarını eklemek gerekebilir.

Her iki durumda da docker-compose geliştirme, test ve üretim iş akışları için kullanışlı bir aracı ve meta veri biçimi, üretim iş akışı, kullanmakta olduğunuz orchestrator üzerinde farklılık gösterebilir ancak.

### <a name="using-multiple-docker-compose-files-to-handle-several-environments"></a>Birden fazla docker-compose birkaç ortamlarını işleyecek şekilde dosyaları

Farklı ortamlar hedeflenirken birden çok kullanması gereken compose dosyası. Bu ortama bağlı olarak birden çok yapılandırma çeşitleri oluşturmanıza olanak sağlar.

#### <a name="overriding-the-base-docker-compose-file"></a>Temel docker-compose dosyası geçersiz kılma

Önceki bölümlerde gösterildiği Basitleştirilmiş örneklerde gösterildiği gibi bir tek docker-compose.yml dosyası kullanabilirsiniz. Bununla birlikte, çoğu uygulama için önerilmez.

Varsayılan olarak, iki dosya, docker-compose.yml ve docker-compose.override.yml isteğe bağlı dosya oluşturma okur. Şekil 8-11'de gösterildiği gibi ne zaman, Visual Studio kullanarak ve Docker desteği, Visual Studio ayrıca etkinleştirme, CI/CD işlem hatlarınızı gibi Azure DevOps hizmetlerinde kullanmak için bir ek docker compose.ci.build,yml dosyası oluşturur.

![](./media/image12.png)

**Şekil 8-11**. docker-compose dosyası Visual Studio 2017

Visual Studio Code veya Sublime, gibi herhangi bir düzenleyici ile docker-compose dosyaları düzenleyin ve uygulamayı çalıştırın docker-compose up komutu.

Kural gereği, docker-compose.yml dosyasını temel yapılandırma ve diğer statik ayarlarını içerir. Hizmet yapılandırması, hedeflediğiniz dağıtım ortamı bağlı olarak değiştirmemelisiniz anlamına gelir.

Adından da anlaşılacağı gibi docker-compose.override.yml dosyası, dağıtım ortamınıza bağlıdır yapılandırma gibi temel yapılandırma geçersiz yapılandırma ayarlarını içerir. Ayrıca, farklı adlara sahip birden fazla geçersiz kılma dosyası olabilir. Geçersiz kılma dosyalar genellikle uygulama ancak belirli bir ortam veya bir dağıtım için gerekli ek bilgileri içerir.

#### <a name="targeting-multiple-environments"></a>Birden çok ortama hedefleme

Tipik bir kullanım örneği olan birden çok tanımlarken compose dosyaları, üretim gibi birden çok ortamı hazırlama, CI veya geliştirme hedefleyebilir. Bu farklar desteklemek için Şekil 8-12'de gösterildiği gibi birden çok dosyalarına oluşturma yapılandırmanızı bölebilirsiniz.

![](./media/image13.png)

**Şekil 8-12**. Geçersiz kılma değerleri temel docker-compose.yml dosyasındaki dosyaları birden çok docker-compose

Temel docker-compose.yml dosyası ile başlayın. Bu temel dosya ortamına bağlı olarak değiştirmeyin temel ya da statik yapılandırma ayarlarını içeren gerekir. Örneğin, hizmetine taban dosyası olarak aşağıdaki docker-compose.yml dosyası vardır.

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

Temel docker-compose.yml dosyasındaki değerleri nedeniyle farklı bir hedef dağıtım ortamlarının değiştirmemesi gerekir.

Örneğin, webmvc hizmet tanımı üzerinde odaklanmak, nasıl bu bilgileri çok hedefleyen hangi ortamı ne olursa olsun aynıdır görebilirsiniz. Aşağıdaki bilgileri vardır:

-   Hizmet adı: webmvc.

-   Kapsayıcının özel görüntü: Elektronik Mağaza/webmvc.

-   Kullanmak için hangi Dockerfile belirten özel Docker görüntüsü oluşturmak için komutu.

-   Bağımlılıkları diğer hizmetleri, bir bağımlılık kapsayıcıları başlatılıncaya kadar bu kapsayıcı başlamaz.

Ek yapılandırma olabilir, ancak önemli temel docker-compose.yml dosyasında, yalnızca ortamlar arasında ortak olan bilgiyi ayarlamak istediğiniz noktasıdır. Ardından docker-compose.override.yml veya benzer dosyaları üretim ya da hazırlık, her ortam için belirli yapılandırma yerleştirmeniz gerekir.

Genellikle, docker-compose.override.yml hizmetine aşağıdaki örnekte olduğu gibi geliştirme ortamınız için kullanılır:

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

Bu örnekte, geliştirme geçersiz kılma yapılandırmasını konağa bazı bağlantı noktalarını kullanıma sunar, ortam değişkenlerini tanımlar URL'lerini yönlendirmek ve geliştirme ortamı için bağlantı dizelerini belirtir. Bu ayarlar, tüm yeni geliştirme ortamına yöneliktir.

Çalıştırdığınızda `docker-compose up` (veya Visual Studio'dan başlatmak), her iki dosya birleştirme gibi komut geçersiz kılmaları otomatik olarak okur.

Farklı yapılandırma değerleri, bağlantı noktası veya bağlantı dizeleri üretim ortamı için başka bir Compose dosyasının istediğinizi varsayalım. Adlı bir dosya gibi başka bir geçersiz kılma dosyası oluşturabilirsiniz `docker-compose.prod.yml` farklı ayarlar ve ortam değişkenleri.  Bu dosyayı farklı bir Git deposunda depolanabilir veya yönetilen ve farklı bir takım tarafından güvenli hale getirilmiş.

#### <a name="how-to-deploy-with-a-specific-override-file"></a>Bir özel geçersiz kılma dosyası ile dağıtma

Farklı ada sahip birden fazla geçersiz kılma dosyası veya bir geçersiz kılma dosyası kullanmak için -f seçeneğiyle kullanabilirsiniz docker-compose komutu ve dosyaları belirtin. Komut satırında belirtildikleri sırada birleştirmeleri dosyalarını oluşturun. Aşağıdaki örnek, geçersiz kılma dosyalarıyla dağıtma gösterilmektedir.

```
docker-compose -f docker-compose.yml -f docker-compose.prod.yml up -d
```

#### <a name="using-environment-variables-in-docker-compose-files"></a>Ortam değişkenlerini kullanarak içinde docker-compose dosyası

Biz önceki örneklerde gösterildiği gibi ortam değişkenlerinden yapılandırma bilgilerini almak için özellikle de üretim ortamlarında, kullanışlı. Docker-compose dosyalarınızı söz dizimini kullanarak bir ortam değişkeni başvurusu \${MY\_VAR}. Aşağıdaki satırı bir docker compose.prod.yml dosyasından bir ortam değişkeninin değerini yapmayı gösterir.

```yml
IdentityUrl=http://${ESHOP_PROD_EXTERNAL_DNS_NAME_OR_IP}:5105
```

Ortam değişkenlerini oluşturuldu ve ana bilgisayar ortamına bağlı olarak, farklı şekillerde başlatıldı (Linux, Windows, bulut kümesine, vs.). Ancak, uygun bir yaklaşım bir .env dosyasında kullanmaktır. .Env dosyasında varsayılan ortam değişkenleri bildirme docker-compose dosyalarını destekler. Bu değerler ortam değişkenleri için varsayılan değerlerdir. Ancak, her ortamlarınızda (ana bilgisayar işletim sistemi veya ortam değişkenlerini kümenizden) tanımlamış olabileceği değerlere göre kılınabilir. .Env dosyasında bu klasöre yerleştirdiğiniz yere docker-compose komutu yürütülmediyse.

Aşağıdaki örnek, bir .env dosyasında gibi gösterir [.env](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/.env) hizmetine uygulamanın dosyası.

```
# .env file

ESHOP_EXTERNAL_DNS_NAME_OR_IP=localhost

ESHOP_PROD_EXTERNAL_DNS_NAME_OR_IP=10.121.122.92
```

Docker-compose bekliyor biçiminde bir .env dosyasında her satırı &lt;değişkeni&gt;=&lt;değer&gt;.

Çalışma zamanı ortamında her zaman ayarlanan değerleri içinde .env dosyasında tanımlı değerlerin üzerine yazılacağını unutmayın. Benzer şekilde, geçirilen komut satırı komut bağımsız değişkenlerinin değerleri de .env dosyasında ayarlanan varsayılan değerlerini geçersiz kılar.

#### <a name="additional-resources"></a>Ek kaynaklar

-   **Genel Bakış docker Compose**
    [*https://docs.docker.com/compose/overview/*](https://docs.docker.com/compose/overview/)

-   **Birden çok Compose dosyaları**
    [*https://docs.docker.com/compose/extends/\#multiple-compose-files*](https://docs.docker.com/compose/extends/#multiple-compose-files)

### <a name="building-optimized-aspnet-core-docker-images"></a>ASP.NET Core Docker görüntüleri oluşturma en iyi duruma getirilmiş

Internet kaynaklarında Docker ve .NET Core araştırıyorsanız, Basitlik, bir kapsayıcıya kaynağınızı kopyalayarak bir Docker görüntüsü oluşturma gösteren dockerfile'ları bulabilirsiniz. Bu örnekler, basit bir yapılandırma öğesini kullanarak bir Docker görüntüsü, uygulamanızla birlikte paketlenmiş ortamıyla sağlayabilirsiniz önerin. Aşağıdaki örnek, basit bir Dockerfile içinde bu damarlı gösterir.

```
FROM microsoft/dotnet

WORKDIR /app

ENV ASPNETCORE_URLS http://+:80

EXPOSE 80

COPY . .

RUN dotnet restore

ENTRYPOINT ["dotnet", "run"]
```

Böyle bir Dockerfile çalışır. Ancak, özellikle de üretim görüntülerinin görüntülerinizi önemli ölçüde iyileştirebilir.

Kapsayıcı ve mikro hizmetler modeli sürekli kapsayıcıları başlıyor. Kapsayıcıları kullanarak normal şekilde kapsayıcı atılabilir olduğundan Uyuyan bir kapsayıcı yeniden başlatmaz. Düzenleyiciler (örneğin, Docker Swarm, Kubernetes, DCOS veya Azure Service Fabric) yalnızca görüntüleri yeni bir örneğini oluşturun. Ne bu örnekleme işlemi daha hızlı olacak şekilde nasıl yapılandırıldığında, uygulama ön derleme tarafından en iyi duruma getirme gerektiğini anlamına gelir. Kapsayıcı başlatıldığında, çalıştırmaya hazır olmalıdır. Olmayan geri yükleme ve çalışma zamanında derleme, .NET Core ve Docker birçok blog gönderileri gördüğünüz gibi dotnet kullanarak geri yükleme ve dotnet dotnet CLI komutları, yapı.

.NET ekibi .NET Core ve ASP.NET Core kapsayıcı iyileştirilmiş bir çerçeve yapmak için önemli işleri yapmak. Yalnızca .NET Core küçük bellek Ayak izi ile basit bir çerçeve olan; Takım başlangıç performansı üzerinde odaklanır ve bazı en iyi duruma getirilmiş Docker görüntüleri gibi üretilen [microsoft/aspnetcore](https://hub.docker.com/r/microsoft/aspnetcore/) görüntü adresinde [Docker Hub](https://hub.docker.com/r/microsoft/aspnetcore/), normal kolaylığına [ Microsoft/dotnet](https://hub.docker.com/r/microsoft/dotnet/) veya [microsoft/nanoserver](https://github.com/dotnet/dotnet-docker/blob/master/1.0/nanoserver/runtime/Dockerfile) görüntüler. [Microsoft/aspnetcore](https://hub.docker.com/r/microsoft/aspnetcore/) otomatik ayarı aspnetcore görüntüsü sağlar\_URL'ler 80 numaralı bağlantı noktasını ve öncesi ngend önbellek derlemelerin; bu ayarların her ikisini de daha hızlı başlangıç neden.

#### <a name="additional-resources"></a>Ek kaynaklar

-   **ASP.NET Core ile Docker görüntü oluşturma en iyi duruma getirilmiş**
    [*https://blogs.msdn.microsoft.com/stevelasker/2016/09/29/building-optimized-docker-images-with-asp-net-core/*](https://blogs.msdn.microsoft.com/stevelasker/2016/09/29/building-optimized-docker-images-with-asp-net-core/)

### <a name="building-the-application-from-a-build-ci-container"></a>Bir derleme (CI) kapsayıcısından uygulama oluşturma

Şekil 8-13'te gösterildiği şekilde, bir derleme makinesi veya uygulamanızı oluşturmak için VM oluşturmak ihtiyacınız yoktur, Docker'ın başka bir avantajı uygulamanızı önceden yapılandırılmış bir kapsayıcı oluşturabilirsiniz içindir. Geliştirme makinenizde çalıştırarak test, yapı kapsayıcısı veya kullanabilirsiniz. Ancak daha da ilginç nedir, CI (sürekli tümleştirme) hattından aynı derleme kapsayıcısı kullanabilirsiniz.

![](./media/image14.png)

**Şekil 8-13**. Docker derleme-kapsayıcı .NET ikili dosyaları derleme 

Bu senaryo için sağladığımız [microsoft/aspnetcore-build](https://hub.docker.com/r/microsoft/aspnetcore-build/) derlemek ve ASP.NET Core uygulamaları oluşturmak için kullanabileceğiniz bir görüntüsü. Çıkış temel alan bir görüntü yerleştirilir [microsoft/aspnetcore](https://hub.docker.com/r/microsoft/aspnetcore/) da daha önce not ettiğiniz en iyi duruma getirilmiş çalışma zamanı görüntünün görüntü.

.NET Core, ASP.NET SDK'sı, npm, dahil olmak üzere bir ASP.NET Core uygulaması derlemek için ihtiyacınız olan her şey aspnetcore-build görüntüsünü içeren Bower, Gulp, vs.

Bu bağımlılıklar oluşturma zamanında ihtiyacımız var. Ancak görüntü gereksiz derecede büyük hale getirir çünkü bu uygulama ile birlikte çalışma zamanında Yürüt istiyoruz değil. Hizmetine uygulamada, uygulamayı oluşturmak yalnızca çalıştırarak kapsayıcısından aşağıdaki docker compose komutuyla.

```
  docker-compose -f docker-compose.ci.build.yml up
```

Şekil 8-14, bu komut komut satırında çalıştıran gösterir.

![](./media/image15.png)

**Şekil 8-14.** .NET uygulamanızı bir kapsayıcı oluşturma

Gördüğünüz gibi çalışmakta olan kapsayıcıyı CI yapısı olduğu\_1 kapsayıcı. Derleme ve Bilgisayarınızdan yerine ilgili kapsayıcıdaki tüm uygulama içinden yapı bu aspnetcore-build görüntüye bağlıdır. Diğer bir deyişle neden gerçekte bu oluşturma ve Linux'ta .NET Core projelerini derlemek — bu kapsayıcı varsayılan Docker Linux ana bilgisayarında çalıştığından.

[Docker-compose.ci.build.yml](https://github.com/dotnet/eShopOnContainers/blob/master/docker-compose.ci.build.yml) için o yansıma (hizmetine parçası) aşağıdaki kodu içeren dosya. Kullanarak yapı kapsayıcı başladıktan gördüğünüz [microsoft/aspnetcore-build](https://hub.docker.com/r/microsoft/aspnetcore-build/) görüntü.

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

* İle başlayarak **.NET Core 2.0**, `dotnet restore` komutu yürütür otomatik olarak zaman `dotnet publish` komutu yürütülür.

Derleme kapsayıcısı çalışır duruma geldikten sonra .NET SDK'sı dotnet restore çalıştırır ve dotnet .NET bit derle için Çözümdeki tüm projeleri komutları yayımlayın. Hizmetine de TypeScript ve Angular için istemci kodu dayalı bir SPA olduğundan, eylem .NET BITS ile ilişkili değildir, ancak bu durumda, bu da npm, JavaScript bağımlılıklarla denetlemesi gerekir.

Dotnet komut yapılar yayımlama ve her projesinin klasörüne içinde derlenen Çıkışta yayımlar... Şekil 8-15'te gösterildiği gibi /obj/Docker/publish klasör.

![](./media/image16.png)

**Şekil 8-15.** Dotnet tarafından oluşturulan ikili dosyaları yayımlama komutu

#### <a name="creating-the-docker-images-from-the-cli"></a>CLI'dan Docker görüntüleri oluşturma

Uygulama çıktısı (her projede) ilgili klasörleri yayımlandıktan sonra sonraki adım gerçekten Docker görüntüleri oluşturmaktır. Bunu yapmak için docker-compose derleme kullanın ve Şekil 8-16 gösterildiği gibi komutları docker-compose.

![](./media/image17.png)

**Şekil 8-16.** Docker görüntülerinizi oluşturmak ve çalışan kapsayıcılar

Şekil 8-17'de nasıl docker-compose komutu çalıştırmaları yapı görebilirsiniz.

![](./media/image18.png)

**Şekil 8-17**. Docker ile Docker görüntüleri oluşturma-oluşturma komutu oluştur

Docker-compose arasındaki fark, derleme ve docker compose up komutları olan docker-compose derlemeler ve başlar görüntüleri.

Visual Studio kullandığınızda, bu adımların tümünü arka planda gerçekleştirilir. Visual Studio .NET uygulamanızı derleyen, Docker görüntüleri oluşturur ve Docker ana bilgisayar kapsayıcıları dağıtır. Visual Studio, Docker, doğrudan Visual Studio'dan çalıştırma kapsayıcılarınızı hata ayıklama yapabilme gibi ek özellikler sunar.

Genel takeway burada aynı şekilde CI/CD ardışık düzeninizi derleme, uygulamanızı oluşturmak üzere mümkün olduğu — bir yerel makine yerine bir kapsayıcısından. Oluşturulan görüntüleri atandıktan sonra sonra docker kullanarak Docker görüntülerini çalıştırmak yeterlidir-compose komutu.

#### <a name="additional-resources"></a>Ek kaynaklar

-   **Bir kapsayıcı bitten oluşturma: bir Windows CLI ortamda (dotnet CLI, Docker CLI ve VS Code) hizmetine çözüm ayarlama**
    [*https://github.com/dotnet/eShopOnContainers/wiki/03.-Setting-the-eShopOnContainers-solution-up-in-a-Windows-CLI-environment-(dotnet-CLI, - Docker - CLI- ve -VS-kod)*](https://github.com/dotnet/eShopOnContainers/wiki/03.-Setting-the-eShopOnContainers-solution-up-in-a-Windows-CLI-environment-(dotnet-CLI,-Docker-CLI-and-VS-Code))


>[!div class="step-by-step"]
[Önceki](data-driven-crud-microservice.md)
[İleri](database-server-container.md)
