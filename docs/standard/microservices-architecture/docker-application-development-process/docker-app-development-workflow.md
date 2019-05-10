---
title: Docker uygulamaları için geliştirme iş akışı
description: Docker tabanlı uygulamalar geliştirmek için iş akışının ayrıntılarını anlayın. Adım adım başlar ve dockerfile'ları iyileştirmek ve Visual Studio kullanırken kullanılabilir Basitleştirilmiş akışıyla sonlandırmak üzere bazı ayrıntıları alın.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 01/07/2019
ms.openlocfilehash: 3d2a57c7dda722bcc39895b41c35a3a29ddd17e2
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64751460"
---
# <a name="development-workflow-for-docker-apps"></a>Docker uygulamaları için geliştirme iş akışı

Uygulama geliştirme yaşam döngüsü, tercih ettiğiniz dili kullanarak uygulama kodu ve yerel olarak test bir geliştirici olarak, bilgisayarınızın başında başlatır. Hangi dil, çerçeve ve seçtiğiniz platform ne olursa olsun bu iş akışı ile her zaman geliştirme ve Docker kapsayıcılarını test, ancak bunun yerel olarak yapılması.

Her kapsayıcı (bir Docker görüntüsü örneği), aşağıdaki bileşenleri içerir:

- Bir işletim sistemi seçimi, örneğin, bir Linux dağıtımı, Windows Nano sunucu veya Windows Server Core.

- Örneğin, kaynak kod ve uygulama ikili dosyalarını geliştirme sırasında eklenen dosyaları.

- Ortam ayarlarını ve bağımlılıklarını gibi yapılandırma bilgileri.

## <a name="workflow-for-developing-docker-container-based-applications"></a>Docker kapsayıcı tabanlı uygulamaları geliştirmek için iş akışı

Bu bölümde açıklanmaktadır *iç döngü* Docker kapsayıcı tabanlı uygulamaları için geliştirme iş akışı. İç döngü iş akışı, üretim dağıtıma kadar içerebilir ve yalnızca geliştiricinin bilgisayarında geliştirme çalışmanın odaklanır daha geniş DevOps iş akışını dikkate yok anlamına gelir. Bu adımlar yalnızca bir kez gerçekleştirilir beri ortamı ayarlamak için ilk adımlarında dahil değildir.

Uygulamanın kendi Hizmetleri ve ek kitaplıklar (bağımlılıklar) karakterlerinden oluşur. Aşağıda, genellikle bir Docker uygulaması oluştururken Şekil 5-1'de gösterildiği gibi temel adımlar verilmiştir.

![Docker uygulamaları için geliştirme işlemi: 2 - uygulamanızı 1 - kod yazma Dockerfile/sn, 3 - Dockerfile/sn, 4 - (isteğe bağlı) oluşturma hizmetleri docker-compose.yml dosyasında tanımlanan görüntüler oluşturmak, depoyu ve yineleme - kapsayıcı çalıştırın veya docker-compose uygulaması, 6 - uygulama ve mikro hizmetler, 7 Test - 5 anında iletme. ](./media/image1.png)

**Şekil 5-1.** Kapsayıcılı Docker uygulamaları geliştirmeye yönelik adım adım iş akışı

Bu bölümde, tüm bu işlemi ayrıntılı olarak verilmiştir ve önemli adım her bir Visual Studio ortamında odaklanarak açıklanmıştır.

