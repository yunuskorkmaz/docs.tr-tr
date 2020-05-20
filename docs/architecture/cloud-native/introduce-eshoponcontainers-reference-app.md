---
title: EShopOnContainers başvuru uygulamasına giriş
description: ASP.NET Core ve Azure için eShopOnContainers bulutu yerel mikro hizmetleri başvuru uygulamasına giriş.
ms.date: 05/13/2020
ms.openlocfilehash: a6f3defabec809eaf1cb143e2b521904248b74f2
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83613973"
---
# <a name="introducing-eshoponcontainers-reference-app"></a>EShopOnContainers başvuru uygulamasına giriş

Microsoft, önde gelen topluluk uzmanlarıyla ortaklık altında, tam özellikli bir bulut Yerel mikro hizmetler başvuru uygulaması olan eShopOnContainers üretti. Bu uygulama, çevrimiçi bir storefront oluşturmak için .NET Core ve Docker ve isteğe bağlı olarak Azure, Kubernetes ve Visual Studio kullanılarak tanıtıma göre oluşturulmuştur.

![eShopOnContainers örnek uygulama ekran görüntüsü.](./media/eshoponcontainers-sample-app-screenshot.png)

**Şekil 2-1**. eShopOnContainers örnek uygulama ekran görüntüsü.

