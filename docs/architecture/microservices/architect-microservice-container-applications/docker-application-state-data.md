---
title: Docker uygulamalarında durum ve veriler
description: Docker uygulamalarında devlet ve veri yönetimi. Microservice örnekleri harcanabilir, ancak DATA Değİl, nasıl microservices ile bu işlemek için.
ms.date: 09/20/2018
ms.openlocfilehash: 1157ea3c4ca8fc389769308cc0a1141b5f92bb88
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "72771435"
---
# <a name="state-and-data-in-docker-applications"></a>Docker uygulamalarında durum ve veriler

Çoğu durumda, bir kapsayıcı bir işlem örneği olarak düşünebilirsiniz. Bir işlem kalıcı durumu korumaz. Bir kapsayıcı yerel depolama yazabilir iken, bir örnek süresiz olarak etrafında olacağını varsayarak bellekte tek bir konumu dayanıklı olacağını varsayarak gibi olacaktır. İşlemler gibi kapsayıcı görüntülerinin birden çok örneği olduğunu veya sonunda öldürüleceğini varsaymalısınız. Bir konteyner orkestratörü ile yönetilirlerse, bir düğümden veya VM'den diğerine taşınabileceklerini varsaymalısınız.

Docker uygulamalarındaki verileri yönetmek için aşağıdaki çözümler kullanılır:

