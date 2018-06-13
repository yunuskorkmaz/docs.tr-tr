---
title: Sorunları ve çözümleri Dağıtılmış veri yönetimi
description: Kapsayıcılı .NET uygulamaları için .NET mikro mimarisi | Sorunları ve çözümleri Dağıtılmış veri yönetimi
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.openlocfilehash: 7d173133ab7c803c7ab48b39c50b02ee4f3b1721
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33578943"
---
# <a name="challenges-and-solutions-for-distributed-data-management"></a>Sorunları ve çözümleri Dağıtılmış veri yönetimi

## <a name="challenge-1-how-to-define-the-boundaries-of-each-microservice"></a>Sınama \#1: her mikro hizmet sınırları tanımlama

Mikro hizmet sınırları tanımlama herkes karşılaştığında ilk testten olabilir. Her mikro hizmet uygulamanızı bir parçası olması gerekir ve her mikro hizmet tüm avantajları ve onu ilettiği güçlükleri ile otonom olması gerekir. Ancak bu sınırlar nasıl tanımlarsınız?

İlk olarak, uygulamanın mantıksal etki alanı modelleri ve ilgili verileri odaklanmak gerekir. Veri ve aynı uygulama içinde farklı bağlamdan ayrılmış Adaları tanımlamak denemeniz gerekir. Her bağlam farklı iş dili (farklı iş koşullarını) olabilir. Bağlamları tanımlanabilir ve bağımsız olarak yönetilebilir. Hüküm ve bu farklı bağlamlarda kullanılan varlıkların benzer görünebilir, ancak belirli bir bağlamda başka bir bağlamda farklı bir amaç için bir iş kavramını kullanıldığını keşfetmenize ve hatta farklı bir ad olabilir. Örneğin, bir kullanıcı kullanıcı kimliği veya üyelik bağlamı olarak Müşteri bir CRM içeriği olarak bir sıralama bağlamında bir alıcı olarak adlandırılabilir ve benzeri.

