---
title: "İlişkisel veritabanlarınızı azure'a geçirme"
description: "Azure Bulut ve Windows kapsayıcıları varolan .NET uygulamaları modernize | İlişkisel veritabanlarınızı azure'a geçirme"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/26/2017
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 221d8c2b837fb738425e26f3af4da895e4987212
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="migrate-your-relational-databases-to-azure"></a>İlişkisel veritabanlarınızı azure'a geçirme

Görme: Azure en kapsamlı veritabanı geçiş sunar.

Azure, doğrudan Iaas VM'ler için (saf yükseltme ve shift) veritabanı sunucularınız geçirebileceğiniz veya Azure SQL veritabanına ek faydalar geçirebilirsiniz. Azure SQL veritabanı yönetilen örneği ve tam veritabanı olarak-hizmet (DBaaS) seçenekleri sunar. Şekil 3-1'birden çok ilişkisel veritabanı mevcut geçiş yolları gösterir.

![Azure veritabanı geçiş yolları](./media/image3-1.png)

> **Şekil 3-1.** Azure veritabanı geçiş yolları

## <a name="when-to-migrate-to-azure-sql-database-managed-instance"></a>Azure SQL veritabanı yönetilen örneğine geçirmek ne zaman

Çoğu durumda, yönetilen Azure SQL veritabanı örneği için Azure verilerinizi geçirdiğinizde dikkate alınması gereken, en iyi seçenek olacaktır. SQL Server veritabanlarını geçirme ve neredeyse uygulamanızı yeniden düzenlenmesine veya veri veya veri erişim kodu için değişiklik gerekmez % 100 güvence ihtiyacınız varsa, Azure SQL veritabanı'nın yönetilen örneği özelliğini seçin.

SQL Server örnek düzeyinde işlevselliği için ek gereksinimler veya standart bir Azure SQL veritabanına (tek veritabanı modeli) sağlanan özellikler ötesinde yalıtım gereksinimleri varsa, yönetilen azure SQL veritabanı örneği en iyi seçenektir. Bu sonuncu en PaaS yönelik bir seçenektir ancak, geleneksel SQL server'ın aynı özellikleri sunmaz. Geçiş frictions yüzey.

Örneğin, derin Yatırımlar örnek düzeyinde SQL Server özellikleri yaptığı bir kuruluş yönetilen SQL örneğine geçirme yararlanabileceğini. Örnek düzeyinde SQL Server özellikleri örnekleri SQL ortak dil çalışma zamanı (CLR) tümleştirmesini, SQL Server Aracısı içerir ve veritabanları arası sorgulama. Bu özellikler için destek standart Azure SQL veritabanı (tek veritabanı modeli) kullanılamaz.

Bir kuruluş içinde yüksek oranda düzenlenen endüstri çalışır ve hangi güvenlik amacıyla yalıtımı sağlamak gereken SQL örneğini yönetilen modeli seçme de yararlanabilir.

Yönetilen Azure SQL veritabanı örneğinde aşağıdaki özelliklere sahiptir:

-   Azure sanal ağ için güvenlik yalıtımı

-   Yüzey ile uygulama uyumluluğu, bu özellikler:

    -   SQL Server Agent ve SQL Server Profiler

    -   Veritabanları arası başvuruları ve sorgular, SQL CLR, çoğaltma, değişiklik verilerini yakalama (CDC) ve hizmet Aracısı

-   Veritabanı 35 TB'ye kadar boyutları

-   Bu özelliklere sahip en az kapalı kalma süresi geçişi:

    -   Azure veritabanı geçiş hizmeti

    -   Yerel yedekleme ve geri yükleme ve günlük aktarma

Azure SQL veritabanı için varolan uygulama veritabanları geçirdiğinizde bu özellikler sayesinde, SQL Server için Paas avantajları yaklaşık % 100 Yönetilen örnek modeli sunar. Burada, uygulamanızın tasarımına değiştirmeden örnek düzeyi özellikleri kullanmaya devam etmek bir SQL Server ortamını yönetilen örneğidir.

Yönetilen örneği SQL Server kullanıyorsanız ve bunların ağ güvenliği bulutta esneklik gerektiren kuruluşlar için en uygun olabilir. Bu, SQL veritabanları için özel bir sanal ağ olması gibi olur.

## <a name="when-to-migrate-to-azure-sql-database"></a>Ne zaman Azure SQL veritabanına geçirme 

