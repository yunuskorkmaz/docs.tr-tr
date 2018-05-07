---
title: Kapsayıcılar ve Docker giriş
description: Kapsayıcılı .NET uygulamaları için .NET mikro mimarisi | Kapsayıcılar ve Docker giriş
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.openlocfilehash: c1f78a8904270123188367a01bddbcac3f7f1b7f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="introduction-to-containers-and-docker"></a>Kapsayıcılar ve Docker giriş

Kapsayıcıyla taşıma, bir uygulama veya hizmet, bağımlılıklarını ve (dağıtım bildirim dosyaları olarak soyutlanır) yapılandırmasıyla birlikte bir kapsayıcı görüntüsü olarak paketlenmiş yazılım geliştirme için bir yaklaşımdır. Kapsayıcılı uygulama bir birim olarak test ve ana bilgisayar işletim sistemi (OS) için bir kapsayıcı görüntü örneği olarak dağıtılabilir.

Yalnızca sevkiyat kapsayıcıları gemi, tren veya kamyon içinde Kargo bakılmaksızın tarafından taşınmasını mal izin olarak yazılım kapsayıcıları farklı kodu ve bağımlılıklarını içeren bir yazılım standart birimi olarak hareket. Bu şekilde yazılım containerizing, geliştiriciler ve BT uzmanları bunları çok az kayıpla veya hiç değişiklik ortamlarıyla üzerinden dağıtmak etkinleştirir.

Kapsayıcılar ayrıca birbirinden uygulamalar, paylaşılan bir işletim sistemine yalıtma. Kapsayıcılı uygulamaları sırayla işletim sisteminde (Linux veya Windows) çalıştıran bir kapsayıcı konak üzerinde çalışır. Kapsayıcılar, bu nedenle sanal makine (VM) görüntüleri daha önemli ölçüde daha küçük bir yer gerekir.

Her kapsayıcı, Şekil 2-1'de gösterildiği gibi tüm web uygulaması veya bir hizmet çalıştırabilirsiniz. Bu örnekte, Docker ana bir kapsayıcı konak ve App1 ve App2, Svc 1 ve Svc 2 kapsayıcılı uygulamalar veya hizmetler şunlardır.

![](./media/image1.png)

**Şekil 2-1**. Bir kapsayıcı ana bilgisayarında çalışan birden çok kapsayıcı

Kapsayıcıyla taşıma başka bir yararı ölçeklenebilirlik özelliğidir. Out hızlı bir şekilde kısa vadeli görevler için yeni kapsayıcılar oluşturarak ölçeklendirebilirsiniz. Bir uygulama açısından bakıldığında, (bir kapsayıcı oluşturma) bir görüntü örneği bir hizmet veya web uygulaması gibi bir işlem örneği için benzer. Birden çok ana bilgisayar sunucuları arasında aynı görüntü birden çok örneğini çalıştırdığınızda güvenilirliği, ancak genellikle her kapsayıcı (bir farklı ana bilgisayar sunucusu çalıştırmak için görüntü örneği) veya VM farklı hata etki alanlarında istediğiniz.

Kısacası, kapsayıcıları tüm uygulama yaşam döngüsü iş akışı yalıtımı, taşınabilirlik, çeviklik, ölçeklenebilirlik ve denetim avantajları sunar. En önemli avantajı geliştirme ve Ops arasında sağlanan yalıtım ' dir.


>[!div class="step-by-step"]
[Önceki] (.. / index.md) [sonraki] (docker-defined.md)
