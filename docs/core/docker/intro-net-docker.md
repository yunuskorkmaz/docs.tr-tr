---
title: .NET ve Docker'a giriş
description: Docker anlama ve .NET Core
author: jralexander
ms.author: johalex
ms.date: 11/06/2017
ms.custom: mvc
ms.openlocfilehash: 0fe3fcdee1c508f5c8165b7709ca08e42d0b1d55
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/09/2018
ms.locfileid: "44251777"
---
# <a name="introduction-to-net-and-docker"></a>.NET ve Docker'a giriş

Bu makalede, bir giriş ve Docker üzerinde .NET ile çalışmak için kavramsal arka plan sağlar.

## <a name="docker-packaging-your-apps-to-deploy-and-run-anywhere"></a>Docker: paketleme uygulamalarınızı dağıtma ve her yerde çalıştırın

[Docker](../../standard/microservices-architecture/container-docker-introduction/docker-defined.md) geliştiriciler ve yöneticiler yapı olanak tanıyan açık bir platformdur [görüntüleri](https://docs.docker.com/glossary/?term=image)gönderin ve dağıtılmış uygulamaları adlı gevşek yalıtılmış bir ortamda çalıştırmak bir [kapsayıcı](https://www.docker.com/what-container). Bu yaklaşım, geliştirme, QA ve üretim ortamları arasında verimli uygulama yaşam döngüsü yönetimi sağlar.
 
[Docker platformu](https://docs.docker.com/engine/docker-overview/#the-docker-platform) kullanan [Docker altyapısı](https://docs.docker.com/engine/docker-overview/#docker-engine) oluşturmayı ve uygulamaları olarak paketini [Docker görüntüleri](https://docs.docker.com/glossary/?term=image) yazılan dosyaları kullanılarak oluşturulan [Dockerfile ](https://docs.docker.com/glossary/?term=Dockerfile) ardından dağıtılmış ve Çalıştır biçimi bir [kapsayıcı katmanlı](https://docs.docker.com/engine/userguide/storagedriver/imagesandcontainers/#container-and-layers).

Ya da kendi oluşturabileceğiniz [görüntüleri katmanlı](https://docs.docker.com/engine/userguide/storagedriver/imagesandcontainers/#images-and-layers) dockerfile'ları veya var olanları gelen kullanımı olarak bir [kayıt defteri](https://docs.docker.com/glossary/?term=registry)gibi [Docker Hub](https://docs.docker.com/glossary/?term=Docker%20Hub).

[Docker kapsayıcıları, görüntüleri ve kayıt defterleri arasındaki ilişki](../../standard/microservices-architecture/container-docker-introduction/docker-containers-images-registries.md) önemli bir kavramdır olduğunda [tasarlama ve oluşturma kapsayıcılı uygulamalar veya mikro Hizmetler](../../standard/microservices-architecture/architect-microservice-container-applications/index.md). Bu yaklaşım, geliştirme ve dağıtım arasındaki süreyi önemli ölçüde kısaltır.

### <a name="further-reading-and-watching"></a>Daha fazla bilgi (ve izleme)

* [Windows tabanlı kapsayıcılar: Kurumsal düzeyde denetimiyle Modern uygulama geliştirme.](https://www.youtube.com/watch?v=Ryx3o0rD5lY&feature=youtu.be)
* [Docker'a genel bakış](https://docs.docker.com/engine/docker-overview/)
* [Dockerfile Windows kapsayıcıları hakkında](/virtualization/windowscontainers/manage-docker/manage-windows-dockerfile)
* [Dockerfile'ları yazmak için en iyi uygulamalar](https://docs.docker.com/engine/userguide/eng-image/dockerfile_best-practices/)
* [.NET Core uygulamaları için Docker görüntüleri oluşturma](../docker/building-net-docker-images.md)


### <a name="getting-net-docker-images"></a>.NET Docker görüntüleri alma

Resmi .NET Docker görüntüleri oluşturulur ve Microsoft tarafından en iyi duruma getirilmiş. Bunlar Microsoft depoları Docker hub'da genel olarak kullanılabilir. Her bir depo birden çok görüntüsü, işletim sistemi sürümleri ve .NET sürümleri bağlı olarak içerebilir. Çoğu resmi depoları, belirli framework sürümü hem (Linux distro veya Windows sürümü) bir işletim sistemi seçmenize yardımcı olmak için kapsamlı etiketleme sağlar.

## <a name="scenario-based-guidance"></a>Temel senaryo Kılavuzu

Microsoft'un amacı .NET deposu için belirli bir senaryoyu veya iş yükünü temsil eder, ayrıntılı ve odaklanmış depoları olmasını sağlamaktır.

`microsoft/aspnetcore` Görüntüleri için iyileştirilmiştir ASP.NET Core uygulamaları, Docker kapsayıcıları daha hızlı bir şekilde başlamak için.

.NET Core görüntüleri (`microsoft/dotnet`) üzerinde .NET Core konsol uygulamaları için tasarlanmıştır. Örneğin, toplu işlemler, Azure Web işleri ve diğer konsol senaryolar en iyi duruma getirilmiş .NET Core görüntüleri kullanmanız gerekir.

Docker ve .NET uygulamaları kullanmak için en belirgin yatay üretim dağıtım ve barındırma için senaryodur. Bu üretim yalnızca bir senaryodur ve diğer formüllerde eşit yararlıdır ettik. Bu senaryolar. NET'e özel değildir, ancak çoğu geliştirici platformu için uygulamanız gerekir.

* **Düşük uyuşmazlıkları yükleme** — yerel bir yüklemesini .NET deneyebilirsiniz. Yalnızca .NET içindeki bir Docker görüntüsünü indirin.

* **Bir kapsayıcıda geliştirme** — tutarlı bir ortamda geliştirme ve üretim ortamları (gibi geliştirici makinelerinde genel durumu sorunlarını önleme) benzer hale geliştirebilirsiniz. Docker için Visual Studio Araçları, hatta doğrudan Visual Studio'dan bir kapsayıcı başlatma olanak sağlar.

* **Bir kapsayıcıda test** — kaynaklanan yanlış yapılandırılmış ortamlar azaltma bir kapsayıcıda test edebilir veya başka değişiklikler son test çalıştırmasından geride bıraktığı.

* **Bir kapsayıcıda yapı** — paylaşılan derleme makinesi birden çok ortam için doğru şekilde yapılandırın, ancak bunun yerine bir "BYOC" taşıma gereğinden kurtulursunuz kod bir kapsayıcıya oluşturabilirsiniz (kendi kapsayıcınızı Getir) yaklaşım.

* **Tüm ortamlarda dağıtımı** — görüntü tüm ortamlarınızda dağıtabilirsiniz. Bu yaklaşım genellikle dış yapılandırma (örneğin, eklenen ortam değişkenlerini) aracılığıyla görüntü davranışını değiştirme, yapılandırma farklılıkları nedeniyle hataları azaltır.

[Genel rehberlik](../../standard/microservices-architecture/net-core-net-framework-containers/general-guidance.md) için Docker kapsayıcı geliştirme için .NET Core ve .NET Framework arasında karar.

### <a name="common-docker-development-scenarios"></a>Docker geliştirme senaryoları

#### <a name="net-core"></a>.NET Core

**.NET core kaynakları**

 İlgilendiğiniz senaryolarınıza uyacak .NET Core örnek seçin. Tüm örnek yönergeler, Windows veya Linux Docker görüntüleri Windows, Linux veya macOS konağından hedef açıklanmaktadır.

.NET Core 2.0 örnekleri kullanın. Docker kullandıkları [çok aşamalı derleme](https://github.com/dotnet/announcements/issues/18) ve [çok yay etiketleri](https://github.com/dotnet/announcements/issues/14) uygun olduğunda.

* [.NET core görüntüleri dockerhub'da](https://hub.docker.com/r/microsoft/dotnet/)

* [.NET Core uygulamasını docker kapsayıcılarında çalıştırın](https://docs.docker.com/engine/examples/dotnetcore/)

* Bu .NET Core Docker örnek gösterir nasıl [.NET Core geliştirme sürecinizde Docker'ı kullanma](https://github.com/dotnet/dotnet-docker-samples/tree/master/dotnetapp-dev). Örnek, hem Linux hem de Windows kapsayıcıları ile çalışır.

* Bu .NET Core Docker örnek bir en iyi uygulama desenini gösterir [üretim için .NET Core uygulamaları için Docker görüntülerinizi oluşturmak.](https://github.com/dotnet/dotnet-docker-samples/tree/master/dotnetapp-prod) Örnek, hem Linux hem de Windows kapsayıcıları ile çalışır.

* Bu [.NET Core Docker örnek](https://github.com/dotnet/dotnet-docker-samples/tree/master/dotnetapp-selfcontained) için Docker görüntüleri oluşturmaya yönelik en iyi uygulama desenini gösterir [kendi başına bir .NET Core uygulamaları](../deploying/index.md). Bir avantajı olmadan en küçük üretim kapsayıcısı için kullanılan [kapsayıcılar arasındaki temel görüntülerini paylaşarak](https://docs.docker.com/engine/userguide/storagedriver/imagesandcontainers/). Ancak, daha düşük Docker katmanları paylaşılan.

#### <a name="arm32--raspberry-pi"></a>ARM32 / Raspberry Pi

* [.NET core çalışma zamanı ARM32 duyuru oluşturur.](https://github.com/dotnet/announcements/issues/29)

* [ARM32 / Raspberry Pi .NET Core üzerinde DockerHub görüntüleri](https://hub.docker.com/r/microsoft/dotnet/)

* [ARM32 / Raspberry Pi .NET Core, Docker, GitHub üzerinde örnekleri](https://github.com/dotnet/dotnet-docker-samples#arm32--raspberry-pi)

#### <a name="net-framework"></a>.NET Framework

* [.NET framework görüntüleri dockerhub'da](https://hub.docker.com/r/microsoft/dotnet-framework/)

Bu deponun çeşitli .NET Framework Docker yapılandırmaları gösteren örnekler içerir. Docker görüntülerinizi temel olarak bu görüntüleri kullanabilirsiniz.

**.NET framework 4.7**

[Dotnet-framework: 4.7 örnek](https://github.com/Microsoft/dotnet-framework-docker-samples/tree/master/dotnetapp-4.7) temel "Merhaba Dünya" kullanımını gösteren [.NET Framework 4.7](../../framework/whats-new/index.md#v47). Size nasıl oluşturun ve bağlı uygulama dağıtma gösterir [.NET Framework 4.7 docker görüntüsü](https://github.com/Microsoft/dotnet-framework-docker-samples/blob/master/dotnetapp-4.7/Dockerfile).

**.NET framework 4.6.2**

[Dotnet-framework: 4.6.2 örnek](https://github.com/Microsoft/dotnet-framework-docker-samples/tree/master/dotnetapp-4.6.2) temel "Merhaba Dünya" kullanımını gösteren [.NET Framework 4.6.2](../../framework/whats-new/index.md#v462). Size nasıl oluşturun ve bağlı uygulama dağıtma gösterir [.NET Framework 4.6.2 docker görüntüsü](https://github.com/Microsoft/dotnet-framework-docker-samples/blob/master/dotnetapp-4.6.2/Dockerfile).

**.NET framework 3.5**

 [Dotnet-framework: 3.5 örnek](https://github.com/Microsoft/dotnet-framework-docker-samples/tree/master/dotnetapp-3.5) temel "Merhaba Dünya" kullanımını gösteren [.NET Framework 3.5](https://github.com/Microsoft/dotnet-framework-docker-samples/blob/master/dotnetapp-3.5/dotnetapp-3.5/Dockerfile). Bu, nasıl yapı ve .NET Framework 3.5 docker'da bağlı bir proje dağıtma gösterilmektedir.

#### <a name="aspnet-core"></a>ASP.NET Core

* [Bu ASP.NET Core Docker örnek](https://github.com/dotnet/dotnet-docker-samples/tree/master/aspnetapp) Docker görüntüleri için ASP.NET Core için üretim uygulamaları oluşturmaya yönelik en iyi uygulama desenini gösterir. Örnek, hem Linux hem de Windows kapsayıcıları ile çalışır.

* [ASP.NET Core görüntüleri dockerhub'da](https://hub.docker.com/r/microsoft/aspnetcore-build/)

* [GitHub üzerinde ASP.NET Core görüntüleri](https://github.com/aspnet/aspnet-docker)

#### <a name="aspnet-framework"></a>ASP.NET Framework

* [ASP.NET Framework görüntüleri dockerhub'da](https://hub.docker.com/r/microsoft/aspnet/)

* [.NET Framework 4.6.2 örnek üzerinde ASP.NET Web Forms uygulaması](https://github.com/Microsoft/dotnet-framework-docker-samples/tree/master/aspnetapp)

#### <a name="windows-communication-framework-wcf"></a>Windows Communication Framework (WCF)

* [Dockerhub'da Windows Communication Framework (WCF) görüntüleri](https://hub.docker.com/r/microsoft/wcf/)

* [GitHub üzerinde Windows Communication Framework (WCF) görüntüleri](https://github.com/microsoft/wcf-docker)

* [Windows Communication Framework (WCF) Docker örnekleri kullanarak .NET Framework 4.6.2](https://github.com/Microsoft/wcf-docker-samples)

#### <a name="internet-information-server-iis"></a>Internet Information Server (IIS)

* [Dockerhub'da Internet Information Server (IIS) görüntüleri](https://hub.docker.com/r/microsoft/iis/)

* [GitHub üzerinde Internet Bilgi Sunucusu (IIS) görüntüleri](https://github.com/microsoft/iis-docker)

### <a name="interact-with-other-microsoft-stack-container-images"></a>Diğer Microsoft stack kapsayıcı görüntüleri ile etkileşim kurma

#### <a name="microsoft-sql-server"></a>Microsoft SQL Server

* [Microsoft SQL Server 2017 Linux kapsayıcı görüntüsü için Docker Hızlı Başlangıç ile çalıştırın.](https://docs.microsoft.com/sql/linux/quickstart-install-connect-docker)

* [Microsoft SQL Server Linux görüntüleri dockerhub'da](https://hub.docker.com/r/microsoft/mssql-server-linux/)

* [Microsoft SQL Server Express Edition görüntülerini dockerhub'da Windows kapsayıcıları için](https://hub.docker.com/r/microsoft/mssql-server-windows-express/)

* [Microsoft SQL Server Developer Edition görüntülerini dockerhub'da Windows kapsayıcıları için](https://hub.docker.com/r/microsoft/mssql-server-windows-developer/)

#### <a name="visual-studio-team-services-vsts-agent"></a>Visual Studio Team Services (VSTS) aracısı

* [Visual Studio Team Services (VSTS) aracısı görüntüleri dockerhub'da](https://hub.docker.com/r/microsoft/vsts-agent/)

* [GitHub üzerinde Visual Studio Team Services (VSTS) aracısı görüntüleri](https://github.com/Microsoft/vsts-agent-docker)

#### <a name="operations-management-suite-oms-linux-agent"></a>Operations Management Suite (OMS) Linux Aracısı

* [Operations Management Suite (OMS) Linux Aracısı genel bakış](https://github.com/Microsoft/OMS-Agent-for-Linux/blob/master/docs/Docker-Instructions.md)

* [Dockerhub'da Operations Management Suite (OMS) görüntüleri](https://hub.docker.com/r/microsoft/oms/)

* [GitHub üzerinde Operations Management Suite (OMS) görüntüleri](https://github.com/Microsoft/OMS-docker)

#### <a name="microsoft-azure-command-line-interface-cli"></a>Microsoft Azure komut satırı arabirimi (CLI)

* [Dockerhub'da Microsoft Azure komut satırı arabirimi (CLI) görüntüleri](https://hub.docker.com/r/microsoft/azure-cli/) 

* [Github'da Microsoft Azure komut satırı arabirimi (CLI) görüntüleri](https://github.com/Azure/azure-cli#Docker)

> [!NOTE]
> Azure aboneliğiniz yoksa [hemen kaydolun](https://azure.microsoft.com/free/?b=16.48) 30 günlük ücretsiz hesabı ve get 200 ABD Doları değerinde Azure kredisi, out Azure Hizmetleri, herhangi bir birleşimini denemek için.

#### <a name="microsoft-azure-cosmos-db-emulator-windows-containers-only"></a>Microsoft Azure Cosmos DB öykünücüsü'nü (yalnızca Windows kapsayıcıları için)

* [Microsoft Azure Cosmos DB öykünücüsü'nü görüntüleri dockerhub'da](https://hub.docker.com/r/microsoft/azure-cosmosdb-emulator) 

* [Yerel geliştirme ve test için Azure Cosmos DB öykünücüsü'nü kullanın](/azure/cosmos-db/local-emulator#developing-with-the-emulator)

## <a name="exploring-the-rich-docker-development-ecosystem"></a>Zengin Docker geliştirme ekosistemini keşfetmeye

Docker platformu ve farklı Docker görüntüleri hakkında öğrendiniz, sonraki adım, zengin Docker ekosistemi sayesinde keşfedin sağlamaktır. Aşağıdaki bağlantılar, Microsoft araçları kapsayıcı geliştirmeyi nasıl tamamlayıcı gösterir.

* [.NET ve Docker'a birlikte kullanma](https://blogs.msdn.microsoft.com/dotnet/2017/05/25/using-net-and-docker-together/)
* [.NET çok kapsayıcılı ve mikro hizmet tabanlı uygulamalar tasarlayıp geliştirerek](../../standard/microservices-architecture/multi-container-microservice-net-applications/index.md)
* [Visual Studio kod Docker uzantısı](https://code.visualstudio.com/docs/languages/dockerfile)
* [Azure Service Fabric kullanmayı öğrenin](/azure/service-fabric/index)
* [Örnek alma, Service Fabric kullanmaya](https://azure.microsoft.com/resources/samples/service-fabric-dotnet-getting-started/)
* [Windows kapsayıcıları avantajları](/virtualization/windowscontainers/about/index#video-overview)
* [Visual Studio Docker araçları ile çalışma](/aspnet/core/host-and-deploy/docker/visual-studio-tools-for-docker)
* [Docker görüntülerini Azure Container registry'den Azure Container ınstances'a dağıtma](https://blogs.msdn.microsoft.com/stevelasker/2017/07/28/deploying-docker-images-from-the-azure-container-registry-to-azure-container-instances/)
* [Visual Studio kodu ile hata ayıklama](https://code.visualstudio.com/docs/nodejs/debugging-recipes#_nodejs-typescript-docker-container)
* [Bire bir Visual Studio ile Mac, kapsayıcılar ve sunucusuz kod için bulutta hakkında edinme](https://blogs.msdn.microsoft.com/visualstudio/2017/08/31/hands-on-with-visual-studio-for-mac-containers-serverless-code-in-the-cloud/#comments)
* [Mac Laboratuvar için Docker ve Visual Studio ile çalışmaya başlama](https://github.com/Microsoft/vs4mac-labs/tree/master/Docker/Getting-Started)

## <a name="next-steps"></a>Sonraki adımlar

* [.NET Core ile Docker Temellerini Öğrenme](docker-basics-dotnet-core.md)
* [.NET Core, Docker görüntüleri oluşturma](building-net-docker-images.md)
