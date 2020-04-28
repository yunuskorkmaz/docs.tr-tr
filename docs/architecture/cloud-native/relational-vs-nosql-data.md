---
title: İlişkisel veriler ile NoSQL verilerinin karşılaştırması
description: Bulutta yerel uygulamalarda ilişkisel ve NoSQL verileri hakkında bilgi edinin
author: robvet
ms.date: 01/22/2020
ms.openlocfilehash: c074be0c973156c1757b97ffc727711d5dd072af
ms.sourcegitcommit: 5988e9a29cedb8757320817deda3c08c6f44a6aa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2020
ms.locfileid: "82199995"
---
# <a name="relational-vs-nosql-data"></a>İlişkisel veriler ile NoSQL verilerinin karşılaştırması

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

İlişkisel ve NoSQL, bulutta yerel uygulamalarda yaygın olarak uygulanan iki tür veritabanı sistemidir. Bunlar farklı şekilde oluşturulmuştur, verileri farklı bir şekilde depolar ve farklı şekilde erişilirler. Bu bölümde, her ikisine de bakacağız. Bu bölümde daha sonra *Newsql*adlı yeni bir veritabanı teknolojisine bakacağız.

*İlişkisel veritabanları* , Decades için yaygın olarak kullanılan bir teknolojidir. Bunlar, Yetişkin, kanıtlanmış ve yaygın olarak uygulanan bir uygulamalılar. Rekabet veritabanı ürünleri, araçları ve uzmanlığı ABO. İlişkisel veritabanları ilgili veri tablolarının bir deposunu sağlar. Bu tablolar sabit bir şemaya sahiptir, verileri yönetmek için SQL (Yapılandırılmış Sorgu Dili) kullanın ve ACID garantilerini destekler.

*Hayır-SQL veritabanları* , yüksek performanslı, ilişkisel olmayan veri depolarına başvurur. Bu kişiler, kullanım kolaylığı, ölçeklenebilirlik, esnekliği ve kullanılabilirlik özellikleriyle Excel. NoSQL, normalleştirilmiş verilerin tablolarını birleştirmek yerine yapılandırılmamış veya yarı yapılandırılmış verileri genellikle anahtar-değer çiftleri veya JSON belgeleri içinde depolar. Hayır-SQL veritabanları genellikle tek bir veritabanı bölümünün kapsamından fazla ACID garantisi vermez. Alt saniye yanıt süresi gerektiren yüksek hacimli hizmetler NoSQL veri depolarını kabul etmek.

