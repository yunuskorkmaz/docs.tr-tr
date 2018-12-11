---
title: Kapsayıcılar ve Docker'a giriş
description: Microsoft Platformu ve araçları ile kapsayıcı Docker uygulaması yaşam
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/22/2017
ms.openlocfilehash: c2a6b9802bbb995939d33c5c40ef9c1afa1620e5
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53148827"
---
# <a name="introduction-to-containers-and-docker"></a>Kapsayıcılar ve Docker'a giriş

Kapsayıcı içinde bir uygulama veya hizmeti ve bağımlılıklarını yapılandırmasıyla (dağıtım bildirim dosyaları soyutlanır) bir arada bir kapsayıcı görüntüsü paketlenmiş yazılım geliştirme için bir yaklaşımdır. Daha sonra bir birim olarak kapsayıcılı uygulamayı test etme ve bir kapsayıcı görüntü örneğinin konak işletim sistemi olarak dağıtabilirsiniz.

Yalnızca ürün sevk, train veya kargo içindeki ne olursa olsun, kamyon taşımak için standartlaştırılmış kapsayıcıları sevkiyat sektör kullandığı yazılım kapsayıcıları farklı kodu ve bağımlılıkları içeren bir yazılım standart birimi davranır. Yazılım kapsayıcılarına yerleştirme ortamlarında çok az kayıpla veya hiç değişiklik ile Bu kapsayıcıları dağıtmak, geliştiriciler ve BT uzmanları için mümkün kılar.

Kapsayıcılar Ayrıca, paylaşılan bir işletim sistemi (OS) uygulamaları birbirinden yalıtın. Kapsayıcılı uygulamaların, işletim sisteminde (Linux veya Windows) sırayla çalışır bir kapsayıcı konağı üzerinde çalıştırın. Bu nedenle, kapsayıcılar, sanal makine (VM) görüntülerini daha önemli ölçüde daha küçük bir ayak izini içerir.

Her kapsayıcı, tüm web uygulaması veya hizmeti, Şekil 1-1'de gösterildiği gibi çalıştırabilirsiniz.

![](./media/image1.png)

Şekil 1-1: Bir kapsayıcı konağı üzerinde çalışan birden çok kapsayıcı

Bu örnekte, Docker ana bir kapsayıcı konağı ve kapsayıcılı uygulamalar veya hizmetler uygulama 1, uygulama 2, Svc'de 1 ve Svc 2'dir.

Kapsayıcı türetilip bir diğer avantajı ölçeklenebilirlik özelliğidir. Hızla yeni kapsayıcılar için kısa vadeli görevleri oluşturarak ölçeklendirme. Bir uygulama açısından, *görüntü örnekleme* (bir kapsayıcı oluşturma), bir hizmeti veya web uygulaması gibi bir işlem örnekleme için benzerdir. Birden çok ana bilgisayar sunucuları arasında aynı görüntüsünün birden çok örneği çalıştırdığınızda güvenilirliği, ancak genellikle her bir kapsayıcı (farklı bir ana sunucu çalıştırmak için görüntü örnek) veya VM farklı hata etki alanlarında istersiniz.

Kısacası, kapsayıcılar arasında tüm uygulama yaşam döngüsü iş akışı yalıtımı, taşınabilirliği, çevikliği, ölçeklenebilirlik ve denetim avantajlarını sunar. En önemli avantajı, geliştirme ve Ops sağlanan yalıtım içindir.

>[!div class="step-by-step"]
>[Next](what-is-docker.md)