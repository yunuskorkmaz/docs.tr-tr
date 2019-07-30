---
title: Docker 'a giriş
description: Bu makalede bir .NET Core uygulaması bağlamında Docker 'a bir giriş ve genel bakış sunulmaktadır.
ms.date: 03/20/2019
ms.custom: mvc, seodec18
ms.openlocfilehash: 5da71215e3b539f10993677d23d89e2b8a49cb39
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68626482"
---
# <a name="introduction-to-net-and-docker"></a>.NET ve Docker’a Giriş

.NET Core, bir Docker kapsayıcısında kolayca çalıştırılabilir. Kapsayıcılar, uygulamanızı konak sisteminin geri kalanından yalıtmak, yalnızca çekirdeği paylaşmak ve uygulamanıza verilen kaynakları kullanmak için basit bir yol sağlar. Docker hakkında bilginiz yoksa Docker 'ın [genel bakış belgelerini](https://docs.docker.com/engine/docker-overview/)okumanız önemle tavsiye edilir.

Docker 'ın nasıl yükleneceğine ilişkin daha fazla bilgi için bkz. Docker [Desktop için indirme sayfası: Community Edition](https://www.docker.com/products/docker-desktop).

## <a name="docker-basics"></a>Docker temelleri

Bilmeniz gereken birkaç kavram vardır. Docker istemcisinin, görüntüleri ve kapsayıcıları yönetmek için kullandığınız bir komut satırı arabirimi programı vardır. Daha önce belirtildiği gibi, [Docker genel bakış](https://docs.docker.com/engine/docker-overview/) belgelerini okumak için zaman yapmanız gerekir. 

### <a name="images"></a>Görüntüler

Görüntü, bir kapsayıcının temelini oluşturan dosya sistemi değişikliklerinin sıralı koleksiyonudur. Görüntüde durum yok ve salt okunurdur. Görüntünün başka bir görüntüye göre, ancak bazı özelleştirmesiyle ilgili zamanı. Örneğin, uygulamanız için yeni bir görüntü oluşturduğunuzda, onu zaten .NET Core çalışma zamanının bulunduğu varolan bir görüntüye dayandırmanız gerekir.

Resimler görüntülerden oluşturulduğu için görüntüler, kapsayıcı başladığında çalışan bir çalıştırma parametreleri (örneğin, başlangıç yürütülebilir dosyası) kümesi vardır.

### <a name="containers"></a>Kapsayıcılar

Kapsayıcı bir görüntünün çalıştırılabilir örneğidir. Görüntünüzü oluştururken uygulamanızı ve bağımlılıklarınızı dağıtırsınız. Daha sonra, birden çok kapsayıcı, her biri bir diğerinden yalıtılmış olarak oluşturulabilir. Her kapsayıcı örneğinin kendi dosya sistemi, belleği ve ağ arabirimi vardır.

### <a name="registries"></a>Kayıt

Kapsayıcı kayıt defterleri, bir görüntü depoları koleksiyonudur. Görüntülerinizi bir kayıt defteri görüntüsünde temel alabilirsiniz. Kapsayıcılardan doğrudan kayıt defterindeki bir görüntüden kapsayıcı oluşturabilirsiniz. [Docker kapsayıcıları, görüntüleri ve kayıt defterleri arasındaki ilişki](../../architecture/microservices/container-docker-introduction/docker-containers-images-registries.md) , [Kapsayıcılı uygulamaları veya mikro hizmetleri tasarlayarak ve derlerken](../../architecture/microservices/architect-microservice-container-applications/index.md)önemli bir kavramdır. Bu yaklaşım geliştirme ve dağıtım arasındaki süreyi büyük ölçüde kısaltır.

Docker 'da, kullanabileceğiniz [Docker Hub 'ında](https://hub.docker.com/) barındırılan ortak bir kayıt defteri vardır. [.NET Core ile ilgili görüntüler](https://hub.docker.com/_/microsoft-dotnet-core/) Docker Hub 'ında listelenmiştir. 

Microsoft Container Registry (MCR), Microsoft tarafından sunulan kapsayıcı görüntülerinin resmi kaynağıdır. MCR, genel olarak çoğaltılan görüntüler sağlamak için Azure CDN oluşturulmuştur. Ancak, MCR, herkese açık bir Web sitesine sahip değildir ve Microsoft tarafından sunulan kapsayıcı görüntüleri hakkında bilgi almanın birincil yolu [Microsoft Docker Hub sayfalarıdır](https://hub.docker.com/_/microsoft-dotnet-core/).

### <a name="dockerfile"></a>Dockerfile

**Dockerfile** , bir görüntü oluşturan bir yönergeler kümesini tanımlayan bir dosyadır. **Dockerfile** dosyasındaki her yönerge görüntüde bir katman oluşturur. Çoğu bölümde, görüntüyü yeniden oluşturduğunuzda yalnızca değiştirilen katmanlar yeniden oluşturulur. **Dockerfile** , başkalarına dağıtılabilir ve yeni bir görüntüyü oluşturduğunuz şekilde oluşturmak için yeniden oluşturulmasına olanak sağlar. Bu, görüntüyü oluşturma *yönergelerini* dağıtmanıza izin verdiğinden, görüntünüzü dağıtmanın ana yolu bir kayıt defterine yayımlamaktır.

## <a name="net-core-images"></a>.NET Core görüntüleri

Resmi .NET Core Docker görüntüleri Microsoft Container Registry (MCR) ' de yayımlanır ve [Microsoft .NET Core Docker Hub deposunda](https://hub.docker.com/_/microsoft-dotnet-core/)bulunabilir. Her depo, .NET (SDK veya çalışma zamanı) ve kullanabileceğiniz farklı .NET birleşimlerinin görüntülerini içerir. 

Microsoft, belirli senaryolar için uyarlanmış görüntüler sağlar. Örneğin, [ASP.NET Core deposu](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) üretimde ASP.NET Core uygulamaları çalıştırmak için oluşturulmuş görüntüler sağlar.

## <a name="azure-services"></a>Azure hizmetleri

Çeşitli Azure Hizmetleri, kapsayıcıları destekler. Uygulamanız için bir Docker görüntüsü oluşturup aşağıdaki hizmetlerden birine dağıtırsınız:

* [Azure Kubernetes hizmeti (AKS)](https://azure.microsoft.com/services/kubernetes-service/)\
Kubernetes kullanarak Linux kapsayıcılarını ölçeklendirin ve düzenleyin.

* [Azure App Service](https://azure.microsoft.com/services/app-service/containers/)\
Bir PaaS ortamında Linux kapsayıcıları kullanarak Web uygulamaları veya API 'Ler dağıtın.

* [Azure Container Instances](https://azure.microsoft.com/services/container-instances/)\
Daha üst düzey yönetim hizmetleri olmadan kapsayıcınızı bulutta barındırın.

* [Azure Batch](https://azure.microsoft.com/services/batch/)\
Kapsayıcıları kullanarak yinelenen işlem işleri çalıştırın.

* [Azure Service Fabric](https://azure.microsoft.com/services/service-fabric/)\
Windows Server kapsayıcıları kullanarak .NET uygulamalarını mikro hizmetlere kaldırma, kaydırma ve modernleştirin

* [Azure Container Registry](https://azure.microsoft.com/services/container-registry/)\
Tüm Azure dağıtımı türlerinde kapsayıcı görüntüleri depolayın ve yönetin.

## <a name="next-steps"></a>Sonraki adımlar

* [.NET Core uygulamasını kapsayıya kapsayıtabilecek hakkında bilgi edinin.](build-docker-netcore-container.md)
* [ASP.NET Core uygulamasını kapsayıya kapsayıtabilecek hakkında bilgi edinin.](/aspnet/core/host-and-deploy/docker/building-net-docker-images)
* [ASP.NET Core mikro hizmeti öğrenin öğreticisini deneyin.](https://dotnet.microsoft.com/learn/web/aspnet-microservice-tutorial/intro)
* [Visual Studio 'da kapsayıcı araçları hakkında bilgi edinin](/visualstudio/containers/overview)
