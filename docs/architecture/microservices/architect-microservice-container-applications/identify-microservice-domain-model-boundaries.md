---
title: Her mikro hizmet için etki alanı modeli sınırlarını tanımlama
description: Bir ses mimarisine ulaşmak için büyük bir uygulamayı mikro hizmetlere bölümlemenin özünü inceleyelim.
ms.date: 09/20/2018
ms.openlocfilehash: aa903e13b20be1084fad60e6fb7bbb1c61403deb
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/30/2019
ms.locfileid: "70295504"
---
# <a name="identify-domain-model-boundaries-for-each-microservice"></a>Her mikro hizmet için etki alanı modeli sınırlarını tanımla

Her mikro hizmet için model sınırlarını ve boyutunu tanımlarken hedef, mümkün olduğunda küçük mikro hizmetlere yaklaşmanız mümkün olsa da en ayrıntılı ayrımı almak zorunda değildir. Bunun yerine, amacınız, etki alanı bilginiz tarafından Kılavuzlu en anlamlı ayrımı almak için olmalıdır. Vurgu, iş özelliklerine göre değil, boyutta değil. Ayrıca, tek bir mikro hizmet gereksinimini de belirten çok sayıda bağımlılığı temel alan uygulamanın belirli bir alanı için gerekli bir cohemi vardır. Cohema, mikro hizmetlerin nasıl parçalanacağına veya gruplandırılabileceğine ilişkin bir yoldur. Sonuç olarak, etki alanı hakkında daha fazla bilgi edinirken, mikro hizmetinizin boyutunu tekrarlayarak uyarlayabilirsiniz. Doğru boyutu bulmak tek bir görüntü işleme değildir.

