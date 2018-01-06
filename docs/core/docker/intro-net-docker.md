---
title: ".NET ve Docker giriş"
description: Anlama Docker ve .NET Core
keywords: .NET, .NET core, Docker
author: jralexander
ms.author: johalex
ms.date: 11/06/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-docker
ms.devlang: dotnet
ms.assetid: 03c28597-7e73-46d6-a9c3-f9cb55642739
manager: wpickett
ms.custom: mvc
ms.workload: dotnetcore
ms.openlocfilehash: 8c6daabb3040998d3376ad022790c16b9629233f
ms.sourcegitcommit: bf8a3ba647252010bdce86dd914ac6c61b5ba89d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/06/2018
---
# <a name="introduction-to-net-and-docker"></a>.NET ve Docker giriş

Bu makalede, bir giriş ve Docker .NET ile çalışmaya kavramsal arka plan sağlar.

## <a name="docker-packaging-your-apps-to-deploy-and-run-anywhere"></a>Docker: dağıtmak ve her yerden çalıştırmak için uygulamalarınızı paketleme

[Docker](../../standard/microservices-architecture/container-docker-introduction/docker-defined.md) geliştiricilerinin ve yöneticilerinin oluşturmak bir açık Platform [görüntüleri](https://docs.docker.com/glossary/?term=image)sevk ve dağıtılmış uygulamaları adlı geniş yalıtılmış bir ortamda çalıştırmak bir [kapsayıcı](https://www.docker.com/what-container). Bu yaklaşım, geliştirme, QA ve üretim ortamlarını arasında verimli uygulama yaşam döngüsü yönetimi sağlar.
 
[Docker platform](https://docs.docker.com/engine/docker-overview/#the-docker-platform) kullanan [Docker altyapısına](https://docs.docker.com/engine/docker-overview/#docker-engine) hızlı bir şekilde oluşturmak ve uygulamaları olarak paketlemek için [Docker görüntüleri](https://docs.docker.com/glossary/?term=image) yazılan dosyaları kullanılarak oluşturulan [Dockerfile ](https://docs.docker.com/glossary/?term=Dockerfile) sonra dağıtılır ve Çalıştır biçimde bir [kapsayıcı katmanlı](https://docs.docker.com/engine/userguide/storagedriver/imagesandcontainers/#container-and-layers).

Oluşturabilir ya da kendi [görüntüleri katmanlı](https://docs.docker.com/engine/userguide/storagedriver/imagesandcontainers/#images-and-layers) dockerfiles veya var olanları gelen kullanım olarak bir [kayıt defteri](https://docs.docker.com/glossary/?term=registry)gibi [Docker hub'a](https://docs.docker.com/glossary/?term=Docker%20Hub).

[Docker kapsayıcıları, görüntüler ve kayıt defterleri arasındaki ilişkiyi](../../standard/microservices-architecture/container-docker-introduction/docker-containers-images-registries.md) önemli bir kavramdır zaman [mimarisi oluşturma ve derleme kapsayıcılı uygulamalar veya mikro](../../standard/microservices-architecture/architect-microservice-container-applications/index.md). Bu yaklaşım, geliştirme ve dağıtım arasındaki süreyi büyük ölçüde kısaltır.

### <a name="further-reading-and-watching"></a>Daha fazla bilgi (ve izleyen)

* [Windows tabanlı kapsayıcıları: Kurumsal düzeyde denetim ile Modern uygulama geliştirme.](https://www.youtube.com/watch?v=Ryx3o0rD5lY&feature=youtu.be)
* [Docker genel bakış](https://docs.docker.com/engine/docker-overview/)
* [Windows kapsayıcılarında Dockerfile](/virtualization/windowscontainers/manage-docker/manage-windows-dockerfile.md)
* [Dockerfiles yazmak için en iyi uygulamalar](https://docs.docker.com/engine/userguide/eng-image/dockerfile_best-practices/)
* [.NET Core uygulamaları için yapı Docker görüntüleri](../docker/building-net-docker-images.md)


### <a name="getting-net-docker-images"></a>.NET Docker görüntüleri alma

Resmi .NET Docker görüntüleri oluşturulur ve Microsoft tarafından en iyi duruma getirilmiş. Bunlar Microsoft depoları Docker hub'ındaki genel olarak kullanılabilir. Her depo işletim sistemi sürümleri ve .NET sürümleri bağlı olarak birden fazla görüntü içerebilir. Çoğu görüntü depoları belirli framework sürümünü ve (Linux distro veya Windows sürümü) bir işletim sistemi seçmenize yardımcı olmak için kapsamlı etiketleme sağlar.

## <a name="scenario-based-guidance"></a>Temel senaryo Kılavuzu

Microsoft'un hedefi .NET depoları için belirli bir senaryoyu ya da iş yükünü temsil ayrıntılı ve odaklanmış depoları olmalıdır.

`microsoft/aspnetcore` Görüntüleri en iyi duruma getirilmiş Docker, ASP.NET Core uygulamaları için kapsayıcıları daha hızlı başlatabilmeniz.

.NET Core görüntüleri (`microsoft/dotnet`) .NET Core üzerinde dayalı konsol uygulamalar için tasarlanmıştır. Örneğin, toplu işlemler, Azure Web işleri ve diğer konsol senaryoları en iyi duruma getirilmiş .NET Core görüntüleri kullanmanız gerekir.

Docker ve .NET uygulamaları kullanmak için en bariz yatay Üretim dağıtımı ve barındırmak için bir senaryodur. Bu üretim yalnızca bir senaryodur ve diğer eşit yararlı olanlardır ortaya çıkmıştır. Bu senaryolar için .NET belirli değildir, ancak çoğu Geliştirici platformları uygulamalıdır.

* **Düşük uyuşmazlık yüklemek** — .NET yerel bir yükleme deneyebilirsiniz. Yalnızca .NET Docker görüntüsüyle da indirin.

* **Bir kapsayıcıda geliştirmek** — tutarlı bir ortamda, geliştirme ve üretim ortamlarını benzer (Geliştirici makinelerde genel durum gibi sorunlarını önleme) yapmadan geliştirebilirsiniz. Docker için Visual Studio Araçları bile doğrudan Visual Studio'dan bir kapsayıcı başlatmak etkinleştirin.

* **Test bir kapsayıcıda** — yanlış yapılandırılmış ortamları kaynaklanan hatalar azaltma bir kapsayıcıda test edebilirsiniz veya başka değişiklikler geride bıraktığı son testten.

* **Bir kapsayıcıda yapı** — paylaşılan yapı makineleri çoklu ortamlar için doğru yapılandırma ancak bunun yerine bir "BYOC" taşımak için gereken önleme kod içinde bir kapsayıcı oluşturabilirsiniz (kendi kapsayıcı Getir) yaklaşım.

* **Tüm ortamlar dağıtımda** — bir görüntü tüm ortamlarınızın dağıtabilirsiniz. Bu yaklaşım, genellikle dış yapılandırması (örneğin, eklenen ortam değişkenleri) aracılığıyla görüntü davranışı değiştirme yapılandırma farklılıkları nedeniyle hataları azaltır.

[Genel rehberlik](../../standard/microservices-architecture/net-core-net-framework-containers/general-guidance.md) .NET Core ve .NET Framework arasında Docker kapsayıcısı geliştirme için karar verme.

### <a name="common-docker-development-scenarios"></a>Docker geliştirme senaryoları

#### <a name="net-core"></a>.NET Core

**.NET core kaynaklar**

 İlgilenilen senaryolarınızı sığacak .NET Core örnekleri seçin. Tüm örnek yönergeleri, Windows, Linux veya macOS ana bilgisayar Windows veya Linux Docker görüntü hedef açıklar.

Örnekleri .NET Core 2.0 kullanın. Docker kullandıkları [çok aşama yapı](https://github.com/dotnet/announcements/issues/18) ve [çok yay etiketleri](https://github.com/dotnet/announcements/issues/14) uygun olduğunda.

* [.NET core DockerHub görüntülerinde](https://hub.docker.com/r/microsoft/dotnet/)

* [.NET Core uygulama dockerize](https://docs.docker.com/engine/examples/dotnetcore/)

* Bu .NET Core Docker örnek gösterilmektedir nasıl [Docker .NET Core geliştirme sürecinizde kullanmak](https://github.com/dotnet/dotnet-docker-samples/tree/master/dotnetapp-dev). Örnek, Linux ve Windows kapsayıcılarını ile çalışır.

* Bu .NET Core Docker örneği için en iyi yöntem deseni gösterir [üretim için .NET Core uygulamaları için Docker görüntülerinizi oluşturmak.](https://github.com/dotnet/dotnet-docker-samples/tree/master/dotnetapp-prod) Örnek, Linux ve Windows kapsayıcılarını ile çalışır.

* Bu [.NET Core Docker örnek](https://github.com/dotnet/dotnet-docker-samples/tree/master/dotnetapp-selfcontained) için Docker görüntülerinizi oluşturmak için en iyi yöntem desen gösteren [müstakil .NET Core uygulamaları](../deploying/index.md). Bir avantajı olmadan küçük üretim kapsayıcısı için kullanılan [kapsayıcılar arasındaki temel görüntüleri paylaşımı](https://docs.docker.com/engine/userguide/storagedriver/imagesandcontainers/). Ancak, daha düşük Docker Katmanlar paylaşılan.

#### <a name="arm32--raspberry-pi"></a>ARM32 / Raspberry Pi

* [Duyuru .NET çekirdeği çalışma zamanı ARM32 derlemeler](https://github.com/dotnet/announcements/issues/29)

* [ARM32 / Raspberry Pi .NET Core üzerinde DockerHub görüntüleri](https://hub.docker.com/r/microsoft/dotnet/)

* [ARM32 / Böğürtlenli Pi .NET Core Docker Github'da örnekleri](https://github.com/dotnet/dotnet-docker-samples#arm32--raspberry-pi)

#### <a name="net-framework"></a>.NET Framework

* [.NET framework DockerHub görüntülerinde](https://hub.docker.com/r/microsoft/dotnet-framework/)

Bu depodaki çeşitli .NET Framework Docker yapılandırmaları gösteren örnekleri içerir. Bu görüntüler, kendi Docker görüntülerinizi temel olarak kullanabilirsiniz.

**.NET framework 4.7**

[Dotnet-framework: 4.7 örnek](https://github.com/Microsoft/dotnet-framework-docker-samples/tree/master/dotnetapp-4.7) temel "hello world" kullanımını gösteren [.NET Framework 4.7](../../framework/whats-new/index.md#v47). Size nasıl derleme ve güvenmek uygulama dağıtma gösterir [.NET Framework 4.7 docker görüntü](https://github.com/Microsoft/dotnet-framework-docker/blob/master/4.7/Dockerfile).

**.NET framework 4.6.2**

[Dotnet-framework: 4.6.2 örnek](https://github.com/Microsoft/dotnet-framework-docker-samples/tree/master/dotnetapp-4.6.2) temel "hello world" kullanımını gösteren [.NET Framework 4.6.2](../../framework/whats-new/index.md#v462). Size nasıl derleme ve güvenmek uygulama dağıtma gösterir [.NET Framework 4.6.2 docker görüntü](https://github.com/Microsoft/dotnet-framework-docker/tree/master/4.6.2).

**.NET framework 3.5**

 [Dotnet-framework: 3.5 örnek](https://github.com/Microsoft/dotnet-framework-docker-samples/tree/master/dotnetapp-3.5) temel "hello world" kullanımını gösteren [.NET Framework 3.5](https://github.com/Microsoft/dotnet-framework-docker/tree/master/3.5). Size nasıl derleme ve .NET Framework 3. 5'Docker ' bağlı olan bir proje dağıtma gösterir.

#### <a name="aspnet-core"></a>ASP.NET Core

* [Bu ASP.NET Core Docker örnek](https://github.com/dotnet/dotnet-docker-samples/tree/master/aspnetapp) Docker görüntülerinizi ASP.NET Core için üretim için uygulamalar oluşturmak için en iyi yöntem desen gösterir. Örnek, Linux ve Windows kapsayıcılarını ile çalışır.

* [ASP.NET Core DockerHub görüntülerinde](https://hub.docker.com/r/microsoft/aspnetcore-build/)

* [Github'da ASP.NET Core görüntüleri](https://github.com/aspnet/aspnet-docker)

#### <a name="aspnet-framework"></a>ASP.NET Framework

* [DockerHub ASP.NET Framework görüntülerde](https://hub.docker.com/r/microsoft/aspnet/)

* [ASP.NET Web Forms uygulama .NET Framework 4.6.2 örneği](https://github.com/Microsoft/dotnet-framework-docker-samples/tree/master/aspnetapp)

#### <a name="windows-communication-framework-wcf"></a>Windows Communication Framework (WCF)

* [Windows Communication Framework (WCF) DockerHub görüntülerinde](https://hub.docker.com/r/microsoft/wcf/)

* [Windows Communication Framework (WCF) görüntüleri github'da](https://github.com/microsoft/iis-docker)

* [Tam .NET Framework 4.6.2 kullanarak Windows Communication Framework (WCF) Docker örnekleri](https://github.com/Microsoft/wcf-docker-samples)

#### <a name="internet-information-server-iis"></a>Internet Information Server (IIS)

* [Internet Information Server (IIS) DockerHub görüntülerinde](https://hub.docker.com/r/microsoft/iis/)

* [Github'da Internet Information Server (IIS) görüntüleri](https://github.com/microsoft/wcf-docker)

### <a name="interact-with-other-microsoft-stack-container-images"></a>Diğer Microsoft yığın kapsayıcı görüntüleri ile etkileşim

#### <a name="microsoft-sql-server"></a>Microsoft SQL Server

* [Linux 2017 kapsayıcı görüntüsü için Microsoft SQL Server ile Docker Quickstart çalıştırın](https://docs.microsoft.com/sql/linux/quickstart-install-connect-docker)

* [Microsoft SQL Server DockerHub Linux görüntülerinde için](https://hub.docker.com/r/microsoft/mssql-server-windows/)

* [DockerHub Windows kapsayıcıları için Microsoft SQL Server görüntülerinde](https://hub.docker.com/r/microsoft/mssql-server-windows/)

* [Microsoft SQL Server Express Edition görüntüleri DockerHub üzerinde Windows kapsayıcıları için](https://hub.docker.com/r/microsoft/mssql-server-windows-express/)

* [Microsoft SQL Server Developer Edition görüntüleri DockerHub üzerinde Windows kapsayıcıları için](https://hub.docker.com/r/microsoft/mssql-server-windows-developer/)

#### <a name="visual-studio-team-services-vsts-agent"></a>Visual Studio Team Services (VSTS) aracısı

* [Visual Studio Team Services (VSTS) aracısı görüntüleri DockerHub üzerinde](https://hub.docker.com/r/microsoft/vsts-agent/)

* [Github'da Visual Studio Team Services (VSTS) aracısı görüntüleri](https://github.com/Microsoft/vsts-agent-docker)

#### <a name="operations-management-suite-oms-linux-agent"></a>Operations Management Suite (OMS) Linux Aracısı

* [Operations Management Suite (OMS) Linux Aracısı genel bakış](https://github.com/Microsoft/OMS-Agent-for-Linux/blob/master/docs/Docker-Instructions.md#overview)

* [Operations Management Suite (OMS) DockerHub görüntülerinde](https://hub.docker.com/r/microsoft/vsts-agent/)

* [Operations Management Suite (OMS) görüntüleri github'da](https://github.com/Microsoft/OMS-docker)

#### <a name="microsoft-azure-command-line-interface-cli"></a>Microsoft Azure komut satırı arabirimi (CLI)

* [DockerHub görüntülerinde Microsoft Azure komut satırı arabirimi (CLI)](https://hub.docker.com/r/microsoft/azure-cli/) 

* [GitHub görüntülerinde Microsoft Azure komut satırı arabirimi (CLI)](https://github.com/Microsoft/OMS-docker)

> [!NOTE]
> Bir Azure aboneliğiniz yoksa [bugün kaydolun](https://azure.microsoft.com/free/?b=16.48) Ücretsiz 30 günlük hesabı ve Azure Hizmetleri herhangi bir bileşimini denemek için Azure KREDİLERİ 200 ABD Doları alın.

#### <a name="microsoft-azure-cosmos-db-emulator-windows-containers-only"></a>Microsoft Azure Cosmos DB öykünücü (yalnızca Windows kapsayıcıları)

* [Microsoft Azure Cosmos DB öykünücüsü DockerHub görüntülerinde](https://hub.docker.com/r/microsoft/azure-cosmosdb-emulator) 

* [Yerel geliştirme ve sınama için Azure Cosmos DB öykünücüsünü kullanma](/azure/cosmos-db/local-emulator.md#developing-with-the-emulator)

## <a name="exploring-the-rich-docker-development-ecosystem"></a>Zengin Docker geliştirme ekosistemi keşfetme

Farklı Docker görüntüler ve Docker platform hakkında öğrendiniz, zengin Docker ekosistemi keşfetmek için sonraki adım olacaktır. Aşağıdaki bağlantılar nasıl Microsoft araçları kapsayıcı geliştirme tamamlayan gösterir.

* [.NET ve Docker birlikte kullanma](https://blogs.msdn.microsoft.com/dotnet/2017/05/25/using-net-and-docker-together/)
* [Tasarlama ve birden çok kapsayıcı ve mikro hizmet tabanlı .NET uygulamaları geliştirme](../../standard/microservices-architecture/multi-container-microservice-net-applications/index.md)
* [Visual Studio kod Docker uzantısı](https://code.visualstudio.com/docs/languages/dockerfile)
* [Azure Service Fabric kullanmayı öğrenin](/azure/service-fabric/index.md)
* [Örnek Service Fabric alma başlatıldı](https://azure.microsoft.com/resources/samples/service-fabric-dotnet-getting-started/)
* [Windows kapsayıcıları yararları](/virtualization/windowscontainers/about/index.md#video-overview)
* [Visual Studio Docker araçları ile çalışma](/aspnet/core/publishing/visual-studio-tools-for-docker/index.md)
* [Azure kapsayıcı örneklerine Azure kapsayıcı kayıt defterinden Docker görüntüleri dağıtma](https://blogs.msdn.microsoft.com/stevelasker/2017/07/28/deploying-docker-images-from-the-azure-container-registry-to-azure-container-instances/)
* [Visual Studio Code ile hata ayıklama](https://code.visualstudio.com/docs/nodejs/debugging-recipes#_nodejs-typescript-docker-container)
* [Ellere Visual Studio ile Mac, kapsayıcıları ve sunucusuz kodu bulutta hakkında alma](https://blogs.msdn.microsoft.com/visualstudio/2017/08/31/hands-on-with-visual-studio-for-mac-containers-serverless-code-in-the-cloud/#comments)
* [Mac Laboratuvar için Docker ve Visual Studio ile çalışmaya başlama](https://github.com/Microsoft/vs4mac-labs/tree/master/Docker/Getting-Started)

## <a name="next-steps"></a>Sonraki adımlar

* [.NET Core ile Docker Temellerini Öğrenme](docker-basics-dotnet-core.md)
* [.NET Core Docker görüntülerinizi oluşturmak](building-net-docker-images.md)
