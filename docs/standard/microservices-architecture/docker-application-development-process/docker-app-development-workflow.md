---
title: "Docker uygulamalar için geliştirme iş akışı"
description: "Kapsayıcılı .NET uygulamaları için .NET mikro mimarisi | Docker uygulamalar için geliştirme iş akışı"
keywords: Docker, Microservices, ASP.NET, Container
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/18/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 8537b1db27f512ec0bfc2f23589efe8199ca3287
ms.sourcegitcommit: c3957fdb990060559d73cca44ab3e2c7b4d049c0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2018
---
# <a name="development-workflow-for-docker-apps"></a>Docker uygulamalar için geliştirme iş akışı

Burada Geliştirici tercih edilen dillerini kullanarak uygulama kodları ve yerel olarak test her geliştiricinin makinenin, uygulama geliştirme yaşam döngüsü başlatır. Hangi dil, çerçeve ve platform geliştirici, bu iş akışı ile seçer olsun Geliştirici her zaman geliştirme ve Docker kapsayıcıları sınama, ancak yerel olarak böylece.

Her kapsayıcı (bir Docker görüntüsü örneğini) aşağıdaki bileşenleri içerir:

-   Bir işletim sistemi seçimi olduğu (örneğin, bir Linux dağıtımı, Windows Nano Server veya Windows Server Core).

-   (Uygulama ikili dosyaları, vb.) geliştirici tarafından eklenen dosyalar.

-   Yapılandırma bilgileri (ortam ayarlarını ve bağımlılıklarını).

## <a name="workflow-for-developing-docker-container-based-applications"></a>Docker kapsayıcısı tabanlı uygulamalar geliştirmek için iş akışı

Bu bölümde açıklanmıştır *iç döngü* Docker kapsayıcısı tabanlı uygulamalar için geliştirme iş akışı. İç döngü iş akışı, daha geniş DevOps iş akışını dikkate alarak değildir ve yalnızca geliştiricinin bilgisayarında geliştirme çalışmanın odaklanır anlamına gelir. İlk ortamını ayarlama adımlarını bu yalnızca bir kez gerçekleştirilir dahil değildir.

Uygulamanın kendi Hizmetleri artı ek kitaplıkları (bağımlılıklar) oluşur. Aşağıda, genellikle bir Docker uygulaması oluştururken, Şekil 5-1'de gösterildiği gibi temel adımlar verilmiştir.

![](./media/image1.png)

**Şekil 5-1.** Kapsayıcılı Docker uygulamaları geliştirmek için adım adım iş akışı

Bu kılavuzda bu sürecin tamamı ayrıntılı ve Visual Studio ortamda Odaklanıldığında her ana adım açıklanmıştır.