Her bağlam tam olarak her iş mikro hizmet ve onun ilişkili sınırları nasıl tanımlamak için farklı bir etki alanı ile birden çok uygulama bağlamları arasındaki sınırları tanımlamak şekilde etki alanı modeli ve veri. Her zaman bu mikro arasında bağ en aza indirmek çalışır. Bu kılavuzun bu bölümünde tanımlama ve etki alanı modeli tasarım hakkında daha fazla ayrıntı girmeyeceğini [her mikro hizmet için etki alanı modeli sınırları tanımlayan](#identifying-domain-model-boundaries-for-each-microservice) daha sonra.

## <a name="challenge-2-how-to-create-queries-that-retrieve-data-from-several-microservices"></a>Sınama \#2: birkaç mikro verileri sorgu oluşturma

Uzak istemci uygulamalardan mikro chatty iletişimi kaçınarak birkaç mikro verileri sorgular gerçekleştirme buna ikinci bir sorundur. Bir örnek Sepeti, katalog ve kullanıcı kimliği mikro ait kullanıcı bilgilerini göstermek için gereken bir mobil uygulaması tek ekranından olabilir. Başka bir örnek içinde birden çok mikro bulunan çok sayıda tabloları içeren karmaşık bir rapor olabilir. Doğru çözüm sorguların karmaşıklığına bağlıdır. Ancak herhangi bir durumda, sisteminizin iletişimin verimliliğini artırmak istiyorsanız toplama bilgileri için bir yol gerekir. En popüler çözümleri aşağıda verilmiştir.

**API ağ geçidi**. Farklı veritabanlarına ait birden çok mikro öğesinden basit veri toplama için önerilen bir API ağ geçidi olarak başvurulan bir toplama mikro hizmet yaklaşımdır. Ancak, sisteminizdeki bir sıkıştırma noktası olabilir ve mikro hizmet otonomisi ilkesini ihlal edebilir çünkü bu deseni uygulama hakkında dikkatli olmanız gerekir. Bu olasılığını azaltmak için her bir dikey "dilim" ya da sistem iş alanı odaklanan birden çok fined düzey API ağ geçidi sahip olabilir. API ağ geçidi desen kullanma bölümünde daha ayrıntılı açıklanmıştır daha sonra bir API ağ geçidi.

**Sorgu/okuma tablolarla CQRS**. Birden çok mikro verileri toplama için başka bir çözüm [gerçekleştirilip görünüm düzeni](https://docs.microsoft.com/azure/architecture/patterns/materialized-view). Bu yaklaşımda, önceden oluşturduğunuz (hazırlamanız Normalleştirilmemiş veri gerçek sorguları durum önce) tarafından birden çok mikro ait verilerle salt okunur bir tablo. Tablo istemci uygulamasının gereksinimlerine göre uygun bir biçime sahip.

Bir mobil uygulama için ekrana benzer şekilde göz önünde bulundurun. Tek bir veritabanınız varsa, birden çok tablo içeren bir karmaşık birleştirme gerçekleştiren bir SQL sorgusu kullanılarak bu ekranda verileri birlikte çekme. Ancak, birden çok veritabanı varsa ve her veritabanı farklı bir mikro hizmet tarafından ait olduğunda, bu veritabanları sorgu ve SQL birleştirme oluşturma olamaz. Bir challenge, karmaşık bir sorgu olur. CQRS yaklaşım kullanarak gereksinimi karşılamak — yalnızca sorgularında kullanılır farklı bir veritabanına Normalleştirilmemiş bir tablo oluşturun. Tablo özellikle uygulamanızın ekran ve sorgu tablodaki sütunlar için gerekli alanlar arasında bire bir ilişki ile karmaşık bir sorgu için gereksinim duyduğunuz verileri için tasarlanmış olabilir. Ayrıca raporlama amacıyla hizmet.

Bu yaklaşım yalnızca (nasıl sorgu ve mikro hizmetler arasında birleştirme); özgün sorununu çözer uygulamanın sorgu tabloda gerekir veri zaten yüklü olduğu da oldukça karmaşık bir birleşim ile karşılaştırıldığında performansı artırır. Elbette, sorgu/okuma tablolarla komutunu ve sorgu sorumluluk ayrımı (CQRS) kullanarak ek geliştirme iş anlamına gelir ve nihai tutarlılık kapsayacak şekilde gerekir. Öte yandan, performans ve yüksek ölçeklenebilirlik gereksinimlerini [işbirliği senaryoları](http://udidahan.com/2011/10/02/why-you-should-be-using-cqrs-almost-everywhere/) (veya bağlı olarak bakış açısından rekabetçi senaryoları) burada birden çok veritabanlarıyla CQRS uygulamalıdır olduğu.

**Merkezi veritabanlarındaki "soğuk veriler"**. Karmaşık raporlar ve gerçek zamanlı veri gerektirmeyebilecek sorgular için ortak bir yaklaşım, "veri hot" verilmesidir (mikro işlem verilerden) yalnızca raporlama için kullanılan büyük veritabanlarına "soğuk veriler" olarak. Bu merkezi veritabanı sistem Hadoop, bir Azure SQL Data Warehouse veya (boyutu bir sorun olursa) yalnızca raporları için kullanılan bile tek bir SQL veritabanı göre gibi bir veri ambarı gibi büyük veri tabanlı bir sistem olabilir.

Bu merkezi veritabanı yalnızca sorgular ve gerçek zamanlı veri gerekmez raporları için kullanılacak aklınızda bulundurun. Özgün güncelleştirmeleri ve gerçekte, kaynağınız işlemleri mikro verilerinizi olması gerekir. Veri eşitleme şekilde olay denetimli iletişimi (sonraki bölümlerde ele) kullanarak veya diğer veritabanı altyapısı içeri/dışarı aktarma araçları kullanarak olacaktır. Olay kaynaklı iletişimi kullanırsanız, tümleştirme işlem CQRS sorgu tablolar için daha önce açıklandığı gibi veri yayılması şekilde benzer olacaktır.

Ancak, Uygulama tasarımınız sürekli karmaşık sorgular için birden çok mikro bilgileri toplama içeriyorsa, hatalı bir tasarım belirtisi olabilir — bir mikro hizmet diğer mikro gelen mümkün olduğunca yalıtılmış olması gerekir. (Soğuk veri merkezi veritabanlarını daima raporları/analytics dışlar.) Bu sorun genellikle mikro birleştirmek için bir neden olabilir. Evrimi otonomisi ve güçlü bağımlılıkları, cohesion ve veri toplama her mikro hizmet dağıtımını dengelemeniz gerekir.

## <a name="challenge-3-how-to-achieve-consistency-across-multiple-microservices"></a>Sınama \#3: birden çok mikro arasında tutarlılık sağlamak nasıl

Daha önce belirtildiği gibi her mikro hizmet tarafından ait veriler bu mikro hizmet özel ve yalnızca kendi mikro hizmet API kullanılarak erişilebilir. Bu nedenle, sunulan bir uçtan uca iş süreçlerini arasında birden çok mikro tutarlılık tutarken uygulamak nasıl iştir.

Bu sorunu çözümlemek için bir örnek bakalım [eShopOnContainers başvuru uygulama](http://aka.ms/eshoponcontainers). Katalog mikro hizmet stok düzeylerini dahil olmak üzere tüm ürünlerle ilgili bilgileri tutar. Sıralama mikro hizmet siparişleri yönetir ve yeni bir sipariş kullanılabilir Kataloğu ürün stok aşmayan doğrulamanız gerekir. (Veya senaryo backordered ürünleri işleme mantığı gerektirebilir.) Bir kuramsal tek yapılı sürümünde bu uygulama, sipariş alt sistemi yalnızca ACID işlemi kullanılabilir hisse senedi denetleyin, Siparişler tablosunda sırasını oluşturmak ve Ürünler tablosuna kullanılabilir stokta güncelleştirmek için kullanabilirsiniz.

Ancak, bir mikro tabanlı uygulamada kendi ilgili mikro tarafından sırası ve ürün tabloları sahibi olur. Şekil 4-9'da gösterildiği gibi hiçbir mikro hizmet kendi işlemleri ya da sorgular, başka bir mikro sahibi veritabanları her zamankinden içermelidir.

![](./media/image9.PNG)

**Şekil 4-9**. Bir mikro hizmet başka bir mikro hizmet tablosunda doğrudan erişemiyor

Katalog mikro hizmet tarafından Ürünler tablosuna ait olduğundan sıralama mikro hizmet Ürünler tablosuna doğrudan güncelleştirmelidir değil. Katalog mikro hizmet için bir güncelleştirme yapmak için sıralama mikro hizmet yalnızca sürekli tümleştirme olaylarını (ileti ve olay tabanlı iletişim) gibi zaman uyumsuz iletişim kullanmanız gerekir. Bunun nasıl [eShopOnContainers](http://aka.ms/eshoponcontainers) başvuru uygulaması bu tür bir güncelleştirme gerçekleştirir.

Tarafından belirtildiği gibi [CAP Teoremi](https://en.wikipedia.org/wiki/CAP_theorem), ACID güçlü tutarlılık ve kullanılabilirlik arasında seçim yapmanız gerekir. Mikro hizmet tabanlı çoğu senaryoda, kullanılabilirlik ve güçlü tutarlılık aksine yüksek ölçeklenebilirlik talep. Görev açısından kritik uygulamalar yukarı kalması ve çalıştığından ve geliştiricilerin güçlü tutarlılık zayıf veya nihai tutarlılık ile çalışmak için teknikleri kullanarak çalışabilir. Mikro hizmet tabanlı çoğu mimariler tarafından uygulanan yaklaşıma budur.

Ayrıca, ACID stili veya iki aşamalı kaydetme işlemleri yalnızca mikro ilkelerine karşı değildir; Çoğu NoSQL veritabanı (örneğin, Azure Cosmos DB, MongoDB, vb.) iki aşamalı kaydetme işlemleri desteklemez. Ancak, veri koruma hizmetleri ve veritabanları arasında tutarlılık gereklidir. Bu sorunu bazı verileri yedek olması gerektiğinde arasında birden çok mikro değişiklikleri yaymak nasıl soru için de ilgili — Örneğin, ne zaman ürünün ad veya açıklama katalog mikro hizmet ve sepeti olması gerekir mikro hizmet.

Bu sorun için iyi bir çözüm olay denetimli iletişim ve bir Yayımla ve abone ol sistemi geliştirilmiştir mikro arasında nihai tutarlılık kullanmaktır. Bu konular bölümünde ele alınmıştır [olay tabanlı zaman uyumsuz iletişim](#async_event_driven_communication) bu kılavuzda daha sonra.

## <a name="challenge-4-how-to-design-communication-across-microservice-boundaries"></a>Sınama \#4: mikro hizmet sınırları boyunca iletişimi tasarlamak nasıl

Mikro hizmet arasında iletişim sınırları olan gerçek bir sınama. Bu bağlamda iletişimi başvurmuyor hangi Protokolü (HTTP ve REST, AMQP, Mesajlaşma vb.) kullanmalısınız. Bunun yerine, kullanmanız gereken hangi iletişim stili ve özellikle bu nasıl bağlı, mikro olmalıdır yöneliktir. Hata oluştuğunda, ilişki düzeyine bağlı olarak, bu hata, sistem üzerindeki etkisini önemli ölçüde farklılık gösterir.

Mikro tabanlı bir uygulama, çok sayıda yapıları hareket etmek ve birçok sunucuları veya ana bilgisayar üzerinde dağıtılmış hizmetlerle gibi dağıtılmış sistemindeki bileşenleri sonunda başarısız olur. Bunlar dikkate riskleri Dağıtılmış Sistem bu tür ortak alarak üzerinde mikro ve iletişimi tasarlamanız gerekir böylece kısmi hatası ve daha da büyük kesintiler oluşacaktır.

Popüler bir yaklaşım HTTP (REST) uygulamaktır-kendi kolaylık olması nedeniyle mikro tabanlı. HTTP tabanlı bir yaklaşım edilebilir; sorunu burada kullandığınız nasıl ilişkilidir. Yalnızca, mikro istemci uygulamaları veya API ağ geçidi ile etkileşim kurmak için HTTP isteklerinin ve yanıtlarının kullanırsanız, sorun yoktur. Ancak mikro arasında zaman uyumlu HTTP çağrıları uzun zincirleri oluşturursanız, mikro tek yapılı bir uygulamadaki nesneler değilmiş gibi kendi sınırlarında iletişim uygulamanızı sonunda sorunlarla çalışır.

Örneğin, istemci uygulamanız sıralama mikro hizmet gibi tek bir mikro hizmet için bir HTTP API çağrısını yapar düşünün. Sıralama mikro hizmet sırayla ek çağırırsa içinde aynı istek/yanıt HTTP kullanarak mikro döngüsü, HTTP çağrıları zinciri oluşturma. Başlangıçta makul görünebilir. Ancak, bu yol geçerken dikkate alınması gereken önemli noktalar vardır:

-   Engelleme ve düşük performans. HTTP zaman uyumlu yapısı nedeniyle, iç HTTP çağrıları tamamlanana kadar özgün istek yanıt almazsınız. Bu çağrılarının sayısını önemli ölçüde artırır ve Ara HTTP birini çağırır mikro hizmet için aynı anda engellenmiş düşünün. Performansı etkilenir ve genel ölçeklenebilirlik katlanarak ek HTTP isteklerini artış etkileneceğini sonucudur.

-   Bağ mikro HTTP ile. İş mikro ile diğer iş mikro eşleştirilmek değil. İdeal olarak, bunlar "diğer mikro varlığı hakkında bilmeniz gereken değil". Uygulamanızı örnekte olduğu gibi mikro Kuplaj dayalıysa, mikro hizmet başına otonomisi elde neredeyse imkansız olur.

-   Herhangi bir mikro hizmet hatası. HTTP çağrıları tarafından mikro hiçbirini başarısız (ve sonunda yapamaz seçtiğinizde) ve tüm zincir mikro, bağlantılı mikro zinciri uygulanırsa, başarısız olur. Mikro hizmet tabanlı bir sistemin yanı sıra olası kısmi hataları sırasında çalışmaya devam etmek için tasarlanmalıdır. Yeniden deneme üstel geri alma veya devre kesici mekanizmaları kullanan istemci mantığı uygulamanız olsa bile, daha fazla karmaşık HTTP çağrısı zincirleri olan HTTP tabanlı bir hata stratejisi uyguladıktan olan daha karmaşık.

İç mikro açıklandığı gibi HTTP isteklerinin zincirleri oluşturarak kurarken, aslında bu bir intraprocess iletişim mekanizmasını yerine işlemleri arasındaki HTTP tabanlı ancak tek yapılı bir uygulamaya sahip tartışılabilir.

Bu nedenle, mikro hizmet otonomisi zorlamak ve daha iyi esneklik olması için istek/yanıt iletişimin zincirleri kullanımını mikro arasında en aza indirmeniz gerekir. Zaman uyumsuz ileti ve olay tabanlı iletişim veya HTTP yoklama özgün HTTP istek/yanıt döngüsü bağımsız olarak kullanan ağlar arası mikro hizmet iletişimi için yalnızca zaman uyumsuz etkileşim kullandığınızdan emin önerilir.

Zaman uyumsuz iletişim kullanımını bölümlerde bu kılavuzda daha sonra ek ayrıntılarıyla açıklandığı [zaman uyumsuz mikro hizmet tümleştirme zorlar mikro'nın otonomisi](#asynchronous-microservice-integration-enforce-microservices-autonomy) ve [zaman uyumsuz ileti tabanlı iletişim](#asynchronous-message-based-communication).

## <a name="additional-resources"></a>Ek kaynaklar

-   **CAP Teoremi**
    [*https://en.wikipedia.org/wiki/CAP\_Teoremi*](https://en.wikipedia.org/wiki/CAP_theorem)

-   **Nihai tutarlılık**
    [*https://en.wikipedia.org/wiki/Eventual\_tutarlılık*](https://en.wikipedia.org/wiki/Eventual_consistency)

-   **Veri tutarlılığı Primer**
    [*https://msdn.microsoft.com/library/dn589800.aspx*](https://msdn.microsoft.com/library/dn589800.aspx)

-   **Martin Fowler. CQRS (komut ve sorgu sorumluluk ayrımı)**
    [*https://martinfowler.com/bliki/CQRS.html*](https://martinfowler.com/bliki/CQRS.html)

-   **Gerçekleştirilmiş Görünüm**
    [*https://docs.microsoft.com/azure/architecture/patterns/materialized-view*](https://docs.microsoft.com/azure/architecture/patterns/materialized-view)

-   **Charles satır. ACID vs. TABAN: Veritabanı işlem işleme Shifting pH**
    [*http://www.dataversity.net/acid-vs-base-the-shifting-ph-of-database-transaction-processing/*](http://www.dataversity.net/acid-vs-base-the-shifting-ph-of-database-transaction-processing/)

-   **İşlem karşılayan**
    [*https://docs.microsoft.com/azure/architecture/patterns/compensating-transaction*](https://docs.microsoft.com/azure/architecture/patterns/compensating-transaction)

-   **UDI Dahan. Birleşim hizmet odaklı**
    [*http://udidahan.com/2014/07/30/service-oriented-composition-with-video/*](http://udidahan.com/2014/07/30/service-oriented-composition-with-video/)


>[!div class="step-by-step"]
[Önceki] (mantıksal-karşı-fiziksel-architecture.md) [sonraki] (tanımlamak-mikro hizmet-etki-model-boundaries.md)
