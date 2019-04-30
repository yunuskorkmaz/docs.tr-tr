---
title: Her mikro hizmet için etki alanı modeli sınırlarını tanımlama
description: Ses Mimarisi elde etmek için büyük bir uygulama mikro hizmetler halinde bölümleme essence keşfedin.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/20/2018
ms.openlocfilehash: 9142c5abbbd3839caac377876ba54258cdf916b4
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61689768"
---
# <a name="identify-domain-model-boundaries-for-each-microservice"></a>Her mikro hizmet etki alanı modeli sınırlarını tanımlama

Mümkünse küçük mikro hizmetler doğru eğilimli ancak en ayrıntılı ayrım mümkün almak için modeli sınırlarını ve her bir mikro hizmetin boyutu tanımlamak için kullanıldığında hedefi değil. Bunun yerine, etki alanı bilginizi destekli en anlamlı ayrımı almak için amacınız olmalıdır. Vurgu boyutuna, ancak bunun yerine iş özellikleri değildir. Yüksek bir bağımlılıklar sayısına göre uygulamanın belirli bir alanı gerekli Temizle uyumda varsa, ek olarak, tek bir mikro hizmet gereksinimi çok gösterir. Uyuma nasıl parçalayın veya grup birlikte mikro hizmetleri tanımlamak için bir yoldur. Sonuç olarak, etki alanı hakkında daha fazla bilgi sahibi olabilirsiniz, ancak boyutu, mikro hizmet çalıştırmalarınızı uyarlamanız gerekir. Doğru boyutta bulma kesin bir işlem değildir.

