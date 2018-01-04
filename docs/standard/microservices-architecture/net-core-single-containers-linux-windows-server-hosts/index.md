---
title: "Tek kapsayıcı dağıtma .NET Core Web uygulamaları Linux veya Windows Nano Server konakları göre"
description: "Kapsayıcılı .NET uygulamaları için .NET mikro mimarisi | Tek kapsayıcı dağıtma .NET Core Web uygulamaları Linux veya Windows Nano Server konakları göre"
keywords: "Docker, mikro, ASP.NET, kapsayıcı"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: f85b3db6b4ca6d22c4b855c8b96051c1c31350a6
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="deploying-single-container-based-net-core-web-applications-on-linux-or-windows-nano-server-hosts"></a>Linux veya Windows Nano Server konakları tek kapsayıcı tabanlı .NET Core Web uygulamalarını dağıtma

*Docker kapsayıcıları tek yapılı daha basit web uygulamalarının dağıtımını için kullanabilirsiniz. Bu, sürekli tümleştirme artırır ve sürekli dağıtımı ardışık düzenleri ve dağıtım üretim başarılı olmasına yardımcı olur. Daha fazla "Makinem içinde çalışır neden üretimde çalışmıyor?"*

Mikro tabanlı bir mimari için birçok fayda olsa da, bu avantajlar artan karmaşıklık maliyetlerine gelir. Bazı durumlarda, maliyetleri ağır basıyor ve, tek bir kapsayıcı veya yalnızca birkaç kapsayıcıları çalıştıran bir tek yapılı dağıtım uygulama ile daha iyi sunulacak. 

Tek yapılı bir uygulama içinde iyi ayrılmış mikro kolayca decomposable olmayabilir. Bu işlev tarafından bölümlenmesi öğrendiniz: mikro birbirinden bağımsız olarak daha esnektir uygulaması sağlamak için çalışmalıdır. Uygulamanın özellik dilimler gönderemez, onu ayırarak karmaşıklık yalnızca ekler.

Bir uygulama, henüz özellikleri bağımsız olarak ölçeklendirebilirsiniz gerekmeyebilir. Şimdi erken ömrünü bizim eShopOnContainers başvuru uygulaması, trafiği özellikleri farklı mikro ayırarak justify değil olduğunu varsayalım. Trafik kaynakları için bir hizmet genellikle ekleme kaynakları tüm hizmetlere ekleme amacı yetecek kadar küçük. Ayrık Hizmetleri uygulamasına ayırmak için ek iş en az avantajı sağlanır.

Ayrıca, erken bir uygulama geliştirmede, dair NET bir fikir doğal işlevsel sınırları nerede sahip olmayabilir. En az bir anlamlı ürün geliştirdikçe doğal ayrımı henüz çıkmıştır değil.

Bu koşullar bazıları geçici olabilir. Tek yapılı bir uygulama oluşturun ve daha sonra geliştirilen ve mikro hizmetler dağıtılan için bazı özellikler ayrı. Diğer koşullar uygulama içinde birden çok mikro hiçbir zaman bozuk, yani uygulamanın sorun alanı için önemli olabilir.

Bir uygulamaya birçok ayrı işlemler ayırarak ek yükü tanıtır. Özellikler farklı işlemlere ayırmak daha karmaşık yoktur. İletişim protokolleri daha karmaşık hale gelir. Yöntem çağrıları yerine Hizmetleri arasındaki zaman uyumsuz iletişim kullanmanız gerekir. Mikro mimarisi için ilerlerken, birçok eShopOnContainers uygulama mikro sürümünde yapı taşları eklemeniz gerekir: olay bus işleme, ileti dayanıklılık ve yeniden deneme, nihai tutarlılık ve daha fazla.