Bir düzenleyici/CLI geliştirme yaklaşımını (örneğin, Visual Studio Code ve Docker CLI'yı MacOS ya da Windows) kullanırken, her adım genellikle Visual Studio kullanıyorsanız, daha ayrıntılı biçimde bilmeniz gerekir. E-kitabı CLI ortamda çalışma hakkında daha fazla bilgi için bkz. [Microsoft Platforms ve araçlarla kapsayıcılı Docker uygulaması yaşam döngüsü](https://aka.ms/dockerlifecycleebook/).

Visual Studio 2017 kullanırken, bu adımların çoğunu sizin yerinize üretkenliğinizi önemli ölçüde artıran işlenir. Bu, özellikle kullandığınız Visual Studio 2017 ve çok kapsayıcılı uygulamalar hedefleme olduğunda geçerlidir. Örneğin, yalnızca tek bir tıklatmayla projelerinize uygulamanız için yapılandırma ile Dockerfile ve docker-compose.yml dosyası Visual Studio ekler. Visual Studio'da uygulamayı çalıştırdığınızda, Docker görüntüsünü oluşturur ve çok kapsayıcılı bir uygulama doğrudan Docker'da çalıştırılır; bile aynı anda birden fazla kapsayıcılar ayıklamanızı sağlar. Bu özellikler, geliştirme hızını çok artırır.

Yalnızca Visual Studio bu adımlar otomatik hale getirir ancak neler olduğunu bilmeniz gerekmez gelmez üzerinde underneath Docker ile. Bu nedenle, aşağıdaki yönergeleri her adım ayrıntılı olarak açıklanmaktadır.

![1 - uygulamanızı kodlayın](./media/image2.png)

## <a name="step-1-start-coding-and-create-your-initial-application-or-service-baseline"></a>Adım 1. Kodlamaya başlayın ve ilk uygulama veya hizmet taban çizgisi oluşturma

Docker uygulaması geliştirmek, Docker olmadan uygulama geliştirme şekilde benzerdir. Docker için geliştirmeye devam ederken, dağıtma ve uygulama ya da Windows kapsayıcıları kullanıyorsanız, yerel ortamınızda (Docker ile bir Linux VM Kurulumu) ya da doğrudan Windows Docker kapsayıcıları içinde çalışan hizmetleri test etme, farktır.

### <a name="set-up-your-local-environment-with-visual-studio"></a>Visual Studio ile yerel ortamınızı ayarlayın

Başlamak için sahip olduğunuzdan emin olun [Docker Community Edition'ı (CE)](https://docs.docker.com/docker-for-windows/) aşağıdaki yönergelerinde açıklandığı gibi yüklü Windows için:

[İçin Docker CE Windows ile çalışmaya başlama](https://docs.docker.com/docker-for-windows/)

Ayrıca, Visual Studio 2017 sürüm 15.7 veya üzeri ile ihtiyacınız **.NET Core çoklu platform geliştirme** yüklüyse, Şekil 5-2'de gösterildiği gibi iş yükü.

![.NET core çoklu platform geliştirme iş yükü seçimi, Visual Studio yüklemesi sırasında.](./media/image3.png)

**Şekil 5-2**. Seçme **.NET Core çoklu platform geliştirme** Visual Studio 2017 Kurulum sırasında iş yükü

Uygulamanızda Docker'ı etkinleştirme ve Docker sınama dağıtımı önce (genellikle, kapsayıcıları kullanmayı planlıyorsanız, .NET Core) düz .NET uygulamanızda kodlamaya başlayabilirsiniz. Ancak, üzerinde Docker olabildiğince çabuk, çünkü gerçek ortam olacak ve sorunları olabildiğince çabuk bulunabileceğini çalışma başlangıç önerilir. Visual Studio, bu nedenle, neredeyse saydam hissettiği Docker'la çalışmak kolaylaştırır çünkü bu teşvik edilir — çok kapsayıcılı uygulamalar Visual Studio'dan hata ayıklama sırasında en iyi örnek.

### <a name="additional-resources"></a>Ek kaynaklar

- **İçin Docker CE Windows ile çalışmaya başlama** \
  <https://docs.docker.com/docker-for-windows/>

- **Visual Studio 2017** \
  [https://visualstudio.microsoft.com/downloads/](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017)

![2 - dockerfile'ları yazma](./media/image4.png)

## <a name="step-2-create-a-dockerfile-related-to-an-existing-net-base-image"></a>Adım 2. Mevcut bir .NET temel görüntü için ilgili bir Dockerfile'ı oluşturma

Derlemek istediğiniz her özel görüntü için bir Dockerfile ihtiyacınız; Ayrıca Visual Studio veya el ile Docker CLI'yı kullanarak otomatik olarak dağıtıp dağıtmamak dağıtılması için her kapsayıcı için bir Dockerfile gerekir (docker run ve docker-compose komutları). Uygulamanızda tek bir özel hizmet varsa, tek bir Dockerfile gerekir. Uygulamanız birden çok hizmeti (olduğu gibi bir mikro hizmetler mimarisinde) içeriyorsa, her hizmet için bir Dockerfile gerekir.

Dockerfile, uygulamanızın veya hizmetinizin kök klasöründe yer alır. Bu, Docker ayarlama ve bir kapsayıcıdaki uygulama veya hizmetinizin çalıştırma bildiririz komutlar içerir. El ile bir Dockerfile içinde kod oluşturma ve birlikte .NET bağımlılıklarınızı projenize ekleyin.

Bu görevi, Visual Studio ve araçları için Docker ile yalnızca birkaç tıklamayla gerektirir. Visual Studio 2017'de yeni bir proje oluşturduğunuzda, adlı bir seçenek yoktur **kapsayıcı etkinleştir (Docker) desteği**Şekil 5-3'te gösterildiği gibi.

![Visual Studio 2017'de yeni bir ASP.NET Core projesi oluştururken, Docker desteği onay kutusunu etkinleştir](./media/image5.png)

**Şekil 5-3**. Visual Studio 2017'de yeni bir ASP.NET Core projesi oluştururken, Docker desteğini etkinleştirme

Projeye sağ tıklayarak mevcut bir ASP.NET Core web uygulaması projesini Docker desteğini de etkinleştirebilirsiniz **Çözüm Gezgini** seçerek **Ekle** > **Docker desteği** Şekil 5-4'te gösterildiği gibi.

![Visual Studio'da Docker desteği menü seçeneği ekleyin](./media/image6.png)

**Şekil 5-4**. Mevcut bir Visual Studio 2017 projesinde Docker desteğini etkinleştirme

Bu eylem ekler bir *Dockerfile* gerekli yapılandırmayla projeye ve ASP.NET Core projelerinde kullanılabilir.

Benzer şekilde, Visual Studio da çözümün tamamının seçeneğiyle için bir docker-compose.yml dosyası ekleyebilirsiniz **Ekle > kapsayıcı Düzenleyicisi desteği**. 4. adımda bu seçenek daha ayrıntılı şunları keşfedeceğiz.

### <a name="using-an-existing-official-net-docker-image"></a>Mevcut bir resmi .NET Docker görüntüsü kullanma

Alma gibi resmi bir depodan bir temel görüntünün üstüne kapsayıcınız için genellikle özel bir görüntü oluşturun [Docker Hub](https://hub.docker.com/) kayıt defteri. Visual Studio'da Docker desteğini etkinleştirmek ne olacağını perde tam olarak olmasıdır. Mevcut bir Dockerfile kullanacağı `aspnetcore` görüntü.

Daha önce hangi Docker görüntülerini ve seçtiğiniz işletim sistemi ve framework bağlı olarak kullanabilirsiniz depoları açıklanmıştır. Örneğin, ASP.NET Core (Linux veya Windows) kullanmak istiyorsanız, kullanılacak görüntüyü olan `mcr.microsoft.com/dotnet/core/aspnet:2.2`. Bu nedenle, kapsayıcınız için kullanacağınız hangi temel Docker görüntüsüne belirtmeniz yeterlidir. Ekleyerek bunu `FROM mcr.microsoft.com/dotnet/core/aspnet:2.2` Dockerfile için. Bu Visual Studio tarafından otomatik olarak gerçekleştirilir, ancak sürüm olsaydı, bu değeri güncelleştirin.

Bir sürüm numarası ile Docker Hub resmi bir .NET görüntü deposundan kullanarak aynı dil özellikleri (geliştirme, test ve üretim dahil) tüm makinelerde kullanılabilir olmasını sağlar.

Aşağıdaki örnek bir ASP.NET Core kapsayıcı için bir örnek Dockerfile gösterir.

```Dockerfile
FROM mcr.microsoft.com/dotnet/core/aspnet:2.2
ARG source
WORKDIR /app
EXPOSE 80
COPY ${source:-obj/Docker/publish} .
ENTRYPOINT ["dotnet", " MySingleContainerWebApp.dll "]
```

Bu durumda, görüntü resmi ASP.NET Core Docker görüntü (Linux ve Windows için çok arch) 2.2 sürümünü temel alır. Ayar budur `FROM mcr.microsoft.com/dotnet/core/aspnet:2.2`. (Bu temel görüntü hakkında daha fazla bilgi için bkz: [.NET Core, Docker görüntüsü](https://hub.docker.com/_/microsoft-dotnet-core/) sayfası.) Dockerfile içinde ayrıca isteyin (Bu durumda, SUNMAYA ayarı ile yapılandırılmış olarak 80 numaralı bağlantı noktası) çalışma zamanında kullanacağınız TCP bağlantı noktasında dinlemek için Docker gerekir.

Dil ve çerçeve kullanmakta olduğunuz bağlı olarak bir Dockerfile içinde ek yapılandırma ayarları belirtebilirsiniz. Örneğin, giriş noktası satırla `["dotnet", "MySingleContainerWebApp.dll"]` bir .NET Core uygulamasını çalıştırmak için Docker söyler. .NET uygulaması derleme ve çalıştırma için SDK ve .NET Core CLI (dotnet CLI) kullanıyorsanız, bu ayar farklı olacaktır. ENTRYPOINT satır ve diğer ayarları uygulamanız için seçtiğiniz dile ve platforma bağlı olarak farklı olacaktır alt çizgidir.

### <a name="additional-resources"></a>Ek kaynaklar

- **.NET Core uygulamaları için Docker görüntüleri oluşturma** \
  [https://docs.microsoft.com/dotnet/core/docker/building-net-docker-images](../../../core/docker/building-net-docker-images.md)

- **Kendi görüntünüzü**. Resmi Docker belgelerinde. \
  <https://docs.docker.com/engine/tutorials/dockerimages/>

- **.NET ile kapsayıcı görüntülerini güncel kalma** \
  <https://devblogs.microsoft.com/dotnet/staying-up-to-date-with-net-container-images/>

- **.NET ve Docker'a DockerCon 2018 güncelleştirmesi birlikte - kullanma** \
  <https://devblogs.microsoft.com/dotnet/using-net-and-docker-together-dockercon-2018-update/>

### <a name="using-multi-arch-image-repositories"></a>Çok yay görüntü depolarını kullanarak

Tek bir depoda bir Linux görüntüsü ve bir Windows görüntüsünü gibi platformu çeşitleri içerebilir. Bu özellik, (yani Linux ve Windows) birden çok platform karşılamak için tek depo oluşturmak Microsoft (temel Görüntü Oluşturucu) gibi satıcıları sağlar. Örneğin, [dotnet/core](https://hub.docker.com/_/microsoft-dotnet-core/) Docker Hub kayıt defterinde depo aynı depo adını kullanarak Linux ve Windows Nano sunucu için destek sağlar.

Açık bir platformu hedefleyen bir etiket belirtirseniz, aşağıdaki durumlarda ister:

- `microsoft/dotnet:2.2-aspnetcore-runtime-stretch-slim` \
  Hedefleri: .NET Core çalışma zamanı Linux üzerinde yalnızca 2.2

- `microsoft/dotnet:2.2-aspnetcore-runtime-nanoserver-1809` \
  Hedefleri: .NET Core çalışma zamanı Windows Nano Sunucu'da yalnızca 2.2

Ancak, görüntü adının aynısını bile aynı etiketi ile çok yay görüntüleri belirtirseniz (gibi `aspnetcore` görüntü) dağıtmakta, Linux veya Windows sürümü işletim sistemi Docker konağı bağlı olarak aşağıdaki örnekte gösterildiği gibi kullanın:

- `microsoft/dotnet:2.2-aspnetcore-runtime` \
  Çok arch: .NET Core çalışma zamanı Linux veya Windows Nano sunucu üzerinde Docker ana bilgisayar işletim sistemi bağlı olarak yalnızca 2.2

Windows konaktan görüntü çekme bu şekilde, Windows değişken çeker ve bir Linux ana bilgisayarından görüntü adının aynısını çekme Linux değişken çeker.

### <a name="multi-stage-builds-in-dockerfile"></a>Çok aşamalı Dockerfile içinde oluşturur.

Dockerfile, bir batch betiğiyle aynıdır. Benzer komut satırından makine kurmak tablonuz varsa ne yapmanız.

Başlangıç bağlamı ayarlar temel bir görüntü ile başlar, konak işletim sistemi en üstünde yer alan başlangıç dosya sistemi gibidir. Bir işletim sistemi değil, ancak kapsayıcı içinde "" işletim sistemi, gibi düşünebilirsiniz.

Her komut satırı yürütme, Öncekine değişikliklerle sisteminde yeni bir katman oluşturur. böylece, birleştirildiğinde, sonuçta elde edilen dosya sistemi üretir.

Her yeni katmanı "ye dayanıyorsa eskisinin üzerine" ve her komut ile elde edilen görüntü boyutunu artırır olduğundan, görüntüleri içerecek şekilde oluşturulduysa Örneğin, SDK'sı geliştirmek ve uygulama yayımlamak için gereken çok büyük alabilirsiniz.

Çok aşamalı yapılar (Docker 17.05 ve üzeri) çizim kendi Sihirli yapmak nereden budur.

Dockerfile yürütme işlemi burada ilk görüntü bir veya daha fazla komut tarafından izlenen bir aşamayı ifade eder ve son aşamasında son görüntü boyutunu belirler. aşamada ayırabilirsiniz çekirdek olur.

Kısacası, çok aşamalı yapılar farklı "aşamaları" içindeki oluşturma bölme izin vermek ve ardından Ara aşamaları yalnızca ilgili dizinlerden alma son görüntü birleştirin. Bu özelliği kullanmak için genel stratejisidir:

1. Temel bir SDK görüntüsünü kullanın (olması fark etmez ne kadar büyük), derleme ve uygulamayı bir klasöre yayımlamak için gereken her şeyi birlikte ve ardından

2. Temel, küçük, yalnızca çalışma zamanı bir görüntüyü kullanmak ve küçük bir son görüntü üretmek için önceki aşamadan yayımlama klasörüne kopyalayın.

Büyük olasılıkla çok aşamalı bir Dockerfile içinde ayrıntılı olarak üzerinden geçiyor anlamak için en iyi yolu satır şimdi başlayın Docker'ı eklerken bir proje için destek ve bazı iyileştirmeler daha sonra alırsınız, Visual Studio tarafından oluşturulan ilk Dockerfile ile.

İlk Dockerfile aşağıdakine benzeyebilir:

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

Ve Ayrıntılar, satır satır şunlardır:

<!-- markdownlint-disable MD029-->
1. "Küçük" yalnızca çalışma zamanı temel görüntü ile bir aşama başlamak için bu çağrı **temel** başvuru.
2. Oluşturma **/app** görüntünün dizin.
3. Bağlantı noktasını kullanıma sunma **80**.
<!-- skip -->
5. "Büyük" görüntü ile yeni bir aşama oluşturma/yayımlama için başlangıç çağrısı **derleme** başvuru.
6. Dizin oluşturma **/src** görüntüde.
7. Satır en çok 16, başvurulan projeler kopyalama **.csproj** paketleri daha sonra geri yüklenmesi mümkün dosyaları gibi.
<!-- skip -->
17. Paketleri geri **Catalog.API** proje ve başvurulan proje.
18. Kopyalama **çözüm için tüm dizin ağacı** (içerdiği dosyaları veya dizinleri hariç **.dockerignore** dosya) öğesinden için **/src** görüntünün dizin.
19. Geçerli klasörü Değiştir **Catalog.API** proje.
20. Proje (ve diğer proje bağımlılıkları) oluşturun ve çıkış için **/app** görüntünün dizin.
<!-- skip -->
22. Derlemeden etmeden yeni aşama başlamak için bu çağrı **yayımlama** başvuru.
23. Proje (ve bağımlılıkları) yayımlama ve çıkış için **/app** görüntünün dizin.
<!-- skip -->
25. Gelen etmeden yeni aşama başlamak **temel** ve onu çağırmak **son**
26. Geçerli dizini **/app**
27. Kopyalama **/app** aşamadaki dizin **yayımlama** geçerli dizinde
28. Kapsayıcı başlatıldığında çalıştırılacak komut tanımlayın.
<!-- markdownlint-enable MD029-->

Artık hizmetine söz konusu olduğunda, yaklaşık 22 dakika veya daha fazla Linux kapsayıcıları tam çözümde oluşturulacak anlamına gelir, tüm işlem performansını artırmak için bazı iyileştirmeler inceleyelim.

Oldukça basittir Docker'ın katmanı önbellek özelliğin avantajlarından yararlanmak: temel görüntü ve komutlar bazı önceden yürütülmüş aynı ise, bu yalnızca gerek kalmadan elde edilen katman süre vermeyip komutları yürütmek için kullanabilirsiniz.

Bunu odaklanalım **derleme** aşama, Satır 5-6 çoğunlukla aynı, ancak satırları 7-17 farklı tek her zaman yürütmek sahip oldukları için değiştirdiyseniz her hizmetinden hizmetine, ancak 7-16 dizesine satırlar için:

```Dockerfile
COPY . .
```

Her hizmet için yalnızca aynı olacaktır sonra tüm çözüm kopyalanır ve daha büyük bir katman oluşturacak ancak:

1) Kopyalama işlemine yalnızca ilk (ve bir dosya değiştirildiğinde yeniden oluştururken) yürütülmesi ve önbelleğe diğer tüm hizmetler için kullanacağınız ve

2) Bir ara aşamasında daha büyük resmi gerçekleşir olduğundan, son görüntü boyutunu etkilemez.

Sonraki önemli iyileştirme içerir `restore` hizmetine her bir hizmet için farklı olan komut satırında 17 yürütüldü. Bu satırı yalnızca değiştirirseniz:

```Dockerfile
RUN dotnet restore
```

Tüm çözüm için paketler geri yüklenebilir, ancak daha sonra tekrar bu yalnızca bir kez geçerli stratejisi ile 15 saatleri yerine bunu.

Ancak, `dotnet restore` tek proje veya çözüm dosyası klasöründe yoksa çalıştırmaları yalnızca, bu nedenle bunu elde etmenin biraz daha karmaşıktır ve çok fazla ayrıntılarına almadan bunu çözmenin bir yolu budur:

1. Aşağıdaki satırları ekleyin **.dockerignore**:

   - `*.sln`, ana klasörü ağacında, tüm çözüm dosyaları yoksaymak için

   - `!eShopOnContainers-ServicesAndWebApps.sln`, yalnızca bu çözüm dosyası eklenecek.

2. Dahil `/ignoreprojectextensions:.dcproj` bağımsız değişkeni `dotnet restore`, bu nedenle de docker-compose proje yok sayar ve yalnızca hizmetine ServicesAndWebApps çözüm için paketler geri yükler.

Son iyileştirme için yalnızca böyle satırı 20 gereksizdir, satır olarak 23 Ayrıca uygulama oluşturur ve orada gider başka bir zaman komutu, esas olarak, sağ 20 satırın sonunda sunulur; böylece.

Sonuç dosyası ise:

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

### <a name="creating-your-base-image-from-scratch"></a>Temel görüntünüzü sıfırdan oluşturma

Kendi Docker temel görüntüsünde sıfırdan oluşturabilirsiniz. Bu senaryo için Docker ile başlayan bir kişinin önerilmez, ancak kendi temel görüntü belirli bitlerini ayarlamak istiyorsanız, bunu yapabilirsiniz.

### <a name="additional-resources"></a>Ek kaynaklar

- **.NET Core görüntüleri çok yay**. \
  <https://github.com/dotnet/announcements/issues/14>

- **Temel görüntü oluşturma**. Resmi Docker belgelerine. \
  <https://docs.docker.com/develop/develop-images/baseimages/>

![3 - dockerfile'ları tanımlanan görüntüleri oluşturma](./media/image7.png)

## <a name="step-3-create-your-custom-docker-images-and-embed-your-application-or-service-in-them"></a>Adım 3. Özel Docker görüntülerinizi oluşturmak ve uygulamanızın veya hizmetinizin bunları ekleme

Uygulamanızdaki her hizmet için ilgili görüntü oluşturmanız gerekir. Uygulamanızı bir tek bir hizmeti veya web uygulaması oluşur, tek bir görüntü yeterlidir.

Docker görüntülerini otomatik olarak sizin için Visual Studio'da oluşturulan unutmayın. Aşağıdaki adımlar yalnızca Düzenleyici/CLI iş akışı için gereken ve altında olabilecekler açıklık için açıklanmıştır.

Geliştirme ve yerel olarak bir tamamlanmış itinceye kadar test için bir geliştirici olarak, ihtiyaç duyduğunuz, özelliği veya kaynak denetim sisteminize (örneğin GitHub) değiştirin. Bu, Docker görüntüleri oluşturun ve kapsayıcıları yerel Docker konağı için (Windows veya Linux VM) dağıtın ve çalıştırın, test ve yerel kapsayıcıların karşı hata ayıklama gerektiği anlamına gelir.

Özel bir görüntü yerel ortamınızda Docker CLI ve Dockerfile'ı kullanarak oluşturmak için docker oluşturma komutu, Şekil 5-5'olduğu gibi kullanabilirsiniz.

![Bir Docker görüntüsü oluşturmak için ilerleme durumu ekranı](./media/image8.png)

**Şekil 5-5**. Özel bir Docker görüntüsü oluşturma

İsteğe bağlı olarak, docker derleme proje klasöründen doğrudan çalıştırmak yerine, önce gerekli .NET kitaplıkları ve ikili dosyaları ile dağıtılabilir bir klasör çalıştırarak oluşturabileceğiniz `dotnet publish`ve ardından `docker build` komutu.

Bu ada sahip bir Docker görüntüsü oluşturacak `cesardl/netcore-webapi-microservice-docker:first`. Bu durumda: öncelikle, belirli bir sürümü temsil eden bir etiketi olan. Oluşturulmuş Docker uygulamanız için oluşturmak için gereken her özel bir görüntü için bu adımı yineleyebilirsiniz.

Bir uygulama birden çok kapsayıcılardan yapılan ne zaman (diğer bir deyişle, çok kapsayıcılı bir uygulama olduğu), ayrıca `docker-compose up --build` ilgili docker-compose.yml dosyaları kullanıma sunulan meta verileri kullanarak tek bir komutla ilgili tüm görüntüleri oluşturmak için komutu .

Var olan görüntülerden yerel deponuzda docker'ı kullanarak görüntü komutu, Şekil 5-6'da gösterildiği gibi bulabilirsiniz.

![Ekran görünümünü görüntü komutu docker görüntüleri listeleme](./media/image9.png)

**Şekil 5-6.** Docker görüntüleri komutunu kullanarak var olan görüntüleri görüntüleme

### <a name="creating-docker-images-with-visual-studio"></a>Visual Studio ile Docker görüntüleri oluşturma

Docker desteği bir proje oluşturmak için Visual Studio kullandığınızda, bir görüntü açıkça oluşturmayın. Bastığınızda bunun yerine, görüntünün sizin için oluşturulan **F5** (veya **Ctrl-F5**) dockerized uygulamaya veya hizmete çalıştırılacak. Bu adım Visual Studio'da otomatik olarak yapılır ve durum göremezsiniz ancak neler olduğunu bilmeniz önemlidir üzerinde underneath.

![4 - (docker-compose.yml dosyası oluşturma hizmetleri isteğe bağlı)](./media/image10.png)

## <a name="step-4-define-your-services-in-docker-composeyml-when-building-a-multi-container-docker-application"></a>4. adımı. Çok kapsayıcılı Docker uygulaması oluştururken, docker-compose.yml hizmetlerinizi tanımlayın

[Docker-compose.yml](https://docs.docker.com/compose/compose-file/) dosya dağıtım komutları ile oluşturulmuş bir uygulama olarak dağıtılması için ilgili bir hizmetler kümesi tanımlamanıza olanak sağlar. Ayrıca, çalışma zamanı yapılandırma ve bağımlılık ilişkilerinin yapılandırır.

Docker-compose.yml dosyası kullanmak için aşağıdaki örnekte benzer içeriğe sahip ana dosyasında veya kök Çözüm klasörü'ı oluşturmanız gerekir:

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

Bu docker-compose.yml dosyası basit ve birleştirilmiş bir sürümüdür. Bu, her kapsayıcı (adı gibi özel görüntü), her zaman gerekli olan ve bağlantı dizesi gibi dağıtım ortamı bağımlı olabileceği yapılandırma bilgileri için statik yapılandırma verilerini içerir. Sonraki bölümlerde nasıl docker-compose.yml bölme için birden çok yapılandırma docker compose dosyaları ve geçersiz kılma değerleri (hata ayıklama veya sürüm) ortamını ve yürütme türüne bağlı olarak öğreneceksiniz.

Docker-compose.yml dosyası örneği dört hizmet tanımlar: `webmvc` hizmeti (web uygulaması), iki mikro hizmetler (`ordering.api` ve `basket.api`) ve bir veri kaynağı kapsayıcı `sql.data`olarak çalışan Linux SQL Server göre bir kapsayıcı. Her biri için gerekli bir Docker görüntüsü, bu nedenle, her hizmetin bir kapsayıcı olarak dağıtılır.

Docker-compose.yml dosyası, yalnızca kapsayıcıların ne kullanılır, ancak ayrı ayrı yapılandırmaya belirtir. Örneğin, `webmvc` kapsayıcısı tanımında .yml dosyası:

- Önceden oluşturulmuş kullanan `eshop/web:latest` görüntü. Ancak, aynı zamanda bir parçası olarak oluşturulacak görüntünün yapılandırabilirsiniz docker-compose temelli bir derleme üzerinde yürütme ek bir yapılandırma: docker-compose dosyasındaki bölümü.

- İki ortam değişkenlerini (katalog URL'si ve OrderingUrl) başlatır.

- Konak makinedeki dış bağlantı noktası 80 kapsayıcı üzerindeki 80 kullanıma sunulan bağlantı noktası iletir.

- Web uygulama kataloğu ve hizmet depends_on ayarıyla sıralama bağlantılarını içerir. Bu hizmet, bu hizmetleri yeniden başlatılana kadar beklenecek neden olur.

Mikro hizmetler ve çok kapsayıcılı uygulamalar uygulamak nasıl ele, biz bir sonraki bölümde docker-compose.yml dosyası yeniden ziyaret.

### <a name="working-with-docker-composeyml-in-visual-studio-2017"></a>Visual Studio 2017'de docker-compose.yml ile çalışma

Biz daha önce bahsedildiği gibi bir proje için bir Dockerfile eklemenin yanı sıra, Visual Studio 2017 (15,8 üzerinde) Docker Compose için orchestrator desteği bir çözüme ekleyebilirsiniz.

Kapsayıcı Düzenleyicisi desteği, ilk kez, Şekil 5-7'de gösterildiği gibi eklediğinizde Visual Studio projesi için bir Dockerfile ve yeni bir (hizmet bölümü) projesi çözümünüzdeki birkaç ile genel oluşturur `docker-compose*.yml` dosyaları ve ekler Bu dosyalar için proje. Docker-compose.yml dosyaları açmak ve bunları ek özellikler ile güncelleştirin.

Bu işlem formu docker-compose.yml dosyasında dahil etmek istediğiniz her proje yinelemek zorunda.

Bu makalenin yazıldığı sırada, Visual Studio, Docker Compose ve Service Fabric düzenleyicileri destekler.

![Bir ASP.NET Core projesi için orchestrator desteği eklemek için bağlam menüsü seçeneği](./media/image21.png)

**Şekil 5-7**. Bir ASP.NET Core projesi sağ tıklayarak Visual Studio 2017'de Docker desteği ekleme

Visual Studio çözümünüzde Düzenleyicisi desteği ekledikten sonra yeni bir düğüm ayrıca görürsünüz (içinde `docker-compose.dcproj` proje dosyası) Çözüm Gezgini'nde, Şekil 5-8'de gösterildiği gibi eklenen docker-compose.yml dosyaları içerir.

![Çözüm Gezgininde docker-compose](./media/image11.png)

**Şekil 5-8**. **Docker-compose** Visual Studio 2017 Çözüm Gezgini'nde eklenen ağaç düğümü

Kullanarak bir docker-compose.yml dosyası ile çok kapsayıcılı bir uygulama dağıtabilirsiniz `docker-compose up` komutu. Ancak, ortam (geliştirme veya üretim) ve yürütme türü (yayınlama veya hata ayıklama) bağlı olarak değerleri geçersiz kılmak için Visual Studio bunları grubu ekler. Bu özellik, sonraki bölümlerde açıklanacaktır.

![5 - kapsayıcıları çalıştırmak veya uygulama oluşur](./media/image12.png)

## <a name="step-5-build-and-run-your-docker-application"></a>5. adımı. Kendi Docker uygulaması derleme ve çalıştırma

Uygulamanız yalnızca tek bir kapsayıcıya sahip değilse, Docker Konağı (VM veya fiziksel sunucu) dağıtarak çalıştırabilirsiniz. Uygulamanız birden fazla hizmet içeriyor, ancak bunu oluşan bir uygulama olarak ya da tek bir CLI komutu kullanarak dağıtabilirsiniz (docker-compose ayarlama), veya Visual Studio ile bu komut aslında altında kullanacak. Farklı seçenekleri göz atalım.

### <a name="option-a-running-a-single-container-application"></a>Seçenek A: Tek kapsayıcı uygulaması çalıştırma

#### <a name="using-docker-cli"></a>Docker CLI kullanma

Kullanarak bir Docker kapsayıcısı çalıştırabilirsiniz `docker run` Şekil 5-9'da gösterildiği gibi komut:

```console
  docker run -t -d -p 80:5000 cesardl/netcore-webapi-microservice-docker:first
```

Yukarıdaki komutu her çalıştırıldığında yeni bir kapsayıcı örneği belirtilen görüntüden oluşturacaksınız. Kullanabileceğiniz `--name` kapsayıcıya bir ad verin ve ardından parametre `docker start {name}` (veya kapsayıcı kimliği veya otomatik adı kullanın) var olan bir kapsayıcı örneği çalıştırmak için.

![Docker kullanarak Docker kapsayıcı çalışırken ekran görünümünü komutunu çalıştırın](./media/image13.png)

**Şekil 5-9**. Komutu çalıştırarak docker kullanarak Docker kapsayıcı çalıştırma

Bu durumda, komut kapsayıcının iç bağlantı noktası 5000 ana makinenin 80 numaralı bağlantı noktasına bağlar. Bu konak 80 numaralı bağlantı noktasında dinleme ve kapsayıcıda genericread 5000 numaralı bağlantı noktasına ileten anlamına gelir.

Gösterilen karma kapsayıcı kimliği olduğunu ve bunu ayrıca bir rastgele okunabilir ad varsa atadığı `--name` seçeneği kullanılamıyor.

#### <a name="using-visual-studio"></a>Visual Studio kullanarak

Kapsayıcı Düzenleyicisi desteği eklemediyseniz, ayrıca bir çoklu kapsayıcı uygulaması Visual Studio'da tuşlarına basarak çalıştırabileceğiniz **Ctrl-F5** ve ayrıca **F5** uygulama kapsayıcı içinde hata ayıklamak için. Kapsayıcı, docker run kullanarak yerel olarak çalışır.

### <a name="option-b-running-a-multi-container-application"></a>Seçenek B: Çok kapsayıcılı bir uygulama çalıştırma

Çoğu Kurumsal senaryolarda, Docker uygulaması birden çok Hizmetleri, Şekil 5-10'da gösterildiği gibi çok kapsayıcılı bir uygulama çalıştırmak gereken yani oluşacaktır.

![VM birkaç Docker kapsayıcıları ile](./media/image14.png)

**Şekil 5-10**. Dağıtılmış Docker kapsayıcıları ile VM

#### <a name="using-docker-cli"></a>Docker CLI kullanma

Docker CLI ile çok kapsayıcılı bir uygulama çalıştırmak için kullandığınız `docker-compose up` komutu. Bu komut **docker-compose.yml** çok kapsayıcılı bir uygulama dağıtmak için çözüm düzeyinde sahip dosya. Şekil 5-11 komut docker-compose.yml dosyasını içeren ana çözüm dizinden çalıştırılırken sonuçları gösterilmektedir.

![Ekran görünümünü çalıştırırken docker-compose komutu](./media/image15.png)

**Şekil 5-11**. Örnek sonuçları çalıştırırken docker-compose komutu

Sonra docker-compose komutu çalıştırmaları, uygulama ve onun ilişkili kapsayıcılar, Docker konağı Şekil 5-10'da görüldüğü gibi dağıtılır.

#### <a name="using-visual-studio"></a>Visual Studio kullanarak

Visual Studio 2017'yi kullanarak çok kapsayıcılı bir uygulama çalıştıran any daha basit alınamıyor. Yalnızca tuşuna **Ctrl-F5** çalıştırmak için veya **F5** hata ayıklama, ayarlama gibi normal **docker-compose** projeyi başlangıç projesi olarak.  Visual Studio, kesme noktaları zamanki gibi oluşturabilir ve ne gibi "uzak sunucular", yalnızca çalışan bağımsız işlemler son haline hata ayıklama için tüm gerekli Kurulum işler.

Her bir çözüm içinde bir proje için Docker çözüm desteğini eklemeden önce belirtildiği gibi proje çalıştırın veya çözümün tamamının aynı anda hata ayıklama olanak sağlayan genel (Çözüm düzeyinde) docker-compose.yml dosyasında yapılandırılır. Visual Studio Docker çözümü desteği etkin olan her proje için bir kapsayıcı başlatın ve iç tüm adımları gerçekleştirdiğiniz (dotnet yayımlama, docker derleme, vs.).

Bir Özet drudgery hiç katılmak istiyorsanız, dosyaya göz atın:

`{root solution folder}\obj\Docker\docker-compose.vs.debug.g.yml`

Burada önemli olan nokta Şekil 5-12'de gösterildiği gibi Visual Studio 2017'de, ek bir yoktur **Docker** F5 anahtar eylemi için komutu. Bu seçenek çalıştırın ya da docker-compose.yml dosyaları çözüm düzeyinde tanımlanan tüm kapsayıcıları çalıştırarak çok kapsayıcılı bir uygulama hata ayıklama sağlar. Birden çok kapsayıcı çözümleri hata ayıklama özelliği (kapsayıcı) farklı bir projede birkaç kesme noktaları, her bir kesme noktası ayarlayın ve Visual Studio'dan hata ayıklama sırasında farklı projelerde tanımlanan ve çalıştırılan kesme noktalarında durdurur anlamına gelir. farklı kapsayıcılar.

![Proje visual Studio hata ayıklama araç çalışan docker-compose](./media/image16.png)

**Şekil 5-12**. Visual Studio 2017'de çalışan çok kapsayıcılı uygulamalar

### <a name="additional-resources"></a>Ek kaynaklar

- **ASP.NET kapsayıcısını uzak Docker konağı için dağıtma** \
  <https://docs.microsoft.com/azure/vs-azure-tools-docker-hosting-web-apps-in-docker>

### <a name="a-note-about-testing-and-deploying-with-orchestrators"></a>Test etme ve dağıtma düzenleyicilerle hakkında bir Not

Docker compose up ve docker run komutları (veya çalışan ve kapsayıcıları Visual Studio'da hata ayıklama) kapsayıcıları geliştirme ortamınızda test etmek için yeterli. Ancak burada hedef gibi düzenleyicileri, üretim dağıtımları için bu yaklaşım kullanmamalısınız [Kubernetes](https://kubernetes.io/) veya [Service Fabric](https://azure.microsoft.com/services/service-fabric/). Kubernetes kullanıyorsanız kullanmak zorunda [pod'ların](https://kubernetes.io/docs/concepts/workloads/pods/pod/) kapsayıcıları düzenlemek için ve [Hizmetleri](https://kubernetes.io/docs/concepts/services-networking/service/) bunları ağ. Ayrıca [dağıtımları](https://kubernetes.io/docs/concepts/workloads/controllers/deployment/) pod oluşturulmasını ve değiştirilmesini düzenlemek için.

![6 - uygulamanızı veya mikro Hizmetleri test etme](./media/image17.png)

## <a name="step-6-test-your-docker-application-using-your-local-docker-host"></a>6. adım. Kullanarak yerel bir Docker ana bilgisayarınızda Docker uygulamanızı test edin

Bu adım, uygulamanızın yapılması bağlı olarak değişir. Tek kapsayıcı veya hizmet olarak dağıtılan bir basit .NET Core Web uygulamasında, Docker konağı üzerinde bir tarayıcı açıp bu siteye gezinme, Şekil 5-13'te gösterildiği gibi hizmete erişebilir. (Dockerfile içinde yapılandırma kapsayıcı 80 dışında her şey, konağa bağlantı noktasına eşler. ana bilgisayar bağlantı noktası URL'ye dahil edin.)

![Bir API uç noktası yanıtının tarayıcı görünümü](./media/image18.png)

**Şekil 5-13**. Örneği yerel olarak localhost kullanarak Docker uygulamanızı test etme

Docker için localhost işaret etmiyorsa IP ana bilgisayar (Bu varsayılan Docker CE kullanırken, gerekir), hizmetinize gidin ve makinenizin Ağ kartının IP adresini kullanın.

Bu URL tarayıcıda tartışılan belirli bir kapsayıcı örneği için 80 numaralı bağlantı noktasını kullandığını unutmayın. Nasıl bu komutu çalıştırın: docker ile bir önceki adımda açıklandığı gibi dağıtılmış olduğu için ancak, dahili olarak istekleri 5000, bağlantı noktası için Rehbere yönlendiriliyorsunuz.

Ayrıca, Şekil 5-14'te gösterildiği gibi terminalden curl kullanarak uygulamayı test edebilirsiniz. Bir Docker yüklemesinde Windows üzerindeki Docker ana bilgisayar IP her zaman 10.0.75.1 makinenizin gerçek IP adresinin yanı sıra varsayılandır.

![Curl ile bir API uç noktası yanıtının ekran görünümü](./media/image19.png)

**Şekil 5-14**. Docker uygulamanızı yerel olarak curl kullanarak test etme örneği

### <a name="testing-and-debugging-containers-with-visual-studio-2017"></a>Test ve hata ayıklama Visual Studio 2017 ile kapsayıcıları

Çalışan kapsayıcılar, olduğu gibi çalışan kapsayıcılar Visual Studio 2017 ile hata ayıklama, .NET uygulama kadar aynı şekilde ayıklayabilirsiniz.

### <a name="testing-and-debugging-without-visual-studio"></a>Test ve hata ayıklama Visual Studio

Düzenleyici/CLI yaklaşımı kullanarak geliştiriyorsanız kapsayıcılarında hata ayıklama daha zordur ve izlemeleri oluşturarak hata ayıklama isteyeceksiniz.

### <a name="additional-resources"></a>Ek kaynaklar

- **Yerel bir Docker kapsayıcısı uygulamalarında hata ayıklama** \
  [https://docs.microsoft.com/visualstudio/containers/edit-and-refresh](/visualstudio/containers/edit-and-refresh)

- **Steve Lasker. Derleme, hata ayıklama, Docker ile ASP.NET Core uygulamaları dağıtın.** Video. \
  <https://channel9.msdn.com/Events/Visual-Studio/Visual-Studio-2017-Launch/T115>

## <a name="simplified-workflow-when-developing-containers-with-visual-studio"></a>Visual Studio ile kapsayıcıları geliştirirken basitleştirilmiş bir iş akışı

Etkili bir şekilde, Visual Studio kullanarak iş akışı Düzenleyicisi'ni / CLI yaklaşımı kullanırsanız, çok daha kolay olacaktır. Docker tarafından gerekli adımların çoğu için Dockerfile ilgili ve gizli ya da Visual Studio tarafından Şekil 5-15'te gösterildiği gibi Basitleştirilmiş docker-compose.yml dosyaları.

![Visual Studio ile Basitleştirilmiş kapsayıcı geliştirme iş akışı: 1 - 2 - Docker ekleme desteği projelerine (yalnızca bir kez), 3 - çalışma kapsayıcı ya da docker uygulama kodu-uygulama oluşturma, 4 - Test uygulama veya mikro hizmetler, 5 - anında iletme depo ve yineleyin.](./media/image20.png)

**Şekil 5-15**. Visual Studio ile geliştirirken basitleştirilmiş bir iş akışı

Ayrıca, yalnızca bir kez (Docker desteği ekleme projelerinize) 2. adım gerçekleştirmeniz gerekir. Bu nedenle, iş akışı herhangi bir geliştirme için .NET kullanarak normal geliştirme görevlerine benzer şekildedir. Kapsar (görüntü oluşturma işlemi, hangi kullandığınız temel görüntüleri, kapsayıcılar, vb. dağıtımını) altında ve bazen de davranışları özelleştirmek için Dockerfile veya docker-compose.yml dosyasını düzenlemeniz gerekir neler olduğunu bilmeniz gerekir. Ancak işin çoğunu, çok daha üretken hale Visual Studio kullanılarak büyük ölçüde basitleştirilir.

### <a name="additional-resources"></a>Ek kaynaklar

- **Steve Lasker. Visual Studio 2017 ile .NET docker geliştirme** \
  <https://channel9.msdn.com/Events/Visual-Studio/Visual-Studio-2017-Launch/T111>

## <a name="using-powershell-commands-in-a-dockerfile-to-set-up-windows-containers"></a>Windows kapsayıcıları ayarlamak için bir Dockerfile içinde PowerShell komutlarını kullanarak

[Windows kapsayıcıları](https://docs.microsoft.com/virtualization/windowscontainers/about/index) mevcut Windows uygulamalarınızı Docker görüntüleri olarak dönüştürmek ve Docker ekosistemi sayesinde geri kalanı gibi aynı araçları ile dağıtmaya olanak sağlar. Windows kapsayıcıları kullanmak için aşağıdaki örnekte gösterildiği gibi bir Dockerfile içinde PowerShell komutlarını çalıştırın:

```Dockerfile
FROM microsoft/windowsservercore
LABEL Description="IIS" Vendor="Microsoft" Version="10"
RUN powershell -Command Add-WindowsFeature Web-Server
CMD [ "ping", "localhost", "-t" ]
```

Bu durumda, biz bir Windows Server Core temel görüntüyü (FROM ayar) kullanarak ve bir (çalışma ayarı) PowerShell komutuyla IIS'yi yükleme. Benzer şekilde, ASP.NET 4.x, .NET 4.6 veya herhangi bir Windows yazılımı gibi ek bileşenler ayarlamak için PowerShell komutlarını kullanabilirsiniz. Örneğin, aşağıdaki komut bir Dockerfile içinde ASP.NET 4.5 ' ayarlar:

```Dockerfile
RUN powershell add-windowsfeature web-asp-net45
```

### <a name="additional-resources"></a>Ek kaynaklar

- **aspnet-docker/Dockerfile.** Windows özellikleri içerecek şekilde dockerfile'ları için örnek PowerShell komutları. \
  <https://github.com/Microsoft/aspnet-docker/blob/master/4.7.1-windowsservercore-ltsc2016/runtime/Dockerfile>

>[!div class="step-by-step"]
>[Önceki](index.md)
>[İleri](../multi-container-microservice-net-applications/index.md)
