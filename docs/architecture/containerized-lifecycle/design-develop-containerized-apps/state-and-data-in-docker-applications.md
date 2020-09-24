---
title: Docker uygulamalarında durum ve veriler
description: Kapsayıcılı uygulamalarda durumu kaydetmek için kullanılabilir seçeneğini öğrenin.
ms.date: 08/06/2020
ms.openlocfilehash: d55519e9340ec06588c2dae3e7363d03f263ce39
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91163472"
---
# <a name="state-and-data-in-docker-applications"></a>Docker uygulamalarında durum ve veriler

Çoğu durumda, bir kapsayıcıyı bir işlem örneği olarak düşünebilirsiniz. Bir işlem kalıcı durumu korumaz. Bir kapsayıcı yerel depolama alanına yazabilirken, bir örneğin süresiz olarak, bellekteki tek bir konumun dayanıklı olacağını varsayarsak. İşlem gibi kapsayıcı görüntüleri, birden çok örneğe sahip olduğu ve sonunda sonlandırdığı varsayılacaktır. bir kapsayıcı Orchestrator ile yönetiliyorsa, bir düğümden veya VM 'den diğerine taşınabileceği varsayılır.

Docker uygulamalarında kalıcı verileri yönetmek için aşağıdaki çözümler kullanılır:

