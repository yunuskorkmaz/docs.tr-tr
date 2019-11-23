---
title: Azure 'da veri depolama
description: Azure için Cloud Native .NET uygulamaları tasarlama | Azure 'da veri depolama
ms.date: 06/30/2019
ms.openlocfilehash: 1a86cecf005c6dbdfda5cf4cacfafaad4711c076
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73087763"
---
# <a name="data-storage-in-azure"></a>Azure 'da veri depolama

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Bu kitapta gördüğümüz gibi, bulut uygulamaların tasarlanmasının, dağıtıldığı ve yönetilme şeklini değiştiriyor. Buluta taşırken, verilerinizi nasıl taşıyacağınız önemli bir sorudır. Neyse ki Azure bulutu birçok seçenek sunar.

Yalnızca bir Azure sanal makinesini temin etmeniz ve istediğiniz veritabanını yükleyebilirsiniz. Bu, [hizmet olarak altyapı (IaaS)](https://www.techopedia.com/definition/141/infrastructure-as-a-service-iaas)olarak bilinir. Bu yaklaşım, şirket içi bir veritabanının buluta taşınmasını basitleştirir, ancak sanal makineyi ve veritabanını yönetme yükünü size geçirir.

Bunun yerine, tam olarak yönetilen [bir hizmet olarak veritabanı (DBaaS)](https://www.stratoscale.com/blog/dbaas/what-is-database-as-a-service/) daha iyi bir seçenektir. Barındırma, bakım ve lisanslama Microsoft tarafından yönetilirken birçok yerleşik özelliği alırsınız. Azure, her biri belirli avantajları içeren farklı, tam olarak yönetilen veri depolama seçenekleri türlerine sahiptir. Hepsi, tam zamanında kapasiteyi ve kullandıkça öde modelini destekler.

Daha sonra Azure 'da bulunan DBaaS seçeneklerine bakacağız. Microsoft 'un, açık kaynaklı ve NoSQL veritabanları için yönetilen destek sunan ve etkin bir üye olarak çeşitli açık kaynaklı tabanlara anahtar katkıları sağlayan, Azure 'u bir "açık platform" olarak tutma konusunda nasıl sorun olduğunu göreceksiniz.

## <a name="azure-sql-database"></a>Azure SQL Database

[Azure SQL veritabanı](https://docs.microsoft.com/azure/sql-database/) , Microsoft SQL Server veritabanı altyapısını temel alan, özellikle zengin, genel amaçlı bir ilişkisel hizmet olarak veritabanı (DBaaS). Microsoft tarafından tam olarak yönetilir ve yüksek performanslı, güvenilir ve güvenli bir bulut veritabanıdır. Hizmet, SQL Server 'ın şirket içi sürümünde bulunan özelliklerin birçoğunu paylaşır.

Dakikalar içinde bir SQL veritabanı sunucusu ve veritabanı sağlayabilirsiniz. Uygulamanız için talepler, bir veya daha fazla müşteriden milyonlarca kullanıcıya büyüdükçe, Azure SQL veritabanı en az kapalı kalma süresiyle birlikte hareket halindeyken ölçeği ölçeklendirir. CPU gücü, bellek, GÇ işleme ve veritabanlarınıza ayrılan depolama dahil olmak üzere kaynakları dinamik olarak ekleyebilir veya kaldırabilirsiniz.

Şekil 5-12, Azure SQL veritabanı için dağıtım seçeneklerini gösterir.

![Azure SQL dağıtım seçenekleri](./media/azure-sql-database-deployment-options.png)

**Şekil 5-12**. Azure SQL dağıtım seçenekleri

SQL veritabanı dağıtımı sırasında önceki şekildeki alternatifleri göz önünde bulun:

- [Tek bir veritabanı](https://docs.microsoft.com/azure/sql-database/sql-database-single-database) , bir [SQL veritabanı sunucusu](https://docs.microsoft.com/azure/sql-database/sql-database-servers)tarafından yönetilen kendi kaynak kümesiyle . Tek bir veritabanı, şirket içi SQL Server dağıtımında [içerilen bir veritabanı](https://docs.microsoft.com/sql/relational-databases/databases/contained-databases) benzerdir.

- Bir SQL veritabanları koleksiyonunun tek bir SQL veritabanı sunucusunu ayarlanan fiyata paylaştığı [elastik bir havuz](https://docs.microsoft.com/azure/sql-database/sql-database-elastic-pool) . Tek veritabanları, bir grup veritabanı için fiyat performansını iyileştirmek için gerektiğinde elastik bir havuzun içine ve dışına taşınabilir.

- Bir sistem ve kullanıcı veritabanlarının koleksiyonu olan [yönetilen bir örnek](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance) , şirket içi SQL Server %100 ' dan fazla uyumluluk sağlar. Bu seçenek, 35 TB 'a kadar daha büyük veritabanlarını destekler ve daha iyi yalıtım için bir [Azure sanal ağına](https://docs.microsoft.com/azure/virtual-network/virtual-networks-overview) yerleştirilir.

Azure SQL veritabanı, Kullanıcı katılımı olmadan yükseltme, düzeltme eki uygulama ve izleme işlemlerini yürüten, tam olarak yönetilen [bir hizmet olarak platform (PaaS) veritabanı altyapısıdır](https://docs.microsoft.com/azure/sql-database/sql-database-paas) . Her zaman SQL Server veritabanı altyapısının ve düzeltme eki uygulanan işletim sisteminin en son kararlı sürümünü çalıştırır ve% 99,99 kullanılabilirliği garanti eder. Bir özellik, [etkin coğrafi çoğaltma](https://docs.microsoft.com/azure/sql-database/sql-database-active-geo-replication), aynı veya farklı bir Azure veri merkezinde okunabilir ikincil veritabanları oluşturmanızı sağlar. Hata sonrasında, ikincil veritabanına yük devretme başlatılabilir. Bu noktada, diğer ikincil öğeler yeni birincili otomatik olarak bağlanır. Aynı ya da farklı bölgelerde dört adede kadar ikincil çoğaltma desteklenir ve bu ikincil öğeler salt okuma erişim sorguları için de kullanılabilir.

Azure SQL veritabanı, performansı en üst düzeye çıkarmanıza ve işlem maliyetlerini azaltmanıza yardımcı olabilecek [yerleşik izleme ve akıllı ayarlama](https://docs.microsoft.com/azure/sql-database/sql-database-monitoring-tuning-index) özellikleri içerir. Örneğin, [otomatik ayarlama](https://docs.microsoft.com/azure/sql-database/sql-database-automatic-tuning) özelliği AI ve makine öğrenimine göre sürekli performans ayarlaması sağlar. Hizmet, çalışan iş yüklerinizde öğrenir ve ayarlama önerilerini uygulayabilir. Daha uzun bir Azure SQL veritabanı otomatik ayarlama etkinken çalışır, daha iyi bir seçenektir.

[Azure SQL veritabanı sunucusuz](https://docs.microsoft.com/azure/sql-database/sql-database-serverless) (Bu kitabın yazılması sırasında önizleme için kullanılabilir), iş yükü talebine göre otomatik olarak ölçeklenen tek veritabanlarına yönelik bir işlem katmandır ve saniye başına kullanılan işlem miktarına göre faturalandırılır. Sunucusuz işlem katmanı Ayrıca, etkin olmayan dönemler sırasında veritabanlarını otomatik olarak duraklatarak yalnızca depolama ücretleri faturalandırılır. Etkinlik geri döndüğünde otomatik olarak devam eder.

Son olarak, yeni [Azure SQL veritabanı hiper ölçek](https://azure.microsoft.com/services/sql-database/) fiyatlandırma katmanı vardır. Bu, yüksek düzeyde ölçeklenebilir bir depolama mimarisine sahiptir ve veritabanınızın gerektiği şekilde büyümesini sağlar ve depolama kaynaklarının önceden sağlanması gereksinimini ortadan kaldırır. İşlem ve depolama kaynaklarını bağımsız olarak ölçeklendirebilirsiniz, her iş yükü için performansı iyileştirme esnekliği sağlayabilirsiniz. Azure SQL veritabanı hiper ölçek, 100 TB 'a kadar depolama özellikli [OLTP](https://en.wikipedia.org/wiki/Online_transaction_processing) işleme ve yüksek performanslı analitik iş yükleri için iyileştirilmiştir.  Okuma yoğunluklu iş yükleri sayesinde hiper ölçek, okuma iş yüklerinin yükünü kaldırma için gerektiğinde ek okuma çoğaltmaları sağlayarak hızlı genişleme sağlar.

Azure, geleneksel Microsoft SQL Server yığınına ek olarak, çeşitli popüler açık kaynaklı veritabanlarının yönetilen sürümlerine de sahiptir.

## <a name="azure-database-for-mysql"></a>MySQL için Azure Veritabanı

[MySQL](https://en.wikipedia.org/wiki/MySQL) , [Açık kaynaklı](https://en.wikipedia.org/wiki/Open-source_software)bir [ilişkisel veritabanıdır](https://en.wikipedia.org/wiki/Relational_database_management_system). Bu, [lamba yazılım yığınındaki](https://en.wikipedia.org/wiki/LAMP_(software_bundle)) bir bileşendir ve Facebook, Twitter ve YouTube dahil olmak üzere çok büyük kuruluşlar tarafından kullanılır. Community sürümü ücretsiz olarak kullanılabilir ve Enterprise Edition için bir lisans satın alma işlemi gerekir. Başlangıçta 1995 ' de oluşturulan ürün, ' de 2010 Oracle tarafından edinilen Sun Microsystems tarafından 2008 ' de satın alınmış.

[MySQL Için Azure veritabanı](https://azure.microsoft.com/services/mysql/) , açık kaynak MySQL sunucu altyapısını temel alan, tam olarak yönetilen, kurumsal özellikli bir ilişkisel veritabanı hizmetidir. MySQL Community Edition uygulaması, ek bir ücret ödemeden aşağıdaki PaaS özelliklerini içerir:

- Yerleşik [yüksek kullanılabilirlik](https://docs.microsoft.com/azure/mysql/concepts-high-availability).

- Kapsamlı [Kullandıkça Öde fiyatlandırması](https://docs.microsoft.com/azure/mysql/concepts-pricing-tiers)kullanılarak öngörülebilir performans.

- Saniyeler içinde gereken şekilde [ölçeklendirin](https://docs.microsoft.com/azure/mysql/concepts-high-availability) .

- REST ve hareket halindeyken hassas verileri korumaya yönelik güvenli hale getirilir.

- [Otomatik yedeklemeler](https://docs.microsoft.com/azure/mysql/concepts-backup) ve [zaman içindeki süre-geri yükleme](https://docs.microsoft.com/azure/mysql/concepts-backup) 35 güne kadar.

- Kurumsal düzeyde güvenlik ve uyumluluk.

Bu yerleşik PaaS özellikleri, veri merkezlerinde yüzlerce "tackatik" (stratejik) veritabanlarına sahip olan, ancak düzeltme eki uygulama, yedekleme, güvenlik ve performans izleme işlemleri gerçekleştirmek için kaynaklara sahip olmayan kuruluşlar için önemlidir.

Ayrıca, [Azure veri geçiş hizmeti](https://azure.microsoft.com/services/database-migration/) , verileri birden çok veritabanı kaynağından Azure veri platformlarına en az kapalı kalma süresiyle geçirebilir. Hizmet, değerlendirme raporları oluşturur ve bir geçiş gerçekleştirmek için gereken değişiklikler boyunca hem küçük hem de büyük olmak üzere size rehberlik sağlayan öneriler sağlar.

Yönetilen [Azure MySQL sunucusu](https://docs.microsoft.com/azure/mysql/concepts-servers) , hizmet için merkezi yönetim noktasıdır. Bu, şirket içi dağıtımlar için kullanılan aynı MySQL Server altyapısıdır. Bununla birlikte, kaynakları paylaşmak için tüm kaynakları kullanmak veya sunucu başına birden çok veritabanı oluşturmak üzere sunucu başına tek bir veritabanı oluşturabilirsiniz. Takımınız, yeni beceriler öğrenmek veya sanal makineleri ve altyapıyı yönetmek zorunda kalmadan açık kaynaklı araçlar ve tercih ettiğiniz platformla uygulama geliştirmeye devam edebilir.

## <a name="azure-database-for-mariadb"></a>MariaDB için Azure veritabanı

[MariaDB](https://mariadb.com/) Sunucu, başka bir popüler açık kaynaklı veritabanı sunucusudur. Bu, MySQL 'in kendine ait olan Sun Microsystems 'e sahip olduğu zaman, MySQL 'in özgün geliştiriciler tarafından MySQL 'in bir çatalı olarak oluşturulmuştur. Amaç, MariaDB 'nin açık kaynaklı olmasını sağlamaktır.

MariaDB, [MySQL 'in çatalından](https://blog.panoply.io/a-comparative-vmariadb-vs-mysql), veri ve tablo tanımları uyumludur ve istemci protokolleri, yapıları ve API 'ler kapalı olur. MySQL veri bağlayıcıları, hiçbir değişiklik yapmadan MariaDB 'yi işler.

MariaDB için güçlü bir aşağıdakiler vardır ve birçok büyük kuruluş tarafından kullanılır. Oracle, MySQL 'i geliştirmeye, geliştirmeye ve desteklemeye devam ederken, MariaDB,, ürüne ve belgelere genel katkılara izin veren MariaDB Foundation tarafından yönetilir.

[MariaDB Için Azure veritabanı](https://azure.microsoft.com/services/mariadb/) , Azure bulutundaki bir hizmet olarak tam olarak yönetilen bir veritabanıdır.  [MariaDB Community Edition](https://mariadb.org/download/) sunucu altyapısını temel alır. Tahmin edilebilir performans ve dinamik ölçeklenebilirlik sayesinde, görev açısından kritik iş yüklerini işleyebilir. Diğer Azure veritabanı platformlarına benzer şekilde, ek bir ücret ödemeden birçok hizmet olarak platform özelliği de vardır:

- Yerleşik [yüksek kullanılabilirlik](https://docs.microsoft.com/azure/mariadb/concepts-high-availability).

- Kapsamlı [Kullandıkça Öde fiyatlandırması](https://docs.microsoft.com/azure/mariadb/concepts-pricing-tiers)kullanılarak öngörülebilir performans.

- Saniyeler içinde gerektiği şekilde [ölçeklendirin](https://docs.microsoft.com/azure/mariadb/concepts-high-availability) .

- REST ve hareket halindeyken hassas verilerin güvenli koruması.

- [Otomatik yedeklemeler](https://docs.microsoft.com/azure/mariadb/concepts-backup) ve [zaman içindeki süre-geri yükleme](https://docs.microsoft.com/azure/mariadb/concepts-backup) 35 güne kadar.

- Kurumsal düzeyde güvenlik ve uyumluluk.

## <a name="azure-database-for-postgresql"></a>PostgreSQL için Azure Veritabanı

[PostgreSQL](https://www.postgresql.org/) , 30 yıldan fazla etkin geliştirmeyi içeren, popüler, açık kaynaklı bir ilişkisel veritabanıdır. Bu, genel amaçlı ve nesne ilişkisel veritabanı yönetim sistemidir. Lisanslama, "özgürlük" olarak kabul edilir ve ürünün herhangi bir biçimde kullanımı, değiştirilmesi ve dağıtılması ücretsizdir. Apple, Red Hat ve Fujitsu gibi birçok büyük kuruluş, PostgreSQL kullanan ürünleri derlediniz.

[PostgreSQL Için Azure veritabanı](https://azure.microsoft.com/services/postgresql/) , açık kaynak Postgres veritabanı altyapısını temel alan, tam olarak yönetilen bir ilişkisel veritabanı hizmetidir. Tahmin edilebilir performans, güvenlik, yüksek kullanılabilirlik ve dinamik ölçeklenebilirlik ile görev açısından kritik iş yüklerini işleyebilir. Java, Python, Node, C\#ve PHP dahil C++olmak üzere çeşitli açık kaynaklı çerçeveleri ve dilleri destekler. PostgreSQL veritabanlarının bir komut satırı arabirimi veya [Azure veri geçiş hizmeti](https://azure.microsoft.com/services/database-migration/)aracılığıyla [geçirilmesini](https://datamigration.microsoft.com/scenario/postgresql-to-azurepostgresql?step=1) mümkün kılar.

Hizmet, benzersiz veritabanı desenlerinizi etkileyen [yerleşik zeka](https://docs.microsoft.com/azure/postgresql/concepts-monitoring) Içerir ve PostgreSQL veritabanınızın performansını en üst düzeye çıkarmanıza yardımcı olacak özelleştirilmiş öneriler ve öngörüler sağlar. [Gelişmiş tehdit koruması](https://docs.microsoft.com/azure/postgresql/concepts-data-access-and-security-threat-protection) , veritabanınızı saatin etrafında izler ve olası kötü amaçlı etkinlikleri algılar, böylece hemen müdahale edebilmeniz için algılama sonrasında sizi uyarır.

PostgreSQL için Azure veritabanı iki dağıtım seçeneği olarak sunulmaktadır: tek sunucu ve hiper ölçek (Citus), bu kitabın yazılması sırasında önizleme için kullanılabilir

- [Tek sunuculu](https://docs.microsoft.com/azure/postgresql/concepts-servers) dağıtım seçeneği, birden çok veritabanı için merkezi bir yönetim noktasıdır. Şirket içi dağıtımlar için aynı PostgreSQL sunucu altyapısı vardır. Bununla birlikte, tüm kaynakları kullanmak veya kaynakları paylaşmak için birden çok veritabanı oluşturmak üzere sunucu başına tek bir veritabanı oluşturabilirsiniz. Fiyatlandırma, çekirdek ve depolama temelinde sunucu başına yapılandırılır.

- [Hyperscale (Citus) seçeneği](https://azure.microsoft.com/blog/get-high-performance-scaling-for-your-azure-database-workloads-with-hyperscale/)  [Citus Data](https://www.citusdata.com/) teknolojisi tarafından desteklenir. Tek bir veritabanını yüzlerce düğüm genelinde yatay olarak ölçeklendirerek yüksek performanslı ölçeklendirmeyi etkinleştirerek, daha hızlı performans ve ölçek sunun. Bu seçenek, altyapının bellekte daha fazla veri sığdırmasını, yüzlerce düğüm üzerinde paralel hale getirmek sorguları ve veri dizinini daha hızlı şekilde erişmesini sağlar. Hiperscale özelliği, PostgreSQL için en son yeniliklerle, sürümlerle ve araçlarla uyumludur, bu sayede mevcut PostgreSQL uzmanlığınızdan yararlanabilirsiniz.

## <a name="cosmos-db"></a>Cosmos DB

Azure Cosmos DB, düşük gecikme süresi, esnek ölçeklenebilirlik, yönetilen veri tutarlılığı ve yüksek kullanılabilirlik sağlamak için tasarlanan, tam olarak yönetilen, küresel olarak dağıtılmış bir NoSQL veritabanı hizmetidir. Kısacası, uygulamanızın dünyanın herhangi bir yerinden garantili hızlı yanıt süresine ihtiyacı varsa, her zaman çevrimiçi olması gerekiyorsa ve verimlilik ve depolama için sınırsız ve esnek ölçeklenebilirlik ihtiyacı varsa Cosmos DB harika bir seçimdir. Şekil 5-13 Cosmos DB üst düzey bir genel bakış gösterir.

![Cosmos DB genel bakış](./media/cosmos-db-overview.png)

**Şekil 5-13**: Cosmos DB genel bakış

Şekil 5-13 ' de, çok sayıda yerleşik bulut Yerel özelliği olan sağlam ve çok yönlü bir veritabanı hizmeti nasıl Cosmos DB. Bu bölümde, bunlara daha yakından bakacağız.

### <a name="global-support"></a>Küresel destek

Cosmos veritabanlarını dünya genelinde tüm Azure bölgelerinde küresel olarak dağıtabilir, kullanıcılarınıza yakın veri ekleyebilir, yanıt süresini geliştirir ve gecikmeyi azaltabilirsiniz. Uygulamanızı duraklatmadan veya yeniden dağıtmaya gerek kalmadan bir bölgeden veritabanı ekleyebilir veya kaldırabilirsiniz. Arka planda Cosmos DB, verileri tüm yapılandırılmış bölgelere şeffaf olarak çoğaltır.

Cosmos DB, genel düzeyde [etkin/etkin](https://kemptechnologies.com/white-papers/unfog-confusion-active-passive-activeactive-load-balancing/) kümelendirmeyi destekler, böylece her türlü veya tüm veritabanı bölgelerini hem yazma hem de okumayı destekleyecek şekilde yapılandırmanıza olanak tanır.

Cosmos DB ' deki [çoklu ana](https://docs.microsoft.com/azure/cosmos-db/how-to-multi-master) protokol özelliği aşağıdaki işlevleri sunar:

- Sınırsız elastik yazma ve okuma ölçeklenebilirliği.

- dünyanın her yerindeki% 99,999 okuma ve yazma kullanılabilirliği.

- %99 ' luk yüzdede 10 milisaniyeden kısa bir süre içinde sunulan garantili okuma ve yazma işlemleri.

Dahili olarak, Cosmos DB tutarlılık düzeyi garantilerini ve mali olarak desteklenen hizmet düzeyi sözleşmelerini içeren bölgeler arasında veri çoğaltmasını işler.

Cosmos DB çok girişli [API 'ler](https://docs.microsoft.com/azure/cosmos-db/distribute-data-globally)sayesinde, uygulamanız en yakın Azure bölgesinden otomatik olarak haberdar olabilir ve istek gönderebilir. En yakın bölge, hiçbir yapılandırma değişikliği yapılmadan Cosmos DB tarafından tanımlanır. Bir bölge kullanılamaz hale gelirse, Cosmos DB otomatik yük devretmeyi destekler ve çoklu barındırma özelliği isteğinizi otomatik olarak en yakın kullanılabilir bölgeye yönlendirir.

### <a name="multi-model-support"></a>Çoklu model desteği

Cosmos DB, belgeler, anahtar-değer çiftleri, geniş sütun ve grafik gösterimleri dahil olmak üzere birçok desteklenen NoSQL modeli kullanarak verilerinizle etkileşim kurmanıza olanak sağlayan *çok modelli bir veri platformudur* . Dahili olarak, veriler dizeler, bota ve sayılar dahil olmak üzere temel veri türlerinden oluşan basit bir [Yapı](https://docs.microsoft.com/dotnet/csharp/programming-guide/classes-and-structs/using-structs) biçiminde depolanır. Her istek için veritabanı altyapısı, verileri seçtiğiniz model gösterimine çevirir. SQL tabanlı Cosmos DB özel bir API veya şekil 5-14 ' de gösterilen herhangi bir [Uyumluluk API](https://www.wikiwand.com/en/Cosmos_DB) 'sinden seçim yapabilirsiniz.

![Cosmos DB sağlayıcıları](./media/cosmos-db-providers.png)

**Şekil 5-14**: Cosmos DB sağlayıcılar

Şekil 5-14 Cosmos DB [Tablo Depolamayı](https://azure.microsoft.com/services/storage/tables/)nasıl desteklediğine göz önünde bulun. Hem Cosmos DB hem de [Azure Tablo depolama](https://docs.microsoft.com/azure/cosmos-db/table-storage-overview) , aynı temel tablo modelini paylaşır ve aynı tablo işlemlerini çok sayıda kullanıma sunar. Ancak, [Cosmos DB tablo API'si](https://docs.microsoft.com/azure/cosmos-db/table-introduction) Azure Storage API 'sinde bulunmayan birçok Premium geliştirme sağlar. Bu özellikler Şekil 5-15 ' de maliyetli değildir.

![Azure Tablo API'si](./media/azure-table-api.png)

**Şekil 5-15**: Azure Tablo API'si

Azure Tablo depolaması için yazılmış uygulamalar, hiçbir kod değişikliği olmadan Tablo API'si kullanarak Azure Cosmos DB geçirebilir.

[Brownfield](https://en.wikipedia.org/wiki/Brownfield_(software_development)) uygulama senaryolarında, geliştirme ekipleri mevcut Mongo, Gremlin veya Cassandra veritabanlarını, mevcut verilerde veya uygulama kodunda en az değişiklikle Cosmos DB içine geçirebilir. Tek [alan](https://en.wikipedia.org/wiki/Greenfield_project) senaryolarında, geliştirme ekipleri MongoDB, Cassandra ve Gremlin platformları için tam olarak desteklenen açık kaynak seçenekleri de dahil olmak üzere gereksinimlerini ve tercihlerini en iyi karşılayan veri modelini seçebilirler.

### <a name="consistency-models"></a>Tutarlılık modeli

*İlişkisel ve NoSQL* bölümünde daha önce, verilerinizin bütünlüğünü ifade eden bir terim olan *veri tutarlılığı*konusunu tartıştık. Yüksek kullanılabilirlik, düşük gecikme süresi veya her ikisi için çoğaltmaya dayanan dağıtılmış veritabanları, okuma tutarlılığı, kullanılabilirliği ve gecikme süresi arasında temel bir zorunluluğunu getirir olmalıdır.

Çoğu dağıtılmış veritabanı, geliştiricilerin iki tutarlılık modeli arasından seçim yapmasına imkan tanır: [güçlü tutarlılık](https://en.wikipedia.org/wiki/Strong_consistency) ve [nihai tutarlılık](https://en.wikipedia.org/wiki/Eventual_consistency). *Güçlü tutarlılık* , veri programlamasına yönelik altın standarttır. Sistemin bir güncelleştirmenin tüm veritabanı kopyalarında çoğaltılmasını bekleyen gecikme süresi olması beklense bile, bir sorgu sonucunun her zaman en güncel verileri döndürmesini güvence altına alır. Diğer taraftan, son *tutarlılık* için yapılandırılmış bir sistem, veriler en güncel kopya olmasa bile hemen verileri döndürür. Bu seçenek daha yüksek kullanılabilirlik, daha fazla ölçek ve daha fazla performans sunar.

Azure Cosmos DB Şekil 5-16 ' de gösterilen [beş iyi tanımlanmış tutarlılık modeli](https://docs.microsoft.com/azure/cosmos-db/consistency-levels) yelpazesi sunar. Bu seçenekler, uygulamanızın ihtiyaçlarına bağlı olarak kullanılabilirlik ve performans açısından kesin seçimler ve ayrıntılı bir denge yapmanızı sağlar. Bu modeller iyi tanımlanmış, sezgisel ve hizmet düzeyi sözleşmeleri (SLA 'Lar) tarafından desteklenir.

![Tutarlılık düzeylerini Cosmos DB](./media/cosmos-db-consistency-levels.png)

**Şekil 5-16**: tutarlılık düzeylerini Cosmos DB

### <a name="partitioning"></a>Bölümlendirme

Azure Cosmos DB, uygulamanızın performans ihtiyaçlarını karşılayacak şekilde veritabanını ölçeklendirmek için otomatik [bölümlendirme](https://docs.microsoft.com/azure/cosmos-db/partitioning-overview) kullanır.

Şekil 5-17 ' de gösterilen [veritabanları, kapsayıcılar ve öğeler](https://docs.microsoft.com/azure/cosmos-db/databases-containers-items)oluşturarak verileri Cosmos DB verileri yönetebilirsiniz.

![Cosmos DB varlıkları](./media/cosmos-db-entities.png)

**Şekil 5-17**: Cosmos DB varlıkların hiyerarşisi

Şekil 5-17 bir veritabanı hesabı içinde Cosmos DB veritabanı oluşturarak nasıl başladığına göz önüne alın. Bu veritabanı bir kapsayıcı kümesi için yönetim birimi olur. Kapsayıcı, seçili API sağlayıcınızı temel alan bir koleksiyon, tablo veya grafik olarak ifade edilebilir öğelerin şema belirsiz gruplandırmasıdır (önceki bölümde ele alınmıştır). Öğeler kapsayıcıya eklediğiniz ve belge, satır, düğüm veya kenar olarak temsil ettiğiniz veriler. Varsayılan olarak, bir kapsayıcıya eklediğiniz tüm öğeler açık dizin veya şema yönetimine gerek kalmadan otomatik olarak dizinlenir.

Kapsayıcıyı bölümlemek için öğeler [mantıksal bölümler](https://docs.microsoft.com/azure/cosmos-db/partition-data)adlı farklı alt kümelere bölünür. Mantıksal bölümler, bir kapsayıcıdaki her öğeyle ilişkili bir bölüm anahtarının değeri temel alınarak oluşturulur. Şekil 5-18 mantıksal bir bölümdeki tüm öğelerin aynı bölüm anahtarı değerine sahip olduğunu gösterir.

![Cosmos DB bölümlendirme mekanizması](./media/cosmos-db-partitioning.png)

**Şekil 5-18**: Cosmos DB bölümlendirme mekanizması

Şekil 5-18 ' de her öğenin ' City ' veya ' Havaalanı ' bölüm anahtarını nasıl içerdiğini göz önünde bırakın. Bu bölüm anahtarı öğenin mantıksal bölümünü belirler. Her şehir kodu, kapsayıcıda yer alan ve sağ taraftaki kapsayıcıya bir Havaalanı kodu olan bir mantıksal bölüme atanır. Bölüm anahtarı değerini bir öğenin KIMLIK değeriyle birleştirmek, öğenin benzersiz olarak tanımlandığı öğenin dizinini oluşturur.

Dahili olarak, Cosmos DB kapsayıcının ölçeklenebilirlik ve performans ihtiyaçlarını etkili bir şekilde karşılamak üzere [fiziksel bölümlerin](https://docs.microsoft.com/azure/cosmos-db/partition-data) [mantıksal bölümlerinin](https://docs.microsoft.com/azure/cosmos-db/partition-data) yerleşimini otomatik olarak yönetir. Bir uygulamanın aktarım hızı ve depolama gereksinimleri arttıkça Azure Cosmos DB, yükü daha fazla sayıda sunucuda yeniden dağıtmak için mantıksal bölümleri taşıtır. Bu yeniden dağıtım işlemleri Cosmos DB tarafından yönetilir ve herhangi bir kesinti veya kesinti olmadan gerçekleştirilir.

## <a name="azure-redis-cache"></a>Azure Redis Cache

Performansı ve ölçeklenebilirliği artırmak için önbelleğe almanın avantajları iyi anlaşılmıştır.

Bulutta yerel bir uygulama için, önbelleğe alma eklemek için ortak bir konum API ağ geçidinin içindedir. Ağ Geçidi, tüm gelen istekler için ön uç işlevi görür. Önbelleğe alma 'yı ekleyerek, önbelleğe alınmış verileri döndürerek ve yerel bir veritabanına veya aşağı akış hizmetine gidiş dönüşleri önleyerek performansı ve yanıt hızını artırabilirsiniz. Şekil 5-19, bulutta yerel bir uygulama için bir önbelleğe alma mimarisi gösterir.

![Bulutta yerel bir uygulamada önbelleğe alma](./media/caching-in-a-cloud-native-app.png)

**Şekil 5-19**: bulut Native bir uygulamada önbelleğe alma

Ortak bir önbelleğe alma deseninin [önbelleğe alma deseninin](https://docs.microsoft.com/azure/architecture/patterns/cache-aside)olması. Gelen bir istek için, Şekil 5-19 ' de adım #1 gösterildiği gibi yanıt önbelleğini sorgulayın. Bulunursa, veriler hemen döndürülür. Veriler önbellekte yoksa ( [önbellek isabetsizliği](https://www.techopedia.com/definition/6308/cache-miss)olarak bilinir), yerel veritabanı veya aşağı akış hizmetinden (adım #2) alınır ve gelecekteki istekler için önbelleğe yazılır (adım #3) ve çağırana döndürülür. Sistem tutarlı ve doğru kalacak şekilde önbelleğe alınan verileri düzenli aralıklarla çıkarmak için dikkatli olunması gerekir.

Ayrıca bkz. Şekil 5-19, önbelleğin hizmetin sınırları içinde yerel olarak nasıl uygulanmadığını, ancak bunun yerine, Bölüm 1 ' de anlatıldığı gibi bulut tabanlı bir yedekleme hizmeti olarak tüketildiğini aklınızda.

[Azure Redis Cache](https://azure.microsoft.com/services/cache/) , veri önbelleğe alma ve mesajlaşma Aracısı hizmetidir. Uygulamalar için verilere yüksek aktarım hızı ve düşük gecikmeli erişim sağlar. Azure 'da barındırılan ve Azure 'un içindeki veya dışındaki herhangi bir uygulamayla erişilebilen Microsoft tarafından tam olarak yönetilir.

Dahili olarak, Redsıs için Azure önbelleği açık kaynaklı [redo sunucusu](https://redis.io/) tarafından desteklenir ve [dizeler](https://redis.io/topics/data-types#strings), [karmalar](https://redis.io/topics/data-types#hashes), [listeler](https://redis.io/topics/data-types#sets), [kümeler](https://redis.io/topics/data-types#sets)ve [sıralanmış kümeler](https://redis.io/topics/data-types#sorted-sets)gibi veri yapılarını yerel olarak destekler. Uygulamanız Redsıs kullanıyorsa, Redsıs için Azure önbelleği ile olduğu gibi çalışır.

Redde için Azure Cache, bellek içi veri önbelleği, dağıtılmış ilişkisel olmayan bir veritabanı ve bir ileti Aracısı olarak da kullanılabilir. Üç farklı fiyatlandırma katmanlarında kullanılabilir. Premium katman kümeleme, veri kalıcılığı, coğrafi çoğaltma ve sanal ağ güvenliği ve yalıtımı gibi birçok kurumsal düzey özelliği sunar.

>[!div class="step-by-step"]
>[Önceki](data-patterns.md)
>[İleri](resiliency.md)
