---
title: Docker giriş
description: Bu makale Docker için bir .NET Core uygulaması bağlamında bir giriş ve genel bakış sağlar.
ms.date: 03/20/2019
ms.custom: mvc, seodec18
ms.openlocfilehash: acf1307c241d9462278bc0fce5cf59fdde0750a3
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59480735"
---
# <a name="introduction-to-net-and-docker"></a>.NET ve Docker'a giriş

.NET core, Docker kapsayıcısında kolayca çalıştırabilirsiniz. Kapsayıcılar, uygulamanızın çekirdek paylaşma ve uygulamanıza verilen kaynaklarını kullanan konak sistemi geri kalanından ayırmak için basit bir yol sağlar. Docker ile bilmiyorsanız, Docker kişinin okuma önerilir [genel bakış belgeleri](https://docs.docker.com/engine/docker-overview/).

Docker yükleme hakkında daha fazla bilgi için bkz: indirme sayfasını [Docker Masaüstü: Community sürümü](https://www.docker.com/products/docker-desktop).

## <a name="docker-basics"></a>Docker temel bilgileri

Bilmeniz birkaç kavram vardır. Docker istemci görüntüleri ve kapsayıcılar yönetmek için kullandığınız bir komut satırı arabirimi programı vardır. Daha önce belirtildiği gibi okumak için zaman atmanız [Docker'a genel bakış](https://docs.docker.com/engine/docker-overview/) belgeleri. 

### <a name="images"></a>Görüntüler

Görüntüyü bir kapsayıcı temelini dosya sistemi değişikliklerini sıralı bir koleksiyonudur. Görüntü bir duruma sahip değil ve salt okunur. Başka bir görüntü, ancak bazı özelleştirme çok zaman görüntüyü temel alır. Uygulamanız için yeni bir görüntü oluşturun, örneğin, .NET Core çalışma zamanı zaten içeren mevcut bir görüntü üzerinde temel.

Kapsayıcı görüntülerini oluşturulduğundan, görüntüleri kapsayıcı başlatıldığında çalıştırılan çalışma parametreler (örneğin, bir başlangıç yürütülebilir dosya) kümesine sahiptir.

### <a name="containers"></a>Kapsayıcılar

Bir kapsayıcı görüntüyü çalıştırılabilir bir örneğidir. Görüntünüzü oluşturmak gibi uygulamayı ve bağımlılıkları dağıtın. Birden çok kapsayıcı örneği sonra her birbirinden yalıtılır. Her kapsayıcı örneği kendi dosya sistemi, bellek ve ağ arabirimi var.

### <a name="registries"></a>kayıt defterleri

Kapsayıcı kayıt defterleri, görüntü deposu koleksiyonudur. Bir kayıt defteri görüntüsünde görüntülerinizi temel alabilir. Doğrudan kayıt defterindeki bir görüntüden kapsayıcılar oluşturabilirsiniz. [Docker kapsayıcıları, görüntüleri ve kayıt defterleri arasındaki ilişki](../../standard/microservices-architecture/container-docker-introduction/docker-containers-images-registries.md) önemli bir kavramdır olduğunda [tasarlama ve oluşturma kapsayıcılı uygulamalar veya mikro Hizmetler](../../standard/microservices-architecture/architect-microservice-container-applications/index.md). Bu yaklaşım, geliştirme ve dağıtım arasındaki süreyi önemli ölçüde kısaltır.

Docker, barındırılan genel bir kayıt defteri sahip [Docker Hub](https://hub.docker.com/) kullanabileceğiniz. [.NET core ilgili görüntüleri](https://hub.docker.com/_/microsoft-dotnet-core/) Docker Hub listelenir. 

Microsoft kapsayıcı kayıt defteri (MCR) Microsoft tarafından sağlanan kapsayıcı görüntülerini resmi kaynağıdır. MCR genel olarak çoğaltılmasına görüntüleri sağlamak için Azure CDN'de yerleşik olarak bulunur. Ancak, MCR genel kullanıma yönelik bir Web sitesi yok ve Microsoft tarafından sağlanan kapsayıcı görüntüleri hakkında bilgi edinmek için birincil yollarından biri sayesinde [Microsoft Docker Hub sayfaları](https://hub.docker.com/_/microsoft-dotnet-core/).

### <a name="dockerfile"></a>Dockerfile

A **Dockerfile** , görüntüyü oluşturan yönerge kümesini tanımlayan bir dosyadır. Her yönerge **Dockerfile** görüntüde bir katman oluşturur. Görüntüyü yeniden oluşturduğunuzda çoğunlukla, değişen katmanları yeniden oluşturulur. **Dockerfile** başkalarına dağıtılabilir ve veren aynı şekilde yeni bir görüntü oluşturmak için yeniden oluşturmak için oluşturduğunuz. Bu sayede dağıtmak sırada *yönergeleri* görüntünüzü dağıtmak için ana yol görüntü oluşturmak nasıl bir kayıt defterine yayımlamak için açıktır.

## <a name="net-core-images"></a>.NET core görüntüleri

Resmi .NET Core Docker görüntüleri Microsoft kapsayıcı kayıt defteri (MCR) yayımlanır ve konumunda bulunabilir [Microsoft .NET Core, Docker Hub deposundaki](https://hub.docker.com/_/microsoft-dotnet-core/). Her depo görüntüler için kullanabileceğiniz bir işletim sistemi ve .NET (SDK'sı veya çalışma zamanı) farklı birleşimlerini içerir. 

Microsoft, belirli senaryolar için uyarlanmış görüntüleri sağlar. Örneğin, [ASP.NET Core depo](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) ASP.NET Core uygulamaları üretim ortamında çalıştırmak için oluşturulan görüntüleri sağlar.

## <a name="azure-services"></a>Azure Hizmetleri

Çeşitli Azure Hizmetleri, kapsayıcıları destekler. Uygulamanız için bir Docker görüntüsü oluşturun ve aşağıdaki hizmetlerden biri dağıtın:

* [Azure Kubernetes Service'i (AKS)](https://azure.microsoft.com/services/kubernetes-service/)\
Ölçeklendirin ve Kubernetes kullanarak Linux kapsayıcıları düzenleyin.

* [Azure uygulama hizmeti](https://azure.microsoft.com/services/app-service/containers/)\
Web uygulamaları veya API'leri bir PaaS ortamında Linux kapsayıcıları kullanarak dağıtın.

* [Azure Container Instances](https://azure.microsoft.com/services/container-instances/)\
Kapsayıcınızı daha yüksek düzeydeki tüm Yönetim Hizmetleri gerektirmeden bulutta barındırın.

* [Azure Batch](https://azure.microsoft.com/services/batch/)\
Kapsayıcıları kullanarak yinelenen işlem işlerini çalıştırın.

* [Azure Service Fabric](https://azure.microsoft.com/services/service-fabric/)\
Windows Server kapsayıcıları kullanarak mikro hizmetler için .NET uygulamalarını modernleştirme kaldırın ve kaydırma

* [Azure kapsayıcı kayıt defteri](https://azure.microsoft.com/services/container-registry/)\
Store ve tüm Azure dağıtımı türlerinde kapsayıcı görüntülerini yönetin.

## <a name="next-steps"></a>Sonraki adımlar

* [.NET Core uygulamasını kapsayıcılı hale getirme hakkında bilgi edinin.](build-docker-netcore-container.md)
* [ASP.NET Core mikro hizmet öğrenin öğreticisini deneyin.](https://dotnet.microsoft.com/learn/web/aspnet-microservice-tutorial/intro)
