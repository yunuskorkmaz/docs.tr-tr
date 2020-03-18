---
title: eShopOnContainers üzerinde bir DDD mikro hizmetine CQRS ve CQS yaklaşımları uygulama
description: .NET Microservices Mimari Containerized .NET Uygulamaları için | CQRS eShopOnContainers sipariş microservice uygulandığı nı anlayın.
ms.date: 03/03/2020
ms.openlocfilehash: 16fe46189a5b43591adebbb764d4acef2f7efbfb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "78847160"
---
# <a name="apply-cqrs-and-cqs-approaches-in-a-ddd-microservice-in-eshoponcontainers"></a>eShopOnContainers bir DDD microservice CQRS ve CQS yaklaşımları uygulayın

eShopOnContainers referans uygulamasında sipariş microservice tasarımı CQRS ilkelerine dayanmaktadır. Ancak, yalnızca komutları ayıran ve her iki eylem için aynı veritabanını kullanarak basit bir yaklaşım kullanır.

Bu desenlerin özü ve buradaki önemli nokta, sorguların iktidarlı olmasıdır: bir sistemi kaç kez sorgularsanız sorgulayın, bu sistemin durumu değişmez. Başka bir deyişle, sorgular yan etkisi ücretsizdir.

Bu nedenle, sipariş mikrohizmetleri aynı veritabanını kullanıyor olsa bile, işlem mantığı "yazar" etki alanı modelinden farklı bir "okuma" veri modeli kullanabilirsiniz. Bu nedenle, bu basitleştirilmiş bir CQRS yaklaşımıdır.

Diğer taraftan, hareketleri ve veri güncelleştirmelerini tetikleyen komutlar, sistemdeki durumu değiştirir. Komutlarla, karmaşıklık ve sürekli değişen iş kuralları ile uğraşırken dikkatli olmanız gerekir. Burada daha iyi bir modellenmiş sistem için DDD teknikleri uygulamak istediğiniz yerdir.

Bu kılavuzda sunulan DDD desenleri evrensel olarak uygulanmamalıdır. Tasarımınızda kısıtlamalar sağlarlar. Bu kısıtlamalar, özellikle komutlarda ve sistem durumunu değiştiren diğer kodlarda zaman içinde daha yüksek kalite gibi avantajlar sağlar. Ancak, bu kısıtlamalar verileri okumak ve sorgulamak için daha az avantajla karmaşıklık ekler.

Bu desenlerden biri, daha sonraki bölümlerde daha fazla inceleyediğimiz Toplam desenidir. Kısaca, Toplam desen, etki alanında ilişkilerinin bir sonucu olarak tek bir birim olarak birçok etki alanı nesneleri tedavi. Sorgularda her zaman bu modelden avantaj elde emeyebilirsiniz; sorgu mantığının karmaşıklığını artırabilir. Salt okunur sorgular için, birden çok nesneyi tek bir Toplu olarak ele almanın avantajlarını elde etmezsiniz. Sadece karmaşıklığı elde elabilirsiniz.

Önceki bölümde Şekil 7-2'de gösterildiği gibi, bu kılavuz da yalnızca microservice işlem /güncelleme alanında DDD desenleri kullanılmasını önerir (yani komutlar tarafından tetiklenir). Sorgular daha basit bir yaklaşım izleyebilir ve CQRS yaklaşımını izleyerek komutlardan ayrılmalıdır.

"Sorgular tarafını" uygulamak için, EF Core, AutoMapper projeksiyonları, depolanmış yordamlar, görünümler, maddeleştirilmiş görünümler veya mikro ORM gibi tam gelişmiş ORM'ınızdan birçok yaklaşım arasından seçim yapabilirsiniz.

Bu kılavuzda ve eShopOnContainers (özellikle sipariş microservice) biz [Dapper](https://github.com/StackExchange/dapper-dot-net)gibi bir mikro ORM kullanarak düz sorgular uygulamak için seçti. Bu, çok az yükü olan hafif bir çerçeve sayesinde en iyi performansı elde etmek için SQL deyimlerini temel alan herhangi bir sorgu uygulamanızı sağlar.

Bu yaklaşımı kullandığınızda, modelinizde varlıkların bir SQL veritabanında nasıl kalıcı olduğunu etkileyen güncelleştirmelerin, Dapper tarafından kullanılan SQL sorgularında ayrı güncelleştirmeler veya sorgulama için başka bir ayrı (EF dışı) yaklaşım olması gerektiğini unutmayın.

## <a name="cqrs-and-ddd-patterns-are-not-top-level-architectures"></a>CQRS ve DDD desenleri üst düzey mimariler değildir

CQRS ve çoğu DDD desenlerinin (DDD katmanları veya agregalı bir etki alanı modeli gibi) mimari stillerin değil, yalnızca mimari desenlerin olduğunu anlamak önemlidir. Microservices, SOA ve olay odaklı mimari (EDA) mimari stilleri örnekleridir. Birçok mikro hizmet gibi birçok bileşenden oluşan bir sistemi tanımlarlar. CQRS ve DDD desenleri tek bir sistem veya bileşen içinde bir şey açıklar; Bu durumda, bir microservice içinde bir şey.

Farklı Sınırlı Bağlamlar (CCs) farklı desenler kullanır. Farklı sorumlulukları vardır ve bu da farklı çözümlere yol açar. Her yerde aynı modele zorlamanın başarısızlığa yol açtığını vurgulamakta değerlidir. Her yerde CQRS ve DDD desenleri kullanmayın. Birçok alt sistem, CD veya mikro hizmet daha basittir ve basit CRUD hizmetleri kullanılarak veya başka bir yaklaşım kullanılarak daha kolay uygulanabilir.

Tek bir uygulama mimarisi vardır: tasarladığınız sistemin mimarisi veya uçtan uca uygulama (örneğin, mikro hizmetler mimarisi). Ancak, bu uygulama içindeki her Sınırlı Bağlam veya mikro hizmetin tasarımı, mimari desen düzeyinde kendi tradeoffs ve iç tasarım kararları yansıtır. CQRS veya DDD gibi mimari desenleri her yerde uygulamayı denemeyin.

### <a name="additional-resources"></a>Ek kaynaklar

- **Martin Fowler' ı. CQRS** \
  <https://martinfowler.com/bliki/CQRS.html>

- **Greg Young' ı. CQRS Belgeleri** \
  <https://cqrs.files.wordpress.com/2010/11/cqrs_documents.pdf>

- **Udi Dahan. Netleştirilmiş CQRS** \
  <http://udidahan.com/2009/12/09/clarified-cqrs/>

>[!div class="step-by-step"]
>[Önceki](apply-simplified-microservice-cqrs-ddd-patterns.md)
>[Sonraki](cqrs-microservice-reads.md)
