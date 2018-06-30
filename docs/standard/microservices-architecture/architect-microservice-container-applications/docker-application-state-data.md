---
title: Durum ve Docker uygulamalarda verileri
description: Kapsayıcılı .NET uygulamaları için .NET mikro mimarisi | Durum ve Docker uygulamalarda verileri
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/18/2017
ms.openlocfilehash: 1469038af29167f7dbb1a161b951eee742cf4bec
ms.sourcegitcommit: 979597cd8055534b63d2c6ee8322938a27d0c87b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/29/2018
ms.locfileid: "37105624"
---
# <a name="state-and-data-in-docker-applications"></a>Durum ve Docker uygulamalarda verileri

Çoğu durumda, kapsayıcı bir işlem örneği olarak düşünebilirsiniz. Bir işlem kalıcı durumunu tutmaz. Yerel depolama alanı için bir kapsayıcı yazabilirsiniz olsa da, bir örneği çevresinde süresiz olarak olacağını varsayılarak bellek tek bir konumda dayanıklı olmasını varsayılarak gibi olacaktır. İşlemleri gibi kapsayıcı görüntüleri kabul birden çok örneğe sahip veya bunlar sonunda sonlandırılacak; bir kapsayıcı orchestrator ile yönetilen varsa, bunlar bir düğüm veya VM diğerine taşınabilir olduğunu kabul edilmelidir.

Docker adlı bir özellik sağlar *kaplama dosya sistemi*. Depoları kapsayıcı kök dosya sistemine bilgi güncelleştirilmiş bir yazarken kopyalama görevi uygular. Bu ayrıca kapsayıcı dayandığı özgün görüntüsüne bilgilerdir. Kapsayıcı sistemden silinirse, bu değişiklikler kaybolur. Yerel depolama alanı içindeki bir kapsayıcı durumunu kaydetmek mümkün olsa da, bu nedenle, bu geçici bir sistem tasarlama, durum bilgisiz varsayılan kapsayıcı tasarım, şirket içi ile çakışabilir.

Aşağıdaki çözümlerde, Docker uygulamaları kalıcı verileri yönetmek için kullanılır:

