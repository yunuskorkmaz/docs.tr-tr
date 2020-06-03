---
title: eShopOnContainers üzerinde bir DDD mikro hizmetine CQRS ve CQS yaklaşımları uygulama
description: Kapsayıcılı .NET uygulamaları için .NET mikro hizmetleri mimarisi | CQRS 'nin eShopOnContainers 'daki sıralama mikro hizmetinde uygulanma biçimini anlayın.
ms.date: 03/03/2020
ms.openlocfilehash: 2916df596a6d0f887411f3ef0074aed395ef58ba
ms.sourcegitcommit: 5280b2aef60a1ed99002dba44e4b9e7f6c830604
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/03/2020
ms.locfileid: "84306948"
---
# <a name="apply-cqrs-and-cqs-approaches-in-a-ddd-microservice-in-eshoponcontainers"></a>EShopOnContainers içindeki DDD mikro hizmetinde CQRS ve CQS yaklaşımları uygulama

EShopOnContainers başvuru uygulamasındaki sıralama mikro hizmetinin tasarımı, CQRS ilkelerine dayanır. Ancak, yalnızca komutlarla sorguları ayıran ve her iki eylem için aynı veritabanını kullanan en basit yaklaşımı kullanır.

Bu desenlerin özü ve önemli nokta burada, sorguların ıdempotent olduğu, bir sistemi kaç kez Sorgulayabileceğiniz önemli değildir, sistemin durumu değişmez. Diğer bir deyişle, sorgular yan etkilerden ücretsizdir.

Bu nedenle, mikro hizmetler aynı veritabanını kullanıyor olsa bile, işlem mantığı "yazma" etki alanı modelinden farklı bir "okuma" veri modeli kullanabilirsiniz. Bu nedenle, Bu basitleştirilmiş bir CQRS yaklaşımıdır.

Diğer taraftan, işlem ve veri güncelleştirmelerini tetikleyen komutlar, sistemdeki durumu değiştirir. Komutlarla, karmaşıklık ve sürekli değişen iş kuralları ile ilgilenirken dikkatli olmanız gerekir. Bu, daha iyi modellenen bir sisteme sahip olmak için DDD tekniklerini uygulamak istediğiniz yerdir.

Bu kılavuzda sunulan DDD desenleri, evrensel olarak uygulanmamalıdır. Bunlar, tasarımınızda kısıtlamalar getirir. Bu kısıtlamalar, özellikle komutlarda ve sistem durumunu değiştiren diğer kodda, zaman içinde daha yüksek kalite gibi avantajlar sağlar. Ancak, bu kısıtlamalar verileri okumak ve sorgulamak için daha az avantajlarla karmaşıklık ekler.

Bu tür bir model, daha sonraki bölümlerde daha fazla bilgi yaptığımız toplam modeldir. Kısaca, toplama modelinde, etki alanındaki ilişkisinin bir sonucu olarak birçok etki alanı nesnesini tek bir birim olarak değerlendirmiş olursunuz. Sorgularda bu örüntüden her zaman avantaj elde edemeyebilirsiniz; sorgu mantığının karmaşıklığını artırabilir. Salt okuma sorguları için birden çok nesneyi tek bir toplama olarak davranma avantajlarına sahip olursunuz. Yalnızca karmaşıklığı alırsınız.

Şekil 7-2 ' de gösterildiği gibi, bu kılavuzda, yalnızca mikro hizmetinizin işlem/güncelleştirme alanındaki (komutları tarafından tetiklenen) DDD desenlerinin kullanılması önerilir. Sorgular daha basit bir yaklaşımla gelir ve bir CQRS yaklaşımını takip eden komutlardan ayrılmalıdır.

"Sorgular tarafını" uygulamak için EF Core, Automaber projeksiyonu, saklı yordamlar, görünümler, gerçekleştirilmiş görünümler veya mikro ORM gibi tam blown ORM arasından birçok yaklaşım arasından seçim yapabilirsiniz.

Bu kılavuzda ve eShopOnContainers 'da (özellikle sıralama mikro hizmeti), mikro [bir gibi mikro](https://github.com/StackExchange/dapper-dot-net)bir sorgu kullanarak düz sorgular uygulamayı seçtik. Bu, en iyi performansı elde etmek için SQL deyimlerine dayalı herhangi bir sorgu uygulamanızı sağlar.

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
  <https://udidahan.com/2009/12/09/clarified-cqrs/>

>[!div class="step-by-step"]
>[Önceki](apply-simplified-microservice-cqrs-ddd-patterns.md) 
> [Sonraki](cqrs-microservice-reads.md)
