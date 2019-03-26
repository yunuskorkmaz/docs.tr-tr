---
title: Mikro hizmet mimarisi
description: Kapsayıcılı .NET uygulamaları için .NET mikro hizmet mimarisi | 30.000 ayak mikro hizmet mimarisini görüntüleyin.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/20/2018
ms.openlocfilehash: 6a3262c65fb221f3b9e058a581b5dc6bfed92076
ms.sourcegitcommit: 7156c0b9e4ce4ce5ecf48ce3d925403b638b680c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/26/2019
ms.locfileid: "58465197"
---
# <a name="microservices-architecture"></a>Mikro hizmet mimarisi

Adından da anlaşılacağı gibi mikro hizmetler mimarisi küçük bir hizmetler kümesi olarak sunucu uygulaması oluşturmaya yönelik bir yaklaşım ' dir. Yaklaşım, ön uç için kullanılıyor olsa da, bir mikro hizmet mimarisi arka uca çoğunlukla yönelimli olduğu anlamına gelir. Her hizmet kendi işleminde çalışır ve diğer işlemler gibi HTTP/HTTPS ve WebSockets, protokoller kullanarak iletişim kurar veya [AMQP](https://en.wikipedia.org/wiki/Advanced_Message_Queuing_Protocol). Her mikro hizmet belirli bir uçtan uca etki alanı ya da belirli bir bağlam sınırında bir iş özelliğini uygular ve her otonom olarak geliştirilmiş olmalıdır ve bağımsız olarak dağıtılabilir. Son olarak, her bir mikro hizmet etki alanı mantığı (özerkliği ve merkezi olmayan veri yönetimi) ve ilgili etki alanı veri modeline ait olması ve farklı veri depolama teknolojileri (SQL, NoSQL) ve farklı programlama dillerini temel alabilir.

Bir mikro hizmet boyutu ne olmalı? Bir mikro hizmet geliştirirken, boyutu en önemli nokta olmamalıdır. Bunun yerine, en önemli nokta gevşek oluşturmak için geliştirme, dağıtma ve ölçeklendirme, her hizmet için'ın kontrolündedir şekilde Hizmetleri eşleşmiş olmalıdır. Elbette, tanımlamak ve mikro hizmetler tasarlama, diğer mikro hizmetler ile çok fazla doğrudan bağımlılıklara sahip olmadığınız sürece olabildiğince küçük olacak şekilde çalışmanız gerekir. Daha fazla mikro hizmet boyutunu iç Uyuma sahip olması gerekir ve bunun bağımsızlığı diğer hizmetlerden daha önemlidir.

Bir mikro hizmet mimarisi neden? Kısacası, uzun vadeli çeviklik sağlar. Mikro hizmetler, daha iyi bakım belirtir, her ayrıntılı ve otonom yaşam döngülerine sahip birden çok bağımsız bir şekilde dağıtılabilen hizmete tabanlı uygulamalar oluşturmanıza imkan vererek karmaşık, büyük ve yüksek oranda ölçeklenebilir sistemlerinde etkinleştirin.

Ek bir avantaj olarak mikro hizmetler bağımsız olarak ölçeği genişletebilirsiniz. Bir birim olarak ölçeği gereken tek bir tek parçalı uygulama sahip olmak yerine, bunun yerine belirli bir mikro hizmetler ölçeklendirebilirsiniz. Böylece, yalnızca ölçeklendirilmesi gerekmeyen diğer alanları uygulamanın ölçeklendirmek yerine isteğe desteklemek için daha fazla işleme güç veya ağ bant genişliği gereksinimlerinize işlevsel alan ölçeklendirebilirsiniz. Daha az donanım gerekeceğinden, maliyet tasarrufu anlamına gelir.

![Geleneksel monolitik yaklaşımda birkaç sunucuları/VM tüm uygulamada kopyalayarak uygulama ölçeklendirir. Mikro hizmetler yaklaşımı her hizmet birbirinden bağımsız şekilde ölçeklenebilmek için işlevleri daha küçük Hizmetleri'nde ayrılır.](./media/image6.png)

**Şekil 4-6**. Mikro hizmetler yaklaşımı yerine tek parçalı dağıtım

Şekil 4-6 gösterildiği gibi karmaşık, büyük ve ölçeklenebilir uygulamaların belirli, küçük alanlarını değiştirebilirsiniz çünkü mikro hizmetler yaklaşımı Çevik değişiklikleri ve her mikro hizmet hızlı yinelemesini sağlar.

Ayrıntılı mikro hizmet tabanlı uygulamalar sağlar, sürekli tümleştirme ve sürekli teslim yöntemleri mimarileri oluşturma. Bu da yeni işlevlerin uygulamaya hızla sunulmasına. Uygulamaların ayrıntılı oluşturma ve mikro hizmetler ayrı olarak test çalıştırabilirsiniz ve bunları otonom olarak bunlar arasında NET sözleşmeleri korurken gelişmesi sağlar. Arabirimleri veya sözleşmeleri değişmez sürece iç herhangi bir mikro hizmet uygulaması değiştirebilir veya diğer mikro hizmetler bozmadan yeni işlevsellik ekler.

Mikro hizmet tabanlı bir sistemle üretime geçmeden başarısı etkinleştirmek için önemli yönleri şunlardır:

- İzleme ve sistem durumu denetimleri altyapı ve Hizmetleri.

- Ölçeklenebilir altyapı Hizmetleri (diğer bir deyişle, Bulut ve düzenleyicileri).

- Güvenlik tasarımı ve uygulaması farklı düzeylere: kimlik doğrulaması, yetkilendirme, gizli dizileri yönetimi, güvenli iletişim, vs.

- Genellikle farklı mikro hizmetler üzerinde odaklanarak farklı ekipler ile hızlı uygulama teslimi.

- DevOps ve CI/CD uygulamalarını ve altyapısını.

Bu yalnızca ilk üç ele veya bu kılavuzda sunulan. Uygulama yaşam döngüsü için ilgili, son iki noktalarına ek ele alınmaktadır [kapsayıcılı Docker uygulaması yaşam döngüsü Microsoft Platformu ve araçları ile](https://aka.ms/dockerlifecycleebook) e-kitabı.

## <a name="additional-resources"></a>Ek kaynaklar

- **Mark Russinovich'e. Mikro hizmetler: Bulut tarafından desteklenen bir uygulama Devrimi** \
  [https://azure.microsoft.com/blog/microservices-an-application-revolution-powered-by-the-cloud/](https://azure.microsoft.com/blog/microservices-an-application-revolution-powered-by-the-cloud/)

- **Martin Fowler. Mikro hizmetler** \
  [https://www.martinfowler.com/articles/microservices.html](https://www.martinfowler.com/articles/microservices.html)

- **Martin Fowler. Mikro hizmet önkoşulları** \
  [https://martinfowler.com/bliki/MicroservicePrerequisites.html](https://martinfowler.com/bliki/MicroservicePrerequisites.html)

- **Jimmy Nilsson. Öbek bulut bilgi işlem** \
  [https://www.infoq.com/articles/CCC-Jimmy-Nilsson](https://www.infoq.com/articles/CCC-Jimmy-Nilsson)

- **Cesar de la Torre. Docker uygulaması yaşam döngüsü Microsoft Platformu ve araçları ile kapsayıcılı hale** (indirilebilir e-kitap) \
  [https://aka.ms/dockerlifecycleebook](https://aka.ms/dockerlifecycleebook)

>[!div class="step-by-step"]
>[Önceki](service-oriented-architecture.md)
>[İleri](data-sovereignty-per-microservice.md)
