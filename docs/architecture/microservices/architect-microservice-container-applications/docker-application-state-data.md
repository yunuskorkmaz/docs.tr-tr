---
title: Docker uygulamalarında durum ve veriler
description: Docker uygulamalarında durum ve veri yönetimi. Mikro hizmet örnekleri anlaşılabilir, ancak VERILER, mikro hizmetler ile nasıl işlenir.
ms.date: 09/20/2018
ms.openlocfilehash: 1157ea3c4ca8fc389769308cc0a1141b5f92bb88
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72771435"
---
# <a name="state-and-data-in-docker-applications"></a>Docker uygulamalarında durum ve veriler

Çoğu durumda, bir kapsayıcıyı bir işlem örneği olarak düşünebilirsiniz. İşlem kalıcı durumu korumaz. Bir kapsayıcı yerel depolama alanına yazabilirken, bir örneğin sonsuza kadar bir yerde olacağı varsayılırsa, bellekte tek bir konumun dayanıklı olacağını varsaymış oluyordu. Süreçler gibi kapsayıcı görüntülerinin birden çok örneğe sahip olduğunu veya sonunda sonlandırdığını varsaymalısınız. Bir kapsayıcı Orchestrator ile yönetilmiyorsa, bunların bir düğümden veya VM 'den diğerine taşınabileceğini varsaymalısınız.

Docker uygulamalarındaki verileri yönetmek için aşağıdaki çözümler kullanılır:

