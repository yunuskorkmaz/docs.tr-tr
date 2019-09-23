---
title: Bulutta yerel veri desenleri
description: Azure için Cloud Native .NET uygulamaları tasarlama | Bulutta yerel veri desenleri
ms.date: 06/30/2019
ms.openlocfilehash: 8fc5a09dca61e6644fdcaa692ff1a21f40ebf179
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2019
ms.locfileid: "71183415"
---
# <a name="cloud-native-data-patterns"></a>Bulutta yerel veri desenleri

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Veri merkezi olmayan veriler, geliştirilmiş performans, ölçeklenebilirlik ve maliyet tasarruflarına yol açacağından, birçok zorluk da sunar. Mikro hizmetler genelinde veri sorgulama karmaşıktır. Mikro hizmetleri kapsayan bir işlem, dağıtılmış işlemler bulutta yerel uygulamalarda desteklenmediğinden programlı bir şekilde yönetilmelidir. *Anında tutarlılık* dünyasının *nihai tutarlılığa*geçiş yapabilirsiniz.

Bu güçlükleri şimdi tartıştık.

## <a name="cross-service-queries"></a>Çapraz hizmet sorguları

Bir uygulama çok sayıda bağımsız mikro hizmete yayılan verileri nasıl sorgular?

Şekil 5-4, bu senaryoyu gösterir.

![Mikro hizmetler genelinde sorgulama](./media/cross-service-query.png)

**Şekil 5-4**. Mikro hizmetler genelinde sorgulama

Önceki şekilde bir kullanıcının alışveriş sepetine bir öğe ekleyen bir alışveriş sepeti mikro hizmeti görtiğimiz hakkında bilgi alın. Alışveriş sepetinin veri deposu bir sepet ve LineItem tablosu içerdiğinde, bu öğeler üründe ve fiyat mikro hizmetlerinde bulunduğundan ürün veya fiyatlandırma verilerini içermez. Bir öğe eklemek için, alışveriş sepeti mikro hizmeti ürün verilerine ve fiyatlandırma verilerine ihtiyaç duyuyor. Ürün ve fiyatlandırma verilerini almaya yönelik seçenekler nelerdir?

Şekil 5-5, ürün kataloğu ve fiyatlandırma mikro hizmetleri için doğrudan HTTP çağrısı yapan alışveriş sepeti mikro hizmetini gösterir.

![Doğrudan HTTP iletişimi](./media/direct-http-communication.png)

**Şekil 5-5**. Doğrudan HTTP iletişimi

Uygulama için uygun olsa da, Bölüm 4 ' te, mikro hizmetler genelinde doğrudan HTTP çağrılarının sistem tarafından ne kadar iyi bir uygulama olarak düşünüldük.

Şekil 5-6 ' de gösterilen bir toplayıcı mikro hizmeti uygulayabiliriz.

![Toplayıcı mikro hizmeti](./media/aggregator-microservice.png)

**Şekil 5-6.** Toplayıcı mikro hizmeti

Bu yaklaşım, tek bir mikro hizmette iş işlemi iş akışını kapsüller, ancak doğrudan HTTP çağrılarına neden olan karmaşıklığa sahiptir.

Çapraz hizmet sorgularını yürütmeye yönelik yaygın bir yaklaşım, Şekil 5-7 ' de gösterilen [gerçekleştirilmiş görünüm düzenlerini](https://docs.microsoft.com/azure/architecture/patterns/materialized-view)kullanır.

![Gerçekleştirilmiş görünüm deseninin](./media/materialized-view-pattern.png)

**Figure5-7**. Gerçekleştirilmiş görünüm deseninin

Bu düzende, ürün ve fiyatlandırma mikro hizmetleri için gereken verilerin yoğun bir kopyasını içeren alışveriş sepeti hizmetine doğrudan bir yerel tablo ( *okuma modeli*olarak bilinir) yerleştirebilirsiniz. Bu verilerin alışveriş sepeti mikro hizmeti içine yerleştirilmesi, pahalı çapraz hizmet çağrılarını çağırma gereksinimini ortadan kaldırır. Hizmetin yerel verileri ile yanıt süresini ve güvenilirliği geliştirebilirsiniz.