Bu bölümü başlatmadan önce [Eshoponcontainers başvuru uygulamasını](https://github.com/dotnet-architecture/eShopOnContainers)indirmeniz önerilir. Bunu yaparsanız, sunulan bilgilerle birlikte izlemeniz daha kolay olmalıdır.

## <a name="features-and-requirements"></a>Özellikler ve gereksinimler

Uygulamanın Özellikler ve gereksinimlerinin bir gözden geçirimiyle başlayalım. EShopOnContainers uygulaması t-Shirts ve kahve Mug gibi çeşitli fiziksel ürünleri satan bir çevrimiçi mağazayı temsil eder. Daha önce çevrimiçi bir şey satın aldıysanız, mağazayı kullanma deneyimi görece tanıdık olmalıdır. Deponun uyguladığı temel özelliklerden bazıları şunlardır:

- Katalog öğelerini listeleme
- Öğeleri türe göre filtrele
- Öğeleri markala filtrele
- Alışveriş sepetine öğe ekleme
- Sepetten öğe düzenleme veya kaldırma
- Kullanıma alma
- Hesap kaydetme
- Oturum aç
- Oturumu kapat
- Siparişleri gözden geçirme

Uygulamanın aşağıdaki işlevsel olmayan gereksinimleri de vardır:

- Yüksek oranda kullanılabilir olması gerekir ve artan trafiği karşılamak için otomatik olarak ölçeklendirilmesi gerekir (ve trafik alt taraflarından sonra ölçeği yeniden ölçeklendirmelidir).
- Karşılaştığı sorunları gidermeye yardımcı olmak için sistem durumu ve tanılama günlüklerinin kullanımı kolay bir şekilde izlenmesini sağlamalıdır.
- Sürekli tümleştirme ve dağıtım (CI/CD) desteği de dahil olmak üzere çevik bir geliştirme sürecini desteklemelidir.
- İki Web ön ucu (geleneksel ve tek sayfalı uygulama) ek olarak, uygulamanın farklı türlerde işletim sistemleri çalıştıran mobil istemci uygulamalarını da desteklemesi gerekir.
- Platformlar arası barındırma ve platformlar arası geliştirmeyi desteklemelidir.

![eShopOnContainers başvuru uygulaması geliştirme mimarisi.](./media/eshoponcontainers-development-architecture.png)

**Şekil 2-2**. eShopOnContainers başvuru uygulaması geliştirme mimarisi.

EShopOnContainers uygulamasına, ASP.NET Core MVC sunucu uygulamasını ya da uygun bir API ağ geçidini hedefleyen HTTPS üzerinden uygulamaya erişen Web veya mobil istemcilerden erişilebilir. API ağ geçitleri, arka uç hizmetlerini ayrı ayrı ön uç istemcilerinden ayırma ve daha iyi güvenlik sağlama gibi çeşitli avantajlar sunar. Uygulama ayrıca her ön uç istemci için ayrı API ağ geçitleri oluşturulmasını öneren backends-for-Frontends (BFF) olarak bilinen ilgili bir model kullanır. Başvuru mimarisi, isteğin bir Web veya mobil istemciden geldiğini temel alarak API ağ geçitlerinin bölünmesini gösterir.

Uygulamanın işlevselliği çeşitli farklı mikro hizmetlere ayrılmıştır. Kimlik doğrulama ve kimlikten sorumlu hizmetler, ürün kataloğundan öğe listeleme, kullanıcıların alışveriş sepetlerini yönetme ve sipariş yerleştirme hizmetleri bulunur. Bu ayrı hizmetlerin her biri kendi kalıcı depolamasına sahiptir. Tüm hizmetlerin etkileşimde bulunduğu tek bir ana veri deposu yoktur. Bunun yerine, hizmetler arasındaki koordinasyon ve iletişim, bir ileti veri yolu kullanımı ile gerekli bir şekilde yapılır.

Farklı mikro hizmetlerin her biri, bireysel gereksinimlerine göre farklı şekilde tasarlanmıştır. Bu, .NET Core kullanılarak oluşturulmuştur ve bulut için tasarlansa da teknoloji yığınının farklı olabileceği anlamına gelir. Daha basit hizmetler temeldeki veri depolarına temel oluşturma-okuma-güncelleştirme-silme (CRUD) erişimi sağlar, ancak daha gelişmiş hizmetler iş karmaşıklığını yönetmek için etki alanı odaklı tasarım yaklaşımlarını ve desenlerini kullanır.

![Farklı mikro hizmet türleri](./media/different-kinds-of-microservices.png)

**Şekil 2-3**. Farklı mikro hizmet türleri.

## <a name="overview-of-the-code"></a>Koda genel bakış

Mikro hizmetlerden yararlandığından eShopOnContainers uygulaması, GitHub deposunda oldukça farklı projeler ve çözümler içerir. Ayrı çözümlerin ve yürütülebilir dosyaların yanı sıra çeşitli hizmetler, hem yerel geliştirme sırasında hem de üretimde çalışma zamanında kendi kapsayıcılarında çalışacak şekilde tasarlanmıştır. Şekil 2-4, çeşitli farklı projelerin düzenlendiği tam Visual Studio çözümünü gösterir.

![Visual Studio çözümündeki projeler.](./media/projects-in-visual-studio-solution.png)

**Şekil 2-4**. Visual Studio çözümündeki projeler.

Kod, farklı mikro hizmetleri desteklemek üzere düzenlenmiştir ve her mikro hizmet içinde, kod etki alanı mantığına, altyapı kaygılarına ve Kullanıcı arabirimine veya hizmet uç noktasına bölünmüştür. Birçok durumda, her hizmetin bağımlılıkları üretimde Azure hizmetleri ve yerel geliştirme için alternatif seçenekler tarafından yerine getirilir. Uygulama gereksinimlerinin Azure hizmetlerine nasıl eşlendiğini inceleyelim.

## <a name="understanding-microservices"></a>Mikro hizmetleri anlama

Bu kitap, Azure teknolojisi kullanılarak oluşturulan bulutta yerel uygulamalara odaklanır. Mikro hizmetler en iyi uygulamaları ve mikro hizmet tabanlı uygulamaların nasıl mimarinin nasıl kullanılacağı hakkında daha fazla bilgi edinmek için yardımcı kitabı, [.net mikro hizmetleri: Kapsayıcılı .NET uygulamalarına yönelik mimariyi](https://dotnet.microsoft.com/download/thank-you/microservices-architecture-ebook)okuyun.

>[!div class="step-by-step"]
>[Önceki](candidate-apps.md) 
> [Sonraki](map-eshoponcontainers-azure-services.md)