Docker ana bilgisayarında [Docker birimleri](https://docs.docker.com/engine/admin/volumes/)olarak:

- **Birimler** , Docker tarafından yönetilen ana bilgisayar FileSystem ' ın bir alanında depolanır.

- **BIND takar** , ana bilgisayar dosya sisteminde herhangi bir klasöre eşlenir, bu nedenle Access Docker işleminden denetlenemez ve bir kapsayıcı hassas işletim sistemi klasörlerine erişebiliyorsa güvenlik riskine neden olabilir.

- **tmpfs takar** , yalnızca konağın belleğinde bulunan ve dosya sistemine hiçbir şekilde yazılmakta olan sanal klasörlere benzer.

Uzak depolama 'dan:

- Kapsayıcılar için iyi bir uzun süreli kalıcı çözüm sağlayan coğrafi dağıtılabilir depolama sağlayan [Azure depolama](https://azure.microsoft.com/documentation/services/storage/).

- [Azure SQL veritabanı](https://azure.microsoft.com/services/sql-database/) gibi uzak ilişkisel veritabanları veya [Azure Cosmos DB](https://docs.microsoft.com/azure/cosmos-db/introduction)gibi NoSQL veritabanları ya da [redin](https://redis.io/)gibi önbellek hizmetleri.

Docker kapsayıcısından:

- **Dosya sisteminin yerini**. Bu Docker özelliği, güncelleştirilmiş bilgileri kapsayıcının kök dosya sistemine depolayan bir kopyalama yazma görevi uygular. Bu bilgiler, kapsayıcının temel aldığı orijinal görüntünün "en üstünde" olur. Kapsayıcı sistemden silinirse, bu değişiklikler kaybolur. Bu nedenle, bir kapsayıcının durumunu yerel depolama alanına kaydetmek mümkün olsa da, bunun etrafında bir sistem tasarlamak, varsayılan olarak durum bilgisiz olan kapsayıcı tasarımı ile çakışır.

Ancak Docker birimlerinin kullanılması artık Docker 'daki yerel verileri işlemek için tercih edilen yoldur. Kapsayıcılarda depolama hakkında daha fazla bilgiye ihtiyacınız varsa [Docker depolama sürücülerinde](https://docs.docker.com/storage/storagedriver/select-storage-driver/) ve [depolama sürücüleri hakkında](https://docs.docker.com/storage/storagedriver/)' yı denetleyin.

Aşağıda bu seçenekler hakkında daha fazla ayrıntı verilmiştir:

**Birimler** , konak işletim sisteminden kapsayıcılardaki dizinlere eşlenmiş dizinlerdir. Kapsayıcıdaki kodun dizine erişimi olduğunda, bu erişim aslında ana bilgisayar IŞLETIM sistemindeki bir dizin olur. Bu dizin kapsayıcının kullanım ömrüne bağlı değildir ve Dizin Docker tarafından yönetilir ve konak makinenin temel işlevselliğinden yalıtılmıştır. Bu nedenle, veri birimleri kapsayıcının ömründen bağımsız olarak verileri kalıcı hale getirmek için tasarlanmıştır. Docker ana bilgisayarındaki bir kapsayıcıyı veya görüntüyü silerseniz, veri biriminde kalıcı olan veriler silinmez.

Birimler adlandırılmış veya anonim olabilir (varsayılan). Adlandırılmış birimler, **veri hacmi kapsayıcıları** evrimi ve kapsayıcılar arasında veri paylaşmayı kolaylaştırır. Birimler ayrıca, diğer seçenekler arasında, uzak konaklarda veri depolamanıza olanak tanıyan birim sürücülerini destekler.

**Bağlama bağlamalarda** uzun bir süre önce kullanılabilir ve bir kapsayıcıdaki bağlama noktasına herhangi bir klasörün eşlenmesinden izin verilir. BIND takmalar, birimlerden ve bazı önemli güvenlik sorunlarından daha fazla sınırlamalara sahiptir, bu nedenle birimler önerilen seçenektir.

**tmpfs takar** , yalnızca konağın belleğinde yaşayan ve dosya sistemine hiçbir şekilde yazılmakta olan temel sanal klasörlerdir. Bunlar hızlı ve güvenlidir, ancak bellek kullanır ve yalnızca geçici ve kalıcı olmayan veriler için tasarlanmıştır.

Şekil 4-5 ' de gösterildiği gibi, normal Docker birimleri kapsayıcı dışında, ancak konak sunucusunun veya VM 'nin fiziksel sınırları içinde depolanabilir. Ancak, Docker Kapsayıcıları bir konak sunucusundan veya VM 'den diğerine bir birime erişemez. Diğer bir deyişle, bu birimlerle, farklı Docker konaklarında çalışan kapsayıcılar arasında paylaşılan verileri yönetmek mümkün değildir, ancak uzak konakları destekleyen bir birim sürücüsüyle elde edilebilir.

![Kapsayıcı tabanlı uygulamalar için birimleri ve dış veri kaynaklarını gösteren diyagram.](./media/docker-application-state-data/volumes-external-data-sources.png)

**Şekil 4-5**. Kapsayıcı tabanlı uygulamalar için birimler ve dış veri kaynakları

Birimler, uzak konakları destekleyen uzak bir sürücü kullanmadığınız müddetçe, kapsayıcılar arasında yalnızca aynı konakta paylaşılabilir. Ayrıca, Docker Kapsayıcıları bir Orchestrator tarafından yönetildiğinde, küme tarafından gerçekleştirilen iyileştirmelere bağlı olarak kapsayıcılar, konaklar arasında "taşıyabilir". Bu nedenle, iş verileri için veri birimleri kullanmanız önerilmez. Ancak, iş verilerinin tutarlılığını etkilemeyecek şekilde izleme dosyaları, zamana bağlı dosyalar veya benzer şekilde çalışmak için iyi bir mekanizmadır.

Azure SQL veritabanı, Azure Cosmos DB veya redde gibi uzak bir önbellek gibi **uzak veri kaynakları ve önbellek** araçları, kapsayıcısız geliştirilirken aynı şekilde Kapsayıcılı uygulamalarda kullanılabilir. Bu, iş uygulaması verilerinin depolanması için kendini kanıtlamış bir yoldur.

**Azure depolama.** İş verilerinin genellikle Azure depolama gibi dış kaynaklara veya veritabanlarına yerleştirilmesi gerekir. Azure depolama, somut bir şekilde bulutta aşağıdaki hizmetleri sağlar:

- Blob Storage yapılandırılmamış nesne verilerini depolar. Blob, belge veya medya dosyaları (görüntüler, ses ve video dosyaları) gibi herhangi bir tür metin veya ikili veri olabilir. BLOB depolama alanı da nesne depolama olarak adlandırılır.

- Dosya depolama, standart SMB protokolünü kullanarak eski uygulamalar için paylaşılan depolama alanı sağlar. Azure sanal makineleri ve bulut Hizmetleri, bağlı paylaşımlar aracılığıyla uygulama bileşenleri arasında dosya verilerini paylaşabilir. Şirket içi uygulamalar dosya hizmeti REST API aracılığıyla bir paylaşımdaki dosya verilerine erişebilir.

- Tablo depolama, yapılandırılmış veri kümelerini depolar. Tablo depolama, çok büyük miktarlarda veriye hızlı geliştirme ve hızlı erişim sağlayan bir NoSQL anahtar özniteliği veri deposudur.

**İlişkisel veritabanları ve NoSQL veritabanları.** Dış veritabanları için SQL Server, PostgreSQL, Oracle veya Azure Cosmos DB, MongoDB gibi NoSQL veritabanları gibi çok sayıda seçenek vardır. Bu veritabanları tamamen farklı bir konu içinde olduklarından bu kılavuzun bir parçası olarak açıklanmıyor.

>[!div class="step-by-step"]
>[Önceki](containerize-monolithic-applications.md)
>[İleri](service-oriented-architecture.md)