-   [Veri birimleri](https://docs.docker.com/engine/tutorials/dockervolumes/) ana bilgisayara bağlayın.

-   [Veri birim kapsayıcıları](https://docs.docker.com/engine/tutorials/dockervolumes/#creating-and-mounting-a-data-volume-container) dış bir kapsayıcı kullanılarak kapsayıcıları arasında paylaşılan depolama birimi sağlayın.

-   [Birim eklentileri](https://docs.docker.com/engine/tutorials/dockervolumes/) uzun vadeli Kalıcılık sağlayan uzak Hizmetleri birimlere bağlayın.

-   [Azure depolama](https://docs.microsoft.com/azure/storage/), coğrafi dağıtılabilir depolama kapsayıcıları için iyi bir uzun vadeli Kalıcılık çözüm sağlayarak, sağlar.

-   Uzak ilişkisel veritabanları ister [Azure SQL veritabanı](https://azure.microsoft.com/services/sql-database/) veya NoSQL veritabanları [Azure Cosmos DB](https://docs.microsoft.com/azure/cosmos-db/introduction), veya önbellek gibi hizmetler [Redis](https://redis.io/).

Bu seçenekler hakkında daha fazla ayrıntı sağlar.

**Veri birimleri** olan konak işletim sistemi kapsayıcıları dizinlerde eşlenmiş dizinleri. Ne zaman kapsayıcı kodda erişim gerçekte konak işletim sistemi için bir dizin için dizin, erişimi vardır. Bu dizin için Kapsayıcının kendisi, kullanım ömrü bağlı değildir ve doğrudan konak üzerinde işletim sistemi çalıştıran kodundan dizin erişilebilir veya başka bir kapsayıcı, aynı ana dizin kendisine eşler. Bu nedenle, veri birimleri, veri kapsayıcısı'nın ömrü bağımsız olarak devam ettirmek için tasarlanmıştır. Bir kapsayıcı silmek ya da veri Docker ana görüntüden kalıcı hale veri hacmi silinmez. Bir birimdeki veriler ana bilgisayardan işletim sistemi de erişilebilir.

**Veri birim kapsayıcıları** normal veri birimlerini bir evrimi olan. Veri birim kapsayıcısı içindeki bir veya daha fazla veri birimlerini içeren basit bir kapsayıcıdır. Veri birim kapsayıcısı, bir merkezi bağlama noktası kapsayıcılara erişim sağlar. Bu yöntem veri erişimi, özgün verilerin konumu soyutlar olduğundan kullanışlıdır. Uygulamanın kapsayıcıları yaşam döngüsü bağımsız olarak ayrılmış bu kapsayıcıda kalıcı veriler için dışındaki davranışını normal veri biriminin benzer.

Şekil 4-5'te gösterildiği gibi normal Docker birim kapsayıcıları kendilerini dışında ancak VM veya konak sunucunun fiziksel sınırları içinde depolanabilir. Ancak, Docker kapsayıcıları bir birimi bir konak sunucusu veya VM diğerine erişemez. Diğer bir deyişle, bu birimler, farklı Docker ana bilgisayarda çalıştırılan kapsayıcıları arasında paylaşılan verileri yönetmek mümkün değil

![](./media/image5.png)

**Şekil 4-5**. Veri birimleri ve kapsayıcı tabanlı uygulamalar için dış veri kaynakları

Docker kapsayıcıları bir orchestrator tarafından yönetildiğinde ek olarak, kapsayıcıları "Küme tarafından gerçekleştirilen iyileştirmeler bağlı olarak ana bilgisayar arasında taşımak". Bu nedenle, iş verilerini veri birimlerini kullanmak önerilmez. Ancak izleme dosyaları, zamana bağlı dosyaları ile çalışmak için iyi bir mekanizma oldukları veya benzer, iş veri tutarlılığını etkilemez.

**Birim eklentileri** gibi [Flocker](https://clusterhq.com/flocker/) bir kümedeki tüm ana bilgisayarlar arasında veri erişim sağlar. Tüm birim eklentileri eşit olarak oluşturulur, birim eklentileri genellikle externalized kalıcı güvenilir depodan değişmez kapsayıcıları sağlar.

**Uzak Veri kaynaklarını ve önbellek** Azure SQL Database, Azure Cosmos DB veya Redis kullanılabilir gibi uzak bir önbellek gibi araçlar kapsayıcılı uygulamaları bunlar kullanılır kapsayıcıları geliştirirken aynı şekilde. Bu, iş uygulama verilerini depolamak için kanıtlanmış bir yoludur.

**Azure depolama.** İş verileri genellikle dış kaynaklara veya veritabanları, Azure depolama gibi yerleştirilmesi gerekir. Azure depolama, somut, bulutta aşağıdaki hizmetleri sağlar:

-   BLOB storage yapılandırılmamış nesne verilerini depolar. Bir blob herhangi bir belge veya medya dosyaları (görüntüleri, ses ve video dosyaları) gibi metin veya ikili veri türü olabilir. BLOB storage ayrıca nesne depolama olarak adlandırılır.

-   File storage standart SMB protokolünü kullanan eski uygulamalar için paylaşılan depolama alanı sağlar. Azure virtual machines ve cloud services bağlı paylaşımlar üzerinden uygulama bileşenleri arasında dosya verileri paylaşabilir. Şirket içi uygulamalar dosya hizmeti REST API'si üzerinden dosya verilerine erişebilir.

-   Table storage yapılandırılmış veri kümelerini depolar. Tablo depolama hızlı geliştirme ve çok miktarda veri hızlı erişim sağlayan bir NoSQL anahtar özniteliği veri deposudur.

**İlişkisel veritabanları ve NoSQL veritabanı.** Azure Cosmos DB, MongoDB, vb. gibi SQL Server, PostgreSQL, Oracle veya NoSQL veritabanları gibi ilişkisel veritabanlarından dış veritabanları için birçok seçeneğiniz vardır. Bu veritabanları, tamamen farklı bir konu olduğundan bu kılavuz bir parçası olarak açıklanması yapmayacağınız.


>[!div class="step-by-step"]
[Önceki](containerize-monolithic-applications.md)
[sonraki](service-oriented-architecture.md)
