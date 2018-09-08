---
title: Tek kapsayıcı dağıtma .NET Core Web uygulamaları Linux veya Windows Nano sunucu konaklarına göre
description: Kapsayıcılı .NET uygulamaları için .NET mikro hizmet mimarisi | Tek kapsayıcı dağıtma .NET Core Web uygulamaları Linux veya Windows Nano sunucu konaklarına göre
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 06/27/2018
ms.openlocfilehash: 45be99a86a52ed450b795ca5f91c01ab82c7da47
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2018
ms.locfileid: "44197361"
---
# <a name="deploying-single-container-based-net-core-web-applications-on-linux-or-windows-nano-server-hosts"></a>Linux veya Windows Nano sunucu konaklarına tek kapsayıcı tabanlı .NET Core Web uygulamaları dağıtma

_Docker kapsayıcıları tek parça daha basit web uygulamaları dağıtımını için kullanabilirsiniz. Bu artırır sürekli tümleştirme ve sürekli dağıtım işlem hatları ve üretim için dağıtım başarı elde etmenize yardımcı olur. Daha fazla "neden üretimde çalışmaz makineme çalışır?"_

Bir mikro hizmet tabanlı mimariye pek çok faydası vardır, ancak bu avantajlar bulunan artan karmaşıklık bedeli. Bazı durumlarda, maliyetleri ağır basıyor ve bir veya birkaç kapsayıcılarda çalıştırılan bir tek parçalı dağıtım uygulaması daha iyi bir seçenektir.

Tek parça bir uygulamayı kolayca iyi ayrılmış mikro hizmetler halinde decomposable olmayabilir. Bu mikro işlevi tarafından bölümlendirilmelidir öğrendiniz: karşı daha dayanıklı bir uygulama sağlamak için birbirinden çalışması gerekir. Uygulamanın özellik dilimleri teslim edilemiyor, bu ayırma karmaşıklık yalnızca ekler.

Bir uygulama, özelliklerin bağımsız olarak ölçeklendirme henüz gerekmeyebilir. Erken aşamalarında varsayalım, `eShopOnContainers` başvuru uygulaması, trafik farklı mikro hizmetler halinde özellikleri ayırma Yasla alamadık. Trafiği bir hizmet için kaynak ekleme, genellikle tüm hizmetler için kaynak ekleme geliyordu kadar küçük. Ayrık Hizmetleri uygulamasına ayırmak için ek iş en az bir avantaj sağladı.

Ayrıca, bir uygulamanın erken geliştirme, dair NET bir fikir doğal işlevsel sınırları nerede sahip olmayabilir. En düşük uygun bir ürün geliştirirken, doğal ayrımı henüz çıkmıştır değil.

Bu koşullar bazıları geçici olabilir. Tek parça bir uygulamayı oluşturun ve daha sonra bazı özellikleri geliştirilen ve mikro hizmet dağıtılan ayrı. Diğer koşullar, uygulamanın birden fazla mikro hizmetler halinde hiçbir zaman bozuk durumda, yani, uygulamanın sorun alanı için gerekli olabilir.

Bir uygulamaya birçok ayrı işlemler ayırma yükü tanıtır. Özellikler farklı işlemlere ayırmak daha karmaşık yoktur. İletişim protokolleri, daha karmaşık hale gelir. Yerine yöntem çağrılarını, hizmetler arasında zaman uyumsuz iletişim kullanmanız gerekir. Bir mikro hizmet mimarisi için taşırken, mikro hizmetler sürümünde yapılan yapı taşlarını birçoğu eklemenize gerek `eShopOnContainers` uygulama: olay veri yolu işleme, ileti dayanıklılık ve yeniden denemeler, nihai tutarlılığa kadar giden ve daha fazla.