EShopOnContainers daha basitleştirilmiş bir sürümünü (adlı [eShopWeb](https://github.com/dotnet-architecture/eShopOnContainers/tree/master/src/Web/WebMonolithic) ve aynı GitHub depo dahil) çalışır ve olarak yalnızca tek yapılı bir MVC uygulaması olarak açıklandığı gibi bu tasarım seçiminin tarafından sunulan avantajı vardır. Bu uygulama için kaynak Github'dan indirin ve yerel olarak çalıştırın. Tek yapılı bu uygulama, bir kapsayıcı ortamında dağıtılan fayda sağlar.

Birincisi, kapsayıcılı dağıtım uygulama her örneğini aynı ortamda çalıştırır anlamına gelir. Bu, burada erken test ve geliştirme gerçekleşmesi Geliştirici ortamı içerir. Geliştirme ekibi uygulamayı üretim ortamına eşleşen kapsayıcılı bir ortamda çalıştırabilirsiniz.

Ayrıca, daha düşük maliyetle uygulamaları ölçeklendirme kapsayıcılı. Daha önce gördüğünüz gibi geleneksel VM ortamlarında paylaşımı büyük kaynak kapsayıcı ortamı sağlar.

Son olarak, uygulama containerizing iş mantığı ve depolama sunucusu arasında ayrım zorlar. Uygulamanın çıkışı ölçeklendirir gibi birden çok kapsayıcı tüm tek bir fiziksel depolama bir ortamda kullanır. Bu, genellikle bir SQL Server veritabanını çalıştıran bir yüksek oranda kullanılabilirlik sunucusu olacaktır.

## <a name="application-tour"></a>Uygulama turu

[EShopWeb](https://github.com/dotnet-architecture/eShopOnContainers/tree/master/src/Web/WebMonolithic) tek yapılı bir uygulama olarak çalışan eShopOnContainers uygulama bazıları uygulamasını temsil eder — .NET Core üzerinde çalışan bir ASP.NET Core göre MVC uygulama. Esas olarak, biz önceki bölümlerde açıklanan özellikleri gözatma Kataloğu sağlar.

Uygulama Kataloğu depolama için bir SQL Server veritabanını kullanır. Kapsayıcı tabanlı dağıtımlarda, bu tek yapılı uygulaması aynı veri deposu mikro tabanlı bir uygulama olarak erişebilir. Uygulama, SQL Server tek yapılı uygulama yanında bir kapsayıcıda çalıştırmak için yapılandırılır. Bir üretim ortamında, SQL Server Docker ana bilgisayar dışında bir yüksek kullanılabilirlik makine üzerinde çalışır. Bir geliştirme veya test ortamına kolaylık olması için kendi kapsayıcısında SQL Server çalıştıran öneririz.

Yalnızca ilk özellik katalog taramayı etkinleştirir. Güncelleştirmeleri kapsayıcılı uygulamanın tam özellik kümesini etkinleştirir. Tek yapılı web uygulama mimarisi daha gelişmiş bir açıklanan [ASP.NET Web uygulaması mimarisi yöntemler](https://aka.ms/webappebook) e-kitap ve ilgili [eShopOnWeb örnek uygulama](http://aka.ms/WebAppArchitecture), ancak bu durumda Bu senaryo ile ASP.NET Core düz web geliştirme odaklanır çünkü Docker kapsayıcılarında çalışmıyor.

Ancak, eShopOnContainers (eShopWeb) kullanılabilir Basitleştirilmiş sürüm Docker kapsayıcısı içinde çalışır.

## <a name="docker-support"></a>Docker desteği

EShopOnWeb proje .NET Core üzerinde çalışır. Bu nedenle, Linux tabanlı veya Windows tabanlı kapsayıcılarında çalıştırabilirsiniz. Aynı ana bilgisayar türü SQL Server için kullanmak istediğiniz Docker dağıtımı için unutmayın. Linux tabanlı kapsayıcıları daha küçük bir yer sağlar ve tercih edilir.

Visual Studio çözüm Docker için destek ekler bir proje şablonu sağlar. Projeye sağ tıklayın, ardından **Ekle** arkasından **Docker Destek**. Projenizi ve yeni bir şablon bir Dockerfile ekler **docker compose'u** proje starter docker-compose.yml dosyası sağlar. Bu adım, Github'dan indirilen eShopOnWeb projede zaten gerçekleştirilmedi. Çözüm içerdiğini görürsünüz **eShopOnWeb** proje ve **docker compose'u** proje Şekil 6-1'de gösterildiği gibi.

![](./media/image1.png)

**Şekil 6-1**. **Docker compose'u** bir tek kapsayıcı web uygulaması projesi

Bu dosyalar standart docker-dosyaları, hiçbir Docker projeyle tutarlı oluşturun. Bunları, Visual Studio ile veya komut satırından kullanabilirsiniz. Bu uygulama .NET Core üzerinde çalışır ve ayrıca kod, derleme ve bir Mac veya Linux makine çalıştırmak için Linux kapsayıcıları kullanır.

Docker-compose.yml dosyası ne oluşturmak için görüntüler ve başlatmak için hangi kapsayıcıları hakkında bilgi içerir. Şablonları nasıl eshopweb yansıması oluştur ve uygulamanın kapsayıcıları başlatma belirtin. Bir görüntü ekleyerek SQL Server'da bağımlılık eklemeniz gerekir (örneğin, mssql sunucu linux) ve bir hizmet oluşturmak ve bu kapsayıcı başlatmak Docker sql.data görüntü için. Bu ayarlar, aşağıdaki örnekte gösterilir:

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

Bağımlı\_eShopWeb görüntü sql.data görüntüde bağlıdır Docker yönergesi üzerinde söyler. Bir görüntü oluşturmak için yönergeler aşağıdaki satırları microsoft/mssql-server-linux görüntüsünü kullanarak sql.data etiketlenir.

**Docker compose'u** project bu dosyaların ilişkili olduğunu görsel bir gösterge sağlamak için ana docker-compose.yml düğümü altındaki diğer docker-compose dosyaları görüntüler. Docker oluşturan override.yml dosyası hem Hizmetleri, bağlantı dizeleri ve diğer uygulama ayarları gibi ayarları içerir.

Aşağıdaki örnek Visual Studio'da hata ayıklama için kullanılan ayarları içerir docker compose.vs.debug.yml dosya gösterir. Bu dosyada eshopweb görüntü eklenmiş geliştirme etiketi yok. Böylece, yanlışlıkla hata ayıklama bilgileri üretim ortamına dağıtılmaz, yayın görüntülerden ayrı hata ayıklama yardımcı olur:

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

Eklenen son docker compose.ci.build.yml dosyasıdır. Bu komut satırından bir CI sunucudan Projeyi derlemek için kullanılabilir. Bu oluşturma dosyası, uygulamanız için gerekli görüntü oluşturur Docker kapsayıcısı başlatır. Aşağıdaki örnek, docker compose.ci.build.yml dosyasının içeriğini gösterir.

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

**Not**: .NET Core 2.0 ile başlayarak, dotnet restore komutu otomatik olarak yürütür dotnet yayımlarken yürütülür.

Görüntünün bir ASP.NET Core yapı görüntü olduğuna dikkat edin. Bu görüntüyü Uygulamanızı yapılandırmak ve gerekli görüntüleri oluşturmak için SDK'sı ve derleme araçlarını içerir. Çalışan **docker compose'u** bu dosyayı kullanarak proje derleme kapsayıcı görüntüden başlar, sonra bu kapsayıcıda uygulamanızın görüntü oluşturur. Bu docker belirtin-Docker kapsayıcısı uygulamanızda oluşturmak için komut satırının parçası olarak dosya oluşturun ve sonra başlatın.

Visual Studio'da seçerek uygulamanızı Docker kapsayıcılarında çalıştırabilirsiniz **docker-oluşturan** proje başlangıç projesi olarak ve Ctrl + F5'e (hata ayıklama için) F5 ' e basarak başka bir uygulama ile yapabileceğiniz gibi. Başlattığınızda **docker compose'u** proje, Visual Studio çalışır **docker compose'u** docker-compose.yml dosyası, docker compose.override.yml dosya ve docker compose.vs birini kullanarak.\* dosyalar. Uygulama başlatıldıktan sonra Visual Studio tarayıcı başlatır.

Hata ayıklayıcı uygulama başlatma, Visual Studio Docker çalışan uygulamaya ekleyecek.

## <a name="troubleshooting"></a>Sorun giderme

Bu bölümde ortaya çıkabilecek bazı sorunlar açıklanmaktadır, yerel olarak çalıştırma kapsayıcılarınızı ve bazı düzeltmeler önerir.

### <a name="stopping-docker-containers"></a>Docker kapsayıcıları durdurma 

Kapsayıcılı uygulama başlattıktan sonra kapsayıcıları bile hata ayıklama durdurduktan sonra çalışmaya devam eder. Docker çalışan hangi kapsayıcılar görmek için komut satırından ps komutu çalıştırabilirsiniz. Şekil 6-2'de gösterildiği gibi docker Durdur komutu çalışan bir kapsayıcı durdurur.

![](./media/image2.png)

**Şekil 6-2**. Listeleme ve docker stop CLI komutlarının ve docker ps ile kapsayıcıları durdurma

Farklı yapılandırmaları arasında geçiş yaptığınızda çalışan işlemleri durdurmanız gerekebilir. Aksi takdirde, web uygulamasını çalıştıran kapsayıcı uygulamanız için bağlantı noktasını kullanıyorsa (Bu örnekte 5106).

### <a name="adding-docker-to-your-projects"></a>Docker projelerinize ekleme

Docker desteği ekler Sihirbazı'nı çalışan Docker işlemi ile iletişim kurar. Sihirbazı başlattığınızda Docker çalışmıyorsa, sihirbazın düzgün çalışmaz. Ayrıca, sihirbaz doğru Docker desteği eklemek için geçerli kapsayıcı tercih ettiğiniz inceler. Windows kapsayıcıları için destek eklemek istiyorsanız, Docker çalışan Windows yapılandırılmış kapsayıcılar ile çalışırken Sihirbazı'nı çalıştırmanız gerekir. Linux kapsayıcıları için destek eklemek istiyorsanız, Docker ile yapılandırılmış Linux kapsayıcıları çalıştıran varken Sihirbazı'nı çalıştırın.

>[!div class="step-by-step"]
[Önceki] (.. / docker-application-development-process/docker-app-development-workflow.md) [sonraki] (.. /containerize-NET-Framework-Applications/index.MD)