Dağıtılmış bulut Yerel sistemlerine yönelik [NoSQL](https://www.geeksforgeeks.org/introduction-to-nosql/) teknolojilerinin etkisi aşırı belirtilemez. Bu alandaki yeni veri teknolojilerinin bir şekilde, ilişkisel veritabanlarına özel olarak bir şekilde güvenilme çözümleri bozulur.

NoSQL veritabanları, her biri belirli kullanım örneklerine uygun olan verilere erişmek ve bunları yönetmek için birkaç farklı model içerir. Şekil 5-9 dört ortak model sunar.

![NoSQL veri modelleri](./media/types-of-nosql-datastores.png)

**Şekil 5-9**: NoSQL veritabanları için veri modelleri

| Model | Özellikler |
| :-------- | :-------- |
| Belge Mağazası | Veriler ve meta veriler, veritabanının içindeki JSON tabanlı belgelerde hiyerarşik olarak depolanır. |
| Anahtar değer deposu | NoSQL veritabanlarının en basit yolu, verileri anahtar-değer çiftleri koleksiyonu olarak temsil eder. |
| Geniş sütunlu depo | İlgili veriler tek bir sütunda iç içe anahtar/değer çiftleri kümesi olarak depolanır. |
| Grafik deposu | Veriler bir grafik yapısında düğüm, kenar ve veri özellikleri olarak depolanır. |

## <a name="the-cap-theorem"></a>Üst sınır

Bu veritabanı türleri arasındaki farklılıkları anlamanın bir yolu olarak, durumu depolayan dağıtılmış sistemlere uygulanan bir ilke kümesi olan üst SıNıRı göz önünde bulundurun. Şekil 5-10, CAP 'in üç özelliğini gösterir.

![CAP 'ler](./media/cap-theorem.png)

**Şekil 5-10**. Üst sınır

Bu, dağıtılmış veri sistemlerinin tutarlılık, kullanılabilirlik ve bölüm toleransı arasında bir denge sunabileceği durumlar olur. Ancak, herhangi bir veritabanı üç özelliği yalnızca *iki* özelliği garanti edebilir:

- *Denetleme.* Kümedeki her düğüm, sistemin tüm çoğaltmalar güncellene kadar isteği engellemeniz gerekir olsa bile en son verilerle yanıt verir. Şu anda güncelleştirilen bir öğe için "tutarlı bir sistem" sorgulerseniz, tüm çoğaltmalar başarıyla güncelleştirilene kadar bu yanıtı beklemelisiniz. Ancak, en güncel verileri alacaksınız.

- *Sonrası.* Her düğüm, bu yanıt en son veriler olmasa bile anında yanıt döndürür. Güncelleştiren bir öğe için "kullanılabilir sistem" i sorgulayıp, hizmetin bu anda sağlayabilmesini sağlayacak en iyi yanıtı alırsınız.

- *Bölüm toleransı.* Çoğaltılan bir veri düğümü başarısız olsa da veya diğer çoğaltılan veri düğümleriyle bağlantıyı kaybederse bile sistemin çalışmaya devam etmesini güvence altına alır.

İlişkisel veritabanları genellikle tutarlılık ve kullanılabilirlik sağlar ancak bölüm toleransı sağlamaz. Bunlar genellikle tek bir sunucu için sağlanır ve makineye daha fazla kaynak ekleyerek dikey olarak ölçeklenir.

Birçok ilişkisel veritabanı sistemi, birincil veritabanının kopyalarının diğer ikincil sunucu örneklerine yapılabilecek yerleşik çoğaltma özelliklerini destekler. Yazma işlemleri birincil örneğe yapılır ve ikincinin her birine çoğaltılır. Bir hata sonrasında, birincil örnek yüksek kullanılabilirlik sağlamak için ikincil üzerinde yük devreder. İkincil öğeler, okuma işlemlerini dağıtmak için de kullanılabilir. Yazma işlemleri her zaman birincil çoğaltmaya karşı hareket ederken, sistem yükünü azaltmak için okuma işlemleri, ikincilden herhangi birine yönlendirilebilir.

Veriler, [parçalı olarak gibi](https://docs.microsoft.com/azure/sql-database/sql-database-elastic-scale-introduction)birden çok düğüm arasında yatay olarak bölümlenebilir. Ancak, parçalama, kolayca iletişim kuramayan birçok parça genelinde Spitting verileri tarafından işlem yükünü önemli ölçüde artırır. Yönetilmesi maliyetli ve zaman alıcı olabilir. Performans, tablo birleştirmeleri ve başvurusal bütünlüğü etkileyen performansı etkileyebilir.

Veri çoğaltmaları "yüksek oranda tutarlı" bir ilişkisel veritabanı kümesinde ağ bağlantısını kaybettiyseniz veritabanına yazabilemezsiniz. Sistem, bu değişikliği diğer veri çoğaltmasına çoğaltacağından yazma işlemini reddeder. İşlem tamamlanmadan önce her veri çoğaltmasının güncelleştirilmesi vardır.

NoSQL veritabanları genellikle yüksek kullanılabilirliği ve bölüm toleransını destekler. Bunlar, genellikle emtia sunucularında yatay olarak ölçeklenir. Bu yaklaşım, daha düşük bir maliyetle coğrafi bölgeler içinde ve arasında yüksek kullanılabilirlik sağlar. Bu makineler veya düğümler genelinde verileri bölümleyip çoğaltarak, artıklık ve hataya dayanıklılık sağlar. Downsıde, tutardır. Bir NoSQL düğümündeki verilerde yapılan değişikliğin, diğer düğümlere yayılması biraz zaman alabilir. Genellikle, bir NoSQL veritabanı düğümü, sunulan veriler eski ve henüz güncelleştirilmemiş olsa bile, bir sorguya anında yanıt verir.

Veri çoğaltmalarının, "yüksek oranda kullanılabilir" NoSQL veritabanı kümesinde bağlantıyı kaybetmeniz durumunda, veritabanına bir yazma işlemi de tamamlayabilirsiniz. Veritabanı kümesi, yazma işlemine izin verir ve her veri çoğaltmasını kullanılabilir hale geldiğinde güncelleştirebilir.

Bu tür bir sonuç, ACID işlemlerinin desteklenmediği dağıtılmış veri sistemlerinin bir özelliği olan nihai tutarlılık olarak bilinir. Bu, bir veri öğesi güncelleştirmesi ve bu güncelleştirmenin her bir çoğaltma düğümüne yayılması için geçen süre arasında kısa bir gecikmeden oluşur. Normal koşullarda, gecikme genellikle kısa olur, ancak sorunlar ortaya çıktığında artabilir. Örneğin, Birleşik Devletler bir NoSQL veritabanında ürün öğesini güncelleştirmek ve aynı veri öğesini Avrupa 'daki bir çoğaltma düğümünden sorgulamak için ne olur? Küme Avrupa düğümünü ürün değişikliğine güncelleştirene kadar önceki ürün bilgilerini alacaksınız. Hemen bir sorgu sonucu döndürerek ve tüm çoğaltma düğümlerinin güncelleştirilmesini beklemedikten sonra, büyük ölçekli ve hacimde daha eski verileri sunma olasılığa sahip olursunuz.

Yüksek kullanılabilirlik ve büyük ölçeklenebilirlik genellikle iş açısından güçlü tutarlılığa göre daha önemlidir. Geliştiriciler, son tutarlılığı daha fazla ayraç içine almak için Sagaz, CQRS ve zaman uyumsuz mesajlaşma gibi teknikleri ve desenleri uygulayabilir.

> Günümüzde, bu, üst sınır kısıtlamaları conidering olduğunda gerçekleştirilmelidir. NewSQL adlı yeni bir veritabanı türü, ilişkisel veritabanı altyapısını hem yatay ölçeklenebilirliği hem de NoSQL sistemlerinin ölçeklenebilir performansını destekleyecek şekilde genişleten bir ortaya çıktı.

## <a name="considerations-for-relational-vs-nosql-systems"></a>İlişkisel ve NoSQL sistemlerine yönelik konular

Belirli veri gereksinimlerine bağlı olarak, bulut Yerel tabanlı bir mikro hizmet, ilişkisel, NoSQL veri deposu veya her ikisini de uygulayabilir.

|  Şu durumlarda bir NoSQL veri deposu göz önünde bulundurun: | Şu durumlarda ilişkisel bir veritabanını göz önünde bulundurun: |
| :-------- | :-------- |
| Büyük ölçekli olan yüksek hacimli iş yükleriniz var | İş yükü biriminiz tutarlı ve orta ila büyük ölçekli bir ölçeğe ihtiyaç duyuyor |
| İş yükleriniz ACID garantisi gerektirmez |  ACID garantisi gereklidir |
| Verileriniz dinamik ve sık sık değişir | Verileriniz öngörülebilir ve yüksek oranda yapılandırılmış |
| Veriler ilişki olmadan ifade edilebilir | Veriler en iyi şekilde ilişkisel olarak ifade edilir |  
| Hızlı yazma ve yazma güvenliği önemli değildir | Yazma güvenliği bir gereksinimdir |  
| Veri alma basittir ve düz olma eğilimi gösterir | Karmaşık sorgular ve raporlarla çalışırsınız|
| Verileriniz geniş bir coğrafi dağıtım gerektiriyor | Kullanıcılarınız daha merkezileştirilmiş |
| Uygulamanız, genel bulutlarla olduğu gibi emtia donanımına dağıtılır | Uygulamanız büyük, yüksek kaliteli donanıma dağıtılacak |
|||

Sonraki bölümlerde, bulutta yerel verilerinizi depolamak ve yönetmek için Azure bulutu 'nda bulunan seçenekleri araştıracağız.

## <a name="database-as-a-service"></a>Hizmet olarak veritabanı

Başlamak için bir Azure sanal makinesi sağlayıp her hizmet için istediğiniz veritabanını yükleyebilirsiniz. Ortam üzerinde tam denetime sahip olduğunuzda, bulut platformunun birçok yerleşik özelliğine inmelisiniz. Ayrıca, her hizmet için sanal makine ve veritabanının yönetilmesi de sorumludur. Bu yaklaşım hızla zaman alabilir ve pahalı hale gelebilir.

Bunun yerine, bulutta yerel uygulamalar, [hizmet olarak veritabanı (DBaaS)](https://www.stratoscale.com/blog/dbaas/what-is-database-as-a-service/)olarak sunulan veri hizmetlerini tercih bir şekilde tercih. Bir bulut satıcısı tarafından tam olarak yönetilen bu hizmetler yerleşik güvenlik, ölçeklenebilirlik ve izleme sağlar. Hizmet sahibi olmak yerine, bunu bir [yedekleme hizmeti](./definition.md#backing-services)olarak kullanırsınız. Sağlayıcı, kaynağı ölçeklendirerek çalışır ve performans ve bakım sorumluluğunu da üstlenir.

Yüksek kullanılabilirlik elde etmek için bulut kullanılabilirliği alanları ve bölgeleri arasında yapılandırılabilirler. Hepsi, tam zamanında kapasiteyi ve kullandıkça öde modelini destekler. Azure, her biri belirli avantajları içeren farklı türlerdeki yönetilen veri hizmeti seçeneklerine sahiptir.

Önce Azure 'da bulunan ilişkisel DBaaS hizmetlerine bakacağız. Microsoft 'un flaggeme SQL Server veritabanının çeşitli açık kaynaklı seçeneklerle birlikte kullanılabildiğini görürsünüz. Daha sonra, Azure 'da NoSQL veri hizmetlerinden bahsereceğiz.

## <a name="azure-relational-databases"></a>Azure ilişkisel veritabanları

İlişkisel veriler gerektiren bulut Yerel mikro hizmetleri için Azure, Şekil 5-11 ' de gösterilen dört adet yönetilen ilişkisel veritabanı (DBaaS) teklifleri sunar.

![Azure 'da yönetilen ilişkisel veritabanları](./media/azure-managed-databases.png)

**Şekil 5-11**. Azure 'da kullanılabilen yönetilen ilişkisel veritabanları

Önceki şekilde, her birinin ek bir ücret ödemeden önemli özellikleri sunan ortak bir DBaaS altyapısı üzerinde nasıl yer aldığına değinirsiniz.

Bu özellikler özellikle çok sayıda veritabanı sağlayan kuruluşlar için önemlidir, ancak bunları yönetmek için sınırlı kaynak vardır.
İşlem çekirdekleri, bellek ve temel depolama miktarını seçerek dakikalar içinde bir Azure veritabanı sağlayabilirsiniz. Veritabanını hareket halindeyken ölçeklendirebilir ve kapalı kalma süresi olmadan kaynakları dinamik olarak ayarlayabilirsiniz.

## <a name="azure-sql-database"></a>Azure SQL Veritabanı

Microsoft SQL Server uzmanlığa sahip geliştirme ekipleri [Azure SQL veritabanı](https://docs.microsoft.com/azure/sql-database/)'nı göz önünde bulundurmalıdır. Bu, Microsoft SQL Server veritabanı altyapısını temel alan, tam olarak yönetilen bir hizmet olarak ilişkisel veritabanı (DBaaS). Hizmet, SQL Server 'ın şirket içi sürümünde bulunan birçok özelliği paylaşır ve SQL Server veritabanı altyapısının en son kararlı sürümünü çalıştırır.

Azure SQL veritabanı, bulut Yerel mikro hizmeti ile kullanılmak üzere üç dağıtım seçeneği ile kullanılabilir:

- Tek Veritabanı, Azure buluttaki bir [Azure SQL veritabanı sunucusunda](https://docs.microsoft.com/azure/sql-database/sql-database-servers) çalışan, tam olarak YÖNETILEN bir SQL veritabanını temsil eder. Veritabanı, temel alınan veritabanı sunucusunda hiç yapılandırma bağımlılığı olmadığından, [*içinde*](https://docs.microsoft.com/sql/relational-databases/databases/contained-databases) olduğu kabul edilir.
  
- [Yönetilen örnek](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance) , Microsoft SQL Server veritabanı altyapısının, şirket içi SQL Server yaklaşık %100 uyumluluk sağlayan tam olarak yönetilen bir örneğidir. Bu seçenek, 35 TB 'a kadar daha büyük veritabanlarını destekler ve daha iyi yalıtım için bir [Azure sanal ağına](https://docs.microsoft.com/azure/virtual-network/virtual-networks-overview) yerleştirilir.

- [Azure SQL veritabanı sunucusuz](https://docs.microsoft.com/azure/sql-database/sql-database-serverless) , iş yükü talebine göre otomatik olarak ölçeklenen tek bir veritabanı için bir işlem katmandır. Yalnızca saniyede kullanılan işlem miktarı için faturalandırılır. Hizmet, zaman aralıklı, öngörülemeyen kullanım desenlerine sahip iş yükleri için uygundur, işlem yapılmayan dönemler ile yapılır. Sunucusuz işlem katmanı Ayrıca, etkin olmayan dönemler sırasında veritabanlarını otomatik olarak duraklatarak yalnızca depolama ücretleri faturalandırılır. Etkinlik geri döndüğünde otomatik olarak devam eder.

Geleneksel Microsoft SQL Server yığının ötesinde Azure, ayrıca üç popüler açık kaynaklı veritabanının yönetilen sürümlerini de sunar.

## <a name="open-source-databases-in-azure"></a>Azure 'da açık kaynaklı veritabanları

Açık kaynaklı ilişkisel veritabanları, bulutta yerel uygulamalar için popüler bir seçenek haline geldi. Birçok kuruluş, özellikle de maliyet tasarrufları için ticari veritabanı ürünleri üzerinden tercih edilir. Birçok geliştirme ekibinin esnekliği, topluluk tarafından desteklenen geliştirme ve araçların ve genişletmeler ekosistemi avantajlarından yararlanın. Açık kaynaklı veritabanları birden çok bulut sağlayıcısı arasında dağıtılabilir ve bu, "satıcı kilidi-ın" kaygısını en aza indirmenize yardımcı olur.

Geliştiriciler bir Azure VM 'de açık kaynaklı bir veritabanını kolayca kendi kendine barındırabilir. Tam denetim sağlarken, bu yaklaşım veritabanını ve VM 'yi yönetmek, izlemek ve bakımını yapmak için sizi kanca altına koyar.

Ancak Microsoft, *tam olarak yönetilen* DBaaS Hizmetleri olarak çeşitli popüler açık kaynaklı veritabanları sunarak Azure 'u bir "açık platform" olarak tutma taahhüdüne devam etmektedir.

### <a name="azure-database-for-mysql"></a>MySQL için Azure Veritabanı

[MySQL](https://en.wikipedia.org/wiki/MySQL) , [lamba yazılım yığınında](https://en.wikipedia.org/wiki/LAMP_(software_bundle))oluşturulan uygulamalara yönelik açık kaynaklı bir ilişkisel veritabanıdır. *Okuma ağır* iş yükleri için yaygın olarak seçilen, Facebook, Twitter ve YouTube dahil olmak üzere çok büyük kuruluşlar tarafından kullanılır. Community sürümü ücretsiz olarak kullanılabilir, ancak Enterprise sürümü bir lisans satın alma işlemi gerektirir. Başlangıçta 1995 ' de oluşturulan ürün, Sun Microsystems tarafından 2008 ' de satın alındı. Oracle 2010 ' de Sun ve MySQL aldı.

[MySQL Için Azure veritabanı](https://azure.microsoft.com/services/mysql/) , açık kaynak MySQL sunucu altyapısını temel alan, yönetilen bir ilişkisel veritabanı hizmetidir. MySQL Community sürümünü kullanır. Azure MySQL sunucusu, hizmetin yönetim noktasıdır. Bu, şirket içi dağıtımlar için kullanılan aynı MySQL Server altyapısıdır. Motor, sunucu başına tek bir veritabanı veya kaynakları paylaşan sunucu başına birden çok veritabanı oluşturabilir. Yeni beceriler öğrenmek veya sanal makineleri yönetmek zorunda kalmadan aynı açık kaynaklı araçları kullanarak verileri yönetmeye devam edebilirsiniz.

### <a name="azure-database-for-mariadb"></a>MariaDB için Azure Veritabanı

[MariaDB](https://mariadb.com/) Sunucu, başka bir popüler açık kaynaklı veritabanı sunucusudur. Oracle, MySQL 'e sahip olan Sun Microsystems 'i satın aldığında MySQL 'in bir *çatalı* olarak oluşturulmuştur. Amaç, MariaDB 'nin açık kaynaklı olmasını sağlamaktır. MariaDB, MySQL 'in çatalından, veri ve tablo tanımları uyumludur ve istemci protokolleri, yapıları ve API 'Ler kapalı olur.

MariaDB güçlü bir topluluğa sahiptir ve birçok büyük kuruluş tarafından kullanılır. Oracle, MySQL 'i korumaya, geliştirmeye ve desteklemeye devam ederken, MariaDB Foundation, MariaDB 'yi yönetir ve ürün ve belgelere genel katkılara izin verir.

[MariaDB Için Azure veritabanı](https://azure.microsoft.com/services/mariadb/) , Azure bulutundaki bir hizmet olarak tam olarak yönetilen bir ilişkisel veritabanıdır. Hizmet, MariaDB Community Edition sunucu altyapısını temel alır. Tahmin edilebilir performans ve dinamik ölçeklenebilirlik sayesinde, görev açısından kritik iş yüklerini işleyebilir.

### <a name="azure-database-for-postgresql"></a>PostgreSQL için Azure Veritabanı

[PostgreSQL](https://www.postgresql.org/) , 30 yıldan daha fazla etkin geliştirme içeren açık kaynaklı bir ilişkisel veritabanıdır. PostgresSQL 'in güvenilirlik ve veri bütünlüğü açısından güçlü bir saygınlığı vardır. Özellikle karmaşık sorgular ve ağır yazmaları olan iş yükleri için zengin, SQL uyumlu ve MySQL 'den daha fazla performans kabul edilir. Apple, Red Hat ve Fujitsu gibi birçok büyük kuruluş, PostgreSQL kullanan ürünleri derlediniz.

[PostgreSQL Için Azure veritabanı](https://azure.microsoft.com/services/postgresql/) , açık kaynak Postgres veritabanı altyapısını temel alan, tam olarak yönetilen bir ilişkisel veritabanı hizmetidir. Hizmet C++, Java, Python, Node, C\#ve PHP gibi birçok geliştirme platformunu destekler. PostgreSQL veritabanlarını [komut satırı arabirimi](https://datamigration.microsoft.com/scenario/postgresql-to-azurepostgresql?step=1) aracını veya Azure Data Migration hizmetini kullanarak buna geçirebilirsiniz.

PostgreSQL için Azure veritabanı iki dağıtım seçeneği ile kullanılabilir:

- [Tek sunuculu](https://docs.microsoft.com/azure/postgresql/concepts-servers) dağıtım seçeneği, çok sayıda veritabanını dağıtabilmeniz için birden fazla veritabanı için merkezi bir yönetim noktasıdır. Fiyatlandırma, çekirdek ve depolama temelinde sunucu başına yapılandırılır.

- [Hyperscale (Citus) seçeneği](https://azure.microsoft.com/blog/get-high-performance-scaling-for-your-azure-database-workloads-with-hyperscale/) Citus veri teknolojisi tarafından desteklenir. Hızlı performans ve ölçek sağlamak için yüzlerce düğüm genelinde tek bir veritabanını *yatay olarak ölçeklendirerek* yüksek performans sağlar. Bu seçenek, altyapının bellekte daha fazla veri sığdırmasını, yüzlerce düğüm üzerinde paralel hale getirmek sorguları ve veri dizinini daha hızlı şekilde erişmesini sağlar.

## <a name="nosql-data-in-azure"></a>Azure 'da NoSQL verileri

Cosmos DB, Azure bulutu 'nda tamamen yönetilen, küresel olarak dağıtılmış bir NoSQL veritabanı hizmetidir. Ortak CA-Cola, Skype, ExxonMobil ve Liberty karşılıklı dahil olmak üzere dünyanın tamamında çok büyük şirketler tarafından benimsenmiştir.

Hizmetleriniz dünyanın her yerinden, yüksek kullanılabilirliğe veya esnek ölçeklenebilirlik için hızlı yanıt gerektiriyorsa, Cosmos DB harika bir seçimdir. Şekil 5-12 Cosmos DB gösterir.

![Cosmos DB genel bakış](./media/cosmos-db-overview.png)

**Şekil 5-12**: Cosmos DB genel bakış

Önceki şekil Cosmos DB ' de bulunan yerleşik buluta özgü yeteneklerin çoğunu gösterir. Bu bölümde, bunlara daha yakından bakacağız.

### <a name="global-support"></a>Küresel destek

Bulutta yerel uygulamalar genellikle küresel bir hedef kitleye sahiptir ve küresel ölçek gerektirir.

Cosmos veritabanlarını bölgeler arasında ya da dünyanın dört bir yanındaki dağıtabilir, kullanıcılarınıza veri yakınlarını, yanıt süresini geliştirir ve gecikmeyi azaltabilirsiniz. Hizmetlerinizi duraklatmadan veya yeniden dağıtmaya gerek kalmadan bir bölgeden veritabanı ekleyebilir veya kaldırabilirsiniz. Arka planda Cosmos DB, verileri, yapılandırılan bölgelerin her birine saydam olarak çoğaltır.

Cosmos DB, genel düzeyde [etkin/etkin](https://kemptechnologies.com/white-papers/unfog-confusion-active-passive-activeactive-load-balancing/) kümelendirmeyi destekler, böylece her türlü veritabanı bölgelerinizin *her ikisini de yazmayı ve*okumayı destekleyecek şekilde yapılandırmanıza olanak tanır.

[Çoklu ana](https://docs.microsoft.com/azure/cosmos-db/multi-master-benefits) protokol, Cosmos DB aşağıdaki işlevleri sağlayan önemli bir özelliktir:

- Sınırsız elastik yazma ve okuma ölçeklenebilirliği.

- dünyanın her yerindeki% 99,999 okuma ve yazma kullanılabilirliği.

- %99 ' luk yüzdede 10 milisaniyeden kısa bir süre içinde sunulan garantili okuma ve yazma işlemleri.

Cosmos DB çok girişli [API 'ler](https://docs.microsoft.com/azure/cosmos-db/distribute-data-globally)sayesinde, mikro hizmetiniz en yakın Azure bölgesini otomatik olarak algılar ve bu sunucuya istek gönderir. En yakın bölge, hiçbir yapılandırma değişikliği yapılmadan Cosmos DB tarafından tanımlanır. Bir bölge kullanılamaz hale gelirse, çoklu barındırma özelliği istekleri otomatik olarak en yakın kullanılabilir bölgeye yönlendirir.

### <a name="multi-model-support"></a>Çoklu model desteği

Tek parçalı uygulamalar buluta özgü bir mimariye yeniden geliştirmede, geliştirme ekiplerinin bazen açık kaynaklı, NoSQL veri depolarını geçirilmesi gerekir. Cosmos DB, bu NoSQL Veri depolarındaki yatırımınızı *çok modelli* veri platformuyla korumanıza yardımcı olabilir. Şekil 5-13 desteklenen NoSQL [Uyumluluk API 'lerini](https://www.wikiwand.com/en/Cosmos_DB)gösterir.

![Cosmos DB sağlayıcıları](./media/cosmos-db-providers.png)

**Şekil 5-13**: Cosmos DB sağlayıcılar

Geliştirme ekipleri, mevcut Mongo, Gremlin veya Cassandra veritabanlarını, veri veya koddaki en az değişiklikle birlikte Cosmos DB geçirebilir. Yeni uygulamalar için, geliştirme ekipleri açık kaynaklı seçenekler veya yerleşik SQL API modeli arasından seçim yapabilir.

> İçsel olarak, Cosmos verileri temel veri türlerinden oluşan basit bir struct formatında depolar. Her istek için, veritabanı altyapısı temel verileri seçtiğiniz model gösterimine çevirir.

Önceki şekilde 5-13, [tablo API'si](https://docs.microsoft.com/azure/cosmos-db/table-introduction) seçeneğine göz önünde. Bu API, Azure Tablo depolamanın bir gelişmidir. Her ikisi de aynı temel tablo modelini paylaşır, ancak Cosmos DB Tablo API'si Azure Storage API 'sinde bulunmayan Premium geliştirmeler ekler. Bu özellikler Şekil 5-4 ' de maliyetli değildir.

![Azure Tablo API'si](media/azure-table-api.png)

**Şekil 5-14**: Azure Tablo API'si sağlayıcıları

Azure Tablo Depolamayı kullanan mikro hizmetler Cosmos DB Tablo API'si kolayca geçirebilir. Kod değişikliği gerekli değildir.

### <a name="tunable-consistency"></a>Ayarlanabilir tutarlılık

*İlişkisel ve NoSQL* bölümünde daha önce, *veri tutarlılığı*konusunu tartıştık. Veri tutarlılığı, verilerinizin *bütünlüğünü* ifade eder. Dağıtılmış veriler içeren bulut Yerel hizmetleri, çoğaltmayı kullanır ve okuma tutarlılığı, kullanılabilirliği ve gecikme süresi arasında temel bir zorunluluğunu getirir olmalıdır.

Çoğu dağıtılmış veritabanı, geliştiricilerin iki tutarlılık modeli arasından seçim yapmasına imkan tanır: güçlü tutarlılık ve nihai tutarlılık. *Güçlü tutarlılık* , veri programlamasına yönelik altın standarttır. Sistemin, bir güncelleştirmenin tüm veritabanı kopyalarında çoğaltılmasını bekleyen gecikme süresi olması beklense bile, bir sorgunun en güncel verileri her zaman döndürmesini güvence altına alır. *Nihai tutarlılık* için yapılandırılmış bir veritabanı, veri en güncel kopya olmasa bile, verileri hemen geri döndürmeyecektir. İkinci seçenek daha yüksek kullanılabilirlik, daha fazla ölçek ve daha fazla performans sunar.

Azure Cosmos DB Şekil 5-15 ' de gösterilen beş iyi tanımlanmış [tutarlılık modeli](https://docs.microsoft.com/azure/cosmos-db/consistency-levels) sunar.

![Cosmos DB tutarlılık grafiği](./media/cosmos-consistency-level-graph.png)

**Şekil 5-15**: tutarlılık düzeylerini Cosmos DB

 Bu seçenekler tutarlılık, kullanılabilirlik ve verilerinizin performansı için kesin seçenekler ve ayrıntılı bir denge yapmanızı sağlar. Şekil 5-16 her bir düzeyi açıklamaktadır.

![Tutarlılık düzeylerini Cosmos DB](./media/cosmos-db-consistency-levels.png)

**Şekil 5-16**: Cosmos DB tutarlılık düzeyi açıklaması

[9-Ball ' ın arkasında elde edilen makale: Cosmos DB tutarlılık seviyeleri](https://blog.jeremylikness.com/blog/2018-03-23_getting-behind-the-9ball-cosmosdb-consistency-levels/)Microsoft bulut geliştirici Danışmanı, beş modelin mükemmel bir açıklamasını sunmaktadır.

### <a name="partitioning"></a>Bölümleme

Azure Cosmos DB, bir veritabanını, bulut Yerel hizmetlerinizin performans ihtiyaçlarını karşılayacak şekilde ölçeklendirmek için otomatik [bölümlendirme](https://docs.microsoft.com/azure/cosmos-db/partitioning-overview) .

Veritabanları, kapsayıcılar ve öğeler oluşturarak verileri Cosmos DB verileri yönetebilirsiniz.

Kapsayıcılar bir Cosmos DB veritabanında canlı ve öğelerin şema belirsiz gruplandırmasını temsil eder. Öğe, kapsayıcıya eklediğiniz veri. Bunlar belge, satır, düğüm veya kenar olarak gösterilir. Bir kapsayıcıya eklenen tüm öğeler otomatik olarak dizinlenir.

Kapsayıcıyı bölümlemek için öğeler mantıksal bölümler adlı farklı alt kümelere bölünür. Mantıksal bölümler, bir kapsayıcıdaki her öğeyle ilişkili bir bölüm anahtarının değerine göre doldurulur. Şekil 5-18, her biri bir bölüm anahtarı değerini temel alan mantıksal bölüme sahip iki kapsayıcıyı gösterir.

![Cosmos DB bölümlendirme mekanizması](./media/cosmos-db-partitioning.png)

**Şekil 5-18**: Cosmos DB bölümlendirme mekanizması

Önceki şekilde, her öğenin ' City ' veya ' Havaalanı ' bölüm anahtarını nasıl içerdiğini göz önünde bulun. Anahtar öğenin mantıksal bölümünü belirler. Şehir koduna sahip öğeler, sol taraftaki kapsayıcıya ve Havaalanı koduna sahip öğelere sağdaki kapsayıcıya atanır. Bölüm anahtarı değerini ID değeri ile birleştirmek, öğeyi benzersiz şekilde tanımlayan bir öğenin dizinini oluşturur.

Dahili olarak, Cosmos DB kapsayıcının ölçeklenebilirlik ve performans ihtiyaçlarını karşılamak için fiziksel bölümlerin [mantıksal bölümlerinin](https://docs.microsoft.com/azure/cosmos-db/partition-data) yerleşimini otomatik olarak yönetir. Uygulama işleme ve Depolama gereksinimlerinin artması halinde, Azure Cosmos DB mantıksal bölümleri daha fazla sayıda sunucuda yeniden dağıtır. Yeniden dağıtım işlemleri Cosmos DB tarafından yönetilir ve kesinti veya kesinti olmadan çağrılır.

## <a name="newsql-databases"></a>NewSQL veritabanları

*Newsql* , bir ilişkisel veritabanının ACID garantisi ile NoSQL 'in dağıtılmış ölçeklenebilirliğini birleştiren, gelişmekte olan bir veritabanı teknolojisidir. NewSQL veritabanları, tam işlem desteği ve ACID uyumluluğu sayesinde, yüksek hacimlerde verileri, dağıtılmış ortamlar arasında işlemesi gereken iş sistemleri için önemlidir. NoSQL veritabanı çok büyük ölçeklenebilirlik sağlayabilme olanağı sağlarken, veri tutarlılığını garanti etmez. Tutarsız verilerden oluşan aralıklı sorunlar, geliştirme ekibine bir yük getirebilir. Geliştiricilerin, tutarsız verilerden kaynaklanan sorunları yönetmesi için mikro hizmet koduna karşı korumalar oluşturulması gerekir.

Cloud Native Computing Foundation (CNCF), çeşitli NewSQL veritabanı projelerini sunar.

| Project | Özellikler |
| :-------- | :-------- |
| Cockroach DB |Küresel olarak ölçeklenen, bir ACID uyumlu ilişkisel veritabanı. Bir kümeye yeni bir düğüm ekleyin ve CockroachDB, verilerin örnekleri ve coğrafi bölgelerde dengelenmesi için gereken bir değer sağlar. Güvenilirliği sağlamak için çoğaltmaları oluşturur, yönetir ve dağıtır. Açık kaynak ve ücretsiz kullanılabilir.  |
| TiDB | Karma Işlem ve analitik Işleme (HTAP) iş yüklerini destekleyen açık kaynaklı bir veritabanı. MySQL uyumludur ve yatay ölçeklenebilirlik, güçlü tutarlılık ve yüksek kullanılabilirlik özellikleri sunar.  TiDB bir MySQL sunucusu gibi davranır. Uygulamanızda kapsamlı kod değişikliklerine gerek duymadan mevcut MySQL istemci kitaplıklarını kullanmaya devam edebilirsiniz. |
| Yugabrivtedb | Açık kaynaklı, yüksek performanslı, dağıtılmış SQL veritabanı. Düşük sorgu gecikmesini, esnekliği ve hatalara karşı genel veri dağıtımını destekler. Yugabyıtedb PostgressSQL ile uyumludur ve genişleme RDBMS ve İnternet ölçeğinde OLTP iş yüklerini yönetir. Ürün ayrıca NoSQL 'i de destekler ve Cassandra ile uyumludur. |
|Vitess | Vitess, büyük MySQL örnekleri kümelerini dağıtmaya, ölçeklendirmeye ve yönetmeye yönelik bir veritabanı çözümüdür. Bu, ortak veya özel bir bulut mimarisinde çalıştırılabilir. Birçok önemli MySQL özelliğini birleştirir ve genişletir ve hem dikey hem de yatay parçalama desteği sunar. YouTube tarafından oluşturulan Vitess, 2011 tarihinden itibaren tüm YouTube veritabanı trafiğini görüyor. |

Önceki şekildeki açık kaynaklı projeler, bulut Yerel Bilgi Işlem altyapısı 'nda bulunabilir. Tekliflerinden üçü, .NET Core desteği dahil olmak üzere tam veritabanı ürünlerdir. Diğer, Vitess, büyük MySQL örnekleri kümelerini yatay olarak ölçeklendirilen bir veritabanı kümeleme sistemidir.

NewSQL veritabanları için önemli bir tasarım hedefi, platformun dayanıklılık ve ölçeklenebilirlik avantajlarından yararlanarak Kubernetes 'te yerel olarak çalışacaktır.

NewSQL veritabanları, temel alınan sanal makinelerin yeniden başlatılması veya bir süre bildirimde yeniden zamanlanmasında, kısa ömürlü bulut ortamlarında Misyonumuz üzere tasarlanmıştır. Veritabanları, veri kaybı veya kapalı kalma süresi olmadan düğüm arızalarını sürdürmesini sağlayacak şekilde tasarlanmıştır. Örneğin, CockroachDB, bir kümedeki düğümlerde bulunan verilerin üç tutarlı çoğaltmasını tutarak makine kaybını devam edebilir.

Kubernetes, bir istemcinin tek bir DNS girdisinden özdeş bir NewSQL veritabanı işlemi grubuna yönelik bir grup kullanmasına izin vermek için bir *hizmet yapısı* kullanır. Veritabanı örneklerini ilişkilendirildiği hizmetin adresinden ayırarak, var olan uygulama örneklerini kesintiye uğratmadan ölçeklendirebiliriz. Belirli bir zamanda herhangi bir hizmete bir istek gönderilmesi her zaman aynı sonucu verir.

Bu senaryoda, tüm veritabanı örnekleri eşittir. Birincil veya ikincil ilişki yok. CockroachDB içinde *konsensus çoğaltması* gibi teknikler, herhangi bir veritabanı düğümünün herhangi bir isteği işlemesini sağlar. Yük dengeli bir istek alan düğümde yerel olarak gereken veriler varsa, hemen yanıt verir. Aksi takdirde, düğüm bir ağ geçidi haline gelir ve doğru yanıtı almak için isteği uygun düğümlere iletir. İstemcinin perspektifinden, her veritabanı düğümü aynıdır: tek makineli bir sistemin tutarlılık garantisi olan tek bir *mantıksal* veritabanı olarak görünürler ve bu da arka planda çalışan onlarca veya hatta yüzlerce düğüm olmasına rağmen.

NewSQL veritabanlarının arkasındaki mekanizması ayrıntılı bir bakış için bkz. [Dash: Kubernetes-Native veritabanları makalesinin dört özelliği](https://thenewstack.io/dash-four-properties-of-kubernetes-native-databases/) .

## <a name="data-migration-to-the-cloud"></a>Buluta veri geçişi

Daha fazla zaman alan görevlerden biri verileri bir veri platformundan diğerine geçirmektedir. [Azure veri geçiş hizmeti](https://azure.microsoft.com/services/database-migration/) , bu çabalara yardımcı olabilir. Birçok dış veritabanı kaynağından verileri en az kapalı kalma süresiyle Azure veri platformları 'na geçirebilir. Hedef platformlar aşağıdaki hizmetleri içerir:

- Azure SQL Veritabanı
- MySQL için Azure Veritabanı
- MariaDB için Azure Veritabanı
- PostgreSQL için Azure Veritabanı
- CosmosDB
  
Hizmet, her ikisi de küçük veya büyük bir geçiş yürütmek için gereken değişikliklere kılavuzluk eden öneriler sağlar.

>[!div class="step-by-step"]
>[Önceki](distributed-data.md)
>[İleri](azure-caching.md)