Belirtildiği gibi standart Azure SQL veritabanı tam olarak yönetilen, ilişkisel DBaaS gereklidir. SQL veritabanı üretim veritabanları, milyonlarca 38 veri merkezleri, dünya genelinde şu anda yönetir. Çok çeşitli uygulamaları ve yürüten bir küresel ölçekli gelişmiş veri işleme gerektiren en veri kullanımı yoğun, görev açısından kritik uygulamalar için basit işlem verilerini yönetmesini iş yükleri, destekler.

Fiyatlandırma tam PaaS özellikleri nedeniyle ve daha iyi- ve sonuçta maliyetini düşürür-o kullanan temel, standart SQL veritabanları ve hiçbir ek örnek özellik bir uygulamanız varsa "varsayılan olarak tercih ettiğiniz" standart Azure SQL veritabanına taşımanız gerekir. SQL Server özellikleri SQL CLR tümleştirme, SQL Server Agent ve veritabanları arası sorgulama gibi standart Azure SQL veritabanı'nda desteklenmez. Bu özellikleri yalnızca Azure SQL veritabanı örneği yönetilen modelde kullanılamaz.

Azure SQL veritabanı, uygulama geliştiricileri için tasarlanmış yalnızca akıllı bulut veritabanı hizmetidir. Bu ayrıca üzerinde-çok müşterili uygulamalar verimli bir şekilde sunmanıza yardımcı olması için kapalı kalma süresi, çalışma sırasında ölçeklendirilebilen yalnızca bulut veritabanı hizmetidir. Sonuç olarak, Azure SQL veritabanı yenilik için daha fazla zaman bırakır ve pazara zamanınızı hızlandırır. Güvenli uygulamalar oluşturma ve tercih ettiğiniz platformlar ve diller kullanarak SQL veritabanına bağlanın.

Azure SQL veritabanı aşağıdaki avantajları sunar:

-   Öğrenir ve uygulamanıza uyum yerleşik zekaya (makine öğrenme)

-   İsteğe bağlı veritabanı sağlama

-   Teklifler, tüm iş yükleri için bir aralığı

-   % 99,99 kullanılabilirlik SLA'sı, sıfır bakım

-   Veri koruma için coğrafi çoğaltma ve Geri Yükleme Hizmetleri

-   Azure SQL veritabanı noktası zaman geri özelliği

-   Karma ve geçiş dahil olmak üzere SQL Server 2016 ile uyumluluk

Standart Azure SQL veritabanı için PaaS Azure SQL veritabanı yönetilen örneği yakındır. Yönetilen bir buluttan daha fazla avantajları elde edersiniz olduğundan, mümkünse, kullanmayı denemeniz gerekir. Ancak, Azure SQL veritabanı normal gelen önemli bazı farklar vardır ve şirket içi SQL Server örnekleri. Buluta geçiş planlarken, mevcut uygulamanızın veritabanı gereksinimleri ve kurumsal gereksinimleri ve ilkeleri bağlı olarak, en iyi seçenek olmayabilir.

## <a name="when-to-move-your-original-rdbms-to-a-vm-iaas"></a>Bir VM'yi (Iaas), özgün RDBMS taşımak ne zaman

Geçiş seçenekleri Azure VM temelinde çalıştırılan benzer bir sunucu için Oracle, IBM DB2, MySQL, PostgreSQL veya SQL Server dahil olmak üzere, özgün ilişkisel veritabanı yönetim sistemine (RDBMS) taşımak için biridir. Tüm küçük değişiklikler ya da herhangi bir değişiklik olan buluta hızlı geçiş gerektiren uygulamalarınız varsa, Iaas bulutta doğrudan geçiş Orta bir seçenek olabilir. Tüm bulutun avantajlarından yararlanmak için en iyi yolu olmayabilir ancak büyük olasılıkla hızlı başlangıç yoludur.