Bir düzenleyici/CLI geliştirme yaklaşım (örneğin, Visual Studio Code artı Docker CLI macOS üzerinde ya da Windows) kullanırken, her adım, Visual Studio kullanıyorsanız, daha ayrıntılı biçimde genellikle bilmeniz gerekir. CLI ortamında çalışma hakkında daha fazla ayrıntı için e-kitap başvuran [kapsayıcılı Docker uygulama yaşam döngüsü Microsoft Platforms ve araçları ile](http://aka.ms/dockerlifecycleebook/).

Visual Studio 2015 veya Visual Studio 2017 kullanırken, bu adımların çoğunu sizin yerinize üretkenliğinizi önemli ölçüde artıran işlenir. Visual Studio 2017 kullanarak ve birden çok kapsayıcı uygulamaları hedefleme durumlarda özellikle geçerlidir. Örneğin, yalnızca tek bir tıklatmayla Visual Studio Dockerfile ve docker-compose.yml dosyası uygulamanız için yapılandırma projelerinizi ekler. Visual Studio'da uygulamayı çalıştırdığınızda, Docker görüntüsünü oluşturur ve doğrudan Docker içinde birden çok kapsayıcı uygulama çalışır; bile aynı anda birden fazla kapsayıcı ayıklamanızı sağlar. Bu özellikleri kullanarak geliştirme hızını artırır.

Yalnızca Visual Studio bu adımları otomatik hale getirir ancak neler olduğunu bilmeniz gerekmez gelmez docker'la üzerinde underneath. Bu nedenle, aşağıdaki kılavuzunda biz her adım ayrıntılı olarak açıklanmaktadır.

![](./media/image2.png)

## <a name="step-1-start-coding-and-create-your-initial-application-or-service-baseline"></a>Adım 1. Kod yazmaya başlayın ve başlangıç uygulaması veya hizmeti taban çizgisi oluşturma

Docker uygulama geliştirme, Docker olmadan uygulama geliştirme şekilde benzer. Docker için geliştirirken, dağıtma ve uygulama veya yerel ortamınızdaki Docker kapsayıcıları içinde çalışan hizmetler sınama olduğundan farktır. Kapsayıcı, bir Linux kapsayıcı veya bir Windows kapsayıcı olabilir.

### <a name="set-up-your-local-environment-with-visual-studio"></a>Visual Studio ile yerel ortamınızı ayarlayın

Başlamak için olduğundan emin olun [Docker Community Edition (CE)](https://www.docker.com/community-edition) aşağıdaki yönergelerde yer açıklandığı gibi yüklü Windows için:

[Docker Windows CE ile çalışmaya başlama](https://docs.docker.com/docker-for-windows/)

Ayrıca, Visual Studio yüklü 2017 gerekir. Visual Studio 2017 Docker, desteği kapsayıcılarında hata ayıklama desteği gibi daha gelişmiş olduğundan bu için Docker eklentisi, Visual Studio Araçları ile Visual Studio 2015 üzerinden tercih edilir. Visual Studio 2017 seçtiyseniz, Docker araç içerir **.NET Core ve Docker** Şekil 5-2'de gösterildiği gibi yükleme sırasında iş yükü.

![](./media/image3.png)

**Şekil 5-2**. Seçme **.NET Core ve Docker** Visual Studio 2017 Kurulum sırasında iş yükü

Docker uygulamanızda etkinleştirme ve dağıtma ve Docker içinde test önce bile düz .NET (genellikle kapsayıcılar kullanma planlıyorsanız, .NET Core) uygulamanızda kodlama başlatabilirsiniz. Ancak, Docker üzerinde olabildiğince çabuk, çünkü gerçek ortamı olacaktır ve sorunları mümkün olan en kısa sürede keşfedilmesini çalışmaya başlamak önerilir. Visual Studio, bu nedenle, neredeyse saydam hissi, Docker ile çalışmak kolaylaştırır çünkü bu teşvik — birden çok kapsayıcı uygulamaları Visual Studio'da hata ayıklama sırasında en iyi örnek.

### <a name="additional-resources"></a>Ek kaynaklar

-   **Docker Windows CE ile çalışmaya başlama**
    [*https://docs.docker.com/docker-for-windows/*](https://docs.docker.com/docker-for-windows/)

-   **Visual Studio 2017**
    [*https://www.visualstudio.com/downloads/*](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs)

![](./media/image4.png)

## <a name="step-2-create-a-dockerfile-related-to-an-existing-net-base-image"></a>Adım 2. Varolan bir .NET temel görüntüsü için ilgili bir Dockerfile oluşturma

Oluşturmak istediğiniz her özel görüntü için bir Dockerfile gerekir; Visual Studio veya Docker CLI kullanarak el ile otomatik olarak dağıtmak isteyip dağıtılması için bir Dockerfile her kapsayıcı için de gerekir (docker çalıştırın ve docker-komutları oluşturma). Uygulamanızın tek bir özel hizmet içeriyorsa, tek bir Dockerfile gerekir. Uygulamanız birden çok hizmet (olduğu gibi bir mikro mimarisi) içeriyorsa, her hizmet için bir Dockerfile gerekir.

Dockerfile uygulama veya hizmet kök klasöründe yer alır. Docker ayarlama ve uygulama veya hizmet bir kapsayıcıda çalıştırmak nasıl anlatın komutları içerir. El ile bir Dockerfile kodda oluşturun ve yanı sıra, .NET bağımlılıkları projenize ekleyin.

Visual Studio ve Docker için kendi araçları ile bu görevi yalnızca birkaç kere fareyi tıklatarak gerektirir. Visual Studio 2017 içinde yeni bir proje oluşturduğunuzda, adında bir seçenek yoktur **etkinleştirmek kapsayıcı (Docker) desteği**Şekil 5-3'te gösterildiği gibi.

![](./media/image5.png)

**Şekil 5-3**. Visual Studio 2017 içinde yeni bir proje oluştururken, Docker desteğini etkinleştirme

Yeni veya var olan bir proje üzerinde Docker desteği, Visual Studio Proje dosyasında sağ tıklayıp seçeneğini seçerek etkinleştirebilirsiniz **Proje Ekle Docker Destek**Şekil 5-4'te gösterildiği gibi.

![](./media/image6.png)

**Şekil 5-4**. Varolan bir Visual Studio 2017 projesinde Docker desteğini etkinleştirme

Bu eylem (bir ASP.NET Web uygulaması veya Web API hizmeti gibi) bir proje üzerinde bir Dockerfile gerekli yapılandırma ile projeye ekler. Ayrıca, tüm çözüm için docker-compose.yml dosyası ekler. Aşağıdaki bölümlerde, bu dosyaların her giden bilgileri açıklar. Visual Studio sizin için bu iş yapmak, ancak bir Dockerfile unsurları anlamak kullanışlıdır.

### <a name="option-a-creating-a-project-using-an-existing-official-net-docker-image"></a>Seçenek A: var olan bir resmi .NET Docker görüntüsünü kullanarak bir proje oluşturma

Genellikle, kapsayıcısının üstünde resmi bir depodan alma temel görüntü için özel bir görüntü yapı [Docker hub'a](https://hub.docker.com/) kayıt defteri. Visual Studio'da Docker desteğini etkinleştirme ne olur perde arkasında tam olarak olmasıdır. Dockerfile var olan bir aspnetcore görüntüsünü kullanır.

Daha önce hangi Docker görüntüler ve seçtiğiniz işletim sistemi ve framework bağlı olarak kullanabilirsiniz depoları açıklanmıştır. ASP.NET Core (Linux veya Windows) kullanmak istiyorsanız, örneğin, kullanılacak microsoft görüntüdür / aspnetcore:2.0. Bu nedenle, kapsayıcı için kullanacağınız temel hangi Docker görüntüyü belirtmek yeterlidir. Microsoft'tan ekleyerek bunu / aspnetcore:2.0, Dockerfile için. Bu Visual Studio tarafından otomatik olarak gerçekleştirilir, ancak sürüm güncelleştirme olsaydı, bu değeri güncelleştirin.

Docker hub'a resmi bir .NET görüntü deposundan sürüm numarasıyla kullanarak (geliştirme, test ve üretim dahil) tüm makinelerde aynı dil özellikleri kullanılabilir olmasını sağlar.

Aşağıdaki örnek, bir ASP.NET Core kapsayıcı için bir örnek Dockerfile gösterir.

```
FROM microsoft/aspnetcore:2.0
  
ARG source
  
WORKDIR /app
  
EXPOSE 80
  
COPY ${source:-obj/Docker/publish} .
  
ENTRYPOINT ["dotnet", " MySingleContainerWebApp.dll "]
```

Bu durumda, kapsayıcı resmi ASP.NET Core Docker görüntü (Linux ve Windows için çok arch) 2.0 sürümünü temel alır. Ayar budur `FROM microsoft/aspnetcore:2.0`. (Bu temel görüntü hakkında daha fazla ayrıntı için bkz: [ASP.NET Core Docker görüntü](https://hub.docker.com/r/microsoft/aspnetcore/) sayfa ve [.NET Core Docker görüntü](https://hub.docker.com/r/microsoft/dotnet/) sayfası.) Dockerfile içinde de (Bu durumda, bağlantı noktası 80 ' SUNMAYA ayarıyla yapılandırıldığı gibi) çalışma zamanında kullanacağı TCP bağlantı noktasında dinlemek için Docker istemeniz gerekir.

Ek yapılandırma ayarlarını dil ve kullandığınız framework bağlı olarak Dockerfile belirtebilirsiniz. Örneğin, ENTRYPOINT satırıyla \["dotnet", "MySingleContainerWebApp.dll"\] .NET Core uygulamayı çalıştırmak için Docker söyler. Derleme ve çalıştırma .NET uygulaması için SDK ve .NET Core CLI (dotnet CLI) kullanıyorsanız bu ayar farklı olacaktır. ENTRYPOINT satır ve diğer ayarları uygulamanız için seçtiğiniz dil ve platforma bağlı olarak farklı olacaktır alt çizgidir.

### <a name="additional-resources"></a>Ek kaynaklar

-   **.NET Core uygulamaları için Docker görüntülerinizi oluşturmak**
    [*https://docs.microsoft.com/dotnet/core/docker/building-net-docker-images*](../../../core/docker/building-net-docker-images.md)

-   **Kendi görüntünüzü yapı**. Resmi Docker belgelerinde.
    [*https://docs.docker.com/engine/tutorials/dockerimages/*](https://docs.docker.com/engine/tutorials/dockerimages/)

### <a name="using-multi-arch-image-repositories"></a>Birden çok yay görüntü depoları kullanma

Tek bir depodaki Linux görüntüsü ve bir Windows görüntüsü gibi platform çeşitleri içerebilir. Bu özellik, (yani Linux ve Windows) birden çok platform kapsayacak şekilde bir tek depodaki satıcılarının Microsoft (temel görüntü oluşturucuları) gibi sağlar. Örneğin, [microsoft/dotnet](https://hub.docker.com/r/microsoft/aspnetcore/) Docker hub'a kayıt defterinde depo aynı depodaki adı kullanarak Linux ve Windows Nano Server desteği sağlar.

Açık bir platform desteği bir etiket belirtirseniz aşağıdaki durumlarda ister:

-   **microsoft/aspnetcore:2.0.0-jessie**

        .NET Core 2.0 runtime-only on Linux 

-   **microsoft/aspnetcore:2.0.0-nanoserver**

        .NET Core 2.0 runtime-only on Windows Nano Server

Ancak ve belirtirseniz, bu yeni mid-2017 itibaren bile aynı etiketi ile aynı görüntü adı, Linux veya Windows sürümü dağıttığınız Docker ana bilgisayar işletim sistemi bağlı olarak yeni çok yay görüntüleri (gibi çok arch destekleyen aspnetcore görüntü) kullanır , aşağıdaki örnekte gösterildiği gibi:

-   **microsoft/aspnetcore:2.0**

        Multi-arch: .NET Core 2.0 runtime-only on Linux or Windows Nano Server depending on the Docker host OS

Bir Windows ana bilgisayardan bir görüntü istek olduğunda bu şekilde, Windows değişken çeker ve aynı görüntü adı Linux ana bilgisayardan çekme Linux değişken çeker.

### <a name="option-b-creating-your-base-image-from-scratch"></a>Seçenek B: temel görüntünüzde sıfırdan oluşturma

Kendi Docker temel görüntü sıfırdan oluşturabilir. Bu senaryo ile Docker başlangıç birinin önerilmez, ancak temel görüntünüzün belirli BITS ayarlamak istiyorsanız, bunu yapabilirsiniz.

### <a name="additional-resources"></a>Ek kaynaklar

-   **Birden çok yay .NET Core görüntüleri**.
https://github.com/dotnet/announcements/issues/14 
-   **Temel görüntü oluşturma**. Resmi Docker belge.
    [*https://docs.docker.com/engine/userguide/eng-image/baseimages/*](https://docs.docker.com/engine/userguide/eng-image/baseimages/)

![](./media/image7.png)

## <a name="step-3-create-your-custom-docker-images-and-embed-your-application-or-service-in-them"></a>Adım 3. Özel Docker görüntülerinizi oluşturmak ve uygulama veya hizmet bunları katıştırma

Uygulamanızdaki her hizmet için ilgili bir görüntüsü oluşturmanız gerekir. Uygulamanızı bir tek hizmeti veya web uygulaması oluşuyorsa, tek bir görüntü yeterlidir.

Docker görüntüleri otomatik olarak sizin için Visual Studio'da oluşturulan unutmayın. Aşağıdaki adımlar yalnızca Düzenleyicisi/CLI iş akışı için gereken ve daha anlaşılır olması için ne altında olduğu hakkında açıklanmıştır.

Geliştirici olarak geliştirmek ve yerel olarak tamamlanmış bir itme kadar test yapmanız özellik veya kaynak denetimi sisteminize (örneğin, GitHub) değiştirin. Bu, Docker görüntülerini oluşturmak ve bir yerel Docker konağına (Windows veya Linux VM) kapsayıcıları dağıtın ve çalıştırın, test ve bu yerel kapsayıcıları karşı hata ayıklama gerektiği anlamına gelir.

Docker CLI ve, Dockerfile kullanarak yerel ortamınıza özel bir görüntü oluşturmak için docker yapı komutu, Şekil 5-5'olduğu gibi kullanabilirsiniz.

![](./media/image8.png)

**Şekil 5-5**. Özel bir Docker görüntü oluşturma

İsteğe bağlı olarak, doğrudan docker yapı proje klasöründen çalıştırmak, yerine, önce gerekli .NET kitaplıklarına dağıtılabilir bir klasör oluşturabilirsiniz ve dotnet çalıştırarak ikili dosyaları yayımlayın ve sonra docker yapı komutunu kullanın.

Bu bir Docker görüntüsü cesardl/netcore-webapı-mikro adı ile oluşturur-docker: ilk. Bu durumda: öncelikle, belirli bir sürümü temsil eden bir etiketi olan. Oluşturulan Docker uygulamanız için oluşturmanıza gerek her özel görüntü için bu adımı yineleyin.

Bir uygulama birden çok kapsayıcı yapılan zaman (diğer bir deyişle, bu çok kapsayıcı uygulama'dir), aynı zamanda docker---ilgili kullanıma sunulan meta verileri kullanarak tek bir komutla ilgili tüm görüntüleri oluşturmak için yapı komutu oluşturmanıza docker-compose.yml dosyaları.

Var olan görüntüleri yerel depoda docker kullanarak görüntüleri komutu, Şekil 5-6'da gösterildiği gibi bulabilirsiniz.

![](./media/image9.png)

**Şekil 5-6.** Docker görüntüleri komutunu kullanarak var olan görüntüleri görüntüleme

### <a name="creating-docker-images-with-visual-studio"></a>Visual Studio ile Docker görüntüleri oluşturma

Docker desteği olan bir proje oluşturmak için Visual Studio kullanırken, görüntüyü açıkça oluşturmayın. Bunun yerine, F5 tuşuna basın ve dockerized uygulaması veya hizmeti çalıştırdığınızda görüntü sizin için oluşturulur. Bu adım Visual Studio'da otomatik olarak yapılır ve bunu durum göremez ancak neler olduğunu bilmeniz önemlidir üzerinde underneath.

![](./media/image10.png)

## <a name="step-4-define-your-services-in-docker-composeyml-when-building-a-multi-container-docker-application"></a>4. adım. Birden çok kapsayıcı Docker uygulama oluştururken hizmetlerinizi docker-compose.yml tanımlayın

[Docker-compose.yml](https://docs.docker.com/compose/compose-file/) dosyası dağıtım komutları ile oluşturulmuş bir uygulama olarak dağıtılması için ilgili hizmetler kümesini tanımlamak imkan tanır.

Docker-compose.yml dosyası kullanmak için aşağıdaki örneğe benzer içerikle, ana dosyasında veya kök Çözüm klasörü oluşturmanız gerekir:

```yml
version: '3'
  
services:

  webmvc:
    image: eshop/web
    environment:
      - CatalogUrl=http://catalog.api
      - OrderingUrl=http://ordering.api
    ports:
      - "80:80"
    depends_on:
      - catalog.api
      - ordering.api

  catalog.api:
    image: eshop/catalog.api
    environment: 
      - ConnectionString=Server=sql.data;Database=CatalogDB;…
    ports:
      - "81:80"
    depends_on:
      - sql.data

  ordering.api:
    image: eshop/ordering.api
    environment:
      - ConnectionString=Server=sql.data;Database=OrderingDb;…
    ports:
      - "82:80"
    extra_hosts:
      - "CESARDLBOOKVHD:10.0.75.1"
    depends_on:
      - sql.data

  sql.data:
    image: mssql-server-linux:latest
    environment:
      - SA_PASSWORD=Pass@word
      - ACCEPT_EULA=Y
    ports:
      - "5433:1433"

```

Bu docker-compose.yml dosyası Basitleştirilmiş ve birleştirilmiş bir sürüm olduğunu unutmayın. Her zaman, bağlantı dizesi gibi dağıtım ortamı bağlı olabilir yapılandırma bilgilerini artı geçerli her kapsayıcı (gibi özel görüntü adı), statik yapılandırma verilerini içerir. Sonraki bölümlerde, birden çok docker-compose.yml yapılandırmaya nasıl bölebilirsiniz öğreneceksiniz dosyaları ve geçersiz kılma değerleri (hata ayıklama veya yayın) ortamını ve yürütme türüne bağlı olarak docker compose'u.

Docker-compose.yml dosyası örneği beş hizmetleri tanımlar: webmvc hizmeti (web uygulaması), iki mikro (catalog.api ve ordering.api) ve bir kapsayıcı olarak çalıştırılan Linux için SQL Server tabanlı bir veri kaynağı kapsayıcı, sql.data,. Docker görüntü her biri için gerekli olacak şekilde, her hizmetin bir kapsayıcı olarak dağıtılır.

Docker-compose.yml dosyası yalnızca hangi kapsayıcılar kullanılır, ancak bunlar ayrı ayrı nasıl yapılandırılacağını belirtir. Örneğin, webmvc kapsayıcı tanımına .yml dosyasında:

-   Önceden oluşturulmuş Elektronik Mağaza kullanan / web: son görüntü. Ancak, aynı zamanda bir parçası olarak oluşturulacak görüntü yapılandırabilirsiniz docker compose'u yürütme ek bir yapılandırma temel yapıyı: docker-compose dosyasındaki bölümü.

-   İki ortam değişkenlerini (katalog URL'si ve OrderingUrl) başlatır.

-   Kullanıma sunulan bağlantı noktası 80 kapsayıcısı konak makinedeki dış bağlantı noktası 80 üzerinde iletir.

-   Web uygulama kataloğu ve hizmetiyle sıralama bağlar bağlıdır\_ayarı. Bu, bu hizmetleri yeniden başlatılana kadar beklenecek hizmeti neden olur.

Biz mikro ve birden çok kapsayıcı uygulamaları uygulama konularını olduğunda sizi bir sonraki bölümde docker-compose.yml dosyası yeniden ziyaret.

### <a name="working-with-docker-composeyml-in-visual-studio-2017"></a>Visual Studio 2017 docker-compose.yml ile çalışma

Docker çözüm destek hizmeti proje bir Visual Studio çözümü ile Şekil 5-7'de gösterildiği gibi eklediğinizde, Visual Studio bir Dockerfile projenize ekler ve hizmet bölümü (Proje) docker-compose.yml dosyalarıyla çözümünüzde ekler. Birden çok kapsayıcı çözümünüzü oluşturmaya başlamak için kolay bir yoludur. Ardından, docker-compose.yml dosyaları açmak ve bunları ile ek özellikler güncelleştirin.

![](./media/image6.png)

**Şekil 5-7**. ASP.NET Core projesinde sağ tıklayarak Visual Studio 2017 Docker desteği ekleme

Visual Studio'da Docker desteği ekleme yalnızca Dockerfile projenize ekler, ancak yapılandırma bilgilerini çözüm düzeyinde ayarlanan birkaç genel docker-compose.yml dosyaları ekler.

Visual Studio çözümünüzde Docker destek ekledikten sonra Çözüm Gezgini'nde, Şekil 5-8'de gösterildiği gibi eklenen docker-compose.yml dosyaları içeren yeni bir düğüm (docker compose.dcproj proje dosyasında) de görürsünüz.

![](./media/image11.PNG)

**Şekil 5-8**. **Docker compose'u** Visual Studio 2017 Çözüm Gezgini'nde eklenen ağaç düğümü

Kullanarak tek docker-compose.yml dosyası ile birden çok kapsayıcı uygulama dağıtabilirsiniz docker compose'u komutu. Ortam (geliştirme üretim karşı) ve yürütme bağlı olarak değerleri kılabilir ancak, Visual Studio onları bir grup ekler türü (hata ayıklama ve yayın). Bu özellik, sonraki bölümlerde açıklandığı.

![](./media/image12.png)

## <a name="step-5-build-and-run-your-docker-application"></a>5. adım. Derleme ve Docker uygulamanızı çalıştırma

Uygulamanız yalnızca tek bir kapsayıcı varsa, Docker ana (VM veya fiziksel sunucu) dağıtarak çalıştırabilirsiniz. Uygulamanız birden çok hizmet içeriyorsa, ancak bunu oluşan bir uygulama olarak ya da tek bir CLI komutu kullanarak dağıtabilirsiniz (docker-compose yukarı) ya da Visual Studio ile bu komutu kapsar altında kullanacak. Farklı seçenekleri bakalım.

### <a name="option-a-running-a-single-container-with-docker-cli"></a>Seçenek A: tek kapsayıcı Docker CLI ile çalıştırma

Komutu, Şekil 5-9'olduğu gibi çalıştırın docker kullanarak bir Docker kapsayıcısı çalıştırabilirsiniz:

```
  docker run -t -d -p 80:5000 cesardl/netcore-webapi-microservice-docker:first
```

![](./media/image13.png)

**Şekil 5-9**. Komutu çalıştırın docker kullanarak bir Docker kapsayıcısı çalıştırma

Bu durumda, komut kapsayıcısının dahili bağlantı noktası 5000 konak makine 80 noktasına bağlar. Bu, ana bilgisayar bağlantı noktası 80 üzerinde dinleme ve kapsayıcısı üzerinde 5000 numaralı bağlantı noktasına ileten anlamına gelir.

### <a name="option-b-running-a-multi-container-application"></a>Seçenek B: birden çok kapsayıcı uygulama çalıştırma

Çoğu Kurumsal senaryoda, Docker uygulama birden fazla hizmet Şekil 5-10'da gösterildiği gibi bir çok kapsayıcı uygulamayı çalıştırmak gereken anlamı oluşacaktır.

![](./media/image14.png)

**Şekil 5-10**. Docker kapsayıcıları dağıtılan VM

#### <a name="running-a-multi-container-application-with-the-docker-cli"></a>Birden çok kapsayıcı uygulama Docker CLI ile çalıştırma

Docker CLI ile birden çok kapsayıcı uygulamayı çalıştırmak için docker çalıştırabilirsiniz-komutu oluşturun. Birden çok kapsayıcı uygulama dağıtmak için çözüm düzeyinde sahip olmanız bu komutu kullanan docker-compose.yml dosyası. Şekil 5-11 komutu docker-compose.yml dosyası içeren ana proje dizininden çalışırken sonuçları gösterir.

![](./media/image15.png)

**Şekil 5-11**. Örnek sonuçları çalıştırırken docker compose'u komutu

Docker sonra-komutu çalıştırır oluşturma, uygulama ve ilgili kapsayıcılarında VM gösteriminde Şekil 5-10'de gösterildiği gibi Docker ana bilgisayara dağıtılır.

#### <a name="running-and-debugging-a-multi-container-application-with-visual-studio"></a>Çalıştıran ve Visual Studio ile birden çok kapsayıcı uygulamasında hata ayıklama 

Visual Studio 2017 kullanarak bir çok kapsayıcı uygulaması çalıştıran daha basit alınamıyor. Yalnızca birden çok kapsayıcı uygulama çalıştırabilirsiniz değil, ancak normal kesme noktalarını ayarlama doğrudan Visual Studio'dan tüm kapsayıcılarında hata ayıklama mümkün.

Her bir çözüm içinde projeye Docker çözüm desteğini eklemeden önce belirtildiği gibi bu proje çalıştırmak veya tam çözüm aynı anda hata ayıklama imkan tanıyan genel (Çözüm düzeyi) docker-compose.yml dosyası içinde yapılandırılır. Visual Studio Docker çözümü desteği etkin olan her proje için bir kapsayıcı başlatmak ve tüm iç adımları gerçekleştirdiğiniz (dotnet yayımladığınızda, docker yapı, vs.).

Burada önemli olan nokta Şekil 5-12'de gösterildiği gibi Visual Studio 2017 içinde ek bir olmasıdır **Docker** F5 anahtar eylemi için komutu. Bu seçenek, çalıştırmak veya docker-compose.yml dosyalarında çözüm düzeyinde tanımlanan tüm kapsayıcıları çalıştırarak birden çok kapsayıcı uygulama hata ayıklama sağlar. Birden çok kapsayıcı çözümleri hata ayıklama özelliği anlamına gelir (kapsayıcı) farklı bir projedeki çeşitli kesme noktaları, her kesme noktası ayarlayabilirsiniz ve Visual Studio'da hata ayıklarken, farklı projelerde tanımlanan ve üzerinde çalışan kesme noktaları adresindeki durdurur farklı kapsayıcılar.

![](./media/image16.png)

**Şekil 5-12**. Visual Studio 2017 içinde çalışan birden çok kapsayıcı uygulamalar

### <a name="additional-resources"></a>Ek kaynaklar

-   **Bir ASP.NET kapsayıcısı uzak bir Docker konağına dağıtın**
    [*https://docs.microsoft.com/azure/vs-azure-tools-docker-hosting-web-apps-in-docker*](https://docs.microsoft.com/azure/vs-azure-tools-docker-hosting-web-apps-in-docker)

### <a name="a-note-about-testing-and-deploying-with-orchestrators"></a>Test etme ve orchestrators ile dağıtma hakkında bir Not

Docker-oluşturmanıza ve docker çalıştırma komutları (veya çalıştıran ve Visual Studio kapsayıcılarında hata ayıklama) kapsayıcıları geliştirme ortamında test etmek için yeterli. Ancak, bu yaklaşım, Docker kümeleri hedeflediğiniz ve Docker Swarm, Mesosphere DC/OS veya Kubernetes orchestrators gibi kullanmamanız gerekir. Gibi bir küme kullanıyorsanız [Docker Swarm modu](https://docs.docker.com/engine/swarm/) dağıtıp gibi ek komutlarla test gerekir (Docker Windows CE ve Mac sürümünden itibaren kullanılabilir sürüm 1.12), [docker hizmet oluşturma](https://docs.docker.com/engine/reference/commandline/service_create/) için tek Hizmetleri. Birkaç kapsayıcıları için oluşan bir uygulama dağıtıyorsanız, kullandığınız [docker compose'u paket](https://docs.docker.com/compose/reference/bundle/) ve [docker dağıtmak myBundleFile](https://docs.docker.com/engine/reference/commandline/deploy/) olarak oluşturulmuş uygulama dağıtmak için bir *yığın*. Daha fazla bilgi için blog gönderisine bakın [Tanıtımı Deneysel dağıtılmış uygulama paketleri](https://blog.docker.com/2016/06/docker-app-bundle/) Docker belgelerinde. Docker sitesinde.

İçin [DC/OS](https://mesosphere.com/blog/2015/09/02/dcos-cli-command-line-tool-datacenter/) ve [Kubernetes](http://kubernetes.io/docs/user-guide/deployments/) farklı dağıtım komutları ve komut dosyaları da kullanırsınız.

![](./media/image17.png)

## <a name="step-6-test-your-docker-application-using-your-local-docker-host"></a>6. adım. Yerel Docker ana bilgisayarınız kullanarak Docker uygulamanızı test etme

Bu adımı uygulamanız yapılması bağlı olarak değişir. Bir tek kapsayıcı ya da hizmet olarak dağıtılan basit bir .NET Core Web uygulama, hizmet Docker ana bilgisayardaki bir tarayıcı açıp Şekil 5-13'te gösterildiği gibi bu siteye gezinme erişebilir. (Konak post Dockerfile yapılandırmasında bir bağlantı noktası 80'dışındaki herhangi bir ana bilgisayarda kapsayıcı eşlendiği, URL'de içerir.)

![](./media/image18.png)

**Şekil 5-13**. Docker uygulamanızı localhost kullanarak yerel olarak test örneği

Localhost için Docker işaret etmiyor, IP ana bilgisayar (Bu varsayılan Docker CE kullanırken, gerekir), hizmetinize gezinmek için makinenizin ağ kartı IP adresini kullanın.

Bu URL tarayıcıda tartışılan belirli kapsayıcı örnek için 80 numaralı bağlantı noktasını kullandığını unutmayın. Nasıl bu komutu çalıştırmak docker ile bir önceki adımda açıklandığı gibi dağıtılmış olduğundan ancak, dahili olarak istekleri 5000 bağlantı noktasına yönlendirilirsiniz.

Ayrıca, Şekil 5-14'te gösterildiği gibi terminalde, curl kullanarak uygulamayı test edebilirsiniz. Windows Docker yüklemesinde Docker ana bilgisayar IP her zaman makinenizin gerçek IP adresinin yanı sıra 10.0.75.1 varsayılandır.

![](./media/image19.png)

**Şekil 5-14**. Curl kullanarak yerel olarak Docker uygulamanızı test örneği

### <a name="testing-and-debugging-containers-with-visual-studio-2017"></a>Test ve Visual Studio 2017 ile kapsayıcıları hata ayıklama

Kapsayıcıları çalışırken olduğu gibi çalıştıran ve Visual Studio 2017 kapsayıcılarla hata ayıklama, benzer şekilde .NET uygulama ayıklayabilirsiniz.

### <a name="testing-and-debugging-without-visual-studio"></a>Test ve hata ayıklama Visual Studio

Düzenleyici/CLI yaklaşımı kullanarak geliştiriyorsanız kapsayıcılarında hata ayıklama daha zordur ve izlemeleri oluşturarak hata ayıklama isteyeceksiniz.

### <a name="additional-resources"></a>Ek kaynaklar

-   **Yerel bir Docker kapsayıcısı uygulamalarında hata ayıklama**
    [*https://docs.microsoft.com/azure/vs-azure-tools-docker-edit-and-refresh*](https://docs.microsoft.com/azure/vs-azure-tools-docker-edit-and-refresh)

-   **Steve Lasker. Yapı, hata ayıklama, Docker ile ASP.NET Core uygulamaları dağıtma.** Video.
    [*https://channel9.msdn.com/Events/Visual-Studio/Visual-Studio-2017-Launch/T115*](https://channel9.msdn.com/Events/Visual-Studio/Visual-Studio-2017-Launch/T115)

## <a name="simplified-workflow-when-developing-containers-with-visual-studio"></a>Visual Studio ile kapsayıcıları geliştirirken Basitleştirilmiş iş akışı

Visual Studio kullanarak Düzenleyicisi/CLI yaklaşımı kullanırsanız, çok daha basit olduğunda etkili bir şekilde, iş akışı. Dockerfile Docker tarafından gerekli olan adımları çoğunu ilgili ve gizli ya da Visual Studio tarafından Şekil 5-15'te gösterildiği gibi Basitleştirilmiş docker-compose.yml dosyaları.

![](./media/image20.png)

**Şekil 5-15**. Visual Studio ile geliştirirken Basitleştirilmiş iş akışı

Ayrıca, adım 2 (Docker destek eklenmesi projelerinize) yalnızca bir kez gerçekleştirmek için gerekir. Bu nedenle, iş akışı .NET herhangi bir geliştirme için kullanılırken normal geliştirme görevlerinizi benzer. Kapak (görüntü oluşturma işlemi, hangi kullanmakta olduğunuz temel görüntüler, kapsayıcıları, vb. dağıtımını) altında ve bazen de davranışları özelleştirmek için Dockerfile veya docker-compose.yml dosyasını düzenlemeniz gerekir neler olduğunu bilmeniz gerekir. Ancak, işlerin çoğunu büyük ölçüde basitleştirilmiştir çok daha verimli hale Visual Studio kullanarak.

### <a name="additional-resources"></a>Ek kaynaklar

-   **Steve Lasker. Visual Studio 2017 ile .NET docker geliştirme**
    [*https://channel9.msdn.com/Events/Visual-Studio/Visual-Studio-2017-Launch/T111*](https://channel9.msdn.com/Events/Visual-Studio/Visual-Studio-2017-Launch/T111)

-   **Jeffrey T. Fritz. Visual Studio için bir kapsayıcı yeni Docker araçları ile .NET Core uygulaması koymak**
    [*https://blogs.msdn.microsoft.com/webdev/2016/11/16/new-docker-tools-for-visual-studio/*](https://blogs.msdn.microsoft.com/webdev/2016/11/16/new-docker-tools-for-visual-studio/)

## <a name="using-powershell-commands-in-a-dockerfile-to-set-up-windows-containers"></a>Windows kapsayıcıları ayarlamak için bir Dockerfile PowerShell komutlarını kullanma 

[Windows kapsayıcıları](https://msdn.microsoft.com/en-us/virtualization/windowscontainers/about/about_overview) var olan Windows uygulamalarınız Docker görüntülere dönüştürmek ve Docker ekosistemi geri kalanı ile aynı araçlarıyla dağıtmadan olanak sağlar. Windows kapsayıcılar kullanmak için aşağıdaki örnekte gösterildiği gibi Dockerfile, PowerShell komutlarını çalıştırın:

```
FROM microsoft/windowsservercore
  
LABEL Description="IIS" Vendor="Microsoft" Version="10"
  
RUN powershell -Command Add-WindowsFeature Web-Server
  
CMD [ "ping", "localhost", "-t" ]
```

Bu durumda, biz bir Windows Server Core temel görüntü (FROM ayarı) kullanarak ve PowerShell komutuyla (çalışma ayarı) IIS yükleniyor. Benzer şekilde, ASP.NET 4.x, .NET 4.6 veya herhangi bir Windows yazılımı gibi ek bileşenleri ayarlamak için PowerShell komutlarını kullanabilirsiniz. Örneğin, bir Dockerfile aşağıdaki komutta ASP.NET 4.5 ayarlar:

```
RUN powershell add-windowsfeature web-asp-net45
```

### <a name="additional-resources"></a>Ek kaynaklar

-   **aspnet-docker/Dockerfile.** Windows özellikleri içerecek şekilde dockerfiles çalıştırmak için Powershell komutlarını örnek.
    [*https://github.com/Microsoft/aspnet-docker/blob/master/4.6.2/Dockerfile*](https://github.com/Microsoft/aspnet-docker/blob/master/4.6.2/Dockerfile)

>[!div class="step-by-step"]
[Önceki] (index.md) [sonraki] (.. / net-core-single-containers-linux-windows-server-hosts/index.md)
