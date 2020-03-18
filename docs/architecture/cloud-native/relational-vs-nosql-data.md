---
title: İlişkisel ve NoSQL verileri
description: Bulut ayarı uygulamalarında ilişkisel ve NoSQL verileri hakkında bilgi edinin
author: robvet
ms.date: 01/22/2020
ms.openlocfilehash: 04693e30ba3848f1e51f1c69a75be5f18ead4cf1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79141425"
---
# <a name="relational-vs-nosql-data"></a>İlişkisel ve NoSQL verileri

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

İlişkisel ve NoSQL, bulut ayarı uygulamalarda yaygın olarak uygulanan iki veritabanı sistemi türütür. Farklı olarak oluşturulurlar, verileri farklı şekilde depolarlar ve farklı erişilirler. Bu bölümde, her ikisine de bakacağız. Daha sonra bu bölümde, *newsql*adı verilen gelişmekte olan bir veritabanı teknolojisi bakacağız.

*İlişkisel veritabanları* yıllardır yaygın bir teknoloji olmuştur. Onlar olgun, kanıtlanmış ve yaygın olarak uygulanmaktadır. Rakip veritabanı ürünleri, takım oluşturma ve uzmanlık boldur. İlişkisel veritabanları, ilgili veri tablolarının deposudur. Bu tablolar sabit bir şema var, verileri yönetmek için SQL (Yapılandırılmış Sorgu Dili) kullanın ve ACID garantileri destekler.

*NO-SQL veritabanları* yüksek performanslı, ilişkisel olmayan veri depolarını ifade eder. Kullanım kolaylığı, ölçeklenebilirlik, esneklik ve kullanılabilirlik özelliklerinde mükemmeldirler. NoSQL, normalleştirilmiş veri tablolarına katılmak yerine, genellikle anahtar değer çiftleri veya JSON belgelerinde yapılandırılmamış veya yarı yapılandırılmış verileri depolar. No-SQL veritabanları genellikle tek bir veritabanı bölümü kapsamı dışında ACID garantileri sağlamaz. Alt ikinci yanıt süresi gerektiren yüksek hacimli hizmetler NoSQL veri depolarını tercih eder.

