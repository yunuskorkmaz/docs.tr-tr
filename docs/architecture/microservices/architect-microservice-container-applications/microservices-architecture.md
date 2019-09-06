---
title: Mikro hizmetler mimarisi
description: Kapsayıcılı .NET uygulamaları için .NET mikro hizmetleri mimarisi | Mikro hizmet mimarisinin 30,000 fit görünümü.
ms.date: 09/20/2018
ms.openlocfilehash: 3cf2a94140042d3cf76b5b63fe4e98638c56dbfe
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/30/2019
ms.locfileid: "70295480"
---
# <a name="microservices-architecture"></a>Mikro hizmetler mimarisi

Adından da anlaşılacağı gibi, mikro hizmet mimarisi bir sunucu uygulamasını bir dizi küçük hizmet olarak oluşturmaya yönelik bir yaklaşımdır. Bu, bir mikro hizmet mimarisinin genellikle arka uca yönlendirilmesine karşın bu yaklaşım ön uç için de kullanılsa da bu anlamına gelir. Her hizmet kendi sürecinde çalışır ve HTTP/HTTPS, WebSockets veya [AMQP](https://en.wikipedia.org/wiki/Advanced_Message_Queuing_Protocol)gibi protokolleri kullanarak diğer işlemlerle iletişim kurar. Her mikro hizmet, belirli bir bağlam sınırı içinde belirli bir uçtan uca etki alanı veya iş yeteneği uygular ve her birinin olarak çalışabilen geliştirilmesi ve bağımsız olarak dağıtılabilir olması gerekir. Son olarak, her mikro hizmet ilgili etki alanı veri modeli ve etki alanı mantığını (sogemenlik ve merkezi olmayan veri yönetimi) ve farklı veri depolama teknolojilerini (SQL, NoSQL) ve farklı programlama dillerini temel almalıdır.

Mikro hizmet hangi boyutta olmalıdır? Mikro hizmet geliştirirken, boyut önemli nokta olmamalıdır. Bunun yerine, her bir hizmet için geliştirme, dağıtım ve ölçeklendirme bağımsız çalışma sınırı sağlamak üzere gevşek olarak bağlanmış hizmetler oluşturmak için önemli nokta olmalıdır. Tabii ki, mikro hizmetleri tanımlarken ve tasarlarken, diğer mikro hizmetlerle çok sayıda doğrudan bağımlılığı olmadığı sürece bunları mümkün olduğunca küçük hale getirme denemeniz gerekir. Mikro hizmet boyutundan daha önemli olan, bu, diğer hizmetlerden gelen bağımsızlık ve bağımsızlığı olmalıdır.

Mikro hizmet mimarisi neden? Kısaca, uzun süreli çeviklik sağlar. Mikro hizmetler, her birinin ayrıntılı ve otonom yaşam döngüleri olan çok sayıda dağıtılabilir hizmete dayalı uygulamalar oluşturmanıza olanak tanıyarak karmaşık, büyük ve yüksek düzeyde ölçeklenebilir sistemlerde daha iyi bakım sağlar.

Ek bir avantaj olarak, mikro hizmetler bağımsız olarak ölçeklendirilebilir. Bir birim olarak ölçeklendirmeniz gereken tek bir tek tek parçalı uygulamaya sahip olmak yerine, belirli mikro hizmetleri de ölçeklendirebilirsiniz. Bu şekilde, uygulamanın ölçeklendirilmesi gerekmeyen diğer alanların ölçeğini genişletmek yerine, talebi desteklemek için yalnızca daha fazla işlem gücü veya ağ bant genişliğine ihtiyacı olan işlevsel alanı ölçeklendirebilirsiniz. Bu, daha az donanım gerektiğinden maliyet tasarrufu anlamına gelir.

![Geleneksel tek parçalı yaklaşımda, uygulama tüm uygulamayı birkaç sunucu/VM 'de kopyalayarak ölçeklendirebilirler. Mikro hizmetler yaklaşımında işlevsellik, her hizmetin bağımsız olarak ölçeklenebilmesi için daha küçük hizmetlerde ayırt edilir.](./media/image6.png)

**Şekil 4-6**. Tek parçalı dağıtım, mikro hizmetler yaklaşımına karşı

Şekil 4-6 gösterdiği gibi, mikro hizmetler yaklaşımı, karmaşık, büyük ve ölçeklenebilir uygulamaların belirli, küçük bölümlerini değiştirebildiğinden, her mikro hizmetin çevik değişikliklere ve hızlı yinelemesine izin verir.

Ayrıntılı mikro hizmet tabanlı uygulamaların mimarisi sürekli tümleştirme ve sürekli teslim uygulamalarına izin vermez. Ayrıca, uygulamaya yeni işlevlerin teslimini da hızlandırır. Uygulamaların hassas bir şekilde oluşturulması, mikro Hizmetleri birlikte çalıştırmanızı ve test etmenizi ve bunları aralarında açık sözleşmeleri sürdürirken olarak çalışabilen geliştirebilir. Arabirimleri veya sözleşmeleri değiştirmedikçe, herhangi bir mikro hizmetin iç uygulamasını değiştirebilir veya diğer mikro hizmetleri bozmadan yeni işlevler ekleyebilirsiniz.

Mikro hizmet tabanlı bir sistemle üretime devam eden bir başarı sağlamak için aşağıdakiler önemli yönleri aşağıda verilmiştir:

- Hizmetlerin ve altyapının izlenmesi ve sistem durumu denetimleri.

- Hizmetler için ölçeklenebilir altyapı (yani, bulut ve Yöneticiler).

- Birden çok düzeyde güvenlik tasarımı ve uygulama: kimlik doğrulama, yetkilendirme, gizli dizi yönetimi, güvenli iletişim, vb.

- Genellikle farklı takımlarla farklı mikro hizmetlere odaklanan hızlı uygulama teslimi.

- DevOps ve CI/CD uygulamaları ve altyapısı.

Bu kılavuzda, bu kılavuzda yalnızca ilk üç tane ele alınmıştır veya sunulmuştur. Uygulama yaşam döngüsüyle ilgili olan son iki işaret, [Microsoft platformu ve araçları e-Book ile ek Kapsayıcılı Docker uygulaması yaşam döngüsü](https://aka.ms/dockerlifecycleebook) kapsamında ele alınmıştır.

## <a name="additional-resources"></a>Ek kaynaklar

- **Mark Russinovich. Mikro hizmetler Bulut tarafından desteklenen bir uygulama Devrimi** \
  <https://azure.microsoft.com/blog/microservices-an-application-revolution-powered-by-the-cloud/>

- **Marwler. Mikro hizmetler** \
  <https://www.martinfowler.com/articles/microservices.html>

- **Marwler. Mikro hizmet önkoşulları** \
  <https://martinfowler.com/bliki/MicroservicePrerequisites.html>

- **Jimmy Nilsson. Öbek bulutu Bilgi Işlem** \
  <https://www.infoq.com/articles/CCC-Jimmy-Nilsson>

- **Cesar de La Torre. Microsoft platformu ve araçları** ile Kapsayıcılı Docker uygulaması yaşam döngüsü (indirilebilir e-kitap) \
  <https://aka.ms/dockerlifecycleebook>

>[!div class="step-by-step"]
>[Önceki](service-oriented-architecture.md)İleri
>[](data-sovereignty-per-microservice.md)
