---
title: Mikro hizmetler, görsel kullanıcı Arabirimi şekli ve düzeni birden fazla mikro hizmetin oluşturduğu dahil olmak üzere temel bileşik kullanıcı Arabirimi oluşturma
description: Kapsayıcılı .NET uygulamaları için .NET mikro hizmet mimarisi | Mikro hizmetler, görsel kullanıcı Arabirimi şekli ve düzeni birden fazla mikro hizmetin oluşturduğu dahil olmak üzere temel bileşik kullanıcı Arabirimi oluşturma
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.openlocfilehash: 3c5f4c5a1dd1c1065be63ad916af078050c069c1
ms.sourcegitcommit: 9bd8f213b50f0e1a73e03bd1e840c917fbd6d20a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/25/2018
ms.locfileid: "50033655"
---
# <a name="creating-composite-ui-based-on-microservices-including-visual-ui-shape-and-layout-generated-by-multiple-microservices"></a>Mikro hizmetler, görsel kullanıcı Arabirimi şekli ve düzeni birden fazla mikro hizmetin oluşturduğu dahil olmak üzere temel bileşik kullanıcı Arabirimi oluşturma

Mikro hizmet mimarisi genellikle sunucu tarafı işleme veri ve mantık ile başlar. Ancak, kullanıcı Arabirimi de mikro hizmetler üzerinde uygulamanızı tasarlamak için daha gelişmiş bir yaklaşım olur. Mikro hizmetler sunucusunda hem de yalnızca mikro hizmetler kullanan bir tek parçalı bir istemci uygulaması yerine mikro hizmetler tarafından üretilen bir bileşik kullanıcı Arabirimi olması anlamına gelir. Bu yaklaşımda, mikro hizmetler oluşturma mantığı ve görsel bir temsili ile tam olabilir.

Şekil 4-20 yalnızca bir tek parçalı bir istemci uygulamasından mikro hizmetler kullanan basit bir yaklaşım gösterilmektedir. Elbette, HTML ve JavaScript üretme aralığındaki bir ASP.NET MVC hizmeti olabilir. Şekilde, tek bir (parçalı) istemci kullanıcı Arabirimi mantığı ve verileri ve kullanıcı Arabirimi şekli (HTML ve JavaScript) değil, yalnızca odak mikro hizmetler kullanan olduğunu vurgular bir basitleştirme ' dir.

![](./media/image20.png)

**Şekil 4-20**. Arka uç mikro hizmetler kullanan tek parça bir kullanıcı Arabirimi uygulama

Buna karşılık, bileşik bir kullanıcı Arabirimi tam olarak oluşturulur ve mikro tarafından hizmetlerden. Mikro hizmetler bazı kullanıcı Arabirimi belirli alanları visual şeklini sürücü. En önemli fark, şablonları temel alan istemci kullanıcı Arabirimi bileşenleri (örneğin, TS sınıflar) sahip ve bu şablonlar için veri şekillendirme UI ViewModel her bir mikro hizmetin gelir ' dir.

İstemci uygulama başlangıç zamanında her istemci kullanıcı Arabirimi bileşenleri (örneğin, TypeScript sınıflar) kendini Viewmodel'lar belirli bir senaryo için sağlayabilen bir altyapı mikro ile kaydeder. Mikro hizmet şekli değişirse, kullanıcı arabirimini de değişir.

Şekil 4-21, bu bileşik kullanıcı Arabirimi yaklaşım bir sürümünü gösterir. Farklı teknikleri üzerinde göre ayrıntılı bölümleri toplayarak diğer mikro hizmetler olabileceği için bu basitleştirilmiştir —, geleneksel web yaklaşım (ASP.NET MVC) veya bir SPA (tek sayfalı uygulama) oluşturma üzerine bağlıdır.

![](./media/image21.png)

**Şekil 4-21**. Arka uç mikro hizmetin şeklinde bileşik bir kullanıcı Arabirimi uygulaması örneği

Her biri bu kullanıcı Arabirimi oluşturma mikro hizmetler, küçük bir API ağ geçidi için benzer olacaktır. Ancak bu durumda her için küçük bir kullanıcı Arabirimi alan sorumludur.

Mikro hizmet tarafından yönetilen bir bileşik kullanıcı Arabirimi yaklaşım daha zor olabilir ya da daha az bir şekilde bağlı olarak hangi UI teknolojileri kullanıyorsanız. Örneğin, aynı teknikleri, yerel mobil uygulama veya bir SPA oluşturmak için kullandığınız bir geleneksel web uygulaması oluşturmak için kullanacağınız değil (olarak için bu yaklaşım daha zor olabilecek Xamarin uygulamaları geliştirirken).

[Hizmetine](https://aka.ms/MicroservicesArchitecture) örnek uygulama, birden çok nedenlerle tek parça UI yaklaşımı kullanır. İlk olarak, mikro hizmetler ve kapsayıcılar giriş niteliğindedir. Bir bileşik kullanıcı Arabirimi daha gelişmiş ancak aynı zamanda daha fazla tasarlama ve kullanıcı arabirimini geliştirirken karmaşıklığı gerektirir. Ayrıca, daha karmaşık C istemcide yapacağınız Xamarin, temel yerel bir mobil uygulama ikinci hizmetine sağlar\# yan.

Ancak, kullanıcı Arabirimi üzerinde mikro hizmet tabanlı bileşik hakkında daha fazla bilgi için aşağıdaki başvuruları kullanmanızı öneririz.

## <a name="additional-resources"></a>Ek kaynaklar

-   **Bileşik kullanıcı Arabirimi kullanarak ASP.NET (belirli'nın Atölyesi)**
    [*https://go.particular.net/workshop-composite-ui-demo*](https://go.particular.net/workshop-composite-ui-demo)

-   **Ruben Oostinga. Mikro hizmetler mimarisinde tek parça ön uç**
    [*https://xebia.com/blog/the-monolithic-frontend-in-the-microservices-architecture/*](https://xebia.com/blog/the-monolithic-frontend-in-the-microservices-architecture/)

-   **Mauro Servienti. Gizli anahtarı daha iyi bir kullanıcı Arabirimi oluşturma**
    [*https://particular.net/blog/secret-of-better-ui-composition*](https://particular.net/blog/secret-of-better-ui-composition)

-   **Viktor Farcic. Mikro hizmetler halinde ön uç Web bileşenler dahil olmak üzere**
    [*https://technologyconversations.com/2015/08/09/including-front-end-web-components-into-microservices/*](https://technologyconversations.com/2015/08/09/including-front-end-web-components-into-microservices/)

-   **Mikro hizmet mimarisi ön yönetme**\
    [*https://allegro.tech/2016/03/Managing-Frontend-in-the-microservices-architecture.html*](https://allegro.tech/2016/03/Managing-Frontend-in-the-microservices-architecture.html)


>[!div class="step-by-step"]
[Önceki](microservices-addressability-service-registry.md)
[İleri](resilient-high-availability-microservices.md)
