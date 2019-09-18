---
title: Docker uygulamaları için geliştirme iş akışı
description: Docker tabanlı uygulamalar geliştirmeye yönelik iş akışının ayrıntılarını anlayın. Adım adım ilerleyin ve Dockerfiles 'ı iyileştirmek ve Visual Studio 'Yu kullanırken kullanılabilecek Basitleştirilmiş iş akışıyla sona erdirmek için bazı ayrıntılara ulaşın.
ms.date: 01/07/2019
ms.openlocfilehash: 36caff247d031b8808ab953ec884b7ce292858eb
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71040298"
---
# <a name="development-workflow-for-docker-apps"></a>Docker uygulamaları için geliştirme iş akışı

Uygulama geliştirme yaşam döngüsü, bilgisayarınızda tercih ettiğiniz dili kullanarak kodlarınızla ve yerel olarak test ettiğiniz bir geliştirici olarak bilgisayarınızda başlatılır. Seçtiğiniz dil, çerçeve ve platforma bakılmaksızın, bu iş akışı ile Docker kapsayıcılarını her zaman geliştirip test edersiniz, ancak bunu yerel olarak yapmanız gerekir.

Her kapsayıcı (bir Docker görüntüsünün örneği) aşağıdaki bileşenleri içerir:

- Bir işletim sistemi seçimi, örneğin bir Linux dağıtımı, Windows nano sunucu veya Windows Server Core.

- Geliştirme sırasında eklenen dosyalar, örneğin, kaynak kodu ve uygulama ikilileri.

- Ortam ayarları ve bağımlılıklar gibi yapılandırma bilgileri.

## <a name="workflow-for-developing-docker-container-based-applications"></a>Docker kapsayıcı tabanlı uygulamalar geliştirmek için iş akışı

Bu bölüm, Docker kapsayıcı tabanlı uygulamalar için *iç döngü* geliştirme iş akışını açıklar. İç döngü iş akışı, daha geniş bir DevOps iş akışını düşünmediği anlamına gelir. Bu, üretim dağıtımına kadar dahil olabilir ve yalnızca geliştirici bilgisayarında yapılan geliştirme işlerine odaklanmaktadır. Bu adımlar yalnızca bir kez yapıldığından, ortamı ayarlamaya yönelik ilk adımlar dahil değildir.

Bir uygulama, kendi hizmetlerinizin yanı sıra ek kitaplıklarınızdan oluşur (bağımlılıklar). Şekil 5-1 ' de gösterildiği gibi, bir Docker uygulaması oluştururken genellikle gereken temel adımlar aşağıda verilmiştir.

![Docker uygulamaları için geliştirme süreci: 1-uygulamanızı kodlayın, 2-Dockerfile/s, 3-Dockerfile/s 'de tanımlanan görüntüleri oluşturun, 4-(isteğe bağlı) oluşturma hizmetleri Docker-Compose. yıml dosyasında, 5-çalıştırma kapsayıcısı veya Docker-Compose uygulaması, 6-uygulamanızı veya mikro hizmetleri, 7-depoyu depoya gönderin ve tekrarlayın. ](./media/image1.png)

**Şekil 5-1.** Docker Kapsayıcılı uygulamalar geliştirmek için adım adım iş akışı

Bu bölümde, bu tüm süreç ayrıntılıdır ve her ana adım bir Visual Studio ortamına odaklanarak açıklanmıştır.

Bir düzenleyici/CLı geliştirme yaklaşımı kullandığınızda (örneğin Visual Studio Code, macOS veya Windows üzerinde Docker CLı), Visual Studio 'Yu kullanmaktan daha ayrıntılı olarak, her adımı bilmeniz gerekir. CLı ortamında çalışma hakkında daha fazla bilgi için bkz. [Microsoft platformları ve araçları ile e-kitap Kapsayıcılı Docker uygulaması yaşam döngüsü](https://aka.ms/dockerlifecycleebook/).

Visual Studio 2017 kullanırken, bu adımların birçoğu sizin için işlenir ve bu da üretkenliğinizi önemli ölçüde geliştirir. Visual Studio 2017 kullanırken ve çok Kapsayıcılı uygulamaları hedeflerken bu durum özellikle doğrudur. Örneğin, yalnızca bir fare tıklaması ile, Visual Studio Dockerfile ve Docker-Compose. yıml dosyasını, uygulamanıza yönelik yapılandırmayla birlikte projenize ekler. Uygulamayı Visual Studio 'da çalıştırdığınızda, Docker görüntüsünü oluşturur ve çok Kapsayıcılı uygulamayı doğrudan Docker içinde çalıştırır; aynı zamanda birkaç kapsayıcıda hata ayıklamanıza da olanak tanır. Bu özellikler, geliştirme hızınızı artırır.

Ancak, yalnızca Visual Studio bu adımları otomatik hale getiren için Docker ile neler olduğunu bilmeniz gerekmez. Bu nedenle, aşağıdaki kılavuz her adımda ayrıntılardır.

![1-uygulamanızı kodlayın](./media/image2.png)

## <a name="step-1-start-coding-and-create-your-initial-application-or-service-baseline"></a>Adım 1. Kodlamaya başlayın ve başlangıç uygulamanızı veya hizmet temelinizi oluşturun

Docker uygulaması geliştirmek, Docker olmadan uygulama geliştirme yöntemine benzer. Bu fark, Docker için geliştirme yaparken, yerel ortamınızdaki Docker Kapsayıcıları içinde çalışan uygulamanızı veya hizmetlerinizi (Windows kapsayıcıları kullanılıyorsa Docker veya doğrudan Windows) bir Linux VM kurulumu) dağıtmakta ve test eteceğiz.

### <a name="set-up-your-local-environment-with-visual-studio"></a>Visual Studio ile yerel ortamınızı ayarlama

