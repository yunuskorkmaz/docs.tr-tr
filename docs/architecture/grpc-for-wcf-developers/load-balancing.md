---
title: WCF geliştiricileri için Yük Dengeleme gRPC-gRPC
description: GRPC hizmetleriyle çalışmak için bir yük dengeleyici seçme.
author: markrendle
ms.date: 09/02/2019
ms.openlocfilehash: 18965b9c4765ac693c6ba36ad3ea9848ce858a5c
ms.sourcegitcommit: 337bdc5a463875daf2cc6883e5a2da97d56f5000
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/24/2019
ms.locfileid: "72846620"
---
# <a name="load-balancing-grpc"></a>GRPC yük dengelemesi

Bir gRPC uygulamasının tipik bir dağıtımı, hizmetin bir dizi özdeş örneğini içerir, bu da esnekliği ve yatay ölçeklenebilirlik sağlar. Tüm kullanılabilir kaynakların tam kullanımını sağlamak için bu örneklerde dağıtılmış gelen istek yükünü dengeleyin. Bu yük dengelemeyi istemcide görünmez hale getirmek için, istemcilerden gelen istekleri işlemek ve arka uç örneklerine yönlendirmek için bir proxy yük dengeleyici sunucusu kullanılması yaygındır.

Yük dengeleyiciler üzerinde çalıştıkları *katmana* göre sınıflandırılmaktadır. Katman 4 yük dengeleyiciler *Aktarım* düzeyinde (ÖRNEĞIN, TCP yuvaları, bağlantılar ve paketler) çalışır. Katman 7 yük dengeleyiciler, özel olarak gRPC uygulamaları için HTTP/2 isteklerini işleyerek *uygulama* düzeyinde çalışır.

## <a name="l4-load-balancers"></a>L4 yük dengeleyiciler

Bir L4 yük dengeleyici bir istemciden gelen TCP bağlantı isteğini kabul eder, arka uç örneklerinden birine başka bir bağlantı açar ve gerçek bir işleme olmadan iki bağlantı arasında verileri kopyalar. L4 mükemmel performans ve düşük gecikme süresi, ancak çok az denetim veya zeka sağlar. İstemci bağlantıyı açık sakladığı sürece tüm istekler aynı arka uç örneğine yönlendirilir.

Bir L4 yük dengeleyiciye bir örnek [Azure Load Balancer](https://azure.microsoft.com/services/load-balancer/).

## <a name="l7-load-balancers"></a>L7 yük dengeleyiciler

Bir L7 yük dengeleyici gelen HTTP/2 isteklerini ayrıştırır ve bağlantının istemci tarafından ne kadar süreceğine bakılmaksızın bunları istek temelli olarak bir istek temelinde, arka uç örneklerine geçirir.

L7 yük dengeleyiciler örnekleri şunlardır:

- [NGINX](https://www.nginx.com/)
- [HAproxy](https://www.haproxy.com/)
- [Traefik](https://traefik.io/)

Bir Thumb kuralı olarak, L7 yük dengeleyiciler gRPC ve diğer HTTP/2 uygulamaları için en iyi seçenektir (ve genellikle HTTP uygulamaları için). L4 yük dengeleyiciler gRPC uygulamalarıyla *çalışır* , ancak düşük gecikme süresi ve düşük ek yük önemli öneme sahip olduğunda özellikle faydalıdır.

> [!IMPORTANT]
> Bu yazma sırasında, tüm L7 yük dengeleyiciler, gRPC Hizmetleri için gerekli olan HTTP/2 belirtiminin, sondaki üstbilgiler gibi tüm parçalarını desteklemez.

TLS şifrelemesini kullanırken, yük dengeleyiciler TLS bağlantısını sonlandırabilir ve şifrelenmemiş istekleri arka uç uygulamasına geçirebilir veya şifreli isteği bir daha geçirebilir. Her iki durumda da yük dengeleyicinin sunucunun ortak ve özel anahtarıyla yapılandırılması gerekir; böylece, işleme isteklerinin şifresini çözebilirler.

Arka uç hizmetleriniz ile HTTP/2 isteklerini işlemek üzere nasıl yapılandıracağınızı öğrenmek için tercih ettiğiniz yük dengeleyiciye yönelik belgelere bakın.

## <a name="load-balancing-within-kubernetes"></a>Kubernetes içinde yük dengeleme

Kubernetes 'deki iç hizmetlerde yük dengelemenin tartışılması için [hizmet kafesleri bölümüne](service-mesh.md) bakın.

>[!div class="step-by-step"]
>[Önceki](service-mesh.md)
>[İleri](application-performance-management.md)