Mikro hizmet [oluşturma](https://samnewman.io/books/building_microservices/)bölümünde tanınan bir mikro hizmet ve yazar olan [Sam Newman](https://samnewman.io/), mikro hizmetleri, sınırlanmış bağlam (BC) düzenine (etki alanı odaklı tasarımın parçası) göre tasarlamanız gerektiğini vurgular öncesiyle. Bazı durumlarda, bir BC birkaç fiziksel hizmetten oluşabilir, ancak tersi de değildir.

Belirli etki alanı varlıklarını içeren bir etki alanı modeli somut bir BC veya mikro hizmet içinde geçerlidir. Bir BC, bir etki alanı modelinin uygulanabilirliğini ayırır ve geliştirici ekibi üyelerine, nelerin birlikte kullanılması gerektiğini ve bağımsız olarak ne tür bir şekilde geliştirileceğini anlamak için açık ve paylaşılan bir anlama sağlar. Bunlar, mikro hizmetler için aynı hedeflerdir.

Tasarım seçiminizi bildiren bir başka araç da, uygulamayı üreten kuruluşun sosyal sınırlarını yansıttığından emin olmak üzere, bir uygulamanın [yasaların yasaları](https://en.wikipedia.org/wiki/Conway%27s_law)olduğunu gösterir. Ancak bazen bunun tersi de geçerlidir; şirketin kuruluşu yazılım tarafından oluşturulur. Conway 'in yasalarını tersine çevirmek ve sınırları şirket içinde organize etmek istediğiniz şekilde oluşturmak, iş süreci Danışmanlığı ' na yaklaşmanız gerekebilir.

Sınırlanmış bağlamları belirlemek için [bağlam eşleme düzeniyle](https://www.infoq.com/articles/ddd-contextmapping)ADLANDıRıLAN bir ddd deseninin kullanabilirsiniz. Bağlam eşleme ile, uygulamadaki çeşitli bağlamlarını ve bunların sınırlarını belirlersiniz. Örneğin, her küçük alt sistem için farklı bir bağlam ve sınırın olması yaygındır. Bağlam Haritası, etki alanları arasında bu sınırları tanımlamanın ve açık hale getirmenin bir yoludur. Bir BC özerk olur ve etki alanı varlıkları gibi tek bir etki alanı ayrıntılarının ayrıntılarını içerir ve diğer IBH ile tümleştirme sözleşmelerini tanımlar. Bu, bir mikro hizmetin tanımına benzerdir: otonom, belirli etki alanı yeteneklerini uygular ve arabirim sağlamalıdır. Bağlam eşlemenin ve sınırlanmış bağlam deseninin, mikro hizmetlerinizin etki alanı model sınırlarını belirlemek için iyi yaklaşımlar vardır.

Büyük bir uygulama tasarlarken, etki alanı modelinin nasıl parçalandığını görürsünüz. katalog etki alanındaki bir etki alanı uzmanı, varlıkları katalogda bir nakliye etki alanı uzmanından farklı olarak adlandırır. Ya da Kullanıcı etki alanı varlığı, müşteriyle ilgili her ayrıntıyı depolamak isteyen bir CRM uzmanı ile ilgilenirken, müşteri hakkında kısmi verilere ihtiyaç duyan bir sipariş etki alanı uzmanından farklı olabilir. Büyük bir uygulamayla ilgili tüm etki alanları genelinde tüm etki alanı koşullarını ortadan kaldırmak çok zordur. Ancak en önemli şey, terimleri birleştirmenize çalışmayın. Bunun yerine, her etki alanı tarafından sunulan farkları ve zenginleştirmesi kabul edin. Uygulamanın tamamına yönelik Birleşik bir veritabanına sahip olmak istiyorsanız, birleştirilmiş bir sözlük için denemeler sürme olur ve birden çok etki alanı uzmanından birine doğrudan yönelmeyecektir. Bu nedenle, BCs (mikro hizmetler olarak uygulanır), belirli etki alanı terimlerini nerede kullanacağınızı ve farklı etki alanları ile ek BCs oluşturmanız gerektiğini açıklığa kavuşturmanıza yardımcı olur.

Etki alanı modelleri arasında çok sayıda güçlü ilişki varsa ve genellikle tipik uygulama işlemlerini gerçekleştirirken birden fazla etki alanı modelinden bilgi birleştirmeniz gerekmiyorsa, her bir BC ve etki alanı modelinin doğru sınırlarını ve boyutlarını bildiğinizi bilirsiniz .

Her mikro hizmet için büyük bir etki alanı modelinin nasıl olması gerektiğine ilişkin en iyi yanıt, olası olarak, diğer bağlamlara geçiş yapmak zorunda kalmadan çalışmanıza olanak tanıyan bir otonom BC içermelidir. (diğer Mikro hizmetin modelleri). Şekil 4-10 ' de, birden fazla mikro hizmetin (birden çok BCs) kendi modeline sahip olduğunu ve uygulamanızda tanımlanan her bir etki alanının belirli gereksinimlerine bağlı olarak varlıkların nasıl tanımlanabileceğiz görebilirsiniz.

![Aynı varlığın "kullanıcılar", "alıcılar", "Ödeiciler" ve "müşteriler" olarak göründüğü, sınırlı içeriğe bağlı olarak, çeşitli model sınırlarındaki (sınırlanmış bağlamlar) varlıklar](./media/image10.png)

**Şekil 4-10**. Varlıkları ve mikro hizmet modeli sınırlarını tanımlama

Şekil 4-10, çevrimiçi bir konferans yönetim sistemiyle ilgili örnek bir senaryoyu göstermektedir. Etki alanı uzmanlarının sizin için tanımladığı etki alanlarına bağlı olarak, mikro hizmetler olarak uygulanabilecek birkaç IBH tanımladınız. Gördüğünüz gibi, ödeme mikro hizmetindeki ödemeler gibi yalnızca tek bir mikro hizmet modelinde bulunan varlıklar vardır. Bunlar, kolayca uygulanabilir.

Ancak, farklı bir şekle sahip olan ancak aynı kimliği birden çok mikro hizmetten oluşan birden fazla etki alanı modeli genelinde paylaşan varlıklara de sahip olabilirsiniz. Örneğin, kullanıcı varlığı, konferanslar yönetim mikro hizmetinde tanımlanmıştır. Aynı kimliğe sahip aynı kullanıcı, sipariş mikro hizmetindeki alıcıların adı, ödeme mikro hizmetindeki ödeyen adı, hatta müşteri hizmeti mikro hizmetindeki müşteri olarak adlandırılan bir kullanıcı. Bunun nedeni, her etki alanı uzmanının kullandığı [ubititous diline](https://martinfowler.com/bliki/UbiquitousLanguage.html) bağlı olarak, bir kullanıcının farklı özniteliklere sahip farklı bir perspektife sahip olabilir. Konferanslar yönetimi adlı mikro hizmet modelindeki Kullanıcı varlığı, kişisel veri özniteliklerinin çoğuna sahip olabilir. Ancak, mikro hizmet ödemedeki veya mikro hizmet müşteri hizmetindeki müşteri şeklinin içindeki aynı kullanıcı aynı öznitelik listesine ihtiyaç duymayabilir.

Şekil 4-11 ' de benzer bir yaklaşım gösterilmektedir.

![Sınırlanmış bağlamlar arasında geleneksel bir veri modeli oluştururken, her sınırlanmış bağlamda farklı özniteliklere sahip aynı kimliği (alıcı da bir Kullanıcı) paylaşan farklı varlıklara sahip olabilirsiniz.](./media/image11.png)

**Şekil 4-11**. Geleneksel veri modellerini birden çok etki alanı modeline ayırmayı kaldırma

Kullanıcının, kullanıcı varlığı olarak konferanslar yönetim mikro hizmet modelinde nasıl mevcut olduğunu ve ayrıca, aslında bir alıcı olduğunda kullanıcı hakkındaki alternatif özniteliklerle veya ayrıntılarla birlikte fiyatlandırma mikro hizmetindeki alıcı varlık biçiminde de mevcut olduğunu görebilirsiniz. Her mikro hizmet veya BC, bir Kullanıcı varlığıyla ilgili tüm verilerin, çözülme veya bağlam sorununa bağlı olarak yalnızca bir parçası olmasına gerek duymayabilir. Örneğin, fiyatlandırma mikro hizmet modelinde, alıcı başına lisans fiyatlarına göre fiyatlandırılması sırasında indirimlerin bir etkisi olacak şekilde, yalnızca KIMLIK (kimlik olarak) ve durum ' a gerek kalmaz.

Bilgisayar varlığı, her etki alanı modelinde aynı ada ancak farklı özniteliklere sahiptir. Ancak, Kullanıcı ve alıcı ile aynı KIMLIĞE göre, bilgisayar tarafından kimlik paylaşımı yapılır.

Temel olarak, birden çok hizmet (etki alanı) içinde bulunan ve bu kullanıcının kimliğini paylaştığı bir kullanıcının paylaşılan bir kavramı vardır. Ancak, her bir etki alanı modelinde, Kullanıcı varlığıyla ilgili ek veya farklı ayrıntılar olabilir. Bu nedenle, bir Kullanıcı varlığını bir etki alanı (mikro hizmet) ile diğerine eşlemenin bir yolu olması gerekir.

Aynı kullanıcı varlığının, etki alanları genelinde aynı sayıda özniteliğe paylaştırmamasının çeşitli avantajları vardır. Bir avantaj, mikro hizmet modellerinin gerek duymayan verileri olmaması için yinelemeyi azaltmaktır. Başka bir avantaj, varlık başına belirli bir veri türüne sahip olan bir ana mikro hizmete sahiptir; böylece bu tür veriler için güncelleştirmeler ve sorgular yalnızca bu mikro hizmet tarafından çalıştırılır.

>[!div class="step-by-step"]
>[Önceki](distributed-data-management.md)İleri
>[](direct-client-to-microservice-communication-versus-the-api-gateway-pattern.md)
