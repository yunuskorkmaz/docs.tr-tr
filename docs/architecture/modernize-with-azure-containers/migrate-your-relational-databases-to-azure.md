---
title: İlişkisel veritabanlarınızı azure'a geçirin
description: Azure Bulutu ve Windows Kapsayıcıları ile Mevcut .NET Uygulamalarını Modernize Edin | ilişkisel veritabanlarınızı azure'a geçirin
ms.date: 04/28/2018
ms.openlocfilehash: efd1548c3f74fc27450f4949d71a1c4d61907ba5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "73093623"
---
# <a name="migrate-your-relational-databases-to-azure"></a>İlişkisel veritabanlarınızı azure'a geçirin

Vizyon: Azure en kapsamlı veritabanı geçişini sunar.

Azure'da, veritabanı sunucularınızı doğrudan IaaS VM'lere (saf kaldırma ve kaydırma) geçirebilirsiniz veya ek avantajlar için Azure SQL Veritabanı'na geçirebilirsiniz. Azure SQL Veritabanı, yönetilen örnek ve hizmet olarak tam veritabanı (DBaaS) seçenekleri sunar. Şekil 3-1, Azure'da bulunan birden çok ilişkisel veritabanı geçiş yollarını gösterir.

![Azure'da veritabanı geçiş yolları](./media/image3-1.png)

**Şekil 3-1.** Azure'da veritabanı geçiş yolları

## <a name="when-to-migrate-to-azure-sql-database-managed-instance"></a>Azure SQL Veritabanı Yönetilen Örneği'ne ne zaman geçirilir?

Çoğu durumda, Azure SQL Veritabanı Yönetilen Örneği, verilerinizi Azure'a aktarırken göz önünde bulundurmanız gereken en iyi seçenek olacaktır. SQL Server veritabanlarını geçiriyorsanız ve uygulamanızı yeniden architecta yapmanıza veya verilerinizde veya veri erişim kodunuzda değişiklik yapmanıza gerek kalmayacağına dair yaklaşık %100 güvenceye ihtiyacınız varsa, Azure SQL Veritabanı'nın Yönetilen Örnek özelliğini seçin.

Sql Server örnek düzeyi işlevselliği veya standart bir Azure SQL Veritabanı'nda (tek veritabanı modeli) sağlanan özelliklerin ötesinde yalıtım gereksinimleri için ek gereksinimleriniz varsa, Azure SQL Veritabanı Yönetilen Örneği en iyi seçenektir. Bu sonuncusu en PaaS odaklı seçimdir, ancak geleneksel bir SQL sunucusu ile aynı özellikleri sunmuyor. Göç sürtünmeleri yüzeye çıkarabilir.

Örneğin, örnek düzeyindeKI SQL Server yeteneklerine derin yatırımlar yapmış bir kuruluş, SQL Yönetilen Örnek'e geçişten yararlanır. Örnek düzeyindeki SQL Server özelliklerine örnek olarak SQL ortak dil çalışma zamanı (CLR) tümleştirmesi, SQL Server Agent ve veritabanı arası sorgulama verilebilir. Bu özellikler için destek standart Azure SQL Veritabanında (tek veritabanı modeli) kullanılamaz.

Son derece düzenli bir sektörde faaliyet gösteren ve güvenlik amacıyla yalıtımı sürdürmesi gereken bir kuruluş, SQL Yönetilen Örnek modelini seçmekten de yararlanabilir.

Azure SQL Veritabanı'nda Yönetilen Örnek aşağıdaki özelliklere sahiptir:

- Azure Sanal Ağ üzerinden güvenlik yalıtımı

- Uygulama yüzey uyumluluğu, bu özelliklerle:

  - SQL Server Agent ve SQL Server Profiler

  - Veritabanı arası başvurular ve sorgular, SQL CLR, çoğaltma, veri yakalamayı değiştirme (CDC) ve Servis Aracısı

- 35 TB'a kadar veritabanı boyutları

- Bu özelliklere sahip minimum kapalı kalma süresi geçişi:

  - Azure Veritabanı Geçiş Hizmeti

  - Yerel yedekleme ve geri yükleme ve günlük gönderim

Bu özelliklerle, varolan uygulama veritabanlarını Azure SQL Veritabanı'na geçirdiğinizde, Yönetilen Örnek modeli SQL Server için PaaS'ın avantajlarının yaklaşık %100'ünü sunar. Yönetilen Örnek, uygulama tasarımınızı değiştirmeden örnek düzeyindeki yetenekleri kullanmaya devam ettiğiniz bir SQL Server ortamıdır.

Yönetilen Örnek, büyük olasılıkla şu anda SQL Server kullanan ve buluttaki ağ güvenliğinde esneklik gerektiren işletmeler için en uygun olandır. Bu, SQL veritabanlarınız için özel bir sanal ağa sahip olmak gibidir.

## <a name="when-to-migrate-to-azure-sql-database"></a>Azure SQL Veritabanı'na ne zaman geçirilir?

Belirtildiği gibi, standart Azure SQL Veritabanı tamamen yönetilen, ilişkisel bir DBaaS'tır. SQL Veritabanı şu anda dünya çapında 38 veri merkezinde milyonlarca üretim veritabanını yönetetmektedir. Basit işlem verilerini yönetmekten, küresel ölçekte gelişmiş veri işleme gerektiren en veri yoğun, görev açısından kritik uygulamaları yönlendirmeye kadar çok çeşitli uygulamaları ve iş yüklerini destekler.

Tam PaaS özellikleri nedeniyle, daha iyi fiyatlandırma ve sonuçta daha düşük maliyet-temel, standart SQL veritabanları kullanan ve ek örnek özellikleri kullanan bir uygulama varsa", varsayılan seçim olarak standart Azure SQL Veritabanı'na taşımalısınız. SQL CLR tümleştirmesi, SQL Server Agent ve çapraz veritabanı sorgulama gibi SQL Server özellikleri standart Azure SQL Veritabanında desteklenmez. Bu özellikler yalnızca Azure SQL Veritabanı Yönetilen Örnek modelinde kullanılabilir.

Azure SQL Veritabanı, uygulama geliştiricileri için oluşturulmuş tek akıllı bulut veritabanı hizmetidir. Ayrıca, çok kiracılı uygulamaları verimli bir şekilde sunmanıza yardımcı olmak için kesinti olmaksızın anında ölçeklendirilebilen tek bulut veritabanı hizmetidir. Sonuç olarak, Azure SQL Veritabanı size yenilik yapmak için daha fazla zaman bırakır ve pazara gitmek için zamanınızı hızlandırır. Tercih ettiğiniz dilleri ve platformları kullanarak güvenli uygulamalar oluşturabilir ve SQL veritabanınıza bağlanabilirsiniz.

Azure SQL Veritabanı aşağıdaki avantajları sunar:

- Uygulamanızı öğrenen ve uygulamanıza uyum sağlayan yerleşik zeka (makine öğrenimi)

- İsteğe bağlı veritabanı sağlama

- Tüm iş yükleri için çeşitli teklifler

- 99.99% kullanılabilirlik SLA, sıfır bakım

- Veri koruma için coğrafi çoğaltma ve geri yükleme hizmetleri

- Azure SQL Veritabanı Zaman Geri Yükleme özelliği

- Hibrit ve geçiş dahil olmak üzere SQL Server 2016 ile uyumluluk

Standart Azure SQL Veritabanı, PaaS'a Azure SQL Veritabanı Yönetilen Örneği'nden daha yakındır. Yönetilen bir buluttan daha fazla avantaj elde edersiniz, çünkü standart Azure SQL Veritabanı'nı tercih edin. Ancak, Azure SQL Veritabanı'nın düzenli ve şirket içi SQL Server örneklerinden bazı önemli farklılıkları vardır. Varolan uygulamanızın veritabanı gereksinimlerine ve kurumsal gereksinimlerinize ve ilkelerinize bağlı olarak, buluta geçişinizi planlarken en iyi seçim olmayabilir.

## <a name="when-to-move-your-original-rdbms-to-a-vm-iaas"></a>Orijinal RDBMS'nizi VM'ye (IaaS) ne zaman taşıyın?

Geçiş seçeneklerinizden biri, Oracle, IBM DB2, MySQL, PostgreSQL veya SQL Server gibi özgün ilişkisel veritabanı yönetim sisteminizi (RDBMS) Azure VM'de çalışan benzer bir sunucuya taşımaktır. En az değişiklikle buluta en hızlı geçişi gerektiren veya hiç değişiklik yapmayan varolan uygulamalarınız varsa, buluttaki IaaS'ye doğrudan geçiş adil bir seçenek olabilir. Bulutun tüm avantajlarından yararlanmanın en iyi yolu olmayabilir, ancak muhtemelen en hızlı başlangıç yoludur.

Şu anda Microsoft Azure, IaaS VM olarak dağıtılan [331 farklı veritabanı sunucusuna](https://azuremarketplace.microsoft.com/marketplace/apps/category/databases?page=1&subcategories=databases-all) kadar destekler. Bunlar arasında SQL Server, Oracle, MySQL, PostgreSQL ve IBM DB2 gibi popüler RDBMS ve MongoDB, Cassandra, DataStax, MariaDB ve Cloudera gibi diğer birçok NoSQL veritabanı bulunmaktadır.

> [!NOTE]
> RDBMS'nizi bir Azure VM'sine taşımak verilerinizi buluta geçirmenin en hızlı yolu olsa da (IaaS olduğundan), bu yaklaşım BT ekiplerinize (veritabanı yöneticileri ve BT uzmanları) önemli bir yatırım gerektirir. Kurumsal ekiplerin SQL Server için yüksek kullanılabilirlik, olağanüstü durum kurtarma ve yama ayarlamayı ve yönetebilmeleri gerekir. Bu bağlamda da tam yönetim hakları ile özelleştirilmiş bir ortam gerekir.

## <a name="when-to-migrate-to-sql-server-as-a-vm-iaas"></a>VM (IaaS) olarak SQL Server'a ne zaman geçirilir?

Normal bir VM olarak SQL Server'a geçiş yapmanız gereken birkaç servis olabilir. Örnek bir senaryo, SQL Server Reporting Services kullanmanız gerekiyorsa. Ancak çoğu durumda, Azure SQL Veritabanı Yönetilen Örneği şirket içi SQL sunucularından geçirmek için ihtiyacınız olan her şeyi sağlayabilir, bu nedenle SQL Server VM'ye geçiş denemek için son çareniz olmalıdır.

## <a name="use-azure-database-migration-service-to-migrate-your-relational-databases-to-azure"></a>İlişkisel veritabanlarınızı Azure'a geçirmek için Azure Veritabanı Geçiş Hizmeti'ni kullanın

Hedef veritabanınız Azure SQL Veritabanı, Azure SQL Veritabanı Yönetilen Örneği veya SQL Server olsun, SQL Server, Oracle ve MySQL gibi ilişkisel veritabanlarını Azure'a geçirmek için Azure Veritabanı Geçiş Hizmeti'ni kullanabilirsiniz.

Değerlendirme raporlamasıyla birlikte otomatik iş akışı, veritabanını geçirmeden önce yapmanız gereken değişiklikler de size yol eder. Hazır olduğunuzda, hizmet kaynak veritabanını Azure'a geçirtir.

Özgün bir RDBMS'yi değiştirdiğinizde, yeniden test etmeniz gerekebilir. Ayrıca, test sonuçlarına bağlı olarak uygulamanızdaki SQL cümlelerini veya Object-Relational Mapping (ORM) kodunu değiştirmeniz gerekebilir.

Başka bir veritabanınız varsa (örneğin IBM DB2) ve kaldırma ve kaydırma yaklaşımını tercih ediyorsanız, daha karmaşık bir veri geçişi gerçekleştirmek istemiyorsanız, bu veritabanlarını Azure'da IaAS VM olarak kullanmaya devam etmek isteyebilirsiniz. Yeni şema ve farklı programlama kitaplıkları ile farklı bir veritabanı türüne geçiş olacağınız için daha karmaşık bir veri geçişi için ek çaba gerekir.

Azure Veritabanı Geçiş Hizmeti'ni kullanarak veritabanlarını nasıl geçirteceklerini öğrenmek için Azure [SQL Veritabanı Yönetilen Örneği ve Azure Veritabanı Geçiş Hizmeti ile buluta daha hızlı ulaşın'a](https://channel9.msdn.com/Events/Build/2017/P4008)bakın.

## <a name="additional-resources"></a>Ek kaynaklar

- **Bulut SQL Server seçeneğini seçin: Azure VM'de Azure SQL Veritabanı (PaaS) veya SQL Server (IaaS)**

    <https://docs.microsoft.com/azure/sql-database/sql-database-paas-vs-sql-server-iaas>

- **Azure SQL DB Yönetilen Örnek ve Veritabanı Geçiş Hizmeti ile buluta daha hızlı ulaşın**

    <https://channel9.msdn.com/Events/Build/2017/P4008>

- **SQL Server veritabanını buluttaki SQL Veritabanına taşıma**

    <https://docs.microsoft.com/azure/sql-database/sql-database-cloud-migrate>

- **Azure SQL Veritabanı**

    <https://azure.microsoft.com/services/sql-database/?v=16.50>

- **Sanal makinelerde SQL Server**

    <https://azure.microsoft.com/services/virtual-machines/sql-server/>

> [!div class="step-by-step"]
> [Önceki](lift-and-shift-existing-apps-azure-iaas.md)
> [Sonraki](modernize-existing-apps-to-cloud-optimized/index.md) <!-- Next Chapter -->
