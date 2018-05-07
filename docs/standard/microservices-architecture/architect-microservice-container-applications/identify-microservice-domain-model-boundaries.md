---
title: Her mikro hizmet için etki alanı modeli sınırları tanımlama
description: Kapsayıcılı .NET uygulamaları için .NET mikro mimarisi | Her mikro hizmet için etki alanı modeli sınırları tanımlama
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.openlocfilehash: b11d2838539b8ddbe21bcfcb77845a10e466c760
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="identify-domain-model-boundaries-for-each-microservice"></a>Her mikro hizmet için etki alanı modeli sınırlarını tanımlayın

Doğru küçük mikro mümkünse eğilimindedir rağmen hedef model sınırları ve her mikro hizmet boyutu tanımlarken en ayrıntılı ayrımı mümkün değil almaktır. Bunun yerine, etki alanı bilginiz destekli en anlamlı ayrımı almak için amacınız olmalıdır. Vurgu boyutuna, ancak bunun yerine iş yeteneklerini değil. Varsa yüksek bir bağımlılıkları sayısına göre uygulamanın belirli bir bölgenin cohesion gerekli Temizle, ayrıca, tek bir mikro hizmet gereksinimini çok gösterir. Cohesion nasıl parçalayın veya grup birlikte mikro tanımlamak için bir yoldur. Sonuç olarak, etki alanı hakkında daha fazla bilgi elde ederken, mikro boyutunu tekrarlayarak uyarlamanız gerekir. Doğru boyutta bulma tek adımda bir işlem değildir.

