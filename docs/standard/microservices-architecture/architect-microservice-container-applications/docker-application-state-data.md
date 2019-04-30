---
title: Docker uygulamalarında durum ve veriler
description: Docker uygulamalarında durum ve veri yönetimi. Mikro hizmet örnekleri expendable ancak verileri nasıl ile mikro hizmetler bu durumu çözmek değil.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/20/2018
ms.openlocfilehash: 70c3cee8c5fd1e63f2ff869f49b1fb02ab8f59dd
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61689570"
---
# <a name="state-and-data-in-docker-applications"></a>Docker uygulamalarında durum ve veriler

Çoğu durumda, bir kapsayıcı örneği bir işlem olarak düşünebilirsiniz. Bir işlemin durumunu sürekli olarak saklamak değil. Yerel depolama alanı için bir kapsayıcı yazabilirsiniz, ancak örneği çevresinde süresiz olarak olacağı varsayılarak bellek tek bir konumda kalıcı olduğu varsayılarak gibi olacaktır. Gibi işlemler, kapsayıcı görüntüleri birden çok örneğe sahip veya sonunda sonlandırılacak varsaymanız gerekir. Bir kapsayıcı Düzenleyicisi ile yönetildikleri varsa, bunlar bir düğüm veya VM diğerine taşınır, varsaymanız gerekir.

Aşağıdaki çözümlerden Docker uygulamalarında kalıcı verileri yönetmek için kullanılır:

