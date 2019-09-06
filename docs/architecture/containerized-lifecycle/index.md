---
title: Kapsayıcılar ve Docker’a Giriş
description: Docker kullanmanın başlıca avantajlarından yüksek düzeyde bir genel bakış elde edin.
ms.date: 02/15/2019
ms.openlocfilehash: a03c67ed4fbc55c84e69fba5b7978863c8305e00
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/30/2019
ms.locfileid: "70295674"
---
# <a name="introduction-to-containers-and-docker"></a>Kapsayıcılara ve Docker 'a giriş

*Kapsayıcılama, bir uygulama veya hizmetin, bağımlılıklarının ve yapılandırma (dağıtım bildirim dosyaları olarak soyut) bir kapsayıcı görüntüsü olarak birlikte paketlenmekte olan yazılım geliştirme yaklaşımına yönelik bir yaklaşımdır. Daha sonra kapsayıcılı uygulamayı bir birim olarak test edebilir ve onu konak işletim sistemine (OS) bir kapsayıcı görüntüsü örneği olarak dağıtabilirsiniz.*

Sevkiyat kapsayıcıları, malların içeri, eğitim veya kamyonu içinde yüzden bağımsız olarak aktarıldığına, yazılım kapsayıcıları farklı kod ve bağımlılıklar içerebilen standart bir yazılım dağıtımı birimi görevi görür. Yazılımın bu şekilde kapsayıcısız olması, geliştiricilerin ve BT uzmanlarının bunları çok az veya hiç değişiklik yapmadan ortamlar arasında dağıtmasını sağlar.

Kapsayıcılar Ayrıca paylaşılan bir işletim sisteminde bulunan uygulamaları birbirinden ayırır. Kapsayıcılı uygulamalar, işletim sistemi üzerinde çalışan bir kapsayıcı konağın üzerinde çalışır (Linux veya Windows). Bu nedenle kapsayıcılar, sanal makine (VM) görüntülerinden çok daha küçük bir parmak izine sahiptir.

Her kapsayıcı Şekil 1-1 ' de gösterildiği gibi bir Web uygulamasını veya bir hizmeti çalıştırabilir. Bu örnekte, Docker ana bilgisayarı bir kapsayıcı ana bilgisayarı ve APP1, app2, Svc1 ve Svc2 Kapsayıcılı uygulamalar veya hizmetlerdir.

![VM 'de veya fiziksel sunucuda işletim sisteminde çalışan iki uygulama ve iki hizmet](./media/image1.png)

**Şekil 1-1**. Kapsayıcı ana bilgisayarında çalışan birden çok kapsayıcı

Kapsayıcılardan türetebilmeniz için başka bir avantaj de ölçeklenebilirlik. Kısa süreli görevler için yeni kapsayıcılar oluşturarak ölçeği hızla değiştirebilirsiniz. Bir görünüm uygulama noktasından, bir görüntüyü (kapsayıcı oluşturma) başlatmak, hizmet veya Web uygulaması gibi bir işlemi başlatmak için benzerdir. Bununla birlikte, aynı görüntünün birden çok konak sunucusunda birden fazla örneğini çalıştırdığınızda, genellikle her kapsayıcının (görüntü örneği) farklı hata etki alanlarında farklı bir konak sunucusunda veya VM 'de çalıştırılmasını istersiniz.

Kısacası, kapsayıcılar tüm uygulama yaşam döngüsü iş akışı genelinde yalıtım, taşınabilirlik, çeviklik, ölçeklenebilirlik ve denetimin avantajlarını sunmaktadır. En önemli avantaj geliştirme ve Ops arasında sunulan ortam yalıtımına sahiptir.

>[!div class="step-by-step"]
>[Next](what-is-docker.md)
