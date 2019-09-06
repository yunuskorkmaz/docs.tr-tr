---
title: docker-compose.yml ile çok kapsayıcılı uygulamanızı tanımlama
description: Docker-Compose. yıml ile çok kapsayıcılı bir uygulama için mikro hizmet birleşimini belirtme.
ms.date: 10/02/2018
ms.openlocfilehash: 1b88d2267b12a33e125a7a1d2273654a50fd2d0f
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70296872"
---
# <a name="defining-your-multi-container-application-with-docker-composeyml"></a>docker-compose.yml ile çok kapsayıcılı uygulamanızı tanımlama

Bu kılavuzda, 4. adım bölümünde [ [Docker-Compose. yıml](https://docs.docker.com/compose/compose-file/) dosyası eklenmiştir. Çok kapsayıcılı bir Docker uygulaması](../docker-application-development-process/docker-app-development-workflow.md#step-4-define-your-services-in-docker-composeyml-when-building-a-multi-container-docker-application)oluştururken hizmetlerinizi Docker-Compose. yıml içinde tanımlayın. Ancak, daha ayrıntılı bir şekilde Araştırılması gereken Docker-Compose dosyalarını kullanmak için ek yollar vardır.

Örneğin, Docker-Compose. yıml dosyasında çok Kapsayıcılı uygulamanızı nasıl dağıtmak istediğinizi açıkça tanımlayabilirsiniz. İsteğe bağlı olarak, özel Docker görüntülerinizi nasıl oluşturacağınız de tanımlayabilirsiniz. (Özel Docker görüntüleri de Docker CLı ile oluşturulabilir.)

Temel olarak, dağıtmak istediğiniz kapsayıcıların her birini ve her bir kapsayıcı dağıtımı için belirli özellikleri tanımlarsınız. Çok kapsayıcılı bir dağıtım açıklama dosyanız olduktan sonra, tüm çözümü [Docker-Compose](https://docs.docker.com/compose/overview/) CLI komutuyla düzenlenmiş tek bir eylemde dağıtabilir veya Visual Studio 'dan saydam olarak dağıtabilirsiniz. Aksi takdirde, komut satırından `docker run` komutunu kullanarak kapsayıcıyı birden çok adımda dağıtmak için Docker CLI 'yi kullanmanız gerekir. Bu nedenle, Docker-Compose. yıml içinde tanımlanan her bir hizmetin tam olarak bir görüntü veya yapı belirtmesi gerekir. Diğer anahtarlar isteğe bağlıdır ve komut satırı karşılıklarına `docker run` benzer.

Aşağıdaki YAML kodu, eShopOnContainers örneği için olası genel ancak tek bir Docker-Compose. yıml dosyasının tanımıdır. Bu, eShopOnContainers 'dan gerçek Docker-Compose dosyası değildir. Bunun yerine, daha sonra açıklanacak şekilde Docker-Compose dosyaları ile çalışmanın en iyi yolu olmayan tek bir dosyadaki Basitleştirilmiş ve birleştirilmiş bir sürümdür.

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

Bu dosyadaki kök anahtar hizmetdir. Bu anahtar altında, `docker-compose up` komutunu çalıştırdığınızda veya bu Docker-Compose. yıml dosyasını kullanarak Visual Studio 'dan dağıtırken dağıtmak ve çalıştırmak istediğiniz hizmetleri tanımlarsınız. Bu durumda, aşağıdaki tabloda açıklandığı gibi, Docker-Compose. yıml dosyasında birden çok hizmet tanımlanmıştır.

| Hizmet adı | Açıklama |
|--------------|-------------|
| webmvc       | Sunucu tarafı C 'den mikro hizmetleri kullanan ASP.NET Core MVC uygulamasını içeren kapsayıcı\#|
| Catalog. API  | Katalog ASP.NET Core Web API mikro hizmeti de dahil olmak üzere kapsayıcı |
| sıralama. API | Web API mikro hizmeti ASP.NET Core sıralamasını içeren kapsayıcı |
| SQL. Data     | Mikro hizmet veritabanlarını tutan Linux için SQL Server çalıştıran kapsayıcı |
| sepet. API   | Sepet ASP.NET Core Web API mikro hizmeti olan kapsayıcı |
| sepet. Data  | Redsıs Cache hizmetini çalıştıran kapsayıcı, sepet veritabanı REDSıS Cache olarak |

### <a name="a-simple-web-service-api-container"></a>Basit bir Web hizmeti API kapsayıcısı

Tek bir kapsayıcıya odaklanarak Catalog. API Container-mikro hizmeti basit bir tanıma sahiptir:

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

Bu Kapsayıcılı hizmet aşağıdaki temel yapılandırmaya sahiptir:

- Özel eShop/Catalog. API görüntüsünü temel alır. Basitlik 'in sake için, dosyada derleme: anahtar ayarı yoktur. Bu, görüntünün daha önce oluşturulmuş olması (Docker derlemesi ile) veya herhangi bir Docker kayıt defterinden indirilen (docker pull komutuyla) olması gerektiği anlamına gelir.

- Katalog veri modelini içeren SQL Server örneğine erişmek üzere Entity Framework tarafından kullanılacak bağlantı dizesiyle ConnectionString adlı bir ortam değişkenini tanımlar. Bu durumda, aynı SQL Server kapsayıcısı birden çok veritabanını tutuyor. Bu nedenle, Docker için geliştirme makinenizde daha az bellek gerekir. Ancak, her mikro hizmet veritabanı için bir SQL Server kapsayıcısı da dağıtabilirsiniz.

- SQL Server adı, Linux için SQL Server örneğini çalıştıran kapsayıcı için kullanılan ad olan SQL. Data ' dır. Bu kullanışlıdır; Bu ad çözümlemesini kullanabilmeniz (Docker ana bilgisayarına iç) ağ adresini çözümleyecek ve bu sayede diğer kapsayıcılardan eriştiğiniz kapsayıcıların iç IP 'sini bilmeniz gerekmez.

Bağlantı dizesi bir ortam değişkeni tarafından tanımlandığından, bu değişkeni farklı bir mekanizmaya ve farklı bir zamanda ayarlayabilirsiniz. Örneğin, son Konaklarda üretime dağıtım yaparken veya Azure DevOps Services ya da tercih ettiğiniz DevOps sisteminizin CI/CD işlem hatlarından yararlanarak farklı bir bağlantı dizesi ayarlayabilirsiniz.

- Docker Konağı içindeki Catalog. API hizmetine iç erişim için 80 bağlantı noktasını kullanıma sunar. Konak, Linux için bir Docker görüntüsünü temel aldığı için şu anda bir Linux sanal makinesi. ancak kapsayıcıyı bir Windows görüntüsünde çalışacak şekilde yapılandırabilirsiniz.

- Kapsayıcı üzerinde 80 numaralı bağlantı noktasını Docker ana makinesi (Linux VM) üzerinde bağlantı noktası 5101 ' e iletir.

- Web hizmetini SQL. Data hizmetine bağlar (bir kapsayıcıda çalışan Linux veritabanı için SQL Server örneği). Bu bağımlılığı belirttiğinizde, SQL. Data kapsayıcısı zaten başlatılana kadar Catalog. API kapsayıcısı başlatılmaz; Bu önemlidir çünkü Catalog. API SQL Server veritabanının önce çalışır ve çalışıyor olması gerekir. Ancak, bu tür bir kapsayıcı bağımlılığı birçok durumda yeterli değildir çünkü Docker yalnızca kapsayıcı düzeyinde kontrol eder. Bazen hizmet (Bu durumda SQL Server) hala hazırlanmayabilir, bu nedenle, istemci mikro hizmetinizdeki üstel geri alma ile yeniden deneme mantığını uygulamanız önerilir. Bu şekilde, bir bağımlılık kapsayıcısı kısa bir süre için hazırsanız, uygulama yine de dayanıklı olacaktır.

- Bu, dış sunuculara erişime izin verecek şekilde yapılandırıldı: ek\_konaklar ayarı, dış sunuculara veya makinelere, yerel bir SQL gibi, Docker Konağı dışındaki (bir geliştirme Docker ana bilgisayarı olan varsayılan Linux VM 'nin dışında) erişmenize olanak tanır. Geliştirme BILGISAYARıNıZDA sunucu örneği.

Ayrıca, aşağıdaki bölümlerde tartışacak başka, daha gelişmiş Docker-Compose. yıml ayarları da vardır.

### <a name="using-docker-compose-files-to-target-multiple-environments"></a>Çoklu ortamları hedeflemek için Docker-Compose dosyalarını kullanma

Docker-Compose. yıml dosyaları tanım dosyalarıdır ve bu biçimi anlayan birden çok altyapı tarafından kullanılabilir. En kolay araç Docker-Compose komutındır.

Bu nedenle, Docker-Compose komutunu kullanarak aşağıdaki ana senaryoları hedefleyebilirsiniz.

#### <a name="development-environments"></a>Geliştirme ortamları

Uygulama geliştirirken, bir uygulamayı yalıtılmış bir geliştirme ortamında çalıştırabilmek önemlidir. Bu ortamı oluşturmak için Docker-Compose CLı komutunu veya kapabileşenler altında Docker-Compose kullanan Visual Studio 'Yu kullanabilirsiniz.

Docker-Compose. yıml dosyası, tüm uygulamanızın hizmet bağımlılıklarını (diğer hizmetler, önbellek, veritabanları, kuyruklar vb.) yapılandırmanıza ve belgeetmenize olanak tanır. Docker-Compose CLı komutunu kullanarak her bağımlılık için bir veya daha fazla kapsayıcıyı tek bir komutla oluşturup başlatabilirsiniz (Docker-Compose).

Docker-Compose. yıml dosyaları Docker altyapısı tarafından yorumlanan yapılandırma dosyalarıdır, ancak aynı zamanda çok Kapsayıcılı uygulamanızın kompozisyonu hakkında uygun belge dosyaları da sunar.

#### <a name="testing-environments"></a>Ortamları test etme

Herhangi bir sürekli dağıtım (CD) veya sürekli tümleştirme (CI) işleminin önemli bir bölümü, birim testleri ve tümleştirme sınamalardır. Bu otomatikleştirilmiş testler, kullanıcılardan etkilenmemesi için yalıtılmış bir ortam gerektirir ve uygulamanın verilerinde başka bir değişiklik olması gerekir.

Docker Compose, aşağıdaki komutlar gibi komut isteminizden veya betiklerinizde bulunan birkaç komut için yalıtılmış ortamı kolayca oluşturabilir ve yok edebilirsiniz:

```console
docker-compose -f docker-compose.yml -f docker-compose-test.override.yml up -d
./run_unit_tests
docker-compose -f docker-compose.yml -f docker-compose.test.override.yml down
```

#### <a name="production-deployments"></a>Üretim dağıtımları

Ayrıca, bir uzak Docker altyapısına dağıtmak için Oluştur ' da kullanabilirsiniz. Tipik bir durum, tek bir Docker ana bilgisayar örneğine (bir üretim VM 'si veya [Docker makinesi](https://docs.docker.com/machine/overview/)ile sağlanan sunucu gibi) dağıtılmaktır.

Başka bir Orchestrator (Azure Service Fabric, Kubernetes vb.) kullanıyorsanız, Docker-Compose. yml ' de olduğu gibi, diğer Orchestrator için gereken biçimde kurulum ve meta veri yapılandırma ayarları eklemeniz gerekebilir.

Her durumda, Docker-Compose geliştirme, test ve üretim iş akışları için uygun bir araç ve meta veri biçimidir, ancak üretim iş akışı kullandığınız Orchestrator üzerinde farklılık gösterebilir.

### <a name="using-multiple-docker-compose-files-to-handle-several-environments"></a>Çeşitli ortamları işlemek için birden çok Docker-Compose dosyası kullanma

Farklı ortamları hedeflerken, birden çok oluşturma dosyası kullanmanız gerekir. Bu, ortama bağlı olarak birden çok yapılandırma çeşitlemesi oluşturmanızı sağlar.

#### <a name="overriding-the-base-docker-compose-file"></a>Temel Docker-Compose dosyasını geçersiz kılma

Önceki bölümlerde gösterilen Basitleştirilmiş örneklerde olduğu gibi tek bir Docker-Compose. yıml dosyası kullanabilirsiniz. Ancak, çoğu uygulama için önerilmez.

Varsayılan olarak, Compose iki dosyayı okur, bir Docker-Compose. yıml ve isteğe bağlı bir Docker-Compose. override. yıml dosyası. Şekil 6-11 ' de gösterildiği gibi, Visual Studio 'yu kullanırken ve Docker desteğini etkinleştirirken, Visual Studio uygulamada hata ayıklamak için ek bir Docker-Compose. vs. Debug. g. i ml dosyası da oluşturur. bu dosyaya\\bir göz atabilirsiniz. \\ ana çözüm klasöründe.

![Docker-Compose proje dosyası yapısı:. dockerıgnore, dosyaları yoksaymak için; Docker-Compose. yıml, mikro hizmetler oluşturmak için; Mikro hizmetler ortamını yapılandırmak için Docker-Compose. override. yıml.](./media/image12.png)

**Şekil 6-11**. Visual Studio 'da Docker-dosyaları oluşturma 2017

Docker-Compose dosyalarını, Visual Studio Code veya alt lime gibi herhangi bir düzenleyici ile düzenleyebilir ve uygulamayı Docker-Compose up komutuyla çalıştırabilirsiniz.

Kural gereği, Docker-Compose. yıml dosyası temel yapılandırmanızı ve diğer statik ayarları içerir. Bu, hizmet yapılandırmasının hedeflediğiniz dağıtım ortamına bağlı olarak değişmeyeceği anlamına gelir.

Docker-Compose. override. yıml dosyası, adının önereceği gibi, temel yapılandırmayı geçersiz kılan yapılandırma ayarlarını (dağıtım ortamına bağlı yapılandırma gibi) içerir. Aynı zamanda farklı adlara sahip birden fazla geçersiz kılma dosyasına sahip olabilirsiniz. Geçersiz kılma dosyaları genellikle uygulama için gerekli olan, ancak bir ortama veya dağıtıma özgü ek bilgiler içerir.

#### <a name="targeting-multiple-environments"></a>Birden çok ortamı hedefleme

Tipik kullanım örneği, birden çok ortamı, hazırlama, CI veya geliştirme gibi birden çok ortamı hedefleyebilir. Bu farklılıkları desteklemek için, Şekil 6-12 ' de gösterildiği gibi, oluşturma yapılandırmanızı birden çok dosyaya bölebilirsiniz.

![Farklı ortamları işlemek için birden çok Docker-Compose*. FML dosyasını birleştirebilirsiniz.](./media/image13.png)

**Şekil 6-12**. Temel Docker-Compose. yıml dosyasındaki değerleri geçersiz kılan birden çok Docker-dosya oluşturma

Temel Docker-Compose. yıml dosyası ile başlayabilirsiniz. Bu temel dosya, ortama bağlı olarak değişmeyen temel veya statik yapılandırma ayarlarını içermelidir. Örneğin eShopOnContainers, temel dosya olarak aşağıdaki Docker-Compose. yıml dosyasına (daha az hizmetlerle Basitleştirilmiş) sahiptir.

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

Temel Docker-Compose. yıml dosyasındaki değerler farklı hedef dağıtım ortamları nedeniyle değişmemelidir.

Örneğin, webmvc hizmeti tanımına odaklandıysanız, bu bilgilerin ne kadar hedeflendiğine bakılmaksızın bu bilgilerin nasıl fazla olduğunu görebilirsiniz. Aşağıdaki bilgilere sahipsiniz:

- Hizmet adı: webmvc.

- Kapsayıcının özel görüntüsü: eshop/webmvc.

- Özel Docker görüntüsünü oluşturma komutu, hangi Dockerfile 'ın kullanılacağını gösterir.

- Diğer hizmetlerde bağımlılıklar, bu nedenle diğer bağımlılık kapsayıcıları başlatılana kadar bu kapsayıcı başlatılmaz.

Ek yapılandırmaya sahip olabilirsiniz ancak önemli nokta, temel Docker-Compose. yıml dosyasında yalnızca ortamlar genelinde ortak olan bilgileri ayarlamak istiyorsunuz. Ardından Docker-Compose. override. yıml veya üretim ya da hazırlama için benzer dosyalarda, her ortam için özel yapılandırmayı yerleştirmeniz gerekir.

Genellikle, eShopOnContainers 'dan aşağıdaki örnekte olduğu gibi, Docker-Compose. override. yml, geliştirme ortamınız için kullanılır:

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

Bu örnekte, geliştirme geçersiz kılma yapılandırması konağa bazı bağlantı noktaları gösterir, yönlendirme URL 'Leri ile ortam değişkenlerini tanımlar ve geliştirme ortamı için bağlantı dizelerini belirtir. Bu ayarlar yalnızca geliştirme ortamına yöneliktir.

Çalıştırdığınızda `docker-compose up` (veya Visual Studio 'dan başlattığınızda), komut geçersiz kılmaları her iki dosyayı birleştiriyor gibi otomatik olarak okur.

Üretim ortamı için farklı yapılandırma değerleriyle, bağlantı noktalarıyla veya bağlantı dizelerine sahip başka bir oluşturma dosyası istediğinizi varsayalım. Farklı ayarlar ve ortam değişkenleriyle adlı `docker-compose.prod.yml` dosya gibi başka bir geçersiz kılma dosyası oluşturabilirsiniz. Bu dosya farklı bir git deposunda depolanabilir veya yönetilen ve farklı bir ekip tarafından güvenli hale getirilmiş olabilir.

#### <a name="how-to-deploy-with-a-specific-override-file"></a>Belirli bir geçersiz kılma dosyası ile dağıtım

Birden çok geçersiz kılma dosyası ya da farklı bir ada sahip bir geçersiz kılma dosyası kullanmak için, Docker-Compose komutuyla-f seçeneğini kullanabilir ve dosyaları belirtebilirsiniz. Birleştirme dosyalarını komut satırında belirtildikleri sırada oluşturun. Aşağıdaki örnek, geçersiz kılma dosyalarıyla nasıl dağıtılacağını göstermektedir.

```console
docker-compose -f docker-compose.yml -f docker-compose.prod.yml up -d
```

#### <a name="using-environment-variables-in-docker-compose-files"></a>Docker-Compose dosyalarında ortam değişkenlerini kullanma

Önceki örneklerde gösterildiği gibi, özellikle üretim ortamlarında, ortam değişkenlerinden yapılandırma bilgilerini alabilmesi için kullanışlı bir yöntemdir. $ {My\_var} sözdizimini kullanarak Docker-Compose dosyalarınızda bir ortam değişkenine başvurabilirsiniz. Bir Docker-Compose. prod. yıml dosyasından aşağıdaki satır, bir ortam değişkeninin değerine nasıl başvurulacağını gösterir.

```yml
IdentityUrl=http://${ESHOP_PROD_EXTERNAL_DNS_NAME_OR_IP}:5105
```

Ortam değişkenleri, ana bilgisayar ortamınıza (Linux, Windows, bulut kümesi, vb.) bağlı olarak farklı yollarla oluşturulur ve başlatılır. Ancak, uygun bir yaklaşım. env dosyası kullanmaktır. Docker-Compose dosyaları,. env dosyasında varsayılan ortam değişkenlerini bildirmeyi destekler. Ortam değişkenlerine yönelik bu değerler varsayılan değerlerdir. Ancak, ortamınızda (konak işletim sistemi veya ortam değişkenleri kümenizdeki) tanımlamış olabileceğiniz değerler tarafından geçersiz kılınabilir. Bu. env dosyasını Docker-Compose komutunun yürütüldüğü klasöre yerleştirebilirsiniz.

Aşağıdaki örnek, eShopOnContainers uygulaması için [. env](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/.env) dosyası gibi bir. env dosyasını gösterir.

```env
# .env file

ESHOP_EXTERNAL_DNS_NAME_OR_IP=localhost

ESHOP_PROD_EXTERNAL_DNS_NAME_OR_IP=10.121.122.92
```

Docker-Compose, \<. env dosyasındaki her satırın biçim değişkeni\>=\<değerinde\>olmasını bekler.

Çalışma zamanı ortamında ayarlanan değerlerin her zaman. env dosyası içinde tanımlanan değerleri geçersiz kıldığını unutmayın. Benzer şekilde, komut satırı komut bağımsız değişkenleri ile geçirilen değerler aynı zamanda. env dosyasında ayarlanan varsayılan değerleri geçersiz kılar.

#### <a name="additional-resources"></a>Ek kaynaklar

- **Docker Compose genel bakış** \
    <https://docs.docker.com/compose/overview/>

- **Birden çok oluşturma dosyası** \
    [https://docs.docker.com/compose/extends/\#multiple-compose-files](https://docs.docker.com/compose/extends/#multiple-compose-files)

### <a name="building-optimized-aspnet-core-docker-images"></a>İyileştirilmiş ASP.NET Core Docker görüntüleri oluşturma

Internet 'teki kaynaklarda Docker ve .NET Core 'u araştırıyorsanız, kaynağınızı bir kapsayıcıya kopyalayarak bir Docker görüntüsü oluşturmanın basitliğini gösteren Dockerfiles 'ı bulabilirsiniz. Bu örnekler, basit bir yapılandırma kullanarak, uygulamanızla birlikte paketlenmiş bir Docker görüntüsüne sahip olabilirsiniz. Aşağıdaki örnekte, bu Vein içindeki basit bir Dockerfile gösterilmektedir.

```Dockerfile
FROM mcr.microsoft.com/dotnet/core/sdk:2.2
WORKDIR /app
ENV ASPNETCORE_URLS http://+:80
EXPOSE 80
COPY . .
RUN dotnet restore
ENTRYPOINT ["dotnet", "run"]
```

Bunun gibi bir Dockerfile çalışacaktır. Ancak, görüntülerinizi önemli ölçüde iyileştirebilirsiniz, özellikle de üretim görüntüleriniz.

Kapsayıcı ve mikro hizmetler modelinde, kapsayıcılardan sürekli olarak başlangıç yapabilirsiniz. Kapsayıcıları kullanmanın tipik yolu, kapsayıcı atılabilir olduğundan, uyuma bir kapsayıcıyı yeniden başlatmaz. Düzenleyiciler (Kubernetes ve Azure Service Fabric gibi) yalnızca yeni görüntü örnekleri oluşturur. Bunun anlamı, örnek oluşturma işleminin daha hızlı olması için uygulamayı derleme sırasında önceden derleyerek iyileştirmeniz gerektiği anlamına gelir. Kapsayıcı başlatıldığında, çalıştırılmaya hazırlanmalıdır. .NET Core ve Docker hakkında birçok blog gönderisine gördüğünüz `dotnet restore` gibi `dotnet build` , ve DotNet CLI içindeki komutları kullanarak çalışma zamanında geri yükleme ve derleme yapmanız gerekmez.

.NET ekibi, .NET Core ve kapsayıcı için iyileştirilmiş bir çerçeve ASP.NET Core için önemli bir iş yapıyor. .NET Core, küçük bellek ayak izine sahip hafif bir çerçeve; ekip, üç ana senaryo için iyileştirilmiş Docker görüntülerine odaklanmıştır ve 2,1 sürümünden itibaren *DotNet/Core*'Da Docker Hub kayıt defterinde yayımlanır:

1. **Geliştirme**: Burada öncelik, değişiklikleri hızlı bir şekilde yinelemek ve hata ayıklamanın yanı sıra boyutun ikincil olduğu yerdir.

2. **Oluşturma**: Öncelik, uygulamayı derliyor ve ikili dosyaları iyileştirmek için ikili dosyaları ve diğer bağımlılıkları içerir.

3. **Üretim**: Odağın, kapsayıcının hızlı bir şekilde dağıtılacağı ve başladığı yerde, bu görüntülerin ikili dosyalarla ve uygulamayı çalıştırmak için gereken içerikle sınırlı olması gerekir.

Bu işlemi gerçekleştirmek için, .NET ekibi [DotNet/Core](https://hub.docker.com/_/microsoft-dotnet-core/) 'da dört temel çeşit sağlar (Docker Hub 'da):

1. **SDK**: geliştirme ve derleme senaryoları için
1. **ASPNET**: ASP.NET üretim senaryoları için
1. **çalışma zamanı**: .NET üretim senaryoları için
1. **Runtime-Deps**: [kendi içindeki uygulamaların](../../../core/deploying/index.md#self-contained-deployments-scd)üretim senaryoları için.

Daha hızlı başlangıç için, çalışma zamanı görüntüleri Ayrıca aspnetcore\_URL 'lerini otomatik olarak 80 numaralı bağlantı noktasına ayarlar ve derlemelerin yerel görüntü önbelleğini oluşturmak için Ngen 'i kullanır.

#### <a name="additional-resources"></a>Ek kaynaklar

- **ASP.NET Core ile Iyileştirilmiş Docker görüntüleri oluşturma** \
    <https://blogs.msdn.microsoft.com/stevelasker/2016/09/29/building-optimized-docker-images-with-asp-net-core/>

- **.NET Core uygulamaları için Docker görüntüleri oluşturma** \
    [https://docs.microsoft.com/dotnet/core/docker/building-net-docker-images](../../../core/docker/building-net-docker-images.md)

> [!div class="step-by-step"]
> [Önceki](data-driven-crud-microservice.md)İleri
> [](database-server-container.md)