[SAM Newman](https://samnewman.io/), mikro hizmetler ve kitabı yazarı tanınan bir promoter [mikro hizmetler oluşturma](https://samnewman.io/books/building_microservices/), mikro hizmetlerin (parçası sınırlanmış bağlam (BC) deseni temel alınarak tasarlamanız gerekir, vurgular etki alanı Odaklı Tasarım), daha önce sunulan gibi. Bazı durumlarda, bir BC birden fazla fiziksel Hizmetleri ancak bunun tam tersinin oluşan.

Belirli bir etki alanı varlıklarının ile etki alanı modeli içinde bir somut BC uygulanır veya mikro hizmet. Bir etki alanı modeli uygulanabilirliğini bir BC sınırlandırır ve hangi cohesive ve hangi bağımsız olarak geliştirilebilir NET ve paylaşılan anlayış verir Geliştirici ekip üyeleri. Bu, aynı hedef mikro hizmetlere yönelik ücretlerdir.

Tasarım seçtiğiniz bildiren başka bir aracı [Conway'in Yasası](https://en.wikipedia.org/wiki/Conway%27s_law), hangi bildiren bir uygulamanın sosyal bunu üreten kuruluş sınırları yansıtır. Ancak bazen true - şirketinizin yazılım tarafından oluşturulmuş tersidir. Conway'in Yasası ters ve düzenlenmesine olanak şirket istediğiniz şekilde sınırları oluşturmak, işlem iş danışmanlık doğru leaning gerekebilir.

Sınırlanmış Bağlamlar tanımlamak için adlandırılan bir DDD deseni kullanabilirsiniz [bağlam eşleme düzeni](https://www.infoq.com/articles/ddd-contextmapping). İçerik eşleme ile uygulama ve sınırlarının çeşitli bağlamlarda belirleyin. Farklı bir bağlama ve her küçük bir alt sınırı örneği için çok yaygındır. İçerik haritası tanımlayan ve bu sınırlar etki alanları arasında açık bir yoludur. Bir BC otonom ve tek bir etki alanı - etki alanı varlıklarının gibi ayrıntılar - ayrıntılarını içerir ve diğer BCs tümleştirme sözleşmeleriyle tanımlar. Bir mikro hizmet tanımına benzer budur: otonom, belirli bir etki alanı özelliği uygular ve arabirimleri sağlamanız gerekir. Eşleme içeriği ve içerik sınırlanmış deseni mikro hizmetlerin etki alanı modeli sınırlarını tanımlamak için iyi bir yaklaşım olan nedeni budur.

Büyük bir uygulama tasarlarken, nasıl kendi etki alanı modeli parçalanmış göreceğiniz - bir etki alanı uzmanı Kataloğu etki alanındaki varlıklar farklı etki alanlarında katalog ve envanter sevkiyat etki alanı uzmanı, daha örneği için adı. Ya da yeni müşteri hakkındaki verilerin bir kısmını gereksinim duyan sıralama bir etki alanı uzmanı için müşteri hakkındaki ayrıntıları depolamak isteyen bir CRM Uzman ile ilgilenirken kullanıcı etki alanı varlığı boyut ve öznitelikler sayısı bakımından farklı olabilir. Büyük bir uygulamayla ilgili tüm etki alanları genelinde tüm etki alanı koşullarını ayırt etmek çok güçtür. Ancak en önemli şey koşulları buluşturulan çalışmaması gerekir. Bunun yerine, her etki alanı tarafından sağlanan zenginlik ve farkları kabul edin. Tüm uygulama için birleştirilmiş bir veritabanı çalışırsanız, birleştirilmiş sözlük girişimleri garip olacak ve birden çok etki alanı uzmanları birine sağ ses olmaz. Bu nedenle, BCs (mikro hizmetler uygulanmış), belirli bir etki alanı terimleri burada kullanabilirsiniz ve burada sistem bölme ve farklı etki alanları ile ek BCs oluşturmak ihtiyacınız olacak açıklamak için yardımcı olur.

Sağ sınırları ve her BC boyutlarını alındı ve etki alanı modeli gerekir tipik uygulama işlemleri gerçekleştirirken birden çok etki alanı modelleri bilgileri birleştirmek, etki alanı modelleri arasında birkaç güçlü ilişkiler varsa ve genellikle bunu anlarsınız .

Belki de en iyi cevabı ne kadar büyük bir etki alanı modeli için her bir mikro hizmetin olması gerektiği sorusunun yanıtını şudur: otonom bir BC olması gereken diğer bağlamları (diğer sürekli geçiş yapmak zorunda kalmadan çalışmanıza olanak sağlayan mümkün olduğunca yalıtılmış mikro hizmet'ın modeller). Şekil 4-10'da gördüğünüz birden fazla mikro hizmetler (birden çok İBH) her biri kendi modeli ve nasıl kendi varlıklar, uygulamanızda tanımlanan etki alanlarının her biri için belirli gereksinimlerine bağlı olarak tanımlanabilir değişti.

![Aynı varlık "Kullanıcılar", "Alıcıların", "Ödeyen" ve "Müşteri" sınırlanmış bağlam bağlı olarak göründüğü çeşitli varlıklarda sınırları (sınırlanmış Bağlamlar) modeli](./media/image10.png)

**Şekil 4-10**. Varlıklar ve mikro hizmet modeli sınırlarını tanımlama

Şekil 4-10 çevrimiçi bir konferans yönetim sistemiyle ilgili bir örnek senaryo gösterilmektedir. Mikro hizmetler, etki alanı uzmanları tanımladığınız etki alanları dayalı olarak uygulanması birkaç BCs tespit ettik. Gördüğünüz gibi mevcut ödeme mikro hizmet ödemeler gibi bir tek bir mikro hizmet modelinde yalnızca varlık vardır. Bu, uygulaması kolay olacaktır.

Ancak, farklı olan, ancak aynı kimlik birden fazla mikro Hizmetleri birden çok etki alanı modellerden paylaşılmasını varlıkları olabilir. Örneğin, kullanıcı varlığı konferans yönetim mikro hizmet içinde tanımlanır. Bu aynı kullanıcı, aynı kimliğe sahip bir sipariş mikro eğilimlerinden adlı veya bir ödeme mikro hizmet ve hatta bir adlandırılmış Müşteri Müşteri Hizmetleri mikro hizmet ödeyen kişi adlı olur. Bu ayarlara bağlı olarak, çünkü [bulunabilen dil](https://martinfowler.com/bliki/UbiquitousLanguage.html) her etki alanı uzmanı kullanarak, bir kullanıcı farklı bir perspektif bile farklı özniteliklere sahip olabilir. Konferans yönetim adlı mikro hizmet modelinde kullanıcı varlığı kişisel veri özniteliklerini çoğunu olabilir. Ancak, ödeme mikro hizmet veya müşteri hizmetleri mikro hizmet müşteri şeklinde ödeyen şeklinde, aynı kullanıcının aynı öznitelik listesine gerekmeyebilir.

Benzer bir yaklaşım, Şekil 4-11'de gösterilmiştir.

![Geleneksel veri modeli sınırlanmış Bağlamlar arasında parçalama, sınırlanmış her bağlam içinde farklı özniteliklerle aynı kimliğe (bir alıcı da bir kullanıcıdır) paylaşan farklı varlıklar sahip olabilir.](./media/image11.png)

**Şekil 4-11**. Geleneksel veri modellerini parçalama birden çok etki alanı modeli

Nasıl kullanıcı konferans yönetim mikro hizmet modelinde kullanıcı varlığı olarak mevcut olduğundan ve ayrıca formunda alıcı varlık başka öznitelikler veya aslında bir alıcı olduğunda kullanıcı hakkındaki ayrıntıları fiyatlandırma mikro hizmet içinde mevcut olduğundan görebilirsiniz. Sorunu çözmek için veya içeriği bağlı olarak bu, yalnızca bölüm, kullanıcı varlığı için ilgili tüm verileri, her bir mikro hizmet veya BC gerekmeyebilir. Örneği için fiyatlandırma mikro hizmet modelinde, adres veya yalnızca kimliği (kimlik) ve bir indirimler zaman alıcı başına lisans fiyatlandırma etkisi durumu, kullanıcı adını ihtiyacınız yoktur.

Bilgisayar varlık aynı olan ad ancak farklı öznitelikleri her etki alanı modeli. Ancak, aynı kimliği temel alarak kimlik lisans paylaşan kullanıcı ve alıcı ile'olmuyor gibi.

Temel olarak, tüm kullanıcı kimliğini paylaşan birden çok hizmetler (etki alanları), mevcut bir kullanıcının paylaşılan bir kavram yoktur. Her etki alanı modeli içinde olabilir ancak kullanıcı varlığı hakkındaki ek veya bunlardan farklı ayrıntıları. Bu nedenle, vardır (mikro) bir etki alanından kullanıcı varlığı için başka bir yolu olması gerekir.

Etki alanları arasında aynı kullanıcı varlığı öznitelikleri ile aynı sayıda kullanılmadığı için çeşitli avantajları vardır. Mikro hizmet modellerini ihtiyaç herhangi bir veri gerekmemesi yararlarından biri çoğaltma azaltmaktır. Başka bir avantajı, belirli bir tür varlık başına veri sahibi ve böylece güncelleştirmeler ve sorgular veri türü için yalnızca bu mikro hizmet tarafından yönlendirilen ana bir mikro hizmet yaşıyor.

>[!div class="step-by-step"]
>[Önceki](distributed-data-management.md)
>[İleri](direct-client-to-microservice-communication-versus-the-api-gateway-pattern.md)