Başlamak için, aşağıdaki yönergelerde açıklandığı gibi Windows için [Docker Community Edition 'ın (CE)](https://docs.docker.com/docker-for-windows/) yüklü olduğundan emin olun:

[Docker CE for Windows kullanmaya başlayın](https://docs.docker.com/docker-for-windows/)

Ayrıca, Şekil 5-2 ' de gösterildiği gibi, **.NET Core platformlar arası geliştirme** iş yükü yüklüyken Visual Studio 2017 sürüm 15,7 veya üzeri bir sürüme ihtiyacınız vardır.

![Visual Studio yüklemesi sırasında .NET Core platformlar arası geliştirme iş yükü seçimi.](./media/image3.png)

**Şekil 5-2**. Visual Studio 2017 kurulumu sırasında **.NET Core platformlar arası geliştirme** iş yükünü seçme

Uygulamanızda Docker 'ı etkinleştirmeden ve Docker 'da dağıtıp test etmeden önce bile, uygulamanızı basit .NET (genellikle .NET Core 'da) kodlamaya başlayabilirsiniz. Ancak, gerçek ortam olacağı ve herhangi bir sorun mümkün olan en kısa sürede keşfedilebilir olduğundan, Docker üzerinde en kısa sürede çalışmaya başlamanız önerilir. Visual Studio, Visual Studio 'daki çok Kapsayıcılı uygulamalarda hata ayıklarken en iyi örnek olan Docker ile neredeyse oldukça kolay bir şekilde çalışmasını sağlayan bu, önerilir.

### <a name="additional-resources"></a>Ek kaynaklar

- **Docker CE for Windows kullanmaya başlayın** \
  <https://docs.docker.com/docker-for-windows/>

- **Visual Studio 2017** \
  [https://visualstudio.microsoft.com/downloads/](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017)

![2-Dockerfiles yazma](./media/image4.png)

## <a name="step-2-create-a-dockerfile-related-to-an-existing-net-base-image"></a>Adım 2. Mevcut bir .NET temel görüntüsüyle ilişkili bir Dockerfile oluşturma

Derlemek istediğiniz her özel görüntü için bir Dockerfile gerekir; Ayrıca, Visual Studio 'dan otomatik olarak veya Docker CLı (Docker Run ve Docker-Compose komutları) kullanarak el ile dağıtım yapıp etmeksizin her bir kapsayıcının dağıtılması için bir Dockerfile gerekir. Uygulamanız tek bir özel hizmet içeriyorsa, tek bir Dockerfile gerekir. Uygulamanız birden çok hizmet içeriyorsa (bir mikro hizmet mimarisinde olduğu gibi), her hizmet için bir Dockerfile gerekir.

Dockerfile, uygulamanızın veya hizmetinizin kök klasörüne yerleştirilir. Bu, Docker 'a uygulamanızı veya hizmetinizi bir kapsayıcıda ayarlamayı ve çalıştırmayı söyleyen komutları içerir. Kodda el ile Dockerfile oluşturabilir ve bunları .NET bağımlılıklarınızla birlikte projenize ekleyebilirsiniz.

Visual Studio ve Docker Araçları ile bu görev yalnızca birkaç fare tıklamasını gerektirir. Visual Studio 2017 ' de yeni bir proje oluşturduğunuzda, Şekil 5-3 ' de gösterildiği gibi, **kapsayıcı (Docker) desteğini etkinleştir**adlı bir seçenek vardır.

![Visual Studio 2017 'de yeni bir ASP.NET Core projesi oluştururken Docker desteği onay kutusunu Etkinleştir](./media/image5.png)

**Şekil 5-3**. Visual Studio 2017 'de yeni bir ASP.NET Core projesi oluştururken Docker desteğini etkinleştirme

Ayrıca, Şekil 5-4 ' de gösterildiği gibi, mevcut bir ASP.NET Core Web uygulaması projesinde, **Çözüm Gezgini** projeye sağ tıklayıp**Docker desteği** **Ekle** > ' yi seçerek Docker desteğini etkinleştirebilirsiniz.

![Visual Studio 'da Docker desteği Ekle menü seçeneği](./media/image6.png)

**Şekil 5-4**. Mevcut bir Visual Studio 2017 projesinde Docker desteğini etkinleştirme

Bu eylem, gerekli yapılandırmayla projeye bir *Dockerfile* ekler ve yalnızca ASP.NET Core projelerinde kullanılabilir.

Benzer bir şekilde, Visual Studio, **> kapsayıcı Orchestrator desteği**seçeneğine sahip tüm çözüme yönelik bir Docker-Compose. yıml dosyası da ekleyebilir. 4\. adımda bu seçeneği daha ayrıntılı bir şekilde araştıracağız.

### <a name="using-an-existing-official-net-docker-image"></a>Mevcut bir resmi .NET Docker görüntüsünü kullanma

Genellikle, [Docker Hub](https://hub.docker.com/) kayıt defteri gibi resmi bir depodan aldığınız temel görüntünün en üstünde Kapsayıcınız için özel bir görüntü oluşturursunuz. Visual Studio 'da Docker desteğini etkinleştirdiğinizde bu durum kesin olarak ne olur? Dockerfile, var olan `aspnetcore` bir görüntüyü kullanacaktır.

Daha önce seçtiğiniz çerçeveye ve işletim sistemine bağlı olarak, hangi Docker görüntülerini ve depolarınızı kullanacağınızı anlatılmıştır. Örneğin, ASP.NET Core (Linux veya Windows) kullanmak istiyorsanız kullanılacak `mcr.microsoft.com/dotnet/core/aspnet:2.2`görüntü. Bu nedenle, yalnızca Kapsayıcınız için kullanacağınız temel Docker görüntüsünü belirtmeniz yeterlidir. Bunu, dockerfile `FROM mcr.microsoft.com/dotnet/core/aspnet:2.2` dosyanıza ekleyerek yapabilirsiniz. Bu, Visual Studio tarafından otomatik olarak gerçekleştirilir, ancak sürümü güncelleştirirseniz, bu değeri güncelleştirmeniz gerekir.

Docker Hub 'dan sürüm numarası olan resmi bir .NET görüntü deposu kullanmak, tüm makinelerde (geliştirme, test ve üretim dahil) aynı dil özelliklerinin kullanılabilmesini sağlar.

Aşağıdaki örnekte, bir ASP.NET Core kapsayıcısı için örnek bir Dockerfile gösterilmektedir.

```Dockerfile
FROM mcr.microsoft.com/dotnet/core/aspnet:2.2
ARG source
WORKDIR /app
EXPOSE 80
COPY ${source:-obj/Docker/publish} .
ENTRYPOINT ["dotnet", " MySingleContainerWebApp.dll "]
```

Bu durumda, görüntü, resmi ASP.NET Core Docker görüntüsünün 2,2 sürümünü temel alır (Linux ve Windows için çoklu mimari). Bu ayar `FROM mcr.microsoft.com/dotnet/core/aspnet:2.2`budur. (Bu temel görüntü hakkında daha fazla bilgi için bkz. [.NET Core Docker Image](https://hub.docker.com/_/microsoft-dotnet-core/) sayfası.) Dockerfile 'da, çalışma zamanında kullanacağınız TCP bağlantı noktasını dinlemek için Docker 'a (Bu durumda, "kullanıma hazır ayarıyla yapılandırıldığı şekilde, bağlantı noktası 80) da sahip olmanız gerekir.

Kullanmakta olduğunuz dile ve çerçeveye bağlı olarak Dockerfile içinde ek yapılandırma ayarları belirtebilirsiniz. Örneğin, giriş noktası satırı `["dotnet", "MySingleContainerWebApp.dll"]` , Docker 'ın bir .NET Core uygulaması çalıştırmasını söyler. .NET uygulamasını derlemek ve çalıştırmak için SDK ve .NET Core CLI (DotNet CLı) kullanıyorsanız, bu ayar farklı olur. Alt çizgi, GIRIŞ noktası çizgisi ve diğer ayarların, uygulamanız için seçtiğiniz dile ve platforma bağlı olarak farklı olacaktır.

### <a name="additional-resources"></a>Ek kaynaklar

- **.NET Core uygulamaları için Docker görüntüleri oluşturma** \
  [https://docs.microsoft.com/dotnet/core/docker/building-net-docker-images](../../../core/docker/building-net-docker-images.md)

- **Kendi görüntünüzü oluşturun**. Resmi Docker belgelerinde. \
  <https://docs.docker.com/engine/tutorials/dockerimages/>

- **.NET kapsayıcı görüntüleriyle güncel kalarak** \
  <https://devblogs.microsoft.com/dotnet/staying-up-to-date-with-net-container-images/>

- **.NET ve Docker birlikte kullanma-DockerCon 2018 güncelleştirmesi** \
  <https://devblogs.microsoft.com/dotnet/using-net-and-docker-together-dockercon-2018-update/>

### <a name="using-multi-arch-image-repositories"></a>Multi-Arch Image depoları kullanma

Tek bir depo, Linux görüntüsü ve Windows görüntüsü gibi platform türevlerini içerebilir. Bu özellik, Microsoft (temel görüntü oluşturucuları) gibi satıcıların birden çok platformu (Linux ve Windows) kapsayan tek bir depoyu oluşturmalarına olanak tanır. Örneğin, Docker Hub kayıt defterinde bulunan [DotNet/Core](https://hub.docker.com/_/microsoft-dotnet-core/) deposu, aynı depo adını kullanarak Linux ve Windows nano sunucu desteği sağlar.

Bir etiketi belirtirseniz, aşağıdaki durumlarda açık olan bir platformu hedefliyorsanız:

- `microsoft/dotnet:2.2-aspnetcore-runtime-stretch-slim` \
  Hedefler: .NET Core 2,2 çalışma zamanı-yalnızca Linux üzerinde

- `microsoft/dotnet:2.2-aspnetcore-runtime-nanoserver-1809` \
  Hedefler: .NET Core 2,2 çalışma zamanı-yalnızca Windows nano Server üzerinde

Ancak, aynı etiketle birlikte aynı görüntü adını belirtirseniz, çok katmanlı görüntüler ( `aspnetcore` görüntü gibi), aşağıdaki örnekte gösterildiği gibi, dağıttığınız Docker ana bilgisayar işletim sistemine bağlı olarak Linux veya Windows sürümünü kullanır:

- `microsoft/dotnet:2.2-aspnetcore-runtime` \
  Multi-Arch: .NET Core 2,2 Runtime-yalnızca Docker Konağı işletim sistemine bağlı olarak Linux veya Windows nano Server

Bu şekilde, bir Windows ana bilgisayardan bir görüntü çektiğinizde Windows türevini çeker ve aynı görüntü adının bir Linux ana bilgisayardan çekilerek Linux varyantı alınır.

### <a name="multi-stage-builds-in-dockerfile"></a>Dockerfile 'da çok aşamalı derlemeler

Dockerfile, bir Batch betiğine benzer. Makineyi komut satırından kurmak zorunda kaldıysanız, yapabileceklerinize benzer.

Başlangıç bağlamını ayarlayan bir temel görüntüyle başlar, bu, ana bilgisayar işletim sisteminin üst kısmında yer alan başlangıç dosya sistemi gibidir. Bu bir işletim sistemi değildir, ancak kapsayıcının içindeki "The" OS gibi düşünün.

Her komut satırının yürütülmesi, bir önceki bir değişiklikten değişikliklerle dosya sisteminde yeni bir katman oluşturur; böylece, birleştirildiğinde, sonuçta elde edilen dosya sistemi oluşturulur.

Her yeni katman, önceki birinin üzerine "oturduğu" ve sonuçta elde edilen görüntü boyutu her komutla arttığı için, örneğin, bir uygulama oluşturmak ve yayımlamak için gerekli SDK 'yi içermesi gerekiyorsa görüntüler çok büyük alabilir.

Bu, çok aşamalı derlemelerin, Magic 'i yapmak için çizim içine (Docker 17,05 ve üzeri) sahip olduğu yerdir.

Temel fikir, bir aşamanın ilk görüntü olduğu ve ardından bir veya daha fazla komutun ardından son aşamanın son görüntü boyutunu belirlediği aşamalar halinde Dockerfile yürütme işlemini ayırabilmeniz için de kullanılır.

Kısaca, çok aşamalı derlemeler, oluşturma işleminin farklı "aşamalarda" bölünmesini sağlar ve ardından son görüntüyü ara aşamaların yalnızca ilgili dizinleri ele alarak birleştirir. Bu özelliği kullanmaya yönelik genel strateji şunlardır:

1. Uygulamayı oluşturmak ve bir klasöre yayımlamak için gereken her şeyi içeren bir temel SDK görüntüsünü (ne kadar büyük değildir) kullanın ve ardından

2. Küçük bir son görüntü oluşturmak için, yalnızca bir temel, küçük, çalışma zamanı görüntüsü kullanın ve önceki aşamada yayımlama klasörünü kopyalayın.

Çoklu aşamayı anlamanın en iyi yolu, bir Dockerfile 'ın ayrıntılı ve satıra göre ayrıntılıdır. böylece, bir projeye Docker desteği eklerken Visual Studio tarafından oluşturulan ilk Dockerfile ile başlayalım ve daha sonra bazı iyileştirmeler elde edilir.

İlk Dockerfile şuna benzer görünebilir:

```Dockerfile
 1  FROM mcr.microsoft.com/dotnet/core/aspnet:2.2 AS base
 2  WORKDIR /app
 3  EXPOSE 80
 4
 5  FROM mcr.microsoft.com/dotnet/core/sdk:2.2 AS build
 6  WORKDIR /src
 7  COPY src/Services/Catalog/Catalog.API/Catalog.API.csproj …
 8  COPY src/BuildingBlocks/HealthChecks/src/Microsoft.AspNetCore.HealthChecks …
 9  COPY src/BuildingBlocks/HealthChecks/src/Microsoft.Extensions.HealthChecks …
10  COPY src/BuildingBlocks/EventBus/IntegrationEventLogEF/ …
11  COPY src/BuildingBlocks/EventBus/EventBus/EventBus.csproj …
12  COPY src/BuildingBlocks/EventBus/EventBusRabbitMQ/EventBusRabbitMQ.csproj …
13  COPY src/BuildingBlocks/EventBus/EventBusServiceBus/EventBusServiceBus.csproj …
14  COPY src/BuildingBlocks/WebHostCustomization/WebHost.Customization …
15  COPY src/BuildingBlocks/HealthChecks/src/Microsoft.Extensions …
16  COPY src/BuildingBlocks/HealthChecks/src/Microsoft.Extensions …
17  RUN dotnet restore src/Services/Catalog/Catalog.API/Catalog.API.csproj
18  COPY . .
19  WORKDIR /src/src/Services/Catalog/Catalog.API
20  RUN dotnet build Catalog.API.csproj -c Release -o /app
21
22  FROM build AS publish
23  RUN dotnet publish Catalog.API.csproj -c Release -o /app
24
25  FROM base AS final
26  WORKDIR /app
27  COPY --from=publish /app .
28  ENTRYPOINT ["dotnet", "Catalog.API.dll"]
```

Ayrıntılar, satır satır:

- **Satır #1:** Yalnızca bir "küçük" çalışma zamanı temel görüntüsü ile bir aşama başlatın, başvuru için **temel** çağırın.

- **Satır #2:** Görüntüde **/App** dizinini oluşturun.

- **Satır #3:** **80**numaralı bağlantı noktasını kullanıma sunun.

- **Satır #5:** Oluşturma/yayımlama için "büyük" görüntüyle yeni bir aşama başlatın. Başvuru için **derlemeyi** çağırın.

- **Satır #6:** Görüntüde **/src** dizini oluşturun.

- **Satır #7:** 16. satıra kadar, paketleri daha sonra geri yükleyebilmeleri için başvurulan **. csproj** proje dosyalarını kopyalayın.

- **Satır #17:** **Catalog. API** projesi ve başvurulan projeler için paketleri geri yükleyin.

- **Satır #18:** **Çözüme yönelik tüm dizin ağacını** ( **. dockerıgnore** dosyasına dahil edilen dosyalar/dizinler hariç) görüntüdeki **/src** dizinine kopyalayın.

- **Satır #19:** Geçerli klasörü **Catalog. API** projesi olarak değiştirin.

- **Satır #20:** Projeyi (ve diğer proje bağımlılıklarını) ve görüntüdeki **/App** dizinine çıkışı oluşturun.

- **Satır #22:** Derlemeden devam eden yeni bir aşama başlatın. Başvuru için **Yayımla** ' yı çağırın.

- **Satır #23:** Projeyi (ve bağımlılıkları) ve çıktıyı görüntüdeki **/App** dizinine yayımlayın.

- **Satır #25:** **Temel** 'den devam eden yeni bir aşama başlatın ve **nihai**çağrı yapın.

- **Satır #26:** Geçerli dizini **/App**olarak değiştirin.

- **Satır #27:** **/App** dizinini aşama **Yayımla** ' dan geçerli dizine kopyalayın.

- **Satır #28:** Kapsayıcı başlatıldığında çalıştırılacak komutu tanımlayın.

Şimdi, eShopOnContainers söz konusu olduğunda tüm işlem performansını geliştirmek için bazı iyileştirmeleri keşfedelim, Linux kapsayıcılarında eksiksiz çözümü oluşturmak için 22 dakika veya daha uzun bir süre anlamına gelir.

Oldukça basit olan Docker 'ın katman önbelleği özelliğinden faydalanabilirsiniz: temel görüntü ve komutlar daha önce yürütülmüş gibi aynıysa, yalnızca komutları yürütmeye gerek kalmadan elde edilen katmanı kullanabilir ve bu nedenle bir süre tasarruf edebilir.

Bu nedenle, **oluşturma** aşamasına odaklanalım, satırlar 5-6, genellikle aynıdır, ancak her iki satır 7-17, eShopOnContainers 'dan her bir hizmet için farklıdır, ancak satırları 7-16, her zaman yürütülmesi gerekir, ancak satırları:

```Dockerfile
COPY . .
```

Böylece, her hizmet için yalnızca aynı olacak, tüm çözümü kopyalayacak ve daha büyük bir katman oluşturacak ancak:

1. Kopyalama işlemi yalnızca ilk kez yürütülür (bir dosya değiştirildiğinde ve yeniden oluşturulduğunda) ve diğer tüm hizmetler için önbelleği kullanacaksanız

2. Büyük görüntü bir ara aşamada gerçekleştiği için, son görüntü boyutunu etkilemez.

Sonraki önemli iyileştirme, her eshoponcontainers hizmeti için de farklı olan 17. satırda yürütülen `restore` komutu içerir. Bu satırı yalnızca öğesine değiştirirseniz:

```Dockerfile
RUN dotnet restore
```

Tüm çözüm için paketleri geri yükler, ancak yeniden geçerli stratejiyle 15 kez yerine yalnızca bir kez yapılır.

Ancak, `dotnet restore` yalnızca klasörde tek bir proje veya çözüm dosyası varsa çalışır, bu nedenle bu, çok fazla ayrıntıya ulaşmadan bu bir bit daha karmaşıktır ve bunu çözmek için bir yoldur:

1. Aşağıdaki satırları **. dockerıgnore**öğesine ekleyin:

   - `*.sln`, ana klasör ağacındaki tüm çözüm dosyalarını yoksaymak için

   - `!eShopOnContainers-ServicesAndWebApps.sln`, yalnızca bu çözüm dosyasını dahil etmek için.

2. Bağımsızdeğişkeninidedahilederek,Docker-Composeprojesinideyoksayarveyalnızcaeshoponcontainers-ServicesAndWebAppsçözümüiçinpaketlerigeriyükler.`/ignoreprojectextensions:.dcproj` `dotnet restore`

Son iyileştirme için, satır 23 ' ün aynı zamanda uygulama oluşturup 20 ' den sonra da bir zaman alan komutla birlikte geldiğinden emin olmak yeterlidir.

Elde edilen dosya bundan sonra:

```Dockerfile
 1  FROM mcr.microsoft.com/dotnet/core/aspnet:2.2 AS base
 2  WORKDIR /app
 3  EXPOSE 80
 4
 5  FROM mcr.microsoft.com/dotnet/core/sdk:2.2 AS publish
 6  WORKDIR /src
 7  COPY . .
 8  RUN dotnet restore /ignoreprojectextensions:.dcproj
 9  WORKDIR /src/src/Services/Catalog/Catalog.API
10  RUN dotnet publish Catalog.API.csproj -c Release -0 /app
11
12  FROM base AS final
13  WORKDIR /app
14  COPY --from=publish /app
15  ENTRYPOINT ["dotnet", "Catalog.API.dll"]
```

### <a name="creating-your-base-image-from-scratch"></a>Sıfırdan taban görüntünüzü oluşturma

Sıfırdan kendi Docker temel görüntünüzü oluşturabilirsiniz. Bu senaryo, Docker ile başlayan birisi için önerilmez, ancak kendi temel görüntününsün belirli bitleri ayarlamak istiyorsanız bunu yapabilirsiniz.

### <a name="additional-resources"></a>Ek kaynaklar

- **Çoklu mimari .NET Core görüntüleri**. \
  <https://github.com/dotnet/announcements/issues/14>

- **Temel görüntü oluşturun**. Resmi Docker belgeleri. \
  <https://docs.docker.com/develop/develop-images/baseimages/>

![3-Dockerfiles 'da tanımlanan görüntüleri oluşturma](./media/image7.png)

## <a name="step-3-create-your-custom-docker-images-and-embed-your-application-or-service-in-them"></a>Adım 3. Özel Docker görüntülerinizi oluşturun ve uygulamanızı veya hizmetinizi bunlara ekleyin

Uygulamanızdaki her hizmet için ilgili bir görüntü oluşturmanız gerekir. Uygulamanız tek bir hizmetten veya Web uygulamasından yapılırsa yalnızca tek bir görüntüye ihtiyacınız vardır.

Docker görüntülerinin Visual Studio 'da sizin için otomatik olarak oluşturulup oluşturulmadığını unutmayın. Aşağıdaki adımlar yalnızca Düzenleyici/CLı iş akışı için gereklidir ve altında neler olacağı hakkında netlik için açıklanır.

Bir geliştirici olarak, tamamlanmış bir özelliği veya kaynak denetim sisteminize (örneğin, GitHub) değişene kadar yerel olarak geliştirme ve test yapmanız gerekir. Bu, Docker görüntülerini oluşturmanız ve kapsayıcıları yerel bir Docker konağına (Windows veya Linux VM) dağıtmanız ve bu yerel kapsayıcılara karşı çalıştırmak, test etmeniz ve hata ayıklaması yapmanız gerektiği anlamına gelir.

Docker CLı ve Dockerfile kullanarak yerel ortamınızda özel bir görüntü oluşturmak için, Şekil 5-5 ' de olduğu gibi Docker Build komutunu kullanabilirsiniz.

![Docker görüntüsü oluşturmak için ilerleme ekranı](./media/image8.png)

**Şekil 5-5**. Özel bir Docker görüntüsü oluşturma

İsteğe bağlı olarak, proje klasöründen Docker derlemesini doğrudan çalıştırmak yerine, çalıştırmadan `dotnet publish`önce gerekli .NET kitaplıkları ve ikili dosyaları içeren dağıtılabilir bir klasör oluşturabilir ve sonra `docker build` komutunu kullanabilirsiniz.

Bu, adıyla `cesardl/netcore-webapi-microservice-docker:first`bir Docker görüntüsü oluşturur. Bu durumda, ilk olarak belirli bir sürümü temsil eden bir etikettir. Bu adımı, oluşturulan Docker uygulamanız için oluşturmanız gereken her özel görüntü için yineleyebilirsiniz.

Bir uygulama birden fazla kapsayıcıda yapıldığında (yani çok kapsayıcılı bir uygulamadır) ilgili Docker-Compose. yıml dosyalarında kullanıma sunulan meta verileri kullanarak tek `docker-compose up --build` bir komutla ilgili tüm görüntüleri oluşturmak için komutunu da kullanabilirsiniz. .

Şekil 5-6 ' de gösterildiği gibi Docker görüntüleri komutunu kullanarak yerel deponuzda mevcut görüntüleri bulabilirsiniz.

![Docker görüntüleri komutundan resim listesinin ekran görünümü](./media/image9.png)

**Şekil 5-6.** Docker görüntüleri komutunu kullanarak mevcut görüntüleri görüntüleme

### <a name="creating-docker-images-with-visual-studio"></a>Visual Studio ile Docker görüntüleri oluşturma

Docker desteğiyle bir proje oluşturmak için Visual Studio kullandığınızda, açıkça bir görüntü oluşturmazsınız. Bunun yerine, dockerte veya hizmeti çalıştırmak için **F5** tuşuna bastığınızda (veya **CTRL + F5**), görüntü sizin için oluşturulur. Bu adım, Visual Studio 'da otomatiktir ve bunun gerçekleşmediğini görmezsiniz, ancak nelerin altında olduğunu bilmeniz önemlidir.

![4-(isteğe bağlı) Docker-Compose. yıml dosyasındaki hizmetleri oluşturma](./media/image10.png)

## <a name="step-4-define-your-services-in-docker-composeyml-when-building-a-multi-container-docker-application"></a>4\. adımı. Çok kapsayıcılı bir Docker uygulaması oluştururken hizmetlerinizi Docker-Compose. yıml 'de tanımlama

[Docker-Compose. yıml](https://docs.docker.com/compose/compose-file/) dosyası, dağıtım komutlarıyla oluşturulmuş bir uygulama olarak dağıtılacak bir ilgili hizmet kümesi tanımlamanızı sağlar. Ayrıca, bağımlılık ilişkilerini ve çalışma zamanı yapılandırmasını yapılandırır.

Bir Docker-Compose. yml dosyası kullanmak için, dosyayı ana veya kök çözüm klasörünüzde aşağıdaki örnekteki gibi içerikle birlikte oluşturmanız gerekir:

```yml
version: '3.4'

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
      - ConnectionString=Server=sql.data;Port=1433;Database=CatalogDB;…
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

Bu Docker-Compose. yıml dosyası Basitleştirilmiş ve birleştirilmiş bir sürümdür. Her bir kapsayıcı için (özel görüntünün adı gibi) statik yapılandırma verilerini, her zaman gerekli olan ve bağlantı dizesi gibi dağıtım ortamına bağlı olabilecek yapılandırma bilgilerini içerir. Sonraki bölümlerde, Docker-Compose. yıml yapılandırmasını birden çok Docker-Compose dosyasına nasıl böleyeceğinizi ve ortam ve yürütme türüne (hata ayıklama veya sürüm) göre değerleri nasıl geçersiz kılacağınızı öğreneceksiniz.

Docker-Compose `webmvc` . yml dosyası örneği dört hizmeti tanımlar: hizmet (bir Web uygulaması), iki mikro hizmet (`ordering.api` ve `basket.api` `sql.data`) ve bir veri kaynağı kapsayıcısı, bir olarak çalışan Linux için SQL Server tabanlı kapsayıcı. Her hizmet bir kapsayıcı olarak dağıtılır, bu nedenle her biri için bir Docker görüntüsü gerekir.

Docker-Compose. yıml dosyası yalnızca hangi kapsayıcıların kullanıldığını, ancak bunların ayrı ayrı nasıl yapılandırıldığını belirtir. Örneğin, `webmvc` . yml dosyasındaki kapsayıcı tanımı:

- Önceden oluşturulmuş `eshop/web:latest` bir görüntü kullanır. Ancak, Docker-Compose dosyasındaki bir derlemeyi temel alan ek bir yapılandırma ile Docker-Compose yürütmesinin bir parçası olarak oluşturulacak görüntüyü de yapılandırabilirsiniz.

- İki ortam değişkenini başlatır (CatalogUrl ve OrderingUrl).

- Kapsayıcıda açığa çıkarılan 80 numaralı bağlantı noktasını ana makinedeki 80 dış bağlantı noktasına iletir.

- Web uygulamasını Katalog ve sıralama hizmetine depends_on ayarıyla bağlar. Bu, hizmetin bu hizmetler başlatılmadan beklemesini sağlar.

Mikro hizmetleri ve çok Kapsayıcılı uygulamaları nasıl uygulayacağınızı kapsadığımızda, Docker-Compose. yıml dosyasını sonraki bir bölümde geri ziyaret edeceğiz.

### <a name="working-with-docker-composeyml-in-visual-studio-2017"></a>Visual Studio 2017 ' de Docker-Compose. yıml ile çalışma

Daha önce bahsedildiği gibi, bir projeye Dockerfile eklemenin yanı sıra, Visual Studio 2017 (15,8 ' den itibaren) bir çözüme Docker Compose için Orchestrator desteği ekleyebilir.

Şekil 5-7 ' de gösterildiği gibi, kapsayıcı Orchestrator desteğini ilk kez eklediğinizde, Visual Studio proje için dockerfile 'ı oluşturur ve çeşitli Global `docker-compose*.yml` dosyalarla çözümünüzde yeni bir (hizmet bölümü) projesi oluşturur ve ardından şunu ekler Bu dosyalara proje. Daha sonra Docker-Compose. yıml dosyalarını açabilir ve bunları ek özelliklerle güncelleştirebilirsiniz.

Bu işlemi, Docker-Compose. yıml dosyasına eklemek istediğiniz her proje için tekrarlamanız gerekir.

Bu yazma sırasında, Visual Studio Docker Compose ve Service Fabric düzenleyiciler destekler.

![ASP.NET Core projesine Orchestrator desteği eklemek için bağlam menüsü seçeneği](./media/image21.png)

**Şekil 5-7**. ASP.NET Core projesine sağ tıklayarak Visual Studio 2017 ' de Docker desteği ekleme

Visual Studio 'daki çözümünüze Orchestrator desteği ekledikten sonra, Şekil 5-8 ' de gösterildiği gibi eklenen Docker-Compose. yıml dosyalarını içeren `docker-compose.dcproj` Çözüm Gezgini yeni bir düğüm (proje dosyasında) görürsünüz.

![Çözüm Gezgini Docker-oluşturma düğümü](./media/image11.png)

**Şekil 5-8**. Visual Studio 2017 Çözüm Gezgini eklenen **Docker-Compose** ağacı düğümü

`docker-compose up` Komutunu kullanarak tek bir Docker-Compose. yıml dosyası ile çok kapsayıcılı bir uygulama dağıtabilirsiniz. Ancak, Visual Studio bu grubun bir grubunu ekleyerek ortama (geliştirme veya üretim) ve yürütme türüne (yayın veya hata ayıklama) bağlı olarak değerleri geçersiz kılabilirsiniz. Bu özellik sonraki bölümlerde açıklanacaktır.

![5-kapsayıcıları veya oluşturulmuş uygulamayı çalıştırma](./media/image12.png)

## <a name="step-5-build-and-run-your-docker-application"></a>5\. adımı. Docker uygulamanızı derleyin ve çalıştırın

Uygulamanızın yalnızca tek bir kapsayıcısı varsa, bunu Docker konağına (VM veya fiziksel sunucu) dağıtarak çalıştırabilirsiniz. Bununla birlikte, uygulamanız birden çok hizmet içeriyorsa, tek bir CLı komutu (Docker-Compose) veya Visual Studio ile birlikte bulunan ve bu komutu kapakları altında kullanacak şekilde oluşturulan bir uygulama olarak dağıtabilirsiniz. Farklı seçeneklere göz atalım.

### <a name="option-a-running-a-single-container-application"></a>Seçenek A: Tek kapsayıcılı bir uygulama çalıştırma

#### <a name="using-docker-cli"></a>Docker CLı 'yi kullanma

Şekil 5-9 ' de gösterildiği gibi, `docker run` komutunu kullanarak bir Docker kapsayıcısı çalıştırabilirsiniz:

```console
  docker run -t -d -p 80:5000 cesardl/netcore-webapi-microservice-docker:first
```

Yukarıdaki komut, her çalıştırılışında belirtilen görüntüden yeni bir kapsayıcı örneği oluşturur. Kapsayıcıya bir ad vermek `--name` için parametresini kullanabilir ve `docker start {name}` sonra var olan bir kapsayıcı örneğini çalıştırmak için (ya da kapsayıcı kimliğini veya otomatik adı kullanabilirsiniz) kullanabilirsiniz.

![Docker Run komutunu kullanarak bir Docker kapsayıcısı çalıştırırken ekran görünümü](./media/image13.png)

**Şekil 5-9**. Docker Run komutunu kullanarak Docker kapsayıcısı çalıştırma

Bu durumda, komut kapsayıcının 5000 iç bağlantı noktasını ana makinenin 80 numaralı bağlantı noktasına bağlar. Bu, konağın 80 numaralı bağlantı noktasını dinlediği ve kapsayıcıda bağlantı noktası 5000 ' e ileten anlamına gelir.

Gösterilen karma kapsayıcı kimliğidir ve `--name` seçenek kullanılmazsa rastgele okunabilir bir ad atanır.

#### <a name="using-visual-studio"></a>Visual Studio 'Yu kullanma

Kapsayıcı Orchestrator desteği eklemediyseniz, Visual Studio 'da **CTRL-F5** tuşlarına basarak tek bir kapsayıcı uygulamasını da çalıştırabilirsiniz ve ayrıca **F5** 'i kullanarak kapsayıcıda uygulamada hata ayıklaması yapabilirsiniz. Kapsayıcı, Docker Run kullanarak yerel olarak çalışır.

### <a name="option-b-running-a-multi-container-application"></a>Seçenek B: Çok kapsayıcılı bir uygulama çalıştırma

Çoğu kurumsal senaryoda, bir Docker uygulaması birden çok hizmetten oluşur. Bu, Şekil 5-10 ' de gösterildiği gibi çok kapsayıcılı bir uygulama çalıştırmanız gerektiği anlamına gelir.

![Birkaç Docker kapsayıcı içeren VM](./media/image14.png)

**Şekil 5-10**. Docker Kapsayıcıları dağıtılan VM

#### <a name="using-docker-cli"></a>Docker CLı 'yi kullanma

Docker CLI ile çok kapsayıcılı bir uygulama çalıştırmak için `docker-compose up` komutunu kullanırsınız. Bu komut, çok kapsayıcılı bir uygulama dağıtmak için çözüm düzeyinde bulunan **Docker-Compose. yıml** dosyasını kullanır. Şekil 5-11, Docker-Compose. yıml dosyasını içeren ana çözüm dizininizden komut çalıştırırken sonuçları gösterir.

![Docker-Compose up komutu çalıştırılırken ekran görünümü](./media/image15.png)

**Şekil 5-11**. Docker-Compose up komutunu çalıştırırken örnek sonuçlar

Docker-Compose komutu çalıştıktan sonra, uygulama ve ilgili kapsayıcıları Şekil 5-10 ' de gösterildiği gibi Docker ana bilgisayarınıza dağıtılır.

#### <a name="using-visual-studio"></a>Visual Studio 'Yu kullanma

Visual Studio 2017 kullanarak çok kapsayıcılı bir uygulama çalıştırmak daha basit olamaz. Hata ayıklamak için **CTRL-F5** tuşlarına **basın veya her** zamanki gibi, **Docker-Compose** projesini başlangıç projesi olarak ayarlayın.  Visual Studio tüm gerekli kurulumu işler, bu nedenle her zamanki gibi kesme noktaları oluşturabilir ve son olarak "uzak sunucular" içinde çalışan bağımsız işlemlere (tıpkı bunun gibi) hata ayıklaması yapabilirsiniz.

Daha önce bahsedildiği gibi, bir çözüm içindeki bir projeye Docker çözüm desteği eklediğinizde, bu proje genel (çözüm düzeyi) Docker-Compose. yıml dosyasında yapılandırılmıştır ve bu, tüm çözümü tek seferde çalıştırmanıza veya hata ayıklamanıza olanak tanır. Visual Studio, Docker çözüm desteğinin etkinleştirildiği her proje için bir kapsayıcı başlatır ve tüm iç adımları (dotnet publish, Docker Build, vb.) gerçekleştirir.

Tüm drudgery göz atmak istiyorsanız, dosyaya göz atın:

`{root solution folder}\obj\Docker\docker-compose.vs.debug.g.yml`

Buradaki önemli nokta, Şekil 5-12 ' de gösterildiği gibi, Visual Studio 2017 ' de gösterildiği gibi, F5 tuşu eylemi için ek bir **Docker** komutu vardır. Bu seçenek, çözüm düzeyindeki Docker-Compose. yıml dosyalarında tanımlanan tüm kapsayıcıları çalıştırarak çok kapsayıcılı bir uygulamayı çalıştırmanızı veya hata ayıklamanıza olanak sağlar. Birden çok Kapsayıcılı çözüm için hata ayıklama özelliği, çeşitli kesme noktaları, farklı bir projede (kapsayıcı) ve Visual Studio 'dan hata ayıklama yaparken, farklı projelerde tanımlanan kesme noktalarında durulacağınız ve üzerinde çalışırken durdurulacak anlamına gelir. farklı kapsayıcılar.

![Docker-Compose projesi çalıştıran Visual Studio hata ayıklama araç çubuğu](./media/image16.png)

**Şekil 5-12**. Visual Studio 2017 'de çok Kapsayıcılı uygulamalar çalıştırma

### <a name="additional-resources"></a>Ek kaynaklar

- **ASP.NET kapsayıcısını uzak bir Docker konağına dağıtma** \
  <https://docs.microsoft.com/azure/vs-azure-tools-docker-hosting-web-apps-in-docker>

### <a name="a-note-about-testing-and-deploying-with-orchestrators"></a>Düzenleyiciler ile test ve dağıtma hakkında bir bilgi

Docker-Compose ve Docker çalıştırma komutları (ya da Visual Studio 'da kapsayıcıları çalıştırmak ve hata ayıklamak) geliştirme ortamınızda kapsayıcıları test etmek için yeterlidir. Ancak, [Kubernetes](https://kubernetes.io/) veya [Service Fabric](https://azure.microsoft.com/services/service-fabric/)gibi düzenleyicilerinin hedeflemesini yapmanız gereken üretim dağıtımları için bu yaklaşımı kullanmamalısınız. Kubernetes kullanıyorsanız, kapsayıcıları ve [Hizmetleri](https://kubernetes.io/docs/concepts/services-networking/service/) ağa göre düzenlemek için [Pod](https://kubernetes.io/docs/concepts/workloads/pods/pod/) 'yi kullanmanız gerekir. Ayrıca, Pod oluşturma ve değişiklik düzenlemek için [dağıtımları](https://kubernetes.io/docs/concepts/workloads/controllers/deployment/) da kullanabilirsiniz.

![6-uygulamanızı veya mikro hizmetlerinizi test edin](./media/image17.png)

## <a name="step-6-test-your-docker-application-using-your-local-docker-host"></a>6\. adım. Yerel Docker konağını kullanarak Docker uygulamanızı test etme

Bu adım, uygulamanızın yaptığı işe göre farklılık gösterir. Tek bir kapsayıcı veya hizmet olarak dağıtılan basit bir .NET Core Web uygulamasında, Şekil 5-13 ' de gösterildiği gibi, Docker ana bilgisayarında bir tarayıcı açarak ve bu siteye giderek hizmete erişebilirsiniz. (Dockerfile içindeki yapılandırma kapsayıcıyı 80 dışında bir şey olan konaktaki bir bağlantı noktasıyla eşleiyorsa, URL 'ye ana bilgisayar bağlantı noktasını ekleyin.)

![API uç noktası yanıtının tarayıcı görünümü](./media/image18.png)

**Şekil 5-13**. Docker uygulamanızı localhost kullanarak yerel olarak test etme örneği

Localhost, Docker ana bilgisayar IP 'sini işaret etmiyor (varsayılan olarak, Docker CE kullanırken), hizmetinize gitmek için makinenizin ağ kartının IP adresini kullanın.

Tarayıcıdaki bu URL 'nin incelenen belirli kapsayıcı örneği için 80 bağlantı noktasını kullandığını unutmayın. Ancak, dahili olarak istekler 5000 numaralı bağlantı noktasına yönlendirilmekte, çünkü bu, önceki adımda açıklandığı gibi Docker Run komutuyla dağıtılmıştı.

Ayrıca Şekil 5-14 ' de gösterildiği gibi, terminalden kıvrımlı kullanarak uygulamayı test edebilirsiniz. Windows 'daki bir Docker yüklemesinde, makinenizin gerçek IP adresine ek olarak varsayılan Docker ana bilgisayar IP 'si her zaman 10.0.75.1.

![Kıvrımlı bir API uç noktası yanıtının ekran görünümü](./media/image19.png)

**Şekil 5-14**. Docker uygulamanızı kıvrımlı kullanarak yerel olarak test etme örneği

### <a name="testing-and-debugging-containers-with-visual-studio-2017"></a>Visual Studio 2017 ile kapsayıcıları test etme ve hata ayıklama

Visual Studio 2017 ile kapsayıcıları çalıştırırken ve hata ayıklarken, kapsayıcılar olmadan çalıştırırken kullandığınız şekilde .NET uygulamasında hata ayıklaması yapabilirsiniz.

### <a name="testing-and-debugging-without-visual-studio"></a>Visual Studio olmadan test etme ve hata ayıklama

Düzenleyici/CLı yaklaşımını kullanarak geliştiriyorsanız, hata ayıklama kapsayıcıları daha zordur ve izleme oluşturarak hata ayıklama yapmak isteyeceksiniz.

### <a name="additional-resources"></a>Ek kaynaklar

- **Yerel bir Docker kapsayıcısında uygulamalarda hata ayıklama** \
  [https://docs.microsoft.com/visualstudio/containers/edit-and-refresh](/visualstudio/containers/edit-and-refresh)

- **Steve Lasker. Docker ile ASP.NET Core uygulamalar oluşturun, hata ayıklayın, dağıtın.** Video. \
  <https://channel9.msdn.com/Events/Visual-Studio/Visual-Studio-2017-Launch/T115>

## <a name="simplified-workflow-when-developing-containers-with-visual-studio"></a>Visual Studio ile kapsayıcılar geliştirirken Basitleştirilmiş iş akışı

Etkin olarak, Visual Studio 'Yu kullanırken iş akışı, düzenleyici/CLı yaklaşımını kullanmaktan daha basittir. Docker ve Docker-Compose. yıml dosyalarıyla ilgili Docker için gereken adımların çoğu Şekil 5-15 ' de gösterildiği gibi Visual Studio tarafından gizlenir veya basitleştirilmiştir.

![Visual Studio ile basitleştirilmiş kapsayıcı geliştirme iş akışı: 1-uygulamanızı kodlayın, 2-projelere Docker desteği ekleyin (tek bir kez), 3-çalıştırma kapsayıcısı veya Docker-Compose uygulaması, 4-uygulamanızı veya mikro hizmetlerinizi, 5-depoyu depoya gönderin ve tekrarlayın.](./media/image20.png)

**Şekil 5-15**. Visual Studio ile geliştirme yaparken Basitleştirilmiş iş akışı

Ayrıca, adım 2 ' yi (projelerinize Docker desteği ekleme) yalnızca bir kez gerçekleştirmeniz gerekir. Bu nedenle, iş akışı herhangi bir geliştirme için .NET kullanırken normal geliştirme görevlerinizde benzerdir. Kapakların (görüntü oluşturma işlemi, kullandığınız temel görüntüler, kapsayıcıların dağıtımı vb.) altında neler olduğunu bilmeniz gerekir ve bazı durumlarda, davranışları özelleştirmek için Dockerfile veya Docker-Compose. yıml dosyasını düzenlemeniz gerekir. Ancak işin çoğu Visual Studio kullanarak büyük ölçüde basitleştirilerek çok daha üretken hale getirirsiniz.

### <a name="additional-resources"></a>Ek kaynaklar

- **Steve Lasker. Visual Studio 2017 ile .NET Docker geliştirme** \
  <https://channel9.msdn.com/Events/Visual-Studio/Visual-Studio-2017-Launch/T111>

## <a name="using-powershell-commands-in-a-dockerfile-to-set-up-windows-containers"></a>Windows kapsayıcıları ayarlamak için bir Dockerfile içinde PowerShell komutlarını kullanma

[Windows kapsayıcıları](https://docs.microsoft.com/virtualization/windowscontainers/about/index) , mevcut Windows uygulamalarınızı Docker görüntülerine dönüştürmenize ve bunları Docker ekosisteminin geri kalanıyla aynı araçlarla dağıtmanıza imkan tanır. Windows kapsayıcılarını kullanmak için aşağıdaki örnekte gösterildiği gibi, Dockerfile içinde PowerShell komutlarını çalıştırın:

```Dockerfile
FROM microsoft/windowsservercore
LABEL Description="IIS" Vendor="Microsoft" Version="10"
RUN powershell -Command Add-WindowsFeature Web-Server
CMD [ "ping", "localhost", "-t" ]
```

Bu durumda, bir Windows Server çekirdek temel görüntüsü (başlangıç ayarı) kullanıyorsunuz ve IIS 'yi bir PowerShell komutuyla (çalıştırma ayarı) kullanıyoruz. Benzer bir şekilde, ASP.NET 4. x, .NET 4,6 veya başka herhangi bir Windows yazılımı gibi ek bileşenler ayarlamak için de PowerShell komutlarını kullanabilirsiniz. Örneğin, bir Dockerfile dosyasında aşağıdaki komut ASP.NET 4,5 ' u ayarlar:

```Dockerfile
RUN powershell add-windowsfeature web-asp-net45
```

### <a name="additional-resources"></a>Ek kaynaklar

- **aspnet-docker/Dockerfile.** Windows özelliklerini dahil etmek için dockerfile 'ları destekliyor 'tan çalıştırılacak örnek PowerShell komutları. \
  <https://github.com/Microsoft/aspnet-docker/blob/master/4.7.1-windowsservercore-ltsc2016/runtime/Dockerfile>

>[!div class="step-by-step"]
>[Önceki](index.md)İleri
>[](../multi-container-microservice-net-applications/index.md)