Bu yaklaşım ile catch, artık sisteminizde Yinelenen veriler var. Bulutta yerel sistemlerde Yinelenen veriler bir [kenar yumuşatma](https://en.wikipedia.org/wiki/Anti-pattern) kabul edilmez ve genellikle bulutta yerel sistemlerde uygulanır. Ancak, bir ve yalnızca bir sistem herhangi bir veri kümesinin sahibi olabilir ve temel alınan verilerde yapılan her değişiklik gerçekleştiğinde ilişkili tüm okuma modellerini güncelleştirmek için kayıt sistemine yönelik bir eşitleme mekanizması uygulamanız gerekir.

## <a name="transactional-support"></a>İşlem desteği

Mikro hizmetler genelinde sorgular zorlayıcı olsa da, mikro hizmetler genelinde bir işlem uygulamak karmaşık olabilir. Farklı mikro hizmetlerde bulunan veri kaynakları arasında veri tutarlılığı sağlamanın devralınmış bir şekilde belirtilmedi. Şekil 5-8 sorunu gösterir.

![Saga düzeninde işlem](./media/saga-transaction-operation.png)

**Şekil 5-8**. Mikro hizmetler genelinde işlem uygulama

Önceki şekilde beş bağımsız mikro hizmetin her türlü dağıtılmış bir *Sipariş oluşturma* işlemine nasıl katıldığına göz önünde. Ancak, her bir beş tek mikro hizmetin işlemi başarılı olmalıdır veya tümü iptal ve işlemi geri alma olmalıdır. Mikro hizmetlerin her birinde yerleşik işlem desteği kullanılabilir olsa da, beş hizmetin tümünde dağıtılmış işlem desteklenmez.

Bu işlem için işlem desteği, verileri mikro hizmetlerde her birinde tutarlı tutmak için gerekli olduğundan, programlı bir şekilde dağıtılmış işlem oluşturmanız gerekir.

İşlem desteğini programlı olarak eklemeye yönelik popüler bir model, [Saga örüntü](https://blog.couchbase.com/saga-pattern-implement-business-transactions-using-microservices-part/). Yerel işlemler birlikte gruplanarak ve her biri sırayla çağırılırken uygulanır. Yerel bir işlem başarısız olursa, Saga işlemi iptal eder ve önceki yerel işlemler tarafından yapılan değişiklikleri geri almak için bir [dengeleyici](https://docs.microsoft.com/azure/architecture/patterns/compensating-transaction) işlem kümesi çağırır. Şekil 5-9, Saga düzeniyle başarısız olan bir işlemi gösterir.

![Saga düzeninde geri alma](./media/saga-rollback-operation.png)

**Şekil 5-9**. Bir işlem geri alınıyor

Önceki şekilde, müzik mikro hizmetinde *Generatecontent* işleminin başarısız olduğunu aklınızda edin. Saga, içeriği kaldırmak için telafi işlemlerini (kırmızı renkte) çağırır, ödemeyi iptal eder ve her bir mikro hizmet için verileri tutarlı bir duruma geri döndürerek sırayı iptal eder.

Saga desenleri genellikle bir dizi ilgili olay olarak ayarlanabilir veya ilgili komutlar kümesi olarak düzenlenir.

## <a name="cqrs-pattern"></a>CQRS stili

CQRS veya [komut ve sorgu sorumluluklarının ayrılığı](https://docs.microsoft.com/azure/architecture/patterns/cqrs), verileri yazanlardan verileri okuyan işlemleri ayıran mimari bir modeldir. Bu model performans, ölçeklenebilirlik ve güvenliğin en üst düzeye çıkmasına yardımcı olabilir.

Normal veri erişimi senaryolarında, hem okuma hem *de* yazma veri işlemlerini gerçekleştiren tek bir model (varlık ve depo nesnesi) uygulacağınızı görürsünüz.

Ancak, daha gelişmiş bir veri erişim senaryosu, okuma ve yazma işlemleri için ayrı modellerden ve veri tablolarından faydalanabilir. Performansı artırmak için, *sorgu*olarak bilinen okuma işlemi, pahalı yinelenen tablo birleştirmelerini önlemek için verilerin yüksek oranda büyük bir gösterimine karşı sorgu gerektirebilir. *Komut*olarak bilinen *yazma* işlemi, verilerin tamamen normalleştirilmiş bir gösterimine karşı güncelleştirebilir. Ardından her iki gösterimi de eşitlenmiş halde tutmak için bir mekanizma uygulamanız gerekir. Genellikle, yazma tablosu her değiştirildiğinde, veri değişikliğini okuma tablosuna çoğaltan bir olay oluşturur.

Şekil 5-10, CQRS deseninin bir uygulamasını gösterir.

![CQRS uygulama](./media/cqrs-implementation.png)

**Şekil 5-10**. CQRS uygulama

Önceki şekilde ayrı komut ve sorgu modellerinin nasıl uygulandığını aklınızda edin. Üstelik, her veri yazma işlemi yazma deposuna kaydedilir ve sonra okuma deposuna yayılır. Yayma işleminin [nihai tutarlılık](https://www.cloudcomputingpatterns.org/eventual_consistency/)ilkesi üzerinde nasıl çalıştığı hakkında daha fazla dikkat edin, ancak okuma modeli yazma modeliyle eşitlenir, ancak işlemde bazı gecikme olabilir.

Ayrımı uygulayarak, okuma ve yazma işlemlerini ayrı olarak ölçeklendirmenize olanak tanır. Ayrıca, yazma işlemlerinde okuma işlemleriyle daha sıkı güvenlik sağlayabilirsiniz.

Genellikle, CQRS desenleri belirli gereksinimlere göre sisteminizin sınırlı bölümlerine uygulanır.

## <a name="relational-vs-nosql"></a>İlişkisel vs NoSQL

[NoSQL](https://www.geeksforgeeks.org/introduction-to-nosql/) teknolojilerinin etkisi, özellikle dağıtılmış bulut Yerel sistemleri için geçersiz şekilde belirtilemez. Bu alandaki yeni veri teknolojilerinin bir şekilde, ilişkisel veritabanlarına özel olarak bir şekilde güvenilme çözümleri bozulur.

Bir tarafta ilişkisel veritabanları, Decades 'in yaygın bir teknolojisinden biridir. Bunlar, Yetişkin, kanıtlanmış ve yaygın olarak uygulanan bir uygulamalılar. Rekabet veritabanı ürünleri, uzmanlığı ve araç abounds. İlişkisel veritabanları ilgili veri tablolarının bir deposunu sağlar. Bu tablolar sabit bir şemaya sahiptir, verileri yönetmek için SQL (Yapılandırılmış Sorgu Dili) kullanın ve [ACID](https://www.geeksforgeeks.org/acid-properties-in-dbms/) (Atomicity, tutarlılık, yalıtım ve dayanıklılık olarak da bilinir) garantisi vardır.

SQL veritabanları yok, diğer tarafta, yüksek performanslı, ilişkisel olmayan veri depolarına bakın. Bu kişiler, kullanım kolaylığı, ölçeklenebilirlik, esnekliği ve kullanılabilirlik özellikleriyle Excel. NoSQL, normalleştirilmiş verilerin tablolarını birleştirmek yerine, genellikle JSON belgelerinde kendi kendini açıklayan (schemaless) verileri depolar. Bunlar, [ACID](https://www.geeksforgeeks.org/acid-properties-in-dbms/) garantisi sunmaz.

Bu tür veritabanları arasındaki farklılıkları anlamanın bir yolu, durumu depolayan dağıtılmış sistemlere uygulanabilen bir ilke kümesi olan üst [sınır](https://towardsdatascience.com/cap-theorem-and-distributed-database-management-systems-5c2be977950e)içinde bulunabilir. Şekil 5-11, CAP 'in üç özelliğini gösterir.

![CAP 'ler](./media/cap-theorem.png)

**Şekil 5-11**. Üst sınır

Bu, herhangi bir dağıtılmış veri sisteminin tutarlılık, kullanılabilirlik ve bölüm toleransı arasında bir denge sunabileceğini ve herhangi bir veritabanının yalnızca iki özelliği garanti edebileceğini belirtir:

- *Tutarlılık*: kümedeki her düğüm, tüm çoğaltmalar doğru şekilde güncelleştirilene kadar bir isteğin engellenmesini gerektirse bile en son verilerle yanıt verir.

- *Kullanılabilirlik*: her düğüm, bu yanıt en son veriler olmasa bile makul bir süre içinde yanıt döndürür.

- *Bölüm toleransı*: bir düğüm başarısız olursa veya başka bir bağlantı kesilirse sistemin çalışmaya devam etmesini güvence altına alır.

İlişkisel veritabanları tutarlılık ve kullanılabilirlik sergiler, ancak bölüm toleransı sağlamaz. Parçalara ayırma gibi ilişkisel bir veritabanının bölümlenmesi zordur ve performansı etkileyebilir.

Öte yandan, NoSQL veritabanları genellikle yatay ölçeklenebilirlik ve yüksek kullanılabilirlik olarak bilinen bölüm dayanıklılığı sergiler. CAP 'ler tarafından belirtildiği gibi, üç ilkeden yalnızca iki ilke olabilir ve tutarlılık özelliğini kaybedersiniz.

NoSQL veritabanları dağıtılır ve genellikle emtia sunucularında ölçeklendirilir. Bunun yapılması, hem coğrafi bölgeler içinde hem de daha düşük bir maliyetle büyük kullanılabilirlik sağlayabilir. Veriler, bu makinelerde veya düğümlerde bölümlenebilir ve çoğaltılarak yedeklenebilir ve hataya dayanıklılık sağlar. Downsıde, tutardır. Bir NoSQL düğümündeki verilerde yapılan değişikliğin, diğer düğümlere yayılması biraz zaman alabilir. Genellikle, bir NoSQL veritabanı düğümü, sunum yaptığı veriler eski ve henüz güncelleştirilmemiş olsa bile bir sorguya anında yanıt verir.

Bu, ACID işlemlerinin desteklenmediği dağıtılmış veri sistemlerinin bir özelliği olan, [nihai tutarlılık](https://www.cloudcomputingpatterns.org/eventual_consistency/)bilinmektedir. Bu, bir veri öğesi güncelleştirmesi ve bu güncelleştirmenin her bir çoğaltma düğümüne yayılması için geçen süre arasında kısa bir gecikmeden oluşur. Birleşik Devletler bir NoSQL veritabanında bir ürün öğesini güncelleştirirseniz, ancak aynı zamanda Avrupa 'daki bir çoğaltma düğümünden aynı veri öğesini sorgulayıp, Avrupa düğümü ürün değişikliği ile güncellenene kadar önceki ürün bilgilerini alabilirsiniz. Bu denge, güçlü tutarlılık vererek, bir sorgu sonucu döndürmeden önce tüm çoğaltma düğümlerinin güncelleştirilmesini beklerken, büyük ölçekli ölçek ve trafik hacminin yanı sıra eski verileri sunma [olasılığından](https://en.wikipedia.org/wiki/Strong_consistency)de daha fazla bir şekilde destek alabilirsiniz.

NoSQL veritabanları aşağıdaki dört modele göre kategorize edilebilir: 

- *Belge Mağazası* (MongoDB, Couşdb, Couşbase): veriler (ve buna karşılık gelen meta veriler), veritabanının içindeki Normalleştirilmemiş JSON tabanlı belgelerde ilişki dışı olarak depolanır.

- *Anahtar/değer deposu* (Redin, Riak, memönbelleğe alınmış): veriler, Kullanıcı verilerinin bir değeriyle eşlenen benzersiz bir erişim anahtarına karşı gerçekleştirilen sistem işlemleri ile basit anahtar-değer çiftlerine depolanır.

- *Geniş sütunlu depo* (HBase, Cassandra): ilgili veriler, genellikle birden çok tabloya birlikte katılması gerekmeden tek bir sütun içinde iç içe geçmiş anahtar/değer çiftleri kümesi olarak bir sütunlu biçimde depolanır.

- *Grafik depoları* (NEO4J, Titan): veriler, düğümler arasındaki ilişkiyi belirten kenarlarla birlikte bir düğüm içinde bir grafik gösterimi olarak depolanır.

NoSQL veritabanları, özellikle de veriler görece basit olduğunda büyük ölçekli verilerle uğraşmak için iyileştirilebilir. Şu durumlarda bir NoSQL veritabanı göz önünde bulundurun:

- İş yükünüz büyük ölçekli ve yüksek eşzamanlılık gerektirir.
- Çok sayıda kullanıcınız var.
- Verileriniz yalnızca ilişkiler olmadan ifade edilebilir.
- Verilerinizi coğrafi olarak dağıtmanız gerekir.
- ACID garantisi gerekmez.
- , Emtia donanımına dağıtılır.

Ardından, şu durumlarda ilişkisel bir veritabanı düşünün:

- İş yükleriniz orta ila büyük ölçekli bir ölçek gerektirir.
- Eşzamanlılık önemli bir sorun değil.
- ACID garantisi gereklidir.
- Veriler en iyi şekilde ifade edilir.
- Uygulamanız büyük ve yüksek kaliteli donanıma dağıtılacak.

Daha sonra, Azure bulutu 'nda veri depolamaya bakacağız.

>[!div class="step-by-step"]
>[Önceki](distributed-data.md)
>[İleri](azure-data-storage.md)
