---
title: Kapsayıcılar ve Docker’a Giriş
description: .NET Microservices Mimari Containerized .NET Uygulamaları için | Konteynerve Docker Giriş
ms.date: 08/31/2018
ms.openlocfilehash: 364cbc0ba8149be1873df628a1ca243f420e7d0b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73740053"
---
# <a name="introduction-to-containers-and-docker"></a>Kapsayıcılar ve Docker’a Giriş

Kapsayıcılaştırma, bir uygulamanın veya hizmetin, bağımlılıklarının ve yapılandırmasının (dağıtım bildirimi dosyaları olarak özetlenmiş) kapsayıcı görüntüsü olarak birlikte paketlendiği yazılım geliştirme yaklaşımıdır. Kapsayıcılaştırılmış uygulama bir birim olarak sınanabilir ve ana bilgisayar işletim sistemine (OS) konteyner görüntü örneği olarak dağıtılabilir.

Nakliye konteynerleri malların içindeki kargodan bağımsız olarak gemi, tren veya kamyonla taşınmasına izin verdiği gibi, yazılım konteynerleri de farklı kod ve bağımlılıklar içerebilen standart bir yazılım dağıtım birimi görevi görebilirsiniz. Yazılımı bu şekilde kapsayıcıhale getirme, geliştiricilerin ve BT uzmanlarının bunları çok az veya hiç değişiklik olmayan ortamlar arasında dağıtmasına olanak tanır.

Kapsayıcılar, paylaşılan bir işletim sistemi üzerinde uygulamaları birbirinden yalıtlar. Kapsayıcılaştırılmış uygulamalar, işletim sistemi (Linux veya Windows) üzerinde çalışan bir kapsayıcı ana bilgisayar üzerinde çalışır. Bu nedenle kapsayıcılar sanal makine (VM) görüntülerden çok daha küçük bir ayak izine sahiptir.

Her kapsayıcı, Şekil 2-1'de gösterildiği gibi bir web uygulamasını veya hizmeti nin tamamını çalıştırabilir. Bu örnekte, Docker ana bilgisayar bir kapsayıcı ana bilgisayardır ve App1, App2, Svc 1 ve Svc 2 kapsayıcı uygulamalar veya hizmetlerdir.

![VM veya sunucuda çalışan dört kapsayıcıyı gösteren diyagram.](./media/index/multiple-containers-single-host.png)

**Şekil 2-1**. Konteyner ana bilgisayarda çalışan birden çok kapsayıcı

Konteynerleştirmenin bir diğer yararı da ölçeklenebilirliktir. Kısa vadeli görevler için yeni kapsayıcılar oluşturarak hızla ölçeklendirebilirsiniz. Uygulama açısından bakıldığında, bir görüntüyü anlık olarak (kapsayıcı oluşturma) bir hizmet veya web uygulaması gibi bir işlemi anında oluşturmaya benzer. Ancak güvenilirlik için, birden çok ana bilgisayar sunucusunda aynı görüntünün birden çok örneğini çalıştırdığınızda, genellikle her kapsayıcının (resim örneği) farklı bir ana bilgisayar sunucusunda veya Farklı hata etki alanlarında VM'de çalışmasını istersiniz.

Kısacası, kapsayıcılar tüm uygulama yaşam döngüsü iş akışı boyunca yalıtım, taşınabilirlik, çeviklik, ölçeklenebilirlik ve denetim avantajları sunar. En önemli yararı, Dev ve Ops arasında sağlanan çevrenin izolasyonudur.

>[!div class="step-by-step"]
>[Önceki](../index.md)
>[Sonraki](docker-defined.md)
