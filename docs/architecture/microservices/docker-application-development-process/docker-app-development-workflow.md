---
title: Docker uygulamaları için geliştirme iş akışı
description: Docker tabanlı uygulamalar geliştirmek için iş akışının ayrıntılarını anlayın. Adım adım başlayın ve Dockerfiles'ı optimize etmek ve Visual Studio'yu kullanırken kullanılabilen basitleştirilmiş iş akışıyla bitirmek için bazı ayrıntılara girin.
ms.date: 01/30/2020
ms.openlocfilehash: c58ea2436027968143777a19286a1a0a72107717
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79401643"
---
# <a name="development-workflow-for-docker-apps"></a>Docker uygulamaları için geliştirme iş akışı

Uygulama geliştirme yaşam döngüsü, uygulamayı tercih ettiğiniz dili kullanarak kodlayıp yerel olarak test ettiğiniz bir geliştirici olarak bilgisayarınızda başlar. Bu iş akışıyla, hangi dili, çerçeveyi ve platformu seçerseniz seçin, Docker kapsayıcılarını her zaman geliştiriyor ve test ediyorsunuz, ancak bunu yerel olarak yapıyorsunuz.

Her kapsayıcı (Docker görüntüsünün bir örneği) aşağıdaki bileşenleri içerir:

- Bir işletim sistemi seçimi, örneğin, bir Linux dağıtımı, Windows Nano Server veya Windows Server Core.

- Geliştirme sırasında eklenen dosyalar, örneğin, kaynak kodu ve uygulama ikilileri.

- Ortam ayarları ve bağımlılıklar gibi yapılandırma bilgileri.

## <a name="workflow-for-developing-docker-container-based-applications"></a>Docker konteyner tabanlı uygulamalar geliştirmek için iş akışı

Bu bölümde Docker kapsayıcı tabanlı uygulamalar için *iç döngü* geliştirme iş akışı açıklanmaktadır. İç döngü iş akışı, üretim dağıtımına kadar dahil edilebilen ve yalnızca geliştiricinin bilgisayarında yapılan geliştirme çalışmalarına odaklanan daha geniş DevOps iş akışını dikkate almadığı anlamına gelir. Bu adımlar yalnızca bir kez yapıldığından, ortamı ayarlamak için ilk adımlar dahil değildir.

Bir uygulama kendi hizmetleri ve ek kitaplıklar (bağımlılıklar) oluşur. Aşağıda, Şekil 5-1'de gösterildiği gibi, docker uygulaması yaparken genellikle attığınız temel adımlar verebilirsiniz.

:::image type="complex" source="./media/docker-app-development-workflow/life-cycle-containerized-apps-docker-cli.png" alt-text="Kapsayıcı bir uygulama oluşturmak için gereken 7 adımı gösteren diyagram.":::
Docker uygulamaları için geliştirme süreci: 1 - Uygulamanızı kodlayın, 2 - Dockerfile/s yazın, 3 - Dockerfile/s'de tanımlanan görüntüleri oluşturun, 4 - (isteğe bağlı) Docker-compose.yml dosyasında hizmetleri oluşturun, 5 - Konteyner veya docker-create app, 6 - Uygulamanızı veya mikro hizmetleri test edin, 7 - Repo'yu tekrarlamak için bastırın ve tekrarlayın.
:::image-end:::

**Şekil 5-1.** Docker konteyner uygulamaları geliştirmek için adım adım iş akışı

Bu bölümde, tüm bu süreç ayrıntılı ve her büyük adım bir Visual Studio ortamı odaklanarak açıklanır.

