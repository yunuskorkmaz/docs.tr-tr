---
title: Docker'a Giriş
description: Bu makalede, bir .NET Core uygulaması bağlamında Docker'a giriş ve genel bakış sağlar.
ms.date: 03/20/2019
ms.custom: mvc
ms.openlocfilehash: eedfd1e7c1b361beb9d4f271e739657ef5e894a6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "78157797"
---
# <a name="introduction-to-net-and-docker"></a>.NET ve Docker’a Giriş

.NET Core, Docker konteynerinde kolayca çalıştırılabilir. Kapsayıcılar, uygulamanızı ana bilgisayar sisteminin geri kalanından izole etmek, sadece çekirdeği paylaşmak ve uygulamanız için verilen kaynakları kullanarak hafif bir yol sağlar. Docker'ı bilmiyorsanız, Docker'ın [genel bakış belgelerini](https://docs.docker.com/engine/docker-overview/)okumanız önerilir.

Docker nasıl yüklenir hakkında daha fazla bilgi için [Docker Desktop: Community Edition](https://www.docker.com/products/docker-desktop)için indirme sayfasına bakın.

## <a name="docker-basics"></a>Docker temelleri

Aşina olmanız gereken birkaç kavram vardır. Docker istemcisi, görüntüleri ve kapsayıcıları yönetmek için kullanabileceğiniz bir CLI'ye sahiptir. Daha önce de belirtildiği gibi, [Docker genel bakış](https://docs.docker.com/engine/docker-overview/) belgelerini okumak için zaman ayırmalısınız.

### <a name="images"></a>Görüntüler

Görüntü, kapsayıcının temelini oluşturan dosya sistemi değişikliklerinin sıralı bir koleksiyonudur. Görüntünün bir durumu yoktur ve salt okunur. Çok zaman bir görüntü başka bir görüntü dayanmaktadır, ancak bazı özelleştirme ile. Örneğin, uygulamanız için yeni bir resim oluşturduğunuzda, bu görüntüyü zaten .NET Core çalışma süresini içeren varolan bir görüntüye dayandırmış olursunuz.

Kapsayıcılar görüntülerden oluşturulduğundan, görüntülerin kapsayıcı başladığında çalışan bir çalışma parametreleri kümesi (başlangıç yürütülebilirliği gibi) vardır.

### <a name="containers"></a>Kapsayıcılar

Kapsayıcı, görüntünün ondan biri. Resminizi oluştururken, uygulamanızı ve bağımlılıklarınızı dağıtırsınız. Daha sonra, birden çok kapsayıcı anlık, her biri birbirinden izole edilebilir. Her kapsayıcı örneğinin kendi dosya sistemi, belleği ve ağ arabirimi vardır.

### <a name="registries"></a>Kayıt Defterleri

Konteyner kayıtları görüntü depolarının bir koleksiyonudur. Resimlerinizi bir kayıt defteri resmine dayandırabilirsiniz. Kapsayıcıları doğrudan kayıt defterindeki bir görüntüden oluşturabilirsiniz. [Docker kaplar, görüntüler ve kayıt defterleri arasındaki ilişki,](../../architecture/microservices/container-docker-introduction/docker-containers-images-registries.md) [konteyner uygulamaları veya mikro hizmetleri tasarlarken ve inşa](../../architecture/microservices/architect-microservice-container-applications/index.md)ederken önemli bir kavramdır. Bu yaklaşım, geliştirme ve dağıtım arasındaki süreyi büyük ölçüde kısaltır.

Docker'ın [Docker Hub'da](https://hub.docker.com/) kullanabileceğiniz bir genel kayıt defteri vardır. [.NET Core ile ilgili görüntüler](https://hub.docker.com/_/microsoft-dotnet-core/) Docker Hub'da listelenir.

Microsoft Kapsayıcı Kayıt Defteri (MCR), Microsoft tarafından sağlanan kapsayıcı görüntülerinin resmi kaynağıdır. MCR, genel olarak çoğaltılan görüntüler sağlamak için Azure CDN'de oluşturulmuştür. Ancak, MCR'nin genel kullanıma açık bir web sitesi yoktur ve Microsoft tarafından sağlanan kapsayıcı görüntüleri hakkında bilgi edinmenin birincil yolu [Microsoft Docker Hub sayfalarından](https://hub.docker.com/_/microsoft-dotnet-core/)geçer.

### <a name="dockerfile"></a>Dockerdosyası

**Dockerfile,** görüntü oluşturan bir yönerge kümesini tanımlayan bir dosyadır. **Dockerfile'daki** her yönerge görüntüde bir katman oluşturur. Çoğunlukla, görüntüyü yeniden oluştururken, yalnızca değiştirilen katmanlar yeniden oluşturulur. **Dockerdosyası** başkalarına dağıtılabilir ve yeni bir görüntüyü sizin oluşturduğunuz şekilde yeniden oluşturmalarına olanak tanır. Bu, resmin nasıl oluşturulacağına ilişkin *yönergeleri* dağıtmanıza olanak sağlarken, resminizi dağıtmanın ana yolu onu bir kayıt defterine yayımlamaktır.

## <a name="net-core-images"></a>.NET Çekirdek görüntüleri

Resmi .NET Core Docker görüntüleri Microsoft Konteyner Kayıt Defteri'nde (MCR) yayınlanır ve [Microsoft .NET Core Docker Hub deposunda](https://hub.docker.com/_/microsoft-dotnet-core/)keşfedilebilir. Her depo, kullanabilirsiniz .NET (SDK veya Runtime) ve işletim sistemi farklı kombinasyonları için görüntüler içerir.

Microsoft, belirli senaryolar için özel leştirilmiş görüntüler sağlar. Örneğin, [ASP.NET Core deposu,](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) üretimde Core uygulamaları ASP.NET çalıştırmak için oluşturulmuş görüntüler sağlar.

## <a name="azure-services"></a>Azure hizmetleri

Çeşitli Azure hizmetleri kapsayıcıları destekler. Uygulamanız için bir Docker görüntüsü oluşturur ve aşağıdaki hizmetlerden birine dağıtırsınız:

- [Azure Kubernetes Servisi (AKS)](https://azure.microsoft.com/services/kubernetes-service/)\
Kubernetes kullanarak Linux konteynerlerini ölçeklendirin ve düzenleyin.

- [Azure Uygulama Hizmeti](https://azure.microsoft.com/services/app-service/containers/)\
PaaS ortamında Linux kapsayıcılarını kullanarak web uygulamalarını veya API'leri dağıtın.

- [Azure Kapsayıcı Örnekleri](https://azure.microsoft.com/services/container-instances/)\
Üst düzey yönetim hizmetleri olmadan kabınızı bulutta barındırın.

- [Azure Toplu İş](https://azure.microsoft.com/services/batch/)\
Kapsayıcıları kullanarak yinelenen işlem işlerini çalıştırın.

- [Azure Servis Kumaşı](https://azure.microsoft.com/services/service-fabric/)\
Windows Server kapsayıcılarını kullanarak .NET uygulamalarını mikro hizmetlere kaldırın, kaydırın ve modernleştirin.

- [Azure Kapsayıcı Kayıt Defteri](https://azure.microsoft.com/services/container-registry/)\
Kapsayıcı görüntülerini tüm Azure dağıtım türlerinde depolayın ve yönetin.

## <a name="next-steps"></a>Sonraki adımlar

- [Bir .NET Core uygulamasını nasıl kaplaştırılamayı öğrenin.](build-container.md)
- [ASP.NET Core uygulamasını nasıl kaplaştırılamayı öğrenin.](/aspnet/core/host-and-deploy/docker/building-net-docker-images)
- [Learn ASP.NET Core Microservice öğreticisini deneyin.](https://dotnet.microsoft.com/learn/web/aspnet-microservice-tutorial/intro)
- [Visual Studio'da Konteyner Araçları hakkında bilgi edinin](/visualstudio/containers/overview)