[SAM Newman](https://samnewman.io/), tanınan bir promoter mikro ve kitap yazarı [yapı mikro](https://samnewman.io/books/building_microservices/), (parçası ilişkisindeki bağlam (BC) deseni temel alınarak, mikro tasarlamanız gerekir, önemli noktalar etki alanı Odaklı Tasarım), daha önce sunulduğu şekilde. Bazı durumlarda, bir BC birkaç fiziksel Hizmetleri ancak bunun tersi oluşan.

Bir etki alanı modeli belirli bir etki alanı varlıklarla somut BC içinde geçerlidir veya mikro hizmet. Etki alanı modeli uygulanabilirliğini bir BC sınırlandırır ve verir Geliştirici takım üyeleri Temizle ve paylaşılan anlama ne bağlı olması gerekir ve ne bağımsız olarak geliştirilebilir. Mikro hizmetler için aynı hedefleri şunlardır.

Tasarım tercih ettiğiniz bildiren bir diğer araç [Conway'in yasaları](https://en.wikipedia.org/wiki/Conway%27s_law), hangi bildiren bir uygulama, üretilen kuruluş sosyal sınırlarının yansıtır. Ancak bazen bunun tersi de geçerlidir — şirketinizin yazılımı tarafından oluşturulur. Conway'in yasaları ters çevirmek ve düzenlenmesine olanak şirket istediğinizi sınırları oluşturmak, işlem iş danışmanlık doğru leaning gerekebilir.

Sınırlanmış bağlamları belirlemek amacıyla bu için kullanılabilir bir DDD desen olan [bağlamı eşleştirme deseni](https://www.infoq.com/articles/ddd-contextmapping). Bağlam eşleme ile uygulama ve bunların sınırlarını çeşitli bağlamlarda tanımlayın. Farklı bağlamını ve küçük her alt sistemi sınır örneği için sağlamak için yaygın bir durumdur. İçerik haritası tanımlayan ve bu sınırlar etki alanları arasında açık bir yoludur. Bir BC otonom ve tek bir etki alanı ayrıntılarını içerir — ayrıntıları ister etki alanı varlıkları — ve diğer BCs tümleştirme Sözleşmelerle tanımlar. Bu bir mikro hizmet tanımına benzer: otonom, belirli etki alanı özelliği uygular ve arabirimleri sağlamanız gerekir. İçerik eşleştirme ve sınırlanmış içerik düzeni, mikro etki alanı modeli sınırlarını tanımlamak için iyi yaklaşımlar olan nedeni budur.

Büyük bir uygulama tasarlarken, nasıl kendi etki alanı modeli parçalanmış görürsünüz — Kataloğu etki alanındaki bir etki alanı Uzman varlıklar sevkiyat etki alanından uzman, katalog ve stok etki alanlarında farklı örneği için adı. Veya yalnızca kısmi veri müşteri hakkındaki gereksinim duyan sıralama bir etki alanı Uzman müşteri hakkında ayrıntılı bilgi her depolamak isteyen bir CRM Uzman ile ilgilenirken kullanıcı etki alanı varlığı boyutu ve öznitelik sayısı farklı olabilir. Çok büyük bir uygulamayla ilgili tüm etki alanları arasında tüm etki alanı koşullarını ayırt etmek zordur. Ancak en önemli terimler bütünleştirin denememelisiniz şeydir; Bunun yerine, her etki alanı tarafından sağlanan zenginliğini ve farkları kabul edin. Tüm uygulama için birleştirilmiş bir veritabanına sahip çalışırsanız, birleştirilmiş sözlük girişimleri garip olacaktır ve birden çok etki alanı uzmanlar birine sağ duyulacaktır değil. Bu nedenle, (mikro uygulanan) BCs belirli etki alanı koşullarını burada kullanabilirsiniz ve sistem bölme ve farklı etki alanlarıyla ek BCs oluşturmak burada gerekir açıklamak için yardımcı olur.

Sağ sınırları ve her BC boyutlarını aldığınız ve etki alanı modelleri arasında birkaç güçlü ilişkiler varsa ve genellikle bunu etki alanı modeli gerektiğini tipik uygulama gerçekleştirirken, birden çok etki alanı modellerinden bilgileri birleştirmek bilirsiniz işlemler.

Belki de her mikro hizmet için bir etki alanı modeli ne kadar büyük olmalıdır soru en iyi yanıt aşağıdadır: bir otonom BC olması gereken diğer bağlamlarda (diğer sürekli geçmek zorunda kalmadan çalışmanıza olanak sağlayan mümkün olduğunca yalıtılmış mikro hizmet 's modeller). Şekil 4-10'gördüğünüz birden çok mikro (birden çok BCs) her kendi modeli ve nasıl kendi varlıklar, uygulamanızda tanımlanan etki alanlarının her biri için belirli gereksinimlerine bağlı olarak tanımlanabilir sahip nasıl.

![](./media/image10.png)

**Şekil 4-10**. Varlıklar ve mikro hizmet modeli sınırları tanımlama

Şekil 4-10 bir çevrimiçi konferans yönetim sistemi için ilgili bir örnek senaryo gösterilmektedir. Mikro, etki alanı uzmanlar tanımladığınız etki alanları dayalı olarak uygulanması birkaç BCs tanımladınız. Gördüğünüz gibi yalnızca bir tek mikro hizmet modeli, ödeme mikro hizmet ödemeler gibi mevcut varlıkları vardır. Bu uygulama kolay olacaktır.

Ancak, farklı bir şekil, ancak aynı kimlik birden çok mikro birden çok etki alanı modellerinden paylaşılmasını varlıklar olabilir. Örneğin, kullanıcı varlığı konferans yönetim mikro hizmet tanımlanır. Bu aynı, aynı kimliğe sahip bir sıralama mikro alıcıların adlı veya bir ödeme mikro hizmet ve müşteri hizmetleri mikro hizmet bile bir adlandırılmış müşterinin ödeyen adlı kullanıcıdır. Bu bağlı olarak, çünkü [bulunabilen dil](https://martinfowler.com/bliki/UbiquitousLanguage.html) her etki alanı Uzman kullanarak, bir kullanıcı farklı bir perspektif bile farklı özniteliklere sahip olabilir. Kullanıcı varlığı konferans yönetim adlı mikro hizmet modelinde kişisel veri özniteliklerini çoğunu olabilir. Ancak, ödeme mikro veya müşteri hizmetleri mikro hizmet müşteri şeklinde ödeyen şeklinde, aynı kullanıcının aynı öznitelik listesine gerekmeyebilir.

Benzer bir yaklaşım Şekil 4-11'de gösterilmiştir.

![](./media/image11.png)

**Şekil 4-11**. Geleneksel veri modellerini ayırma birden fazla etki alanı modeli

Nasıl kullanıcı konferans yönetim mikro hizmet modeli kullanıcı varlık olarak bulunur ve diğer öznitelikleri ya da gerçekte bir alıcı olduğunda kullanıcı hakkındaki ayrıntıları mikro fiyatlandırma hizmet alıcı varlıkta biçiminde de mevcuttur görebilirsiniz. Her mikro hizmet veya BC sorunu çözmek için veya içeriği bağlı olarak bu, yalnızca bölüm, kullanıcı varlığıyla ilgili tüm verileri gerekmeyebilir. Örneği için fiyatlandırma mikro hizmet modeli, adres veya yalnızca kimliği (kimlik) ve bir indirimler alıcı başına kişilik fiyatlandırma zaman etkileyecek durumu, kullanıcı Kimliğini gerekmez.

Aynı bilgisayar başına varlık sahip adı her etki alanı modeli ancak farklı öznitelikleri. Ancak, bilgisayar başına aynı kimliği temel alarak kimlik paylaşımları gibi kullanıcı ve alıcı gerçekleşir.

Temel olarak, tüm bu kullanıcı kimliğini paylaşmak birden çok Hizmetleri (etki alanları), mevcut bir kullanıcı paylaşılan bir kavramı yoktur. Her etki alanı modelinde olabilir ancak kullanıcı varlık ile ilgili ek ya da farklı ayrıntıları. Bu nedenle, var. başka bir kullanıcı bir bir etki alanı (mikro) varlıktan eşleştirmek için bir yol olması gerekir.

Aynı kullanıcı varlık öznitelikleri ile aynı sayıda etki alanları arasında paylaşmıyor çeşitli avantajları vardır. Mikro hizmet modelleri gerekiyor mu herhangi bir veri olmayan bir avantajı çoğaltma azaltmak için böylelikle. Başka bir avantajı, belirli bir varlık başına veri türünü sahibi ve böylece güncelleştirmeleri ve sorguları veri türü için yalnızca bu mikro hizmet tarafından yönlendirilen ana mikro hizmet yaşıyor.


>[!div class="step-by-step"]
[Önceki] (dağıtılmış-data-management.md) [sonraki] (direct-client-to-microservice-communication-versus-the-api-gateway-pattern.md)
