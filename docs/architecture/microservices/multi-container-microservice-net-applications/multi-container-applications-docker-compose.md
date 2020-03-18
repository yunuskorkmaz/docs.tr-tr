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
# <a name="defining-your-multi-container-application-with-docker-composeyml"></a>docker-compose.yml ile çok kapsayıcılı uygulamanızı tanımlama

Bu kılavuzda [docker-compose.yml](https://docs.docker.com/compose/compose-file/) dosyası Adım 4 bölümünde [tanıtıldı. Çok konteynerli Docker uygulaması oluştururken servislerinizi docker-compose.yml olarak tanımlayın.](../docker-application-development-process/docker-app-development-workflow.md#step-4-define-your-services-in-docker-composeyml-when-building-a-multi-container-docker-application) Ancak, daha ayrıntılı olarak araştırılmaya değer docker-compose dosyaları kullanmak için ek yollar vardır.

Örneğin, docker-compose.yml dosyasında çok kapsayıcı uygulamanızı nasıl dağıtmak istediğinizi açıkça açıklayabilirsiniz. İsteğe bağlı olarak, özel Docker resimlerinizi nasıl oluşturacağınızaçıklayabilirsiniz. (Özel Docker görüntüleri de Docker CLI ile oluşturulabilir.)

Temel olarak, dağıtmak istediğiniz kapsayıcıların her birini ve her kapsayıcı dağıtımı için belirli özellikleri tanımlarsınız. Çok kapsayıcılı dağıtım açıklama dosyasına sahip olduktan sonra, tüm çözümü [docker-com to](https://docs.docker.com/compose/overview/) CLI komutu tarafından düzenlenmiş tek bir eylemde dağıtabilir veya Visual Studio'dan saydam olarak dağıtabilirsiniz. Aksi takdirde, komut satırından `docker run` komutu kullanarak konteyner-by-konteyner birden çok adımda dağıtmak için Docker CLI kullanmanız gerekir. Bu nedenle, docker-compose.yml'de tanımlanan her hizmet tam olarak bir görüntü veya yapı belirtmelidir. Diğer anahtarlar isteğe bağlıdır ve `docker run` komut satırı benzerlerine benzerdir.

Aşağıdaki YAML kodu eShopOnContainers örnek için olası bir küresel ama tek docker-compose.yml dosyasının tanımıdır. Bu eShopOnContainers gerçek docker-beste dosyası değildir. Bunun yerine, daha sonra açıklanacaktır docker-compose dosyaları ile çalışmak için en iyi yol değildir tek bir dosya, basitleştirilmiş ve konsolide sürümüdür.

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

Bu dosyadaki temel anahtar hizmetlerdir. Bu anahtarın altında, `docker-compose up` bu docker-compose.yml dosyasını kullanarak komutu çalıştırdığınızda veya Visual Studio'dan dağıtırken dağıtmak ve çalıştırmak istediğiniz hizmetleri tanımlarsınız. Bu durumda, docker-compose.yml dosyası, aşağıdaki tabloda açıklandığı gibi, tanımlanan birden çok hizmete sahiptir.

| Hizmet adı | Açıklama |
|--------------|-------------|
| webmvc       | Sunucu tarafındaki C'den mikro hizmetleri tüketen ASP.NET Core MVC uygulamasını içeren konteyner\#|
| katalog-api  | Katalog ASP.NET Core Web API microservice dahil Konteyner |
| sipariş-api | Sipariş ASP.NET Core Web API microservice dahil konteyner |
| sql data     | Linux için SQL Server çalıştıran, mikrohizmetler veritabanlarını tutan konteyner |
| sepet-api   | Core Web API microservice ASP.NET Sepetli Konteyner |
| sepet verileri  | REDIS önbellek hizmetini çalıştıran kapsayıcı, redis önbelleği olarak sepet veritabanı ile |

### <a name="a-simple-web-service-api-container"></a>Basit bir Web Hizmeti API kapsayıcısı

Tek bir kapsayıcı ya odaklanarak, katalog-api konteyner-microservice basit bir tanımı vardır:

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

Bu kapsayıcı hizmet aşağıdaki temel yapılandırmaya sahiptir:

- Bu özel **eshop / katalog-api** görüntü dayanmaktadır. Basitlik aşkına, hiçbir yapı: dosyada anahtar ayarı. Bu, görüntünün daha önce (docker build ile) oluşturulmuş veya herhangi bir Docker kayıt defterinden (docker çekme komutuyla) indirilmiş olması gerektiği anlamına gelir.

- Katalog veri modelini içeren SQL Server örneğine erişmek için Entity Framework tarafından kullanılacak bağlantı dizesiyle ConnectionString adlı bir ortam değişkeni tanımlar. Bu durumda, aynı SQL Server kapsayıcıbirden çok veritabanları tutuyor. Bu nedenle, Docker için geliştirme makinenizde daha az belleğe ihtiyacınız var. Ancak, her microservice veritabanı için bir SQL Server kapsayıcıdağıtabilirsiniz.

- SQL Server **adı,** Linux için SQL Server örneğini çalıştıran kapsayıcı için kullanılan adla aynı olan sqldata'dır. Bu uygundur; Bu ad çözünürlüğünü (Docker ana bilgisayarındahil) kullanabilmek, ağ adresini çözecek, böylece diğer kapsayıcılardan erişmekte olduğunuz kapsayıcıların dahili IP'sini bilmeniz gerekmez.

Bağlantı dizesi bir ortam değişkeni tarafından tanımlandığından, bu değişkeni farklı bir mekanizma aracılığıyla ve farklı bir zamanda ayarlayabilirsiniz. Örneğin, son ana bilgisayarlarda üretime dağıtılırken veya Azure DevOps Hizmetleri'ndeki CI/CD ardışık hatlarınızdan veya tercih ettiğiniz DevOps sisteminden bunu yaparak farklı bir bağlantı dizesi ayarlayabilirsiniz.

- Docker ana bilgisayar içindeki **katalog-api** hizmetine dahili erişim için bağlantı noktası 80'i ortaya çıkarır. Ana bilgisayar şu anda bir Linux VM'dir, çünkü Linux için bir Docker resmine dayanır, ancak bunun yerine kapsayıcıyı Windows görüntüsünde çalışacak şekilde yapılandırabilirsiniz.

- Konteynerüzerindeki 80 portu Docker ana makinedeki (Linux VM) 5101 portuna iletir.

- Web hizmetini **sqldata** hizmetine (bir kapsayıcıda çalışan Linux veritabanı için SQL Server örneği) bağlar. Bu bağımlılık belirttiğiniz zaman, katalog-api kapsayıcı sqldata kapsayıcısı zaten başlayana kadar başlamaz; katalog-api'nin önce SQL Server veritabanını çalışır hale alması gerektiğinden bu önemlidir. Ancak, Docker yalnızca kapsayıcı düzeyinde denetlediği için, bu tür kapsayıcı bağımlılığı birçok durumda yeterli değildir. Bazen hizmet (bu durumda SQL Server) hala hazır olmayabilir, bu nedenle istemci mikro hizmetlerinde üstel geri çekilme ile yeniden deneme mantığını uygulamak tavsiye edilir. Bu şekilde, bir bağımlılık kapsayıcısı kısa bir süre için hazır değilse, uygulama yine de esnek olacaktır.

- Harici sunuculara erişime izin verecek şekilde\_yapılandırılmıştır: Ekstra ana bilgisayar ayarı, geliştirme bilgisayarınızdaki yerel bir SQL Server örneği gibi, Docker ana bilgisayarının dışında harici sunuculara veya makinelere (diğer bir şekilde geliştirme Docker ana bilgisayarı olan varsayılan Linux VM dışında) erişmenizi sağlar.

Ayrıca, aşağıdaki bölümlerde `docker-compose.yml` tartışacağız diğer, daha gelişmiş ayarları vardır.

### <a name="using-docker-compose-files-to-target-multiple-environments"></a>Birden çok ortamı hedeflemek için docker oluşturma dosyalarını kullanma

Dosyalar `docker-compose.*.yml` tanım dosyalarıdır ve bu biçimi anlayan birden çok altyapı tarafından kullanılabilir. En basit araç docker-compose komutudur.

Bu nedenle, docker-compose komutunu kullanarak aşağıdaki ana senaryoları hedefleyebilirsiniz.

#### <a name="development-environments"></a>Geliştirme ortamları

Uygulamaları geliştirirken, bir uygulamayı yalıtılmış bir geliştirme ortamında çalıştırabilmek önemlidir. Bu ortamı oluşturmak için docker-create CLI komutunu veya kapakların altında docker-create kullanan Visual Studio'yu kullanabilirsiniz.

Docker-compose.yml dosyası, uygulamanızın tüm hizmet bağımlılıklarını (diğer hizmetler, önbellek, veritabanları, kuyruklar, vb.) yapılandırmanızı ve belgelemenizi sağlar. Docker-create CLI komutunu kullanarak, her bağımlılık için tek bir komutla (docker-create to up) bir veya daha fazla kapsayıcı oluşturabilir ve başlatabilirsiniz.

Docker-compose.yml dosyaları Docker motoru tarafından yorumlanan yapılandırma dosyaları dır, ancak aynı zamanda çoklu konteyner uygulamanızın bileşimi hakkında uygun dokümantasyon dosyaları olarak hizmet vermektedir.

#### <a name="testing-environments"></a>Test ortamları

Herhangi bir sürekli dağıtım (CD) veya sürekli tümleştirme (CI) işleminin önemli bir parçası birim testleri ve tümleştirme testleridir. Bu otomatik leştirilmiş testler, kullanıcılardan veya uygulamanın verilerindeki herhangi bir değişiklikten etkilenmemesi için yalıtılmış bir ortam gerektirir.

Docker Compose ile, aşağıdaki komutlar gibi komut istemi veya komut komutları birkaç komutları çok kolay bu yalıtılmış ortamı oluşturabilir ve yok:

```console
docker-compose -f docker-compose.yml -f docker-compose-test.override.yml up -d
./run_unit_tests
docker-compose -f docker-compose.yml -f docker-compose.test.override.yml down
```

#### <a name="production-deployments"></a>Üretim dağıtımları

Uzak bir Docker Engine dağıtmak için Oluştur'u da kullanabilirsiniz. Tipik bir durum tek bir Docker ana bilgisayar örneğine dağıtmaktır (üretim VM'si veya [Docker Machine](https://docs.docker.com/machine/overview/)ile birlikte verilen sunucu gibi).

Başka bir orchestrator kullanıyorsanız (Azure Hizmet Kumaşı, Kubernetes, vb.), docker-compose.yml'dekigibi kurulum ve meta veri yapılandırma ayarlarını, ancak diğer orkestratörün gerektirdiği biçimde eklemeniz gerekebilir.

Her durumda, docker-compose geliştirme, test ve üretim iş akışları için uygun bir araç ve meta veri biçimidir, ancak üretim iş akışı kullanmakta olduğunuz orkestratöre göre değişiklik gösterebilir.

### <a name="using-multiple-docker-compose-files-to-handle-several-environments"></a>Çeşitli ortamları işlemek için birden çok docker-beste dosyası kullanma

Farklı ortamları hedeflerken, birden çok oluşturma dosyası kullanmanız gerekir. Bu, ortama bağlı olarak birden çok yapılandırma varyantı oluşturmanıza olanak tanır.

#### <a name="overriding-the-base-docker-compose-file"></a>Temel docker oluşturma dosyasını geçersiz kılma

Önceki bölümlerde gösterilen basitleştirilmiş örneklerde olduğu gibi tek bir docker-compose.yml dosyası kullanabilirsiniz. Ancak, bu çoğu uygulama için önerilmez.

Varsayılan olarak, Compose iki dosya, bir docker-compose.yml ve isteğe bağlı docker-compose.override.yml dosyaokur. Şekil 6-11'de gösterildiği gibi, Visual Studio'yu kullanırken ve Docker desteğini etkinleştirirken, Visual Studio ayrıca uygulamanın hata ayıklanması için ek bir docker-compose.vs.debug.g.yml dosyası oluşturur, ana çözüm klasöründe obj\\Docker\\ klasöründe bu dosyaya göz atabilirsiniz.

![Bir docker oluşturmak proje dosyaların ekran görüntüsü.](./media/multi-container-applications-docker-compose/docker-compose-file-visual-studio.png)

**Şekil 6-11**. Visual Studio 2019'da docker-compose dosyaları

**docker-beste** proje dosya yapısı:

- *.dockerignore* - dosyaları yoksaymak için kullanılır
- *docker-compose.yml* - mikrohizmetler oluşturmak için kullanılan
- *docker-compose.override.yml* - mikro hizmetler ortamı yapılandırmak için kullanılan

Visual Studio Code veya Sublime gibi herhangi bir düzenleyiciyle docker-beste dosyalarını oluşturabilir ve uygulamayı docker-comto komutuyla çalıştırabilirsiniz.

Sözleşmeye göre docker-compose.yml dosyası temel yapılandırmanızı ve diğer statik ayarları içerir. Bu, hizmet yapılandırmasının hedeflediğiniz dağıtım ortamına bağlı olarak değişmemesi gerektiği anlamına gelir.

Docker-compose.override.yml dosyası, adından da anlaşılacağı gibi, dağıtım ortamına bağlı yapılandırma gibi temel yapılandırmayı geçersiz kılınan yapılandırma ayarlarını içerir. Farklı adlar içeren birden çok geçersiz kılma dosyanız da olabilir. Geçersiz kılma dosyaları genellikle uygulama tarafından gereken ancak bir ortama veya dağıtıma özgü ek bilgiler içerir.

#### <a name="targeting-multiple-environments"></a>Birden çok ortamı hedefleme

Tipik bir kullanım örneği, üretim, evreleme, CI veya geliştirme gibi birden çok ortamı hedefleyebilmeniz için birden çok oluşturma dosyası tanımladığınız zamandır. Bu farklılıkları desteklemek için, Şekil 6-12'de gösterildiği gibi, Oluşturma yapılandırmanızı birden çok dosyaya bölebilirsiniz.

![Temel dosyayı geçersiz kılmak için ayarlanmış üç docker-com-files diyagramı.](./media/multi-container-applications-docker-compose/multiple-docker-compose-files-override-base.png)

**Şekil 6-12**. Temel docker-compose.yml dosyasındaki değerleri geçersiz kılan birden çok docker-compose dosyaları

Farklı ortamları işlemek için birden çok docker-compose*.yml dosyasını birleştirebilirsiniz. Temel docker-compose.yml dosyası ile başlar. Bu temel dosya, ortama bağlı olarak değişmeden temel veya statik yapılandırma ayarlarını içermelidir. Örneğin, eShopOnContainers temel dosya olarak aşağıdaki docker-compose.yml dosyası (daha az hizmet ile basitleştirilmiş) vardır.

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

Temel docker-compose.yml dosyasındaki değerler, farklı hedef dağıtım ortamları nedeniyle değişmemelidir.

Örneğin, webmvc hizmet tanımına odaklanırsanız, hangi ortamı hedefliyor olursanız olun bu bilgilerin nasıl aynı olduğunu görebilirsiniz. Aşağıdaki bilgilere sahipsiniz:

- Hizmet adı: webmvc.

- Konteynerin özel görüntüsü: eshop/webmvc.

- Hangi Dockerfile'nin kullanılacağını belirten özel Docker görüntüsünü oluşturma komutu.

- Diğer hizmetlere bağımlılıklar, bu nedenle bu kapsayıcı diğer bağımlılık kapsayıcıları başlayana kadar başlamaz.

Ek yapılandırmanız olabilir, ancak önemli olan nokta, temel docker-compose.yml dosyasında yalnızca ortamlar arasında yaygın olan bilgileri ayarlamak istemenizdir. Daha sonra docker-compose.override.yml veya üretim veya evreleme için benzer dosyalarda, her ortam için özel yapılandırma yerleştirmelisiniz.

Genellikle, docker-compose.override.yml geliştirme ortamı için kullanılır, eShopOnContainers aşağıdaki örnekte olduğu gibi:

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

Bu örnekte, geliştirme geçersiz kılma yapılandırması bazı bağlantı noktalarını ana bilgisayara gösterir, yeniden yönlendirme URL'leri olan ortam değişkenlerini tanımlar ve geliştirme ortamı için bağlantı dizeleri belirtir. Bu ayarların tümü sadece geliştirme ortamı içindir.

Çalıştırdığınızda `docker-compose up` (veya Visual Studio'dan başlattığınızda), komut, geçersiz kılmaları her iki dosyayı da birleştiriyormuş gibi otomatik olarak okur.

Farklı yapılandırma değerleri, bağlantı noktaları veya bağlantı dizeleri ile üretim ortamı için başka bir Oluşturma dosyası istediğinizi varsayalım. Farklı ayarlar ve ortam değişkenleri `docker-compose.prod.yml` ile adlı dosya gibi başka bir geçersiz kılma dosyası oluşturabilirsiniz. Bu dosya farklı bir Git repo'sunda depolanabilir veya farklı bir ekip tarafından yönetilip güvenli hale alınabilir.

#### <a name="how-to-deploy-with-a-specific-override-file"></a>Belirli bir geçersiz kılma dosyasıyla nasıl dağıtılır?

Birden çok geçersiz kılma dosyasını veya farklı bir ada sahip bir geçersiz kılma dosyasını kullanmak için docker-comoluştur komutuyla -f seçeneğini kullanabilir ve dosyaları belirtebilirsiniz. Dosyaları komut satırında belirtilen sırayla birleştirin. Aşağıdaki örnek, dosyaları geçersiz kılmakla nasıl dağıtılanın gerektiğini gösterir.

```console
docker-compose -f docker-compose.yml -f docker-compose.prod.yml up -d
```

#### <a name="using-environment-variables-in-docker-compose-files"></a>Docker-compose dosyalarında ortam değişkenlerini kullanma

Özellikle üretim ortamlarında, önceki örneklerde de gösterdiğimiz gibi, çevre değişkenlerinden yapılandırma bilgileri alabilmek uygundur. ${MY\_VAR} sözdizimini kullanarak docker-compose dosyalarınızda bir ortam değişkenine başvuruyapabilirsiniz. Docker-compose.prod.yml dosyasından aşağıdaki satır, bir ortam değişkeninin değerine nasıl başvurulsüreceğini gösterir.

```yml
IdentityUrl=http://${ESHOP_PROD_EXTERNAL_DNS_NAME_OR_IP}:5105
```

Ortam değişkenleri, ana bilgisayar ortamınıza (Linux, Windows, Bulut kümesi, vb.) bağlı olarak farklı şekillerde oluşturulur ve başharflere alınır. Ancak, uygun bir yaklaşım bir .env dosyası kullanmaktır. Docker-compose dosyaları .env dosyasında varsayılan ortam değişkenlerini bildiren destekler. Ortam değişkenleri için bu değerler varsayılan değerlerdir. Ancak bunlar, ortamlarınızın her birinde tanımlamış olabileceğiniz değerler (kümenizden os veya ortam değişkenleri barındırma) tarafından geçersiz kılınabilir. Bu .env dosyasını docker-compose komutunun yürütüldüğü klasöre yersiniz.

Aşağıdaki örnekte eShopOnContainers uygulaması için .env dosyası gibi bir [.env](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/.env) dosyası gösterilmektedir.

```sh
# .env file

ESHOP_EXTERNAL_DNS_NAME_OR_IP=localhost

ESHOP_PROD_EXTERNAL_DNS_NAME_OR_IP=10.121.122.92
```

Docker-compose, .env dosyasındaki her satırın \<biçim\>=\<\>değişken değerinde olmasını bekler.

Çalışma zamanı ortamında ayarlanan değerler her zaman .env dosyasıiçinde tanımlanan değerleri geçersiz kılar. Benzer şekilde, komut satırı bağımsız değişkenleri aracılığıyla geçirilen değerler de .env dosyasında ayarlanan varsayılan değerleri geçersiz kılar.

#### <a name="additional-resources"></a>Ek kaynaklar

- **Docker Compose'a Genel Bakış** \
    <https://docs.docker.com/compose/overview/>

- **Birden Çok Dosya Oluştur** \
    [https://docs.docker.com/compose/extends/\#multiple-compose-files](https://docs.docker.com/compose/extends/#multiple-compose-files)

### <a name="building-optimized-aspnet-core-docker-images"></a>Core Docker görüntüleri ASP.NET optimize edilmiş bina

Docker ve .NET Core'u Internet'teki kaynaklarda keşfediyorsanız, kaynağınızı bir konteyneriçine kopyalayarak Docker görüntüsü oluşturmanın basitliğini gösteren Dockerfiles'ı bulacaksınız. Bu örnekler, basit bir yapılandırma kullanarak, uygulamanızla birlikte çevreyle birlikte bir Docker görüntüsüne sahip olabileceğinizi düşündürmektedir. Aşağıdaki örnek, bu ven basit bir Dockerfile gösterir.

```Dockerfile
FROM mcr.microsoft.com/dotnet/core/sdk:3.1
WORKDIR /app
ENV ASPNETCORE_URLS http://+:80
EXPOSE 80
COPY . .
RUN dotnet restore
ENTRYPOINT ["dotnet", "run"]
```

Böyle bir Dockerdosyası işe yarar. Ancak, resimlerinizi, özellikle de üretim resimlerinizi önemli ölçüde optimize edebilirsiniz.

Konteyner ve mikrohizmetler modelinde, sürekli konteyner başlatın. Kapsayıcı tek kullanımlık olduğundan, kapsayıcıları kullanmanın tipik yolu uyku kabını yeniden başlatmaz. Orkestratörler (Kubernetes ve Azure Hizmet Kumaşı gibi) yeni görüntü örnekleri oluşturur. Bunun anlamı, uygulama inşa edildiğinde önceden derleyerek en iyi duruma getirmeniz gerektiğidir, böylece anlık işlem daha hızlı olacaktır. Kapsayıcı başlatıldığında, çalışmaya hazır olmalıdır. .NET Core ve Docker hakkındaki birçok `dotnet restore` `dotnet build` blog gönderisinde gördüğünüz gibi, dotnet CLI'yi kullanarak ve komutları kullanarak çalışma zamanında geri yüklememeli ve derlememelisiniz.

.NET ekibi .NET Core ve ASP.NET Core'u konteyner için optimize edilmiş bir çerçeve haline getirmek için önemli çalışmalar yapıyor. Sadece .NET Core küçük bir bellek ayak izi ile hafif bir çerçeve; ekip üç ana senaryo için optimize edilmiş Docker görüntülerine odaklanmıştır ve bunları sürüm 2.1 ile başlayan *dotnet/core*adresindeki Docker Hub kayıt defterinde yayınlamıştır:

1. **Geliştirme**: Önceliğin değişiklikleri hızlı bir şekilde yineleme ve hata ayıklama yeteneği ve boyutun ikincil olduğu yerdir.

2. **Yapı**: Öncelik uygulamayı derlemektir ve ikilileri optimize etmek için ikili leri ve diğer bağımlılıkları içerir.

3. **Üretim**: Odak noktasının konteynerlerin hızlı bir şekilde dağıtılması ve başlatılması dır, bu nedenle bu görüntüler uygulamanın çalıştırılması için gereken ikili ve içerikle sınırlıdır.

Bunu başarmak için ,NET ekibi [dotnet/core'da](https://hub.docker.com/_/microsoft-dotnet-core/) (Docker Hub'da) dört temel türevi sağlar:

1. **sdk**: geliştirme ve inşa senaryoları için
1. **aspnet**: ASP.NET üretim senaryoları için
1. **runtime**: .NET üretim senaryoları için
1. **runtime-deps**: bağımsız uygulamaların üretim [senaryoları](../../../core/deploying/index.md#publish-self-contained)için.

Daha hızlı başlangıç için, çalışma zamanı görüntüleri\_aspnetcore url'lerini 80 bağlantı noktasına otomatik olarak ayarlar ve yerel bir anagörüntü önbelleği oluşturmak için Ngen'i kullanır.

#### <a name="additional-resources"></a>Ek kaynaklar

- **ASP.NET Core ile Optimize Edilmiş Docker Görüntüleri Oluşturma**  
  <https://docs.microsoft.com/archive/blogs/stevelasker/building-optimized-docker-images-with-asp-net-core>

- **.NET Core Uygulamaları için Docker Görüntülerinizi Derleme**  
  [https://docs.microsoft.com/dotnet/core/docker/building-net-docker-images](/aspnet/core/host-and-deploy/docker/building-net-docker-images)

> [!div class="step-by-step"]
> [Önceki](data-driven-crud-microservice.md)
> [Sonraki](database-server-container.md)
