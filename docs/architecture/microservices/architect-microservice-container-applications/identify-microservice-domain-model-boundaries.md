---
title: Her mikro hizmet için etki alanı modeli sınırlarını tanımlama
description: Sağlam bir mimari elde etmek için büyük bir uygulamayı mikro hizmetlere bölmenin özünü keşfedin.
ms.date: 09/20/2018
ms.openlocfilehash: 9c433066dd8e93dbb09b15e58c9c85617775723d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "71834409"
---
# <a name="identify-domain-model-boundaries-for-each-microservice"></a>Her microservice için etki alanı modeli sınırlarını belirleme

Her microservice için model sınırları ve boyutu tanımlarken amaç mümkün olan en ayrıntılı ayırma almak için değil, mümkünse küçük mikrohizmetler doğru eğiliminde olmalıdır rağmen. Bunun yerine, amacınız etki alanı bilginiz tarafından yönlendirilen en anlamlı ayrıma ulaşmak olmalıdır. Vurgu boyutu değil, iş yetenekleri üzerindedir. Buna ek olarak, yüksek sayıda bağımlılıkları temel alan uygulamanın belirli bir alanı için gereken açık bir uyum varsa, bu da tek bir mikro hizmet gereksinimini gösterir. Uyum, parçalanmanın veya mikro hizmetlerin nasıl gruplandırılabildiğini belirlemenin bir yoludur. Sonuç olarak, etki alanı hakkında daha fazla bilgi edinirken, mikro hizmetinizin boyutunu yinelemeli olarak uyarlamanız gerekir. Doğru boyutu bulmak tek çekimlik bir işlem değildir.

