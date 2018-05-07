---
title: Mikro mimarisi
description: Kapsayıcılı .NET uygulamaları için .NET mikro mimarisi | Mikro mimarisi
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.openlocfilehash: 9bcaacce323ed9afa482660f409312f9a1b82cfa
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="microservices-architecture"></a>Mikro mimarisi

Adından da anlaşılacağı gibi mikro mimarisi küçük Hizmetleri kümesi olarak bir sunucu uygulaması oluşturmak için bir yaklaşımdır. Her hizmetin kendi işleminde çalışır ve HTTP/HTTPS, WebSockets, gibi protokoller kullanan diğer işlemleri ile iletişim kurar veya [AMQP](https://en.wikipedia.org/wiki/Advanced_Message_Queuing_Protocol). Her mikro hizmet belirli uçtan uca etki alanı veya iş yetenek belirli bağlam sınırında uygular ve her sınırlarına geliştirilmiş olmalıdır ve bağımsız olarak dağıtılabilir. Son olarak, her mikro hizmet, farklı veri depolama teknolojileri (SQL, NoSQL) ve farklı programlama dillerini dayalı etki alanı mantığı (Egemenlik ve merkezi olmayan veri yönetimi) ve ilişkili etki alanı veri modeli kendi.

Hangi boyutu bir mikro olmalıdır? Bir mikro hizmet geliştirirken, boyutu en önemli nokta olmamalıdır. Bunun yerine, en önemli nokta geniş oluşturmak için geliştirme, dağıtım ve her hizmet için ölçek otonomiye sahip şekilde Hizmetleri bağlı olmalıdır. Elbette, tanımlama ve mikro tasarlama, diğer mikro ile çok fazla doğrudan bağımlılıkları olmayan sürece, bunları olabildiğince küçük yapmak çalıştığınızda. Daha fazla mikro hizmet boyutunu gerekir iç cohesion ve kendi bağımsızlığı diğer hizmetlerden daha önemlidir.

Mikro mimarisi neden? Kısacası, uzun vadeli çeviklik sağlar. Mikro her ayrıntılı ve otonom yaşam döngüleri sahip çok sayıda bağımsız olarak dağıtılabilir hizmetlerini temel alarak uygulamalar oluşturmanızı sağlayarak daha iyi bakım karmaşık, büyük ve yüksek düzeyde ölçeklenebilir sistemlerinde etkinleştirin.

Ek bir avantaj olarak mikro çıkışı bağımsız olarak ölçeklendirebilirsiniz. Bir birim olarak ölçeğini gereken tek bir tek yapılı uygulama sahip olmak yerine, belirli mikro yerine ölçeklendirebilirsiniz. Bu şekilde, yalnızca ölçeklendirilmesi gerekmez diğer alanlarını uygulama ölçeklendirmek yerine isteğe bağlı desteklemek için daha fazla işlem gücü veya ağ bant genişliği gerekiyor işlevsel alan ölçeklendirebilirsiniz. Daha az donanım gerekeceğinden, maliyet tasarrufu anlamına gelir.

![](./media/image6.png)

**Şekil 4-6**. Tek yapılı dağıtım mikro yaklaşım karşılaştırması

Şekil 4-6 gösterildiği gibi karmaşık, büyük ve ölçeklenebilir uygulamalar belirli, küçük alanlarının değişebildiğinden mikro yaklaşım Çevik değişiklikleri ve her mikro hizmet hızlı yinelemesi sağlar.

Hassas mikro tabanlı uygulamaları etkinleştirir sürekli tümleştirme ve kesintisiz teslim yöntemleri mimarisi oluşturma. Ayrıca yeni işlevler teslimini uygulamasına hızlandırır. Hassas uygulamalar oluşumunu ve yalıtım modunda mikro test çalıştırmak ve bunları sınırlarına aralarında Temizle sözleşmeleri korurken gelişmesi sağlar. Arabirimleri veya sözleşmeleri değiştirmeyin sürece tüm mikro hizmet iç uyarlamasını değiştirin veya yeni işlevsellik diğer mikro bozmadan ekleyin.

Mikro tabanlı bir sistemle üretime geçmeden başarısı etkinleştirmek için önemli yönleri şunlardır:

-   İzleme ve sistem durumu hizmetleri ve altyapı denetler.

-   Ölçeklenebilir altyapı Hizmetleri (diğer bir deyişle, Bulut ve orchestrators).

-   Güvenlik tasarımı ve uygulama, birden çok düzeyde: kimlik doğrulama, yetkilendirme, gizli yönetimi, güvenli iletişim, vs.

-   Genellikle farklı mikro odaklanan farklı ekipler ile hızlı uygulama teslim.

-   DevOps ve CI/CD uygulamalar ve altyapı.

Bu, yalnızca ilk üç kapsamında veya bu kılavuzda sunulan. Uygulama yaşam döngüsü için ilgili en son iki nokta ilave kapsanan [Microsoft Platformu ve araçları ile kapsayıcılı Docker uygulama yaşam döngüsü](https://aka.ms/dockerlifecycleebook) e-Kitap.

## <a name="additional-resources"></a>Ek kaynaklar

-   **İşareti Russinovich. Mikro: Bulut tarafından desteklenen bir uygulama devrim**
    [*https://azure.microsoft.com/blog/microservices-an-application-revolution-powered-by-the-cloud/*](https://azure.microsoft.com/blog/microservices-an-application-revolution-powered-by-the-cloud/)

-   **Martin Fowler. Mikro**
    [*https://www.martinfowler.com/articles/microservices.html*](https://www.martinfowler.com/articles/microservices.html)

-   **Martin Fowler. Mikro hizmet önkoşulları**
    [*https://martinfowler.com/bliki/MicroservicePrerequisites.html*](https://martinfowler.com/bliki/MicroservicePrerequisites.html)

-   **Jimmy Nilsson. Öbek bulut bilgi işlem**
    [*https://www.infoq.com/articles/CCC-Jimmy-Nilsson*](https://www.infoq.com/articles/CCC-Jimmy-Nilsson)

-   **Cesar de la Torre. Microsoft Platformu ve araçları ile Docker uygulama yaşam döngüsü kapsayıcılı** (indirilebilir e-kitap) [*https://aka.ms/dockerlifecycleebook*](https://aka.ms/dockerlifecycleebook)




>[!div class="step-by-step"]
[Önceki] (hizmet-yönelimli-architecture.md) [sonraki] (veri-Egemenlik-başına-microservice.md)
