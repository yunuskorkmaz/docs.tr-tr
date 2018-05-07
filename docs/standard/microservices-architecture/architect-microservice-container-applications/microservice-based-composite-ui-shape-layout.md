---
title: Mikro visual UI şekli ve birden çok mikro tarafından oluşturulan düzeni dahil olmak üzere, temel bileşik kullanıcı Arabirimi oluşturma
description: Kapsayıcılı .NET uygulamaları için .NET mikro mimarisi | Mikro visual UI şekli ve birden çok mikro tarafından oluşturulan düzeni dahil olmak üzere, temel bileşik kullanıcı Arabirimi oluşturma
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.openlocfilehash: cbadb13109c51ba53530011a17006b585573f40a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="creating-composite-ui-based-on-microservices-including-visual-ui-shape-and-layout-generated-by-multiple-microservices"></a>Mikro visual UI şekli ve birden çok mikro tarafından oluşturulan düzeni dahil olmak üzere, temel bileşik kullanıcı Arabirimi oluşturma

Mikro mimarisi genellikle veri ve mantığı işleme sunucu tarafı ile başlar. Ancak, daha gelişmiş bir yaklaşım da mikro üzerinde UI tabanlı uygulamanızı tasarlayın olmaktır. Sunucu ve yalnızca mikro kullanan bir tek yapılı istemci uygulaması mikro sahip yerine mikro tarafından üretilen bir bileşik UI olması anlamına gelir. Bu yaklaşımda, yapı mikro mantığı ve görsel gösterimi ile tam olabilir.

Şekil 4-20 yalnızca bir tek yapılı istemci uygulamasından mikro kullanan basit bir yaklaşım gösterir. Elbette, JavaScript ve HTML oluşturan Between bir ASP.NET MVC hizmeti olabilir. Şekilde tek bir (tek yapılı) istemci UI mantığı ve verileri ve UI şekli (HTML ve JavaScript) değil, yalnızca odaklanmak mikro tüketen sahip vurgular basitleştirme gösterilmiştir.

![](./media/image20.png)

**Şekil 4-20**. Arka uç mikro tüketen tek yapılı bir kullanıcı Arabirimi uygulama

Buna karşılık, bileşik bir kullanıcı Arabirimi tam olarak oluşturulur ve mikro tarafından oluşur. Mikro bazıları UI belirli alanlarında visual şeklini sürücü. En önemli fark, şablonlar temelinde istemci Arabirim bileşenlerinin (örneğin, TS sınıflar) varsa ve bu şablonları için veri şekillendirme UI ViewModel her mikro hizmet gelir ' dir.

İstemci uygulama başlatma zaman, her istemci Arabirim bileşenlerinin (örneğin, TypeScript sınıflar) kendisini bir altyapı mikro hizmet ViewModels belirli bir senaryo için sağlama yeteneğine sahip kaydeder. Mikro hizmet şekli değişirse UI da değişir.

Şekil 4-21 bileşik bu UI yaklaşım sürümünü gösterir. Ayrıntılı bölümleri üzerinde farklı teknikleri tabanlı toplama diğer mikro olabileceği için bu, basitleştirilir —, geleneksel web yaklaşım (ASP.NET MVC) veya bir SPA (tek sayfa uygulaması) oluşturma üzerine bağlıdır.

![](./media/image21.png)

**Şekil 4-21**. Arka uç mikro tarafından şeklinde bileşik bir UI uygulaması örneği

Bu UI birleşim mikro her küçük bir API ağ geçidi için benzer olacaktır. Ancak bu durumda her için küçük bir kullanıcı Arabirimi alanı sorumludur.

Veya hangi UI teknolojileri bağlı olarak, daha az bu nedenle, kullandığınız mikro tarafından yönlendirilen bileşik bir UI yaklaşımı daha zor olabilir. Örneğin, aynı teknikleri yerel mobil uygulama veya bir SPA oluşturmak için kullandığınız bir geleneksel web uygulaması oluşturmak için kullanacağınız değil (gibi bu yaklaşım için daha zor olabilir Xamarin uygulamaları geliştirirken).

[EShopOnContainers](http://aka.ms/MicroservicesArchitecture) örnek uygulama için birden çok nedenleri tek yapılı UI yaklaşımı kullanır. İlk olarak, mikro ve kapsayıcıları bir giriş değil. Bileşik bir kullanıcı Arabirimi, daha gelişmiş ancak da daha fazla tasarlama ve kullanıcı arabirimini geliştirirken karmaşıklık gerektirir. İkinci olarak, eShopOnContainers, daha karmaşık C istemcide yapacağı Xamarin göre yerel bir mobil uygulama de sağlar\# yan.

Ancak, üzerinde mikro UI tabanlı bileşik hakkında daha fazla bilgi için aşağıdaki başvuruları kullanmanızı öneririz.

## <a name="additional-resources"></a>Ek kaynaklar

-   **ASP.NET (özellikle'nın Atölyesi) kullanarak bileşik UI**
    [*http://go.particular.net/workshop-composite-ui-demo*](http://go.particular.net/workshop-composite-ui-demo)

-   **Ruben Oostinga. Mikro mimarisinde tek yapılı ön uç**
    [*http://blog.xebia.com/the-monolithic-frontend-in-the-microservices-architecture/*](http://blog.xebia.com/the-monolithic-frontend-in-the-microservices-architecture/)

-   **Mauro Servienti. Daha iyi UI birleşim gizli anahtarı**
    [*https://particular.net/blog/secret-of-better-ui-composition*](https://particular.net/blog/secret-of-better-ui-composition)

-   **Viktor Farcic. Ön uç Web Bileşenleri mikro dahil**
    [*https://technologyconversations.com/2015/08/09/including-front-end-web-components-into-microservices/*](https://technologyconversations.com/2015/08/09/including-front-end-web-components-into-microservices/)

-   **Ön uç mikro mimarisinde yönetme**\
    [*https://allegro.tech/2016/03/Managing-Frontend-in-the-microservices-architecture.html*](https://allegro.tech/2016/03/Managing-Frontend-in-the-microservices-architecture.html)


>[!div class="step-by-step"]
[Önceki] (mikro-çözümlenebilme-service-registry.md) [sonraki] (esnek-yüksek-kullanılabilirlik-microservices.md)