Şu anda, Microsoft Azure kadar destekler [331 farklı veritabanı sunucuları](https://azuremarketplace.microsoft.com/en-us/marketplace/apps/category/databases?page=1&subcategories=databases-all) Iaas VM'ler dağıtılabilir. Bunlar, SQL Server, Oracle, MySQL, PostgreSQL ve IBM DB2 gibi popüler RDBMSes ve MongoDB, Cassandra, DataStax, MariaDB ve Cloudera gibi diğer birçok NoSQL veritabanı içerir.

> [!NOTE]
> Taşıma rağmen bir Azure VM, RDBMS (Iaas olduğundan) verilerinizi buluta geçirmek için en hızlı yolu olabilir, bu yaklaşım BT ekipleriniz (Veritabanı yöneticileri ve BT uzmanlarının) önemli bir yatırım gerektirir. Kurumsal takımlar ayarlamak ve yüksek kullanılabilirlik, olağanüstü durum kurtarma ve SQL Server için düzeltme eki uygulama yönetmek gerekir. Bu bağlamda tam yönetici haklarına sahip bir özelleştirilmiş ortamını da gerekir.

## <a name="when-to-migrate-to-sql-server-as-a-vm-iaas"></a>SQL Server (Iaas) VM olarak geçirmek ne zaman

Burada, hala SQL Server normal VM olarak geçirmek için gereken bazı durumlarda olabilir. Örnek bir senaryo, SQL Server Reporting Services kullanmanız gerekip gerekmediğini ' dir. Çoğu durumda, yine de Azure SQL veritabanı yönetilen örneği bir SQL Server VM geçiş denemek için son çare nedenle şirket içi SQL sunuculardan geçirmek için gereken her şeyi sağlayabilir.

## <a name="use-azure-database-migration-service-to-migrate-your-relational-databases-to-azure"></a>Azure veritabanı geçiş hizmeti ilişkisel veritabanlarınızı Azure'a geçirmek için kullanın 

Azure SQL Database, Azure SQL veritabanı yönetilen örneği veya Azure VM'de SQL Server hedef veritabanınızın olup olmadığını SQL Server, Oracle ve MySQL gibi ilişkisel veritabanları, Azure'a geçirmek için Azure veritabanı geçiş hizmetini kullanabilirsiniz.

Değerlendirme Raporlama ile otomatik iş akışı, veritabanı geçirmeden önce yapmanız gereken değişiklikleri size rehberlik eder. Hazır olduğunuzda, hizmet kaynak veritabanı için Azure geçirir.

Özgün RDBMS değiştirdiğinizde, yeniden sınayın gerekebilir. Ayrıca SQL cümleleri veya nesne ilişkisel eşleme (ORM), uygulamanızdaki kod sınama sonuçları bağlı olarak, değiştirmeniz gerekebilir.

Daha karmaşık veri geçişi gerçekleştirmek hazır olduğunuz sürece herhangi diğer bir veritabanını (örneğin, IBM DB2) varsa ve yükseltme ve shift bir yaklaşım opt, bu veritabanları, azure'da Iaas Vm'leri olarak kullanmaya devam etmek isteyebilirsiniz. Farklı veritabanı türü yeni şema ve farklı programlama kitaplıkları ile geçiş çünkü daha karmaşık bir veri geçişi ek çaba gerekir.

Azure veritabanı geçiş hizmetini kullanarak veritabanlarını geçirme konusunda bilgi almak için bkz: [yönetilen Azure SQL veritabanı örneği ve Azure veritabanı geçiş hizmeti ile daha hızlı buluta alma](https://channel9.msdn.com/Events/Build/2017/P4008).

## <a name="additional-resources"></a>Ek kaynaklar

-   **Bir bulut SQL Server seçeneği seçin: Azure SQL veritabanı (PaaS) ya da SQL Server Azure VM'de (Iaas)**

    [https://docs.microsoft.com/azure/sql-database/sql-database-paas-vs-sql-server-iaas](https://docs.microsoft.com/azure/sql-database/sql-database-paas-vs-sql-server-iaas)

-   **Azure SQL DB yönetilen örneği ve veritabanı geçiş hizmeti ile daha hızlı buluta alma**

    [https://channel9.msdn.com/Events/Build/2017/P4008](https://channel9.msdn.com/Events/Build/2017/P4008)

-   **Bulutta SQL veritabanı için SQL Server veritabanı geçirme**

    [https://docs.microsoft.com/azure/sql-database/sql-database-cloud-migrate](https://docs.microsoft.com/azure/sql-database/sql-database-cloud-migrate)

-   Azure SQL veritabanı

    [https://azure.microsoft.com/services/sql-database/?v=16.50](https://azure.microsoft.com/services/sql-database/?v=16.50)

-   **SQL Server sanal makineler**

    [https://azure.microsoft.com/services/virtual-machines/sql-server/](https://azure.microsoft.com/services/virtual-machines/sql-server/)

>[!div class="step-by-step"]
[Önceki](lift-and-shift-existing-apps-azure-iaas.md)
[sonraki](lift-and-shift-existing-apps-devops/index.md)