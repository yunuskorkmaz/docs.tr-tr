---
title: eShopOnContainers üzerinde bir DDD mikro hizmetine CQRS ve CQS yaklaşımları uygulama
description: Kapsayıcılı .NET uygulamaları için .NET mikro hizmetleri mimarisi | CQRS 'nin eShopOnContainers 'daki sıralama mikro hizmetinde uygulanma biçimini anlayın.
ms.date: 10/08/2018
ms.openlocfilehash: 0380e759595e8a159e89f858a5ced4dacfa4e9b4
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/30/2019
ms.locfileid: "70295920"
---
# <a name="apply-cqrs-and-cqs-approaches-in-a-ddd-microservice-in-eshoponcontainers"></a>EShopOnContainers içindeki DDD mikro hizmetinde CQRS ve CQS yaklaşımları uygulama

EShopOnContainers başvuru uygulamasındaki sıralama mikro hizmetinin tasarımı, CQRS ilkelerine dayanır. Ancak, yalnızca komutlarla sorguları ayıran ve her iki eylem için aynı veritabanını kullanan en basit yaklaşımı kullanır.

Bu desenlerin özü ve önemli nokta burada, sorguların ıdempotent olduğu, bir sistemi kaç kez Sorgulayabileceğiniz önemli değildir, sistemin durumu değişmez. Diğer bir deyişle, sorgular yan etkilerden ücretsizdir.

Bu nedenle, mikro hizmetler aynı veritabanını kullanıyor olsa bile, işlem mantığı "yazma" etki alanı modelinden farklı bir "okuma" veri modeli kullanabilirsiniz. Bu nedenle, Bu basitleştirilmiş bir CQRS yaklaşımıdır.

Diğer taraftan, işlem ve veri güncelleştirmelerini tetikleyen komutlar, sistemdeki durumu değiştirir. Komutlarla, karmaşıklık ve sürekli değişen iş kuralları ile ilgilenirken dikkatli olmanız gerekir. Bu, daha iyi modellenen bir sisteme sahip olmak için DDD tekniklerini uygulamak istediğiniz yerdir.

Bu kılavuzda sunulan DDD desenleri, evrensel olarak uygulanmamalıdır. Bunlar, tasarımınızda kısıtlamalar getirir. Bu kısıtlamalar, özellikle komutlarda ve sistem durumunu değiştiren diğer kodda, zaman içinde daha yüksek kalite gibi avantajlar sağlar. Ancak, bu kısıtlamalar verileri okumak ve sorgulamak için daha az avantajlarla karmaşıklık ekler.

Bu tür bir model, daha sonraki bölümlerde daha fazla bilgi yaptığımız toplam modeldir. Kısaca, toplama modelinde, etki alanındaki ilişkisinin bir sonucu olarak birçok etki alanı nesnesini tek bir birim olarak değerlendirmiş olursunuz. Sorgularda bu örüntüden her zaman avantaj elde edemeyebilirsiniz; sorgu mantığının karmaşıklığını artırabilir. Salt okuma sorguları için birden çok nesneyi tek bir toplama olarak davranma avantajlarına sahip olursunuz. Yalnızca karmaşıklığı alırsınız.

Şekil 7-2 ' de gösterildiği gibi, bu kılavuz yalnızca mikro hizmetinizin işlem/güncelleştirme alanında (komutları tarafından tetiklenen) DDD desenlerinin kullanılmasını önerir. Sorgular daha basit bir yaklaşımla gelir ve bir CQRS yaklaşımını takip eden komutlardan ayrılmalıdır.

"Sorgular tarafını" uygulamak için EF Core, Automaber projeksiyonu, saklı yordamlar, görünümler, gerçekleştirilmiş görünümler veya mikro ORM gibi tam blown ORM arasından birçok yaklaşım arasından seçim yapabilirsiniz.

Bu kılavuzda ve eShopOnContainers 'da (özellikle sıralama mikro hizmeti), mikro [bir gibi mikro](https://github.com/StackExchange/dapper-dot-net)bir sorgu kullanarak düz sorgular uygulamayı seçtik. Bu, en iyi performansı elde etmek için SQL deyimlerine dayalı herhangi bir sorgu uygulayıp çok az ek yük içeren bir açık çatı sayesinde uygulamanızı yapmanızı sağlar.

Bu yaklaşımı kullandığınızda, modelinizdeki varlıkların bir SQL veritabanına nasıl kalıcı olduğunu etkileyen tüm güncelleştirmeler aynı zamanda, sorgulama için bir veya daha fazla farklı (EF olmayan) yaklaşım tarafından kullanılan SQL sorgularına ayrı güncelleştirmeler de gerekir.

## <a name="cqrs-and-ddd-patterns-are-not-top-level-architectures"></a>CQRS ve DDD desenleri üst düzey mimariler değildir

CQRS ve en çok DDD desenlerinin (örneğin, DDD katmanları veya toplamalar içeren bir etki alanı modeli) mimari stilleri değil, yalnızca mimari desenler olduğunu anlamak önemlidir. Mikro hizmetler, SOA ve olay odaklı mimari (EDA), mimari stillere örnektir. Birçok mikro hizmet gibi birçok bileşeni bir sistem tanımlarlar. CQRS ve DDD desenleri tek bir sistem veya bileşen içindeki bir şeyi anlatmaktadır; Bu durumda, bir mikro hizmet içindeki bir şeydir.

Farklı sınırlanmış bağlamlar (IBH) farklı desenler kullanacaktır. Farklı sorumluluklara sahiptir ve bu farklı çözümlere yol açar. Her yerde aynı modele zorlamak, hataya yol açar. CQRS ve DDD düzenlerini her yerde kullanmayın. Birçok alt sistemi, IBH veya mikro hizmet daha basittir ve basit CRUD Hizmetleri kullanılarak veya başka bir yaklaşım kullanarak daha kolay bir şekilde uygulanabilir.

Yalnızca bir uygulama mimarisi vardır: tasarlamakta olduğunuz sistemin veya uçtan uca uygulamanın mimarisi (örneğin, mikro hizmetler mimarisi). Ancak, bu uygulamadaki her sınırlı bağlam veya mikro hizmetin tasarımı, mimari desenler düzeyinde kendi dengelerini ve iç tasarım kararlarını yansıtır. CQRS veya DDD gibi her yerde aynı mimari desenleri uygulamayı denemeyin.

### <a name="additional-resources"></a>Ek kaynaklar

- **Marwler. CQRS** \
  <https://martinfowler.com/bliki/CQRS.html>

- **Greg başak. CQRS belgeleri** \
  <https://cqrs.files.wordpress.com/2010/11/cqrs_documents.pdf>

- **UDI Dahan. Açıklanan CQRS** \
  <http://udidahan.com/2009/12/09/clarified-cqrs/>

>[!div class="step-by-step"]
>[Önceki](apply-simplified-microservice-cqrs-ddd-patterns.md)İleri
>[](cqrs-microservice-reads.md)
