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
# <a name="defining-your-multi-container-application-with-docker-composeyml"></a>Docker-compose.yml ile çok Kapsayıcılı uygulamanızı tanımlama 

Bu kılavuzdaki [docker-compose.yml](https://docs.docker.com/compose/compose-file/) dosya bölümünde tanıtılmıştır [4. adım. Çok kapsayıcılı Docker uygulaması oluştururken, hizmetlerinizi docker-compose.yml tanımlamak](../docker-application-development-process/docker-app-development-workflow.md#step-4-define-your-services-in-docker-composeyml-when-building-a-multi-container-docker-application). Ancak, daha ayrıntılı olarak incelenmesi yararlı olan docker-compose dosyaları kullanmak için ek yolu vardır.

Örneğin, docker-compose.yml dosyası çok Kapsayıcılı uygulamanızı dağıtmak istediğiniz nasıl açıkça tanımlayabilirsiniz. İsteğe bağlı olarak, özel Docker görüntülerinizi oluşturmak için nasıl yükleyeceksiniz tanımlayabilirsiniz. (Özel Docker görüntüleri ile Docker CLI'yı da oluşturulabilir.)

Temel olarak, her kapsayıcıları dağıtmak istediğiniz ek olarak her kapsayıcı dağıtımı için belirli özellikleri tanımlar. Bir çoklu kapsayıcı dağıtım açıklama dosyası oluşturduktan sonra tek bir eylem tarafından düzenlenen tüm çözüm dağıtabileceğiniz [docker compose up](https://docs.docker.com/compose/overview/) CLI komutunu veya dağıtabilir, saydam Visual Studio'dan. Aksi takdirde, Docker CLI'yı kullanarak kapsayıcı tarafından kapsayıcı birden çok adımda dağıtmak için kullanmanız gerekecektir `docker run` komut satırından komutu. Bu nedenle, docker-compose.yml tanımlanan her bir hizmet tam olarak bir resim belirtin veya bu yapı gerekir. Diğer anahtarlar isteğe bağlıdır ve alınmak üzere kendi `docker run` komut satırı ortaklarınıza.

Aşağıdaki YAML koduna hizmetine örneği için bir olası genel ancak tek docker-compose.yml dosyası tanımıdır. Bu gerçek docker-compose dosyasından hizmetine değildir. Bunun yerine, tek bir dosyada en iyi değil, bir basit ve birleştirilmiş sürüm olduğu şekilde çalışmak için docker compose dosyaları, daha sonra açıklanacaktır gibi.

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

Hizmetler bu dosyadaki kök anahtardır. Bu anahtarın altında dağıtmak ve yürüttüğünüzde çalıştırmak istediğiniz hizmetleri tanımlamakta `docker-compose up` komut ya da bu docker-compose.yml dosyasını kullanarak Visual Studio'dan dağıtırken. Bu durumda, docker-compose.yml dosyası aşağıdaki tabloda açıklandığı gibi tanımlı, birden çok hizmet yok.

| Hizmet adı | Açıklama |
|--------------|-------------|
| webmvc       | Sunucu tarafı c mikro hizmetler kullanan ASP.NET Core MVC uygulaması da dahil olmak üzere kapsayıcı\#|
| catalog.api  | Katalog ASP.NET Core Web API'si mikro hizmet de dahil olmak üzere kapsayıcı |
| ordering.api | ASP.NET Core Web API'si sıralama mikro hizmet de dahil olmak üzere kapsayıcı |
| SQL.Data     | Linux için mikro hizmetler veritabanlarını barındıran SQL Server çalıştıran kapsayıcı |
| Basket.api   | Sepet ASP.NET Core Web API'si mikro hizmet ile kapsayıcı |
| Basket.Data  | REDIS çalıştıran kapsayıcısı önbellek hizmeti, sepet veritabanı olarak REDIS önbelleği ile |

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

Docker-compose.yml dosyaları tanımı dosyaları ve söz konusu biçimini birden çok altyapıları tarafından kullanılabilir. En basit bir araçtır docker-compose komutu.

Kullanarak bu nedenle, docker compose komutuyla aşağıdaki ana senaryoları hedefleyebilir.

#### <a name="development-environments"></a>Geliştirme ortamları

Uygulama geliştirirken, yalıtılmış bir geliştirme ortamında bir uygulamayı çalıştırmak önemlidir. Kullanabileceğiniz docker-compose, ortam veya kullandığı docker perde compose Visual Studio kullanmak için CLI komutu.

Docker-compose.yml dosyasını yapılandırın ve hizmeti tüm uygulama bağımlılıklarınızın (diğer hizmetleri, önbellek, veritabanları, kuyruklar, vb.) belge sağlar. Kullanarak CLI komut docker-compose, oluşturabilir ve her bir bağımlılığın için bir veya daha fazla kapsayıcıları tek bir komutla Başlat (docker compose up).

Docker-compose.yml dosyaları Docker altyapısı tarafından yorumlanan yapılandırma dosyalarını ancak uygun belge dosyaları çok kapsayıcılı bir uygulama, oluşumunu hakkında da görür.

#### <a name="testing-environments"></a>Test ortamları

Herhangi bir sürekli dağıtım (CD) veya sürekli tümleştirme (CI) işlem önemli bir parçası olan birim testleri ve tümleştirme testleri. Bu otomatik testleri yalıtılmış bir ortam gerektirdiğinden, kullanıcılar ya da herhangi bir değişiklik uygulamanın veri etkilenmez.

Docker Compose ile oluşturabilir ve bu yalıtılmış bir ortamda çok bir kolayca komut istemi veya komut dosyaları, aşağıdaki komutları gibi birkaç komut yok:

```
docker-compose -f docker-compose.yml -f docker-compose-test.override.yml up -d
./run_unit_tests
docker-compose -f docker-compose.yml -f docker-compose.test.override.yml down
```

#### <a name="production-deployments"></a>Üretim dağıtımları

Oluştur, uzak bir Docker altyapısı dağıtmak için de kullanabilirsiniz. Tipik bir durumda, tek bir Docker konağı örneği dağıtmaktır (üretim VM veya sunucu ile sağlanan gibi [Docker Machine](https://docs.docker.com/machine/overview/)).

Herhangi diğer orchestrator (Azure Service Fabric, Kubernetes, vb.) kullanıyorsanız, bu docker-compose.yml, ancak diğer orchestrator tarafından gereken biçimde gibi Kurulum ve meta verileri yapılandırma ayarlarını eklemek gerekebilir.

Her iki durumda da docker-compose geliştirme, test ve üretim iş akışları için kullanışlı bir aracı ve meta veri biçimi, üretim iş akışı, kullanmakta olduğunuz orchestrator üzerinde farklılık gösterebilir ancak.

### <a name="using-multiple-docker-compose-files-to-handle-several-environments"></a>Birden fazla docker-compose birkaç ortamlarını işleyecek şekilde dosyaları

Farklı ortamlar hedeflenirken birden çok kullanması gereken compose dosyası. Bu ortama bağlı olarak birden çok yapılandırma çeşitleri oluşturmanıza olanak sağlar.

#### <a name="overriding-the-base-docker-compose-file"></a>Temel docker-compose dosyası geçersiz kılma

Önceki bölümlerde gösterildiği Basitleştirilmiş örneklerde gösterildiği gibi bir tek docker-compose.yml dosyası kullanabilirsiniz. Bununla birlikte, çoğu uygulama için önerilmez.

Varsayılan olarak, iki dosya, docker-compose.yml ve docker-compose.override.yml isteğe bağlı dosya oluşturma okur. Visual Studio kullanıyorsanız ve Docker desteğini etkinleştirme, Visual Studio ayrıca uygulamayı hata ayıklama için bir ek docker compose.vs.debug.g.yml dosyası oluşturur, Şekil 6-11'de gösterildiği gibi bu klasör obj dosyasında bir göz atabilirsiniz\\Docker \\ ana çözüm klasöründe.

![docker-compose proje dosya yapısı: .dockerignore dosyaları yoksaymak için docker-compose mikro hizmetler için compose.yml, docker-mikro hizmetler ortamını yapılandırmak için compose.override.yml.](./media/image12.png)

**Şekil 6-11**. docker-compose dosyası Visual Studio 2017

Visual Studio Code veya Sublime, gibi herhangi bir düzenleyici ile docker-compose dosyaları düzenleyin ve uygulamayı çalıştırın docker-compose up komutu.

Kural gereği, docker-compose.yml dosyasını temel yapılandırma ve diğer statik ayarlarını içerir. Hizmet yapılandırması, hedeflediğiniz dağıtım ortamı bağlı olarak değiştirmemelisiniz anlamına gelir.

Adından da anlaşılacağı gibi docker-compose.override.yml dosyası, dağıtım ortamınıza bağlıdır yapılandırma gibi temel yapılandırma geçersiz yapılandırma ayarlarını içerir. Ayrıca, farklı adlara sahip birden fazla geçersiz kılma dosyası olabilir. Geçersiz kılma dosyalar genellikle uygulama ancak belirli bir ortam veya bir dağıtım için gerekli ek bilgileri içerir.

#### <a name="targeting-multiple-environments"></a>Birden çok ortama hedefleme

Tipik bir kullanım örneği olan birden çok tanımlarken compose dosyaları, üretim gibi birden çok ortamı hazırlama, CI veya geliştirme hedefleyebilir. Bu farklar desteklemek için Şekil 6-12'de gösterildiği gibi birden çok dosyalarına oluşturma yapılandırmanızı bölebilirsiniz.

![Farklı ortamlar işlemek için birden fazla docker compose*.fml dosyaları birleştirebilirsiniz.](./media/image13.png)

**Şekil 6-12**. Geçersiz kılma değerleri temel docker-compose.yml dosyasındaki dosyaları birden çok docker-compose

Temel docker-compose.yml dosyası ile başlayın. Bu temel dosya ortamına bağlı olarak değiştirmeyin temel ya da statik yapılandırma ayarlarını içeren gerekir. Örneğin, hizmetine taban dosyası olarak (daha az Hizmetleri ile Basitleştirilmiş) aşağıdaki docker-compose.yml dosyası vardır.

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

Bu örnekte, geliştirme geçersiz kılma yapılandırmasını konağa bazı bağlantı noktalarını kullanıma sunar, ortam değişkenlerini tanımlar URL'lerini yönlendirmek ve geliştirme ortamı için bağlantı dizelerini belirtir. Bu ayarlar, tüm yeni geliştirme ortamına yöneliktir.

Çalıştırdığınızda `docker-compose up` (veya Visual Studio'dan başlatmak), her iki dosya birleştirme gibi komut geçersiz kılmaları otomatik olarak okur.

Farklı yapılandırma değerleri, bağlantı noktası veya bağlantı dizeleri üretim ortamı için başka bir Compose dosyasının istediğinizi varsayalım. Adlı bir dosya gibi başka bir geçersiz kılma dosyası oluşturabilirsiniz `docker-compose.prod.yml` farklı ayarlar ve ortam değişkenleri.  Bu dosyayı farklı bir Git deposunda depolanabilir veya yönetilen ve farklı bir takım tarafından güvenli hale getirilmiş.

#### <a name="how-to-deploy-with-a-specific-override-file"></a>Bir özel geçersiz kılma dosyası ile dağıtma

Farklı ada sahip birden fazla geçersiz kılma dosyası veya bir geçersiz kılma dosyası kullanmak için -f seçeneğiyle kullanabilirsiniz docker-compose komutu ve dosyaları belirtin. Komut satırında belirtildikleri sırada birleştirmeleri dosyalarını oluşturun. Aşağıdaki örnek, geçersiz kılma dosyalarıyla dağıtma gösterilmektedir.

```
docker-compose -f docker-compose.yml -f docker-compose.prod.yml up -d
```

#### <a name="using-environment-variables-in-docker-compose-files"></a>Ortam değişkenlerini kullanarak içinde docker-compose dosyası

Biz önceki örneklerde gösterildiği gibi ortam değişkenlerinden yapılandırma bilgilerini almak için özellikle de üretim ortamlarında, kullanışlı. Bir ortam değişkeni kullanarak söz dizimi $ docker-compose dosyalarınızda başvurabilirsiniz {MY\_VAR}. Aşağıdaki satırı bir docker compose.prod.yml dosyasından bir ortam değişkeninin değerini yapmayı gösterir.

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

Docker-compose bekliyor biçiminde bir .env dosyasında her satırı \<değişkeni\>=\<değer\>.

Çalışma zamanı ortamında her zaman ayarlanan değerleri içinde .env dosyasında tanımlı değerlerin üzerine yazılacağını unutmayın. Benzer şekilde, geçirilen komut satırı komut bağımsız değişkenlerinin değerleri de .env dosyasında ayarlanan varsayılan değerlerini geçersiz kılar.

#### <a name="additional-resources"></a>Ek kaynaklar

-   **Genel Bakış docker Compose** <br/>
    [*https://docs.docker.com/compose/overview/*](https://docs.docker.com/compose/overview/)

-   **Birden çok Compose dosyaları** <br/>
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

Kapsayıcı ve mikro hizmetler modeli sürekli kapsayıcıları başlıyor. Kapsayıcıları kullanarak normal şekilde kapsayıcı atılabilir olduğundan Uyuyan bir kapsayıcı yeniden başlatmaz. Düzenleyiciler (gibi Kubernetes ve Azure Service Fabric) yalnızca görüntüleri yeni bir örneğini oluşturun. Ne bu örnekleme işlemi daha hızlı olacak şekilde nasıl yapılandırıldığında, uygulama ön derleme tarafından en iyi duruma getirme gerektiğini anlamına gelir. Kapsayıcı başlatıldığında, çalıştırmaya hazır olmalıdır. Olmayan geri yükleme ve çalışma zamanında derleme kullandığınızdan `dotnet restore` ve `dotnet build` dotnet CLI komutları bu, .NET Core ve Docker birçok blog gönderileri gördüğünüz gibi.

.NET ekibi .NET Core ve ASP.NET Core kapsayıcı iyileştirilmiş bir çerçeve yapmak için önemli işleri yapmak. Yalnızca .NET Core küçük bellek Ayak izi ile basit bir çerçeve olan; Takım üç ana senaryo için en iyi duruma getirilmiş Docker görüntüleri odaklanan ve bunları Docker Hub kayıt defterinde yayımlanan <span class="underline">microsoft/dotnet</span>, sürüm 2.1 ile başlangıç:

1.  **Geliştirme**: öncelik yeteneği hızla olduğu interate ve hata ayıklama değişiklikleri ve boyutu ikincil.

2.  **Derleme**: öncelikli uygulama derlemek ve ikili dosyalar ve ikili dosyaları iyileştirmek için diğer bağımlılıklar içerir.

3.  **Üretim**: odağı hızlı dağıtma ve kapsayıcılar başlangıç olduğunda, böylece bu görüntüleri ikili dosyaları ve uygulamayı çalıştırmak için içerik nedded ile sınırlıdır.

Bunu başarmak için .NET ekibi üç temel çeşitlere sağlayan [microsoft/dotnet](https://hub.docker.com/r/microsoft/dotnet/) (en Docker hub'ı):

1.  **SDK'sı**: geliştirme ve derleme senaryolar için.
2.  **çalışma zamanı**: üretim senaryosu için ve
3.  **çalışma zamanı deps**: üretim bir senaryo için [kendi içindeki uygulamaları](https://docs.microsoft.com/dotnet/core/deploying/index#self-contained-deployments-scd).

Çalışma zamanı görüntüleri de aspnetcore otomatik ayarı sağlar\_URL'ler 80 numaralı bağlantı noktasını ve daha hızlı başlatma alınırken yardımcı olmak için derleme; öncesi ngend önbellek.

#### <a name="additional-resources"></a>Ek kaynaklar

-   **ASP.NET Core ile Docker görüntü oluşturma en iyi duruma getirilmiş** <br/>
    [*https://blogs.msdn.microsoft.com/stevelasker/2016/09/29/building-optimized-docker-images-with-asp-net-core/*](https://blogs.msdn.microsoft.com/stevelasker/2016/09/29/building-optimized-docker-images-with-asp-net-core/)

-   **.NET Core Uygulamaları için Docker Görüntülerinizi Derleme** <br/>
    [*https://docs.microsoft.com/en-us/dotnet/core/docker/building-net-docker-images*](https://docs.microsoft.com/en-us/dotnet/core/docker/building-net-docker-images)

>[!div class="step-by-step"]
[Önceki](data-driven-crud-microservice.md)
[İleri](database-server-container.md)
