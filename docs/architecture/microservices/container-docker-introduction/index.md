---
title: Kapsayıcılar ve Docker’a Giriş
description: Kapsayıcılı .NET uygulamaları için .NET mikro hizmetleri mimarisi | Kapsayıcılara ve Docker 'a giriş
ms.date: 08/31/2018
ms.openlocfilehash: cb6244939f6ae89ba1dc824b55a21d1e010cef5e
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/30/2019
ms.locfileid: "70296161"
---
# <a name="introduction-to-containers-and-docker"></a>Kapsayıcılar ve Docker’a Giriş

Kapsayıcılama, bir uygulama veya hizmetin, bağımlılıklarının ve yapılandırma (dağıtım bildirim dosyaları olarak soyut) bir kapsayıcı görüntüsü olarak birlikte paketlenmekte olan yazılım geliştirme yaklaşımına yönelik bir yaklaşımdır. Kapsayıcılı uygulama bir birim olarak test edilebilir ve konak işletim sistemine (OS) kapsayıcı görüntüsü örneği olarak dağıtılabilir.

Sevkiyat kapsayıcıları, malların içeri, eğitim veya kamyonu içinde yüzden bağımsız olarak aktarıldığına, yazılım kapsayıcıları farklı kod ve bağımlılıklar içerebilen standart bir yazılım dağıtımı birimi görevi görür. Yazılımın bu şekilde kapsayıcısız olması, geliştiricilerin ve BT uzmanlarının bunları çok az veya hiç değişiklik yapmadan ortamlar arasında dağıtmasını sağlar.

Kapsayıcılar Ayrıca paylaşılan bir işletim sisteminde bulunan uygulamaları birbirinden ayırır. Kapsayıcılı uygulamalar, işletim sistemi üzerinde çalışan bir kapsayıcı konağın üzerinde çalışır (Linux veya Windows). Bu nedenle kapsayıcılar, sanal makine (VM) görüntülerinden önemli ölçüde daha küçük bir parmak izine sahiptir.

Her kapsayıcı Şekil 2-1 ' de gösterildiği gibi bir Web uygulamasını veya bir hizmeti çalıştırabilir. Bu örnekte, Docker ana bilgisayarı bir kapsayıcı ana bilgisayarı ve APP1, app2, svc 1 ve svc 2 Kapsayıcılı uygulamalar veya hizmetlerdir.

![VM 'de veya fiziksel sunucuda işletim sisteminde çalışan iki uygulama ve iki hizmet](./media/image1.png)

**Şekil 2-1**. Kapsayıcı ana bilgisayarında çalışan birden çok kapsayıcı

Kapsayıcılama kullanmanın başka bir avantajı da ölçeklenebilirlik. Kısa süreli görevler için yeni kapsayıcılar oluşturarak ölçeği hızla değiştirebilirsiniz. Bir görünüm uygulama noktasından, bir görüntüyü (kapsayıcı oluşturma) başlatmak, hizmet veya Web uygulaması gibi bir işlemi başlatmak için benzerdir. Bununla birlikte, aynı görüntünün birden çok konak sunucusunda birden fazla örneğini çalıştırdığınızda, genellikle her kapsayıcının (görüntü örneği) farklı hata etki alanlarında farklı bir konak sunucusunda veya VM 'de çalıştırılmasını istersiniz.

Kısaca, kapsayıcılar tüm uygulama yaşam döngüsü iş akışı genelinde yalıtım, taşınabilirlik, çeviklik, ölçeklenebilirlik ve denetimin avantajlarından yararlanır. En önemli avantaj, ortamın geliştirme ve Ops arasında sağladığı yalıtımdır.

>[!div class="step-by-step"]
>[Önceki](../index.md)İleri
>[](docker-defined.md)