Docker ana bilgisayarından olarak [Docker birimleri](https://docs.docker.com/engine/admin/volumes/):

- **Birimleri** Docker tarafından yönetilen konak dosya sistemine bir bölgede depolanır.

- **Takar bağlama** erişim Docker işlemden kontrol edilemez ve bir kapsayıcı önemli işletim sistemi klasörleri erişebilecek şekilde bir güvenlik riski oluşturabilir, ana bilgisayar dosya sistemi herhangi bir klasörde eşleyebilirsiniz.

- **tmpfs bağlar** yalnızca ana bilgisayarın belleğinde bulunur ve dosya sistemi için hiçbir zaman yazılır sanal klasörler gibi şunlardır.

Uzaktaki depolama biriminden:

- [Azure depolama](https://azure.microsoft.com/documentation/services/storage/), kapsayıcılar için iyi bir uzun vadeli Kalıcılık çözüm sağlayan coğrafi dağıtılabilir depolama sağlar.

- Gibi uzak ilişkisel veritabanları [Azure SQL veritabanı](https://azure.microsoft.com/services/sql-database/) veya gibi NoSQL veritabanları [Azure Cosmos DB](https://docs.microsoft.com/azure/cosmos-db/introduction), veya önbellek gibi hizmetler [Redis](https://redis.io/).

Docker kapsayıcısı'ndan:

> Docker adlı bir özellik sağlar *kaplama dosya sistemi*. Bu depolar kapsayıcısının kök dosya sistemine bilgiler güncelleştirilmiştir yazarken kopyalama görev uygular. Bu bilgileri ayrıca, kapsayıcı temel özgün görüntüsüne olur. Kapsayıcı sistemden silinirse, bu değişiklikler kaybolur. Bir kapsayıcı içinde yerel depolama durumunu kaydetmek mümkün olsa da, bu nedenle, bu geçici bir sistem tasarımı, varsayılan olarak durum bilgisiz olduğundan kapsayıcı tasarım, şirket içi ile çakışıyor.
>
> Ancak, daha önce sunulan Docker birimleri şimdi Docker yerel veri işleme için tercih edilen yoludur. Depolama kapsayıcıları denetimi hakkında daha fazla bilgi gerekiyorsa [Docker depolama sürücülerini](https://docs.docker.com/storage/storagedriver/select-storage-driver/) ve [depolama sürücüleri hakkında](https://docs.docker.com/storage/storagedriver/).

Bu seçenekler hakkında daha fazla ayrıntı sağlar:

**Birimleri** olan konak işletim sisteminden kapsayıcılarında dizinlere eşlenen dizinleri. Kapsayıcıyı kodda erişim gerçekten konak işletim sistemi üzerindeki dizine olan dizinine sahip olduğunda. Bu dizin için kapsayıcı ömrünü bağlı değildir ve dizin Docker tarafından yönetilen ve ana makinenin çekirdek işlevleri birbirinden yalıtılmış. Bu nedenle, veri hacimleri, kapsayıcının yaşam bağımsız olarak verilerin kalıcı hale getirmek için tasarlanmıştır. Bir kapsayıcıyı silme ya da bir görüntüden bir Docker konağı, verileri kalıcı hale veri hacmi silinmez.

Adlandırılmış ve anonim birimleri olabilir (varsayılan). Adlandırılmış birimlerdir gelişimi **veri birim kapsayıcıları** ve kapsayıcılar arasında veri paylaşımı kolaylaştırır. Birimleri Ayrıca, diğer seçenekler arasında Uzak konaklarda veri depolamanızı sağlayan birim sürücüsü, destekler.

**Takar bağlama** uzun zaman önce bu yana kullanılabilir ve bir kapsayıcıdaki bir bağlama noktası herhangi bir klasöre eşleme sağlar. Böylece birimleri önerilen seçenek bağlama takar birimleri değerinden daha fazla sınırlamalar ve bazı önemli güvenlik sorunları vardır.

**tmpfs bağlar** yalnızca ana bilgisayarın bellek canlı ve dosya sistemi için hiçbir zaman yazılır, temel sanal klasörlerdir. Bunlar hızlı ve güvenli ancak bellek kullanın ve yalnızca kalıcı olmayan veri modellemesine yöneliktir.

Şekil 4-5'te gösterildiği gibi normal Docker birim kapsayıcıları dışında ancak fiziksel ana bilgisayar sunucusuna veya VM sınırları içinde depolanabilir. Ancak, Docker kapsayıcıları bir birimi bir konak sunucusu veya VM diğerine erişemez. Diğer bir deyişle, bu birimler, uzak ana destekleyen bir birim sürücü elde ancak farklı Docker konakları üzerinde çalışan kapsayıcılar arasında paylaşılan verileri yönetmek mümkün değildir.

![Birim kapsayıcıları arasında paylaşılabilir, ancak yalnızca aynı ana bilgisayar, uzak bir sürücüyü kullanmadığınız sürece uzak ana destekleyen. ](./media/image5.png)

**Şekil 4-5**. Birimler ve kapsayıcı tabanlı uygulamalar için dış veri kaynakları

Docker kapsayıcıları bir orchestrator tarafından yönetildiğinde ek olarak, kapsayıcıları "Küme tarafından gerçekleştirilen iyileştirmeleri bağlı olarak, konaklar arasında taşıyabilirsiniz". Bu nedenle, iş verileri için veri birimleri kullanmanız önerilmez. Ancak geçici dosyaları, izleme dosyaları ile çalışmak için iyi bir mekanizma oldukları veya benzer, iş veri tutarlılığı etkilemez.

**Uzak Veri kaynaklarını ve önbellek** Azure SQL veritabanı, Azure Cosmos DB veya Redis kullanılabilir gibi uzak bir önbellek gibi araçlarla kapsayıcılı uygulamaları bunlar kullanılır kapsayıcıları geliştirirken aynı şekilde. Bu, iş uygulama verilerini depolamak için kendini kanıtlamış bir yoludur.

**Azure depolama.** İş verileri genellikle dış kaynaklara veya veritabanları, Azure depolama gibi yerleştirilmesi gerekir. Azure depolama, somut, bulutta aşağıdaki hizmetleri sağlar:

- BLOB Depolama, yapılandırılmamış nesne verilerini depolar. Bir blob, belge veya medya dosyaları (görüntüler, ses ve video dosyaları) gibi metin veya ikili veriler herhangi bir türde olabilir. BLOB storage ayrıca nesne depolama olarak adlandırılır.

- File storage standart SMB protokolünü kullanan eski uygulamalar için paylaşılan depolama alanı sağlar. Azure virtual machines ve cloud services bağlı paylaşımlar üzerinden uygulama bileşenleri arasında dosya verileri paylaşabilir. Şirket içi uygulamalar dosya hizmeti REST API'si yoluyla paylaşımdaki dosya verilerine erişebilir.

- Tablo depolama, yapılandırılmış veri kümelerini depolar. Tablo, hızlı geliştirme ve büyük miktarda verilerin hızlı erişim sağlayan bir NoSQL anahtar özniteliği veri deposu depolamadır.

**İlişkisel veritabanları ve NoSQL veritabanları.** Azure Cosmos DB, MongoDB gibi SQL Server, Oracle, PostgreSQL ya da NoSQL veritabanları gibi ilişkisel veritabanlarından dış veritabanları için çok sayıda seçeneğiniz vardır. Bu veritabanları, bu kılavuzun bir parçası olarak da tamamen farklı bir konu olduklarından açıklanması yapmayacağınız.

>[!div class="step-by-step"]
>[Önceki](containerize-monolithic-applications.md)
>[İleri](service-oriented-architecture.md)