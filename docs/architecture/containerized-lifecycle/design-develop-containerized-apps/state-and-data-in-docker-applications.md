---
title: Docker uygulamalarında durum ve veriler
description: Kapsayıcı uygulamalarda durum kaydetmek için kullanılabilir seçeneği öğrenin.
ms.date: 02/15/2019
ms.openlocfilehash: b2368efb0eff2bdce48b77b2addcc4de89822c74
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "72394627"
---
# <a name="state-and-data-in-docker-applications"></a>Docker uygulamalarında durum ve veriler

Çoğu durumda, bir kapsayıcı bir işlem örneği olarak düşünebilirsiniz. Bir işlem kalıcı durumu korumaz. Bir kapsayıcı yerel depolama yazabilir iken, bir örnek süresiz olarak etrafında olacağını varsayarak bellekte tek bir konumu dayanıklı olacağını varsayarak gibidir. Kapsayıcı görüntülerinin, süreçler gibi, birden çok örneği olduğu ve sonunda öldürüleceği varsayılmalıdır; bir konteyner orchestrator ile yönetilirse, bir düğüm veya VM'den diğerine taşınabilecekleri varsayılmalıdır.

Docker uygulamalarında kalıcı verileri yönetmek için aşağıdaki çözümler kullanılır:

Docker ev sahibinden, [Docker Volumes](https://docs.docker.com/engine/admin/volumes/)olarak:

- **Birimler,** docker tarafından yönetilen ana bilgisayar dosya sisteminin bir alanında depolanır.

- **Bağlama yuvaları** ana bilgisayar dosya sistemindeki herhangi bir klasöre eşleyebilir, bu nedenle erişim Docker işleminden denetlenebilir ve bir kapsayıcı hassas işletim sistemi klasörlerine erişebildiği için güvenlik riski oluşturabilir.

- **tmpfs bağlar** yalnızca ana bilgisayar belleğinde var olan ve dosya sistemine asla yazılmayan sanal klasörler gibidir.

Uzak depolamadan:

- [Azure Depolama,](https://azure.microsoft.com/documentation/services/storage/) kapsayıcılar için iyi bir uzun vadeli kalıcılık çözümü sağlayarak coğrafi olarak dağıtılabilir depolama sağlar.

- [Azure SQL Veritabanı](https://azure.microsoft.com/services/sql-database/)gibi uzak ilişkisel veritabanları, Azure [Cosmos DB](https://docs.microsoft.com/azure/cosmos-db/introduction)gibi NoSQL veritabanları veya [Redis](https://redis.io/)gibi önbellek hizmetleri.

Docker konteynerinden:

- Docker, *bindirme dosya sistemi*adlı bir özellik sağlar. Bu özellik, güncelleştirilmiş bilgileri kapsayıcının kök dosya sistemine depolayan bir yazma üzerine kopyalama görevi uygular. Bu bilgiler, kapsayıcının temel aldığı orijinal görüntünün "üstüne" yerleştirir. Kapsayıcı sistemden silinirse, bu değişiklikler kaybolur. Bu nedenle, bir kapsayıcının durumunu yerel depolama alanı içinde kaydetmek mümkün olsa da, bu özelliğe dayalı bir sistem tasarlamak, varsayılan olarak durum dışı olan kapsayıcı tasarımıöncüsüyle çakışacak.

- Ancak, Docker Volumes artık Docker'daki yerel verileri işlemenin tercih edilen yoludur. Kapsayıcılarda depolama hakkında daha fazla bilgiye ihtiyacınız varsa, [Docker depolama sürücüleri](https://docs.docker.com/engine/userguide/storagedriver/) ve [görüntüler, kapsayıcılar ve depolama sürücüleri hakkında](https://docs.docker.com/engine/userguide/storagedriver/imagesandcontainers/)kontrol edin.

Aşağıda, bu seçenekler hakkında ek ayrıntı sağlar.

**Birimler,** barındırılan işletim sisteminden kapsayıcıdaki dizinlere eşlenen dizinlerdir. Kapsayıcıdaki kod dizine erişesahipse, bu erişim aslında ana bilgisayar işletim sistemi üzerindeki bir dizine erişimdir. Bu dizin kapsayıcının ömrüne bağlı değildir ve dizin Docker tarafından yönetilir ve ana makinenin temel işlevselliğinden izole edilir. Böylece, veri hacimleri, verileri kapsayıcının ömründen bağımsız olarak devam etmek üzere tasarlanmıştır. Docker ana bilgisayarından bir kapsayıcıyı veya görüntüyü silerseniz, veri hacminde kalıcı veriler silinmez.

Birimler adlandırılmış veya anonim (varsayılan). Adlandırılmış **birimler, Veri Hacmi Kapsayıcılarının** evrimidir ve verileri kapsayıcılar arasında paylaşmayı kolaylaştırır. Birimler, diğer seçeneklerin yanı sıra uzak ana bilgisayarlarda veri depolamanızı sağlayan birim sürücülerini de destekler.

**Bağlama bağları** uzun zamandır kullanılabilir ve herhangi bir klasörün bir konteynerdeki montaj noktasına eşlemesine izin verir. Bağlama bağları, birimlerden ve bazı önemli güvenlik sorunlarından daha fazla sınırlamaya sahiptir, bu nedenle birimler önerilen seçenektir.

bağlar, yalnızca ana bilgisayarbelleğinde yaşayan ve dosya sistemine asla yazılmayan sanal klasörlerdir. ** `tmpfs` ** Onlar hızlı ve güvenli ama bellek kullanımı ve sadece kalıcı olmayan veri içindir.

Şekil 4-5'te gösterildiği gibi, normal Docker hacimleri kapsayıcıların dışında, ancak ana bilgisayar sunucusunun veya VM'nin fiziksel sınırları içinde depolanabilir. Ancak, Docker kapsayıcıları bir ana bilgisayar sunucusundan veya VM'den diğerine bir birim erişemez. Başka bir deyişle, bu birimlerile, farklı Docker ana bilgisayarlarında çalışan kapsayıcılar arasında paylaşılan verileri yönetmek mümkün değildir, ancak uzak ana bilgisayarları destekleyen bir ses düzeyi sürücüsüyle elde edilebilir.

![Kapsayıcıların dışında depolanan Docker birimlerini gösteren diyagram.](./media/state-and-data-in-docker-applications/container-based-application-external-data-sources.png)

**Şekil 4-5**. Kapsayıcı tabanlı uygulamalar için birimler ve dış veri kaynakları

Buna ek olarak, Docker kapsayıcıları bir orkestratör tarafından yönetildiğinde, kapsayıcılar küme tarafından gerçekleştirilen optimizasyonlara bağlı olarak ana bilgisayarlar arasında "taşınabilir". Bu nedenle, iş verileri için veri birimleri kullanmanız önerilmez. Ancak, iş veri tutarlılığını etkilemeyen izleme dosyaları, zamansal dosyalar veya benzerleriyle çalışmak için iyi bir mekanizmadır.

Azure SQL Veritabanı, Azure Cosmos DB veya Redis gibi uzak **veri kaynakları ve önbellek** araçları, kapsayıcılı uygulamalarda kapsayıcıolmadan geliştirilirken kullanıldıkları gibi kullanılabilir. Bu, iş uygulama verilerini depolamanın kanıtlanmış bir yoludur.

**Azure Depolama.** İş verilerinin genellikle Azure Depolama gibi dış kaynaklara veya veritabanlarına yerleştirilmesi gerekir. Azure Depolama bulutta aşağıdaki hizmetleri sağlar:

- Blob depolama, yapılandırılmamış nesne verilerini depolar. Bir blob, belge veya medya dosyaları (resim, ses ve video dosyaları) gibi her tür metin veya ikili veri olabilir. Blob Storage ayrıca Nesne depolama olarak adlandırılır.

- Dosya depolama, standart SMB protokolünü kullanarak eski uygulamalar için paylaşılan depolama alanı sunar. Azure sanal makineleri ve bulut hizmetleri, dosya verilerini monte edilmiş paylaşımlar aracılığıyla uygulama bileşenleri arasında paylaşabilir. Şirket içi uygulamalar, Dosya Hizmeti REST API aracılığıyla bir paylaşımdaki dosya verilerine erişebilir.

- Tablo depolama, yapılandırılmış veri kümelerini depolar. Tablo depolama, hızlı geliştirme ve büyük miktarlarda verilere hızlı erişim sağlayan bir NoSQL anahtar öznitelik veri deposudur.

**İlişkisel veritabanları ve NoSQL veritabanları.** SQL Server, PostgreSQL, Oracle veya Azure Cosmos DB, MongoDB gibi NoSQL veritabanları gibi ilişkisel veritabanlarından harici veritabanları için birçok seçenek vardır. Bu veritabanları tamamen farklı bir konu olduğu için bu kılavuzun bir parçası olarak açıklanmaz.

>[!div class="step-by-step"]
>[Önceki](monolithic-applications.md)
>[Sonraki](soa-applications.md)
