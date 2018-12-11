---
title: İlişkisel veritabanlarınızı azure'a geçirin
description: Azure Bulutu ve Windows kapsayıcıları ile mevcut .NET uygulamalarını modernleştirme | İlişkisel veritabanlarınızı azure'a geçirin
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 04/28/2018
ms.openlocfilehash: a2aedc9729c674a7b4958506b90c285e54d8d724
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53153767"
---
# <a name="migrate-your-relational-databases-to-azure"></a>İlişkisel veritabanlarınızı azure'a geçirin

İşleme: Azure, en kapsamlı veritabanı geçişi sunar.

Azure, veritabanı sunucularınız doğrudan Iaas Vm'lerine (saf lift- and -shift) geçirebilirsiniz veya Azure SQL veritabanı'na ek avantajlardan yararlanma geçirebilirsiniz. Azure SQL veritabanı yönetilen örneği ve tam olarak bir-hizmet veritabanı (DBaaS) seçenekleri sunar. Şekil 3-1, birden çok ilişkisel veritabanı Azure'da kullanılabilmesi için geçiş yolları gösterir.

![Azure veritabanı geçiş yolları](./media/image3-1.png)

> **Şekil 3-1.** Azure veritabanı geçiş yolları

## <a name="when-to-migrate-to-azure-sql-database-managed-instance"></a>Azure SQL veritabanı yönetilen örneğine geçirmek ne zaman

Çoğu durumda, Azure SQL veritabanı yönetilen örneği göz önünde bulundurun, verilerinizi Azure'a geçiş için en iyi seçenek olacaktır. SQL Server veritabanlarını geçirme ve uygulamanızı yeniden oluşturma veya veri veya veri erişim kodu değişiklik gerekmez neredeyse % 100 güvencesi gerekir, Azure SQL veritabanı yönetilen örneği'özelliği ' ni seçin.

SQL Server Örnek düzeyi işlevi için ek gereksinimler ya da bir standart Azure SQL veritabanı'nda (tek veritabanı modeli) sağlanan özelliklerin ötesinde yalıtım gereksinimleri varsa, azure SQL veritabanı yönetilen örneği en iyi seçenektir. Bu sonuncu en PaaS odaklı seçim olmakla birlikte, geleneksel SQL Server ile aynı özellikleri sunulmaz. Geçiş frictions yüzey.

Örneğin, SQL yönetilen örneği'ne geçiş öğesinden ayrıntılı Yatırımlar örnek düzeyi SQL Server özellikleri yaptığı bir kuruluş faydalanacaktır. Örnek düzeyi SQL Server özellikleri örnekleri SQL ortak dil çalışma zamanı (CLR) tümleştirmesini, SQL Server Aracısı içerir ve veritabanları arası sorgulama. Bu özellikler için destek, standart Azure SQL veritabanı (tek veritabanı modeli) kullanılamıyor.

Bir yüksek düzeyde denetime tabi sektöründe çalışır ve hangi güvenlik amacıyla ayırma sağlamak gereken bir kuruluş, SQL yönetilen örnek modeli seçmesini de yararlanabilir.

Azure SQL veritabanı yönetilen örneği, aşağıdaki özelliklere sahiptir:

- Azure sanal ağ için güvenlik yalıtımı

- Uygulama yüzey uyumluluğu, bu özelliklere sahip:

  - SQL Server Agent'ı ve SQL Server Profiler

  - Veritabanları arası başvurular ve sorgular, SQL CLR, çoğaltma, değişiklik verilerini yakalama (CDC) ve hizmet Aracısı

- En fazla 35 TB veritabanı boyutları

- Bu özelliklere sahip en az kapalı kalma süresiyle geçiş:

  - Azure veritabanı geçiş hizmeti

  - Yerel yedekleme ve geri yükleme ve günlük aktarma

Mevcut uygulama veritabanlarını Azure SQL veritabanı'na geçirirken bu özellikler sayesinde, SQL Server için yaklaşık %100 Paas avantajlarını yönetilen örnek modeli sunar. Yönetilen örnek, burada örnek düzeyi özelliklerini uygulama tasarımınızı değiştirmeden kullanmaya devam bir SQL Server ortamıdır.

Yönetilen örnek SQL Server kullanıyorsanız ve bulutta kullanarak ağ güvenliğini esneklik gerektiren kuruluşlar için en uygun olabilir. Bu, SQL veritabanları için özel bir sanal ağ gibidir.

## <a name="when-to-migrate-to-azure-sql-database"></a>Azure SQL veritabanı'na geçirmek ne zaman

