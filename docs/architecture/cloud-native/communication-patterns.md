---
title: Bulutta yerel iletişim desenleri
description: Bulutta yerel uygulamalarda önemli hizmet iletişim sorunları hakkında bilgi edinin
author: robvet
ms.date: 05/13/2020
ms.openlocfilehash: 3d678df44b5fef68427846e59f446b7408795625
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83614220"
---
# <a name="cloud-native-communication-patterns"></a>Bulutta yerel iletişim desenleri

Bir bulutta yerel sistem oluştururken, iletişim önemli bir tasarım kararı haline gelir. Ön uç istemci uygulaması, arka uç mikro hizmeti ile nasıl iletişim kurar? Arka uç mikro hizmetleri birbirleriyle nasıl iletişim kurar? Bulutta yerel uygulamalarda iletişim uygularken dikkate alınması gereken ilkeler, desenler ve en iyi uygulamalar nelerdir?

## <a name="communication-considerations"></a>İletişim konuları

Tek parçalı bir uygulamada, iletişim basittir. Kod modülleri bir sunucuda aynı yürütülebilir alanda (işlem) birlikte yürütülür. Bu yaklaşım, her şey paylaşılan bellekte birlikte çalıştığı için performans avantajlarına sahip olabilir, ancak bakım, geliştirilmesi ve ölçeklendirilmesi zor olan sıkı şekilde bağlanmış bir koda neden olur.

Bulutta yerel sistemler, çok küçük ve bağımsız mikro hizmetlerden oluşan mikro hizmet tabanlı bir mimari uygular. Her mikro hizmet ayrı bir işlemde yürütülür ve genellikle bir *kümeye*dağıtılan bir kapsayıcı içinde çalışır.

Bir küme, yüksek oranda kullanılabilir bir ortam oluşturmak için bir sanal makine havuzunu birlikte gruplandırır. Kapsayıcılı mikro hizmetleri dağıtmaktan ve yönetmekten sorumlu olan bir Orchestration aracıyla yönetilirler. Şekil 4-1, tam olarak yönetilen [Azure Kubernetes hizmetleriyle](https://docs.microsoft.com/azure/aks/intro-kubernetes)Azure bulutuna dağıtılan bir [Kubernetes](https://kubernetes.io) kümesini gösterir.

![Azure 'da bir Kubernetes kümesi](./media/kubernetes-cluster-in-azure.png)

**Şekil 4-1**. Azure 'da bir Kubernetes kümesi

Mikro hizmetler, küme genelinde API 'Ler ve mesajlaşma teknolojileri aracılığıyla birbirleriyle iletişim kurar.

Birçok avantaj sağlarken, mikro hizmetler ücretsiz öğle yemeği değildir. Bileşenler arasındaki yerel işlem içi Yöntem çağrıları artık ağ çağrılarıyla değiştirilmiştir. Her mikro hizmet, sisteminize karmaşıklık ekleyen bir ağ protokolü üzerinden iletişim kurmalıdır:

- Ağ tıkanıklığı, gecikme süresi ve geçici hatalar, sabit bir konudur.

- Dayanıklılık (diğer bir deyişle, başarısız isteklerin yeniden denenme) gereklidir.

- Bazı çağrıların tutarlı durumda tutulması için [ıdempotent](https://www.restapitutorial.com/lessons/idempotency.html) olması gerekir.

- Her mikro hizmet için çağrı kimlik doğrulaması ve yetkilendirme gerekir.

- Her iletinin serileştirilmesi ve ardından seri durumdan çıkarılmalıdır ve bu pahalı olabilir.

- İleti şifreleme/şifre çözme önemli hale gelir.

[.Net mikro hizmetleri: Kapsayıcılı .NET uygulamaları Için](https://dotnet.microsoft.com/download/thank-you/microservices-architecture-ebook)Microsoft 'tan ücretsiz olarak sunulan mimari, mikro hizmet uygulamalarına yönelik iletişim desenlerinin ayrıntılı bir kapsamını sunmaktadır. Bu bölümde, Azure bulutu 'nda bulunan uygulama seçenekleriyle birlikte bu desenlere yönelik yüksek düzeyde bir genel bakış sunuyoruz.

Bu bölümde, önce ön uç uygulamaları ve arka uç mikro hizmetleri arasındaki iletişimi ele alacağız. Ardından arka uç mikro hizmetlerinin birbirleriyle iletişim kurmasına bakacağız. Yukarı ve gRPC iletişim teknolojisini keşfereceğiz. Son olarak, hizmet kafesi teknolojisini kullanarak yeni yenilikçi iletişim desenleri inceleyeceğiz. Ayrıca, Azure bulutunun bulut Yerel iletişimini desteklemek için farklı türlerde *yedekleme hizmetleri* sağladığını de göreceğiz.

>[!div class="step-by-step"]
>[Önceki](other-deployment-options.md) 
> [Sonraki](front-end-communication.md)