[NoSQL](https://www.geeksforgeeks.org/introduction-to-nosql/) teknolojilerinin dağıtılmış bulut tabanlı sistemler üzerindeki etkisi abartılamaz. Bu alanda yeni veri teknolojilerinin çoğalması, bir zamanlar sadece ilişkisel veritabanlarına dayanan çözümleri sekteye uğratmıştır.

NoSQL veritabanları, her biri belirli kullanım örneklerine uygun verilere erişmek ve bunları yönetmek için birkaç farklı model içerir. Şekil 5-9 dört ortak model sunar.

![NoSQL veri modelleri](./media/types-of-nosql-datastores.png)

**Şekil 5-9**: NoSQL veritabanları için veri modelleri

| Model | Özellikler |
| :-------- | :-------- |
| Belge Deposu | Veriler ve meta veriler veritabanı içinde JSON tabanlı belgelerde hiyerarşik olarak depolanır. |
| Anahtar Değer Deposu | NoSQL veritabanlarının en basiti olan veriler, anahtar değer çiftleri topluluğu olarak temsil edilir. |
| Geniş Sütunlu Mağaza | İlgili veriler, tek bir sütuniçinde iç içe anahtar/değer çiftleri kümesi olarak depolanır. |
| Grafik Deposu | Veriler, düğüm, kenar ve veri özellikleri olarak grafik yapısında depolanır. |

## <a name="the-cap-theorem"></a>CAP teoremi

Bu veritabanları bu tür arasındaki farkları anlamak için bir yol olarak, CAP teoremi, durum depolanan dağıtılmış sistemlere uygulanan bir dizi ilke düşünün. Şekil 5-10 CAP teoreminin üç özelliğini gösterir.

![CAP teoremi](./media/cap-theorem.png)

**Şekil 5-10**. CAP teoremi

Teorem, dağıtılmış veri sistemlerinin tutarlılık, kullanılabilirlik ve bölüm toleransı arasında bir denge sunacağını belirtir. Ve, herhangi bir veritabanı sadece üç özelliklerinden *ikisini* garanti edebilir:

- *Tutarlı -lık.* Tüm yinelemeler güncellenene kadar sistem isteği engellemesi gerekse bile kümedeki her düğüm en son verilerle yanıt verir. Şu anda güncelliğini güncelleştirmekte olan bir öğe için "tutarlı bir sistem" sorgularsanız, tüm yinelemeler başarıyla güncelleştirilene kadar bu yanıtı beklersiniz. Ancak, en güncel verileri alırsınız.

- *Kullanılabilir -lik.* Bu yanıt en son veriler olmasa bile, her düğüm anında yanıt verir. Güncelleyen bir öğe için "kullanılabilir bir sistem" sorgularsanız, hizmetin o anda sağlayabileceği en iyi yanıtı alırsınız.

- *Bölüm Toleransı.* Çoğaltılan bir veri düğümü başarısız olsa veya diğer çoğaltılan veri düğümleriyle bağlantı kaybetse bile sistemin çalışmaya devam etmesini garanti eder.

İlişkisel veritabanları genellikle tutarlılık ve kullanılabilirlik sağlar, ancak bölüm toleransı sağlamaz. Genellikle tek bir sunucuya sağlanır ve makineye daha fazla kaynak ekleyerek dikey olarak ölçeklenirler.

Birçok ilişkisel veritabanı sistemi, birincil veritabanının kopyalarının diğer ikincil sunucu örneklerine yapılabilir ışıkkopyalama özelliklerini destekler. Yazma işlemleri birincil örneğe yapılır ve ikincilerin her birine çoğaltılır. Bir hata üzerine, birincil örnek yüksek kullanılabilirlik sağlamak için ikincil üzerinde başarısız olabilir. İkinciller okuma işlemlerini dağıtmak için de kullanılabilir. Yazma işlemleri her zaman birincil yinelemeye ters giderken, okuma işlemleri sistem yükünü azaltmak için ikinci basamaklardan herhangi biri için yönlendirilebilir.

Veriler, [parçalama](https://docs.microsoft.com/azure/sql-database/sql-database-elastic-scale-introduction)gibi birden çok düğüm arasında yatay olarak bölümlenebilir. Ancak, parçalama, kolayca iletişim kuramayan birçok parçaya veri tükürerek operasyonel yükü önemli ölçüde artırır. Bu pahalı ve yönetmek için zaman alıcı olabilir. Performansı, tablo birleştirmeleri ve başvuru bütünlüğünü etkileyebilir.

Veri yinelemeleri "son derece tutarlı" bir ilişkisel veritabanı kümesinde ağ bağlantısını kaybederse, veritabanına yazamazsınız. Sistem, bu değişikliği diğer veri çoğaltmaya kopyalayamayacağından yazma işlemini reddeder. İşlem tamamlanmadan önce her veri yinelemesinin güncelleştirisi gerekir.

NoSQL veritabanları genellikle yüksek kullanılabilirlik ve bölüm toleransını destekler. Bunlar yatay olarak ölçeklendirilir, genellikle emtia sunucuları arasında. Bu yaklaşım, hem coğrafi bölgeler içinde hem de coğrafi bölgeler arasında daha düşük bir maliyetle muazzam bir kullanılabilirlik sağlar. Artıklık ve hata toleransı sağlayarak bu makineler veya düğümler arasında verileri bölümlere ayırıp çoğaltırsınız. Dezavantajı tutarlılık olduğunu. Bir NoSQL düğümündeki verilerde yapılan bir değişikliğin diğer düğümlere yayılması biraz zaman alabilir. Genellikle, bir NoSQL veritabanı düğümü bir sorguya anında yanıt sağlar - sunulan veriler eski olsa ve henüz güncelleştirilmemiş olsa bile.

Veri yinelemeleri "yüksek oranda kullanılabilir" bir NoSQL veritabanı kümesinde bağlantı kaybederse, veritabanına bir yazma işlemini yine de tamamlayabilirsiniz. Veritabanı kümesi yazma işlemine izin verir ve kullanılabilir olduğunda her veri yinelemesini güncelleştirin.

Bu tür bir sonuç, ACID işlemlerinin desteklenmediği dağıtılmış veri sistemlerinin bir özelliği olan nihai tutarlılık olarak bilinir. Bu, bir veri öğesinin güncelleştirmesi ile bu güncelleştirmeyi çoğaltma düğümlerinin her birine yaymak için gereken süre arasında kısa bir gecikmedir. Normal koşullarda, gecikme genellikle kısa, ancak sorunlar ortaya çıktığında artabilir. Örneğin, bir ürün öğesini ABD'deki NoSQL veritabanında güncelleştirip aynı veri öğesini Avrupa'daki bir yineleme düğümünden sorgularsanız ne olur? Küme, Avrupa düğümünü ürün değişikliğiyle güncellene kadar önceki ürün bilgilerini alırsınız. Hemen bir sorgu sonucu döndürerek ve tüm yineleme düğümleri güncelleştirmek için beklemeyen, büyük ölçek ve hacim kazanmak, ancak eski verileri sunma olasılığı ile.

Yüksek kullanılabilirlik ve büyük ölçeklenebilirlik genellikle iş için güçlü tutarlılıktan daha önemlidir. Geliştiriciler, nihai tutarlılığı benimsemek için Sagas, CQRS ve eşzamanlı mesajlaşma gibi teknikler ve desenler uygulayabilir.

> Günümüzde CAP teoremi kısıtlamaları nın kısıtlanmasına özen dilmelidir. NewSQL adı verilen yeni bir veritabanı türü ortaya çıktı ve bu veritabanı altyapısı hem yatay ölçeklenebilirliği hem de NoSQL sistemlerinin ölçeklenebilir performansını destekleyecek şekilde genişletildi.

## <a name="considerations-for-relational-vs-nosql-systems"></a>İlişkisel ve NoSQL sistemleri için dikkat edilecek noktalar

Belirli veri gereksinimlerine bağlı olarak, bulut tabanlı bir mikro hizmet ilişkisel, NoSQL veri deposu veya her ikisini de uygulayabilir.

|  Şu anda bir NoSQL veri deposu düşünün: | Şu anda ilişkisel bir veritabanı düşünün: |
| :-------- | :-------- |
| Büyük ölçekli iş yükleri gerektiren yüksek hacimli iş yükleri var | İş yükü hacminiz tutarlıdır ve orta ve büyük ölçekli |
| İş yüklerinACID garantisi gerektirmez |  ASİt teminatları gereklidir |
| Verileriniz dinamiktir ve sık sık değişir | Verileriniz tahmin edilebilir ve yüksek yapılı |
| Veriler ilişkiler olmadan ifade edilebilir | Veriler ilişkisel olarak en iyi şekilde ifade edilir |  
| Hızlı yazma ve yazma güvenliği önemli değil gerekir | Yazma güvenliği bir gerekliliktir |  
| Veri alma basittir ve düz olma eğilimindedir | Karmaşık sorgular ve raporlarla çalışırsınız|
| Verileriniz geniş bir coğrafi dağılım gerektirir | Kullanıcılarınız daha merkezi |
| Uygulamanız, genel bulutlar gibi emtia donanımına dağıtılacaktır | Uygulamanız büyük, üst düzey donanıma dağıtılacak |
|||

Sonraki bölümlerde, buluta özgü verilerinizi depolamak ve yönetmek için Azure bulutunda bulunan seçenekleri inceleyeceğiz.

## <a name="database-as-a-service"></a>Hizmet Olarak Veritabanı

Başlangıç olarak, bir Azure sanal makinesi sağlayabilir ve her hizmet için seçtiğiniz veritabanını yükleyebilirsiniz. Çevre üzerinde tam denetime sahip olsanız da, bulut platformunun birçok yerleşik özelliğinden göz ardı edersiniz. Ayrıca, her hizmet için sanal makine ve veritabanını yönetmekten de sorumlu olabilirsiniz. Bu yaklaşım hızla zaman alıcı ve pahalı hale gelebilir.

Bunun yerine, bulut yerel uygulamalar, [Hizmet (DBaaS) olarak Veritabanı](https://www.stratoscale.com/blog/dbaas/what-is-database-as-a-service/)olarak ortaya çıkarılan veri hizmetlerini tercih eder. Tamamen bir bulut satıcısı tarafından yönetilen bu hizmetler yerleşik güvenlik, ölçeklenebilirlik ve izleme sağlar. Hizmete sahip olmak yerine, sadece bir [destek hizmeti](./definition.md#backing-services)olarak tüketirsiniz. Sağlayıcı kaynağı ölçekte çalışır ve performans ve bakım sorumluluğunu üstleniyor.

Bunlar, yüksek kullanılabilirlik elde etmek için bulut kullanılabilirliği bölgeleri ve bölgeleri arasında yapılandırılabilir. Hepsi tam zamanında kapasiteyi ve bir öde-as-you-go modelini destekler. Azure, her biri belirli avantajlara sahip farklı türde yönetilen veri hizmeti seçenekleri sunar.

Öncelikle Azure'da bulunan ilişkisel DBaaS hizmetlerine bakacağız. Microsoft'un amiral gemisi SQL Server veritabanının çeşitli açık kaynak seçenekleriyle birlikte kullanılabildiğini görürsünüz. Ardından Azure'daki NoSQL veri hizmetleri hakkında konuşuruz.

## <a name="azure-relational-databases"></a>Azure ilişkisel veritabanları

İlişkisel veri gerektiren bulut adaklı mikro hizmetler için Azure, Şekil 5-11'de gösterilen bir hizmet (DBaaS) teklifi olarak yönetilen dört ilişkisel veritabanı sunar.

![Azure'da yönetilen ilişkisel veritabanları](./media/azure-managed-databases.png)

**Şekil 5-11**. Azure'da kullanılabilen yönetilen ilişkisel veritabanları

Önceki şekilde, her birinin ek ücret ödemeden temel özelliklere sahip ortak bir DBaaS altyapısına nasıl dayandığına dikkat edin.

Bu özellikler, özellikle çok sayıda veritabanları sağlayan, ancak bunları yönetmek için sınırlı kaynaklara sahip kuruluşlar için önemlidir.
İşleme çekirdekleri, bellek ve temel depolama miktarını seçerek bir Azure veritabanını dakikalar içinde sağlayabilirsiniz. Veritabanını anında ölçeklendirebilir ve kaynakları çok az veya hiç kesinti olmadan dinamik olarak ayarlayabilirsiniz.

## <a name="azure-sql-database"></a>Azure SQL Veritabanı

Microsoft SQL Server'da uzmanlığa sahip geliştirme ekipleri [Azure SQL Veritabanı'nı](https://docs.microsoft.com/azure/sql-database/)göz önünde bulundurmalıdır. Microsoft SQL Server Database Engine'e dayalı, hizmet olarak tam olarak yönetilen bir ilişkisel veritabanıdır (DBaaS). Hizmet, SQL Server'ın şirket içi sürümünde bulunan birçok özelliği paylaşır ve SQL Server Veritabanı Altyapısının en son kararlı sürümünü çalıştırZ.

Azure SQL Veritabanı, bulut ayarı mikro hizmetiyle kullanmak için üç dağıtım seçeneğiyle kullanılabilir:

- Tek Veritabanı, Azure bulutundaki bir [Azure SQL Veritabanı sunucusunda](https://docs.microsoft.com/azure/sql-database/sql-database-servers) çalışan tam olarak yönetilen bir SQL Veritabanı'nı temsil eder. Veritabanı, temel veritabanı sunucusunda yapılandırma bağımlılığı olmadığı için [*içerdiği*](https://docs.microsoft.com/sql/relational-databases/databases/contained-databases) kabul edilir.
  
- [Yönetilen Örnek,](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance) Microsoft SQL Server Veritabanı Altyapısının şirket içi bir SQL Server ile %100'e yakın uyumluluk sağlayan tam olarak yönetilen bir örneğidir. Bu seçenek, 35 TB'a kadar daha büyük veritabanlarını destekler ve daha iyi yalıtım için bir [Azure Sanal Ağına](https://docs.microsoft.com/azure/virtual-network/virtual-networks-overview) yerleştirilir.

- [Azure SQL Veritabanı sunucusuz,](https://docs.microsoft.com/azure/sql-database/sql-database-serverless) iş yükü talebine göre otomatik olarak ölçeklendirilebilen tek bir veritabanı için bir bilgi işlem katmanıdır. Yalnızca saniyede kullanılan işlem miktarı için faturalar. Hizmet, aralıklı, öngörülemeyen kullanım alışkanlıkları olan ve hareketsizlik dönemleriyle serpiştirilmiş iş yükleri için çok uygundur. Sunucusuz bilgi işlem katmanı, yalnızca depolama ücretlerinin faturalanması için etkin olmayan dönemlerde veritabanlarını otomatik olarak duraklatır. Etkinlik döndüğünde otomatik olarak devam eder.

Azure, geleneksel Microsoft SQL Server yığınının ötesinde, üç popüler açık kaynak veritabanının yönetilen sürümlerini de sunar.

## <a name="open-source-databases-in-azure"></a>Azure'da açık kaynak veritabanları

Açık kaynak ilişkisel veritabanları bulut tabanlı uygulamalar için popüler bir seçim haline gelmiştir. Birçok işletme, özellikle maliyet tasarrufu için ticari veritabanı ürünleri üzerinde onları lehine. Birçok geliştirme ekibi esnekliklerinden, topluluk destekli gelişimlerinden ve araç ve uzantıekosisteminden yararlanır. Açık kaynak veritabanları birden çok bulut sağlayıcısı arasında dağıtılabilir ve bu da "satıcı kilitleme" endişesini en aza indirmeye yardımcı olur.

Geliştiriciler, azure vm'deki herhangi bir açık kaynak veritabanını kolayca barındırabilir. Bu yaklaşım, tam denetim sağlarken, veritabanının ve VM'nin yönetimi, izlenmesi ve bakımı için sizi kancaya koyar.

Ancak Microsoft, *azure'u tam olarak yönetilen* DBaaS hizmetleri olarak birkaç popüler açık kaynak veritabanı sunarak Azure'u "açık bir platform" olarak tutma taahhüdünü sürdürmektedir.

### <a name="azure-database-for-mysql"></a>MySQL için Azure Veritabanı

[MySQL](https://en.wikipedia.org/wiki/MySQL) açık kaynak ilişkisel bir veritabanı ve [LAMP yazılım yığını](https://en.wikipedia.org/wiki/LAMP_(software_bundle))üzerine inşa uygulamalar için bir sütundur. Yaygın ağır iş yükleri *okumak* için seçilen, Facebook, Twitter ve YouTube dahil olmak üzere birçok büyük kuruluşlar tarafından kullanılır. Topluluk sürümü ücretsiz olarak kullanılabilirken, kurumsal sürüm lisans satın alma gerektirir. İlk olarak 1995 yılında oluşturulan ürün 2008 yılında Sun Microsystems tarafından satın alınmıştır. Oracle, Sun ve MySQL'i 2010 yılında satın aldı.

[MySQL için Azure Veritabanı,](https://azure.microsoft.com/services/mysql/) açık kaynak MySQL Server altyapısına dayalı yönetilen bir ilişkisel veritabanı hizmetidir. MySQL Community sürümünü kullanır. Azure MySQL sunucusu hizmetin yönetim noktasıdır. Şirket içi dağıtımlar için kullanılan MySQL sunucu altyapısının aynısı. Altyapı, sunucu başına tek bir veritabanı veya kaynakları paylaşan sunucu başına birden çok veritabanı oluşturabilir. Yeni beceriler öğrenmek veya sanal makineleri yönetmek zorunda kalmadan aynı açık kaynak araçlarını kullanarak verileri yönetmeye devam edebilirsiniz.

### <a name="azure-database-for-mariadb"></a>MariaDB için Azure Veritabanı

[MariaDB](https://mariadb.com/) Sunucu başka bir popüler açık kaynak veritabanı sunucusudur. Oracle, MySQL'in *fork* sahibi Sun Microsystems'i satın aldığında MySQL'in çatalı olarak oluşturuldu. Amaç MariaDB'nin açık kaynak olarak kalmasını sağlamaktı. MariaDB MySQL'in bir çatalı olduğundan, veri ve tablo tanımları uyumludur ve istemci protokolleri, yapıları ve API'leri birbirine yakındır.

MariaDB güçlü bir topluluğa sahiptir ve birçok büyük işletme tarafından kullanılmaktadır. Oracle MySQL'i korumaya, geliştirmeye ve desteklemeye devam ederken, MariaDB vakfı MariaDB'yi yöneterek ürün ve belgelere genel katkıları sağlar.

[MariaDB için Azure Veritabanı,](https://azure.microsoft.com/services/mariadb/) Azure bulutundaki bir hizmet olarak tam olarak yönetilen bir ilişkisel veritabanıdır. Hizmet MariaDB topluluk sürümü sunucu motoru dayanmaktadır. Öngörülebilir performans ve dinamik ölçeklenebilirlik ile görev açısından kritik iş yüklerini işleyebilir.

### <a name="azure-database-for-postgresql"></a>PostgreSQL için Azure Veritabanı

[PostgreSQL,](https://www.postgresql.org/) 30 yılı aşkın aktif gelişime sahip açık kaynaklı bir ilişkisel veritabanıdır. PostgresSQL güvenilirlik ve veri bütünlüğü konusunda güçlü bir üne sahiptir. Bu özellik zengin, SQL uyumlu ve MySQL daha performant olarak kabul - özellikle karmaşık sorguları ve ağır yazma ile iş yükleri için. Apple, Red Hat ve Fujitsu gibi birçok büyük işletme PostgreSQL kullanarak ürünler üretmiş.

[PostgreSQL için Azure Veritabanı,](https://azure.microsoft.com/services/postgresql/) açık kaynaklı Postgres veritabanı altyapısına dayalı olarak tam olarak yönetilen bir ilişkisel veritabanı hizmetidir. Hizmet, C++, Java, Python, Düğüm, C\#ve PHP gibi birçok geliştirme platformunu destekler. Komut [satırı arabirimi](https://datamigration.microsoft.com/scenario/postgresql-to-azurepostgresql?step=1) aracını veya Azure Veri Geçiş Hizmeti'ni kullanarak PostgreSQL veritabanlarını bu veritabanına geçirebilirsiniz.

PostgreSQL için Azure Veritabanı iki dağıtım seçeneğiyle kullanılabilir:

- [Tek Sunucu](https://docs.microsoft.com/azure/postgresql/concepts-servers) dağıtım seçeneği, birçok veritabanı dağıtabileceğiniz birden çok veritabanı için merkezi bir yönetim noktasıdır. Fiyatlandırma, çekirdek ve depolama temel alınarak sunucu başına yapılandırılmıştır.

- [Hyperscale (Citus) seçeneği](https://azure.microsoft.com/blog/get-high-performance-scaling-for-your-azure-database-workloads-with-hyperscale/) Citus Data teknolojisi tarafından desteklenmektedir. Hızlı performans ve ölçek lendirmek için yüzlerce düğüm üzerinden tek bir veritabanını *yatay olarak ölçeklendirerek* yüksek performans sağlar. Bu seçenek, motorun belleğe daha fazla veri sığdırmasına, yüzlerce düğüme sorgular paralellemesine ve verileri daha hızlı dizine dahil etmesine olanak tanır.

## <a name="nosql-data-in-azure"></a>Azure'da NOSQL verileri

Cosmos DB, Azure bulutunda tam olarak yönetilen, küresel olarak dağıtılan bir NoSQL veritabanı hizmetidir. Coca-Cola, Skype, ExxonMobil ve Liberty Mutual gibi dünya çapında birçok büyük şirket tarafından benimsenmiştir.

Hizmetleriniz dünyanın her yerinden hızlı yanıt gerektiriyorsa, yüksek kullanılabilirlik veya elastik ölçeklenebilirlik, Cosmos DB mükemmel bir seçimdir. Şekil 5-12 Cosmos DB'yi gösteriyor.

![Cosmos DB'ye Genel Bakış](./media/cosmos-db-overview.png)

**Şekil 5-12**: Cosmos DB'ye Genel Bakış

Önceki şekil, Cosmos DB'de bulunan yerleşik bulut yerel özelliklerinin çoğunu sunar. Bu bölümde, onlara daha yakından bakacağız.

### <a name="global-support"></a>Küresel destek

Bulut ait uygulamalar genellikle küresel bir hedef kitleye sahiptir ve genel ölçek gerektirir.

Cosmos veritabanlarını bölgelere veya dünyanın dört bir yanına dağıtarak, verileri kullanıcılarınıza yakın bir yere yerleştirebilir, yanıt süresini kısaltabilir ve gecikme süresini azaltabilirsiniz. Hizmetlerinizi duraklatmadan veya yeniden dağıtmadan bir bölgeden veritabanı ekleyebilir veya kaldırabilirsiniz. Arka planda, Cosmos DB verileri yapılandırılan bölgelerin her birine saydam olarak çoğaltır.

Cosmos DB, genel düzeyde [etkin/etkin](https://kemptechnologies.com/white-papers/unfog-confusion-active-passive-activeactive-load-balancing/) kümelenmeyi destekler ve veritabanı bölgenizden herhangi birini *hem yazma ları hem de okumaları*destekleyecek şekilde yapılandırmanızı sağlar.

[Multi-Master](https://docs.microsoft.com/azure/cosmos-db/multi-master-benefits) protokolü, Cosmos DB'de aşağıdaki işlevselliği sağlayan önemli bir özelliktir:

- Sınırsız elastik yazmak ve ölçeklenebilirlik okuyun.

- 99.999% okumak ve tüm dünyada kullanılabilirlik yazmak.

- Garantili okuma ve yazma 99 yüzdelik olarak 10 milisaniyeden daha az bir sürede servis edilir.

Cosmos DB [Çoklu Homing API'leri](https://docs.microsoft.com/azure/cosmos-db/distribute-data-globally)ile mikro hizmetiniz otomatik olarak en yakın Azure bölgesinden haberdar olur ve bu bölgeye istekler gönderir. En yakın bölge cosmos DB tarafından herhangi bir yapılandırma değişikliği olmadan tanımlanır. Bir bölge kullanılamıyorsa, Çoklu Homing özelliği istekleri otomatik olarak bir sonraki en yakın kullanılabilir bölgeye yönlendirir.

### <a name="multi-model-support"></a>Çok modelli destek

Yekpare uygulamaları bulut-yerel mimariye yeniden platformlaaktarırken, geliştirme ekiplerinin bazen açık kaynak kodlu NoSQL veri depolarını geçirmeleri gerekir. Cosmos DB, *çok modelli* veri platformu ile bu NoSQL veri depolarında yaptığınız yatırımı korumanıza yardımcı olabilir. Şekil 5-13 desteklenen NoSQL [uyumluluk API'lerini](https://www.wikiwand.com/en/Cosmos_DB)gösterir.

![Cosmos DB sağlayıcıları](./media/cosmos-db-providers.png)

**Şekil 5-13**: Cosmos DB sağlayıcıları

Geliştirme ekipleri, veri veya kodda en az değişiklikle varolan Mongo, Gremlin veya Cassandra veritabanlarını Cosmos DB'ye geçirebilirsiniz. Yeni uygulamalar için geliştirme ekipleri açık kaynak seçenekleri veya yerleşik SQL API modeli arasından seçim yapabilir.

> Cosmos, verileri ilkel veri türlerinden oluşan basit bir yapı biçiminde dahili olarak saklar. Her istek için veritabanı altyapısı ilkel verileri seçtiğiniz model gösterimine çevirir.

Önceki şekilde, 5-13, [Tablo API](https://docs.microsoft.com/azure/cosmos-db/table-introduction) seçeneğine dikkat edin. Bu API, Azure Tablo Depolama'nın bir evrimidir. Her ikisi de aynı temel tablo modelini paylaşır, ancak Cosmos DB Table API, Azure Depolama API'sinde bulunmayan premium geliştirmeler ekler. Bu özellikler Şekil 5-4'te karşılaştırılır.

![Azure Tablo API'si](media/azure-table-api.png)

**Şekil 5-14**: Azure Tablo API Sağlayıcıları

Azure Tablo depolama alanını tüketen mikro hizmetler Cosmos DB Table API'ye kolayca geçiş yapabilir. Kod değişikliği gerekmez.

### <a name="tunable-consistency"></a>Tunable tutarlılık

Daha önce *İlişkisel vs NoSQL* bölümünde, veri *tutarlılığı*konusunu tartıştık. Veri tutarlılığı verilerinizin *bütünlüğünü* ifade eder. Dağıtılmış verilere sahip bulut yerel hizmetler çoğaltmaya dayanır ve okuma tutarlılığı, kullanılabilirlik ve gecikme süresi arasında temel bir denge sağlamalıdır.

Çoğu dağıtılmış veritabanları geliştiricilerin iki tutarlılık modeli arasında seçim yapmalarına olanak tanır: güçlü tutarlılık ve nihai tutarlılık. *Güçlü tutarlılık* veri programlanabilirliğinin altın standardıdır. Sistem tüm veritabanı kopyalarında çoğaltmak için bir güncelleştirme bekliyor gecikme sayılsa bile, sorgunun her zaman en güncel verileri döndüreceğini garanti eder. *Nihai tutarlılık* için yapılandırılan bir veritabanı, bu veriler en güncel kopya olmasa bile verileri hemen döndürecektir. İkinci seçenek daha yüksek kullanılabilirlik, daha büyük ölçek ve daha yüksek performans sağlar.

Azure Cosmos DB, Şekil 5-15'te gösterilen beş iyi tanımlanmış [tutarlılık modeli](https://docs.microsoft.com/azure/cosmos-db/consistency-levels) sunar.

![Cosmos DB tutarlılık grafiği](./media/cosmos-consistency-level-graph.png)

**Şekil 5-15**: Cosmos DB Tutarlılık Düzeyleri

 Bu seçenekler, tutarlılık, kullanılabilirlik ve verilerinizin performansı için kesin seçimler ve parçalı dengelemeler yapmanızı sağlar. Şekil 5-16 her düzeyi açıklar.

![Cosmos DB tutarlılık düzeyleri](./media/cosmos-db-consistency-levels.png)

**Şekil 5-16**: Cosmos DB Tutarlılık Düzeyi Açıklaması

Makalede [9-Ball Behind Başlarken: Cosmos DB Tutarlılık Düzeyleri Açıkladı](https://blog.jeremylikness.com/blog/2018-03-23_getting-behind-the-9ball-cosmosdb-consistency-levels/), Microsoft Cloud Developer Advocate Jeremy Likeness beş model mükemmel bir açıklama sağlar.

### <a name="partitioning"></a>Bölümleme

Azure Cosmos DB, bulut ayarı olan hizmetlerinizin performans gereksinimlerini karşılamak için bir veritabanını ölçeklendirmek için otomatik [bölümlemayı](https://docs.microsoft.com/azure/cosmos-db/partitioning-overview) benimser.

Veritabanları, kapsayıcılar ve öğeler oluşturarak Cosmos DB verilerindeki verileri yönetirsiniz.

Kapsayıcılar Bir Cosmos DB veritabanında yaşar ve öğelerin şema-agnostik gruplandırmatemsil eder. Öğeler kapsayıcıya eklediğiniz verilerdir. Belgeler, satırlar, düğümler veya kenarlar olarak temsil edilirler. Bir kapsayıcıya eklenen tüm öğeler otomatik olarak dizine eklenir.

Kapsayıcıyı bölmek için öğeler mantıksal bölümler adı verilen farklı alt kümelere ayrılır. Mantıksal bölümler, bir kapsayıcıdaki her öğeyle ilişkili bir bölüm anahtarının değerine göre doldurulur. Şekil 5-18, her biri bir bölüm anahtar değerine dayalı mantıksal bir bölüme sahip iki kapsayıcıyı gösterir.

![Cosmos DB bölümleme mekaniği](./media/cosmos-db-partitioning.png)

**Şekil 5-18**: Cosmos DB bölümleme mekaniği

Önceki şekilde, her öğenin 'şehir' veya 'havaalanı' bölüm anahtarını nasıl içerdiğini not edin. Anahtar öğenin mantıksal bölümleyi belirler. Şehir kodu olan öğeler soldaki kapsayıcıya, havaalanı kodu olan öğeler ise sağdaki konteynere atanır. Bölüm anahtar değerini kimlik değeriyle birleştirmek, öğeyi benzersiz olarak tanımlayan bir öğenin dizinini oluşturur.

Dahili olarak, Cosmos DB otomatik olarak kapsayıcının ölçeklenebilirlik ve performans gereksinimlerini karşılamak için fiziksel bölümler üzerinde [mantıksal bölümlerin](https://docs.microsoft.com/azure/cosmos-db/partition-data) yerleşimyönetir. Uygulama çıktısı ve depolama gereksinimleri arttıkça, Azure Cosmos DB mantıksal bölümleri daha fazla sayıda sunucuya yeniden dağıtır. Yeniden dağıtım işlemleri Cosmos DB tarafından yönetilir ve kesintisiz veya kapalı kalma süresi olmadan çağrılır.

## <a name="newsql-databases"></a>NewSQL veritabanları

*NewSQL, NoSQL'in* dağıtılmış ölçeklenebilirliğini ilişkisel bir veritabanının ACID garantileri ile birleştiren yeni ortaya çıkan bir veritabanı teknolojisidir. NewSQL veritabanları, dağıtılmış ortamlarda, tam işlem desteği ve ACID uyumluluğu yla yüksek hacimli verileri işlemesi gereken iş sistemleri için önemlidir. NoSQL veritabanı büyük ölçeklenebilirlik sağlayabilir iken, veri tutarlılığı garanti etmez. Tutarsız verilerden aralıklı sorunlar geliştirme ekibine bir yük getirebilir. Geliştiriciler, tutarsız verilerin neden olduğu sorunları yönetmek için mikro hizmet kodlarına koruma lar oluşturmalıdır.

Cloud Native Computing Foundation (CNCF) birkaç NewSQL veritabanı projesine sahiptir.

| Project | Özellikler |
| :-------- | :-------- |
| Hamamböceği DB |Küresel olarak ölçeklendirilen ACID uyumlu, ilişkisel bir veritabanı. Kümeye yeni bir düğüm ekleyin ve Hamamböceği verileri örnekler ve coğrafyalar arasında dengelemeyi halleder. Güvenilirliği sağlamak için yinelemeler oluşturur, yönetir ve dağıtır. Açık kaynak kodve serbestçe kullanılabilir.  |
| TiDB | Karma İşlemsel ve Analitik İşlem (HTAP) iş yüklerini destekleyen açık kaynak veritabanı. MySQL uyumludur ve yatay ölçeklenebilirlik, güçlü tutarlılık ve yüksek kullanılabilirlik özellikleridir.  TiDB bir MySQL sunucusu gibi davranır. Uygulamanızda kapsamlı kod değişiklikleri gerektirmeden varolan MySQL istemci kitaplıklarını kullanmaya devam edebilirsiniz. |
| YugabyteDB | Açık kaynak kodlu, yüksek performanslı, dağıtılmış SQL veritabanı. Düşük sorgu gecikmesi, hatalara karşı esneklik ve genel veri dağıtım destekler. YugabyteDB PostgressSQL uyumludur ve ölçeklenmiş RDBMS ve internet ölçekli OLTP iş yüklerini işler. Ürün ayrıca NoSQL'i destekler ve Cassandra ile uyumludur. |
|Vitess | Vitess, büyük MySQL örnek kümelerini dağıtmak, ölçekleme ve yönetmek için bir veritabanı çözümüdür. Genel veya özel bulut mimarisinde çalıştırılabilir. Birçok önemli MySQL özelliğini ve hem dikey hem de yatay parçalama desteğini birleştirir ve genişletir. YouTube tarafından menşeli, Vitess 2011 yılından bu yana tüm YouTube veritabanı trafiği hizmet vermektedir. |

Önceki rakamdaki açık kaynak projeleri Cloud Native Computing Foundation tarafından kullanılabilir. Tekliflerin üçü .NET Core desteği içeren tam veritabanı ürünleridir. Diğeri, Vitess, MySQL örneklerinin büyük kümelerini yatay olarak ölçeklendiren bir veritabanı kümeleme sistemidir.

NewSQL veritabanları için önemli bir tasarım hedefi, platformun esnekliğinden ve ölçeklenebilirliğinden yararlanarak Kubernetes'te yerel olarak çalışmaktır.

NewSQL veritabanları, temel sanal makinelerin bir anda yeniden başlatılabildiği veya yeniden zamanlanabileceği geçici bulut ortamlarında başarılı olmak üzere tasarlanmıştır. Veritabanları, veri kaybı veya kapalı kalma süresi olmadan düğüm hatalarından kurtulacak şekilde tasarlanmıştır. Örneğin Hamamböceği, bir kümedeki düğümler arasında herhangi bir verinin üç tutarlı kopyasını koruyarak bir makine kaybından kurtulabilir.

Kubernetes, istemcinin tek bir DNS girişinden aynı NewSQL veritabanları ndan oluşan bir gruba hitap etmesine izin vermek için bir *Hizmet yapısı* kullanır. Veritabanı örneklerini ilişkili olduğu hizmetin adresinden ayırarak, varolan uygulama örneklerini bozmadan ölçeklendirebiliriz. Belirli bir zamanda herhangi bir hizmete istek göndermek her zaman aynı sonucu verir.

Bu senaryoda, tüm veritabanı örnekleri eşittir. Birincil veya ikincil ilişki yoktur. Hamamböceği'nde bulunan *konsensüs çoğaltma* gibi teknikler herhangi bir veritabanı düğümüherhangi bir istek işlemek için izin verir. Yük dengeli bir istek alan düğüm, yerel olarak ihtiyaç duyduğu verilere sahipse, hemen yanıt verir. Değilse, düğüm bir ağ geçidi olur ve doğru yanıtı almak için isteği uygun düğümlere iletin. İstemcinin bakış açısından, her veritabanı düğümü aynıdır: Perde arkasında çalışan düzinelerce hatta yüzlerce düğümolmasına rağmen, tek bir makine sisteminin tutarlılık garantileri ile tek bir *mantıksal* veritabanı olarak görünürler.

NewSQL veritabanlarının arkasındaki mekaniği ayrıntılı bir şekilde görmek için [DASH: Dört Kubernetes-Native Databases](https://thenewstack.io/dash-four-properties-of-kubernetes-native-databases/) makalesine bakın.

## <a name="data-migration-to-the-cloud"></a>Buluta veri geçişi

Daha fazla zaman alan görevlerden biri, verileri bir veri platformundan diğerine geçirmektir. [Azure Veri Geçiş Hizmeti](https://azure.microsoft.com/services/database-migration/) bu tür çabaların hızlandırılabiliyor. Birkaç dış veritabanı kaynağından gelen verileri en az kapalı kalma süresiyle Azure Veri platformlarına aktarabilir. Hedef platformlar aşağıdaki hizmetleri içerir:

- Azure SQL Veritabanı
- MySQL için Azure Veritabanı
- MariaDB için Azure Veritabanı
- PostgreSQL için Azure Veritabanı
- CosmosDB
  
Hizmet, küçük veya büyük bir geçiş yürütmek için gereken değişiklikler boyunca size rehberlik etmek için öneriler sağlar.

>[!div class="step-by-step"]
>[Önceki](Database-per-microservice.md)
>[Sonraki](azure-caching.md)