Belirtildiği gibi standart Azure SQL veritabanı tam olarak yönetilen, ilişkisel DBaaS hizmetidir. SQL veritabanı, dünya çapındaki 38 veri merkezleri arasında şu anda üretim veritabanları, milyonlarca yönetir. Bu, çok çeşitli uygulamalar ve sürüş küresel ölçekte gelişmiş veri işleme gerektiren en yoğun olarak veri, görev açısından kritik uygulamalar için basit işlem verilerini yönetmesini iş yüklerini destekler.

Tam PaaS özellikleri nedeniyle daha iyi fiyat- ve sonuçta düşürün-o kullandığı temel, standart SQL veritabanları ve hiçbir ek örnek özellik bir uygulamanız varsa, "varsayılan seçenek" olarak standart Azure SQL veritabanı'na taşımanız gerekir. SQL Server özellikleri SQL CLR tümleştirmesi, SQL Server Agent ve veritabanları arası sorgulama gibi standart Azure SQL veritabanı'nda desteklenmez. Bu özellikler, yalnızca Azure SQL veritabanı yönetilen örneği modelinde kullanılabilir.

Azure SQL veritabanı, uygulama geliştiriciler için tasarlanmış yalnızca akıllı bulut veritabanı hizmetidir. Bu da şirket-çok kiracılı uygulamaları verimli bir şekilde sunmanıza yardımcı olması için kapalı kalma süresi olmadan, çalışma sırasında ölçeklenen yalnızca bulut veritabanı hizmetidir. Sonuç olarak, Azure SQL veritabanı, yenilik geliştirmeye daha fazla zaman ayrılması ve pazara sunma sürenizi hızlandırır. Güvenli uygulamalar oluşturmak ve tercih ettiğiniz platformları ve dilleri kullanarak SQL veritabanınıza bağlanın.

Azure SQL veritabanı, aşağıdaki avantajları sunar:

- Öğrenip uygulamanıza uyarlayan yerleşik zeka (makine öğrenimi)

- İsteğe bağlı veritabanı sağlama

- Teklif, tüm iş yükleri için çeşitli

- % 99,99 kullanılabilirlik SLA'sı, sıfır bakım gerektirir

- Veri koruma için coğrafi çoğaltma ve Geri Yükleme Hizmetleri

- Azure SQL veritabanı noktası geri yükleme özelliği

- Karma ve geçiş de dahil olmak üzere SQL Server 2016 ile uyumluluk

Standart Azure SQL veritabanı PaaS için Azure SQL veritabanı yönetilen örneği yakındır. Standart Azure SQL veritabanı, yönetilen bir buluttan daha fazla Avantajdan faydalanmak çünkü tercih eder. Ancak, Azure SQL veritabanı düzenli gelen bazı temel farklılıklara sahiptir ve şirket içinde SQL Server örnekleri. Buluta geçişinizi planlarken, mevcut uygulamanızın veritabanı gereksinimleri ve kurumsal gereksinimleri ve ilkeleri bağlı olarak, en iyi seçim olmayabilir.

## <a name="when-to-move-your-original-rdbms-to-a-vm-iaas"></a>Bir VM'ye (Iaas), özgün RDBMS taşıma zamanı

Geçiş seçeneklerinizi benzer sunucuya bir Azure sanal makinesinde çalıştırılan Oracle, IBM DB2, MySQL, PostgreSQL veya SQL Server dahil olmak üzere, özgün ilişkisel veritabanı yönetim sistemi (RDBMS) taşımak için biridir. Hiç olası en az değişiklikle veya hiç değişiklik ile buluta hızlı geçiş gerektiren uygulamalarınız varsa, doğrudan geçiş için Iaas bulutta adil bir seçenek olabilir. Bulutun tüm avantajlarından yararlanmak için en iyi yolu olmayabilir, ancak bu hızlı başlangıç yolu olabilir.

Şu anda Microsoft Azure'ı kadar destekler [331 farklı veritabanı sunucuları](https://azuremarketplace.microsoft.com/en-us/marketplace/apps/category/databases?page=1&subcategories=databases-all) Iaas Vm'leri olarak dağıtılabilir. Bunlar, SQL Server, Oracle, MySQL, PostgreSQL ve IBM DB2 gibi popüler RDBMS ve MongoDB, Cassandra, DataStax, MariaDB ve Cloudera gibi diğer birçok NoSQL veritabanlarını içerir.