Docker ana bilgisayarında [Docker birimleri](https://docs.docker.com/engine/admin/volumes/)olarak:

- **Birimler** , Docker tarafından yönetilen ana bilgisayar FileSystem ' ın bir alanında depolanır.

- **BIND takar** , ana bilgisayar dosya sisteminde herhangi bir klasöre eşlenir, bu nedenle Access bir Docker işleminden denetlenemez ve bir kapsayıcı hassas işletim sistemi klasörlerine erişebiliyorsa güvenlik riskine neden olabilir.

- **tmpfs takar** , yalnızca konağın belleğinde bulunan ve dosya sistemine hiçbir şekilde yazılmakta olan sanal klasörlere benzer.

Uzak depolama 'dan:

- [Azure depolama](https://azure.microsoft.com/documentation/services/storage/) , kapsayıcılar için iyi bir uzun süreli kalıcı çözüm sağlayan coğrafi dağıtılabilir depolama sağlar.

- [Azure SQL veritabanı](https://azure.microsoft.com/services/sql-database/)gibi uzak ilişkisel veritabanları, [Azure Cosmos DB](/azure/cosmos-db/introduction)gibi NoSQL veritabanları veya [redin](https://redis.io/)gibi önbellek hizmetleri.

Docker kapsayıcısından:

- Docker, *kaplama dosya sistemi*adlı bir özellik sağlar. Bu özellik, güncelleştirilmiş bilgileri kapsayıcının kök dosya sistemine depolayan bir yazma kopyalama görevi uygular. Bu bilgiler, kapsayıcının temel aldığı orijinal görüntünün "üzerine yerleştirir". Kapsayıcı sistemden silinirse, bu değişiklikler kaybolur. Bu nedenle, bir kapsayıcının durumunu yerel depolama alanına kaydetmek mümkün olsa da, bu özelliği temel alan bir sistem tasarlamak kapsayıcı tasarımı Şirket adıyla çakışarak varsayılan olarak durum bilgisiz olur.

- Ancak Docker birimleri artık Docker 'daki yerel verileri işlemek için tercih edilen yoldur. Kapsayıcılarda depolama hakkında daha fazla bilgiye ihtiyacınız varsa [Docker depolama sürücülerini](https://docs.docker.com/engine/userguide/storagedriver/) ve [görüntüler, kapsayıcılar ve depolama sürücüleri hakkında](https://docs.docker.com/engine/userguide/storagedriver/imagesandcontainers/)' yı denetleyin.

Aşağıdakiler, bu seçenekler hakkında ek ayrıntılar sağlar.

**Birimler** , konak işletim sisteminden kapsayıcılardaki dizinlere eşlenmiş dizinlerdir. Kapsayıcıdaki kodun dizine erişimi olduğunda, bu erişim aslında ana bilgisayar IŞLETIM sistemindeki bir dizin olur. Bu dizin kapsayıcının kullanım ömrüne bağlı değildir ve Dizin Docker tarafından yönetilir ve konak makinenin temel işlevselliğinden yalıtılmıştır. Bu nedenle, veri birimleri kapsayıcının ömründen bağımsız olarak verileri kalıcı hale getirmek için tasarlanmıştır. Docker ana bilgisayarındaki bir kapsayıcıyı veya görüntüyü silerseniz, veri biriminde kalıcı olan veriler silinmez.

Birimler adlandırılmış veya anonim olabilir (varsayılan). Adlandırılmış birimler, **veri hacmi kapsayıcıları** evrimi ve kapsayıcılar arasında veri paylaşmayı kolaylaştırır. Birimler ayrıca, diğer seçenekler arasında, uzak konaklarda veri depolamanıza olanak tanıyan birim sürücülerini destekler.

**Bağlama bağlamalarda** uzun bir süre kullanılabilir ve bir kapsayıcıdaki bağlama noktasına herhangi bir klasörün eşlenmesiyle izin veriyor. BIND takmalar, birimlerden ve bazı önemli güvenlik sorunlarından daha fazla sınırlamalara sahiptir, bu nedenle birimler önerilen seçenektir.

** `tmpfs` takar** yalnızca konağın belleğinde yaşayan ve dosya sistemine hiçbir şekilde yazılmakta olan sanal klasörlerdir. Bunlar hızlı ve güvenlidir, ancak bellek kullanır ve yalnızca kalıcı olmayan veriler için tasarlanmıştır.

Şekil 4-5 ' de gösterildiği gibi, normal Docker birimleri kapsayıcı dışında, ancak konak sunucusunun veya VM 'nin fiziksel sınırları içinde depolanabilir. Ancak, Docker Kapsayıcıları bir birime bir konak sunucusundan veya VM 'den diğerine erişemez. Diğer bir deyişle, bu birimlerle, farklı Docker konaklarında çalışan kapsayıcılar arasında paylaşılan verileri yönetmek mümkün değildir, ancak uzak konakları destekleyen bir birim sürücüsüyle elde edilebilir.

![Kapsayıcılar dışında depolanan Docker birimlerinin gösterildiği diyagram.](./media/state-and-data-in-docker-applications/container-based-application-external-data-sources.png)

**Şekil 4-5**. Kapsayıcı tabanlı uygulamalar için birimler ve dış veri kaynakları

Ayrıca, Docker Kapsayıcıları bir Orchestrator tarafından yönetildiğinde, küme tarafından gerçekleştirilen iyileştirmelere bağlı olarak kapsayıcılar, konaklar arasında "taşıyabilir". Bu nedenle, iş verileri için veri birimleri kullanmanız önerilmez. Ancak, iş verilerinin tutarlılığını etkilemeyecek izleme dosyaları, zamana bağlı dosyalar veya benzer şekilde çalışmak için iyi bir mekanizmadır.

Azure SQL veritabanı, Azure Cosmos DB veya redde gibi uzak bir önbellek gibi **uzak veri kaynakları ve önbellek** araçları, kapsayıcısız geliştirilirken aynı şekilde Kapsayıcılı uygulamalarda kullanılabilir. Bu, iş uygulaması verilerinin depolanması için kendini kanıtlamış bir yoldur.

**Azure depolama.** İş verilerinin genellikle Azure depolama gibi dış kaynaklara veya veritabanlarına yerleştirilmesi gerekir. Azure depolama, bulutta aşağıdaki hizmetleri sağlar:

- Blob Storage yapılandırılmamış nesne verilerini depolar. Blob, belge veya medya dosyaları (görüntüler, ses ve video dosyaları) gibi herhangi bir tür metin veya ikili veri olabilir. Blob Storage ayrıca Nesne depolama olarak adlandırılır.

- Dosya depolama, standart SMB protokolünü kullanarak eski uygulamalar için paylaşılan depolama alanı sağlar. Azure sanal makineleri ve bulut Hizmetleri, bağlı paylaşımlar aracılığıyla uygulama bileşenleri arasında dosya verilerini paylaşabilir. Şirket içi uygulamalar dosya hizmeti REST API aracılığıyla bir paylaşımdaki dosya verilerine erişebilir.

- Tablo depolama, yapılandırılmış veri kümelerini depolar. Tablo depolama, çok büyük miktarlarda veriye hızlı geliştirme ve hızlı erişim sağlayan bir NoSQL anahtar özniteliği veri deposudur.

**İlişkisel veritabanları ve NoSQL veritabanları.** Dış veritabanları için SQL Server, PostgreSQL, Oracle veya Azure Cosmos DB, MongoDB gibi NoSQL veritabanları gibi çok sayıda seçenek vardır. Bu veritabanları, farklı bir konu olduğundan, bu kılavuzun bir parçası olarak açıklanmıyor.

>[!div class="step-by-step"]
>[Önceki](monolithic-applications.md) 
> [Sonraki](soa-applications.md)
