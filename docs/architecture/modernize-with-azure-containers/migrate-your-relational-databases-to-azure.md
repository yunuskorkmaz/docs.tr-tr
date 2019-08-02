---
title: İlişkisel veritabanlarınızı Azure 'a geçirin
description: Azure bulut ve Windows kapsayıcıları Ile mevcut .NET uygulamalarını modernleştirin | ilişkisel veritabanlarınızı Azure 'a geçirin
ms.date: 04/28/2018
ms.openlocfilehash: 3d4f03e61144bb6a442a50916d7fd024d38ec611
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68677047"
---
# <a name="migrate-your-relational-databases-to-azure"></a>İlişkisel veritabanlarınızı Azure 'a geçirin

Minin Azure, en kapsamlı veritabanı geçişini sunmaktadır.

Azure 'da, veritabanı sunucularınızı doğrudan IaaS VM 'lerine (saf kaldırma ve kaydırma) geçirebilir veya ek avantajlar için Azure SQL veritabanı 'na geçiş yapabilirsiniz. Azure SQL veritabanı, yönetilen örnek ve hizmet olarak tam veritabanı (DBaaS) seçeneği sunar. Şekil 3-1, Azure 'da kullanılabilen birden çok ilişkisel veritabanı geçiş yolunu gösterir.