> [!NOTE]
> Taşıma olsa da (Iaas olduğundan) verilerinizi buluta taşımak için en hızlı yolu, bir RDBMS'de Azure VM'ye olabilir, bu yaklaşım, BT ekiplerinin (Veritabanı yöneticileri ve BT uzmanları) önemli bir yatırım gerektirir. Kurumsal takımlar ayarlamak ve yüksek kullanılabilirlik, olağanüstü durum kurtarma ve SQL Server için düzeltme yönetmek gerekir. Bu bağlam, tam yönetici haklarına sahip özelleştirilmiş bir ortama da gerekir.

## <a name="when-to-migrate-to-sql-server-as-a-vm-iaas"></a>Ne zaman bir sanal makine (Iaas) SQL Server'a geçirme

Burada normal bir VM olarak SQL Server'a geçirme yine bazı durumlar olabilir. Örnek bir senaryo, SQL Server Reporting Services'ı kullanmanız gerekip gerekmediğini ' dir. Çoğu durumda, Azure SQL veritabanı yönetilen örneği SQL Server VM geçişi, son çare denemeniz bu nedenle şirket içi SQL sunucusundan geçirmek için gereken her şeyi yine de sağlayabilirsiniz.

## <a name="use-azure-database-migration-service-to-migrate-your-relational-databases-to-azure"></a>İlişkisel veritabanlarınızı Azure'a geçirmek için Azure veritabanı geçiş hizmeti kullanın 

Hedef veritabanınızı Azure SQL veritabanı, Azure SQL veritabanı yönetilen örneği veya Azure VM'deki SQL Server olup, SQL Server, Oracle ve MySQL gibi ilişkisel veritabanları, Azure geçişi için Azure veritabanı geçiş hizmeti kullanabilirsiniz.

Değerlendirme Raporlama ile otomatikleştirilmiş iş akışı, veritabanını geçirmeden önce yapmanız gereken değişiklikleri size yol gösterir. Hazır olduğunuzda, hizmet kaynak veritabanını Azure'a geçirir.

Özgün bir RDBMS'de değiştirdiğinizde değişiyorsa gerekebilir. SQL cümleler veya sınama sonuçları bağlı olarak, uygulamanızda nesne ilişkisel eşleme (ORM) kodu değiştirmek gerekebilir.

Daha karmaşık bir veri geçişi gerçekleştirmek hazır olduğunuz sürece başka bir veritabanı (örneğin, IBM DB2) varsa ve lift and shift ile bir yaklaşım için iyileştirilmiş, bu veritabanları, azure'da Iaas Vm'leri olarak kullanmaya devam etmek isteyebilirsiniz. Farklı veritabanı türüne yeni bir şema ve farklı programlama kitaplıkları ile geçiş çünkü daha karmaşık bir veri geçişi ek çaba gerektirir.

Azure veritabanı geçiş hizmetini kullanarak veritabanlarını geçirme konusunda bilgi almak için bkz: [almak için Azure veritabanı geçiş hizmeti ile Azure SQL veritabanı yönetilen örneği ile daha hızlı bulut](https://channel9.msdn.com/Events/Build/2017/P4008).

## <a name="additional-resources"></a>Ek kaynaklar

- **Bir bulut SQL Server seçeneği seçin: Azure SQL veritabanı (PaaS) ya da (Iaas) Azure VM'de SQL Server**

    [https://docs.microsoft.com/azure/sql-database/sql-database-paas-vs-sql-server-iaas](https://docs.microsoft.com/azure/sql-database/sql-database-paas-vs-sql-server-iaas)

- **Bulutta Azure SQL DB yönetilen örneği ve veritabanı geçiş hizmeti ile daha hızlı alın**

    [https://channel9.msdn.com/Events/Build/2017/P4008](https://channel9.msdn.com/Events/Build/2017/P4008)

- **SQL veritabanı bulutta SQL Server veritabanını geçirme**

    [https://docs.microsoft.com/azure/sql-database/sql-database-cloud-migrate](https://docs.microsoft.com/azure/sql-database/sql-database-cloud-migrate)

- **Azure SQL Veritabanı**

    [https://azure.microsoft.com/services/sql-database/?v=16.50](https://azure.microsoft.com/services/sql-database/?v=16.50)

- **Sanal makinelerde SQL Server**

    [https://azure.microsoft.com/services/virtual-machines/sql-server/](https://azure.microsoft.com/services/virtual-machines/sql-server/)

>[!div class="step-by-step"]
>[Önceki](lift-and-shift-existing-apps-azure-iaas.md)
>[İleri](modernize-existing-apps-to-cloud-optimized/index.md)