[Sam Newman](https://samnewman.io/), mikrohizmetler tanınmış bir organizatörü ve kitap [Building Microservices](https://samnewman.io/books/building_microservices/)yazarı , size Sınırlı Bağlam (BC) desen (etki alanı odaklı tasarımın bir parçası) dayalı mikrohizmetler tasarlamak gerektiğini vurgulamaktadır, daha önce tanıtıldı. Bazen, bir BC birkaç fiziksel hizmetlerden oluşabilir, ancak tam tersi olmayabilir.

Belirli etki alanı varlıklarına sahip bir etki alanı modeli, somut bir BC veya microservice içinde geçerlidir. BC, bir etki alanı modelinin uygulanabilirliğini kısıtlar ve geliştirici ekip üyelerine neyin uyumlu olması ve bağımsız olarak nelerin geliştirilebileceği hakkında açık ve ortak bir anlayış sağlar. Bunlar mikro hizmetler için aynı hedeflerdir.

Tasarım seçiminizi bildiren bir diğer araç [da,](https://en.wikipedia.org/wiki/Conway%27s_law)bir uygulamanın onu üreten kuruluşun sosyal sınırlarını yansıtacağını belirten Conway yasasıdır. Ama bazen tam tersi doğrudur -şirketin organizasyonu yazılım tarafından oluşturulur. Conway'in yasasını tersine çevirmen ve şirketin organize olmasını istediğiniz şekilde sınırları oluşturmanız gerekebilir, iş süreci danışmanlığına eğilmeniz gerekebilir.

Sınırlanmış bağlamları tanımlamak için [Bağlam Eşleme deseni](https://www.infoq.com/articles/ddd-contextmapping)adı verilen bir DDD deseni kullanabilirsiniz. Bağlam Eşleme ile, uygulamadaki çeşitli bağlamları ve bunların sınırlarını tanımlarsınız. Örneğin, her küçük alt sistem için farklı bir bağlam ve sınır olması yaygındır. Bağlam Haritası, etki alanları arasındaki bu sınırları tanımlamanın ve açıkça ifade etmenin bir yoludur. BC özerktir ve etki alanı varlıkları gibi tek bir etki alanının ayrıntılarını içerir ve diğer BC'lerle tümleştirme sözleşmeleri tanımlar. Bu bir microservice tanımına benzer: bu özerk, belirli etki alanı yeteneği uygular ve arayüzleri sağlaması gerekir. Bu nedenle Bağlam Eşleme ve Sınırlanmış Bağlam deseni, mikro hizmetlerinizin etki alanı modeli sınırlarını belirlemek için iyi yaklaşımlardır.

Büyük bir uygulama tasarlarken, etki alanı modelinin nasıl parçalanabileceğini görürsünüz - katalog etki alanından bir etki alanı uzmanı, örneğin katalog ve stok etki alanlarındaki varlıkları bir gönderi etki alanı uzmanından farklı adlandıracaktır. Veya kullanıcı etki alanı varlığı, müşteri hakkında kısmi verilere ihtiyaç duyan bir sipariş etki alanı uzmanından daha çok müşteri yle ilgili her ayrıntıyı depolamak isteyen bir CRM uzmanıyla uğraşırken boyut ve öznitelik sayısı açısından farklı olabilir. Büyük bir uygulamayla ilgili tüm etki alanlarındaki tüm etki alanı terimlerini birbirinden ayrıştırmak çok zordur. Ama en önemli şey şartları birleştirmeye çalışmamanız. Bunun yerine, her etki alanı tarafından sağlanan farklılıkları ve zenginliği kabul edin. Tüm uygulama için birleşik bir veritabanına sahip olmaya çalışırsanız, birleşik bir sözcük dağarcığı denemeleri garip olacaktır ve birden çok etki alanı uzmanının hiçbirine doğru gelmez. Bu nedenle, BC'ler (mikro hizmetler olarak uygulanan) belirli etki alanı terimlerini nerede kullanabileceğinizi ve sistemi nerede bölmeniz ve farklı etki alanlarıyla ek BC'ler oluşturmanız gerektiğini açıklığa kavuşturmaya yardımcı olur.

Etki alanı modelleri arasında birkaç güçlü ilişkiniz varsa ve tipik uygulama işlemleri gerçekleştirirken genellikle birden çok etki alanı modelindeki bilgileri birleştirmeniz gerekmiyorsa, her BC ve etki alanı modelinin doğru sınırlarına ve boyutlarına sahip olduğunuzu bileceksiniz. .

Her mikro hizmet için ne kadar büyük bir etki alanı modeli nin olması gerektiği sorusuna belki de en iyi cevap şudur: mümkün olduğunca izole edilmiş özerk bir BC'ye sahip olmalıdır ve bu da sürekli olarak diğer bağlamlara geçmenize gerek kalmadan çalışmanızı sağlar (diğer microservice modelleri). Şekil 4-10'da, birden çok mikro hizmetin (birden çok BC) her birinin kendi modeline nasıl sahip olduğunu ve uygulamanızdaki tanımlanan etki alanlarının her biri için özel gereksinimlere bağlı olarak varlıklarının nasıl tanımlanabileceğini görebilirsiniz.

![Çeşitli model sınırlarındaki varlıkları gösteren diyagram.](./media/identify-microservice-domain-model-boundaries/identify-entities-microservice-model-boundries.png)

**Şekil 4-10**. Varlıkların ve mikrohizmet modeli sınırlarının belirlenmesi

Şekil 4-10, çevrimiçi konferans yönetim sistemiyle ilgili örnek bir senaryoyu göstermektedir. Aynı varlık, sınırlanan içeriğe bağlı olarak "Kullanıcılar", "Alıcılar", "Mükellefler" ve "Müşteriler" olarak görünür. Etki alanı uzmanlarının sizin için tanımladığı etki alanlarını temel alan olarak mikro hizmetler olarak uygulanabilecek birkaç BC belirlediniz. Gördüğünüz gibi, ödeme mikrohizmetindeki Ödemeler gibi tek bir mikro hizmet modelinde bulunan varlıklar vardır. Bunları uygulamak kolay olacak.

Ancak, farklı bir şekle sahip ancak birden çok mikro hizmetten birden çok etki alanı modelinde aynı kimliği paylaşan varlıklar da olabilir. Örneğin, Kullanıcı varlığı Konferansyönetimi Yönetimi mikrohizmetinde tanımlanır. Aynı kullanıcı, aynı kimliğe sahip, Sipariş microservice Alıcılar adlı veya Ödeme microservice payer adlı ve hatta müşteri hizmetleri microservice müşteri adlı biridir. Bunun nedeni, her etki alanı uzmanının kullandığı [her yerde](https://martinfowler.com/bliki/UbiquitousLanguage.html) bulunan dile bağlı olarak, bir kullanıcının farklı özniteliklere sahip olsa bile farklı bir perspektife sahip olmasıdır. Konferansyönetimi adlı mikrohizmet modelindeki kullanıcı varlığı, kişisel veri özniteliklerinin çoğuna sahip olabilir. Ancak, microservice Payment'da veya microservice Müşteri Hizmetleri'nde Müşteri şeklinde ki aynı kullanıcının aynı öznitelikler listesine ihtiyacı olmayabilir.

Benzer bir yaklaşım Şekil 4-11'de gösterilmiştir.

![Bir veri modelinin birden çok etki alanı modeline nasıl ayrıştırılabildiğini gösteren diyagram.](./media/identify-microservice-domain-model-boundaries/decompose-traditional-data-models.png)

**Şekil 4-11**. Geleneksel veri modellerini birden çok etki alanı modeline dönüştürme

Geleneksel bir veri modelini sınırlanmış bağlamlar arasında ayrıştırırken, her sınırlı bağlamda farklı özniteliklere sahip aynı kimliği (alıcı da kullanıcıdır) paylaşan farklı varlıklara sahip olabilirsiniz. Kullanıcı varlığı olarak Konferanslar Yönetimi mikrohizmet modelinde kullanıcının nasıl bulunduğunu ve aslında bir alıcı olduğunda kullanıcı hakkında alternatif öznitelikler veya ayrıntılarla Fiyatlandırma mikrohizmetinde Alıcı varlık biçiminde nasıl bulunduğunu görebilirsiniz. Her microservice veya BC, çözülmesi gereken soruna veya içeriğe bağlı olarak, kullanıcı varlığıyla ilgili tüm verilere, yalnızca bir kısmına ihtiyaç duymayabilir. Örneğin, Fiyatlandırma mikrohizmet modelinde, alıcı başına koltukları fiyatlarken indirimler üzerinde etkisi olacak yalnızca kimlik (kimlik olarak) ve Durum adresine veya kullanıcının adına ihtiyacınız yoktur.

Seat varlığı, her etki alanı modelinde aynı ada ancak farklı özelliklere sahiptir. Ancak Seat, Kullanıcı ve Alıcı'da olduğu gibi aynı kimliğe dayalı olarak kimlik paylaşır.

Temel olarak, birden çok hizmette (etki alanlarında) bulunan ve tüm kullanıcının kimliğini paylaşan paylaşılan bir kullanıcı kavramı vardır. Ancak her etki alanı modelinde kullanıcı varlığı hakkında ek veya farklı ayrıntılar olabilir. Bu nedenle, bir kullanıcı varlığını bir etki alanından (mikro hizmet) diğerine eşleninin bir yolu olması gerekir.

Aynı kullanıcı varlığını etki alanları arasında aynı sayıda öznitelikle paylaşmamak için çeşitli avantajlar vardır. Bir yararı çoğaltma azaltmak için, böylece microservice modelleri gerek meyen herhangi bir veri yok. Başka bir yararı, bu tür veriler için güncelleştirmeler ve sorgular yalnızca bu mikro hizmet tarafından tahrik böylece varlık başına veri belirli bir tür sahibi bir ana microservice sahip olmasıdır.

>[!div class="step-by-step"]
>[Önceki](distributed-data-management.md)
>[Sonraki](direct-client-to-microservice-communication-versus-the-api-gateway-pattern.md)
