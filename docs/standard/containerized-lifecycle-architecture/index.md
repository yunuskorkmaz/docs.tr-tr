---
title: Kapsayıcılar ve Docker giriş
description: Microsoft Platformu ve araçları ile kapsayıcılı Docker uygulama yaşam döngüsü
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/22/2017
ms.openlocfilehash: e9f81c5fecc06b19ebd84cc4b2cc232686768a90
ms.sourcegitcommit: 979597cd8055534b63d2c6ee8322938a27d0c87b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/29/2018
ms.locfileid: "37106638"
---
# <a name="introduction-to-containers-and-docker"></a>Kapsayıcılar ve Docker giriş

Kapsayıcıyla taşıma, bir uygulama veya hizmet, bağımlılıklarını ve (dağıtım bildirim dosyaları olarak soyutlanır) yapılandırmasıyla birlikte bir kapsayıcı görüntüsü olarak paketlenmiş yazılım geliştirme için bir yaklaşımdır. Ardından bir birim olarak kapsayıcılı uygulamayı test etme ve ana bilgisayar işletim sistemi için bir kapsayıcı görüntü örneği olarak dağıtabilirsiniz.

Yalnızca sevk, tren veya bunları içinde Kargo bakılmaksızın kamyon mal taşımak için standartlaştırılmış kapsayıcıları sevkiyat endüstri kullanır gibi yazılım kapsayıcıları farklı kodu ve bağımlılıklarını içeren bir yazılım standart birimi davranır. Yazılım kapsayıcılarına yerleştirme, geliştiriciler ve BT Uzmanları bu kapsayıcıların çok az kayıpla veya hiç değişiklik ortamlarıyla üzerinden dağıtmak mümkün kılar.

Kapsayıcılar ayrıca paylaşılan bir işletim sistemine (OS) uygulamaları birbirinden yalıtmak. Kapsayıcılı uygulamaları sırayla (Linux veya Windows) işletim sisteminde çalışan bir kapsayıcı konak üzerinde çalışır. Bu nedenle, sanal makine (VM) görüntüleri daha önemli ölçüde daha küçük bir yer kapsayıcıları sahip.

Her bir kapsayıcıdaki tüm web uygulaması veya hizmeti, Şekil 1-1'de gösterildiği gibi çalıştırabilirsiniz.

![](./media/image1.png)

Şekil 1-1: bir kapsayıcı ana bilgisayarında çalışan birden çok kapsayıcı

Bu örnekte, Docker ana kapsayıcı ana bilgisayar ve uygulama, uygulama 2, Svc 1, Svc 2 kapsayıcılı uygulamalar veya hizmetler şunlardır: 1 ve.

Kapsayıcıyla taşıma türetilen başka bir avantaj ölçeklenebilirlik olmalıdır. Hızlı bir şekilde kısa vadeli görevler için yeni kapsayıcılar oluşturarak genişletme. Açısından bir uygulama, *görüntü başlatmasını* (bir kapsayıcı oluşturma) benzer bir hizmeti veya web uygulaması gibi bir işlem örneği için. Birden çok ana bilgisayar sunucuları arasında aynı görüntü birden çok örneğini çalıştırdığınızda güvenilirliği, ancak genellikle her kapsayıcı (bir farklı ana bilgisayar sunucusu çalıştırmak için görüntü örneği) veya VM farklı hata etki alanlarında istediğiniz.

Kısacası, kapsayıcıları tüm uygulama yaşam döngüsü iş akışı yalıtımı, taşınabilirlik, çeviklik, ölçeklenebilirlik ve denetim avantajları sunar. En önemli avantajı geliştirme ve Ops arasında sağlanan yalıtım ' dir.


>[!div class="step-by-step"]
[Next](what-is-docker.md)
