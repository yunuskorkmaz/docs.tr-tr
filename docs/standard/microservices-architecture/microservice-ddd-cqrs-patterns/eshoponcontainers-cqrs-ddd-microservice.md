---
title: eShopOnContainers üzerinde bir DDD mikro hizmetine CQRS ve CQS yaklaşımları uygulama
description: Kapsayıcılı .NET uygulamaları için .NET mikro hizmet mimarisi | Sıralama mikro hizmetine CQRS uygulanan şekilde anlayın.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/08/2018
ms.openlocfilehash: fc8c27c25fb6d07207586eb65d5ac9cc543bcc1a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61818007"
---
# <a name="apply-cqrs-and-cqs-approaches-in-a-ddd-microservice-in-eshoponcontainers"></a>Bir DDD mikro hizmetine CQRS ve CQS yaklaşımları uygulama

CQRS kurallara göre sıralama mikro hizmetine başvuru uygulama tasarımının temel alır. Ancak, yalnızca sorguları komutlardan ayrılması ve için her iki eylem aynı veritabanını kullanarak basit bir yaklaşım kullanır.

Bu desen ve burada önemli olan nokta, sorguları eşgüçlüdür olduğu: bir sistem sorgu kaç kez ne olursa olsun, bu sistem durumu değişmez. Diğer bir deyişle, sorguların yan etkisi ücretsiz.

Bu nedenle, etki alanı modeli işlem mantığı "Yazar daha" sıralama mikro hizmetler aynı veritabanı kullanıyor olsa bile farklı "Okuma" veri modelini kullanabilirsiniz. Bu nedenle, Basitleştirilmiş bir CQRS yaklaşım budur.

Öte yandan, işlemleri ve veri güncelleştirmeleri tetiklemek, komutları, sistemin durumunu değiştirin. Komutları ile ne zaman dikkatli olmanız gerekir. karmaşıklığı ve durmaksızın değişen iş kuralları ile ilgili. Burada bir daha iyi Modellenen sistem olacak şekilde DDD teknikleri uygulamak istediğiniz.

Bu kılavuzda sunulan DDD deseni Evrensel uygulanmamalıdır. Bunlar, tasarımınızı kısıtlamalar sunar. Bu kısıtlamaları, özellikle de komutlar ve sistem durumunu değiştiren diğer kodun zaman içinde daha yüksek kalite gibi avantajlar sağlar. Ancak, bu kısıtlamaları okuma ve veri sorgulama için daha az avantajlarla karmaşıklık ekleyin.

Bir desen daha sonraki bölümlerde inceleyeceğiz toplama modelidir. Kısaca, toplama modelinde, birçok etki alanı nesnelerini ilişkilerini etki alanındaki bir sonucu olarak tek bir birim olarak kabul eder. Her zaman bu sorguları modelinde avantajları elde edebilir değil; Bu sorgu mantığının karmaşıklığını artırabilirsiniz. Salt okunur sorguların birden çok nesne tek bir toplamada değerlendirmesini avantajlarını elde ederim. Yalnızca karmaşıklığı sahip olursunuz.

Şekil 7-2'de gösterildiği gibi bu Kılavuzu (diğer bir deyişle, komutları tarafından tetiklenen gibi) yalnızca, mikro işlem/güncelleştirmelerini alan DDD deseni kullanılarak önerir. Sorguları basit bir yaklaşım izleyerek ve bir CQRS yaklaşımı izleyerek komutlarından ayrılmalıdır.

"Sorgu yan" uygulamak için tam ORM EF Core, AutoMapper tahminler, saklı yordamları, görünümleri, gerçekleştirilmiş görünümler veya mikro ORM gibi gelen birçok yaklaşım arasında seçim yapabilirsiniz.

Bu kılavuzda hem seçtik düz sorguları kullanarak bir mikro hizmetine (özellikle sıralama mikro) ORM ister [Dapper](https://github.com/StackExchange/dapper-dot-net). Bu bir açık çerçeve çok az bir Giderle sayesinde en iyi performansı elde etmek için SQL deyimleri göre herhangi bir sorgu uygulamanıza olanak sağlar.

Bu yaklaşımı kullandığınızda, varlıklar bir SQL veritabanı'na nasıl kalıcı etkileyen herhangi bir güncelleştirme modelinizi ayrıca Dapper veya sorgulama herhangi diğer ayrı (EF olmayan) yaklaşımları tarafından kullanılan SQL sorguları için ayrı güncelleştirmeler gerektiğini unutmayın.

## <a name="cqrs-and-ddd-patterns-are-not-top-level-architectures"></a>CQRS ve DDD desenlerini en üst düzey mimari değildir.

CQRS ve çoğu DDD deseni (DDD katmanları veya bir etki alanı modeli toplamalar ile gibi) mimari stilleri, ancak yalnızca mimarisi desenleri değil olduğunu anlama açısından önemlidir. Mikro hizmetler ve SOA olay denetimli mimari (EDA) mimari stilleri örnekleridir. Bunlar bir sistemin birçok mikro hizmetler gibi birçok bileşen açıklanmaktadır. CQRS ve DDD desenlerini, tek bir sistem veya bileşeni içinde bir şeyi anlatma; Bu durumda, bir mikro hizmet içinde bir şey.

Farklı sınırlanmış Bağlamlar (İBH) farklı desenleri kullanılacaktır. Bunlar farklı sorumluluklara sahiptir ve bu farklı çözümler için gidiyor. Bu değer, her yerde yıpranmasıyla aynı düzeni zorlama vurgulama olur. CQRS ve DDD desenlerini her yerde kullanmayın. Çok sayıda alt sistemler, BCs veya mikro hizmet daha basittir ve basit CRUD Hizmetleri daha kolay veya başka bir yaklaşım kullanarak uygulanabilir.

Yalnızca bir uygulama mimari: Sistem veya uçtan uca uygulama mimarisi (örneğin, mikro hizmetler Mimarisi) tasarlarken. Ancak, her bir sınırlanmış bağlam veya mikro hizmet, uygulama içinde tasarımını kendi ödün ve iç tasarım kararları bir mimari desenleri düzeyinde yansıtır. Aynı mimari desenleri CQRS veya DDD gibi her yerde uygulamak çalışmayın.

### <a name="additional-resources"></a>Ek kaynaklar

- **Martin Fowler. CQRS** \
  <https://martinfowler.com/bliki/CQRS.html>

- **Greg Young. CQS vs. CQRS** \
  <http://codebetter.com/gregyoung/2009/08/13/command-query-separation/>

- **Greg Young. CQRS belgeleri** \
  [https://cqrs.files.wordpress.com/2010/11/cqrs\_documents.pdf](https://cqrs.files.wordpress.com/2010/11/cqrs_documents.pdf)

- **Greg Young. CQRS, görev tabanlı kullanıcı arabirimleri ve olay kaynağını belirleme** \
  <http://codebetter.com/gregyoung/2010/02/16/cqrs-task-based-uis-event-sourcing-agh/>

- **UDI Dahan. Açıklanan CQRS** \
  <http://udidahan.com/2009/12/09/clarified-cqrs/>

- **Olay kaynak belirleme (ES)** \
  <http://codebetter.com/gregyoung/2010/02/20/why-use-event-sourcing/>

>[!div class="step-by-step"]
>[Önceki](apply-simplified-microservice-cqrs-ddd-patterns.md)
>[İleri](cqrs-microservice-reads.md)
