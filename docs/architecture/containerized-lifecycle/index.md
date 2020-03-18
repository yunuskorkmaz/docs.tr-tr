---
title: Kapsayıcılar ve Docker’a Giriş
description: Docker kullanmanın temel yararları hakkında üst düzey bir genel bakış elde edin.
ms.date: 02/15/2019
ms.openlocfilehash: 9ac08a64cd2465b4b88a266c1ec0925f37680bf9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73738182"
---
# <a name="introduction-to-containers-and-docker"></a>Konteynerlere giriş ve Docker

*Kapsayıcılaştırma, bir uygulamanın veya hizmetin, bağımlılıklarının ve yapılandırmasının (dağıtım bildirimi dosyaları olarak özetlenmiş) kapsayıcı görüntüsü olarak birlikte paketlendiği yazılım geliştirme yaklaşımıdır. Daha sonra kapsayıcılı uygulamayı bir birim olarak sınayabilir ve kapsayıcı görüntü örneği olarak ana bilgisayar işletim sistemine (OS) dağıtabilirsiniz.*

Nakliye konteynerleri malların içindeki kargodan bağımsız olarak gemi, tren veya kamyonla taşınmasına izin verdiği gibi, yazılım konteynerleri de farklı kod ve bağımlılıklar içerebilen standart bir yazılım dağıtım birimi görevi görebilirsiniz. Yazılımı bu şekilde kapsayıcıhale getirme, geliştiricilerin ve BT uzmanlarının bunları çok az veya hiç değişiklik olmayan ortamlar arasında dağıtmasına olanak tanır.

Kapsayıcılar, paylaşılan bir işletim sistemi üzerinde uygulamaları birbirinden yalıtlar. Kapsayıcılaştırılmış uygulamalar, işletim sistemi (Linux veya Windows) üzerinde çalışan bir kapsayıcı ana bilgisayar üzerinde çalışır. Bu nedenle kaplar sanal makine (VM) görüntülerden çok daha küçük bir ayak izine sahiptir.

Her kapsayıcı, Şekil 1-1'de gösterildiği gibi bir web uygulamasını veya hizmeti nin tamamını çalıştırabilir. Bu örnekte, Docker ana bilgisayar bir kapsayıcı ana bilgisayardır ve App1, App2, Svc1 ve Svc2 kapsayıcı uygulamalar veya hizmetlerdir.

![VM veya sunucuda çalışan dört kapsayıcıyı gösteren diyagram.](./media/index/multiple-containers-single-host.png)

**Şekil 1-1**. Konteyner ana bilgisayarda çalışan birden çok kapsayıcı

Konteynerleştirme den elde edebilirsiniz başka bir yararı ölçeklenebilirlik olduğunu. Kısa vadeli görevler için yeni kapsayıcılar oluşturarak hızla ölçeklendirebilirsiniz. Uygulama açısından bakıldığında, bir görüntüyü anlık olarak (kapsayıcı oluşturma) bir hizmet veya web uygulaması gibi bir işlemi anında oluşturmaya benzer. Ancak güvenilirlik için, birden çok ana bilgisayar sunucusunda aynı görüntünün birden çok örneğini çalıştırdığınızda, genellikle her kapsayıcının (resim örneği) farklı bir ana bilgisayar sunucusunda veya Farklı hata etki alanlarında VM'de çalışmasını istersiniz.

Kısacası, kapsayıcılar tüm uygulama yaşam döngüsü iş akışı boyunca yalıtım, taşınabilirlik, çeviklik, ölçeklenebilirlik ve denetim avantajları sunar. En önemli yararı Dev ve Ops arasında sağlanan çevre yalıtımı.

>[!div class="step-by-step"]
>[Sonraki](what-is-docker.md)