Bir düzenleyici/CLI geliştirme yaklaşımı (örneğin, visual studio code artı Docker CLI macOS veya Windows'da) kullanırken, genellikle Visual Studio'yu kullandığınızdan daha ayrıntılı olarak her adımı bilmeniz gerekir. CLI ortamında çalışma hakkında daha fazla bilgi için, Microsoft Platformları ve Araçları ile e-kitap [Containerized Docker Uygulama yaşam döngüsüne](https://aka.ms/dockerlifecycleebook/)bakın.

Visual Studio 2019'u kullanırken, bu adımların çoğu sizin için işlenir ve bu da üretkenliğinizi önemli ölçüde artırır. Bu özellikle Visual Studio 2019'u kullanırken ve çoklu konteyner uygulamalarını hedefliyorsanız geçerlidir. Örneğin, tek bir fare tıklamasıyla Visual `Dockerfile` `docker-compose.yml` Studio, uygulamanızın yapılandırmasıyla projelerinizi ve dosyayı ve dosyayı ekler. Visual Studio'da uygulamayı çalıştırdığınızda, Docker görüntüsünü oluşturur ve çoklu konteyner uygulamasını doğrudan Docker'da çalıştırAr; hatta aynı anda birden fazla kapsayıcı hata ayıklama sağlar. Bu özellikler geliştirme hızınızı artırır.

Ancak Visual Studio'nun bu adımları otomatik hale getiriyor olması Docker'ın altında neler olup bittiğini bilmeniz edemek değildir. Bu nedenle, aşağıdaki kılavuz her adımı ayrıntıları.

![Adım 1 için görüntü.](./media/docker-app-development-workflow/step-1-code-your-app.png)

## <a name="step-1-start-coding-and-create-your-initial-application-or-service-baseline"></a>1. Adım. Kodlamaya başlayın ve ilk uygulama nızı veya hizmet temelinizi oluşturun

Docker uygulaması geliştirmek, Docker olmadan bir uygulama geliştirme şeklinize benzer. Aradaki fark, Docker için geliştirme sırasında, uygulamanızı veya hizmetlerinizi yerel ortamınızda Docker kapsayıcıları içinde (Docker tarafından linux VM kurulumu veya Windows Kapsayıcıları kullanıyorsanız doğrudan Windows tarafından bir Linux VM kurulumu) dağıtıyor ve test ediyor olmasıdır.

### <a name="set-up-your-local-environment-with-visual-studio"></a>Visual Studio ile yerel ortamınızı ayarlama

Başlamak için, aşağıdaki talimatlarda açıklandığı gibi Windows için [Docker Community Edition (CE)](https://docs.docker.com/docker-for-windows/) yüklü olduğundan emin olun:

[Windows için Docker CE ile başlayın](https://docs.docker.com/docker-for-windows/)

Buna ek olarak, Şekil 5-2'de gösterildiği gibi **.NET Core çapraz platform geliştirme** iş yükünün yüklü olduğu Visual Studio 2019 sürüm 16.4 veya daha sonrasına ihtiyacınız vardır.

![.NET Core çapraz platform geliştirme seçiminin ekran görüntüsü.](./media/docker-app-development-workflow/dotnet-core-cross-platform-development.png)

**Şekil 5-2**. Visual Studio 2019 kurulumu sırasında **.NET Core platform lar arası geliştirme** iş yükünü seçme

Docker'ı uygulamanızda etkinleştirmeden ve Docker'da dağıtmadan ve test etmeden önce uygulamanızı düz .NET'te (genellikle kapsayıcıkullanmayı planlıyorsanız .NET Core'da) kodlamaya başlayabilirsiniz. Ancak, docker üzerinde mümkün olan en kısa sürede çalışmaya başlamanız önerilir, çünkü bu gerçek ortam olacaktır ve herhangi bir sorun en kısa sürede keşfedilebilir. Visual Studio Docker ile çalışmayı o kadar kolaylaştırır ki, Visual Studio'dan çoklu konteyner uygulamalarını hata ayıklarken en iyi örnek neredeyse saydam dır.

### <a name="additional-resources"></a>Ek kaynaklar

- **Windows için Docker CE ile başlayın** \
  <https://docs.docker.com/docker-for-windows/>

- **Visual Studio 2019** \
  [https://visualstudio.microsoft.com/downloads/](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019)

![Adım 2 için görüntü.](./media/docker-app-development-workflow/step-2-write-dockerfile.png)

## <a name="step-2-create-a-dockerfile-related-to-an-existing-net-base-image"></a>2. Adım Varolan bir .NET taban görüntüsüyle ilgili dockerdosyası oluşturma

Oluşturmak istediğiniz her özel görüntü için bir Dockerfile gerekir; Ayrıca, Visual Studio'dan otomatik olarak veya Docker CLI'yi (docker run and docker-compose komutları) kullanarak otomatik olarak dağıtın, dağıtılacak her bir konteyner için bir Dockerfile'a da ihtiyacınız vardır. Uygulamanız tek bir özel hizmet içeriyorsa, tek bir Dockerfile gerekir. Uygulamanız birden çok hizmet içeriyorsa (mikro hizmetler mimarisinde olduğu gibi), her hizmet için bir Dockerfile gerekir.

Dockerfile, uygulamanızın veya hizmetinizin kök klasörüne yerleştirilir. Docker'a uygulamanızı veya hizmetinizi bir kapsayıcıda nasıl ayarlayıp çalıştıreceğini söyleyen komutları içerir. Kod halinde bir Dockerfile oluşturabilir ve .NET bağımlılıklarınizle birlikte projenize ekleyebilirsiniz.

Visual Studio ve Docker için araçları ile, bu görev sadece birkaç fare tıklaması gerektirir. Visual Studio 2019'da yeni bir proje oluşturduğunuzda, Şekil 5-3'te gösterildiği gibi **Docker Desteğini Etkinleştir**adlı bir seçenek vardır.

![Docker Destek onay kutusunu etkinleştir'i gösteren ekran görüntüsü.](./media/docker-app-development-workflow/enable-docker-support-check-box.png)

**Şekil 5-3**. Visual Studio 2019'da yeni bir ASP.NET Core projesi oluştururken Docker Desteğini etkinleştirme

Ayrıca, **Solution Explorer'daki** projeyi sağ tıklatarak ve Şekil 5-4'te gösterildiği gibi**Docker Desteği Ekle'yi** **Add** > seçerek mevcut bir ASP.NET Core web uygulaması projesinde Docker desteğini de etkinleştirebilirsiniz.

![Ekle menüsünde Docker Destek seçeneğini gösteren ekran görüntüsü.](./media/docker-app-development-workflow/add-docker-support-option.png)

**Şekil 5-4**. Mevcut bir Visual Studio 2019 projesinde Docker desteğini etkinleştirme

Bu eylem, projeye gerekli yapılandırmayla bir *Dockerfile* ekler ve yalnızca ASP.NET Core projelerinde kullanılabilir.

Benzer bir şekilde, Visual Studio `docker-compose.yml` da seçenek > Konteyner **Orchestrator Destek ekle**ile tüm çözüm için bir dosya ekleyebilirsiniz ... . Adım 4'te, bu seçeneği daha ayrıntılı olarak inceleyeceğiz.

### <a name="using-an-existing-official-net-docker-image"></a>Varolan bir resmi .NET Docker görüntüsünü kullanma

Genellikle [Docker Hub](https://hub.docker.com/) kayıt defteri gibi resmi bir depodan aldığınız temel görüntünün üzerine kapsayıcınız için özel bir resim oluşturursunuz. Visual Studio'da Docker desteğini etkinleştirdiğinizde örtünün altında tam olarak böyle olur. Dockerfile'ınız varolan `dotnet/core/aspnet` bir görüntü kullanır.

Daha önce seçtiğiniz çerçeve ye ve işletim sistemi ne bağlı olarak hangi Docker görüntüleri ve repos kullanabileceğinizi açıkladı. Örneğin, ASP.NET Core (Linux veya Windows) kullanmak istiyorsanız, `mcr.microsoft.com/dotnet/core/aspnet:3.1`kullanılacak görüntü . Bu nedenle, sadece konteyner için kullanacağınız temel Docker görüntü belirtmeniz gerekir. Bunu Dockerfile'ınıza ekleyerek `FROM mcr.microsoft.com/dotnet/core/aspnet:3.1` yaparsınız. Bu işlem Visual Studio tarafından otomatik olarak gerçekleştirilir, ancak sürümü güncellerseniz, bu değeri güncellersiniz.

Docker Hub'ın sürüm numarasıyla resmi bir .NET görüntü deposunun kullanılması, aynı dil özelliklerinin tüm makinelerde (geliştirme, test ve üretim dahil) kullanılabilmesini sağlar.

Aşağıdaki örnekte, ASP.NET Core kapsayıcısı için örnek bir Dockerfile gösterilmektedir.

```Dockerfile
FROM mcr.microsoft.com/dotnet/core/aspnet:3.1
ARG source
WORKDIR /app
EXPOSE 80
COPY ${source:-obj/Docker/publish} .
ENTRYPOINT ["dotnet", " MySingleContainerWebApp.dll "]
```

Bu durumda, görüntü resmi ASP.NET Core Docker görüntüsünün (Linux ve Windows için çoklu kemer) 3.1 sürümüne dayanmaktadır. Bu ayardır. `FROM mcr.microsoft.com/dotnet/core/aspnet:3.1` (Bu temel resim hakkında daha fazla bilgi için [.NET Core Docker Resim](https://hub.docker.com/_/microsoft-dotnet-core/) sayfasına bakın.) Dockerfile'da, Docker'a çalışma zamanında kullanacağınız TCP bağlantı noktasını dinlemesi için talimat vermeniz gerekir (bu durumda, port 80, EXPOSE ayarı ile yapılandırıldığı gibi).

Kullandığınız dile ve çerçeveye bağlı olarak Dockerfile'da ek yapılandırma ayarları belirtebilirsiniz. Örneğin, entrypoint satırı `["dotnet", "MySingleContainerWebApp.dll"]` Docker'a bir .NET Core uygulaması çalıştırmasını söyler. .NET uygulamasını oluşturmak ve çalıştırmak için SDK ve .NET Core CLI 'yi (dotnet CLI) kullanıyorsanız, bu ayar farklı olacaktır. Alt satırda ENTRYPOINT satırı ve diğer ayarları uygulamanız için seçtiğiniz dil ve platforma bağlı olarak farklı olacaktır.

### <a name="additional-resources"></a>Ek kaynaklar

- **.NET Çekirdek Uygulamaları için Docker Görüntüleri Oluşturma** \
  [https://docs.microsoft.com/dotnet/core/docker/building-net-docker-images](/aspnet/core/host-and-deploy/docker/building-net-docker-images)

- **Kendi resminizi oluşturun.** Resmi Docker belgelerinde.\
  <https://docs.docker.com/engine/tutorials/dockerimages/>

- **.NET Konteyner Görüntüleri ile güncel kalma** \
  <https://devblogs.microsoft.com/dotnet/staying-up-to-date-with-net-container-images/>

- **.NET ve Docker'ı Birlikte Kullanma - DockerCon 2018 Güncellemesi** \
  <https://devblogs.microsoft.com/dotnet/using-net-and-docker-together-dockercon-2018-update/>

### <a name="using-multi-arch-image-repositories"></a>Çok kemerli görüntü depolarını kullanma

Tek bir repo, Linux görüntüsü ve Windows görüntüsü gibi platform türevlerini içerebilir. Bu özellik, Microsoft (temel görüntü oluşturucular) gibi satıcıların birden çok platformu (Linux ve Windows) kapsayacak şekilde tek bir repo oluşturmasına olanak tanır. Örneğin, Docker Hub kayıt defterinde bulunan [dotnet/core](https://hub.docker.com/_/microsoft-dotnet-core/) deposu, aynı repo adını kullanarak Linux ve Windows Nano Server için destek sağlar.

Bir etiket belirtirseniz, aşağıdaki durumlarda olduğu gibi açık olan bir platformu hedeflemek:

- `mcr.microsoft.com/dotnet/core/aspnet:3.1-buster-slim` \
  Hedefler: .NET Core 3.1 yalnızca Linux'ta çalışma zamanı

- `mcr.microsoft.com/dotnet/core/aspnet:3.1-nanoserver-1909` \
  Hedefler: .NET Core 3.1 yalnızca Windows Nano Server'da çalışma zamanı

Ancak, aynı görüntü adını belirtirseniz, aynı etiketle bile, çok kemerli görüntüler `aspnet` (resim gibi) aşağıdaki örnekte gösterildiği gibi, dağıttAcağınız Docker ana bilgisayar işletim sistemi'ne bağlı olarak Linux veya Windows sürümünü kullanır:

- `mcr.microsoft.com/dotnet/core/aspnet:3.1` \
  Çok kemerli: .NET Core 3.1 docker ana bilgisayar işletim sistemi bağlı olarak Linux veya Windows Nano Server üzerinde yalnızca çalışma süresi

Bu şekilde, bir Windows ana bilgisayardan bir görüntü çektiğinde, Windows varyantını çeker ve linux ana bilgisayardan aynı görüntü adını çekerek Linux varyantını çeker.

### <a name="multi-stage-builds-in-dockerfile"></a>Dockerfile'de çok aşamalı yapılar

Dockerfile toplu komut dosyasına benzer. Makineyi komut satırından ayarlamanız gerekirse yapacağınız şeye benzer.

Bu ilk bağlamı oluşturan bir temel görüntü ile başlar, bu başlangıç dosya sistemi gibi, bu ana işletim sisteminin üstüne oturur. Bir işletim sistemi değil, ama kapsayıcı içinde "" işletim sistemi gibi düşünebilirsiniz.

Her komut satırının yürütülmesi, bir öncekinden gelen değişikliklerle dosya sisteminde yeni bir katman oluşturur, böylece birleştiğinde ortaya çıkan dosya sistemini oluşturur.

Her yeni katman bir öncekinin üstüne "dayanıyor" ve ortaya çıkan görüntü boyutu her komutla arttığı için, örneğin Bir uygulama oluşturmak ve yayınlamak için gereken SDK'yı eklemek zorunda kalırlarsa görüntüler çok büyük olabilir.

Bu çok aşamalı yapılar arsa içine almak (Docker 17,05 ve daha yüksek) kendi sihirli yapmaktır.

Temel fikir, Dockerfile yürütme işlemini aşamalı olarak ayırabildiğiniz, bir aşamanın bir veya daha fazla komutla izlenen ilk görüntü olduğu ve son aşamanın son görüntü boyutunu belirleyebileceğidir.

Kısacası, çok aşamalı yapılar, oluşturmanın farklı "aşamalarda" bölünmesine izin verir ve ardından yalnızca ara aşamalardan yalnızca ilgili dizinleri alarak son görüntüyü birleştirir. Bu özelliği kullanmak için genel strateji:

1. Uygulamayı oluşturmak ve bir klasöre yayınlamak için gereken her şey ile temel SDK görüntüsü (ne kadar büyük olursa olsun) kullanın ve ardından

2. Temel, küçük, yalnızca çalışma zamanı görüntü kullanın ve yayımlama klasörünü önceki aşamadan kopyalayarak küçük bir son görüntü oluşturabilirsiniz.

Muhtemelen çok aşamalı anlamak için en iyi yolu ayrıntılı bir Dockerfile geçiyor, satır satır, bu yüzden bir projeye Docker desteği eklerken Visual Studio tarafından oluşturulan ilk Dockerfile ile başlayalım ve daha sonra bazı optimizasyonlar içine alacak.

İlk Dockerfile şuna benzer:

```Dockerfile
 1  FROM mcr.microsoft.com/dotnet/core/aspnet:3.1 AS base
 2  WORKDIR /app
 3  EXPOSE 80
 4
 5  FROM mcr.microsoft.com/dotnet/core/sdk:3.1 AS build
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

Ve bunlar da satır satır detaylar:

- **Satır #1:** Bir "küçük" çalışma zamanı yalnızca temel görüntü ile bir sahne başlayın, referans için **temel** çağırın.

- **Satır #2:** Görüntüdeki **/uygulama** dizinini oluşturun.

- **Satır #3:** Bağlantı noktası **80'i**açığa çıkar.

- **Satır #5:** Bina /yayımlama için "büyük" görüntü ile yeni bir aşamaya başlayın. Referans için **inşa** deyin.

- **Satır #6:** Görüntüde dizin **/src** oluşturun.

- **Satır #7:** Satır 16'ya kadar, paketleri daha sonra geri yükleyebilmek için başvurulan **.csproj** proje dosyalarını kopyalayın.

- **Satır #17:** **Catalog.API** projesi ve başvurulan projeler için paketleri geri yükleyin.

- **Satır #18:** **Çözüm için tüm dizin ağacını** **(.dockerignore** dosyasında yer alan dosyalar/dizinler hariç) görüntüdeki **/src** dizinine kopyalayın.

- **Satır #19:** Geçerli klasörü **Catalog.API** projesiyle değiştirin.

- **Satır #20:** Projeyi (ve diğer proje bağımlılıklarını) oluşturun ve görüntüdeki **/uygulama** dizinine çıktı oluşturun.

- **Satır #22:** Yapıdan devam eden yeni bir aşamaya başlayın. Referans için **yayımlayın** deyin.

- **Satır #23:** Projeyi (ve bağımlılıkları) yayımlayın ve çıktıyı görüntüdeki **/uygulama** dizinine yayınlayın.

- **Satır #25:** **Üsten** devam eden yeni bir aşamaya başlayın ve **buna son**deyin.

- **Satır #26:** Geçerli dizini **/app**olarak değiştirin.

- **Satır #27:** **/app** dizinini sahne **yayımından** geçerli dizine kopyalayın.

- **Satır #28:** Kapsayıcı başlatıldığında çalışacak komutu tanımlayın.

Şimdi, eShopOnContainers durumunda, Linux kapkaplarında tam bir çözüm oluşturmak için yaklaşık 22 dakika veya daha fazla anlamına gelen tüm işlem performansını artırmak için bazı optimizasyonları inceleyelim.

Docker'ın katman önbellek özelliğinden yararlanırsınız, ki bu oldukça basittir: temel görüntü ve komutlar daha önce yürütülmüş bazı komutlarla aynıysa, yalnızca komutları yürütmeye gerek kalmadan ortaya çıkan katmanı kullanabilir ve böylece biraz zaman kazandırır.

Yani, **inşa** aşamasında odaklanalım, satır 5-6 çoğunlukla aynıdır, ama satır 7-17 eShopOnContainers her hizmet için farklıdır, bu yüzden her zaman yürütmek zorunda, ancak satır 7-16 değişti:

```Dockerfile
COPY . .
```

Sonra her hizmet için sadece aynı olurdu, tüm çözüm kopyalamak ve daha büyük bir katman yaratacak ama:

1. Kopyalama işlemi yalnızca ilk kez yürütülür (ve bir dosya değiştirilirse yeniden oluşturma) ve önbelleği diğer tüm hizmetler için kullanır ve

2. Daha büyük görüntü bir ara aşamada oluştuğundan, son görüntü boyutunu etkilemez.

Bir sonraki önemli optimizasyon, `restore` eShopOnContainers'ın her hizmeti için de farklı olan satır 17'de gerçekleştirilen komutu içerir. Bu satırı sadece olarak değiştirirseniz:

```Dockerfile
RUN dotnet restore
```

Tüm çözüm için paketleri geri, ama sonra tekrar, sadece bir kez yerine mevcut strateji ile 15 kez yapardı.

Ancak, `dotnet restore` yalnızca klasörde tek bir proje veya çözüm dosyası varsa çalışır, bu nedenle bunu başarmak biraz daha karmaşıktır ve çok fazla ayrıntıya girmeden çözmenin yolu şudur:

1. **.dockerignore**için aşağıdaki satırları ekleyin:

   - `*.sln`, ana klasör ağacındaki tüm çözüm dosyalarını yoksaymak

   - `!eShopOnContainers-ServicesAndWebApps.sln`, yalnızca bu çözüm dosyasını eklemek için.

2. Argüman `/ignoreprojectextensions:.dcproj` dahil `dotnet restore`, bu yüzden de docker-compose proje yok sayar ve sadece eShopOnContainers-ServicesAndWebApps çözümü için paketleri geri yükler.

Son optimizasyon için, sadece satır 20 gereksiz olduğunu olur, satır 23 de uygulama oluşturur ve gelir, özünde, satır 20 hemen sonra, bu yüzden başka bir zaman alıcı komut gider.

Ortaya çıkan dosya daha sonra:

```Dockerfile
 1  FROM mcr.microsoft.com/dotnet/core/aspnet:3.1 AS base
 2  WORKDIR /app
 3  EXPOSE 80
 4
 5  FROM mcr.microsoft.com/dotnet/core/sdk:3.1 AS publish
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

### <a name="creating-your-base-image-from-scratch"></a>Temel görüntünüzsıfırdan oluşturma

Sıfırdan kendi Docker temel görüntü oluşturabilirsiniz. Bu senaryo Docker ile başlayan biri için önerilmez, ancak kendi temel görüntünüzün belirli bitlerini ayarlamak istiyorsanız, bunu yapabilirsiniz.

### <a name="additional-resources"></a>Ek kaynaklar

- **Multi-arch .NET Core görüntüleri**.\
  <https://github.com/dotnet/announcements/issues/14>

- **Temel görüntü oluşturun.** Resmi Docker belgeleri.\
  <https://docs.docker.com/develop/develop-images/baseimages/>

![Adım 3 için görüntü.](./media/docker-app-development-workflow/step-3-create-dockerfile-defined-images.png)

## <a name="step-3-create-your-custom-docker-images-and-embed-your-application-or-service-in-them"></a>3. Adım Özel Docker resimlerinizi oluşturun ve uygulamanızı veya hizmetinizi bunlara göm

Uygulamanızdaki her hizmet için ilgili bir resim oluşturmanız gerekir. Uygulamanız tek bir hizmet veya web uygulamasından oluşuyorsa, tek bir görüntüye ihtiyacınız vardır.

Docker görüntülerinin Visual Studio'da sizin için otomatik olarak üretilediğini unutmayın. Aşağıdaki adımlar yalnızca düzenleyici/CLI iş akışı için gereklidir ve altında ne olduğu hakkında netlik için açıklanmıştır.

Bir geliştirici olarak, tamamlanmış bir özelliği itene veya kaynak denetim sisteminizde (örneğin, GitHub'a) geçene kadar yerel olarak geliştirmeniz ve test etmeniz gerekir. Bu, Docker görüntülerini oluşturmanız ve kapsayıcıları yerel bir Docker ana bilgisayara (Windows veya Linux VM) dağıtmanız ve bu yerel kapsayıcılara karşı çalıştırmanız, test etmeniz ve hata ayıklamanız gerektiği anlamına gelir.

Docker CLI ve Dockerfile'ınızı kullanarak yerel ortamınızda özel bir görüntü oluşturmak için Şekil 5-5'te olduğu gibi docker build komutunu kullanabilirsiniz.

![Docker build komutunun konsol çıktısını gösteren ekran görüntüsü.](./media/docker-app-development-workflow/run-docker-build-command.png)

**Şekil 5-5**. Özel Docker görüntüsü oluşturma

İsteğe bağlı olarak, proje klasöründen doğrudan docker build çalıştırmak yerine, önce gerekli .NET kitaplıkları ve ikilileri çalıştırarak `dotnet publish`dağıtılabilir bir klasör oluşturabilir ve ardından komutu `docker build` kullanabilirsiniz.

Bu, adında `cesardl/netcore-webapi-microservice-docker:first`bir Docker görüntüsü oluşturur. Bu durumda: birincisi belirli bir sürümü temsil eden bir etikettir. Oluşturduğunuz Docker uygulaması için oluşturmanız gereken her özel görüntü için bu adımı yineleyebilirsiniz.

Bir uygulama birden çok kapsayıcıdan yapıldığında (yani çok kapsayıcılı bir uygulamadır), ilgili docker-compose.yml dosyalarında açıkta bulunan meta verileri kullanarak ilgili tüm görüntüleri tek bir komutla oluşturmak için `docker-compose up --build` komutu da kullanabilirsiniz.

Mevcut görüntüleri Şekil 5-6'da gösterildiği gibi docker images komutunu kullanarak yerel deponuzda bulabilirsiniz.

![Varolan görüntüleri gösteren komut docker görüntüleri konsol çıkışı.](./media/docker-app-development-workflow/view-existing-images-with-docker-images.png)

**Şekil 5-6.** Docker görüntüleri komutunu kullanarak varolan görüntüleri görüntüleme

### <a name="creating-docker-images-with-visual-studio"></a>Visual Studio ile Docker görüntüleri oluşturma

Docker destekli bir proje oluşturmak için Visual Studio'yı kullandığınızda, açıkça bir görüntü oluşturmazsınız. Bunun yerine, dockerized uygulama veya hizmeti çalıştırmak için **F5** (veya **Ctrl-F5)** tuşuna bastığında görüntü sizin için oluşturulur. Bu adım Visual Studio'da otomatiktir ve bunun olduğunu görmezsiniz, ancak altında neler olup bittiğini bilmeniz önemlidir.

![İsteğe bağlı Adım 4 için görüntü.](./media/docker-app-development-workflow/step-4-define-services-docker-compose-yml.png)

## <a name="step-4-define-your-services-in-docker-composeyml-when-building-a-multi-container-docker-application"></a>4. Adım. Çok konteynerli Docker uygulaması oluştururken docker-compose.yml'de hizmetlerinizi tanımlayın

[Docker-compose.yml](https://docs.docker.com/compose/compose-file/) dosyası, dağıtım komutları içeren oluşturulmuş bir uygulama olarak dağıtılacak ilgili hizmetler kümesini tanımlamanızı sağlar. Ayrıca bağımlılık ilişkilerini ve çalışma zamanı yapılandırmasını da yapılandırır.

Docker-compose.yml dosyasını kullanmak için, aşağıdaki örnekte benzer içeriğe sahip ana veya kök çözüm klasörünüzde dosyaoluşturmanız gerekir:

```yml
version: '3.4'

services:

  webmvc:
    image: eshop/web
    environment:
      - CatalogUrl=http://catalog-api
      - OrderingUrl=http://ordering-api
    ports:
      - "80:80"
    depends_on:
      - catalog-api
      - ordering-api

  catalog-api:
    image: eshop/catalog-api
    environment:
      - ConnectionString=Server=sqldata;Port=1433;Database=CatalogDB;…
    ports:
      - "81:80"
    depends_on:
      - sqldata

  ordering-api:
    image: eshop/ordering-api
    environment:
      - ConnectionString=Server=sqldata;Database=OrderingDb;…
    ports:
      - "82:80"
    extra_hosts:
      - "CESARDLBOOKVHD:10.0.75.1"
    depends_on:
      - sqldata

  sqldata:
    image: mssql-server-linux:latest
    environment:
      - SA_PASSWORD=Pass@word
      - ACCEPT_EULA=Y
    ports:
      - "5433:1433"
```

Bu docker-compose.yml dosyası basitleştirilmiş ve birleştirilmiş bir sürümüdür. Her zaman gerekli olan her kapsayıcı için statik yapılandırma verileri (özel görüntünün adı gibi) ve bağlantı dizesi gibi dağıtım ortamına bağlı olabilecek yapılandırma bilgileri içerir. Daha sonraki bölümlerde, docker-compose.yml yapılandırmasını birden çok docker-compose dosyasına nasıl böleceğinizi ve ortam adedine ve yürütme türüne (hata ayıklama veya sürüm) bağlı olarak değerleri geçersiz kılmayı öğreneceksiniz.

Docker-compose.yml dosya örneği dört hizmeti `webmvc` tanımlar: hizmet (bir web`ordering-api` uygulaması), iki mikro hizmet (ve), `basket-api`ve bir veri kaynağı kapsayıcı, `sqldata`Linux için SQL Server'a dayalı bir kapsayıcı olarak çalışır. Her hizmet bir kapsayıcı olarak dağıtılır, bu nedenle her hizmet için bir Docker görüntüsü gerekir.

Docker-compose.yml dosyası, yalnızca hangi kapsayıcıların kullanıldığını değil, aynı zamanda bunların tek tek nasıl yapılandırıldığını da belirtir. Örneğin, .yml dosyasındaki `webmvc` kapsayıcı tanımı:

- Önceden oluşturulmuş `eshop/web:latest` bir görüntü kullanır. Ancak, docker-com-yürütmenin bir parçası olarak oluşturulacak görüntüyü, bir yapıya dayalı ek bir yapılandırmayla da yapılandırabilirsiniz: docker-compose dosyasındaki bölüm.

- İki ortam değişkenini (CatalogUrl ve OrderingUrl) başharfe getirir.

- Konteynerüzerindeki 80 portu ana makinedeki harici bağlantı noktasına 80 iletir.

- Web uygulamasını katalog ve sipariş hizmetine depends_on ayarı ile bağlar. Bu, hizmetin bu hizmetler başlatılana kadar beklemesine neden olur.

Mikro hizmetlerin ve çoklu konteyner uygulamalarının nasıl uygulanacağını ele aldığımızda docker-compose.yml dosyasını daha sonraki bir bölümde tekrar ziyaret edeceğiz.

### <a name="working-with-docker-composeyml-in-visual-studio-2019"></a>Visual Studio 2019'da docker-compose.yml ile çalışma

Daha önce de belirttiğimiz gibi, bir projeye Dockerfile eklemenin yanı sıra, Visual Studio 2017 (15.8 sürümünden itibaren) Docker Compose için bir çözüme orkestratör desteği ekleyebilir.

Şekil 5-7'de gösterildiği gibi konteyner orkestratör desteği eklediğinizde, Visual Studio ilk kez proje için Dockerfile oluşturur ve çözümünüzde birkaç `docker-compose*.yml` genel dosyayla birlikte yeni bir (hizmet bölümü) proje oluşturur ve projeyi bu dosyalara ekler. Daha sonra docker-compose.yml dosyalarını açabilir ve ek özelliklerle güncelleyebilirsiniz.

Docker-compose.yml dosyasına eklemek istediğiniz her projeyi bu işlem formunu yinelemeniz gerekir.

Bu yazının yazıldığı sırada Visual Studio, **Docker Compose** ve **Kubernetes/Helm** orkestratörlerini desteklemektedir.

![Proje bağlamı menüsünde Konteyner Orchestrator Desteği seçeneğini gösteren ekran görüntüsü.](./media/docker-app-development-workflow/add-container-orchestrator-support-option.png)

**Şekil 5-7**. Visual Studio 2019'da ASP.NET Core projesine sağ tıklayarak Docker desteği ekleme

Visual Studio'da çözümünüze orchestrator desteği ekledikten sonra, Solution Explorer'da `docker-compose.dcproj` Şekil 5-8'de gösterildiği gibi eklenen docker-compose.yml dosyalarını içeren yeni bir düğüm de görürsünüz.

![Solution Explorer'da docker-compose düğümünün ekran görüntüsü.](./media/docker-app-development-workflow/docker-compose-tree-node.png)

**Şekil 5-8**. Visual Studio 2019 Solution Explorer'da eklenen **docker-compose** ağaç düğümü

`docker-compose up` Komutu kullanarak tek bir docker-compose.yml dosyası ile çok kapsayıcı uygulama dağıtabilirsiniz. Ancak Visual Studio, ortama (geliştirme veya üretim) ve yürütme türüne (sürüm veya hata ayıklama) bağlı olarak değerleri geçersiz kılabilmeniz için bunlardan bir grup ekler. Bu özellik sonraki bölümlerde açıklanacaktır.

![Adım 5 için görüntü.](./media/docker-app-development-workflow/step-5-run-containers-compose-app.png)

## <a name="step-5-build-and-run-your-docker-application"></a>5. Adım. Docker uygulamanızı oluşturun ve çalıştırın

Uygulamanızda yalnızca tek bir kapsayıcı varsa, docker ana bilgisayarınıza (VM veya fiziksel sunucu) dağıtarak uygulamayı çalıştırabilirsiniz. Ancak, uygulamanız birden çok hizmet içeriyorsa, tek bir CLI komutu`docker-compose up)`kullanarak (veya kapakların altında bu komutu kullanacak Visual Studio ile) oluşturulmuş bir uygulama olarak dağıtabilirsiniz. Farklı seçeneklere bakalım.

### <a name="option-a-running-a-single-container-application"></a>Seçenek A: Tek kapsayıcı uygulaması çalıştırma

#### <a name="using-docker-cli"></a>Docker CLI kullanma

Şekil 5-9'da `docker run` gösterildiği gibi komutu kullanarak docker kapsayıcısı çalıştırabilirsiniz:

```console
docker run -t -d -p 80:5000 cesardl/netcore-webapi-microservice-docker:first
```

Yukarıdaki komut, her çalıştırışta belirtilen görüntüden yeni bir kapsayıcı örneği oluşturur. Parametreyi `--name` kapsayıcıya ad vermek için kullanabilir ve `docker start {name}` ardından varolan bir kapsayıcı örneğini çalıştırmak için kapsayıcı kimliğini veya otomatik adı kullanabilirsiniz.

![Docker çalıştır komutunu kullanarak Docker kapsayıcısını çalıştıran ekran görüntüsü.](./media/docker-app-development-workflow/use-docker-run-command.png)

**Şekil 5-9**. Docker çalıştır komutunu kullanarak Docker kapsayıcısı çalıştırma

Bu durumda, komut, kapsayıcının iç bağlantı noktası 5000'i ana makinenin 80 bağlantı noktasına bağlar. Bu, ana bilgisayar bağlantı noktasının 80 bağlantı noktasını dinlediği ve konteynerüzerindeki 5000 portuna iletilmesi anlamına gelir.

Gösterilen karma kapsayıcı kimliğidir ve `--name` seçenek kullanılmazsa rasgele okunabilir bir ad da atanır.

#### <a name="using-visual-studio"></a>Visual Studio’yu kullanma

Konteyner orkestrator desteği eklemediyseniz, **Ctrl-F5** tuşuna basarak Visual Studio'da tek bir kapsayıcı uygulaması çalıştırabilir ve konteynır içindeki uygulamayı hata ayıklamak için **F5'i** de kullanabilirsiniz. Kapsayıcı docker run kullanarak yerel olarak çalışır.

### <a name="option-b-running-a-multi-container-application"></a>Seçenek B: Çok kapsayıcılı bir uygulama çalıştırma

Çoğu kurumsal senaryoda, Docker uygulaması birden çok hizmetiçeren olacaktır, bu da Şekil 5-10'da gösterildiği gibi çok kapsayıcılı bir uygulama çalıştırmanız gerektiği anlamına gelir.

![Birkaç Docker konteynerli VM](./media/docker-app-development-workflow/vm-with-docker-containers-deployed.png)

**Şekil 5-10**. Docker konteynerleri dağıtılan VM

#### <a name="using-docker-cli"></a>Docker CLI kullanma

Docker CLI ile çok kapsayıcılı bir uygulama `docker-compose up` çalıştırmak için komutu kullanırsınız. Bu komut, çok kapsayıcılı bir uygulama dağıtmak için çözüm düzeyinde sahip olduğunuz **docker-compose.yml** dosyasını kullanır. Şekil 5-11, docker-compose.yml dosyasını içeren ana çözüm dizininizden komutu çalıştırırken sonuçları gösterir.

![Docker-comto command komutunu çalıştırırken ekran görünümü](./media/docker-app-development-workflow/results-docker-compose-up.png)

**Şekil 5-11**. Docker-comto komutunu çalıştırırken örnek sonuçlar

Docker-compose up komutu çalıştırıldıktan sonra, uygulama ve ilgili kapsayıcılar Şekil 5-10'da belirtildiği gibi Docker ana cihazınıza dağıtılır.

#### <a name="using-visual-studio"></a>Visual Studio’yu kullanma

Visual Studio 2019'u kullanarak çok konteynerli bir uygulama çalıştırmak daha kolay olamaz. Her zamanki gibi hata ayıklamak için **ctrl-F5** tuşuna veya **F5'e** basarak başlangıç projesi olarak **docker-compose** projesini ayarlamanız gerekiyor.  Visual Studio, her zamanki gibi kesme noktaları oluşturabilir ve hata ayıklama zaten bağlı olan "uzak sunucularda" çalışan bağımsız işlemler haline ne hata ayıklama sağlar, böylece gerekli tüm kurulum işler. Aynen böyle.

Daha önce de belirtildiği gibi, bir çözüm içinde bir projeye Docker çözüm desteği eklediğinizde, bu proje tüm çözümü aynı anda çalıştırmanızı veya hata ayıklamanızı sağlayan genel (çözüm düzeyinde) docker-compose.yml dosyasında yapılandırılır. Visual Studio, Docker çözüm desteği etkin olan her proje için bir konteyner başlatacak ve sizin için tüm dahili adımları gerçekleştirecektir (dotnet yayımlama, docker build, vb.).

Tüm angarya bir göz atmak istiyorsanız, dosyaya bir göz atın:

`{root solution folder}\obj\Docker\docker-compose.vs.debug.g.yml`

Burada önemli olan nokta, Şekil 5-12'de gösterildiği gibi Visual Studio 2019'da F5 anahtar eylemi için ek bir **Docker** komutu olmasıdır. Bu seçenek, docker-compose.yml dosyalarında tanımlanan tüm kapsayıcıları çözüm düzeyinde çalıştırarak çok kapsayıcılı bir uygulamayı çalıştırmanızı veya hata ayıklamanızı sağlar. Birden çok kapsayıcı çözümlerini hata ayıklama yeteneği, her bir kesme noktası farklı bir projede (kapsayıcı) birkaç kesme noktası ayarlayabileceğiniz anlamına gelir ve Visual Studio'dan hata ayıklama sırasında farklı projelerde tanımlanan ve üzerinde çalışan kesme noktalarında duracağınız anlamına gelir farklı kaplar.

![Docker-compose projesini çalıştıran hata ayıklama araç çubuğunun ekran görüntüsü.](./media/docker-app-development-workflow/debug-toolbar-docker-compose-project.png)

**Şekil 5-12**. Visual Studio 2019'da çoklu konteyner uygulamaları çalıştırma

### <a name="additional-resources"></a>Ek kaynaklar

- **Uzak bir Docker ana bilgisayara ASP.NET kapsayıcısı dağıtma** \
  <https://docs.microsoft.com/azure/vs-azure-tools-docker-hosting-web-apps-in-docker>

### <a name="a-note-about-testing-and-deploying-with-orchestrators"></a>Orkestratörlerle test etme ve dağıtma hakkında bir not

Docker-compose up ve docker run komutları (veya Visual Studio'daki kapsayıcıları çalıştırma ve hata ayıklama) geliştirme ortamınızdaki kapsayıcıları test etmek için yeterlidir. Ancak bu yaklaşımı, [Kubernetes](https://kubernetes.io/) veya [Service Fabric](https://azure.microsoft.com/services/service-fabric/)gibi orkestratörleri hedeflemeniz gereken üretim dağıtımları için kullanmamalısınız. Kubernetes kullanıyorsanız, bunları ağ için kapsayıcılar ve [hizmetleri](https://kubernetes.io/docs/concepts/services-networking/service/) düzenlemek için [bölmeleri](https://kubernetes.io/docs/concepts/workloads/pods/pod/) kullanmanız gerekir. Pod oluşturma ve modifikasyondüzenlemek için dağıtımları da [kullanırsınız.](https://kubernetes.io/docs/concepts/workloads/controllers/deployment/)

![Adım 6 için görüntü.](./media/docker-app-development-workflow/step-6-test-app-microservices.png)

## <a name="step-6-test-your-docker-application-using-your-local-docker-host"></a>6. Adım. Docker uygulamanızı yerel Docker ana bilgisayarınızı kullanarak test edin

Bu adım, uygulamanızın ne yaptığına bağlı olarak değişir. Tek bir kapsayıcı veya hizmet olarak dağıtılan basit bir .NET Core Web uygulamasında, Docker ana bilgisayarında bir tarayıcı açarak ve Şekil 5-13'te gösterildiği gibi bu siteye yönlendirerek hizmete erişebilirsiniz. (Dockerfile'deki yapılandırma kapsayıcıyı 80'den başka bir bağlantı noktasıyla eşlerse, ANA Bilgisayar bağlantı noktasını URL'ye ekleyin.)

![Localhost/API/values'den yanıtın ekran görüntüsü.](./media/docker-app-development-workflow/test-docker-app-locally-localhost.png)

**Şekil 5-13**. Docker uygulamanızı localhost kullanarak yerel olarak test etme örneği

Localhost Docker ana bilgisayar IP'sini işaret etmiyorsa (varsayılan olarak, Docker CE kullanırken, olmalıdır), hizmetinize gitmek için makinenizin ağ kartının IP adresini kullanın.

Tarayıcıdaki bu URL'nin tartışılan belirli kapsayıcı örneği için 80 no'lu bağlantı noktasını kullandığını unutmayın. Ancak, önceki adımda açıklandığı gibi, docker run komutu yla bu şekilde dağıtıldığı için, istekler dahili olarak 5000 portuna yönlendiriliyor.

Ayrıca, Şekil 5-14'te gösterildiği gibi, terminalden kıvrılma kullanarak uygulamayı test edebilirsiniz. Windows'daki Docker yüklemesinde, varsayılan Docker Host IP'si makinenizin gerçek IP adresine ek olarak her zaman 10.0.75.1'dir.

![Kıvrılma http://10.0.75.1/API/values ile almaktan konsol çıkışı.](./media/docker-app-development-workflow/test-docker-app-locally-curl.png)

**Şekil 5-14**. Docker uygulamanızı curl kullanarak yerel olarak test etme örneği

### <a name="testing-and-debugging-containers-with-visual-studio-2019"></a>Visual Studio 2019 ile konteynerleri test etme ve hata ayıklama

Visual Studio 2019 ile kapsayıcıları çalıştırıp hata ayıklarken,.NET uygulamasını, kapsayıcıolmadan çalışırken yaptığınız gibi hata ayıklayabilirsiniz.

### <a name="testing-and-debugging-without-visual-studio"></a>Visual Studio olmadan test ve hata ayıklama

Düzenleyici/CLI yaklaşımını kullanarak geliştiriyorsanız, hata ayıklama kapsayıcıları daha zordur ve büyük olasılıkla izleme ler oluşturarak hata ayıklamak istersiniz.

### <a name="additional-resources"></a>Ek kaynaklar

- **Uygulamaları yerel bir Docker konteynerinde hata ayıklama** \
  [https://docs.microsoft.com/visualstudio/containers/edit-and-refresh](/visualstudio/containers/edit-and-refresh)

- **Steve Lasker' ı. Docker ile Core Apps ASP.NET oluşturun, hata ayıklayın, dağıtın.** Video. \
  <https://channel9.msdn.com/Events/Visual-Studio/Visual-Studio-2017-Launch/T115>

## <a name="simplified-workflow-when-developing-containers-with-visual-studio"></a>Visual Studio ile kaplar geliştirirken basitleştirilmiş iş akışı

Visual Studio'yu kullanırken iş akışı, editör/CLI yaklaşımını kullandığınızdan çok daha basittir. Dockerfile ve docker-compose.yml dosyaları yla ilgili Docker tarafından gerekli olan adımların çoğu Şekil 5-15'te gösterildiği gibi Visual Studio tarafından gizlenir veya basitleştirilmiştir.

:::image type="complex" source="./media/docker-app-development-workflow/simplified-life-cycle-containerized-apps-docker-cli.png" alt-text="Bir uygulama oluşturmak için gereken beş basitleştirilmiş adımı gösteren diyagram.":::
Docker uygulamaları için geliştirme süreci: 1 - Uygulamanızı kodlayın, 2 - Dockerfile/s yazın, 3 - Dockerfile/s'de tanımlanan görüntüleri oluşturun, 4 - (isteğe bağlı) Docker-compose.yml dosyasında hizmetleri oluşturun, 5 - Konteyner veya docker-create app, 6 - Uygulamanızı veya mikro hizmetleri test edin, 7 - Repo'yu tekrarlamak için bastırın ve tekrarlayın.
:::image-end:::

**Şekil 5-15**. Visual Studio ile gelişirken basitleştirilmiş iş akışı

Buna ek olarak, adım 2 (projelerinize Docker desteği ekleyerek) sadece bir kez gerçekleştirmek gerekir. Bu nedenle, iş akışı, başka bir geliştirme için .NET kullanırken olağan geliştirme görevlerine benzer. Kapakların altında neler olup bittiğini (görüntü oluşturma işlemi, kullandığınız temel görüntüler, kapsayıcıların dağıtımı, vb.) bilmeniz gerekir ve bazen davranışları özelleştirmek için Dockerfile veya docker-compose.yml dosyasını da kaldırmanız gerekir. Ama işin çoğu büyük ölçüde Visual Studio kullanarak basitleştirilmiş, çok daha üretken hale.

### <a name="additional-resources"></a>Ek kaynaklar

- **Steve Lasker' ı. .NET Docker Geliştirme Visual Studio (2017)** \
  <https://channel9.msdn.com/Events/Visual-Studio/Visual-Studio-2017-Launch/T111>

## <a name="using-powershell-commands-in-a-dockerfile-to-set-up-windows-containers"></a>Windows Kapsayıcıları kurmak için Dockerfile'daki PowerShell komutlarını kullanma

[Windows Kapsayıcıları,](https://docs.microsoft.com/virtualization/windowscontainers/about/index) mevcut Windows uygulamalarınızı Docker görüntülerine dönüştürmenize ve bunları Docker ekosisteminin geri kalanıyla aynı araçlarla dağıtmanıza olanak sağlar. Windows Kapsayıcıları'nı kullanmak için, aşağıdaki örnekte gösterildiği gibi Dockerfile'da PowerShell komutlarını çalıştırın:

```Dockerfile
FROM mcr.microsoft.com/windows/servercore
LABEL Description="IIS" Vendor="Microsoft" Version="10"
RUN powershell -Command Add-WindowsFeature Web-Server
CMD [ "ping", "localhost", "-t" ]
```

Bu durumda, bir Windows Server Core temel görüntüsü (FROM ayarı) kullanıyoruz ve PowerShell komutu (RUN ayarı) ile IIS yüklüyoruz. Benzer bir şekilde, powershell komutlarını kullanarak ASP.NET 4.x, .NET 4.6 veya başka bir Windows yazılımı gibi ek bileşenler de kullanabilirsiniz. Örneğin, Dockerfile'deki aşağıdaki komut 4,5'ASP.NET ayarlar:

```Dockerfile
RUN powershell add-windowsfeature web-asp-net45
```

### <a name="additional-resources"></a>Ek kaynaklar

- **aspnet-docker/Dockerfile.** Örnek PowerShell komutları dockerdosyalarından Windows özelliklerini içerecek şekilde çalıştırılabilmektedir.\
  <https://github.com/Microsoft/aspnet-docker/blob/master/4.7.1-windowsservercore-ltsc2016/runtime/Dockerfile>

>[!div class="step-by-step"]
>[Önceki](index.md)
>[Sonraki](../multi-container-microservice-net-applications/index.md)