![Azure 'da veritabanı geçiş yolları](./media/image3-1.png)

> **Şekil 3-1.** Azure 'da veritabanı geçiş yolları

## <a name="when-to-migrate-to-azure-sql-database-managed-instance"></a>Azure SQL veritabanı yönetilen örneği 'ne geçiş

Çoğu durumda, Azure SQL veritabanı yönetilen örneği, verilerinizi Azure 'a geçirdiğinizde göz önünde bulundurmanız gereken en iyi seçenektir. SQL Server veritabanlarını geçiriyorsanız ve uygulamanızı yeniden mimarın veya veri ya da veri erişim kodunuzda değişiklikler yapmanız gerekmeyeceği hakkında neredeyse% 100 güvence altına almanız gerekiyorsa, Azure SQL veritabanı 'nın yönetilen örnek özelliğini seçin.

Örnek düzeyi işlevselliği SQL Server ek gereksinimleriniz veya standart bir Azure SQL veritabanında (tek veritabanı modeli) sunulan özelliklerin ötesinde yalıtım gereksinimleri varsa, Azure SQL veritabanı yönetilen örneği en iyi seçenektir. Bu son, en PaaS yönelimli seçenektir, ancak geleneksel bir SQL Server ile aynı özellikleri sunmaz. Geçiş, uçumlar gösterebilir.

Örneğin, örnek düzeyi SQL Server özelliklerde derin yatırımlar yapmış olan bir kuruluş, SQL yönetilen örneği 'ne geçiş özelliğinden faydalanır. Örnek düzeyi SQL Server özelliklerine örnek olarak SQL ortak dil çalışma zamanı (CLR) tümleştirmesi, SQL Server Agent ve veritabanları arası sorgulama dahildir. Bu özellikler için destek standart Azure SQL veritabanı 'nda (tek veritabanı modeli) kullanılamaz.

Yüksek düzeyde düzenlenen bir sektörde çalışan ve güvenlik amaçları için yalıtımın korunması gereken bir kuruluş, SQL yönetilen örnek modelinin seçilmesiyle de faydalanabilir.

Azure SQL veritabanı 'nda yönetilen örnek aşağıdaki özelliklere sahiptir:

- Azure sanal ağı üzerinden güvenlik yalıtımı

- Uygulama yüzeyi uyumluluğu, bu özelliklerle:

  - SQL Server Agent ve SQL Server Profiler

  - Veritabanları arası başvurular ve sorgular, SQL CLR, çoğaltma, değişiklik verilerini yakalama (CDC) ve Hizmet Aracısı

- Veritabanı boyutları 35 TB 'a kadar

- Bu özelliklerle en düşük kesinti süresi geçişi:

  - Azure veritabanı geçiş hizmeti

  - Yerel yedekleme ve geri yükleme ve günlük aktarma

Bu yetenekler sayesinde, mevcut uygulama veritabanlarını Azure SQL veritabanı 'na geçirdiğinizde, yönetilen örnek modeli SQL Server PaaS avantajlarından neredeyse% 100 ' ı sunar. Yönetilen örnek, Uygulama tasarımınızı değiştirmeden örnek düzeyi özellikleri kullanmaya devam ettiğiniz bir SQL Server ortamıdır.

Yönetilen örnek büyük olasılıkla SQL Server kullanmakta olan ve bulutta ağ güvenliğine esneklik gerektiren kuruluşlara en iyi şekilde uyum sağlar. SQL veritabanlarınız için özel bir sanal ağ olması gibidir.

## <a name="when-to-migrate-to-azure-sql-database"></a>Azure SQL veritabanı 'na geçiş

Belirtildiği gibi, standart Azure SQL veritabanı, tam olarak yönetilen, ilişkisel bir DBaaS olur. SQL veritabanı şu anda milyonlarca üretim veritabanını, dünyanın dört bir yanındaki 38 veri merkezinde yönetmektedir. Genel bir ölçekte gelişmiş veri işleme gerektiren en fazla veri kullanımı açısından kritik uygulamaları, çok sayıda uygulama ve iş yükünü yönetim açısından kolay işlem verilerini yönetmeyi destekler.

Tam PaaS özellikleri nedeniyle, daha iyi fiyatlandırma ve en düşük maliyetten dolayı, temel, standart SQL veritabanlarını kullanan ve ek örnek özelliği olmayan bir uygulamanız varsa standart Azure SQL veritabanına "varsayılan olarak seçim" olarak geçmeniz gerekir. SQL CLR tümleştirmesi, SQL Server Agent ve veritabanları arası sorgulama gibi SQL Server özellikler standart Azure SQL veritabanında desteklenmez. Bu özellikler yalnızca Azure SQL veritabanı yönetilen örnek modelinde kullanılabilir.

Azure SQL veritabanı, uygulama geliştiricileri için tasarlanan tek akıllı bulut veritabanı hizmetidir. Ayrıca, çok kiracılı uygulamaları verimli bir şekilde sunmanıza yardımcı olması için kapalı kalma süresi olmadan, hareket halindeyken ölçeklendirilen tek bulut veritabanı hizmetidir. Sonuç olarak, Azure SQL veritabanı, yenilik yapın 'e daha fazla zaman bırakır ve pazara sunma sürenizi hızlandırır. Tercih ettiğiniz dilleri ve platformları kullanarak güvenli uygulamalar oluşturabilir ve SQL veritabanınıza bağlanabilirsiniz.

Azure SQL veritabanı aşağıdaki avantajları sunar:

- Uygulamanıza öğrenip uyum sağlayan yerleşik zeka (Machine Learning)

- İsteğe bağlı veritabanı sağlama

- Tüm iş yükleri için bir dizi teklif

- % 99,99 kullanılabilirlik SLA 'Sı, sıfır bakım

- Veri koruma için coğrafi çoğaltma ve geri yükleme hizmetleri

- Azure SQL veritabanı zaman içindeki bir noktaya geri yükleme özelliği

- Karma ve geçiş dahil olmak üzere SQL Server 2016 ile uyumluluk

Standart Azure SQL veritabanı, Azure SQL veritabanı yönetilen örneği 'ne göre PaaS 'ye yakın. Yönetilen buluttan daha fazla avantaj elde edeceğiniz için standart Azure SQL veritabanını tercih edin. Ancak, Azure SQL veritabanı, normal ve şirket içi SQL Server örneklerinden bazı önemli farklılıklar içerir. Mevcut uygulamanızın veritabanı gereksinimlerine ve Kurumsal gereksinimlerinize ve ilkelerinize bağlı olarak, buluta geçişinizi planlarken bu en iyi seçenek olmayabilir.

## <a name="when-to-move-your-original-rdbms-to-a-vm-iaas"></a>Özgün RDBMS 'yi bir VM 'ye (IaaS) ne zaman taşıyacağınız

Geçiş seçeneklerinizin biri, Oracle, IBM DB2, MySQL, PostgreSQL veya SQL Server dahil olmak üzere özgün ilişkisel veritabanı yönetim sisteminizi (RDBMS) Azure VM 'de çalışan benzer bir sunucuya taşımadır. En az değişiklikle buluta en hızlı geçişi gerektiren mevcut uygulamalarınız varsa veya hiçbir değişiklik yapmadıysanız, bulutta IaaS 'ye doğrudan geçiş bir dengeli seçenek olabilir. Tüm bulutun avantajlarından faydalanmanın en iyi yolu olmayabilir, ancak en hızlı başlangıç yoludur.

Şu anda, Microsoft Azure IaaS VM olarak dağıtılan en fazla [331 farklı veritabanı sunucusunu](https://azuremarketplace.microsoft.com/marketplace/apps/category/databases?page=1&subcategories=databases-all) destekler. Bunlar SQL Server, Oracle, MySQL, PostgreSQL ve IBM DB2 gibi popüler RDBMS ve MongoDB, Cassandra, DataStax, MariaDB ve Cloudera gibi diğer birçok NoSQL veritabanlarını içerir.

> [!NOTE]
> RDBMS 'nizi bir Azure VM 'ye taşımak, verilerinizi buluta geçirmenin en hızlı yolu olabilir (IaaS olduğu için), bu yaklaşım BT ekipleriniz (veritabanı yöneticileri ve BT uzmanları) için önemli bir yatırım gerektirir. Kurumsal takımların SQL Server için yüksek kullanılabilirlik, olağanüstü durum kurtarma ve düzeltme eki uygulama ve yönetme olanağı vardır. Ayrıca, bu bağlamın tam yönetici haklarıyla özelleştirilmiş bir ortama ihtiyacı vardır.

## <a name="when-to-migrate-to-sql-server-as-a-vm-iaas"></a>VM (IaaS) olarak SQL Server 'e geçiş yapma

Hala SQL Server normal bir VM olarak geçirmeniz gereken birkaç durum olabilir. SQL Server Reporting Services kullanmanız gerekiyorsa örnek bir senaryo. Çoğu durumda, Azure SQL veritabanı yönetilen örneği, şirket içi SQL Server 'dan geçiş yapmak için ihtiyacınız olan her şeyi sağlayabilse de SQL Server VM geçiş yapmak için son çare olmalıdır.

## <a name="use-azure-database-migration-service-to-migrate-your-relational-databases-to-azure"></a>Azure veritabanı geçiş hizmeti 'ni kullanarak ilişkisel veritabanlarınızı Azure 'a geçirin 

Azure veritabanı geçiş hizmeti 'ni, hedef veritabanınızın Azure SQL veritabanı, Azure SQL veritabanı yönetilen örneği veya bir Azure VM üzerinde SQL Server gibi SQL Server, Oracle ve MySQL gibi ilişkisel veritabanlarını Azure 'a geçirmek için kullanabilirsiniz.

Değerlendirme raporlaması ile otomatikleştirilmiş iş akışı, veritabanını geçirmeden önce yapmanız gereken değişiklikler boyunca size rehberlik eder. Hazırsanız, hizmet kaynak veritabanını Azure 'a geçirir.

Özgün bir RDBMS 'yi her değiştirdiğinizde yeniden test etmeniz gerekebilir. Ayrıca, test sonuçlarına bağlı olarak uygulamanızdaki SQL cümleleri veya nesne Ilişkisel eşleme (ORM) kodunu değiştirmeniz gerekebilir.

Başka bir veritabanınız varsa (örneğin, IBM DB2) ve bir kaldırma ve kaydırma yaklaşımını tercih ediyorsanız, daha karmaşık bir veri geçişi gerçekleştirmek istemediğiniz sürece bu veritabanlarını Azure 'da IaaS VM 'Leri olarak kullanmaya devam etmek isteyebilirsiniz. Yeni şema ve farklı programlama kitaplıklarıyla farklı bir veritabanı türüne geçiş yapmanız gerektiğinden, daha karmaşık bir veri geçişi daha fazla çaba gerektirir.

Azure veritabanı geçiş hizmeti 'ni kullanarak veritabanlarının nasıl geçirileceğiyle ilgili bilgi edinmek için bkz. [Azure SQL veritabanı yönetilen örneği ve Azure veritabanı geçiş hizmeti ile buluta daha hızlı ulaşın](https://channel9.msdn.com/Events/Build/2017/P4008).

## <a name="additional-resources"></a>Ek kaynaklar

- **Bir bulut SQL Server seçeneği belirleyin: Azure SQL veritabanı (PaaS) veya Azure VM 'de SQL Server (IaaS)**

    <https://docs.microsoft.com/azure/sql-database/sql-database-paas-vs-sql-server-iaas>

- **Azure SQL VERITABANı yönetilen örneği ve veritabanı geçiş hizmeti ile buluta daha hızlı ulaşın**

    <https://channel9.msdn.com/Events/Build/2017/P4008>

- **SQL veritabanı bulutta SQL Server veritabanını geçirme**

    <https://docs.microsoft.com/azure/sql-database/sql-database-cloud-migrate>

- **Azure SQL Veritabanı**

    <https://azure.microsoft.com/services/sql-database/?v=16.50>

- **Sanal makinelerde SQL Server**

    <https://azure.microsoft.com/services/virtual-machines/sql-server/>

> [!div class="step-by-step"]
> [Önceki](lift-and-shift-existing-apps-azure-iaas.md)İleri
> [](modernize-existing-apps-to-cloud-optimized/index.md)
