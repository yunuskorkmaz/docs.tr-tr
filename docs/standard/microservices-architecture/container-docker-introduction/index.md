---
title: Kapsayıcılar ve Docker’a Giriş
description: Kapsayıcılı .NET uygulamaları için .NET mikro hizmet mimarisi | Kapsayıcılar ve Docker'a giriş
ms.date: 08/31/2018
ms.openlocfilehash: cb6244939f6ae89ba1dc824b55a21d1e010cef5e
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65644510"
---
# <a name="introduction-to-containers-and-docker"></a>Kapsayıcılar ve Docker’a Giriş

Kapsayıcı içinde bir uygulama veya hizmeti ve bağımlılıklarını yapılandırmasıyla (dağıtım bildirim dosyaları soyutlanır) bir arada bir kapsayıcı görüntüsü paketlenmiş yazılım geliştirme için bir yaklaşımdır. Kapsayıcılı uygulama, bir birim olarak test edilmiş ve bir kapsayıcı görüntü örneğinin konak işletim sistemi (OS) olarak dağıtılır.

Yalnızca ürün sevk, train veya kargo içinde bağımsız olarak kamyon taşınmasını nakliye izin vermek gibi yazılım kapsayıcıları farklı kodu ve bağımlılıkları içerebilir, yazılım dağıtımının standart bir birim olarak davranır. Bu şekilde yazılım kapsayıcılı hale getirmek, geliştiriciler ve BT uzmanları onları ortamlarında çok az kayıpla veya hiç değişiklik ile dağıtmak etkinleştirir.

Kapsayıcılar ayrıca paylaşılan bir işletim sisteminde uygulamaları birbirinden yalıtın. Kapsayıcılı uygulamaların, işletim sisteminde (Linux veya Windows) sırayla çalıştırılan bir kapsayıcı konağı üzerinde çalıştırın. Kapsayıcılar, bu nedenle sanal makine (VM) görüntülerini daha önemli ölçüde daha küçük bir ayak izini içerir.

Her kapsayıcı, tüm web uygulaması veya hizmeti, Şekil 2-1'de gösterildiği gibi çalıştırabilirsiniz. Bu örnekte, Docker ana bir kapsayıcı konağı ve App1 ve App2, Svc'de 1 ve Svc 2 kapsayıcılı uygulamalar veya hizmetler şunlardır.

![İki uygulama ve işletim sisteminde bir VM veya fiziksel sunucu üzerinde çalışan iki Hizmetleri](./media/image1.png)

**Şekil 2-1**. Bir kapsayıcı konağı üzerinde çalışan birden çok kapsayıcı

Kapsayıcı başka bir faydası ölçeklenebilirlik özelliğidir. Hızlı bir şekilde yeni kapsayıcılar için kısa vadeli görevleri oluşturarak ölçeği genişletebilirsiniz. Bir uygulama açısından bakıldığında, örnekleme (bir kapsayıcı oluşturma) görüntü hizmeti veya web uygulaması gibi bir işlem örnekleme için benzerdir. Birden çok ana bilgisayar sunucuları arasında aynı görüntüsünün birden çok örneği çalıştırdığınızda güvenilirliği, ancak genellikle her bir kapsayıcı (farklı bir ana sunucu çalıştırmak için görüntü örnek) veya VM farklı hata etki alanlarında istersiniz.

Kısacası, kapsayıcılar arasında tüm uygulama yaşam döngüsü iş akışı yalıtımı, taşınabilirliği, çevikliği, ölçeklenebilirlik ve denetim avantajlarını sunar. En önemli avantajı, geliştirme ve Ops sağlanan ortamın yalıtım olur.

>[!div class="step-by-step"]
>[Önceki](../index.md)
>[İleri](docker-defined.md)