Hizmetine daha basitleştirilmiş bir sürümünü (adlı [eShopWeb](https://github.com/dotnet-architecture/eShopOnContainers/tree/master/src/Web/WebMonolithic) ve aynı GitHub deposunda dahil) tek parça bir MVC uygulaması çalışır. Açıklandığı gibi bu tasarım seçiminin tarafından sunulan avantajları vardır. Bu uygulama kaynağını Github'dan indirip yerel olarak çalıştırın. Tek parça bu uygulama bir kapsayıcı ortamında dağıtılan fayda sağlar.

Biri için kapsayıcı dağıtımı uygulamanın her örneği aynı ortamda çalıştığı anlamına gelir. Bu, burada erken test ve geliştirme gerçekleşmesi Geliştirici ortamı içerir. Geliştirme ekibi, uygulamayı üretim ortamına eşleşen bir kapsayıcı ortamında çalıştırabilirsiniz.

Ayrıca, kapsayıcılı uygulamaların ölçeklendirme daha düşük maliyetle. Daha önce bahsettiğim gibi kapsayıcı ortamınızı geleneksel VM ortamları paylaşımı büyük kaynak sağlar.

Son olarak, ASP.NET'in, iş mantığı ve depolama sunucusu arasında bir ayrım zorlar. Uygulama Ölçeklendirmesi eşitlenene gibi çeşitli kapsayıcıları tek bir fiziksel depolama bir ortamda tüm güvenirsiniz. Bu depolama genelde bir SQL Server veritabanı çalıştıran bir yüksek kullanılabilirlik sunucusu olacaktır.

## <a name="application-tour"></a>Uygulama turu

[EShopWeb](https://github.com/dotnet-architecture/eShopOnContainers/tree/master/src/Web/WebMonolithic) bazı tek parça bir uygulamayı çalıştıran hizmetine uygulama uygulamasını temsil eder: .NET Core üzerinde çalışan bir ASP.NET Core MVC tabanlı uygulama. Esas olarak, önceki bölümlerde açıklandığı gibi göz atma özellikleri Kataloğu sağlar.

Uygulama Kataloğu depolama alanı için bir SQL Server veritabanını kullanır. Kapsayıcı tabanlı dağıtımlarda, bu tek parça bir uygulamayı mikro hizmet tabanlı uygulama aynı veri deposuna erişebilirsiniz. Uygulama, bir kapsayıcıdaki tek parça bir uygulamayı yanı sıra SQL Server çalıştırmak için yapılandırılmıştır. Bir üretim ortamında, SQL Server, Docker konağının dışında bir yüksek kullanılabilirlik makinede çalıştırılır. Geliştirme veya test ortamında, kolaylık sağlamak için SQL Server kendi kapsayıcısında çalıştırılması önerilir.

Yalnızca ilk özelliği, katalog taramayı etkinleştirir. Güncelleştirmeleri kapsayıcılı uygulama tüm özellik kümesini etkinleştirir. Tek parça bir web uygulaması mimarisi daha gelişmiş bir açıklanan [ASP.NET Web uygulaması mimarisi yöntemler](https://aka.ms/webappebook) e-kitap ve ilgili [eShopOnWeb örnek uygulama](https://aka.ms/WebAppArchitecture).

## <a name="docker-support"></a>Docker desteği

EShopOnWeb proje .NET Core üzerinde çalışır. Linux tabanlı veya Windows tabanlı kapsayıcılarda çalıştırabilirsiniz anlamına gelir. Aynı ana bilgisayar türü için SQL Server kullanmak istediğiniz bir dağıtım için Docker unutmayın. Linux tabanlı kapsayıcılar bir daha küçük kaplama alanı izin ve tercih edilir.

Visual Studio için Docker desteği ekleyen bir çözüme bir proje şablonu sağlar. Projeye sağ tıklayın, tıklayın **Ekle** ardından **Docker desteği**. Projenizi ve yeni bir şablon bir Dockerfile ekler **docker-compose** bir Başlatıcısı sağlayan proje *docker-compose.yml* dosya. Bu adım, Github'dan indirilen eShopOnWeb projede zaten yapılmıştır. Çözüm içerdiğini görebilirsiniz **eShopOnWeb** proje ve **docker-compose** proje Şekil 6-1'de gösterildiği gibi.

![](./media/image1.png)

**Şekil 6-1**. **Docker-compose** tek kapsayıcı web uygulaması projesinde

Bu dosyalar standart docker-compose dosyası, herhangi bir Docker projesi ile tutarlı. Bunları, Visual Studio ile veya komut satırından kullanabilirsiniz. Bu uygulama, .NET Core üzerinde çalışır ve Linux kapsayıcıları kullanır. Bu nedenle, kod, derleme da bir Mac veya Linux makine üzerinde çalıştırın.

*Docker-compose.yml* dosya ne oluşturmak için görüntüler ve başlatmak için hangi kapsayıcıları hakkında bilgiler içerir. Şablonları nasıl oluşturulacağını belirtin `eshopweb` görüntü ve uygulamanın kapsayıcılar'ı başlatın. Görüntü ekleyerek SQL Server'da bağımlılık eklemeniz gerekir (örneğin, `mssql-server-linux`) ve bir hizmet oluşturmak ve bu kapsayıcısı başlatmak Docker için sql.data görüntüsü. Bu ayarlar, aşağıdaki örnekte gösterilmiştir:

```yml
version: '2'

services:
  eshopweb:
    image: eshop/web
    build:
    context: ./eShopWeb
    dockerfile: Dockerfile
    depends_on:
      - sql.data

  sql.data:
    image: microsoft/mssql-server-linux
```

`depends_on` Yönergesi Docker eShopWeb görüntü sql.data görüntüye bağlı olduğunu bildirir. Aşağıdaki satırları `depends_on` etiketli bir görüntüsünü oluşturmak için yönergeler `sql.data` kullanarak `microsoft/mssql-server-linux` görüntü.

**Docker-compose** proje ana altındaki diğer docker-compose dosyaları görüntüler *docker-compose.yml* düğümü bu dosyaların ilişkili olduğunu görsel bir gösterge sağlar. *Docker compose override.yml* dosya bağlantı dizelerini ve diğer uygulama ayarları gibi her iki hizmet ayarlarını içerir.

Aşağıdaki örnekte gösterildiği *docker compose.vs.debug.yml* dosyasını Visual Studio'da hata ayıklama için kullanılan ayarları içerir. Bu dosyada, kendisine eklenmiş geliştirme etiketi eshopweb görüntü sahiptir. Böylece hata ayıklama bilgileri yanlışlıkla bir üretim ortamına dağıtmanıza gerek yoktur, sürüm görüntülerden ayrı hata ayıklama yardımcı olur:

```yml
version: '2'

services:
  eshopweb:
    image: eshop/web:dev
    build:
    args:
    source: ${DOCKER_BUILD_SOURCE}
    environment:
      - DOTNET_USE_POLLING_FILE_WATCHER=1
    volumes:
      - ./eShopWeb:/app
      - ~/.nuget/packages:/root/.nuget/packages:ro
      - ~/clrdbg:/clrdbg:ro
    entrypoint: tail -f /dev/null
    labels:
      - "com.microsoft.visualstudio.targetoperatingsystem=linux"
```

Eklenen son dosya *docker-compose.ci.build.yml*. Komut satırından bu dosya bir CI sunucudan projeyi oluşturmak için kullanılır. Bu compose dosyasının, uygulamanız için gereken bir görüntü oluşturur bir Docker kapsayıcısı başlatır. Aşağıdaki örnek, içeriğini gösterir *docker-compose.ci.build.yml* dosyası:

```yml
version: '2'

services:
  ci-build:
    image: microsoft/aspnetcore-build:latest
    volumes:
      - .:/src
    working_dir: /src
  command: /bin/bash -c "dotnet restore ./eShopWeb.sln && dotnet publish  ./eShopWeb.sln -c Release -o ./obj/Docker/publish"
```

> [!NOTE]
> .NET Core SDK 2.0 ile başlayarak [dotnet restore](../../../core/tools/dotnet-restore.md) komutu yürütür otomatik olarak zaman [dotnet yayımlama](../../../core/tools/dotnet-publish.md) yürütülür.

Görüntünün bir ASP.NET Core derleme görüntü olduğuna dikkat edin. Bu görüntüyü, uygulamanızı yapılandırmak ve gerekli görüntüleri oluşturmak için SDK'sı ve derleme araçları içerir. Çalışan **docker-compose** proje bu dosyayı kullanan derleme kapsayıcı görüntüsünden başlatılır ve ardından kapsayıcıdaki uygulamanızın görüntü oluşturur. Belirttiğiniz *docker-compose* uygulamanızı bir Docker kapsayıcısında oluşturun ve ardından başlatmak için komut satırının bir parçası olarak dosya.

Visual Studio'da seçerek uygulamanızı Docker kapsayıcılarında çalıştırabilirsiniz **docker-compose** projesini başlangıç projesi olarak ve ardından (hata ayıklamak için F5), Ctrl + F5 tuşlarına basarak herhangi bir uygulama ile yapabildiğiniz gibi. Başladığınızda **docker-compose** proje, Visual Studio çalıştırmaları **docker-compose** kullanarak *docker-compose.yml* dosyası  *docker-compose.override.yml* dosyası ve bir docker-compose.vs.\* dosyaları. Uygulama başlatıldıktan sonra Visual Studio tarayıcı başlatılır.

Visual Studio hata ayıklayıcı uygulamasını başlatın, Docker uygulama çalışırken ekler.

## <a name="troubleshooting"></a>Sorun giderme

Bu bölümde ortaya çıkabilecek bazı sorunlar açıklanmaktadır, yerel olarak çalıştırma kapsayıcılarınızı ve bazı düzeltmeler önerir.

### <a name="stop-docker-containers"></a>Docker kapsayıcıları Durdur

Kapsayıcılı uygulama başlattıktan sonra kapsayıcıları bile hata ayıklama durdurduktan sonra çalışmaya devam edin. Çalıştırabileceğiniz `docker ps` çalışan kapsayıcıları görmek için komut satırından komutu. `docker stop` Komut Şekil 6-2'de gösterildiği gibi bir çalışan kapsayıcıya durdurur.

![](./media/image2.png)

**Şekil 6-2**. Listeleme ve kapsayıcılar docker ps ve docker durdurma CLI komutları ile durduruluyor

Çalışan işlemleri farklı yapılandırmalar arasında geçiş yaptığınızda durdurmanız gerekebilir. Aksi takdirde, web uygulamasını çalıştıran kapsayıcıyı uygulamanız için bağlantı noktasını kullanıyorsa (Bu örnekte 5106).

### <a name="add-docker-to-your-projects"></a>Docker, projenize ekleyin.

Docker desteği ekler Sihirbazı çalışan Docker işlemi ile iletişim kurar. Sihirbazı başlattığınızda Docker çalışmıyorsa, sihirbaz düzgün çalışmıyor. Sihirbazın geçerli kapsayıcı seçiminizi doğru Docker desteği Ekle inceler. Windows kapsayıcıları için destek eklemek için Windows yapılandırılmış kapsayıcılarla çalışan Docker varken Sihirbazı'nı çalıştırın. Linux kapsayıcıları için destek eklemek üzere yapılandırılmış Linux kapsayıcıları ile çalışan Docker varken Sihirbazı'nı çalıştırın.

>[!div class="step-by-step"]
[Önceki](../docker-application-development-process/docker-app-development-workflow.md)
[İleri](../containerize-net-framework-applications/index.md)