Docker ev sahibinden, [Docker Volumes](https://docs.docker.com/engine/admin/volumes/)olarak:

- **Birimler,** docker tarafından yönetilen ana bilgisayar dosya sisteminin bir alanında depolanır.

- **Bağlama yuvaları** ana bilgisayar dosya sistemindeki herhangi bir klasöre eşleyebilir, bu nedenle erişim Docker işleminden denetlenebilir ve bir kapsayıcı hassas işletim sistemi klasörlerine erişebildiği için güvenlik riski oluşturabilir.

- **tmpfs bağlar** yalnızca ana bilgisayar belleğinde var olan ve dosya sistemine asla yazılmayan sanal klasörler gibidir.

Uzak depolamadan:

- Coğrafi olarak dağıtılabilir depolama sağlayan [Azure Depolama,](https://azure.microsoft.com/documentation/services/storage/)kapsayıcılar için iyi bir uzun vadeli kalıcılık çözümü sağlar.

- [Azure SQL Veritabanı](https://azure.microsoft.com/services/sql-database/) veya Azure [Cosmos DB](https://docs.microsoft.com/azure/cosmos-db/introduction)gibi NoSQL veritabanları veya [Redis](https://redis.io/)gibi önbellek hizmetleri gibi uzak ilişkisel veritabanları.

Docker konteynerinden:

- **Bindirme Dosya Sistemi**. Bu Docker özelliği, güncelleştirilmiş bilgileri kapsayıcının kök dosya sistemine depolayan bir yazma üzerine kopyalama görevi uygular. Bu bilgiler, kapsayıcının dayandığı orijinal görüntünün "üstünde" dir. Kapsayıcı sistemden silinirse, bu değişiklikler kaybolur. Bu nedenle, yerel depolama içinde bir kapsayıcının durumunu kaydetmek mümkün olsa da, bunun etrafında bir sistem tasarlamak varsayılan olarak durum dışı olan kapsayıcı tasarımı öncülüyle çakışacak.

Ancak, Docker Volumes'i kullanmak artık Docker'daki yerel verileri işlemenin tercih edilen yoludur. Kapsayıcılarda depolama hakkında daha fazla bilgiye ihtiyacınız varsa [Docker depolama sürücüleri](https://docs.docker.com/storage/storagedriver/select-storage-driver/) ve depolama sürücüleri [hakkında](https://docs.docker.com/storage/storagedriver/)kontrol edin.

Aşağıdaki, bu seçenekler hakkında daha fazla ayrıntı sağlar:

**Birimler,** barındırılan işletim sisteminden kapsayıcıdaki dizinlere eşlenen dizinlerdir. Kapsayıcıdaki kod dizine erişesahipse, bu erişim aslında ana bilgisayar işletim sistemi üzerindeki bir dizine erişimdir. Bu dizin kapsayıcının ömrüne bağlı değildir ve dizin Docker tarafından yönetilir ve ana makinenin temel işlevselliğinden izole edilir. Böylece, veri hacimleri, verileri kapsayıcının ömründen bağımsız olarak devam etmek üzere tasarlanmıştır. Docker ana bilgisayarından bir kapsayıcıyı veya görüntüyü silerseniz, veri hacminde kalıcı veriler silinmez.

Birimler adlandırılmış veya anonim (varsayılan). Adlandırılmış **birimler, Veri Hacmi Kapsayıcılarının** evrimidir ve verileri kapsayıcılar arasında paylaşmayı kolaylaştırır. Birimler, diğer seçeneklerin yanı sıra uzak ana bilgisayarlarda veri depolamanızı sağlayan birim sürücülerini de destekler.

**Bağlama bağları** uzun zaman önce kullanılabilir ve herhangi bir klasörün bir kapsayıcıdaki montaj noktasına eşlemesine izin verir. Bağlama bağları, birimlerden ve bazı önemli güvenlik sorunlarından daha fazla sınırlamaya sahiptir, bu nedenle birimler önerilen seçenektir.

**tmpfs bağlar** temelde yalnızca ana bilgisayar belleğinde yaşayan ve dosya sistemine asla yazılmayan sanal klasörlerdir. Bunlar hızlı ve güvenlidir, ancak bellek kullanırlar ve yalnızca geçici, kalıcı olmayan veriler içindirler.

Şekil 4-5'te gösterildiği gibi, normal Docker hacimleri kapsayıcıların dışında, ancak ana bilgisayar sunucusunun veya VM'nin fiziksel sınırları içinde depolanabilir. Ancak, Docker kapsayıcıları bir ana bilgisayar sunucusundan veya VM'den diğerine bir birim erişemez. Başka bir deyişle, bu birimlerile, farklı Docker ana bilgisayarlarında çalışan kapsayıcılar arasında paylaşılan verileri yönetmek mümkün değildir, ancak uzak ana bilgisayarları destekleyen bir ses düzeyi sürücüsüyle elde edilebilir.

![Kapsayıcı tabanlı uygulamalar için hacimleri ve dış veri kaynaklarını gösteren diyagram.](./media/docker-application-state-data/volumes-external-data-sources.png)

**Şekil 4-5**. Kapsayıcı tabanlı uygulamalar için birimler ve dış veri kaynakları

Uzak ana bilgisayarları destekleyen uzak bir sürücü kullanmadığınız sürece, birimler kapsayıcılar arasında ancak yalnızca aynı ana bilgisayarda paylaşılabilir. Buna ek olarak, Docker kapsayıcıları bir orkestratör tarafından yönetildiğinde, kapsayıcılar küme tarafından gerçekleştirilen optimizasyonlara bağlı olarak ana bilgisayarlar arasında "taşınabilir". Bu nedenle, iş verileri için veri birimleri kullanmanız önerilmez. Ancak, iş veri tutarlılığını etkilemeyen izleme dosyaları, zamansal dosyalar veya benzerleriyle çalışmak için iyi bir mekanizmadır.

Azure SQL Veritabanı, Azure Cosmos DB veya Redis gibi uzak **veri kaynakları ve önbellek** araçları, kapsayıcılı uygulamalarda kapsayıcıolmadan geliştirilirken kullanıldıkları gibi kullanılabilir. Bu, iş uygulama verilerini depolamanın kanıtlanmış bir yoludur.

**Azure Depolama.** İş verilerinin genellikle Azure Depolama gibi dış kaynaklara veya veritabanlarına yerleştirilmesi gerekir. Azure Depolama, somut olarak bulutta aşağıdaki hizmetleri sağlar:

- Blob depolama, yapılandırılmamış nesne verilerini depolar. Bir blob, belge veya medya dosyaları (resim, ses ve video dosyaları) gibi her tür metin veya ikili veri olabilir. Blob Storage ayrıca Nesne depolama olarak adlandırılır.

- Dosya depolama, standart SMB protokolü kullanarak eski uygulamalar için paylaşılan depolama alanı sunar. Azure sanal makineleri ve bulut hizmetleri, dosya verilerini monte edilmiş paylaşımlar aracılığıyla uygulama bileşenleri arasında paylaşabilir. Şirket içi uygulamalar, Dosya hizmeti REST API aracılığıyla bir paylaşımdaki dosya verilerine erişebilir.

- Tablo depolama, yapılandırılmış veri kümelerini depolar. Tablo depolama, hızlı geliştirme ve büyük miktarlarda verilere hızlı erişim sağlayan bir NoSQL anahtar öznitelik veri deposudur.

**İlişkisel veritabanları ve NoSQL veritabanları.** SQL Server, PostgreSQL, Oracle veya Azure Cosmos DB, MongoDB gibi NoSQL veritabanları gibi ilişkisel veritabanlarından harici veritabanları için birçok seçenek vardır. Tamamen farklı bir konu olduğu için bu veritabanları bu kılavuzun bir parçası olarak açıklanmaz.

>[!div class="step-by-step"]
>[Önceki](containerize-monolithic-applications.md)
>[Sonraki](service-oriented-architecture.md)
